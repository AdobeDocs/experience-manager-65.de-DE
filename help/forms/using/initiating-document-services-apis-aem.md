---
title: Starten Sie Document Services-APIs aus dem AEM-Arbeitsablauf
seo-title: Starten Sie Document Services-APIs aus dem AEM-Arbeitsablauf
description: Erfahren Sie, wie Sie AEM Document Services auf DDX aufrufen. Siehe auch „Konvertieren von PDF in PDF/A“
seo-description: Erfahren Sie, wie Sie AEM Document Services auf DDX aufrufen. Siehe auch „Konvertieren von PDF in PDF/A“
uuid: aacec2df-1ad6-4ff2-a99d-ef206efcdc09
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 8b85bdc7-3864-49c9-81b0-cf15b8e986d9
exl-id: 123087a2-9d09-4579-9185-2ccd7d25bf8d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 92%

---

# Starten Sie Document Services-APIs aus dem AEM-Arbeitsablauf  {#initiate-document-services-apis-from-aem-workflow}

## Assembler {#assembler}

AEM Forms bietet benutzerdefinierte Workflows zum Aufrufen der folgenden Assembler-Dienst-APIs:

* **invoke**: Ruft die Prozesse auf, die in der Eingabe-DDX bei gelieferten Eingaben angegeben wurden.
* **toPDFA**: Konvertiert Eingabe-PDF-Dokumente in PDF/A-Dokumente.

### Rufen Sie den DDX-Arbeitsablauf auf {#invoke-ddx-workflow}

Der Workflow **DDX aufrufen** ruft die `Invoke` Assembler-Dienst-API auf, die Sie zum Zusammenführen oder Aufteilen von Dokumenten, zum Hinzufügen von Wasserzeichen zu einer PDF-Datei usw. verwenden können.

1. Ziehen Sie **[!UICONTROL Invoke DDX]** auf der Registerkarte „Forms Workflow“ in den Sidekick.
1. Doppelklicken Sie auf „Hinzugefügt“, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Bearbeiten“ Input Documents, Environment Options und Output Documents und klicken Sie auf **[!UICONTROL OK]**.

#### Input Documents  {#input-documents}

Der Arbeitsablauf „Invoke DDX“ erfordert folgende Eingabedokumente:

* **DDX**: Ist eine obligatorische Eingabe für „Invoke DDX“ und kann angegeben werden, indem eine der folgenden Optionen aus der DDX-Eingabe-Dropdownliste ausgewählt wird.

   * *Relative To Payload*: Die DDX-Eingabedatei ist relativ zum Payload-Ordner für das Arbeitsablaufelement.
   * *Use Payload*: Die Payload für das Arbeitsablaufelement wird als DDX-Eingabedokument verwendet.
   * *Absoluter Path*: Der absolute Pfad zum DDX-Dokument im CRX-Repository.

* **Create Map from PayLoad**: Ist diese Option ausgewählt, werden alle Dokumente im Payload-Ordner zur Zuordnung des Eingabedokuments für die `invoke`-API im Assembler hinzugefügt. Der Knotenname für jedes Dokument wird als Schlüssel in der Zuordnung verwendet.

* **Input Document&#39;s Map**: Gibt die Zuordnung des Eingabedokuments an. Sie können beliebig viele Einträge hinzufügen, wobei jeder Eintrag den Schlüssel des Dokuments in der Zuordnung und die Quelle des Dokuments angibt.

#### Environment Options {#environment-options}

Auf der Registerkarte „Environment Options“ können Sie die verschiedenen Verarbeitungsoptionen für die invoke-API festlegen.

* *Job Log Level*: Gibt die Protokollebene für die Verarbeitungsprotokolle an.
* *Validate Only*: Prüft die Gültigkeit der Eingabe-DDX.

* *Fail On Error*: Gibt an, ob der Aufruf an den Assembler-Dienst im Falle eines Fehlers fehlschlagen soll. Der Standardwert ist „False“.

#### Output Documents {#output-documents}

Je nach Eingabe-DDX kann das invoke-API mehrere Ausgabe-Dokumente erstellen. Auf der Registerkarte „Output Documents“ können Sie festlegen, wo Output Documents gespeichert werden.

1. *Save Output in Payload*: Speichert Ausgabedokumente im Payload-Ordner oder überschreibt die Payload, wenn es sich bei der Payload um eine Datei handelt.
1. *Output Document&#39;s Map*: Hiermit können Sie explizit angeben, wo jedes output document gespeichert werden soll, indem ein Eintrag pro output document hinzugefügt wird. Jeder Eintrag gibt das Dokument und den entsprechenden Speicherort an. Ein Output Document kann die Payload überschreiben oder im Payload-Ordner speichern. Dies ist nützlich, wenn es mehrere Output Documents gibt.

1. *Job Log*: Gibt an, wo das Auftragsprotokolldokument gespeichert werden soll, was bei Fehlerbehebungsfehlern hilfreich sein kann.

### Arbeitsablauf „Nach PDF/A konvertieren“  {#convert-to-pdf-a-workflow}

Die Option „Nach PDF/A konvertieren“ ruft die `toPDFA`-Assembler-Dienst-API auf. Sie wird zum Konvertieren von PDF-Dokumenten in PDF/A-kompatible Dokumente verwendet.

1. Ziehen Sie **[!UICONTROL ConvertToPDFA]** auf der Registerkarte „Forms Workflow“ in den Sidekick.

1. Doppelklicken Sie auf „Hinzugefügt“, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Bearbeiten“ Input Documents, Conversion Options und Output Documents und klicken Sie auf **[!UICONTROL OK]**.

#### Input Documents  {#input-documents-1}

Geben Sie die Quelle des Dokuments, das in ein PDF/A-kompatibles Dokument konvertiert werden soll, auf folgende Art an.

* *Relative To Payload*: Das Eingabedokument ist relativ zum Payload-Ordner für das Arbeitsablaufelement. 
* *Use Payload*: Die Payload für das Arbeitsablaufelement wird als Eingabedokument verwendet.
* *Absolute Path*: Der absolute Pfad des Eingabedokuments im CRX-Repository.

#### Conversion Options {#conversion-options}

Mithilfe der Konvertierungsoptionen können Sie Optionen festlegen, die den Vorgang der PDF/A- Konvertierung ändern.

* *Compliance*: Gibt den PDF/A-Standard an, mit dem die Ausgabe-PDF/A kompatibel sein muss.
* *Result Level*: Gibt die Protokollebene, die für die PDF/A-Konvertierungsprotokolle verwendet werden soll, an.
* *Signatures*: Gibt an, wie die Signaturen im Eingabedokument während der Konvertierung verarbeitet werden müssen.
* *Color Space*: Gibt den vordefinierten Farbraum, der für das PDF/A-Dokument verwendet werden soll, an.
* ** VerifyConversion: Gibt an, ob das konvertierte PDF/A-Dokument nach der Konvertierung auf PDF/A-Konformität überprüft werden soll.
* *Job Log Level*: Gibt die Protokollebene, die für die Verarbeitung von Protokollen verwendet werden soll, an.

* *Metadata Extension Schema*: Gibt den Pfad zum Metadaten-Erweiterungsschema, der für XMP-Eigenschaften in den Metadaten des PDF-Dokuments verwendet werden soll, an.

#### Output Documents {#output-documents-1}

Auf der Registerkarte „Output Documents“ können Sie das Ziel für die Output Documents angeben

* *PDFA-Dokument*: Gibt den Ort an, an dem das konvertierte PDF/A-Dokument gespeichert wird. Es kann entweder das Payload-Dokument überschreiben oder im Payload-Ordner gespeichert werden.
* *Conversion Log*: Gibt den Ort an, an dem die Konvertierungsprotokolle gespeichert werden. Es kann entweder das Payload-Dokument überschreiben oder im Payload-Ordner gespeichert werden.

## Formulare {#forms}

Der Arbeitsablauf zum Rendern von PDF-Formularen ist ein Wrapper um die Formulardienst-API `renderPDFForm`, um ein PDF-Formular mit einer XDP-Vorlage und Daten-XML zu erstellen.

### Arbeitsablauf zum Rendern von PDF-Formularen {#render-pdf-form-workflow}

1. Ziehen Sie den Arbeitsablauf zum Rendern von PDF-Formularen unter der Registerkarte „Forms Workflow“ in den Sidekick.
1. Doppelklicken Sie auf „Hinzugefügt“, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Bearbeiten“ Input Documents, Output Documents und zusätzlichen Parameter und klicken Sie auf **[!UICONTROL OK]**.

#### Input Documents  {#input-documents-2}

* *Template File*: Gibt den Speicherort der XDP-Vorlage an. Dies ist ein Pflichtfeld.

* *Data Document*: Gibt den Ort der Daten-XML an, die mit der Vorlage zusammengeführt werden muss.

#### Output Documents {#output-documents-2}

* *Output Document*: Gibt den Namen des erstellten PDF-Formulars an.

#### Additional Parameters  {#additional-parameters}

* *Content Root*: Gibt den Pfad zum Ordner im Repository an, in dem die Fragmente oder Bilder, die in der Eingabe-XDP-Vorlage verwendet wurden, gespeichert werden.
* *Submit Url*: Gibt die Standard-URL zum Übermitteln für das erstellte PDF-Formular an.
* *Locale*: Gibt das Gebietsschema für das erstellte PDF-Formular an.
* *Acrobat-Version*: Gibt die vorgesehene Acrobat-Version für das erstellte PDF-Formular an.
* *Tagged PDF*: Gibt an, ob die erstellten PDF-Dateien barrierefrei gemacht werden.
* *XCI document*: Gibt den Pfad zur XCI-Datei an.

## Ausgabe {#output}

Der Arbeitsablauf „Nicht-interaktive PDF generieren“ ist ein Wrapper um die Ausgabe-Dienst-API `generatePDFOutput`. Er wird verwendet, um nicht-interaktive PDF-Dokumente aus der XDP-Vorlage und der Daten-XML zu generieren.

### Arbeitsablauf „Nicht-interaktive PDF-Ausgabe generieren“  {#generate-non-interactive-pdf-output-workflow-nbsp}

1. Ziehen Sie den Arbeitsablauf „Nicht-interaktive PDF-Ausgabe generieren“ auf der Registerkarte „Forms Workflow“ in den Sidekick.
1. Doppelklicken Sie auf „Hinzugefügt“, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Bearbeiten“ Input Documents, Output Documents und zusätzlichen Parameter und klicken Sie auf **[!UICONTROL OK]**.

#### Input Documents  {#input-documents-3}

* *Template File*: Gibt den Speicherort der XDP-Vorlage an. Dies ist ein Pflichtfeld.

* *Data Document*: Gibt den Ort der Daten-XML an, die mit der Vorlage zusammengeführt werden muss.

#### Output Document {#output-document}

*Output Document*: Gibt den Namen des erstellten PDF-Formulars an.

#### Additional Parameters  {#additional-parameters-1}

* *Content Root*: Gibt den Pfad zum Ordner im Repository an, in dem die Fragmente oder Bilder, die in der Eingabe-XDP-Vorlage verwendet wurden, gespeichert werden.
* *Locale*: Gibt das Standard-Gebietsschema für das erstellte PDF-Formular an.
* *Acrobat-Version*: Gibt die vorgesehene Acrobat-Version für das erstellte PDF-Formular an.
* Linearized PDF: Gibt an, ob die generierte PDF-Datei für Webanzeige optimiert werden soll.
* *Tagged PDF*: Gibt an, ob die erstellten PDF-Dateien barrierefrei gemacht werden.
* *XCI document*: Gibt den Pfad zur XCI-Datei an.
