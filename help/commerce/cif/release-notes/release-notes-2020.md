---
title: AEM Content and Commerce – Versionshinweise 2020
description: Versionshinweise zu Adobe Experience Manager Content and Commerce 2020.
exl-id: 440ecd8e-55dc-4606-8678-c65cda1d2b3a
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '1354'
ht-degree: 68%

---

# Übersicht über die GitHub-Version von Commerce Integration Framework

## Releasedatum: November 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.6.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.6.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.12.01 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-november}

* Vorlagenvererbung, die einer bestimmten Kategorieseite hinzugefügt wurde. Diese Funktion verbessert die Effizienz der Unternehmensbenutzer, da sie es allen Unterkategorien ermöglicht, die Vorlage zu übernehmen, die für eine bestimmte oberste Kategorie erstellt wurde.

* Venia-Referenz-Storefront wurde aktualisiert, um Experience Fragment für die Fußzeile zu verwenden. Geschäftsbenutzer können die Fußzeile mit AEM Authoring-Tools bearbeiten.

### Verbesserte Funktionen {#what-is-improved-november}

* Die Checkout-Komponente wurde verbessert, um Käufern die Möglichkeit zu geben, in das Zielland zu gelangen, um Abrechnungs-/Versandadressen außerhalb der USA zuzulassen.

* Die Navigationskomponente wurde erweitert, sodass sie die Adobe-Client-Datenschicht abzudeckt.

* Mehrere Fehlerbehebungen.

## Veröffentlichungsdatum: Oktober 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.5.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.5.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.10.27 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-october}

* Eine neue Karussellkomponente für Kategorie wurde hinzugefügt, damit geschäftliche Benutzer diese Komponente per Drag-and-Drop auf AEM Inhaltsseiten einfügen können, um Inhaltsseiten mit Commerce-Daten anzureichern.

* CIF-Kernkomponenten wurden erweitert, sodass sie die Adobe-Client-Datenschicht durch Senden von Commerce-Daten einbinden. Die Adobe Client-Datenschicht ist eine standardisierte Methode zur Erfassung von Daten und zur Kommunikation der Daten mit Digital Analytics- und Reporting-Servern. Weitere Informationen finden Sie unter [Adobe-Client-Datenschicht](https://github.com/adobe/adobe-client-data-layer/wiki).

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

* Für die Seiten Produktliste und Suchergebnisse wird ein Stil für verzögertes Laden der Seitenumbrüche implementiert, damit Entwickler diese Komponenten so konfigurieren können, dass die Schaltfläche &quot;Mehr laden&quot;als Paginierungsstil angezeigt wird.

* Die Seite zum Zurücksetzen des Kennworts wurde implementiert, damit Käufer ihr Kontokennwort aktualisieren/zurücksetzen können.

* Unterstützung für gebündelte Produktarten ist verfügbar.

* Entwickler können die HTML-Tags der Komponenten für Produktkarussells, verwandte Produkte und vorgestellte Kategorielisten konfigurieren, um SEO-Best-Practices zu befolgen.

* Fehler bei „Mein Konto“ wurde behoben.

* Mehrere Fehlerbehebungen.

## Releasedatum: August 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 1.3.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 1.3.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF Venia-Referenz-Site | 2020.9.2 | [Versionshinweise](https://github.com/adobe/aem-cif-guides-venia/releases) |

### Neue Funktionen {#what-is-new-august}

* Breadcrumb-Komponente wurde zur Unterstützung von Inhalts- und Commerce-Seiten hinzugefügt.

* Die Registerkarte „Commerce“ wurde in den Seiteneigenschaften hinzugefügt, um CIF-Eigenschaften für Landingpages und Experience Fragments anzuzeigen.

* Die Searchbar-Komponente wurde verbessert, um die Option zur Anzeige von Platzhaltertext zu unterstützen.

* Zusätzliche Flexibilität bei Produkt- und Produkt-Teaser-Komponenten zur Unterstützung einfacher Anpassungen.

* Flexibilität wurde hinzugefügt, um die standardmäßige CTA-Schaltflächenbeschriftung für die Produkt-Teaser-Komponente zu überschreiben und zu konfigurieren.

* Die Komponente Adressbuch wurde verbessert, damit registrierte Käufer beim Checkout die im Adressbuch gespeicherten Versand- und Rechnungsadressen auswählen können.

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

* Die Verwaltung des Adressbuchs wurde hinzugefügt, damit angemeldete Benutzer ihre Adressen verwalten können.

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

* Auf der Seite Produktliste und Suchergebnisse wurde eine Produktsortierung hinzugefügt, damit Käufer anhand von Relevanz, Preis und Produktname sortieren können.

* Kategoriefilterung wurde als Facette hinzugefügt, damit Käufer nach Kategorie filtern können.

* Eine Zuordnung von Service und Benutzer wurde als Teil der Sicherheitsanforderung hinzugefügt, um den Zugriff auf „/conf“ über Service-Benutzer und nicht durch direkte Bearbeitung von ACLs sicherzustellen. CIF-Kernkomponenten müssen jetzt einen Service-Benutzer verwenden, um auf Konfigurationen zuzugreifen.

### Verbesserte Funktionen {#what-is-improved-june}

* Auf den Seiten Produktliste und Suchergebnis wird die Gesamtanzahl der Elemente angezeigt. Die Anzahl der Elemente wird aktualisiert, wenn der Käufer Filter anwendet.

* Die facettierte Suche wird durch die Kombination einer Kategorieabfrage mit einer Produktsuchabfrage optimiert.

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

* Neuer OSGi-Dienst wurde hinzugefügt, um PDP/PLP-URLs für SEO-Zwecke anzupassen. Weitere Informationen finden Sie unter [Dokumentation](https://github.com/adobe/aem-core-cif-components).

* Die Produktbindung wird automatisch erstellt, wenn eine Cloud-Konfiguration erstellt wird.

### Verbesserte Funktionen

* Die Cloud-Konfiguration wurde erweitert, um die Aktion &quot;Ordner erstellen&quot;anzuzeigen.

* Es wurden mehrere Fehlerbehebungen vorgenommen.

## Veröffentlichungsdatum: April 2020

| GitHub | Version | Detaillierte Versionshinweise |
|:-------|:-----:|---------------------:|
| CIF-Connector | 0.10.0 | [Versionshinweise](https://github.com/adobe/commerce-cif-connector/releases) |
| CIF-Kernkomponenten | 0.10.0 | [Versionshinweise](https://github.com/adobe/aem-core-cif-components/releases) |
| CIF-Archetyp | 0.10.0 | [Versionshinweise](https://github.com/adobe/aem-cif-project-archetype/releases) |

### Neue Funktionen {#what-is-new-april}

* Die Konfigurationseinstellungen für CIF Connector sind vereinheitlicht und vereinfacht. Weitere Details finden Sie unter [Erste Schritte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/home.html?lang=de) oder [Neue AEM-CIF-Projekteinrichtung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/home.html?lang=de).

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

* Paginierung in der Komponente &quot;Kategorieliste&quot;, um große Katalogsätze zu unterstützen.

### Verbesserte Funktionen {#what-is-improved-february}

* Der Warenkorb wurde um die Anzeige von Rabatten erweitert.

* Produktdetails, Produkt-Teaser und Produktlisten-Komponenten unterstützen die Anzeige erweiterter Preisinformationen.

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

* Ändern Sie die in meinem Konto verfügbare Passwortfunktion.

* i18n-Unterstützung für Server-seitige AEM-CIF-Kernkomponenten.

* Eine generisch verwandte Produktkomponente ist verfügbar.

### Verbesserte Funktionen {#what-is-improved-january}

* Unterstützung für die Anzeige der CTA-Schaltfläche im Produkt-Teaser.

* Option zum Ändern/Auswählen von Bildern in der Komponente für vorgestellte Kategorienlisten.

* Option zum Ausblenden/Anzeigen von Titel/Banner in der Produktlistenkomponente.

* Ziehen Sie die Funktion per Drag-and-Drop auf die Komponente &quot;Produktkarussell&quot;.

* Es wurden mehrere Fehlerbehebungen vorgenommen.
