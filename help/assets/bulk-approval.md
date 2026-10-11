---
title: Überprüfen von Ordner-Assets und Sammlungen
description: Richten Sie Prüfungs-Workflows für Assets innerhalb eines Ordners oder einer Sammlung ein und geben Sie diese für Prüfer oder kreative Partner frei, um Feedback zu erhalten.
contentOwner: AG
feature: Collaboration, Collections
role: User
exl-id: 23c90e10-aa03-450e-9fb0-2f5be0c5066b
hide: true
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: ac365bec-0634-4744-9473-c42f47320593
    internal-label: Asset management and governance
subfeature_v2:
  - id: f7212149-7f65-4e43-89c2-1f075f45be16
    internal-label: Collaboration
  - id: c73531c3-4c05-471e-beff-cefb35857910
    internal-label: Collections
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 100%
---
# Überprüfen von Ordner-Assets und Sammlungen {#review-folder-assets-and-collections}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/bulk-approval.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Richten Sie Prüfungs-Workflows für Assets innerhalb eines Ordners oder einer Sammlung ein und geben Sie diese für Prüfer oder kreative Partner frei, um Feedback zu erhalten.

Mit [!DNL Adobe Experience Manager Assets] können Sie einen Ad-hoc-Prüfungs-Workflow für Assets innerhalb eines Ordners oder einer Sammlung einrichten und ihn für Prüfer oder kreative Partner freigeben, um Feedback zu erhalten.

Sie können den Prüfungs-Workflow entweder mit einem Projekt verbinden oder eine eigenständige Prüfungsaufgabe erstellen.

Nachdem Sie die Assets freigegeben haben, können Überprüfende sie genehmigen oder ablehnen. Benachrichtigungen werden in verschiedenen Phasen des Workflows gesendet, um die vorgesehenen Empfangenden über den Abschluss verschiedener Aufgaben zu informieren. Wenn Sie beispielsweise einen Ordner oder eine Sammlung freigeben, erhalten Prüfende eine Benachrichtigung, dass ein Ordner/eine Sammlung zur Überprüfung freigegeben wurde.

Nachdem Überprüfende die Überprüfung abgeschlossen haben (Assets genehmigt oder ablehnt), erhalten Sie eine Benachrichtigung zum Abschluss der Überprüfung.

## Erstellen einer Prüfungsaufgabe für Ordner {#creating-a-review-task-for-folders}

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche den Ordner aus, für den Sie eine Prüfungsaufgabe erstellen möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Prüfungsaufgabe erstellen]** ![Prüfungsaufgabe erstellen](assets/do-not-localize/create-review-task.png), um die Seite **[!UICONTROL Prüfungsaufgabe]** zu öffnen. Wenn Sie die Option in der Symbolleiste nicht sehen können, klicken Sie auf **[!UICONTROL Mehr]** und wählen Sie dann die Option aus.

1. (Optional) Wählen Sie in der Liste **[!UICONTROL Projekt]** das Projekt aus, mit dem Sie die Prüfungsaufgabe verbinden möchten. Standardmäßig ist die Option **[!UICONTROL Ohne]** ausgewählt. Wenn Sie kein Projekt mit der Prüfungsaufgabe verknüpfen möchten, behalten Sie diese Auswahl bei.

   >[!NOTE]
   >
   >Nur die Projekte, für die Sie über Berechtigungen auf Editor-Ebene (oder höher) verfügen, sind in der Liste **[!UICONTROL Projekte]** sichtbar.

1. Geben Sie einen Namen für die Prüfungsaufgabe ein und wählen Sie einen Genehmigenden aus der Liste **[!UICONTROL Zuweisen zu]** aus.

   >[!NOTE]
   >
   >Die Mitglieder/Gruppen des ausgewählten Projekts sind als Genehmigende in der Liste **[!UICONTROL Zuweisen zu]** verfügbar.

1. Geben Sie eine Beschreibung, die Aufgabenpriorität und das Fälligkeitsdatum für die Prüfungsaufgabe ein.

   ![Aufgabendetails](assets/task_details.png)

1. Geben Sie auf der Registerkarte „Erweitert“ eine Beschriftung ein, die zum Erstellen der URI verwendet werden soll.

   ![Prüfungsname](assets/review_name.png)

1. Klicken Sie auf **[!UICONTROL Senden]** und dann auf **[!UICONTROL Fertig]**, um die Bestätigungsmeldung zu schließen. Eine Benachrichtigung für die neue Aufgabe wird an die genehmigende Person gesendet.
1. Melden Sie sich bei [!DNL Assets] als genehmigende Person an und gehen Sie zur [!DNL Assets]-Benutzeroberfläche. Um Assets zu genehmigen, klicken Sie auf **[!UICONTROL Benachrichtigungen]** und wählen Sie die Prüfungsaufgabe aus der Liste aus.

   ![Asset-Benachrichtigung](assets/aemAssetsNotification.png)

1. Überprüfen Sie auf der Seite **[!UICONTROL Prüfungsaufgabe]** die Details der Prüfungsaufgabe und klicken Sie dann auf **[!UICONTROL Überprüfen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Prüfungsaufgabe]** Assets aus und klicken Sie auf **[!UICONTROL Genehmigen/Ablehnen]**, um die Assets je nach Bedarf zu genehmigen oder abzulehnen.

   ![Prüfungsaufgabe](assets/review_task.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Fertig stellen]**. Geben Sie im Dialogfeld einen Kommentar ein und klicken Sie zur Bestätigung auf **[!UICONTROL Fertig stellen]**.
1. Navigieren Sie zur [!DNL Assets]-Benutzeroberfläche und öffnen Sie den Ordner. Die Symbole für den Genehmigungsstatus für die Assets werden in der Karten- und der Listenansicht angezeigt.

   **Kartenansicht**

   ![Prüfungsstatus in der Kartenansicht](assets/chlimage_1-404.png)

   **Listenansicht**

   ![Überprüfungsstatus in der Listenansicht](assets/review_status_listview.png)

## Erstellen einer Prüfungsaufgabe für Sammlungen {#creating-a-review-task-for-collections}

1. Wählen Sie auf der Seite „Sammlungen“ die Sammlung aus, für die Sie eine Prüfungsaufgabe erstellen möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Prüfungsaufgabe erstellen]** ![Prüfungsaufgabe erstellen](assets/do-not-localize/create-review-task.png), um die Seite **[!UICONTROL Prüfungsaufgabe]** zu öffnen. Wenn Sie die Option in der Symbolleiste nicht sehen können, klicken Sie auf **[!UICONTROL Mehr]** und wählen Sie dann die Option aus.

1. (Optional) Wählen Sie in der Liste **[!UICONTROL Projekt]** das Projekt aus, mit dem Sie die Prüfungsaufgabe verbinden möchten. Standardmäßig ist die Option **[!UICONTROL Ohne]** ausgewählt. Wenn Sie kein Projekt mit der Prüfungsaufgabe verknüpfen möchten, behalten Sie diese Auswahl bei.

   >[!NOTE]
   >
   >Nur die Projekte, für die Sie über Berechtigungen auf Editor-Ebene (oder höher) verfügen, sind in der Liste **[!UICONTROL Projekte]** sichtbar.

1. Geben Sie einen Namen für die Prüfungsaufgabe ein und wählen Sie einen Genehmigenden aus der Liste **[!UICONTROL Zuweisen zu]** aus.

   >[!NOTE]
   >
   >Die Mitglieder/Gruppen des ausgewählten Projekts sind als Genehmigende in der Liste **[!UICONTROL Zuweisen zu]** verfügbar.

1. Geben Sie eine Beschreibung, die Aufgabenpriorität und das Fälligkeitsdatum für die Prüfungsaufgabe ein.

   ![Aufgabendetails-Sammlung](assets/task_details-collection.png)

1. Klicken Sie auf **[!UICONTROL Senden]** und dann auf **[!UICONTROL Fertig]**, um die Bestätigungsmeldung zu schließen. Eine Benachrichtigung für die neue Aufgabe wird an die genehmigende Person gesendet.
1. Melden Sie sich bei [!DNL Assets] als genehmigende Person an und gehen Sie zur [!DNL Assets]-Konsole. Um Assets zu genehmigen, klicken Sie auf **[!UICONTROL Benachrichtigungen]** und wählen Sie die Prüfungsaufgabe aus der Liste aus.
1. Überprüfen Sie auf der Seite **[!UICONTROL Prüfungsaufgabe]** die Details der Prüfungsaufgabe und klicken Sie dann auf **[!UICONTROL Überprüfen]**.
1. Alle Assets in der Sammlung sind auf der Prüfungsseite sichtbar. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Genehmigen/Ablehnen]**, um die Assets je nach Bedarf zu genehmigen bzw. abzulehnen.

   ![Prüfungsaufgabe-Sammlung](assets/review_task_collection.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Fertig stellen]**. Geben Sie im Dialogfeld einen Kommentar ein und klicken Sie zur Bestätigung auf **[!UICONTROL Fertig stellen]**.
1. Gehen Sie zur Konsole „Sammlungen“ und öffnen Sie die Sammlung. Die Symbole für den Genehmigungsstatus für die Assets werden sowohl in der Karten- als auch in der Listenansicht angezeigt.

   ![Sammlung-Prüfungsstatus-Kartenansicht](assets/collection_reviewstatuscardview.png)

   *Abbildung: Kartenansicht.*

   ![Sammlung-Prüfungsstatus-Listenansicht](assets/collection_reviewstatuslistview.png)

   *Abbildung: Listenansicht.*
