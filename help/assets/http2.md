---
title: 'Bereitstellung von Inhalt über HTTP/2 '
description: HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 100%

---


# Bereitstellung von Inhalt über HTTP/2  {#http-delivery-of-content}

Adobe freut sich, die Bereitstellung von Inhalt über HTTP/2 zu präsentieren, die eine Verbesserung der Leistung mit sich bringt.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und seine Vorteile kurz und einfach beschrieben:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Verbesserung der Leistung ist von verschiedenen Faktoren abhängig, z. B. dem Code Ihrer Website oder wie Sie Dynamic Media und Geräte, Bildschirme und Standorte von Verbrauchern nutzen.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen?   {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Sie verwenden das von Adobe gebündelte CDN (Content Delivery Network) als Teil Ihrer Dynamic Media-Lizenz.
* Sie verwenden eine dedizierte (non- company-h.assetsadobe#.com) Domäne.

   Wenn Sie bereits über eine dedizierte Domäne verfügen, können Sie sich über den technischen Support anmelden.

   Wenn Sie nicht über eine dedizierte Domäne verfügen, wird Adobe Ihre Umstellung auf HTTP/2 für 2018 einplanen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Sie müssen den Wechsel auf HTTP/2 beantragen, da er nicht automatisch erfolgt.

1. Senden Sie eine Anfrage an den technischen Support, um auf HTTP/2 umzustellen. Siehe [Zugriff auf das AEM-Supportportal](https://helpx.adobe.com/de/experience-manager/kb/accessing-aem-support-portal.html).

   1. In der Anfrage geben Sie folgende Informationen an:

      1. Name des Hauptansprechpartners, E-Mail, Telefon.
      1. Alle Domänen, die auf HTTP/2 umgestellt werden sollen.
      1. Stellen Sie sicher, dass Sie für Ihre Rich Media-Anforderungen sicheres HTTPS verwenden.
      1. Stellen Sie sicher, dass Sie das CDN von Adobe verwenden und nicht mittels einer direkten Beziehung verwaltet werden.
      1. Stellen Sie sicher, dass Sie eine dedizierte Domäne verwenden. Wenn Sie Dynamic Media verwenden, verfügen Sie bereits über eine dedizierte Domäne.
   1. Der technische Support reiht Sie entsprechend der Reihenfolge der eingegangenen Anfragen in die HTTP/2-Kundenwarteschlange ein.
   1. Wenn Adobe für die Bearbeitung Ihrer Anfrage bereit ist, setzt sich der Support mit Ihnen in Verbindung, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
   1. Nach Abschluss werden Sie benachrichtigt, wonach Sie prüfen können, ob die Umstellung auf HTTP/2 erfolgreich durchgeführt wurde.

      Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

      Für Firefox und Chrome gibt es eine Erweiterung namens „HTTP/2 and SPDY Indicator“. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und die Beschriftung „X-Firefox-Spdy“ : „h2“ angezeigt. 


## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim technischen Support eingehen.

>[!NOTE]
>
>Die Vorlaufzeit kann lang sein, da die Umstellung auf HTTP/2 die Löschung des Cache erfordert. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden?   {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aus diesem Grund führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus unserer Quelle abgerufen werden.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde?   {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

Für Firefox und Chrome gibt es eine Erweiterung namens „HTTP/2 and SPDY Indicator“. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und die Beschriftung „X-Firefox-Spdy“ : „h2“ angezeigt. 
