---
title: Entwickeln des Bulk Editors
seo-title: Entwickeln des Bulk Editors
description: Tagging ermöglicht die Kategorisierung und Organisation von Inhalten
seo-description: Tagging ermöglicht die Kategorisierung und Organisation von Inhalten.
uuid: 3cd04c52-5bdb-47f6-9fa3-d7a4937e8e20
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: e9a1ff95-e88e-41f0-9731-9a59159b4653
exl-id: 8753aaab-959f-459b-bdb6-057cbe05d480
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1849'
ht-degree: 65%

---

# Entwickeln des Bulk Editors{#developing-the-bulk-editor}

In diesem Abschnitt wird erläutert, wie Sie das Bulk Editor-Tool entwickeln und die Produktlisten-Komponente erweitern, die auf dem Bulk Editor basiert.

## Abfrageparameter für den Bulk Editor  {#bulk-editor-query-parameters}

Wenn Sie den Bulk Editor verwenden, können Sie einige Abfrageparameter zur URL hinzufügen, um den Bulk Editor mit einer bestimmten Konfiguration aufzurufen. Wenn Sie den Bulk Editor immer mit einer bestimmten Konfiguration nutzen möchten, beispielsweise in der Produktlisten-Komponente, müssen Sie die Datei bulkeditor.jsp (zu finden unter /libs/wcm/core/components/bulkeditor) ändern oder eine Komponente mit der spezifischen Konfiguration erstellen. Änderungen, die über Abfrageparameter erfolgen, sind nicht dauerhaft.

Wenn Sie zum Beispiel folgende URL in den Browser eingeben:

`https://<servername><port_number>/etc/importers/bulkeditor.html?rootPath=/content/geometrixx/en&queryParams=geometrixx&initialSearch=true&hrp=true`

wird der Bulk Editor ohne das Feld **Stammverzeichnis** angezeigt, da „hrp=true“ dieses Feld ausblendet. Mit dem Parameter „hrp=false“ (Standardwert) wird das Feld angezeigt.

Nachstehend finden Sie eine Liste der Abfrageparameter für den Bulk Editor:

>[!NOTE]
>
>Jeder Parameter kann einen langen und einen kurzen Namen haben. Der lange Name für die Suche nach dem Stammverzeichnis ist z. B. `rootPath`, der kurze `rp`. Wenn der lange Name nicht definiert ist, wird der kurze aus der Anfrage ausgelesen.

<table>
 <tbody>
  <tr>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p> Parameter</p> <p>(Langname/Kurzname)<br /> </p> </td>
   <td> Typ <br /> </td>
   <td> Beschreibung <br /> </td>
  </tr>
  <tr>
   <td> rootPath / rp<br /> </td>
   <td> Zeichenfolge </td>
   <td> Suchstammpfad</td>
  </tr>
  <tr>
   <td> queryParams / qp<br /> </td>
   <td> Zeichenfolge</td>
   <td> Suchabfrage</td>
  </tr>
  <tr>
   <td> contentMode / cm<br /> </td>
   <td> Boolesch</td>
   <td> Wenn "true", wird der Inhaltsmodus aktiviert<br /> </td>
  </tr>
  <tr>
   <td> colsValue / cv<br /> </td>
   <td> Zeichenfolge[]</td>
   <td> durchsuchte Eigenschaften (angekreuzte Werte aus colsSelection werden als Kontrollkästchen angezeigt)</td>
  </tr>
  <tr>
   <td> extraCols / ec<br /> </td>
   <td> Zeichenfolge[]</td>
   <td> extra durchsuchte Eigenschaften (in einem kommagetrennten Textfeld angezeigt)</td>
  </tr>
  <tr>
   <td> initialSearch / is<br /> </td>
   <td> Boolesch</td>
   <td> Wenn "true", wird die Abfrage beim Laden der Seite ausgeführt<br /> </td>
  </tr>
  <tr>
   <td> colsSelection / cs<br /> </td>
   <td> Zeichenfolge[]</td>
   <td> Auswahl durchsuchter Eigenschaften (angezeigt als Kontrollkästchen)</td>
  </tr>
  <tr>
   <td> showGridOnly / sgo<br /> </td>
   <td> Boolesch</td>
   <td> wenn "true", zeigt nur das Raster und nicht das Suchfeld <br /> an </td>
  </tr>
  <tr>
   <td> searchPanelCollapsed/spc</td>
   <td> Boolesch</td>
   <td> Wenn "true", wird das Suchfeld beim Laden reduziert</td>
  </tr>
  <tr>
   <td> hideRootPath / hrp</td>
   <td> Boolesch</td>
   <td> Wenn "true", blendet das Stammpfadfeld aus</td>
  </tr>
  <tr>
   <td> hideQueryParams/hqp</td>
   <td> Boolesch</td>
   <td> wenn "true", blendet das Abfragefeld aus</td>
  </tr>
  <tr>
   <td> hideContentMode/hcm</td>
   <td> Boolesch</td>
   <td> Wenn "true", wird das Feld für den Inhaltsmodus ausgeblendet</td>
  </tr>
  <tr>
   <td> hideColsSelection/hcs</td>
   <td> Boolesch</td>
   <td> blendet, wenn "true", das Spaltenauswahlfeld aus</td>
  </tr>
  <tr>
   <td> hideExtraCols / hec</td>
   <td> Boolesch</td>
   <td> Wenn "true", wird das zusätzliche Spaltenfeld ausgeblendet</td>
  </tr>
  <tr>
   <td> hideSearchButton</td>
   <td> Boolesch</td>
   <td> Wenn "true", wird die Suchschaltfläche ausgeblendet.</td>
  </tr>
  <tr>
   <td> hideSaveButton/savep</td>
   <td> Boolesch</td>
   <td> Wenn "true", wird die Schaltfläche "Speichern"ausgeblendet</td>
  </tr>
  <tr>
   <td> hideExportButton/hexpb</td>
   <td> Boolesch</td>
   <td> Wenn "true", wird die Export-Schaltfläche ausgeblendet</td>
  </tr>
  <tr>
   <td> hideImportButton/hib</td>
   <td> Boolesch</td>
   <td> blendet bei "true"die Importschaltfläche aus</td>
  </tr>
  <tr>
   <td> hideResultNumber / hrn</td>
   <td> Boolesch</td>
   <td> Wenn "true", blendet den Text der Rastersuchergebnisnummer aus.</td>
  </tr>
  <tr>
   <td> hideInsertButton/hinsertb</td>
   <td> Boolesch</td>
   <td> blendet bei "true"die Rastereinfüge-Schaltfläche aus</td>
  </tr>
  <tr>
   <td> hideDeleteButton/hdelb</td>
   <td> Boolesch</td>
   <td> Wenn "true", wird die Schaltfläche zum Löschen des Rasters ausgeblendet</td>
  </tr>
  <tr>
   <td> hidePathCol/hpc</td>
   <td> Boolesch</td>
   <td> blendet bei "true"die Spalte "path"des Rasters aus</td>
  </tr>
 </tbody>
</table>

### Entwickeln einer auf dem Bulk Editor basierenden Komponente: der Produktlisten-Komponente {#developing-a-bulk-editor-based-component-the-product-list-component}

In diesem Abschnitt finden Sie einen Überblick über die Verwendung des Bulk Editors und eine Beschreibung der vorhandenen Geometrixx-Komponente, die auf dem Bulk Editor basiert: der Produktlisten-Komponente.

Mit der Produktlisten-Komponente können Benutzer eine Tabelle mit Daten anzeigen und bearbeiten. Sie können beispielsweise mit der Produktlisten-Komponente Produkte in einem Katalog darstellen. Die Daten werden in einer standardmäßigen HTML-Tabelle angezeigt. Die Bearbeitung erfolgt über das Dialogfeld **Bearbeiten**, das ein Bulk Editor-Widget enthält. (Es handelt sich hierbei um denselben Bulk Editor, auf den Sie auch unter /etc/importers/bulkeditor.html oder über das Menü „Tools“ zugreifen können.) Die Produktlisten-Komponente wurde für eine spezifische, eingeschränkte Bulk Editor-Funktionalität konfiguriert. Alle Teile des Bulk Editors (oder Komponenten, die vom Bulk Editor abgeleitet werden) können konfiguriert werden.

Mit dem Bulk Editor können Sie Zeilen hinzufügen, ändern, löschen, filtern und exportieren, Änderungen speichern und einen Satz an Zeilen importieren. Jede Zeile wird als Knoten unter der Instanz der Produktlisten-Komponente gespeichert. Jede Zelle ist eine Eigenschaft eines jeden Knotens. Dies wurde bei der Entwicklung festgelegt und kann leicht geändert werden. Sie können Knoten beispielsweise auch an anderer Stelle im Repository speichern. Die Aufgabe des Abfrage-Servlets besteht darin, eine Liste der anzuzeigenden Knoten zurückzugeben; der Suchpfad ist als Produktliste-Instanz definiert.

Der Quellcode der Produktlisten-Komponente ist im Repository unter /apps/geometrixx/components/productlist verfügbar und besteht aus mehreren Teilen wie allen AEM Komponenten:

* HTML-Rendering: Das Rendering erfolgt in einer JSP-Datei (/apps/geometrixx/components/productlist/productlist.jsp). Die JSP-Datei liest die untergeordneten Knoten der aktuellen Produktlisten-Komponente und zeigt jeden dieser Knoten als Zeile einer HTML-Tabelle an.
* Dialogfeld „Bearbeiten“: Hier definieren Sie die Bulk Editor-Konfiguration. Passen Sie das Dialogfeld an die Anforderungen der Komponente an: verfügbare Spalten und mögliche Aktionen, die beim Raster oder bei der Suche ausgeführt werden sollen. Informationen zu allen Konfigurationseigenschaften finden Sie unter [Konfigurationseigenschaften des Bulk Editors](#bulk-editor-configuration-properties).

Hier sehen Sie eine XML-Darstellung der untergeordneten Knoten des Dialogfelds:

```xml
        <editor
            jcr:primaryType="cq:Widget"
            colsSelection="[ProductId,ProductName,Color,CatalogCode,SellingSku]"
            colsValue="[ProductId,ProductName,Color,CatalogCode,SellingSku]"
            contentMode="false"
            exportURL="/etc/importers/bulkeditor/export.tsv"
            extraCols="Selection"
            hideColsSelection="false"
            hideContentMode="true"
            hideDeleteButton="false"
            hideExportButton="false"
            hideExtraCols="true"
            hideImportButton="false"
            hideInsertButton="false"
            hideMoveButtons="false"
            hidePathCol="true"
            hideRootPath="true"
            hideSaveButton="false"
            hideSearchButton="false"
            importURL="/etc/importers/bulkeditor/import"
            initialSearch="true"
            insertedResourceType="geometrixx/components/productlist/sku"
            queryParams=""
            queryURL="/etc/importers/bulkeditor/query.json"
            saveURL="/etc/importers/bulkeditor/save"
            xtype="bulkeditor">
            <saveButton
                jcr:primaryType="nt:unstructured"
                text="Save modifications"/>
            <searchButton
                jcr:primaryType="nt:unstructured"
                text="Apply filter"/>
            <queryParamsInput
                jcr:primaryType="nt:unstructured"
                fieldDescription="Enter here your filters"
                fieldLabel="Filters"/>
            <searchPanel
                jcr:primaryType="nt:unstructured"
                height="200">
                <defaults
                    jcr:primaryType="nt:unstructured"
                    labelWidth="150"/>
            </searchPanel>
            <grid
                jcr:primaryType="nt:unstructured"
                height="275"/>
            <store jcr:primaryType="nt:unstructured">
                <sortInfo
                    jcr:primaryType="nt:unstructured"
                    direction="ASC"
                    field="CatalogCode"/>
            </store>
            <colModel
                jcr:primaryType="nt:unstructured"
                width="150"/>
            <colsMetadata jcr:primaryType="nt:unstructured">
                <Selection
                    jcr:primaryType="nt:unstructured"
                    checkbox="true"
                    forcedPosition="0"
                    headerText=""/>
                <ProductId
                    jcr:primaryType="nt:unstructured"
                    cellCls="productlist-cell-productid"
                    headerText="Product Id"/>
                <ProductName
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #FFCC99;"
                    headerText="Product Name"/>
                <CatalogCode
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #EDEDED;"
                    headerText="Catalog Code"/>
                <Color jcr:primaryType="nt:unstructured">
                    <editor
                        jcr:primaryType="nt:unstructured"
                        store="[Blue,Red,Yellow]"
                        triggerAction="all"
                        typeAhead="true"
                        xtype="combo"/>
                </Color>
                <SellingSku
                    jcr:primaryType="nt:unstructured"
                    headerText="Sku Id"/>
            </colsMetadata>
        </editor>
```

### Konfigurationseigenschaften des Bulk Editors  {#bulk-editor-configuration-properties}

Jeder Teil des Bulk Editors kann konfiguriert werden. In der folgenden Tabelle sind alle Konfigurationseigenschaften für den Bulk Editor aufgeführt.

<table>
 <tbody>
  <tr>
   <td>Eigenschaftsname</td>
   <td>Definition</td>
  </tr>
  <tr>
   <td>rootPath</td>
   <td>Suchstammpfad</td>
  </tr>
  <tr>
   <td>queryParams</td>
   <td>Suchanfrage</td>
  </tr>
  <tr>
   <td>contentMode</td>
   <td>True zum Aktivieren des Inhaltsmodus: Eigenschaften werden auf dem Knoten jcr:content und nicht im Suchergebnisknoten gelesen</td>
  </tr>
  <tr>
   <td>colsValue</td>
   <td>Durchsuchte Eigenschaften (angekreuzte Werte aus colsSelection werden als Kontrollkästchen angezeigt)</td>
  </tr>
  <tr>
   <td>extraCols</td>
   <td>Zusätzliche durchsuchte Eigenschaften (in einem Textfeld durch Kommas getrennt angezeigt)</td>
  </tr>
  <tr>
   <td>initialSearch</td>
   <td>True zum Ausführen einer Abfrage beim Laden der Seite</td>
  </tr>
  <tr>
   <td>colsSelection</td>
   <td>Auswahl der durchsuchten Eigenschaften (angezeigt als Kontrollkästchen)</td>
  </tr>
  <tr>
   <td>showGridOnly</td>
   <td>True , um nur das Raster und nicht das Suchfeld anzuzeigen (vergessen Sie nicht, initialSearch auf "true"festzulegen)</td>
  </tr>
  <tr>
   <td>searchPanelCollapsed</td>
   <td>"True"zum standardmäßigen Reduzieren des Suchfelds</td>
  </tr>
  <tr>
   <td>hideRootPath</td>
   <td>Feld für Stammpfad ausblenden</td>
  </tr>
  <tr>
   <td>hideQueryParams</td>
   <td>Abfragefeld ausblenden</td>
  </tr>
  <tr>
   <td>hideContentMode</td>
   <td>Feld für Inhaltsmodus ausblenden</td>
  </tr>
  <tr>
   <td>hideColsSelection</td>
   <td>Auswahlfeld "Protokolle ausblenden"</td>
  </tr>
  <tr>
   <td>hideExtraCols</td>
   <td>Feld "Zusätzliche Protokolle ausblenden"</td>
  </tr>
  <tr>
   <td>hideSearchButton</td>
   <td>Schaltfläche "Suche ausblenden"</td>
  </tr>
  <tr>
   <td>hideSaveButton</td>
   <td>Schaltfläche "Speichern ausblenden"</td>
  </tr>
  <tr>
   <td>hideExportButton</td>
   <td>Schaltfläche "Export ausblenden"</td>
  </tr>
  <tr>
   <td>hideImportButton</td>
   <td>Schaltfläche "Import ausblenden"</td>
  </tr>
  <tr>
   <td>hideResultNumber</td>
   <td>Text der Rastersuchergebnisnummer ausblenden</td>
  </tr>
  <tr>
   <td>hideInsertButton</td>
   <td>Schaltfläche zum Ausblenden des Rastereinfügens</td>
  </tr>
  <tr>
   <td>hideDeleteButton</td>
   <td>Schaltfläche zum Löschen eines Rasters ausblenden</td>
  </tr>
  <tr>
   <td>hidePathCol</td>
   <td>Rasterspalte "Pfad"ausblenden</td>
  </tr>
  <tr>
   <td>queryURL</td>
   <td>Pfad zum Abfrage-Servlet</td>
  </tr>
  <tr>
   <td>exportURL</td>
   <td>Pfad zum Exportieren des Servlets</td>
  </tr>
  <tr>
   <td>importURL</td>
   <td>Pfad zum Importieren des Servlets</td>
  </tr>
  <tr>
   <td>addedResourceType</td>
   <td>Ressourcentyp, der dem Knoten hinzugefügt wird, wenn eine Zeile eingefügt wird</td>
  </tr>
  <tr>
   <td>saveButton</td>
   <td>Schaltfläche speichern Widget-Konfiguration</td>
  </tr>
  <tr>
   <td>searchButton</td>
   <td>Widget-Konfiguration für Suchschaltflächen</td>
  </tr>
  <tr>
   <td>exportButton</td>
   <td>Konfigurieren des Widgets "Schaltfläche exportieren"</td>
  </tr>
  <tr>
   <td>importButton</td>
   <td>Konfigurieren des Widgets "Schaltfläche importieren"</td>
  </tr>
  <tr>
   <td>searchPanel</td>
   <td>Widget-Konfiguration des Suchbereichs</td>
  </tr>
  <tr>
   <td>grid</td>
   <td>Widget-Konfiguration für Raster</td>
  </tr>
  <tr>
   <td>store</td>
   <td>Store config</td>
  </tr>
  <tr>
   <td>colModel</td>
   <td>Konfiguration des Rasterspaltenmodells</td>
  </tr>
  <tr>
   <td>rootPathInput</td>
   <td>rootPath widget config</td>
  </tr>
  <tr>
   <td>queryParamsInput</td>
   <td>queryParams-Widget config</td>
  </tr>
  <tr>
   <td>contentModeInput</td>
   <td>contentMode-Widget-Konfiguration</td>
  </tr>
  <tr>
   <td>colsSelectionInput</td>
   <td>colsSelection-Widget config</td>
  </tr>
  <tr>
   <td>extraColsInput</td>
   <td>extraCols-Widget-Konfiguration</td>
  </tr>
  <tr>
   <td>colsMetadata</td>
   <td>Konfiguration der Spaltenmetadaten. Mögliche Eigenschaften sind (werden auf alle Zellen der Spalte angewendet): <br />
    <ul>
     <li>cellStyle: HTML-Stil </li>
     <li>cellCls: css-Klasse </li>
     <li>readOnly: true , um Wert nicht ändern zu können </li>
     <li>Kontrollkästchen: true , um alle Zellen der Spalte als Kontrollkästchen zu definieren (true/false-Werte) </li>
     <li>forcedPosition: Ganzzahlwert, um anzugeben, wo die Spalte im Raster platziert werden soll (zwischen 0 und der Anzahl der Spalten-1)<p><br /> </p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Konfigurieren der Spalten-Metadaten {#columns-metadata-configuration}

Sie können für jede Spalte Folgendes konfigurieren:

* Anzeige-Eigenschaften: HTML-Stil, CSS-Klasse und Schreibschutz

* ein Kontrollkästchen
* eine erzwungene Position

CSS und schreibgeschützte Spalten

Der Bulk Editor verfügt über drei Spaltenkonfigurationen:

* Klassenname des Zellen-CSS (cellCls): ein CSS-Klassenname, der zu jeder Zelle der konfigurierten Spalte hinzugefügt wird
* Zellen-Stil (cellStyle): ein HTML-Stil, der zu jeder Zelle der konfigurierten Spalte hinzugefügt wird
* Schreibschutz (readOnly): Jede Zelle der konfigurierten Spalte wird als schreibgeschützt festgelegt.

Die Konfiguration muss wie die folgende definiert werden:

```
"colsMetadata": {
"Column name": {
     "cellStyle": "html style",
     "cellCls": "CSS class",
     "readOnly": true/false
}
}
```

Das folgende Beispiel findet sich in der Produktlisten-Komponente (/apps/geometrixx/components/productlist/dialog/items/editor/colsMetadata):

```xml
            <colsMetadata jcr:primaryType="nt:unstructured">
                <Selection
                    jcr:primaryType="nt:unstructured"
                    checkbox="true"
                    forcedPosition="0"
                    headerText=""/>
                <ProductId
                    jcr:primaryType="nt:unstructured"
                    cellCls="productlist-cell-productid"
                    headerText="Product Id"/>
                <ProductName
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #FFCC99;"
                    headerText="Product Name"/>
                <CatalogCode
                    jcr:primaryType="nt:unstructured"
                    cellStyle="background-color: #EDEDED;"
                    headerText="Catalog Code"/>
                <Color jcr:primaryType="nt:unstructured">
                    <editor
                        jcr:primaryType="nt:unstructured"
                        store="[Blue,Red,Yellow]"
                        triggerAction="all"
                        typeAhead="true"
                        xtype="combo"/>
                </Color>
                <SellingSku
                    jcr:primaryType="nt:unstructured"
                    headerText="Sku Id"/>
            </colsMetadata>
```

**Kontrollkästchen**

Wenn die Konfigurationseigenschaft „Checkbox“ auf „true“ festgelegt ist, werden alle Zellen der Spalte als Kontrollkästchen gerendert. Ein aktiviertes Kontrollkästchen sendet **true** an das Servlet „Speichern“ des Servers, ein nicht aktiviertes sendet **false**. Im Header-Menü können Sie auch **alle auswählen** oder **keines auswählen**. Diese Optionen sind aktiviert, wenn der ausgewählte Header der Header einer Kontrollkästchenspalte ist.

Im vorhergehenden Beispiel enthält die Auswahlspalte nur Kontrollkästchen mit der Eigenschaft checkbox=&quot;true&quot;.

**Erzwungene Position**

Mit forcedPosition, den Metadaten für die erzwungene Position, können Sie festlegen, an welcher Stelle im Raster die Spalte platziert werden soll: 0 ist die erste Position und &lt;Anzahl an Spalten> – 1 ist die letzte Position. Alle anderen Werte werden ignoriert.

Im vorhergehenden Beispiel ist die Auswahlspalte die erste Spalte mit forcedPosition = &quot;0&quot;.

### Abfrage-Servlet  {#query-servlet}

Standardmäßig befindet sich das Abfrage-Servlet unter `/libs/wcm/core/components/bulkeditor/json.java`. Sie können einen anderen Pfad konfigurieren, um die Daten abzurufen.

Das Abfrage-Servlet funktioniert wie folgt: Es erhält eine GQL-Abfrage und die zurückzugebenden Spalten, berechnet die Ergebnisse und sendet sie als JSON-Stream zurück an den Bulk Editor.

Im Fall der Produktlisten-Komponente werden zwei Parameter wie folgt an das Abfrage-Servlet gesendet:

* query: &quot;path:/content/geometrixx/en/customers/jcr:content/par/productlist Cube&quot;
* cols: &quot;Selection,ProductId,ProductName,Color,CatalogCode,SellingSku&quot;

und der folgende JSON-Stream wird zurückgegeben:

```
{
  "hits": [{
      "jcr:path": "/content/geometrixx/en/products/jcr:content/par/productlist/1258674828905",
      "ProductId": "21",
      "ProductName": "Cube",
      "Color": "Blue",
      "CatalogCode": "43244",
      "SellingSku": "32131"
    }
  ],
  "results": 1
}
```

Jeder Treffer entspricht einem Knoten und seinen Eigenschaften und wird als Zeile im Raster angezeigt.

Sie können das Abfrage-Servlet erweitern, sodass es ein komplexes Vererbungsmodell oder Knoten zurückgibt, die an einem bestimmten logischen Ort gespeichert sind. Mit dem Abfrage-Servlet können Sie alle Arten an komplexen Berechnungen durchführen. Das Raster kann daraufhin Zeilen anzeigen, die ein Aggregat mehrerer Knoten im Repository sind. Die Änderung und das Speichern dieser Zeilen werden in diesem Fall vom Speichern-Servlet verwaltet.

### Speichern-Servlet {#save-servlet}

In der Standardkonfiguration des Bulk Editors ist jede Zeile ein Knoten und der Pfad dieses Knotens wird im Zeilendatensatz gespeichert. Der Bulk Editor behält die Verbindung zwischen der Zeile und dem Knoten über den JCR-Pfad bei. Wenn ein Benutzer das Raster bearbeitet, wird eine Liste aller Änderungen erstellt. Klickt ein Benutzer auf **Speichern**, wird eine POST-Abfrage mit den aktualisierten Eigenschaftswerten an jeden Pfad gesendet. Dies ist die Grundlage des Sling-Konzepts. Es funktioniert problemlos, wenn jede Zelle eine Eigenschaft des Knotens ist. Wenn das Abfrage-Servlet dagegen zur Berechnung von Vererbungen implementiert wurde, kann dieses Modell nicht funktionieren, da eine vom Abfrage-Servlet zurückgegebene Eigenschaft von einem anderen Knoten geerbt werden kann.

Beim Speichern-Servlet werden die Änderungen nicht direkt an jeden Knoten übermittelt, sondern an ein Servlet, das die Aufgabe des Speicherns übernimmt. Auf diese Weise kann dieses Servlet die Änderungen analysieren und die Eigenschaften auf dem richtigen Knoten speichern.

Jede aktualisierte Eigenschaft wird im folgenden Format an das Servlet gesendet:

* Parametername: &lt;jcr path>/&lt;property name>

   Beispiel: /content/geometrixx/en/products/jcr:content/par/productlist/1258674859000/SellingSku

* Wert: &lt;Wert>

   Beispiel: 12123

Das Servlet muss wissen, wo die Eigenschaft catalogCode gespeichert ist.

Eine standardmäßige Save-Servlet-Implementierung ist unter /libs/wcm/bulkeditor/save/POST.jsp verfügbar und wird in der Produktlisten-Komponente verwendet. Es nimmt alle Parameter aus der Anfrage (mit dem Format &lt;jcr path>/&lt;property name> ) und schreibt Eigenschaften mithilfe der JCR-API auf Knoten. Außerdem erstellt das Servlet Knoten, wenn sie nicht vorhanden sind (in das Raster eingefügte Zeilen).

Der Standardcode sollte nicht so verwendet werden, wie es ist, da er das, was der Server nativ tut (eine POST auf &lt;jcr path>/&lt;property name>), neu implementiert und daher nur ein guter Ausgangspunkt für die Erstellung eines Save-Servlets ist, das ein Eigenschaftsvererbungsmodell verwaltet.
