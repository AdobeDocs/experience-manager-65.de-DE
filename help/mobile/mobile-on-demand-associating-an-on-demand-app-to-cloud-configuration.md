---
title: Cloud-Konfiguration
seo-title: Cloud-Konfiguration
description: Wenn Sie eine On-Demand-App einer Cloud-Konfiguration zuordnen, kann Adobe Experience Manager (AEM) direkt mit einem Mobile On-Demand-gehosteten Projekt kommunizieren, indem Sie eine Zwei-Wege-Verknüpfung erstellen. Auf dieser Seite erfahren Sie mehr.
seo-description: Wenn Sie eine On-Demand-App einer Cloud-Konfiguration zuordnen, kann Adobe Experience Manager (AEM) direkt mit einem Mobile On-Demand-gehosteten Projekt kommunizieren, indem Sie eine Zwei-Wege-Verknüpfung erstellen. Auf dieser Seite erfahren Sie mehr.
uuid: f377f2af-864b-43df-9d42-4a5fd6cd70d5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: d0d29b99-53d4-4b0d-947b-39d91b381de7
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Cloud-Konfiguration{#cloud-configuration}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Wenn Sie eine On-Demand-App einer Cloud-Konfiguration zuordnen, kann Adobe Experience Manager (AEM) direkt mit einem Mobile On-Demand-gehosteten Projekt kommunizieren, indem Sie eine Zwei-Wege-Verknüpfung erstellen. Wenn Sie Ihre App mit einem Mobile On-Demand-Projekt verknüpfen, können Sie Inhalte wie Artikel, Banner und Sammlungen in AEM erstellen, diese Inhalte aber auch für Mobile On-Demand bereitstellen.

Von dort aus können Inhalte veröffentlicht, in der Vorschau angezeigt und verwaltet werden. Sie können auch vorhandene Mobile On-Demand-Inhalte in AEM importieren und die Inhaltsbearbeitung durchführen.

## Einrichten der Cloud-Konfiguration {#setting-up-cloud-configuration}

>[!CAUTION]
>
>Bevor Sie mit der Konfiguration der Cloud für Ihre On-Demand-App beginnen, müssen Sie mit der Bereitstellung und Konfiguration von AEM Mobile On-Demand Services Client vertraut sein.
>
>Weitere Informationen finden Sie unter AEM Mobile-On-Demand-Dienste [einrichten](/help/mobile/aem-mobile-setup.md) im Abschnitt Administration.

Um Mobile On-Demand Cloud-Dienste zu konfigurieren, klicken Sie auf das obere Zahnrad rechts oben in der Kachel &quot;Verbindung **** verwalten&quot;im App-Dashboard.

Sie sollten mit dem App-Dashboard und den verfügbaren Kacheln vertraut sein. Weitere Informationen finden Sie unter [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md) .

### Link zur Cloud-Konfiguration einrichten {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>Vergewissern Sie sich, dass Sie über eine On-Demand-Client- und Cloud-Konfiguration verfügen.
>
>Weitere Informationen finden Sie unter AEM Mobile-On-Demand-Dienste [einrichten](/help/mobile/aem-mobile-setup.md) im Abschnitt Administration.

Die folgenden Schritte beschreiben das Einrichten von Link zur Cloud-Konfiguration:

1. Wählen Sie in **Mobile**&quot; **Apps** &quot;und dann Ihre Mobile On-Demand-App aus dem Katalog.
1. Klicken Sie auf das Zahnradsymbol auf der Kachel Verbindung **verwalten** .

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Geben Sie die bereits vorhandene Konfiguration ein oder erstellen Sie eine neue Konfiguration, indem Sie den **Konfigurationstitel**, die **Geräte-ID** und das **Gerätetoken** eingeben.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Wählen Sie nach Überprüfung der **Geräte-ID** und des **Gerätetokens** Ihr On-Demand-Projekt in der Liste aus.

   Klicken Sie auf **Übermitteln**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

   Die Kachel **&quot;Verbindung** verwalten&quot;zeigt Ihre Cloud-Konfiguration an.

   ![chlimage_1-68](assets/chlimage_1-68.png)

   >[!CAUTION]
   >
   >Wenn Sie versuchen, das Projekt zu ändern, mit dem diese App verknüpft ist, während Sie das Projekt im Dashboard wechseln, erhalten Sie eine Warnung zu Problemen mit der Inhaltsintegrität, wie in der folgenden Abbildung gezeigt:

   ![chlimage_1-69](assets/chlimage_1-69.png)

### Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Cloud-Konfiguration für Ihre App konfiguriert haben, finden Sie weitere Informationen zum Verwalten von Inhalten:

* [Verwalten von Artikeln](/help/mobile/mobile-on-demand-managing-articles.md)
* [Banner verwalten](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verwalten von Sammlungen](/help/mobile/mobile-on-demand-managing-collections.md)
* [Hochladen freigegebener Ressourcen](/help/mobile/mobile-on-demand-shared-resources.md)
* [Veröffentlichen/Rückgängigmachen der Veröffentlichung des Inhalts](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Vorschau mit Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
