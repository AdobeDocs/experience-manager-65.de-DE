---
title: Festlegen des Referrer-Filters auf „Leer zulassen“
description: Informationen zum Referrer-Filter. Damit der Adobe Experience Manager (AEM) Mobile App Viewer Apps auf Ihrer Autoreninstanz anzeigen kann, müssen Sie Ihren HTML-Referrer-Filter auf „Leer zulassen“ einstellen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: 2f02f541-92db-469b-bf23-ec64d2e282ff
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Festlegen des Referrer-Filters auf „Leer zulassen“{#setting-your-referrer-filter-to-allow-empty}

{{ue-over-mobile}}

Damit der Adobe Experience Manager (AEM) Mobile App Viewer Apps auf Ihrer Autoreninstanz anzeigen kann, müssen Sie Ihren HTML-Referrer-Filter auf „Leer zulassen“ einstellen.

Wenn Sie nicht beabsichtigen, den Anwendungs-Viewer zur Überprüfung von Anwendungen im Entwicklungs- und Staging-Status zu verwenden, müssen Sie die Standardeinstellung des Referrer-Filters nicht ändern.

Navigieren Sie in Ihrer laufenden AEM-Autoreninstanz zu: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) und suchen Sie nach „Apache Sling Referrer Filter“. Klicken Sie, um den Referrer-Filter zu bearbeiten, und aktivieren Sie das Kontrollkästchen „Leer zulassen“ (siehe Abbildung unten). Klicken Sie anschließend auf die Schaltfläche Speichern und schließen Sie die Browser-Seite.

![Einstellungen des Referrer-Filters](assets/chlimage_1-106.png)
