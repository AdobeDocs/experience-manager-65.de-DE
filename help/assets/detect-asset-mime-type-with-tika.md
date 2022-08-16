---
title: Erkennen des MIME-Typs von Assets mit Apache Tika
description: Aktivieren Sie Apache Tika, um zu helfen [!DNL Experience Manager Assets] den MIME-Typ von Assets aus dem Inhalts-Stream während des Upload-Vorgangs anstelle der Dateierweiterung erkennen.
contentOwner: AG
role: Admin, Architect
feature: Metadata,Developer Tools,Asset Management
exl-id: a312466d-8d84-4c94-af85-1549afc61aed
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 11%

---

# Erkennen des MIME-Typs von Assets mit [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika}

Normalerweise [!DNL Adobe Experience Manager Assets] erkennt den MIME-Typ der Assets, die Sie von ihrer Dateierweiterung hochladen.

Wenn Sie [!DNL Apache Tika] Assets hochladen, [!DNL Assets] erkennt ihren MIME-Typ während des Upload-Vorgangs aus dem Inhalts-Stream anstelle der Dateierweiterung.

Diese Funktion ist standardmäßig deaktiviert.  Um die Funktion zu aktivieren, konfigurieren Sie die **[!UICONTROL Day CQ DAM Mime Type]** Dienst von [!UICONTROL Configuration Manager].

>[!NOTE]
>
>MIME-Typerkennung mit [!DNL Apache Tika] -Bibliothek ist ein ressourcenintensiver Vorgang.

1. Um die Web-Konsole &quot;Configuration Manager&quot;zu öffnen, greifen Sie auf `https://[aem_server]:[port]/system/console/configMgr`.

1. Suchen Sie in der Liste der Dienste nach **[!UICONTROL Day CQ DAM Mime Type Service]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Wählen Sie die **[!UICONTROL MIME aus Inhalt erkennen]** -Option zum Parsen hochgeladener Assets aktivieren, um ihren MIME-Typ zu bestimmen, während Dateierweiterungen ignoriert werden. Standardmäßig ist diese Option deaktiviert. 

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.
