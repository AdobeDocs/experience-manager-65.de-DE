---
title: Konfigurieren der Videokomponente
seo-title: Konfigurieren der Videokomponente
description: Erfahren Sie, wie Sie die Videokomponente konfigurieren können.
seo-description: Erfahren Sie, wie Sie die Videokomponente konfigurieren können.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Konfigurieren der Videokomponente {#configure-the-video-component}

The [Video component](/help/sites-authoring/default-components-foundation.md#video) lets you place a predefined, OOTB (out-of-the-box) video element on your page.

For proper transcoding to occur, your administrator must [Install FFmpeg and configure AEM](#install-ffmpeg) separately. Ihr Administrator kann auch [Ihre Videoprofile für die Verwendung mit HTML5-Elementen konfigurieren](#configure-video-profiles).

## Videoprofile konfigurieren {#configure-video-profiles}

Es empfiehlt sich, Videoprofile für die Verwendung von HTML5-Elementen zu definieren. Die hier getroffene Auswahl wird der Reihenfolge nach verwendet. Um zuzugreifen, verwenden Sie [Designmodus](/help/sites-authoring/default-components-designmode.md) (nur in der klassischen Benutzeroberfläche) und wählen Sie die Registerkarte **[!UICONTROL Profile]** aus:

![chlimage_1-317](assets/chlimage_1-317.png)

You can also configure the design of the video components and parameters for [!UICONTROL Playback], [!UICONTROL Flash], and [!UICONTROL Advanced].

## Installieren und Konfigurieren von AEM {#install-ffmpeg}

The Video Component relies on the third-party open-source product FFmpeg for proper transcoding of videos that can be downloaded from [https://ffmpeg.org/](https://ffmpeg.org/). Nach der Installation von FFmpeg müssen Sie AEM zur Verwendung eines bestimmten Audiocodecs und bestimmter Echtzeitoptionen konfigurieren.

**So installieren Sie FFmpeg für Ihre Plattform**:

* **Windows:**

   1. Laden Sie die kompilierte Binärdatei als `ffmpeg.zip` herunter.
   1. Entpacken Sie den Inhalt in einen Ordner.
   1. Die Variable &quot;Umgebung&quot;des Systems `PATH` auf `<*your-ffmpeg-locatio*n>\bin`
   1. Starten Sie AEM neu.

* **Unter Mac OS X:**

   1. Install Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Installieren Sie XQuartz/X11.
   1. Install MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. Führen Sie in der Konsole den folgenden Befehl aus und befolgen Sie die Anweisungen:

      `sudo port install ffmpeg`

      `FFmpeg` muss in sein, `PATH` damit AEM sie über die Befehlszeile abrufen kann.

* **Vorkompilierte Version für OS X 10.6:**

   1. Laden Sie die vorkompilierte Version herunter.
   1. Extract it to the `/usr/local` directory.
   1. Führen Sie vom Terminal aus:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**Konfigurieren von AEM**:

1. Open [!UICONTROL CRXDE Lite] in your web browser. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Select the `/libs/settings/dam/video/format_aac/jcr:content` node and ensure that the node properties are as follows:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. To customize the configuration, create an overlay in `/apps/settings/` node and move the same structure under `/conf/global/settings/` node. It cannot be edited in `/libs` node. Um beispielsweise einen Überlagerungspfad zu erstellen, erstellen Sie ihn `/libs/settings/dam/video/fullhd-bp`unter `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Überlagern und bearbeiten Sie den gesamten Profilknoten und nicht nur die Eigenschaft, die geändert werden muss. Solche Ressourcen werden nicht über SlingResourceMerger aufgelöst.

1. Haben Sie eine der Eigenschaften geändert, klicken Sie auf **[!UICONTROL Alle speichern]**.

>[!NOTE]
>
>OOTB-Workflow-Modelle werden beim Aktualisieren der AEM-Instanz nicht beibehalten. Adobe empfiehlt, dass Sie OOTB-Workflow-Modelle kopieren, bevor Sie sie bearbeiten. For example, copy the OOTB [!UICONTROL DAM Update Asset] model before editing the FFmpeg Transcoding step in the [!UICONTROL DAM Update Asset] model to pick video-profile names that existed before the upgrade. Then, you can overlay the `/apps` node to let AEM retrieve the custom changes to the OOTB model.

