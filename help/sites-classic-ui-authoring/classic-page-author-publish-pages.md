---
title: Veröffentlichen von Seiten
seo-title: Veröffentlichen von Seiten
description: Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, muss dieser auf der öffentlichen Website verfügbar gemacht werden.
seo-description: Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, muss dieser auf der öffentlichen Website verfügbar gemacht werden.
uuid: ab5ffc59-1c41-46fe-904e-9fc67d7ead04
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 46d6bde0-8645-4cff-b79c-8e1615ba4ed4
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50

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
   >  Dies sind die primären Begriffe für die Aktionen, mit denen Ihre Inhalte in Ihrer Veröffentlichungsumgebung öffentlich verfügbar gemacht werden (oder nicht).
   >
   >
* **Aktivieren/Deaktivieren**
   >  Diese Begriffe sind gleichbedeutend mit Veröffentlichung/Rückgängigmachen der Veröffentlichung.
   >
   >
* **Wiederholen/Replikation**
   >  Dies sind die technischen Begriffe, die die Datenbewegung (z. B. Seiteninhalt, Dateien, Code, Benutzerkommentare) von einer Umgebung in eine andere beschreiben, z. B. wenn Benutzerkommentare veröffentlicht oder rückgängig repliziert werden.
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

* [Über die Websites-Konsole](#activating-a-page-from-the-websites-console)
* [Über den Sidekick auf der Seite selbst](#activating-a-page-from-sidekick)

>[!NOTE]
>
>Mit [Tree aktivieren](#howtoactivateacompletesectiontreeofyourwebsite) in der Tools-Konsole können Sie auch eine Unterbaumstruktur mit mehreren Seiten aktivieren.

### Activating a Page from the Websites Console {#activating-a-page-from-the-websites-console}

Sie können Seiten in der Konsole „Websites“ aktivieren. Nachdem Sie eine Seite geöffnet und die zugehörigen Inhalte geändert haben, kehren Sie zur Konsole „Websites“ zurück:

1. Wählen Sie in der Konsole „Websites“ die zu aktivierende Seite.
1. Wählen Sie entweder im oberen Menü oder im Dropdown-Menü für das ausgewählte Seitenelement die Option **Aktivieren**.

   Um den Inhalt einer Seite und alle zugehörigen Unterseiten zu aktivieren, verwenden Sie die [**Konsole Tools **](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Gegebenenfalls werden Sie von AEM aufgefordert, alle Assets zu aktivieren bzw. zu reaktivieren, die mit der Seite verknüpft sind. Sie können die Aktivierung der Assets steuern, indem Sie die zugehörigen Kontrollkästchen aktivieren bzw. deaktivieren.

1. Gegebenenfalls werden Sie von AEM aufgefordert, alle Assets zu aktivieren bzw. zu reaktivieren, die mit der Seite verknüpft sind. Sie können die Aktivierung der Assets steuern, indem Sie die zugehörigen Kontrollkästchen aktivieren bzw. deaktivieren.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. Die ausgewählten Inhalte werden von AEM WCM aktiviert. Die veröffentlichten Seiten werden in der [Websites-Konsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (grün markiert) zusammen mit Angaben über den Benutzer, der den Inhalt aktiviert hat, sowie Datum und Uhrzeit der Aktivierung angezeigt.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Activating a Page from Sidekick {#activating-a-page-from-sidekick}

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

1. Öffnen Sie in der Websites-Konsole das Menü **Aktivieren** und wählen Sie die Option **Später aktivieren**.
1. In the dialog that opens you provide the date and time for activation and click **OK**. This creates a version of the page that is activated at the specified time.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

Die Wahl von „Später aktivieren“ startet einen Workflow zur Aktivierung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Wahl von „Später deaktivieren“ einen Workflow zur Deaktivierung der Seite zum angegebenen Zeitpunkt.

Wenn Sie diese Aktivierung/Deaktivierung abbrechen möchten, gehen Sie zur [Workflow-Konsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd), um den entsprechenden Workflow zu beenden.

### Später deaktivieren {#deactivate-later}

So planen Sie die Deaktivierung einer Seite für einen späteren Zeitpunkt:

1. In the Website console, go to the **Deactivate** menu, and select **Deactivate later**.

1. In the dialog that opens you provide the date and time for deactivation and click **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

Die Wahl von **Später deaktivieren** startet einen Workflow zur Deaktivierung der Seite zum angegebenen Zeitpunkt.

Wenn Sie diese Deaktivierung abbrechen möchten, gehen Sie zur [Workflow-Konsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd), um den entsprechenden Workflow zu beenden.

## Aktivieren bzw. Deaktivieren zu einer festgelegten Zeit (Einschalt- bzw. Ausschaltzeit) {#scheduled-activation-deactivation-on-off-time}

Über die Optionen **Einschaltzeit** und **Ausschaltzeit** können Sie Zeiten wählen, zu denen eine Seite veröffentlicht bzw. ihre Veröffentlichung rückgängig gemacht werden soll. Diese Optionen können in den [Seiteneigenschaften](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) definiert werden.

### Bestimmen des Seitenveröffentlichungsstatus {#determining-page-publication-status-classic-ui}

Der Status ist in der Konsole [Websites](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) sichtbar. Die Farben kennzeichnen den Veröffentlichungsstatus.

## Aktivieren einer kompletten Baumstruktur der Website {#activating-a-complete-section-tree-of-your-website}

Von der Registerkarte **Websites** aus können Sie einzelne Seiten aktivieren. Wenn Sie allerdings eine große Anzahl von Inhaltsseiten erstellt bzw. aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion den gesamten Baum zu aktivieren. Sie können auch einen Probelauf durchführen, um eine Aktivierung zu emulieren und die Seiten hervorzuheben, die aktiviert werden würden.

1. Open the **Tools** console by selecting it from the **Welcome** page and then double-click **Replication** to open the console ( `https://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. Klicken Sie in der **Replikations-Konsole** auf **Tree aktivieren**.

   The following window ( `https://localhost:4502/etc/replication/treeactivation.html`) will be displayed.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Enter the **Start Path**. This specifies the path to the root of the section you want to activate (publish). This page and all pages underneath are considered for activation (or used in the emulation if a Dry Run is selected).
1. Aktivieren Sie je nach Bedarf die Auswahlkriterien:

   * **Nur geänderte**: nur Seiten aktivieren, die geändert wurden.
   * **Nur aktivierte**: nur Seiten aktivieren, die bereits vorher aktiviert waren. Dies stellt eine Art von Reaktivierung dar.
   * **Deaktivierte ignorieren**: alle deaktivierten Seiten ignorieren.

1. Wählen Sie die gewünschte Aktion:

   1. Select **Dry Run** if you want to check which pages *would* be activated. This is only an emulation, no pages will be activated.

   1. Select **Activate** if you want to activate the pages.
