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
source-git-commit: e8d8bf89971d3d9d5ec150308dda247aa53c77bb

---


# Create a Sample Page {#create-a-sample-page}

Ab AEM 6.1 Communities besteht die einfachste Möglichkeit, eine Beispielseite zu erstellen, darin, eine einfache Community-Site zu erstellen, die aus einer Seitenfunktion besteht.

Dazu gehört eine parsys-Komponente, damit Sie Komponenten für das Authoring [aktivieren können](basics.md#accessing-communities-components).

Eine weitere Möglichkeit zur Untersuchung von Beispielkomponenten ist die Verwendung der im [Community-Komponentenleitfaden](components-guide.md)dargestellten Funktionen.

## Community-Site erstellen {#create-a-community-site}

Dies ist der Erstellung einer neuen Site sehr ähnlich, die unter [Erste Schritte mit AEM Communities](getting-started.md)beschrieben wird.

Der Hauptunterschied ist, dass dieses Tutorial eine neue Community-Site-Vorlage erstellen wird, die nur die Funktion [](functions.md#page-function) Seite enthält, um eine einfache Community-Site zu erstellen, die frei von anderen Funktionen ist (außer den vorab verkabelten Funktionen, die für alle Community-Sites grundlegend sind).

### Neue Site-Vorlage erstellen {#create-new-site-template}

Erstellen Sie zunächst eine einfache [Community-Site-Vorlage](sites.md).

Wählen Sie in der globalen Navigation in einer Autoreninstanz **[!UICONTROL Extras > Communities > Site-Vorlagen]**.

![chlimage_1-82](assets/chlimage_1-82.png)

* Wählen Sie nun eine der folgenden Optionen aus `Create button`
* GRUNDINFORMATIONEN

   * `Name`: Einzelseitenvorlage
   * `Description`: Eine Vorlage, die aus einer einzelnen Seitenfunktion besteht.
   * Wählen Sie nun eine der folgenden Optionen aus `Enabled`

![chlimage_1-83](assets/chlimage_1-83.png)

* STRUKTUR

   * Ziehen Sie eine `Page` Funktion in den Vorlagenaufbau
   * Geben Sie für Konfigurationsfunktionsdetails

      * `Title`: Einzelseite
      * `URL`: page

![chlimage_1-84](assets/chlimage_1-84.png)

* Für **`Save`** die Konfiguration auswählen
* Für **`Save`** die Sitevorlage auswählen

### Neue Community-Site erstellen {#create-new-community-site}

Erstellen Sie jetzt eine neue Community-Site basierend auf der einfachen Site-Vorlage.

Wählen Sie nach dem Erstellen der Sitevorlage aus der globalen Navigation **[!UICONTROL Communities > Sites]**.

![chlimage_1-85](assets/chlimage_1-85.png)

* Symbol **`Create`** auswählen

* Schritt `1 - Site Template`

   * `Title`: Einfache Community-Site
   * `Description`: Eine Community-Site, die aus einer einzelnen Seite zum Experimentieren besteht.
   * `Community Site Root: (leave blank)`
   * `Community Site Base Language: English`
   * `Name`: Beispiel

      * url = http://localhost:4502/content/sites/sample
   * `Template`: auswählen `Single Page Template`


![chlimage_1-86](assets/chlimage_1-86.png)

* Wählen Sie nun eine der folgenden Optionen aus `Next`
* Schritt `2 - Design`

   * Auswählen eines Entwurfs

* Wählen Sie nun eine der folgenden Optionen aus `Next`
* Wählen Sie nun eine der folgenden Optionen aus `Next`

   (Alle Standardeinstellungen akzeptieren)

* Wählen Sie nun eine der folgenden Optionen aus `Create`

![chlimage_1-87](assets/chlimage_1-87.png)

## Veröffentlichen der Site {#publish-the-site}

![chlimage_1-88](assets/chlimage_1-88.png)

Wählen Sie in der [Community-Sites-Konsole](sites-console.md)das Veröffentlichungssymbol aus, um die Site zu veröffentlichen. Die Standardeinstellung ist &quot;http://localhost:4503&quot;.

## Öffnen Sie die Site im Autorenmodus im Bearbeitungsmodus {#open-the-site-on-author-in-edit-mode}

![chlimage_1-89](assets/chlimage_1-89.png)

Wählen Sie das Symbol zum Öffnen der Site aus, um die Site im Bearbeitungsmodus Ansicht.

Die URL lautet [http://localhost:4502/editor.html/content/sites/sample/en.html](http://localhost:4502/editor.html/content/sites/sample/en.html)

![chlimage_1-90](assets/chlimage_1-90.png)

Auf der einfachen Startseite ist es möglich, zu sehen, was durch die Community-Funktionen und -Vorlagen vorverkabelt ist, und mit dem Hinzufügen und Konfigurieren von Community-Komponenten zu spielen.

## Ansicht-Site bei Veröffentlichung {#view-site-on-publish}

Nach dem Veröffentlichen der Seite öffnen Sie die Seite in der [Veröffentlichungsinstanz](http://localhost:4503/content/sites/sample/en.html) , um mit den Funktionen als anonymer Site-Besucher, angemeldeter Benutzer oder Administrator zu experimentieren. Der in der Autorenumgebung angezeigte Link &quot;Administration&quot;wird in der Umgebung &quot;Veröffentlichen&quot;nur angezeigt, wenn sich ein Administrator anmeldet.
