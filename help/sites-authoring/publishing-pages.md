---
title: Veröffentlichen von Inhaltsseiten
description: Erfahren Sie, wie Sie Inhaltsseiten in Adobe Experience Manager 6.5 veröffentlichen.
exl-id: 61144bbe-6710-4cae-a63e-e708936ff360
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 95%

---

# Veröffentlichen von Seiten {#publishing-pages}

Nachdem Sie Ihren Inhalt in der Authoring-Umgebung erstellt und geprüft haben, muss dieser [auf der öffentlichen Website](/help/sites-authoring/author.md#concept-of-authoring-and-publishing) (der Publishing-Umgebung) verfügbar gemacht werden.

Dies wird als Publishing einer Seite bezeichnet. Wenn Sie eine Seite aus der Publishing-Umgebung entfernen möchten, wird dies als Aufheben der Veröffentlichung bezeichnet. Beim „Publishing“ und „Veröffentlichung aufheben“ bleibt die Seite in der Authoring-Umgebung für weitere Änderungen verfügbar, bis Sie diese löschen.

Sie können eine Seite auch sofort oder zu einem vordefinierten Datum/Zeitpunkt in der Zukunft veröffentlichen oder die Veröffentlichungen aufheben.

>[!NOTE]
>
>Bestimmte Begriffe im Zusammenhang mit Publishing sind leicht zu verwechseln:
>
>* **Veröffentlichen/Veröffentlichung rückgängig machen**
>  Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungsumgebung verfügbar machen (oder dies rückgängig machen).
>
>* **Aktivieren/Deaktivieren**
>  Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
>
>* **Replizieren/Replikation**
>  Dies sind die technischen Begriffe, die die Verschiebung von Daten (z. B. Seiteninhalt, Dateien, Code, Benutzerkommentare) von einer Umgebung in eine andere beschreiben, z. B. bei der Veröffentlichung oder umgekehrten Replizierung von Benutzerkommentaren.
>

>[!NOTE]
>
>Wenn Sie nicht über die erforderlichen Berechtigungen zum Veröffentlichen einer bestimmten Seite verfügen, dann:
>
>* wird ein Workflow ausgelöst, der die entsprechende Person über Ihre Veröffentlichungsanfrage informiert.
>* wurde dieser [Workflow möglicherweise angepasst](/help/sites-developing/workflows-models.md#main-pars-procedure-6fe6) von Ihrem Entwicklungsteam.
>* Sie werden in einer Mitteilung darüber informiert, dass der Workflow ausgelöst wurde.
>

## Veröffentlichen von Seiten {#publishing-pages-1}

Abhängig davon, wo Sie sich gerade befinden, können Sie Veröffentlichungen folgendermaßen vornehmen:

* [Im Seiten-Editor](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor)
* [In der Sites-Konsole](/help/sites-authoring/publishing-pages.md#publishing-from-the-console)

### Veröffentlichungen im Editor {#publishing-from-the-editor}

Wenn Sie eine Seite bearbeiten, kann sie direkt im Editor veröffentlicht werden.

1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Menü zu öffnen, und danach die Option **Seite veröffentlichen**.

   ![screen_shot_2018-03-21at152734](assets/screen_shot_2018-03-21at152734.png)

1. Je nachdem, ob die Seite Verweise enthält, die veröffentlicht werden müssen, geschieht Folgendes:

   * Die Seite wird direkt veröffentlicht, wenn keine Verweise veröffentlicht werden müssen.
   * Wenn die Seite Verweise enthält, die veröffentlicht werden müssen, werden diese im **Veröffentlichungsassistenten** aufgeführt und Sie können eine der folgenden Aktionen ausführen:

      * Geben Sie an, welche Assets, Tags usw. Sie mit der Seite veröffentlichen möchten, und wählen Sie **Veröffentlichen** aus, um den Vorgang abzuschließen.

      * Mit **Abbrechen** können Sie den Vorgang abbrechen.

   ![chlimage_1](assets/chlimage_1.png)

1. Mit **Veröffentlichen** wird die Seite in der Veröffentlichungsumgebung repliziert. Im Seiteneditor wird ein Hinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

   ![screen_shot_2018-03-21at152840](assets/screen_shot_2018-03-21at152840.png)

   Wird diese Seite in der Konsole dargestellt, ist der aktualisierte Veröffentlichungsstatus sichtbar.

   ![pp-01](assets/pp-01.png)

>[!NOTE]
>
>Im Editor kann nur eine teilweise Veröffentlichung vorgenommen werden, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

>[!NOTE]
>
>Seiten, auf die von [Aliase](/help/sites-authoring/editing-page-properties.md#advanced) im Editor kann nicht veröffentlicht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

### Veröffentlichungen über die Konsole {#publishing-from-the-console}

In der Sites-Konsole gibt es zwei Möglichkeiten zur Veröffentlichung:

* [Quick Publish](/help/sites-authoring/publishing-pages.md#quick-publish)
* [Veröffentlichung verwalten](/help/sites-authoring/publishing-pages.md#manage-publication)

#### Quick Publish {#quick-publish}

**Quick Publish** wird für einfache Fälle verwendet. Die ausgewählten Seiten werden damit sofort ohne weitere Interaktion veröffentlicht. Aus diesem Grund werden alle nicht-veröffentlichten Verweise ebenfalls automatisch veröffentlicht.

So veröffentlichen Sie eine Seite mit der Funktion „Quick Publish“:

1. Wählen Sie die gewünschten Seiten in der Sites-Konsole aus und klicken Sie auf die Schaltfläche **Quick Publish**.

   ![pp-02](assets/pp-02.png)

1. Bestätigen Sie im Dialogfeld „Schnell veröffentlichen“ die Veröffentlichung, indem Sie auf **Veröffentlichen** klicken, oder brechen Sie den Vorgang ab, indem Sie auf **Abbrechen** klicken. Beachten Sie, dass auch alle unveröffentlichten Verweise ebenfalls automatisch veröffentlicht werden.

   ![chlimage_1-1](assets/chlimage_1-1.png)

1. Bei der Veröffentlichung der Seite wird ein Warnhinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

>[!NOTE]
>
>Die Option „Quick Publish“ ermöglicht nur die teilweise Veröffentlichung, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

#### Veröffentlichung verwalten {#manage-publication}

**Veröffentlichung verwalten** bietet mehr Optionen als „Quick Publish“. Mit dieser Funktion können Sie auch untergeordnete Seiten einschließen, Verweise anpassen, alle nötigen Workflows starten und bei Bedarf zu einem späteren Zeitpunkt veröffentlichen.

So veröffentlichen Sie eine Seite bzw. machen ihre Veröffentlichung rückgängig mit „Veröffentlichung verwalten“:

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.

   ![pp-02-1](assets/pp-02-1.png)

1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Der erste Schritt, **Optionen** ermöglicht Folgendes:

   * Veröffentlichen Sie die ausgewählte Seite oder machen Sie die Veröffentlichung rückgängig.
   * Entscheiden Sie, ob Sie diese Aktion jetzt oder zu einem späteren Zeitpunkt durchführen möchten.

   Bei späterer Veröffentlichung wird ein Workflow gestartet, um die ausgewählte(n) Seite(n) zum angegebenen Zeitpunkt zu veröffentlichen. Umgekehrt startet „Veröffentlichung aufheben“ später einen Workflow zum Aufheben der Veröffentlichung der ausgewählte(n) Seite(n) zu einem angegebenen Zeitpunkt.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-administering/workflows.md), um den entsprechenden Workflow zu beenden.

   ![chlimage_1-2](assets/chlimage_1-2.png)

   Klicken Sie auf **Weiter**, um fortzufahren.

1. Im nächsten Schritt des Assistenten „Veröffentlichung verwalten“, **Umfang**, können Sie den Umfang der Veröffentlichung/der rückgängig gemachten Veröffentlichung definieren, wie z. B. das Einschließen von untergeordneten Seiten und/oder von Verweisen.

   ![screen_shot_2018-03-21at153354](assets/screen_shot_2018-03-21at153354.png)

   Mit der Schaltfläche **Inhalt hinzufügen** können Sie zusätzliche Seiten zur Liste der zu veröffentlichenden Seiten hinzufügen, falls Sie dies noch nicht vor dem Starten des Assistenten „Veröffentlichung verwalten“ getan haben.

   Durch Klicken auf die Schaltfläche „Inhalt hinzufügen“ wird der [Pfad-Browser](/help/sites-authoring/author-environment-tools.md#path-browser) gestartet, mit dem Inhalte ausgewählt werden können.

   Wählen Sie die gewünschten Seiten aus und klicken Sie dann auf **Auswählen**, um den Inhalt dem Assistenten hinzuzufügen, oder auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   Zurück im Assistenten können Sie ein Element in der Liste auswählen, um dessen weitere Optionen zu konfigurieren, z. B.:

   * Einschließen seiner untergeordneten Elemente.
   * Entfernen des Elements aus der Auswahl.
   * Verwalten seiner veröffentlichten Verweise

   ![pp-03](assets/pp-03.png)

   Durch Klicken auf **Untergeordnete Elemente einbeziehen** wird ein Dialogfeld geöffnet, in dem Sie folgende Möglichkeiten haben:

   * Nur unmittelbar untergeordnete Elemente einbeziehen.
   * Nur geänderte Seiten einbeziehen.
   * Nur bereits veröffentlichte Seiten einbeziehen.

   Klicken Sie auf **Hinzufügen**, um die untergeordneten Seiten zur Liste der Seiten hinzuzufügen, die je nach Auswahloptionen veröffentlicht werden sollen oder deren Veröffentlichung rückgängig gemacht werden soll. Klicken Sie auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   ![chlimage_1-3](assets/chlimage_1-3.png)

   Dort sehen Sie die hinzugefügten Seiten entsprechend Ihrer Auswahl im Dialogfeld „Untergeordnete Elemente einbeziehen“.

   Zur Ansicht und zum Ändern der Verweise, die für eine Seite veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll, wählen Sie sie aus und klicken Sie anschließend auf die Schaltfläche **Veröffentlichte Verweise**.

   ![pp-04](assets/pp-04.png)

   Das Dialogfeld **Veröffentlichte Verweise** zeigt die Verweise für den ausgewählten Inhalt an. Standardmäßig sind alle ausgewählt und werden veröffentlicht bzw. die Veröffentlichung wird rückgängig gemacht. Sie können sie aber auch deaktivieren, um die Auswahl aufzuheben, sodass sie nicht in die Aktion einbezogen werden.

   Klicken Sie auf **Fertig**, um Ihre Änderungen zu speichern, oder auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   Im Assistenten wird die Spalte **Verweise** aktualisiert und zeigt Ihre Auswahl von Verweisen an, die veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll.

   ![pp-05](assets/pp-05.png)

1. Klicken Sie auf **Veröffentlichen**, um den Vorgang abzuschließen.

   In der Sites-Konsole wird die Veröffentlichung durch eine Benachrichtigung bestätigt.

1. Wenn die veröffentlichten Seiten mit Workflows verknüpft sind, werden diese im abschließenden **Workflow**-Schritt des Veröffentlichungsassistenten gezeigt.

   >[!NOTE]
   >
   >Der gezeigte **Workflow**-Schritt hängt von den Rechten des jeweiligen Benutzers ab. Weitere Informationen finden Sie im [vorherigen Hinweis auf dieser Seite](/help/sites-authoring/publishing-pages.md#main-pars-note-0-ejsjqg-refd) bezüglich Berechtigungen für die Veröffentlichung sowie unter [Verwaltung der Zugriffsrechte auf Workflows](/help/sites-administering/workflows-managing.md) und unter [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md#main-pars-text-5-bvhbkh-refd).

   Die Ressourcen werden nach den ausgelösten Workflows gruppiert und erhalten jeweils folgende Optionen:

   * Definieren des Workflow-Titels
   * Behalten Sie das Workflow-Pakets bei, vorausgesetzt, der Workflow [unterstützt mehrere Ressourcen](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).
   * Definieren des Titels des Workflow-Pakets, sofern die Option zum Beibehalten des Workflow-Pakets ausgewählt wurde

   Klicken Sie auf **Veröffentlichen** oder **Später veröffentlichen**, um die Veröffentlichung abzuschließen.

   ![chlimage_1-4](assets/chlimage_1-4.png)

## Veröffentlichen von Seiten rückgängig machen {#unpublishing-pages}

Wenn Sie die Veröffentlichung einer Seite rückgängig machen, wird sie aus der Veröffentlichungsumgebung gelöscht, sodass sie nicht mehr für Ihre Leser verfügbar ist.

[Ähnlich wie beim Veröffentlichen](/help/sites-authoring/publishing-pages.md#publishing-pages) können Sie auch die Veröffentlichung einer oder mehrerer Seiten aufheben:

* [Im Seiten-Editor](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-editor)
* [In der Sites-Konsole](/help/sites-authoring/publishing-pages.md#unpublishing-from-the-console)

### Rückgängigmachen der Veröffentlichung im Editor {#unpublishing-from-the-editor}

Wenn Sie die Veröffentlichung einer von Ihnen bearbeiteten Seite rückgängig machen möchten, wählen Sie analog zur [Veröffentlichung einer Seite](/help/sites-authoring/publishing-pages.md#publishing-from-the-editor) im Menü **Seiteninformationen** die Option **Veröffentlichung der Seite rückgängig machen** aus.

>[!NOTE]
>
>Seiten, auf die von [Aliase](/help/sites-authoring/editing-page-properties.md#advanced) im Editor kann die Veröffentlichung nicht rückgängig gemacht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

### Rückgängigmachen der Veröffentlichung in der Konsole {#unpublishing-from-the-console}

Ebenso wie Sie [die Option „Veröffentlichung verwalten“ zur Veröffentlichung verwenden](/help/sites-authoring/publishing-pages.md#manage-publication), können Sie damit auch eine Veröffentlichung aufheben.

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie im ersten Schritt **Optionen** die Option **Veröffentlichung aufheben** anstelle der Standardoption **Veröffentlichen** aus.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   Die Auswahl von „Später veröffentlichen“ startet einen Workflow zur Veröffentlichung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Auswahl von „Später deaktivieren“ einen Workflow zum Rückgängigmachen der Veröffentlichung der ausgewählten Seiten zum angegebenen Zeitpunkt.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-administering/workflows.md), um den entsprechenden Workflow zu beenden.

1. Um das Rückgängigmachen der Veröffentlichung abzuschließen, fahren Sie mit dem Assistenten ähnlich wie beim [Veröffentlichen der Seite](/help/sites-authoring/publishing-pages.md#manage-publication) fort.

## Veröffentlichen und Rückgängigmachen der Veröffentlichung eines Baums {#publishing-and-unpublishing-a-tree}

Wenn Sie eine beträchtliche Anzahl von Inhaltsseiten eingegeben oder aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion die gesamte Baumstruktur zu veröffentlichen.

Sie können dazu die Option [Veröffentlichung verwalten](/help/sites-authoring/publishing-pages.md#manage-publication) auf der Sites-Konsole verwenden.

1. Wählen Sie in der Sites-Konsole die Stammseite des Baums aus, den Sie veröffentlichen bzw. dessen Veröffentlichung Sie aufheben möchten, und wählen Sie **Veröffentlichung verwalten** aus.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie „Veröffentlichen“ oder „Veröffentlichung aufheben“ sowie den Zeitpunkt aus und danach **Weiter**, um fortzufahren.
1. Wählen Sie im Schritt **Umfang** die Stammseite aus und wählen Sie **Untergeordnete Elemente einschließen** aus.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Deaktivieren Sie im Dialogfeld **Untergeordnete Elemente einbeziehen** die folgenden Optionen:

   * Nur unmittelbar untergeordnete Elemente einbeziehen
   * Nur bereits veröffentlichte Seiten einbeziehen

   Diese Optionen sind standardmäßig ausgewählt. Sie müssen also darauf achten, diese Auswahl aufzuheben. Klicken Sie auf **Hinzufügen**, um zu bestätigen und den Inhalt für die Veröffentlichung bzw. das Rückgängigmachen einer Veröffentlichung hinzuzufügen.

   ![chlimage_1-7](assets/chlimage_1-7.png)

1. Im Assistenten **Veröffentlichung verwalten** wird der Inhalt des Baums zur Überprüfung aufgelistet. Sie können die Auswahl weiter anpassen, indem Sie zusätzliche Seiten hinzufügen oder die ausgewählten Seiten entfernen.

   ![screen_shot_2018-03-21at154237](assets/screen_shot_2018-03-21at154237.png)

   Sie können die zu veröffentlichenden Verweise auch in der Option **Veröffentlichte Verweise** überprüfen.

1. [Fahren Sie mit dem Assistenten „Veröffentlichung verwalten“ wie üblich fort](#manage-publication), um die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung der Baumstruktur abzuschließen.

## Bestimmen des Veröffentlichungsstatus {#determining-publication-status}

Sie können den Veröffentlichungsstatus einer Seite bestimmen:

* In der [Ressourcenübersicht in der Sites-Konsole](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)

  ![screen-shot_2019-03-05at112019](assets/screen-shot_2019-03-05at112019.png)

  Der Veröffentlichungsstatus wird in der Sites-Konsole in der Ansicht [Karte](/help/sites-authoring/basic-handling.md#card-view), [Spalte](/help/sites-authoring/basic-handling.md#column-view) und [Liste](/help/sites-authoring/basic-handling.md#list-view) angezeigt.

* in der [Zeitleisten](/help/sites-authoring/basic-handling.md#timeline)

  ![screen_shot_2018-03-21at154420](assets/screen_shot_2018-03-21at154420.png)

* im Menü [Seiteninformationen](/help/sites-authoring/author-environment-tools.md#page-information) beim Bearbeiten einer Seite

  ![screen_shot_2018-03-21at154456](assets/screen_shot_2018-03-21at154456.png)
