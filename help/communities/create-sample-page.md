---
title: Erstellen einer Beispielseite
description: Erfahren Sie, wie Sie eine Community-Site-Vorlage erstellen, die nur die Seitenfunktion enthält, die Ihnen beim Erstellen einer einfachen Community-Site helfen kann.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: developing
exl-id: d66fc1ff-a669-4a2c-b45a-093060facd97
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# Erstellen einer Beispielseite {#create-a-sample-page}

Ab AEM 6.1 Communities besteht der einfachste Weg, eine Beispielseite zu erstellen, darin, eine einfache Community-Site zu erstellen, die einfach aus einer Seitenfunktion besteht.

Dazu gehört eine parsys-Komponente, mit der Sie [Komponenten für das Authoring aktivieren](basics.md#accessing-communities-components).

Eine weitere Möglichkeit, mit Beispielkomponenten zu untersuchen, besteht darin, die Funktionen zu verwenden, die im [Community-Komponentenhandbuch](components-guide.md) vorgestellt werden.

## Erstellen einer Community-Site {#create-a-community-site}

Dies ähnelt dem Erstellen einer Site, wie unter [Erste Schritte mit AEM Communities](getting-started.md) beschrieben.

Der Hauptunterschied besteht darin, dass dieses Tutorial eine Community-Site-Vorlage erstellt, die nur die [Seitenfunktion](functions.md#page-function) zum Erstellen einer einfachen Community-Site enthält. Es tut dies kostenlos von anderen Funktionen (außer den vorverkabelten grundlegenden Funktionen für alle Community-Sites).

### Erstellen einer neuen Site-Vorlage {#create-new-site-template}

Erstellen Sie zunächst eine einfache [Community-Site-Vorlage](sites.md).

Wählen Sie in der globalen Navigation einer Autoreninstanz die Option **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Site Templates]**.

![create-site-template](assets/create-site-template1.png)

* Klicken Sie auf `Create button`
* GRUNDLEGENDE INFORMATIONEN

   * `Name`: Einzelseitenvorlage
   * `Description`: Eine aus einer einzelnen Seitenfunktion bestehende Vorlage.
   * Klicken Sie auf `Enabled`

![site-template-editor](assets/site-template-editor.png)

* STRUKTUR

   * Ziehen Sie eine `Page` Funktion in den Vorlagengenerator
   * Für Details zur Konfigurationsfunktion geben Sie Folgendes ein

      * `Title`: einzelne Seite
      * `URL`: Seite

![site-template-editor-structure](assets/site-template-editor1.png)

* **`Save`** für die Konfiguration auswählen
* **`Save`** für die Site-Vorlage auswählen

### Neue Community-Site erstellen {#create-new-community-site}

Erstellen Sie jetzt eine Community-Site basierend auf der einfachen Site-Vorlage.

Wählen Sie nach dem Erstellen der Site-Vorlage in der globalen Navigation **[!UICONTROL Communities > Sites]**.

![create-community-site](assets/create-community-site1.png)

* **`Create`** auswählen

* Schritt `1 - Site Template`

   * `Title`: Einfache Community-Site
   * `Description`: Eine Community-Site, die aus einer einzigen Seite zum Experimentieren besteht.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: Beispiel

      * URL = http://localhost:4502/content/sites/sample

      * `Template`: `Single Page Template` auswählen

     ![create-community-site-template](assets/create-community-site-template.png)

* Klicken Sie auf `Next`
* Schritt `2 - Design`

   * Beliebiges Design auswählen

* Klicken Sie auf `Next`
* Klicken Sie auf `Next`

  (Alle Standardeinstellungen akzeptieren)

* Klicken Sie auf `Create`

  ![create-community-site](assets/create-community-site.png)

## Publish die Site {#publish-the-site}

![publish-site](assets/publish-site.png)

Wählen Sie in der [Community-Sites](sites-console.md)Konsole das Symbol Veröffentlichen aus, um die Site zu veröffentlichen, standardmäßig in http://localhost:4503.

## Öffnen Sie die Site in der Autoreninstanz im Bearbeitungsmodus {#open-the-site-on-author-in-edit-mode}

![open-site](assets/open-site.png)

Wählen Sie das Symbol Site öffnen aus, damit Sie die Site im Bearbeitungsmodus anzeigen können.

Die URL lautet [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![author-site](assets/author-site.png)

Auf der einfachen Startseite können Sie sehen, was durch die Community-Funktionen und -Vorlagen vorverkabelt ist, und mit dem Hinzufügen und Konfigurieren von Community-Komponenten spielen.

## Site auf Publish anzeigen {#view-site-on-publish}

Öffnen Sie die Seite nach dem Veröffentlichen auf der [Veröffentlichungsinstanz](http://localhost:4503/content/sites/sample/en.html) um mit den Funktionen als anonymer Site-Besucher, angemeldeter Mitglied oder Administrator zu experimentieren. Der Link Administration , der in der Autorenumgebung sichtbar ist, wird in der Veröffentlichungsumgebung nur angezeigt, wenn sich ein Administrator anmeldet.
