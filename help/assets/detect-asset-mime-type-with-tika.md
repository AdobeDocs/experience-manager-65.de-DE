---
title: MIME-Typ von Assets mithilfe von Apache Tika erkennen
description: Aktivieren Sie Apache Tika, damit AEM Assets beim Upload-Vorgang den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung erkennen kann.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 50%

---


# Detect MIME type of assets using Apache Tika {#detecting-mime-type-of-assets-using-apache-tika}

Normalerweise erkennt Adobe Experience Manager (AEM) Assets den MIME-Typ der von Ihnen hochgeladenen Assets anhand der Dateierweiterung.  

Wenn Sie Apache Tika verwenden, um Assets hochzuladen, erkennt AEM Assets deren MIME-Typ durch den Content Stream während des Uploadvorgangs statt durch die Dateierweiterung. 

Diese Funktion ist standardmäßig deaktiviert.  To enable the feature, configure the **[!UICONTROL Day CQ DAM Mime Type]** service from [!UICONTROL Configuration Manager].

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Um die Configuration Manager-Webkonsole zu öffnen, öffnen Sie `https://[aem_server]:[port]/system/console/configMgr`.

1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Select the **[!UICONTROL Detect MIME from content]** option to enable the parsing of uploaded assets to determine their MIME type while ignoring file extensions. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
