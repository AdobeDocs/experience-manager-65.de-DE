---
title: Struktur der Touch-optimierten Benutzeroberfläche von Adobe Experience Manager
description: Die Touch-optimierte Benutzeroberfläche basiert, so wie sie in AEM implementiert ist, auf bestimmten Prinzipien und besteht aus mehreren Schlüsselelementen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: e562b289-5d8b-4fa8-ad1c-fff5f807a45e
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 100%

---

# Struktur der Touch-optimierten Benutzeroberfläche von Adobe Experience Manager{#structure-of-the-aem-touch-enabled-ui}

Die Touch-optimierte Benutzeroberfläche von Adobe Experience Manager (AEM) basiert auf bestimmten Prinzipien und besteht aus mehreren Schlüsselelementen:

## Konsolen {#consoles}

### Grundlegendes Layout und Größenanpassung {#basic-layout-and-resizing}

Die Benutzeroberfläche ist für Mobilgeräte sowie Desktop-Computer geeignet. Adobe hat sich dagegen entschieden, zwei verschiedene Layouts zu entwickeln, und verwendet stattdessen ein Layout, das mit allen Bildschirmen und Geräten kompatibel ist.

Alle Module verwenden dasselbe Basis-Layout. In AEM sieht es wie folgt aus:

![chlimage_1-142](assets/chlimage_1-142.png)

Das Layout ermöglicht eine schnelle und einfache Bedienung und passt sich an die Größe des verwendeten Bildschirms oder Fensters an.

Wenn beispielsweise die Auflösung unter 1.024 px liegt (z. B. bei einem Mobilgerät), wird die Anzeige entsprechend angepasst:

![chlimage_1-143](assets/chlimage_1-143.png)

### Kopfzeilenleiste {#header-bar}

![chlimage_1-144](assets/chlimage_1-144.png)

Die Kopfzeilenleiste zeigt globale Elemente, z. B.:

* das Logo sowie das aktuell verwendete Produkt bzw. die verwendete Lösung; für AEM zudem inklusive eines Links zur globalen Navigation
* Suchen
* ein Symbol für den Zugriff auf Hilferessourcen
* ein Symbol für den Zugriff auf andere Lösungen
* ein Hinweis (und Zugriff) auf Warnungen und Elemente im Posteingang
* Benutzersymbol mit einem Link zum Profil-Management

### Symbolleiste {#toolbar}

Die Symbolleiste zeigt abhängig vom Kontext Tools an, die die Ansicht oder Elemente der Seite steuern. Die Symbolleiste ist produktspezifisch, bei den Elementen gibt es jedoch einige Gemeinsamkeiten.

Sie zeigt stets die aktuell möglichen Aktionen an:

![chlimage_1-145](assets/chlimage_1-145.png)

Dies ist auch abhängig davon, ob eine Ressource ausgewählt ist:

![chlimage_1-146](assets/chlimage_1-146.png)

### Linke Leiste {#left-rail}

Die linke Leiste kann nach Bedarf geöffnet oder ausgeblendet werden. Sie zeigt Folgendes an:

* **Zeitleiste**
* **Verweise**
* **Filter**

Standardmäßig ist **Nur Inhalt** eingestellt (die Leiste ist ausgeblendet).

![chlimage_1-147](assets/chlimage_1-147.png)

## Bearbeiten von Seiten {#page-authoring}

Beim Bearbeiten von Seiten gibt es folgende strukturelle Bereiche.

### Inhalts-Frame {#content-frame}

Der Seiteninhalt wird im Inhalts-Frame gerendert. Der Inhalts-Frame ist unabhängig vom Editor, um sicherzustellen, dass keine CSS- oder JavaScript-bedingten Konflikte auftreten.

Der Inhalts-Frame wird im rechten Bereich des Fensters unter der Symbolleiste angezeigt.

![chlimage_1-148](assets/chlimage_1-148.png)

### Editor-Frame {#editor-frame}

Der Editor-Frame umfasst die Bearbeitungsfunktionen.

Der Editor-Frame ist ein Container (eine Abstraktion) für alle *Seitenbearbeitungselemente*. Er wird über dem Inhalts-Frame angezeigt und enthält:

* die obere Symbolleiste
* das seitliche Bedienfeld
* alle Überlagerungen
* alle anderen Seitenbearbeitungselemente, z. B. die Komponenten-Symbolleiste

![chlimage_1-149](assets/chlimage_1-149.png)

### Seitenbereich {#side-panel}

Das seitliche Bedienfeld enthält zwei Standardregisterkarten, über die Sie Assets und Komponenten auswählen können. Sie können von hier auf die Seite gezogen und dort abgelegt werden.

Der Seitenbereich ist standardmäßig ausgeblendet. Wenn es ausgewählt ist, wird das seitliche Bedienfeld entweder auf der linken Seite bzw. über die gesamte Fensterbreite angezeigt (wenn das Fenster weniger als 1.024 Pixel breit ist, beispielsweise auf einem Mobilgerät).

![chlimage_1-150](assets/chlimage_1-150.png)

### Seitenbereich – Assets {#side-panel-assets}

Auf der Registerkarte „Assets“ können Sie aus einer Reihe von Assets auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![chlimage_1-151](assets/chlimage_1-151.png)

### Seitenbereich – Asset-Gruppen {#side-panel-asset-groups}

Auf der Registerkarte „Assets“ gibt es eine Dropdown-Liste zum Auswählen bestimmter Asset-Gruppen.

![chlimage_1-152](assets/chlimage_1-152.png)

### Seitliches Panel – Komponenten {#side-panel-components}

Auf der Registerkarte „Komponenten“ können Sie aus einer Reihe von Komponenten auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![chlimage_1-153](assets/chlimage_1-153.png)

### Überlagerungen {#overlays}

Diese überlagern den Inhalts-Frame und werden von [Ebenen](#layer) genutzt, um die (transparente) Interaktion mit Komponenten und ihrem Inhalt zu ermöglichen.

Die Überlagerungen befinden sich im Editor-Frame (neben allen anderen Seitenbearbeitungselementen); sie überlagern jedoch die entsprechenden Elemente im Inhalts-Frame.

![chlimage_1-154](assets/chlimage_1-154.png)

### Ebene {#layer}

Eine Ebene ist eine unabhängige Funktionsgruppe, die Sie aktivieren können, um Folgendes auszuführen:

* eine andere Ansicht der Seite aufrufen
* Bearbeiten einer Seite und/oder Interagieren mit einer Seite

Anders als spezifische Aktionen zu einzelnen Komponenten bieten die Ebenen komplexe Funktionen für die gesamte Seite.

AEM enthält verschiedene vorab implementierte Ebenen für die Seitenbearbeitung, z. B. für die Bearbeitung, Vorschau und Anmerkungen.

>[!NOTE]
>
>Bei Ebenen handelt es sich um ein leistungsstarkes Konzept, das die Ansicht der Benutzenden auf den Seiteninhalt und ihre Interaktion mit dem Seiteninhalt beeinflusst. Wenn Sie Ihre eigenen Ebenen entwickeln, müssen Sie sicherstellen, dass die betreffende Ebene beim Verlassen bereinigt wird.

### Ebenenschalter {#layer-switcher}

Mit dem Ebenenschalter können Sie die Ebene auswählen, die verwendet werden soll. Wenn er geschlossen ist, zeigt er die aktuell verwendete Ebene an.

Der Ebenenschalter ist ein Dropdown-Menü in der Symbolleiste (am oberen Fensterrand im Editor-Frame).

![chlimage_1-155](assets/chlimage_1-155.png)

### Komponenten-Symbolleiste {#component-toolbar}

Jede Instanz einer Komponente zeigt die zugehörige Symbolleiste an, wenn Sie darauf klicken (einmaliger Klick oder langsamer Doppelklick). Die Symbolleiste enthält spezifische Aktionen (z. B. „Kopieren“, „Einfügen“, „Editor öffnen“), die für die Komponenteninstanz (Bearbeitbar) auf der Seite verfügbar sind.

Je nach verfügbarem Platz werden die Komponenten-Symbolleisten in der oberen oder unteren rechten Ecke der entsprechenden Komponente platziert.

![chlimage_1-156](assets/chlimage_1-156.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen zu den Konzepten der Touch-optimierten Benutzeroberfläche finden Sie unter [Konzepte der Touch-optimierten Benutzeroberfläche von AEM](/help/sites-developing/touch-ui-concepts.md).

Weitere technische Informationen finden Sie im [JS-Dokumentationssatz](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/jsdoc/ui-touch/editor-core/index.html) für den Touch-optimierten Seiteneditor.
