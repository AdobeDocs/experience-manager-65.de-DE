---
title: Admin Consoles
description: Erfahren Sie, wie Sie die in Adobe Experience Manager verfügbaren Admin Consoles verwenden.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: d4de517e-50bc-4ca5-89b1-295d259fd5bb
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 5ef752af-d616-5b23-8312-06964e46b208
    internal-label: Administering
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 100%
---

# Admin Consoles{#admin-consoles}

Die Möglichkeit, über die Admin Consoles zur klassischen Benutzeroberfläche zu wechseln, ist standardmäßig deaktiviert. Daher werden die Popup-Symbole, die beim Bewegen des Mauszeigers über bestimmte Konsolensymbole angezeigt wurden und den Zugriff auf die klassische Benutzeroberfläche ermöglichten, nicht mehr angezeigt.

Jede Konsole, die unter `/libs/cq/core/content/nav` über eine klassische Benutzeroberfläche verfügt, kann einzeln wieder aktiviert werden. Die Option **Klassische Benutzeroberfläche** wird für das Konsolensymbol dann wieder angezeigt, wenn Sie den Mauszeiger darüber bewegen.

In diesem Beispiel aktivieren wir die klassische Benutzeroberfläche wieder für die Sites-Konsole.

1. Suchen Sie in CRXDE Lite nach dem Knoten für die Admin Console, für die Sie die klassische Benutzeroberfläche wieder aktivieren möchten. Sie finden ihn hier:

   `/libs/cq/core/content/nav`

   Beispiel

   [`https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](https://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Wählen Sie den entsprechenden Knoten der Konsole aus, für die Sie die klassische Benutzeroberfläche wieder aktivieren möchten. In diesem Beispiel aktivieren wir die klassische Benutzeroberfläche wieder für die Sites-Konsole.

   `/libs/cq/core/content/nav/sites`

1. Erstellen Sie eine Überlagerung mit der Option **Überlagerungsknoten**. Beispiel:

   * **Pfad**: `/apps/cq/core/content/nav/sites`
   * **Pfad für Überlagerung**: `/apps/`
   * **Knotentypen abgleichen**: aktiv (aktivieren Sie das Kontrollkästchen)

1. Fügen Sie dem überlagerten Knoten die folgende boolesche Eigenschaft hinzu:

   `enableDesktopOnly = {Boolean}true`

1. Die Option **Klassische Benutzeroberfläche** ist in der Admin Console wieder als Popover-Option verfügbar.

   ![Popover-Option „klassische Benutzeroberfläche“](assets/syui-01-2019-02-27-15-16-55.png)

Wiederholen Sie diese Schritte für jede Konsole, für die Sie den Zugriff auf die klassische Benutzeroberfläche erneut aktivieren möchten.
