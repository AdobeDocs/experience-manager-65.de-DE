---
title: '"Tutorial: Erstellen Sie Vorlagen"'
seo-title: Create Print and Web templates for Interactive Communication
description: Erstellen Sie Druck- und Webvorlagen für die interaktive Kommunikation
seo-description: Create Print and Web templates for Interactive Communication
uuid: 22256a61-bcf6-4b02-9ee6-0ffb1cc20a6e
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 879ff6ca-e5f3-451d-acc2-f75142101ddd
docset: aem65
feature: Interactive Communication
exl-id: bef1f05e-aea2-433e-b3d5-0b7ad8163fa7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1796'
ht-degree: 100%

---

# Tutorial: Erstellen Sie Vorlagen{#tutorial-create-templates}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Dieses Tutorial ist ein Schritt in der Reihe [Erstellen Sie Ihre erste interaktive Kommunikation](/help/forms/using/create-your-first-interactive-communication.md). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

Um eine interaktive Kommunikation zu erstellen, müssen auf dem AEM-Server Vorlagen für Druck- und Webkanäle verfügbar sein.

Die Vorlagen für den Druckkanal werden in Adobe Forms Designer erstellt und auf den AEM-Server hochgeladen. Diese Vorlagen stehen dann zur Verfügung, während Sie eine interaktive Kommunikation erstellen.

Die Vorlagen für den Webkanal werden in AEM erstellt. Vorlagenautoren und Administratoren können Webvorlagen erstellen, bearbeiten und aktivieren. Nachdem sie erstellt und aktiviert wurden, stehen diese Vorlagen zur Verfügung, während Sie eine interaktive Kommunikation erstellen.

In diesem Tutorial werden Sie durch die Schritte zum Erstellen von Vorlagen für Druck- und Webkanäle geführt, sodass sie beim Erstellen von interaktiver Kommunikation verfügbar sind. Am Ende dieser Schulung können Sie Folgendes:

* Erstellen Sie XDP-Vorlagen für den Druckkanal mit Adobe Forms Designer
* Laden Sie die XDP-Vorlagen auf den AEM Forms Server hoch
* Erstellen und aktivieren Sie Vorlagen für den Webkanal

## Erstellen Sie eine Vorlage für den Druckkanal {#create-template-for-print-channel}

Erstellen und verwalten Sie eine Vorlage für den Druckkanal von interaktiver Kommunikation mit folgenden Aufgaben:

* [Erstellen Sie eine XDP-Vorlage mit dem Forms Designer](../../forms/using/create-templates-print-web.md#create-xdp-template-using-forms-designer)
* [Laden Sie die XDP-Vorlagen auf den AEM Forms Server hoch](../../forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server)
* [XDP-Vorlage für Layoutfragmente erstellen](../../forms/using/create-templates-print-web.md#create-xdp-template-for-layout-fragments)

### Erstellen Sie eine XDP-Vorlage mit dem Forms Designer {#create-xdp-template-using-forms-designer}

Basierend auf dem [Anwendungsfall](/help/forms/using/create-your-first-interactive-communication.md) und der [Anatomie](/help/forms/using/planning-interactive-communications.md), erstellen Sie die folgenden Teilformulare in der XDP-Vorlage:

* Rechnungsdetails: Enthält ein Dokumentfragment
* Kundendetails: Enthält ein Dokumentfragment
* Rechnungszusammenfassung: Enthält ein Dokumentfragment
* Zusammenfassung: Enthält ein Dokumentfragment (Teilformular „Gebühren“) und ein Diagramm (Teilformular „Diagramme“).
* Einzeln aufgeführte Anrufe: Enthält eine Tabelle (Layoutfragment)
* Jetzt bezahlen: Enthält ein Bild
* Mehrwert-Services: Enthält ein Bild

![create_print_template](assets/create_print_template.gif)

Diese Unterformulare werden nach dem Hochladen der XDP-Datei auf den Forms-Server als Zielbereiche in der Druckvorlage angezeigt. Alle Entitäten wie Dokumentfragmente, Diagramme, Layoutfragmente und Bilder werden bei der Erstellung der interaktiven Kommunikation Zielbereichen hinzugefügt.

Führen Sie die folgenden Schritte aus, um eine XDP-Vorlage für den Druckkanal zu erstellen:

1. Öffnen Sie den Forms Designer, wählen Sie **Datei** > **Neu** > **Verwenden Sie ein leeres Formular**,  tippen Sie auf **Weiter** und anschließend auf **Fertig stellen**, um das Formular für die Vorlagenerstellung zu öffnen.

   Stellen Sie sicher, dass die **Objektbibliothek** und die Option **Objekt** im Menü **Fenster** ausgewählt werden.

1. Ziehen Sie die Komponente **Teilformular** aus der **Objektbibliothek** in das Formular.
1. Wählen Sie das Teilformular aus, um die Optionen für das Teilformular im Fenster **Objekt** im rechten Bereich anzuzeigen.
1. Wählen Sie die Registerkarte **Teilformular** und wählen Sie **Textfluss** aus der Dropdown-Liste **Inhalt** aus. Ziehen Sie den linken Endpunkt des Teilformulars, um die Länge anzupassen.
1. Führen Sie auf der Registerkarte **Bindungen** folgende Schritte aus:

   1. Geben Sie **BillDetails** in das Feld **Name** ein.

   1. Wählen Sie **Keine Datenbindung** aus der Dropdown-Liste **Datenbindung**.

   ![Designer Teilformular](assets/forms_designer_subform_new.png)

1. Wählen Sie das Teilformular „Stamm“, dann die Registerkarte **Teilformular** und dann **Textfluss** aus der Dropdown-Liste **Inhalt** aus. Führen Sie auf der Registerkarte **Bindungen** folgende Schritte aus:

   1. Geben Sie **TelecaBill** in das Feld **Name** ein.

   1. Wählen Sie **Keine Datenbindung** aus der Dropdown-Liste **Datenbindung**.

   ![Teilformular für Druckvorlage](assets/root_subform_print_template_new.png)

1. Wiederholen Sie die Schritte 2 bis 5, um die folgenden Teilformulare zu erstellen:

   * BillDetails
   * CustomerDetails
   * BillSummary
   * Zusammenfassung – Wählen Sie die Registerkarte **Teilformular** und wählen Sie für dieses Teilformular **Positioniert** aus der Dropdown-Liste **Inhalt**. Fügen Sie die folgenden Teilformulare in das Teilformular **Zusammenfassung** ein.

      * Gebühren
      * Diagramme
   * ItemisedCalls
   * PayNow
   * Mehrwert - Service

   Um Zeit zu sparen, können Sie auch vorhandene Teilformulare kopieren und einfügen, um neue Teilformulare zu erstellen.

   Um das Teilformular **Diagramme** rechts neben das Teilformular „Gebühren“ zu verschieben, wählen Sie das Teilformular **Diagramme** im linken Bereich aus, wählen Sie die Registerkarte **Layout** und geben Sie einen Wert für das Feld **AnkerX** an. Der Wert muss größer als der Wert für das Feld **Breite** für das Teilformular **Gebühren** sein. Wählen Sie das Teilformular **Gebühren** und wählen Sie die Registerkarte **Layout**, um den Wert des Felds **Breite** anzuzeigen.

1. Ziehen Sie das Objekt **Text** aus der **Objektbibliothek** in das Formular, und geben Sie den Text **XXXX zum Abonnieren wählen** in das Feld ein.
1. Klicken Sie mit der rechten Maustaste auf das Textobjekt im linken Bereich, wählen Sie **Objekt umbenennen**, und geben Sie den Namen des Textobjekts als **Abonnieren** ein.

   ![XDP-Vorlage](assets/print_xdp_template_subform_new.png)

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie den Namen **create_first_ic_print_template** ein.
   1. Wählen Sie **.xdp** aus der Dropdown-Liste **Dateityp**.

   1. Tippen Sie auf **Speichern**.

### Laden Sie die XDP-Vorlagen auf den AEM Forms Server hoch {#upload-xdp-template-to-the-aem-forms-server}

Nachdem Sie eine XDP-Vorlage mit dem Forms-Designer erstellt haben, müssen Sie sie auf den AEM Forms-Server hochladen, damit die Vorlage beim Erstellen der interaktiven Kommunikation verwendet werden kann.

1. Wählen Sie **[!UICONTROL Formulare]** > **[!UICONTROL Formulare &amp; Dokumente]**.
1. Tippen Sie auf **Erstellen** > **Datei hochladen**.

   Navigieren Sie zur Vorlage **create_first_ic_print_template** (XDP) und wählen Sie sie aus. Tippen Sie auf **Öffnen**, um die XDP-Vorlage auf den AEM Forms-Server zu importieren.

### XDP-Vorlage für Layoutfragmente erstellen {#create-xdp-template-for-layout-fragments}

Um ein Layoutfragment für den Druckkanal der interaktiven Kommunikation zu erstellen, erstellen Sie ein XDP mit Forms Designer und laden Sie es auf den AEM Forms-Server hoch.

1. Öffnen Sie den Formular-Designer, wählen Sie **Datei** > **Neu** > **Leeres Formular verwenden**, und tippen Sie auf **Weiter**, und danach auf **Fertig stellen**, um das Formular für die Vorlagenerstellung zu öffnen.

   Stellen Sie sicher, dass die **Objektbibliothek** und die Option **Objekt** im Menü **Fenster** ausgewählt werden.

1. Ziehen Sie die Komponente **Tabelle** per Drag-and-Drop aus der **Objektbibliothek** auf das Formular.
1. Im Dialogfeld Tabelle einfügen:

   1. Geben Sie die Anzahl der Spalten als **5** an.
   1. Spezifizieren Sie die Anzahl von Zeilen im Hauptteil als **1**.
   1. Aktivieren -sie das Kontrollkästchen **Kopfzeile in Tabelle einschließen**.
   1. Registerkarte **OK**.

1. Tippen Sie im linken Bereich neben **Tabelle** 1 auf **+** und klicken Sie mit der rechten Maustaste auf **Zelle1** und wählen Sie **Objekt umbenennen** in **Datum**.

   Benennen Sie **Zelle2**, **Zelle3**, **Zelle4** und **Zelle5** in **Zeit**, **Anzahl**, **Dauer** und **Kosten** um.

1. Klicken Sie in der **Designer-Ansicht** auf die Textfelder „Kopfzeile“ und benennen Sie sie in **Zeit**, **Anzahl**, **Dauer** und **Kosten** um.

   ![Layout-Fragment](assets/layout_fragment_print_new.png)

1. Wählen Sie **Zeile 1** aus dem linken Bereich und wählen Sie **Objekt** > **Bindung** > **Zeile für jedes Datenelement wiederholen**.

   ![Wiederholungseigenschaften für Layout-Fragmente](assets/layout_fragment_print_repeat_new.png)

1. Ziehen Sie die Komponente **Textfeld** per Drag-and-Drop aus der **Objektbibliothek** in die **Designer-Ansicht**.

   ![Textfeld für Layout-Fragment](assets/layout_fragment_print_text_field_new.png)

   Ziehen Sie die Komponente **Textfeld** in die Zeilen **Zeit**, **Anzahl**, **Dauer** und **Kosten**.

1. Wählen Sie **Datei** > **Speichern unter**, um die Datei im lokalen Dateisystem zu speichern:

   1. Navigieren Sie zum Speicherort der Datei und geben Sie den Namen **table_lf** ein.
   1. Wählen Sie **.xdp** aus der Dropdown-Liste **Dateityp**.

   1. Tippen Sie auf **Speichern**.
   Nachdem Sie eine XDP-Vorlage mit dem Forms-Designer erstellt haben, müssen Sie sie auf den AEM Forms-Server [hochladen](../../forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server), damit die Vorlage beim Erstellen der von Layout-Fragmenten verwendet werden kann.

## Erstellen Sie eine Vorlage für den Webkanal {#create-template-for-web-channel}

Erstellen und verwalten Sie eine Vorlage für den Webkanal von interaktiver Kommunikation mit folgenden Aufgaben:

* [Ordner für Vorlagen erstellen](../../forms/using/create-templates-print-web.md#create-folder-for-templates)
* [Vorlage erstellen](../../forms/using/create-templates-print-web.md#create-the-template)
* [Vorlage aktivieren](../../forms/using/create-templates-print-web.md#enable-the-template)
* [Aktivieren von Schaltflächen in interaktiven Kommunikationen](../../forms/using/create-templates-print-web.md#enabling-buttons-in-interactive-communications)

### Ordner für Vorlagen erstellen {#create-folder-for-templates}

Um eine Webkanal-Vorlage zu erstellen, definieren Sie einen Ordner, in dem Sie die erstellten Vorlagen speichern können. Sobald Sie eine Vorlage in einem Ordner erstellt haben, müssen Sie die Vorlage aktivieren, damit die Formularbenutzer den Webkanal einer interaktiven Kommunikation basierend auf der Vorlage erstellen können.

Führen Sie die folgenden Schritte aus, um einen Ordner für die bearbeitbaren Vorlagen zu erstellen:

1. Tippen Sie auf **Tools** ![Hammersymbol](assets/hammer-icon.svg) > **Konfigurationsbrowser**.
   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](/help/sites-administering/configurations.md).
1. Tippen Sie auf der Seite „Konfigurationsbrowser“ auf **Erstellen**.
1. Legen Sie im Dialogfeld **Konfiguration erstellen** **Create_First_IC_templates** als den Titel für den Ordner fest, aktivieren Sie **Bearbeitbare Vorlagen** und tippen Sie auf **Erstellen**.

   ![Konfigurieren von Webvorlagen](assets/create_first_ic_web_template_new.png)

   Der Ordner **Create_First_IC_templates** wird auf der Seite **Konfigurations-Browser** erstellt und aufgeführt.

### Vorlage erstellen {#create-the-template}

Basierend auf dem [Anwendungsfall](/help/forms/using/create-your-first-interactive-communication.md) und der [Anatomie](/help/forms/using/planning-interactive-communications.md), erstellen Sie die folgenden Bereiche in der Webvorlage:

* Rechnungsdetails: Enthält ein Dokumentfragment
* Kundendetails: Enthält ein Dokumentfragment
* Rechnungszusammenfassung: Enthält ein Dokumentfragment
* Kostenübersicht: Enthält ein Dokumentfragment und ein Diagramm (zweispaltiges Layout)
* Einzeln aufgeführte Anrufe: Enthält eine Tabelle
* Jetzt bezahlen: Enthält die Schaltfläche **Jetzt bezahlen** und ein Bild
* Mehrwert-Services: Enthält ein Bild und die Schaltfläche **Abonnieren**.

![create_web_template](assets/create_web_template.gif)

Beim Erstellen der interaktiven Kommunikation werden alle Elemente wie Dokumentfragmente, Diagramme, Tabellen, Bilder und Schaltflächen hinzugefügt.

Führen Sie die folgenden Schritte aus, um eine Vorlage für den Webkanal im Ordner **Create_First_IC_templates** zu erstellen:

1. Navigieren Sie zum entsprechenden Vorlagenordner durch Auswahl von **Tools** > **Vorlagen** > **Create_First_IC_templates**.
1. Tippen Sie auf **Erstellen**.
1. Wählen Sie im Konfigurationsassistenten **Vorlagentyp wählen** den Typ **Interaktive Kommunikation - Webkanal** und tippen Sie auf **Weiter**.
1. Geben Sie im Konfigurationsassistenten **Vorlagendetails** **Create_First_IC_Web_Template** als Vorlagentitel ein. Geben Sie eine optionale Beschreibung ein und tippen Sie auf **Erstellen**.

   Eine Bestätigungsmeldung, dass **Create_First_IC_Web_Template** angezeigt wird.

1. Tippen Sie auf **Öffnen**, um die Vorlage im Vorlageneditor zu öffnen.
1. Wählen Sie **Anfänglicher Inhalt** aus der Dropdown-Liste neben der Option **Vorschau**.

   ![Vorlagen-Editor](assets/template_editor_initial_content_new.png)

1. Tippen Sie auf **Stammbereich** und dann auf **+**, um die Liste der Komponenten anzuzeigen, die Sie der Vorlage hinzufügen können.
1. Wählen Sie **Bereich** aus der Liste, um einen Bereich über dem **Stammbereich** hinzuzufügen.
1. Wählen Sie die Registerkarte **Inhalt** im linken Bereich. Der neue Bereich, der in Schritt 8 hinzugefügt wurde, wird im **Stammbereich** in der Inhaltsstruktur angezeigt.

   ![Inhaltsstruktur](assets/content_tree_root_panel_new.png)

1. Wählen Sie die Tabelle aus und tippen Sie auf ![configure_icon](assets/configure_icon.png) (Konfigurieren).
1. Im Bereich „Eigenschaften“:

   1. Geben Sie in das Feld „Name“ **BillDetails** ein.
   1. Geben Sie in das Feld „Titel“ **Rechnungsdetails** ein.
   1. Wählen Sie **1** aus der Dropdown-Liste **Anzahl der Spalten**.

   1. Tippen Sie auf ![](/help/forms/using/assets/done_icon.png), um die Eigenschaften zu speichern.

   Der Name des Bereichs wird in der Inhaltsstruktur auf **Rechnungsdetails** aktualisiert.

1. Wiederholen Sie die Schritte 7 bis 11, um der Vorlage Bereiche mit den folgenden Eigenschaften hinzuzufügen:

   | Name | Titel | Spaltenanzahl |
   |---|---|---|
   | customerdetails | Kundendetails | 1 |
   | billsummary | Rechnungszusammenfassung | 1 |
   | summarycharges | Zusammenfassung der Gebühren | 2 |
   | itemisedcalls | Einzeln aufgeführte Anrufe | 1 |
   | paynow | Jetzt zahlen | 2 |
   | vas | Mehrwert - Service | 1 |

   Das folgende Bild zeigt die Inhaltsstruktur, nachdem alle Bereiche zur Vorlage hinzugefügt wurden:

   ![Inhaltsstruktur für alle Bedienfelder](assets/content_tree_all_panels_new.png)

### Vorlage aktivieren {#enable-the-template}

Nachdem Sie die Webvorlage erstellt haben, müssen Sie sie zur Erstellung der interaktiven Kommunikation aktivieren.

Führen Sie die folgenden Schritte aus, um die Webvorlage zu aktivieren:

1. Tippen Sie auf **Tools** ![Hammersymbol](assets/hammer-icon.svg) > **Vorlagen**.
1. Navigieren Sie zur Vorlage **Create_First_IC_Web_Template**, wählen Sie sie aus und tippen Sie auf **Aktivieren**.
1. Registerkarte **Aktivieren** erneut zur Bestätigung.

   Die Vorlage ist aktiviert und ihr Status wird als „Aktiviert“ angezeigt. Sie können diese Vorlage beim Erstellen von interaktiver Kommunikation für den Webkanal verwenden.

### Aktivieren von Schaltflächen in interaktiven Kommunikationen {#enabling-buttons-in-interactive-communications}

Basierend auf den Anwendungsfall müssen Sie die Schaltflächen **Jetzt bezahlen** und **Abonnieren** einbeziehen (adaptive Formularkomponenten) in der interaktiven Kommunikation. Führen Sie die folgenden Schritte aus, um die Verwendung dieser Schaltflächen in der interaktiven Kommunikation zu aktivieren:

1. Wählen Sie **Struktur** aus der Dropdown-Liste neben der Option **Vorschau**.
1. Wählen Sie im Stammbereich **Dokument-Container** mit der Inhaltsstruktur und tippen Sie auf **Richtlinie**, um die Komponenten auszuwählen, die für die Verwendung in der interaktiven Kommunikation erlaubt sind.

   ![Richtlinie konfigurieren](assets/structure_configure_policy_new.png)

1. Wählen Sie auf der Registerkarte **Zugelassene Komponenten** im Abschnitt **Eigenschaften** die Option **Schaltfläche** aus den Komponenten **Adaptives Formular**.

   ![Zugelassene Komponenten](assets/allowed_components_af_new.png)

1. Tippen Sie auf das ![Symbol „Fertig“](assets/done_icon.png), um die Eigenschaften zu speichern.
