---
title: AEM Content and Commerce - Versionshinweise 2021
description: AEM Content and Commerce - Versionshinweise 2021
source-git-commit: 99636664a49da3ac5d236db5a1185ad6659ee255
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 15%

---

# Übersicht über die Commerce Integration Framework GitHub-Version

## Übersicht über die Systemanforderungen

Überprüfen Sie die Mindestanforderungen in der folgenden Tabelle für die CIF-Version, die Sie derzeit verwenden oder in Zukunft verwenden möchten.

**Mit der Version vom April haben wir den CIF Connector von GitHub durch das CIF-Add-on ersetzt, das auf der Adobe [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar ist. Der Wechsel zum Add-on bringt große Vorteile für Projekte mit sich:

* Die meisten neuen Funktionen stehen ab AEM 6.5 sofort zur Verfügung (keine Wartezeiten mehr auf Feature Side Port).
* Einfache Aktualisierung auf neue Add-on-Versionen
* Bereit für Cloud Service

Der alte AEM CIF Connector befindet sich im Wartungsmodus und sollte nicht mehr verwendet werden. Ersetzen Sie den CIF-Connector durch das neue CIF-Add-on. Für die meisten Projekte sollte einfach ein Package-Ersatz möglich sein. **

| Komponente | Systemanforderungen |
|:-------|:-----:|
| CIF-Add-on | Minimum: AEM 6.5.7, Magento 2.3.5 GraphQL-Schemata |
| CIF-Kernkomponenten | [Systemanforderungen](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM-Projektarchetyp | [Systemanforderungen](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: Mai 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021,05,26 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.05.26.zip) |
| CIF-Kernkomponenten | 1,11,0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.11.0) |
| CIF Venia-Referenz-Site | 2021,05,24 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.05.24) |

### Neue Funktionen {#what-is-new-may}

* Paginierungsunterstützung für verknüpften Inhalt in den Eigenschaften der Produktkonsole

### Fehlerbehebungen {#bug-fixes-may}

* Asset-Miniaturansichten werden nicht auf der Registerkarte &quot;Asset&quot;der Produkteigenschaften angezeigt

* Breadcrumb setzt Vorschaudaten in der Produktkonsole zurück

## Releasedatum: April 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | 2021.04.22 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.04.22.zip) |
| CIF-Kernkomponenten | 1,10,0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021.04.22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-april}

* Unterstützung für Kategorie-UID - Dadurch werden Commerce-Integrationen von Drittanbietern für Systeme freigeschaltet, die Zeichenfolgen für Kategorie-IDs verwenden

* AEM Erweiterung für PWA Studio inkl. Beispielintegration

* Neue CIF-Navigationskernkomponente, die die WCM-Navigationskernkomponente erweitert

* Visueller Indikator für gestaffelte Katalogdaten in AEM Storefront

### Fehlerbehebungen {#bug-fixes-april}

* Das Feld der Stammkategorie wurde nicht auf der Registerkarte &quot;Commerce&quot;in den Seiteneigenschaften von Kategorieseiten angezeigt

## Releasedatum: März 2021 {#what-is-new-march}

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,9,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,9,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021,03,25 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neuerungen

* Unterstützung für Magento 2.4.2

### Verbesserte Funktionen

* Verbesserte Wiederverwendbarkeit der Produktdetailkomponente für inhaltsgesteuerte Seiten

* Besseres Caching und weniger Backend-Aufrufe für PDPs

* Mehrere Fehlerbehebungen.

## Releasedatum: Februar 2021

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,8,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,8,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021,02,24 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-february}

* Produkt-Experience-Management: Reichern Sie Produktkatalogseiten individuell mit Experience Fragments an.

* Die Eigenschaften der Produktkonsole wurden erweitert, um verknüpfte Assets und Experience Fragments anzuzeigen, einschließlich Aktionen zur schnellen Navigation zum zugehörigen Inhalt.

### Verbesserte Funktionen {#what-is-improved-february}

* Verbesserte Client-seitige Datenschicht mit Produkt-Bild-URL und Kategorieinformationen.

* Mehrere Fehlerbehebungen.

## Releasedatum: Januar 2021

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,7,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,7,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2021,02,02 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-january}

* Produkt-Experience-Management: Neue Registerkarte mit der Eigenschaft &quot;Commerce&quot;für Assets und Experience Fragments. Auf dieser Registerkarte können Sie Assets und Experience Fragments mit Produkten und Kategorien verknüpfen. Auf der Registerkarte werden auch Echtzeitdaten für verknüpfte Commerce-Objekte und ein Link zur Anzeige von Details in der Produktkonsole angezeigt.

### Verbesserte Funktionen {#what-is-improved-january}

* Senden Sie Benutzerdaten nach der Authentifizierung an die Adobe Client-Datenschicht.

* Mehrere Fehlerbehebungen.
