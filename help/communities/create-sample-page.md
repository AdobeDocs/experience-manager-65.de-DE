---
title: Erstellen einer Beispielseite
description: Erfahren Sie, wie Sie eine Community-Site-Vorlage erstellen, die nur die Funktion Seite enthält, mit der Sie eine einfache Community-Site erstellen können.
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

Ab AEM 6.1 Communities ist es am einfachsten, eine Beispielseite zu erstellen, indem eine einfache Community-Site erstellt wird, die aus einer Page-Funktion besteht.

Dazu gehört eine parsys-Komponente, sodass Sie [Komponenten für die Bearbeitung aktivieren](basics.md#accessing-communities-components) können.

Eine weitere Möglichkeit zur Erforschung mit Beispielkomponenten besteht darin, die im [Leitfaden zu Community-Komponenten](components-guide.md) dargestellten Funktionen zu verwenden.

## Community-Site erstellen {#create-a-community-site}

Dies ähnelt dem Erstellen einer Website, die unter [Erste Schritte mit AEM Communities](getting-started.md) beschrieben wird.

Der Hauptunterschied besteht darin, dass dieses Tutorial eine Community-Site-Vorlage erstellt, die nur die [Seitenfunktion](functions.md#page-function) enthält, um eine einfache Community-Site zu erstellen. Dies erfolgt frei von anderen Funktionen (außer den vorverkabelten Funktionen, die für alle Community-Sites grundlegend sind).

### Neue Site-Vorlage erstellen {#create-new-site-template}

Erstellen Sie zunächst eine einfache [Community-Site-Vorlage](sites.md).

Wählen Sie in der globalen Navigation einer Autoreninstanz **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Site-Vorlagen]** aus.

![create-site-template](assets/create-site-template1.png)

* Klicken Sie auf `Create button`
* GRUNDLEGENDE INFORMATIONEN

   * `Name`: Einzelseitenvorlage
   * `Description`: Eine Vorlage, die aus einer einzelnen Seitenfunktion besteht.
   * Klicken Sie auf `Enabled`

![site-template-editor](assets/site-template-editor.png)

* STRUKTUR

   * Ziehen Sie eine `Page` -Funktion in den Vorlagenaufbau
   * Geben Sie für Details zur Konfigurationsfunktion ein

      * `Title`: Einzelseite
      * `URL`: page

![site-template-editor-structure](assets/site-template-editor1.png)

* Wählen Sie **`Save`** für die Konfiguration aus
* Wählen Sie **`Save`** für die Site-Vorlage aus

### Neue Community-Site erstellen {#create-new-community-site}

Erstellen Sie nun eine Community-Site basierend auf der einfachen Site-Vorlage.

Wählen Sie nach der Erstellung der Site-Vorlage in der globalen Navigation **[!UICONTROL Communities > Sites]** aus.

![create-community-site](assets/create-community-site1.png)

* Symbol **`Create`** auswählen

* Schritt `1 - Site Template`

   * `Title`: Einfache Community-Site
   * `Description`: Eine Community-Site, die aus einer einzelnen Seite zum Experimentieren besteht.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: sample

      * url = http://localhost:4502/content/sites/sample

      * `Template`: `Single Page Template` auswählen

     ![create-community-site-template](assets/create-community-site-template.png)

* Klicken Sie auf `Next`
* Schritt `2 - Design`

   * Entwurf auswählen

* Klicken Sie auf `Next`
* Klicken Sie auf `Next`

  (Alle Standardeinstellungen akzeptieren)

* Klicken Sie auf `Create`

  ![create-community-site](assets/create-community-site.png)

## Publish der Site {#publish-the-site}

![publish-site](assets/publish-site.png)

Wählen Sie in der Konsole [Community-Sites-Konsole](sites-console.md) das Veröffentlichungssymbol aus, um die Site zu veröffentlichen. Standardmäßig ist dies http://localhost:4503.

## Öffnen Sie die Site im Autorenmodus im Bearbeitungsmodus. {#open-the-site-on-author-in-edit-mode}

![open-site](assets/open-site.png)

Wählen Sie das Symbol zum Öffnen der Site aus, damit Sie die Site im Bearbeitungsmodus anzeigen können.

Die URL lautet [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![author-site](assets/author-site.png)

Auf der einfachen Startseite können Sie sehen, was über die Community-Funktionen und -Vorlagen vorab verkabelt ist, und mit dem Hinzufügen und Konfigurieren von Community-Komponenten spielen.

## Website in Publish anzeigen {#view-site-on-publish}

Öffnen Sie nach dem Veröffentlichen der Seite die Seite in der [Veröffentlichungsinstanz](http://localhost:4503/content/sites/sample/en.html) , um mit den Funktionen als anonymer Site-Besucher, angemeldetes Mitglied oder Administrator zu experimentieren. Der in der Autorenumgebung angezeigte Link Administration wird nur dann in der Veröffentlichungsumgebung angezeigt, wenn sich ein Administrator anmeldet.
