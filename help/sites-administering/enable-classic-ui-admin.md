---
title: Admin Consoles
description: Erfahren Sie, wie Sie die in AEM verfügbaren Admin Consolen verwenden.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: d4de517e-50bc-4ca5-89b1-295d259fd5bb
source-git-commit: 260f71acd330167572d817fdf145a018b09cbc65
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 38%

---


# Admin Consoles{#admin-consoles}

Standardmäßig wurde die Möglichkeit deaktiviert, über die Admin Console zur klassischen Benutzeroberfläche zu wechseln. Daher werden die Popup-Symbole, die beim Bewegen des Mauszeigers über bestimmte Konsolensymbole angezeigt wurden und den Zugriff auf die klassische Benutzeroberfläche ermöglichen, nicht mehr angezeigt.

Jede Konsole, die unter `/libs/cq/core/content/nav` über eine klassische Benutzeroberfläche verfügt, kann einzeln wieder aktiviert werden. Die Option **Klassische Benutzeroberfläche** wird für das Konsolensymbol dann wieder angezeigt, wenn Sie den Mauszeiger darauf bewegen.

In diesem Beispiel aktivieren wir die klassische Benutzeroberfläche wieder für die Sites-Konsole.

1. Suchen Sie mithilfe von CRXDE Lite den Knoten, der der Admin Console entspricht, für die Sie die klassische Benutzeroberfläche erneut aktivieren möchten. Sie finden ihn hier:

   `/libs/cq/core/content/nav`

   Beispiel

   [`https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Wählen Sie den Knoten aus, der der Konsole entspricht, für die Sie die klassische Benutzeroberfläche erneut aktivieren möchten. In unserem Beispiel wird die klassische Benutzeroberfläche für die Sites-Konsole erneut aktiviert.

   `/libs/cq/core/content/nav/sites`

1. Erstellen Sie eine Überlagerung mit der Option **Überlagerungsknoten**. Beispiel:

   * **Pfad**: `/apps/cq/core/content/nav/sites`
   * **Pfad für Überlagerung**: `/apps/`
   * **Knotentypen abgleichen**: active (aktivieren Sie das Kontrollkästchen)

1. Fügen Sie dem überlagerten Knoten die folgende boolesche Eigenschaft hinzu:

   `enableDesktopOnly = {Boolean}true`

1. Die **Klassische Benutzeroberfläche** ist in der Admin Console wieder als Popover-Option verfügbar.

   ![Popupoption &quot;klassische Benutzeroberfläche&quot;](assets/syui-01-2019-02-27-15-16-55.png)

Wiederholen Sie diese Schritte für jede Konsole, für die Sie den Zugriff auf die klassische Benutzeroberfläche erneut aktivieren möchten.
