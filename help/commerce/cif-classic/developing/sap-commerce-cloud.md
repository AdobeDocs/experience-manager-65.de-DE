---
title: Entwicklung mit SAP Commerce Cloud
seo-title: Entwicklung mit SAP Commerce Cloud
description: Das Integrations-Framework SAP Commerce Cloud enthält eine Integrationsebene mit einer API
seo-description: Das Integrations-Framework SAP Commerce Cloud enthält eine Integrationsebene mit einer API
uuid: a780dd17-027a-4a61-af8f-3e2f600524c7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
translation-type: tm+mt
source-git-commit: 1cef6f87fa66fd78d439c23e6ac907f9531b8fd6
workflow-type: tm+mt
source-wordcount: '2329'
ht-degree: 85%

---

# Entwicklung mit SAP Commerce Cloud {#developing-with-sap-commerce-cloud}

>[!NOTE]
>
>Das eCommerce-Framework kann mit jeder eCommerce-Lösung verwendet werden. Bestimmte hier behandelte Aspekte und Beispiele beziehen sich auf die [Hybris](https://www.hybris.com/)-Lösung.

Das Integrations-Framework enthält eine Integrationsebene mit einer API. Dadurch können Sie:

* ein eCommerce-System einbinden und Produktdaten in AEM abrufen.

* AEM-Komponenten für Commerce-Funktionalität unabhängig von einer spezifischen eCommerce-Engine entwickeln.

![chlimage_1-11](/help/sites-developing/assets/chlimage_1-11a.png)

>[!NOTE]
>
>[API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) ist ebenfalls verfügbar.

Zur Verwendung der Integrationsebene stehen eine Reihe vordefinierter AEM zur Verfügung. Derzeit sind folgende Komponenten verfügbar:

* Produktanzeige
* Warenkorb
* Kasse

Für Suchen ist ein Integrations-Hook verfügbar, mit dem Sie die Suchfunktion von AEM, des eCommerce-Systems oder eines Drittanbieters (z. B. Search&amp;Promote) separat oder in Kombination verwenden können.

## Auswählen der eCommerce-Engine {#ecommerce-engine-selection}

Das eCommerce-Framework kann mit einer beliebigen eCommerce-Lösung verwendet werden, allerdings muss die verwendete Engine von AEM identifizierbar sein:

* eCommerce-Engines sind OSGi-Dienste, die die `CommerceService`-Schnittstelle unterstützen.

   * Engines können anhand einer `commerceProvider`-Service-Eigenschaft identifiziert werden.

* AEM unterstützt `Resource.adaptTo()` für `CommerceService` und `Product`

   * Die `adaptTo`-Implementierung sucht in der Ressourcenhierarchie nach einer `cq:commerceProvider`-Eigenschaft:

      * Falls eine Eigenschaft gefunden wird, wird der Wert zum Filtern der CommerceService-Suche verwendet.

      * Falls keine Eigenschaft gefunden wird, wird der Commerce-Service mit dem höchsten Rang verwendet.
   * Es wird ein `cq:Commerce`-Mixin verwendet, damit `cq:commerceProvider` zu stark typisierten Ressourcen hinzugefügt werden kann.


* Die `cq:commerceProvider`-Eigenschaft wird auch als Verweis auf die geeignete Commerce-Factory-Definition verwendet.

   * Eine `cq:commerceProvider`-Eigenschaft mit dem Wert `hybris` korreliert beispielsweise mit der OSGi-Konfiguration für **Day CQ Commerce Factory for** (com.adobe.cq.commerce.hybris.impl.HybrisServiceFactory), wenn der Parameter `commerceProvider` auch den Wert `hybris`hybris aufweist.

   * In diesem Fall können weitere Eigenschaften wie **Catalog version** konfiguriert werden (falls zutreffend und verfügbar).

Siehe folgendes Beispiel:

| `cq:commerceProvider = geometrixx` | in einer AEM-Standardinstallation eine spezifische Implementierung erforderlich ist; zum Beispiel das Beispiel geometrixx, das minimale Erweiterungen der generischen API enthält |
|--- |--- |
| `cq:commerceProvider = hybris` | Hybridimplementierung |

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

Die hybris Erweiterung des eCommerce-Integrationsrahmens wurde aktualisiert, um Hybris 5 zu unterstützen und gleichzeitig die Abwärtskompatibilität mit Hybris 4 zu gewährleisten.

Die Standardeinstellungen im Code sind auf Hybris 5 abgestimmt.

Für das Entwickeln mit Hybris 4 ist Folgendes erforderlich:

* Fügen Sie beim Aufrufen von maven dem Befehl das folgende Befehlszeilenargument hinzu

   `-P hybris4`

   Es lädt die vorkonfigurierte Hybris 4 Distribution herunter und bettet sie in das Bundle `cq-commerce-hybris-server` ein.

* Nehmen Sie im OSGi-Konfigurations-Manager folgende Einstellungen vor:

   * Deaktivieren Sie die Hybris 5-Unterstützung für den Default Response Parser-Dienst.

   * Stellen Sie sicher, dass der Hybris Basic Authentication Handler-Dienst einen niedrigeren Rang als der Hybris OAuth Handler-Dienst hat.

### Session-Handling {#session-handling}

Hybris verwendet eine Benutzersitzung zum Speichern von Daten, z. B. zum Warenkorb eines Kunden. Die Sitzungs-ID wird von Hybris in einem `JSESSIONID`-Cookie zurückgegeben, das bei nachfolgenden Anfragen an Hybris gesendet werden muss. Um zum vermeiden, dass die Sitzungs-ID im Repository gespeichert wird, ist sie als Code in ein anderes Cookie eingebettet, das im Browser des Kunden gespeichert wird. Die folgenden Schritte werden ausgeführt:

* Bei der ersten Anfrage wird kein Cookie für die Anfrage des Kunden gesetzt. An die Hybris-Instanz wird eine Anfrage gesendet, eine Sitzung zu erstellen.

* Die Sitzungs-Cookies werden aus der Antwort extrahiert, als Code in ein neues Cookie (z. B. `hybris-session-rest`) eingebettet und für die Antwort an den Kunden gesetzt. Die Kodierung in einem neuen Cookie ist erforderlich, da das ursprüngliche Cookie nur für einen bestimmten Pfad gültig ist und andernfalls bei nachfolgenden Anfragen nicht vom Browser zurückgesendet wird. Die Pfadinformationen müssen dem Wert des Cookies ebenfalls hinzugefügt werden.

* Bei nachfolgenden Anforderungen werden die Cookies aus den `hybris-session-<*xxx*>`-Cookies dekodiert und auf dem HTTP-Client gesetzt, der zum Anfordern von Daten von hybris verwendet wird.

>[!NOTE]
>
>Eine neue, anonyme Sitzung wird erstellt, wenn die ursprüngliche Sitzung nicht mehr gültig ist.

#### CommerceSession  {#commercesession}

* Diese Sitzung &quot;gehört&quot; dem **Warenkorb**

   * Sie führt Hinzufügen/Entfernen-Aktionen aus.

   * führt die verschiedenen Berechnungen im Warenkorb durch;

      `commerceSession.getProductPrice(Product product)`

* Sie steuert den *Speicherort* für die **Auftrags** daten

   `CommerceSession.getUserContext()`

* Sie steuert auch die Verbindung für die **Zahlungs** verarbeitung.

* Sie steuert ebenfalls die Verbindung für die **Auftragserfüllung**.

### Synchronisieren und Veröffentlichen von Produkten  {#product-synchronization-and-publishing}

In Hybris gepflegte Produktdaten müssen in AEM verfügbar sein. Dafür wurde folgende Methode implementiert:

* Die anfänglich geladenen IDs werden von Hybris als Feed bereitgestellt. Dieser Feed kann aktualisiert werden.
* Hybris stellt Update-Informationen über einen Feed bereit, (die AEM abruft).
* Beim Verwenden von Produktdaten sendet AEM Anfragen für die aktuellen Daten zurück an Hybris (bedingte GET-Anfrage mit Datum der letzten Änderung).
* In Hybris können Feed-Inhalte deklarativ angegeben werden.
* Die Zuordnung der Feed-Struktur zum AEM-Inhaltsmodell erfolgt auf AEM-Seite im Feed-Adapter.

![chlimage_1-12](/help/sites-developing/assets/chlimage_1-12a.png)

* Das Importtool (b) wird für die anfängliche Einrichtung der Seitenstruktur in AEM für Kataloge verwendet.
* Katalogänderungen in Hybris werden AEM über ein Feed mitgeteilt und dann in AEM wie folgt übernommen (b):

   * Produkt im Hinblick auf die Katalogversion hinzugefügt/gelöscht/geändert

   * Produkt genehmigt

* Die Hybris-Erweiterung stellt ein Abruf-Importtool („Hybris-Schema“) bereit, das für das Importieren von Änderungen in AEM in bestimmten Abständen konfiguriert werden kann (z. B. alle 24 Stunden, wobei das Intervall in Sekunden angegeben wird):

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

* Für das Synchronisieren von Produkten zwischen Katalogversionen muss die entsprechende AEM-Seite (a, c) aktiviert bzw. deaktiviert werden.

   * Wenn Sie ein Produkt zur **Online**-Version eines Katalogs hinzufügen möchten, müssen Sie die Produktseite aktivieren.

   * Wenn Sie ein Produkt entfernen möchten, müssen Sie die Seite deaktivieren.

* Das Aktivieren einer Seite in AEM (c) erfordert eine Prüfung (b) und ist nur möglich, wenn

   * sich das Produkt in der **Online**-Version eines Katalogs für Produktseiten befindet.

   * die Produkte, auf die verwiesen wird, in der **Online**-Version eines Katalogs für andere Seiten (z. B. Kampagnenseiten) verfügbar sind.

* Aktivierte Produktseiten müssen auf die **Online**-Version der Produktdaten zugreifen (d).

* Die AEM-Veröffentlichungsinstanz benötigt Zugriff auf Hybris, um Produkt- und personalisierte Daten abzurufen.

### Architektur {#architecture}

#### Architektur von Produkt und Varianten {#architecture-of-product-and-variants}

Ein einzelnes Produkt kann mehrere Varianten aufweisen, z. B. unterschiedliche Farben und/oder Größen. Für ein Produkt müssen so genannte *Variantenachsen* definiert werden, die angeben, welche Eigenschaften die Variante bestimmen.

Es sind jedoch nicht alle Eigenschaften Variantenachsen. Varianten können sich auch auf andere Eigenschaften auswirken, z. B. kann der Preis größenabhängig sein. Diese Eigenschaften können vom Kunden nicht ausgewählt werden und werden daher nicht als Variantenachsen angesehen.

Jedes Produkt bzw. jede Variante steht für eine Ressource und ist daher im Verhältnis 1:1 einem Repository-Knoten zugeordnet. Folglich kann ein spezifisches Produkt bzw. eine spezifische Variante eindeutig anhand des Pfads identifiziert werden.

Die Ressource des Produkts bzw. der Variante enthält nicht immer die tatsächlichen Produktdaten. Es kann sich um eine Repräsentation der Daten handeln, die sich in einem anderen System (wie Hybris) befinden. Beispielsweise werden Produktbeschreibungen, Preise und dergleichen nicht in AEM gespeichert, sondern in Echtzeit aus der eCommerce-Engine abgerufen.

Jede Produktressource kann durch ein `Product API` dargestellt werden. Die meisten Aufrufe in der Produkt-API sind variationsspezifisch (obwohl Varianten freigegebene Werte von einem Vorgänger übernehmen können), aber es gibt auch Aufrufe, bei denen die Variationssätze ( `getVariantAxes()`, `getVariants()` usw.) Liste werden.

>[!NOTE]
>
>In der Tat wird eine Variantenachse von dem Wert bestimmt, den `Product.getVariantAxes()` zurückgibt:
>* Hybris definiert diese für die Hybris-Implementierung.
>
>
Zwar können Produkte (im Allgemeinen) viele Variantenachsen haben, vorkonfigurierte Produktkomponenten jedoch nur zwei:
>
>1. `size`
   >
   >
1. plus eins mehr
>
>
Diese zusätzliche Variante wird über die `variationAxis`-Eigenschaft der Produktreferenz ausgewählt (normalerweise `color` für Geometrixx Outdoors).

#### Produktverweise und Produktdaten {#product-references-and-product-data}

Im Allgemeinen:

* befinden sich Produktdaten unter `/etc`

* und Produktverweise unter `/content`.

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

   * Produktknoten sind `nt:unstructured`.

   * Ein Produktknoten kann Folgendes sein:

      * Ein Verweis, wenn die Produktdaten an anderer Stelle gespeichert sind:

         * Produktverweise enthalten eine `productData`-Eigenschaft, die auf die Produktdaten verweist (normalerweise unter `/etc/commerce/products`).

         * Produktdaten sind hierarchisch. Produktattribute werden von den Vorgängern eines Produktdatenknotens geerbt.

         * Produktverweise können auch lokale Eigenschaften enthalten, die die in den Produktdaten angegebenen Eigenschaften überschreiben.
      * Ein Produkt als solches:

         * Ohne eine `productData`-Eigenschaft.

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

   * Die `CommerceSession` führt Hinzufügen/Entfernen-Aktionen usw. durch.
   * Die `CommerceSession` nimmt auch die diversen Berechnungen des Warenkorbs vor. ``

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

   * Bei Hybris steuert der Hybris-Server den Warenkorb.
   * Bei AEM werden Warenkörbe im Allgemeinen in [ClientContext](/help/sites-administering/client-context.md) gespeichert.

**Personalisierung**

* Die Personalisierung sollte immer mithilfe von [ClientContext](/help/sites-administering/client-context.md) erfolgen.
* In allen Fällen wird eine ClientContext `/version/` des Einkaufswagens erstellt:

   * Produkte sollten mit der `CommerceSession.addCartEntry()`-Methode hinzugefügt werden.

* Nachstehend sehen Sie ein Beispiel für Warenkorbinformationen in einem ClientContext-Warenkorb:

![chlimage_1-13](/help/sites-developing/assets/chlimage_1-13a.png)

#### Architektur der Kasse {#architecture-of-checkout}

**Warenkorb- und Auftragsdaten**

Die `CommerceSession` steuert die drei folgenden Elemente:

1. Inhalt des Warenkorbs
1. Preise
1. Auftragsdetails

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

   * Die `CommerceSession` besitzt Versandkosten.
   * Kann Versand-Details mit `updateOrder(Map<String, Object> delta)` abrufen/aktualisieren

>[!NOTE]
>
>Sie können eine Versandauswahl implementieren, z. B.:
>
>`yourProject/commerce/components/shippingpicker`:
>
>* Im Wesentlichen könnte dies eine Kopie von `foundation/components/form/radio` sein, jedoch mit Rückrufen von `CommerceSession` für:
   >
   >
* Überprüfen, ob die Methode verfügbar ist
>* Hinzufügen von Preisinformationen
>* Möglichkeit für Kunden, die Auftragsseite in AEM (einschließlich Obermenge der Versandmethoden und Beschreibungstexten) zu aktualisieren und weiterhin die Anzeige relevanter `CommerceSession`-Informationen zu steuern


**Zahlungsverarbeitung**

* Die `CommerceSession` steuert auch die Verbindung für die Zahlungsverarbeitung.

* Implementierungsprogramme müssen spezifische Aufrufe (an den ausgewählten Zahlungsverarbeitungsdienst) zur `CommerceSession`-Implementierung hinzufügen.

**Auftragserfüllung**

* Die `CommerceSession` steuert auch die Verbindung für die Auftragserfüllung.
* Implementierungprogramme müssen spezifische Aufrufe (an den ausgewählten Zahlungsverabeitungsdienst) zur `CommerceSession`-Implementierung hinzufügen.

### Suchdefinition {#search-definition}

Nach dem standardmäßigen Dienst-API-Modell stellt das Commerzbank-Projekt einen Satz suchbezogener APIs bereit, die in einzelnen Commerce-Engines implementiert werden können.

>[!NOTE]
>
>Derzeit wird die vorkonfigurierte Such-API nur von der Hybris-Engine implementiert.
>
>Die Such-API ist jedoch generisch und kann von jeder CommerceService-Suche einzeln implementiert werden.

Das eCommerce-Projekt enthält eine Standardsuchkomponenten in:

`/libs/commerce/components/search`

![chlimage_1-14](/help/sites-developing/assets/chlimage_1-14a.png)

Dabei wird die Such-API zum Abfragen der ausgewählten Commerce-Engine (siehe [Auswahl der eCommerce Engine](#ecommerce-engine-selection)) verwendet:

#### Such-API {#search-api}

Vom Kernprojekt werden mehrere generische bzw. Helper-Klassen bereitgestellt:

1. `CommerceQuery`

   Wird zum Beschreiben einer Suchabfrage verwendet (enthält Informationen zu Abfragetext, aktueller Seite, Seitengröße, Sortierung und ausgewählten Facetten). Alle eCommerce-Dienste, die die Such-API implementieren, erhalten Instanzen dieser Klasse, um die Suche durchführen zu können. Ein `CommerceQuery` kann von einem Anforderungsobjekt ( `HttpServletRequest`) instanziiert werden.

1. `FacetParamHelper`

   Eine Hilfsprogramm-Klasse, die eine statische Methode – `toParams` – zum Erzeugen von `GET`-Parameterzeichenfolgen aus einer Facettenliste und einem umgeschalteten Wert bereitstellt. Dies ist in der Benutzeroberfläche nützlich, wenn Sie einen Hyperlink für jeden Wert einer Facette anzeigen möchten, damit beim Klicken eines Benutzers auf den Hyperlink der entsprechende Wert umgeschaltet wird (z. B. aus der Abfrage entfernt wird, falls er ausgewählt war, oder andernfalls hinzugefügt wird). Damit wird die gesamte Logik zur Verarbeitung von Facetten, einschließlich Facetten mit einzelnen oder mehreren Werten, das Überschreiben von Werten usw., abgedeckt.

Einstiegspunkt für die Such-API ist die `CommerceService#search`-Methode, die ein `CommerceResult`-Objekt zurückgibt. Weitere Informationen zu diesem Thema finden Sie in der [API-Dokumentation](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation).

### Benutzerintegration  {#user-integration}

AEM kann mit diversen eCommerce-Systemen integriert werden. Dazu ist eine Strategie zum Synchronisieren von Kunden zwischen unterschiedlichen Systemen erforderlich, damit AEM-spezifischer Code nur an AEM weitergegeben wird, und umgekehrt:

* Authentifizierung

   Es wird angenommen, dass AEM nur das *Web-Front-End ist und daher* alle *-Authentifizierung durchführt.*

* Konten in Hybris

   AEM erstellt für jeden Käufer ein entsprechendes (Untergeordnet-)Konto in hybris. Der Benutzername dieses Kontos ist mit dem AEM Benutzernamen identisch. Ein kryptografisches Zufallskennwort wird automatisch in AEM erstellt und gespeichert (verschlüsselt).

#### Bereits vorhandene Benutzer {#pre-existing-users}

Vor einer vorhandenen Hybris-Implementierung kann ein AEM-Font-End platziert werden. Außerdem kann einer vorhandenen AEM-Installation eine Hybris-Engine hinzugefügt werden. Dazu müssen die Systeme bereits vorhandene Benutzer in beiden Systemen reibungslos verarbeiten können:

* AEM -> Hybris

   * Beim Anmelden bei Hybris (falls noch kein AEM-Benutzer vorhanden ist):

      * Erstellen Sie einen neuen Hybris-Benutzer mit einem kryptografischen Zufallskennwort.
      * Speichern Sie den Hybris-Benutzernamen im Benutzerverzeichnis des AEM-Benutzers.
   * Siehe: `com.adobe.cq.commerce.hybris.impl.HybrisSessionImpl#login()`


* Hybris -> AEM

   * Beim Anmelden bei AEM (falls das System einen Benutzer erkennt):

      * Versuchen Sie, sich mit dem angegebenen Benutzenamen/Kennwort bei Hybris anzumelden.
      * Falls erfolgreich, erstellen Sie einen neuen Benutzer in AEM mit demselben Kennwort (AEM-spezifisches Salt wird zu AEM-spezifischem Hash). 
   * Der obige Algorithmus wird in einem `AuthenticationInfoPostProcessor` von Sling implementiert.

      * Siehe: `com.adobe.cq.commerce.hybris.impl.user.LazyUserImporter.java`


### Anpassen des Import-Prozesses {#customizing-the-import-process}

Um vorhandene Funktionalität nutzen zu können, gilt Folgendes für den benutzerdefinierten Import-Handler:

* muss die `ImportHandler`-Schnittstelle implementieren

* kann das `DefaultImportHandler` erweitern.

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
  * @param parentPath    Path of parent category or base path of import in case of root category
  * @return Path of created category
  */
  public String createCategory(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;
}
```

Damit der benutzerdefinierte Handler vom Importtool erkannt wird, muss die `service.ranking`- -Eigenschaft einen Wert über 0 aufweisen, zum Beispiel.

```java
@Component
@Service
@Property(name = "service.ranking", value = 100)
public class MyImportHandler extends DefaultImportHandler
{
...
}
```
