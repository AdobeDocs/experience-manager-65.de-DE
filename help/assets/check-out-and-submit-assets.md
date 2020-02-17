---
title: Einchecken und Auschecken Ihrer digitalen Assets zur Bearbeitung
description: Erfahren Sie, wie Sie Assets für die Bearbeitung auschecken und nach Abschluss der Änderungen wieder einchecken können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 07c1a4102539ba4678c55dee3a4882101e39864f

---


# Checkin- und Checkout-Dateien in AEM DAM {#check-in-and-check-out-files-in-assets}

Mit Adobe Experience Manager (AEM) Assets können Sie Assets zum Bearbeiten auschecken und dann wieder einchecken, wenn Sie keine weiteren Änderungen vornehmen möchten. Wenn Sie ein Asset ausgecheckt haben, können nur Sie das Asset bearbeiten, mit Anmerkungen versehen, veröffentlichen, verschieben oder löschen. Beim Auschecken eines Assets wird das Asset gesperrt. Andere Benutzer können diese Vorgänge erst dann für das Asset ausführen, wenn Sie das Asset wieder in AEM Assets einchecken. Allerdings können Sie nach wie vor die Metadaten für das gesperrte Asset ändern.

Um Assets aus-/einchecken zu können, benötigen Sie entsprechenden Schreibzugriff.

Mithilfe dieser Funktion können Sie verhindern, dass Benutzer die von einem Autor vorgenommenen Änderungen überschreiben, wenn mehrere Benutzer teamübergreifend im Rahmen von Bearbeitungsworkflows zusammenarbeiten.

## Assets überprüfen {#checking-out-assets}

1. Wählen Sie in der Assets-Benutzeroberfläche das Asset aus, das ausgecheckt werden soll. Sie können auch mehrere Assets zum Auschecken auswählen.
1. From the toolbar, click/tap **[!UICONTROL Checkout]**.
Die **[!UICONTROL Checkout]** -Option wechselt zum **[!UICONTROL Checkin]**.
Um zu überprüfen, ob andere Benutzer das von Ihnen ausgecheckte Asset bearbeiten können, melden Sie sich unter einem anderen Benutzernamen an. Auf der Miniaturansicht des Assets, das Sie ausgecheckt haben, wird ein Sperrsymbol angezeigt.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Wählen Sie das Asset aus. In der Symbolleiste werden keine Optionen zum Bearbeiten, Kommentieren, Veröffentlichen oder Löschen des Assets angezeigt.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   You can, however, tap **[!UICONTROL View Properties]** to edit the metadata for the locked asset.

1. Tippen Sie auf **[!UICONTROL Bearbeiten]** , um das Asset im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Bearbeiten Sie das Asset und speichern Sie die Änderungen. Schneiden Sie beispielsweise das Bild zu und speichern Sie es.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   Sie können das Asset auch mit Anmerkungen versehen oder es veröffentlichen.

1. Select the edited asset from the Assets UI, and tap **[!UICONTROL Checkin]** from the toolbar. Das geänderte Asset wird in AEM Assets eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Forced check in {#forced-check-in}

Administratoren können von anderen Benutzern ausgecheckte Assets einchecken.

1. Melden Sie sich bei AEM Assets als Administrator an.
1. Wählen Sie in der Assets-Benutzeroberfläche ein bzw. mehrere Assets, das bzw. die von anderen Benutzern ausgecheckt wurde(n).

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Sperren]**. Das Asset wird wieder eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

>[!MORELIKETHIS]
>
>* [Einchecken und Auschecken in der AEM-Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#how-app-works2)
>* [Videoschulung zum Einchecken und Auschecken in AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)

