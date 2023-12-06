---
title: Bereitstellung von Inhalten per HTTP/2
description: Erfahren Sie, wie HTTP/2 die Kommunikation zwischen Browsern und Servern verbessert, wodurch eine schnellere Übertragung von Informationen ermöglicht und gleichzeitig die benötigte Verarbeitungsleistung reduziert wird.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
exl-id: 9eb9f309-33e5-4694-84d2-fb2cd3de50a6
feature: Publishing,Configuration
source-git-commit: 04050f31742c926b45235595f6318929d3767bd8
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 92%

---

# Bereitstellung von Inhalten per HTTP/2 {#http-delivery-of-content}

Adobe freut sich, die Bereitstellung von Inhalt über HTTP/2 zu präsentieren, die eine Verbesserung der Leistung mit sich bringt.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und seine Vorteile kurz und einfach beschrieben:

[Was Sie über HTTP/2 wissen müssen](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html)

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Leistungsverbesserung kann stark variieren. Sie basiert auf vielen Faktoren, wie dem Code Ihrer Website, der Verwendung von Dynamic Media, dem Gerät, dem Bildschirm und dem Standort des Verbrauchers.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen? {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Verwenden Sie das Adobe-gebündelte CDN (Content Delivery Network) als Teil Ihrer Dynamic Media-Lizenz.
* Sie verwenden eine dedizierte (non- company-h.assetsadobe#.com) Domain.

  Wenn Sie bereits über eine dedizierte Domain verfügen, können Sie sich über den Kunden-Support von Adobe anmelden.

  Wenn Sie nicht über eine dedizierte Domain verfügen, wird Adobe Ihre Umstellung auf HTTP/2 für 2018 einplanen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Sie müssen den Wechsel auf HTTP/2 beantragen, da er nicht automatisch erfolgt.

1. Um zu HTTP/2 zu wechseln, starten Sie eine Anfrage an den Kunden-Support von Adobe. Siehe [Öffnen eines Support-Tickets](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de&amp;support-tab=home#support).

   1. In der Anfrage geben Sie folgende Informationen an:

      1. Name des Hauptansprechpartners, E-Mail, Telefon.
      1. Alle Domains, die auf HTTP/2 umgestellt werden sollen.
      1. Vergewissern Sie sich, dass Sie sicheres HTTPS für Rich-Media-Anforderungen verwenden.
      1. Stellen Sie sicher, dass Sie das CDN über Adobe und nicht über eine direkte Beziehung verwenden.
      1. Stellen Sie sicher, dass Sie eine dedizierte Domain verwenden. Wenn Sie Dynamic Media verwenden, verfügen Sie bereits über eine dedizierte Domain.

   1. Der Kunden-Support fügt Sie entsprechend der Reihenfolge der eingegangenen Anfragen der HTTP/2-Kundenwarteschlange hinzu.
   1. Wenn Adobe für die Bearbeitung Ihrer Anfrage bereit ist, setzt sich der Support mit Ihnen in Verbindung, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
   1. Nach Abschluss werden Sie benachrichtigt, wonach Sie prüfen können, ob die Umstellung auf HTTP/2 erfolgreich durchgeführt wurde.

      Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

      Für Firefox und Chrome gibt es eine Erweiterung namens „HTTP/2 and SPDY Indicator“. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und die Kopfzeile „X-Firefox-Spdy“ : „h2“ angezeigt.

## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim Kunden-Support eingehen.

>[!NOTE]
>
>Die Vorlaufzeit kann lang sein, da die Umstellung auf HTTP/2 die Löschung des Cache erfordert. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden? {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aus diesem Grund führt Adobe nur wenige Umstellungen gleichzeitig durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus der Quelle abgerufen werden.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

Für Firefox und Chrome gibt es eine Erweiterung namens „HTTP/2 and SPDY Indicator“. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und die Kopfzeile `X-Firefox-Spdy` : `h2` angezeigt.
