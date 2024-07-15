---
title: Adobe Mobile Services Cloud Service konfigurieren
description: Auf dieser Seite erfahren Sie, wie Sie Ihren Adobe Mobile Services-Cloud Service konfigurieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
legacypath: /content/docs/en/aem/6-1/develop/mobile-apps/apps/managing-aem-mobile-apps/configure-your-adobe-phonegap-build-cloud-service1
exl-id: 209c36f9-1a4b-4eea-8dde-22e0fc9718c1
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 7%

---

# Adobe Mobile Services Cloud Service konfigurieren {#configure-your-adobe-mobile-services-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Kachel &quot;**Mobile Metriken&quot;** im Befehlszentrum bietet Echtzeitanalysen für Ihre Mobile App.

Das SDK [Adobe Mobile Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) wird über ein PhoneGap-Plug-in bereitgestellt. Metriken werden erfasst und auf dem Gerät zwischengespeichert, bis das Gerät verbunden ist. Zu diesem Zeitpunkt werden die Daten zur Berichterstellung und Analyse an die Adobe Mobile Services Cloud gesendet.

Adobe Mobile Analytics SDK bietet Folgendes:

1. **Datenerfassung für mobile Kanäle** - Erfassen Sie umfassende Daten für Ihre mobilen Websites und Apps auf allen wichtigen Betriebssystemen.
1. **Analyse der mobilen Interaktion** - Verstehen Sie die Benutzerinteraktion innerhalb Ihrer mobilen App, Website oder Videos, einschließlich der Häufigkeit, mit der Verbraucher den Kanal starten, ob sie Käufe darüber tätigen und mehr.
1. **Mobile App-Dashboards und -Berichte** - Rufen Sie Nutzungsberichte ab, die Lebenszyklusmetriken für Ihre Apps und App Store-Metriken enthalten - siehe Trends für Benutzer, Starts, durchschnittliche Sitzungslänge, Aufbewahrungsdauer und Abstürze.
1. **Analyse mobiler Kampagnen** - Quantifizieren Sie die Effektivität mobiler Kampagnen wie SMS, mobile Suchanzeigen, mobiler Display-Anzeigen und QR-Codes.
1. **Geolocation analysis** - Finden Sie, wo Ihre App-Benutzer Ihre mobilen Erlebnisse starten und damit interagieren, nach GPS-Position oder Zielpunkten.
1. **Pfadanalyse** - Erfahren Sie, wie Benutzer durch Ihre App navigieren, um zu ermitteln, welche Bildschirme und Benutzeroberflächenelemente Benutzer anregen und welche dazu führen, dass Benutzer abbrechen.

>[!CAUTION]
>
>Die Kachel **Metriken analysieren** wird nur dann im Dashboard angezeigt, wenn Sie Cloud-Services konfiguriert haben.

![chlimage_1-22](assets/chlimage_1-22.png)

Kachel AEM Befehlszeilenmetriken

## Konfigurieren des Cloud Service {#configuring-the-cloud-service}

Um Adobe Mobile Services Analytics nutzen zu können, müssen Sie den AEM Mobile Analytics Cloud-Dienst mit Ihren Adobe Analytics-Kontoinformationen konfigurieren.

1. Klicken Sie auf das Symbol oben rechts, um die Cloud Service über die Kachel **Cloud Service verwalten** im App-Dashboard hinzuzufügen oder zu bearbeiten.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. Der Bildschirm **Cloud Service hinzufügen oder bearbeiten** wird angezeigt. Wählen Sie **Adobe Mobile Services** und klicken Sie auf **Weiter**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Wählen Sie eine vorhandene Konfiguration aus den **Mobile Services** oder wählen Sie **Konfiguration erstellen** , um eine Konfiguration zu erstellen.

   Geben Sie für eine neue Konfiguration die **Eigenschaften der Mobile Services** ein und klicken Sie auf **Überprüfen.**

   ![chlimage_1-25](assets/chlimage_1-25.png)

   Wenn die Anmeldeinformationen geprüft werden, ändert sich die Schaltfläche **Verify** in **Verified**. Sie können eine Mobile-Service-App unter **Wählen Sie einen Mobile-App-Dienst aus**.

   Klicken Sie zum Einrichten Ihrer Konfiguration auf **Senden** .

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Nachdem Sie eine Cloud-Konfiguration eingerichtet haben, können Sie dieselbe Ansicht in Ihrem Dashboard anzeigen.

   ![chlimage_1-27](assets/chlimage_1-27.png)

   >[!NOTE]
   >
   >Nachdem Sie Ihre Cloud-Konfiguration eingerichtet haben, können Sie die Kachel **Metriken analysieren** in Ihrem App-Dashboard anzeigen.

   ![chlimage_1-28](assets/chlimage_1-28.png)
