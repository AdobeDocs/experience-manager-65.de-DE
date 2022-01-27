---
title: AEM Content and Commerce - Versionshinweise 2021
description: AEM Content and Commerce - Versionshinweise 2021
exl-id: 440ecd8e-55dc-4606-8678-c65cda1d2b3a
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '1328'
ht-degree: 10%

---

# Übersicht über die Commerce Integration Framework GitHub-Version

## Releasedatum: November 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,6,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,6,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.12.01 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-november}

* Vorlagenvererbung wurde zu einer bestimmten Kategorieseite hinzugefügt. Diese Funktion verbessert die Effizienz der Unternehmensbenutzer, da sie es allen Unterkategorien ermöglicht, die Vorlage zu übernehmen, die für eine bestimmte oberste Kategorie erstellt wurde.

* Venia-Referenz-Storefront aktualisiert, um Experience Fragment für die Fußzeile zu verwenden. Geschäftsbenutzer können die Fußzeile mit AEM Authoring-Tools bearbeiten.

### Verbesserte Funktionen {#what-is-improved-november}

* Die Checkout-Komponente wurde verbessert, um Käufern die Möglichkeit zu geben, in das Zielland zu gelangen, um Abrechnungs-/Versandadressen außerhalb der USA zuzulassen.

* Navigationskomponente erweitert, um die Client-Datenschicht der Adobe zu hydrieren.

* Mehrere Fehlerbehebungen.

## Releasedatum: Oktober 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,5,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,5,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.10.27 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-october}

* Neue Karussellkomponente für Kategorie hinzugefügt, damit geschäftliche Benutzer diese Komponente per Drag-and-Drop auf AEM Inhaltsseiten verschieben können, um Inhaltsseiten mit Commerce-Daten anzureichern.

* CIF-Kernkomponenten wurden erweitert, um die Adobe Client Data Layer durch Senden von Commerce-Daten zu hydrieren. Die Adobe Client-Datenschicht ist eine standardisierte Methode zur Erfassung von Daten und zur Kommunikation der Daten mit digitalen Analyse- und Reporting-Servern. Weitere Informationen finden Sie unter [Adobe Client-Datenschicht](https://github.com/adobe/adobe-client-data-layer/wiki).

* Produktdetailseiten und Produktlisten wurden erweitert, um SEO-Metadaten (wie Titel, Meta-Beschreibung, Meta-Keywords) automatisch zu füllen, die über die Administrator-Benutzeroberfläche von Adobe Commerce konfiguriert wurden.

* Fehler der Commerce-Teaser-Komponente behoben.

## Releasedatum: September 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,4,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,4,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.10.2 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-september}

* Unterstützt Abfragen für das Adobe Commerce 2.4.0-Schema.

* Kontoinformationen wurden hinzugefügt, damit Käufer personenbezogene Daten aktualisieren können.

* Seitenumbruch beim verzögerten Laden wurde für die Seiten Produktliste und Suchergebnisse implementiert, damit Entwickler diese Komponenten so konfigurieren können, dass die Schaltfläche &quot;Mehr laden&quot;als Seitenumbruchstil angezeigt wird.

* Die Seite zum Zurücksetzen des Kennworts wurde implementiert, damit Käufer ihr Kontokennwort aktualisieren/zurücksetzen können.

* Unterstützung für gebündelte Produktarten verfügbar.

* Entwickler können die HTML-Tags für Produktkarussell, verwandte Produkte und vorgestellte Kategorielisten-Komponenten konfigurieren, um SEO-Best Practices zu befolgen.

* Mein Konto hat Fehler behoben.

* Mehrere Fehlerbehebungen.

## Releasedatum: August 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,3,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,3,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.9.2 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-august}

* Breadcrumb-Komponente zur Unterstützung von Inhalten und Commerce-Seiten hinzugefügt.

* Registerkarte &quot;Commerce&quot;in den Seiteneigenschaften hinzugefügt, um CIF-Eigenschaften für Landingpages und Experience Fragments anzuzeigen.

* Die Suchleistenkomponente wurde verbessert, um die Option zur Anzeige von Platzhaltertext zu unterstützen

* Zusätzliche Flexibilität bei Produkt- und Produkt-Teaser-Komponenten zur Unterstützung einfacher Anpassungen.

* Es wurde eine Flexibilität hinzugefügt, um die standardmäßige CTA-Schaltflächenbeschriftung für die Produkt-Teaser-Komponente zu überschreiben und zu konfigurieren.

* Die Adressbuchkomponente wurde verbessert, um registrierten Käufern die Möglichkeit zu geben, beim Checkout im Adressbuch gespeicherte Versand- und Rechnungsadressen auszuwählen.

* Mehrere Fehlerbehebungen.

## Releasedatum: Juli 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1,2,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,2,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.8.14 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-july}

* Die CIF-Venia-Referenz-Site wurde aus dem CIF-Archetyp-Repository extrahiert und ist jetzt ein eigenständiges GitHub-Repository.

* Der CIF-Archetyp wurde mit AEM Projektarchetyp zusammengeführt. Verwenden Sie für neue Projekte [AEM Projektarchetyp](https://github.com/adobe/aem-project-archetype) als Ausgangspunkt.

* Adressbuchverwaltung hinzugefügt, damit angemeldete Benutzer ihre Adressen verwalten können.

* Die Benutzeroberfläche der CIF-Cloud-Konfiguration unterstützt das Veröffentlichen/Rückgängigmachen der Veröffentlichung von Aktionen.

### Verbesserte Funktionen {#what-is-improved-july}

* Die Anmelde-Komponente wurde in die Benutzer-Dropdown-Liste verschoben, um einfachen Zugriff zu erhalten.

* Das Paket aem-core-cif-response-components wurde vereinfacht.

* Mehrere Fehlerbehebungen.

## Releasedatum: Juni 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.1.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.1.1 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,11,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-june}

Dies ist die erste Version der CIF-Kernkomponenten, die von Adobe Experience Manager unterstützt wird.

* Die Produktsortierung auf der Seite Produktliste und Suchergebnisse wurde hinzugefügt, damit Käufer anhand von Relevanz, Preis und Produktname sortieren können.

* Kategoriefilterung wurde als Facette hinzugefügt, damit Käufer nach Kategorie filtern können.

* Das Service-User-Mapping wurde als Teil der Sicherheitsanforderung hinzugefügt, um den Zugriff auf /conf über Dienstbenutzer und nicht durch direkte Bearbeitung von ACLs sicherzustellen. CIF-Kernkomponenten müssen jetzt einen Dienstbenutzer verwenden, um auf Konfigurationen zuzugreifen.

### Verbesserte Funktionen {#what-is-improved-june}

* Die Produktlistenseite und die Suchergebnisseite zeigen die Gesamtanzahl der Elemente an. Die Anzahl der Elemente wird aktualisiert, wenn der Käufer Filter anwendet.

* Facettensuche optimiert durch Kombination von Kategorieabfrage und Produktsuchabfrage.

* Kategorie-/Produkt-Wähler für die Seitenvorschau berücksichtigen cq:catalogPath.

* Mehrere Fehlerbehebungen.

## Releasedatum: Mai 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.0.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1,0,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,11,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-may}

* Unterstützt Abfragen für das Adobe Commerce 2.3.5-Schema.

* Die Unterstützung für die Facettensuche wurde der Suchseite und der Produktlistenseite hinzugefügt, damit Käufer Suchergebnisse anhand von Produktfacetten filtern können.

* Neuer OSGi-Dienst wurde hinzugefügt, um PDP/PLP-URLs für SEO-Zwecke anzupassen. Weiterführende Informationen dazu finden Sie in diesem Abschnitt [Dokumentation](https://github.com/adobe/aem-core-cif-components/wiki/configuration).

* Produktbindung wird automatisch erstellt, wenn eine Cloud-Konfiguration erstellt wird.

### Verbesserte Funktionen

* Die Cloud-Konfiguration wurde erweitert, um die Aktion &quot;Ordner erstellen&quot;anzuzeigen.

* Es wurden mehrere Fehlerbehebungen vorgenommen.

## Releasedatum: April 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,10,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,10,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,10,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-april}

* Konfigurationseinstellungen für CIF Connector vereinheitlicht und vereinfacht. Weitere Details zum Checkout [Erste Schritte](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html) oder [Neue AEM CIF-Projekteinstellungen](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html#!AdobeDocs/commerce-cif-documentation/master/getting-started/02-new-cif-project.md)

### Verbesserte Funktionen {#what-is-improved-april}

* Der Warenkorb und der Checkout-Fluss wurden erweitert, um registrierte Käufer zu unterstützen.

* Erweiterte Internationalisierungsunterstützung für alle Komponenten.

* Unterstützung für gruppierte Produkte und virtuelle Produkte verfügbar.

* Zugehörige Produkte, Produktkarussell und vorgestellte Kategoriekomponenten wurden verbessert, um optionale Titel zu unterstützen.

* Es wurden mehrere Fehlerbehebungen vorgenommen.

## Releasedatum: Februar 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,9,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,9,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,9,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-february}

* Unterstützt Abfragen für das Adobe Commerce 2.3.4-Schema.

* Zusätzliche Suchunterstützung in der Kategorieauswahl.

* Paginierung in der Komponente &quot;Kategorieliste&quot;, um große Katalogsätze zu unterstützen.

### Verbesserte Funktionen {#what-is-improved-february}

* Der Warenkorb wurde um Rabatte erweitert.

* Produktdetails, Produkt-Teaser und Produktlisten-Komponenten unterstützen die Anzeige erweiterter Preisinformationen.

* Die Produktsuche in der Produktkonsole und der Produktauswahl wurde verbessert.

* Es wurden mehrere Fehlerbehebungen vorgenommen.

## Releasedatum: Januar 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0,8,0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0,8,0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0,7,0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-january}

* Experience Fragment-Komponente (XF) wurde hinzugefügt, damit Kunden XF in ihrem Commerce-Projekt erstellen können.

* Ändern Sie die Kennwortfunktionalität, die in meinem Konto verfügbar ist.

* i18n-Unterstützung für AEM CIF-Server-seitige Kernkomponenten.

* Generische zugehörige Produktkomponente verfügbar.

### Verbesserte Funktionen {#what-is-improved-january}

* Unterstützung für die Anzeige der CTA-Schaltfläche im Produkt-Teaser.

* Option zum Ändern/Auswählen von Bildern in der Komponente &quot;Spezielle Kategorienliste&quot;.

* Option zum Ausblenden/Anzeigen von Titel/Banner in der Komponente Produktliste .

* Ziehen Sie die Funktion per Drag-and-Drop, die auf die Produktkarussellkomponente angewendet wird.

* Es wurden mehrere Fehlerbehebungen vorgenommen.
