---
title: Einbetten des Dynamic Media-Video-, Bild- oder Dimensional-Viewers auf einer Web-Seite
description: Erfahren Sie, wie Sie Dynamic Media-Videos, -Bilder oder -3D-Bilder in eine Web-Seite einbetten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: Viewers
role: User, Admin
exl-id: 203ea349-ef4c-421c-b4b6-76ee9d46ec34
source-git-commit: 04050f31742c926b45235595f6318929d3767bd8
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 96%

---

# Einbetten des Dynamic Media-Video-, Bild- oder Dimensional-Viewers auf einer Web-Seite {#embedding-the-video-or-image-viewer-on-a-web-page}

Verwenden Sie die Funktion **[!UICONTROL Einbettungs-Code]**, wenn Sie ein Video wiedergeben oder ein Asset anzeigen möchten, das auf einer Web-Seite eingebettet wurde. Kopieren Sie den Einbettungs-Code in die Zwischenablage, damit Sie ihn in die Web-Seiten einfügen können. Der Code kann im Dialogfeld **[!UICONTROL Einbettungs-Code]** nicht bearbeitet werden.

Betten Sie URLs nur dann ein, wenn Sie Adobe Experience Manager *nicht* als Ihr WCM verwenden. Wenn Sie Experience Manager als Ihr WCM verwenden, [fügen Sie die Assets direkt zu Ihrer Seite hinzu](adding-dynamic-media-assets-to-pages.md).

Siehe [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe [Bereitstellen optimierter Bilder für eine responsive Website](responsive-site.md).

>[!NOTE]
>
>Der Einbettungscode kann erst kopiert werden, nachdem Sie das ausgewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

**Gehen Sie zum Einbetten des Dynamic Media-Video-, -Bild- oder Dimensional-Viewers in eine Web-Seite folgendermaßen vor:**

1. Navigieren Sie zum *veröffentlichten* Video- oder Bild-Asset, dessen Einbettungs-Code Sie kopieren möchten.

   Denken Sie daran, dass der Einbettungs-Code nur *nach* der ersten *Veröffentlichung* der Assets kopiert werden können. Darüber hinaus müssen die Viewer-Vorgabe oder die Bildvorgabe ebenfalls veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. Wählen Sie in der linken Leiste im Dropdown-Menü **[!UICONTROL Viewer]** aus.
1. Wählen Sie in der linken Leiste den Namen einer Viewer-Vorgabe aus. Die Viewer-Vorgabe wird auf das Asset angewendet.
1. Klicken Sie auf **[!UICONTROL Einbetten]**.
1. Kopieren Sie im Dialogfeld **[!UICONTROL Einbettungs-Code]** den gesamten Code in die Zwischenablage und klicken Sie dann auf **[!UICONTROL Schließen]**.
1. Fügen Sie den Integrations-Code in die Web-Seiten ein.

## Verwenden von HTTP/2 zur Bereitstellung von Dynamic Media-Assets   {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Web-Protokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Die Bereitstellung von Dynamic Media-Assets kann über HTTP/2 erfolgen, das schnellere Antwort- und Ladezeiten bietet.

Siehe [Bereitstellung von Inhalt über HTTP/2](http2.md), um ausführliche Informationen zu den ersten Schritten mit HTTP/2 mit Ihrem Dynamic Media-Konto zu erhalten.
