---
title: '"[!DNL Adobe Camera Raw] Unterstützung für die Verarbeitung digitaler Assets"'
description: Erfahren Sie, wie Sie [!DNL Adobe Camera Raw] Unterstützung in [!DNL Adobe Experience Manager Assets]
contentOwner: AG
role: Admin
feature: Developer Tools
exl-id: 7159a908-4c36-42b4-bbb4-d7fb1be4ee1b
source-git-commit: e24316cb9495a552960ae0620e4198f10a08b691
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 29%

---

# Bilder verarbeiten mit [!DNL Adobe Camera Raw] {#camera-raw-support}

Sie können die [!DNL Adobe Camera Raw] Unterstützung für die Verarbeitung von Rohdateiformaten wie CR2, NEF und RAF sowie das Rendern der Bilder im JPEG-Format. Die Funktion wird in [!DNL Adobe Experience Manager Assets] mithilfe der [Camera Raw Package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) über Softwareverteilung verfügbar.

>[!NOTE]
>
>Die Funktion unterstützt nur JPEG-Darstellungen. Es wird unter Windows 64 Bit, Mac OS und RHEL 7.x unterstützt.

Aktivieren [!DNL Camera Raw] Unterstützung in [!DNL Experience Manager Assets]führen Sie die folgenden Schritte aus:

1. Laden Sie die [[!DNL Camera Raw] package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-cameraraw-pkg-1.4.8.zip) von [!DNL Software Distribution].
1. Greife Sie auf `https://[aem_server]:[port]/workflow` zu. Öffnen Sie die **[!UICONTROL DAM-Update-Asset]** Arbeitsablauf.
1. Bearbeiten Sie die **[!UICONTROL Prozessminiaturansichten]** Schritt.
1. Stellen Sie die folgende Konfiguration in der **[!UICONTROL Miniaturen]** tab:

   * **[!UICONTROL Miniaturen]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL MIME-Typen überspringen]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage_1-128](assets/chlimage_1-334.png)

1. Im **[!UICONTROL Webfähiges Bild]** im **[!UICONTROL Liste überspringen]** Feld, geben Sie `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)`.

   ![chlimage_1-129](assets/chlimage_1-335.png)

1. Fügen Sie im seitlichen Bedienfeld die **[!UICONTROL Camera Raw/DNG Handler]** Schritt unter dem **[!UICONTROL Prozessminiaturansichten]** Schritt.
1. Im **[!UICONTROL Camera Raw/DNG Handler]** Fügen Sie im Schritt die folgende Konfiguration hinzu. **[!UICONTROL Argumente]** tab:

   * **[!UICONTROL MIME-Typen]**: `image/dng` und `image/x-raw-(.*)`
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

Nun können Sie Camera Raw-Dateien in  Assets importieren. Nachdem Sie das Camera Raw Paket installiert und den erforderlichen Workflow konfiguriert haben, **[!UICONTROL Bildanpassung]** in der Liste der Seitenfenster angezeigt.

![chlimage_1-131](assets/chlimage_1-337.png)

*Abbildung: Optionen im Seitenbereich.*

![chlimage_1-132](assets/chlimage_1-338.png)

*Abbildung: Verwenden Sie die Option , um Ihre Bilder geringfügig zu bearbeiten.*

Nach dem Speichern der Änderungen in einer [!DNL Camera Raw] Bild, eine neue Ausgabedarstellung `AdjustedPreview.jpg` wird für das Bild generiert. Für andere Bildtypen außer [!DNL Camera Raw], werden die Änderungen in allen Ausgabedarstellungen übernommen.

## Best Practices, bekannte Probleme und Einschränkungen {#best-practices}

Für die Funktionalität gelten folgende Einschränkungen:

* Die Funktion unterstützt nur JPEG-Darstellungen. Sie wird unter 64-Bit Windows, macOS und RHEL 7.x unterstützt.
* Metadaten-Writeback wird für RAW- und DNG-Formate nicht unterstützt.
* Die [!DNL Camera Raw] -Bibliothek hat Einschränkungen hinsichtlich der Gesamtanzahl der Pixel, die gleichzeitig verarbeitet werden können. Derzeit kann es eine maximale Größe von 65000 Pixel auf der langen Seite einer Datei oder 512 MP verarbeiten, je nachdem, welches Kriterium zuerst erfüllt wird.
