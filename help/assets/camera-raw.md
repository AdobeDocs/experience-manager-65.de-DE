---
title: „[!DNL Adobe Camera Raw]-Unterstützung für die Verarbeitung digitaler Assets“
description: Erfahren Sie, wie Sie die  [!DNL Adobe Camera Raw] -Unterstützung in [!DNL Adobe Experience Manager Assets] aktivieren
contentOwner: AG
role: Admin
feature: Developer Tools
exl-id: 7159a908-4c36-42b4-bbb4-d7fb1be4ee1b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 90%

---

# Bildverarbeitung mit [!DNL Adobe Camera Raw] {#camera-raw-support}

Sie können die [!DNL Adobe Camera Raw]-Unterstützung für die Verarbeitung von Rohdatenformaten wie CR2, NEF und RAF sowie das Rendern der Bilder im JPEG-Format aktivieren. Die Funktion wird in [!DNL Adobe Experience Manager Assets] mithilfe des [Camera RAW-Pakets](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-cameraraw-pkg) unterstützt, das über Software Distribution verfügbar ist.

>[!NOTE]
>
>Die Funktion unterstützt nur JPEG-Darstellungen. Sie wird unter Windows 64-Bit, macOS und RHEL 7.x unterstützt.

Gehen Sie zum Aktivieren der [!DNL Camera Raw]-Unterstützung in [!DNL Experience Manager Assets] folgendermaßen vor:

1. Laden Sie das [[!DNL Camera Raw] Paket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/aem-assets-cameraraw-pkg-1.4.8.zip) von [!DNL Software Distribution] herunter.
1. Greife Sie auf `https://[aem_server]:[port]/workflow` zu. Öffnen Sie den Workflow **[!UICONTROL DAM-Update-Asset]**.
1. Bearbeiten Sie den Schritt **[!UICONTROL Miniaturen verarbeiten]**.
1. Legen Sie auf der Registerkarte **[!UICONTROL Miniaturansichten]** folgende Konfiguration fest:

   * **[!UICONTROL Miniaturansichten]**: `140:100:false, 48:48:false, 319:319:false`
   * **[!UICONTROL MIME-Typen überspringen]**: `skip:image/dng, skip:image/x-raw-(.*)`

   ![chlimage_1-128](assets/chlimage_1-334.png)

1. Geben Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** im Feld **[!UICONTROL Liste überspringen]** `audio/mpeg, video/(.*), image/dng, image/x-raw-(.*)` an.

   ![chlimage_1-129](assets/chlimage_1-335.png)

1. Fügen Sie im seitlichen Bedienfeld den Schritt **[!UICONTROL Camera Raw/DNG Handler]** unter dem Schritt **[!UICONTROL Miniaturen verarbeiten]** hinzu.
1. Fügen Sie im Schritt **[!UICONTROL Camera Raw/DNG Handler]** auf der Registerkarte **[!UICONTROL Argumente]** die folgende Konfiguration hinzu:

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
>Stellen Sie sicher, dass die oben aufgeführte Konfiguration mit der Konfiguration **[!UICONTROL Beispiel-DAM-Update-Asset mit Schritt für Camera RAW- und DNG-Handling]** übereinstimmt.

Nun können Sie Camera Raw-Dateien in Assets importieren. Nach der Installation des Camera RAW-Pakets und der Konfiguration des erforderlichen Workflows wird die Option **[!UICONTROL Bildanpassung]** in der Liste der seitlichen Bedienfelder angezeigt.

![chlimage_1-131](assets/chlimage_1-337.png)

*Abbildung: Optionen im seitlichen Bedienfeld.*

![chlimage_1-132](assets/chlimage_1-338.png)

*Abbildung: Verwenden Sie die Option, um Ihre Bilder geringfügig zu bearbeiten.*

Nach Speichern der Änderungen in einem [!DNL Camera Raw]-Bild wird die neue Ausgabedarstellung `AdjustedPreview.jpg` für das Bild erstellt. Für andere Bildtypen als [!DNL Camera Raw] werden die Änderungen in allen Ausgabedarstellungen übernommen.

## Best Practices, bekannte Probleme und Einschränkungen {#best-practices}

Die Funktionalität weist die folgenden Einschränkungen auf:

* Die Funktion unterstützt nur JPEG-Darstellungen. Es wird unter Windows 64 Bit, Mac OS und RHEL 7.x unterstützt.
* Metadaten-Writeback wird für RAW- und DNG-Formate nicht unterstützt.
* Für die [!DNL Camera Raw]-Bibliothek gelten Beschränkungen bei der gleichzeitig verarbeiteten Gesamtanzahl von Pixeln. Derzeit kann sie eine maximale Größe von 65.000 Pixel auf der langen Seite einer Datei oder 512 MP verarbeiten, je nachdem, welches Kriterium zuerst erfüllt wird.
