---
title: Verwalten von Video-Assets
description: Hochladen, Anzeigen einer Vorschau, Kommentieren und Veröffentlichen von Video-Assets in [!DNL Adobe Experience Manager].
contentOwner: AG
role: User
feature: Asset Management
exl-id: 21d3e0bd-5955-470a-8ca2-4d995c17eb4c
source-git-commit: 068f6c1c2909c2840e9ad4c0ad295538e543d9c9
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 57%

---

# Verwalten von Video-Assets  {#manage-video-assets}

| Version | Artikellink |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-video-assets.html?lang=en) |
| AEM 6.5 | Dieser Artikel |
| AEM 6.4 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-64/assets/managing/managing-video-assets.html?lang=en) |

Das Videoformat ist ein wichtiger Bestandteil der digitalen Assets eines Unternehmens. [!DNL Adobe Experience Manager] bietet ausgereifte Produkte und Funktionen, mit denen Sie den gesamten Lebenszyklus von Video-Assets nach deren Erstellung verwalten können.

Lernen Sie, wie Sie die Video-Assets in [!DNL Adobe Experience Manager Assets] verwalten und bearbeiten. Videokodierung und -transkodierung, z. B. FFmpeg-Transkodierung, ist mit [!DNL Dynamic Media] Integration.

## Hochladen und Anzeigen der Vorschau von Video-Assets {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] generiert eine Vorschau für Video-Assets mit der Erweiterung MP4. Wenn das Format des Assets nicht MP4 ist, installieren Sie das FFmpeg-Paket, um eine Vorschau zu generieren. FFmpeg erstellt Videoausgabeformate vom Typ OGG und MP4. Sie können eine Vorschau dieser Ausgabedarstellungen in der Benutzeroberfläche von [!DNL Assets] anzeigen.

1. Navigieren Sie im Ordner „Digitale Assets“ (oder dessen Unterordnern) zum Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Um Assets hochzuladen, klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]** und wählen dann **[!UICONTROL Dateien]** aus. Alternativ können Sie eine Datei auf die Benutzeroberfläche ziehen. Weitere Informationen finden Sie unter [Hochladen von Assets](manage-assets.md#uploading-assets).
1. Um ein Video in der Kartenansicht anzuzeigen, klicken Sie auf die Schaltfläche **[!UICONTROL Play]** ![Abspieloption](assets/do-not-localize/play.png) -Option für das Video-Asset. Sie können Videos nur in der Kartenansicht anhalten oder wiedergeben. Die Optionen [!UICONTROL Wiedergabe] und [!UICONTROL Pause] sind in der Listenansicht nicht verfügbar.

1. Um eine Vorschau des Videos auf der Seite mit den Asset-Details anzuzeigen, klicken Sie auf **[!UICONTROL Bearbeiten]** auf der Karte. Das Video wird im systemeigenen Video-Player des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

   ![Steuerelemente für die Videowiedergabe](assets/video-playback-controls.png)

## Konfiguration zum Hochladen von Assets, die größer als 2 GB sind {#configuration-to-upload-assets-that-are-larger-than-gb}

Standardmäßig [!DNL Assets] dürfen Sie keine Assets hochladen, die aufgrund einer Dateigrößenbeschränkung größer als 2 GB sind. Sie können diese Beschränkung aber umgehen, indem Sie CRXDE Lite aufrufen und im Verzeichnis `/apps` einen Knoten erstellen. Der Knoten muss denselben Knotennamen, dieselbe Verzeichnisstruktur und vergleichbare Knoteneigenschaften im Hinblick auf die Reihenfolge aufweisen.

Zusätzlich zu [!DNL Assets] Konfiguration ändern Sie die folgenden Konfigurationen, um große Assets hochzuladen:

* Erhöhen Sie die Ablaufzeit des Tokens. Siehe [!UICONTROL Adobe Granite CSRF Servlet] in der Web-Konsole unter `https://[aem_server]:[port]/system/console/configMgr`. Weitere Informationen finden Sie unter [CSRF-Schutz](/help/sites-developing/csrf-protection.md).
* Erhöhen Sie `receiveTimeout` in der Dispatcher-Konfiguration. Weitere Informationen finden Sie unter [Experience Manager Dispatcher-Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options).

>[!NOTE]
>
>Die [!DNL Experience Manager] Die klassische Benutzeroberfläche hat keine Dateigrößenbeschränkung von 2 GB. Außerdem werden End-to-End-Workflows für große Videos nicht vollständig unterstützt.

Um eine höhere Dateigrößenbeschränkung zu konfigurieren, führen Sie die folgenden Schritte im Verzeichnis `/apps` aus.

1. In [!DNL Experience Manager]klicken **[!UICONTROL Instrumente]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in CRXDE Lite zu `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`. Um das Verzeichnisfenster anzuzeigen, klicken Sie auf das `>>`.
1. Klicken Sie in der Symbolleiste auf die **[!UICONTROL Überlagerungsknoten]**. Wählen Sie alternativ **[!UICONTROL Überlagerungsknoten]** aus dem Kontextmenü aus.
1. Im **[!UICONTROL Überlagerungsknoten]** dialog, klicken Sie **[!UICONTROL OK]**.

   ![Überlagerungsknoten](assets/overlay-node-path.png)

1. Aktualisieren Sie die Browser-Ansicht. Der Überlagerungsknoten `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` ist ausgewählt.
1. Geben Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** den gewünschten Wert in Byte ein, um die maximale Größe festzulegen. Um beispielsweise die Größenbeschränkung auf 30 GB zu erhöhen, geben Sie den Wert `32212254720` ein.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Alle speichern]**.
1. In [!DNL Experience Manager]klicken **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Web-Konsole]**.
1. Im [!DNL Adobe Experience Manager] [!UICONTROL Web Console Bundles] Seite in der Spalte &quot;Name&quot;der Tabelle, suchen Sie nach und klicken Sie auf **[!UICONTROL Adobe Granite Workflow External Process Job Handler]**.
1. Im [!UICONTROL Adobe Granite Workflow External Process Job Handler] Seite, legen Sie die Sekunden für **[!UICONTROL Standard-Timeout]** und **[!UICONTROL Max. Timeout]** Felder zu `18000` (fünf Stunden). Klicken Sie auf **[!UICONTROL Speichern]**.
1. In [!DNL Experience Manager]klicken **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie auf der Seite &quot;Workflow-Modelle&quot;die Option **[!UICONTROL Dynamic Media-Kodierungsvideo]** Klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Doppelklicken Sie auf der Workflow-Seite auf die **[!UICONTROL Dynamic Media Video Service-Prozess]** -Komponente.
1. Erweitern Sie im Dialogfeld [!UICONTROL Schritteigenschaften] auf der Registerkarte **[!UICONTROL Allgemein]** die Option **Erweiterte Einstellungen**.
1. Im **[!UICONTROL Zeitüberschreitung]** ein Feld, geben Sie den Wert von `18000`Klicken Sie auf **[!UICONTROL OK]** , um zur **[!UICONTROL Dynamic Media-Kodierungsvideo]** Workflow-Seite.
1. Oben auf der Seite unter dem [!UICONTROL Dynamic Media-Kodierungsvideo] Seitentitel, klicken Sie auf **[!UICONTROL Speichern]**.

## Veröffentlichen von Video-Assets {#publish-video-assets}

Nach der Veröffentlichung können Sie die Video-Assets als URL in eine Web-Seite einbeziehen oder die Assets direkt einbetten. Weitere Informationen finden Sie unter [Veröffentlichen von Dynamic Media-Assets](/help/assets/publishing-dynamicmedia-assets.md).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotate-video-assets}

1. Wählen Sie in der [!DNL Assets]-Konsole auf der Asset-Karte die Option **[!UICONTROL Bearbeiten]**, um die Seite mit den Asset-Details anzuzeigen.
1. Um das Video wiederzugeben, klicken Sie auf **[!UICONTROL Vorschau]**.
1. Um das Video zu kommentieren, klicken Sie auf **[!UICONTROL Kommentieren]**. Zu dem jeweiligen Zeitpunkt (Frame) im Video wird eine Anmerkung hinzugefügt. Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch gespeichert. Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**.

   ![Zeichnen und Kommentieren in einem Videoframe](assets/annotate-video.png)

1. Suchen Sie nach einem bestimmten Punkt im Video, indem Sie die Zeit in Sekunden in das **Textfeld** eingeben und auf **Springen** klicken. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie „20“ in das Textfeld ein.

   ![Suche nach einer Zeit in einem Video, die um bestimmte Sekunden übersprungen werden soll](assets/seek-in-video.png)

1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

   ![Anzeigen von Anmerkungen und Details in der Timeline](assets/timeline-view-annotation.png)

>[!MORELIKETHIS]
>
>* [Verwalten digitaler Assets in Experience Manager Assets](/help/assets/manage-assets.md)
>* [Verwalten von Sammlungen in Experience Manager Assets](/help/assets/manage-collections.md)
>* [Dokumentation zu Dynamic Media-Videos](/help/assets/video.md).

