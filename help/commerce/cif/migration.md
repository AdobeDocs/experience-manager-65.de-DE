---
title: Migration zum Add-on für das AEM Commerce Integration Framework (CIF)
description: Migrieren zum Add-on für das AEM Commerce Integration Framework (CIF) von einer alten Version
exl-id: c6c0c2fc-6cfa-4c64-b3d8-7e428b2a4b2e
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 44%

---

# Migrationshandbuch für das Experience Manager-Add-on {#cif-migration}

Dieses Handbuch hilft dabei, die Bereiche zu identifizieren, die für die Experience Manager-Add-on-Migration aktualisiert werden müssen.

## CIF-Add-on

Das CIF-Add-on ist für AEM 6.5 über die [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Es ist kompatibel und bietet dieselben Funktionen wie das CIF-Add-on für Experience Manager as a Cloud Service.

Siehe [Erste Schritte mit AEM Content und Commerce](getting-started.md).

Zur Unterstützung von CIF-Projekten bietet Adobe [CIF-Kernkomponenten AEM](https://github.com/adobe/aem-core-cif-components).

## Produktkatalog

Der Import von Produktkatalogdaten wird vom CIF-Add-on nicht unterstützt. Mithilfe der CIF-Add-On-Prinzipale werden Produkt- und Kataloganforderungen über Echtzeitaufrufe an eine externe Commerce-Lösung On-Demand ausgeführt. Wechseln Sie zum Kapitel über Integration, um mehr über die Integration von Commerce-Lösungen zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel: [Magento Open Source](https://business.adobe.com/products/magento/open-source.html).

## Produktkatalog-Erlebnisse mit AEM Rendering

Wenn Sie die Katalog-Blueprint mit dem klassischen CIF verwenden, müssen Sie den Workflow für den Produktkatalog aktualisieren. Das CIF-Add-on rendert Produktkatalog-Erlebnisse mithilfe von AEM-Katalogvorlagen nun direkt. Das Replizieren von Produktdaten oder Produktseiten ist nicht mehr erforderlich.

## Nicht zwischenspeicherbare Daten und Shopping-Interaktion

Clientseitige Anforderungen für nicht zwischenspeicherbare Daten und Interaktionen (z. B. Add-to-Warenkorb, Suche) sollten direkt über CDN/Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsschicht) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur als Proxy fungierte.
