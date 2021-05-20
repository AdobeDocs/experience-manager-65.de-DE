---
title: AEM Content and Commerce - Versionshinweise 2021
description: AEM Content and Commerce - Versionshinweise 2021
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 8%

---

# Übersicht über die Commerce Integration Framework GitHub-Version

## Releasedatum: November 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,7,1 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,6,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,6,2 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-november}

* Autoren können Produktdetailseiten und Produktlistenseiten mit Produkten/Kategorien mit der neuen Option &quot;Ansicht mit Produkt/Kategorie&quot;im Sites-Editor in der Vorschau anzeigen.

* Autoren können Assets nach Produkt-SKU taggen und nach produktspezifischen Assets nach SKU suchen.

* Im Warenkorb hinzugefügte Couponunterstützung hinzufügen/entfernen.

* Braintree Zahlungsunterstützung in AEM Venia Storefront hinzugefügt.

### Verbesserte Funktionen {#what-is-improved-november}

* Die Kategorie-/Produktauswahl wurde verbessert, um die angegebene Magento Store-Ansicht in einem Multi-Store-Setup zu berücksichtigen.

* React-basierte Komponenten, die als NPM-Paket verfügbar sind. Dadurch können Entwickler das React-Komponenten-Paket als Abhängigkeit für ein neues React-Projekt verwenden, um die Anpassung vorhandener Komponenten zu ermöglichen oder neue React-basierte Komponenten zu entwickeln.

* GraphQL-Abfrageanpassung vereinfacht. Dadurch können Entwickler CIF-Kernkomponenten mit weniger Code anpassen.

## Releasedatum: Oktober 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,6,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,5,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,5,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-october}

* Vollständig bearbeitbare Vorlagen für Produktdetailseite und Produktlistenseite. Autoren können jetzt neue Vorlagen erstellen und Produktlisten- und Produktdetailkomponenten auf diese Vorlagen ziehen und dort ablegen. Zusätzlich zum Hinzufügen anderer Komponenten können Autoren jetzt auch das Layout dieser Vorlagen ändern, sodass sie unbegrenzte Möglichkeiten haben, erstaunliche Erlebnisse durch die Kombination von Marketing- und Commerce-Inhalten zu erstellen.

* Alle Authoring-freundlichen CIF-Kernkomponenten wurden verbessert, um [AEM Stilsystem](https://helpx.adobe.com/de/experience-manager/6-5/sites/authoring/using/style-system.html) zu unterstützen. Für die Produktlistenkomponente wurden Beispielstile bereitgestellt.

* Reaktionsbasierte Client-seitige Komponenten für die Kontoverwaltung. Diese Version unterstützt die folgenden Funktionen: Anmelden, Kennwort vergessen und Konto erstellen.

### Verbesserte Funktionen {#what-is-improved-october}

* Produktdetails und Produktlistenkomponenten wurden verbessert, um Platzhalterdaten anzuzeigen und Autoren eine Vorschau des Layouts zu ermöglichen, wenn diese Komponenten auf einer Vorlage/Seite platziert werden.

* Minicart- und Checkout-Komponenten verwenden jetzt React-Hooks für eine verbesserte Erweiterbarkeit.

## Releasedatum: September 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,5,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,4,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,4,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-september}

* Funktion mit mehreren Vorlagen, mit der Autoren bestimmte Produktdetailseiten oder Produktelisten anreichern können. Autoren können einfach eine benutzerdefinierte Produktdetailseite oder Produkteliste erstellen und mit der Produkt- oder Kategorieauswahl die benutzerdefinierte Seite einem bestimmten Produkt oder einer bestimmten Kategorie zuweisen.

* Multi-Catalog-Bindung, damit Autoren mehrere Kataloge in der AEM Produktkonsole binden können. Autoren können die Eigenschaften der Katalogbindung auch bearbeiten und anzeigen, nachdem sie die Bindung erstellt haben.

* React-basiertes clientseitiges Checkout und Mini-Warenkorb mit GraphQL zur Unterstützung einer kompletten einfachen Einkaufs-Journey.

* Die Komponente &quot;Checkout&quot;enthält Adressformulare, die Auswahl der Zahlung und die Auswahl der Versandmethode.

### Verbesserte Funktionen {#what-is-improved-september}

* Produkt-Teaser- und Produkt-Karussell-Komponenten unterstützen Produktvarianten.

## Releasedatum: August 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,4,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,3,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,3,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-august}

* Das Einbetten des CIF-Connectors in den CIF-Archetyp wurde optional gestaltet, um Entwicklern mehr Flexibilität zu bieten.

* CIF-Komponenten, die von &quot;Venia&quot;-spezifischen CSS-Stilen entkoppelt sind, damit Entwickler CSS-Stile ihrer Wahl anwenden können.

* Funktion für mehrere Stores/Sites, um die Verwendung von CIF-Kernkomponenten auf mehreren AEM Site-Strukturen zu ermöglichen und die zugrunde liegende GraphQL-Client-Implementierung zu ermöglichen, eine Verbindung zu verschiedenen Magento Store-/Store-Ansichten herzustellen.

* GraphQL-Zwischenspeicherung aktiviert für bestimmte GraphQL-Abfragen über HTTP-GET, um die Reaktionszeit zu verkürzen.

* Die Produktbeschreibungsansicht ist in AEM Produktekonsole aktiviert.

* Commerce Teaser erweitert die WCM-Teaser-Komponente, damit Autoren auch CTA-Felder zu einer Produktdetailseite oder einer Produktlistenseite hinzufügen können.

* Schaltfläche, mit der Autoren das Platzieren auf einer AEM und Verknüpfen zu einer AEM Seite, Produktdetailseite, Produktlistenseite oder einem externen Link zulassen können.

### Verbesserte Funktionen {#what-is-improved-august}

* Die Konfiguration des Magento-Stores wurde von OSGi in AEM Produktkonsole verschoben, um die Integrationseinrichtung benutzerfreundlicher zu gestalten.

## Releasedatum: Juli 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,3,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,2,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,2,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-july}

* Erster CIF-Archetyp, um Entwicklern verschiedene Bereitstellungsoptionen bereitzustellen: 1. Stellen Sie AEM Venia-Storefront 2 bereit. Strukturvorlage für ein neues Projekt bereitstellen 3. Verwenden von CIF-Elementen in einem vorhandenen Projekt

* Mehrstufige Katalognavigation zur Unterstützung der Navigation durch Kategorien und Unterkategorien.

* Paginierung auf Kategorieseiten für bessere UX.

* Client-seitiges Rendering des Preisattributs in den Komponenten Produktdetails und Produktliste , um das Rendering dynamischer Attribute zu unterstützen.

* Server-seitiges Produktkarussell zur Anzeige einer Liste mit vorgestellten Produkten im Karussell-Stil.

* Serverseitige Liste der vorgestellten Kategorien , um eine Liste der Kategorien auf einer AEM anzuzeigen.

### Verbesserte Funktionen {#what-is-improved-july}

* Unterstützung für Magento 2.3.2 und Fehlerbehebungen im Zusammenhang mit Produkteigenschaften werden in der Produktkonsole angezeigt.

## Releasedatum: Juni 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,2,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,1,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |

### Neue Funktionen {#what-is-new-june}

* AEM B2C-Storefront mit mobilem CSS-Styling, Landingpage, dynamischer Katalognavigation über Produkt- und Kategorieseiten, Produktsuchseite und Warenkorbfunktionen, um Commerce-Projekte zu starten und zu beschleunigen.

* CIF-Connector- und Authoring-Tools (Produktkonsole, Produktauswahl und Kategorieauswahl), mit denen Autoren Erlebnisse in AEM mit Commerce-Inhalten erstellen können.

* Erste Version der CIF-Kernkomponenten kompatibel mit Magento 2.3.1:
   * Produktdetails
   * Produktliste
   * Produkt-Teaser
   * Navigation
   * Produktsuche
   * Warenkorb (REST)

