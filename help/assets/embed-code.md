---
title: Einbetten des Dynamic Media-Video- oder Bild-Viewers auf einer Web-Seite
description: Erfahren Sie, wie Sie Dynamic Media-Videos oder -Bilder auf einer Web-Seite einbetten.
uuid: 6f786521-eb6c-4c80-8c15-9bf97b56818f
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4ae76d8a-208f-4099-9f17-a94df424685e
feature: Viewer
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 99%

---


# Einbetten des Dynamic Media-Video-, Bild- oder Dimensional-Viewers auf einer Web-Seite {#embedding-the-video-or-image-viewer-on-a-web-page}

Verwenden Sie die Funktion **[!UICONTROL Einbettungs-Code]**, wenn Sie ein Video wiedergeben oder ein Asset anzeigen möchten, das auf einer Web-Seite eingebettet wurde. Kopieren Sie den Einbettungs-Code in die Zwischenablage, damit Sie ihn in die Web-Seiten einfügen können. Der Code kann im Dialogfeld **[!UICONTROL Einbettungs-Code]** nicht bearbeitet werden.

Sie betten URLs nur dann ein, wenn Sie AEM _nicht_ als Ihren WCM verwenden. Wenn Sie AEM als Ihren WCM verwenden, [fügen Sie die Assets direkt zu Ihrer Seite hinzu](adding-dynamic-media-assets-to-pages.md).

Siehe [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe [Bereitstellen von optimierten Bildern für eine responsive Site](responsive-site.md).

>[!NOTE]
>
>Der eingebettete Code kann erst kopiert werden, nachdem Sie das ausgewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

**So betten Sie den Dynamic Media-Video- oder Bild-Viewer auf einer Web-Seite ein**

1. Navigieren Sie zum *veröffentlichten* Video- oder Bild-Asset, dessen Einbettungs-Code Sie kopieren möchten.

   Denken Sie daran, dass der Einbettungscode nur *nach* der ersten *Veröffentlichung* der Assets kopiert werden können. Darüber hinaus müssen die Viewer-Vorgabe oder die Bildvorgabe ebenfalls veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. Wählen Sie in der linken Leiste das Dropdown-Menü aus und tippen Sie auf **[!UICONTROL Viewer.]**
1. Tippen Sie auf der linken Schiene auf den Namen einer Viewer-Vorgabe. Die Viewer-Vorgabe wird auf das Asset angewendet.
1. Tippen Sie auf **[!UICONTROL Einbetten.]**
1. Kopieren Sie im Dialogfeld **[!UICONTROL Einbettungs-Code]** den gesamten Code in die Zwischenablage und tippen Sie dann auf **[!UICONTROL Schließen.]**
1. Fügen Sie den Integrations-Code in die Web-Seiten ein.

## Verwendung von HTTP/2 zur Bereitstellung von Dynamic Media-Assets {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Webprotokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2.md).
