---
title: Entwickeln von Mobilanwendungen in AEM
seo-title: Entwickeln von Mobilanwendungen in AEM
description: Auf dieser Seite erfahren Sie, wie Sie mit der Entwicklung von Mobile Apps in AEM mit Adobe PhoneGap Enterprise beginnen.
seo-description: Auf dieser Seite erfahren Sie, wie Sie mit der Entwicklung von Mobile Apps in AEM mit Adobe PhoneGap Enterprise beginnen.
uuid: d8442447-ee04-4bb2-a0d7-17dcc8979dba
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fd7bcf17-af7e-4bd6-8137-48401d9743c5
exl-id: cf8ba05c-6dcd-4880-b8bf-72382118cd80
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 12%

---

# Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM nutzt Adobe PhoneGap und Adobe Publishing Solutions, damit Sie inhaltsreiche und anwendungsbasierte, plattformübergreifende Mobilanwendungen erstellen können:

* Verwalten Sie alle mobilen Apps Ihrer Unternehmen an einem Ort.
* Überprüfen Sie Apps in Entwicklungs- und Staging-Umgebungen, ohne die Komplexität von Bereitstellungsprofilen und den zusätzlichen Aufwand zum Erstellen und Hochladen Ihrer App zur Freigabe zu haben.
* Verwenden Sie die AEM Authoring-Umgebung, um Rich-Content für Ihre Apps zu erstellen und zu verwalten.
* Verwenden Sie HTML5 mit Adobe PhoneGap, um umfangreiche Erlebnisse mit gerätespezifischen Funktionen zu erstellen.
* Stellen Sie HTML5-Webansichten neuen oder bereits vorhandenen **nativen** Anwendungen über Cordova WebViews vor.
* Erstellen, kuratieren und teilen Sie Rich-Multimedia-Inhalte über alle Versandkanäle, einschließlich Web, Mobile-Web, Mobile-App und Druck.

AEM Integration in die Adobe **[PhoneGap Build service](https://build.phonegap.com/)** zur Vereinfachung des Anwendungs-Build- und Bereitstellungsprozesses.

**Mit Adobe** ContentSyncies können Benutzer mühelos Seiten- und Inhaltsaktualisierungen über Over-the-Air (OTA) auf ihre Geräte herunterladen, ohne die Anwendung neu installieren oder aus dem AppStore, Google Play oder anderen App-Quellen herunterladen zu müssen.

**Adobe** Analytics ist vollständig in AEM-Apps integriert und ermöglicht das detaillierte Tracking von Verteilung, Geolocation, Betriebssystemen, Geräten, Clickstreams, iBeacon-Tracking und mehr.

## Erstellen von Apps {#creating-apps}

Entwickler können das [AEM PhoneGap Starter Kit](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) zusammen mit zusätzlichen Ressourcen in [https://github.com/adobe-marketing-cloud-apps](https://github.com/adobe-marketing-cloud-apps) verwenden, um AEM Apps mit PhoneGap zu bootstrapping durchzuführen, einschließlich einer nativen Referenzanwendung, in der Cordova Webviews ausgeführt werden.

Die Readme für das Starter Kit-Git-Repository enthält ein Tutorial zur Verwendung des Starter-Kits:

* Anpassen des Brandings
* Maven-Beispiel-Build- und -Bereitstellungsziele
* Repository-Konfiguration der Quellcodeverwaltung
* Installieren und Bereitstellen in lokalen oder Remote-AEM-Instanzen
* Deinstallieren von AEM

>[!NOTE]
>
>Zusätzliche Referenz-Implementierungsquelle, einschließlich Labs, finden Sie auf GitHub [hier](https://github.com/adobe-marketing-cloud-apps) und der Quelle &quot;Küche-Spülbecken&quot; [hier](https://github.com/blefebvre/aem-phonegap-kitchen-sink).

## Entwickeln für IOS 9- und HTTP-Hosts {#developing-for-ios-and-http-hosts}

IOS-Entwickler sollten sich eines offenen Problems mit Cordova-Apps bewusst sein, die unter iOS 9 ausgeführt werden. Dieses Problem verhindert, dass Anfragen an unsichere Hosts gesendet werden (z. B. *http://localhost:4502*). Dieses Problem wird mit einer kommenden Version von Cordova-iOS behoben (von der Cordova CLI verwendet), aber in der Zwischenzeit gibt es zwei Problemumgehungen:

1. Als sofortige Problemumgehung können Sie weiterhin jeden beliebigen iOS 8-Simulator problemlos verwenden.
1. Wenn Sie iOS 9 verwenden müssen, können Sie die Datei &quot;apps -Info.plist&quot;(gefunden nach Ausführung von `cordova platform add ios` in &quot;&lt;App-Stammordner>/platforms/ios/&lt;App-Name>/&lt;App-Name>-Info.plist&quot;) manuell bearbeiten, um die folgende Eigenschaft einzuschließen:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Weitere Informationen zu &quot;App Transport Security&quot;finden Sie im folgenden Abschnitt von [Apple&#39;s iOS9-Vorabversionsdocs](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) und in dieser [Diskussion zum Stack-Überlauf](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

## Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem-1}

* [Starten AEM PhoneGap](/help/mobile/starting-aem-phonegap-app.md)
* [Erstellen von Mobilanwendungen](/help/mobile/building-app-mobile-phonegap.md)
* [App strukturieren](/help/mobile/phonegap-structure-an-app.md)
* [Erstellen und Bearbeiten von Apps mithilfe der Apps-Konsole](/help/mobile/phonegap-apps-console.md)
* [Single Page Applications](/help/mobile/phonegap-single-page-applications.md)
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
