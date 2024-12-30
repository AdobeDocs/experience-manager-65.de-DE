---
title: Cloud-Konfiguration
description: Durch die Verknüpfung einer On-Demand-App mit einer Cloud-Konfiguration kann Adobe Experience Manager (AEM) direkt mit einem auf Anfrage gehosteten mobilen Projekt kommunizieren, indem ein bidirektionaler Link eingerichtet wird. Auf dieser Seite erfahren Sie mehr.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: 37428543-c310-4712-a4ec-1f482579fb4b
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 11%

---

# Cloud-Konfiguration{#cloud-configuration}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Durch die Verknüpfung einer On-Demand-App mit einer Cloud-Konfiguration kann Adobe Experience Manager (AEM) direkt mit einem auf Anfrage gehosteten mobilen Projekt kommunizieren, indem ein bidirektionaler Link eingerichtet wird. Durch die Verknüpfung Ihrer App mit einem Mobile-On-Demand-Projekt können Sie Inhalte wie Artikel, Banner und Sammlungen innerhalb von AEM erstellen, diese Inhalte aber auch Mobile On-Demand bereitstellen.

Von dort aus wird die Veröffentlichung, Vorschau und Verwaltung von Inhalten möglich. Sie können auch vorhandene Mobile-On-Demand-Inhalte in AEM importieren und Inhaltsbearbeitungen durchführen.

## Einrichten der Cloud-Konfiguration {#setting-up-cloud-configuration}

>[!CAUTION]
>
>Bevor Sie mit der Konfiguration der Cloud-Konfiguration für Ihre On-Demand-App beginnen, müssen Sie mit der Bereitstellung und Konfiguration des AEM Mobile On-demand Services-Clients in AEM Mobile vertraut sein.
>
>Weitere Informationen finden Sie [Einrichten von AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) im Abschnitt zur Verwaltung.

Um Mobile On-Demand-Cloud Service zu konfigurieren, klicken Sie im Dashboard Ihrer Mobile App auf das oberste Zahnrad oben rechts **der Kachel** Verbindung verwalten“.

Sie sollten mit dem App-Dashboard und den verfügbaren Kacheln vertraut sein. Weitere Informationen finden Sie unter {0](/help/mobile/mobile-apps-ondemand-application-dashboard.md) Dashboard der AEM Mobile-Anwendung .[

### Einrichten eines Links zur Cloud-Konfiguration {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>Stellen Sie sicher, dass Sie über eine On-Demand-Client- und -Cloud-Konfiguration verfügen.
>
>Weitere Informationen finden Sie [Einrichten von AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) im Abschnitt zur Verwaltung.

Die folgenden Schritte beschreiben das Einrichten eines Links zur Cloud-Konfiguration:

1. Wählen **Mobile** die Option **Apps** und dann Ihre Mobile On-Demand-App aus dem Katalog aus.
1. Klicken Sie auf der Kachel **Verbindung verwalten** auf das Zahnradsymbol.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Geben Sie die bereits vorhandene Konfiguration ein oder erstellen Sie eine, indem Sie **Konfigurationstitel**, **Geräte-ID** und **Geräte-Token** eingeben.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Sobald Ihre **Geräte-ID** und **Geräte-Token** verifiziert sind, wählen Sie Ihr On-Demand-Projekt aus der Liste aus.

   Klicken Sie auf **Absenden**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

   Die **Verbindung verwalten** zeigt Ihre Cloud-Konfiguration an.

   ![chlimage_1-68](assets/chlimage_1-68.png)

   >[!CAUTION]
   >
   >Wenn Sie beim Wechseln des Projekts im Dashboard versuchen, zu ändern, welchem Projekt diese App zugeordnet ist, erhalten Sie eine Warnung zu Problemen mit der Inhaltsintegrität, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-69](assets/chlimage_1-69.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Cloud-Konfiguration für Ihre App konfiguriert haben, finden Sie weitere Informationen in den folgenden Ressourcen zum Verwalten von Inhalten:

* [Artikel verwalten](/help/mobile/mobile-on-demand-managing-articles.md)
* [Verwalten von Bannern](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Rückgängigmachen der Veröffentlichung von Inhalten](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
