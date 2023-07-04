---
title: Verwalten von generischem eCommerce
seo-title: Administering generic eCommerce
description: Die AEM allgemeine Lösung bietet Methoden zum Verwalten der Commerce-Informationen, die im Repository gespeichert sind.
seo-description: The AEM generic solution provides methods of managing the commerce information held within the repository.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
docset: aem65
exl-id: c29f6213-1df6-45af-91c8-14b255276d82
source-git-commit: 6ebcc7bd5c72c01672244fdfba353a8949f6e331
workflow-type: tm+mt
source-wordcount: '2979'
ht-degree: 35%

---

# Verwalten von generischem eCommerce {#administering-generic-ecommerce}

Die AEM allgemeine Lösung bietet Methoden zum Verwalten der Commerce-Informationen, die im Repository gespeichert sind (im Gegensatz zur Verwendung einer externen E-Commerce-Engine). Hierzu gehört Folgendes:

* [Produkte](/help/commerce/cif-classic/administering/concepts.md#products)
* [Produktvarianten](/help/commerce/cif-classic/administering/concepts.md#product-variants)
* [Kataloge](/help/commerce/cif-classic/administering/concepts.md#catalogs)
* [Promotions](/help/commerce/cif-classic/administering/concepts.md#promotions)
* [Gutscheine](/help/commerce/cif-classic/administering/concepts.md#vouchers)
* [Bestellungen](/help/commerce/cif-classic/administering/concepts.md#shopping-cart-and-orders)
* [Proxyseiten](/help/commerce/cif-classic/administering/concepts.md#proxy-pages)

>[!NOTE]
>
>Die standardmäßige AEM-Installation umfasst die allgemeine AEM (JCR) eCommerce-Implementierung.
>
>Dies ist derzeit für Demonstrationszwecke oder als Basis für eine benutzerdefinierte Implementierung gemäß Ihren Anforderungen gedacht.

## Produkte und Produktvarianten {#products-and-product-variations}

>[!NOTE]
>
>Die folgenden Verfahren gelten sowohl für Produkte als auch für Produktvarianten.

Bevor Sie Produkte erstellen, müssen Sie eine [scaffold](/help/sites-authoring/scaffolding.md). Hier werden die Felder angegeben, die Sie zum Definieren der Produkte und deren Bearbeitung benötigen.

Für jeden einzelnen Produkttyp ist eine Grundlage erforderlich. Die entsprechende Strukturvorlage ist mit den Produkten verknüpft, indem Sie entweder:

* Pfad
* Produkt kann auf Strukturvorlage verweisen

>[!NOTE]
>
>Der Geometrixx-Outdoors-Store verfügt über nur einen Produkttyp (und somit auch nur eine Strukturvorlage):
>
>`/etc/scaffolding/geometrixx-outdoors`
>
>Der Geometrixx-Outdoors-Produkttyp ist aktiv unter:
>
>`/etc/commerce/products/geometrixx-outdoors`
>
>Sie können eine neue Produktdefinition an einer beliebigen Stelle unter dieser ohne zusätzliche Einrichtung erstellen.

### Importieren von Produkten {#importing-products}

#### Importieren von Produkten - Touch-optimierte Benutzeroberfläche {#importing-products-touch-optimized-ui}

1. Navigieren Sie zur **Produktekonsole** über die Option **Commerce**.
1. Verwenden der **Produkte** -Konsole navigieren Sie zum gewünschten Speicherort.
1. Verwenden Sie die **Importieren von Produkten** -Symbol, um den Assistenten zu öffnen.

   ![Symbol &quot;Produkte importieren&quot;](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. Geben Sie Folgendes an:

   * **Importtool**

     Das Import-Tool für den jeweiligen [E-Commerce-Anbieter](/help/commerce/cif-classic/administering/concepts.md#commerce-providers), (standardmäßig `Geometrixx`).

   * **Quelle**

     Die Datei, die importiert werden soll. Sie können den Browser nutzen, um eine Datei auszuwählen.

   * **Inkrementeller Import**

     Geben Sie an, ob dies ein inkrementeller Import ist (und kein vollständiger Import).

   >[!NOTE]
   >
   >Der inkrementelle Import (des Beispiel-Import-Tools „geometrixx-outdoors“) erfolgt auf Produktebene.
   >
   >Ein angepasstes Import-Tool kann so definiert werden, dass es wie gewünscht ausgeführt wird.

1. Auswählen **Nächste** zum Importieren der Produkte wird ein Protokoll der durchgeführten Aktionen angezeigt.

   >[!NOTE]
   >
   >Die Produkte werden an den aktuellen Speicherort importiert oder relativ zum aktuellen Speicherort.

   >[!NOTE]
   >
   >Wiederholte Verwendung von **Nächste** und **Zurück** wiederholt die Produktdefinitionen importieren. Da diese aber über dieselben SKUs verfügen, werden die im Repository vorhandenen Informationen einfach überschrieben.

1. Auswählen **Fertig** , um den Assistenten zu schließen.

#### Importieren von Produkten - Klassische Benutzeroberfläche {#importing-products-classic-ui}

1. Verwenden der **Instrumente** Konsole öffnen **Handel** Ordner.
1. Doppelklicken Sie, um das **Produkt-Import-Tool** zu öffnen:

   ![Produkt-Importkonsole](/help/sites-administering/assets/chlimage_1-22.jpeg)

1. Geben Sie Folgendes an:

   * **Name speichern**

     Die Produkte werden importiert in:

     `/etc/commerce/products/<*store name*>/`

   * **E-Commerce-Anbieter**

     Das Import-Tool für Ihren [E-Commerce-Anbieter](/help/commerce/cif-classic/administering/concepts.md#commerce-providers) (standardmäßig „Geometrixx“).

   * **Quelldatei**

     Der Ort der zu importierenden Datei im Repository.

   * **Inkrementeller Import**

     Geben Sie an, ob dies ein inkrementeller Import ist (und kein vollständiger Import).

1. Klicken **Importieren von Produkten**.

### Erstellen von Produktinformationen {#creating-product-information}

>[!NOTE]
>
>Die standardmäßige Produktverwaltung ist einfach aufgebaut, da dies auch für die Geometrixx-Outdoors-Produktgruppe gilt. Die Komplexität basiert auf der [Strukturvorlage](/help/sites-authoring/scaffolding.md) des Produkts. Indem Sie Ihre eigene Strukturvorlage für ein Produkt verwenden, können Sie also eine anspruchsvollere Bearbeitung erzielen.

#### Erstellen von Produktinformationen - Touch-optimierte Benutzeroberfläche {#creating-product-information-touch-optimized-ui}

1. Verwenden der **Produkte** console (via **Handel**) zum gewünschten Speicherort navigieren.
1. Verwenden Sie die **Erstellen** -Symbol, um eine der folgenden Optionen auszuwählen (je nach Struktur und Standort):

   * **Produkt erstellen**
   * **Produktvariante erstellen**

   ![Plus-Symbol zum Erstellen](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. Der Assistent wird geöffnet. Verwenden Sie die **Allgemein** und **Produktregisterkarten** , um [Produktattribute](/help/commerce/cif-classic/administering/concepts.md#product-attributes) für das neue Produkt oder die neue Produktvariante.

   >[!NOTE]
   >
   >**Titel** und **SKU** sind das Minimum, das zum Erstellen eines Produkts oder einer Variante erforderlich ist.

1. Auswählen **Erstellen** um die Informationen zu speichern.

>[!NOTE]
>
>Viele Produkte werden in verschiedenen Farben und/oder Größen angeboten. Informationen über das Basisprodukt und die zugehörigen Produktvarianten können beide über die **Produkte** Konsole.
>
>Produkte und ihre Varianten werden als Baumstruktur gespeichert. Die Produktinformationen befinden sich oben und die Varianten darunter (diese Struktur wird von der Benutzeroberfläche durchgesetzt).

### Bearbeiten von Produktinformationen {#editing-product-information}

>[!NOTE]
>
>Produktbilder in geometrixx-outdoors werden von folgenden Anbietern bereitgestellt:
>
>`/etc/commerce/products/...`
>
>Dies bedeutet, dass sie standardmäßig vom [dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de), konfigurieren Sie sie nach Bedarf.

#### Bearbeiten von Produktinformationen - Touch-optimierte Benutzeroberfläche {#editing-product-information-touch-optimized-ui}

1. Verwenden der **Produkte** console (via **Handel**) zu Ihren Produktinformationen navigieren.
1. Verwenden Sie entweder:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie das Symbol **Produktdaten anzeigen**:

   ![Symbol &quot;Produktdaten anzeigen&quot;- Informationssymbol](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. Die [Produktattribute](/help/commerce/cif-classic/administering/concepts.md#product-attributes) werden angezeigt. Verwenden Sie die Optionen **Bearbeiten** und **Fertig**, um Änderungen vorzunehmen.

### Anzeigen von Produktverweisen {#showing-product-references}

#### Anzeigen von Produktverweisen: Touch-optimierte Benutzeroberfläche {#showing-product-references-touch-optimized-ui}

1. Verwenden der **Produkte** console (via **Handel**) zu Ihren Produktinformationen navigieren.
1. Öffnen Sie die sekundäre Leiste für Verweise mit dem Symbol:

   ![Symbol mit Doppelpfeil](/help/sites-administering/do-not-localize/chlimage_1-16.png)

1. Wählen Sie das gewünschte Produkt aus. Die sekundäre Leiste wird aktualisiert, um die verfügbaren Verweistypen anzuzeigen:

   ![Produktkonsole mit geöffneten Verweisen](/help/sites-administering/assets/chlimage_1-88.png)

1. Klicken/tippen Sie auf den Referenztyp (z. B. Produktseiten), um die Liste zu erweitern.
1. Wählen Sie eine spezifische Referenz aus, um die Optionen anzuzeigen:

   * Zu Produktseite navigieren
   * Produktseite bearbeiten

   ![Produktkonsole - Referenzbereich](/help/sites-administering/assets/chlimage_1-89.png)

### Nach Produkten suchen {#search-for-products}

1. Navigieren Sie zur **Produktekonsole**; nutzen Sie dazu die Option **Commerce**.
1. Öffnen Sie die sekundäre Leiste für Suche mit dem Symbol:

   ![Lupensymbol](/help/sites-administering/do-not-localize/chlimage_1-17.png)

1. Für die Suche nach Produkten stehen verschiedene Facetten zur Verfügung. Sie können nur eine oder mehrere Facetten für eine Suche verwenden. Die gefundenen Produkte werden angezeigt:

   ![Produktdaten in der Produktkonsole](/help/sites-administering/assets/chlimage_1-90.png)

1. Wenn Sie auf ein Produkt klicken/tippen, wird es geöffnet. Sie können sie auch veröffentlichen oder die Produktdaten anzeigen.

#### Erweitern der Suche {#extending-search}

Sie können eine vorhandene Facette ändern oder neue hinzufügen, indem Sie CRXDE Lite verwenden:

1. Navigieren Sie zu:

   `http://localhost:4502/crx/de/index.jsp#/libs/commerce/gui/content/products/aside/items/search/items/searchpanel/facets`

1. Beispielsweise können Sie die Größen ändern, die auf der Seite für die Produktsuche angezeigt werden. Klicken Sie auf den Knoten `sizegroup`.
1. Klicken Sie auf den Knoten `items` und dann auf den Knoten `propertypredicate`.
1. Sie können die `propertyValues` ändern. Beispielsweise können Sie XS oder XXL hinzufügen oder eine Größe entfernen.
1. Klicken Sie auf **Alle speichern** und gehen Sie zur Seite für die Produktsuche. Ihre Änderungen sollten angezeigt werden.

### Mehrere Assets {#multiple-assets}

Sie können mehrere Assets zur Produktkomponente hinzufügen und dann das Asset angeben, das auf der Produktseite angezeigt wird.

>[!NOTE]
>
>Alles, was sich auf mehrere Assets bezieht, erfolgt über die Touch-optimierte Benutzeroberfläche.

#### Hinzufügen mehrerer Assets {#adding-multiple-assets}

1. Navigieren Sie zur **Produktekonsole**; nutzen Sie dazu die Option **Commerce**.
1. Navigieren Sie in der **Produktekonsole** zum gewünschten Produkt.

   >[!NOTE]
   >
   >Sie müssen sich auf der Produktebene befinden, nicht auf der Variantenebene.

1. Klicken oder tippen Sie auf das Symbol **Produktdaten anzeigen** (per Auswahlmodus oder Schnellaktionen).
1. Tippen/klicken Sie auf das Symbol Bearbeiten .
1. Scrollen Sie zu **Hinzufügen**.

   ![Screenshot zum Hinzufügen von Produktdaten](/help/sites-administering/assets/chlimage_1-91.png)

1. Tippen oder klicken Sie auf **Hinzufügen**. Ein neuer Asset-Platzhalter wird angezeigt.
1. Wenn Sie auf **Ändern** klicken oder tippen, wird ein Dialogfeld geöffnet, in dem Sie ein Asset wählen können.
1. Wählen Sie das Asset aus, das Sie hinzufügen möchten.

   >[!NOTE]
   >
   >Die Assets, die Sie auswählen können, stammen aus [Assets](/help/assets/assets.md).

1. Klicken oder tippen Sie auf das Symbol „Fertig“. 

Zwei Assets werden jetzt in Ihrer Produktkomponente gespeichert. Sie können konfigurieren, welche Seite auf der Produktseite angezeigt wird. Dies funktioniert mit einem Kategoriesystem. Zuerst müssen Sie den einzelnen Assets eine Kategorie hinzufügen:

1. Klicken oder tippen Sie auf **Produktdaten anzeigen**.
1. Geben Sie unter den Assets eine **Asset-Kategorie** ein, z. B. `cat1` und `cat2`.

   >[!NOTE]
   >
   >Sie können Tags auch für Kategorien verwenden.

1. Klicken oder tippen Sie auf das Symbol „Fertig“. Sie müssen jetzt [Rollout](#rolling-out-a-catalog) Ihre Änderungen.

Jetzt verfügen Ihre Assets in der Produktkomponente über eine Kategorie. Sie können konfigurieren, welche Kategorie auf drei verschiedenen Ebenen angezeigt wird:

* [Produktseite](#product-page)
* [Katalog](#catalog)
* [Produktekonsole](#products-console)

>[!NOTE]
>
>Wenn Sie keine Kategorien festlegen, wird das erste Asset auf der Produktseite angezeigt.

Die Auswahl des anzuzeigenden Bildes erfolgt wie folgt:

1. Überprüfen Sie, ob eine Kategorie für die Produktseite festgelegt ist.
1. Ist dies nicht der Fall, überprüfen Sie, ob eine Kategorie für den Katalog festgelegt ist.
1. Wenn nicht, überprüfen Sie, ob für die Produktekonsole eine Kategorie festgelegt ist.

>[!NOTE]
>
>Sowohl für die Katalogebene als auch für die Produktekonsole müssen Sie einen Rollout Ihrer Änderungen durchführen, um die Änderungen anzuwenden und den Unterschied auf der Produktseite zu sehen.

#### Produktseite {#product-page}

1. Navigieren Sie zu Ihrer Produktseite.
1. **Bearbeiten** die Produktkomponente.
1. Geben Sie die **Bildkategorie** ein, die Sie ausgewählt haben (z. B. `cat1`).
1. Klicken oder tippen Sie auf **Fertig**. Die Seite wird aktualisiert und das richtige Asset sollte angezeigt werden.

#### Katalog  {#catalog}

1. Navigieren Sie zu Ihrem Katalog.
1. Tippen/klicken **Eigenschaften anzeigen**.
1. Tippen/klicken Sie auf **Bearbeiten**.
1. Klicken oder tippen Sie auf die Registerkarte **Assets**.
1. Geben Sie die erforderlichen **Produkt-Asset-Kategorie**.
1. Klicken oder tippen Sie auf **Fertig**.
1. [Rollout](#rolling-out-a-catalog) Ihre Änderungen.

#### Produktekonsole {#products-console}

1. Navigieren Sie in der **Produktekonsole** zum gewünschten Produkt.
1. Klicken oder tippen Sie auf **Produktdaten anzeigen**.
1. Tippen/klicken Sie auf **Bearbeiten**.
1. Geben Sie einen **Standard-Asset-Kategorie**.
1. Klicken oder tippen Sie auf **Fertig**.
1. [Rollout](#rolling-out-a-catalog) Ihre Änderungen.

### Veröffentlichen/Rückgängigmachen der Veröffentlichung von Produktinformationen {#publishing-unpublishing-product-information}

#### Veröffentlichen/Rückgängigmachen der Veröffentlichung von Produktinformationen - Touch-optimierte Benutzeroberfläche {#publishing-unpublishing-product-information-touch-optimized-ui}

>[!NOTE]
>
>Häufig werden die Produktinformationen über die Seiten veröffentlicht, die darauf verweisen. Wenn Sie zum Beispiel Seite X veröffentlichen, die auf Produkt Y verweist, fragt AEM, ob Sie auch Produkt Y veröffentlichen möchten.
>
>Für Sonderfälle unterstützt AEM auch die direkte Veröffentlichung aus den Produktdaten.

1. Verwenden der **Produkte** console (via **Handel**) zu Ihren Produktinformationen navigieren.
1. Verwenden Sie entweder:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie je nach Bedarf das Symbol **Veröffentlichen** oder **Veröffentlichung rückgängig machen**:

   ![Welt-Symbol](/help/sites-administering/do-not-localize/chlimage_1-18.png) ![Weltsymbol mit einem Kreuz - kein Zeichen](/help/sites-administering/do-not-localize/chlimage_1-19.png)

   Die Produktinformationen werden entsprechend veröffentlicht bzw. die Veröffentlichung wird rückgängig gemacht.

<!-- Search&Promote is end of life as of September 1, 2022 ### Product Feed {#product-feed} -->

<!-- Search&Promote is end of life as of September 1, 2022 The Search&Promote integration allows you to: -->

<!-- Search&Promote is end of life as of September 1, 2022 * use the eCommerce API, independently of the underlying repository structure and commerce platform. -->
<!-- Search&Promote is end of life as of September 1, 2022 * leverage the Index Connector feature of Search&Promote to provide a product feed in XML format. -->
<!-- Search&Promote is end of life as of September 1, 2022 * leverage the Remote Control feature of Search&Promote to perform on-demand or scheduled requests of the product feed -->
<!-- Search&Promote is end of life as of September 1, 2022 * feed generation for different Search&Promote accounts, configured as cloud services configurations. -->

<!-- Search&Promote is end of life as of September 1, 2022 For more information, read [Product Feed](/help/sites-administering/product-feed.md). -->

### Ereignis-Handler für Produktaktualisierungen {#event-handler-for-product-updates}

Es gibt einen Ereignis-Handler, der ein Ereignis protokolliert, wenn ein Produkt hinzugefügt, geändert oder gelöscht und eine Produktseite hinzugefügt, geändert oder gelöscht wird. Es gibt die folgenden OSGi-Ereignisse:

* `com/adobe/cq/commerce/pim/PRODUCT_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_DELETED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_ADDED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_MODIFIED`
* `com/adobe/cq/commerce/pim/PRODUCT_PAGE_DELETED`

Für die `PRODUCT_*`-Ereignisse zeigt der Pfad auf das Basisprodukt unter `/etc/commerce/products`. Für die `PRODUCT_PAGE_*`-Ereignisse zeigt der Pfad auf den Knoten `cq:Page`.

Sie können diese in der Web-Konsole in den OSGi-Ereignissen (`/system/console/events` ) anzeigen, z. B.:

![Beispiele für OSGi-Ereignisse](/help/sites-administering/do-not-localize/chlimage_1-20.png)

>[!NOTE]
>
>Lesen Sie auch die Informationen unter [Ereignishandhabung in AEM](https://blogs.adobe.com/experiencedelivers/experience-management/event_handling_incq/).

### Bild mit Links für Hinzufügen zum Warenkorb {#image-with-add-to-cart-links}

Mit der Komponente Bild mit Zum Warenkorb-Links hinzufügen können Sie schnell ein Produkt zum Warenkorb hinzufügen, indem Sie einen Hotspot erstellen, der mit einem Produkt auf einem Bild verknüpft ist.

Durch Klicken auf den Hotspot wird ein Dialogfeld geöffnet, in dem Sie die Größe und Menge des Produkts auswählen können.

1. Navigieren Sie zu der Seite, auf der Sie die Komponente hinzufügen möchten.
1. Ziehen Sie die Komponente per Drag-and-Drop auf die Seite.
1. Ziehen Sie ein Bild in die Komponente aus dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser).
1. Wählen Sie eine der folgenden Möglichkeiten aus:

   * Klicken Sie auf die Komponente und dann auf das Symbol „Bearbeiten“.
   * Führen Sie einen langsamen Doppelklick aus.

1. Klicken Sie auf das Vollbildsymbol.

   ![fullscreen-Symbol](/help/sites-administering/assets/chlimage_1-92.png)

1. Klicken Sie auf das Symbol „Launch-Karte“.

   ![Symbol für Startkarte](/help/sites-administering/assets/chlimage_1-93.png)

1. Klicken Sie auf eines der Formsymbole.

   ![Formsymbole](/help/sites-administering/do-not-localize/chlimage_1-21.png)

1. Ändern und verschieben Sie die Form nach Bedarf.
1. Klicken Sie auf die Form.
1. Wenn Sie auf das Symbol &quot;Durchsuchen&quot;klicken, wird das [Asset-Auswahl](/help/assets/search-assets.md#assetpicker).

   >[!NOTE]
   >
   >Alternativ können Sie direkt den Produktpfad eingeben, der auf Produktebene und nicht auf Variantenebene sein muss.

   ![type path](/help/sites-administering/assets/chlimage_1-94.png)

1. Klicken Sie zweimal auf das Bestätigungssymbol und dann auf Vollbild beenden .
1. Klicken Sie auf eine beliebige Stelle auf der Seite neben der Komponente. Die Seite sollte aktualisiert werden und auf dem Bild sollte das folgende Symbol angezeigt werden:

   ![Pluszeichen](/help/sites-administering/do-not-localize/chlimage_1-22.png)

1. Wechseln zu [Vorschau](/help/sites-authoring/editing-content.md#previewingpagestouchoptimizedui) -Modus.
1. Klicken Sie auf den Hotspot + . Ein Dialogfeld wird geöffnet, in dem Sie die Größe und Menge für das Produkt auswählen können, das Sie unter **Pfad** eingegeben haben.

   ![Produktbeispiel: poncho](/help/sites-administering/assets/chlimage_1-95.png)

1. Geben Sie eine Größe und eine Menge ein.
1. Klicken Sie auf die Schaltfläche Zum Warenkorb hinzufügen . Das Dialogfeld wird geschlossen.
1. Navigieren Sie zu Ihrem Warenkorb. Das Produkt sollte hier sein.

#### Konfigurationsoptionen {#configuration-options}

Sie können konfigurieren, wie das Dialogfeld aussieht, wenn Sie auf den Hotspot klicken:

1. Klicken Sie auf die Komponente und dann auf das Konfigurationssymbol.

   ![Symbol zum Konfigurieren](/help/sites-administering/assets/chlimage_1-96.png)

1. Bildlauf nach unten. Es gibt eine **ZUM WARENKORB HINZUFÜGEN** Registerkarte.

   ![Zum Warenkorb hinzufügen](/help/sites-administering/assets/chlimage_1-97.png)

1. Klicken **ZUM WARENKORB HINZUFÜGEN**. Es gibt 3 Konfigurationsoptionen, die Sie verwenden können.

   ![Konfigurationsoptionen](/help/sites-administering/assets/chlimage_1-98.png)

1. Klicken Sie auf das Symbol Fertig .

## Kataloge {#catalogs}

### Erstellen eines Katalogs {#generating-a-catalog}

#### Generieren eines Katalogs: Touch-optimierte Benutzeroberfläche {#generating-a-catalog-touch-optimized-ui}

>[!NOTE]
>
>Im Katalog wird auf Ihre Produktdaten verwiesen.

Generieren Sie wie folgt einen Katalog:

1. Öffnen Sie die Sites-Konsole (z. B. [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)).
1. Navigieren Sie zu der Position, an der Sie die neue Seite erstellen möchten.
1. Um die Optionsliste zu öffnen, verwenden Sie das Symbol **Erstellen**:

   ![create-icon](/help/sites-administering/do-not-localize/chlimage_1-23.png)

1. Wählen Sie in der Liste die Option **Katalog erstellen**. Der Assistent für das Erstellen eines Katalogs wird geöffnet.

   ![Assistent zum Erstellen eines Katalogs](/help/sites-administering/assets/chlimage_1-99.png)

1. Navigieren Sie zum gewünschten Katalog-Blueprint.
1. Tippen/klicken **Auswählen** und tippen/klicken Sie auf den gewünschten Katalog-Blueprint.
1. Klicken oder tippen Sie auf **Weiter**.

   ![Assistent für Katalogeigenschaften](/help/sites-administering/assets/chlimage_1-100.png)

1. Geben Sie einen **Titel** und einen **Namen** ein.
1. Tippen/klicken Sie auf **Erstellen** Schaltfläche. Der Katalog wird erstellt und ein Dialogfeld wird geöffnet.

   ![Dialogfeld &quot;Katalog erstellt&quot;](/help/sites-administering/assets/chlimage_1-101.png)

1. Wenn Sie auf die Schaltfläche **Fertig** klicken oder tippen, gelangen Sie wieder zur Sites-Konsole, in der der Katalog angezeigt wird.

   Wenn Sie auf die Schaltfläche **Katalog öffnen** klicken oder tippen, wird Ihr Katalog geöffnet (z. B. `http://localhost:4502/editor.html/content/test-catalog.html`).

#### Erstellen eines Katalogs: Klassische Benutzeroberfläche {#generating-a-catalog-classic-ui}

>[!NOTE]
>
>Der Katalog verweist auf Ihre [Produktdaten](#products-and-product-variants).

1. Verwenden der **Websites** Konsole, navigieren Sie zu Ihrer **Katalog-Blueprint**, dann den Basiskatalog.

   Beispiel:

   `http://localhost:4502/siteadmin#/content/catalogs/geometrixx-outdoors/base-catalog`

1. Erstellen Sie mit der Vorlage **Bereichs-Blueprint** eine neue Seite.

   Beispiel: `Swimwear`.

1. Öffnen Sie die neue Seite `Swimwear` und klicken Sie dann auf **Blueprint bearbeiten**, um das Dialogfeld **Eigenschaften** zu öffnen, in dem Sie die Auswahl **Produkte** einrichten können.

   Öffnen Sie beispielsweise die **Tags/Keywords** -Feld, um &quot;Aktivität&quot;auszuwählen, und dann im Bereich &quot;Geometrixx-Outdoors&quot;die Option Schwimmen .

1. Klicken **OK** Speichern Ihrer Eigenschaften; Beispielprodukte werden unter der **Produktauswahlkriterien** auf der Blueprint-Seite.
1. Klicken Sie auf **Rollout-Änderungen...** auswählen **Rollout-Seite und alle Unterseiten** Klicken Sie auf **Nächste** then **Rollout**. Nachdem der Rollout erfolgreich abgeschlossen wurde, wird als **Status** die Farbe Grün angezeigt.
1. Sie können jetzt auf **Schließen** klicken und den neuen Katalogbereich überprüfen, z. B. unter:

   `http://localhost:4502/cf#/content/geometrixx-outdoors/en/swimwear.html`

1. Klicken Sie ebenfalls auf der Blueprint-Seite auf **Blueprint bearbeiten** und öffnen Sie im Dialogfeld **Eigenschaften** die Registerkarte **Erzeugte Seite**. Wählen Sie im Banner-Listenfeld das gewünschte Bild aus, z. B. `summer.jpg`.
1. Klicken **OK** Speichern Ihrer Eigenschaften; Bannerinformationen werden unter der **Produktauswahlkriterien** auf der Blueprint-Seite.
1. Rollout dieser neuen Änderungen.

### Durchführen des Rollouts für einen Katalog {#rolling-out-a-catalog}

#### Rollout eines Katalogs: Touch-optimierte Benutzeroberfläche {#rolling-out-a-catalog-touch-optimized-ui}

So erstellen Sie einen Katalog:

1. Navigieren Sie über die Option **Commerce** zur **Katalogkonsole**.
1. Navigieren Sie zum Katalog, für den Sie einen Rollout durchführen möchten.
1. Verwenden Sie entweder:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie das Symbol **Rollout-Änderungen**:

   ![Rollout](/help/sites-administering/do-not-localize/chlimage_1-24.png)

1. Legen Sie im Assistenten den Rollout wie gewünscht fest und klicken oder tippen Sie dann auf **Rollout-Änderungen**.
1. Ein Dialogfeld wird geöffnet. Klicken oder tippen Sie auf **Fertig**, wenn der Prozess abgeschlossen ist.

#### Rollout eines Katalogs: Klassische Benutzeroberfläche {#rolling-out-a-catalog-classic-ui}

So erstellen Sie einen Katalog:

1. Navigieren Sie zu dem Katalog, für den Sie den Rollout durchführen möchten. Beispiel:

   `http://localhost:4502/cf#/content/catalogs/geometrixx-outdoors/base-catalog.html`

1. Klicken **Rollout-Änderungen...**
1. Legen Sie den Rollout nach Bedarf fest.
1. Klicken Sie auf **Rollout**.

### Blueprint-Importtool {#blueprint-importer}

#### Blueprint-Importtool - Touch-optimierte Benutzeroberfläche {#blueprint-importer-touch-optimized-ui}

1. Navigieren Sie über die Option **Commerce** zur **Katalogkonsole**.
1. Navigieren Sie zu dem Speicherort, an dem Sie den Katalog-Blueprint importieren möchten.
1. Tippen/klicken Sie auf **Importieren von Blueprints** Symbol.

   ![Symbol &quot;Blueprint importieren&quot;](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. Wählen Sie im Assistenten die gewünschte Quelle aus und tippen/klicken Sie auf **Nächste**.

   ![Blueprint-Assistent](/help/sites-administering/assets/chlimage_1-102.png)

1. Tippen/klicken **Fertig** nach Abschluss des Imports.

#### Blueprint-Importtool - Klassische Benutzeroberfläche {#blueprint-importer-classic-ui}

1. Navigieren Sie über die **Tools**-Konsole zu **Commerce**.

   Beispiel:

   `http://localhost:4502/miscadmin#/etc/commerce`

1. Öffnen Sie die **Katalog-Blueprint-Importtool**.
1. Legen Sie den Import nach Bedarf fest.
1. Klicken **Katalog-Blueprints importieren**.

## Promotions {#promotions}

### Erstellen einer Promotion {#creating-a-promotion}

#### Erstellen einer Promotion: Klassische Benutzeroberfläche {#creating-a-promotion-classic-ui}

>[!NOTE]
>
>Das folgende Beispiel behandelt eine Promotion, die direkt in einer [Kampagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md), wird dies für Gutscheine verwendet.
>
>Eine Promotion kann auch in einer [Erlebnis](/help/sites-authoring/personalization.md) innerhalb einer Kampagne.
>
>Weitere Informationen finden Sie unter [Promotions und Gutscheine](#promotions-and-vouchers).

1. Öffnen Sie die **Websites** -Konsole Ihrer Autoreninstanz.
1. Wählen Sie im linken Bereich die gewünschte **Kampagne**.
1. Klicken Sie auf **Neu**, wählen Sie die **Promotion** Vorlage und geben Sie dann eine **Titel** und **Name** falls erforderlich) für Ihren neuen Gutschein.
1. Klicken Sie auf **Erstellen**. Die neue Promotion-Seite wird im rechten Bereich angezeigt.

1. Bearbeiten Sie die **Eigenschaften**, indem Sie eine der folgenden Möglichkeiten wählen:

   * Öffnen Sie die Seite und klicken Sie dann auf die Schaltfläche „Bearbeiten“, um das Dialogfeld „Eigenschaften“ zu öffnen.
   * Wählen Sie die Seite in der Websites-Konsole aus und wählen Sie dann mithilfe des Kontextmenüs (in der Regel die rechte Maustaste) **Eigenschaften...** und öffnen Sie das Dialogfeld &quot;Eigenschaften&quot;

   Geben Sie die **Promotion-Typ**, **Rabatttyp**, **Rabattwert** und anderen Feldern nach Bedarf.

1. Klicken Sie zum Speichern auf **OK**.

1. Sie können Ihre Promotion jetzt aktivieren, damit sie den Käufern in der Veröffentlichungsinstanz angezeigt wird.

## Gutscheine {#vouchers}

### Erstellen eines Gutscheins {#creating-a-voucher}

#### Erstellen eines Gutscheins: Klassische Benutzeroberfläche {#creating-a-voucher-classic-ui}

1. Öffnen Sie die **Websites** -Konsole Ihrer Autoreninstanz.
1. Wählen Sie im linken Bereich die gewünschte **Kampagne**.
1. Klicken Sie auf **Neu**, wählen Sie die **Gutschein** Vorlage und geben Sie dann eine **Titel** und **Name** falls erforderlich) für Ihren neuen Gutschein.
1. Klicken Sie auf **Erstellen**. Die neue Gutscheinseite wird im rechten Bereich angezeigt.

1. Öffnen Sie Ihre neue Gutscheinseite per Doppelklick und klicken Sie dann auf **Bearbeiten**, um die Informationen wie gewünscht zu konfigurieren.
1. Klicken Sie zum Speichern auf **OK**.

1. Jetzt können Sie Ihren Gutschein aktivieren, damit die Käufer ihn in der Veröffentlichungsinstanz in ihrem Warenkorb verwenden können.

### Entfernen von Gutscheinen {#removing-vouchers}

#### Entfernen von Gutscheinen: Klassische Benutzeroberfläche {#removing-vouchers-classic-ui}

Um einen Gutschein für Kunden nicht verfügbar zu machen, haben Sie folgende Möglichkeiten:

* Deaktivieren Sie den Gutschein - er bleibt in der Autorenumgebung verfügbar, damit Sie ihn später erneut aktivieren können.
* Löschen Sie sie vollständig.

Beide Aktionen können über die **Websites** Konsole.

### Gutscheine ändern {#modifying-vouchers}

#### Ändern von Gutscheinen: Klassische Benutzeroberfläche {#modifying-vouchers-classic-ui}

Um die Eigenschaften eines Gutscheins oder einer Promotion zu ändern, können Sie darauf doppelklicken auf **Websites** Konsole und klicken Sie auf **Bearbeiten**. Nach dem Speichern sollten Sie sie aktivieren, damit die Änderungen an die Veröffentlichungsinstanz(en) gesendet werden.

### Hinzufügen von Gutscheinen zu einem Warenkorb {#adding-vouchers-to-a-cart}

Damit Benutzer Gutscheine zu ihrem Warenkorb hinzufügen können, können Sie die integrierte **Gutscheine** -Komponente (Commerce-Kategorie). Fügen Sie diese Seite der Seite hinzu, auf der der Warenkorb angezeigt wird (dies ist jedoch nicht obligatorisch). Die Komponente &quot;Gutscheine&quot;ist lediglich ein Formular, in das der Benutzer einen Gutscheincode eingeben kann. Die Komponente &quot;Warenkorb&quot;zeigt tatsächlich die Liste der angewendeten Gutscheine und deren Rabatt an.

Auf der Demosite (Geometrixx Outdoors - Englisch) können Sie das Gutscheinformular auf der Warenkorbseite unter dem tatsächlichen Warenkorb sehen.

## Bestellungen {#orders}

>[!NOTE]
>
>Beachten Sie Folgendes: Vorkonfiguriert verfügt AEM nicht über Aktionen, die für standardmäßige Funktionen für Bestellungen erforderlich sind, z. B. Warenrückgabe, Aktualisierung des Bestellstatus, Bestellabwicklung, Generierung von Lieferscheinen. Der Hauptzweck ist die Technologievorschau.
>
>Die allgemeine Bestellverwaltung in AEM wurde bewusst einfach gehalten. Es hängt von der Strukturvorlage ab, welche Felder im Assistenten verfügbar sind:
>`/etc/scaffolding/geometrixx-outdoors/order/jcr:content/cq:dialog`
>
>Wenn Sie eine angepasste Grundlage erstellen, können Sie weitere Bestellinformationen speichern.

>[!NOTE]
>
>Die Auftragskonsole legt die Bestellinformationen des Anbieters offen, die nie veröffentlicht werden.
>
>Die Bestellinformationen der Kunden werden jeweils in ihren Home-Verzeichnissen vorgehalten und über den „Auftragsverlauf“ für ihr Konto verfügbar gemacht. Diese Informationen werden zusammen mit dem Rest des Basisverzeichnisses veröffentlicht.

### Bestellinformationen erstellen {#creating-order-information}

#### Erstellen von Bestellinformationen: Touch-optimierte Benutzeroberfläche {#creating-order-information-touch-optimized-ui}

1. Verwenden der **Bestellungen** -Konsole navigieren Sie zum gewünschten Speicherort.
1. Verwenden Sie die **Erstellen** Symbol zur Auswahl **Bestellung erstellen**.

   ![Plus-Symbol zum Erstellen](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. Der Assistent wird geöffnet. Verwenden Sie die Registerkarten **Allgemein**, **Inhalt**, **Zahlung** und **Erfüllung**, um die [Informationen zur neuen Bestellung](/help/commerce/cif-classic/administering/concepts.md#order-information) einzugeben.

1. Auswählen **Erstellen** um die Informationen zu speichern.

### Bearbeiten von Bestellinformationen {#editing-order-information}

#### Bearbeiten von Bestellinformationen - Touch-optimierte Benutzeroberfläche {#editing-order-information-touch-optimized-ui}

1. Navigieren Sie in der **Auftragskonsole** zur Bestellung.
1. Verwenden Sie entweder:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie die **Bestelldaten anzeigen** Symbol:

   ![Informationssymbol](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. Die [Bestellinformationen](/help/commerce/cif-classic/administering/concepts.md#order-information) angezeigt. Verwenden Sie die Optionen **Bearbeiten** und **Fertig**, um Änderungen vorzunehmen.

