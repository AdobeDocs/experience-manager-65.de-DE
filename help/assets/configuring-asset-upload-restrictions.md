---
title: Einschränkungen beim Hochladen von Assets konfigurieren
description: 'Beschränken der Art von Assets (Dateien), die Benutzer hochladen können '
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Einschränkungen beim Hochladen von Assets konfigurieren {#configuring-asset-upload-restrictions}

Sie können Adobe Experience Manager (AEM) Assets so konfigurieren, dass der von den Benutzern hochladbare Typ von Assets (Dateien) eingeschränkt ist. Mit dieser Funktion können Sie verhindern, dass Benutzer Assets in einem unerwünschten Format oder schädliche Dateien hochladen. The `Day CQ DAM Asset Upload Restriction` service enables you to control the type of files that users can upload. Standardmäßig lässt es AEM Assets zu, dass Benutzer Assets aller MIME-Typen hochladen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Öffnen Sie die Configuration Manager-Webkonsole. Zugriff `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Day CQ DAM Asset Upload Restriction]** service in Edit mode. By default, the **Allow all MIME** option is selected, which allows users to upload files of all MIME types.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. To restrict users to upload files of certain MIME types only, unselect the **[!UICONTROL Allow all MIME]** option and specify allowed MIME types in the **[!UICONTROL Allowed Asset MIMEs (regex)]** fields using regular expressions.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Click/tap **[!UICONTROL Save]** to save the changes. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Uploadvorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
