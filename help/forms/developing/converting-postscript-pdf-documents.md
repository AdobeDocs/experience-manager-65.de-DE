---
title: Konvertieren von PostScript in PDF-Dokumente
seo-title: Konvertieren von PostScript in PDF-Dokumente
description: 'null'
seo-description: 'null'
uuid: 2143f406-1fdd-4551-a738-1a8388f8d478
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 06ad343a-f74d-41f5-b3c8-b85bb723ceeb
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Konvertieren von PostScript in PDF-Dokumente {#converting-postscript-to-pdf-documents}

## Informationen zum Distiller-Dienst {#about-the-distiller-service}

Der Distiller®-Dienst konvertiert PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien in kompakte, zuverlässige und sicherere PDF-Dateien über ein Netzwerk. Der Distiller-Dienst dient häufig zum Konvertieren großen Mengen gedruckter Dokumente in elektronische Dokumente, z. B. Rechnungen und Belege. Das Konvertieren von Dokumenten in PDF ermöglicht Unternehmen auch, ihren Kunden eine Papier- und eine elektronische Version eines Dokuments zu senden.

>[!NOTE]
>
>For more information about the Distiller service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PostScript in PDF-Dokumente {#converting-postscript-to-pdf-documents-inner}

In diesem Thema wird beschrieben, wie Sie mit der Distiller Service API (Java und Webdienst) PostScript- (PS), Encapsulated PostScript- (EPS) und PRN-Dateien programmatisch in PDF-Dokumente konvertieren können.

>[!NOTE]
>
>For more information about the Distiller service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Um PostScript-Dateien in PDF-Dokumente zu konvertieren, muss auf dem Server, der als Host für AEM Forms dient, einer der folgenden Programme installiert sein: Redistributable Package für Acrobat 9 oder Microsoft Visual C++ 2005.

### Zusammenfassung der Schritte {#summary-of-steps}

So konvertieren Sie einen der unterstützten Typen in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Distiller-Dienstclient.
1. Rufen Sie die zu konvertierende Datei ab.
1. Rufen Sie den PDF-Erstellungsvorgang auf.
1. Speichern Sie das PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Distiller-Dienstclients**

Bevor Sie einen Distiller-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Distiller-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DistillerServiceClient` Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie ein `DistillerServiceService` Objekt.

**Zu konvertierende Datei abrufen**

Sie müssen die Datei abrufen, die Sie konvertieren möchten. Um beispielsweise eine PS-Datei in ein PDF-Dokument zu konvertieren, müssen Sie die PS-Datei abrufen.

**PDF-Erstellungsvorgang aufrufen**

Nachdem Sie den Dienstclient erstellt haben, können Sie den PDF-Erstellungsvorgang aufrufen. Dieser Vorgang erfordert Informationen zum zu konvertierenden Dokument, einschließlich des Pfads zum Zieldokument.

**PDF-Dokument speichern**

Sie können das PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[PostScript-Dateien mit der Java-API in PDF konvertieren](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Konvertieren einer PostScript-Datei in eine PDF-Datei mit der Webdienst-API](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API des Output-Dienstes](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### PostScript-Dateien mit der Java-API in PDF konvertieren {#convert-a-postscript-file-to-pdf-using-the-java-api}

Konvertieren einer PostScript-Datei in ein PDF-Dokument mithilfe der Distiller Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien, wie z. B. adobe-tiller-client.jar, in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Create an `DistillerServiceClient` object by using its constructor and passing the `ServiceClientFactory` object.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das die zu konvertierende Datei darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort der Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die `DistillerServiceClient` Objektmethode `createPDF` auf und übergeben Sie die folgenden Werte:

   * Das `com.adobe.idp.Document` Objekt, das die zu konvertierende PS-, EPS- oder PRN-Datei darstellt
   * Ein `java.lang.String` Objekt, das den Namen der zu konvertierenden Datei enthält
   * Ein `java.lang.String` Objekt, das den Namen der zu verwendenden Adobe PDF-Einstellungen enthält
   * Ein `java.lang.String` Objekt mit dem Namen der zu verwendenden Sicherheitseinstellungen
   * Ein optionales `com.adobe.idp.Document` Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen
   * Ein optionales `com.adobe.idp.Document` Objekt mit Metadateninformationen, die auf das PDF-Dokument angewendet werden sollen
   Die `createPDF` Methode gibt ein `CreatePDFResult` Objekt zurück, das das neue PDF-Dokument und eine eventuell generierte Protokolldatei enthält. Die Protokolldatei enthält in der Regel Fehler- oder Warnmeldungen, die von der Konvertierungsanforderung generiert werden.

1. Speichern Sie das PDF-Dokument.

   So rufen Sie das neu erstellte PDF-Dokument ab:

   * Rufen Sie die `CreatePDFResult` Methode des `getCreatedDocument` Objekts auf. Dadurch wird ein `com.adobe.idp.Document` Objekt zurückgegeben.
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf, um das PDF-Dokument zu extrahieren.
   Um das Protokolldokument abzurufen, führen Sie die folgenden Schritte aus.

   * Rufen Sie die `CreatePDFResult` Methode des `getLogDocument` Objekts auf. Dadurch wird ein `com.adobe.idp.Document` Objekt zurückgegeben.
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf, um das Protokolldokument zu extrahieren.


**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

[Kurzanleitung (SOAP-Modus): Konvertieren einer PostScript-Datei in ein PDF-Dokument mit der Java-API](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren einer PostScript-Datei in eine PDF-Datei mit der Webdienst-API {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Konvertieren einer PostScript-Datei in ein PDF-Dokument mithilfe der Distiller Service API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Create a `DistillerServiceClient` object by using its default constructor.
   * Create a `DistillerServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/DistillerService?blob=mtom`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` die Verwendung von MTOM an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `DistillerServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `DistillerServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DistillerServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Mit diesem `BLOB` Objekt wird die Datei gespeichert, die in ein PDF-Dokument konvertiert werden soll.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seine `MTOM` Eigenschaft mit dem Inhalt des Byte-Arrays zuweisen.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die `DistillerServiceService` Objektmethode `CreatePDF2` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Das `BLOB` Objekt, das die zu konvertierende PS-Datei darstellt
   * Eine Zeichenfolge, die den Pfadnamen der zu konvertierenden Datei enthält
   * Ein Zeichenfolgenobjekt, das die zu verwendenden Adobe PDF-Einstellungen enthält (z. B. `Standard`)
   * Ein Zeichenfolgenobjekt, das die zu verwendenden Sicherheitseinstellungen enthält (z. B. `No Securit`y)
   * Ein optionales `BLOB` Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen
   * Ein optionales `BLOB` Objekt mit Metadateninformationen, die auf das PDF-Dokument angewendet werden sollen
   * Ein `BLOB` Ausgabeparameter zum Speichern des PDF-Dokuments
   * Ein `BLOB` Ausgabeparameter zum Speichern des Protokolls

1. Speichern Sie das PDF-Dokument.

   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `BLOB` Objekts speichert, das von der `CreatePDF2` Methode zurückgegeben wurde (der Ausgabeparameter). Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
