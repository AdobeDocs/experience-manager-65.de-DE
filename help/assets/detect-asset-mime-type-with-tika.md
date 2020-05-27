---
title: MIME-Typ von Assets mithilfe von Apache Tika erkennen
description: Aktivieren Sie Apache Tika, damit Experience Manager Assets den MIME-Typ von Assets aus dem Inhaltsstream während des Upload-Vorgangs und nicht die Dateierweiterung erkennen kann.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 10%

---


# Detect MIME type of assets using Apache Tika {#detecting-mime-type-of-assets-using-apache-tika}

In der Regel erkennt Adobe Experience Manager Assets den MIME-Typ von Assets, die Sie von ihrer Dateierweiterung hochladen.

Wenn Sie Apache Tika verwenden, um Assets hochzuladen, erkennt Assets den MIME-Typ, den sie während des Upload-Vorgangs vom Inhaltsstream und nicht von der Dateierweiterung unterscheiden.

Diese Funktion ist standardmäßig deaktiviert.  To enable the feature, configure the **[!UICONTROL Day CQ DAM Mime Type]** service from [!UICONTROL Configuration Manager].

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Um die Configuration Manager-Webkonsole zu öffnen, öffnen Sie `https://[aem_server]:[port]/system/console/configMgr`.

1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Select the **[!UICONTROL Detect MIME from content]** option to enable the parsing of uploaded assets to determine their MIME type while ignoring file extensions. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
