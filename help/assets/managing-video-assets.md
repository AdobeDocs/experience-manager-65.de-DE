---
title: 'Verwalten von Video-Assets   '
description: Hochladen, Vorschau, Anmerkungen und Veröffentlichen von Video-Assets [!DNL Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 36%

---


# Verwalten von Video-Assets    {#manage-video-assets}

Das Videoformat ist ein wichtiger Bestandteil digitaler Assets eines Unternehmens. [!DNL Adobe Experience Manager] angebote bieten und verwalten den gesamten Lebenszyklus Ihrer Video-Assets nach deren Erstellung.

Learn how to manage and edit the video assets in [!DNL Adobe Experience Manager Assets]. Videokodierung und -transkodierung, z. B. FFmpeg-Transkodierung, sind über die [!DNL Dynamic Media] Integration möglich.

## Hochladen und Anzeigen der Vorschau von Video-Assets {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] generiert Vorschauen für Video-Assets mit der Erweiterung MP4. Wenn das Asset nicht im MP4-Format vorliegt, installieren Sie das FFmpeg-Paket, um eine Vorschau zu generieren. FFmpeg erstellt Videodarstellungen vom Typ OGG und MP4. You can preview the renditions in the [!DNL Assets] user interface.

1. Navigieren Sie im Ordner oder in den Unterordnern für digitale Assets zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. To upload the asset, click **[!UICONTROL Create]** from the toolbar and choose **[!UICONTROL Files]**. Alternativ können Sie eine Datei auf die Benutzeroberfläche ziehen. Weitere Informationen finden Sie unter [Hochladen von Assets](manage-assets.md#uploading-assets).
1. To preview a video in the Card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. Sie können Videos nur in der Kartenansicht anhalten oder wiedergeben. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.

1. To preview the video in the asset details page, click **[!UICONTROL Edit]** on the card. Das Video wird im systemeigenen Video-Player des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

   ![Steuerelemente für die Videowiedergabe](assets/video-playback-controls.png)

## Konfiguration zum Hochladen von Assets, die größer als 2 GB sind {#configuration-to-upload-assets-that-are-larger-than-gb}

By default, [!DNL Assets] does not let you upload any assets that are larger than 2 GB because of a file size limit. Sie können diese Beschränkung aber umgehen, indem Sie CRXDE Lite aufrufen und im Verzeichnis `/apps` einen Knoten erstellen. Der Knoten muss denselben Knotennamen, dieselbe Verzeichnisstruktur und vergleichbare Knoteneigenschaften im Hinblick auf die Reihenfolge aufweisen.

In addition to [!DNL Assets] configuration, change the following configurations to upload large assets:

* Erhöhen Sie die Ablaufzeit des Tokens. Siehe [!UICONTROL Adobe Granite CSRF Servlet] in Web Console unter `https://[aem_server]:[port]/system/console/configMgr`. Weitere Informationen finden Sie unter [CSRF-Schutz](/help/sites-developing/csrf-protection.md).
* Erhöhen Sie `receiveTimeout` in der Dispatcher-Konfiguration. Weitere Informationen finden Sie unter [Experience Manager Dispatcher-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>The [!DNL Experience Manager] Classic user interface does not have a 2-GB file size limit restriction. Außerdem werden End-to-End-Workflows für große Videos nicht vollständig unterstützt.

Um eine höhere Dateigrößenbeschränkung zu konfigurieren, führen Sie die folgenden Schritte im Verzeichnis `/apps` aus.

1. In [!DNL Experience Manager], click **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in CRXDE Lite zu `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. To see the directory window, click the `>>`.
1. From the toolbar, click the **[!UICONTROL Overlay Node]**. Wählen Sie alternativ **[!UICONTROL Überlagerungsknoten]** aus dem Kontextmenü aus.
1. In the **[!UICONTROL Overlay Node]** dialog, click **[!UICONTROL OK]**.

   ![Überlagerungsknoten](assets/overlay-node-path.png)

1. Aktualisieren Sie die Browser-Ansicht. Der Überlagerungsknoten `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` ist ausgewählt.
1. Geben Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** den gewünschten Wert in Byte ein, um die maximale Größe festzulegen. Um beispielsweise die Größenbeschränkung auf 30 GB zu erhöhen, geben Sie den Wert `32212254720` ein.

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

Nach der Veröffentlichung können Sie die Video-Assets als URL in eine Webseite einbetten oder die Assets direkt einbetten. Weitere Informationen finden Sie unter [Veröffentlichen von Dynamischen Medien-Assets](/help/assets/publishing-dynamicmedia-assets.md).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotate-video-assets}

1. Wählen Sie in der [!DNL Assets] Konsole auf der Asset-Karte die Option **[!UICONTROL Bearbeiten]** , um die Seite mit den Asset-Details anzuzeigen.
1. Um das Video abzuspielen, klicken Sie auf **[!UICONTROL Vorschau]**.
1. To annotate the video, click **[!UICONTROL Annotate]**. Eine Anmerkung wird zur bestimmten Zeit (Frame) im Video hinzugefügt. Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch gespeichert. Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**.

   ![Zeichnen und kommentieren in einem Videoframe](assets/annotate-video.png)

1. Suchen Sie nach einem bestimmten Punkt im Video, indem Sie die Zeit in Sekunden in das **Textfeld** eingeben und auf **Springen** klicken. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie „20“ in das Textfeld ein.

   ![Suche nach einer Zeit in einem Video, um nach einer bestimmten Sekunde zu überspringen](assets/seek-in-video.png)

1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

   ![Anmerkungen zur Ansicht und Details in der Zeitleiste](assets/timeline-view-annotation.png)

>[!MORELIKETHIS]
>
>* [Digitale Assets in Experience Manager-Assets verwalten](/help/assets/manage-assets.md)
>* [Verwalten von Sammlungen in Experience Manager-Assets](/help/assets/manage-collections.md)
>* [Dokumentation](/help/assets/video.md)zu Videos zu dynamischen Medien

