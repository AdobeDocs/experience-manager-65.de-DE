---
title: Assets mit Aktivitätsstream integrieren
description: Beschreibt die Aufzeichnungsfunktionen von AEM und wie Sie AEM zum Aufzeichnen bestimmter Ereignisse konfigurieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Integrate Assets with activity stream {#integrating-assets-with-activity-stream}

Benutzer von Adobe Experience Manager (AEM) Assets führen zahlreiche Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Benutzeraktivitätenverlauf erstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von AEM beschrieben und gezeigt, und wie Sie AEM zum Aufzeichnen bestimmter Ereignisse konfigurieren.

## Performance considerations and default behavior {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen ist die AEM Assets-Integration mit dem Activity Stream standardmäßig deaktiviert.

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

## Configure AEM Assets events recording {#configuring-aem-assets-events-recording}

The [Web console](/help/sites-deploying/configuring-osgi.md) provides access to the AEM Assets Event Recorder tuning. Gehen Sie wie folgt vor, um den Ereignisaufzeichnungsbefehl für AEM Assets zu konfigurieren:

1. Navigate to the **[!UICONTROL Web Console]**

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM-Ereignisaufzeichnung]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Wählen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzer-Aktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Aufgenommene Ereignisse lesen {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. You can read them programmatically using the [ActivityManager API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
