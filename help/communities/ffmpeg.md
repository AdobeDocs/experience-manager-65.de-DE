---
title: FFmpeg für Communities
seo-title: FFmpeg für Communities
description: Installieren und Konfigurieren von FFmpeg für Communities
seo-description: Installieren und Konfigurieren von FFmpeg für Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: dbe28334-3b38-4362-b4f8-e0630e634503
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 1%

---

# FFmpeg für Communities {#ffmpeg-for-communities}

## Übersicht {#overview}

FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird bei der Installation für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) sowie für die Aktivierungsfunktion von AEM Communities verwendet.

FFmpeg wird in der Autorenumgebung verwendet, um Metadaten für hochgeladene Aktivierungsressourcen abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Aktivierungsressource angezeigt wird.

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf den Servern installiert sein, auf denen die AEM *author* -Instanz(en) gehostet wird.

1. Gehen Sie zu [https://www.ffmpeg.org](https://www.ffmpeg.org/).
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung (Macintosh, Windows oder Linux) herunter.

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen auf dem neuesten Stand zu halten.

1. Installieren Sie FFmpeg anhand der Anweisungen für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare FFmpeg-Datei in Ihrem Systempfad festgelegt ist.

   Sie sollten in der Lage sein, FFmpeg aus einem beliebigen Verzeichnis in Ihrem System auszuführen.

   * Beispiel: `ffmpeg -version`.

## FFmpeg Transcoding Service konfigurieren {#configure-ffmpeg-transcoding-service}

Standardmäßig werden bei installiertem FFmpeg mehrere Ausgabedarstellungen gemäß der Workflow-Definition [!UICONTROL DAM Update Asset] konfiguriert (Transkodierungen).

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Zielausgabeformate zu ändern. In den meisten Fällen ist eine Transkodierung nicht erforderlich.

So ändern Sie den Workflow [!UICONTROL DAM Update Asset] und deaktivieren Sie in diesem Beispiel die Transkodierung:

* Melden Sie sich mit Administratorrechten bei der Autoreninstanz an.
* Navigieren Sie von der globalen Navigation zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
* Suchen Sie **[!UICONTROL DAM Update Asset]**.
* Doppelklicken Sie auf , um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen.

   Ergebnisort: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doppelklicken Sie auf den Schritt **[!UICONTROL FFmpeg-Transkodierung]** , um auf das Dialogfeld Schritt-Eigenschaften zuzugreifen.
* Auf der Registerkarte **[!UICONTROL Process]** :

   * **[!UICONTROL Argumente]**: Löschen Sie alle Einträge, um die Transkodierung von Standardwerten zu deaktivieren:  `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

   ![configure-ffmpeg](assets/configure-ffmpeg.png)

* Wählen Sie **[!UICONTROL OK]** aus, um das Dialogfeld `Step Properties` zu schließen.

* Wählen Sie **[!UICONTROL Save]** aus, um den Workflow `DAM Update Asset` zu speichern.
