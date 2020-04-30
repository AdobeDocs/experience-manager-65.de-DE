---
title: Überprüfen von Ordner-Assets und Sammlungen
description: Richten Sie Prüfungs-Workflows für Assets innerhalb eines Ordners oder einer Sammlung ein und geben Sie diese für Prüfer oder kreative Partner frei, um Feedback zu erhalten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Überprüfen von Ordner-Assets und Sammlungen {#review-folder-assets-and-collections}

Richten Sie Prüfungs-Workflows für Assets innerhalb eines Ordners oder einer Sammlung ein und geben Sie diese für Prüfer oder kreative Partner frei, um Feedback zu erhalten.

Mit Adobe Experience Manager (AEM) Assets können Sie einen Ad-hoc-Prüfungs-Workflow für Assets innerhalb eines Ordners oder einer Sammlung einrichten und ihn für Prüfer oder kreative Partner freigeben, um Feedback zu erhalten.

Sie können den Prüfungs-Workflow entweder mit einem Projekt verbinden oder eine eigenständige Prüfungsaufgabe erstellen.

Wenn Sie die Assets freigeben, können Prüfer sie genehmigen oder ablehnen. Benachrichtigungen werden in verschiedenen Phasen des Workflows gesendet, um die beabsichtigten Empfänger über die Ausführung verschiedener Aufgaben zu informieren. Wenn Sie beispielsweise einen Ordner oder eine Sammlung freigeben, erhält der Prüfer eine Benachrichtigung, dass ein Ordner/eine Sammlung zur Prüfung freigegeben wurde.

Nachdem der Prüfer die Prüfung abgeschlossen hat (Assets genehmigt oder ablehnt), erhalten Sie eine Benachrichtigung über den Abschluss der Prüfung.

## Create a review task for folders {#creating-a-review-task-for-folders}

1. Wählen Sie in der Assets-Benutzeroberfläche den Ordner aus, für den Sie eine Prüfungsaufgabe erstellen möchten.
1. From the toolbar, click **[!UICONTROL Create Review Task]** to open the **[!UICONTROL Review Task]** page. If you cannot see the option in the toolbar, click **[!UICONTROL More]** and then select the option.

   ![chlimage_1-403](assets/chlimage_1-403.png)

1. (Optional) Wählen Sie in der Liste **[!UICONTROL Projekt]** das Projekt aus, mit dem Sie die Prüfungsaufgabe verbinden möchten. Standardmäßig ist die Option **[!UICONTROL Ohne]** ausgewählt. Wenn Sie kein Projekt mit der Prüfungsaufgabe verbinden möchten, behalten Sie diese Auswahl bei.

   >[!NOTE]
   >
   >Nur die Projekte, für die Sie Berechtigungen auf Editor-Ebene (oder höher) haben, sind in der Liste **[!UICONTROL Projekte]** sichtbar.

1. Geben Sie einen Namen für die Prüfungsaufgabe ein und wählen Sie einen Genehmigenden aus der Liste **[!UICONTROL Zuweisen zu]** aus.

   >[!NOTE]
   >
   >Die Mitglieder/Gruppen des ausgewählten Projekts sind als Genehmigende in der Liste **[!UICONTROL Zuweisen zu]** verfügbar.

1. Geben Sie eine Beschreibung, die Aufgabenpriorität und das Fälligkeitsdatum für die Prüfungsaufgabe ein.

   ![Aufgabendetails](assets/task_details.png)

1. Geben Sie auf der Registerkarte „Erweitert“ eine Beschriftung ein, die zum Erstellen der URL verwendet werden soll.

   ![Prüfungsname](assets/review_name.png)

1. Click **[!UICONTROL Submit]**, and then click **[!UICONTROL Done]** to close the confirmation message. Eine Benachrichtigung für die neue Aufgabe wird an den Genehmiger gesendet.
1. Melden Sie sich bei AEM Assets als Genehmiger an und gehen Sie zur Assets-Benutzeroberfläche. To approve assets, click **[!UICONTROL Notifications]** and then select the review task from the list.

   ![Asset-Benachrichtigung](assets/aemAssetsNotification.png)

1. In the **[!UICONTROL Review Task]** page, examine the details of the review task, and then click **[!UICONTROL Review]**.
1. In the **[!UICONTROL Review Task]** page, select assets, and click **[!UICONTROL Approve/Reject]** to approve or reject, as appropriate.

   ![Prüfungsaufgabe](assets/review_task.png)

1. Click **[!UICONTROL Complete]** from the toolbar. In the dialog, enter a comment and click  **[!UICONTROL Complete]** to confirm.
1. Navigieren Sie zur Benutzeroberfläche &quot;Assets&quot;und öffnen Sie den Ordner. Die Symbole für den Genehmigungsstatus für die Assets werden in der Ansicht für die Ansicht und Liste der Karte angezeigt.

   **Kartenansicht**

   ![Überprüfungsstatus in der Ansicht der Karte](assets/chlimage_1-404.png)

   **Listenansicht**

   ![Überprüfungsstatus in der Ansicht der Liste](assets/review_status_listview.png)

## Create a review task for collections {#creating-a-review-task-for-collections}

1. Wählen Sie auf der Seite „Sammlungen“ die Sammlung aus, für die Sie eine Prüfungsaufgabe erstellen möchten.
1. From the toolbar, click **[!UICONTROL Create Review Task]** to open the **[!UICONTROL Review Task]** page. If you cannot see the option on the toolbar, click **[!UICONTROL More]** and then select the option.

   ![chlimage_1-405](assets/chlimage_1-405.png)

1. (Optional) Wählen Sie in der Liste **[!UICONTROL Projekt]** das Projekt aus, mit dem Sie die Prüfungsaufgabe verbinden möchten. Standardmäßig ist die Option **[!UICONTROL Ohne]** ausgewählt. Wenn Sie kein Projekt mit der Prüfungsaufgabe verbinden möchten, behalten Sie diese Auswahl bei.

   >[!NOTE]
   >
   >Nur die Projekte, für die Sie Berechtigungen auf Editor-Ebene (oder höher) haben, sind in der Liste **[!UICONTROL Projekte]** sichtbar.

1. Geben Sie einen Namen für die Prüfungsaufgabe ein und wählen Sie einen Genehmigenden aus der Liste **[!UICONTROL Zuweisen zu]** aus.

   >[!NOTE]
   >
   >Die Mitglieder/Gruppen des ausgewählten Projekts sind als Genehmigende in der Liste **[!UICONTROL Zuweisen zu]** verfügbar.

1. Geben Sie eine Beschreibung, die Aufgabenpriorität und das Fälligkeitsdatum für die Prüfungsaufgabe ein.

   ![Aufgabendetails-Sammlung](assets/task_details-collection.png)

1. Click **[!UICONTROL Submit]**, and then click **[!UICONTROL Done]** to close the confirmation message. Eine Benachrichtigung für die neue Aufgabe wird an den Genehmiger gesendet.
1. Melden Sie sich bei AEM Assets als Genehmiger an und gehen Sie zur Konsole „Assets“. To approve assets, click **[!UICONTROL Notifications]** and then select the review task from the list.
1. In the **[!UICONTROL Review Task]** page, examine the details of the review task, and then click **[!UICONTROL Review]**.
1. Alle Assets in der Sammlung sind auf der Prüfungsseite sichtbar. Select the assets and click **[!UICONTROL Approve/Reject]** to approve or reject assets, as appropriate.

   ![Prüfungsaufgabe-Sammlung](assets/review_task_collection.png)

1. Click **[!UICONTROL Complete]** from the toolbar. In the dialog, enter a comment and click **[!UICONTROL Complete]** to confirm.
1. Gehen Sie zur Konsole „Sammlungen“ und öffnen Sie die Sammlung. Die Symbole für den Genehmigungsstatus der Assets werden in der Karten- sowie in der Listenansicht angezeigt.

   ![Sammlung-Prüfungsstatus-Kartenansicht](assets/collection_reviewstatuscardview.png)

   *Abbildung: Ansicht der Karte.*

   ![Sammlung-Prüfungsstatus-Listenansicht](assets/collection_reviewstatuslistview.png)

   *Abbildung: Ansicht der Liste.*
