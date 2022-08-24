---
title: 'Video   '
description: Erfahren Sie mehr über die zentrale Verwaltung von Video-Assets in Adobe Experience Manager Assets, wo Sie Videos zur automatischen Kodierung in Dynamic Media Classic hochladen und direkt von Experience Manager Assets aus auf Dynamic Media Classic-Videos zugreifen können. Die Dynamic Media Classic-Videointegration erweitert die Reichweite optimierter Videos auf alle Bildschirme.
uuid: 8b3423f1-d96b-44d9-bdb7-e3b77875b25d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
discoiquuid: 2685f9f3-0973-40a9-89b8-e7db0a6a75f2
role: User, Admin
mini-toc-levels: 3
exl-id: 56009925-1a36-48b5-b96c-ec2e468da106
feature: Video
source-git-commit: 77687a0674b939460bd34011ee1b94bd4db50ba4
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 36%

---

# Video    {#video}

Adobe Experience Manager Assets bietet eine zentralisierte Video-Asset-Verwaltung, mit der Sie Videos direkt in Assets hochladen können, um sie automatisch in Dynamic Media Classic zu kodieren, und über Assets direkt auf Dynamic Media Classic-Videos zugreifen können, um sie zu erstellen.

Die Dynamic Media Classic-Videointegration erweitert die Reichweite optimierter Videos auf alle Bildschirme (automatische Geräte- und Bandbreitenerkennung).

* Die **[!UICONTROL Scene7-Video]** -Komponente führt automatisch eine Geräte- und Bandbreitenerkennung durch, um das richtige Format und die richtige Qualität von Videos auf Desktop-, Tablet- und Mobilgeräten wiederzugeben.
* Assets – Sie können adaptive Videosets statt einzelner Video-Assets verwenden. Ein adaptives Videoset enthält alle Videoausgabedarstellungen, die für die nahtlose Wiedergabe des Videos auf mehreren Bildschirmen erforderlich sind. Es umfasst Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert wurden, wie 400 kBit/s, 800 kBit/s und 1000 kBit/s. Sie verwenden ein adaptives Videoset zusammen mit der S7-Videokomponente für adaptives Video-Streaming auf mehreren Bildschirmen, einschließlich Desktop-, iOS-, Android™-, BlackBerry®- und Windows-Mobilgeräten.
<!-- See [Scene7 documentation about adaptive video sets for more information](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html). -->

## Über FFMPEG und Dynamic Media Classic {#about-ffmpeg-and-scene}

Die Grundlage des standardmäßigen Videokodierungsprozesses ist die Verwendung der FFMPEG-basierten Integration mit Videoprofilen. Aus diesem Grund enthält der Standard-Aufnahme-Workflow von DAM die folgenden ffmpeg-basierten Workflow-Schritte:

* FFMPEG-Miniaturen
* FFMPEG-Kodierung

Durch die Aktivierung und Konfiguration der Dynamic Media Classic-Integration werden diese beiden Workflow-Schritte nicht automatisch aus dem vordefinierten Workflow zur DAM-Erfassung entfernt oder deaktiviert. Wenn Sie bereits die FFMPEG-basierte Videokodierung in Adobe Experience Manager verwenden, ist es wahrscheinlich, dass FFMPEG in Ihren Authoring-Umgebungen installiert ist. In diesem Fall wird ein neues Video, das mit DAM erfasst wird, zweimal kodiert: einmal vom FFMPEG-Kodierer und einmal von der Dynamic Media Classic-Integration.

Wenn Sie die FFMPEG-basierte Videokodierung in Experience Manager konfiguriert und FFMPEG installiert haben, empfiehlt Adobe, die beiden FFMPEG-Workflows aus Ihren DAM-Aufnahme-Workflows zu entfernen.

## Unterstützte Formate {#supported-formats}

Die folgenden Formate werden für die Scene7-Videokomponente unterstützt:

* F4V H.264
* H.264 (.mp4)

## Festlegen, wo das Video hochgeladen werden soll {#deciding-where-to-upload-your-video}

Der Speicherort für hochgeladene Videos hängt von folgenden Faktoren ab:

* Benötigen Sie für das Video-Asset einen Workflow?
* Benötigen Sie für das Video-Asset eine Versionskontrolle?

Falls Sie eine der Fragen mit „ja“ beantworten können, laden Sie Ihr Video direkt in Adobe DAM hoch. Wenn die Antwort auf beide Fragen &quot;Nein&quot;lautet, laden Sie Ihr Video direkt in Dynamic Media Classic hoch. Der Workflow für die einzelnen Szenarien wird im folgenden Abschnitt beschrieben.

### Wenn Sie Ihr Video direkt in Adobe DAM hochladen {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Wenn Sie einen Workflow oder eine Versionierung für Ihre Assets benötigen, laden Sie zuerst in Adobe DAM hoch. Der folgende Workflow wird empfohlen:

1. Laden Sie das Video-Asset in Adobe DAM hoch und kodieren und veröffentlichen Sie es automatisch in Dynamic Media Classic.
1. Greifen Sie in Experience Manager auf Video-Assets in WCM im **[!UICONTROL Filme]** im Content Finder.
1. Autor mit **[!UICONTROL Scene7-Video]** oder **[!UICONTROL Foundation-Video]** -Komponente.

### Wenn Sie Ihr Video in Dynamic Media Classic hochladen {#if-you-are-uploading-your-video-to-scene}

Wenn Sie keinen Workflow oder keine Versionierung für Ihre Assets benötigen, laden Sie Ihre Assets in Scene7 hoch. Der folgende Workflow wird empfohlen:

1. In Dynamic Media Classic [Geplantes Hochladen und Kodieren von FTP-Servern in Scene7 einrichten (System automatisiert)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#upload-files-using-via-ftp).
1. Greifen Sie in Experience Manager auf Video-Assets in WCM im **[!UICONTROL Scene7]** im Content Finder.
1. Autor mit der **[!UICONTROL Scene7-Video]** -Komponente.

## Integration mit Scene7 konfigurieren - Video {#configuring-integration-with-scene-video}

1. In **[!UICONTROL Cloud Services]**, navigieren Sie zu Ihrer **[!UICONTROL Scene7]** Konfiguration und Auswahl **[!UICONTROL Bearbeiten]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Video]** aus.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >Die Registerkarte **[!UICONTROL Video]** wird nicht angezeigt, wenn die Seite keine Cloud-Konfiguration hat.

1. Wählen Sie das Profil für adaptive Videokodierung, ein Standardprofil für die Kodierung einzelner Videos, oder ein benutzerdefiniertes Videokodierungsprofil aus.

   >[!NOTE]
   >
   >Weitere Informationen dazu, was die Videovorgaben bedeuten, finden Sie unter [Dynamic Media Classic-Dokumentation](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe empfiehlt, entweder beide adaptive Videosets bei der Konfiguration der universellen Vorlagen oder die Option **[!UICONTROL Adaptive Videokodierung]** auszuwählen.

1. Die ausgewählten Kodierungsprofile werden automatisch auf alle Videos angewendet, die in den CQ DAM-Zielordner, den Sie für diese Scene7-Cloud-Konfiguration einrichten, hochgeladen werden. Sie können mehrere Scene7-Cloud-Konfigurationen mit verschiedenen Zielordnern einrichten, um nach Bedarf verschiedene Kodierungsprofile anzuwenden.

## Viewer- und Kodierungsvorgaben aktualisieren {#updating-viewer-and-encoding-presets}

Um die Viewer- und Kodierungsvorgaben für Videos zu aktualisieren, weil die Vorgaben in Scene7 aktualisiert wurden, navigieren Sie zur Scene7-Konfiguration in der Cloud-Konfiguration und wählen Sie **[!UICONTROL Aktualisieren von Viewer- und Kodierungsvorgaben]**.

![chlimage_1-364](assets/chlimage_1-364.png)

## Hochladen des Primärvideos von Adobe DAM zu Scene7 {#uploading-your-master-video}

1. Navigieren Sie zum CQ DAM-Zielordner, in dem Sie Ihre Cloud-Konfiguration mit Scene7-Kodierungsprofilen eingerichtet haben.
1. Auswählen **[!UICONTROL Hochladen]** , um das Primärvideo hochzuladen. Hochladen und Kodieren von Videos sind nach dem [!UICONTROL DAM-Update-Asset] der Workflow abgeschlossen ist und **[!UICONTROL In Scene7 veröffentlichen]** hat ein Häkchen.

   >[!NOTE]
   >
   >Es dauert lange, bis die Videominiaturen generiert werden.

   Durch Ziehen des DAM-Primärvideos auf die Videokomponente wird auf zugegriffen. *all* Scene7-kodierte Proxy-Ausgabeformate für die Bereitstellung.

## Foundation-Videokomponente im Vergleich zur Scene7-Videokomponente {#foundation-video-component-versus-scene-video-component}

Bei Verwendung von Experience Manager haben Sie Zugriff auf die Videokomponente, die in Sites verfügbar ist, und auf die Scene7-Videokomponente. Diese Komponenten sind nicht austauschbar.

Die Scene7-Videokomponente funktioniert nur für Scene7-Videos. Die Foundation-Komponente funktioniert mit Videos, die aus Experience Manager (mithilfe von ffmpeg) und Scene7-Videos gespeichert werden.

In der folgenden Matrix wird erläutert, wann welche Komponente verwendet werden soll:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>Die S7-Videokomponente verwendet standardmäßig das universelle Videoprofil. Sie können jedoch den HTML5-basierten Videoplayer für die Verwendung durch Experience Manager abrufen. Kopieren Sie in Scene7 den Einbettungscode des vordefinierten HTML5-Videoplayers und fügen Sie ihn in Ihre Experience Manager-Seite ein.

## Experience Manager-Videokomponente {#aem-video-component}

Auch wenn die Verwendung der Scene7-Videokomponente für die Anzeige von Scene7-Videos empfohlen wird, wird in diesem Abschnitt beschrieben, wie Scene7-Videos mit der Foundation-Videokomponente in Experience Manager verwendet werden, um die Vollständigkeit zu gewährleisten.

### Vergleich von Experience Manager-Videos und Scene7-Videos {#aem-video-and-scene-video-comparison}

Die folgende Tabelle bietet einen allgemeinen Vergleich der unterstützten Funktionen zwischen der Experience Manager Foundation-Videokomponente und der Scene7-Videokomponente:

|  | Experience Manager Foundation-Video | Scene7 Video |
|---|---|---|
| Ansatz | HTML5 hat Priorität. Flash dient nur zum Ausweichen bei Nicht-HTML5-Inhalten. | Flash auf den meisten Desktopgeräten HTML5 kommt auf Mobilgeräten und Tablets zum Einsatz. |
| Bereitstellung | Progressiv | Adaptives Streaming |
| Nachverfolgung | Ja | Ja |
| Erweiterbarkeit | Ja | Nein |
| Mobile Videos | Ja | Ja |

### Setup {#setting-up}

#### Erstellen von Videoprofilen {#creating-video-profiles}

Die verschiedenen Videokodierungsmethoden werden anhand der S7-Kodierungsvorlagen erstellt, die in der S7-Cloud-Konfiguration ausgewählt werden. Damit die Foundation-Videokomponente sie verwendet, muss für jede ausgewählte S7-Kodierungsvorgabe ein Videoprofil erstellt werden. Diese Methode ermöglicht es der Videokomponente, die DAM-Ausgabeformate entsprechend auszuwählen.

>[!NOTE]
>
>Neue Videoprofile und Änderungen daran müssen für eine Veröffentlichung aktiviert werden.

1. Wählen Sie in Experience Manager **[!UICONTROL Instrumente]** > **[!UICONTROL Konfigurationskonsole]**.
1. Im **[!UICONTROL Konfigurationskonsole]**, navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL DAM]** > **[!UICONTROL Videoprofile]** in der Navigationsstruktur.
1. Erstellen Sie ein S7-Videoprofil. Im **[!UICONTROL Neu]**. Menü auswählen **[!UICONTROL Seite erstellen]** und wählen Sie dann die Vorlage Scene7-Videoprofil aus. Benennen Sie die neue Videoprofilseite und wählen Sie **[!UICONTROL Erstellen]**.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Bearbeiten Sie das neue Videoprofil. Wählen Sie zuerst die Cloud-Konfiguration aus. Wählen Sie anschließend dieselbe Kodierungsvorlage aus, die Sie bereits in der Cloud-Konfiguration ausgewählt haben.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Eigenschaft | Beschreibung |
   |---|---|
   | Scene7-Cloud-Konfiguration | Die Cloud-Konfiguration, die für die Kodierungsvorlagen verwendet werden soll |
   | Scene7-Kodierungsvorlage | Die Kodierungsvorlage, die diesem Videoprofil zugeordnet werden soll |
   | HTML5-Videotyp | Mit dieser Eigenschaft können Sie den Wert der Eigenschaft type des Videoquellenelements HTML5 festlegen. Diese Information wird nicht von den S7-Kodierungsvorlagen bereitgestellt, sie ist jedoch erforderlich, um die Videos anhand des HTML5-Videoelements richtig zu rendern. Eine Liste für gängige Formate wird bereitgestellt, kann jedoch für andere Formate überschrieben werden. |

   Wiederholen Sie diesen Schritt für alle in der Cloud-Konfiguration ausgewählten Kodierungsvorlagen, die Sie in der Videokomponente verwenden möchten.

#### Design konfigurieren {#configuring-design}

Die **[!UICONTROL Foundation-Video]** -Komponente muss wissen, welche Videoprofile zum Erstellen der Videoquellenliste verwendet werden sollen. Öffnen Sie das Dialogfeld &quot;Design&quot;der Videokomponenten und konfigurieren Sie das Komponentendesign für die Verwendung der neuen Videoprofile.

>[!NOTE]
>
>Wenn Sie **[!UICONTROL Foundation-Video]** -Komponente auf einer mobilen Seite verwenden, wiederholen Sie diese Schritte beim Design der mobilen Seite.

>[!NOTE]
>
>Bei Änderungen am Design ist eine Aktivierung des Designs erforderlich, damit sie für die Veröffentlichung übernommen wird.

1. Öffnen Sie die **[!UICONTROL Foundation-Video]** Dialogfeld &quot;Design&quot;der Komponente und ändern Sie zum **[!UICONTROL Profile]** Registerkarte. Löschen Sie dann die nativen Profile und fügen Sie die neuen S7-Videoprofile hinzu. Die Reihenfolge der Profilliste im Dialogfeld &quot;Design&quot;definiert die Reihenfolge des Videoquellenelements beim Rendern.
1. Bei Browsern, die HTML 5 nicht unterstützen, können Sie mit der Videokomponente einen Flash-Fallback konfigurieren. Öffnen Sie das Dialogfeld &quot;Design&quot;der Videokomponenten und ändern Sie zum **[!UICONTROL Flash]** Registerkarte. Konfigurieren Sie die Flash-Player-Einstellungen und weisen Sie dem Flash-Player ein Fallback-Profil zu.

#### Checkliste {#checklist}

1. Erstellen Sie eine S7-Cloud-Konfiguration. Stellen Sie sicher, dass die Vorgaben für die Videokodierung festgelegt sind und das Importtool ausgeführt wird.
1. Erstellen Sie ein S7-Videoprofil für jede in der Cloud-Konfiguration ausgewählte Videokodierungsvorlage.
1. Die Videoprofile müssen aktiviert sein.
1. Konfigurieren des Designs der **[!UICONTROL Foundation-Video]** -Komponente auf Ihrer Seite.
1. Aktivieren Sie das Design, nachdem Sie mit Ihren Designänderungen fertig sind.
