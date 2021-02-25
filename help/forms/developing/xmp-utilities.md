---
title: Arbeiten mit XMP Utilities
seo-title: Arbeiten mit XMP Utilities
description: Verwenden Sie die XMP Utilities Java und Web Service APIs, um XMP Metadaten programmgesteuert in ein PDF-Dokument zu importieren und XMP Metadaten aus einem PDF-Dokument abzurufen und zu speichern.
seo-description: Verwenden Sie die XMP Utilities Java und Web Service APIs, um XMP Metadaten programmgesteuert in ein PDF-Dokument zu importieren und XMP Metadaten aus einem PDF-Dokument abzurufen und zu speichern.
uuid: 90ce6cef-efe1-456a-8e0c-5ba90249dda0
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 01d5677f-5c87-4a6e-987b-8eda9acc0b27
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 3%

---


# Arbeiten mit XMP Dienstprogrammen {#working-with-xmp-utilities}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

**Informationen zum XMP Utilities-Dienst**

PDF-Dokumente enthalten Metadaten, d. h. Informationen über das Dokument, die sich vom Inhalt des Dokuments unterscheiden, z. B. Text und Grafiken. Adobe Extensible Metadata Platform (XMP) ist ein Standard für die Verarbeitung von Dokument-Metadaten.

Der XMP Utilities-Dienst kann XMP Metadaten aus PDF-Dokumenten abrufen und speichern und XMP Metadaten in PDF-Dokumente importieren.

Sie können diese Aufgaben mithilfe des XMP Utilities-Dienstes ausführen:

* Importieren von Metadaten in PDF-Dokumente (Siehe [Importieren von Metadaten in PDF-Dokumente](xmp-utilities.md#importing-metadata-into-pdf-documents).)
* Exportieren von Metadaten aus PDF-Dokumenten (Siehe [Exportieren von Metadaten aus PDF-Dokumenten](xmp-utilities.md#exporting-metadata-from-pdf-documents).)

>[!NOTE]
>
>Weitere Informationen zum XMP Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Importieren von Metadaten in PDF-Dokumente {#importing-metadata-into-pdf-documents}

Sie können die Java- und Webdienst-APIs der XMP Utilities verwenden, um XMP Metadaten programmgesteuert in ein PDF-Dokument zu importieren. Metadaten enthalten Informationen zu einem PDF-Dokument, z. B. den Autor des Dokuments und Schlüsselwörter zum Dokument. Metadaten können Sie im Dialogfeld &quot;Dokument-Eigenschaften&quot;des Dokuments finden, wie in der folgenden Abbildung dargestellt.

![ww_ww_metadatadialog](assets/ww_ww_metadatadialog.png)

Um Metadaten programmgesteuert in ein PDF-Dokument zu importieren, können Sie ein vorhandenes XML-Dokument verwenden, das die Metadatenwerte angibt, oder Sie können ein Objekt des Typs `XMPUtilityMetadata` verwenden. (Siehe [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

>[!NOTE]
>
>In diesem Abschnitt wird die Verwendung eines XML-Dokuments zum Importieren von Metadaten in ein PDF-Dokument erläutert.

Der folgende XML-Code enthält Metadatenwerte, die der vorherigen Abbildung entsprechen. Beachten Sie beispielsweise die fett gedruckten Elemente, die Suchbegriffe angeben.

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
>Weitere Informationen zum XMP Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So importieren Sie XMP Metadaten in ein PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen XMPUtilityService-Client.
1. Rufen Sie den Importvorgang für XMP Metadaten auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**XMPUtilityService-Client erstellen**

Bevor Sie einen XMP Dienstprogrammvorgang ausführen können, müssen Sie einen XMPUtilityService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `XMPUtilityServiceClient`-Objekt erstellt wird. Mit der Webdienst-API wird dies mithilfe eines `XMPUtilityServiceService`-Objekts erreicht.

**Aufrufen des Importvorgangs für XMP Metadaten**

Nachdem Sie den Dienstclient erstellt haben, können Sie einen der XMP Metadaten-Importvorgänge aufrufen, um die XMP Metadaten in das angegebene PDF-Dokument zu importieren.

**Siehe auch**

[Importieren XMP Metadaten mit der Java-API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[Importieren XMP Metadaten mit der Webdienst-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importieren XMP Metadaten mit der Java-API {#import-xmp-metadata-using-the-java-api}

Importieren Sie XMP Metadaten mithilfe der XMP Utilities API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-pdfutility-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

   >[!NOTE]
   >
   >Die Datei &quot;adobe-pdfutility-client.jar&quot;enthält Klassen, mit denen Sie den XMP Utilities-Dienst programmgesteuert aufrufen können.

1. XMPUtilityService-Client erstellen

   Erstellen Sie ein `XMPUtilityServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Aufrufen des Importvorgangs für XMP Metadaten

   Um die XMP-Metadaten zu ändern, rufen Sie entweder die `XMPUtilityServiceClient`-Methode des Objekts `importMetadata` oder die `importXMP`-Methode auf.

   Wenn Sie die `importMetadata`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt.
   * Ein `XMPUtilityMetadata`-Objekt, das die zu importierenden Metadaten enthält.

   Wenn Sie die `importXMP`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt.
   * Ein `com.adobe.idp.Document`-Objekt, das eine XML-Datei darstellt, die die zu importierenden Metadaten enthält.

   In beiden Fällen ist der zurückgegebene Wert ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei mit den neu importierten Metadaten darstellt. Sie können dieses Objekt dann auf der Festplatte speichern.

**Siehe auch**

[Importieren von Metadaten in PDF-Dokumente](xmp-utilities.md#importing-metadata-into-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Importieren XMP Metadaten mit der Webdienst-API {#importing-xmp-metadata-using-the-web-service-api}

So importieren Sie XMP Metadaten programmgesteuert mit der XMP Utilities-Webdienst-API:

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des XMP Utilities-Dienstes verwendet. (Siehe [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding) verwendet.)

1. XMPUtilityService-Client erstellen

   Erstellen Sie ein `XMPUtilityServiceService`-Objekt mit Ihrem Proxyklassenkonstruktor.

1. Aufrufen des Importvorgangs für XMP Metadaten

   Um die XMP-Metadaten zu ändern, rufen Sie entweder die `XMPUtilityServiceService`-Methode des Objekts `importMetadata` oder die `importXMP`-Methode auf.

   Wenn Sie die `importMetadata`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `BLOB`-Objekt, das die PDF-Datei darstellt.
   * Ein `XMPUtilityMetadata`-Objekt, das die zu importierenden Metadaten enthält.

   Wenn Sie die `importXMP`-Methode verwenden, geben Sie die folgenden Werte ein:

   * Ein `BLOB`-Objekt, das die PDF-Datei darstellt.
   * Ein `BLOB`-Objekt, das eine XML-Datei darstellt, die die zu importierenden Metadaten enthält.

   In beiden Fällen ist der zurückgegebene Wert ein `BLOB`-Objekt, das die PDF-Datei mit den neu importierten Metadaten darstellt. Sie können dieses Objekt dann auf der Festplatte speichern.

**Siehe auch**

[Importieren von Metadaten in PDF-Dokumente](xmp-utilities.md#importing-metadata-into-pdf-documents)

<!--REVIEW: [Quick Start (Base64): Importing XMP metadata using the web service API](unresolvedlink-lc-qs-xmp-utilities-xu.xml#ws624e3cba99b79e12e69a9941333732bac8-7be8.2)-->

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Exportieren von Metadaten aus PDF-Dokumenten {#exporting-metadata-from-pdf-documents}

Sie können die Java- und Webdienst-APIs der XMP Utilities verwenden, um XMP Metadaten programmgesteuert aus einem PDF-Dokument abzurufen und zu speichern.

>[!NOTE]
>
>Weitere Informationen zum XMP Utilities-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So exportieren Sie XMP Metadaten aus einem PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen XMPUtilityService-Client.
1. Rufen Sie den Exportvorgang für XMP Metadaten auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**XMPUtilityService-Client erstellen**

Bevor Sie einen XMP Dienstprogrammvorgang ausführen können, müssen Sie einen XMPUtilityService-Client erstellen. Mit dem Java-API wird dies durch Erstellen eines `XMPUtilityServiceClient`-Objekts erreicht. Mit der Webdienst-API wird dies mithilfe eines `XMPUtilityServiceService`-Objekts erreicht.

**Aufrufen des Exportvorgangs für XMP Metadaten**

Nachdem Sie den Dienstclient erstellt haben, können Sie einen der Exportvorgänge für XMP Metadaten aufrufen, mit denen die XMP überprüft oder auf der Festplatte gespeichert werden können.

**Siehe auch**

[Importieren XMP Metadaten mit der Java-API](xmp-utilities.md#import-xmp-metadata-using-the-java-api)

[Importieren XMP Metadaten mit der Webdienst-API](xmp-utilities.md#importing-xmp-metadata-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren XMP Metadaten mit der Java-API {#export-xmp-metadata-using-the-java-api}

Exportieren Sie XMP Metadaten mithilfe der XMP Utilities API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-pdfutility-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

   >[!NOTE]
   >
   >Die Datei &quot;adobe-pdfutility-client.jar&quot;enthält Klassen, mit denen Sie den Dienst XMP Utility programmgesteuert aufrufen können.

1. XMPUtilityService-Client erstellen

   Erstellen Sie ein `XMPUtilityServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Aufrufen des Importvorgangs für XMP Metadaten

   Um die XMP-Metadaten zu überprüfen, rufen Sie die `XMPUtilityServiceClient`-Methode des Objekts `exportMetadata` auf und übergeben Sie ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `XMPUtilityMetadata`-Objekt zurück, das die abgerufenen Metadaten enthält.

   Rufen Sie zum Abrufen und Speichern der XMP-Metadaten die `XMPUtilityServiceClient`-Methode des Objekts `exportXMP` auf und übergeben Sie ein `com.adobe.idp.Document`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das die abgerufenen Metadaten enthält, die Sie anschließend als XML-Datei auf der Festplatte speichern können.

**Siehe auch**

[Exportieren von Metadaten aus PDF-Dokumenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Exportieren XMP Metadaten mit der Webdienst-API {#export-xmp-metadata-using-the-web-service-api}

Exportieren Sie XMP Metadaten mithilfe der XMP Utilities API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL-Datei des XMP Utilities-Dienstes verwendet.
   * Verweisen Sie auf die Microsoft .NET-Clientassembly.

1. XMPUtilityService-Client erstellen

   Erstellen Sie ein `XMPUtilityServiceService`-Objekt mit Ihrem Proxyklassenkonstruktor.

1. Aufrufen des Importvorgangs für XMP Metadaten

   Um die XMP-Metadaten zu überprüfen, rufen Sie die `XMPUtilityServiceClient`-Methode des Objekts `exportMetadata` auf und übergeben Sie ein `BLOB`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `XMPUtilityMetadata`-Objekt zurück, das die abgerufenen Metadaten enthält.

   Rufen Sie zum Abrufen und Speichern der XMP-Metadaten die `XMPUtilityServiceClient`-Methode des Objekts `exportXMP` auf und übergeben Sie ein `BLOB`-Objekt, das die PDF-Datei darstellt. Die Methode gibt ein `BLOB`-Objekt zurück, das die abgerufenen Metadaten enthält, die Sie anschließend als XML-Datei auf der Festplatte speichern können.

**Siehe auch**

[Exportieren von Metadaten aus PDF-Dokumenten](xmp-utilities.md#exporting-metadata-from-pdf-documents)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Erstellen einer .NET-Client-Assembly, die Base64-Kodierung verwendet](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)
