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
source-git-commit: 0362be4d78fa39ac73c9be5dd5d08ccfebd21edc
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 21%

---


# Konfigurieren der Videokomponente {#configure-the-video-component}

Mit der [Videokomponente](/help/sites-authoring/default-components-foundation.md#video) können Sie ein vordefiniertes OOTB-Video-Asset (Out-of-the-Box) auf Ihrer Seite platzieren.

Damit eine ordnungsgemäße Transkodierung erfolgt, installiert ein Administrator FFmpeg separat. Siehe [Installieren Sie FFmpeg und konfigurieren Sie AEM](#install-ffmpeg). Administratoren können auch [Video-Profil](#configure-video-profiles) für die Verwendung mit HTML5-Elementen konfigurieren.

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt stattdessen die Verwendung der [Kernkomponenten-Einbettungskomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/embed.html).

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente ohne umfangreiche Anpassungen auf Projektebene standardmäßig funktioniert.

## Videoprofile konfigurieren {#configure-video-profiles}

Definieren Sie für die Verwendung von HTML5-Elementen Video-Profil. Die hier getroffene Auswahl wird der Reihenfolge nach verwendet. Um zuzugreifen, verwenden Sie [Designmodus](/help/sites-authoring/default-components-designmode.md) (nur in der klassischen Benutzeroberfläche) und wählen Sie die Registerkarte **[!UICONTROL Profile]** aus:

![chlimage_1-317](assets/chlimage_1-317.png)

In diesem Dialogfeld können Sie auch den Entwurf der Videokomponente und die Parameter für [!UICONTROL Wiedergabe], [!UICONTROL Flash] und [!UICONTROL Advanced] konfigurieren.

## Installieren und konfigurieren Sie AEM {#install-ffmpeg}

Die Video-Komponente nutzt das Open-Source-Produkt FFmpeg eines Drittanbieters für die Transkodierung von Videos. Heruntergeladen von [https://ffmpeg.org/](https://ffmpeg.org/). Nachdem Sie FFmpeg installiert haben, konfigurieren Sie AEM, um einen bestimmten Audio-Codec und bestimmte Laufzeitoptionen zu verwenden.

Gehen Sie wie folgt vor, um FFmpeg unter **Windows** zu installieren:

1. Laden Sie die kompilierte Binärdatei als `ffmpeg.zip` herunter.
1. Archivieren Sie die Datei in einem Ordner.
1. Setzen Sie die Systemvariable `PATH` auf &lt;*your-ffmpeg-location*`\bin`.
1. Starten Sie AEM neu.

Gehen Sie wie folgt vor, um FFmpeg unter **Mac OS X** zu installieren:

1. Installieren Sie Xcode verfügbar unter [developer.apple.com/xcode](https://developer.apple.com/xcode/).
1. Installieren Sie unter [XQuartz](https://www.xquartz.org), um [X11](https://support.apple.com/de-de/HT201341) abzurufen.
1. Installieren Sie MacPorts, die unter [www.macports.org](https://www.macports.org/) verfügbar sind.
1. Führen Sie in der Konsole den Befehl `sudo port install ffmpeg` aus und befolgen Sie die Anweisungen auf dem Bildschirm. Stellen Sie sicher, dass der Pfad der ausführbaren Datei `FFmpeg` der Systemvariablen `PATH` hinzugefügt wird.

Gehen Sie wie folgt vor, um FFmpeg unter **Mac OS X 10.6** mit der vorkompilierten Version zu installieren:

1. Laden Sie die vorkompilierte Version herunter.
1. Heben Sie die Archivierung im Ordner `/usr/local` auf.
1. Führen Sie in der Konsole `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg` aus. Ändern Sie die Pfade entsprechend.

Gehen Sie wie folgt vor, um AEM **zu konfigurieren:**

>[!NOTE]
>
>Diese Schritte sind nur erforderlich, wenn eine weitere Anpassung der Codecs erforderlich ist.

1. Öffnen Sie [!UICONTROL CRXDE Lite] in Ihrem Webbrowser. Zugriff auf [http://localhost:4502/crx/de](http://localhost:4502/crx/de).
2. Wählen Sie den Knoten `/libs/settings/dam/video/format_aac/jcr:content` aus und stellen Sie sicher, dass die Knoteneigenschaften wie folgt lauten:

   * `audioCodec` das `aac`.
   * `customArgs` das `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8`.

3. Um die Konfiguration anzupassen, erstellen Sie eine Überlagerung im Knoten `/apps/settings/` und verschieben Sie die gleiche Struktur unter dem Knoten `/conf/global/settings/`. Es kann nicht im Knoten `/libs` bearbeitet werden. Um beispielsweise den Pfad `/libs/settings/dam/video/fullhd-bp` zu überlagern, erstellen Sie ihn unter `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Überlagern und bearbeiten Sie den gesamten Profilknoten und nicht nur die Eigenschaft, die geändert werden muss. Solche Ressourcen werden nicht über SlingResourceMerger aufgelöst.

4. Haben Sie eine der Eigenschaften geändert, klicken Sie auf **[!UICONTROL Alle speichern.]**

>[!NOTE]
>
>Änderungen an den standardmäßigen Out-of-the-Box-Workflow-Modellen (OOTB) werden beim Aktualisieren Ihrer AEM nicht beibehalten. Adobe empfiehlt, dass Sie die geänderten Workflow-Modelle kopieren, bevor Sie diese bearbeiten. Kopieren Sie beispielsweise das OOTB [!UICONTROL DAM Update Asset]-Modell, bevor Sie den FFmpeg Transcoding-Schritt im [!UICONTROL DAM Update Asset]-Profil bearbeiten, um die vor der Aktualisierung vorhandenen Videonamen auszuwählen. Anschließend können Sie den Knoten `/apps` überlagern, damit AEM die benutzerdefinierten Änderungen am OOTB-Modell abrufen können.
