---
title: AEM mit SAP Commerce Cloud verwenden
description: Erfahren Sie, wie Sie AEM mit SAP Commerce Cloud verwenden.
uuid: cee1a781-fcba-461e-a0a4-c561a1dbcbf3
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: c342f789-2ff7-4802-99c7-c3699218fe47
source-git-commit: e1a0b114ce16d0e7f6a464e9d30b8f111297bcc6
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 65%

---

# SAP Commerce Cloud{#sap-commerce-cloud}

Nach der Installation können Sie Ihre Instanz konfigurieren:

1. [Konfigurieren der Facettensuche für Geometrixx Outdoors](#configure-the-facetted-search-for-geometrixx-outdoors).
1. [Konfigurieren der Katalogversion](#configure-the-catalog-version).
1. [Konfigurieren der Importstruktur](#configure-the-import-structure).
1. [Konfigurieren der zu ladenden Produktattribute](#configure-the-product-attributes-to-load).
1. [Importieren der Produktdaten](#importing-the-product-data).
1. [Konfigurieren des Katalog-Import-Tools](#configure-the-catalog-importer).
1. Verwenden Sie die [Importer zum Importieren des Katalogs](#catalog-import) an einen bestimmten Ort in AEM.

## Konfigurieren der Facettensuche für Geometrixx Outdoors {#configure-the-facetted-search-for-geometrixx-outdoors}

>[!NOTE]
>
>Dies ist für hybris 5.3.0.1 und höher nicht erforderlich.

1. Navigieren Sie in Ihrem Browser zum **Hybris-Verwaltungskonsole** unter:

   [http://localhost:9001/hmc/hybris](http://localhost:9001/hmc/hybris)

1. Wählen Sie in der Seitenleiste **System**, dann **Facettensuche**, dann **Konfiguration der Facettensuche**.
1. **Öffnen Sie den Editor** für die **Solr-Beispielkonfiguration für „clothescatalog“**.

1. Nutzen Sie unter **Katalogversionen** die Option **Katalogversion hinzufügen**, um `outdoors-Staged` und `outdoors-Online` zur Liste hinzuzufügen.
1. **Speichern** Sie die Konfiguration.
1. Öffnen Sie **SOLR-Elementtypen**, um **SOLR-Sortierungen** zu `ClothesVariantProduct` hinzuzufügen:

   * Relevanz (&quot;Relevanz&quot;, Punktzahl)
   * name-asc (&quot;Name (aufsteigend)&quot;, name)
   * name-desc (&quot;Name (absteigend)&quot;, name)
   * price-asc (&quot;Price (aufsteigend)&quot;, priceValue)
   * price-desc (&quot;Preis (absteigend)&quot;, priceValue)

   >[!NOTE]
   >
   >Wählen Sie im Kontextmenü (in der Regel über Rechtsklick aufrufbar) `Create Solr sort` aus.
   >
   >Öffnen Sie für Hybris 5.0.0 die Registerkarte `Indexed Types`, doppelklicken Sie auf `ClothesVariantProduct`, dann auf die Registerkarte `SOLR Sort`.

   ![chlimage_1-36](/help/sites-administering/assets/chlimage_1-36a.png)

1. Legen Sie auf der Registerkarte **Indizierte Typen** unter **Zusammengestellter Typ** den folgenden Wert fest:

   `Product - Product`

1. Passen Sie auf der Registerkarte **Indizierte Typen** die **Indexerabfragen** für `full` an:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}})
   ```

1. Passen Sie auf der Registerkarte **Indizierte Typen** die **Indexerabfragen** für `incremental` an:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}}) AND {modifiedtime} <= ?lastIndexTime
   ```

1. Passen Sie auf der Registerkarte **Indizierte Typen** die Facette `category` an. Doppelklicken Sie auf den letzten Eintrag in der „category“-Liste, um die Registerkarte **Indizierte Eigenschaft** zu öffnen:

   >[!NOTE]
   >
   >Stellen Sie bei Hybris 5.2 sicher, dass das Attribut `Facet` in der Tabelle „Eigenschaften“ entsprechend folgendem Screenshot ausgewählt ist:

   ![chlimage_1-37](/help/sites-administering/assets/chlimage_1-37a.png) ![chlimage_1-38](/help/sites-administering/assets/chlimage_1-38a.png)

1. Öffnen Sie die Registerkarte **Facetteneinstellungen** und passen Sie die Feldwerte an:

   ![chlimage_1-39](/help/sites-administering/assets/chlimage_1-39a.png)

1. **Speichern** Sie die Änderungen.
1. Passen Sie über **SOLR-Elementtypen** die Facette `price` entsprechend den folgenden Screenshots an. Doppelklicken Sie wie bei `category` auf `price`, um die Registerkarte **Indizierte Eigenschaft** zu öffnen:

   ![chlimage_1-40](/help/sites-administering/assets/chlimage_1-40a.png)

1. Öffnen Sie die Registerkarte **Facetteneinstellungen** und passen Sie die Feldwerte an:

   ![chlimage_1-41](/help/sites-administering/assets/chlimage_1-41a.png)

1. **Speichern** Sie die Änderungen.
1. Öffnen **System**, **Facettensuche**, dann **Indexer-Vorgangsassistent**. Starten Sie einen Cronjob:

   * **Indexervorgang**: `full`
   * **Solr-Konfiguration**: `Sample Solr Config for Clothes`

## Konfigurieren der Katalogversion {#configure-the-catalog-version}

Sie können die importierte **Katalogversion** (`hybris.catalog.version`) für den OSGi-Service konfigurieren:

**Day CQ Commerce Hybris Configuration**
( `com.adobe.cq.commerce.hybris.common.DefaultHybrisConfigurationService`)

**Katalogversion** wird in der Regel entweder auf `Online` oder `Staged` (Standard) festgelegt.

>[!NOTE]
>
>In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

Die Protokollausgabe liefert Feedback zu den erstellten Seiten und Komponenten und meldet mögliche Fehler.

## Konfigurieren der Importstruktur {#configure-the-import-structure}

Die folgende Liste zeigt eine Beispielstruktur (von Assets, Seiten und Komponenten), die standardmäßig erstellt wird:

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

Solch eine Struktur wird vom OSGi-Service `DefaultImportHandler` erstellt, der die Schnittstelle `ImportHandler` implementiert. Der eigentliche Importeur ruft einen Import-Handler auf, um Produkte, Produktvarianten, Kategorien, Assets usw. zu erstellen.

>[!NOTE]
>
>Sie können [Anpassen dieses Prozesses durch Implementierung eines eigenen Import-Handlers](#configure-the-import-structure).

Die beim Import zu erzeugende Struktur kann für Folgendes konfiguriert werden:

``**Day CQ Commerce Hybris Default Import Handler**
`(com.adobe.cq.commerce.hybris.importer.DefaultImportHandler`)

In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

## Konfigurieren der zu ladenden Produktattribute {#configure-the-product-attributes-to-load}

Der Antwort-Parser kann so konfiguriert werden, dass er die Eigenschaften und Attribute definiert, die für (Varianten-)Produkte geladen werden sollen:

1. Konfigurieren Sie das OSGi-Bundle:

   **Day CQ Commerce Hybris Default Response Parser**
(`com.adobe.cq.commerce.hybris.impl.importer.DefaultResponseParser`)

   Hier können Sie verschiedene Optionen und Attribute definieren, die für das Laden und Zuordnungen benötigt werden.

   >[!NOTE]
   >
   >In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

## Importieren der Produktdaten {#importing-the-product-data}

Es gibt verschiedene Möglichkeiten, die Produktdaten zu importieren. Die Produktdaten können beim erstmaligen Einrichten der Umgebung oder nach Änderungen in den hybris-Daten importiert werden:

* [Vollständiger Import](#full-import)
* [Inkrementeller Import](#incremental-import)
* [Express-Update](#express-update)

Die Produktdaten, die tatsächlich von Hybris importiert wurden, werden im Repository unter folgendem Pfad gespeichert:

`/etc/commerce/products`

Die folgenden Eigenschaften geben die Verknüpfung mit Hybris an:

* `commerceProvider`
* `cq:hybrisCatalogId`
* `cq:hybrisProductID`

>[!NOTE]
>
>Die Hybris-Implementierung (d. h. `geometrixx-outdoors/en_US`) speichert nur Produkt-IDs und weitere grundlegende Daten unter `/etc/commerce`.
>
>Der hybris-Server wird jedes Mal referenziert, wenn Informationen zu einem Produkt angefordert werden.

### Vollständiger Import {#full-import}

1. Falls erforderlich, löschen Sie alle vorhandenen Produktdaten mit CRXDE Lite.

   1. Navigieren Sie zur Unterstruktur mit den Produktdaten:

      `/etc/commerce/products`

      Beispiel:

      [`http://localhost:4502/crx/de/index.jsp#/etc/commerce/products`](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

   1. Löschen Sie den Knoten, in dem die Produktdaten gespeichert sind, z. B. `outdoors`.
   1. Klicken Sie auf **Alle speichern**, um die Änderung zu übernehmen.

1. Öffnen Sie das Hybris-Import-Tool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Konfigurieren Sie die erforderlichen Parameter. Beispiel:

   ![chlimage_1-42](/help/sites-administering/assets/chlimage_1-42a.png)

1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Nach dem Abschluss des Importvorgangs können Sie die Daten hier überprüfen:

   ```
       /etc/commerce/products/outdoors
   ```

   Sie können den Pfad in CRXDE Lite öffnen, z. B.:

   `[http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)`

### Inkrementeller Import {#incremental-import}

1. Überprüfen Sie die in AEM gespeicherten Informationen auf das/die relevante(n) Produkt(e) im entsprechenden Unterbaum unter:

   `/etc/commerce/products`

   Sie können den Pfad in CRXDE Lite öffnen, z. B.:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Aktualisieren Sie in Hybris die gespeicherten Daten zu den relevanten Produkten.

1. Öffnen Sie das Hybris-Import-Tool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Wählen Sie das Kontrollkästchen aus **Inkrementeller Import**.
1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Nach Abschluss des Importvorgangs können Sie die aktualisierten Daten in AEM unter folgendem Pfad überprüfen:

   ```
       /etc/commerce/products
   ```


### Express-Update {#express-update}

Der Importvorgang kann lange dauern. Als Erweiterung der Produktsynchronisierung können Sie daher bestimmte Bereiche des Katalogs für ein Express-Update auswählen, das manuell ausgelöst wird. Dabei wird der Export-Feed zusammen mit der Konfiguration der Standardattribute verwendet.

1. Überprüfen Sie die in AEM gespeicherten Informationen auf das/die relevante(n) Produkt(e) im entsprechenden Unterbaum unter:

   `/etc/commerce/products`

   Sie können den Pfad in CRXDE Lite öffnen, z. B.:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Aktualisieren Sie in Hybris die gespeicherten Daten zu den relevanten Produkten.

1. Fügen Sie in Hybris die Produkte zur Express-Warteschlange hinzu, z. B.:

   ![chlimage_1-43](/help/sites-administering/assets/chlimage_1-43a.png)

1. Öffnen Sie das Hybris-Import-Tool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Wählen Sie das Kontrollkästchen aus **Express Update**.
1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Nach Abschluss des Importvorgangs können Sie die aktualisierten Daten in AEM unter folgendem Pfad überprüfen:

   ```
       /etc/commerce/products
   ```

## Konfigurieren des Katalog-Import-Tools {#configure-the-catalog-importer}

Sie können den Hybris-Katalog in AEM importieren. Nutzen Sie dazu das Batch-Import-Tool für Hybris-Kataloge, -Kategorien und -Produkte.

Die vom Import-Tool verwendeten Parameter können für Folgendes konfiguriert werden:

**Day CQ Commerce Hybris Catalog Importer**
( `com.adobe.cq.commerce.hybris.impl.importer.DefaultHybrisImporter`)

In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

## Katalogimport {#catalog-import}

Das hybris-Paket enthält ein Katalog-Importer zum Einrichten der anfänglichen Seitenstruktur.

Dies ist verfügbar unter:

`http://localhost:4502/etc/importers/hybris.html`

![ecommerceimportconsole](/help/sites-administering/assets/ecommerceimportconsole.png)

Sie müssen die folgenden Informationen angeben:

* **Basisspeicher**
Die ID des in Hybris konfigurierten Basisspeichers.

* **Katalog**
Die ID des zu importierenden Katalogs.

* **Stammverzeichnis**
Der Pfad, in den der Katalog importiert werden soll.

## Entfernen eines Produkts aus dem Katalog {#removing-a-product-from-the-catalog}

So entfernen Sie ein oder mehrere Produkte aus dem Katalog:

1. [Konfigurieren des für den OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **Day CQ Commerce Hybris Catalog Importer**; Siehe auch [Konfigurieren des Katalog-Importers](#configure-the-catalog-importer).

   Aktivieren Sie die folgenden Eigenschaften:

   * **Produktaktivierung aktivieren**
   * **Entfernen von Produkt-Assets aktivieren**

   >[!NOTE]
   >
   >In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

1. Initialisieren Sie das Import-Tool, indem Sie zwei inkrementelle Aktualisierungen durchführen (siehe [Katalogimport](#catalog-import)):

   * Die erste Ausführung resultiert in einigen geänderten Produkten – aufgeführt in der Protokollliste.
   * Zum zweiten Mal sollten keine Produkte aktualisiert werden.

   >[!NOTE]
   >
   >Der erste Import besteht darin, die Produktinformationen zu initialisieren. Der zweite Import überprüft, ob alles funktioniert hat und das Produkt fertig ist.

1. Überprüfen Sie die Kategorieseite mit dem Produkt, das Sie entfernen möchten. Die Produktdetails sollten sichtbar sein.

   Beispielsweise zeigt die folgende Kategorie Details zum Cajamara-Produkt:

   [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

1. Entfernen Sie das Produkt in der hybris-Konsole. Ändern Sie mit der Option **Genehmigungsstatus ändern** den Status in `unapproved`. Das Produkt wird aus dem Live-Feed entfernt.

   Beispiel:

   * Öffnen Sie die Seite [http://localhost:9001/productcockpit](http://localhost:9001/productcockpit).
   * Wählen Sie den Katalog `Outdoors Staged` aus.
   * Suchen Sie nach `Cajamara`.
   * Wählen Sie dieses Produkt aus und ändern Sie den Genehmigungsstatus in `unapproved`.

1. Führen Sie eine weitere inkrementelle Aktualisierung durch (siehe [Katalogimport](#catalog-import)). Das Protokoll listet das gelöschte Produkt auf.
1. [Rollout](/help/commerce/cif-classic/administering/generic.md#rolling-out-a-catalog) den entsprechenden Katalog. Die Produkt- und Produktseite wurde aus AEM entfernt.

   Beispiel:

   * Öffnen Sie:

      [http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris](http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris)

   * Führen Sie den Rollout des Katalogs `Hybris Base` durch.
   * Öffnen Sie:

      [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

   * Das Produkt `Cajamara` wurde aus der Kategorie `Bike` entfernt.

1. So aktivieren Sie das Produkt erneut:

   1. Ändern Sie in Hybris den Genehmigungsstatus zurück in **Genehmigt**.
   1. AEM:

      1. inkrementelle Aktualisierung durchführen
      1. Führen Sie erneut den Rollout des entsprechenden Katalogs durch.
      1. Aktualisieren der entsprechenden Kategorieseite

## Hinzufügen der Auftragsverlaufseigenschaft zum ClientContext {#add-order-history-trait-to-the-client-context}

So fügen Sie einen Auftragsverlauf zum [Client Context](/help/sites-developing/client-context.md) hinzu:

1. Öffnen Sie die [Client Context-Designseite](/help/sites-administering/client-context.md) auf eine der folgenden Arten:

   * Öffnen Sie eine Seite für die Bearbeitung und anschließend Client Context mit **Strg+Alt+C** (Windows) oder **Ctrl+Wahltaste+C** (Mac). Klicken Sie in der linken oberen Ecke von Client Context auf das Stiftsymbol, um **die ClientContext-Design-Seite zu öffnen**.
   * Direktes Navigieren zu [http://localhost:4502/etc/clientcontext/default/content.html](http://localhost:4502/etc/clientcontext/default/content.html)

1. [Fügen Sie die **Auftragsverlauf** component](/help/sites-administering/client-context.md#adding-a-property-component) der **Warenkorb** t -Komponente des ClientContext.
1. Sie können bestätigen, dass im Client-Kontext Details zum Auftragsverlauf angezeigt werden. Beispiel:

   1. Öffnen Sie die [Client-Kontext](/help/sites-administering/client-context.md).
   1. Fügen Sie dem Warenkorb einen Artikel hinzu.
   1. Beenden Sie den Checkout.
   1. Überprüfen Sie den Client-Kontext.
   1. Fügen Sie dem Warenkorb ein weiteres Element hinzu.
   1. Navigieren Sie zur Checkout-Seite:

      * Der Client Context zeigt eine Zusammenfassung des Auftragsverlaufs an.
      * Die Nachricht „Sie sind ein wiederkehrender Kunde“ wird angezeigt.

   >[!NOTE]
   >
   >So wird die Nachricht realisiert:
   >
   >* Navigieren Sie zu [http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html](http://localhost:4502/content/campaigns/geometrixx-outdoors/hybris-returning-customer.html).
   >
   >  Die Kampagne besteht aus einem Erlebnis.
   >
   >* Klicken Sie auf das Segment ([http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html](http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html)).
   >
   >* Das Segment basiert auf der Eigenschaft **Order History Property**.

