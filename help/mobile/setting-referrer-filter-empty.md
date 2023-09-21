---
title: Einstellen des Referrer-Filters auf "Leere erlauben"
description: Erfahren Sie mehr über den Referrer-Filter. Damit der Adobe Experience Manager (AEM) Mobile Application Viewer Apps in Ihrer Autoreninstanz anzeigen kann, müssen Sie den HTML-Referrer-Filter auf "Leer zulassen"einstellen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: 2f02f541-92db-469b-bf23-ec64d2e282ff
source-git-commit: 6799f1d371734b69c547f3c0c68e1e633aa63229
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Einstellen des Referrer-Filters auf &quot;Leere erlauben&quot;{#setting-your-referrer-filter-to-allow-empty}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

Damit der Adobe Experience Manager (AEM) Mobile Application Viewer Apps in Ihrer Autoreninstanz anzeigen kann, müssen Sie den HTML-Referrer-Filter auf &quot;Leer zulassen&quot;einstellen.

Wenn Sie nicht beabsichtigen, mit dem Anwendungs-Viewer Anwendungen in Entwicklungs- und Staging-Status zu überprüfen, müssen Sie die Standardeinstellung des Referrer-Filters nicht ändern.

Navigieren Sie in der laufenden Autoreninstanz von AEM zu: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) und suchen Sie nach &quot;Apache Sling Referrer Filter&quot;. Klicken Sie auf , um den Referrer-Filter zu bearbeiten, und aktivieren Sie das Kontrollkästchen &quot;Leere erlauben&quot;(siehe Abbildung unten). Klicken Sie anschließend auf die Schaltfläche &quot;Speichern&quot;und schließen Sie die Browser-Seite.

![Einstellungen für Referrer-Filter](assets/chlimage_1-106.png)
