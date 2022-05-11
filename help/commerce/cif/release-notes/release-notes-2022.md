---
title: AEM Content and Commerce - Versionshinweise 2022
description: AEM Content and Commerce - Versionshinweise 2022
exl-id: d0a66e70-c4f1-4051-8161-11f07dad0612
source-git-commit: aacb497b10f46be3157aae86a5973aa277fda967
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 21%

---

# Übersicht über die Commerce Integration Framework GitHub-Version

## Übersicht über die Systemanforderungen

Überprüfen Sie die Mindestanforderungen in der folgenden Tabelle für die CIF-Version, die Sie derzeit verwenden oder in Zukunft verwenden möchten.

| Komponente | Systemanforderungen |
|:-------|:-----:|
| CIF-Add-on | Minimum: AEM 6.5.7, Magento 2.3.5 GraphQL-Schemata |
| CIF-Kernkomponenten | [Systemanforderungen](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM-Projektarchetyp | [Systemanforderungen](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: April 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022,04,28,00 | [Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.04.28.00.zip) |
| CIF-Kernkomponenten | 2,8,0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.8.0) |
| CIF Venia-Referenz-Site | 2022.04.28 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.04.28) |

### Neue Funktionen {#what-is-new}

* Schnellzugriff auf das Produkt-Cockpit: Einfacher Zugriff auf detaillierte Produktinformationen mit einem Klick im Sites Editor

   ![Wunschliste aktivieren](/help/assets/CIF/enable-wishlist.png)

* Unterstützung für zusätzliche Marketing-Commerce-Komponenten: Komponenten können so konfiguriert werden, dass sie einen Aufruf zum Hinzufügen zum Warenkorb und zum Hinzufügen zur Wunschliste anzeigen

   ![Verknüpfung zum Produkt-Cockpit im Sites-Editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)

## Releasedatum: März 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022,02,24,00 | [Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.02.24.00.zip) |
| CIF-Kernkomponenten | 2,6,0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) |
| CIF Venia-Referenz-Site | 2022,02,24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.02.24) |

### Neue Funktionen {#what-is-new-march}

* Beta: AEM CIF-Such-Kernkomponente unterstützt Commerce LiveSearch
* Verbessertes SEO für Multi-Store-Szenarien: URL-Formate für PDP/PLP können jetzt auf Store-Ebene über die CIF Cloud-Konfigurationseigenschaften konfiguriert werden
* Die Produktauswahl unterstützt gestaffelte Produkte über die neue Filteroption in der Benutzeroberfläche.  Dadurch können Content-Experten das Content-Management für bevorstehende Produktstarts vorbereiten.
* Vereinfachte CIF-Konfigurationsverwaltung und Fehlerbehandlung durch Verwendung des CIF-Cloud-Konfigurationsnamens anstelle der config-Proxy-URL
* Manuelle Kategorieauswahl für Produktliste und Karussellkomponenten. Dadurch können Content-Experten diese Komponenten auf Inhaltsseiten außerhalb des Katalogerlebnisses verwenden

## Releasedatum: Januar 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022,01,20,00 | [Software-Verteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.01.20.00.zip) |
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
