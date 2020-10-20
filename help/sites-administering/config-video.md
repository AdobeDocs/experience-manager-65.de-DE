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
source-git-commit: 535a175486a2d0f31762d71954c4fead2ef246e1
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 21%

---


# Konfigurieren der Videokomponente {#configure-the-video-component}

The [Video component](/help/sites-authoring/default-components-foundation.md#video) lets you place a predefined, out-of-the-box (OOTB) video asset on your page.

Damit eine ordnungsgemäße Transkodierung erfolgt, installiert ein Administrator FFmpeg separat. Siehe [Installieren von FFmpeg und Konfigurieren von AEM](#install-ffmpeg). Administrators also [Configure Video Profiles](#configure-video-profiles) for use with HTML5 elements.

## Videoprofile konfigurieren {#configure-video-profiles}

Definieren Sie für die Verwendung von HTML5-Elementen Video-Profil. Die hier getroffene Auswahl wird der Reihenfolge nach verwendet. Um zuzugreifen, verwenden Sie [Designmodus](/help/sites-authoring/default-components-designmode.md) (nur in der klassischen Benutzeroberfläche) und wählen Sie die Registerkarte **[!UICONTROL Profile]** aus:

![chlimage_1-317](assets/chlimage_1-317.png)

From this dialog, you can also configure the design of the Video component and parameters for [!UICONTROL Playback], [!UICONTROL Flash], and [!UICONTROL Advanced].

## Installieren und Konfigurieren von AEM {#install-ffmpeg}

Die Video-Komponente nutzt das Open-Source-Produkt FFmpeg eines Drittanbieters für die Transkodierung von Videos. Heruntergeladen von [https://ffmpeg.org/](https://ffmpeg.org/). Nachdem Sie FFmpeg installiert haben, konfigurieren Sie AEM, um einen bestimmten Audio-Codec und bestimmte Laufzeitoptionen zu verwenden.

Gehen Sie wie folgt vor, um FFmpeg unter **Windows** zu installieren:

1. Download the compiled binary as `ffmpeg.zip`.
1. Archivieren Sie die Datei in einem Ordner.
1. Legen Sie die Variable &quot;Umgebung&quot; `PATH` auf &lt;*Ihr-ffmpeg-location*>`\bin`fest.
1. Starten Sie AEM neu.

Gehen Sie wie folgt vor, um FFmpeg unter **Mac OS X** zu installieren:

1. Installieren Sie Xcode unter [developer.apple.com/xcode](https://developer.apple.com/xcode/).
1. Installieren Sie unter [XQuartz](https://www.xquartz.org) , um [X11](https://support.apple.com/de-de/HT201341)zu erhalten.
1. Installieren Sie die MacPorts unter [www.macports.org](https://www.macports.org/).
1. Führen Sie in der Konsole den Befehl `sudo port install ffmpeg` aus und befolgen Sie die Anweisungen auf dem Bildschirm. Stellen Sie sicher, dass der Pfad der `FFmpeg` ausführbaren Datei der `PATH` Systemvariablen hinzugefügt wird.

Gehen Sie wie folgt vor, um FFmpeg unter **Mac OS X 10.6** mit der vorkompilierten Version zu installieren:

1. Laden Sie die vorkompilierte Version herunter.
1. Heben Sie die Archivierung im `/usr/local` Verzeichnis auf.
1. Führen Sie in der Konsole aus `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`. Ändern Sie die Pfade entsprechend.

Gehen Sie wie **folgt vor, um AEM** zu konfigurieren:

>[!NOTE]
>
>Diese Schritte sind nur erforderlich, wenn eine weitere Anpassung der Codecs erforderlich ist.

1. Open [!UICONTROL CRXDE Lite] in your web browser. Access [http://localhost:4502/crx/de](http://localhost:4502/crx/de).
2. Select the `/libs/settings/dam/video/format_aac/jcr:content` node and ensure that the node properties are as follows:

   * `audioCodec` das `aac`.
   * `customArgs` das `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8`.

3. To customize the configuration, create an overlay in `/apps/settings/` node and move the same structure under `/conf/global/settings/` node. It cannot be edited in `/libs` node. Um beispielsweise einen Überlagerungspfad zu erstellen, erstellen Sie ihn `/libs/settings/dam/video/fullhd-bp`unter `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Überlagern und bearbeiten Sie den gesamten Profilknoten und nicht nur die Eigenschaft, die geändert werden muss. Solche Ressourcen werden nicht über SlingResourceMerger aufgelöst.

4. Haben Sie eine der Eigenschaften geändert, klicken Sie auf **[!UICONTROL Alle speichern.]**

>[!NOTE]
>
>Änderungen an den standardmäßigen Out-of-the-Box-Workflow-Modellen (OOTB) werden beim Aktualisieren Ihrer AEM nicht beibehalten. Adobe empfiehlt, dass Sie die geänderten Workflow-Modelle kopieren, bevor Sie diese bearbeiten. For example, copy the OOTB [!UICONTROL DAM Update Asset] model before editing the FFmpeg Transcoding step in the [!UICONTROL DAM Update Asset] model to pick video-profile names that existed before the upgrade. Then, you can overlay the `/apps` node to let AEM retrieve the custom changes to the OOTB model.
