---
title: Cloud-Konfiguration
description: Durch die Verknüpfung einer On-Demand-App mit einer Cloud-Konfiguration kann Adobe Experience Manager (AEM) direkt mit einem von Mobile On-Demand gehosteten Projekt kommunizieren, indem eine Zwei-Wege-Verknüpfung erstellt wird. Auf dieser Seite erfahren Sie mehr.
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

Durch die Verknüpfung einer On-Demand-App mit einer Cloud-Konfiguration kann Adobe Experience Manager (AEM) direkt mit einem von Mobile On-Demand gehosteten Projekt kommunizieren, indem eine Zwei-Wege-Verknüpfung erstellt wird. Wenn Sie Ihre App mit einem On-Demand-Projekt für Mobilgeräte verknüpfen, können Sie Inhalte wie Artikel, Banner und Sammlungen in AEM erstellen, diese Inhalte aber auch für mobile On-Demand bereitstellen.

Von dort aus ist es möglich, Inhalte zu veröffentlichen, in der Vorschau anzuzeigen und zu verwalten. Sie können auch vorhandene mobile On-Demand-Inhalte in AEM importieren und die Inhaltsbearbeitung durchführen.

## Einrichten der Cloud-Konfiguration {#setting-up-cloud-configuration}

>[!CAUTION]
>
>Bevor Sie mit der Konfiguration der Cloud-Konfiguration für Ihre On-Demand-App beginnen, müssen Sie mit der Bereitstellung und Konfiguration des AEM Mobile On-demand Services-Clients für AEM Mobile vertraut sein.
>
>Weitere Informationen finden Sie unter [Einrichten von AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) im Abschnitt &quot;Verwaltung&quot;.

Klicken Sie zum Konfigurieren von Mobile On-Demand-Cloud Services oben rechts auf der Kachel **Verbindung verwalten** in Ihrem App-Dashboard auf das obere Zahnrad.

Sie sollten mit dem App-Dashboard und den verfügbaren Kacheln vertraut sein. Weitere Informationen finden Sie unter [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md) .

### Einrichten von Link zur Cloud-Konfiguration {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>Stellen Sie sicher, dass Sie über einen On-Demand-Client und eine Cloud-Konfiguration verfügen.
>
>Weitere Informationen finden Sie unter [Einrichten von AEM Mobile On-demand Services](/help/mobile/aem-mobile-setup.md) im Abschnitt &quot;Verwaltung&quot;.

Im Folgenden wird beschrieben, wie Sie einen Link zur Cloud-Konfiguration einrichten:

1. Wählen Sie unter **Mobil** die Option **Apps** und dann Ihre Mobile On-Demand-App aus dem Katalog.
1. Klicken Sie auf das Zahnradsymbol auf der Kachel **Verbindung verwalten** .

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Geben Sie die bereits vorhandene Konfiguration ein oder erstellen Sie eine, indem Sie den **Konfigurationstitel**, die **Geräte-ID** und das **Geräte-Token** eingeben.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Nachdem Sie Ihre **Geräte-ID** und Ihr **Geräte-Token** überprüft haben, wählen Sie Ihr On-Demand-Projekt aus der Liste aus.

   Klicken Sie auf **Absenden**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

   Die Kachel **Verbindung verwalten** enthält Ihre Cloud-Konfiguration.

   ![chlimage_1-68](assets/chlimage_1-68.png)

   >[!CAUTION]
   >
   >Wenn Sie beim Wechsel des Projekts im Dashboard versuchen, das Projekt zu ändern, mit dem diese App verknüpft ist, erhalten Sie eine Warnung zu Problemen mit der Inhaltsintegrität, wie in der folgenden Abbildung dargestellt:

   ![chlimage_1-69](assets/chlimage_1-69.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Cloud-Konfiguration für Ihre App konfiguriert haben, finden Sie weitere Informationen zum Verwalten von Inhalten in den folgenden Ressourcen:

* [Verwalten von Artikeln](/help/mobile/mobile-on-demand-managing-articles.md)
* [Banner verwalten](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Veröffentlichung des Inhalts rückgängig machen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
