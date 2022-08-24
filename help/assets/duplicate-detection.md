---
title: Erkennung Asset-Duplikaten aktivieren
description: Erfahren Sie, wie Sie die Erkennung doppelter Assets in Experience Manager aktivieren.
contentOwner: AG
role: User, Admin
feature: Asset Management,Asset Reports
exl-id: a403d60e-2193-4835-8f37-4a40f2d01819
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 22%

---

# Erkennung Asset-Duplikaten aktivieren {#enable-detection-of-duplicate-assets}

Wenn Sie versuchen, ein Asset hochzuladen, das in [!DNL Adobe Experience Manager Assets], identifiziert die Funktion zur Duplikatserkennung sie als Duplikat. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die [!DNL Experience Manager] Web-Konsolenkonfigurationsseite durch Zugriff auf `https://[aem_server]:[port]/system/console/configMgr`.
1. Bearbeiten der Konfiguration für das Servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Wählen Sie die **[!UICONTROL Duplikat erkennen]** und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

   *Abbildung: Wählen Sie die Option Duplikat erkennen im Servlet aus.*

Die Funktion zur Duplikatserkennung ist jetzt in aktiviert. [!DNL Assets]. Wenn ein Benutzer versucht, ein Asset hochzuladen, das in [!DNL Experience Manager], prüft das System auf Konflikte und zeigt sie an. Die Assets werden mit dem SHA-1-Hash identifiziert, der unter `jcr:content/metadata/dam:sha1`, d. h. doppelte Assets werden unabhängig von den Dateinamen erkannt.

>[!MORELIKETHIS]
>
>* [Duplizieren von Assets in einem vorhandenen Repository (ein Tutorial von einem Community-Mitglied)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

