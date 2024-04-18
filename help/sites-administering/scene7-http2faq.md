---
title: Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)
description: Erfahren Sie mehr über die Bereitstellung von HTTP2-Inhalten und darüber, wie sie die Gesamtleistung Ihrer Web-Inhalte steigern können.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 2428914c-5fb0-439e-a1ef-8ee30b890f58
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 100%

---

# Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ){#http-delivery-of-content-faq}

Adobe freut sich, die Möglichkeit zur Bereitstellung von Inhalten per HTTP/2 bekanntgeben zu können. Wenn Sie HTTP/2 verwenden, wird die Gesamtleistung gesteigert.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und seine Vorteile kurz und einfach beschrieben:

[Was Sie über HTTP/2 wissen müssen](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html).

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Verbesserung der Leistung ist von verschiedenen Faktoren abhängig, z. B. dem Code Ihrer Website oder wie Sie Dynamic Media und Geräte, Bildschirme und Standorte von Kunden nutzen.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen? {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Sie verwenden das von Adobe gebündelte CDN (Content Delivery Network) als Teil Ihrer Dynamic Media-Lizenz.
* Verwenden Sie eine dedizierte Domain (d. h. `images.company.com` oder `mycompany.scene7.com`), keine generische Dynamic Media-Domain (d. h. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

  Öffnen Sie die [Dynamic Media Classic-Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Unternehmenskonto an, um Ihre Domains zu finden. Wechseln Sie dann zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **Veröffentlichungs-Server-Name**. Wenn Sie derzeit eine generische Dynamic Media-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-scene-account}

1. Erstellen Sie [über die Admin Console einen Support-Fall](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) und fordern Sie die Umstellung auf HTTP/2 an. Dies wird nicht automatisch für Sie erledigt.
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   * Name, E-Mail-Adresse und Telefonnummer des Primärkontakts
   * Alle Domains, die auf HTTP/2 umgestellt werden sollen. Das heißt, `images.company.com` oder `mycompany.scene7.com`.

     Öffnen Sie die [Dynamic Media Classic-Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Unternehmenskonto an, um Ihre Domains zu finden. Wechseln Sie dann zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**.

   * Vergewissern Sie sich, dass Sie sicheres HTTPS für Rich Media-Anforderungen verwenden.
   * Stellen Sie sicher, dass Sie das CDN über Adobe und nicht über eine direkte Beziehung verwenden.
   * Stellen Sie sicher, dass Sie eine dedizierte Domain verwenden. Das heißt, `images.company.com` oder `mycompany.scene7.com`, nicht eine generische Dynamic Media-Domain wie `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

     Öffnen Sie die [Dynamic Media Classic-Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Unternehmenskonto an, um Ihre Domains zu finden. Wechseln Sie dann zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**. Wenn Sie derzeit eine generische Dynamic Media-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.

1. Der Adobe-Support fügt Sie entsprechend der Reihenfolge der eingegangenen Anfragen der HTTP/2-Kundenwarteschlange hinzu.
1. Wenn Adobe für die Bearbeitung Ihrer Anfrage bereit ist, setzt sich der Support mit Ihnen in Verbindung, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
1. Nach Abschluss werden Sie benachrichtigt, wonach Sie prüfen können, ob die Umstellung auf HTTP/2 erfolgreich durchgeführt wurde.

## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim Adobe-Support eingehen.

>[!NOTE]
>
>Die Vorlaufzeit ist lang, da die Umstellung auf HTTP/2 die Löschung des Cache erfordert. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden? {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aufgrund dieser Aktion führt Adobe nur wenige Umstellungen zugleich durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus der Adobe-Quelle abgerufen werden.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Laden Sie eine Erweiterung herunter, die Sie mit Ihrem Webbrowser verwenden können. Für Firefox und Chrome gibt es eine Erweiterung namens **[!UICONTROL HTTP/2 and SPDY Indicator]**. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit HTTPS aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und die Beschriftung „X-Firefox-Spdy“ : „h2“ angezeigt.
