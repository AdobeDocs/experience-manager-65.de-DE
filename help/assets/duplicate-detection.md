---
title: Erkennung Asset-Duplikaten aktivieren
description: Erfahren Sie, wie Sie die Erkennung von Duplikat-Assets in Experience Manager aktivieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 22%

---


# Erkennung Asset-Duplikaten aktivieren {#enable-detection-of-duplicate-assets}

If you attempt to upload an asset that exists in [!DNL Adobe Experience Manager Assets], the duplicate detection feature identifies it as duplicate. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die Konfigurationsseite der [!DNL Experience Manager] Web-Konsole durch Zugriff `https://[aem_server]:[port]/system/console/configMgr`.
1. Edit the configuration for the servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Select the **[!UICONTROL detect duplicate]** option, and click **[!UICONTROL Save]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

   *Abbildung: Wählen Sie im Servlet die Option &quot;Duplikat erkennen&quot;.*

The detect duplicate feature is now enabled in [!DNL Assets]. When a user attempts to upload an asset that exists in [!DNL Experience Manager], the system checks for conflict and indicates it. The assets are identified using SHA-1 hash stored at `jcr:content/metadata/dam:sha1`, which means duplicate assets are detected irrespective of the filenames.

>[!MORELIKETHIS]
>
>* [Duplikat-Assets im vorhandenen Repository (ein Tutorial von einem Community-Mitglied)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

