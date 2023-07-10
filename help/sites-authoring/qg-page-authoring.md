---
title: Kurzanleitung zur Seitenbearbeitung (Authoring)
seo-title: Quick Guide to Authoring Pages
description: Kurzanleitung zu den wichtigsten Aktionen beim Bearbeiten von Seiteninhalten auf hoher Ebene
seo-description: A quick, high-level guide to the key actions of authoring page content
uuid: ef7ab691-f80d-4eeb-9f4a-afbf1bc83669
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 2d35a2a4-0c8c-4b16-99a6-c6e6d66446dc
docset: aem65
exl-id: a7e16555-9bbe-4da2-817c-4495a0193f3f
source-git-commit: d045fc1ac408f992d594a4cb68d1c4eeae2b0de1
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 56%

---

# Kurzanleitung zur Seitenbearbeitung (Authoring){#quick-guide-to-authoring-pages}

Diese Verfahren dienen als schnelle (allgemeine) Anleitung zu den wichtigsten Aktionen beim Bearbeiten von Seiteninhalten in AEM.

Sie:

* sind nicht als umfassende Abdeckung vorgesehen.
* Stellen Sie Links zur ausführlichen Dokumentation bereit.

Genauere Informationen zur Bearbeitung mit AEM finden Sie unter:

* [Erste Schritte für Autoren](/help/sites-authoring/first-steps.md)
* [Bearbeiten von Seiten (Authoring)](/help/sites-authoring/page-authoring.md)

## Tipps {#a-few-quick-hints}

Bevor Sie sich einen Überblick über die Besonderheiten verschaffen, hier eine kleine Sammlung von allgemeinen Tipps und Hinweisen, die es wert sind, beachtet zu werden.

### Sites-Konsole {#sites-console}

* **Erstellen**

   * Diese Schaltfläche ist in vielen Konsolen verfügbar - die angezeigten Optionen sind kontextsensitiv und können je nach Szenario variieren.

* Neuanordnen von Seiten in einem Ordner

   * Dies kann in [Listenansicht](/help/sites-authoring/basic-handling.md#list-view). Die Änderungen werden angewendet und in anderen Ansichten angezeigt.

#### Bearbeiten von Seiten {#page-authoring}

* Navigieren per Links

   * ***Links sind nicht für die Navigation verfügbar*** wann Sie **Bearbeiten** -Modus. Um mit Links zu navigieren, müssen Sie [Seitenvorschau](/help/sites-authoring/editing-content.md#previewing-pages) entweder:

      * [Vorschaumodus](/help/sites-authoring/editing-content.md#preview-mode)
      * [Als veröffentlicht anzeigen](/help/sites-authoring/editing-content.md#view-as-published)

* Versionen werden nicht aus dem Seiteneditor gestartet/erstellt. Dies erfolgt jetzt über die Sites-Konsole (über **Erstellen** oder [Zeitleiste](/help/sites-authoring/basic-handling.md#timeline) für die jeweilige Ressource).   

>[!NOTE]
>
>Es gibt mehrere Tastaturbefehle, die die Bearbeitung vereinfachen können.
>
>* [Tastaturbefehle bei der Seitenbearbeitung](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
>* [Tastaturbefehle für Konsolen](/help/sites-authoring/keyboard-shortcuts.md)
>

### Suchen nach Seiten {#finding-your-page}

Es gibt verschiedene Möglichkeiten, eine Seite zu finden: Sie können navigieren und/oder suchen:

1. Öffnen Sie die **Sites** -Konsole (mithilfe der **Sites** in der [Globale Navigation](/help/sites-authoring/basic-handling.md#global-navigation)) - Wird ausgelöst (Dropdown), wenn Sie den Adobe Experience Manager-Link (oben links) auswählen.

1. Navigieren Sie durch Tippen/Klicken auf die entsprechende Seite in der Baumstruktur nach unten. Die Darstellung der Seitenressourcen ist von der verwendeten Ansicht abhängig: [Karte, Liste oder Spalte](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources):

   ![screen_shot_2018-03-21at160214](assets/screen_shot_2018-03-21at160214.png)

1. Navigieren Sie in der Baumstruktur nach oben, indem Sie [die Breadcrumbs in der Kopfzeile](/help/sites-authoring/basic-handling.md#theheaderwithbreadcrumbs) verwenden. Dies ermöglicht es Ihnen, zum ausgewählten Pfad zurückzukehren:

   ![qgtap-01](assets/qgtap-01.png)

1. Sie können auch nach einer Seite [suchen](/help/sites-authoring/search.md). Sie können Ihre Seite aus den angezeigten Ergebnissen auswählen.

   ![qgtap-03](assets/qgtap-03.png)

### Erstellen einer neuen Seite {#creating-a-new-page}

nach [Erstellen einer Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page):

1. [Navigieren zum Speicherort](#finding-your-page) wo Sie die Seite erstellen möchten.
1. Verwenden Sie die **Erstellen** und wählen Sie **Seite** aus der Liste:

   ![qgtap-02](assets/qgtap-02.png)

1. Dadurch wird der Assistent geöffnet, der Sie durch das Erfassen der benötigten Informationen führt, wenn [Erstellen einer neuen Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page). Befolgen Sie die Anweisungen auf dem Bildschirm.

### Auswählen Ihrer Seite für weitere Aktionen {#selecting-your-page-for-further-action}

Sie können eine Seite auswählen, damit Sie Maßnahmen ergreifen können. Wenn Sie eine Seite auswählen, wird die Symbolleiste automatisch aktualisiert, sodass die für diese Ressource relevanten Aktionen angezeigt werden.

Wie Sie eine Seite auswählen, hängt davon ab, welche Ansicht Sie in der Konsole verwenden:

1. Spaltenansicht:

   * Tippen/klicken Sie auf die Miniatur für die gewünschte Ressource. Auf der Miniaturansicht wird die ausgewählte Ressource durch ein Häkchen gekennzeichnet

1. Listenansicht:

   * Tippen/klicken Sie auf die Miniatur für die gewünschte Ressource. Auf der Miniaturansicht wird die ausgewählte Ressource durch ein Häkchen gekennzeichnet

1. Kartenansicht:

   * Auswahlmodus aufrufen durch [Auswahl der erforderlichen Ressource](/help/sites-authoring/basic-handling.md#viewingandselectingyourresources) mit:

      * Mobilgerät: Tippen und halten
      * Desktop: [Schnellaktion](/help/sites-authoring/basic-handling.md#quick-actions) – Häkchen:

   ![screen_shot_2018-03-21at160503](assets/screen_shot_2018-03-21at160503.png)

   * Auf der Karte wird die ausgewählte Seite durch ein Häkchen gekennzeichnet.

   >[!NOTE]
   >
   >Wenn Sie sich im Auswahlmodus befinden, ändert sich das Symbol **Auswählen** (ein Häkchen) in das Symbol **Deaktivieren** (ein Kreuz).

### Schnellaktionen (nur Kartenansicht/Desktop) {#quick-actions-card-view-desktop-only}

[Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions) sind verfügbar:

1. [Navigieren Sie zu der Seite,](#finding-your-page) mit der Sie eine Aktion ausführen möchten.
1. Zeigen Sie mit der Maus auf die Karte für die gewünschte Ressource. Die Schnellaktionen werden angezeigt: 

   ![screen_shot_2018-03-21at160503-1](assets/screen_shot_2018-03-21at160503-1.png)

### Bearbeiten des Seiteninhalts {#editing-your-page-content}

1. [Navigieren Sie zu der Seite](#finding-your-page), die Sie bearbeiten möchten.
1. [Öffnen Sie die zu bearbeitende Seite](/help/sites-authoring/managing-pages.md#opening-a-page-for-editing) über das Symbol „Bearbeiten“ (Bleistift):

   ![screen_shot_2018-03-21at160607](assets/screen_shot_2018-03-21at160607.png)

   Darauf können Sie zugreifen, indem Sie wahlweise Folgendes verwenden:

   * [Schnellzugriffe (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die jeweilige Ressource
   * Symbolleiste, wenn die [Seite ausgewählt wurde](#selectiingyourpageforfurtheraction)

1. Wenn der Editor geöffnet wird, haben Sie folgende Möglichkeiten:

   * [Fügen Sie der Seite eine neue Komponente hinzu](/help/sites-authoring/editing-content.md#inserting-a-component), indem Sie:

      * Öffnen des Seitenbereichs
      * Wählen Sie die Registerkarte Komponenten (die [Komponenten-Browser](/help/sites-authoring/author-environment-tools.md#components-browser))
      * Ziehen der erforderlichen Komponente auf Ihre Seite.

     Der Seitenbereich kann mit folgendem Symbol geöffnet (und geschlossen) werden:

     ![Seitenbereich öffnen](do-not-localize/screen_shot_2018-03-21at160738.png)

   * [Inhalt einer vorhandenen Komponente bearbeiten](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) auf der Seite:

      * Öffnen Sie die Komponenten-Symbolleiste durch Tippen oder Klicken. Verwenden Sie die **Bearbeiten** (Bleistift), um das Dialogfeld zu öffnen.
      * Öffnen Sie den Editor für die Bearbeitung an Ort und Stelle für die Komponente durch Tippen und Halten oder durch einen doppelten langsamen Klick. Die verfügbaren Aktionen werden angezeigt (bei einigen Komponenten ist dies eine eingeschränkte Auswahl).
      * Um alle verfügbaren Aktionen anzuzeigen, gehen Sie wie folgt in den Vollbildmodus:

     ![Vollbildmodus](do-not-localize/screen_shot_2018-03-21at160706.png)

   * [Die Eigenschaften einer vorhandenen Komponente konfigurieren](/help/sites-authoring/editing-content.md#component-edit-dialog)

      * Öffnen Sie die Komponenten-Symbolleiste durch Tippen oder Klicken. Verwenden Sie die **Konfigurieren** (Schraubenschlüssel), um das Dialogfeld zu öffnen.

   * [Verschieben einer Komponente](/help/sites-authoring/editing-content.md#moving-a-component) Entweder:

      * Ziehen Sie die gewünschte Komponente an die neue Position.
      * Öffnen Sie die Komponenten-Symbolleiste durch Tippen oder Klicken. Verwenden Sie die Symbole **Ausschneiden** und **Einfügen** nach Bedarf.

   * [Kopieren (und Einfügen)](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) eine Komponente:

      * Öffnen Sie die Komponenten-Symbolleiste durch Tippen oder Klicken. Verwenden Sie die Symbole **Kopieren** und **Einfügen** nach Bedarf.

   >[!NOTE]
   >
   >Sie können Komponenten auf derselben oder einer anderen Seite **einfügen**. Wenn Sie Komponenten auf einer anderen Seite einfügen, die bereits vor dem Ausschneiden und Kopieren geöffnet war, muss diese Seite aktualisiert werden.

   * Eine Komponente [löschen](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste):

      * Öffnen Sie die Komponenten-Symbolleiste durch Tippen oder Klicken. Verwenden Sie dann das Symbol **Löschen**.

   * [Hinzufügen von Anmerkungen](/help/sites-authoring/annotations.md#annotations) auf der Seite:

      * Wählen Sie die **Anmerken** -Modus (Sprechblasensymbol). Hinzufügen von Anmerkungen mithilfe der **Anmerkung hinzufügen** (Pluszeichen). Beenden Sie den Anmerkungsmodus mit dem X oben rechts.

     ![Anmerken](do-not-localize/screen_shot_2018-03-21at160813.png)

   * [Seitenvorschau](/help/sites-authoring/editing-content.md#preview-mode) (um zu sehen, wie es in der Veröffentlichungsumgebung angezeigt wird)

      * Auswählen **Vorschau** aus der Symbolleiste.

   * Kehren Sie mit dem **Bearbeiten** Dropdown-Auswahl.

   >[!NOTE]
   >
   >Um mithilfe von Links im Inhalt zu navigieren, müssen Sie [Vorschaumodus](/help/sites-authoring/editing-content.md#preview-mode).

### Bearbeiten der Seiteneigenschaften {#editing-the-page-properties}

Es gibt zwei (wesentliche) Methoden für [Bearbeiten von Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md):

* In der Konsole **Sites**:

   1. [Navigieren zur Seite](#finding-your-page) Sie veröffentlichen möchten.
   1. Wählen Sie die **Eigenschaften** Symbol aus:

      * [Schnellzugriffe (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die jeweilige Ressource
      * Symbolleiste, wenn die [Seite ausgewählt wurde](#selectiingyourpageforfurtheraction)

  ![screen_shot_2018-03-21at160850](assets/screen_shot_2018-03-21at160850.png)

   1. Die Seiteneigenschaften werden angezeigt. Sie können nach Bedarf Aktualisierungen vornehmen. Speichern Sie diese anschließend, um sie beizubehalten.

* Wann [Bearbeiten einer Seite](#editing-your-page-content):

   1. Öffnen Sie die **Seiteninformationen** Menü.
   1. Auswählen **Eigenschaften öffnen** , um das Dialogfeld zum Bearbeiten der Eigenschaften zu öffnen.

  ![screen_shot_2018-03-21at160920](assets/screen_shot_2018-03-21at160920.png)

### Veröffentlichen Ihrer Seite (oder Rückgängigmachen der Veröffentlichung) {#publishing-your-page-or-unpublishing}

Es gibt zwei Hauptmethoden von [Veröffentlichen einer Seite](/help/sites-authoring/publishing-pages.md) (und auch das Rückgängigmachen der Veröffentlichung):

* In der Konsole **Sites**:

   1. [Navigieren zur Seite](#finding-your-page) Sie veröffentlichen möchten.
   1. Wählen Sie das Symbol **Quick Publish** aus, indem Sie wahlweise Folgendes verwenden:

      * [Schnellzugriffe (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die jeweilige Ressource
      * Symbolleiste, wenn die [Seite ausgewählt wurde](#selectiingyourpageforfurtheraction) (ermöglicht auch Zugriff auf [Später veröffentlichen](/help/sites-authoring/publishing-pages.md#main-pars-title-12)).

  ![screen_shot_2018-03-21at160957](assets/screen_shot_2018-03-21at160957.png)

* Wann [Bearbeiten einer Seite](#editing-your-page-content):

   1. Öffnen Sie die **Seiteninformationen** Menü.
   1. Auswählen **Seite veröffentlichen**.

  ![screen_shot_2018-03-21at161026](assets/screen_shot_2018-03-21at161026.png)

* Das Rückgängigmachen der Veröffentlichung einer Seite in der Konsole kann nur über die Option **Veröffentlichung verwalten** erfolgen, die nur in der Symbolleiste verfügbar ist (nicht über Schnellaktionen).

  Die **Seite rückgängig machen** weiterhin über die Option **Seiteninformationen** im Editor.

  ![screen_shot_2018-03-21at161059](assets/screen_shot_2018-03-21at161059.png)

  Siehe [Veröffentlichen von Seiten](/help/sites-authoring/publishing-pages.md#unpublishing-pages) für weitere Informationen.

### Verschieben, Kopieren und Einfügen oder Löschen Ihrer Seite {#move-copy-and-paste-or-delete-your-page}

Diese Aktionen können alle durch Folgendes ausgelöst werden:

1. [Navigieren zur Seite](#finding-your-page) Sie verschieben, kopieren, einfügen oder löschen möchten.
1. Wählen Sie das Symbol zum Kopieren (und dann Einfügen), Verschieben oder Löschen nach Bedarf aus, indem Sie eine der folgenden Aktionen durchführen:

   * [Schnellaktionen (nur Kartenansicht/Desktop)](#quick-actions-card-view-desktop-only) für die gewünschte Ressource.
   * Symbolleiste, wenn die [Seite ausgewählt wurde](#selecting-your-page-for-further-action)

   Anschließend abhängig von Ihrer Aktion:

   * Kopieren:

      * Navigieren Sie zum neuen Speicherort und fügen Sie ihn ein.

   * Verschieben:

      * Der Assistent wird geöffnet, um die zum Verschieben der Seite erforderlichen Informationen zu sammeln. Befolgen Sie die Anweisungen auf dem Bildschirm.

   * Löschen:

      * Sie werden aufgefordert, die Aktion zu bestätigen.

   >[!NOTE]
   >
   >Löschen ist nicht als Schnellaktion verfügbar.

### Sperren (und Entsperren) Ihrer Seite  {#locking-your-page-then-unlocking}

[Sperren einer Seite](/help/sites-authoring/editing-content.md#locking-a-page): Verhindert, dass andere Autoren daran arbeiten, während Sie dies tun. Das Symbol bzw. die Schaltfläche „Sperren“ (und „Entsperren“) ist verfügbar:

* Symbolleiste, wenn die [Seite ausgewählt wurde](#selecting-your-page-for-further-action)
* Die [Dropdown-Menü &quot;Seiteninformationen&quot;](#editing-the-page-properties) beim Bearbeiten einer Seite.
* Seitensymbolleiste beim Bearbeiten einer Seite (wenn die Seite gesperrt ist)

Beispielsweise sieht das Schloss-Symbol folgendermaßen aus:

![screen_shot_2018-03-21at161124](assets/screen_shot_2018-03-21at161124.png)

### Zugreifen auf Seitenverweise {#accessing-page-references}

[Schnellzugriff auf Verweise](/help/sites-authoring/author-environment-tools.md#references) zu einer Seite oder von einer Seite aus in der Verweisleiste verfügbar.

1. Wählen Sie die Option **Verweise** mithilfe des Symbolleistensymbols (vor oder nach dem [Auswählen Ihrer Seite](#selecting-your-page-for-further-action)):

   ![screen_shot_2018-03-21at161210](assets/screen_shot_2018-03-21at161210.png)

   Ein Liste von Verweistypen wird angezeigt:

   ![screen-shot_2019-03-05at114412](assets/screen-shot_2019-03-05at114412.png)

1. Tippen/klicken Sie auf den gewünschten Verweistyp, um weitere Details anzuzeigen und (bei Bedarf) weitere Aktionen auszuführen.

### Erstellen einer Seitenversion {#creating-a-version-of-your-page}

So erstellen Sie eine [Version](/help/sites-authoring/working-with-page-versions.md) Ihrer Seite:

1. Wählen Sie zum Öffnen der Zeitleiste die Option **[Zeitleiste](/help/sites-authoring/basic-handling.md#timeline)** mithilfe des Symbolleistensymbols (vor oder nach dem [Auswählen Ihrer Seite](#selecting-your-page-for-further-action)):

   ![screen_shot_2018-03-21at161355](assets/screen_shot_2018-03-21at161355.png)

1. Tippen oder klicken Sie unten rechts in der Spalte „Zeitleiste“ auf den Nach-oben-Pfeil, um weitere Schaltflächen einzublenden, darunter auch **Als Version speichern**.

   ![screen-shot_2019-03-05at114600](assets/screen-shot_2019-03-05at114600.png)

1. Wählen Sie **Als Version speichern**, gefolgt von **Erstellen**.

### Wiederherstellen/Vergleichen einer Seitenversion {#restoring-comparing-a-version-of-your-page}

Beim Wiederherstellen und/oder Vergleichen von Seitenversionen wird dasselbe grundlegende Verfahren eingesetzt:

1. Wählen Sie mithilfe des Symbolleistensymbols die Option **[Zeitleiste](/help/sites-authoring/basic-handling.md#timeline)** (vor oder nach dem [Auswählen Ihrer Seite](#selecting-your-page-for-further-action)):

   ![screen_shot_2018-03-21at161355-1](assets/screen_shot_2018-03-21at161355-1.png)

   Wenn eine Version Ihrer Seite bereits gespeichert wurde, wird sie in der Timeline aufgeführt.

1. Tippen/klicken Sie auf die Version, die Sie wiederherstellen möchten. Dadurch werden zusätzliche Aktionsschaltflächen angezeigt:

   * **Auf diese Version zurück**

      * Die Version wird wiederhergestellt.

   * **Unterschiede anzeigen**

      * Die Seite wird geöffnet und die Unterschiede (zwischen den beiden Versionen) werden hervorgehoben.
