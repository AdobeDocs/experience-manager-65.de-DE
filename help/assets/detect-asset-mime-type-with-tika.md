---
title: MIME-Typ von Assets mithilfe von Apache Tika erkennen
description: Enable Apache Tika to help [!DNL Experience Manager Assets] detect the MIME type of assets from the content stream during the upload operation instead of the file extension.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 11%

---


# MIME-Typ von Assets erkennen mit [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika}

Normally, [!DNL Adobe Experience Manager Assets] detects the MIME type of assets that you upload from their file extension.

If you use [!DNL Apache Tika] to upload assets, [!DNL Assets] detects their MIME type from the content stream during the upload operation instead of the file extension.

Diese Funktion ist standardmäßig deaktiviert.  To enable the feature, configure the **[!UICONTROL Day CQ DAM Mime Type]** service from [!UICONTROL Configuration Manager].

>[!NOTE]
>
>MIME type detection using the [!DNL Apache Tika] library is a resource-intensive operation.

1. Um die Configuration Manager-Webkonsole zu öffnen, öffnen Sie `https://[aem_server]:[port]/system/console/configMgr`.

1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Select the **[!UICONTROL Detect MIME from content]** option to enable the parsing of uploaded assets to determine their MIME type while ignoring file extensions. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
