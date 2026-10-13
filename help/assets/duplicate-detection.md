---
title: Erkennung von Asset-Duplikaten aktivieren
description: Erfahren Sie, wie Sie die Erkennung von Asset-Duplikaten in Experience Manager aktivieren.
contentOwner: AG
role: User, Admin
feature: Asset Management,Asset Reports
exl-id: a403d60e-2193-4835-8f37-4a40f2d01819
hide: true
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: 7d2b2ec8-499c-5434-9ffd-9218cd71f683
    internal-label: Asset Management
  - id: ac365bec-0634-4744-9473-c42f47320593
    internal-label: Asset management and governance
subfeature_v2:
  - id: c29e3a96-cd2b-4e21-b382-a8279aa04553
    internal-label: Asset reports
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 100%
---
# Erkennung von Asset-Duplikaten aktivieren {#enable-detection-of-duplicate-assets}

Beim Versuch, ein Asset hochzuladen, das in [!DNL Adobe Experience Manager Assets] vorhanden ist, wird es von der Funktion zur Duplikatserkennung als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die Seite [!DNL Experience Manager]-Web-Konsolen-Konfiguration über `https://[aem_server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration für das Servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Aktivieren Sie die Option **[!UICONTROL Duplikat erkennen]**, und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

   *Abbildung: Auswahl der Option „Duplikat erkennen“ im Servlet.*

Die Funktion zur Duplikatserkennung ist nun in [!DNL Assets] aktiviert. Wenn ein Benutzer versucht, ein Asset hochzuladen, das in [!DNL Experience Manager] vorhanden ist, prüft das System auf Konflikte und zeigt diese an. Die Elemente werden mit dem unter `jcr:content/metadata/dam:sha1` gespeicherten SHA-1-Hash identifiziert, d. h. doppelte Assets werden unabhängig von den Dateinamen erkannt.

>[!MORELIKETHIS]
>
>* [Duplizieren von Assets im vorhandenen Repository (Tutorial eines Community-Mitglieds)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)
>* [Erkennen von doppelten Assets in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/detect-duplicate-assets.html?lang=de)
