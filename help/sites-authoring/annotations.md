---
title: Anmerkungen beim Bearbeiten einer Inhaltsseite
description: Viele direkt auf den Inhalt bezogene Komponenten erlauben die Hinzufügung von Anmerkungen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: de1ae7e3-db3a-4b5e-8a4f-ae111227181f
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 75%

---

# Anmerkungen beim Bearbeiten einer Seite{#annotations-when-editing-a-page}

Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Um diesen Vorgang zu erleichtern, können Sie in vielen Komponenten, die direkt mit Inhalt (und nicht mit dem Layout) in Verbindung stehen, Anmerkungen hinzufügen.

Bei einer Anmerkung wird eine farbige Markierung/Haftnotiz auf der Seite platziert. Mit einer Anmerkung können Sie (oder andere Benutzer) Kommentare und/oder Fragen für andere Autoren/Prüfer hinterlassen.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

>[!NOTE]
>
>In der klassischen Benutzeroberfläche erstellte Anmerkungen werden in der Touch-optimierten Benutzeroberfläche angezeigt. Zeichnungen sind jedoch benutzeroberflächenspezifisch und werden nur in der Benutzeroberfläche angezeigt, in der sie erstellt wurden.

>[!CAUTION]
>
>Durch Löschen einer Ressource (z. B. eines Absatzes) werden alle Anmerkungen und Zeichnungen gelöscht, die mit dieser Ressource verbunden sind (unabhängig von ihrer Position auf der Seite als Ganzes).

>[!NOTE]
>
>Je nach Ihren Anforderungen können Sie auch einen Workflow erstellen, damit Benachrichtigungen gesendet werden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

## Anmerkungen {#annotations}

Zum Erstellen und Ansehen von Anmerkungen wird ein spezieller [Modus](/help/sites-authoring/author-environment-tools.md#page-modes) verwendet.

>[!NOTE]
>
>Beachten Sie Folgendes: [Kommentare](/help/sites-authoring/basic-handling.md#timeline) Sie können auch Feedback zu einer Seite geben.

>[!NOTE]
>
>Sie können Anmerkungen zu einer Vielzahl von Ressourcen anfügen: 
>
>* [Anmerkungen zu Assets](/help/assets/manage-assets.md#annotating)
>* [Kommentieren von Video-Assets](/help/assets/managing-video-assets.md#annotate-video-assets)
>

### Hinzufügen von Anmerkungen zu Komponenten {#annotating-a-component}

Im Anmerkungsmodus können Sie Anmerkungen für Ihre Inhalte erstellen, bearbeiten, verschieben oder löschen:

1. Sie können den Anmerkungsmodus über das Symbol in der Symbolleiste (rechts oben) aufrufen, wenn Sie eine Seite bearbeiten:

   ![Anmerken](do-not-localize/screen_shot_2018-03-22at110414.png)

   Sie können nun vorhandene Anmerkungen anzeigen.

   >[!NOTE]
   >
   >Um den Anmerkungsmodus zu beenden, klicken Sie rechts oben in der Symbolleiste auf das Symbol Anmerken (x-Symbol).

1. Klicken Sie auf das Symbol Anmerkung hinzufügen (Plussymbol links in der Symbolleiste), um mit dem Hinzufügen von Anmerkungen zu beginnen.

   >[!NOTE]
   >
   >Um das Hinzufügen von Anmerkungen zu beenden (und zur Anzeige zurückzukehren), klicken Sie links in der oberen Symbolleiste auf das Symbol Abbrechen (x-Symbol in einem weißen Kreis).

1. Klicken Sie auf die gewünschte Komponente (Komponenten, die kommentiert werden können, werden durch einen blauen Rahmen hervorgehoben), um die Anmerkung hinzuzufügen und das Dialogfeld zu öffnen:

   ![screen_shot_2018-03-22at110606](assets/screen_shot_2018-03-22at110606.png)

   Hier können Sie das entsprechende Feld und/oder Symbol verwenden, um:

   * den Anmerkungstext einzugeben.
   * Eine Zeichnung (Linien und Formen) erstellen, um den Bereich der Komponente hervorzuheben.

     Der Mauszeiger ändert sich in ein Fadenkreuz, wenn Sie eine Zeichnung erstellen. Sie können mehrere separate Linien zeichnen. Die Zeichnungslinie hat dieselbe Farbe wie die Anmerkung und kann ein Pfeil, ein Kreis oder ein Oval sein.

     ![Skizze](do-not-localize/screen_shot_2018-03-22at110640.png)

   * Farbe wählen/ändern:

     ![Farbe wählen/ändern](do-not-localize/chlimage_1-19.png)

   * Die Anmerkung löschen.

     ![Anmerkung löschen](do-not-localize/screen_shot_2018-03-22at110647.png)

1. Sie können das Dialogfeld für die Anmerkungen schließen, indem Sie außerhalb des Dialogfelds. Es wird eine gekürzte Ansicht der Anmerkung zusammen mit sämtlichen Zeichnungen angezeigt:

   ![screen_shot_2018-03-22at110850](assets/screen_shot_2018-03-22at110850.png)

1. Wenn Sie mit dem Bearbeiten einer bestimmten Anmerkung fertig sind, können Sie Folgendes tun:

   * Klicken Sie auf die Textmarkierung, um die Anmerkung zu öffnen. Sobald sie geöffnet ist, können Sie den vollständigen Text sehen, Änderungen vornehmen oder die Anmerkung löschen.

      * Zeichnungen können nicht unabhängig von der Anmerkung gelöscht werden.

   * Positionieren Sie die Textmarkierung neu.
   * Klicken Sie auf eine Zeichnung, um diese Zeichnung auszuwählen und sie an die gewünschte Position zu ziehen.
   * Eine Komponente zu verschieben oder zu kopieren.

      * Alle damit verbundenen Anmerkungen und deren Zeichnungen werden ebenfalls verschoben oder kopiert und ihre Position in Relation zum Absatz bleibt gleich.

1. Um den Anmerkungsmodus zu beenden und zum zuvor verwendeten Modus zurückzukehren, klicken Sie auf das Symbol Anmerken (x-Symbol) rechts oben in der Symbolleiste.

>[!NOTE]
>
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einer anderen Person gesperrt wurde.

### Kennzeichnung von Anmerkungen {#annotation-indicator}

Anmerkungen werden nicht im Bearbeitungsmodus angezeigt, doch die Kennzeichnung oben rechts in der Symbolleiste gibt an, wie viele Anmerkungen auf der aktuellen Seite vorhanden sind. Die Kennzeichnung ersetzt das standardmäßige Anmerkungssymbol, dient jedoch ebenfalls als schneller Link, mit dem Sie den Anmerkungsmodus aktivieren/deaktivieren können:

![Anmerkungsanzeige](assets/chlimage_1-242.png)
