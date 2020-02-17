---
title: Verwalten von Video-Assets
description: Erfahren Sie, wie Sie Video-Assets hochladen und veröffentlichen, eine Vorschau der entsprechenden Assets anzeigen und Anmerkungen hinzufügen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Verwalten von Video-Assets {#manage-video-assets}

Lernen Sie, wie Sie die Video-Assets in Adobe Experience Manager (AEM) Assets verwalten und bearbeiten. Wenn Sie eine Lizenz für die Nutzung von Dynamic Media besitzen, sehen Sie sich die [Dynamic Media-Videodokumentation](/help/assets/video.md) an.

## Upload and preview video assets {#upload-and-preview-video-assets}

Adobe Experience Manager Assets generiert Vorschauen für Video-Assets mit der Erweiterung MP4. Wenn das Format des Assets nicht MP4 ist, installieren Sie das FFmpeg-Paket, um eine Vorschau zu generieren. FFmpeg erstellt Videodarstellungen vom Typ OGG und MP4. Sie können eine Vorschau dieser Wiedergaben in der Benutzeroberfläche von AEM Assets anzeigen.

1. Navigieren Sie im Ordner „Digitale Assets“ (oder dessen Unterordnern) zum Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Um Assets hochzuladen, klicken oder tippen Sie in der Symbolleiste auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Dateien]** aus. Alternativ können Sie sie direkt in den Assets-Bereich ziehen. See [Uploading assets](managing-assets-touch-ui.md#uploading-assets) for details around the upload operation.
1. To preview a video in the Card view, tap the **[!UICONTROL Play]** button on the video asset.

   ![chlimage_1-65](assets/chlimage_1-201.png)

   Sie können Videos nur in der Kartenansicht anhalten oder abspielen. Die [!UICONTROL Schaltflächen &quot;Abspielen] &quot;und &quot; [!UICONTROL Anhalten] &quot;stehen in der Listenansicht nicht zur Verfügung.

1. To preview the video in the asset details page, click or tap the **[!UICONTROL Edit]** icon on the card.

   Das Video wird im systemeigenen Videoplayer des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

   ![chlimage_1-66](assets/chlimage_1-202.png)

## Configuration to upload assets that are larger than 2 GB {#configuration-to-upload-assets-that-are-larger-than-gb}

Standardmäßig können Sie mit den Experience Manager-Assets keine Assets hochladen, die aufgrund einer Dateigrößenbeschränkung größer als 2 GB sind. However, you can overwrite this limit by going into CRXDE Lite and creating a node under the `/apps` directory. Der Knoten muss denselben Knotennamen, dieselbe Verzeichnisstruktur und vergleichbare Knoteneigenschaften im Hinblick auf die Reihenfolge aufweisen.

Zusätzlich zur Experience Manager Assets-Konfiguration ändern Sie die folgenden Konfigurationen, um große Assets hochzuladen:

* Erhöhen Sie die Ablaufzeit des Tokens. Siehe [!UICONTROL Adobe Granite CSRF Servlet] in Web Console unter `https://[aem_server]:[port]/system/console/configMgr`. Weitere Informationen finden Sie unter [CSRF-Schutz](/help/sites-developing/csrf-protection.md).
* Erhöhen Sie die `receiveTimeout` in der Dispatcher-Konfiguration. Weitere Informationen finden Sie unter [Experience Manager Dispatcher-Konfiguration](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>Die klassische Benutzeroberfläche von AEM hat keine Dateigrößenbeschränkung von 2 GB. Außerdem werden End-to-End-Workflows für große Videos nicht vollständig unterstützt.

To configure a higher file size limit, perform the following steps in the `/apps` directory.

1. Tippen Sie in AEM auf **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in CRXDE Lite zu `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. To see the directory window, touch the `>>` icon.
1. From the toolbar, tap the **[!UICONTROL Overlay Node]**. Alternatively, select **[!UICONTROL Overlay Node]** from the context menu.
1. In the **[!UICONTROL Overlay Node]** dialog, tap **[!UICONTROL OK]**.

   ![chlimage_1-67](assets/chlimage_1-203.png)

1. Aktualisieren Sie die Browser-Ansicht. Der Überlagerungsknoten `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` ist ausgewählt.
1. In the **[!UICONTROL Properties]** tab, enter the appropriate value in bytes to increase the size limit to the desired size. Geben Sie zum Beispiel einen Wert ein, um die maximale Größe auf 30 GB zu erhöhen `{sizeLimit : "32212254720"}` .

1. From the toolbar, touch **[!UICONTROL Save All]**.
1. Tippen Sie in AEM auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. On the Adobe Experience Manager Web Console Bundles page, under the Name column of the table, locate and tap **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Stellen Sie auf der Seite „Adobe Granite Workflow External Process Job Handler“ die Sekunden für die Felder **[!UICONTROL Timeout-Standartwert]** und **[!UICONTROL Max. Timeout]** auf `18000` (fünf Stunden) ein.
1. Tippen Sie auf **[!UICONTROL Speichern]**.
1. Tippen Sie in AEM auf **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite „Workflow-Modelle“ die Option **[!UICONTROL Dynamic Media-Videokodierung]** aus und tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Doppeltippen Sie auf der Workflow-Seite auf die Komponente **[!UICONTROL Prozess für Videodienst für dynamische Medien]**.
1. In the [!UICONTROL Step Properties] dialog box, under the **[!UICONTROL Common]** tab, expand **Advanced Settings**.
1. In the **[!UICONTROL Timeout]** field, specify a value of `18000`, then tap **[!UICONTROL OK]** to return to the **[!UICONTROL Dynamic Media Encode Video]** workflow page.
1. Tippen Sie oben auf der Seite unter dem Seitentitel „Dynamic Media-Videokodierung“ auf **[!UICONTROL Speichern]**.

## Veröffentlichen von Video-Assets {#publish-video-assets}

Nach dem Veröffentlichen Ihrer Video-Assets können diese über eine URL auf einer Webseite eingebunden oder eingebettet werden. See [publishing assets](/help/assets/publishing-dynamicmedia-assets.md).

## Video-Assets kommentieren {#annotate-video-assets}

1. From the Assets console, click or tap the [!UICONTROL Edit] icon on the asset card to display the asset details page.
1. To play the video, click or tap the [!UICONTROL Preview] icon.
1. To annotate the video, click the **[!UICONTROL Annotate]** button. Eine Anmerkung wird an diesem speziellen Zeitpunkt (Frame) im Video hinzugefügt. Wenn Sie kommentieren, können Sie auf die Arbeitsfläche zeichnen und einen Kommentar mit der Zeichnung einschließen. Kommentare werden automatisch gespeichert.

   ![chlimage_1-68](assets/chlimage_1-204.png)

   Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**. 

1. Seek to a specific point in the video, specify the time in seconds in the **text** field and click **Jump**. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie 10 in das Textfeld ein.

   ![chlimage_1-69](assets/chlimage_1-205.png)

1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

   ![chlimage_1-70](assets/chlimage_1-206.png)
