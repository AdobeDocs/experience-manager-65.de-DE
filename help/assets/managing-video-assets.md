---
title: Verwalten von Video-Assets
description: Erfahren Sie, wie Sie Video-Assets hochladen und veröffentlichen, eine Vorschau der entsprechenden Assets anzeigen und Anmerkungen hinzufügen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 64%

---


# Verwalten von Video-Assets  {#manage-video-assets}

Erfahren Sie, wie Sie die Video-Assets in Adobe Experience Manager Assets verwalten und bearbeiten. Wenn Sie eine Lizenz für die Nutzung von Dynamic Media besitzen, sehen Sie sich die [Dynamic Media-Videodokumentation](/help/assets/video.md) an.

## Hochladen und Anzeigen der Vorschau von Video-Assets {#upload-and-preview-video-assets}

Adobe Experience Manager Assets generiert Vorschauen für Video-Assets mit der Erweiterung MP4. Wenn das Asset nicht im MP4-Format vorliegt, installieren Sie das FFmpeg-Paket, um eine Vorschau zu generieren. FFmpeg erstellt Videodarstellungen vom Typ OGG und MP4. Sie können eine Vorschau dieser Wiedergaben in der Benutzeroberfläche von Assets anzeigen.

1. Navigieren Sie im Ordner „Digitale Assets“ (oder dessen Unterordnern) zum Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. To upload the asset, click **[!UICONTROL Create]** from the toolbar and then choose **[!UICONTROL Files]**. Alternativ können Sie sie direkt in den Assets-Bereich ziehen. Weitere Informationen zum Hochladen finden Sie unter [Hochladen von Assets](managing-assets-touch-ui.md#uploading-assets).
1. To preview a video in the Card view, click the **[!UICONTROL Play]** button on the video asset.

   ![chlimage_1-65](assets/chlimage_1-201.png)

   Sie können Videos nur in der Kartenansicht anhalten oder wiedergeben. Die Schaltflächen [!UICONTROL Wiedergabe] und [!UICONTROL Pause] sind in der Listenansicht nicht verfügbar.

1. To preview the video in the asset details page, click the **[!UICONTROL Edit]** icon on the card.

   Das Video wird im systemeigenen Video-Player des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

   ![chlimage_1-66](assets/chlimage_1-202.png)

## Konfiguration zum Hochladen von Assets, die größer als 2 GB sind {#configuration-to-upload-assets-that-are-larger-than-gb}

Sie können aufgrund einer Größenbeschränkung für Dateien standardmäßig keine Assets über Experience Manager Assets hochladen, die größer als 2 GB sind. Sie können diese Beschränkung aber umgehen, indem Sie CRXDE Lite aufrufen und im Verzeichnis `/apps` einen Knoten erstellen. Der Knoten muss denselben Knotennamen, dieselbe Verzeichnisstruktur und vergleichbare Knoteneigenschaften im Hinblick auf die Reihenfolge aufweisen.

Ändern Sie zusätzlich zur Konfiguration von Experience Manager Assets die folgenden Konfigurationen, um große Assets hochzuladen:

* Erhöhen Sie die Ablaufzeit des Tokens. Siehe [!UICONTROL Adobe Granite CSRF Servlet] in Web Console unter `https://[aem_server]:[port]/system/console/configMgr`. Weitere Informationen finden Sie unter [CSRF-Schutz](/help/sites-developing/csrf-protection.md).
* Erhöhen Sie `receiveTimeout` in der Dispatcher-Konfiguration. Weitere Informationen finden Sie unter [Experience Manager Dispatcher-Konfiguration](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>Für die Benutzeroberfläche von Experience Manager Classic gelten keine 2-GB-Dateigrößenbeschränkungen. Außerdem werden End-to-End-Workflows für große Videos nicht vollständig unterstützt.

Um eine höhere Dateigrößenbeschränkung zu konfigurieren, führen Sie die folgenden Schritte im Verzeichnis `/apps` aus.

1. In Experience Manager, click **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in CRXDE Lite zu `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Um das Verzeichnisfenster anzuzeigen, tippen Sie auf das `>>`-Symbol.
1. From the toolbar, click the **[!UICONTROL Overlay Node]**. Wählen Sie alternativ **[!UICONTROL Überlagerungsknoten]** aus dem Kontextmenü aus.
1. In the **[!UICONTROL Overlay Node]** dialog, click **[!UICONTROL OK]**.

   ![chlimage_1-67](assets/chlimage_1-203.png)

1. Aktualisieren Sie die Browser-Ansicht. Der Überlagerungsknoten `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` ist ausgewählt.
1. Geben Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** den gewünschten Wert in Byte ein, um die maximale Größe festzulegen. Um beispielsweise die Größenbeschränkung auf 30 GB zu erhöhen, geben Sie den Wert `{sizeLimit : "32212254720"}` ein.

1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Alle speichern]**.
1. Klicken Sie in Experience Manager auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. On the Adobe Experience Manager Web Console Bundles page, under the Name column of the table, locate and click **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Stellen Sie auf der Seite „Adobe Granite Workflow External Process Job Handler“ die Sekunden für die Felder **[!UICONTROL Timeout-Standardwert]** und **[!UICONTROL Max. Timeout]** auf `18000` (fünf Stunden) ein.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie in Experience Manager auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. On the Workflow Models page, select **[!UICONTROL Dynamic Media Encode Video]**, then click **[!UICONTROL Edit]**.
1. On the workflow page, double-click the **[!UICONTROL Dynamic Media Video Service Process]** component.
1. Erweitern Sie im Dialogfeld [!UICONTROL Schritteigenschaften] auf der Registerkarte **[!UICONTROL Allgemein]** die Option **Erweiterte Einstellungen**.
1. In the **[!UICONTROL Timeout]** field, specify a value of `18000`, then click **[!UICONTROL OK]** to return to the **[!UICONTROL Dynamic Media Encode Video]** workflow page.
1. Near the top of the page, below the Dynamic Media Encode Video page title, click **[!UICONTROL Save]**.

## Veröffentlichen von Video-Assets {#publish-video-assets}

Nach dem Veröffentlichen Ihrer Video-Assets können diese über eine URL auf einer Web-Seite eingebunden oder eingebettet werden. Informationen hierzu finden Sie unter [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotate-video-assets}

1. From the Assets console, click the [!UICONTROL Edit] icon on the asset card to display the asset details page.
1. To play the video, click the [!UICONTROL Preview] icon.
1. Um das Video zu kommentieren, klicken Sie auf die Schaltfläche **[!UICONTROL Kommentieren]**. Eine Anmerkung wird an diesem speziellen Zeitpunkt (Frame) im Video hinzugefügt. Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch gespeichert.

   ![chlimage_1-68](assets/chlimage_1-204.png)

   Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**.

1. Suchen Sie nach einem bestimmten Punkt im Video, indem Sie die Zeit in Sekunden in das **Textfeld** eingeben und auf **Springen** klicken. Um beispielsweise die ersten 10 Sekunden des Videos zu überspringen, geben Sie „20“ in das Textfeld ein.

   ![chlimage_1-69](assets/chlimage_1-205.png)

1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

   ![chlimage_1-70](assets/chlimage_1-206.png)
