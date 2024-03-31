---
title: Starten von Document Services-APIs aus dem AEM-Workflow
description: Erfahren Sie, wie Sie die AEM-Dokumentendienste mit DDX oder bereitgestellten Eingaben aufrufen können. Weitere Informationen finden Sie unter „Konvertieren von PDF in PDF/A“
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
exl-id: 123087a2-9d09-4579-9185-2ccd7d25bf8d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 100%

---

# Starten Sie Document Services-APIs aus dem AEM-Arbeitsablauf  {#initiate-document-services-apis-from-aem-workflow}

## Assembler {#assembler}

AEM Forms bietet benutzerdefinierte Workflows, um die folgenden Assembler Service-APIs aufzurufen:

* **invoke**: Ruft Vorgänge auf, die in Eingabe-DDX für bereitgestellte Eingaben angegeben wurden.
* **toPDFA**: Konvertiert ein PDF-Eingabedokument in ein PDF/A-Dokument.

### Aufrufen eines DDX-Workflows {#invoke-ddx-workflow}

Der Workflow **DDX aufrufen** ruft die Assembler Service-API `Invoke` auf, mit der Sie Dokumente zusammenstellen oder aufteilen, ein Wasserzeichen zu einem PDF hinzufügen können usw.

1. Ziehen Sie **[!UICONTROL Invoke DDX]** auf der Registerkarte „Forms Workflow“ in den Sidekick.
1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Komponente bearbeiten“ die Eingabedokumente, Umgebungsoptionen und Ausgabedokumente und klicken Sie auf **[!UICONTROL OK]**.

#### Eingabedokumente {#input-documents}

Der Workflow „Invoke DDX“ erfordert folgende Eingabedokumente:

* **DDX**: Dies ist eine obligatorische Eingabe für den Workflow-Schritt „Invoke DDX“ und kann durch Auswahl einer der folgenden Optionen in der DDX-Eingabe-Dropdown-Liste angegeben werden.

   * *Relative To Payload*: Die DDX-Eingabedatei ist relativ zum Payload-Ordner für das Arbeitsablaufelement.
   * *Nutzlast verwenden*: Die Nutzlast für das Workflow-Element wird als DDX-Eingabedokument verwendet.
   * *Absoluter Pfad*: Der absolute Pfad zum DDX-Dokument im CRX-Repository.

* **Create Map from PayLoad**: Ist diese Option ausgewählt, werden alle Dokumente im Payload-Ordner zur Zuordnung des Eingabedokuments für die `invoke`-API im Assembler hinzugefügt. Der Knotenname für jedes Dokument wird als Schlüssel in der Zuordnung verwendet.

* **Zuordnung des Eingabedokuments**: Legt die Zuordnung des Eingabedokuments fest. Sie können beliebig viele Einträge hinzufügen, wobei jeder Eintrag den Schlüssel des Dokuments in der Zuordnung und die Quelle des Dokuments angibt.

#### Umgebungsoptionen {#environment-options}

Auf der Registerkarte „Umgebungsoptionen“ können Sie verschiedene Verarbeitungsoptionen für die aufrufende API festlegen.

* *Vorgangslog-Stufe*: Gibt die Protokollebene für die Verarbeitungsprotokolle an.
* *Validate Only*: Prüft die Gültigkeit der Eingabe-DDX.

* *Bei Fehler abbrechen*: Gibt an, ob der Aufruf an den Assembler-Dienst bei einem Fehler fehlschlagen soll. Der Standardwert ist „False“.

#### Ausgabedokumente {#output-documents}

Je nach Eingabe-DDX kann die aufrufende API mehrere Ausgabedokumente erstellen. Auf der Registerkarte der Ausgabedokumente können Sie auswählen, wo das Ausgabedokument gespeichert werden soll.

1. *Ausgabe in Payload speichern*: Speichert Ausgabedokumente unter dem Payload-Ordner oder überschreibt die Payload, wenn die Payload eine Datei ist.
1. *Ausgabedokumentzuordnung*: Lässt Sie explizit angeben, wo jedes Ausgabedokument gespeichert werden soll, indem ein Eintrag pro Ausgabedokument hinzugefügt wird. Jeder Eintrag gibt das Dokument an und wo es gespeichert werden soll. Ein Output Document kann die Payload überschreiben oder im Payload-Ordner speichern. Dies ist nützlich, wenn es mehrere Output Documents gibt.

1. *Vorgangslog*: Gibt an, wo das Vorgangslogdokument gespeichert werden soll. Dies ist bei der Fehlerbehebung hilfreich.

### Workflow „Nach PDF/A konvertieren“ {#convert-to-pdf-a-workflow}

Die Option „Nach PDF/A konvertieren“ ruft die `toPDFA`-Assembler-Dienst-API auf. Sie wird zum Konvertieren von PDF-Dokumenten in PDF/A-kompatible Dokumente verwendet.

1. Ziehen Sie **[!UICONTROL ConvertToPDFA]** auf der Registerkarte „Forms Workflow“ in den Sidekick.

1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Komponente bearbeiten“ Eingabedokumente, Konvertierungsoptionen und Ausgabedokumente und klicken Sie auf **[!UICONTROL OK]**.

#### Eingabedokumente {#input-documents-1}

Geben Sie die Quelle des Dokuments, das in ein PDF/A-konformes Dokument konvertiert werden soll, auf eine der folgenden Arten an.

* *Relativ zur Nutzlast*: Das Eingabedokument ist relativ zum Payload-Ordner für das Workflow-Element.
* *Nutzlast verwenden*: Das Payload für das Workflow-Element wird als Eingabedokument verwendet.
* *Absolute Path*: Der absolute Pfad des Eingabedokuments im CRX-Repository.

#### Konvertierungsoptionen {#conversion-options}

Mit den Konvertierungsoptionen können Sie Optionen angeben, die den PDF/A-Konvertierungsprozess ändern.

* *Compliance*: Gibt den PDF/A-Standard an, mit dem die Ausgabe des PDF/A-Dokuments kompatibel sein muss.
* *Result Level*: Gibt die Protokollebene, die für die PDF/A-Konvertierungsprotokolle verwendet werden soll, an.
* *Signaturen* : Gibt an, wie die Signaturen im Eingabedokument bei der Konvertierung verarbeitet werden müssen.
* *Farbraum* : Gibt den vordefinierten Farbraum an, der für das PDF/A-Ausgabedokument verwendet werden soll.
* *Konvertierung überprüfen*: Gibt an, ob das konvertierte PDF/A-Dokument nach der Konvertierung auf PDF/A-Konformität geprüft werden soll.
* *Job Log Level*: Gibt die Protokollebene, die für die Verarbeitung von Protokollen verwendet werden soll, an.

* *Metadata Extension Schema*: Gibt den Pfad zum Metadaten-Erweiterungsschema, der für XMP-Eigenschaften in den Metadaten des PDF-Dokuments verwendet werden soll, an.

#### Ausgabedokumente {#output-documents-1}

Auf der Registerkarte für Ausgabedokumente können Sie das Ziel für die Ausgabedokumente angeben

* *PDFA Document*: Gibt den Speicherort an, an dem das konvertierte PDF/A-Dokument gespeichert wird. Es kann entweder das Payload-Dokument überschreiben oder im Payload-Ordner gespeichert werden.
* *Conversion Log*: Gibt den Ort an, an dem die Konvertierungsprotokolle gespeichert werden. Es kann entweder das Payload-Dokument überschreiben oder im Payload-Ordner gespeichert werden.

## Formulare {#forms}

Der Arbeitsablauf zum Rendern von PDF-Formularen ist ein Wrapper um die Formulardienst-API `renderPDFForm`, um ein PDF-Formular mit einer XDP-Vorlage und Daten-XML zu erstellen.

### Workflow zum Rendern von PDF-Formularen {#render-pdf-form-workflow}

1. Ziehen Sie den Workflow zum Rendern von PDF-Formularen unter der Registerkarte „Forms Workflow“ in den Sidekick.
1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Komponente bearbeiten“ Eingabedokumente, Ausgabedokumente und zusätzliche Parameter und klicken Sie auf **[!UICONTROL OK]**.

#### Eingabedokumente {#input-documents-2}

* *Vorlagendatei*: Gibt den Speicherort der XDP-Vorlage an. Dies ist ein Pflichtfeld.

* *Datendokument*: Gibt den Speicherort der Daten-XML an, die mit der Vorlage zusammengeführt werden muss.

#### Ausgabedokumente {#output-documents-2}

* *Ausgabedokument*: Gibt den Namen des generierten PDF-Formulars an.

#### Zusätzliche Parameter {#additional-parameters}

* *Inhaltsstamm*: Gibt den Pfad zum Ordner im Repository an, in dem in der Eingabe-XDP-Vorlage verwendete Fragmente oder Bilder gespeichert werden.
* *Sende-URL*: Gibt die Standard-URL für die Übermittlung des generierten PDF-Formulars an.
* *Gebietsschema*: Gibt das Standardgebietsschema für das generierte PDF-Formular an.
* *Acrobat-Version*: Gibt die Acrobat-Zielversion für das generierte PDF-Formular an.
* *PDF mit Tags*: Gibt an, ob die generierte PDF-Datei barrierefrei gemacht werden soll.
* *XCI-Dokument*: Gibt den Pfad zur XCI-Datei an.

## Ausgabe {#output}

Der Arbeitsablauf „Nicht-interaktive PDF generieren“ ist ein Wrapper um die Ausgabe-Dienst-API `generatePDFOutput`. Er wird verwendet, um nicht-interaktive PDF-Dokumente aus der XDP-Vorlage und der Daten-XML zu generieren.

### Workflow „Nicht-interaktive PDF-Ausgabe generieren“ {#generate-non-interactive-pdf-output-workflow-nbsp}

1. Ziehen Sie den Workflow „Nicht-interaktive PDF-Ausgabe generieren“ unter die Registerkarte „Forms Workflow“ per Drag-and-Drop in den Sidekick.
1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Komponente bearbeiten“ Eingabedokumente, Ausgabedokumente und zusätzliche Parameter und klicken Sie auf **[!UICONTROL OK]**.

#### Eingabedokumente {#input-documents-3}

* *Vorlagendatei*: Gibt den Speicherort der XDP-Vorlage an. Dies ist ein Pflichtfeld.

* *Datendokument*: Gibt den Speicherort der Daten-XML an, die mit der Vorlage zusammengeführt werden muss.

#### Ausgabedokument {#output-document}

*Ausgabedokument*: Gibt den Namen des generierten PDF-Formulars an.

#### Zusätzliche Parameter {#additional-parameters-1}

* *Inhaltsstamm*: Gibt den Pfad zum Ordner im Repository an, in dem in der Eingabe-XDP-Vorlage verwendete Fragmente oder Bilder gespeichert werden.
* *Gebietsschema*: Gibt das Standardgebietsschema für das generierte PDF-Formular an.
* *Acrobat-Version*: Gibt die Acrobat-Zielversion für das generierte PDF-Formular an.
* Linearisierte PDF: Gibt an, ob die generierte PDF-Datei für die Ansicht im Web optimiert werden soll.
* *PDF mit Tags*: Gibt an, ob die generierte PDF-Datei barrierefrei gemacht werden soll.
* *XCI-Dokument*: Gibt den Pfad zur XCI-Datei an.
