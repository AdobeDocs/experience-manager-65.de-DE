---
title: Einstellen des Referrer-Filters auf "Leere erlauben"
seo-title: Setting Your Referrer Filter to Allow Empty
description: Auf dieser Seite erfahren Sie mehr über den Referrer-Filter. Damit der AEM Mobile Application Viewer Apps in Ihrer Autoreninstanz anzeigen kann, müssen Sie Ihren HTML-Referrer-Filter auf "Leer zulassen"einstellen.
seo-description: Follow this page to learn about Referrer Filter. In order to allow the AEM Mobile Application Viewer to view apps on your Author instance, you'll need to set your HTML referrer filter to 'allow empty'.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 2f02f541-92db-469b-bf23-ec64d2e282ff
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---

# Einstellen des Referrer-Filters auf &quot;Leere erlauben&quot;{#setting-your-referrer-filter-to-allow-empty}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Damit der AEM Mobile Application Viewer Apps in Ihrer Autoreninstanz anzeigen kann, müssen Sie Ihren HTML-Referrer-Filter auf &quot;Leer zulassen&quot;einstellen.

Wenn Sie nicht beabsichtigen, mit dem Anwendungs-Viewer Anwendungen in Entwicklungs- und Staging-Status zu überprüfen, müssen Sie die Standardeinstellung des Referrer-Filters nicht ändern.

Navigieren Sie in der laufenden Autoreninstanz von AEM zu: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) und suchen Sie nach &quot;Apache Sling Referrer Filter&quot;. Klicken Sie auf , um den Referrer-Filter zu bearbeiten, und aktivieren Sie das Kontrollkästchen &quot;Leere erlauben&quot;(siehe Abbildung unten). Klicken Sie anschließend auf die Schaltfläche &quot;Speichern&quot;und schließen Sie die Browser-Seite.

![Einstellungen für Referrer-Filter](assets/chlimage_1-106.png)
