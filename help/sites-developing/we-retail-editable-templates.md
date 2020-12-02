---
title: Testen bearbeitbarer Vorlagen in We.Retail
seo-title: Testen bearbeitbarer Vorlagen in We.Retail
description: 'null'
seo-description: 'null'
uuid: 0d4b97cb-efcc-4312-a783-eae3ecd6f889
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 3cc8ac23-98ff-449f-bd76-1203c7cbbed7
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 86%

---


# Testen bearbeitbarer Vorlagen in We.Retail{#trying-out-editable-templates-in-we-retail}

Mit bearbeitbaren Vorlagen können nicht mehr nur Entwickler Vorlagen erstellen und verwalten. Ein erfahrener Benutzer, ein so genannter Vorlagenautor, kann nun Vorlagen erstellen. Entwickler müssen weiterhin die Umgebung einrichten, Clientbibliotheken erstellen und die zu verwendenden Komponenten erstellen. Sobald diese Grundlagen vorhanden sind, hat der Vorlagenautor jedoch die Flexibilität, Vorlagen ohne Entwicklungsprojekt zu erstellen und zu konfigurieren.

Alle Seiten in We.Retail basieren auf bearbeitbaren Vorlagen, sodass auch Benutzer, die keine Entwickler sind, die Vorlagen anpassen können.

## Testen {#trying-it-out}

1. Bearbeiten Sie die Seite „Ausrüstung“ der Sprach-Master-Verzweigung.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/equipment.html

1. Beachten Sie, dass die Modusauswahl keinen Designmodus mehr aufweist. Alle Seiten für We.Retail basieren auf bearbeitbaren Vorlagen. Um das Design bearbeitbarer Vorlagen zu ändern, müssen diese im Vorlagen-Editor bearbeitet werden.
1. Wählen Sie im Menü **Seiteninformationen** **Vorlage bearbeiten** aus.
1. Sie bearbeiten nun die Vorlage der Hero-Seite.

   Der Strukturmodus der Seite ermöglicht es Ihnen, die Struktur der Vorlage zu ändern. Dazu gehören beispielsweise die Komponenten, die im Layout-Container zulässig sind.

   ![chlimage_1-138](assets/chlimage_1-138.png)

1. Konfigurieren Sie die Richtlinien für den Layout-Container, um festzulegen, welche Komponenten im Container zulässig sind.

   Richtlinien sind das Äquivalent zu Designkonfigurationen.

   ![chlimage_1-139](assets/chlimage_1-139.png)

1. Im Designdialogfeld des Layout-Containers können Sie Folgendes:

   * Eine bestehende Richtlinie auswählen oder eine neue Richtlinie für den Container erstellen
   * Auswählen, welche Komponenten im Container zulässig sind
   * Die Standardkomponenten definieren, die platziert werden sollen, wenn ein Asset per Drag-and-Drop in den Container verschoben wird

   ![chlimage_1-140](assets/chlimage_1-140.png)

1. Zurück im Vorlagen-Editor können Sie die Richtlinie für die Textkomponente innerhalb des Layout-Containers bearbeiten.

   Dies ermöglicht Ihnen Folgendes:

   * Eine bestehende Richtlinie auswählen oder eine neue Richtlinie für den Container erstellen
   * Die Funktionen definieren, die den Seitenautoren bei der Verwendung dieser Komponente zur Verfügung stehen, beispielsweise

      * Zulässige Einfügequellen
      * Formatierungsoptionen
      * Zulässige Absatzformate
      * Zulässige Sonderzeichen

   Viele Komponenten, die auf den Kernkomponenten basieren, ermöglichen die Konfiguration von Optionen auf Komponentenebene über die bearbeitbaren Vorlagen, wodurch die Notwendigkeit der Anpassung durch die Entwickler entfällt.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Zurück im Vorlagen-Editor können Sie mit der Modusauswahl in den Modus **Anfänglicher Inhalt** wechseln, um festzulegen, welcher Inhalt auf der Seite benötigt wird.

   Der **Layout-Modus** kann wie auf einer normalen Seite verwendet werden, um das Layout für die Vorlage zu definieren.

## Weitere Informationen  {#more-information}

Weitere Informationen zu bearbeitbaren Vorlagen finden Sie im Authoring-Dokument [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md) oder auf der Developer Dokument-Seite [Vorlagen - Bearbeitbar](/help/sites-developing/page-templates-editable.md).

Sie können sich darüber hinaus eingehender mit [Kernkomponenten](/help/sites-developing/we-retail-core-components.md) befassen. Eine technische Übersicht über die Funktionen der Kernkomponenten und des Developer-Dokuments [Entwickeln von Kernkomponenten](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) finden Sie im Authoring-Dokument [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html).

