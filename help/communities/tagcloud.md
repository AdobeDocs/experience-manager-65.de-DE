---
title: Verwenden der Social Tag Cloud
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
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 9%

---

# Verwenden der Social Tag Cloud {#using-social-tag-cloud}

## Einführung {#introduction}

Die `Social Tag Cloud` -Komponente hebt Tags hervor, die von Community-Mitgliedern beim Posten von Inhalten angewendet werden. Es ermöglicht die Identifizierung von Trendthemen und die schnelle Suche nach getaggten Inhalten durch Site-Besucher.

Weitere Möglichkeiten zur Identifizierung aktueller Trends finden Sie unter [Aktivitätstrends](trends.md).

Diese Seite dokumentiert die `Social Tag Cloud` Einstellungen des Komponentendialogfelds und beschreibt das Benutzererlebnis.

Detaillierte Informationen für Entwickler finden Sie unter [Tag-Grundlagen](tag.md).

Informationen zur Erstellung und Verwaltung von Tags sowie dazu, auf welche Inhalte Tags angewendet wurden, finden Sie unter [Verwalten von Tags](../../help/sites-administering/tags.md).

## Hinzufügen einer Social Tag Cloud {#adding-a-social-tag-cloud}

So fügen Sie eine `Social Tag Cloud` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Social Tag Cloud` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der die Tag-Cloud erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](tag.md#essentials-for-client-side) eingeschlossen sind, wird die `Social Tag Cloud` wird angezeigt:

![social-tag](assets/social-tag.png)

## Konfigurieren der Social Tag Cloud {#configuring-social-tag-cloud}

Wählen Sie die platzierte `Social Tag Cloud` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **[!UICONTROL Social Tag Cloud]** angeben, welche Tags angezeigt werden sollen, und, wenn es sich bei den Tags um aktive Links handelt, den Speicherort der Seite für Suchergebnisse angeben:

![social-tag-cloud](assets/social-tag-cloud.png)

* **[!UICONTROL Anzuzeigende Social Tags]**
Ermitteln Sie, welche UGC-Tags angezeigt werden sollen. Die Pulldown-Optionen sind:

   * `From page and child pages`
   * `All tags`

  Der Standardwert ist `From page and child pages`, wobei &quot;Seite&quot;auf die **Seite** unten.

* **[!UICONTROL Seite]**

  (Erforderlich, falls nicht erforderlich `All tags)` Der Pfad zum benutzergenerierten Inhalt einer Seite. Standardmäßig wird die aktuelle Seite angezeigt, wenn sie leer gelassen wird.

* **[!UICONTROL Keine Einschränkung bezüglich Tags]**

  Wenn diese Option aktiviert ist, werden die Tags in der Tag-Cloud als Nur-Text angezeigt. Wenn diese Option deaktiviert ist, werden die Tags als aktive Links angezeigt, die nach allen Inhalten suchen, auf die dieses Tag angewendet wird. Die Standardeinstellung ist deaktiviert und erfordert die **[!UICONTROL Suchergebnispfad]** festgelegt werden.

* **[!UICONTROL Suchergebnispfad]**

  Der Pfad zu einer Seite, auf der ein `Search Result` -Komponente platziert wurde, die so konfiguriert ist, dass sie auf UGC verweist, das den durch die **Seite** -Einstellung.

## Anzeige der Social Tag Cloud ändern {#change-display-of-social-tag-cloud}

So bearbeiten Sie die Anzeige der **Social Tag Cloud**, eingeben [Designmodus](../../help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Social Tag Cloud` -Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Verwenden der **[!UICONTROL Social Tag Cloud (Design)]** Registerkarte angeben, wie Tags angezeigt werden. Ein Tag kann ein einfaches Tag, ein einzelnes Wort im Standard-Namespace oder eine hierarchische Taxonomie sein:

![social-tag-cloud-design](assets/social-tag-cloud-design.png)

* **[!UICONTROL Vollständige Titelpfade anzeigen]**

  Wenn diese Option aktiviert ist, zeigt die Titel für die übergeordneten Tags und den Namespace für jedes angewendete Tag an.

  Beispiel:

   * Aktiviert: `Geometrixx Media: Gadgets / Cars`
   * Deaktiviert: `Cars`

  Für ein einfaches Tag gibt es keinen Unterschied.

  Die Option Standard ist deaktiviert.

* **[!UICONTROL Nur Leaf-Tags anzeigen]**

  Wenn diese Option aktiviert ist, werden nur angewendete Tags angezeigt, die keine anderen Tags enthalten.

  Beispielsweise bei der TagID von:

  `Geometrixx Media: Gadgets / Cars`

  Es gibt 3 Tags, die angewendet werden können:

  `Geometrixx Media (the namespace)`, `Gadgets`, und `Cars`

   * Aktiviert: Nur `Cars` wird angezeigt, falls angewendet.
   * deaktiviert: `Geometrixx Media` und `Gadgets`sowie `Cars` wird angezeigt, falls angewendet.

  Ein einfaches Tag ist ein Leaf-Tag.

  Die Option Standard ist deaktiviert.

* **[!UICONTROL Verknüpfungsvorlage]**

  Eine andere Vorlage als die Standardvorlage, mit der die Links in einer Tag-Cloud angezeigt werden, wenn Links über das Dialogfeld &quot;Komponentenbearbeitung&quot;aktiviert werden.

* **[!UICONTROL Gleiche Größe für alle Tags]**

  Wenn diese Option aktiviert ist, werden alle Wörter in der Tag-Cloud denselben Stil zugewiesen. Wenn diese Option deaktiviert ist, werden Wörter je nach Verwendung unterschiedlich formatiert. Die Option Standard ist deaktiviert.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Tag-Grundlagen](tag.md) für Entwickler.

Siehe [Tagging benutzergenerierter Inhalte](tag-ugc.md) (UGC) für Informationen zum Erstellen und Verwalten von Tags.
