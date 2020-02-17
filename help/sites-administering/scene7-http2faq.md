---
title: Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)
seo-title: Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)
description: Erfahren Sie mehr über die Bereitstellung von Inhalten per HTTP/2.
seo-description: Erfahren Sie mehr über die Bereitstellung von Inhalten per HTTP/2.
uuid: e837c3e0-6e48-46f1-b510-847c9976807a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: afbe9f80-c2a3-4a46-b9d6-4c9406667d7f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ){#http-delivery-of-content-faq}

Adobe freut sich, die Möglichkeit zur Bereitstellung von Inhalten per HTTP/2 bekanntgeben zu können. Sie werden insgesamt eine Leistungssteigerung feststellen, wenn Sie HTTP/2 verwenden.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und seine Vorteile kurz und einfach beschrieben:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Verbesserung der Leistung ist von verschiedenen Faktoren abhängig, z. B. dem Code Ihrer Website oder wie Sie Scene7 und Geräte, Bildschirme und Standorte von Verbrauchern nutzen.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen? {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Verwenden Sie das Adobe-gebündelte CDN (Content Delivery Network) als Teil Ihrer Dynamic Media Classic-Lizenz.
* Verwenden Sie eine dedizierte Domäne (d. h. `images.company.com` oder `mycompany.scene7.com`), keine allgemeine Dynamic Media Classic-Domäne (d. h. `s7d1.scene7.com`, `s7d2.scene7.com`oder `s7d13.scene7.com`).

   Ihre Domänen finden Sie, indem Sie sich für jedes Unternehmenskonto [bei Ihrer Instanz des Scene7 Publishing-Systems anmelden](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html).

    Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.  Suchen Sie nach dem Feld **Veröffentlichungsservername**.  Wenn Sie derzeit eine generische Scene7-Domäne verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domäne beantragen. 

## What is the process for enabling HTTP/2 for my Dynamic Media Classic account? {#what-is-the-process-for-enabling-http-for-my-scene-account}

You must initiate an Adobe Technical Support (`s7support@adobe.com`) request to switch over to HTTP/2; it is not automatically done for you.

1. In der Anfrage geben Sie folgende Informationen an:

   * Name, E-Mail-Adresse und Telefonnummer des Primärkontakts
   * Alle Domänen, die auf HTTP/2 umgestellt werden sollen. Das ist `images.company.com` oder `mycompany.scene7.com`.
   Ihre Domänen finden Sie, indem Sie sich für jedes Unternehmenskonto [bei Ihrer Instanz des Scene7 Publishing-Systems anmelden](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html).

    Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.  Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  

   * Vergewissern Sie sich, dass Sie sicheres HTTPS für Rich Media-Anforderungen verwenden.
   * Stellen Sie sicher, dass Sie das CDN über Adobe und nicht über eine direkte Beziehung verwenden.
   * Stellen Sie sicher, dass Sie eine dedizierte Domäne verwenden. Das ist `images.company.com` oder `mycompany.scene7.com`nicht eine allgemeine Scene7-Domäne wie `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.
   Ihre Domänen finden Sie, indem Sie sich für jedes Unternehmenskonto [bei Ihrer Instanz des Scene7 Publishing-Systems anmelden](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html).

    Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.  Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungsservername]**.  Wenn Sie derzeit eine generische Scene7-Domäne verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domäne beantragen. 

   1. Der technische Support fügt Sie basierend auf der Reihenfolge, in der Anfragen gesendet wurden, zur Kundenwarteschlange für HTTP/2 hinzu.
   1. Wenn Adobe für die Bearbeitung Ihrer Anfrage bereit ist, setzt sich der Support mit Ihnen in Verbindung, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
   1. Nach Abschluss werden Sie benachrichtigt, wonach Sie prüfen können, ob die Umstellung auf HTTP/2 erfolgreich durchgeführt wurde.



## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge bearbeitet, in der sie beim technischen Support eingehen.

>[!NOTE]
>
>Die Vorlaufzeit kann lang sein, da die Umstellung auf HTTP/2 die Löschung des Cache erfordert. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden? {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aus diesem Grund führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus unserer Quelle abgerufen werden.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Sie müssen eine Erweiterung für die Verwendung Ihres Webbrowsers herunterladen. For Firefox and Chrome there is an extension called **[!UICONTROL HTTP/2 and SPDY Indicator]**. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit HTTPS aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und einer Kopfzeile &quot;X-Firefox-Spdy&quot; angezeigt: &quot;h2&quot;.
