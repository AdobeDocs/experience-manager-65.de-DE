---
title: Konfigurieren von Asset-Upload-Beschränkungen
description: 'Beschränken Sie den Typ der Assets (Dateien), die Benutzer hochladen können. '
contentOwner: AG
role: Developer, Admin, Architect
feature: Asset-Verwaltung,Hochladen
exl-id: 0e009b9a-54c4-4715-98ee-0207839f90f6
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 54%

---

# Konfigurieren von Asset-Upload-Beschränkungen {#configuring-asset-upload-restrictions}

Sie können [!DNL Adobe Experience Manager Assets] konfigurieren, um den Typ der Assets zu beschränken, die Benutzer hochladen können. Dadurch wird verhindert, dass versehentlich unerwünschte und böswillige Dateien hochgeladen werden. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien, die Benutzer hochladen können, zu steuern. Standardmäßig ermöglicht [!DNL Assets] Benutzern das Hochladen von Assets aller MIME-Typen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Öffnen Sie die Web-Konsole „Configuration Manager“. Greife Sie auf `https://[aem_server]:[port]/system/console/configMgr` zu.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um Benutzer auf das Hochladen von Dateien bestimmter MIME-Typen zu beschränken, deaktivieren Sie die Option **[!UICONTROL Alle MIME-Typen zulassen]** und geben Sie die zulässigen MIME-Typen in den Feldern **[!UICONTROL Zulässige Asset-MIMEs (regex)]** mithilfe regulärer Ausdrücke an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
