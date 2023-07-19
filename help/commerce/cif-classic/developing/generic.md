---
title: Entwicklung (generisch)
seo-title: Developing (generic)
description: Das Integrations-Framework umfasst eine Integrationsschicht mit einer API, die es Ihnen ermöglicht, AEM Komponenten für eCommerce-Funktionen zu erstellen
seo-description: The integration framework includes an integration layer with an API, allowing you to build AEM components for eCommerce capabilities
uuid: 393bb28a-9744-44f4-9796-09228fcd466f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
exl-id: 1138a548-d112-4446-b0e1-b7a9ea7c7604
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1863'
ht-degree: 55%

---

# Entwicklung (generisch){#developing-generic}

>[!NOTE]
>
>[API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) ist ebenfalls verfügbar.

Das Integrations-Framework enthält eine Integrationsebene mit einer API. Dies ermöglicht es Ihnen, AEM-Komponenten für eCommerce-Funktionen (unabhängig von einer bestimmten eCommerce-Engine) zu erstellen. Außerdem können Sie die interne CRX-Datenbank verwenden oder ein eCommerce-System einbinden und Produktdaten in AEM abrufen.

Eine Reihe vorkonfigurierter AEM-Komponenten wird zur Verwendung der Integrationsebene bereitgestellt. Derzeit sind dies:

* Eine Komponente „Produktanzeige“
* Warenkorb
* Promotions und Gutscheine
* Katalog- und Abschnitts-Blueprints
* Checkout
* Suchen

Für die Suche wird ein Integrations-Hook zur Verfügung gestellt, mit dem Sie die AEM-Suche, eine Suche von Drittanbietern oder eine Kombination daraus verwenden können.

## Auswahl der eCommerce-Engine {#ecommerce-engine-selection}

Das eCommerce-Framework kann mit jeder eCommerce-Lösung verwendet werden, die verwendete Engine muss von AEM identifiziert werden - auch bei Verwendung der generischen AEM-Engine:

* eCommerce-Engines sind OSGi-Dienste, die die `CommerceService`-Schnittstelle unterstützen.

   * Engines können anhand einer `commerceProvider`-Service-Eigenschaft identifiziert werden.

* AEM unterstützt `Resource.adaptTo()` für `CommerceService` und `Product`.

   * Die `adaptTo`-Implementierung sucht nach einer `cq:commerceProvider`-Eigenschaft in der Hierarchie der Ressource:

      * Wenn der Wert gefunden wird, wird er zum Filtern der Commerce-Service-Suche verwendet.
      * Wenn nicht gefunden, wird der Commerce-Dienst mit dem höchsten Rang verwendet.

   * Ein `cq:Commerce`-Mixin wird verwendet, um `cq:commerceProvider` zu stark typisierten Ressourcen hinzuzufügen.

* Die `cq:commerceProvider`-Eigenschaft wird auch als Verweis auf die geeignete Commerce-Factory-Definition verwendet.

   * Zum Beispiel korreliert eine Eigenschaft `cq:commerceProvider` mit dem Wert mit der OSGi-Konfiguration für **Day CQ Commerce Factory für Geometrixx-Outdoors** (`com.adobe.cq.commerce.hybris.impl.GeoCommerceServiceFactory`) - wobei der Parameter `commerceProvider` auch den Wert `geometrixx`geometrixx hat.
   * Hier können weitere Eigenschaften konfiguriert werden (falls zutreffend und verfügbar).

In einer Standard-AEM-Installation wird eine spezifische Implementierung benötigt, zum Beispiel:

|  |  |
|---|---|
| `cq:commerceProvider = geometrixx` | Geometrixx-Beispiel; dies umfasst minimale Erweiterungen der generischen API |

### Beispiel {#example}

```shell
/etc/commerce/products/geometrixx-outdoors
+ cq:commerceProvider = geometrixx
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
>Mithilfe der CRXDE Lite können Sie sehen, wie dies in der Produktkomponente für die AEM allgemeine Implementierung gehandhabt wird:
>
>`/apps/geometrixx-outdoors/components/product`

### Session-Handling {#session-handling}

Eine Sitzung zum Speichern von Informationen über den Warenkorb des Kunden.

Die **CommerceSession**:

* Besitzt den **Warenkorb**

   * Sie führt Hinzufügen/Entfernen-Aktionen aus.
   * Sie führt diverse Berechnungen im Hinblick auf den Warenkorb aus,

     `commerceSession.getProductPriceInfo(Product product, Predicate filter)`

* Besitzt Persistenz der **Bestelldaten**:

  `CommerceSession.getUserContext()`

* Kann Versanddetails über `updateOrder(Map<String, Object> delta)` abrufen oder aktualisieren.
* Eigentümer des **payment** Verarbeitungsverbindung
* Sie steuert ebenfalls die Verbindung für die **Auftragserfüllung**.

### Architektur {#architecture}

#### Architektur von Produkt und Varianten {#architecture-of-product-and-variants}

Ein einzelnes Produkt kann mehrere Varianten aufweisen. Beispielsweise kann es je nach Farbe und/oder Größe variieren. Ein Produkt muss definieren, welche Eigenschaften die Variante beeinflussen. wir diese *Variantenachsen*.

Es sind jedoch nicht alle Eigenschaften Variantenachsen. Varianten können sich auch auf andere Eigenschaften auswirken. Beispielsweise kann der Preis von der Größe abhängen. Diese Eigenschaften können nicht vom Käufer ausgewählt werden und werden daher nicht als Variantenachsen betrachtet.

Jedes Produkt bzw. jede Variante steht für eine Ressource und ist daher im Verhältnis 1:1 einem Repository-Knoten zugeordnet. Eine Folge ist, dass ein bestimmtes Produkt und/oder eine bestimmte Variante durch ihren Pfad eindeutig identifiziert werden kann.

Jede Produktressource kann durch eine `Product API` dargestellt werden. Die meisten Aufrufe in einer Produkt-API beziehen sich auf spezifische Varianten (obwohl Varianten gemeinsame Werte von einem Vorgänger erben können). Bei manchen Aufrufen wird jedoch ein Variantensatz (`getVariantAxes()`, `getVariants()` usw.) aufgelistet.

>[!NOTE]
>
>Eine Variantenachse wird letztendlich von dem bestimmt, was der `Product.getVariantAxes()`-Aufruf zurückgibt:
>
>* für die generische Implementierung liest AEM es aus einer Eigenschaft in den Produktdaten ( `cq:productVariantAxes`)
>
>Zwar können Produkte (im Allgemeinen) viele Variantenachsen haben, vorkonfigurierte Produktkomponenten jedoch nur zwei:
>
>1. `size`
>1. und eine zusätzliche Variante
>
>   Diese zusätzliche Variante wird von der `variationAxis`-Eigenschaft des Produktverweises (in der Regel `color` für Geometrixx Outdoors) ausgewählt.

#### Produktverweise und PIM-Daten {#product-references-and-pim-data}

Allgemein:

* befinden sich PIM-Daten unter `/etc`

* und Produktverweise unter `/content`.

Die Knoten für die Produktvarianten und Produktdaten müssen 1:1 zugeordnet sein.

Produktverweise müssen außerdem einen Knoten für jede präsentierte Variante haben, es müssen jedoch nicht alle Varianten präsentiert werden. Wenn ein Produkt beispielsweise die Varianten S, M und L hat, können die Produktdaten wie folgt aussehen:

```shell
etc
  commerce
    products
      shirt
        shirt-s
        shirt-m
        shirt-l
```

Im Katalog „big-and-tall“ sind möglicherweise nur diese Daten enthalten:

```shell
content
  big-and-tall
    shirt
      shirt-l
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

   * Produktknoten sind nt:unstructured.
   * Ein Produktknoten kann entweder:

      * Referenz mit den an anderer Stelle gespeicherten Produktdaten:

         * Produktverweise enthalten eine `productData`-Eigenschaft, die auf die Produktdaten verweist (in der Regel unter `/etc/commerce/products`).
         * Die Produktdaten sind hierarchisch; Produktattribute werden von den Vorgängern eines Produktdatenknotens vererbt.
         * Produktverweise können auch lokale Eigenschaften enthalten, die die in ihren Produktdaten angegebenen überschreiben.

      * Ein Produkt selbst:

         * Ohne eine `productData`-Eigenschaft.
         * Ein Produktknoten, der alle Eigenschaften lokal enthält (und keine productData -Eigenschaft enthält), erbt Produktattribute direkt von seinen eigenen Vorgängern.

* **AEM-generische Produktstruktur**

   * Jede Variante muss über einen eigenen Blattknoten verfügen.
   * Die Produktoberfläche stellt sowohl Produkte als auch Varianten dar, aber der zugehörige Repository-Knoten ist spezifisch für den es ist.
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

* Der Warenkorb wird von der `CommerceSession:` gesteuert:

   * Die `CommerceSession` führt Hinzufügen, Entfernen usw. durch.
   * Die `CommerceSession` nimmt auch die diversen Berechnungen des Warenkorbs vor.
   * Die `CommerceSession` wendet auch Gutscheine und Aktionen an, die auf den Warenkorb ausgeführt werden.

* Obwohl dies nicht direkt mit dem Warenkorb zusammenhängt, muss die `CommerceSession` auch Kataloginformationen angeben (da sie die Preise steuert).

   * Preise können mehrere Modifikatoren aufweisen:

      * Mengenrabatte.
      * Verschiedene Währungen.
      * Mehrwertsteuerpflichtig und mehrwertsteuerfrei.

   * Die Modifikatoren sind vollständig offen mit der folgenden Benutzeroberfläche:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`

**Speicher**

* Speicher

   * Im AEM generischen Fall werden Warenkörbe im [ClientContext](/help/sites-administering/client-context.md)

**Personalisierung**

* Die Personalisierung sollte immer durch das [ClientContext](/help/sites-administering/client-context.md).
* In allen Fällen wird eine ClientContext-Version (`/version/`) des Warenkorbs erstellt:

   * Produkte sollten mithilfe der `CommerceSession.addCartEntry()`-Methode hinzugefügt werden.

* Nachstehend sehen Sie ein Beispiel für Warenkorbinformationen in einem ClientContext-Warenkorb:

![chlimage_1-33](/help/sites-developing/assets/chlimage_1-33a.png)

#### Architektur des Auscheckens {#architecture-of-checkout}

**Warenkorb- und Bestelldaten**

Die `CommerceSession` steuert die drei folgenden Elemente:

1. **Inhalt des Warenkorbs**

   Das Inhaltsschema des Warenkorbs wird durch die API festgelegt:

   ```java
       public void addCartEntry(Product product, int quantity);
       public void modifyCartEntry(int entryNumber, int quantity);
       public void deleteCartEntry(int entryNumber);
   ```

1. **Preise**

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

**Versandberechnungen**

* Bestellformulare müssen häufig mehrere Versandoptionen (und Preise) enthalten.
* Die Preise können auf Artikeln und Details der Bestellung basieren, wie Gewicht und/oder Lieferadresse.
* `CommerceSession` hat Zugriff auf alle Abhängigkeiten und kann daher ähnlich wie Produktpreise behandelt werden:

   * Die `CommerceSession` steuert die Versandkosten.
   * Verwenden Sie `updateOrder(Map<String, Object> delta)`, um Lieferdetails abzurufen / zu aktualisieren.

### Suchdefinition {#search-definition}

Gemäß dem Standard-Service-API-Modell stellt das eCommerce-Projekt eine Reihe suchbezogener APIs bereit, die von einzelnen Commerce-Engines implementiert werden können.

>[!NOTE]
>
>Derzeit implementiert nur die hybris-Engine die Such-API standardmäßig.
>
>Die Such-API ist jedoch generisch und kann von jedem CommerceService einzeln implementiert werden.
>
>Obwohl die standardmäßig bereitgestellte generische Implementierung diese API nicht implementiert, können Sie sie erweitern und die Suchfunktion hinzufügen.

Das eCommerce-Projekt enthält eine standardmäßige Suchkomponente, die sich unter:

`/libs/commerce/components/search`

![chlimage_1-34](/help/sites-developing/assets/chlimage_1-34a.png)

Dadurch wird die Such-API zur Abfrage der ausgewählten Commerce-Engine verwendet (siehe [Auswahl der eCommerce-Engine](#ecommerce-engine-selection)):

#### Such-API {#search-api}

Es gibt mehrere generische / Helper-Klassen, die vom Kernprojekt bereitgestellt werden:

1. `CommerceQuery`

   Wird zum Beschreiben einer Suchabfrage verwendet (enthält Informationen zu Abfragetext, aktueller Seite, Seitengröße, Sortierung und ausgewählten Facetten). Alle eCommerce-Services, die die Such-API implementieren, erhalten Instanzen dieser Klasse, um die Suche durchführen zu können. Es kann eine `CommerceQuery`-Instanz anhand eines Anfrageobjekts (`HttpServletRequest`) erstellt werden.

1. `FacetParamHelper`

   Eine Hilfsprogramm-Klasse, die eine statische Methode (`toParams`) zum Erzeugen von `GET`-Parameterzeichenfolgen aus einer Facettenliste und einen umgeschalteten Wert bereitstellt. Dies ist auf der UI-Seite nützlich, auf der Sie für jeden Wert einer Facette einen Hyperlink anzeigen müssen. Wenn der Benutzer auf den Hyperlink klickt, wird der entsprechende Wert umgeschaltet (d. h. wenn er ausgewählt wurde, wird er aus der Abfrage entfernt und andernfalls hinzugefügt). Dadurch wird die gesamte Logik des Umgangs mit Facetten mit mehreren/einzelnen Werten, des Überschreibens von Werten usw. berücksichtigt.

Einstiegspunkt für die Such-API ist die `CommerceService#search`-Methode, die ein `CommerceResult`-Objekt zurückgibt. Weitere Informationen zu diesem Thema finden Sie in der API-Dokumentation.

### Entwickeln von Promotions und Gutscheinen {#developing-promotions-and-vouchers}

* Gutscheine:

   * Ein Gutschein ist eine seitenbasierte Komponente, die mit der Website-Konsole erstellt/bearbeitet und unter folgendem Ordner gespeichert wird:

     `/content/campaigns`

   * Gutscheine:

      * Ein Gutscheincode (der vom Käufer in den Warenkorb eingegeben wird).
      * Eine Gutscheinbeschriftung (die angezeigt wird, nachdem der Käufer sie in den Warenkorb eingegeben hat).
      * Ein Promotionpfad (der die Aktion definiert, die der Gutschein anwendet).

   * Gutscheine verfügen nicht über eigene Ein- und Ausschaltzeiten, sondern über die ihrer übergeordneten Kampagnen.
   * Externe Commerce-Engines können auch Gutscheine bereitstellen. diese erfordern mindestens:

      * Ein Gutscheincode
      * eine `isValid()`-Methode

   * Die **Gutschein**-Komponente (`/libs/commerce/components/voucher`) bietet:

      * einen Renderer für die Gutscheinadministration; er zeigt alle Gutscheine an, die sich aktuell im Warenkorb befinden
      * Die Bearbeitungsdialogfelder (Formular) zum Verwalten (Hinzufügen/Entfernen) der Gutscheine.
      * Die zum Hinzufügen/Entfernen von Gutscheinen zum/vom Warenkorb erforderlichen Aktionen.

* Promotions:

   * Eine Promotion ist eine seitenbasierte Komponente, die mit der Website-Konsole erstellt/bearbeitet und unter folgendem Ordner gespeichert wird:

     `/content/campaigns`

   * Angebote für Werbeaktionen:

      * Eine Priorität
      * Ein Promotion-Handler-Pfad

   * Sie können Promotions mit einer Kampagne verknüpfen, um deren Aktivierungs-/Ausschaltzeiten zu definieren.
   * Sie können Promotions mit einem Erlebnis verbinden, um deren Segmente zu definieren.
   * Promotions, die nicht mit einem Erlebnis verbunden sind, werden nicht allein ausgelöst, können aber dennoch von einem Gutschein ausgelöst werden.
   * Die Promotion-Komponente (`/libs/commerce/components/promotion`) umfasst:

      * Renderer und Dialogfelder für die Promotions-Administration
      * Unterkomponenten zum Rendern und Bearbeiten von Konfigurationsparametern, die spezifisch für die Promotion-Handler sind

   * Zwei Promotion-Handler werden standardmäßig bereitgestellt:

      * `DiscountPromotionHandler`, der einen absoluten oder prozentualen Rabatt auf den gesamten Warenkorb anwendet
      * `PerfectPartnerPromotionHandler`, der einen absoluten oder prozentualen Rabatt auf ein Produkt anwendet, wenn das Partnerprodukt ebenfalls im Warenkorb ist

   * Der ClientContext `SegmentMgr` löst Segmente auf und der ClientContext `CartMgr` löst Promotions auf. Jede Promotion, die mindestens einem aufgelösten Segment unterliegt, wird ausgelöst.

      * Ausgelöste Promotions werden über einen AJAX-Aufruf an den Server zurückgesendet, um den Warenkorb neu zu berechnen.
      * Ausgelöste Promotions (und hinzugefügte Gutscheine) werden auch im ClientContext-Bedienfeld angezeigt.

Das Hinzufügen/Entfernen eines Gutscheins aus einem Warenkorb erfolgt über die `CommerceSession`-API:

```java
/**
 * Apply a voucher to this session's cart.
 *
 * @param code the voucher's code
 * @throws CommerceException
 */
public void addVoucher(String code) throws CommerceException;

/**
 * Remove a voucher that was previously added with {@link #addVoucher(String)}.
 *
 * @param code the voucher's code
 * @throws CommerceException
 */
public void removeVoucher(String code) throws CommerceException;

/**
 * Get a list of vouchers that were added to this cart via {@link #addVoucher(String)}.
 *
 * @throws CommerceException
 */
public List<Voucher> getVouchers() throws CommerceException;
```

Auf diese Weise ist `CommerceSession` für die Überprüfung verantwortlich, ob ein Gutschein existiert und ob er angewendet werden kann oder nicht. Dies könnte Gutscheine betreffen, die nur angewendet werden können, wenn eine bestimmte Bedingung erfüllt ist; zum Beispiel, wenn der gesamte Warenkorbpreis größer als 100 € ist). Wenn ein Gutschein aus irgendeinem Grund nicht angewendet werden kann, löst die `addVoucher`-Methode eine Ausnahme aus. Außerdem ist die `CommerceSession` für die Aktualisierung der Preise im Warenkorb verantwortlich, nachdem ein Gutschein hinzugefügt/entfernt wurde.

Der `Voucher` ist eine Bean-ähnliche Klasse, die Felder enthält für:

* Gutscheincode
* Eine kurze Beschreibung
* Verweis auf die zugehörige Promotion, die den Rabatttyp und den Wert angibt

Die bereitgestellte `AbstractJcrCommerceSession` kann Gutscheine beantragen. Die von der Klasse `getVouchers()` zurückgegebenen Gutscheine sind Instanzen von `cq:Page`, die einen jcr:content-Knoten mit folgenden Eigenschaften enthalten (unter anderem):

* `sling:resourceType` (String) - dieser muss `commerce/components/voucher` sein

* `jcr:title` (String) - für die Beschreibung des Gutscheins
* `code` (String) - der Code, den der Benutzer eingeben muss, um den Gutschein anwenden
* `promotion` (String) - die anzuwendende Promotion; Beispiel: `/content/campaigns/geometrixx-outdoors/article/10-bucks-off`

Promotion-Handler sind OSGi-Dienste, die den Warenkorb verändern. Der Warenkorb unterstützt mehrere Hooks, die in der `PromotionHandler`-Schnittstelle definiert werden.

```java
/**
 * Apply promotion to a cart line item. The method returns a discount
 * <code>PriceInfo</code> instance or <code>null</code> if no discount
 * was applied.
 * @param commerceSession The commerce session
 * @param promotion The configured promotion
 * @param cartEntry The cart line item
 * @return A discounted <code>PriceInfo</code> or <code>null</code>
 */
public PriceInfo applyCartEntryPromotion(CommerceSession commerceSession,
                                         Promotion promotion, CartEntry cartEntry)
    throws CommerceException;

/**
 * Apply promotion to an order. The method returns a discount
 * <code>PriceInfo</code> instance or <code>null</code> if no discount
 * was applied.
 * @param commerceSession The commerce session
 * @param promotion The configured promotion
 * @return A discounted <code>PriceInfo</code> or <code>null</code>
 */
public PriceInfo applyOrderPromotion(CommerceSession commerceSession, Promotion promotion)
    throws CommerceException;

public PriceInfo applyShippingPromotion(CommerceSession commerceSession, Promotion promotion)
    throws CommerceException;

/**
 * Allows a promotion handler to define a custom, author-oriented message for a promotion.
 * The {@link com.adobe.cq.commerce.common.promotion.PerfectPartnerPromotionHandler}, for instance,
 * uses this to list the qualifying pairs of products in the current cart.
 * @param commerceSession
 * @param promotion
 * @return A message to display
 * @throws CommerceException
 */
public String getMessage(SlingHttpServletRequest request, CommerceSession commerceSession, Promotion promotion) throws CommerceException;

/**
 * Informs the promotion handler that something under the promotions root has been edited, and the handler
 * should invalidate any caches it might be keeping.
 */
public void invalidateCaches();
```

Drei Promotion-Handler stehen zur Verfügung:

* `DiscountPromotionHandler` wendet einen absoluten oder prozentualen Rabatt auf den gesamten Warenkorb an
* `PerfectPartnerPromotionHandler` wendet einen absoluten oder prozentualen Rabatt auf ein Produkt an, wenn sich das Partnerprodukt ebenfalls im Warenkorb befindet
* `FreeShippingPromotionHandler` wendet kostenlosen Versand an
