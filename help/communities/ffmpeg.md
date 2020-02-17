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
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# FFmpeg für Communities {#ffmpeg-for-communities}

## Überblick {#overview}

FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird, falls installiert, für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video) sowie für die Funktion zur Aktivierung von AEM Communities verwendet.

FFmpeg wird in der Autorenumgebung verwendet, um Metadaten für hochgeladene Ressourcen zur Aktivierung abzurufen und eine Miniaturansicht zu erstellen, die bei der Auflistung der Aktivierungsressource angezeigt wird.

## Installieren von FFmpeg {#installing-ffmpeg}

FFmpeg sollte auf den Servern installiert sein, auf denen die AEM- *Autoreninstanz* gehostet wird.

1. Go to [https://www.ffmpeg.org](https://www.ffmpeg.org/)
1. Laden Sie die neueste Version von FFmpeg für Ihre spezifische Umgebung (Macintosh, Windows oder Linux) herunter

   * Es ist wichtig, FFmpeg aufgrund von Sicherheitslücken in älteren Versionen auf dem neuesten Stand zu halten.

1. Installieren Sie FFmpeg entsprechend den Anweisungen für das Betriebssystem.

1. Stellen Sie sicher, dass die ausführbare Datei FFmpeg im Systempfad festgelegt ist.

   Sie sollten in der Lage sein, FFmpeg von einem beliebigen Verzeichnis in Ihrem System auszuführen.

   * for example, `ffmpeg -version`

## FFmpeg Transcoding-Dienst konfigurieren {#configure-ffmpeg-transcoding-service}

Wenn FFmpeg installiert ist, werden gemäß der Definition des DAM Update Asset-Workflows standardmäßig mehrere Darstellungen konfiguriert (Transkodierungen).

Da die Transkodierungen CPU-intensiv sind, wird empfohlen, die Liste der Zieldarstellungen zu ändern. In den meisten Fällen ist eine Transkodierung nicht erforderlich.

So ändern Sie den Arbeitsablauf für DAM Update Asset und deaktivieren Sie in diesem Beispiel die Transkodierung:

* Anmelden bei der Autoreninstanz mit Administratorrechten
* Aus globaler Navigation: **[!UICONTROL Werkzeuge > Workflow > Modelle]**
* Locate **[!UICONTROL DAM Update Asset]**
* Doppelklicken Sie auf , um den Workflow zur Bearbeitung in der klassischen Benutzeroberfläche zu öffnen

   Ergebnis: [http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html](http://localhost:4502/cf#/etc/workflow/models/dam/update_asset.html)

* Doppelklicken Sie auf den Schritt **[!UICONTROL FFmpeg-Transkodierung]** , um das Dialogfeld Schritt-Eigenschaften aufzurufen.
* Under the **[!UICONTROL Process]** tab:

   * **[!UICONTROL Anpassungen]**: Löschen Sie alle Einträge, um die Transkodierung von Standardwerten zu deaktivieren: `profile:firefoxhq,profile:hq,profile:flv,profile:iehq`

![chlimage_1-372](assets/chlimage_1-372.png)

* Select **[!UICONTROL OK]** to close the `Step Properties` dialog

* Select **[!UICONTROL Save]** to save the `DAM Update Asset` workflow

   (obere linke Ecke)

