---
title: Integrieren [!DNL Assets] in Aktivität-Stream
description: Beschreibt die Aufzeichnungsfunktionen von [!DNL Experience Manager] und wie sie zum Aufzeichnen bestimmter Ereignis konfiguriert werden.
contentOwner: AG
role: Developer
feature: Asset Management
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 53%

---


# [!DNL Assets] mit Aktivität-Stream {#integrating-assets-with-activity-stream} integrieren

[!DNL Adobe Experience Manager Assets] Benutzer führen zahlreiche Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Benutzeraktivitätenverlauf erstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von [!DNL Experience Manager] und die Konfiguration von [!DNL Experience Manager] zum Aufzeichnen bestimmter Ereignis beschrieben.

## Leistungsaspekte und Standardverhalten {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen ist die [!DNL Assets]-Integration mit dem Aktivitäten-Stream standardmäßig deaktiviert.

## Ereignisse für unterstützte Aktionen {#supported-action-events}

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

## [!DNL Assets]-Ereignis für die Aufzeichnung von {#configuring-aem-assets-events-recording} konfigurieren

Die [Webkonsole](/help/sites-deploying/configuring-osgi.md) ermöglicht den Zugriff auf die Assets Ereignis Recorder-Abstimmung. Gehen Sie wie folgt vor, um den Asset-Ereignis-Recorder zu konfigurieren:

1. Navigieren Sie zur **[!UICONTROL Webkonsole]**

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM-Ereignisaufzeichnung]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Wählen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzer-Aktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Gelesene aufgezeichnete Ereignis {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. Sie können sie programmgesteuert mit der [ActivityManager-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html) lesen.
