---
title: Hinzufügen von Dynamic Media-Assets zu Seiten
description: Hinzufügen von Dynamic Media-Komponenten zu einer Seite in Adobe Experience Manager.
uuid: b5e982f5-fa1c-478a-bcb3-a1ef980df201
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 97a5f018-8255-4b87-9d21-4a0fdf740e4d
docset: aem65
role: User, Admin
exl-id: 62d4a38c-2873-4560-8d58-ad172288764d
feature: Components,Publishing
source-git-commit: d947bd98b3a0f6fd79cde5b5b2fca23487077da3
workflow-type: tm+mt
source-wordcount: '3258'
ht-degree: 76%

---

# Hinzufügen von Dynamic Media-Assets zu Seiten{#adding-dynamic-media-assets-to-pages}

Wenn Sie Assets auf Ihren Websites Dynamic Media-Funktionen hinzufügen möchten, können Sie die Komponente für **Dynamic Media**, **interaktive Medien**, **Panoramamedien** oder **Video-360-Medien** direkt auf der Seite hinzufügen. Sie fügen Komponenten hinzu, indem Sie in den Layout -Modus wechseln und die Dynamic Media-Komponenten aktivieren. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. Die Komponenten für Dynamic Media sind smart – sie erkennen, ob Sie ein Bild oder ein Video hinzufügen. Die verfügbaren Konfigurationsoptionen ändern sich entsprechend.

Sie fügen Dynamic Media-Assets direkt zur Seite hinzu, wenn Sie Adobe Experience Manager als WCM verwenden. Wenn Sie einen Drittanbieter für Ihr WCM verwenden, [verknüpfen](/help/assets/linking-urls-to-yourwebapplication.md) Sie Ihre Assets oder [betten](/help/assets/embed-code.md) Sie sie ein. Eine responsive Website von Drittanbietern finden Sie unter [Bereitstellen optimierter Bilder für eine responsive Site](/help/assets/responsive-site.md).

>[!NOTE]
>
>Stellen Sie sicher, dass Sie Assets veröffentlichen, bevor Sie sie in Experience Manager zu Seiten hinzufügen. Siehe [Veröffentlichen von Dynamic Media-Assets](/help/assets/publishing-dynamicmedia-assets.md).

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite {#adding-a-dynamic-media-component-to-a-page}

Beim Hinzufügen einer Komponente für 3D Media, Dynamic Media, interaktive Medien, Panoramamedien, Smart-Zuschnitt-Videos oder 360-Grad-Videomedien gehen Sie genauso vor wie beim Hinzufügen einer Komponente zu einer beliebigen Seite. Die Dynamic Media-Komponenten werden in den folgenden Abschnitten beschrieben.

**So fügen Sie einer Seite eine Dynamic Media-Komponente hinzu:**

1. Öffnen Sie in Experience Manager die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Wählen Sie im Bedienfeld auf der linken Seite der Seite (wenn nötig, die Anzeige des Seitenbedienfelds ein-/ausschalten) die Option **[!UICONTROL Komponenten]** Symbol.
1. Unter dem **[!UICONTROL Komponenten]** -Überschrift in der Dropdown-Liste wählen Sie **[!UICONTROL Dynamic Media]**.

   Wenn keine Liste der Dynamic Media-Komponenten verfügbar ist, müssen Sie die Dynamic Media-Komponenten aktivieren, die Sie verwenden möchten. Informationen hierzu finden Sie unter [Aktivieren von Dynamic Media-Komponenten](#enabling-dynamic-media-components).

   ![6_5_360video_wcmcomponent](/help/assets/assets/6_5_360video_wcmcomponent.png)

1. Ziehen Sie eine **[!UICONTROL Dynamic Media]** -Komponente, die Sie verwenden möchten, und legen Sie sie an der gewünschten Stelle auf der Seite ab.

1. Bewegen Sie den Mauszeiger direkt über die Komponente. Wenn die Komponente blau hervorgehoben wird, klicken Sie einmal darauf, um die Symbolleiste der Komponente anzuzeigen. Klicken Sie auf das Symbol **[!UICONTROL Konfiguration]** (Schraubenschlüssel).

   ![6_5_360video_wcmcomponentconfigure](/help/assets/assets/6_5_360video_wcmcomponentconfigure.png)

1. Je nachdem, welche Dynamic Media-Komponente Sie auf der Seite abgelegt haben, wird ein Konfigurationsdialogfeld geöffnet. [Legen Sie die Optionen der Komponente](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) wie gewünscht fest.

   Im folgenden Beispiel sehen Sie das Dialogfeld der Dynamic Media-Komponente **[!UICONTROL Video-360-Medien]** und die verfügbaren Optionen in der Dropdown-Liste für Viewer-Vorgaben.

   ![Komponente für 360-Grad-Videomedien](assets/6_5_360video_wcmcomponentviewerpreset.png)

   Die Dynamic Media-Komponente für 360-Grad-Videomedien

1. Wenn Sie fertig sind, wählen Sie in der oberen rechten Ecke des Dialogfelds das Häkchen aus, um Ihre Änderungen zu speichern.

### Aktivieren von Dynamic Media-Komponenten {#enabling-dynamic-media-components}

Wenn keine Dynamic Media-Komponenten zum Hinzufügen zu einer Seite verfügbar sind, bedeutet dies wahrscheinlich, dass Sie zuerst die Komponenten aktivieren müssen, die Sie verwenden möchten.

**So aktivieren Sie Dynamic Media-Komponenten:**

1. Öffnen Sie in Experience Manager die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Wählen Sie links oben auf der Seite in der Symbolleiste das Symbol Seiteninformationen und dann **[!UICONTROL Vorlage bearbeiten]** aus der Dropdown-Liste aus.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Wählen Sie oben rechts auf der Seite in der Symbolleiste in der Dropdown-Liste **[!UICONTROL Struktur]** aus.

   ![Richtlinie](/help/assets/assets-dm/structure-mode.png)

1. Wählen Sie unten auf der Seite **[!UICONTROL Layout-Container]**, um die Symbolleiste zu öffnen. Wählen Sie anschließend das Symbol „Richtlinie“.
1. Stellen Sie auf der Seite **[!UICONTROL Layout-Container]** unter der Überschrift **[!UICONTROL Eigenschaften]** sicher, dass die Registerkarte **[!UICONTROL Zugelassene Komponenten]** ausgewählt ist.

   ![Zugelassene Komponenten](/help/assets/assets-dm/allowed-components.png)

1. Scrollen Sie nach unten, bis **[!UICONTROL Dynamic Media]** angezeigt wird.
1. Wählen Sie das Symbol > links neben **[!UICONTROL Dynamic Media]** Sie können die Liste erweitern und dann die Dynamic Media-Komponenten auswählen, die Sie aktivieren möchten.

   ![Liste der Dynamic Media-Komponenten](/help/assets/assets-dm/dm-components-select.png)

1. In der rechten oberen Ecke des **[!UICONTROL Layout-Container]** -Seite, wählen Sie das Symbol Fertig (Häkchen) aus.

1. Wählen Sie rechts oben auf der Seite in der Symbolleiste aus der Dropdown-Liste die Option **[!UICONTROL Anfänglicher Inhalt]**, dann [Hinzufügen einer Dynamic Media-Komponente zu einer Seite](#adding-a-dynamic-media-component-to-a-page) wie gewohnt.

## Dynamic Media-Komponenten lokalisieren {#localizing-dynamic-media-components}

Zum Lokalisieren von Dynamic Media-Komponenten stehen Ihnen zwei Möglichkeiten zur Verfügung:

* Öffnen Sie auf einer Web-Seite unter „Sites“ die Option **[!UICONTROL Eigenschaften]** und wählen Sie die Registerkarte **[!UICONTROL Erweitert]** aus. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

   ![chlimage_1-172](assets/chlimage_1-538.png)

* Wählen Sie über den Site-Selector die gewünschte Seite oder Seitengruppe aus. Klicken Sie auf **[!UICONTROL Eigenschaften]** und wählen Sie die Registerkarte **[!UICONTROL Erweitert]** aus. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

   >[!NOTE]
   >
   >Nicht allen im Menü **[!UICONTROL Sprache]** verfügbaren Sprachen sind derzeit Tokens zugewiesen.

## Komponenten vom Typ „Dynamische Medien“ {#dynamic-media-components}

Dynamic Media-Komponenten sind verfügbar, wenn Sie auf das Symbol **[!UICONTROL Komponenten]** klicken und nach **[!UICONTROL Dynamic Media]** filtern.

Zu den verfügbaren Dynamic Media-Komponenten zählen:

* **[!UICONTROL Dynamic Media]**: Assets wie Bilder, Videos, E-Kataloge und Rotationssets.
* **[!UICONTROL Interaktive Medien]**: interaktive Assets wie interaktive Videos, interaktive Bilder oder Karussellsets.
* **[!UICONTROL Panoramamedien]**: Panoramabilder oder VR-Panoramabilder.
* **[!UICONTROL Video-360-Medien]**: 360-Grad-Videos und 360-Grad-VR-Videos.

>[!NOTE]
>
>Diese Komponenten sind standardmäßig nicht verfügbar. Sie müssen über den Vorlageneditor verfügbar gemacht werden, bevor Sie sie verwenden können. [Nachdem sie in bereitgestellt wurden](/help/sites-authoring/templates.md#editing-templates-template-authors)Im Vorlageneditor können Sie die Komponenten wie jede andere Experience Manager-Komponente zu Ihrer Seite hinzufügen.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### Komponente „Dynamische Medien“ {#dynamic-media-component}

Die Dynamic Media-Komponente ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, Sets für gemischte Medien und Videos. Darüber hinaus ist der Viewer responsiv - die Größe des Bildschirms ändert sich automatisch basierend auf der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn Folgendes auf Ihre Web-Seite zutrifft:
>
>* Mehrere Instanzen der Dynamic Media-Komponente werden auf derselben Seite verwendet.
>* Jede Instanz verwendet denselben Asset-Typ.

>
>Sie können den einzelnen Dynamic Media-Komponenten auf dieser Seite nicht unterschiedliche Viewer-Vorgaben zuweisen.
>
>Sie können jedoch dieselbe Viewer-Vorgabe für alle Dynamic Media-Komponenten, die Assets desselben Typs verwenden, auf der Seite verwenden.

Wenn Sie die Dynamic Media-Komponente hinzufügen und **[!UICONTROL Einstellungen für Dynamic Media]** leer ist, ist es nicht möglich, ein Asset ordnungsgemäß hinzuzufügen. Überprüfen Sie Folgendes:

* Sie [Dynamic Media aktiviert](/help/assets/config-dynamic.md) haben. Dynamic Media ist standardmäßig deaktiviert.
* das Bild eine Pyramid TIFF-Datei aufweist. Bilder, die Sie vor der Aktivierung von Dynamic Media importieren, verfügen nicht über eine Pyramid TIFF-Datei.

#### Arbeiten mit Bildern {#when-working-with-images}

Mit der Komponente „Dynamic Media“ können Sie dynamische Bilder, einschließlich Bildsets, Rotationssets und Sets für gemischte Medien, hinzufügen. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotationsset drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild dynamisch zu machen, können Sie die Breackpoints festlegen oder eine dynamische Bildvorgabe anwenden.

Bearbeiten Sie die folgenden Dynamic Media-Einstellungen, indem Sie die **[!UICONTROL Bearbeiten]** Symbol in der Komponente und dann **[!UICONTROL Dynamic Media-Einstellungen]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für Dynamic Media adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie auf der Registerkarte **[!UICONTROL Erweitert]** in der Komponente mit der **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

* **[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien die einzig verfügbare Option. Die angezeigten Viewer-Vorgaben sind intelligent. Es werden nur relevante Viewer-Vorgaben angezeigt.

* **[!UICONTROL Viewer-Modifikatoren]**: Viewer-Modifikatoren haben die Form „name=value pair with a &amp; delimiter“ (Name=Wertepaar mit einem &amp;-Trennzeichen ) und ermöglichen eine Viewer-Bearbeitung, wie im Viewers-Referenzhandbuch beschrieben. Ein Beispiel für einen Viewer-Modifikator ist `posterimage=img.jpg&caption=text.vtt,1`. Damit wird ein anderes Bild für die Videominiatur festgelegt und eine Untertiteldatei mit dem Video verknüpft.

* **[!UICONTROL Bildvorgabe]** - Wählen Sie eine vorhandene Bildvorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe „Verwalten von Bildvorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Bild-Modifikatoren]** - Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese Effekte werden unter Bildvorgaben und in der Referenz zum Image Serving-Befehl beschrieben.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breakpoints]**: Wenn Sie dieses Asset auf einer responsiven Website verwenden, müssen Sie die Bild-Breakpoints hinzufügen. Bildhaltepunkte werden durch Kommas (,) getrennt. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

   Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** – Aktivieren Sie das Kontrollkästchen (Standard), um die Optimierung des DPR (Device Pixel Ratio, Gerätepixelverhältnis) zu ermöglichen.

   Die Option **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** wird nur angezeigt, wenn Folgendes zutrifft:

   * Unter „Vorgabetyp“ ist **[!UICONTROL Bildvorgabe]** ausgewählt und **[!UICONTROL RESS_IP]** wird aus der Dropdownliste **[!UICONTROL Bildvorgabe]** ausgewählt.

   ![DPR-Einstellung für Bildvorgabe](/help/assets/assets-dm/dpr-ress-ip.png)

   Siehe auch [Informationen zur Optimierung des DPR](/help/assets/imaging-faq.md#dpr). Alle DSGVO-Werte für die intelligente Bildbearbeitung in Adobe Experience Manager Dynamic Media werden ignoriert.

* **[!UICONTROL Titel]**: Ändern Sie den Bildtitel.

* **[!UICONTROL Alternativer Text]**: Geben Sie dem Bild einen Titel, für die Benutzer, deren Grafiken deaktiviert sind.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL URL, Öffnen in]**: Sie können ein Asset so einrichten, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### Arbeiten mit Videos {#when-working-with-video}

Verwenden Sie die Dynamic Media-Komponente, um Ihren Web-Seiten dynamische Videos hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

![chlimage_1-173](assets/chlimage_1-540.png)

Bearbeiten Sie die folgenden Dynamic Media-Einstellungen durch Auswahl von **[!UICONTROL Bearbeiten]** in der Komponente.

>[!NOTE]
>
>Die Videokomponente für Dynamic Media ist standardmäßig adaptiv. Wenn sie eine feste Größe aufweisen soll, müssen Sie dies in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** festlegen.

* **[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Video-Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

* **[!UICONTROL Viewer-Modifikatoren]** - Viewer-Modifikatoren haben die Form &quot;name=value pair with a &amp; delimiter&quot;und ermöglichen eine Viewer-Bearbeitung, wie im Adobe Viewer-Referenzhandbuch beschrieben. Ein Beispiel für einen Viewer-Modifikator ist `posterimage=img.jpg&caption=text.vtt,1`.

   Mit Viewer-Modifikatoren können Sie beispielsweise Folgendes tun:

   * Verknüpfen einer Untertiteldatei mit einem Video: [caption][https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Verknüpfen einer Navigationsdatei mit einem Video: [Navigation][https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

      Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Titel]**: Ändern Sie den Videotitel.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### Bei der Arbeit mit smartem Zuschneiden {#when-working-with-smart-crop}

Verwenden Sie die Dynamic Media-Komponente, um Bild-Assets für smartes Zuschneiden zu Ihren Web-Seiten hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

Weitere Informationen finden Sie unter [Bildprofile](/help/assets/image-profiles.md).

![dm-settings-smart-cut](assets/dm-settings-smart-crop.png)

Bearbeiten Sie die folgende Dynamic Media-Einstellung durch Auswahl von **[!UICONTROL Bearbeiten]** in der Komponente.

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für Dynamic Media adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie auf der Registerkarte **[!UICONTROL Erweitert]** in der Komponente mit der **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

* **[!UICONTROL Bild-Modifikatoren]** - Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese Effekte werden unter Bildvorgaben und in der Referenz zum Image Serving-Befehl beschrieben.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

   Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Seitenverhältnisübereinstimmung aktivieren]**: Wählen Sie diese Option aus, damit Dynamic Media eine intelligente zugeschnittene (Smart-Crop) Ausgabedarstellung mit einem Seitenverhältnis auswählt, das dem Seitenverhältnis des Originalbilds am besten entspricht.

* **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** – Aktivieren Sie das Kontrollkästchen (Standard), um die Optimierung des DPR (Device Pixel Ratio, Gerätepixelverhältnis) zu ermöglichen.

   Die Option **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** wird nur angezeigt, wenn Folgendes zutrifft:

   * Unter „Vorgabetyp“ ist die Option **[!UICONTROL Smartes Zuschneiden]** ausgewählt.

   ![DPR-Einstellung für smartes Zuschneiden](/help/assets/assets-dm/dpr-smartcrop.png)

   Siehe auch [Informationen zur Optimierung des DPR](/help/assets/imaging-faq.md#dpr). Alle DSGVO-Werte für die intelligente Bildbearbeitung in Adobe Experience Manager Dynamic Media werden ignoriert.

* **[!UICONTROL Titel]**: Ändern Sie den Titel des Smart-Crop-Bildes.

* **[!UICONTROL Alternativer Text]**: Geben Sie dem Smart-Crop-Bild einen Titel, für die Benutzer, deren Grafiken deaktiviert sind.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL URL, Öffnen in]**: Sie können ein Asset so einrichten, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

### Komponente für interaktive Medien {#interactive-media-component}

Die Komponente „Interaktive Medien“ ist für Assets mit interaktiven Elementen wie Hotspots oder Imagemaps vorgesehen. Verwenden Sie bei interaktiven Bildern, interaktiven Videos oder Karussellbannern die Komponente **[!UICONTROL Interaktive Medien]**.

Die Komponente Interaktives Medium ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Darüber hinaus ist der Viewer responsiv - die Größe des Bildschirms ändert sich automatisch basierend auf der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn Folgendes auf Ihre Web-Seite zutrifft:
>
>* Mehrere Instanzen der Komponente für interaktive Medien werden auf derselben Seite verwendet.
>* Jede Instanz verwendet denselben Asset-Typ.

>
>Sie können den einzelnen Komponenten für interaktive Medien auf dieser Seite nicht unterschiedliche Viewer-Vorgaben zuweisen.
>
>Sie können jedoch dieselbe Viewer-Vorgabe für alle interaktiven Medienkomponenten, die Assets desselben Typs verwenden, auf der Seite verwenden.

![chlimage_1-174](assets/chlimage_1-541.png)

Sie können die folgenden **[!UICONTROL allgemeinen]** Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Viewer-Vorgabe]** - Wählen Sie eine vorhandene Viewer-Vorgabe aus dem Dropdown-Menü aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe „Verwalten von Viewer-Vorgaben“.

* **[!UICONTROL Titel]**: Ändern Sie den Videotitel.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

   Sie können die folgenden Einstellungen von **[!UICONTROL Zu Warenkorb hinzufügen]** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Produkt-Asset anzeigen]**: Dieser Wert ist standardmäßig ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

* **[!UICONTROL Produktpreis anzeigen]**: Dieser Wert ist standardmäßig ausgewählt. Der Produktpreis gibt den Preis des Artikels an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

* **[!UICONTROL Produktformular anzeigen]**: Dieser Wert ist standardmäßig nicht ausgewählt. Das Produktformular beinhaltet jegliche Produktvarianten, etwa hinsichtlich der Größe und der Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.

### Panoramamedienkomponente {#panoramic-media-component}

Die Panoramamedienkomponente bezieht sich auf Kugelpanoramen. Solche Bilder bieten ein 360°-Zuschauererlebnis eines Raums, einer Immobile, eines Ortes oder einer Landschaft. Damit ein Bild als Kugelpanorama gilt, muss MINDESTENS eine der beiden folgenden Eigenschaften zutreffen:

* Ein Seitenverhältnis von 2:1.
* Mit den Keywords `equirectangular` oder (`spherical` + `panorama`) oder (`spherical` + `panoramic`) markiert. Weitere Informationen finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

Die Kriterien für das Seitenverhältnis sowie die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die WCM-Komponente **[!UICONTROL Panoramamedien]**.

>[!NOTE]
>
>Wenn Folgendes auf Ihre Web-Seite zutrifft:
>
>* Mehrere Instanzen der Komponente für **[!UICONTROL Panoramamedien]** werden auf derselben Seite verwendet.
>* Jede Instanz verwendet denselben Asset-Typ.

>
>Sie können den einzelnen Komponenten für **[!UICONTROL Panoramamedien]** auf dieser Seite nicht unterschiedliche Viewer-Vorgaben zuweisen.
>
>Sie können jedoch dieselbe Viewer-Vorgabe für alle Komponenten für Panoramamedien, die Assets desselben Typs verwenden, auf der Seite verwenden.

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

Sie können die folgenden Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Konfigurieren]** klicken.

* **[!UICONTROL Viewer-Vorgabe]** - Wählen Sie einen vorhandenen Viewer aus dem Dropdown-Menü &quot;Viewer-Vorgabe&quot;aus.

Wenn die gesuchte Viewer-Vorgabe nicht angezeigt wird, stellen Sie sicher, dass sie veröffentlicht wurde. Veröffentlichen Sie Viewer-Vorgaben, bevor Sie sie verwenden. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

### Komponente für 360-Grad-Videomedien {#video-media-component}

Verwenden Sie die Komponente für **[!UICONTROL Video-360-Medien]**, um ein Panoramavideo auf Ihrer Web-Seite für eine interaktive Anzeige eines Raums, einer Eigenschaft, eines Standorts, einer Landschaft oder eines medizinischen Verfahrens zu rendern.

Während der Wiedergabe auf einer flachen Anzeige kann der Benutzer den Anzeigewinkel bestimmen; bei der Wiedergabe auf Mobilgeräten werden in der Regel die integrierten gyroskopischen Funktionen verwendet.

Der Viewer bietet native Unterstützung für die Bereitstellung von 360-Grad-Video-Assets. Standardmäßig ist keine weitere Konfiguration für die Anzeige oder die Wiedergabe erforderlich. 360-Grad-Videos werden mit Standardvideoerweiterungen wie .mp4, .mkv und .mov bereitgestellt. Der am häufigsten verwendete Codec ist H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

Sie können die folgenden Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Konfigurieren]** klicken.

* **[!UICONTROL Viewer-Vorgabe]** - Wählen Sie einen vorhandenen Viewer aus dem Dropdown-Menü &quot;Viewer-Vorgabe&quot;aus. Verwenden Sie „Video360VR“ für Endbenutzer, die Virtual-Reality-Brillen verwenden. Enthält grundlegende Steuerelemente für die Videowiedergabe und Social-Media-Eigenschaften. Verwenden Sie „Video360_social“ mit grundlegenden Steuerelementen für die Videowiedergabe. Videorendering erfolgt im Stereomodus. Die manuelle Blickwinkelsteuerung ist deaktiviert, aber gyroskopische Steuerelemente sind aktiviert. Es sind keine Eigenschaften für Social Media verfügbar.

Wenn die gesuchte Viewer-Vorgabe nicht angezeigt wird, stellen Sie sicher, dass sie veröffentlicht wurde. Stellen Sie sicher, dass Sie Viewer-Vorgaben veröffentlichen, bevor Sie sie verwenden. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

### Bereitstellen von Dynamic Media-Assets mit HTTP/2 {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Web-Protokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](/help/assets/http2.md).

>[!MORELIKETHIS]
>
>* [Videoplayer in Experience Manager Dynamic Media verwenden](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-video-player-feature-video-use.html)
>* [Verwenden von interaktiven Videos mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html)
>* [Grundlegendes zum Asset-Viewer mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-viewer-feature-video-understand.html)
>* [Verwenden benutzerdefinierter Videominiaturen mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Grundlegendes zum Farbmanagement mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-color-management-technical-video-setup.html)
>* [Verwenden der Bildschärfe mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html)

