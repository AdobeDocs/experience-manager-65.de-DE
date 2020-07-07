---
title: Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang
seo-title: Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang
description: Mit dem AEM-Posteingang können Sie formularzentrierte Workflows starten, indem Sie Anwendungen senden und Aufgaben verwalten.
seo-description: Mit dem AEM-Posteingang können Sie formularzentrierte Workflows starten, indem Sie Anwendungen senden und Aufgaben verwalten.
uuid: c6c0d8ea-743f-4852-99d1-69fd50a0994e
contentOwner: vishgupt
topic-tags: publish
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dd11fd83-3df1-4727-8340-8c5426812823
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 81%

---


# Verwalten von Formularanwendungen und Aufgaben im AEM-Posteingang{#manage-forms-applications-and-tasks-in-aem-inbox}

Zu den vielen Möglichkeiten, einen formularzentrierten Workflow zu starten oder auszulösen, gehören Anwendungen im AEM-Posteingang. Sie müssen eine Workflow-Anwendung erstellen, um einen Forms-Workflow als Anwendung im Posteingang verfügbar zu machen. For more information about workflow application and other ways to launch Forms workflows, see [Launch a Forms-centric workflow on OSGi](../../forms/using/aem-forms-workflow.md#launch).

Darüber hinaus führt der AEM-Posteingang Benachrichtigungen und Aufgaben aus verschiedenen AEM-Komponenten einschließlich Forms-Workflows zusammen. Wenn ein Forms-Workflow ausgelöst wird, der einen Schritt zur Zuweisung einer Aufgabe enthält, wird die dazugehörige Anwendung als Aufgabe im Posteingang der zugewiesenen Person angezeigt. Wenn der Empfänger eine Gruppe ist, wird die Aufgabe im Posteingang aller Gruppenmitglieder angezeigt, bis eine Person die Aufgabe beansprucht oder delegiert.

In der Benutzeroberfläche des Posteingangs können die Aufgaben in einer Listen- oder einer Kalenderansicht angezeigt werden. Sie können außerdem die Einstellungen für die Anzeige konfigurieren. Sie können die Aufgaben nach verschiedenen Parametern filtern. For more information about view and filters, see [Your Inbox](/help/sites-authoring/inbox.md).

Kurz zusammengefasst: Mit dem Posteingang können Sie neue Anwendungen erstellen und zugewiesene Aufgaben verwalten.

>[!NOTE]
>
>Damit Sie den AEM-Posteingang verwenden können, müssen Sie der Gruppe „workflow-users“ angehören.

## Anwendung erstellen {#create-application}

1. Go to AEM Inbox at https://&#39;[server]:[port]&#39;/aem/inbox.
1. In the Inbox UI, tap **[!UICONTROL Create > Application]**. Die Seite &quot;Anwendung auswählen&quot;wird angezeigt.
1. Select an application and click **[!UICONTROL Create]**. Das mit der Anwendung verknüpfte adaptive Formular wird geöffnet. Füllen Sie die Informationen im adaptiven Formular aus und tippen Sie auf **[!UICONTROL Senden]**. Der dazugehörige Workflow wird gestartet und erstellt eine Aufgabe im Posteingang des Empfängers.

## Aufgaben verwalten {#manage-tasks}

Wenn ein Forms-Workflow ausgelöst wird und Sie der Empfänger sind oder einer Empfängergruppe angehören, wird eine Aufgabe in Ihrem Posteingang angezeigt. Sie können im Posteingang Aufgabendetails anzeigen und verfügbare Aktionen für die Aufgabe ausführen.

### Aufgaben annehmen oder delegieren {#claim-or-delegate-tasks}

Aufgaben, die einer Gruppe zugewiesen sind, werden im Posteingang aller Gruppenmitglieder angezeigt. Jedes Gruppenmitglied kann diese Aufgabe annehmen oder an ein anderes Gruppenmitglied delegieren. Gehen Sie dazu wie folgt vor:

1. Tippen Sie auf die Miniaturansicht der Aufgabe, um sie auszuwählen. Optionen zum Öffnen oder Delegieren der Aufgabe werden oben angezeigt.

   ![select-Aufgabe](assets/select-task.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Um die Aufgabe delegieren, tippen Sie auf **[!UICONTROL Delegieren]**. Das Dialogfeld „Element delegieren“ wird geöffnet. Wählen Sie einen Benutzer aus, fügen Sie optional einen Kommentar ein und tippen Sie auf **[!UICONTROL OK]**.

   ![delegate](assets/delegate.png)

   * Um die Aufgabe anzunehmen, tippen Sie auf **[!UICONTROL Öffnen]**. Das Dialogfeld „Selbst zuweisen“ wird geöffnet. Tippen Sie auf **[!UICONTROL Fortfahren]**, um die Aufgabe anzunehmen. Die angenommene Aufgabe wird mit Ihnen als Empfänger in Ihrem Posteingang angezeigt.

   ![claim](assets/claim.png)

### Aufgabendetails anzeigen und Aktionen für Aufgaben durchführen {#view-details-and-perform-actions-on-tasks}

Wenn Sie eine Aufgabe öffnen, können Sie Aufgabendetails anzeigen und verfügbare Aktionen durchführen. Die für eine Aufgabe verfügbaren Aktionen werden im Schritt „Aufgabe zuweisen“ des dazugehörigen Forms-Workflows definiert.

1. Tippen Sie auf die Miniaturansicht der Aufgabe, um sie auszuwählen. Optionen zum Öffnen oder Delegieren der ausgewählten Aufgabe werden oben angezeigt.
1. Tippen Sie auf **Öffnen**, um die Aufgabendetails anzuzeigen und Aktionen auszuführen. Die detaillierte Aufgabenansicht wird geöffnet. In dieser Ansicht können Sie Aufgabendetails anzeigen und verfügbare Aktionen für die Aufgabe ausführen.

   >[!NOTE]
   >
   >Wenn eine Aufgabe einer Gruppe zugewiesen ist, müssen Sie sie annehmen, damit Sie sie in der detaillierten Ansicht anzeigen können.

![Aufgabe-Details](assets/task-details.png)

Die detaillierte Aufgabenansicht umfasst die folgenden Abschnitte:

* Aufgabendetails
* Formular- 
* Workflow-Details
* Aktionssymbolleiste

#### Aufgabendetails {#task-details}

Der Abschnitt „Aufgabendetails“ zeigt Informationen zur Aufgabe an. The information displayed depends on the configuration settings of the [Assign task step](/help/sites-developing/workflows-step-ref.md) in the workflow. Das Beispiel oben zeigt die Beschreibung, den Status, das Startdatum und den verwendeten Workflow für die Aufgabe an. Es ist außerdem möglich, Dateien an Aufgaben anzuhängen.

#### Formular- {#form}

Auf der Registerkarte „Formular“ im Hauptinhaltsbereich werden das übermittelte Formular und gegebenenfalls Anhänge für einzelne Felder angezeigt.

#### Workflow-Details {#workflow-details}

Die Registerkarte „Workflow-Details“ oben zeigt den Fortschritt der Aufgabe in verschiedenen Phasen des Workflows an. Sie zeigt abgeschlossene, aktuelle und ausstehende Phasen der Aufgabe. The stages for a workflow are defined in the [Assign task step](/help/sites-developing/workflows-step-ref.md) of the associated workflow.

Darüber hinaus wird auf der Registerkarte der Aufgabenverlauf für jede abgeschlossene Phase im Workflow angezeigt. Sie können auf **[!UICONTROL Details anzeigen]** für eine abgeschlossene Phase tippen, um Details zu dieser Phase anzuzeigen. Dies zeigt Kommentare, Formular- und Aufgabenanhänge, Status, Start- und Enddatum usw. für die Aufgabe an.

![workflow-details](assets/workflow-details.png)

#### Aktionssymbolleiste {#actions-toolbar}

Die Aktionssymbolleiste zeigt alle verfügbaren Optionen für die Aufgabe. Speichern, Zurücksetzen und Delegieren sind Standardaktionen, andere verfügbare Aktionen werden dagegen im Schritt [Aufgabe zuweisen](/help/sites-developing/workflows-step-ref.md) konfiguriert. Im obigen Beispiel sind „Genehmigen“ und „Ablehnen“ im Workflow konfiguriert.

Wenn Sie eine Aktion für die Aufgabe ausführen, wird diese im Workflow weitergeleitet.

### Abgeschlossene Aufgaben anzeigen {#view-completed-tasks}

Im AEM-Posteingang werden nur aktive Aufgaben angezeigt. Abgeschlossene Aufgaben werden nicht in der Liste aufgeführt. Sie können jedoch mithilfe von Posteingangsfiltern Aufgaben basierend auf verschiedenen Parametern filtern, z. B. Aufgabentyp, Status, Start- und Enddatum usw. Abgeschlossene Aufgaben anzeigen:

1. In AEM Inbox, tap ![toggle-side-panel1](assets/toggle-side-panel1.png) to open the filter selector.
1. Tippen Sie auf das Akkordion **[!UICONTROL Aufgabenstatus]** und wählen Sie **[!UICONTROL Abgeschlossen]**. Alle Ihre abgeschlossenen Aufgaben werden angezeigt.

   ![filter](assets/filter.png)

1. Wählen Sie eine Aufgabe und klicken Sie auf **[!UICONTROL Öffnen]**.

Die Aufgabe wird geöffnet und das dazugehörige Dokument oder adaptive Formular wird angezeigt. For adaptive form, the task displays the read-only adaptive form or its PDF document of record as configured in the Form/Document tab of the [Assign Task workflow step](/help/sites-developing/workflows-step-ref.md).

Im Abschnitt mit den Aufgabendetails werden Informationen wie die durchgeführte Aktion, der Aufgabenstatus, das Startdatum und das Enddatum angezeigt.

![completed-Aufgabe](assets/completed-task.png)

The **[!UICONTROL Workflow Details]** tab shows each step of the workflow. Tap **[!UICONTROL View details]** for a step for detailed information.

![completed-Aufgabe-workflow](assets/completed-task-workflow.png)

