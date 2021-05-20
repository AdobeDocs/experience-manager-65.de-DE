---
title: Digitales Signieren und Zertifizieren von Dokumenten
seo-title: Digitales Signieren und Zertifizieren von Dokumenten
description: Mit dem Signature-Dienst können Sie einem PDF-Dokument digitale Signaturfelder hinzufügen und löschen, die Namen der in einem PDF-Dokument enthaltenen Signaturfelder abrufen, Signaturfelder ändern, PDF-Dokumente digital signieren, PDF-Dokumente zertifizieren, digitale Signaturen in einem PDF-Dokument validieren, alle digitalen Signaturen in einem PDF-Dokument validieren und eine digitale Signatur aus einem Signaturfeld entfernen.
seo-description: Mit dem Signature-Dienst können Sie einem PDF-Dokument digitale Signaturfelder hinzufügen und löschen, die Namen der in einem PDF-Dokument enthaltenen Signaturfelder abrufen, Signaturfelder ändern, PDF-Dokumente digital signieren, PDF-Dokumente zertifizieren, digitale Signaturen in einem PDF-Dokument validieren, alle digitalen Signaturen in einem PDF-Dokument validieren und eine digitale Signatur aus einem Signaturfeld entfernen.
uuid: 6331de8a-2a9c-45bf-89d2-29f1ad5cc856
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 42de04bf-25e4-4478-a411-38671ed871ae
role: Developer
exl-id: c200f345-40ab-46fd-b6ed-f3af0a23796b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '17113'
ht-degree: 8%

---

# Digitales Signieren und Zertifizieren von Dokumenten {#digitally-signing-and-certifying-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

**Über den Signature-Dienst**

Mit dem Signature-Dienst kann Ihr Unternehmen die Sicherheit und den Datenschutz von Adobe PDF-Dokumenten schützen, die es verteilt und empfängt. Dieser Dienst verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur beabsichtigte Empfänger Dokumente ändern können. Da Sicherheitsfunktionen auf das Dokument selbst angewendet werden, bleibt das Dokument für seinen gesamten Lebenszyklus sicher und kontrolliert. Ein Dokument bleibt außerhalb der Firewall sicher, wenn es offline heruntergeladen und an Ihr Unternehmen zurückgesendet wird.

>[!NOTE]
>
>Sie können einen benutzerdefinierten Signatur-Handler für den Signature-Dienst erstellen, der beim Aufrufen bestimmter Vorgänge aufgerufen wird, z. B. beim Signieren eines PDF-Dokuments.

**Signaturfeldnamen**

Bei einigen Signature-Dienstvorgängen müssen Sie den Namen des Signaturfelds angeben, für das ein Vorgang ausgeführt wird. Beispielsweise geben Sie beim Signieren eines PDF-Dokuments den Namen des Signaturfelds an, das signiert werden soll. Angenommen, der vollständige Name eines Signaturfelds ist `form1[0].Form1[0].SignatureField1[0]`. Sie können `SignatureField1[0]` anstelle von `form1[0].Form1[0].SignatureField1[0]` angeben.

Manchmal führt ein Konflikt dazu, dass der Signature-Dienst das falsche Feld signiert (oder einen anderen Vorgang ausführt, für den der Signaturfeldname erforderlich ist). Dieser Konflikt ist das Ergebnis des Namens `SignatureField1[0]`, der an zwei oder mehr Stellen im selben PDF-Dokument angezeigt wird. Angenommen, ein PDF-Dokument enthält zwei Signaturfelder mit den Namen `form1[0].Form1[0].SignatureField1[0]` und `form1[0].Form1[0].SubForm1[0].SignatureField1[0]` und Sie geben `SignatureField1[0]` an. In diesem Fall signiert der Signature-Dienst das erste Signaturfeld, das er beim Iterieren aller Signaturfelder im Dokument findet.

Wenn ein PDF-Dokument mehrere Signaturfelder enthält, sollten Sie die vollständigen Namen der Signaturfelder angeben. Geben Sie also `form1[0].Form1[0].SignatureField1[0]`anstelle von `SignatureField1[0]` an.

Sie können diese Aufgaben mithilfe des Signature-Dienstes ausführen:

* Hinzufügen und Löschen digitaler Signaturfelder zu einem PDF-Dokument. (Siehe [Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields).)
* Rufen Sie die Namen der Signaturfelder ab, die sich in einem PDF-Dokument befinden. (Siehe [Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names).)
* Ändern Sie die Signaturfelder. (Siehe [Ändern von Signaturfeldern](digitally-signing-certifying-documents.md#modifying-signature-fields).)
* PDF-Dokumente digital signieren (Siehe [PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)
* PDF-Dokumente zertifizieren. (Siehe [Zertifizieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#certifying-pdf-documents).)
* Validieren digitaler Signaturen in einem PDF-Dokument. (Siehe [Digitale Signaturen überprüfen](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Validieren Sie alle digitalen Signaturen, die sich in einem PDF-Dokument befinden. (Siehe [Überprüfen mehrerer digitaler Signaturen](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Entfernen Sie eine digitale Signatur aus einem Signaturfeld. (Siehe [Entfernen digitaler Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures).)

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Hinzufügen von Signaturfeldern {#adding-signature-fields}

Digitale Signaturen werden in Signaturfeldern angezeigt, die eine grafische Darstellung der Signatur enthaltende Formularfelder sind. Signaturfelder können sichtbar oder unsichtbar sein. Unterzeichner können ein bereits vorhandenes Signaturfeld verwenden oder programmgesteuert ein Signaturfeld hinzugefügt werden. In beiden Fällen muss das Signaturfeld vorhanden sein, bevor ein PDF-Dokument signiert werden kann.

Sie können ein Signaturfeld programmgesteuert hinzufügen, indem Sie die Signature-Dienst-Java-API oder die Signature-Webdienst-API verwenden. Sie können einem PDF-Dokument mehr als ein Signaturfeld hinzufügen. Jeder Signaturfeldname muss jedoch eindeutig sein.

>[!NOTE]
>
>Bei einigen PDF-Dokumenttypen können Sie kein Signaturfeld programmgesteuert hinzufügen. Weitere Informationen zum Signature-Dienst und zum Hinzufügen von Signaturfeldern finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein Signaturfeld zu einem PDF-Dokument hinzuzufügen, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie ein PDF-Dokument ab, dem ein Signaturfeld hinzugefügt wird.
1. Fügen Sie ein Signaturfeld hinzu.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument abrufen, dem ein Signaturfeld hinzugefügt wird**

Sie müssen ein PDF-Dokument abrufen, dem ein Signaturfeld hinzugefügt wird.

**Signaturfeld hinzufügen**

Um einem PDF-Dokument erfolgreich ein Signaturfeld hinzuzufügen, geben Sie Koordinatenwerte an, die den Speicherort des Signaturfelds angeben. (Wenn Sie ein unsichtbares Signaturfeld hinzufügen, sind diese Werte nicht erforderlich.) Sie können auch angeben, welche Felder im PDF-Dokument gesperrt werden, nachdem eine Signatur auf das Signaturfeld angewendet wurde.

**PDF-Dokument als PDF-Datei speichern**

Nachdem der Signature-Dienst ein Signaturfeld zum PDF-Dokument hinzugefügt hat, können Sie das Dokument als PDF-Datei speichern, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Signaturfelder mithilfe der Java-API hinzufügen {#add-signature-fields-using-the-java-api}

Fügen Sie mithilfe der Signature-API (Java) ein Signaturfeld hinzu:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-signatures-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, dem ein Signaturfeld hinzugefügt wird

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, dem ein Signaturfeld hinzugefügt wird, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Signaturfeld hinzufügen

   * Erstellen Sie ein `PositionRectangle`-Objekt, das den Speicherort des Signaturfelds mithilfe seines Konstruktors angibt. Geben Sie im Konstruktor Koordinatenwerte an.
   * Erstellen Sie bei Bedarf ein `FieldMDPOptions`-Objekt, das die Felder angibt, die gesperrt werden, wenn eine digitale Signatur auf das Signaturfeld angewendet wird.
   * Fügen Sie ein Signaturfeld zu einem PDF-Dokument hinzu, indem Sie die `addSignatureField` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

      * A `com.adobe.idp`. `Document` -Objekt, das das PDF-Dokument darstellt, dem ein Signaturfeld hinzugefügt wird.
      * Ein string -Wert, der den Namen des Signaturfelds angibt.
      * Ein `java.lang.Integer` -Wert für die Seitennummer, der ein Signaturfeld hinzugefügt wird.
      * Ein `PositionRectangle` -Objekt, das den Speicherort des Signaturfelds angibt.
      * Ein `FieldMDPOptions` -Objekt, das Felder im PDF-Dokument angibt, die gesperrt werden, nachdem eine digitale Signatur auf das Signaturfeld angewendet wurde. Dieser Parameterwert ist optional und Sie können `null` übergeben.
   * Ein `PDFSeedValueOptions` -Objekt, das verschiedene Laufzeitwerte angibt. Dieser Parameterwert ist optional und Sie können `null` übergeben.

      Die `addSignatureField`-Methode gibt einen `com.adobe.idp` zurück. `Document` -Objekt, das ein PDF-Dokument mit einem Signaturfeld darstellt.
   >[!NOTE]
   >
   >Sie können die `addInvisibleSignatureField`-Methode des Objekts `SignatureServiceClient` aufrufen, um ein unsichtbares Signaturfeld hinzuzufügen.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie `com.adobe.idp` auf. `Document` - `copyToFile` Methode des -Objekts verwenden, um den Inhalt des - `Document` Objekts in die -Datei zu kopieren. Stellen Sie sicher, dass Sie `com.adobe.idp` verwenden. `Document` -Objekt, das von der - `addSignatureField` Methode zurückgegeben wurde.

**Siehe auch**

[Schnellstarts für Signature Service-API](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

### Signaturfelder mithilfe der Webdienst-API {#add-signature-fields-using-the-web-service-api} hinzufügen

So fügen Sie mithilfe der Signature-API (Webdienst) ein Signaturfeld hinzu:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen, dem ein Signaturfeld hinzugefügt wird

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das ein Signaturfeld enthalten wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Signaturfeld hinzufügen

   Fügen Sie ein Signaturfeld zum PDF-Dokument hinzu, indem Sie die `addSignatureField` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB` -Objekt, das das PDF-Dokument darstellt, dem ein Signaturfeld hinzugefügt wird.
   * Ein string -Wert, der den Signaturfeldnamen angibt.
   * Ein integer -Wert für die Seitenzahl, der ein Signaturfeld hinzugefügt wird.
   * Ein `PositionRect` -Objekt, das den Speicherort des Signaturfelds angibt.
   * Ein `FieldMDPOptions` -Objekt, das Felder im PDF-Dokument angibt, die gesperrt werden, nachdem eine digitale Signatur auf das Signaturfeld angewendet wurde. Dieser Parameterwert ist optional und Sie können `null` übergeben.
   * Ein `PDFSeedValueOptions` -Objekt, das verschiedene Laufzeitwerte angibt. Dieser Parameterwert ist optional und Sie können `null` übergeben.

   Die `addSignatureField`-Methode gibt ein `BLOB`-Objekt zurück, das ein PDF-Dokument mit einem Signaturfeld darstellt.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das das Signaturfeld enthalten wird, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `addSignatureField` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Abrufen von Signaturfeldnamen {#retrieving-signature-field-names}

Sie können die Namen aller Signaturfelder abrufen, die sich in einem zu signierenden und zertifizierenden PDF-Dokument befinden. Wenn Sie nicht sicher sind, wie die Signaturfeldnamen in einem PDF-Dokument lauten oder die Namen prüfen möchten, können Sie diese programmgesteuert abrufen. Der Signature-Dienst gibt den vollständig qualifizierten Namen des Signaturfelds zurück, z. B. `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um Signaturfeldnamen abzurufen, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das Signaturfelder enthält.
1. Rufen Sie die Signaturfeldnamen ab.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument abrufen, das Signaturfelder enthält**

Rufen Sie ein PDF-Dokument mit Signaturfeldern ab.

**Abrufen der Signaturfeldnamen**

Sie können Signaturfeldnamen abrufen, nachdem Sie ein PDF-Dokument abgerufen haben, das ein oder mehrere Signaturfelder enthält.

**Siehe auch**

[Abrufen von Signaturfeldnamen mithilfe der Java-API](digitally-signing-certifying-documents.md#retrieve-signature-field-names-using-the-java-api)

[Abrufen von Signaturfeldern mithilfe der Webdienst-API](digitally-signing-certifying-documents.md#retrieve-signature-field-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

### Abrufen von Signaturfeldnamen mithilfe der Java-API {#retrieve-signature-field-names-using-the-java-api}

Rufen Sie mithilfe der Signature-API (Java) Signaturfeldnamen ab:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie die adobe-signatures-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das Signaturfelder enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, das Signaturfelder enthält, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Abrufen der Signaturfeldnamen

   * Rufen Sie die Signaturfeldnamen ab, indem Sie die `getSignatureFieldList` -Methode des Objekts `SignatureServiceClient` aufrufen und das `com.adobe.idp.Document` -Objekt übergeben, das das PDF-Dokument mit Signaturfeldern enthält. Diese Methode gibt ein `java.util.List` -Objekt zurück, in dem jedes Element ein `PDFSignatureField` -Objekt enthält. Mit diesem Objekt können Sie zusätzliche Informationen zu einem Signaturfeld abrufen, z. B. ob es sichtbar ist.
   * Durchsuchen Sie das `java.util.List`-Objekt, um festzustellen, ob Signaturfeldnamen vorhanden sind. Für jedes Signaturfeld im PDF-Dokument können Sie ein separates `PDFSignatureField` -Objekt abrufen. Um den Namen des Signaturfelds abzurufen, rufen Sie die `getName`-Methode des Objekts `PDFSignatureField` auf. Diese Methode gibt einen string -Wert zurück, der den Signaturfeldnamen angibt.

**Siehe auch**

[Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Schnellstart (SOAP-Modus): Abrufen von Signaturfeldnamen mithilfe der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Signaturfeld mit der Webdienst-API abrufen {#retrieve-signature-field-using-the-web-service-api}

Rufen Sie Signaturfeldnamen mithilfe der Signature-API (Webdienst) ab:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen, das Signaturfelder enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das Signaturfelder enthält.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld den Inhalt des Byte-Arrays zuweisen.

1. Abrufen der Signaturfeldnamen

   * Rufen Sie die Signaturfeldnamen ab, indem Sie die `getSignatureFieldList` -Methode des Objekts `SignatureServiceClient` aufrufen und das `BLOB` -Objekt übergeben, das das PDF-Dokument mit Signaturfeldern enthält. Diese Methode gibt ein Kollektionsobjekt `MyArrayOfPDFSignatureField` zurück, in dem jedes Element ein `PDFSignatureField` -Objekt enthält.
   * Durchsuchen Sie das `MyArrayOfPDFSignatureField`-Objekt, um festzustellen, ob Signaturfeldnamen vorhanden sind. Für jedes Signaturfeld im PDF-Dokument können Sie ein `PDFSignatureField` -Objekt abrufen. Um den Namen des Signaturfelds abzurufen, rufen Sie die `getName`-Methode des Objekts `PDFSignatureField` auf. Diese Methode gibt einen string -Wert zurück, der den Signaturfeldnamen angibt.

**Siehe auch**

[Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Ändern von Signaturfeldern {#modifying-signature-fields}

Sie können Signaturfelder in einem PDF-Dokument mithilfe der Java-API und der Web-Service-API ändern. Das Ändern eines Signaturfelds umfasst das Manipulieren seiner Signaturfeldsperre- oder Seed-Wert-Lexikonwerte.

Ein *Feldsperre-Wörterbuch* gibt eine Liste von Feldern an, die beim Signieren des Signaturfelds gesperrt werden. Ein gesperrtes Feld verhindert, dass Benutzer Änderungen an dem Feld vornehmen. Ein *Seed-Wert-Wörterbuch* enthält Einschränkungsinformationen, die zum Zeitpunkt der Anwendung der Signatur verwendet werden. Beispiel: Sie können die Berechtigungen ändern, die Aktionen steuern, die auftreten können, ohne dass eine Signatur ungültig wird.

Durch Änderung eines vorhandenen Signaturfelds können Sie Änderungen am PDF-Dokument vornehmen, um die sich ändernden Geschäftsanforderungen widerzuspiegeln. Eine neue Geschäftsanforderung kann beispielsweise das Sperren aller Dokumentfelder nach dem Signieren des Dokuments erfordern.

In diesem Abschnitt wird beschrieben, wie Sie ein Signaturfeld ändern, indem Sie sowohl die Werte des Feldsperre-Wörterbuchs als auch des Seed-Wert-Wörterbuchs ändern. Änderungen am Sperrwörterbuch für Signaturfelder führen dazu, dass alle Felder im PDF-Dokument gesperrt werden, wenn ein Signaturfeld signiert wird. Änderungen am Seed-Wert-Wörterbuch verbieten bestimmte Arten von Änderungen am Dokument.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Ändern von Signaturfeldern finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um Signaturfelder in einem PDF-Dokument zu ändern, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das das zu ändernde Signaturfeld enthält.
1. Legen Sie Wörterbuchwerte fest.
1. Ändern Sie das Signaturfeld.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von LiveCycle Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument abrufen, das das zu ändernde Signaturfeld enthält**

Rufen Sie ein PDF-Dokument ab, das das zu ändernde Signaturfeld enthält.

**Festlegen von Wörterbuchwerten**

Um ein Signaturfeld zu ändern, weisen Sie seinem Feldsperre- oder Seed-Wert-Wörterbuch Werte zu. Das Festlegen von Signaturfeld-Sperrwörterbuchwerten umfasst das Angeben von PDF-Dokumentfeldern, die beim Signieren des Signaturfelds gesperrt werden. (In diesem Abschnitt wird beschrieben, wie Sie alle Felder sperren.)

Die folgenden Seed-Wert-Wörterbuchwerte können festgelegt werden:

* **Revisionsüberprüfung**: Gibt an, ob eine Sperrprüfung durchgeführt wird, wenn eine Signatur auf das Signaturfeld angewendet wird.
* **Zertifikatoptionen**: Weist dem Seed-Wert-Wörterbuch des Zertifikats Werte zu. Bevor Sie Zertifikatoptionen angeben, sollten Sie sich mit einem Seed-Wert-Wörterbuch für Zertifikate vertraut machen. (Siehe [PDF-Referenz](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Digest options**: Weist Digest-Algorithmen zu, die zum Signieren verwendet werden. Gültige Werte sind SHA1, SHA256, SHA384, SHA512 und RIPEMD160.
* **Filter**: Gibt den Filter an, der mit dem Signaturfeld verwendet wird. Sie können beispielsweise den Filter Adobe.PPKLite verwenden. (Siehe [PDF-Referenz](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Flag-Optionen**: Gibt die mit diesem Signaturfeld verknüpften Flaggenwerte an. Der Wert 1 bedeutet, dass ein Unterzeichner nur die angegebenen Werte für den Eintrag verwenden darf. Der Wert 0 bedeutet, dass andere Werte zulässig sind. Hier sind die Bitpositionen:

   * **1(Filter):** Der zum Signieren des Signaturfelds zu verwendende Signatur-Handler
   * **2 (SubFilter):** Ein Array von Namen, die akzeptable Kodierungen angeben, die beim Signieren verwendet werden können
   * **3 (V)**: Die erforderliche Mindestversionsnummer des zum Signieren des Signaturfelds zu verwendenden Signatur-Handlers.
   * **4 (Gründe):** Ein Array von Zeichenfolgen, die mögliche Gründe für das Signieren eines Dokuments angeben
   * **5 (PDFLegalWarnings):** Ein Array von Zeichenfolgen, die mögliche gültige Beglaubigungen angeben

* **Rechtliche Beglaubigungen**: Wenn ein Dokument zertifiziert ist, wird es automatisch auf bestimmte Inhaltstypen überprüft, die den sichtbaren Inhalt eines Dokuments mehrdeutig oder irreführend machen können. Beispielsweise kann eine Anmerkung Text verdecken, der für das Verständnis dessen wichtig ist, was zertifiziert wird. Der Scanvorgang erzeugt Warnungen, die auf das Vorhandensein dieses Inhaltstyps hinweisen. Es bietet außerdem eine zusätzliche Erläuterung des Inhalts, der möglicherweise Warnungen generiert hat.
* **Berechtigungen**: Gibt Berechtigungen an, die für ein PDF-Dokument verwendet werden können, ohne die Signatur ungültig zu machen.
* **Gründe**: Gibt Gründe an, aus denen dieses Dokument signiert werden muss.
* **Zeitstempel**: Gibt Zeitstempeloptionen an. Sie können beispielsweise die URL des verwendeten Zeitstempelservers festlegen.
* **Version**: Gibt die Mindestversionsnummer des Signatur-Handlers an, der zum Signieren des Signaturfelds verwendet werden soll.

**Signaturfeld ändern**

Nachdem Sie einen Signature-Dienst-Client erstellt, das PDF-Dokument abgerufen haben, das das zu ändernde Signaturfeld enthält, und Wörterbuchwerte festgelegt haben, können Sie den Signature-Dienst anweisen, das Signaturfeld zu ändern. Der Signature-Dienst gibt dann ein PDF-Dokument zurück, das das geänderte Signaturfeld enthält. Das ursprüngliche PDF-Dokument ist nicht betroffen.

**PDF-Dokument als PDF-Datei speichern**

Speichern Sie das PDF-Dokument mit dem geänderten Signaturfeld als PDF-Datei, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts für Signature Service-API](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Ändern von Signaturfeldern mithilfe der Java-API {#modify-signature-fields-using-the-java-api}

Ändern Sie ein Signaturfeld mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-signatures-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das das zu ändernde Signaturfeld enthält

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das PDF-Dokument darstellt, das das zu ändernde Signaturfeld enthält, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Wörterbuchwerten

   * Erstellen Sie ein Objekt `PDFSignatureFieldProperties`, indem Sie den Konstruktor verwenden. Ein `PDFSignatureFieldProperties` -Objekt speichert Signaturfeld-Sperrwörterbuch und Seed-Wert-Wörterbücher.
   * Erstellen Sie ein Objekt `PDFSeedValueOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Seed-Wert-Wörterbuchwerte festlegen.
   * Deaktivieren Sie Änderungen am PDF-Dokument, indem Sie die `setMdpValue`-Methode des Objekts `PDFSeedValueOptionSpec` aufrufen und den Auflistungswert `MDPPermissions.NoChanges` übergeben.
   * Erstellen Sie ein Objekt `FieldMDPOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Signaturfeldsperre-Wörterbuchwerte festlegen.
   * Sperren Sie alle Felder im PDF-Dokument, indem Sie die Methode `setMdpValue` des Objekts `FieldMDPOptionSpec` aufrufen und den Auflistungswert `FieldMDPAction.ALL` übergeben.
   * Legen Sie die Wörterbuchinformationen für Seed-Werte fest, indem Sie die `setSeedValue` -Methode des Objekts `PDFSignatureFieldProperties` aufrufen und das `PDFSeedValueOptionSpec` -Objekt übergeben.
   * Legen Sie die Signaturfeldsperre-Wörterbuchinformationen fest, indem Sie die `setFieldMDP`-Methode des Objekts `PDFSignatureFieldProperties`aufrufen und das `FieldMDPOptionSpec`-Objekt übergeben.

   >[!NOTE]
   >
   >Informationen zum Anzeigen aller Seed-Wert-Wörterbuchwerte, die Sie festlegen können, finden Sie in der `PDFSeedValueOptionSpec` -Klassenreferenz. (Siehe [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

1. Signaturfeld ändern

   Ändern Sie das Signaturfeld, indem Sie die `modifySignatureField` -Methode des `SignatureServiceClient` -Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument speichert, das das zu ändernde Signaturfeld enthält
   * Ein string -Wert, der den Namen des Signaturfelds angibt
   * Das `PDFSignatureFieldProperties`-Objekt, das das Signaturfeld-Sperrwörterbuch und die Seed-Wert-Wörterbuchinformationen speichert

   Die `modifySignatureField`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein PDF-Dokument speichert, das das geänderte Signaturfeld enthält.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `modifySignatureField`-Methode zurückgegeben wurde.

### Ändern Sie die Signaturfelder mithilfe der Webdienst-API {#modify-signature-fields-using-the-web-service-api}.

Ändern Sie ein Signaturfeld mithilfe der Signature-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen, das das zu ändernde Signaturfeld enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das das zu ändernde Signaturfeld enthält.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Wörterbuchwerten

   * Erstellen Sie ein Objekt `PDFSignatureFieldProperties`, indem Sie den Konstruktor verwenden. Dieses Objekt speichert das Signaturfeldsperre-Wörterbuch und Seed-Wert-Wörterbuch.
   * Erstellen Sie ein Objekt `PDFSeedValueOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Seed-Wert-Wörterbuchwerte festlegen.
   * Deaktivieren Sie Änderungen am PDF-Dokument, indem Sie den Auflistungswert `MDPPermissions.NoChanges` dem `PDFSeedValueOptionSpec` -Datenelement des Objekts `mdpValue` zuweisen.
   * Erstellen Sie ein Objekt `FieldMDPOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Signaturfeldsperre-Wörterbuchwerte festlegen.
   * Sperren Sie alle Felder im PDF-Dokument, indem Sie den Auflistungswert `FieldMDPAction.ALL` dem `FieldMDPOptionSpec` -Datenelement des Objekts `mdpValue` zuweisen.
   * Legen Sie die Wörterbuchinformationen für Seed-Werte fest, indem Sie das `PDFSeedValueOptionSpec`-Objekt dem `PDFSignatureFieldProperties`-Datenelement des Objekts `seedValue` zuweisen.
   * Setzen Sie die Signaturfeld-Sperrwörterbuchinformationen, indem Sie das `FieldMDPOptionSpec`-Objekt dem `PDFSignatureFieldProperties`-Datenelement des `fieldMDP`-Objekts zuweisen.

   >[!NOTE]
   >
   >Informationen zum Anzeigen aller Seed-Wert-Wörterbuchwerte, die Sie festlegen können, finden Sie in der `PDFSeedValueOptionSpec` -Klassenreferenz. (Siehe [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

1. Signaturfeld ändern

   Ändern Sie das Signaturfeld, indem Sie die `modifySignatureField` -Methode des `SignatureServiceClient` -Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument speichert, das das zu ändernde Signaturfeld enthält
   * Ein string -Wert, der den Namen des Signaturfelds angibt
   * Das `PDFSignatureFieldProperties`-Objekt, das das Signaturfeld-Sperrwörterbuch und die Seed-Wert-Wörterbuchinformationen speichert

   Die `modifySignatureField`-Methode gibt ein `BLOB`-Objekt zurück, das ein PDF-Dokument speichert, das das geänderte Signaturfeld enthält.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das das Signaturfeld enthalten soll, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der `addSignatureField`-Methode zurückgegeben wird. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digital Signing PDF Documents {#digitally-signing-pdf-documents}

Digitale Signaturen können zu Sicherheitszwecken auf PDF-Dokumente angewendet werden. Digitale Signaturen bieten wie handschriftliche Signaturen ein Mittel, mit dem sich die Unterzeichner identifizieren und zum Dokument Stellung nehmen. Die zum digitalen Signieren verwendete Technologie stellt sicher, dass sowohl der Unterzeichner als auch die Empfänger genau wissen, was signiert wurde und dass das Dokument nach dem Signieren nicht geändert wurde.

PDF-Dokumente werden mittels der Technologie öffentlicher Schlüssel signiert. Ein Unterzeichner hat zwei Schlüssel: einen öffentlichen Schlüssel und einen privaten Schlüssel. Der private Schlüssel wird in den Anmeldedaten eines Benutzers gespeichert, die zum Zeitpunkt des Signierens verfügbar sein müssen. Der öffentliche Schlüssel wird im Zertifikat des Benutzers gespeichert, das Empfängern zur Validierung der Signatur zur Verfügung stehen muss. Informationen zu gesperrten Zertifikaten finden Sie in den Zertifikatsperrlisten (CRLs) und den Antworten des Online-Zertifikatstatusprotokolls (OCSP), die von Zertifizierungsstellen (CAs) verteilt werden. Der Zeitpunkt der Signatur kann von einer vertrauenswürdigen Quelle, die als Zeitstempeldienst bezeichnet wird, erhalten werden.

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument digital signieren können, müssen Sie sicherstellen, dass Sie das Zertifikat zu AEM Forms hinzufügen. Ein Zertifikat wird über Administration Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Importing Credentials by using the Trust Manager API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Sie können PDF-Dokumente programmgesteuert digital signieren. Beim digitalen Signieren eines PDF-Dokuments müssen Sie auf eine Sicherheitsberechtigung verweisen, die in AEM Forms vorhanden ist. Die Anmeldedaten bestehen aus dem zum Signieren verwendeten privaten Schlüssel.

Der Signature-Dienst führt beim Signieren eines PDF-Dokuments die folgenden Schritte aus:

1. Der Signature-Dienst ruft die Berechtigung aus dem Truststore ab, indem er den in der Anfrage angegebenen Alias übergibt.
1. Der Truststore sucht nach der angegebenen Berechtigung.
1. Die Berechtigung wird an den Signature-Dienst zurückgegeben und zum Signieren des Dokuments verwendet. Die Berechtigung wird auch gegen den Alias für zukünftige Anforderungen zwischengespeichert.

Informationen zum Umgang mit Sicherheitsberechtigungen finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

>[!NOTE]
>
>Es gibt Unterschiede zwischen dem Signieren und Zertifizieren von Dokumenten. (Siehe [Zertifizieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#certifying-pdf-documents).)

>[!NOTE]
>
>Nicht alle PDF-Dokumente unterstützen das Signieren. Weitere Informationen zum Signature-Dienst und zum digitalen Signieren von Dokumenten finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Der Signature-Dienst unterstützt keine XDP-Dateien mit eingebetteten PDF-Daten als Eingabe für einen Vorgang, z. B. das Zertifizieren eines Dokuments. Diese Aktion führt dazu, dass der Signature-Dienst ein `PDFOperationException` zurückgibt. Um dieses Problem zu beheben, konvertieren Sie die XDP-Datei mithilfe des PDF Utilities-Dienstes in eine PDF-Datei und übergeben Sie dann die konvertierte PDF-Datei an einen Signature-Dienst-Vorgang. (Siehe [Arbeiten mit PDF Utilities](/help/forms/developing/pdf-utilities.md#working-with-pdf-utilities).)

**Cipher nShield HSM-Berechtigung**

Wenn Sie zum Signieren oder Zertifizieren eines PDF-Dokuments eine Cipher nShield-HSM-Berechtigung verwenden, kann die neue Berechtigung erst verwendet werden, nachdem der J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt ist, neu gestartet wurde. Sie können jedoch einen Konfigurationswert festlegen, der dazu führt, dass der Vorgang zum Signieren oder Zertifizieren funktioniert, ohne den J2EE-Anwendungsserver neu zu starten.

Sie können den folgenden Konfigurationswert zur Datei &quot;cknfastrc&quot;hinzufügen, die sich unter /opt/nfast/cknfastrc (oder c:\nfast\cknfastrc) befindet:

```shell
    CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nachdem Sie diesen Konfigurationswert zur cknfastrc-Datei hinzugefügt haben, können die neuen Anmeldedaten verwendet werden, ohne den J2EE-Anwendungsserver neu zu starten.

**Signatur ist nicht vertrauenswürdig**

Wenn beim Zertifizieren und Signieren desselben PDF-Dokuments die Zertifizierungssignatur nicht als vertrauenswürdig eingestuft wird, wird beim Öffnen des PDF-Dokuments in Acrobat oder Adobe Reader ein gelbes Dreieck gegen die erste Signatur angezeigt. Die Zertifizierungssignatur muss als vertrauenswürdig eingestuft werden, um dies zu vermeiden.

**Signieren von Dokumenten, die XFA-basierte Formulare sind**

Wenn Sie versuchen, ein XFA-basiertes Formular mithilfe der Signature-Dienst-API zu signieren, fehlen die Daten möglicherweise in der in Acrobat vorhandenen `View` `Signed` `Version`. Betrachten Sie beispielsweise den folgenden Workflow:

* Mithilfe einer mit Designer erstellten XDP-Datei führen Sie einen Formularentwurf zusammen, der ein Unterschriftsfeld und XML-Daten enthält, die Formulardaten enthalten. Mit dem Forms-Dienst generieren Sie ein interaktives PDF-Dokument.
* Sie signieren das PDF-Dokument mit der Signature-Dienst-API.

### Zusammenfassung der Schritte {#summary_of_steps-3}

Um ein PDF-Dokument digital zu signieren, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signature-Dienst-Client.
1. PDF-Dokument zum Signieren abrufen.
1. Signieren Sie das PDF-Dokument.
1. Speichern Sie das signierte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument zum Signieren abrufen**

Zum Signieren eines PDF-Dokuments müssen Sie ein PDF-Dokument abrufen, das ein Signaturfeld enthält. Wenn ein PDF-Dokument kein Signaturfeld enthält, kann es nicht signiert werden. Ein Signaturfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden.

**Signieren des PDF-Dokuments**

Beim Signieren eines PDF-Dokuments können Sie Laufzeitoptionen festlegen, die vom Signature-Dienst verwendet werden. Sie können die folgenden Optionen festlegen:

* Aussehen-Optionen
* Sperrprüfung
* Zeitstempelwerte

Sie legen die Darstellungsoptionen mithilfe eines `PDFSignatureAppearanceOptionSpec` -Objekts fest. Beispielsweise können Sie das Datum innerhalb einer Signatur anzeigen, indem Sie die `setShowDate` -Methode des Objekts `PDFSignatureAppearanceOptionSpec` aufrufen und `true` übergeben.

Sie können auch angeben, ob eine Sperrprüfung durchgeführt werden soll, mit der festgestellt wird, ob das Zertifikat, das zum digitalen Signieren eines PDF-Dokuments verwendet wird, widerrufen wurde. Zur Durchführung der Sperrprüfung können Sie einen der folgenden Werte angeben:

* **NoCheck**: Führen Sie keine Sperrprüfung durch.
* **BestEffort**: Versuchen Sie immer, nach dem Sperren aller Zertifikate in der Kette zu suchen. Tritt bei der Überprüfung ein Problem auf, wird davon ausgegangen, dass der Widerruf gültig ist. Wenn ein Fehler auftritt, gehen Sie davon aus, dass das Zertifikat nicht widerrufen wird.
* **CheckIfAvailable:** Überprüfen Sie, ob Sperrinformationen für alle Zertifikate in der Kette verfügbar sind, ob Sperren möglich ist. Tritt bei der Überprüfung ein Problem auf, wird davon ausgegangen, dass die Sperrung ungültig ist. Wenn ein Fehler auftritt, gehen Sie davon aus, dass das Zertifikat widerrufen und ungültig ist. (Dies ist der Standardwert.)
* **AlwaysCheck**: Prüfen Sie, ob alle Zertifikate in der Kette auf Sperren gesetzt wurden. Wenn in keinem Zertifikat Sperrinformationen vorhanden sind, wird der Widerruf als ungültig angenommen.

Um eine Sperrprüfung für ein Zertifikat durchzuführen, können Sie mithilfe eines `CRLOptionSpec` -Objekts eine URL für einen Zertifikatsperrlisten-Server (CRL) angeben. Wenn Sie jedoch eine Sperrprüfung durchführen möchten und keine URL für einen Zertifikatsperrlisten-Server angeben, ruft der Signature-Dienst die URL aus dem Zertifikat ab.

Anstelle eines CRL-Servers können Sie bei der Prüfung von Sperren einen OCSP-Server (Online Certificate Status Protocol) verwenden. Normalerweise wird bei Verwendung eines OCSP-Servers im Gegensatz zu einem CRL-Server die Sperrprüfung schneller durchgeführt. (Siehe &quot;Online Certificate Status Protocol&quot;unter [https://tools.ietf.org/html/rfc2560](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signature-Dienst mithilfe von Adobe Applications and Services verwendet. Wenn beispielsweise der OCSP-Server zuerst in Adobe Applications and Services festgelegt wird, wird der OCSP-Server überprüft, gefolgt vom CRL-Server. (Siehe &quot;Verwalten von Zertifikaten und Berechtigungen mithilfe des Trust Store&quot;in der AAC-Hilfe).

Wenn Sie angeben, dass keine Sperrprüfung durchgeführt werden soll, prüft der Signature-Dienst nicht, ob das zum Signieren oder Zertifizieren eines Dokuments verwendete Zertifikat widerrufen wurde. Das heißt, CRL- und OCSP-Serverinformationen werden ignoriert.

>[!NOTE]
>
>Obwohl im Zertifikat eine Zertifikatsperrliste oder ein OCSP-Server angegeben werden kann, können Sie die im Zertifikat angegebene URL überschreiben, indem Sie ein `CRLOptionSpec`- und ein `OCSPOptionSpec`-Objekt verwenden. Um beispielsweise den CRL-Server zu überschreiben, können Sie die `setLocalURI` -Methode des Objekts `CRLOptionSpec` aufrufen.

Zeitstempel bezeichnen den Prozess der Nachverfolgung des Zeitpunkts, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, sollte es nicht mehr geändert werden, auch nicht vom Dokumenteigentümer. Die Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mit einem `TSPOptionSpec` -Objekt festlegen. Sie können beispielsweise die URL eines Zeitstempelanbieter-Servers (TSP) angeben.

>[!NOTE]
>
>Im Java- und Webdienst werden die Abschnitte und die entsprechenden Schnellstarts durchlaufen. Dabei wird die Sperrprüfung verwendet. Da keine CRL- oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem Zertifikat abgerufen, das zum digitalen Signieren des PDF-Dokuments verwendet wird.

Um ein PDF-Dokument erfolgreich zu signieren, können Sie den vollständig qualifizierten Namen des Signaturfelds angeben, das die digitale Signatur enthalten soll, z. B. `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds kann auch der Teilname des Signaturfelds verwendet werden: `SignatureField3[3]`.

Sie müssen auch auf eine Sicherheitsberechtigung verweisen, um ein PDF-Dokument digital zu signieren. Um auf eine Sicherheitsberechtigung zu verweisen, geben Sie einen Alias an. Der Alias ist ein Verweis auf eine tatsächliche Berechtigung, die sich in einer PKCS#12-Datei (mit .pfx-Erweiterung) oder einem Hardware-Sicherheitsmodul (HSM) befinden kann. Informationen zu den Sicherheitsberechtigungen finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

**Signiertes PDF-Dokument speichern**

Nachdem der Signature-Dienst das PDF-Dokument digital signiert hat, können Sie es als PDF-Datei speichern, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[PDF-Dokumente mit der Java-API digital signieren](digitally-signing-certifying-documents.md#digitally-sign-pdf-documents-using-the-java-api)

[PDF-Dokumente mit der Webdienst-API digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

[Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

### PDF-Dokumente mit der Java-API {#digitally-sign-pdf-documents-using-the-java-api} digital signieren

Digital signieren Sie ein PDF-Dokument mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-signatures-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument zum Signieren abrufen

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu digital signierende PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Signieren des PDF-Dokuments

   Signieren Sie das PDF-Dokument, indem Sie die `sign` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` -Objekt, das das zu signierende PDF-Dokument darstellt.
   * Ein string -Wert für den Namen des Signaturfelds, das die digitale Signatur enthalten wird.
   * Ein `Credential` -Objekt, das die Berechtigung darstellt, die zum digitalen Signieren des PDF-Dokuments verwendet wird. Erstellen Sie ein `Credential` -Objekt, indem Sie die statische `getInstance` -Methode des Objekts `Credential` aufrufen und einen string -Wert übergeben, der den Aliaswert angibt, der der Sicherheitsberechtigung entspricht.
   * Ein `HashAlgorithm` -Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein string -Wert, der den Grund darstellt, aus dem das PDF-Dokument digital signiert wurde.
   * Ein string -Wert, der die Kontaktinformationen des Signierers darstellt.
   * Ein `PDFSignatureAppearanceOptions` -Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um ein benutzerdefiniertes Logo zu einer digitalen Signatur hinzuzufügen.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll.
   * Ein `OCSPOptionSpec` -Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `CRLPreferences` -Objekt, das Voreinstellungen für Zertifikatsperrlisten (CRL) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `TSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein. Weitere Informationen finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Die `sign`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf und übergeben Sie `java.io.File`zum Kopieren des Inhalts des `Document`-Objekts in die Datei. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `sign`-Methode zurückgegeben wurde.

**Siehe auch**

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Schnellstart (SOAP-Modus): PDF-Dokument mit der Java-API digital signieren](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-Dokumente mit der Webdienst-API {#digitally-signing-pdf-documents-using-the-web-service-api} digital signieren

So signieren Sie ein PDF-Dokument digital mithilfe der Signature-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument zum Signieren abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines signierten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu signierenden PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Signieren des PDF-Dokuments

   Signieren Sie das PDF-Dokument, indem Sie die `sign` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB` -Objekt, das das zu signierende PDF-Dokument darstellt.
   * Ein string -Wert für den Namen des Signaturfelds, das die digitale Signatur enthalten wird.
   * Ein `Credential` -Objekt, das die Berechtigung darstellt, die zum digitalen Signieren des PDF-Dokuments verwendet wird. Erstellen Sie ein `Credential` -Objekt mithilfe des zugehörigen Konstruktors und geben Sie den Alias an, indem Sie der `alias` -Eigenschaft des Objekts `Credential` einen Wert zuweisen.
   * Ein `HashAlgorithm` -Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein string -Wert, der den Grund darstellt, aus dem das PDF-Dokument digital signiert wurde.
   * Ein string -Wert, der den Standort des Signierers darstellt.
   * Ein string -Wert, der die Kontaktinformationen des Signierers darstellt.
   * Ein `PDFSignatureAppearanceOptions` -Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um ein benutzerdefiniertes Logo zu einer digitalen Signatur hinzuzufügen.
   * Ein `System.Boolean` -Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `OCSPOptionSpec` -Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben. Weitere Informationen zu diesem Objekt finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences` -Objekt, das Voreinstellungen für Zertifikatsperrlisten (CRL) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `TSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein.

   Die `sign`-Methode gibt ein `BLOB`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `sign` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digital Signing Interactive Forms {#digitally-signing-interactive-forms}

Sie können ein interaktives Formular signieren, das der Forms-Dienst erstellt. Betrachten Sie beispielsweise den folgenden Workflow:

* Sie führen ein XFA-basiertes PDF-Formular, das mithilfe von Designer erstellt wurde, zusammen und verwenden den Forms-Dienst verwenden Formulardaten, die sich in einem XML-Dokument befinden. Der Forms-Server rendert ein interaktives Formular.
* Sie signieren das interaktive Formular mit der Signature-Dienst-API.

Das Ergebnis ist ein digital signiertes interaktives PDF-Formular. Wenn Sie ein PDF-Formular signieren, das auf einem XFA-Formular basiert, stellen Sie sicher, dass Sie die PDF-Datei als statisches PDF-Formular für die Adobe speichern. Wenn Sie versuchen, ein PDF-Formular zu signieren, das als dynamische PDF-Formular der Adobe gespeichert wird, tritt eine Ausnahme auf. Da Sie das Formular signieren, das vom Forms-Dienst zurückgegeben wird, stellen Sie sicher, dass das Formular ein Signaturfeld enthält.

>[!NOTE]
>
>Bevor Sie ein interaktives Formular digital signieren können, müssen Sie sicherstellen, dass Sie das Zertifikat zu AEM Forms hinzufügen. Ein Zertifikat wird über Administration Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Importing Credentials by using the Trust Manager API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Legen Sie bei Verwendung der Forms Service-API die Laufzeitoption `GenerateServerAppearance` auf `true` fest. Diese Laufzeitoption stellt sicher, dass das Erscheinungsbild des Formulars, das auf dem Server generiert wird, auch dann gültig bleibt, wenn es in Acrobat oder Adobe Reader geöffnet wird. Es wird empfohlen, diese Laufzeitoption beim Generieren eines interaktiven Formulars festzulegen, das mithilfe der Forms-API signiert werden soll.

>[!NOTE]
>
>Bevor Sie Digital Signing Interactive Forms lesen, sollten Sie mit dem Signieren von PDF-Dokumenten vertraut sein. (Siehe [PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um ein interaktives Formular digital zu signieren, das der Forms-Dienst zurückgibt, führen Sie die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Forms- und Signaturclient.
1. Rufen Sie das interaktive Formular mit dem Forms-Dienst ab.
1. Signieren Sie das interaktive Formular.
1. Speichern Sie das signierte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-forms-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Forms- und Signaturclient**

Da dieser Workflow sowohl den Forms- als auch den Signature-Dienst aufruft, erstellen Sie sowohl einen Forms-Dienstclient als auch einen Signature-Dienstclient.

**Abrufen des interaktiven Formulars mit dem Forms-Dienst**

Sie können den Forms-Dienst verwenden, um das zu signierende interaktive PDF-Formular abzurufen. Ab AEM Forms können Sie ein `com.adobe.idp.Document`-Objekt an den Forms-Dienst übergeben, der das wiederzugebende Formular enthält. Der Name dieser Methode ist `renderPDFForm2`. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das das zu signierende Formular enthält. Sie können diese `com.adobe.idp.Document`-Instanz an den Signature-Dienst übergeben.

Wenn Sie Webdienste verwenden, können Sie auch die `BLOB`-Instanz übergeben, die der Forms-Dienst an den Signature-Dienst zurückgibt.

>[!NOTE]
>
>Der Schnellstart im Zusammenhang mit dem Abschnitt &quot;Digitales Signieren interaktiver Forms&quot;ruft die Methode `renderPDFForm2` auf.

**Interaktives Formular unterschreiben**

Beim Signieren eines PDF-Dokuments können Sie Laufzeitoptionen festlegen, die der Signature-Dienst verwendet. Sie können die folgenden Optionen festlegen:

* Aussehen-Optionen
* Sperrprüfung
* Zeitstempelwerte

Sie legen die Darstellungsoptionen mithilfe eines `PDFSignatureAppearanceOptionSpec` -Objekts fest. Beispielsweise können Sie das Datum innerhalb einer Signatur anzeigen, indem Sie die `setShowDate` -Methode des Objekts `PDFSignatureAppearanceOptionSpec` aufrufen und `true` übergeben.

**Signiertes PDF-Dokument speichern**

Nachdem der Signature-Dienst das PDF-Dokument digital signiert hat, können Sie es als PDF-Datei speichern. Die PDF-Datei kann in Acrobat oder Adobe Reader geöffnet werden.

**Siehe auch**

[Interaktives Formular mit der Java-API digital signieren](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-java-api)

[Interaktives Formular mit der Webdienst-API digital signieren](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms)

### Interaktives Formular mit der Java-API {#digitally-sign-an-interactive-form-using-the-java-api} digital signieren

Interaktives Formular mit der Forms- und Signatur-API (Java) digital signieren:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-signatures-client.jar und adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms- und Signaturclient

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des interaktiven Formulars mit dem Forms-Dienst

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, das mithilfe des Konstruktors an den Forms-Dienst übergeben werden soll. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das XML-Dokument darstellt, das Formulardaten enthält, die mithilfe des Konstruktors an den Forms-Dienst übergeben werden sollen. Übergeben Sie einen string -Wert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `PDFFormRenderSpec`-Objekt, mit dem Laufzeitoptionen festgelegt werden. Rufen Sie die `setGenerateServerAppearance` -Methode des Objekts `PDFFormRenderSpec` auf und übergeben Sie `true`.
   * Rufen Sie die `renderPDFForm2` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

      * Ein `com.adobe.idp.Document` -Objekt, das das zu rendernde PDF-Formular enthält.
      * Ein `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen.
      * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert.
      * Ein `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind. Sie können `null` für diesen Parameterwert angeben.
      * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

      Die `renderPDFForm2`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält

   * Rufen Sie das PDF-Formular ab, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das das interaktive Formular darstellt.


1. Interaktives Formular unterschreiben

   Signieren Sie das PDF-Dokument, indem Sie die `sign` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` -Objekt, das das zu signierende PDF-Dokument darstellt. Stellen Sie sicher, dass dieses Objekt das Objekt `com.adobe.idp.Document` ist, das vom Forms-Dienst abgerufen wurde.
   * Ein string -Wert, der den Namen des signierten Signaturfelds darstellt.
   * Ein `Credential` -Objekt, das die Berechtigung darstellt, die zum digitalen Signieren des PDF-Dokuments verwendet wird. Erstellen Sie ein `Credential` -Objekt, indem Sie die statische `getInstance` -Methode des `Credential` -Objekts aufrufen. Übergeben Sie einen string -Wert, der den Alias-Wert angibt, der der Sicherheitsberechtigung entspricht.
   * Ein `HashAlgorithm` -Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein string -Wert, der den Grund darstellt, aus dem das PDF-Dokument digital signiert wurde.
   * Ein string -Wert, der die Kontaktinformationen des Signierers darstellt.
   * Ein `PDFSignatureAppearanceOptions` -Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um ein benutzerdefiniertes Logo zu einer digitalen Signatur hinzuzufügen.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll.
   * Ein `OCSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `CRLPreferences` -Objekt, das Voreinstellungen für Zertifikatsperrlisten (CRL) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `TSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein.

   Die `sign`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateinamenerweiterung .pdf lautet.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf und übergeben Sie `java.io.File`zum Kopieren des Inhalts des `Document`-Objekts in die Datei. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `sign`-Methode zurückgegeben wurde.

**Siehe auch**

[Digital Signing Interactive Forms](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Schnellstart (SOAP-Modus): PDF-Dokument mit der Java-API digital signieren](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Interaktives Formular mit der Webdienst-API {#digitally-sign-an-interactive-form-using-the-web-service-api} digital signieren

Interaktives Formular mit der Forms- und Signatur-API (Webdienst) digital signieren:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Client-Anwendung zwei AEM Forms-Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Signature-Dienst verknüpft ist: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für die Dienstreferenz, die mit dem Forms-Dienst verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Da der Datentyp `BLOB` für beide Dienstverweise gleich ist, müssen Sie den Datentyp `BLOB` bei Verwendung vollständig qualifizieren. Im entsprechenden Webdienst-Schnellstart sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Forms- und Signaturclient

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den Forms-Dienstclient.

1. Abrufen des interaktiven Formulars mit dem Forms-Dienst

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines signierten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu signierenden PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort der XML-Datei, die Formulardaten enthält, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `PDFFormRenderSpec`-Objekt, mit dem Laufzeitoptionen festgelegt werden. Weisen Sie den Wert `true` dem `PDFFormRenderSpec` -Objektfeld `generateServerAppearance` zu.
   * Rufen Sie die `renderPDFForm2` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

      * Ein `BLOB` -Objekt, das das zu rendernde PDF-Formular enthält.
      * Ein `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen.
      * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert.
      * Ein `URLSpec` -Objekt, das URI-Werte enthält, die für den Forms-Dienst erforderlich sind. Sie können `null` für diesen Parameterwert angeben.
      * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
      * Ein long -Ausgabeparameter, mit dem die Anzahl der Seiten im Formular gespeichert wird.
      * Ein string -Ausgabeparameter, der für den Gebietsschema-Wert verwendet wird.
      * Ein `FormResult` -Wert, der ein Ausgabeparameter ist, der zum Speichern des interaktiven Formulars verwendet wird.
   * Rufen Sie das PDF-Formular ab, indem Sie das `outputContent` -Feld des Objekts `FormsResult` aufrufen. Dieses Feld speichert ein `BLOB`-Objekt, das das interaktive Formular darstellt.


1. Interaktives Formular unterschreiben

   Signieren Sie das PDF-Dokument, indem Sie die `sign` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB` -Objekt, das das zu signierende PDF-Dokument darstellt. Verwenden Sie die vom Forms-Dienst zurückgegebene `BLOB`-Instanz.
   * Ein string -Wert, der den Namen des signierten Signaturfelds darstellt.
   * Ein `Credential` -Objekt, das die Berechtigung darstellt, die zum digitalen Signieren des PDF-Dokuments verwendet wird. Erstellen Sie ein `Credential` -Objekt mithilfe des zugehörigen Konstruktors und geben Sie den Alias an, indem Sie der `alias` -Eigenschaft des Objekts `Credential` einen Wert zuweisen.
   * Ein `HashAlgorithm` -Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein string -Wert, der den Grund darstellt, aus dem das PDF-Dokument digital signiert wurde.
   * Ein string -Wert, der den Standort des Signierers darstellt.
   * Ein string -Wert, der die Kontaktinformationen des Signierers darstellt.
   * Ein `PDFSignatureAppearanceOptions` -Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um ein benutzerdefiniertes Logo zu einer digitalen Signatur hinzuzufügen.
   * Ein `System.Boolean` -Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `OCSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben. Weitere Informationen zu diesem Objekt finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences` -Objekt, das Voreinstellungen für Zertifikatsperrlisten (CRL) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `TSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein.

   Die `sign`-Methode gibt ein `BLOB`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `sign` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Digital Signing Interactive Forms](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## PDF-Dokumente zertifizieren {#certifying-pdf-documents}

Sie können ein PDF-Dokument absichern, indem Sie es mit einem bestimmten Signaturtyp (einer zertifizierten Signatur) zertifizieren. Eine zertifizierte Signatur entscheidet sich wie folgt von einer digitalen Signatur:

* Sie muss die erste, auf das PDF-Dokument angewendete Signatur sein. Das heißt, zum Zeitpunkt, zu dem die zertifizierte Signatur angewendet wird, müssen alle anderen Signaturfelder im Dokument unsigniert sein. In einem PDF-Dokument ist nur eine zertifizierte Signatur zulässig. Wenn Sie ein PDF-Dokument signieren und zertifizieren möchten, müssen Sie es vor dem signieren zertifizieren. Nach dem Zertifizieren eines PDF-Dokuments können Sie weitere Signaturfelder digital signieren.
* Der Autor oder Ersteller des Dokuments kann festlegen, dass das Dokument auf bestimmte Arten modifiziert werden kann, ohne dass die zertifizierte Signatur ungültig wird. Beispiel: Das Ausfüllen von Formularen oder Einfügen von Kommentaren im Dokument kann zulässig sein. Wenn der Autor festlegt, dass eine bestimmte Änderung nicht zulässig ist, Acrobat verhindert, dass Benutzer das Dokument auf diese Weise ändern. Wenn solche Änderungen vorgenommen werden, etwa durch Verwenden einer anderen Anwendung, wird die zertifizierte Signatur ungültig und Acrobat gibt eine Warnung aus, wenn ein Benutzer das Dokument öffnet. (Bei nicht zertifizierten Signaturen werden Änderungen nicht verhindert und Bearbeitungsvorgänge führen nicht dazu, dass die ursprüngliche Signatur ungültig wird.)
* Zum Zeitpunkt des Signierens wird das Dokument auf bestimmte Typen von Inhalt überprüft, durch die die Inhalte eines Dokuments mehrdeutig oder irreführend werden könnten. Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Eine Erläuterung (gültige Beglaubigung) zu solchen Inhalten kann bereitgestellt werden.

Sie können PDF-Dokumente programmgesteuert mit der Signature-Dienst-Java-API oder der Signature-Webdienst-API zertifizieren. Beim Zertifizieren eines PDF-Dokuments müssen Sie auf eine Sicherheitsberechtigung verweisen, die im Berechtigungsdienst vorhanden ist. Informationen zu den Sicherheitsberechtigungen finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

>[!NOTE]
>
>Wenn beim Zertifizieren und Signieren desselben PDF-Dokuments die Zertifizierungssignatur nicht als vertrauenswürdig eingestuft wird, wird beim Öffnen des PDF-Dokuments in Acrobat oder Adobe Reader neben der ersten Signatursignatur ein gelbes Dreieck angezeigt. Die Zertifizierungssignatur muss vertrauenswürdig sein, um dies zu vermeiden.

>[!NOTE]
>
>Wenn Sie zum Signieren oder Zertifizieren eines PDF-Dokuments eine Cipher nShield-HSM-Berechtigung verwenden, können die neuen Anmeldedaten erst verwendet werden, nachdem der J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt wird, neu gestartet wurde. Sie können jedoch einen Konfigurationswert festlegen, der dazu führt, dass der Vorgang zum Signieren oder Zertifizieren funktioniert, ohne den J2EE-Anwendungsserver neu zu starten.

Sie können den folgenden Konfigurationswert zur Datei &quot;cknfastrc&quot;hinzufügen, die sich unter /opt/nfast/cknfastrc (oder c:\nfast\cknfastrc) befindet:

```shell
    CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nachdem Sie diesen Konfigurationswert zur cknfastrc-Datei hinzugefügt haben, können die neuen Anmeldedaten verwendet werden, ohne den J2EE-Anwendungsserver neu zu starten.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Zertifizieren eines Dokuments finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Führen Sie zum Zertifizieren eines PDF-Dokuments die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das zu zertifizierende PDF-Dokument ab.
1. Zertifizieren Sie das PDF-Dokument.
1. Speichern Sie das zertifizierte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signaturvorgang programmgesteuert ausführen können, müssen Sie einen Signature-Client erstellen.

**PDF-Dokument zum Zertifizieren abrufen**

Zum Zertifizieren eines PDF-Dokuments müssen Sie ein PDF-Dokument abrufen, das ein Signaturfeld enthält. Wenn ein PDF-Dokument kein Signaturfeld enthält, kann es nicht zertifiziert werden. Ein Signaturfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden. Informationen zum programmgesteuerten Hinzufügen eines Signaturfelds finden Sie unter [Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields).

**PDF-Dokument zertifizieren**

Zum erfolgreichen Zertifizieren eines PDF-Dokuments benötigen Sie die folgenden Eingabewerte, die vom Signature-Dienst zum Zertifizieren eines PDF-Dokuments verwendet werden:

* **PDF-Dokument**: Ein PDF-Dokument, das ein Signaturfeld enthält. Dies ist ein Formularfeld, das eine grafische Darstellung der zertifizierten Signatur enthält. Ein PDF-Dokument muss ein Signaturfeld enthalten, bevor es zertifiziert werden kann. Ein Signaturfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden. (Siehe [Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields).)
* **Name des Signaturfelds**: Der vollständig qualifizierte Name des zertifizierten Signaturfelds. Der folgende Wert ist ein Beispiel: `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds kann auch der Teilname des Signaturfelds verwendet werden: `SignatureField3[3]`. Wenn für den Feldnamen ein Nullwert übergeben wird, wird ein unsichtbares Signaturfeld dynamisch erstellt und zertifiziert.
* **Sicherheitsberechtigungen**: Eine Berechtigung, die zum Zertifizieren des PDF-Dokuments verwendet wird. Diese Sicherheitsberechtigung enthält ein Kennwort und einen Alias, der mit einem Alias übereinstimmen muss, der in der Berechtigung angezeigt wird, die sich im Credential-Dienst befindet. Der Alias ist ein Verweis auf eine tatsächliche Berechtigung, die sich in einer PKCS#12-Datei (mit .pfx-Erweiterung) oder einem Hardware-Sicherheitsmodul (HSM) befinden kann.
* **Hash-Algorithmus**: Ein Hash-Algorithmus zur Erfassung des PDF-Dokuments.
* **Grund für die Unterzeichnung**: Ein Wert, der in Acrobat oder Adobe Reader angezeigt wird, sodass andere Benutzer wissen, warum das PDF-Dokument zertifiziert wurde.
* **Standort des Signierers**: Der Speicherort des Signierers, der durch die Berechtigung angegeben wurde.
* **Kontaktangaben**: Kontaktinformationen des Unterzeichners, wie Adresse und Telefonnummer.
* **Berechtigungsinformationen**: Berechtigungen, die steuern, welche Aktionen ein Endbenutzer für ein Dokument ausführen kann, ohne dass die zertifizierte Signatur ungültig ist. Beispielsweise können Sie die Berechtigung so festlegen, dass jede Änderung am PDF-Dokument dazu führt, dass die zertifizierte Signatur ungültig wird.
* **Rechtliche Erläuterung**: Wenn ein Dokument zertifiziert ist, wird es automatisch auf bestimmte Inhaltstypen überprüft, die den Inhalt eines Dokuments mehrdeutig oder irreführend machen könnten. Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Der Scanvorgang erzeugt Warnungen zu diesen Inhaltstypen. Dieser Wert bietet eine zusätzliche Erläuterung des Inhalts, der möglicherweise Warnungen generiert hat.
* **Aussehen-Optionen**: Optionen, die das Erscheinungsbild der zertifizierten Signatur steuern. Beispielsweise kann die zertifizierte Signatur Datumsangaben anzeigen.
* **Sperrprüfung**: Dieser Wert gibt an, ob die Sperrprüfung für das Zertifikat des Signierers durchgeführt wird. Die Standardeinstellung von `false` bedeutet, dass die Sperrprüfung nicht durchgeführt wird.
* **OCSP-Einstellungen**: Unterstützung von Einstellungen für das Online Certificate Status Protocol (OCSP), das Informationen zum Status der Berechtigung bereitstellt, die zum Zertifizieren des PDF-Dokuments verwendet wird. Sie können beispielsweise die URL des Servers angeben, der Informationen zu den Anmeldedaten bereitstellt, die Sie zum Anmelden beim PDF-Dokument verwenden.
* **CRL-Einstellungen**: Einstellungen für die Voreinstellungen für Zertifikatsperrliste (CRL), wenn die Sperrprüfung durchgeführt wird. Sie können beispielsweise festlegen, dass immer geprüft werden soll, ob eine Berechtigung widerrufen wurde.
* **Zeitstempel**: Einstellungen, die Zeitstempelinformationen definieren, die auf die zertifizierte Signatur angewendet werden. Ein Zeitstempel gibt an, dass bestimmte Daten vor einer bestimmten Zeit ermittelt wurden. Dieses Wissen hilft beim Aufbau einer vertrauensvollen Beziehung zwischen dem Unterzeichner und dem Prüfer.

**Zertifiziertes PDF-Dokument als PDF-Datei speichern**

Nachdem der Signature-Dienst das PDF-Dokument zertifiziert hat, können Sie es als PDF-Datei speichern, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[PDF-Dokumente mit der Java-API zertifizieren](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-java-api)

[PDF-Dokumente mit der Webdienst-API zertifizieren](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

### Zertifizieren von PDF-Dokumenten mit der Java-API {#certify-pdf-documents-using-the-java-api}

Zertifizieren Sie ein PDF-Dokument mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-signatures-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument zum Zertifizieren abrufen

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu zertifizierende PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PDF-Dokument zertifizieren

   Zertifizieren Sie das PDF-Dokument, indem Sie die `certify` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das zu zertifizierende PDF-Dokument darstellt.
   * Ein string -Wert für den Namen des Signaturfelds, das die Signatur enthalten soll.
   * Ein `Credential` -Objekt, das die Berechtigung darstellt, die zum Zertifizieren des PDF-Dokuments verwendet wird. Erstellen Sie ein `Credential` -Objekt, indem Sie die statische `getInstance` -Methode des Objekts `Credential` aufrufen und einen string -Wert übergeben, der den Aliaswert angibt, der der Sicherheitsberechtigung entspricht.
   * Ein `HashAlgorithm` -Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet wird. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein string -Wert, der den Grund für die Zertifizierung des PDF-Dokuments darstellt.
   * Ein string -Wert, der die Kontaktinformationen des Signierers darstellt.
   * Ein `MDPPermissions` -Objekt, das Aktionen angibt, die für das PDF-Dokument ausgeführt werden können, das die Signatur ungültig macht.
   * Ein `PDFSignatureAppearanceOptions` -Objekt, das das Erscheinungsbild der zertifizierten Signatur steuert. Ändern Sie bei Bedarf das Erscheinungsbild der Signatur, indem Sie eine Methode aufrufen, z. B. `setShowDate`.
   * Ein string -Wert, der erklärt, durch welche Aktionen die Signatur ungültig gemacht wird.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `java.lang.Boolean` -Objekt, das angibt, ob das zertifizierte Signaturfeld gesperrt ist. Wenn das Feld gesperrt ist, wird das Signaturfeld als schreibgeschützt markiert, seine Eigenschaften können nicht geändert werden und es kann von niemandem gelöscht werden, der nicht über die erforderlichen Berechtigungen verfügt. Der Standardwert lautet `false`.
   * Ein `OCSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben. Weitere Informationen zu diesem Objekt finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences` -Objekt, das Voreinstellungen für Zertifikatsperrlisten (CRL) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `TSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Nachdem Sie beispielsweise ein `TSPPreferences` -Objekt erstellt haben, können Sie die URL des TSP-Servers festlegen, indem Sie die `setTspServerURL` -Methode des Objekts `TSPPreferences` aufrufen. Dieser Parameter ist optional und kann `null` sein. Weitere Informationen finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

   Die `certify`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das zertifizierte PDF-Dokument darstellt.

1. Zertifiziertes PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um den Inhalt des `com.adobe.idp.Document` -Objekts in die Datei zu kopieren.

**Siehe auch**

[PDF-Dokumente zertifizieren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Schnellstart (SOAP-Modus): Zertifizieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zertifizieren von PDF-Dokumenten mithilfe der Webdienst-API {#certify-pdf-documents-using-the-web-service-api}

Zertifizieren Sie ein PDF-Dokument mithilfe der Signature-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument zum Zertifizieren abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines zertifizierten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu zertifizierenden PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Datenelement dem Inhalt des Byte-Arrays zuweisen.

1. PDF-Dokument zertifizieren

   Zertifizieren Sie das PDF-Dokument, indem Sie die `certify` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das zu zertifizierende PDF-Dokument darstellt.
   * Ein string -Wert für den Namen des Signaturfelds, das die Signatur enthalten soll.
   * Ein `Credential` -Objekt, das die Berechtigung darstellt, die zum Zertifizieren des PDF-Dokuments verwendet wird. Erstellen Sie ein `Credential` -Objekt mithilfe des zugehörigen Konstruktors und geben Sie den Alias an, indem Sie der `alias` -Eigenschaft des Objekts `Credential` einen Wert zuweisen.
   * Ein `HashAlgorithm` -Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet wird. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein string -Wert, der den Grund für die Zertifizierung des PDF-Dokuments darstellt.
   * Ein string -Wert, der den Standort des Signierers darstellt.
   * Ein string -Wert, der die Kontaktinformationen des Signierers darstellt.
   * Das statische Datenelement eines `MDPPermissions` -Objekts, das Aktionen angibt, die für das PDF-Dokument ausgeführt werden können, durch das die Signatur ungültig gemacht wird.
   * Ein boolescher Wert, der angibt, ob das `MDPPermissions`-Objekt verwendet werden soll, das als vorheriger Parameterwert übergeben wurde.
   * Ein string -Wert, der erklärt, durch welche Aktionen die Signatur ungültig gemacht wird.
   * Ein `PDFSignatureAppearanceOptions` -Objekt, das das Erscheinungsbild der zertifizierten Signatur steuert. Erstellen Sie ein Objekt `PDFSignatureAppearanceOptions`, indem Sie den Konstruktor verwenden. Sie können das Erscheinungsbild der Signatur ändern, indem Sie eines ihrer Datenelemente festlegen.
   * Ein `System.Boolean` -Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `System.Boolean` -Objekt, das angibt, ob das zertifizierte Signaturfeld gesperrt ist. Wenn das Feld gesperrt ist, wird das Signaturfeld als schreibgeschützt markiert, seine Eigenschaften können nicht geändert werden und es kann von niemandem gelöscht werden, der nicht über die erforderlichen Berechtigungen verfügt. Der Standardwert lautet `false`.
   * Ein `System.Boolean` -Objekt, das angibt, ob das Signaturfeld gesperrt ist. Das heißt, wenn Sie `true` an den vorherigen Parameter übergeben, dann übergeben Sie `true` an diesen Parameter.
   * Ein `OCSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert, das Informationen zum Status der Berechtigung bereitstellt, die zum Zertifizieren des PDF-Dokuments verwendet wird. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `CRLPreferences` -Objekt, das Voreinstellungen für Zertifikatsperrlisten (CRL) speichert. Wenn die Sperrprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `TSPPreferences` -Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Nachdem Sie beispielsweise ein `TSPPreferences` -Objekt erstellt haben, können Sie die URL des TSP festlegen, indem Sie das `tspServerURL` -Datenelement des Objekts `TSPPreferences` festlegen. Dieser Parameter ist optional und kann `null` sein.

   Die `certify`-Methode gibt ein `BLOB`-Objekt zurück, das das zertifizierte PDF-Dokument darstellt.

1. Zertifiziertes PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das das zertifizierte PDF-Dokument enthalten soll, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `certify` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `binaryData` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[PDF-Dokumente zertifizieren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Überprüfen digitaler Signaturen {#verifying-digital-signatures}

Digitale Signaturen können überprüft werden, um sicherzustellen, dass ein signiertes PDF-Dokument nicht geändert wurde und die digitale Signatur gültig ist. Beim Überprüfen einer digitalen Signatur können Sie den Status der Signatur und die Eigenschaften der Signatur überprüfen, z. B. die Identität des Signierers. Bevor Sie einer digitalen Signatur vertrauen, sollten Sie sie überprüfen. Verwenden Sie beim Überprüfen einer digitalen Signatur ein PDF-Dokument, das eine digitale Signatur enthält.

Angenommen, die Identität des Signierers ist unbekannt. Wenn Sie das PDF-Dokument in Acrobat öffnen, wird in einer Warnmeldung darauf hingewiesen, dass die Identität des Unterzeichners unbekannt ist, wie in der folgenden Abbildung dargestellt.

![vd_vd_verifysig](assets/vd_vd_verifysig.png)

Ebenso können Sie beim programmgesteuerten Überprüfen einer digitalen Signatur den Status der Identität des Signierers ermitteln. Wenn Sie beispielsweise die digitale Signatur in dem in der vorherigen Abbildung gezeigten Dokument überprüfen, wäre das Ergebnis, dass die Identität des Unterzeichners unbekannt ist.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Überprüfen digitaler Signaturen finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Führen Sie zum Überprüfen einer digitalen Signatur die folgenden Aufgaben aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das die zu überprüfende Signatur enthält.
1. Festlegen von PKI-Laufzeitoptionen.
1. Überprüfen Sie die digitale Signatur.
1. Bestimmen Sie den Status der Signatur.
1. Bestimmen Sie die Identität des Signierers.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert ausführen, erstellen Sie einen Signature-Dienstclient.

**PDF-Dokument abrufen, das die zu überprüfende Signatur enthält**

Um eine Signatur zu überprüfen, die zum digitalen Signieren oder Zertifizieren eines PDF-Dokuments verwendet wird, rufen Sie ein PDF-Dokument ab, das eine Signatur enthält.

**Festlegen von PKI-Laufzeitoptionen**

Legen Sie diese PKI-Laufzeitoptionen fest, die der Signature-Dienst beim Überprüfen von Signaturen in einem PDF-Dokument verwendet:

* Überprüfungszeit
* Sperrprüfung
* Zeitstempelwerte

Im Rahmen der Einstellung dieser Optionen können Sie den Überprüfungszeitpunkt festlegen. Sie können beispielsweise die aktuelle Zeit (die Zeit auf dem Computer des Validators) auswählen, die angibt, die aktuelle Zeit zu verwenden. Weitere Informationen zu den verschiedenen Zeitwerten finden Sie im Auflistungswert `VerificationTime` in der AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).[

Sie können auch angeben, ob im Rahmen des Überprüfungsprozesses eine Sperrprüfung durchgeführt werden soll. Sie können beispielsweise eine Sperrprüfung durchführen, um festzustellen, ob das Zertifikat gesperrt ist. Weitere Informationen zu den Optionen zur Prüfung von Sperren finden Sie unter dem Auflistungswert `RevocationCheckStyle` in der AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).[

Um eine Sperrprüfung für ein Zertifikat durchzuführen, geben Sie mithilfe eines `CRLOptionSpec` -Objekts eine URL für einen Zertifikatsperrlisten-Server (CRL) an. Wenn Sie jedoch keine URL für den CRL-Server angeben, ruft der Signature-Dienst die URL vom Zertifikat ab.

Anstelle eines CRL-Servers können Sie bei der Prüfung von Sperren einen OCSP-Server (Online Certificate Status Protocol) verwenden. Normalerweise wird bei Verwendung eines OCSP-Servers im Gegensatz zu einem CRL-Server die Sperrprüfung schneller durchgeführt. (Siehe [Online Certificate Status Protocol](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signature-Dienst mithilfe von Adobe Applications and Services verwendet. Wenn beispielsweise der OCSP-Server zuerst in Adobe Applications and Services festgelegt wird, wird der OCSP-Server überprüft, gefolgt vom CRL-Server.

Wenn Sie keine Sperrprüfung durchführen, überprüft der Signature-Dienst nicht, ob das Zertifikat gesperrt ist. Das heißt, CRL- und OCSP-Serverinformationen werden ignoriert.

>[!NOTE]
>
>Sie können die im Zertifikat angegebene URL überschreiben, indem Sie ein `CRLOptionSpec`- und ein `OCSPOptionSpec`-Objekt verwenden. Um beispielsweise den CRL-Server zu überschreiben, können Sie die `setLocalURI` -Methode des Objekts `CRLOptionSpec` aufrufen.

Beim Zeitstempel wird der Zeitpunkt verfolgt, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, kann es von niemandem geändert werden. Die Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mit einem `TSPOptionSpec` -Objekt festlegen. Sie können beispielsweise die URL eines Zeitstempelanbieter-Servers (TSP) angeben.

>[!NOTE]
>
>In den Schnellstarts für Java- und Webdienst wird die Verifizierungszeit auf `VerificationTime.CURRENT_TIME` und die Sperrprüfung auf `RevocationCheckStyle.BestEffort` gesetzt. Da keine CRL- oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem Zertifikat abgerufen.

**Digitale Signatur überprüfen**

Um eine Signatur erfolgreich zu überprüfen, geben Sie den vollständig qualifizierten Namen des Signaturfelds an, das die Signatur enthält, z. B. `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds können Sie auch den Teilnamen des Signaturfelds verwenden: `SignatureField3`.

Standardmäßig beschränkt der Signature-Dienst die Zeit, die ein Dokument nach der Validierung signiert werden kann, auf 65 Minuten. Wenn ein Benutzer versucht, eine Signatur zur aktuellen Zeit zu überprüfen, die Signaturzeit nach der aktuellen Zeit liegt und innerhalb von 65 Minuten liegt, erstellt der Signature-Dienst keinen Überprüfungsfehler.

>[!NOTE]
>
>Weitere Werte, die Sie beim Überprüfen einer Signatur benötigen, finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Status der Signatur bestimmen**

Beim Überprüfen einer digitalen Signatur können Sie den Status der Signatur überprüfen.

**Identität des Signierers bestimmen**

Sie können die Identität des Signierers bestimmen, bei dem es sich um einen der folgenden Werte handeln kann:

* **Unbekannt**: Dieser Signierer ist unbekannt, da die Signiererüberprüfung nicht durchgeführt werden kann.
* **Vertrauenswürdig**: Dieser Unterzeichner wird als vertrauenswürdig eingestuft.
* **Nicht vertrauenswürdig**: Dieser Unterzeichner wird nicht als vertrauenswürdig eingestuft.

**Siehe auch**

[Digitale Signaturen mithilfe der Java-API überprüfen](#verify-digital-signatures-using-the-java-api)

[Digitale Signaturen mithilfe der Webdienst-API überprüfen](#verify-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mithilfe der Java-API überprüfen {#verify-digital-signatures-using-the-java-api}

Überprüfen einer digitalen Signatur mithilfe der Signature Service-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-signatures-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das die zu überprüfende Signatur enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, das die Signatur enthält, die mithilfe des Konstruktors überprüft werden soll. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von PKI-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Verifizierungszeit fest, indem Sie die `setVerificationTime`-Methode des Objekts `PKIOptions` aufrufen und einen `VerificationTime`-Auflistungswert übergeben, der die Verifizierungszeit angibt.
   * Legen Sie die Option zur Prüfung von Sperren fest, indem Sie die `setRevocationCheckStyle`-Methode des Objekts `PKIOptions` aufrufen und einen `RevocationCheckStyle`-Auflistungswert übergeben, der angibt, ob eine Sperrprüfung durchgeführt werden soll.

1. Digitale Signatur überprüfen

   Überprüfen Sie die Signatur, indem Sie die `verify2`-Methode des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` -Objekt, das ein digital signiertes oder zertifiziertes PDF-Dokument enthält.
   * Ein string -Wert für den Signaturfeldnamen, der die zu verifizierende Signatur enthält.
   * Ein `PKIOptions` -Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können `null` für diesen Parameter angeben.

   Die `verify2`-Methode gibt ein `PDFSignatureVerificationInfo`-Objekt zurück, das Informationen enthält, die zum Überprüfen der digitalen Signatur verwendet werden können.

1. Status der Signatur bestimmen

   * Bestimmen Sie den Status der Signatur, indem Sie die `getStatus` -Methode des Objekts `PDFSignatureVerificationInfo` aufrufen. Diese Methode gibt ein `SignatureStatus` -Objekt zurück, das den Signaturstatus angibt. Wenn beispielsweise ein signiertes PDF-Dokument nicht geändert wird, gibt diese Methode `SignatureStatus.DocumentSigNoChanges` zurück.

1. Identität des Signierers bestimmen

   * Bestimmen Sie die Identität des Unterzeichners, indem Sie die `getSigner` -Methode des Objekts `PDFSignatureVerificationInfo` aufrufen. Diese Methode gibt ein `IdentityInformation` -Objekt zurück.
   * Rufen Sie die `getStatus` -Methode des Objekts `IdentityInformation` auf, um die Identität des Unterzeichners zu ermitteln. Diese Methode gibt einen Auflistungswert `IdentityStatus` zurück, der die Identität angibt. Wenn der Unterzeichner beispielsweise als vertrauenswürdig eingestuft wird, gibt diese Methode `IdentityStatus.TRUSTED` zurück.

**Siehe auch**

[Überprüfen digitaler Signaturen](#verify-digital-signatures-using-the-java-api)

[Schnellstart (SOAP-Modus): Digitale Signatur mithilfe der Java-API überprüfen](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mithilfe der Webdienst-API überprüfen {#verify-digital-signatures-using-the-web-service-api}

Überprüfen einer digitalen Signatur mithilfe der Signature Service-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen, das die zu überprüfende Signatur enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das eine zu verifizierende digitale oder zertifizierte Signatur enthält.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von PKI-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Verifizierungszeit fest, indem Sie dem `verificationTime`-Datenelement des `PKIOptions`-Objekts einen `VerificationTime`-Auflistungswert zuweisen, der die Verifizierungszeit angibt.
   * Legen Sie die Option zur Prüfung von Sperren fest, indem Sie dem `revocationCheckStyle`-Datenelement des `PKIOptions`-Objekts einen `RevocationCheckStyle`-Auflistungswert zuweisen, der angibt, ob eine Sperrprüfung durchgeführt werden soll.

1. Digitale Signatur überprüfen

   Überprüfen Sie die Signatur, indem Sie die `verify2`-Methode des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das ein digital signiertes oder zertifiziertes PDF-Dokument enthält.
   * Ein string -Wert für den Signaturfeldnamen, der die zu verifizierende Signatur enthält.
   * Ein `PKIOptions` -Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können `null` für diesen Parameter angeben.

   Die `verify2`-Methode gibt ein `PDFSignatureVerificationInfo`-Objekt zurück, das Informationen enthält, die zum Überprüfen der digitalen Signatur verwendet werden können.

1. Status der Signatur bestimmen

   Bestimmen Sie den Status der Signatur, indem Sie den Wert des `PDFSignatureVerificationInfo` -Datenelements des Objekts `status` abrufen. Dieses Datenelement speichert ein `SignatureStatus` -Objekt, das den Status der Signatur angibt. Wenn beispielsweise ein signiertes PDF-Dokument geändert wird, speichert das `status`-Datenelement den Wert `SignatureStatus.DocumentSigNoChanges`.

1. Identität des Signierers bestimmen

   * Bestimmen Sie die Identität des Unterzeichners, indem Sie den Wert des `PDFSignatureVerificationInfo` -Datenelements des Objekts `signer` abrufen. Dieses Element gibt ein `IdentityInformation` -Objekt zurück.
   * Rufen Sie das `IdentityInformation` -Datenelement des `status` -Objekts ab, um die Identität des Unterzeichners zu bestimmen. Dieses Datenelement gibt einen Auflistungswert `IdentityStatus` zurück, der die Identität angibt. Wenn der Unterzeichner beispielsweise vertrauenswürdig ist, gibt dieses Mitglied `IdentityStatus.TRUSTED` zurück.

**Siehe auch**

[Überprüfen digitaler Signaturen](#verify-digital-signatures-using-the-java-api)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Überprüfen mehrerer digitaler Signaturen {#verifying-multiple-digital-signatures}

AEM Forms bietet die Möglichkeit, alle digitalen Signaturen zu überprüfen, die sich in einem PDF-Dokument befinden. Angenommen, ein PDF-Dokument enthält mehrere digitale Signaturen als Ergebnis eines Geschäftsprozesses, der Signaturen von mehreren Signierern erfordert. Betrachten Sie beispielsweise eine Finanztransaktion, die sowohl die Unterschrift eines Kreditsachbediensteten als auch eines Managers erfordert. Sie können die Java-API oder Webdienst-API des Signature-Dienstes verwenden, um alle Signaturen im PDF-Dokument zu überprüfen. Beim Überprüfen mehrerer digitaler Signaturen können Sie den Status und die Eigenschaften jeder Signatur prüfen. Bevor Sie einer digitalen Signatur vertrauen, sollten Sie sie überprüfen. Es wird empfohlen, dass Sie mit der Verifizierung einer einzelnen digitalen Signatur vertraut sind.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Überprüfen digitaler Signaturen finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

Führen Sie die folgenden Aufgaben aus, um mehrere digitale Signaturen zu überprüfen:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das die zu überprüfenden Signaturen enthält.
1. Festlegen von PKI-Laufzeitoptionen.
1. Rufen Sie alle digitalen Signaturen ab.
1. Iterate through all signatures.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert ausführen, erstellen Sie einen Signature-Dienstclient.

**PDF-Dokument abrufen, das die zu überprüfenden Signaturen enthält**

Um eine Signatur zu überprüfen, die zum digitalen Signieren oder Zertifizieren eines PDF-Dokuments verwendet wird, rufen Sie ein PDF-Dokument ab, das eine Signatur enthält.

**PKI-Laufzeitoptionen festlegen**

Legen Sie diese PKI-Laufzeitoptionen fest, die der Signature-Dienst beim Überprüfen aller Signaturen in einem PDF-Dokument verwendet:

* Überprüfungszeit
* Sperrprüfung
* Zeitstempelwerte

Im Rahmen der Einstellung dieser Optionen können Sie den Überprüfungszeitpunkt festlegen. Sie können beispielsweise die aktuelle Zeit (die Zeit auf dem Computer des Validators) auswählen, die angibt, die aktuelle Zeit zu verwenden. Weitere Informationen zu den verschiedenen Zeitwerten finden Sie im Auflistungswert `VerificationTime` in der AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).[

Sie können auch angeben, ob im Rahmen des Überprüfungsprozesses eine Sperrprüfung durchgeführt werden soll. Sie können beispielsweise eine Sperrprüfung durchführen, um festzustellen, ob das Zertifikat gesperrt ist. Weitere Informationen zu den Optionen zur Prüfung von Sperren finden Sie unter dem Auflistungswert `RevocationCheckStyle` in der AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).[

Um eine Sperrprüfung für ein Zertifikat durchzuführen, geben Sie mithilfe eines `CRLOptionSpec` -Objekts eine URL für einen Zertifikatsperrlisten-Server (CRL) an. Wenn Sie jedoch keine URL für einen Zertifikatsperrlisten-Server angeben, ruft der Signature-Dienst die URL vom Zertifikat ab.

Anstelle eines CRL-Servers können Sie bei der Prüfung von Sperren einen OCSP-Server (Online Certificate Status Protocol) verwenden. In der Regel wird bei Verwendung eines OCSP-Servers anstelle eines CRL-Servers die Sperrprüfung schneller durchgeführt. (Siehe [Online Certificate Status Protocol](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signature-Dienst mithilfe von Adobe Applications and Services verwendet. Wenn beispielsweise der OCSP-Server zuerst in Adobe Applications and Services festgelegt wird, wird der OCSP-Server überprüft, gefolgt vom CRL-Server.

Wenn Sie keine Sperrprüfung durchführen, überprüft der Signature-Dienst nicht, ob das Zertifikat gesperrt ist. Das heißt, CRL- und OCSP-Serverinformationen werden ignoriert.

>[!NOTE]
>
>Sie können die im Zertifikat angegebene URL überschreiben, indem Sie ein `CRLOptionSpec`- und ein `OCSPOptionSpec`-Objekt verwenden. Um beispielsweise den CRL-Server zu überschreiben, können Sie die `setLocalURI` -Methode des Objekts `CRLOptionSpec` aufrufen.

Beim Zeitstempel wird der Zeitpunkt verfolgt, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, kann es von niemandem geändert werden. Die Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mithilfe eines `TSPOptionSpec` -Objekts festlegen. Sie können beispielsweise die URL eines Zeitstempelanbieter-Servers (TSP) angeben.

>[!NOTE]
>
>In den Schnellstarts für Java- und Webdienst wird die Verifizierungszeit auf `VerificationTime.CURRENT_TIME` und die Sperrprüfung auf `RevocationCheckStyle.BestEffort` gesetzt. Da keine CRL- oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem Zertifikat abgerufen.

**Alle digitalen Signaturen abrufen**

Rufen Sie zum Überprüfen aller digitalen Signaturen in einem PDF-Dokument die digitalen Signaturen aus dem PDF-Dokument ab. Alle Signaturen werden in einer Liste zurückgegeben. Überprüfen Sie im Rahmen der Überprüfung einer digitalen Signatur den Status der Signatur.

>[!NOTE]
>
>Im Gegensatz zur Überprüfung einer einzelnen digitalen Signatur müssen Sie bei der Überprüfung mehrerer Signaturen keinen Signaturfeldnamen angeben.

**Durchsuchen aller Signaturen**

Iterieren Sie durch jede Signatur. Das heißt, für jede Signatur überprüfen Sie die digitale Signatur und überprüfen Sie die Identität des Signierers und den Status jeder Signatur. (Siehe [Digitale Signaturen überprüfen](#verify-digital-signatures-using-the-java-api).)

>[!NOTE]
>
>Sie müssen nicht alle Signaturen durchlaufen, wenn die Anforderung das gesamte Dokument ist.

**Siehe auch**

[Mehrere digitale Signaturen mithilfe der Java-API überprüfen](#verify-digital-signatures-using-the-java-api)

[Mehrere digitale Signaturen mithilfe der Webdienst-API überprüfen](#verify-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mehrere digitale Signaturen mithilfe der Java-API {#verify-multiple-digital-signatures-using-the-java-api} überprüfen

Überprüfen mehrerer digitaler Signaturen mithilfe der Signature Service-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-signatures-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das die zu überprüfenden Signaturen enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, das mehrere digitale Signaturen enthält, die mithilfe des Konstruktors überprüft werden sollen. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Verifizierungszeit fest, indem Sie die `setVerificationTime`-Methode des Objekts `PKIOptions` aufrufen und einen `VerificationTime`-Auflistungswert übergeben, der die Verifizierungszeit angibt.
   * Legen Sie die Option zur Prüfung von Sperren fest, indem Sie die `setRevocationCheckStyle`-Methode des Objekts `PKIOptions` aufrufen und einen `RevocationCheckStyle`-Auflistungswert übergeben, der angibt, ob eine Sperrprüfung durchgeführt werden soll.

1. Alle digitalen Signaturen abrufen

   Rufen Sie die `verifyPDFDocument` -Methode des Objekts `SignatureServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` -Objekt, das ein PDF-Dokument mit mehreren digitalen Signaturen enthält.
   * Ein `PKIOptions` -Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können `null` für diesen Parameter angeben.

   Die `verifyPDFDocument`-Methode gibt ein `PDFDocumentVerificationInfo`-Objekt zurück, das Informationen über alle im PDF-Dokument enthaltenen digitalen Signaturen enthält.

1. Durchsuchen aller Signaturen

   * Iterieren Sie durch alle Signaturen, indem Sie die `getVerificationInfos` -Methode des Objekts `PDFDocumentVerificationInfo` aufrufen. Diese Methode gibt ein `java.util.List` -Objekt zurück, bei dem jedes Element ein `PDFSignatureVerificationInfo` -Objekt ist. Verwenden Sie ein `java.util.Iterator`-Objekt, um durch die Liste der Signaturen zu iterieren.
   * Mithilfe des Objekts `PDFSignatureVerificationInfo` können Sie Aufgaben wie die Bestimmung des Status der Signatur ausführen, indem Sie die `getStatus` -Methode des Objekts `PDFSignatureVerificationInfo` aufrufen. Diese Methode gibt ein `SignatureStatus` -Objekt zurück, dessen statisches Datenelement Sie über den Status der Signatur informiert. Wenn die Signatur beispielsweise unbekannt ist, gibt diese Methode `SignatureStatus.DocumentSignatureUnknown` zurück.

**Siehe auch**

[Überprüfen mehrerer digitaler Signaturen](#verifying-multiple-digital-signatures)

[Schnellstart (SOAP-Modus): Überprüfen mehrerer digitaler Signaturen mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Überprüfen digitaler Signaturen](#verify-digital-signatures-using-the-java-api)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mehrere digitale Signaturen mithilfe der Webdienst-API überprüfen {#verifying-multiple-digital-signatures-using-the-web-service-api}

Überprüfen mehrerer digitaler Signaturen mithilfe der Signature Service-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen, das die zu überprüfenden Signaturen enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt speichert ein PDF-Dokument, das mehrere zu verifizierende digitale Signaturen enthält.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Verifizierungszeit fest, indem Sie dem `verificationTime`-Datenelement des `PKIOptions`-Objekts einen `VerificationTime`-Auflistungswert zuweisen, der die Verifizierungszeit angibt.
   * Legen Sie die Option zur Prüfung von Sperren fest, indem Sie dem `revocationCheckStyle`-Datenelement des `PKIOptions`-Objekts einen `RevocationCheckStyle`-Auflistungswert zuweisen, der angibt, ob eine Sperrprüfung durchgeführt werden soll.

1. Alle digitalen Signaturen abrufen

   Rufen Sie die `verifyPDFDocument` -Methode des Objekts `SignatureServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` -Objekt, das ein PDF-Dokument mit mehreren digitalen Signaturen enthält.
   * Ein `PKIOptions` -Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können für diesen Parameter null angeben.

   Die `verifyPDFDocument`-Methode gibt ein `PDFDocumentVerificationInfo`-Objekt zurück, das Informationen über alle im PDF-Dokument enthaltenen digitalen Signaturen enthält.

1. Durchsuchen aller Signaturen

   * Iterieren Sie durch alle Signaturen, indem Sie das `verificationInfos`-Datenelement des `PDFDocumentVerificationInfo`-Objekts abrufen. Dieses Datenelement gibt ein `Object` -Array zurück, wobei jedes Element ein `PDFSignatureVerificationInfo` -Objekt ist.
   * Mithilfe des Objekts `PDFSignatureVerificationInfo` können Sie Aufgaben wie die Bestimmung des Status der Signatur ausführen, indem Sie das `status`-Datenelement des Objekts `PDFSignatureVerificationInfo` abrufen. Dieses Datenelement gibt ein `SignatureStatus` -Objekt zurück, dessen statisches Datenelement Sie über den Status der Signatur informiert. Wenn die Signatur beispielsweise unbekannt ist, gibt diese Methode `SignatureStatus.DocumentSignatureUnknown` zurück.

**Siehe auch**

[Überprüfen mehrerer digitaler Signaturen](#verifying-multiple-digital-signatures)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen digitaler Signaturen {#removing-digital-signatures}

Digitale Signaturen müssen aus einem Signaturfeld entfernt werden, bevor eine neuere digitale Signatur angewendet werden kann. Eine digitale Signatur kann nicht überschrieben werden. Wenn Sie versuchen, eine digitale Signatur auf ein Signaturfeld anzuwenden, das eine Signatur enthält, tritt eine Ausnahme auf.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Führen Sie die folgenden Aufgaben aus, um eine digitale Signatur aus einem Signaturfeld zu entfernen:

1. Projektdateien einschließen.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das eine zu entfernende Signatur enthält.
1. Entfernen Sie die digitale Signatur aus dem Signaturfeld.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument abrufen, das eine Signatur zum Entfernen enthält**

Um eine Signatur aus einem PDF-Dokument zu entfernen, müssen Sie ein PDF-Dokument abrufen, das eine Signatur enthält.

**Digitale Signatur aus dem Signaturfeld entfernen**

Um eine digitale Signatur erfolgreich aus einem PDF-Dokument zu entfernen, müssen Sie den Namen des Signaturfelds angeben, das die digitale Signatur enthält. Außerdem müssen Sie über die Berechtigung zum Entfernen der digitalen Signatur verfügen. Andernfalls tritt eine Ausnahme auf.

**PDF-Dokument als PDF-Datei speichern**

Nachdem der Signature-Dienst eine digitale Signatur aus einem Signaturfeld entfernt hat, können Sie das PDF-Dokument als PDF-Datei speichern, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Digitale Signaturen mithilfe der Java-API entfernen](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-java-api)

[Digitale Signaturen mithilfe der Webdienst-API entfernen](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

### Digitale Signaturen mithilfe der Java-API entfernen {#remove-digital-signatures-using-the-java-api}

Entfernen Sie eine digitale Signatur mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-signatures-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Signaturclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das eine Signatur zum Entfernen enthält

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das PDF-Dokument darstellt, das die zu entfernende Signatur enthält, indem Sie den Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Digitale Signatur aus dem Signaturfeld entfernen

   Entfernen Sie eine digitale Signatur aus einem Signaturfeld, indem Sie die `clearSignatureField` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` -Objekt, das das PDF-Dokument darstellt, das die zu entfernende Signatur enthält.
   * Ein string -Wert, der den Namen des Signaturfelds angibt, das die digitale Signatur enthält.

   Die `clearSignatureField`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das PDF-Dokument darstellt, aus dem die digitale Signatur entfernt wurde.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf. Übergeben Sie das `java.io.File`-Objekt, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `clearSignatureField`-Methode zurückgegeben wurde.

**Siehe auch**

[Entfernen digitaler Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Schnellstart (SOAP-Modus): Digitale Signatur mithilfe der Java-API entfernen](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mithilfe der Webdienst-API entfernen {#remove-digital-signatures-using-the-web-service-api}

Entfernen Sie eine digitale Signatur mithilfe der Signature-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `SignatureServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `SignatureServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument abrufen, das eine Signatur zum Entfernen enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das eine zu entfernende digitale Signatur enthält.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Digitale Signatur aus dem Signaturfeld entfernen

   Entfernen Sie die digitale Signatur, indem Sie die `clearSignatureField` -Methode des Objekts `SignatureServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB` -Objekt, das das signierte PDF-Dokument enthält.
   * Ein string -Wert für den Namen des Signaturfelds, das die zu entfernende digitale Signatur enthält.

   Die `clearSignatureField`-Methode gibt ein `BLOB`-Objekt zurück, das das PDF-Dokument darstellt, aus dem die digitale Signatur entfernt wurde.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das ein leeres Signaturfeld enthält, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `sign` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Entfernen digitaler Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
