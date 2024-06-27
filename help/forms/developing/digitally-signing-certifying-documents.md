---
title: Digitales Signieren und Zertifizieren von Dokumenten
description: Verwenden Sie den Signatur-Dienst, um einem PDF-Dokument digitale Signaturfelder hinzuzufügen oder sie zu löschen, die Namen von Signaturfeldern in einem PDF-Dokument abzurufen, Signaturfelder zu ändern, PDF-Dokumente digital zu signieren, PDF-Dokumente zu zertifizieren, digitale Signaturen in einem PDF-Dokument zu validieren, alle in einem PDF-Dokument enthaltenen digitalen Signaturen zu validieren oder eine digitale Signatur aus einem Signaturfeld zu entfernen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: c200f345-40ab-46fd-b6ed-f3af0a23796b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '16917'
ht-degree: 100%

---

# Digitales Signieren und Zertifizieren von Dokumenten {#digitally-signing-and-certifying-documents}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den Signature-Service**

Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfänger, für die dies vorgesehen ist, die Dokumente ändern können. Da Sicherheitsfunktionen auf das Dokument selbst angewendet werden, bleibt das Dokument für seinen gesamten Lebenszyklus sicher und kontrolliert. Ein Dokument bleibt außerhalb der Firewall sicher, wenn es offline heruntergeladen und an Ihr Unternehmen zurückgesendet wird.

>[!NOTE]
>
>Sie können einen benutzerdefinierten Signatur-Handler für den Signature-Service erstellen, der beim Aufrufen bestimmter Vorgänge aufgerufen wird, z. B. beim Signieren eines PDF-Dokuments.

**Signaturfeldnamen**

Bei einigen Vorgängen des Signature-Services müssen Sie den Namen des Signaturfelds angeben, für das ein Vorgang ausgeführt wird. Wenn beispielsweise ein PDF-Dokument signiert wird, geben Sie den Namen des Signaturfelds an, das signiert werden soll. Angenommen, der vollständige Name eines Signaturfelds lautet `form1[0].Form1[0].SignatureField1[0]`. Sie können `SignatureField1[0]` anstelle von `form1[0].Form1[0].SignatureField1[0]` angeben.

Manchmal wird aufgrund eines Konflikts das falsche Feld signiert (oder ein anderer Vorgang, der den Namen des Signaturfelds erfordert, mit dem falschen Feld durchgeführt). Dieser Konflikt entsteht, wenn der Name `SignatureField1[0]` an zwei oder mehr Stellen im selben PDF-Dokument erscheint. Angenommen, ein PDF-Dokument enthält zwei Unterschriftsfelder mit dem Namen `form1[0].Form1[0].SignatureField1[0]` und `form1[0].Form1[0].SubForm1[0].SignatureField1[0]`, und Sie geben `SignatureField1[0]` an. In diesem Fall signiert der Signature-Service das erste Signaturfeld, das er beim Iterieren durch alle Signaturfelder im Dokument findet.

Wenn sich mehrere Signaturfelder in einem PDF-Dokument befinden, wird empfohlen, die vollständigen Namen der Signaturfelder anzugeben. Das heißt, Sie sollten `form1[0].Form1[0].SignatureField1[0]` anstelle von `SignatureField1[0]` angeben.

Sie können die folgenden Aufgaben mithilfe des Signature-Services ausführen:

* Hinzufügen und Löschen von digitalen Signaturfeldern zu einem PDF-Dokument. (Siehe [Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields).)
* Abrufen der Namen der Signaturfelder in einem PDF-Dokument. (Siehe [Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names).)
* Ändern von Signaturfeldern. (Siehe [Ändern von Signaturfeldern](digitally-signing-certifying-documents.md#modifying-signature-fields).)
* Digitales Signieren von PDF-Dokumenten. (Siehe [Digitales Signieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)
* Zertifizieren von PDF-Dokumenten. (Siehe [Zertifizieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#certifying-pdf-documents).)
* Validieren digitaler Signaturen in einem PDF-Dokument. (Siehe [Überprüfen digitaler Signaturen](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Validieren aller digitalen Signaturen in einem PDF-Dokument. (Siehe [Überprüfen mehrerer digitaler Signaturen](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Entfernen einer digitalen Signatur aus einem Signaturfeld. (Siehe [Entfernen digitaler Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures).)

>[!NOTE]
>
>Weitere Informationen zum Signatur-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Hinzufügen von Signaturfeldern {#adding-signature-fields}

Digitale Signaturen werden in Signaturfeldern angezeigt, bei denen es sich um Formularfelder handelt, die eine grafische Darstellung der Signatur enthalten. Signaturfelder können sichtbar oder unsichtbar sein. Unterzeichnende können ein bereits vorhandenes Signaturfeld verwenden, oder ein Signaturfeld kann programmgesteuert hinzugefügt werden. In beiden Fällen muss das Signaturfeld vorhanden sein, bevor ein PDF-Dokument signiert werden kann.

Sie können ein Signaturfeld programmgesteuert hinzufügen, indem Sie die Signature-Dienst-Java-API oder die Signature-Webdienst-API verwenden. Sie können mehr als ein Signaturfeld zu einem PDF-Dokument hinzufügen. Jeder Signaturfeldname muss jedoch eindeutig sein.

>[!NOTE]
>
>Bei einigen PDF-Dokumenttypen können Sie kein Signaturfeld programmgesteuert hinzufügen. Weitere Informationen zum Signature-Service und zum Hinzufügen von Signaturfeldern finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein Signaturfeld zu einem PDF-Dokument hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signatur-Client.
1. Rufen Sie ein PDF-Dokument ab, dem ein Signaturfeld hinzugefügt wird.
1. Fügen Sie ein Signaturfeld hinzu.
1. Speichern Sie das Formular als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Service-Vorgang programmgesteuert ausführen können, müssen Sie einen Signature-Service-Client erstellen.

**Abrufen eines PDF-Dokuments, dem ein Signaturfeld hinzugefügt wird**

Abrufen eines PDF-Dokuments, dem ein Signaturfeld hinzugefügt wurde.

**Hinzufügen eines Signaturfelds**

Um einem PDF-Dokument erfolgreich ein Signaturfeld hinzuzufügen, geben Sie Koordinatenwerte an, die die Position des Signaturfelds angeben. (Wenn Sie ein unsichtbares Signaturfeld hinzufügen, sind diese Werte nicht erforderlich.) Sie können auch angeben, welche Felder im PDF-Dokument gesperrt werden, nachdem eine Signatur auf das Signaturfeld angewendet wurde.

**Speichern des PDF-Dokuments als PDF-Datei**

Nachdem der Signatur-Service ein Signaturfeld zum PDF-Dokument hinzugefügt hat, können Sie das Dokument als PDF-Datei speichern, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Digitales Signieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Hinzufügen von Signaturfeldern mithilfe der Java-API {#add-signature-fields-using-the-java-api}

Fügen Sie mithilfe der Signature-API (Java) ein Signaturfeld hinzu:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien, beispielsweise „adobe-signatures-client.jar“, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines PDF-Dokuments, dem ein Signaturfeld hinzugefügt wurde

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, dem ein Signaturfeld hinzugefügt wird. Verwenden Sie dazu seinen Konstruktor und übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Hinzufügen eines Signaturfeldes

   * Erstellen Sie ein `PositionRectangle`-Objekt, das die Position des Signaturfelds angibt, indem Sie seinen Konstruktor verwenden. Geben Sie im Konstruktor Koordinatenwerte an.
   * Erstellen Sie bei Bedarf ein `FieldMDPOptions`-Objekt, das die Felder angibt, die gesperrt werden, wenn eine digitale Signatur auf das Signaturfeld angewendet wird.
   * Fügen Sie ein Signaturfeld zu einem PDF-Dokument hinzu, indem Sie die Methode `addSignatureField` des `SignatureServiceClient`-Objekts verwenden und die folgenden Werte übergeben:

      * A `com.adobe.idp`. `Document`-Objekt, das das PDF-Dokument darstellt, dem ein Signaturfeld hinzugefügt wird.
      * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt.
      * Ein `java.lang.Integer`-Wert, der die Seitenzahl der Seite darstellt, zu der ein Signaturfeld hinzugefügt wird.
      * Ein `PositionRectangle`-Objekt, das die Position des Signaturfelds angibt.
      * Ein `FieldMDPOptions`-Objekt, das Felder im PDF-Dokument angibt, die gesperrt werden, nachdem eine digitale Signatur auf das Signaturfeld angewendet wurde. Dieser Parameterwert ist optional und Sie können `null` übergeben.

   * Ein `PDFSeedValueOptions`-Objekt, das verschiedene Laufzeitwerte angibt. Dieser Parameterwert ist optional und Sie können `null` übergeben.

     Die Methode `addSignatureField` gibt ein `com.adobe.idp` zurück. Ein `Document`-Objekt, das ein PDF-Dokument mit einem Signaturfeld darstellt.

   >[!NOTE]
   >
   >Sie können die Methode `addInvisibleSignatureField` des `SignatureServiceClient`-Objekts zum Hinzufügen eines unsichtbaren Signaturfelds aufrufen.

1. Das PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `com.adobe.idp` Rufen Sie die Methode `copyToFile` des `Document`-Objekts auf, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp` `Document`-Objekt verwenden, das von der `addSignatureField`-Methode zurückgegeben wurde.

**Siehe auch**

[Signature-Dienst-API Schnellstarts](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

### Hinzufügen von Signaturfeldern mit der Webdienst-API {#add-signature-fields-using-the-web-service-api}

So fügen Sie mithilfe der Signature-API (Webdienst) ein Signaturfeld hinzu:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie mithilfe des betreffenden Standardkonstruktors ein `SignatureServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Abrufen eines PDF-Dokuments, dem ein Signaturfeld hinzugefügt wurde

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` -Objekt wird zum Speichern des PDF-Dokuments verwendet, das ein Signaturfeld enthalten wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Hinzufügen eines Signaturfeldes

   Fügen Sie ein Signaturfeld zum PDF-Dokument hinzu, indem Sie die Methode `addSignatureField` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, welches das PDF-Dokument darstellt, dem ein Signaturfeld hinzugefügt werden soll.
   * Ein Zeichenkettenwert, der den Namen des Signaturfeldes angibt.
   * Ein Integer-Wert, der die Seitenzahl angibt, zu der ein Signaturfeld hinzugefügt wird.
   * Ein `PositionRect`-Objekt, das den Speicherort des Signaturfelds angibt.
   * Ein `FieldMDPOptions`-Objekt, das Felder im PDF-Dokument angibt, die gesperrt werden, nachdem eine digitale Signatur auf das Signaturfeld angewendet wurde. Dieser Parameterwert ist optional und Sie können `null` übergeben.
   * Ein `PDFSeedValueOptions`-Objekt, das verschiedene Laufzeitwerte angibt. Dieser Parameterwert ist optional und Sie können `null` übergeben.

   Die `addSignatureField`-Methode gibt ein `BLOB`-Objekt zurück, das ein mit einem Signaturfeld versehenes PDF-Dokument darstellt.

1. Das PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgewert übergeben, der den Dateispeicherort des PDF-Dokuments, welches das Signaturfeld enthalten soll, und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der `addSignatureField`-Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `binaryData` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Abrufen von Signaturfeldnamen {#retrieving-signature-field-names}

Sie können die Namen aller Signaturfelder abrufen, die sich in einem PDF-Dokument befinden, das Sie signieren oder zertifizieren möchten. Wenn Sie sich nicht sicher sind, welche Signaturfeldnamen sich in einem PDF-Dokument befinden, oder die Namen überprüfen möchten, können Sie sie programmgesteuert abrufen. Der Signature-Dienst gibt den vollqualifizierten Namen des Signaturfelds zurück, z. B. `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

>[!NOTE]
>
>Weitere Informationen über den Signature-Dienst finden Sie unter [Dienstverweise für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um Signaturfeldnamen abzurufen, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signatur-Client.
1. Rufen Sie das PDF-Dokument ab, das Signaturfelder enthält.
1. Rufen Sie die Namen der Signaturfelder ab.

**Binden Sie Projektdateien ein**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signature-Clients**

Bevor Sie einen Signature-Service-Vorgang programmgesteuert ausführen können, müssen Sie einen Signature-Service-Client erstellen.

**Abrufen des PDF-Dokuments, das Signaturfelder enthält**

Rufen Sie ein PDF-Dokument ab, das Signaturfelder enthält.

**Abrufen von Signaturfeldnamen**

Sie können die Namen von Signaturfeldern abrufen, nachdem Sie ein PDF-Dokument abgerufen haben, das ein oder mehrere Signaturfelder enthält.

**Siehe auch**

[Abrufen von Signaturfeldnamen mit der Java-API](digitally-signing-certifying-documents.md#retrieve-signature-field-names-using-the-java-api)

[Abrufen von Signaturfeldern mit der Webdienst-API](digitally-signing-certifying-documents.md#retrieve-signature-field-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields)

### Abrufen von Signaturfeldnamen mit der Java-API {#retrieve-signature-field-names-using-the-java-api}

Abrufen von Signaturfeldnamen mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien, beispielsweise „adobe-livecycle-client.jar“, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des PDF-Dokuments, das Signaturfelder enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, welches das PDF-Dokument darstellt, das Signaturfelder enthält, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Abrufen der Signaturfeldnamen

   * Rufen Sie die Namen der Signaturfelder ab, indem Sie die Methode `getSignatureFieldList` des `SignatureServiceClient`-Objekts aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das PDF-Dokument mit den Signaturfeldern enthält. Diese Methode gibt eine `java.util.List` -Objekt zurück, in dem jedes Element eine `PDFSignatureField` -Objekt enthält. Mit diesem Objekt können Sie zusätzliche Informationen zu einem Signaturfeld abrufen, beispielsweise ob es sichtbar ist.
   * Iterieren Sie durch das `java.util.List`-Objekt, um festzustellen, ob es Signaturfeldnamen gibt. Für jedes Signaturfeld im PDF-Dokument können Sie ein separates `PDFSignatureField`-Objekt erhalten. Um den Namen des Signaturfelds zu erhalten, rufen Sie die Methode `getName` des `PDFSignatureField`-Objekts auf. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Signaturfeldnamen angibt.

**Siehe auch**

[Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Schnellstart (SOAP-Modus): Abrufen von Signaturfeldnamen mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Abrufen von Signaturfeldern mit der Webdienst-API {#retrieve-signature-field-using-the-web-service-api}

Rufen Sie Signaturfeldnamen mit der Signature-API (Webdienst) ab:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie mithilfe des betreffenden Standardkonstruktors ein `SignatureServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Abrufen des PDF-Dokuments, das Signaturfelder enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des PDF-Dokuments verwendet, das Signaturfelder enthält.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt durch Zuweisen des Inhalts des Byte-Arrays zu seinem Feld `MTOM`.

1. Abrufen der Signaturfeldnamen

   * Rufen Sie die Namen der Signaturfelder ab, indem Sie die Methode `getSignatureFieldList` des `SignatureServiceClient`-Objekts abrufen und das `BLOB`-Objekt übergeben, das das PDF-Dokument mit Signaturfehldern enthält. Diese Methode gibt ein `MyArrayOfPDFSignatureField`-Sammlungsobjekt zurück, in dem jedes Element ein `PDFSignatureField`-Objekt enthält.
   * Gehen Sie schrittweise durch das `MyArrayOfPDFSignatureField`-Objekt, um festzustellen, ob Signaturfeldnamen vorhanden sind. Für jedes Signaturfeld im PDF-Dokument können Sie ein `PDFSignatureField`-Objekt erhalten. Um den Namen des Signaturfelds abzurufen, rufen Sie die Methode `getName` des `PDFSignatureField`-Objekts auf. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Signaturfeldnamen angibt.

**Siehe auch**

[Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Ändern von Signaturfeldern {#modifying-signature-fields}

Sie können Signaturfelder in einem PDF-Dokument ändern, indem Sie die Java-API und die Web-Service-API verwenden. Das Ändern eines Signaturfelds umfasst das Manipulieren seiner Signaturfeldsperre- oder Seed-Wert-Lexikonwerte.

Ein *Feldsperre-Wörterbuch* gibt eine Liste von Feldern an, die gesperrt werden, wenn das Signaturfeld signiert wird. Ein gesperrtes Feld verhindert, dass Benutzer Änderungen an dem Feld vornehmen. Ein *Seed-Wert-Wörterbuch* enthält Einschränkungsinformationen, die zum Zeitpunkt der Anwendung der Signatur verwendet werden. Beispiel: Sie können die Berechtigungen ändern, die Aktionen steuern, die auftreten können, ohne dass eine Signatur ungültig wird.

Durch Ändern eines vorhandenen Signaturfelds können Sie das PDF-Dokument so bearbeiten, dass es die sich ändernden Geschäftsanforderungen widerspiegelt. Beispiel: Eine neue Geschäftsanforderung erfordert das Sperren aller Felder eines Dokuments, nachdem es signiert wurde.

In diesem Abschnitt wird beschrieben, wie Sie ein Signaturfeld ändern, indem Sie sowohl die Werte des Feldsperre-Wörterbuchs als auch des Seed-Wert-Wörterbuchs ändern. Änderungen am Signaturfeldsperre-Wörterbuch führen dazu, dass alle Felder im PDF-Dokument gesperrt werden, wenn ein Signaturfeld signiert wird. Änderungen am Seed-Wert-Wörterbuch verbieten bestimmte Arten von Änderungen am Dokument.

>[!NOTE]
>
>Weitere Informationen zum Signature-Service und zum Ändern von Signaturfeldern finden Sie unter [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um Signaturfelder in einem PDF-Dokument zu ändern, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signatur-Client.
1. Rufen Sie das PDF-Dokument ab, das das zu ändernde Signaturfeld enthält.
1. Legen Sie Wörterbuchwerte fest.
1. Klicken Sie auf das Signaturfeld.
1. Speichern Sie das Formular als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehung von LiveCycle Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Service-Vorgang programmgesteuert ausführen können, müssen Sie einen Signature-Service-Client erstellen.

**Abrufen des PDF-Dokuments, das das zu ändernde Signaturfeld enthält**

Rufen Sie ein PDF-Dokument ab, das das zu ändernde Signaturfeld enthält.

**Festlegen von Wörterbuchwerten**

Um ein Signaturfeld zu ändern, weisen Sie seinem Feldsperre- oder Seed-Wert-Wörterbuch Werte zu. Das Festlegen von Signaturfeldsperre-Wörterbuchwerten umfasst das Angeben von PDF-Dokumentfeldern, die beim Signieren des Signaturfelds gesperrt werden. (In diesem Abschnitt wird beschrieben, wie Sie alle Felder sperren.)

Die folgenden Seed-Wert-Wörterbuchwerte können festgelegt werden:

* **Sperrprüfung**: Gibt an, ob eine Sperrprüfung durchgeführt wird, wenn eine Signatur auf das Signaturfeld angewendet wird.
* **Zertifikatoptionen**: Weist dem Seed-Wert-Wörterbuch des Zertifikats Werte zu. Bevor Sie Zertifikatoptionen angeben, sollten Sie sich mit einem Seed-Wert-Wörterbuch des Zertifikats vertraut machen. (Siehe [PDF-Verweis](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Digest-Optionen**: Weist Digest-Algorithmen zu, die zum Signieren verwendet werden. Gültige Werte sind SHA1, SHA256, SHA384, SHA512 und RIPEMD160.
* **Filter**: Gibt den Filter an, der mit dem Signaturfeld verwendet wird. Sie können beispielsweise den Adobe.PPKLite-Filter verwenden. (Siehe [PDF-Verweis](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Flag-Optionen**: Gibt die Markierungswerte an, die mit diesem Signaturfeld verbunden sind. Ein Wert von 1 bedeutet, dass ein Unterzeichner nur die angegebenen Werte für den Eintrag verwenden darf. Ein Wert von 0 bedeutet, dass andere Werte zulässig sind. Hier sind die Bit-Positionen:

   * **1 (Filter):** Der Signatur-Handler, der zum Signieren des Signaturfeldes verwendet werden soll
   * **2 (SubFilter):** Ein Array von Namen, die für das Signieren gültige Kodierungen angeben
   * **3 (V)**: Die minimal erforderliche Versionsnummer des Signaturhandlers, der zum Signieren des Signaturfeldes verwendet werden soll
   * **4 (Gründe):** Ein Array von Zeichenfolgen, die mögliche Gründe für das Signieren eines Dokuments angeben
   * **5 (PDFLegalWarnings):** Ein Array von Zeichenfolgen, die mögliche rechtliche Bescheinigungen angeben

* **Rechtliche Bescheinigungen**: Wenn ein Dokument zertifiziert wird, wird es automatisch auf bestimmte Arten von Inhalten gescannt, die den sichtbaren Inhalt eines Dokuments mehrdeutig oder irreführend machen können. Beispielsweise kann eine Anmerkung einen Text verdecken, der für das Verständnis dessen, was zertifiziert werden soll, wichtig ist. Der Scanvorgang erzeugt Warnungen, die auf das Vorhandensein dieser Art von Inhalten hinweisen. Außerdem wird eine ergänzende Erklärung zu den Inhalten gegeben, die möglicherweise Warnungen ausgelöst haben.
* **Berechtigungen**: Gibt die Berechtigungen an, die für ein PDF-Dokument verwendet werden können, ohne dass die Signatur ungültig wird.
* **Gründe**: Gibt Gründe an, warum dieses Dokument signiert werden muss.
* **Zeitstempel**: Legt Optionen für den Zeitstempel fest. Sie können beispielsweise die URL des verwendeten Zeitstempelservers festlegen.
* **Version**: Gibt die Mindestversionsnummer des Signaturhandlers an, der zum Signieren des Signaturfelds verwendet werden soll.

**Ändern des Signaturfelds**

Nachdem Sie einen Signature-Dienst-Client erstellt, ddas PDF-Dokument mit dem zu ändernden Signaturfeld abgerufen und Wörterbuchwerte festgelegt haben, können Sie den Signature-Dienst anweisen, das Signaturfeld zu ändern. Der Signature-Dienst gibt dann ein PDF-Dokument zurück, das das geänderte Signaturfeld enthält. Das ursprüngliche PDF-Dokument ist nicht betroffen.

**Das PDF-Dokument als PDF-Datei speichern**

Speichern Sie das PDF-Dokument mit dem geänderten Signaturfeld als PDF-Datei, damit die Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signature-Dienst-API Schnellstarts](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

[Digitales Signieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Ändern von Signaturfeldern mit der Java-API {#modify-signature-fields-using-the-java-api}

Ändern eines Signaturfeld mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie JAR-Dateien, beispielsweise „adobe-signatures-client.jar“, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des PDF-Dokuments, welches das zu ändernde Signaturfeld enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, welches das PDF-Dokument mit dem zu ändernden Signaturfeld darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgewert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Wörterbuchwerten

   * Erstellen Sie ein Objekt `PDFSignatureFieldProperties`, indem Sie den Konstruktor verwenden. Ein `PDFSignatureFieldProperties`-Objekt speichert Informationen zum Sperrwörterbuch für Signaturfelder und zum Seed-Wert-Wörterbuch.
   * Erstellen Sie ein Objekt `PDFSeedValueOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Werte im Seed-Wert-Wörterbuch festlegen.
   * Verhindern Sie Änderungen am PDF-Dokument, indem Sie die Methode `setMdpValue` des `PDFSeedValueOptionSpec`-Objekts aufrufen und den `MDPPermissions.NoChanges`-Auflistungswert übergeben.
   * Erstellen Sie ein Objekt `FieldMDPOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Werte im Signaturfeldsperre-Wörterbuch festlegen.
   * Sperren Sie alle Felder im PDF-Dokument, indem Sie die Methode `setMdpValue` des `FieldMDPOptionSpec`-Objekts aufrufen und den `FieldMDPAction.ALL`-Auflistungswert übergeben.
   * Legen Sie Informationen zum Seed-Wert-Wörterbuch fest, indem Sie die Methode `setSeedValue` des `PDFSignatureFieldProperties`-Objekts aufrufen und das `PDFSeedValueOptionSpec`-Objekt übergeben.
   * Legen Sie Informationen für das Wörterbuch für die Signaturfeldsperre fest, indem Sie die Methode `setFieldMDP` des `PDFSignatureFieldProperties`-Objekts aufrufen und das `FieldMDPOptionSpec`-Objekt übergeben.

   >[!NOTE]
   >
   >Alle Seed-Wert-Wörterbuchwerte, die Sie festlegen können, finden Sie in dem Klassenverweis `PDFSeedValueOptionSpec`. (Siehe [AEM Forms-API-Verweis](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

1. Ändern des Signaturfelds

   Ändern Sie das Signaturfeld, indem Sie die Methode `modifySignatureField` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, in dem das PDF-Dokument mit dem zu ändernden Signaturfeld gespeichert ist
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt
   * Das `PDFSignatureFieldProperties`-Objekt, das Informationen zum Signaturfeldsperre-Wörterbuch und zum Seed-Wert-Wörterbuch speichert

   Die Methode `modifySignatureField` gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein PDF-Dokument speichert, welches das geänderte Signaturfeld enthält.

1. Das PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das die Methode `modifySignatureField` zurückgegeben hat.

### Ändern von Signaturfeldern mithilfe der Webservice-API {#modify-signature-fields-using-the-web-service-api}

So ändern Sie ein Signaturfeld mithilfe der Signature-API (Webservice):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie mithilfe des betreffenden Standardkonstruktors ein `SignatureServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Abrufen des PDF-Dokuments, welches das zu ändernde Signaturfeld enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Die `BLOB` -Objekt wird verwendet, um das PDF-Dokument zu speichern, das das zu ändernde Signaturfeld enthält.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner Eigenschaft `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Wörterbuchwerten

   * Erstellen Sie ein Objekt `PDFSignatureFieldProperties`, indem Sie den Konstruktor verwenden. Dieses Objekt speichert Informationen zum Signaturfeldsperre-Wörterbuch und zum Seed-Wert-Wörterbuch.
   * Erstellen Sie ein Objekt `PDFSeedValueOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Werte im Seed-Wert-Wörterbuch festlegen.
   * Sie können Änderungen am PDF-Dokument verbieten, indem Sie dem Datenelement `mdpValue` des `PDFSeedValueOptionSpec`-Objekts den `MDPPermissions.NoChanges`-Auflistungswert zuweisen.
   * Erstellen Sie ein Objekt `FieldMDPOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Werte im Signaturfeldsperre-Wörterbuch festlegen.
   * Sperren Sie alle Felder im PDF-Dokument, indem Sie den `FieldMDPAction.ALL`-Auflistungswert dem Datenelement `mdpValue` des `FieldMDPOptionSpec`-Objekts zuweisen.
   * Legen Sie Informationen für das Seed-Wert-Wörterbuch fest, indem Sie das `PDFSeedValueOptionSpec`-Objekt dem Datenelement `seedValue` des `PDFSignatureFieldProperties`-Objekts zuweisen.
   * Legen Sie Informationen für das Wörterbuch für die Signaturfeldsperre fest, indem Sie das `FieldMDPOptionSpec`-Objekt dem Datenelement `fieldMDP` des `PDFSignatureFieldProperties`-Objekts zuweisen.

   >[!NOTE]
   >
   >Informationen zu allen Seed-Wert-Wörterbuchwerten, die Sie festlegen können, finden Sie in der `PDFSeedValueOptionSpec`-Klassenreferenz. (Siehe [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

1. Ändern des Signaturfelds

   Ändern Sie das Signaturfeld, indem Sie die Methode `modifySignatureField` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, in dem das PDF-Dokument mit dem zu ändernden Signaturfeld gespeichert ist
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt
   * Das `PDFSignatureFieldProperties`-Objekt, das Informationen zum Signaturfeldsperre-Wörterbuch und zum Seed-Wert-Wörterbuch speichert

   Die Methode `modifySignatureField` gibt ein `BLOB`-Objekt zurück, das ein PDF-Dokument speichert, welches das geänderte Signaturfeld enthält.

1. Das PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments, das das Signaturfeld enthalten soll, und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das die Methode `addSignatureField` zurückgibt. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digitales Signieren von PDF-Dokumenten {#digitally-signing-pdf-documents}

Digitale Signaturen können zu Sicherheitszwecken auf PDF-Dokumente angewendet werden. Digitale Signaturen bieten wie handschriftliche Signaturen ein Mittel, mit dem sich die Unterzeichner identifizieren und zum Dokument Stellung nehmen. Die zum digitalen Signieren von Dokumenten verwendete Technologie stellt sicher, dass sowohl die Person, die es unterzeichnet, als auch die Empfängerinnen und Empfänger genau wissen, was signiert wurde, und dass das Dokument seit der Unterzeichnung nicht mehr geändert wurde.

PDF-Dokumente werden mithilfe von Public-Key-Technologie signiert. Unterzeichnende haben zwei Schlüssel: einen öffentlichen und einen privaten Schlüssel. Der private Schlüssel wird in den Benutzeranmeldedaten gespeichert, die zum Zeitpunkt des Signierens verfügbar sein müssen. Der öffentliche Schlüssel ist im Zertifikat der Benutzenden gespeichert, das den Empfängerinnen und Empfängern zur Validierung der Signatur zur Verfügung stehen muss. Informationen zu widerrufenen Zertifikaten finden Sie in den von Zertifizierungsstellen (CAs) verteilten Antworten auf Zertifikatwiderrufslisten (CRLs) und dem Online Certificate Status Protocol (OCSP). Der Zeitpunkt des Signierens kann von einer vertrauenswürdigen Quelle erhalten werden, die als Zeitstempelstelle bezeichnet wird.

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument digital signieren können, müssen Sie sicherstellen, dass Sie das Zertifikat zu AEM Forms hinzufügen. Ein Zertifikat wird über die Administration-Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Importieren von Anmeldeinformationen mithilfe der Trust Manager-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Sie können PDF-Dokumente programmgesteuert digital signieren. Beim digitalen Signieren eines PDF-Dokuments müssen Sie auf eine Sicherheitsberechtigung verweisen, die in AEM Forms vorhanden ist. Die Anmeldedaten bestehen aus dem zum Signieren verwendeten privaten Schlüssel.

Der Signature-Service führt beim Signieren eines PDF-Dokuments die folgenden Schritte aus:

1. Der Signature-Service ruft die Berechtigung aus dem TrustStore ab, indem er den in der Anfrage angegebenen Alias übergibt.
1. Der TrustStore sucht nach der angegebenen Berechtigung.
1. Die Berechtigung wird an den Signature-Service zurückgegeben und zum Signieren des Dokuments verwendet. Die Berechtigung wird auch für zukünftige Anforderungen gegen den Alias zwischengespeichert.

Informationen zum Umgang mit den Sicherheitsberechtigungen finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Programm-Server.

>[!NOTE]
>
>Es gibt einen Unterschied zwischen dem Signieren und Zertifizieren von Dokumenten. (Siehe [Zertifizieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#certifying-pdf-documents).)

>[!NOTE]
>
>Nicht alle PDF-Dokumente unterstützen das Signieren. Weitere Informationen zum Signature-Service und zum digitalen Signieren von Dokumenten finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Der Signature-Service unterstützt keine XDP-Dateien mit eingebetteten PDF-Daten als Eingabe für einen Vorgang, z. B. das Zertifizieren eines Dokuments. Diese Aktion führt dazu, dass der Signature-Service eine `PDFOperationException` auslöst. Um dieses Problem zu beheben, konvertieren Sie die XDP-Datei mithilfe des PDF Utilities-Services in eine PDF-Datei und übergeben Sie dann die konvertierte PDF-Datei an einen Vorgang des Signature-Services. (Siehe [Arbeiten mit PDF Utilities](/help/forms/developing/pdf-utilities.md#working-with-pdf-utilities).)

**nCipher-nShield-HSM-Berechtigung**

Bei Verwendung einer nCipher-nShield-HSM-Berechtigung zum Signieren oder Zertifizieren eines PDF-Dokuments können die neuen Anmeldedaten erst verwendet werden, nachdem der J2EE-Programm-Server, auf dem AEM Forms bereitgestellt wird, neu gestartet wurde. Sie können jedoch einen Konfigurationswert festlegen, der dazu führt, dass der Vorgang zum Signieren oder Zertifizieren funktioniert, ohne den J2EE-Programm-Server neu starten zu müssen.

Sie können den folgenden Konfigurationswert zur Datei „cknfastrc“ hinzufügen, die sich unter „/opt/nfast/cknfastrc“ (oder „c:\nfast\cknfastrc“) befindet:

```shell
    CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nachdem Sie diesen Konfigurationswert zur Datei „cknfastrc“ hinzugefügt haben, können die neuen Anmeldedaten verwendet werden, ohne den J2EE-Programm-Server neu starten zu müssen.

    >[!NOTE]
    >
    > Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mithilfe alternativer Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

**Signatur ist nicht vertrauenswürdig**

Wenn beim Zertifizieren und Signieren desselben PDF-Dokuments die Zertifizierungssignatur nicht als vertrauenswürdig eingestuft wird, wird beim Öffnen des PDF-Dokuments in Acrobat oder Adobe Reader ein gelbes Dreieck neben der ersten Signatur angezeigt. Die Zertifizierungssignatur muss vertrauenswürdig sein, um dies zu vermeiden.

**Signieren von Dokumenten, die XFA-basierte Formulare sind**

Wenn Sie versuchen, ein XFA-basiertes Formular mithilfe der Signatur-Dienst-API zu signieren, fehlen die Daten möglicherweise in der `View` `Signed` `Version` in Acrobat. Betrachten Sie beispielsweise den folgenden Workflow:

* Mithilfe einer mit Designer erstellten XDP-Datei führen Sie einen Formularentwurf zusammen, der ein Unterschriftsfeld und XML-Daten enthält, die Formulardaten enthalten. Sie verwenden den Forms-Service zum Erzeugen eines interaktiven PDF-Dokuments.
* Sie signieren das PDF-Dokument mithilfe der Signature-Service-API.

### Zusammenfassung der Schritte {#summary_of_steps-3}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument digital zu signieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signature-Service-Client.
1. Rufen Sie das zu signierende PDF-Dokument ab.
1. Signieren Sie das PDF-Dokument.
1. Speichern Sie das signierte PDF-Dokument als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signature-Service-Vorgang programmgesteuert ausführen können, müssen Sie einen Signature-Service-Client erstellen.

**Abrufen des zu signierenden PDF-Dokuments**

Um ein PDF-Dokument zu signieren, müssen Sie ein PDF-Dokument abrufen, das ein Signaturfeld enthält. Wenn ein PDF-Dokument kein Signaturfeld enthält, kann es nicht signiert werden. Ein Signaturfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden.

**Signieren des PDF-Dokuments**

Beim Signieren eines PDF-Dokuments können Sie Laufzeitoptionen festlegen, die vom Signature-Service verwendet werden. Sie können die folgenden Optionen festlegen:

* Erscheinungsbildoptionen
* Sperrprüfung
* Zeitstempelwerte

Sie können Optionen für das Erscheinungsbild mithilfe eines `PDFSignatureAppearanceOptionSpec`-Objekts festlegen. Sie können zum Beispiel das Datum in einer Signatur anzeigen, indem Sie die Methode `setShowDate` des `PDFSignatureAppearanceOptionSpec`-Objekts aufrufen und `true` übergeben.

Sie können auch angeben, ob eine Sperrprüfung durchgeführt werden soll, mit der festgestellt wird, ob das Zertifikat, das zum digitalen Signieren eines PDF-Dokuments verwendet wird, widerrufen wurde. Zur Durchführung der Sperrprüfung können Sie einen der folgenden Werte angeben:

* **NoCheck**: Keine Sperrprüfung durchführen.
* **BestEffort**: Immer versuchen, nach der Sperrung aller Zertifikate in der Kette zu suchen. Tritt bei der Überprüfung ein Problem auf, wird davon ausgegangen, dass die Sperrung gültig ist. Wenn ein Fehler auftritt, gehen Sie davon aus, dass das Zertifikat nicht widerrufen wird.
* **CheckIfAvailable**: Prüfen aller Zertifikate in der Kette auf Sperren, wenn Sperrinformationen verfügbar sind. Tritt bei der Überprüfung ein Problem auf, wird davon ausgegangen, dass die Sperrung ungültig ist. Wenn ein Fehler auftritt, gehen Sie davon aus, dass das Zertifikat widerrufen und ungültig ist. (Dies ist der Standardwert.)
* **AlwaysCheck**: Prüfen aller Zertifikate in der Kette auf Sperren. Wenn in keinem Zertifikat Sperrinformationen vorhanden sind, wird die Sperrung als ungültig angenommen.

Um eine Sperrprüfung für ein Zertifikat durchzuführen, können Sie mithilfe eines `CRLOptionSpec`-Objekts eine URL zu einem Zertifikatsperrlisten-Server (CRL) angeben. Wenn Sie jedoch eine Sperrprüfung durchführen möchten und keine URL für einen Zertifikatsperrlisten-Server angeben, ruft der Signature-Service die URL aus dem Zertifikat ab.

Anstelle eines CRL-Servers können Sie bei der Sperrprüfung einen OCSP-Server (Online Certificate Status Protocol) verwenden. Normalerweise wird bei Verwendung eines OCSP-Servers im Gegensatz zu einem CRL-Server die Sperrprüfung schneller durchgeführt. (Siehe „Online Certificate Status Protocol“ unter [https://tools.ietf.org/html/rfc2560](https://tools.ietf.org/html/rfc2560).)

Sie können Adobe-Programme und -Services verwenden, um die Reihenfolge zwischen CRL- und OCSP-Server festzulegen, die der Signature-Service verwendet. Wenn beispielsweise in Adobe Programme und Services der OCSP-Server als erster festgelegt wird, wird erst der OCSP-Server überprüft, dann der CRL-Server. (Siehe „Verwalten von Zertifikaten und Berechtigungen mithilfe des Trust Store“ in der AAC-Hilfe).

Wenn Sie angeben, dass keine Sperrprüfung durchgeführt werden soll, prüft der Signature-Service nicht, ob das zum Signieren oder Zertifizieren eines Dokuments verwendete Zertifikat widerrufen wurde. Das heißt, die CRL- und OCSP-Serverinformationen werden ignoriert.

>[!NOTE]
>
>Obwohl ein CRL- oder ein OCSP-Server im Zertifikat angegeben werden kann, können Sie die im Zertifikat angegebene URL überschreiben, indem Sie ein `CRLOptionSpec`- und ein `OCSPOptionSpec`-Objekt verwenden. Um beispielsweise den CRL-Server zu überschreiben, können Sie die Methode `setLocalURI` des `CRLOptionSpec`-Objekts aufrufen.

Zeitstempel beziehen sich auf den Prozess der Nachverfolgung des Zeitpunkts, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, sollte es nicht mehr geändert werden, auch nicht vom Dokumenteigentümer. Die Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mithilfe eines `TSPOptionSpec`-Objekts festlegen. Sie können beispielsweise die URL eines Zeitstempelanbieter-Servers (TSP) angeben.

>[!NOTE]
>
>In den Abschnitten über die Java- und Webservices sowie in den entsprechenden Kurzanleitungen wird die Sperrprüfung verwendet. Da keine Informationen zu CRL- oder OCSP-Servern angegeben sind, werden die Server-Informationen aus dem Zertifikat abgerufen, das zum digitalen Signieren des PDF-Dokuments verwendet wird.

Damit ein PDF-Dokument erfolgreich signiert werden kann, können Sie den vollqualifizierten Namen des Signaturfelds angeben, das die digitale Signatur enthalten soll, z. B. `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds kann auch der Teilname des Signaturfelds verwendet werden: `SignatureField3[3]`.

Sie müssen auch auf eine Sicherheitsberechtigung verweisen, um ein PDF-Dokument digital signieren zu können. Um auf eine Sicherheitsberechtigung zu verweisen, geben Sie einen Alias an. Der Alias ist ein Verweis auf eine tatsächliche Berechtigung, die sich in einer PKCS#12-Datei (mit einer .pfx-Erweiterung) oder einem Hardware-Sicherheitsmodul (HSM) befinden kann. Informationen zum Sicherheitsberechtigung finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

**Speichern des signierten PDF-Dokuments**

Nachdem der Signature-Dienst das PDF-Dokument digital signiert hat, können Sie es als PDF-Datei speichern, damit die Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Digitales Signieren von PDF-Dokumenten mit der Java-API](digitally-signing-certifying-documents.md#digitally-sign-pdf-documents-using-the-java-api)

[Digitales Signieren von PDF-Dokumenten mit der Webdienst-API](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields)

[Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

### Digitales Signieren von PDF-Dokumenten mit der Java-API {#digitally-sign-pdf-documents-using-the-java-api}

Digitales Signieren eines PDF-Dokuments mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien, beispielsweise „adobe-signatures-client.jar“, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument zum Signieren abrufen

   * Erstellen Sie eine `java.io.FileInputStream`-Objekt, welches das PDF-Dokument darstellt, das mit seinem Konstruktor digital signiert werden soll, und einen Zeichenfolgenwert übergibt, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Signieren des PDF-Dokuments

   Signieren Sie das PDF-Dokument, indem Sie die Methode `sign` des `SignatureServiceClient`-Objekts verwenden und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, welches das zu signierende PDF-Dokument darstellt.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt, das die digitale Signatur enthalten wird.
   * Ein `Credential`-Objekt, das die Berechtigung darstellt, die zum digitalen Signieren des PDF-Dokuments verwendet werden. Erstellen Sie ein Objekt vom Typ `Credential`, indem Sie die statische Methode `getInstance` des `Credential`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Aliaswert angibt, welcher den Sicherheitsanmeldedaten entspricht.
   * Ein `HashAlgorithm`-Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der für das Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Signatur des PDF-Dokuments angibt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen der unterzeichnenden Person darstellt.
   * Ein `PDFSignatureAppearanceOptions`-Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um einer digitalen Signatur ein benutzerdefiniertes Logo hinzuzufügen.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob eine Sperrprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll.
   * Ein `OCSPOptionSpec`-Objekt, das Einstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `CRLPreferences`-Objekt, das Einstellungen für die Zertifikats-Sperrliste (CRL) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben.
   * Ein `TSPPreferences`-Objekt, das Einstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein. Weitere Informationen finden Sie in der [AEM Forms-API-Verweis](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Die `sign`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Speichern des signierten PDF-Dokuments

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf und übergeben Sie `java.io.File`, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `sign`-Methode zurückgegeben wurde.

**Siehe auch**

[Digitales Signieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Schnellstart (SOAP-Modus): Digitales Signieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitales Signieren von PDF-Dokumenten mit der Webdienst-API {#digitally-signing-pdf-documents-using-the-web-service-api}

Digitales Signieren eines PDF-Dokuments mithilfe der Signatur-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. PDF-Dokument zum Signieren abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines signierten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort des zu signierenden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner Eigenschaft `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Signieren des PDF-Dokuments

   Signieren Sie das PDF-Dokument, indem Sie die Methode `sign` des `SignatureServiceClient`-Objekts verwenden und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, welches das zu signierende PDF-Dokument darstellt.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt, das die digitale Signatur enthalten wird.
   * Ein `Credential`-Objekt, das die Berechtigung darstellt, die zum digitalen Signieren des PDF-Dokuments verwendet werden. Erstellen Sie ein Objekt vom Typ `Credential`, indem Sie seinen Konstruktor verwenden, und geben Sie den Alias an, indem Sie der Eigenschaft `alias` des `Credential`-Objekts einen Wert zuweisen.
   * Ein `HashAlgorithm`-Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der für das Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Signatur des PDF-Dokuments angibt.
   * Ein Zeichenfolgenwert, der den Standort der unterzeichnenden Person darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen der unterzeichnenden Person darstellt.
   * Ein `PDFSignatureAppearanceOptions`-Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um einer digitalen Signatur ein benutzerdefiniertes Logo hinzuzufügen.
   * Ein `System.Boolean`-Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird dies in der Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `OCSPOptionSpec`-Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben. Weitere Informationen zu diesem Objekt finden Sie in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences`-Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben.
   * Ein `TSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein.

   Die Methode `sign` gibt ein `BLOB`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Speichern des signierten PDF-Dokuments

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der Methode `sign` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Digitales Signieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digitales Signieren interaktiver Formulare {#digitally-signing-interactive-forms}

Sie können ein interaktives Formular signieren, das vom Forms-Service erstellt wird. Betrachten Sie beispielsweise den folgenden Workflow:

* Sie führen mithilfe des Forms-Services ein XFA-basiertes PDF-Formular, das mithilfe von Designer erstellt wurde, und Formulardaten in einem XML-Dokument zusammen. Der Forms-Server rendert ein interaktives Formular.
* Sie signieren das interaktive Formular mithilfe der Signature-Service-API.

Das Ergebnis ist ein digital signiertes, interaktives PDF-Formular. Wenn Sie ein PDF-Formular signieren, das auf einem XFA-Formular basiert, stellen Sie sicher, dass Sie die PDF-Datei als statisches Adobe-PDF-Formular speichern. Wenn Sie versuchen, ein PDF-Formular zu signieren, das als Adobe Dynamic PDF-Formular gespeichert ist, tritt eine Ausnahme auf. Da Sie das vom Forms-Dienst zurückgegebene Formular signieren, stellen Sie sicher, dass das Formular ein Signaturfeld enthält.

>[!NOTE]
>
>Bevor Sie ein interaktives Formular digital signieren können, müssen Sie sicherstellen, dass Sie das Zertifikat zu AEM Forms hinzufügen. Ein Zertifikat wird über die Administration-Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Importieren von Berechtigungen mithilfe der Trust Manager-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api).)

Wenn Sie die Forms Service-API verwenden, setzen Sie die Laufzeitoption `GenerateServerAppearance` auf `true`. Diese Laufzeitoption stellt sicher, dass das Erscheinungsbild des auf dem Server generierten Formulars gültig bleibt, wenn es in Acrobat oder Adobe Reader geöffnet wird. Es wird empfohlen, diese Laufzeitoption zu setzen, wenn Sie ein interaktives Formular zum Signieren mithilfe der Forms-API generieren.

>[!NOTE]
>
>Bevor Sie „Digitales Signieren von interaktiven Formularen“ lesen, sollten Sie mit dem Signieren von PDF-Dokumenten vertraut sein. (Siehe [Digitales Signieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um ein interaktives Formular, das der Forms-Dienst zurückgibt, digital zu signieren, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Forms and Signatures-Client.
1. Rufen Sie das interaktive Formular über den Forms-Dienst ab.
1. Signieren Sie das interaktive Formular.
1. Speichern Sie das signierte PDF-Dokument als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-forms-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Weitere Informationen über den Speicherort dieser JAR-Dateien finden Sie unter [AEM Forms-Java-Bibliotheksdateien einbinden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Forms and Signatures-Client**

Da dieser Workflow sowohl den Forms- als auch den Signature-Dienst aufruft, müssen Sie sowohl einen Forms- als auch einen Signature-Dienst-Client erstellen.

**Abrufen des interaktiven Formulars mit dem Forms-Dienst**

Sie können den Forms-Dienst verwenden, um das interaktive PDF-Formular zum Signieren abzurufen. Ab AEM Forms können Sie ein `com.adobe.idp.Document`-Objekt an den Forms-Dienst übergeben, der das rendernde Formular enthält. Der Name dieser Methode lautet `renderPDFForm2`. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, welches das zu signierende Formular enthält. Sie können diese `com.adobe.idp.Document`-Instanz an den Signature-Dienst übergeben.

Ebenso können Sie, wenn Sie Webdienste verwenden, die `BLOB`-Instanz, die der Forms-Dienst zurückgibt, an den Signature-Dienst weitergeben.

>[!NOTE]
>
>Der Schnellstart im Zusammenhang mit dem Abschnitt „Digitales Signieren interaktiver Formulare“ ruft die Methode `renderPDFForm2` auf.

**Signieren des interaktiven Formulars**

Beim Signieren eines PDF-Dokuments können Sie Laufzeitoptionen festlegen, die der Signature-Dienst verwendet. Sie können die folgenden Optionen festlegen:

* Erscheinungsbildoptionen
* Sperrprüfung
* Zeitstempelwerte

Sie können Optionen für das Erscheinungsbild mithilfe eines `PDFSignatureAppearanceOptionSpec`-Objekts festlegen. Sie können zum Beispiel das Datum in einer Signatur anzeigen, indem Sie die Methode `setShowDate` des `PDFSignatureAppearanceOptionSpec`-Objekts aufrufen und `true` übergeben.

**Speichern des signierten PDF-Dokuments**

Nachdem der Signature-Dienst das PDF-Dokument digital signiert hat, können Sie es als PDF-Datei speichern. Die PDF-Datei kann in Acrobat oder Adobe Reader geöffnet werden.

**Siehe auch**

[Digitales Signieren eines interaktiven Formulars mit der Java-API](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-java-api)

[Digitales Signieren eines interaktiven Formulars mit der Webdienst-API](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Digitales Signieren von PDF-Dokumenten](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms)

### Digitales Signieren eines interaktiven Formulars mit der Java-API {#digitally-sign-an-interactive-form-using-the-java-api}

Digitales Signieren eines interaktiven Formulars mithilfe der Forms and Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie „adobe-signatures-client.jar“ und „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms- and Signature-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des interaktiven Formulars mit dem Forms-Dienst

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, das mithilfe seines Konstruktors an den Forms-Service übergeben werden soll. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das XML-Dokument darstellt, das Formulardaten enthält, die mithilfe seines Konstruktors an den Forms-Service übergeben werden sollen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `PDFFormRenderSpec`-Objekt, das zum Festlegen von Laufzeitoptionen verwendet wird. Rufen Sie die Methode `setGenerateServerAppearance` des `PDFFormRenderSpec`-Objekts auf, und übergeben Sie das `true`-Objekt.
   * Rufen Sie die Methode `renderPDFForm2` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

      * Ein `com.adobe.idp.Document`-Objekt, das das zu rendernde PDF-Formular enthält.
      * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen.
      * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
      * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind. Für diesen Parameterwert können Sie `null` angeben.
      * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

     Die `renderPDFForm2`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardaten-Stream enthält

   * Rufen Sie das PDF-Formular ab, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das das interaktive Formular darstellt.

1. Signieren des interaktiven Formulars

   Signieren Sie das PDF-Dokument, indem Sie die Methode `sign` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, das das zu signierende PDF-Dokument darstellt. Stellen Sie sicher, dass dieses Objekt das `com.adobe.idp.Document`-Objekt ist, das vom Forms-Service abgerufen wurde.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds darstellt, das eine Signatur enthält.
   * Ein `Credential`-Objekt, der die zum digitalen Signieren des PDF-Dokuments verwendeten Anmeldededaten darstellt. Erstellen Sie ein Objekt vom Typ `Credential`, indem Sie die statische Methode `getInstance` des `Credential`-Objekts aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Alias-Wert angibt, der den Sicherheitsanmeldedaten entspricht.
   * Ein `HashAlgorithm`-Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der für den Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Signatur des PDF-Dokuments angibt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen der unterzeichnenden Person darstellt.
   * Ein `PDFSignatureAppearanceOptions`-Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um einer digitalen Signatur ein benutzerdefiniertes Logo hinzuzufügen.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob eine Sperrprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll.
   * Ein `OCSPPreferences`-Objekt, das Einstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null` angeben.
   * Ein `CRLPreferences`-Objekt, das Einstellungen für die Zertifikats-Sperrliste (CRL) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben.
   * Ein `TSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein.

   Die Methode `sign` gibt ein `com.adobe.idp.Document`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Speichern des signierten PDF-Dokuments

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf und übergeben Sie `java.io.File`, um den Inhalt des `Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das die `sign`-Methode zurückgegeben hat.

**Siehe auch**

[Digitales Signieren interaktiver Formulare](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Schnellstart (SOAP-Modus): Digitales Signieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitales Signieren eines interaktiven Formulars mit der Webdienst-API {#digitally-sign-an-interactive-form-using-the-web-service-api}

So signieren Sie mit der Forms- und Signatur-API (Web-Service) ein interaktives Formular digital:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da dieses Client-Programm zwei AEM Forms-Services aufruft, erstellen Sie zwei Service-Verweise. Verwenden Sie die folgende WSDL-Definition für den Service-Verweis, der mit dem Signature-Service verknüpft ist: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für den Service-Verweis, der mit dem Forms-Service verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Da der Datentyp `BLOB` für beide Service-Verweise verwendet wird, müssen Sie den Datentyp `BLOB` bei der Verwendung voll qualifizieren. Im entsprechenden Webservice-Schnellstart sind alle `BLOB`-Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` mit der IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Forms- and Signature-Clients

   * Erstellen Sie ein Objekt `SignatureServiceClient`, indem Sie seinen standardmäßigen Konstruktor verwenden.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den Forms-Service-Client.

1. Abrufen des interaktiven Formulars mit dem Forms-Dienst

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines signierten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort des zu signierenden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie die Inhalte des Byte-Arrays seiner `MTOM`-Eigenschaft zuweisen.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern von Formulardaten verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der XML-Datei, die Formulardaten enthält, und den Modus, in dem die Datei geöffnet werden soll, darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekt speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft die Inhalte des Byte-Arrays zuweisen.
   * Erstellen Sie ein `PDFFormRenderSpec`-Objekt, das zum Festlegen von Laufzeitoptionen verwendet wird. Weisen Sie dem Feld `generateServerAppearance` des `PDFFormRenderSpec`-Objekts den Wert `true` zu.
   * Rufen Sie die Methode `renderPDFForm2` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

      * Ein `BLOB`-Objekt, das das zu rendernde PDF-Formular enthält.
      * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen.
      * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
      * Ein `URLSpec`-Objekt, das URI-Werte enthält, die für den Forms-Service erforderlich sind. Für diesen Parameterwert können Sie `null` angeben.
      * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
      * Ein Ausgabeparameter „long“, mit dem die Anzahl der Seiten im Formular gespeichert wird.
      * Ein Zeichenfolgen-Ausgabeparameter, der für den Gebietsschema-Wert verwendet wird.
      * Ein `FormResult`-Wert, der ein Ausgabeparameter ist, der zum Speichern des interaktiven Formulars verwendet wird.

   * Rufen Sie das PDF-Formular ab, indem Sie das Feld `outputContent` des `FormsResult`-Objekts aufrufen. In diesem Feld wird ein `BLOB`-Objekt, das das interaktive Formular darstellt, gespeichert.

1. Signieren des interaktiven Formulars

   Signieren Sie das PDF-Dokument, indem Sie die Methode `sign` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, das das zu signierende PDF-Dokument darstellt. Verwenden Sie die vom Forms-Service zurückgegebene `BLOB`-Instanz.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds darstellt, das eine Signatur enthält.
   * Ein `Credential`-Objekt, der die zum digitalen Signieren des PDF-Dokuments verwendeten Anmeldededaten darstellt. Erstellen Sie ein Objekt vom Typ `Credential`, indem Sie seinen Konstruktor verwenden, und geben Sie den Alias an, indem Sie der Eigenschaft `alias` des `Credential`-Objekts einen Wert zuweisen.
   * Ein `HashAlgorithm`-Objekt, das ein statisches Datenelement angibt, das den Hash-Algorithmus darstellt, der für das Digest des PDF-Dokuments verwendet werden soll. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Signatur des PDF-Dokuments angibt.
   * Ein Zeichenfolgenwert, der den Standort der unterzeichnenden Person darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen der unterzeichnenden Person darstellt.
   * Ein `PDFSignatureAppearanceOptions`-Objekt, das das Erscheinungsbild der digitalen Signatur steuert. Beispielsweise können Sie dieses Objekt verwenden, um einer digitalen Signatur ein benutzerdefiniertes Logo hinzuzufügen.
   * Ein `System.Boolean`-Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird dies in der Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `OCSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben. Weitere Informationen zu diesem Objekt finden Sie in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences`-Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben.
   * Ein `TSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Dieser Parameter ist optional und kann `null` sein.

   Die Methode `sign` gibt ein `BLOB`-Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Speichern des signierten PDF-Dokuments

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der Methode `sign` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Digitales Signieren interaktiver Formulare](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## PDF-Dokumente zertifizieren {#certifying-pdf-documents}

Sie können ein PDF-Dokument absichern, indem Sie es mit einem bestimmten Signaturtyp (nämlich einer zertifizierten Signatur) zertifizieren. Eine zertifizierte Signatur unterscheidet sich wie folgt von einer digitalen Signatur:

* Sie muss die erste, auf das PDF-Dokument angewendete Signatur sein. Das heißt, zum Zeitpunkt, zu dem die zertifizierte Signatur angewendet wird, müssen alle anderen Signaturfelder im Dokument unsigniert sein. In einem PDF-Dokument ist nur eine zertifizierte Signatur zulässig. Wenn Sie ein PDF-Dokument signieren und zertifizieren möchten, müssen Sie es vor dem signieren zertifizieren. Nach dem Zertifizieren eines PDF-Dokuments können Sie weitere Signaturfelder digital signieren.
* Beim Signieren wird das Dokument auf bestimmte Arten von Inhalten geprüft, die den Inhalt des Dokuments missverständlich oder irreführend machen könnten. Beispiel: Das Ausfüllen von Formularen oder Einfügen von Kommentaren kann in dem Dokument zulässig sein. Wenn der Autor festlegt, dass eine bestimmte Änderung nicht zulässig ist, verhindert Acrobat, dass Benutzer das Dokument auf diese Weise ändern. Wenn solche Änderungen vorgenommen werden, etwa durch Verwenden einer anderen Anwendung, wird die zertifizierte Signatur ungültig und Acrobat gibt eine Warnung aus, wenn jemand das Dokument öffnet. (Bei nicht zertifizierten Signaturen werden Änderungen nicht verhindert und normale Bearbeitungsvorgänge führen nicht dazu, dass die ursprüngliche Signatur ungültig wird.)
* Beim Signieren wird das Dokument auf bestimmte Arten von Inhalten geprüft, die den Inhalt des Dokuments missverständlich oder irreführend machen könnten. Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Eine Erläuterung (gültige Beglaubigung) zu solchen Inhalten kann bereitgestellt werden.

Sie können PDF-Dokumente programmgesteuert zertifizieren, indem Sie die Java-API des Signature-Services oder die Signature-Webservice-API verwenden. Beim Zertifizieren eines PDF-Dokuments müssen Sie auf eine Sicherheitsberechtigung verweisen, die im Berechtigungs-Service vorhanden ist. Informationen zu den Sicherheitsberechtigungen finden Sie im Handbuch zum *Installieren und Bereitstellen von AEM Forms* für Ihren Programm-Server.

>[!NOTE]
>
>Wenn beim Zertifizieren und Signieren desselben PDF-Dokuments die Zertifizierungssignatur nicht als vertrauenswürdig eingestuft wird, wird beim Öffnen des PDF-Dokuments in Acrobat oder Adobe Reader neben der ersten Signatur ein gelbes Dreieck angezeigt. Die Zertifizierungssignatur muss vertrauenswürdig sein, um dies zu vermeiden.

>[!NOTE]
>
>Bei Verwendung einer nCipher-nShield-HSM-Berechtigung zum Signieren oder Zertifizieren eines PDF-Dokuments können die neuen Anmeldedaten erst verwendet werden, wenn der J2EE-Programm-Server, auf dem AEM Forms bereitgestellt wird, neu gestartet wird. Sie können jedoch einen Konfigurationswert festlegen, der dazu führt, dass der Vorgang zum Signieren oder Zertifizieren funktioniert, ohne den J2EE-Programm-Server neu starten zu müssen.

Sie können den folgenden Konfigurationswert zur Datei „cknfastrc“ hinzufügen, die sich unter „/opt/nfast/cknfastrc“ (oder „c:\nfast\cknfastrc“) befindet:

```shell
    CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nachdem Sie diesen Konfigurationswert zur Datei „cknfastrc“ hinzugefügt haben, können die neuen Anmeldedaten verwendet werden, ohne den J2EE-Programm-Server neu starten zu müssen.

>[!NOTE]
>
>Weitere Informationen zum Signature-Service und zum Zertifizieren eines Dokuments finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Führen Sie zum Zertifizieren eines PDF-Dokuments die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signatur-Client.
1. Rufen Sie das zu zertifizierende PDF-Dokument ab.
1. Zertifizieren Sie das PDF-Dokument.
1. Speichern Sie das zertifizierte PDF-Dokument als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signatur-Clients**

Bevor Sie einen Signaturvorgang programmgesteuert ausführen können, müssen Sie einen Signature-Client erstellen.

**Abrufen des zu zertifizierenden PDF-Dokuments**

Um ein PDF-Dokument zu zertifizieren, müssen Sie ein PDF-Dokument abrufen, das ein Signaturfeld enthält. Wenn ein PDF-Dokument kein Signaturfeld enthält, kann es nicht zertifiziert werden. Ein Signaturfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden. Informationen zum programmgesteuerten Hinzufügen eines Signaturfelds finden Sie unter [Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields).

**Zertifizieren des PDF-Dokuments**

Zum erfolgreichen Zertifizieren eines PDF-Dokuments benötigen Sie die folgenden Eingabewerte, die vom Signature-Service zum Zertifizieren eines PDF-Dokuments verwendet werden:

* **PDF-Dokument**: Ein PDF-Dokument mit einem Signaturfeld, das ein Formularfeld ist, welches eine grafische Darstellung der zertifizierten Signatur enthält. Ein PDF-Dokument muss ein Signaturfeld enthalten, bevor es zertifiziert werden kann. Ein Signaturfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden. (Siehe [Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields).)
* **Name des Signaturfelds**: Der vollständig qualifizierte Name des Signaturfelds, das zertifiziert wird. Der folgende Wert ist ein Beispiel: `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds kann auch der Teilname des Signaturfelds verwendet werden: `SignatureField3[3]`. Wenn für den Feldnamen ein Nullwert übergeben wird, wird ein unsichtbares Signaturfeld dynamisch erstellt und zertifiziert.
* **Sicherheitsberechtigungen**: Eine Berechtigung, die zum Zertifizieren des PDF-Dokuments verwendet wird. Diese Sicherheitsberechtigung enthält ein Kennwort und einen Alias, der mit einem Alias übereinstimmen muss, der in der Berechtigung angezeigt wird, die sich im Credential-Service befindet. Der Alias ist ein Verweis auf eine tatsächliche Berechtigung, die sich in einer PKCS#12-Datei (mit .pfx-Erweiterung) oder einem Hardware-Sicherheitsmodul (HSM) befinden kann.
* **Hash-Algorithmus**: Ein Hash-Algorithmus, der zum Digest des PDF-Dokuments verwendet wird.
* **Grund für die Unterzeichnung**: Ein Wert, der in Acrobat oder Adobe Reader angezeigt wird, sodass andere Benutzer wissen, warum das PDF-Dokument zertifiziert wurde.
* **Standort des Signierers**: Der Speicherort des Signierers, der durch die Berechtigung angegeben wurde.
* **Kontaktangaben**: Kontaktinformationen des Signierers, wie Adresse und Telefonnummer.
* **Berechtigungsinformationen**: Berechtigungen, die steuern, welche Aktionen ein Endbenutzer für ein Dokument ausführen kann, ohne dass die zertifizierte Signatur ungültig wird. Beispielsweise können Sie die Berechtigung so festlegen, dass jede Änderung am PDF-Dokument dazu führt, dass die zertifizierte Signatur ungültig wird.
* **Rechtliche Erläuterung**: Wenn ein Dokument zertifiziert wird, wird es automatisch auf bestimmte Inhaltstypen überprüft, die den Inhalt eines Dokuments mehrdeutig oder irreführend machen könnten. Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Der Scan-Vorgang erzeugt Warnungen zu diesen Inhaltstypen. Dieser Wert liefert eine zusätzliche Erklärung für die Inhalte, die möglicherweise zu Warnungen geführt haben.
* **Erscheinungsbildoptionen**: Optionen, die das Erscheinungsbild der zertifizierten Signatur steuern. Beispielsweise kann die zertifizierte Signatur Datumsangaben anzeigen.
* **Sperrprüfung**: Dieser Wert gibt an, ob für das Zertifikat des Signierers eine Sperrprüfung durchgeführt wird. Die Standardeinstellung von `false` bedeutet, dass keine Sperrprüfung durchgeführt wird.
* **OCSP-Einstellungen**: Unterstützung von Einstellungen für das Online Certificate Status Protocol (OCSP), das Informationen zum Status der Berechtigung bereitstellt, die zum Zertifizieren des PDF-Dokuments verwendet wird. Sie können beispielsweise die URL des Servers angeben, der Informationen zu den Anmeldedaten bereitstellt, die Sie zum Anmelden beim PDF-Dokument verwenden.
* **CRL-Einstellungen**: Voreinstellungen der Zertifikatsperrliste (CRL), wenn die Sperrprüfung durchgeführt wird. Sie können beispielsweise festlegen, dass immer geprüft werden soll, ob eine Berechtigung widerrufen wurde.
* **Zeitstempel**: Einstellungen, die Zeitstempelinformationen definieren, welche auf die zertifizierte Signatur angewendet werden. Ein Zeitstempel gibt an, dass bestimmte Daten vor einer bestimmten Zeit entstanden sind. Dieses Wissen hilft beim Aufbau einer vertrauensvollen Beziehung zwischen dem Signierer und dem Prüfer.

**Speichern des zertifizierten PDF-Dokuments als PDF-Datei**

Nachdem der Signature-Service das PDF-Dokument zertifiziert hat, können Sie es als PDF-Datei speichern, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Zertifizieren von PDF-Dokumenten mithilfe der Java-API](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-java-api)

[Zertifizieren von PDF-Dokumenten mithilfe der Webservice-API](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields)

### Zertifizieren von PDF-Dokumenten mithilfe der Java-API {#certify-pdf-documents-using-the-java-api}

So zertifizieren Sie ein PDF-Dokument mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-signatures-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des zu zertifizierenden PDF-Dokuments

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu zertifizierende PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Zertifizieren des PDF-Dokuments

   Zertifizieren Sie das PDF-Dokument, indem Sie die Methode `certify` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document`-Objekt, das das zu zertifizierende PDF-Dokument darstellt.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfeldes darstellt, das die Signatur enthalten wird.
   * Ein `Credential`-Objekt, das die zum Signieren des PDF-Dokuments verwendete Berechtigung darstellt. Erstellen Sie ein Objekt vom Typ `Credential`, indem Sie die statische Methode `getInstance` des `Credential`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Aliaswert angibt, welcher der Sicherheitsberechtigung entspricht.
   * Ein `HashAlgorithm`-Objekt, das ein statisches Datenelement angibt, welches den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet wird. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein Zeichenfolgenwert, der den Grund darstellt, aus dem das PDF-Dokument zertifiziert wurde.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen der unterzeichnenden Person darstellt.
   * Ein `MDPPermissions`-Objekt, das Aktionen angibt, die mit dem PDF-Dokument ausgeführt werden können und dadurch die Signatur ungültig machen.
   * Ein `PDFSignatureAppearanceOptions`-Objekt, das das Erscheinungsbild der zertifizierten Signatur steuert. Ändern Sie bei Bedarf das Erscheinungsbild der Signatur, indem Sie eine Methode aufrufen, z. B. `setShowDate`.
   * Ein Zeichenfolgenwert, der erklärt, durch welche Aktionen die Signatur ungültig gemacht wird.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird dies in der Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `java.lang.Boolean`-Objekt, das angibt, ob das zu zertifizierende Signaturfeld gesperrt ist. Wenn das Feld gesperrt ist, wird das Signaturfeld als schreibgeschützt markiert, seine Eigenschaften können nicht geändert werden und es kann von niemandem gelöscht werden, der nicht über die erforderlichen Berechtigungen verfügt. Der Standardwert lautet `false`.
   * Ein `OCSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben. Weitere Informationen zu diesem Objekt finden Sie in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences`-Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben.
   * Ein `TSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Nachdem Sie zum Beispiel ein `TSPPreferences`-Objekt erstellt haben, können Sie die URL des TSP-Servers festlegen, indem Sie die Methode `setTspServerURL` des `TSPPreferences`-Objekts aufrufen. Dieser Parameter ist optional und kann `null` sein. Weitere Informationen finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

   Die Methode `certify` gibt ein `com.adobe.idp.Document`-Objekt zurück, das das zertifizierte PDF-Dokument darstellt.

1. Speichern des zertifizierten PDF-Dokuments als PDF-Datei

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren.

**Siehe auch**

[PDF-Dokumente zertifizieren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Kurzanleitung (SOAP-Modus): Zertifizieren eines PDF-Dokuments mithilfe der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zertifizieren von PDF-Dokumenten mithilfe der Webservice-API {#certify-pdf-documents-using-the-web-service-api}

So zertifizieren Sie ein PDF-Dokument mithilfe der Signature-API (Webservice):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie mithilfe des betreffenden Standardkonstruktors ein `SignatureServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Abrufen des zu zertifizierenden PDF-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines zertifizierten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu zertifizierenden PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des Objekts `System.IO.FileStream` verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge weitergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Zertifizieren des PDF-Dokuments

   Zertifizieren Sie das PDF-Dokument, indem Sie die Methode `certify` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das zu zertifizierende PDF-Dokument darstellt.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfeldes darstellt, das die Signatur enthalten wird.
   * Ein `Credential`-Objekt, das die zum Signieren des PDF-Dokuments verwendete Berechtigung darstellt. Erstellen Sie ein Objekt vom Typ `Credential`, indem Sie seinen Konstruktor verwenden, und geben Sie den Alias an, indem Sie der Eigenschaft `alias` des `Credential`-Objekts einen Wert zuweisen.
   * Ein `HashAlgorithm`-Objekt, das ein statisches Datenelement angibt, welches den Hash-Algorithmus darstellt, der zum Digest des PDF-Dokuments verwendet wird. Sie können beispielsweise `HashAlgorithm.SHA1` angeben, um den SHA1-Algorithmus zu verwenden.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein Zeichenfolgenwert, der den Grund darstellt, aus dem das PDF-Dokument zertifiziert wurde.
   * Ein Zeichenfolgenwert, der den Standort der unterzeichnenden Person darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen der unterzeichnenden Person darstellt.
   * Das statische Datenelement eines `MDPPermissions`-Objekts, das die Aktionen angibt, die mit dem PDF-Dokument durchgeführt werden können und dadurch die Signatur ungültig machen.
   * Ein boolescher Wert, der angibt, ob das `MDPPermissions`-Objekt verwendet werden soll, das als vorheriger Parameterwert übergeben wurde.
   * Ein Zeichenfolgenwert, der erklärt, durch welche Aktionen die Signatur ungültig gemacht wird.
   * Ein `PDFSignatureAppearanceOptions`-Objekt, das das Erscheinungsbild der zertifizierten Signatur steuert. Erstellen Sie ein Objekt `PDFSignatureAppearanceOptions`, indem Sie den Konstruktor verwenden. Sie können das Erscheinungsbild der Signatur ändern, indem Sie eines ihrer Datenelemente festlegen.
   * Ein `System.Boolean`-Objekt, das angibt, ob das Zertifikat des Signierers einer Sperrprüfung unterzogen werden soll. Wenn diese Sperrprüfung durchgeführt wird, wird dies in der Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `System.Boolean`-Objekt, das angibt, ob das zu zertifizierende Signaturfeld gesperrt ist. Wenn das Feld gesperrt ist, wird das Signaturfeld als schreibgeschützt markiert, seine Eigenschaften können nicht geändert werden und es kann von niemandem gelöscht werden, der nicht über die erforderlichen Berechtigungen verfügt. Der Standardwert lautet `false`.
   * Ein `System.Boolean`-Objekt, das angibt, ob das Signaturfeld gesperrt ist. Das heißt, wenn Sie `true` an den vorherigen Parameter übergeben, übergeben Sie `true` an diesen Parameter.
   * Ein `OCSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Online Certificate Status Protocol (OCSP) speichert, welches Informationen zum Status der Berechtigung bereitstellt, die zum Zertifizieren des PDF-Dokuments verwendet wird. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben.
   * Ein `CRLPreferences`-Objekt, das Einstellungen für die Zertifikats-Sperrliste (CRL) speichert. Wenn keine Sperrprüfung durchgeführt wird, wird dieser Parameter nicht verwendet, und Sie können `null` angeben.
   * Ein `TSPPreferences`-Objekt, das Voreinstellungen für die Unterstützung des Zeitstempelanbieters (TSP) speichert. Nachdem Sie zum Beispiel ein Objekt vom Typ `TSPPreferences` erstellt haben, können Sie die URL des TSP festlegen, indem Sie das Datenelement `tspServerURL` des `TSPPreferences`-Objekts festlegen. Dieser Parameter ist optional und kann `null` sein.

   Die Methode `certify` gibt ein `BLOB`-Objekt zurück, das das zertifizierte PDF-Dokument darstellt.

1. Speichern des zertifizierten PDF-Dokuments als PDF-Datei

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments, das das zertifizierte PDF-Dokument enthalten wird, sowie den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der Methode `certify` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `binaryData` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[PDF-Dokumente zertifizieren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Überprüfen digitaler Signaturen {#verifying-digital-signatures}

Digitale Signaturen können überprüft werden, um sicherzustellen, dass ein signiertes PDF-Dokument nicht geändert wurde und die digitale Signatur gültig ist. Beim Überprüfen einer digitalen Signatur können Sie den Signaturstatus und die Signatureigenschaften, wie etwa die Identität der unterzeichnenden Person, prüfen. Bevor Sie einer digitalen Signatur vertrauen, sollten Sie sie überprüfen. Verwenden Sie beim Überprüfen einer digitalen Signatur ein PDF-Dokument, das eine digitale Signatur enthält.

Angenommen, die Identität des Signierers ist unbekannt. Wenn Sie das PDF-Dokument in Acrobat öffnen, wird in einer Warnmeldung darauf hingewiesen, dass die Identität der unterzeichnenden Person unbekannt ist, wie in der folgenden Abbildung dargestellt.

![vd_vd_verifysig](assets/vd_vd_verifysig.png)

Ebenso können Sie beim programmgesteuerten Überprüfen einer digitalen Signatur den Status der Identität der unterzeichnenden Person ermitteln. Wenn Sie beispielsweise die digitale Signatur in dem in der vorherigen Abbildung gezeigten Dokument überprüfen, wäre das Ergebnis, dass die Identität der unterzeichnenden Person unbekannt ist.

>[!NOTE]
>
>Weitere Informationen über den Signature-Dienst und zum Überprüfen digitaler Signaturen finden Sie unter [Dienstverweis für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Führen Sie zum Überprüfen einer digitalen Signatur die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signatur-Client.
1. Rufen Sie das PDF-Dokument ab, das die zu verifizierende Signatur enthält.
1. Legen Sie PKI-Laufzeitoptionen fest.
1. Überprüfen Sie die digitale Signatur.
1. Bestimmen Sie den Status der Signatur.
1. Bestimmen Sie die Identität des Signierers.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signature-Clients**

Bevor Sie einen Vorgang des Signature-Services programmgesteuert ausführen, erstellen Sie einen Signature-Service-Client.

**Abrufen des PDF-Dokuments, das die zu überprüfende Signatur enthält**

Um eine Signatur zu überprüfen, die zum digitalen Signieren oder Zertifizieren eines PDF-Dokuments verwendet wird, rufen Sie ein PDF-Dokument ab, das eine Signatur enthält.

**Festlegen von PKI-Laufzeitoptionen**

Legen Sie diese PKI-Laufzeitoptionen fest, die der Signature-Service beim Überprüfen von Signaturen in einem PDF-Dokument verwendet:

* Überprüfungszeit
* Sperrprüfung
* Zeitstempelwerte

Im Rahmen der Einstellung dieser Optionen können Sie den Überprüfungszeitpunkt festlegen. Sie können beispielsweise die aktuelle Zeit (die Zeit auf dem Computer des Validators bzw. der Validatorin) auswählen, was angibt, die aktuelle Zeit zu verwenden. Weitere Informationen zu den verschiedenen Zeitwerten finden Sie unter `VerificationTime` Aufzählungswert in [AEM Forms-API-Verweis](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Sie können auch angeben, ob im Rahmen des Überprüfungsprozesses eine Sperrprüfung durchgeführt werden soll. Sie können beispielsweise eine Sperrprüfung durchführen, um festzustellen, ob das Zertifikat widerrufen wurde. Weitere Informationen zu den Optionen für die Sperrprüfung finden Sie unter `RevocationCheckStyle` Auflistungswert in [AEM Forms-API-Verweis](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Um eine Widerrufsprüfung für ein Zertifikat durchzuführen, geben Sie mithilfe eines `CRLOptionSpec`-Objekts eine URL zu einem Zertifikatssperrlisten-Server (CRL) an. Wenn Sie jedoch keine URL für den CRL-Server angeben, ruft der Signature-Service die URL vom Zertifikat ab.

Anstelle eines CRL-Servers können Sie bei der Sperrprüfung einen OCSP-Server (Online Certificate Status Protocol) verwenden. Normalerweise wird bei Verwendung eines OCSP-Servers im Gegensatz zu einem CRL-Server die Sperrprüfung schneller durchgeführt. (Siehe [Online Certificate Status Protocol](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signaturdienst mithilfe von Adobe Applications and Services verwendet. Wenn beispielsweise der OCSP-Server in Adobe Applications and Services zuerst festgelegt wird, wird der OCSP-Server überprüft, gefolgt vom CRL-Server.

Wenn Sie keine Sperrprüfung durchführen, überprüft der Signaturdienst nicht, ob das Zertifikat widerrufen wurde. Das heißt, die CRL- und OCSP-Serverinformationen werden ignoriert.

>[!NOTE]
>
>Sie können die im Zertifikat angegebene URL überschreiben, indem Sie ein `CRLOptionSpec`- und ein `OCSPOptionSpec`-Objekt verwenden. Um beispielsweise den CRL-Server zu überschreiben, können Sie die Methode `setLocalURI` des `CRLOptionSpec`-Objekts aufrufen.

Beim Zeitstempel wird der Zeitpunkt ermittelt, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, kann es von niemandem geändert werden. Die Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mithilfe eines `TSPOptionSpec`-Objekts festlegen. Sie können beispielsweise die URL eines Zeitstempelanbieter-Servers (TSP) angeben.

>[!NOTE]
>
>In den Java- und Webdienst-Schnellstarts ist die Überprüfungszeit auf `VerificationTime.CURRENT_TIME` und die Sperrprüfung auf `RevocationCheckStyle.BestEffort` eingestellt. Da keine CRL- oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem Zertifikat bezogen.

**Überprüfen der digitalen Signatur**

Um eine Signatur erfolgreich zu überprüfen, geben Sie den vollqualifizierten Namen des Signaturfelds an, das die Signatur enthält, beispielsweise `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds können Sie auch den Teilnamen des Signaturfelds verwenden: `SignatureField3`.

Standardmäßig begrenzt der Signaturdienst die Zeitspanne, die ein Dokument nach der Validierung signiert werden kann, auf 65 Minuten. Wenn ein Benutzer versucht, eine Signatur zum aktuellen Zeitpunkt zu überprüfen und der Signaturzeitpunkt nach dem aktuellen Zeitpunkt aber innerhalb von 65 Minuten liegt, erzeugt der Signature-Dienst keinen Prüffehler.

>[!NOTE]
>
>Weitere Werte, die Sie beim Überprüfen einer Signatur benötigen, finden Sie unter [AEM Forms-API-Verweis](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Status der Signatur ermitteln**

Im Zuge der Prüfung einer digitalen Signatur können Sie den Status der Signatur überprüfen.

**Identität des Unterzeichners ermitteln**

Sie können die Identität des Unterzeichners ermitteln, die einen der folgenden Werte annehmen kann:

* **Unbekannt**: Dieser Unterzeichner ist unbekannt, da die Unterzeichner-Überprüfung nicht durchgeführt werden kann.
* **Vertrauenswürdig**: Dieser Unterzeichner ist vertrauenswürdig.
* **Nicht vertrauenswürdig**: Dieser Unterzeichner ist nicht vertrauenswürdig.

**Siehe auch**

[Digitale Signaturen mit der Java-API überprüfen](#verify-digital-signatures-using-the-java-api)

[Digitale Signaturen mit der Webdienst-API überprüfen](#verify-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mit der Java-API überprüfen {#verify-digital-signatures-using-the-java-api}

Überprüfen einer digitalen Signatur mithilfe der Signature-Service-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien, beispielsweise „adobe-signatures-client.jar“, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das PDF-Dokument ab, das die zu prüfende Signatur enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, welches das PDF-Dokument darstellt, welches die zu prüfende Signatur enthält, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie die Methode `setVerificationTime` des `PKIOptions`-Objekts aufrufen und einen `VerificationTime`-Aufzählungswert übergeben, der die Überprüfungszeit angibt.
   * Legen Sie die Option für die Sperrprüfung fest, indem Sie die Methode `setRevocationCheckStyle` des `PKIOptions`-Objekts aufrufen und einen `RevocationCheckStyle`-Aufzählungswert übergeben, der angibt, ob eine Sperrprüfung durchgeführt werden soll.

1. Überprüfen der digitalen Signatur

   Überprüfen Sie die Signatur, indem Sie die Methode `verify2` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` -Objekt, das ein digital signiertes oder zertifiziertes PDF-Dokument enthält.
   * Ein Zeichenfolgewert für den Signaturfeldnamen, der die zu überprüfende Signatur enthält.
   * Ein `PKIOptions`-Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können für diesen Parameter `null` angeben.

   Die `verify2`-Methode gibt ein `PDFSignatureVerificationInfo`-Objekt mit Informationen zurück, die zum Überprüfen der digitalen Signatur verwendet werden können.

1. Bestimmen des Status der Signatur

   * Ermitteln Sie den Signaturstatus, indem Sie die Methode `getStatus` des `PDFSignatureVerificationInfo`-Objekts aufrufen. Diese Methode gibt ein `SignatureStatus`-Objekt zurück, das den Signaturstatus angibt. Wenn beispielsweise ein signiertes PDF-Dokument nicht geändert wird, gibt diese Methode `SignatureStatus.DocumentSigNoChanges` zurück.

1. Bestimmen der Identität des Signierers

   * Ermitteln Sie die Identität der unterzeichnenden Person, indem Sie die Methode `getSigner` des `PDFSignatureVerificationInfo`-Objekts aufrufen. Diese Methode gibt ein `IdentityInformation`-Objekt zurück.
   * Rufen Sie die Methode `getStatus` des `IdentityInformation`-Objekts auf, um die Identität der unterzeichnenden Person zu bestimmen. Diese Methode gibt einen Auflistungswert `IdentityStatus` zurück, der die Identität angibt. Wenn beispielsweise der Unterzeichner als vertrauenswürdig eingestuft wird, gibt diese Methode `IdentityStatus.TRUSTED` zurück.

**Siehe auch**

[Überprüfen digitaler Signaturen](#verify-digital-signatures-using-the-java-api)

[Schnellstart (SOAP-Modus): Überprüfen einer digitalen Signatur mithilfe der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mit der Webdienst-API überprüfen {#verify-digital-signatures-using-the-web-service-api}

Überprüfen einer digitalen Signatur mithilfe der Signature Service-API (Web Service):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie mithilfe des betreffenden Standardkonstruktors ein `SignatureServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das PDF-Dokument ab, das die zu prüfende Signatur enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, das eine zu verifizierende digitale oder zertifizierte Signatur enthält.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, in dem der Inhalt des `System.IO.FileStream`-Objekts gespeichert wird. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner Eigenschaft `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie dem Datenelement `verificationTime` des `PKIOptions`-Objekts einen `VerificationTime`-Aufzählungswert zuweisen, der die Überprüfungszeit angibt.
   * Legen Sie die Option für die Sperrprüfung fest, indem Sie dem Datenelement `revocationCheckStyle` des `PKIOptions`-Objekts einen `RevocationCheckStyle`-Aufzählungswert zuweisen, der angibt, ob eine Sperrprüfung durchgeführt werden soll.

1. Überprüfen der digitalen Signatur

   Überprüfen Sie die Signatur, indem Sie die Methode `verify2` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das ein digital signiertes oder zertifiziertes PDF-Dokument enthält.
   * Ein Zeichenfolgewert für den Signaturfeldnamen, der die zu überprüfende Signatur enthält.
   * Ein `PKIOptions`-Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können für diesen Parameter `null` angeben.

   Die `verify2`-Methode gibt ein `PDFSignatureVerificationInfo`-Objekt mit Informationen zurück, die zum Überprüfen der digitalen Signatur verwendet werden können.

1. Bestimmen des Status der Signatur

   Bestimmen Sie den Signaturstatus, indem Sie den Wert des Datenelements `status` des `PDFSignatureVerificationInfo`-Objekts abrufen. Dieses Datenelement enthält ein `SignatureStatus`-Objekt, das den Status der Signatur angibt. Wenn beispielsweise ein signiertes PDF-Dokument geändert wird, enthält das Datenelement `status` den Wert `SignatureStatus.DocumentSigNoChanges`.

1. Bestimmen der Identität des Signierers

   * Bestimmen Sie die Identität der unterzeichnenden Person, indem Sie den Wert des Datenelements `signer` des `PDFSignatureVerificationInfo`-Objekts abrufen. Dieses Element gibt ein `IdentityInformation`-Objekt zurück.
   * Rufen Sie das Datenelement `status` des `IdentityInformation`-Objekts ab, um die Identität der unterzeichnenden Person zu bestimmen. Dieses Datenelement gibt einen `IdentityStatus`-Auflistungswert zurück, der die Identität angibt. Wenn beispielsweise der Unterzeichner als vertrauenswürdig eingestuft wird, gibt dieses Element `IdentityStatus.TRUSTED` zurück.

**Siehe auch**

[Überprüfen digitaler Signaturen](#verify-digital-signatures-using-the-java-api)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Überprüfen mehrerer digitaler Signaturen {#verifying-multiple-digital-signatures}

AEM Forms bietet die Möglichkeit, alle digitalen Signaturen zu überprüfen, die sich in einem PDF-Dokument befinden. Angenommen, ein PDF-Dokument enthält mehrere digitale Unterschriften als Ergebnis eines Geschäftsprozesses, der Unterschriften von mehreren Personen erfordert. Betrachten Sie beispielsweise eine Finanztransaktion, die sowohl die Unterschrift eines oder einer Kreditsachbediensteten als auch von Manager-Seite erfordert. Sie können die Signature-Dienst-API verwenden, um alle Signaturen im PDF-Dokument zu überprüfen. Beim Überprüfen mehrerer digitaler Signaturen können Sie den Status und die Eigenschaften jeder Signatur prüfen. Bevor Sie einer digitalen Signatur vertrauen, sollten Sie diese überprüfen. Es wird empfohlen, dass Sie mit der Überprüfung einer einzelnen digitalen Signatur vertraut sind.

>[!NOTE]
>
>Weitere Informationen über den Signature-Dienst und zum Überprüfen digitaler Signaturen finden Sie unter [Dienstverweis für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

Um mehrere digitale Signaturen zu überprüfen, führen Sie die folgenden Aufgaben aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signatur-Client.
1. Rufen Sie das PDF-Dokument ab, das die zu überprüfenden Signaturen enthält.
1. Legen Sie PKI-Laufzeitoptionen fest.
1. Rufen Sie alle digitalen Signaturen ab.
1. Iterieren Sie durch alle Signaturen.

**Projektdateien einbinden**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signature-Clients**

Bevor Sie einen Vorgang des Signature-Services programmgesteuert ausführen, erstellen Sie einen Signature-Service-Client.

**Abrufen des PDF-Dokuments, das die zu überprüfenden Signaturen enthält**

Um eine Signatur zu überprüfen, die zum digitalen Signieren oder Zertifizieren eines PDF-Dokuments verwendet wird, rufen Sie ein PDF-Dokument ab, das eine Signatur enthält.

**PKI-Laufzeitoptionen festlegen**

Legen Sie diese PKI-Laufzeitoptionen fest, die der Signature-Dienst bei der Prüfung aller Signaturen in einem PDF-Dokument verwendet:

* Überprüfungszeit
* Sperrprüfung
* Zeitstempelwerte

Im Rahmen der Einstellung dieser Optionen können Sie den Überprüfungszeitpunkt festlegen. Sie können beispielsweise die aktuelle Zeit (die Zeit auf dem Computer des Validators bzw. der Validatorin) auswählen, was angibt, die aktuelle Zeit zu verwenden. Weitere Informationen zu den verschiedenen Zeitwerten finden Sie unter `VerificationTime` Aufzählungswert in [AEM Forms-API-Verweis](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Sie können auch angeben, ob im Rahmen des Überprüfungsprozesses eine Sperrprüfung durchgeführt werden soll. Sie können beispielsweise eine Sperrprüfung durchführen, um festzustellen, ob das Zertifikat widerrufen wurde. Weitere Informationen zu den Optionen für die Sperrprüfung finden Sie unter `RevocationCheckStyle` Auflistungswert in [AEM Forms-API-Verweis](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Um eine Sperrprüfung für ein Zertifikat durchzuführen, geben Sie mit einem `CRLOptionSpec`-Objekt eine URL zu einem Zertifikatssperrlistenserver (CRL) an. Wenn Sie jedoch keine URL zu einem CRL-Server angeben, bezieht der Signature-Dienst die URL aus dem Zertifikat.

Anstelle eines CRL-Servers können Sie bei der Sperrprüfung einen OCSP-Server (Online Certificate Status Protocol) verwenden. In der Regel wird bei Verwendung eines OCSP-Servers anstelle eines CRL-Servers die Sperrprüfung schneller durchgeführt. (Siehe [Onlinezertifikat Statussprotokoll](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signaturdienst mithilfe von Adobe Applications and Services verwendet. Wenn beispielsweise der OCSP-Server zuerst in Adobe Applications and Services festgelegt wird, wird der OCSP-Server überprüft, gefolgt vom CRL-Server.

Wenn Sie keine Sperrprüfung durchführen, überprüft der Signaturdienst nicht, ob das Zertifikat widerrufen wurde. Das heißt, die CRL- und OCSP-Serverinformationen werden ignoriert.

>[!NOTE]
>
>Sie können die im Zertifikat angegebene URL überschreiben, indem Sie ein `CRLOptionSpec`- und ein `OCSPOptionSpec`-Objekt verwenden. Um beispielsweise den CRL-Server zu überschreiben, können Sie die Methode `setLocalURI` des `CRLOptionSpec`-Objekts aufrufen.

Beim Zeitstempel wird der Zeitpunkt ermittelt, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, kann es von niemandem geändert werden. Die Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mithilfe eines `TSPOptionSpec` -Objekts festlegen. Sie können beispielsweise die URL eines Zeitstempelanbieter-Servers (TSP) angeben.

>[!NOTE]
>
>In den Java- und Webdienst-Schnellstarts ist die Überprüfungszeit auf `VerificationTime.CURRENT_TIME` und die Sperrprüfung auf `RevocationCheckStyle.BestEffort` eingestellt. Da keine CRL- oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem Zertifikat bezogen.

**Alle digitalen Signaturen abrufen**

Um alle digitalen Signaturen in einem PDF-Dokument zu überprüfen, rufen Sie die digitalen Signaturen aus dem PDF-Dokument ab. Alle Signaturen werden in einer Liste zurückgegeben. Kontrollieren Sie im Rahmen der Überprüfung einer digitalen Signatur den Status der Signatur.

>[!NOTE]
>
>Im Gegensatz zur Überprüfung einer einzelnen digitalen Signatur müssen Sie bei der Überprüfung mehrerer Signaturen keinen Signaturfeldnamen angeben.

**Iteration aller Signaturen**

Iterieren Sie durch jede Signatur. Das heißt, für jede Signatur überprüfen Sie die digitale Signatur und überprüfen außerdem die Identität der unterzeichnenden Person und den Status jeder Signatur. (Siehe [Überprüfen digitaler Signaturen](#verify-digital-signatures-using-the-java-api).)

>[!NOTE]
>
>Sie müssen nicht alle Signaturen zu iterieren, wenn die Anforderung das gesamte Dokument ist.

**Siehe auch**

[Mehrere digitale Signaturen mit der Java-API überprüfen](#verify-digital-signatures-using-the-java-api)

[Mehrere digitale Signaturen mit der Webdienst-API überprüfen](#verify-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mehrere digitale Signaturen mit der Java-API überprüfen {#verify-multiple-digital-signatures-using-the-java-api}

Überprüfen mehrerer digitaler Signaturen mithilfe der Signature-Service-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien, beispielsweise „adobe-signatures-client.jar“, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des PDF-Dokuments, das die zu überprüfenden Signaturen enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, welches das PDF-Dokument darstellt, das mehrere zu prüfende Signatur enthält, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie die Methode `setVerificationTime` des `PKIOptions`-Objekts aufrufen und einen `VerificationTime`-Auflistungswert übergeben, der die Überprüfungszeit angibt.
   * Legen Sie die Option für die Widerrufsprüfung fest, indem Sie die Methode `setRevocationCheckStyle` des `PKIOptions`-Objekts aufrufen und einen `RevocationCheckStyle`-Auflistungswert übergeben, der angibt, ob eine Widerrufsprüfung durchgeführt werden soll.

1. Abrufen aller digitalen Signaturen

   Rufen Sie die Methode `verifyPDFDocument` des `SignatureServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document`-Objekt, das ein PDF-Dokument mit mehreren digitalen Signaturen enthält.
   * Ein `PKIOptions`-Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können für diesen Parameter `null` angeben.

   Die Methode `verifyPDFDocument` gibt ein `PDFDocumentVerificationInfo`-Objekt zurück, das Informationen zu allen digitalen Signaturen enthält, die sich im PDF-Dokument befinden.

1. Iteration durch alle Signaturen

   * Iterieren Sie durch alle Signaturen, indem Sie die Methode `getVerificationInfos` des `PDFDocumentVerificationInfo`-Objekts aufrufen. Diese Methode gibt eine `java.util.List` Objekt zurück, bei dem jedes Element ein `PDFSignatureVerificationInfo`-Objekt ist. Verwenden Sie ein `java.util.Iterator`-Objekt, um durch die Liste der Signaturen zu iterieren.
   * Mit dem `PDFSignatureVerificationInfo`-Objekt können Sie Aufgaben durchführen, beispielsweise die Bestimmung des Status der Signatur, indem Sie die Methode `getStatus` des `PDFSignatureVerificationInfo`-Objekts aufrufen. Diese Methode gibt ein `SignatureStatus`-Objekt zurück, dessen statisches Datenelement Sie über den Status der Signatur informiert. Wenn die Signatur beispielsweise unbekannt ist, gibt diese Methode `SignatureStatus.DocumentSignatureUnknown` zurück.

**Siehe auch**

[Überprüfen mehrerer digitaler Signaturen](#verifying-multiple-digital-signatures)

[Schnellstart (SOAP-Modus): Überprüfen mehrerer digitaler Signaturen mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Überprüfen digitaler Signaturen](#verify-digital-signatures-using-the-java-api)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mehrere digitale Signaturen mit der Webdienst-API überprüfen {#verifying-multiple-digital-signatures-using-the-web-service-api}

Überprüfen mehrerer digitaler Signaturen mithilfe der Signature-Service-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie mithilfe des betreffenden Standardkonstruktors ein `SignatureServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Abrufen des PDF-Dokuments, das die zu überprüfenden Signaturen enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt speichert ein PDF-Dokument, das mehrere zu überprüfende digitale Signaturen enthält.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Dokuments und den Modus angibt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie dem Datenelement `verificationTime` des `PKIOptions`-Objekts einen `VerificationTime`-Auflistungswert zuweisen, der die Überprüfungszeit angibt.
   * Legen Sie die Widerrufsprüfungsoption fest, indem Sie dem Datenelement `revocationCheckStyle` des `PKIOptions`-Objekts einen `RevocationCheckStyle`-Auflistungswert zuweisen, der angibt, ob eine Widerrufsprüfung durchgeführt werden soll.

1. Abrufen aller digitalen Signaturen

   Rufen Sie die Methode `verifyPDFDocument` des `SignatureServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB`-Objekt, das ein PDF-Dokument mit mehreren digitalen Signaturen enthält.
   * Ein `PKIOptions`-Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions`-Instanz, die SPI-Informationen enthält. Sie können für diesen Parameter null angeben.

   Die Methode `verifyPDFDocument` gibt ein `PDFDocumentVerificationInfo`-Objekt zurück, das Informationen über alle digitalen Signaturen im PDF-Dokument enthält.

1. Iteration durch alle Signaturen

   * Iterieren Sie durch alle Signaturen, indem Sie das Datenelement `verificationInfos` des `PDFDocumentVerificationInfo`-Objekts abrufen. Dieses Datenelement gibt ein `Object`-Array zurück, in dem jedes Element ein `PDFSignatureVerificationInfo`-Objekt ist.
   * Mithilfe des `PDFSignatureVerificationInfo`-Objekts können Sie Aufgaben ausführen wie die Bestimmung des Signaturstatus, indem Sie das Datenelement `status` des `PDFSignatureVerificationInfo`-Objekts aufrufen. Dieses Datenelement gibt ein `SignatureStatus`-Objekt zurück, dessen statisches Datenelement Sie über den Status der Signatur informiert. Wenn die Signatur beispielsweise unbekannt ist, gibt diese Methode `SignatureStatus.DocumentSignatureUnknown` zurück.

**Siehe auch**

[Überprüfen mehrerer digitaler Signaturen](#verifying-multiple-digital-signatures)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Entfernen von digitalen Signaturen {#removing-digital-signatures}

Digitale Signaturen müssen aus einem Signaturfeld entfernt werden, bevor eine neuere digitale Signatur angewendet werden kann. Eine digitale Signatur kann nicht überschrieben werden. Wenn Sie versuchen, eine digitale Signatur auf ein Signaturfeld anzuwenden, das bereits eine Signatur enthält, tritt eine Ausnahme auf.

>[!NOTE]
>
>Weitere Informationen zum Signature-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Führen Sie die folgenden Aufgaben aus, um eine digitale Signatur aus einem Signaturfeld zu entfernen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signatur-Client.
1. Rufen Sie das PDF-Dokument ab, das eine zu entfernende Signatur enthält.
1. Entfernen Sie die digitale Signatur aus dem Signaturfeld.
1. Speichern Sie das Formular als PDF-Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Signature-Clients**

Bevor Sie einen Signature-Service-Vorgang programmgesteuert ausführen können, müssen Sie einen Signature-Service-Client erstellen.

**Abrufen des PDF-Dokuments, das eine Signatur zum Entfernen enthält**

Um eine Signatur aus einem PDF-Dokument zu entfernen, müssen Sie ein PDF-Dokument abrufen, das eine Signatur enthält.

**Entfernen der digitalen Signatur aus dem Signaturfeld**

Um eine digitale Signatur erfolgreich aus einem PDF-Dokument zu entfernen, müssen Sie den Namen des Signaturfelds angeben, das die digitale Signatur enthält. Außerdem müssen Sie über die Berechtigung zum Entfernen der digitalen Signatur verfügen. Andernfalls tritt eine Ausnahme auf.

**Speichern des PDF-Dokuments als PDF-Datei**

Nachdem der Signature-Service eine digitale Signatur aus einem Signaturfeld entfernt hat, können Sie das PDF-Dokument als PDF-Datei speichern, damit Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Entfernen digitaler Signaturen mithilfe der Java-API](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-java-api)

[Entfernen digitaler Signaturen mithilfe der Webservice-API](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Hinzufügen von Signaturfeldern](digitally-signing-certifying-documents.md#adding-signature-fields)

### Entfernen digitaler Signaturen mithilfe der Java-API {#remove-digital-signatures-using-the-java-api}

So entfernen Sie eine digitale Signatur mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-signatures-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Signatur-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen des PDF-Dokuments, das eine zu entfernende Signatur enthält

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt, welches die zu entfernende Signatur enthält, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen der digitalen Signatur aus dem Signaturfeld

   Entfernen Sie eine digitale Signatur aus einem Signaturfeld, indem Sie die Methode `clearSignatureField` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, das das PDF-Dokument darstellt, welches die zu entfernende Signatur enthält.
   * Ein Zeichenfolgewert für den Namen des Signaturfelds, das eine Signatur enthält.

   Die `clearSignatureField`-Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, welches das PDF-Dokument darstellt, aus dem die digitale Signatur entfernt wurde.

1. Das PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die Methode `copyToFile` des `com.adobe.idp.Document`-Objekts auf. Übergeben Sie das `java.io.File`-Objekt, um den Inhalt des `com.adobe.idp.Document`-Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `clearSignatureField`-Methode zurückgegeben wurde.

**Siehe auch**

[Entfernen von digitalen Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Schnellstart (SOAP-Modus): Digitale Signatur mit der Java-API entfernen](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Entfernen digitaler Signaturen mithilfe der Webservice-API {#remove-digital-signatures-using-the-web-service-api}

Entfernen einer digitalen Signatur mithilfe der Signature-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Signatur-Clients

   * Erstellen Sie mithilfe des betreffenden Standardkonstruktors ein `SignatureServiceClient`-Objekt.
   * Erstellen Sie mithilfe des `System.ServiceModel.EndpointAddress`-Konstruktors ein `SignatureServiceClient.Endpoint.Address`-Objekt. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Das Attribut `lc_version` muss nicht verwendet werden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `SignatureServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Stellen Sie das Feld `MessageEncoding` des Objekts `System.ServiceModel.BasicHttpBinding` auf `WSMessageEncoding.Mtom` ein. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `SignatureServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Abrufen des PDF-Dokuments, das eine zu entfernende Signatur enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments, das eine zu entfernende digitale Signatur enthält, verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des signierten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays ermitteln, indem Sie die Eigenschaft `Length` des `System.IO.FileStream`-Objekts abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten auf, indem Sie die Methode `Read` des `System.IO.FileStream`-Objekts aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt durch Zuweisen seiner `MTOM`-Eigenschaft mit dem Inhalt des Byte-Arrays.

1. Entfernen der digitalen Signatur aus dem Signaturfeld

   Entfernen Sie die digitale Signatur, indem Sie die Methode `clearSignatureField` des `SignatureServiceClient`-Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, welches das signierte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfeldes angibt, das die zu entfernende digitale Signatur enthält.

   Die `clearSignatureField`-Methode gibt ein `BLOB`-Objekt zurück, welches das PDF-Dokument darstellt, aus dem die digitale Signatur entfernt wurde.

1. Das PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das ein leeres Signaturfeld enthält, und den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB`-Objekts speichert, das von der `sign`-Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Datenelements `MTOM` des `BLOB`-Objekts abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in die PDF-Datei, indem Sie die Methode `Write` des `System.IO.BinaryWriter`-Objekts aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Entfernen von digitalen Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
