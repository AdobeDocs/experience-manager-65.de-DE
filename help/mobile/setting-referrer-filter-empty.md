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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 3%
---
# Festlegen des Referrer-Filters auf „Leer zulassen“{#setting-your-referrer-filter-to-allow-empty}

{{ue-over-mobile}}

Damit der Adobe Experience Manager (AEM) Mobile App Viewer Apps auf Ihrer Autoreninstanz anzeigen kann, müssen Sie Ihren HTML-Referrer-Filter auf „Leer zulassen“ einstellen.

Wenn Sie nicht beabsichtigen, den Anwendungs-Viewer zur Überprüfung von Anwendungen im Entwicklungs- und Staging-Status zu verwenden, müssen Sie die Standardeinstellung des Referrer-Filters nicht ändern.

Navigieren Sie in Ihrer aktuellen AEM-Autoreninstanz zu: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) und suchen Sie nach „Apache Sling Referrer Filter“. Klicken Sie, um den Referrer-Filter zu bearbeiten, und aktivieren Sie das Kontrollkästchen „Leer zulassen“ (siehe Abbildung unten). Klicken Sie anschließend auf die Schaltfläche Speichern und schließen Sie die Browser-Seite.

![Einstellungen des Referrer-Filters](assets/chlimage_1-106.png)
