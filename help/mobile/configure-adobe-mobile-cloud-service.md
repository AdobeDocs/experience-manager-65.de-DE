---
title: Konfigurieren des Adobe Mobile Services-Cloud Service
description: Auf dieser Seite können Sie Ihren Adobe Mobile Services-Cloud Service konfigurieren.
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

# Konfigurieren des Adobe Mobile Services-Cloud Service {#configure-your-adobe-mobile-services-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Kachel **Mobile-Metriken** im Befehlscenter bietet Echtzeitanalysen für Ihre Mobile App.

Die [Adobe Mobile Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) SDK wird über ein PhoneGap-Plug-in zur Verfügung gestellt. Metriken werden erfasst und auf dem Gerät zwischengespeichert, bis das Gerät verbunden ist. Zu diesem Zeitpunkt werden die Daten zur Berichterstellung und Analyse an die Adobe Mobile Services Cloud weitergeleitet.

Adobe Mobile Analytics SDK bietet Folgendes:

1. **Datenerfassung für mobile Kanäle** - Erfassen Sie umfassende Daten für Ihre mobilen Websites und Apps auf allen wichtigen Betriebssystemen.
1. **Mobile Interaktionsanalyse** - Verstehen Sie die Benutzerinteraktion in Ihrer Mobile App, Website oder in Ihrem Video, einschließlich der Häufigkeit, mit der Verbraucher den Kanal starten, ob sie darüber Einkäufe tätigen und mehr.
1. **Mobile-App-Dashboards und -Berichte** - Erhalten Sie Nutzungsberichte, die Lebenszyklusmetriken für Ihre Apps und App-Store-Metriken enthalten - sehen Sie Trends für Benutzer, Launches, durchschnittliche Sitzungsdauer, Aufbewahrungsdauer und Abstürze.
1. **Mobile-Kampagnenanalyse** - Quantifizieren Sie die Effektivität mobilgerätespezifischer Kampagnen wie SMS, mobile Suchanzeigen, mobile Display-Anzeigen und QR-Codes.
1. **Geolokalisierungsanalyse** - Ermitteln Sie anhand des GPS-Standorts oder der Points of Interest, wo Ihre App-Benutzer starten und mit Ihren mobilen Erlebnissen interagieren.
1. **Pfadanalyse** Ermitteln Sie, wie Benutzer durch Ihre App navigieren, um festzustellen, welche Bildschirme und Benutzeroberflächenelemente Benutzer ansprechen und welche Benutzer dazu veranlassen, abzulegen.

>[!CAUTION]
>
>Die **Metriken analysieren** wird nur dann im Dashboard angezeigt, wenn Sie Cloud-Services konfiguriert haben.

![chlimage_1-22](assets/chlimage_1-22.png)

AEM Command Center-Metriken-Kachel

## Konfigurieren des Cloud Service {#configuring-the-cloud-service}

Um Adobe Mobile Services Analytics nutzen zu können, müssen Sie den AEM Mobile Analytics Cloud-Service mit Ihren Adobe Analytics-Kontoinformationen konfigurieren.

1. Klicken Sie auf das Symbol oben rechts, um die Cloud Service über die Kachel **Cloud Service verwalten** im App-Dashboard hinzuzufügen oder zu bearbeiten.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. Der **&quot;Cloud Service hinzufügen oder bearbeiten** wird angezeigt. Wählen Sie **Adobe Mobile Services aus** klicken Sie auf **Weiter**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Wählen Sie eine vorhandene Konfiguration aus dem Menü **Mobile Services** oder wählen Sie **Konfiguration erstellen**, um eine zu erstellen.

   Geben Sie für eine neue Konfiguration die **Eigenschaften von Mobile Services** ein und klicken Sie auf **Überprüfen.**

   ![chlimage_1-25](assets/chlimage_1-25.png)

   Wenn die Anmeldeinformationen überprüft werden, ändert sich die Schaltfläche **Überprüfen** in **Verifiziert**. Sie können eine Mobile-Service-App unter **Wählen Sie einen Mobile-App-Service** auswählen.

   Klicken Sie **Senden**, um Ihre Konfiguration einzurichten.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Nachdem Sie eine Cloud-Konfiguration eingerichtet haben, können Sie diese in Ihrem Dashboard anzeigen.

   ![chlimage_1-27](assets/chlimage_1-27.png)

   >[!NOTE]
   >
   >Nachdem Sie Ihre Cloud-Konfiguration eingerichtet haben, können Sie die Kachel **Metriken analysieren** in Ihrem App-Dashboard anzeigen.

   ![chlimage_1-28](assets/chlimage_1-28.png)
