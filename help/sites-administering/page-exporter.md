---
title: Das Seiten-Exporttool
description: Erfahren Sie, wie Sie das AEM-Seiten-Exporttool verwenden.
translation-type: tm+mt
source-git-commit: 6aee1506b54a932bae8f2521fce4488de7d2a52a
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 28%

---


# Das Seiten-Exporttool{#the-page-exporter}

AEM ermöglicht es Ihnen, eine Seite als vollständige Webseite zu exportieren, einschließlich Bilder, `.js`- und `.css`-Dateien.

Nach der Konfiguration fordern Sie einen Seitenexport aus Ihrem Browser an, indem Sie `html` durch `export.zip` in der URL ersetzen. Dadurch wird eine ZIP-Datei generiert, die die gerenderte Seite im HTML-Format sowie die referenzierten Assets enthält. Alle Pfade auf der Seite (z. B. Pfade zu Bildern) werden umgeschrieben, um entweder auf die im Archiv enthaltenen Dateien oder auf die Ressourcen auf dem Server zu verweisen. Die ZIP-Datei kann dann von Ihrem Browser heruntergeladen werden.

>[!NOTE]
>
>Je nach Browser und Einstellungen wird der Download wie folgt ausgeführt:
>* eine Archivdatei (`<page-name>.export.zip`)
>* ein Ordner (`<page-name>`); effektiv die Archivdatei, die bereits erweitert wurde


## Exportieren einer Seite {#exporting-a-page}

Die folgenden Schritte beschreiben, wie eine Seite exportiert wird, und gehen davon aus, dass eine Exportvorlage für Ihre Site vorhanden ist. Eine Exportvorlage definiert, wie eine Seite exportiert wird, und ist spezifisch für Ihre Site. Informationen zum Erstellen einer Exportvorlage finden Sie im Abschnitt [Erstellen einer Seitenexportkonfiguration für Ihre Site](#creating-a-page-exporter-configuration-for-your-site).

So exportieren Sie eine Seite:

1. Navigieren Sie zur gewünschten Seite in der Konsole **Sites**.

1. Wählen Sie die Seite aus und öffnen Sie dann das Dialogfeld **Eigenschaften**.

1. Wählen Sie die Registerkarte **Erweitert**.

1. Erweitern Sie das Feld **Export**, um eine Exportvorlage auszuwählen.
Wählen Sie die erforderliche Vorlage für Ihre Site aus und bestätigen Sie dann mit **OK**.

1. Wählen Sie **Speichern und Schließen**, um das Dialogfeld für die Seiteneigenschaften zu schließen.

1. Fordern Sie die Seite zum Exportieren an und ersetzen Sie das Suffix `html` durch `export.zip` in der URL.

   Beispiel:
   * localhost:4502/content/we-retail/language-masters/en.html

   Der Zugriff erfolgt über:
   * localhost:4502/content/we-retail/language-masters/en.export.zip


1. Laden Sie die Archivdatei auf Ihr Dateisystem herunter.

1. Dekomprimieren Sie die Datei im Dateisystem bei Bedarf. Nach der Erweiterung wird ein Ordner mit dem Namen der ausgewählten Seite angezeigt. Dieser Ordner enthält:

   * der Unterordner `content`, der der Stamm einer Reihe von Unterordnern ist, die den Pfad zur Seite im Repository widerspiegeln

      * in dieser Struktur die HTML-Datei für die ausgewählte Seite (`<page-name>.html`)
   * andere Ressourcen (`.js`-Dateien, `.css`-Dateien, Bilder usw.) gemäß den Einstellungen in der Exportvorlage


1. Öffnen Sie die HTML-Datei der Seite (`<unzip-dir>/<path>/<to>/<page>/<page-path>.html`) in Ihrem Browser, um die Wiedergabe zu überprüfen.

## Erstellen einer Seiten-Exporttoolkonfiguration für Ihre Website {#creating-a-page-exporter-configuration-for-your-site}

Das Seiten-Exporttool basiert auf dem [Inhaltssynchronisierungs-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html). Die im Dialogfeld **Seiteneigenschaften** verfügbaren Konfigurationen sind Exportvorlagen, die die erforderlichen Abhängigkeiten für eine Seite definieren.

Wenn ein Seitenexport ausgelöst wird, wird auf die Exportvorlage verwiesen und sowohl der Seitenpfad als auch der Entwurfspfad werden dynamisch angewendet. Anschließend wird die ZIP-Datei erstellt, indem die Standardfunktion zur Inhaltssynchronisierung genutzt wird.

Eine vordefinierte AEM-Installation enthält eine Standardvorlage unter `/etc/contentsync/templates/default`.

* Diese Vorlage ist die Ausweichvorlage, wenn keine Exportvorlage im Repository gefunden wird.

* Die Vorlage `default` zeigt Ihnen, wie ein Seitenexport konfiguriert werden kann, sodass er als Grundlage für eine neue Exportvorlage dienen kann.

* Um die Knotenstruktur der Vorlage im Browser als JSON-Format Ansicht, fordern Sie die folgende URL an:
   `http://localhost:4502/etc/contentsync/templates/default.json`

Die einfachste Methode zum Erstellen einer neuen Vorlage für den Seitenexporteur besteht darin,

* Kopieren der Vorlage `default`,

* einen neuen Namen zuzuweisen, der Ihrer Site entspricht,

* dann die erforderlichen Aktualisierungen vornehmen.

So erstellen Sie eine komplett neue Vorlage:

1. Erstellen Sie in **CRXDE Lite** einen Knoten unter `/etc/contentsync/templates`:

   * `Name`: einen Namen, der Ihrer Site entspricht; zum Beispiel  `<mysite>`. Der Name wird im Dialogfeld &quot;Seiteneigenschaften&quot;angezeigt, wenn Sie die Vorlage für den Seitenexporteur auswählen.

   * `Type`: `nt:unstructured`

2. Erstellen Sie unter dem Vorlagenknoten (in diesem Beispiel: `mysite`) eine Knotenstruktur mit den unten beschriebenen Konfigurationsknoten.

## Aktivieren einer Seitenexportvorlage für Ihre Seiten {#activating-a-page-exporter-configuration-for-your-pages}

Sobald die Vorlage konfiguriert wurde, müssen Sie sie verfügbar machen:

1. Navigieren Sie in CRXDE zur gewünschten Seite in der Verzweigung `/content`. Dabei kann es sich um eine einzelne Seite oder um die Stamm-Seite eines Unterbaums handeln.

1. Erstellen Sie auf dem Knoten `jcr:content` der Seite die Eigenschaft:
   * `Name`:  `cq:exportTemplate`
   * `Type`:  `String`
   * `Value`: Pfad zur Vorlage; Beispiel:  `/etc/contentsync/templates/mysite`

### Konfigurationsknoten für das Seiten-Exporttool {#page-exporter-configuration-nodes}

Die Vorlage besteht aus einer Knotenstruktur, da sie das [Content Sync-Framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/package-summary.html) verwendet.  Jeder Knoten verfügt über die Eigenschaft `type`, die eine spezifische Aktion beim Erstellungsprozess der ZIP-Datei definiert.

<!-- For more details about the type property, refer to the Overview of configuration types section in the Content Sync framework page.
-->

Die folgenden Knoten können zum Erstellen einer Exportvorlage verwendet werden:

* `page`
Mit dem Knoten page wird die HTML-Seite in die ZIP-Datei kopiert. Er weist die folgenden Eigenschaften auf:

   * Er ist ein obligatorischer Knoten.
   * Befindet sich unterhalb von `/etc/contentsync/templates/<mysite>`.
   * Ist definiert, wenn die Eigenschaft `Name`auf `page` eingestellt ist.
   * Der Knotentyp ist `nt:unstructured`

   Der Knoten `page` hat folgende Eigenschaften:

   * Eine `type`-Eigenschaft mit dem Wert `pages`.

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
   * Befindet sich unterhalb von `/etc/contentsync/templates/<mysite>`.
   * Ist definiert, wenn die Eigenschaft `Name` auf `design` eingestellt ist.
   * Der Knotentyp ist `nt:unstructured`.

   Der Knoten `design` hat folgende Eigenschaften:

   * Eine `type`-Eigenschaft, die auf den Wert `copy` gesetzt ist.

   * Es hat keine `path`-Eigenschaft, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.


* `generic`
Ein generischer Knoten wird zum Kopieren von Ressourcen wie clientlibs verwendet 
`.js` oder  `.css` Dateien in die ZIP-Datei. Er weist die folgenden Eigenschaften auf:

   * Er ist optional.
   * Befindet sich unterhalb von `/etc/contentsync/templates/<mysite>`.
   * Er weist keinen bestimmten Namen auf.
   * Der Knotentyp ist `nt:unstructured`.
   * Hat eine `type`-Eigenschaft und `type` verwandte Eigenschaften. <!--Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.-->

   Beispielsweise kopiert der folgende Konfigurationsknoten die `mysite.clientlibs.js`-Dateien in die ZIP-Datei:

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

Um bestimmte Anforderungen zu erfüllen, müssen Sie möglicherweise einen [benutzerdefinierten Updatehandler](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/handler/package-summary.html) implementieren.

<!-- To meet some specific requirements, you may need to implement a custom `type` property: to do so, refer to the Implementing a custom update handler section in the Content Sync page.
-->

## Programmatisches Exportieren einer Seite {#programmatically-exporting-a-page}

Um eine Seite programmatisch zu exportieren, können Sie den OSGi-Dienst [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) nutzen. Mit diesem Dienst können Sie:

* eine Seite exportieren und in die HTTP-Servlet-Antwort schreiben
* eine Seite exportieren und die ZIP-Datei an einem bestimmten Ort speichern

Das Servlet, das an den Selektor `export` und die Erweiterung `zip` gebunden ist, verwendet den PageExporter-Dienst.

## Fehlerbehebung {#troubleshooting}

Wenn beim Herunterladen der ZIP-Datei ein Problem auftritt, können Sie den Knoten `/var/contentsync` im Repository löschen und die Exportanforderung erneut senden.
