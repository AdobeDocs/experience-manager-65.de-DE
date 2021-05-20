---
title: Konvertieren von Postscript in PDF-Dokumente
seo-title: Konvertieren von Postscript in PDF-Dokumente
description: Verwenden Sie den Distiller-Dienst zum Konvertieren von PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien in kompakte, zuverlässige und sicherere PDF-Dateien über ein Netzwerk. Der Distiller-Dienst konvertiert große Mengen von Druckdokumenten in elektronische Dokumente, z. B. Rechnungen und Aussagen mithilfe der Java-API und der Web Service-API.
seo-description: Verwenden Sie den Distiller-Dienst zum Konvertieren von PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien in kompakte, zuverlässige und sicherere PDF-Dateien über ein Netzwerk. Der Distiller-Dienst konvertiert große Mengen von Druckdokumenten in elektronische Dokumente, z. B. Rechnungen und Aussagen mithilfe der Java-API und der Web Service-API.
uuid: 2143f406-1fdd-4551-a738-1a8388f8d478
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 06ad343a-f74d-41f5-b3c8-b85bb723ceeb
role: Developer
exl-id: 744df8b2-0c61-410f-89e9-20b8adddbf45
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 6%

---

# Konvertieren von Postscript in PDF-Dokumente {#converting-postscript-to-pdf-documents}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Über den Distiller-Dienst {#about-the-distiller-service}

Der Distiller®-Dienst konvertiert PostScript®-, Encapsulated PostScript (EPS)- und PRN-Dateien in kompakte, zuverlässige und sicherere PDF-Dateien über ein Netzwerk. Der Distiller-Dienst dient häufig zum Konvertieren großen Mengen gedruckter Dokumente in elektronische Dokumente, z. B. Rechnungen und Belege. Das Konvertieren von Dokumenten in PDF ermöglicht Unternehmen auch, ihren Kunden eine Papier- und eine elektronische Version eines Dokuments zu senden.

>[!NOTE]
>
>Weitere Informationen zum Distiller-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von PostScript in PDF-Dokumente {#converting-postscript-to-pdf-documents-inner}

Hier wird beschrieben, wie Sie mit der Distiller Service API (Java- und Webdienst) PostScript- (PS), Encapsulated PostScript (EPS)- und PRN-Dateien programmgesteuert in PDF-Dokumente konvertieren können.

>[!NOTE]
>
>Weitere Informationen zum Distiller-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Um PostScript-Dateien in PDF-Dokumente zu konvertieren, muss einer der folgenden Schritte auf dem Server installiert sein, der als Host für AEM Forms dient: Redistributable Package für Acrobat 9 oder Microsoft Visual C++ 2005.

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Schritte aus, um einen der unterstützten Typen in ein PDF-Dokument zu konvertieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen Distiller-Dienstclient.
1. Rufen Sie die zu konvertierende Datei ab.
1. Rufen Sie den PDF-Erstellungsvorgang auf.
1. Speichern Sie das PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Distiller-Dienstclients**

Bevor Sie einen Distiller-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Distiller-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DistillerServiceClient` -Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie ein `DistillerServiceService` -Objekt.

**Zu konvertierende Datei abrufen**

Sie müssen die Datei abrufen, die Sie konvertieren möchten. Um beispielsweise eine PS-Datei in ein PDF-Dokument zu konvertieren, müssen Sie die PS-Datei abrufen.

**Aufrufen des PDF-Erstellungsvorgangs**

Nachdem Sie den Dienst-Client erstellt haben, können Sie den PDF-Erstellungsvorgang aufrufen. Dieser Vorgang benötigt Informationen zum zu konvertierenden Dokument, einschließlich des Pfads zum Zieldokument.

**PDF-Dokument speichern**

Sie können das PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Konvertieren einer PostScript-Datei in PDF mithilfe der Java-API](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Konvertieren einer PostScript-Datei in PDF mithilfe der Webdienst-API](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur API für Output Service](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Konvertieren einer PostScript-Datei in PDF mithilfe der Java-API {#convert-a-postscript-file-to-pdf-using-the-java-api}

Konvertieren einer PostScript-Datei in ein PDF-Dokument mithilfe der Distiller Service API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-tiller-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DistillerServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das die zu konvertierende Datei mithilfe des zugehörigen Konstruktors darstellt und einen string -Wert übergibt, der den Speicherort der Datei angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die `createPDF` -Methode des Objekts `DistillerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Das `com.adobe.idp.Document`-Objekt, das die zu konvertierende PS-, EPS- oder PRN-Datei darstellt.
   * Ein `java.lang.String` -Objekt, das den Namen der zu konvertierenden Datei enthält
   * Ein `java.lang.String` -Objekt, das den Namen der zu verwendenden Adobe PDF-Einstellungen enthält
   * Ein `java.lang.String` -Objekt, das den Namen der zu verwendenden Sicherheitseinstellungen enthält
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen
   * Ein optionales `com.adobe.idp.Document` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen

   Die `createPDF`-Methode gibt ein `CreatePDFResult`-Objekt zurück, das das neue PDF-Dokument und eine eventuell generierte Protokolldatei enthält. Die Protokolldatei enthält in der Regel Fehler- oder Warnmeldungen, die von der Konvertierungsanforderung generiert werden.

1. Speichern Sie das PDF-Dokument.

   Um das neu erstellte PDF-Dokument abzurufen, führen Sie die folgenden Schritte aus:

   * Rufen Sie die `getCreatedDocument` -Methode des Objekts `CreatePDFResult` auf. Dadurch wird ein `com.adobe.idp.Document` -Objekt zurückgegeben.
   * Rufen Sie die `copyToFile`-Methode des Objekts `com.adobe.idp.Document` auf, um das PDF-Dokument zu extrahieren.

   Um das Protokolldokument abzurufen, führen Sie die folgenden Schritte aus.

   * Rufen Sie die `getLogDocument` -Methode des Objekts `CreatePDFResult` auf. Dadurch wird ein `com.adobe.idp.Document` -Objekt zurückgegeben.
   * Rufen Sie die `copyToFile` -Methode des Objekts `com.adobe.idp.Document` auf, um das Protokolldokument zu extrahieren.


**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren einer PostScript-Datei in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren einer PostScript-Datei in PDF mithilfe der Webdienst-API {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Konvertieren einer PostScript-Datei in ein PDF-Dokument mithilfe der Distiller Service API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Distiller-Dienstclient.

   * Erstellen Sie ein `DistillerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DistillerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DistillerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Geben Sie jedoch `?blob=mtom` an, um MTOM zu verwenden.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DistillerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DistillerServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DistillerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie die zu konvertierende Datei ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Dieses `BLOB`-Objekt wird zum Speichern der Datei verwendet, die in ein PDF-Dokument konvertiert werden soll.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen `MTOM`-Eigenschaft dem Inhalt des Byte-Arrays zuweisen.

1. Rufen Sie den PDF-Erstellungsvorgang auf.

   Rufen Sie die `CreatePDF2` -Methode des Objekts `DistillerServiceService` auf und übergeben Sie die folgenden erforderlichen Werte:

   * Das `BLOB`-Objekt, das die zu konvertierende PS-Datei darstellt
   * Eine Zeichenfolge, die den Pfadnamen der zu konvertierenden Datei enthält
   * Ein string -Objekt, das die zu verwendenden Adobe PDF-Einstellungen enthält (z. B. `Standard`).
   * Ein string -Objekt, das die zu verwendenden Sicherheitseinstellungen enthält (z. B. `No Securit`y)
   * Ein optionales `BLOB` -Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen
   * Ein optionales `BLOB` -Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen
   * Ein `BLOB` Ausgabeparameter, der zum Speichern des PDF-Dokuments verwendet wird
   * Ein `BLOB` Ausgabeparameter, der zum Speichern des Protokolls verwendet wird

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des signierten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `BLOB` -Objekts speichert, das von der `CreatePDF2` -Methode (dem Ausgabeparameter) zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
