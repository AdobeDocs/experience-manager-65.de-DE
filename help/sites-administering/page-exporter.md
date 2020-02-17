---
title: Das Seiten-Exporttool
seo-title: Das Seiten-Exporttool
description: Erfahren Sie, wie Sie das AEM-Seiten-Exporttool verwenden.
seo-description: Erfahren Sie, wie Sie das AEM-Seiten-Exporttool verwenden.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Das Seiten-Exporttool{#the-page-exporter}

AEM bietet Ihnen die Möglichkeit, eine Seite als vollständige Webseite einschließlich aller Grafiken, JS- und CSS-Dateien zu exportieren.

Wenn Sie den Export konfiguriert haben, können Sie einfach eine Seite im Browser anfordern. Ersetzen Sie dafür in der URL `html` durch `export.zip`. So erzeugen Sie den Download einer ZIP-Datei, in der die gerenderte Seite im HTML-Format und die referenzierten Assets enthalten sind. Alle in der Seite enthaltenen Pfade, z. B. Pfade zu Grafiken, werden umgeschrieben und verweisen entweder auf die in der ZIP-Datei enthaltenen Dateien oder auf die Ressourcen auf dem Server.

## Exportieren einer Seite {#exporting-a-page}

Die folgenden Schritte beschreiben, wie Sie eine Seite exportieren können. Vorausgesetzt wird, dass für Ihre Website eine Vorlage für die Exportkonfiguration vorliegt: Eine Konfigurationsvorlage legt fest, wie eine Seite exportiert wird, und gilt speziell für Ihre Website. To create a configuration template refer to the [Creating a Page Exporter Configuration for your Site](#creating-a-page-exporter-configuration-for-your-site) section.

So exportieren Sie eine Seite:

1. Öffnen Sie die Seite im Browser. Beispiel:
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. Öffnen Sie das Dialogfeld „Seiteneigenschaften“, wählen Sie die Registerkarte **Erweitert** und erweitern Sie das Feld **Exportieren**.

1. Klicken Sie auf das Lupensymbol und wählen Sie eine Konfigurationsvorlage aus. Wählen Sie die **geometrixx**-Vorlage aus; sie ist die standardmäßige Vorlage für die Geometrixx-Website. Klicken Sie auf **OK**.

1. Klicken Sie auf **OK**, um das Dialogfeld „Seiteneigenschaften“ zu schließen.
1. Request the page by replacing `html` with `export.zip` in the URL.

1. Download the `<page-name>.export.zip` file to your file system.

1. Entpacken Sie in Ihrem Dateisystem die Datei:

   * Die HTML-Datei der Seite ( `<page-name>.html`) ist unten verfügbar. `<unzip-dir>/<page-path>`
   * Die anderen Ressourcen (JS- und CSS-Dateien, Grafiken usw.) befinden sich in den in der Exportvorlage festgelegten Verzeichnissen. In diesem Beispiel sind einige Ressourcen unten `<unzip-dir>/etc`, einige unten `<unzip-dir>/<page-path>`.

1. Open the page html file ( `<unzip-dir>/<page-path>.html`) in your browser to check the rendering.

## Erstellen einer Seiten-Exporttoolkonfiguration für Ihre Website {#creating-a-page-exporter-configuration-for-your-site}

Das Seiten-Exporttool basiert auf dem Inhaltssynchronisierungs-Framework. Die im Dialogfeld &quot;Seiteneigenschaften&quot;verfügbaren Konfigurationen sind Konfigurationsvorlagen. Sie definieren alle erforderlichen Abhängigkeiten einer Seite. Wenn ein Seitenexport ausgelöst wird, wird die Konfigurationsvorlage verwendet und sowohl der Seitenpfad als auch der Entwurfspfad werden dynamisch auf die Konfiguration angewendet. Anschließend wird die ZIP-Datei erstellt, indem die Standardfunktion zur Inhaltssynchronisierung genutzt wird.

AEM bettet einige Vorlagen ein, darunter eine:

* A default one at `/etc/contentsync/templates/default`. Diese Vorlage:

   * Dient als Fallback-Vorlage, wenn keine Konfigurationsvorlage im Repository gefunden wird
   * Kann als Grundlage für eine neue Konfigurationsvorlage dienen.

* One that is dedicated to the **Geometrixx** site, at `/etc/contentsync/templates/geometrixx`. Diese Vorlage kann als Beispiel verwendet werden, um eine neue zu erstellen.

So erstellen Sie eine Konfigurationsvorlage für das Seiten-Exporttool:

1. In **CRXDE Lite**, create a node below `/etc/contentsync/templates`:

   * Name:z. B. `mysite`. Der Name wird im Dialogfeld &quot;Seiteneigenschaften&quot;angezeigt, wenn Sie die Vorlage für den Seitenexporteur auswählen.
   * Typ: `nt:unstructured`

1. Erstellen Sie unter dem Vorlagenknoten (in diesem Beispiel: `mysite`) eine Knotenstruktur mit den unten beschriebenen Konfigurationsknoten.

### Konfigurationsknoten für das Seiten-Exporttool {#page-exporter-configuration-nodes}

Die Konfigurationsvorlage besteht aus einer Knotenstruktur. Jeder Knoten verfügt über die Eigenschaft `type`, die eine spezifische Aktion beim Erstellungsprozess der ZIP-Datei definiert. Weitere Informationen zur type-Eigenschaft finden Sie im Abschnitt Übersicht über Konfigurationstypen auf der Seite Inhaltssynchronisierung-Framework.

Mit den folgenden Knoten können Sie eine Export-Konfigurationsvorlage erstellen:

**Seitenknoten** Der Seitenknoten wird verwendet, um die Seiten-HTML in die ZIP-Datei zu kopieren. Er weist die folgenden Eigenschaften auf:

* Er ist ein obligatorischer Knoten.
* Befindet sich unterhalb `/etc/contentsync/templates/<sitename>`.
* Its name is `page`.
* Its node type is `nt:unstructured`

Der Knoten `page` hat folgende Eigenschaften:

* A `type` property set with the value `pages`.

* Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

* Die anderen Eigenschaften werden im Abschnitt Übersicht über die Konfigurationstypen des Content Sync-Frameworks beschrieben.

**rewrite-Knoten** Der rewrite-Knoten definiert, wie die Links auf der exportierten Seite umgeschrieben werden. Die neu geschriebenen Links können entweder auf die Dateien in der ZIP-Datei oder auf die Ressourcen auf dem Server verweisen.

Auf der Seite Inhaltssynchronisierung finden Sie eine vollständige Beschreibung des Knotens `rewrite`.

**Designknoten** Der Designknoten wird verwendet, um den Entwurf zu kopieren, der für die exportierte Seite verwendet wird. Er weist die folgenden Eigenschaften auf:

* Er ist optional.
* Befindet sich unterhalb `/etc/contentsync/templates/<sitename>`.
* Its name is `design`.
* Its node type is `nt:unstructured`.

Der Knoten `design` hat folgende Eigenschaften:

* A `type` property set to the value `copy`.

* Er verfügt nicht über die Eigenschaft `path`, da der aktuelle Seitenpfad dynamisch in die Konfiguration kopiert wird.

**generischer Knoten** Ein generischer Knoten wird verwendet, um Ressourcen wie clientlibs .js- oder .css-Dateien in die ZIP-Datei zu kopieren. Er weist die folgenden Eigenschaften auf:

* Er ist optional.
* Befindet sich unterhalb `/etc/contentsync/templates/<sitename>`.
* Er weist keinen bestimmten Namen auf.
* Its node type is `nt:unstructured`.
* Has a `type` property and any `type` related properties as defined in the Overview of configuration types section of the Content Sync framework.

Beispielsweise kopiert der folgende Konfigurationsknoten die JS-Dateien der Geometrixx-Clientlibs in die ZIP-Datei:

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

Die **Geometrixx**-Konfigurationsvorlage für das Seiten-Exporttool zeigt, wie Sie einen Seitenexport konfigurieren können. Um die Knotenstruktur der Vorlage in Ihrem Browser im JSON-Format anzuzeigen, fordern Sie die folgenden URL an:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**Implementieren einer benutzerdefinierten Konfiguration**

Wie Sie vielleicht bei der Knotenstruktur bemerkt haben, verfügt die **Geometrixx**-Konfigurationsvorlage für das Seiten-Exporttool über den Knoten `logo`, bei dem die Eigenschaft `type`auf `image` festgelegt ist. Das ist ein spezieller Konfigurationstyp, der erstellt wurde, um das Grafiklogo in die ZIP-Datei zu kopieren. Um bestimmte Anforderungen zu erfüllen, müssen Sie möglicherweise eine benutzerdefinierte Eigenschaft `type` implementieren. Informationen hierzu finden Sie im Abschnitt Implementieren eines benutzerdefinierten Aktualisierungshandlers auf der Seite „Inhaltssynchronisierung“.

## Programmatisches Exportieren einer Seite {#programmatically-exporting-a-page}

Um eine Seite programmatisch zu exportieren, können Sie den OSGi-Dienst [PageExporter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) nutzen. Mit diesem Dienst können Sie:

* eine Seite exportieren und in die HTTP-Servlet-Antwort schreiben
* eine Seite exportieren und die ZIP-Datei an einem bestimmten Ort speichern

The servlet that is bound to the `export` selector and the `zip` extension uses the PageExporter service.

## Fehlerbehebung {#troubleshooting}

If you experience a problem with the download of the zip file, you may delete the `/var/contentsync` node in the repository and send the export request again.

