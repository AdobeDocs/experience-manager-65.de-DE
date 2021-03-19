---
title: E-Commerce-Übersicht
seo-title: E-Commerce-Übersicht
description: Der generische AEM-E-Commerce ist als Teil der Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.
seo-description: Der generische AEM-E-Commerce ist als Teil der Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
docset: aem65
feature: Commerce Integration Framework
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 56%

---


# E-Commerce-Übersicht{#ecommerce-overview}

Der generische AEM-E-Commerce ist als Teil einer Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.

Adobe bietet zwei Versionen des Commerce-Integrations-Frameworks:

|  | CIF On-Premise | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Unterstützte AEM-Versionen | AEM On-Premise oder AMS 6.x | AEM AMS 6.4 und 6.5 |
| Back-End | - AEM, Java <br> - Monolithische Integration, vorgefertigte Zuordnung (Vorlage)<br> - JCR-Repository | - Magento <br>- Java und JavaScript <br>- Keine Commerce-Daten im JCR-Repository gespeichert |
| Front-End | Server-seitig wiedergegebene AEM-Seiten | Gemischte Seitenanwendung (hybrides Rendering) |
| Produktkatalog | - Product Importer, Editor, Zwischenspeicherung in AEM <br>- Regelmäßige Kataloge mit AEM- oder Proxy-Seiten | - Kein Produktimport <br>- Allgemeine Vorlagen <br>- On-Demand-Daten über Connector |
| Skalierbarkeit | - Kann bis zu wenigen Millionen Produkte unterstützen (abhängig vom Anwendungsfall) <br> - Zwischenspeicherung unter Dispatcher | - Keine Volumenbegrenzung <br>- Zwischenspeicherung auf Dispatcher oder CDN |
| Standardisiertes Datenmodell | Nein | Ja, Magento GraphQL-Schema |
| Verfügbarkeit | Ja:<br> - SAP-Commerce Cloud (Erweiterung aktualisiert, um AEM 6.4 und Hybris 5 zu unterstützen (Standard) und Kompatibilität mit Hybris 4 <br>- Salesforce-Commerce Cloud (Connector offen für Unterstützung von AEM 6.4) | Ja, über Open Source von GitHub. <br> Magento Commerce (unterstützt Magento 2.3.2 (standardmäßig) und ist mit Magento 2.3.1 kompatibel). |
| Wann ist sie einzusetzen? | Eingeschränkte Anwendungsfälle: In Szenarien, in denen kleine statische Kataloge möglicherweise importiert werden müssen | Bevorzugte Lösung in den meisten Anwendungsfällen |


## Bereitstellen weiterer Implementierungen {#deploying-other-implementations}

AEM und Magento finden Sie unter [AEM und Magento-Integration](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md) mithilfe des [Commerce-Integrationsrahmens](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html).

>[!NOTE]
>
>Weitere Informationen zu den Konzepten und zur Verwaltung von eCommerce-Implementierungen finden Sie unter [Verwaltung von eCommerce](/help/sites-administering/ecommerce.md).
>
>Informationen zum Erweitern der eCommerce-Funktionen finden Sie unter [Entwickeln von eCommerce](/help/sites-developing/ecommerce.md).

