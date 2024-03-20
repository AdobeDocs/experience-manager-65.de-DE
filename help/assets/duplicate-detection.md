---
title: Erkennung von Asset-Duplikaten aktivieren
description: Erfahren Sie, wie Sie die Erkennung von Asset-Duplikaten in Experience Manager aktivieren.
contentOwner: AG
role: User, Admin
feature: Asset Management,Asset Reports
exl-id: a403d60e-2193-4835-8f37-4a40f2d01819
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 85%

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
>* [Erkennen doppelter Assets in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/detect-duplicate-assets.html)
