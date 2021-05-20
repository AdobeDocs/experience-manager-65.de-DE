---
title: ConvertPDF-Dienst
seo-title: ConvertPDF-Dienst
description: Mithilfe des ConvertPDF-Dienstes von AEM Forms werden PDF-Dokumente in PostScript- oder Bilddateien konvertiert.
seo-description: Mithilfe des ConvertPDF-Dienstes von AEM Forms werden PDF-Dokumente in PostScript- oder Bilddateien konvertiert.
uuid: 7fa94c8c-485b-4a77-bcd3-ed716e3cf316
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 5ec4f0ec-a9fd-4571-9b9a-278f4622c028
exl-id: 575bab27-d973-47fa-a0da-fa889cec6f27
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 94%

---

# ConvertPDF-Dienst {#convertpdf-service}

## Überblick {#overview}

Der Convert PDF-Dienst konvertiert PDF-Dokumente in PostScript oder Bilddateien (JPEG, JPEG 2000, PNG und TIFF). Das Konvertieren eines PDF-Dokuments in PostScript ist nützlich für die unbeaufsichtigte serverbasierte Druckausgabe auf PostScript-Druckern. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist beim Archivieren von Dokumenten in Content Management-Systemen praktisch, die PDF-Dokumente nicht unterstützen.

Mit dem Convert PDF-Dienst können Sie Folgendes ausführen:

* Konvertieren von PDF-Dokumenten in PostScript – Beim Konvertieren in PostScript können Sie für den Konvertierungsvorgang das Quelldokument und die PostScript-Ebene (2 oder 3) angeben. Das PDF-Dokument, das in eine PostScript-Datei konvertiert wird, muss nicht interaktiv sein.
* Konvertieren von PDF-Dokumenten in die Bildformate JPEG, JPEG 2000, PNG und TIFF – Beim Konvertieren in diese Bildformate können Sie für den Konvertierungsvorgang das Quelldokument und eine Grafikoptionsspezifizierung angeben. Die Spezifizierung enthält verschiedene Voreinstellungen, z. B. das Bildkonvertierungsformat, die Bildauflösung und Farbumwandlung.

## Konfigurieren der Eigenschaften des Dienstes   {#properties}

Sie können den Dienst **AEMFD ConvertPDF** in AEM-Konsole verwenden, um Eigenschaften für diesen Dienst zu konfigurieren. Die Standard-URL AEM Konsole lautet `https://[host]:'port'/system/console/configMgr`.

## Verwendung des Dienstes {#using-the-service}

Der ConvertPDF-Dienst stellt die folgenden APIs bereit:

* **[toPS](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toPS)**: Konvertiert ein PDF-Dokument in eine PostScript-Datei.

* **[toImage](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage)**: Konvertiert ein PDF-Dokument in eine Bilddatei. Unterstützte Bildformate sind JPEG, JPEG2000, PNG und TIFF.

### Verwenden der toPS-API mit JSP oder Servlets {#using-tops-api-with-a-jsp-or-servlets}

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
 // please replace this with path to your document
String documentPath = "/content/dam/formsanddocuments/ExpenseClaimFlat.pdf";

 // Create a Docmanager Document object for
 // the flat PDF file which needs to be converted
 // to PostScript

 Document inputPDF = new Document(documentPath);

 // options object to pass to toPS API
 ToPSOptionsSpec toPSOptions = new ToPSOptionsSpec();

 // mandatory option to pass, sets PostScript langauge
 toPSOptions.setPsLevel(PSLevel.LEVEL_3);

 // invoke toPS method to convert inputPDF to PostScript
 Document convertedPS = cpdfService.toPS(inputPDF, toPSOptions);

 // save converted PostScript file to disk
 convertedPS.copyToFile(new File("C:/temp/out.ps"));

%>
```

### Verwenden der toImage-API mit JSPs oder Servlets {#using-toimage-api-with-a-jsp-or-servlets}

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
 // please replace this with path to your document
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

### Verwenden des ConvertPDF-Dienstes mit AEM-Workflows {#using-convertpdf-service-with-aem-workflows}

Die Ausführung des ConvertPDF-Dienstes über einen Workflow ist ähnlich wie die Ausführung über JSP/Servlet.

Der einzige Unterschied beim Ausführen des Dienstes über JSP/Servlet liegt darin, dass das Dokumentobjekt automatisch eine Instanz des ResourceResolver-Objekts vom ResourceResolverHelper-Objekt abruft. Dieser automatische Mechanismus funktioniert nicht, wenn der Code in einem Workflow aufgerufen wird. Bei einem Workflow müssen Sie ausdrücklich eine Instanz des ResourceResolver-Objekts an die Dokument-Klassen-Constructor übermitteln. Anschließend verwendet das Dokumentobjekt
bereitgestelltes ResourceResolver -Objekt zum Lesen von Inhalten aus dem Repository.

Der folgende Beispielworkflow-Prozess konvertiert das Eingabedokument in ein PostScript-Dokument. Der Code ist in ECMAScript geschrieben und das Dokument wird als Workflow-Nutzlast übergeben:

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
