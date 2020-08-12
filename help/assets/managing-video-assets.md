---
title: Verwalten Sie Video-Assets in [!DNL Adobe Experience Manager].
description: Hochladen, Vorschau, Anmerkungen und Veröffentlichen von Video-Assets [!DNL Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9e67e252348f471c052f6c3e88aea61d7a309241
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 37%

---


# Verwalten von Video-Assets    {#manage-video-assets}

Das Videoformat ist ein wichtiger Bestandteil digitaler Assets eines Unternehmens. [!DNL Adobe Experience Manager] angebote bieten und verwalten den gesamten Lebenszyklus Ihrer Video-Assets nach deren Erstellung.

Learn how to manage and edit the video assets in [!DNL Adobe Experience Manager Assets]. Also, if you are licensed to use [!DNL Dynamic Media], see the [Dynamic Media video documentation](/help/assets/video.md).

## Hochladen und Anzeigen der Vorschau von Video-Assets {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] generiert Vorschauen für Video-Assets mit der Erweiterung MP4. If the format of the asset is not MP4, install the FFmpeg pack to generate a preview. FFmpeg creates video renditions of type OGG and MP4. You can preview the renditions in the [!DNL Assets] user interface.

1. In the digital assets folder or subfolders, navigate to the location where you want to add digital assets.
1. To upload the asset, click **[!UICONTROL Create]** from the toolbar and then choose **[!UICONTROL Files]**. Alternativ können Sie sie direkt in den Assets-Bereich ziehen. See [upload assets](managing-assets-touch-ui.md#uploading-assets) for details around the upload operation.
1. To preview a video in the Card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. Sie können Videos nur in der Kartenansicht anhalten oder wiedergeben. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.

1. To preview the video in the asset details page, click **[!UICONTROL Edit]** on the card. Das Video wird im systemeigenen Video-Player des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

   ![Steuerelemente für die Videowiedergabe](assets/video-playback-controls.png)

## Konfiguration zum Hochladen von Assets, die größer als 2 GB sind {#configuration-to-upload-assets-that-are-larger-than-gb}

By default, [!DNL Assets] does not let you upload any assets that are larger than 2 GB because of a file size limit. Sie können diese Beschränkung aber umgehen, indem Sie CRXDE Lite aufrufen und im Verzeichnis `/apps` einen Knoten erstellen. Der Knoten muss denselben Knotennamen, dieselbe Verzeichnisstruktur und vergleichbare Knoteneigenschaften im Hinblick auf die Reihenfolge aufweisen.

In addition to [!DNL Assets] configuration, change the following configurations to upload large assets:

* Erhöhen Sie die Ablaufzeit des Tokens. Siehe [!UICONTROL Adobe Granite CSRF Servlet] in Web Console unter `https://[aem_server]:[port]/system/console/configMgr`. Weitere Informationen finden Sie unter [CSRF-Schutz](/help/sites-developing/csrf-protection.md).
* Erhöhen Sie `receiveTimeout` in der Dispatcher-Konfiguration. Weitere Informationen finden Sie unter [Experience Manager Dispatcher-Konfiguration](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>The [!DNL Experience Manager] Classic user interface does not have a 2-GB file size limit restriction. Außerdem werden End-to-End-Workflows für große Videos nicht vollständig unterstützt.

Um eine höhere Dateigrößenbeschränkung zu konfigurieren, führen Sie die folgenden Schritte im Verzeichnis `/apps` aus.

1. In [!DNL Experience Manager], click **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in CRXDE Lite zu `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. To see the directory window, click the `>>`.
1. From the toolbar, click the **[!UICONTROL Overlay Node]**. Wählen Sie alternativ **[!UICONTROL Überlagerungsknoten]** aus dem Kontextmenü aus.
1. In the **[!UICONTROL Overlay Node]** dialog, click **[!UICONTROL OK]**.

   ![Überlagerungsknoten](assets/overlay-node-path.png)

1. Aktualisieren Sie die Browser-Ansicht. Der Überlagerungsknoten `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` ist ausgewählt.
1. Geben Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** den gewünschten Wert in Byte ein, um die maximale Größe festzulegen. Um beispielsweise die Größenbeschränkung auf 30 GB zu erhöhen, geben Sie den Wert `{sizeLimit : "32212254720"}` ein.

1. From the toolbar, click **[!UICONTROL Save All]**.
1. In [!DNL Experience Manager], click **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. On the [!DNL Adobe Experience Manager] [!UICONTROL Web Console Bundles] page, under the Name column of the table, locate and click **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. On the [!UICONTROL Adobe Granite Workflow External Process Job Handler] page, set the seconds for both **[!UICONTROL Default Timeout]** and **[!UICONTROL Max Timeout]** fields to `18000` (five hours). Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie [!DNL Experience Manager]in &quot; **[!UICONTROL Werkzeuge]** &quot;> &quot; **[!UICONTROL Workflow]** &quot;> &quot; **[!UICONTROL Modelle]**&quot;.
1. On the Workflow Models page, select **[!UICONTROL Dynamic Media Encode Video]**, then click **[!UICONTROL Edit]**.
1. On the workflow page, double-click the **[!UICONTROL Dynamic Media Video Service Process]** component.
1. Erweitern Sie im Dialogfeld [!UICONTROL Schritteigenschaften] auf der Registerkarte **[!UICONTROL Allgemein]** die Option **Erweiterte Einstellungen**.
1. In the **[!UICONTROL Timeout]** field, specify a value of `18000`, then click **[!UICONTROL OK]** to return to the **[!UICONTROL Dynamic Media Encode Video]** workflow page.
1. Near the top of the page, below the [!UICONTROL Dynamic Media Encode Video] page title, click **[!UICONTROL Save]**.

## Veröffentlichen von Video-Assets {#publish-video-assets}

Nach der Veröffentlichung können Sie die Video-Assets als URL in eine Webseite einbetten oder die Assets direkt einbetten. Weitere Informationen finden Sie unter [Veröffentlichen von dynamischen Medienelementen](/help/assets/publishing-dynamicmedia-assets.md).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotate-video-assets}

1. From the [!DNL Assets] console, click [!UICONTROL Edit] on the asset card to display the asset details page.
1. Um das Video abzuspielen, klicken Sie auf [!UICONTROL Vorschau].
1. Um das Video zu kommentieren, klicken Sie auf die Schaltfläche **[!UICONTROL Kommentieren]**. Eine Anmerkung wird zur bestimmten Zeit (Frame) im Video hinzugefügt. Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch gespeichert.

   ![Zeichnen und kommentieren in einem Videoframe](assets/annotate-video.png)

   Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**.

1. Suchen Sie nach einem bestimmten Punkt im Video, indem Sie die Zeit in Sekunden in das **Textfeld** eingeben und auf **Springen** klicken. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie „20“ in das Textfeld ein.

   ![Seek to a time in a video to skip by specified seconds](assets/seek-in-video.png)

1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

   ![View annotations and the details in the timeline](assets/timeline-view-annotation.png)

>[!MORELIKETHIS]
>
>* [Manage digital assets in Experience Manager Assets](/help/assets/managing-assets-touch-ui.md)
>* [Verwalten von Sammlungen in Experience Manager-Assets](/help/assets/managing-collections-touch-ui.md)

