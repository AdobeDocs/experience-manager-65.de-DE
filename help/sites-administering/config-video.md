---
title: Konfigurieren der Videokomponente
seo-title: Configure the Video component
description: Erfahren Sie, wie Sie die Videokomponente konfigurieren können.
seo-description: Learn how to configure the Video Component.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 9c97f99e-d6ef-4817-8b2a-201ab22f2b38
source-git-commit: b1e0ea01688095b29d8fb18baf6fa0bda660dad5
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 19%

---

# Konfigurieren der Videokomponente {#configure-the-video-component}

Die [Videokomponente](/help/sites-authoring/default-components-foundation.md#video) können Sie ein vordefiniertes OOTB-Video-Asset (Out-of-the-Box) auf Ihrer Seite platzieren.

Damit eine korrekte Transkodierung erfolgt, installiert ein Administrator FFmpeg separat. Siehe [Installieren Sie FFmpeg und konfigurieren Sie AEM](#install-ffmpeg). Administratoren können auch [Videoprofile konfigurieren](#configure-video-profiles) zur Verwendung mit HTML5-Elementen.

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, die [Einbettungskomponente der Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/embed.html) anstatt.

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente ohne umfassende Anpassungen auf Projektebene nativ funktioniert.

## Videoprofile konfigurieren {#configure-video-profiles}

Definieren Sie Videoprofile für die Verwendung von HTML5-Elementen. Die hier getroffene Auswahl wird der Reihenfolge nach verwendet. Um zuzugreifen, verwenden Sie [Designmodus](/help/sites-authoring/default-components-designmode.md) (nur in der klassischen Benutzeroberfläche) und wählen Sie die Registerkarte **[!UICONTROL Profile]** aus:

![chlimage_1-317](assets/chlimage_1-317.png)

In diesem Dialogfeld können Sie auch das Design der Videokomponente und die Parameter für [!UICONTROL Wiedergabe], [!UICONTROL Flash]und [!UICONTROL Erweitert].

## Installieren Sie FFmpeg und konfigurieren Sie AEM {#install-ffmpeg}

Die Videokomponente stützt sich bei der Transkodierung von Videos auf das Open-Source-Produkt FFmpeg eines Drittanbieters. Heruntergeladen von [https://ffmpeg.org/](https://ffmpeg.org/). Konfigurieren Sie nach der Installation von FFmpeg AEM so, dass ein bestimmter Audio-Codec und bestimmte Laufzeitoptionen verwendet werden.

So installieren Sie FFmpeg in **Windows** führen Sie die folgenden Schritte aus:

1. Laden Sie die kompilierte Binärdatei als `ffmpeg.zip`.
1. Archivierung in einem Ordner aufheben.
1. Systemumgebungsvariable festlegen `PATH` bis &lt;*your-ffmpeg-location*>`\bin`.
1. Starten Sie AEM neu.

So installieren Sie FFmpeg in **Mac OS X** führen Sie die folgenden Schritte aus:

1. Installieren Sie Xcode unter [developer.apple.com/xcode](https://developer.apple.com/xcode/).
1. Installieren Sie das unter [XQuartz](https://www.xquartz.org) um [X11](https://support.apple.com/de-de/HT201341).
1. Installieren Sie die unter verfügbaren MacPorts. [www.macports.org](https://www.macports.org/).
1. Führen Sie in der Konsole die `sudo port install ffmpeg` und befolgen Sie die Anweisungen auf dem Bildschirm. Stellen Sie sicher, dass der Pfad der `FFmpeg` ausführbare Datei hinzugefügt wird. `PATH` Systemvariable.

So installieren Sie FFmpeg in **Mac OS X 10.6** Führen Sie mithilfe der vorkompilierten Version die folgenden Schritte aus:

1. Laden Sie die vorkompilierte Version herunter.
1. Archivieren Sie sie in `/usr/local` Verzeichnis.
1. Führen Sie in der Konsole `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`. Ändern Sie die Pfade entsprechend.

nach **AEM konfigurieren** führen Sie die folgenden Schritte aus:

>[!NOTE]
>
>Diese Schritte sind nur erforderlich, wenn eine weitere Anpassung der Codecs erforderlich ist.

1. Öffnen [!UICONTROL CRXDE Lite] in Ihrem Webbrowser. Zugriff [http://localhost:4502/crx/de](http://localhost:4502/crx/de).
2. Wählen Sie die `/libs/settings/dam/video/format_aac/jcr:content` und stellen Sie sicher, dass die Knoteneigenschaften wie folgt lauten:

   * `audioCodec` das `aac`.
   * `customArgs` das `-flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8`.

3. Um die Konfiguration anzupassen, erstellen Sie eine Überlagerung in `/apps/settings/` Knoten und verschieben Sie dieselbe Struktur unter `/conf/global/settings/` Knoten. Es kann nicht bearbeitet werden in `/libs` Knoten. Beispiel: Überlagerungspfad `/libs/settings/dam/video/fullhd-bp`, erstellen Sie es unter `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Überlagern und bearbeiten Sie den gesamten Profilknoten und nicht nur die Eigenschaft, die geändert werden muss. Solche Ressourcen werden nicht über SlingResourceMerger aufgelöst.

4. Haben Sie eine der Eigenschaften geändert, klicken Sie auf **[!UICONTROL Alle speichern]**.

>[!NOTE]
>
>Änderungen an den standardmäßigen OOTB-Workflow-Modellen (Standard Out-of-the-Box) bleiben beim Upgrade Ihrer AEM-Instanz nicht erhalten. Adobe empfiehlt, die geänderten Workflow-Modelle zu kopieren, bevor Sie sie bearbeiten. Kopieren Sie beispielsweise den OOTB [!UICONTROL DAM-Update-Asset] -Modell vor der Bearbeitung des FFmpeg-Transkodierungsschritts im [!UICONTROL DAM-Update-Asset] -Modell, um Videoprofilnamen auszuwählen, die vor dem Upgrade vorhanden waren. Anschließend können Sie die `/apps` -Knoten, damit AEM die benutzerdefinierten Änderungen am OOTB-Modell abrufen kann.
