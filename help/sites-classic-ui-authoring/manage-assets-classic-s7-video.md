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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Video{#video}

Assets bieten eine zentralisierte Verwaltung von Video-Assets, mit der Sie Videos direkt in Assets hochladen können, um sie automatisch für Dynamic Media Classic zu kodieren, und mit denen Sie direkt aus Assets zum Erstellen von Seiten auf Dynamic Media Classic-Videos zugreifen können.

Durch die Integration von Videos aus Dynamic Media Classic wird die Reichweite optimierter Videos auf alle Bildschirme (automatische Geräte- und Bandbreitenerkennung) erweitert.

* Die Videokomponente &quot;Dynamic Media Classic&quot;(Scene7) führt automatisch eine Geräte- und Bandbreitenerkennung durch, um das richtige Format und die richtige Videoqualität auf Desktop-, Tablet- und Mobilgeräten wiederzugeben.
* Assets – Sie können adaptive Videosets statt einzelner Video-Assets verwenden. Ein adaptives Videoset ist ein Container für alle Videoausgabeformate, die zur nahtlosen Wiedergabe von Videos auf verschiedenen Bildschirmen erforderlich sind. Es umfasst Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert wurden, wie 400 kBit/s, 800 kBit/s und 1000 kBit/s. Ein adaptives Videoset wird zusammen mit der S7-Videokomponente für adaptives Videostreaming auf mehreren Bildschirmen verwendet, einschließlich Desktopgeräten und iOS-, Android-, Blackberry- und Windows-Mobilgeräten. Weitere Informationen finden Sie in der [Scene7-Dokumentation zu adaptiven Videosets](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html).

## Info zu FFMPEG und Dynamic Media Classic {#about-ffmpeg-and-scene}

Die Grundlage des standardmäßigen Videokodierungsprozesses ist die Verwendung der FFMPEG-basierten Integration mit Videoprofilen. Aus diesem Grund enthält der Standard-Update-Asset-Workflow von DAM die folgenden ffmpeg-basierten Workflow-Schritte:

* FFMPEG-Miniaturen
* FFMPEG-Kodierung

Beachten Sie, dass beim Aktivieren und Konfigurieren der Dynamic Media Classic-Integration diese beiden Workflow-Schritte nicht automatisch aus dem vordefinierten DAM Update Asset-Erfassungsarbeitsablauf entfernt oder deaktiviert werden. Wenn Sie die FFMPEG-basierte Videokodierung in AEM bereits nutzen, ist es wahrscheinlich, dass FFMPEG in Ihren Erstellungsumgebungen bereits installiert ist. In diesem Fall wird ein neues Video, das mit Assets erfasst wird, zweimal kodiert: Einmal vom FFMPEG-Encoder und einmal von der Integration von Dynamic Media Classic.

Wenn Sie die FFMPEG-basierte Videokodierung in AEM konfiguriert und FFMPEG installiert haben, empfiehlt Adobe, die beiden FFMPEG-Workflows aus Ihren DAM-Update-Asset-Workflows zu entfernen.

### Unterstützte Formate {#supported-formats}

Die folgenden Formate werden für die Komponente &quot;Dynamic Media Classic Video&quot;unterstützt:

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
1. Autor mit Dynamic Media Classic-Video- oder Foundation-Videokomponente.

#### Wenn Sie Ihr Video auf Dynamic Media Classic hochladen {#if-you-are-uploading-your-video-to-scene}

Wenn Sie keinen Workflow oder keine Versionierung für Ihre Assets benötigen, sollten Sie Ihre Assets in Dynamic Media Classic hochladen. Der folgende Workflow wird empfohlen:

1. Richten Sie in Dynamic Media Classic einen geplanten FTP-Upload- und -Kodierungsvorgang auf Dynamic Media Classic (systemautomatisiert)[](https://help.adobe.com/en_US/scene7/using/WS70B173EC-4CAD-4b4c-BF9C-43A11F3A5950.html)ein.
1. In AEM, access video assets in WCM in the **[!UICONTROL Dynamic Media Classic]** tab of the Content Finder.
1. Erstellen Sie mit der Videokomponente &quot;Dynamic Media Classic&quot;.

### Konfigurieren der Integration mit dem Video &quot;Dynamic Media Classic&quot; {#configuring-integration-with-scene-video}

**So konfigurieren Sie universelle Vorlagen**:

1. In **[!UICONTROL Cloud Services]**, navigate to your **[!UICONTROL Dynamic Media Classic]** configuration and click **[!UICONTROL Edit]**.
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

1. Die ausgewählten Kodierungsprofile werden automatisch auf alle Videos angewendet, die in den CQ DAM-Zielordner hochgeladen wurden, den Sie für diese Konfiguration der Dynamic Media Classic-Cloud eingerichtet haben. Sie können mehrere Dynamic Media Classic-Cloud-Konfigurationen mit unterschiedlichen Zielordnern einrichten, um bei Bedarf unterschiedliche Kodierungsprofile anzuwenden.

### Aktualisieren von Viewer- und Kodierungsvorlagen {#updating-viewer-and-encoding-presets}

If you need to update the viewer and encoding presets for video in AEM because the presets have been updated in Dynamic Media Classic, navigate to the Dynamic Media Classic configuration in the cloud configuration and click **Update the viewer and encoding presets**.

![chlimage_1-131](assets/chlimage_1-131.png)

### Hochladen Ihres Mastervideos {#uploading-your-master-video}

So laden Sie Ihr Mastervideo von Adobe DAM in Dynamic Media Classic hoch:

1. Navigieren Sie zum CQ DAM-Zielordner, in dem Sie Ihre Cloud-Konfiguration mit dynamischen Media Classic-Kodierungsprofilen eingerichtet haben.
1. Klicken Sie auf **[!UICONTROL Hochladen]**, um das Mastervideo hochzuladen. Video uploading and encoding is complete after the [!UICONTROL DAM Update Asset] workflow is complete and **[!UICONTROL Publish to Dynamic Media Classic]** has a checkmark.

   >[!NOTE]
   >
   >Es kann etwas Zeit in Anspruch nehmen, bis die Videominiaturen erstellt wurden.

   Dragging the DAM master video on to the video component accesses *all* of the Dynamic Media Classic encoded proxy renditions for delivery.

### Video-Komponente für Foundation und Classic-Komponente für dynamische Medien {#foundation-video-component-versus-scene-video-component}

Bei Verwendung von AEM haben Sie Zugriff sowohl auf die Videokomponente, die in Sites verfügbar ist, als auch auf die Videokomponente von Dynamic Media Classic (Scene7). Diese Komponenten sind nicht austauschbar.

Die Videokomponente &quot;Dynamic Media Classic&quot;funktioniert nur bei Videos mit Dynamic Media Classic. Die Stiftungskomponente funktioniert mit Videos, die in AEM (mithilfe von ffmpeg) und Dynamic Media Classic-Videos gespeichert wurden.

Die folgende Matrix verdeutlicht, wann Sie welche Komponente nutzen sollten:

![chlimage_1-132](assets/chlimage_1-132.png)

>[!NOTE]
>
>Standardmäßig verwendet die Komponente &quot;Dynamic Media Classic&quot;das universelle Videoprofil. Sie können jedoch den HTML5-basierten Videoplayer für die Verwendung durch AEM abrufen. Kopieren Sie in Dynamic Media Classic den Einbettungscode des standardmäßigen HTML5-Videoplayers und fügen Sie ihn auf Ihre AEM-Seite ein.


## AEM-Videokomponente {#aem-video-component}

Auch wenn die Verwendung der Videokomponente &quot;Dynamic Media Classic&quot;für die Anzeige von Videos aus Dynamic Media Classic empfohlen wird, wird in diesem Abschnitt beschrieben, wie Sie Videos aus Gründen der Vollständigkeit mit der [!UICONTROL Foundation-Videokomponente] in AEM verwenden.

### Vergleich von AEM Video- und Dynamic Media Classic-Videos {#aem-video-and-scene-video-comparison}

In der folgenden Tabelle finden Sie einen Vergleich der unterstützen Funktionen der AEM-Foundation-Videokomponente und der Scene7-Videokomponente:

|  | AEM Foundation Video | Dynamisches Medienklassisches Video |
|---|---|---|
| Ansatz | HTML5 hat Priorität. Flash dient nur zum Ausweichen bei Nicht-HTML5-Inhalten. | Flash auf den meisten Desktopgeräten HTML5 kommt auf Mobilgeräten und Tablets zum Einsatz. |
| Bereitstellung | Progressiv | Adaptives Streaming |
| Nachverfolgung | Ja | Ja |
| Erweiterbarkeit | Ja | Ja (mit dem Dynamischen Media Classic Viewer-SDK) |
| Mobile Videos | Ja | Ja |

### Einrichtung {#setting-up}

#### Erstellen von Videoprofilen {#creating-video-profiles}

Die verschiedenen Videokodierungen werden entsprechend den Kodierungsvorgaben für dynamische Medien Classic erstellt, die in der Cloud-Konfiguration für dynamische Medien Classic ausgewählt wurden. Damit die zugrunde liegende Videokomponente diese verwenden kann, muss für jede ausgewählte Kodierungsvorgabe für Dynamic Media Classic ein Videoprofil erstellt werden. Damit kann die Videokomponente die DAM-Ausgabeformate entsprechend auswählen.

>[!NOTE]
>
>Neue Videoprofile und Änderungen daran müssen für eine Veröffentlichung aktiviert werden.

1. Starten Sie AEM, gehen Sie zu **[!UICONTROL Tools]** und wählen Sie **[!UICONTROL Konfigurationskonsole]** aus. In the Configuration Console navigate to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Profiles]** in the navigation tree.
1. Erstellen Sie ein neues Videoprofil für Dynamic Media Classic. **[!UICONTROL In der]** Neuen... wählen Sie &quot;Seite **[!UICONTROL erstellen]** &quot;und dann die Vorlage &quot;Dynamisches Medienklassisches Videoprofil&quot;. Geben Sie der neuen Videoprofilseite einen Namen und klicken Sie auf **[!UICONTROL Erstellen]**.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Bearbeiten Sie das neue Videoprofil. Wählen Sie zuerst die Cloud-Konfiguration aus. Wählen Sie anschließend dieselbe Kodierungsvorlage aus, die Sie bereits in der Cloud-Konfiguration ausgewählt haben.

   ![chlimage_1-134](assets/chlimage_1-134.png)

   | Eigenschaft | Beschreibung |
   |---|---|
   | Konfiguration von Dynamic Media Classic (Scene7) Cloud | Die Cloud-Konfiguration, die für die Kodierungsvorlagen verwendet werden soll |
   | Kodierungsvorgabe für dynamische Medien Classic (Scene7) | Die Kodierungsvorlage, die diesem Videoprofil zugeordnet werden soll |
   | HTML5-Videotyp | Diese Eigenschaft ermöglicht, den Wert der Typeigenschaft des HTML5-Videoquellelements festzulegen. Diese Informationen werden nicht von den Kodierungsvorgaben für Dynamic Media Classic bereitgestellt, sondern sind für die ordnungsgemäße Wiedergabe der Videos mit dem HTML5-Videoelement erforderlich. Eine Liste für gängige Formate wird bereitgestellt, kann jedoch für andere Formate überschrieben werden. |

   Wiederholen Sie diesen Schritt für alle in der Cloud-Konfiguration ausgewählten Kodierungsvorlagen, die Sie in der Videokomponente verwenden möchten.

#### Konfigurieren des Designs {#configuring-design}

Die Foundation-Videokomponente muss darüber informiert sein, welche Videoprofile verwendet werden sollen, damit sie die Videoquellenliste erstellen kann. Öffnen Sie den Designdialog der Videokomponenten und konfigurieren Sie das Design der Komponenten für die Nutzung der neuen Videoprofile.

>[!NOTE]
>
>Wenn Sie die Foundation-Videokomponente auf einer Mobilseite verwenden, müssen Sie diese Schritte für das Design der Mobilseite möglicherweise wiederholen.

>[!NOTE]
>
>Bei Änderungen am Design ist eine Aktivierung des Designs erforderlich, damit sie für die Veröffentlichung übernommen wird.

1. Öffnen Sie den Designdialog der Foundation-Videokomponente und wechseln Sie auf die Registerkarte **[!UICONTROL Profile]**. Löschen Sie dann die vordefinierten Profile und fügen Sie die neuen Videoprofile für Dynamic Media Classic hinzu. Die Reihenfolge der Profilliste im Designdialogfeld definiert auch die Reihenfolge des Videoquellen-Elements beim Rendern.
1. Bei Browsern, die kein HTML5 unterstützen, ermöglicht die Videokomponente ein Ausweichen auf Flash. Öffnen Sie den Designdialog der Videokomponenten und wechseln Sie auf die Registerkarte **[!UICONTROL Flash]**. Konfigurieren Sie die Einstellungen des Flash-Players und ordnen Sie ein Ersatzprofil für den Flash-Player zu.

#### Checkliste {#checklist}

1. Erstellen Sie eine Cloud-Konfiguration für Dynamic Media Classic (Scene7). Vergewissern Sie sich, dass die Videokodierungsvorlagen festgelegt sind und das Importprogramm ausgeführt wird.
1. Erstellen Sie für jede in der Cloud-Konfiguration ausgewählte Videokodierungsvorgabe ein Videoprofil für Dynamic Media Classic.
1. Die Videoprofile müssen aktiviert sein.
1. Konfigurieren Sie das Design der Foundation-Videokomponente auf Ihrer Seite.
1. Aktivieren Sie das Design, nachdem Sie mit Ihren Designänderungen fertig sind.

