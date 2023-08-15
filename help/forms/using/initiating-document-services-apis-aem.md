---
title: Starten von Document Services-APIs aus dem AEM-Workflow
seo-title: Initiate Document Services APIs from AEM Workflow
description: Erfahren Sie, wie Sie Document Services AEM DDX oder bereitgestellte Eingaben aufrufen. Weitere Informationen finden Sie unter Konvertieren von PDF in PDF/A
seo-description: Learn how to invoke AEM Document services on DDX or supplied inputs. Also see hwo to convert PDF to PDF/A
uuid: aacec2df-1ad6-4ff2-a99d-ef206efcdc09
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 8b85bdc7-3864-49c9-81b0-cf15b8e986d9
exl-id: 123087a2-9d09-4579-9185-2ccd7d25bf8d
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 56%

---

# Starten Sie Document Services-APIs aus dem AEM-Arbeitsablauf  {#initiate-document-services-apis-from-aem-workflow}

## Assembler {#assembler}

AEM Forms bietet benutzerdefinierte Workflows, um die folgenden Assembler Service-APIs aufzurufen:

* **invoke**: Ruft Vorgänge auf, die in Eingabe-DDX für bereitgestellte Eingaben angegeben sind.
* **toPDFA**: Konvertiert ein PDF-Eingabedokument in ein PDF/A-Dokument.

### DDX-Workflow aufrufen {#invoke-ddx-workflow}

Der Workflow **DDX aufrufen** ruft die Assembler Service-API `Invoke` auf, mit der Sie Dokumente zusammenstellen oder aufteilen, ein Wasserzeichen zu einem PDF hinzufügen können usw.

1. Ziehen Sie die **[!UICONTROL DDX aufrufen]** Workflow-Schritt auf der Registerkarte Forms Workflow unter Sidekick.
1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld &quot;Komponente bearbeiten&quot;Eingabedokumente, Umgebungsoptionen und Ausgabedokumente und klicken Sie auf **[!UICONTROL OK]**.

#### Eingabedokumente {#input-documents}

Der Workflow &quot;Invoke DDX&quot;erfordert die folgenden Eingabedokumente:

* **DDX**: Dies ist eine obligatorische Eingabe für den Workflow-Schritt &quot;DDX aufrufen&quot;und kann durch Auswahl einer der folgenden Optionen aus der DDX-Eingabe-Dropdown-Liste angegeben werden.

   * *Relative To Payload*: Die DDX-Eingabedatei ist relativ zum Payload-Ordner für das Arbeitsablaufelement.
   * *Nutzlast verwenden*: Die Payload für das Workflow-Element wird als DDX-Eingabedokument verwendet.
   * *Absoluter Pfad*: Der absolute Pfad zum DDX-Dokument im CRX-Repository.

* **Create Map from PayLoad**: Ist diese Option ausgewählt, werden alle Dokumente im Payload-Ordner zur Zuordnung des Eingabedokuments für die `invoke`-API im Assembler hinzugefügt. Der Knotenname für jedes Dokument wird als Schlüssel in der Zuordnung verwendet.

* **Zuordnung des Eingabedokuments**: Legt die Zuordnung des Eingabedokuments fest. Sie können beliebig viele Einträge hinzufügen, wobei jeder Eintrag den Schlüssel des Dokuments in der Zuordnung und die Quelle des Dokuments angibt.

#### Umgebungsoptionen {#environment-options}

Auf der Registerkarte &quot;Umgebungsoptionen&quot;können Sie verschiedene Verarbeitungsoptionen für die invoke-API festlegen.

* *Job Log Level*: Gibt die Protokollebene für die Verarbeitungslogs an.
* *Validate Only*: Prüft die Gültigkeit der Eingabe-DDX.

* *Fehler bei Fehler*: Gibt an, ob der Aufruf des Assembler-Dienstes im Fall eines Fehlers fehlschlagen soll. Der Standardwert ist False.

#### Output Documents {#output-documents}

Je nach Eingabe-DDX kann die invoke-API mehrere Ausgabedokumente erstellen. Auf der Registerkarte &quot;Output Documents&quot;können Sie auswählen, wo das Ausgabedokument gespeichert werden soll.

1. *Ausgabe in Payload speichern*: Speichert Ausgabedokumente unter dem Payload-Ordner oder überschreibt die Payload, wenn die Payload eine Datei ist.
1. *Output Document&#39;s Map*: Hiermit können Sie explizit angeben, wo jedes output document gespeichert werden soll, indem ein Eintrag pro output document hinzugefügt wird. Jeder Eintrag gibt das Dokument an und wo es gespeichert werden soll. Ein Output Document kann die Payload überschreiben oder im Payload-Ordner speichern. Dies ist nützlich, wenn es mehrere Output Documents gibt.

1. *Auftragsprotokoll*: Gibt an, wo das Auftragsprotokolldokument gespeichert werden soll. Dies ist bei der Fehlerbehebung hilfreich.

### In PDF/A-Workflow konvertieren {#convert-to-pdf-a-workflow}

Die Option „Nach PDF/A konvertieren“ ruft die `toPDFA`-Assembler-Dienst-API auf. Sie wird zum Konvertieren von PDF-Dokumenten in PDF/A-kompatible Dokumente verwendet.

1. Ziehen Sie **[!UICONTROL ConvertToPDFA]** auf der Registerkarte „Forms Workflow“ in den Sidekick.

1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld &quot;Komponente bearbeiten&quot;Eingabedokumente, Konvertierungsoptionen und Ausgabedokumente und klicken Sie auf **[!UICONTROL OK]**.

#### Eingabedokumente {#input-documents-1}

Geben Sie die Quelle des Dokuments, das in ein PDF/A-kompatibles Dokument konvertiert werden soll, auf eine der folgenden Arten an.

* *Relativ zur Nutzlast*: Das Eingabedokument ist relativ zum Payload-Ordner für das Workflow-Element.
* *Nutzlast verwenden*: Die Payload für das Workflow-Element wird als Eingabedokument verwendet.
* *Absolute Path*: Der absolute Pfad des Eingabedokuments im CRX-Repository.

#### Konvertierungsoptionen {#conversion-options}

Mit den Konvertierungsoptionen können Sie Optionen angeben, die den PDF/A-Konvertierungsprozess ändern.

* *Compliance* : Gibt den PDF/A-Standard an, dem die Ausgabe-PDF/A entsprechen muss.
* *Result Level*: Gibt die Protokollebene, die für die PDF/A-Konvertierungsprotokolle verwendet werden soll, an.
* *Signaturen* : Gibt an, wie die Signaturen im Eingabedokument während der Konvertierung verarbeitet werden müssen.
* *Farbraum* : Gibt den vordefinierten Farbraum an, der für das PDF/A-Ausgabedokument verwendet werden soll.
* *Konvertierung überprüfen*: Gibt an, ob das konvertierte PDF/A-Dokument nach der Konvertierung auf PDF/A-Konformität geprüft werden soll.
* *Job Log Level*: Gibt die Protokollebene, die für die Verarbeitung von Protokollen verwendet werden soll, an.

* *Metadata Extension Schema*: Gibt den Pfad zum Metadaten-Erweiterungsschema, der für XMP-Eigenschaften in den Metadaten des PDF-Dokuments verwendet werden soll, an.

#### Output Documents {#output-documents-1}

Auf der Registerkarte &quot;Output Documents&quot;können Sie das Ziel für die Output Documents angeben

* *PDFA-Dokument*: Gibt den Speicherort an, an dem das konvertierte PDF/A-Dokument gespeichert wird. Es kann entweder das Payload-Dokument überschreiben oder im Payload-Ordner gespeichert werden.
* *Conversion Log*: Gibt den Ort an, an dem die Konvertierungsprotokolle gespeichert werden. Es kann entweder das Payload-Dokument überschreiben oder im Payload-Ordner gespeichert werden.

## Formulare {#forms}

Der Arbeitsablauf zum Rendern von PDF-Formularen ist ein Wrapper um die Formulardienst-API `renderPDFForm`, um ein PDF-Formular mit einer XDP-Vorlage und Daten-XML zu erstellen.

### Render PDF Form-Workflow {#render-pdf-form-workflow}

1. Ziehen Sie den Workflow PDF Formular rendern unter der Registerkarte Forms Workflow auf Sidekick.
1. Doppelklicken Sie auf den hinzugefügten Workflow-Schritt, um die Komponente zu bearbeiten.
1. Konfigurieren Sie im Dialogfeld „Komponente bearbeiten“ Eingabedokumente, Ausgabedokumente und zusätzliche Parameter und klicken Sie auf **[!UICONTROL OK]**.

#### Eingabedokumente {#input-documents-2}

* *Vorlagendatei*: Gibt den Speicherort der XDP-Vorlage an. Dies ist ein Pflichtfeld.

* *Datendokument*: Gibt den Speicherort der Daten-XML an, die mit der Vorlage zusammengeführt werden muss.

#### Output Documents {#output-documents-2}

* *Output Document*: - Gibt den Namen des generierten PDF-Formulars an.

#### Zusätzliche Parameter {#additional-parameters}

* *Inhaltsstamm*: Gibt den Pfad zum Ordner im Repository an, in dem in der Eingabe-XDP-Vorlage verwendete Fragmente oder Bilder gespeichert werden.
* *Sende-URL*: Gibt die Standard-Sende-URL für das generierte PDF-Formular an.
* *Gebietsschema*: Gibt das Standardgebietsschema für das generierte PDF-Formular an.
* *Acrobat-Version*: Gibt die Acrobat-Zielversion für das generierte PDF-Formular an.
* *PDF mit Tags*: Gibt an, ob die generierte PDF-Datei barrierefrei gemacht werden soll.
* *XCI-Dokument*: Gibt den Pfad zur XCI-Datei an.

## Ausgabe {#output}

Der Arbeitsablauf „Nicht-interaktive PDF generieren“ ist ein Wrapper um die Ausgabe-Dienst-API `generatePDFOutput`. Er wird verwendet, um nicht-interaktive PDF-Dokumente aus der XDP-Vorlage und der Daten-XML zu generieren.

### Workflow &quot;Nicht interaktive PDF-Ausgabe generieren&quot;   {#generate-non-interactive-pdf-output-workflow-nbsp}

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
