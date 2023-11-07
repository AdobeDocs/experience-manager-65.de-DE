---
title: Arbeiten mit XMP Utilities
seo-title: Working with XMP Utilities
description: Verwenden Sie die XMP Utilities Java- und Web Service-APIs, um XMP-Metadaten programmgesteuert in ein PDF-Dokument zu importieren und XMP-Metadaten aus einem PDF-Dokument abzurufen und zu speichern.
seo-description: Use the XMP Utilities Java and Web Service APIs to programmatically import XMP metadata into a PDF document and retrieve and save XMP metadata from a PDF document.
uuid: 90ce6cef-efe1-456a-8e0c-5ba90249dda0
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 01d5677f-5c87-4a6e-987b-8eda9acc0b27
role: Developer
exl-id: cff65f74-ba95-438e-88a4-5ec7d22aafba
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1404'
ht-degree: 98%

---

# Arbeiten mit XMP Utilities {#working-with-xmp-utilities}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Über den XMP Utilities-Service**

PDF-Dokumente enthalten Metadaten, d. h. Informationen über das Dokument, die sich vom Dokumentinhalt, z. B. Text und Grafiken, unterscheiden. Adobe Extensible Metadata Platform (XMP) ist ein Standard für die Verarbeitung von Dokumentmetadaten.

Der XMP Utilities-Service kann XMP-Metadaten aus PDF-Dokumenten abrufen und speichern und XMP-Metadaten in PDF-Dokumente importieren.

Diese Aufgaben können Sie mit dem XMP Utilities-Service ausführen:

* Importieren von Metadaten in PDF-Dokumente. (Siehe [Importieren von Metadaten in PDF-Dokumente](xmp-utilities.md#importing-metadata-into-pdf-documents).)
* Exportieren von Metadaten aus PDF-Dokumenten. (Siehe [Exportieren von Metadaten aus PDF-Dokumenten](xmp-utilities.md#exporting-metadata-from-pdf-documents).)

>[!NOTE]
>
>Weitere Informationen zum XMP Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importieren von Metadaten in PDF-Dokumente {#importing-metadata-into-pdf-documents}

Sie können die XMP Utilities Java- und Web-Service-APIs verwenden, um XMP-Metadaten programmgesteuert in ein PDF-Dokument zu importieren. Metadaten enthalten Informationen zu einem PDF-Dokument, z. B. den Autor des Dokuments und Schlüsselwörter zum Dokument. Metadaten können sich im Dialogfeld Dokumenteigenschaften des Dokuments befinden, wie in der folgenden Abbildung dargestellt.

![ww_ww_metadatadialog](assets/ww_ww_metadatadialog.png)

Um Metadaten programmgesteuert in ein PDF-Dokument zu importieren, können Sie ein vorhandenes XML-Dokument verwenden, das die Metadatenwerte angibt, oder Sie können ein Objekt vom Typ `XMPUtilityMetadata` verwenden. (Siehe [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

>[!NOTE]
>
>In diesem Abschnitt wird die Verwendung eines XML-Dokuments zum Importieren von Metadaten in ein PDF-Dokument behandelt.

Der folgende XML-Code enthält Metadatenwerte, die der vorherigen Abbildung entsprechen. Beachten Sie beispielsweise die fett gedruckten Elemente, die Schlüsselwörter angeben.

```xml
 <?xpacket begin="?" id="W5M0MpCehiHzreSzNTczkc9d"?>
 <x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="Adobe XMP Core 4.2-jc015 52.349034, 2008 Jun 20 00:30:39-PDT (debug)">
       <rdf:RDF xmlns:rdf="https://www.w3.org/1999/02/22-rdf-syntax-ns#">
          <rdf:Description rdf:about=""
                xmlns:xmp="https://ns.adobe.com/xap/1.0/">
             <xmp:MetadataDate>2008-10-22T10:52:21-04:00</xmp:MetadataDate>
             <xmp:CreatorTool>AEM Forms</xmp:CreatorTool>
             <xmp:ModifyDate>2008-10-22T10:52:21-04:00</xmp:ModifyDate>
             <xmp:CreateDate>2008-02-13T11:00:18-05:00</xmp:CreateDate>
          </rdf:Description>
          <rdf:Description rdf:about=""
                xmlns:pdf="https://ns.adobe.com/pdf/1.3/">
             <pdf:Producer>AEM Forms</pdf:Producer>
             <pdf:Keywords>keyword1, keyword2, keyword3,keyword4</pdf:Keywords>
          </rdf:Description>
          <rdf:Description rdf:about=""
                xmlns:xmpMM="https://ns.adobe.com/xap/1.0/mm/">
             <xmpMM:DocumentID>uuid:1cce1f84-331e-4d8d-8538-15441c271dd7</xmpMM:DocumentID>
             <xmpMM:InstanceID>uuid:cdda0ca6-7c91-4771-9dc9-796c8fe59350</xmpMM:InstanceID>
          </rdf:Description>
          <rdf:Description rdf:about=""
                >
             <dc:format>application/pdf</dc:format>
             <dc:description>
                <rdf:Alt>
                   <rdf:li xml:lang="x-default">Adobe Designer Sample</rdf:li>
                </rdf:Alt>
             </dc:description>
             <dc:title>
                <rdf:Alt>
                   <rdf:li xml:lang="x-default">Grant Application</rdf:li>
                </rdf:Alt>
             </dc:title>
             <dc:creator>
                <rdf:Seq>
                   <rdf:li>Tony Blue</rdf:li>
                </rdf:Seq>
             </dc:creator>
             <dc:subject>
                <rdf:Bag>
                   <rdf:li>keyword1</rdf:li>
                   <rdf:li>keyword2</rdf:li>
                   <rdf:li>keyword3</rdf:li>
                   <rdf:li>keyword4</rdf:li>
                </rdf:Bag>
             </dc:subject>
          </rdf:Description>
          <rdf:Description rdf:about=""
                xmlns:desc="https://ns.adobe.com/xfa/promoted-desc/">
             <desc:version rdf:parseType="Resource">
                <rdf:value>1.0</rdf:value>
                <desc:ref>/template/subform[1]</desc:ref>
             </desc:version>
             <desc:contact rdf:parseType="Resource">
                <rdf:value>Adobe Systems Incorporated</rdf:value>
                <desc:ref>/template/subform[1]</desc:ref>
             </desc:contact>
          </rdf:Description>
       </rdf:RDF>
 </x:xmpmeta>
```

>[!NOTE]
>
>Weitere Informationen zum XMP Utilities-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um XMP Metadaten in ein PDF-Dokument zu importieren:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen XMPUtilityService-Client.
1. Rufen Sie den Importvorgang für XMP-Metadaten auf.

**Schließen Sie Projektdateien ein**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines XMPUtilityService-Clients**

Bevor Sie einen Vorgang für XMP-Dienstprogramme programmgesteuert durchführen können, müssen Sie einen XMPUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `XMPUtilityServiceClient`-Objekt erstellt wird. Mit der Web-Service-API wird dies durch die Verwendung eines `XMPUtilityServiceService`-Objekts erreicht.

**Aufrufen des Importvorgangs XMP-Metadaten**

Nachdem Sie den Service-Client erstellt haben, können Sie einen der XMP-Metadaten-Importvorgänge aufrufen, um die XMP-Metadaten in das angegebene PDF-Dokument zu importieren.

**Siehe auch**

[Importieren von XMP-Metadaten mithilfe der Java-API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[Importieren von XMP-Metadaten mithilfe der Webservice-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importieren von XMP-Metadaten mithilfe der Java-API {#import-xmp-metadata-using-the-java-api}

Importieren Sie XMP-Metadaten mithilfe der XMP Utilities-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-pdfutility-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

   >[!NOTE]
   >
   >Die Datei adobe-pdfutility-client.jar enthält Klassen, mit denen Sie den Service „XMP Utilities“ programmgesteuert aufrufen können.

1. Erstellen Sie einen XMP-Utilities-Dienst-Clienten

   Erstellen Sie ein `XMPUtilityServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und dabei ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie den Importvorgang der XMP-Metadaten auf

   Um die XMP-Metadaten zu ändern, rufen Sie entweder die `importMetadata`-Methode oder die `importXMP`-Methode des `XMPUtilityServiceClient`-Objekts auf.

   Wenn Sie `importMetadata`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt.
   * Ein `XMPUtilityMetadata`-Objekt, das die zu importierenden Metadaten enthält.

   Wenn Sie die `importXMP`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt.
   * Ein `com.adobe.idp.Document`-Objekt, das eine XML-Datei mit den zu importierenden Metadaten darstellt.

   In beiden Fällen ist der zurückgegebene Wert ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei mit den neu importierten Metadaten darstellt. Sie können dieses Objekt dann auf der Festplatte speichern.

**Siehe auch**

[Importieren von Metadaten in PDF-Dokumente](xmp-utilities.md#importing-metadata-into-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importieren von XMP-Metadaten mithilfe der Webservice-API {#importing-xmp-metadata-using-the-web-service-api}

Führen Sie die folgenden Aufgaben aus, um XMP-Metadaten mithilfe der XMP-Utilities-Webservice-API programmgesteuert zu importieren:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des XMP Utilities-Services verwendet. (Siehe [Aufrufen von AEM Forms mithilfe von Base64-Codierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Referenzieren Sie die Microsoft .NET-Client-Assembly. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Codierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Erstellen Sie einen XMP-Utilities-Dienst-Clienten

   Erstellen Sie ein `XMPUtilityServiceService`-Objekt mithilfe des Klassenkonstruktors der Proxy.

1. Rufen Sie den Importvorgang der XMP-Metadaten auf

   Um die XMP-Metadaten zu ändern, rufen Sie entweder die `importMetadata`-Methode oder die `importXMP`-Methode des `XMPUtilityServiceService`-Objekts auf.

   Wenn Sie `importMetadata`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `BLOB`-Objekt, das die PDF-Datei darstellt.
   * Ein `XMPUtilityMetadata`-Objekt, das die zu importierenden Metadaten enthält.

   Wenn Sie die `importXMP`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `BLOB`-Objekt, das die PDF-Datei darstellt.
   * Ein `BLOB`-Objekt, das eine XML-Datei mit den zu importierenden Metadaten darstellt.

   In beiden Fällen ist der zurückgegebene Wert ein `BLOB`-Objekt, das die PDF-Datei mit den neu importierten Metadaten darstellt. Sie können dieses Objekt dann auf der Festplatte speichern.

**Siehe auch**

[Importieren von Metadaten in PDF-Dokumente](xmp-utilities.md#importing-metadata-into-pdf-documents)

<!--REVIEW: [Quick Start (Base64): Importing XMP metadata using the web service API](unresolvedlink-lc-qs-xmp-utilities-xu.xml#ws624e3cba99b79e12e69a9941333732bac8-7be8.2)-->

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Exportieren von Metadaten aus PDF-Dokumenten {#exporting-metadata-from-pdf-documents}

Sie können die XMP-Dienstprogramme Java- und Webservice-APIs verwenden, um XMP-Metadaten programmgesteuert aus einem PDF-Dokument abzurufen und zu speichern.

>[!NOTE]
>
>Weitere Informationen zum Service für XMP-Dienstprogramme finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um XMP-Metadaten aus einem PDF-Dokument zu exportieren, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen XMPUtilityService-Client.
1. Rufen Sie den Vorgang zum Export von XMP-Metadaten auf.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines XMPUtilityService-Clients**

Bevor Sie einen Vorgang für XMP-Dienstprogramme programmgesteuert durchführen können, müssen Sie einen XMPUtilityService-Client erstellen. Mit der Java-API wird dies durch Erstellen eines `XMPUtilityServiceClient`-Objekts erreicht. Mit der Webservice-API wird dies mithilfe eines `XMPUtilityServiceService`-Objekts erreicht.

**Aufrufen des Vorgangs zum Export von XMP-Metadaten**

Nachdem Sie den Service-Client erstellt haben, können Sie einen der Exportvorgänge für XMP-Metadaten aufrufen, mit denen die XMP-Metadaten geprüft oder auf der Festplatte gespeichert werden können.

**Siehe auch**

[Importieren von XMP-Metadaten mithilfe der Java-API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[Importieren von XMP-Metadaten mithilfe der Webservice-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren von XMP-Metadaten mithilfe der Java-API {#export-xmp-metadata-using-the-java-api}

Exportieren von XMP-Metadaten mithilfe der API für XMP-Dienstprogramme (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-pdfutility-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

   >[!NOTE]
   >
   >Die Datei „adobe-pdfutility-client.jar“ enthält Klassen, mit denen Sie den XMP-Utilities-Dienst programmgesteuert aufrufen können.

1. Erstellen Sie einen XMP-Utilities-Dienst-Clienten

   Erstellen Sie ein `XMPUtilityServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und dabei ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie den Importvorgang der XMP-Metadaten auf

   Rufen Sie zum Überprüfen der XMP-Metadaten die `exportMetadata`-Methode des `XMPUtilityServiceClient`-Objekts auf und übergeben Sie ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `XMPUtilityMetadata`-Objekt zurück, das die abgerufenen Metadaten enthält.

   Rufen Sie zum Abrufen und Speichern der XMP-Metadaten die `exportXMP`-Methode des `XMPUtilityServiceClient`-Objekts auf und übergeben Sie dabei ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die abgerufenen Metadaten enthält, die Sie anschließend als XML-Datei auf der Festplatte speichern können.

**Siehe auch**

[Exportieren von Metadaten aus PDF-Dokumenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren von XMP-Metadaten anhand der Web-Service-API {#export-xmp-metadata-using-the-web-service-api}

Exportieren von XMP-Metadaten anhand der XMP Utilities-API (Web-Service):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Zusammenführung, bei der die WSDL-Datei des XMP Utilities-Dienstes verwendet wird.
   * Verweisen Sie auf die Microsoft .NET-Client-Assembly.

1. Erstellen Sie einen XMP-Utilities-Dienst-Clienten

   Erstellen Sie ein `XMPUtilityServiceService`-Objekt mithilfe des Klassenkonstruktors der Proxy.

1. Rufen Sie den Importvorgang der XMP-Metadaten auf

   Rufen Sie zum Überprüfen der XMP-Metadaten die `exportMetadata`-Methode des `XMPUtilityServiceClient`-Objekts auf und übergeben Sie ein `BLOB`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `XMPUtilityMetadata`-Objekt zurück, das die abgerufenen Metadaten enthält.

   Rufen Sie zum Abrufen und Speichern der XMP-Metadaten die `exportXMP`-Methode des `XMPUtilityServiceClient`-Objekts auf und übergeben Sie dabei ein `BLOB`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `BLOB`-Objekt zurück, das die abgerufenen Metadaten enthält, die Sie anschließend als XML-Datei auf der Festplatte speichern können.

**Siehe auch**

[Exportieren von Metadaten aus PDF-Dokumenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Zusammenführung, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
