---
title: Checken Sie Ihre digitalen Assets ein und checken Sie sie zur Bearbeitung aus.
description: Erfahren Sie, wie Sie Assets für die Bearbeitung auschecken und nach Abschluss der Änderungen wieder einchecken können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 53%

---


# Check-in and check-out files in [!DNL Experience Manager] DAM {#check-in-and-check-out-files-in-assets}

[!DNL Adobe Experience Manager Assets]Mit können Sie Assets zum Bearbeiten auschecken und dann wieder einchecken, wenn Sie keine weiteren Änderungen vornehmen möchten. Wenn Sie ein Asset ausgecheckt haben, können nur Sie das Asset bearbeiten, mit Anmerkungen versehen, veröffentlichen, verschieben oder löschen. Beim Auschecken eines Assets wird das Asset gesperrt. Other users cannot perform any of these operations on the asset until you check the asset back in to [!DNL Assets]. Allerdings können Sie nach wie vor die Metadaten für das gesperrte Asset ändern.

Um Assets aus-/einchecken zu können, benötigen Sie entsprechenden Schreibzugriff.

Mithilfe dieser Funktion können Sie verhindern, dass Benutzer die von einem Autor vorgenommenen Änderungen überschreiben, wenn mehrere Benutzer teamübergreifend im Rahmen von Bearbeitungsworkflows zusammenarbeiten.

## Assets überprüfen {#checking-out-assets}

1. From the [!DNL Assets] user interface, select the asset you want to check out. Sie können auch mehrere Assets zum Auschecken auswählen.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Checkout]**.
Die **[!UICONTROL Checkout]** -Option wechselt zum **[!UICONTROL Checkin]**.
Um zu überprüfen, ob andere Benutzer das von Ihnen ausgecheckte Asset bearbeiten können, melden Sie sich unter einem anderen Benutzernamen an. Auf der Miniaturansicht des Assets, das Sie ausgecheckt haben, wird ein Sperrsymbol angezeigt.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Wählen Sie das Asset aus. In der Symbolleiste werden keine Optionen zum Bearbeiten, Kommentieren, Veröffentlichen oder Löschen des Assets angezeigt.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   You can click **[!UICONTROL View Properties]** to edit the metadata for the locked asset.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]** , um das Asset im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Bearbeiten Sie das Asset und speichern Sie die Änderungen. Schneiden Sie beispielsweise das Bild zu und speichern Sie es.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   Sie können das Asset auch mit Anmerkungen versehen oder es veröffentlichen.

1. Wählen Sie das bearbeitete Asset in der [!DNL Assets] Benutzeroberfläche aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Checkin]** . The modified asset is checked in to [!DNL Assets] and is available to other users for editing.

## Forced check in {#forced-check-in}

Administratoren können von anderen Benutzern ausgecheckte Assets einchecken.

1. Log in to [!DNL Assets] as an administrator.
1. From the [!DNL Assets] user interface select one or more assets that have been checked out by other users.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Sperren]**. Das Asset wird wieder eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

>[!MORELIKETHIS]
>
>* [Einchecken und Auschecken in der Experience Manager Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#how-app-works2)
>* [Videoschulung zum Einchecken und Auschecken in Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)

