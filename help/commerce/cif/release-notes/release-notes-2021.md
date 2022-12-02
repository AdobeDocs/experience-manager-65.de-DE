---
title: AEM Content and Commerce – Versionshinweise 2021
description: AEM Content and Commerce – Versionshinweise 2021
exl-id: ec47c5f8-d4dd-469f-94df-5ee28f25d696
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '1314'
ht-degree: 100%

---

# Übersicht über die GitHub-Version von Commerce Integration Framework

## Übersicht über die Systemanforderungen

Überprüfen Sie die minimalen Systemanforderungen in der folgenden Tabelle für die CIF-Version, die Sie derzeit verwenden oder in Zukunft verwenden möchten.

| Komponente | Systemanforderungen |
|:-------|:-----:|
| CIF-Add-on | Minimum: AEM 6.5.7, Adobe Commerce 2.3.5-GraphQL-Schemata |
| CIF-Kernkomponenten | [Systemanforderungen](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM-Projektarchetyp | [Systemanforderungen](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Veröffentlichungsdatum: November 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.11.18.00 | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.11.18.00.zip) |
| CIF-Kernkomponenten | 2.4.2 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.4.2) |
| CIF Venia-Referenz-Site | 2021.12.01 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.12.01) |

### Neue Funktionen {#what-is-new-november}

* Erweiterte myAccount-Komponenten, die auf den erweiterbaren Peregrine-Komponenten von Commerce basieren

![Erweiterte myAccount-Komponenten](/help/assets/CIF/extended-myAccount-components.png)

* Autoren können Ad-hoc-Commerce-Produktempfehlungen mithilfe zusätzlicher Empfehlungstypen erstellen

* Unterstützung für Geschenkgutscheine in der AEM-Storefront

## Veröffentlichungsdatum: Oktober 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.10.20.02 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.10.20.02.zip) |
| CIF-Kernkomponenten | 2.4.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.4.0) |
| CIF Venia-Referenz-Site | 2021.11.01 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.11.01) |

### Neue Funktionen {#what-is-new-october}

* Das CIF-Add-on unterstützt die neueste Commerce-Version 2.4.3 mit neuen GraphQL-APIs und -Schemata

* Autoren können mithilfe des Rich-Text-Editors (RTE) Links zu Produkt- und Katalogseiten in Textfeldern hinzufügen. Es wurde ein CIF-Symbol zur RTE-Symbolleiste hinzugefügt, mit dem sich die Auswahlwerkzeuge öffnen lassen, um das Produkt oder die Kategorie schnell zu suchen und auszuwählen, ohne den Kontext zu verlassen.

* Bestehende Popups für Warenkorb- und Kassenvorgänge wurden durch spezielle AEM-Seiten für Warenkorb und Checkout ersetzt. Die Komponenten auf diesen Seiten werden mithilfe der erweiterbaren Peregrine-Komponenten von Adobe Commerce erstellt

* Händler können bestimmte Kategorien des Produktkatalogs in der Navigation mithilfe des Commerce-Backends ausblenden. Die CIF-Navigations-Kernkomponente respektiert die Konfiguration „Einbeziehen in Menü“ im Commerce-Backend, um Kategorien in der Navigation ein- oder auszublenden.

* AEM Storefront Venia gibt den HTTP 404-Fehler zurück, wenn keine Kategorie- oder Produktseite gefunden wird

## Veröffentlichungsdatum: September 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.09.27 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.09.27.zip) |
| CIF-Kernkomponenten | 2.2.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.2.0) |
| CIF Venia-Referenz-Site | 2021.09.23 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.09.23) |

### Neue Funktionen {#what-is-new-september}

* Die neue Registerkarte „Zugehörige Commerce-Inhalte“ im Sites-Editor erhöht die Autoreneffizienz, indem schnell auf relevante AEM-Produktinhalte für den aktuellen Kontext zugegriffen werden kann.

   ![Zugehörige Commerce-Inhalte](/help/assets/CIF/associated-commerce-content.png)

* Verbesserte Benutzeroberfläche für die Produktauswahl für ein besseres Benutzererlebnis, höhere Effizienz und Unterstützung für einen komplexen Produktkatalog

   ![Neue Produktauswahl](/help/assets/CIF/product-picker.png)

* Berücksichtigung der Eigenschaft „include_in_menu“ in der Navigationskomponente

### Fehlerbehebungen {#bug-fixes-september}

* Das Leeren des Menücache funktioniert jetzt erwartungsgemäß

* JS-Fehler während AEM CS-Bereitstellungsschritts und bei Nichtverwendung Client-seitiger Komponenten tritt nicht mehr auf

* CIF-Cloud-Konfiguration kann jetzt auch in Ordnern erstellt werden, die einen sling:configs-Knoten haben

## Veröffentlichungsdatum: August 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.09.02 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.09.02.zip) |
| CIF-Kernkomponenten | 2.1.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.1.0) |
| CIF Venia-Referenz-Site | 2021.08.27 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.08.27) |

### Neue Funktionen {#what-is-new-august}

* Neue Kategorieauswahl-Benutzeroberfläche für ein verbessertes Benutzererlebnis, höhere Effizienz und bessere Unterstützung komplexer Produktkataloge

   ![Neue Kategorieauswahl](/help/assets/CIF/category-picker.png)

* Bessere A11Y-Unterstützung für CIF-Kernkomponenten

### Fehlerbehebungen {#bug-fixes-august}

* Das Akkordeon des Kategoriefilters kann nicht geschlossen werden, nachdem es geöffnet wurde.

* Die Eigenschaft „Aktionsaufruf-Text“ ist im Produkt-Teaser fehlerhaft.

* CIF-JS-Fehler während des AEM CS-Bereitstellungsschritts

* Fehlerbehebung für den Produktzugriff für zugeordnete Produktlistenelemente

## Veröffentlichungsdatum: Juli 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.07.21 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.07.21.zip) |
| CIF-Kernkomponenten | 2.0.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-2.0.0) |
| CIF Venia-Referenz-Site | 2021.07.22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.07.22) |

### Neue Funktionen {#what-is-new-july}

* CIF-Kernkomponenten v2
   * Vereinfachte und verbesserte Konfigurationen für PDP/PLP-URL und SEO
   * Visueller Indikator für gestaffelte Produktdaten im Authoring-Modus für bessere Sichtbarkeit bevorstehender Änderungen
   * Neue Sitemap-Komponente für Inhalte und Commerce-Seiten

* Unterstützung für [Adobe Commerce Sensei Product Recommendation, powered by Adobe Sensei](https://business.adobe.com/de/products/magento/product-recommendations.html) in der AEM-Storefront mit vordefinierten oder direkt erstellten Empfehlungen

## Veröffentlichungsdatum: Juni 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.06.18 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.06.18.zip) |
| CIF-Kernkomponenten | 1.12.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.12.0) |
| CIF Venia-Referenz-Site | 2021.06.12 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.06.17) |

### Neue Funktionen {#what-is-new-june}

* Neue CIF-Produkt- und Kategoriereferenzdatentypen für Inhaltsfragmente (inkl. Benutzeroberflächenunterstützung für Produkt-/Kategorieauswahl)
* Neue Commerce-Inhaltsfragment-Kernkomponente
* Im AEM-Backend unterstützte E-Commerce-Volltext-Suche
* Commerce-Kernkomponenten unterstützen die Adobe Commerce Sensei Recs-Datenerfassung
* Verbesserte SEO-freundliche URLs für Kategorieseiten
* Unterstützung benutzerdefinierter HTTP-Header pro Website/Konfiguration

## Veröffentlichungsdatum: Mai 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.05.26 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.05.26.zip) |
| CIF-Kernkomponenten | 1.11.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.11.0) |
| CIF Venia-Referenz-Site | 2021.05.24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.05.24) |

### Neue Funktionen {#what-is-new-may}

* Unterstützung der Seitenumbrüche für zugehörige Inhalte in den Eigenschaften der Produktkonsole

### Fehlerbehebungen {#bug-fixes-may}

* Asset-Miniaturen werden nicht auf der Registerkarte „Asset“ der Produkteigenschaften angezeigt.

* Breadcrumb setzt Vorschaudaten in der Produktkonsole zurück.

## Veröffentlichungsdatum: April 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.04.22 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.04.22.zip) |
| CIF-Kernkomponenten | 1.10.0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021.04.22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-april}

* Unterstützung für Kategorie-UID – Dadurch werden Commerce-Integrationen von Drittanbietern für Systeme freigeschaltet, die Zeichenfolgen für Kategorie-IDs verwenden

* AEM-Erweiterung für PWA Studio inkl. Beispielintegration

* Neue CIF-Navigationskernkomponente, die die WCM-Navigationskernkomponente erweitert

### Fehlerbehebungen {#bug-fixes-april}

* Das Feld „Stammkategorie“ wurde auf der Registerkarte „Commerce“ in den Seiteneigenschaften von Kategorieseiten nicht angezeigt

## Veröffentlichungsdatum: März 2021 {#what-is-new-march}

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.9.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,9,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021.03.25 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neuerungen

* Unterstützung für Adobe Commerce 2.4.2

### Verbesserte Funktionen

* Verbesserte Wiederverwendbarkeit der Produktdetailkomponente für inhaltsgesteuerte Seiten

* Besseres Caching und weniger Backend-Aufrufe für PDPs

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: Februar 2021

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.8.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,8,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021.02.24 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-february}

* Produkterlebnis-Management: Reichern Sie Produktkatalogseiten individuell mit Experience Fragments an.

* Erweiterte Eigenschaften der Produktkonsole zum Anzeigen verknüpfter Assets und Experience Fragments, einschließlich Aktionen zum schnellen Navigieren zum zugehörigen Inhalt.

### Verbesserte Funktionen  {#what-is-improved-february}

* Verbesserte Client-seitige Datenschicht mit Produktbild-URL und Kategorieinformationen.

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: Januar 2021

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.7.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,7,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021.02.02 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-january}

* Produkterlebnis-Management: Neue Eigenschaftenseite „Commerce“ für Assets und Experience Fragments. Auf dieser Registerkarte können Sie Assets und Experience Fragments mit Produkten und Kategorien verknüpfen. Auf der Registerkarte werden auch Echtzeitdaten für verknüpfte Commerce-Objekte sowie ein Link zur Anzeige von Details in der Produktkonsole angezeigt.

### Verbesserte Funktionen  {#what-is-improved-january}

* Benutzerdaten werden nach der Authentifizierung an die Adobe-Client-Datenschicht gesendet.

* Mehrere Fehlerbehebungen.
