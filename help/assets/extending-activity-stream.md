---
title: Integrieren von  [!DNL Assets]  in den Aktivitäts-Stream
description: Beschreibt die Aufzeichnungsfunktionen von  [!DNL Experience Manager]  und die Konfiguration zum Aufzeichnen bestimmter Ereignisse.
contentOwner: AG
role: Developer
feature: Asset Management
exl-id: 2a08a7c1-8be9-42d1-9983-f9c8b12ea4e8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%

---

# Integrieren von [!DNL Assets] in den Aktivitäts-Stream {#integrating-assets-with-activity-stream}

[!DNL Adobe Experience Manager Assets] -Benutzer führen viele Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Benutzeraktivitätenverlauf erstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von [!DNL Experience Manager] und die Konfigration von [!DNL Experience Manager] zum Aufzeichnen bestimmter Ereignisse beschrieben.

## Überlegungen zur Leistung und Standardverhalten {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Speicherplatz-intensiv sein, beispielsweise beim Massenimport. Aus diesen Gründen ist die [!DNL Assets]-Integration in den Aktivitäts-Stream standardmäßig deaktiviert.

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

## Konfigurieren der [!DNL Assets]-Ereignisaufzeichnung {#configuring-aem-assets-events-recording}

Die Einstellungen für die Assets-Ereignisaufzeichnung können über die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) vorgenommen werden. Zum Konfigurieren der Assets-Ereignisaufzeichnung gehen Sie wie folgt vor:

1. Navigieren Sie zur **[!UICONTROL Web-Konsole]**.

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken Sie auf **[!UICONTROL Day CQ DAM-Ereignisaufzeichnung]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Wählen Sie, welche **[!UICONTROL Ereignistypen]** im Benutzer-Aktivitäts-Stream aufgezeichnet werden sollen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Lesen aufgezeichneter Ereignisse {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. Sie können sie programmgesteuert über die [ActivityManager-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html) lesen.
