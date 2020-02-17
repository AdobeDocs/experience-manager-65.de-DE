---
title: Einbetten des Video- oder Bild-Viewers für dynamische Medien in eine Webseite
description: Erfahren Sie, wie Sie Videos oder Bilder mit dynamischen Medien auf einer Webseite einbetten
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Embedding the Dynamic Media Video or Image viewer on a web page {#embedding-the-video-or-image-viewer-on-a-web-page}

Use the **[!UICONTROL Embed Code]** feature when you want to play the video or view an asset embedded on a web page. You copy the embed code to the clipboard so you can paste it in your web pages. Editing of the code is not permitted in the **[!UICONTROL Embed Code]** dialog box.

You embed URLs only if you are _not_ using AEM as your WCM. Wenn Sie AEM als Ihren WCM verwenden, [fügen Sie die Assets direkt zu Ihrer Seite hinzu](adding-dynamic-media-assets-to-pages.md).

See [Linking URLs to your Web Application.](linking-urls-to-yourwebapplication.md)

See [Delivering Optimized Images for a Responsive Site.](responsive-site.md)

>[!NOTE]
>
>Der eingebettete Code kann erst kopiert werden, nachdem Sie das ausgewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

**So betten Sie das Video oder den Bild-Viewer für dynamische Medien in eine Webseite ein**

1. Navigate to the *published* video or image asset whose embed code you want to copy.

   Denken Sie daran, dass der Einbettungscode erst kopiert werden kann, *nachdem* Sie die Assets *veröffentlicht* haben. Darüber hinaus müssen die Viewer-Vorgabe oder die Bildvorgabe ebenfalls veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. In the left rail, select the drop-down menu and tap **[!UICONTROL Viewers]**.
1. Tippen Sie auf der linken Schiene auf einen Viewer-Vorgabennamen. Die Viewer-Vorgabe wird auf das Asset angewendet.
1. Tippen Sie auf **[!UICONTROL Einbetten]**.
1. In the **[!UICONTROL Embed Code]** dialog box, copy the entire code to the clipboard, and then tap **[!UICONTROL Close]**.
1. Fügen Sie den Integrationscode in die Webseiten ein.

## Verwendung von HTTP/2 zur Bereitstellung von Dynamic Media-Assets {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Webprotokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2.md).
