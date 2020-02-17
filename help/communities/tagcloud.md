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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

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

Legen Sie auf der Registerkarte **[!UICONTROL Social Tag-Cloud]** fest, welche Tags angezeigt werden sollen, und geben Sie den Ort der Suchergebnisseite an, falls es sich bei den Tags um aktive Links handelt:

![chlimage_1-305](assets/chlimage_1-305.png)

* **[!UICONTROL Anzuzeigende Social Tags]** Legt fest, welche UGC-Tags angezeigt werden sollen. Die verfügbaren Optionen sind

   * `From page and child pages`
   * `All tags`
   Die Standardeinstellung ist `From page and child pages`, wobei &quot;page&quot;auf die **Seiteneinstellung** unten verweist.

* **[!UICONTROL Seite]**(erforderlich, wenn nicht `All tags)` Der Pfad zum UGC für eine Seite. Wird kein Pfad angegeben, verweist die Standardeinstellung automatisch auf die aktuelle Seite.

* **[!UICONTROL Keine Einschränkung bezüglich Tags]** Ist diese Option aktiviert, werden Tags in der Tag-Cloud als normaler Text dargestellt. Wenn diese Option nicht aktiviert ist, werden die Tags als aktive Links angezeigt, die nach allen Inhalten suchen, auf die dieses Tag angewendet wird. Standardmäßig ist die Option deaktiviert und es muss ein **[!UICONTROL Suchergebnispfad]** festgelegt werden.

* **[!UICONTROL Suchergebnispfad]** Der Pfad zu einer Seite, auf der eine `Search Result` Komponente platziert wurde, die so konfiguriert ist, dass auf UGC verwiesen wird, das den von der Einstellung &quot; **Seite** &quot;angegebenen UGC-Pfad enthält.

## Anpassen der Anzeige einer Social-Tag-Cloud {#change-display-of-social-tag-cloud}

To edit the display of the **Social Tag Cloud**, enter [Design Mode](../../help/sites-authoring/default-components-designmode.md) and double click on the placed `Social Tag Cloud` component to open a dialog with an additional tab.

Using the **[!UICONTROL Social Tag Cloud (Design)]** tab, specify how tags are displayed. Ein Tag kann ein einfaches Tag, ein einzelnes Wort im Standard-Namespace oder eine hierarchische Taxonomie sein:

![chlimage_1-306](assets/chlimage_1-306.png)

* **[!UICONTROL Vollständige Titelpfade anzeigen]** Ist diese Option aktiviert, werden die Titel der übergeordneten Tags sowie der Namespace für alle verwendeten Tags angezeigt.

   Beispiel:

   * Aktiviert: `Geometrixx Media: Gadgets / Cars`
   * Deaktiviert: `Cars`
   Bei einfachen Tags ist kein Unterschied feststellbar.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Nur Leaf-Tags anzeigen]** Ist diese Option aktiviert, werden nur verwendete Tags angezeigt, in denen keine weiteren Tags enthalten sind.

   Wenn beispielsweise TagID von

   `Geometrixx Media: Gadgets / Cars`

   Es gibt drei Tags, die angewendet werden können: `Geometrixx Media (the namespace)`, `Gadgets`und `Cars`

   * Checked: only `Cars` will display, if applied
   * Unchecked: `Geometrixx Media` and `Gadgets`as well as `Cars` will display, if applied
   Einfache Tags sind immer Leaf-Tags.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Verknüpfungsvorlage]** Eine Vorlage, die sich von der Standardeinstellung unterscheidet und dazu dient, Links in einer Tag-Cloud anzuzeigen, wenn diese im Dialogfeld für die Komponentenbearbeitung aktiviert wurden.

* **[!UICONTROL Gleiche Größe für alle Tags]** Ist diese Option aktiviert, werden alle Wörter einer Tag-Cloud nach demselben Muster formatiert. Wenn diese Option deaktiviert ist, werden Wörter je nach Verwendung unterschiedlich formatiert. Diese Option ist standardmäßig deaktiviert.

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Tag Essentials](tag.md) page for developers.

See [Tagging User Generated Content](tag-ugc.md) (UGC) for information about creating and managing tags.
