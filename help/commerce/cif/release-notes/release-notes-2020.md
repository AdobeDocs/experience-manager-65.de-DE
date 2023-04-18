---
title: AEM Content and Commerce – Versionshinweise 2020
description: AEM Content and Commerce – Versionshinweise 2020
exl-id: 440ecd8e-55dc-4606-8678-c65cda1d2b3a
source-git-commit: e1a0b114ce16d0e7f6a464e9d30b8f111297bcc6
workflow-type: tm+mt
source-wordcount: '1328'
ht-degree: 100%

---

# Übersicht über die GitHub-Version von Commerce Integration Framework

## Veröffentlichungsdatum: November 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.6.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.6.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.12.01 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-november}

* Vorlagenvererbung wurde zu einer bestimmten Kategorieseite hinzugefügt. Diese Funktion verbessert die Effizienz der Business-Anwender, da sie es ermöglicht, dass alle Unterkategorien die Vorlage übernehmen können, die für eine bestimmte übergeordnete Kategorie erstellt wurde.

* Venia-Referenz-Storefront wurde aktualisiert, um Experience Fragment für die Fußzeile zu verwenden. Business-Anwender können die Fußzeile einer Seite mit AEM-Authoring-Tools bearbeiten.

### Verbesserte Funktionen {#what-is-improved-november}

* Die Checkout-Komponente wurde verbessert, um Käufern die Möglichkeit zu geben, das Zielland einzugeben, um Abrechnungs-/Versandadressen außerhalb der USA zuzulassen.

* Die Navigationskomponente wurde erweitert, sodass sie die Adobe-Client-Datenschicht abzudeckt.

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: Oktober 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.5.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.5.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.10.27 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-october}

* Eine neue Karussellkomponente für Kategorien wurde hinzugefügt, damit Business-Anwender diese Komponente auf AEM-Inhaltsseiten ziehen können, um Inhaltsseiten mit Commerce-Daten anzureichern.

* CIF-Kernkomponenten wurden erweitert, sodass sie die Adobe-Client-Datenschicht durch Senden von Commerce-Daten einbinden. Die Adobe-Client-Datenschicht ist eine standardisierte Methode zur Erfassung von Daten und zur Weitergabe der Daten für digitale Analysen und Reporting-Server. Weitere Informationen finden Sie unter [Adobe-Client-Datenschicht](https://github.com/adobe/adobe-client-data-layer/wiki).

* Produktdetailseiten und Produktlistenseiten wurden erweitert, um SEO-Metadaten (wie Titel, Meta-Beschreibung, Meta-Schlüsselwörter) automatisch auszufüllen, die über die Adobe Commerce-Benutzeroberfläche für Admins konfiguriert wurden.

* Fehler der Commerce-Teaser-Komponente wurde behoben.

## Veröffentlichungsdatum: September 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.4.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.4.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.10.2 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-september}

* Unterstützt Abfragen für das Adobe Commerce 2.4.0-Schema.

* Funktionen für Kontoinformationen wurden hinzugefügt, damit Käufer personenbezogene Daten aktualisieren können.

* Ein Seitenumbruchstil mit verzögertem Laden wurde für die Produktlisten- und Suchergebnisseiten implementiert, damit Entwickler diese Komponenten so konfigurieren können, dass die Schaltfläche „Mehr laden“ als Seitenumbruchstil angezeigt wird.

* Die Seite zum Zurücksetzen des Kennworts wurde implementiert, damit Käuferinnen und Käufer ihr Kontokennwort aktualisieren/zurücksetzen können.

* Unterstützung für gebündelte Produktarten ist verfügbar.

* Entwickler können die HTML-Tags der Komponenten für Produktkarussells, verwandte Produkte und vorgestellte Kategorielisten konfigurieren, um SEO-Best-Practices zu befolgen.

* Fehler bei „Mein Konto“ wurde behoben.

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: August 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.3.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.3.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.9.2 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-august}

* Breadcrumb-Komponente wurde zur Unterstützung von Inhalts- und Commerce-Seiten hinzugefügt.

* Die Registerkarte „Commerce“ wurde in den Seiteneigenschaften hinzugefügt, um CIF-Eigenschaften für Landingpages und Experience Fragments anzuzeigen.

* Die Suchleistenkomponente wurde verbessert, sodass sie die Option zur Anzeige von Platzhaltertext zu unterstützt

* Zusätzliche Flexibilität bei Produkt- und Produkt-Teaser-Komponenten zur Unterstützung einfacher Anpassungen.

* Mehr Flexibilität, um die standardmäßige CTA-Schaltflächenbeschriftung für die Produkt-Teaser-Komponente zu überschreiben und zu konfigurieren.

* Die Adressbuchkomponente wurde verbessert, um registrierten Käufern die Möglichkeit zu geben, beim Checkout im Adressbuch gespeicherte Versand- und Rechnungsadressen auszuwählen.

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: Juli 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.2.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.2.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.8.14 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-july}

* Die CIF Venia-Referenz-Site wurde aus dem CIF-Archetyp-Repository extrahiert und ist jetzt ein eigenständiges GitHub-Repository.

* Der CIF-Archetyp wurde mit dem AEM-Projektarchetyp zusammengeführt. Verwenden Sie für neue Projekte den [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) als Ausgangspunkt.

* Adressbuchverwaltung wurde hinzugefügt, damit angemeldete Benutzer ihre Adressen verwalten können.

* Die Benutzeroberfläche der CIF-Cloud-Konfiguration unterstützt das Veröffentlichen/Rückgängigmachen der Veröffentlichung von Aktionen.

### Verbesserte Funktionen {#what-is-improved-july}

* Die Anmelde-Komponente wurde in die Benutzer-Dropdown-Liste verschoben, um einfachen Zugriff zu ermöglichen.

* Das Paket „aem-core-cif-response-components“ wurde vereinfacht.

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: Juni 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.1.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.1.1 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.11.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-june}

Dies ist die erste Version der CIF-Kernkomponenten, die von Adobe Experience Manager unterstützt wird.

* Die Produktsortierung wurde auf den Produktlisten- und Suchergebnisseiten hinzugefügt, damit Käufer nach Relevanz, Preis und Produktname sortieren können.

* Kategoriefilterung wurde als Facette hinzugefügt, damit Käufer nach Kategorie filtern können.

* Eine Zuordnung von Service und Benutzer wurde als Teil der Sicherheitsanforderung hinzugefügt, um den Zugriff auf „/conf“ über Service-Benutzer und nicht durch direkte Bearbeitung von ACLs sicherzustellen. CIF-Kernkomponenten müssen jetzt einen Service-Benutzer verwenden, um auf Konfigurationen zuzugreifen.

### Verbesserte Funktionen {#what-is-improved-june}

* Die Produktlistenseite und die Suchergebnisseite zeigen die Gesamtanzahl der Elemente an. Die Anzahl der Elemente wird aktualisiert, wenn der Käufer Filter anwendet.

* Die Facettensuche wurde durch die Kombination von Kategorieabfrage und Produktsuchabfrage optimiert.

* Die Kategorie-/Produktauswahl für die Seitenvorschau berücksichtigt „cq:catalogPath“.

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: Mai 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.0.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.0.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.11.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-may}

* Unterstützt Abfragen für das Adobe Commerce 2.3.5-Schema.

* Die Unterstützung für die Facettensuche wurde der Suchseite und der Produktlistenseite hinzugefügt, damit Käufer Suchergebnisse anhand von Produktfacetten filtern können.

* Ein neuer OSGi-Service wurde hinzugefügt, um PDP/PLP-URLs für SEO-Zwecke anzupassen. Weiterführende Informationen dazu finden Sie in dieser [Dokumentation](https://github.com/adobe/aem-core-cif-components/wiki/configuration).

* Die Produktbindung wird automatisch erstellt, wenn eine Cloud-Konfiguration erstellt wird.

### Verbesserte Funktionen

* Die Cloud-Konfiguration wurde erweitert, um die Aktion „Ordner erstellen“ anzuzeigen.

* Es wurden mehrere Fehlerbehebungen vorgenommen.

## Veröffentlichungsdatum: April 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.10.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.10.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.10.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-april}

* Konfigurationseinstellungen für den CIF-Connector wurden vereinheitlicht und vereinfacht. Weitere Details finden Sie unter [Erste Schritte](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html) oder [Neue AEM-CIF-Projekteinrichtung](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html#!AdobeDocs/commerce-cif-documentation/master/getting-started/02-new-cif-project.md).

### Verbesserte Funktionen {#what-is-improved-april}

* Der Warenkorb- und der Checkout-Ablauf wurden erweitert, um registrierte Käufer zu unterstützen.

* Erweiterte Internationalisierungsunterstützung für alle Komponenten.

* Unterstützung für gruppierte Produkte und virtuelle Produkte ist verfügbar.

* Die Komponenten für verwandte Produkte, das Produktkarussell und vorgestellte Kategorien wurden verbessert, um optionale Titel zu unterstützen.

* Es wurden mehrere Fehlerbehebungen vorgenommen.

## Veröffentlichungsdatum: Februar 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.9.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.9.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.9.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-february}

* Unterstützt Abfragen für das Adobe Commerce 2.3.4-Schema.

* Suchunterstützung wurde in der Kategorieauswahl hinzugefügt.

* Seitenumbruch in der Kategorielistenkomponente, um große Katalogsätze zu unterstützen.

### Verbesserte Funktionen {#what-is-improved-february}

* Der Warenkorb wurde um die Anzeige von Rabatten erweitert.

* Komponenten für Produktdetails, Produkt-Teaser und Produktlisten unterstützen die Anzeige erweiterter Preisinformationen.

* Die Produktsuche in der Produktkonsole und in der Produktauswahl wurde verbessert.

* Es wurden mehrere Fehlerbehebungen vorgenommen.

## Veröffentlichungsdatum: Januar 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.8.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.8.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.7.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-january}

* Experience-Fragment-Komponente (XF) wurde hinzugefügt, damit Kunden XF in ihrem Commerce-Projekt erstellen können.

* Die Kennwortfunktionalität wurde geändert, die in „Mein Konto“ verfügbar ist.

* i18n-Unterstützung für Server-seitige AEM-CIF-Kernkomponenten.

* Generische Komponente für verwandte Produkte ist verfügbar.

### Verbesserte Funktionen {#what-is-improved-january}

* Unterstützung für die Anzeige der CTA-Schaltfläche im Produkt-Teaser.

* Option zum Ändern/Auswählen von Bildern in der Komponente für vorgestellte Kategorienlisten.

* Option zum Ausblenden/Anzeigen von Titel/Banner in der Produktlistenkomponente.

* Drag-and-Drop-Funktion wurde auf die Produktkarussellkomponente angewendet.

* Es wurden mehrere Fehlerbehebungen vorgenommen.
