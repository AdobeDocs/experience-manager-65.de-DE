---
title: Struktur der Touch-optimierten Benutzeroberfläche von AEM
seo-title: Struktur der Touch-optimierten Benutzeroberfläche von AEM
description: Die Implementierung der Touch-optimierten Benutzeroberfläche in AEM basiert auf bestimmten Prinzipien und besteht aus mehreren Schlüsselelementen
seo-description: Die Implementierung der Touch-optimierten Benutzeroberfläche in AEM basiert auf bestimmten Prinzipien und besteht aus mehreren Schlüsselelementen
uuid: 9a255238-1adc-4a40-9c37-30cb53ffb26c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 55dba890-4847-4986-b272-33480bc1d573
exl-id: e562b289-5d8b-4fa8-ad1c-fff5f807a45e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 96%

---

# Struktur der Touch-optimierten Benutzeroberfläche von AEM{#structure-of-the-aem-touch-enabled-ui}

Die Touch-optimierte Benutzeroberfläche von AEM basiert auf bestimmten Prinzipien und besteht aus mehreren Schlüsselelementen:

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

* Das Logo und das Produkt/die Lösung, das/die Sie derzeit verwenden. In AEM wird außerdem ein Link zur globalen Navigation angezeigt
* Suchen
* Symbol für Zugriff auf Hilfe-Ressourcen
* Symbol für Zugriff auf andere Lösungen
* Hinweis (und Zugriff) auf Warnungen und Objekte im Posteingang, die auf Sie warten
* Benutzersymbol mit einem Link zum Profil-Management

### Symbolleiste {#toolbar}

Die Symbolleiste zeigt abhängig vom Kontext Tools an, die die Ansicht oder Elemente der Seite steuern. Die Symbolleiste ist produktspezifisch, es gibt jedoch einige gemeinsame Elemente.

Sie zeigt stets die aktuell möglichen Aktionen an:

![chlimage_1-145](assets/chlimage_1-145.png)

Die möglichen Aktionen hängen auch davon ab, ob eine Ressource ausgewählt ist:

![chlimage_1-146](assets/chlimage_1-146.png)

### Linke Leiste {#left-rail}

Die linke Leiste kann nach Bedarf geöffnet oder ausgeblendet werden. Sie zeigt Folgendes an:

* **Zeitleistensegment**
* **Verweise**
* **Filter**

Die Standardeinstellung ist **nur Inhalt** (Leiste ausgeblendet).

![chlimage_1-147](assets/chlimage_1-147.png)

## Bearbeiten von Seiten {#page-authoring}

Beim Bearbeiten von Seiten gibt es folgende strukturelle Bereiche.

### Inhalts-Frame {#content-frame}

Der Seiteninhalt wird im Inhalts-Frame gerendert. Der Inhalts-Frame ist komplett unabhängig vom Editor, sodass Konflikte durch CSS- oder JavaScript-Code vermieden werden.

Der Inhalts-Frame wird im rechten Bereich des Fensters unter der Symbolleiste angezeigt.

![chlimage_1-148](assets/chlimage_1-148.png)

### Editor-Frame {#editor-frame}

Der Editor-Frame enthält die Bearbeitungsfunktionen.

Der Editor-Frame ist ein Container (Abstraktion) für alle *Seitenbearbeitungselemente*. Er wird über dem Inhalts-Frame angezeigt und enthält:

* die obere Symbolleiste
* den Seitenbereich
* alle Überlagerungen
* alle anderen Seitenbearbeitungselemente, z. B. die Komponentensymbolleiste

![chlimage_1-149](assets/chlimage_1-149.png)

### Seitenbereich {#side-panel}

Der Seitenbereich enthält standardmäßig zwei Registerkarten, in denen Sie Assets und Komponenten auswählen und von dort auf die Seite ziehen können.

Der Seitenbereich ist standardmäßig ausgeblendet. Wenn er ausgewählt ist, wird er entweder auf der linken Seite oder über die gesamte Fensterbreite angezeigt (wenn das Fenster weniger als 1024 px breit ist, beispielsweise auf einem Mobilgerät).

![chlimage_1-150](assets/chlimage_1-150.png)

### Seitenbereich – Assets {#side-panel-assets}

Auf der Registerkarte „Assets“ können Sie aus einer Reihe von Assets auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![chlimage_1-151](assets/chlimage_1-151.png)

### Seitenbereich – Asset-Gruppen {#side-panel-asset-groups}

Auf der Registerkarte „Assets“ gibt es eine Dropdown-Liste zum Auswählen bestimmter Asset-Gruppen.

![chlimage_1-152](assets/chlimage_1-152.png)

### Seitenbereich – Komponenten {#side-panel-components}

Auf der Registerkarte „Komponenten“ können Sie aus verschiedenen Komponenten auswählen. Sie können auch nach einem bestimmten Begriff filtern oder eine Gruppe auswählen.

![chlimage_1-153](assets/chlimage_1-153.png)

### Überlagerungen {#overlays}

Diese überlagern den Inhalts-Frame und werden von [Ebenen](#layer) genutzt, um die (vollständig transparente) Interaktion mit Komponenten und ihrem Inhalt zu ermöglichen.

Die Überlagerungen befinden sich im Editor-Frame (neben allen anderen Seitenbearbeitungselementen); sie überlagern jedoch die entsprechenden Elemente im Inhalts-Frame.

![chlimage_1-154](assets/chlimage_1-154.png)

### Ebene {#layer}

Eine Ebene ist eine unabhängige Funktionsgruppe, die Sie aktivieren können, um Folgendes auszuführen:

* eine andere Ansicht der Seite aufrufen
* eine Seite bearbeiten und/oder damit interagieren

Anders als spezifische Aktionen zu einzelnen Komponenten bieten die Ebenen komplexe Funktionen für die gesamte Seite.

AEM enthält verschiedene vorab implementierte Ebenen für die Seitenbearbeitung. z. B. Bearbeiten, Vorschau, Anmerkungen.

>[!NOTE]
>
>Ebenen sind ein Konzept mit hohem Potenzial; sie beeinflussen die Ansicht und die Interaktion des Nutzers mit dem Seiteninhalt. Wenn Sie Ihre eigenen Ebenen entwickeln, stellen Sie sicher, dass die Ebene beim Verlassen eine Bereinigung durchführt.

### Ebenenschalter   {#layer-switcher}

Mit dem Ebenenschalter können Sie die Ebene auswählen, die Sie verwenden möchten. Wenn er geschlossen ist, zeigt er die aktuell verwendete Ebene an.

Der Ebenenschalter ist ein Dropdown-Menü in der Symbolleiste (am oberen Rand des Fensters im Editor-Frame).

![chlimage_1-155](assets/chlimage_1-155.png)

### Komponenten-Symbolleiste {#component-toolbar}

Jede Instanz einer Komponente zeigt ihre Symbolleiste an, wenn Sie darauf klicken (entweder einmal oder mit einem langsamen Doppelklick). Die Symbolleiste enthält spezifische Aktionen (z. B. Kopieren, Einfügen, offene Bearbeitung), die für die Komponenteninstanz (bearbeitbar) auf der Seite verfügbar sind.

Je nach verfügbarem Platz werden die Komponenten-Symbolleisten in der oberen oder unteren rechten Ecke der entsprechenden Komponente platziert.

![chlimage_1-156](assets/chlimage_1-156.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen zu den Konzepten der Touch-optimierten Benutzeroberfläche finden Sie im Artikel [Konzepte der Touch-optimierten AEM-Benutzeroberfläche](/help/sites-developing/touch-ui-concepts.md).

Weitere technische Informationen finden Sie im [JS-Dokumentationssatz](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/jsdoc/ui-touch/editor-core/index.html) für den Touch-optimierten Seiteneditor.
