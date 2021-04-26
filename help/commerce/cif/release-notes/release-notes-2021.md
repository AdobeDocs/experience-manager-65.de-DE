---
title: AEM Content and Commerce - Versionshinweise 2021
description: AEM Content and Commerce - Versionshinweise 2021
translation-type: tm+mt
source-git-commit: 2d0b52dbf85e1fbe91c09a8366744aa77f25cd73
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 15%

---

# Commerce Integration Framework GitHub - Versionshinweise

## Übersicht über die Systemanforderungen

Überprüfen Sie die Mindestsystemanforderungen in der unten stehenden Tabelle für die CIF-Version, die Sie derzeit verwenden oder für die Zukunft verwenden möchten.

**CIF-Add-on jetzt über  [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) erhältlich. Der alte AEM CIF Connector befindet sich im Wartungsmodus und sollte nicht mehr verwendet werden. Bitte migrieren Sie zum neuen CIF-Add-on.**

| Komponente | Systemanforderungen |
|:-------|:-----:|
| CIF-Add-on | Minimum: AEM 6.5.7, Magento 2.3.5 GraphQL-Schema |
| CIF-Kernkomponenten | [Systemanforderungen](https://github.com/adobe/aem-core-cif-components/blob/master/VERSIONS.md) |
| AEM-Projektarchetyp | [Systemanforderungen](https://github.com/adobe/aem-project-archetype/blob/master/VERSIONS.md) |

## Releasedatum: April 2021

| Komponente | Version | Details |
|:-------|:-----:|---------------------:|
| CIF-Add-on | v2021.04.22 | [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Faem-commerce-addon-65-2021.04.22.zip) |
| CIF-Kernkomponenten | 1,10,0 | [GitHub](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Venedig-Referenzseite | 2021,04,22 | [GitHub](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neuerungen {#what-is-new-april}

* **CIF-Add-on jetzt über  [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) erhältlich. Der alte AEM CIF Connector befindet sich im Wartungsmodus und sollte nicht mehr verwendet werden. Bitte migrieren Sie zum neuen CIF-Add-on.**

* Unterstützung für Kategorie-UID - Hierdurch werden Commerce-Integrationen von Drittanbietern für Systeme freigeschaltet, die Strings für Kategorien-IDs verwenden

* AEM Erweiterung für PWA Studio incl. Beispielintegration

* Neue CIF-Navigationskernkomponente, die die WCM-Navigationskernkomponente erweitert

* Visueller Indikator für gestaffelte Katalogdaten im AEM Store

### Fehlerbehebungen {#bug-fixes-april}

* Das Feld &quot;Stamm-Kategorie&quot;wurde nicht auf der Registerkarte &quot;Handel&quot;in den Seiteneigenschaften der Kategorien angezeigt

## Releasedatum: März 2021 {#what-is-new-march}

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 1.9.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.9.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Venedig-Referenzseite | 2021,03,25 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neuerungen

* Unterstützung für Magento 2.4.2

### Verbesserte Funktionen

* Verbesserte Wiederverwendbarkeit der Produktdetailkomponente für inhaltsgesteuerte Seiten

* Bessere Zwischenspeicherung und weniger Backend-Aufrufe für PDPs

* Mehrere Fehlerkorrekturen.

## Releasedatum: Februar 2021

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 1.8.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.8.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Venedig-Referenzseite | 2021,02,24 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neuerungen {#what-is-new-february}

* Produkt-Experience-Management: Richten Sie Produktkatalogseiten einzeln mit Erlebnisfragmenten ein.

* Die Eigenschaften der Produktkonsole wurden erweitert, um verknüpfte Assets und Erlebnisfragmente anzuzeigen, einschließlich Aktionen zum schnellen Navigieren zu den zugehörigen Inhalten.

### Verbesserte Funktionen  {#what-is-improved-february}

* Verbesserte clientseitige Datenschicht mit Produkt-Image-URL und Kategorieinformationen

* Mehrere Fehlerkorrekturen.

## Releasedatum: Januar 2021

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 1.7.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.7.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Venedig-Referenzseite | 2021,02,02 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neuerungen {#what-is-new-january}

* Produkt-Experience-Management: Neue Registerkarte &quot;Commerce&quot;-Eigenschaft für Assets und Erlebnisfragmente. Auf dieser Registerkarte können Sie Assets und Erlebnisfragmente mit Produkten und Kategorien verknüpfen. Auf der Registerkarte werden auch Echtzeitdaten für verknüpfte Commerce-Objekte und ein Link zur Anzeige von Details in der Produktkonsole angezeigt.

### Verbesserte Funktionen  {#what-is-improved-january}

* Senden Sie Benutzerdaten nach der Authentifizierung an die Adobe Client Data Layer.

* Mehrere Fehlerkorrekturen.
