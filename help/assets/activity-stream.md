---
title: Aktivitäts-Stream digitaler Assets in der Timeline-Ansicht
description: Dieser Artikel beschreibt, wie Sie Aktivitätsprotokolle für Assets in der Timeline anzeigen können.
contentOwner: AG
feature: Asset Management
role: User, Admin
exl-id: 28dc0aa5-f2be-4e27-b7d8-415569b7ecd4
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: 7d2b2ec8-499c-5434-9ffd-9218cd71f683
    internal-label: Asset Management
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%
---
# Aktivitäts-Stream in der Timeline {#activity-stream-in-timeline}

Diese Funktion zeigt Aktivitätsprotokolle für Assets in der Timeline an. Wenn Sie einen der folgenden Asset-bezogenen Vorgänge in [!DNL Adobe Experience Manager Assets]durchführen, aktualisiert die Aktivitäts-Stream-Funktion die Timeline, um die Aktivität anzuzeigen.

Folgende Vorgänge werden im Aktivitäts-Stream protokolliert:

* Erstellen
* Löschen
* Download (einschließlich Ausgabedarstellungen)
* Veröffentlichen
* Veröffentlichung aufheben
* Genehmigen
* Ablehnen
* Verschieben

Die in der Timeline angezeigten Aktivitätsprotokolle werden aus dem Ordner `/var/audit/com.day.cq.dam/content/dam` in CRX abgerufen, in dem Protokolldateien gespeichert werden. Außerdem wird die Timeline-Aktivität protokolliert, wenn neue Assets hochgeladen oder vorhandene Assets geändert und in [!DNL Experience Manager] über [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) oder das [Experience Manager Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=de) gespeichert werden.

>[!NOTE]
>
>ÜbergangsWorkflows werden nicht in der Timeline angezeigt, da keine Verlaufsinformationen für diese Workflows gespeichert werden.

Um den Aktivitäts-Stream anzuzeigen, führen Sie einen oder mehrere Vorgänge für die Assets aus, wählen Sie das Asset aus und wählen Sie dann **[!UICONTROL Timeline]** aus der GlobalNav-Liste aus.

![timeline-2](assets/timeline-2.png)

In der Timeline wird der Aktivitäts-Stream für die mit den Assets ausgeführten Vorgänge angezeigt.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>Der standardmäßige Speicherort für Aufgaben des Typs **[!UICONTROL Veröffentlichen]** und **[!UICONTROL Veröffentlichung aufheben]** befindet sich in `/var/audit/com.day.cq.replication/content`. Für Aufgaben des Typs **[!UICONTROL Verschieben]** ist der standardmäßige Speicherort `/var/audit/com.day.cq.wcm.core.page`.
