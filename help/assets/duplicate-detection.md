---
title: Erkennung Asset-Duplikaten aktivieren
description: Erfahren Sie, wie Sie die Erkennung von Asset-Duplikaten in AEM aktivieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Erkennung Asset-Duplikaten aktivieren {#enable-detection-of-duplicate-assets}

Wenn Sie versuchen, ein Asset hochzuladen, das in Adobe Experience Manager (AEM) Assets vorhanden ist, wird das Asset von der Funktion zur Duplikatserkennung als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die Seite &quot;AEM Web Console-Konfiguration&quot;, indem Sie auf `https://[aem_server]:[port]/system/console/configMgr`.
1. Edit the configuration for the servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Select the **[!UICONTROL detect duplicate]** option, and click **[!UICONTROL Save]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

   *Abbildung: Option &quot;Duplikat erkennen&quot;im Servlet auswählen*

Die Funktion zur Duplikatserkennung ist nun in AEM Assets aktiviert. Wenn ein Benutzer versucht, ein Asset hochzuladen, das in AEM vorhanden ist, prüft das System auf Konflikte und zeigt diese an. The assets are identified using SHA-1 hash stored at `jcr:content/metadata/dam:sha1`, which means duplicate assets are detected irrespective of the filenames.

>[!MORELIKETHIS]
>
>* [Duplikat-Assets im vorhandenen Repository (ein Tutorial von einem Community-Mitglied)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

