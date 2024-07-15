---
title: Hinzufügen von Adobe Analytics zu einer Mobile App
description: Auf dieser Seite erfahren Sie, wie Sie Mobile App Analytics in Ihren Adobe Experience Manager-Apps verwenden können, indem Sie sie in Adobe Mobile Services integrieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 8d965e94-c368-481d-b000-6e22456c34db
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 2%

---

# Hinzufügen von Adobe Analytics zu einer Mobile App{#add-adobe-analytics-to-your-mobile-application}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Möchten Sie ansprechende und relevante Erlebnisse für Ihre Mobile App-Benutzer erstellen? Wenn Sie das Adobe Mobile Services SDK nicht verwenden, um den Lebenszyklus und die Nutzung von Anwendungen zu überwachen und zu messen, worauf basieren Sie dann auf Ihren Entscheidungen? Wo sind Ihre treusten Kunden? Wie können Sie garantieren, dass Sie relevant bleiben und Konversionen optimieren?

Haben Ihre Benutzer Zugriff auf alle Inhalte? Verlassen sie die App, und wenn ja, wo? Wie oft bleiben sie in der App und wie oft kommen sie zurück, um die App zu verwenden? Welche Änderungen können eingeführt und dann gemessen werden, um die Bindung zu erhöhen? Wie sieht es mit den Absturzraten aus, stürzt Ihre App für Ihre Benutzer ab?

Nutzen Sie die Vorteile von [Mobile App Analytics](https://business.adobe.com/products/analytics/mobile-marketing.html) in Ihren Adobe Experience Manager (AEM)-Apps durch die Integration mit [Adobe Mobile Services](https://business.adobe.com/products/campaign/mobile-marketing.html).

Instrumentieren Sie Ihre AEM-Apps, um zu verfolgen, darüber zu berichten und zu verstehen, wie Ihre Benutzer mit Ihrer mobilen App und Ihren Inhalten interagieren, und um wichtige Lebenszyklusmetriken wie Starts, Zeit in der App und Absturzhäufigkeit zu messen.

In diesem Abschnitt wird beschrieben, wie AEM *Entwickler*:

* Mobile Analytics in Ihre Mobile App integrieren
* Testen Sie Ihr Analytics-Tracking mit Bloodhound.

## Voraussetzungen {#prerequisties}

AEM Mobile benötigt ein Adobe Analytics-Konto, um Tracking-Daten in Ihrer App zu erfassen und zu melden. Im Rahmen der Konfiguration muss der AEM *Administrator* zuerst:

* Richten Sie ein Adobe Analytics-Konto ein und erstellen Sie eine Report Suite für Ihre Anwendung in Mobile Services.
* Konfigurieren Sie einen AMS-Cloud Service in Adobe Experience Manager (AEM).

## Für Entwickler - Integration von Mobile Analytics in Ihre App {#for-developers-integrate-mobile-analytics-into-your-app}

### ContentSync zum Abrufen der Konfigurationsdatei konfigurieren {#configure-contentsync-to-pull-in-configuration-file}

Nachdem das Analytics-Konto eingerichtet wurde, erstellen Sie eine Konfiguration zur Inhaltssynchronisierung , um den Inhalt in Ihre Mobile App zu übernehmen.

Weitere Informationen finden Sie unter Konfigurieren des Inhalts der Inhaltssynchronisierung . Die Konfiguration muss die Inhaltssynchronisierung anweisen, um die ADBMobileConfig im Verzeichnis /www abzulegen. In der Geometrixx Outdoors App ist beispielsweise die Konfiguration für die Inhaltssynchronisierung unter: */content/phonegap/geometrixx-outdoors/shell/jcr:content/page-app/app-config/ams-ADBMobileConfig*. Es gibt auch eine Konfiguration für die Entwicklung. Es ist jedoch identisch mit der Nicht-Entwicklungs-Konfiguration, wenn Geometrixx Outdoors vorhanden sind.

Weitere Informationen zum Herunterladen der ADBMobileConfig über das Dashboard für Mobile Apps AEM Apps finden Sie unter Analytics - Mobile Services - Adobe Mobile Services SDK-Konfigurationsdatei.

```xml
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
    jcr:primaryType="nt:unstructured"
    extension="json"
    path="../../../.."
    selector="ADBMobileConfig"
    targetRootDirectory="www"
    type="mobileADBMobileConfigJSON"/>
```

Für jede Plattform muss ADBMobileConfig an einen bestimmten Speicherort kopiert werden.

Beim Erstellen mit der PhoneGap-CLI kann dies mit Cordova-Build-Hook-Skripten durchgeführt werden. Dies ist in der Geometrixx Outdoors App unter:*content/phonegap/geometrixx-outdoors/shell/_jcr_content/pge-app/app-content/phonegap/scripts/restore_plugins.js.* zu sehen.

Für iOS muss die Datei in den Ordner &quot;**Resources**&quot;des XCode-Projekts kopiert werden (z. B. &quot;platforms/ios/Geometrixx/Resources/ADBMobileConfig.json&quot;). Wenn die App für Android™ vorgesehen ist, lautet der Pfad, in den kopiert werden soll, &quot;platforms/android/assets/ADBMobileConfig.json&quot;. Weitere Informationen zur Verwendung von Hooks während des PhoneGap-CLI-Builds finden Sie unter [Drei Hooks für Ihr Cordova-/PhoneGap-Projekt benötigen](https://gist.github.com/jlcarvalho/22402d013bc72f795d45a01836ce735c).

```xml
///////////////////////////
//          iOS
///////////////////////////
    ios : [
        {
            "www/ADBMobileConfig.json": "platforms/ios/<YOUR_APP_NAME>/Resources/ADBMobileConfig.json"
        }
    ],
///////////////////////////
//          ANDROID
///////////////////////////
    android: [
        {
            "www/ADBMobileConfig.json": "platforms/android/assets/ADBMobileConfig.json"
        }
    ]
```

### Hinzufügen des AMS-Plug-ins in der App {#add-the-ams-plugin-in-the-app}

Damit die App die Daten erfassen kann, muss das Adobe Mobile Services (AMS)-Plug-in als Teil der App enthalten sein. Indem Sie das Plug-in als Funktion in die config.xml der App einfügen, kann ein weiterer Cordova-Erweiterungspunkt verwendet werden, um das Plug-in während des PhoneGap-Build-Prozesses automatisch hinzuzufügen.

```xml
<feature name="ADBMobile">
    <param name="id" value="https://github.com/Adobe-Marketing-Cloud/mobile-services#0482f9cedf90c98a8d4b07219ece1933b2e46a60"/>
</feature>
```

Die Geometrixx Outdoors App config.xml befindet sich unter */content/phonegap/geometrixx-outdoors/shell/jcr:content/pge-app/app-content/phonegap/www/config.xml*. Im obigen Beispiel wird eine bestimmte Version des Plug-ins angefordert, indem ein &quot;#&quot;hinzugefügt und anschließend ein Tag-Wert nach der Plug-in-URL eingefügt wird. Dies ist eine Best Practice, um sicherzustellen, dass nicht erwartete Probleme nicht auftreten, da nicht getestete Plug-ins während eines Builds hinzugefügt werden.

Nachdem Sie diese Schritte ausgeführt haben, kann Ihre App alle von Adobe Analytics bereitgestellten Lebenszyklusmetriken melden. Dazu gehören Daten wie Starts, Abstürze und Installationen. Wenn es die einzigen Daten sind, die Ihnen wichtig sind, dann sind Sie fertig. Wenn Sie benutzerdefinierte Daten erfassen möchten, müssen Sie Ihren Code instrumentieren.

### Instrumentieren Ihres Codes für das vollständige App-Tracking {#instrument-your-code-for-full-app-tracking}

Es gibt mehrere Tracking-APIs, die in der [AMS PhoneGap-Plug-in-API](https://github.com/Adobe-Marketing-Cloud/mobile-services/blob/master/docs/ios/phonegap/phonegap-methods.md) bereitgestellt werden.

Auf diese Weise können Sie Status und Aktionen verfolgen, z. B., wohin Seiten Ihre Benutzer in Ihrer App navigieren und welche Steuerelemente am häufigsten verwendet werden. Die einfachste Möglichkeit, Ihre App für das Tracking zu instrumentieren, besteht in der Verwendung der Analytics-APIs, die vom AMS-Plug-in bereitgestellt werden.

* ADB.trackState()
* ADB.trackAction()

Sehen Sie sich den Code in der Geometrixx Outdoors App an. In der Geometrixx Outdoors App wird die gesamte Seitennavigation mithilfe der ADB.trackState() -Methode verfolgt. Weitere Informationen finden Sie im Quellcode für /libs/mobileapps/components/angular/ng-page/clientlibs/app-navigation.js

Durch die Instrumentierung Ihres Quellcodes mit diesen Methodenaufrufen können Sie vollständige Metriken für Ihre Anwendung erfassen.

#### Eigenschaften für die Verbindung mit AMS {#properties-for-connecting-to-ams}

*com.adobe.cq.mobile.mobileservices.impl.service.MobileServicesHttpClientImp* l legt die folgenden Eigenschaften für die Verbindung mit AMS offen:

| **Beschriftung** | **Beschreibung** | **Standard** |
|---|---|---|
| API-Endpunkt | Die Basis-URL der Adobe Mobile Services-HTTP-APIs | https://api.omniture.com |
| Config Endpoint | Die URL, die zum Abrufen der ADB Mobile-Konfiguration für die jeweilige Report Suite-ID verwendet wird | /ams/1.0/app/config/ |
| Mobile Service-Apps | Abrufen einer Liste von Apps im Benutzerunternehmen | /ams/1.0/apps |
