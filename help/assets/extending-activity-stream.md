---
title: Integrieren von  [!DNL Assets]  in den Aktivitäts-Stream
description: Beschreibt die Aufzeichnungsfunktionen von  [!DNL Experience Manager]  und die Konfiguration zum Aufzeichnen bestimmter Ereignisse.
contentOwner: AG
role: Developer
feature: Asset Management
exl-id: 2a08a7c1-8be9-42d1-9983-f9c8b12ea4e8
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 32%

---

# Integrieren von [!DNL Assets] in den Aktivitäts-Stream {#integrating-assets-with-activity-stream}

[!DNL Adobe Experience Manager Assets] -Benutzer führen viele Aktionen durch, z. B. das Erstellen, Hochladen und Löschen von Assets. Diese Aktionen können aufgezeichnet werden, sodass Sie einen Verlauf der Aktionen eines Benutzers bereitstellen können. In diesem Abschnitt werden die Aufzeichnungsfunktionen von [!DNL Experience Manager] und wie Sie [!DNL Experience Manager] , um bestimmte Ereignisse aufzuzeichnen.

## Überlegungen zur Leistung und Standardverhalten {#performance-considerations-and-default-behavior}

Diese Integration kann CPU- und Festplattenspeicher umfassen, die beispielsweise beim Massenimport benötigt werden. Aus diesen Gründen wird die Variable [!DNL Assets] Die Integration mit dem Aktivitäts-Stream ist standardmäßig deaktiviert.

## Unterstützte Aktionsereignisse {#supported-action-events}

Sie können die folgenden Ereignisse für die Aufzeichnung konfigurieren:

* Lizenz akzeptiert (AKZEPTIERT)
* Asset erstellt (ASSET_CREATED)
* Asset verschoben (ASSET_MOVED)
* Asset entfernt (ASSET_REMOVED)
* Lizenz abgelehnt (ABGELEHNT)
* Asset heruntergeladen (HERUNTERGELADEN)
* Asset versioniert (VERSIONED)
* Asset-Version wiederhergestellt (RESTORED)
* Asset-Metadaten aktualisiert (METADATA_UPDATED)
* Asset in externem System veröffentlicht (PUBLISHED_EXTERNAL)
* Original des Assets aktualisiert (ORIGINAL_UPDATED)
* Asset-Ausgabedarstellung aktualisiert (RENDITION_UPDATED)
* Asset-Ausgabedarstellung entfernt (RENDITION_REMOVED)
* Teilasset aktualisiert (SUBASSET_UPDATED)
* Teilasset entfernt (SUBASSET_REMOVED)

## Konfigurieren der [!DNL Assets]-Ereignisaufzeichnung {#configuring-aem-assets-events-recording}

Die Einstellungen für die Assets-Ereignisaufzeichnung können über die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) vorgenommen werden. Zum Konfigurieren der Assets-Ereignisaufzeichnung gehen Sie wie folgt vor:

1. Navigieren Sie zur **[!UICONTROL Web-Konsole]**.

1. Klicken Sie auf **[!UICONTROL Konfiguration]**.

1. Doppelklicken **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Aktivieren Sie die Option **[!UICONTROL Diesen Service aktivieren]**.

1. Überprüfen Sie, welche **[!UICONTROL Ereignistypen]** , die Sie im Benutzeraktivitäts-Stream aufzeichnen möchten.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Lesen aufgezeichneter Ereignisse {#reading-recorded-events}

Die aufgezeichneten Ereignisse werden als Aktivitäten gespeichert. Sie können sie programmgesteuert über die [ActivityManager-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/activitystreams/ActivityManager.html) lesen.
