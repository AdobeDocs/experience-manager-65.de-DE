---
title: Barcoded Forms-Service
description: Verwenden Sie den AEM Forms Barcoded Forms-Dienst, um Daten aus elektronischen Abbildungen von Barcodes zu extrahieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services
source-git-commit: 744cfcee691ea71f33cd56509f65d4f640d4c6e3
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 26%

---

# Barcoded Forms-Service{#barcoded-forms-service}

## Übersicht {#overview}

Der Barcoded Forms-Dienst extrahiert Daten aus elektronischen Abbildungen von Barcodes. Der Service akzeptiert TIFF- und PDF-Dateien mit einem oder mehreren Barcodes als Eingabe und extrahiert die Barcode-Daten. Barcodedaten können auf verschiedene Weise formatiert werden, z. B. XML, durch Trennzeichen getrennte Zeichenfolgen oder mit JavaScript erstellte benutzerdefinierte Formate.

Der Barcoded Forms-Service unterstützt die folgenden **zweidimensionalen (2D)** Symbologien, die als gescannte TIFF- oder PDF-Dokumente bereitgestellt werden:

* PDF417
* Datenmatrix
* QR-Code

Der Service unterstützt außerdem die folgenden **eindimensionalen** Symbologien, die als gescannte TIFF- oder PDF-Dokumente bereitgestellt werden:

* Codabar
* Code128
* Code 3 von 9
* EAN13
* EAN8

Mit dem Barcoded Forms-Dienst können Sie die folgenden Aufgaben ausführen:

* Extrahieren Sie Barcodedaten aus Barcodebildern (TIFF oder PDF). Die Daten werden als durch Trennzeichen getrennten Text gespeichert.
* Konvertieren von durch Trennzeichen getrennten Textdaten in XML (XDP oder XFDF). XML-Daten lassen sich leichter analysieren als durch Trennzeichen getrennten Text. Außerdem können Daten im XDP- oder XFDF-Format als Eingabe für andere Dienste in AEM Forms verwendet werden.

Für jeden Barcode in einem Bild sucht der Barcoded Forms-Dienst den Barcode, dekodiert ihn und extrahiert die Daten. Der Dienst gibt die Barcodedaten (gegebenenfalls unter Verwendung der Entitätskodierung) in einem Inhaltselement eines XML-Dokuments zurück. Beispielsweise enthält das folgende gescannte TIFF-Bild eines Formulars zwei Barcodes:

![Beispiel](assets/example.png)

Der Barcoded Forms-Dienst gibt nach Dekodierung der Barcodes das folgende XML-Dokument zurück:

```xml
<?xml version="1.0" encoding="UTF-8" ?>  
<xb:scanned_image xmlns:xb="https://decoder.barcodedforms.adobe.com/xmlbeans"     path="tiff" version="1.0"> 
    <xb:decode> 
        <xb:date>2007-05-11T15:07:49.965-04:00</xb:date>  
        <xb:host_name>myhost.adobe.com</xb:host_name>  
        <xb:status type="success"> 
            <xb:message />  
        </xb:status> 
    </xb:decode> 
    <xb:barcode id="1"> 
        <xb:header symbology="pdf417"> 
            <xb:location page_no="1"> 
                <xb:coordinates> 
                    <xb:point x="0.119526625" y="0.60945123" />  
                    <xb:point x="0.44457594" y="0.60945123" />  
                    <xb:point x="0.44457594" y="0.78445125" />  
                    <xb:point x="0.119526625" y="0.78445125" />  
                </xb:coordinates> 
            </xb:location> 
        </xb:header> 
        <xb:body> 
            <xb:content encoding="utf-8">t_SID t_FirstName t_MiddleName t_LastName t_nFirstName t_nMiddleName t_nLastName 90210 Patti Y Penne Patti P Prosciutto</xb:content>  
        </xb:body> 
    </xb:barcode> 
    <xb:barcode id="2"> 
        <xb:header symbology="pdf417"> 
            <xb:location page_no="1"> 
                <xb:coordinates> 
                    <xb:point x="0.119526625" y="0.825" />  
                    <xb:point x="0.44457594" y="0.825" />  
                    <xb:point x="0.44457594" y="0.9167683" />  
                    <xb:point x="0.119526625" y="0.9167683" />  
                </xb:coordinates> 
            </xb:location> 
         </xb:header> 
        <xb:body> 
            <xb:content encoding="utf-8">t_FormType t_FormVersion ChangeName 20061128</xb:content>  
         </xb:body> 
    </xb:barcode> 
</xb:scanned_image>
```

## Überlegungen zum Dienst {#considerations}

### Workflows, die mit Strichcode versehene Formulare verwenden {#workflows-that-use-barcoded-forms}

Formularverfasser erstellen interaktive Formulare mit Strichcode mithilfe von Designer. (Weitere Informationen finden Sie in der [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63_de).) Wenn ein Benutzer ein mit Strichcode versehenes Formular mit Adobe Reader oder Acrobat ausfüllt, wird der Strichcode automatisch aktualisiert, um die Formulardaten zu kodieren.

Der Barcoded Forms-Dienst ist nützlich zum Konvertieren von Daten, die auf Papier vorhanden sind, in ein elektronisches Format. Wenn beispielsweise ein mit Strichcode versehenes Formular ausgefüllt und gedruckt wird, kann die gedruckte Kopie gescannt und als Eingabe für den Barcoded Forms-Dienst verwendet werden.

Überwachter Ordner-Endpunkte dienen zumeist zum Starten von Anwendungen, die den Barcoded Forms-Dienst nutzen. Dokumentscanner können beispielsweise TIFF- oder PDF-Bilder von mit Strichcode versehenen Formularen in einem überwachten Ordner speichern. Der Endpunkt des überwachten Ordners übergibt die Bilder zur Dekodierung an den Dienst.

### Empfohlene Kodierungs- und Dekodierungsformate {#recommended-encoding-and-decoding-formats}

Autoren von mit Strichcode versehenen Formularen sollten bei der Kodierung von Daten in Barcodes ein einfaches, durch Trennzeichen (z. B. Tabulatoren) Format verwenden. Vermeiden Sie außerdem die Verwendung von Zeilenumbruch als Feldtrennzeichen. Designer bietet eine Auswahl von durch Trennzeichen getrennten Kodierungen, die automatisch JavaScript-Skripten zur Kodierung von Barcodes generieren. Die dekodierten Daten haben die Feldnamen in der ersten Zeile und ihre Werte in der zweiten Zeile, mit Tabulatoren zwischen den einzelnen Feldern.

Geben Sie beim Dekodieren von Barcodes das Zeichen an, das zum Trennen von Feldern verwendet wird. Das für die Dekodierung angegebene Zeichen muss mit dem für die Kodierung des Barcodes verwendeten Zeichen übereinstimmen. Bei Verwendung des empfohlenen tabulatorgetrennten Formats muss der Vorgang &quot;Extract to XML&quot;beispielsweise den Standardwert Tab für das Feldtrennzeichen verwenden.

### Vom Benutzer angegebene Zeichensätze {#user-specified-character-sets}

Wenn Formularautoren mithilfe von Designer Barcode-Objekte zu ihren Formularen hinzufügen, können sie eine Zeichenkodierung angeben. Die anerkannten Kodierungen sind UTF-8, ISO-8859-1, ISO-8859-2, ISO-8859-7, Shift-JIS, KSC-5601, Big-Five, GB-2312, UTF-16. Standardmäßig sind alle Daten in Barcodes als UTF-8 kodiert.

Beim Dekodieren von Barcodes können Sie die zu verwendende Zeichensatzkodierung angeben. Um sicherzustellen, dass alle Daten korrekt dekodiert sind, geben Sie denselben Zeichensatz an, den der Formularverfasser beim Entwurf des Formulars angegeben hat.

### API-Einschränkungen {#api-limitations}

Beachten Sie bei der Verwendung der BCF-APIs die folgenden Einschränkungen:

* dynamische Formulare werden nicht unterstützt.
* Interaktive Formulare werden nur dann korrekt dekodiert, wenn sie reduziert werden.
* 1D-Strichcodes dürfen nur alphanumerische Werte enthalten (wenn sie unterstützt werden). 1D-Strichcodes, die Sonderzeichen enthalten, werden nicht dekodiert.

### Weitere Einschränkungen {#other-limitations}

Beachten Sie auch die folgenden Einschränkungen bei der Verwendung des Barcoded Forms-Service:

* Der Dienst unterstützt AcroForms und statische Formulare mit 2D-Strichcodes, die mit Adobe Reader oder Acrobat gespeichert wurden, in vollem Umfang. Bei 1D-Barcodes reduzieren Sie das Formular jedoch entweder oder geben es als gescanntes PDF- oder TIFF-Dokument an.
* Dynamic XFA-Formulare werden nicht vollständig unterstützt. Um 1D- und 2D-Barcodes in einem dynamischen Formular korrekt zu dekodieren, reduzieren Sie das Formular entweder oder geben Sie es als gescanntes PDF- oder TIFF-Dokument an.

Der Service kann zusätzlich sämtliche Strichcodes dekodieren, die unterstützte Symbologien nutzen, sofern die oben genannten Beschränkungen berücksichtigt werden. Weitere Informationen dazu, wie Sie interaktive Formulare mit Strichcode erstellen, finden Sie unter [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63_de).

## Eigenschaften des Dienstes konfigurieren   {#configureproperties}

Sie können die **AEMFD Barcoded Forms-Dienst** in AEM Console , um Eigenschaften für diesen Dienst zu konfigurieren. Die Standard-URL der AEM-Konsole lautet `https://[host]:'port'/system/console/configMgr`.

## Verwenden des Dienstes {#using}

Der Barcoded Forms-Dienst bietet die folgenden beiden APIs:

* **[decode](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Dekodiert alle Barcodes, die in einem PDF-Eingabedokument oder in einem TIFF-Bild verfügbar sind. Es wird ein XML-Dokument mit den Daten zurückgegeben, die von allen Strichcodes abgerufen wurden, welche im Eingabedokument oder im Bild verfügbar sind.

* **[extractToXML](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Konvertiert Daten, die mit der Dekodier-API für XML-Daten dekodiert wurden. Diese XML-Daten können mit einem XFA-Formular zusammengeführt werden. Es wird eine Liste mit XML-Dokumenten zurückgegeben, eines für jeden Barcode.

### Verwenden des BCF-Dienstes mit JSP oder Servlets {#using-bcf-service-with-a-jsp-or-servlets}

Der folgende Beispielcode dekodiert einen Strichcode in einem Dokument und speichert die Ausgabe-XML auf der Festplatte.

```jsp
<%@ page import="java.util.List,
                com.adobe.fd.bcf.api.BarcodedFormsService,
                com.adobe.fd.bcf.api.CharSet,
                com.adobe.fd.bcf.api.Delimiter,
                com.adobe.fd.bcf.api.XMLFormat,
                com.adobe.aemfd.docmanager.Document,
                javax.xml.transform.Transformer,
                javax.xml.transform.TransformerFactory,
                java.io.StringWriter,
                javax.xml.transform.stream.StreamResult,
                javax.xml.transform.dom.DOMSource,
                javax.servlet.jsp.JspWriter,
                org.apache.commons.lang.StringEscapeUtils" %><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/><%

 // Get reference to BarcodedForms OSGi service.
 // Within an OSGi bundle @Reference annotation 
 // can be used to retrieve service reference

 BarcodedFormsService bcfService = sling.getService(BarcodedFormsService.class);

 // Path to image containing barcodes in AEM repository. 
 // Replace this with path to image in your repository
 String documentPath = "/content/dam/TestImage-010.tif";

 // Create a Docmanager Document object for 
 // the tiff file containing barcode
 // See Docmanager Document javadoc for
 // more details
 Document inputDoc = new Document(documentPath);

 // Invoke decode operation of barcoded forms service 
 // Second parameter is set to true to decode PDF417 barcode symbology
 // See javadoc for details of parameters

 org.w3c.dom.Document result = bcfService.decode(inputDoc, // Input Document Object
                                                    true, 
                                                    false,  
                                                    false,
                                                    false,
                                                    false,
                                                    false,
                                                    false,
                                                    false,
                                                    CharSet.UTF_8);// use UTF-8 character encoding 

 out.println("<h2> Output Returned from decode operation </h2>");
 printDoc(result,out);

 // Invoke extractToXML to convert Carriage 
 // return / Tab delimited data to XML 

 List<org.w3c.dom.Document> listResult = bcfService.extractToXML(result, // w3c document from the output of decode operation
                                                                    Delimiter.Carriage_Return, // Lines are separated using "\r"
                                                                    Delimiter.Tab, // Fields are separated using "\t" 
                                                                    XMLFormat.XDP); // wraps generated XML in <xdp:xdp> packet

 out.println("<h2> Output returned from extractToXML </h2>");
 printDoc(listResult.get(0),out);

%><%!

 // helper function to convert w3c document to string

 String convertToString(org.w3c.dom.Document inputDoc) throws Exception {
   TransformerFactory tf = TransformerFactory.newInstance();
   Transformer tr = tf.newTransformer();
   StringWriter sw = new StringWriter();
   StreamResult sr = new StreamResult(sw);
   tr.transform(new DOMSource(inputDoc), sr);
   return sw.toString();
 }

 // helper function to render XML to response

 void printDoc(org.w3c.dom.Document inputDoc,JspWriter out) throws Exception {
   String escapedString = StringEscapeUtils.escapeHtml(convertToString(inputDoc));
   out.println(escapedString);
 }

%>
```

### Verwenden des BCF-Dienstes mit AEM Workflows {#using-the-bcf-service-with-aem-workflows}

Das Ausführen des Barcoded Forms-Dienstes über einen Workflow ähnelt dem Ausführen des Dienstes über JSP/Servlet. Der einzige Unterschied besteht darin, dass der Dienst von JSP/Servlet ausgeführt wird. Das Dokumentobjekt ruft automatisch eine Instanz des ResourceResolver-Objekts aus dem ResourceResolverHelper-Objekt ab. Dieser automatische Mechanismus funktioniert nicht, wenn der Code in einem Workflow aufgerufen wird.

Bei einem Workflow müssen Sie ausdrücklich eine Instanz des ResourceResolver-Objekts an die Dokument-Klassen-Konstruktor übermitteln. Dann benutzt das Document-Objekt das bereitgestellte ResourceResolver-Objekt, um Inhalte aus dem Repository zu lesen.

Der folgende Beispiel-Workflow-Prozess dekodiert einen Barcode in einem Dokument und speichert das Ergebnis auf der Festplatte. Der Code wird in ECMAScript geschrieben und das Dokument wird als Workflow-Payload übergeben:

```javascript
/*
 * Imports 
 */
var BarcodedFormsService = Packages.com.adobe.fd.bcf.api.BarcodedFormsService;
var CharSet = Packages.com.adobe.fd.bcf.api.CharSet;

var Document = Packages.com.adobe.aemfd.docmanager.Document;
var File = Packages.java.io.File;
var FileOutputStream = Packages.java.io.FileOutputStream;
var TransformerFactory = Packages.javax.xml.transform.TransformerFactory;
var Transformer = Packages.javax.xml.transform.Transformer;
var StreamResult = Packages.javax.xml.transform.stream.StreamResult;
var DOMSource = Packages.javax.xml.transform.dom.DOMSource;

var ResourceResolverFactory = Packages.org.apache.sling.api.resource.ResourceResolverFactory;

// get reference to BarcodedFormsService
var bcfService = sling.getService(BarcodedFormsService);

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

// invoke decode operation to decode barcodes in inputDocument
var decodedBarcode = bcfService.decode(inputDocument, true, false, false, false, false, false, false, false, CharSet.UTF_8);

// save decoded barcode data to disk
saveW3CDocument(decodedBarcode, "C:/temp/decoded.xml");

/*
 * Helper function to save W3C Document
 * to a file on disk
 */
function saveW3CDocument(inputDoc, filePath) {
   var tf = TransformerFactory.newInstance();
   var tr = tf.newTransformer();
   var os = new FileOutputStream(filePath);
   var sr = new StreamResult(os);
   tr.transform(new DOMSource(inputDoc), sr);
   os.close();
}
```
