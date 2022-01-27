---
title: E-Commerce-Übersicht
seo-title: eCommerce Overview
description: Der generische AEM-E-Commerce ist als Teil der Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.
seo-description: AEM generic eCommerce is available as part of the standard installation and provides you with the full functionality of the eCommerce framework.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
docset: aem65
feature: Commerce Integration Framework
exl-id: 3567bd28-73aa-401a-8aa9-a62a99d2a613
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 45%

---

# eCommerce  Übersicht{#ecommerce-overview}

Der generische AEM-E-Commerce ist als Teil einer Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.

Adobe bietet zwei Versionen des Commerce-Integrations-Frameworks:

|  | CIF On-Premise | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Unterstützte AEM-Versionen | AEM On-Premise oder AMS 6.x | AEM AMS 6.4 und 6.5 |
| Back-End | - AEM, Java <br> - Monolithische Integration, Pre-Build-Zuordnung (Vorlage)<br> - JCR-Repository | - Adobe Commerce <br>- Java und JavaScript <br>- Keine Commerce-Daten im JCR-Repository gespeichert |
| Front-End | Server-seitig wiedergegebene AEM-Seiten | Gemischte Seitenanwendung (hybrides Rendering) |
| Produktkatalog | - Produkt-Importer, Editor, Zwischenspeicherung in AEM <br>- Regelmäßige Kataloge mit AEM- oder Proxy-Seiten | - Keine Einfuhr von Erzeugnissen <br>- Allgemeine Vorlagen <br>- On-Demand-Daten über Connector |
| Skalierbarkeit | - Kann bis zu einigen Millionen Produkte unterstützen (abhängig vom Anwendungsfall) <br> - Zwischenspeicherung im Dispatcher | - Keine Volumenbegrenzung <br>- Caching im Dispatcher oder CDN |
| Standardisiertes Datenmodell | Nein | Ja, Adobe Commerce GraphQL-Schema |
| Verfügbarkeit | Ja:<br> - SAP-Commerce Cloud (Erweiterung aktualisiert, um AEM 6.4 und Hybris 5 zu unterstützen (Standard) und Kompatibilität mit Hybris 4 sicherzustellen <br>- Salesforce-Commerce Cloud (Connector Open-Source-Unterstützung für AEM 6.4) | Ja, über Open Source von GitHub. <br> Adobe Commerce (unterstützt 2.3.2 (Standard) und kompatibel mit 2.3.1). |
| Wann ist sie einzusetzen? | Eingeschränkte Anwendungsfälle: In Szenarien, in denen kleine statische Kataloge importiert werden müssen | Bevorzugte Lösung in den meisten Anwendungsfällen |


## Bereitstellen weiterer Implementierungen {#deploying-other-implementations}

Informationen zu AEM und Adobe Commerce finden Sie unter [Integration von AEM und Adobe Commerce](/help/commerce/cif/integrating/magento.md) mithilfe der [Commerce Integration Framework](/help/commerce/cif/introduction.md).

>[!NOTE]
>
>Weitere Informationen zu den Konzepten und zur Verwaltung von eCommerce-Implementierungen finden Sie unter [Verwaltung von eCommerce](/help/commerce/cif-classic/administering/ecommerce.md).
>
>Informationen zur Erweiterung der eCommerce-Funktionen finden Sie unter [Entwicklung von eCommerce](/help/commerce/cif-classic/developing/ecommerce.md).
