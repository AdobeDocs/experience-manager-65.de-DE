---
title: Beispielseite erstellen
seo-title: Beispielseite erstellen
description: Erstellen einer Beispiel-Community-Site
seo-description: Erstellen einer Beispiel-Community-Site
uuid: 04a8f027-b7d8-493a-a9bd-5c4a6715d754
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: developing
discoiquuid: a03145f7-6697-4797-b73e-6f8d241ce469
translation-type: tm+mt
source-git-commit: 824ddd48e4680eed1d4612c6ad450a8f1bc68e7c
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 2%

---


# Beispielseite {#create-a-sample-page} erstellen

Ab AEM 6.1 Communities ist es am einfachsten, eine Beispielseite zu erstellen, eine einfache Community-Site zu erstellen, die aus einer Seitenfunktion besteht.

Dazu gehört eine parsys-Komponente, damit Sie [Komponenten für das Authoring](basics.md#accessing-communities-components) aktivieren können.

Eine weitere Möglichkeit, Beispielkomponenten zu entdecken, besteht darin, die Funktionen zu verwenden, die im [Community-Komponentenleitfaden](components-guide.md) beschrieben sind.

## Community-Site {#create-a-community-site} erstellen

Dies ist der Erstellung einer neuen Site sehr ähnlich, die unter [Erste Schritte mit AEM Communities](getting-started.md) beschrieben wird.

Der Hauptunterschied ist, dass dieses Tutorial eine neue Community-Site-Vorlage erstellt, die nur die Funktion [Seite](functions.md#page-function) enthält, um eine einfache Community-Site zu erstellen, die frei von anderen Funktionen ist (außer den vorab verkabelten Funktionen, die für alle Community-Sites grundlegend sind).

### Neue Site-Vorlage erstellen {#create-new-site-template}

Erstellen Sie zunächst eine einfache [Community-Site-Vorlage](sites.md).

Wählen Sie in der globalen Navigation in einer Autoreninstanz **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Site-Vorlagen]**.

![create-site-template](assets/create-site-template1.png)

* Wählen Sie nun eine der folgenden Optionen aus `Create button`
* GRUNDINFORMATIONEN

   * `Name`: Einzelseitenvorlage
   * `Description`: Eine Vorlage, die aus einer einzelnen Seitenfunktion besteht.
   * Wählen Sie nun eine der folgenden Optionen aus `Enabled`

![site-template-editor](assets/site-template-editor.png)

* STRUKTUR

   * Ziehen Sie eine `Page`-Funktion in den Vorlagenaufbau
   * Geben Sie für Konfigurationsfunktionsdetails

      * `Title`: Einzelseite
      * `URL`: page

![site-template-editor-structure](assets/site-template-editor1.png)

* Wählen Sie **`Save`** für die Konfiguration
* Wählen Sie **`Save`** für die Sitevorlage

### Neue Community-Site {#create-new-community-site} erstellen

Erstellen Sie jetzt eine neue Community-Site basierend auf der einfachen Site-Vorlage.

Wählen Sie nach dem Erstellen der Site-Vorlage in der globalen Navigation **[!UICONTROL Communities > Sites]**.

![create-community-site](assets/create-community-site1.png)

* Symbol **`Create`** auswählen

* Schritt `1 - Site Template`

   * `Title`: Einfache Community-Site
   * `Description`: Eine Community-Site, die aus einer einzelnen Seite zum Experimentieren besteht.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: Beispiel

      * url = http://localhost:4502/content/sites/sample

      * `Template`: auswählen  `Single Page Template`

      ![create-community-site-template](assets/create-community-site-template.png)


* Wählen Sie nun eine der folgenden Optionen aus `Next`
* Schritt `2 - Design`

   * Auswählen eines Entwurfs

* Wählen Sie nun eine der folgenden Optionen aus `Next`
* Wählen Sie nun eine der folgenden Optionen aus `Next`

   (Alle Standardeinstellungen akzeptieren)

* Wählen Sie nun eine der folgenden Optionen aus `Create`

   ![create-community-site](assets/create-community-site.png)

## Veröffentlichen der Site {#publish-the-site}

![publish-site](assets/publish-site.png)

Wählen Sie in der [Community-Sites-Konsole](sites-console.md) das Symbol zum Veröffentlichen aus, um die Site zu veröffentlichen. Standardmäßig lautet das Symbol http://localhost:4503.

## Öffnen Sie die Site im Autorenmodus im Bearbeitungsmodus {#open-the-site-on-author-in-edit-mode}

![open-site](assets/open-site.png)

Wählen Sie das Symbol zum Öffnen der Site aus, um die Site im Bearbeitungsmodus Ansicht.

Die URL lautet [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![author-site](assets/author-site.png)

Auf der einfachen Startseite ist es möglich, zu sehen, was durch die Community-Funktionen und -Vorlagen vorverkabelt ist, und mit dem Hinzufügen und Konfigurieren von Community-Komponenten zu spielen.

## Ansicht-Site bei Veröffentlichung {#view-site-on-publish}

Nach dem Veröffentlichen der Seite öffnen Sie die Seite in der [Veröffentlichungsinstanz](http://localhost:4503/content/sites/sample/en.html), um mit den Funktionen als anonymer Site-Besucher zu experimentieren, als angemeldeter Mitglied oder als Administrator angemeldet zu sein. Der in der Autorenumgebung angezeigte Link &quot;Administration&quot;wird in der Umgebung &quot;Veröffentlichen&quot;nur angezeigt, wenn sich ein Administrator anmeldet.
