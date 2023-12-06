---
title: Hinzufügen von Dynamic Media-Assets zu Seiten
description: So fügen Sie einer Seite in Adobe Experience Manager Dynamic Media-Komponenten hinzu.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: 62d4a38c-2873-4560-8d58-ad172288764d
feature: Components,Publishing
source-git-commit: 04050f31742c926b45235595f6318929d3767bd8
workflow-type: tm+mt
source-wordcount: '3219'
ht-degree: 99%

---

# Hinzufügen von Dynamic Media-Assets zu Seiten{#adding-dynamic-media-assets-to-pages}

Um die Dynamic Media-Funktionen zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden, können Sie die Komponente für **Dynamic Media**, **Interaktive Medien**, **Panoramamedien** oder **360-Grad-Videomedien** direkt auf der Seite hinzufügen. Wechseln Sie zum Hinzufügen von Komponenten in den Layout-Modus und aktivieren Sie die Komponenten für Dynamic Media. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. Die Komponenten für Dynamic Media sind smart – sie erkennen, ob Sie ein Bild oder ein Video hinzufügen. Die verfügbaren Konfigurationsoptionen ändern sich entsprechend.

Sie fügen Dynamic Media-Assets direkt zur Seite hinzu, wenn Sie Adobe Experience Manager als WCM verwenden. Wenn Sie einen Drittanbieter für Ihr WCM verwenden, [verknüpfen](/help/assets/linking-urls-to-yourwebapplication.md) Sie Ihre Assets oder [betten](/help/assets/embed-code.md) Sie sie ein. Eine responsive Website von Drittanbietern finden Sie unter [Bereitstellen optimierter Bilder für eine responsive Site](/help/assets/responsive-site.md).

>[!NOTE]
>
>Stellen Sie sicher, dass Sie Assets veröffentlichen, bevor Sie sie Seiten in Experience Manager hinzufügen. Siehe [Veröffentlichen von Dynamic Media-Assets](/help/assets/publishing-dynamicmedia-assets.md).

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite {#adding-a-dynamic-media-component-to-a-page}

Beim Hinzufügen einer Komponente für 3D Media, Dynamic Media, interaktive Medien, Panoramamedien, Smart-Zuschnitt-Videos oder 360-Grad-Videomedien gehen Sie genauso vor wie beim Hinzufügen einer Komponente zu einer beliebigen Seite. Die Dynamic Media-Komponenten werden in den folgenden Abschnitten beschrieben.

**So fügen Sie einer Seite eine Dynamic Media-Komponente hinzu:**

1. Öffnen Sie in Experience Manager die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Wählen Sie im Bedienfeld links auf der Seite (ggf. Seitenbedienfeld ein-/ausblenden) das Symbol **[!UICONTROL Komponenten]** aus.
1. Wählen Sie unter der Überschrift **[!UICONTROL Komponenten]** in der Dropdown-Liste **[!UICONTROL Dynamic Media]** aus.

   Wenn keine Liste von Dynamic Media-Komponenten verfügbar ist, müssen Sie die zu verwendenden Dynamic Media-Komponenten aktivieren. Informationen hierzu finden Sie unter [Aktivieren von Dynamic Media-Komponenten](#enabling-dynamic-media-components).

   ![6_5_360video_wcmcomponent](/help/assets/assets/6_5_360video_wcmcomponent.png)

1. Ziehen Sie die zu verwendende **[!UICONTROL Dynamic Media]**-Komponente per Drag-and-Drop an die gewünschte Position auf der Seite.

1. Bewegen Sie den Mauszeiger direkt über die Komponente. Wenn die Komponente blau hervorgehoben wird, klicken Sie einmal darauf, um die Symbolleiste der Komponente anzuzeigen. Klicken Sie auf das Symbol **[!UICONTROL Konfiguration]** (Schraubenschlüssel).

   ![6_5_360video_wcmcomponentconfigure](/help/assets/assets/6_5_360video_wcmcomponentconfigure.png)

1. Je nachdem, welche Dynamic Media-Komponente Sie auf der Seite abgelegt haben, wird ein Konfigurationsdialogfeld geöffnet. [Legen Sie bei Bedarf die Optionen der Komponente fest](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

   Im folgenden Beispiel sehen Sie das Dialogfeld der Dynamic Media-Komponente **[!UICONTROL Video-360-Medien]** und die verfügbaren Optionen in der Dropdown-Liste für Viewer-Vorgaben.

   ![Komponente für 360-Grad-Videomedien](assets/6_5_360video_wcmcomponentviewerpreset.png)

   Die Dynamic Media-Komponente für 360-Grad-Videomedien

1. Wenn Sie fertig sind, wählen Sie oben rechts im Dialogfeld das Häkchen aus, um Ihre Änderungen zu speichern.

### Aktivieren von Dynamic Media-Komponenten {#enabling-dynamic-media-components}

Wenn keine Dynamic Media-Komponenten zum Hinzufügen zu einer Seite verfügbar sind, bedeutet dies wahrscheinlich, dass Sie die zu verwendenden Komponenten zunächst aktivieren müssen.

**So aktivieren Sie Dynamic Media-Komponenten:**

1. Öffnen Sie in Experience Manager die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. Klicken Sie links oben auf der Seite in der Symbolleiste auf das Symbol „Seiteninformationen“ und wählen Sie dann in der Dropdown-Liste **[!UICONTROL Vorlage bearbeiten]** aus.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Wählen Sie oben rechts auf der Seite in der Symbolleiste in der Dropdown-Liste **[!UICONTROL Struktur]** aus.

   ![Richtlinie](/help/assets/assets-dm/structure-mode.png)

1. Wählen Sie unten auf der Seite **[!UICONTROL Layout-Container]**, um die Symbolleiste zu öffnen. Wählen Sie anschließend das Symbol „Richtlinie“.
1. Stellen Sie auf der Seite **[!UICONTROL Layout-Container]** unter der Überschrift **[!UICONTROL Eigenschaften]** sicher, dass die Registerkarte **[!UICONTROL Zugelassene Komponenten]** ausgewählt ist.

   ![Zugelassene Komponenten](/help/assets/assets-dm/allowed-components.png)

1. Scrollen Sie nach unten, bis **[!UICONTROL Dynamic Media]** angezeigt wird.
1. Wählen Sie links neben **[!UICONTROL Dynamic Media]** das Symbol „>“ aus, um die Liste zu erweitern, und wählen Sie die Dynamic Media-Komponenten aus, die Sie aktivieren möchten.

   ![Liste der Dynamic Media-Komponenten](/help/assets/assets-dm/dm-components-select.png)

1. Wählen Sie rechts oben auf der Seite **[!UICONTROL Layout-Container]** das Symbol „Fertig“ (Häkchen) aus.

1. Wählen Sie rechts in der Symbolleiste oben auf der Seite **[!UICONTROL Anfänglicher Inhalt]** in der Dropdown-Liste aus und [fügen Sie dann wie gewohnt eine Dynamic Media-Komponente zu einer Seite hinzu](#adding-a-dynamic-media-component-to-a-page).

## Lokalisieren von Dynamic Media-Komponenten {#localizing-dynamic-media-components}

Zum Lokalisieren von Dynamic Media-Komponenten stehen Ihnen zwei Möglichkeiten zur Verfügung:

* Öffnen Sie auf einer Web-Seite unter „Sites“ die Option **[!UICONTROL Eigenschaften]** und wählen Sie die Registerkarte **[!UICONTROL Erweitert]** aus. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

  ![chlimage_1-172](assets/chlimage_1-538.png)

* Wählen Sie über den Site-Selector die gewünschte Seite oder Seitengruppe aus. Klicken Sie auf **[!UICONTROL Eigenschaften]** und wählen Sie die Registerkarte **[!UICONTROL Erweitert]** aus. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

  >[!NOTE]
  >
  >Nicht allen im Menü **[!UICONTROL Sprache]** verfügbaren Sprachen sind derzeit Token zugewiesen.

## Komponenten vom Typ „Dynamic Media“ {#dynamic-media-components}

Dynamic Media-Komponenten sind verfügbar, wenn Sie auf das Symbol **[!UICONTROL Komponenten]** klicken und nach **[!UICONTROL Dynamic Media]** filtern.

Zu den verfügbaren Dynamic Media-Komponenten zählen:

* **[!UICONTROL Dynamic Media]**: Assets wie Bilder, Videos, E-Kataloge und Rotationssets.
* **[!UICONTROL Interaktive Medien]**: interaktive Assets wie interaktive Videos, interaktive Bilder oder Karussellsets.
* **[!UICONTROL Panoramamedien]**: Panoramabilder oder VR-Panoramabilder.
* **[!UICONTROL Video-360-Medien]**: 360-Grad-Videos und 360-Grad-VR-Videos.

>[!NOTE]
>
>Diese Komponenten sind nicht standardmäßig verfügbar, sondern müssen zunächst über den Vorlageneditor bereitgestellt werden. Nachdem sie im Vorlageneditor [zur Verfügung gestellt wurden](/help/sites-authoring/templates.md#editing-templates-template-authors), können Sie die Komponenten wie jede andere Experience Manager-Komponente Ihrer Seite hinzufügen.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### Dynamic Media-Komponente {#dynamic-media-component}

Die Dynamic Media-Komponente ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, Sets für gemischte Medien und Videos. Zudem ist der Viewer dynamisch. Die Anzeigegröße ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

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

* Sie haben [Dynamic Media aktiviert](/help/assets/config-dynamic.md). Dynamic Media ist standardmäßig deaktiviert.
* Das Bild weist eine Pyramid TIFF-Datei auf. Bilder, die vor der Aktivierung von Dynamic Media importiert wurden, verfügen nicht über eine Pyramid TIFF-Datei.

#### Arbeiten mit Bildern {#when-working-with-images}

Mit der Komponente „Dynamic Media“ können Sie dynamische Bilder, einschließlich Bildsets, Rotationssets und Sets für gemischte Medien, hinzufügen. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotationsset drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild dynamisch zu machen, können Sie die Breakpoints festlegen oder eine dynamische Bildvorgabe anwenden.

Bearbeiten Sie die folgenden Einstellungen für Dynamic Media, indem Sie in der Komponente auf das Symbol **[!UICONTROL Bearbeiten]** und dann auf **[!UICONTROL Einstellungen für Dynamic Media]** klicken.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für Dynamic Media adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie auf der Registerkarte **[!UICONTROL Erweitert]** in der Komponente mit der **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md). Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

  Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien die einzig verfügbare Option. Die angezeigten Viewer-Vorgaben sind intelligent – es werden nur relevante Viewer-Vorgaben angezeigt.

* **[!UICONTROL Viewer-Modifikatoren]**: Viewer-Modifikatoren haben die Form „name=value pair with a &amp; delimiter“ (Name=Wertepaar mit einem &amp;-Trennzeichen ) und ermöglichen eine Viewer-Bearbeitung, wie im Viewers-Referenzhandbuch beschrieben. Ein Beispiel für einen Viewer-Modifikator ist `posterimage=img.jpg&caption=text.vtt,1`. Damit wird ein anderes Bild für die Videominiatur festgelegt und eine Untertiteldatei mit dem Video verknüpft.

* **[!UICONTROL Bildvorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Bildvorgabe aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie sichtbar machen. Siehe „Verwalten von Bildvorgaben“. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

  Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Bildmodifikatoren]**: Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese Effekte werden unter „Bildvorgaben“ und in der Referenz zum Image-Serving-Befehl beschrieben.

  Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breakpoints]**: Wenn Sie dieses Asset auf einer responsiven Website verwenden, müssen Sie die Bild-Breakpoints hinzufügen. Bild-Breakpoints werden durch Kommas (,) getrennt. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.

  Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

  Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** – Aktivieren Sie das Kontrollkästchen (Standard), um die Optimierung des DPR (Device Pixel Ratio, Gerätepixelverhältnis) zu ermöglichen.

  Die Option **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** wird nur angezeigt, wenn Folgendes zutrifft:

   * Unter „Vorgabetyp“ ist **[!UICONTROL Bildvorgabe]** ausgewählt und **[!UICONTROL RESS_IP]** wird aus der Dropdownliste **[!UICONTROL Bildvorgabe]** ausgewählt.

  ![DPR-Einstellung für Bildvorgabe](/help/assets/assets-dm/dpr-ress-ip.png)

  Siehe auch [Informationen zur Optimierung des DPR](/help/assets/imaging-faq.md#dpr). Alle DPR-Werte für intelligente Bildbearbeitung in Adobe Experience Manager Dynamic Media werden ignoriert.

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

Bearbeiten Sie die folgenden Einstellungen für Dynamic Media, indem Sie in der Komponente **[!UICONTROL Bearbeiten]** auswählen.

>[!NOTE]
>
>Die Videokomponente für Dynamic Media ist standardmäßig adaptiv. Wenn sie eine feste Größe aufweisen soll, müssen Sie dies in der Komponente auf der Registerkarte **[!UICONTROL Erweitert]** mit **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** festlegen.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Video-Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

* **[!UICONTROL Viewer-Modifikatoren]**: Viewer-Modifikatoren haben die Form eines Name=Wert-Paars mit einem &amp; als Trennzeichen und ermöglichen die Viewer-Bearbeitung, wie im Adobe Viewer-Referenzhandbuch beschrieben. Ein Beispiel für einen Viewer-Modifikator ist `posterimage=img.jpg&caption=text.vtt,1`.

  Viewer-Modifikatoren ermöglichen z. B. Folgendes:

   * Verknüpfen einer Untertiteldatei mit einem Video: [Untertitel](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html?lang=de)
   * Verknüpfen einer Navigationsdatei mit einem Video: [Navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html?lang=de)

     Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Titel]**: Ändern Sie den Videotitel.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

#### Bei der Arbeit mit smartem Zuschneiden {#when-working-with-smart-crop}

Verwenden Sie die Dynamic Media-Komponente, um Bild-Assets für smartes Zuschneiden zu Ihren Web-Seiten hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

Weitere Informationen finden Sie unter [Bildprofile](/help/assets/image-profiles.md).

![dm-settings-smart-cut](assets/dm-settings-smart-crop.png)

Bearbeiten Sie die folgende Einstellung für Dynamic Media, indem Sie in der Komponente **[!UICONTROL Bearbeiten]** auswählen.

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für Dynamic Media adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie auf der Registerkarte **[!UICONTROL Erweitert]** in der Komponente mit der **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

* **[!UICONTROL Bildmodifikatoren]**: Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese Effekte werden unter „Bildvorgaben“ und in der Referenz zum Image-Serving-Befehl beschrieben.

  Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

  Sie können die folgenden erweiterten Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Seitenverhältnisübereinstimmung aktivieren]**: Wählen Sie diese Option aus, damit Dynamic Media eine intelligente zugeschnittene (Smart-Crop) Ausgabedarstellung mit einem Seitenverhältnis auswählt, das dem Seitenverhältnis des Originalbilds am besten entspricht.

* **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** – Aktivieren Sie das Kontrollkästchen (Standard), um die Optimierung des DPR (Device Pixel Ratio, Gerätepixelverhältnis) zu ermöglichen.

  Die Option **[!UICONTROL Für Geräte mit höherer Auflösung optimieren]** wird nur angezeigt, wenn Folgendes zutrifft:

   * Unter „Vorgabetyp“ ist die Option **[!UICONTROL Smartes Zuschneiden]** ausgewählt.

  ![DPR-Einstellung für smartes Zuschneiden](/help/assets/assets-dm/dpr-smartcrop.png)

  Siehe auch [Informationen zur Optimierung des DPR](/help/assets/imaging-faq.md#dpr). Alle DPR-Werte für intelligente Bildbearbeitung in Adobe Experience Manager Dynamic Media werden ignoriert.

* **[!UICONTROL Titel]**: Ändern Sie den Titel des Smart-Crop-Bildes.

* **[!UICONTROL Alternativer Text]**: Geben Sie dem Smart-Crop-Bild einen Titel, für die Benutzer, deren Grafiken deaktiviert sind.

  Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL URL, Öffnen in]**: Sie können ein Asset so einrichten, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in „Öffnen in“ an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

  Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

### Komponente für interaktive Medien {#interactive-media-component}

Die interaktive Medienkomponente eignet sich für Assets, die interaktiv sind, wie Hotspots oder Imagemaps. Verwenden Sie bei interaktiven Bildern, interaktiven Videos oder Karussellbannern die Komponente **[!UICONTROL Interaktive Medien]**.

Die Komponente Interaktives Medium ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Zudem ist der Viewer dynamisch. Die Anzeigegröße ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn Folgendes auf Ihre Web-Seite zutrifft:
>
>* Mehrere Instanzen der interaktiven Medienkomponente werden auf derselben Seite verwendet.
>* Jede Instanz verwendet denselben Asset-Typ.
>
>Sie können den einzelnen Komponenten für interaktive Medien auf dieser Seite nicht unterschiedliche Viewer-Vorgaben zuweisen.
>
>Sie können jedoch dieselbe Viewer-Vorgabe für alle interaktiven Medienkomponenten, die Assets desselben Typs verwenden, auf der Seite verwenden.

![chlimage_1-174](assets/chlimage_1-541.png)

Sie können die folgenden **[!UICONTROL allgemeinen]** Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe „Verwalten von Viewer-Vorgaben“.

* **[!UICONTROL Titel]**: Ändern Sie den Videotitel.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixeln an, wenn das Bild eine feste Größe aufweisen soll. Wenn die Werte leer gelassen werden, ist das Asset adaptiv.

  Sie können die folgenden Einstellungen von **[!UICONTROL Zu Warenkorb hinzufügen]** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Produkt-Asset anzeigen]**: Dieser Wert ist standardmäßig ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

* **[!UICONTROL Produktpreis anzeigen]**: Dieser Wert ist standardmäßig ausgewählt. Der Produktpreis gibt den Preis des Artikels an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

* **[!UICONTROL Produktformular anzeigen]**: Dieser Wert ist standardmäßig nicht ausgewählt. Das Produktformular beinhaltet jegliche Produktvarianten, etwa hinsichtlich der Größe und der Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.

### Panoramamedienkomponente {#panoramic-media-component}

Die Panoramamedienkomponente ist für die Assets bestimmt, bei denen es sich um kugelförmige Panoramabilder handelt. Solche Bilder bieten eine 360-Grad-Anzeige eines Raums, einer Eigenschaft, eines Standorts oder einer Landschaft. Damit ein Bild als kugelförmiges Panoramabild gilt, muss MINDESTENS eine der beiden folgenden Eigenschaften zutreffen:

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

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie einen vorhandenen Viewer aus dem Dropdown-Menü „Viewer-Vorgaben“ aus.

Wenn die gesuchte Viewer-Vorgabe nicht angezeigt wird, stellen Sie sicher, dass sie veröffentlicht wurde. Veröffentlichen Sie Viewer-Vorgaben, bevor Sie sie verwenden. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

### Komponente für 360-Grad-Videomedien {#video-media-component}

Verwenden Sie die Komponente für **[!UICONTROL Video-360-Medien]**, um ein Panoramavideo auf Ihrer Web-Seite für eine interaktive Anzeige eines Raums, einer Eigenschaft, eines Standorts, einer Landschaft oder eines medizinischen Verfahrens zu rendern.

Während der Wiedergabe auf einer flachen Anzeige kann der Benutzer den Anzeigewinkel bestimmen; bei der Wiedergabe auf Mobilgeräten werden in der Regel die integrierten gyroskopischen Funktionen verwendet.

Der Viewer bietet native Unterstützung für die Bereitstellung von 360-Grad-Video-Assets. Standardmäßig ist keine weitere Konfiguration für die Anzeige oder die Wiedergabe erforderlich. 360-Grad-Videos werden mit Standardvideoerweiterungen wie .mp4, .mkv und .mov bereitgestellt. Der häufigste Codec ist H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

Sie können die folgenden Einstellungen bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Konfigurieren]** klicken.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie einen vorhandenen Viewer aus dem Dropdown-Menü „Viewer-Vorgaben“ aus. Verwenden Sie „Video360VR“ für Endbenutzer, die Virtual-Reality-Brillen verwenden. Enthält grundlegende Steuerelemente für die Videowiedergabe und Social-Media-Eigenschaften. Verwenden Sie „Video360_social“ mit grundlegenden Steuerelementen für die Videowiedergabe. Das Video-Rendering erfolgt im Stereo-Modus. Die manuelle Perspektivensteuerung ist deaktiviert, aber die gyroskopische Steuerung ist aktiviert. Es sind keine Eigenschaften für Social Media verfügbar.

Wenn die gesuchte Viewer-Vorgabe nicht angezeigt wird, stellen Sie sicher, dass sie veröffentlicht wurde. Stellen Sie sicher, dass Sie Viewer-Vorgaben veröffentlichen, bevor Sie sie verwenden. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

### Bereitstellen von Dynamic Media-Assets mit HTTP/2 {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Web-Protokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Die Bereitstellung von Dynamic Media-Assets kann über HTTP/2 erfolgen, das schnellere Antwort- und Ladezeiten bietet.

Siehe [Bereitstellung von Inhalt über HTTP/2](/help/assets/http2.md), um ausführliche Informationen zu den ersten Schritten mit HTTP/2 mit Ihrem Dynamic Media-Konto zu erhalten.

>[!MORELIKETHIS]
>
>* [Verwenden des Video-Players in Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-player-feature-video-use.html?lang=de)
>* [Verwenden von interaktiven Videos mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-interactive-video-feature-video-use.html?lang=de)
>* [Verwenden des Asset-Viewers mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/viewers/dynamic-media-viewer-feature-video-understand.html?lang=de)
>* [Verwenden der benutzerdefinierten Videominiatur mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-thumbnails-feature-video-use.html?lang=de)
>* [Farb-Management mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-color-management-technical-video-setup.html?lang=de)
>* [Verwenden des Scharfzeichnens von Bildern mit Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use.html?lang=de)
