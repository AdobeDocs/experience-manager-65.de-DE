---
title: Überprüfen von Ordner-Assets und Sammlungen
description: Richten Sie Prüfungs-Workflows für Assets innerhalb eines Ordners oder einer Sammlung ein und geben Sie diese für Prüfer oder kreative Partner frei, um Feedback zu erhalten.
contentOwner: AG
feature: Collaboration, Collections
role: User
exl-id: 23c90e10-aa03-450e-9fb0-2f5be0c5066b
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 60%

---

# Überprüfen von Ordner-Assets und Sammlungen {#review-folder-assets-and-collections}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/bulk-approval.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/using/bulk-approval.html?lang=en) |

Richten Sie Prüfungs-Workflows für Assets innerhalb eines Ordners oder einer Sammlung ein und geben Sie diese für Prüfer oder kreative Partner frei, um Feedback zu erhalten.

[!DNL Adobe Experience Manager Assets]Mit können Sie einen Ad-hoc-Prüfungs-Workflow für Assets innerhalb eines Ordners oder einer Sammlung einrichten und ihn für Prüfer oder kreative Partner freigeben, um Feedback zu erhalten.

Sie können den Prüfungs-Workflow entweder mit einem Projekt verbinden oder eine eigenständige Prüfungsaufgabe erstellen.

Wenn Sie die Assets freigeben, können Prüfer sie genehmigen oder ablehnen. Benachrichtigungen werden in verschiedenen Phasen des Workflows gesendet, um die beabsichtigten Empfänger über die Ausführung verschiedener Aufgaben zu informieren. Wenn Sie beispielsweise einen Ordner oder eine Sammlung freigeben, erhält der Prüfer eine Benachrichtigung, dass ein Ordner/eine Sammlung zur Prüfung freigegeben wurde.

Nachdem der Prüfer die Prüfung abgeschlossen hat (Assets genehmigt oder ablehnt), erhalten Sie eine Benachrichtigung über den Abschluss der Prüfung.

## Erstellen einer Prüfungsaufgabe für Ordner {#creating-a-review-task-for-folders}

1. Aus dem [!DNL Assets] -Benutzeroberfläche den Ordner auswählen, für den Sie eine Prüfungsaufgabe erstellen möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Prüfungsaufgabe erstellen]** ![Prüfungsaufgabe erstellen](assets/do-not-localize/create-review-task.png) , um **[!UICONTROL Prüfungsaufgabe]** Seite. Wenn die Option in der Symbolleiste nicht angezeigt wird, klicken Sie auf **[!UICONTROL Mehr]** und wählen Sie dann die Option aus.

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

1. Geben Sie auf der Registerkarte „Erweitert“ eine Beschriftung ein, die zum Erstellen der URI verwendet werden soll.

   ![Prüfungsname](assets/review_name.png)

1. Klicken **[!UICONTROL Einsenden]** und klicken Sie anschließend auf **[!UICONTROL Fertig]** um die Bestätigungsnachricht zu schließen. Eine Benachrichtigung für die neue Aufgabe wird an den Genehmiger gesendet.
1. Anmelden bei [!DNL Assets] als Genehmiger verwenden und zum [!DNL Assets] Benutzeroberfläche. Um Assets zu genehmigen, klicken Sie auf **[!UICONTROL Benachrichtigungen]** und wählen Sie dann die Prüfungsaufgabe aus der Liste aus.

   ![Asset-Benachrichtigung](assets/aemAssetsNotification.png)

1. Im **[!UICONTROL Prüfungsaufgabe]** Seite, überprüfen Sie die Details der Prüfungsaufgabe und klicken Sie dann auf **[!UICONTROL Überprüfen]**.
1. Im **[!UICONTROL Prüfungsaufgabe]** Seite, Assets auswählen und auf **[!UICONTROL Genehmigen/Ablehnen]** gegebenenfalls zu genehmigen oder abzulehnen.

   ![Prüfungsaufgabe](assets/review_task.png)

1. Klicken **[!UICONTROL Fertig]** aus der Symbolleiste. Geben Sie im Dialogfeld einen Kommentar ein und klicken Sie auf  **[!UICONTROL Fertig]** zur Bestätigung.
1. Navigieren Sie zum [!DNL Assets] -Benutzeroberfläche und öffnen Sie den Ordner. Die Symbole für den Genehmigungsstatus für die Assets werden in der Karten- und Listenansicht angezeigt.

   **Kartenansicht**

   ![Prüfungsstatus in der Kartenansicht](assets/chlimage_1-404.png)

   **Listenansicht**

   ![Überprüfungsstatus in der Listenansicht](assets/review_status_listview.png)

## Erstellen einer Prüfungsaufgabe für Sammlungen {#creating-a-review-task-for-collections}

1. Wählen Sie auf der Seite „Sammlungen“ die Sammlung aus, für die Sie eine Prüfungsaufgabe erstellen möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Prüfungsaufgabe erstellen]** ![Prüfungsaufgabe erstellen](assets/do-not-localize/create-review-task.png) , um **[!UICONTROL Prüfungsaufgabe]** Seite. Wenn die Option in der Symbolleiste nicht angezeigt wird, klicken Sie auf **[!UICONTROL Mehr]** und wählen Sie dann die Option aus.

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

1. Klicken **[!UICONTROL Einsenden]** und klicken Sie anschließend auf **[!UICONTROL Fertig]** um die Bestätigungsnachricht zu schließen. Eine Benachrichtigung für die neue Aufgabe wird an den Genehmiger gesendet.
1. Anmelden bei [!DNL Assets] als Genehmiger verwenden und zum [!DNL Assets] Konsole. Um Assets zu genehmigen, klicken Sie auf **[!UICONTROL Benachrichtigungen]** und wählen Sie dann die Prüfungsaufgabe aus der Liste aus.
1. Im **[!UICONTROL Prüfungsaufgabe]** Seite, überprüfen Sie die Details der Prüfungsaufgabe und klicken Sie dann auf **[!UICONTROL Überprüfen]**.
1. Alle Assets in der Sammlung sind auf der Prüfungsseite sichtbar. Wählen Sie die Assets aus und klicken Sie auf **[!UICONTROL Genehmigen/Ablehnen]** um Assets zu genehmigen oder abzulehnen.

   ![Prüfungsaufgabe-Sammlung](assets/review_task_collection.png)

1. Klicken **[!UICONTROL Fertig]** aus der Symbolleiste. Geben Sie im Dialogfeld einen Kommentar ein und klicken Sie auf **[!UICONTROL Fertig]** zur Bestätigung.
1. Gehen Sie zur Konsole „Sammlungen“ und öffnen Sie die Sammlung. Die Symbole für den Genehmigungsstatus der Assets werden in der Karten- sowie in der Listenansicht angezeigt.

   ![Sammlung-Prüfungsstatus-Kartenansicht](assets/collection_reviewstatuscardview.png)

   *Abbildung: Kartenansicht.*

   ![Sammlung-Prüfungsstatus-Listenansicht](assets/collection_reviewstatuslistview.png)

   *Abbildung: Listenansicht.*
