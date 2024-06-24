---
title: Barcoded Forms-Service
description: Mit dem Dienst „Barcode-Formulare“ von AEM Forms extrahieren Sie Daten aus elektronischen Abbildungen von Strichcodes.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services,Assembler,Barcoded Forms
exl-id: d4b5cacd-0bac-48b5-a8a6-0f58883136d7
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 100%

---

# Barcoded Forms-Service{#barcoded-forms-service}

## Übersicht {#overview}

Der Dienst „Barcode-Formulare“ extrahiert Daten aus elektronischen Abbildungen von Barcodes. Der Service akzeptiert TIFF- und PDF-Dateien mit einem oder mehreren Barcodes als Eingabe und extrahiert die Barcode-Daten. Barcode-Daten können verschiedene Formate haben, z. B. XML, durch ein Zeichen getrennte Zeichenfolgen oder mit JavaScript erstellte benutzerdefinierte Formate.

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

Mit dem Dienst „Barcode-Formulare“ können Sie die folgenden Aufgaben ausführen:

* Extrahieren von Barcode-Daten aus Barcode-Grafiken (TIFF oder PDF). Die Daten werden als Text mit Trennzeichen gespeichert.
* Konvertieren von Daten in Text mit Trennzeichen in das XML-Format (XDP oder XFDF). XML-Daten können leichter analysiert werden als Text mit Trennzeichen. Außerdem können Daten im XDP- oder XFDF-Format als Eingabe für andere Dienste in AEM Forms dienen.

Der Dienst „Barcode-Formulare“ sucht in einer Grafik den Barcode, decodiert diesen und extrahiert die Daten. Der Dienst gibt die Barcode-Daten (bei Bedarf mithilfe der Entitätenkodierung) in einem Element vom Typ „content“ eines XML-Dokuments zurück. Die folgende gescannte TIFF-Grafik eines Formulars enthält beispielsweise zwei Barcodes:

![Beispiel](assets/example.png)

Der Dienst „Barcode-Formulare“ gibt nach Dekodierung der Barcodes das folgende XML-Dokument zurück:

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

### Workflows, die mit Barcode versehene Formulare verwenden {#workflows-that-use-barcoded-forms}

Autorinnen und Autoren von Formularen erstellen interaktive Formulare mit Barcode mithilfe von Designer. (Weitere Informationen finden Sie in der [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63_de).) Wenn Sie ein Barcode-Formular mit Adobe Reader, Acrobat Professional oder Acrobat Standard ausfüllen, wird der Barcode automatisch aktualisiert, um die eingegebenen Formulardaten zu verschlüsseln. 

Der Dienst „Barcode-Formulare“ dient zum Konvertieren von Daten, die in Papierform vorliegen, in ein vom Computer lesbares Format. Beispiel: Wenn ein mit Barcode versehenes Formular ausgefüllt und gedruckt wird, kann die gedruckte Kopie gescannt werden und als Eingabe für den Dienst „Barcode-Formulare“ dienen.

Überwachter Ordner-Endpunkte dienen zumeist zum Starten von Anwendungen, die den Barcoded Forms-Dienst nutzen. Dokumentenscanfunktionen legen beispielsweise TIFF- oder PDF-Grafiken von mit Barcodes versehenen Formularen in einem überwachten Ordner ab. Der Endpunkt „Überwachter Ordner“ übergibt die Grafiken zur Dekodierung an den Dienst.

### Empfohlene Kodierungs- und Dekodierungsformate {#recommended-encoding-and-decoding-formats}

Erstellende von Barcode-Formularen sollten bei der Kodierung von Daten in Barcodes ein einfaches Format mit Trennzeichen (z. B. Tabulatoren) verwenden.  Außerdem sollten Zeilenumbrüche als Feldtrennzeichen vermieden werden. Designer bietet eine Auswahl von Kodierungen mit Trennzeichen, die automatisch ein JavaScript-Skript für die Kodierung von Barcodes generieren. Die dekodierten Daten haben den Feldnamen in der ersten Zeile und ihre Werte in der zweiten Zeile, mit Tabulatoren zwischen jedem Feld.

Geben Sie beim Dekodieren von Barcodes das Zeichen an, das zum Trennen von Feldern dient. Das für die Dekodierung angegebene Zeichen muss dem für die Kodierung des Barcodes verwendeten Zeichen entsprechen. Wenn jemand beispielsweise das empfohlene Format mit Tabulatoren als Trennzeichen nutzt, muss der Tabulator auch als Standardwert für das Feldtrennzeichen im Vorgang „Als XML extrahieren“ verwendet werden.

### Benutzerseitig angegebene Zeichensätze {#user-specified-character-sets}

Wenn Formularautorinnen und -autoren mithilfe von Designer Barcode-Objekte zu ihren Formularen hinzufügen, können sie eine Zeichenkodierung angeben. Folgende Kodierungen werden erkannt: UTF-8, ISO-8859-1, ISO-8859-2, ISO-8859-7, Shift-JIS, KSC-5601, Big-Five, GB-2312 und UTF-16. Standardmäßig werden alle Daten in Barcodes als UTF-8 kodiert.

Beim Dekodieren von Barcodes können Sie die zu verwendende Zeichensatzkodierung angeben. Damit sämtliche Daten ordnungsgemäß kodiert werden, geben Sie denselben Zeichensatz an, den die Autorin bzw. der Autor des Formulars bei dessen Entwurf festgelegt hat.

### API-Einschränkungen {#api-limitations}

Beim Einsatz der BCF-API sollten Sie die folgenden Einschränkungen berücksichtigen:

* Dynamische Formulare werden nicht unterstützt.
* Interaktive Formulare werden nur dann korrekt dekodiert, wenn sie reduziert werden.
* 1D-Strichcodes dürfen nur alphanumerische Werte enthalten (wenn sie unterstützt werden). 1D-Barcodes, die Sonderzeichen enthalten, werden nicht dekodiert.

### Weitere Einschränkungen {#other-limitations}

Beachten Sie auch die folgenden Einschränkungen bei der Verwendung des Barcoded Forms-Service:

* Der Dienst unterstützt AcroForms und statische Formulare mit 2D-Strichcodes, die mit Adobe Reader oder Acrobat gespeichert wurden, in vollem Umfang. Für 1D-Barcodes müssen Sie das Formular jedoch reduzieren oder es als gescanntes PDF- oder TIFF-Dokument zur Verfügung stellen.
* Dynamische XFA-Formulare werden nicht in vollem Umfang unterstützt. Für die ordnungsgemäße Dekodierung eines 1D- und 2D-Barcodes in einem dynamischen Formular müssen Sie das Formular entweder reduzieren oder es als gescanntes PDF- oder TIFF-Dokument bereitstellen.

Der Service kann zusätzlich sämtliche Strichcodes dekodieren, die unterstützte Symbologien nutzen, sofern die oben genannten Beschränkungen berücksichtigt werden. Weitere Informationen dazu, wie Sie interaktive Formulare mit Strichcode erstellen, finden Sie unter [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63_de).

## Konfigurieren der Eigenschaften des Dienstes  {#configureproperties}

Sie können den **AEMFD-Dienst „Barcode-Formulare“** in der AEM-Konsole verwenden, um Eigenschaften für diesen Dienst zu konfigurieren. Die Standard-URL der AEM-Konsole lautet `https://[host]:'port'/system/console/configMgr`.

## Verwenden des Dienstes {#using}

Der Dienst „Barcode-Formulare“ stellt die folgenden zwei APIs zur Verfügung:

* **[decode](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Dekodiert alle Barcodes, die in einem PDF-Eingabedokument oder in einem TIFF-Bild verfügbar sind. Es wird ein XML-Dokument mit den Daten zurückgegeben, die von allen Strichcodes abgerufen wurden, welche im Eingabedokument oder im Bild verfügbar sind.

* **[extractToXML](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Konvertiert Daten, die mit der Dekodier-API für XML-Daten dekodiert wurden. Diese XML-Daten können mit einem XFA-Formular zusammengeführt werden. Es wird eine Liste von XML-Dokumenten zurückgegeben (eines je Barcode).

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

### Verwenden des BCF-Dienstes mit AEM-Workflows {#using-the-bcf-service-with-aem-workflows}

Die Ausführung des Dienstes „Barcode-Formulare“ über einen Workflow ist ähnlich wie die Ausführung per JSP/Servlet. Der einzige Unterschied beim Ausführen des Dienstes über JSP/Servlet liegt darin, dass das Dokumentobjekt automatisch eine Instanz des ResourceResolver-Objekts vom ResourceResolverHelper-Objekt abruft. Dieser automatische Mechanismus funktioniert nicht, wenn der Code in einem Workflow aufgerufen wird.

Bei einem Workflow müssen Sie ausdrücklich eine Instanz des ResourceResolver-Objekts an die Dokument-Klassen-Konstruktor übermitteln. Dann benutzt das Document-Objekt das bereitgestellte ResourceResolver-Objekt, um Inhalte aus dem Repository zu lesen.

Der folgende Workflow-Prozess dekodiert einen Barcode in einem Dokument und speichert das Ergebnis auf der Festplatte. Der Code ist in ECMAScript geschrieben und das Dokument wird als Payload des Workflows übergeben:

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
