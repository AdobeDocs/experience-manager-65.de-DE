---
title: FFmpeg für Communities
seo-title: FFmpeg for Communities
description: Installieren und Konfigurieren von FFmpeg für Communities
seo-description: How to install and configure FFmpeg for Communities
uuid: ef2f821c-70e9-4889-a8d7-a93b10a1d428
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 739ec991-552b-42cd-85cd-984d1c9fe8fd
role: Admin
exl-id: dbe28334-3b38-4362-b4f8-e0630e634503
source-git-commit: 942db8fe3dad16be53dc6abe0e519d97a659e480
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 1%

---

# FFmpeg für Communities {#ffmpeg-for-communities}

## Übersicht {#overview}

FFmpeg ist eine Lösung für das Konvertieren und Streaming von Audio und Video und wird, falls installiert, für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video).

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf den Servern installiert sein, auf denen das AEM gehostet wird *author* Instanz(en).

1. Navigieren Sie zu [https://www.ffmpeg.org](https://www.ffmpeg.org/).
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung (Macintosh, Windows oder Linux) herunter.

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen auf dem neuesten Stand zu halten.

1. Installieren Sie FFmpeg anhand der Anweisungen für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare FFmpeg-Datei in Ihrem Systempfad festgelegt ist.

   Sie sollten in der Lage sein, FFmpeg aus einem beliebigen Verzeichnis in Ihrem System auszuführen.

   * Beispiel: `ffmpeg -version`.

## FFmpeg Transcoding Service konfigurieren {#configure-ffmpeg-transcoding-service}

Standardmäßig werden bei der Installation von FFmpeg mehrere Ausgabedarstellungen gemäß der [!UICONTROL DAM-Update-Asset] Workflow-Definition.

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Zielausgabeformate zu ändern. In den meisten Fällen ist eine Transkodierung nicht erforderlich.

So ändern Sie die [!UICONTROL DAM-Update-Asset] -Workflow und in diesem Beispiel zur Deaktivierung der Transkodierung:

* Melden Sie sich mit Administratorrechten bei der Autoreninstanz an.
* Navigieren Sie von der globalen Navigation zu **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
* Suchen **[!UICONTROL DAM-Update-Asset]**.
* Doppelklicken Sie auf , um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen.

   Ergebnisort: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doppelklicken Sie auf die **[!UICONTROL FFmpeg-Transkodierung]** Schritt , um auf das Dialogfeld Schritt-Eigenschaften zuzugreifen.
* Unter dem **[!UICONTROL Prozess]** tab:

   * **[!UICONTROL Werbemittel]**: Löschen Sie alle Einträge, um die Transkodierung von Standardwerten zu deaktivieren: `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

   ![configure-ffmpeg](assets/configure-ffmpeg.png)

* Auswählen **[!UICONTROL OK]** zum Schließen der `Step Properties` angezeigt.

* Auswählen **[!UICONTROL Speichern]** , um `DAM Update Asset` Arbeitsablauf.
