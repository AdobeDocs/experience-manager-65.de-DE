---
title: '[!DNL Adobe Camera Raw]-Unterstützung.'
description: Erfahren Sie, wie Sie die Unterstützung [!DNL Adobe Camera Raw] aktivieren [!DNL Adobe Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: b2628d37c3ad158913c28ecd890aee9fd0106de4
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 30%

---


# Bilder mit Camera Raw verarbeiten {#camera-raw-support}

Sie können die [!DNL Adobe Camera Raw] Unterstützung aktivieren, um Rohdateiformate wie CR2, NEF und RAF zu verarbeiten und die Bilder im JPEG-Format zu rendern. Die Funktion wird bei [!DNL Adobe Experience Manager Assets] der Verwendung des [Camera Raw-Pakets](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) unterstützt, das über Package Share verfügbar ist.

>[!NOTE]
>
>Die Funktion unterstützt nur JPEG-Darstellungen. Es wird unter Windows 64 Bit, Mac OS und RHEL 7.x unterstützt.

Gehen Sie wie folgt vor, um die [!DNL Camera Raw] Unterstützung in [!DNL Experience Manager Assets]zu aktivieren:

1. Laden Sie das [Camera Raw-Paket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) von Package Share oder von der [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem620/product/assets/aem-assets-cameraraw-pkg)herunter.
1. Greife Sie auf `https://[aem_server]:[port]/workflow` zu. Open the **[!UICONTROL DAM Update Asset]** workflow.
1. Open the **[!UICONTROL Process Thumbnails]** step.
1. Provide the following configuration in the **[!UICONTROL Thumbnails]** tab:

   * **[!UICONTROL Miniaturansichten]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL MIME-Typen überspringen]**: `skip:image/dng, skip:image/x-raw-(.*)`
   ![chlimage_1-128](assets/chlimage_1-334.png)

1. Geben Sie auf der Registerkarte &quot; **[!UICONTROL Web-aktiviertes Bild]** &quot;im Feld &quot;Liste **** überspringen&quot; `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![chlimage_1-129](assets/chlimage_1-335.png)

1. From the side panel, add the **[!UICONTROL Camera Raw/DNG Handler]** step below the **[!UICONTROL Thumbnail creation]** step.
1. In the **[!UICONTROL Camera Raw/DNG Handler]** step, add the following configuration in the **[!UICONTROL Arguments]** tab:

   * **[!UICONTROL Mime-Typen]**: `image/dng` und `image/x-raw-(.*)`
   * **[!UICONTROL Befehl]**:

      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.web.1280.1280.jpeg 1280 1280`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.319.319.jpeg 319 319`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.140.100.jpeg 140 100`
      * `DAM_Raw_Converter ${directory}/${filename} ${directory} cq5dam.thumbnail.48.48.jpeg 48 48`
   ![chlimage_1-130](assets/chlimage_1-336.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Stellen Sie sicher, dass die oben aufgeführte Konfiguration mit der Konfiguration **** Beispiel-DAM-Update-Asset mit Schritt für Camera RAW- und DNG-Handling übereinstimmt.

Nun können Sie Camera Raw-Dateien in  Assets importieren. After you install the Camera RAW package and configure the required workflow, **[!UICONTROL Image Adjust]** option appears in the list of side panes.

![chlimage_1-131](assets/chlimage_1-337.png)

*Abbildung: Optionen im Seitenbereich.*

![chlimage_1-132](assets/chlimage_1-338.png)

*Abbildung: Verwenden Sie diese Option, um Ihre Bilder leichter zu bearbeiten.*

After saving the edits to a [!DNL Camera Raw] image, a new rendition `AdjustedPreview.jpg` is generated for the image. For other image types except [!DNL Camera Raw], the changes are reflected in all the renditions.

## Best Practices, bekannte Probleme und Einschränkungen {#best-practices}

Für die Funktionalität gelten folgende Einschränkungen:

* Die Funktion unterstützt nur JPEG-Darstellungen. Sie wird unter 64-Bit Windows, macOS und RHEL 7.x unterstützt.
* Metadaten-Writeback wird für RAW- und DNG-Formate nicht unterstützt.
* The [!DNL Camera Raw] library has limitations around the total pixels it can process at a time. Derzeit kann eine Datei maximal 65000 Pixel auf der langen Seite oder 512 MP verarbeitet werden, je nachdem, welches Kriterium zuerst erfüllt wird.
