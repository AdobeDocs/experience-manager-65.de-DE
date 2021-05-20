---
title: Barcoded Forms-Dienst
seo-title: Verwendung des Barcoded Forms-Dienst von AEM Forms
description: 'Mit dem Barcoded Forms-Dienst von AEM Forms extrahieren Sie Daten aus elektronischen Abbildungen von Strichcodes. '
seo-description: 'Mit dem Barcoded Forms-Dienst von AEM Forms extrahieren Sie Daten aus elektronischen Abbildungen von Strichcodes. '
uuid: b044a788-0e4a-4718-b71a-bd846933d51b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: d431c4cb-e4be-41a5-8085-42393d4d468c
docset: aem65
exl-id: edaf12be-473f-4175-b4e0-549b41159a55
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 93%

---

# Barcoded Forms-Dienst{#barcoded-forms-service}

## Überblick {#overview}

Der Barcoded Forms-Dienst extrahiert Daten aus elektronischen Abbildungen von Strichcodes. Der Dienst akzeptiert TIFF- und PDF-Dateien mit einem oder mehreren Strichcodes als Eingabe und extrahiert die Strichcodedaten. Strichcodedaten können verschiedene Formate haben, so z. B. XML, durch ein Zeichen getrennte Zeichenfolgen oder mit JavaScript erstellte benutzerdefinierte Formate.

Der Barcoded Forms-Dienst unterstützt die folgenden **zweidimensionalen (2D)** Symbologien, die als gescannte TIFF- oder PDF-Dokumente bereitgestellt werden:

* PDF417
* Datenmatrix
* QR-Code

Der Dienst unterstützt außerdem die folgenden **eindimensionalen** Symbologien, die als gescannte TIFF- oder PDF-Dokumente bereitgestellt werden:

* Codabar
* Code128
* Code 3 von 9
* EAN13
* EAN8

Mit dem Barcoded Forms-Dienst können Sie die folgenden Aufgaben ausführen:

* Extrahieren von Strichcodedaten aus Strichcodegrafiken (TIFF oder PDF), die als Text mit Trennzeichen gespeichert werden.
* Konvertieren von Daten in Text mit Trennzeichen in das XML-Format (XDP oder XFDF). XML-Daten können leichter analysiert werden als Text mit Trennzeichen. Außerdem können Daten im XDP- oder XFDF-Format als Eingabe für andere Dienste in AEM Forms dienen.

Der Barcoded Forms-Dienst sucht in einer Grafik den Strichcode, dekodiert diesen und extrahiert die Daten. Der Dienst gibt die Strichcodedaten (bei Bedarf mithilfe der Entitätenkodierung) in einem Element vom Typ content eines XML-Dokuments zurück. Die folgende gescannte TIFF-Grafik eines Formulars enthält beispielsweise zwei Strichcodes:

![example](assets/example.png)

Der Barcoded Forms-Dienst gibt nach Dekodierung der Strichcodes das folgende XML-Dokument zurück:

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

Formularentwickler erstellen mithilfe von Designer interaktive mit Strichcodes versehene Formulare. (Weitere Informationen finden Sie in der [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63).) Wenn ein Benutzer ein mit Strichcode versehenes Formular mit Adobe Reader oder Acrobat ausfüllt, wird der Strichcode automatisch aktualisiert, um die Formulardaten zu verschlüsseln.

Der Barcoded Forms-Dienst dient zum Konvertieren von Daten, die in Papierform vorliegen, in ein vom Computer lesbares Format. Beispiel: Wenn ein mit Strichcode versehenes Formular ausgefüllt und gedruckt wird, kann die gedruckte Kopie gescannt werden und als Eingabe für den Barcoded Forms-Dienst dienen.

Überwachter Ordner-Endpunkte dienen zumeist zum Starten von Anwendungen, die den Barcoded Forms-Dienst nutzen. Dokumentscanfunktionen legen beispielsweise TIFF- oder PDF-Grafiken gescannter mit Strichcodes versehener Formulare in einem überwachten Ordner ab. Der Überwachter Ordner-Endpunkt übergibt die Grafiken zur Dekodierung an den Dienst.

### Empfohlene Kodierungs- und Dekodierungsformate  {#recommended-encoding-and-decoding-formats}

Ersteller von Strichcodeformularen sollten bei der Kodierung von Daten in Strichcodes ein einfaches Format mit Trennzeichen (z.B. Tabulatoren) verwenden. Außerdem sollten Zeilenumbrüche als Feldtrennzeichen vermieden verwenden. Designer bietet eine Auswahl von Kodierungen mit Trennzeichen, die automatisch ein JavaScript-Skript für die Kodierung von Strichcodes generieren. Die dekodierten Daten haben den Feldnamen in der ersten Zeile und ihre Werte in der zweiten Zeile, mit Tabulatoren zwischen jedem Feld.

Geben Sie beim Dekodieren von Strichcodes das Zeichen an, das zum Trennen von Feldern dient. Das für die Dekodierung angegebene Zeichen muss dem für die Kodierung des Strichcodes verwendeten Zeichen entsprechen. Wenn Formularersteller beispielsweise das empfohlene Format mit Tabulatoren als Trennzeichen nutzen, müssen sie den Standardwert Tabulator für das Feldtrennzeichen im Vorgang „Als XML extrahieren“ verwenden.

### Vom Benutzer angegebene Zeichensätze  {#user-specified-character-sets}

Wenn Formularentwickler in Designer ihren Formularen Strichcodeobjekte hinzufügen, kann eine Zeichenkodierung angegeben werden. Die erkannten Kodierungen sind: UTF-8, ISO-8859-1, ISO-8859-2, ISO-8859-7, Shift-JIS, KSC-5601, Big-Five, GB-2312, UTF-16. Standardmäßig werden alle Daten in Strichcodes als UTF-8 kodiert.

Beim Dekodieren von Strichcodes können Sie die zu verwendende Zeichensatzkodierung angeben. Damit sämtliche Daten ordnungsgemäß kodiert werden, geben Sie denselben Zeichensatz an, den der Formularersteller beim Entwurf des Formulars angegeben hat.

### API-Beschränkungen {#api-limitations}

Beim Einsatz der BCF-API sollten Sie die folgenden Einschränkungen berücksichtigen:

* Dynamische Formulare werden nicht unterstützt.
* Interaktive Formulare werden nur dann korrekt dekodiert, wenn sie reduziert werden.
* 1D-Strichcodes dürfen nur alphanumerische Werte enthalten (wenn sie unterstützt werden). 1D-Strichcodes, die Sonderzeichen enthalten, werden nicht dekodiert.

### Weitere Einschränkungen {#other-limitations}

Beachten Sie auch die folgenden Einschränkungen bei der Verwendung des Barcoded Forms-Dienstes:

* Der Dienst unterstützt AcroForms und statische Formulare mit 2D-Strichcodes, die mit Adobe Reader oder Acrobat gespeichert wurden, in vollem Umfang. Für 1D-Strichcodes müssen Sie das Formular jedoch reduzieren oder es als gescanntes PDF- oder TIFF-Dokument zur Verfügung stellen.
* Dynamische XFA-Formulare werden nicht in vollem Umfang unterstützt. Für die ordnungsgemäße Dekodierung eines 1D- und 2D-Strichcodes in einem dynamischen Formular müssen Sie das Formular entweder reduzieren oder es als gescanntes PDF- oder TIFF-Dokument bereitstellen.

Der Dienst kann zusätzlich sämtliche Strichcodes dekodieren, die unterstützte Symbologien nutzen, sofern die oben genannten Beschränkungen eingehalten werden. Weitere Informationen zum Erstellen interaktiver Barcoded Forms finden Sie unter [Designer-Hilfe](https://www.adobe.com/go/learn_aemforms_designer_63).

## Konfigurieren Sie die Eigenschaften des Dienstes   {#configureproperties}

Sie können den Dienst **AEMFD Barcoded Forms-Dienst** in AEM-Konsole verwenden, um Eigenschaften für diesen Dienst zu konfigurieren. Die Standard-URL AEM Konsole lautet `https://[host]:'port'/system/console/configMgr`.

## Verwendung des Dienstes {#using}

Der Barcoded Forms-Dienst stellt die folgenden zwei APIs zur Verfügung:

* **[decode](https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Dekodiert alle Barcodes, die in einem PDF-Eingabedokument oder in einem TIFF-Bild verfügbar sind. Es wird ein XML-Dokument mit den Daten zurückgegeben, die von allen Barcodes abgerufen wurden, welche im Eingabedokument oder im Bild verfügbar sind.

* **[extractToXML](https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode)**: Konvertiert Daten, die mit der Dekodier-API für XML-Daten dekodiert wurden. Diese XML-Daten können mit einem XFA-Formular zusammengeführt werden. Es wird eine Liste von XML-Dokumenten, eines je Barcode, zurückgegeben.

### Verwenden des BCF-Dienstes mit JSPs oder Servlets  {#using-bcf-service-with-a-jsp-or-servlets}

Der folgende Beispielcode dekodiert einen Barcode in einem Dokument und speichert die Ausgabe-XML auf der Festplatte.

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
 // Please see Docmanager Document javadoc for
 // more details
 Document inputDoc = new Document(documentPath);

 // Invoke decode operation of barcoded forms service 
 // Second parameter is set to true to decode PDF417 barcode symbology
 // Please see javadoc for details of parameters

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

Die Ausführung des Barcoded Forms-Dienstes über einen Workflow ist ähnlich wie die Ausführung über JSP/Servlet. Der einzige Unterschied beim Ausführen des Dienstes über JSP/Servlet liegt darin, dass das Dokumentobjekt automatisch eine Instanz des ResourceResolver-Objekts vom ResourceResolverHelper-Objekt abruft. Dieser automatische Mechanismus funktioniert nicht, wenn der Code in einem Workflow aufgerufen wird.

Bei einem Workflow müssen Sie ausdrücklich eine Instanz des ResourceResolver-Objekts an die Dokument-Klassen-Constructor übermitteln. Anschließend verwendet das Dokumentobjekt das bereitgestellte ResourceResolver-Objekt, um Inhalte aus dem Repository zu lesen.

Der folgende Workflowprozess dekodiert einen Barcode in einem Dokument und speichert das Ergebnis auf der Festplatte. Der Code ist in ECMAScript geschrieben und das Dokument wird als Workflow-Nutzlast übergeben:

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
