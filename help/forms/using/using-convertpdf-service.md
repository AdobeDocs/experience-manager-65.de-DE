---
title: ConvertPDF-Service
description: Verwenden Sie den Adobe Experience Manager Forms ConvertPDF-Dienst, um PDF-Dokumente in PostScript- oder Bilddateien zu konvertieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
exl-id: 575bab27-d973-47fa-a0da-fa889cec6f27
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 28%

---

# ConvertPDF-Dienst {#convertpdf-service}

## Übersicht {#overview}

Der Convert PDF-Dienst konvertiert PDF-Dokumente in PostScript- oder Bilddateien (JPEG, JPEG 2000, PNG und TIFF). Die Konvertierung eines PDF-Dokuments in PostScript ist für den unbeaufsichtigten serverbasierten Druck auf einem beliebigen PostScript-Drucker nützlich. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist bei der Archivierung von Dokumenten in Content-Management-Systemen praktisch, die keine PDF-Dokumente unterstützen.

Mit dem Convert PDF-Dienst können Sie Folgendes ausführen:

* Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie den Konvertierungsvorgang verwenden, um das Quelldokument anzugeben und festzulegen, ob es in PostScript-Ebene 2 oder 3 konvertiert werden soll. Das PDF-Dokument, das Sie in eine PostScript-Datei konvertieren, muss nicht interaktiv sein.
* Konvertieren Sie PDF-Dokumente in die Bildformate JPEG, JPEG 2000, PNG und TIFF. Beim Konvertieren in eines dieser Bildformate können Sie den Konvertierungsvorgang verwenden, um das Quelldokument und eine Spezifikation für Bildoptionen anzugeben. Die Spezifikation enthält verschiedene Voreinstellungen, z. B. das Bildkonvertierungsformat, die Bildauflösung und die Farbkonvertierung.

## Eigenschaften des Dienstes konfigurieren   {#properties}

Sie können die **AEMFD ConvertPDF-Dienst** in AEM Console , um Eigenschaften für diesen Dienst zu konfigurieren. Die Standard-URL der AEM-Konsole lautet `https://[host]:'port'/system/console/configMgr`.

## Verwenden des Dienstes {#using-the-service}

Der ConvertPDF-Dienst stellt die beiden folgenden APIs bereit:

* **[toPS](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toPS)**: Konvertiert ein PDF-Dokument in eine PostScript-Datei.

* **[toImage](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage)**: Konvertiert ein PDF-Dokument in eine Bilddatei. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF.

### Verwenden der toPS-API mit einer JSP oder Servlets {#using-tops-api-with-a-jsp-or-servlets}

```jsp
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToPSOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.PSLevel,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // replace this with path to your document
String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for
 // the flat PDF file which needs to be converted
 // to PostScript

 Document inputPDF = new Document(documentPath);

 // options object to pass to toPS API
 ToPSOptionsSpec toPSOptions = new ToPSOptionsSpec();

 // mandatory option to pass, sets PostScript language
 toPSOptions.setPsLevel(PSLevel.LEVEL_3);

 // invoke toPS method to convert inputPDF to PostScript
 Document convertedPS = cpdfService.toPS(inputPDF, toPSOptions);

 // save converted PostScript file to disk
 convertedPS.copyToFile(new File("C:/temp/out.ps"));

%>
```

### Verwenden der toImage-API mit einer JSP oder Servlets {#using-toimage-api-with-a-jsp-or-servlets}

```jsp
<%@ page import="java.util.List, java.io.File,

                com.adobe.fd.cpdf.api.ConvertPdfService,
                com.adobe.fd.cpdf.api.ToImageOptionsSpec,
                com.adobe.fd.cpdf.api.enumeration.ImageConvertFormat,

                com.adobe.aemfd.docmanager.Document" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to ConvertPdfService OSGi service.
 // Within an OSGi bundle @Reference annotation
 // can be used to retrieve service reference

 ConvertPdfService cpdfService = sling.getService(ConvertPdfService.class);

 // path to input document in AEM repository
 // replace this with path to your document
 String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for
 // the flat PDF file which needs to be converted
 // to image

 Document inputPDF = new Document(documentPath);

 // options object to pass to toImage API
 ToImageOptionsSpec toImageOptions = new ToImageOptionsSpec();

 // mandatory option to pass, image format
 toImageOptions.setImageConvertFormat(ImageConvertFormat.JPEG);

 // invoke toImage method to convert inputPDF to Image
 List<Document> convertedImages = cpdfService.toImage(inputPDF, toImageOptions);

 // save converted image files to disk
 for(int i=0;i<convertedImages.size();i++){
     Document pageImage = convertedImages.get(i);
     pageImage.copyToFile(new File("C:/temp/out_"+(i+1)+".jpeg"));
 }

%>
```

### Verwenden des ConvertPDF-Dienstes mit AEM Workflows {#using-convertpdf-service-with-aem-workflows}

Das Ausführen des ConvertPDF-Dienstes über einen Workflow ähnelt dem Ausführen über JSP/Servlet.

Der einzige Unterschied besteht darin, dass der Dienst von JSP/Servlet ausgeführt wird. Das Dokumentobjekt ruft automatisch eine Instanz des ResourceResolver-Objekts aus dem ResourceResolverHelper-Objekt ab. Dieser automatische Mechanismus funktioniert nicht, wenn der Code in einem Workflow aufgerufen wird. Bei einem Workflow müssen Sie ausdrücklich eine Instanz des ResourceResolver-Objekts an die Dokument-Klassen-Constructor übermitteln. Dann benutzt das Document-Objekt das bereitgestellte ResourceResolver-Objekt, um Inhalt aus dem Repository zu lesen.

Der folgende Beispiel-Workflow-Prozess konvertiert das Eingabedokument in ein PostScript-Dokument. Der Code wird in ECMAScript geschrieben und das Dokument wird als Workflow-Payload übergeben:

```javascript
/*
 * Imports
 */
var ConvertPdfService = Packages.com.adobe.fd.cpdf.api.ConvertPdfService;
var ToPSOptionsSpec = Packages.com.adobe.fd.cpdf.api.ToPSOptionsSpec;
var PSLevel = Packages.com.adobe.fd.cpdf.api.enumeration.PSLevel;
var Document = Packages.com.adobe.aemfd.docmanager.Document;
var File = Packages.java.io.File;
var ResourceResolverFactory = Packages.org.apache.sling.api.resource.ResourceResolverFactory;

// get reference to ConvertPdfService
var cpdfService = sling.getService(ConvertPdfService);

/*
 * workflow payload and path to it
 */
var payload = graniteWorkItem.getWorkflowData().getPayload();
var payload_path = payload.toString();

/* Create resource resolver using current session
 * this resource resolver needs to be passed to Document
 * object constructor when file is to be read from
 * crx repository.
 */

/* get ResourceResolverFactory service reference , used
 * to construct resource resolver
 */
var resourceResolverFactory = sling.getService(ResourceResolverFactory);

var authInfo = {
    "user.jcr.session":graniteWorkflowSession.getSession()
};

var resourceResolver = resourceResolverFactory.getResourceResolver(authInfo);

// Create Document object from payload_path
var inputDocument = new Document(payload_path, resourceResolver);

// options object to be passed to toPS operation
var toPSOptions = new ToPSOptionsSpec();

// Set PostScript Language Three
toPSOptions.setPsLevel(PSLevel.LEVEL_3);

// invoke toPS operation to convert inputDocument to PS
var convertedPS = cpdfService.toPS(inputDocument, toPSOptions);

// save converted PostScript file to disk
convertedPS.copyToFile(new File("C:/temp/out.ps"));
```
