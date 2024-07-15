---
title: Massenverarbeitungsvorgänge
description: null
page-status-flag: never-activated
contentOwner: sarchiz
docset: aem65
source-git-commit: 96e2e945012046e6eac878389b7332985221204e
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 35%

---


# Massenverarbeitungsvorgänge {#bulk-processing-operations}

## Einführung {#introduction}

Mit der neuesten Version von Adobe Experience Manager (AEM) wurde die Schaltfläche Alle auswählen auf alle Ansichten erweitert: Listen-, Spalten- und Kartenansicht. Über die Schaltfläche „Alle auswählen“ werden jetzt alle Inhalte eines bestimmten Ordners oder einer bestimmten Sammlung ausgewählt und nicht nur die Assets und Seiten, die im Client-Browser geladen und angezeigt werden.

Schlüsselaktionen für den Massenvorgang wurden aktiviert: **Verschieben**, **Löschen** und **Kopieren**. Ein neues Dialogfeld informiert Kunden darüber, für welche Aktionen die Massenverarbeitung nicht verfügbar ist.

## Verwendung {#how-to-use}

Der Karten-, Listen- oder Spaltenansicht wurde eine neue Schaltfläche mit dem Namen **Alle auswählen** hinzugefügt. Diese Schaltfläche kann in allen Ansichten verwendet werden, um alle Elemente im Datensatz auszuwählen.

In früheren Versionen von AEM war die Auswahl darauf begrenzt, was im Client-Browser geladen war. Diese neue Änderung wurde eingeführt, um Verwirrung in Bezug auf die Anzahl der Elemente zu vermeiden, für die ein Massenvorgang durchgeführt wird.

Vorerst wurden drei Vorgänge zur Massenverarbeitung hinzugefügt:

* Verschieben
* Kopieren
* Löschen

Künftig werden weitere Vorgänge unterstützt.
Um diese Funktion zu verwenden, navigieren Sie zu dem Ordner oder der Sammlung, in dem Sie Massenvorgänge auf Seiten oder in Assets durchführen möchten.

Wählen Sie dann eine der Ansichten aus, wie unten dargestellt:

### Kartenansicht {#card-view}

![Kartenansicht, die Miniaturansichten verschiedener Bild-Assets anzeigt.](assets/unu.png)

### Massenauswahl in der Kartenansicht {#bulk-selection-in-card-view}

Assets oder Seiten können mit der Schaltfläche **Alle auswählen** per Massenauswahl ausgewählt werden:

![Schaltfläche Alle auswählen , die oben rechts in der Kartenansicht angezeigt wird.](assets/doi.png) ![Alle Miniaturansichten von Bild-Assets in der Kartenansicht werden mit Häkchen als ausgewählt angezeigt.](assets/trei.png)

### Listenansicht {#list-view}

Dasselbe gilt auch für die Listenansicht:

![Die Option &quot;Alle auswählen&quot;in der oberen rechten Ecke der Listenansicht ist hervorgehoben.](assets/patru_modified.png)

### Massenauswahl in der Listenansicht {#bulk-selection-in-list-view}

Verwenden Sie in der Listenansicht entweder die Schaltfläche **Alle auswählen** oder das Kontrollkästchen links für die Massenauswahl.

![Die Live-Ansicht mit Miniaturansichten von Bild-Assets wird in horizontalen Zeilen angezeigt.](assets/cinci.png) ![Listenfeld mit Miniaturansichten von Bild-Assets und einem Kontrollkästchen links neben Name.](assets/sase.png)

### Spaltenansicht {#column-view}

![Spaltenansicht mit Miniaturbildern von Bild-Assets, die in vertikalen Spalten angezeigt werden.](assets/sapte.png)

### Massenauswahl in der Spaltenansicht {#bulk-selection-in-column-view}

![Alle Miniaturansichten von Bild-Assets in der Spaltenansicht werden mit Häkchen als ausgewählt angezeigt.](assets/opt.png)

## Massenverarbeitungsvorgänge {#bulk-enabled-operations}

Nach der Auswahl kann eine der drei Massenaktionen ausgeführt werden: **Verschieben**, **Kopieren** oder **Löschen**.

Hier wird der Vorgang **Verschieben** für die oben ausgewählten Assets ausgeführt. In jeder der Ansichten führt dies dazu, dass alle Assets an den ausgewählten Ort verschoben werden und nicht nur die, die auf dem Bildschirm geladen werden.

![Verschieben Sie Assets, die einen ausgewählten Ordner in der Spaltenansicht anzeigen.](assets/noua.png)

Bei anderen Vorgängen, bei denen keine Massenvorgänge aktiviert sind, z. B. **Download,**, wird eine Warnung angezeigt, die besagt, dass nur Elemente, die im Browser geladen werden, in den Vorgang einbezogen werden.

![Assets-Ansicht mit ausgewählten Bild-Assets und dem Popup-Dialogfeld &quot;Massenaktion nicht unterstützt&quot;.](assets/zece.png)
