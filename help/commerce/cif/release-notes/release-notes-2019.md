---
title: AEM Content and Commerce - Versionshinweise 2021
description: AEM Content and Commerce - Versionshinweise 2021
translation-type: tm+mt
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 8%

---

# Commerce Integration Framework GitHub - Versionshinweise

## Releasedatum: November 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 0,7,1 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,6,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,6,2 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-november}

* Autoren können Produktdetails und Produktseiten mit Produkten/Kategorien mit einer neuen Option &quot;Ansicht mit Produkt/Kategorie&quot;im Sites-Editor Vorschau.

* Autoren können Assets nach Produkt-SKU taggen und nach produktspezifischen Assets nach SKU suchen.

* hinzufügen/entfernen Sie den Coupon-Support, der im Warenkorb hinzugefügt wurde.

* Braintree Zahlungsunterstützung in AEM Venia Shop Front hinzugefügt.

### Verbesserte {#what-is-improved-november}

* Kategorien-/Produktwähler wurden verbessert, um die angegebene Magento Store-Ansicht in einem Multi-Store-Setup zu respektieren.

* React-basierte Komponenten als npm-Paket verfügbar. Dadurch können Entwickler das React-Komponenten-Paket als Abhängigkeit für ein neues React-Projekt verwenden, um die Anpassung vorhandener Komponenten zu ermöglichen oder neue react-basierte Komponenten zu entwickeln.

* Die Anpassung der GraphQL-Abfrage wurde vereinfacht. Dadurch können Entwickler CIF-Kernkomponenten mit weniger Code anpassen.

## Releasedatum: Oktober 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 0,6,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,5,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,5,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-october}

* Vollständig verlässliche Vorlagen für Produktdetailseite und Produktseite für die Liste. Autoren können jetzt neue Vorlagen erstellen und Produktdetailkomponenten per Drag &amp; Drop auf diese Vorlagen ziehen. Neben dem Hinzufügen anderer Komponenten können Autoren jetzt auch das Layout dieser Vorlagen ändern, sodass sie unbegrenzte Freiheit haben, erstaunliche Erlebnisse zu erstellen, die Marketing- und Commerce-Inhalte kombinieren.

* Alle autorfreundlichen CIF-Kernkomponenten wurden erweitert, um [AEM Style System](https://helpx.adobe.com/de/experience-manager/6-5/sites/authoring/using/style-system.html) zu unterstützen. Beispielstile wurden für die Produktkomponente &quot;Liste&quot;bereitgestellt.

* Kundenspezifische Komponenten für die Kontoverwaltung. Diese Version unterstützt die folgenden Funktionen: Melden Sie sich an, vergessen Sie das Kennwort und erstellen Sie ein Konto.

### Verbesserte {#what-is-improved-october}

* Produktdetails und Produktkomponenten wurden erweitert, um Platzhalterdaten anzuzeigen und Autoren eine Vorschau des Layouts bereitzustellen, wenn diese Listen auf einer Vorlage/Seite platziert werden.

* Die Komponenten Minicart und Checkout verwenden jetzt React-Haken, um die Erweiterbarkeit zu verbessern.

## Releasedatum: September 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 0,5,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,4,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,4,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-september}

* Funktion mit mehreren Vorlagen, mit der Autoren bestimmte Produktdetailseiten oder Produktseiten erweitern können. Autoren können auf einfache Weise eine benutzerspezifische Produktdetailseite oder Produktseite erstellen und mit der Produkt- oder Kategorie-Auswahl die benutzerspezifische Liste einem bestimmten Produkt oder einer bestimmten Kategorie zuweisen.

* Bindung mehrerer Kataloge, damit Autoren mehrere Kataloge in der AEM Produktkonsole binden können. Autoren können die Katalogbindungseigenschaften auch nach dem Erstellen der Bindung bearbeiten und Ansichten vornehmen.

* React-basierte clientseitige Checkout- und Mini-Warenkorb mit GraphQL zur Unterstützung einer kompletten grundlegenden Journey.

* Die Kassengangkomponente umfasst Adressformulare, Zahlungsauswahl und Versandmethodenauswahl.

### Verbesserte {#what-is-improved-september}

* Die Komponenten Teaser und Product Carousel unterstützen Produktvarianten.

## Releasedatum: August 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 0,4,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,3,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,3,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-august}

* Das Einbetten von CIF Connector in CIF Archetype wurde optional, um Entwicklern mehr Flexibilität zu bieten.

* CIF-Komponenten entkoppelt von &quot;Venia&quot;-spezifischen CSS-Stilen, damit Entwickler CSS-Stile ihrer Wahl anwenden können.

* Multi-Store/Site-Funktion, um die Verwendung von CIF-Kernkomponenten auf mehreren AEM Sitestrukturen zu ermöglichen und die zugrunde liegende GraphQL-Client-Implementierung zu ermöglichen, eine Verbindung zu verschiedenen Magento Store/Store-Ansichten herzustellen.

* GraphQL-Zwischenspeicherung für bestimmte GraphQL-Abfragen über HTTP-GET aktiviert, um die Reaktionszeit zu verkürzen.

* Ansicht der Produktbeschreibung in AEM Produktkonsole aktiviert.

* Commerce Teaser erweitert die WCM Teaser-Komponente, sodass Autoren auch CTA-Felder zu einer Produktdetailseite oder Produktseite hinzufügen können.

* Schaltfläche, mit der Autoren eine AEM Seite platzieren und entweder eine Verknüpfung zu einer AEM, Produktdetailseite, Produktseite oder zu einer Liste eines externen Links herstellen können.

### Verbesserte {#what-is-improved-august}

* Die Konfiguration des Magento-Stores wurde von OSGi in AEM Produktkonsole verschoben, um die Integration noch autorfreundlicher zu gestalten.

## Releasedatum: Juli 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 0,3,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,2,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,2,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-july}

* Erster CIF-Archetyp, der Entwicklern mehrere Bereitstellungsoptionen bereitstellt: 1. Stellen Sie AEM Venia Store 2 bereit. Stellen Sie Gerüste für ein neues Projekt bereit 3. CIF-Elemente in einem vorhandenen Projekt verwenden

* Mehrstufige Katalognavigation zur Unterstützung der Navigation durch Kategorien und Untergruppen.

* Paginierung auf Seiten der Kategorie für eine bessere UX.

* Clientseitige Wiedergabe des Preisattributs in Produktdetails und Produktkomponenten, um die Liste dynamischer Attribute zu unterstützen.

* Serverseitiges Karussell zur Anzeige der Liste von Sonderprodukten im Karussell-Stil.

* Serverseitige Liste der speziellen Kategorie, um die Liste der Kategorien auf einer AEM anzuzeigen.

### Verbesserte {#what-is-improved-july}

* Unterstützung für Magento 2.3.2 und Fehlerbehebungen im Zusammenhang mit Produkteigenschaften werden in der Produktkonsole angezeigt.

## Releasedatum: Juni 2019

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Anschluss | 0,2,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,1,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |

### Neue Funktionen {#what-is-new-june}

* AEM B2C-Schaufenster mit dem mobilen ersten Venia CSS-Stil, der Landingpage, der dynamischen Katalognavigation über Produkt- und Kategorien-Seiten, der Produktsuchseite und den Funktionen des Einkaufswagens, um Handelsprojekte zu starten und zu beschleunigen.

* CIF Connector- und Authoring-Werkzeuge (Produktkonsole, Produktauswahl und Kategorie-Auswahl), mit denen Autoren Erlebnisse in AEM mit Commerce-Inhalten erstellen können.

* Erste Version der CIF-Kernkomponenten, die mit Magento 2.3.1 kompatibel sind:
   * Produktdetails
   * Produktliste
   * Produkt-Teaser
   * Navigation
   * Produktsuche
   * Warenkorb (REST)

