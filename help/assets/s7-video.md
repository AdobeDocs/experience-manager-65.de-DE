---
title: Video
description: Erfahren Sie mehr über das zentrale Video-Asset-Management in Adobe Experience Manager Assets, wo Sie Videos zur automatischen Kodierung in Dynamic Media Classic hochladen und direkt über Experience Manager Assets auf Dynamic Media Classic-Videos zugreifen können. Die Dynamic Media Classic-Videointegration erweitert die Reichweite optimierter Videos auf alle Bildschirme.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
role: User, Admin
mini-toc-levels: 3
exl-id: 56009925-1a36-48b5-b96c-ec2e468da106
feature: Video
source-git-commit: 04050f31742c926b45235595f6318929d3767bd8
workflow-type: tm+mt
source-wordcount: '1551'
ht-degree: 88%

---

# Video {#video}

Adobe Experience Manager Assets bietet zentralisiertes Video-Asset-Management, mit dem Sie Videos direkt in Assets zur automatischen Kodierung in Dynamic Media Classic hochladen und für die Seitenerstellung direkt in Assets auf Dynamic Media Classic-Videos zugreifen können.

Die Dynamic Media Classic-Videointegration erweitert die Reichweite optimierter Videos auf alle Bildschirme (automatische Geräteanpassung und Bandbreitenerkennung).

* Die Komponente **[!UICONTROL Scene7-Video]** führt automatisch eine Geräte- und Bandbreitenerkennung durch, damit Videos auf Desktop-, Tablet- und Mobilgeräten im richtigen Format und in einer geeigneten Qualität wiedergegeben werden.
* Assets – Sie können adaptive Videosets statt einzelner Video-Assets verwenden. Ein adaptives Videoset enthält alle Videoausgabedarstellungen, die für die nahtlose Wiedergabe des Videos auf mehreren Bildschirmen erforderlich sind. Es umfasst Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert wurden, wie 400 kBit/s, 800 kBit/s und 1000 kBit/s. Ein adaptives Videoset wird zusammen mit der S7-Videokomponente für adaptives Video-Streaming auf mehreren Bildschirmen verwendet, einschließlich Desktop-Geräten und iOS-, Android™-, BlackBerry®- und Windows-Mobilgeräten.
<!-- See [Scene7 documentation about adaptive video sets for more information](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html). -->

## Informationen zu FFMPEG und Dynamic Media Classic {#about-ffmpeg-and-scene}

Die Grundlage des standardmäßigen Videokodierungsprozesses ist die Verwendung der FFMPEG-basierten Integration mit Videoprofilen. Daher enthält der vordefinierte DAM-Aufnahme-Workflow die folgenden beiden ffmpeg-basierten Workflow-Schritte:

* FFMPEG-Miniaturen
* FFMPEG-Codierung

Durch Aktivierung und Konfiguration der Dynamic Media Classic-Integration werden diese beiden Workflow-Schritte im standardmäßigen Aufnahme-Workflow von DAM nicht automatisch entfernt oder deaktiviert. Wenn Sie die FFMPEG-basierte Videokodierung in Adobe Experience Manager bereits nutzen, ist es wahrscheinlich, dass FFMPEG in Ihren Authoring-Umgebungen bereits installiert ist. In diesem Fall würde ein Video, das über DAM aufgenommen wurde, zweimal kodiert werden: einmal durch den FFMPEG-Kodierer und einmal durch die Dynamic Media Classic-Integration.

Wenn Sie die FFMPEG-basierte Videokodierung in Experience Manager konfiguriert und FFMPEG installiert haben, empfiehlt Adobe, die beiden FFMPEG-Workflows aus Ihren DAM-Aufnahme-Workflows zu entfernen.

## Unterstützte Formate {#supported-formats}

Die folgenden Formate werden für die Scene7-Videokomponente unterstützt:

* F4V H.264
* MP4 H.264

## Festlegen eines Speicherorts für hochgeladene Videos {#deciding-where-to-upload-your-video}

Die Entscheidung, wo Sie Ihre Video-Assets hochladen können, hängt von Folgendem ab:

* Benötigen Sie einen Workflow für das Video-Asset?
* Benötigen Sie eine Versionskontrolle für das Video-Asset?

Wenn Sie eine oder beide Fragen mit „Ja“ beantworten können, laden Sie Ihr Video direkt in Adobe DAM hoch. Lautet die Antwort auf beide Fragen „nein“, sollten Sie Ihr Video direkt in Dynamic Media Classic hochladen. Der Workflow für die einzelnen Szenarien wird im folgenden Abschnitt beschrieben.

### Wenn Sie Ihr Video direkt auf Adobe DAM hochladen {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Wenn Sie einen Workflow oder eine Versionierung für Ihre Assets benötigen, laden Sie sie zuerst in Adobe DAM hoch. Der folgende Workflow wird empfohlen:

1. Laden Sie das Video-Asset in Adobe DAM hoch. Es findet eine automatische Kodierung und Veröffentlichung in Dynamic Media Classic statt.
1. Öffnen Sie Experience Manager und greifen Sie in WCM auf der Registerkarte **[!UICONTROL Filme]** des Content Finders auf Video-Assets zu.
1. Verwenden Sie die **[!UICONTROL Scene7]**- oder **[!UICONTROL Foundation]**-Videokomponente.

### Wenn Sie Ihr Video in Dynamic Media Classic hochladen {#if-you-are-uploading-your-video-to-scene}

Wenn Sie keinen Workflow und keine Versionierung für Ihre Assets benötigen, laden Sie sie in Scene7 hoch. Der folgende Workflow wird empfohlen:

1. [Planen Sie in Dynamic Media Classic einen FTP-Upload und eine Kodierung für Scene7 (System automatisiert)](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html?lang=de#upload-files-using-via-ftp).
1. Greifen Sie in Experience Manager in WCM auf der Registerkarte **[!UICONTROL Scene7]** des Content Finders auf Video-Assets zu.
1. Verwenden Sie die Komponente **[!UICONTROL Scene7-Video]**.

## Konfigurieren der Integration mit Scene7-Videos {#configuring-integration-with-scene-video}

1. Navigieren Sie in **[!UICONTROL Cloud-Services]** zu Ihrer **[!UICONTROL Scene7]**-Konfiguration und wählen Sie **[!UICONTROL Bearbeiten]** aus.
1. Wählen Sie die Registerkarte **[!UICONTROL Video]** aus.

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >Die Registerkarte **[!UICONTROL Video]** wird nicht angezeigt, wenn die Seite keine Cloud-Konfiguration hat.

1. Wählen Sie das Profil für adaptive Videokodierung, ein Standardprofil für die Kodierung einzelner Videos, oder ein benutzerdefiniertes Videokodierungsprofil aus.

   >[!NOTE]
   >
   >Weitere Informationen dazu, was die Videovorgaben bedeuten, finden Sie in der [Dynamic Media Classic-Dokumentation](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html?lang=de#video-presets-for-encoding-video-files).
   >
   >Adobe empfiehlt, entweder beide adaptive Videosets bei der Konfiguration der universellen Vorgaben oder die Option **[!UICONTROL Adaptive Videokodierung]** auszuwählen.

1. Die ausgewählten Kodierungsprofile werden automatisch auf alle Videos angewendet, die in den für diese Scene7-Cloud-Konfiguration eingerichteten CQ DAM-Zielordner hochgeladen wurden. Sie können mehrere Scene7-Cloud-Konfigurationen mit verschiedenen Zielordnern einrichten, um bei Bedarf unterschiedliche Kodierungsprofile anzuwenden.

## Aktualisieren von Viewer- und Kodierungsvorgaben {#updating-viewer-and-encoding-presets}

Um die Viewer- und Kodierungsvorgaben für Videos zu aktualisieren, da die Vorgaben in Scene7 aktualisiert wurden, navigieren Sie zur Scene7-Konfiguration in der Cloud-Konfiguration und wählen Sie **[!UICONTROL Viewer- und Kodierungsvorgaben aktualisieren]** aus.

![chlimage_1-364](assets/chlimage_1-364.png)

## Hochladen des primären Quellvideos von Adobe DAM in Scene7 {#uploading-your-master-video}

1. Navigieren Sie zum CQ DAM-Zielordner, in dem Sie Ihre Cloud-Konfiguration mit Scene7-Kodierungsprofilen eingerichtet haben.
1. Wählen Sie **[!UICONTROL Hochladen]** aus, um das primäre Quellvideo hochzuladen. Upload und Kodierung des Videos sind abgeschlossen, wenn der Workflow [!UICONTROL DAM-Update-Asset] abgeschlossen ist und **[!UICONTROL In Scene7 veröffentlichen]** mit einem Häkchen versehen ist.

   >[!NOTE]
   >
   >Es nimmt etwas Zeit in Anspruch, bis die Videominiaturansichten erstellt wurden.

   Durch Ziehen des primären DAM-Quellvideos auf die Videokomponente wird auf *alle* Scene7-kodierten Proxy-Ausgabedarstellungen für die Bereitstellung zugegriffen.

## Foundation-Videokomponente im Vergleich zur Scene7-Videokomponente {#foundation-video-component-versus-scene-video-component}

Wenn Sie Experience Manager nutzen, haben Sie auf die Videokomponente, die in Sites verfügbar ist, und auf die Scene7-Videokomponente Zugriff. Diese Komponenten sind nicht austauschbar.

Die Scene7-Videokomponente funktioniert nur für Scene7-Videos. Die Foundation-Komponente funktioniert mit Videos, die in Experience Manager (mit FFMPEG) gespeichert wurden, und Scene7-Videos.

Die folgende Matrix verdeutlicht, wann welche Komponente verwendet wird:

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>Die S7-Videokomponente verwendet standardmäßig das universelle Videoprofil. Sie können jedoch den HTML5-basierten Video-Player für die Verwendung durch Experience Manager abrufen. Kopieren Sie den Einbettungs-Code des standardmäßigen HTML5-Video-Players in Scene7 und fügen Sie ihn in Ihre Experience Manager-Seite ein.

## Experience Manager-Videokomponente {#aem-video-component}

Es wird zwar empfohlen, zum Abspielen von Scene7-Videos die Scene7-Videokomponente zu verwenden, in diesem Abschnitt wird der Vollständigkeit halber aber trotzdem beschrieben, wie Sie Scene7-Videos in Experience Manager mit der Foundation-Videokomponente verwenden.

### Vergleich von Experience Manager-Videos und Scene7-Videos {#aem-video-and-scene-video-comparison}

In der folgenden Tabelle finden Sie einen Vergleich der unterstützen Funktionen der Experience Manager-Foundation-Videokomponente und der Scene7-Videokomponente:

|   | Experience Manager-Foundation-Video | Scene7-Video |
|---|---|---|
| Ansatz | HTML5 als erster Ansatz. Flash dient nur als Ausweichlösung bei Nicht-HTML5-Inhalten. | Flash auf den meisten Desktopgeräten HTML5 wird für Mobilgeräte und Tablets verwendet. |
| Bereitstellung | Progressiv | Adaptives Streaming |
| Tracking | Ja | Ja |
| Erweiterbarkeit | Ja | Nein |
| Mobile-Video | Ja | Ja |

### Setup {#setting-up}

#### Erstellen von Videoprofilen {#creating-video-profiles}

Die verschiedenen Videokodierungsmethoden werden anhand der S7-Kodierungsvorgaben erstellt, die in der S7-Cloud-Konfiguration ausgewählt werden. Damit sie von der Foundation-Videokomponente genutzt werden, muss für jede ausgewählte S7-Kodierungsvorgabe ein Videoprofil erstellt werden. Mit dieser Methode kann die Videokomponente die DAM-Ausgabedarstellungen entsprechend auswählen.

>[!NOTE]
>
>Neue Videoprofile und Änderungen daran müssen für eine Veröffentlichung aktiviert werden.

1. Wählen Sie in Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Konfigurationskonsole]** aus.
1. Navigieren Sie in der **[!UICONTROL Konfigurationskonsole]** in der Navigationsstruktur zu **[!UICONTROL Tools]** > **[!UICONTROL DAM]** > **[!UICONTROL Videoprofile]**.
1. Erstellen Sie ein S7-Videoprofil. Im **[!UICONTROL Neu]**. Menü auswählen **[!UICONTROL Seite erstellen]** und wählen Sie dann die Vorlage Scene7-Videoprofil aus. Geben Sie der neuen Videoprofilseite einen Namen und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. Bearbeiten Sie das neue Videoprofil. Wählen Sie zuerst die Cloud-Konfiguration aus. Wählen Sie dann dieselbe Codierungsvorgabe aus wie in der Cloud-Konfiguration.

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | Eigenschaft | Beschreibung |
   |---|---|
   | Scene7-Cloud-Konfiguration | Die Cloud-Konfiguration, die für die Codierungsvorlagen verwendet werden soll |
   | Scene7-Kodierungsvorgabe | Die Codierungsvorgabe, mit der dieses Videoprofil verknüpft werden soll. |
   | HTML5-Videotyp | Mit dieser Eigenschaft können Sie den Wert der Typeigenschaft des HTML5-Videoquellelements festlegen. Diese Informationen werden nicht von den S7-Kodierungsvorgaben bereitgestellt, sind aber für die korrekte Wiedergabe der Videos mithilfe des HTML5-Videoelements erforderlich. Eine Liste für gängige Formate wird bereitgestellt, kann jedoch für andere Formate überschrieben werden. |

   Wiederholen Sie diesen Schritt für alle in der Cloud-Konfiguration ausgewählten Kodierungsvorgaben, die Sie in der Videokomponente verwenden möchten.

#### Konfigurieren des Designs {#configuring-design}

Die **[!UICONTROL Foundation-Video]** muss wissen, welche Videoprofile zum Erstellen der Videoquellenliste verwendet werden sollen. Öffnen Sie das Dialogfeld für das Design von Videokomponenten und konfigurieren Sie das Design der Komponenten für die Nutzung der neuen Videoprofile.

>[!NOTE]
>
>Wenn Sie die **[!UICONTROL Foundation]**-Videokomponente auf einer Mobilseite verwenden, wiederholen Sie diese Schritte für das Design der Mobilseite.

>[!NOTE]
>
>Änderungen am Entwurf erfordern die Aktivierung des Designs, damit er bei der Veröffentlichung wirksam wird.

1. Öffnen Sie das Dialogfeld für das Design der **[!UICONTROL Foundation]**-Videokomponente und wechseln Sie auf die Registerkarte **[!UICONTROL Profile]**. Löschen Sie anschließend die vordefinierten Profile und fügen Sie die neuen S7-Videoprofile hinzu. Die Reihenfolge der Profilliste im Design-Dialogfeld definiert die Reihenfolge des Videoquellenelements beim Rendern.
1. Bei Browsern, die kein HTML5 unterstützen, ermöglicht die Videokomponente ein Ausweichen auf Flash. Öffnen Sie das Dialogfeld für das Design der Videokomponenten und wechseln Sie auf die Registerkarte **[!UICONTROL Flash]**. Konfigurieren Sie die Einstellungen des Flash-Players und weisen Sie ein Ersatzprofil für den Flash-Player zu.

#### Checkliste {#checklist}

1. Erstellen Sie eine S7-Cloud-Konfiguration. Vergewissern Sie sich, dass die Videokodierungsvorgaben festgelegt sind und das Importprogramm ausgeführt wird.
1. Erstellen Sie für jede in der Cloud-Konfiguration ausgewählte Videokodierungsvorgabe ein S7-Videoprofil.
1. Die Videoprofile müssen aktiviert sein.
1. Konfigurieren Sie das Design der **[!UICONTROL Foundation]**-Videokomponente auf Ihrer Seite.
1. Aktivieren Sie das Design, sobald Sie mit Ihren Design-Änderungen fertig sind.
