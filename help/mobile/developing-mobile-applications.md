---
title: Entwickeln von Mobilanwendungen in AEM
seo-title: Entwickeln von Mobilanwendungen in AEM
description: Folgen Sie dieser Seite, um mit der Entwicklung von Mobilanwendungen in AEM mit Adobe PhoneGap Enterprise zu beginnen.
seo-description: Folgen Sie dieser Seite, um mit der Entwicklung von Mobilanwendungen in AEM mit Adobe PhoneGap Enterprise zu beginnen.
uuid: d8442447-ee04-4bb2-a0d7-17dcc8979dba
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fd7bcf17-af7e-4bd6-8137-48401d9743c5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM nutzt Adobe PhoneGap und Adobe Publishing Solutions, damit Sie inhaltsreiche und anwendungsbasierte, plattformübergreifende Mobilanwendungen erstellen können:

* Verwalten Sie alle mobilen Apps Ihrer Unternehmen an einem Ort.
* Überprüfen Sie Apps in Entwicklungs- und Staging-Umgebungen, ohne dass Bereitstellungsprofile kompliziert sind und zusätzliche Anstrengungen erforderlich sind, um Ihre App für die Freigabe zu erstellen und hochzuladen.
* Verwenden Sie die AEM-Authoring-Umgebung, um Rich Content für Ihre Apps zu erstellen und zu verwalten.
* Verwenden Sie HTML5 mit Adobe PhoneGap, um umfangreiche Erlebnisse mit geräteeigenen Funktionen zu erstellen.
* Einführung von HTML5-Webansichten in neue oder bereits vorhandene **native** Anwendungen über Cordova WebViews.
* Erstellen, kuratieren und teilen Sie Rich-Media-Inhalte über alle Kanäle, einschließlich Web, Mobile-Web, Mobile-App und Druck.

AEM kann mit dem Adobe **[PhoneGap Build-Dienst](https://build.phonegap.com/)**integriert werden, um die Erstellung und Bereitstellung von Anwendungen zu vereinfachen.

**Mit Adobe ContentSync** können Benutzer mühelos Seiten- und Inhaltsupdates Over-the-Air (OTA) auf ihre Geräte herunterladen, ohne die Anwendung neu installieren oder aus dem AppStore, Google Play oder anderen App-Quellen herunterladen zu müssen.

**Adobe Analytics** ist vollständig in AEM-Apps integriert und ermöglicht eine detaillierte Verfolgung von Distribution, Geolocation, Betriebssystemen, Geräten, Clickstreams, iBeacon-Verfolgung und mehr.

## Erstellen von Apps {#creating-apps}

Entwickler können das [AEM PhoneGap Starter Kit](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) zusammen mit zusätzlichen Ressourcen in [https://github.com/adobe-marketing-cloud-apps](https://github.com/adobe-marketing-cloud-apps) verwenden, um AEM-Apps mit PhoneGap zu bootstrapping zu machen, einschließlich einer Referenz-nativen App, in der Cordova Webviews ausgeführt wird.

Die Readme für das Starter Kit Git-Repository enthält ein Lernprogramm zur Verwendung des Starter-Kits:

* Anpassen des Brandings
* Mustererstellungs- und Bereitstellungsziele
* Repository-Konfiguration der Quellcodeverwaltung
* Installieren und Bereitstellen in lokalen oder Remote-AEM-Instanzen
* Deinstallieren von AEM

>[!NOTE]
>
>Zusätzliche Referenz-Implementierungsquelle, einschließlich Labs, finden Sie [hier](https://github.com/adobe-marketing-cloud-apps) auf GitHub und die Quelle &quot;Küche-Spülbecken&quot; [hier](https://github.com/blefebvre/aem-phonegap-kitchen-sink).

## Entwickeln für IOS 9- und HTTP-Hosts {#developing-for-ios-and-http-hosts}

IOS-Entwickler sollten sich eines offenen Problems mit Cordova-Apps, die unter iOS 9 ausgeführt werden, bewusst sein. Dieses Problem verhindert, dass Anforderungen an unsichere Hosts (z. B. *http://localhost:4502*) gesendet werden. Dieses Problem wird mit einer kommenden Version von Cordova-Ios (von der Cordova-Befehlszeilenschnittstelle verwendet) behoben, aber in der Zwischenzeit gibt es zwei Workarounds:

1. Als sofortige Problemumgehung können Sie weiterhin jeden beliebigen iOS 8-Simulator ohne Ausgabe verwenden.
1. Wenn Sie iOS 9 verwenden müssen, können Sie die Datei &quot;apps -Info.plist&quot;(die Sie nach der Ausführung `cordova platform add ios` in &quot;&lt;App-Stammordner>/platforms/ios//&lt;App-Name>/-Info.plist&quot;gefunden haben) manuell bearbeiten, um die folgende Eigenschaft einzuschließen:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Weitere Informationen zu &quot;App Transport Security&quot;finden Sie im folgenden Abschnitt der [Apple iOS9-Prerelease-Dokumente](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) und in dieser [Stack Overflow-Diskussion](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

## Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem-1}

* [Starten von AEM PhoneGap](/help/mobile/starting-aem-phonegap-app.md)
* [Erstellen von Mobilanwendungen](/help/mobile/building-app-mobile-phonegap.md)
* [App strukturieren](/help/mobile/phonegap-structure-an-app.md)
* [Erstellen und Bearbeiten von Apps mit der Apps-Konsole](/help/mobile/phonegap-apps-console.md)
* [Einzelseiten-Webanwendungen](/help/mobile/phonegap-single-page-applications.md)
* [Entwickeln von Apps mit der PhoneGap-CLI](/help/mobile/phonegap-apps-pg-cli.md)
* [Gerätefunktionen aufrufen](/help/mobile/phonegap-access-device-features.md)
* [Verfolgen der App-Leistung mit Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md)
* [Adobe Analytics zu Ihrer mobilen Anwendung hinzufügen](/help/mobile/phonegap-add-analytics-to-apps.md)
* [Push-Benachrichtigungen](/help/mobile/phonegap-push-notifications.md)
* [Personalisierung von AEM Mobile-Inhalten](/help/mobile/phonegap-aem-mobile-content-personalization.md)
* [Die Anatomie einer App](/help/mobile/phonegap-apps-arch.md)
* [Ist Ihre Hybrid-App für AEM Mobile bereit?](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten von Administratoren und Entwicklern finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
