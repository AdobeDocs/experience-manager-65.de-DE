---
title: Einschränkungen beim Hochladen von Assets konfigurieren
description: 'Beschränken der Art von Assets (Dateien), die Benutzer hochladen können '
contentOwner: AG
role: Entwickler, Administrator, Architekt
feature: Asset-Verwaltung, Hochladen
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 53%

---


# Beschränkungen für das Hochladen von Assets konfigurieren {#configuring-asset-upload-restrictions}

Sie können [!DNL Adobe Experience Manager Assets] konfigurieren, um den Typ der Assets einzuschränken, die Benutzer hochladen können. Dadurch wird verhindert, dass versehentliche Uploads unerwünschter Formate und böswilliger Dateien erfolgen. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien, die Benutzer hochladen können, zu steuern. Standardmäßig ermöglicht [!DNL Assets] Benutzern das Hochladen von Assets aller MIME-Typen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Öffnen Sie die Web-Konsole „Configuration Manager“. Greife Sie auf `https://[aem_server]:[port]/system/console/configMgr` zu.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um das Hochladen von Dateien bestimmter MIME-Typen zu beschränken, deaktivieren Sie die Option **[!UICONTROL Alle MIME]** zulassen und geben Sie in den Feldern **[!UICONTROL Zulässige Asset-MIMEs (regex)]** zulässige MIME-Typen unter Verwendung regulärer Ausdruck an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
