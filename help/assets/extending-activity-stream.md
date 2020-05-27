---
title: Assets mit Aktivitäten-Stream integrieren
description: Beschreibt die Aufzeichnungsfunktionen von Experience Manager und die Konfiguration, um bestimmte Ereignis aufzuzeichnen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 51%

---


# Integrate Assets with activity stream {#integrating-assets-with-activity-stream}

Adobe Experience Manager Assets-Benutzer führen zahlreiche Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Benutzeraktivitätenverlauf erstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von Experience Manager und die Konfiguration von Experience Manager zur Aufzeichnung bestimmter Ereignis beschrieben.

## Performance considerations and default behavior {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen ist die Asset-Integration mit dem Aktivität Stream standardmäßig deaktiviert.

## Supported action events {#supported-action-events}

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

## Assets-Ereignis konfigurieren - Aufzeichnung {#configuring-aem-assets-events-recording}

The [Web console](/help/sites-deploying/configuring-osgi.md) provides access to the Assets Event Recorder tuning. Gehen Sie wie folgt vor, um den Asset-Ereignis-Recorder zu konfigurieren:

1. Navigate to the **[!UICONTROL Web Console]**

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM-Ereignisaufzeichnung]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Wählen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzer-Aktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Aufgenommene Ereignisse lesen {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. You can read them programmatically using the [ActivityManager API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
