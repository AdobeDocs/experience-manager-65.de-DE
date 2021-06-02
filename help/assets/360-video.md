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
feature: 360-Grad-VR-Video
role: Business Practitioner, Administrator
exl-id: 0c2077a7-bd16-484b-980f-4d4a1a681491
source-git-commit: a4e9a4003bf0ce686578d3f8b3fddc19bc49dfb4
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 79%

---

# 360-Grad-/VR-Video {#vr-video}

360-Grad-Videos zeichnen ein Motiv aus allen Richtungen gleichzeitig auf. Sie werden mit einer omnidirektionalen Kamera oder mit mehreren Kameras aufgenommen. Während der Wiedergabe auf einer flachen Anzeige hat der Benutzer die Kontrolle über den Anzeigewinkel. -Wiedergabe auf Mobilgeräten verwendet in der Regel die integrierten gyroskopischen Steuerelemente.

Dynamic Media – Scene7-Modus bietet native Unterstützung für die Bereitstellung von 360-Grad-Videoassets. Standardmäßig ist keine weitere Konfiguration für die Anzeige oder die Wiedergabe erforderlich. 360-Grad-Videos werden mit Standardvideoerweiterungen wie .mp4, .mkv und .mov bereitgestellt. Der am häufigsten verwendete Codec ist H.264.

In diesem Abschnitt erfahren Sie, wie Sie mit dem 360-Grad-/VR-Video-Viewer ein Panoramavideo für eine interaktive Anzeige eines Raums, einer Eigenschaft, eines Standorts, einer Landschaft oder eines medizinischen Verfahrens rendern.

Räumliches Audio wird derzeit nicht unterstützt. Falls Audio in Stereo gemischt wird, ändert sich die Balance (L/R) nicht, wenn der Kunde den Anzeigewinkel der Kamera ändert.

Informationen hierzu finden Sie in [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

## 360-Grad-Video in Aktion {#video-in-action}

Tippen Sie auf [Space Station 360](https://mobiletest.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS), um ein Browser-Fenster zu öffnen und ein 360-Grad-Video anzusehen. Ziehen Sie während der Videowiedergabe den Mauszeiger an eine neue Position, um den Anzeigewinkel zu ändern.

![360-Grad-Video-Beispiel](assets/6_5_360videoiss_simplified.png)-*Videoframe aus Space Station 360*

## 360-Grad-/VR-Video und Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Sie können 360-Grad-/VR-Videos mit Adobe Premiere Pro anzeigen und bearbeiten. Beispielsweise können Sie Logos und Text in einer Szene platzieren sowie speziell für Panoramavideos entwickelte Effekte und Überblendungen anwenden.

Weitere Informationen finden Sie unter [Bearbeiten von 360-Grad-/VR-Videos](https://helpx.adobe.com/de/premiere-pro/how-to/edit-360-vr-video.html).

## Hochladen von Assets für die Verwendung mit dem 360-Grad-Video-Viewer {#uploading-assets-for-use-with-the-video-viewer}

360 Video-Assets, die in Adobe Experience Manager hochgeladen werden, werden auf einer Asset-Seite wie normale Video-Assets als **Multimedia** gekennzeichnet.

![6_5_360video-selecttopreview](assets/6_5_360video-selecttopreview.png)
*Ein hochgeladenes 360-Grad-Video-Asset in der Kartenansicht. Das Asset wird als „Multimedia“ gekennzeichnet.*

**So laden Sie Assets für die Verwendung mit dem 360-Grad-Video-Viewer hoch:**

1. Erstellen Sie einen Ordner für Ihr 360-Grad-Video-Asset.
1. [Wenden Sie ein adaptives Videoprofil auf den Ordner an.](/help/assets/video-profiles.md#applying-a-video-profile-to-folders)

   Das Rendern von 360-Grad-Videos ist mit höheren Anforderungen an die Auflösung des Quellvideos sowie der kodierten Ausgabedarstellungen verbunden als Standard-Videoinhalte.

   Sie können das vordefinierte adaptive Videoprofil von Dynamic Media verwenden. Mit diesem erzielen Sie jedoch eine etwas schlechtere Qualität bei 360-Grad-Videos als bei normalen Videos, die mit den gleichen Einstellungen kodiert und mit einem normalen Video-Viewer gerendert wurden. Wenn Sie hochwertige 360-Grad-Videos benötigen, gehen Sie wie folgt vor:

   * Idealerweise sollten Sie Ihren ursprünglichen 360-Grad-Videoinhalt mit einer der folgenden Auflösungen verwenden:

      * 1080p – 1920 x 1080 (Full HD- oder FHD-Auflösung) oder
      * 2160p – 3840 x 2160 (4K-, UHD- oder Ultra HD-Auflösung). Diese hohe Auflösung ist häufig auf Premium-Fernsehgeräten und Computermonitoren verfügbar. Die 2160p-Auflösung wird häufig als „4K“ bezeichnet, da die Breite fast 4000 Pixel beträgt. Das heißt, sie bietet viermal so viele Pixel wie 1080p.
   * [Erstellen Sie ein benutzerdefiniertes adaptives Videoprofil](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) mit hochwertigeren Ausgabedarstellungen. Erstellen Sie beispielsweise ein adaptives Videoprofil, das die folgenden drei Einstellungen enthält:

      * width=auto; height=720; bitrate=2500 kbps
      * width=auto; height=1080; bitrate=5000 kbps
      * width=auto; height=1440; bitrate=6600 kbps
   * Verarbeiten Sie 360-Grad-Videoinhalte in einem Ordner, der ausschließlich 360-Grad-Video-Assets enthält.

   Dieser Ansatz stellt höhere Anforderungen an das Netzwerk und die CPU des Endbenutzers.

1. [Laden Sie Ihr Video in den Ordner hoch](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

## Überschreiben des Standardseitenverhältnisses von 360-Grad-Videos  {#overriding-the-default-aspect-ratio-of-videos}

Hochgeladene Assets sind als 360-Grad-Videos und für die Verwendung mit dem 360-Grad-Video-Viewer geeignet, wenn sie ein Seitenverhältnis von 2 aufweisen.

Standardmäßig erkennt Experience Manager das Video als &quot;360&quot;, wenn das Seitenverhältnis (Breite/Höhe) 2,0 beträgt. Wenn Sie Administrator sind, können Sie die standardmäßige Seitenverhältniseinstellung von 2 überschreiben, indem Sie die optionale Eigenschaft `s7video360AR` in CRXDE Lite wie folgt festlegen:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

   * **Eigenschaftstyp**: Doppelt
   * **Wert:** Gleitkomma-Seitenverhältnis, standardmäßig 2.0.

Wenn Sie diese Eigenschaft festlegen, wird sie umgehend auf vorhandene und neu hochgeladene Videos angewendet.

Das Seitenverhältnis gilt für 360-Grad-Video-Assets für die Asset-Detailseite und die [WCM-Komponente für 360-Grad-Videos](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components).

Laden Sie zunächst 360-Grad-Videos hoch.

## Anzeigen einer Vorschau für 360-Grad-Videos {#previewing-video}

Mit der Vorschau können Sie prüfen, wie das 360-Grad-Video bei Ihren Kunden aussieht, und sicherstellen, dass es sich wie erwartet verhält.

Siehe auch [Bearbeiten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md#editing-viewer-presets).

Wenn das 360-Grad-Video Ihren Vorstellungen entspricht, können Sie es veröffentlichen.

Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite.](/help/assets/embed-code.md)
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in Adobe Experience Manager Sites.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).

**So zeigen Sie eine Vorschau von 360-Grad-Videos an:**

1. Navigieren Sie in **[!UICONTROL Assets]** zu einem von Ihnen erstellten 360-Grad-Video. Tippen Sie auf das 360-Grad-Video-Asset, damit Sie es im Vorschaumodus öffnen können.

   ![6_5_360video-selecttopreview-1](assets/6_5_360video-selecttopreview-1.png)

   Tippen Sie auf das 360-Grad-Video-Asset, damit Sie eine Vorschau des Videos anzeigen können.

1. Tippen Sie auf der Vorschauseite links oben auf der Seite auf die Dropdown-Liste und wählen Sie **[!UICONTROL Viewer.]** aus.

   ![6_5_360video-preview-viewers](assets/6_5_360video-preview-viewers.png)

   Tippen Sie in der Viewer-Liste auf **[!UICONTROL Video360_social]** und führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie den Mauszeiger über das Video, wenn Sie den Anzeigewinkel der statischen Szene ändern möchten.
   * Tippen Sie auf die Schaltfläche **[!UICONTROL Wiedergabe]** des Videos, wenn Sie die Wiedergabe starten möchten. Ziehen Sie bei der Wiedergabe des Videos den Mauszeiger über das Video, um den Anzeigewinkel zu ändern.

   ![6_5_360video-preview-video360-social ](assets/6_5_360video-preview-video360-social.png)*Screenshot eines 360-Grad-Videos.*

   * Tippen Sie in der Viewer-Liste auf **[!UICONTROL Video360VR.]**

      Virtual Reality (VR)-Videos sind interaktive Videoinhalte, die über Virtual Reality-Headsets angezeigt werden. Wie bei herkömmlichen Videos erstellen Sie VR-Videos zu Beginn, wenn ein Video mit 360-Grad-Videokameras aufgezeichnet oder erfasst wird.
   ![6_5_360video-preview-video360vr](assets/6_5_360video-preview-video360vr.png)
   *Screenshot eines 360-Grad-VR-Videos.*

1. Tippen Sie oben rechts auf der Vorschauseite auf **[!UICONTROL Schließen.]**

## Veröffentlichen von 360-Grad-Videos {#publishing-video}

Veröffentlichen Sie das 360-Grad-Video, damit Sie es verwenden können. Die Veröffentlichung eines 360-Grad-Videos aktiviert die URL und den Einbettungs-Code. Außerdem wird das 360-Grad-Video in der Dynamic Media-Cloud veröffentlicht, die für eine skalierbare und leistungsfähige Bereitstellung mit einem CDN integriert ist.

Unter [Veröffentlichen von Dynamic Media-Assets](/help/assets/publishing-dynamicmedia-assets.md) finden Sie Details zum Veröffentlichen von 360-Grad-Videos.
Siehe auch [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md).
Siehe auch [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in Adobe Experience Manager Sites.
Siehe auch [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/adding-dynamic-media-assets-to-pages.md).
