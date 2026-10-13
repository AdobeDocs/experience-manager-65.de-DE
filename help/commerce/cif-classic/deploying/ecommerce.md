---
title: E-Commerce-Übersicht
description: Der generische AEM-E-Commerce ist als Teil der Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.
feature: Commerce Integration Framework
exl-id: 3567bd28-73aa-401a-8aa9-a62a99d2a613
solution: Experience Manager,Commerce
role: Admin, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 97%
---
# E-Commerce-Übersicht{#ecommerce-overview}

Der generische AEM-E-Commerce ist als Teil einer Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.

Adobe bietet zwei Versionen des Commerce Integration Frameworks:

|                         | CIF On-Premise | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Unterstützte AEM-Versionen | AEM On-Premise oder AMS 6.x | AEM AMS 6.4 und 6.5 |
| Back-End | - AEM, Java™ <br>- Monolithische Integration, voreingestellte Zuordnung (Vorlage)<br>- JCR-Repository | - Adobe Commerce <br>- Java und JavaScript <br>- Keine Commerce-Daten im JCR-Repository gespeichert |
| Frontend | In AEM Server-seitig gerenderte Seiten | Gemischte Seitenanwendung (Hybrid-Rendering) |
| Produktkatalog | - Produktimport-Tool, Editor, Zwischenspeicherung in AEM <br>- Standardkataloge mit AEM- oder Proxy-Seiten | - Kein Produktimport <br>- Generische Vorlagen <br>- On-Demand-Daten über Connector |
| Skalierbarkeit | - Unterstützt bis zu mehrere Millionen Produkte (je nach Anwendungsfall) <br>- Zwischenspeicherung im Dispatcher | - Keine Volumenbegrenzung <br>- Zwischenspeicherung im Dispatcher oder im CDN |
| Standardisiertes Datenmodell | Nein | Ja, das Adobe Commerce GraphQL-Schema |
| Verfügbarkeit | Ja:<br>- SAP-Commerce Cloud (Erweiterung aktualisiert, um AEM 6.4 und Hybris 5 zu unterstützen (Standard) und Kompatibilität mit Hybris 4 zu gewährleisten) <br>- Salesforce-Commerce Cloud (Open-Source-Connector zur Unterstützung von AEM 6.4) | Ja, über Open Source über GitHub. <br> Adobe Commerce (unterstützt 2.3.2 (standardmäßig) und ist mit 2.3.1 kompatibel). |
| Wann ist sie einzusetzen? | Eingeschränkte Anwendungsfälle: wenn kleine, statische Kataloge importiert werden müssen | Bevorzugte Lösung in den meisten Anwendungsfällen |


## Bereitstellen weiterer Implementierungen {#deploying-other-implementations}

Für AEM und Adobe Commerce lesen Sie [Integration von AEM und Adobe Commerce](/help/commerce/cif/integrating/magento.md) mithilfe des [Commerce Integration Frameworks](/help/commerce/cif/introduction.md).

>[!NOTE]
>
>Weitere Informationen zu den Konzepten und zur Verwaltung von eCommerce-Implementierungen finden Sie unter [Verwaltung von eCommerce](/help/commerce/cif-classic/administering/ecommerce.md).
>
>Weitere Informationen zu erweiterten E-Commerce-Funktionen finden Sie unter [Entwicklung von E-Commerce](/help/commerce/cif-classic/developing/ecommerce.md).
