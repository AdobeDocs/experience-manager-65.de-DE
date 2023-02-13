---
title: 360-Grad-/VR-Video
description: Erfahren Sie mehr über die Verwendung von 360-Grad- und Virtual Reality (VR)-Videos in Dynamic Media.
uuid: c21bf2c0-7acc-401f-857e-0186de86e7a1
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: aac3c850-ae84-4bff-80de-d370e150f675
docset: aem65
feature: 360 VR Video
role: User, Admin
exl-id: 0c2077a7-bd16-484b-980f-4d4a1a681491
source-git-commit: c0a60ec39e35fa8113ce9e1795561709b9c7e289
workflow-type: ht
source-wordcount: '1109'
ht-degree: 100%

---

# 360-Grad-/VR-Video {#vr-video}

360-Grad-Videos zeichnen ein Motiv aus allen Richtungen gleichzeitig auf. Sie werden mit einer omnidirektionalen Kamera oder mit mehreren Kameras aufgenommen. Während der Wiedergabe auf einer flachen Anzeige können Benutzende den Anzeigewinkel bestimmen; bei der Wiedergabe auf Mobilgeräten werden in der Regel die integrierten gyroskopischen Funktionen verwendet.

Der Dynamic Media – Scene7-Modus bietet native Unterstützung für die Bereitstellung von 360-Grad-Video-Assets. Standardmäßig ist keine weitere Konfiguration für die Anzeige oder die Wiedergabe erforderlich. 360-Grad-Videos werden mit Standardvideoerweiterungen wie .mp4, .mkv und .mov bereitgestellt. Der am häufigsten verwendete Codec ist H.264.

In diesem Abschnitt erfahren Sie, wie Sie mit dem 360-Grad-/VR-Video-Viewer ein Panoramavideo für eine interaktive Anzeige eines Raums, einer Eigenschaft, eines Standorts, einer Landschaft oder eines medizinischen Verfahrens rendern.

Räumliches Audio wird derzeit nicht unterstützt. Falls Audio in Stereo gemischt wird, ändert sich die Balance (L/R) nicht, wenn der Kunde den Anzeigewinkel der Kamera ändert.

Informationen hierzu finden Sie in [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

## 360-Grad-Video in Aktion {#video-in-action}

Wählen Sie [Space Station 360](https://s7d1.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS), um ein Browser-Fenster zu öffnen und ein 360-Grad-Video anzusehen. Ziehen Sie während der Videowiedergabe den Mauszeiger an eine neue Position, um den Anzeigewinkel zu ändern.

![360-Grad-Videobeispiel mit der im Weltraum schwebenden internationalen Raumstation und der Erde und Sonne dahinter.](assets/6_5_360videoiss_simplified.png)
*Videoframe aus Space Station 360*

## 360-Grad-/VR-Video und Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Sie können 360-Grad-/VR-Videos mit Adobe Premiere Pro anzeigen und bearbeiten. Beispielsweise können Sie Logos und Text in einer Szene platzieren sowie speziell für Panoramavideos entwickelte Effekte und Überblendungen anwenden.

Weitere Informationen finden Sie unter [Bearbeiten von 360-Grad-/VR-Videos](https://helpx.adobe.com/de/premiere-pro/how-to/edit-360-vr-video.html).

## Hochladen von Assets für die Verwendung mit dem 360-Grad-Video-Viewer {#uploading-assets-for-use-with-the-video-viewer}

Beim Hochladen in Adobe Experience Manager werden 360-Grad-Video-Assets wie normale Video-Assets auf der Asset-Seite als **Multimedia** gekennzeichnet.

![6_5_360video-selecttopreview](assets/6_5_360video-selecttopreview.png)
*Ein hochgeladenes 360-Grad-Video-Asset in der Kartenansicht. Das Asset wird als „Multimedia“ gekennzeichnet.*

**Hochladen von Assets für die Verwendung mit dem 360-Grad-Video-Viewer:**

1. Erstellen Sie einen dedizierten Ordner für Ihr 360-Grad-Video-Asset.
1. [Wenden Sie ein adaptives Videoprofil auf den Ordner an](/help/assets/video-profiles.md#applying-a-video-profile-to-folders).

   Das Rendern von 360-Grad-Videos ist mit höheren Anforderungen an die Auflösung des Quellvideos sowie der codierten Ausgabeformate verbunden als bei Standard-Videoinhalten.

   Sie können das vordefinierte adaptive Videoprofil von Dynamic Media verwenden. Mit diesem erzielen Sie jedoch eine etwas schlechtere Qualität bei 360-Grad-Videos als bei normalen Videos, die mit den gleichen Einstellungen codiert und mit einem normalen Video-Viewer gerendert wurden. Wenn Sie hochwertige 360-Grad-Videos benötigen, gehen Sie wie folgt vor:

   * Idealerweise sollten Ihre ursprünglichen 360-Grad-Videoinhalte eine der folgenden Auflösungen haben:

      * 1080p – 1920 x 1080 (Full HD- oder FHD-Auflösung) oder
      * 2160p – 3840 x 2160 (4K-, UHD- oder Ultra HD-Auflösung). Diese hohe Auflösung ist häufig auf Premium-Fernsehgeräten und Computer-Monitoren verfügbar. Die 2160p-Auflösung wird häufig als „4K“ bezeichnet, da die Breite fast 4000 Pixel beträgt. Das heißt, sie bietet viermal so viele Pixel wie 1080p.
   * [Erstellen Sie ein benutzerdefiniertes adaptives Videoprofil](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) mit hochwertigeren Ausgabedarstellungen. Ein Beispiel: Sie möchten ein adaptives Videoprofil erstellen, das diese drei Einstellungen enthält:

      * width=auto; height=720; bitrate=2500 kbps
      * width=auto; height=1080; bitrate=5000 kbps
      * width=auto; height=1440; bitrate=6600 kbps
   * Verarbeiten Sie 360-Grad-Videoinhalte in einem Ordner, der ausschließlich 360-Grad-Video-Assets enthält.

   Dieser Ansatz stellt höhere Anforderungen an das Netzwerk und die CPU des Endbenutzers.

1. [Laden Sie Ihr Video in den Ordner hoch](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

## Überschreiben des Standardseitenverhältnisses von 360-Grad-Videos  {#overriding-the-default-aspect-ratio-of-videos}

Hochgeladene Assets sind als 360-Grad-Videos und für die Verwendung mit dem 360-Grad-Video-Viewer geeignet, wenn sie ein Seitenverhältnis von 2 aufweisen.

Standardmäßig erkennt Experience Manager Videos als „360“, wenn ihr Seitenverhältnis (Breite/Höhe) 2,0 beträgt. Als Admin können Sie das Standardseitenverhältnis von 2 außer Kraft setzen, indem Sie die optionale Eigenschaft `s7video360AR` in CRXDE Lite unter folgendem Pfad festlegen:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

   * **Eigenschaftstyp**: Doppelt
   * **Wert**: Gleitkomma-Seitenverhältnis, standardmäßig 2.0.

Wenn Sie diese Eigenschaft festlegen, wird sie umgehend auf vorhandene und neu hochgeladene Videos angewendet.

Das Seitenverhältnis gilt für 360-Grad-Video-Assets für die Asset-Detailseite und die [WCM-Komponente für 360-Grad-Videos](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

Laden Sie zunächst 360-Grad-Videos hoch.

## Vorschau eines 360-Grad-Videos {#previewing-video}

Mit der Vorschau können Sie prüfen, wie das 360-Grad-Video bei Ihren Kunden aussieht, und sicherstellen, dass es sich wie erwartet verhält.

Siehe auch [Bearbeiten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md#editing-viewer-presets).

Wenn das 360-Grad-Video Ihren Vorstellungen entspricht, können Sie es veröffentlichen.

Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md).
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in Adobe Experience Manager Sites.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

**Vorschau von 360-Grad-Videos:**

1. Gehen Sie in **[!UICONTROL Assets]** zu einem von Ihnen erstellten 360-Grad-Video. Wählen Sie das 360-Grad-Video-Asset aus, damit Sie es im Vorschaumodus öffnen können.

   ![6_5_360video-selecttopreview-1](assets/6_5_360video-selecttopreview-1.png)

   Wählen Sie das 360-Grad-Video-Asset aus, damit Sie eine Vorschau des Videos anzeigen können.

1. Klicken Sie links oben auf der Vorschauseite auf die Dropdown-Liste und wählen Sie **[!UICONTROL Viewer]** aus.

   ![6_5_360video-preview-viewers](assets/6_5_360video-preview-viewers.png)

   Wählen Sie in der Viewer-Liste **[!UICONTROL Video360_social]** aus und führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie den Mauszeiger über das Video, um den Anzeigewinkel der statischen Szene zu ändern.
   * Wählen Sie die Schaltfläche **[!UICONTROL Play]**, um die Wiedergabe des Videos zu starten. Ziehen Sie während der Wiedergabe des Videos den Mauszeiger über das Video, um den Anzeigewinkel zu ändern.

   ![Screenshot der im Weltraum schwebenden internationalen Weltraumstation mit Erde und Sonne im Hintergrund ](assets/6_5_360video-preview-video360-social.png)*Ein 360-Grad-Screenshot.*

   * Wählen Sie in der Viewer-Liste **[!UICONTROL Video360VR]** aus.

      Virtual Reality (VR)-Videos sind interaktive Videoinhalte, die über Virtual-Reality-Headsets angezeigt werden. Wie bei herkömmlichen Videos erstellen Sie VR-Videos zu Beginn, wenn ein Video mit 360-Grad-Videokameras aufgezeichnet oder erfasst wird.
   ![Screenshot einer Nahaufnahme der im Weltraum schwebenden internationalen Weltraumstation, wobei Erde und Sonne teilweise im Hintergrund sichtbar sind](assets/6_5_360video-preview-video360vr.png)
   *Screenshot eines 360-Grad-VR-Videos.*

1. Klicken Sie oben rechts auf der Vorschauseite auf **[!UICONTROL Schließen]**.

## Veröffentlichen von 360-Grad-Videos {#publishing-video}

Veröffentlichen Sie das 360-Grad-Video, damit Sie es verwenden können. Die Veröffentlichung eines 360-Grad-Videos aktiviert die URL und den Einbettungs-Code. Außerdem wird das 360-Grad-Video in der Dynamic Media-Cloud veröffentlicht, die für eine skalierbare und leistungsfähige Bereitstellung mit einem CDN integriert ist.

Unter [Veröffentlichen von Dynamic Media-Assets](/help/assets/publishing-dynamicmedia-assets.md) finden Sie Details zum Veröffentlichen von 360-Grad-Videos.
Siehe auch [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md).
Siehe auch [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in Adobe Experience Manager Sites.
Siehe auch [Hinzufügen von Dynamic Media Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).
