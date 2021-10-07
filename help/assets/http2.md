---
title: Bereitstellung von Inhalten per HTTP/2
description: HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
role: User, Admin
exl-id: 9eb9f309-33e5-4694-84d2-fb2cd3de50a6
feature: Publishing,Configuration
source-git-commit: 65af6e33ae3897519491952f4d3a6832700f77b2
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 58%

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

Die Leistungsverbesserung kann stark variieren. Er basiert auf vielen Faktoren, wie dem Code Ihrer Website, der Verwendung von Dynamic Media, dem Gerät, dem Bildschirm und dem Standort des Verbrauchers.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen? {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Sie verwenden das von Adobe gebündelte CDN (Content Delivery Network) als Teil Ihrer Dynamic Media-Lizenz.
* Sie verwenden eine dedizierte (non- company-h.assetsadobe#.com) Domäne.

   Wenn Sie bereits über eine dedizierte Domäne verfügen, können Sie sich über den Adobe-Support anmelden.

   Wenn Sie nicht über eine dedizierte Domäne verfügen, plant Adobe, den Übergang zu HTTP/2 für 2018 zu planen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Sie initiieren die Anfrage zum Umschalten auf HTTP/2. wird nicht automatisch für Sie durchgeführt.

1. Um zu HTTP/2 zu wechseln, starten Sie eine Anfrage an den Adobe-Support. Siehe [Zugriff auf das Adobe Experience Manager Support-Portal](https://helpx.adobe.com/de/experience-manager/kb/accessing-aem-support-portal.html).

   1. In der Anfrage geben Sie folgende Informationen an:

      1. Name des Hauptansprechpartners, E-Mail, Telefon.
      1. Alle Domänen, die auf HTTP/2 umgestellt werden sollen.
      1. Stellen Sie sicher, dass Sie sichere HTTPS für Rich-Media-Anforderungen verwenden.
      1. Vergewissern Sie sich, dass Sie das CDN über Adobe verwenden und nicht mit einer direkten Beziehung verwaltet werden.
      1. Stellen Sie sicher, dass Sie eine dedizierte Domäne verwenden. Wenn Sie Dynamic Media verwenden, verwenden Sie eine dedizierte Domäne.
   1. Der Support fügt Sie zur HTTP/2-Kundenwarteschlange hinzu, die auf der Reihenfolge basiert, in der die Anfragen gesendet wurden.
   1. Wenn Adobe zur Bearbeitung Ihrer Anfrage bereit ist, kontaktiert der Support Sie, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
   1. Sie werden nach Abschluss benachrichtigt und können den erfolgreichen Übergang zu HTTP2 überprüfen.

      Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

      Für Firefox und Chrome gibt es eine Erweiterung namens &quot;HTTP/2 and SPDY Indicator&quot;. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn http/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und der Kopfzeile &quot;X-Firefox-Spdy&quot;angezeigt: &quot;h2&quot;.


## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim Support eingehen.

>[!NOTE]
>
>Es kann eine lange Vorlaufzeit geben, da beim Übergang zu HTTP/2 der Cache geleert werden muss. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden? {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aus diesem Grund führt Adobe nur wenige Umstellungen gleichzeitig durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus der Quelle abgerufen werden.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

Für Firefox und Chrome gibt es eine Erweiterung namens &quot;HTTP/2 and SPDY Indicator&quot;. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn http/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und einer Kopfzeile `X-Firefox-Spdy` angezeigt: `h2`.
