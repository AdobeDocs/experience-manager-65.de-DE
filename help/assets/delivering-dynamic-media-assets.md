---
title: Bereitstellen von Dynamic Media-Assets
description: Informationen zum Bereitstellen von Dynamic Media-Assets
uuid: 23eddf83-34f5-4aae-8b81-d1cd7a098a7e
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e3b44330-d476-49c6-b7ba-079d0d60e500
docset: aem65
role: User, Admin
exl-id: 274af114-845a-46bd-b091-802cf589687a
feature: Asset Management,Renditions
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 87%

---

# Bereitstellen von Dynamic Media-Assets{#delivering-dynamic-media-assets}

Wie Sie Dynamic Media-Assets (sowohl Videos als auch Bilder) bereitstellen können, ist davon abhängig, wie Ihre Website implementiert ist.

Mit Dynamic Media haben Sie mehrere Optionen:

* Wenn Ihre Website auf Adobe Experience Manager gehostet wird, können Sie die Dynamic Media-Assets direkt zu Ihrer Seite hinzufügen.
* Wenn sich Ihre Website nicht in Experience Manager befindet, können Sie eine der folgenden Aktionen ausführen:

   * Betten Sie Ihr Video oder Bild auf Ihrer Website ein.
   * Verknüpfen Sie URLs mit Ihrer Web-Anwendung. Verwenden Sie die Verknüpfung, wenn Sie einen Video-Player als Popup- oder modales Fenster bereitstellen möchten.
   * Wenn Ihre Website dynamisch ist, können Sie [optimierte Bilder bereitstellen](/help/assets/responsive-site.md).

>[!NOTE]
>
>Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert im letzten Moment abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. Weitere Informationen finden Sie unter [Intelligente Bildbearbeitung](/help/assets/imaging-faq.md).

Weitere Informationen finden Sie in den folgenden Themen:

* [Hinzufügen von Dynamic Media-Assets zu Webseiten](/help/assets/adding-dynamic-media-assets-to-pages.md)
* [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/embed-code.md)
* [Aktivieren des Hotlink-Schutzes in Dynamic Media](/help/assets/hotlink-protection.md)
* [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/linking-urls-to-yourwebapplication.md)
* [Bereitstellen optimierter Bilder für eine responsive Website](/help/assets/responsive-site.md)
* [Bereitstellung von Inhalten per HTTP/2](/help/assets/http2.md)
* [Invalidierung des CDN-Cache über Dynamic Media Classic](/help/assets/invalidate-cdn-cache-dm-classic.md)
* [Verwenden von Regelsätzen zum Konvertieren von URLs](/help/assets/using-rulesets-to-transform-urls.md)


## Bereitstellung von Dynamic Media-Assets über HTTP/2 {#http-delivery-of-dynamic-media-assets}

Experience Manager unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur Bereitstellung von Inhalten über HTTP/2](/help/sites-administering/scene7-http2faq.md).
