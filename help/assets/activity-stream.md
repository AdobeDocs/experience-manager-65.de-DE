---
title: Aktivitäts-Stream in der Timeline
description: Dieser Artikel beschreibt, wie Sie Aktivitätsprotokolle für Assets in der Timeline anzeigen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 73%

---


# Aktivitäts-Stream in der Timeline {#activity-stream-in-timeline}

Diese Funktion zeigt Aktivitätsprotokolle für Assets in der Timeline an. Wenn Sie einen der folgenden Asset-bezogenen Vorgänge in Adobe Experience Manager Assets ausführen, wird die Zeitschiene mit der Stream-Funktion der Aktivität aktualisiert, um die Aktivität widerzuspiegeln.

Folgende Vorgänge werden im Aktivitäts-Stream protokolliert:

* Erstellen
* Löschen
* Download (einschließlich Wiedergaben)
* Veröffentlichen
* Veröffentlichung rückgängig machen
* Genehmigen
* Ablehnen
* Verschieben

Die in der Timeline angezeigten Aktivitätsprotokolle werden aus dem Ordner `/var/audit/com.day.cq.dam/content/dam` in CRX abgerufen, in dem Protokolldateien gespeichert werden. In addition, timeline activity is logged when new assets are uploaded or existing asses are modified and checked into Experience Manager via [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) or [Experience Manager desktop app](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html).

>[!NOTE]
>
>Übergangsarbeitsabläufe werden nicht in der Timeline angezeigt, da keine Verlaufsinformationen für diese Arbeitsabläufe gespeichert werden.

Um den Aktivitätsstream anzuzeigen, führen Sie einen oder mehrere Vorgänge für die Assets aus, wählen Sie das Asset aus und wählen Sie dann **[!UICONTROL Timeline]** aus der GlobalNav-Liste aus.

![timeline-2](assets/timeline-2.png)

In der Timeline wird der Aktivitäts-Stream für die mit den Assets ausgeführten Vorgänge angezeigt.

![Aktivität_stream](assets/activity_stream.png)

>[!NOTE]
>
>Der standardmäßige Speicherort für Aufgaben des Typs **[!UICONTROL Veröffentlichen]** und **[!UICONTROL Veröffentlichung rückgängig machen]** befindet sich in `/var/audit/com.day.cq.replication/content`. Für Aufgaben des Typs **[!UICONTROL Verschieben]** ist der standardmäßige Speicherort `/var/audit/com.day.cq.wcm.core.page`.
