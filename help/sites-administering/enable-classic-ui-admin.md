---
title: Admin Consoles
seo-title: Admin Consolen
description: Es wird beschrieben, wie Sie die in AEM verfügbaren Admin Consoles verwenden.
seo-description: Es wird beschrieben, wie Sie die in AEM verfügbaren Admin Consoles verwenden.
uuid: 82ab5267-2f2a-4772-85d5-678d883a0294
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6dbe82c2-7a25-49ab-a980-3635f0344817
docset: aem65
exl-id: d4de517e-50bc-4ca5-89b1-295d259fd5bb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 69%

---

# Admin Consolen{#admin-consoles}

In der Standardeinstellung ist die Option zum Wechseln zur klassischen Benutzeroberfläche über die Admin Consoles nun deaktiviert. Aus diesem Grund werden die Pop-up-Symbole, die beim Bewegen des Mauszeigers auf bestimmte Konsolensymbole angezeigt wurden, um den Zugriff auf die klassische Benutzeroberfläche zu ermöglichen, nicht mehr eingeblendet.

Jede Konsole, die über eine klassische Benutzeroberflächenversion in `/libs/cq/core/content/nav` verfügt, kann einzeln wieder aktiviert werden, sodass die Option **Klassische Benutzeroberfläche** erneut über das Konsolensymbol angezeigt wird, wenn die Maus darauf bewegt wird.

In diesem Beispiel aktivieren wir die klassische Benutzeroberfläche wieder für die Sites-Konsole.

1. Suchen Sie mithilfe von CRXDE Lite den Knoten, der der Admin Console entspricht, für die Sie die klassische Benutzeroberfläche erneut aktivieren möchten. Sie finden ihn hier:

   `/libs/cq/core/content/nav`

   Beispiel

   [ `https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Wählen Sie den entsprechenden Knoten der Konsole aus, für die Sie die klassische Benutzeroberfläche wieder aktivieren möchten. Im Beispiel aktivieren wir die klassische Benutzeroberfläche für die Sites-Konsole.

   `/libs/cq/core/content/nav/sites`

1. Erstellen Sie eine Überlagerung mit der Option **Überlagerungsknoten** . Beispiel:

   * **Pfad**: `/apps/cq/core/content/nav/sites`
   * **Pfad für Überlagerung**: `/apps/`
   * **Übereinstimmungstypen abgleichen**: aktiv (Kontrollkästchen aktivieren)

1. Fügen Sie dem überlagerten Knoten die folgende boolesche Eigenschaft hinzu:

   `enableDesktopOnly = {Boolean}true`

1. Die Option **Klassische Benutzeroberfläche** ist in der Admin Console jetzt wieder als Popover-Option verfügbar.

   ![](assets/syui-01-2019-02-27-15-16-55.png)

Wiederholen Sie diese Schritte für jede Konsole, für die Sie den Zugriff auf die klassische Benutzeroberfläche wieder aktivieren möchten.
