---
title: hinzufügen von Adobe Analytics zur Mobilanwendung
seo-title: hinzufügen von Adobe Analytics zur Mobilanwendung
description: Auf dieser Seite erfahren Sie, wie Sie Mobile App Analytics in Ihren AEM-Apps verwenden können, indem Sie sie in Adobe Mobile Services integrieren.
seo-description: Auf dieser Seite erfahren Sie, wie Sie Mobile App Analytics in Ihren AEM-Apps verwenden können, indem Sie sie in Adobe Mobile Services integrieren.
uuid: d3ff6f9b-0467-4abe-9a59-b3495a6af0f8
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: cd9d2bea-48d8-4a17-8544-ea25dcad69f3
translation-type: tm+mt
source-git-commit: 8279cd590244a7f2d20cfaf1c7505a3ef57fae4a
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 2%

---


# hinzufügen von Adobe Analytics in Ihre Mobilanwendung{#add-adobe-analytics-to-your-mobile-application}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Möchten Sie ansprechende und relevante Erlebnisse für Ihre Benutzer mobiler Anwendungen erstellen? Wenn Sie das Adobe Mobile Services SDK nicht zur Überwachung und Messung von Anwendungslebenszyklus und -nutzung verwenden, auf welcher Grundlage basieren Sie dann Ihre Entscheidungen? Wo sind Ihre treusten Kunden? Wie können Sie sicherstellen, dass Sie relevant bleiben und Konversionen optimieren?

Haben Ihre Benutzer Zugriff auf den gesamten Inhalt? Verlassen sie die App, und wenn ja, wo? Wie oft bleiben sie in der App und wie oft kommen sie zurück, um die App zu verwenden? Welche Änderungen können Sie einführen und dann messen, dass die Retention erhöht wird? Was ist mit den Absturzraten, stürzt Ihre App für Ihre Benutzer ab?

Nutzen Sie die Vorteile von [Mobile App Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) in Ihren AEM-Apps, indem Sie [Adobe Mobile Services](https://www.adobe.com/marketing-cloud/mobile-marketing.html) integrieren.

Instrumentieren Sie Ihre AEM-Apps, um zu verfolgen, Berichte darüber zu erstellen und zu verstehen, wie Sie mit Ihrer mobilen App und Ihren Inhalten interagieren, und um wichtige Lebenszyklusmetriken wie Starts, Besuchszeit in der App und Absturzrate zu messen.

In diesem Abschnitt wird beschrieben, wie AEM *Entwickler*:

* Mobile Analytics in Ihre mobile Anwendung integrieren
* Testen Sie Ihre Analysenachverfolgung mit Bloodhound.

## Voraussetzungen {#prerequisties}

AEM Mobile benötigt ein Adobe Analytics-Konto, um Verfolgungsdaten in Ihrer App zu erfassen und zu melden. Als Teil der Konfiguration muss der AEM *Administrator* zunächst:

* Richten Sie ein Adobe Analytics-Konto ein und erstellen Sie eine Report Suite für Ihre Anwendung in Mobile Services.
* Konfigurieren Sie einen AMS-Cloud Service in Adobe Experience Manager (AEM).

## Für Entwickler - Integration von Mobile Analytics in Ihre App {#for-developers-integrate-mobile-analytics-into-your-app}

### ContentSync zum Ziehen der Konfigurationsdatei {#configure-contentsync-to-pull-in-configuration-file} konfigurieren

Nachdem Sie das Analytics-Konto eingerichtet haben, müssen Sie eine Inhaltssynchronisierungskonfiguration erstellen, um den Inhalt in Ihre Mobile-Anwendung zu übernehmen.

Weitere Informationen finden Sie unter Konfigurieren des Inhalts der Inhaltssynchronisierung. Die Konfiguration muss Content Sync anweisen, ADBMobileConfig in den Ordner /www zu verschieben. In der Geometrixx Outdoors-App befindet sich beispielsweise die Content Sync-Konfiguration unter: */content/phonegap/geometrixx-outdoors/shell/jcr:content/pge-app/app-config/ams-ADBMobileConfig*. Es gibt auch eine Konfiguration für die Entwicklung. es ist jedoch bei Geometrixx Outdoors identisch mit der Nicht-Entwicklungskonfiguration.

Weitere Informationen zum Herunterladen von ADBMobileConfig aus Ihrem Mobile Application AEM Apps-Dashboard finden Sie unter Analytics - Mobile Services - Adobe Mobile Services SDK-Konfigurationsdatei.

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

Wenn Sie mit der PhoneGap-CLI erstellen, können Sie dies mit einem Cordova-Build-Hook-Skript tun. Dies ist in der Geometrixx Outdoors-App zu sehen unter:*content/phonegap/geometrixx-outdoors/shell/_jcr_content/pge-app/app-content/phonegap/scripts/restore_plugins.js.*

Für iOS muss die Datei in den Ordner **Resources** des XCode-Projekts kopiert werden (z.B. &quot;platforms/ios/Geometrixx/Resources/ADBMobileConfig.json&quot;). Wenn die App auf Android ausgerichtet ist, lautet der Pfad, in den kopiert werden soll, &quot;platforms/android/assets/ADBMobileConfig.json&quot;. Weitere Informationen zur Verwendung von Haken während des PhoneGap-CLI-Builds finden Sie unter [Drei Haken, die Ihr Cordova/PhoneGap-Projekt benötigt](https://devgirl.org/2013/11/12/three-hooks-your-cordovaphonegap-project-needs/).

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

### hinzufügen Sie das AMS-Plugin in der App {#add-the-ams-plugin-in-the-app}

Damit die App die Daten erfassen kann, muss das AMS-Zusatzmodul (Adobe Mobile Services) als Teil der App enthalten sein. Indem das Plugin als Funktion in die Datei &quot;config.xml&quot;der App aufgenommen wird, kann ein weiterer Cordova-Haken verwendet werden, um das Plugin während des PhoneGap-Build-Prozesses automatisch hinzuzufügen.

```xml
<feature name="ADBMobile">
    <param name="id" value="https://github.com/Adobe-Marketing-Cloud/mobile-services#0482f9cedf90c98a8d4b07219ece1933b2e46a60"/>
</feature>
```

Die Geometrixx Outdoors App config.xml befindet sich unter */content/phonegap/geometrixx-outdoors/shell/jcr:content/pge-app/app-content/phonegap/www/config.xml*. Im obigen Beispiel wird eine bestimmte Version des Plugins angefordert, indem ein &quot;#&quot;und anschließend ein Tag-Wert nach der Plug-in-URL hinzugefügt werden. Dies ist eine gute Vorgehensweise, um sicherzustellen, dass unerwartete Probleme nicht angezeigt werden, da nicht getestete Plugins während eines Builds hinzugefügt werden.

Nachdem Sie diese Schritte ausgeführt haben, wird Ihre App in die Lage versetzt, alle von Adobe Analytics bereitgestellten Lebenszyklusmetriken zu melden. Dazu gehören Daten wie Starts, Abstürze und Installationen. Wenn das die einzigen Daten sind, die Ihnen wichtig sind, dann sind Sie fertig. Wenn Sie benutzerdefinierte Daten erfassen möchten, müssen Sie Ihren Code instrumentieren.

### Geben Sie Ihren Code für die vollständige App-Verfolgung ein {#instrument-your-code-for-full-app-tracking}

Die API für das AMS PhoneGap-Plugin enthält mehrere Tracking-APIs.](https://docs.adobe.com/content/help/en/mobile-services/ios/phonegap-ios/phonegap-methods.html)[

Auf diese Weise können Sie Status und Aktionen verfolgen, z. B., zu welchen Seiten Ihre Benutzer in Ihrer App navigieren, welche Steuerelemente am häufigsten verwendet werden. Die einfachste Möglichkeit, Ihre App für die Verfolgung zu instrumentieren, besteht darin, die Analytics-APIs zu verwenden, die vom AMS-Plugin bereitgestellt werden.

* ADB.trackState()
* ADB.trackAction()

Als Referenz können Sie sich den Code in der Geometrixx Outdoors-App ansehen. In der Geometrixx Outdoors-App werden alle Seitennavigationen mit der ADB.trackState()-Methode verfolgt. Weitere Informationen finden Sie im Quellcode unter /libs/mobileapps/components/angular/ng-page/clientlibs/app-navigation.js

Indem Sie Ihren Quellcode mit diesen Methodenaufrufen instrumentieren, können Sie vollständige Metriken für Ihre Anwendung erfassen.

#### Eigenschaften für die Verbindung mit AMS {#properties-for-connecting-to-ams}

*com.adobe.cq.mobile.mobileservices.impl.service.* MobileServicesHttpClientImpl stellt die folgenden Eigenschaften für die Verbindung mit AMS bereit:

| **Bezeichnung** | **Beschreibung** | **Default** |
|---|---|---|
| API-Endpunkt | Die Basis-URL der HTTP-APIs der Adobe Mobile Services | https://api.omniture.com |
| Config-Endpunkt | Die URL, die zum Abrufen der ADB Mobile-Konfiguration für die angegebene Report Suite-ID verwendet wird | /ams/1.0/app/config/ |
| Mobile Service-Apps | Liste von Apps in der Firma &quot;Benutzer&quot; | /ams/1.0/apps |

