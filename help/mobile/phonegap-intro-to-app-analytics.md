---
title: Verfolgen der App-Performance mit Adobe Mobile Analytics
seo-title: Verfolgen der App-Performance mit Adobe Mobile Analytics
description: Mit Adobe Mobile Services erhalten Sie Einblicke in die Verwendung Ihrer mobilen Apps durch Tracking-Nutzung, App-Abstürze, Gerätetexte und so viele andere wichtige Metriken für Ihre mobilen Apps. Auf dieser Seite erfahren Sie mehr.
seo-description: Mit Adobe Mobile Services erhalten Sie Einblicke in die Verwendung Ihrer mobilen Apps durch Tracking-Nutzung, App-Abstürze, Gerätetexte und so viele andere wichtige Metriken für Ihre mobilen Apps. Auf dieser Seite erfahren Sie mehr.
uuid: 139858c7-66a1-4fea-9f7e-4671b86f67e6
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 377548fa-987a-4a59-84a3-067a3541b6b2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 10%

---


# Verfolgen der App-Performance mit Adobe Mobile Analytics{#track-app-performance-with-adobe-mobile-analytics}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Sie möchten höhere Kundenkonversionen und mehr Loyalität erzielen.

Sie möchten Ihren Kunden relevante und ansprechende Erlebnisse bereitstellen.

Was macht Ihre AEM Mobile-App für Ihre Marketing-Kampagnen?

Wie können Sie Ihre mobilen Anwendungen optimieren, um den Benutzern das beste Erlebnis zu bieten?

Mit Adobe Mobile Services erhalten Sie Einblicke in die Verwendung Ihrer mobilen Apps durch Tracking-Nutzung, App-Abstürze, Gerätetexte und so viele andere wichtige Metriken für Ihre mobilen Apps.

Adobe Experience Manager Mobile bietet einen Einblick in die Details Ihrer mobilen Analyse direkt vom AEM Mobile Application Dashboard. Die **Mobilmetriken-Kachel** im Dashboard bietet Echtzeitanalysen für Ihre Mobilanwendung, sodass Entwickler, Autoren und Administratoren einen schnellen Überblick über den Zustand Ihrer mobilen App erhalten. Unter den Deckblättern wird das SDK [Adobe Mobile Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) aktiviert. Das Adobe Mobile Analytics SDK kann für Webansichten nativ oder über ein PhoneGap-Bridge-Plug-in in Ihre Anwendungen eingeklinkt werden. Metriken werden erfasst und auf dem Gerät zwischengespeichert, bis das Gerät angeschlossen ist und die Daten an die Adobe Mobile Services Cloud für Berichte und Analyse gesendet werden.

Das Adobe Mobile Analytics-SDK bietet Folgendes:

1. **Datenerfassung für mobile Kanäle** - Erfassen Sie umfassende Daten zu Ihren mobilen Websites und Apps auf allen wichtigen Betriebssystemen.
1. **Analyse**  zur Interaktion mit Mobilgeräten: Verstehen Sie die Interaktion der Benutzer mit Ihrer mobilen App, Website oder Ihrem Video, einschließlich der Häufigkeit, mit der der Kanal gestartet wird, der Anzahl der getätigten Käufe und mehr.
1. **Mobile App-Dashboard und -Berichte**  - Nutzungsberichte mit Lebenszyklusmetriken für Ihre Apps- und App Store-Metriken abrufen — Zeigen Sie Trends für Benutzer, Starts, durchschnittliche Sitzungslänge, Aufbewahrungslänge und Abstürze an.
1. **Analyse**  mobiler Kampagnen - Quantifizieren Sie die Effektivität mobiler Kampagnen wie SMS, Mobil-Suchwerbung, Display-Anzeigen und QR-Codes.
1. **Geolocation-Analyse** : Finden Sie heraus, wo Ihre App-Benutzer Ihre mobilen Erlebnisse starten und mit ihnen interagieren, nach GPS-Position oder Zielpunkten.
1. **Pfade**  - Erfahren Sie, wie Benutzer durch Ihre App navigieren, um festzustellen, welche Bildschirme und UI-Elemente Benutzer ansprechen und welche die Benutzer abbrechen.

In diesem Abschnitt wird beschrieben, wie [AEM-Entwickler ](#developers) dann lernen können, wie AEM Mobile-Apps mit Analytics-Verfolgung instrumentiert werden.

[AEM Administratoren](#administrators) lernen schließlich Folgendes:

* Cloud-Dienst für Adobe Mobile Services erstellen
* Erstellen einer Mobile Service-Konfiguration und Verknüpfen einer Report Suite
* Zuordnen der Mobile Service-Konfiguration zu einer mobilen App
* Metriken zur Ansicht über das AEM Apps Command Center
* AMS SDK-Konfiguration zu Ihrer mobilen App zuweisen

## Für Entwickler - Integration von Analytics in Ihre App {#for-developers-integrate-analytics-into-your-app}

**Voraussetzung:** AEM Administratoren müssen die Konfiguration der Adobe Mobile Services Cloud konfigurieren,  [wie nachfolgend](#amscloudserviceconfig) beschrieben.

Entwickler sind dafür verantwortlich, nach Bedarf Analysen zu einer AEM Mobile-App hinzuzufügen, um zu verfolgen, Berichte darüber zu erstellen und zu verstehen, wie Benutzer mit Ihren mobilen App-Inhalten interagieren, und wichtige Lebenszyklusmetriken wie Starts, Besuchszeit in der App und Absturzrate zu messen.[](/help/mobile/phonegap-add-analytics-to-apps.md)

## Für Administratoren - Konfigurieren des Adobe Mobile Services-Cloud Service {#for-administrators-configure-the-adobe-mobile-services-cloud-service}

Um die Adobe Mobile Services nutzen zu können, müssen Sie den AEM Adobe Mobile Services Cloud Service mit Ihren Adobe Analytics-Kontoinformationen konfigurieren. Das Apps Command Center bietet eine Kachel **Metriken analysieren**, in der Sie den Cloud-Dienst erstellen und mit Ihrer mobilen App verknüpfen können.

Konfigurieren Sie den Cloud-Dienst für Ihre mobile App, indem Sie auf das Zahnradsymbol in der Kachel &quot;Metriken analysieren&quot;klicken.

![chlimage_1-125](assets/chlimage_1-125.png)

Wenn Sie auf das Zahnradsymbol in der Kachel &quot;Metriken analysieren&quot;klicken, wird das modale Dialogfeld &quot;Analyse der Mobile Services konfigurieren&quot;geöffnet. Wählen Sie Ihre Konfiguration aus der Dropdownliste &quot;Konfiguration des mobilen Dienstes auswählen&quot;aus. Wenn Sie eine neue Konfiguration erstellen müssen, klicken Sie auf die Schraubenschlüssel-Schaltfläche.

Zum Erstellen eines Adobe Mobile Service Cloud-Dienstes sind zwei Schritte erforderlich: die Verbindung zum Dienst und die Auswahl der Berichte-Suite, die der Konfiguration zugewiesen werden soll.

Um zu beginnen, klicken Sie auf die Schaltfläche &quot;+&quot;in der Kachel Cloud Services verwalten im Dashboard.

![chlimage_1-126](assets/chlimage_1-126.png)

Wenn Sie auf die Schaltfläche &quot;**+**&quot;klicken, wird der Assistent **Hinzufügen Cloud Service** angezeigt.

![chlimage_1-127](assets/chlimage_1-127.png)

Wählen oder erstellen Sie eine neue Konfiguration des mobilen Dienstes, indem Sie die erforderlichen Felder wie unten gezeigt ausfüllen. Der AEM-Administrator benötigt diese Informationen, um die Verbindung mit Adobe Mobile Services erfolgreich herstellen zu können.

![chlimage_1-128](assets/chlimage_1-128.png)

Nachdem Sie die Kontoeinstellungen für Mobile Services abgeschlossen haben, werden Sie aufgefordert, eine App auszuwählen. Dadurch wird Adobe Mobile Service Analytics Berichte mit dieser Anwendung verbunden.

Wählen Sie den gewünschten Mobildienst aus und klicken Sie auf &quot;Aktualisieren&quot;, um die Konfiguration des Mobilfunkdienstes zuzuweisen und das Dialogfeld zu schließen.

Nachdem Sie die Konfiguration des Mobildienstes mit der AEM Mobile-App verknüpft haben, ruft die Kachel die Metrikdaten ab und beginnt mit dem Berichte.

![chlimage_1-129](assets/chlimage_1-129.png)

### Adobe Mobile Services SDK-Konfigurationsdatei {#adobe-mobile-services-sdk-config-file}

Zu diesem Zeitpunkt ist Ihre Mobilanwendung mit einem Cloud-Dienst verknüpft, aber die Mobilanwendung weiß noch nicht, wie die erfassten Metriken für Mobilgeräte wieder an Adobe Analytics übermittelt werden sollen. Um die mobile App mit Adobe Analytics zu verbinden, muss die Adobe Mobile Services SDK Config-Datei Adobe Experience Manager hinzugefügt werden.

Klicken Sie in der Kachel Metriken analysieren auf das Pfeilsymbol, um die Menüeinträge AMS SDK-Konfiguration herunterladen/hochladen anzuzeigen.

![chlimage_1-130](assets/chlimage_1-130.png)

Der erste Schritt besteht darin, die SDK-Konfiguration von Adobe Mobile Services abzurufen. Wenn Sie auf &quot;AMS SDK-Konfiguration herunterladen&quot;klicken, werden Sie zur Adobe Mobile Services-Website weitergeleitet, von der Sie die Konfigurationsdatei herunterladen können. Nachdem Sie die Datei ADBMobileConfig.json erhalten haben, klicken Sie auf &quot;AMS SDK Config hochladen&quot;, um die Konfigurationsdatei in AEM hochzuladen.

![chlimage_1-131](assets/chlimage_1-131.png)

Klicken Sie auf die Schaltfläche &quot;Adobe hochladen - Anwendungskonfiguration&quot;und suchen Sie die Datei &quot;ADBMobileConfig.json&quot;und klicken Sie dann auf &quot;Hochladen&quot;.

Jetzt, wo die mobile App Zugriff auf die Datei ADBMobileConfig.json hat, verfügt sie über Kenntnisse, wie sie mit Adobe Analytics kommunizieren und Berichte über diese wichtigen Metrikwerte starten kann, die Ihren Apps zum Erfolg verhelfen.

## Wie geht es weiter? {#what-s-next}

1. [Mein AEM Mobile App-Erlebnis](/help/mobile/starting-aem-phonegap-app.md) 
1. [Verwalten des App-Inhalts](/help/mobile/phonegap-manage-app-content.md) 
1. [Erstellen meiner Anwendung](/help/mobile/building-app-mobile-phonegap.md) 
1. [Messen der Leistung meiner App mit Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md) 
1. [Ein personalisiertes App-Erlebnis mit Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md) 
1. [Senden wichtiger Nachrichten an meine Benutzer](/help/mobile/phonegap-push-notifications.md) 