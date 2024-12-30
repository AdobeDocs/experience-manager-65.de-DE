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

FFmpeg ist eine Lösung zum Konvertieren und Streamen von Audio und Video und wird, wenn installiert, für die korrekte Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) verwendet.

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf den Servern installiert sein, die die AEM-(*)*.

1. Navigieren Sie zu [https://www.ffmpeg.org](https://www.ffmpeg.org/).
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung (Macintosh, Windows oder Linux) herunter.

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen aktuell zu halten.

1. Installieren Sie FFmpeg wie folgt für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare Datei FFmpeg in Ihrem Systempfad festgelegt ist.

   Sie sollten FFmpeg von einem beliebigen Verzeichnis in Ihrem System aus ausführen können.

   * Zum Beispiel: `ffmpeg -version`.

## Konfigurieren des FFmpeg-Transkodierungs-Service {#configure-ffmpeg-transcoding-service}

Standardmäßig werden bei der Installation von FFmpeg mehrere Ausgabedarstellungen (Transkodierungen) gemäß der Workflow-Definition [!UICONTROL DAM Update Asset] konfiguriert.

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Ziel-Ausgabedarstellungen zu ändern. In den meisten Fällen ist keine Transkodierung erforderlich.

So ändern Sie den [!UICONTROL DAM Update Asset]-Workflow und deaktivieren in diesem Beispiel die Transkodierung:

* Melden Sie sich mit Administratorrechten bei der Autoreninstanz an.
* Navigieren Sie in der globalen Navigation zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
* Suchen Sie **[!UICONTROL DAM-Update-Asset]**.
* Doppelklicken Sie, um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen.

  Ergebnisspeicherort: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doppelklicken Sie auf den Schritt **[!UICONTROL FFmpeg]**, um auf das Dialogfeld Schritteigenschaften zuzugreifen.
* Auf der Registerkarte **[!UICONTROL Prozess]**:

   * **[!UICONTROL Argumente]**: Alle Einträge löschen, um die Transkodierung zu deaktivieren Standardwerte: `profile:format_ogg,profile:format_aac,profile:format_flv,profile:format_aac_ie`

  ![configure-ffmpeg](assets/configure-ffmpeg.png)

* Klicken Sie **[!UICONTROL OK]**, um das Dialogfeld &quot;`Step Properties`&quot; zu schließen.

* Wählen Sie **[!UICONTROL Speichern]**, um den `DAM Update Asset` Workflow zu speichern.
