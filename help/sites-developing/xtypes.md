---
title: Verwenden von xtypes (klassische Benutzeroberfläche)
description: Erfahren Sie mehr über alle in Adobe Experience Manager verfügbaren xtypes.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
exl-id: 06ca4e6d-9ab7-4c5b-905c-07c448632f2b
source-git-commit: 7d46ba0eaa73d9f7a67034ba81d7fa379aa0112c
workflow-type: tm+mt
source-wordcount: '6381'
ht-degree: 88%

---

# Verwenden von xtypes (klassische Benutzeroberfläche){#using-xtypes-classic-ui}

Auf dieser Seite werden alle xtypes beschrieben, die in Adobe Experience Manager (AEM) verfügbar sind.

In der ExtJS-Sprache ist ein xtype ein symbolischer Name, der einer Klasse zugewiesen wird. Eine ausführliche Erläuterung der Funktionsweise und Einsatzmöglichkeiten von xtypes finden Sie im Abschnitt zu „Komponenten-xtypes“ unter [Übersicht zu ExtJS 2](https://www.sencha.com/learn/overview-of-extjs-2).

Ausführliche Informationen zu allen verfügbaren Widgets in AEM finden Sie in der [Dokumentation zur Widget-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html).

Sie können die folgende Xpath-Abfrage in CRXDE verwenden, um herausfinden, in welchen Komponenten ein bestimmter xtype in AEM verwendet wird. Ersetzen Sie dazu „checkbox“ durch den gewünschten xtype:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Diese Seite beschreibt die Verwendung von ExtJS-xtypes in der klassischen Benutzeroberfläche.
>
>Adobe empfiehlt die Verwendung der standardmäßigen, modernen [Touch-optimierte Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md) basierend auf [Coral-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#coral-ui) und [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Im Folgenden sind die verfügbaren xtypes in Adobe Experience Manager aufgeführt:

* annotation

  [CQ.wcm.Annotation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Annotation)

   Ein spezielles Fenster mit einem Formular im Hauptteil und einer Schaltflächengruppe in der Fußzeile. Sie wird normalerweise zur Bearbeitung von Inhalten verwendet, kann aber auch nur Informationen anzeigen.

* arraystore

  [CQ.Ext.data.ArrayStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayStore)

  Zuvor als „SimpleStore“ bezeichnet.

  Kleine Helferklasse die das Erstellen von [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)s aus Array-Daten erleichtert. Ein ArrayStore wird automatisch mit einer [CQ.Ext.data.ArrayReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.ArrayReader).

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

  BlueprintStatus stellt ein Feld bereit, in dem Sie einen Blueprint und dessen Live Copies-Beziehungen anzeigen und bearbeiten können. Das Durchsuchen erfolgt über eine [CQ.wcm.msm.BlueprintStatus.Tree](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintStatus.Tree), Bearbeitung durch eine [CQ.wcm.msm.BlueprintConfig](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.BlueprintConfig) und [CQ.wcm.msm.LiveCopyProperties](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.LiveCopyProperties).

* box

  [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent)

  Eine allgemeine Klasse für eine beliebige [Komponente](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component), die anhand von Breite und Höhe als Feld formatiert werden soll.

  BoxComponent passt das Feldmodell automatisch an die Größen- und Platzierungsdefinition an und funktioniert auch im Rendering-Modell der Komponente ordnungsgemäß.

* browsedialog

  [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog)

  Mit BrowseDialog können Benutzer das Repository durchsuchen, um einen Pfad auszuwählen. Die Klasse wird in der Regel in einem [BrowseField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField) verwendet.

* browsefield

  [CQ.form.BrowseField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.BrowseField)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField).**

* bulkeditor

  [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor)

  BulkEditor stellt eine Suchmaschine und ein Raster zum Bearbeiten von Suchergebnissen bereit.

  Der BulkEditor muss in ein HTML-Formular eingefügt werden (für die Importfunktion erforderlich). Dies funktioniert ausgezeichnet mit einem [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* bulkeditorform

  [CQ.wcm.BulkEditorForm](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditorForm)

  BulkEditorForm bietet [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor) umgeben von einem HTML-Formular. Dies ist die eigenständige Version von [CQ.wcm.BulkEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.BulkEditor). Daher ist das HTML-Formular für die Import-Schaltfläche erforderlich.

* Schaltfläche

  [CQ.Ext.Button](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button)

  Eine einfache Schaltflächenklasse.

* buttongroup

  [CQ.Ext.ButtonGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ButtonGroup)

  Ein Container für eine Schaltflächengruppe.

* chart

  [CQ.Ext.chart.Chart](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart)

  Das CQ.Ext.chart-Paket stellt die Funktion zum Visualisieren von Daten anhand von Flash-basierten Diagrammen bereit. Jedes Diagramm wird direkt an einen CQ.Ext.data.Store gebunden, was automatische Aktualisierungen des Diagramms ermöglicht. Sie können das Erscheinungsbild eines Diagramms anhand der Konfigurationsoptionen [chartStyle](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) und [extraStyle](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.chart.Chart) ändern.

* checkbox

  [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox)

  Ein einzelnes Kontrollkästchen. Kann als direkter Ersatz für herkömmliche Kontrollkästchen verwendet werden.

* checkboxgroup

  [CQ.Ext.form.CheckboxGroup](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.CheckboxGroup)

  Ein Gruppierungs-Container für [CQ.Ext.form.Checkbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Checkbox)-Steuerelemente.

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

  Ein Kombinationsfeld-Steuerelement mit Unterstützung für automatisches Ausfüllen, Remote-Laden, Paging und viele andere Funktionen.

  Eine ComboBox funktioniert ähnlich wie ein herkömmliches &lt;select>-Feld in HTML. Der Unterschied besteht darin, dass für das [valueField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) ein [hiddenName](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox) angegeben werden muss, um eine ausgeblendete Eingabe zu erstellen.

* Komponente

  [CQ.Ext.Component](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component)

  Eine allgemeine Klasse für alle Ext-Komponenten. Alle Unterklassen der Komponente können am automatisierten Lebenszyklus der Ext-Komponente von Erstellung, Rendering und Zerstörung teilnehmen, der von der [Container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) -Klasse. Komponenten können einem Container über die Konfigurationsoption [items](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) hinzugefügt werden, wenn der Container erstellt wird.

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

  Eine allgemeine Klasse für eine beliebige [CQ.Ext.BoxComponent](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.BoxComponent), die andere Komponenten enthalten kann. Container verarbeiten das grundlegende Verhalten von enthaltenen Elementen, d. h. das Hinzufügen, Einfügen und Entfernen von Elementen.

  Die am häufigsten verwendeten Container-Klassen sind [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel), [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window), und [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel).

* contentfinder

  [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder)

  ContentFinder ist ein spezialisiertes zweispaltiges [Viewport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport) enthält den tatsächlichen Content Finder auf der linken und den Inhalts-Frame auf der rechten Seite.

* contentfindertab

  [CQ.wcm.ContentFinderTab](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinderTab)

  ContentFinderTab ist ein spezialisiertes Bedienfeld mit Funktionen, die in den Registerkartenfeldern in [CQ.wcm.ContentFinder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder) verwendet werden. Normalerweise enthält es ein Suchformular – das Abfragefeld – und eine Datenansicht zum Anzeigen der Suche.

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

  Das Dialogfeld CreateVersionDialog ist ein Dialogfeld, in dem eine Version einer Seite erstellt werden kann.

* customcontentpanel

  [CQ.CustomContentPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.CustomContentPanel)

  CustomContentPanel ist ein spezielles Feld für die Verwendung in [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog): Die darin enthaltenen Inhalte werden von einer anderen URL abgerufen bzw. zu einer anderen URL gesendet als die anderen Felder im Dialogfeld.

* cycle

  [CQ.Ext.CycleButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)

  Ein spezieller SplitButton, der ein Menü mit [CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)-Elementen enthält. Beim Klicken durchblättert die Schaltfläche automatisch alle Menüelemente und löst für das aktive Menüelement das [change](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton)-Ereignis aus (bzw. ruft die Funktion [changeHandler](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.CycleButton) der Schaltfläche ab, falls vorhanden).

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

  Ein Popup für die Datumsauswahl. Diese Klasse wird von der Klasse [DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) verwendet, um das Durchsuchen und Auswählen von gültigen Daten zu ermöglichen.

* datetime

  [CQ.form.DateTime](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DateTime)

  Mit DateTime können Benutzer ein Datum und eine Uhrzeit eingeben, indem sie [CQ.Ext.form.DateField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DateField) und [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField) miteinander kombinieren.

* Dialogfeld

  [CQ.Dialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog)

   Ein spezielles Fenster mit einem Formular im Hauptteil und einer Schaltflächengruppe in der Fußzeile. Sie wird normalerweise zur Bearbeitung von Inhalten verwendet, kann aber auch nur Informationen anzeigen.

* dialogfieldset

  [CQ.form.DialogFieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.DialogFieldSet)

  DialogFieldSet ist ein [FieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet) zur Verwendung in [Dialogfeldern](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Dialog).

* directstore

  [CQ.Ext.data.DirectStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectStore)

  Eine kleine Helper-Klasse zum Erstellen von [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store), konfiguriert mit einem [CQ.Ext.data.DirectProxy](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.DirectProxy) und [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader), um die Interaktion mit einem Server-seitigen [CQ.Ext.Direct](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Direct)-[Provider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.direct.Provider) zu erleichtern.

* displayField

  [CQ.Ext.form.DisplayField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.DisplayField)

  Ein nur für die Anzeige bestimmtes Textfeld, das nicht validiert und gesendet wird.

* editbar

  [CQ.wcm.EditBar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBar)

  Mit EditBar können Benutzer mithilfe von Schaltflächen in einer Leiste Inhalte bearbeiten.

  Obwohl hier nicht aufgeführt, enthält EditBar alle Mitglieder von [CQ.wcm.EditBase](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditBase).

* editor

  [CQ.Ext.Editor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Editor)

  Ein allgemeines Editor-Feld für die Anzeige bzw. das Ausblenden nach Bedarf, mit integrierter Logik für Größenänderung und Ereignisbehandlung.

* editorgrid

  [CQ.Ext.grid.EditorGridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)

  Diese Klasse erweitert die [GridPanel-Klasse](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), um die Bearbeitung von Zellen in ausgewählten [Spalten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column) zu ermöglichen. Die bearbeitbaren Spalten werden durch Angabe eines [Editors](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel) in der [Spaltenkonfiguration](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.Column) festgelegt.

* editrollover

  [CQ.wcm.EditRollover](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.EditRollover)

  Mit EditRollover können Benutzende Inhalte durch Doppelklick bearbeiten und über ein Kontextmenü weitere Bearbeitungsaktionen durchführen. Der bearbeitbare Bereich wird durch einen Rahmen gekennzeichnet, wenn die Maus über den Inhalt bewegt wird.

* feedimporter

  [CQ.wcm.FeedImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.FeedImporter)

  Mit FeedImporter können Benutzer RSS- oder Atom-Feeds importieren und Seiten für jeden Feed-Eintrag erstellen.

* field

  [CQ.Ext.form.Field](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Field)

  Eine allgemeine Klasse für Formularfelder, die Standardfunktionen für die Ereignisbehandlung, Größenänderung, Werteverarbeitung und anderes bereitstellt.

* fieldset

  [CQ.Ext.form.FieldSet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FieldSet)

  Ein Standardcontainer zum Gruppieren von Elementen in einem [Formular](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.FormPanel).

* fileuploaddialogbutton

  [CQ.form.FileUploadDialogButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.FileUploadDialogButton)

  FileUploadDialogButton erstellt eine Schaltfläche, die ein neues Dialogfeld zum Hochladen einer Datei über das FileUploadField öffnet. Kann in Bearbeitungsdialogfeldern verwendet werden, in denen der Upload in einem separaten Formular erfolgen muss.

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

  Diese Klasse stellt die primäre Schnittstelle eines komponentenbasierten Rastersteuerelements dar, um Daten in einem tabellarischen Format von Zeilen und Spalten darzustellen.

* groupingstore

  [CQ.Ext.data.GroupingStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)

  Eine spezielle Speicherimplementierung zum Gruppieren von Datensätzen nach einem der verfügbaren Felder. Dies wird zusammen mit einer [CQ.Ext.grid.GroupingView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GroupingView) , um das Datenmodell für ein gruppiertes GridPanel zu überprüfen.

* heavymovedialog

  [CQ.wcm.HeavyMoveDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.HeavyMoveDialog)

  HeavyMoveDialog ist ein Dialogfenster zum Verschieben einer Seite und der untergeordneten Seiten, einschließlich erneuter Aktivierung zuvor aktivierter Seiten („große“ Verschiebung).

* hidden

  [CQ.Ext.form.Hidden](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Hidden)

  Ein einfaches ausgeblendetes Feld zum Speichern ausgeblendeter Werte in Formularen, die beim Senden des Formulars übergeben werden müssen.

* historybutton

  [CQ.HistoryButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.HistoryButton)

  HistoryButton ist eine kleine Helper-Klasse für die einfache Bereitstellung der Schaltflächen „Vorwärts“ und „Zurück“. Normalerweise sind zwei verwandte Instanzen erforderlich: Die Instanz für die Schaltfläche „Vorwärts“ ist eine einfache Schaltfläche, die mit der Instanz für die Schaltfläche „Zurück“ verknüpft ist, die den Verlauf handhabt.

* htleditor

  [CQ.Ext.form.HtmlEditor](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)

  Stellt eine einfache HTML-Editor-Komponente bereit. Einige Symbolleistenfunktionen werden von Safari nicht unterstützt und bei Bedarf automatisch ausgeblendet. Diese werden gegebenenfalls in den Konfigurationsoptionen angegeben.

  Für die Schaltflächen in der Editor-Symbolleiste sind in der [buttonTips](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.HtmlEditor)-Eigenschaft QuickInfos definiert.

* iframedialog

  [CQ.IframeDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframeDialog)

  Ein einfaches Dialogfeld, das die Inhalte eines iFrame anzeigt und Formulare in iFrames zulässt.

* iframepanel

  [CQ.IframePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.IframePanel)

  Ein Feld mit einem iFrame. Bietet einfache Erstellung von iFrames, ein iFrame-Ladeereignis und einfachen Zugriff auf den iframe-Inhalt.

* inlinetextfield

  [CQ.form.InlineTextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.InlineTextField)

  InlineField ist ein Textfeld, das als Beschriftung angezeigt wird, wenn es sich nicht im Fokus befindet.

* jsonstore

  [CQ.Ext.data.JsonStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonStore)

  Eine kleine Helferklasse, die das Erstellen von [CQ.Ext.data.Stores](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store) aus JSON-Daten erleichtert. Ein JsonStore wird automatisch mit einer [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader).

* label

  [CQ.Ext.form.Label](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Label)

  Ein einfaches Beschriftungsfeld.

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

  Die LiveCopyProperties bieten einen Bereich zum Anzeigen und Bearbeiten von Live Copy-Eigenschaften ( Vererbung der Beziehung, Synchronisierung von Triggern und Synchronisierungsaktionen ).

* lvbooleancolumn

  [CQ.Ext.list.BooleanColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.BooleanColumn)

  Eine Spaltendefinitionsklasse, die boolesche Datenfelder rendert. Weitere Informationen finden Sie unter [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column).

* lvcolumn

  [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)

  Diese Klasse kapselt Konfigurationsdaten von Spalten, die bei der Initialisierung von [ListView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.ListView) verwendet werden sollen.

* lvdatecolumn

  [CQ.Ext.list.DateColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn)

  Eine Spaltendefinitionsklasse, die ein übergebenes Datum gemäß dem Standardgebietsschema oder einem konfigurierten [Format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.DateColumn) rendert. Weitere Informationen finden Sie unter [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column).

* lvnumbercolumn

  [CQ.Ext.list.NumberColumn](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)

  Eine Spaltendefinitionsklasse, die ein numerisches Datenfeld gemäß einer [Format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.NumberColumn)-Zeichenfolge rendert. Weitere Informationen finden Sie unter [xtype](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column)-Konfigurationsoptionen von [CQ.Ext.list.Column](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.list.Column).

* mediabrowsedialog

  [CQ.MediaBrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.MediaBrowseDialog)

  **Veraltet: Verwenden Sie stattdessen [Content Finder](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.ContentFinder), um Medien zu durchsuchen.**

  MediaBrowseDialog ist ein Dialogfeld zum Durchsuchen der Medienbibliothek.

* menu

  [CQ.Ext.menu.Menu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Menu)

  Ein Menüobjekt. Dies ist der Container, dem Sie Menüelemente hinzufügen können. Das Menü kann auch als Basisklasse dienen, wenn Sie ein spezielles Menü basierend auf einer anderen Komponente (wie [CQ.Ext.menu.DateMenu](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.DateMenu) zum Beispiel).

  Menüs können entweder [Menu-Elemente](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item) oder allgemeine [Komponenten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Component) enthalten.

* menubaseitem

  [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem)

  Die allgemeine Klasse für alle in Menüs gerenderten Elemente. BaseItem bietet standardmäßige Rendering-, aktivierte Statusverwaltung- und Basiskonfigurationsoptionen, die von allen Menükomponenten gemeinsam genutzt werden.

* menucheckitem

  [CQ.Ext.menu.CheckItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.CheckItem)

  Fügt ein Menüelement hinzu, das standardmäßig ein Kontrollkästchen enthält, aber auch Teil einer Optionsfeldgruppe sein kann.

* menuitem

  [CQ.Ext.menu.Item](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Item)

  Eine Basisklasse für alle Menüelemente, die menübezogene Funktionen erfordern (wie Untermenüs) und keine statischen Anzeigeelemente sind. „Item“ erweitert die allgemeinen Funktionen von [CQ.Ext.menu.BaseItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.BaseItem) und fügt die menüspezifische Bearbeitung von Aktivierungs- und Klickaktionen hinzu.

* menuseparator

  [CQ.Ext.menu.Separator](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.Separator)

  Fügt eine Leiste mit Trennzeichen zu einem Menü hinzu, die zum Trennen logischer Gruppen von Menüelementen verwendet werden. Im Allgemeinen fügen Sie einen dieser Elemente hinzu, indem Sie &quot;-&quot;in Ihrem Aufruf zu add() oder in Ihrer Elementkonfiguration verwenden, anstatt einen direkt zu erstellen.

* menutextitem

  [CQ.Ext.menu.TextItem](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.menu.TextItem)

  Fügt eine statische Textzeichenfolge zu einem Menü hinzu, die entweder als Überschrift oder als Gruppentrennzeichen verwendet wird.

* Metadaten

  [CQ.dam.form.Metadata](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.dam.form.Metadata)

  Metadaten bieten eine Reihe von Feldern, um die für ein Metadatenfeld erforderlichen Informationen zu bestimmen, wie sie z. B. auf Asset-Editor-Seiten verwendet werden.

  Die Klasse enthält die folgenden Felder:

* multifield

  [CQ.form.MultiField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)

  MultiField ist eine bearbeitbare Liste von Formularfeldern zum Bearbeiten von Eigenschaften mit mehreren Werten.

* mvt

  [CQ.form.MVT](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MVT)

  Die Multivariate Testing-Komponente kann verwendet werden, um eine Reihe von Bildern zu definieren und zu bearbeiten, die als abwechselnde Banner dargestellt werden. Klickratenstatistiken werden pro Banner erfasst.

* notificationinbox

  [CQ.wcm.NotificationInbox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.NotificationInbox)

  Mit NotificationInbox können Benutzer WCM-Aktionen abonnieren und Benachrichtigungen verwalten.

* numberfield

  [CQ.Ext.form.NumberField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.NumberField)

  Ein numerisches Textfeld, das automatisch Tastenanschläge filtert und numerische Werte validiert.

* offlineimporter

  [CQ.wcm.OfflineImporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.OfflineImporter)

  OfflineImporter ist ein Tool zum Importieren und Konvertieren von Microsoft® Word-Dokumenten in AEM Seiten. Mit dieser Funktion können Inhalte mithilfe eines Textverarbeitungsgeräts offline bearbeitet werden.

* ownerdraw

  [CQ.form.OwnerDraw](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.OwnerDraw)

  OwnerDraw kann benutzerdefinierten HTML-Code enthalten (der entweder direkt eingegeben oder von einer URL abgerufen wurde).

* paging

  [CQ.Ext.PagingToolbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.PagingToolbar)

  Mit zunehmender Anzahl von Datensätzen nimmt die für die Wiedergabe durch den Browser erforderliche Zeit zu. Paging wird verwendet, um die Datenmenge zu reduzieren, die mit dem Client ausgetauscht wird.

* panel

  [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel)

  „Panel“ ist ein Container mit spezifischen Funktionen und Strukturkomponenten und ist ideal als Baustein für anwendungsorientierte Benutzeroberflächen geeignet.

  Felder werden vom [CQ.Ext.Container](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) vererbt.

* paragraphreference

  [CQ.form.ParagraphReference](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.ParagraphReference)

  Über das Absatzreferenzfeld können Sie Seiten durchsuchen und einen ihrer Absätze auswählen. Sie besteht aus einem Feld für Trigger und einem zugehörigen Dialogfeld für die Absatzsuche.

* Kennwort

  [CQ.form.Password](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Password)

   „Password“ ist einem [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField) ähnlich, die darin enthaltenen Werte bleiben jedoch privat, sodass Benutzer vertrauliche Daten eingeben können.

* pathcompletion

  [CQ.form.PathCompletion](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathCompletion)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField).**

* pathfield

  [CQ.form.PathField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.PathField)

  „PathField“ ist ein Eingabefeld für Pfade mit Pfadvervollständigung und einer Schaltfläche zum Öffnen eines [CQ.BrowseDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.BrowseDialog) zum Durchsuchen des Server-Repositorys. Damit können auch Seitenabsätze zur erweiterten Link-Erzeugung durchsucht werden.

* Fortschritt

  [CQ.Ext.ProgressBar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)

  Eine Komponente mit einer Fortschrittsleiste, die aktualisiert werden kann. Die Fortschrittsleiste unterstützt zwei verschiedene Modi: manuell und automatisch.

  Im manuellen Modus sind Sie für das Anzeigen, Aktualisieren (über [updateProgress](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ProgressBar)) und Löschen der Fortschrittsleiste nach Bedarf über Ihren eigenen Code verantwortlich. Diese Methode eignet sich am besten, wenn Sie den Fortschritt anzeigen möchten.

* propertygrid

  [CQ.Ext.grid.PropertyGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyGrid)

  Eine spezielle Rasterimplementierung, die das herkömmliche Eigenschaftenraster nachahmen soll, das normalerweise in Entwicklungs-IDEs verwendet wird. Jede Zeile im Raster steht für eine Eigenschaft eines Objekts; die Daten werden in Namen-Wert-Paaren in [CQ.Ext.grid.PropertyRecord](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.PropertyRecord) gespeichert.

* propgrid

  [CQ.PropertyGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.PropertyGrid)

  PropertyGrid ist ein generisches Raster, das zum Anzeigen und Bearbeiten von Objekteigenschaften verwendet wird.

* quicktip

  [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip)

  @xtype quicktip. Eine spezielle QuickInfo-Klasse für QuickInfos, die im Markup angegeben und automatisch von der globalen [CQ.Ext.QuickTips](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTips)-Instanz verwaltet werden können. Zusätzliche Informationen zur Verwendung und Beispiele finden Sie unter dem Header „QuickTips-Klasse“.

* radio

  [CQ.Ext.form.Radio](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.Radio)

  Ein einzelnes Optionsfeld Ähnlich wie das Kontrollkästchen, der Eingabetyp kann jedoch für die einfache Verwendung automatisch festgelegt werden. Die Gruppierung von Optionsfeldern erfolgt automatisch im Browser, falls alle Optionsfelder einer Gruppe gleich benannt werden.

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

  „RichText“ stellt ein Formularfeld zum Bearbeiten von formatierten Textinformationen (Rich Text) zur Verfügung.

  Die RichText-Komponente bietet derzeit die folgenden Funktionen:

* rolloutplan

  [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan)

  RolloutPlan stellt ein Dialogfeld zum Überwachen des Rollout-Fortschritts einer Seite bereit. „RolloutPlan“ wird von einem [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard) gestartet.

* rolloutwizard

  [CQ.wcm.msm.RolloutWizard](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutWizard)

  RolloutWizard stellt einen Assistenten für das Rollout einer Seite bereit. „RolloutWizard“ startet einen [CQ.wcm.msm.RolloutPlan](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.msm.RolloutPlan).

* searchfield

  [CQ.form.SearchField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SearchField)

  Das SearchField bietet ein Suchfeld, das die Ergebnisse in einer Dropdown-Liste bereitstellt, die für die Suche nach dem Repository verwendet werden kann.

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

  Mit SizeField können Benutzer die Breite und Höhe eingeben (z. B. für ein Bild).

* slider

  [CQ.Ext.Slider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Slider)

  Ein Regler für die vertikale und horizontale Ausrichtung, Tastaturanpassungen, konfigurierbare Ausrichtungen, Achsenklicks und Animationen. Kann als Element zu jedem Container hinzugefügt werden. Anwendungsbeispiel: ...

* slideshow

  [CQ.form.Slideshow](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Slideshow)

  „Slideshow“ stellt eine Komponente bereit, die zum Definieren und Bearbeiten von Bildern und Bildtiteln verwendet werden kann, die möglicherweise in einer Bildschirmpräsentation angezeigt werden.

  Die Komponente &quot;Bildschirmpräsentation&quot;basiert auf dem [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage) -Komponente.

* smartfile

  [CQ.form.SmartFile](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartFile)

  „SmartFile“ ist ein intelligenter Datei-Uploader.

  Wenn ein Flash-Plug-in (Version 9 oder höher) installiert ist, werden Uploads mit der SWFupload-Bibliothek durchgeführt, was eine benutzerfreundliche Upload-Methode darstellt.

* smartimage

  [CQ.form.SmartImage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SmartImage)

  SmartImage ist ein intelligenter Bild-Uploader, Es bietet Tools zur Verarbeitung eines hochgeladenen Bildes, z. B. ein Tool zum Definieren von Imagemaps und einem Bildzuschnitt.

  Die Komponente wurde für die Verwendung auf einer separaten Registerkarte für Dialogfelder entwickelt.

* spacer

  [CQ.Ext.Spacer](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Spacer)

  Wird verwendet, um einen anpassbaren Bereich in einem Layout bereitzustellen.

* spinner

  [CQ.form.Spinner](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Spinner)

  Das Spinner-Feld ist ein Trigger für numerische, Datums- oder Uhrzeitwerte. Der Wert kann mit den bereitgestellten Aufwärts- und Abwärts-Auslösern, dem Scroll-Rad oder den Tasten erhöht und verringert werden.

* splitbutton

  [CQ.Ext.SplitButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.SplitButton)

   Eine unterteilte Schaltfläche, die einen integrierten Abwärtspfeil bereitstellt, der ein Ereignis separat zu einem Standard-Klick-Ereignis der Schaltfläche auslösen kann. Normalerweise wird dies verwendet, um ein Dropdown-Menü anzuzeigen, das zusätzliche Optionen für die primäre Schaltflächenaktion bereitstellt. Jeder benutzerdefinierte Handler kann jedoch die Pfeilklick-Implementierung bereitstellen.

* static

  [CQ.Static](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Static)

  Mit „Static“ kann beliebiger Text oder HTML angezeigt werden.

* Statistiken

  [CQ.wcm.Statistics](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.wcm.Statistics)

   „Statistics“ zeigt die Seitenimpressionen als Diagramm an. Das Widget ermöglicht die Auswahl eines Zeitraums, für den die Statistiken angezeigt werden sollen.

* store

  [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)

  Die Store-Klasse kapselt einen clientseitigen Cache von [Datensatz](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Record) Objekte, die Eingabedaten für Komponenten wie die [GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel), die [ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)oder die [DataView](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.DataView).

* suggestfield

  [CQ.form.SuggestField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.SuggestField)

  Das SuggestField bietet dem Benutzer Vorschläge basierend auf seiner Eingabe.

* switcher

  [CQ.Switcher](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Switcher)

   „Switcher“ stellt eine Gruppe von Schaltflächen für die Kopfzeilenleiste in einer Konsole bereit, mit denen Benutzer zwischen Websites, digitalen Assets, Tools, Workflows und Sicherheit wechseln können.

* tableedit

  [CQ.form.TableEdit](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit)

  **Veraltet: Verwenden Sie stattdessen [CQ.form.TableEdit2.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2)**

* tableedit2

  [CQ.form.TableEdit2](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.TableEdit2)

  „TableEdit2“ stellt ein Widget zum Erstellen von Tabellen bereit.

* tabpanel

  [CQ.Ext.TabPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.TabPanel)

  Ein allgemeiner Container für Registerkarten. TabPanels kann zu Layout-Zwecken genauso wie ein standardmäßiges [CQ.Ext.Panel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Panel) verwendet werden, verfügt aber auch über spezielle Unterstützung für darin enthaltene untergeordnete Komponenten ([`items` ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container)).

* tags

  [CQ.tagging.TagInputField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tagging.TagInputField)

  ```
  CQ.tagging.TagInputField
  ```

  ist ein Formular-Widget zum Eingeben von Tags. Es beinhaltet ein Popup-Menü für die Auswahl vorhandener Tags, einschließlich Autovervollständigen und vieler anderer Funktionen.

* textarea

  [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea)

  Ein mehrere Zeilen umspannendes Textfeld. Kann als direkter Ersatz für herkömmliche textarea-Felder verwendet werden und unterstützt auch die automatische Größenänderung.

* textbutton

  [CQ.TextButton](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.TextButton)

  TextButton stellt einen Textlink mit den Funktionen einer [CQ.Ext.Button](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button) bereit.

* textfield

  [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)

  Ein einfaches Textfeld. Kann als direkter Ersatz für herkömmliche Texteingaben oder als allgemeine Klasse für komplexere Eingabeelemente (wie [CQ.Ext.form.TextArea](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextArea) und [CQ.Ext.form.ComboBox](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.ComboBox)) verwendet werden.

* thumbnail

  [CQ.form.Thumbnail](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Thumbnail)

* timefield

  [CQ.Ext.form.TimeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TimeField)

  Stellt ein Zeiteingabefeld mit einem Zeit-Dropdown-Menü und automatischer Zeitvalidierung bereit. Anwendungsbeispiel: ...

* tip

  [CQ.Ext.Tip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tip)

  @xtype tip. Dieses ist die allgemeine Klasse für [CQ.Ext.QuickTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.QuickTip) und [CQ.Ext.Tooltip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Tooltip), die das grundlegende Layout und die Platzierung bereitstellt, die für alle Klassen mit QuickInfo erforderlich sind. Diese Klasse kann direkt für einfache, statisch positionierte Tipps verwendet werden.

* titleseparator

  [CQ.menu.TitleSeparator](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.menu.TitleSeparator)

  Fügt eine Leiste mit Trennzeichen zu einem Menü hinzu, die zum Trennen logischer Gruppen von Menüelementen verwendet werden. Das Trennzeichen kann auch einen Titel enthalten.

* toolbar

  [CQ.Ext.Toolbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Toolba)

  Eine allgemeine Klasse für Symbolleisten. Der [`defaultType`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Container) für die Toolbar-Klasse ist zwar [`button`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Button), Toolbar-Elemente (untergeordnete Elemente für den toolbar-Container) können jedoch praktisch jeden Komponententyp umfassen. Symbolleistenelemente können explizit über ihre Konstruktoren erstellt werden.

* QuickInfo

  [CQ.Ext.ToolTip](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.ToolTip)

  Eine Standardimplementierung für QuickInfos, die zusätzliche Informationen beim Zeigen auf ein Zielelement bereitstellt. @xtype tooltip.

* treegrid

  [CQ.tree.TreeGrid](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.tree.TreeGrid)

  @xtype-Treegrid

* treepanel

  [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)

  „TreePanel“ ermöglicht das Anzeigen von Baumstruktur-Daten in einer Baumstruktur-Benutzeroberfläche.

  Zu TreePanel hinzugefügte [TreeNode](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode)s können Metadaten enthalten, die von der Anwendung in der Eigenschaft [attributes](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreeNode) verwendet werden.

* trigger

  [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)

  Stellt einen benutzerfreundlichen Wrapper für TextFields bereit, der eine klickbare Auslöserschaltfläche hinzufügt (ähnelt einem Standard-Kombinationsfeld). Für den Auslöser gibt es keine Standardaktion. Sie müssen eine Funktion zuweisen, um den Klick-Handler für den Auslöser durch Überschreiben von [onTriggerClick](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField) zu implementieren. Sie können ein TriggerField direkt erstellen, da es genauso wie ein Kombinationsfeld gerendert wird.

* uploaddialog

  [CQ.UploadDialog](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UploadDialog)

  Mit UploadDialog können Benutzer Dateien ins Repository hochladen. Erstellt einen neuen UploadDialog.

* userinfo

  [CQ.UserInfo](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.UserInfo)

  Ein Element der Symbolleiste, das den aktuellen Benutzernamen anzeigt und Benutzeraktionen wie das Bearbeiten von Benutzereigenschaften und die Personifikation ermöglicht.

* viewport

  [CQ.Ext.Viewport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Viewport)

  Ein spezieller Container, der den sichtbaren Anwendungsbereich (das Browser-Darstellungsfeld) darstellt.

  „Viewport“ wird automatisch im Hauptteil des Dokuments gerendert. Die Größe wird automatisch an das Browser-Darstellungsfeld angepasst und die Größenänderung des Fensters verwaltet. Es kann nur ein Viewport erstellt werden.

* window

  [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)

  Ein spezielles Bedienfeld, das als Anwendungsfenster verwendet werden soll. Fenster sind standardmäßig nicht verankert, [anpassbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) und per Maus [ziehbar](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window). Fenster können auf die Größe des Darstellungsfelds [maximiert](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window), auf die ursprüngliche Größe zurückgesetzt oder [minimiert](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window) werden.

* xmlstore

  [CQ.Ext.data.XmlStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlStore)

  Eine kleine Helferklasse, die das Erstellen von [CQ.Ext.data.Store](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.Store)aus XML-Daten erleichtert. Ein XmlStore wird automatisch mit einer [CQ.Ext.data.XmlReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.XmlReader).

  **Cqinclude>**: Ein Pseudo-xtype, das Widget-Definitionen aus unterschiedlichen Pfaden im Repository enthält. Es wird in der Regel in Seitendialogfeldern verwendet. Für diesen xtype gibt es keine tatsächliche JavaScript-Widget-Klasse. Es wird durch die formatData()-Funktion der CQ.Util-Klasse verarbeitet. Weitere Informationen finden Sie in diesem Knowledge Base-Artikel.
