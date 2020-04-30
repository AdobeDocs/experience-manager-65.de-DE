---
title: Verwenden von einer Social-Tag-Cloud
seo-title: Verwenden von einer Social-Tag-Cloud
description: Hinzufügen einer Social Tag Cloud-Komponente zu einer Seite
seo-description: Hinzufügen einer Social Tag Cloud-Komponente zu einer Seite
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
translation-type: tm+mt
source-git-commit: 77d00c1d6e94b257aa0533ca88b5f9a12dba0054

---


# Verwenden von einer Social-Tag-Cloud {#using-social-tag-cloud}

## Einführung {#introduction}

The `Social Tag Cloud` component highlights tags applied by community members when posting content. Dies dient der Bestimmung beliebter Themen und ermöglicht es Site-Besuchern, gekennzeichnete Inhalte schneller aufzufinden.

Informationen zu einer weiteren Möglichkeit zur Bestimmung von Trends finden Sie unter [Aktivitätstrends](trends.md).

This page documents the `Social Tag Cloud` component dialog settings and describes the user experience.

Detaillierte Informationen für Entwickler finden Sie unter [Tag-Grundlagen](tag.md).

See [Administering Tags](../../help/sites-administering/tags.md) for information about creating and managing tags, as well as to which content tags have been applied.

## Hinzufügen einer Social-Tag-Cloud {#adding-a-social-tag-cloud}

Wenn Sie einer Seite im Autorenmodus eine `Social Tag Cloud` `Communities / Social Tag Cloud` Komponente hinzufügen möchten, suchen Sie die Komponente im Komponenten-Browser und ziehen Sie sie auf eine Seite, auf der die Tag-Cloud angezeigt werden soll.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](tag.md#essentials-for-client-side) are included, this is how the `Social Tag Cloud` component will appear:

![chlimage_1-303](assets/chlimage_1-303.png)

## Konfigurieren einer Social-Tag-Cloud {#configuring-social-tag-cloud}

Select the placed `Social Tag Cloud` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-304](assets/chlimage_1-304.png)

Under the **[!UICONTROL Social Tag Cloud]** tab, specify which tags to display and, if the tags are active links, the location of the page for search results:

![chlimage_1-305](assets/chlimage_1-305.png)

* **[!UICONTROL Anzuzeigende Social Tags]** Legt fest, welche UGC-Tags angezeigt werden sollen. Die verfügbaren Optionen sind:

   * `From page and child pages`
   * `All tags`
   Die Standardeinstellung ist `From page and child pages`, wobei &quot;page&quot;auf die unten stehende Einstellung &quot; **Page** &quot;verweist.

* **[!UICONTROL Seite]**

   (Required if not `All tags)` The path to the UGC for a page. Wird kein Pfad angegeben, verweist die Standardeinstellung automatisch auf die aktuelle Seite.

* **[!UICONTROL Keine Einschränkung bezüglich Tags]**

   Wenn diese Option aktiviert ist, werden die Tags in der Tag-Cloud als Nur-Text angezeigt. Wenn diese Option nicht aktiviert ist, werden die Tags als aktive Links angezeigt, die nach allen Inhalten suchen, auf die dieses Tag angewendet wird. Standardmäßig ist die Option deaktiviert und es muss ein **[!UICONTROL Suchergebnispfad]** festgelegt werden.

* **[!UICONTROL Suchergebnispfad]**

   The path to a page on which a `Search Result` component has been placed, configured to reference UGC which includes the UGC path specified by the **Page** setting.

## Anpassen der Anzeige einer Social-Tag-Cloud {#change-display-of-social-tag-cloud}

To edit the display of the **Social Tag Cloud**, enter [Design Mode](../../help/sites-authoring/default-components-designmode.md) and double click on the placed `Social Tag Cloud` component to open a dialog with an additional tab.

Using the **[!UICONTROL Social Tag Cloud (Design)]** tab, specify how tags are displayed. Ein Tag kann ein einfaches Tag, ein einzelnes Wort im Standard-Namensraum oder eine hierarchische Taxonomie sein:

![chlimage_1-306](assets/chlimage_1-306.png)

* **[!UICONTROL Vollständige Titelpfade anzeigen]**

   Wenn diese Option aktiviert ist, werden die Titel der übergeordneten Tags und des Namensraums für jedes angewendete Tag angezeigt.

   Beispiel:

   * Aktiviert: `Geometrixx Media: Gadgets / Cars`
   * Deaktiviert: `Cars`
   Bei einfachen Tags ist kein Unterschied feststellbar.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Nur Leaf-Tags anzeigen]**

   Wenn diese Option aktiviert ist, werden nur angewendete Tags angezeigt, die keine anderen Tags enthalten.

   Beispiel für TagID:

   `Geometrixx Media: Gadgets / Cars`

   Es gibt drei Tags, die angewendet werden können:

   `Geometrixx Media (the namespace)`, `Gadgets`, und `Cars`

   * Checked: Only `Cars` will display, if applied.
   * Unchecked: `Geometrixx Media` and `Gadgets`as well as `Cars` will display, if applied.
   Einfache Tags sind immer Leaf-Tags.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Verknüpfungsvorlage]**

   Eine Vorlage, die nicht standardmäßig verwendet wird, um die Links in einer Tag-Cloud anzuzeigen, wenn die Verknüpfungen über das Dialogfeld zum Bearbeiten der Komponente aktiviert werden.

* **[!UICONTROL Gleiche Größe für alle Tags]**

   Wenn diese Option aktiviert ist, werden alle Wörter in der Tag-Cloud gleich formatiert. Wenn diese Option deaktiviert ist, werden Wörter je nach Verwendung unterschiedlich formatiert. Diese Option ist standardmäßig deaktiviert.

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Tag Essentials](tag.md) page for developers.

See [Tagging User Generated Content](tag-ugc.md) (UGC) for information about creating and managing tags.
