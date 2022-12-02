---
title: Veröffentlichen von Seiten
seo-title: Publishing Pages
description: Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, muss dieser auf der öffentlichen Website verfügbar gemacht werden.
seo-description: Once you have created and reviewed your content on the author environment, the goal is to make it available on your public website.
uuid: ab5ffc59-1c41-46fe-904e-9fc67d7ead04
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 46d6bde0-8645-4cff-b79c-8e1615ba4ed4
docset: aem65
exl-id: 3f6aa06e-b5fd-4ab0-9ecc-14250cb3f55e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 100%

---

# Veröffentlichen von Seiten{#publishing-pages}

Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, muss dieser auf der öffentlichen Website (der Veröffentlichungsumgebung) verfügbar gemacht werden.

Dies wird als Veröffentlichung einer Seite bezeichnet. Wenn Sie eine Seite aus der Veröffentlichungsumgebung entfernen, wird dies als Rückgängigmachen der Veröffentlichung bezeichnet. Während der Veröffentlichung und des Rückgängigmachens der Veröffentlichung bleibt die Seite so lange in der Bearbeitungsumgebung verfügbar und kann geändert werden, bis Sie sie löschen.

Sie können eine Seite auch sofort oder zu einem vordefinierten künftigen Zeitpunkt (Datum/Uhrzeit) veröffentlichen bzw. ihre Veröffentlichung rückgängig machen.

>[!NOTE]
>
>Manche Begriffe im Zusammenhang mit dem Veröffentlichen können leicht verwechselt werden:
>
>* **Veröffentlichen/Veröffentlichung rückgängig machen**
   >  Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungsumgebung verfügbar machen (oder dies rückgängig machen).
>
>* **Aktivieren/Deaktivieren**
   >  Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
>
>* **Replizieren/Replikation**
   >  Dies sind technische Begriffe, die für die Verschiebung von Daten (z. B. Seiteninhalten, Dateien, Code, Benutzerkommentaren) zwischen Umgebungen verwendet werden, z. B. beim Veröffentlichen oder Zurückreplizieren von Benutzerkommentaren.
>


>[!NOTE]
>
>Wenn Sie nicht über die erforderlichen Berechtigungen für das Veröffentlichen einer bestimmten Seite verfügen:
>
>* Ein Workflow wird ausgelöst, der die entsprechende Person über Ihre Veröffentlichungsanfrage informiert.
>* Eine Meldung wird (für kurze Zeit) angezeigt, in der Sie darüber informiert werden.
>


## Veröffentlichen einer Seite {#publishing-a-page}

Es gibt zwei Möglichkeiten, eine Seite zu veröffentlichen:

* [Mit der Websites-Konsole](#activating-a-page-from-the-websites-console)
* [Mit dem Sidekick auf der Seite selbst](#activating-a-page-from-sidekick)

>[!NOTE]
>
>Mit [Tree aktivieren](#howtoactivateacompletesectiontreeofyourwebsite) in der Tools-Konsole können Sie auch eine Unterbaumstruktur mit mehreren Seiten aktivieren.

### Aktivieren einer Seite in der Websites-Konsole {#activating-a-page-from-the-websites-console}

Sie können Seiten in der Websites-Konsole aktivieren. Nachdem Sie eine Seite geöffnet und die zugehörigen Inhalte geändert haben, kehren Sie zur Konsole „Websites“ zurück:

1. Wählen Sie in der Konsole „Websites“ die zu aktivierende Seite.
1. Wählen Sie entweder im oberen Menü oder im Dropdown-Menü für das ausgewählte Seitenelement die Option **Aktivieren**.

   Um den Inhalt einer Seite und alle zugehörigen Unterseiten zu aktivieren, verwenden Sie die [**Tools**-Konsole](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Gegebenenfalls werden Sie von AEM aufgefordert, alle Assets zu aktivieren bzw. zu reaktivieren, die mit der Seite verknüpft sind. Sie können die Aktivierung der Assets steuern, indem Sie die zugehörigen Kontrollkästchen aktivieren bzw. deaktivieren.

1. Gegebenenfalls werden Sie von AEM aufgefordert, alle Assets zu aktivieren bzw. zu reaktivieren, die mit der Seite verknüpft sind. Sie können die Aktivierung der Assets steuern, indem Sie die zugehörigen Kontrollkästchen aktivieren bzw. deaktivieren.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. Die ausgewählten Inhalte werden von AEM WCM aktiviert. Die veröffentlichten Seiten werden in der [Websites-Konsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (grün markiert) zusammen mit Angaben über den Benutzer, der den Inhalt aktiviert hat, sowie Datum und Uhrzeit der Aktivierung angezeigt.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Aktivieren einer Seite mithilfe des Sidekicks {#activating-a-page-from-sidekick}

Sie können eine Seite außerdem aktivieren, wenn Sie sie zur Bearbeitung geöffnet haben.

Dazu können Sie, nachdem Sie eine Seite geöffnet und die zugehörigen Inhalte bearbeitet haben, folgende Aktionen durchführen

1. Wählen Sie im Sidekick die Registerkarte **Seite**.
1. Klicken Sie auf **Seite aktivieren**.
Oben rechts im Fenster wird eine Meldung angezeigt, die die Aktivierung der Seite bestätigt.

## Veröffentlichen einer Seite rückgängig machen {#unpublishing-a-page}

Um eine Seite aus der Veröffentlichungsumgebung zu entfernen, deaktivieren Sie den entsprechenden Inhalt.

So deaktivieren Sie eine Seite:

1. Wählen Sie in der Konsole „Websites“ die zu deaktivierende Seite.
1. Wählen Sie entweder im oberen Menü oder im Dropdown-Menü für das ausgewählte Seitenelement die Option **Deaktivieren**. Sie werden aufgefordert, die Deaktivierung zu bestätigen.

   ![screen_shot_2012-02-08at14859pm](assets/screen_shot_2012-02-08at14859pm.png)

1. Aktualisieren Sie die [Websites-Konsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). Der Inhalt wird rot hervorgehoben, wodurch angezeigt wird, dass er nicht mehr veröffentlicht ist.

   ![screen_shot_2012-02-08at15018pm](assets/screen_shot_2012-02-08at15018pm.png)

## Später aktivieren/deaktivieren {#activate-deactivate-later}

### Später aktivieren {#activate-later}

So planen Sie die Aktivierung einer Seite für einen späteren Zeitpunkt:

1. Öffnen Sie in der Websites-Konsole das Menü **Aktivieren** und wählen Sie die Option **Später aktivieren** aus.
1. Geben Sie in dem daraufhin angezeigten Dialogfeld Datum und Uhrzeit für die Aktivierung ein und klicken Sie auf **OK**. Dadurch wird eine Version der Seite erstellt, die zum angegebenen Zeitpunkt aktiviert wird.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

Die Wahl von „Später aktivieren“ startet einen Workflow zur Aktivierung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Wahl von „Später deaktivieren“ einen Workflow zur Deaktivierung der Seite zum angegebenen Zeitpunkt.

Wenn Sie diese Aktivierung/Deaktivierung abbrechen möchten, gehen Sie zur [Workflow-Konsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd), um den entsprechenden Workflow zu beenden.

### Später deaktivieren {#deactivate-later}

So planen Sie die Deaktivierung einer Seite für einen späteren Zeitpunkt:

1. Öffnen Sie in der Websites-Konsole das Menü **Deaktivieren** und wählen Sie die Option **Später deaktivieren** aus.

1. Geben Sie in dem daraufhin angezeigten Dialogfeld Datum und Uhrzeit für die Deaktivierung ein und klicken Sie auf **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

Mit **Später deaktivieren** wird ein Workflow zur Deaktivierung der Seite zum angegebenen Zeitpunkt gestartet.

Wenn Sie diese Deaktivierung abbrechen möchten, gehen Sie zur [Workflow-Konsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd), um den entsprechenden Workflow zu beenden.

## Aktivieren bzw. Deaktivieren zu einer festgelegten Zeit (Einschalt- bzw. Ausschaltzeit) {#scheduled-activation-deactivation-on-off-time}

Über die Optionen **Einschaltzeit** und **Ausschaltzeit** können Sie Zeiten auswählen, zu denen eine Seite veröffentlicht bzw. ihre Veröffentlichung rückgängig gemacht werden soll. Diese Optionen können in den [Seiteneigenschaften](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) definiert werden.

### Bestimmen des Seitenveröffentlichungsstatus {#determining-page-publication-status-classic-ui}

Der Status ist in der Konsole [Websites](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) sichtbar. Die Farben kennzeichnen den Veröffentlichungsstatus.

## Aktivieren einer kompletten Baumstruktur der Website {#activating-a-complete-section-tree-of-your-website}

Von der Registerkarte **Websites** aus können Sie einzelne Seiten aktivieren. Wenn Sie allerdings eine große Anzahl von Inhaltsseiten erstellt bzw. aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion den gesamten Baum zu aktivieren. Sie können auch einen Probelauf durchführen, um eine Aktivierung zu emulieren und die Seiten hervorzuheben, die aktiviert werden würden.

1. Öffnen Sie die **Tools**-Konsole, indem Sie sie auf dem **Startbildschirm** auswählen, und doppelklicken Sie dann auf **Replikation**, um die Konsole zu öffnen (`https://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. Klicken Sie in der Konsole **Replikation** auf **Tree aktivieren**.

   Das folgende Fenster (`https://localhost:4502/etc/replication/treeactivation.html`) wird angezeigt.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Geben Sie den **Startpfad** ein. Dies ist der Pfad zum Stammverzeichnis des Abschnitts, den Sie aktivieren (veröffentlichen) möchten. Diese Seite und alle darunter liegenden Seiten werden bei der Aktivierung (bzw. bei der Emulation, falls ein Probelauf ausgewählt wurde) berücksichtigt.
1. Aktivieren Sie je nach Bedarf die Auswahlkriterien:

   * **Nur geänderte**: nur Seiten aktivieren, die geändert wurden.
   * **Nur aktivierte**: nur Seiten aktivieren, die bereits vorher aktiviert waren. Dies stellt eine Art von Reaktivierung dar.
   * **Deaktivierte ignorieren**: alle deaktivierten Seiten ignorieren.

1. Wählen Sie die gewünschte Aktion:

   1. Wählen Sie **Probelauf** aus, wenn Sie überprüfen möchten, welche Seiten aktiviert *würden*. Dabei handelt es sich lediglich um eine Emulation, bei der keine Seiten tatsächlich aktiviert werden.

   1. Wählen Sie **Aktivieren** aus, wenn die Seiten aktiviert werden sollen.
