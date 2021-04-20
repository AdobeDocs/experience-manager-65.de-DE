---
title: MIME-Typ von Assets mithilfe von Apache Tika erkennen
description: 'Aktivieren Sie die Apache-Tika, um beim Upload-Vorgang anstelle der Dateierweiterung den MIME-Typ von Assets vom Inhaltsstream zu erkennen. [!DNL Experience Manager Assets] '
contentOwner: AG
role: Administrator, Architect
feature: Metadata,Developer Tools,Asset Management
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 11%

---


# MIME-Typ von Assets mit [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika} erkennen

Normalerweise erkennt [!DNL Adobe Experience Manager Assets] den MIME-Typ von Assets, die Sie von ihrer Dateierweiterung hochladen.

Wenn Sie zum Hochladen von Assets [!DNL Apache Tika] verwenden, erkennt [!DNL Assets] deren MIME-Typ während des Upload-Vorgangs vom Inhaltsstream und nicht von der Dateierweiterung.

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie den Dienst **[!UICONTROL Day CQ DAM Mime Type]** von [!UICONTROL Configuration Manager].

>[!NOTE]
>
>Die MIME-Typerkennung mit der Bibliothek [!DNL Apache Tika] ist ein ressourcenintensiver Vorgang.

1. Um die Configuration Manager-Webkonsole zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.

1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Wählen Sie die Option **[!UICONTROL MIME aus Inhalt erkennen]**, um die Analyse hochgeladener Assets zu aktivieren, um deren MIME-Typ zu bestimmen, während Sie Dateierweiterungen ignorieren. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
