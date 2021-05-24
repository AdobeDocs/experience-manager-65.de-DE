---
title: Komponentenkonsole
seo-title: Komponentenkonsole
description: Komponentenkonsole
seo-description: 'null'
uuid: a4e34d81-7875-4e26-8b48-4473e2905c37
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: b657f95d-7be3-4409-a31b-d47fb2bfa550
docset: aem65
exl-id: d79107b9-dfa4-4e80-870e-0b7ea72f0bc7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 97%

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

Um weitere Einzelheiten zu einer bestimmten Komponente anzuzeigen, tippen/klicken Sie auf die gewünschte Ressource. Die drei Registerkarten bieten:

* **Eigenschaften**

   ![screen_shot_2018-03-27at165847](assets/screen_shot_2018-03-27at165847.png)

   In der Registerkarte „Eigenschaften“ haben Sie folgende Möglichkeiten:

   * Ansehen der allgemeinen Eigenschaften der Komponente
   * Ansehen, wie das [Symbol oder die Abkürzung für die Komponente definiert wurde](/help/sites-developing/components-basics.md#component-icon-in-touch-ui)

      * Durch Klicken auf die Symbolquelle gelangen Sie zu dieser Komponente.
   * Ansehen des **Ressourcentyps** und des **Ressourcen-Supertyps** (sofern definiert) für die Komponente

      * Durch Klicken auf den Ressourcen-Supertyp gelangen Sie zu dieser Komponente.
   >[!NOTE]
   >
   >Da `/apps` zur Laufzeit nicht bearbeitet werden kann, ist die Komponentenkonsole schreibgeschützt.

* **Richtlinien**

   ![chlimage_1-169](assets/chlimage_1-169.png)

* **Live-Nutzung**

   ![chlimage_1-170](assets/chlimage_1-170.png)

   >[!CAUTION]
   >
   >Aufgrund der Art der Informationen, die für diese Ansicht erfasst werden, kann es eine Weile dauern, bis sie zusammengestellt/angezeigt wird. 

* **Dokumentation**

   Etwaige vom Entwickler [für eine Komponente bereitgestellte Dokumentation](/help/sites-developing/developing-components.md#documenting-your-component) wird auf der Registerkarte **Dokumentation** angezeigt. Ist keine Dokumentation verfügbar, wird die Registerkarte **Dokumentation** nicht angezeigt.

   ![chlimage_1-171](assets/chlimage_1-171.png)
