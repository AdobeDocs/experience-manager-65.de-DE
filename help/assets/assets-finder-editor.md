---
title: Erstellen und Konfigurieren von Asset-Editor-Seiten
description: Erfahren Sie, wie Sie benutzerdefinierte Asset-Editor-Seiten erstellen und mehrere Assets gleichzeitig bearbeiten können.
contentOwner: AG
role: User, Admin
feature: Developer Tools,Asset Management
exl-id: 53e310a9-c511-447a-91bd-8c5b2760dc03
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 98%

---

# Erstellen und Konfigurieren von Asset-Editor-Seiten {#creating-and-configuring-asset-editor-pages}

Dieses Dokument beschäftigt sich mit den folgenden Themen:

* Gründe zum Erstellen benutzerdefinierter Asset-Editor-Seiten
* Erstellen und Anpassen von Asset-Editor-Seiten, bei denen es sich um WCM-Seiten handelt, mit denen Sie Metadaten anzeigen und bearbeiten und Aktionen für das Asset durchführen können.
* Gleichzeitiges Bearbeiten mehrerer Assets

<!-- TBD: Add UICONTROL tags. Need PM review. Flatten the structure a bit. Re-write to remove Geometrixx mentions and to adhere to 6.5 default samples. -->

>[!NOTE]
>
>Die Asset-Freigabe ist als Open-Source-Refrerenzimplementierung verfügbar. Siehe [Asset-Freigabe](https://adobe-marketing-cloud.github.io/asset-share-commons/). Sie wird nicht offiziell unterstützt.

## Was spricht für das Erstellen und Konfigurieren von Asset-Editor-Seiten? {#why-create-and-configure-asset-editor-pages}

Digital Asset Management wird für eine immer größere Anzahl von Szenarien eingesetzt. Wenn Sie von einer kleinen Lösung für eine überschaubare Benutzergruppe von professionell ausgebildeten Benutzenden wie Fotografinnen und Fotografen oder Systematikerinnen und Systematikern auf größere und vielfältigere Benutzergruppen mit Geschäftsbenutzenden, WCM-Autorinnen und WCM-Autoren sowie Journalistinnen und Journalisten umstellen, kann die leistungsstarke Benutzeroberfläche von [!DNL Adobe Experience Manager Assets] zu viele Informationen bereitstellen. Stakeholder beginnen damit, bestimmte Benutzeroberflächen oder Anwendungen für den Zugriff auf die digitalen Assets anzufordern, die für sie relevant sind.

Bei diesen Asset-orientierten Anwendungen kann es sich um einfache Fotogalerien im Internet handeln, über die Mitarbeitende Fotos von Messebesuchen hochladen, oder um Pressezentren öffentlicher Websites. Asset-orientierte Anwendungen können sich auch auf komplette Lösungen, einschließlich Warenkörben, Kassengängen und Verifizierungsprozessen, erstrecken.

Das Erstellen einer Asset-orientierten Anwendung wird zu einem Konfigurationsprozess, der keine Kodierung erfordert, nur Informationen über Benutzergruppen und deren Anforderungen sowie Kenntnisse über die verwendeten Metadaten. Mit [!DNL Assets] erstellte Asset-orientierte Anwendungen sind erweiterbar: Mit moderatem Kodierungsaufwand können Sie wiederverwendbare Komponenten für die Suche, Anzeige und Bearbeitung von Assets erstellen.

Eine Asset-orientierte Anwendung in [!DNL Experience Manager] besteht aus einer Asset-Editor-Seite, die eine detaillierte Ansicht eines bestimmten Assets liefert. Über eine Asset-Editor-Seite können zudem Metadaten bearbeitet werden, sofern Benutzende, die auf das Asset zugreifen, über die erforderlichen Berechtigungen verfügen.

<!--
## Create and configure an Asset Share page {#creating-and-configuring-an-asset-share-page}

You customize the DAM Finder functionality and create pages that have all the functionality you require, which are called Asset Share pages. To create an Asset Share page, you add the page using the Geometrixx Asset Share template and then you customize the actions users can perform on that page, determine how viewers see the assets, and decide how users can build their queries.

Here are some use cases for creating a customized Asset Share page:

* Press Center for Journalists.
* Image Search Engine for internal business users.
* Image Database for website users.
* Media Tagging Interface for metadata editors.

### Create an Asset Share page {#creating-an-asset-share-page}

To create an Asset Share page, you can either create it when you are working on web sites or from the digital asset manager.

>[!NOTE]
>
>By default, when you create an Asset Share page from **New** in the digital asset manager, an Asset viewer and Asset editor are automatically created for you.

To create an new Asset Share page in the **Websites** console:

1. In the **Websites** tab, navigate to the place where you want to create an asset share page and click **New**.

1. Select the **Asset Share** page and click **Create**. The new page is created and the asset share page is listed in the **Websites** tab.

![dam8](assets/dam8.png)

The basic page created using the Geometrixx DAM Asset Share template looks as follows:

![screen_shot_2012-04-18at115456am](assets/screen_shot_2012-04-18at115456am.png)

To customize your Asset Share page, you use elements from the sidekick and you also edit query builder properties. The page **Geometrixx Press Center** is a customized version of a page based on this template:

![screen_shot_2012-04-19at123048pm](assets/screen_shot_2012-04-19at123048pm.png)

To create an asset share page by way of the digital asset manager:

1. In the digital asset manager, in **New**, select **New Asset Share**.
1. In the **Title**, enter the name of the asset share page. If desired, enter a name for the URL.

   ![screen_shot_2012-04-19at23626pm](assets/screen_shot_2012-04-19at23626pm.png)

1. Double-click the asset share page to open it and configure the page.

   ![screen_shot_2012-04-19at24114pm](assets/screen_shot_2012-04-19at24114pm.png)

   By default, when you create an Asset Share page from **New**, an Asset viewer and Asset editor are automatically created for you.

#### Customize actions {#customizing-actions}

You can determine what actions users can perform on selected digital assets from a selection of predefined actions.

To add actions to the Asset Share page:

1. In the Asset Share page that you want to customize, click **Actions** in the sidekick.

The following actions are available:

 | Action | Description |
 |---|---|
 | [!UICONTROL Delete Action] | Users can delete the selected assets. |
 | [!UICONTROL Download Action] | Lets users download selected assets to their computers. |
 | [!UICONTROL Lightbox Action] | Saves assets to a "lightbox"   where you can perform other actions on them. This comes in handy when working   with assets across multiple pages. The lightbox can also be used as a   shopping cart for assets. |
 | [!UICONTROL Move Action] | Users can move the asset to another   location |
 | [!UICONTROL Tags Action] | Lets users add tags to selected assets |
 | [!UICONTROL View Asset Action] | Opens the asset in the Asset editor for   user manipulation. |

1. Drag the appropriate action to the **Actions** area on the page. Doing so creates a button that is used to execute that action.

![chlimage_1-159](assets/chlimage_1-387.png)

#### Determine how search results are presented {#determining-how-search-results-are-presented}

You determine how results are displayed from a predefined list of lenses.

To change how search results are viewed:

1. In the Asset Share page that you want to customize, click Search.

![chlimage_1](assets/assetshare3.png)

1. Drag the appropriate lens to the top center of the page. In the Press Center, the lenses are already available. Users press the appropriate lens icon to display search results as desired.

The following lenses are available:

| Lens | Description |
|---|---|
| **[!UICONTROL List Lens]** |Presents the assets in a list fashion with details. |
| **[!UICONTROL Mosaic Lens]** |Presents assets in a mosaic fashion. |

#### Mosaic Lens {#mosaic-lens}

![chlimage_1-160](assets/chlimage_1-388.png)

#### List Lens {#list-lens}

![chlimage_1-161](assets/chlimage_1-389.png)

#### Customize the Query Builder {#customizing-the-query-builder}

The query builder lets you enter search terms and create content for the Asset Share page. When you edit the query builder, you also get to determine how many search results are displayed per page, which asset editor opens when you double-click an asset, the path the query searches, and customizes nodetypes.

To customize the query builder:

1. In the Asset Share page that you want to customize, click **Edit** in the Query Builder. By default, the **General** tab opens.
1. Select the number of results per page, the path of the asset editor (if you have a customized asset editor) and the Actions title.

![screen_shot_2012-04-23at15055pm](assets/screen_shot_2012-04-23at15055pm.png)

1. Click the **Paths** tab. Enter a path or multiple paths that the search will run. These paths are overwritten if the user uses the Paths predicate.

![screen_shot_2012-04-23at15150pm](assets/screen_shot_2012-04-23at15150pm.png)

1. Enter another node type, if desired.

1. In the **Query Builder URL** field, you can override or wrap the query builder and enter the new servlet URLs with the existing query builder component. In the **Feed URL** field, you can override the Feed URL as well.

![screen_shot_2012-04-23at15313pm](assets/screen_shot_2012-04-23at15313pm.png)

1. In the **Text** field, enter the text you want to appear for results and page numbers of results. Click **OK** when finished making changes.

![screen_shot_2012-04-23at15300pm](assets/screen_shot_2012-04-23at15300pm.png)

#### Add predicates {#adding-predicates}

Experience Manager Assets includes several predicates that you can add to the Asset Share page. These let your users further narrow searches. In some cases, they may override a query builder parameter (for example, the Path parameter).

To add predicates:

1. In the Asset Share page that you want to customize, click **Search**.

![assetshare3](assets/assetshare3.png)

1. Drag the appropriate predicates to the Asset Share page underneath the query builder. Doing so creates the appropriate fields.

![assetshare4](assets/assetshare4.png)

The following predicates are available:

| Predicate | Description |
|---|---|
| **[!UICONTROL Date Predicate]** |Lets users search for assets that were modified before and after certain dates. |
| **[!UICONTROL Options Predicate]** |The site owner can specify a property to search for (as in the property predicate, for example, cq:tags) and a content tree to populate the options from (for example, the tag tree). Doing so generates a list of options where the users can select the values (tags) that the selected property (tag property) should have. This predicate lets you build list controls like the list of tags, file types, image orientations, and so on. It is great for a fixed set of options. |
| **[!UICONTROL Path Predicate]** |Lets users define the path and subfolders, if desired. |
| **[!UICONTROL Property Predicate]** |The site owner specifies a property to search for, for example, tiff:ImageLength and the user can then enter a value, for example, 800. This returns all images that are 800 pixels high. Useful predicate if your property can have arbitrary values. |

For more information, see the [predicate Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/package-summary.html).

1. To configure the predicate further, double-click it. For example, when you open the Path Predicate, you need to assign the root path.

![screen_shot_2012-04-23at15640pm](assets/screen_shot_2012-04-23at15640pm.png)
-->

## Erstellen und Konfigurieren einer Asset-Editor-Seite {#creating-and-configuring-an-asset-editor-page}

Sie können den Asset-Editor anpassen, um festzulegen, wie Benutzende die digitalen Assets anzeigen und bearbeiten können. Erstellen Sie dazu eine Asset-Editor-Seite und passen Sie dann die Ansichten und Aktionen an, die Benutzende auf dieser Seite ausführen können.

>[!NOTE]
>
>Wenn Sie den DAM-Asset-Editor um benutzerdefinierte Felder ergänzen möchten, fügen Sie neue `cq:Widget`-Knoten zu `/apps/dam/content/asseteditors.` hinzu.

### Erstellen einer Asset-Editor-Seite {#creating-the-asset-editor-page}

Beim Erstellen der Asset-Editor-Seite empfiehlt es sich, die Seite direkt unter der Asset-Freigabe-Seite zu erstellen.

So erstellen Sie eine Asset-Editor-Seite:

1. Navigieren Sie auf der Registerkarte **[!UICONTROL Websites]** zu der Stelle, an der Sie eine Asset-Editor-Seite erstellen möchten, und klicken Sie auf **Neu**.
1. Wählen Sie **Geometrixx-Asset-Editor** und klicken Sie auf **Erstellen**. Die neue Seite wird erstellt und auf der Registerkarte **Websites** aufgeführt.

![screen_shot_2012-04-23at15858pm](assets/screen_shot_2012-04-23at15858pm.png)

Die mit der Vorlage „Geometrixx-Asset-Editor“ erstellte Standardseite sieht wie folgt aus:

![assetshare5](assets/assetshare5.png)

Anpassen können Sie die Asset-Editor-Seite mithilfe der Elemente aus dem Sidekick. Die Seite, auf die über das **Geometrixx-Pressezentrum** zugegriffen wird, ist eine angepasste Version einer auf dieser Vorlage basierenden Seite:

![assetshare6](assets/assetshare6.png)

#### Festlegen, dass ein Asset-Editor über eine Asset-Freigabe-Seite geöffnet wird {#setting-which-asset-editor-opens-from-an-asset-share-page}

Nachdem Sie die benutzerdefinierte Asset-Editor-Seite erstellt haben, stellen Sie sicher, dass beim Doppelklicken auf Assets diese über die von Ihnen erstellte benutzerdefinierten Asset-Freigabe in der benutzerdefinierten Editor-Seite geöffnet werden.

So legen Sie die Asset-Editor-Seite fest:

1. Klicken Sie auf der Asset-Freigabe-Seite neben dem Query Builder auf **Bearbeiten**.

![screen_shot_2012-04-23at20123pm](assets/screen_shot_2012-04-23at20123pm.png)

1. Klicken Sie auf die Registerkarte **Allgemein**, sofern diese nicht bereits ausgewählt ist.

1. Geben Sie in das Feld **Pfad des Asset-Editors** den Pfad zu dem Asset-Editor ein, in dem die Asset-Freigabe-Seite Assets öffnen soll, und klicken Sie auf **OK**.

![screen_shot_2012-04-23at21653pm](assets/screen_shot_2012-04-23at21653pm.png)

#### Hinzufügen von Asset-Editor-Komponenten {#adding-asset-editor-components}

Sie bestimmen, über welche Funktionen ein Asset-Editor verfügt, indem Sie Komponenten zur Seite hinzufügen.

So fügen Sie Asset-Editor-Komponenten hinzu:

1. Klicken Sie auf der anzupassenden Asset-Editor-Seite im Sidekick auf **Asset-Editor**. Alle verfügbaren Asset-Editor-Komponenten werden angezeigt.

>[!NOTE]
>
>Was Sie anpassen können, hängt von den verfügbaren Komponenten ab. Um Komponenten zu aktivieren, wechseln Sie in den Design-Modus und wählen Sie die zu aktivierenden Komponenten aus.

1. Ziehen Sie die Komponenten aus dem Sidekick in den Asset-Editor und nehmen Sie Änderungen in den Komponentendialogfeldern vor. Die Komponenten werden in der folgenden Tabelle und in den nachfolgenden detaillierten Anweisungen beschrieben.

>[!NOTE]
>
>Beim Entwerfen der Asset-Editor-Seite erstellen Sie Komponenten, die entweder schreibgeschützt oder bearbeitbar sind. Benutzende wissen, dass ein Feld bearbeitet werden kann, wenn ein Bleistift in dieser Komponente abgebildet wird. Standardmäßig sind die meisten Komponenten als schreibgeschützt eingerichtet.

| Komponente | Beschreibung |
|---|---|
| **[!UICONTROL Metadatenformular] und [!UICONTROL Metadaten-Textfeld]** | Ermöglicht das Hinzufügen zusätzlicher Metadaten zu einem Asset und das Ausführen einer Aktion (z. B. Senden) für dieses Asset. |
| **[!UICONTROL Unter-Assets]** | Ermöglicht das Anpassen von Unter-Assets. |
| **Tags** | Benutzende haben die Möglichkeit, Tags auszuwählen und zu einem Asset hinzuzufügen. |
| **[!UICONTROL Miniaturansicht]** | Zeigt eine Miniaturansicht des Assets und dessen Dateinamen an und ermöglicht das Hinzufügen eines alternativen Textes. Hierüber können Sie zudem Asset-Editor-Aktionen hinzufügen. |
| **[!UICONTROL Titel]** | Zeigt den Asset-Titel an, der angepasst werden kann. |

![screen_shot_2012-04-23at22743pm](assets/screen_shot_2012-04-23at22743pm.png)

#### Metadatenformular und Textfeld – Konfigurieren der Komponente „Metadaten anzeigen“ {#metadata-form-and-text-field-configuring-the-view-metadata-component}

Das Metadatenformular ist ein Formular mit einer Start- und einer Endaktion. Dazwischen geben Sie **Textfelder** ein. Weitere Informationen zum Verwenden von Formularen finden Sie unter [Formulare](/help/sites-authoring/default-components-foundation.md#form-component).

1. Erstellen Sie eine Startaktion, indem Sie im Startbereich des Formulars auf **Bearbeiten** klicken. Sie können bei Bedarf einen Box-Titel eingeben. Standardmäßig lautet der Box-Titel **Metadaten**. Aktivieren Sie das Kontrollkästchen „Client-Validierung“, wenn der JavaScript-Clientcode zur Validierung generiert werden soll.

![screen_shot_2012-04-23at22911pm](assets/screen_shot_2012-04-23at22911pm.png)

1. Erstellen Sie eine Endaktion, indem Sie im Endbereich des Formulars auf **Bearbeiten** klicken. Beispielsweise können Sie eine Option **[!UICONTROL Absenden]** zum Übermitteln geänderter Metadaten erstellen. Optional Sie können auch OPTIONS **Zurücksetzen** hinzufügen, um den ursprünglichen Zustand der Metadaten wiederherzustellen.

![screen_shot_2012-04-23at23138pm](assets/screen_shot_2012-04-23at23138pm.png)

1. Ziehen Sie zwischen **Formular-Start** und **Formular-Ende** die Metadaten-Textfelder in das Formular. Benutzende füllen diese Textfelder mit Metadaten auf, die übermittelt werden können oder für die eine weitere Aktion ausgeführt werden kann.

1. Doppelklicken Sie auf den Feldnamen, z. B. **Titel**, um das Metadatenfeld zu öffnen und Änderungen vorzunehmen. Definieren Sie auf der Registerkarte **Allgemein** des Fensters **Komponente bearbeiten** den Namespace, die Feldbezeichnung sowie den Typ, z. B. `dc:title`.

![screen_shot_2012-04-23at23305pm](assets/screen_shot_2012-04-23at23305pm.png)

Informationen zum Ändern der im Metadatenformular verfügbaren Namespaces finden Sie unter [Anpassen und Erweitern von Assets](/help/assets/extending-assets.md).

1. Klicken Sie auf die Registerkarte **Beschränkungen**. Hier können Sie festlegen, ob ein Feld erforderlich ist, und ggf. weitere Beschränkungen hinzufügen.

![screen_shot_2012-04-23at23435pm](assets/screen_shot_2012-04-23at23435pm.png)

1. Klicken Sie auf die Registerkarte **Anzeigen**. Hier können Sie eine neue Breite und die Anzahl der Zeilen für das Metadatenfeld eingeben. Aktivieren Sie das Kontrollkästchen **Feld ist schreibgeschützt**, damit Benutzende die Metadaten bearbeiten können.

![screen_shot_2012-04-23at23446pm](assets/screen_shot_2012-04-23at23446pm.png)

Es folgt ein Beispiel für ein Metadatenformular mit verschiedenen Feldern:

![Metadaten](assets/chlimage_1-390.png)

Auf der Asset-Editor-Seite können Benutzende dann Werte in die Metadatenfelder eingeben (sofern diese bearbeitbar sind) und die Endaktion ausführen (etwa Änderungen übermitteln).

#### Unter-Assets {#sub-assets}

Über die Komponente „Teil-Assets“ können Sie Teil-Assets anzeigen und auswählen. Sie können festlegen, welche Namen unter dem [Haupt-Asset](/help/assets/assets.md#what-are-digital-assets) und den Teil-Assets angezeigt werden.

Doppelklicken Sie auf die Komponente „Teil-Assets“, um das Dialogfeld „Teil-Assets“ zu öffnen, in dem Sie die Titel für das Haupt-Asset und alle Teil-Assets ändern können. Die Standardwerte werden unter dem entsprechenden Feld angezeigt.

![screen_shot_2012-04-23at23907pm](assets/screen_shot_2012-04-23at23907pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Unter-Assets“:

![screen_shot_2012-04-23at24442pm](assets/screen_shot_2012-04-23at24442pm.png)

Achten Sie z. B. bei Auswahl eines Unter-Assets darauf, wie die Komponente die entsprechende Seite anzeigt und sich der Box-Titel von „Unter-Assets“ zu „Gleichgeordnete“ ändert.

![screen_shot_2012-04-23at24552pm](assets/screen_shot_2012-04-23at24552pm.png)

#### Tags {#tags}

Über die Komponente „Tags“ können Benutzende einem Asset vorhandene Tags zuweisen, was später die Organisation und den Abruf vereinfacht. Sie können diese Komponente als schreibgeschützt festlegen, sodass Benutzende keine Tags hinzufügen, sondern nur anzeigen können.

![screen_shot_2012-04-23at25031pm](assets/screen_shot_2012-04-23at25031pm.png)

Doppelklicken Sie auf die Komponente „Tags“, um das gleichnamige Dialogfeld zu öffnen, in dem Sie den Titel „Tags“ ggf. ändern und die zugewiesenen Namespaces auswählen können. Damit dieses Feld bearbeitet werden kann, deaktivieren Sie das Kontrollkästchen **[!UICONTROL Bearbeitungsschaltfläche ausblenden]**. Standardmäßig können Tags bearbeitet werden.

![screen_shot_2012-04-23at24731pm](assets/screen_shot_2012-04-23at24731pm.png)

Wenn Benutzende Tags bearbeiten können, können sie auf das Bleistiftsymbol klicken, um Tags durch Auswahl aus dem Dropdownmenü hinzuzufügen.

![screen_shot_2012-04-23at25150pm](assets/screen_shot_2012-04-23at25150pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Tags“:

![screen_shot_2012-04-23at25244pm](assets/screen_shot_2012-04-23at25244pm.png)

#### Miniaturansicht {#thumbnail}

Über die Komponente „Miniaturansicht“ wird für ein Asset die ausgewählte Miniaturansicht angezeigt (für viele Formate wird die Miniaturansicht automatisch extrahiert). Außerdem präsentiert die Komponente den Dateinamen und [von Ihnen veränderbare Aktionen](/help/assets/assets-finder-editor.md#adding-asset-editor-actions).

![screen_shot_2012-04-23at25452pm](assets/screen_shot_2012-04-23at25452pm.png)

Doppelklicken Sie auf die Komponente „Miniaturansicht“, um das gleichnamige Dialogfeld zum Ändern des ALT-Texts zu öffnen. Standardmäßig wird **Klicken, um Asset herunterzuladen** als ALT-Text für die Miniatur angezeigt.

![screen_shot_2012-04-23at25604pm](assets/screen_shot_2012-04-23at25604pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Miniatur“:

![screen_shot_2012-04-23at34815pm](assets/screen_shot_2012-04-23at34815pm.png)

#### Titel {#title}

Über die Komponente „Titel“ werden der Titel des Assets und eine Beschreibung angezeigt.

Standardmäßig liegt die Komponente im schreibgeschützten Modus vor, um eine Bearbeitung durch Benutzende zu verhindern. Damit sie bearbeitet werden kann, doppelklicken Sie auf die Komponente und deaktivieren Sie das Kontrollkästchen **Bearbeitungsschaltfläche ausblenden**. Geben Sie außerdem einen Titel für mehrere Assets ein.

![screen_shot_2012-04-23at35100pm](assets/screen_shot_2012-04-23at35100pm.png)

Wenn der Titel bearbeitet werden kann, können Sie einen Titel und eine Beschreibung hinzufügen, indem Sie durch Klicken auf das Bleistiftsymbol das Fenster **Asset-Eigenschaften** öffnen. Darüber hinaus können Sie das Asset ein- und ausschalten, indem Sie Datum und Uhrzeit auswählen.

Beim Bearbeiten von [!UICONTROL Titel] können Benutzende den **Titel** und die **Beschreibung** ändern und **Einschaltzeiten** sowie **Ausschaltzeiten** eingeben, um das Asset zu aktivieren und zu deaktivieren.

![screen_shot_2012-04-23at35241pm](assets/screen_shot_2012-04-23at35241pm.png)

Es folgt ein Beispiel für eine ausgefüllte Komponente „Titel“:

![chlimage_1-164](assets/chlimage_1-392.png)

#### Hinzufügen von Asset-Editor-Aktionen {#adding-asset-editor-actions}

Anhand einer Auswahl vordefinierter Aktionen können Sie bestimmen, welche Aktionen Benutzende für ausgewählte digitale Assets ausführen dürfen.

So fügen Sie der Asset-Editor-Seite Aktionen hinzu:

1. Klicken Sie auf der anzupassenden Asset-Editor-Seite im Sidekick auf **Asset-Editor**.

![screen_shot_2012-04-23at35515pm](assets/screen_shot_2012-04-23at35515pm.png)

Die folgenden Aktionen sind verfügbar:

| Aktion | Beschreibung |
|---|---|
| [!UICONTROL Download] | Ermöglicht Benutzenden das Herunterladen ausgewählter Assets auf ihre Computer. |
| [!UICONTROL Editoren] | Ermöglicht Benutzenden die Bearbeitung eines Bildes (interaktive Bearbeitung). |
| [!UICONTROL Lightbox] | Speichert Assets in einer „Lightbox“, in der Sie andere Aktionen durchführen können. Dies ist praktisch, wenn über mehrere Seiten hinweg an Assets gearbeitet wird. |
| [!UICONTROL Sperren] | Ermöglicht es Benutzenden, ein Asset zu sperren. Diese Funktion ist nicht standardmäßig aktiviert und muss in der Liste der Komponenten aktiviert werden. |
| [!UICONTROL Verweise] | Klicken Sie auf diese Option, um anzuzeigen, auf welchen Seiten das Asset verwendet wird. |
| [!UICONTROL Versionierung] | Ermöglicht das Erstellen und Wiederherstellen von Versionen eines Assets. |

1. Ziehen Sie die entsprechende Aktion in den Bereich **Aktionen** auf der Seite. Hierdurch wird eine Option erstellt, mit der die auf die Seite gezogene Aktion ausgeführt wird.

![chlimage_1-165](assets/chlimage_1-393.png)

## Mehrfachbearbeitung von Assets mit einer Asset-Editor-Seite {#multi-editing-assets-with-the-asset-editor-page}

Mit [!DNL Experience Manager Assets] können Sie mehrere Assets gleichzeitig ändern. Nachdem Sie die Assets ausgewählt haben, können Sie gleichzeitig Tags und Metadaten ändern.

So führen Sie eine Mehrfachbearbeitung von Assets mit der Asset-Editor-Seite durch:

1. Öffnen Sie die Geometrixx-Seite **Pressezentrum**:
   `https://localhost:4502/content/geometrixx/en/company/press.html`

1. Wählen Sie die Assets aus:

   * unter Windows: `Ctrl + click` auf jedes Asset.
   * unter Mac: `Cmd + click` auf jedes Asset.

   Um einen Bereich von Assets auszuwählen, klicken Sie auf das erste Asset und dann `Shift + click` auf das letzte Asset.

1. Klicken Sie im Feld **Aktionen** auf **Metadaten bearbeiten** (linker Seitenbereich).
1. Die Geometrixx-Seite mit dem **Pressezentrum-Asset-Editor** wird auf einer neuen Registerkarte geöffnet. Die Metadaten der Assets werden wie folgt angezeigt:

   * Ein Tag, das nicht für alle Assets gilt, sondern nur für einige wenige, wird kursiv dargestellt.
   * Ein Tag, das für alle Assets gilt, wird in normaler Schrift angezeigt.
   * Andere Metadaten als Tags: Der Wert des Felds wird nur angezeigt, wenn dieser für alle ausgewählten Assets identisch ist.

1. Klicken Sie auf **Herunterladen**, um eine ZIP-Datei mit den ursprünglichen Ausgabedarstellungen des Assets herunterzuladen.
1. Klicken Sie auf die Option zum Bearbeiten der Tags neben dem Feld **Tags**.

   * Ein Tag, das nicht für alle Assets gilt, sondern nur für einige wenige, hat einen grauen Hintergrund.
   * Ein Tag, das für alle Assets gilt, hat einen weißen Hintergrund.

   Sie haben folgende Möglichkeiten:

   * Klicken Sie auf `x`, um das Tag für alle Assets zu entfernen.
   * Klicken Sie auf `+`, um das Tag allen Assets hinzuzufügen.
   * Klicken Sie auf den **Pfeil** und wählen Sie ein Tag aus, um allen Assets ein neues Tag hinzuzufügen.

   Klicken Sie auf **OK**, um die Änderungen in das Formular zu schreiben. Das Kästchen neben dem Feld **Tags** wird automatisch aktiviert.

1. Bearbeiten Sie das Feld „Beschreibung“. Setzen Sie sie beispielsweise auf:

   `This is a common description`

   Wenn ein Feld bearbeitet wird, überschreibt sein Wert die vorhandenen Werte der ausgewählten Assets, sobald das Formular übermittelt wird.

   Hinweis: Das Kästchen neben dem Feld wird automatisch aktiviert, wenn das Feld bearbeitet wird.

1. Klicken Sie auf **Metadaten aktualisieren**, um das Formular abzusenden und die Änderungen für alle Assets zu speichern.

   Hinweis: Nur die ausgewählten Metadaten werden geändert.
