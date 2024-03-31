---
title: Arbeiten mit Inhaltsseitenversionen
description: Sie können in Adobe Experience Manager verschiedene Versionen einer Seite erstellen, vergleichen und wiederherstellen.
exl-id: cb7a9da2-7112-4ef0-b1cf-211a7df93625
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 100%

---

# Arbeiten mit Seitenversionen{#working-with-page-versions}

Durch die Versionierung wird die „Momentaufnahme“ einer Seite zu einem bestimmten Zeitpunkt festgehalten. Bei der Versionierung können Sie die folgenden Aktionen durchführen:

* Erstellen einer Version einer Seite.
* Wiederherstellen einer früheren Version einer Seite, z. B.:
   * zum Rückgängigmachen einer Änderung an einer Seite
* Vergleichen der aktuellen Version einer Seite mit einer früheren Version:
   * zum Hervorheben der Unterschiede im Text und in Bildern

## Erstellen einer neuen Version {#creating-a-new-version}

Sie können eine Version Ihrer Ressource folgendermaßen erstellen:

* über die [Zeitleiste](#creating-a-new-version-timeline)
* mithilfe der Option [Erstellen](#creating-a-new-version-create-with-a-selected-resource) (wenn eine Ressource ausgewählt ist)

### Erstellen einer neuen Version – Zeitleiste {#creating-a-new-version-timeline}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die Spalte **Zeitleiste**.
1. Klicken Sie auf die Pfeilspitze neben dem Kommentarfeld, um die Optionen anzuzeigen:

   ![Zeitleiste – Als Version speichern](assets/screen-shot_2019-03-05at112335.png)

1. Wählen Sie **Als Version speichern**.
1. Geben Sie ggf. eine **Beschriftung** und einen **Kommentar** ein.

   ![Version erstellen – Beschriftung und Kommentar hinzufügen](assets/chlimage_1-42.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Informationen in der Timeline werden aktualisiert, um die neue Version anzuzeigen.

### Erstellen einer neuen Version – Erstellen mit einer ausgewählten Ressource {#creating-a-new-version-create-with-a-selected-resource}

1. Navigieren Sie zu der Seite, für die Sie eine Version erstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Wählen Sie aus der Symbolleiste die Option **Erstellen** aus, um das Dialogfeld zu öffnen.
1. Sie können ggf. eine **Beschriftung** und einen **Kommentar** eingeben:

   ![Beschriftung und Kommentar eingeben](assets/screen_shot_2012-02-15at105050am.png)

1. Bestätigen Sie die neue Version, indem Sie auf **Erstellen** klicken.

   Die Timeline wird geöffnet und die Informationen werden aktualisiert, um die neue Version anzuzeigen.

## Reaktivierung von Versionen {#reinstating-versions}

Nachdem Sie eine Version Ihrer Seite erstellt haben, gibt es verschiedene Methoden, eine ältere Version zu reaktivieren:

* die Option **Auf diese Version zurück** in der [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline).

  Reaktivieren Sie eine frühere Version einer ausgewählten Seite.

* die Optionen zum **Wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-authoring/basic-handling.md#actions-toolbar)

   * **Version wiederherstellen**

     Reaktivieren Sie Versionen bestimmter Seiten im derzeit ausgewählten Ordner; dies kann auch die Wiederherstellung von zuvor gelöschten Seiten umfassen.

   * **Baum wiederherstellen**

     Reaktivieren Sie eine Version eines gesamten Baums zu einem bestimmten Datum und einer bestimmten Uhrzeit; dies kann Seiten umfassen, die zuvor gelöscht wurden.

>[!NOTE]
>
>Wenn eine Seite reaktiviert wird, gehört die erstellte Version zu einem neuen Zweig.
>
>Beispiel:
>
>1. Erstellen Sie Versionen einer beliebigen Seite.
>1. Die anfänglichen Beschriftungen und Versionsknotennamen lauten 1.0, 1.1, 1.2 usw.
>1. Reaktivieren Sie die erste Version, in diesem Fall 1.0.
>1. Erstellen Sie erneut Versionen.
>1. Die generierten Beschriftungen und Knotennamen lauten nun 1.0.0, 1.0.1, 1.0.2 usw.

### Auf eine Version zurücksetzen {#revert-to-a-version}

So können Sie für die ausgewählte Seite eine frühere Version **wiederherstellen**:

1. Navigieren Sie zu der Seite, für die Sie eine frühere Version wiederherstellen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus. Die Seitenversionen für die ausgewählte Seite werden aufgelistet.
1. Wählen Sie die Version aus, die Sie wiederherstellen möchten. Die möglichen Optionen werden angezeigt:

   ![Auf diese Version zurück](assets/screen-shot_2019-03-05at112505.png)

1. Wählen Sie **Auf diese Version zurück**. Die ausgewählte Version wird wiederhergestellt und die Informationen in der Zeitleiste werden aktualisiert.

### Version wiederherstellen {#restore-version}

Mit dieser Methode können Versionen bestimmter Seiten im aktuellen Ordner wiederhergestellt werden. Dies kann auch die Wiederherstellung von Seiten umfassen, die zuvor gelöscht wurden:

1. Navigieren Sie zum gewünschten Ordner und [wählen](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) Sie ihn aus.

1. Wählen Sie **Wiederherstellen** und dann **Version wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-authoring/basic-handling.md#actions-toolbar).

   >[!NOTE]
   >
   >Wenn Sie:
   >
   >* eine einzelne Seite ausgewählt haben, die noch nie untergeordnete Seiten hatte,
   >* oder keine der Seiten im Ordner Versionen enthält,
   >
   >ist die Anzeige leer, da keine Versionen verfügbar sind.

1. Die verfügbaren Versionen sind aufgeführt:

   ![Version wiederherstellen – Liste aller Seiten im Ordner](/help/sites-authoring/assets/versions-restore-version-01.png)

1. Verwenden Sie für eine bestimmte Seite die Dropdown-Auswahl unter **WIEDERHERZUSTELLENDE VERSION**, um die erforderliche Version für diese Seite auszuwählen.

   ![Version wiederherstellen – Version auswählen](/help/sites-authoring/assets/versions-restore-version-02.png)

1. Wählen Sie in der Hauptanzeige die zu wiederherzustellende Seite aus:

   ![Version wiederherstellen – Seite auswählen](/help/sites-authoring/assets/versions-restore-version-03.png)

1. Wählen Sie für die ausgewählte Version der ausgewählten Seite, die als aktuelle Version wiederhergestellt werden soll, die Option **Wiederherstellen**.

>[!NOTE]
>
>Die Reihenfolge, in der Sie eine erforderliche Seite und die zugehörige Version auswählen, ist austauschbar.

### Baum wiederherstellen {#restore-tree}

Diese Methode kann verwendet werden, um eine Version eines Baums, wie er zu einem bestimmten Datum und zu einer bestimmten Zeit war, wiederherzustellen; dies kann Seiten umfassen, die zuvor gelöscht wurden:

1. Navigieren Sie zum gewünschten Ordner und [wählen](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) Sie ihn aus.

1. Wählen Sie **Wiederherstellen** und dann **Baum wiederherstellen** in der oberen [Symbolleiste für Aktionen](/help/sites-authoring/basic-handling.md#actions-toolbar). Die aktuelle Version des Baums wird angezeigt:

   ![Baum wiederherstellen](/help/sites-authoring/assets/versions-restore-tree-02.png)

1. Verwenden Sie die Datums- und Uhrzeitauswahl unter **Neueste Versionen am Datum**, um eine andere Version des Baums auszuwählen – und zwar die, die wiederhergestellt werden soll.

1. Setzen Sie bei Bedarf das Flag **Seiten ohne Versionsangabe beibehalten**:

   * Wenn diese Option aktiviert (ausgewählt) ist, werden alle Seiten ohne Versionierung beibehalten und von der Wiederherstellung nicht beeinflusst.

   * Wenn diese Option deaktiviert (nicht ausgewählt) ist, werden alle Seiten ohne Versionierung entfernt, da sie nicht im versionierten Baum vorhanden waren.

1. Wählen Sie **Wiederherstellen** für die ausgewählte Version des Baums, die als *aktuelle* Version wiederhergestellt werden soll.

## Vorschau einer Version {#previewing-a-version}

Sie können eine Vorschau einer bestimmten Version anzeigen:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgelistet. Wählen Sie die Version, die Sie in der Vorschau anzeigen möchten:

   ![Version zur Vorschau auswählen](assets/screen-shot_2019-03-05at112505-1.png)

1. Wählen Sie **Vorschau**. Die Seite wird in einer neuen Registerkarte angezeigt.

   >[!CAUTION]
   >
   >Wenn eine Seite verschoben wurde, können Sie keine Vorschau von Versionen mehr anzeigen, die vor dem Verschieben erstellt wurden.
   >
   >* Wenn Probleme bei der Vorschau auftreten, überprüfen Sie in der [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline) der Seite, ob die Seite verschoben wurde.

## Vergleichen einer Version mit der aktuellen Seite {#comparing-a-version-with-current-page}

So vergleichen Sie eine frühere Version mit der aktuellen Seite:

1. Navigieren Sie zu der Seite, die Sie vergleichen möchten.
1. Wählen Sie die Seite im [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Öffnen Sie die **Zeitleiste** und wählen Sie entweder **Alle anzeigen** oder **Versionen** aus.
1. Die Seitenversionen werden aufgelistet. Wählen Sie die Version aus, die Sie vergleichen möchten.

   ![Aufgeführte Seitenversionen – Version auswählen](assets/screen-shot_2019-03-05at112505-2.png)

1. Wählen Sie **Mit aktueller Version vergleichen** aus. Der [Seitenvergleich](/help/sites-authoring/page-diff.md) wird geöffnet und zeigt die Unterschiede an.

## Timewarp {#timewarp}

Timewarp ist eine Funktion, die den *Veröffentlichungsstatus* einer Seite zu einer bestimmten Zeit in der Vergangenheit simuliert.

>[!TIP]
>
>[Timewarp kann auch mit Launches verwendet werden, um eine Vorschau der Zukunft anzuzeigen](/help/sites-authoring/launches.md), wenn AEM 6.5.10.0 oder höher ausgeführt wird.

Die Inhaltserstellung ist ein fortlaufender und kollaborativer Prozess. Der Zweck von Timewarp besteht darin, Autorinnen und Autoren zu ermöglichen, die veröffentlichte Website im Laufe der Zeit zu verfolgen, um zu verstehen, wie sich der Inhalt verändert hat. Diese Funktion verwendet die Seitenversionen, um den Zustand der Veröffentlichungsumgebung zu bestimmen.

* Das System sucht nach der Seitenversion, die zum ausgewählten Zeitpunkt aktiv war.
   * Die Seitenversion wurde *vor* dem in Timewarp ausgewählten Zeitpunkt erstellt/aktiviert.
* Wenn Sie zu einer inzwischen gelöschten Seite navigieren, wird diese ebenfalls gerendert, sofern die alten Versionen der Seite nach wie vor im Repository verfügbar sind.
* Wenn keine veröffentlichte Version gefunden wird, kehrt Timewarp zum aktuellen Status der Seite in der Autorenumgebung zurück (um eine Fehler-/404-Seite zu vermeiden, die dazu führen würde, dass Sie nicht weiter browsen können).

### Verwenden von Timewarp {#using-timewarp}

Timewarp ist ein [Modus](/help/sites-authoring/author-environment-tools.md#page-modes) des Seiteneditors. Um ihn zu starten, aktivieren Sie ihn einfach wie jeden anderen Modus.

1. Starten Sie den Editor für die Seite, auf der Timewarp ausgeführt werden soll, und wählen Sie in der Modusauswahl **Timewarp** aus.

   ![Timewarp in der Modusauswahl auswählen](assets/wwpv-01.png)

1. Legen Sie im Dialogfeld ein Zieldatum und eine Uhrzeit fest und klicken Sie auf **Datum einstellen**. Wenn Sie keine Zeit festlegen, wird standardmäßig die aktuelle Zeit eingestellt.

   ![Datum einstellen](assets/wwpv-02.png)

1. Die Seite wird basierend auf dem festgelegten Datum angezeigt. Der Timewarp-Modus ist durch die blaue Statusleiste am oberen Fensterrand gekennzeichnet. Verwenden Sie die Links in der Statusleiste, um ein neues Zieldatum auszuwählen oder den Timewarp-Modus zu verlassen.

   ![Timewarp-Indikator](assets/wwpv-03.png)

### Timewarp-Beschränkungen {#timewarp-limitations}

Timewarp bemüht sich nach Kräften, eine Seite zu einem bestimmten Zeitpunkt zu reproduzieren. Aufgrund der Komplexität der kontinuierlichen Bearbeitung von Inhalten in AEM ist dies jedoch nicht immer möglich. Diese Einschränkungen sollten bei der Verwendung von Timewarp beachtet werden.

* **Timewarp arbeitet auf der Grundlage der veröffentlichtenSeiten**: Timewarp funktioniert nur dann vollständig, wenn Sie die Seite bereits veröffentlicht haben. Andernfalls zeigt Timewarp die aktuelle Seite in der Autorenumgebung an.
* **Timewarp verwendet Seitenversionen**: Wenn Sie zu einer inzwischen aus dem Repository gelöschten Seite navigieren, wird diese ebenfalls korrekt wiedergegeben, sofern die alten Versionen der Seite noch im Repository verfügbar sind.
* **Entfernte Versionen wirken sich auf Timewarp**: Wenn Versionen aus dem Repository entfernt wurden, kann Timewarp die korrekte Ansicht nicht anzeigen.

* **Timewarp ist schreibgeschützt**: Sie können die alte Version der Seite nicht bearbeiten. Sie kann nur angezeigt werden. Wenn Sie die ältere Version wiederherstellen möchten, müssen Sie diesen Vorgang über [Wiederherstellen](#reverting-to-a-page-version) manuell ausführen.

* **Timewarp basiert nur auf dem Seiteninhalt**: Die Ansicht unterscheidet sich von der ursprünglichen Ansicht, wenn Elemente für das Rendern der Website geändert wurden, da diese Elemente nicht im Repository versioniert werden. Zu diesen Elementen gehören u. a. Code, CSS, Assets/Bilder.

>[!CAUTION]
>
>Timewarp wurde als Tool entwickelt, um Autoren beim Verstehen und Erstellen ihres Inhalts zu unterstützen. Es ist nicht als Prüfprotokoll oder zu rechtlichen Zwecken gedacht.
