---
title: MIME-Typ von Assets erkennen mit Apache Tika
description: Aktivieren Sie Apache Tika, damit [!DNL Experience Manager Assets] beim Upload-Vorgang den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung erkennen können.
contentOwner: AG
role: Admin, Developer
feature: Metadata,Developer Tools,Asset Management
exl-id: a312466d-8d84-4c94-af85-1549afc61aed
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: f2d27a5f-0d67-4d85-8a24-86a8d8a3574b
    internal-label: Developer tools
  - id: 7d2b2ec8-499c-5434-9ffd-9218cd71f683
    internal-label: Asset Management
  - id: ac365bec-0634-4744-9473-c42f47320593
    internal-label: Asset management and governance
subfeature_v2:
  - id: ed6971a3-2c12-4fd2-81f4-ff329c416250
    internal-label: Metadata
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 85%
---
# MIME-Typ von Assets erkennen mit [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika}

Normalerweise erkennt [!DNL Adobe Experience Manager Assets] den MIME-Typ der von Ihnen hochgeladenen Assets anhand der Dateierweiterung.

Wenn Sie [!DNL Apache Tika]verwenden, um Assets hochzuladen, erkennt [!DNL Assets] deren MIME-Typ anhand des Inhalts-Streams während des Upload-Vorgangs statt anhand der Dateierweiterung.

Diese Funktion ist standardmäßig deaktiviert. Um die Funktion zu aktivieren, konfigurieren Sie in [!UICONTROL Configuration Manager] den Dienst **[!UICONTROL Day CQ DAM Mime Type]**.

>[!NOTE]
>
>Die Erkennung des MIME-Typs mithilfe der [!DNL Apache Tika]-Bibliothek ist ein ressourcenintensiver Vorgang.

1. Um die Web-Konsole „Configuration Manager“ zu öffnen, verwenden Sie `https://[aem_server]:[port]/system/console/configMgr`.

1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]**, und klicken Sie auf **[!UICONTROL Edit]**.

1. Aktivieren Sie die Option **[!UICONTROL Detect MIME from content]**, um das Analysieren hochgeladener Assets zu aktivieren und so den zugehörigen MIME-Typ ohne Beachtung der Dateierweiterungen zu bestimmen. Standardmäßig ist diese Option deaktiviert.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
