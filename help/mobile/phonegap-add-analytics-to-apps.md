---
title: Adobe Analytics zu Ihrer Mobile App hinzufügen
description: Auf dieser Seite erfahren Sie, wie Sie Mobile App Analytics in Ihren Adobe Experience Manager-Apps verwenden können, indem Sie es mit Adobe Mobile Services integrieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 8d965e94-c368-481d-b000-6e22456c34db
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Adobe Analytics zu Ihrer Mobile App hinzufügen{#add-adobe-analytics-to-your-mobile-application}

{{ue-over-mobile}}

Möchten Sie ansprechende und relevante Erlebnisse für Benutzer Ihrer Mobile App erstellen? Wenn Sie die Adobe Mobile Services SDK nicht zur Überwachung und Messung des Anwendungslebenszyklus und der Anwendungsnutzung verwenden, worauf gründen Sie dann Ihre Entscheidungen? Wo sind Ihre treuesten Kunden? Wie können Sie garantieren, dass Sie relevant bleiben und Konversionen optimieren?

Greifen Ihre Benutzer auf den gesamten Inhalt zu? Geben sie die App auf und wenn ja, wo? Wie oft bleiben sie in der App und wie oft kommen sie zurück, um die App zu verwenden? Welche Änderungen können eingeführt und dann gemessen werden, um die Kundenbindung zu erhöhen? Wie steht es mit Absturzraten? Stürzt Ihre Mobile App für Ihre Benutzer ab?

Nutzen Sie [Mobile App Analytics](https://business.adobe.com/products/analytics/mobile-marketing.html) in Ihren Adobe Experience Manager (AEM) Apps durch die Integration mit [Adobe Mobile Services](https://business.adobe.com/products/campaign/mobile-marketing.html).

Instrumentieren Sie Ihre AEM-Apps, um zu verfolgen, Berichte zu erstellen und zu verstehen, wie Ihre Benutzerinnen und Benutzer mit Ihrer Mobile App und Ihren Inhalten interagieren, und um wichtige Lebenszyklusmetriken wie Starts, Zeit in der App und Absturzrate zu messen.

In diesem Abschnitt wird beschrieben, wie AEM *Entwickler*:

* Integrieren von Mobile Analytics in Ihre Mobile App
* Analytics-Tracking mit Bloodhound testen

## Voraussetzungen {#prerequisties}

AEM Mobile erfordert ein Adobe Analytics-Konto, um Tracking-Daten in Ihrer App zu erfassen und zu melden. Im Rahmen der Konfiguration muss der AEM *Administrator* zuerst:

* Richten Sie ein Adobe Analytics-Konto ein und erstellen Sie eine Report Suite für Ihre Mobile App in Mobile Services.
* AMS-Cloud Service in Adobe Experience Manager (AEM) konfigurieren.

## Für Entwickler: Integrieren von Mobile Analytics in die App {#for-developers-integrate-mobile-analytics-into-your-app}

### Konfigurieren von ContentSync zum Abrufen der Konfigurationsdatei {#configure-contentsync-to-pull-in-configuration-file}

Erstellen Sie nach der Einrichtung des Analytics-Kontos eine Inhaltssynchronisierungskonfiguration, um den Inhalt in Ihre Mobile App zu übertragen.

Weitere Informationen finden Sie unter Konfigurieren des Inhaltssynchronisierungsinhalts . Die Konfiguration muss Content Sync anweisen, die ADBMobileConfig in das Verzeichnis /www abzulegen. In der Geometrixx Outdoors-App befindet sich die Inhaltssynchronisierungskonfiguration beispielsweise unter: */content/phonegap/geometrixx-outdoors/shell/jcr:content/pge-app/app-config/ams-ADBMobileConfig*. Es gibt auch eine Konfiguration für die Entwicklung. Sie ist jedoch mit der Nicht-Entwicklungskonfiguration identisch, wenn Geometrixx Outdoors vorhanden sind.

Weitere Informationen zum Herunterladen von ADBMobileConfig von Ihrem Dashboard für Mobile-App-AEM-Apps finden Sie unter Analytics - Mobile Services - Adobe Mobile Services SDK Config File.

```xml
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
    jcr:primaryType="nt:unstructured"
    extension="json"
    path="../../../.."
    selector="ADBMobileConfig"
    targetRootDirectory="www"
    type="mobileADBMobileConfigJSON"/>
```

Für jede Plattform muss die ADBMobileConfig an einen bestimmten Speicherort kopiert werden.

Beim Erstellen mit der PhoneGap-CLI kann dies mit einem Cordova-Build-Hook-Skript erfolgen. Dies ist in der Geometrixx Outdoors-App unter folgender Adresse zu sehen:*content/phonegap/geometrixx-outdoors/shell/_jcr_content/pge-app/app-content/phonegap/scripts/restore_plugins.js.*

Für iOS muss die Datei in das Verzeichnis **Resources“ des XCode** Projekts kopiert werden (z. B. &quot;platforms/ios/Geometrixx/Resources/ADBMobileConfig.json„). Wenn die App für Android™ vorgesehen ist, lautet der Pfad zum Kopieren &quot;platforms/android/assets/ADBMobileConfig.json&quot;. Weitere Informationen zur Verwendung von Erweiterungspunkten während der PhoneGap-CLI-Erstellung finden Sie unter [Drei Erweiterungspunkte, die Ihr Cordova/PhoneGap-Projekt benötigt](https://gist.github.com/jlcarvalho/22402d013bc72f795d45a01836ce735c).

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

Damit die App die Daten erfassen kann, muss das AMS-Plug-in (Adobe Mobile Services) in die App aufgenommen werden. Indem Sie das Plug-in als Funktion in die config.xml der App aufnehmen, kann ein anderer Cordova-Hook verwendet werden, um das Plug-in während des PhoneGap-Build-Prozesses automatisch hinzuzufügen.

```xml
<feature name="ADBMobile">
    <param name="id" value="https://github.com/Adobe-Marketing-Cloud/mobile-services#0482f9cedf90c98a8d4b07219ece1933b2e46a60"/>
</feature>
```

Die Geometrixx Outdoors-App config.xml befindet sich unter */content/phonegap/geometrixx-outdoors/shell/jcr:content/pge-app/app-content/phonegap/www/config.xml*. Im obigen Beispiel wird die Verwendung einer bestimmten Version des Plug-ins angefordert, indem nach der Plug-in-URL ein &#39;#&#39; und dann ein Tag-Wert hinzugefügt werden. Dies ist eine gute Vorgehensweise, um sicherzustellen, dass keine unerwarteten Probleme auftreten, da während eines Builds nicht getestete Plug-ins hinzugefügt werden.

Nachdem Sie diese Schritte ausgeführt haben, kann Ihre App alle von Adobe Analytics bereitgestellten Lebenszyklusmetriken melden. Dazu gehören Daten wie Starts, Abstürze und Installationen. Wenn das die einzigen Daten sind, die einem wichtig sind, dann seid ihr fertig. Wenn Sie benutzerdefinierte Daten erfassen möchten, müssen Sie Ihren Code instrumentieren.

### Instrumentieren des Codes für das vollständige App-Tracking {#instrument-your-code-for-full-app-tracking}

In der AMS Phonegap-Plug-in[API sind mehrere Tracking-APIs verfügbar](https://github.com/Adobe-Marketing-Cloud/mobile-services/blob/master/docs/ios/phonegap/phonegap-methods.md)

Auf diese Weise können Sie Status und Aktionen verfolgen, z. B. wo Ihre Benutzerinnen und Benutzer in Ihrer App zu Seiten navigieren, welche Steuerelemente am häufigsten verwendet werden. Die einfachste Möglichkeit, Ihre App für das Tracking zu instrumentieren, besteht in der Verwendung der Analytics-APIs, die vom AMS-Plug-in bereitgestellt werden.

* ADB.trackState()
* ADB.trackAction()

Sehen Sie sich als Referenz den Code in der Geometrixx Outdoors-App an. In der Geometrixx Outdoors-App wird die gesamte Seitennavigation mit der Methode ADB.trackState() verfolgt. Weitere Informationen finden Sie im Quellcode für /libs/mobileapps/components/angular/ng-page/clientlibs/app-navigation.js

Indem Sie Ihren Quell-Code mit diesen Methodenaufrufen instrumentieren, können Sie vollständige Metriken für Ihr Programm erfassen.

#### Eigenschaften für die Verbindung mit AMS {#properties-for-connecting-to-ams}

*com.adobe.cq.mobile.mobileservices.impl.service.MobileServicesHttpClientImp* l macht die folgenden Eigenschaften für die Verbindung mit AMS verfügbar:

| **label** | **Beschreibung** | **Standard** |
|---|---|---|
| API-Endpunkt | Die Basis-URL der Adobe Mobile Services-HTTP-APIs | https://api.omniture.com |
| config-Endpunkt | Die URL, die zum Abrufen der ADB Mobile-Konfiguration für die angegebene Report Suite-ID verwendet wird | /ams/1.0/app/config/ |
| Mobile Service-Apps | Abrufen einer Liste von Apps innerhalb des Unternehmens der Benutzer | /ams/1.0/apps |
