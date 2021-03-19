---
title: FFmpeg für Communities
seo-title: FFmpeg für Communities
description: Installation und Konfiguration von FFmpeg für Communities
seo-description: Installation und Konfiguration von FFmpeg für Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 1%

---


# FFmpeg für Communities {#ffmpeg-for-communities}

## Überblick {#overview}

FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird, wenn sie installiert ist, zur korrekten Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) sowie zur Aktivierung von AEM Communities verwendet.

FFmpeg wird in der Authoring-Umgebung verwendet, um Metadaten für hochgeladene Aktivierungsressourcen abzurufen und eine Miniaturansicht zu erstellen, die bei der Auflistung der Aktivierungsressource angezeigt wird.

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf dem (den) Server(n) installiert sein, auf dem (denen) die AEM *author* Instanz(en) gehostet wird.

1. Gehen Sie zu [https://www.ffmpeg.org](https://www.ffmpeg.org/).
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung herunter (Macintosh, Windows oder Linux).

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen auf dem neuesten Stand zu halten.

1. Installieren Sie FFmpeg entsprechend den Anweisungen für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare Datei FFmpeg im Systempfad festgelegt ist.

   Sie sollten in der Lage sein, FFmpeg von einem beliebigen Verzeichnis in Ihrem System auszuführen.

   * Beispiel: `ffmpeg -version`.

## FFmpeg Transcoding Service {#configure-ffmpeg-transcoding-service} konfigurieren

Standardmäßig werden bei der Installation von FFmpeg mehrere Darstellungen gemäß der Workflow-Definition von [!UICONTROL DAM Update Asset] konfiguriert (Transkodierungen).

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Zielgruppe-Darstellungen zu ändern. In den meisten Fällen ist eine Transkodierung nicht erforderlich.

So ändern Sie den Workflow [!UICONTROL DAM-Update-Asset] und deaktivieren Sie in diesem Beispiel die Transkodierung:

* Melden Sie sich mit Administratorrechten bei der Autoreninstanz an.
* Navigieren Sie in der globalen Navigation zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
* Suchen Sie nach **[!UICONTROL DAM Update Asset]**.
* Klicken Sie mit der Dublette, um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen.

   Ergebnis: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Klicken Sie bei gedrückter Dublette auf den Schritt **[!UICONTROL FFmpeg transcoding]**, um das Dialogfeld &quot;Schritteigenschaften&quot;aufzurufen.
* Auf der Registerkarte **[!UICONTROL Prozess]**:

   * **[!UICONTROL Anpassungen]**: Löschen Sie alle Einträge, um die Transkodierung von Standardwerten zu deaktivieren:  `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

   ![configure-ffmpeg](assets/configure-ffmpeg.png)

* Wählen Sie **[!UICONTROL OK]**, um das `Step Properties`-Dialogfeld zu schließen.

* Wählen Sie **[!UICONTROL Speichern]**, um den `DAM Update Asset`-Workflow zu speichern.



