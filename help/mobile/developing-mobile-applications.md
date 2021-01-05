---
title: Entwickeln von Mobilanwendungen in AEM
seo-title: Entwickeln von Mobilanwendungen in AEM
description: Folgen Sie dieser Seite, um Beginn bei der Entwicklung von Mobilanwendungen in AEM Adobe PhoneGap Enterprise zu erhalten.
seo-description: Folgen Sie dieser Seite, um Beginn bei der Entwicklung von Mobilanwendungen in AEM Adobe PhoneGap Enterprise zu erhalten.
uuid: d8442447-ee04-4bb2-a0d7-17dcc8979dba
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fd7bcf17-af7e-4bd6-8137-48401d9743c5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 12%

---


# Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

AEM nutzt Adobe PhoneGap und Adobe Publishing Solutions, damit Sie inhaltsreiche und anwendungsbasierte, plattformübergreifende Mobilanwendungen erstellen können:

* Verwalten Sie alle mobilen Apps Ihrer Firmen an einem Ort.
* Überprüfen Sie Apps in Entwicklungs- und Staging-Umgebung, ohne dass Bereitstellungs-Profil kompliziert sind und zusätzliche Anstrengungen erforderlich sind, um Ihre App für die Freigabe zu erstellen und hochzuladen.
* Verwenden Sie die AEM Authoring-Umgebung, um Rich-Content für Ihre Apps zu erstellen und zu verwalten.
* Verwenden Sie HTML5 mit Adobe PhoneGap, um umfangreiche Erlebnisse mit geräteeigenen Funktionen zu erstellen.
* Stellen Sie HTML5-Webansichten neuen oder bereits vorhandenen **nativen**-Anwendungen über Cordova WebViews vor.
* Rich-Media-Inhalte erstellen, kuratieren und für alle Versand-Kanal freigeben, einschließlich Web, Mobile-Web, Mobile-App und Print.

AEM wird in die Adobe **[PhoneGap Build service](https://build.phonegap.com/)** integriert, um die Erstellung und Bereitstellung der Anwendung zu vereinfachen.

**Mit Adobe** ContentSyncis können Benutzer mühelos Seiten- und Inhaltsupdates Over-the-Air (OTA) auf ihre Geräte herunterladen, ohne die Anwendung neu installieren oder aus dem AppStore, Google Play oder anderen App-Quellen herunterladen zu müssen.

**Adobe** Analytics ist vollständig in AEM-Apps integriert und ermöglicht eine detaillierte Verfolgung von Distribution, Geolocation, Betriebssystemen, Geräten, Clickstreams, iBeacon-Verfolgung und mehr.

## Erstellen von Apps {#creating-apps}

Entwickler können das [AEM PhoneGap Starter Kit](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) zusammen mit zusätzlichen Ressourcen in [https://github.com/adobe-marketing-cloud-apps](https://github.com/adobe-marketing-cloud-apps) verwenden, um AEM Apps mit PhoneGap zu bootstrapping, einschließlich einer Referenz-nativen App, in der Cordova Webviews ausgeführt wird.

Die Readme für das Starter Kit Git-Repository enthält ein Lernprogramm zur Verwendung des Starter-Kits:

* Anpassen des Brandings
* Maven-Zielgruppen zum Erstellen und Bereitstellen von Beispielen
* Repository-Konfiguration der Quellcodeverwaltung
* Installieren und Bereitstellen in lokalen oder Remote-AEM
* Deinstallieren von AEM

>[!NOTE]
>
>Zusätzliche Referenz-Implementierungsquelle, einschließlich Labs, finden Sie auf GitHub [hier](https://github.com/adobe-marketing-cloud-apps) und der Quelle &quot;Küchenbecken&quot; [hier](https://github.com/blefebvre/aem-phonegap-kitchen-sink).

## Entwickeln für IOS 9- und HTTP-Hosts {#developing-for-ios-and-http-hosts}

IOS-Entwickler sollten sich eines offenen Problems mit Cordova-Apps, die unter iOS 9 ausgeführt werden, bewusst sein. Dieses Problem verhindert, dass Anforderungen an unsichere Hosts (wie *http://localhost:4502*) gesendet werden. Dieses Problem wird mit einer kommenden Version von Cordova-Ios (von der Cordova-Befehlszeilenschnittstelle verwendet) behoben, aber in der Zwischenzeit gibt es zwei Workarounds:

1. Als sofortige Problemumgehung können Sie weiterhin jeden beliebigen iOS 8-Simulator ohne Ausgabe verwenden.
1. Wenn Sie iOS 9 verwenden müssen, können Sie die Datei &quot;apps -Info.plist&quot;(die Sie nach der Ausführung von `cordova platform add ios` in &quot;&lt;App-Stammordner>/platforms/ios/&lt;App-Name>/&lt;App-Name>-Info.plist&quot;) manuell bearbeiten, um die folgende Eigenschaft einzuschließen:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Weitere Informationen zu &quot;App Transport Security&quot;finden Sie im folgenden Abschnitt von [Apple&#39;s iOS9 Prerelease docs](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) und in dieser [Stack Overflow-Diskussion](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

## Entwickeln von Mobilanwendungen in AEM {#developing-mobile-applications-in-aem-1}

* [Starten AEM PhoneGap](/help/mobile/starting-aem-phonegap-app.md)
* [Erstellen von Mobilanwendungen](/help/mobile/building-app-mobile-phonegap.md)
* [App strukturieren](/help/mobile/phonegap-structure-an-app.md)
* [Erstellen und Bearbeiten von Apps mit der Apps-Konsole](/help/mobile/phonegap-apps-console.md)
* [Single Page Applications](/help/mobile/phonegap-single-page-applications.md)
* [Entwickeln von Apps mit der PhoneGap-CLI](/help/mobile/phonegap-apps-pg-cli.md)
* [Gerätefunktionen aufrufen](/help/mobile/phonegap-access-device-features.md)
* [Verfolgen der App-Performance mit Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md)
* [hinzufügen von Adobe Analytics zur Mobilanwendung](/help/mobile/phonegap-add-analytics-to-apps.md)
* [Push-Benachrichtigungen](/help/mobile/phonegap-push-notifications.md)
* [Personalisierung von AEM Mobile-Inhalten](/help/mobile/phonegap-aem-mobile-content-personalization.md)
* [Die Anatomie einer App](/help/mobile/phonegap-apps-arch.md)
* [Ist Ihre Hybrid-App für AEM Mobile bereit?](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Zusätzliche Ressourcen {#additional-resources}

Informationen zu den Rollen und Verantwortlichkeiten von Administratoren und Entwicklern finden Sie in den nachfolgend aufgeführten Ressourcen:

* [Authoring für Adobe PhoneGap Enterprise mit AEM](/help/mobile/phonegap.md)
* [Verwalten von Inhalten für Adobe PhoneGap Enterprise mit AEM](/help/mobile/administer-phonegap.md)
