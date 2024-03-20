---
title: Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche)
description: Die Web-basierte Oberfläche von Adobe Experience Manager nutzt AJAX und andere moderne Browser-Technologien, um WYSIWYG-Bearbeitung und -Formatierung von Inhalten durch Autorinnen und Autoren direkt auf der Web-Seite zu ermöglichen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
exl-id: 56a9591c-cd78-42e8-a5d7-6b48581d6af6
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '4896'
ht-degree: 94%

---

# Verwenden und Erweitern von Widgets (klassische Benutzeroberfläche){#using-and-extending-widgets-classic-ui}

>[!NOTE]
>
>Auf dieser Seite wird die Verwendung von Widgets innerhalb der klassischen Benutzeroberfläche beschrieben, die ab AEM 6.4 veraltet ist.
>
>Adobe empfiehlt die Verwendung der modernen [Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md), die auf der [Coral-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#coral-ui) und der [Granite-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components) basiert.

Die Web-basierte Oberfläche von Adobe Experience Manager (AEM) nutzt AJAX und andere moderne Browser-Technologien, um die WYSIWYG-Bearbeitung und -Formatierung von Inhalten durch Autorinnen und Autoren direkt auf der Web-Seite zu ermöglichen.

AEM verwendet die Widgets-Bibliothek [ExtJS](https://www.sencha.com/), die die hochoptimierten Elemente der Benutzeroberfläche bereitstellt, die in allen wichtigen Browsern funktionieren und die Erstellung von Benutzeroberflächen in Desktop-Qualität ermöglichen.

Diese Widgets sind in AEM enthalten und können nicht nur von AEM selbst verwendet werden, sondern auch von jeder Website, die mit AEM erstellt wurde.

Eine vollständige Übersicht aller verfügbaren Widgets in AEM finden Sie in der [Widget-API-Dokumentation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) oder der [Liste der bestehenden xtypes](/help/sites-developing/xtypes.md). Darüber hinaus zeigen zahlreiche Beispiele auf der Website von [Sencha](https://examples.sencha.com/extjs/7.6.0/), dem Eigentümer des Frameworks, wie das ExtJS-Framework zu verwenden ist.

Auf dieser Seite erhalten Sie einige Einblicke in die Verwendung und Erweiterung von Widgets. Zuerst wird beschrieben, wie [Client-seitiger Code in eine Seite eingefügt wird](#including-the-client-sided-code-in-a-page). Anschließend werden einige Beispielkomponenten beschrieben, die erstellt wurden, um einige grundlegende Verwendungen und Erweiterungen zu veranschaulichen. Diese Komponenten stehen als das Paket **Verwenden von ExtJS Widgets** auf **Package Share** zur Verfügung.

Das Paket enthält Beispiele für:

* [Grundlegende Dialogfelder](#basic-dialogs), die mit vordefinierten Widgets erstellt wurden.
* [Dynamische Dialogfelder](#dynamic-dialogs), die mit nativen Widgets und benutzerdefinierter JavaScript-Logik erstellt wurden.
* Dialogfelder, die auf [benutzerdefinierten Widgets](#custom-widgets) basieren.
* Ein [Baumstrukturbedienfeld](#tree-overview), das eine JCR-Baumstruktur unterhalb eines bestimmten Pfades anzeigt.
* Ein [Rasterbedienfeld](#grid-overview), das Daten im Tabellenformat anzeigt.

>[!NOTE]
>
>Die klassische Benutzeroberfläche von Adobe Experience Manager baut auf [ExtJS 3.4.0](https://extjs.cachefly.net/ext-3.4.0/docs/) auf.

## Einbauen von Client-seitigem Code in eine Seite {#including-the-client-sided-code-in-a-page}

Client-seitiger JavaScript- und Stylesheet-Code sollte in einer Client-Bibliothek platziert werden.

Erstellen Sie eine Client-Bibliothek wie folgt:

1. Erstellen Sie einen Knoten unterhalb von `/apps/<project>` mit den folgenden Eigenschaften:

   * name=&quot;clientlib&quot;
   * jcr:mixinTypes=&quot;[mix:lockable]&quot;
   * jcr:primaryType=&quot;cq:ClientLibraryFolder&quot;
   * sling:resourceType=&quot;widgets/clientlib&quot;
   * categories=&quot;[&lt;category-name>]&quot;
   * dependencies=&quot;[cq.widgets]&quot;

   `Note: <category-name> is the name of the custom library (for example, "cq.extjstraining") and is used to include the library on the page.`

1. Erstellen Sie unterhalb von `clientlib` die Ordner `css` und `js` (nt:folder).

1. Erstellen Sie unterhalb von `clientlib` die Dateien `css.txt` und `js.txt` (nt:files). Diese TXT-Dateien listen die Dateien auf, die in der Bibliothek enthalten sind.

1. Bearbeiten Sie die Datei `js.txt`: Sie muss mit „`#base=js`“ beginnen, worauf eine Liste der Dateien folgen muss, die vom CQ-Client-Bibliotheksdienst aggregiert werden sollen, z. B.:

   ```
   #base=js
    components.js
    exercises.js
    CustomWidget.js
    CustomBrowseField.js
    InsertTextPlugin.js
   ```

1. Bearbeiten Sie die Datei `css.txt`: Sie muss mit „`#base=css`“ beginnen, worauf eine Liste der Dateien folgen muss, die vom CQ-Client-Bibliotheksdienst aggregiert werden sollen, z. B.:

   ```
   #base=css
    components.css
   ```

1. Platzieren Sie die JavaScript-Dateien, die der Bibliothek angehören, unterhalb des Ordners `js`.

1. Platzieren Sie die Dateien `.css` und die von den CSS-Dateien verwendeten Ressourcen (z. B. `my_icon.png`) unterhalb des Ordners `css`.

>[!NOTE]
>
>Die oben beschriebene Handhabung von Stylesheets ist optional.

Fügen Sie die Client-Bibliothek wie folgt in die Seitenkomponenten-JSP ein:

* um sowohl JavaScript-Code als auch Stylesheets einzuschließen:
  `<ui:includeClientLib categories="<category-name1>, <category-name2>, ..."/>`
where `<category-nameX>` ist der Name der clientseitigen Bibliothek.

* um nur JavaScript-Code einzuschließen:
  `<ui:includeClientLib js="<category-name>"/>`

Weitere Informationen finden Sie in der Beschreibung des [&lt;ui:includeclientlib>](/help/sites-developing/taglib.md#lt-ui-includeclientlib) -Tag.

Manchmal sollte eine Client-Bibliothek nur im Authoring-Modus verfügbar sein und im Publishing-Modus ausgeschlossen werden. Dies lässt sich wie folgt erreichen:

```xml
    if (WCMMode.fromRequest(request) != WCMMode.DISABLED) {
        %><ui:includeClientLib categories="cq.collab.blog"/><%
    }
```

### Erste Schritte mit den Beispielen {#getting-started-with-the-samples}

Zum Durchführen der Übungen auf dieser Seite installieren Sie das Paket **Verwenden von ExtJS Widgets** auf einer lokalen AEM-Instanz und erstellen eine Beispielseite, in der die Komponenten enthalten sind. Gehen Sie dazu wie folgt vor:

1. Laden Sie in Ihrer AEM-Instanz das Paket **Verwenden von ExtJS Widgets (v01)** von Package Share herunter und installieren Sie es. Dabei wird im Repository unter `extjstraining` das Projekt `/apps` erstellt.
1. Fügen Sie die Client-Bibliothek, die die Skripte (js) und das Stylesheet (css) enthält, in das Head-Tag der Geometrixx-Seiten-JSP ein. Sie werden jetzt die Beispielkomponenten in eine neue Seite des **Geometrixx**-Zweiges einbinden:
Öffnen Sie in **CRXDE Lite** die Datei `/apps/geometrixx/components/page/headlibs.jsp` und fügen Sie die Kategorie `cq.extjstraining` wie folgt zum bestehenden `<ui:includeClientLib>`-Tag hinzu:
   `%><ui:includeClientLib categories="apps.geometrixx-main, cq.extjstraining"/><%`
1. Erstellen Sie eine Seite im **Geometrixx**-Zweig unter `/content/geometrixx/en/products` und nennen Sie sie **Verwenden von ExtJS Widgets**.
1. Wechseln Sie in den Designmodus und fügen Sie alle Komponenten der Gruppe **Verwenden von ExtJS Widgets** dem Design von Geometrixx hinzu.
1. Wechseln Sie zurück in den Bearbeitungsmodus: Die Komponenten der Gruppe **Verwenden von ExtJS Widgets** stehen im Sidekick zur Verfügung.

>[!NOTE]
>
>Die Beispiele auf dieser Seite basieren auf dem Geometrixx-Beispielinhalt, der nicht mehr im Lieferumfang von AEM enthalten ist, da er durch We.Retail ersetzt wurde. Wie Sie Geometrixx herunterladen und installieren können, erfahren Sie in der [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md#we-retail-geometrixx).

### Grundlegende Dialogfelder {#basic-dialogs}

Dialogfelder werden normalerweise zum Bearbeiten von Inhalten verwendet, können aber auch Informationen anzeigen. Eine einfache Möglichkeit, ein vollständiges Dialogfeld anzuzeigen, besteht darin, auf seine Darstellung im JSON-Format zuzugreifen. Verweisen Sie dazu Ihren Browser auf:

`https://localhost:4502/<path-to-dialog>.-1.json`

Die erste Komponente der **Verwenden von ExtJS-Widgets** -Gruppe in der Sidekick heißt **1. Dialoggrundlagen** und umfasst vier grundlegende Dialogfelder, die mit vordefinierten Widgets und ohne benutzerdefinierte JavaScript-Logik erstellt wurden. Die Dialogfelder werden unter `/apps/extjstraining/components/dialogbasics` gespeichert. Die grundlegenden Dialogfelder sind:

* das Dialogfeld „Full“ (Knoten `full`): Es zeigt ein Fenster mit drei Registerkarten an, wobei jede Registerkarte zwei Textfelder enthält.
* das Dialogfeld „Single Panel“ (Knoten `singlepanel`): Es zeigt ein Fenster mit einer Registerkarte mit zwei Textfeldern an.
* das Dialogfeld „Multi Panel“ (Knoten `multipanel`): Es zeigt dasselbe an wie das Dialogfeld „Full“, ist aber anders aufgebaut.
* das Dialogfeld „Design“ (Knoten `design`): Es zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte besitzt ein Textfeld, ein Dropdown-Menü und einen ausblendbaren Textbereich. Die zweite Registerkarte verfügt über einen Feldsatz mit vier Textfeldern und einen ausblendbaren Feldsatz mit zwei Textfeldern.

Fügen Sie die **1. Dialoggrundlagen** -Komponente in der Beispielseite:

1. Fügen Sie die **1. Dialoggrundlagen** -Komponente auf der Beispielseite aus der **Verwenden von ExtJS-Widgets** im **Sidekick**.
1. Die Komponente zeigt einen Titel, etwas Text und einen Link **EIGENSCHAFTEN** an. Wenn Sie den Link auswählen, werden die Eigenschaften des im Repository gespeicherten Absatzes angezeigt. Wählen Sie das Symbol erneut aus, um die Eigenschaften auszublenden.

Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-60](assets/chlimage_1-60.png)

#### Beispiel 1: Dialogfeld „Full“ {#example-full-dialog}

Das Dialogfeld **Full** zeigt ein Fenster mit drei Registerkarten, wobei jede Registerkarte zwei Textfelder enthält. Es ist das Standarddialogfeld der Komponente **Dialog Allgemein**. Die Eigenschaften sind:

* Wird von einem Knoten definiert: node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`.
* Zeigt drei Registerkarten (node type = `cq:Panel`).
* Jede Registerkarte weist zwei Textfelder auf (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wird durch den Knoten definiert:
  `/apps/extjstraining/components/dialogbasics/full`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/dialogbasics/full.-1.json`

Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at45411pm](assets/screen_shot_2012-01-31at45411pm.png)

#### Beispiel 2: Dialogfeld „Single Panel“ {#example-single-panel-dialog}

Das Dialogfeld **Single Panel** zeigt ein Fenster mit einer Registerkarte und zwei Textfeldern an. Die Eigenschaften sind:

* Zeigt eine Registerkarte (node type = `cq:Dialog`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`)
* Die Registerkarte weist zwei Textfelder auf (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`)
* Wird durch den Knoten definiert:
  `/apps/extjstraining/components/dialogbasics/singlepanel`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/dialogbasics/singlepanel.-1.json`
* Ein Vorteil gegenüber dem Dialogfeld **Full** besteht darin, dass weniger Konfiguration erforderlich ist.
* Empfohlene Verwendung: für einfache Dialogfelder, die Informationen anzeigen oder nur wenige Felder aufweisen.

So verwenden Sie das Dialogfeld „Single Panel“:

1. Ersetzen Sie das Dialogfeld der Komponente **Dialog Basics** durch das Dialogfeld **Single Panel**:
   1. Löschen Sie in **CRXDE Lite** den Knoten: `/apps/extjstraining/components/dialogbasics/dialog`
   1. Klicken Sie auf **Alle speichern**, um die Änderungen zu speichern.
   1. Kopieren Sie den Knoten: `/apps/extjstraining/components/dialogbasics/singlepanel`
   1. Fügen Sie den kopierten Knoten ein unter: `/apps/extjstraining/components/dialogbasics`
   1. Wählen Sie den Knoten `/apps/extjstraining/components/dialogbasics/Copy of singlepanel` aus und benennen Sie ihn um zu `dialog`.
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at45952pm](assets/screen_shot_2012-01-31at45952pm.png)

#### Beispiel 3: Dialogfeld „Multi-Panel“ {#example-multi-panel-dialog}

Das Dialogfeld **Multi-Panel** zeigt dasselbe wie das Dialogfeld **Full**, ist aber anders aufgebaut. Die Eigenschaften sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`).
* Zeigt drei Registerkarten (node type = `cq:Panel`).
* Jede Registerkarte weist zwei Textfelder auf (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wird durch den Knoten definiert:
  `/apps/extjstraining/components/dialogbasics/multipanel`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/dialogbasics/multipanel.-1.json`
* Ein Vorteil gegenüber dem Dialogfeld **Full** besteht in der vereinfachten Struktur.
* Empfohlene Verwendung: für Dialogfelder mit mehreren Registerkarten.

Das Dialogfeld „Multi-Panel“ verwenden Sie wie folgt:

1. Ersetzen Sie das Dialogfeld der Komponente **Dialog Allgemein** durch das Dialogfeld **Multi-Panel**: Führen Sie die in [Beispiel 2: Dialogfeld „Single Panel“](#example-single-panel-dialog) beschriebenen Schritte aus.
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at50119pm](assets/screen_shot_2012-01-31at50119pm.png)

#### Beispiel 4: Dialogfeld „Rich“ {#example-rich-dialog}

Das Dialogfeld **Rich** zeigt ein Fenster mit zwei Registerkarten an. Die erste Registerkarte besitzt ein Textfeld, ein Dropdown-Menü und einen ausblendbaren Textbereich. Die zweite Registerkarte verfügt über einen Feldsatz mit vier Textfeldern und einen ausblendbaren Feldsatz mit zwei Textfeldern. Die Eigenschaften sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Zeigt zwei Registerkarten (node type = `cq:Panel`).
* Die erste Registerkarte verfügt über ein ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)`-Widget mit einem ` [textfield](/help/sites-developing/xtypes.md#textfield)`- und einem ` [selection](/help/sites-developing/xtypes.md#selection)`-Widget mit drei Optionen sowie ein ausblendbares ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)` mit einem ` [textarea](/help/sites-developing/xtypes.md#textarea)`-Widget.
* Die zweite Registerkarte verfügt über ein ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)`-Widget mit vier ` [textfield](/help/sites-developing/xtypes.md#textfield)`-Widgets und ein ausblendbares `dialogfieldset` mit zwei ` [textfield](/help/sites-developing/xtypes.md#textfield)`-Widgets.
* Wird durch den Knoten definiert:
  `/apps/extjstraining/components/dialogbasics/rich`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/dialogbasics/rich.-1.json`

So verwenden Sie das Dialogfeld **Rich**:

1. Ersetzen Sie das Dialogfeld der Komponente **Dialog Allgemein** durch das Dialogfeld **Rich**: Führen Sie die in [Beispiel 2: Dialogfeld „Single Panel“](#example-single-panel-dialog) beschriebenen Schritte aus.
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-01-31at50429pm](assets/screen_shot_2012-01-31at50429pm.png) ![screen_shot_2012-01-31at50519pm](assets/screen_shot_2012-01-31at50519pm.png)

### Dynamische Dialogfelder {#dynamic-dialogs}

Die zweite Komponente der **Verwenden von ExtJS-Widgets** -Gruppe in der Sidekick heißt **2. Dynamische Dialogfelder** und umfasst drei dynamische Dialogfelder, die mit vordefinierten Widgets und **mit angepasster JavaScript-Logik**. Die Dialogfelder werden unter `/apps/extjstraining/components/dynamicdialogs` gespeichert. Die dynamischen Dialogfelder sind:

* das Dialogfeld „Registerkarten wechseln“ (Knoten `switchtabs`): Es zeigt ein Fenster mit zwei Registerkarten. Die erste Registerkarte verfügt über eine Optionsfeldauswahl mit drei Optionen: Wenn eine Option ausgewählt ist, wird eine Registerkarte angezeigt, die sich auf die Option bezieht. Die zweite Registerkarte enthält zwei Textfelder.
* das Dialogfeld „Beliebig“ (Knoten `arbitrary`): Es zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein Feld, in das Sie Assets ziehen oder hochladen können, und ein Feld, das Informationen über die Seite, die es umfasst, und das Asset (falls auf eines verwiesen wird) anzeigt.
* das Dialogfeld „Felder umschalten“ (Knoten `togglefield`): Es zeigt ein Fenster mit einer Registerkarte. Die Registerkarte verfügt über ein Kontrollkästchen: Ist es aktiviert, wird ein Feldsatz mit zwei Textfeldern angezeigt.

So schließen Sie die **2. Dynamische Dialogfelder** -Komponente auf der Beispielseite:

1. Fügen Sie die **2. Dynamische Dialogfelder** -Komponente auf der Beispielseite aus der **Verwenden von ExtJS-Widgets** im **Sidekick**.
1. Die Komponente zeigt einen Titel, etwas Text und einen Link **EIGENSCHAFTEN** an. Wenn Sie den Link auswählen, werden die Eigenschaften des im Repository gespeicherten Absatzes angezeigt. Wählen Sie das Symbol erneut aus, um die Eigenschaften auszublenden.

Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-61](assets/chlimage_1-61.png)

#### Beispiel 1: Dialogfeld „Registerkarten wechseln“ {#example-switch-tabs-dialog}

Das Dialogfeld **Registerkarten wechseln** zeigt ein Fenster mit zwei Registerkarten. Die erste Registerkarte verfügt über eine Optionsfeldauswahl mit drei Optionen: Wenn eine Option ausgewählt ist, wird eine Registerkarte angezeigt, die sich auf die Option bezieht. Die zweite Registerkarte enthält zwei Textfelder.

Die wichtigsten Merkmale sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Zeigt zwei Registerkarten an (node type = `cq:Panel`): eine Auswahlregisterkarte, die zweite Registerkarte hängt von der Auswahl der ersten Registerkarte ab (drei Optionen).
* Hat drei optionale Registerkarten (node type = `cq:Panel`), jede hat zwei Textfelder (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`). Es wird jeweils nur eine optionale Registerkarte angezeigt.
* Wird definiert durch den Knoten `switchtabs` unter:
  `/apps/extjstraining/components/dynamicdialogs/switchtabs`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/switchtabs.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* Der Dialogfeldknoten hat einen „`beforeshow`“-Listener, der alle optionalen Registerkarten ausblendet, bevor das Dialogfeld angezeigt wird:
  `beforeshow="function(dialog){Ejst.x2.manageTabs(dialog.items.get(0));}"`
  `dialog.items.get(0)` ruft `tabpanel` ab, welches das Auswahlfeld und die drei optionalen Bedienfelder enthält.
* Das Objekt `Ejst.x2` wird definiert in der Datei `exercises.js` unter:
  `/apps/extjstraining/clientlib/js/exercises.js`
* In der Methode `Ejst.x2.manageTabs()` werden alle optionalen Registerkarten ausgeblendet, weil der Wert von `index` „-1“ ist (i umfasst den Bereich von 1 bis 3).
* Die Auswahlregisterkarte weist zwei Listener auf: Einer zeigt die ausgewählte Registerkarte, wenn das ausgewählte Dialogfeld geladen wird (Ereignis „`loadcontent`“), und einer zeigt die ausgewählte Registerkarte, wenn die Auswahl geändert wird (Ereignis „`selectionchanged`“):
  `loadcontent="function(field,rec,path){Ejst.x2.showTab(field);}"`
  `selectionchanged="function(field,value){Ejst.x2.showTab(field);}"`
* Für die Methode `Ejst.x2.showTab()`,
  ruft `field.findParentByType('tabpanel')` `tabpanel` ab, welches alle Registerkarten enthält (`field` stellt das selection-Widget dar)
  `field.getValue()` ruft den Wert der Auswahl ab, z. B. „tab2“
  zeigt `Ejst.x2.manageTabs()` die ausgewählte Registerkarte an.
* Jede optionale Registerkarte verfügt über einen Listener, der die Registerkarte beim Ereignis „`render`“ ausblendet:
  `render="function(tab){Ejst.x2.hideTab(tab);}"`
* Für die Methode `Ejst.x2.hideTab()`,
  ist `tabPanel` das `tabpanel`, welches alle Registerkarten enthält
  ist `index` der Index der optionalen Registerkarte.
  blendet `tabPanel.hideTabStripItem(index)` die Registerkarte aus.

Dies wird wie folgt angezeigt:

![screen_shot_2012-02-01at114745am](assets/screen_shot_2012-02-01at114745am.png)

#### Beispiel 2: Dialogfeld „Arbitrary“ {#example-arbitrary-dialog}

Oft zeigt ein Dialogfeld Inhalte aus der zugrunde liegenden Komponente an. Das hier beschriebene Dialogfeld **Arbitrary** zeigt Inhalte aus einer anderen Komponente an.

Das Dialogfeld **Beliebig** zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte hat zwei Felder: eines zum Ablegen oder Hochladen eines Assets und eines, das einige Informationen über die enthaltende Seite und über das Asset anzeigt, falls ein solches referenziert wurde.

Die wichtigsten Merkmale sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Zeigt ein `tabpanel`-Widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) mit einem Bedienfeld (node type = `cq:Panel`) an
* Das Bedienfeld verfügt über ein smartfile-Widget (Knotentyp = `cq:Widget`, xtype = ` [smartfile](/help/sites-developing/xtypes.md#smartfile)`) und ein ownerdraw-Widget (Knotentyp = `cq:Widget`, xtype = ` [ownerdraw](/help/sites-developing/xtypes.md#ownerdraw)`)
* Wird definiert durch den Knoten `arbitrary` unter:
  `/apps/extjstraining/components/dynamicdialogs/arbitrary`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/arbitrary.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* Das `ownerdraw`-Widget hat einen „`loadcontent`“-Listener, der Informationen über die Seite anzeigt, die die Komponente enthält. Das heißt, das Asset, auf das das Smartfile-Widget verweist, wenn der Inhalt geladen wird:
  `loadcontent="function(field,rec,path){Ejst.x2.showInfo(field,rec,path);}"`
  `field` ist mit dem Objekt `ownerdraw` festgelegt
  `path` ist mit dem Inhaltspfad der Komponente festgelegt (zum Beispiel `/content/geometrixx/en/products/triangle/ui-tutorial/jcr:content/par/dynamicdialogs`)
* Das Objekt `Ejst.x2` wird definiert in der Datei `exercises.js` unter:
  `/apps/extjstraining/clientlib/js/exercises.js`
* Für die Methode `Ejst.x2.showInfo()`,
  ist `pagePath` der Pfad der Seite, die die Komponente enthält;
  stellt `pageInfo` die Seiteneigenschaften im JSON-Format dar;
  ist `reference` der Pfad des referenzierten Assets;
  stellt `metadata` die Metadaten des Assets im JSON-Format dar;
  zeigt `ownerdraw.getEl().update(html);` die erstellte HTML im Dialogfeld an.

So verwenden Sie das Dialogfeld **Arbitrary**:

1. Ersetzen Sie das Dialogfeld der Komponente **Dynamische Dialogfelder** durch das Dialogfeld **Beliebig**: Führen Sie die in [Beispiel 2: Dialogfeld „Single Panel“](#example-single-panel-dialog) beschriebenen Schritte aus.
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at115300am](assets/screen_shot_2012-02-01at115300am.png)

#### Beispiel 3: Dialogfeld „Felder umschalten“ {#example-toggle-fields-dialog}

Das Dialogfeld **Felder umschalten** zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein Kontrollkästchen: Ist es aktiviert, wird ein Feldsatz mit zwei Textfeldern angezeigt.

Die wichtigsten Merkmale sind:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Zeigt ein `tabpanel`-Widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#textpanel)`) mit einem Bedienfeld (node type = `cq:Panel`) an.
* Das Bedienfeld verfügt über ein selection-/checkbox-Widget (node type = `cq:Widget`, xtype = ` [selection](/help/sites-developing/xtypes.md#selection)`, type = ` [checkbox](/help/sites-developing/xtypes.md#checkbox)`) und ein zusammenklappbares dialogfieldset-Widget (node type = `cq:Widget`, xtype = ` [dialogfieldset](/help/sites-developing/xtypes.md#dialogfieldset)`), das standardmäßig ausgeblendet ist, sowie zwei Textfeld-Widgets (node type = `cq:Widget`, xtype = ` [textfield](/help/sites-developing/xtypes.md#textfield)`).
* Wird definiert durch den Knoten `togglefields` unter:
  `/apps/extjstraining/components/dynamicdialogs/togglefields`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/dynamicdialogs/togglefields.-1.json`

Die Logik wird wie folgt durch Ereignis-Listener und JavaScript-Code implementiert:

* die Registerkarte „Auswahl“ hat zwei Listener: einen, der das dialogfieldset anzeigt, wenn der Inhalt geladen wird (Ereignis „`loadcontent`“) und einen, der das dialogfieldset anzeigt, wenn die Auswahl geändert wird (Ereignis „`selectionchanged`“):
  `loadcontent="function(field,rec,path){Ejst.x2.toggleFieldSet(field);}"`
  `selectionchanged="function(field,value){Ejst.x2.toggleFieldSet(field);}"`
* Das Objekt `Ejst.x2` wird definiert in der Datei `exercises.js` unter:
  `/apps/extjstraining/clientlib/js/exercises.js`
* Für die Methode `Ejst.x2.toggleFieldSet()`,
  ist `box` das Auswahlobjekt;
  ist `panel` das Bedienfeld, das das selection- und das dialogfieldset-Widget enthält;
  ist `fieldSet` das dialogfieldset-Objekt;
  ist `show` der Wert der Auswahl (true oder false)
basierend auf „`show`“ wird das dialogfieldset angezeigt oder nicht

Um das Dialogfeld **Felder umschalten** zu verwenden, gehen Sie wie folgt vor:

1. Ersetzen Sie das Dialogfeld der Komponente **Dynamische Dialogfelder** durch das Dialogfeld **Felder umschalten**: Führen Sie die in [Beispiel 2: Dialogfeld „Single Panel“](#example-single-panel-dialog) beschriebenen Schritte aus.
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at115518am](assets/screen_shot_2012-02-01at115518am.png)

### Benutzerdefinierte Widgets {#custom-widgets}

Die im Lieferumfang von AEM enthaltenen vordefinierten Widgets sollten die meisten Anwendungsfälle abdecken. Trotzdem kann es passieren, dass ein benutzerdefiniertes Widget erstellt werden muss, um eine projektspezifische Anforderung zu erfüllen. Benutzerdefinierte Widgets können durch Erweiterung vorhandener Widgets erstellt werden. Um Ihnen den Einstieg in eine solche Anpassung zu erleichtern, enthält das Paket **`Using ExtJS Widgets`** drei Dialogfelder, die drei verschiedene benutzerdefinierte Widgets verwenden:

* Das Dialogfeld „Multi Field“ (Knoten `multifield`) zeigt ein Fenster mit einer Registerkarte. Die Registerkarte verfügt über ein benutzerdefiniertes multifield-Widget mit zwei Feldern: Ein Dropdown-Menü mit zwei Optionen und ein Textfeld. Da es auf dem im Lieferumfang enthaltenen `multifield`-Widget (mit nur einem Textfeld) basiert, verfügt es über alle Funktionen des `multifield`-Widgets.
* Das Dialogfeld „Tree Browse“ (`treebrowse`-Knoten) zeigt ein Fenster mit einer Registerkarte, die ein Pfadbrowser-Widget enthält: Wenn Sie auf den Pfeil klicken, wird ein Fenster geöffnet, in dem Sie eine Hierarchie durchsuchen und ein Element auswählen können. Der Pfad des Elements wird dann dem Pfadfeld hinzugefügt und wird beibehalten, wenn das Dialogfeld geschlossen wird.
* Ein Dialogfeld, das auf dem Rich-Text-Editor-Plug-in basiert (Knoten `rteplugin`) und dem Rich-Text-Editor eine benutzerdefinierte Schaltfläche hinzufügt, mit der benutzerdefinierter Text in den Haupttext eingefügt werden kann. Es besteht aus einem `richtext`-Widget (RTE) und einer benutzerdefinierten Funktion, die durch den RTE-Plug-in-Mechanismus hinzugefügt wird.

Die benutzerdefinierten Widgets und das Plug-in sind in der Komponente namens **3. Benutzerdefinierte Widgets** des **Verwenden von ExtJS-Widgets** Paket. Um diese Komponente in die Beispielseite aufzunehmen:

1. Fügen Sie die **3. Benutzerdefinierte Widgets** -Komponente auf der Beispielseite aus der **Verwenden von ExtJS-Widgets** im **Sidekick**.
1. Die Komponente zeigt einen Titel, etwas Text und, wenn Sie auf den Link **EIGENSCHAFTEN** klicken, die Eigenschaften des im Repository gespeicherten Absatzes an. Durch erneutes Klicken werden die Eigenschaften verborgen.
Die Komponente wird wie im Folgenden dargestellt:

![chlimage_1-62](assets/chlimage_1-62.png)

#### Beispiel 1: Benutzerdefiniertes Multifield-Widget {#example-custom-multifield-widget}

Das Widget-basierte Dialogfeld **Benutzerdefiniertes Multifield** zeigt ein Fenster mit einer Registerkarte an. Die Registerkarte verfügt über ein benutzerdefiniertes multifield-Widget, das im Gegensatz zum Standard-Widget, das ein Feld hat, zwei Felder enthält: ein Dropdown-Menü mit zwei Optionen und ein Textfeld.

Das Widget-basierte Dialogfeld **Benutzerdefiniertes Multifield**:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Zeigt ein `tabpanel`-Widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) an, das ein Bedienfeld (node type = `cq:Widget`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`) enthält.
* Das Bedienfeld weist ein `multifield`-Widget (node type = `cq:Widget`, xtype = ` [multifield](/help/sites-developing/xtypes.md#multifield)`) auf.
* Das `multifield`-Widget verfügt über eine fieldconfig (Knotentyp = `nt:unstructured`, xtype = `ejstcustom`, optionsProvider = `Ejst.x3.provideOptions`), die auf dem benutzerdefinierten xtype „`ejstcustom`“ basiert:
   * „`fieldconfig`“ ist eine Konfigurationsoption des ` [CQ.form.MultiField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.MultiField)`-Objekts.
   * „`optionsProvider`“ ist eine Konfiguration des `ejstcustom`-Widgets. Sie wird mit der `Ejst.x3.provideOptions`-Methode festgelegt, die definiert ist in `exercises.js` unter:
     `/apps/extjstraining/clientlib/js/exercises.js`
und gibt zwei Optionen zurück.
* Wird definiert durch den Knoten `multifield` unter:
  `/apps/extjstraining/components/customwidgets/multifield`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/customwidgets/multifield.-1.json`

Das benutzerdefinierte `multifield`-Widget (xtype = `ejstcustom`):

* Ist ein JavaScript-Objekt namens `Ejst.CustomWidget`
* Wird definiert in der JavaScript-Datei `CustomWidget.js` unter:
  `/apps/extjstraining/clientlib/js/CustomWidget.js`
* Erweitert das Widget ` [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.CompositeField)`.
* Hat drei Felder: `hiddenField` (Textfeld), `allowField` (ComboBox), und `otherField` (Textfeld)
* Überschreibt `CQ.Ext.Component#initComponent`, um die drei Felder hinzuzufügen:
   * `allowField` ist ein [CQ.form.Selection](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.Selection)-Objekt vom Typ „select“. „optionsProvider“ ist eine Konfiguration des Auswahl-Objekts, das mit der optionsProvider-Konfiguration des im Dialogfeld definierten CustomWidget instanziert wird.
   * `otherField` ist ein [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextField)-Objekt.
* Überschreibt die Methoden `setValue`, `getValue` und `getRawValue` von [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.CompositeField) zum Setzen und Abrufen des Wertes von CustomWidget mit dem Format:
  `<allowField value>/<otherField value>, for example: 'Bla1/hello'`.
* Registriert sich selbst als xtype „`ejstcustom`“:
  `CQ.Ext.reg('ejstcustom', Ejst.CustomWidget);`

Das Widget-basierte Dialogfeld **Benutzerdefiniertes Multifield** wird wie folgt angezeigt:

![screen_shot_2012-02-01at115840am](assets/screen_shot_2012-02-01at115840am.png)

#### Beispiel 2: Benutzerdefiniertes `Treebrowse`-Widget {#example-custom-treebrowse-widget}

Das benutzerdefinierte und Widget-basierte Dialogfeld **`Treebrowse`** zeigt ein Fenster mit einer Registerkarte, die ein benutzerdefiniertes Pfad-Browser-Widget enthält. Wenn Sie den Pfeil auswählen, öffnet sich ein Fenster, in dem Sie eine Hierarchie durchsuchen und ein Element auswählen können. Der Pfad des Elements wird dann dem Pfadfeld hinzugefügt und wird beibehalten, wenn das Dialogfeld geschlossen wird.

Das benutzerdefinierte Dialogfeld `treebrowse`:

* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [dialog](/help/sites-developing/xtypes.md#dialog)`).
* Zeigt ein `tabpanel`-Widget (node type = `cq:Widget`, xtype = ` [tabpanel](/help/sites-developing/xtypes.md#tabpanel)`) an, das ein Bedienfeld (node type = `cq:Widget`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`) enthält.
* Das Bedienfeld weist ein benutzerdefiniertes Widget (node type = `cq:Widget`, xtype = `ejstbrowse`) auf.
* Wird definiert durch den Knoten `treebrowse` unter:
  `/apps/extjstraining/components/customwidgets/treebrowse`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/customwidgets/treebrowse.-1.json`

Das benutzerdefinierte treebrowse-Widgets (xtype = `ejstbrowse`):

* Ist ein JavaScript-Objekt namens `Ejst.CustomWidget`
* Wird definiert in der JavaScript-Datei `CustomBrowseField.js` unter:
  `/apps/extjstraining/clientlib/js/CustomBrowseField.js`
* Erweitert ` [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TriggerField)`.
* Definiert ein Fenster zum Durchsuchen namens `browseWindow`.
* Überschreibt ` [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TriggerField)#onTriggerClick`, um das Fenster zum Durchsuchen anzuzeigen, wenn auf den Pfeil geklickt wird.
* Definiert ein [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)-Objekt:
   * Es ruft Daten ab, indem es das Servlet aufruft, das unter `/bin/wcm/siteadmin/tree.json` registriert ist.
   * Sein Stamm ist „`apps/extjstraining`“.
* Definiert ein `window`-Objekt ( ` [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window)`):
   * Basierend auf dem vordefinierten Bedienfeld.
   * Weist eine **OK**-Schaltfläche auf, die den Wert des ausgewählten Pfads festlegt und das Bedienfeld ausblendet.
* Das Fenster wird unterhalb des Feldes **Pfad** verankert.
* Der ausgewählte Pfad wird bei einem `show`-Ereignis vom Durchsuchfeld an das Fenster weitergegeben.
* Registriert sich selbst als xtype „`ejstbrowse`“:
  `CQ.Ext.reg('ejstbrowse', Ejst.CustomBrowseField);`

Um das Widget-basierte Dialogfeld **Benutzerdefiniertes Treebrowse** zu verwenden:

1. Ersetzen Sie das Dialogfeld der Komponente **Benutzerdefinierte Widgets** durch das Dialogfeld **Benutzerdefiniertes Durchsuchen der Baumstruktur**: Führen Sie die in [Beispiel 2: Dialogfeld „Single Panel“](#example-single-panel-dialog) beschriebenen Schritte aus.
1. Bearbeiten Sie die Komponente: Das Dialogfeld wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at120104pm](assets/screen_shot_2012-02-01at120104pm.png)

#### Beispiel 3: Rich-Text-Editor(RTE)-Plug-in {#example-rich-text-editor-rte-plug-in}

Das **Rich-Text-Editor(RTE)-Plug-in** basierte Dialogfeld ist ein auf dem Rich-Text-Editor basierendes Dialogfeld, das eine benutzerdefinierte Schaltfläche zum Einfügen eines benutzerdefinierten Textes in eckigen Klammern enthält. Der benutzerdefinierte Text kann durch eine serverseitige Logik analysiert werden (in diesem Beispiel nicht implementiert), z. B. um Text hinzuzufügen, der am angegebenen Pfad definiert ist:

Das auf dem **RTE-Plug-in** basierende Dialogfeld:

* Wird definiert durch den Knoten „rteplugin“ unter:
  `/apps/extjstraining/components/customwidgets/rteplugin`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/customwidgets/rteplugin.-1.json`
* Der Knoten `rtePlugins` verfügt über einen untergeordneten Knoten `inserttext` (node type = `nt:unstructured`) der nach dem Plug-in benannt ist. Er weist eine Eigenschaft mit der Bezeichnung `features` auf, die definiert, welche der Plug-in-Funktionen für den RTE verfügbar sind.

Das RTE-Plug-in:

* Ist ein JavaScript-Objekt namens `Ejst.InsertTextPlugin`
* Wird definiert in der JavaScript-Datei `InsertTextPlugin.js` unter:
  `/apps/extjstraining/clientlib/js/InsertTextPlugin.js`
* Erweitert das ` [CQ.form.rte.plugins.Plugin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)`-Objekt.
* Die folgenden Methoden definieren das ` [CQ.form.rte.plugins.Plugin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin)`-Objekt und werden im implementierenden Plug-in überschrieben:
   * `getFeatures()` gibt ein Array aller Funktionen zurück, die vom Plug-in bereitgestellt werden.
   * `initializeUI()` fügt die neue Schaltfläche der RTE-Symbolleiste hinzu.
   * `notifyPluginConfig()` zeigt Titel und Text an, wenn auf die Schaltfläche gezeigt wird.
   * `execute()` wird aufgerufen, wenn auf die Schaltfläche geklickt wird, und führt die Plug-in-Aktion durch: Sie zeigt ein Fenster an, in dem Text definiert wird, der eingeschlossen werden soll.
* `insertText()` fügt einen Text anhand des entsprechenden Dialogfeldobjekts `Ejst.InsertTextPlugin.Dialog` ein (siehe unten).
* `executeInsertText()` wird von der Methode `apply()` des Dialogfelds aufgerufen, die ausgelöst wird, wenn auf die Schaltfläche **OK** geklickt wird.
* Registriert sich selbst als „`inserttext`“-Plug-in:
  `CQ.form.rte.plugins.PluginRegistry.register("inserttext", Ejst.InsertTextPlugin);`
* Das `Ejst.InsertTextPlugin.Dialog`-Objekt definiert das Dialogfeld, das geöffnet wird, wenn auf die Plug-in-Schaltfläche geklickt wird. Das Dialogfeld besteht aus einem Bedienfeld, einem Formular, einem Textfeld und zwei Schaltflächen (**OK** und **Abbrechen**).

So verwenden Sie das auf dem **Rich-Text-Editor (RTE)-Plug-in** basierende Dialogfeld:

1. Ersetzen Sie das Dialogfeld der Komponente **Benutzerdefinierte Widgets** durch das auf dem **Rich-Text-Editor (RTE)-Plug-in** basierende Dialogfeld: Führen Sie die in [Beispiel 2: Dialogfeld „Single Panel“](#example-single-panel-dialog) beschriebenen Schritte aus.
1. Bearbeiten Sie die Komponente.
1. Klicken Sie auf das letzte Symbol auf der rechten Seite (das mit den vier Pfeilen). Geben Sie einen Pfad ein und klicken Sie auf **OK**:
Der Pfad wird in eckigen Klammern ([ ]) angezeigt.
1. Klicken Sie auf **OK**, sodass sich der Rich-Text-Editor schließt.

Das **Rich-Text-Editor(RTE)-Plug-in**-basierte Dialogfeld wird wie folgt angezeigt:

![screen_shot_2012-02-01at120254pm](assets/screen_shot_2012-02-01at120254pm.png)

>[!NOTE]
>
>Dieses Beispiel zeigt nur die Implementierung des Client-seitigen Teils der Logik: Die Platzhalter (*[Text]*) müssen dann explizit Server-seitig geparst werden (z. B. in der Komponenten-JSP).

### Tree Overview {#tree-overview}

Das im Lieferumfang enthaltene ` [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)`-Objekt bietet eine baumstrukturierte Benutzeroberflächendarstellung baumstrukturierter Daten. Die im Paket **Verwenden von ExtJS Widgets** enthaltene Komponente „Übersicht über die Baumstruktur“ zeigt die Verwendung des Objekts `TreePanel` zur Anzeige einer JCR-Baumstruktur unterhalb eines gegebenen Pfads. Das Fenster selbst kann an- bzw. abgedockt werden. In diesem Beispiel wird die Fensterlogik in die Komponenten-JSP zwischen &lt;script>&lt;/script>-Tags eingebunden.

Fügen Sie die Komponente **Tree Overview** wie folgt der Beispielseite hinzu:

1. Fügen Sie die **4. Baumübersicht** -Komponente auf der Beispielseite aus der **Verwenden von ExtJS-Widgets** im **Sidekick**.
1. Die Komponente zeigt:
   * einen Titel und etwas Text
   * einen Link **EIGENSCHAFTEN**: klicken Sie darauf, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.
   * ein schwebendes Fenster mit einer Baumstruktur-Darstellung des Repositorys, das erweitert werden kann.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at120639pm](assets/screen_shot_2012-02-01at120639pm.png)

Die Komponente „Tree Overview“:

* Wird definiert unter:
  `/apps/extjstraining/components/treeoverview`

* Im Dialogfeld können Sie die Größe des Fensters festlegen und das Fenster andocken oder abdocken (siehe Details unten).

Die Komponenten-JSP:

* Ruft die Eigenschaften „width“, „height“ und „docked“ aus dem Repository ab.
* Zeigt Text zum Datenformat der Baumübersicht an.
* Bettet die Fensterlogik zwischen JavaScript-Tags in die Komponenten-JSP ein.
* Wird definiert unter:
  `apps/extjstraining/components/treeoverview/content.jsp`

Der in die Komponenten-JSP eingebettete JavaScript-Code:

* Definiert ein `tree`-Objekt, indem versucht wird, ein Baumstrukturfenster von der Seite abzurufen.
* Wenn das Fenster, das die Baumstruktur anzeigt, nicht vorhanden ist, wird `treePanel` ([CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.tree.TreePanel)) erstellt:
   * `treePanel` enthält die Daten, anhand derer das Fenster erstellt wird.
   * Die Daten werden durch den Aufruf des Servlets abgerufen, das registriert ist unter:
     `/bin/wcm/siteadmin/tree.json`
* Der `beforeload`-Listener stellt sicher, dass der gewählte Knoten geladen wird.
* Das `root`-Objekt legt den Pfad `apps/extjstraining` als Stamm der Baumstruktur fest.
* `tree` (` [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window)`) wird anhand des vordefinierten `treePanel` festgelegt und angezeigt mit:
  `tree.show();`
* Wenn das Fenster vorhanden ist, wird es anhand der aus dem Repository abgerufenen Breite, Höhe und Andockungseigenschaften angezeigt.

Das Komponentendialogfeld:

* Zeigt eine Registerkarte mit zwei Feldern zum Festlegen der Größe (Breite und Höhe) des Fensters der Baumstrukturübersicht und ein Feld zum An-/Abdocken des Fensters.
* Wird von einem Knoten definiert (node type = `cq:Dialog`, xtype = ` [panel](/help/sites-developing/xtypes.md#panel)`).
* Das Bedienfeld verfügt über ein sizefield-Widget (node type = `cq:Widget`, xtype = ` [sizefield](/help/sites-developing/xtypes.md#sizefield)`) und ein selection-Widget (node type = `cq:Widget`, xtype = ` [selection](/help/sites-developing/xtypes.md#selection)`, type = `radio`) mit zwei Optionen (true/false)
* Wird definiert durch den dialog-Knoten unter:
  `/apps/extjstraining/components/treeoverview/dialog`
* Wird im JSON-Format gerendert, indem Folgendes angefragt wird:
  `https://localhost:4502/apps/extjstraining/components/treeoverview/dialog.-1.json`
* Wird wie folgt angezeigt:

![screen_shot_2012-02-01at120745pm](assets/screen_shot_2012-02-01at120745pm.png)

### Rasterübersicht {#grid-overview}

Ein Rasterbedienfeld stellt Daten in tabellarischer Form von Zeilen und Spalten dar. Es umfasst Folgendes:

* Store: das Modell, das die Datendatensätze enthält (Zeilen)
* Spaltenmodell: das Spaltendesign
* Ansicht: fasst die Benutzeroberfläche zusammen
* Auswahlmodell: das Auswahlverhalten

Die im Paket **Verwenden von ExtJS Widgets** enthaltene Komponente „Raster-Übersicht“ zeigt, wie Daten in einem tabellarischen Format angezeigt werden:

* Das Beispiel 1 verwendet statische Daten.
* Das Beispiel 2 verwendet aus dem Repository abgerufene Daten.

Fügen Sie die Komponente „Raster-Übersicht“ wie folgt der Beispielseite hinzu:

1. Fügen Sie die **5. Rasterübersicht** -Komponente auf der Beispielseite aus der **Verwenden von ExtJS-Widgets** im **Sidekick**.
1. Die Komponente zeigt:
   * einen Titel und etwas Text.
   * einen Link **EIGENSCHAFTEN**: klicken Sie darauf, um die Eigenschaften des im Repository gespeicherten Absatzes anzuzeigen. Klicken Sie erneut, um die Eigenschaften zu verbergen.
   * ein schwebendes Fenster mit Daten im Tabellenformat.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at121109pm](assets/screen_shot_2012-02-01at121109pm.png)

#### Beispiel 1: Standardraster {#example-default-grid}

In der vordefinierten Version der Komponente **Rasterübersicht** wird ein Fenster mit statischen Daten im Tabellenformat angezeigt. In diesem Beispiel wird die Logik auf zwei Arten in die Komponenten-JSP eingebettet:

* Die generische Logik wird zwischen &lt;script>&lt;/script>-Tags definiert
* Die spezifische Logik steht in einer separaten .js-Datei zur Verfügung und ist in der JSP verlinkt. Diese Einrichtung ermöglicht es, einfach zwischen den beiden Logiken (statisch/dynamisch) umzuschalten, indem die gewünschten &lt;script>-Tags kommentiert werden.

Die Komponente „Grid Overview“:

* Wird definiert unter:
  `/apps/extjstraining/components/gridoverview`
* Im Dialogfeld können Sie die Größe des Fensters festlegen und das Fenster andocken oder abdocken.

Die Komponenten-JSP:

* Ruft die Eigenschaften „width“, „height“ und „docked“ aus dem Repository ab.
* Zeigt etwas Text als Einführung zum Datenformat des Rasterüberblicks an.
* Verweist auf JavaScript-Code, der das GridPanel-Objekt definiert:
  `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script>`
  `defaultgrid.js` definiert einige statische Daten als Grundlage für das GridPanel-Objekt.
* Bettet zwischen JavaScript-Tags JavaScript-Code ein, der das Window-Objekt definiert, das das GridPanel-Objekt verwendet.
* Wird definiert unter:
  `apps/extjstraining/components/gridoverview/content.jsp`

Der in die Komponenten-JSP eingebettete JavaScript-Code:

* Definiert das `grid`-Objekt, indem versucht wird, die Fensterkomponente von folgender Seite abzurufen:
  `var grid = CQ.Ext.getCmp("<%= node.getName() %>-grid");`
* Wenn `grid` nicht vorhanden ist, wird ein [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)-Objekt (`gridPanel`) definiert, indem die Methode `getGridPanel()` aufgerufen wird (siehe unten). Diese Methode wird in `defaultgrid.js` definiert.
* `grid` ist ein ` [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.Window)`-Objekt, das auf dem vordefinierten GridPanel basiert, und wird angezeigt als: `grid.show();`
* Ist `grid` vorhanden, wird es anhand der aus dem Repository abgerufenen Breite, Höhe und Andockungseigenschaften angezeigt.

Die JavaScript-Datei (`defaultgrid.js`), auf die in der Komponenten-JSP verwiesen wird, definiert die `getGridPanel()`-Methode, die von dem Skript aufgerufen wird, das in der JSP eingebettet ist, und gibt ein ` [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)`-Objekt zurück, das auf statischen Daten basiert. Die Logik lautet wie folgt:

* `myData` ist ein Array statischer Daten, formatiert als Tabelle mit fünf Spalten und vier Zeilen.
* `store` ist ein `CQ.Ext.data.Store`-Objekt, das `myData` verbraucht.
* `store` wird in den Speicher geladen:
  `store.load();`
* `gridPanel` ist ein ` [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)`, das `store` verbraucht:
   * Die Spaltenbreiten werden ständig proportional angepasst:
     `forceFit: true`
   * Nur eine Zeile kann jeweils ausgewählt werden:
     `singleSelect:true`

#### Beispiel 2: Verweissuchraster {#example-reference-search-grid}

Bei der Installation des Pakets zeigt die Datei `content.jsp` der Komponente **Raster-Übersicht** ein Raster an, das auf statischen Daten basiert. Es ist möglich, die Komponente zu ändern, um ein Raster mit den folgenden Eigenschaften anzuzeigen:

* Hat drei Spalten.
* Basiert auf Daten, die vom Repository durch Aufruf eines Servlets abgerufen werden.
* Die Zellen der letzten Spalte können bearbeitet werden. Der Wert wird in einer `test`-Eigenschaft unterhalb des Knotens gespeichert, der anhand des in der ersten Spalte angezeigten Pfades definiert wird.

Wie bereits weiter oben beschrieben ruft das Fensterobjekt sein ` [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)`-Objekt ab, indem die unter `/apps/extjstraining/components/gridoverview/defaultgrid.js` in der Datei `defaultgrid.js` definierte Methode `getGridPanel()` aufgerufen wird. Die Komponente **Raster-Übersicht** bietet eine andere Implementierung für die `getGridPanel()`-Methode, definiert in der Datei `referencesearch.js` unter `/apps/extjstraining/components/gridoverview/referencesearch.js`. Durch Wechseln der .js-Datei, auf die in der Komponenten-JSP verwiesen wird, basiert das Raster auf aus dem Repository abgerufenen Daten.

Wechseln Sie die JS-Datei, auf die in der Komponenten-JSP verwiesen wird:

1. Kommentieren Sie in **CRXDE Lite** in der Datei `content.jsp` der Komponente die Zeile, die die Datei `defaultgrid.js` enthält, sodass sie wie folgt aussieht:
   `<!-- script type="text/javascript" src="/apps/extjstraining/components/gridoverview/defaultgrid.js"></script-->`
1. Entfernen Sie den Kommentar aus der Zeile, die die Datei `referencesearch.js` enthält, sodass sie wie folgt aussieht:
   `<script type="text/javascript" src="/apps/extjstraining/components/gridoverview/referencesearch.js"></script>`
1. Speichern Sie die Änderungen.
1. Aktualisieren Sie die Beispielseite.

Die Komponente wird wie im Folgenden dargestellt:

![screen_shot_2012-02-01at121429pm](assets/screen_shot_2012-02-01at121429pm.png)

Der JavaScript-Code, auf den in der Komponenten-JSP verwiesen wird (`referencesearch.js`), definiert die `getGridPanel()`-Methode, die von der Komponenten-JSP aufgerufen wird und ein ` [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.GridPanel)`-Objekt zurückgibt, das auf Daten basiert, welche dynamisch aus dem Repository abgerufen werden. Die Logik in `referencesearch.js` definiert dynamische Daten als Basis für das GridPanel:

* `reader` ist ein ` [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.JsonReader)`-Objekt, das die Antwort des Servlets im JSON-Format für drei Spalten liest.
* `cm` ist ein ` [CQ.Ext.grid.ColumnModel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.ColumnModel)`-Objekt für drei Spalten.
Die „Test“-Spaltenzellen können bearbeitet werden, da sie mit einem Editor definiert werden:
  `editor: new [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.form.TextField)({})`
* die Spalten sind sortierbar:
  `cm.defaultSortable = true;`
* `store` ist ` [CQ.Ext.data.GroupingStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.data.GroupingStore)`-Objekt:
   * Es ruft seine Daten ab, indem es das unter „`/bin/querybuilder.json`“ registrierte Servlet mit einigen Parametern zum Filtern der Abfrage aufruft.
   * Es basiert auf dem vorher definierten `reader`.
   * Die Tabelle wird anhand der Spalte „**jcr:path**“ in aufsteigender Reihenfolge definiert.
* `gridPanel` ist ein ` [CQ.Ext.grid.EditorGridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.EditorGridPanel)`-Objekt, das bearbeitet werden kann:
   * Es basiert auf dem vordefinierten `store` und auf dem Spaltenmodell `cm`.
   * Nur eine Zeile kann jeweils ausgewählt werden:
     `sm: new [CQ.Ext.grid.RowSelectionModel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.Ext.grid.RowSelectionModel)({singleSelect:true})`
   * Der `afteredit`-Listener stellt sicher, dass nach der Bearbeitung einer Zelle in der „**Test**“-Spalte Folgendes passiert:
      * Die Eigenschaft „`test`“ des Knotens an dem durch die Spalte „**jcr:path**“ definierten Pfad wird im Repository mit dem Wert der Zelle festgelegt.
      * Wenn der POST erfolgreich ist, wird der Wert dem `store`-Objekt hinzugefügt, andernfalls wird er abgelehnt.
