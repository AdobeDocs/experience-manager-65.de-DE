---
title: Konfigurieren des Adobe Mobile Services Cloud-Dienstes
seo-title: Konfigurieren des Adobe Mobile Services Cloud-Dienstes
description: Folgen Sie dieser Seite, um Ihren Adobe Mobile Services Cloud Service zu konfigurieren.
seo-description: Folgen Sie dieser Seite, um Ihren Adobe Mobile Services Cloud Service zu konfigurieren.
uuid: 21fe5b24-dc4d-4ee4-9e7f-ed4783baf276
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 962e9e98-a303-435b-a938-31319282e022
legacypath: /content/docs/en/aem/6-1/develop/mobile-apps/apps/managing-aem-mobile-apps/configure-your-adobe-phonegap-build-cloud-service1
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 25%

---


# Konfigurieren des Adobe Mobile Services Cloud-Dienstes {#configure-your-adobe-mobile-services-cloud-service}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Die Kachel **Mobile Metriken** im Befehlszentrum bietet Echtzeitanalysen für Ihre Mobilanwendung.

Das [Adobe Mobile Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html)-SDK wird als PhoneGap-Plug-in zur Verfügung gestellt. Metriken werden erfasst und auf dem Gerät zwischengespeichert, bis das Gerät angeschlossen ist. Zu diesem Zeitpunkt werden die Daten an die Adobe Mobile Services Cloud für Berichte und Analyse gesendet.

Das Adobe Mobile Analytics-SDK bietet Folgendes:

1. **Datenerfassung für mobile Kanäle** - Erfassen Sie umfassende Daten zu Ihren mobilen Websites und Apps auf allen wichtigen Betriebssystemen.
1. **Analyse**  zur Interaktion mit Mobilgeräten: Verstehen Sie die Interaktion der Benutzer mit Ihrer mobilen App, Website oder Ihrem Video, einschließlich der Häufigkeit, mit der der Kanal gestartet wird, der Anzahl der getätigten Käufe und mehr.
1. **Mobile App-Dashboard und -Berichte**  - Nutzungsberichte mit Lebenszyklusmetriken für Ihre Apps- und App Store-Metriken abrufen — Zeigen Sie Trends für Benutzer, Starts, durchschnittliche Sitzungslänge, Aufbewahrungslänge und Abstürze an.
1. **Analyse**  mobiler Kampagnen - Quantifizieren Sie die Effektivität mobiler Kampagnen wie SMS, Mobil-Suchwerbung, Display-Anzeigen und QR-Codes.
1. **Geolocation-Analyse** : Finden Sie heraus, wo Ihre App-Benutzer Ihre mobilen Erlebnisse starten und mit ihnen interagieren, nach GPS-Position oder Zielpunkten.
1. **Pfade**  - Erfahren Sie, wie Benutzer durch Ihre App navigieren, um festzustellen, welche Bildschirme und UI-Elemente Benutzer ansprechen und welche die Benutzer abbrechen.

>[!CAUTION]
>
>Die Kachel **Metriken analysieren** wird im Dashboard nur angezeigt, wenn Sie Cloud-Dienste konfiguriert haben.

![chlimage_1-22](assets/chlimage_1-22.png)

Kachel „AEM-Befehlszeilenmetriken“

## Konfigurieren des Cloud-Dienstes {#configuring-the-cloud-service}

Um Adobe Mobile Services Analytics nutzen zu können, müssen Sie den AEM Mobile Analytics Cloud-Dienst mit Ihren Adobe Analytics-Kontoinformationen konfigurieren.

1. Klicken Sie auf das Symbol oben rechts, um die Cloud Services aus der Kachel **Cloud Services verwalten** aus dem App-Dashboard hinzuzufügen oder zu bearbeiten.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. Der Bildschirm **Hinzufügen oder Cloud Services bearbeiten** wird angezeigt. Wählen Sie **Adobe Mobile Services** und klicken Sie auf **Weiter**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Wählen Sie unter **Mobile Services** eine vorhandene Konfiguration aus oder wählen Sie **Konfiguration erstellen**, um eine neue zu erstellen.

   Geben Sie für eine neue Konfiguration die Eigenschaften **Mobile Services ein und klicken Sie auf** Überprüfen.****

   ![chlimage_1-25](assets/chlimage_1-25.png)

   Wenn die Anmeldeinformationen überprüft wurden, wird die Schaltfläche **Überprüfen** in **Geprüft** geändert. Sie können eine Mobile Service-App aus **Wählen Sie einen Mobile App Service**.

   Klicken Sie auf **Senden**, um Ihre Konfiguration einzurichten.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Nachdem Sie eine Cloud-Konfiguration eingerichtet haben, können Sie die gleiche Ansicht in Ihrem Dashboard vornehmen.

   ![chlimage_1-27](assets/chlimage_1-27.png)

   >[!NOTE]
   >
   >Nachdem Sie die Cloud-Konfiguration eingerichtet haben, können Sie die Kachel **Metriken analysieren** in Ihrem App-Dashboard Ansicht haben.

   ![chlimage_1-28](assets/chlimage_1-28.png)

