---
title: MIME-Typ von Assets erkennen mit Apache Tika
description: Aktivieren Sie Apache Tika, damit  [!DNL Experience Manager Assets]  beim Upload-Vorgang den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung erkennen kann.
contentOwner: AG
role: Admin, Architect
feature: Metadata,Developer Tools,Asset Management
exl-id: a312466d-8d84-4c94-af85-1549afc61aed
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 100%

---

# MIME-Typ von Assets erkennen mit [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika}

Normalerweise erkennt [!DNL Adobe Experience Manager Assets] den MIME-Typ der von Ihnen hochgeladenen Assets anhand der Dateierweiterung.

Wenn Sie [!DNL Apache Tika]verwenden, um Assets hochzuladen, erkennt [!DNL Assets] deren MIME-Typ anhand des Inhalts-Streams während des Upload-Vorgangs statt anhand der Dateierweiterung. 

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie in [!UICONTROL Configuration Manager] den Dienst **[!UICONTROL Day CQ DAM Mime Type]**.

>[!NOTE]
>
>Die Erkennung des MIME-Typs mithilfe der [!DNL Apache Tika]-Bibliothek ist ein ressourcenintensiver Vorgang. 

1. Um die Web-Konsole „Configuration Manager“ zu öffnen, verwenden Sie `https://[aem_server]:[port]/system/console/configMgr`.

1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]**, und klicken Sie auf **[!UICONTROL Edit]**.

1. Aktivieren Sie die Option **[!UICONTROL Detect MIME from content]**, um das Analysieren hochgeladener Assets zu aktivieren und so den zugehörigen MIME-Typ ohne Beachtung der Dateierweiterungen zu bestimmen. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
