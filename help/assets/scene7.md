---
title: Hinzufügen von Dynamic Media Classic-Funktionen zu Ihrer Seite
description: Erfahren Sie, wie Sie Ihrer AEM Funktionen und Komponenten von Dynamic Media Classic hinzufügen.
uuid: aa5a4735-bfec-43b8-aec0-a0c32bff134f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: managing-assets
discoiquuid: e7b95732-a571-48e8-afad-612059cdbde7
feature: Dynamic Media Classic
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '2866'
ht-degree: 32%

---


# Hinzufügen von Dynamic Media Classic-Funktionen zu Ihrer Seite {#adding-scene-features-to-your-page}

[Adobe Dynamic Media ](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) Classicis ist eine gehostete Lösung zum Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internetanzeigen und Drucken.

In Dynamic Media Classic veröffentlichte Assets können in verschiedenen Viewern Ansicht AEM werden:

* Zoom
* Flyout
* Video
* Bildvorlage
* Bild

Sie können digitale Assets direkt von AEM nach Dynamic Media Classic veröffentlichen und digitale Assets von Dynamic Media Classic nach AEM veröffentlichen.

In diesem Dokument wird beschrieben, wie digitale Assets von AEM nach Dynamic Media Classic und umgekehrt veröffentlicht werden. Die Viewer werden auch detailliert beschrieben. Weitere Informationen zum Konfigurieren von AEM für Dynamic Media Classic finden Sie unter [Integrieren von Dynamic Media Classic mit AEM](/help/sites-administering/scene7.md).

Siehe auch [Hinzufügen von Imagemaps](image-maps.md).

Weitere Informationen über die Arbeit mit Videokomponenten mit AEM finden Sie unter [Video](video.md).

>[!NOTE]
>
>Wenn Dynamic Media Classic-Assets nicht richtig angezeigt werden, stellen Sie sicher, dass das dynamische Medium [deaktiviert](config-dynamic.md#disabling-dynamic-media) ist, und aktualisieren Sie dann die Seite.

## Manuelles Veröffentlichen in Dynamic Media Classic aus Assets {#manually-publishing-to-scene-from-assets}

Sie können digitale Assets wie folgt in Dynamic Media Classic veröffentlichen:

* [In der Assets-Konsole, klassische Benutzeroberfläche](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-the-assets-console) 
* [Von einem Asset, klassische Benutzeroberfläche](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-an-asset) 
* [In der klassischen Benutzeroberfläche außerhalb des Ordners &quot;CQ-Zielgruppe&quot;](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-assets-from-outside-the-cq-target-folder)

>[!NOTE]
>
>AEM veröffentlicht asynchron in Dynamic Media Classic. Nach dem Klicken auf **[!UICONTROL Veröffentlichen]** kann es mehrere Sekunden dauern, bis Ihr Asset in Dynamic Media Classic veröffentlicht wird.


## Dynamic Media Classic-Komponenten {#scene-components}

Die folgenden Dynamic Media Classic-Komponenten sind in AEM verfügbar:

* Zoom
* Flyout (Zoom)
* Bildvorlage
* Bild
* Video

>[!NOTE]
>
>Diese Komponenten sind nicht standardmäßig verfügbar und müssen vor der Verwendung im **[!UICONTROL Design]**-Modus ausgewählt werden.

Nachdem sie im **[!UICONTROL Design]**-Modus verfügbar gemacht wurden, können Sie die Komponenten wie jede andere AEM Ihrer Seite hinzufügen. Assets, die noch nicht in Dynamic Media Classic veröffentlicht wurden, werden in Dynamic Media Classic veröffentlicht, wenn sie sich in einem synchronisierten Ordner, auf einer Seite oder in einer Dynamic Media Classic-Cloud-Konfiguration befinden.

>[!NOTE]
>
>Wenn Sie benutzerdefinierte Viewer erstellen und entwickeln und die Inhaltssuche verwenden, müssen Sie den Parameter **[!UICONTROL allowfullscreen]** explizit hinzufügen.

### Hinweis zur Einstellung von Flash-Viewer {#flash-viewers-end-of-life-notice}

Ab dem 31. Januar 2017 hat Adobe Dynamic Media Classic die Unterstützung für die Flash-Viewer-Plattform eingestellt.

Weitere Informationen zu dieser wichtigen Änderung finden Sie unter [Fragen und Antworten zum Lebenszyklusende von Flash Viewer](https://docs.adobe.com/content/docs/en/aem/6-1/administer/integration/marketing-cloud/scene7/flash-eol.html).

### Hinzufügen einer Dynamic Media Classic-Komponente (Scene7) zu einer Seite {#adding-a-scene-component-to-a-page}

Das Hinzufügen einer Dynamic Media Classic-Komponente (Scene7) zu einer Seite ist dasselbe wie das Hinzufügen einer Komponente zu einer beliebigen Seite. Die Komponenten von Dynamic Media Classic werden in den folgenden Abschnitten ausführlich beschrieben.

**So fügen Sie einer Seite eine Dynamic Media Classic (Scene7)-Komponente hinzu**

1. Öffnen Sie in AEM die Seite, auf der Sie die Komponente Dynamic Media Classic (Scene7) hinzufügen möchten.

1. Wenn keine Dynamic Media Classic-Komponenten verfügbar sind, klicken Sie auf den Modus **[!UICONTROL Design]**, tippen Sie auf eine beliebige Komponente mit blauem Rand, dann auf das Symbol **[!UICONTROL Übergeordnet]** und dann auf das Symbol **[!UICONTROL Konfiguration]**. Wählen Sie unter **[!UICONTROL Parsys (Design)]** alle Dynamic Media Classic-Komponenten aus, um sie verfügbar zu machen, und klicken Sie auf **[!UICONTROL OK.]**

   ![chlimage_1-224](assets/chlimage_1-224.png)

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um zum Modus **[!UICONTROL Bearbeiten]** zurückzukehren.

1. Ziehen Sie eine Komponente aus der Gruppe Dynamic Media Classic im Sidekick auf die Seite an der gewünschten Position.

1. Klicken Sie auf das Symbol **[!UICONTROL Konfiguration]**, um die Komponente zu öffnen.

1. Bearbeiten Sie die Komponente bei Bedarf und klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.
1. Ziehen Sie das Bild oder Video aus dem Inhaltsbrowser auf die Dynamic Media Classic-Komponente, die Sie der Seite hinzugefügt haben.

   >[!NOTE]
   >
   >Nur in der Touch-Benutzeroberfläche müssen Sie das Bild oder Video per Drag &amp; Drop auf die Dynamic Media Classic-Komponente ziehen, die Sie auf der Seite platziert haben. Die Auswahl und Bearbeitung der Komponente Dynamic Media Classic und die anschließende Auswahl des Assets werden nicht unterstützt.

### Hinzufügen interaktiver Anzeigeerlebnisse zu einer responsive Site {#adding-interactive-viewing-experiences-to-a-responsive-website}

Dynamisches Design für Ihre Assets bedeutet, dass Ihre Assets in Abhängigkeit ihrer Anzeigeposition angepasst werden. Mithilfe des dynamischen Designs können dieselben Assets auf mehreren Geräten effektiv dargestellt werden.

Informationen hierzu finden Sie auch unter [Dynamisches Design für Webseiten](/help/sites-developing/responsive.md).

**So fügen Sie einer responsive Site ein interaktives Anzeigeerlebnis hinzu**

1. Melden Sie sich bei AEM an und stellen Sie sicher, dass Sie über [konfigurierte Adobe Dynamic Media Classic-Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) verfügen und dass Dynamic Media Classic-Komponenten verfügbar sind.

   >[!NOTE]
   >
   >Wenn die Dynamic Media Classic-Komponenten nicht verfügbar sind, stellen Sie sicher, dass [sie im Designmodus](/help/sites-authoring/default-components-designmode.md) aktiviert werden.

1. Ziehen Sie auf einer Website mit aktivierten Komponenten **[!UICONTROL Dynamic Media Classic]** eine Komponente **[!UICONTROL Image]** auf die Seite.
1. Wählen Sie die Komponente aus und tippen Sie auf das Konfigurationssymbol.
1. Passen Sie auf der Registerkarte **[!UICONTROL Dynamic Media Classic Settings]** die Haltepunkte an.

   ![chlimage_1-225](assets/chlimage_1-225.png)

1. Bestätigen Sie, dass die Größe der Viewer dynamisch geändert wird und dass alle Interaktionen für Desktopcomputer, Tablets und Mobilgeräte optimiert sind.

### Allgemeine Einstellungen für alle Dynamic Media Classic-Komponenten {#settings-common-to-all-scene-components}

Obwohl die Konfigurationsoptionen variieren, gelten für alle Komponenten [!UICONTROL Dynamic Media Classic] die folgenden:

* **[!UICONTROL Dateiverweis]** : Navigieren Sie zu einer Datei, auf die Sie verweisen möchten. Der Dateiverweis zeigt die Asset-URL und nicht unbedingt die vollständige Dynamic Media Classic-URL einschließlich der URL-Befehle und -Parameter. Sie können in diesem Feld keine Dynamic Media Classic-URL-Befehle und -Parameter hinzufügen. Sie müssen über die entsprechende Funktionalität in der Komponente hinzugefügt werden.
* **[!UICONTROL Breite]** : Hiermit können Sie die Breite einstellen.
* **[!UICONTROL Höhe]**  - Hiermit können Sie die Höhe einstellen.

Sie legen diese Konfigurationsoptionen fest, indem Sie eine Dynamic Media Classic-Komponente öffnen (Dublette-Klicken), z. B. wenn Sie eine Komponente **[!UICONTROL Zoom]** öffnen:

![chlimage_1-226](assets/chlimage_1-226.png)

### Zoom {#zoom}

Die HTML5-Zoomkomponente zeigt ein größeres Bild an, wenn Sie die Schaltfläche **[!UICONTROL +]** drücken.

Das Asset verfügt unten über Zoomwerkzeuge. Tippen Sie zum Vergrößern auf **[!UICONTROL +]**. Tippen Sie zum Reduzieren auf **[!UICONTROL -]**. Durch Tippen auf den **[!UICONTROL x]**- oder den Zurücksetzen-Zoom-Pfeil wird das Bild wieder in der ursprünglichen Größe angezeigt, in der es importiert wurde. Tippen Sie auf die diagonalen Pfeile, um den Vollbildmodus zu aktivieren. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die allen [!UICONTROL Dynamic Media Classic]-Komponenten gemein sind](#settings-common-to-all-scene-components).

![chlimage_1-227](/help/assets/assets/do-not-localize/chlimage_1-227.png)

### Flyout {#flyout}

In der Komponente HTML5 **[!UICONTROL Flyout]** wird das Asset als geteilter Bildschirm angezeigt. den Vermögenswert in der angegebenen Größe belassen; rechts wird der Zoomteil angezeigt. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Mit dieser Komponente können Sie [Einstellungen konfigurieren, die allen Dynamic Media Classic-Komponenten gemein sind](#settings-common-to-all-scene-components).

>[!NOTE]
>
>Wenn Ihre Komponente **[!UICONTROL Flyout]** eine benutzerdefinierte Größe verwendet, wird diese benutzerdefinierte Größe verwendet und das reaktionsfähige Setup der Komponente deaktiviert.
>
>Wenn die Komponente **[!UICONTROL Flyout]** die Standardgröße verwendet, wie in der **[!UICONTROL Design-Ansicht]** festgelegt, wird die Standardgröße verwendet und die Komponente wird gedehnt, um die Seitenlayoutgröße bei aktivierter reaktionsfähiger Einrichtung der Komponente anzupassen. Beachten Sie jedoch, dass es eine Beschränkung für das reaktionsfähige Setup der Komponente gibt. Wenn Sie die Komponente **[!UICONTROL Flyout]** mit reaktionsfähigem Setup verwenden, sollten Sie sie nicht mit voller Seitendehnung verwenden. Andernfalls kann das **[!UICONTROL Flyout]** über den rechten Rand der Seite hinausgehen.

![chlimage_1-228](assets/chlimage_1-228.png)

### Bild {#image}

Mit der Komponente Dynamic Media Classic **[!UICONTROL Image]** können Sie Ihren Bildern Dynamic Media Classic-Funktionen hinzufügen, z. B. Dynamic Media Classic-Modifikatoren, Bild- oder Viewer-Vorgaben und Scharfzeichnen. Die Komponente &quot;Dynamic Media Classic **[!UICONTROL Image]**&quot;ähnelt anderen Bildkomponenten in AEM mit speziellen Funktionen von Dynamic Media Classic. In diesem Beispiel wurde auf das Bild der URL-Modifikator Dynamic Media Classic angewendet, `&op_invert=1`.

![chlimage_1-229](assets/chlimage_1-229.png)

**[!UICONTROL Titel, Alt-Text]**  - Fügen Sie auf der Registerkarte &quot; **** Erweitert&quot;dem Bild einen Titel und alternativem Text für Benutzer hinzu, die Grafiken deaktiviert haben.

**[!UICONTROL URL, Öffnen in]** : Sie können ein Asset vom zum Öffnen eines Links festlegen. Legen Sie die **[!UICONTROL URL]** fest. Geben Sie in **[!UICONTROL Öffnen in]** an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-230](assets/chlimage_1-230.png)

**[!UICONTROL Viewer-Vorgabe]** : Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Dynamic Media Classic-Konfiguration]** : Wählen Sie die Dynamic Media Classic-Konfiguration aus, die Sie zum Abrufen aktiver Bildvorgaben aus dem SPS verwenden möchten.

**[!UICONTROL Bildvorgabe]** : Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Ausgabeformat]** : Wählen Sie das Ausgabeformat des Bilds, z. B. jpeg, aus. In Abhängigkeit des von Ihnen ausgewählten Ausgabeformats stehen Ihnen möglicherweise zusätzliche Konfigurationsoptionen zur Verfügung. Siehe [Best Practices für Bildvorgaben](/help/assets/managing-image-presets.md#image-preset-options).

**[!UICONTROL Scharfzeichnen]** : Wählen Sie aus, wie das Bild scharfgezeichnet werden soll. Das Scharfzeichnen wird unter [Best Practices für Bildvorgaben](/help/assets/managing-image-presets.md#image-preset-options) und in den [Best Practices für das Scharfzeichnen](/help/assets/assets/sharpening_images.pdf) detailliert beschrieben.

**[!UICONTROL URL-Modifikatoren]** : Sie können Bildeffekte ändern, indem Sie zusätzliche Dynamic Media Classic-Bildbefehle bereitstellen. Diese werden unter [Bildvorgaben](/help/assets/managing-image-presets.md) und in der [Befehlsreferenz](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) beschrieben.

**[!UICONTROL Haltepunkte]** : Wenn Ihre Website responsiv ist, sollten Sie die Haltepunkte anpassen. Haltepunkte müssen durch Kommas (,) voneinander getrennt werden.

### Bildvorlage {#image-template}

[Dynamic Media Classic-](https://docs.adobe.com/help/en/dynamic-media-classic/using/template-basics/quick-start-template-basics.html) Bildvorlagen sind Photoshop-Inhalte mit Ebenen, die in Dynamic Media Classic importiert wurden, wobei Inhalt und Eigenschaften auf Variabilität parametrisiert wurden. Mit der Komponente **[!UICONTROL Bildvorlage]** können Sie Bilder importieren und den Text in AEM dynamisch ändern. Zusätzlich können Sie die Komponente **[!UICONTROL Bildvorlage]** dahingehend konfigurieren, dass sie Werte aus dem Clientkontext übernimmt, damit das Bild jedem Benutzer personalisiert angezeigt wird.

Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Komponente zu konfigurieren. Sie können [Einstellungen konfigurieren, die allen Dynamic Media Classic-Komponenten gemeinsam sind](#settings-common-to-all-scene-components) sowie andere in diesem Abschnitt beschriebene Einstellungen.

![chlimage_1-231](assets/chlimage_1-231.png)

**[!UICONTROL Dateiverweis, Breite, Höhe]**  - Siehe Einstellungen, die allen ScDynamic Media Classic7-Komponenten gemeinsam sind.

>[!NOTE]
>
>Dynamic Media Classic-URL-Befehle und -Parameter können der Dateiverweis-URL nicht direkt hinzugefügt werden. Sie können nur auf der Komponenten-Benutzeroberfläche im Bedienfeld **[!UICONTROL Parameter]** definiert werden.

**[!UICONTROL Titel, Alt-Text]** : Fügen Sie auf der Registerkarte &quot;Dynamic Media Classic-Bildvorlage&quot;dem Bild und dem Alternativtext einen Titel für Benutzer hinzu, die Grafiken deaktiviert haben.

**[!UICONTROL URL, Öffnen in]** : Sie können ein Asset vom zum Öffnen eines Links festlegen. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-232](assets/chlimage_1-232.png)

**[!UICONTROL Parameter-Bedienfeld]** : Beim Importieren eines Bildes werden die Parameter vorab mit Informationen aus dem Bild gefüllt. Wenn kein Inhalt vorhanden ist, der dynamisch geändert werden kann, ist dieses Fenster leer.

![chlimage_1-233](assets/chlimage_1-233.png)

#### Dynamisches Ändern von Text {#changing-text-dynamically}

Geben Sie zum dynamischen Ändern des Texts neuen Text in die Felder ein und klicken Sie auf **[!UICONTROL OK.]** In diesem Beispiel lautet der **[!UICONTROL Preis]** 50 $ und der Versand kostet 0,99 $.

![chlimage_1-234](assets/chlimage_1-234.png)

Der Text im Bild ändert sich. Sie können den Text wieder auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** tippen.

![chlimage_1-235](assets/chlimage_1-235.png)

#### Ändern von Text zum Berücksichtigen des Werts eines Clientkontextwerts {#changing-text-to-reflect-the-value-of-a-client-context-value}

Um ein Feld mit einem Clientkontextwert zu verknüpfen, tippen Sie auf **[!UICONTROL Wählen Sie]**, um das Client-Kontextmenü zu öffnen, wählen Sie den Clientkontext aus und tippen Sie auf **[!UICONTROL OK.]** In diesem Beispiel ändert sich der Name auf Grundlage der Verknüpfung des Namens mit dem formatierten Namen im Profil.

![chlimage_1-236](assets/chlimage_1-236.png)

Der Text berücksichtigt den Namen des aktuell angemeldeten Benutzers. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** klicken.

![chlimage_1-237](assets/chlimage_1-237.png)

#### Erstellen der Dynamic Media Classic-Bildvorlage als Link {#making-the-scene-image-template-a-link}

1. Tippen Sie auf der Seite mit der Komponente Dynamic Media Classic **[!UICONTROL Bildvorlage]** auf **[!UICONTROL Bearbeiten.]**
1. Geben Sie im Feld **[!UICONTROL URL]** die URL ein, zu der Benutzer navigieren, wenn auf das Bild getippt wird. Wählen Sie im Feld **[!UICONTROL Öffnen in]** aus, ob das Ziel (in einem neuen oder im selben Fenster) geöffnet werden soll.

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. Tippen Sie auf **[!UICONTROL OK]**.

### Komponente „Video“{#video-component}

Die Komponente Dynamic Media Classic **[!UICONTROL Video]** (verfügbar im Abschnitt &quot;Dynamic Media Classic&quot;des Sidekick) verwendet Geräte- und Bandbreitenerkennung, um das richtige Video für jeden Bildschirm bereitzustellen. Bei dieser Komponente handelt es sich um einen HTML5-Video-Player. Es ist ein einzelner Viewer, der kanalübergreifend verwendet werden kann.

Er kann für adaptive Videosets, ein einzelnes MP4-Video oder ein einzelnes F4V-Video verwendet werden.

Weitere Informationen zur Funktionsweise von Videos bei der Dynamic Media Classic-Integration finden Sie unter [Video](s7-video.md). Weitere Informationen finden Sie unter [Dynamic Media Classic-Videokomponente versus Foundation-Videokomponente](s7-video.md).

![chlimage_1-239](assets/chlimage_1-239.png)

### Bekannte Einschränkungen für die Videokomponente {#known-limitations-for-the-video-component}

Adobe DAM und WCM zeigen an, ob ein Hauptquellvideo hochgeladen wurde. Sie zeigen diese Proxy-Assets nicht an:

* Dynamic Media Classic-kodierte Darstellungen
* Adaptive Dynamic Media Classic-Videosets

Wenn Sie ein adaptives Videoset mit der Dynamic Media Classic-Videokomponente verwenden, müssen Sie die Größe der Komponente an die Abmessungen des Videos anpassen.

## Dynamic Media Classic Content Browser {#scene-content-browser}

Mit dem Dynamic Media Classic-Inhaltsbrowser können Sie Inhalte aus Dynamic Media Classic direkt in AEM Ansicht verwenden. Um auf den Inhaltsbrowser zuzugreifen, wählen Sie in der **[!UICONTROL Inhaltssuche]** **[!UICONTROL Dynamic Media Classic]** in der touchoptimierten Benutzeroberfläche oder in der klassischen Benutzeroberfläche das Symbol **[!UICONTROL S7]** aus. Die Funktionalität ist zwischen den beiden Benutzeroberflächen identisch.

Wenn Sie über mehrere Konfigurationen verfügen, zeigt AEM standardmäßig die [Standardkonfiguration](/help/sites-administering/scene7.md#configuring-a-default-configuration) an. Sie können verschiedene Konfigurationen direkt im Dynamic Media Classic-Inhaltsbrowser im Dropdown-Menü auswählen.

>[!NOTE]
>
>* Assets, die sich im Ad-hoc-Ordner befinden, werden nicht im Dynamic Media Classic-Inhaltsbrowser angezeigt.
>* Wenn [Sichere Vorschau aktiviert ist, werden veröffentlichte und unveröffentlichte Assets in Dynamic Media Classic im Dynamic Media Classic-Inhaltsbrowser angezeigt.](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene)
>* Wenn Sie im Inhaltsbrowser weder das Symbol **[!UICONTROL Dynamic Media Classic]** noch das Symbol **[!UICONTROL S7]** als Option sehen, müssen Sie [Dynamic Media Classic für die Verwendung mit AEM](/help/sites-administering/scene7.md) konfigurieren.
>* Für Videos unterstützt der Dynamic Media Classic-Inhaltsbrowser:

   >
   >   
   * Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabeformaten
   >   * Einzelnes MP4-Video
   >   * Einzelnes F4V-Video


### Durchsuchen von Inhalten in der touchoptimierten Benutzeroberfläche {#browsing-content-in-the-touch-optimized-ui}

Sie können über die Touch-optimierte oder klassische Benutzeroberfläche auf den Inhaltsbrowser zugreifen. Zurzeit weist die Touch-optimierte Benutzeroberfläche die folgende Begrenzung auf:

* FXG- und Flash-Assets aus Dynamic Media Classic werden nicht unterstützt.

Durchsuchen Sie die Dynamic Media Classic-Assets, indem Sie im dritten Dropdownmenü **[!UICONTROL Dynamic Media Classic]** auswählen. Dynamic Media Classic wird nicht in der Liste angezeigt, wenn Sie die Dynamic Media Classic/AEM-Integration nicht konfiguriert haben.

>[!NOTE]
>
>* Der Content Browser von Dynamic Media Classic lädt etwa 100 Assets und sortiert sie nach Namen.
>* Wenn Sie einen sicheren Vorschauserver festgelegt haben, verwendet der Browser diesen Vorschauserver zum Darstellen von Miniaturansichten und Assets.

>



![chlimage_1-240](assets/chlimage_1-240.png)

Zusätzlich können Sie Informationen über Auflösung, Größe, Tage seit der Änderung und Dateiname erhalten, indem Sie den Mauszeiger über das Asset im Browser halten.

![chlimage_1-241](assets/chlimage_1-241.png)

* Bei adaptiven Videosets und -vorlagen werden für Miniaturansichten keine Größeninformationen generiert.
* Bei adaptiven Videosets wird für Miniaturansichten keine Auflösung generiert.

### Suchen nach Dynamic Media Classic-Assets mit dem Inhaltsbrowser {#searching-for-scene-assets-with-the-content-browser}

Die Suche nach Dynamic Media Classic-Assets funktioniert ähnlich wie die Suche nach AEM Assets. Bei der Suche sehen Sie jedoch eine Remote-Ansicht der Assets im Dynamic Media Classic-System, anstatt sie direkt in AEM zu importieren.

Sie können die klassische oder Touch-optimierte Benutzeroberfläche verwenden, um Assets anzuzeigen und nach ihnen zu suchen. In Abhängigkeit von der Oberfläche unterscheidet sich die Art und Weise der Suche etwas.

Wenn Sie auf einer der Benutzeroberflächen suchen, können Sie nach den folgenden Kriterien filtern (wird hier in der Touch-optimierten Benutzeroberfläche gezeigt):

**[!UICONTROL Suchbegriffe]**  eingeben - Sie können Assets nach Namen suchen. Bei der Suche entsprechen die von Ihnen eingegebenen Keywords dem Beginn des Dateinamens. Zum Beispiel führt die Eingabe des Worts „schwimmen“ dazu, dass nach Asset-Dateinamen gesucht wird, die mit diesen Buchstaben in dieser Reihenfolge beginnen. Tippen Sie auf &quot;Geben Sie ein&quot;, nachdem Sie den Begriff eingegeben haben, um das Asset zu finden.

![chlimage_1-242](assets/chlimage_1-242.png)

**[!UICONTROL Ordner/Pfad]**  - Der Name des angezeigten Ordners hängt von der ausgewählten Konfiguration ab. Sie können einen Drilldown zu niedrigeren Ebenen durchführen, indem Sie auf das Ordnersymbol tippen, einen Unterordner auswählen und dann auf das Häkchen tippen, um ihn auszuwählen.

Wenn Sie ein Keyword eingeben und einen Ordner auswählen, durchsucht AEM diesen Ordner und die zugehörigen Unterordner. Wenn Sie jedoch bei der Suche keine Keywords eingeben, wird durch die Auswahl des Ordners das Asset nur in diesem Ordner angezeigt und nicht in Unterordnern.

Standardmäßig durchsucht AEM den ausgewählten Ordner und alle Unterordner.

![chlimage_1-243](assets/chlimage_1-243.png)

**[!UICONTROL Asset]** -Typ: Wählen Sie  **[!UICONTROL Dynamic Media]** Classic, um Dynamic Media Classic-Inhalte zu durchsuchen. Diese Option ist nur verfügbar, wenn Dynamic Media Classic konfiguriert wurde.

![chlimage_1-244](assets/chlimage_1-244.png)

**[!UICONTROL Konfiguration]** : Wenn Sie mehr als eine Dynamic Media Classic-Konfiguration in  [!UICONTROL Cloud Services] definiert haben, können Sie sie hier auswählen. Der Ordner ändert sich anhand der von Ihnen ausgewählten Konfiguration.

![chlimage_1-245](assets/chlimage_1-245.png)

**[!UICONTROL Asset-Typ]** : Im Dynamic Media Classic-Browser können Sie die Ergebnisse filtern, um Folgendes einzuschließen: Bilder, Vorlagen, Videos und adaptive Videosets. Wenn Sie keinen Asset-Typ auswählen, durchsucht AEM standardmäßig alle Asset-Typen.

![chlimage_1-246](assets/chlimage_1-246.png)

>[!NOTE]
>
>* Auf der klassischen Benutzeroberfläche können Sie auch nach **Flash** und **FXG** suchen. Das Filtern nach diesen auf der Touch-optimierten Benutzeroberfläche wird derzeit nicht unterstützt.
   >
   >
* Beim Durchsuchen eines Videos suchen Sie nach einem einzelnen Ausgabeformat. Die Ergebnisse geben die ursprüngliche Darstellung (nur &amp;ast;.mp4) und die kodierte Darstellung zurück.
>* Beim Durchsuchen eines adaptiven Videosets werden der Ordner und alle Unterordner durchsucht, allerdings nur, wenn Sie der Suche einen Suchbegriff hinzugefügt haben. Wenn Sie kein Keyword hinzugefügt haben, durchsucht AEM nicht die Unterordner.

>



**[!UICONTROL Veröffentlichungsstatus]** : Sie können nach Assets basierend auf dem Veröffentlichungsstatus filtern:  **[!UICONTROL Veröffentlichung]** rückgängig machen oder  **[!UICONTROL veröffentlicht.]** Wenn Sie keinen  **[!UICONTROL Veröffentlichungsstatus]** auswählen, durchsucht AEM standardmäßig alle Veröffentlichungsstatus.

![chlimage_1-247](assets/chlimage_1-247.png)

