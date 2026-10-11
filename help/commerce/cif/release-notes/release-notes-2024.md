---
title: AEM Content and Commerce – Versionshinweise 2024
description: Versionshinweise zu Adobe Experience Manager Content and Commerce 2024.
exl-id: 372e6a46-72bb-4db4-ad01-534ca723ae58
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
source-wordcount: '274'
ht-degree: 100%
---
# Übersicht über die GitHub-Version von Commerce Integration Framework

## Übersicht über die Systemanforderungen

Überprüfen Sie die Mindestsystemanforderungen in der folgenden Tabelle für die CIF-Version, die Sie derzeit verwenden oder in Zukunft verwenden möchten.

| Komponente | Systemanforderungen |
|:-------|:-----------------------------------------------------------------------------------------------:|
| CIF-Add-on | Minimum: AEM 6.5.18, Adobe Commerce 2.3.5-GraphQL-Schemata |
| CIF-Kernkomponenten | [Systemanforderungen](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM-Projektarchetyp | [Systemanforderungen](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Veröffentlichungsdatum: Oktober 2024

| Komponente | Version | Details |
|:-------|:-------:|-----------------------------------------------------------------------------------------------------------:|
| CIF-Kernkomponenten | 2.15.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.15.0) |

### Fehlerbehebungen {#bug-fixes-October}

* Die Benutzeroberflächentests funktionieren jetzt ordnungsgemäß mit den CIF-Kernkomponenten.
* Es wurde ein Problem behoben, durch das das URL-Format „Kategorie“ in der Cloud-Instanz nicht wie erwartet funktionierte.

## Veröffentlichungsdatum: September 2024

| Komponente | Version | Details |
|:-------|:-------:|-----------------------------------------------------------------------------------------------------------:|
| CIF-Kernkomponenten | 2.14.2 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.14.2) |

### Verbesserungen {#improvements-September}

* Kategoriebegrenzung anpassbar machen.

### Fehlerbehebungen {#bug-fixes-September}

* Commerce-Felder sind nicht ordnungsgemäß mit dem Metadatenschema-Editor von Assets integriert.
* Problem mit dem Karussell-Produkte-Multifield für Drag-and-Drop.
* Problem mit dem Karussell-Kategorie-Multifield für Drag-and-Drop.
* Anklicken funktioniert nicht in den Menüs der Seiteninformation für die Kategorie- und Produkt-Editor-Seite.
* Die Bestellnummer ist auf der Seite „Bestellbestätigung“ nicht sichtbar.

## Veröffentlichungsdatum: Januar 2024

| Komponente | Version | Details |
|:-------|:-------:|-----------------------------------------------------------------------------------------------------------:|
| CIF-Kernkomponenten | 2.12.6 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.12.6) |

### Fehlerbehebungen {#bug-fixes-january}

* Die Schaltfläche „Zum Warenkorb hinzufügen“ und die Schaltfläche „Zur Wunschliste hinzufügen“ in der Produktkollektionskomponente wurden korrigiert
