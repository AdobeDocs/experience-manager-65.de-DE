---
title: Ein- und Auschecken von Dateien in  [!DNL Assets]
description: Erfahren Sie, wie Sie Assets für die Bearbeitung auschecken und nach Abschluss der Änderungen wieder einchecken können.
contentOwner: AG
role: User
feature: Asset Management
exl-id: 544ef73c-4e4b-433f-a173-fdf1c8f45d8e
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 91%

---

# Ein- und Auschecken von Dateien im DAM von [!DNL Experience Manager] {#check-in-and-check-out-files-in-assets}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/check-out-and-submit-assets.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/managing/check-out-and-submit-assets.html?lang=en) |

Mit [!DNL Adobe Experience Manager Assets] können Sie Assets zum Bearbeiten auschecken und dann wieder einchecken, wenn Sie keine weiteren Änderungen vornehmen möchten. Wenn Sie ein Asset ausgecheckt haben, können nur Sie das Asset bearbeiten, mit Anmerkungen versehen, veröffentlichen, verschieben oder löschen. Beim Auschecken eines Assets wird das Asset gesperrt. Andere Benutzer können diese Vorgänge erst dann für das Asset ausführen, wenn Sie das Asset wieder in [!DNL Assets] eingecheckt haben. Allerdings können Sie nach wie vor die Metadaten für das gesperrte Asset ändern.

Um Assets aus-/einchecken zu können, benötigen Sie entsprechenden Schreibzugriff.

Mithilfe dieser Funktion können Sie verhindern, dass Benutzer die von einem Autor vorgenommenen Änderungen überschreiben, wenn mehrere Benutzer Team-übergreifend im Rahmen von Bearbeitungs-Workflows zusammenarbeiten.

## Auschecken von Assets {#checking-out-assets}

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche das Asset aus, das ausgecheckt werden soll. Sie können auch mehrere Assets zum Auschecken auswählen.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Auschecken]**. Die Option **[!UICONTROL Auschecken]** wird zu **[!UICONTROL Einchecken]** umgeschaltet.
Um zu überprüfen, ob andere Benutzer das von Ihnen ausgecheckte Asset bearbeiten können, melden Sie sich unter einem anderen Benutzernamen an. Auf der Miniaturansicht des Assets, das Sie ausgecheckt haben, wird ein Sperrsymbol angezeigt.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Wählen Sie das Asset aus. In der Symbolleiste werden keine Optionen zum Bearbeiten, Kommentieren, Veröffentlichen oder Löschen des Assets angezeigt.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   Um die Metadaten für das gesperrte Asset zu bearbeiten, klicken Sie auf **[!UICONTROL Eigenschaften anzeigen]**.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Asset im Bearbeitungsmodus zu öffnen.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Bearbeiten Sie das Asset und speichern Sie die Änderungen. Schneiden Sie beispielsweise das Bild zu und speichern Sie es.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   Sie können das Asset auch mit Anmerkungen versehen oder es veröffentlichen.

1. Wählen Sie das bearbeitete Asset in der [!DNL Assets]-Benutzeroberfläche aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Einchecken]**. Das geänderte Asset wird in [!DNL Assets] eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Erzwungenes Einchecken {#forced-check-in}

Administratoren können von anderen Benutzern ausgecheckte Assets einchecken.

1. Melden Sie sich bei [!DNL Assets] als Administrator an.
1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche ein bzw. mehrere Assets, das bzw. die von anderen Benutzern ausgecheckt wurde(n).

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Sperre aufheben]**. Das Asset wird wieder eingecheckt und steht anderen Benutzern zur Bearbeitung zur Verfügung.

## Best Practices und Einschränkungen {#tips-limitations}

* Es ist möglich, einen *Ordner* zu löschen, der ausgecheckte Asset-Dateien enthält. Stellen Sie vor dem Löschen eines Ordners sicher, dass er keine von Benutzern ausgecheckte digitale Assets enthält.

>[!MORELIKETHIS]
>
>* [Einchecken und Auschecken in der [!DNL Experience Manager] Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#how-app-works2)
>* [Video-Tutorial zum Ein- und Auschecken in  [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html?lang=de)

