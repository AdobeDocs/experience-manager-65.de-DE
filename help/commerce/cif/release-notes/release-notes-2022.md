---
title: AEM Content and Commerce - Versionshinweise 2022
description: AEM Content and Commerce - Versionshinweise 2022
exl-id: ec47c5f8-d4dd-469f-94df-5ee28f25d696
source-git-commit: 26df21270e8c586ba21b9bf3e9fc5003facbaade
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 22%

---

# Übersicht über die Commerce Integration Framework GitHub-Version

## Übersicht über die Systemanforderungen

Überprüfen Sie die Mindestanforderungen in der folgenden Tabelle für die CIF-Version, die Sie derzeit verwenden oder in Zukunft verwenden möchten.

| Komponente | Systemanforderungen |
|:-------|:-----:|
| CIF-Add-on | Minimum: AEM 6.5.7, Magento 2.3.5 GraphQL-Schemata |
| CIF-Kernkomponenten | [Systemanforderungen](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM-Projektarchetyp | [Systemanforderungen](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: Januar 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022,01,20,00 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.01.20.00.zip) |
| CIF-Kernkomponenten | 2,5,0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.5.0) |
| CIF Venia-Referenz-Site | 2022,01,27 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.01.27) |

### Neue Funktionen {#what-is-new-january}

* Verbesserte myAccount-Komponenten
* Die Komponente &quot;Produktempfehlung&quot;unterstützt zusätzliche Seitentypen (Homepage, Warenkorb, Bestellbestätigung).
* **Wunschliste**
   * Angemeldete Besucher können Produkte zu einer Wunschliste hinzufügen
   * Die Verwaltung der Wunschliste und ihrer Produkte ist über myAccount möglich.
   * Die Schaltfläche &quot;Zur Wunschliste hinzufügen&quot;kann auf Komponentenebene über eine Richtlinie (z. B. Produkt-Teaser, Produktdetails) aktiviert/deaktiviert werden
   * Verfügbar als Kernkomponente und in der Venia-Storefront AEM

![Wunschliste](/help/assets/CIF/wishlist.png)

