---
title: Konzepte
description: Erfahren Sie mehr über die allgemeinen Konzepte von eCommerce mit Adobe Experience Manager.
contentOwner: Guillaume Carlino
exl-id: 290b2af6-257f-42f2-b809-1248227a4795
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '4480'
ht-degree: 30%

---

# Konzepte{#concepts}

Das Integrations-Framework bietet Mechanismen und Komponenten für:

* Verbindung zu einer eCommerce-Engine
* Abrufen von Daten in Adobe Experience Manager (AEM)
* Anzeigen dieser Daten und Erfassen der Antworten des Kunden
* Zurückgeben von Transaktionsdetails
* Suchen nach Daten beider Systeme

Das heißt:

* Käufer können sich registrieren und ohne Wartezeit einkaufen.
* Preisänderungen werden von den Käufern unverzüglich beobachtet.
* Produkte können nach Bedarf hinzugefügt werden.

>[!NOTE]
>
>Das eCommerce-Framework kann mit folgenden Funktionen verwendet werden:
>
>* [Adobe Commerce](/help/commerce/cif/integrating/magento.md)
>* [SAP Commerce Cloud](/help/commerce/cif-classic/administering/sap-commerce-cloud.md)
>* [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
>

>[!CAUTION]
>
>Das [eCommerce-Integrationsframework](https://business.adobe.com/products/experience-manager/sites/ecommerce-integrations.html) ist ein Add-on von AEM.
>
>Ihr Vertriebsmitarbeiter kann nach dem entsprechenden Modul alle Einzelheiten angeben.

>[!CAUTION]
>
>Das Framework stellt die grundlegenden Voraussetzungen für Ihr eigenes Projekt bereit.
>
>Ein gewisses Maß an Entwicklungsarbeit ist immer erforderlich, um das Framework an Ihre Vorgaben anzupassen.

>[!CAUTION]
>
>Die AEM-Standardinstallation umfasst die generische AEM-E-Commerce-Implementierung (JCR).
>
>Dies ist für Demonstrationszwecke oder als Basis für eine benutzerdefinierte Implementierung entsprechend Ihren Anforderungen gedacht.

Um den Betrieb zu optimieren, konzentrieren sich sowohl AEM als auch die eCommerce-Engine auf ihr eigenes Fachgebiet. Informationen werden zwischen den beiden in Echtzeit übertragen, z. B.:

* AEM können:

   * Anfrage:

      * Produktinformationen aus der eCommerce-Engine.

   * Geben Sie Folgendes an:

      * Benutzeransichten für Produktinformationen, Warenkorb und Checkout.
      * Warenkorb und Checkout-Informationen an die eCommerce-Engine.
      * Suchmaschinenoptimierung (SEO).
      * Community-Funktionalität.
      * Unstrukturierte Marketinginteraktionen.

* Die eCommerce-Engine kann:

   * Geben Sie Folgendes an:

      * Produktinformationen aus der Datenbank.
      * Verwaltung von Produktvarianten.
      * Auftragsverwaltung.
      * Enterprise Resource Planning (ERP)
      * Suchen Sie in den Produktinformationen.

   * Prozess:

      * Der Warenkorb.
      * Der Kassengang.
      * Auftragserfüllung.

>[!NOTE]
>
>Die genauen Details hängen von der eCommerce-Engine und der Projektimplementierung ab.

Für die Verwendung der Integrationsschicht stehen verschiedene vordefinierte AEM zur Verfügung. Derzeit umfassen diese Folgendes:

* Produktinformationen
* Warenkorb
* Checkout
* Mein Konto

Es stehen auch verschiedene Suchoptionen zur Verfügung.

## Architektur {#architecture}

Das Integrations-Framework stellt die API, eine Reihe von Komponenten zur Veranschaulichung der Funktionalität und mehrere Erweiterungen bereit, um Beispiele für Verbindungsmethoden bereitzustellen:

![chlimage_1-4](/help/sites-administering/assets/chlimage_1-4.png)

Über das Framework erhalten Sie Zugriff auf Funktionen, z. B.:

![chlimage_1-5](/help/sites-administering/assets/chlimage_1-5.png)

### Implementierungen {#implementations}

AEM eCommerce wird mit einer eCommerce-Engine implementiert:

* Das eCommerce-Integrations-Framework wurde entwickelt, damit Sie eine E-Commerce-Engine einfach in AEM integrieren können. Die speziell entwickelte eCommerce-Engine steuert Produktdaten, Warenkörbe, Checkout und die Auftragserfüllung, während AEM die Datenanzeige und Marketingkampagnen steuert.


>[!NOTE]
>
>Die AEM-Standardinstallation umfasst die generische AEM-E-Commerce-Implementierung (JCR).
>
>Dies ist für Demonstrationszwecke oder als Basis für eine benutzerdefinierte Implementierung entsprechend Ihren Anforderungen gedacht.
>
>AEM in AEM implementierter eCommerce mithilfe einer generischen, auf JCR basierenden Entwicklung lautet:
>
>* Ein eigenständiges, AEM-natives eCommerce-Beispiel zur Veranschaulichung der Verwendung der API. Damit können Produktdaten, Warenkörbe und Checkout mit den vorhandenen Datenanzeige- und Marketingkampagnen gesteuert werden. In diesem Fall wird die Produktdatenbank im Repository gespeichert, das nativ zu AEM ist (Adobe-Implementierung von [JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)).
>
>  Die standardmäßige AEM-Installation enthält die Grundlagen der [generische eCommerce-Implementierung](/help/commerce/cif-classic/administering/generic.md).

### Commerce-Anbieter {#commerce-providers}

Beim Importieren von Daten aus einer Commerce-Engine in Ihre AEM E-Commerce-Site wird ein Commerce-Anbieter verwendet, um den Importeuren Daten bereitzustellen. Ein Commerce-Anbieter kann mehrere Importeure unterstützen.

Ein Commerce-Anbieter ist AEM Code angepasst an:

* Schnittstelle zu einer Back-End-Commerce-Engine
* ein Commerce-System über dem JCR-Repository implementieren

Derzeit stehen zwei Beispiel-Commerce-Anbieter für AEM zur Verfügung:

* ein für geometrixx-hybris
* ein anderer für geometrixx-generic (JCR)

In der Regel muss ein Projekt jedoch einen eigenen, benutzerdefinierten Commerce-Anbieter entwickeln, der für sein PIM- und Produktdatenschema spezifisch ist.

>[!NOTE]
>
>Die Geometrixx-Importeure verwenden CSV-Dateien. In den obigen Kommentaren ihrer Implementierung finden Sie eine Beschreibung des akzeptierten Schemas (mit zulässigen benutzerdefinierten Eigenschaften).

Der [ProductServicesManager](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/ProductServicesManager.html) verwaltet (über [OSGi](/help/sites-deploying/configuring.md#osgi-configuration-settings)) eine Liste der Implementierungen der [ProductImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/ProductImporter.html)- und [CatalogBlueprintImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/CatalogBlueprintImporter.html)-Schnittstelle. Diese sind im Import-Tool-Assistenten im Dropdown-Feld **Import-Tool/Commerce-Anbieter** aufgeführt (mit der Eigenschaft `commerceProvider` als Name).

Wenn ein bestimmtes Import-Tool/ein bestimmter Commerce-Anbieter im Dropdown-Feld verfügbar ist, müssen Sie alle weiteren benötigten Daten (je nach Art des Import-Tools) unter einem der folgenden Pfade definieren:

* `/apps/commerce/gui/content/catalogs/importblueprintswizard/importers`
* `/apps/commerce/gui/content/products/importproductswizard/importers`

Der Ordner unter dem entsprechenden `importers`-Ordner muss mit dem Namen des Import-Tools übereinstimmen, z. B.:

* `.../importproductswizard/importers/geometrixx/.content.xml`

Das Format der Quell-Importdatei wird vom Import-Tool definiert. Oder der Importeur stellt eine Verbindung (z. B. WebDAV oder http) zur Commerce-Engine her.

## Rollen {#roles}

Das integrierte System ermöglicht die Pflege der Daten durch die folgenden Rollen:

* Produktdatenverwaltung (PIM)-Benutzer, der Folgendes verwaltet:

   * Produktinformationen.
   * Taxonomie, Kategorisierung, Genehmigung.
   * Interagiert mit Digital Asset Management.
   * Preise - Häufig handelt es sich dabei um ein ERP-System, das nicht explizit im Commerce-System verwaltet wird.

* Autor/Marketing-Manager, der Folgendes verwaltet:

   * Marketinginhalte für alle Kanäle.
   * Promotions.
   * Gutscheine.
   * Kampagnen.

* Surfer/Käufer, die:

   * Zeigt Ihre Produktinformationen an.
   * Setzt Artikel in den Warenkorb.
   * Checkt ihre Bestellungen aus.
   * Erwarten Sie die Erfüllung der Bestellung.

Der tatsächliche Speicherort kann von Ihrer Implementierung abhängen, z. B. von einer generischen oder einer eCommerce-Engine:

![chlimage_1-6](/help/sites-administering/assets/chlimage_1-6.png)

## Produkte {#products}

### Produktdaten im Vergleich zu Marketingdaten {#product-data-versus-marketing-data}

#### Strukturelle und Marketing-Kategorien {#structural-versus-marketing-categories}

Wenn die beiden folgenden Kategorien unterschieden werden können, können Sie damit eindeutige URLs mit einer aussagekräftigen Struktur (Baumstrukturen von `cq:Page` -Knoten) und daher sehr nah am klassischen AEM Content Management):

* *Strukturelle *Kategorien

  Kategoriestruktur, die definiert, *was ein Produkt ist*; Beispiel:

  `/products/mens/shoes/sneakers`

* *Marketing*-Kategorien

  Alle anderen Kategorien, die *-Produkt kann*; zum Beispiel:

  `/special-offers/christmas/shoes`)

### Produktdaten {#product-data}

Um Ihr Produkt zu präsentieren und zu verwalten, sollten Sie eine Reihe von Informationen über das Produkt speichern.

Produktdaten können sein:

* direkt in AEM verwaltet werden (allgemein)
* in der eCommerce-Engine verwaltet und in AEM bereitgestellt werden

  Je nach Datentyp ist es [synchronisiert](#catalog-maintenance-data-synchronization) bei Bedarf oder direkt darauf zugreifen. Beispielsweise werden hochgradig flüchtige und kritische Daten wie Produktpreise bei jeder Seitenanforderung von der E-Commerce-Engine abgerufen, um sicherzustellen, dass sie immer auf dem neuesten Stand sind.

Wenn die Produktdaten in AEM eingegeben/importiert wurden, können sie in den **Produkte** Konsole. Hier zeigen die Karten- und Listenansichten eines Produkts Informationen wie:

* das Bild
* der SKU-Code
* wann zuletzt geändert

![chlimage_1-7](/help/sites-administering/assets/chlimage_1-7.png)

### Produktvarianten {#product-variants}

Für geeignete Produkte können auch Informationen über Varianten gespeichert werden. Beispielsweise werden bei Bekleidungsartikeln die unterschiedlichen angebotenen Farben als Varianten gespeichert:

![ecommerceproductvariables](/help/sites-administering/assets/ecommerceproductvariants.png)

### Produktattribute {#product-attributes}

Die über die einzelnen Produkte gespeicherten Attribute können von der verwendeten eCommerce-Engine und Ihrer AEM-Implementierung abhängen. Diese sind (je nach Bedarf) beim Anzeigen von Produktseiten und/oder Bearbeiten von Produktinformationen verfügbar und können Folgendes umfassen:

* **Bild**

  Ein Bild des Produkts.

* **Titel**

  Der Produktname.

* **Beschreibung**

  Ein beschreibender Text zum Produkt.

* **Tags**

  Tags, mit denen ähnliche Produkte gruppiert werden

* **Standard-Asset-Kategorie**

  Eine Standardkategorie für Assets.

* **ERP-Daten**

  Informationen zum Enterprise Resource Planning (ERP).

   * **SKU**

     SKU-Daten

   * **Farbe**
   * **Größe**
   * **Preis**

     Der Stückpreis des Produkts.

* **Zusammenfassung**

  Eine Zusammenfassung der Produktfunktionen.

* **Funktionen**

  Umfassendere Details zu den Produktfunktionen.

### Produktassets {#product-assets}

Eine Auswahl von Assets kann für einzelne Produkte gespeichert werden. Dazu gehören in der Regel Bilder und Videos.

## Kataloge {#catalogs}

Ein Katalog fasst Produktdaten zusammen, um sowohl die Verwaltung als auch die Darstellung für den Käufer zu erleichtern. Häufig ist ein Katalog nach Attributen wie Sprache, geografisches Gebiet, Marke, Saison, Hobby, Sport, unter vielen anderen strukturiert.

### Katalogstruktur {#catalog-structure}

#### Kataloge in mehreren Sprachen {#catalogs-in-multiple-languages}

AEM unterstützt Produktinhalte in mehreren Sprachen. Beim Abfragen von Daten ruft das Integrations-Framework die Sprache vom aktuellen Baum ab (z. B. `en_US` für Seiten unter `/content/geometrixx-outdoors/en_US`).

Für einen mehrsprachigen Speicher können Sie Ihren Katalog für jeden Sprachbaum einzeln importieren (oder ihn mit [MSM](/help/sites-administering/msm.md)).

#### Kataloge für mehrere Marken {#catalogs-for-multiple-brands}

Wie bei Sprachen müssen große multinationale Unternehmen mehrere Marken abdecken.

#### Kataloge nach Tags {#catalogs-by-tags}

Tags können auch verwendet werden, um Produkte in einem Katalog zusammenzufassen. Dieser Ansatz bietet sich für dynamischere Kataloge an.

### Katalogeinrichtung (erster Import) {#catalog-setup-initial-import}

Abhängig von Ihrer Implementierung können Sie die für Ihren Basiskatalog erforderlichen Produktdaten aus folgenden AEM importieren:

* eine CSV-Datei (für die allgemeine Implementierung)
* eCommerce-Engine

### Katalogwartung (Datensynchronisierung) {#catalog-maintenance-data-synchronization}

Weitere Änderungen der Produktdaten sind unvermeidlich:

* für die generische Implementierung können diese mit der [Produkteditor](/help/commerce/cif-classic/administering/generic.md#editing-product-information)
* die Verwendung einer [eCommerce-Engine; hier müssen die Änderungen synchronisiert werden](#data-synchronization-with-an-ecommerce-engine-ongoing)

#### Datensynchronisation mit einer eCommerce-Engine (laufend) {#data-synchronization-with-an-ecommerce-engine-ongoing}

Nach dem ersten Import sind Änderungen an Ihren Produktdaten unvermeidlich.

Bei Verwendung einer eCommerce-Engine werden die Produktdaten dort gespeichert und müssen in AEM verfügbar sein. Diese Produktdaten müssen bei Aktualisierungen synchronisiert werden.

Dies kann vom Datentyp abhängen:

* A [Die periodische Synchronisierung wird zusammen mit einem Daten-Feed der Änderungen verwendet](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#product-synchronization-and-publishing).

  Zusätzlich können Sie bestimmte Aktualisierungen für ein Express-Update auswählen.

* Hoch schwankende Daten wie Preisinformationen werden für jede Seitenanforderung von der Commerce-Engine abgerufen, um sicherzustellen, dass sie immer auf dem neuesten Stand sind.

### Kataloge - Leistung und Skalierung {#catalogs-performance-and-scaling}

Der Import eines großen Katalogs mit einer großen Anzahl von Produkten (über 100.000) aus einer eCommerce-Engine (PIM) kann sich aufgrund der großen Anzahl von Knoten auf das System auswirken. Sie kann auch die Authoring-Instanz verlangsamen, wenn die Produkte über verknüpfte Assets verfügen (z. B. Produktbilder). Dies liegt daran, dass die Nachbearbeitung dieser Assets CPU- und speicherintensiv ist.

Es gibt verschiedene Strategien, mit denen Sie diese Probleme umgehen können:

* [Buckets](#bucketing) – um die große Anzahl an Knoten zu unterstützen
* [Abladen der Asset-Nachbearbeitung auf einer dedizierten Instanz](#offload-asset-post-processing-to-a-dedicated-instance)
* [Importieren von Produktdaten ohne Assets](#only-import-product-data)
* [Importbeschränkung und Batch-Speicherung](#import-throttling-and-batch-saves)
* [Leistungstests](#performance-testing)
* [Leistung – Verschiedenes](#performance-miscellaneous)

#### Bucket {#bucketing}

Wenn ein JCR-Knoten viele direkt untergeordnete Knoten hat (z. B. 1000 und mehr), sind Buckets (Phantom-Ordner) erforderlich, um sicherzustellen, dass die Leistung nicht beeinträchtigt wird. Diese werden beim Import anhand eines Algorithmus generiert.

Diese Behälter haben die Form von Phantom-Ordnern, die in Ihre Katalogstruktur eingeführt werden, aber so konfiguriert werden können, dass sie in öffentlichen URLs nicht sichtbar sind.

#### Auslagern der Asset-Nachbearbeitung auf eine dedizierte Instanz {#offload-asset-post-processing-to-a-dedicated-instance}

Dieses Szenario umfasst das Einrichten von zwei Autoreninstanzen:

1. Primäre Autoreninstanz

   Importiert Produktdaten vom PIM, auf dem die Nachbearbeitung für Asset-Pfade deaktiviert ist.

1. Dedizierte DAM-Autoreninstanz

   Importiert Produkt-Assets aus dem PIM, bearbeitet sie nach und repliziert sie zur Nutzung zurück zur primären Autoreninstanz.

![Architekturdiagramm](/help/sites-administering/assets/chlimage_1-8.png)

#### Importieren von Produktdaten ohne Assets {#only-import-product-data}

Wenn Produkte keine Assets (Bilder) enthalten, die importiert werden sollen, können Sie die Produktdaten importieren, ohne von der Nachbearbeitung der Assets betroffen zu sein.

![Architekturdiagramm](/help/sites-administering/assets/chlimage_1-9.png)

#### Leistungstests {#performance-testing}

Leistungstests müssen in AEM E-Commerce-Implementierungen berücksichtigt werden:

* Autorenumgebung:

  Die Hintergrundaktivität (z. B. Import) kann gleichzeitig mit der normalen Benutzeraktivität (z. B. Seitenbearbeitung) auftreten. Selbst wenn die Frontend-Leistung (im Allgemeinen) eine höhere Priorität hat, kann eine von Online-Autoren erkannte schlechte Leistung zu Frustration führen, die eine Go-Live-Entscheidung blockieren kann.

* Veröffentlichungsumgebung:

  Die Replikation ist wichtig, um sicherzustellen, dass die Inhalte schnell und zuverlässig veröffentlicht werden. Dies kann dadurch beeinflusst werden, wie der Autor die Inhalte gruppiert, die veröffentlicht werden sollen.

* Frontend:

  Kombination aus Frontend- und Cache-Invalidierung kann zu Leistungseinbußen führen. Tests helfen dabei, diese zu vermeiden.

Beachten Sie, dass dieser Leistungstest Kenntnisse und Analysen Ihrer Zielgruppe erfordert:

* Inhaltsvolumen

   * Assets
   * Lokalisierte I18-End-Produkte und SKUs

* Benutzeraktivität:

   * Massenbearbeitung
   * Massenveröffentlichung
   * Intensiv-Suchanfragen

* Hintergrundprozesse

   * Importvorgänge
   * Synchronisierungsaktualisierungen (z. B. Preise)

* Wartungsanforderungen (Sicherung, Tar-PM-Optimierung, Datenspeicherbereinigung usw.)

#### Leistung – Verschiedenes {#performance-miscellaneous}

Bei allen Implementierungen können die folgenden Punkte beachtet werden:

* Da Produkt, Lagereinheiten und Kategorien zahlreich sein können, versuchen Sie, die geringstmögliche Anzahl von Knoten zur Modellierung des Inhalts zu verwenden.

  Je mehr Knoten Sie haben, desto flexibler ist Ihr Inhalt (z. B. parsys). Alles ist jedoch ein Kompromiss und benötigen Sie (standardmäßig) individuelle Flexibilität bei der Bearbeitung (z. B. 30.000 Produkte)?

* Vermeiden Sie Duplizierungen so oft wie möglich (siehe Lokalisierung) oder überlegen Sie, zu wie vielen Knoten Ihre Duplizierung führt.
* Versuchen Sie, Ihren Inhalt so oft wie möglich mit Tags zu versehen, um die Abfrageoptimierung vorzubereiten.

  Zum Beispiel:

  `/content/products/france/fr/shoe/reebok/pump/46 SKU`

  sollte ein Tag pro Inhaltsebene haben (d. h. Land, Sprache, Kategorie, Marke, Produkt). Die Suche nach

  `//element(*,my:Sku)[@country='france' and @language='fr'`

  und

  `@category='shoe' and @brand='reebok' and @product='pump']`

  wird drastisch schneller sein als die Suche nach

  `/jcr:root/content/france/fr/shoe/reebok/pump/element(*,my:Sku)`

* Planen Sie in Ihrem technischen Stack das factorisierte Inhaltszugriffsmodell und -dienste. Dies ist eine allgemeine Best Practice, aber noch wichtiger ist dies hier, da Sie in Optimierungsphasen Anwendungscaches für Daten hinzufügen können, die häufig gelesen werden (und mit denen Sie den Bundle-Cache nicht füllen möchten).

  Beispielsweise ist die Attributverwaltung häufig ein guter Kandidat für die Zwischenspeicherung, da sie Daten betrifft, die über den Produktimport aktualisiert werden.
* Erwägen Sie die Verwendung von [Proxy-Seiten](#proxy-pages).

### Katalogbereichsseiten {#catalog-section-pages}

In Katalogabschnitten finden Sie beispielsweise Folgendes:

* eine Einleitung (Bild und/oder Text) für die Kategorie; hier können auch Banner und Teaser für Sonderangebote werben
* Links zu den einzelnen Produkten in dieser Kategorie
* Relationen zu den anderen Kategorien

![ecommerce_categoryrunning](/help/sites-administering/assets/ecommerce_categoryrunning.png)

### Produktseiten {#product-pages}

Produktseiten bieten umfassende Informationen zu einzelnen Produkten. Dynamische Aktualisierungen von werden ebenfalls angezeigt, z. B. Preisänderungen, die in der eCommerce-Engine registriert sind.

Produktseiten sind AEM Seiten, die **Produkt** -Komponente, z. B. im **Commerce-Produkt** template:

![ecommerce_nairobirunnersgreen](/help/sites-administering/assets/ecommerce_nairobirunnersgreen.png)

Die Produkt-Komponente bietet:

* allgemeine Produktinformationen, darunter Text und Bilder
* Preise; diese werden jedes Mal, wenn die Seite angezeigt/aktualisiert wird, von der eCommerce-Engine abgerufen.
* Informationen zu Produktvarianten, z. B. Farbe und Größe

Anhand dieser Daten kann der Käufer folgende Optionen auswählen, wenn er einen Artikel zum Warenkorb hinzufügt:

* Farbe und Größenvarianten
* Menge

#### Produkt-Landingpages {#product-landing-pages}

Dies sind AEM Seiten, die hauptsächlich statische Informationen bereitstellen, wie z. B. eine Einführung und eine Übersicht mit Links zu den zugrunde liegenden Produktseiten.

### Produktkomponente {#product-component}

Die **Produkt** -Komponente zu jeder Seite mit einer übergeordneten Seite hinzugefügt werden, die die erforderlichen Metadaten bereitstellt (d. h. die Pfade zu `cartPage` und `cartObject`). Bei der Demo-Website, Geometrixx Outdoors, ist dies `UserInfo.jsp`.

Die **Produkt** -Komponente kann auch entsprechend Ihren individuellen Anforderungen angepasst werden.

### Proxy-Seiten {#proxy-pages}

Proxy-Seiten werden verwendet, um die Struktur des Repositorys zu vereinfachen und den Speicher für große Kataloge zu optimieren.

Beim Erstellen eines Katalogs werden zehn Knoten pro Produkt verwendet, da er einzelne Komponenten für jedes Produkt bereitstellt, die Sie in AEM aktualisieren und anpassen können. Diese große Anzahl von Knoten kann zu einem Problem werden, wenn Ihr Katalog Hunderte oder sogar Tausende von Produkten enthält. Um Probleme zu vermeiden, können Sie Ihren Katalog mit Proxy-Seiten erstellen.

Proxy-Seiten nutzen eine Struktur mit zwei Knoten (`jcr:content` und `cq:Page`), die keine Produktinhalte enthalten. Die Inhalte werden zur Abfragezeit durch Verweise auf die Produktdaten und die Vorlagenseite generiert.

Es gibt jedoch einen Kompromiss. Sie können Ihre Produktinformationen nicht innerhalb von AEM anpassen. Es wird eine Standardvorlage (definiert für Ihre Site) verwendet.

>[!NOTE]
>
>Wenn Sie einen großen Katalog ohne Proxyseiten importieren, treten keine Probleme auf.
>
>Sie können von einer Methodik zur anderen jederzeit konvertieren. Sie können auch einen Unterabschnitt Ihres Katalogs konvertieren.

## Promotions und Gutscheine {#promotions-and-vouchers}

### Gutscheine {#vouchers}

Gutscheine sind eine bewährte Methode, Rabatte anzubieten, um Käufer dazu zu bewegen, einen Kauf zu tätigen und/oder die Treue des Kunden zu belohnen.

* Gutscheine:

   * Ein Gutscheincode (der vom Käufer in den Warenkorb eingegeben wird).
   * Eine Gutscheinbeschriftung (die angezeigt wird, nachdem der Käufer sie in den Warenkorb eingegeben hat).
   * Ein Promotionpfad (der die Aktion definiert, die der Gutschein anwendet).

* Externe Commerce-Engines können auch Gutscheine bereitstellen.

Gehen Sie in AEM wie folgt vor:

* Ein Gutschein ist eine seitenbasierte Komponente, die mit der Websites-Konsole erstellt und bearbeitet wird.
* Die **Gutschein**-Komponente bietet:

   * einen Renderer für die Gutscheinadministration; er zeigt alle Gutscheine an, die sich aktuell im Warenkorb befinden
   * Die Bearbeitungsdialogfelder (Formular) zum Verwalten (Hinzufügen/Entfernen) der Gutscheine.
   * Die zum Hinzufügen/Entfernen von Gutscheinen zum/vom Warenkorb erforderlichen Aktionen.

* Gutscheine verfügen nicht über eigene Ein- und Ausschaltzeiten, sondern über die ihrer übergeordneten Kampagnen.

>[!NOTE]
>
>AEM verwendet den Begriff **Gutschein**, der ein Synonym zu **Coupon** ist.

### Promotions {#promotions}

Mithilfe von Promotions können Sie gemeinsam mit Gutscheinen Szenarien umsetzen, z. B.:

* Ein Unternehmen bietet benutzerdefinierte Preise für Mitarbeiter, eine handgefertigte Liste von Benutzern.
* Langfristige Kunden erhalten Rabatte auf alle Bestellungen.
* Ein Verkaufspreis, der über einen genau festgelegten Zeitraum angeboten wird.
* Ein Kunde erhält einen Gutschein, wenn seine vorherige Bestellung einen bestimmten Betrag überschritten hat.
* Ein Kunde, der *product-X* erhalten Sie einen Rabatt auf *product-Y* (Produkte paarweise).

Promotions werden nicht von Produktinformationsmanagern verwaltet, sondern von Marketing-Managern:

* Eine Promotion ist eine seitenbasierte Komponente, die mit der Websites-Konsole erstellt und bearbeitet wird. ``
* Angebote für Werbeaktionen:

   * Eine Priorität
   * Ein Promotion-Handler-Pfad

* Sie können Promotions mit einer Kampagne verknüpfen, um deren Aktivierungs-/Ausschaltzeiten zu definieren.
* Sie können Promotions mit einem Erlebnis verbinden, um deren Segmente zu definieren.
* Promotions, die nicht mit einem Erlebnis verbunden sind, werden nicht allein ausgelöst, können aber dennoch von einem Gutschein ausgelöst werden.
* Die Komponente Promotion enthält:

   * Renderer und Dialogfelder für die Promotions-Administration
   * Unterkomponenten zum Rendern und Bearbeiten von Konfigurationsparametern, die spezifisch für die Promotion-Handler sind

AEM werden die Promotions auch in die [Campaign Management](/help/sites-authoring/personalization.md):

* a [Kampagne](/help/sites-authoring/personalization.md) gibt die Ein-/Ausschaltzeiten an
* [Erlebnisse](/help/sites-authoring/personalization.md) *Innerhalb* die Kampagne wird verwendet, um Assets (Teaser-Seiten, Promotions usw.) entsprechend dem jeweiligen Zielgruppensegment zu gruppieren.

Eine Promotion kann entweder in einem Erlebnis oder direkt in der Kampagne stattfinden:

* Wenn eine Promotion in einem Erlebnis gespeichert wird, kann sie automatisch auf ein Zielgruppensegment angewendet werden.

  Beispielsweise die Promotion auf der Beispielsite geometrixx-outdoors:

  `/content/campaigns/geometrixx-outdoors/big-spender/ordervalueover100/free-shipping`

  befindet sich in einem Erlebnis, wird also immer dann automatisch ausgelöst, wenn das Segment ( `ordervalueover100`) aufgelöst wird.

* Wenn eine Promotion nicht in einem Erlebnis angezeigt wird (also nur in der Kampagne), kann sie nicht automatisch auf eine Zielgruppe angewendet werden. Sie kann jedoch dennoch ausgelöst werden, wenn ein Käufer einen Gutschein im Warenkorb eingibt und dieser Gutschein auf die Promotion verweist.

  Zum Beispiel gilt für die Promotion:

  `/content/campaigns/geometrixx-outdoors/article/10-bucks-off`

  außerhalb eines Erlebnisses liegt und daher nie automatisch ausgelöst wird (d. h. auf Grundlage der Segmentierung). Es verweisen jedoch Gutscheine, die sich in mehreren Erlebnissen der Artikelkampagne befinden, auf diese Promotion. Wenn Sie diese Gutscheincodes in den Warenkorb eingeben, wird die Promotion ausgelöst.

>[!NOTE]
>
>[hybris-Promotions](https://www.hybris.com/modules/promotion) und [hybris-Gutscheine](https://www.hybris.com/en/modules/voucher) decken Sie alles ab, was den Warenkorb beeinflusst und mit der Preisgestaltung in Zusammenhang steht. Werbeinhalt (z. B. Banner) ist nicht Teil der hybris-Promotion.

## Personalisierung  {#personalization}

### Kundenregistrierung und -konten {#customer-registration-and-accounts}

Wenn sich ein Kunde registriert, müssen die Kontodetails zwischen AEM und der eCommerce-Engine synchronisiert werden. Sensible Daten werden separat gespeichert, die Profile sind jedoch freigegeben:

![chlimage_1-10](/help/sites-administering/assets/chlimage_1-10.png)

Der genaue Mechanismus hängt vom Szenario ab:

1. Die Benutzerkonten sind in beiden Systemen vorhanden:

   1. Keine Aktion erforderlich.

1. Das Benutzerkonto existiert nur in AEM:

   1. Der Benutzer wird in der eCommerce-Engine mit derselben Konto-ID und einem zufälligen Kennwort erstellt, das in AEM gespeichert wird.
   1. Das zufällig generierte Kennwort ist nötig, weil AEM beim ersten Aufruf (wenn beispielsweise eine Produktseite angefragt und für den Preis auf die eCommerce-Engine verwiesen wird) versucht, sich bei der eCommerce-Engine anzumelden. Da dies nach der AEM geschieht, ist das Kennwort nicht verfügbar.

1. Das Benutzerkonto existiert nur in der eCommerce-Engine:

   1. Das Konto wird in AEM mit derselben Konto-ID und demselben Kennwort erstellt.

Bei Verwendung einer eCommerce-Engine speichert AEM nur die Konto-ID und das Kennwort (optional eine Benutzergruppe). Alle anderen Daten werden in der eCommerce-Engine gespeichert.

>[!NOTE]
>
>Bei Verwendung einer eCommerce-Engine müssen Sie sicherstellen, dass Konten, die für Benutzer erstellt wurden, die sich bei einer AEM-Instanz anmelden (z. B. über Workflows), mit allen anderen AEM Instanzen repliziert werden, die mit dieser Engine kommunizieren.
>
>Andernfalls werden diese anderen AEM auch versuchen, Konten für dieselben Benutzer in der Engine zu erstellen. Diese Aktionen schlagen fehl, `DuplicateUidException` aus dem Motor kommen.

### Kundenanmeldung {#customer-sign-up}

Häufig ist eine Anmeldung erforderlich, damit der Käufer Zugriff auf den Warenkorb hat. Dafür ist eine Registrierung (Konto erstellen) nötig, damit ein kundenspezifisches Konto erstellt werden kann.

![chlimage_1-11](/help/sites-administering/assets/chlimage_1-11.png)

>[!NOTE]
>
>Ein anonymer Warenkorb und ein anonymer Kassengang werden ebenfalls unterstützt.

### Kundenanmeldung {#customer-sign-in}

Nach der Anmeldung kann sich der Käufer mit seinem Konto anmelden, damit seine Aktionen verfolgt und seine Bestellungen erfüllt werden können.

![chlimage_1-12](/help/sites-administering/assets/chlimage_1-12.png)

### Single Sign-on {#single-sign-on}

Single Sign-on (SSO) wird bereitgestellt, sodass Autoren sowohl im AEM als auch im E-Commerce-System bekannt sind, ohne sich zweimal anmelden zu müssen.

### myAccount {#myaccount}

Transaktionsdaten von der eCommerce-Engine werden mit personenbezogenen Daten zum Kunden kombiniert. AEM verwendet einige dieser Daten als Profildaten. Die Aktion eines Formulars in AEM schreibt Informationen zurück in die eCommerce-Engine.

Es gibt eine Seite, auf der Sie Ihre Kontoinformationen einfach verwalten können. Klicken Sie auf **Mein Konto** oben auf einer Geometrixx oder durch Navigieren zu `/content/geometrixx-outdoors/en/user/account.html`.

![chlimage_1-13](/help/sites-administering/assets/chlimage_1-13.png)

### Adressbuch {#address-book}

Ihre Site muss eine Auswahl von Adressen speichern, einschließlich Versand-, Abrechnungs- und alternativen Adressen. Dies kann mithilfe von Formularen implementiert werden, die auf Ihrem Standard-Adressformat basieren, oder Sie können die Komponente Adressbuch verwenden, die von AEM bereitgestellt wird.

Mit dieser Komponente Adressbuch können Sie:

* Adressdaten im Buch bearbeiten
* eine Adresse aus dem Buch für die Lieferadresse auswählen
* eine Adresse aus dem Buch für die Rechnungsadresse auswählen

Sie können auswählen, welche Adresse Sie als Standard verwenden möchten.

Die Adressbuch-Komponente finden Sie auf der Seite **Mein Konto** durch Klicken auf **Adressbuch** oder indem Sie zu `/content/geometrixx-outdoors/en/user/account/address-book.html` gehen.

![chlimage_1-14](/help/sites-administering/assets/chlimage_1-14.png)

Sie können auf **Neue Adresse hinzufügen...** , um eine Adresse in Ihr Adressbuch einzutragen. Dadurch wird ein Formular geöffnet, das Sie ausfüllen können. Klicken Sie dann auf **Adresse hinzufügen**.

>[!NOTE]
>
>Sie können mehrere Adressen in Ihr Adressbuch eingeben.

Das Adressbuch wird verwendet, wenn Sie Ihren Warenkorb &quot;auschecken&quot;:

![chlimage_1-15](/help/sites-administering/assets/chlimage_1-15.png)

Adressen werden unter `user_home/profile/addresses` aufbewahrt.
Die Adresse von Alison Parker befindet sich beispielsweise unter /home/users/geometrixx/aparker@geometrixx.info/profile/addresses.

Sie können auswählen, welche Adresse Sie als Standard festlegen möchten. Diese Information wird im Käuferprofil gespeichert, nicht zusammen mit der Anschrift. Als Wert für die Profileigenschaft `address.default` wird der Pfad der ausgewählten Adresse festgelegt.

### Kundenspezifische Preise {#customer-specific-pricing}

Die eCommerce-Engine verwendet den Kontext (im Wesentlichen die Kaufinformationen), um den Preis zu bestimmen, den sie hält, und stellt dann die richtigen Informationen zurück an AEM.

## Warenkorb und Bestellungen {#shopping-cart-and-orders}

Beim Einkauf durchsucht der Käufer die Produktseiten und wählt die Artikel aus, um sie in den Warenkorb zu legen. Wenn sie zum Checkout übergehen, kann eine Bestellung aufgegeben werden.

### Anonyme Käufer {#anonymous-shoppers}

Ein anonymer Käufer kann:

* Produkte anzeigen
* Produkte zum Warenkorb hinzufügen
* Checkout durchführen, um ihre Bestellung zu platzieren

>[!NOTE]
>
>Je nach Konfiguration Ihrer Instanz können vor dem Checkout Informationen zur Adresse oder zur Kundenregistrierung erforderlich sein.

### Registrierte Käufer {#registered-shoppers}

Ein registrierter Käufer kann:

* Melden Sie sich bei ihrem Konto an
* Produkte anzeigen
* Produkte zum Warenkorb hinzufügen
* Checkout durchführen, um ihre Bestellung zu platzieren
* Anzeigen und Verfolgen früherer Bestellungen

### Übersicht über den Inhalt des Warenkorbs {#shopping-cart-content-overview}

Der Warenkorb bietet:

* Übersicht über die ausgewählten Elemente
* Links zu den Produktseiten für die ausgewählten Artikel
* die Fähigkeit,

   * Anzahl/Menge der einzelnen Elemente aktualisieren
   * einzelne Elemente entfernen

![ecommerce_shoppingcart](/help/sites-administering/assets/ecommerce_shoppingcart.png)

Der Warenkorb wird je nach verwendeter Engine gespeichert:

* Die generische AEM-Version speichert den Warenkorb in einem Cookie.
* Bestimmte eCommerce-Engines können den Warenkorb in einer Sitzung speichern.

In beiden Fällen bleiben Artikel im Warenkorb (und können wiederhergestellt werden) über die Anmeldung/das Abmelden (aber nur auf demselben Computer/Browser). Beispiel:

* Surfen Sie `anonymous` und fügen Sie Produkte zum Warenkorb hinzu.
* anmelden als `Allison Parker` - Der Warenkorb von Allison ist leer
* Produkte zum Warenkorb von Allison hinzufügen
* Abmelden - der Warenkorb zeigt die Produkte für `anonymous`

* erneut anmelden als `Allison Parker` - Die Produkte von Allison werden wiederhergestellt

>[!NOTE]
>
>Ein anonymer Warenkorb kann nur auf demselben Rechner/im selben Browser wiederhergestellt werden.

>[!NOTE]
>
>Es wird nicht empfohlen, die Wiederherstellung des Warenkorbinhalts mit dem `admin` -Konto, da dies mit dem `admin` -Konto der eCommerce-Engine (z. B. hybris).

>[!NOTE]
>
>hybris kann so konfiguriert werden, dass ausstehende Warenkörbe nach einem bestimmten Zeitraum entfernt werden.

Vor dem Checkout werden Preisänderungen (in beiden Systemen) übernommen, sobald sie auftreten.

### Bestellinformationen {#order-information}

Abhängig von Ihrer Implementierung werden Informationen zu einer Bestellung entweder in der eCommerce-Engine oder AEM gespeichert. Diese Informationen werden von AEM gerendert.

Verschiedene Informationen werden gespeichert, darunter:

* **Auftrags-ID**

  Die Referenznummer für die Bestellung.

* **Platziert**

  Das Datum, an dem die Bestellung aufgegeben wurde.

* **Status**

   Der Status der Bestellung z. B. „versendet“

* **Währung**

  Die Währung der Bestellung.

* **Inhaltselemente**

  Eine Liste der bestellten Artikel.

* **Zwischensumme**

  Die Gesamtkosten der bestellten Artikel.

* **Steuer**

  Der für die Bestellung anfallende Steuerbetrag.

* **Versand**

  Versandkosten.

* **Gesamtbetrag**

  Der Gesamtwert der Bestellung, bestellte Artikel, Steuern und Versandkosten.

* **Rechnungsadresse**

  Die Adresse, an die die Rechnung gesendet werden soll.

* **Zahlungs-Token**

  Die Zahlungsmethode.

* **Zahlungsstatus**

  Status der Zahlung.

* **Lieferadresse**

  Die Adresse, an die die Waren geliefert werden sollen.

* **Versandart**

  Die Versandart, z. B. Post, Luftfracht, Seefracht.

* **Tracking-Nummer**

  Eine Tracking-Nummer des Versandunternehmens für die Sendungsnachverfolgung

* **Tracking-Link**

  Der Link, der während des Versands zur Sendungsnachverfolgung genutzt wird.

>[!NOTE]
>
>Die im Assistenten zum Erstellen einer Bestellung verwendeten Felder hängen davon ab, ob für den Speicherort eine Touch-optimierte Strukturvorlage definiert ist. Im generischen Beispiel findet sich diese unter:
>`/etc/scaffolding/geometrixx-outdoors/order/jcr:content/cq:dialog`

Wenn eine Bestellung in AEM gespeichert wird, zeigt die Bestellungs-Konsole Folgendes für jede Bestellung an:

* die Anzahl der Artikel im Warenkorb
* den Gesamtwert der Bestellung
* den Zeitpunkt, zu dem die Bestellung aufgegeben wurde
* den Status

![chlimage_1-16](/help/sites-administering/assets/chlimage_1-16.png)

### Bestellverfolgung {#order-tracking}

Nach der Bestellung kehren die Käufer häufig zu folgenden Punkten zurück:

* Überprüfen des Status ihrer Bestellung
* Produkte aus der Bestellung entfernen
* Produkte zur Bestellung hinzufügen

Nach Erhalt des Bestellversands möchten die Käufer möglicherweise auch den Verlauf der über einen bestimmten Zeitraum erfolgten Bestellungen anzeigen.

Die Auftragserfüllung und -verfolgung werden von der eCommerce-Engine verwaltet. Informationen können über die Bestellverlauf-Komponente in AEM angezeigt werden, die alle relevanten Details aufführt, einschließlich der angewendeten Gutscheine und Promotions. Beispiel:

![chlimage_1-17](/help/sites-administering/assets/chlimage_1-17.png)

## Checkout {#checkout}

Das Auschecken wird mit standardmäßigen AEM-Formularen implementiert. Dadurch kann der Marketing-Manager das Erlebnis mit Marketing-Inhalten anpassen.

Der eCommerce verwaltet dann den Checkout-Prozess mit Eingaben aus den AEM Formularen.

### Zahlungssicherheit {#payment-security}

Zahlungsdetails wie Kreditkarteninformationen werden häufig von der eCommerce-Engine verwaltet. AEM leitet solche Transaktionsdaten an die Engine weiter (von wo aus sie dann zu einem Zahlungsdienstleister weitergeleitet werden).

Die Einhaltung des Payment Card Industry (PCI)-Standards kann erzielt werden.

### Bestellbestätigung {#confirmation-of-order}

Die Bestellung wird auf dem Bildschirm bestätigt und lässt sich mit der [Bestellungsnachverfolgung](#order-tracking) nachverfolgen.

## Suchen {#search-features}

![chlimage_1-18](/help/sites-administering/assets/chlimage_1-18.png)

Da AEM Standardseiten für Produkte nutzt, können Sie mit der Standard-Such-Komponente eine Suchseite erstellen.

Wenn Sie eine gründlichere Implementierung benötigen, können Sie entweder:

* Erweitern Sie die Standardsuchkomponente mit der benötigten Funktionalität.
* die Suchmethode im `CommerceService` implementieren und dann die eCommerce-Such-Komponente auf der Suchseite nutzen

Bei Nutzung einer E-Commerce-Engine kann die E-Commerce-Such-API vollständig in die E-Commerce-Engine-Lösung implementiert werden, sodass Sie die vorkonfigurierte E-Commerce-Such-Komponente nutzen können. Mit der Facettensuche können Sie JCR und/oder die Engine durchsuchen:
