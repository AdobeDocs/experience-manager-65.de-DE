---
title: Migration zum Add-on für das AEM Commerce Integration Framework (CIF)
description: Migrieren zum Add-on für das AEM Commerce Integration Framework (CIF) von einer alten Version
exl-id: c6c0c2fc-6cfa-4c64-b3d8-7e428b2a4b2e
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: ht
source-wordcount: '265'
ht-degree: 100%

---

# Leitfaden zur Migration für das Experience Manager Add-on {#cif-migration}

Dieser Leitfaden hilft bei der Identifizierung von Bereichen, die für die Experience Manager Add-on-Migration aktualisiert werden müssen.

## CIF-Add-on

Das CIF-Add-on ist über das [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) auch für AEM 6.5 verfügbar. Es ist mit dem CIF-Add-on kompatibel und bietet dieselben Funktionen für Experience Manager as a Cloud Service.

Siehe [Erste Schritte mit AEM Content and Commerce](getting-started.md).

Um Projekte mit CIF-Bereitstellung zu unterstützen, stellt Adobe die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bereit.

## Produktkatalog

Der Import von Produktkatalogdaten wird vom CIF-Add-on nicht unterstützt. Die Verwendung der CIF-Add-on-Prinzipale für Produkt- und Kataloganforderungen erfolgt über Echtzeit-Aufrufe an eine externe Commerce-Lösung. Wechseln Sie zum Kapitel über Integration, um mehr über die Integration von Commerce-Lösungen zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel: [Magento Open Source](https://business.adobe.com/de/products/magento/open-source.html).

## Produktkatalogerlebnisse mit AEM-Rendering

Wenn Sie die Katalog-Blueprint mit dem klassischen CIF verwenden, müssen Sie den Workflow für den Produktkatalog aktualisieren. Das CIF-Add-on rendert Produktkatalog-Erlebnisse mithilfe von AEM-Katalogvorlagen nun direkt. Das Replizieren von Produktdaten oder Produktseiten ist nicht mehr erforderlich.

## Nicht Cache-taugliche Daten und Shopping-Interaktionen

Client-seitige Anforderungen für nicht Cache-taugliche Daten und Interaktionen (z. B. Warenkorb-Interaktionen, Suchen) sollten direkt über das CDN bzw. den Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsschicht) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur als Proxy fungierte.
