---
title: Konfigurieren der Videokomponente
description: Erfahren Sie, wie Sie mit der Videokomponente in Adobe Experience Manager ein vordefiniertes, vordefiniertes Video-Asset auf Ihrer Seite platzieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 9c97f99e-d6ef-4817-8b2a-201ab22f2b38
source-git-commit: 06a6d4e0ba2aeaefcfb238233dd98e8bbd6731da
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 82%

---

# Konfigurieren der Videokomponente {#configure-the-video-component}

Mit der [Videokomponente](/help/sites-authoring/default-components-foundation.md#video) können Sie ein vordefiniertes, vorkonfiguriertes Videoelement auf Ihrer Seite platzieren.

Damit eine korrekte Transkodierung erfolgt, installiert ein Admin FFmpeg separat. Siehe [Installieren von FFmpeg und Konfigurieren von AEM](#install-ffmpeg). Admins können auch [Videoprofile](#configure-video-profiles) für die Verwendung mit HTML5-Elementen konfigurieren..

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Einbetten“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/embed.html?lang=de) zu verwenden.

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente vorkonfiguriert und ohne umfassende Anpassungen auf Projektebene funktioniert.

## Videoprofile konfigurieren {#configure-video-profiles}

Definieren Sie Videoprofile für die Verwendung von HTML5-Elementen. Die hier gewählten werden der Reihe nach verwendet. Um zuzugreifen, verwenden Sie [Design-Modus](/help/sites-authoring/default-components-designmode.md) (nur in der klassischen Benutzeroberfläche) und wählen Sie die Registerkarte **[!UICONTROL Profile]** aus:

![chlimage_1-317](assets/chlimage_1-317.png)

In diesem Dialog können Sie auch das Design der Videokomponenten und Parameter für [!UICONTROL Wiedergabe], [!UICONTROL Flash] und [!UICONTROL Erweitert] konfigurieren.

## Installieren von FFmpeg und Konfigurieren von AEM {#install-ffmpeg}

Die Videokomponente stützt sich bei der Transkodierung von Videos auf das Open-Source-Produkt FFmpeg eines Drittanbieters. Heruntergeladen von [https://ffmpeg.org/](https://ffmpeg.org/). Nach der Installation von FFmpeg müssen Sie AEM zur Verwendung eines bestimmten Audiocodecs und bestimmter Laufzeitoptionen konfigurieren.

Gehen Sie wie folgt vor, um FFmpeg unter **Windows** zu installieren:

1. Laden Sie die kompilierte Binärdatei als `ffmpeg.zip` herunter.
1. Dekomprieren Sie sie in einen Ordner.
1. Legen Sie die Systemumgebungsvariable `PATH` als &lt;*your-ffmpeg-location*>`\bin` fest.
1. Starten Sie AEM neu.

So installieren Sie FFmpeg in **MACOS X** führen Sie die folgenden Schritte aus:

1. Installieren Sie Xcode, das unter [developer.apple.com/xcode](https://developer.apple.com/xcode/) verfügbar ist.
1. Installieren Sie es unter [XQuartz](https://www.xquartz.org), um [X11](https://support.apple.com/en-us/100724) zu erhalten.
1. Installieren Sie die unter [www.macports.org](https://www.macports.org/) verfügbaren MacPorts.
1. Führen Sie in der Konsole `sudo port install ffmpeg` und befolgen Sie die Anweisungen auf dem Bildschirm. Stellen Sie sicher, dass der Pfad der ausführbaren Datei `FFmpeg` zur Systemvariablen `PATH` hinzugefügt wird.

So installieren Sie FFmpeg in **macOS X 10.6** Führen Sie mithilfe der vorkompilierten Version die folgenden Schritte aus:

1. Laden Sie die vorkompilierte Version herunter.
1. Archivieren Sie sie im Verzeichnis `/usr/local`.
1. Führen Sie in der Konsole `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`. Ändern Sie den Pfad entsprechend.

Gehen Sie wie folgt vor, um **AEM zu konfigurieren**:

>[!NOTE]
>
>Diese Schritte sind nur erforderlich, wenn eine weitere Anpassung der Codecs erforderlich ist.

1. Öffnen Sie [!UICONTROL CRXDE Lite] in einem Webbrowser. Besuchen Sie [http://localhost:4502/crx/de](http://localhost:4502/crx/de).
2. Wählen Sie den Knoten `/libs/settings/dam/video/format_aac/jcr:content` aus und stellen Sie sicher, dass die Knoteneigenschaften wie folgt lauten:

   * `audioCodec` ist `aac`.
   * `customArgs` ist `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8`.

3. Um die Konfiguration anzupassen, erstellen Sie eine Überlagerung im Knoten `/apps/settings/` und verschieben Sie dieselbe Struktur unter den Knoten `/conf/global/settings/`. Sie kann nicht im Knoten `/libs` bearbeitet werden. Um zum Beispiel den Pfad `/libs/settings/dam/video/fullhd-bp` zu überlagern, erstellen Sie ihn bei `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Überlagern und bearbeiten Sie den gesamten Profilknoten und nicht nur die Eigenschaft, die geändert werden muss. Solche Ressourcen werden nicht über SlingResourceMerger aufgelöst.

4. Haben Sie eine der Eigenschaften geändert, klicken Sie auf **[!UICONTROL Alle speichern]**.

>[!NOTE]
>
>Standardmäßige vorkonfigurierte Workflow-Modelle bleiben beim Upgrade Ihrer AEM-Instanz nicht erhalten. Adobe empfiehlt, die geänderten Workflow-Modelle zu kopieren, bevor Sie sie bearbeiten. Kopieren Sie beispielsweise das vorkonfigirierte Modell [!UICONTROL DAM Update Asset], bevor Sie den FFmpeg-Transkodierungsschritt im Modell [!UICONTROL DAM Update Asset] ändern, um bereits vor dem Upgrade vorhandene Videoprofilnamen auszuwählen. Sie können dann den Knoten `/apps` überlagern, damit AEM die benutzerdefinierten Änderungen am vorkonfigurierten Modell abrufen kann.
