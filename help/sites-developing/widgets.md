---
title: Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche)
seo-title: Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche)
description: Die webbasierte Oberfläche von AEM nutzt AJAX und andere moderne Browsertechnologien, um WYSIWYG-Bearbeitung und -Formatierung von Inhalten durch Autoren direkt auf der Webseite zu ermöglichen.
seo-description: Die webbasierte Oberfläche von AEM nutzt AJAX und andere moderne Browsertechnologien, um WYSIWYG-Bearbeitung und -Formatierung von Inhalten durch Autoren direkt auf der Webseite zu ermöglichen.
uuid: eb3da415-cbef-4766-a28e-837e238a4156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 7b234f1f-4470-4de1-a3c3-ab19e5e001ad
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche){#using-and-extending-widgets-classic-ui}

>[!NOTE]
>
>Diese Seite beschreibt die Verwendung von Widgets in der klassischen Benutzeroberfläche, die in AEM 6.4 nicht mehr unterstützt wurde.
>
>Adobe empfiehlt, die moderne [Touch-optimierte Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md) zu verwenden, die auf [Coral-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#coral-ui) und [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components) basiert.

Die webbasierte Oberfläche von Adobe Experience Manager nutzt AJAX und andere moderne Browsertechnologien, um WYSIWYG-Bearbeitung und -Formatierung von Inhalten durch Autoren direkt auf der Webseite zu ermöglichen.

Adobe Experience Manager (AEM) verwendet die [ExtJS](https://www.sencha.com/)-Widgetbibliothek, die die besonders ausgereiften Benutzeroberflächenelemente bereitstellt, die in allen wichtigen Browsern funktionieren und die Erstellung von Benutzeroberflächen in Desktopqualität ermöglichen.

Diese Widgets sind in AEM enthalten und können nicht nur von AEM, sondern auch von jeder mit AEM erstellten Website verwendet werden.

Eine vollständige Übersicht aller verfügbaren Widgets in AEM finden Sie in der [Widget-API-Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html) oder der [Liste der bestehenden X-Typen](/help/sites-developing/xtypes.md). Darüber hinaus zeigen zahlreiche Beispiele auf der Website von [Sencha](https://www.sencha.com/products/extjs/examples/), dem Eigentümer des Frameworks, wie das ExtJS-Framework zu verwenden ist.

Auf dieser Seite erhalten Sie einige Einblicke in die Verwendung und Erweiterung von Widgets. Zuerst wird beschrieben, wie [clientseitiger Code in eine Seite eingefügt wird](#including-the-client-sided-code-in-a-page). Dann werden einige Beispielkomponenten beschrieben, die erstellt wurden, um einige grundlegende Anwendungs- und Erweiterungsfälle zu illustrieren. Diese Komponenten stehen als das Paket **Using ExtJS Widgets** auf **Package Share** zur Verfügung.

Das Paket enthält Beispiele für:

* [Grundlegende Dialogfelder](#basic-dialogs), die mit vordefinierten Widgets erstellt wurden.
* [Dynamische Dialogfelder](#dynamic-dialogs), die mit vordefinierten Widgets und benutzerdefinierter JavaScript-Logik konfiguriert wurden.
* Dialogfelder, die auf [benutzerdefinierten Widgets](#custom-widgets) basieren.
* Ein [Baumstrukturbedienfeld](#tree-overview), das eine JCR-Baumstruktur unterhalb eines bestimmten Pfades anzeigt.
* Ein [Rasterbedienfeld](#grid-overview), das Daten im Tabellenformat anzeigt.

>[!NOTE]
>
>Die klassische Benutzeroberfläche von Adobe Experience Manager baut auf [ExtJS 3.4.0](https://extjs.cachefly.net/ext-3.4.0/docs/) auf.

## Einbauen von clientseitigem Code in eine Seite {#including-the-client-sided-code-in-a-page}

Clientseitiger JavaScript- und Stylesheet-Code sollte in einer Client-Bibliothek platziert werden.

Erstellen Sie eine Client-Bibliothek wie folgt:

1. Create a node below `/apps/<project>` with the following properties:

   * name=&quot;clientlib&quot;
   * jcr:mixinTypes=&quot;[mix:lockable]&quot;
   * jcr:primaryType=&quot;cq:ClientLibraryFolder&quot;
   * sling:resourceType=&quot;widgets/clientlib&quot;
   * categories=&quot;[&lt;category-name>]&quot;
   * dependencies=&quot;[cq.widgets]&quot;
   `Note: <category-name> is the name of the custom library (e.g. "cq.extjstraining") and is used to include the library on the page.`

1. Below `clientlib` create the `css` and `js` folders (nt:folder).

1. Below `clientlib` create the `css.txt` and `js.txt` files (nt:files). Diese TXT-Dateien listen die Dateien auf, die in der Bibliothek enthalten sind.

1. Edit `js.txt`: it needs to start with &#39; `#base=js`&#39; followed by the list of the files that will be aggregated by the CQ client library service, eg:

   ```
   #base=js
    components.js
    exercises.js
    CustomWidget.js
    CustomBrowseField.js
    InsertTextPlugin.js
   ```

1. Edit `css.txt`: it needs to start with &#39; `#base=css`&#39; followed by the list of the files that will be aggregated by the CQ client library service, eg:

   ```
   #base=css
    components.css
   ```

1. Platzieren Sie die JavaScript-Dateien, die der Bibliothek angehören, unterhalb des Ordners `js`.

1. Below the `css` folder, place the `.css` files and the resources used by the css files (e.g. `my_icon.png`).

>[!NOTE]
>
>Die oben beschriebene Verarbeitung von Stylesheets ist optional.

Fügen Sie die Client-Bibliothek wie folgt in die Seitenkomponenten-JSP ein:

* um sowohl JavaScript-Code als auch Stylesheets einzuschließen:
   `<ui:includeClientLib categories="<category-name1>, <category-name2>, ..."/>`
wobei `<category-nameX>` der Name der clientseitigen Bibliothek steht.

* nur JavaScript-Code einschließen:
   `<ui:includeClientLib js="<category-name>"/>`

Weitere Informationen finden Sie in der Beschreibung des Tags [&lt;ui:includeClientLib>](/help/sites-developing/taglib.md#lt-ui-includeclientlib).

In manchen Fällen darf eine Client-Bibliothek nur im Autorenmodus verfügbar sein und muss im Veröffentlichungsmodus ausgeschlossen werden. Dies erreichen Sie wie folgt:

```xml
    if (WCMMode.fromRequest(request) != WCMMode.DISABLED) {
        %><ui:includeClientLib categories="cq.collab.blog"/><%
    }
```

### Erste Schritte mit den Beispielen {#getting-started-with-the-samples}

To follow the tutorials on this page, install the package called **Using ExtJS Widgets** in a local AEM instance and create a sample page in which the components will be included. Gehen Sie dazu wie folgt vor:

1. In your AEM instance download the package called **Using ExtJS Widgets (v01)** from Package Share and install the package. It creates the project `extjstraining` below `/apps` in the repository.
1. Include the client library containing the scripts (js) and the stylesheet (css) in the head tag of the geometrixx page jsp, as you will include the sample components in a new page of the **Geometrixx** branch:
in **CRXDE Lite** open the file `/apps/geometrixx/components/page/headlibs.jsp` and add the `cq.extjstraining` category to the existing `<ui:includeClientLib>` tag as follows:
   `%><ui:includeClientLib categories="apps.geometrixx-main, cq.extjstraining"/><%`
1. Create a new page in the **Geometrixx** branch below `/content/geometrixx/en/products` and call it **Using ExtJS Widgets**.
1. Wechseln Sie in den Designmodus und fügen Sie alle Komponenten der Gruppe **Using ExtJS Widgets** dem Design von Geometrixx hinzu.
1. Go back in edit mode: the components of the group **Using ExtJS Widgets** are available in the Sidekick.

>[!NOTE]
>
>Die Beispiele auf dieser Seite basieren auf dem Geometrixx-Beispielinhalt, der nicht mehr im Lieferumfang von AEM enthalten ist, da er durch We.Retail ersetzt wurde. See the document [We.Retail Reference Implementation](/help/sites-developing/we-retail.md#we-retail-geometrixx) for how to download and install Geometrixx.

### Grundlegende Dialogfelder {#basic-dialogs}

Dialogfelder werden in der Regel verwendet, um Inhalte zu bearbeiten, aber auch nur zum Anzeigen von Informationen. Eine einfache Möglichkeit zum Anzeigen eines vollständigen Dialogfelds besteht darin, auf seine Darstellung im JSON-Format zuzugreifen. Verweisen Sie dazu Ihren Browser auf:

`https://localhost:4502/<path-to-dialog>.-1.json`

Die erste Komponente der Gruppe **Using ExtJS Widgets** im Sidekick wird mit **1. Dialog Basics** bezeichnet und umfasst vier grundlegende Dialogfelder, die mit standardmäßigen Widgets und ohne modifizierte JavaScript-Logik erstellt wurden. The dialogs are stored below `/apps/extjstraining/components/dialogbasics`. Die grundlegenden Dialogfelder sind:

* das Dialogfeld „“ (Knoten `full`full): Es zeigt ein Fenster mit drei Registerkarten mit jeweils zwei Textfeldern an.
* das Dialogfeld „Single Panel“ (Knoten `singlepanel`): Es zeigt ein Fenster mit einer Registerkarte mit zwei Textfeldern an.
* das Dialogfeld „Multi Panel“ (Knoten `multipanel`): Es zeigt dasselbe an wie das Dialogfeld „Full“, ist aber anders aufgebaut.
* das Dialogfeld „“ (Knoten `design`design): Es zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte weist ein Textfeld auf, ein Dropdown-Menü und einen ausblendbaren Textbereich. Die zweite Registerkarte verfügt über einen Feldsatz mit vier Textfeldern und einen ausblendbaren Feldsatz mit zwei Textfeldern.

Fügen Sie die Komponente **1. Dialog Basics** der Beispielseite hinzu:

1. Add the **1. Dialog Basics** component to the sample page from the **Using ExtJS Widgets** tab in the **Sidekick**.
1. Die Komponente zeigt einen Titel, etwas Text und einen Link **EIGENSCHAFTEN**: Klicken Sie auf den Link, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut auf den Link, um die Eigenschaften zu verbergen.

Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-60](assets/chlimage_1-60.png)

#### Beispiel 1: Dialogfeld „Full“{#example-full-dialog}

Das Dialogfeld **Full** zeigt ein Fenster mit drei Registerkarten mit jeweils zwei Textfeldern. Es ist das Standarddialogfeld der Komponente **Dialog Basics**. Die Eigenschaften sind:

* Is defined by a node: node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`.
* Displays 3 tabs (node type = `cq:Panel`).
* Each tab has 2 textfields (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wird durch den Knoten definiert:
   `/apps/extjstraining/components/dialogbasics/full`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/full.-1.json`

Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at45411pm](assets/screen_shot_2012-01-31at45411pm.png)

#### Beispiel 2: Dialogfeld „Single Panel“{#example-single-panel-dialog}

Das Dialogfeld **Single Panel** zeigt ein Fenster mit einer Registerkarte und zwei Textfeldern an. Die Eigenschaften sind:

* Displays 1 tab (node type = `cq:Dialog`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`)
* The tab has 2 textfields (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`)
* Wird durch den Knoten definiert:
   `/apps/extjstraining/components/dialogbasics/singlepanel`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/singlepanel.-1.json`
* Ein Vorteil gegenüber dem Dialogfeld **Full** besteht darin, dass weniger Konfiguration erforderlich ist.
* Empfohlene Verwendung: für einfache Dialogfelder, die Informationen anzeigen oder nur wenige Felder aufweisen.

So verwenden Sie das Dialogfeld „Single Panel“:

1. Ersetzen Sie das Dialogfeld der Komponente **Dialog Basics** durch das Dialogfeld **Single Panel**:
   1. In **CRXDE Lite**, delete the node: `/apps/extjstraining/components/dialogbasics/dialog`
   1. Klicken Sie auf **Alle speichern**, um die Änderungen zu speichern.
   1. Copy the node: `/apps/extjstraining/components/dialogbasics/singlepanel`
   1. Paste the copied node below: `/apps/extjstraining/components/dialogbasics`
   1. Wählen Sie die Node aus: und benennen Sie sie `/apps/extjstraining/components/dialogbasics/Copy of singlepanel`um `dialog`.
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at45952pm](assets/screen_shot_2012-01-31at45952pm.png)

#### Beispiel 3: Dialogfeld „Multi Panel“{#example-multi-panel-dialog}

Das Dialogfeld **Multi Panel** zeigt dasselbe wie das Dialogfeld **Full**, ist aber anders aufgebaut. Die Eigenschaften sind:

* Is defined by a node (node type = `cq:Dialog`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`).
* Displays 3 tabs (node type = `cq:Panel`).
* Each tab has 2 textfields (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wird durch den Knoten definiert:
   `/apps/extjstraining/components/dialogbasics/multipanel`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/multipanel.-1.json`
* Ein Vorteil gegenüber dem Dialogfeld **Full** besteht in der vereinfachten Struktur.
* Empfohlene Verwendung: für Dialogfelder mit mehreren Registerkarten.

So verwenden Sie das Dialogfeld &quot;Mehrere Bereiche&quot;:

1. Replace the dialog of the **Dialog Basics** component with the **Multi Panel** dialog:
follow the steps described for the [Example 2: Single Panel Dialog](#example-single-panel-dialog)
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at50119pm](assets/screen_shot_2012-01-31at50119pm.png)

#### Beispiel 4: Dialogfeld „Rich“{#example-rich-dialog}

Das Dialogfeld **Rich** zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte weist ein Textfeld auf, ein Dropdown-Menü und einen ausblendbaren Textbereich. Die zweite Registerkarte verfügt über einen Feldsatz mit vier Textfeldern und einen ausblendbaren Feldsatz mit zwei Textfeldern. Die Eigenschaften sind:

* Is defined by a node (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Displays 2 tabs (node type = `cq:Panel`).
* The first tab has a ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)` widget with a ` [textfield](/help/sites-developing/xtypes.md#textfield)` and a ` [selection](/help/sites-developing/xtypes.md#selection)` widget with 3 options, and a collapsible ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)` with a ` [textarea](/help/sites-developing/xtypes.md#textarea)` widget.
* The second tab has a ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)` widget with 4 ` [textfield](/help/sites-developing/xtypes.md#textfield)` widgets, and a collapsible `dialogfieldset` with 2 ` [textfield](/help/sites-developing/xtypes.md#textfield)` widgets.
* Wird durch den Knoten definiert:
   `/apps/extjstraining/components/dialogbasics/rich`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/dialogbasics/rich.-1.json`

So verwenden Sie das Dialogfeld **Rich**:

1. Replace the dialog of the **Dialog Basics** component with the **Rich** dialog:
follow the steps described for the [Example 2: Single Panel Dialog](#example-single-panel-dialog)
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at50429pm](assets/screen_shot_2012-01-31at50429pm.png) ![screen_shot_2012-01-31at50519pm](assets/screen_shot_2012-01-31at50519pm.png)

### Dynamische Dialogfelder {#dynamic-dialogs}

Die zweite Komponente der Gruppe **Using ExtJS Widgets** im Sidekick heißt **2. Dynamic Dialogs** und umfasst drei dynamische Dialogfelder, die mit standardmäßigen Widgets und **modifizierter JavaScript-Logik** erstellt wurden. The dialogs are stored below `/apps/extjstraining/components/dynamicdialogs`. Die dynamischen Dialoge sind:

* das Dialogfeld „Switch Tabs“ (Knoten `switchtabs`): Es zeigt ein Fenster mit zwei Registerkarten. Die erste Registerkarte weist eine Navigationsauswahl mit drei Optionen auf: Wenn eine Option ausgewählt ist, wird eine Registerkarte zu der Option angezeigt. Die zweite Registerkarte weist zwei Textfelder auf.
* das Dialogfeld „“ (Knoten `arbitrary`arbitrary): Es zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein Feld, in das Sie Assets ziehen oder hochladen können, und ein Feld, das Informationen über die Seite, die es umfasst, und das Asset (falls auf eines verwiesen wird) anzeigt.
* the Toggle Fields dialog ( `togglefield` node): it displays a window with one tab. Die Registerkarte verfügt über ein Kontrollkästchen: Ist es aktiviert, wird ein Feldsatz mit zwei Textfeldern angezeigt.

To include the **2. Dynamic Dialogs** component on the sample page:

1. Add the **2. Dynamic Dialogs** component to the sample page from the **Using ExtJS Widgets** tab in the **Sidekick**.
1. Die Komponente zeigt einen Titel, etwas Text und einen Link **EIGENSCHAFTEN**: Klicken Sie, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.

Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-61](assets/chlimage_1-61.png)

#### Beispiel 1: Dialogfeld „Switch Tabs“{#example-switch-tabs-dialog}

Das Dialogfeld **Switch Tabs** zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte weist eine Navigationsauswahl mit drei Optionen auf: Wenn eine Option ausgewählt ist, wird eine Registerkarte zu der Option angezeigt. Die zweite Registerkarte weist zwei Textfelder auf.

Die wichtigsten Eigenschaften sind:

* Is defined by a node (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Zeigt zwei Registerkarten (node type = `cq:Panel`): eine Auswahlregisterkarte und eine zweite Registerkarte, die von der Auswahl auf der ersten Registerkarte abhängt (drei Optionen).
* Has 3 optional tabs (node type = `cq:Panel`), each one has 2 textfields (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`). Es wird jeweils nur eine optionale Registerkarte angezeigt.
* Wird durch den `switchtabs` Knoten unter:
   `/apps/extjstraining/components/dynamicdialogs/switchtabs`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/switchtabs.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* Der Knoten &quot;dialog&quot;verfügt über einen `beforeshow`&quot;Listener, der alle optionalen Registerkarten ausblendet, bevor das Dialogfeld angezeigt wird:
   `beforeshow="function(dialog){Ejst.x2.manageTabs(dialog.items.get(0));}"`
   `dialog.items.get(0)` Ruft das Tabulatorbedienfeld mit dem Auswahlfeld und den 3 optionalen Bereichen ab.
* The `Ejst.x2` object is defined in the `exercises.js` file at:
   `/apps/extjstraining/clientlib/js/exercises.js`
* In the `Ejst.x2.manageTabs()` method, as the value of `index` is -1, all the optional tabs are hidden (i goes from 1 to 3).
* The selection tab has 2 listeners: one that shows the selected tab when the dialog is loaded (&quot; `loadcontent`&quot; event) and one that shows the selected tab when the selection is changed (&quot; `selectionchanged`&quot; event):
   `loadcontent="function(field,rec,path){Ejst.x2.showTab(field);}"`
   `selectionchanged="function(field,value){Ejst.x2.showTab(field);}"`
* In the `Ejst.x2.showTab()` method:
   `field.findParentByType('tabpanel')` ruft das Tabulatorbedienfeld ab, das alle Registerkarten enthält ( `field` entspricht dem Auswahl-Widget)
   `field.getValue()` ruft den Wert der Auswahl ab, z. B.: tab2
   `Ejst.x2.manageTabs()` zeigt die ausgewählte Registerkarte an.
* Each optional tab has a listener that hides the tab on &quot; `render`&quot; event:
   `render="function(tab){Ejst.x2.hideTab(tab);}"`
* In the `Ejst.x2.hideTab()` method:
   ist `tabPanel` das Registerkartenbedienfeld, das alle Registerkarten enthält.
   ist `index` der Index der optionalen Registerkarte.
   `tabPanel.hideTabStripItem(index)` Blendet die Registerkarte aus

Dies wird wie folgt angezeigt:

![screen_shot_2012-02-01at114745am](assets/screen_shot_2012-02-01at114745am.png)

#### Beispiel 2: Dialogfeld „Arbitrary“{#example-arbitrary-dialog}

Sehr oft zeigt ein Dialogfeld Inhalte aus der zugrunde liegenden Komponente an. Das hier beschriebene Dialogfeld **Arbitrary** zeigt Inhalte aus einer anderen Komponente an.

Das Dialogfeld **Arbitrary** zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über zwei Felder: eines, in das Sie Assets ziehen oder hochladen können, und eines, das Informationen über die Seite, die es umfasst, und das Asset (falls auf eines verwiesen wird) anzeigt.

Die wichtigsten Eigenschaften sind:

* Is defined by a node (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Displays 1 tabpanel widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) with 1 panel (node type = `cq:Panel`)
* The panel has a smartfile widget (node type = `cq:Widget`, xtype = ` [smartfile](/help/sites-developing/xtypes.md#smartfile)`) and an ownerdraw widget (node type = `cq:Widget`, xtype = ` [ownerdraw](/help/sites-developing/xtypes.md#ownerdraw)`)
* Wird durch den `arbitrary` Knoten unter:
   `/apps/extjstraining/components/dynamicdialogs/arbitrary`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/arbitrary.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* The ownerdraw widget has a &quot; `loadcontent`&quot; listener that shows info about the page containing the component and the asset referenced by the smartfile widget when the content is loaded:
   `loadcontent="function(field,rec,path){Ejst.x2.showInfo(field,rec,path);}"`
   `field` wird mit dem ownerdraw-Objekt festgelegt
   `path` wird mit dem Inhalts-Pfad der Komponente festgelegt (z. B.: /content/geometrixx/de/products/triangle/ui-tutorial/jcr:content/par/dynamicdialogs)
* The `Ejst.x2` object is defined in the `exercises.js` file at:
   `/apps/extjstraining/clientlib/js/exercises.js`
* In the `Ejst.x2.showInfo()` method:
   ist `pagePath` der Pfad der Seite, die die Komponente enthält.
   stellt `pageInfo` die Seiteneigenschaften im JSON-Format dar.
   ist `reference` der Pfad des referenzierten Assets.
   stellt `metadata` die Metadaten des Assets im JSON-Format dar.
   `ownerdraw.getEl().update(html);` zeigt den erstellten HTML-Code im Dialogfeld

So verwenden Sie das Dialogfeld **Arbitrary**:

1. Replace the dialog of the **Dynamic Dialog** component with the **Arbitrary** dialog:
follow the steps described for the [Example 2: Single Panel Dialog](#example-single-panel-dialog)
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at115300am](assets/screen_shot_2012-02-01at115300am.png)

#### Beispiel 3: Dialogfeld „Toggle Fields“{#example-toggle-fields-dialog}

Das Dialogfeld **Toggle Fields** zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein Kontrollkästchen: Ist es aktiviert, wird ein Feldsatz mit zwei Textfeldern angezeigt.

Die wichtigsten Eigenschaften sind:

* Is defined by a node (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Displays 1 tabpanel widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#textpanel)`) with 1 panel (node type = `cq:Panel`).
* The panel has a selection/checkbox widget (node type = `cq:Widget`, xtype = ` [selection](/help/sites-developing/xtypes.md#selection)`, type = ` [checkbox](/help/sites-developing/xtypes.md#checkbox)`) and a collapsible dialogfieldset widget (node type = `cq:Widget`, xtype = ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)`) that is hidden by default, with 2 textfield widgets (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wird durch den `togglefields` Knoten unter:
   `/apps/extjstraining/components/dynamicdialogs/togglefields`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/togglefields.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* the selection tab has 2 listeners: one that shows the dialogfieldset when the content is loaded (&quot; `loadcontent`&quot; event) and one that shows the dialogfieldset when the selection is changed (&quot; `selectionchanged`&quot; event):
   `loadcontent="function(field,rec,path){Ejst.x2.toggleFieldSet(field);}"`
   `selectionchanged="function(field,value){Ejst.x2.toggleFieldSet(field);}"`
* The `Ejst.x2` object is defined in the `exercises.js` file at:
   `/apps/extjstraining/clientlib/js/exercises.js`
* In the `Ejst.x2.toggleFieldSet()` method:
   `box` ist das Auswahlobjekt
   ist `panel` das Bedienfeld, das das selection- und das dialogfieldset-Widget enthält.
   `fieldSet` ist das dialogFieldSet-Objekt
   `show` ist der Wert der Auswahl (true oder false), basierend auf &#39; `show`&#39;, wenn das Dialogfeld angezeigt wird oder nicht

To use the **Toggle Fields** dialog:

1. Replace the dialog of the **Dynamic Dialog** component with the **Toggle Fields** dialog:
follow the steps described for the [Example 2: Single Panel Dialog](#example-single-panel-dialog)
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at115518am](assets/screen_shot_2012-02-01at115518am.png)

### Benutzerdefinierte Widgets {#custom-widgets}

Die direkt einsatzbereiten und im Lieferumfang von AEM enthaltenen Widgets sollten die meisten Anwendungsfälle abdecken. Manchmal kann es jedoch erforderlich sein, ein benutzerdefiniertes Widget zu erstellen, um eine projektspezifische Anforderung abzudecken. Benutzerdefinierte Widgets werden erstellt, indem vorhandene erweitert werden. Das Paket **Using ExtJS Widgets** enthält drei Dialogfelder, die drei verschiedene benutzerdefinierte Widgets verwenden, um die ersten Schritte mit der Anpassung zu vereinfachen:

* Das Dialogfeld „Multi Field“ (Knoten `multifield`) zeigt ein Fenster mit einer Registerkarte. Die Registerkarte verfügt über ein benutzerdefiniertes multifield-Widget mit zwei Feldern: Ein Dropdown-Menü mit zwei Optionen und ein Textfeld. Da es auf dem im Lieferumfang enthaltenen `multifield`-Widget (mit nur einem Textfeld) basiert, verfügt es über alle Funktionen des `multifield`-Widgets.
* Das Dialogfeld „Tree Browse“ (`treebrowse`-Knoten) zeigt ein Fenster mit einer Registerkarte, die ein Pfadbrowser-Widget enthält: Wenn Sie auf den Pfeil klicken, wird ein Fenster geöffnet, in dem Sie eine Hierarchie durchsuchen und ein Element auswählen können. Der Pfad des Elements wird dann dem Pfadfeld hinzugefügt und wird beibehalten, wenn das Dialogfeld geschlossen wird.
* Ein Dialogfeld, das auf dem Rich-Text-Editor-Plug-in basiert (Knoten `rteplugin`) und dem Rich-Text-Editor eine benutzerdefinierte Schaltfläche hinzufügt, mit der benutzerdefinierter Text in den Haupttext eingefügt werden kann. Es besteht aus einem `richtext`-Widget (RTE) und einer benutzerdefinierten Funktion, die durch den RTE-Plug-in-Mechanismus hinzugefügt wird.

Die benutzerdefinierten Widgets und das Plug-in sind in der Komponente **3. Custom Widgets** des Pakets **Using ExtJS Widgets** enthalten. Fügen Sie diese Komponente wie folgt der Beispielseite hinzu:

1. Add the **3. Custom Widgets** component to the sample page from the **Using ExtJS Widgets** tab in the **Sidekick**.
1. Die Komponente zeigt einen Titel, etwas Text und, wenn Sie auf den Link **EIGENSCHAFTEN** klicken, die Eigenschaften des im Repository gespeicherten Absatzes an. Durch erneutes Klicken werden die Eigenschaften verborgen.
Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-62](assets/chlimage_1-62.png)

#### Beispiel 1: Custom Multifield-Widget {#example-custom-multifield-widget}

Das auf dem **Custom Multifield**-Widget basierende Dialogfeld zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein benutzerdefiniertes multifield-Widget mit zwei Feldern (im Gegensatz zur Standardversion mit einem Feld): Ein Dropdown-Menü mit zwei Optionen und ein Textfeld.

Das auf dem **Custom Multifield**-Widget basierende Dialogfeld:

* Is defined by a node (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Displays 1 tabpanel widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) containing a panel (node type = `cq:Widget`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`).
* The panel has a `multifield` widget (node type = `cq:Widget`, xtype = ` [multifield](/help/sites-developing/xtypes.md#multifield)`).
* The `multifield` widget has a fieldconfig (node type = `nt:unstructured`, xtype = `ejstcustom`, optionsProvider = `Ejst.x3.provideOptions`) that is based on the custom xtype &#39; `ejstcustom`&#39;:
   * &#39; `fieldconfig`&#39; is a config option of the ` [CQ.form.MultiField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.MultiField)` object.
   * &#39; `optionsProvider`&#39; is a configuration of the `ejstcustom` widget. Er wird mit der `Ejst.x3.provideOptions` Methode festgelegt, die in `exercises.js` folgender Tabelle definiert ist:
      `/apps/extjstraining/clientlib/js/exercises.js`
und gibt 2 Optionen zurück.
* Wird durch den `multifield` Knoten unter:
   `/apps/extjstraining/components/customwidgets/multifield`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/customwidgets/multifield.-1.json`

Das benutzerdefinierte Multifield-Widget (xtype = `ejstcustom`):

* Ist ein JavaScript-Objekt namens `Ejst.CustomWidget`.
* Is defined in the `CustomWidget.js` javascript file at:
   `/apps/extjstraining/clientlib/js/CustomWidget.js`
* Extends the ` [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField)` widget.
* Has 3 fields: `hiddenField` (Textfield), `allowField` (ComboBox) and `otherField` (Textfield)
* Overrides `CQ.Ext.Component#initComponent` to add the 3 fields:
   * `allowField` ist ein [CQ.form.Selection](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.Selection)-Objekt vom Typ „select“. optionsProvider ist eine Konfiguration des Selection-Objekts, das mit der optionsProvider-Konfiguration des CustomWidget instanziiert wird, die im Dialogfeld
   * `otherField` ist ein [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)-Objekt.
* Überschreibt die Methoden `setValue``getValue` und `getRawValue` von [CQ.form.CompositeField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.CompositeField) , um den Wert von CustomWidget mit folgendem Format festzulegen und abzurufen:
   `<allowField value>/<otherField value>, e.g.: 'Bla1/hello'`.
* Registriert sich als &quot; `ejstcustom`&quot; xtype:
   `CQ.Ext.reg('ejstcustom', Ejst.CustomWidget);`

Das auf dem **Custom Multifield**-Widget basierende Dialogfeld wird wie folgt angezeigt:

![screen_shot_2012-02-01at115840am](assets/screen_shot_2012-02-01at115840am.png)

#### Beispiel 2: Benutzerdefiniertes Treebrowse-Widget {#example-custom-treebrowse-widget}

Das auf dem **Treebrowse**-Widget basierende benutzerdefinierte Dialogfeld zeigt ein Fenster mit einer Registerkarte, die ein benutzerdefiniertes Pfadbrowser-Widget enthält: Wenn Sie auf den Pfeil klicken, wird ein Fenster geöffnet, in dem Sie eine Hierarchie durchsuchen und ein Element auswählen können. Der Pfad des Elements wird dann dem Pfadfeld hinzugefügt und wird beibehalten, wenn das Dialogfeld geschlossen wird.

Das benutzerdefinierte treebrowse-Dialogfeld:

* Is defined by a node (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Displays 1 tabpanel widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) containing a panel (node type = `cq:Widget`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`).
* The panel has a custom widget (node type = `cq:Widget`, xtype = `ejstbrowse`)
* Wird durch den `treebrowse` Knoten unter:
   `/apps/extjstraining/components/customwidgets/treebrowse`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/customwidgets/treebrowse.-1.json`

Das benutzerdefinierte treebrowse-Widgets (xtype = `ejstbrowse`):

* Ist ein JavaScript-Objekt namens `Ejst.CustomWidget`.
* Is defined in the `CustomBrowseField.js` javascript file at:
   `/apps/extjstraining/clientlib/js/CustomBrowseField.js`
* Extends ` [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)`.
* Definiert ein Fenster zum Durchsuchen namens `browseWindow`.
* Overrides ` [CQ.Ext.form.TriggerField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TriggerField)#onTriggerClick` to show the browse window when the arrow is clicked.
* Definiert ein [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)-Objekt:
   * It gets its data by calling the servlet registered at `/bin/wcm/siteadmin/tree.json`.
   * Its root is &quot; `apps/extjstraining`&quot;.
* Defines a `window` object ( ` [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)`):
   * Basierend auf dem vordefinierten Bedienfeld.
   * Weist eine **OK**-Schaltfläche auf, die den Wert des ausgewählten Pfads festlegt und das Bedienfeld ausblendet.
* Das Fenster wird unterhalb des Feldes **Pfad** verankert.
* Der ausgewählte Pfad wird bei einem `show`-Ereignis vom Durchsuchfeld an das Fenster weitergegeben.
* Registriert sich als &quot; `ejstbrowse`&quot; xtype:
   `CQ.Ext.reg('ejstbrowse', Ejst.CustomBrowseField);`

To use the **Custom Treebrowse** widget based dialog:

1. Replace the dialog of the **Custom Widgets** component with the **Custom Treebrowse** dialog:
follow the steps described for the [Example 2: Single Panel Dialog](#example-single-panel-dialog)
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at120104pm](assets/screen_shot_2012-02-01at120104pm.png)

#### Beispiel 3: Rich-Text-Editor (RTE)-Plug-in {#example-rich-text-editor-rte-plug-in}

Das auf dem **Rich-Text-Editor (RTE)-Plug-in** basierende Dialogfeld ist ein auf dem Rich-Text-Editor basierendes Dialogfeld, das eine benutzerdefinierte Schaltfläche aufweist, mit der benutzerdefinierter Text in eckigen Klammern eingefügt wird. Der benutzerdefinierte Text kann auch anhand einer serverseitigen Logik geparst werden (in diesem Beispiel nicht implementiert), um beispielsweise Text hinzuzufügen, der am jeweiligen Pfad definiert ist:

Das auf dem **RTE-Plug-in** basierende Dialogfeld:

* Wird durch den Knoten rteplugin unter:
   `/apps/extjstraining/components/customwidgets/rteplugin`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/customwidgets/rteplugin.-1.json`
* The `rtePlugins` node has a child node `inserttext` (node type = `nt:unstructured`) that is named after the plugin. Er weist eine Eigenschaft mit der Bezeichnung `features` auf, die definiert, welche der Plug-in-Funktionen für den RTE verfügbar sind.

Das RTE-Plug-in:

* Ist ein JavaScript-Objekt namens `Ejst.InsertTextPlugin`.
* Is defined in the `InsertTextPlugin.js` javascript file at:
   `/apps/extjstraining/clientlib/js/InsertTextPlugin.js`
* Extends the ` [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)` object.
* Die folgenden Methoden definieren das ` [CQ.form.rte.plugins.Plugin](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)`-Objekt und werden im implementierenden Plug-in überschrieben:
   * `getFeatures()` gibt ein Array aller Funktionen zurück, die vom Plug-in bereitgestellt werden.
   * `initializeUI()` fügt die neue Schaltfläche der RTE-Symbolleiste hinzu.
   * `notifyPluginConfig()` zeigt Titel und Text an, wenn auf die Schaltfläche gezeigt wird.
   * `execute()` wird aufgerufen, wenn auf die Schaltfläche geklickt wird, und führt die Plug-in-Aktion durch: Sie zeigt ein Fenster an, in dem Text definiert wird, der eingeschlossen werden soll.
* `insertText()` fügt einen Text anhand des entsprechenden Dialogfeldobjekts `Ejst.InsertTextPlugin.Dialog` ein (siehe unten).
* `executeInsertText()` wird durch die `apply()` Methode des Dialogfelds aufgerufen, die ausgelöst wird, wenn auf die Schaltfläche **OK** geklickt wird.
* Registriert sich als Plugin `inserttext`&quot;:
   `CQ.form.rte.plugins.PluginRegistry.register("inserttext", Ejst.InsertTextPlugin);`
* Das `Ejst.InsertTextPlugin.Dialog`-Objekt definiert das Dialogfeld, das geöffnet wird, wenn auf die Plug-in-Schaltfläche geklickt wird. Das Dialogfeld besteht aus einem Bedienfeld, einem Formular, einem Textfeld und zwei Schaltflächen (**OK** und **Abbrechen**).

So verwenden Sie das auf dem **Rich-Text-Editor (RTE)-Plug-in** basierende Dialogfeld:

1. Ersetzen Sie das Dialogfeld der Komponente **Custom Widgets** durch das auf dem **Rich-Text-Editor (RTE)-Plug-in** basierende Dialogfeld: Führen Sie die in [Beispiel 2: Dialogfeld „Single Panel“](#example-single-panel-dialog) beschriebenen Schritte aus.
1. Bearbeiten Sie die Komponente.
1. Klicken Sie auf das letzte Symbol rechts (das Symbol mit vier Pfeilen). Enter a path and click **OK**:
The path is displayed within brackets ([ ]).
1. Klicken Sie auf **OK**, um den Rich-Text-Editor zu schließen.

Das auf dem **Rich-Text-Editor (RTE)-Plug-in** basierende Dialogfeld wird wie folgt angezeigt:

![screen_shot_2012-02-01at120254pm](assets/screen_shot_2012-02-01at120254pm.png)

>[!NOTE]
>
>This example only shows how to implement the client-side part of the logic: the placeholders (*[text]*) have then to be parsed on the server-side explicitly (e.g. in the component JSP).

### Tree Overview {#tree-overview}

Das im Lieferumfang enthaltene ` [CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)`-Objekt bietet eine baumstrukturierte Benutzeroberflächendarstellung baumstrukturierter Daten. Die im Paket **Using ExtJS Widgets** enthaltene Komponente „Tree Overview“ zeigt die Verwendung des Objekts `TreePanel` zur Anzeige einer JCR-Baumstruktur unterhalb eines gegebenen Pfads. Das Fenster selbst kann an- bzw. abgedockt werden. In diesem Beispiel wird die Fensterlogik in die Komponenten-JSP zwischen &lt;script>&lt;/script>-Tags eingebunden.

Fügen Sie die Komponente **Tree Overview** wie folgt der Beispielseite hinzu:

1. Add the **4. Tree Overview** component to the sample page from the **Using ExtJS Widgets** tab in the **Sidekick**.
1. Die Komponente zeigt:
   * einen Titel und etwas Text.
   * einen **EIGENSCHAFTEN**-Link: Klicken Sie, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.
   * ein frei bewegliches Fenster mit einer Baumstrukturdarstellung des Repositorys, das erweitert werden kann.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at120639pm](assets/screen_shot_2012-02-01at120639pm.png)

Die Komponente „Tree Overview“:

* Wird definiert unter:
   `/apps/extjstraining/components/treeoverview`

* Ihr Dialogfeld ermöglicht das Festlegen der Fenstergröße und das An- bzw.- Abdocken des Fensters (weitere Details unten).

Die Komponenten-JSP:

* Ruft die Breite, Höhe und angedockten Eigenschaften aus dem Repository ab.
* Zeigt Text zum Datenformat des Baumstrukturüberblicks an.
* Bettet die Fensterlogik zwischen JavaScript-Tags in die Komponenten-JSP ein.
* Wird definiert unter:
   `apps/extjstraining/components/treeoverview/content.jsp`

Der in die Komponenten-JSP eingebettete JavaScript-Code:

* Definiert ein `tree`-Objekt, indem versucht wird, ein Baumstrukturfenster von der Seite abzurufen.
* If the window displaying the tree does not exist, `treePanel` ([CQ.Ext.tree.TreePanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)) is created:
   * `treePanel` enthält die Daten, anhand derer das Fenster erstellt wird.
   * Die Daten werden abgerufen, indem das Servlet aufgerufen wird, registriert unter:
      `/bin/wcm/siteadmin/tree.json`
* The `beforeload` listener makes sure the clicked node is loaded.
* The `root` object sets the path `apps/extjstraining` as the tree root.
* `tree` ( ` [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)`) auf Basis der vordefinierten Einstellung festgelegt `treePanel`und angezeigt wird mit:
   `tree.show();`
* Wenn das Fenster bereits vorhanden ist, wird es anhand der aus dem Repository abgerufenen Breite, Höhe und angedockten Eigenschaften angezeigt.

Das Komponentendialogfeld:

* Zeigt eine Registerkarte mit zwei Feldern zum Festlegen der Größe (Breite und Höhe) des Fensters des Baumstrukturüberblicks und ein Feld zum An-/Abdocken des Fensters.
* Is defined by a node (node type = `cq:Dialog`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`).
* The panel has a sizefield widget (node type = `cq:Widget`, xtype = ` [sizefield](/help/sites-developing/xtypes.md#sizefield)`) and a selection widget (node type = `cq:Widget`, xtype = ` [selection](/help/sites-developing/xtypes.md#selection)`, type = `radio`) with 2 options (true/false)
* Wird durch den Knoten dialog unter:
   `/apps/extjstraining/components/treeoverview/dialog`
* Wird im JSON-Format wiedergegeben, indem Sie Folgendes anfordern:
   `https://localhost:4502/apps/extjstraining/components/treeoverview/dialog.-1.json`
* Wird wie folgt angezeigt:

![screen_shot_2012-02-01at120745pm](assets/screen_shot_2012-02-01at120745pm.png)

### Grid Overview {#grid-overview}

Ein „Grid Panel“ stellt Daten in tabellarischer Form als Zeilen und Spalten dar. Es setzt sich aus Folgendem zusammen:

* Store: das Modell, das die Datendatensätze enthält (Zeilen)
* Spaltenmodell: das Spaltendesign
* Ansicht: fasst die Benutzeroberfläche zusammen
* Auswahlmodell: das Auswahlverhalten

The Grid Overview component included in the **Using ExtJS Widgets** package shows how to display data in a tabular format:

* Das Beispiel 1 verwendet statische Daten.
* Beispiel 2 verwendet Daten, die aus dem Repository abgerufen wurden.

So fügen Sie die Komponente &quot;Rasterübersicht&quot;zur Beispielseite hinzu:

1. Add the **5. Grid Overview** component to the sample page from the **Using ExtJS Widgets** tab in the **Sidekick**.
1. Die Komponente zeigt:
   * ein Titel mit Text
   * einen **EIGENSCHAFTEN**-Link: Klicken Sie, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.
   * ein frei bewegbares Fenster, das Daten im Tabellenformat enthält.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at121109pm](assets/screen_shot_2012-02-01at121109pm.png)

#### Beispiel 1: Standardraster {#example-default-grid}

In der von Adobe ausgelieferten Version zeigt die Komponente **Grid Overview** ein Fenster mit statischen Daten in tabellarischer Form. In diesem Beispiel wird die Logik auf zwei Arten in die Komponenten-JSP eingebunden:

* Die generische Logik wird zwischen &lt;script>&lt;/script>-Tags definiert.
* Die spezifische Logik steht in einer separaten JS-Datei zur Verfügung und ist in der JSP verlinkt. Diese Einrichtung ermöglicht es, einfach zwischen den beiden Logiken (statisch/dynamisch) umzuschalten, indem die gewünschten &lt;script>-Tags kommentiert werden.

Die Komponente „Grid Overview“:

* Wird definiert unter:
   `/apps/extjstraining/components/gridoverview`
* Ihr Dialogfeld ermöglicht das Festlegen der Fenstergröße und das An- bzw.- Abdocken des Fensters.

Die Komponenten-JSP:

* Ruft die Breite, Höhe und angedockten Eigenschaften aus dem Repository ab.
* Zeigt Text als Einführung zum Datenformat des Rasterüberblicks an.
* Verweist auf JavaScript-Code, der das GridPanel-Objekt definiert:
   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script>`
   `defaultgrid.js` definiert einige statische Daten als Grundlage für das GridPanel-Objekt.
* Bettet zwischen JavaScript-Tags JavaScript-Code ein, der das Window-Objekt definiert, das das GridPanel-Objekt verbraucht.
* Wird definiert unter:
   `apps/extjstraining/components/gridoverview/content.jsp`

Der in die Komponenten-JSP eingebettete JavaScript-Code:

* Defines the `grid` object by trying to retrieve the window component from the page:
   `var grid = CQ.Ext.getCmp("<%= node.getName() %>-grid");`
* If `grid` does not exist, a [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel) object ( `gridPanel`) is defined by calling the `getGridPanel()` method (see below). Diese Methode wird in `defaultgrid.js` definiert.
* `grid` ist ein ` [CQ.Ext.Window](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.Window)` Objekt, basierend auf dem vordefinierten GridPanel, und wird angezeigt: `grid.show();`
* Ist `grid` bereits vorhanden, wird es anhand der aus dem Repository abgerufenen Breite, Höhe und angedockten Eigenschaften angezeigt.

The javascript file ( `defaultgrid.js`) referenced in the component jsp defines the `getGridPanel()` method which is called by the script embedded in the JSP and returns a ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` object, based on static data. Die Logik lautet wie folgt:

* `myData` ist ein Array statischer Daten, formatiert als Tabelle mit fünf Spalten und vier Zeilen.
* `store` ist ein `CQ.Ext.data.Store` Objekt, das konsumiert `myData`.
* `store` im Arbeitsspeicher geladen wird:
   `store.load();`
* `gridPanel` ist ein ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` Objekt, das Folgendes konsumiert `store`:
   * Die Spaltenbreiten werden jederzeit neu proportional angepasst:
      `forceFit: true`
   * Es kann jeweils nur eine Zeile ausgewählt werden:
      `singleSelect:true`

#### Beispiel 2: Verweissuchraster {#example-reference-search-grid}

When you install the package, the `content.jsp` of the **Grid Overview** component displays a grid that is based on static data. Es ist möglich, die Komponente so zu ändern, dass ein Raster mit den folgenden Eigenschaften angezeigt wird:

* Hat drei Spalten.
* Basiert auf Daten, die aus dem Repository abgerufen werden, indem ein Servlet aufgerufen wird.
* Die Zellen der letzten Spalte können bearbeitet werden. Der Wert wird in einer `test`-Eigenschaft unterhalb des Knotens gespeichert, der anhand des in der ersten Spalte angezeigten Pfades definiert wird.

As explained in the section before, the window object gets its ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` object by calling the `getGridPanel()` method defined in the `defaultgrid.js` file at `/apps/extjstraining/components/gridoverview/defaultgrid.js`. Die Komponente **Grid Overview **stellt eine andere Implementierung für die `getGridPanel()` Methode bereit, die in der `referencesearch.js` Datei unter `/apps/extjstraining/components/gridoverview/referencesearch.js`. Durch Wechseln der JS-Datei, auf die in der Komponenten-JSP verwiesen wird, basiert das Raster auf aus dem Repository abgerufenen Daten.

Wechseln Sie die JS-Datei, auf die in der Komponenten-JSP verwiesen wird:

1. In **CRXDE Lite**, in the `content.jsp` file of the component, comment the line that includes the `defaultgrid.js` file, so that it looks as follows:
   `<!-- script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script-->`
1. Remove the comment from the line that includes the `referencesearch.js` file, so that it looks as follows:
   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/referencesearch.js"></script>`
1. Speichern Sie die Änderungen.
1. Aktualisieren Sie die Beispielseite.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at121429pm](assets/screen_shot_2012-02-01at121429pm.png)

The javascript code referenced in the component jsp ( `referencesearch.js`) defines the `getGridPanel()` method called from the component jsp and returns a ` [CQ.Ext.grid.GridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)` object, based on data that are dynamically retrieved from the repository. Die Logik in `referencesearch.js` definiert dynamische Daten als Basis für das GridPanel:

* `reader` ist ein ` [CQ.Ext.data.JsonReader](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.JsonReader)`-Objekt, das die Servlet-Antwort im JSON-Format für drei Spalten liest.
* `cm` ist ein ` [CQ.Ext.grid.ColumnModel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel)` Objekt für 3 Spalten.
Die Zellen der Spalte &quot;Test&quot;können bearbeitet werden, da sie mit einem Editor definiert wurden:
   `editor: new [CQ.Ext.form.TextField](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.form.TextField)({})`
* Die Spalten sind sortierbar:
   `cm.defaultSortable = true;`
* `store` ist ein ` [CQ.Ext.data.GroupingStore](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)` Objekt:
   * it gets its data by calling the servlet registered at &quot; `/bin/querybuilder.json`&quot; with a few parameters used to filter the query
   * Es basiert auf dem vorher definierten `reader`.
   * Die Tabelle wird anhand der Spalte „**jcr:path**“ in aufsteigender Reihenfolge definiert.
* `gridPanel` ist ein ` [CQ.Ext.grid.EditorGridPanel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)` Objekt, das bearbeitet werden kann:
   * Es basiert auf dem vordefinierten `store` und auf dem Spaltenmodell `cm`.
   * Es kann jeweils nur eine Zeile ausgewählt werden:
      `sm: new [CQ.Ext.grid.RowSelectionModel](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.Ext.grid.RowSelectionModel)({singleSelect:true})`
   * Der `afteredit`-Listener stellt sicher, dass nach der Bearbeitung einer Zelle in der „**Test**“-Spalte Folgendes passiert:
      * the property &#39; `test`&#39; of the node at the path defined by the &quot;**jcr:path**&quot; column is set in the repository with the value of the cell
      * Wenn der POST erfolgreich ist, wird der Wert dem `store`-Objekt hinzugefügt, andernfalls wird er abgelehnt.
