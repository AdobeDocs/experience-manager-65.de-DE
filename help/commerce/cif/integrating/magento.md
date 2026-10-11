---
title: Integration von AEM und Adobe Commerce mithilfe des Commerce Integration Framework
description: AEM und Adobe Commerce werden über das Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM den Zugriff auf eine Adobe Commerce-Instanz und die Kommunikation mit Adobe Commerce über GraphQL. Darüber hinaus können AEM-Autoren Produkt- und Kategorieauswahlen sowie die Produktkonsole verwenden, um Produkt- und Kategoriedaten zu durchsuchen, die bei Bedarf aus Adobe Commerce abgerufen werden . Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.
thumbnail: aem-magento-architecture.jpg
exl-id: f843784c-5ff7-41d1-97c5-13facb8459b2
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
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
source-wordcount: '402'
ht-degree: 80%
---
# Integration von AEM und Adobe Commerce (Magento) mithilfe des Commerce Integration Framework {#aem-commerce-framework}

Adobe Experience Manager und Adobe Commerce werden über das Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM direkten Zugriff auf und die direkte Kommunikation mit der Commerce-Instanz mithilfe der [GraphQL-APIs](https://devdocs.magento.com/guides/v2.4/graphql/) von Adobe Commerce.

>[!NOTE]
>
>Die mindestens unterstützte GraphQL API-Version ist 2.3.5. Bestimmte Funktionen werden nur in neueren Versionen oder nur in der Adobe Commerce-Edition unterstützt.

## Architekturüberblick {#overview}

Die Gesamtarchitektur sieht wie folgt aus:

![CIF-Architekturübersicht](../assets/AEM_Magento_Architecture.png)

CIF unterstützt Server-seitige und Client-seitige Kommunikationsmuster.
Server-seitige APIs werden mithilfe des integrierten, generischen [GraphQL-Clients](https://github.com/adobe/commerce-cif-graphql-client) in Kombination mit einem [Satz generierter Datenmodelle) ](https://github.com/adobe/commerce-cif-magento-graphql) Commerce-GraphQL-Schema implementiert. Darüber hinaus können alle GraphQL-Abfragen oder Mutationen im GQL-Format verwendet werden.

Bei Client-seitigen Komponenten, die mit [React](https://reactjs.org/) erstellt werden, kommt der [Apollo-Client](https://www.apollographql.com/docs/react/) zum Einsatz.

## Architektur mit den AEM CIF-Kernkomponenten {#cif-core-components}

![Architektur mit den AEM CIF-Kernkomponenten](../assets/cif-component-architecture.jpg)

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) folgen sehr ähnlichen Design-Mustern und Best Practices wie die [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components).

Die Geschäftslogik und Backend-Kommunikation mit Adobe Commerce für die AEM CIF-Kernkomponenten werden in Sling-Modellen implementiert. Falls es notwendig ist, diese Logik an projektspezifische Anforderungen anzupassen, kann das Delegationsmuster für Sling-Modelle verwendet werden.

>[!TIP]
>
>Die Seite [Anpassen von AEM CIF-Kernkomponenten](../customizing/customize-cif-components.md) enthält ein detailliertes Beispiel und Best Practices zur Anpassung von CIF-Kernkomponenten.

Innerhalb von Projekten können AEM CIF-Kernkomponenten und benutzerdefinierte Projektkomponenten den konfigurierten Client für einen mit einer AEM-Seite verknüpften Adobe Commerce-Store über eine Sling-kontextsensible Konfiguration abrufen.
