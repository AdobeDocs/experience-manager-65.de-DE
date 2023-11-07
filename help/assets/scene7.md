---
title: Hinzufügen von Dynamic Media Classic-Funktionen zu Seiten
description: Hinzufügen von Dynamic Media Classic-Funktionen und -Komponenten zu einer Seite in Adobe Experience Manager.
uuid: aa5a4735-bfec-43b8-aec0-a0c32bff134f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: managing-assets
discoiquuid: e7b95732-a571-48e8-afad-612059cdbde7
feature: Dynamic Media Classic
role: User, Admin
mini-toc-levels: 3
exl-id: 815f577d-4774-4830-8baf-0294bd085b83
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '2845'
ht-degree: 98%

---

# Hinzufügen von Dynamic Media Classic-Funktionen zu Seiten {#adding-scene-features-to-your-page}

[Adobe Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/home.html?lang=de) ist eine gehostete Lösung für die Verwaltung, Optimierung, Veröffentlichung und Bereitstellung von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internet-verbundene Anzeigen und Ausdrucke.

Sie können Experience Manager-Assets, die in Dynamic Media Classic veröffentlicht wurden, in verschiedenen Viewern anzeigen:

* Zoom
* Flyout
* Video
* Bildvorlage
* Bild

Sie können digitale Assets direkt aus Experience Manager in Dynamic Media Classic veröffentlichen und Sie können digitale Assets aus Dynamic Media Classic in Experience Manager veröffentlichen.

In diesem Dokument wird beschrieben, wie Sie digitale Assets aus Experience Manager in Dynamic Media Classic veröffentlichen und umgekehrt. Die Viewer werden auch detailliert beschrieben. Informationen zum Konfigurieren von Experience Manager für Dynamic Media Classic finden Sie unter [Integrieren von Dynamic Media Classic mit Experience Manager](/help/sites-administering/scene7.md).

Siehe auch [Hinzufügen von Imagemaps](image-maps.md).

Weitere Informationen über die Verwendung von Videokomponenten mit Experience Manager finden Sie unter [Video](video.md).

>[!NOTE]
>
>Wenn Dynamic Media Classic-Assets nicht korrekt angezeigt werden, stellen Sie sicher, dass Dynamic Media [deaktiviert](config-dynamic.md#disabling-dynamic-media) ist, und aktualisieren Sie die Seite.

## Manuelles Veröffentlichen von Assets in Dynamic Media Classic {#manually-publishing-to-scene-from-assets}

Sie können digitale Assets wie folgt in Dynamic Media Classic veröffentlichen:

* [In der Assets-Konsole, klassische Benutzeroberfläche](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-the-assets-console)
* [Von einem Asset, klassische Benutzeroberfläche](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-from-an-asset)
* [Von außerhalb des CQ-Zielordner, klassische Benutzeroberfläche](/help/sites-classic-ui-authoring/manage-assets-classic-s7.md#publishing-assets-from-outside-the-cq-target-folder)

>[!NOTE]
>
>Experience Manager veröffentlicht asynchron in Dynamic Media Classic. Nachdem Sie **[!UICONTROL Veröffentlichen]** ausgewählt haben, dauert es mehrere Sekunden, bis Ihr Asset in Dynamic Media Classic veröffentlicht wird.
>

## Dynamic Media Classic-Komponenten {#scene-components}

Die folgenden Dynamic Media Classic-Komponenten sind in Experience Manager verfügbar:

* Zoom
* Flyout (Zoom)
* Bildvorlage
* Bild
* Video

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar und müssen im Modus **[!UICONTROL Design]** ausgewählt werden, bevor sie verwendet werden können.

Nachdem sie im Modus **[!UICONTROL Design]** zur Verfügung gestellt wurden, können Sie die Komponenten wie jede andere Experience Manager-Komponente zu Ihrer Seite hinzufügen. Assets, die noch nicht in Dynamic Media Classic veröffentlicht wurden, werden in Dynamic Media Classic veröffentlicht, wenn sie sich in einem synchronisierten Ordner oder auf einer Seite befinden oder eine Dynamic Media Classic-Cloud-Konfiguration aufweisen.

>[!NOTE]
>
>Beim Erstellen und Entwickeln von benutzerdefinierten Viewern und beim Verwenden des Content Finders müssen Sie den Parameter `allowfullscreen` explizit hinzufügen.

### Hinweis zur Einstellung von Flash-Viewern {#flash-viewers-end-of-life-notice}

Am 31. Januar 2017 hat Adobe Dynamic Media Classic die Unterstützung für die Flash-Viewer-Plattform beendet.

### Hinzufügen einer Dynamic Media Classic-Komponente (Scene7) zu einer Seite {#adding-a-scene-component-to-a-page}

Das Hinzufügen einer Dynamic Media Classic-Komponente (Scene7) entspricht dem Hinzufügen einer Komponente zu einer Seite. Dynamic Media Classic-Komponenten werden in den folgenden Abschnitten ausführlich beschrieben.

**So fügen Sie eine Dynamic Media Classic-Komponente (Scene7) zu einer Seite hinzu**:

1. Öffnen Sie in Experience Manager die Seite, auf der Sie die Komponente **[!UICONTROL Dynamic Media Classic (Scene7)]** hinzufügen möchten.

1. Wenn keine Dynamic Media Classic-Komponenten verfügbar sind, wählen Sie den Modus **[!UICONTROL Design]**, dann eine beliebige Komponente mit einem blauen Rahmen, anschließend das Symbol **[!UICONTROL Übergeordnetes Element]** und das Symbol **[!UICONTROL Konfiguration]** aus. Wählen Sie in **[!UICONTROL ParSys (Design)]** alle Dynamic Media Classic-Komponenten aus, um sie verfügbar zu machen, und wählen Sie **[!UICONTROL OK]** aus.

   ![chlimage_1-224](assets/chlimage_1-224.png)

1. Wählen Sie **[!UICONTROL Bearbeiten]** aus, damit Sie zum Modus **[!UICONTROL Bearbeiten]** zurückkehren können.

1. Ziehen Sie eine Komponente aus der Dynamic Media Classic-Gruppe im Sidekick an die gewünschte Position auf die Seite.

1. Wählen Sie das Symbol **[!UICONTROL Konfiguration]** aus, damit Sie die Komponente öffnen können.

1. Bearbeiten Sie die Komponente nach Bedarf und wählen Sie **[!UICONTROL OK]** aus, um die Änderungen zu speichern.
1. Ziehen Sie Ihr Bild oder Video aus dem Inhaltsbrowser auf die Dynamic Media Classic-Komponente, die Sie zur Seite hinzugefügt haben.

   >[!NOTE]
   >
   >Nur in der Touch-optimierten Benutzeroberfläche müssen Sie das Bild oder Video auf die Dynamic Media Classic-Komponente ziehen, die Sie zur Seite hinzugefügt haben. Es ist nicht möglich, zunächst die Dynamic Media Classic-Komponente auszuwählen und zu bearbeiten und anschließend das Asset zu auszuwählen.

### Hinzufügen eines interaktiven Anwendererlebnisses zu einer responsiven Site {#adding-interactive-viewing-experiences-to-a-responsive-website}

Ein responsives Design für Ihre Assets bedeutet, dass Ihre Assets in Abhängigkeit ihrer Anzeigeposition angepasst werden. Mithilfe des dynamischen Designs können dieselben Assets auf mehreren Geräten effektiv dargestellt werden.

Informationen hierzu finden Sie auch unter [Responsives Design für Web-Seiten](/help/sites-developing/responsive.md).

**So fügen Sie einer responsiven Site ein interaktives Anwendererlebnis hinzu:**

1. Melden Sie sich bei Experience Manager an und stellen Sie sicher, dass Sie [Cloud-Services für Adobe Dynamic Media Classic konfiguriert haben](/help/sites-administering/scene7.md#configuring-scene-integration) und dass Dynamic Media Classic-Komponenten verfügbar sind.

   >[!NOTE]
   >
   >Wenn keine Dynamic Media Classic-Komponenten verfügbar sind, müssen Sie sie [mit dem Designmodus aktivieren](/help/sites-authoring/default-components-designmode.md).

1. Ziehen Sie auf einer Website mit aktivierten **[!UICONTROL Dynamic Media Classic]**-Komponenten eine **[!UICONTROL Bild]**-Komponente auf die Seite.
1. Wählen Sie die Komponente und dann das Konfigurationssymbol aus.
1. Passen Sie auf der Registerkarte **[!UICONTROL Dynamic Media Classic-Einstellungen]** die Breakpoints an.

   ![chlimage_1-225](assets/chlimage_1-225.png)

1. Bestätigen Sie, dass die Größe der Viewer dynamisch geändert wird und dass alle Interaktionen für Desktop-Computer, Tablets und Mobilgeräte optimiert sind.

### Gemeinsame Einstellungen für alle Dynamic Media Classic-Komponenten {#settings-common-to-all-scene-components}

Auch wenn sich die Konfigurationsoptionen unterscheiden, sind folgende Einstellungen für alle [!UICONTROL Dynamic Media Classic]-Komponenten gleich:

* **[!UICONTROL Dateiverweis]**: Navigieren Sie zu einer Datei, die Sie referenzieren möchten. Der Dateiverweis zeigt die Asset-URL und nicht zwangsläufig die vollständige Dynamic Media Classic-URL, einschließlich der URL-Befehle und -Parameter. Das Hinzufügen von Dynamic Media Classic-URL-Befehlen und -Parametern ist in diesem Feld nicht möglich. Stattdessen fügen Sie sie über die entsprechende Funktionalität in der Komponente hinzu.
* **[!UICONTROL Breite]**: Hier können Sie die Breite festlegen.
* **[!UICONTROL Höhe]**: Hier können Sie die Höhe festlegen.

Sie können diese Konfigurationsoptionen festlegen, indem Sie eine Dynamic Media Classic-Komponente (per Doppelklick) öffnen. Zum Beispiel beim Öffnen einer **[!UICONTROL Zoom]**-Komponente:

![chlimage_1-226](assets/chlimage_1-226.png)

### Zoom {#zoom}

Die HTML5-Zoom-Komponente zeigt ein größeres Bild an, wenn Sie die Taste **[!UICONTROL +]** drücken.

Das Asset verfügt unten über Zoomwerkzeuge. Wählen Sie **[!UICONTROL +]** aus, wenn Sie die Anzeige vergrößern möchten, und **[!UICONTROL -]**, wenn Sie sie verkleinern möchten. Durch Tippen auf **[!UICONTROL x]** oder den Pfeil zum Zurücksetzen des Zooms wird das Bild auf die ursprüngliche Größe zurückgesetzt, in der es importiert wurde. Wählen Sie die diagonalen Pfeile aus, um es im Vollbildmodus anzuzeigen. Wählen Sie **[!UICONTROL Bearbeiten]** aus, damit Sie die Komponente konfigurieren können. Mit dieser Komponente können Sie die [gemeinsamen Einstellungen für alle [!UICONTROL Dynamic Media Classic]-Komponenten](#settings-common-to-all-scene-components) konfigurieren.

![chlimage_1-227](/help/assets/assets/do-not-localize/chlimage_1-227.png)

### Flyout {#flyout}

In der HTML5-**[!UICONTROL Flyout]**-Komponente wird das Asset als geteilter Bildschirm angezeigt. Links wird das Asset in der angegebenen Größe angezeigt, rechts wird der Zoom-Teil dargestellt. Wählen Sie **[!UICONTROL Bearbeiten]** aus, damit Sie die Komponente konfigurieren können. Mit dieser Komponente können Sie die [gemeinsamen Einstellungen für alle Dynamic Media Classic-Komponenten](#settings-common-to-all-scene-components) konfigurieren.

>[!NOTE]
>
>Wenn die **[!UICONTROL Flyout]**-Komponente eine benutzerdefinierte Größe aufweist, wird diese benutzerdefinierte Größe verwendet und das responsive Setup der Komponente wird deaktiviert.
>
>Wenn die **[!UICONTROL Flyout]**-Komponente die Standardgröße aufweist, wie dies in der **[!UICONTROL Entwurfsansicht]** festgelegt ist, wird die Standardgröße verwendet und die Komponente wird gedehnt, um die Größe des Seiten-Layouts im dynamischen Setup der aktivierten Komponente zu berücksichtigen. Das responsive Setup der Komponente weist eine Einschränkung auf. Nutzen Sie beim Verwenden der **[!UICONTROL Flyout]**-Komponente mit responsivem Setup nicht die vollständige Seitendehnung. Andernfalls ragt das **[!UICONTROL Flyout]** über den rechten Rand der Seite hinaus.

![chlimage_1-228](assets/chlimage_1-228.png)

### Bild {#image}

Mit der Dynamic Media Classic-Komponente **[!UICONTROL Bild]** können Sie Bildern Dynamic Media Classic-Funktionen hinzufügen, z. B. Dynamic Media Classic-Modifikatoren, Bild- oder Viewer-Vorgaben und Scharfzeichnen. Die Dynamic Media Classic-Komponente **[!UICONTROL Bild]** ähnelt anderen Bildkomponenten in Experience Manager mit speziellen Dynamic Media Classic-Funktionen. In diesem Beispiel wurde auf das Bild der Dynamic Media Classic-URL-Modifikator `&op_invert=1` angewendet.

![chlimage_1-229](assets/chlimage_1-229.png)

**[!UICONTROL Titel, ALT-Text]**: Fügen Sie auf der Registerkarte **[!UICONTROL Erweitert]** einen Titel zum Bild und alternativen Text für die Benutzer hinzu, die Grafiken deaktiviert haben.

**[!UICONTROL URL, Öffnen in]**: Sie können ein Asset so einrichten, dass ein Link geöffnet wird. Legen Sie die **[!UICONTROL URL]** fest. Geben Sie in **[!UICONTROL Öffnen in]** an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-230](assets/chlimage_1-230.png)

**[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Dynamic Media Classic-Konfiguration]**: Wählen Sie die Dynamic Media Classic-Konfiguration aus, die Sie zum Abrufen aktiver Bildvorgaben aus SPS verwenden möchten.

**[!UICONTROL Bildvorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Bildvorgabe aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie sichtbar machen. Siehe [Verwalten von Bildvorgaben](/help/assets/managing-image-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

**[!UICONTROL Ausgabeformat]** - Wählen Sie das Ausgabeformat des Bildes aus, z. B. jpeg. In Abhängigkeit des von Ihnen ausgewählten Ausgabeformats stehen Ihnen zusätzliche Konfigurationsoptionen zur Verfügung. Siehe [Best Practices für Bildvorgaben](/help/assets/managing-image-presets.md#image-preset-options).

**[!UICONTROL Scharfzeichnen]**: Wählen Sie aus, wie Sie das Bild scharfzeichnen möchten. Das Scharfzeichnen wird unter [Best Practices für Bildvorgaben](/help/assets/managing-image-presets.md#image-preset-options) und [Best Practices für das Scharfzeichnen](/help/assets/assets/sharpening_images.pdf) detailliert beschrieben.

**[!UICONTROL URL-Modifikatoren]**: Sie können Bildeffekte ändern, indem Sie zusätzliche Dynamic Media Classic-Bildbefehle bereitstellen. Diese Befehle werden unter [Bildvorgaben](/help/assets/managing-image-presets.md) und in der [Befehlsreferenz](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=de) beschrieben.

**[!UICONTROL Breakpoints]**: Wenn Ihre Website responsiv ist, können Sie die Breakpoints anpassen. Breakpoints müssen durch Kommas (,) voneinander getrennt werden.

### Bildvorlage {#image-template}

[Dynamic Media Classic-Bildvorlagen](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/template-basics/quick-start-template-basics.html?lang=de) sind mehrschichtige Photoshop-Inhalte, die in Dynamic Media Classic importiert wurden, wo Inhalte und Eigenschaften für Variabilität parametrisiert wurden. Mit der Komponente **[!UICONTROL Bildvorlage]** können Sie Bilder importieren und den Text in Experience Manager dynamisch ändern. Zusätzlich können Sie die Komponente **[!UICONTROL Bildvorlage]** dahingehend konfigurieren, dass sie Werte aus dem Client-Kontext übernimmt, damit das Bild jedem Benutzer personalisiert angezeigt wird.

Wählen Sie **[!UICONTROL Bearbeiten]** aus, wenn Sie die Komponente konfigurieren möchten. Sie können [Einstellungen, die für alle Dynamic Media Classic-Komponenten gelten](#settings-common-to-all-scene-components), und andere Einstellungen, die in diesem Abschnitt beschrieben werden, konfigurieren.

![chlimage_1-231](assets/chlimage_1-231.png)

**[!UICONTROL Dateiverweis, Breite, Höhe]**: Sehen Sie sich die Einstellungen an, die für alle Dynamic Media Classic Scene7-Komponenten gelten.

>[!NOTE]
>
>Dynamic Media Classic-URL-Befehle und -Parameter können nicht direkt zur Dateiverweis-URL hinzugefügt werden. Sie können nur auf der Komponenten-Benutzeroberfläche im Bedienfeld **[!UICONTROL Parameter]** definiert werden.

**[!UICONTROL Titel, ALT-Text]**: Fügen Sie auf der Registerkarte für Dynamic Media Classic-Bildvorlagen einen Titel zum Bild und alternativen Text für die Benutzer hinzu, die Grafiken deaktiviert haben.

**[!UICONTROL URL, Öffnen in]**: Sie können ein Asset so einrichten, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

![chlimage_1-232](assets/chlimage_1-232.png)

**[!UICONTROL Bedienfeld „Parameter“]**: Beim Importieren eines Bildes werden die Parameter mit den Informationen aus dem Bild vorab ausgefüllt. Wenn kein Inhalt vorhanden ist, der dynamisch geändert werden kann, ist dieses Fenster leer.

![chlimage_1-233](assets/chlimage_1-233.png)

#### Dynamisches Ändern von Text {#changing-text-dynamically}

Geben Sie zum dynamischen Ändern von Text neuen Text in die Felder ein und klicken Sie auf **[!UICONTROL OK]**. In diesem Beispiel lautet der **[!UICONTROL Preis]** 50 $ und der Versand kostet 0,99 $.

![chlimage_1-234](assets/chlimage_1-234.png)

Der Text im Bild ändert sich. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** tippen.

![chlimage_1-235](assets/chlimage_1-235.png)

#### Ändern von Text zum Berücksichtigen des Werts eines Client-Kontextwerts {#changing-text-to-reflect-the-value-of-a-client-context-value}

Wählen Sie zum Verknüpfen eines Felds mit einem Client-Kontextwert **[!UICONTROL Auswählen]** aus, um das Client-Kontextmenü zu öffnen. Wählen Sie den Client-Kontext und dann **[!UICONTROL OK]** aus. In diesem Beispiel ändert sich der Name auf Grundlage der Verknüpfung des Namens mit dem formatierten Namen im Profil.

![chlimage_1-236](assets/chlimage_1-236.png)

Der Text berücksichtigt den Namen des aktuell angemeldeten Benutzers. Sie können den Text auf den ursprünglichen Wert zurücksetzen, indem Sie neben dem Feld auf **[!UICONTROL Zurücksetzen]** klicken.

![chlimage_1-237](assets/chlimage_1-237.png)

#### Festlegen der Dynamic Media Classic-Bildvorlage als Verknüpfung {#making-the-scene-image-template-a-link}

1. Wählen Sie auf der Seite mit der Dynamic Media Classic-Komponente **[!UICONTROL Bildvorlage]** die Option **[!UICONTROL Bearbeiten]** aus.
1. Geben Sie im Feld **[!UICONTROL URL]** die URL ein, zu der Benutzer wechseln, wenn sie auf das Bild tippen. Wählen Sie im Feld **[!UICONTROL Öffnen in]** aus, ob das Ziel (in einem neuen oder im selben Fenster) geöffnet werden soll.

   ![chlimage_1-238](assets/chlimage_1-238.png)

1. Klicken Sie auf **[!UICONTROL OK]**.

### Komponente „Video“ {#video-component}

Die Dynamic Media Classic-Komponente **[!UICONTROL Video]** (verfügbar über den Dynamic Media Classic-Abschnitt im Sidekick) verwendet die Geräte- und Bandbreitenerkennung, damit auf jedem Bildschirm das richtige Video bereitgestellt wird. Bei dieser Komponente handelt es sich um einen HTML5-Video-Player. Es ist ein einzelner Viewer, der kanalübergreifend verwendet werden kann.

Er kann für adaptive Videosets, ein einzelnes MP4-Video oder ein einzelnes F4V-Video verwendet werden.

Weitere Informationen darüber, wie Videos mit Dynamic Media Classic-Integration funktionieren, finden Sie unter [Video](s7-video.md). Vergleichen Sie zudem [die Dynamic Media Classic-Videokomponente mit der Foundation-Videokomponente](s7-video.md).

![chlimage_1-239](assets/chlimage_1-239.png)

### Bekannte Einschränkungen der Videokomponente {#known-limitations-for-the-video-component}

Adobe DAM und WCM zeigen, ob ein primäres Quellvideo hochgeladen wurde. Sie zeigen diese Proxy-Assets nicht an:

* Dynamic Media Classic-kodierte Ausgabedarstellungen
* Adaptive Dynamic Media Classic-Videosets

Wenn Sie ein adaptives Videoset mit der Dynamic Media Classic-Videokomponente verwenden, müssen Sie die Größe der Komponente ändern, damit sie zu den Abmessungen des Videos passen.

## Dynamic Media Classic-Inhaltsbrowser {#scene-content-browser}

Mit dem Dynamic Media Classic-Inhaltsbrowser können Sie Inhalte aus Dynamic Media Classic direkt in Experience Manager anzeigen. Wählen Sie für den Zugriff auf den Inhaltsbrowser in der **[!UICONTROL Inhaltssuche]** die Option **[!UICONTROL Dynamic Media Classic]** auf der Touch-optimierten Benutzeroberfläche oder das Symbol **[!UICONTROL S7]** auf der klassischen Benutzeroberfläche aus. Die Funktionalität ist auf den beiden Benutzeroberflächen identisch.

Wenn Sie über mehrere Konfigurationen verfügen, zeigt Experience Manager standardmäßig die [Standardkonfiguration](/help/sites-administering/scene7.md#configuring-a-default-configuration) an. Sie können unterschiedliche Kategorien direkt im Dynamic Media Classic-Inhaltsbrowser im Dropdown-Menü auswählen.

>[!NOTE]
>
>* Assets im bedarfsabhängigen Ordner werden nicht im Dynamic Media Classic-Inhaltsbrowser angezeigt.
>* Wenn [Sichere Vorschau](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) aktiviert ist, werden in Dynamic Media Classic veröffentlichte und nicht veröffentlichte Assets im Dynamic Media Classic-Inhaltsbrowser angezeigt.
>* Wenn Sie **[!UICONTROL Dynamic Media Classic]** oder das Symbol **[!UICONTROL S7]** nicht als Option im Inhaltsbrowser sehen, müssen Sie [Dynamic Media Classic für die Verwendung mit Experience Manager konfigurieren](/help/sites-administering/scene7.md).
>* Für Videos unterstützt der Dynamic Media Classic-Inhaltsbrowser Folgendes:
>
>   * Adaptive Videosets: Container von allen für die bildschirmübergreifende optimierte Wiedergabe erforderlichen Videoausgabedarstellungen
>   * Einzelnes MP4-Video
>   * Einzelnes F4V-Video

### Durchsuchen von Inhalt auf der Touch-optimierten Benutzeroberfläche {#browsing-content-in-the-touch-optimized-ui}

Sie können entweder über die Touch-optimierte oder die klassische Benutzeroberfläche auf den Inhaltsbrowser zugreifen. Derzeit gilt für die Touch-optimierte Funktion die folgende Einschränkung:

* FXG- und Flash-Assets aus Dynamic Media Classic werden nicht unterstützt.

Durchsuchen Sie Dynamic Media Classic-Assets, indem Sie **[!UICONTROL Dynamic Media Classic]** aus dem dritten Dropdown-Menü auswählen. Dynamic Media Classic wird nicht in der Liste angezeigt, wenn Sie die Dynamic Media Classic/Experience Manager-Integration nicht konfiguriert haben.

>[!NOTE]
>
>* Der Dynamic Media Classic-Inhaltsbrowser lädt etwa 100 Assets und sortiert sie nach Namen.
>* Wenn Sie einen sicheren Vorschauserver festgelegt haben, verwendet der Browser diesen Vorschauserver zum Darstellen von Miniaturansichten und Assets.
>

![chlimage_1-240](assets/chlimage_1-240.png)

Zusätzlich können Sie Informationen über Auflösung, Größe, Tage seit der Änderung und Dateiname erhalten, indem Sie den Mauszeiger über das Asset im Browser halten.

![chlimage_1-241](assets/chlimage_1-241.png)

* Für adaptive Videosets und Vorlagen werden keine Größeninformationen für Miniaturansichten generiert.
* Für adaptive Videosets wird keine Auflösung für Miniaturansichten generiert.

### Suchen nach Dynamic Media Classic-Assets mit dem Inhaltsbrowser {#searching-for-scene-assets-with-the-content-browser}

Die Suche nach Assets in Dynamic Media Classic ähnelt der Suche nach Assets in Experience Manager Assets. Während der Suche wird Ihnen tatsächlich eine Remote-Ansicht der Assets im Dynamic Media Classic-System angezeigt. Es erfolgt kein direkter Import in Experience Manager.

Sie können entweder die klassische oder die Touch-optimierte Benutzeroberfläche verwenden, um Assets anzuzeigen und nach ihnen zu suchen. Je nach Benutzeroberfläche unterscheidet sich die Suchweise geringfügig.

Wenn Sie auf einer der Benutzeroberflächen suchen, können Sie nach den folgenden Kriterien filtern (wird hier in der Touch-optimierten Benutzeroberfläche gezeigt):

**[!UICONTROL Keywords eingeben]**: Sie können Assets nach Namen suchen. Bei der Suche entsprechen die von Ihnen eingegebenen Keywords dem Anfang des Dateinamens. Zum Beispiel führt die Eingabe des Worts „schwimmen“ dazu, dass nach Asset-Dateinamen gesucht wird, die mit diesen Buchstaben in dieser Reihenfolge beginnen. Drücken Sie die Eingabetaste, nachdem Sie den Begriff eingegeben haben, um nach dem Asset zu suchen.

![chlimage_1-242](assets/chlimage_1-242.png)

**[!UICONTROL Ordner/Pfad]**: Der Name des angezeigten Ordners basiert auf der von Ihnen ausgewählten Konfiguration. Sie können niedrigere Ebenen anzeigen, indem Sie auf das Ordnersymbol tippen, einen Unterordner auswählen und dann auf das Häkchen tippen, um ihn auszuwählen.

Wenn Sie ein Keyword eingeben und einen Ordner auswählen, durchsucht Experience Manager diesen Ordner und die zugehörigen Unterordner. Wenn Sie jedoch bei der Suche keine Keywords eingeben, werden durch die Auswahl des Ordners nur die Assets in diesem Ordner angezeigt und nicht in Unterordnern.

Standardmäßig durchsucht Experience Manager den ausgewählten Ordner und alle Unterordner.

![chlimage_1-243](assets/chlimage_1-243.png)

**[!UICONTROL Asset-Typ]**: Wählen Sie **[!UICONTROL Dynamic Media Classic]** aus, um Dynamic Media Classic-Inhalte zu durchsuchen. Diese Option ist nur verfügbar, wenn Dynamic Media Classic konfiguriert wurde.

![chlimage_1-244](assets/chlimage_1-244.png)

**[!UICONTROL Konfiguration]**: Wenn Sie über mehr als eine in [!UICONTROL Cloud-Services] definierte Dynamic Media Classic-Konfiguration verfügen, können Sie sie hier auswählen. Der Ordner ändert sich anhand der von Ihnen ausgewählten Konfiguration.

![chlimage_1-245](assets/chlimage_1-245.png)

**[!UICONTROL Medientyp]**: Im Dynamic Media Classic-Browser können Sie Ergebnisse so filtern, dass Folgendes enthalten ist: Bilder, Vorlagen, Videos und adaptive Videosets. Wenn Sie keinen Medientyp auswählen, durchsucht Experience Manager standardmäßig alle Medientypen.

![chlimage_1-246](assets/chlimage_1-246.png)

>[!NOTE]
>
>* Auf der klassischen Benutzeroberfläche können Sie auch nach **Flash** und **FXG** suchen. Das Filtern nach diesen Typen auf der Touch-optimierten Benutzeroberfläche wird nicht unterstützt.
>
>* Beim Durchsuchen eines Videos suchen Sie nach einer einzelnen Ausgabedarstellung. Die Ergebnisse geben die ursprüngliche (nur &amp;ast;.mp4) und die kodierte Ausgabedarstellung zurück.
>* Beim Suchen nach einem adaptiven Videoset durchsuchen Sie den Ordner und alle Unterordner, jedoch nur dann, wenn Sie zur Suche ein Keyword hinzugefügt haben. Wenn Sie kein Keyword hinzugefügt haben, durchsucht Experience Manager die Unterordner nicht.
>

**[!UICONTROL Veröffentlichungsstatus]**: Sie können Assets nach dem Veröffentlichungsstatus filtern: **[!UICONTROL Unveröffentlicht]** oder **[!UICONTROL Veröffentlicht]**. Wenn Sie keinen **[!UICONTROL Veröffentlichungsstatus]** auswählen, durchsucht Experience Manager standardmäßig alle Veröffentlichungsstatus.

![chlimage_1-247](assets/chlimage_1-247.png)
