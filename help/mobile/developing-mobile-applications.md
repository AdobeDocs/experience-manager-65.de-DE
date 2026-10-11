---
title: Entwickeln von Mobile Apps in AEM
description: Auf dieser Seite können Sie mit der Entwicklung von Mobile Apps in AEM mithilfe von Adobe PhoneGap Enterprise beginnen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: cf8ba05c-6dcd-4880-b8bf-72382118cd80
solution: Experience Manager
feature: Mobile
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 1%
---
# Entwickeln von Mobile Apps in AEM {#developing-mobile-applications-in-aem}

{{ue-over-mobile}}

AEM verwendet Adobe PhoneGap- und Adobe-Publishing-Lösungen, mit denen Sie plattformübergreifende Mobile Apps mit umfangreichen Inhalten und Dienstprogrammen erstellen und verwalten können:

* Verwalten Sie alle mobilen Apps Ihres Unternehmens an einem Ort.
* Überprüfen Sie Apps in Entwicklungs- und Staging-Umgebungen, ohne die Komplexität der Bereitstellung von Profilen und den zusätzlichen Aufwand beim Erstellen und Hochladen Ihrer App zur Freigabe zu bewältigen.
* Verwenden Sie die Authoring-Umgebung von AEM, um Rich-Content für Ihre Apps zu erstellen und zu verwalten.
* Verwenden Sie HTML5 mit Adobe PhoneGap, um umfangreiche Erlebnisse mit gerätenativen Funktionen zu erstellen.
* Einführung von HTML5-Webansichten in neue oder bereits vorhandene **native**-Anwendungen über Cordova WebViews.
* Erstellen, kuratieren und teilen Sie Rich-Media-Inhalte über alle Bereitstellungskanäle hinweg, einschließlich Web, Mobile-Web, Mobile-App und Druck.

AEM kann mit dem Adobe PhoneGap Build Service (`https://build.phonegap.com/`) integriert werden, um die Erstellung und Bereitstellung von Anwendungen zu vereinfachen.

**Adobe ContentSync** ermöglicht es Benutzenden, Seiten- und Inhaltsaktualisierungen ganz einfach über das Internet (OTA) auf ihre Geräte herunterzuladen, ohne die Anwendung neu installieren oder aus dem AppStore, Google Play oder anderen App-Quellen herunterladen zu müssen.

**Adobe Analytics** ist vollständig in AEM-Apps integriert und ermöglicht eine detaillierte Verfolgung von Verteilung, Geolokalisierung, Betriebssystemen, Geräten, Clickstreams, iBeacon-Tracking und mehr.

## Erstellen von Apps {#creating-apps}

Entwicklerinnen und Entwickler können das [AEM PhoneGap-Starter](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit)Kit zusammen mit zusätzlichen Ressourcen in [https://github.com/adobe-marketing-cloud-apps](https://github.com/adobe-marketing-cloud-apps) verwenden, um AEM-Apps mit PhoneGap per Bootstrapping zu aktivieren, einschließlich einer nativen Referenz-App, in der Cordova Webviews ausgeführt wird.

Die Readme-Datei für das Git-Repository des Starter Kits enthält ein Tutorial für die Verwendung des Starter Kits:

* Anpassen des Brandings
* Maven-Beispiel-Build- und Bereitstellungsziele
* Repository-Konfiguration für Source-Steuerung
* Installieren und Bereitstellen in lokalen oder Remote-AEM-Instanzen
* Deinstallieren von AEM

>[!NOTE]
>
>Weitere Referenzimplementierungsquellen, einschließlich Labs, finden Sie auf GitHub [hier](https://github.com/adobe-marketing-cloud-apps) und in der „Kitchen-Sink“-Quelle [hier](https://github.com/blefebvre/aem-phonegap-kitchen-sink).

## Entwickeln für IOS 9- und HTTP-Hosts {#developing-for-ios-and-http-hosts}

IOS-Entwickler sollten sich über ein offenes Problem mit Cordova-Apps, die auf iOS 9 ausgeführt werden, im Klaren sein. Dieses Problem verhindert, dass Anfragen an unsichere Hosts (z. B. *http://localhost:4502*) gesendet werden. Dieses Problem wird mit einer kommenden Version von cordova-ios (die von der Cordova CLI genutzt wird) behoben, aber in der Zwischenzeit gibt es zwei Problemumgehungen:

1. Als sofortige Problemumgehung können Sie weiterhin jeden der iOS 8-Simulatoren ohne Problem verwenden.
1. Wenn Sie iOS 9 verwenden müssen, können Sie Ihre Datei apps -info.plist (nach der Ausführung von `cordova platform add ios` in &quot;&lt;app root>/platform/ios/&lt;app name>/&lt;app name>-info.plist„) manuell bearbeiten, um die folgende Eigenschaft einzuschließen:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Weitere Informationen zu „App Transport Security“ finden Sie im folgenden Abschnitt der Vorabversionsdokumente für iOS9 von [Apple &#x200B;](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) dieser [Stack Overflow-Diskussion](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

## Entwickeln von Mobile Apps in AEM {#developing-mobile-applications-in-aem-1}

* [Starten von AEM PhoneGap](/help/mobile/starting-aem-phonegap-app.md)
* [Erstellen von Mobile Apps](/help/mobile/building-app-mobile-phonegap.md)
* [Strukturieren einer App](/help/mobile/phonegap-structure-an-app.md)
* [Erstellen und Bearbeiten von Apps mit der Apps-Konsole](/help/mobile/phonegap-apps-console.md)
* [Single Page Applications (SPA)](/help/mobile/phonegap-single-page-applications.md)
* [Entwickeln von Apps mit PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md)
* [Zugriff auf Gerätefunktionen](/help/mobile/phonegap-access-device-features.md)
* [App-Leistung mit Adobe Mobile Analytics verfolgen](/help/mobile/phonegap-intro-to-app-analytics.md)
* [Adobe Analytics zu Ihrer Mobile App hinzufügen](/help/mobile/phonegap-add-analytics-to-apps.md)
* [Push-Benachrichtigungen](/help/mobile/phonegap-push-notifications.md)
* [AEM Mobile-Inhaltspersonalisierung](/help/mobile/phonegap-aem-mobile-content-personalization.md)
* [Die Anatomie einer App](/help/mobile/phonegap-apps-arch.md)
* [Ist Ihre Hybrid-App bereit für AEM Mobile?](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Zuständigkeiten eines Administrators bzw. einer Administratorin und eines Entwicklers finden Sie in den folgenden Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
