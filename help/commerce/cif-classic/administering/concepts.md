---
title: Konzepte
description: Erfahren Sie mehr über die allgemeinen E-Commerce-Konzepte in Adobe Experience Manager.
contentOwner: Guillaume Carlino
exl-id: 290b2af6-257f-42f2-b809-1248227a4795
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '4439'
ht-degree: 100%

---

# Konzepte{#concepts}

Das Integrations-Framework stellt Mechanismen und Komponenten für die folgenden Vorgänge bereit:

* Verbinden mit einer E-Commerce-Engine
* Abrufen von Daten in Adobe Experience Manager (AEM)
* Anzeigen dieser Daten und Erfassen der Antworten der Kundinnen und Kunden
* Zurückgeben von Transaktionsdetails
* Durchsuchen der Daten aus beiden Systemen

Das heißt:

* Käuferinnen und Käufer können sich registrieren und ohne Wartezeit einkaufen.
* Preisänderungen werden von den Käuferinnen und Käufern unverzüglich wahrgenommen.
* Produkte können nach Bedarf hinzugefügt werden.

>[!NOTE]
>
>Das E-Commerce-Framework kann mit folgenden Lösungen verwendet werden:
>
>* [Adobe Commerce](/help/commerce/cif/integrating/magento.md)
>* [SAP Commerce Cloud](/help/commerce/cif-classic/administering/sap-commerce-cloud.md)
>* [Salesforce Commerce Cloud](https://github.com/adobe/commerce-salesforce)
>

>[!CAUTION]
>
>Das [eCommerce-Integrationsframework](https://business.adobe.com/de/products/experience-manager/sites/ecommerce-integrations.html) ist ein Add-on von AEM.
>
>Umfassende Informationen hierzu, passend zur entsprechenden Engine, erhalten Sie von dem für Sie zuständigen Vertriebsmitglied.

>[!CAUTION]
>
>Das Framework stellt die grundlegenden Voraussetzungen für Ihr eigenes Projekt bereit.
>
>Ein gewisses Maß an Entwicklungsarbeit ist immer erforderlich, um das Framework an Ihre Vorgaben anzupassen.

>[!CAUTION]
>
>Die AEM-Standardinstallation umfasst die generische E-Commerce-Implementierung (JCR) von AEM.
>
>Diese ist für Demonstrationszwecke oder als Basis für eine benutzerdefinierte Implementierung gemäß Ihren Anforderungen gedacht.

Um den Betrieb zu optimieren, konzentrieren sich AEM und die E-Commerce-Engine auf ihren jeweiligen Fachbereich. Informationen werden zwischen den beiden in Echtzeit übertragen, zum Beispiel:

* AEM kann:

   * Anfrage:

      * Produktinformationen aus der E-Commerce-Engine.

   * Geben Sie Folgendes an:

      * Benutzeransichten für Produktinformationen, Warenkorb und Checkout.
      * Warenkorb und Checkout-Informationen an die E-Commerce-Engine.
      * Suchmaschinenoptimierung (SEO).
      * Community-Funktionalität.
      * Unstrukturierte Marketing-Interaktionen.

* Die eCommerce-Engine kann:

   * Geben Sie Folgendes an:

      * Produktinformationen aus der Datenbank.
      * Verwaltung von Produktvarianten.
      * Order Management.
      * Enterprise Resource Planning (ERP)
      * Suche innerhalb der Produktinformationen.

   * Prozess:

      * Der Warenkorb
      * Der Checkout.
      * Auftragserfüllung

>[!NOTE]
>
>Die Details hängen von der E-Commerce-Engine und der Projektimplementierung ab.

Für die Verwendung der Integrationsschicht werden mehrere sofort einsatzbereite AEM-Komponenten bereitgestellt. Derzeit umfassen diese Folgendes:

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

AEM E-Commerce wird mit einer E-Commerce-Engine implementiert:

* Das E-Commerce-Integrations-Framework ermöglicht Ihnen die unkomplizierte Integration einer E-Commerce-Engine in AEM. Die speziell entwickelte E-Commerce-Engine steuert Produktdaten, Warenkörbe, Bezahlungen und die Auftragserfüllung. AEM steuert die Datenanzeige und Marketing-Kampagnen.


>[!NOTE]
>
>Die AEM-Standardinstallation umfasst die generische E-Commerce-Implementierung (JCR) von AEM.
>
>Diese ist für Demonstrationszwecke oder als Basis für eine benutzerdefinierte Implementierung gemäß Ihren Anforderungen gedacht.
>
>AEM E-Commerce, implementiert in AEM, mit generischer Entwicklung basierend auf JCR, ist:
>
>* Ein eigenständiges, AEM-natives E-Commerce-Beispiel, das die Nutzung der API veranschaulichen soll. Damit können Produktdaten, Warenkörbe und Checkout mit der vorhandenen Datenanzeige und Marketing-Kampagnen gesteuert werden. In diesem Fall ist die Produktdatenbank im nativen Repository von AEM gespeichert (die [JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)-Implementierung von Adobe).
>
>  Die standardmäßige AEM-Installation enthält die Grundlagen der [generischen E-Commerce-Implementierung](/help/commerce/cif-classic/administering/generic.md).

### Commerce-Anbieter {#commerce-providers}

Beim Importieren von Daten aus einer Commerce-Engine in Ihre AEM-E-Commerce-Site erhalten die Import-Tools ihre Daten von Commerce-Anbietern. Ein Commerce-Anbieter kann mehrere Import-Tools unterstützen.

Ein Commerce-Anbieter ist angepasster AEM-Code, der entweder

* eine Schnittstelle zu einer Backend-Commerce-Engine darstellt oder
* ein Commerce-System auf dem JCR-Repository implementiert.

Derzeit stehen beispielhaft zwei Commerce-Anbieter für AEM zur Verfügung:

* einer für geometrixx-hybris
* ein weiterer für geometrixx-generic (JCR)

Sie müssen jedoch für ein Projekt in der Regel einen eigenen, angepassten Commerce-Anbieter entsprechend dem PIM und Produktdatenschema entwickeln.

>[!NOTE]
>
>Die Geometrixx-Import-Tools verwenden CSV-Dateien. In den Kommentaren zu ihrer Implementierung finden Sie eine Beschreibung des akzeptierten Schemas (mit den zulässigen benutzerdefinierten Eigenschaften).

Der [ProductServicesManager](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/ProductServicesManager.html) verwaltet (über [OSGi](/help/sites-deploying/configuring.md#osgi-configuration-settings)) eine Liste der Implementierungen der [ProductImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/ProductImporter.html)- und [CatalogBlueprintImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/commerce/pim/api/CatalogBlueprintImporter.html)-Schnittstelle. Diese sind im Import-Tool-Assistenten im Dropdown-Feld **Import-Tool/Commerce-Anbieter** aufgeführt (mit der Eigenschaft `commerceProvider` als Name).

Wenn ein bestimmtes Import-Tool/ein bestimmter Commerce-Anbieter im Dropdown-Feld verfügbar ist, müssen Sie alle weiteren benötigten Daten (je nach Art des Import-Tools) unter einem der folgenden Pfade definieren:

* `/apps/commerce/gui/content/catalogs/importblueprintswizard/importers`
* `/apps/commerce/gui/content/products/importproductswizard/importers`

Der Ordner unter dem entsprechenden `importers`-Ordner muss mit dem Namen des Import-Tools übereinstimmen, z. B.:

* `.../importproductswizard/importers/geometrixx/.content.xml`

Das Format der Quell-Importdatei wird vom Import-Tool definiert. Alternativ kann das Import-Tool eine Verbindung (z. B. WebDAV oder HTTP) zur Commerce-Engine herstellen.

## Rollen {#roles}

Das integrierte System ermöglicht die Pflege der Daten durch die folgenden Rollen:

* Produktdatenverwaltung (PIM)-Benutzer, der Folgendes verwaltet:

   * Produktinformationen
   * Taxonomie, Kategorisierung, Genehmigung
   * Interaktion mit Digital Asset Management
   * Preisgestaltung: stammt häufig von einem ERP-System und wird nicht explizit im Commerce-System verwaltet

* Autor/Marketing-Manager, der Folgendes verwaltet:

   * Marketing-Inhalte für alle Kanäle.
   * Promotions.
   * Gutscheine.
   * Kampagnen.

* Surfende/Käuferinnen und Käufer, die:

   * die Produktinformationen anzeigen
   * Artikel in den Warenkorb legen
   * ihre Bestellung bezahlen
   * die Erfüllung ihrer Bestellung erwarten

Der tatsächliche Ort kann je nach Implementierung unterschiedlich ausfallen (z. B. generisch oder mit einer E-Commerce-Engine):

![chlimage_1-6](/help/sites-administering/assets/chlimage_1-6.png)

## Produkte {#products}

### Produktdaten gegenüber Marketing-Daten {#product-data-versus-marketing-data}

#### Strukturelle gegenüber Marketing-Kategorien {#structural-versus-marketing-categories}

Durch die Unterscheidung der folgenden beiden Kategorien können Sie deutliche URLs mit einer sinnvollen Struktur erstellen (Strukturen mit `cq:Page`-Knoten und daher dem klassischen Content-Management in AEM sehr ähnlich):

* *Strukturelle *Kategorien

  Kategoriestruktur, die definiert, *was ein Produkt ist*; Beispiel:

  `/products/mens/shoes/sneakers`

* *Marketing*-Kategorien

  Alle anderen Kategorien, zu denen ein *Produkt gehören kann*; Beispiel:

  `/special-offers/christmas/shoes`)

### Produktdaten {#product-data}

Um Ihr Produkt zu präsentieren und zu verwalten, sollten Sie eine Reihe von Informationen über das Produkt speichern.

Produktdaten können:

* direkt in AEM verwaltet werden (allgemein)
* in der eCommerce-Engine verwaltet und in AEM bereitgestellt werden

  Je nach Datentyp werden die Daten [synchronisiert](#catalog-maintenance-data-synchronization), falls erforderlich, oder sind direkt zugänglich. Höchst volatile und wichtige Daten wie Produktpreise werden beispielsweise bei jeder Seitenabfrage von der E-Commerce-Engine abgerufen, damit sie jederzeit aktuell sind.

In jedem Fall können Sie die Produktdaten nach der Eingabe bzw. dem Import in AEM über die **Produkt-Konsole** einsehen. Hier finden Sie in der Karten- und der Listenansicht eines Produkts u. a. folgende Informationen:

* das Bild
* den SKU-Code
* wann zuletzt geändert

![chlimage_1-7](/help/sites-administering/assets/chlimage_1-7.png)

### Produktvarianten {#product-variants}

Für entsprechende Produkte können auch Informationen über Varianten gespeichert werden. Beispielsweise werden bei Bekleidungsartikeln die unterschiedlichen angebotenen Farben als Varianten gespeichert:

![ecommerceproductvariables](/help/sites-administering/assets/ecommerceproductvariants.png)

### Produktattribute {#product-attributes}

Welche Attribute zu jedem Produkt gespeichert werden, hängt möglicherweise von der genutzten E-Commerce-Engine und Ihrer AEM-Implementierung ab. Sie sind jeweils entsprechend beim Anzeigen von Produktseiten und/oder Bearbeiten von Produktinformationen verfügbar und können Folgendes umfassen:

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

### Produkt-Assets {#product-assets}

Eine Auswahl von Assets kann für einzelne Produkte gespeichert werden. Dazu gehören in der Regel Bilder und Videos.

## Kataloge {#catalogs}

Ein Katalog fasst Produktdaten zusammen, um sowohl die Verwaltung als auch die Darstellung für die Käuferin bzw. den Käufer zu erleichtern. Häufig ist ein Katalog nach Attributen wie Sprache, geografisches Gebiet, Marke, Saison, Hobby, Sport und vielen anderen strukturiert.

### Katalogstruktur {#catalog-structure}

#### Kataloge in mehreren Sprachen {#catalogs-in-multiple-languages}

AEM unterstützt Produktinhalte in mehreren Sprachen. Beim Abfragen von Daten ruft das Integrations-Framework die Sprache vom aktuellen Baum ab (z. B. `en_US` für Seiten unter `/content/geometrixx-outdoors/en_US`).

Für einen mehrsprachigen Store können Sie Ihren Katalog für jeden Sprachbaum einzeln importieren (oder ihn mit [MSM](/help/sites-administering/msm.md) kopieren).

#### Kataloge für mehrere Marken {#catalogs-for-multiple-brands}

Ähnlich wie bei Sprachen müssen große, multinationale Unternehmen auch mehrere Marken bedienen.

#### Kataloge nach Tags {#catalogs-by-tags}

Tags können auch verwendet werden, um Produkte in einem Katalog zusammenzufassen. Dieser Ansatz bietet sich für dynamischere Kataloge an.

### Katalogeinrichtung (erster Import) {#catalog-setup-initial-import}

Abhängig von Ihrer Implementierung können Sie die für Ihren Basiskatalog erforderlichen Produktdaten in AEM importieren:

* eine CSV-Datei (für die allgemeine Implementierung)
* die E-Commerce-Engine

### Katalogwartung (Datensynchronisierung) {#catalog-maintenance-data-synchronization}

Weitere Änderungen der Produktdaten sind unvermeidlich:

* für die generische Implementierung, sie können mit dem [Produkt-Editor](/help/commerce/cif-classic/administering/generic.md#editing-product-information) verwaltet werden
* die Verwendung einer [eCommerce-Engine; hier müssen die Änderungen synchronisiert werden](#data-synchronization-with-an-ecommerce-engine-ongoing)

#### Datensynchronisation mit einer E-Commerce-Engine (fortlaufend) {#data-synchronization-with-an-ecommerce-engine-ongoing}

Nach dem ersten Import sind Änderungen an Ihren Produktdaten unvermeidlich.

Bei Verwendung einer E-Commerce-Engine werden die Produktdaten dort gespeichert und müssen in AEM verfügbar sein. Diese Produktdaten müssen nach Aktualisierungen synchronisiert werden.

Dies kann vom Datentyp abhängen:

* Eine [periodische Synchronisierung wird zusammen mit einem Daten-Feed der Änderungen verwendet](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#product-synchronization-and-publishing).

  Zusätzlich können Sie bestimmte Aktualisierungen für ein Express-Update auswählen.

* Stark schwankende Daten wie Preisinformationen werden für jede Seitenanfrage von der Commerce-Engine abgerufen, um sicherzustellen, dass sie immer auf dem neuesten Stand sind.

### Kataloge – Leistung und Skalierung {#catalogs-performance-and-scaling}

Der Import eines großen Katalogs mit einer sehr großen Anzahl von Produkten (über 100.000) aus einer E-Commerce-Engine (PIM) kann sich aufgrund der großen Anzahl von Knoten auf das System auswirken. Er kann auch die Autoreninstanz verlangsamen, wenn die Produkte über verknüpfte Assets verfügen (beispielsweise Produktbilder). Dies liegt daran, dass die Nachbearbeitung dieser Assets CPU- und speicherintensiv ist.

Es gibt verschiedene Strategien, die Sie wählen können, um diese Probleme zu umgehen:

* [Buckets](#bucketing) – um die große Anzahl an Knoten zu unterstützen
* [Abladen der Asset-Nachbearbeitung auf einer dedizierten Instanz](#offload-asset-post-processing-to-a-dedicated-instance)
* [Importieren von Produktdaten ohne Assets](#only-import-product-data)
* [Importbeschränkung und Batch-Speicherung](#import-throttling-and-batch-saves)
* [Leistungstests](#performance-testing)
* [Leistung – Verschiedenes](#performance-miscellaneous)

#### Bucketing {#bucketing}

Wenn ein JCR-Knoten viele direkt untergeordnete Knoten hat (z. B. 1000 und mehr), sind Buckets (Phantom-Ordner) erforderlich, um sicherzustellen, dass die Leistung nicht beeinträchtigt wird. Diese werden beim Import anhand eines Algorithmus generiert.

Diese Buckets haben die Form von Phantom-Ordnern, die in Ihre Katalogstruktur eingeführt werden, aber so konfiguriert werden können, dass sie in öffentlichen URLs nicht sichtbar sind.

#### Auslagern der Asset-Nachbearbeitung auf eine dedizierte Instanz {#offload-asset-post-processing-to-a-dedicated-instance}

Dieses Szenario umfasst das Einrichten von zwei Autoreninstanzen:

1. Primäre Autoreninstanz

   Importiert Produktdaten vom PIM, auf dem die Nachbearbeitung für Asset-Pfade deaktiviert ist.

1. Dedizierte DAM-Autoreninstanz

   Importiert Produkt-Assets aus dem PIM, bearbeitet sie nach und repliziert sie zur Nutzung zurück zur primären Autoreninstanz.

![Architekturdiagramm](/help/sites-administering/assets/chlimage_1-8.png)

#### Importieren von Produktdaten ohne Assets {#only-import-product-data}

Wenn Produkte keine Assets (Bilder) enthalten, die importiert werden sollen, können Sie die Produktdaten importieren, ohne von einer Nachbearbeitung der Assets beeinträchtigt zu werden.

![Architekturdiagramm](/help/sites-administering/assets/chlimage_1-9.png)

#### Leistungstests {#performance-testing}

Leistungstests müssen in AEM E-Commerce-Implementierungen berücksichtigt werden:

* Autorenumgebung:

  Eine Hintergrundaktivität (z. B. ein Importvorgang) kann gleichzeitig mit einer normalen Benutzeraktivität (z. B. Seitenbearbeitung) ausgeführt werden. Selbst wenn der Frontend-Leistung (im Allgemeinen) eine höhere Priorität zugeschrieben wird, kann eine mangelhafte Leistung, die Online-Autorinnen und -Autoren erleben, demotivieren und sogar eine Entscheidung, live zu gehen, blockieren.

* Veröffentlichungsumgebung:

  Die Replikation ist wichtig, um sicherzustellen, dass die Inhalte schnell und zuverlässig veröffentlicht werden. Dies kann dadurch beeinflusst werden, wie der Autor die Inhalte gruppiert, die veröffentlicht werden sollen.

* Frontend:

  Kombination aus Frontend- und Cache-Invalidierung kann zu Leistungseinbußen führen. Tests helfen dabei, diese zu vermeiden.

Beachten Sie, dass dieser Leistungstest Kenntnisse und Analysen Ihrer Zielgruppe erfordert:

* Inhaltsvolumen

   * Assets
   * Lokalisierte i18n-Produkte und SKUs

* Benutzeraktivität:

   * Massenbearbeitung
   * Massenveröffentlichung
   * Intensive Suchanfragen

* Hintergrundprozesse

   * Importvorgänge
   * Synchronisierungsaktualisierungen (z. B. Preisgestaltung)

* Wartungsanforderungen (Backup, Tar-PM-Optimierung, Datenspeicherbereinigung usw.)

#### Leistung – Verschiedenes {#performance-miscellaneous}

Bei allen Implementierungen ist es gut, die folgenden Punkte zu beachten:

* Da Produkt, Lagereinheiten und Kategorien zahlreich sein können, versuchen Sie, die geringstmögliche Anzahl von Knoten zur Modellierung des Inhalts zu verwenden.

  Je mehr Knoten Sie nutzen, desto flexibler sind Ihre Inhalte (z. B. ParSys). Alles ist jedoch ein Kompromiss. Benötigen Sie etwa standardmäßig individuelle Flexibilität, wenn Sie (beispielsweise) mit 30.000 Produkten zu tun haben?

* Vermeiden Sie Duplizierungen so oft wie möglich (siehe Lokalisierung) oder überlegen Sie, zu wie vielen Knoten Ihre Duplizierung führt.
* Versuchen Sie, Ihren Inhalt so oft wie möglich mit Tags zu versehen, um die Abfrageoptimierung vorzubereiten.

  Zum Beispiel:

  `/content/products/france/fr/shoe/reebok/pump/46 SKU`

  sollte es ein Tag pro Inhaltsebene geben (d. h. Land, Sprache, Kategorie, Marke, Produkt). Die Suche nach

  `//element(*,my:Sku)[@country='france' and @language='fr'`

  und

  `@category='shoe' and @brand='reebok' and @product='pump']`

  wird drastisch schneller sein als die Suche nach

  `/jcr:root/content/france/fr/shoe/reebok/pump/element(*,my:Sku)`

* Planen Sie in Ihrem technischen Stack das faktorisierte Inhaltszugriffsmodell und Dienste. Dies ist allgemein eine Best Practice, in diesem Fall aber sogar noch wichtiger, da Sie in Optimierungsphasen Anwendungs-Caches für Daten hinzufügen können, die häufig gelesen werden (und nicht den Bundle-Cache füllen sollten).

  Beispielsweise ist die Attributverwaltung oft gut für das Caching geeignet, da sie Daten betrifft, die durch das Importieren von Produkten aktualisiert werden.
* Ziehen Sie die Nutzung von [Proxy-Seiten](#proxy-pages) in Erwägung.

### Katalogbereichsseiten {#catalog-section-pages}

In Katalogbereichen finden Sie zum Beispiel:

* eine Einleitung (Bild und/oder Text) für die Kategorie; hier können auch Banner und Teaser für Sonderangebote werben
* Links zu den einzelnen Produkten in dieser Kategorie
* Links zu den anderen Kategorien

![ecommerce_categoryrunning](/help/sites-administering/assets/ecommerce_categoryrunning.png)

### Produktseiten {#product-pages}

Produktseiten bieten umfassende Informationen zu einzelnen Produkten. Hier spiegeln sich auch dynamische Aktualisierungen wider, z. B. Preisänderungen, die auf der E-Commerce-Engine erfolgt sind.

Produktseiten sind AEM-Seiten, die die **Produkt-Komponente** nutzen, beispielsweise in der Vorlage **Commerce-Produkt**:

![ecommerce_nairobirunnersgreen](/help/sites-administering/assets/ecommerce_nairobirunnersgreen.png)

Die Produkt-Komponente bietet:

* allgemeine Produktinformationen, darunter Text und Bilder
* Preise (diese werden bei jedem Aufruf bzw. jeder Aktualisierung der Seite von der E-Commerce-Engine abgerufen)
* Informationen zu Produktvarianten, z. B. Farbe und Größe

Anhand dieser Daten kann der Käufer folgende Optionen auswählen, wenn er einen Artikel zum Warenkorb hinzufügt:

* Farb- und Größenvarianten
* Menge

#### Produkt-Landingpages {#product-landing-pages}

Dies sind AEM-Seiten, die hauptsächlich statische Informationen enthalten, z. B. eine Einführung und ein Überblick mit Links zu den zugrunde liegenden Produktseiten.

### Produktkomponente {#product-component}

Die **Produktkomponente** können Sie zu jeder Seite mit einer übergeordneten Seite hinzufügen, welche die benötigten Metadaten bereitstellt (d. h. die Pfade zu `cartPage` und `cartObject`). Bei der Demo-Website, Geometrixx Outdoors, ist dies `UserInfo.jsp`.

Sie können die **Produktkomponente** auch an Ihre individuellen Anforderungen anpassen.

### Proxy-Seiten {#proxy-pages}

Proxy-Seiten werden verwendet, um die Struktur des Repositorys zu vereinfachen und den Speicher für große Kataloge zu optimieren.

Beim Erstellen eines Katalogs werden zehn Knoten pro Produkt verwendet, da er einzelne Komponenten für jedes Produkt bereitstellt, die Sie in AEM aktualisieren und anpassen können. Diese große Anzahl von Knoten kann zu einem Problem werden, wenn Ihr Katalog Hunderte oder gar Tausende von Produkten enthält. Um Probleme zu vermeiden, können Sie Ihren Katalog mit Proxy-Seiten erstellen.

Proxy-Seiten nutzen eine Struktur mit zwei Knoten (`jcr:content` und `cq:Page`), die keine Produktinhalte enthalten. Die Inhalte werden zur Abfragezeit durch Verweise auf die Produktdaten und die Vorlagenseite generiert.

Dabei gilt allerdings: Sie können die Produktdaten nicht in AEM anpassen. Es wird eine Standardvorlage (für Ihre Site definiert) verwendet.

>[!NOTE]
>
>Wenn Sie einen großen Katalog ohne Proxy-Seiten importieren, treten keine Probleme auf.
>
>Die Konversion von einer Methode zur anderen ist jederzeit möglich. Sie können auch einen Teilbereich Ihres Katalogs umwandeln.

## Promotions und Gutscheine {#promotions-and-vouchers}

### Gutscheine {#vouchers}

Gutscheine sind eine bewährte Methode, Rabatte anzubieten – entweder um Käuferinnen und Käufer dazu zu bewegen, einen Kauf zu tätigen, und/oder um die Treue der Kundschaft zu belohnen.

* Zu Gutscheinen gehört:

   * Ein Gutschein-Code (der von der kaufenden Person in den Warenkorb eingegeben wird).
   * Eine Gutscheinbeschriftung (die angezeigt wird, nachdem die Person sie im Warenkorb eingegeben hat).
   * Ein Promotion-Pfad (der die Aktion definiert, die der Gutschein auslöst).

* Externe Commerce-Engines können ebenfalls Gutscheine bereitstellen.

In AEM gilt:

* Ein Gutschein ist eine seitenbasierte Komponente, die mit der Websites-Konsole erstellt und bearbeitet wird.
* Die **Gutschein**-Komponente bietet:

   * einen Renderer für die Gutscheinadministration; er zeigt alle Gutscheine an, die sich aktuell im Warenkorb befinden
   * Die Bearbeitungsdialogfelder (Formular) zum Verwalten (Hinzufügen/Entfernen) der Gutscheine.
   * Die für das Hinzufügen/Entfernen von Gutscheinen zum/vom Warenkorb erforderlichen Aktionen.

* Gutscheine haben keine eigenen Datums-/Zeitangaben für Aktivierung und Deaktivierung, sondern nutzen die der übergeordneten Kampagnen.

>[!NOTE]
>
>AEM verwendet den Begriff **Gutschein**, der ein Synonym zu **Coupon** ist.

### Promotions {#promotions}

Mit Promotions können Sie in Verbindung mit Gutscheinen Szenarien umsetzen wie z. B.:

* Ein Unternehmen bietet Sonderpreise für Mitarbeitende an: eine manuell zusammengestellte Liste von Benutzenden.
* Langfristige Kundinnen und Kunden erhalten Rabatte auf alle Bestellungen.
* Ein Verkaufspreis, der über einen genau festgelegten Zeitraum angeboten wird.
* Eine Kundin oder ein Kunde erhält einen Gutschein, wenn die vorherige Bestellung einen bestimmten Betrag überschritten hat.
* Kundinnen oder Kunden, die *Produkt X* kaufen, wird ein Rabatt auf *Produkt Y* angeboten (Produktpaarung).

Promotions werden nicht von Produktinformations-Managern verwaltet, sondern von Marketing-Managern:

* Eine Promotion ist eine seitenbasierte Komponente, die mit der Websites-Konsole erstellt und bearbeitet wird. ``
* Zu Promotions gehört:

   * Eine Priorität
   * Ein Promotion-Handler-Pfad

* Sie können Promotions mit einer Kampagne verknüpfen, um deren Aktivierungs-/Ablaufzeiten zu definieren.
* Sie können Promotions mit einem Erlebnis verbinden, um deren Segmente zu definieren.
* Promotions, die nicht mit einem Erlebnis verbunden sind, werden nicht allein ausgelöst, können aber von einem Gutschein ausgelöst werden.
* Die Promotion-Komponente umfasst:

   * Renderer und Dialogfelder für die Promotions-Administration
   * Unterkomponenten zum Rendern und Bearbeiten von Konfigurationsparametern, die spezifisch für die Promotion-Handler sind

In AEM sind die Promotions auch in das [Kampagnen-Management](/help/sites-authoring/personalization.md) integriert:

* Eine [Kampagne](/help/sites-authoring/personalization.md) legt die Zeiten für Aktivierung/Deaktivierung fest
* [Erlebnisse](/help/sites-authoring/personalization.md) *innerhalb* der Kampagne dienen dazu, Assets (Teaser-Seiten, Promotions usw.) je nach dem entsprechenden Zielgruppensegment zu gruppieren

Eine Promotion kann entweder in einem Erlebnis oder direkt in der Kampagne gespeichert werden:

* Wenn eine Promotion in einem Erlebnis gespeichert wird, kann sie automatisch auf ein Zielgruppensegment angewendet werden.

  Beispielsweise die Promotion auf der Beispielsite geometrixx-outdoors:

  `/content/campaigns/geometrixx-outdoors/big-spender/ordervalueover100/free-shipping`

  befindet sich in einem Erlebnis, wird also immer dann automatisch ausgelöst, wenn das Segment ( `ordervalueover100`) aufgelöst wird.

* Wenn eine Promotion nicht in einem Erlebnis angezeigt wird (also nur in der Kampagne), kann sie nicht automatisch auf eine Zielgruppe angewendet werden. Sie kann jedoch dennoch ausgelöst werden, wenn ein Käufer einen Gutschein im Warenkorb eingibt und dieser Gutschein auf die Promotion verweist.

  Zum Beispiel gilt für die Promotion:

  `/content/campaigns/geometrixx-outdoors/article/10-bucks-off`

  Sie befindet sich außerhalb eines Erlebnisses und wird daher nie automatisch (d. h. basierend auf der Segmentierung) ausgelöst. Jedoch verweisen Gutscheine, die sich in mehreren Erlebnissen innerhalb der Artikelkampagne befinden können, auf diese Promotion. Werden diese Gutschein-Codes im Warenkorb eingegeben, wird die Promotion ausgelöst.

>[!NOTE]
>
>[hybris-Promotions](https://www.hybris.com/modules/promotion) und [hybris-Gutscheine](https://www.hybris.com/en/modules/voucher) decken alles ab, was sich auf den Warenkorb auswirkt und mit der Preisgestaltung in Zusammenhang steht. Promotion-spezifische Marketing-Inhalte (wie Banner usw.) sind nicht Teil der hybris-Promotion.

## Personalisierung  {#personalization}

### Kundenregistrierung und -konten {#customer-registration-and-accounts}

Wenn sich Käuferinnen und Käufer registrieren, müssen die Kontodetails zwischen AEM und der E-Commerce-Engine synchronisiert werden. Sensible Daten werden separat gespeichert, die Profile sind jedoch freigegeben:

![chlimage_1-10](/help/sites-administering/assets/chlimage_1-10.png)

Der genaue Mechanismus hängt vom Szenario ab:

1. Das Benutzerkonto ist auf beiden Systemen vorhanden:

   1. Keine Aktion erforderlich.

1. Das Benutzerkonto existiert nur in AEM:

   1. Benutzende werden in der E-Commerce-Engine mit derselben Konto-ID und einem zufälligen Passwort erstellt, das in AEM gespeichert wird.
   1. Das zufällig generierte Kennwort ist nötig, weil AEM beim ersten Aufruf (wenn beispielsweise eine Produktseite angefragt und für den Preis auf die eCommerce-Engine verwiesen wird) versucht, sich bei der eCommerce-Engine anzumelden. Da dies nach der AEM-Anmeldung geschieht, ist das Passwort nicht verfügbar.

1. Das Benutzerkonto existiert nur in der E-Commerce-Engine:

   1. Das Konto wird in AEM mit derselben Konto-ID und demselben Passwort erstellt.

Bei Verwendung einer E-Commerce-Engine speichert AEM nur die Konto-ID und das Passwort (optional eine Benutzergruppe). Alle anderen Daten werden in der eCommerce-Engine gespeichert.

>[!NOTE]
>
>Bei Verwendung einer E-Commerce-Engine müssen Sie sicherstellen, dass Konten, die für Benutzende erstellt wurden, die sich bei einer AEM-Instanz anmelden (z. B. über Workflows), für alle anderen AEM-Instanzen repliziert werden, die mit dieser Engine kommunizieren.
>
>Andernfalls werden diese anderen AEM-Instanzen versuchen, ebenfalls Konten für dieselben Benutzenden in der Engine zu erstellen. Diese Aktionen scheitern mit einer `DuplicateUidException`, die von der Engine kommt.

### Kundenregistrierung {#customer-sign-up}

Häufig ist eine Registrierung erforderlich, damit die Käuferin bzw. der Käufer Zugriff auf den Warenkorb hat. Dafür ist eine Registrierung (Konto erstellen) nötig, damit ein kundenspezifisches Konto erstellt werden kann.

![chlimage_1-11](/help/sites-administering/assets/chlimage_1-11.png)

>[!NOTE]
>
>Ein anonymer Warenkorb und ein anonymer Checkout werden ebenfalls unterstützt.

### Kundenanmeldung {#customer-sign-in}

Nach der Registrierung kann sich die Kundin bzw. der Kunde im Konto anmelden, damit die Aktionen nachverfolgt und die Bestellungen bearbeitet werden können.

![chlimage_1-12](/help/sites-administering/assets/chlimage_1-12.png)

### Single Sign-on {#single-sign-on}

Single Sign-on (SSO) wird bereitgestellt, sodass Autorinnen und Autoren sowohl in AEM als auch im E-Commerce-System bekannt sind, ohne sich zweimal anmelden zu müssen.

### myAccount {#myaccount}

Transaktionsdaten von der E-Commerce-Engine werden mit personenbezogenen Daten zur Käuferin bzw. zum Käufer kombiniert. AEM verwendet einige dieser Daten als Profildaten. Bei einer Aktion eines Formulars in AEM werden Informationen an die E-Commerce-Engine zurückgeschrieben.

Es gibt eine Seite, auf der Sie Ihre Kontodaten leicht verwalten können. Um diese Seite anzuzeigen, klicken Sie oben auf der Geometrixx-Seite auf **Mein Konto** oder gehen Sie zu `/content/geometrixx-outdoors/en/user/account.html`.

![chlimage_1-13](/help/sites-administering/assets/chlimage_1-13.png)

### Adressbuch {#address-book}

Ihre Site muss eine Auswahl von Adressen speichern, einschließlich Versand-, Abrechnungs- und alternativen Adressen. Dies kann entweder mithilfe von Formularen implementiert werden, die auf Ihrem Standard-Adressformat basieren, oder Sie können die Komponente „Adressbuch“ verwenden, die von AEM bereitgestellt wird.

Mit der Adressbuch-Komponente können Sie:

* Adressdaten im Buch bearbeiten
* eine Adresse aus dem Buch für die Lieferadresse auswählen
* eine Adresse aus dem Buch für die Rechnungsadresse auswählen

Sie können auswählen, welche Adresse Sie als Standard verwenden möchten.

Die Adressbuch-Komponente finden Sie auf der Seite **Mein Konto** durch Klicken auf **Adressbuch** oder indem Sie zu `/content/geometrixx-outdoors/en/user/account/address-book.html` gehen.

![chlimage_1-14](/help/sites-administering/assets/chlimage_1-14.png)

Klicken Sie auf **Neue Adresse hinzufügen…**, um eine neue Adresse zum Adressbuch hinzuzufügen. Dadurch wird ein Formular geöffnet, das Sie ausfüllen können. Klicken Sie dann auf **Adresse hinzufügen**.

>[!NOTE]
>
>Sie können mehrere Adressen in Ihr Adressbuch eingeben.

Das Adressbuch wird verwendet, wenn Sie mit Ihrem Warenkorb zum Checkout gehen:

![chlimage_1-15](/help/sites-administering/assets/chlimage_1-15.png)

Adressen werden unter `user_home/profile/addresses` aufbewahrt.
Die Adresse von Alison Parker befindet sich beispielsweise unter /home/users/geometrixx/aparker@geometrixx.info/profile/addresses.

Sie können auswählen, welche Adresse Sie als Standard festlegen möchten. Diese Information wird im Käuferprofil gespeichert, nicht zusammen mit der Anschrift. Als Wert für die Profileigenschaft `address.default` wird der Pfad der ausgewählten Adresse festgelegt.

### Kundenspezifische Preise {#customer-specific-pricing}

Die E-Commerce-Engine verwendet den Kontext (im Wesentlichen die Informationen zu den Käuferinnen und Käufern), um den Preis zu bestimmen und die richtigen Informationen an AEM weiterzugeben.

## Warenkorb und Bestellungen {#shopping-cart-and-orders}

Beim Einkauf durchsucht die Käuferin bzw. der Käufer die Produktseiten und wählt die Artikel aus, um sie in den Warenkorb zu legen. Beim Kassengang kann eine Bestellung aufgegeben werden.

### Anonyme Käufer {#anonymous-shoppers}

Ein anonymer Käufer kann:

* Produkte anzeigen
* Produkte zum Warenkorb hinzufügen
* Checkout durchführen, um die Bestellung aufzugeben

>[!NOTE]
>
>Je nach Konfiguration Ihrer Instanz können vor dem Checkout Informationen zur Adresse oder zur Kundenregistrierung erforderlich sein.

### Registrierte Käuferinnen und Käufer {#registered-shoppers}

Ein registrierter Käufer kann:

* sich in ihrem Konto anmelden
* Produkte anzeigen
* Produkte zum Warenkorb hinzufügen
* Checkout durchführen, um die Bestellung aufzugeben
* Anzeigen und Verfolgen früherer Bestellungen

### Übersicht über den Inhalt des Warenkorbs {#shopping-cart-content-overview}

Der Warenkorb bietet:

* eine Übersicht über die ausgewählten Elemente
* Links zu den Produktseiten für die ausgewählten Artikel
* die Möglichkeit,

   * die Anzahl/Menge der einzelnen Elemente zu aktualisieren
   * einzelne Elemente zu entfernen

![ecommerce_shoppingcart](/help/sites-administering/assets/ecommerce_shoppingcart.png)

Der Warenkorb wird je nach verwendeter Engine gespeichert:

* Die generische AEM-Version speichert den Warenkorb in einem Cookie.
* Bestimmte E-Commerce-Engines können den Warenkorb in einer Sitzung speichern.

In beiden Fällen bleiben Artikel unabhängig von einer Anmeldung/Abmeldung im Warenkorb (und können wiederhergestellt werden), aber nur auf demselben Computer/Browser. Beispiel:

* Surfen Sie `anonymous` und fügen Sie Produkte zum Warenkorb hinzu.
* Melden Sie sich als `Allison Parker` an. Der Warenkorb von Allison ist leer.
* Fügen Sie Produkte zu ihrem Warenkorb hinzu.
* Melden Sie sich ab. Der Warenkorb zeigt die Produkte für `anonymous` an.

* Melden Sie sich erneut als `Allison Parker` an. Die Produkte von Allison werden wiederhergestellt.

>[!NOTE]
>
>Ein anonymer Warenkorb kann nur auf demselben Rechner und im selben Browser wiederhergestellt werden.

>[!NOTE]
>
>Wir raten davon ab, die Wiederherstellung der Warenkorbinhalte mit dem `admin`-Konto zu testen, da dabei ein Konflikt mit dem `admin`-Konto der E-Commerce-Engine (z. B. hybris) auftreten kann.

>[!NOTE]
>
>hybris kann so konfiguriert werden, dass ausstehende Warenkörbe nach einem bestimmten Zeitraum entfernt werden.

Vor dem Checkout werden Preisänderungen (in beiden Systemen) übernommen, sobald sie auftreten.

### Bestellinformationen {#order-information}

Abhängig von Ihrer Implementierung werden Informationen zu einer Bestellung entweder in der E-Commerce-Engine oder in AEM gespeichert. Diese Informationen werden von AEM gerendert.

Es werden verschiedene Informationen gespeichert, beispielsweise:

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

  Der Gesamtbetrag der Bestellung: bestellte Artikel, Steuern und Versandkosten.

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
>Welche Felder im Assistenten „Auftrag erstellen“ verwendet werden, hängt davon ab, ob für den Ort eine Touch-optimierte Strukturvorlage definiert ist. Im generischen Beispiel findet sich diese unter:
>`/etc/scaffolding/geometrixx-outdoors/order/jcr:content/cq:dialog`

Wenn eine Bestellung in AEM gespeichert wird, zeigt die Bestellungs-Konsole Folgendes für jede Bestellung an:

* die Anzahl der Artikel im Warenkorb
* den Gesamtwert der Bestellung
* den Zeitpunkt, zu dem die Bestellung aufgegeben wurde
* den Status

![chlimage_1-16](/help/sites-administering/assets/chlimage_1-16.png)

### Bestellverfolgung {#order-tracking}

Nach der Bestellung kehren die Käuferinnen und Käufer häufig zu folgenden Punkten zurück:

* Überprüfen des Status ihrer Bestellung
* Produkte aus der Bestellung entfernen
* Produkte zur Bestellung hinzufügen

Nach der Lieferung der Bestellung möchten die Käuferinnen und Käufer möglicherweise auch den Verlauf der über einen bestimmten Zeitraum erfolgten Bestellungen einsehen.

Die Erfüllung und die Nachverfolgung von Bestellungen werden von der E-Commerce-Engine verwaltet. Informationen können über die Bestellverlauf-Komponente in AEM angezeigt werden, die alle relevanten Details aufführt, einschließlich der angewendeten Gutscheine und Promotions. Beispiel:

![chlimage_1-17](/help/sites-administering/assets/chlimage_1-17.png)

## Checkout {#checkout}

Der Checkout wird mit standardmäßigen AEM-Formularen implementiert. Dadurch können Marketing-Fachleute das Erlebnis mit Marketing-Inhalten anpassen.

Der E-Commerce verwaltet dann den Checkout-Prozess mit Eingaben aus den AEM Formularen.

### Zahlungssicherheit {#payment-security}

Zahlungsdetails wie Kreditkarteninformationen werden häufig von der E-Commerce-Engine verwaltet. AEM leitet solche Transaktionsdaten an die Engine weiter (von wo aus sie dann zu einem Zahlungsdienstleister weitergeleitet werden).

Die Einhaltung des Payment Card Industry (PCI)-Standards kann erzielt werden.

### Bestellbestätigung {#confirmation-of-order}

Die Bestellung wird auf dem Bildschirm bestätigt und lässt sich mit der [Bestellungsnachverfolgung](#order-tracking) nachverfolgen.

## Suchen {#search-features}

![chlimage_1-18](/help/sites-administering/assets/chlimage_1-18.png)

Da AEM Standardseiten für Produkte nutzt, können Sie mit der Standard-Such-Komponente eine Suchseite erstellen.

Wenn Sie eine gründlichere Implementierung benötigen, können Sie entweder:

* die Standardsuchkomponente um die benötigten Funktionen erweitern
* die Suchmethode im `CommerceService` implementieren und dann die eCommerce-Such-Komponente auf der Suchseite nutzen

Bei Nutzung einer E-Commerce-Engine kann die E-Commerce-Such-API vollständig in die E-Commerce-Engine-Lösung implementiert werden, sodass Sie die vorkonfigurierte E-Commerce-Such-Komponente nutzen können. Mit der Facettensuche können Sie JCR und/oder die Engine durchsuchen:
