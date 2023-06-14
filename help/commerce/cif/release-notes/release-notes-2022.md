---
title: AEM Content and Commerce – Versionshinweise 2022
description: AEM Content and Commerce – Versionshinweise 2022
exl-id: d0a66e70-c4f1-4051-8161-11f07dad0612
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 82%

---

# Übersicht über die GitHub-Version von Commerce Integration Framework

## Übersicht über die Systemanforderungen

Überprüfen Sie die Mindestanforderungen in der folgenden Tabelle für die CIF-Version, die Sie derzeit verwenden oder in Zukunft verwenden möchten.

| Komponente | Systemanforderungen |
|:-------|:-----:|
| CIF-Add-on | Minimum: AEM 6.5.7, Adobe Commerce 2.3.5-GraphQL-Schemata |
| CIF-Kernkomponenten | [Systemanforderungen](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM-Projektarchetyp | [Systemanforderungen](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: September 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022.09.20.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.09.20.00.zip) |
| CIF-Kernkomponenten | 2.11.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.11.0) |
| CIF Venia-Referenz-Site | 2022.09.02 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.09.02) |

### Neue Funktionen {#what-is-new-september}

* Autorinnen und Autoren können Produktlisten mit Experience Fragments dynamisch anreichern (Beispiel: Das Platzieren von Bannern zwischen Produktlisten)
* Listenkomponente unterstützt verknüpfte Produkt-/Kategorieseiten zur dynamischen Anzeige verwandter Seiten
* Unterstützung für Peregrine 12.5-Komponenten
* Unterstützung für Client-seitiges Laden von Preisen in Produkt-Teaser und Karussell

## Releasedatum: Juli 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022.08.02.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.08.02.00.zip) |

### Neue Funktionen {#what-is-new-july}

* Zuordnung von AEM-Seiten zu Produkten und Kategorien über AEM-Seiteneigenschaften plus Übersicht im Produkt-Cockpit
  ![Produkt-Cockpit-Seitenzuordnung](/help/assets/CIF/product_cockpit_page_association.png)

## Releasedatum: Juni 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022.07.05.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.07.05.00.zip) |
| CIF-Kernkomponenten | 2.10.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.10.0) |
| CIF Venia-Referenz-Site | 2022.07.04 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.07.04) |

### Neue Funktionen {#what-is-new-june}

* Die Anreicherung von Produktkatalogen unterstützt jetzt AEM Seiten, sodass Autoren die Zuordnung von Seite und Produkt verwalten können.

* Verschiedene Verbesserungen der CIF-Kernkomponenten

### Fehlerbehebungen {#bug-fixes-june}

* Login-Token zur Client-seitigen Preisabfrage hinzufügen

* Falsche Seitenkomponente in der Datenschicht.

## Releasedatum: Mai 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022.05.31.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.05.31.00.zip) |
| CIF-Kernkomponenten | 2.9.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.9.0) |
| CIF Venia-Referenz-Site | 2022.05.30 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.05.30) |

### Neue Funktionen {#what-is-new-may}

* Neue Seite mit Eigenschaften für das Produkt-Cockpit für eine bessere und vereinfachte Übersicht

![Übersicht über die Eigenschaften des Produkt-Cockpits](/help/assets/CIF/product_cockpit_properties_overview.png)

* Verbesserte Kompatibilität und Stabilität für Connectoren von Drittanbietern in I/O Runtime

* Verbessern der Unterstützung für Überschreibungen der GQL-Client-Konfiguration (z. B. Festlegen des benutzerdefinierten Caching-Verhaltens)

### Fehlerbehebungen {#bug-fixes-may}

* Das Feld für die Produktauswahl mit mehreren Werten zeigt ein zweites und zusätzliche Produkte als ungültig an

* Die Produktauswahl ist gelegentlich hinter Komponenten verborgen.

## Releasedatum: April 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022.04.28.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.04.28.00.zip) |
| CIF-Kernkomponenten | 2.8.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.8.0) |
| CIF Venia-Referenz-Site | 2022.04.28 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.04.28) |

### Neue Funktionen {#what-is-new-april}

* Schnellzugriff auf das Produkt-Cockpit: Einfacher Zugriff auf detaillierte Produktinformationen mit einem Klick im Sites-Editor

  ![Wunschliste aktivieren](/help/assets/CIF/enable-wishlist.png)

* Unterstützung für zusätzliche Marketing-Commerce-Komponenten: Komponenten können so konfiguriert werden, dass sie einen Aufruf zum Hinzufügen zum Warenkorb und zum Hinzufügen zur Wunschliste anzeigen

  ![Verknüpfung mit dem Produkt-Cockpit im Sites-Editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)

## Releasedatum: Februar 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022.02.24.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.02.24.00.zip) |
| CIF-Kernkomponenten | 2.6.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.6.0) |
| CIF Venia-Referenz-Site | 2022.02.24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.02.24) |

### Neue Funktionen {#what-is-new-march}

* Beta: AEM CIF-Kernkomponente für die Suche unterstützt Commerce LiveSearch
* Verbessertes SEO für Multi-Store-Szenarien: URL-Formate für PDP/PLP können jetzt auf Store-Ebene über die CIF-Cloud-Konfigurationseigenschaften konfiguriert werden
* Die Produktauswahl unterstützt Staging-Produkte über die neue Filteroption in der Benutzeroberfläche. Ermöglicht es Inhaltspraktikern, das Content Management für bevorstehende Produktstarts vorzubereiten.
* Vereinfachte CIF-Konfigurationsverwaltung und Fehlerbehandlung durch Verwendung des CIF-Cloud-Konfigurationsnamens anstelle der Proxy-URL für die Konfiguration
* Manuelle Kategorieauswahl für Produktlisten- und Karussellkomponenten. Ermöglicht es Inhaltspraktikern, diese Komponenten auf Inhaltsseiten außerhalb des Katalogerlebnisses zu verwenden

## Releasedatum: Januar 2022

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2022.01.20.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2022.01.20.00.zip) |
| CIF-Kernkomponenten | 2.5.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.5.0) |
| CIF Venia-Referenz-Site | 2022.01.27 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2022.01.27) |

### Neue Funktionen {#what-is-new-january}

* Verbesserte myAccount-Komponenten
* Die Komponente „Produktempfehlung“ unterstützt zusätzliche Seitentypen (Homepage, Warenkorb, Bestellbestätigung).
* **Wunschliste**
   * Angemeldete Besucher können Produkte zu einer Wunschliste hinzufügen
   * Die Verwaltung der Wunschliste und ihrer Produkte ist über myAccount möglich
   * Die Schaltfläche „Zur Wunschliste hinzufügen“ kann auf Komponentenebene über eine Richtlinie (z. B. Produkt-Teaser, Produktdetails) aktiviert/deaktiviert werden
   * Verfügbar als Kernkomponente und in der Venia-Storefront von AEM

![Wunschliste](/help/assets/CIF/wishlist.png)
