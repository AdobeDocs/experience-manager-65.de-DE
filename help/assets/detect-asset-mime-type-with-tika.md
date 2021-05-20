---
title: Erkennen des MIME-Typs von Assets mit Apache Tika
description: Aktivieren Sie Apache Tika, um [!DNL Experience Manager Assets] beim Hochladen zu helfen, den MIME-Typ von Assets aus dem Inhalts-Stream anstelle der Dateierweiterung zu erkennen.
contentOwner: AG
role: Administrator, Architect
feature: Metadaten,Entwicklertools,Asset-Management
exl-id: a312466d-8d84-4c94-af85-1549afc61aed
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 11%

---

# MIME-Typ von Assets mit [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika} erkennen

Normalerweise erkennt [!DNL Adobe Experience Manager Assets] den MIME-Typ von Assets, die Sie von ihrer Dateierweiterung hochladen.

Wenn Sie zum Hochladen von Assets [!DNL Apache Tika] verwenden, erkennt [!DNL Assets] deren MIME-Typ während des Upload-Vorgangs aus dem Inhalts-Stream anstelle der Dateierweiterung.

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie den Dienst **[!UICONTROL Day CQ DAM Mime Type]** unter [!UICONTROL Configuration Manager].

>[!NOTE]
>
>Die MIME-Typerkennung mit der Bibliothek [!DNL Apache Tika] ist ein ressourcenintensiver Vorgang.

1. Um die Web-Konsole &quot;Configuration Manager&quot;zu öffnen, greifen Sie auf `https://[aem_server]:[port]/system/console/configMgr` zu.

1. Suchen Sie in der Liste der Dienste **[!UICONTROL Day CQ DAM Mime Type Service]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Wählen Sie die Option **[!UICONTROL MIME aus Inhalt erkennen]** aus, um das Parsen hochgeladener Assets zu aktivieren, um ihren MIME-Typ zu bestimmen, während Dateierweiterungen ignoriert werden. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
