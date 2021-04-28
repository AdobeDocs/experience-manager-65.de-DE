---
title: Migration zum AEM Commerce Integration Framework (CIF)-Add-on
description: So migrieren Sie von einer alten Version zum AEM Commerce Integration Framework (CIF)-Add-On
translation-type: tm+mt
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 4%

---

# Migrationshandbuch für den Experience Manager Hinzufügen-On {#cif-migration}

Dieses Handbuch hilft Ihnen dabei, die Bereiche zu identifizieren, die Sie für die Experience Manager-Add-on-Migration aktualisieren müssen.

## CIF-Hinzufügen

CIF-Add-on ist für AEM 6.5 über das [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar. Es ist kompatibel und bietet dieselben Funktionen wie das CIF-Add-on für Experience Manager wie ein Cloud Service.

Siehe [Erste Schritte mit AEM Content and Commerce](getting-started.md).

Zur Unterstützung von CIF-Bereitstellungsprojekten stellt Adobe [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bereit.

## Produktkatalog

Das Importieren von Produktkatalogdaten wird vom CIF-Add-on nicht unterstützt. Mithilfe der CIF-Add-On-Prinzipale werden Produkt- und Kataloganforderungen über Echtzeitaufrufe an eine externe Commerce-Lösung auf Abruf gesendet. Gehen Sie zu Kapitel Integration, um mehr über die Integration einer Commerce-Lösung zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel [Magento open-source](https://magento.com/products/magento-open-source).

## Erlebnisse im Produktkatalog mit AEM Rendering

Wenn Sie Katalogvorlagen mit Classic CIF verwenden, müssen Sie den Arbeitsablauf für Produktkataloge aktualisieren. Das CIF-Add-on rendert jetzt Produktkatalog-Erlebnisse im Handumdrehen mithilfe AEM Katalogvorlagen. Es ist keine Replikation von Produktdaten oder Produktseiten mehr erforderlich.

## Nicht speicherbare Daten und Shopping-Interaktion

Clientseitige Anforderungen für nicht zwischengespeicherte Daten und Interaktionen (z. B. Add-to-cart, Suche) sollten direkt über CDN/Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsebene) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur ein Proxy war.
