---
title: Einschränkungen beim Hochladen von Assets konfigurieren
description: 'Beschränken der Art von Assets (Dateien), die Benutzer hochladen können '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 55%

---


# Einschränkungen beim Hochladen von Assets konfigurieren {#configuring-asset-upload-restrictions}

You can configure [!DNL Adobe Experience Manager Assets] to restrict the type of assets that users can upload. Dadurch wird verhindert, dass versehentliche Uploads unerwünschter Formate und böswilliger Dateien erfolgen. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien, die Benutzer hochladen können, zu steuern. By default, [!DNL Assets] allows users to upload assets of all MIME types. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Öffnen Sie die Web-Konsole „Configuration Manager“. Greife Sie auf `https://[aem_server]:[port]/system/console/configMgr` zu.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. To restrict users to upload files of certain MIME types only, unselect the **[!UICONTROL Allow all MIME]** option and specify allowed MIME types in the **[!UICONTROL Allowed Asset MIMEs (regex)]** fields using regular expressions.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
