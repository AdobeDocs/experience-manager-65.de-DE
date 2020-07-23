---
title: Das Seiten-Exporttool
description: Erfahren Sie, wie Sie das AEM-Seiten-Exporttool verwenden.
translation-type: tm+mt
source-git-commit: 6aee1506b54a932bae8f2521fce4488de7d2a52a
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 24%

---


# Das Seiten-Exporttool{#the-page-exporter}

AEM allows you to export a page as a complete web page including images, `.js` and `.css` files.

Nach der Konfiguration fordern Sie einen Seitenexport aus Ihrem Browser an, indem Sie `html` durch `export.zip` in der URL ersetzen. Dadurch wird eine ZIP-Datei generiert, die die gerenderte Seite im HTML-Format sowie die referenzierten Assets enthält. Alle Pfade auf der Seite (z. B. Pfade zu Bildern) werden umgeschrieben, um entweder auf die im Archiv enthaltenen Dateien oder auf die Ressourcen auf dem Server zu verweisen. Die ZIP-Datei kann dann von Ihrem Browser heruntergeladen werden.

>[!NOTE]
>
>Je nach Browser und Einstellungen wird der Download wie folgt ausgeführt:
>* eine Archivdatei (`<page-name>.export.zip`)
>* Ordner (`<page-name>`); effektiv die Archivdatei, die bereits erweitert wurde


## Exportieren einer Seite {#exporting-a-page}

Die folgenden Schritte beschreiben, wie eine Seite exportiert wird, und gehen davon aus, dass eine Exportvorlage für Ihre Site vorhanden ist. Eine Exportvorlage definiert, wie eine Seite exportiert wird, und ist spezifisch für Ihre Site. To create an export template refer to the [Creating a Page Exporter Configuration for your Site](#creating-a-page-exporter-configuration-for-your-site) section.

So exportieren Sie eine Seite:

1. Navigieren Sie zur gewünschten Seite in der **Sites** -Konsole.

1. Wählen Sie die Seite aus und öffnen Sie dann das Dialogfeld **Eigenschaften** .

1. Wählen Sie die Registerkarte **Erweitert**.

1. Erweitern Sie das Feld **Exportieren** , um eine Exportvorlage auszuwählen.
Wählen Sie die erforderliche Vorlage für Ihre Site aus und bestätigen Sie dann mit **OK**.

1. Wählen Sie **Speichern und Schließen** , um das Dialogfeld mit den Seiteneigenschaften zu schließen.

1. Fordern Sie die Seite zum Exportieren an und ersetzen Sie das Suffix `html` durch `export.zip` die URL.

   Beispiel:
   * localhost:4502/content/we-retail/language-masters/en.html

   Der Zugriff erfolgt über:
   * localhost:4502/content/we-retail/language-masters/en.export.zip


1. Laden Sie die Archivdatei auf Ihr Dateisystem herunter.

1. Dekomprimieren Sie die Datei im Dateisystem bei Bedarf. Nach der Erweiterung wird ein Ordner mit dem Namen der ausgewählten Seite angezeigt. Dieser Ordner enthält:

   * der Unterordner `content`, der der Stamm einer Reihe von Unterordnern ist, die den Pfad zur Seite im Repository widerspiegeln

      * innerhalb dieser Struktur befindet sich die HTML-Datei für die ausgewählte Seite (`<page-name>.html`)
   * andere Ressourcen (`.js` Dateien, `.css` Dateien, Bilder usw.) gemäß den Einstellungen in der Exportvorlage


1. Open the page html file (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) in your browser to check the rendering.

## Erstellen einer Seiten-Exporttoolkonfiguration für Ihre Website {#creating-a-page-exporter-configuration-for-your-site}

Das Seiten-Exporttool basiert auf dem [Inhaltssynchronisierungs-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html). Die im Dialogfeld &quot; **Seiteneigenschaften** &quot;verfügbaren Konfigurationen sind Exportvorlagen, die die erforderlichen Abhängigkeiten für eine Seite definieren.

Wenn ein Seitenexport ausgelöst wird, wird auf die Exportvorlage verwiesen und sowohl der Seitenpfad als auch der Entwurfspfad werden dynamisch angewendet. Anschließend wird die ZIP-Datei erstellt, indem die Standardfunktion zur Inhaltssynchronisierung genutzt wird.

Eine vordefinierte AEM-Installation enthält eine Standardvorlage unter `/etc/contentsync/templates/default`.

* Diese Vorlage ist die Ausweichvorlage, wenn keine Exportvorlage im Repository gefunden wird.

* Die `default` Vorlage zeigt Ihnen, wie ein Seitenexport konfiguriert werden kann, sodass er als Grundlage für eine neue Exportvorlage dienen kann.

* Um die Knotenstruktur der Vorlage im Browser als JSON-Format Ansicht, fordern Sie die folgende URL an:
   `http://localhost:4502/etc/contentsync/templates/default.json`

Die einfachste Methode zum Erstellen einer neuen Vorlage für den Seitenexporteur besteht darin,

* die `default` Vorlage kopieren,

* einen neuen Namen zuzuweisen, der Ihrer Site entspricht,

* dann die erforderlichen Aktualisierungen vornehmen.

So erstellen Sie eine komplett neue Vorlage:

1. In **CRXDE Lite**, create a node below `/etc/contentsync/templates`:

   * `Name`: einen Namen, der Ihrer Site entspricht; zum Beispiel `<mysite>`. Der Name wird im Dialogfeld &quot;Seiteneigenschaften&quot;angezeigt, wenn Sie die Vorlage für den Seitenexporteur auswählen.

   * `Type`: `nt:unstructured`

2. Erstellen Sie unter dem Vorlagenknoten (in diesem Beispiel: `mysite`) eine Knotenstruktur mit den unten beschriebenen Konfigurationsknoten.

## Aktivieren einer Seitenexportvorlage für Ihre Seiten {#activating-a-page-exporter-configuration-for-your-pages}

Sobald die Vorlage konfiguriert wurde, müssen Sie sie verfügbar machen:

1. Navigieren Sie in CRXDE zur gewünschten Seite in der `/content` Verzweigung. Dabei kann es sich um eine einzelne Seite oder um die Stamm-Seite eines Unterbaums handeln.

1. Erstellen Sie auf dem `jcr:content` Knoten der Seite die Eigenschaft:
   * `Name`: `cq:exportTemplate`
   * `Type`: `String`
   * `Value`: Pfad zur Vorlage; Beispiel: `/etc/contentsync/templates/mysite`

### Konfigurationsknoten für das Seiten-Exporttool {#page-exporter-configuration-nodes}

Die Vorlage besteht aus einer Knotenstruktur, da sie das [Content Sync-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html)verwendet.  Jeder Knoten verfügt über die Eigenschaft `type`, die eine spezifische Aktion beim Erstellungsprozess der ZIP-Datei definiert.

<!-- For more details about the type property, refer to the Overview of configuration types section in the Content Sync framework page.
-->

Die folgenden Knoten können zum Erstellen einer Exportvorlage verwendet werden:

* `page`
Mit dem Knoten page wird die HTML-Seite in die ZIP-Datei kopiert. Er weist die folgenden Eigenschaften auf:

   * Er ist ein obligatorischer Knoten.
   * Befindet sich unterhalb `/etc/contentsync/templates/<mysite>`.
   * Ist definiert, wobei die Eigenschaft `Name`auf `page`.
   * Der Knotentyp ist `nt:unstructured`

   Der Knoten `page` hat folgende Eigenschaften:

   * A `type` property set with the value `pages`.

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
   * Befindet sich unterhalb `/etc/contentsync/templates/<mysite>`.
   * Ist definiert mit der Eigenschaft `Name` auf `design`.
   * Der Knotentyp ist `nt:unstructured`.

   Der Knoten `design` hat folgende Eigenschaften:

   * A `type` property set to the value `copy`.

   * It does not have a `path` property, as the current page path is dynamically copied to the configuration.


* `generic`
Ein generischer Knoten wird zum Kopieren von Ressourcen wie clientlibs verwendet 
`.js` oder `.css` Dateien in die ZIP-Datei. Er weist die folgenden Eigenschaften auf:

   * Er ist optional.
   * Befindet sich unterhalb `/etc/contentsync/templates/<mysite>`.
   * Er weist keinen bestimmten Namen auf.
   * Der Knotentyp ist `nt:unstructured`.
   * Hat eine `type` Eigenschaft und zugehörige `type` Eigenschaften. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

   For example the following configuration node copies the `mysite.clientlibs.js` files to the zip file:

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

Um bestimmte Anforderungen zu erfüllen, müssen Sie möglicherweise einen [benutzerdefinierten Aktualisierungshandler](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/handler/package-summary.html)implementieren.

<!-- To meet some specific requirements, you may need to implement a custom `type` property: to do so, refer to the Implementing a custom update handler section in the Content Sync page.
-->

## Programmatisches Exportieren einer Seite {#programmatically-exporting-a-page}

Um eine Seite programmatisch zu exportieren, können Sie den OSGi-Dienst [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) nutzen. Mit diesem Dienst können Sie:

* eine Seite exportieren und in die HTTP-Servlet-Antwort schreiben
* eine Seite exportieren und die ZIP-Datei an einem bestimmten Ort speichern

The servlet that is bound to the `export` selector and the `zip` extension uses the PageExporter service.

## Fehlerbehebung {#troubleshooting}

If you experience a problem with the download of the zip file, you may delete the `/var/contentsync` node in the repository and send the export request again.
