---
title: Entwickeln von Mobilanwendungen in AEM
seo-title: Developing Mobile Applications in AEM
description: Auf dieser Seite erfahren Sie, wie Sie mit der Entwicklung von Mobile Apps in AEM mit Adobe PhoneGap Enterprise beginnen.
seo-description: Follow this page to start developing mobile application in AEM using Adobe PhoneGap Enterprise.
uuid: d8442447-ee04-4bb2-a0d7-17dcc8979dba
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fd7bcf17-af7e-4bd6-8137-48401d9743c5
exl-id: cf8ba05c-6dcd-4880-b8bf-72382118cd80
source-git-commit: 17d13e9b201629d9d1519fde4740cf651fe89d2c
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 4%

---

# Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM nutzt Adobe PhoneGap- und Adobe Publishing Solutions, mit denen Sie inhaltsreiche und anwendungsbasierte, plattformübergreifende mobile Apps erstellen und verwalten können:

* Verwalten Sie alle mobilen Apps Ihrer Unternehmen an einem Ort.
* Überprüfen Sie Apps in Entwicklungs- und Staging-Umgebungen, ohne die Komplexität von Bereitstellungsprofilen und den zusätzlichen Aufwand zum Erstellen und Hochladen Ihrer App zur Freigabe zu haben.
* Verwenden Sie die AEM Authoring-Umgebung, um Rich-Content für Ihre Apps zu erstellen und zu verwalten.
* Verwenden Sie HTML5 mit Adobe PhoneGap, um umfangreiche Erlebnisse mit geräteübergreifenden Funktionen zu erstellen.
* Einführung von HTML5-Webansichten in neue oder bereits vorhandene **nativ** Anwendungen über Cordova WebViews.
* Erstellen, kuratieren und teilen Sie Rich-Multimedia-Inhalte über alle Versandkanäle, einschließlich Web, Mobile-Web, Mobile-App und Druck.

AEM Integration mit dem Adobe PhoneGap Build-Dienst (`https://build.phonegap.com/`), um den Prozess zum Erstellen und Bereitstellen von Anwendungen zu vereinfachen.

**Adobe ContentSync** ermöglicht Benutzern das einfache Herunterladen von Seiten- und Inhaltsaktualisierungen Over-the-Air (OTA) auf ihre Geräte, ohne die Anwendung neu installieren oder aus dem AppStore, Google Play oder anderen App-Quellen herunterladen zu müssen.

**Adobe Analytics** ist vollständig in AEM Apps integriert und ermöglicht ein detailliertes Tracking von Verteilung, Geolocation, Betriebssystemen, Geräten, Clickstreams, iBeacon-Tracking und mehr.

## Erstellen von Apps {#creating-apps}

Entwickler können die [AEM PhoneGap Starter Kit](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) sowie zusätzlichen Ressourcen, die in [https://github.com/adobe-marketing-cloud-apps](https://github.com/adobe-marketing-cloud-apps) zum Bootstrapping von AEM Apps mit PhoneGap, einschließlich einer nativen Referenzanwendung, in der Cordova Webviews ausgeführt werden.

Die Readme für das Starter Kit-Git-Repository enthält ein Tutorial zur Verwendung des Starter-Kits:

* Anpassen des Brandings
* Maven-Beispiel-Build- und -Bereitstellungsziele
* Repository-Konfiguration der Quellcodeverwaltung
* Installieren und Bereitstellen in lokalen oder Remote-AEM-Instanzen
* Deinstallieren von AEM

>[!NOTE]
>
>Zusätzliche Referenz-Implementierungsquelle, einschließlich Labs, finden Sie auf GitHub [here](https://github.com/adobe-marketing-cloud-apps) und die Quelle &quot;Küchenbecken&quot; [here](https://github.com/blefebvre/aem-phonegap-kitchen-sink).

## Entwickeln für IOS 9- und HTTP-Hosts {#developing-for-ios-and-http-hosts}

iOS-Entwickler sollten sich eines offenen Problems mit Cordova-Apps bewusst sein, das auf iOS 9 ausgeführt wird. Dieses Problem verhindert, dass Anfragen an unsichere Hosts (wie *http://localhost:4502*). Dieses Problem wird mit einer kommenden Version von Cordova-iOS behoben (von der Cordova CLI verwendet), aber in der Zwischenzeit gibt es zwei Problemumgehungen:

1. Als sofortige Problemumgehung können Sie weiterhin jeden der iOS 8-Simulatoren problemlos verwenden.
1. Wenn Sie iOS 9 verwenden müssen, Ihre apps -Info.plist (gefunden nach der Ausführung) `cordova platform add ios` in &quot;&lt;app root=&quot;&quot;>/platforms/ios/&lt;app name=&quot;&quot;>/&lt;app name=&quot;&quot;>-Info.plist&quot;) manuell bearbeitet werden, um die folgende Eigenschaft einzuschließen:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Weitere Informationen zu &quot;App Transport Security&quot;finden Sie im folgenden Abschnitt von [Dokumente zu Apple iOS9-Vorabversionen](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) und dies [Diskussion über Stack Overflow](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

## Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem-1}

* [Starten AEM PhoneGap](/help/mobile/starting-aem-phonegap-app.md)
* [Erstellen von Mobile Apps](/help/mobile/building-app-mobile-phonegap.md)
* [App strukturieren](/help/mobile/phonegap-structure-an-app.md)
* [Erstellen und Bearbeiten von Apps mithilfe der Apps-Konsole](/help/mobile/phonegap-apps-console.md)
* [Single Page Applications (SPA)](/help/mobile/phonegap-single-page-applications.md)
* [Entwickeln von Apps mit PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md)
* [Auf Gerätefunktionen zugreifen](/help/mobile/phonegap-access-device-features.md)
* [App-Leistung mit Adobe Mobile Analytics verfolgen](/help/mobile/phonegap-intro-to-app-analytics.md)
* [Hinzufügen von Adobe Analytics zu einer Mobile App](/help/mobile/phonegap-add-analytics-to-apps.md)
* [Push-Benachrichtigungen](/help/mobile/phonegap-push-notifications.md)
* [Personalisierung von AEM Mobile-Inhalten](/help/mobile/phonegap-aem-mobile-content-personalization.md)
* [Die Anatomie einer App](/help/mobile/phonegap-apps-arch.md)
* [Ist Ihre Hybrid-App für AEM Mobile bereit?](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten von Administratoren und Entwicklern finden Sie in den folgenden Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
