---
title: Transaktionsberichte Abrechnungsfähige APIs für AEM Forms on JEE.
description: Liste aller APIs, die als Transaktionen für AEM Forms on JEE bilanziert werden.
topic-tags: forms-manager
feature: Transaction Reports
exl-id: dbb22369-c0a2-4cf6-b01b-096b4de13a14
role: Admin, User, Developer
solution: "Experience Manager, Experience Manager Forms"
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 54%

---

# Rechnungsstellungs-APIs für Transaktionsberichte für AEM Forms on JEE {#transaction-reports-billable-apis}

AEM Forms on JEE bietet mehrere APIs zum Senden, Verarbeiten und Rendern von Dokumenten. Einige APIs werden als Transaktionen verbucht, andere können kostenlos verwendet werden. Dieses Dokument enthält eine Liste aller APIs, die als Transaktionen bilanziert werden. Im Folgenden finden Sie einige gängige Szenarien, in denen eine kostenpflichtige API verwendet wird:

* Konvertieren eines Dokuments aus einem Format in ein anderes
* Reduzieren eines dynamischen PDF-Dokuments
* Zusammenführen eines interaktiven PDF-Dokuments mit einem anderen PDF-Dokument

Abrechnungs-APIs berücksichtigen nicht die Anzahl der Seiten, die Länge eines Dokuments oder Formulars oder das endgültige Format des wiedergegebenen Dokuments.
<!--

* **Forms Submitted:** When data is submitted from any type of form created with AEM Forms and the data is submitted to any data storage repository or database is considered form submission. For example, submitting an HTML5 Form, PDF Forms are accounted as forms submitted. Each form in a form set is considered a submission. For example, if a form set has 5 forms, when the form set is submitted, transaction reporting service counts it as 5 submissions.

* **Documents Rendered:** Generating a document by combining a template and data, digitally signing or certifying a document, using a billable document services API for document services, or converting a document from one format to another are accounted as documents rendered.

-->

Nachstehend finden Sie eine Liste der abrechnungsfähigen JEE-APIs. Suchen Sie die Liste der abrechnungsfähigen APIs für AEM Forms unter OSGi](/help/forms/using/transaction-reports-billable-apis.md).[

## Kostenpflichtige Document Services-APIs {#billable-document-services-apis}

### Generate PDF-Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
   <tr>
   <td><a>CreatePDF</a></td>
   <td>Erstellt Adobe PDF für unterstützte Dateitypen.</td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a>CreatePDF3</a></td>
   <td>Erstellt Adobe PDF für unterstützte Dateitypen. </td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a> HtmlToPDF</a></td>
   <td>Konvertiert die HTML-Datei in Adobe PDF. </td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a>ExportPDF</a></td>
   <td>Exportiert PDF in unterstützte Dateitypen. </td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a>ExportPDF2</a></td>
   <td><p>Exportiert PDF in unterstützte Dateitypen.</p> </td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a>ExportPDF3</a></td>
   <td>Exportiert PDF in unterstützte Dateitypen.</td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a>HtmlFileToPDF</a></td>
   <td>Konvertiert die HTML-Datei in PDF.</td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a>HtmlToPDF2</a></td>
   <td>Konvertiert die HTML-Datei in PDF.</td>
   <td>Konversion<br /> </td>
  </tr>
  <tr>
   <td><a>OptimizePDF</a></td>
   <td>Optimiert das PDF, um die Dateigröße zu reduzieren, indem unnötige Metadaten entfernt werden, ohne die Qualität zu beeinträchtigen.</td>
   <td>Konversion<br /> </td>
  </tr>
 </tbody>
</table>

### DocAssurance-Dienst {#DocAssurance-Service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
  <tr>
   <td><a>Signieren/Zertifizieren</a><br /> </td>
   <td>Mit dieser API können Sie Ihr Dokument sichern. Sie können die API zum Signieren und Zertifizieren eines PDF-Dokuments verwenden.</td>
   <td>Konversion</td>
  </tr>
 </tbody>
</table>


### Distiller-Service {#distiller-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
  <tr>
  <tr>
   <td><a>CreatePDF</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Konversion</td>
  </tr>
  <tr>
   <td><a>CreatePDF2</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Konversion</td>
  </tr>
 </tbody>
</table>

<!--

### Document of Record Service (DoR Service) {#document-of-record-service-dor-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">render</a></td>
   <td>Invokes the specified render method to generate a document of record using provided parameters.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

### Ausgabe-Service {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
  <tr>
   <td><a>generateOutput</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Gerenderte Dokumente</td>
  </tr>
  <tr>
   <td><a>generatePDFOutput</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Gerenderte Dokumente</td>
  </tr>
  <tr>
   <td><a>generatePDFOutput2</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Gerenderte Dokumente</td>
  </tr>
  <tr>
   <td><a>generatePrintedOutput</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Dateiformate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Gerenderte Dokumente</td>
  </tr>
  <tr>
   <td><a>generatePrintedOutput2</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Dateiformate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Gerenderte Dokumente</td>
  </tr>
  <tr>
   <td><a>transformPDF</a></td>
   <td>Konvertiert einen Satz von XDP- und PDF-Dokumenten in die Formate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Dokumentkonvertierung</td>
  </tr>
 </tbody>
</table>

<!-- ### Forms Service {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Renders PDF Form from XDP templates. The XDP templates are created in Forms Designer.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extracts data from a PDF Form or XDP templates</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

### Convert PDF-Service {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
  <tr>
   <td><a>toImage2</a></td>
   <td>Konvertiert ein PDF-Dokument in eine Liste von Bilddokumenten. Unterstützte Bildformate sind JPEG, JPEG2K, PNG und TIFF.</td>
   <td>Dokumentkonvertierung</td>
  </tr>
  <tr>
   <td><a>toPS2</a></td>
   <td>Konvertiert eine einfache PDF-Datei in das PostScript-Format mithilfe der in der Optionsbeschreibung angegebenen Optionen.</td>
   <td>Dokumentkonvertierung</td>
  </tr>
  <tr>
   <td><a>toSWF</a></td>
   <td>Konvertiert eine einfache PDF-Datei in das SWF-Format unter Verwendung der in der Optionsbeschreibung angegebenen Optionen.</td>
   <td>Dokumentkonvertierung</td>
  </tr>
 </tbody>
</table>

### Barcoded Forms-Dienst {#barcoded-forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
  <tr>
   <td><a>decode</a></td>
   <td>Decodiert alle Barcodes in einem Dokumentobjekt und gibt ein org.w3c.dom.Document-Objekt zurück, das Daten enthält, die aus dem Barcode abgerufen wurden.</td>
   <td>Dokumentkonvertierung</td>
  </tr>
 </tbody>
</table>

### Assembler-Service {#assembler-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
  <tr>
   <td><a>invoke</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein AssemblerResult-Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Dokumentkonvertierung</td>
  </tr>
  <tr>
   <td><a>invokeDDX</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein AssemblerResult-Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Dokumentkonvertierung</td>
  </tr>
  <tr>
   <td><a>invokeOneDocument</a></td>
   <td>Konvertieren Sie ein bestimmtes Dokument mithilfe der angegebenen Optionen in PDF/A.</td>
   <td>Dokumentkonvertierung</td>
  </tr>
  <tr>
   <td><a>invokeDDXOneDocument</a></td>
   <td>Konvertieren Sie ein bestimmtes Dokument mithilfe der angegebenen Optionen in PDF/A.</td>
   <td>Dokumentkonvertierung</td>
  </tr>
  <tr>
   <td><a>toPDFA</a></td>
   <td>Konvertieren Sie ein bestimmtes Dokument mithilfe der angegebenen Optionen in PDF/A.</td>
   <td>Dokumentkonvertierung</td>
  </tr>
 </tbody>
</table>

Die Verwendung der invoke-API wird als Transaktion gezählt, wenn Sie einen oder mehrere der folgenden Vorgänge ausführen:
1. Konvertierung von Nicht-PDF-Formaten in PDF-Formate. Beispielsweise die Konvertierung vom XDP-Format in das PDF-Format.<!-- catering to both interactive and non-interactive forms of communication, and the conversion from Word to PDF.-->
1. Konvertierung vom PDF-Format in das PDF/A-Format.
1. Konvertierung vom PDF-Format in Nicht-PDF-Formate. Beispiele sind die Umwandlung von PDF in das Bildformat oder die Konvertierung von PDF in das Textformat.

>[!NOTE]
>
>* Die invoke-API des Assembler-Services kann abhängig von der Eingabe intern eine kostenpflichtige API eines anderen Services aufrufen. Die `invoke API` kann also als keine, einzelne oder mehrere Transaktionen verbucht werden. Die Anzahl der gezählten Transaktionen hängt von der Eingabe und den aufgerufenen internen APIs ab.
>* Ein einzelnes PDF-Dokument, das mit Assembler-Dienst wie `invoke` und `invokeDDX` erstellt wurde, kann als keine, einzelne oder mehrere Transaktionen erfasst werden. Die Anzahl der gezählten Transaktionen hängt vom bereitgestellten <!--DDX--> -Code ab.

<!--
### PDF Utility Service  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a>convertPDFtoXDP</a></td>
   <td>Converts a PDF document into an XDP file. For a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the AcroForm dictionary.</td>
   <td>Documents Conversion</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

## Kostenpflichtige Datenerfassungs-APIs {#billable-data-capture-apis}

<!--All the submission events of Forms, HTML5 Forms, and form set are accounted as transactions. By default, submission of a PDF Form is not accounted as a transaction. Use the provided [transaction recorder API](record-transaction-custom-implementation.md) to record a PDF Forms submission as a transaction.-->

<!--
### Adaptive Forms {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an adaptive form</td>
   <td>Submits an adaptive form to configured submit action. </td>
   <td>Forms Submitted</td>
   <td>
    <ul>
     <li>Successful submissions account for single or two transactions. The number of transactions counted depends upon the type of submit action used for submission. For example, sending PDF through email submit action accounts for two counts of transactions. One transaction for form submission and another for PDF generated using the Document of Record (DOR) service. </li>
     <li>Using the adaptive form within an adaptive form (Adaptive form formset) accounts only single transaction. You can have any number of adaptive forms within an adaptive form.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

-->

<!--### HTML5 Forms {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an HTML5 Form</td>
   <td>Submits an HTML5 Form to submit URL configured in the form.</td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->

### Forms {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
  </tr>
  <tr>
   <td>exportData</td>
   <td>Formular wird gesendet.</td>
   <td>Übermittelte Formulare</td>
  </tr>
  <tr>
   <td>exportData2</td>
   <td>Formular wird gesendet.</td>
   <td>Übermittelte Formulare</td>
  </tr>
  <tr>
   <td>renderForm</td>
   <td>Formular wird gesendet.</td>
   <td>Forms Rendering</td>
  </tr>
  <tr>
   <td>renderHTMLForm</td>
   <td>Formular wird gesendet.</td>
   <td>Forms Rendering</td>
  </tr>
  <tr>
   <td>renderHTMLForm2</td>
   <td>Formular wird gesendet.</td>
   <td>Forms Rendering</td>
  </tr>
  <tr>
   <td>renderPDFForm</td>
   <td>Formular wird gesendet.</td>
   <td>Forms Rendering</td>
  </tr>
  <tr>
   <td>renderPDFForm2</td>
   <td>Formular wird gesendet.</td>
   <td>Forms Rendering</td>
  </tr>
  <tr>
   <td>renderPDFFormWithUsageRights</td>
   <td>Formular wird gesendet.</td>
   <td>Forms Rendering</td>
  </tr>
 </tbody>
</table>

<!-- ## Billable Interactive Communication and Form-centric AEM Workflows on OSGi APIs {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Assign task and document services steps of Form-centric AEM Workflows on OSGi and all the renditions of interactive communication and are accounted as transactions. Previewing an interactive communication on the author instance and previewing on the publish instance using Agent UI are not accounted as transactions. If a workflow step accounts a transaction and the workflow fails to complete, the transaction count is not reversed.

<!--

### Interactive Communication - Web Channel {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Rendering a web channel</td>
   <td>Opens the web version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interactive Communication - Print Channel {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (convert to PDF)</td>
   <td>Generates the PDF version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

-->


<!--
### Form-centric AEM Workflows on OSGi  {#form-centric-aem-workflows-on-osgi}

<table>
 <tbody>
  <tr>
   <td><p>Use case</p> </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an Assign Task step</td>
   <td>Forms Submitted</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Submitting a workflow application startpoint </td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
  <tr>
   <td>Submitting an interactive communication (Print Channel) from the Agent UI to a workflow</td>
   <td>Documents Rendered</td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->


<!--

WILL ADD THIS ONE - 

## Recording billable APIs as transactions for custom code {#recording-billable-apis-as-transactions-for-custom-code}

Actions like submitting a PDF Form, using Agent UI to preview an interactive communication, using non-standard form submission, and custom implementations are not accounted as transactions. AEM Forms provides an API to record such actions as transactions. You can call the API from your custom implementations to [record a transaction](/help/forms/using/record-transaction-custom-implementation.md).

## Related Articles {#related-articles}

* [Transaction Reports Overview](../../forms/using/transaction-reports-overview.md)
* [Viewing and Understanding a Transaction Reports](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Record a transaction for custom implementations](/help/forms/using/record-transaction-custom-implementation.md)

-->

## Ähnliche Artikel

* [Aktivieren und Anzeigen des Transaktionsberichts für AEM Forms on JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Eine Transaktion für benutzerdefinierte Komponenten-APIs für AEM Forms on JEE aufzeichnen](/help/forms/using/record-transaction-custom-component-jee.md)
