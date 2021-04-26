---
title: SAP Commerce Cloud
seo-title: SAP-Commerce Cloud
description: Hier erfahren Sie, wie Sie AEM mit SAP Commerce Cloud nutzen.
seo-description: Hier erfahren Sie, wie Sie AEM mit SAP Commerce Cloud nutzen.
uuid: cee1a781-fcba-461e-a0a4-c561a1dbcbf3
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
translation-type: tm+mt
source-git-commit: 1cef6f87fa66fd78d439c23e6ac907f9531b8fd6
workflow-type: tm+mt
source-wordcount: '1726'
ht-degree: 89%

---

# SAP-Commerce Cloud{#sap-commerce-cloud}

Nach der Installation können Sie Ihre Instanz konfigurieren:

1. [Konfigurieren Sie die Facettensuche für Geometrixx Outdoors](#configure-the-facetted-search-for-geometrixx-outdoors).
1. [Konfigurieren Sie die Katalogversion](#configure-the-catalog-version).
1. [Konfigurieren Sie die Importstruktur](#configure-the-import-structure).
1. [Konfigurieren Sie die zu ladenden Produktattribute](#configure-the-product-attributes-to-load).
1. [Importieren Sie die Produktdaten](#importing-the-product-data).
1. [Konfigurieren Sie das Katalog-Importtool](#configure-the-catalog-importer).
1. [Importieren Sie den Katalog mit dem Importtool](#catalog-import) zu einem bestimmten Ort in AEM.

## Konfigurieren der Facettensuche für Geometrixx Outdoors {#configure-the-facetted-search-for-geometrixx-outdoors}

>[!NOTE]
>
>Bei hybris 5.3.0.1 und höher ist dies nicht erforderlich.

1. Navigieren Sie im Browser zur **hybris-Verwaltungskonsole** unter:

   [http://localhost:9001/hmc/hybris](http://localhost:9001/hmc/hybris)

1. Wählen Sie in der Seitenleiste **System** > **Facettensuche** > **Konfiguration der Facettensuche** aus.
1. **Öffnen Sie den Editor** für die **Sample Solr Configuration for clothescatalog**.

1. Nutzen Sie unter **Katalogversionen** die Option **Katalogversion hinzufügen**, um `outdoors-Staged` und `outdoors-Online` zur Liste hinzuzufügen.
1. **Speichern Sie die Konfiguration.**
1. Öffnen Sie **SOLR-Elementtypen**, um **SOLR-Sortierungen** zu `ClothesVariantProduct` hinzuzufügen:

   * relevance („Relevanz“, score)
   * name-asc („Name (aufsteigend)“, name)
   * name-desc („Name (absteigend)“, name)
   * price-asc („Preis (aufsteigend)“, priceValue)
   * price-desc („Preis (absteigend)“, priceValue)

   >[!NOTE]
   >
   >Verwenden Sie das Kontextmenü (normalerweise Rechtsklick), um `Create Solr sort` auszuwählen.
   >
   >Bei Hybris 5.0.0 öffnen Sie die Registerkarte `Indexed Types`, klicken Sie mit der Dublette auf `ClothesVariantProduct` und dann auf die Registerkarte `SOLR Sort`.

   ![chlimage_1-36](/help/sites-administering/assets/chlimage_1-36a.png)

1. Legen Sie auf der Registerkarte **Indizierte Typen** unter **Zusammengestellter Typ** den folgenden Wert fest:

   `Product - Product`

1. Passen Sie auf der Registerkarte **Indizierte Typen** die **Indexerabfragen** auf `full` an:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}})
   ```

1. Passen Sie auf der Registerkarte **Indizierte Typen** die **Indexerabfragen** auf `incremental` an:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}}) AND {modifiedtime} <= ?lastIndexTime
   ```

1. Passen Sie auf der Registerkarte **Indizierte Typen** die Facette `category` an. Doppelklicken Sie auf den letzten Eintrag in der „category“-Liste, um die Registerkarte **Indizierte Eigenschaft** zu öffnen:

   >[!NOTE]
   >
   >Stellen Sie bei hybris 5.2 sicher, dass das Attribut `Facet` in der Tabelle „Eigenschaften“ entsprechend folgendem Screenshot ausgewählt ist:

   ![chlimage_1-37](/help/sites-administering/assets/chlimage_1-37a.png) ![chlimage_1-38](/help/sites-administering/assets/chlimage_1-38a.png)

1. Öffnen Sie die Registerkarte **Facetteneinstellungen** und passen Sie die Feldwerte an:

   ![chlimage_1-39](/help/sites-administering/assets/chlimage_1-39a.png)

1. **Speichern** Sie die Änderungen.
1. Passen Sie über **SOLR-Elementtypen** die Facette `price` entsprechend den folgenden Screenshots an. Wie bei `category` doppelklicken Sie auf `price`, um die Registerkarte **Indizierte Eigenschaft** zu öffnen:

   ![chlimage_1-40](/help/sites-administering/assets/chlimage_1-40a.png)

1. Öffnen Sie die Registerkarte **Facetteneinstellungen** und passen Sie die Feldwerte an:

   ![chlimage_1-41](/help/sites-administering/assets/chlimage_1-41a.png)

1. **Speichern** Sie die Änderungen.
1. Öffnen Sie **System**, **Facettensuche** und dann den **Indexervorgangsassistenten**. Starten Sie einen Cronjob:

   * **Indexervorgang**:  `full`
   * **Solr-Konfiguration**:  `Sample Solr Config for Clothes`

## Konfigurieren der Katalogversion {#configure-the-catalog-version}

Sie können die importierte **Katalogversion** (`hybris.catalog.version`) für den OSGi-Dienst konfigurieren:

**Day CQ Commerce Hybris Configuration**
( `com.adobe.cq.commerce.hybris.common.DefaultHybrisConfigurationService`)

**Katalogversion** wird in der Regel entweder auf `Online` oder `Staged` (Standard) festgelegt.

>[!NOTE]
>
>In AEM können Sie die Konfigurationseinstellungen für solche Dienste auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi. ](/help/sites-deploying/configuring-osgi.md) Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

Die Protokollausgabe bietet Feedback zu den erstellten Seiten und Komponenten und zeigt potenzielle Fehler auf.

## Konfigurieren der Importstruktur  {#configure-the-import-structure}

Die folgende Auflistung zeigt eine Beispielstruktur (von Assets, Seiten und Komponenten), die standardmäßig erstellt wird:

```shell
+ /content/dam/path/to/images
  + 12345.jpg (dam:Asset)
    + ...
  + ...
+ /content/site/en
  - cq:commerceProvider = "hybris"
  - cq:hybrisBaseStore = "basestore"
  - cq:hybrisCatalogId = "catalog"
  + category1 (cq:Page)
    + jcr:content (cq:PageContent)
      - jcr:title = "Category 1"
    + category11 (cq:Page)
      + jcr:content (cq:PageContent)
        - jcr:title = "Category 1.1"
      + 12345 (cq:Page)
        + jcr:content (cq:PageContent)
          + par
            + product (nt:unstructured)
              - cq:hybrisProductId = "12345"
              - sling:resourceType = "commerce/components/product"
              + image (nt:unstructured)
                - sling:resourceType = "commerce/components/product/image"
                - fileReference = "/content/dam/path/to/images/12345.jpg"
              + 12345.1-S (nt:unstructured)
                - cq:hybrisProductId = "12345.1-S"
                - sling:resourceType = "commerce/components/product"
                + image (nt:unstructured)
                  - sling:resourceType = "commerce/components/product/image"
                  - fileReference = "/content/dam/path/to/images/12345.1-S.jpg"
              + ...
```

Solch eine Struktur wird vom OSGi-Dienst `DefaultImportHandler` erstellt, der die Schnittstelle `ImportHandler` implementiert. Ein Import-Handler wird vom Importtool aufgerufen, um Produkte, Produktvariationen, Kategorien, Assets usw. zu erstellen.

>[!NOTE]
>
>Sie können [diesen Prozess anpassen, indem Sie Ihren eigenen Import-Handler implementieren](#configure-the-import-structure).

Die beim Importieren zu erstellende Struktur können Sie konfigurieren für:

``**Day CQ Commerce Hybris Default Import Handler**
`(com.adobe.cq.commerce.hybris.importer.DefaultImportHandler`)

In AEM können Sie die Konfigurationseinstellungen für solche Dienste auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi. ](/help/sites-deploying/configuring-osgi.md) Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

## Konfigurieren der zu ladenden Produktattribute  {#configure-the-product-attributes-to-load}

Sie können den Reaktionsparser so konfigurieren, dass er die Eigenschaften und Attribute definiert, die für (verschiedene) Produkte geladen werden sollen:

1. Konfigurieren Sie das OSGi-Bundle:

   **Day CQ Commerce Hybris Default Response Parser**
(`com.adobe.cq.commerce.hybris.impl.importer.DefaultResponseParser`)

   Hier können Sie verschiedene Optionen und Attribute definieren, die für das Laden und Zuordnungen benötigt werden.

   >[!NOTE]
   >
   >In AEM können Sie die Konfigurationseinstellungen für solche Dienste auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi. ](/help/sites-deploying/configuring-osgi.md) Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

## Importieren der Produktdaten {#importing-the-product-data}

Es gibt mehrere Methoden, um Produktdaten zu importieren. Sie können die Produktdaten importieren, wenn Sie die Umgebung erstmalig einrichten oder nachdem Änderungen an den hybris-Daten vorgenommen wurden:

* [Vollständiger Import](#full-import)
* [Inkrementeller Import](#incremental-import)
* [Express-Update](#express-update)

Die Produktdaten, die tatsächlich von hybris importiert wurden, werden im Repository unter folgendem Pfad gespeichert:

`/etc/commerce/products`

Die folgenden Eigenschaften geben die Verknüpfung mit hybris an:

* `commerceProvider`
* `cq:hybrisCatalogId`
* `cq:hybrisProductID`

>[!NOTE]
>
>Die hybris Implementierung (d.h. `geometrixx-outdoors/en_US`) speichert nur Produkt-IDs und andere grundlegende Informationen unter `/etc/commerce`.
>
>Immer, wenn Daten zu einem Produkt angefordert werden, wird auf den hybris-Server verwiesen.

### Vollständiger Import  {#full-import}

1. Löschen Sie bei Bedarf alle vorhandenen Produktdaten mit CRXDE Lite.

   1. Navigieren Sie zur Unterstruktur mit den Produktdaten:

      `/etc/commerce/products`

      Beispiel:

      [`http://localhost:4502/crx/de/index.jsp#/etc/commerce/products`](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

   1. Löschen Sie den Knoten, in dem die Produktdaten gespeichert sind, z. B. `outdoors`.
   1. Klicken Sie auf **Alle speichern**, um die Änderung zu übernehmen.

1. Öffnen Sie das hybris-Importtool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Konfigurieren Sie die erforderlichen Parameter, zum Beispiel:

   ![chlimage_1-42](/help/sites-administering/assets/chlimage_1-42a.png)

1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Nach dem Abschluss des Importvorgangs können Sie die Daten hier überprüfen:

   ```
       /etc/commerce/products/outdoors
   ```

   Sie können dies in CRXDE Lite öffnen. Beispiel:

   `[http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)`

### Inkrementeller Import {#incremental-import}

1. Überprüfen Sie die Informationen für die relevanten Produkte in AEM in der Verzeichnisstruktur unter:

   `/etc/commerce/products`

   Sie können dies in CRXDE Lite öffnen. Beispiel:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Aktualisieren Sie in hybris die gespeicherten Daten zu den relevanten Produkten.

1. Öffnen Sie das hybris-Importtool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Aktivieren Sie das Kontrollkästchen **Inkrementeller Import**.
1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Wenn abgeschlossen, können Sie die in AEM aktualisierten Daten überprüfen unter:

   ```
       /etc/commerce/products
   ```


### Express-Update {#express-update}

Der Importvorgang kann lange dauern. Als Erweiterung der Produktsynchronisierung können Sie daher bestimmte Bereiche des Katalogs für eine Express-Aktualisierung auswählen, die manuell ausgelöst wird. Diese Methode nutzt den Exportfeed zusammen mit der Standard-Attributkonfiguration.

1. Überprüfen Sie die Informationen für die relevanten Produkte in AEM in der Verzeichnisstruktur unter:

   `/etc/commerce/products`

   Sie können dies in CRXDE Lite öffnen. Beispiel:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Aktualisieren Sie in hybris die gespeicherten Daten zu den relevanten Produkten.

1. Fügen Sie in hybris die Produkte zur Express-Warteschlange hinzu, z. B.:

   ![chlimage_1-43](/help/sites-administering/assets/chlimage_1-43a.png)

1. Öffnen Sie das hybris-Importtool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Aktivieren Sie das Kontrollkästchen **Express-Aktualisierung**.
1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Wenn abgeschlossen, können Sie die in AEM aktualisierten Daten überprüfen unter:

   ```
       /etc/commerce/products
   ```

   ` [](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)`

## Konfigurieren des Katalog-Importtools {#configure-the-catalog-importer}

Sie können den hybris-Katalog in AEM importieren. Nutzen Sie dazu das Stapel-Importtool für hybris-Kataloge, -Kategorien und -Produkte.

Die vom Importtool verwendeten Parameter können für Folgendes konfiguriert werden:

**Day CQ Commerce Hybris Catalog Importer**
( `com.adobe.cq.commerce.hybris.impl.importer.DefaultHybrisImporter`)

In AEM können Sie die Konfigurationseinstellungen für solche Dienste auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi. ](/help/sites-deploying/configuring-osgi.md) Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

## Katalogimport {#catalog-import}

Das hybris-Paket umfasst ein Katalog-Importtool zum Einrichten der anfänglichen Seitenstruktur.

Verfügbar ist es unter:

`http://localhost:4502/etc/importers/hybris.html`

![ecommerceimportconsole](/help/sites-administering/assets/ecommerceimportconsole.png)

Sie müssen die folgenden Informationen angeben:

* **Basisspeicher** Die ID des in hybris konfigurierten Basisspeichers.

* **Katalog** Die ID des zu importierenden Katalogs.

* **Stammverzeichnis** Der Pfad, zu dem der Katalog importiert werden soll.

## Entfernen eines Produkts aus dem Katalog {#removing-a-product-from-the-catalog}

So entfernen Sie mindestens ein Produkt aus dem Katalog:

1. [Konfigurieren Sie den OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **Day CQ Commerce Hybris Catalog Importer**. Informationen hierzu finden Sie auch unter [Konfigurieren des Katalog-Importtools](#configure-the-catalog-importer).

   Aktivieren Sie die folgenden Eigenschaften:

   * **Enable product removal**
   * **Enable product asset removal**

   >[!NOTE]
   >
   >In AEM können Sie die Konfigurationseinstellungen für solche Dienste auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi. ](/help/sites-deploying/configuring-osgi.md) Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

1. Initialisieren Sie das Importtool, indem Sie zwei inkrementelle Aktualisierungen durchführen (siehe [Katalogimport](#catalog-import)):

   * Die erste Ausführung resultiert in einigen geänderten Produkten – aufgeführt in der Protokollliste.
   * Bei der zweiten Ausführung sollten keine Produkte aktualisiert werden.

   >[!NOTE]
   >
   >Der erste Importvorgang dient zur Initialisierung der Produktdaten. Der zweite Importvorgang überprüft, ob alles funktioniert hat und der Produktsatz bereit ist.

1. Aktivieren Sie die Kategorieseite, die das Produkt enthält, das Sie entfernen möchten. Die Produktdetails sollten angezeigt werden.

   Beispielsweise zeigt die folgende Kategorie Details zum Cajamara-Produkt:

   [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

1. Entfernen Sie das Produkt in der hybris-Konsole. Verwenden Sie die Option **Genehmigungsstatus** ändern, um den Status auf `unapproved` festzulegen. Das Produkt wird aus dem Live-Feed entfernt.

   Beispiel:

   * Öffnen Sie die Seite [http://localhost:9001/productcockpit](http://localhost:9001/productcockpit).
   * Wählen Sie den Katalog `Outdoors Staged`
   * Suchen Sie nach `Cajamara`
   * Wählen Sie dieses Produkt und ändern Sie den Genehmigungsstatus in `unapproved`

1. Führen Sie eine weitere inkrementelle Aktualisierung durch (siehe [Katalogimport](#catalog-import)). Im Protokoll wird das gelöschte Produkt aufgeführt.
1. Führen Sie den [Rollout](/help/commerce/cif-classic/administering/generic.md#rolling-out-a-catalog) für den entsprechenden Katalog durch. Das Produkt und die Produktseite wurden in AEM entfernt.

   Beispiel:

   * Öffnen Sie:

      [http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris](http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris)

   * Rollout des Katalogs `Hybris Base`
   * Öffnen Sie:

      [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

   * Das Produkt `Cajamara` wurde aus der Kategorie `Bike` entfernt

1. So installieren Sie das Produkt erneut:

   1. Ändern Sie in hybris den Genehmigungsstatus zurück in **Genehmigt**.
   1. In AEM:

      1. Führen Sie eine inkrementelle Aktualisierung durch.
      1. Führen Sie erneut den Rollout des entsprechenden Katalogs durch.
      1. Aktualisieren Sie die entsprechende Produktseite.

## Hinzufügen der Auftragsverlaufs-Eigenschaft zum Client Context  {#add-order-history-trait-to-the-client-context}

So fügen Sie einen Auftragsverlauf zum [Client Context](/help/sites-developing/client-context.md) hinzu:

1. Öffnen Sie die [Client Context-Designseite](/help/sites-administering/client-context.md) auf eine der folgenden Arten:

   * Öffnen Sie eine Seite zur Bearbeitung und öffnen Sie dann den Clientkontext mit **Strg-Alt-c** (Windows) oder **control-option-c** (Mac). Klicken Sie in der linken oberen Ecke von Client Context auf das Stiftsymbol, um **die ClientContext-Designseite zu öffnen**.
   * Navigieren Sie direkt zu [http://localhost:4502/etc/clientcontext/default/content.html](http://localhost:4502/etc/clientcontext/default/content.html).

1. [Fügen Sie die Komponente **Auftragsverlauf** zur](/help/sites-administering/client-context.md#adding-a-property-component) Komponente **Warenkorb** von Client Context hinzu.
1. Sie können bestätigen, dass der Client Context Details Ihres Auftragsverlaufs anzeigt. Beispiel:

   1. Öffnen Sie den [Client Context](/help/sites-administering/client-context.md).
   1. Fügen Sie einen Artikel zum Warenkorb hinzu.
   1. Schließen Sie den Bezahlvorgang ab.
   1. Überprüfen Sie den Client Context.
   1. Fügen Sie einen weiteren Artikel zum Warenkorb hinzu.
   1. Navigieren Sie zur Kassenseite:

      * Der Client Context zeigt eine Zusammenfassung des Auftragsverlaufs an.
      * Die Nachricht „Sie sind ein wiederkehrender Kunde.“ wird angezeigt.

   >[!NOTE]
   >
   >So wird die Nachricht realisiert:
   >
   >* Navigieren Sie zu [http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html](http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html)
   >
   >  Die Kampagne besteht aus einem Erlebnis.
   >
   >* Klicken Sie auf das Segment ([http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html](http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html))
      >
      >
   * Das Segment basiert auf der Eigenschaft **Order History Property**.

