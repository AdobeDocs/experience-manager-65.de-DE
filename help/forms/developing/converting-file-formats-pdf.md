---
title: Zwischen Dateiformaten und PDF konvertieren
description: Verwenden Sie den Generate PDF-Dienst, um native Dateiformate in PDF zu konvertieren. Der Generate PDF-Dienst kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 10535740-e3c2-4347-a88f-86706ad699b4
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '7812'
ht-degree: 89%

---

# Zwischen Dateiformaten und PDF konvertieren {#converting-between-file-formatsand-pdf}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über Generate PDF-Dienst**

Der Generate PDF-Dienst konvertiert native Dateiformate in PDF. Er kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren.

Der Generate PDF-Dienst verwendet native Programme, um die folgenden Dateiformate in PDF zu konvertieren. Sofern nicht anders angegeben, werden nur die deutsche, französische, englische und japanische Version dieser Anwendungen unterstützt. *Nur Windows* bedeutet, dass nur Windows Server® 2003 und Windows Server 2008 unterstützt werden.

* Microsoft Office 2003 und 2007 zum Konvertieren von DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX, XPS und PUB (nur Windows)

>[!NOTE]
>
>Acrobat® 9.2 oder höher ist erforderlich, um das Microsoft XPS-Format in PDF zu konvertieren.

* Autodesk AutoCAD 2005, 2006, 2007, 2008 und 2009 zum Konvertieren von DWF, DWG und DXW (nur auf Englisch)
* Corel WordPerfect 12 und X4 zum Konvertieren von WPD, QPW, SHW (nur auf Englisch)
* OpenOffice 2.0, 2.4, 3.0.1 und 3.1 zum Konvertieren von ODT, ODS, ODP, ODG, ODF, SXW, SXI, SXC, SXD, DOC, DOCX, RTF, TXT, XLS, XLSX, PPT, PPTX, VSD, MPP, MPPX und PUB

>[!NOTE]
>
Der Generate PDF-Dienst unterstützt keine 64-Bit-Versionen von OpenOffice.

* Adobe Photoshop® CS2 zum Konvertieren von PSD (nur Windows)

>[!NOTE]
>
Photoshop CS3 und CS4 werden nicht unterstützt, da sie Windows Server 2003 oder Windows Server 2008 nicht unterstützen.

* Adobe FrameMaker® 7.2 zum Konvertieren von FM (nur Windows)
* Adobe PageMaker® 7.0 zum Konvertieren von PMD, PM6, P65 und PM (nur Windows)
* Native Formate, die von Drittanbieteranwendungen unterstützt werden (erfordert die Entwicklung von Setupdateien, die spezifisch für die Anwendung sind) (nur Windows)

Der Generate PDF-Dienst konvertiert die folgenden standardbasierten Dateiformate in PDF.

* Videoformate: SWF, FLV (nur Windows)
* Bildformate: JPEG, JPG, JP2, J2Kí, JPC, J2C, GIF, BMP, TIFF, TIF, PNG, JPF
* HTML (Windows, Sun™ Solaris™ und Linux®)

Der Generate PDF-Dienst konvertiert PDF in die folgenden Dateiformate (nur Windows):

* Encapsulated PostScript (EPS)
* HTML 3.2
* HTML 4.01 mit CSS 1.0
* DOC (Microsoft Word-Format)
* RTF
* Text (sowohl barrierefrei als auch einfach)
* XML
* PDF/A-1a, das nur den DeviceRGB-Farbraum verwendet
* PDF/A-1b, das nur den DeviceRGB-Farbraum verwendet

Für den Generate PDF-Dienst müssen Sie die folgenden Verwaltungsaufgaben ausführen:

* Installieren Sie die erforderlichen nativen Anwendungen auf dem Computer, auf dem AEM Forms gehostet wird.
* Installieren Sie Adobe Acrobat Professional oder Acrobat Pro Extended 9.2 auf dem Computer, der als Host für AEM Forms dient
* Ausführen von Einrichtungsaufgaben nach der Installation

Diese Aufgaben werden unter „Installieren und Bereitstellen von AEM Forms“ mithilfe von JBoss Turnkey beschrieben.

Mithilfe des Generate PDF-Dienstes können Sie diese Aufgaben ausführen:

* Konvertieren von nativen Dateiformaten in PDF.
* Konvertieren von HTML-Dokumenten in PDF-Dokumente.
* Konvertieren von PDF-Dokumenten in Dateiformate.

>[!NOTE]
>
Weitere Informationen zum Generate PDF-Dienst finden Sie in der [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Konvertieren von Word-Dokumenten in PDF-Dokumente {#converting-word-documents-to-pdf-documents}

In diesem Abschnitt wird beschrieben, wie Sie mit der Generate PDF-API ein Microsoft Word-Dokument programmgesteuert in ein PDF-Dokument konvertieren können.

>[!NOTE]
>
Weitere Informationen zu weiteren Dateiformaten finden Sie unter [Hinzufügen der Unterstützung für weitere native Dateiformate](converting-file-formats-pdf.md#adding-support-for-additional-native-file-formats).

>[!NOTE]
>
Weitere Informationen zum Generate PDF-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So konvertieren Sie ein Microsoft Word-Dokument in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Generate PDF-Client.
1. Rufen Sie die in ein PDF-Dokument zu konvertierende Datei ab.
1. Konvertieren Sie die Datei in ein PDF-Dokument.
1. Rufen Sie die Ergebnisse ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Generate PDF-Clients**

Bevor Sie programmgesteuert einen Vorgang „Generate PDF“ durchführen können, müssen Sie einen Generate PDF-Service-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `GeneratePdfServiceClient`-Objekt. Wenn Sie die Web-Service-API verwenden, erstellen Sie ein `GeneratePDFServiceService`-Objekt.

**Rufen Sie die in ein PDF-Dokument zu konvertierende Datei ab.**

Rufen Sie das in ein PDF-Dokument zu konvertierende Microsoft Word-Dokument ab.

**Konvertieren der Datei in ein PDF-Dokument**

Nachdem Sie den Generate PDF-Service-Client erstellt haben, können Sie die `createPDF2`-Methode aufrufen. Diese Methode benötigt Informationen über das zu konvertierende Dokument, einschließlich der Dateierweiterung.

**Abrufen der Ergebnisse**

Nachdem die Datei in ein PDF-Dokument konvertiert worden ist, können Sie die Ergebnisse abrufen. Nachdem Sie beispielsweise eine Word-Datei in ein PDF-Dokument konvertiert haben, können Sie das PDF-Dokument abrufen und speichern.

**Siehe auch**

[Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Java-API](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-java-api)

[Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Web-Service-API](converting-file-formats-pdf.md#convert-word-documents-to-pdf-documents-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generieren der PDF-Service-API – Schnellstarts](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Java-API {#convert-word-documents-to-pdf-documents-using-the-java-api}

Konvertieren Sie ein Microsoft Word-Dokument mithilfe der Generate PDF- API (Java) in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-generatepdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Generate PDF-Client.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `GeneratePdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie die in ein PDF-Dokument zu konvertierende Datei ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das die zu konvertierende Word-Datei repräsentiert, mithilfe seines Konstruktors. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Konvertieren Sie die Datei in ein PDF-Dokument.

   Konvertieren Sie die Datei in ein PDF-Dokument, indem Sie die `GeneratePdfServiceClient` -Objekt `createPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, das die zu konvertierende Datei darstellt.
   * Ein `java.lang.String`-Objekt, das die Dateierweiterung enthält.
   * Ein `java.lang.String`-Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen. Dateitypeinstellungen ermöglichen Konvertierungseinstellungen für verschiedene Dateitypen, wie etwa .doc oder .xls.
   * Ein `java.lang.String`-Objekt, das den Namen der zu verwendenden PDF-Einstellungen enthält. Beispielsweise können Sie `Standard` angeben.
   * Ein `java.lang.String`-Objekt, das den Namen der zu verwendenden Sicherheitseinstellungen enthält.
   * Ein optionales `com.adobe.idp.Document`-Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.
   * Ein optionales `com.adobe.idp.Document`-Objekt, das Metadaten enthält, die für das PDF-Dokument übernommen werden sollen.

   Die `createPDF2`-Methode gibt ein `CreatePDFResult`-Objekt zurück, das das neue PDF-Dokument und Protokollinformationen enthält. Die Protokolldatei enthält in der Regel Fehler- oder Warnmeldungen, die durch die Konvertierungsanfrage generiert wurden.

1. Rufen Sie die Ergebnisse ab.

   So erhalten Sie das PDF-Dokument:

   * Rufen Sie die `CreatePDFResult` -Objekt `getCreatedDocument` -Methode, die eine `com.adobe.idp.Document` -Objekt.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument aus dem im vorherigen Schritt erstellten Objekt zu extrahieren.

   Wenn Sie die `createPDF2`-Methode zum Abrufen des Protokolldokuments (nicht anwendbar auf HTML-Konvertierungen), führen Sie die folgenden Schritte aus:

   * Rufen Sie die `CreatePDFResult` -Objekt `getLogDocument` -Methode. Dadurch wird ein `com.adobe.idp.Document`-Objekt zurückgegeben.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das Protokolldokument zu extrahieren.

**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren eines Microsoft Word-Dokuments in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-a-microsoft-word-document-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von Word-Dokumenten in PDF-Dokumente mithilfe der Web-Service-API {#convert-word-documents-to-pdf-documents-using-the-web-service-api}

So konvertieren Sie ein Microsoft Word-Dokument mithilfe der Generate PDF-API (Web-Service) in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Generate PDF-Client.

   * Erstellen Sie ein `GeneratePDFServiceClient`-Objekt unter Verwendung seines standardmäßigen Konstruktors.
   * Erstellen Sie ein `GeneratePDFServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `GeneratePDFServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `GeneratePDFServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `GeneratePDFServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` dem Feld `BasicHttpBindingSecurity.Security.Mode` zu.

1. Rufen Sie die in ein PDF-Dokument zu konvertierende Datei ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um die Datei zu speichern, die Sie in ein PDF-Dokument konvertieren möchten.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort der zu konvertierenden Datei und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Befüllen Sie das `BLOB`-Objekt, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Konvertieren Sie die Datei in ein PDF-Dokument.

   Konvertieren Sie die Datei in ein PDF-Dokument, indem Sie die `GeneratePDFServiceService` -Objekt `CreatePDF2` -Methode verwenden und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, das die zu konvertierende Datei darstellt.
   * Eine Zeichenfolge, die die Dateierweiterung enthält.
   * Ein `java.lang.String`-Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen. Dateitypeinstellungen ermöglichen Konvertierungseinstellungen für verschiedene Dateitypen, wie etwa .doc oder .xls.
   * Ein Zeichenfolgenobjekt, das die zu verwendenden PDF-Einstellungen enthält. Sie können Folgendes angeben `Standard`.
   * Ein Zeichenfolgenobjekt, das die zu verwendenden Sicherheitseinstellungen enthält. Sie können Folgendes angeben `No Security`.
   * Ein optionales `BLOB`-Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.
   * Ein optionales `BLOB`-Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen.
   * Einen Ausgabeparameter vom Typ `BLOB`, der durch die `CreatePDF2`-Methode befüllt wird. Die `CreatePDF2`-Methode befüllt dieses Objekt mit dem konvertierten Dokument. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).
   * Einen Ausgabeparameter vom Typ `BLOB`, der durch die `CreatePDF2`-Methode befüllt wird. Die `CreatePDF2`-Methode befüllt dieses Objekt mit dem Protokolldokument. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).

1. Rufen Sie die Ergebnisse ab.

   * Abrufen des konvertierten PDF-Dokuments durch Zuweisen der `BLOB` -Objekt `MTOM` in ein Byte-Array. Das Byte-Array stellt das konvertierte PDF-Dokument dar. Stellen Sie sicher, dass Sie das `BLOB`-Objekt verwenden, das als Ausgabeparameter für die `createPDF2`-Methode dient.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des konvertierten PDF-Dokuments darstellt.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor abrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von HTML-Dokumenten in PDF-Dokumente {#converting-html-documents-to-pdf-documents}

In diesem Abschnitt wird beschrieben, wie Sie mit Generate PDF-API HTML-Dokumente programmgesteuert in PDF-Dokumente konvertieren können.

>[!NOTE]
>
Weitere Informationen zum Generate PDF-Dienst finden Sie in der [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Führen Sie die folgenden Schritte aus, um ein HTML-Dokument in ein PDF-Dokument zu konvertieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Generate PDF-Client.
1. Rufen Sie den HTML-Inhalt ab, der in ein PDF-Dokument konvertiert werden soll.
1. Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument.
1. Rufen Sie die Ergebnisse ab.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Generate PDF Client**

Bevor Sie programmgesteuert einen Generate PDF-Vorgang durchführen können, müssen Sie einen Generate PDF-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `GeneratePdfServiceClient`-Objekt. Wenn Sie die Webdienst-API verwenden, erstellen Sie einen `GeneratePDFServiceService`.

**Abrufen des HTML-Inhalts zum Konvertieren in ein PDF-Dokument**

Verweisen Sie auf HTML-Inhalte, die Sie in ein PDF-Dokument konvertieren möchten. Sie können auf HTML-Inhalte wie eine HTML-Datei oder HTML-Inhalte verweisen, die über eine URL zugänglich sind.

**Konvertieren des HTML-Inhalts in ein PDF-Dokument**

Nachdem Sie den Dienst-Client erstellt haben, können Sie den entsprechenden PDF-Erstellungsvorgang aufrufen. Dieser Vorgang benötigt Informationen über das zu konvertierende Dokument, einschließlich des Pfads zum Zieldokument.

**Ergebnisse abrufen**

Nachdem der HTML-Inhalt in ein PDF-Dokument konvertiert wurde, können Sie die Ergebnisse abrufen und das PDF-Dokument speichern.

**Siehe auch**

[Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-java-api)

[Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Webdienst-API](converting-file-formats-pdf.md#convert-html-content-to-a-pdf-document-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generate PDF Service-API Schnellstarts](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API {#convert-html-content-to-a-pdf-document-using-the-java-api}

Konvertieren Sie ein HTML-Dokument mithilfe der Generate PDF-API (Java) in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-generatepdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Generate PDF-Client.

   Erstellen Sie ein `GeneratePdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie den HTML-Inhalt ab, der in ein PDF-Dokument konvertiert werden soll.

   Rufen Sie HTML-Inhalte ab, indem Sie eine Zeichenfolgenvariable erstellen und eine URL zuweisen, die auf HTML-Inhalte verweist.

1. Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument.

   Rufen Sie die `GeneratePdfServiceClient` -Objekt `htmlToPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * Ein `java.lang.String`-Objekt, das die URL der zu konvertierenden HTML-Datei enthält.
   * Ein `java.lang.String`-Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen. Dateitypeinstellungen können Spider-Level enthalten.
   * Ein `java.lang.String`-Objekt, das den Namen der zu verwendenden Sicherheitseinstellungen enthält.
   * Ein optionales `com.adobe.idp.Document`-Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen. Wenn diese Informationen nicht angegeben werden, werden die Einstellungen automatisch anhand der drei vorangehenden Parameter ausgewählt.
   * Ein optionales `com.adobe.idp.Document`-Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen.

1. Rufen Sie die Ergebnisse ab.

   Die `htmlToPDF2`-Methode gibt ein `HtmlToPdfResult`-Objekt zurück, das das neue generierte PDF-Dokument enthält. Führen Sie die folgenden Schritte aus, um das neu erstellte PDF-Dokument abzurufen:

   * Rufen Sie die `HtmlToPdfResult` -Objekt `getCreatedDocument` -Methode. Dadurch wird ein `com.adobe.idp.Document`-Objekt zurückgegeben.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das PDF-Dokument aus dem im vorherigen Schritt erstellten Objekt zu extrahieren.

**Siehe auch**

[Konvertieren von HTML-Dokumenten in PDF-Dokumente](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[Schnellstart (SOAP-Modus): Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Schnellstart (SOAP-Modus): Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Webdienst-API {#convert-html-content-to-a-pdf-document-using-the-web-service-api}

So konvertieren Sie HTML-Inhalte mithilfe der Generate PDF-API (Webservice) in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Generate PDF-Client.

   * Erstellen Sie ein `GeneratePDFServiceClient`-Objekt unter Verwendung seines standardmäßigen Konstruktors.
   * Erstellen Sie ein `GeneratePDFServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `GeneratePDFServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `GeneratePDFServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `GeneratePDFServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie den HTML-Inhalt ab, der in ein PDF-Dokument konvertiert werden soll.

   Rufen Sie HTML-Inhalte ab, indem Sie eine Zeichenfolgenvariable erstellen und eine URL zuweisen, die auf HTML-Inhalte verweist.

1. Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument.

   Konvertieren Sie den HTML-Inhalt in ein PDF-Dokument, indem Sie die `GeneratePDFServiceService` -Objekt `HtmlToPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * Eine Zeichenfolge, die den zu konvertierenden HTML-Inhalt enthält.
   * Ein `java.lang.String`-Objekt, das die Dateitypeinstellungen enthält, die bei der Konvertierung verwendet werden sollen.
   * Ein Zeichenfolgenobjekt, das die zu verwendenden Sicherheitseinstellungen enthält.
   * Ein optionales `BLOB`-Objekt, das Einstellungen enthält, die beim Erzeugen des PDF-Dokuments angewendet werden sollen.
   * Ein optionales `BLOB`-Objekt, das Metadateninformationen enthält, die auf das PDF-Dokument angewendet werden sollen.
   * Einen Ausgabeparameter vom Typ `BLOB`, der durch die `CreatePDF2`-Methode befüllt wird. Die `CreatePDF2`-Methode befüllt dieses Objekt mit dem konvertierten Dokument. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).

1. Rufen Sie die Ergebnisse ab.

   * Abrufen des konvertierten PDF-Dokuments durch Zuweisen der `BLOB` -Objekt `MTOM` in ein Byte-Array. Das Byte-Array stellt das konvertierte PDF-Dokument dar. Stellen Sie sicher, dass Sie das `BLOB`-Objekt verwenden, das als Ausgabeparameter für die `HtmlToPDF2`-Methode dient.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt durch Aufrufen des Konstruktors und Übergeben eines Zeichenfolgenwerts, der den Dateispeicherort des konvertierten PDF-Dokuments darstellt.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor abrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Konvertieren von HTML-Dokumenten in PDF-Dokumente](converting-file-formats-pdf.md#converting-html-documents-to-pdf-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Konvertieren von PDF-Dokumenten in Nicht-Bildformate {#converting-pdf-documents-to-non-image-formats}

In diesem Abschnitt wird beschrieben, wie Sie mit der Generate PDF-Java-API und der Webservice-API ein PDF-Dokument programmgesteuert in eine RTF-Datei konvertieren können. Dies ist ein Beispiel für ein Nicht-Bildformat. Andere Nicht-Bildformate sind HTML, Text, DOC und EPS. Stellen Sie beim Konvertieren eines PDF-Dokuments in RTF sicher, dass das PDF-Dokument keine Formularelemente wie eine Senden-Schaltfläche enthält. Formularelemente werden nicht konvertiert.

>[!NOTE]
>
Weitere Informationen zum Generate PDF-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Führen Sie die folgenden Schritte aus, um ein PDF-Dokument in einen der unterstützten Typen zu konvertieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen Generate PDF-Client.
1. Rufen Sie das zu konvertierende PDF-Dokument ab.
1. Konvertieren Sie das PDF-Dokument.
1. Speichern Sie die konvertierte Datei.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Generate PDF Client**

Bevor Sie programmgesteuert einen Generate PDF-Vorgang durchführen können, müssen Sie einen Generate PDF-Dienstclient erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `GeneratePdfServiceClient`-Objekt. Wenn Sie die Webservice-API verwenden, erstellen Sie ein `GeneratePDFServiceService`-Objekt.

**Abrufen des zu konvertierenden PDF-Dokuments**

Rufen Sie das PDF-Dokument ab, das in ein Nicht-Bildformat konvertiert werden soll.

**Konvertieren des PDF-Dokuments**

Nachdem Sie den Service-Client erstellt haben, können Sie den PDF-Exportvorgang aufrufen. Dieser Vorgang benötigt Informationen über das zu konvertierende Dokument, einschließlich des Pfads zum Zieldokument.

**Speichern der konvertierten Datei**

Speichern Sie die konvertierte Datei. Wenn Sie beispielsweise ein PDF-Dokument in eine RTF-Datei konvertieren, speichern Sie das konvertierte Dokument in eine RTF-Datei.

**Siehe auch**

[Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Java-API](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-java-api)

[Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Webservice-API](converting-file-formats-pdf.md#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Generate PDF Service-API Schnellstarts](/help/forms/developing/generate-pdf-service-java-api.md#generate-pdf-service-java-api-quick-start-soap)

### Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Java-API {#convert-a-pdf-document-to-a-rtf-file-using-the-java-api}

So konvertieren Sie ein PDF-Dokument mithilfe der Generate PDF-API (Java) in eine RTF-Datei:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-generatepdf-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Generate PDF-Client.

   Erstellen Sie ein `GeneratePdfServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das zu konvertierende PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Konvertieren Sie das PDF-Dokument.

   Rufen Sie die `GeneratePdfServiceClient` -Objekt `exportPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * Ein `com.adobe.idp.Document`-Objekt, das die zu konvertierende PDF-Datei darstellt.
   * Ein `java.lang.String`-Objekt, das den Namen der zu konvertierenden Datei enthält.
   * Ein `java.lang.String`-Objekt, das den Namen der Adobe PDF-Einstellungen enthält.
   * Ein `ConvertPDFFormatType`-Objekt, das den Zieldateityp für die Konvertierung angibt.
   * Ein optionales `com.adobe.idp.Document`-Objekt, das Einstellungen enthält, die beim Erzeugen des PDF-Dokuments angewendet werden sollen.

   Die Methode `exportPDF2` gibt ein `ExportPDFResult`-Objekt zurück, das die konvertierte Datei enthält.

1. Konvertieren Sie das PDF-Dokument.

   Um die neu erstellte Datei abzurufen, führen Sie die folgenden Schritte aus:

   * Rufen Sie die `ExportPDFResult` -Objekt `getConvertedDocument` -Methode. Dadurch wird ein `com.adobe.idp.Document`-Objekt zurückgegeben.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode, um das neue Dokument zu extrahieren.

**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Konvertieren von HTML-Inhalten in ein PDF-Dokument mithilfe der Java-API](/help/forms/developing/generate-pdf-service-java-api.md#quick-start-soap-mode-converting-html-content-to-a-pdf-document-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Konvertieren eines PDF-Dokuments in eine RTF-Datei mithilfe der Webservice-API {#convert-a-pdf-document-to-a-rtf-file-using-the-web-service-api}

Konvertieren Sie ein PDF-Dokument mithilfe der Generate PDF API (Webservice) in eine RTF-Datei:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/GeneratePDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Generate PDF-Client.

   * Erstellen Sie ein `GeneratePDFServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `GeneratePDFServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/GeneratePDFService?blob=mtom`). Sie brauchen das Attribut `lc_version` nicht zu verwenden. Geben Sie jedoch `?blob=mtom` an.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Feldes `GeneratePDFServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `GeneratePDFServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `GeneratePDFServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie das zu konvertierende PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines konvertierten PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das Objekt `BLOB`, indem Sie seiner `MTOM`-Eigenschaft den Inhalt des Byte-Arrays zuweisen.

1. Konvertieren Sie das PDF-Dokument.

   Rufen Sie die `GeneratePDFServiceServiceWse` -Objekt `ExportPDF2` -Methode verwenden und die folgenden Werte übergeben:

   * Ein `BLOB`-Objekt, das die zu konvertierende PDF-Datei repräsentiert.
   * Eine Zeichenfolge, die den Pfadnamen der zu konvertierenden Datei enthält.
   * Ein `java.lang.String`-Objekt, das den Dateispeicherort angibt.
   * Ein Zeichenfolgenobjekt, das für die Konvertierung den Typ der Zieldatei angibt. Geben Sie `RTF`.
   * Ein optionales `BLOB`-Objekt, das Einstellungen enthält, die beim Generieren des PDF-Dokuments angewendet werden sollen.
   * Einen Ausgabeparameter vom Typ `BLOB`, der durch die `ExportPDF2`-Methode befüllt wird. Die `ExportPDF2`-Methode befüllt dieses Objekt mit dem konvertierten Dokument. (Dieser Parameterwert ist nur für den Webservice-Aufruf erforderlich).

1. Speichern Sie die konvertierte Datei.

   * Rufen Sie das konvertierte RTF-Dokument ab, indem Sie die `BLOB` -Objekt `MTOM` in ein Byte-Array. Das Byte-Array repräsentiert das konvertierte RTF-Dokument. Stellen Sie sicher, dass Sie das `BLOB`-Objekt verwenden, das bei der `ExportPDF2`-Methode als Ausgabeparameter dient.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen Zeichenfolgewert, der den Speicherort der RTF-Datei repräsentiert.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine RTF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](converting-file-formats-pdf.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erweitern der Unterstützung auf weitere native Dateiformate {#adding-support-for-additional-native-file-formats}

In diesem Abschnitt wird erläutert, wie Sie für weitere native Dateiformate eine Unterstützung hinzufügen. Dargeboten wird ein Überblick über die Interaktionen zwischen dem Generate PDF-Service und den nativen Programmen, die dieser Service zum Konvertieren nativer Dateiformate in PDF verwendet.

Außerdem wird in diesem Abschnitt Folgendes erläutert:

* die Vorgehensweise beim Ändern der Antwort, die der Generate PDF-Service den nativen Programmen bereitstellt, die dieses Produkt bereits verwendet, um native Dateiformate in PDF zu konvertieren
* die Interaktionen zwischen dem Generate PDF-Service, der Programmüberwachungs- (AppMon)-Komponente des Generate PDF-Service und nativen Programmen wie Microsoft Word
* die Rollen, die XML-Grammatiken bei diesen Interaktionen spielen

### Interaktionen von Komponenten {#component-interactions}

Der Generate PDF-Dienst konvertiert native Dateiformate, indem er das mit dem Dateiformat verknüpfte Programm aufruft und dann mit dem Programm interagiert, um das Dokument unter Verwendung des Standarddruckers zu drucken. Der Standarddrucker muss als Adobe PDF Printer eingerichtet sein.

Diese Abbildung zeigt die Komponenten und Treiber, die an der Unterstützung nativer Programme beteiligt sind. Außerdem sind die XML-Grammatiken vermerkt, die Einfluss auf die Interaktionen haben.

Komponenteninteraktionen bei der Konvertierung nativer Dateien

In diesem Dokument wird der Ausdruck *natives Programm* verwendet, um das Programm anzugeben, das zum Erzeugen eines nativen Dateiformats verwendet wird, wie beispielsweise Microsoft Word.

*AppMon* ist eine für Unternehmen konzipierte Komponente, die mit einem nativen Programm auf dieselbe Weise interagiert, wie ein Benutzer durch die von diesem Programm präsentierten Dialogfelder navigieren würde. Die XML-Grammatiken, die von AppMon verwendet werden, um ein Programm wie Microsoft Word anzuweisen, eine Datei zu öffnen und zu drucken, umfassen die folgenden nacheinander auszuführenden Aufgaben:

1. Öffnen der Datei durch Auswählen von „Datei“ und „Öffnen“
1. Sicherstellen, dass das Dialogfeld „Öffnen“ angezeigt wird; geschieht dies nicht, erfolgt eine Fehlerbehandlung
1. Eingeben des Dateinamens im Feld „Dateiname“ und anschließendes Klicken auf die Schaltfläche „Öffnen“.
1. Sicherstellen, dass die Datei tatsächlich geöffnet wird
1. Öffnen des Dialogfeldes „Drucken“ durch Auswählen von „Datei“ und „Drucken“
1. Sicherstellen, dass das Dialogfeld „Drucken“ angezeigt wird

AppMon verwendet standardmäßige Win32-APIs, um mit Drittanbieteranwendungen zu interagieren und Benutzeroberflächenereignisse wie Tastenanschläge und Mausklicks zu übertragen. Dies ist nützlich, um diese Anwendungen zur Erstellung von PDF-Dateien zu steuern.

Aufgrund einer Einschränkung bei diesen Win32-APIs kann AppMon diese Benutzeroberflächenereignisse nicht an bestimmte Arten von Fenstern, wie z. B. unverankerte Menüleisten (in einigen Programmen, wie beispielsweise TextPad, enthalten) und bestimmte Arten von Dialogfeldern, deren Inhalt nicht mithilfe der Win32-APIs abgerufen werden kann, senden.

Eine unverankerte Menüleiste lässt sich leicht visuell erkennen. Gegebenenfalls ist es jedoch nicht möglich, die speziellen Dialogfeldtypen allein durch visuelle Überprüfung zu identifizieren. Sie würden ein Drittanbieterprogramm wie Microsoft Spy++ (Teil der Microsoft Visual C++-Entwicklungsumgebung) oder das äquivalente WinID (das kostenlos von [https://www.dennisbabkin.com/php/download.php?what=WinID](https://www.dennisbabkin.com/php/download.php?what=WinID) heruntergeladen werden kann) benötigen, um ein Dialogfeld darauf zu prüfen, ob AppMon unter Verwendung von Standard-Win32-APIs damit interagieren könnte.

Wenn WinID in der Lage ist, Dialogfeldinhalte wie Text, Unterfenster, Fensterklassen-ID usw. zu extrahieren, dann kann AppMon dies ebenfalls tun.

In dieser Tabelle sind die Informationstypen aufgeführt, die beim Drucken nativer Dateiformate verwendet werden.

<table>
 <thead>
  <tr>
   <th><p>Informationstyp</p></th>
   <th><p>Beschreibung</p></th>
   <th><p>Ändern/Erstellen von Einträgen für native Dateien </p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Administrative Einstellungen </p></td>
   <td><p>Enthält PDF-Einstellungen, Sicherheitseinstellungen und Dateitypeinstellungen. </p><p>Dateitypeinstellungen verknüpfen Dateinamenerweiterungen mit den entsprechenden nativen Programmen. Außerdem geben Dateitypeinstellungen Einstellungen für native Programme an, die zum Drucken nativer Dateien verwendet werden. </p></td>
   <td><p>Um Einstellungen für eine bereits unterstützte native Anwendung zu ändern, legt der Systemadministrator die „Dateitypeinstellungen“ in der Administration-Console fest. </p><p>Um die Unterstützung bei einem neuen nativen Dateiformat hinzuzufügen, müssen Sie die Datei manuell bearbeiten. (Siehe <a href="converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format">Hinzufügen oder Ändern der Unterstützung bei einem nativen Dateiformat</a>.) </p></td>
  </tr>
  <tr>
   <td><p>Script </p></td>
   <td><p>Gibt Interaktionen zwischen dem Generate PDF-Service und einem nativen Programm an. Durch diese Interaktionen wird normalerweise das Programm zum Drucken einer Datei an den Adobe PDF-Treiber weitergeleitet. </p><p>Das Skript enthält Anweisungen, die das native Programm anweisen, bestimmte Dialogfelder zu öffnen, und die bestimmte Antworten auf Felder und Schaltflächen in diesen Dialogfeldern bereitstellen. </p></td>
   <td><p>Der Generate PDF-Service schließt Skriptdateien für alle unterstützten nativen Programme ein. Diese Dateien lassen sich mithilfe eines Programms zur Bearbeitung von XML modifizieren.</p><p>Um Unterstützung für eine neue native Anwendung hinzuzufügen, müssen Sie eine Skriptdatei erstellen. (Siehe <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Erstellen oder Modifizieren einer zusätzlichen XML-Dialogfelddatei für ein natives Programm</a>.) </p></td>
  </tr>
  <tr>
   <td><p>Allgemeine Dialogfeldanweisungen </p></td>
   <td><p>Geben an, wie auf Dialogfelder reagiert werden soll, die für mehrere Programme verwendet werden. Solche Dialogfelder werden von Betriebssystemen, Hilfsprogrammen (wie PDFMaker) und Treibern generiert. </p><p>Die Datei, die diese Informationen enthält, lautet appmon.global.en_US.xml.</p></td>
   <td><p>Diese Datei darf nicht geändert werden. </p></td>
  </tr>
  <tr>
   <td><p>Anwendungsspezifische Dialogfeldanweisungen</p></td>
   <td><p>Geben an, wie auf anwendungsspezifische Dialogfelder reagiert werden soll. </p><p>Die Datei, die diese Informationen enthält, heißt appmon.<i>`[appname]`</i>.dialog.<i>`[locale]`</i>.xml (zum Beispiel appmon.word.en_US.xml).</p></td>
   <td><p>Diese Datei darf nicht geändert werden. </p><p>Informationen dazu, wie Dialogfeldanweisungen bei einem neuen nativen Programm hinzuzufügen sind, finden Sie unter <a href="converting-file-formats-pdf.md#creating_or_modifying_an_additional_dialog_xml_file_for_a_native_application">Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei bei einem nativen Programm</a>.</p></td>
  </tr>
  <tr>
   <td><p>Zusätzliche anwendungsspezifische Dialogfeldanweisungen </p></td>
   <td><p>Geben Überschreibungen und Hinzufügungen zu anwendungsspezifischen Dialogfeldanweisungen an. Der Abschnitt enthält ein Beispiel für solche Informationen. </p><p>Die Datei, die diese Informationen enthält, ist „appmon“.<i>`[appname]`</i>.addition.<i>`[locale]`</i>.xml. Ein Beispiel ist „appmon.addition.de_DE.xml“.</p></td>
   <td><p>Dateien dieses Typs können mit einem Programm zur XML-Bearbeitung erstellt und geändert werden. (Siehe <a href="converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application">Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für ein natives Programm</a>.) </p><p><strong>Wichtig</strong>: Erstellen Sie zusätzliche anwendungsspezifische Dialogfeldanweisungen für jede native Anwendung, die Ihr Server unterstützt. </p></td>
  </tr>
 </tbody>
</table>

### Über XML-Dateien für Skripte und Dialogfelder {#about-the-script-and-dialog-xml-files}

Skript-XML-Dateien weisen den Generate PDF-Service an, durch die Dialogfelder des Programms so zu navigieren, wie ein Benutzer durch die Dialogfelder des Programms navigieren würde. Skript-XML-Dateien können den Generate PDF-Service außerdem anweisen, auf Dialogfelder zu reagieren, indem sie beispielsweise auf Schaltflächen klicken, Kontrollkästchen aktivieren oder deaktivieren oder Menüelemente auswählen.

Im Gegensatz dazu reagieren XML-Dialogfelddateien einfach auf Dialogfelder mit den gleichen Aktionstypen, die in XML-Skript-Dateien verwendet werden.

#### Terminologie von Dialogfeld- und Fensterelementen {#dialog-box-and-window-element-terminology}

In diesem und im nächsten Abschnitt wird je nach der beschriebenen Perspektive eine andere Terminologie für Dialogfelder und die darin enthaltenen Komponenten verwendet. Dialogfeldkomponenten sind Elemente wie Schaltflächen, Felder und Kombinationsfelder.

Dort, wo dieser und der nächste Abschnitt Dialogfelder und ihre Komponenten aus der Perspektive eines Benutzers beschreiben, werden Begriffe wie *Dialogfeld*, *Schaltfläche*, *Feld* und *Kombinationsfeld* verwendet.

Dort, wo dieser und der nächste Abschnitt Dialogfelder und ihre Komponenten aus der Perspektive ihrer internen Darstellung beschreiben, wird der Begriff *Fensterelement* verwendet. Die interne Darstellung von Fensterelementen ist eine Hierarchie, in der jede Fensterelementinstanz durch Beschriftungen identifiziert wird. Die Fensterelementinstanz beschreibt auch ihre physischen Merkmale und ihr Verhalten.

Aus Sicht eines Benutzers zeigen die Dialogfelder und ihre Komponenten unterschiedliche Verhaltensweisen an, bei denen einige Dialogfeldelemente ausgeblendet werden, bis sie aktiviert werden. Aus der Sicht der internen Darstellung gibt es kein solches Verhaltensproblem. Beispielsweise sieht die interne Darstellung eines Dialogfelds ähnlich aus wie die der darin enthaltenen Komponenten, abgesehen davon, dass die Komponenten innerhalb des Dialogfelds verschachtelt sind.

In diesem Abschnitt werden XML-Elemente beschrieben, die AppMon Anweisungen geben. Diese Elemente haben Namen wie das `dialog`-Element und das `window`-Element. In diesem Dokument wird zur Unterscheidung von XML-Elementen eine Schriftart mit fester Zeichenbreite verwendet. Das `dialog`-Element identifiziert ein Dialogfeld, das durch eine XML-Skriptdatei absichtlich oder unabsichtlich angezeigt werden kann. Das `window`-Element bezeichnet ein Fensterelement (Dialogfeld oder die Komponenten eines Dialogfelds).

#### Hierarchie {#hierarchy}

Dieses Diagramm zeigt die Hierarchie des Skript- und Dialog-XML. Eine XML-Skriptdatei entspricht dem Schema „script.xsd“, das (im Sinne von XML) das Schema „window.xsd“ enthält. Analog entspricht eine XML-Dialogfelddatei dem Schema „dialogs.xsd“, das ebenfalls das Schema „window.xsd“ enthält.

![as_as_xml_hierarchy](assets/as_as_xml_hierarchy.png)

Hierarchie des Skripts und Dialogfeld-XML

#### XML-Skriptdateien {#script-xml-files}

Eine *XML-Skriptdatei* gibt eine Reihe von Schritten an, die das native Programm anweisen, zu bestimmten Fensterelementen zu navigieren und dann Reaktionen auf diese Elemente bereitzustellen. Bei den meisten Reaktionen handelt es sich um Text oder Tastenanschläge, die den Eingaben entsprechen, die ein Benutzer in ein Feld, ein Kombinationsfeld oder eine Schaltfläche im entsprechenden Dialogfeld eingeben würde.

Der Generate PDF-Dienst unterstützt Skript-XML-Dateien, indem er eine native Anwendung anweist, eine native zu drucken. Skript-XML-Dateien können jedoch verwendet werden, um alle Aufgaben auszuführen, die ein Benutzer bei der Interaktion mit den Dialogfeldern der nativen Anwendung ausführen kann.

Die Schritte in einer XML-Skriptdatei werden der Reihe nach ausgeführt, ohne die Möglichkeit einer Verzweigung. Der einzige unterstützte bedingte Test ist die Zeitüberschreitung/Wiederholung, wodurch ein Skript beendet wird, wenn ein Schritt nicht innerhalb eines bestimmten Zeitraums und nach einer bestimmten Anzahl weiterer Versuche erfolgreich abgeschlossen wird.

Die Anweisungen in einem Schritt sind nicht nur sequenziell, sondern werden auch der Reihe nach ausgeführt. Stellen Sie sicher, dass die Schritte und Anweisungen die Reihenfolge widerspiegeln, in der ein Benutzer die gleichen Schritte durchführt.

Jeder Schritt in einer XML-Skript-Datei identifiziert das Fensterelement, das angezeigt werden soll, wenn die Anweisungen des Schritts erfolgreich ausgeführt wurden. Wird während der Ausführung eines Skriptschritts ein unerwartetes Dialogfeld angezeigt, durchsucht der Service „Generate PDF“ die XML-Dialogfelddateien, wie im nächsten Abschnitt beschrieben.

#### XML-Dialogfelddateien {#dialog-xml-files}

Während der Ausführung nativer Programme werden verschiedene Dialogfelder angezeigt, die unabhängig davon erscheinen, ob sich die nativen Programme in einem sichtbaren oder unsichtbaren Modus befinden. Die Dialogfelder können vom Betriebssystem oder vom Programm selbst erstellt werden. Wenn native Programme unter der Kontrolle des Service „Generate PDF“ ausgeführt werden, werden die Dialogfelder des Systems und des nativen Programms in einem unsichtbaren Fenster angezeigt.

Eine *XML-Dialogfelddatei* gibt an, wie der Service „Generate PDF“ auf die Dialogfelder des Systems oder des nativen Programms antwortet. Die XML-Dialogfelddateien ermöglichen es dem Service „Generate PDF“, so auf unaufgeforderte Dialogfelder zu reagieren, dass der Konvertierungsprozess erleichtert wird.

Wenn das System oder das native Programm ein Dialogfeld anzeigt, das nicht von der derzeit ausgeführten XML-Skriptdatei verarbeitet wird, durchsucht der Service „Generate PDF“ die XML-Dialogfelddateien in dieser Reihenfolge und stoppt, wenn er eine Übereinstimmung findet:

* appmon.`[appname]`.additional.`[locale]`.xml
* appmon.`[appname]`.`[locale]`.xml (Diese Datei darf nicht geändert werden.)
* appmon.global.`[locale]`.xml (Diese Datei darf nicht geändert werden.)

Wenn der Service „Generate PDF“ eine Übereinstimmung für das Dialogfeld findet, schließt er es, indem er ihm die für das Dialogfeld angegebene Tastenanschlag oder eine andere Aktion sendet. Wenn in den Anweisungen für das Dialogfeld eine Abbruchmeldung angegeben wird, beendet der Service „Generate PDF“ den derzeit ausgeführten Auftrag und erzeugt eine Fehlermeldung. Eine solche Abbruchmeldung würde im `abortMessage`-Element in der XML-Skriptgrammatik angegeben.

Wenn der Generate PDF-Dienst auf ein Dialogfeld stößt, das in keiner der oben aufgeführten Dateien beschrieben wird, fügt der Generate PDF-Dienst die Beschriftung des Dialogfelds in den Protokolldateieintrag ein. Der derzeit ausgeführte Auftrag wird schließlich mit einer Zeitüberschreitung beendet. Sie können dann die Informationen in der Protokolldatei verwenden, um neue Anweisungen in der zusätzlichen XML-Dialogfelddatei (additional) für das native Programm zu erstellen.

### Hinzufügen oder Ändern der Unterstützung für ein natives Dateiformat {#adding-or-modifying-support-for-a-native-file-format}

In diesem Abschnitt werden die Aufgaben beschrieben, die Sie ausführen müssen, um andere native Dateiformate zu unterstützen oder um die Unterstützung eines bereits unterstützten nativen Dateiformats zu ändern.

Bevor Sie Unterstützung hinzufügen oder ändern können, müssen Sie die folgenden Aufgaben ausführen.

#### Auswahl eines Tools zum Identifizieren von Fensterelementen {#choosing-a-tool-for-identifying-window-elements}

In den XML-Dateien für Dialogfelder und Skripte müssen Sie das Fensterelement (Dialogfeld, Feld oder andere Dialogfeldkomponente) identifizieren, auf das Ihr Dialogfeld oder Skriptelement reagiert. Wenn beispielsweise ein Skript ein Menü für ein natives Programm aufruft, muss das Skript das Fensterelement in diesem Menü identifizieren, auf das Tastatureingaben oder eine Aktion angewendet werden sollen.

Sie können ein Dialogfeld einfach anhand der Beschriftung identifizieren, die in der Titelleiste angezeigt wird. Sie müssen jedoch ein Tool wie Microsoft Spy++ verwenden, um Fensterelemente auf einer niedrigeren Ebene zu identifizieren. Die Fensterelemente einer niedrigeren Ebene können durch eine Vielzahl von Attributen identifiziert werden, die nicht offensichtlich sind. Außerdem kann es sein, dass jedes native Programm sein Fensterelement anders identifiziert. Daher gibt es mehrere Möglichkeiten, ein Fensterelement zu identifizieren. Im Folgenden finden Sie die empfohlene Reihenfolge, in der die Identifizierung von Fensterelementen erfolgen sollte:

1. Beschriftung selbst, sofern sie eindeutig ist
1. Kontroll-ID, die für ein bestimmtes Dialogfeld eindeutig sein kann, aber nicht muss
1. Klassenname, der eindeutig sein kann, aber nicht muss

Jedes dieser drei Attribute kann zur Identifizierung eines Fensters verwendet werden.

Wenn die Attribute eine Beschriftung nicht identifizieren können, können Sie stattdessen ein Fensterelement identifizieren, indem Sie dessen Index in Bezug auf dessen übergeordnetes Element verwenden. Ein *index* gibt die Position des Fensterelements relativ zu den gleichrangigen Fensterelementen an. Häufig sind Indizes die einzige Möglichkeit, Kombinationsfelder zu identifizieren.

Seien Sie sich dieser Dinge bewusst:

* Microsoft Spy++ zeigt Untertitel mit einem kaufmännischen Und-Zeichen (&amp;) an, um den Hotkey der Beschriftung zu identifizieren. Beispielsweise zeigt Spy++ die Beschriftung für ein Druckdialogfeld als `Pri&nt`, was anzeigt, dass der Hotkey *n* ist. Beschriftungstitel in XML-Dateien für Skripte und Dialogfelder dürfen keine kaufmännischen Und-Zeichen enthalten.
* Einige Beschriftungen enthalten Zeilenumbrüche. Der Generate PDF-Service kann jedoch Zeilenumbrüche nicht identifizieren. Wenn eine Beschriftung einen Zeilenumbruch enthält, fügen Sie genug von der Beschriftung ein, um sie von den anderen Menüpunkten zu unterscheiden, und verwenden Sie dann reguläre Ausdrücke für den ausgelassenen Teil. Ein Beispiel: `^Long caption title$`. (Siehe [Verwenden regulärer Ausdrücke in Beschriftungsattributen](converting-file-formats-pdf.md#using-regular-expressions-in-caption-attributes).)
* Verwenden Sie Zeichenentitäten (auch als Escape-Sequenzen bezeichnet) für reservierte XML-Zeichen. Verwenden Sie beispielsweise `&` für Ampersands, `<` und `>` für die Symbole „kleiner als“ und „größer als“, `&apos;` bei Apostrophen und `&quot;` für Anführungszeichen.

Wenn Sie mit Dialogfeld- oder Skript-XML-Dateien arbeiten möchten, sollten Sie das Programm Microsoft Spy++ installieren.

#### Dekomprimieren der Dialogfeld- und Skriptdateien {#unpackaging-the-dialog-and-script-files}

Die Dialogfeld- und Skriptdateien befinden sich in der Datei „appmondata.jar“. Bevor Sie eine dieser Dateien ändern oder neue Skript- oder Dialogfelddateien hinzufügen können, müssen Sie diese JAR-Datei entpacken. Angenommen, Sie möchten Unterstützung für das Programm EditPlus hinzufügen. Sie erstellen zwei XML-Dateien mit den Namen „appmon.editplus.script.de_DE.xml“ und „appmon.editplus.script.additional.de_DE.xml“. Diese XML-Skripte müssen zur Datei „adobe-appmondata.jar“ an zwei Stellen hinzugefügt werden, wie unten angegeben:

* adobe-livecycle-native-jboss-x86_win32.ear > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar\com\adobe\appmon. Die Datei „adobe-livecycle-native-jboss-x86_win32.ear“ befindet sich im Exportordner unter `[AEM forms install directory]\configurationManager`. (Wenn AEM Forms auf einem anderen J2EE-Programm-Server bereitgestellt wird, ersetzen Sie die Datei „adobe-livecycle-native-jboss-x86_win32.ear“ durch die EAR-Datei, die Ihrem J2EE-Programm-Server entspricht.)
* adobe-generatepdf-dsc.jar > adobe-appmondata.jar\com\adobe\appmon (die Datei „adobe-appmondata.jar“ befindet sich in der Datei „adobe-generatepdf-dsc.jar“). Die Datei „adobe-generatepdf-dsc.jar“ befindet sich im Ordner `[AEM forms install directory]\deploy`.

Nachdem Sie diese XML-Dateien zur Datei „adobe-appmondata.jar“ hinzugefügt haben, müssen Sie die GeneratePDF-Komponente erneut bereitstellen. Führen Sie die folgenden Aufgaben aus, um Dialogfeld- und Skript-XML-Dateien zur Datei „adobe-appmondata.jar“ hinzuzufügen:

1. Öffnen Sie mit einem Tool wie WinZip oder WinRAR die Datei adobe-livecycle-native-jboss-x86_win32.earfile > adobe-Native2PDFSvc.war\WEB-INF\lib > adobe-native.jar > Native2PDFSvc-native.jar\bin > adobe-appmondata.jar.
1. Fügen Sie die Dialogfeld- und Skript-XML-Dateien zur Datei „appmondata.jar“ hinzu oder ändern Sie bestehende XML-Dateien in dieser Datei. (Siehe [Erstellen oder Ändern einer XML-Skript-Datei für ein natives Programm](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application) und [Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für ein natives Programm](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).)
1. Öffnen Sie mit einem Tool wie WinZip oder WinRAR die Datei adobe-generatepdf-dsc.jar > adobe-appmondata.jar.
1. Fügen Sie die Dialogfeld- und Skript-XML-Dateien zur Datei „appmondata.jar“ hinzu oder ändern Sie bestehende XML-Dateien in dieser Datei. (Siehe [Erstellen oder Ändern einer XML-Skript-Datei für ein natives Programm](converting-file-formats-pdf.md#creating-or-modifying-a-script-xml-file-for-a-native-application) und [Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für ein natives Programm](converting-file-formats-pdf.md#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application).) Nachdem Sie die XML-Dateien zur Datei „adobe-appmondata.jar“ hinzugefügt haben, platzieren Sie die neue Datei „adobe-appmondata.jar“ in die Datei „adobe-generatepdf-dsc.jar“.
1. Wenn Sie Unterstützung für ein zusätzliches natives Dateiformat hinzugefügt haben, erstellen Sie eine Systemumgebungsvariable, die den Pfad des Programms bereitstellt (siehe [Erstellen einer Umgebungsvariable zum Suchen des nativen Programms](converting-file-formats-pdf.md#creating-an-environment-variable-to-locate-the-native-application)).

**So stellen Sie die GeneratePDF-Komponente erneut bereit**

1. Melden Sie sich bei Workbench an.
1. Wählen Sie **Fenster** > **Ansicht anzeigen** > **Komponenten**. Durch diese Aktion wird die Ansicht „Komponenten“ zu Workbench hinzugefügt.
1. Klicken Sie mit der rechten Maustaste auf die GeneratePDF-Komponente und wählen Sie **Komponente stoppen**.
1. Wenn die Komponente angehalten worden ist, klicken Sie mit der rechten Maustaste und wählen Sie „Komponente deinstallieren“, um sie zu entfernen.
1. Klicken Sie mit der rechten Maustaste auf das Symbol **Komponenten** und wählen Sie **Komponente installieren**.
1. Suchen Sie die geänderte Datei „adobe-generatepdf-dsc.jar“ und wählen Sie sie aus. Klicken Sie dann auf „Öffnen“. Beachten Sie, dass neben der GeneratePDF-Komponente ein rotes Quadrat angezeigt wird.
1. Erweitern Sie die GeneratePDF-Komponente, wählen Sie „Service-Deskriptoren“ aus, klicken Sie dann mit der rechten Maustaste auf „GeneratePDFService“ und wählen Sie „Service aktivieren“.
1. Geben Sie im angezeigten Konfigurationsdialogfeld die entsprechenden Konfigurationswerte ein. Wenn Sie diese Werte leer lassen, werden die Standardkonfigurationswerte verwendet.
1. Klicken Sie mit der rechten Maustaste auf GeneratePDF und wählen Sie „Komponente starten“.
1. Erweitern Sie „Aktive Services“. Neben dem Namen eines Services erscheint ein grüner Pfeil, wenn er ausgeführt wird. Andernfalls befindet sich der Service im Status „Angehalten“.
1. Wenn der Service angehalten ist, klicken Sie mit der rechten Maustaste auf den Namen des Services und wählen Sie „Service starten“.

### Erstellen oder Ändern einer XML-Skript-Datei für ein natives Programm {#creating-or-modifying-a-script-xml-file-for-a-native-application}

Wenn Sie Dateien an ein neues natives Programm weiterleiten möchten, müssen Sie eine XML-Skript-Datei für dieses Programm erstellen. Wenn Sie ändern möchten, wie der Generate PDF-Service mit einem bereits unterstützten nativen Programm interagiert, müssen Sie das Skript für dieses Programm ändern.

Das Skript enthält Anweisungen, die durch die Fensterelemente der nativen Anwendung navigieren und spezifische Antworten auf diese Elemente bereitstellen. Die Datei, die diese Informationen enthält, lautet `appmon.`[appname]`` `.script.`[locale]`.xml`. Ein Beispiel ist „appmon.notepad.script.de_DE.xml“.

#### Identifizieren der Schritte, die das Skript ausführen muss {#identifying-steps-the-script-must-execute}

Ermitteln Sie mithilfe des nativen Programms die Fensterelemente, durch die Sie navigieren müssen, und jede Antwort, die Sie zum Drucken des Dokuments ausführen müssen. Notieren Sie sich die Dialogfelder, die aus einer Antwort resultieren. Die Schritte ähneln den folgenden Schritten:

1. Wählen Sie „Datei“ > „Öffnen“.
1. Geben Sie den Pfad an und klicken Sie auf „Öffnen“.
1. Wählen Sie in der Menüleiste „Datei“ > „Drucken“ aus.
1. Geben Sie die für den Drucker erforderlichen Eigenschaften an.
1. Wählen Sie „Drucken“ aus und warten Sie, bis das Dialogfeld „Speichern unter“ angezeigt wird. Das Dialogfeld „Speichern unter“ ist erforderlich, damit der Generate PDF-Service das Ziel für die PDF-Datei angeben kann.

#### Identifizieren der in Beschriftungsattributen angegebenen Dialogfelder {#identifying-the-dialogs-specified-in-caption-attributes}

Verwenden Sie Microsoft Spy++, um die Identitäten der Fensterelementeigenschaften im nativen Programm abzurufen. Sie müssen über diese Identitäten verfügen, um Skripte zu schreiben.

#### Verwenden regulärer Ausdrücke in Beschriftungsattributen {#using-regular-expressions-in-caption-attributes}

Sie können reguläre Ausdrücke in Beschriftungsspezifikationen verwenden. Der Generate PDF-Service verwendet die `java.util.regex.Matcher`-Klasse, um reguläre Ausdrücke zu unterstützen. Dieses Dienstprogramm unterstützt die regulären Ausdrücke, die unter `java.util.regex.Pattern` beschrieben werden.

**Regulärer Ausdruck, der den Dateinamen unterstützt, dem im Editor-Banner Notepad vorangestellt wird**

```xml
 <!-- The regular expression ".*Notepad" means any number of non-terminating characters followed by Notepad. -->
 <step>
     <expectedWindow>
         <window caption=".*Notepad"/>
     </expectedWindow>
 </step>
```

**Regulärer Ausdruck, der Druck von der Druckeinrichtung unterscheidet**

```xml
 <!-- This regular expression differentiates the Print dialog box from the Print Setup dialog box. The "^" specifies the beginning of the line, and the "$" specifies the end of the line. -->
 <windowList>
     <window controlID="0x01" caption="^Print$" action="press"/>
 </windowList>
```

#### Sortieren von window- und windowList-Elementen {#ordering-the-window-and-windowlist-elements}

Bestellung `window` und `windowList` -Elemente wie folgt:

* Wenn mehrere `window` -Elemente werden als untergeordnete Elemente in `windowList` oder `dialog` -Element, diese sortieren `window` -Elemente in absteigender Reihenfolge, mit den Längen der `caption` Namen, die die Position in der Reihenfolge angeben.
* Wenn mehrere `windowList`-Elemente in einem `window`-Element enthalten sind, sortieren Sie diese `windowList`-Elemente in absteigender Reihenfolge, wobei den Längen der `caption`-Attribute des ersten `indexes/`-Elements die Position in der Reihenfolge angeben.

**Sortieren von Fensterelementen in einer Dialogfelddatei**

```xml
 <!-- The caption attribute in the following window element is 40 characters long. It is the longest caption in this example, so its parent window element appears before the others. -->
 <window caption="Unexpected Failure in DebugActiveProcess">
     <…>
 </window>

 <!-- Caption length is 33 characters. -->
 <window caption="Adobe Acrobat - License Agreement">
     <…>
 </window>

 <!-- Caption length is 33 characters. -->
 <window caption="Microsoft Visual.*Runtime Library">
     <…>
 </window>

 <!-- The caption attribute in the following window element is 28 characters long. It is the shortest caption in this example, so its parent window element appears after the others. -->
 <window caption="Adobe Acrobat - Registration">
     <…>
 </window>
```

**Sortieren von Fensterelementen in einem windowList-Element**

```xml
 <!-- The caption attribute in the following indexes element is 56 characters long. It is the longest caption in this example, so its parent window element appears before the others. -->
 <windowList>
     <window caption="Can&apos;t exit design mode because.* cannot be created"/>
     <window className="Button" caption="OK" action="press"/>
 </windowList>
 <windowList>
     <window caption="Do you want to continue loading the project?"/>
     <window className="Button" caption="No" action="press"/>
 </windowList>
 <windowList>
     <window caption="The macros in this project are disabled"/>
     <window className="Button" caption="OK" action="press"/>
 </windowList>
```

### Erstellen oder Ändern einer zusätzlichen XML-Dialogfelddatei für ein natives Programm {#creating-or-modifying-an-additional-dialog-xml-file-for-a-native-application}

Wenn Sie ein Skript für ein natives Programm erstellen, das zuvor nicht unterstützt wurde, müssen Sie auch eine zusätzliche XML-Dialogfelddatei für dieses Programm erstellen. Jedes native Programm, das von AppMon verwendet wird, darf nur eine zusätzliche XML-Dialogfelddatei haben. Die zusätzliche XML-Dialogfelddatei ist auch dann erforderlich, wenn keine unangeforderten Dialogfelder erwartet werden. Das zusätzliche Dialogfeld muss mindestens ein `window`-Element enthalten, selbst wenn dieses `window`-Element lediglich ein Platzhalter ist.

>[!NOTE]
>
In diesem Zusammenhang steht der Begriff „zusätzlich“ für den Inhalt der `appmon.[applicationname].addition.[locale].xml`-Datei. Eine solche Datei gibt Überschreibungen und Ergänzungen der XML-Dialogfelddatei an.

Sie können für folgende Zwecke auch die zusätzliche XML-Dialogfelddatei für ein natives Programm ändern:

* So überschreiben Sie die XML-Datei des Dialogfelds für ein Programm mit einer anderen Antwort
* So fügen Sie eine Antwort zu einem Dialogfeld hinzu, das nicht in der XML-Dialogfelddatei für dieses Programm angesprochen wird

Der Dateiname, der eine zusätzliche dialogXML-Datei angibt, lautet `appmon.[appname].addition.[locale].xml`. Ein Beispiel ist „appmon.excel.additional.de_DE.xml“.

Der Name der zusätzlichen XML-Dialogfelddatei muss das Format `appmon.[applicationname].addition.[locale].xml` verwenden, wobei *applicationname* genau mit dem in der XML-Konfigurationsdatei und im Skript verwendeten Programmnamen übereinstimmen muss.

>[!NOTE]
>
Keines der generischen Programme, die in der Konfigurationsdatei „native2pdfconfig.xml“ angegeben sind, verfügt über eine primäre XML-Dialogfelddatei. Der Abschnitt [Hinzufügen oder Ändern der Unterstützung für ein natives Dateiformat](converting-file-formats-pdf.md#adding-or-modifying-support-for-a-native-file-format) beschreibt solche Spezifikationen.

Bestellung `windowList` -Elemente, die als untergeordnete Elemente in einer `window` -Element. (Siehe [Sortieren von window- und windowList-Elementen](converting-file-formats-pdf.md#ordering-the-window-and-windowlist-elements).)

### Ändern der allgemeinen XML-Dialogfelddatei {#modifying-the-general-dialog-xml-file}

Sie können die allgemeine XML-Dialogfelddatei ändern, um auf vom System generierte Dialogfelder zu reagieren oder auf Dialogfelder zu reagieren, die für mehrere Programme gelten.

#### Hinzufügen eines Dateitypeintrags in der XML-Konfigurationsdatei {#adding-a-filetype-entry-in-the-xml-configuration-file}

In diesem Verfahren wird beschrieben, wie Sie die Konfigurationsdatei des Generate PDF-Services aktualisieren, um Dateitypen mit nativen Programmen zu verknüpfen. Um diese Konfigurationsdatei zu aktualisieren, müssen Sie die Konfigurationsdaten mithilfe von Administration Console in eine Datei exportieren. Der standardmäßige Dateiname für die Konfigurationsdaten lautet „native2pdfconfig.xml“.

**Aktualisieren der Konfigurationsdatei des Generate PDF-Services**

1. Wählen Sie **Startseite** > **Services** > **Adobe PDF Generator** > **Konfigurationsdateien**, und wählen Sie dann **Exportkonfiguration**.
1. Ändern Sie das `filetype-settings`-Element in der Datei „native2pdfconfig.xml“ nach Bedarf.
1. Wählen Sie **Startseite** > **Services** > **Adobe PDF Generator** > **Konfigurationsdateien**, und wählen Sie dann **Importkonfiguration**. Die Konfigurationsdaten werden in den Generate PDF-Service importiert, wobei die vorherigen Einstellungen ersetzt werden.

>[!NOTE]
>
Der Name der Anwendung wird als Wert der Variablen `GenericApp` -Element `name` -Attribut. Dieser Wert muss exakt mit dem entsprechenden Namen übereinstimmen, der im Skript angegeben ist, das Sie für dieses Programm entwickeln. Genauso wird die `GenericApp` -Element `displayName` sollte genau mit dem entsprechenden Skript übereinstimmen `expectedWindow` Fensterbeschriftung. Diese Gleichwertigkeit wird nach der Auflösung von regulären Ausdrücken, die in den `displayName`- oder `caption`-Attributen erscheinen, bewertet.

In diesem Beispiel wurden die mit dem Generate PDF-Service bereitgestellten Standardkonfigurationsdaten geändert, um anzugeben, dass nicht Microsoft Word, sondern Notepad zur Verarbeitung von Dateien mit der Dateierweiterung .txt verwendet werden soll. Vor dieser Änderung wurde Microsoft Word als das native Programm angegeben, das solche Dateien verarbeiten soll.

**Änderungen für die Weiterleitung von Textdateien an Notepad (native2pdfconfig.xml)**

```xml
 <filetype-settings>

 <!-- Some native app file types were omitted for brevity. -->
 <!-- The following GenericApp element specifies Notepad as the native application that should be used to process files that have a txt file name extension. -->
             <GenericApp
                 extensions="txt"
                 name="Notepad" displayName=".*Notepad"/>
             <GenericApp
                 extensions="wpd"
                 name="WordPerfect" displayName="Corel WordPerfect"/>
             <GenericApp extensions="pmd,pm6,p65,pm"
                 name="PageMaker" displayName="Adobe PageMaker"/>
             <GenericApp extensions="fm"
                 name="FrameMaker" displayName="Adobe FrameMaker"/>
             <GenericApp extensions="psd"
                 name="Photoshop" displayName="Adobe Photoshop"/>
         </settings>
     </filetype-settings>
```

#### Erstellen einer Umgebungsvariablen zum Auffinden des nativen Programms {#creating-an-environment-variable-to-locate-the-native-application}

Erstellen Sie eine Umgebungsvariable, die den Speicherort der ausführbaren Datei des nativen Programms angibt. Die Variable muss das Format `[applicationname]_PATH` haben, wobei *applicationname* exakt mit dem in der XML-Konfigurationsdatei und im Skript verwendeten Programmnamen übereinstimmen muss und der Pfad den Pfad zur ausführbaren Datei in doppelten Anführungszeichen enthält. Ein Beispiel für eine solche Umgebungsvariable ist `Photoshop_PATH`.

Nachdem Sie die neue Umgebungsvariable erstellt haben, müssen Sie den Server neu starten, auf dem der Generate PDF-Service bereitgestellt wird.

**Erstellen einer Systemvariablen in der Windows XP-Umgebung**

1. Wählen Sie **Systemsteuerung > System**.
1. Klicken Sie im Dialogfeld „Systemeigenschaften“ auf die Registerkarte **Erweitert** und dann auf **Umgebungsvariablen**.
1. Klicken Sie unter „Systemvariablen“ im Dialogfeld „Umgebungsvariablen“ auf **Neu**.
1. Geben Sie im Dialogfeld „Neue Systemvariable“ einen Namen im Format `[applicationname]_PATH` in das Feld **Variablenname** ein.
1. Geben Sie in das Feld **Variablenwert** den vollständigen Pfad und Dateinamen der ausführbaren Datei des Programms ein und klicken Sie dann auf **OK**. Geben Sie beispielsweise: `c:\windows\Notepad.exe`
1. Klicken Sie im Dialogfeld „Umgebungsvariablen“ auf **OK**.

**Erstellen einer Systemvariablen über die Befehlszeile**

1. Geben Sie in einem Befehlszeilenfenster die Variablendefinition in folgendem Format ein:

   ```shell
            [applicationname]_PATH=[Full path name]
   ```

   Geben Sie beispielsweise: `NotePad_PATH=C:\WINDOWS\NOTEPAD.EXE`

1. Starten Sie eine neue Eingabeaufforderung, damit die Systemvariable wirksam wird.

#### XML-Dateien {#xml-files}

AEM Forms enthält XML-Beispieldateien, die dazu führen, dass der Generate PDF-Service Notepad zur Verarbeitung von Dateien mit der Dateinamenerweiterung .txt verwendet. Dieser Code ist in diesem Abschnitt enthalten. Darüber hinaus müssen Sie die anderen in diesem Abschnitt beschriebenen Änderungen vornehmen.

#### Zusätzliche XML-Dialogfelddatei {#additional-dialog-xml-file}

Dieses Beispiel enthält die zusätzlichen Dialogfelder für das Notepad-Programm. Diese Dialogfelder können zusätzlich zu den vom Generate PDF-Service angegebenen Dialogfeldern angezeigt werden.

**Editor-Dialogfelder (appmon.notepad.additional.de_DE.xml)**

```xml
 <dialogs app="Notepad" locale="en_US" version="7.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="dialogs.xsd">
     <window caption="Caption Title">
         <windowList>
             <window className="Button" caption="OK" action="press"/>
         </windowList>
     </window>
 </dialogs>
```

#### XML-Skriptdatei {#script-xml-file}

In diesem Beispiel wird angegeben, wie der Generate PDF-Service mit Editor interagieren soll, um Dateien mithilfe des Adobe PDF-Druckers zu drucken.

**XML-Skriptdatei für Editor (appmon.notepad.script.de_DE.xml)**

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!--
*
* ADOBE CONFIDENTIAL
* ___________________
* Copyright 2004 - 2005 Adobe Systems Incorporated
* All Rights Reserved.
*
* NOTICE:  All information contained herein is, and remains
* the property of Adobe Systems Incorporated and its suppliers,
* if any.  The intellectual and technical concepts contained
* herein are proprietary to Adobe Systems Incorporated and its
* suppliers and may be covered by U.S. and Foreign Patents,
* patents in process, and are protected by trade secret or copyright law.
* Dissemination of this information or reproduction of this material
* is strictly forbidden unless prior written permission is obtained
* from Adobe Systems Incorporated.
*-->

<!-- This file automates printing of text files via notepad to Adobe PDF printer. To see the complete hierarchy Adobe recommends using the Microsoft Spy++ which details the properties of windows necessary to write scripts. In this sample there are total of eight steps-->

<application name="Notepad" version="9.0" locale="en_US" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="scripts.xsd">

    <!-- In this step we wait for the application window to appear -->
    <step>
        <expectedWindow>
            <window caption=".*Notepad"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the application window and send File->Open menu bar, menu item commands and the expectation is the windows Open dialog-->
    <step>
        <acquiredWindow>
            <window caption=".*Notepad">
                <virtualInput>
                    <menuBar>
                        <selection>
                            <name>File</name>
                        </selection>
                        <selection>
                            <name>Open...</name>
                        </selection>
                    </menuBar>
                </virtualInput>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Open"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the Open window and then select the 'Edit' widget and input the source path followed by clicking on the 'Open' button . The expectation of this 'action' is that the Open dialog will disappear -->
    <step>
        <acquiredWindow>
            <window caption="Open">
                <windowList>
                    <window className="ComboBoxEx32">
                        <windowList>
                            <window className="ComboBox">
                                <windowList>
                                <window className="Edit" action="inputSourcePath"/>
                                </windowList>
                            </window>
                        </windowList>
                    </window>
                </windowList>
                <windowList>
                    <window className="Button" caption="Open" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Open" action="disappear"/>
        </expectedWindow>
        <pause value="30"/>
    </step>

    <!-- In this step, we acquire the application window and send File->Print menu bar, menu item commands and the expectation is the windows Print dialog-->
    <step>
        <acquiredWindow>
            <window caption=".*Notepad">
                <virtualInput>
                    <menuBar>
                        <selection>
                            <name>File</name>
                        </selection>
                        <selection>
                            <name>Print...</name>
                        </selection>
                    </menuBar>
                </virtualInput>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Print">
        </window>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the Print dialog and click the 'Preferences' button and the expected window in this case is the dialog with the caption '"Printing Preferences' -->
    <step>
        <acquiredWindow>
            <window caption="Print">
                <windowList>
                    <window caption="General">
                        <windowList>
                            <window className="Button" caption="Preferences" action="press"/>
                        </windowList>
                    </window>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Printing Preferences"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the dialog "Printing Preferences' and select the combo box which is the 10th child of window with caption '"Adobe PDF Settings' and select the first index. (Note: All indeces start with 0.) Besides this we uncheck the box which has the caption '"View Adobe PDF results' and we click the button OK. The expectation is that 'Printing Preferences' dialog disappears. -->
    <step>
        <acquiredWindow>
            <window caption="Printing Preferences">
                <windowList>
                    <window caption="Adobe PDF Settings">
                        <windowList>
                            <window className="Button" caption="View Adobe PDF results" action="uncheck"/>
                        </windowList>
                        <windowList>
                            <window className="Button" caption="Ask to Replace existing PDF file" action="uncheck"/>
                        </windowList>
                    </window>
                </windowList>
                <windowList>
                    <window className="Button" caption="OK" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Printing Preferences" action="disappear"/>
        </expectedWindow>
    </step>

    <!-- In this step, we acquire the 'Print' dialog and click the Print button. The expectation is that the dialog with caption 'Print' disappears. In this case we use the regular expression '^Print$' for specifying the caption given there could be multiple dialogs with caption that includes the word Print. -->
    <step>
        <acquiredWindow>
            <window caption="Print">
                <windowList>
                    <window caption="General"/>
                    <window className="Button" caption="^Print$" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Print" action="disappear"/>
        </expectedWindow>
    </step>
    <step>
        <expectedWindow>
            <window caption="Save PDF File As"/>
        </expectedWindow>
    </step>
    <!-- Finally in this step, we acquire the dialog with caption "Save PDF File As" and in the Edit widget type the destination path for the output PDF file and click the Save button. The expectation is that the dialog disappears-->
    <step>
        <acquiredWindow>
            <window caption="Save PDF File As">
                <windowList>
                    <window className="Edit" action="inputDestinationPath"/>
                </windowList>
                <windowList>
                    <window className="Button" caption="Save" action="press"/>
                </windowList>
            </window>
        </acquiredWindow>
        <expectedWindow>
            <window caption="Save PDF File As" action="disappear"/>
        </expectedWindow>
    </step>

    <!-- We can always set a retry count or a maximum time for a step. In case we surpass these limitations, PDF Generator generates this abort message and terminates processing. -->
    <abortMessage msg="15078"/>
</application>
```
