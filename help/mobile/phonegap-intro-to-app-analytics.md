---
title: App-Leistung mit Adobe Mobile Analytics verfolgen
description: Mit Adobe Mobile Services können Sie Einblicke in die Verwendung Ihrer mobilen Apps erhalten, indem Sie die Nutzung, App-Abstürze, Gerätedetails und so viele andere wichtige Metriken für Ihre mobilen Apps verfolgen. Auf dieser Seite erfahren Sie mehr.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 7e358660-bc2f-4d8f-8d74-6cdb6c1ea7b5
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 1%

---

# App-Leistung mit Adobe Mobile Analytics verfolgen{#track-app-performance-with-adobe-mobile-analytics}

{{ue-over-mobile}}

Sie möchten höhere Kundenkonversionen und die Kundentreue fördern.

Sie möchten Ihren Kunden relevante und ansprechende Erlebnisse bieten.

Was tut Ihre AEM Mobile-App für Ihre Marketing-Kampagnen?

Wie können Sie Ihre Mobile Apps optimieren, um Ihren Benutzern das beste Erlebnis zu bieten?

Mit Adobe Mobile Services können Sie Einblicke in die Verwendung Ihrer mobilen Apps erhalten, indem Sie die Nutzung, App-Abstürze, Gerätedetails und so viele andere wichtige Metriken für Ihre mobilen Apps verfolgen.

Adobe Experience Manager Mobile bietet einen Einblick in die Details Ihrer Mobile-Analyse direkt über das AEM Mobile-Anwendungs-Dashboard. Die Kachel **Mobile Metriken** im Dashboard bietet Real-Time Analytics für Ihre Mobile App, sodass Entwickelnde, Autoren und Administratoren einen schnellen Überblick über den Zustand Ihrer Mobile App erhalten. Unter der Abdeckung ist das Bereitstellen der Analyse die [Adobe Mobile Analytics](https://business.adobe.com/de/products/analytics/mobile-marketing.html)-SDK. Das Adobe Mobile Analytics SDK kann nativ oder über ein PhoneGap Bridge-Plug-in für Webansichten an Ihre Anwendungen angeschlossen werden. Metriken werden erfasst und auf dem Gerät zwischengespeichert, bis das Gerät verbunden ist, wodurch die Daten zur Berichterstellung und Analyse an die Adobe Mobile Services Cloud übertragen werden.

Adobe Mobile Analytics SDK bietet Folgendes:

1. **Datenerfassung für mobile Kanäle** - Erfassen Sie umfassende Daten für Ihre mobilen Websites und Apps auf allen wichtigen Betriebssystemen.
1. **Mobile Interaktionsanalyse** - Verstehen Sie die Benutzerinteraktion in Ihrer Mobile App, Website oder in Ihrem Video, einschließlich der Häufigkeit, mit der Verbraucher den Kanal starten, ob sie darüber Einkäufe tätigen und mehr.
1. **Mobile-App-Dashboards und -Berichte** - Erhalten Sie Nutzungsberichte, die Lebenszyklusmetriken für Ihre Apps und App-Store-Metriken enthalten - sehen Sie Trends für Benutzer, Launches, durchschnittliche Sitzungsdauer, Aufbewahrungsdauer und Abstürze.
1. **Mobile-Kampagnenanalyse** - Quantifizieren Sie die Effektivität mobilgerätespezifischer Kampagnen wie SMS, mobile Suchanzeigen, mobile Display-Anzeigen und QR-Codes.
1. **Geolokalisierungsanalyse** - Ermitteln Sie anhand des GPS-Standorts oder der Points of Interest, wo Ihre App-Benutzer starten und mit Ihren mobilen Erlebnissen interagieren.
1. **Pfadanalyse** Ermitteln Sie, wie Benutzer durch Ihre App navigieren, um festzustellen, welche Bildschirme und Benutzeroberflächenelemente Benutzer ansprechen und welche Benutzer dazu veranlassen, abzulegen.

In diesem Abschnitt wird beschrieben, wie [AEM](#developers)Entwicklerinnen und -Entwickler lernen können, wie Sie AEM Mobile-Apps mit Analytics-Tracking instrumentieren.

Abschließend lernen [AEM](#administrators)Administratoren Folgendes:

* Erstellen eines Cloud-Service zum Adobe von Mobile Services
* Erstellen einer Mobile Service-Konfiguration und Verknüpfen einer Report Suite
* Verknüpfen der Mobile-Service-Konfiguration mit einer Mobile App
* Anzeigen von Metriken über das AEM Apps Command Center
* Zuweisen der AMS-SDK-Konfiguration zu Ihrer Mobile App

## Für Entwickler: Integrieren von Analytics in Ihre App {#for-developers-integrate-analytics-into-your-app}

**Voraussetzung:** AEM-Administratoren müssen die Cloud-Konfiguration für Adobe Mobile Services konfigurieren [wie unten beschrieben](#amscloudserviceconfig).

Entwickler sind für das [Hinzufügen von Analysen zu einer AEM Mobile-App](/help/mobile/phonegap-add-analytics-to-apps.md) nach Bedarf verantwortlich, um zu verfolgen, Berichte zu erstellen und zu verstehen, wie Ihre Benutzerinnen und Benutzer mit den Inhalten Ihrer Mobile App interagieren, und um wichtige Lebenszyklusmetriken wie Launches, die Zeit in der App und die Absturzrate zu messen.

## Für Administratoren: Konfigurieren des Adobe Mobile Services-Cloud Service {#for-administrators-configure-the-adobe-mobile-services-cloud-service}

Um Adobe Mobile Services nutzen zu können, müssen Sie den AEM Adobe Mobile Services-Cloud Service mit Ihren Adobe Analytics-Kontoinformationen konfigurieren. Das Apps Command Center bietet eine Kachel **Metriken analysieren** in der Sie den Cloud-Service erstellen und mit Ihrer Mobile App verknüpfen können.

Konfigurieren Sie den Cloud Service für Ihre Mobile App. Klicken Sie dazu zunächst auf das Zahnradsymbol auf der Kachel Metriken analysieren .

![chlimage_1-125](assets/chlimage_1-125.png)

Durch Klicken auf das Zahnradsymbol in der Kachel Metriken analysieren wird das modale Dialogfeld „Mobile Services Analytics konfigurieren“ geöffnet. Wählen Sie Ihre Konfiguration aus der Dropdown-Liste „Mobile-Service-Konfiguration auswählen“. Wenn Sie eine Konfiguration erstellen müssen, klicken Sie auf die Schaltfläche Schraubenschlüssel .

Um einen Adobe Mobile Service-Cloud-Service zu erstellen, sind zwei Schritte erforderlich: die Verbindung zum Service und die Auswahl der Reporting-Suite, die der Konfiguration zugewiesen werden soll.

Klicken Sie zunächst auf die Schaltfläche &quot;+&quot; auf der Kachel Cloud Service verwalten im Dashboard.

![chlimage_1-126](assets/chlimage_1-126.png)

Nach dem Klicken auf die Schaltfläche &quot;**+**&quot; wird **Assistent &quot;Cloud Service**&quot; angezeigt.

![chlimage_1-127](assets/chlimage_1-127.png)

Wählen oder erstellen Sie eine Mobile-Service-Konfiguration, indem Sie die erforderlichen Felder wie unten dargestellt ausfüllen. Ihr AEM-Administrator benötigt diese Informationen, um die Verbindung zu Adobe Mobile Services erfolgreich herstellen zu können.

![chlimage_1-128](assets/chlimage_1-128.png)

Nachdem Sie die Mobile Services-Kontoeinstellungen abgeschlossen haben, werden Sie aufgefordert, eine App auszuwählen. Dadurch wird das Reporting zu Adobe Mobile Service-Analysen mit dieser Anwendung verbunden.

Wählen Sie den gewünschten Mobile Service aus und klicken Sie auf „Aktualisieren“, um die Mobile Service-Konfiguration zuzuweisen und das Dialogfeld zu schließen.

Nachdem Sie die Mobile-Service-Konfiguration mit der AEM Mobile-App verknüpft haben, beginnt die Kachel mit dem Abrufen der Metrikdaten und dem Erstellen von Berichten.

![chlimage_1-129](assets/chlimage_1-129.png)

### Adobe Mobile Services SDK-Konfigurationsdatei {#adobe-mobile-services-sdk-config-file}

Zu diesem Zeitpunkt ist Ihre Mobile App mit einem Cloud-Service verknüpft. Die Mobile App weiß jedoch noch nicht, wie die erfassten Mobile-Metriken zurück an Adobe Analytics übermittelt werden sollen. Um die Mobile App mit Adobe Analytics zu verkabeln, muss die Adobe Mobile Services SDK-Konfigurationsdatei zu Adobe Experience Manager hinzugefügt werden.

Klicken Sie auf der Kachel Metriken analysieren auf das Pfeilsymbol, um die Menüeinträge AMS-SDK-Konfiguration herunterladen/hochladen anzuzeigen.

![chlimage_1-130](assets/chlimage_1-130.png)

Der erste Schritt besteht darin, die SDK-Konfiguration von Adobe Mobile Services abzurufen. Klicken Sie auf „AMS SDK Config herunterladen“, um zur Adobe Mobile Services-Website weitergeleitet zu werden, von der Sie die Konfigurationsdatei herunterladen können. Nachdem Sie die Datei ADBMobileConfig.json erhalten haben, klicken Sie auf „AMS SDK Config hochladen“, um die Konfigurationsdatei in AEM hochzuladen.

![chlimage_1-131](assets/chlimage_1-131.png)

Klicken Sie auf die Schaltfläche &quot;Adobe-Mobile-Services-Anwendungskonfiguration hochladen“, suchen Sie die Datei „ADBMobileConfig.json“ und klicken Sie dann auf „Hochladen“.

Nachdem die Mobile App nun Zugriff auf die Datei ADBMobileConfig.json hat, weiß sie, wie sie zurück an Adobe Analytics kommunizieren und mit dem Reporting zu den wichtigen Wertmetriken beginnen kann, die zum Erfolg Ihrer Apps beitragen.

## Wie geht es weiter? {#what-s-next}

1. [Mein AEM Mobile-App-Erlebnis starten](/help/mobile/starting-aem-phonegap-app.md)
1. [Inhalt meiner App verwalten](/help/mobile/phonegap-manage-app-content.md)
1. [Meine Anwendung erstellen](/help/mobile/building-app-mobile-phonegap.md)
1. [Leistung meiner App mit Adobe Mobile Analytics verfolgen](/help/mobile/phonegap-intro-to-app-analytics.md)
1. [Bereitstellen eines personalisierten App-Erlebnisses mit Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md)
1. [Senden wichtiger Nachrichten an meine Benutzer](/help/mobile/phonegap-push-notifications.md)
