---
title: Abrechenbare APIs für Transaktionsberichte
seo-title: Transaction Reports Billable APIs
description: Liste aller APIs, die als Transaktionen verbucht werden
seo-description: List of all the APIs that are accounted as transactions
uuid: d2f38ae4-75df-426f-af34-52ae6fb324f3
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 929a298d-7f22-487f-bf7d-8ab2556d0d81
docset: aem65
exl-id: 1bc99f3b-3f28-4e74-b259-6ebddc11ffc5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1949'
ht-degree: 100%

---

# Abrechenbare APIs für Transaktionsberichte{#transaction-reports-billable-apis}

AEM Forms bietet mehrere APIs zum Senden von Formularen, zum Verarbeiten von Dokumenten und zum Rendern von Dokumenten. Einige APIs werden als Transaktionen verbucht, andere können kostenlos verwendet werden. Dieses Dokument enthält eine Liste aller APIs, die in einem Transaktionsbericht als Transaktionen verbucht werden. Im Folgenden finden Sie einige gängige Szenarien, in denen eine kostenpflichtige API verwendet wird:

* Übermitteln eines adaptiven Formulars, HTML5-Formulars und Formularsatzes
* Rendern einer Druck- oder Web-Version einer interaktiven Kommunikation
* Konvertieren eines Dokuments aus einem Format in ein anderes
* Reduzieren eines dynamischen PDF-Dokuments
* Generieren eines Datensatzdokuments
* Zusammenführen eines interaktiven PDF-Dokuments mit einem anderen PDF-Dokument
* Verwenden des Schritts zum Zuweisen einer Aufgabe und der Schritte für Dokumenten-Services von AEM-Workflows
* Verwenden eines adaptiven Formulars innerhalb eines adaptiven Formulars

Kostenpflichtige APIs berücksichtigen nicht die Anzahl der Seiten, die Länge eines Dokuments oder Formulars oder das endgültige Format des wiedergegebenen Dokuments. Ein Transaktionsbericht unterteilt die Transaktionen in zwei Kategorien: gerenderte Dokumente und übermittelte Formulare.

* **Übermittelte Formulare**: Wenn Daten von einem mit AEM Forms erstellten Formular beliebigen Typs gesendet werden und die Daten an ein Datenspeicher-Repository oder an eine Datenbank gesendet werden, gilt dies als Formularübermittlung. Beispielsweise werden das Übermitteln eines adaptiven Formulars, eines HTML5-Formulars, von PDF-Formularen und eines Formularsatzes als Übermittlungen von Formularen verbucht. Jedes Formular in einem Formularsatz gilt als Übermittlung. Wenn ein Formularsatz beispielsweise 5 Formulare umfasst, zählt der Transaktionsberichts-Service die Übermittlung des Formularsatzes als 5 Übermittlungen.

* **Gerenderte Dokumente**: Das Generieren eines Dokuments durch Kombinieren einer Vorlage und von Daten, das digitale Signieren oder Zertifizieren eines Dokuments, die Verwendung kostenpflichtiger Document Services-APIs für Dokumenten-Services oder das Konvertieren eines Dokuments von einem Format in ein anderes werden als gerenderte Dokumente verbucht.

>[!NOTE]
>
>Die Benutzeroberfläche „Transaktionsberichte“ zeigt drei Kategorien an: übermittelte Formulare, gerenderte Dokumente und verarbeitete Dokumente. Sowohl gerenderte als auch verarbeitete Dokumente werden als gerenderte Dokumente verbucht.

## Kostenpflichtige Document Services-APIs {#billable-document-services-apis}

### Generate PDF-Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Konvertiert Adobe PDF in unterstützte Dateitypen. </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Konvertiert Adobe PDF in unterstützte Dateitypen. </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Konvertiert Adobe PDF in unterstützte Dateitypen. </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Erstellt PDF von HTML-Seiten.</p> </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Erstellt PDF aus URLs, die auf eine HTML-Seite verweisen.</td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Erstellt PDF aus URLs, die auf eine HTML-Seite verweisen.</td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimiert das PDF, um die Dateigröße zu reduzieren, indem unnötige Metadaten entfernt werden, ohne die Qualität zu beeinträchtigen.</td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
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
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Datensatzdokument-Service (DoR-Service) {#document-of-record-service-dor-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">render</a></td>
   <td>Ruft die angegebene Render-Methode auf, um mithilfe der bereitgestellten Parameter ein Datensatzdokument zu generieren.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Ausgabe-Service {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PDFOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePDFOutputBatch</a></td>
   <td>Führt Daten und Vorlagen zusammen, um einen Satz von PDF-Dokumenten zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> Die generatePDFOutputBatch-API kombiniert eine Formularvorlage mit einem Datensatz und generiert eine PDF-Datei. Wenn Sie einen Datensatz-Batch verarbeiten, zählt der Transaktionsberichts-Service jeden Datensatz als separate PDF-Ausgabedarstellung. <br> Sie können das Flag <a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> verwenden, um mehrere Ausgabedarstellungen zu einer einzigen PDF-Datei zu kombinieren. Unabhängig vom Status des Flags zählt der Service jeden Datensatz als separate PDF-Ausgabedarstellung. </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Dateiformate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Dateiformate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PrintedOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePrintedOutputBatch</a></td>
   <td>Konvertiert einen Satz von XDP- und PDF-Dokumenten in die Formate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> Die generatePDFOutputBatch-API kombiniert eine Formularvorlage mit einem Datensatz und generiert eine PDF-Datei. Wenn Sie einen Datensatz-Batch verarbeiten, zählt der Transaktionsberichts-Service jeden Datensatz als separate PDF-Ausgabedarstellung. <br> Sie können das Flag <a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> verwenden, um mehrere Ausgabedarstellungen zu einer einzigen PDF-Datei zu kombinieren. Unabhängig vom Status des Flags zählt der Service jeden Datensatz als separate PDF-Ausgabedarstellung. </td>
  </tr>
 </tbody>
</table>

### Formularservice {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Rendert ein PDF-Formular aus XDP-Vorlagen. Die XDP-Vorlagen werden in Forms Designer erstellt.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extrahiert Daten aus einem PDF-Formular oder XDP-Vorlagen</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Convert PDF-Service {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Konvertiert ein PDF-Dokument in eine Liste von Bilddokumenten. Unterstützte Bildformate sind JPEG, JPEG2K, PNG und TIFF.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td>
   <td>Konvertiert eine einfache PDF-Datei in das PostScript-Format mithilfe der in der Optionsbeschreibung angegebenen Optionen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
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
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td>
   <td>Decodiert alle Barcodes in einem Dokumentobjekt und gibt ein org.w3c.dom.Document-Objekt zurück, das Daten enthält, die aus dem Barcode abgerufen wurden.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
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
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-">invoke</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein <a href="https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a>-Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Verarbeitete Dokumente</td>
   <td>Folgende Vorgänge werden nicht als Transaktionen verbucht:
    <ul>
     <li>Erstellen von Paketen oder Portfolios</li>
     <li>Zusammenfügen mehrerer XDPs </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-" target="_blank">invoke</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein <a href="https://helpx.adobe.com/de/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a>-Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Verarbeitete Dokumente</td>
   <td>Der Assembler-Service unterstützt alle Eingabedateiformate, die von PDF Generator, Forms und Ausgabe-Services unterstützt werden, als Ausgabedateiformate. </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#toPDFA-com.adobe.aemfd.docmanager.Document-com.adobe.fd.assembler.client.PDFAConversionOptionSpec-">toPDFA</a></td>
   <td>Konvertieren Sie ein bestimmtes Dokument mithilfe der angegebenen Optionen in PDF/A.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Die invoke-API des Assembler-Services kann abhängig von der Eingabe intern eine kostenpflichtige API eines anderen Services aufrufen. Daher kann die invoke-API als keine, eine einzige oder auch mehrere Transaktionen verbucht werden. Die Anzahl der gezählten Transaktionen hängt von der Eingabe und den aufgerufenen internen APIs ab.
>* Ein einzelnes PDF-Dokument, das mit dem Assembler-Service erstellt wurde, kann als keine, eine einzige oder auch mehrere Transaktionen erfasst werden. Die Anzahl der gezählten Transaktionen hängt vom bereitgestellten DDX-Code ab.
>


### PDF Utility-Service  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td>
   <td>Konvertiert ein PDF-Dokument in eine XDP-Datei. Damit ein PDF-Dokument erfolgreich in eine XDP-Datei konvertiert werden kann, muss das PDF-Dokument einen XFA-Stream im AcroForm-Wörterbuch enthalten.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Kostenpflichtige Datenerfassungs-APIs {#billable-data-capture-apis}

Alle Übermittlungsereignisse von adaptiven Formularen, HTML5-Formularen und Formularsätzen werden als Transaktionen verbucht. Standardmäßig wird die Übermittlung eines PDF-Formulars nicht als Transaktion verbucht. Verwenden Sie die bereitgestellte [Transaktions-Recorder-API](record-transaction-custom-implementation.md), um eine Übermittlung von PDF-Formularen als Transaktion zu erfassen.

### Adaptive Formulare {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Nutzungsszenario</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines adaptiven Formulars</td>
   <td>Übermittelt ein adaptives Formular entsprechend der konfigurierten Übermittlungsaktion. </td>
   <td>Übermittelte Formulare</td>
   <td>
    <ul>
     <li>Erfolgreiche Übermittlungen zählen als eine oder zwei Transaktionen. Die Anzahl der gezählten Transaktionen hängt vom Typ der für die Übermittlung verwendeten Übermittlungsaktion ab. Das Senden einer PDF-Datei über eine E-Mail-Übermittlungsaktion wird zum Beispiel als zwei Transaktionen gezählt. Eine Transaktion für die Formularübermittlung und eine andere für die PDF, die mit dem DoR-Service (Datensatzdokument) generiert wurde. </li>
     <li>Bei Verwendung des adaptiven Formulars innerhalb eines adaptiven Formulars (Formularsatz von adaptiven Formularen) wird nur eine einzige Transaktion verbucht. Sie können eine beliebige Anzahl adaptiver Formulare innerhalb eines adaptiven Formulars verwenden.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### HTML5-Formulare {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Nutzungsszenario</p> </td>
   <td>Beschreibung </td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Übermitteln eines HTML5-Formulars</td>
   <td>Übermittelt ein HTML5-Formular an die im Formular konfigurierte Übermittlungs-URL.</td>
   <td>Übermittelte Formulare</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Formularsatz {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Übermitteln eines Formularsatzes</td>
   <td>Übermittelt einen Formularsatz an die im Formularsatz konfigurierte Übermittlungs-URL.</td>
   <td>Übermittelte Formulare</td>
   <td>
    <ul>
     <li>Bei Verwendung des adaptiven Formulars innerhalb eines adaptiven Formulars (Formularsatz von adaptiven Formularen) wird nur eine einzige Transaktion verbucht. Sie können eine beliebige Anzahl adaptiver Formulare innerhalb eines adaptiven Formulars verwenden.</li>
     <li>Jedes Formular in einem Formularsatz von HTML5-Formularen wird als separate Transaktion verbucht. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Kostenpflichtige interaktive Kommunikation und formularzentrierte AEM Workflows in OSGi-APIs {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Die Schritte der Zuweisung von Aufgaben und der Dokumenten-Services von formularzentrierten AEM-Workflows unter OSGi und alle Ausgabedarstellungen von interaktiver Kommunikation werden als Transaktionen verbucht. Die Vorschau einer interaktiven Kommunikation auf der Autoreninstanz und die Vorschau auf der Veröffentlichungsinstanz mithilfe der Agent-Benutzeroberfläche werden nicht als Transaktionen verbucht. Wenn durch einen Workflow-Schritt eine Transaktion verbucht wird und der Workflow nicht abgeschlossen werden kann, wird die Transaktionsanzahl nicht zurückgesetzt.

### Webkanal für interaktive Kommunikation {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Rendern eines Web-Kanals</td>
   <td>Öffnet die Web-Version einer interaktiven Kommunikation.</td>
   <td>Gerenderte Dokumente</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interaktive Kommunikation – Druckkanal {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (in PDF konvertieren)</td>
   <td>Erzeugt die PDF-Version einer interaktiven Kommunikation.</td>
   <td>Gerenderte Dokumente</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Formularorientierte AEM-Workflows in OSGi  {#form-centric-aem-workflows-on-osgi}

<table>
 <tbody>
  <tr>
   <td><p>Nutzungsszenario</p> </td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Übermitteln eines Schritts „Aufgabe zuweisen“</td>
   <td>Übermittelte Formulare</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Übermitteln eines Startpunkts für ein Workflow-Programm </td>
   <td>Übermittelte Formulare</td>
   <td> </td>
  </tr>
  <tr>
   <td>Übermitteln einer interaktiven Kommunikation (Druckkanal) von der Agent-Benutzeroberfläche an einen Workflow</td>
   <td>Gerenderte Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Aufzeichnen von kostenpflichtigen APIs als Transaktionen für benutzerspezifischen Code {#recording-billable-apis-as-transactions-for-custom-code}

Aktionen wie das Übermitteln eines PDF-Formulars, die Verwendung der Agent-Benutzeroberfläche zur Vorschau einer interaktiven Kommunikation, die Verwendung nicht standardmäßiger Formularübermittlung und benutzerdefinierte Implementierungen werden nicht als Transaktionen berücksichtigt. AEM Forms bietet eine API zum Aufzeichnen solcher Aktionen als Transaktionen. Sie können die API aus Ihren benutzerdefinierten Implementierungen aufrufen, um [eine Transaktion aufzuzeichnen](/help/forms/using/record-transaction-custom-implementation.md).

## Ähnliche Artikel {#related-articles}

* [Übersicht über Transaktionsberichte](../../forms/using/transaction-reports-overview.md)
* [Anzeigen und Verstehen von Transaktionsberichten](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen](/help/forms/using/record-transaction-custom-implementation.md)
