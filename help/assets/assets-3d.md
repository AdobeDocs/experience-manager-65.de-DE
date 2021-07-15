---
title: Arbeiten mit 3D-Assets in Dynamic Media
seo-title: Arbeiten mit 3D-Assets in Dynamic Media
description: Erfahren Sie, wie Sie in Dynamic Media mit 3D-Assets arbeiten.
seo-description: Erfahren Sie, wie Sie in Dynamic Media mit 3D-Assets arbeiten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: introduction
content-type: reference
feature: 3D Assets,Asset Management
role: User, Admin
exl-id: 01c96f1e-c0e6-497d-bd7a-c0fd547a34da
source-git-commit: 471f9e99078a1e0af60024d439afd42ae77cba8c
workflow-type: tm+mt
source-wordcount: '2330'
ht-degree: 54%

---

# Arbeiten mit 3D-Assets in Dynamic Media {#working-with-three-d-assets-dm}

Mit Dynamic Media können Sie 3D-Assets hochladen, verwalten, anzeigen und als eindrucksvolle Erlebnisse bereitstellen.

* Veröffentlichen von 3D-Assets mit einem Klick (mithilfe von **[!UICONTROL Quick Publish]** in der Symbolleiste) zum Generieren einer URL.
* Optimierte Unterstützung für die Anzeige von 3D-Assets mit der hochwertigen, interaktiven Viewer-Vorgabe „Dimensional“, bereitgestellt von Adobe Dimension.
* Mit der 3D-Medien-WCM-Komponente können Sie Ihren Adobe Experience Manager Sites-Seiten einfach 3D-Assets hinzufügen.

Für die Verwendung von 3D-Assets in Dynamic Media ist keine zusätzliche Konfiguration erforderlich.

![Schuhe in 3D](/help/assets/assets-dm/3d-dimensional-viewer-quickpublish-url-embed2.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## Unterstützte 3D-Formate in Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media unterstützt die folgenden 3D-Formate.

Siehe auch [Unterstützte 3D-Formate](/help/assets/assets-formats.md).

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Hinweise |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary | Umfasst die Materialien und Texturen als ein Asset. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universelles Scene Description-Zip-Archiv | model/vnd.usdz+zip | *Nur Erfassung unterstützt, keine Anzeige oder Interaktion möglich.* USDZ ist ein proprietäres 3D-Format, das von Safari- und iOS-Geräten nativ angezeigt werden kann. |

## Schnellstart: Arbeiten mit 3D-Assets in Dynamic Media {#quick-start-three-d}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen dabei helfen, 3D-Assets im Dynamic Media-Scene7-Modus einzurichten und schnell auszuführen.

>[!IMPORTANT]
>
>3D-Assets werden im Hybridmodus von Dynamic Media nicht unterstützt.

Bevor Sie mit 3D-Assets in Dynamic Media arbeiten, stellen Sie sicher, dass Ihr Experience Manager-Administrator Dynamic Media-Cloud Services bereits im Modus Dynamic Media - Scene7 aktiviert und konfiguriert hat.

Weitere Informationen finden Sie unter [Dynamic Media-Cloud Services konfigurieren](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) unter Konfigurieren von Dynamic Media - Scene7-Modus und [Fehlerbehebung bei Dynamic Media - Scene7-Modus](/help/assets/troubleshoot-dms7.md).

1. **Hochladen von 3D-Assets**

   * [Laden Sie Ihre 3D-Assets zur Verwendung in Dynamic Media](/help/assets/manage-assets.md#uploading-assets) hoch.
   * [Unterstützte 3D-Dateiformate zum Hochladen in Dynamic Media](#supported-three-d-file-formats-in-dm).

1. **Verwalten von 3D-Assets**

   * Organisieren und Suchen von 3D-Assets

      * [Organisieren von digitalen Assets](/help/assets/organize-assets.md#organize-digital-assets).
      * [Suchen nach 3D-Assets](/help/assets/search-assets.md).
      * [Verwenden Sie benutzerdefinierte Eigenschaften zum Filtern von Suchergebnissen](/help/assets/search-assets.md#custompredicates).
   * Anzeigen von 3D-Assets

      * [Anzeigen von und Interagieren mit 3D-Assets](#viewing-three-d-assets).
      * [Verwalten der Viewer-Vorgabe &quot;Dimensional&quot;](/help/assets/managing-viewer-presets.md).
   * Arbeiten mit 3D-Asset-Metadaten

      * [Metadaten für digitale Assets verwalten](/help/assets/metadata.md).
      * [Metadatenschemata](/help/assets/metadata-schemas.md).



1. **Veröffentlichen von 3D-Assets**

   * [Veröffentlichen von statischen Dynamic Media 3D-Assets](#publishing-three-d-assets)
   * [Alternative Methoden zum Veröffentlichen von Dynamic Media-3D-Assets mit dem Dimensional-Viewer](#alternate-publish-methods)

## Wissenswertes über das Anzeigen von und Interagieren mit 3D-Assets {#viewing-three-d-assets}

In diesem Abschnitt wird beschrieben, wie Sie 3D-Assets auf zwei verschiedene Arten anzeigen und mit ihnen arbeiten können: auf der Seite „Asset-Details“ und in der 3D-Medien-Komponente in Sites.

Der interaktive 3D-Viewer bietet unter anderem eine Reihe interaktiver Kamera-Steuerelemente, mit denen Sie die Kamera um das 3D-Asset drehen sowie Zoom- und Schwenkvorgänge durchführen können.

Die Zeit, die zum Öffnen eines 3D-Assets in der Seitenansicht &quot;Asset-Details&quot;benötigt wird, hängt von verschiedenen Faktoren ab. den folgenden Faktoren abhängt:

* Bandbreite zum Server.
* Latenzen zum Server.
* Komplexität des Bildes.

Wenn Sie die Kamera interaktiv bearbeiten, muss darüber hinaus die Kapazität des Client-Computers – etwa Workstation, Notebook oder Mobilgerät mit Touch-Funktion – berücksichtigt werden. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

>[!TIP]
>
>Sie können die Viewer-Vorgabe „Dimensional“ im Viewer Preset Editor öffnen, um die Navigation in einem 3D-Asset zu üben, ohne 3D-Dateien hochzuladen. Die Viewer-Vorgabe „Dimensional“ verfügt über ein integriertes 3D-Asset, mit dem Sie interagieren können.
>
>Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

## Anzeigen von und Interagieren mit einem 3D-Asset auf der Seite &quot;Asset-Details&quot; {#viewing-three-d-assets-from-asset-details-page}

Siehe auch [Asset-Vorschau mithilfe der Software-Oberfläche](/help/assets/previewing-assets.md).

**So zeigen Sie ein 3D-Asset auf der Seite &quot;Asset-Details&quot;an und interagieren mit ihm:**

1. Stellen Sie sicher, dass Sie 3D-Assets in Adobe Experience Manager hochgeladen haben.

   Siehe [Hochladen von 3D-Assets zur Verwendung in Dynamic Media](/help/assets/manage-assets.md#uploading-assets).

1. Navigieren Sie vom Experience Manager auf der Seite **[!UICONTROL Navigation]** zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Wählen Sie in der rechten oberen Ecke der Seite aus der Dropdownliste **[!UICONTROL Ansicht]** die Option **[!UICONTROL Kartenansicht]** aus.
1. Navigieren Sie zu einem 3D-Asset, das Sie anzeigen möchten.
1. Wählen Sie die Karte des 3D-Assets aus.
1. Führen Sie auf der Seite mit der Detailansicht für das 3D-Asset einen der folgenden Schritte aus:

   | Anzeigen | Beschreibung | Mausaktion | Touchscreen-Aktion |
   | --- | --- | --- | --- |
   | **Kamera drehen** | Drehen Sie die Ansicht um die 3D-Szene und Objekte. | Klicken und ziehen Sie mit der linken Maustaste. | Drücken und ziehen Sie mit einem Finger. |
   | **Kamera schwenken** | Schwenken Sie nach links, rechts, oben und unten. | Klicken und ziehen Sie mit der rechten Maustaste. | Drücken und ziehen Sie mit zwei Fingern. |
   | **Kamera zoomen** | Verschieben Sie Bereiche in die 3D-Szene ein- und aus ihnen. | Scrollen Sie mit dem Mausrad. | Bewegen Sie zwei Finger auseinander- bzw. zusammen. |
   | **Kamera neu zentrieren** | Zentrieren Sie die Kamera neu auf einen Punkt an einem Objekt in der 3D-Szene. | Doppelklicken. | Doppeltippen. |
   | **Zurücksetzen** | Wählen Sie unten rechts auf der Seite das Symbol Zurücksetzen aus, um den Zielpunkt der Ansicht wieder in die Mitte des 3D-Assets zu setzen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen. |  |  |
   | **Vollbildmodus** | Um in den Vollbildmodus zu wechseln, wählen Sie unten rechts auf der Seite das Symbol &quot;Vollbild&quot;aus. |  |  |

1. Wählen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Close]** aus, um zur Seite &quot;Assets&quot;zurückzukehren.

## Anzeigen von und Interagieren mit einem 3D-Asset innerhalb einer 3D-Medien-Komponente {#interacting-with-asset-inside-three-d-media-component}

Wenn sich eine Web-Seite im **[!UICONTROL Bearbeitungsmodus]** befindet, ist keine Interaktion mit einem 3D-Asset möglich. Um das Asset interaktiv zu gestalten, können Sie die Web-Seite im Seiteneditor mithilfe der **[!UICONTROL Vorschaufunktion]** mit vollem Zugriff auf die Funktionen der 3D-Medien-Komponente anzeigen.

>[!IMPORTANT]
>
>Sie können diese Aufgabe erst ausführen, nachdem Sie einer Web-Seite eine 3D-Medien-Komponente hinzugefügt und der Komponente ein 3D-Asset zugewiesen haben. Siehe [Hinzufügen der 3D-Medien-Komponente zu einer Web-Seite](#adding-the-three-d-media-component-to-a-web-page) und [Zuweisen eines 3D-Assets zu einer 3D-Medien-Komponente](#assigning-a-three-d-asset-to-the-component).

Siehe auch [Asset-Vorschau mithilfe der Software-Oberfläche](/help/assets/previewing-assets.md).

**Anzeigen von und Interagieren mit einem 3D-Asset innerhalb einer 3D-Medien-Komponente:**

1. Führen Sie während sich die Web-Seite im **[!UICONTROL Bearbeitungsmodus]** befindet, einen der folgenden Schritte aus:

   * Wählen Sie rechts oben auf der Seite **[!UICONTROL Vorschau]** aus, um den Modus **[!UICONTROL Vorschau]** aufzurufen.
   * Löschen Sie `/editor.html` aus der Seiten-URL im Browser.

Ein vollständig interaktives 3D-Asset, wie im    ![3D-Asset, das innerhalb der 3D-Medien-Komponente angezeigt wird](/help/assets/assets-dm/3d-asset-in-3d-media.png)
Ein vollständig interaktives 3D-Asset, wie im **[!UICONTROL Vorschaumodus]** angezeigt.

1. Führen Sie im **[!UICONTROL Vorschaumodus]** einen der folgenden Schritte aus:

   | Anzeigen | Beschreibung | Mausaktion | Touchscreen-Aktion |
   | --- | --- | --- | --- |
   | **Kamera drehen** | Drehen Sie die Ansicht um die 3D-Szene und Objekte. | Klicken und ziehen Sie mit der linken Maustaste. | Drücken und ziehen Sie mit einem Finger. |
   | **Kamera schwenken** | Schwenken Sie nach links, rechts, oben und unten. | Klicken und ziehen Sie mit der rechten Maustaste. | Drücken und ziehen Sie mit zwei Fingern. |
   | **Kamera zoomen** | Verschieben Sie Bereiche in die 3D-Szene ein- und aus ihnen. | Scrollen Sie mit dem Mausrad. | Bewegen Sie zwei Finger auseinander- bzw. zusammen. |
   | **Kamera neu zentrieren** | Zentrieren Sie die Kamera neu auf einen Punkt an einem Objekt in der 3D-Szene. | Doppelklicken. | Doppeltippen. |
   | **Zurücksetzen** | Wählen Sie unten rechts auf der Seite das Symbol Zurücksetzen aus, um den Zielpunkt der Ansicht wieder in die Mitte des 3D-Assets zu setzen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen. |  |  |
   | **Vollbildmodus** | Um in den Vollbildmodus zu wechseln, wählen Sie unten rechts auf der Seite das Symbol &quot;Vollbild&quot;aus. |  |  |

## Wissenswertes über die Arbeit mit der 3D-Medien-Komponente {#working-with-three-d-media-component}

Dynamic Media enthält eine Dynamic Media-3D-Medien-Komponente, die Sie in Adobe Experience Manager Sites verwenden können, um die interaktive Anzeige von 3D-Modellen auf Ihren Webseiten zu ermöglichen.

* [Hinzufügen der 3D-Medien-Komponente zur Seitenvorlage](#adding-three-d-media-component-to-page-template)
* [Hinzufügen der 3D-Medien-Komponente zu einer Web-Seite](#adding-the-three-d-media-component-to-a-web-page)
   * [Optional - Konfigurieren der 3D-Medien-Komponente](#configuring-the-three-d-component)
* [Zuweisen eines 3D-Assets zur 3D-Medien-Komponente](#assigning-a-three-d-asset-to-the-component)

## Hinzufügen der 3D-Medien-Komponente zur Seitenvorlage {#adding-three-d-media-component-to-page-template}

1. Öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Vorlagen]**.
1. Navigieren Sie zu der Seitenvorlage, in der Sie die 3D-Komponente aktivieren möchten, und wählen Sie sie aus.
1. Wählen Sie **[!UICONTROL Bearbeiten]** aus, damit Sie die Vorlage öffnen können.
1. Wählen Sie rechts oben auf der Seite im Dropdown-Menü den Modus **[!UICONTROL Struktur]** aus, falls er noch nicht aktiv ist.

   ![3d-media-component-structure](/help/assets/assets-dm/3d-media-component-structure.png)

1. Wählen Sie einen leeren Bereich im Bereich **[!UICONTROL Layout-Container]** aus, damit Sie ihn auswählen und die zugehörige Symbolleiste öffnen.
1. Wählen Sie in der Symbolleiste das Symbol **[!UICONTROL Richtlinie]** aus, um den **[!UICONTROL Richtlinien-Editor]** zu öffnen.
1. Scrollen Sie im Abschnitt **[!UICONTROL Eigenschaften]** auf der Registerkarte **[!UICONTROL Zulässige Komponenten]** zu **[!UICONTROL Dynamic Media]**, erweitern Sie dann die Liste und aktivieren Sie die Option **[!UICONTROL 3D-Medien]**.
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Änderungen zu speichern und den **[!UICONTROL Richtlinien-Editor]** zu schließen.

   Sie können jetzt die Dynamic Media-3D-Medien-Komponente auf allen Seiten platzieren, die diese Vorlage verwenden.

## Hinzufügen der 3D-Medien-Komponente auf einer Web-Seite {#adding-the-three-d-media-component-to-a-web-page}

Wenn Sie Experience Manager als Web Content Management-System verwenden, können Sie Ihren Web-Seiten mithilfe der 3D-Medien-Komponente 3D-Assets hinzufügen.

Siehe auch [Hinzufügen von Dynamic Media-Assets auf Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

**So fügen Sie die 3D-Medien-Komponente auf einer Web-Seite hinzu:**

1. Öffnen Sie Adobe Experience Manager Sites und wählen Sie die Web-Seite aus, der Sie die Dynamic Media-3D-Medien-Komponente hinzufügen möchten.
1. Wählen Sie das Symbol **[!UICONTROL Bearbeiten]** (Bleistift) aus, damit Sie die Seite im Seiteneditor öffnen können. Stellen Sie sicher, dass rechts oben auf der Seite der Modus **[!UICONTROL Bearbeiten]** ausgewählt ist.

   ![3d-media-component-add](/help/assets/assets-dm/3d-media-component-edit.png)

1. Wählen Sie in der Symbolleiste das Symbol Seitenbereich aus, um die Anzeige des Bedienfelds zu aktivieren bzw. umzuschalten.

1. Wählen Sie im Seitenbedienfeld das Pluszeichen-Symbol aus, um die Liste **[!UICONTROL Komponenten]** zu öffnen.

   ![3d-media-component-drag-drop](/help/assets/assets-dm/3d-assets-filter.png)

1. Ziehen Sie die Komponente **[!UICONTROL 3D-Medien]** aus der Liste **[!UICONTROL Komponenten]** an die Stelle auf der Seite, an der der 3D-Viewer angezeigt werden soll.

Sie können der Komponente jetzt ein 3D-Asset zuweisen.

Siehe [Zuweisen eines 3D-Assets zur 3D-Medien-Komponente](#assigning-a-three-d-asset-to-the-component).

### Optional - Konfigurieren der 3D-Medien-Komponente {#configuring-the-three-d-component}

1. Wählen Sie im Seiten-Editor in Adobe Experience Manager Sites die Komponente **[!UICONTROL 3D Media Viewer]** aus, die Sie zuvor zur Seite hinzugefügt haben.
1. Wählen Sie das Symbol **[!UICONTROL Konfiguration]** (Schraubenschlüssel) aus, damit Sie das Dialogfeld für die Komponentenkonfiguration öffnen können.

   ![3d-media-component-config](/help/assets/assets-dm/3d-media-component-config.png)

1. Wählen Sie im Dialogfeld „3D-Medien“ aus der Dropdown-Liste „Viewer-Vorgabe“ die Option **[!UICONTROL Dimensional]** aus, um der Komponente die Viewer-Vorgabe „Dimensional“ zuzuweisen.

   ![3d-media-component-edit-config](/help/assets/assets-dm/3d-media-component-edit-config.png)

1. Aktivieren Sie in der oberen rechten Ecke das Kontrollkästchen, um Ihre Änderungen zu speichern.

## Zuweisen eines 3D-Assets zur 3D-Medien-Komponente {#assigning-a-three-d-asset-to-the-component}

Nachdem Sie einer Web-Seite eine 3D-Medien-Komponente hinzugefügt haben, können Sie ihr ein 3D-Asset zuweisen.

Siehe [Hinzufügen der 3D-Medien-Komponente zu einer Web-Seite](#adding-the-three-d-media-component-to-a-web-page).

**So weisen Sie ein 3D-Asset der 3D-Medien-Komponente zu:**

1. Wählen Sie im Seiteneditor von Experience Manager Sites das Symbol **[!UICONTROL Assets]** aus, um **[!UICONTROL Assets]** im Seitenbereich zu öffnen.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL 3D]** aus, um nur 3D-Asset-Dateitypen anzuzeigen.
1. Suchen Sie im Seitenbedienfeld nach dem 3D-Asset, das Sie auf der entsprechenden Seite anzeigen möchten, oder scrollen Sie zu diesem.
1. Ziehen Sie das 3D-Asset aus dem Seitenbedienfeld „Assets“ und legen Sie es auf der Komponente **[!UICONTROL 3D-Medien]** ab, die Sie der Seite zuvor hinzugefügt haben.

   ![Zuweisen eines 3D-Assets zur 3D-Medien-Komponente](/help/assets/assets-dm/3d-asset-add.png)

>[!NOTE]
>
>Während sich eine Web-Seite im Modus **[!UICONTROL Bearbeiten]** für Adobe Experience Manager Sites befindet, zeigt die 3D-Medien-Komponente das 3D-Asset an, jedoch ist keine Interaktion mit dem Asset möglich. Um das Asset interaktiv zu gestalten, können Sie die Web-Seite im Seiteneditor mithilfe der **[!UICONTROL Vorschaufunktion]** mit vollem Zugriff auf die Funktionen der 3D-Medien-Komponente anzeigen.

## Veröffentlichen von statischen Dynamic Media 3D-Assets {#publishing-three-d-assets}

Dynamic Media akzeptiert verschiedene 3D-Dateiformate, die in Dynamic Media als *statische Inhalte* unterstützt werden. Statischer Inhalt bedeutet, dass Sie 3D-Assets hochladen und veröffentlichen können. Es gibt jedoch keine Unterstützung für *Variablendarstellung* oder Bildnachbearbeitung, die mit dem 3D-Asset verknüpft ist. Der Grund dafür ist, dass der Dynamic Media-Bildbearbeitungs-Server keine 3D-Formate erkennt. Nach der Veröffentlichung eines 3D-Assets in Dynamic Media haben Sie daher eine sofortige URL, die Sie kopieren können. Die URL für das 3D-Asset entspricht der üblichen URL-Struktur für Dynamic Media. Im Gegensatz zu herkömmlichen Bild-Assets in Dynamic Media können Sie jedoch keine Parameter in der URL des Assets bearbeiten.

Siehe auch [Abrufen einer URL für ein statisches Asset](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

In der **[!UICONTROL Kartenansicht]** wird ein kleines Globussymbol direkt unter dem Namen eines Assets und links von Datum und Uhrzeit angezeigt, um anzuzeigen, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

Wenn Sie Experience Manager als WCM verwenden, verwenden Sie diese Veröffentlichungsmethode, um die Dynamic Media 3D-Assets direkt auf Ihrer Web-Seite hinzuzufügen.

Siehe auch [Veröffentlichen von Dynamic Media-Assets](publishing-dynamicmedia-assets.md).

Siehe auch [Veröffentlichen von Seiten](/help/sites-authoring/publishing-pages.md).

**Veröffentlichen von statischen Dynamic Media-3D-Assets:**

1. Öffnen Sie ein 3D-Asset (Dateiformat GLB, OBJ oder STL), damit Sie es auf der Asset-Detailseite anzeigen können.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus.

   ![3d-asset-quick-publish](/help/assets/assets-dm/3d-asset-quick-publish.png)

1. Wählen Sie **[!UICONTROL Close]** aus, um das Dialogfeld zu verlassen und zur Asset-Detailseite zurückzukehren.
1. Wählen Sie aus der Dropdown-Liste links neben dem Dateinamen des 3D-Assets **[!UICONTROL Ausgabeformate]** aus.

   ![3d-asset-renditions](/help/assets/assets-dm/3d-asset-renditions.png)

1. Wählen Sie **[!UICONTROL original]** aus. Wenn ein 3D-Asset veröffentlicht (oder &quot;aktiviert&quot;) wird, wird die Schaltfläche **[!UICONTROL URL]** unten links auf der Seite angezeigt, wenn alle folgenden 3D-Asset-Bedingungen erfüllt sind:
   * Das 3D-Asset ist ein unterstütztes Format (GLB, OBJ, STL und USDZ).
   * Das 3D-Asset wurde in das Dynamic Media Image Production System (IPS) erfasst.
   * Das 3D-Asset ist veröffentlicht.

   ![3d-asset-url](/help/assets/assets-dm/3d-asset-url.png)

1. Wählen Sie **[!UICONTROL URL]** aus, damit Sie die direkte Produktions-URL des 3D-Assets anzeigen können, die Sie kopieren und auf Webseiten verwenden können.

### Alternative Methoden zum Veröffentlichen von Dynamic Media-3D-Assets mit dem Dimensional-Viewer {#alternate-publish-methods}

Verwenden Sie die folgenden beiden Methoden zum Veröffentlichen von Dynamic Media 3D-Assets, wenn Sie *nicht* den Experience Manager als WCM verwenden.

* **[!UICONTROL URL]**  - Verwenden Sie die  **** URL, wenn Sie ein Drittanbieter-Web Content Management-System verwenden und Dynamic Media 3D-Assets mit dem Dimensional-Viewer mit Ihren Web-Seiten verknüpfen möchten.

   Siehe [Verknüpfen von URLs mit einer Webanwendung](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Einbetten]**  - Verwenden Sie  **** Einbetten , wenn Sie ein Dynamic Media 3D-Asset anzeigen möchten, das mit dem Dimensional-Viewer auf einer Web-Seite eingebettet ist. Kopieren Sie den Einbettungs-Code in die Zwischenablage, damit Sie ihn in Ihre Web-Seiten einfügen können. Die Bearbeitung des Codes ist im Dialogfeld **[!UICONTROL Eingebettet]** nicht zulässig.

   Siehe [Einbetten des Dynamic Media-Video-, Bild- oder Dimensional-Viewers auf einer Web-Seite](/help/assets/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
