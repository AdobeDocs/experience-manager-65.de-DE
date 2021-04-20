---
title: Erkennung Asset-Duplikaten aktivieren
description: Erfahren Sie, wie Sie die Erkennung von Duplikat-Assets in Experience Manager aktivieren.
contentOwner: AG
role: Business Practitioner, Administrator
feature: Asset Management,Asset Reports
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 23%

---


# Erkennung Asset-Duplikaten aktivieren {#enable-detection-of-duplicate-assets}

Wenn Sie versuchen, ein Asset hochzuladen, das in [!DNL Adobe Experience Manager Assets] vorhanden ist, wird es von der Duplikat-Erkennungsfunktion als Duplikat identifiziert. Die Duplikatserkennung ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Funktion zu aktivieren:

1. Öffnen Sie die Konfigurationsseite [!DNL Experience Manager] der Webkonsole, indem Sie auf `https://[aem_server]:[port]/system/console/configMgr` zugreifen.
1. Bearbeiten Sie die Konfiguration für das Servlet **[!UICONTROL Day CQ DAM Asset]** erstellen.
1. Wählen Sie die Option **[!UICONTROL Duplikat erkennen]** und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Auswahl der Option „Duplikat erkennen“ im Servlet](assets/chlimage_1-377.png)

   *Abbildung: Wählen Sie im Servlet die Option &quot;Duplikat erkennen&quot;.*

Die Funktion zum Erkennen von Duplikaten ist jetzt in [!DNL Assets] aktiviert. Wenn ein Benutzer versucht, ein Asset hochzuladen, das in [!DNL Experience Manager] vorhanden ist, sucht das System nach Konflikten und zeigt dies an. Die Assets werden mit dem SHA-1-Hash identifiziert, der bei `jcr:content/metadata/dam:sha1` gespeichert ist. Das bedeutet, dass Duplikat-Assets unabhängig von den Dateinamen erkannt werden.

>[!MORELIKETHIS]
>
>* [Duplikat-Assets im vorhandenen Repository (ein Tutorial von einem Community-Mitglied)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

