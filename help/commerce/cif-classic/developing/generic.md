---
title: Entwicklung (generisch)
seo-title: Entwicklung (generisch)
description: Das Integrations-Framework enthält eine Integrationsebene mit einer API und ermöglicht es Ihnen, AEM-Komponenten für eCommerce-Funktionen zu erstellen
seo-description: Das Integrations-Framework enthält eine Integrationsebene mit einer API und ermöglicht es Ihnen, AEM-Komponenten für eCommerce-Funktionen zu erstellen
uuid: 393bb28a-9744-44f4-9796-09228fcd466f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 84%

---

# Entwicklung (generisch){#developing-generic}

>[!NOTE]
>
>[API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) ist ebenfalls verfügbar.

Das Integrations-Framework enthält eine Integrationsebene mit einer API. Dies ermöglicht es Ihnen, AEM-Komponenten für eCommerce-Funktionen (unabhängig von einer bestimmten eCommerce-Engine) zu erstellen. Außerdem können Sie die interne CRX-Datenbank verwenden oder ein eCommerce-System einbinden und Produktdaten in AEM ziehen.

Für die Verwendung der Integrationsschicht stehen eine Reihe vordefinierter AEM zur Verfügung. Derzeit sind folgende Komponenten verfügbar:

* Produktanzeige
* Warenkorb
* Promotions und Gutscheine
* Katalog- und Abschnitts-Blueprints
* Kasse
* Suchen

Für die Suche wird ein Integrations-Hook zur Verfügung gestellt, mit dem Sie die AEM-Suche, eine Suche Dritter (wie Search&amp;Promote) oder eine Kombination daraus verwenden können.

## Auswählen der eCommerce-Engine {#ecommerce-engine-selection}

Das eCommerce-Framework kann mit jeder eCommerce-Lösung verwendet werden, die verwendete Engine muss von AEM identifiziert werden - auch bei Verwendung der generischen AEM-Engine:

* eCommerce-Engines sind OSGi-Dienste, die die `CommerceService`-Schnittstelle unterstützen.

   * Engines können anhand einer `commerceProvider`-Service-Eigenschaft identifiziert werden.

* AEM unterstützt `Resource.adaptTo()` für `CommerceService` und `Product`

   * Die `adaptTo`-Implementierung sucht in der Ressourcenhierarchie nach einer `cq:commerceProvider`-Eigenschaft:

      * Falls eine Eigenschaft gefunden wird, wird der Wert zum Filtern der CommerceService-Suche verwendet.
      * Falls keine Eigenschaft gefunden wird, wird der Commerce-Service mit dem höchsten Rang verwendet.
   * Es wird ein `cq:Commerce` -Mixin verwendet, sodass `cq:commerceProvider` zu stark typisierten Ressourcen hinzugefügt werden kann.


* Die `cq:commerceProvider`-Eigenschaft wird auch als Verweis auf die geeignete Commerce-Factory-Definition verwendet.

   * Zum Beispiel korreliert eine Eigenschaft `cq:commerceProvider` mit dem Wert mit der OSGi-Konfiguration für **Day CQ Commerce Factory für Geometrixx-Outdoors** (`com.adobe.cq.commerce.hybris.impl.GeoCommerceServiceFactory`) - wobei der Parameter `commerceProvider` auch den Wert `geometrixx`geometrixx hat.
   * Hier können weitere Eigenschaften konfiguriert werden (falls zutreffend und verfügbar).

In einer Standard-AEM-Installation wird eine spezifische Implementierung benötigt, zum Beispiel:

|  |  |
|---|---|
| `cq:commerceProvider = geometrixx` | Geometrixx-Beispiel; Dies umfasst minimale Erweiterungen der generischen API |

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
>Mit CRXDE Lite können Sie sehen, wie dies in der Produktkomponente für die generische AEM-Implementierung gehandhabt wird:
>
>`/apps/geometrixx-outdoors/components/product`

### Session-Handling {#session-handling}

Eine Sitzung zum Speichern von Informationen über den Warenkorb des Kunden.

Die **CommerceSession**:

* Besitzt den **Warenkorb**

   * Sie führt Hinzufügen/Entfernen-Aktionen aus.
   * führt die verschiedenen Berechnungen für den Warenkorb durch;

      `commerceSession.getProductPriceInfo(Product product, Predicate filter)`

* Besitzt Persistenz der **order**-Daten:

   `CommerceSession.getUserContext()`

* Kann Versanddetails mit `updateOrder(Map<String, Object> delta)` abrufen/aktualisieren
* Sie steuert auch die Verbindung für die **Zahlungs** verarbeitung.
* Steuert ebenfalls die Verbindung für die **Auftragserfüllung**

### Architektur {#architecture}

#### Architektur von Produkt und Varianten  {#architecture-of-product-and-variants}

Ein einzelnes Produkt kann mehrere Varianten aufweisen, z. B. unterschiedliche Farben und/oder Größen. Für ein Produkt müssen so genannte *Variantenachsen* definiert werden, die angeben, welche Eigenschaften die Variante bestimmen.

Es sind jedoch nicht alle Eigenschaften Variantenachsen. Varianten können sich auch auf andere Eigenschaften auswirken, z. B. kann der Preis größenabhängig sein. Diese Eigenschaften können vom Kunden nicht ausgewählt werden und werden daher nicht als Variantenachsen angesehen.

Jedes Produkt bzw. jede Variante steht für eine Ressource und ist daher im Verhältnis 1:1 einem Repository-Knoten zugeordnet. Folglich kann ein spezifisches Produkt bzw. eine spezifische Variante eindeutig anhand des Pfads identifiziert werden.

Jede Produktressource kann durch ein `Product API` dargestellt werden. Die meisten Aufrufe in der Produkt-API sind variationsspezifisch (obwohl Varianten gemeinsame Werte von einem Vorgänger erben können), es gibt aber auch Aufrufe, in denen der Variantensatz aufgelistet wird ( `getVariantAxes()`, `getVariants()` usw.).

>[!NOTE]
>
>Eine Variantenachse wird tatsächlich von dem bestimmt, was `Product.getVariantAxes()` zurückgibt:
>
>* für die generische Implementierung liest AEM es aus einer Eigenschaft in den Produktdaten ( `cq:productVariantAxes`)
>
>
Zwar können Produkte (im Allgemeinen) viele Variantenachsen haben, vorkonfigurierte Produktkomponenten jedoch nur zwei:
>
>1. `size`
>1. plus eins mehr

>
>   
Diese zusätzliche Variante wird über die Eigenschaft `variationAxis` der Produktreferenz ausgewählt (normalerweise `color` für Geometrixx Outdoors).

#### Produktreferenzen und PIM-Daten {#product-references-and-pim-data}

Im Allgemeinen:

* befinden sich PIM-Daten unter `/etc`

* Produktverweise unter `/content`.

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
 * e.g. when using {@link Product#getVariants(VariantFilter filter)}.
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

* **Allgemeine Speichermethode**

   * Produktknoten weisen die Eigenschaft „nt:unstructured“ auf.
   * Ein Produktknoten kann Folgendes sein:

      * Ein Verweis, wenn die Produktdaten an anderer Stelle gespeichert sind:

         * Produktverweise enthalten eine `productData` -Eigenschaft, die auf die Produktdaten verweist (normalerweise unter `/etc/commerce/products`).
         * Produktdaten sind hierarchisch. Produktattribute werden von den Vorgängern eines Produktdatenknotens geerbt.
         * Produktverweise können auch lokale Eigenschaften enthalten, die die in den Produktdaten angegebenen Eigenschaften überschreiben.
      * Ein Produkt als solches:

         * Ohne eine `productData` -Eigenschaft.
         * Ein Produktknoten, der alle Eigenschaften lokal speichert (und keine productData-Eigenschaft enthält), erbt Produktattribute direkt von seinen Vorgängern.


* **AEM-generische Produktstruktur**

   * Jede Variante muss einen eigenen Blattknoten haben.
   * Die Produktschnittstelle stellt sowohl Produkte als auch Varianten dar, der zugeordnete Repository-Knoten gibt jedoch genau an, um was es sich handelt.
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

   * Für Preise können mehrere Modifikatoren gelten:

      * Mengenrabatte
      * Unterschiedliche Währungen
      * Mehrwertsteuerpflichtig und mehrwertsteuerfrei
   * Die Modifikatoren sind bei folgenden Schnittstellen vollständig offen:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`


**Speicher**

* Speicherung

   * Im AEM-generischen Fall werden Warenkörbe im [ClientContext](/help/sites-administering/client-context.md) gespeichert

**Personalisierung**

* Die Personalisierung sollte immer mithilfe von [ClientContext](/help/sites-administering/client-context.md) erfolgen.
* Eine ClientContext `/version/` des Warenkorbs wird in allen Fällen erstellt:

   * Produkte sollten mithilfe der `CommerceSession.addCartEntry()`-Methode hinzugefügt werden.

* Nachstehend sehen Sie ein Beispiel für Warenkorbinformationen in einem ClientContext-Warenkorb:

![chlimage_1-33](/help/sites-developing/assets/chlimage_1-33a.png)

#### Architektur der Kasse {#architecture-of-checkout}

**Warenkorb- und Auftragsdaten**

Die `CommerceSession` steuert die drei folgenden Elemente:

1. **Inhalt des Warenkorbs**

   Das Inhaltsschema des Warenkorbs wird von der API festgelegt:

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

* Auftragsformulare müssen häufig mehrere Versandoptionen (und Preise) enthalten.
* Die Preise können auf Elementen und Details des Auftrags, wie Gewicht und/oder Lieferadresse, basieren.
* Die `CommerceSession` hat Zugriff auf alle Abhängigkeiten und kann daher ähnlich wie Produktpreise behandelt werden:

   * Die `CommerceSession` ist Eigentümer der Versandpreise.
   * Verwenden Sie `updateOrder(Map<String, Object> delta)`, um Versanddetails abzurufen/zu aktualisieren.

### Suchdefinition {#search-definition}

Nach dem standardmäßigen Dienst-API-Modell stellt das Commerzbank-Projekt einen Satz suchbezogener APIs bereit, die in einzelnen Commerce-Engines implementiert werden können.

>[!NOTE]
>
>Derzeit wird die vorkonfigurierte Such-API nur von der Hybris-Engine implementiert.
>
>Die Such-API ist jedoch generisch und kann von jeder CommerceService-Suche einzeln implementiert werden.
>
>Obwohl die standardmäßig bereitgestellte generische Implementierung diese API nicht implementiert, können Sie sie erweitern und die Suchfunktionalität hinzufügen.

Das eCommerce-Projekt enthält eine Standardsuchkomponente in:

`/libs/commerce/components/search`

![chlimage_1-34](/help/sites-developing/assets/chlimage_1-34a.png)

Dabei wird die Such-API zum Abfragen der ausgewählten Commerce-Engine (siehe [Auswahl der eCommerce Engine](#ecommerce-engine-selection)) verwendet:

#### Such-API {#search-api}

Vom Kernprojekt werden mehrere generische bzw. Helper-Klassen bereitgestellt:

1. `CommerceQuery`

   Wird zum Beschreiben einer Suchabfrage verwendet (enthält Informationen zu Abfragetext, aktueller Seite, Seitengröße, Sortierung und ausgewählten Facetten). Alle eCommerce-Dienste, die die Such-API implementieren, erhalten Instanzen dieser Klasse, um die Suche durchführen zu können. Ein `CommerceQuery` kann von einem Anfrageobjekt ( `HttpServletRequest`) instanziiert werden.

1. `FacetParamHelper`

   Eine Hilfsprogramm-Klasse, die eine statische Methode – `toParams` – zum Erzeugen von `GET`-Parameterzeichenfolgen aus einer Facettenliste und einem umgeschalteten Wert bereitstellt. Dies ist in der Benutzeroberfläche nützlich, wenn Sie einen Hyperlink für jeden Wert einer Facette anzeigen möchten, damit beim Klicken eines Benutzers auf den Hyperlink der entsprechende Wert umgeschaltet wird (z. B. aus der Abfrage entfernt wird, falls er ausgewählt war, oder andernfalls hinzugefügt wird). Damit wird die gesamte Logik zur Verarbeitung von Facetten, einschließlich Facetten mit einzelnen oder mehreren Werten, das Überschreiben von Werten usw., abgedeckt.

Einstiegspunkt für die Such-API ist die `CommerceService#search`-Methode, die ein `CommerceResult`-Objekt zurückgibt. Weitere Informationen zu diesem Thema finden Sie in der API-Dokumentation.

### Entwickeln von Promotions und Gutscheinen {#developing-promotions-and-vouchers}

* Gutscheine:

   * Ein Gutschein ist eine seitenbasierte Komponente, die mit der Websites-Konsole erstellt/bearbeitet und unter folgendem Pfad gespeichert wird:

      `/content/campaigns`

   * Gutscheine umfassen:

      * einen Gutscheincode (den der Käufer im Warenkorb eingeben muss)
      * eine Gutscheinkennzeichnung (die angezeigt wird, wenn der Käufer den Gutschein im Warenkorb eingegeben hat)
      * einen Promotionpfad (der die Aktion definiert, die der Gutschein auslöst)
   * Gutscheine haben keine eigenen Datums-/Zeitangaben für Aktivierung und Deaktivierung, sondern nutzen die der übergeordneten Kampagnen.
   * Externe Commerce-Engines können ebenfalls Gutscheine bereitstellen; diese erfordern mindestens:

      * einen Gutscheincode
      * Eine `isValid()`-Methode
   * Die Komponente **Gutschein** ( `/libs/commerce/components/voucher`) bietet Folgendes:

      * einen Renderer für die Gutscheinadministration; er zeigt alle Gutscheine an, die sich aktuell im Warenkorb befinden
      * das Bearbeitungsdialogfeld (Formular), um die Gutscheine zu administrieren (hinzuzufügen/zu entfernen)
      * die Aktionen, die erforderlich sind, um Gutscheine zum Warenkorb hinzuzufügen oder daraus zu entfernen



* Promotions:

   * Eine Promotion ist eine seitenbasierte Komponente, die mit der Websites-Konsole erstellt/bearbeitet und unter folgendem Pfad gespeichert wird:

      `/content/campaigns`

   * Promotions umfassen:

      * eine Priorität
      * einen Promotion-Handler-Pfad
   * Sie können Promotions mit einer Kampagne verbinden, um ihre Datums-/Zeitangaben für Aktivierung und Deaktivierung zu definieren.
   * Sie können Promotions mit einem Erlebnis verbinden, um ihre Segmente zu definieren.
   * Promotions, die nicht mit einem Erlebnis verbunden sind, starten nicht von selbst, können aber durch einen Gutschein ausgelöst werden.
   * Die Komponente Promotion ( `/libs/commerce/components/promotion`) enthält:

      * Renderer und Dialogfelder für die Administration von Promotions
      * Subkomponenten für das Rendern und Bearbeiten von Konfigurationsparametern für die Promotion-Handler
   * Zwei Promotion-Handler sind im Lieferumfang enthalten:

      * `DiscountPromotionHandler`, der einen absoluten oder prozentualen Rabatt auf den gesamten Warenkorb anwendet
      * `PerfectPartnerPromotionHandler`, der einen absoluten oder prozentualen Rabatt auf ein Produkt anwendet, wenn das Partnerprodukt ebenfalls im Warenkorb ist
   * Die ClientContext `SegmentMgr` löst Segmente auf und die ClientContext `CartMgr` löst Promotions auf. Jede Promotion, die mindestens einem aufgelösten Segment unterliegt, wird ausgelöst.

      * Ausgelöste Promotions werden über einen AJAX-Aufruf an den Server zurückgesendet, um den Warenkorb neu zu berechnen.
      * Ausgelöst Promotions (und hinzugefügte Gutscheine), werden auch im ClientContext-Fenster angezeigt.




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

`Voucher` ist eine bohnenähnliche Klasse, die Felder für Folgendes enthält:

* Gutscheincode
* Kurzbeschreibung
* Verweis auf die verknüpfte Promotion, die den Rabatttyp und -wert angibt

Die bereitgestellte `AbstractJcrCommerceSession` kann Gutscheine beantragen. Die von der Klasse `getVouchers()` zurückgegebenen Gutscheine sind Instanzen von `cq:Page`, die einen jcr:content -Knoten mit den folgenden Eigenschaften enthalten (unter anderem):

* `sling:resourceType` (String) - dies muss  `commerce/components/voucher`

* `jcr:title` (String) - für die Beschreibung des Gutscheins
* `code` (String) - der Code, den der Benutzer eingeben muss, um den Gutschein anwenden
* `promotion` (String) - die anzuwendende Promotion; z. B.  `/content/campaigns/geometrixx-outdoors/article/10-bucks-off`

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
* `FreeShippingPromotionHandler` kostenlosen Versand
