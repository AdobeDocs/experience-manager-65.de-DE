---
title: FFmpeg für Communities
description: Installieren und Konfigurieren von FFmpeg für Communities
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: dbe28334-3b38-4362-b4f8-e0630e634503
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---

# FFmpeg für Communities {#ffmpeg-for-communities}

## Überblick {#overview}

FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird bei Installation für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) verwendet.

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf den Servern installiert sein, auf denen die AEM *author* -Instanz(en) gehostet wird.

1. Wechseln Sie zu [https://www.ffmpeg.org](https://www.ffmpeg.org/).
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung (Macintosh, Windows oder Linux) herunter.

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen auf dem neuesten Stand zu halten.

1. Installieren Sie FFmpeg anhand der Anweisungen für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare FFmpeg-Datei in Ihrem Systempfad festgelegt ist.

   Sie sollten in der Lage sein, FFmpeg aus einem beliebigen Verzeichnis in Ihrem System auszuführen.

   * Zum Beispiel: `ffmpeg -version`.

## FFmpeg Transcoding Service konfigurieren {#configure-ffmpeg-transcoding-service}

Standardmäßig werden bei installiertem FFmpeg mehrere Ausgabedarstellungen gemäß der Workflow-Definition für [!UICONTROL DAM-Update-Asset] konfiguriert (Transkodierungen).

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Zielausgabeformate zu ändern. In den meisten Fällen ist eine Transkodierung nicht erforderlich.

So ändern Sie den Workflow [!UICONTROL DAM-Update-Asset] und deaktivieren Sie in diesem Beispiel die Transkodierung:

* Melden Sie sich mit Administratorrechten bei der Autoreninstanz an.
* Navigieren Sie von der globalen Navigation zu &quot;**[!UICONTROL Tools]**&quot;> &quot;**[!UICONTROL Workflow]**&quot;> &quot;**[!UICONTROL Modelle]**&quot;.
* Suchen Sie nach **[!UICONTROL DAM Update Asset]**.
* Doppelklicken Sie auf , um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen.

  Resultierender Speicherort: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doppelklicken Sie auf den Schritt **[!UICONTROL FFmpeg-Transkodierung]** , um auf das Dialogfeld &quot;Schritteigenschaften&quot;zuzugreifen.
* Auf der Registerkarte **[!UICONTROL Prozess]** :

   * **[!UICONTROL Argumente]**: Löschen Sie alle Einträge, um die Transkodierung von Standardwerten zu deaktivieren: `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

  ![configure-ffmpeg](assets/configure-ffmpeg.png)

* Wählen Sie **[!UICONTROL OK]** aus, um das Dialogfeld `Step Properties` zu schließen.

* Wählen Sie **[!UICONTROL Speichern]** aus, um den Workflow `DAM Update Asset` zu speichern.
