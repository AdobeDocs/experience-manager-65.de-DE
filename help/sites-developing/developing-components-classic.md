---
title: Entwickeln von AEM-Komponenten (klassische Benutzeroberfläche)
seo-title: Entwickeln von AEM-Komponenten (klassische Benutzeroberfläche)
description: Die klassische Benutzeroberfläche nutzt ExtJS, um Widgets zu erstellen, die das Erscheinungsbild der Komponenten angeben. HTL ist nicht die empfohlene Skriptsprache für AEM.
seo-description: Die klassische Benutzeroberfläche nutzt ExtJS, um Widgets zu erstellen, die das Erscheinungsbild der Komponenten angeben. HTL ist nicht die empfohlene Skriptsprache für AEM.
uuid: ed53d7c6-5996-4892-81a4-4ac30df85f04
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: c68f724f-f9b3-4018-8d3a-1680c53d73f8
legacypath: /content/docs/en/aem/6-2/develop/components/components-classic
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# Entwickeln von AEM-Komponenten (klassische Benutzeroberfläche){#developing-aem-components-classic-ui}

Die klassische Benutzeroberfläche nutzt ExtJS, um Widgets zu erstellen, die das Erscheinungsbild der Komponenten angeben. Aufgrund der Struktur dieses Widgets gibt es einige Unterschiede zwischen der Interaktion von Komponenten mit der klassischen Benutzeroberfläche und mit der [Touch-optimierten Benutzeroberfläche](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Many aspects of component development are common to both the classic UI and the touch-enabled UI, so **you must read[AEM Components - The Basics](/help/sites-developing/components-basics.md)before** using this page, which deals with the specifics of the classic UI.

>[!NOTE]
>
>Auch wenn die HTML Template Language (HTL) und JSP beide für die Entwicklung von Komponenten für die klassische Benutzeroberfläche verwendet werden können, ist auf dieser Seite nur die Entwicklung mit JSP abgebildet. Dies liegt einzig an der Historie der Verwendung von JSP für die klassische Benutzeroberfläche.
>
>HTL ist jetzt die empfohlene Skriptsprache für AEM. See [HTL](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) and [Developing AEM Components](/help/sites-developing/developing-components.md) to compare methods.

## Struktur {#structure}

The basic structure of a component is covered on the page [AEM Components - The Basics](/help/sites-developing/components-basics.md#structure), which applies both the touch-eanbeld and classic UIs. Auch wenn Sie die Einstellungen für die Touch-optimierte Benutzeroberfläche in Ihrer neuen Komponente nicht verwenden müssen, ist es möglicherweise hilfreich, diese beim Vererben aus vorhandenen Komponenten zu beachten.

## JSP-Skripte {#jsp-scripts}

JSP-Skripte oder -Servlets können verwendet werden, um Komponenten zu rendern. Gemäß den Anforderungsverarbeitungsregeln von Sling lautet der Name für das Standardskript:

`<*componentname*>.jsp`

## global.jsp {#global-jsp}

Die JSP-Skriptdatei `global.jsp` wird verwendet, um allen JSP-Skriptdateien, die zum Rendern einer Komponente verwendet werden, schnellen Zugriff auf bestimmte Objekte (d. h. Zugriff auf Inhalte) bereitzustellen.

Daher muss `global.jsp` in jedem JSP-Skript enthalten sein, das Komponenten rendert, bei dem mindestens ein in `global.jsp` bereitgestelltes Objekt verwendet wird.

Der Speicherort der standardmäßigen `global.jsp` ist:

`/libs/foundation/global.jsp`

>[!NOTE]
>
>The path `/libs/wcm/global.jsp`, which was used by the versions CQ 5.3 and earlier, is now obsolete.

### Funktion von global.jsp, verwendeten APIs und Taglibs {#function-of-global-jsp-used-apis-and-taglibs}

Im Folgenden sind die wichtigsten Objekte aufgelistet, die die standardmäßige `global.jsp` bereitstellt:

Zusammenfassung:

* `<cq:defineObjects />`

   * `slingRequest` - Das umschlossene Anforderungsobjekt ( `SlingHttpServletRequest`).
   * `slingResponse` - Das umschlossene Antwortobjekt ( `SlingHttpServletResponse`).
   * `resource` - Das Sling-Ressourcenobjekt ( `slingRequest.getResource();`).
   * `resourceResolver` - Das Sling Resource Resolver-Objekt ( `slingRequest.getResoucreResolver();`).
   * `currentNode` – der aufgelöste JCR-Knoten für die Anforderung.
   * `log` - Die Standard-Protokollfunktion ().
   * `sling` - Der Sling-Skript-Helfer.
   * `properties` - Die Eigenschaften der adressierten Ressource ( `resource.adaptTo(ValueMap.class);`).
   * `pageProperties` – die Eigenschaften der Seite der betreffenden Ressource.
   * `pageManager` - Der Seitenmanager für den Zugriff auf AEM-Inhaltsseiten ( `resourceResolver.adaptTo(PageManager.class);`).
   * `component` – das Komponentenobjekt der aktuellen AEM-Komponente.
   * `designer` - Das Designerobjekt zum Abrufen von Designinformationen ( `resourceResolver.adaptTo(Designer.class);`).
   * `currentDesign` – das Design der betreffenden Ressource.
   * `currentStyle` – der Stil der betreffenden Ressource.

### Zugreifen auf Inhalte {#accessing-content}

Es gibt drei Methoden für den Zugriff auf Inhalte in AEM WCM:

* Über das in `global.jsp`:

   Das properties-Objekt ist eine Instanz einer ValueMap (siehe [Sling API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ValueMap.html)) und enthält alle Eigenschaften der aktuellen Ressource.

   Example: `String pageTitle = properties.get("jcr:title", "no title");` used in the rendering script of a page component.

   Example: `String paragraphTitle = properties.get("jcr:title", "no title");` used in the rendering script of a standard paragraph component.

* Über das `currentPage` Objekt, das in `global.jsp`:

   Das `currentPage` Objekt ist eine Instanz einer Seite (siehe [AEM API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.mhtml)). Die Seitenklasse bietet verschiedene Methoden, um auf Inhalte zuzugreifen.

   Beispiel: `String pageTitle = currentPage.getTitle();`

* Via- `currentNode` Objekt eingeführt in `global.jsp`:

   Das `currentNode` Objekt ist eine Instanz eines Knotens (siehe [JCR-API](https://jackrabbit.apache.org/api/2.16/org/apache/jackrabbit/standalone/cli/core/CurrentNode.html)). The properties of a node can be accessed by the `getProperty()` method.

   Beispiel: `String pageTitle = currentNode.getProperty("jcr:title");`

## JSP-Tag-Bibliotheken {#jsp-tag-libraries}

Die Tag-Bibliotheken von CQ und Sling verleihen Ihnen Zugriff auf spezifische Funktionen für die Verwendung im JSP-Skript der Vorlagen und Komponenten.

For more information, see the document [Tag Libraries](/help/sites-developing/taglib.md).

## Verwendung clientseitiger HTML-Bibliotheken {#using-client-side-html-libraries}

Moderne Websites beruhen in hohem Maße auf der clientseitigen Verarbeitung durch einen komplexen JavaScript- und CSS-Code. Die Organisation und Optimierung der Bereitstellung dieses Codes kann äußerst kompliziert sein.

To help deal with this issue, AEM provides **Client-side Library Folders**, which allow you to store your client-side code in the repository, organize it into categories and define when and how each category of code is to be served to the client. Das clientseitige Bibliotheksystem übernimmt dann das Herstellen der richtigen Links auf der endgültigen Webseite, um den korrekten Code zu laden.

See the document [Using Client-Side HTML Libraries](/help/sites-developing/clientlibs.md) for more information.

## Dialogfeld {#dialog}

Ihre Komponente benötigt ein Dialogfeld für Autoren, um Inhalte hinzuzufügen und zu konfigurieren.

See [AEM Components - The Basics](/help/sites-developing/components-basics.md#dialogs) for further details.

## Konfigurieren des Bearbeitungsverhaltens {#configuring-the-edit-behavior}

Sie können das Bearbeitungsverhalten einer Komponente konfigurieren. Hierzu zählen Attribute, wie für die Komponente verfügbare Aktionen, Eigenschaften des Editors für die Bearbeitung im Kontext und die Listener, die im Zusammenhang mit den Ereignissen der Komponente stehen. Die Konfiguration ist für die Touch-optimierte und die klassische Benutzeroberfläche dieselbe, auch wenn bestimmte, spezifische Unterschiede bestehen.

The [edit behavior of a component is configured](/help/sites-developing/components-basics.md#edit-behavior) by adding a `cq:editConfig` node of type `cq:EditConfig` below the component node (of type `cq:Component`) and by adding specific properties and child nodes.

## Verwenden und Erweitern von ExtJS-Widgets {#using-and-extending-extjs-widgets}

Weitere Details finden Sie unter [Verwenden und Erweitern von ExtJS-Widgets](/help/sites-developing/widgets.md).

## Verwenden von xtypes für ExtJS-Widgets {#using-xtypes-for-extjs-widgets}

Weitere Details finden Sie unter [Verwenden von xtypes](/help/sites-developing/xtypes.md).

## Entwickeln neuer Komponenten {#developing-new-components}

Dieser Abschnitt beschreibt, wie Sie Ihre eigenen Komponenten erstellen und diese dem Absatzsystem hinzufügen.

Eine schnelle Möglichkeit für den Einstieg ist das Kopieren einer vorhandenen Komponente und das anschließende Vornehmen der gewünschten Änderungen.

Ein Beispiel für die Entwicklung einer Komponente wird detailliert unter [Erweitern der Text- und Bildkomponente – ein Beispiel](#extending-the-text-and-image-component-an-example) beschrieben.

### Entwickeln einer neuen Komponente (vorhandene Komponente anpassen) {#develop-a-new-component-adapt-existing-component}

Um neue Komponenten für AEM basierend auf einer vorhandenen Komponente zu entwickeln, können Sie die Komponente kopieren, eine JavaScript-Datei für die neue Komponente erstellen und sie an einem Ort speichern, auf den AEM zugreifen kann (siehe auch [Anpassen von Komponenten und anderen Elementen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)):

1. Verwenden Sie CRXDE Lite und erstellen Sie einen neuen Komponentenordner unter:

   / `apps/<myProject>/components/<myComponent>`

   Erstellen Sie die Knotenstruktur wie in den Bibliotheken neu und kopieren Sie dann die Definition einer vorhandenen Komponente, wie etwa die Textkomponente. Um beispielsweise die Textkomponente anzupassen, kopieren Sie diese

   * from `/libs/foundation/components/text`
   * in `/apps/myProject/components/text`

1. Modify the `jcr:title` to reflect its new name.
1. Öffnen Sie den neuen Komponentenordner und nehmen Sie die erforderlichen Änderungen vor. Löschen Sie zudem alle irrelevanten Informationen im Ordner.

   Sie können Änderungen vornehmen, wie etwa:

   * Hinzufügen eines neuen Felds im Dialogfeld

      * `cq:dialog` - Dialogfeld für die touchfähige Benutzeroberfläche
      * `dialog` – Dialogfeld für die klassische Benutzeroberfläche
   * replacing the `.jsp` file (name it after your new component)
   * oder vollständiges Überarbeiten der gesamten Komponente, falls gewünscht
   For example, if you take a copy of the standard Text component, you can add an additional field to the dialog box, then update the `.jsp` to process the input made there.

   >[!NOTE]
   >
   >Eine Komponente für:
   >
   >* Die Touch-optimierte Benutzeroberfläche verwendet [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)-Komponenten
   >* Die klassische Benutzeroberfläche verwendet [ExtJS-Widgets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html)


   >[!NOTE]
   >
   >Ein Dialogfeld, das für die klassische Benutzeroberfläche definiert ist, funktioniert auf der Touch-optimierten Benutzeroberfläche.
   >
   >Ein Dialogfeld, das für die Touch-optimierte Benutzeroberfläche definiert ist, funktioniert auf der klassischen Benutzeroberfläche nicht.
   >
   >Abhängig von Ihrer Instanz und der Autorenumgebung können Sie beide Arten eines Dialogfelds für Ihre Komponente definieren.

1. Einer der folgenden Knoten muss vorhanden und ordnungsgemäß initialisiert sein, damit die neue Komponente angezeigt wird:

   * `cq:dialog` - Dialogfeld für die touchfähige Benutzeroberfläche
   * `dialog` – Dialogfeld für die klassische Benutzeroberfläche
   * `cq:editConfig` – Verhalten von Komponenten in der Bearbeitungsumgebung (z. B Ziehen und Ablegen)
   * `design_dialog` - Dialogfeld für den Designmodus (nur klassische Benutzeroberfläche)

1. Aktivieren Sie die neue Komponente in Ihrem Absatzsystem anhand folgender Optionen:

   * using CRXDE Lite to add the value `<path-to-component>` (for example, `/apps/geometrixx/components/myComponent`) to the property components of the node `/etc/designs/geometrixx/jcr:content/contentpage/par`
   * Beachten der Anweisungen in [Hinzufügen neuer Komponenten zu Absatzsystemen](#adding-a-new-component-to-the-paragraph-system-design-mode)

1. Öffnen Sie in AEM WCM auf Ihrer Website eine Seite und fügen Sie einen neuen Absatz vom gerade erstellten Typ ein, um zu gewährleisten, dass die Komponente ordnungsgemäß funktioniert.

>[!NOTE]
>
>To see timing statistics for page loading, you can use Ctrl-Shift-U - with `?debugClientLibs=true` set in the URL.

### Hinzufügen einer neuen Komponente zum Absatzsystem (Designmodus) {#adding-a-new-component-to-the-paragraph-system-design-mode}

Nach dem Entwickeln der Komponente fügen Sie sie dem Absatzsystem hinzu. Autoren können dadurch die Komponente auswählen und verwenden, wenn sie eine Seite bearbeiten.

1. Access a page within your authoring environment that uses the paragraph system, for example `<contentPath>/Test.html`.
1. Wechseln Sie auf eine der folgenden Arten zum Designmodus:

   * Hinzufügen `?wcmmode=design` zum Ende der URL und erneuter Zugriff, z. B.:

      `<contextPath>/ Test.html?wcmmode=design`

   * Klicken auf „Design“ im Sidekick
   Sie befinden sich jetzt im Designmodus und können das Absatzsystem bearbeiten.

1. Klicken Sie auf „Bearbeiten“.

   Eine Liste von Komponenten, die zum Absatzsystem gehören, wird angezeigt. Ihre neue Komponente ist jetzt auch aufgeführt.

   Die Komponenten können aktiviert (oder deaktiviert) werden, um zu bestimmen, welche dem Verfasser beim Bearbeiten einer Seite angeboten werden.

1. Aktivieren Sie Ihre Komponente, kehren Sie dann wieder in den normalen Bearbeitungsmodus zurück, um zu bestätigen, dass sie zur Nutzung verfügbar ist.

### Erweitern der Text- und der Bildkomponente – ein Beispiel {#extending-the-text-and-image-component-an-example}

Dieser Abschnitt bietet ein Beispiel dazu, wie die weithin verwendete, standardmäßige Text- und Bildkomponente um eine konfigurierbare Bildplatzierungsfunktion erweitert wird.

Die Erweiterung der Text- und Bildkomponente ermöglicht Editoren die Nutzung sämtlicher vorhandener Funktionen der Komponente sowie zusätzlich die Möglichkeit, die Platzierung des Bilds festzulegen:

* Auf der linken Seite des Texts (aktuelles Verhalten und der neue Standard)
* Sowie auf der rechten Seite

Nach der Erweiterung dieser Komponente können Sie die Bildplatzierung über das Dialogfeld der Komponente konfigurieren.

Die folgenden Techniken werden in dieser Übung erläutert:

* Kopieren des vorhandenen Komponentenknotens und Ändern seiner Metadaten
* Ändern des Dialogfelds der Komponente, einschließlich der Vererbung von Widgets aus den übergeordneten Dialogfeldern
* Ändern des Skripts der Komponente, um die neue Funktion zu implementieren

>[!NOTE]
>
>Dieses Beispiel ist auf die klassische Benutzeroberfläche ausgerichtet.

>[!NOTE]
>
>Dieses Beispiel beruht auf dem Geometrixx-Beispielinhalt, der nicht mehr im Lieferumfang von AEM enthalten ist und durch We.Retail ersetzt wird. See the document [We.Retail Reference Implementation](/help/sites-developing/we-retail.md#we-retail-geometrixx) for how to download and install Geometrixx.

#### Erweitern der vorhandenen textimage-Komponente {#extending-the-existing-textimage-component}

Um die neue Komponente zu erstellen, verwenden wir die Standard-textimage-Komponente als Grundlage und ändern sie. Wir speichern die neue Komponente in der Geometrixx-AEM WCM-Beispielanwendung.

1. Copy the standard textimage component from `/libs/foundation/components/textimage` into the Geometrixx component folder, `/apps/geometrixx/components`, using textimage as the target node name. (Kopieren Sie die Komponente, indem Sie zur Komponente navigieren, mit der rechten Maustaste klicken, „Kopieren“ auswählen und zum Zielverzeichnis navigieren.)

   ![chlimage_1-59](assets/chlimage_1-59a.png)

1. Um dieses Beispiel einfach zu halten, navigieren Sie zu der Komponente, die Sie kopiert haben, und löschen alle Unterknoten des neuen textimage-Knotens mit Ausnahme der folgenden:

   * dialog definition: `textimage/dialog`
   * Komponentenskript: `textimage/textimage.jsp`
   * edit configuration node (allowing drag-and-drop of assets): `textimage/cq:editConfig`
   >[!NOTE]
   >
   >Die Dialogfelddefinition hängt von der Benutzeroberfläche ab:
   >
   >* Touch-enabled UI: `textimage/cq:dialog`
   >* Klassische Benutzeroberfläche: `textimage/dialog`


1. Bearbeiten Sie die Komponentenmetadaten:

   * Komponentenname

      * Setzen Sie `jcr:description` auf `Text Image Component (Extended)`
      * Setzen Sie `jcr:title` auf `Text Image (Extended)`
   * Gruppe, in der die Komponente im Sidekick aufgelistet ist (unverändert lassen)

      * Lassen Sie `componentGroup` die `General`
   * Übergeordnete Komponente für die neue Komponente (die standardmäßige textimage-Komponente)

      * Setzen Sie `sling:resourceSuperType` auf `foundation/components/textimage`
   Nach diesem Schritt sieht der Komponentenknoten wie folgt aus:

   ![chlimage_1-60](assets/chlimage_1-60a.png)

1. Ändern Sie die `sling:resourceType` Eigenschaft des Konfigurationsknotens zum Bearbeiten des Bildes (Eigenschaft: `textimage/cq:editConfig/cq:dropTargets/image/parameters/sling:resourceType`) `geometrixx/components/textimage.`

   Auf diese Weise wird beim Ablegen eines Bilds in der Komponente auf der Seite die `sling:resourceType`-Eigenschaft der erweiterten textimage-Komponente auf `geometrixx/components/textimage.` festgelegt.

1. Ändern Sie das Dialogfeld „Komponente“, damit es die neue Option enthält. Die neue Komponente erbt die Teile des Dialogfelds, die dem Original entsprechen. Wir erweitern zusätzlich lediglich die Registerkarte **Erweitert** und fügen eine Dropdown-Liste **Bildposition** mit den Optionen **Links** und **Rechts** hinzu:

   * Leave the `textimage/dialog`properties unchanged.
   Beachten Sie, dass `textimage/dialog/items` vier Unterknoten aufweist, tab1 bis tab4, die den vier Registerkarten des textimage-Dialogfelds entsprechen.

   * Für die ersten beiden Registerkarten (tab1 und tab2):

      * Ändern Sie xtype in cqinclude (um von der Standardkomponente zu erben).
      * Fügen Sie eine Pfadeigenschaft mit Werten `/libs/foundation/components/textimage/dialog/items/tab1.infinity.json`bzw. `/libs/foundation/components/textimage/dialog/items/tab2.infinity.json`Werten hinzu.
      * Entfernen Sie alle anderen Eigenschaften oder Unterknoten.
   * Für tab3:

      * Lassen Sie die Funktionen und Unterknoten unverändert.
      * Add a new field definition to `tab3/items`, node position of type `cq:Widget`
      * Set the following properties (of type String) for the new `tab3/items/position`node:

         * `name`: `./imagePosition`
         * `xtype`: `selection`
         * `fieldLabel`: `Image Position`
         * `type`: `select`
      * Add subnode `position/options` of type `cq:WidgetCollection` to represent the two choices for image placement, and under it create two nodes, o1 and o2 of type `nt:unstructured`.
      * Legen Sie für Knoten die Eigenschaften `position/options/o1` fest: `text` nach `Left` und `value` nach `left.`
      * Legen Sie für Knoten die Eigenschaften `position/options/o2` fest: `text` nach `Right` und `value` nach `right`.
   * Löschen Sie tab4.
   Die Bildposition wird im Inhalt als `imagePosition`-Eigenschaft des Knotens beibehalten, der für den Absatz `textimage` steht. Nach diesen Schritten sieht das Komponentendialogfeld folgendermaßen aus:

   ![chlimage_1-61](assets/chlimage_1-61a.png)

1. Erweitern Sie das Komponentenskript `textimage.jsp` um eine zusätzliche Bearbeitungsmöglichkeit des neuen Parameters:

   ```xml
   Image image = new Image(resource, "image");
   
   if (image.hasContent() || WCMMode.fromRequest(request) == WCMMode.EDIT) {
        image.loadStyleData(currentStyle);
   ```

   Wir ersetzen das hervorgehobene Code-Fragment *%>&lt;div class=&quot;image&quot;>&lt;%* durch einen neuen Code, der einen benutzerdefinierten Stil für dieses Tag generiert.

   ```xml
   // todo: add new CSS class for the 'right image' instead of using
   // the style attribute
   String style="";
        if (properties.get("imagePosition", "left").equals("right")) {
             style = "style=\"float:right\"";
        }
        %><div <%= style %> class="image"><%
   ```

1. Speichern Sie die Komponente im Repository. Die Komponente kann jetzt getestet werden.

#### Testen der neuen Komponente {#checking-the-new-component}

Nach der Entwicklung der Komponente können Sie sie dem Absatzsystem hinzufügen. Damit können Autoren die Komponente auswählen und verwenden, wenn sie eine Seite bearbeiten. Mit diesen Schritten können Sie die Komponente testen.

1. Öffnen Sie eine Seite in Geometrixx, wie etwa „Englisch/Unternehmen“.
1. Wechseln Sie in den Designmodus, indem Sie im Sidekick auf „Design“ klicken.
1. Bearbeiten Sie das Absatzsystemdesign, indem Sie in der Mitte der Seite im Absatzsystem auf die Schaltfläche „Bearbeiten“ klicken. Eine Liste der Komponenten, die im Absatzsystem platziert werden können, wird angezeigt und sollte Ihre neu entwickelte Komponente „Textbild (erweitert)“ enthalten. Aktivieren Sie diese für das Absatzsystem, indem Sie sie auswählen und auf „OK“ klicken.
1. Wechseln Sie zurück zum Bearbeitungsmodus.
1. Fügen Sie dem Absatzsystem den Absatz „Text-Bild (erweitert)“ hinzu und initialisieren Sie Text und Bild mit Beispielinhalten. Speichern Sie die Änderungen.
1. Öffnen Sie das Dialogfeld des Text- und Bildabsatzes, ändern Sie die Bildposition auf der Registerkarte „Erweitert“ in „Rechts“ und klicken Sie auf „OK“, um die Änderungen zu speichern.
1. Der Absatz wird mit dem Bild auf der rechten Seite wiedergegeben.
1. Die Komponente ist jetzt einsatzbereit.

Die Komponente speichert den Inhalt in einem Absatz auf der Unternehmensseite.

### Upload-Funktion der image-Komponente deaktivieren {#disable-upload-capability-of-the-image-component}

Um diese Funktion zu deaktivieren, verwenden wir die Standard-Bildkomponente als Grundlage und ändern sie. Wir speichern die neue Komponente in der Geometrixx-Beispielanwendung.

1. Copy the standard image component from `/libs/foundation/components/image` into the Geometrixx component folder, `/apps/geometrixx/components`, using image as the target node name.

   ![chlimage_1-62](assets/chlimage_1-62a.png)

1. Bearbeiten Sie die Komponentenmetadaten:

   * &quot; **jcr:title** &quot;auf `Image (Extended)`

1. Navigieren Sie zu `/apps/geometrixx/components/image/dialog/items/image`.
1. Neue Eigenschaft hinzufügen:

   * **Name**: `allowUpload`
   * **Typ**: `String`
   * **Wert**: `false`
   ![chlimage_1-63](assets/chlimage_1-63a.png)

1. Klicken Sie auf **Alle speichern**. Die Komponente kann jetzt getestet werden.
1. Öffnen Sie eine Seite in Geometrixx, wie etwa „Englisch/Unternehmen“.
1. Wechseln Sie in den Designmodus und aktivieren Sie „Bild (erweitert)“.
1. Wechseln Sie zurück zum Bearbeitungsmodus und fügen Sie diese Option dem Absatzsystem hinzu. Auf den nächsten Bildern sehen Sie die Unterschiede zwischen der ursprünglichen image-Komponente und der, die Sie soeben erstellt haben.

   Ursprüngliche image-Komponente:

   ![chlimage_1-64](assets/chlimage_1-64a.png)

   Ihre neue image-Komponente:

   ![chlimage_1-65](assets/chlimage_1-65a.png)

1. Die Komponente ist jetzt einsatzbereit.

