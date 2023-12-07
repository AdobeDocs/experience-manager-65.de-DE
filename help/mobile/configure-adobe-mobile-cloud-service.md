---
title: Adobe Mobile Services Cloud Service konfigurieren
description: Auf dieser Seite erfahren Sie, wie Sie Ihren Adobe Mobile Services-Cloud Service konfigurieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
legacypath: /content/docs/en/aem/6-1/develop/mobile-apps/apps/managing-aem-mobile-apps/configure-your-adobe-phonegap-build-cloud-service1
exl-id: 209c36f9-1a4b-4eea-8dde-22e0fc9718c1
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 3%

---

# Adobe Mobile Services Cloud Service konfigurieren {#configure-your-adobe-mobile-services-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die **Mobilmetrikbereich** im Befehlszentrum bietet Echtzeitanalysen für Ihre Mobile App.

Die [Adobe Mobile Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) SDK wird über ein PhoneGap-Plug-in bereitgestellt. Metriken werden erfasst und auf dem Gerät zwischengespeichert, bis das Gerät verbunden ist. Zu diesem Zeitpunkt werden die Daten zur Berichterstellung und Analyse an die Adobe Mobile Services Cloud gesendet.

Adobe Mobile Analytics SDK bietet Folgendes:

1. **Datenerfassung für mobile Kanäle** - Erfassen Sie umfassende Daten für Ihre mobilen Websites und Apps auf allen gängigen Betriebssystemen.
1. **Mobile Interaktionsanalyse** - Erfahren Sie mehr über die Benutzerinteraktion innerhalb Ihrer mobilen App, Website oder Videos, einschließlich der Häufigkeit, mit der Verbraucher den Kanal starten, ob sie Käufe darüber tätigen und mehr.
1. **Dashboards und Berichte für mobile Apps** - Rufen Sie Nutzungsberichte ab, die Lebenszyklusmetriken für Ihre Apps und App Store-Metriken enthalten - siehe Trends für Benutzer, Starts, durchschnittliche Sitzungslänge, Aufbewahrungsdauer und Abstürze.
1. **Analyse mobiler Kampagnen** - Quantifizieren Sie die Effektivität mobiler Kampagnen wie SMS, mobile Suchanzeigen, mobile Display-Anzeigen und QR-Codes.
1. **Geolocation-Analyse** - Ermitteln Sie, wo Ihre App-Benutzer Ihre mobilen Erlebnisse starten und mit ihnen interagieren, nach GPS-Standort oder Zielpunkten.
1. **Pfadanalyse** - Erfahren Sie, wie Benutzer durch Ihre App navigieren, um zu ermitteln, welche Bildschirme und Benutzeroberflächenelemente Benutzer anregen und welche dazu führen, dass Benutzer abbrechen.

>[!CAUTION]
>
>Die **Metriken analysieren** Die Kachel wird nur dann im Dashboard angezeigt, wenn Sie Cloud Services konfiguriert haben.

![chlimage_1-22](assets/chlimage_1-22.png)

Kachel AEM Befehlszeilenmetriken

## Konfigurieren des Cloud Service {#configuring-the-cloud-service}

Um Adobe Mobile Services Analytics nutzen zu können, müssen Sie den AEM Mobile Analytics Cloud-Dienst mit Ihren Adobe Analytics-Kontoinformationen konfigurieren.

1. Klicken Sie auf das Symbol oben rechts, um die Cloud Service über das **Cloud Service verwalten** -Kachel im App-Dashboard angezeigt.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. Die **Cloud Service hinzufügen oder bearbeiten** angezeigt. Auswählen **Adobe Mobile Services** und klicken **Nächste**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Wählen Sie eine vorhandene Konfiguration aus dem **Mobile Services** oder wählen **Konfiguration erstellen** , um eine zu erstellen.

   Geben Sie für eine neue Konfiguration die **Eigenschaften von Mobile Services** und klicken **Überprüfen.**

   ![chlimage_1-25](assets/chlimage_1-25.png)

   Wenn die Anmeldeinformationen geprüft werden, wird die **Überprüfen** Schaltflächenänderungen in **Verifiziert**. Sie können eine Mobile-Service-App unter **Auswählen eines Mobile-App-Dienstes**.

   Klicks **Einsenden** zum Einrichten der Konfiguration.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Nachdem Sie eine Cloud-Konfiguration eingerichtet haben, können Sie dieselbe Ansicht in Ihrem Dashboard anzeigen.

   ![chlimage_1-27](assets/chlimage_1-27.png)

   >[!NOTE]
   >
   >Nachdem Sie Ihre Cloud-Konfiguration eingerichtet haben, können Sie die **Metriken analysieren** Kacheln Sie in Ihrem App-Dashboard.

   ![chlimage_1-28](assets/chlimage_1-28.png)
