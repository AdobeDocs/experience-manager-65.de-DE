---
title: Auf Gerätefunktionen zugreifen
description: Auf dieser Seite erfahren Sie, wie Sie Adobe Experience Manager (AEM)-Komponenten erstellen, die auf Gerätefunktionen zugreifen. Das AEM PhoneGap Kitchen Sink GitHub-Repository stellt Entwicklern eine funktionale AEM App zur Verfügung, die die Verwendung mehrerer Cordova-Core-APIs veranschaulicht.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 385f7924-e8ab-4dcb-83f0-7b81bead3dda
source-git-commit: 96e2e945012046e6eac878389b7332985221204e
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 3%

---

# Auf Gerätefunktionen zugreifen{#access-device-features}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

## Erstellen von Adobe Experience Manager (AEM)-Komponenten, die auf Gerätefunktionen zugreifen {#building-aem-components-that-access-device-features}

Die [AEM PhoneGap Kitchen Sink](https://github.com/blefebvre/aem-phonegap-kitchen-sink) Das GitHub-Repository bietet Entwicklern eine funktionale AEM App, die die Verwendung mehrerer Cordova-Haupt-APIs veranschaulicht. Wenn die App über die PhoneGap-CLI auf iOS oder Android™ ausgeführt wird, wird sie auf der folgenden Seite geöffnet, auf der sie einen Link zu den einzelnen Geräte-APIs enthält, die sie demonstriert:

![chlimage_1-107](assets/chlimage_1-107.png)

Der Quellcode für jede dieser Geräte-API-Komponenten lautet [auf GitHub verfügbar](https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/apps/brucelefebvre/kitchen-sink/components).

Weitere Informationen zur Verwendung der einzelnen APIs finden Sie in der Dokumentation zum Cordova-Plug-in (`https://docs.phonegap.com/en/4.0.0/cordova_plugins_pluginapis.md.html`).

## Die nächsten Schritte {#the-next-steps}

Siehe [App-Leistung mit Adobe Mobile Analytics verfolgen](/help/mobile/phonegap-intro-to-app-analytics.md).
