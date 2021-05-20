---
title: Erkennung Asset-Duplikaten aktivieren
description: Erfahren Sie, wie Sie die Erkennung doppelter Assets in Experience Manager aktivieren.
contentOwner: AG
role: Business Practitioner, Administrator
feature: Asset-Management, Asset-Berichte
exl-id: a403d60e-2193-4835-8f37-4a40f2d01819
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 21%

---

# Erkennung Asset-Duplikaten aktivieren {#enable-detection-of-duplicate-assets}

Wenn Sie versuchen, ein Asset hochzuladen, das in [!DNL Adobe Experience Manager Assets] vorhanden ist, wird es von der Funktion zur Duplikatserkennung als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die Konfigurationsseite [!DNL Experience Manager] der Web-Konsole, indem Sie auf `https://[aem_server]:[port]/system/console/configMgr` zugreifen.
1. Bearbeiten Sie die Konfiguration für das Servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Wählen Sie die Option **[!UICONTROL Duplikat erkennen]** und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

   *Abbildung: Wählen Sie die Option Duplikat erkennen im Servlet aus.*

Die Funktion zur Duplikatserkennung ist jetzt in [!DNL Assets] aktiviert. Wenn ein Benutzer versucht, ein in [!DNL Experience Manager] vorhandenes Asset hochzuladen, prüft das System den Konflikt und zeigt es an. Die Assets werden mit dem SHA-1-Hash identifiziert, der unter `jcr:content/metadata/dam:sha1` gespeichert ist. Das bedeutet, dass doppelte Assets unabhängig von den Dateinamen erkannt werden.

>[!MORELIKETHIS]
>
>* [Duplizieren von Assets in einem vorhandenen Repository (ein Tutorial von einem Community-Mitglied)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

