---
title: Verwenden von xtypes (klassische Benutzeroberfläche)
seo-title: Verwenden von xtypes (klassische Benutzeroberfläche)
description: Erfahren Sie mehr über die xtypes, die im Lieferumfang von AEM enthalten sind.
seo-description: Erfahren Sie mehr über die xtypes, die im Lieferumfang von AEM enthalten sind.
uuid: 6497caa4-2f9b-4f21-9023-88d485fd1d78
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: adb70b43-1b0b-4302-905a-c7612675dabb
exl-id: 06ca4e6d-9ab7-4c5b-905c-07c448632f2b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '6414'
ht-degree: 52%

---

# Verwenden von xtypes (klassische Benutzeroberfläche){#using-xtypes-classic-ui}

Diese Seite beschreibt die xtypes, die im Lieferumfang von Adobe Experience Manager (AEM) enthalten sind.

In der ExtJS-Sprache ist ein xtype ein symbolischer Name, der einer Klasse zugewiesen wird. Sie können den Absatz &quot;Komponenten-XTypes&quot;im Abschnitt [Überblick über ExtJS 2](https://www.sencha.com/learn/overview-of-extjs-2) lesen, um eine detaillierte Erläuterung zu erhalten, was ein xtype ist und wie er verwendet werden kann.

Informationen zu allen in AEM verfügbaren Widgets finden Sie in der [Dokumentation zur Widgets-API](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html).

Sie können die folgende Xpath-Abfrage in CRXDE verwenden, um herausfinden, in welchen Komponenten ein bestimmter xtype in AEM verwendet wird. Ersetzen Sie dazu „checkbox“ durch den gewünschten xtype:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Diese Seite beschreibt die Verwendung von ExtJS-xtypes in der klassischen Benutzeroberfläche.
>
>Adobe empfiehlt die Verwendung der standardmäßigen, modernen [Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md) basierend auf [Coral UI](/help/sites-developing/touch-ui-concepts.md#coral-ui) und [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Nachstehend finden Sie eine Liste der in Adobe Experience Manager verfügbaren xtypes:

* annotation

   [CQ.wcm.Annotation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Annotation)

    Ein spezielles Fenster mit einem Formular im Hauptteil und einer Schaltflächengruppe in der Fußzeile. Es wird in der Regel zum Bearbeiten von Inhalten verwendet, kann aber auch nur zur Anzeige von Informationen genutzt werden.

* arraystore

   [CQ.Ext.data.ArrayStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayStore)

   Früher als „SimpleStore“ bezeichnet.

   Eine kleine Helper-Klasse, die das Erstellen von [CQ.Ext.data.Stores](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) aus Array-Daten vereinfacht. Ein ArrayStore wird automatisch mit einem [CQ.Ext.data.ArrayReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayReader) konfiguriert.

* asseteditor

   [CQ.dam.AssetEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.AssetEditor)

   Der in DAM Admin verwendete Asset-Editor.

* assetreferencesearchdialog

   [CQ.wcm.AssetReferenceSearchDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.AssetReferenceSearchDialog)

   AssetReferenceSearchDialog ist ein Dialogfeld, das angezeigt wird, wenn eine Seite auf Assets oder Tags verweist.

* blueprintconfig

   [CQ.wcm.msm.BlueprintConfig](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig)

    BlueprintConfig stellt ein Feld bereit, in dem Sie die Live Copies eines Blueprint anzeigen und die Blueprint-Eigenschaften („Synchronisierungsauslöser“ und „Aktionen synchronisieren“) bearbeiten können.

* blueprintstatus

   [CQ.wcm.msm.BlueprintStatus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus)

   BlueprintStatus stellt ein Feld bereit, in dem Sie einen Blueprint und dessen Live Copies-Beziehungen anzeigen und bearbeiten können. Das Durchsuchen erfolgt mit [CQ.wcm.msm.BlueprintStatus.Tree](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus.Tree), die Bearbeitung mit [CQ.wcm.msm.BlueprintConfig](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig) und [CQ.wcm.msm.LiveCopyProperties](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties).

* box

   [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent)

   Eine allgemeine Klasse für eine beliebige [Komponente](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component), die anhand von Breite und Höhe als Feld formatiert werden soll.

   BoxComponent passt das Feldmodell automatisch an die Größen- und Platzierungsdefinition an und funktioniert auch im Rendering-Modell der Komponente ordnungsgemäß.

* browsedialog

   [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog)

   Mit BrowseDialog können Benutzer das Repository durchsuchen und einen Pfad auswählen. Die Klasse wird in der Regel in einem [BrowseField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField) verwendet.

* browsefield

   [CQ.form.BrowseField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField)

   **Veraltet: Verwenden Sie stattdessen  [CQ.form.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField) PathField .**

* bulkeditor

   [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor)

   BulkEditor stellt eine Suchmaschine und ein Raster zum Bearbeiten von Suchergebnissen bereit.

   BulkEditor muss in ein HTML-Formular eingefügt werden (dies ist für die Import-Funktion erforderlich). Die Klasse funktioniert ausgezeichnet mit [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* bulkeditorform

   [CQ.wcm.BulkEditorForm](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditorForm)

   BulkEditorForm stellt [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor) umgeben von einem HTML-Formular bereit. Dies ist die eigenständige Version von [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor). Daher ist das HTML-Formular für die Import-Schaltfläche erforderlich.

* button

   [CQ.Ext.Button](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button)

   Einfache Button-Klasse

* buttongroup

   [CQ.Ext.ButtonGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ButtonGroup)

   Container für eine Gruppe von Schaltflächen.

* chart

   [CQ.Ext.chart.Chart](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart)

   Das CQ.Ext.chart-Paket stellt die Funktion zum Visualisieren von Daten anhand von Flash-basierten Diagrammen bereit. Jedes Diagramm ist direkt mit einem CQ.Ext.data.Store verbunden, wodurch das Diagramm automatisch aktualisiert werden kann. Sie können das Erscheinungsbild eines Diagramms anhand der Konfigurationsoptionen [chartStyle](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) und [extraStyle](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) ändern.

* checkbox

   [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox)

   Einfaches Kontrollkästchen. Kann als direkter Ersatz für herkömmliche Kontrollkästchen verwendet werden.

* checkboxgroup

   [CQ.Ext.form.CheckboxGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.CheckboxGroup)

   Ein Gruppierungscontainer für [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox)-Steuerelemente.

* clearcombo

   [CQ.form.ClearableComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ClearableComboBox)

   ClearableComboBox ist ein nicht bearbeitbares Kombinationsfeld mit einem Auslöser zum Löschen des darin enthaltenen Werts.

* colorfield

   [CQ.form.ColorField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorField)

   Mit ColorField können Benutzer einen Hex-Farbwert direkt oder über das [CQ.Ext.ColorMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorMenu) eingeben.

* colorlist

   [CQ.form.ColorList](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ColorList)

   Mit ColorList kann der Benutzer eine Farbe aus einer bearbeitbaren Liste auswählen.

* colormenu

   [CQ.Ext.menu.ColorMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.ColorMenu)

   Ein Menü, das eine [CQ.Ext.ColorPalette](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette)-Komponente enthält.

* colorpalette

   [CQ.Ext.ColorPalette](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ColorPalette)

   Eine einfache Farbpalettenklasse zum Auswählen von Farben. Die Palette kann in einem beliebigen Container gerendert werden.

* combo

   [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)

   Ein Kombinationsfeld-Steuerelement mit Unterstützung für das automatische Ausfüllen, Remote-Laden, Paging und viele andere Funktionen.

   ComboBox funktioniert ähnlich wie ein herkömmliches &lt;select>-Feld in HTML. Allerdings müssen Sie zum Senden eines [valueField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) einen [hiddenName](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) angeben, um eine ausgeblendete Eingabe zu erstellen.

* component

   [CQ.Ext.Component](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component)

   Eine allgemeine Klasse für alle Ext-Komponenten. Alle Unterklassen von „component“ können an dem automatischen Lebenszyklus zum Erstellen, Rendern und Zerstören von Ext-Komponenten beteiligt sein, der von der [Container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)-Klasse definiert wird. Komponenten können anhand der [items](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)-Konfigurationsoption hinzugefügt werden, wenn der Container erstellt wird.

* componentextractor

   [CQ.wcm.ComponentExtractor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ComponentExtractor)

   Mit ComponentExtractor können Benutzer Komponenten aus einer Website bzw. Seite extrahieren.

* componentselector

   [CQ.form.ComponentSelector](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentSelector)

   Eine gruppierte, sortierte Auswahl der verfügbaren Komponenten.

* componentstyles

   [CQ.form.ComponentStyles](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ComponentStyles)

* compositefield

   [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)

   Eine allgemeine Klasse für feldbasierte, komplexe Formularfelder, einschließlich einzelner Formularfelder oder Formularfeldgruppen.

* container

   [CQ.Ext.Container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)

   Eine allgemeine Klasse für eine beliebige [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent), die andere Komponenten enthalten kann. Container verarbeiten das grundlegende Verhalten der darin enthaltenen Elemente, d. h., Hinzufügen, Einfügen oder Entfernen von Elementen.

   Die am häufigsten verwendeten Containerklassen sind [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel), [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) und [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel).

* contentfinder

   [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder)

   ContentFinder ist ein spezieller, zweispaltiger [Viewport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport) mit dem Content Finder auf der linken und dem Content Frame auf der rechten Seite.

* contentfindertab

   [CQ.wcm.ContentFinderTab](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinderTab)

   ContentFinderTab ist ein spezielles Feld mit Funktionen, die in den Registerkartenfeldern in [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder) verwendet werden. Normalerweise enthält es ein Suchformular – das Abfragefeld – und eine Datenansicht zum Anzeigen der Suche.

* cq.workflow.model.combo

   [CQ.wcm.WorkflowModelCombo](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelCombo)

   WorkflowModelCombo ist ein benutzerdefiniertes [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox), in dem eine Liste der verfügbaren Workflow-Modelle angezeigt wird.

* cq.workflow.model.selector

   [CQ.wcm.WorkflowModelSelector](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.WorkflowModelSelector)

   WorkflowModelSelector ist eine Kombination aus WorkflowModelCombo und Workflow-Miniaturbild und enthält auch Schaltflächen zum Erstellen und Bearbeiten von Workflow-Modellen.

* createsitewizard

   [CQ.wcm.CreateSiteWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateSiteWizard)

   CreateSiteWizard ist ein schrittweiser Assistent zum Erstellen von (MSM-)Sites.

* createversiondialog

   [CQ.wcm.CreateVersionDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.CreateVersionDialog)

   CreateVersionDialog ist ein Dialogfeld, in dem eine neue Version einer Seite erstellt werden kann.

* customcontentpanel

   [CQ.CustomContentPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.CustomContentPanel)

   CustomContentPanel ist ein spezielles Feld für die Verwendung in [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog): Die darin enthaltenen Inhalte werden von einer anderen URL abgerufen bzw. zu einer anderen URL gesendet als die anderen Felder im Dialogfeld.

* cycle

   [CQ.Ext.CycleButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)

   Ein spezieller SplitButton, der ein Menü mit [CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)-Elementen enthält. Die Schaltfläche durchläuft bei einem Klick automatisch jedes Menüelement, indem sie das [change](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)-Ereignis der Schaltfläche (oder ggf. die [changeHandler](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)-Funktion der Schaltfläche) für das aktive Menüelement auslöst.

* dataview

   [CQ.Ext.DataView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView)

   Ein Mechanismus für die Datenanzeige mithilfe von benutzerdefinierten Layout-Vorlagen und Formatierungen. DataView verwendet ein [CQ.Ext.XTemplate](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.XTemplate) als internen Vorlagenmechanismus und ist mit einem [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) verbunden, sodass beim Ändern von Daten im Speicher die Ansicht automatisch mit diesen Änderungen aktualisiert wird.

* datefield

   [CQ.Ext.form.DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField)

   Stellt ein Datumseingabefeld mit einem [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker)-Dropdown-Menü und automatischer Datumsvalidierung bereit.

* datemenu

   [CQ.Ext.menu.DateMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)

   Ein Menü, das eine [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker)-Komponente enthält.

* datepicker

   [CQ.Ext.DatePicker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DatePicker)

   Ein Popup für die Datumsauswahl. Diese Klasse wird von der [DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField)-Klasse zum Durchsuchen und Auswählen eines gültigen Datums verwendet.

* datetime

   [CQ.form.DateTime](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DateTime)

   Mit DateTime können Benutzer ein Datum und eine Uhrzeit eingeben, indem sie [CQ.Ext.form.DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) und [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField) miteinander kombinieren.

* Dialogfeld

   [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog)

    Ein spezielles Fenster mit einem Formular im Hauptteil und einer Schaltflächengruppe in der Fußzeile. Es wird in der Regel zum Bearbeiten von Inhalten verwendet, kann aber auch nur zur Anzeige von Informationen genutzt werden.

* dialogfieldset

   [CQ.form.DialogFieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DialogFieldSet)

   DialogFieldSet ist ein [FieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet) zur Verwendung in [Dialogfeldern](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* directstore

   [CQ.Ext.data.DirectStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectStore)

   Eine kleine Helper-Klasse zum Erstellen von [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store), konfiguriert mit einem [CQ.Ext.data.DirectProxy](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectProxy) und [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader), um die Interaktion mit einem serverseitigen [CQ.Ext.Direct](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Direct)-[Provider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.direct.Provider) zu erleichtern.

* displayfield

   [CQ.Ext.form.DisplayField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DisplayField)

   Ein nur für die Anzeige bestimmtes Textfeld, das nicht validiert und gesendet wird.

* editbar

   [CQ.wcm.EditBar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBar)

   Mit EditBar können Benutzer mithilfe von Schaltflächen in einer Leiste Inhalte bearbeiten.

   Diese sind zwar an dieser Stelle nicht aufgelistet, aber EditBar beinhaltet alle Mitglieder von [CQ.wcm.EditBase](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBase).

* editor

   [CQ.Ext.Editor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Editor)

   Ein allgemeines Editor-Feld für die Anzeige bzw. das Ausblenden nach Bedarf, mit integrierter Logik für Größenänderung und Ereignisbehandlung.

* editorgrid

   [CQ.Ext.grid.EditorGridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)

   Diese Klasse erweitert die [GridPanel Class](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) und ermöglicht die Zellenbearbeitung ausgewählter [Spalten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column). Die bearbeitbaren Spalten werden durch Bereitstellen eines [Editors](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) in der [Spaltenkonfiguration](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column) angegeben.

* editrollover

   [CQ.wcm.EditRollover](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditRollover)

   Mit EditRollover können Benutzer Inhalte durch Doppelklick bearbeiten und weitere Bearbeitungsaktionen im Kontextmenü nutzen. Der bearbeitbare Bereich wird durch einen Rahmen markiert, wenn die Maus über den Inhalt bewegt wird.

* feedimporter

   [CQ.wcm.FeedImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FeedImporter)

   Mit FeedImporter können Benutzer RSS- oder Atom-Feeds importieren und Seiten für jeden Feed-Eintrag erstellen.

* field

   [CQ.Ext.form.Field](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Field)

   Eine allgemeine Klasse für Formularfelder, die Standardfunktionen für die Ereignisbehandlung, Größenänderung, Werteverarbeitung und anderes bereitstellt.

* fieldset

   [CQ.Ext.form.FieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet)

   Ein Standardcontainer zum Gruppieren von Elementen in einem [Formular](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FormPanel). ...

* fileuploaddialogbutton

   [CQ.form.FileUploadDialogButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadDialogButton)

   FileUploadDialogButton erstellt eine Schaltfläche, die ein neues Dialogfeld zum Hochladen einer Datei über das FileUploadField öffnet. Diese Klasse kann in Bearbeitungsdialogfeldern verwendet werden, bei denen das Hochladen in einem separaten Formular erfolgen muss.

* fileuploadfield

   [CQ.form.FileUploadField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadField)

   Mit FileUploadField können Benutzer eine einzelne Datei zum Hochladen auswählen.

* findreplacedialog

   [CQ.wcm.FindReplaceDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FindReplaceDialog)

   FindReplaceDialog ist ein Dialogfeld zum Suchen nach und Ersetzen von Tokens in einer Seite und deren untergeordneten Seiten.

* flash

   [CQ.Ext.FlashComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.FlashComponent)

* grid

   [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)

   Diese Klasse stellt die primäre Oberfläche eines Raster-Steuerelements auf Komponentenbasis bereit, in der Daten im Tabellenformat in Zeilen und Spalten dargestellt werden.

* groupingstore

   [CQ.Ext.data.GroupingStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)

   Eine spezielle Speicherimplementierung zum Gruppieren von Datensätzen nach einem der verfügbaren Felder. Diese Klasse wird normalerweise in Kombination mit [CQ.Ext.grid.GroupingView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GroupingView) verwendet, um das Datenmodell für ein gruppiertes GridPanel zu bestätigen.

* heavymovedialog

   [CQ.wcm.HeavyMoveDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.HeavyMoveDialog)

   HeavyMoveDialog ist ein Dialogfenster zum Verschieben einer Seite und der untergeordneten Seiten, einschließlich erneuter Aktivierung zuvor aktivierter Seiten („große“ Verschiebung).

* hidden

   [CQ.Ext.form.Hidden](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Hidden)

   Ein allgemeines Feld zum Speichern ausgeblendeter Werte in Formularen, die beim Senden des Formulars weitergeleitet werden müssen.

* historybutton

   [CQ.HistoryButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.HistoryButton)

   HistoryButton ist eine kleine Helper-Klasse für die einfache Bereitstellung der Schaltflächen „Vorwärts“ und „Zurück“ . Normalerweise sind zwei verwandte Instanzen erforderlich: Die Instanz für die Schaltfläche „Vorwärts“ ist eine einfache Schaltfläche, die mit der Instanz für die Schaltfläche „Zurück“ verknüpft ist, die den Verlauf handhabt.

* htmleditor

   [CQ.Ext.form.HtmlEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)

   Bietet eine einfache HTML-Editor-Komponente. Einige Symbolleisteneigenschaften werden nicht von Safari unterstützt und werden automatisch ausgeblendet, falls erforderlich. In den Konfigurationsoptionen werden diese Eigenschaften vermerkt, falls zutreffend.

   Für die Schaltflächen in der Editor-Symbolleiste sind in der [buttonTips](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)-Eigenschaft QuickInfos definiert.

* iframedialog

   [CQ.IframeDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframeDialog)

   Ein einfaches Dialogfeld, das die Inhalte eines iFrame anzeigt und Formulare in iFrames zulässt.

* iframepanel

   [CQ.IframePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframePanel)

   Ein Bedienfeld, das einen iframe enthält. Ermöglicht die einfache Erstellung von iFrames, ein iFrame-Ladeereignis und einfachen Zugriff auf die Inhalte von iFrames.

* inlinetextfield

   [CQ.form.InlineTextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.InlineTextField)

   InlineField ist ein Textfeld, das als Beschriftung angezeigt wird, wenn es sich nicht im Fokus befindet.

* jsonstore

   [CQ.Ext.data.JsonStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonStore)

   Eine kleine Helper-Klasse, die das Erstellen von [CQ.Ext.data.Stores](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) aus JSON-Daten erleichtert. Ein JsonStore wird automatisch mit einem [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader) konfiguriert.

* label

   [CQ.Ext.form.Label](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Label)

   Grundlegende Beschriftung

* languagecopydialog

   [CQ.wcm.LanguageCopyDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LanguageCopyDialog)

   LanguageCopyDialog ist ein Dialogfeld zum Kopieren von Sprachstrukturen.

* linkchecker

   [CQ.wcm.LinkChecker](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.LinkChecker)

   LinkChecker ist ein Tool zum Überprüfen externer Links in einer Site.

* listview

   [CQ.Ext.list.ListView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView)

   CQ.Ext.list.ListView ist eine schnelle, einfache Implementierung einer [Raster](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)-ähnlichen Ansicht.

* livecopyproperties

   [CQ.wcm.msm.LiveCopyProperties](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties)

    LiveCopyProperties stellt ein Feld zum Anzeigen und Bearbeiten von Live Copy-Eigenschaften („Beziehungsvererbung“, „Synchronisierungsauslöser“ und „Aktionen synchronisieren“) bereit.

* lvbooleancolumn

   [CQ.Ext.list.BooleanColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.BooleanColumn)

   Eine Spaltendefinitionsklasse, die boolesche Datenfelder rendert. Weitere Informationen finden Sie unter [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column).

* lvcolumn

   [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)

   Diese Klasse kapselt Konfigurationsdaten von Spalten, die bei der Initialisierung von [ListView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView) verwendet werden sollen.

* lvdatecolumn

   [CQ.Ext.list.DateColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn)

   Eine Spaltendefinitionsklasse, die ein verarbeitetes Datum gemäß dem Standardgebietsschema oder in einem konfigurierten [Format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn) ausgibt. Weitere Informationen finden Sie unter [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column).

* lvnumbercolumn

   [CQ.Ext.list.NumberColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)

   Eine Spaltendefinitionsklasse, die ein numerisches Datenfeld gemäß einer [Format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)-Zeichenfolge rendert. Weitere Informationen finden Sie unter [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column).

* mediabrowsedialog

   [CQ.MediaBrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.MediaBrowseDialog)

   **Veraltet: Verwenden Sie stattdessen [Content Finder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder), um Medien zu durchsuchen.**

   MediaBrowseDialog ist ein Dialogfeld zum Durchsuchen der Medienbibliothek.

* menu

   [CQ.Ext.menu.Menu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Menu)

   Ein Menüobjekt. Der Container, dem Sie Menüelemente hinzufügen können. „Menu“ kann als allgemeine Klasse verwendet werden, wenn Sie ein spezielles Menü auf Basis einer anderen Komponente (z. B. [CQ.Ext.menu.DateMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu)) benötigen.

   Menüs können [Menüelemente](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item) oder allgemeine [Komponenten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component) enthalten.

* menubaseitem

   [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem)

   Die allgemeine Klasse für alle in Menüs gerenderten Elemente. BaseItem stellt Optionen für das Standard-Rendering, die Verwaltung in aktiviertem Zustand und die Basiskonfiguration bereit, die von allen Menükomponenten gemeinsam verwendet werden.

* menucheckitem

   [CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)

   Fügt ein Menüelement hinzu, das standardmäßig ein Kontrollkästchen enthält, aber auch Teil einer Optionsfeldgruppe sein kann.

* menuitem

   [CQ.Ext.menu.Item](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item)

   Eine allgemeine Klasse für alle Menüelemente, für die menübezogene Funktionen (wie Untermenüs) erforderlich sind und die keine statischen Anzeigeelemente sind. „Item“ erweitert die allgemeinen Funktionen von [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem) und fügt die menüspezifische Bearbeitung von Aktivierungs- und Klickaktionen hinzu.

* menuseparator

   [CQ.Ext.menu.Separator](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Separator)

   Fügt eine Leiste mit Trennzeichen zu einem Menü hinzu, die zum Trennen logischer Gruppen von Menüelementen verwendet werden. Normalerweise fügen Sie eines dieser Zeichen mit „-“ in der add()-Abfrage oder der Elementkonfiguration hinzu, anstatt das Zeichen direkt zu erstellen.

* menutextitem

   [CQ.Ext.menu.TextItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.TextItem)

   Fügt eine statische Textzeichenfolge zu einem Menü hinzu; wird in der Regel entweder als Überschrift oder als Gruppentrennzeichen verwendet.

* metadata

   [CQ.dam.form.Metadata](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.form.Metadata)

   „Metadata“ stellt Felder zum Bestimmen der für ein Metadatenfeld erforderlichen Informationen bereit (z. B. auf Asset-Editor-Seiten).

   Die Klasse enthält die folgenden Felder:

* multifield

   [CQ.form.MultiField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)

   MultiField ist eine bearbeitbare Liste von Formularfeldern zum Bearbeiten von Eigenschaften mit mehreren Werten.

* mvt

   [CQ.form.MVT](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MVT)

   Mit der MultivariateTesting-Komponente können Benutzer eine Reihe von Bildern definieren und bearbeiten, die in Form alternierender Banner angezeigt werden. Klickratenstatistiken werden pro Banner erfasst.

* notificationinbox

   [CQ.wcm.NotificationInbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.NotificationInbox)

   Mit NotificationInbox können Benutzer WCM-Aktionen abonnieren und Benachrichtigungen verwalten.

* numberfield

   [CQ.Ext.form.NumberField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.NumberField)

   Ein numerisches Textfeld, das automatisch Tastenanschläge filtert und numerische Werte validiert.

* offlineimporter

   [CQ.wcm.OfflineImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.OfflineImporter)

   OfflineImporter ist ein Tool zum Importieren und Konvertieren von Microsoft Word-Dokumenten in AEM-Seiten. Diese Funktion ermöglicht die Offline-Bearbeitung von Inhalten mit einem Textverarbeitungsprogramm.

* ownerdraw

   [CQ.form.OwnerDraw](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.OwnerDraw)

   OwnerDraw kann benutzerdefinierten HTML-Code enthalten (der entweder direkt eingegeben oder von einer URL abgerufen wurde).

* paging

   [CQ.Ext.PagingToolbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.PagingToolbar)

   Mit der steigenden Anzahl von Datensätzen steigt auch die vom Browser zum Rendern benötigte Zeit. Paging wird verwendet, um die Datenmenge zu reduzieren, die mit dem Client ausgetauscht wird.

* panel

   [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel)

   „Panel“ ist ein Container mit spezifischen Funktionen und Strukturkomponenten und ist ideal als Baustein für anwendungsorientierte Benutzeroberflächen geeignet.

   Felder werden vom [CQ.Ext.Container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) vererbt.

* paragraphreference

   [CQ.form.ParagraphReference](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ParagraphReference)

   Das ParagraphReference-Feld ermöglicht das Durchsuchen von Seiten und die Auswahl eines der darin enthaltenen Absätze. Es beinhaltet ein Auslöserfeld und ein damit verknüpftes Dialogfeld zum Durchsuchen von Absätzen.

* password

   [CQ.form.Password](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Password)

    „Password“ ist einem [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField) ähnlich, die darin enthaltenen Werte bleiben jedoch privat, sodass Benutzer vertrauliche Daten eingeben können.

* pathcompletion

   [CQ.form.PathCompletion](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathCompletion)

   **Veraltet: Verwenden Sie stattdessen  [CQ.form.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField) PathField .**

* pathfield

   [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField)

   PathField ist ein Eingabefeld, das für Pfade mit Pfadfertigstellung und einer Schaltfläche zum Öffnen eines [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog) zum Durchsuchen des Server-Repository entwickelt wurde. Damit können auch Seitenabsätze zur erweiterten Linkerzeugung durchsucht werden.

* progress

   [CQ.Ext.ProgressBar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)

   Eine Komponente mit Fortschrittsleiste, die aktualisiert werden kann. Die Fortschrittsleiste unterstützt zwei unterschiedliche Modi: manuell und automatisch.

   Im manuellen Modus sind Benutzer für das Anzeigen, Aktualisieren (über [updateProgress](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)) und Löschen der Fortschrittsleiste aus dem Code verantwortlich, falls erforderlich. Diese Methode eignet sich optimal zum Anzeigen des Fortschritts.

* propertygrid

   [CQ.Ext.grid.PropertyGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyGrid)

   Eine spezielle Rasterimplementierung, die das herkömmliche Eigenschaftenraster nachahmen soll, das normalerweise in Entwicklungs-IDEs verwendet wird. Jede Zeile im Raster steht für eine Eigenschaft eines Objekts; die Daten werden in Namen-Wert-Paaren in [CQ.Ext.grid.PropertyRecords](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyRecord) gespeichert.

* propgrid

   [CQ.PropertyGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.PropertyGrid)

   PropertyGrid ist ein generisches Raster, das zum Anzeigen und Bearbeiten von Objekteigenschaften verwendet wird.

* quicktip

   [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip)

   @xtype quicktip. Eine spezielle QuickInfo-Klasse für QuickInfos, die im Markup angegeben und automatisch von der globalen [CQ.Ext.QuickTips](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTips)-Instanz verwaltet werden können. Zusätzliche Informationen zur Verwendung und Beispiele finden Sie unter „QuickTips-Klasse“.

* radio

   [CQ.Ext.form.Radio](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio)

   Einzelnes Optionsfeld. Ähnlich wie das Kontrollkästchen, der Eingabetyp kann jedoch für die einfache Verwendung automatisch festgelegt werden. Die Gruppierung von Optionsfeldern erfolgt automatisch im Browser, falls alle Optionsfelder einer Gruppe gleich benannt werden.

* radiogroup

   [CQ.Ext.form.RadioGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.RadioGroup)

   Ein Gruppierungscontainer für [CQ.Ext.form.Radio](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio)-Steuerelemente.

* referencesdialog

   [CQ.wcm.ReferencesDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ReferencesDialog)

   ReferencesDialog ist ein Dialogfeld zum Anzeigen von Verweisen auf einer Seite.

* restoretreedialog

   [CQ.wcm.RestoreTreeDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreTreeDialog)

   RestoreTreeDialog ist ein Dialogfeld zum Wiederherstellen einer vorherigen Version einer Struktur.

* restoreversiondialog

   [CQ.wcm.RestoreVersionDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.RestoreVersionDialog)

   RestoreVersionDialog ist ein Dialogfeld zum Wiederherstellen einer vorherigen Version einer Seite.

* richtext

   [CQ.form.RichText](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.RichText)

   RichText stellt ein Formularfeld zum Bearbeiten von formatierten Textinformationen (Rich Text) zur Verfügung.

   Die RichText-Komponente bietet derzeit die folgenden Funktionen:

* rolloutplan

   [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan)

   RolloutPlan stellt ein Dialogfeld zum Überwachen des Rollout-Fortschritts einer Seite bereit. RolloutPlan wird von einem [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard) gestartet.

* rolloutwizard

   [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard)

   RolloutWizard stellt einen Assistenten für das Rollout einer Seite bereit. RolloutWizard startet einen [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan).

* searchfield

   [CQ.form.SearchField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SearchField)

   SearchField ist ein Suchfeld, das die Ergebnisse in einer Dropdown-Liste bereitstellt, die zum Durchsuchen des Repositorys verwendet werden kann.

* selection

   [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection)

   Mit „Selection“ können Benutzer aus mehreren Optionen auswählen. Die Optionen können Teil der Konfiguration sein oder aus einer JSON-Antwort geladen werden. „Selection“ kann entweder als Dropdown-Menü (Auswahl) oder als Kombinationsfeld (Auswahl plus freie Texteingabe) gerendert werden.

* sidekick

   [CQ.wcm.Sidekick](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Sidekick)

   Der „Sidekick“ ist ein unverankerter Hilfsdienst, in dem gängige Tools zur Seitenbearbeitung bereitgestellt werden.

* siteadmin

   [CQ.wcm.SiteAdmin](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteAdmin)

   SiteAdmin ist eine Konsole mit WCM-Administrationsfunktionen.

* siteimporter

   [CQ.wcm.SiteImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.SiteImporter)

   Mit SiteImporter können Benutzer komplette Websites importieren und erste Projekte erstellen.

* sizefield

   [CQ.form.SizeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SizeField)

    Mit SizeField können Benutzer die Breite und Höhe (z. B. eines Bildes) eingeben.

* slider

   [CQ.Ext.Slider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Slider)

   Ein Regler für die vertikale und horizontale Ausrichtung, Tastaturanpassungen, konfigurierbare Ausrichtungen, Achsenklicks und Animationen. Kann als Element einem beliebigen Container hinzugefügt werden. Anwendungsbeispiel...

* slideshow

   [CQ.form.Slideshow](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Slideshow)

   „Slideshow“ stellt eine Komponente bereit, die zum Definieren und Bearbeiten von Bildern und Bildtiteln verwendet werden kann, die möglicherweise in einer Bildschirmpräsentation angezeigt werden.

   Die Komponente für die Bildschirmpräsentation basiert auf der Komponente [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage).

* smartfile

   [CQ.form.SmartFile](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartFile)

   SmartFile ist ein intelligenter Datei-Uploader.

   Wenn ein Flash-Plug-in (Version 9 oder höher) installiert ist, werden Uploads mit der SWFupload-Bibliothek durchgeführt, eine benutzerfreundliche Upload-Methode.

* smartimage

   [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage)

   SmartImage ist ein intelligenter Bild-Uploader, der Tools zum Verarbeiten von hochgeladenen Bildern bereitstellt, beispielsweise ein Definitionstool für Bildzuordnungen und einen Bildbeschneider.

   Beachten Sie, dass die Komponente hauptsächlich für die Nutzung auf einer separaten Dialogfeld-Registerkarte bestimmt ist.

* spacer

   [CQ.Ext.Spacer](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Spacer)

   Wird verwendet, um einen anpassbaren Bereich in einem Layout bereitzustellen.

* spinner

   [CQ.form.Spinner](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Spinner)

   „Spinner“ ist ein Auslöserfeld für numerische, Daten- oder Zeitwerte. Der Wert kann mit den bereitgestellten Aufwärts- und Abwärts-Auslösern, dem Scrollrad oder den Tasten erhöht und verringert werden.

* splitbutton

   [CQ.Ext.SplitButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.SplitButton)

    Eine unterteilte Schaltfläche, die einen integrierten Abwärtspfeil bereitstellt, der ein Ereignis separat zu einem Standard-Klick-Ereignis der Schaltfläche auslösen kann. Sie wird in der Regel verwendet, um ein Dropdown-Menü anzuzeigen, das zusätzliche Optionen zur Hauptaktion der Schaltfläche bereitstellt. Jeder benutzerdefinierte Handler kann jedoch den Pfeilklick implementieren.

* static

   [CQ.Static](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Static)

   Mit „Static“ kann beliebiger Text oder HTML angezeigt werden.

* Statistiken

   [CQ.wcm.Statistics](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Statistics)

    „Statistics“ zeigt die Seitenimpressionen als Diagramm an. Mit dem Widget kann ein Zeitraum ausgewählt werden, für den die Statistiken angezeigt werden sollen.

* store

   [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)

   Die Store-Klasse kapselt einen clientseitigen Cache der [Datensatz](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Record)-Objekte, die Eingabedaten für die Komponenten [GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), [ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) oder [DataView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView) liefern.

* suggestfield

   [CQ.form.SuggestField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SuggestField)

   SuggestField macht Benutzern Vorschläge auf Basis ihrer Eingaben.

* switcher

   [CQ.Switcher](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Switcher)

    „Switcher“ stellt eine Gruppe von Schaltflächen für die Kopfzeilenleiste in einer Konsole bereit, mit denen Benutzer zwischen Websites, digitalen Assets, Tools, Workflows und Sicherheit wechseln können.

* tableedit

   [CQ.form.TableEdit](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit)

   **Veraltet: Verwenden Sie stattdessen  [CQ.form.TableEdit2](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2) .**

* tableedit2

   [CQ.form.TableEdit2](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2)

   TableEdit2 stellt ein Widget für das Erstellen von Tabellen zur Verfügung.

* tabpanel

   [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel)

   Ein allgemeiner Container für Registerkarten. TabPanels können für Layoutzwecke genauso wie ein Standard [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel) verwendet werden, haben aber auch besondere Unterstützung für die Verwendung von untergeordneten Komponenten ([`items`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)).

* tags

   [CQ.tagging.TagInputField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tagging.TagInputField)

   ```
   CQ.tagging.TagInputField
   ```

   ist ein Formular-Widget zum Eingeben von Tags. Es beinhaltet ein Popup-Menü für die Auswahl vorhandener Tags, einschließlich Autovervollständigen und vieler anderer Funktionen.

* textarea

   [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea)

   Mehrzeiliges Textfeld. Kann als direkter Ersatz für herkömmliche textarea-Felder verwendet werden und unterstützt auch die automatische Größenänderung.

* textbutton

   [CQ.TextButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.TextButton)

   TextButton stellt einen Textlink mit den Funktionen einer [CQ.Ext.Button](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button) bereit.

* textfield

   [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)

   Ein einfaches Textfeld. Es kann als direkter Ersatz für herkömmliche Texteingaben oder als allgemeine Klasse für ausgereiftere Eingabesteuerelemente (wie [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea) und [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)) verwendet werden.

* thumbnail

   [CQ.form.Thumbnail](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Thumbnail)

* timefield

   [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField)

   Stellt ein Zeiteingabefeld mit einem Zeit-Dropdown-Menü und automatischer Zeitvalidierung bereit. Anwendungsbeispiel...

* tip

   [CQ.Ext.Tip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tip)

   @xtype tip. Dieses ist die allgemeine Klasse für [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip) und [CQ.Ext.Tooltip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tooltip), die das grundlegende Layout und die Platzierung bereitstellt, die für alle Klassen mit QuickInfo erforderlich sind. Diese Klasse kann direkt für einfache, statisch platzierte QuickInfos verwendet werden.

* titleseparator

   [CQ.menu.TitleSeparator](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.menu.TitleSeparator)

   Fügt eine Leiste mit Trennzeichen zu einem Menü hinzu, die zum Trennen logischer Gruppen von Menüelementen verwendet werden. Das Trennzeichen kann zusätzlich einen Titel aufweisen.

* toolbar

   [CQ.Ext.Toolbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Toolbar)

   Eine allgemeine Klasse für Symbolleisten. Der [`defaultType`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) für die Toolbar-Klasse ist zwar [`button`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button), Toolbar-Elemente (untergeordnete Elemente für den toolbar-Container) können jedoch praktisch jeden Komponententyp umfassen. Symbolleistenelemente können ausdrücklich über den zugehörigen Konstruktor erstellt werden.

* tooltip

   [CQ.Ext.ToolTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ToolTip)

   Eine Standardimplementierung für QuickInfos, die zusätzliche Informationen beim Zeigen auf ein Zielelement bereitstellt. @xtype tooltip.

* treegrid

   [CQ.tree.TreeGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tree.TreeGrid)

   @xtype treegrid

* treepanel

   [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)

   TreePanel ermöglicht das Anzeigen von Baumstruktur-Daten in einer Baumstruktur-Benutzeroberfläche.

   Zu TreePanel hinzugefügte [TreeNodes](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode)können Metadaten enthalten, die von der Anwendung in der [attributes](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode)-Eigenschaft verwendet werden.

* trigger

   [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)

   Stellt einen benutzerfreundlichen Wrapper für TextFields bereit, der eine klickbare Auslöserschaltfläche hinzufügt (ähnelt einem Standard-Kombinationsfeld). Der Auslöser beinhaltet keine Standardaktion. Sie müssen eine Funktion zuweisen, um den Klick-Handler für den Auslöser durch Überschreiben von [onTriggerClick](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField) zu implementieren. Sie können ein TriggerField direkt erstellen, da es genauso wie ein Kombinationsfeld gerendert wird.

* uploaddialog

   [CQ.UploadDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UploadDialog)

   Mit UploadDialog können Benutzer Dateien ins Repository hochladen. Erstellt einen neuen UploadDialog.

* userinfo

   [CQ.UserInfo](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UserInfo)

   Ein Element der Symbolleiste, das den aktuellen Benutzernamen anzeigt und Benutzeraktionen wie das Bearbeiten von Benutzereigenschaften und die Personifikation ermöglicht.

* viewport

   [CQ.Ext.Viewport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport)

   Ein spezieller Container, der den sichtbaren Anwendungsbereich (den Browser-Viewport) darstellt.

   „Viewport“ wird automatisch im Hauptteil des Dokuments gerendert. Die Größe wird automatisch an den Browser-Viewport angepasst und die Größenänderung des Fensters verwaltet. Es kann nur ein Viewport erstellt werden.

* window

   [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)

   Eine spezielles Feld für die Verwendung als Anwendungsfenster. Fenster sind standardmäßig nicht verankert, [anpassbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) und [ziehbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window). Fenster können auf die Größe des Viewports [maximiert](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window), auf die ursprüngliche Größe zurückgesetzt und [minimiert](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) werden.

* xmlstore

   [CQ.Ext.data.XmlStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlStore)

   Eine kleine Helper-Klasse, die das Erstellen von [CQ.Ext.data.Stores](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) aus XML-Daten vereinfacht. XmlStore wird automatisch mit einem [CQ.Ext.data.XmlReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlReader) konfiguriert.

   **** cqincludePseudo xtype, der Widget-Definitionen aus einem anderen Pfad im Repository enthält. Es wird in der Regel in Seitendialogfeldern verwendet. Es gibt keine tatsächliche JavaScript-Widget-Klasse für dieses xtype. Es wird durch die formatData()-Funktion der CQ.Util-Klasse verarbeitet. Weitere Informationen finden Sie in diesem Knowledge Base-Artikel.
