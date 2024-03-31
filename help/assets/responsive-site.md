---
title: Bereitstellen von optimierten Bildern für eine responsive Website
description: Erfahren Sie, wie Sie mit der Funktion für responsiven Code optimierte Bilder bereitstellen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: Asset Management
role: User, Admin
exl-id: 753d806f-5f44-4d73-a3a3-a2a0fc3e154b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 100%

---

# Bereitstellen optimierter Bilder für eine responsive Site {#delivering-optimized-images-for-a-responsive-site}

Verwenden Sie die Funktion für responsiven Code, wenn Sie den Code für responsive Verarbeitung für Ihren Web-Entwickler freigeben möchten. Kopieren Sie den responsiven Code (**[!UICONTROL RESS]**) in die Zwischenablage, damit Sie ihn für Ihren Web-Entwickler freigeben können.

Verwenden Sie diese Funktion, wenn sich Ihre Website auf einem Drittanbieter-WCM befindet. Wenn sich Ihre Website jedoch in Adobe Experience Manager befindet, rendert ein Offsite-Image-Server das Bild und stellt es der Web-Seite bereit.

Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Web-Seite](embed-code.md).

Siehe auch [Verknüpfen von URLs mit Ihrer Web-Anwendung](linking-urls-to-yourwebapplication.md).

**So stellen Sie optimierte Bilder für eine responsive Website bereit:**

1. Wechseln Sie zu dem Bild, für das Sie responsiven Code bereitstellen möchten, und wählen Sie im Dropdown-Menü **[!UICONTROL Ausgabedarstellungen]** aus.

   ![chlimage_1-408](assets/chlimage_1-408.png)

1. Wählen Sie eine responsive Bildvorgabe aus. Die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL RESS]** werden angezeigt.

   ![chlimage_1-409](assets/chlimage_1-208.png)

   >[!NOTE]
   >
   >Das ausgewählte Asset *und* die ausgewählte Bildvorgabe oder Viewer-Vorgabe müssen veröffentlicht werden, um die Schaltfläche **[!UICONTROL URL]** oder **[!UICONTROL RESS]** verfügbar zu machen.
   >
   >Wenn Sie Dynamic Media im Hybridmodus ausführen, müssen Sie Bildvorgaben manuell veröffentlichen. Im Scene7-Modus von Dynamic Media werden Bildvorgaben automatisch veröffentlicht.

1. Wählen Sie **[!UICONTROL RESS]** aus.

   ![chlimage_1-410](assets/chlimage_1-410.png)

1. Wählen Sie im Dialogfeld **[!UICONTROL Responsive Bilder einbetten]** den responsiven Code-Text aus und fügen Sie ihn in Ihre Website ein, um auf das responsive Asset zuzugreifen.
1. Bearbeiten Sie die Standard-Breakpoints im Embed-Code direkt im Code so, dass sie denen der responsiven Website entsprechen. Testen Sie außerdem die verschiedenen Bildauflösungen bei verschiedenen Seiten-Breakpoints.

## Bereitstellen von Dynamic Media-Assets mit HTTP/2 {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Web-Protokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Die Bereitstellung von Dynamic Media-Assets kann über HTTP/2 erfolgen, das schnellere Antwort- und Ladezeiten bietet.

Unter [Bereitstellung von Inhalten über HTTP/2](http2.md) finden Sie ausführliche Informationen zu den ersten Schritten mit HTTP/2 mit Ihrem Dynamic Media-Konto.
