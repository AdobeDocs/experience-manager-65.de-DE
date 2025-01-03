---
title: E-Commerce-Übersicht
description: Der generische AEM-E-Commerce ist als Teil der Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.
feature: Commerce Integration Framework
exl-id: 3567bd28-73aa-401a-8aa9-a62a99d2a613
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 100%

---

# E-Commerce-Übersicht{#ecommerce-overview}

Der generische AEM-E-Commerce ist als Teil einer Standardinstallation verfügbar und bietet Ihnen alle Funktionen des E-Commerce-Frameworks.

Adobe bietet zwei Versionen des Commerce-Integrations-Frameworks:

|                         | CIF On-Premise | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Unterstützte AEM-Versionen | AEM On-Premise oder AMS 6.x | AEM AMS 6.4 und 6.5 |
| Back-End | - AEM, Java™ <br>- Monolithische Integration, voreingestellte Zuordnung (Vorlage)<br>- JCR-Repository | - Adobe Commerce <br>- Java und JavaScript <br>- Keine Commerce-Daten im JCR-Repository gespeichert |
| Frontend | In AEM Server-seitig gerenderte Seiten | Gemischte Seitenanwendung (Hybrid-Rendering) |
| Produktkatalog | - Produktimport-Tool, Editor, Zwischenspeicherung in AEM <br>- Standardkataloge mit AEM- oder Proxy-Seiten | - Kein Produktimport <br>- Generische Vorlagen <br>- On-Demand-Daten über Connector |
| Skalierbarkeit | - Unterstützt bis zu mehrere Millionen Produkte (je nach Anwendungsfall) <br>- Zwischenspeicherung im Dispatcher | - Keine Volumenbegrenzung <br>- Zwischenspeicherung im Dispatcher oder im CDN |
| Standardisiertes Datenmodell | Nein | Ja, das Adobe Commerce GraphQL-Schema |
| Verfügbarkeit | Ja:<br>- SAP-Commerce Cloud (Erweiterung aktualisiert, um AEM 6.4 und Hybris 5 zu unterstützen (Standard) und Kompatibilität mit Hybris 4 zu gewährleisten) <br>- Salesforce-Commerce Cloud (Open-Source-Connector zur Unterstützung von AEM 6.4) | Ja, über Open Source von GitHub. <br> Adobe Commerce (unterstützt 2.3.2 (standardmäßig) und ist mit 2.3.1 kompatibel). |
| Wann ist sie einzusetzen? | Eingeschränkte Anwendungsfälle: wenn kleine, statische Kataloge importiert werden müssen | Bevorzugte Lösung in den meisten Anwendungsfällen |


## Bereitstellen weiterer Implementierungen {#deploying-other-implementations}

Für AEM und Adobe Commerce lesen Sie [Integration von AEM und Adobe Commerce](/help/commerce/cif/integrating/magento.md) mithilfe des [Commerce-Integrations-Frameworks](/help/commerce/cif/introduction.md).

>[!NOTE]
>
>Weitere Informationen zu den Konzepten und zur Verwaltung von eCommerce-Implementierungen finden Sie unter [Verwaltung von eCommerce](/help/commerce/cif-classic/administering/ecommerce.md).
>
>Weitere Informationen zu erweiterten E-Commerce-Funktionen finden Sie unter [Entwicklung von E-Commerce](/help/commerce/cif-classic/developing/ecommerce.md).
