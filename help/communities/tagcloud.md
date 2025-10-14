---
title: Verwenden von Social Tag Cloud
description: Erfahren Sie, wie Sie einer Seite eine Social-Tag-Cloud-Komponente hinzufügen, mit der angemeldete Community-Mitglieder schnell Trending-Themen identifizieren und getaggte Inhalte finden können.
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

# Verwenden von Social Tag Cloud {#using-social-tag-cloud}

## Einführung {#introduction}

Die `Social Tag Cloud`-Komponente hebt Tags hervor, die von Community-Mitgliedern beim Posten von Inhalten angewendet wurden. Es ist eine Möglichkeit, Trending-Themen zu identifizieren und es Website-Besuchern zu ermöglichen, getaggte Inhalte schnell zu finden.

Eine weitere Möglichkeit zur Ermittlung aktueller Trends finden Sie unter [Aktivitätstrends](trends.md).

Auf dieser Seite werden die Einstellungen des Dialogfelds &quot;`Social Tag Cloud`&quot; dokumentiert und das Benutzererlebnis beschrieben.

Detaillierte Informationen für Entwickler finden Sie unter [Tag Essentials](tag.md).

Informationen zum Erstellen und Verwalten von Tags sowie dazu, welchen Inhalten Tags zugewiesen wurden, finden Sie unter [Verwalten von Tags](../../help/sites-administering/tags.md).

## Hinzufügen einer Social-Tag-Cloud {#adding-a-social-tag-cloud}

Um einer Seite im Autorenmodus eine `Social Tag Cloud` Komponente hinzuzufügen, verwenden Sie den Komponenten-Browser, um `Communities / Social Tag Cloud` zu finden, und ziehen Sie ihn an eine Stelle auf einer Seite, an der die Tag-Cloud angezeigt werden soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](tag.md#essentials-for-client-side) enthalten sind, wird die `Social Tag Cloud` Komponente wie folgt angezeigt:

![social-tag](assets/social-tag.png)

## Konfigurieren von Social Tag Cloud {#configuring-social-tag-cloud}

Wählen Sie die platzierte `Social Tag Cloud` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

Geben Sie auf der Registerkarte **[!UICONTROL Social Tag]** Cloud) an, welche Tags angezeigt werden sollen. Wenn es sich bei den Tags um aktive Links handelt, geben Sie den Speicherort der Seite für Suchergebnisse an:

![social-tag-cloud](assets/social-tag-cloud.png)

* **[!UICONTROL Anzuzeigende Social-Tags]**
Identifizieren Sie, welche UGC-Tags angezeigt werden sollen. Die Pulldown-Optionen sind:

   * `From page and child pages`
   * `All tags`

  Der Standardwert ist `From page and child pages`, wobei sich „Seite“ auf die Einstellung **Seite** unten bezieht.

* **[!UICONTROL Seite]**

  (Erforderlich, wenn nicht `All tags)` Der Pfad zum benutzergenerierten Inhalt für eine Seite. Standard ist die aktuelle Seite, wenn sie leer gelassen wird.

* **[!UICONTROL Keine Einschränkung bezüglich Tags]**

  Wenn diese Option aktiviert ist, werden die Tags in der Tag-Cloud als unformatierter Text angezeigt. Wenn diese Option deaktiviert ist, werden die Tags als aktive Links angezeigt, die nach allen Inhalten suchen, denen dieses Tag zugewiesen ist. „Standard“ ist deaktiviert und erfordert die **[!UICONTROL „Suchergebnispfad]**.

* **[!UICONTROL Suchergebnispfad]**

  Der Pfad zu einer Seite, auf der eine `Search Result` platziert wurde, konfiguriert zum Verweisen auf benutzergenerierten Inhalt, der den durch die Einstellung „Seite **angegebenen benutzergenerierten** enthält.

## Anzeige der Social Tag Cloud ändern {#change-display-of-social-tag-cloud}

Um die Anzeige von **Social Tag Cloud** zu bearbeiten, wechseln Sie [Design-Modus](../../help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Social Tag Cloud`-Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Geben Sie auf der Registerkarte **[!UICONTROL Social Tag Cloud (Design]** an, wie Tags angezeigt werden sollen. Ein Tag kann ein einfaches Tag, ein einzelnes Wort im Standard-Namespace oder eine hierarchische Taxonomie sein:

![social-tag-cloud-design](assets/social-tag-cloud-design.png)

* **[!UICONTROL Vollständige Titelpfade anzeigen]**

  Wenn diese Option aktiviert ist, werden die Titel für die übergeordneten Tags und der Namespace für jedes angewendete Tag angezeigt.

  Zum Beispiel:

   * Geprüft: `Geometrixx Media: Gadgets / Cars`
   * Nicht aktiviert: `Cars`

  Bei einem einfachen -Tag gibt es keinen Unterschied.

  Standard ist deaktiviert.

* **[!UICONTROL Nur Leaf-Tags anzeigen]**

  Wenn diese Option aktiviert ist, werden nur angewendete Tags angezeigt, die keine anderen Tags enthalten.

  Beispiel: Bei einer Tag-ID von:

  `Geometrixx Media: Gadgets / Cars`

  Es gibt drei Tags, die angewendet werden können:

  `Geometrixx Media (the namespace)`, `Gadgets`, und `Cars`

   * Kontrollkästchen aktiviert: Nur `Cars` werden angezeigt, falls angewendet.
   * Deaktiviert: `Geometrixx Media`, `Gadgets` und `Cars` werden angezeigt, falls sie angewendet wurden.

  Ein einfaches Tag ist ein Leaf-Tag.

  Standard ist deaktiviert.

* **[!UICONTROL Vorlage verknüpfen]**

  Eine andere Vorlage als die Standardvorlage, die zum Anzeigen der Links in einer Tag-Cloud verwendet wird, wenn Links über das Dialogfeld zum Bearbeiten von Komponenten aktiviert werden.

* **[!UICONTROL Gleiche Größe für alle Tags]**

  Wenn diese Option aktiviert ist, sind alle Wörter in der Tag-Cloud gleich formatiert. Wenn diese Option deaktiviert ist, werden Wörter je nach Verwendung unterschiedlich formatiert. Standard ist deaktiviert.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Tag Essentials](tag.md) für Entwickler.

Informationen [&#x200B; Erstellen und Verwalten von Tags finden &#x200B;](tag-ugc.md) unter Tagging von benutzergenerierten Inhalten (UGC) .
