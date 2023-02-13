---
title: Video
seo-title: Video
description: Assets bietet zentralisierte Video-Asset-Verwaltung, mit der Sie Videos direkt in Assets zur automatischen Kodierung in Dynamic Media Classic hochladen und für die Seitenerstellung direkt in Assets auf Dynamic Media Classic-Videos zugreifen können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dfaa4b3f-f65a-4fe3-87a7-f3bc71015e56
exl-id: c540aa49-9981-4e8c-97df-972085b26490
source-git-commit: b5cf18d8e83786a23005aadf8aafe43d006a2e67
workflow-type: ht
source-wordcount: '1678'
ht-degree: 100%

---

# Video{#video}

Assets bietet zentralisierte Video-Asset-Verwaltung, mit der Sie Videos direkt in Assets zur automatischen Kodierung in Dynamic Media Classic hochladen und für die Seitenerstellung direkt in Assets auf Dynamic Media Classic-Videos zugreifen können.

Die Dynamic Media Classic-Videointegration erweitert die Reichweite optimierter Videos auf alle Bildschirme (automatische Geräteanpassung und Bandbreitenerkennung).

* Die Dynamic Media Classic-Videokomponente führt automatisch eine Geräte- und Bandbreitenerkennung durch, damit Videos auf Desktop-, Tablet- und Mobilgeräten im richtigen Format und in einer geeigneten Qualität wiedergegeben werden.
* Assets – Sie können adaptive Videosets statt einzelner Video-Assets verwenden. Ein adaptives Videoset ist ein Container für alle Videoausgabedarstellungen, die zur nahtlosen Wiedergabe von Videos auf verschiedenen Bildschirmen erforderlich sind. Es umfasst Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert wurden, wie 400 kBit/s, 800 kBit/s und 1000 kBit/s. Ein adaptives Videoset wird zusammen mit der S7-Videokomponente für adaptives Videostreaming auf mehreren Bildschirmen verwendet, einschließlich Desktop-Geräten und iOS-, Android™-, Blackberry®- und Windows-Mobilgeräten. Weitere Informationen finden Sie in der [Dynamic Media Classic-Dokumentation zu adaptiven Videosets](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/video/quick-start-video.html?lang=de#video).

## Über FFMPEG und Dynamic Media Classic {#about-ffmpeg-and-scene}

Die Grundlage des standardmäßigen Videokodierungsprozesses ist die Verwendung der FFMPEG-basierten Integration mit Videoprofilen. Aus diesem Grund enthält der vorkonfigurierte Workflow [!UICONTROL DAM-Update-Asset] die folgenden FFMPEG-basierten Workflow-Schritte:

* FFMPEG-Miniaturen
* FFMPEG-Kodierung

Diese beiden Workflow-Schritte werden durch Aktivierung und Konfiguration der Dynamic Media Classic-Integration nicht automatisch aus dem Aufnahme-Workflow [!UICONTROL DAM-Update-Asset] entfernt oder deaktiviert. Wenn Sie die FFMPEG-basierte Videokodierung in Adobe Experience Manager bereits nutzen, ist es wahrscheinlich, dass FFMPEG in Ihren Authoring-Umgebungen bereits installiert ist. In diesem Fall wird ein neues Video, das mit Experience Manager Assets erfasst wird, zweimal kodiert: einmal vom FFMPEG-Kodierer und einmal von der Dynamic Media Classic-Integration.

Wenn Sie die FFMPEG-basierte Videokodierung in Experience Manager konfiguriert und FFMPEG installiert haben, empfiehlt Adobe, die beiden FFMPEG-Workflows aus Ihren Workflows [!UICONTROL DAM-Update-Asset] zu entfernen.

### Unterstützte Formate {#supported-formats}

Die folgenden Formate werden für die Dynamic Media Classic-Videokomponente unterstützt:

* F4V H.264
* H.264 (.mp4)

### Festlegen eines Speicherorts für hochgeladene Videos {#deciding-where-to-upload-your-video}

Der Speicherort für hochgeladene Videos hängt von folgenden Faktoren ab:

* Benötigen Sie für das Video-Asset einen Workflow?
* Benötigen Sie für das Video-Asset eine Versionskontrolle?

Falls Sie eine der Fragen mit „ja“ beantworten können, laden Sie Ihr Video direkt in Adobe DAM hoch. Lautet die Antwort auf beide Fragen „nein“, sollten Sie Ihr Video direkt in Dynamic Media Classic hochladen. Der Workflow für die einzelnen Szenarien wird im folgenden Abschnitt beschrieben.

#### Wenn Sie Ihr Video direkt in Adobe Assets hochladen {#if-you-are-uploading-your-video-directly-to-adobe-assets}

Wenn Sie einen Workflow oder eine Versionierung für Ihre Assets benötigen, sollten Sie sie zuerst in Adobe Assets hochladen. Der folgende Workflow wird empfohlen:

1. Laden Sie das Video-Asset in Adobe Assets hoch. Es findet eine automatische Kodierung und Veröffentlichung in Dynamic Media Classic statt.
1. Öffnen Sie Experience Manager und greifen Sie in WCM auf der Registerkarte **[!UICONTROL Filme]** des Content Finders auf Video-Assets zu.
1. Verwenden Sie zum Erstellen die Video- oder Foundation-Videokomponente von Dynamic Media Classic.

#### Wenn Sie Ihr Video in Dynamic Media Classic hochladen {#if-you-are-uploading-your-video-to-scene}

Wenn Sie keinen Workflow und keine Versionierung für Ihre Assets benötigen, sollten Sie sie in Dynamic Media Classic hochladen. Der folgende Workflow wird empfohlen:

1. Richten Sie im Dynamic Media Classic-Desktop-Programm das [geplante Hochladen und Kodieren von FTP-Servern in Dynamic Media Classic ein (automatisiert)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html?lang=de#upload-options).
1. Greifen Sie in Experience Manager auf Video-Assets in WCM auf der Registerkarte **[!UICONTROL Dynamic Media Classic]** im Content Finder zu.
1. Verwenden Sie zum Erstellen die Dynamic Media Classic-Videokomponente.

### Konfigurieren der Integration mit Dynamic Media Classic-Video {#configuring-integration-with-scene-video}

1. Navigieren Sie in **[!UICONTROL Cloud Services]** zu Ihrer **[!UICONTROL Dynamic Media Classic]**-Konfiguration und wählen Sie **[!UICONTROL Bearbeiten]** aus.
1. Wählen Sie die Registerkarte **[!UICONTROL Video]** aus.

   >[!NOTE]
   >
   >Die Registerkarte **[!UICONTROL Video]** wird nicht angezeigt, wenn die Seite keine Cloud-Konfiguration hat. Siehe [Aktivieren von Dynamic Media Classic für WCM](#enablingscene7forwcm).

1. Wählen Sie das Profil für adaptive Videokodierung, ein Standardprofil für die Kodierung einzelner Videos, oder ein benutzerdefiniertes Videokodierungsprofil aus.

   >[!NOTE]
   >
   >Weitere Informationen zur Bedeutung der Videovorgaben finden Sie unter [Videovorgaben für die Kodierung von Videodateien](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html?lang=de#video-presets-for-encoding-video-files).
   >
   >Adobe empfiehlt, entweder beide adaptive Videosets bei der Konfiguration der universellen Vorlagen oder die Option **[!UICONTROL Adaptive Videokodierung]** auszuwählen.

1. Die ausgewählten Kodierungsprofile werden automatisch auf alle Videos angewendet, die in den CQ DAM-Zielordner hochgeladen werden, den Sie für diese Dynamic Media Classic-Cloud-Konfiguration einrichten. Sie können mehrere Dynamic Media Classic-Cloud-Konfigurationen mit verschiedenen Zielordnern einrichten, um nach Bedarf verschiedene Kodierungsprofile anzuwenden.

### Aktualisieren von Viewer- und Kodierungsvorlagen {#updating-viewer-and-encoding-presets}

Aktualisieren Sie die Viewer- und Kodierungsvorgaben für Videos in Experience Manager, wenn die Vorgaben in Dynamic Media Classic aktualisiert wurden. Navigieren Sie in diesem Fall zur Dynamic Media Classic-Konfiguration in der Cloud-Konfiguration und wählen Sie **Aktualisieren von Viewer- und Kodierungsvorgaben** aus.

![chlimage_1-131](assets/chlimage_1-131.png)

### Hochladen des Primärvideos {#uploading-your-master-video}

So laden Sie Ihr Primärvideo von Adobe DAM in Dynamic Media Classic hoch:

1. Navigieren Sie zum CQ DAM-Zielordner, in dem Sie Ihre Cloud-Konfiguration mit Dynamic Media Classic-Kodierungsprofilen eingerichtet haben.
1. Wählen Sie **[!UICONTROL Hochladen]** aus, um das Primärvideo hochzuladen. Upload und Kodierung des Videos sind fertig, wenn der Workflow [!UICONTROL DAM-Update-Asset] abgeschlossen und neben **[!UICONTROL In Dynamic Media Classic veröffentlichen]** ein Häkchen zu sehen ist.

   >[!NOTE]
   >
   >Es kann etwas Zeit in Anspruch nehmen, bis die Videominiaturen erstellt wurden.

   Wenn Sie das DAM-Primärvideo auf die Videokomponente ziehen, greift es für die Bereitstellung auf *alle* Dynamic Media Classic-kodierten Proxy-Ausgabedarstellungen zu.

### Foundation-Videokomponente und Dynamic Media Classic-Videokomponente im Vergleich {#foundation-video-component-versus-scene-video-component}

Wenn Sie Experience Manager nutzen, haben Sie Zugriff auf die Videokomponente in Sites und auf die Dynamic Media Classic-Videokomponente. Diese Komponenten sind nicht austauschbar.

Die Dynamic Media Classic-Videokomponente funktioniert nur für Dynamic Media Classic-Videos. Die Foundation-Komponente funktioniert für Videos, die aus Experience Manager (mithilfe von ffmpeg) und Dynamic Media Classic-Videos gespeichert werden.

Die folgende Matrix verdeutlicht, wann Sie welche Komponente nutzen sollten:

![chlimage_1-132](assets/chlimage_1-132.png)

>[!NOTE]
>
>Die Dynamic Media Classic-Videokomponente verwendet standardmäßig das universelle Videoprofil. Sie können jedoch den HTML5-basierten Videoplayer für die Verwendung durch Experience Manager abrufen. Kopieren Sie in Dynamic Media Classic den Einbettungs-Code des vorkonfigurierten HTML5-Videoplayers und fügen Sie ihn in Ihre Experience Manager-Seite ein.

## Experience Manager-Videokomponente {#aem-video-component}

Auch wenn die Verwendung der Dynamic Media Classic-Videokomponente für die Anzeige von Dynamic Media Classic-Videos empfohlen wird, wird in diesem Abschnitt der Vollständigkeit halber die Verwendung von Dynamic Media Classic-Videos mit der [!UICONTROL Foundation-Videokomponente] im Experience Manager beschrieben.

### Experience Manager-Videos und Dynamic Media Classic-Videos im Vergleich {#aem-video-and-scene-video-comparison}

Die folgende Tabelle bietet einen allgemeinen Vergleich der unterstützten Funktionen zwischen der Experience Manager Foundation-Videokomponente und der Dynamic Media Classic-Videokomponente:

|  | Experience Manager Foundation-Video | Dynamic Media Classic­Video |
|---|---|---|
| Ansatz | HTML5 hat Priorität. Flash dient nur zum Ausweichen bei Nicht-HTML5-Inhalten. | Flash auf den meisten Desktopgeräten HTML5 kommt auf Mobilgeräten und Tablets zum Einsatz. |
| Bereitstellung | Progressiv | Adaptives Streaming |
| Nachverfolgung | Ja | Ja |
| Erweiterbarkeit | Ja | Nein |
| Mobile Videos | Ja | Ja |

### Setup {#setting-up}

#### Erstellen von Videoprofilen {#creating-video-profiles}

Die verschiedenen Videokodierungen werden entsprechend den in der Dynamic Media Classic-Cloud-Konfiguration ausgewählten Dynamic Media Classic-Kodierungsvorgaben erstellt. Damit die Foundation-Videokomponente sie verwendet, müssen Sie für jede ausgewählte Dynamic Media Classic-Kodierungsvorgabe ein Videoprofil erstellen. Damit kann die Videokomponente die DAM-Ausgabedarstellungen entsprechend auswählen.

>[!NOTE]
>
>Neue Videoprofile und Änderungen daran müssen für eine Veröffentlichung aktiviert werden.

1. Starten Sie Experience Manager, gehen Sie zu **[!UICONTROL Tools]** und wählen Sie **[!UICONTROL Konfigurationskonsole]** aus.
1. Navigieren Sie in der Konfigurationskonsole in der Navigationsstruktur zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoprofile]**.
1. Erstellen Sie ein Dynamic Media Classic-Videoprofil. Wählen Sie im Menü **[!UICONTROL Neu]** den Befehl **[!UICONTROL Seite erstellen]** aus.
1. Wählen Sie die Dynamic Media Classic-Videoprofilvorlage aus. Geben Sie der neuen Videoprofilseite einen Namen und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. Bearbeiten Sie das neue Videoprofil. Wählen Sie zuerst die Cloud-Konfiguration aus. Wählen Sie anschließend dieselbe Kodierungsvorlage aus, die Sie bereits in der Cloud-Konfiguration ausgewählt haben.

   ![chlimage_1-134](assets/chlimage_1-134.png)

   | Eigenschaft | Beschreibung |
   |---|---|
   | Dynamic Media Classic-Cloud-Konfiguration | Die Cloud-Konfiguration, die für die Kodierungsvorlagen verwendet werden soll |
   | Dynamic Media Classic-Kodierungsvorgabe | Die Kodierungsvorlage, die diesem Videoprofil zugeordnet werden soll |
   | HTML5-Videotyp | Diese Eigenschaft ermöglicht es, den Wert der Typeigenschaft des HTML5-Videoquellelements festzulegen. Diese Information wird nicht von den Dynamic Media Classic-Kodierungsvorlagen bereitgestellt, sie ist jedoch erforderlich, um die Videos mit dem HTML5-Videoelements richtig zu rendern. Eine Liste für gängige Formate wird bereitgestellt, kann jedoch für andere Formate überschrieben werden. |

   Wiederholen Sie diesen Schritt für alle in der Cloud-Konfiguration ausgewählten Kodierungsvorlagen, die Sie in der Videokomponente verwenden möchten.

#### Konfigurieren des Designs {#configuring-design}

Die Foundation-Videokomponente muss darüber informiert sein, welche Videoprofile verwendet werden sollen, damit sie die Videoquellenliste erstellen kann. Öffnen Sie das Design-Dialogfeld der Videokomponenten und konfigurieren Sie das Design der Komponenten für die Nutzung der neuen Videoprofile.

>[!NOTE]
>
>Wenn Sie die Foundation-Videokomponente auf einer Mobilseite verwenden, wiederholen Sie diese Schritte für das Design der Mobilseite.

>[!NOTE]
>
>Bei Änderungen am Design ist eine Aktivierung des Designs erforderlich, damit es für die Veröffentlichung übernommen wird.

1. Öffnen Sie den Designdialog der Foundation-Videokomponente und wechseln Sie auf die Registerkarte **[!UICONTROL Profile]**. Löschen Sie dann die nativen Profile und fügen Sie die neuen Dynamic Media Classic-Videoprofile hinzu. Die Reihenfolge der Profilliste im Design-Dialogfeld definiert die Reihenfolge des Videoquellenelements beim Rendern.
1. Bei Browsern, die kein HTML5 unterstützen, ermöglicht die Videokomponente ein Ausweichen auf Flash. Öffnen Sie den Designdialog der Videokomponenten und wechseln Sie auf die Registerkarte **[!UICONTROL Flash]**. Konfigurieren Sie die Einstellungen des Flash-Players und ordnen Sie ein Ersatzprofil für den Flash-Player zu.

#### Checkliste {#checklist}

1. Erstellen Sie eine Dynamic Media Classic-Cloud-Konfiguration. Vergewissern Sie sich, dass die Videocodierungsvorgaben festgelegt sind und das Importprogramm ausgeführt wird.
1. Erstellen Sie ein Dynamic Media Classic-Videoprofil für jede in der Cloud-Konfiguration ausgewählte Videokodierungsvorlage.
1. Die Videoprofile müssen aktiviert sein.
1. Konfigurieren Sie das Design der Foundation-Videokomponente auf Ihrer Seite.
1. Aktivieren Sie das Design, sobald Sie mit Ihren Design-Änderungen fertig sind.
