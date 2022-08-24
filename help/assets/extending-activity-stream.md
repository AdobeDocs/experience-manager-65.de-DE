---
title: Integrieren [!DNL Assets] mit Aktivitäts-Stream
description: Beschreibt die Aufzeichnungsfunktionen von [!DNL Experience Manager] und wie Sie es so konfigurieren, dass bestimmte Ereignisse aufgezeichnet werden.
contentOwner: AG
role: Developer
feature: Asset Management
exl-id: 2a08a7c1-8be9-42d1-9983-f9c8b12ea4e8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 53%

---

# Integrieren [!DNL Assets] mit Aktivitäts-Stream {#integrating-assets-with-activity-stream}

[!DNL Adobe Experience Manager Assets] -Benutzer führen viele Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Benutzeraktivitätenverlauf erstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von [!DNL Experience Manager] und wie Sie [!DNL Experience Manager] , um bestimmte Ereignisse aufzuzeichnen.

## Leistungsaspekte und Standardverhalten {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen [!DNL Assets] Die Integration mit dem Aktivitäts-Stream ist standardmäßig deaktiviert.

## Unterstützte Aktionsereignisse {#supported-action-events}

Die folgenden Ereignisse können zur Aufzeichnung konfiguriert werden:

* Lizenz akzeptiert (ACCEPTED)
* Asset erstellt (ASSET_CREATED)
* Asset verschoben (ASSET_MOVED)
* Asset entfernt (ASSET_REMOVED)
* Lizenz abgelehnt (REJECTED)
* Asset heruntergeladen (DOWNLOADED)
* Asset versioniert (VERSIONED)
* Asset-Version wiederhergestellt (RESTORED)
* Asset-Metadaten aktualisiert (METADATA_UPDATED)
* Asset veröffentlicht auf externem System (PUBLISHED_EXTERNAL)
* Original des Assets aktualisiert (ORIGINAL_UPDATED)
* Asset-Ausgabeformat aktualisiert (RENDITION_UPDATED)
* Asset-Ausgabeformat entfernt (RENDITION_REMOVED)
* Unter-Asset aktualisiert (SUBASSET_UPDATED)
* Unter-Asset entfernt (SUBASSET_REMOVED)

## Konfigurieren [!DNL Assets] Ereignisaufzeichnung {#configuring-aem-assets-events-recording}

Die [Webkonsole](/help/sites-deploying/configuring-osgi.md) bietet Zugriff auf die Optimierung der Asset-Ereignisaufzeichnung. Gehen Sie wie folgt vor, um die Ereignisaufzeichnung &quot;Assets&quot;zu konfigurieren:

1. Navigieren Sie zum **[!UICONTROL Web-Konsole]**

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM-Ereignisaufzeichnung]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Wählen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzer-Aktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Gelesene Ereignisse lesen {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. Sie können sie programmgesteuert mit der [ActivityManager-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
