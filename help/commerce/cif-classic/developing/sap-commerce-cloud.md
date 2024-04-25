---
title: Entwicklung mit SAP Commerce Cloud
description: Das Integrations-Framework SAP Commerce Cloud enthält eine Integrationsebene mit einer API.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
exl-id: b3de1a4a-f334-44bd-addc-463433204c99
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '2303'
ht-degree: 100%

---

# Entwickeln mit SAP Commerce Cloud {#developing-with-sap-commerce-cloud}

>[!NOTE]
>
>Das eCommerce-Framework kann mit jeder eCommerce-Lösung verwendet werden. Bestimmte hier behandelte Aspekte und Beispiele beziehen sich auf die [hybris](https://www.sap.com/germany/products/crm.html)-Lösung.

Das Integrations-Framework enthält eine Integrationsebene mit einer API. Damit können Sie:

* ein E-Commerce-System einbinden und Produktdaten in AEM (Adobe Experience Manager) abrufen

* AEM-Komponenten für Commerce-Funktionen erstellen, und zwar unabhängig von der jeweiligen E-Commerce-Engine

![chlimage_1-11](/help/sites-developing/assets/chlimage_1-11a.png)

>[!NOTE]
>
>[API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) ist ebenfalls verfügbar.

Für die Verwendung der Integrationsschicht werden mehrere sofort einsatzbereite AEM-Komponenten bereitgestellt. Derzeit sind dies:

* Produktanzeige
* Warenkorb
* Checkout

Für die Suche ist ein Integrations-Hook verfügbar, mit dem Sie die Suchfunktion von AEM, des E-Commerce-Systems oder eines Drittanbieters separat oder in Kombination verwenden können.

## Auswahl der E-Commerce-Engine {#ecommerce-engine-selection}

Das E-Commerce-Framework kann mit einer beliebigen E-Commerce-Lösung verwendet werden, allerdings muss die verwendete Engine von AEM identifizierbar sein:

* eCommerce-Engines sind OSGi-Services, die die `CommerceService`-Schnittstelle unterstützen.

   * Engines können anhand einer `commerceProvider`-Service-Eigenschaft identifiziert werden.

* AEM unterstützt `Resource.adaptTo()` für `CommerceService` und `Product`.

   * Die `adaptTo`-Implementierung sucht nach einer `cq:commerceProvider`-Eigenschaft in der Hierarchie der Ressource:

      * Wenn der Wert gefunden wird, wird er zum Filtern der Suche nach einem Commerce-Service verwendet.

      * Wenn nicht gefunden, wird der Commerce-Service mit dem höchsten Rang verwendet.

   * Ein `cq:Commerce`-Mixin wird verwendet, um `cq:commerceProvider` zu stark typisierten Ressourcen hinzuzufügen.

* Die `cq:commerceProvider`-Eigenschaft wird auch als Verweis auf die geeignete Commerce-Factory-Definition verwendet.

   * Eine `cq:commerceProvider`-Eigenschaft mit dem Wert `hybris` korreliert beispielsweise mit der OSGi-Konfiguration für **Day CQ Commerce Factory for Hybris** (com.adobe.cq.commerce.hybris.impl.HybrisServiceFactory), wobei der Parameter `commerceProvider` auch den Wert `hybris` aufweist.

   * In diesem Fall können weitere Eigenschaften wie **Catalog version** konfiguriert werden (falls zutreffend und verfügbar).

Siehe folgendes Beispiel:

| `cq:commerceProvider = geometrixx` | In einer AEM-Standardinstallation ist eine bestimmte Implementierung erforderlich. Beispiel: das Geometrixx-Beispiel, das minimale Erweiterungen der generischen API enthält |
|--- |--- |
| `cq:commerceProvider = hybris` | Hybris-Implementierung |

### Beispiel {#example}

```shell
/content/store
+ cq:commerceProvider = hybris
  + mens
    + polo-shirt-1
    + polo-shirt-2
    + employee
+ cq:commerceProvider = jcr
  + adobe-logo-shirt
    + cq:commerceType = product
    + price = 12.50
  + adobe-logo-shirt_S
    + cq:commerceType = variant
    + size = S
  + adobe-logo-shirt_XL
    + cq:commerceType = variant
    + size = XL
    + price = 14.50
```

>[!NOTE]
>
>Bei Verwendung von CRXDE Lite können Sie sehen, wie dies in der Produktkomponente für die Hybris-Implementierung gehandhabt wird:
>
>`/apps/geometrixx-outdoors/components/hybris/product/product.jsp`

### Entwickeln für Hybris 4 {#developing-for-hybris}

Die Hybris-Erweiterung des eCommerce-Integrations-Frameworks wurde aktualisiert und unterstützt jetzt Hybris 5, wobei die Rückwärtskompatibilität mit Hybris 4 ebenfalls gewährleistet bleibt.

Die Standardeinstellungen im Code sind auf Hybris 5 abgestimmt.

Für das Entwickeln mit Hybris 4 ist Folgendes erforderlich:

* Fügen Sie beim Aufrufen von Maven das folgende Befehlszeilenargument zum Befehl hinzu:

  `-P hybris4`

  Es lädt die vorkonfigurierte Hybris 4-Distribution herunter und bettet sie in das Paket `cq-commerce-hybris-server` ein.

* Nehmen Sie im OSGi-Konfigurations-Manager folgende Einstellungen vor:

   * Deaktivieren Sie die Hybris 5-Unterstützung für den Default Response Parser-Service.

   * Stellen Sie sicher, dass der Hybris Basic Authentication Handler-Dienst einen niedrigeren Rang als der Hybris OAuth Handler-Dienst hat.

### Session-Handling {#session-handling}

Hybris verwendet eine Benutzersitzung, um Informationen wie den Warenkorb der Kundin bzw. des Kunden zu speichern. Die Sitzungs-ID wird von Hybris in einem `JSESSIONID`-Cookie zurückgegeben, das bei nachfolgenden Anfragen an Hybris gesendet werden muss. Um zu vermeiden, dass die Sitzungs-ID im Repository gespeichert wird, ist sie als Code in ein anderes Cookie eingebettet, das im Browser der Kundin bzw. des Kunden gespeichert wird. Die folgenden Schritte werden ausgeführt:

* Bei der ersten Anfrage wird kein Cookie für die Anfrage der Käuferin bzw. des Käufers gesetzt. Daher wird eine Anfrage an die hybris-Instanz gesendet, eine Sitzung zu erstellen.

* Die Sitzungs-Cookies werden aus der Antwort extrahiert, als Code in ein neues Cookie (z. B. `hybris-session-rest`) eingebettet und in der Antwort an den Erstkäufer festgelegt. Die Kodierung in einem neuen Cookie ist erforderlich, da das ursprüngliche Cookie nur für einen bestimmten Pfad gültig ist und andernfalls bei nachfolgenden Anfragen nicht vom Browser zurückgesendet wird. Die Pfadinformationen müssen zum Wert des Cookies hinzugefügt werden.

* Bei nachfolgenden Anfragen wird das Cookie aus den `hybris-session-<*xxx*>`-Cookies dekodiert und auf den HTTP-Client festgelegt, der zum Anfordern der Daten von Hybris verwendet wird.

>[!NOTE]
>
>Eine neue, anonyme Sitzung wird erstellt, wenn die ursprüngliche Sitzung nicht mehr gültig ist.

#### CommerceSession {#commercesession}

* Diese Sitzung „besitzt“ den **Warenkorb**.

   * Sie führt Hinzufügen/Entfernen-Aktionen aus.

   * Führt die verschiedenen Berechnungen für den Warenkorb durch;

     `commerceSession.getProductPrice(Product product)`

* Sie steuert den *Speicherort* für die **Auftragsdaten**.

  `CommerceSession.getUserContext()`

* Sie steuert die Verbindung für die **Zahlungsverarbeitung**.

* Sie steuert die Verbindung für die **Erfüllung**.

### Synchronisieren und Veröffentlichen von Produkten {#product-synchronization-and-publishing}

In hybris gepflegte Produktdaten müssen in AEM verfügbar sein. Dafür wurde folgender Mechanismus implementiert:

* Die anfänglich geladenen IDs werden von Hybris als Feed bereitgestellt. Dieser Feed kann aktualisiert werden.
* hybris stellt Aktualisierungsinformationen über einen Feed bereit (den AEM abruft).
* Beim Verwenden von Produktdaten sendet AEM Anfragen für die aktuellen Daten zurück an hybris (bedingte GET-Anfrage mit dem Datum der letzten Änderung).
* In hybris können Feed-Inhalte deklarativ angegeben werden.
* Die Zuordnung der Feed-Struktur zum AEM-Inhaltsmodell erfolgt auf AEM-Seite im Feed-Adapter.

![chlimage_1-12](/help/sites-developing/assets/chlimage_1-12a.png)

* Das Import-Tool (b) wird für die anfängliche Einrichtung der Seitenstruktur in AEM für Kataloge verwendet.
* Katalogänderungen in hybris werden AEM über einen Feed mitgeteilt und dann in AEM wie folgt übernommen (b):

   * Produkt im Hinblick auf die Katalogversion hinzugefügt/gelöscht/geändert.

   * Produkt genehmigt.

* Die hybris-Erweiterung stellt ein Abruf-Import-Tool („hybris-Schema“) bereit, das für das Importieren von Änderungen in AEM in bestimmten Abständen konfiguriert werden kann (z. B. alle 24 Stunden, wobei das Intervall in Sekunden angegeben wird):

  ```JavaScript
      http://localhost:4502/content/geometrixx-outdoors/en_US/jcr:content.json
       {
       * "jcr:mixinTypes": ["cq:PollConfig"],
       * "enabled": true,
       * "source": "hybris:outdoors",
       * "jcr:primaryType": "cq:PageContent",
       * "interval": 86400
       }
  ```

* Die Katalogkonfiguration in AEM erkennt Kataloge der Versionen **Gestaffelt** und **Online**.

* Für das Synchronisieren von Produkten zwischen Katalogversionen muss die entsprechende AEM-Seite aktiviert bzw. deaktiviert werden (a, c):

   * Wenn Sie ein Produkt zur **Online**-Version eines Katalogs hinzufügen möchten, müssen Sie die Produktseite aktivieren.

   * Wenn Sie ein Produkt entfernen möchten, müssen Sie die Seite deaktivieren.

* Das Aktivieren einer Seite in AEM (c) erfordert eine Prüfung (b) und ist nur möglich, wenn:

   * sich das Produkt in der **Online**-Version eines Katalogs für Produktseiten befindet.

   * die Produkte, auf die verwiesen wird, in der **Online**-Version eines Katalogs für andere Seiten (z. B. Kampagnenseiten) verfügbar sind.

* Aktivierte Produktseiten müssen auf die **Online**-Version (d) der Produktdaten zugreifen.

* Die AEM-Veröffentlichungsinstanz benötigt Zugriff auf hybris, um Produkt- und personalisierte Daten abzurufen (d).

### Architektur {#architecture}

#### Architektur von Produkt und Varianten {#architecture-of-product-and-variants}

Ein einzelnes Produkt kann mehrere Variationen aufweisen, z. B. kann es je nach Farbe und/oder Größe variieren. Ein Produkt muss definieren, welche Eigenschaften die Variation bestimmen. Bei Adobe heißt dies *Variantenachsen*.

Es sind jedoch nicht alle Eigenschaften Variantenachsen. Varianten können sich auch auf andere Eigenschaften auswirken, z. B. kann der Preis von der Größe abhängen. Diese Eigenschaften können nicht von den Käuferinnen und Käufern ausgewählt werden und werden daher nicht als Variantenachsen betrachtet.

Jedes Produkt bzw. jede Variante steht für eine Ressource und ist daher im Verhältnis 1:1 einem Repository-Knoten zugeordnet. Eine Folge ist, dass ein bestimmtes Produkt und/oder eine bestimmte Variante durch ihren Pfad eindeutig identifiziert werden kann.

Die Produkt-/Variantenressource enthält nicht immer die tatsächlichen Produktdaten. Es kann sich um eine Darstellung von Daten handeln, die in einem anderen System (z. B. Hybris) gespeichert sind. Beispielsweise werden Produktbeschreibungen und Preise nicht in AEM gespeichert, sondern werden in Echtzeit aus der E-Commerce-Engine abgerufen.

Jede Produktressource kann durch eine `Product API` dargestellt werden. Die meisten Aufrufe in der Produkt-API beziehen sich auf spezifische Varianten (obwohl Varianten gemeinsame Werte von einem Vorgänger erben können). Bei manchen Aufrufen wird jedoch ein Variantensatz (`getVariantAxes()`, `getVariants()` usw.) aufgelistet.

>[!NOTE]
>
>Eine Variantenachse wird letztendlich von dem bestimmt, was der Aufruf `Product.getVariantAxes()` zurückgibt:
>* hybris definiert diese für die hybris-Implementierung.
>
>Zwar können Produkte (im Allgemeinen) viele Variantenachsen haben, vorkonfigurierte Produktkomponenten jedoch nur zwei:
>
>1. `size`
>
>1. und eine zusätzliche Variante
>
>Diese zusätzliche Variante wird von der `variationAxis`-Eigenschaft des Produktverweises (in der Regel `color` für Geometrixx Outdoors) ausgewählt.

#### Produktverweise und Produktdaten {#product-references-and-product-data}

Im Allgemeinen befinden sich Produktdaten unter `/etc` und Produktverweise unter `/content`.

Die Knoten für die Produktvarianten und Produktdaten müssen 1:1 zugeordnet sein.

Produktverweise müssen außerdem einen Knoten für jede präsentierte Variante haben, es müssen jedoch nicht alle Varianten präsentiert werden. Wenn ein Produkt beispielsweise die Varianten S, M und L hat, können die Produktdaten wie folgt aussehen:

```shell
etc
|──commerce
|  |──products
|     |──shirt
|       |──shirt-s
|       |──shirt-m
|       |──shirt-l
```

Im Katalog „big-and-tall“ sind möglicherweise nur diese Daten enthalten:

```shell
content
|──big-and-tall
|  |──shirt
|     |──shirt-l
```

Es ist nicht zwingend erforderlich, Produktdaten zu verwenden. Sie können alle Produktdaten unter den Verweisen im Katalog speichern. Allerdings müssen Sie dann alle Produktdaten duplizieren, wenn Sie mehrere Kataloge verwenden möchten.

**API**

#### com.adobe.cq.commerce.api.Product interface {#com-adobe-cq-commerce-api-product-interface}

```java
public interface Product extends Adaptable {

    public String getPath();            // path to specific variation
    public String getPagePath();        // path to presentation page for all variations
    public String getSKU();             // unique ID of specific variation

    public String getTitle();           // shortcut to getProperty(TITLE)
    public String getDescription();     // shortcut to getProperty(DESCRIPTION)
    public String getImageUrl();        // shortcut to getProperty(IMAGE_URL)
    public String getThumbnailUrl();    // shortcut to getProperty(THUMBNAIL_URL)

    public <T> T getProperty(String name, Class<T> type);

    public Iterator<String> getVariantAxes();
    public boolean axisIsVariant(String axis);
    public Iterator<Product> getVariants(VariantFilter filter) throws CommerceException;
}
```

#### com.adobe.cq.commerce.api.VariantFilter  {#com-adobe-cq-commerce-api-variantfilter}

```java
/**
 * Interface for filtering variants and AxisFilter provided as common implementation
 *
 * The <code>VariantFilter</code> is used to filter variants,
 * for example, when using {@link Product#getVariants(VariantFilter filter)}.
 */
public interface VariantFilter {
    public boolean includes(Product product);
}

/**
 * A {@link VariantFilter} for filtering variants by the given
 * axis and value. The following example returns a list of
 * variant products that have a value of <i>blue</i> on the
 * <i>color</i> axis.
 *
 * <p>
 * <code>product.getVariants(new AxisFilter("color", "blue"));</code>
 */
public class AxisFilter implements VariantFilter {

    private String axis;
    private String value;

    public AxisFilter(String axis, String value) {
        this.axis = axis;
        this.value = value;
    }

    /**
     * {@inheritDoc}
     */
    public boolean includes(Product product) {
        ValueMap values = product.adaptTo(ValueMap.class);

        if(values != null) {
            String v = values.get(axis, String.class);

            return v != null && v == value;
        }

        return false;
    }
}
```

* **Allgemeiner Speichermechanismus**

   * Produktknoten weisen die Eigenschaft „`nt:unstructured`“ auf.

   * Ein Produktknoten kann Folgendes sein:

      * Eine Referenz, wobei die Produktdaten an anderer Stelle gespeichert werden:

         * Produktverweise enthalten eine `productData`-Eigenschaft, die auf die Produktdaten verweist (in der Regel unter `/etc/commerce/products`).

         * Die Produktdaten sind hierarchisch. Produktattribute werden von den Vorgängern eines Produktdatenknotens übernommen.

         * Produktverweise können auch lokale Eigenschaften enthalten, die die in ihren Produktdaten angegebenen überschreiben.

      * Ein Produkt selbst:

         * Ohne eine `productData`-Eigenschaft.

         * Ein Produktknoten, der alle Eigenschaften lokal enthält (und keine productData-Eigenschaft enthält), erbt Produktattribute direkt von seinen eigenen Vorgängern.

* **AEM-generische Produktstruktur**

   * Jede Variante muss über einen eigenen Blattknoten verfügen.

   * Die Produktoberfläche stellt sowohl Produkte als auch Varianten dar, aber der zugehörige Repository-Knoten gibt an, um was es sich handelt.

   * Der Produktknoten beschreibt die Produktattribute und Variantenachsen.

#### Beispiel {#example-1}

```shell
+ banyan_shirt
    - cq:commerceType = product
    - cq:productAttributes = [jcr:title, jcr:description, size, price, color]
    - cq:productVariantAxes = [color, size]
    - jcr:title = Banyan Shirt
    - jcr:description = Flowery, all-cotton shirt.
    - price = 14.00
    + banyan_shirt_s
        - cq:commerceType = variant
        - size = S
        + banyan_shirt_s_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_s_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_m
        - cq:commerceType = variant
        - size = M
        + banyan_shirt_m_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_m_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_l
        - cq:commerceType = variant
        - size = L
        + banyan_shirt_l_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_l_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_xl
        - cq:commerceType = variant
        - size = XL
        - price = 18.00
```

#### Architektur des Warenkorbs {#architecture-of-the-shopping-cart}

**Komponenten**

* Der Warenkorb wird von `CommerceSession:` gesteuert:

   * Die `CommerceSession` führt das Hinzufügen, Entfernen usw. durch.
   * `CommerceSession` nimmt auch die diversen Berechnungen des Warenkorbs vor. ``

* Obwohl dies nicht direkt mit dem Warenkorb zusammenhängt, muss `CommerceSession` auch Katalogpreisinformationen angeben (da sie die Preise steuert).

   * Für die Preisgestaltung können mehrere Modifikatoren gelten:

      * Mengenrabatte.
      * Verschiedene Währungen.
      * Mehrwertsteuerpflichtig und mehrwertsteuerfrei.

   * Die Modifikatoren sind offen und haben die folgende Schnittstelle:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`

**Speicher**

* Speicher

   * Bei hybris steuert der hybris-Server den Warenkorb.
   * Bei AEM werden Warenkörbe im Allgemeinen in [ClientContext](/help/sites-administering/client-context.md) gespeichert.

**Personalisierung**

* Die Personalisierung erfolgt immer über den [ClientContext](/help/sites-administering/client-context.md).
* In allen Fällen wird eine ClientContext-Version (`/version/`) des Warenkorbs erstellt:

   * Produkte sollten mithilfe der `CommerceSession.addCartEntry()`-Methode hinzugefügt werden.

* Nachstehend sehen Sie ein Beispiel für Warenkorbinformationen in einem ClientContext-Warenkorb:

![chlimage_1-13](/help/sites-developing/assets/chlimage_1-13a.png)

#### Architektur des Checkout {#architecture-of-checkout}

**Warenkorb- und Bestelldaten**

`CommerceSession` steuert die drei folgenden Elemente:

1. Inhalt des Warenkorbs
1. Preisgestaltung
1. Bestelldetails

1. **Inhalt des Warenkorbs**

   Das Inhaltsschema des Warenkorbs wird durch die API festgelegt:

   ```java
   public void addCartEntry(Product product, int quantity);
   public void modifyCartEntry(int entryNumber, int quantity);
   public void deleteCartEntry(int entryNumber);
   ```

1. **Preisgestaltung**

   Das Preisschema wird ebenfalls von der API festgelegt:

   ```java
   public String getCartPreTaxPrice();
   public String getCartTax();
   public String getCartTotalPrice();
   public String getOrderShipping();
   public String getOrderTotalTax();
   public String getOrderTotalPrice();
   ```

1. **Auftragsdetails**

   Die Auftragsdetails werden jedoch *nicht* von der API festgelegt:

   ```java
   public void updateOrderDetails(Map<String, String> orderDetails);
   public Map<String, String> getOrderDetails();
   public void submitOrder();
   ```

**Versandkostenberechnungen**

* Bestellformulare müssen oft mehrere Versandoptionen (und Preise) enthalten.
* Die Preise können auf Artikeln und Details der Bestellung basieren, wie Gewicht und/oder Lieferadresse.
* `CommerceSession` hat Zugriff auf alle Abhängigkeiten und kann daher ähnlich wie Produktpreise behandelt werden:

   * `CommerceSession` steuert die Versandkosten.
   * Kann Versanddetails über `updateOrder(Map<String, Object> delta)` abrufen oder aktualisieren.

>[!NOTE]
>
>Sie können eine Versandauswahl implementieren, z. B.:
>
>`yourProject/commerce/components/shippingpicker`:
>
>* Dabei kann es sich im Wesentlichen um eine Kopie von `foundation/components/form/radio` handeln, jedoch mit Rückrufen an `CommerceSession` für folgende Zwecke:
>
>* Überprüfen, ob die Methode verfügbar ist
>* Hinzufügen von Preisinformationen
>* Möglichkeit für Erstkäufer, die Auftragsseite in AEM (einschließlich Obermenge der Versandmethoden und Beschreibungstexten) zu aktualisieren und weiterhin die Anzeige relevanter `CommerceSession`-Informationen zu steuern.

**Zahlungsverarbeitung**

* `CommerceSession` steuert auch die Verbindung für die Zahlungsverarbeitung.

* Implementierungsprogramme sollten spezifische Aufrufe (an den ausgewählten Zahlungsverarbeitungs-Service) zur `CommerceSession`-Implementierung hinzufügen.

**Auftragserfüllung**

* `CommerceSession` steuert auch die Verbindung für die Auftragserfüllung.
* Implementierungsprogramme müssen spezifische Aufrufe (an den ausgewählten Zahlungsverarbeitungs-Service) zur `CommerceSession`-Implementierung hinzufügen.

### Suchdefinition {#search-definition}

Gemäß dem standardmäßigen Dienst-API-Modell stellt das eCommerce-Projekt einen Satz suchbezogener APIs bereit, die von einzelnen Commerce-Engines implementiert werden können.

>[!NOTE]
>
>Derzeit wird die vorkonfigurierte Such-API nur von der Hybris-Engine implementiert.
>
>Die Such-API ist jedoch generisch und kann von jedem CommerceService einzeln implementiert werden.

Das eCommerce-Projekt enthält eine Standardsuchkomponente in:

`/libs/commerce/components/search`

![chlimage_1-14](/help/sites-developing/assets/chlimage_1-14a.png)

Hierbei wird die Such-API verwendet, um die ausgewählte Commerce-Engine abzufragen (siehe [Auswahl der E-Commerce-Engine](#ecommerce-engine-selection)):

#### Such-API {#search-api}

Es gibt mehrere generische bzw. Hilfsklassen, die vom Kernprojekt bereitgestellt werden:

1. `CommerceQuery`

   Beschreibung einer Suchabfrage (enthält Informationen über den Abfragetext, die aktuelle Seite, die Seitengröße, die Sortierung und die ausgewählten Facetten). Alle eCommerce-Dienste, die die Such-API implementieren, erhalten Instanzen dieser Klasse, um die Suche durchführen zu können. Es kann eine `CommerceQuery`-Instanz anhand eines Anfrageobjekts (`HttpServletRequest`) erstellt werden.

1. `FacetParamHelper`

   Eine Hilfsprogramm-Klasse, die eine statische Methode (`toParams`) zum Erzeugen von `GET`-Parameterzeichenfolgen aus einer Facettenliste und einen umgeschalteten Wert bereitstellt. Dies ist in der Benutzeroberfläche nützlich, wo Sie einen Hyperlink für jeden Wert jeder Facette anzeigen müssen, sodass der entsprechende Wert umgeschaltet wird, wenn die Benutzenden auf den Hyperlink klicken. Das heißt, wenn er ausgewählt wurde, wird er aus der Abfrage entfernt, andernfalls wird er hinzugefügt. Damit wird die gesamte Logik der Handhabung von Facetten mit mehreren oder einzelnen Werten, das Überschreiben von Werten usw. übernommen.

Einstiegspunkt für die Such-API ist die `CommerceService#search`-Methode, die ein `CommerceResult`-Objekt zurückgibt. Weitere Informationen zu diesem Thema finden Sie in der [API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation).

### Benutzerintegration {#user-integration}

AEM kann mit diversen E-Commerce-Systemen integriert werden. Dazu ist eine Strategie zum Synchronisieren von Käuferinnen und Käufern zwischen unterschiedlichen Systemen erforderlich, damit AEM-spezifischer Code nur an AEM weitergegeben wird und umgekehrt:

* Authentifizierung

  Es wird davon ausgegangen, dass AEM das *einzige* Web-Frontend ist und daher *alle* Authentifizierungen verarbeitet.

* Konten in Hybris

  AEM erstellt für jeden Erstkäufer ein entsprechendes (sekundäres) Konto in Hybris. Der Benutzername dieses Kontos ist mit dem AEM-Benutzernamen identisch. Ein kryptografisches Zufallskennwort wird automatisch in AEM erstellt und (verschlüsselt) gespeichert.

#### Bereits vorhandene Benutzende {#pre-existing-users}

Vor einer vorhandenen hybris-Implementierung kann ein AEM-Font-End platziert werden. Außerdem kann eine hybris-Engine zu einer vorhandenen AEM-Installation hinzugefügt werden. Dazu müssen die Systeme bereits vorhandene Benutzende in beiden Systemen reibungslos verarbeiten können:

* AEM > hybris

   * Beim Anmelden bei hybris (falls keine AEM-Benutzenden vorhanden sind):

      * Erstellen Sie eine hybris-Benutzerin oder einen hybris-Benutzer mit einem kryptografischen Zufallskennwort.
      * Speichern Sie den Hybris-Benutzernamen im Benutzerverzeichnis des AEM-Benutzers.

   * Siehe: `com.adobe.cq.commerce.hybris.impl.HybrisSessionImpl#login()`

* hybris > AEM

   * Beim Anmelden bei AEM (falls das System die Person erkennt):

      * Versuchen Sie, sich mit dem angegebenen Benutzernamen/Kennwort bei Hybris anzumelden.
      * Falls erfolgreich, erstellen Sie eine neue Benutzerin oder einen neuen Benutzer in AEM mit demselben Kennwort (AEM-spezifisches Salt wird zu AEM-spezifischem Hash).

   * Der obige Algorithmus wird in einem `AuthenticationInfoPostProcessor` von Sling implementiert.

      * Siehe: `com.adobe.cq.commerce.hybris.impl.user.LazyUserImporter.java`

### Anpassen des Import-Prozesses {#customizing-the-import-process}

Um vorhandene Funktionen nutzen zu können, gilt Folgendes für den benutzerdefinierten Import-Handler:

* Er muss die `ImportHandler`-Schnittstelle implementieren.

* Er kann den `DefaultImportHandler` erweitern.

```java
/**
 * Services implementing the <code>ImportHandler</code> interface are
 * called by the {@link HybrisImporter} to create actual commerce entities
 * such as products.
 */
public interface ImportHandler {

  /**
  * Not used.
  */
  public void createTaxonomie(ImporterContext ctx);

  /**
  * Creates a catalog with the given name.
  * @param ctx   The importer context
  * @param name  The catalog's name
  * @return Path of created catalog
  */
  public String createCatalog(ImporterContext ctx, String name) throws Exception;

  /**
  * Creates a product from the given values.
  * @param ctx                The importer context
  * @param values             The product's properties
  * @param parentCategoryPath The containing category's path
  * @return Path of created product
  */
  public String createProduct(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;

  /**
  * Creates a variant product from the given values.
  * @param ctx             The importer context
  * @param values          The product's properties
  * @param baseProductPath The base product's path
  * @return Path of created product
  */
  public String createVariantProduct(ImporterContext ctx, ValueMap values, String baseProductPath) throws Exception;

  /**
  * Creates an asset for a product. This is usually a product
  * image.
  * @param ctx             The importer context
  * @param values          The product's properties
  * @param baseProductPath The product's path
  * @return Path of created asset
  */
  public String createAsset(ImporterContext ctx, ValueMap values, String productPath) throws Exception;

  /**
  * Creates a category from the given values.
  * @param ctx           The importer context
  * @param values        The category's properties
  * @param parentPath    Path of parent category or base path of import if there is a root category
  * @return Path of created category
  */
  public String createCategory(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;
}
```

Damit der benutzerdefinierte Handler vom Import-Tool erkannt wird, muss die Eigenschaft `service.ranking` einen Wert über 0 aufweisen, Beispiel:

```java
@Component
@Service
@Property(name = "service.ranking", value = 100)
public class MyImportHandler extends DefaultImportHandler
{
...
}
```
