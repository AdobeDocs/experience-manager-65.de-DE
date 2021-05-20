---
title: Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework
description: Unternehmen benötigen möglicherweise zusätzliche Commerce-Lösungen von Drittanbietern, um ihre Storefront zu betreiben. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarios verwendet werden, um mithilfe von I/O Runtime eine Commerce-Lösung von Drittanbietern mit Adobe Experience Manager zu verbinden.
thumbnail: cif-third-party-architecture.jpg
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 4%

---

# Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework {#aem-third-party}

Die Integration einer Commerce-Lösung, die keine Adobe ist, ist ein gängiges Szenario für CIF. Drittanbieterlösungen mit verschiedenen APIs und Schemas werden über eine Integrationsschicht verbunden.

## Architektur {#architecture}

Die Gesamtarchitektur sieht wie folgt aus:

![AEM Überblick über die Nicht-Magento-/Drittanbieter-Architektur](../assets//AEM_nonMagento_Architecture.png)

Diese Integrationsschicht dient der Zuordnung von Drittanbieter-APIs und -Schemas zu den unterstützten Commerce-GraphQL-APIs und -Schemas außerhalb des Experience Managers der Adobe. Dank dieser Kapselung können die Integrationslogik und -systeme aktualisiert werden, ohne den Code im Experience Manager zu ändern.

## Lösungsanforderungen für eine Integration

Da der Experience Manager Daten bei Bedarf abruft, sind Echtzeit-APIs für den Produktkatalog erforderlich.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel [Magento open-source](https://magento.com/products/magento-open-source).

Es ist nicht erforderlich, das vollständige GraphQL-Schema zu implementieren, sondern nur die Objekte des Schemas, um die gewünschten Anwendungsfälle zu aktivieren.

## Backend-Anwendungsfälle

CIF erweitert den Experience Manager mit Echtzeit-Produktkatalogzugriff und Tools für das Erlebnismanagement. Diese nahtlose Integration ermöglicht es Autoren, bei Bedarf über eingebettete Benutzeroberflächen auf Commerce-Daten zuzugreifen, ohne den Inhaltskontext verlassen zu müssen.

Die Integration von Produktkatalog-APIs ist erforderlich, um diese Anwendungsfälle zu entsperren.

## Frontend-Anwendungsfälle

[AEM CIF-Kernkomponenten ](https://github.com/adobe/aem-core-cif-components) rufen Daten über die CIF-unterstützten Adobe Commerce-APIs ab und tauschen sie aus. Um Komponenten wiederzuverwenden, müssen die entsprechenden APIs implementiert werden.

Die Empfehlung für leistungskritische clientseitige Komponenten besteht darin, direkt mit der Drittanbieterlösung zu kommunizieren, um Latenzzeiten zu vermeiden.

## Entwickeln einer Integration {#develop-integration}

Es wird empfohlen, [Adobe I/O Runtime](https://www.adobe.io/apis/experienceplatform/runtime.html) für die Integrationsschicht zu verwenden. Sie ist im CIF-Add-on für Dritte enthalten. Da es mit einem Mikroservice-ähnlichen Ansatz arbeitet, ist es gut geeignet, einfach mehrere Lösungen zu integrieren.

Die [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) ist ein guter Ausgangspunkt für die Erstellung der Integration in Ihre Commerce-Lösung. Obwohl GraphQL unterstützt wird, kann es auch in andere API-Typen wie REST integriert werden.

Diese Integrationsschicht ist nicht erforderlich, wenn eine Drittanbieterschicht verfügbar ist (z. B. Mulesoft) oder die Integration auf der Drittanbieterlösung aufbaut.
