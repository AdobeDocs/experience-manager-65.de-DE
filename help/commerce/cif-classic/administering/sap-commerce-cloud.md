---
title: Verwenden von AEM mit SAP Commerce Cloud
description: Erfahren Sie, wie Sie Adobe Experience Manager mit SAP Commerce Cloud verwenden.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: c342f789-2ff7-4802-99c7-c3699218fe47
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 100%

---

# SAP Commerce Cloud{#sap-commerce-cloud}

Nach der Installation können Sie Ihre Instanz konfigurieren:

1. [Konfigurieren der Facettensuche für Geometrixx Outdoors](#configure-the-facetted-search-for-geometrixx-outdoors).
1. [Konfigurieren der Katalogversion](#configure-the-catalog-version).
1. [Konfigurieren der Importstruktur](#configure-the-import-structure).
1. [Konfigurieren der zu ladenden Produktattribute](#configure-the-product-attributes-to-load).
1. [Importieren der Produktdaten](#importing-the-product-data).
1. [Konfigurieren des Katalog-Import-Tools](#configure-the-catalog-importer).
1. Verwenden Sie das [Importtool zum Importieren des Katalogs](#catalog-import) an einen bestimmten Speicherort in AEM.

## Konfigurieren der Facettensuche für Geometrixx Outdoors {#configure-the-facetted-search-for-geometrixx-outdoors}

>[!NOTE]
>
>Dies ist für Hybris 5.3.0.1 und spätere Versionen nicht erforderlich.

1. Navigieren Sie in Ihrem Browser zur **Hybris-Verwaltungskonsole** unter:

   [http://localhost:9001/hmc/hybris](http://localhost:9001/hmc/hybris)

1. Wählen Sie in der Seitenleiste **System** > **Facettensuche** > **Konfiguration der Facettensuche** aus.
1. **Öffnen Sie den Editor** für die **Solr-Beispielkonfiguration für „clothescatalog“**.

1. Nutzen Sie unter **Katalogversionen** die Option **Katalogversion hinzufügen**, um `outdoors-Staged` und `outdoors-Online` zur Liste hinzuzufügen.
1. **Speichern** Sie die Konfiguration.
1. Öffnen Sie **SOLR-Elementtypen**, um **SOLR-Sortierungen** zu `ClothesVariantProduct` hinzuzufügen:

   * relevance („Relevanz“, score)
   * name-asc („Name (aufsteigend)“, name)
   * name-desc („Name (absteigend)“, name)
   * price-asc („Preis (aufsteigend)“, priceValue)
   * price-desc („Preis (absteigend)“, priceValue)

   >[!NOTE]
   >
   >Wählen Sie im Kontextmenü (in der Regel über Rechtsklick aufrufbar) `Create Solr sort` aus.
   >
   >Für Hybris 5.0.0 öffnen Sie die Registerkarte `Indexed Types`, doppelklicken Sie auf `ClothesVariantProduct`, dann auf die Registerkarte `SOLR Sort`.

   ![chlimage_1-36](/help/sites-administering/assets/chlimage_1-36a.png)

1. Setzen Sie auf der Registerkarte **Indizierte Typen** den **zusammengestellten Typ** auf:

   `Product - Product`

1. Passen Sie auf der Registerkarte **Indizierte Typen** die **Indexer-Abfragen** für `full` an:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}})
   ```

1. Passen Sie auf der Registerkarte **Indizierte Typen** die **Indexer-Abfragen** für `incremental` an:

   ```shell
   SELECT {pk} FROM {Product} WHERE {pk} NOT IN ({{SELECT {baseProductpk} FROM {variantproduct}}}) AND {modifiedtime} <= ?lastIndexTime
   ```

1. Passen Sie auf der Registerkarte **Indizierte Typen** die Facette `category` an. Doppelklicken Sie auf den letzten Eintrag in der Kategorieliste, um die Registerkarte **Indizierte Eigenschaft** zu öffnen:

   >[!NOTE]
   >
   >Stellen Sie bei Hybris 5.2 sicher, dass das Attribut `Facet` in der Tabelle „Eigenschaften“ entsprechend folgendem Screenshot ausgewählt ist:

   ![chlimage_1-37](/help/sites-administering/assets/chlimage_1-37a.png) ![chlimage_1-38](/help/sites-administering/assets/chlimage_1-38a.png)

1. Öffnen Sie die Registerkarte **Facetteneinstellungen** und passen Sie die Feldwerte an:

   ![chlimage_1-39](/help/sites-administering/assets/chlimage_1-39a.png)

1. **Speichern** Sie die Änderungen.
1. Passen Sie über **SOLR-Elementtypen** die Facette `price` entsprechend den folgenden Screenshots an. Wie bei `category` doppelklicken Sie auf `price`, um die Registerkarte **Indizierte Eigenschaft** zu öffnen:

   ![chlimage_1-40](/help/sites-administering/assets/chlimage_1-40a.png)

1. Öffnen Sie die Registerkarte **Facetteneinstellungen** und passen Sie die Feldwerte an:

   ![chlimage_1-41](/help/sites-administering/assets/chlimage_1-41a.png)

1. **Speichern** Sie die Änderungen.
1. Öffnen Sie **System** > **Facettensuche** > **Indexervorgangsassistent**. Starten Sie einen Cronjob:

   * **Indexervorgang**: `full`
   * **Solr-Konfiguration**: `Sample Solr Config for Clothes`

## Konfigurieren der Katalogversion {#configure-the-catalog-version}

Sie können die importierte **Katalogversion** (`hybris.catalog.version`) für den OSGi-Service konfigurieren:

**Day CQ Commerce Hybris Configuration**
( `com.adobe.cq.commerce.hybris.common.DefaultHybrisConfigurationService`)

Die **Katalogversion** ist entweder auf `Online` oder `Staged` (Standard) eingestellt.

>[!NOTE]
>
>In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

Die Protokollausgabe bietet Feedback zu den erstellten Seiten und Komponenten und zeigt potenzielle Fehler auf.

## Konfigurieren der Importstruktur {#configure-the-import-structure}

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

Solch eine Struktur wird vom OSGi-Service `DefaultImportHandler` erstellt, der die Schnittstelle `ImportHandler` implementiert. Ein Import-Handler wird vom eigentlichen Import-Tool aufgerufen, um Produkte, Produktvarianten, Kategorien, Assets usw. zu erstellen.

>[!NOTE]
>
>Sie können [diesen Prozess anpassen, indem Sie Ihren eigenen Import-Handler implementieren](#configure-the-import-structure).

Die beim Importieren zu erzeugende Struktur kann für Folgendes konfiguriert werden:

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

Es gibt verschiedene Möglichkeiten, die Produktdaten zu importieren. Sie können die Produktdaten importieren, wenn Sie die Umgebung erstmalig einrichten oder nachdem Änderungen an den Hybris-Daten vorgenommen wurden:

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
>Die Hybris-Implementierung (d. h. `geometrixx-outdoors/en_US`) speichert nur Produkt-IDs und andere grundlegende Informationen unter `/etc/commerce`.
>
>Der Hybris-Server wird immer dann referenziert, wenn Informationen zu einem Produkt angefordert werden.

### Vollständiger Import {#full-import}

1. Löschen Sie ggf. alle vorhandenen Produktdaten mit CRXDE Lite.

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

1. Konfigurieren Sie die erforderlichen Parameter, zum Beispiel:

   ![chlimage_1-42](/help/sites-administering/assets/chlimage_1-42a.png)

1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Nach dem Abschluss des Importvorgangs können Sie die Daten hier überprüfen:

   ```
       /etc/commerce/products/outdoors
   ```

   Sie können den Pfad in CRXDE Lite öffnen, z. B.:

   `[http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)`

### Inkrementeller Import {#incremental-import}

1. Überprüfen Sie die Informationen für die relevanten Produkte in AEM in der entsprechenden Verzeichnisstruktur unter:

   `/etc/commerce/products`

   Sie können den Pfad in CRXDE Lite öffnen, z. B.:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Aktualisieren Sie in hybris die Informationen zu den betreffenden Produkten.

1. Öffnen Sie das Hybris-Import-Tool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Aktivieren Sie das Kontrollkästchen **Inkrementeller Import**.
1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Nach Abschluss des Importvorgangs können Sie die aktualisierten Daten in AEM unter folgendem Pfad überprüfen:

   ```
       /etc/commerce/products
   ```


### Express-Update {#express-update}

Der Importvorgang kann lange dauern. Als Erweiterung der Produktsynchronisierung können Sie daher bestimmte Bereiche des Katalogs für ein Express-Update auswählen, das manuell ausgelöst wird. Dafür wird der Export-Feed zusammen mit der Standard-Attributkonfiguration verwendet.

1. Überprüfen Sie die Informationen für die relevanten Produkte in AEM in der entsprechenden Verzeichnisstruktur unter:

   `/etc/commerce/products`

   Sie können den Pfad in CRXDE Lite öffnen, z. B.:

   [http://localhost:4502/crx/de/index.jsp#/etc/commerce/products](http://localhost:4502/crx/de/index.jsp#/etc/commerce/products)

1. Aktualisieren Sie in hybris die Informationen zu den betreffenden Produkten.

1. Fügen Sie in hybris ein oder mehrere Produkte zur Express-Warteschlange hinzu, zum Beispiel:

   ![chlimage_1-43](/help/sites-administering/assets/chlimage_1-43a.png)

1. Öffnen Sie das Hybris-Import-Tool in AEM:

   `/etc/importers/hybris.html`

   Beispiel:

   [http://localhost:4502/etc/importers/hybris.html](http://localhost:4502/etc/importers/hybris.html)

1. Aktivieren Sie das Kontrollkästchen **Express-Update**.
1. Klicken Sie auf **Katalog importieren**, um den Import zu starten.

   Nach Abschluss des Importvorgangs können Sie die aktualisierten Daten in AEM unter folgendem Pfad überprüfen:

   ```
       /etc/commerce/products
   ```

## Konfigurieren des Katalog-Import-Tools {#configure-the-catalog-importer}

Sie können den hybris-Katalog in AEM importieren. Nutzen Sie dazu das Batch-Import-Tool für hybris-Kataloge, -Kategorien und -Produkte.

Die vom Import-Tool verwendeten Parameter können für Folgendes konfiguriert werden:

**Day CQ Commerce Hybris Catalog Importer**
( `com.adobe.cq.commerce.hybris.impl.importer.DefaultHybrisImporter`)

In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

## Katalogimport {#catalog-import}

Das Hybris-Paket umfasst ein Katalog-Importtool zum Einrichten der anfänglichen Seitenstruktur.

Verfügbar ist es unter:

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

1. [Konfigurieren Sie den OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **Day CQ Commerce Hybris Catalog Importer**. Informationen hierzu finden Sie auch unter [Konfigurieren des Katalog-Importtools](#configure-the-catalog-importer).

   Aktivieren Sie die folgenden Eigenschaften:

   * **Entfernen von Produkten aktivieren**
   * **Entfernen von Produkt-Assets aktivieren**

   >[!NOTE]
   >
   >In AEM können Sie die Konfigurationseinstellungen für solche Services auf unterschiedliche Weise vornehmen. Umfassende Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md). Darüber hinaus enthält die Konsole eine vollständige Liste mit den konfigurierbaren Parametern und den dazugehörigen Standardwerten.

1. Initialisieren Sie das Import-Tool, indem Sie zwei inkrementelle Aktualisierungen durchführen (siehe [Katalogimport](#catalog-import)):

   * Der erste Lauf führt zu einer Reihe von geänderten Produkten, die in der Protokollliste angezeigt werden.
   * Bei der zweiten Ausführung sollten keine Produkte aktualisiert werden.

   >[!NOTE]
   >
   >Der erste Importvorgang dient zur Initialisierung der Produktdaten. Der zweite Importvorgang überprüft, ob alles funktioniert hat und der Produktsatz bereit ist.

1. Aktivieren Sie die Kategorieseite, die das Produkt enthält, das Sie entfernen möchten. Die Produktdetails sollten angezeigt werden.

   Beispielsweise zeigt die folgende Kategorie Details zum Produkt „Cajamara“:

   [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

1. Entfernen Sie das Produkt in der Hybris-Konsole. Ändern Sie mit der Option **Genehmigungsstatus ändern** den Status in `unapproved`. Das Produkt wird aus dem Live-Feed entfernt.

   Beispiel:

   * Öffnen Sie die Seite [http://localhost:9001/productcockpit](http://localhost:9001/productcockpit).
   * Wählen Sie den Katalog `Outdoors Staged` aus.
   * Suchen Sie nach `Cajamara`.
   * Wählen Sie dieses Produkt aus und ändern Sie den Genehmigungsstatus in `unapproved`.

1. Führen Sie eine weitere inkrementelle Aktualisierung durch (siehe [Katalogimport](#catalog-import)). Das Protokoll listet das gelöschte Produkt auf.
1. Führen Sie den [Rollout](/help/commerce/cif-classic/administering/generic.md#rolling-out-a-catalog) für den entsprechenden Katalog durch. Das Produkt und die Produktseite wurden aus AEM entfernt.

   Beispiel:

   * Öffnen Sie:

     [http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris](http://localhost:4502/aem/catalogs.html/content/catalogs/geometrixx-outdoors-hybris)

   * Führen Sie den Rollout des Katalogs `Hybris Base` durch.
   * Öffnen Sie:

     [http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html](http://localhost:4502/editor.html/content/geometrixx-outdoors/en_US/equipment/biking.html)

   * Das Produkt `Cajamara` wird aus der Kategorie `Bike` entfernt.

1. So aktivieren Sie das Produkt erneut:

   1. Ändern Sie in Hybris den Genehmigungsstatus zurück in **Genehmigt**.
   1. In AEM gilt:

      1. Führen Sie eine inkrementelle Aktualisierung durch.
      1. Führen Sie erneut den Rollout des entsprechenden Katalogs durch.
      1. Aktualisieren Sie die entsprechende Kategorieseite.

## Fügen Sie eine Auftragsverlaufs-Eigenschaft zum Client-Kontext hinzu. {#add-order-history-trait-to-the-client-context}

So fügen Sie einen Auftragsverlauf zum [Client Context](/help/sites-developing/client-context.md) hinzu:

1. Öffnen Sie die [Client Context-Designseite](/help/sites-administering/client-context.md) auf eine der folgenden Arten:

   * Öffnen Sie eine Seite für die Bearbeitung und anschließend Client Context mit **Strg+Alt+C** (Windows) oder **Ctrl+Wahltaste+C** (Mac). Verwenden Sie das Bleistiftsymbol in der oberen linken Ecke des Client-Kontextes, um **die ClientContext-Design-Seite zu öffnen**.
   * Navigieren Sie direkt zu [http://localhost:4502/etc/clientcontext/default/content.html](http://localhost:4502/etc/clientcontext/default/content.html).

1. [Fügen Sie die Komponente **Auftragsverlauf** ](/help/sites-administering/client-context.md#adding-a-property-component) zur Komponente **Warenkorb** des Client-Kontexts hinzu.
1. Sie können bestätigen, dass im Client-Kontext Details zum Auftragsverlauf angezeigt werden. Beispiel:

   1. Öffnen Sie den [Client-Kontext](/help/sites-administering/client-context.md).
   1. Fügen Sie dem Warenkorb einen Artikel hinzu.
   1. Beenden Sie den Checkout.
   1. Überprüfen Sie den Client-Kontext.
   1. Fügen Sie dem Warenkorb einen weiteren Artikel hinzu.
   1. Navigieren Sie zur Kasse:

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
   >* Klicken Sie auf das Segment ([http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html](http://localhost:4502/etc/segmentation/geometrixx-outdoors/returning-customer.html))
   >
   >* Das Segment basiert auf der Eigenschaft **Order History Property**.
