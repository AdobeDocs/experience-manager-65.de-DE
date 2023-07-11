---
title: Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework
description: Unternehmen benötigen möglicherweise zusätzliche Commerce-Lösungen von Drittanbietern, um ihre Storefront zu betreiben. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarios verwendet werden, um mithilfe von I/O Runtime eine Commerce-Lösung von Drittanbietern mit Adobe Experience Manager zu verbinden.
thumbnail: cif-third-party-architecture.jpg
exl-id: e99899a4-df86-4108-991a-8b30d303a279
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 61%

---

# Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework {#aem-third-party}

Die Integration von Lösungen außerhalb von Adobe Commerce ist ein häufiges Szenario für CIF. Drittanbieterlösungen mit verschiedenen APIs und Schemas werden über eine Integrationsschicht verbunden.

## Architektur {#architecture}

Die Gesamtarchitektur sieht wie folgt aus:

![Überblick über die AEM-Nicht-Magento-/-Drittanbieter-Architektur](../assets//AEM_nonMagento_Architecture.png)

Der Zweck dieser Integrationsebene ist es, APIs und Schemata von Drittanbietern den unterstützten Adobe Commerce-GraphQL-APIs und -Schemata außerhalb von Experience Manager zuzuordnen. Dank dieser Kapselung können die Integrationslogik und die Systeme aktualisiert werden, ohne den Code im Experience Manager zu ändern.

## Lösungsanforderungen für eine Integration

Da Experience Manager Daten bei Bedarf abruft, sind für den Produktkatalog Echtzeit-APIs erforderlich.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel: [Magento open-source](https://business.adobe.com/de/products/magento/open-source.html).

Es ist nicht erforderlich, das vollständige GraphQL-Schema zu implementieren, sondern nur die Objekte des Schemas, um die gewünschten Anwendungsfälle zu ermöglichen.

## Backend-Anwendungsfälle

CIF erweitert Experience Manager mit Echtzeit-Produktkatalogzugriff und Tools für das Erlebnis-Management. Diese nahtlose Integration ermöglicht es Autoren, bei Bedarf über eingebettete Benutzeroberflächen auf Commerce-Daten zuzugreifen, ohne den Inhaltskontext verlassen zu müssen.

Die Integration von Produktkatalog-APIs ist erforderlich, um diese Anwendungsfälle zu erschließen.

## Front-End-Anwendungsfälle

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) rufen Daten über die CIF-unterstützten Adobe Commerce-APIs ab und tauschen sie aus. Um Komponenten wiederzuverwenden, müssen die entsprechenden APIs implementiert sein.

Die Empfehlung für leistungskritische clientseitige Komponenten besteht darin, direkt mit der Drittanbieterlösung zu kommunizieren, um Latenzzeiten zu vermeiden.

## Entwickeln einer Integration {#develop-integration}

Adobe empfiehlt die Verwendung von [Adobe I/O Runtime](https://developer.adobe.com/apis/experienceplatform/runtime.html) für die Integrationsschicht. Es ist im CIF-Add-on für Drittanbieter enthalten. Da sie mit einem Microservice-artigen Ansatz arbeitet, ist sie gut geeignet, einfach mehrere Lösungen zu integrieren.

Die [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) ist ein guter Ausgangspunkt für die Erstellung der Integration in Ihre Commerce-Lösung. Sie unterstützt zwar GraphQL, kann aber auch mit jeder anderen Art von API wie REST integriert werden.

Diese Integrationsschicht ist nicht erforderlich, wenn eine Drittanbieterschicht verfügbar ist (z. B. Mulesoft) oder die Integration auf der Drittanbieterlösung aufbaut.

## Vorkonfigurierte Connectoren {#connectors}

Connectoren bieten einen guten Ausgangspunkt für Projekte. Sie enthalten eine Commerce-lösungsspezifische Verbindung und Standard-API-Zuordnung. Diese Connectoren werden von Dritten erstellt und nicht von Adobe gepflegt. Kontaktieren Sie den jeweiligen Partner für Informationen.

* [SAP Commerce](https://github.com/diconium/commerce-cif-graphql-integration-hybris), erstellt von Diconium
* [Commercetools](https://github.com/diconium/commerce-cif-graphql-integration-commercetool), erstellt von Diconium

>[!TIP]
>
>Obwohl Connectoren in Projekten helfen, die Commerce-Integration zu beschleunigen, sind sie nicht Plug-and-Play. Enterprise Commerce-Lösungen sind stark angepasst und erfordern eine benutzerdefinierte Integration. Es sind gute Kenntnisse der Commerce-Plattform, der Adobe Commerce GraphQL-Schemata und von Adobe I/O Runtime erforderlich.
