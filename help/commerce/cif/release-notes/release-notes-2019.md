---
title: AEM Content and Commerce – Versionshinweise 2019
description: Versionshinweise zu Adobe Experience Manager Content and Commerce 2019.
exl-id: 7e61a75d-6b35-46ee-b88a-444c10b2708f
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 75%

---

# Übersicht über die GitHub-Version von Commerce Integration Framework

## Releasedatum: November 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.7.1 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.6.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.6.2 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-november}

* Autoren können Produktdetailseiten und Produktlistenseiten mit Produkten/Kategorien mit der neuen Option „Mit Produkt/Kategorie anzeigen“ im Sites-Editor in der Vorschau anzeigen.

* Autoren können Assets mit der Produkt-SKU taggen und über die SKU nach produktspezifischen Assets suchen.

* Sie können im Warenkorb hinzugefügte Couponunterstützung hinzufügen oder entfernen.

* Braintree-Zahlungsunterstützung wurde in der AEM Venia-Storefront hinzugefügt.

### Verbesserte Funktionen {#what-is-improved-november}

* Kategorie-/Produkt-Wähler wurden verbessert, um die angegebene Adobe Commerce Store-Ansicht in einem Multi-Store-Setup zu berücksichtigen.

* React-basierte Komponenten sind als NPM-Paket verfügbar. Dadurch können Entwickler das React-Komponentenpaket als Abhängigkeit für ein neues React-Projekt verwenden, um die Anpassung vorhandener Komponenten zu ermöglichen oder neue React-basierte Komponenten zu entwickeln.

* Die Anpassung der GraphQL-Abfrage wurde vereinfacht. Dadurch können Entwickler CIF-Kernkomponenten mit weniger Code anpassen.

## Releasedatum: Oktober 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.6.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.5.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.5.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-october}

* Vollständig bearbeitbare Vorlagen für die Produktdetailseite und die Produktlistenseite. Autoren können jetzt Vorlagen erstellen und Produktlisten- und Produktdetailkomponenten auf diese Vorlagen ziehen und dort ablegen. Zusätzlich zum Hinzufügen anderer Komponenten können Autoren jetzt auch das Layout dieser Vorlagen ändern, sodass sie unbegrenzte Möglichkeiten haben, erstaunliche Erlebnisse durch die Kombination von Marketing- und Commerce-Inhalten zu erstellen.

* Alle benutzerfreundlichen CIF-Kernkomponenten wurden verbessert, sodass sie nun das [AEM-Stilsystem](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/siteandpage/style-system.html?lang=de) unterstützen. Für die Produktlistenkomponente wurden Beispielstile bereitgestellt.

* React-basierte Client-seitige Komponenten für die Kontoverwaltung. Diese Version unterstützt die folgenden Funktionen: Anmelden, Kennwort vergessen und Konto erstellen.

### Verbesserte Funktionen {#what-is-improved-october}

* Produktdetail- und Produktlistenkomponenten wurden verbessert, um Platzhalterdaten anzuzeigen und Autoren eine Vorschau des Layouts zu bieten, wenn diese Komponenten auf einer Vorlage/Seite platziert werden.

* Minicart- und Checkout-Komponenten verwenden jetzt React-Hooks für eine verbesserte Erweiterbarkeit.

## Veröffentlichungsdatum: September 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.5.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.4.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.4.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-september}

* Mit der Funktion für mehrere Vorlagen können Autoren eine bestimmte Produktdetailseite oder Produkteliste anreichern. Autoren können einfach eine benutzerdefinierte Produktdetailseite oder Produkteliste erstellen und mit der Produkt- oder Kategorieauswahl die benutzerdefinierte Seite einem bestimmten Produkt oder einer bestimmten Kategorie zuweisen.

* Bindung an mehrere Kataloge, mit der Autoren mehrere Kataloge in der AEM-Produktkonsole binden können. Autoren können die Eigenschaften der Katalogbindung auch bearbeiten und anzeigen, nachdem sie die Bindung erstellt haben.

* React-basierte Client-seitige Checkout- und Minicart-Komponenten mit GraphQL zur Unterstützung eines kompletten einfachen Einkaufs.

* Die Komponente &quot;Checkout&quot;enthält Adressformulare, die Auswahl der Zahlung und die Auswahl der Versandmethode.

### Verbesserte Funktionen {#what-is-improved-september}

* Produkt-Teaser- und Produktkarussell-Komponenten unterstützen Produktvarianten.

## Releasedatum: August 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.4.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.3.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.3.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-august}

* Das Einbetten CIF Connectors in CIF Archetyp ist optional, damit Entwickler flexibler arbeiten können.

* CIF-Komponenten wurden von Venia-spezifischen CSS-Stilen entkoppelt, damit Entwickler CSS-Stile ihrer Wahl anwenden können.

* Funktion für mehrere Stores/Sites, um die Verwendung von CIF-Kernkomponenten auf mehreren AEM-Site-Strukturen zu ermöglichen, sodass die zugrunde liegende GraphQL-Client-Implementierung eine Verbindung mit verschiedenen Store/Store-Ansichten von Adobe Commerce herstellen kann.

* Die GraphQL-Zwischenspeicherung ist für bestimmte GraphQL-Abfragen über HTTP-GET aktiviert, um die Reaktionszeit zu verkürzen.

* Die Ansicht &quot;Produktbeschreibung&quot;ist in der AEM Produktekonsole aktiviert.

* Commerce Teaser erweitert die WCM-Teaser-Komponente, sodass Autoren auch CTA-Felder zu einer Produktdetailseite oder einer Produktlistenseite hinzufügen können.

* Schaltfläche, mit der Autoren auf einer AEM-Seite platzieren oder mit einer AEM-Seite, Produktdetailseite, Produktlistenseite oder einem externen Link verknüpfen können.

### Verbesserte Funktionen {#what-is-improved-august}

* Die Adobe Commerce Store-Konfiguration wurde von OSGi in die AEM Product Console verschoben, um die Einrichtung der Integration noch autorfreundlicher zu gestalten.

## Veröffentlichungsdatum: Juli 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.3.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.2.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.2.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-july}

* Erster CIF-Archetyp, um Entwicklern verschiedene Bereitstellungsoptionen anzubieten: 1. Bereitstellen der AEM Venia-Storefront 2. Bereitstellen der Strukturvorlage für ein neues Projekt 3. Verwenden von CIF-Elementen in einem vorhandenen Projekt

* Mehrstufige Katalognavigation zur Unterstützung der Navigation durch Kategorien und Unterkategorien.

* Seitenumbruch auf Kategorieseiten für bessere Benutzererlebnisse.

* Client-seitiges Rendering des Preisattributs in den Komponenten „Produktdetails“ und „Produktliste“, um das Rendering dynamischer Attribute zu unterstützen.

* Server-seitiges Produktkarussell , um eine Liste mit vorgestellten Produkten im Karussell-Stil anzuzeigen.

* Serverseitige Liste der vorgestellten Kategorien , um eine Liste der Kategorien auf einer AEM anzuzeigen.

### Verbesserte Funktionen {#what-is-improved-july}

* Die Unterstützung für Adobe Commerce 2.3.2 und Fehlerbehebungen im Zusammenhang mit der Anzeige von Produkteigenschaften in der Produktkonsole.

## Veröffentlichungsdatum: Juni 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.2.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.1.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |

### Neue Funktionen {#what-is-new-june}

* AEM-B2C-Storefront mit Venia-CSS-Stilen für mobile Geräte, Landingpage, dynamischer Katalognavigation über Produkt- und Kategorieseiten, Produktsuchseite und Warenkorbfunktionen, um Commerce-Projekte zu starten und zu beschleunigen.

* CIF-Connector- und Authoring-Tools (Produktkonsole, Produktauswahl und Kategorieauswahl), mit denen Autoren Erlebnisse in AEM mit Commerce-Inhalten erstellen können.

* Erste Version der CIF-Kernkomponenten, die mit Adobe Commerce 2.3.1 kompatibel sind:
   * Produktdetails
   * Produktliste
   * Produkt-Teaser
   * Navigation
   * Produktsuche
   * Warenkorb (REST)
