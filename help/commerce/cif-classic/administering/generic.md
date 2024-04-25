---
title: Verwalten von generischem E-Commerce
description: Die generische AEM-Lösung verfügt über Methoden zum Verwalten der Commerce-Informationen, die im Repository gespeichert sind.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
docset: aem65
exl-id: c29f6213-1df6-45af-91c8-14b255276d82
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '2907'
ht-degree: 100%

---

# Verwalten von generischem E-Commerce {#administering-generic-ecommerce}

Die generische Lösung Adobe Experience Manager (AEM) bietet Methoden zum Verwalten der E-Commerce-Informationen, die im Repository gespeichert sind (im Gegensatz zur Verwendung einer externen E-Commerce-Engine). Hierzu gehört Folgendes:

* [Produkte](/help/commerce/cif-classic/administering/concepts.md#products)
* [Produktvarianten](/help/commerce/cif-classic/administering/concepts.md#product-variants)
* [Kataloge](/help/commerce/cif-classic/administering/concepts.md#catalogs)
* [Promotions](/help/commerce/cif-classic/administering/concepts.md#promotions)
* [Gutscheine](/help/commerce/cif-classic/administering/concepts.md#vouchers)
* [Bestellungen](/help/commerce/cif-classic/administering/concepts.md#shopping-cart-and-orders)
* [Proxyseiten](/help/commerce/cif-classic/administering/concepts.md#proxy-pages)

>[!NOTE]
>
>Die AEM-Standardinstallation umfasst die generische E-Commerce-Implementierung (JCR) von AEM.
>
>Diese ist für Demonstrationszwecke oder als Basis für eine benutzerdefinierte Implementierung gemäß Ihren Anforderungen gedacht.

## Produkte und Produktvarianten {#products-and-product-variations}

>[!NOTE]
>
>Die folgenden Verfahren gelten sowohl für Produkte als auch für Produktvarianten.

Definieren Sie eine [Strukturvorlage](/help/sites-authoring/scaffolding.md), bevor Sie Produkte erstellen. Hier werden die Felder festgelegt, die Sie definieren müssen, die Produkte und die Art und Weise, wie sie bearbeitet werden.

Für jeden Produkttyp ist eine separate Strukturvorlage erforderlich. Die Strukturvorlage ist einem Produkt jeweils wie folgt zugeordnet:

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
>Sie können eine Produktdefinition überall darunter erstellen, ohne dass ein zusätzliches Setup erforderlich ist.

### Importieren von Produkten {#importing-products}

#### Importieren von Produkten – Touch-optimierte Benutzeroberfläche {#importing-products-touch-optimized-ui}

1. Navigieren Sie zur **Produktekonsole** über die Option **Commerce**.
1. Navigieren Sie in der **Produktekonsole** zum gewünschten Ort.
1. Verwenden Sie das Symbol **Produkte importieren**, um den Assistenten zu öffnen.

   ![Symbol „Produkte importieren“](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. Geben Sie Folgendes an:

   * **Importtool**

     Das Import-Tool für den jeweiligen [E-Commerce-Anbieter](/help/commerce/cif-classic/administering/concepts.md#commerce-providers), (standardmäßig `Geometrixx`).

   * **Quelle**

     Die Datei, die importiert werden soll. Sie können den Browser verwenden, um eine Datei auszuwählen.

   * **Inkrementeller Import**

     Geben Sie an, ob dies ein inkrementeller Import ist (und kein vollständiger Import).

   >[!NOTE]
   >
   >Der inkrementelle Import (des Beispiel-Import-Tools „geometrixx-outdoors“) erfolgt auf Produktebene.
   >
   >Ein angepasstes Import-Tool kann so definiert werden, dass es wie gewünscht ausgeführt wird.

1. Wählen Sie **Weiter**, um die Produkte zu importieren. Es wird ein Protokoll mit den durchgeführten Aktionen angezeigt.

   >[!NOTE]
   >
   >Die Produkte werden zum aktuellen Speicherort oder relativ zum aktuellen Speicherort importiert.

   >[!NOTE]
   >
   >Wenn Sie **Weiter** und **Zurück** mehrfach verwenden, werden die Produktdefinitionen wiederholt importiert. Da diese aber über dieselben SKUs verfügen, werden die im Repository vorhandenen Informationen überschrieben.

1. Wählen Sie **Fertig**, um den Assistenten zu schließen.

#### Importieren von Produkten – klassische Benutzeroberfläche {#importing-products-classic-ui}

1. Verwenden Sie die **Tools**-Konsole, um den Ordner **Commerce** zu öffnen.
1. Doppelklicken Sie, um das **Produkt-Import-Tool** zu öffnen:

   ![Produkt-Importkonsole](/help/sites-administering/assets/chlimage_1-22.jpeg)

1. Geben Sie Folgendes an:

   * **Name speichern**

     Die Produkte werden nach folgenden Kriterien importiert:

     `/etc/commerce/products/<*store name*>/`

   * **E-Commerce-Anbieter**

     Das Import-Tool für Ihren [E-Commerce-Anbieter](/help/commerce/cif-classic/administering/concepts.md#commerce-providers) (standardmäßig „Geometrixx“).

   * **Quelldatei**

     Der Ort der zu importierenden Datei im Repository.

   * **Inkrementeller Import**

     Geben Sie an, ob dies ein inkrementeller Import ist (und kein vollständiger Import).

1. Klicken Sie auf **Produkte importieren**.

### Erstellen von Produktinformationen {#creating-product-information}

>[!NOTE]
>
>Die standardmäßige Produktverwaltung ist einfach aufgebaut, da dies auch für die Geometrixx-Outdoors-Produktgruppe gilt. Die Komplexität basiert auf der [Strukturvorlage](/help/sites-authoring/scaffolding.md) des Produkts. Indem Sie Ihre eigene Strukturvorlage für ein Produkt verwenden, können Sie also eine anspruchsvollere Bearbeitung erzielen.

#### Erstellen von Produktinformationen – Touch-optimierte Benutzeroberfläche {#creating-product-information-touch-optimized-ui}

1. Navigieren Sie in der **Produktekonsole** (über **Commerce**) zum gewünschten Speicherort.
1. Verwenden Sie das Symbol **Erstellen**, um eine der folgenden Optionen zu wählen (je nach Struktur und Ort):

   * **Produkt erstellen**
   * **Produktvariante erstellen**

   ![Plusförmiges Erstellungssymbol](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. Der Assistent wird geöffnet. Verwenden Sie die Registerkarten **Allgemein** und **Produkt**, um die [Produktattribute](/help/commerce/cif-classic/administering/concepts.md#product-attributes) für das neue Produkt bzw. die Produktvariante einzugeben.

   >[!NOTE]
   >
   >Für die Erstellung eines Produkts oder einer Variante sind mindestens Angaben für **Titel** und **SKU** erforderlich.

1. Wählen Sie **Erstellen** aus, um die Informationen zu speichern.

>[!NOTE]
>
>Viele Produkte werden in verschiedenen Farben und Größen angeboten. Informationen zum grundlegenden Produkt und zu den dazugehörigen Produktvarianten können über die **Produktekonsole** verwaltet werden.
>
>Produkte und ihre Varianten werden als Baumstruktur gespeichert. Die Produktinformationen befinden sich oben und die Varianten darunter (diese Struktur wird von der Benutzeroberfläche durchgesetzt).

### Bearbeiten von Produktinformationen {#editing-product-information}

>[!NOTE]
>
>Produktbilder werden für Geometrixx-outdoors vom folgenden Ort aus bereitgestellt:
>
>`/etc/commerce/products/...`
>
>Dies bedeutet, dass sie standardmäßig vom [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de) blockiert werden. Konfigurieren Sie dies also je nach Bedarf.

#### Bearbeiten von Produktinformationen – Touch-optimierte Benutzeroberfläche {#editing-product-information-touch-optimized-ui}

1. Navigieren Sie in der **Produktekonsole** (über **Commerce**) zu Ihren Produktinformationen.
1. Verwenden Sie:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie das Symbol **Produktdaten anzeigen**:

   ![Symbol „Produktdaten anzeigen“ – Informationssymbol](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. Die [Produktattribute](/help/commerce/cif-classic/administering/concepts.md#product-attributes) werden angezeigt. Verwenden Sie die Optionen **Bearbeiten** und **Fertig**, um Änderungen vorzunehmen.

### Anzeigen von Produktverweisen {#showing-product-references}

#### Anzeigen von Produktverweisen – Touch-optimierte Benutzeroberfläche {#showing-product-references-touch-optimized-ui}

1. Navigieren Sie in der **Produktekonsole** (über **Commerce**) zu Ihren Produktinformationen.
1. Öffnen Sie die sekundäre Leiste für „Verweise“ mit dem folgenden Symbol:

   ![Symbol mit Doppelpfeil](/help/sites-administering/do-not-localize/chlimage_1-16.png)

1. Wählen Sie Ihr erforderliches Produkt aus. Die sekundäre Leiste wird aktualisiert und zeigt Ihnen die verfügbaren Referenztypen an:

   ![Produktkonsole mit geöffneten Verweisen](/help/sites-administering/assets/chlimage_1-88.png)

1. Klicken Sie auf den Referenztyp (z. B. Produktseiten), um die Liste zu erweitern.
1. Wählen Sie eine spezifische Referenz aus, damit Sie die Optionen anzeigen können:

   * Zu Produktseite navigieren
   * Bearbeiten der Produktseite

   ![Verweisbedienfeld der Produktekonsole](/help/sites-administering/assets/chlimage_1-89.png)

### Nach Produkten suchen {#search-for-products}

1. Navigieren Sie zur **Produktekonsole**; nutzen Sie dazu die Option **Commerce**.
1. Öffnen Sie die sekundäre Leiste für „Suchen“ mit dem folgenden Symbol:

   ![Lupensymbol](/help/sites-administering/do-not-localize/chlimage_1-17.png)

1. Für die Suche nach Produkten stehen verschiedene Facetten zur Verfügung. Sie können für eine Suche eine oder mehrere Facetten verwenden. Die gefundenen Produkte werden angezeigt:

   ![Produktdaten in der Produktekonsole](/help/sites-administering/assets/chlimage_1-90.png)

1. Wenn Sie auf ein Produkt klicken/tippen, wird es geöffnet. Sie können es auch veröffentlichen oder die Produktdaten anzeigen.

#### Erweitern der Suche {#extending-search}

Sie können eine vorhandene Facette ändern oder neue hinzufügen, indem Sie CRXDE Lite verwenden:

1. Navigieren Sie zu:

   `http://localhost:4502/crx/de/index.jsp#/libs/commerce/gui/content/products/aside/items/search/items/searchpanel/facets`

1. Sie können z. B. die Größen, die auf der Produktsuchseite erscheinen, bearbeiten. Klicken Sie auf den Knoten `sizegroup`.
1. Klicken Sie auf den Knoten `items` und dann auf den Knoten `propertypredicate`.
1. Sie können `propertyValues` bearbeiten. Beispielsweise können Sie XS oder XXL hinzufügen oder eine Größe entfernen.
1. Klicken Sie auf **Alle speichern** und gehen Sie zur Seite für die Produktsuche. Ihre Änderungen sollten angezeigt werden.

### Mehrere Assets {#multiple-assets}

Sie können in der Produktkomponente mehrere Assets hinzufügen und dann das Asset angeben, das auf der Produktseite angezeigt werden soll.

>[!NOTE]
>
>Alles, was sich auf mehrere Assets bezieht, erfolgt über die Touch-optimierte Benutzeroberfläche.

#### Hinzufügen mehrerer Assets {#adding-multiple-assets}

1. Navigieren Sie zur **Produktekonsole**; nutzen Sie dazu die Option **Commerce**.
1. Navigieren Sie in der **Produktekonsole** zum gewünschten Produkt.

   >[!NOTE]
   >
   >Sie müssen sich auf der Produktebene befinden, nicht auf der Variantenebene.

1. Wählen Sie (per Auswahlmodus oder Schnellaktionen) das Symbol **Produktdaten anzeigen**.
1. Wählen Sie das Bearbeitungssymbol aus.
1. Scrollen Sie zu **Hinzufügen**.

   ![Screenshot zum Hinzufügen von Produktdaten](/help/sites-administering/assets/chlimage_1-91.png)

1. Klicken Sie auf **Hinzufügen**. Ein neuer Asset-Platzhalter wird angezeigt.
1. Wenn Sie **Ändern** wählen, öffnet sich ein Dialogfeld, in dem Sie ein Asset auswählen können.
1. Wählen Sie das Asset, das Sie hinzufügen möchten.

   >[!NOTE]
   >
   >Die Assets, die Sie auswählen können, stammen aus [Assets](/help/assets/assets.md).

1. Klicken Sie auf das Symbol „Fertig“.

Zwei Assets werden jetzt in Ihrer Produktkomponente gespeichert. Sie können konfigurieren, welches von ihnen auf der Produktseite angezeigt werden soll. Dies funktioniert mit einem Kategoriesystem. Zuerst müssen Sie den einzelnen Assets eine Kategorie hinzufügen:

1. Wählen Sie **Produktdaten anzeigen**.
1. Geben Sie unter den Assets eine **Asset-Kategorie** ein, z. B. `cat1` und `cat2`.

   >[!NOTE]
   >
   >Sie können auch Tags für Kategorien verwenden.

1. Klicken Sie auf das Symbol „Fertig“. Als Nächstes müssen Sie den [Rollout](#rolling-out-a-catalog) für Ihre Änderungen durchführen.

Jetzt verfügen Ihre Assets in der Produktkomponente über eine Kategorie. Sie können auf drei verschiedenen Ebenen festlegen, welche Kategorie angezeigt wird:

* [Produktseite](#product-page)
* [Katalog](#catalog)
* [Produktekonsole](#products-console)

>[!NOTE]
>
>Wenn Sie keine Kategorien festlegen, wird das erste Asset auf der Produktseite angezeigt.

Die Auswahl des anzuzeigenden Bildes erfolgt wie folgt:

1. Überprüfen Sie, ob eine Kategorie für die Produktseite festgelegt ist.
1. Wenn nicht, überprüfen Sie, ob für den Katalog eine Kategorie festgelegt ist.
1. Wenn nicht, überprüfen Sie, ob für die Produktekonsole eine Kategorie festgelegt ist.

>[!NOTE]
>
>Sowohl für die Katalogebene als auch für die Produktekonsole müssen Sie einen Rollout Ihrer Änderungen durchführen, um die Änderungen anzuwenden und den Unterschied auf der Produktseite zu sehen.

#### Produktseite {#product-page}

1. Navigieren Sie zu Ihrer Produktseite. 
1. **Bearbeiten** Sie die Produktkomponente.
1. Geben Sie die **Bildkategorie** ein, die Sie gewählt haben (z. B. `cat1`).
1. Klicken Sie auf **Fertig**. Die Seite wird aktualisiert und das richtige Asset sollte angezeigt werden.

#### Katalog  {#catalog}

1. Navigieren Sie zu Ihrem Katalog.
1. Wählen Sie **Eigenschaften anzeigen**.
1. Wählen Sie **Bearbeiten** aus.
1. Wählen Sie die Registerkarte **Assets**.
1. Geben Sie die gewünschte **Produkt-Asset-Kategorie** ein.
1. Wählen Sie **Fertig**.
1. Führen Sie für Ihre Änderungen den [Rollout](#rolling-out-a-catalog) durch.

#### Produktekonsole {#products-console}

1. Navigieren Sie in der **Produktekonsole** zum gewünschten Produkt.
1. Wählen Sie **Produktdaten anzeigen**.
1. Wählen Sie **Bearbeiten** aus.
1. Geben Sie eine **Standard-Asset-Kategorie** ein.
1. Wählen Sie **Fertig**.
1. Führen Sie für Ihre Änderungen den [Rollout](#rolling-out-a-catalog) durch.

### Veröffentlichen und Rückgängigmachen der Veröffentlichung von Produktinformationen {#publishing-unpublishing-product-information}

#### Veröffentlichen und Rückgängigmachen der Veröffentlichung von Produktinformationen – Touch-optimierte Benutzeroberfläche {#publishing-unpublishing-product-information-touch-optimized-ui}

>[!NOTE]
>
>Häufig werden die Produktinformationen über die Seiten veröffentlicht, die darauf verweisen. Wenn Sie zum Beispiel Seite X veröffentlichen, die auf Produkt Y verweist, fragt AEM, ob Sie auch Produkt Y veröffentlichen möchten.
>
>Für Sonderfälle unterstützt AEM auch die direkte Veröffentlichung aus den Produktdaten.

1. Navigieren Sie in der **Produktekonsole** (über **Commerce**) zu Ihren Produktinformationen.
1. Verwenden Sie:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie je nach Bedarf das Symbol **Veröffentlichen** oder **Veröffentlichung rückgängig machen**:

   ![Welt-Symbol](/help/sites-administering/do-not-localize/chlimage_1-18.png) ![Weltsymbol mit einem Kreuz – kein Zeichen](/help/sites-administering/do-not-localize/chlimage_1-19.png)

   Die Produktinformationen werden entsprechend veröffentlicht bzw. die Veröffentlichung wird rückgängig gemacht.

<!-- Search&Promote is end of life as of September 1, 2022 ### Product Feed {#product-feed} -->

<!-- Search&Promote is end of life as of September 1, 2022 The Search&Promote integration lets you: -->

<!-- Search&Promote is end of life as of September 1, 2022 * use the eCommerce API, independently of the underlying repository structure and commerce platform. -->
<!-- Search&Promote is end of life as of September 1, 2022 * use the Index Connector feature of Search&Promote to provide a product feed in XML format. -->
<!-- Search&Promote is end of life as of September 1, 2022 * use the Remote Control feature of Search&Promote to perform on-demand or scheduled requests of the product feed -->
<!-- Search&Promote is end of life as of September 1, 2022 * feed generation for different Search&Promote accounts, configured as cloud services configurations. -->

<!-- Search&Promote is end of life as of September 1, 2022 For more information, read [Product Feed](/help/sites-administering/product-feed.md). -->

### Ereignis-Handler für Produktaktualisierungen {#event-handler-for-product-updates}

Es gibt einen Ereignis-Handler, der ein Ereignis protokolliert, wenn ein Produkt hinzugefügt, bearbeitet oder gelöscht wird und wenn eine Produktseite hinzugefügt, bearbeitet oder gelöscht wird. Es gibt die folgenden OSGi-Ereignisse:

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

Die Komponente „Bild mit Links für Hinzufügen zum Warenkorb“ ermöglicht Ihnen das schnelle Hinzufügen eines Produkts zum Warenkorb, indem Sie einen Hotspot erstellen, der mit einem Produkt in einem Bild verknüpft ist.

Beim Klicken auf den Hotspot wird ein Dialogfeld geöffnet, in dem Sie die Größe und Menge für das Produkt auswählen können.

1. Navigieren Sie zu der Seite, auf der Sie die Komponente hinzufügen möchten.
1. Ziehen Sie die Komponente per Drag-and-Drop auf die Seite.
1. Ziehen Sie ein Bild aus dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser) per Drag-and-Drop und legen Sie es in der Komponente ab.
1. Wählen Sie eine der folgenden Möglichkeiten aus:

   * Klicken Sie auf die Komponente und dann auf das Symbol „Bearbeiten“.
   * Führen Sie einen langsamen Doppelklick durch.

1. Klicken Sie auf das Vollbildsymbol.

   ![Vollbildsymbol](/help/sites-administering/assets/chlimage_1-92.png)

1. Klicken Sie auf das Symbol „Karte starten“.

   ![Symbol „Karte starten“](/help/sites-administering/assets/chlimage_1-93.png)

1. Klicken Sie auf eines der Formsymbole.

   ![Formsymbole](/help/sites-administering/do-not-localize/chlimage_1-21.png)

1. Ändern und verschieben Sie die Form nach Bedarf.
1. Klicken Sie auf die Form.
1. Wenn Sie auf das Symbol „Durchsuchen“ klicken, wird die [Asset-Auswahl](/help/assets/search-assets.md#assetpicker) geöffnet.

   >[!NOTE]
   >
   >Alternativ hierzu können Sie den Produktpfad auch direkt eingeben. Dieser muss sich auf der Produktebene befinden, nicht auf der Variantenebene.

   ![Typenpfad](/help/sites-administering/assets/chlimage_1-94.png)

1. Klicken Sie zweimal auf das Symbol „Bestätigen“ und dann auf die Option zum Beenden des Vollbildmodus.
1. Klicken Sie auf eine beliebige Stelle auf der Seite neben der Komponente. Die Seite sollte aktualisiert werden und auf dem Bild sollte das folgende Symbol angezeigt werden:

   ![Pluszeichen](/help/sites-administering/do-not-localize/chlimage_1-22.png)

1. Wechseln Sie in den [Vorschaumodus](/help/sites-authoring/editing-content.md#previewingpagestouchoptimizedui).
1. Klicken Sie auf den Hotspot „+“ Ein Dialogfeld wird geöffnet, in dem Sie die Größe und Menge für das Produkt auswählen können, das Sie unter **Pfad** eingegeben haben.

   ![Produktbeispiel: Poncho](/help/sites-administering/assets/chlimage_1-95.png)

1. Geben Sie eine Größe und eine Menge ein.
1. Klicken Sie auf die Schaltfläche „Zum Warenkorb hinzufügen“. Das Dialogfeld wird geschlossen.
1. Navigieren Sie zu Ihrem Warenkorb. Das Produkt sollte sich hier befinden.

#### Konfigurationsoptionen {#configuration-options}

Sie können konfigurieren, wie das Dialogfeld aussieht, wenn Sie auf den Hotspot klicken:

1. Klicken Sie auf die Komponente und dann auf das Konfigurationssymbol.

   ![Konfigurationssymbol](/help/sites-administering/assets/chlimage_1-96.png)

1. Scrollen Sie nach unten. Die Registerkarte **ZUM WARENKORB HINZUFÜGEN** wird angezeigt.

   ![Zum Warenkorb hinzufügen](/help/sites-administering/assets/chlimage_1-97.png)

1. Klicken Sie auf **ZUM WARENKORB HINZUFÜGEN**. Sie können zwischen drei Konfigurationsoptionen wählen.

   ![Konfigurationsoptionen](/help/sites-administering/assets/chlimage_1-98.png)

1. Klicken Sie auf das Symbol „Fertig“.

## Kataloge {#catalogs}

### Generieren eines Katalogs {#generating-a-catalog}

#### Generieren eines Katalogs – Touch-optimierte Benutzeroberfläche {#generating-a-catalog-touch-optimized-ui}

>[!NOTE]
>
>Der Katalog verweist auf Ihre Produktdaten.

Generieren Sie wie folgt einen Katalog:

1. Öffnen Sie die Sites-Konsole (z. B. [http://localhost:4502/sites.html/content](http://localhost:4502/sites.html/content)).
1. Navigieren Sie dorthin, wo die neue Seite erstellt werden soll.
1. Um die Optionsliste zu öffnen, verwenden Sie das Symbol **Erstellen**:

   ![create-icon](/help/sites-administering/do-not-localize/chlimage_1-23.png)

1. Wählen Sie in der Liste **Katalog erstellen**. Der Assistent zum Erstellen von Katalogen wird geöffnet.

   ![Assistent zum Erstellen eines Katalogs](/help/sites-administering/assets/chlimage_1-99.png)

1. Navigieren Sie zum gewünschten Katalog-Blueprint.
1. Wählen Sie die Schaltfläche **Auswählen** und klicken Sie auf den gewünschten Katalog-Blueprint.
1. Wählen Sie **Weiter** aus.

   ![Assistent für Katalogeigenschaften](/help/sites-administering/assets/chlimage_1-100.png)

1. Geben Sie einen **Titel** und einen **Namen** ein.
1. Klicken Sie auf die Schaltfläche **Erstellen**. Der Katalog wird erstellt und ein Dialogfeld wird geöffnet.

   ![Dialogfeld „Katalog erstellt“](/help/sites-administering/assets/chlimage_1-101.png)

1. Wenn Sie auf die Schaltfläche **Fertig** klicken, gelangen Sie zurück zur Sites-Konsole, wo Sie Ihren Katalog finden können.

   Wenn Sie auf die Schaltfläche **Katalog öffnen** tippen oder klicken, wird Ihr Katalog geöffnet (z. B. `http://localhost:4502/editor.html/content/test-catalog.html`).

#### Generieren eines Katalogs – klassische Benutzeroberfläche {#generating-a-catalog-classic-ui}

>[!NOTE]
>
>Der Katalog verweist auf Ihre [Produktdaten](#products-and-product-variants).

1. Navigieren Sie über die **Websites-Konsole** zu Ihrem **Katalog-Blueprint** und dann zum Basiskatalog.

   Beispiel:

   `http://localhost:4502/siteadmin#/content/catalogs/geometrixx-outdoors/base-catalog`

1. Erstellen Sie mit der Vorlage **Bereichs-Blueprint** eine Seite.

   Zum Beispiel: `Swimwear`.

1. Öffnen Sie die neue Seite `Swimwear` und klicken Sie dann auf **Blueprint bearbeiten**. Das Dialogfeld **Eigenschaften** wird geöffnet, damit Sie die Auswahl der **Produkte** einrichten können.

   Öffnen Sie beispielsweise das Feld **Tags/Keywords**, um „Aktivität“ und im Bereich „Geometrixx-Outdoors“ dann „Swimming“ zu wählen.

1. Klicken Sie auf **OK**, damit Ihre Eigenschaften gespeichert werden. Beispielprodukte werden unter **Produktauswahlkriterien** auf der Blueprint-Seite angezeigt.
1. Klicken Sie auf **Rollout-Änderungen…**, wählen Sie **Rollout für Seite und alle Unterseiten**, klicken Sie dann auf **Weiter** und schließlich auf **Rollout**. Sobald der Rollout erfolgreich abgeschlossen ist, leuchtet die Anzeige **Status** grün.
1. Sie können jetzt auf **Schließen** klicken und den neuen Katalogbereich überprüfen, z. B. unter:

   `http://localhost:4502/cf#/content/geometrixx-outdoors/en/swimwear.html`

1. Klicken Sie ebenfalls auf der Blueprint-Seite auf **Blueprint bearbeiten** und öffnen Sie im Dialogfeld **Eigenschaften** die Registerkarte **Erzeugte Seite**. Wählen Sie im Banner-Listenfeld das Bild aus, das Sie anzeigen möchten, z. B. `summer.jpg`
1. Klicken Sie auf **OK**, damit Ihre Eigenschaften gespeichert werden. Die Bannerinformationen werden unter **Produktauswahlkriterien** auf der Blueprint-Seite angezeigt.
1. Führen Sie den Rollout für diese neuen Änderungen durch.

### Durchführen des Rollouts für einen Katalog {#rolling-out-a-catalog}

#### Durchführen des Rollouts für einen Katalog – Touch-optimierte Benutzeroberfläche {#rolling-out-a-catalog-touch-optimized-ui}

Führen Sie den Rollout für einen Katalog wie folgt durch:

1. Navigieren Sie über die Option **Commerce** zur **Katalogkonsole**.
1. Navigieren Sie zu dem Katalog, für den Sie den Rollout durchführen möchten.
1. Verwenden Sie:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie das Symbol **Rollout-Änderungen**:

   ![Rollout](/help/sites-administering/do-not-localize/chlimage_1-24.png)

1. Legen Sie im Assistenten den Rollout wie gewünscht fest und klicken Sie dann auf **Rollout-Änderungen**.
1. Ein Dialogfeld wird angezeigt. Wählen Sie **Fertig**, wenn der Vorgang abgeschlossen ist.

#### Durchführen des Rollouts für einen Katalog – klassische Benutzeroberfläche {#rolling-out-a-catalog-classic-ui}

Führen Sie den Rollout für einen Katalog wie folgt durch:

1. Navigieren Sie zu dem Katalog, für den Sie den Rollout durchführen möchten. Beispiel:

   `http://localhost:4502/cf#/content/catalogs/geometrixx-outdoors/base-catalog.html`

1. Klicken Sie auf **Rollout der Änderungen…**.
1. Legen Sie den Rollout nach Bedarf fest.
1. Klicken Sie auf **Rollout**.

### Blueprint-Importtool {#blueprint-importer}

#### Blueprint-Importtool – Touch-optimierte Benutzeroberfläche {#blueprint-importer-touch-optimized-ui}

1. Navigieren Sie über die Option **Commerce** zur **Katalogkonsole**.
1. Navigieren Sie zu dem Speicherort, an dem Sie den Katalog-Blueprint importieren möchten.
1. Wählen Sie das Symbol **Blueprints importieren**.

   ![Symbol „Blueprints importieren“](/help/sites-administering/do-not-localize/chlimage_1-13.png)

1. Wählen Sie im Assistenten die gewünschte Quelle aus und klicken Sie auf **Weiter**.

   ![Blueprint-Assistent](/help/sites-administering/assets/chlimage_1-102.png)

1. Wählen Sie **Fertig**, wenn der Import abgeschlossen ist.

#### Blueprint-Importtool – klassische Benutzeroberfläche {#blueprint-importer-classic-ui}

1. Navigieren Sie über die **Tools**-Konsole zu **Commerce**.

   Beispiel:

   `http://localhost:4502/miscadmin#/etc/commerce`

1. Öffnen Sie das **Katalog-Blueprint-Importtool**.
1. Legen Sie den Import wie gewünscht fest.
1. Klicken Sie auf **Katalog-Blueprints importieren**.

## Promotions {#promotions}

### Erstellen einer Promotion {#creating-a-promotion}

#### Erstellen einer Promotion – klassische Benutzeroberfläche {#creating-a-promotion-classic-ui}

>[!NOTE]
>
>Im folgenden Beispiel geht es um eine Promotion, die direkter Teil einer [Kampagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md) ist. Dies wird für Gutscheine verwendet.
>
>Eine Promotion kann innerhalb einer Kampagne auch Teil eines [Erlebnisses](/help/sites-authoring/personalization.md) sein.
>
>Weitere Informationen finden Sie unter [Promotions und Gutscheine](#promotions-and-vouchers).

1. Öffnen Sie die **Websites-Konsole** Ihrer Autoreninstanz.
1. Wählen Sie im linken Bereich die gewünschte **Kampagne** aus.
1. Klicken Sie auf **Neu**, wählen Sie die Vorlage **Promotion** und geben Sie dann einen **Titel** (und einen **Namen**, falls erforderlich) für Ihren neuen Gutschein an.
1. Klicken Sie auf **Erstellen**. Die neue Promotion-Seite wird im rechten Bereich angezeigt.

1. Bearbeiten Sie die **Eigenschaften**, indem Sie eine der folgenden Möglichkeiten wählen:

   * Öffnen Sie die Seite und klicken Sie dann auf die Schaltfläche „Bearbeiten“, um das Dialogfeld „Eigenschaften“ zu öffnen.
   * Wählen Sie die Seite in der Websites-Konsole aus, wählen Sie über das Kontextmenü (normalerweise mit der rechten Maustaste) die Option **Eigenschaften…** und öffnen Sie das Dialogfeld „Eigenschaften“.

   Geben Sie je nach Bedarf Werte für **Promotion-Typ**, **Rabatttyp**, **Rabattwert** und alle anderen gewünschten Felder an.

1. Klicken Sie zum Speichern auf **OK**.

1. Sie können Ihre Promotion jetzt aktivieren, damit sie für Käuferinnen und Käufer auf der Veröffentlichungsinstanz angezeigt wird.

## Gutscheine {#vouchers}

### Erstellen eines Gutscheins {#creating-a-voucher}

#### Erstellen eines Gutscheins – klassische Benutzeroberfläche {#creating-a-voucher-classic-ui}

1. Öffnen Sie die **Websites-Konsole** Ihrer Autoreninstanz.
1. Wählen Sie im linken Bereich die gewünschte **Kampagne** aus.
1. Klicken Sie auf **Neu**, wählen Sie die Vorlage **Gutschein** und geben Sie dann einen **Titel** (und einen **Namen**, falls erforderlich) für Ihren neuen Gutschein an.
1. Klicken Sie auf **Erstellen**. Die neue Gutscheinseite wird im rechten Bereich angezeigt.

1. Öffnen Sie Ihre neue Gutscheinseite mit einem Doppelklick, klicken Sie dann auf **Bearbeiten** und konfigurieren Sie die Informationen wie gewünscht.
1. Klicken Sie zum Speichern auf **OK**.

1. Jetzt können Sie Ihren Gutschein aktivieren, damit die Käuferinnen und Käufer ihn in der Publishing-Instanz in ihrem Warenkorb verwenden können.

### Entfernen von Gutscheinen {#removing-vouchers}

#### Entfernen von Gutscheinen – klassische Benutzeroberfläche {#removing-vouchers-classic-ui}

Sie haben folgende Möglichkeiten, wenn Sie einen Gutschein für Kundinnen oder Kunden unzugänglich machen möchten:

* Deaktivieren Sie den Gutschein. Er bleibt in der Autorenumgebung verfügbar, damit Sie ihn später erneut aktivieren können.
* Löschen Sie ihn vollständig.

Sie können beide Aktionen über die **Websites-Konsole** durchführen.

### Ändern von Gutscheinen {#modifying-vouchers}

#### Ändern von Gutscheinen – klassische Benutzeroberfläche {#modifying-vouchers-classic-ui}

Um die Eigenschaften eines Gutscheins oder eine Promotion zu ändern, können Sie auf der **Websites-Konsole** darauf doppelklicken und dann auf **Bearbeiten** klicken. Nach dem Speichern sollten Sie die Aktivierung durchführen, damit die Änderungen auf die Veröffentlichungsinstanzen übertragen werden.

### Hinzufügen von Gutscheinen zu einem Warenkorb {#adding-vouchers-to-a-cart}

Sie können die integrierte Komponente **Gutscheine** (Kategorie „Commerce“) verwenden, um für Benutzende das Hinzufügen von Gutscheinen zum Warenkorb zu ermöglichen. Fügen Sie dies auf der gleichen Seite ein, auf der auch der Warenkorb angezeigt wird (dies ist jedoch nicht zwingend erforderlich). Die Gutscheine-Komponente umfasst lediglich ein Formular, in das Benutzende einen Gutschein-Code eingeben können. Dabei ist es die Warenkorb-Komponente, in der die Liste mit den angewendeten Gutscheinen und den dazugehörigen Rabatten angezeigt wird.

Auf der Demosite (Geometrixx Outdoors – Englisch) können Sie das Gutscheinformular auf der Warenkorbseite unter dem tatsächlichen Warenkorb sehen.

## Bestellungen {#orders}

>[!NOTE]
>
>Beachten Sie Folgendes: Vorkonfiguriert verfügt AEM nicht über Aktionen, die für standardmäßige Funktionen für Bestellungen erforderlich sind, z. B. Warenrückgabe, Aktualisierung des Bestellstatus, Bestellabwicklung, Generierung von Lieferscheinen. Der Hauptzweck ist die Technologievorschau.
>
>Die allgemeine Bestellverwaltung in AEM wurde bewusst einfach gehalten. Es hängt von der Strukturvorlage ab, welche Felder im Assistenten verfügbar sind:
>`/etc/scaffolding/geometrixx-outdoors/order/jcr:content/cq:dialog`
>
>Wenn Sie eine angepasste Strukturvorlage erstellen, können Sie mehr Bestellinformationen speichern.

>[!NOTE]
>
>In der Auftragskonsole werden die Bestellinformationen des Anbieters verfügbar gemacht, die niemals veröffentlicht werden.
>
>Die Bestellinformationen der Kunden werden jeweils in ihren Home-Verzeichnissen vorgehalten und über den „Auftragsverlauf“ für ihr Konto verfügbar gemacht. Diese Informationen werden zusammen mit dem Rest des Basisverzeichnisses veröffentlicht.

### Erstellen von Bestellinformationen {#creating-order-information}

#### Erstellen von Bestellinformationen – Touch-optimierte Benutzeroberfläche {#creating-order-information-touch-optimized-ui}

1. Navigieren Sie in der **Auftragskonsole** zum gewünschten Ort.
1. Verwenden Sie das Symbol **Erstellen**, um die Option **Auftrag erstellen** auszuwählen.

   ![Plusförmiges Erstellungssymbol](/help/sites-administering/do-not-localize/chlimage_1-14.png)

1. Der Assistent wird geöffnet. Verwenden Sie die Registerkarten **Allgemein**, **Inhalt**, **Zahlung** und **Erfüllung**, um die [Informationen zur neuen Bestellung](/help/commerce/cif-classic/administering/concepts.md#order-information) einzugeben.

1. Wählen Sie **Erstellen** aus, um die Informationen zu speichern.

### Bearbeiten von Bestellinformationen {#editing-order-information}

#### Bearbeiten von Bestellinformationen – Touch-optimierte Benutzeroberfläche {#editing-order-information-touch-optimized-ui}

1. Navigieren Sie in der **Auftragskonsole** zur Bestellung.
1. Verwenden Sie:

   * [Schnellaktionen](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Auswahlmodus](/help/sites-authoring/basic-handling.md#navigating-and-selection-mode)

   Wählen Sie das Symbol **Auftragsdaten anzeigen**:

   ![Informationssymbol](/help/sites-administering/do-not-localize/chlimage_1-15.png)

1. Die [Bestellinformationen](/help/commerce/cif-classic/administering/concepts.md#order-information) werden angezeigt. Verwenden Sie die Optionen **Bearbeiten** und **Fertig**, um Änderungen vorzunehmen.

