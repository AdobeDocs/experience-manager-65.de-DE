---
title: Verwalten von Viewer-Vorgaben
description: 'Erstellen und Verwalten von Viewer-Vorgaben '
uuid: 64fcf16a-7c4a-435b-bf1a-f27b8b39a715
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: cf7823f4-82c2-4e36-9b65-3c58359b8104
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/viewer-presets
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Verwalten von Viewer-Vorgaben{#managing-viewer-presets}

Eine Viewer-Vorgabe ist eine Sammlung von Einstellungen, mit denen festgelegt wird, wie Benutzer Rich-Media-Assets auf ihren Computerbildschirmen und Mobilgeräten anzeigen. Als Administrator können Sie Viewer-Vorgaben erstellen. Es sind Einstellungen für eine Reihe von Viewer-Konfigurationsoptionen verfügbar. Sie können beispielsweise die Anzeigegröße oder das Zoomverhalten des Viewers ändern.

For instructions on creating and customizing your own HTML5 viewer presets, see the *Adobe Scene7 HTML5 Viewer SDK*. Das SDK ist auf dem im SDK eingebetteten IS-Veröffentlichungsserver verfügbar. Jede Bibliotheksversion verfügt über eine eigene SDK-Dokumentation.

Pfad: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.
For example, 3.5 SDK: [https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html)

Siehe auch das [Adobe-Viewer-Referenzhandbuch](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/). 

In diesem Abschnitt wird beschrieben, wie Viewer-Vorgaben erstellt, bearbeitet und verwaltet werden.  Sie können jederzeit bei der Vorschau eines Assets eine Viewer-Vorgabe darauf anwenden.  Siehe [Anwenden von Viewer-Vorgaben](#applying-a-viewer-preset-to-an-asset). 

>[!NOTE]
>
>Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird.  Wenn Sie versuchen, eine standardmäßig vorhandene Viewer-Vorgabe zu bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern. 

## Möglichkeit des Zugriffs auf die Tastatur im Viewer {#keyboard-accessibility-for-viewers}

Alle standardmäßigen Viewer unterstützen den Zugriff auf die Tastatur.

Weitere Informationen finden Sie unter [ Tastaturzugriff und Navigation](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_keyboard_accessibility.html).

## Verwalten von Viewer-Vorgaben {#managing-viewer-presets-1}

You can add, edit, delete, publish, unpublish, and preview viewer presets in AEM by tapping **[!UICONTROL Tools** (hammer icon) **[!UICONTROL > Assets > Viewer Presets]**.

![6_5_tools-assets-viewerpresets](assets/6_5_tools-assets-viewerpresets.png)

>[!NOTE]
>
>Standardmäßig zeigt das System 15 Viewer-Vorgaben, wenn Sie in einer Detailansicht eines Assets „Viewer“ auswählen.  Sie können diesen Grenzwert erhöhen.  Siehe [Erhöhen der Anzahl angezeigter Viewer-Vorgaben](#increasing-the-number-of-viewer-presets-that-display). 

### Viewer-Unterstützung für Webseiten mit responsivem Design  {#viewer-support-for-responsive-designed-web-pages}

Unterschiedliche Webseiten haben unterschiedliche Anforderungen.  Mitunter möchten Sie vielleicht, dass eine Webseite über einen Link verfügt, der den HTML5-Viewer in einem separaten Browserfenster öffnet.  In anderen Fällen kann es aber auch erforderlich sein, den HTML5-Viewer direkt auf der Hostseite einzubetten. In letzterem Fall kann die Webseite ein statisches Layout aufweisen.  Oder sie kann „responsiv“ sein und auf verschiedenen Geräten oder bei verschieden großen Browserfenstern anders angezeigt werden.  Um all diese Anforderungen zu berücksichtigen, unterstützen sämtliche vordefinierten, standardmäßig vorhandenen HTML5-Viewer, die mit Dynamic Media bereitgestellt werden, sowohl statische als auch responsive Webseiten. 

Weitere Informationen zum Einbetten responsiver Viewer auf Webseiten finden Sie unter [Bibliothek responsiver Bilder](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/is_api/c_about_responsive_static_image_library.html) in der *Scene7 Image Serving-API-Hilfe*.

>[!NOTE]
>
>Sie müssen zunächst alle standardmäßig vorhandenen Viewer veröffentlichen, um sie verwenden zu können. 
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

### Kompatibilität mit Viewer-Vorgaben {#viewer-preset-system-compatibility}

Alle standardmäßig vorhandenen Viewer-Vorgaben, die mit Dynamic Media bereitgestellt werden, sind mit den folgenden Systemen vollständig kompatibel: 

* Desktops 
* Apple iPhones 
* Apple iPads 
* Android-Smartphones 
* Android-Tablets 
* Videos: zusätzliche Unterstützung zur MP4-Wiedergabe für [Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678) und [Windows Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx) 

### Rich media types for Viewer Presets {#rich-media-types-for-viewer-presets}

Administratoren können die folgenden Rich-Media-Typen hinzufügen und anpassen, wenn sie Viewer-Vorgaben erstellen. 

<table>
 <tbody>
  <tr>
   <td><strong>Karussell-Set</strong><br /> </td>
   <td><p>Hotspots, Imagemaps oder beide werden zu einer Reihe von mindestens zwei Bildern hinzugefügt. Ein Kunde kann die Bilder nach links oder rechts schwenken und dann auf einen Hotspot auf einem Bild klicken, um weitere Details zu erhalten oder direkt von einer Website-Kategorie, -Startseite oder -Einstiegsseite zu erwerben.</p> </td>
  </tr>
  <tr>
   <td><strong>Flyout-Zoom</strong></td>
   <td><p>Zeigt ein zweites Bild des vergrößerten Bereichs neben dem Originalbild an. Dafür gibt es keine Steuerelemente. Benutzer verschieben die Auswahl auf den gewünschten Bereich.</p> <p>Bei der Bestimmung der vollständigen Bandbreitenauslastung für diesen Viewer müssen Sie berücksichtigen, dass sowohl das Hauptbild als auch das Flyout-Bild im Viewer verarbeitet werden. Die Größe des Hauptbildes (Anzeigenbreite und -höhe) und der Zoomfaktor bestimmen die Größe des Flyout-Bildes. Sie müssen ein Gleichgewicht zwischen diesen beiden Werten schaffen, um zu verhindern, dass die Flyout-Datei zu groß wird: Wenn das Hauptbild sehr groß ist, reduzieren Sie den Zoomfaktor-Wert. (Die Flyout-Breite und Flyout-Höhe bestimmen die Größe des Flyout-Fensters, aber nicht die Größe des Flyout-Bildes, das im Viewer verarbeitet wird.)</p> <p>Beispiel: Wenn das Hauptbild eine Größe von 350 x 350 Pixel und einen Zoomfaktor von 3 aufweist, hat das resultierende Flyout-Bild eine Größe von 1050 x 1050 Pixel. Wenn das Hauptbild eine Größe von 300 x 300 Pixel und einen Zoomfaktor von 4 aufweist, hat das Flyout-Bild eine Größe von 1200 x 1200 Pixel. Abhängig von der JPEG-Qualitätseinstellung (empfohlene Einstellungen liegen zwischen 80 und 90) können Sie die Dateigröße erheblich reduzieren. Als Zoomfaktor wird ein Wert zwischen 2,5 und 4 empfohlen, je nach Größe des Hauptbildes.</p> </td>
  </tr>
  <tr>
   <td><strong>Inline-Zoom</strong></td>
   <td>Zeigt ein Bild des hereingezoomten Bereichs im ursprünglichen Viewer an. Es stehen keinerlei Steuerelemente zur Verfügung.  Benutzer verschieben vielmehr die Auswahl über den Bereich, der angezeigt werden soll. </td>
  </tr>
  <tr>
   <td><strong>Bildset</strong></td>
   <td>Im Bildset-Viewer können Benutzer unterschiedliche Ansichten oder Farbvariationen eines Elements sehen, indem sie auf eine Miniaturansicht klicken. Dieser Viewer bietet auch Zoomtools, mit denen Bilder genauer untersucht werden können.</td>
  </tr>
  <tr>
   <td><strong>Interaktives Bild</strong></td>
   <td>Hotspots werden zu Bildteilen hinzugefügt, auf die ein Kunde klicken kann, um weitere Details zu erhalten oder direkt von den Kategorien-, Home- oder Einstiegsseiten einer Website zu erwerben.</td>
  </tr>
  <tr>
   <td><strong>Interaktives Video</strong></td>
   <td>Miniaturansichten werden zu Zeitschienensegmenten in einem Video hinzugefügt, auf das ein Kunde klicken kann, um weitere Details zu erhalten oder direkt von den Kategorien-, Home- oder Einstiegsseiten einer Website zu erwerben.</td>
  </tr>
  <tr>
   <td><strong>Gemischte Medien</strong></td>
   <td>Zeigt unterschiedliche Medientypen in einem Viewer an. Dort können Sie Rotationssets, Bildsets, Bilder und Videos aufnehmen.</td>
  </tr>
  <tr>
   <td><strong>Panoramabild</strong></td>
   <td><p>Die Viewer für Panoramabilder und PanoramicVR geben Kugelpanoramen wieder, um Benutzern ein 360°-Betrachtererlebnis eines Zimmers, einer Immobilie, eines Orts oder einer Landschaft zu bieten.</p> <p>Damit ein hochgeladenes Bild als Kugelpanorama gilt, muss mindestens eine der beiden folgenden Eigenschaften zutreffen:</p>
    <ul>
     <li>Ein Seitenverhältnis von 2:1.</li>
     <li>Tagged with the keywords <code>equirectangular</code>, or <code>spherical</code> and <code>panorama</code>, or <code>spherical </code>and <code>panoramic</code>. Weitere Informationen finden Sie unter <a href="/help/sites-authoring/tags.md">Verwenden von Tags</a>.</li>
    </ul> <p>Die Kriterien für das Seitenverhältnis sowie die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die WCM-Komponente „Panoramamedien“.</p> <p><strong>Wichtig:</strong> Dieser Viewer ist nur im Scene7-Modus von Dynamic Media verfügbar.</p> </td>
  </tr>
  <tr>
   <td><strong>Rotationsset</strong></td>
   <td>Stellt mehrere Ansichten eines Bildes bereit, sodass Benutzer den Gegenstand drehen können, um ihn von allen Seiten zu betrachten.</td>
  </tr>
  <tr>
   <td><strong>360-Grad-Video</strong></td>
   <td><p>Verwenden Sie den 360/VR-Video-Viewer, um ein Panoramavideo für eine interaktive Anzeige eines Raums, einer Eigenschaft, eines Standorts, einer Landschaft oder eines medizinischen Verfahrens zu rendern.</p> <p>Während der Wiedergabe auf einer flachen Anzeige kann der Benutzer den Anzeigewinkel bestimmen; bei der Wiedergabe auf Mobilgeräten werden in der Regel die integrierten gyroskopischen Funktionen verwendet.</p> <p>Der Viewer bietet native Unterstützung für die Bereitstellung von 360-Grad-Videoassets. Standardmäßig ist keine weitere Konfiguration für die Anzeige oder die Wiedergabe erforderlich. 360-Grad-Videos werden mit Standardvideoerweiterungen wie .mp4, .mkv und .mov bereitgestellt. Der am häufigsten verwendete Codec ist H.264.</p> <p><strong>Wichtig:</strong> Dieser Viewer ist nur im Scene7-Modus von Dynamic Media verfügbar.</p> </td>
  </tr>
  <tr>
   <td><strong>Video</strong></td>
   <td><p>Wiedergeben von Videos unter Verwendung des progressiven oder adaptiven Bitraten-Streamings. Beim Streaming mit adaptiver Bitrate wird eine automatische Geräte- und Brandbreitenerkennung durchgeführt, um Videos mit der richtigen Qualität und im richtigen Format bereitzustellen.</p> </td>
  </tr>
  <tr>
   <td><strong>Vertikaler Zoom</strong></td>
   <td><p>Mit dem Viewer für vertikalen Zoom können Sie das Betrachtererlebnis für Produktbilder optimieren, um Ihren Benutzern die bestmögliche Darstellung eines Produktes zu bieten. Die vertikale Positionierung von Farbfeldern:</p>
    <ul>
     <li>Stellt sicher, dass sich Farbfelder „oberhalb der Falte“ befinden.<br/> Bei einer horizontalen Platzierung von Farbfeldern sind die Farbfelder je nach Bildschirmgröße nicht sichtbar, bis der Benutzer auf der Seite nach unten scrollt. Wenn die Farbfelder vertikal im Viewer platziert werden, sind sie unabhängig von der Bildschirmgröße des Benutzers sichtbar.</li>
     <li>Maximiert die Größe des Hauptbildes.<br /> Bei horizontalen Farbfeldern ist es erforderlich, Platz auf der Seite zu lassen, um sicherzustellen, dass sie sichtbar sind. Diese Positionierung verringerte die mögliche Größe des Hauptbildes. Bei einer vertikalen Farbfeld-Platzierung ist es jedoch nicht notwendig, diesen Platz freizulassen. Somit können Sie die Größe des Hauptbildes maximieren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Zoom</strong></td>
   <td>Damit können Benutzer den Bereich durch Klicken ein- und auszoomen. Benutzer können auf Steuerelemente klicken, um ein- und auszuzoomen und das Bild auf seine Standardgröße zurückzusetzen.</td>
  </tr>
 </tbody>
</table>

### Liste standardmäßig vorhandener Viewer-Vorgaben {#list-of-out-of-the-box-viewer-presets}

In der folgenden Tabelle werden alle vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben, die mit Dynamic Media bereitgestellt werden, benannt. 

Weitere Informationen finden Sie in den [Viewer-Referenzbibliothek-Beispielen](https://marketing.adobe.com/resources/help/en_US/s7/vlist/vlist.html) und [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Informationen zu unterstützten Webbrowsern und Betriebssystemversionen für Viewer finden Sie in den Viewer-Versionshinweisen. 

Weitere Informationen finden Sie in den Viewer-Versionshinweisen im Inhaltsverzeichnis des [Viewer-Referenzhandbuchs](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/).

>[!NOTE]
>
>Alle standardmäßig vorhandenen Viewer-Vorgaben in Dynamic Media sind bereits aktiviert. Sie müssen sie allerdings noch veröffentlichen. 
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).
>
>Alle neuen Viewer-Vorgaben, die Sie erstellen und hinzufügen, müssen sowohl aktiviert werden *und *veröffentlicht.
> Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets) und [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets). 

<table>
 <tbody>
  <tr>
   <td><strong>Viewer-Vorgabentitel </strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>CSS-Dateiname</strong><br /> </td>
  </tr>
  <tr>
   <td>Carousel_Dotted_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Dotted_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_light.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_light.css</code></td>
  </tr>
  <tr>
   <td>Flyout</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_flyoutviewer.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_dark</td>
   <td>Bildset</td>
   <td><code>html5_zoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_light</td>
   <td>Bildset</td>
   <td><code>html5_zoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_dark</td>
   <td>Mixed_Media</td>
   <td><code>html5_inlinemixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_light</td>
   <td>Mixed_Media</td>
   <td><code>html5_inlinemixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineZoom</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_inlinezoomviewer.css</code></td>
  </tr>
  <tr>
   <td>MixedMedia_dark</td>
   <td>Mixed_Media</td>
   <td><code>html5_mixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>MixedMedia_light</td>
   <td>Mixed_Media</td>
   <td><code>html5_mixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>PanoramicImage</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>PanoramicImageVR</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Banner</td>
   <td>Interactive_Image</td>
   <td><code>html5_interactiveimage.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Video_dark</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideoviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Video_light</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideovewer_light.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_dark</td>
   <td>Spin_Set</td>
   <td><code>html5_spinviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_light</td>
   <td>Spin_Set</td>
   <td><code>html5_spinviewer_light.css</code></td>
  </tr>
  <tr>
   <td><p>Video</p> <p>(mit Unterstützung für Untertitel)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video360_social</p> <p>(Enthält grundlegende Steuerelemente für die Videowiedergabe, das Video-Rendering erfolgt im Stereomodus, und die manuelle Blickwinkelsteuerung ist deaktiviert. Jedoch sind die gyroskopischen Funktionen aktiviert und die Social-Media-Eigenschaften deaktiviert)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewersocial.css</code></td>
  </tr>
  <tr>
   <td><p>Video360VR</p> <p>(Für Endbenutzer, die Virtual-Reality-Brillen verwenden. Enthält grundlegende Steuerelemente für die Videowiedergabe und Social Media-Eigenschaften)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video_social</p> <p>(mit Unterstützung für Untertitel und soziale Medien)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewersocial.css</code></td>
  </tr>
  <tr>
   <td>Zoom_dark<br /> </td>
   <td>Zoom<br /> </td>
   <td><code>html5_basiczoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Zoom_light<br /> </td>
   <td>Zoom</td>
   <td><code>html5_basiczoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_dark<br /> </td>
   <td>Vertical_Zoom</td>
   <td><code>html5_zoomverticalviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_light</td>
   <td>Vertical_Zoom</td>
   <td><code>html5_zoomverticalviewer_light.css</code></td>
  </tr>
 </tbody>
</table>

### Matrix unterstützter Mobile Viewer-Gesten {#supported-mobile-viewers-gestures-matrix}

In der folgenden Tabelle werden die Mobile Viewer-Gesten benannt, die auf iOS-, Android 2.x- und Android 3.x-Geräten unterstützt werden. 

<table>
 <tbody>
  <tr>
   <td><strong>Geste</strong></td>
   <td><strong>Flyout-Zoom</strong></td>
   <td><strong>Zoom</strong></td>
   <td><strong>Drehung</strong></td>
  </tr>
  <tr>
   <td><p><strong>ziehen</strong></p> </td>
   <td><p>Schwenken</p> </td>
   <td><p>Schwenken</p> </td>
   <td><p>Schwenken</p> </td>
  </tr>
  <tr>
   <td><p><strong>Tippen</strong></p> </td>
   <td><p>Blendet Flyout-Fenster ein</p> </td>
   <td><p>Blendet die Benutzeroberfläche ein oder aus</p> </td>
   <td><p>Blendet die Benutzeroberfläche ein oder aus</p> </td>
  </tr>
  <tr>
   <td><p><strong>Doppeltippen</strong></p> </td>
   <td><p>Gilt nicht</p> </td>
   <td><p>Vergrößern oder Zurücksetzen</p> </td>
   <td><p>Vergrößern oder Zurücksetzen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Aufziehen</strong></p> </td>
   <td><p>Gilt nicht</p> </td>
   <td><p>Vergrößert (nur iOS und Android 3x)</p> </td>
   <td><p>Vergrößert (nur iOS und Android 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Schließen</strong></p> </td>
   <td><p>Gilt nicht</p> </td>
   <td><p>Verkleinert (nur iOS und Android 3x)</p> </td>
   <td><p>Verkleinert (nur iOS und Android 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Streichen</strong></p> </td>
   <td><p>Bildlaufleiste</p> </td>
   <td><p>Bildlauf</p> </td>
   <td><p>Rotationen</p> </td>
  </tr>
  <tr>
   <td><p><strong>Flick</strong></p> </td>
   <td><p>Bildlaufleiste</p> </td>
   <td><p>Bildlauf</p> </td>
   <td><p>Rotationen</p> </td>
  </tr>
 </tbody>
</table>

## Increasing the number of Viewer Presets that display {#increasing-the-number-of-viewer-presets-that-display}

AEM zeigt verschiedene Viewer-Vorgaben an, wenn Sie ein Asset unter **[!UICONTROL Detailansicht > Viewer]** anzeigen. Sie können die Anzahl der angezeigten Viewer erhöhen oder verringern.

**So erhöhen Sie die Anzahl angezeigter Viewer-Vorgaben**

1. Navigate to CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigieren Sie zum Knoten für die Viewer-Vorgabenliste unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](assets/chlimage_1-221.png)

1. Ändern Sie für die Eigenschaft **[!UICONTROL limit]** den **[!UICONTROL Wert]**, für den standardmäßig 15 festgelegt ist, in einen höheren Wert.
1. Navigieren Sie zur Datenquelle der Viewer-Vorgabe unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](assets/chlimage_1-222.png)

1. In the limit property, change the number to the desired number, for example `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`
1. Tippen Sie auf **[!UICONTROL Alle speichern]**.

## Creating a Viewer Preset {#creating-a-new-viewer-preset}

Durch Erstellen von Viewer-Vorgaben können Sie verschiedene Einstellungen anwenden, um Assets anzuzeigen und mit diesen zu interagieren.  Sie müssen jedoch keine neuen Viewer-Vorgaben erstellen.  Wenn Sie dies bevorzugen, können Sie auch die bereits standardmäßig in AEM Assets verfügbaren Viewer-Vorgaben verwenden. 

If you choose to create a new viewer preset, after you save it, the viewer&#39;s state is automatically activated (set to **[!UICONTROL On]**) in the Viewer Presets page. Dieser Status bedeutet, dass er in der Komponente &quot;Dynamische Medien&quot;und in der Komponente &quot;Interaktive Medien&quot;sowie bei jeder Vorschau eines Bildes oder Videos sichtbar ist.

Bestimmte Viewer-Vorgaben weisen exklusive Einstellungen auf, die die Nutzung und das Gesamtverhalten des Viewers beeinflussen können.  Je nach der von Ihnen erstellten Viewer-Vorgabe sollten Sie diese besonderen Hinweise berücksichtigen.  

Siehe [Besondere Hinweise zum Erstellen von Vorgaben für interaktive Viewer](#special-considerations-for-creating-an-interactive-viewer-preset).

Siehe [Besondere Hinweise zum Erstellen von Viewer-Vorgaben für Karussellbanner](#special-considerations-for-creating-a-carousel-banner-viewer-preset). 

**So erstellen Sie eine Viewer-Vorgabe**

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools** (hammer icon) **[!UICONTROL > Assets > Viewer Presets**.

   ![6_5_viewerpresets](assets/6_5_viewerpresets.png)

1. Tippen Sie auf der Seite „Viewer-Vorgaben“ auf der Symbolleiste auf **[!UICONTROL Erstellen]**. 
1. In the **[!UICONTROL New Viewer Preset** dialog box, in the **[!UICONTROL Preset Name]** field, enter the name of the new preset. Choose a name carefully—they are not editable after you tap **[!UICONTROL Create]**.

   Wenn Sie die Vorgabe an späterer Stelle in diesen Schritten speichern, wird der Name auf der Seite „Viewer-Vorgaben“ unter der Spaltenüberschrift „Vorgabentitel“ angezeigt. 

1. On the Rich Media Type drop-down menu, select the type of viewer preset you want to create, then in the upper-right corner of the page, tap **[!UICONTROL Create]**.

   Siehe [Rich-Media-Typen für Viewer-Vorgaben](#rich-media-types-for-viewer-presets).

1. Tippen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ auf die Registerkarte **[!UICONTROL Erscheinungsbild]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie aus dem Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren visuelles Design angepasst werden soll. Sie können auch auf ein beliebiges visuelles Element im Viewer tippen oder klicken, um es zum Konfigurieren auszuwählen. 

        Der Visual Editor zeigt Ihnen, wie sich eine bestimmte Eigenschaft auf einen Stil auswirkt.  Legen Sie eine beliebige Eigenschaft fest bzw. passen Sie diese an, um sofort anhand des Beispiels auf der linken Seite des Editors zu sehen, wie sich dies auf den Viewer auswirkt. 

      The CSS styling properties for each type of viewer preset are described in the any &quot;Customizing *`<viewer name>`* Viewer&quot; Help topic in the [Viewers Reference Guide](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/). For example, if you are creating a viewer preset of the type `Mixed_Media`, see [Customizing Mixed Media Viewer](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_mixedmedia_viewer_customizingviewer.html) for a list and description of each property.

   * Wenn Stileinstellungen in einer separaten CSS-Datei definiert sind, können Sie die CSS-Datei in AEM Assets hochladen.  Tippen Sie unterhalb des Pulldown-Menüs „Ausgewählter Typ“ auf **[!UICONTROL CSS importieren]** (ggf. müssen Sie hierzu einen Bildlauf im Visual Editor durchführen), um nach der hochgeladenen CSS-Datei zu suchen und diese mit der Viewer-Vorgabe zu verknüpfen.****

        Beim Importieren einer CSS-Datei überprüft der Visual Editor, ob CSS die korrekten Viewer-Markierungen verwendet.  For example, if you are creating a Zoom viewer, all the CSS rules you import must be defined using its viewer class name `.s7mixedmediaviewer` defined on a parent viewer element.

      Sie können beliebige, handgefertigten CSS-Dateien importieren, solange diese die CSS-Markierungen für den jeweiligen Viewer ordnungsgemäß definieren. (CSS-Markierungen werden im Hilfethema *Anpassen des &lt;Viewer-Name>-Viewers* im [Viewer-Referenzhandbuch](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/) erläutert. Wenn Sie beispielsweise mehr über CSS-Markierungen für den Zoom-Viewer erfahren möchten, lesen Sie den Abschnitt [Anpassen des Zoom-Viewers](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_20_zoom_viewer_customizingviewer.html).) Es ist jedoch möglich, dass der Visual Editor nicht alle CSS-Werte versteht.  In solchen Fällen versucht der Visual Editor, die Fehler zu überschreiben, damit das CSS weiterhin funktionieren kann.
   >[!NOTE]
   >
   >Wenn Sie es vorziehen, CSS direkt in seiner Rohform zu bearbeiten, tippen Sie unterhalb des Pulldown-Menüs „Ausgewählter Typ“ auf **[!UICONTROL CSS ein-/ausbl.]** (ggf. müssen Sie hierzu einen Bildlauf im Visual Editor durchführen).
   >Wenn Sie eine Eigenschaft direkt in CSS ändern, können Sie wie im Visual Editor sofort sehen, wie sich dies auf das Viewer-Beispiel auswirkt.  Außerdem wird zur gleichen Zeit genau diese Eigenschaft automatisch im Visual Editor aktualisiert.  Daher können Sie entweder den CSS-Editor, den Visual Editor oder beide abwechselnd verwenden. 

   >[!NOTE]
   >
   >Für Schaltflächengrafiken wählen Sie das 2x-Bild aus und laden Sie Grafiken mit hoher Auflösung hoch.  Beim Arbeiten mit interaktiven Bildern und Bannern mit Einkaufsfunktion können Sie auch aus verschiedenen standardmäßig vorhandenen Hotspot-Schaltflächen wählen. 

1. (Optional) Tippen Sie in der Nähe des oberen Bereichs der Seite „Viewer-Vorgabe bearbeiten“ auf **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]** oder **[!UICONTROL Telefon]**, um visuelle Stile für verschiedene Geräte- und Bildschirmtypen individuell zu definieren. 
1. Tippen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ auf die Registerkarte **[!UICONTROL Verhalten.]** Sie können auch auf ein beliebiges visuelles Element im Viewer tippen oder klicken, um es zum Konfigurieren auszuwählen. 
1. Wählen Sie aus dem Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren Verhalten geändert werden soll.

   Viele Komponenten im Visual Editor sind mit einer detaillierten Beschreibung verknüpft.  Diese Beschreibungen werden in blauen Feldern angezeigt, wenn Sie eine Komponente zum Anzeigen der mit ihr verknüpften Parameter einblenden. 

   Einige Viewer-Typen besitzen Komponenten, mit denen Sie Image Serving-Befehle im Textfeld **[!UICONTROL IS-Befehl]** festlegen können.  Eine Liste der verfügbaren Befehle finden Sie in der [Image Serving-API-Referenz](https://marketing.adobe.com/resources/help/en_US/s7/is_ir_api/image_serving_api_ref.html). 

   >[!NOTE]
   >
   >**Bei Nutzung eines Touchgeräts, etwa eines Telefons oder Tablets:** 
   >
   >
   >Nachdem Sie einen Wert in das Textfeld eingegeben haben, tippen Sie auf eine andere Stelle in der Benutzeroberfläche, um die Änderung weiterzuleiten und die virtuelle Tastatur zu schließen. Wenn Sie auf die Eingabetaste tippen, wird keine Aktion ausgeführt.

1. Tippen Sie in der Nähe der oberen rechten Ecke auf **[!UICONTROL Speichern]**.
1. Veröffentlichen Sie die neue Viewer-Vorgabe.  Sie müssen die Vorgabe veröffentlichen, um sie auf Ihrer Website verwenden zu können. 

   Siehe[ Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

### Besondere Hinweise zum Erstellen von Viewer-Vorgaben für interaktive Videos  {#special-considerations-for-creating-an-interactive-viewer-preset}

**Wissenswertes über Anzeigemodi für Bildminiaturansichten im Anzeigefeld** 

When you create or edit an Interactive Video viewer preset, you have the choice of which Display Mode setting to use when you select `InteractiveSwatches` from the **[!UICONTROL Selected Component]** pull-down menu under the **[!UICONTROL Behavior]** tab. Der von Ihnen gewählte Anzeigemodus beeinflusst, wie und wann Miniaturansichten während der Videowiedergabe angezeigt werden.  You can choose either a `segment`display mode (default) or a `continuous` display mode.

<table>
 <tbody>
  <tr>
   <td><strong>Anzeigemodus</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Segment</td>
   <td><p><code>Segment </code>ist der Standardanzeigemodus für die standardmäßigen interaktiven Video-Viewer-Vorgaben <code>Shoppable_Video_light</code> und <code>Shoppable_Video_dark</code> alle interaktiven Video-Viewer-Vorgaben, die Sie selbst erstellen.</p> <p>In this mode, when there are fewer thumbnails assigned to a video segment than the number of visible spots in the display panel, thumbnails from the next or previous sub-segments are <i>not </i>pulled in to fill any empty spots in the panel. So bleibt die Anzeige von einem bestimmten Videosegment zugewiesenen Mustern erhalten.</p> </td>
  </tr>
  <tr>
   <td>Kontinuierlich</td>
   <td><p>In <code>continuous </code>display mode, if the number of thumbnails in a segment is less than the number that are visible in the panel, the viewer automatically includes the display of thumbnails from the next segment, or the previous segment, in cases where the last thumbnail is displayed.</p> <p>Das <a href="/help/assets/interactive-videos.md">Video in diesem Thema</a> ist ein Beispiel für den <code>continuous </code>Anzeigemodus.</p> </td>
  </tr>
 </tbody>
</table>

**Verhalten beim automatischen Bildlauf im interaktiven Video-Viewer**

Das automatische Bildlaufverhalten von Miniaturansichten der Viewer-Funktionen für interaktive Videos erfolgt unabhängig vom gewählten Anzeigemodus. 

Um beim Erstellen oder Bearbeiten einer Viewer-Vorgabe für interaktive Videos auf die Option „Automatischer Bildlauf“ zuzugreifen, rufen Sie die Registerkarte „Verhalten“ auf.  Tippen Sie auf der Registerkarte „Verhalten“ im Dropdownmenü **[!UICONTROL Ausgewählte Komponenten]** auf die Option für **[!UICONTROL interaktive Muster]**. Das Kontrollkästchen „Automatischer Bildlauf“ befindet sich unter dem Textfeld „IS-Befehl“. 

If you disable **[!UICONTROL Auto Scroll]** (clear the check box) in the viewer preset, during video playback by the user, the panel only displays the first thumbnail image for the entire length of the video. Allerdings kann der Benutzer ggf. mithilfe der Pfeilsymbole nach oben und nach unten einen manuellen Bildlauf durch die Miniaturansichten durchführen.

When you enable (select) **[!UICONTROL Auto Scroll]** in the viewer preset, during video playback, thumbnail images assigned to a video segment scroll into view at the start of a segment. Es gibt jedoch Instanzen, in denen bestimmte Miniaturansichten in einem Segment doppelt so lang angezeigt werden wie die Miniaturansichten vor und hinter ihnen. Zu diesem Verhalten kommt es, weil die Anzahl von Miniaturansichten in einem Segment größer ist als die Anzahl sichtbarer Miniaturansichten im Feld und diese nicht gleichmäßig verteilt sind. 

Gehen wir zu Illustrationszwecken von einem 30 Sekunden langen Videosegment aus.  Insgesamt gibt es neun Miniaturansichten, die im Laufe dieser 30 Sekunden angezeigt werden.  Die Größe Ihres Browsers wird dergestalt geändert, dass vier verfügbare Miniaturpositionen im Anzeigefeld vorliegen.  Das 30-sekündige Videozeitsegment ist in drei Untersegmente unterteilt.  In der folgenden Tabelle wird aufgeschlüsselt, welche Miniaturansichten für ein bestimmtes Zeituntersegment angezeigt werden: 

| **Video-Untersegment** | **Zeit des Teilsegments in Sekunden** | **Im Feld sichtbare Miniaturen** |
|---|---|---|
| 1 | 0–10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

Das Videountersegment 3 wird nicht über die Miniaturansichten hinweg erweitert, die ihm zugewiesen sind.  Beachten Sie, dass die Miniaturansichten 4, 6 und 7 im Anzeigefeld doppelt so lang sichtbar sind wie die anderen.

Die durch den Viewer zum Bestimmen der Anzahl der im seitlichen Bedienfeld angezeigten Miniaturansichten verwendete Logik basiert wie folgt auf der Anzahl der verfügbaren Positionen:

* Anzahl der Untersegmente = Aufrundung auf das nächste Untersegment (Anzahl der Miniaturansichten : Anzahl der sichtbaren Spots im Miniaturansichtsfeld, auf Grundlage der Browserfenstergröße)
Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten : 4 Slots = 2,25, was die Viewer-Logik auf 3 Untersegmente aufrundet.

* Anzahl der Miniaturen = Aufrundung auf die nächste Miniaturansicht (Anzahl der Miniaturansichten : Anzahl der Videountersegmente)
Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten : 3 Videountersegmente = 3 Miniaturansichten.

* Dauer des Untersegments = gesamte Videodauer : Anzahl der Videountersegmente
Unter Verwendung des Beispiels in der obigen Tabelle ergibt 30 Sekunden : 3 Segmente = 10 Sekunden anhaltende Anzeige jedes Segments.

#### Special considerations for creating a Carousel Banner Viewer Presets {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Beim Erstellen von Viewer-Vorgaben für Karussellbanner kann der Stil von Hotspots wie folgt geändert werden: 

|  | **Beschreibung** | **Aktionen** |
|---|---|---|
| **[!UICONTROL Hotspot-Symbol]** | Ändern des für Hotspot verwendeten Symbols | Um das Bild des Hotspot-Symbols zu ändern, tippen Sie auf der Registerkarte &quot; **[!UICONTROL Erscheinungsbild]** &quot;in der **[!UICONTROL ausgewählten Komponente]** auf **[!UICONTROL ImageMapEffect]**. Under **[!UICONTROL Icon]**, select **[!UICONTROL Background]** and in the **[!UICONTROL Image]** field navigate to the background image you want. |

## Activating or deactivating Viewer Presets {#activating-or-deactivating-viewer-presets}

Welche Viewer-Vorgaben in der Benutzeroberfläche verfügbar sind, hängt davon ab, welche Vorgaben im Autorenmodus aktiviert wurden. Nach dem Erstellen ist eine Viewer-Vorgabe standardmäßig auf „Ein“ eingestellt.  Wenn Sie die Vorgabe deaktivieren möchten, wird sie nicht im Autorenmodus angezeigt. Wenn die Vorgabe veröffentlicht wird. Sie wird immer veröffentlicht, unabhängig davon, ob sie aktiviert oder deaktiviert wurde. Ggf. müssen Sie Viewer-Vorgaben deaktivieren, wenn die Liste zu umfangreich wird oder wenn eine Viewer-Vorgabe nicht zur Verfügung gestellt werden soll.

**So aktivieren oder deaktivieren Sie Viewer-Vorgaben**

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools** (hammer icon) **[!UICONTROL > Assets > Viewer Presets]**.
1. Tippen Sie auf der Seite „Viewer-Vorgabe“ unter der Spaltenüberschrift **[!UICONTROL Status]** auf die Umschaltfläche zum Aktivieren bzw. Deaktivieren einer Viewer-Vorgabe. 

   Bei aktivierten Viewer-Vorgaben wird die Umschaltfläche rechts in einem blauen Feld angezeigt; bei deaktivierten Viewer-Vorgaben wird die Umschaltfläche links in einem hellgrauen Feld angezeigt. 

## Veröffentlichen von Viewer-Vorgaben  {#publishing-viewer-presets}

Wird der Status einer Viewer-Vorgabe aktiviert (auf „Ein“ gestellt), bedeutet dies, dass sie in der Komponente für dynamische Medien, in der Komponente für interaktive Medien und bei jeder Anzeige eines Assets sichtbar ist.

Um jedoch* *ein Asset mit einer Viewer-Vorgabe bereitzustellen, muss die Viewer-Vorgabe ebenfalls veröffentlicht werden. Alle Viewer-Vorgaben müssen aktiviert werden *und *veröffentlicht, um URL- oder Einbettungscode für ein Asset zu erhalten. Sie müssen alle standardmäßig vorhandenen Viewer-Vorgaben aktivieren und veröffentlichen, die von Dynamic Media bereitgestellt werden. Benutzerdefinierte Viewer-Vorgaben, die Sie selbst erstellen und hinzufügen, werden automatisch aktiviert, müssen jedoch ebenfalls veröffentlicht werden.

Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets). 

Siehe auch [Anzeigen von Assets in einer Vorschau](/help/assets/previewing-assets.md).

**So veröffentlichen Sie Viewer-Vorgaben**

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools** (hammer icon) **[!UICONTROL > Assets > Viewer Presets]**.
1. Wählen Sie eine oder mehrere Viewer-Vorgaben zum Veröffentlichen aus. 
1. Tippen Sie auf der Symbolleiste auf das Symbol **[!UICONTROL Veröffentlichen]**.

## Sortieren von Viewer-Vorgaben {#sorting-viewer-presets}

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools** (hammer icon) **[!UICONTROL > Assets > Viewer Presets]**.
1. Klicken Sie auf **[!UICONTROL Vorgabentitel]**, **[!UICONTROL Typ]**, **[!UICONTROL Veröffentlicht]** oder **[!UICONTROL Status]**, um nach dieser Spaltenüberschrift zu sortieren. Klicken Sie beispielsweise auf **[!UICONTROL Typ]**, um die Viewer-Vorgabentypen in alphabetischer oder in umgekehrt alphabetischer Reihenfolge zu sortieren. 

## Bearbeiten von Viewer-Vorgaben {#editing-viewer-presets}

Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird.  Wenn Sie eine standardmäßig vorhandene Viewer-Vorgabe bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern. 

**So bearbeiten Sie Viewer-Vorgaben**

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools** (hammer icon) **[!UICONTROL > Asset > Viewer Presets]**.
1. Wählen Sie eine Vorgabe aus, indem Sie das Kontrollkästchen links neben dem Viewer-Vorgabentitel aktivieren. 
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
1. Nehmen Sie im **[!UICONTROL Viewer-Vorgabeneditor]** die gewünschten Änderungen an der Viewer-Vorgabe vor. Dazu verwenden Sie die Optionen auf den Registerkarten **[!UICONTROL Erscheinungsbild]** und **[!UICONTROL Verhalten]**.

   Tippen Sie auf der Registerkarte **[!UICONTROL Erscheinungsbild]** in der oberen linken Ecke des Viewer-Vorgabeneditors auf **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]** oder **[!UICONTROL Telefon]**, um den Präsentationsmodus des Assets zu ändern.

1. Führen Sie in der oberen rechten Ecke der Seite eine der folgenden Aktionen aus:

   * Tap **[!UICONTROL Save]** to save your changes and return to the Viewer Preset page.
   * Tap **[!UICONTROL Cancel]** to void any changes you made and return to the Viewer Preset page.

## Löschen von benutzerdefinierten Viewer-Vorgaben {#deleting-custom-viewer-presets}

Sie können Viewer-Vorgaben löschen, die Sie Dynamic Media erstellt und hinzugefügt haben.

**So löschen Sie benutzerdefinierte Viewer-Vorgaben**

1. In the upper-left corner of AEM, tap the AEM logo, then in the left rail, tap **[!UICONTROL Tools]** (hammer icon) **[!UICONTROL > Assets > Viewer Presets]**.
1. On the Viewer Presets page, check a Preset Title, and then tap the **[!UICONTROL Trash]** icon.
1. Tippen Sie auf **[!UICONTROL Löschen]**. 

## Applying a Viewer Presets to an asset {#applying-a-viewer-preset-to-an-asset}

If you have already published both the asset and the selected viewer, the **[!UICONTROL URL]** and **[!UICONTROL Embed]** buttons appear after you select a viewer preset.

**So wenden Sie eine Viewer-Vorgabe auf ein Asset an**

1. Öffnen Sie das Asset, tippen Sie in der Nähe des oberen linken Bereichs der Seite auf das Dropdownmenü und wählen Sie **[!UICONTROL Viewer]** aus.

   >[!NOTE]
   >
   >If you have already published both the asset and the selected viewer, the **[!UICONTROL URL]** and **[!UICONTROL Embed]** buttons appear after you select a viewer preset.

1. Wählen Sie eine Viewer-Vorgabe im linken Bereich aus, um sie auf das Asset anzuwenden. 

   Sie können die [URL kopieren, um sie für andere Benutzer freizugeben](/help/assets/linking-urls-to-yourwebapplication.md). 

## Delivering assets with Viewer Presets {#delivering-assets-with-viewer-presets}

Informationen zum Abrufen der URLs für Viewer-Vorgaben finden Sie unter [Verknüpfen von URLs mit Ihrer Webanwendung](/help/assets/linking-urls-to-yourwebapplication.md). Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Webseite](/help/assets/embed-code.md).

Wenn Sie AEM als WCM verwenden, können Sie Assets mithilfe der Viewer-Vorgaben direkt auf der Seite hinzufügen.  Siehe [Hinzufügen von Assets mit dynamischen Medien zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md). 
