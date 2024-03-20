---
title: Konfigurieren von Asset-Upload-Beschränkungen
description: Beschränken Sie den Typ der Assets (Dateien), die Benutzer hochladen können.
contentOwner: AG
role: Developer, Admin, Architect
feature: Asset Management,Upload
exl-id: 0e009b9a-54c4-4715-98ee-0207839f90f6
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---

# Konfigurieren von Asset-Upload-Beschränkungen {#configuring-asset-upload-restrictions}

Sie können [!DNL Adobe Experience Manager Assets] so konfigurieren, dass Benutzer nur bestimmte Asset-Typen hochladen können. Dadurch wird verhindert, dass versehentlich Dateien in unerwünschten Formaten oder böswillige Dateien hochgeladen werden. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien zu steuern, die Benutzer hochladen können. Standardmäßig lässt [!DNL Assets] es zu, dass Benutzer Assets aller MIME-Typen hochladen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Öffnen Sie die Web-Konsole „Configuration Manager“. Greife Sie auf `https://[aem_server]:[port]/system/console/configMgr` zu.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um den Upload von Dateien bestimmter MIME-Typen zu beschränken, deaktivieren Sie die Option **[!UICONTROL Alle MIME-Typen zulassen]** und geben Sie die zulässigen MIME-Typen mithilfe regulärer Ausdrücke im Feld **[!UICONTROL Zulässige Asset-MIME-Typen (regex)]** an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
