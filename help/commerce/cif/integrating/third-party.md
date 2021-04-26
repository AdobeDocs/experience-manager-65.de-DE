---
title: Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework
description: Unternehmen benötigen möglicherweise zusätzliche Drittanbieterlösungen für den Handel, um ihre Storefront zu betreiben. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarien verwendet werden, um eine Drittanbieterlösungen für den Handel mit Adobe Experience Manager über I/O Runtime zu verbinden.
thumbnail: cif-third-party-architecture.jpg
translation-type: tm+mt
source-git-commit: d92a635d41cf1b14e109c316bd7264cf7d45a9fe
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 20%

---

# Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework {#aem-third-party}

Die Integration von Nicht-Adobe-Commerce-Lösungen ist ein gängiges Szenario für CIF. Lösungen von Drittanbietern mit verschiedenen APIs und Schemas werden über eine Integrationsebene miteinander verbunden.

## Architektur {#architecture}

Die Gesamtarchitektur sieht wie folgt aus:

![Überblick über die AEM-Nicht-Magento-/-Drittanbieter-Struktur](../assets//AEM_nonMagento_Architecture.png)

Diese Integrationsebene dient der Zuordnung von Drittanbieter-APIs und -Schemas zu den unterstützten Adobe-Commerce-GraphQL-APIs und -Schemas außerhalb des Experience Managers. Dank dieser Kapselung können die Integrationslogik und die Systeme aktualisiert werden, ohne den Code im Experience Manager zu ändern.

## Lösungsanforderungen für eine Integration

Da der Experience Manager Daten bei Bedarf abruft, sind Echtzeit-APIs für den Produktkatalog erforderlich.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel [Magento open-source](https://magento.com/products/magento-open-source).

Es ist nicht notwendig, das vollständige GraphQL Schema zu implementieren, sondern nur die Objekte des Schemas, um die gewünschten Anwendungsfälle zu aktivieren.

## Backend-Anwendungsfälle

CIF erweitert den Experience Manager um Echtzeit-Produktkatalogzugriff und Produkterlebnis-Management-Tools. Diese nahtlose Integration ermöglicht Autoren den Zugriff auf Commerce-Daten mit eingebetteten Benutzeroberflächen, wann immer dies erforderlich ist, ohne den Inhaltskontext zu verlassen.

Die Integration von Produktkatalog-APIs ist erforderlich, um diese Anwendungsfälle zu entsperren.

## Frontend-Anwendungsfälle

[AEM CIF-Core-](https://github.com/adobe/aem-core-cif-components) Komponenten rufen Daten über die CIF-unterstützten Adobe Commerce-APIs ab und tauschen sie aus. Zur Wiederverwendung von Komponenten müssen die entsprechenden APIs implementiert werden.

Die Empfehlung für leistungskritische clientseitige Komponenten besteht darin, direkt mit der Drittanbieter-Lösung zu kommunizieren, um Latenzzeiten zu vermeiden.

## Entwickeln einer Integration {#develop-integration}

Es wird empfohlen, [Adobe I/O Runtime](https://www.adobe.io/apis/experienceplatform/runtime.html) für die Integrationsebene zu verwenden. Es ist im CIF-Add-on für Dritte enthalten. Da es mit einem mikrodienstähnlichen Ansatz funktioniert, eignet es sich gut, mehrere Lösungen einfach zu integrieren.

Die [Referenz-Implementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) ist ein hervorragender Ausgangspunkt zum Aufbau der Integration in Ihre Commerce-Lösung. GraphQL wird zwar unterstützt, kann aber auch in andere API-Typen wie REST integriert werden.

Diese Integrationsebene ist nicht erforderlich, wenn eine Drittanbieterebene verfügbar ist (z. B. Mulesoft) oder die Integration auf der Lösung eines Drittanbieters aufbaut.
