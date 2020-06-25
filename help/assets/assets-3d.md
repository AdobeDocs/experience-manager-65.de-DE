---
title: Arbeiten mit 3D-Assets in Dynamic Media
seo-title: Arbeiten mit 3D-Assets in Dynamic Media
description: Erfahren Sie, wie Sie mit 3D-Assets in Dynamic Media arbeiten können
seo-description: Erfahren Sie, wie Sie mit 3D-Assets in Dynamic Media arbeiten können
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 56c9bc1ea99dcb93af21d8b26bac8792512f4d42
workflow-type: tm+mt
source-wordcount: '2312'
ht-degree: 13%

---


# Arbeiten mit 3D-Assets in Dynamic Media {#working-with-three-d-assets-dm}

Mit Dynamic Media können Sie 3D-Assets hochladen, verwalten, Ansicht und bereitstellen - als eindrucksvolle Erlebnisse.

* Ein Klick auf die Veröffentlichung (mithilfe der **[!UICONTROL Schnellveröffentlichung]** in der Symbolleiste) von 3D-Assets, um eine URL zu generieren.
* Optimierte Unterstützung für die Anzeige von 3D-Assets mit der hochwertigen, interaktiven Dimensions-Viewer-Vorgabe auf Basis von Adobe Dimension.
* Mit der 3D-Media-WCM-Komponente können Sie Ihren AEM Sites ganz einfach 3D-Elemente hinzufügen.

Es ist keine zusätzliche Konfiguration erforderlich, um 3D-Elemente in Dynamic Media zu verwenden.

![Schuh in 3D](/help/assets/assets-dm/3d-dimensional-viewer-quickpublish-url-embed2.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## Unterstützte 3D-Formate in Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media unterstützt die folgenden 3D-Formate.

Siehe auch unterstützte [3D-Formate.](/help/assets/assets-formats.md)

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Hinweise |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary | Umfasst die Materialien und Texturen als ein Asset. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universelles Scene Description-Zip-Archiv | model/vnd.usdz+zip | *Unterstützung nur für die Aufnahme; keine Anzeige oder Interaktion verfügbar ist.* USDZ ist ein proprietäres 3D-Format, das nativ von Safari- und iOS-Geräten angezeigt werden kann. |

## Quick Beginn: 3D-Assets in Dynamic Media {#quick-start-three-d}

Die folgende Workflow-Beschreibung hilft Ihnen, sich schnell mit 3D-Assets in Dynamic Media - Scene7-Modus vertraut zu machen.

>[!NOTE]
>
>3D-Assets werden im Dynamic Media-Hybridmodus nicht unterstützt.

Bevor Sie mit 3D-Assets in Dynamic Media arbeiten, vergewissern Sie sich, dass Ihr AEM-Administrator die Cloud Service für Dynamic Media im Scene7-Modus bereits aktiviert und konfiguriert hat.

Siehe [Konfiguration von Dynamic Media Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) in „Konfigurieren von Dynamic Media – Scene7-Modus“ und [Fehlerbehebung in Dynamic Media – Scene7-Modus](/help/assets/troubleshoot-dms7.md).

1. **Hochladen von 3D-Assets**

   * [Hochladen von 3D-Assets zur Verwendung in Dynamic Media](/help/assets/managing-assets-touch-ui.md#uploading-assets).
   * [Unterstützte 3D-Dateiformate zum Hochladen in Dynamic Media](#supported-three-d-file-formats-in-dm).

1. **Verwalten von 3D-Assets**

   * Organisieren und Suchen von 3D-Assets

      * [Organisieren digitaler Assets](/help/assets/organize-assets.md#organize-digital-assets).
      * [Durchsuchen von 3D-Assets](/help/assets/search-assets.md).
      * [Verwenden benutzerdefinierter Prädikate zum Filtern der Suchergebnisse](/help/assets/search-assets.md#custompredicates).
   * Ansicht 3D-Assets

      * [Anzeigen und Interagieren mit 3D-Assets](#viewing-three-d-assets).
      * [Verwalten der Viewer-Vorgabe](/help/assets/managing-viewer-presets.md)für Dimensionen
   * Arbeiten mit 3D-Asset-Metadaten

      * [Verwalten von Metadaten für digitale Assets](/help/assets/metadata.md).
      * [Metadatenschemata](/help/assets/metadata-schemas.md).



1. **Veröffentlichen von 3D-Assets**

   * [Veröffentlichen von statischen Dynamic Media - 3D-Assets](#publishing-three-d-assets)
   * [Alternative Methoden zum Veröffentlichen von Dynamic Media-3D-Assets mit dem Dimensionsviewer](#alternate-publish-methods)

## Informationen zum Anzeigen und Arbeiten mit 3D-Assets {#viewing-three-d-assets}

In diesem Abschnitt wird die Ansicht und Interaktion mit 3D-Assets auf zwei verschiedene Arten beschrieben: von der Seite mit den Asset-Details und von der Komponente mit den 3D-Medien in Sites.

Der interaktive 3D-Viewer enthält unter anderem eine Sammlung interaktiver Kamerasysteme, mit denen Sie das 3D-Asset drehen, zoomen und schwenken können.

Beachten Sie, dass die zum Öffnen eines 3D-Assets in der Ansicht &quot;Asset-Details&quot;benötigte Zeit von mehreren Faktoren abhängt. den folgenden Faktoren ab:

* Bandbreite zum Server.
* Latenzen zum Server
* Komplexität des Bildes.

Darüber hinaus sind die Funktionen des Client-Computers, wie eine Workstation, ein Notebook oder ein mobiles Touch-Gerät, auch bei der interaktiven Manipulation der Kamera wichtig. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

>[!TIP]
>
>Sie können die Viewer-Vorgabe &quot;Größe&quot;im Viewer-Vorgabeneditor öffnen, um die Navigation in einem 3D-Asset zu praktizieren, ohne dass zuvor 3D-Dateien hochgeladen werden müssen. Die Viewer-Vorgabe &quot;Größe&quot;verfügt über ein integriertes 3D-Asset, mit dem Sie interagieren können.
>
>See [Managing viewer presets.](/help/assets/managing-viewer-presets.md)

## Anzeigen und Interagieren mit einem 3D-Asset auf der Seite mit den Asset-Details {#viewing-three-d-assets-from-asset-details-page}

Siehe auch [Anzeigen einer Asset-Vorschau über die Software-Oberfläche](/help/assets/previewing-assets.md).

**So können Sie ein 3D-Asset über die Seite mit den Asset-Details Ansicht und damit interagieren**

1. Laden Sie 3D-Assets in AEM hoch.

   Siehe [Hochladen von 3D-Assets zur Verwendung in Dynamic Media.](/help/assets/managing-assets-touch-ui.md#uploading-assets)

1. Tippen Sie in AEM auf der **[!UICONTROL Navigationsseite]** auf **[!UICONTROL Assets > Dateien.]**
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL Card View.]**
1. Navigieren Sie zu einem 3D-Asset, das Sie anzeigen möchten.
1. Tippen Sie auf die Karte des 3D-Assets, um das Asset auf der Seite „Asset-Details“ zu öffnen.
1. Führen Sie auf der Detailseite für die Ansicht des 3D-Assets einen der folgenden Schritte aus:

   * **Drehen Sie Ihre Kamera** - Richten Sie Ihre Ansicht um die 3D-Szene und -Objekte.
      * _Maus_: Klicken und ziehen Sie mit der linken Maustaste.
      * _Touchscreen_: Drücken und ziehen Sie mit einem Finger.
   * **Schwenken Sie die Ansicht** - Drehen Sie sie nach links, rechts, oben oder unten.
      * _Maus_: Klicken und ziehen Sie mit der rechten Maustaste.
      * _Touchscreen_: Drücken und ziehen Sie mit zwei Fingern.
   * **Zoomen Sie Ihre Kamera** - Zoomen Sie Ihre Kamera, um sich in- und außerhalb der 3D-Szene zu bewegen.
      * _Maus_: Scrollen Sie mit dem Mausrad.
      * _Touchscreen_: Führen Sie mit zwei Fingern Pinch-Gesten aus.
   * **Setzen Sie Ihre Kamera** neu ein - geben Sie Ihre Kamera bis zu einem Punkt auf einem Objekt in der 3D-Szene ein.
      * _Maus_: Doppelklicken Sie.
      * _Touchscreen_: Doppeltippen Sie.
   * **Zurücksetzen** - Tippen Sie auf das Symbol &quot;Zurücksetzen&quot;, um den Punkt &quot;Zielgruppe&quot;der Ansicht in der rechten unteren Ecke des 3D-Assets wiederherzustellen. Durch das Zurücksetzen wird die Kamera auch näher oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen.
   * **Vollbildmodus** : Um in den Vollbildmodus zu wechseln, tippen Sie in der rechten unteren Ecke der Seite auf das Symbol &quot;Vollbild&quot;.

1. Tippen Sie in der linken oberen Ecke der Seite auf **[!UICONTROL Schließen]**, um zur Seite „Assets“ zurückzukehren.

## Anzeigen und Interagieren mit einem 3D-Asset innerhalb einer 3D-Medienkomponente {#interacting-with-asset-inside-three-d-media-component}

Wenn sich eine Webseite im **[!UICONTROL Bearbeitungsmodus befindet]** , ist keine Interaktion mit einem 3D-Asset möglich. Um das Asset interaktiv zu gestalten, können Sie mit der Funktion &quot; **[!UICONTROL Vorschau]** &quot;die Webseite im Seiteneditor mit vollem Zugriff auf die Funktionen der 3D-Medienkomponente Ansicht haben.

>[!IMPORTANT]
>
>Sie können diese Aufgabe erst ausführen, nachdem Sie einer Webseite eine 3D-Medienkomponente hinzugefügt und der Komponente ein 3D-Asset zugewiesen haben. Siehe [Hinzufügen der 3D-Medienkomponente zu einer Webseite](#adding-the-three-d-media-component-to-a-web-page) und [Zuweisen eines 3D-Assets zu einer 3D-Medienkomponente.](#assigning-a-three-d-asset-to-the-component)

Siehe auch [Anzeigen einer Asset-Vorschau über die Software-Oberfläche.](/help/assets/previewing-assets.md)

**So erstellen Sie eine Ansicht und Interaktion mit einem 3D-Asset innerhalb einer 3D-Medienkomponente**

1. Führen Sie während der **[!UICONTROL Bearbeitung]** einer Webseite einen der folgenden Schritte aus:

   * Klicken Sie rechts oben auf der Seite auf **[!UICONTROL Vorschau]** , um in den **[!UICONTROL Vorschau]** -Modus zu wechseln.
   * Löschen Sie `/editor.html` aus der Seiten-URL im Browser.
   ![
Ein vollständig interaktives 3D-Asset, wie in ](/help/assets/assets-dm/3d-asset-in-3d-media.png)****

1. ![3D-Asset, das innerhalb der 3D-Medienkomponente](/help/assets/assets-dm/3d-asset-in-3d-media.png)angezeigt wird Ein vollständig interaktives 3D-Asset, wie im **[!UICONTROL Vorschau]** -Modus angezeigt.

   * Führen Sie im Modus **[!UICONTROL Vorschau]** einen der folgenden Schritte aus:**
      * **Drehen Sie Ihre Kamera** - Richten Sie Ihre Ansicht um die 3D-Szene und -Objekte.
      * _Maus_: Klicken und ziehen Sie mit der linken Maustaste.
   * _Touchscreen_: Drücken und ziehen Sie mit einem Finger.
      * **Schwenken Sie die Ansicht** - Drehen Sie sie nach links, rechts, oben oder unten.
      * _Maus_: Klicken und ziehen Sie mit der rechten Maustaste.
   * _Touchscreen_: Drücken und ziehen Sie mit zwei Fingern.
      * **Zoomen Sie Ihre Kamera** - Zoomen Sie Ihre Kamera, um sich in- und außerhalb der 3D-Szene zu bewegen.
      * _Maus_: Scrollen Sie mit dem Mausrad.
   * _Touchscreen_: Führen Sie mit zwei Fingern Pinch-Gesten aus.
      * **Setzen Sie Ihre Kamera** neu ein - geben Sie Ihre Kamera bis zu einem Punkt auf einem Objekt in der 3D-Szene ein.
      * _Maus_: Doppelklicken Sie.
   * _Touchscreen_: Doppeltippen Sie.
   * **Zurücksetzen** - Tippen Sie auf das Symbol &quot;Zurücksetzen&quot;, um den Punkt &quot;Zielgruppe&quot;der Ansicht in der rechten unteren Ecke des 3D-Assets wiederherzustellen. Durch das Zurücksetzen wird die Kamera auch näher oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen.

## **Vollbildmodus** : Um in den Vollbildmodus zu wechseln, tippen Sie in der rechten unteren Ecke der Seite auf das Symbol &quot;Vollbild&quot;.

Grundlagen zum Arbeiten mit der 3D-Medienkomponente {#working-with-three-d-media-component}

* [Dynamic Media enthalten eine Dynamic Media-3D-Medienkomponente, die Sie in AEM Sites verwenden können, um die interaktive Anzeige von 3D-Modellen auf Ihren Webseiten zu ermöglichen.](#adding-three-d-media-component-to-page-template)
* [Hinzufügen der 3D-Medienkomponente zur Seitenvorlage](#adding-three-d-media-component-to-page-template)
   * [Hinzufügen der 3D-Medienkomponente zu einer Webseite](#adding-the-three-d-media-component-to-a-web-page)
* [Optional - Konfigurieren der 3D-Medienkomponente](#configuring-the-three-d-component)


## [Zuweisen eines 3D-Assets zur 3D-Medienkomponente](#assigning-a-three-d-asset-to-the-component)

1. Adding the 3D Media component to the page template {#adding-three-d-media-component-to-page-template}]**
1. Öffnen Sie **[!UICONTROL Tools > Allgemein > Vorlagen.]**
1. Navigieren Sie zu der Seitenvorlage, in der Sie die 3D-Komponente aktivieren möchten, und wählen Sie sie aus.****
1. Tap **[!UICONTROL Edit]** to open the template.

   Wählen Sie rechts oben auf der Seite im Dropdown-Menü die Option **[!UICONTROL Strukturierungsmodus]** , falls diese noch nicht aktiv ist.](/help/assets/assets-dm/3d-media-component-structure.png)

1. ![3d-media-component-structure](/help/assets/assets-dm/3d-media-component-structure.png)]**
1. Tippen Sie auf einen leeren Bereich im Bereich &quot; **[!UICONTROL Layout-Container]** &quot;, um ihn auszuwählen und die zugehörige Symbolleiste zu öffnen.****
1. Tippen Sie in der Symbolleiste auf das Symbol &quot; **[!UICONTROL Richtlinie]** &quot;, um den **[!UICONTROL Richtlinien-Editor zu öffnen.]**********
1. Führen Sie im Abschnitt **[!UICONTROL Eigenschaften]** auf der Registerkarte **[!UICONTROL Zulässige Komponenten]** einen Bildlauf zu den **[!UICONTROL Dynamic Media]** durch, erweitern Sie dann die Liste und aktivieren Sie die Option **[!UICONTROL 3D-Medien.]**

   Tippen Sie auf **[!UICONTROL Fertig]** , um die Änderungen zu speichern und den **[!UICONTROL Richtlinien-Editor zu schließen.]**

## Sie können jetzt die Dynamic Media 3D-Medienkomponente auf allen Seiten platzieren, die diese Vorlage verwenden.{#adding-the-three-d-media-component-to-a-web-page}

Adding the 3D Media component to a web page {#adding-the-three-d-media-component-to-a-web-page}

Wenn Sie Adobe Experience Manager als Web-Content-Management-System verwenden, können Sie Ihren Webseiten 3D-Elemente über die 3D-Medienkomponente hinzufügen.[](/help/assets/adding-dynamic-media-assets-to-pages.md)

1. See also [Adding Dynamic Media assets to pages.](/help/assets/adding-dynamic-media-assets-to-pages.md)
1. Öffnen Sie AEM Sites und wählen Sie die Webseite aus, der Sie die Dynamic Media 3D-Medienkomponente hinzufügen möchten.********

   Tap the **[!UICONTROL Edit]** (pencil) icon to open the page into the page editor. Stellen Sie sicher, dass rechts oben auf der Seite der **[!UICONTROL Bearbeitungsmodus]** ausgewählt ist.](/help/assets/assets-dm/3d-media-component-edit.png)

1. ![3d-media-component-add](/help/assets/assets-dm/3d-media-component-edit.png)

1. Tippen Sie in der Symbolleiste auf das Symbol für das seitliche Bedienfeld, um die Anzeige des Bedienfelds zu aktivieren bzw. zu aktivieren.****

   Tippen Sie im Seitenbedienfeld auf das Pluszeichen, um die Liste &quot; **[!UICONTROL Komponenten]** &quot;zu öffnen.](/help/assets/assets-dm/3d-assets-filter.png)

1. ![3d-media-component-drag-drop](/help/assets/assets-dm/3d-assets-filter.png)]******

Ziehen Sie die **[!UICONTROL 3D-Medienkomponente]** aus der Liste &quot; **[!UICONTROL Komponenten]** &quot;an die Stelle auf der Seite, an der der 3D-Viewer angezeigt werden soll.

Sie können der Komponente jetzt ein 3D-Asset zuweisen.[](#assigning-a-three-d-asset-to-the-component)

### Siehe [Zuweisen eines 3D-Assets zu einer 3D-Medienkomponente.](#assigning-a-three-d-asset-to-the-component)

1. Optional - Konfigurieren der 3D-Medienkomponente {#configuring-the-three-d-component}]**
1. In the AEM Sites page editor, select the **[!UICONTROL 3D Media Viewer]** component that you previously added to the page.

   Tap the **[!UICONTROL Configuration]** icon (wrench) to open the component configuration dialog box.](/help/assets/assets-dm/3d-media-component-config.png)

1. ![3d-media-component-config](/help/assets/assets-dm/3d-media-component-config.png)]**

   Wählen Sie im Dialogfeld &quot;3D-Medien&quot;aus der Dropdown-Liste &quot;Viewer-Vorgabe&quot;die Option &quot; **[!UICONTROL Größe]** &quot;, um der Komponente die Viewer-Vorgabe &quot;Größe&quot;zuzuweisen.](/help/assets/assets-dm/3d-media-component-edit-config.png)

1. ![3d-media-component-edit-config](/help/assets/assets-dm/3d-media-component-edit-config.png)

## Tippen Sie in der oberen rechten Ecke auf das Häkchen, um Ihre Änderungen zu speichern.{#assigning-a-three-d-asset-to-the-component}

Zuweisen eines 3D-Assets zur 3D-Medienkomponente {#assigning-a-three-d-asset-to-the-component}

Nachdem Sie einer Webseite eine 3D-Medienkomponente hinzugefügt haben, können Sie ihr ein 3D-Asset zuweisen.[](#adding-the-three-d-media-component-to-a-web-page)

1. See [Adding the 3D Media component to a web page.](#adding-the-three-d-media-component-to-a-web-page)]******
1. In the AEM Sites page editor, click the **[!UICONTROL Assets]** icon to open **[!UICONTROL Assets]** in the side panel.
1. Wählen Sie in der Dropdown-Liste &quot; **[!UICONTROL 3D]** &quot;aus, um nur 3D-Asset-Dateitypen anzuzeigen.
1. Suchen Sie im Seitenbedienfeld nach dem 3D-Asset, das Sie auf der bearbeiteten Seite Ansicht haben möchten, oder blättern Sie zu diesem.****

   Ziehen Sie das 3D-Asset aus dem Bedienfeld &quot;Assets&quot;und legen Sie es auf die Komponente &quot; **[!UICONTROL 3D-Medien]** &quot;ab, die Sie der Seite zuvor hinzugefügt haben.](/help/assets/assets-dm/3d-asset-add.png)

>![3D-Asset der 3D-Medienkomponente zuweisen](/help/assets/assets-dm/3d-asset-add.png)
>
>[!NOTE]]******

## Während sich eine Webseite im Modus &quot;AEM Sites **[!UICONTROL bearbeiten]** &quot;befindet, zeigt die 3D-Medienkomponente das 3D-Asset an, es ist jedoch keine Interaktion mit dem Asset möglich. Um das Asset interaktiv zu gestalten, können Sie mit der Funktion &quot; **[!UICONTROL Vorschau]** &quot;die Webseite im Seiteneditor mit vollem Zugriff auf die Funktionen der 3D-Medienkomponente Ansicht haben.

Veröffentlichen von statischen Dynamic Media - 3D-Assets {#publishing-three-d-assets}***

Dynamic Media akzeptieren eine Vielzahl von 3D-Dateiformaten, die in Dynamic Media als *statischer Inhalt* unterstützt werden. Statischer Inhalt bedeutet, dass Sie 3D-Assets hochladen und veröffentlichen können. *Dynamische* Bildbearbeitung oder Bildbearbeitung, die mit dem 3D-Asset verknüpft sind, werden jedoch nicht unterstützt. Der Grund dafür ist, dass Dynamic Media Imaging Server keine 3D-Formate erkennt. Nach der Veröffentlichung eines 3D-Assets in Dynamic Media verfügen Sie daher über eine sofortige URL, die Sie kopieren können. Die URL für das 3D-Asset entspricht der üblichen Dynamic Media-URL-Struktur. Im Gegensatz zu herkömmlichen Bild-Assets in Dynamic Media können Sie jedoch keine Parameter in der URL des Assets bearbeiten.

See also [Obtaining a URL for a static asset.](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset)]**********

In der Ansicht **[!UICONTROL &quot;]** Karte&quot;wird ein kleines Globussymbol direkt unter dem Namen eines Assets sowie links neben dem Datum und der Uhrzeit angezeigt, um anzugeben, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

Wenn Sie AEM als WCM verwenden, verwenden Sie diese Veröffentlichungsmethode, um die Dynamic Media-3D-Elemente direkt auf Ihrer Webseite hinzuzufügen.[](publishing-dynamicmedia-assets.md)

See also [Publishing Dynamic Media assets.](publishing-dynamicmedia-assets.md)

Siehe auch [Veröffentlichen von Seiten.](/help/sites-authoring/publishing-pages.md)

1. **So veröffentlichen Sie statische Dynamic Media-3D-Assets**
1. Öffnen Sie ein 3D-Asset (Dateiformat GLB, OBJ oder STL), um es auf der Seite mit den Asset-Details Ansicht.****

   On the toolbar, tap **[!UICONTROL Quick Publish.]**](/help/assets/assets-dm/3d-asset-quick-publish.png)

1. ![3d-asset-quick-publish](/help/assets/assets-dm/3d-asset-quick-publish.png)]**
1. Tippen Sie auf **[!UICONTROL Schließen]** , um das Dialogfeld zu verlassen und zur Seite mit den Asset-Details zurückzukehren.

   Tippen Sie in der Dropdown-Liste links neben dem Dateinamen des 3D-Assets auf **[!UICONTROL Darstellungen.]**](/help/assets/assets-dm/3d-asset-renditions.png)

1. ![3d-asset-renditions](/help/assets/assets-dm/3d-asset-renditions.png)]******
   * Tippen Sie auf **[!UICONTROL Original.]** Wenn ein 3D-Asset veröffentlicht (oder aktiviert) wird, wird die Schaltfläche &quot; **[!UICONTROL URL]** &quot;in der linken unteren Ecke der Seite angezeigt, wenn alle folgenden 3D-Asset-Bedingungen erfüllt sind:
   * Das 3D-Asset ist ein unterstütztes Format (GLB, OBJ, STL und USDZ).
   * Das 3D-Asset wurde in das Dynamic Media Image Production System (IPS) aufgenommen.
   ![Das 3D-Asset wird veröffentlicht.](/help/assets/assets-dm/3d-asset-url.png)

1. ![3d-asset-url](/help/assets/assets-dm/3d-asset-url.png)]**

### Tippen Sie auf **[!UICONTROL URL]** , um die direkte Produktions-URL des 3D-Assets anzuzeigen, die Sie auf Webseiten kopieren und verwenden können.

Alternative Methoden zum Veröffentlichen von Dynamic Media-3D-Assets mit dem Dimensionsviewer {#alternate-publish-methods}*

* Verwenden Sie die folgenden beiden Methoden zum Veröffentlichen von Dynamic Media-3D-Assets, wenn Sie AEM *nicht* als WCM verwenden.]******

   **[!UICONTROL URL]** - Verwenden Sie die **[!UICONTROL URL]** , wenn Sie ein Drittanbieter-Web-Content-Management-System verwenden und mit dem Dimensions-Viewer Dynamic Media 3D-Assets mit Ihren Webseiten verknüpfen möchten.](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset)

* See [Linking URLs to your web application.](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset)]**********

   **[!UICONTROL Einbetten]** - Verwenden Sie &quot; **[!UICONTROL Einbetten]** &quot;, wenn Sie ein Dynamic Media-3D-Asset, das mit dem Dimensions-Viewer auf einer Webseite eingebettet ist, Ansicht haben möchten. Kopieren Sie den Einbettungscode in die Zwischenablage, damit Sie ihn in Ihre Webseiten einfügen können. Editing of the code is not permitted in the **[!UICONTROL Embed]** dialog box.](/help/assets/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page)