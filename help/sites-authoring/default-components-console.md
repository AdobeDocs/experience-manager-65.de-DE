---
title: Komponentenkonsole
description: Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind, und wichtige Informationen für jede Komponente anzuzeigen.
exl-id: d79107b9-dfa4-4e80-870e-0b7ea72f0bc7
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 93%

---

# Komponentenkonsole{#components-console}

Die Komponentenkonsole ermöglicht es Ihnen, alle Komponenten zu durchsuchen, die für Ihre Instanz definiert sind, und wichtige Informationen für jede Komponente anzuzeigen.

Der Zugriff erfolgt über **Tools >** **Allgemein >** **Komponenten**. In der Konsole sind Karten- und Listenansicht verfügbar. Da es keine Baumstruktur für Komponenten gibt, ist die Spaltenansicht nicht verfügbar.

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

   * Anzeigen des **Ressourcentyps** und **Ressourcen-Supertyps** (sofern definiert) für die Komponente.

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
