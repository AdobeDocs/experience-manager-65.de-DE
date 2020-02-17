---
title: Transaktionsberichte Abrechnungsfähige APIs
seo-title: Transaktionsberichte Abrechnungsfähige APIs
description: Liste aller APIs, die als Transaktionen bilanziert werden
seo-description: Liste aller APIs, die als Transaktionen bilanziert werden
uuid: d2f38ae4-75df-426f-af34-52ae6fb324f3
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 929a298d-7f22-487f-bf7d-8ab2556d0d81
docset: aem65
translation-type: tm+mt
source-git-commit: 5831c173114a5a6f741e0721b55d85a583e52f78

---


# Transaktionsberichte Abrechnungsfähige APIs{#transaction-reports-billable-apis}

AEM Forms bietet mehrere APIs zum Senden von Formularen, zum Verarbeiten von Dokumenten und zum Rendern von Dokumenten. Einige APIs werden als Transaktionen erfasst und andere können kostenlos verwendet werden. Dieses Dokument enthält eine Liste aller APIs, die in einem Transaktionsbericht als Transaktionen bilanziert werden. Im Folgenden finden Sie einige gängige Szenarien, in denen eine abrechnungsfähige API verwendet wird:

* Übermitteln eines adaptiven Formulars, HTML5-Formulars und Formularsatzes
* Rendern einer Druck- oder Webversion einer interaktiven Kommunikation
* Konvertieren eines Dokuments von einem Format in ein anderes
* Reduzieren eines dynamischen PDF-Dokuments
* Erstellen eines Datensatzdokuments
* Zusammenführen eines interaktiven PDF-Dokuments mit einem anderen PDF-Dokument
* Verwenden der Schritte zum Zuweisen von Aufgabenschritten und den DOC-Diensten von AEM-Workflows
* Verwenden von adaptiven Formularen in einem adaptiven Formular

Die Abrechnungs-APIs berücksichtigen nicht die Anzahl der Seiten, die Länge eines Dokuments oder Formulars oder das endgültige Format des wiedergegebenen Dokuments. Ein Transaktionsbericht unterteilt die Transaktionen in zwei Kategorien: Gerenderte Dokumente und gesendete Formulare

* **** Übermittelte Formulare: Wenn Daten von einem beliebigen mit AEM Forms erstellten Formulartyp gesendet werden und die Daten an ein Datenspeicher-Repository gesendet werden, gilt die Formularübermittlung. Beispielsweise werden beim Senden eines adaptiven Formulars, HTML5-Formulars, PDF-Formulare und Formularsätze als gesendete Formulare verbucht. Jedes Formular in einem Formularsatz gilt als Übermittlung. Wenn ein Formularsatz beispielsweise 5 Formulare umfasst, zählt der Transaktionsberichtsdienst ihn bei Übermittlung des Formularsatzes als 5 Übermittlungen.

* **** Gerenderte Dokumente: Das Generieren eines Dokuments durch Kombination von Vorlage und Daten, das digitale Signieren oder Zertifizieren eines Dokuments, die Verwendung einer abrechnungsfähigen Document Services-APIs für Document Services oder die Konvertierung eines Dokuments von einem Format in ein anderes werden als gerenderte Dokumente berücksichtigt.

>[!NOTE]
>
>Die Benutzeroberfläche &quot;Transaktionsberichte&quot;enthält drei Kategorien: Formulare gesendet, wiedergegebene Dokumente und verarbeitete Dokumente. Sowohl gerenderte als auch verarbeitete Dokumente werden als gerenderte Dokumente verbucht.

## Billable Document Services-APIs {#billable-document-services-apis}

### Generate PDF Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Konvertiert Adobe PDF in unterstützte Dateitypen. </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Konvertiert Adobe PDF in unterstützte Dateitypen. </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Konvertiert Adobe PDF in unterstützte Dateitypen. </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Erstellt PDF-Dateien aus HTML-Seiten.</p> </td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Erstellt PDF-Dateien aus URLs, die auf eine HTML-Seite verweisen.</td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Erstellt PDF-Dateien aus URLs, die auf eine HTML-Seite verweisen.</td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimiert PDF-Dateien, um die Dateigröße zu reduzieren, indem unnötige Metadaten entfernt werden, ohne die Qualität zu beeinträchtigen.</td>
   <td>Verarbeitete Dokumente<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Distiller Service {#distiller-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Erstellt Adobe PDF aus unterstützten Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Datensatzdokument-Dienst (DoR-Dienst) {#document-of-record-service-dor-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">render</a></td>
   <td>Ruft die angegebene Render-Methode auf, um ein Datensatzdokument mit den bereitgestellten Parametern zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Output Service {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PDFOutputOptions-" target="_blank">generatePDFOutput</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePDFOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PDFOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePDFOutputBatch</a></td>
   <td>Führt Daten und Vorlagen zusammen, um einen Satz von PDF-Dokumenten zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> Die generatePDFOutputBatch-API kombiniert eine Formularvorlage mit einem Datensatz und generiert eine PDF-Datei. Bei der Verarbeitung eines Datensatzstapels zählt der Transaktionsberichtsdienst jeden Datensatz als separate PDF-Darstellung. <br> Mit dem Flag <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> können Sie mehrere Darstellungen zu einer einzelnen PDF-Datei kombinieren. Unabhängig vom Status des Flag zählt der Dienst jeden Datensatz als separate PDF-Darstellung. </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Formate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutput-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.output.api.PrintedOutputOptions-" target="_blank">generatePrintedOutput</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Formate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/OutputService.html#generatePrintedOutputBatch-java.util.Map-java.util.Map-com.adobe.fd.output.api.PrintedOutputOptions-com.adobe.fd.output.api.BatchOptions-" target="_blank">generatePrintedOutputBatch</a></td>
   <td>Konvertiert eine Reihe von XDP- und PDF-Dokumenten in eine Reihe von PostScript- (PS), Printer Command Language (PCL)- und ZPL-Dateiformaten. </td>
   <td>Verarbeitete Dokumente</td>
   <td> Die generatePDFOutputBatch-API kombiniert eine Formularvorlage mit einem Datensatz und generiert eine PDF-Datei. Bei der Verarbeitung eines Datensatzstapels zählt der Transaktionsberichtsdienst jeden Datensatz als separate PDF-Darstellung. <br> Mit dem Flag <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> können Sie mehrere Darstellungen zu einer einzelnen PDF-Datei kombinieren. Unabhängig vom Status des Flag zählt der Dienst jeden Datensatz als separate PDF-Darstellung. </td>
  </tr>
 </tbody>
</table>

### Formularservice {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Rendert PDF-Formulare aus XDP-Vorlagen. Die XP-Vorlagen werden in Forms Designer erstellt.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extrahiert Daten aus einem PDF-Formular oder einer XDP-Vorlage</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Convert PDF Service {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Konvertiert ein PDF-Dokument in eine Liste von Bilddokumenten. Unterstützte Bildformate sind JPEG, JPEG2K, PNG und TIFF.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td>
   <td>Konvertiert eine einfache PDF-Datei in das PostScript-Format mit den in der Optionsangabe angegebenen Optionen.</td>
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
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td>
   <td>Dekodiert alle Barcodes in einem Dokumentobjekt und gibt ein Objekt "org.w3c.dom.Document"zurück, das Daten enthält, die aus dem Barcode abgerufen wurden.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Assembler-Dienst {#assembler-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-">invoke</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein <a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a> -Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Verarbeitete Dokumente</td>
   <td>Folgende Vorgänge werden nicht als Transaktionen erfasst:
    <ul>
     <li>Erstellen von Paketen oder Portfolios</li>
     <li>Mehrere XDPs anheften </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-" target="_blank">invoke</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein <a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a> -Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Verarbeitete Dokumente</td>
   <td>Der Assembler-Dienst unterstützt alle Eingabedateiformate, die von PDF Generator, Forms und Output-Diensten unterstützt werden, als Ausgabeformate. </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#toPDFA-com.adobe.aemfd.docmanager.Document-com.adobe.fd.assembler.client.PDFAConversionOptionSpec-">toPDFA</a></td>
   <td>Konvertieren Sie ein angegebenes Dokument mit den angegebenen Optionen in PDF/A.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Die invoke-API des Assembler-Dienstes kann intern abhängig von der Eingabe eine abrechnungsfähige API eines anderen Dienstes aufrufen. Die invoke-API kann also als keine, einzelne oder mehrere Transaktionen bilanziert werden. Die Anzahl der gezählten Transaktionen hängt von der Eingabe und den aufgerufen internen APIs ab.
>* Ein einzelnes mit Assembler-Dienst erstelltes PDF-Dokument kann als keine, einzelne oder mehrere Transaktionen bilanziert werden. Die Anzahl der gezählten Transaktionen hängt vom bereitgestellten DDX-Code ab.
>



### PDF-Dienstprogrammdienst {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td>
   <td>Konvertiert ein PDF-Dokument in eine XDP-Datei. Damit ein PDF-Dokument erfolgreich in eine XDP-Datei konvertiert werden kann, muss das PDF-Dokument einen XFA-Stream im AcroForm-Wörterbuch enthalten.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Billable Datenerfassungs-APIs {#billable-data-capture-apis}

Alle Übermittlungsereignisse von adaptiven Formularen, HTML5-Formularen und Formularsätzen werden als Transaktionen erfasst. Standardmäßig wird die Übermittlung eines PDF-Formulars nicht als Transaktion erfasst. Verwenden Sie die bereitgestellte [Transaktions-Recorder-API](transaction-reports-billable-apis.md#recordingbillableapisastransactionsforcustomcode) , um eine PDF-Formularübermittlung als Transaktion aufzuzeichnen.

### Adaptive Formulare {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Nutzungsszenario</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines adaptiven Formulars</td>
   <td>Sendet ein adaptives Formular zur konfigurierten Übermittlungsaktion. </td>
   <td>Übermittelte Formulare</td>
   <td>
    <ul>
     <li>Erfolgreiches Übermittlungskonto für ein oder zwei Transaktionen. Die Anzahl der gezählten Transaktionen hängt von der Art der Sendeaktion ab, die für die Übermittlung verwendet wird. Beispielsweise werden beim Senden von PDF per E-Mail-Übermittlungsaktion zwei Transaktionszahlen erfasst. Eine Transaktion für die Formularübermittlung und eine andere für mit dem DOR-Dienst generierte PDF. </li>
     <li>Bei Verwendung des adaptiven Formulars in einem adaptiven Formular (adaptiven Formularsatz) wird nur eine Transaktion erfasst. Sie können eine beliebige Anzahl adaptiver Formulare in einem adaptiven Formular haben.</li>
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
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines HTML5-Formulars</td>
   <td>Sendet ein HTML5-Formular, um die im Formular konfigurierte URL zu senden.</td>
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
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines Formularsatzes</td>
   <td>Sendet den Formularsatz an die im Formularsatz konfigurierte Sende-URL.</td>
   <td>Übermittelte Formulare</td>
   <td>
    <ul>
     <li>Bei Verwendung des adaptiven Formulars in einem adaptiven Formular (adaptiven Formularsatz) wird nur eine Transaktion erfasst. Sie können eine beliebige Anzahl adaptiver Formulare in einem adaptiven Formular haben.</li>
     <li>Jedes Formular in einem HTML5-Formularsatz wird als separate Transaktion behandelt. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Billable interaktive Kommunikation und formularorientierte AEM-Workflows auf OSGi-APIs {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Weisen Sie Aufgaben- und Document Services-Schritte für Form-orientierte AEM-Workflows auf OSGi und alle Darstellungen der interaktiven Kommunikation zu und werden als Transaktionen erfasst. Die Vorschau einer interaktiven Kommunikation auf der Autoreninstanz und die Vorschau auf der Veröffentlichungsinstanz mithilfe der Agent-Benutzeroberfläche werden nicht als Transaktionen erfasst. Wenn ein Workflow-Schritt eine Transaktion abschließt und der Workflow nicht abgeschlossen werden kann, wird die Transaktionsanzahl nicht umgekehrt.

### Webkanal für interaktive Kommunikation {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Rendern eines Webkanals</td>
   <td>Öffnet die Webversion einer interaktiven Kommunikation.</td>
   <td>Gerenderte Dokumente</td>
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
   <td>Beschreibung</td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (in PDF konvertieren)</td>
   <td>Generiert die PDF-Version einer interaktiven Kommunikation.</td>
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
   <td><p>Anwendungsfall
</p> </td>
   <td>Transaktionsberichtkategorie</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines Assign Task-Schritts</td>
   <td>Übermittelte Formulare</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Senden eines Startpunkts für eine Workflow-Anwendung </td>
   <td>Übermittelte Formulare</td>
   <td> </td>
  </tr>
  <tr>
   <td>Senden einer interaktiven Kommunikation (Druckkanal) von der Benutzeroberfläche des Agenten an einen Workflow</td>
   <td>Gerenderte Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Aufzeichnen von abrechnungsfähigen APIs als Transaktionen für benutzerdefinierten Code {#recording-billable-apis-as-transactions-for-custom-code}

Aktionen wie das Senden eines PDF-Formulars, die Verwendung der Agent-Benutzeroberfläche zum Anzeigen einer Vorschau einer interaktiven Kommunikation, das Senden von nicht standardmäßigen Formularen und benutzerdefinierte Implementierungen werden nicht als Transaktionen erfasst. AEM Forms bietet eine API zum Aufzeichnen von Aktionen wie Transaktionen. Sie können die API aus Ihren benutzerdefinierten Implementierungen aufrufen, um eine Transaktion [aufzuzeichnen](/help/forms/using/record-transaction-custom-implementation.md).

## Related Articles {#related-articles}

* [Übersicht über Transaktionsberichte](../../forms/using/transaction-reports-overview.md)
* [Anzeigen und Verstehen von Transaktionsberichten](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Eine Transaktion für benutzerdefinierte Implementierungen aufzeichnen](/help/forms/using/record-transaction-custom-implementation.md)

