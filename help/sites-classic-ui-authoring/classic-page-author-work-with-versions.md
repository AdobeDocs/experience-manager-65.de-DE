---
title: Arbeiten mit Seitenversionen
description: Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten.
uuid: 06e112cd-e4ae-4ee0-882d-7009f53ac85b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 48936115-4be2-4b0c-81ce-d61e43e4535d
docset: aem65
exl-id: 4eb0de5e-0306-4166-9cee-1297a5cd14ce
source-git-commit: e1a0b114ce16d0e7f6a464e9d30b8f111297bcc6
workflow-type: tm+mt
source-wordcount: '1362'
ht-degree: 57%

---

# Arbeiten mit Seitenversionen{#working-with-page-versions}

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung können Sie die folgenden Aktionen durchführen:

* Erstellen Sie eine Version einer Seite.
* Stellen Sie eine Seite auf eine frühere Version zurück, um eine Änderung rückgängig zu machen, die Sie beispielsweise an einer Seite vorgenommen haben.
* Vergleichen Sie die aktuelle Version einer Seite mit einer früheren Version mit Unterschieden in Text und Bildern, die hervorgehoben sind.

## Erstellen einer neuen Version   {#creating-a-new-version}

So erstellen Sie eine neue Version einer Seite:

1. Öffnen Sie in Ihrem Browser die Seite, für die Sie eine neue Version erstellen möchten.
1. Wählen Sie im Sidekick die **Versionierung** Registerkarte, dann die **Version erstellen** Unterregisterkarte.

   ![screen_shot_2012-02-14at40259pm](assets/screen_shot_2012-02-14at40259pm.png)

1. Geben Sie einen **Kommentar** ein (optional).
1. Um eine Bezeichnung für die Version anzugeben (optional), klicken Sie auf die Schaltfläche **Mehr >>** und geben Sie unter **Bezeichnung** einen Namen für die Version ein. Wird keine Bezeichnung festgelegt, wird die Version automatisch nummeriert.
1. Klicken Sie auf **Version erstellen**. Auf der Seite wird eine grau hinterlegte Meldung eingeblendet, z. B.:
Version 1.2 erstellt für: Hemden.

>[!NOTE]
>
>Eine Version wird automatisch bei Aktivierung einer Seite erstellt.

## Wiederherstellen einer Seitenversion über den Sidekick {#restoring-a-page-version-from-sidekick}

So stellen Sie eine frühere Version der Seite wieder her:

1. Öffnen Sie die Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie im Sidekick die **Versionierung** Registerkarte, dann die **Version wiederherstellen** Unterregisterkarte.

   ![screen_shot_2012-02-14at42949pm](assets/screen_shot_2012-02-14at42949pm.png)

1. Wählen Sie die Version aus, die Sie wiederherstellen möchten, und wählen Sie **Wiederherstellen** aus.

## Wiederherstellen einer Seitenversion über die Konsole {#restoring-a-page-version-from-the-console}

Sie können diese Methode verwenden, um eine Seitenversion wiederherzustellen. Sie kann auch verwendet werden, um zuvor gelöschte Seiten wiederherzustellen:

1. Im **Websites** , navigieren Sie zu der Seite, die Sie wiederherstellen möchten, und wählen Sie sie aus.
1. Wählen Sie im oberen Menü die Option **Instrumente**, dann **Wiederherstellen**:

   ![screen_shot_2012-02-08at41326pm](assets/screen_shot_2012-02-08at41326pm.png)

1. Wenn Sie **Version wiederherstellen...** auswählen, werden die Versionen der Dokumente im aktuellen Ordner aufgelistet. Auch wenn eine Seite gelöscht wurde, wird ihre letzte Version aufgeführt:

   ![screen_shot_2012-02-08at45743pm](assets/screen_shot_2012-02-08at45743pm.png)

1. Wählen Sie die Version aus, die Sie wiederherstellen möchten, und klicken Sie auf **Wiederherstellen**. AEM stellt die ausgewählten Versionen (bzw. Bäume) wieder her.

### Wiederherstellen eines Baums über die Konsole {#restoring-a-tree-from-the-console}

Sie können diese Methode verwenden, um eine Seitenversion wiederherzustellen. Sie kann auch verwendet werden, um zuvor gelöschte Seiten wiederherzustellen:

1. Im **Websites** -Konsole, navigieren Sie zu dem Ordner, den Sie wiederherstellen möchten, und wählen Sie ihn aus.
1. Wählen Sie im oberen Menü die Option **Instrumente**, dann **Wiederherstellen**.
1. Wenn Sie **Baum wiederherstellen...** auswählen, wird ein Dialogfeld geöffnet, in dem Sie den wiederherzustellenden Baum auswählen können:

   ![screen_shot_2012-02-08at45743pm-1](assets/screen_shot_2012-02-08at45743pm-1.png)

1. Klicken **Wiederherstellen**. AEM stellt den ausgewählten Baum wieder her.

## Vergleich mit einer früheren Version {#comparing-with-a-previous-version}

So vergleichen Sie die aktuelle Version der Seite mit einer früheren Version:

1. Öffnen Sie in Ihrem Browser die Seite, für die Sie einen Vergleich mit einer früheren Version anstellen möchten.
1. Wählen Sie im Sidekick die Registerkarte **Versionierung** und dann die Unterregisterkarte **Version wiederherstellen** aus.

   ![screen_shot_2012-02-14at42949pm-1](assets/screen_shot_2012-02-14at42949pm-1.png)

1. Markieren Sie die Version, die Sie vergleichen möchten, und klicken Sie auf die Schaltfläche **Differenz**.
1. Die Unterschiede zwischen der aktuellen Version und der ausgewählten Version werden wie folgt dargestellt:

   * Gelöschter Text ist rot und durchgestrichen.
   * Der hinzugefügte Text ist grün und hervorgehoben.
   * Bilder, die hinzugefügt oder gelöscht wurden, werden grün gerahmt.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Wählen Sie im Sidekick die **Version wiederherstellen** und klicken Sie auf **&lt;&lt;back span=&quot;&quot; id=&quot;3&quot; translate=&quot;no&quot; /> -Schaltfläche, um die aktuelle Version anzuzeigen.**

## Timewarp {#timewarp}

Timewarp ist eine Funktion, die den ***Veröffentlichungsstatus*** einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

Ziel ist es, Ihnen die Nachverfolgung der veröffentlichten Website zu einem bestimmten Zeitpunkt zu ermöglichen. Hierbei werden die Seitenaktivierungen verwendet, um den Status der Veröffentlichungsumgebung zu ermitteln.

Gehen Sie hierfür wie folgt vor:

* Das System sucht nach der Seitenversion, die zum ausgewählten Zeitpunkt aktiv war.
* Dies bedeutet, dass die angezeigte Version erstellt/aktiviert wurde *before* den in Timewarp ausgewählten Zeitpunkt.
* Wenn Sie zu einer Seite navigieren, die gelöscht wurde, wird dies ebenfalls gerendert - solange die alten Versionen der Seite noch im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Status der Seite in der Autorenumgebung zurück (um einen Fehler/404-Seite zu verhindern, was bedeutet, dass Sie nicht mehr durchsuchen können).

>[!NOTE]
>
>Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen. Wenn sich Elemente (wie Code, CSS, Bilder usw.) zum Rendern der Website geändert haben, unterscheidet sich die Ansicht von der ursprünglichen Ansicht, da diese Elemente nicht im Repository versioniert werden.

### Verwenden des Timewarp-Kalenders {#using-the-timewarp-calendar}

Timewarp ist im Sidekick verfügbar.

Die Kalenderversion wird verwendet, wenn ein bestimmter Tag angezeigt werden soll:

1. Öffnen Sie die Registerkarte **Versionierung** und klicken Sie auf **Timewarp** (unten im Sidekick). Das folgende Dialogfeld wird angezeigt:

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Geben Sie mithilfe der Datums- und Uhrzeitauswahl das gewünschte Datum/die gewünschte Uhrzeit an und klicken Sie auf **Los**.

   Timewarp zeigt die Seite so an, wie sie vor/am gewählten Datum veröffentlicht wurde.

   >[!NOTE]
   >
   >Timewarp funktioniert nur dann vollständig, wenn Sie die Seite zuvor veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung an.

   >[!NOTE]
   >
   >Wenn Sie zu einer Seite navigieren, die aus dem Repository entfernt/gelöscht wurde, wird sie ordnungsgemäß gerendert, wenn alte Versionen der Seite weiterhin im Repository verfügbar sind.

   >[!NOTE]
   >
   >Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie dies über [Wiederherstellen](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoring-a-page-version-from-sidekick) manuell ausführen.

1. Wenn Sie die Seite wieder verlassen möchten, klicken Sie auf eine der folgenden Optionen:

   * Mit **Timewarp beenden** verlassen Sie Timewarp und kehren zur aktuellen Autorenseite zurück.
   * Mit [Zeitleiste anzeigen](#using-the-timewarp-timeline) zeigen Sie die Zeitleiste an.

   ![chlimage_1-77](assets/chlimage_1-77.png)

### Verwenden der Timewarp-Zeitleiste {#using-the-timewarp-timeline}

Die Zeitleistenversion wird verwendet, wenn Sie eine Übersicht über die Veröffentlichungsaktivitäten auf der Seite anzeigen möchten.

Wenn Sie die Zeitleiste im Dokument anzeigen möchten:

1. Sie können die Zeitleiste wie folgt anzeigen:

   1. Öffnen Sie die Registerkarte **Versionierung** und klicken Sie auf **Timewarp** (unten im Sidekick).

   1. Verwenden Sie das Sidekick-Dialogfeld, das nach [der Verwendung des Timewarp-Kalenders angezeigt wird](#using-the-timewarp-calendar).

1. Klicken Sie auf **Zeitleiste anzeigen**, die Zeitleiste des Dokuments wird angezeigt. Beispiel:

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Wählen Sie (durch Gedrückthalten und Ziehen) die Zeitleiste aus und verschieben Sie sie, um sich durch die Zeitleiste des Dokuments zu bewegen.

   * Jede Linie steht für eine veröffentlichte Version.
Wenn eine Seite aktiviert wird, beginnt eine neue Linie. Jedes Mal, wenn das Dokument bearbeitet wird, wird eine neue Farbe angezeigt.
Im Beispiel unten zeigt die rote Linie an, dass die Seite während des Zeitraums der ursprünglichen grünen Version bearbeitet wurde, und die gelbe Linie zeigt an, dass die Seite während der roten Version bearbeitet wurde usw.

   ![chlimage_1-79](assets/chlimage_1-79.png)

1. Klicken Sie auf:

   1. **Los** , um den Inhalt der veröffentlichten Seite zum ausgewählten Zeitpunkt anzuzeigen.
   1. Wenn der Inhalt angezeigt wird, verwenden Sie **Timewarp beenden**, um Timewarp zu verlassen und zur aktuellen Autorenseite zurückzukehren.

### Timewarp-Beschränkungen {#timewarp-limitations}

Timewarp versucht, eine Seite zu einem bestimmten Zeitpunkt zu reproduzieren. Aufgrund der Komplexität der kontinuierlichen Bearbeitung von Inhalten in AEM ist dies jedoch nicht immer möglich. Diese Einschränkungen sollten bei der Verwendung von Timewarp beachtet werden.

* **Timewarp funktioniert auf veröffentlichten Seiten**: Timewarp funktioniert nur dann vollständig, wenn Sie die Seite bereits veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung.
* **Timewarp verwendet Seitenversionen**: Wenn Sie zu einer inzwischen aus dem Repository gelöschten Seite navigieren, wird diese ebenfalls korrekt wiedergegeben, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* **Entfernte Versionen wirken sich auf Timewarp**: Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen.

* **Timewarp ist schreibgeschützt**: Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie dies über [Wiederherstellen](#main-pars-title-1) manuell ausführen.

* **Timewarp basiert nur auf dem Seiteninhalt**: Die Ansicht unterscheidet sich von der ursprünglichen Ansicht, wenn Elemente (Code, CSS, Assets/Bilder usw.) für die Anzeige der Website geändert wurden, da diese Elemente nicht im Repository versioniert werden.

>[!CAUTION]
>
>Timewarp wurde als Tool entwickelt, das Autoren beim Verstehen und Erstellen ihres Inhalts unterstützen kann. Es ist nicht als Prüfprotokoll oder zu rechtlichen Zwecken gedacht.
