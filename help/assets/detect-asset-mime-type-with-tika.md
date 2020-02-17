---
title: MIME-Typ von Assets mithilfe von Apache Tika erkennen
description: Aktivieren Sie Apache Tika, damit AEM Assets beim Upload-Vorgang den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung erkennen kann.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Detect MIME type of assets using Apache Tika {#detecting-mime-type-of-assets-using-apache-tika}

Normalerweise erkennt Adobe Experience Manager (AEM) Assets den MIME-Typ der von Ihnen hochgeladenen Assets anhand der Dateierweiterung.  

Wenn Sie Apache Tika verwenden, um Assets hochzuladen, erkennt AEM Assets deren MIME-Typ durch den Content Stream während des Uploadvorgangs statt durch die Dateierweiterung. 

Diese Funktion ist standardmäßig deaktiviert.  To enable the feature, configure the **[!UICONTROL Day CQ DAM Mime Type]** service from [!UICONTROL Configuration Manager].

>[!NOTE]
>
>Die MIME-Typerkennung mit der Apache Tika-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Um die Configuration Manager-Webkonsole zu öffnen, öffnen Sie `https://[aem_server]:[port]/system/console/configMgr`.
1. From the list of services, locate **[!UICONTROL Day CQ DAM Mime Type Service]** and tap **[!UICONTROL Edit]** beside it to open it in Edit mode.

1. Select the **[!UICONTROL Detect MIME from content]** option to enable the parsing of uploaded assets to determine their MIME type while ignoring file extensions. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Click/tap **[!UICONTROL Save]** to save the changes.
