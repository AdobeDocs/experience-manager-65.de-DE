---
title: Migration zum AEM Commerce Integration Framework (CIF)-Add-on
description: Migrieren zum AEM Commerce Integration Framework (CIF)-Add-on von einer alten Version
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 4%

---

# Migrationshandbuch für das Experience Manager-Add-on {#cif-migration}

Dieses Handbuch hilft dabei, die Bereiche zu identifizieren, die für die Experience Manager-Add-on-Migration aktualisiert werden müssen.

## CIF-Add-on

Das CIF-Add-on ist für AEM 6.5 über das [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar. Es ist kompatibel und bietet dieselben Funktionen wie das CIF-Add-on für Experience Manager als Cloud Service.

Siehe [Erste Schritte mit AEM Content and Commerce](getting-started.md).

Zur Unterstützung von CIF-Projekten stellt Adobe [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bereit.

## Produktkatalog

Der Import von Produktkatalogdaten wird vom CIF-Add-on nicht unterstützt. Mithilfe der CIF-Add-On-Prinzipale werden Produkt- und Kataloganforderungen über Echtzeitaufrufe an eine externe Commerce-Lösung On-Demand ausgeführt. Gehen Sie zu Kapitel-Integration , um mehr über die Integration einer Commerce-Lösung zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel [Magento open-source](https://magento.com/products/magento-open-source).

## Produktkatalog-Erlebnisse mit AEM Rendering

Wenn Sie den Katalog-Blueprint mit Classic CIF verwenden, müssen Sie den Workflow für den Produktkatalog aktualisieren. Das CIF-Add-on rendert jetzt Produktkatalog-Erlebnisse mithilfe AEM Katalogvorlagen direkt. Es ist keine Replikation von Produktdaten oder Produktseiten mehr erforderlich.

## Nicht zwischenspeicherbare Daten und Shopping-Interaktion

Clientseitige Anforderungen für nicht zwischenspeicherbare Daten und Interaktionen (z. B. Add-to-Warenkorb, Suche) sollten direkt über CDN/Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsebene) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur ein Proxy war.
