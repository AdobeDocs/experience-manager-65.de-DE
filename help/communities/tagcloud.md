---
title: Verwenden von einer Social-Tag-Cloud
seo-title: Using Social Tag Cloud
description: Hinzufügen einer Social-Tag-Cloud-Komponente zu einer Seite
seo-description: Adding a Social Tag Cloud component to a page
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
exl-id: 56af5362-78de-4308-8958-63a45e8573cc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 26%

---

# Verwenden von einer Social-Tag-Cloud {#using-social-tag-cloud}

## Einführung    {#introduction}

Die `Social Tag Cloud` -Komponente hebt Tags hervor, die von Community-Mitgliedern beim Posten von Inhalten angewendet werden. Dies dient der Bestimmung beliebter Themen und ermöglicht es Site-Besuchern, gekennzeichnete Inhalte schneller aufzufinden.

Informationen zu einer weiteren Möglichkeit zur Bestimmung von Trends finden Sie unter [Aktivitätstrends](trends.md).

Diese Seite dokumentiert die `Social Tag Cloud` Einstellungen des Komponentendialogfelds und beschreibt das Benutzererlebnis.

Detaillierte Informationen für Entwickler finden Sie unter [Tag-Grundlagen](tag.md).

Siehe [Verwalten von Tags](../../help/sites-administering/tags.md) Informationen zum Erstellen und Verwalten von Tags sowie dazu, auf welche Inhalts-Tags angewendet wurden.

## Hinzufügen einer Social-Tag-Cloud {#adding-a-social-tag-cloud}

So fügen Sie eine `Social Tag Cloud` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Social Tag Cloud` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der die Tag-Cloud erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](tag.md#essentials-for-client-side) eingeschlossen sind, wird die `Social Tag Cloud` wird angezeigt:

![social-tag](assets/social-tag.png)

## Konfigurieren einer Social-Tag-Cloud {#configuring-social-tag-cloud}

Wählen Sie die platzierte `Social Tag Cloud` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **[!UICONTROL Social Tag Cloud]** angeben, welche Tags angezeigt werden sollen, und, wenn es sich bei den Tags um aktive Links handelt, den Speicherort der Seite für Suchergebnisse angeben:

![social-tag-cloud](assets/social-tag-cloud.png)

* **[!UICONTROL Anzuzeigende Social Tags]** Legt fest, welche UGC-Tags angezeigt werden sollen. Die verfügbaren Optionen sind:

   * `From page and child pages`
   * `All tags`

   Der Standardwert ist `From page and child pages`, wobei &quot;Seite&quot;auf die **Seite** unten.

* **[!UICONTROL Page]**

   (Erforderlich, falls nicht erforderlich `All tags)` Der Pfad zum benutzergenerierten Inhalt einer Seite. Wird kein Pfad angegeben, verweist die Standardeinstellung automatisch auf die aktuelle Seite.

* **[!UICONTROL Keine Einschränkung bezüglich Tags]**

   Wenn diese Option aktiviert ist, werden die Tags in der Tag-Cloud als Nur-Text angezeigt. Wenn diese Option deaktiviert ist, werden die Tags als aktive Links angezeigt, die nach allen Inhalten suchen, auf die dieses Tag angewendet wird. Standardmäßig ist die Option deaktiviert und es muss ein **[!UICONTROL Suchergebnispfad]** festgelegt werden.

* **[!UICONTROL Suchergebnispfad]**

   Der Pfad zu einer Seite, auf der ein `Search Result` -Komponente platziert wurde, die so konfiguriert ist, dass sie auf UGC verweist, das den durch die **Seite** -Einstellung.

## Anpassen der Anzeige einer Social-Tag-Cloud {#change-display-of-social-tag-cloud}

So bearbeiten Sie die Anzeige der **Social Tag Cloud**, eingeben [Designmodus](../../help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Social Tag Cloud` -Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Verwenden der **[!UICONTROL Social Tag Cloud (Design)]** Registerkarte angeben, wie Tags angezeigt werden. Ein Tag kann ein einfaches Tag, ein einzelnes Wort im Standard-Namespace oder eine hierarchische Taxonomie sein:

![social-tag-cloud-design](assets/social-tag-cloud-design.png)

* **[!UICONTROL Vollständige Titelpfade anzeigen]**

   Wenn diese Option aktiviert ist, zeigt die Titel für die übergeordneten Tags und den Namespace für jedes angewendete Tag an.

   Beispiel:

   * Aktiviert: `Geometrixx Media: Gadgets / Cars`
   * Deaktiviert: `Cars`

   Bei einfachen Tags ist kein Unterschied feststellbar.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Nur Leaf-Tags anzeigen]**

   Wenn diese Option aktiviert ist, werden nur angewendete Tags angezeigt, die keine anderen Tags enthalten.

   Beispielsweise bei der TagID von:

   `Geometrixx Media: Gadgets / Cars`

   Es gibt 3 Tags, die angewendet werden können:

   `Geometrixx Media (the namespace)`, `Gadgets`, und `Cars`

   * Aktiviert: Nur `Cars` wird angezeigt, falls angewendet.
   * deaktiviert: `Geometrixx Media` und `Gadgets`sowie `Cars` wird angezeigt, falls angewendet.

   Einfache Tags sind immer Leaf-Tags.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Verknüpfungsvorlage]**

   Eine andere Vorlage als die Standardvorlage, mit der die Links in einer Tag-Cloud angezeigt werden, wenn Links über das Dialogfeld &quot;Komponentenbearbeitung&quot;aktiviert werden.

* **[!UICONTROL Gleiche Größe für alle Tags]**

   Wenn diese Option aktiviert ist, werden alle Wörter in der Tag-Cloud denselben Stil zugewiesen. Wenn diese Option deaktiviert ist, werden Wörter je nach Verwendung unterschiedlich formatiert. Diese Option ist standardmäßig deaktiviert.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Tag-Grundlagen](tag.md) für Entwickler.

Siehe [Tagging benutzergenerierter Inhalte](tag-ugc.md) (UGC) für Informationen zum Erstellen und Verwalten von Tags.
