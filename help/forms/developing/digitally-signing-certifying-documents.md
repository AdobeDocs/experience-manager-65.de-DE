---
title: Digitales Signieren und Zertifizieren von Dokumenten
seo-title: Digitales Signieren und Zertifizieren von Dokumenten
description: 'null'
seo-description: 'null'
uuid: 6331de8a-2a9c-45bf-89d2-29f1ad5cc856
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 42de04bf-25e4-4478-a411-38671ed871ae
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '16977'
ht-degree: 8%

---


# Digitales Signieren und Zertifizieren von Dokumenten {#digitally-signing-and-certifying-documents}

**Info zum Signature-Dienst**

Mit dem Signature-Dienst kann Ihr Unternehmen die Sicherheit und den Datenschutz von Adobe PDF-Dokumenten schützen, die es verteilt und empfängt. Dieser Dienst verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur vorgesehene Empfänger Dokumente ändern können. Da Sicherheitsfunktionen auf das Dokument selbst angewendet werden, bleibt das Dokument während seines gesamten Lebenszyklus sicher und kontrolliert. Ein Dokument bleibt über die Firewall hinaus geschützt, wenn es offline heruntergeladen und an Ihr Unternehmen zurückgesendet wird.

>[!NOTE]
>
>Sie können einen benutzerdefinierten Unterschriften-Handler für den Signature-Dienst erstellen, der aufgerufen wird, wenn bestimmte Vorgänge aufgerufen werden, z. B. das Signieren eines PDF-Dokuments.

**Namen von Unterschriftsfeldern**

Bei einigen Signature-Dienstvorgängen müssen Sie den Namen des Signaturfelds angeben, für das ein Vorgang ausgeführt wird. Wenn Sie beispielsweise ein PDF-Dokument signieren, geben Sie den Namen des Signaturfelds an, das signiert werden soll. Angenommen, der vollständige Name eines Unterschriftsfelds ist `form1[0].Form1[0].SignatureField1[0]`vorhanden. Sie können `SignatureField1[0]` anstelle von `form1[0].Form1[0].SignatureField1[0]`angeben.

Manchmal führt ein Konflikt dazu, dass der Signature-Dienst das falsche Feld signiert (oder einen anderen Vorgang ausführt, für den der Signaturfeldname erforderlich ist). Dieser Konflikt resultiert aus dem Namen, der an zwei oder mehr Stellen im gleichen PDF-Dokument `SignatureField1[0]` angezeigt wird. Angenommen, ein PDF-Dokument enthält zwei Unterschriftsfelder mit dem Namen `form1[0].Form1[0].SignatureField1[0]` und `form1[0].Form1[0].SubForm1[0].SignatureField1[0]` den Sie angeben `SignatureField1[0]`. In diesem Fall signiert der Signature-Dienst das erste Signaturfeld, das er findet, während er alle Signaturfelder im Dokument durchläuft.

Wenn sich in einem PDF-Dokument mehrere Unterschriftsfelder befinden, sollten Sie die vollständigen Namen der Unterschriftsfelder angeben. Das heißt, spezifizieren Sie `form1[0].Form1[0].SignatureField1[0]`statt `SignatureField1[0]`.

Sie können diese Aufgaben mithilfe des Signature-Dienstes ausführen:

* Hinzufügen und löschen Sie digitale Unterschriftsfelder in einem PDF-Dokument. (Siehe [Hinzufügen von Unterschriftsfeldern](digitally-signing-certifying-documents.md#adding-signature-fields).)
* Rufen Sie die Namen der Signaturfelder in einem PDF-Dokument ab. (Siehe [Abrufen von Signaturfeldnamen](digitally-signing-certifying-documents.md#retrieving-signature-field-names).)
* Signaturfelder ändern (Siehe [Unterschriftsfelder](digitally-signing-certifying-documents.md#modifying-signature-fields)ändern.)
* PDF-Dokumente digital signieren (See [Digitally Signing PDF Documents](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)
* PDF-Dokumente zertifizieren. (See [Certifying PDF Documents](digitally-signing-certifying-documents.md#certifying-pdf-documents).)
* Digitale Signaturen in einem PDF-Dokument überprüfen (Siehe [Digitale Signaturen](digitally-signing-certifying-documents.md#verifying-digital-signatures)überprüfen.)
* Validieren Sie alle digitalen Signaturen in einem PDF-Dokument. (See [Verifying Multiple Digital Signatures](digitally-signing-certifying-documents.md#verifying-digital-signatures).)
* Entfernen Sie eine digitale Signatur aus einem Signaturfeld. (Siehe [Digitale Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures)entfernen.)

>[!NOTE]
>
>For more information about the Signature service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)..

## Signaturfelder hinzufügen {#adding-signature-fields}

Digitale Signaturen werden in Signaturfeldern angezeigt, die eine grafische Darstellung der Signatur enthaltende Formularfelder sind. Signaturfelder können sichtbar oder unsichtbar sein. Unterzeichner können ein bereits vorhandenes Unterschriftsfeld verwenden oder ein Unterschriftsfeld programmgesteuert hinzugefügt werden. In beiden Fällen muss das Signaturfeld vorhanden sein, bevor ein PDF-Dokument signiert werden kann.

Sie können ein Signaturfeld programmgesteuert hinzufügen, indem Sie die Signature-Dienst-Java-API oder die Signature-Webdienst-API verwenden. Sie können einem PDF-Dokument mehrere Unterschriftsfelder hinzufügen. Jeder Signaturfeldname muss jedoch eindeutig sein.

>[!NOTE]
>
>Bei einigen PDF-Dokument-Typen können Sie kein Unterschriftsfeld programmatisch hinzufügen. Weitere Informationen zum Signature-Dienst und zum Hinzufügen von Signaturfeldern finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So fügen Sie einem PDF-Dokument ein Unterschriftsfeld hinzu:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie ein PDF-Dokument ab, dem ein Unterschriftsfeld hinzugefügt wird.
1. Hinzufügen ein Unterschriftsfeld.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

**Signaturclient erstellen**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument abrufen, dem ein Unterschriftsfeld hinzugefügt wird**

Sie müssen ein PDF-Dokument abrufen, dem ein Unterschriftsfeld hinzugefügt wird.

**Signaturfeld Hinzufügen**

Um einem PDF-Dokument erfolgreich ein Unterschriftsfeld hinzuzufügen, geben Sie Koordinatenwerte an, die die Position des Unterschriftsfelds angeben. (Wenn Sie ein unsichtbares Unterschriftsfeld hinzufügen, sind diese Werte nicht erforderlich.) Sie können auch angeben, welche Felder im PDF-Dokument gesperrt werden, nachdem eine Unterschrift auf das Unterschriftsfeld angewendet wurde.

**PDF-Dokument als PDF-Datei speichern**

Nachdem der Signature-Dienst dem PDF-Dokument ein Signaturfeld hinzugefügt hat, können Sie das Dokument als PDF-Datei speichern, damit die Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Hinzufügen Signaturfelder mit der Java-API {#add-signature-fields-using-the-java-api}

Hinzufügen eines Signaturfelds mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-signatures-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Signaturclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, dem ein Unterschriftsfeld hinzugefügt wird

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument darstellt, dem ein Unterschriftsfeld hinzugefügt wird, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Signaturfeld Hinzufügen

   * Erstellen Sie ein `PositionRectangle` Objekt, das die Position des Unterschriftsfelds mithilfe des Konstruktors angibt. Geben Sie im Konstruktor Koordinatenwerte an.
   * Erstellen Sie bei Bedarf ein `FieldMDPOptions` Objekt, das die Felder angibt, die gesperrt werden, wenn eine digitale Unterschrift auf das Unterschriftsfeld angewendet wird.
   * Hinzufügen Sie ein Unterschriftsfeld an ein PDF-Dokument, indem Sie die `SignatureServiceClient` `addSignatureField` Objektmethode aufrufen und die folgenden Werte übergeben:

      * A `com.adobe.idp`. `Document` -Objekt, das das PDF-Dokument darstellt, dem ein Unterschriftsfeld hinzugefügt wird.
      * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt.
      * Ein `java.lang.Integer` Wert, der die Seitenzahl darstellt, der ein Unterschriftsfeld hinzugefügt wird.
      * Ein `PositionRectangle` Objekt, das die Position des Unterschriftsfelds angibt.
      * Ein `FieldMDPOptions` Objekt, das Felder im PDF-Dokument angibt, die nach dem Anwenden einer digitalen Unterschrift auf das Unterschriftsfeld gesperrt werden. Dieser Parameterwert ist optional und Sie können ihn übergeben `null`.
   * Ein `PDFSeedValueOptions` Objekt, das verschiedene Laufzeitwerte angibt. Dieser Parameterwert ist optional und Sie können ihn übergeben `null`.

      Die `addSignatureField` Methode gibt eine `com.adobe.idp`zurück. `Document` Objekt, das ein PDF-Dokument mit einem Unterschriftsfeld darstellt.
   >[!NOTE]
   >
   >Sie können die `SignatureServiceClient` Methode des `addInvisibleSignatureField` Objekts aufrufen, um ein unsichtbares Unterschriftsfeld hinzuzufügen.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `com.adobe.idp`auf. `Document` - `copyToFile` Methode verwenden, um den Inhalt des `Document` Objekts in die Datei zu kopieren. Vergewissern Sie sich, dass Sie die Variable `com.adobe.idp`verwenden. `Document` -Objekt, das von der `addSignatureField` Methode zurückgegeben wurde.

**Siehe auch**

[Beginn zur Signature Service API](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

### Hinzufügen Unterschriftsfelder mit der Webdienst-API {#add-signature-fields-using-the-web-service-api}

So fügen Sie mithilfe der Signature-API (Webdienst) ein Signaturfeld hinzu:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument abrufen, dem ein Unterschriftsfeld hinzugefügt wird

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des PDF-Dokuments verwendet, das ein Unterschriftsfeld enthält.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `MTOM` Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Signaturfeld Hinzufügen

   Hinzufügen Sie ein Unterschriftsfeld an das PDF-Dokument, indem Sie die `SignatureServiceClient` `addSignatureField` Objektmethode aufrufen und die folgenden Werte übergeben:

   * A `BLOB` object that represents the PDF document to which a signature field is added.
   * Ein Zeichenfolgenwert, der den Signaturfeldnamen angibt.
   * Ein ganzzahliger Wert, der die Seitenzahl darstellt, der ein Unterschriftsfeld hinzugefügt wird.
   * Ein `PositionRect` Objekt, das die Position des Unterschriftsfelds angibt.
   * Ein `FieldMDPOptions` Objekt, das Felder im PDF-Dokument angibt, die nach dem Anwenden einer digitalen Unterschrift auf das Unterschriftsfeld gesperrt werden. Dieser Parameterwert ist optional und Sie können ihn übergeben `null`.
   * Ein `PDFSeedValueOptions` Objekt, das verschiedene Laufzeitwerte angibt. Dieser Parameterwert ist optional und Sie können ihn übergeben `null`.

   Die `addSignatureField` Methode gibt ein `BLOB` Objekt zurück, das ein PDF-Dokument mit einem Unterschriftsfeld darstellt.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das das Signaturfeld enthalten soll, sowie den Dateimodus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das von der `addSignatureField` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `binaryData` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Signaturfeldnamen abrufen {#retrieving-signature-field-names}

Sie können die Namen aller Signaturfelder abrufen, die sich in einem zu signierenden und zertifizierenden PDF-Dokument befinden. Wenn Sie nicht sicher sind, wie die Signaturfeldnamen in einem PDF-Dokument lauten oder die Namen prüfen möchten, können Sie diese programmgesteuert abrufen. The Signature service returns the fully qualified name of the signature field, such as `form1[0].grantApplication[0].page1[0].SignatureField1[0]`.

>[!NOTE]
>
>For more information about the Signature service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)

### Zusammenfassung der Schritte {#summary_of_steps-1}

So rufen Sie Signaturfeldnamen ab:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument mit Unterschriftsfeldern ab.
1. Rufen Sie die Signaturfeldnamen ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Signaturclient erstellen**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument mit Unterschriftsfeldern abrufen**

Rufen Sie ein PDF-Dokument mit Unterschriftsfeldern ab.

**Signaturfeldnamen abrufen**

Sie können Signaturfeldnamen abrufen, nachdem Sie ein PDF-Dokument abgerufen haben, das ein oder mehrere Unterschriftsfelder enthält.

**Siehe auch**

[Signaturfeldnamen mit der Java-API abrufen](digitally-signing-certifying-documents.md#retrieve-signature-field-names-using-the-java-api)

[Signaturfeld mit der Webdienst-API abrufen](digitally-signing-certifying-documents.md#retrieve-signature-field-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

### Signaturfeldnamen mit der Java-API abrufen {#retrieve-signature-field-names-using-the-java-api}

Signaturfeldnamen mithilfe der Signature-API (Java) abrufen:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-signatures-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Signaturclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument mit Unterschriftsfeldern abrufen

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument mit Unterschriftsfeldern darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Signaturfeldnamen abrufen

   * Rufen Sie die Unterschriftsfeldnamen ab, indem Sie die `SignatureServiceClient` Objektmethode aufrufen und das `getSignatureFieldList` `com.adobe.idp.Document` Objekt übergeben, das das PDF-Dokument mit Unterschriftsfeldern enthält. Diese Methode gibt ein `java.util.List` Objekt zurück, in dem jedes Element ein `PDFSignatureField` Objekt enthält. Mit diesem Objekt können Sie zusätzliche Informationen zu einem Unterschriftsfeld abrufen, z. B. ob es sichtbar ist.
   * Durchlaufen Sie das `java.util.List` Objekt, um festzustellen, ob Signaturfeldnamen vorhanden sind. Für jedes Unterschriftsfeld im PDF-Dokument können Sie ein separates `PDFSignatureField` Objekt abrufen. Um den Namen des Unterschriftsfelds abzurufen, rufen Sie die `PDFSignatureField` Objektmethode `getName` auf. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Signaturfeldnamen angibt.

**Siehe auch**

[Signaturfeldnamen abrufen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Quick Beginn (SOAP-Modus): Abrufen von Signaturfeldnamen mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-retrieving-signature-field-names-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Signaturfeld mit der Webdienst-API abrufen {#retrieve-signature-field-using-the-web-service-api}

Signaturfeldnamen mit der Signature-API abrufen (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument mit Unterschriftsfeldern abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des PDF-Dokuments verwendet, das Unterschriftsfelder enthält.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Signaturfeldnamen abrufen

   * Rufen Sie die Unterschriftsfeldnamen ab, indem Sie die `SignatureServiceClient` Objektmethode aufrufen und das `getSignatureFieldList` `BLOB` Objekt übergeben, das das PDF-Dokument mit Unterschriftsfeldern enthält. Diese Methode gibt ein `MyArrayOfPDFSignatureField` Collection-Objekt zurück, in dem jedes Element ein `PDFSignatureField` Objekt enthält.
   * Durchlaufen Sie das `MyArrayOfPDFSignatureField` Objekt, um zu ermitteln, ob Signaturfeldnamen vorhanden sind. Für jedes Unterschriftsfeld im PDF-Dokument können Sie ein `PDFSignatureField` Objekt abrufen. Um den Namen des Unterschriftsfelds abzurufen, rufen Sie die `PDFSignatureField` Objektmethode `getName` auf. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Signaturfeldnamen angibt.

**Siehe auch**

[Signaturfeldnamen abrufen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Modifying Signature Fields {#modifying-signature-fields}

Sie können Signaturfelder in einem PDF-Dokument mithilfe der Java-API und der Webdienst-API ändern. Das Ändern eines Signaturfelds umfasst das Manipulieren seiner Signaturfeldsperre- oder Seed-Wert-Lexikonwerte.

A *field lock dictionary* specifies a list of fields that are locked when the signature field is signed. Ein gesperrtes Feld verhindert, dass Benutzer Änderungen an dem Feld vornehmen. A *seed value dictionary* contains constraining information that is used at the time the signature is applied. Beispiel: Sie können die Berechtigungen ändern, die Aktionen steuern, die auftreten können, ohne dass eine Signatur ungültig wird.

Durch Ändern eines vorhandenen Unterschriftsfelds können Sie Änderungen am PDF-Dokument vornehmen, um den sich ändernden Geschäftsanforderungen Rechnung zu tragen. Eine neue Geschäftsanforderung kann beispielsweise die Sperrung aller Dokument-Felder nach der Unterzeichnung des Dokuments erfordern.

In diesem Abschnitt wird beschrieben, wie Sie ein Unterschriftsfeld ändern, indem Sie sowohl die Wörterbuchwerte für Feldsperre als auch die Wörterbuchwerte für Seed-Werte ändern. Änderungen am Unterschriftsfeld-Sperrwörterbuch führen dazu, dass alle Felder im PDF-Dokument gesperrt werden, wenn ein Unterschriftsfeld unterschrieben wird. Änderungen am Wörterbuch für Seed-Werte verbieten bestimmte Änderungen am Dokument.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Ändern von Signaturfeldern finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

So ändern Sie Signaturfelder in einem PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das das zu ändernde Unterschriftsfeld enthält.
1. Legen Sie Wörterbuchwerte fest.
1. Ändern Sie das Unterschriftsfeld.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

For information about the location of these JAR files, see [Including LiveCycle Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Signaturclient erstellen**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument abrufen, das das zu ändernde Unterschriftsfeld enthält**

Rufen Sie ein PDF-Dokument ab, das das zu ändernde Unterschriftsfeld enthält.

**Festlegen von Wörterbuchwerten**

Um ein Unterschriftsfeld zu ändern, weisen Sie seinem Feldsperrwörterbuch oder Seed-Wert-Wörterbuch Werte zu. Die Angabe von Wörterbuchwerten für die Sperrung von Unterschriftsfeldern umfasst die Angabe von PDF-Dokument-Feldern, die beim Unterschreiben des Unterschriftsfelds gesperrt werden. (In diesem Abschnitt wird beschrieben, wie Sie alle Felder sperren.)

Folgende Wörterbuchwerte für Seed-Werte können festgelegt werden:

* **Überprüfung** von Überarbeitungen: Gibt an, ob eine Sperrüberprüfung durchgeführt wird, wenn eine Unterschrift auf das Unterschriftsfeld angewendet wird.
* **Zertifikatoptionen**: Weist dem Wörterbuch mit dem Seed-Wert des Zertifikats Werte zu. Bevor Sie Zertifikatoptionen festlegen, sollten Sie sich mit einem Wörterbuch mit dem Seed-Wert des Zertifikats vertraut machen. (Siehe [PDF-Referenz](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Digest-Optionen**: Weist Digest-Algorithmen zu, die zum Signieren verwendet werden. Gültige Werte sind SHA1, SHA256, SHA384, SHA512 und RIPEMD160.
* **Filter**: Gibt den Filter an, der mit dem Unterschriftsfeld verwendet wird. Sie können beispielsweise den Filter Adobe.PPKLite verwenden. (Siehe [PDF-Referenz](https://www.adobe.com/devnet/acrobat/pdfs/pdf_reference_1-7.pdf).)
* **Flag-Optionen**: Gibt die mit diesem Unterschriftsfeld verknüpften Flag-Werte an. Der Wert 1 bedeutet, dass ein Unterzeichner nur die angegebenen Werte für den Eintrag verwenden muss. Der Wert 0 bedeutet, dass andere Werte zulässig sind. Die Bit-Positionen lauten wie folgt:

   * **1(Filter):** Der Signatur-Handler, der zum Signieren des Signaturfelds verwendet wird
   * **2 (SubFilter):** Ein Array mit Namen, die für die Signatur zu verwendende Kodierungen zulässig sind
   * **3 (V)**: Die erforderliche MindestVersionsnummer des Unterschriften-Handlers, der zum Unterschriftsfeld verwendet wird
   * **4 (Gründe):** Ein Zeichenfolgen-Array, das die möglichen Gründe für die Unterzeichnung eines Dokuments angibt
   * **5 (PDFLegalWarnungen):** Ein Zeichenfolgen-Array, das mögliche rechtliche Bezeichnungen angibt

* **Rechtliche Bescheinigungen**: Wenn ein Dokument zertifiziert ist, wird es automatisch auf bestimmte Inhaltstypen überprüft, die den sichtbaren Inhalt eines Dokuments mehrdeutig oder irreführend machen können. Eine Anmerkung kann beispielsweise Text verdecken, der wichtig ist, um zu verstehen, was zertifiziert wird. Der Scanvorgang generiert Warnungen, die auf das Vorhandensein dieses Inhaltstyps hinweisen. Er enthält außerdem eine zusätzliche Erläuterung des Inhalts, der möglicherweise Warnungen generiert hat.
* **Berechtigungen**: Gibt Berechtigungen an, die für ein PDF-Dokument verwendet werden können, ohne dass die Unterschrift ungültig wird.
* **Gründe**: Gibt Gründe an, aus denen dieses Dokument unterzeichnet werden muss.
* **Zeitstempel**: Gibt Zeitstempeloptionen an. Sie können beispielsweise die URL des verwendeten Zeitstempelservers festlegen.
* **Version**: Gibt die Mindestversionsnummer des Unterschriften-Handlers an, der zum Unterschreiben des Unterschriftsfelds verwendet werden soll.

**Signaturfeld ändern**

Nachdem Sie einen Signature-Dienst-Client erstellt haben, das PDF-Dokument abrufen, das das zu ändernde Signaturfeld enthält, und die Wörterbuchwerte festlegen, können Sie den Signature-Dienst anweisen, das Signaturfeld zu ändern. Der Signature-Dienst gibt dann ein PDF-Dokument zurück, das das geänderte Signaturfeld enthält. Das Original-PDF-Dokument ist davon nicht betroffen.

**PDF-Dokument als PDF-Datei speichern**

Speichern Sie das PDF-Dokument, das das geänderte Unterschriftsfeld enthält, als PDF-Datei, damit die Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Signature Service API](/help/forms/developing/signature-service-java-api-quick.md#signature-service-java-api-quick-start-soap)

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

### Signaturfelder mit der Java-API ändern {#modify-signature-fields-using-the-java-api}

Signaturfelder mithilfe der Signature-API (Java) ändern:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien, wie z. B. &quot;adobe-signatures-client.jar&quot;, in den Klassenpfad Ihres Java-Projekts ein.

1. Signaturclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das das zu ändernde Unterschriftsfeld enthält

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument darstellt, das das zu ändernde Unterschriftsfeld enthält, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von Wörterbuchwerten

   * Erstellen Sie ein Objekt `PDFSignatureFieldProperties`, indem Sie den Konstruktor verwenden. Ein `PDFSignatureFieldProperties` Objekt speichert Signaturfeld-Sperrwörterbuch und Seed-Wert-Wörterbuch-Informationen.
   * Erstellen Sie ein Objekt `PDFSeedValueOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Wörterbuchwerte für Seed-Werte festlegen.
   * Deaktivieren Sie Änderungen am PDF-Dokument, indem Sie die `PDFSeedValueOptionSpec` Objektmethode aufrufen und den Wert für die `setMdpValue` `MDPPermissions.NoChanges` Auflistung übergeben.
   * Erstellen Sie ein Objekt `FieldMDPOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie die Werte für die Sperrung von Unterschriftsfeldern festlegen.
   * Sperren Sie alle Felder im PDF-Dokument, indem Sie die `FieldMDPOptionSpec` Objektmethode aufrufen und den Wert für die `setMdpValue` `FieldMDPAction.ALL` Auflistung übergeben.
   * Legen Sie Wörterbuchinformationen zum Seed-Wert fest, indem Sie die `PDFSignatureFieldProperties` Methode des `setSeedValue` Objekts aufrufen und das `PDFSeedValueOptionSpec` Objekt übergeben.
   * Legen Sie die Wörterbuchinformationen zum Sperren von Unterschriftsfeldern fest, indem Sie die `PDFSignatureFieldProperties`Methode des `setFieldMDP` Objekts aufrufen und das `FieldMDPOptionSpec` Objekt übergeben.

   >[!NOTE]
   >
   >Informationen zu allen von Ihnen festgelegten Wörterbuchwerten für Seed-Werte finden Sie in der `PDFSeedValueOptionSpec` Klassenreferenz. (Siehe API-Referenz zu [AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

1. Signaturfeld ändern

   Ändern Sie das Unterschriftsfeld, indem Sie die `SignatureServiceClient` Methode des `modifySignatureField` Objekts aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document` Objekt, in dem das PDF-Dokument mit dem zu ändernden Unterschriftsfeld gespeichert wird
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt
   * Das `PDFSignatureFieldProperties` Objekt, in dem das Wörterbuch für die Sperrung von Signaturfeldern und das Wörterbuch für den Seed-Wert gespeichert werden

   Die `modifySignatureField` Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das ein PDF-Dokument speichert, das das geänderte Unterschriftsfeld enthält.

1. PDF-Dokument als PDF-Datei speichern

   * Create a `java.io.File` object and ensure that the file name extension is .pdf.
   * Invoke the `com.adobe.idp.Document` object’s `copyToFile` method to copy the contents of the `com.adobe.idp.Document` object to the file. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document` Objekt verwenden, das von der `modifySignatureField` Methode zurückgegeben wurde.

### Signaturfelder mithilfe der Web-Service-API ändern {#modify-signature-fields-using-the-web-service-api}

Ändern Sie ein Signaturfeld mithilfe der Signature-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument abrufen, das das zu ändernde Unterschriftsfeld enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern des PDF-Dokuments verwendet, das das zu ändernde Unterschriftsfeld enthält.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie dessen `MTOM` Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von Wörterbuchwerten

   * Erstellen Sie ein Objekt `PDFSignatureFieldProperties`, indem Sie den Konstruktor verwenden. Dieses Objekt speichert die Wörterbücher für die Sperrung von Unterschriftsfeldern und die Wörterbuchinformationen für Seed-Werte.
   * Erstellen Sie ein Objekt `PDFSeedValueOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie Wörterbuchwerte für Seed-Werte festlegen.
   * Deaktivieren Sie Änderungen am PDF-Dokument, indem Sie den Wert für die `MDPPermissions.NoChanges` Auflistung dem `PDFSeedValueOptionSpec` `mdpValue` Datenmember des Objekts zuweisen.
   * Erstellen Sie ein Objekt `FieldMDPOptionSpec`, indem Sie den Konstruktor verwenden. Mit diesem Objekt können Sie die Werte für die Sperrung von Unterschriftsfeldern festlegen.
   * Sperren Sie alle Felder im PDF-Dokument, indem Sie den Wert für die `FieldMDPAction.ALL` Auflistung dem `FieldMDPOptionSpec` `mdpValue` Datenmember des Objekts zuweisen.
   * Legen Sie Wörterbuchinformationen zum Seed-Wert fest, indem Sie das `PDFSeedValueOptionSpec` Objekt dem `PDFSignatureFieldProperties` Datenmember des Objekts zuweisen `seedValue` .
   * Legen Sie die Wörterbuchinformationen zum Sperren von Unterschriftsfeldern fest, indem Sie das `FieldMDPOptionSpec` Objekt dem `PDFSignatureFieldProperties` `fieldMDP` Datenmember des Objekts zuweisen.

   >[!NOTE]
   >
   >Informationen zu allen von Ihnen festgelegten Wörterbuchwerten für Seed-Werte finden Sie in der `PDFSeedValueOptionSpec` Klassenreferenz. (Siehe API-Referenz zu [AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

1. Signaturfeld ändern

   Ändern Sie das Unterschriftsfeld, indem Sie die `SignatureServiceClient` Methode des `modifySignatureField` Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB` Objekt, in dem das PDF-Dokument mit dem zu ändernden Unterschriftsfeld gespeichert wird
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt
   * Das `PDFSignatureFieldProperties` Objekt, in dem das Wörterbuch für die Sperrung von Signaturfeldern und das Wörterbuch für den Seed-Wert gespeichert werden

   Die `modifySignatureField` Methode gibt ein `BLOB` Objekt zurück, das ein PDF-Dokument speichert, das das geänderte Unterschriftsfeld enthält.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das das Signaturfeld enthalten soll, sowie den Dateimodus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das von der `addSignatureField` Methode zurückgegeben wird. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Digitally Signing PDF Documents {#digitally-signing-pdf-documents}

Digitale Signaturen können zu Sicherheitszwecken auf PDF-Dokumente angewendet werden. Digitale Signaturen bieten wie handschriftliche Signaturen ein Mittel, mit dem sich die Unterzeichner identifizieren und zum Dokument Stellung nehmen. Die zum digitalen Signieren verwendete Technologie stellt sicher, dass sowohl der Unterzeichner als auch die Empfänger genau wissen, was signiert wurde und dass das Dokument nach dem Signieren nicht geändert wurde.

PDF-Dokumente werden mittels der Technologie öffentlicher Schlüssel signiert. Ein Unterzeichner hat zwei Schlüssel: einen öffentlichen Schlüssel und einen privaten Schlüssel. Der private Schlüssel wird in der Berechtigung eines Benutzers gespeichert, die zum Zeitpunkt der Unterzeichnung verfügbar sein muss. Der öffentliche Schlüssel wird im Benutzerzertifikat gespeichert, das den Empfängern zur Überprüfung der Unterschrift zur Verfügung stehen muss. Informationen zu gesperrten Zertifikaten finden Sie in den Zertifikatsperrlisten (CRLs) und den Antworten des Online-Zertifikatstatusprotokolls (OCSP), die von Zertifizierungsstellen (CAs) verteilt werden. Der Zeitpunkt der Signatur kann von einer vertrauenswürdigen Quelle, die als Zeitstempeldienst bezeichnet wird, erhalten werden.

>[!NOTE]
>
>Bevor Sie ein PDF-Dokument digital signieren können, müssen Sie sicherstellen, dass das Zertifikat den AEM Forms hinzugefügt wird. Ein Zertifikat wird mithilfe von Administration Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Berechtigungen mithilfe der Trust Manager-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api)importieren.)

Sie können PDF-Dokumente programmgesteuert digital signieren. Beim digitalen Signieren eines PDF-Dokuments müssen Sie auf eine Sicherheitsberechtigung verweisen, die in AEM Forms vorhanden ist. Die Anmeldedaten bestehen aus dem zum Signieren verwendeten privaten Schlüssel.

Der Signature-Dienst führt die folgenden Schritte aus, wenn ein PDF-Dokument signiert wird:

1. Der Signature-Dienst ruft die Berechtigung aus dem Truststore ab, indem er den in der Anforderung angegebenen Alias übergibt.
1. Der Truststore sucht nach der angegebenen Berechtigung.
1. Die Berechtigung wird an den Signature-Dienst zurückgegeben und zum Signieren des Dokuments verwendet. Die Berechtigung wird auch gegen den Alias für zukünftige Anforderungen zwischengespeichert.

Informationen zum Umgang mit den Sicherheitsberechtigungen finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

>[!NOTE]
>
>Es gibt Unterschiede zwischen dem Unterzeichnen und Zertifizieren von Dokumenten. (See [Certifying PDF Documents](digitally-signing-certifying-documents.md#certifying-pdf-documents).)

>[!NOTE]
>
>Nicht alle PDF-Dokumente unterstützen das Signieren. Weitere Informationen zum Signature-Dienst und zu Dokumenten mit Digitalsignatur finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Der Signature-Dienst unterstützt keine XDP-Dateien mit eingebetteten PDF-Daten als Eingabe für einen Vorgang, z. B. das Zertifizieren eines Dokuments. Diese Aktion führt dazu, dass der Signature-Dienst eine `PDFOperationException`. Um dieses Problem zu beheben, konvertieren Sie die XDP-Datei mithilfe des PDF Utilities-Dienstes in eine PDF-Datei und übergeben Sie dann die konvertierte PDF-Datei an einen Signature-Dienst-Vorgang. (Siehe [Arbeiten mit PDF-Dienstprogrammen](/help/forms/developing/pdf-utilities.md#working-with-pdf-utilities).)

**OpenShield-HSM-Berechtigung**

Bei Verwendung einer OpenShield-HSM-Berechtigung zum Signieren oder Zertifizieren eines PDF-Dokuments kann die neue Berechtigung erst verwendet werden, wenn der J2EE-Anwendungsserver, auf dem AEM Forms bereitgestellt sind, neu gestartet wurde. Sie können jedoch einen Konfigurationswert festlegen, der dazu führt, dass der Vorgang zum Signieren oder Zertifizieren funktioniert, ohne den J2EE-Anwendungsserver neu zu starten.

Sie können den folgenden Konfigurationswert in der Datei &quot;cknfastrc&quot;hinzufügen, die sich unter &quot;/opt/nfast/cknfastrc&quot;(oder &quot;c:\nfast\cknfastrc&quot;) befindet:

```as3
 CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nachdem Sie diesen Konfigurationswert zur cknfastrc-Datei hinzugefügt haben, können Sie die neue Berechtigung verwenden, ohne den J2EE-Anwendungsserver neu zu starten.

**Unterschrift ist nicht vertrauenswürdig**

Beim Zertifizieren und Signieren desselben PDF-Dokuments wird beim Öffnen des PDF-Dokuments in Acrobat oder Adobe Reader ein gelbes Dreieck gegen die erste Unterschrift angezeigt, wenn die Zertifizierungsunterschrift nicht vertrauenswürdig ist. Die zertifizierende Signatur muss als vertrauenswürdig eingestuft werden, um dies zu vermeiden.

**Signieren von Dokumenten, die XFA-basierte Formulare sind**

Wenn Sie versuchen, ein XFA-basiertes Formular mit der Signature-Dienst-API zu signieren, fehlen die Daten möglicherweise im `View` Ordner `Signed` in Acrobat `Version` . Betrachten Sie zum Beispiel den folgenden Arbeitsablauf:

* Mit einer XDP-Datei, die mit Designer erstellt wurde, führen Sie einen Formularentwurf zusammen, der ein Unterschriftsfeld und XML-Daten enthält, die Formulardaten enthalten. Mit dem Forms-Dienst können Sie ein interaktives PDF-Dokument erstellen.
* Sie signieren das PDF-Dokument mit der Signature-Dienst-API.

### Zusammenfassung der Schritte {#summary_of_steps-3}

So signieren Sie ein PDF-Dokument digital:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signature-Dienst-Client.
1. Signieren Sie das PDF-Dokument.
1. Signieren Sie das PDF-Dokument.
1. Speichern Sie das signierte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

**Signaturclient erstellen**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument signieren lassen**

Um ein PDF-Dokument zu signieren, müssen Sie ein PDF-Dokument abrufen, das ein Signaturfeld enthält. Wenn ein PDF-Dokument kein Unterschriftsfeld enthält, kann es nicht unterschrieben werden. Ein Unterschriftsfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden.

**PDF-Dokument signieren**

Beim Signieren eines PDF-Dokuments können Sie Laufzeitoptionen festlegen, die vom Signature-Dienst verwendet werden. Sie können die folgenden Optionen festlegen:

* Aussehen-Optionen
* Sperrüberprüfung
* Zeitstempelwerte

Sie legen die Aussehen-Optionen mithilfe eines `PDFSignatureAppearanceOptionSpec` Objekts fest. Beispielsweise können Sie das Datum in einer Unterschrift anzeigen, indem Sie die `PDFSignatureAppearanceOptionSpec` Methode des `setShowDate` Objekts aufrufen und weitergeben `true`.

Sie können auch angeben, ob eine Sperrüberprüfung durchgeführt werden soll, die bestimmt, ob das Zertifikat, das zum digitalen Signieren eines PDF-Dokuments verwendet wird, gesperrt wurde. Zur Durchführung der Sperrungsüberprüfung können Sie einen der folgenden Werte angeben:

* **NoCheck**: Führen Sie keine Sperrüberprüfung durch.
* **BestEffort**: Versuchen Sie immer, den Widerruf aller Zertifikate in der Kette zu prüfen. Tritt bei der Überprüfung ein Problem auf, wird davon ausgegangen, dass der Widerruf gültig ist. Wenn ein Fehler auftritt, gehen Sie davon aus, dass das Zertifikat nicht widerrufen wird.
* **CheckIfAvailable:** Überprüfen Sie, ob alle Zertifikate in der Kette auf Sperrung hin gesperrt wurden, wenn Sperrinformationen verfügbar sind. Tritt bei der Überprüfung ein Problem auf, wird der Widerruf als ungültig angenommen. Wenn ein Fehler auftritt, gehen Sie davon aus, dass das Zertifikat gesperrt und ungültig ist. (Dies ist der Standardwert.)
* **ImmerCheck**: Prüfen Sie, ob alle Zertifikate in der Kette widerrufen werden. Wenn keine Sperrinformationen in einem Zertifikat vorhanden sind, wird der Widerruf als ungültig angenommen.

Um die Sperrüberprüfung für ein Zertifikat durchzuführen, können Sie eine URL zu einem Zertifikatsperrlisten-Liste (CRL) angeben, indem Sie ein `CRLOptionSpec` Objekt verwenden. Wenn Sie jedoch eine Sperrüberprüfung durchführen möchten und keine URL für einen Zertifikatsperrlisten-Server angeben, ruft der Signature-Dienst die URL aus dem Zertifikat ab.

Statt einen CRL-Server zu verwenden, können Sie einen OCSP-Server (Online Certificate Status Protocol) verwenden, wenn Sie die Sperrüberprüfung durchführen. Bei Verwendung eines OCSP-Servers im Gegensatz zu einem CRL-Server wird die Sperrüberprüfung in der Regel schneller durchgeführt. (Siehe &quot;Online-Zertifikatstatusprotokoll&quot;unter [https://tools.ietf.org/html/rfc2560](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signature-Dienst mit Adobe-Anwendungen und -Diensten verwendet. Beispiel: Wenn der OCSP-Server zuerst in Adobe Applications and Services eingestellt wird, wird der OCSP-Server und anschließend der CRL-Server überprüft. (Siehe &quot;Verwalten von Zertifikaten und Berechtigungen mithilfe des Trust Store&quot;in der AAC-Hilfe).

Wenn Sie angeben, dass keine Sperrüberprüfung durchgeführt werden soll, prüft der Signature-Dienst nicht, ob das zum Signieren oder Zertifizieren eines Dokuments verwendete Zertifikat widerrufen wurde. Das heißt, die Serverinformationen für CRL und OCSP werden ignoriert.

>[!NOTE]
>
>Obwohl eine Zertifikatsperrliste oder ein OCSP-Server im Zertifikat angegeben werden kann, können Sie die im Zertifikat angegebene URL mit einem `CRLOptionSpec` und einem `OCSPOptionSpec` Objekt überschreiben. Um beispielsweise den CRL-Server zu überschreiben, können Sie die `CRLOptionSpec` Methode des `setLocalURI` Objekts aufrufen.

Der Zeitstempel bezieht sich auf den Prozess der Verfolgung des Zeitpunkts, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Sobald ein Dokument signiert wurde, sollte es nicht geändert werden, auch nicht vom Eigentümer des Dokuments. Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mit einem `TSPOptionSpec` Objekt festlegen. Sie können beispielsweise die URL eines TSP-Servers (Time Stamping Provider) angeben.

>[!NOTE]
>
>Im Java- und Webdienst werden die einzelnen Abschnitte und die entsprechenden schnellen Beginn einer Sperrüberprüfung unterzogen. Da keine Zertifikatsperrliste oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem zum digitalen Signieren des PDF-Dokuments verwendeten Zertifikat abgerufen.

Um ein PDF-Dokument erfolgreich zu signieren, können Sie den vollständig qualifizierten Namen des Signaturfelds angeben, das die digitale Signatur enthalten soll, z. B. `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds kann auch der teilweise Name des Signaturfelds verwendet werden: `SignatureField3[3]`.

Sie müssen auch auf eine Sicherheitsberechtigung verweisen, um ein PDF-Dokument digital signieren zu können. Um auf eine Sicherheitsberechtigung zu verweisen, geben Sie einen Alias an. Der Alias ist ein Verweis auf eine tatsächliche Berechtigung, die sich in einer PKCS#12-Datei (mit der Erweiterung .pfx) oder in einem Hardware-Sicherheitsmodul (HSM) befinden kann. Informationen zur Sicherheitsberechtigung finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

**Signiertes PDF-Dokument speichern**

Nachdem der Signature-Dienst das PDF-Dokument digital signiert hat, können Sie es als PDF-Datei speichern, damit die Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[PDF-Dokumente mit der Java-API digital signieren](digitally-signing-certifying-documents.md#digitally-sign-pdf-documents-using-the-java-api)

[Digitales Signieren von PDF-Dokumenten mit der Webdienst-API](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

[Signaturfeldnamen abrufen](digitally-signing-certifying-documents.md#retrieving-signature-field-names)

### PDF-Dokumente mit der Java-API digital signieren {#digitally-sign-pdf-documents-using-the-java-api}

PDF-Dokumente mit der Signature-API (Java) digital signieren:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-signatures-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Signaturclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument signieren lassen

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument darstellt, das mit dem Konstruktor digital signiert werden soll, und übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PDF-Dokument signieren

   Signieren Sie das PDF-Dokument, indem Sie die `SignatureServiceClient` `sign` Objektmethode aufrufen und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` object that represents the PDF document to sign.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds darstellt, das die digitale Signatur enthalten wird.
   * A `Credential` object that represents the credential that is used to digitally sign the PDF document. Erstellen Sie ein `Credential` Objekt, indem Sie die statische `Credential` Methode des `getInstance` Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Aliaswert angibt, der der Sicherheitsberechtigung entspricht.
   * Ein `HashAlgorithm` Objekt, das einen statischen Datenmember angibt, der den Hash-Algorithmus darstellt, der zum Verarbeiten des PDF-Dokuments verwendet wird. Sie können beispielsweise angeben, `HashAlgorithm.SHA1` dass der SHA1-Algorithmus verwendet werden soll.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Unterzeichnung des PDF-Dokuments darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen des Unterzeichners darstellt.
   * Ein `PDFSignatureAppearanceOptions` Objekt, das das Erscheinungsbild der digitalen Unterschrift steuert. Beispielsweise können Sie mit diesem Objekt ein benutzerdefiniertes Logo zu einer digitalen Unterschrift hinzufügen.
   * Ein `java.lang.Boolean` Objekt, das angibt, ob eine Sperrüberprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll.
   * Ein `OCSPOptionSpec` Objekt, das Voreinstellungen für die Unterstützung des Online-Zertifikatstatusprotokolls (OCSP) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `CRLPreferences` Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `TSPPreferences` Objekt, das Voreinstellungen für die Unterstützung von Zeitstempelanbietern (TSP) speichert. Dieser Parameter ist optional und kann `null`verwendet werden. For more information, see [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Die `sign` Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Invoke the `com.adobe.idp.Document` object’s `copyToFile` method and pass `java.io.File`to copy the contents of the `Document` object to the file. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document`-Objekt verwenden, das von der `sign`-Methode zurückgegeben wurde.

**Siehe auch**

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Quick Beginn (SOAP-Modus): Digitales Signieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitales Signieren von PDF-Dokumenten mit der Webdienst-API {#digitally-signing-pdf-documents-using-the-web-service-api}

So signieren Sie ein PDF-Dokument mit der Signature-API (Webdienst) digital:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument signieren lassen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern eines signierten PDF-Dokuments.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu signierenden PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie dessen `MTOM` Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. PDF-Dokument signieren

   Signieren Sie das PDF-Dokument, indem Sie die `SignatureServiceClient` `sign` Objektmethode aufrufen und die folgenden Werte übergeben:

   * A `BLOB` object that represents the PDF document to sign.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds darstellt, das die digitale Signatur enthalten wird.
   * A `Credential` object that represents the credential that is used to digitally sign the PDF document. Erstellen Sie ein `Credential` Objekt mithilfe des Konstruktors und geben Sie den Alias an, indem Sie der `Credential` Objekteigenschaft einen Wert zuweisen `alias` .
   * Ein `HashAlgorithm` Objekt, das einen statischen Datenmember angibt, der den Hash-Algorithmus darstellt, der zum Verarbeiten des PDF-Dokuments verwendet wird. Sie können beispielsweise angeben, `HashAlgorithm.SHA1` dass der SHA1-Algorithmus verwendet werden soll.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Unterzeichnung des PDF-Dokuments darstellt.
   * Ein Zeichenfolgenwert, der die Position des Unterzeichners darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen des Unterzeichners darstellt.
   * Ein `PDFSignatureAppearanceOptions` Objekt, das das Erscheinungsbild der digitalen Unterschrift steuert. Beispielsweise können Sie mit diesem Objekt ein benutzerdefiniertes Logo zu einer digitalen Unterschrift hinzufügen.
   * Ein `System.Boolean` Objekt, das angibt, ob eine Sperrüberprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll. Wenn diese Sperrüberprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `OCSPOptionSpec` Objekt, das Voreinstellungen für die Unterstützung des Online-Zertifikatstatusprotokolls (OCSP) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben. Weitere Informationen zu diesem Objekt finden Sie unter API-Referenz zu [AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences` Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `TSPPreferences` Objekt, das Voreinstellungen für die Unterstützung von Zeitstempelanbietern (TSP) speichert. Dieser Parameter ist optional und kann `null`verwendet werden.

   Die `sign` Methode gibt ein `BLOB` Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das von der `sign` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Interaktive Formulare digital signieren {#digitally-signing-interactive-forms}

Sie können ein interaktives Formular signieren, das vom Forms-Dienst erstellt wird. Betrachten Sie zum Beispiel den folgenden Arbeitsablauf:

* Sie führen ein XFA-basiertes PDF-Formular zusammen, das mit Designer erstellt wurde, und Formulardaten, die sich in einem XML-Dokument befinden, mit dem Forms-Dienst. Der Forms-Server rendert ein interaktives Formular.
* Sie signieren das interaktive Formular mit der Signature-Dienst-API.

Das Ergebnis ist ein interaktives, digital signiertes PDF-Formular. Beim Signieren eines PDF-Formulars, das auf einem XFA-Formular basiert, stellen Sie sicher, dass Sie die PDF-Datei als statisches PDF-Formular von Adobe speichern. Wenn Sie versuchen, ein PDF-Formular zu signieren, das als dynamisches Adobe PDF-Formular gespeichert wurde, tritt eine Ausnahme auf. Da Sie das Formular signieren, das vom Forms-Dienst zurückgegeben wird, stellen Sie sicher, dass das Formular ein Unterschriftsfeld enthält.

>[!NOTE]
>
>Bevor Sie ein interaktives Formular digital signieren können, müssen Sie sicherstellen, dass das Zertifikat den AEM Forms hinzugefügt wird. Ein Zertifikat wird mithilfe von Administration Console oder programmgesteuert mithilfe der Trust Manager-API hinzugefügt. (Siehe [Berechtigungen mithilfe der Trust Manager-API](/help/forms/developing/credentials.md#importing-credentials-by-using-the-trust-manager-api)importieren.)

Wenn Sie die Forms Service API verwenden, setzen Sie die `GenerateServerAppearance` Laufzeitoption auf `true`. Mit dieser Laufzeitoption wird sichergestellt, dass das Erscheinungsbild des Formulars, das auf dem Server generiert wird, gültig bleibt, wenn es in Acrobat oder Adobe Reader geöffnet wird. Es wird empfohlen, diese Laufzeitoption beim Generieren eines interaktiven Formulars zur Unterzeichnung mit der Forms-API festzulegen.

>[!NOTE]
>
>Bevor Sie interaktive Formulare digital signieren, sollten Sie mit dem Signieren von PDF-Dokumenten vertraut sein. (See [Digitally Signing PDF Documents](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

### Zusammenfassung der Schritte {#summary_of_steps-4}

So signieren Sie ein interaktives Formular, das der Forms-Dienst zurückgibt:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Forms- und Signaturclient.
1. Rufen Sie das interaktive Formular mit dem Forms-Dienst ab.
1. Unterschreiben Sie das interaktive Formular.
1. Speichern Sie das signierte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-forms-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Forms- und Signaturclients**

Da dieser Arbeitsablauf sowohl die Forms- als auch die Signature-Dienste aufruft, erstellen Sie sowohl einen Forms-Dienstclient als auch einen Signature-Dienstclient.

**Interaktives Formular mit dem Forms-Dienst abrufen**

Mit dem Forms-Dienst können Sie das interaktive PDF-Formular zum Signieren abrufen. Ab sofort können Sie ein `com.adobe.idp.Document` Objekt an den Forms-Dienst übergeben, der das wiederzugebende Formular enthält. Der Name dieser Methode lautet `renderPDFForm2`. Diese Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das das zu signierende Formular enthält. Sie können diese `com.adobe.idp.Document` Instanz an den Signature-Dienst weiterleiten.

Bei Verwendung von Webdiensten können Sie auch die `BLOB` Instanz weiterleiten, die der Forms-Dienst an den Signature-Dienst zurückgibt.

>[!NOTE]
>
>Der schnelle Beginn, der mit dem Abschnitt &quot;Interaktive Formulare mit digitalem Signieren&quot;verknüpft ist, ruft die `renderPDFForm2` Methode auf.

**Interaktives Formular unterschreiben**

Beim Signieren eines PDF-Dokuments können Sie Laufzeitoptionen festlegen, die vom Signature-Dienst verwendet werden. Sie können die folgenden Optionen festlegen:

* Aussehen-Optionen
* Sperrüberprüfung
* Zeitstempelwerte

Sie legen die Aussehen-Optionen mithilfe eines `PDFSignatureAppearanceOptionSpec` Objekts fest. Beispielsweise können Sie das Datum in einer Unterschrift anzeigen, indem Sie die `PDFSignatureAppearanceOptionSpec` Methode des `setShowDate` Objekts aufrufen und weitergeben `true`.

**Signiertes PDF-Dokument speichern**

Nachdem der Signature-Dienst das PDF-Dokument digital signiert hat, können Sie es als PDF-Datei speichern. Die PDF-Datei kann in Acrobat oder Adobe Reader geöffnet werden.

**Siehe auch**

[Interaktives Formular mit der Java-API digital signieren](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-java-api)

[Interaktives Formular mit der Webdienst-API digital signieren](digitally-signing-certifying-documents.md#digitally-sign-an-interactive-form-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-Dokumente digital signieren](digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)

[Interaktive PDF forms wiedergeben](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms)

### Interaktives Formular mit der Java-API digital signieren {#digitally-sign-an-interactive-form-using-the-java-api}

Interaktive Formulare mit der Formular- und Signatur-API (Java) digital signieren:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-signatures-client.jar&quot;und &quot;adobe-forms-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms- und Signaturclients

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Interaktives Formular mit dem Forms-Dienst abrufen

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument darstellt, das mithilfe des Konstruktors an den Forms-Dienst übergeben wird. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das XML-Dokument darstellt, das Formulardaten enthält, die mithilfe des Konstruktors an den Forms-Dienst übergeben werden sollen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort der XML-Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `PDFFormRenderSpec` Objekt, mit dem Laufzeitoptionen festgelegt werden. Rufen Sie die `PDFFormRenderSpec` Methode des `setGenerateServerAppearance` Objekts auf und übergeben Sie sie `true`.
   * Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm2` auf und übergeben Sie die folgenden Werte:

      * Ein `com.adobe.idp.Document` Objekt, das das zu rendernde PDF-Formular enthält.
      * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen.
      * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert.
      * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden. Sie können `null` für diesen Parameterwert angeben.
      * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.

      Die `renderPDFForm2` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält

   * Rufen Sie das PDF-Formular ab, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen. Diese Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das das interaktive Formular darstellt.


1. Interaktives Formular unterschreiben

   Signieren Sie das PDF-Dokument, indem Sie die `SignatureServiceClient` `sign` Objektmethode aufrufen und die folgenden Werte übergeben:

   * A `com.adobe.idp.Document` object that represents the PDF document to sign. Stellen Sie sicher, dass dieses Objekt das vom Forms-Dienst abgerufene `com.adobe.idp.Document` Objekt ist.
   * Ein Zeichenfolgenwert, der den Namen des unterschriebenen Unterschriftsfelds darstellt.
   * A `Credential` object that represents the credential that is used to digitally sign the PDF document. Erstellen Sie ein `Credential` Objekt, indem Sie die statische `Credential` Objektmethode aufrufen `getInstance` . Übergeben Sie einen Zeichenfolgenwert, der den Aliaswert angibt, der der Sicherheitsberechtigung entspricht.
   * Ein `HashAlgorithm` Objekt, das einen statischen Datenmember angibt, der den Hash-Algorithmus darstellt, der zum Verarbeiten des PDF-Dokuments verwendet wird. Sie können beispielsweise angeben, `HashAlgorithm.SHA1` dass der SHA1-Algorithmus verwendet werden soll.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Unterzeichnung des PDF-Dokuments darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen des Unterzeichners darstellt.
   * Ein `PDFSignatureAppearanceOptions` Objekt, das das Erscheinungsbild der digitalen Unterschrift steuert. Beispielsweise können Sie mit diesem Objekt ein benutzerdefiniertes Logo zu einer digitalen Unterschrift hinzufügen.
   * Ein `java.lang.Boolean` Objekt, das angibt, ob eine Sperrüberprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll.
   * Ein `OCSPPreferences` Objekt, das Voreinstellungen für die Unterstützung des Online-Zertifikatstatusprotokolls (OCSP) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `CRLPreferences` Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `TSPPreferences` Objekt, das Voreinstellungen für die Unterstützung von Zeitstempelanbietern (TSP) speichert. Dieser Parameter ist optional und kann `null`verwendet werden.

   Die `sign` Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Create a `java.io.File` object and ensure that the filename extension is .pdf.
   * Invoke the `com.adobe.idp.Document` object’s `copyToFile` method and pass `java.io.File`to copy the contents of the `Document` object to the file. Stellen Sie sicher, dass Sie das `com.adobe.idp.Document` Objekt verwenden, das von der `sign` Methode zurückgegeben wurde.

**Siehe auch**

[Interaktive Formulare digital signieren](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Quick Beginn (SOAP-Modus): Digitales Signieren eines PDF-Dokuments mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Interaktives Formular mit der Webdienst-API digital signieren {#digitally-sign-an-interactive-form-using-the-web-service-api}

Interaktive Formulare mit der Formular- und Signatur-API (Webdienst) digital signieren:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Da diese Clientanwendung zwei Dienste aufruft, erstellen Sie zwei Dienstverweise. Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Signature-Dienst verknüpft ist: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   Verwenden Sie die folgende WSDL-Definition für den Dienstverweis, der mit dem Forms-Dienst verknüpft ist: `http://localhost:8080/soap/services/FormsService?WSDL&lc_version=9.0.1`.

   Da der `BLOB` Datentyp für beide Dienstverweise gleich ist, müssen Sie den Datentyp bei der Verwendung vollständig qualifizieren `BLOB` . Im entsprechenden Web Service Quick Beginn sind alle `BLOB` Instanzen vollständig qualifiziert.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Erstellen eines Forms- und Signaturclients

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Wiederholen Sie diese Schritte für den Forms-Dienstclient.

1. Interaktives Formular mit dem Forms-Dienst abrufen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern eines signierten PDF-Dokuments.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu signierenden PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie dessen `MTOM` Eigenschaft den Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern von Formulardaten.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort der XML-Datei, die Formulardaten enthält, sowie den Modus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie dessen `MTOM` Eigenschaft den Inhalt des Byte-Arrays zuweisen.
   * Erstellen Sie ein `PDFFormRenderSpec` Objekt, mit dem Laufzeitoptionen festgelegt werden. Weisen Sie den Wert `true` dem `PDFFormRenderSpec` Objektfeld `generateServerAppearance` zu.
   * Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm2` auf und übergeben Sie die folgenden Werte:

      * Ein `BLOB` Objekt, das das zu rendernde PDF-Formular enthält.
      * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen.
      * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert.
      * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden. Sie können `null` für diesen Parameterwert angeben.
      * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
      * Ein langer Ausgabeparameter, mit dem die Anzahl der Seiten im Formular gespeichert wird.
      * Ein Zeichenfolgenausgabeparameter, der für den Gebietsschemawert verwendet wird.
      * Ein `FormResult` Wert, der ein Ausgabeparameter ist, mit dem das interaktive Formular gespeichert wird.
   * Rufen Sie das PDF-Formular zurück, indem Sie das `FormsResult` Objektfeld aufrufen `outputContent` . Dieses Feld speichert ein `BLOB` Objekt, das das interaktive Formular darstellt.


1. Interaktives Formular unterschreiben

   Signieren Sie das PDF-Dokument, indem Sie die `SignatureServiceClient` `sign` Objektmethode aufrufen und die folgenden Werte übergeben:

   * A `BLOB` object that represents the PDF document to sign. Verwenden Sie die vom Forms-Dienst zurückgegebene `BLOB` Instanz.
   * Ein Zeichenfolgenwert, der den Namen des unterschriebenen Unterschriftsfelds darstellt.
   * A `Credential` object that represents the credential that is used to digitally sign the PDF document. Erstellen Sie ein `Credential` Objekt mithilfe des Konstruktors und geben Sie den Alias an, indem Sie der `Credential` Objekteigenschaft einen Wert zuweisen `alias` .
   * Ein `HashAlgorithm` Objekt, das einen statischen Datenmember angibt, der den Hash-Algorithmus darstellt, der zum Verarbeiten des PDF-Dokuments verwendet wird. Sie können beispielsweise angeben, `HashAlgorithm.SHA1` dass der SHA1-Algorithmus verwendet werden soll.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein Zeichenfolgenwert, der den Grund für die digitale Unterzeichnung des PDF-Dokuments darstellt.
   * Ein Zeichenfolgenwert, der die Position des Unterzeichners darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen des Unterzeichners darstellt.
   * Ein `PDFSignatureAppearanceOptions` Objekt, das das Erscheinungsbild der digitalen Unterschrift steuert. Beispielsweise können Sie mit diesem Objekt ein benutzerdefiniertes Logo zu einer digitalen Unterschrift hinzufügen.
   * Ein `System.Boolean` Objekt, das angibt, ob eine Sperrüberprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll. Wenn diese Sperrüberprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `OCSPPreferences` Objekt, das Voreinstellungen für die Unterstützung des Online-Zertifikatstatusprotokolls (OCSP) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben. Weitere Informationen zu diesem Objekt finden Sie unter API-Referenz zu [AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences` Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `TSPPreferences` Objekt, das Voreinstellungen für die Unterstützung von Zeitstempelanbietern (TSP) speichert. Dieser Parameter ist optional und kann `null`verwendet werden.

   Die `sign` Methode gibt ein `BLOB` Objekt zurück, das das signierte PDF-Dokument darstellt.

1. Signiertes PDF-Dokument speichern

   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das von der `sign` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[Interaktive Formulare digital signieren](digitally-signing-certifying-documents.md#digitally-signing-interactive-forms)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## PDF-Dokumente zertifizieren {#certifying-pdf-documents}

Sie können ein PDF-Dokument absichern, indem Sie es mit einem bestimmten Signaturtyp (einer zertifizierten Signatur) zertifizieren. Eine zertifizierte Signatur entscheidet sich wie folgt von einer digitalen Signatur:

* Sie muss die erste, auf das PDF-Dokument angewendete Signatur sein. Das heißt, zum Zeitpunkt, zu dem die zertifizierte Signatur angewendet wird, müssen alle anderen Signaturfelder im Dokument unsigniert sein. In einem PDF-Dokument ist nur eine zertifizierte Signatur zulässig. Wenn Sie ein PDF-Dokument signieren und zertifizieren möchten, müssen Sie es vor dem signieren zertifizieren. Nach dem Zertifizieren eines PDF-Dokuments können Sie weitere Signaturfelder digital signieren.
* Der Autor oder Ersteller des Dokuments kann festlegen, dass das Dokument auf bestimmte Arten modifiziert werden kann, ohne dass die zertifizierte Signatur ungültig wird. Beispiel: Das Ausfüllen von Formularen oder Einfügen von Kommentaren im Dokument kann zulässig sein. Wenn der Autor festlegt, dass eine bestimmte Änderung nicht zulässig ist, Acrobat verhindert, dass Benutzer das Dokument auf diese Weise ändern. Wenn solche Änderungen vorgenommen werden, etwa durch Verwenden einer anderen Anwendung, wird die zertifizierte Signatur ungültig und Acrobat gibt eine Warnung aus, wenn ein Benutzer das Dokument öffnet. (Bei nicht zertifizierten Signaturen werden Änderungen nicht verhindert und Bearbeitungsvorgänge führen nicht dazu, dass die ursprüngliche Signatur ungültig wird.)
* Zum Zeitpunkt des Signierens wird das Dokument auf bestimmte Typen von Inhalt überprüft, durch die die Inhalte eines Dokuments mehrdeutig oder irreführend werden könnten. Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Eine Erläuterung (gültige Beglaubigung) zu solchen Inhalten kann bereitgestellt werden.

Sie können PDF-Dokumente programmgesteuert mit der Signature-Dienst-Java-API oder der Signature-Webdienst-API zertifizieren. Beim Zertifizieren eines PDF-Dokuments müssen Sie auf eine Sicherheitsberechtigung verweisen, die im Berechtigungsdienst vorhanden ist. Informationen zur Sicherheitsberechtigung finden Sie im Handbuch *Installieren und Bereitstellen von AEM Forms* für Ihren Anwendungsserver.

>[!NOTE]
>
>Wenn beim Zertifizieren und Signieren desselben PDF-Dokuments die Zertifizierungsunterschrift nicht als vertrauenswürdig eingestuft wird, wird beim Öffnen des PDF-Dokuments in Acrobat oder Adobe Reader neben der ersten Unterschrift ein gelbes Dreieck angezeigt. Die Zertifizierungsunterschrift muss als vertrauenswürdig eingestuft werden, um diese Situation zu vermeiden.

>[!NOTE]
>
>Bei Verwendung einer OpenShield-HSM-Berechtigung zum Signieren oder Zertifizieren eines PDF-Dokuments kann die neue Berechtigung erst verwendet werden, nachdem der J2EE-Anwendungsserver, auf dem die AEM Forms bereitgestellt sind, neu gestartet wurde. Sie können jedoch einen Konfigurationswert festlegen, der dazu führt, dass der Vorgang zum Signieren oder Zertifizieren funktioniert, ohne den J2EE-Anwendungsserver neu zu starten.

Sie können den folgenden Konfigurationswert in der Datei &quot;cknfastrc&quot;hinzufügen, die sich unter &quot;/opt/nfast/cknfastrc&quot;(oder &quot;c:\nfast\cknfastrc&quot;) befindet:

```as3
             CKNFAST_ASSUME_SINGLE_PROCESS=0
```

Nachdem Sie diesen Konfigurationswert zur cknfastrc-Datei hinzugefügt haben, können Sie die neue Berechtigung verwenden, ohne den J2EE-Anwendungsserver neu zu starten.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Zertifizieren eines Dokuments finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

So zertifizieren Sie ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signaturclient.
1. PDF-Dokument zertifizieren lassen.
1. PDF-Dokument zertifizieren.
1. Speichern Sie das zertifizierte PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Signaturclient erstellen**

Bevor Sie einen Signaturvorgang programmgesteuert durchführen können, müssen Sie einen Signaturclient erstellen.

**PDF-Dokument zertifizieren lassen**

Um ein PDF-Dokument zu zertifizieren, müssen Sie ein PDF-Dokument abrufen, das ein Unterschriftsfeld enthält. Wenn ein PDF-Dokument kein Unterschriftsfeld enthält, kann es nicht zertifiziert werden. Ein Unterschriftsfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden. Informationen zum programmgesteuerten Hinzufügen eines Unterschriftsfelds finden Sie unter [Hinzufügen von Unterschriftsfeldern](digitally-signing-certifying-documents.md#adding-signature-fields).

**PDF-Dokument zertifizieren**

Zum erfolgreichen Zertifizieren eines PDF-Dokuments benötigen Sie die folgenden Eingabewerte, die vom Signature-Dienst zum Zertifizieren eines PDF-Dokuments verwendet werden:

* **PDF-Dokument**: Ein PDF-Dokument, das ein Unterschriftsfeld enthält. Dabei handelt es sich um ein Formularfeld, das eine grafische Darstellung der zertifizierten Unterschrift enthält. Ein PDF-Dokument muss ein Unterschriftsfeld enthalten, bevor es zertifiziert werden kann. Ein Unterschriftsfeld kann mithilfe von Designer oder programmgesteuert hinzugefügt werden. (Siehe [Hinzufügen von Unterschriftsfeldern](digitally-signing-certifying-documents.md#adding-signature-fields).)
* **Name** des Unterschriftsfelds: Der vollständig qualifizierte Name des zertifizierten Signaturfelds. Der folgende Wert ist ein Beispiel: `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds kann auch der teilweise Name des Signaturfelds verwendet werden: `SignatureField3[3]`. Wenn für den Feldnamen ein Null-Wert übergeben wird, wird ein unsichtbares Unterschriftsfeld dynamisch erstellt und zertifiziert.
* **Sicherheitsberechtigung**: Eine Berechtigung zum Zertifizieren des PDF-Dokuments. Diese Sicherheitsberechtigung enthält ein Kennwort und einen Alias, der mit einem Alias übereinstimmen muss, der in der Berechtigung im Berechtigungsdienst angezeigt wird. Der Alias ist ein Verweis auf eine tatsächliche Berechtigung, die sich in einer PKCS#12-Datei (mit der Erweiterung .pfx) oder in einem Hardware-Sicherheitsmodul (HSM) befinden kann.
* **Hash-Algorithmus**: Ein Hash-Algorithmus, mit dem das PDF-Dokument verarbeitet werden kann.
* **Grund für die Unterzeichnung**: Ein Wert, der in Acrobat oder Adobe Reader angezeigt wird, damit andere Benutzer den Grund für die Zertifizierung des PDF-Dokuments kennen.
* **Speicherort des Unterzeichners**: Der Speicherort des Unterzeichners, der durch die Berechtigung angegeben wird.
* **Kontaktangaben**: Kontaktinformationen des Unterzeichners, z. B. Adresse und Telefonnummer.
* **Berechtigungsinformationen**: Berechtigungen, die die Aktionen steuern, die ein Endbenutzer an einem Dokument ausführen kann, ohne dass die zertifizierte Signatur ungültig wird. Sie können die Berechtigung beispielsweise so festlegen, dass jede Änderung am PDF-Dokument dazu führt, dass die zertifizierte Signatur ungültig wird.
* **Rechtliche Erklärung**: Wenn ein Dokument zertifiziert ist, wird es automatisch auf bestimmte Inhaltstypen überprüft, die den Inhalt eines Dokuments mehrdeutig oder irreführend machen könnten. Beispiel: Eine Anmerkung kann Text auf einer Seite verdecken, der für das Verständnis dessen, was zertifiziert wird, wichtig ist. Der Scanvorgang erzeugt Warnungen zu diesen Inhaltstypen. Dieser Wert bietet eine zusätzliche Erläuterung des Inhalts, der möglicherweise Warnungen generiert hat.
* **Aussehen-Optionen**: Optionen, die das Erscheinungsbild der zertifizierten Signatur steuern. Beispielsweise kann die zertifizierte Signatur Datumsangaben anzeigen.
* **Sperrüberprüfung**: Dieser Wert gibt an, ob die Sperrüberprüfung für das Zertifikat des Unterzeichners durchgeführt wird. Die Standardeinstellung von `false` bedeutet, dass die Sperrüberprüfung nicht durchgeführt wird.
* **OCSP-Einstellungen**: Unterstützung für das Online-Zertifikatstatusprotokoll (OCSP), das Informationen zum Status der Berechtigung bereitstellt, mit der das PDF-Dokument zertifiziert wird. Sie können beispielsweise die URL des Servers angeben, der Informationen über die Berechtigung bereitstellt, mit der Sie sich beim PDF-Dokument anmelden.
* **CRL-Einstellungen**: Einstellungen für Zertifikatsperrlisten-Listen (CRL), wenn die Sperrüberprüfung abgeschlossen ist. Sie können beispielsweise angeben, dass immer geprüft werden soll, ob eine Berechtigung gesperrt wurde.
* **Zeitstempel**: Einstellungen, die Zeitstempelinformationen definieren, die auf die zertifizierte Signatur angewendet werden. Ein Zeitstempel gibt an, dass bestimmte Daten vor einer bestimmten Zeit ermittelt wurden. Dieses Wissen hilft, eine vertrauensvolle Beziehung zwischen dem Unterzeichner und dem Prüfer aufzubauen.

**Zertifiziertes PDF-Dokument als PDF-Datei speichern**

Nachdem der Signature-Dienst das PDF-Dokument zertifiziert hat, können Sie es als PDF-Datei speichern, damit die Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[PDF-Dokumente mit der Java-API zertifizieren](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-java-api)

[PDF-Dokumente mithilfe der Webdienst-API zertifizieren](digitally-signing-certifying-documents.md#certify-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

### PDF-Dokumente mit der Java-API zertifizieren {#certify-pdf-documents-using-the-java-api}

PDF-Dokumente mithilfe der Signature-API (Java) zertifizieren:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-signatures-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Signaturclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument zertifizieren lassen

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das zu zertifizierende PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PDF-Dokument zertifizieren

   Zertifizieren Sie das PDF-Dokument, indem Sie die `SignatureServiceClient` `certify` Objektmethode aufrufen und die folgenden Werte übergeben:

   * Das `com.adobe.idp.Document` Objekt, das das zu zertifizierende PDF-Dokument darstellt.
   * Ein Zeichenfolgenwert, der den Namen des Unterschriftsfelds darstellt, das die Unterschrift enthalten soll.
   * A `Credential` object that represents the credential that is used to certify the PDF document. Erstellen Sie ein `Credential` Objekt, indem Sie die statische `Credential` Methode des `getInstance` Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Aliaswert angibt, der der Sicherheitsberechtigung entspricht.
   * Ein `HashAlgorithm` Objekt, das einen statischen Datenmember angibt, der den Hash-Algorithmus darstellt, mit dem das PDF-Dokument verarbeitet wird. Sie können beispielsweise angeben, `HashAlgorithm.SHA1` dass der SHA1-Algorithmus verwendet werden soll.
   * Ein Zeichenfolgenwert, der den Grund für die Zertifizierung des PDF-Dokuments darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen des Unterzeichners darstellt.
   * Ein `MDPPermissions` Objekt, das Aktionen angibt, die für das PDF-Dokument ausgeführt werden können und die die Unterschrift ungültig machen.
   * Ein `PDFSignatureAppearanceOptions` Objekt, das das Erscheinungsbild der zertifizierten Signatur steuert. Ändern Sie bei Bedarf das Erscheinungsbild der Unterschrift, indem Sie eine Methode aufrufen, z. B. `setShowDate`.
   * Ein Zeichenfolgenwert, der erklärt, welche Aktionen die Unterschrift ungültig machen.
   * Ein `java.lang.Boolean` Objekt, das angibt, ob eine Sperrüberprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll. Wenn diese Sperrüberprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `java.lang.Boolean` Objekt, das angibt, ob das zertifizierte Unterschriftsfeld gesperrt ist. Wenn das Feld gesperrt ist, wird das Unterschriftsfeld als schreibgeschützt markiert, seine Eigenschaften können nicht geändert werden und es kann nicht von Personen gelöscht werden, die nicht über die erforderlichen Berechtigungen verfügen. Der Standardwert lautet `false`.
   * Ein `OCSPPreferences` Objekt, das Voreinstellungen für die Unterstützung des Online-Zertifikatstatusprotokolls (OCSP) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben. Weitere Informationen zu diesem Objekt finden Sie unter API-Referenz zu [AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `CRLPreferences` Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `TSPPreferences` Objekt, das Voreinstellungen für die Unterstützung von Zeitstempelanbietern (TSP) speichert. Nachdem Sie beispielsweise ein `TSPPreferences` Objekt erstellt haben, können Sie die URL des TSP-Servers festlegen, indem Sie die `TSPPreferences` Objektmethode `setTspServerURL` aufrufen. Dieser Parameter ist optional und kann `null`verwendet werden. For more information, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

   Die `certify` Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das das zertifizierte PDF-Dokument darstellt.

1. Zertifiziertes PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Invoke the `com.adobe.idp.Document` object’s `copyToFile` method to copy the contents of the `com.adobe.idp.Document` object to the file.

**Siehe auch**

[PDF-Dokumente zertifizieren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Quick Beginn (SOAP-Modus): PDF-Dokumente mit der Java-API zertifizieren](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-certifying-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-Dokumente mithilfe der Webdienst-API zertifizieren {#certify-pdf-documents-using-the-web-service-api}

PDF-Dokumente mithilfe der Signature-API (Webdienst) zertifizieren:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument zertifizieren lassen

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern eines zertifizierten PDF-Dokuments.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu zertifizierenden PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Datenmember den Inhalt des Byte-Arrays zuweisen.

1. PDF-Dokument zertifizieren

   Zertifizieren Sie das PDF-Dokument, indem Sie die `SignatureServiceClient` `certify` Objektmethode aufrufen und die folgenden Werte übergeben:

   * Das `BLOB` Objekt, das das zu zertifizierende PDF-Dokument darstellt.
   * Ein Zeichenfolgenwert, der den Namen des Unterschriftsfelds darstellt, das die Unterschrift enthalten soll.
   * A `Credential` object that represents the credential that is used to certify the PDF document. Erstellen Sie ein `Credential` Objekt mithilfe des Konstruktors und geben Sie den Alias an, indem Sie der `Credential` Objekteigenschaft einen Wert zuweisen `alias` .
   * Ein `HashAlgorithm` Objekt, das einen statischen Datenmember angibt, der den Hash-Algorithmus darstellt, mit dem das PDF-Dokument verarbeitet wird. Sie können beispielsweise angeben, `HashAlgorithm.SHA1` dass der SHA1-Algorithmus verwendet werden soll.
   * Ein boolescher Wert, der angibt, ob der Hash-Algorithmus verwendet wird.
   * Ein Zeichenfolgenwert, der den Grund für die Zertifizierung des PDF-Dokuments darstellt.
   * Ein Zeichenfolgenwert, der die Position des Unterzeichners darstellt.
   * Ein Zeichenfolgenwert, der die Kontaktinformationen des Unterzeichners darstellt.
   * Der statische Datenmember eines `MDPPermissions` Objekts, der Aktionen angibt, die für das PDF-Dokument ausgeführt werden können und die die Unterschrift ungültig machen.
   * Ein boolescher Wert, der angibt, ob das `MDPPermissions` Objekt, das als vorheriger Parameterwert übergeben wurde, verwendet werden soll.
   * Ein Zeichenfolgenwert, der erklärt, welche Aktionen die Unterschrift ungültig machen.
   * Ein `PDFSignatureAppearanceOptions` Objekt, das das Erscheinungsbild der zertifizierten Signatur steuert. Erstellen Sie ein Objekt `PDFSignatureAppearanceOptions`, indem Sie den Konstruktor verwenden. Sie können das Erscheinungsbild der Signatur ändern, indem Sie einen ihrer Datenmitglieder festlegen.
   * Ein `System.Boolean` Objekt, das angibt, ob eine Sperrüberprüfung für das Zertifikat des Unterzeichners durchgeführt werden soll. Wenn diese Sperrüberprüfung durchgeführt wird, wird sie in die Signatur eingebettet. Der Standardwert lautet `false`.
   * Ein `System.Boolean` Objekt, das angibt, ob das zertifizierte Unterschriftsfeld gesperrt ist. Wenn das Feld gesperrt ist, wird das Unterschriftsfeld als schreibgeschützt markiert, seine Eigenschaften können nicht geändert werden und es kann nicht von Personen gelöscht werden, die nicht über die erforderlichen Berechtigungen verfügen. Der Standardwert lautet `false`.
   * Ein `System.Boolean` Objekt, das angibt, ob das Unterschriftsfeld gesperrt ist. Das heißt, wenn Sie an `true` den vorherigen Parameter übergeben, dann an diesen Parameter übergeben `true` .
   * Ein `OCSPPreferences` Objekt, das Voreinstellungen für die Unterstützung des Online-Zertifikatstatusprotokolls (OCSP) speichert, das Informationen zum Status der Berechtigung bereitstellt, die zum Zertifizieren des PDF-Dokuments verwendet wird. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `CRLPreferences` Objekt, das die Voreinstellungen für die Zertifikatsperrliste (CRL) speichert. Wenn die Sperrüberprüfung nicht durchgeführt wird, wird dieser Parameter nicht verwendet und Sie können `null`angeben.
   * Ein `TSPPreferences` Objekt, das Voreinstellungen für die Unterstützung von Zeitstempelanbietern (TSP) speichert. Nachdem Sie beispielsweise ein `TSPPreferences` Objekt erstellt haben, können Sie die URL des TSP festlegen, indem Sie den `TSPPreferences` Datenmember des Objekts `tspServerURL` festlegen. Dieser Parameter ist optional und kann `null`verwendet werden.

   Die `certify` Methode gibt ein `BLOB` Objekt zurück, das das zertifizierte PDF-Dokument darstellt.

1. Zertifiziertes PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das das zertifizierte PDF-Dokument enthalten soll, sowie den Dateimodus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das von der `certify` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `binaryData` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[PDF-Dokumente zertifizieren](digitally-signing-certifying-documents.md#certifying-pdf-documents)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Verifying Digital Signatures {#verifying-digital-signatures}

Digitale Signaturen können überprüft werden, um sicherzustellen, dass ein signiertes PDF-Dokument nicht geändert wurde und die digitale Signatur gültig ist. Beim Überprüfen einer digitalen Signatur können Sie den Status der Signatur und die Eigenschaften der Signatur, z. B. die Identität des Unterzeichners, überprüfen. Bevor Sie einer digitalen Signatur vertrauen, sollten Sie sie überprüfen. Verwenden Sie beim Überprüfen einer digitalen Signatur ein PDF-Dokument, das eine digitale Signatur enthält.

Nehmen Sie an, dass die Identität des Unterzeichners unbekannt ist. Wenn Sie das PDF-Dokument in Acrobat öffnen, wird in einer Warnmeldung darauf hingewiesen, dass die Identität des Unterzeichners unbekannt ist (siehe folgende Abbildung).

![vd_vd_verifysig](assets/vd_vd_verifysig.png)

Ebenso können Sie beim programmatischen Überprüfen einer digitalen Signatur den Status der Identität des Unterzeichners bestimmen. Wenn Sie beispielsweise die Digitalsignatur im Dokument der vorherigen Abbildung überprüfen, ist die Identität des Unterzeichners unbekannt.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Überprüfen digitaler Signaturen finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

So überprüfen Sie eine Digitalsignatur:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das die zu überprüfende Signatur enthält.
1. Legen Sie PKI-Laufzeitoptionen fest.
1. Überprüfen Sie die digitale Signatur.
1. Legen Sie den Status der Signatur fest.
1. Bestimmen Sie die Identität des Unterzeichners.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Signaturclient erstellen**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert durchführen, erstellen Sie einen Signature-Dienstclient.

**PDF-Dokument abrufen, das die zu überprüfende Signatur enthält**

Wenn Sie eine Signatur überprüfen möchten, die zum digitalen Signieren oder Zertifizieren eines PDF-Dokuments verwendet wird, können Sie ein PDF-Dokument abrufen, das eine Signatur enthält.

**Festlegen von PKI-Laufzeitoptionen**

Legen Sie die folgenden PKI-Laufzeitoptionen fest, die der Signature-Dienst beim Überprüfen von Signaturen in einem PDF-Dokument verwendet:

* Überprüfungszeit
* Sperrüberprüfung
* Zeitstempelwerte

Während Sie diese Optionen einstellen, können Sie die Überprüfungszeit angeben. Sie können beispielsweise die aktuelle Zeit (die Zeit auf dem Computer des Validators) auswählen, was bedeutet, dass die aktuelle Zeit verwendet werden soll. Weitere Informationen zu den verschiedenen Zeitwerten finden Sie im Abschnitt zum Wert für die `VerificationTime` Auflistung in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Sie können auch angeben, ob die Sperrüberprüfung im Rahmen des Überprüfungsprozesses durchgeführt werden soll. Sie können beispielsweise eine Sperrüberprüfung durchführen, um zu ermitteln, ob das Zertifikat gesperrt wurde. Informationen zu den Optionen für die Prüfung von Sperren finden Sie im Abschnitt zum Wert `RevocationCheckStyle` Auflistung in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Um eine Sperrüberprüfung für ein Zertifikat durchzuführen, geben Sie mithilfe eines `CRLOptionSpec` Objekts eine URL zu einem Zertifikatsperrlisten-Liste (CRL) an. Wenn Sie jedoch keine URL für den Zertifikatsperrlisten-Server angeben, ruft der Signature-Dienst die URL aus dem Zertifikat ab.

Statt einen CRL-Server zu verwenden, können Sie einen OCSP-Server (Online Certificate Status Protocol) verwenden, wenn Sie die Sperrüberprüfung durchführen. Normalerweise wird die Sperrüberprüfung bei Verwendung eines OCSP-Servers im Gegensatz zu einem CRL-Server schneller durchgeführt. (See [Online Certificate Status Protocol](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signature-Dienst verwendet, indem Sie Adobe-Anwendungen und -Dienste verwenden. Beispiel: Wenn der OCSP-Server zuerst in Adobe Applications and Services eingestellt wird, wird der OCSP-Server und anschließend der CRL-Server überprüft.

Wenn Sie keine Sperrüberprüfung durchführen, prüft der Signature-Dienst nicht, ob das Zertifikat gesperrt wurde. Das heißt, die Serverinformationen für CRL und OCSP werden ignoriert.

>[!NOTE]
>
>Sie können die im Zertifikat angegebene URL mit einem `CRLOptionSpec` und einem `OCSPOptionSpec` Objekt überschreiben. Um beispielsweise den CRL-Server zu überschreiben, können Sie die `CRLOptionSpec` Methode des `setLocalURI` Objekts aufrufen.

Bei der Zeitstempelung wird der Zeitpunkt verfolgt, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, kann es von niemandem geändert werden. Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mit einem `TSPOptionSpec` Objekt festlegen. Sie können beispielsweise die URL eines TSP-Servers (Time Stamping Provider) angeben.

>[!NOTE]
>
>In den Beginn für die Schnellüberprüfung von Java und Webdienst ist die Überprüfungszeit auf `VerificationTime.CURRENT_TIME` und die Sperrüberprüfung auf `RevocationCheckStyle.BestEffort`. Da keine Zertifikatsperrlisten- oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem Zertifikat abgerufen.

**Digitalsignatur überprüfen**

Um eine Unterschrift erfolgreich zu überprüfen, geben Sie den vollständig qualifizierten Namen des Unterschriftsfelds an, das die Unterschrift enthält, z. B. `form1[0].#subform[1].SignatureField3[3]`. Bei Verwendung eines XFA-Formularfelds können Sie auch den Teilnamen des Signaturfelds verwenden: `SignatureField3`.

Standardmäßig beschränkt der Signature-Dienst die Zeit, die ein Dokument nach der Validierung signiert werden kann, auf 65 Minuten. Wenn ein Benutzer versucht, eine Signatur zur aktuellen Zeit zu überprüfen, und die Signaturzeit nach der aktuellen Zeit liegt und innerhalb von 65 Minuten liegt, erstellt der Signature-Dienst keinen Überprüfungsfehler.

>[!NOTE]
>
>Weitere Werte, die Sie beim Überprüfen einer Unterschrift benötigen, finden Sie unter API-Referenz für [AEM Forms](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Status der Signatur festlegen**

Bei der Überprüfung einer digitalen Signatur können Sie den Status der Signatur überprüfen.

**Identität des Unterzeichners bestimmen**

Sie können die Identität des Unterzeichners festlegen, bei der es sich um einen der folgenden Werte handeln kann:

* **Unbekannt**: Dieser Unterzeichner ist unbekannt, da die Unterzeichner-Überprüfung nicht durchgeführt werden kann.
* **Vertrauenswürdig**: Diesem Unterzeichner wird vertraut.
* **Nicht vertrauenswürdig**: Diesem Unterzeichner wird nicht vertraut.

**Siehe auch**

[Digitale Signaturen mit der Java-API überprüfen](#verify-digital-signatures-using-the-java-api)

[Digitale Signaturen mit der Web-Service-API überprüfen](#verify-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mit der Java-API überprüfen {#verify-digital-signatures-using-the-java-api}

Überprüfen einer digitalen Signatur mithilfe der Signature Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-signatures-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Signaturclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das die zu überprüfende Signatur enthält

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument darstellt, das die Signatur enthält, die mithilfe des Konstruktors überprüft werden soll. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Festlegen von PKI-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie die `PKIOptions` Objektmethode aufrufen und einen `setVerificationTime` `VerificationTime` Auflistung-Wert übergeben, der die Überprüfungszeit angibt.
   * Legen Sie die Option zur Prüfung der Sperre fest, indem Sie die `PKIOptions` Methode des `setRevocationCheckStyle` Objekts aufrufen und einen Wert für die `RevocationCheckStyle` Auflistung übergeben, der angibt, ob die Sperrüberprüfung durchgeführt werden soll.

1. Digitalsignatur überprüfen

   Überprüfen Sie die Unterschrift, indem Sie die `SignatureServiceClient` Methode des `verify2` Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` Objekt, das ein digital signiertes oder zertifiziertes PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Signaturfeldnamen darstellt, der die zu überprüfende Signatur enthält.
   * Ein `PKIOptions` Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions` Instanz, die SPI-Informationen enthält. Sie können `null` für diesen Parameter angeben.

   Die `verify2` Methode gibt ein `PDFSignatureVerificationInfo` Objekt zurück, das Informationen enthält, die zum Überprüfen der digitalen Signatur verwendet werden können.

1. Status der Signatur festlegen

   * Bestimmen Sie den Status der Unterschrift, indem Sie die `PDFSignatureVerificationInfo` Objektmethode `getStatus` aufrufen. Diese Methode gibt ein `SignatureStatus` Objekt zurück, das den Signaturstatus angibt. Wenn beispielsweise ein signiertes PDF-Dokument nicht geändert wird, gibt diese Methode `SignatureStatus.DocumentSigNoChanges`zurück.

1. Identität des Unterzeichners bestimmen

   * Bestimmen Sie die Identität des Unterzeichners, indem Sie die `PDFSignatureVerificationInfo` Methode des `getSigner` Objekts aufrufen. Diese Methode gibt ein `IdentityInformation` Objekt zurück.
   * Rufen Sie die `IdentityInformation` Methode des `getStatus` Objekts auf, um die Identität des Unterzeichners zu bestimmen. Diese Methode gibt einen `IdentityStatus` Identitätswert zurück, der die Auflistung angibt. Wenn der Unterzeichner beispielsweise vertrauenswürdig ist, gibt diese Methode `IdentityStatus.TRUSTED`zurück.

**Siehe auch**

[Digitale Signaturen überprüfen](#verify-digital-signatures-using-the-java-api)

[Quick Beginn (SOAP-Modus): Digitale Signaturen mit der Java-API überprüfen](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-a-digital-signature-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mit der Web-Service-API überprüfen {#verify-digital-signatures-using-the-web-service-api}

Überprüfen einer digitalen Signatur mithilfe der Signature Service API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument abrufen, das die zu überprüfende Signatur enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern eines PDF-Dokuments verwendet, das eine zu überprüfende digitale oder zertifizierte Signatur enthält.
   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB` Objekt, indem Sie dessen `MTOM` Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Festlegen von PKI-Laufzeitoptionen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie dem `PKIOptions` Datenmember des `verificationTime` Objekts einen `VerificationTime` Auflistung-Wert zuweisen, der die Überprüfungszeit angibt.
   * Legen Sie die Option zur Prüfung der Sperre fest, indem Sie dem `PKIOptions` Datenmember des `revocationCheckStyle` Objekts einen Wert für die `RevocationCheckStyle` Auflistung zuweisen, der angibt, ob die Sperrüberprüfung durchgeführt werden soll.

1. Digitalsignatur überprüfen

   Überprüfen Sie die Unterschrift, indem Sie die `SignatureServiceClient` Methode des `verify2` Objekts aufrufen und die folgenden Werte übergeben:

   * Das `BLOB` Objekt, das ein digital signiertes oder zertifiziertes PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Signaturfeldnamen darstellt, der die zu überprüfende Signatur enthält.
   * Ein `PKIOptions` Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions` Instanz, die SPI-Informationen enthält. Sie können `null` für diesen Parameter angeben.

   Die `verify2` Methode gibt ein `PDFSignatureVerificationInfo` Objekt zurück, das Informationen enthält, die zum Überprüfen der digitalen Signatur verwendet werden können.

1. Status der Signatur festlegen

   Bestimmen Sie den Status der Signatur, indem Sie den Wert des `PDFSignatureVerificationInfo` Objektdatenelements abrufen `status` . Dieser Datenmember speichert ein `SignatureStatus` Objekt, das den Status der Signatur angibt. Wenn beispielsweise ein signiertes PDF-Dokument geändert wird, speichert der `status` Datenmember den Wert `SignatureStatus.DocumentSigNoChanges`.

1. Identität des Unterzeichners bestimmen

   * Bestimmen Sie die Identität des Unterzeichners, indem Sie den Wert des `PDFSignatureVerificationInfo` Objektdatenelements `signer` abrufen. Dieses Element gibt ein `IdentityInformation` Objekt zurück.
   * Rufen Sie den `IdentityInformation` Datenmember des `status` Objekts ab, um die Identität des Unterzeichners zu bestimmen. Dieser Datenmember gibt einen `IdentityStatus` Identitätswert zurück, der die Auflistung angibt. Wenn der Unterzeichner beispielsweise vertrauenswürdig ist, gibt dieses Mitglied zurück `IdentityStatus.TRUSTED`.

**Siehe auch**

[Digitale Signaturen überprüfen](#verify-digital-signatures-using-the-java-api)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Verifying Multiple Digital Signatures {#verifying-multiple-digital-signatures}

AEM Forms bietet die Möglichkeit, alle digitalen Signaturen zu überprüfen, die sich in einem PDF-Dokument befinden. Angenommen, ein PDF-Dokument enthält mehrere digitale Signaturen, weil ein Geschäftsprozess Unterschriften von mehreren Unterzeichnern erfordert. Betrachten Sie zum Beispiel eine Finanztransaktion, die sowohl die Unterschrift eines Kreditsachverständigen als auch eines Managers erfordert. Sie können die Java-API oder Webdienst-API des Signature-Dienstes verwenden, um alle Signaturen im PDF-Dokument zu überprüfen. Beim Überprüfen mehrerer digitaler Signaturen können Sie den Status und die Eigenschaften jeder Signatur prüfen. Bevor Sie einer digitalen Signatur vertrauen, sollten Sie sie überprüfen. Es wird empfohlen, dass Sie mit der Überprüfung einer einzelnen digitalen Signatur vertraut sind.

>[!NOTE]
>
>Weitere Informationen zum Signature-Dienst und zum Überprüfen digitaler Signaturen finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

So überprüfen Sie mehrere digitale Unterschriften:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das die zu überprüfenden Signaturen enthält.
1. Legen Sie PKI-Laufzeitoptionen fest.
1. Rufen Sie alle digitalen Signaturen ab.
1. Durchlaufen Sie alle Unterschriften.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Signaturclient erstellen**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert durchführen, erstellen Sie einen Signature-Dienstclient.

**PDF-Dokument abrufen, das die zu überprüfenden Unterschriften enthält**

Wenn Sie eine Signatur überprüfen möchten, die zum digitalen Signieren oder Zertifizieren eines PDF-Dokuments verwendet wird, können Sie ein PDF-Dokument abrufen, das eine Signatur enthält.

**PKI-Laufzeitoptionen festlegen**

Legen Sie die folgenden PKI-Laufzeitoptionen fest, die der Signature-Dienst beim Überprüfen aller Signaturen in einem PDF-Dokument verwendet:

* Überprüfungszeit
* Sperrüberprüfung
* Zeitstempelwerte

Während Sie diese Optionen einstellen, können Sie die Überprüfungszeit angeben. Sie können beispielsweise die aktuelle Zeit (die Zeit auf dem Computer des Validators) auswählen, was bedeutet, dass die aktuelle Zeit verwendet werden soll. Weitere Informationen zu den verschiedenen Zeitwerten finden Sie im Abschnitt zum Wert für die `VerificationTime` Auflistung in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Sie können auch angeben, ob die Sperrüberprüfung im Rahmen des Überprüfungsprozesses durchgeführt werden soll. Sie können beispielsweise eine Sperrüberprüfung durchführen, um zu ermitteln, ob das Zertifikat gesperrt wurde. Informationen zu den Optionen für die Prüfung von Sperren finden Sie im Abschnitt zum Wert `RevocationCheckStyle` Auflistung in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

Um eine Sperrüberprüfung für ein Zertifikat durchzuführen, geben Sie mithilfe eines `CRLOptionSpec` Objekts eine URL zu einem Zertifikatsperrlisten-Liste (CRL) an. Wenn Sie jedoch keine URL für einen Zertifikatsperrlisten-Server angeben, ruft der Signature-Dienst die URL aus dem Zertifikat ab.

Statt einen CRL-Server zu verwenden, können Sie einen OCSP-Server (Online Certificate Status Protocol) verwenden, wenn Sie die Sperrüberprüfung durchführen. Normalerweise wird die Sperrüberprüfung schneller durchgeführt, wenn ein OCSP-Server anstelle eines CRL-Servers verwendet wird. (See [Online Certificate Status Protocol](https://tools.ietf.org/html/rfc2560).)

Sie können die CRL- und OCSP-Serverreihenfolge festlegen, die der Signature-Dienst verwendet, indem Sie Adobe-Anwendungen und -Dienste verwenden. Wenn beispielsweise der OCSP-Server zuerst in Adobe Applications and Services festgelegt wird, wird der OCSP-Server und anschließend der CRL-Server überprüft.

Wenn Sie keine Sperrüberprüfung durchführen, prüft der Signature-Dienst nicht, ob das Zertifikat gesperrt wurde. Das heißt, die Serverinformationen für CRL und OCSP werden ignoriert.

>[!NOTE]
>
>Sie können die im Zertifikat angegebene URL mit einem `CRLOptionSpec` und einem `OCSPOptionSpec` Objekt überschreiben. Um beispielsweise den CRL-Server zu überschreiben, können Sie die `CRLOptionSpec` Methode des `setLocalURI` Objekts aufrufen.

Bei der Zeitstempelung wird der Zeitpunkt verfolgt, zu dem ein signiertes oder zertifiziertes Dokument geändert wurde. Nachdem ein Dokument signiert wurde, kann es von niemandem geändert werden. Zeitstempel helfen, die Gültigkeit eines signierten oder zertifizierten Dokuments zu erzwingen. Sie können Zeitstempeloptionen mithilfe eines `TSPOptionSpec` Objekts festlegen. Sie können beispielsweise die URL eines TSP-Servers (Time Stamping Provider) angeben.

>[!NOTE]
>
>In den Beginn für die Schnellüberprüfung von Java und Webdienst ist die Überprüfungszeit auf `VerificationTime.CURRENT_TIME` und die Sperrüberprüfung auf `RevocationCheckStyle.BestEffort`. Da keine Zertifikatsperrlisten- oder OCSP-Serverinformationen angegeben sind, werden die Serverinformationen aus dem Zertifikat abgerufen.

**Alle digitalen Signaturen abrufen**

Um alle digitalen Unterschriften in einem PDF-Dokument zu überprüfen, rufen Sie die digitalen Unterschriften aus dem PDF-Dokument ab. Alle Signaturen werden in einer Liste zurückgegeben. Überprüfen Sie im Rahmen der Überprüfung einer digitalen Signatur den Status der Signatur.

>[!NOTE]
>
>Anders als bei der Überprüfung einer einzelnen digitalen Unterschrift müssen Sie bei der Überprüfung mehrerer Unterschriften nicht den Unterschriftsfeldnamen angeben.

**Durchsuchen aller Unterschriften**

Durchlaufen Sie jede Unterschrift. Das heißt, für jede Signatur überprüfen Sie die digitale Signatur und überprüfen Sie die Identität des Unterzeichners und den Status jeder Signatur. (Siehe [Digitale Signaturen](#verify-digital-signatures-using-the-java-api)überprüfen.)

>[!NOTE]
>
>Sie müssen nicht alle Unterschriften durchlaufen, wenn die Anforderung das gesamte Dokument ist.

**Siehe auch**

[Mehrere digitale Signaturen mit der Java-API überprüfen](#verify-digital-signatures-using-the-java-api)

[Mehrere digitale Signaturen mithilfe der Webdienst-API überprüfen](#verify-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mehrere digitale Signaturen mit der Java-API überprüfen {#verify-multiple-digital-signatures-using-the-java-api}

Mehrere digitale Signaturen mithilfe der Signature Service API (Java) überprüfen:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-signatures-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Signaturclient erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das die zu überprüfenden Unterschriften enthält

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument darstellt, das mehrere digitale Signaturen enthält, die mithilfe des Konstruktors überprüft werden sollen. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie die `PKIOptions` Objektmethode aufrufen und einen `setVerificationTime` `VerificationTime` Auflistung-Wert übergeben, der die Überprüfungszeit angibt.
   * Legen Sie die Option zur Prüfung der Sperre fest, indem Sie die `PKIOptions` Methode des `setRevocationCheckStyle` Objekts aufrufen und einen Wert für die `RevocationCheckStyle` Auflistung übergeben, der angibt, ob die Sperrüberprüfung durchgeführt werden soll.

1. Alle digitalen Signaturen abrufen

   Rufen Sie die `SignatureServiceClient` Objektmethode `verifyPDFDocument` auf und übergeben Sie die folgenden Werte:

   * Ein `com.adobe.idp.Document` Objekt, das ein PDF-Dokument mit mehreren digitalen Unterschriften enthält.
   * Ein `PKIOptions` Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions` Instanz, die SPI-Informationen enthält. Sie können `null` für diesen Parameter angeben.

   Die `verifyPDFDocument` Methode gibt ein `PDFDocumentVerificationInfo` Objekt zurück, das Informationen über alle digitalen Unterschriften im PDF-Dokument enthält.

1. Durchsuchen aller Unterschriften

   * Durchlaufen Sie alle Unterschriften, indem Sie die `PDFDocumentVerificationInfo` Objektmethode `getVerificationInfos` aufrufen. Diese Methode gibt ein `java.util.List` Objekt zurück, bei dem jedes Element ein `PDFSignatureVerificationInfo` Objekt ist. Verwenden Sie ein `java.util.Iterator` Objekt, um durch die Liste der Unterschriften zu iterieren.
   * Mithilfe des `PDFSignatureVerificationInfo` Objekts können Sie Aufgaben durchführen, z. B. den Signaturstatus durch Aufrufen der `PDFSignatureVerificationInfo` Objektmethode `getStatus` bestimmen. Diese Methode gibt ein `SignatureStatus` Objekt zurück, dessen statisches Datenelement Sie über den Status der Signatur informiert. Wenn die Signatur beispielsweise unbekannt ist, gibt diese Methode `SignatureStatus.DocumentSignatureUnknown`zurück.

**Siehe auch**

[Überprüfen mehrerer digitaler Signaturen](#verifying-multiple-digital-signatures)

[Quick Beginn (SOAP-Modus): Mehrere digitale Signaturen mit der Java-API überprüfen](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-verifying-multiple-digital-signatures-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Digitale Signaturen überprüfen](#verify-digital-signatures-using-the-java-api)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mehrere digitale Signaturen mithilfe der Webdienst-API überprüfen {#verifying-multiple-digital-signatures-using-the-web-service-api}

Mehrere digitale Signaturen mithilfe der Signature Service API (Webdienst) überprüfen:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument abrufen, das die zu überprüfenden Unterschriften enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt speichert ein PDF-Dokument, das mehrere zu überprüfende digitale Unterschriften enthält.
   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB` Objekt, indem Sie dessen `MTOM` Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. PKI-Laufzeitoptionen festlegen

   * Erstellen Sie ein Objekt `PKIOptions`, indem Sie den Konstruktor verwenden.
   * Legen Sie die Überprüfungszeit fest, indem Sie dem `PKIOptions` Datenmember des `verificationTime` Objekts einen `VerificationTime` Auflistung-Wert zuweisen, der die Überprüfungszeit angibt.
   * Legen Sie die Option zur Prüfung der Sperre fest, indem Sie dem `PKIOptions` Datenmember des `revocationCheckStyle` Objekts einen Wert für die `RevocationCheckStyle` Auflistung zuweisen, der angibt, ob die Sperrüberprüfung durchgeführt werden soll.

1. Alle digitalen Signaturen abrufen

   Rufen Sie die `SignatureServiceClient` Objektmethode `verifyPDFDocument` auf und übergeben Sie die folgenden Werte:

   * Ein `BLOB` Objekt, das ein PDF-Dokument mit mehreren digitalen Unterschriften enthält.
   * Ein `PKIOptions` Objekt, das PKI-Laufzeitoptionen enthält.
   * Eine `VerifySPIOptions` Instanz, die SPI-Informationen enthält. Sie können null für diesen Parameter angeben.

   Die `verifyPDFDocument` Methode gibt ein `PDFDocumentVerificationInfo` Objekt zurück, das Informationen über alle digitalen Unterschriften im PDF-Dokument enthält.

1. Durchsuchen aller Unterschriften

   * Durchlaufen Sie alle Unterschriften, indem Sie den `PDFDocumentVerificationInfo` Datenmember des Objekts `verificationInfos` abrufen. Dieser Datenmember gibt ein `Object` Array zurück, bei dem jedes Element ein `PDFSignatureVerificationInfo` Objekt ist.
   * Mithilfe des `PDFSignatureVerificationInfo` Objekts können Sie Aufgaben wie das Festlegen des Unterschriftsstatus durchführen, indem Sie den `PDFSignatureVerificationInfo` Datenmember des Objekts abrufen `status` . Dieser Datenmember gibt ein `SignatureStatus` Objekt zurück, dessen statisches Datenelement Sie über den Status der Signatur informiert. Wenn die Signatur beispielsweise unbekannt ist, gibt diese Methode `SignatureStatus.DocumentSignatureUnknown`zurück.

**Siehe auch**

[Überprüfen mehrerer digitaler Signaturen](#verifying-multiple-digital-signatures)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Removing Digital Signatures {#removing-digital-signatures}

Digitale Signaturen müssen aus einem Signaturfeld entfernt werden, bevor eine neuere digitale Signatur angewendet werden kann. Eine digitale Signatur kann nicht überschrieben werden. Wenn Sie versuchen, eine digitale Unterschrift auf ein Unterschriftsfeld anzuwenden, das eine Unterschrift enthält, tritt eine Ausnahme auf.

>[!NOTE]
>
>For more information about the Signature service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

So entfernen Sie eine digitale Unterschrift aus einem Unterschriftsfeld:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Signaturclient.
1. Rufen Sie das PDF-Dokument ab, das eine zu entfernende Unterschrift enthält.
1. Entfernen Sie die digitale Signatur aus dem Signaturfeld.
1. Speichern Sie das PDF-Dokument als PDF-Datei.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-signatures-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)
* jbossall-client.jar (erforderlich, wenn AEM Forms unter JBoss bereitgestellt werden)

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Signaturclient erstellen**

Bevor Sie einen Signature-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Signature-Dienstclient erstellen.

**PDF-Dokument abrufen, das eine Signatur zum Entfernen enthält**

Um eine Unterschrift aus einem PDF-Dokument zu entfernen, müssen Sie ein PDF-Dokument abrufen, das eine Unterschrift enthält.

**Entfernen der digitalen Signatur aus dem Signaturfeld**

Um eine digitale Unterschrift erfolgreich aus einem PDF-Dokument zu entfernen, müssen Sie den Namen des Unterschriftsfelds angeben, das die digitale Unterschrift enthält. Außerdem müssen Sie über die Berechtigung zum Entfernen der digitalen Signatur verfügen. Andernfalls tritt eine Ausnahme auf.

**PDF-Dokument als PDF-Datei speichern**

Nachdem der Signature-Dienst eine digitale Signatur aus einem Signaturfeld entfernt hat, können Sie das PDF-Dokument als PDF-Datei speichern, damit die Benutzer es in Acrobat oder Adobe Reader öffnen können.

**Siehe auch**

[Digitale Signaturen mit der Java-API entfernen](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-java-api)

[Digitale Signaturen mit der Webdienst-API entfernen](digitally-signing-certifying-documents.md#remove-digital-signatures-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Signaturfelder hinzufügen](digitally-signing-certifying-documents.md#adding-signature-fields)

### Digitale Signaturen mit der Java-API entfernen {#remove-digital-signatures-using-the-java-api}

Entfernen Sie eine digitale Signatur mithilfe der Signature-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-signatures-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Signaturclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `SignatureServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen, das eine Signatur zum Entfernen enthält

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument darstellt, das die zu entfernende Unterschrift enthält, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen der digitalen Signatur aus dem Signaturfeld

   Entfernen Sie eine digitale Signatur aus einem Signaturfeld, indem Sie die `SignatureServiceClient` `clearSignatureField` Objektmethode aufrufen und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document` Objekt, das das PDF-Dokument darstellt, das die zu entfernende Unterschrift enthält.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds angibt, das die digitale Signatur enthält.

   Die `clearSignatureField` Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das das PDF-Dokument darstellt, aus dem die digitale Unterschrift entfernt wurde.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .pdf ist.
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf. Übergeben Sie das `java.io.File` Objekt, um den Inhalt des `com.adobe.idp.Document` Objekts in die Datei zu kopieren. Stellen Sie sicher, dass Sie das `Document`-Objekt verwenden, das von der `clearSignatureField`-Methode zurückgegeben wurde.

**Siehe auch**

[Entfernen digitaler Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Quick Beginn (SOAP-Modus): Entfernen einer digitalen Signatur mit der Java-API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-removing-a-digital-signature-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Digitale Signaturen mit der Webdienst-API entfernen {#remove-digital-signatures-using-the-web-service-api}

Entfernen Sie eine digitale Signatur mithilfe der Signature-API (Webdienst):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/SignatureService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` dies durch die IP-Adresse des Hosting-AEM Forms.

1. Signaturclient erstellen

   * Create a `SignatureServiceClient` object by using its default constructor.
   * Create a `SignatureServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/SignatureService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `SignatureServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `SignatureServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `SignatureServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. PDF-Dokument abrufen, das eine Signatur zum Entfernen enthält

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern eines PDF-Dokuments verwendet, das eine zu entfernende digitale Unterschrift enthält.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des signierten PDF-Dokuments und den Dateimodus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `MTOM` Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Entfernen der digitalen Signatur aus dem Signaturfeld

   Entfernen Sie die digitale Signatur, indem Sie die `SignatureServiceClient` Methode des `clearSignatureField` Objekts aufrufen und die folgenden Werte übergeben:

   * Ein `BLOB` Objekt, das das signierte PDF-Dokument enthält.
   * Ein Zeichenfolgenwert, der den Namen des Signaturfelds darstellt, das die zu entfernende digitale Signatur enthält.

   Die `clearSignatureField` Methode gibt ein `BLOB` Objekt zurück, das das PDF-Dokument darstellt, aus dem die digitale Unterschrift entfernt wurde.

1. PDF-Dokument als PDF-Datei speichern

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments darstellt, das ein leeres Unterschriftsfeld enthält, sowie den Dateimodus, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das von der `sign` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in die PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[Entfernen digitaler Signaturen](digitally-signing-certifying-documents.md#removing-digital-signatures)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aufrufen mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
