---
title: Komponentenkonsole
description: Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind, und wichtige Informationen für jede Komponente anzuzeigen.
exl-id: d79107b9-dfa4-4e80-870e-0b7ea72f0bc7
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 100%
---
# Komponentenkonsole{#components-console}

Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind, und wichtige Informationen für jede Komponente anzuzeigen.

Auf sie kann über **Tools** > **Allgemein** > **Komponenten** zugegriffen werden. In der Konsole sind Karten- und Listenansicht verfügbar. Da es keine Baumstruktur für Komponenten gibt, ist die Spaltenansicht nicht verfügbar.

![screen-shot_2019-03-05at113145](assets/screen-shot_2019-03-05at113145.png)

>[!NOTE]
>
>In der Komponentenkonsole werden alle im System vorhandenen Komponenten angezeigt. Im [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen (`.`).

## Suchen {#searching}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern:

![screen-shot_2019-03-05at113251](assets/screen-shot_2019-03-05at113251.png)

### Komponentendetails {#component-details}

Um Details zu einer bestimmten Komponente anzuzeigen, klicken Sie auf die gewünschte Ressource. Drei Registerkarten bieten Folgendes:

* **Eigenschaften**

  ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

  In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

  * Ansehen der allgemeinen Eigenschaften der Komponente
  * Anzeigen, wie das [Symbol oder die Abkürzung für die Komponente definiert wurde](/help/sites-developing/components-basics.md#component-icon-in-touch-ui).

    * Wenn Sie auf die Quelle des Symbols klicken, gelangen Sie zu dieser Komponente.

  * Zeigen Sie den **Ressourcentyp** und **Ressourcen-Supertyp** (sofern definiert) für die Komponente an.

    * Durch Klicken auf den Ressourcen-Supertyp gelangen Sie zu dieser Komponente.

  >[!NOTE]
  >
  >Da `/apps` zur Laufzeit nicht bearbeitet werden kann, ist die Komponentenkonsole schreibgeschützt.

* **Richtlinien**

  ![Richtlinien](assets/chlimage_1-169.png)

* **Live-Nutzung**

  ![Live-Nutzung](assets/chlimage_1-170.png)

  >[!CAUTION]
  >
  >Aufgrund der Art der Informationen, die für diese Ansicht erfasst werden, kann es eine Weile dauern, bis sie zusammengestellt/angezeigt wird.

* **Dokumentation**

  Etwaige von Entwickelnden [für eine Komponente bereitgestellte Dokumentationen](/help/sites-developing/developing-components.md#documenting-your-component) werden auf der Registerkarte **Dokumentation** angezeigt. Ist keine Dokumentation verfügbar, wird die Registerkarte **Dokumentation** nicht angezeigt.

  ![Dokumentation](assets/chlimage_1-171.png)
