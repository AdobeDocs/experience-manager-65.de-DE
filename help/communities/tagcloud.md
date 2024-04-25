---
title: Verwenden der Social Tag Cloud
description: Erfahren Sie, wie Sie einer Seite eine Social-Tag-Cloud-Komponente hinzufügen, mit der angemeldete Community-Mitglieder schnell Trendthemen identifizieren und getaggte Inhalte finden können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 56af5362-78de-4308-8958-63a45e8573cc
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 5%

---

# Verwenden der Social Tag Cloud {#using-social-tag-cloud}

## Einführung {#introduction}

Die `Social Tag Cloud` -Komponente hebt Tags hervor, die von Community-Mitgliedern beim Posten von Inhalten angewendet werden. Es ermöglicht die Identifizierung von Trendthemen und die schnelle Auffindung von getaggten Inhalten durch Site-Besucher.

Eine weitere Möglichkeit zur Identifizierung aktueller Trends finden Sie unter [Aktivitätstrends](trends.md).

Diese Seite dokumentiert die `Social Tag Cloud` Einstellungen des Komponentendialogfelds und beschreibt das Benutzererlebnis.

Detaillierte Informationen für Entwickler finden Sie unter [Tag-Grundlagen](tag.md).

Informationen zum Erstellen und Verwalten von Tags sowie dazu, welchen Inhalten Tags zugewiesen wurden, finden Sie unter [Verwalten von Tags](../../help/sites-administering/tags.md).

## Hinzufügen einer Social Tag Cloud {#adding-a-social-tag-cloud}

So fügen Sie eine `Social Tag Cloud` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / Social Tag Cloud` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der die Tag-Cloud erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](tag.md#essentials-for-client-side) eingeschlossen sind, wird die `Social Tag Cloud` -Komponente angezeigt:

![social-tag](assets/social-tag.png)

## Konfigurieren der Social Tag Cloud {#configuring-social-tag-cloud}

Auswählen der platzierten `Social Tag Cloud` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

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

  Zum Beispiel:

   * Aktiviert: `Geometrixx Media: Gadgets / Cars`
   * deaktiviert: `Cars`

  Für ein einfaches Tag gibt es keinen Unterschied.

  Die Option Standard ist deaktiviert.

* **[!UICONTROL Nur Leaf-Tags anzeigen]**

  Wenn diese Option aktiviert ist, werden nur angewendete Tags angezeigt, die keine anderen Tags enthalten.

  Beispielsweise bei der TagID von:

  `Geometrixx Media: Gadgets / Cars`

  Es gibt drei Tags, die angewendet werden können:

  `Geometrixx Media (the namespace)`, `Gadgets`, und `Cars`

   * Aktiviert: nur `Cars` angezeigt werden, falls angewendet.
   * deaktiviert: `Geometrixx Media`, `Gadgets`, und `Cars` angezeigt werden, falls angewendet.

  Ein einfaches Tag ist ein Leaf-Tag.

  Die Option Standard ist deaktiviert.

* **[!UICONTROL Link-Vorlage]**

  Eine andere Vorlage als die Standardvorlage, mit der die Links in einer Tag-Cloud angezeigt werden, wenn Links über das Dialogfeld &quot;Komponentenbearbeitung&quot;aktiviert werden.

* **[!UICONTROL Gleiche Größe für alle Tags]**

  Wenn diese Option aktiviert ist, werden alle Wörter in der Tag-Cloud denselben Stil zugewiesen. Wenn diese Option deaktiviert ist, werden Wörter je nach Verwendung unterschiedlich formatiert. Die Option Standard ist deaktiviert.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Tag-Grundlagen](tag.md) -Seite für Entwickler.

Siehe [Tagging benutzergenerierter Inhalte](tag-ugc.md) (UGC) für Informationen zum Erstellen und Verwalten von Tags.
