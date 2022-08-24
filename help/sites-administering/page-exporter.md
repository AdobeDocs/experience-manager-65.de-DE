---
title: Das Seiten-Exporttool
description: Erfahren Sie, wie Sie das AEM-Seiten-Exporttool verwenden.
exl-id: 15d08758-cf75-43c0-9818-98a579d64183
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 28%

---

# Das Seiten-Exporttool{#the-page-exporter}

AEM ermöglicht den Export einer Seite als vollständige Webseite mit Bildern, `.js` und `.css` Dateien.

Nach der Konfiguration fordern Sie einen Seitenexport über Ihren Browser an, indem Sie `html` mit `export.zip` in der URL. Dadurch wird eine Archivdatei (ZIP) generiert, die die gerenderte Seite im HTML-Format zusammen mit den referenzierten Assets enthält. Alle Pfade auf der Seite (z. B. Pfade zu Bildern) werden umgeschrieben, um entweder auf die im Archiv enthaltenen Dateien oder auf die Ressourcen auf dem Server zu verweisen. Die Archivdatei (zip) kann dann von Ihrem Browser heruntergeladen werden.

>[!NOTE]
>
>Abhängig von Ihrem Browser und den Einstellungen wird der Download wie folgt ausgeführt:
>* eine Archivdatei (`<page-name>.export.zip`)
>* ein Ordner (`<page-name>`); effektiv die Archivdatei wurde bereits erweitert


## Exportieren einer Seite {#exporting-a-page}

In den folgenden Schritten wird beschrieben, wie Sie eine Seite exportieren und davon ausgehen, dass für Ihre Site eine Exportvorlage vorhanden ist. Eine Exportvorlage definiert die Art und Weise, wie eine Seite exportiert wird, und ist spezifisch für Ihre Site. Informationen zum Erstellen einer Exportvorlage finden Sie im Abschnitt [Erstellen einer Seiten-Exporter-Konfiguration für Ihre Site](#creating-a-page-exporter-configuration-for-your-site) Abschnitt.

So exportieren Sie eine Seite:

1. Navigieren Sie zur gewünschten Seite im **Sites** Konsole.

1. Wählen Sie die Seite aus und öffnen Sie dann die **Eigenschaften** angezeigt.

1. Wählen Sie die Registerkarte **Erweitert**.

1. Erweitern Sie die **Export** -Feld, um eine Exportvorlage auszuwählen.
Wählen Sie die erforderliche Vorlage für Ihre Site aus und bestätigen Sie dann mit **OK**.

1. Auswählen **Speichern und schließen** , um das Dialogfeld &quot;Seiteneigenschaften&quot;zu schließen.

1. Anfordern der Seite zum Exportieren, Ersetzen des Suffix `html` mit `export.zip` in der URL.

   Beispiel:
   * localhost:4502/content/we-retail/language-masters/en.html

   Der Zugriff erfolgt über:
   * localhost:4502/content/we-retail/language-masters/en.export.zip


1. Laden Sie die Archivdatei in Ihr Dateisystem herunter.

1. Entpacken Sie die Datei in Ihrem Dateisystem bei Bedarf. Nach der Erweiterung wird ein Ordner mit demselben Namen wie die ausgewählte Seite angezeigt. Dieser Ordner enthält:

   * den Unterordner `content`, der Stamm einer Reihe von Unterordnern ist, die den Pfad zur Seite im Repository widerspiegeln

      * innerhalb dieser Struktur befindet sich die HTML-Datei für die ausgewählte Seite (`<page-name>.html`)
   * sonstige Ressourcen (`.js` Dateien, `.css` Dateien, Bilder usw.) befinden sich gemäß den Einstellungen in der Exportvorlage


1. Öffnen Sie die HTML-Datei der Seite (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`), um das Rendering zu überprüfen.

## Erstellen einer Seiten-Exporttoolkonfiguration für Ihre Website {#creating-a-page-exporter-configuration-for-your-site}

Das Seiten-Exporttool basiert auf dem [Inhaltssynchronisierungs-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html). Die Konfigurationen, die in der **Seiteneigenschaften** -Dialogfeld sind Exportvorlagen, die die erforderlichen Abhängigkeiten für eine Seite definieren.

Wenn ein Seitenexport ausgelöst wird, wird auf die Exportvorlage verwiesen und sowohl der Seitenpfad als auch der Designpfad werden dynamisch angewendet. Anschließend wird die ZIP-Datei erstellt, indem die Standardfunktion zur Inhaltssynchronisierung genutzt wird.

Eine vordefinierte AEM-Installation enthält eine Standardvorlage unter `/etc/contentsync/templates/default`.

* Diese Vorlage ist die Fallback-Vorlage, wenn keine Exportvorlage im Repository gefunden wird.

* Die `default` zeigt Ihnen, wie ein Seitenexport konfiguriert werden kann, sodass er als Grundlage für eine neue Exportvorlage dienen kann.

* Um die Knotenstruktur der Vorlage in Ihrem Browser als JSON-Format anzuzeigen, fordern Sie die folgende URL an:
   `http://localhost:4502/etc/contentsync/templates/default.json`

Die einfachste Methode zum Erstellen einer neuen Vorlage für den Seitenexporteur besteht darin, Folgendes zu tun:

* Kopieren Sie die `default` Vorlage,

* einen neuen Namen zuweisen, der Ihrer Site entspricht,

* dann die erforderlichen Aktualisierungen vornehmen.

So erstellen Sie eine völlig neue Vorlage:

1. In **CRXDE Lite**, erstellen Sie einen Knoten unter `/etc/contentsync/templates`:

   * `Name`: einen Namen, der Ihrer Site entspricht; Beispiel: `<mysite>`. Der Name wird im Dialogfeld &quot;Seiteneigenschaften&quot;angezeigt, wenn Sie die Vorlage &quot;Seitenexporteur&quot;auswählen.

   * `Type`: `nt:unstructured`

2. Erstellen Sie unter dem Vorlagenknoten (in diesem Beispiel: `mysite`) eine Knotenstruktur mit den unten beschriebenen Konfigurationsknoten.

## Aktivieren einer Page Exporter-Vorlage für Ihre Seiten {#activating-a-page-exporter-configuration-for-your-pages}

Nachdem die Vorlage konfiguriert wurde, müssen Sie sie verfügbar machen:

1. Navigieren Sie in CRXDE zur gewünschten Seite in der `/content` -Verzweigung. Dies kann eine einzelne Seite oder die Stammseite eines Unterbaums sein.

1. Im `jcr:content` -Knoten der Seite erstellen Sie die Eigenschaft:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: Pfad zur Vorlage; Beispiel: `/etc/contentsync/templates/mysite`

### Konfigurationsknoten für das Seiten-Exporttool {#page-exporter-configuration-nodes}

Die Vorlage besteht aus einer Knotenstruktur, da sie die [Content Sync-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html).  Jeder Knoten verfügt über die Eigenschaft `type`, die eine spezifische Aktion beim Erstellungsprozess der ZIP-Datei definiert.

<!-- For more details about the type property, refer to the Overview of configuration types section in the Content Sync framework page.
-->

Die folgenden Knoten können zum Erstellen einer Exportvorlage verwendet werden:

* `page`
Mit dem Knoten page wird die HTML-Seite in die ZIP-Datei kopiert. Er weist die folgenden Eigenschaften auf:

   * Er ist ein obligatorischer Knoten.
   * befindet sich unten `/etc/contentsync/templates/<mysite>`.
   * Wird mit der Eigenschaft definiert `Name`auf `page`.
   * Der Knotentyp ist `nt:unstructured`

   Der Knoten `page` hat folgende Eigenschaften:

   * A `type` -Eigenschaft mit dem Wert `pages`.

   * Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

   <!--
  * The other properties are described in the Overview of configuration types section of the Content Sync framework.
  -->

* `rewrite`
Der Knoten rewrite definiert, wie die Links in der exportierten Seite neu geschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.
   <!-- Please refer to the Content Sync page for a complete description of the `rewrite` node. -->

* `design`
Mit dem Knoten design wird das für die exportierte Seite genutzte Design kopiert. Er weist die folgenden Eigenschaften auf:

   * Er ist optional.
   * befindet sich unten `/etc/contentsync/templates/<mysite>`.
   * Wird mit der Eigenschaft definiert `Name` auf `design`.
   * Der Knotentyp ist `nt:unstructured`.

   Der Knoten `design` hat folgende Eigenschaften:

   * A `type` Eigenschaft auf den Wert eingestellt `copy`.

   * Es gibt keine `path` -Eigenschaft, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.


* `generic`
Ein generischer Knoten wird zum Kopieren von Ressourcen wie clientlibs verwendet 
`.js` oder `.css` -Dateien in die ZIP-Datei. Er weist die folgenden Eigenschaften auf:

   * Er ist optional.
   * befindet sich unten `/etc/contentsync/templates/<mysite>`.
   * Er weist keinen bestimmten Namen auf.
   * Der Knotentyp ist `nt:unstructured`.
   * Hat eine `type` -Eigenschaft und `type` verwandte Eigenschaften. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

   Beispielsweise kopiert der folgende Konfigurationsknoten die `mysite.clientlibs.js` -Dateien in die ZIP-Datei:

   ```xml
   "mysite.clientlibs.js": {
       "extension": "js",
       "type": "clientlib",
       "path": "/etc/designs/mysite/clientlibs",
       "jcr:primaryType": "nt:unstructured"
   }
   ```

**Implementieren einer benutzerdefinierten Konfiguration**

Benutzerdefinierte Konfigurationen sind ebenfalls möglich.

<!--
As you may have noticed in the node structure, the **Geometrixx** page export template has a `logo` node with a `type` property set to `image`. This is a special configuration type that has been created to copy the image logo to the zip file. 
-->

Um bestimmte Anforderungen zu erfüllen, müssen Sie möglicherweise eine [benutzerspezifischer Update-Handler](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/handler/package-summary.html).

<!-- To meet some specific requirements, you may need to implement a custom `type` property: to do so, refer to the Implementing a custom update handler section in the Content Sync page.
-->

## Programmatisches Exportieren einer Seite {#programmatically-exporting-a-page}

Um eine Seite programmatisch zu exportieren, können Sie den OSGi-Dienst [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) nutzen. Mit diesem Dienst können Sie:

* eine Seite exportieren und in die HTTP-Servlet-Antwort schreiben
* eine Seite exportieren und die ZIP-Datei an einem bestimmten Ort speichern

Das Servlet, das an die `export` und `zip` -Erweiterung verwendet den PageExporter-Dienst.

## Fehlerbehebung {#troubleshooting}

Wenn beim Herunterladen der ZIP-Datei Probleme auftreten, können Sie die `/var/contentsync` -Knoten im Repository und senden Sie die Exportanfrage erneut.
