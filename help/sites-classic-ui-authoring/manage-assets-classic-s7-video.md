---
title: Video
seo-title: Video
description: Assets bietet zentralisierte Video-Asset-Verwaltung, mit der Sie Videos direkt in Assets zur automatischen Kodierung in Scene7 hochladen und für die Seitenerstellung direkt in Assets auf Scene7-Videos zugreifen können.
seo-description: Assets bietet zentralisierte Video-Asset-Verwaltung, mit der Sie Videos direkt in Assets zur automatischen Kodierung in Scene7 hochladen und für die Seitenerstellung direkt in Assets auf Scene7-Videos zugreifen können.
uuid: 46da7a0d-d17b-4716-a304-ce5496421b5a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dfaa4b3f-f65a-4fe3-87a7-f3bc71015e56
translation-type: tm+mt
source-git-commit: e916f70549197ac9f95443e972401a78735b0560
workflow-type: tm+mt
source-wordcount: '1741'
ht-degree: 46%

---


# Video{#video}

Assets bieten eine zentralisierte Verwaltung von Video-Assets, bei der Sie Videos direkt in Assets hochladen können, um sie automatisch in Dynamic Media Classic zu kodieren, und auf Dynamic Media Classic-Videos direkt aus Assets zum Erstellen von Seiten zugreifen können.

Die Videointegration von Dynamic Media Classic erweitert die Reichweite optimierter Videos auf alle Bildschirme (automatische Geräte- und Bandbreitenerkennung).

* Die Videokomponente Dynamic Media Classic (Scene7) führt automatisch die Geräte- und Bandbreitenerkennung durch, um das richtige Format und die richtige Videoqualität auf Desktop-, Tablet- und Mobilgeräten wiederzugeben.
* Assets – Sie können adaptive Videosets statt einzelner Video-Assets verwenden. Ein adaptives Videoset ist ein Container für alle Videoausgabeformate, die zur nahtlosen Wiedergabe von Videos auf verschiedenen Bildschirmen erforderlich sind. Es umfasst Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert wurden, wie 400 kBit/s, 800 kBit/s und 1000 kBit/s. Ein adaptives Videoset wird zusammen mit der S7-Videokomponente für adaptives Videostreaming auf mehreren Bildschirmen verwendet, einschließlich Desktopgeräten und iOS-, Android-, Blackberry- und Windows-Mobilgeräten. Weitere Informationen finden Sie in der [Scene7-Dokumentation zu adaptiven Videosets](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html).

## Info zu FFMPEG und Dynamic Media Classic {#about-ffmpeg-and-scene}

Die Grundlage des standardmäßigen Videokodierungsprozesses ist die Verwendung der FFMPEG-basierten Integration mit Videoprofilen. Therefore, the out-of-the-box [!UICONTROL DAM Update Asset] workflow contains the following two ffmpeg-based workflow steps:

* FFMPEG-Miniaturen
* FFMPEG-Kodierung

Be aware that enabling and configuring the Dynamic Media Classic integration does not automatically remove or deactivate these two workflow steps from the out-of-the-box [!UICONTROL DAM Update Asset] ingestion workflow. Wenn Sie die FFMPEG-basierte Videokodierung in AEM bereits nutzen, ist es wahrscheinlich, dass FFMPEG in Ihren Erstellungsumgebungen bereits installiert ist. In diesem Fall wird ein neues Video, das mit Assets erfasst wird, zweimal kodiert: Einmal vom FFMPEG-Encoder und einmal von der Dynamic Media Classic-Integration.

If you have the FFMPEG-based video encoding in AEM configured and FFMPEG installed, Adobe recommends that you remove the two FFMPEG workflows from your [!UICONTROL DAM Update Asset] workflows.

### Unterstützte Formate {#supported-formats}

Die folgenden Formate werden für die Videokomponente Dynamic Media Classic unterstützt:

* F4V H.264
* H.264 (.mp4)

### Festlegen eines Speicherorts für hochgeladene Videos {#deciding-where-to-upload-your-video}

Der Speicherort für hochgeladene Videos hängt von folgenden Faktoren ab:

* Benötigen Sie für das Video-Asset einen Workflow?
* Benötigen Sie für das Video-Asset eine Versionskontrolle?

Falls Sie eine der Fragen mit „ja“ beantworten können, laden Sie Ihr Video direkt in Adobe DAM hoch. Wenn beide Fragen mit &quot;Nein&quot;beantwortet werden, laden Sie Ihr Video direkt in Dynamic Media Classic hoch. Der Workflow für die einzelnen Szenarien wird im folgenden Abschnitt beschrieben.

#### Wenn Sie Ihr Video direkt in Adobe Assets hochladen {#if-you-are-uploading-your-video-directly-to-adobe-assets}

Wenn Sie einen Workflow oder eine Versionierung für Ihre Assets benötigen, sollten Sie sie zuerst in Adobe Assets hochladen. Der folgende Workflow wird empfohlen:

1. Laden Sie das Video-Asset in Adobe Assets hoch und kodieren und veröffentlichen Sie es automatisch in Dynamic Media Classic.
1. Öffnen Sie AEM und greifen Sie in WCM auf der Registerkarte **[!UICONTROL Filme]** des Content Finders auf Video-Assets zu.
1. Autor mit Dynamic Media Classic Video- oder Foundation-Videokomponente.

#### Wenn Sie Ihr Video auf Dynamic Media Classic hochladen {#if-you-are-uploading-your-video-to-scene}

Wenn Sie keinen Workflow oder keine Versionierung für Ihre Assets benötigen, sollten Sie Ihre Assets in Dynamic Media Classic hochladen. Der folgende Workflow wird empfohlen:

1. Richten Sie in Dynamic Media Classic einen geplanten FTP-Upload und eine geplante FTP-Kodierung auf Dynamic Media Classic (systemautomatisiert) [](https://help.adobe.com/en_US/scene7/using/WS70B173EC-4CAD-4b4c-BF9C-43A11F3A5950.html)ein.
1. In AEM, access video assets in WCM in the **[!UICONTROL Dynamic Media Classic]** tab of the Content Finder.
1. Erstellen Sie mit der Videokomponente &quot;Dynamic Media Classic&quot;.

### Konfigurieren der Integration mit Dynamic Media Classic Video {#configuring-integration-with-scene-video}

**So konfigurieren Sie universelle Vorlagen**:

1. In **[!UICONTROL Cloud Services]**, navigate to your **[!UICONTROL Dynamic Media Classic]** configuration and click **[!UICONTROL Edit.]**
1. Wählen Sie die Registerkarte **[!UICONTROL Video]** aus.

   >[!NOTE]
   >
   >Die Registerkarte **[!UICONTROL Video]** wird nicht angezeigt, wenn die Seite keine Cloud-Konfiguration hat. Siehe [Aktivieren von Dynamic Media Classic für WCM](#enablingscene7forwcm).

1. Wählen Sie das Profil für adaptive Videokodierung, ein Standardprofil für die Kodierung einzelner Videos, oder ein benutzerdefiniertes Videokodierungsprofil aus.

   >[!NOTE]
   >
   >For more information about what the video presets mean, see the [Dynamic Media Classic documentation](https://help.adobe.com/en_US/scene7/using/WSE86ACF2B-BD50-4c48-A1D7-9CD4405B62D0.html).
   >
   >Adobe empfiehlt, entweder beide adaptive Videosets bei der Konfiguration der universellen Vorlagen oder die Option **[!UICONTROL Adaptive Videokodierung]** auszuwählen.

1. Die ausgewählten Kodierungs-Profil werden automatisch auf alle Videos angewendet, die in den Ordner &quot;CQ DAM-Zielgruppe&quot;hochgeladen wurden, den Sie für diese Dynamic Media Classic Cloud-Konfiguration eingerichtet haben. Sie können mehrere Dynamic Media Classic-Cloud-Konfigurationen mit unterschiedlichen Zielgruppen-Ordnern einrichten, um bei Bedarf verschiedene Kodierungs-Profil anzuwenden.

### Aktualisieren von Viewer- und Kodierungsvorlagen {#updating-viewer-and-encoding-presets}

If you need to update the viewer and encoding presets for video in AEM because the presets have been updated in Dynamic Media Classic, navigate to the Dynamic Media Classic configuration in the cloud configuration and click **Update the viewer and encoding presets**.

![chlimage_1-131](assets/chlimage_1-131.png)

### Hochladen des primären Quellvideos {#uploading-your-master-video}

So laden Sie Ihr primäres Quellvideo von Adobe DAM in Dynamic Media Classic hoch:

1. Navigieren Sie zum Ordner &quot;CQ DAM-Zielgruppe&quot;, in dem Sie Ihre Cloud-Konfiguration mit Dynamic Media Classic-Kodierungs-Profilen eingerichtet haben.
1. Klicken Sie auf **[!UICONTROL Hochladen]** , um das primäre Quellvideo hochzuladen. Video uploading and encoding is complete after the [!UICONTROL DAM Update Asset] workflow is complete and **[!UICONTROL Publish to Dynamic Media Classic]** has a checkmark.

   >[!NOTE]
   >
   >Es kann etwas Zeit in Anspruch nehmen, bis die Videominiaturen erstellt wurden.

   Dragging the DAM primary source video on to the video component accesses *all* of the Dynamic Media Classic encoded proxy renditions for delivery.

### Foundation-Videokomponente im Vergleich zu Dynamic Media Classic-Videokomponente {#foundation-video-component-versus-scene-video-component}

Bei Verwendung von AEM haben Sie Zugriff sowohl auf die Videokomponente, die in Sites verfügbar ist, als auch auf die Videokomponente Dynamic Media Classic (Scene7). Diese Komponenten sind nicht austauschbar.

Die Videokomponente &quot;Dynamic Media Classic&quot;funktioniert nur bei Dynamic Media Classic-Videos. Die Stiftungskomponente funktioniert mit Videos, die in AEM (mithilfe von ffmpeg) und Dynamic Media Classic-Videos gespeichert wurden.

Die folgende Matrix verdeutlicht, wann Sie welche Komponente nutzen sollten:

![chlimage_1-132](assets/chlimage_1-132.png)

>[!NOTE]
>
>Standardmäßig verwendet die Videokomponente Dynamic Media Classic das universelle Profil. Sie können jedoch den HTML5-basierten Videoplayer für die Verwendung durch AEM abrufen. Kopieren Sie in Dynamic Media Classic den Einbettungscode des standardmäßigen HTML5-Videoplayers und fügen Sie ihn auf Ihre AEM-Seite ein.


## AEM-Videokomponente {#aem-video-component}

Auch wenn die Verwendung der Videokomponente &quot;Dynamic Media Classic&quot;für die Anzeige von Dynamic Media Classic-Videos empfohlen wird, wird in diesem Abschnitt beschrieben, wie Dynamic Media Classic-Videos mit der [!UICONTROL Foundation-Videokomponente] in AEM verwendet werden, um die Vollständigkeit zu gewährleisten.

### Vergleich von AEM-Videos und Dynamic Media mit klassischen Videos {#aem-video-and-scene-video-comparison}

In der folgenden Tabelle finden Sie einen Vergleich der unterstützen Funktionen der AEM-Foundation-Videokomponente und der Scene7-Videokomponente:

|  | AEM Foundation Video | Dynamic Media Classic Video |
|---|---|---|
| Ansatz | HTML5 hat Priorität. Flash dient nur zum Ausweichen bei Nicht-HTML5-Inhalten. | Flash auf den meisten Desktopgeräten HTML5 kommt auf Mobilgeräten und Tablets zum Einsatz. |
| Bereitstellung | Progressiv | Adaptives Streaming |
| Nachverfolgung | Ja | Ja |
| Erweiterbarkeit | Ja | Ja (mit Dynamic Media Classic Viewer-SDK) |
| Mobile Videos | Ja | Ja |

### Einrichtung {#setting-up}

#### Erstellen von Videoprofilen {#creating-video-profiles}

Die verschiedenen Videokodierungen werden entsprechend den in der Cloud-Konfiguration von Dynamic Media Classic ausgewählten Dynamic Media Classic-Kodierungsvorgaben erstellt. Damit die zugrunde liegende Videokomponente diese verwenden kann, muss für jede ausgewählte Dynamic Media Classic-Kodierungsvorgabe ein Profil erstellt werden. Damit kann die Videokomponente die DAM-Ausgabeformate entsprechend auswählen.

>[!NOTE]
>
>Neue Videoprofile und Änderungen daran müssen für eine Veröffentlichung aktiviert werden.

1. Starten Sie AEM, gehen Sie zu **[!UICONTROL Tools]** und wählen Sie **[!UICONTROL Konfigurationskonsole aus.]** Navigieren Sie in der Konfigurationskonsole zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video-Profil]** in der Navigationsstruktur.
1. Erstellen Sie ein neues Dynamic Media Classic Video-Profil. In the **[!UICONTROL New...]** menu, select **[!UICONTROL Create Page]** and then select the Dynamic Media Classic Video Profile template. Geben Sie der neuen Videoprofilseite einen Namen und klicken Sie auf **[!UICONTROL Erstellen.]**

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Bearbeiten Sie das neue Videoprofil. Wählen Sie zuerst die Cloud-Konfiguration aus. Wählen Sie anschließend dieselbe Kodierungsvorlage aus, die Sie bereits in der Cloud-Konfiguration ausgewählt haben.

   ![chlimage_1-134](assets/chlimage_1-134.png)

   | Eigenschaft | Beschreibung |
   |---|---|
   | Dynamic Media Classic (Scene7) Cloud-Konfiguration | Die Cloud-Konfiguration, die für die Kodierungsvorlagen verwendet werden soll |
   | Kodierungsvorgabe &quot;Dynamic Media Classic&quot;(Scene7) | Die Kodierungsvorlage, die diesem Videoprofil zugeordnet werden soll |
   | HTML5-Videotyp | Diese Eigenschaft ermöglicht, den Wert der Typeigenschaft des HTML5-Videoquellelements festzulegen. Diese Informationen werden nicht von den Dynamic Media Classic-Kodierungsvorgaben bereitgestellt, sondern sind für die ordnungsgemäße Wiedergabe der Videos mit dem HTML5-Videoelement erforderlich. Eine Liste für gängige Formate wird bereitgestellt, kann jedoch für andere Formate überschrieben werden. |

   Wiederholen Sie diesen Schritt für alle in der Cloud-Konfiguration ausgewählten Kodierungsvorlagen, die Sie in der Videokomponente verwenden möchten.

#### Konfigurieren des Designs {#configuring-design}

Die Foundation-Videokomponente muss darüber informiert sein, welche Videoprofile verwendet werden sollen, damit sie die Videoquellenliste erstellen kann. Öffnen Sie den Designdialog der Videokomponenten und konfigurieren Sie das Design der Komponenten für die Nutzung der neuen Videoprofile.

>[!NOTE]
>
>Wenn Sie die Foundation-Videokomponente auf einer Mobilseite verwenden, müssen Sie diese Schritte für das Design der Mobilseite möglicherweise wiederholen.

>[!NOTE]
>
>Bei Änderungen am Design ist eine Aktivierung des Designs erforderlich, damit sie für die Veröffentlichung übernommen wird.

1. Öffnen Sie den Designdialog der Foundation-Videokomponente und wechseln Sie auf die Registerkarte **[!UICONTROL Profile]**. Löschen Sie dann die vordefinierten Profil und fügen Sie die neuen Dynamic Media Classic-Video-Profil hinzu. Die Reihenfolge der Profil-Liste im Designdialogfeld definiert auch die Reihenfolge des Videoquellen-Elements beim Rendern.
1. Bei Browsern, die kein HTML5 unterstützen, ermöglicht die Videokomponente ein Ausweichen auf Flash. Öffnen Sie den Designdialog der Videokomponenten und wechseln Sie auf die Registerkarte **[!UICONTROL Flash]**. Konfigurieren Sie die Einstellungen des Flash-Players und ordnen Sie ein Ersatzprofil für den Flash-Player zu.

#### Checkliste {#checklist}

1. Erstellen Sie eine Cloud-Konfiguration für Dynamic Media Classic (Scene7). Vergewissern Sie sich, dass die Videokodierungsvorlagen festgelegt sind und das Importprogramm ausgeführt wird.
1. Erstellen Sie für jede in der Cloud-Konfiguration ausgewählte Videokodierungsvorgabe ein Dynamic Media Classic-Profil.
1. Die Videoprofile müssen aktiviert sein.
1. Konfigurieren Sie das Design der Foundation-Videokomponente auf Ihrer Seite.
1. Aktivieren Sie das Design, nachdem Sie mit Ihren Designänderungen fertig sind.

