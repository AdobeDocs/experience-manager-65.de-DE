---
title: 'Bereitstellung von Inhalt über HTTP/2 '
description: HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
role: Business Practitioner, Administrator
exl-id: 9eb9f309-33e5-4694-84d2-fb2cd3de50a6
feature: Veröffentlichen, Konfiguration
translation-type: tm+mt
source-git-commit: c9aec973faf4caef741961d92a6f258646aeddb7
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 52%

---

# HTTP/2 Versand des Inhalts {#http-delivery-of-content}

Adobe freut sich, die Bereitstellung von Inhalt über HTTP/2 zu präsentieren, die eine Verbesserung der Leistung mit sich bringt.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene Out-of-the-Box-CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und seine Vorteile kurz und einfach beschrieben:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Leistungsverbesserung kann sehr unterschiedlich sein. Er basiert auf vielen Faktoren, wie dem Code Ihrer Website, der Verwendung von Dynamic Media, dem Gerät, dem Bildschirm und dem Standort des Verbrauchers.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen?  {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Sie verwenden das von Adobe gebündelte CDN (Content Delivery Network) als Teil Ihrer Dynamic Media-Lizenz.
* Sie verwenden eine dedizierte (non- company-h.assetsadobe#.com) Domäne.

   Wenn Sie bereits über eine dedizierte Domäne verfügen, können Sie über den technischen Support Opt-in.

   Wenn Sie keine dedizierte Domäne haben, plant Adobe, Ihre Transition auf HTTP/2 im Jahr 2018 zu planen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Sie initiieren die Anforderung, zu HTTP/2 zu wechseln. es wird nicht automatisch für Sie durchgeführt.

1. Um zu HTTP/2 zu wechseln, starten Sie eine Anfrage an den Kundendienst der Adobe. Siehe [Zugriff auf das AEM-Supportportal](https://helpx.adobe.com/de/experience-manager/kb/accessing-aem-support-portal.html).

   1. In der Anfrage geben Sie folgende Informationen an:

      1. Name des Hauptansprechpartners, E-Mail, Telefon.
      1. Alle Domänen, die auf HTTP/2 übertragen werden sollen.
      1. Überprüfen Sie, ob Sie sichere HTTPS für Rich-Media-Anfragen verwenden.
      1. Vergewissern Sie sich, dass Sie das CDN über Adobe verwenden und nicht mit einer direkten Beziehung verwaltet werden.
      1. Überprüfen Sie, ob Sie eine dedizierte Domäne verwenden. Wenn Sie Dynamic Media verwenden, verwenden Sie eine dedizierte Domäne.
   1. Der Kundendienst fügt Sie je nach der Reihenfolge, in der Anfragen gesendet wurden, zur HTTP/2-Kundenwarteschlange hinzu.
   1. Wenn die Adobe bereit ist, Ihre Anfrage zu bearbeiten, kontaktiert der Kundendienst Sie, um die Transition zu koordinieren und ein Datum für die Zielgruppe festzulegen.
   1. Sie werden nach Abschluss benachrichtigt und können die erfolgreiche Transition auf HTTP2 überprüfen.

      Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

      Für Firefox und Chrome gibt es die Erweiterung &quot;HTTP/2 und SPDY Indicator&quot;. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn http/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flashs und einer Kopfzeile &quot;X-Firefox-Spdy&quot; angezeigt: &quot;h2&quot;.


## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim Kundendienst eingehen.

>[!NOTE]
>
>Es kann eine lange Vorlaufzeit geben, da bei der Transition zu HTTP/2 der Cache gelöscht werden muss. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden?   {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Daher plant Adobe, mehrere Kundenanforderungen gleichzeitig zu bearbeiten, damit beim Abrufen von Anforderungen aus der Herkunft eine annehmbare Transition erhalten bleibt.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde?   {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Da der Browser nicht auf diese Tatsache hinweist, muss eine Erweiterung heruntergeladen werden.

Für Firefox und Chrome gibt es die Erweiterung &quot;HTTP/2 und SPDY Indicator&quot;. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit https aufgerufen werden. Wenn http/2 unterstützt wird, wird es durch die Erweiterung in Form eines blauen Flashs und einer Überschrift `X-Firefox-Spdy` angezeigt: `h2`.
