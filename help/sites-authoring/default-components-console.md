---
title: Komponentenkonsole
description: Mit der Komponentenkonsole können Sie alle für Ihre Instanz definierten Komponenten durchsuchen und wichtige Informationen zu den einzelnen Komponenten anzeigen.
exl-id: d79107b9-dfa4-4e80-870e-0b7ea72f0bc7
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 57%

---

# Komponentenkonsole{#components-console}

Mit der Komponentenkonsole können Sie alle für Ihre Instanz definierten Komponenten durchsuchen und wichtige Informationen zu den einzelnen Komponenten anzeigen.

Auf sie kann über **Tools** > **Allgemein** > **Komponenten** zugegriffen werden. In der Konsole sind Karten- und Listenansicht verfügbar. Da es keine Baumstruktur für Komponenten gibt, ist die Spaltenansicht nicht verfügbar.

![screen-shot_2019-03-05at113145](assets/screen-shot_2019-03-05at113145.png)

>[!NOTE]
>
>In der Komponentenkonsole werden alle im System vorhandenen Komponenten angezeigt. Im [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser) werden Komponenten angezeigt, die Autoren zur Verfügung stehen, und alle Komponentengruppen verborgen, die mit einem Punkt beginnen (`.`).

## Suchen {#searching}

Mit dem Symbol **Nur Inhalt** (oben links) können Sie den **Suchbereich** öffnen, um die Komponenten zu durchsuchen und/oder zu filtern:

![screen-shot_2019-03-05at113251](assets/screen-shot_2019-03-05at113251.png)

### Komponentendetails {#component-details}

Um Details zu einer bestimmten Komponente anzuzeigen, tippen/klicken Sie auf die gewünschte Ressource. Drei Registerkarten bieten:

* **Eigenschaften**

  ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

  In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
   * Anzeigen der [Symbol oder Abkürzung wurde definiert](/help/sites-developing/components-basics.md#component-icon-in-touch-ui) für die Komponente.

      * Wenn Sie auf die Quelle des Symbols klicken, gelangen Sie zu dieser Komponente.

   * Anzeigen der **Ressourcentyp** und **Resource Super Type** (sofern definiert) für die Komponente.

      * Wenn Sie auf den Ressourcen-Supertyp klicken, gelangen Sie zu dieser Komponente.

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

  Wenn der Entwickler [Dokumentation für die Komponente](/help/sites-developing/developing-components.md#documenting-your-component), wird sie im **Dokumentation** Registerkarte. Ist keine Dokumentation verfügbar, wird die Registerkarte **Dokumentation** nicht angezeigt.

  ![Dokumentation](assets/chlimage_1-171.png)
