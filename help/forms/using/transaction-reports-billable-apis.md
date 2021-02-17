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
source-git-commit: 13016df927448d93af86899f746199e1815fdfe7
workflow-type: tm+mt
source-wordcount: '1963'
ht-degree: 9%

---


# Transaktionsberichte Abrechnungsfähige APIs{#transaction-reports-billable-apis}

AEM Forms bietet mehrere APIs zum Senden von Formularen, zum Verarbeiten von Dokumenten und zum Rendern von Dokumenten. Einige APIs werden als Transaktionen erfasst und andere können kostenlos verwendet werden. Dieses Dokument bietet eine Liste aller APIs, die in einem Transaktionsbericht als Transaktionen bilanziert werden. Im Folgenden finden Sie einige gängige Szenarien, in denen eine abrechnungsfähige API verwendet wird:

* Übermitteln eines adaptiven Formulars, HTML5-Formulars und Formularsatzes
* Wiedergabe einer Druck- oder Webversion einer interaktiven Kommunikation
* Konvertieren eines Dokuments von einem Format in ein anderes
* Reduzieren eines dynamischen PDF-Dokuments
* Erstellen eines Dokuments aus Datensatz
* Zusammenführen eines interaktiven PDF-Dokuments mit einem anderen PDF-Dokument
* Verwenden der Schritte zum Zuweisen der Aufgabe und des Dokumentendiensts von AEM Workflows
* Verwenden von adaptiven Formularen in einem adaptiven Formular

Die Abrechnungs-APIs berücksichtigen nicht die Anzahl der Seiten, die Länge eines Dokuments oder Formulars oder das endgültige Format des gerenderten Dokuments. Ein Transaktionsbericht unterteilt die Transaktionen in zwei Kategorien: Dokumente gerendert und Forms gesendet.

* **Forms gesendet:** Wenn Daten von einem beliebigen mit AEM Forms erstellten Formulartypen gesendet werden und die Daten an ein Datenspeicher gesendet werden, gilt dies als Formularübermittlung. Beispielsweise werden das Senden eines adaptiven Formulars, HTML5-Formulars, PDF forms und Formularsätze als gesendete Formulare verbucht. Jedes Formular in einem Formularsatz gilt als Übermittlung. Wenn ein Formularsatz beispielsweise 5 Formulare enthält, zählt der Berichte-Dienst ihn beim Senden des Formularsatzes als 5 Übermittlungen.

* **Gerenderte Dokumente:** Generieren eines Dokuments durch Kombinieren einer Vorlage und von Daten, digitale Unterzeichnung oder Zertifizierung eines Dokuments, Verwendung einer abrechnungsfähigen Dokument Services APIs für Dokument-Services oder Konvertieren eines Dokuments von einem Format in ein anderes werden als gerenderte Dokumente erfasst.

>[!NOTE]
>
>Die Benutzeroberfläche &quot;Transaktionsberichte&quot;enthält drei Kategorien: Forms gesendet, gerenderte Dokumente und verarbeitete Dokumente. Sowohl gerenderte Dokumente als auch verarbeitete Dokumente werden als gerenderte Dokumente erfasst.

## Billable Dokument Services APIs {#billable-document-services-apis}

### Generieren des PDF-Dienstes {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
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
   <td>Kategorie des Transaktionsberichts</td>
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

### Dokument of Record Service (DoR Service) {#document-of-record-service-dor-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/addon/dor/DoRService.html#render-com.adobe.aemds.guide.addon.dor.DoROptions-" target="_blank">render</a></td>
   <td>Ruft die angegebene Render-Methode auf, um ein Dokument aus Datensatz mit den bereitgestellten Parametern zu generieren.</td>
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
   <td>Kategorie des Transaktionsberichts</td>
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
   <td> Die generatePDFOutputBatch-API kombiniert eine Formularvorlage mit einem Datensatz und generiert eine PDF-Datei. Wenn Sie einen Datensatzstapel verarbeiten, zählt der Transaktions-Berichte-Dienst jeden Datensatz als separate PDF-Darstellung. <br> Sie können das Flag  <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--"></a> getGenerateManyFilesFlag verwenden, um mehrere Darstellungen zu einer einzelnen PDF-Datei zu kombinieren. Unabhängig vom Status des Flag zählt der Dienst jeden Datensatz als separate PDF-Darstellung. </td>
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
   <td> Die generatePDFOutputBatch-API kombiniert eine Formularvorlage mit einem Datensatz und generiert eine PDF-Datei. Wenn Sie einen Datensatzstapel verarbeiten, zählt der Transaktions-Berichte-Dienst jeden Datensatz als separate PDF-Darstellung. <br> Sie können das Flag  <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--"></a> getGenerateManyFilesFlag verwenden, um mehrere Darstellungen zu einer einzelnen PDF-Datei zu kombinieren. Unabhängig vom Status des Flag zählt der Dienst jeden Datensatz als separate PDF-Darstellung. </td>
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
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Konvertiert ein PDF-Dokument in eine Liste von Dokumenten. Unterstützte Bildformate sind JPEG, JPEG2K, PNG und TIFF.</td>
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
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td>
   <td>Dekodiert alle Barcodes in einem Dokument-Objekt und gibt ein Objekt "org.w3c.dom.Dokument"zurück, das Daten enthält, die aus dem Barcode abgerufen wurden.</td>
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
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-">invoke</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein <a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a>-Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Verarbeitete Dokumente</td>
   <td>Folgende Vorgänge werden nicht als Transaktionen erfasst:
    <ul>
     <li>Erstellen von Paketen oder Portfolios</li>
     <li>Mehrere XDPs anheften </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#invoke-com.adobe.aemfd.docmanager.Document-java.util.Map-com.adobe.fd.assembler.client.AssemblerOptionSpec-" target="_blank">invoke</a></td>
   <td>Führt das angegebene DDX-Dokument aus und gibt ein <a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/fd/assembler/client/AssemblerResult.html">AssemblerResult</a>-Objekt zurück, das die resultierenden Dokumente enthält. </td>
   <td>Verarbeitete Dokumente</td>
   <td>Der Assembler-Dienst unterstützt alle Eingabedateiformate, die von PDF Generator, Forms und Output unterstützt werden, als Ausgabeformate. </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/assembler/service/AssemblerService.html#toPDFA-com.adobe.aemfd.docmanager.Document-com.adobe.fd.assembler.client.PDFAConversionOptionSpec-">toPDFA</a></td>
   <td>Konvertieren Sie ein angegebenes Dokument mithilfe der angegebenen Optionen in PDF/A.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Die invoke-API des Assembler-Dienstes kann intern abhängig von der Eingabe eine abrechnungsfähige API eines anderen Dienstes aufrufen. Die invoke-API kann also als keine, einzelne oder mehrere Transaktionen bilanziert werden. Die Anzahl der gezählten Transaktionen hängt von der Eingabe und den aufgerufen internen APIs ab.
>* Ein einzelnes mit Assembler-Dienst erstelltes PDF-Dokument kann als keine, einzelne oder mehrere Transaktionen erfasst werden. Die Anzahl der gezählten Transaktionen hängt vom bereitgestellten DDX-Code ab.

>



### PDF Utility Service {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
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

Alle Ereignisse zum Senden von adaptiven Formularen, HTML5-Forms und Formularsätzen werden als Transaktionen erfasst. Standardmäßig wird die Übermittlung eines PDF-Formulars nicht als Transaktion erfasst. Verwenden Sie die bereitgestellte [Transaktions-Recorder-API](record-transaction-custom-implementation.md), um eine Übermittlung von PDF forms als Transaktion aufzuzeichnen.

### Adaptive Formulare {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Nutzungsszenario </p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines adaptiven Formulars</td>
   <td>Sendet ein adaptives Formular zur konfigurierten Übermittlungsaktion. </td>
   <td>Übermittelte Formulare</td>
   <td>
    <ul>
     <li>Erfolgreiches Übermittlungskonto für ein oder zwei Transaktionen. Die Anzahl der gezählten Transaktionen hängt von der Art der Sendeaktion ab, die für die Übermittlung verwendet wird. Beispielsweise werden beim Senden von PDF per E-Mail-Übermittlungsaktion zwei Transaktionszahlen erfasst. Eine Transaktion für die Formularübermittlung und eine andere für mit dem Dokument of Record (DOR)-Dienst generierte PDF. </li>
     <li>Bei Verwendung des adaptiven Formulars in einem adaptiven Formular (adaptiven Formularsatz) wird nur eine Transaktion erfasst. Sie können eine beliebige Anzahl adaptiver Formulare in einem adaptiven Formular haben.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### HTML5-Formulare {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Nutzungsszenario </p> </td>
   <td>Beschreibung </td>
   <td>Kategorie des Transaktionsberichts</td>
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
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines Formularsatzes</td>
   <td>Sendet den Formularsatz an die im Formularsatz konfigurierte Sende-URL.</td>
   <td>Übermittelte Formulare</td>
   <td>
    <ul>
     <li>Bei Verwendung des adaptiven Formulars in einem adaptiven Formular (adaptiven Formularsatz) wird nur eine Transaktion erfasst. Sie können eine beliebige Anzahl adaptiver Formulare in einem adaptiven Formular haben.</li>
     <li>Jedes Formular in einem HTML5-Forms-Formularsatz wird als separate Transaktion behandelt. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Billable interaktive Kommunikation und formularzentrierte AEM Workflows für OSGi-APIs {#billable-interactive-communication-and-form-centric-aem-workflows-on-osgi-apis}

Weisen Sie Aufgabe- und Dokument-Services-Schritte für Form-zentrierte AEM auf OSGi und alle Darstellungen der interaktiven Kommunikation zu und werden als Transaktionen erfasst. Die Vorschau einer interaktiven Kommunikation auf der Autoreninstanz und die Vorschau auf der Veröffentlichungsinstanz mithilfe der Agent-Benutzeroberfläche werden nicht als Transaktionen erfasst. Wenn ein Workflow-Schritt eine Transaktion abschließt und der Workflow nicht abgeschlossen werden kann, wird die Transaktionsanzahl nicht umgekehrt.

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
   <td>Wiedergeben eines Web-Kanals</td>
   <td>Öffnet die Webversion einer interaktiven Kommunikation.</td>
   <td>Gerenderte Dokumente</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interaktive Kommunikation - Kanal drucken {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a>  (in PDF konvertieren)</td>
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
   <td><p>Anwendungsfall</p> </td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Übermitteln einer Aufgabe zuweisen</td>
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
   <td>Senden einer interaktiven Kommunikation (Print Kanal) von der Benutzeroberfläche des Agenten an einen Workflow</td>
   <td>Gerenderte Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Aufzeichnen von abrechnungsfähigen APIs als Transaktionen für benutzerdefinierten Code {#recording-billable-apis-as-transactions-for-custom-code}

Aktionen wie das Senden eines PDF-Formulars, die Verwendung der Agent-Benutzeroberfläche zur Vorschau einer interaktiven Kommunikation, die Verwendung nicht standardmäßiger Formularübermittlung und benutzerdefinierte Implementierungen werden nicht als Transaktionen erfasst. AEM Forms stellt eine API zur Aufzeichnung von Aktionen wie Transaktionen bereit. Sie können die API aus Ihren benutzerdefinierten Implementierungen aufrufen, um [eine Transaktion](/help/forms/using/record-transaction-custom-implementation.md) aufzuzeichnen.

## Verwandte Artikel {#related-articles}

* [Übersicht über Transaktionsberichte](../../forms/using/transaction-reports-overview.md)
* [Anzeigen und Verstehen von Transaktionsberichten](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Eine Transaktion für benutzerdefinierte Implementierungen aufzeichnen](/help/forms/using/record-transaction-custom-implementation.md)

