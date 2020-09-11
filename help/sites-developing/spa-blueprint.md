---
title: SPA-Blueprint
seo-title: SPA-Blueprint
description: In diesem Dokument wird der allgemeine, rahmenunabhängige Vertrag beschrieben, den ein SPA-Framework erfüllen sollte, um bearbeitbare SPA-Komponenten in AEM zu implementieren.
seo-description: In diesem Dokument wird der allgemeine, rahmenunabhängige Vertrag beschrieben, den ein SPA-Framework erfüllen sollte, um bearbeitbare SPA-Komponenten in AEM zu implementieren.
uuid: 48f2d415-ec34-49dc-a8e1-6feb5a8a5bbe
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 04ac8203-320b-4671-aaad-6e1397b12b6f
docset: aem65
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '2112'
ht-degree: 14%

---


# SPA-Blueprint{#spa-blueprint}

Damit der Autor den AEM SPA-Editor zum Bearbeiten des Inhalts einer SPA verwenden kann, müssen bestimmte Anforderungen erfüllt sein, die in diesem Dokument beschrieben werden.

>[!NOTE]
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen clientseitiges Rendering (z.B. React oder Angular) durch das SPA-Framework erforderlich ist.

## Einführung {#introduction}

In diesem Dokument wird der allgemeine Vertrag beschrieben, den ein SPA-Framework erfüllen sollte (d.h. die Art AEM Supportebene), um bearbeitbare SPA-Komponenten in AEM zu implementieren.

>[!NOTE]
>
>Die folgenden Bedingungen gelten unabhängig vom Framework. Sofern diese Anforderungen erfüllt sind, kann eine Framework-spezifische Schicht aus Modulen, Komponenten und Services bereitgestellt werden.
>
>**Diese Anforderungen sind bereits für die React- und Angular-Frameworks in AEM erfüllt.** Die Anforderungen in diesem Entwurf sind nur relevant, wenn Sie ein anderes Framework zur Verwendung mit AEM implementieren möchten.

>[!CAUTION]
>
>Obwohl die SPA-Funktionen von AEM Framework-unabhängig sind, werden derzeit nur die React- und Angular-Frameworks unterstützt.

Damit der Autor den AEM-Seiten-Editor verwenden kann, um die Daten zu bearbeiten, die von einem Einzelseitenanwendungs-Framework bereitgestellt werden, muss ein Projekt die Struktur des Modells interpretieren können, das die Semantik der Daten darstellt, die für eine Anwendung im AEM Repository gespeichert sind. Um dieses Ziel zu erreichen, stehen zwei Framework-agnostische Bibliotheken zur Verfügung: die `PageModelManager` und die `ComponentMapping`.

### PageModelManager {#pagemodelmanager}

Die `PageModelManager` Bibliothek wird als NPM-Paket bereitgestellt, das von einem SPA-Projekt verwendet werden soll. Es begleitet die SPA und dient als Datenmodellmanager.

Es abstrahiert den Abruf und die Verwaltung der JSON-Struktur, die die eigentliche Inhaltsstruktur darstellt, im Namen der SPA. Es ist auch für die Synchronisierung mit der SPA verantwortlich, um ihr mitzuteilen, wann sie ihre Komponenten wiedergeben muss.

Siehe NPM-Paket [@adobe/aem-spa-page-model-manager](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager)

Beim Initialisieren der App lädt `PageModelManager`die Bibliothek zunächst das bereitgestellte Stammmodell der App (über Parameter, Metadateneigenschaft oder aktuelle URL). Wenn die Bibliothek erkennt, dass das Modell der aktuellen Seite nicht Teil des Stammmodells ist, wird es abgerufen und als Modell einer untergeordneten Seite eingefügt.

![page_model_configuration](assets/page_model_consolidation.png)

### ComponentMapping {#componentmapping}

The `ComponentMapping` module is provided as an NPM package to the front-end project. Es speichert Front-End-Komponenten und bietet eine Möglichkeit für die SPA, Front-End-Komponenten AEM Ressourcentypen zuzuordnen. Dies ermöglicht eine dynamische Auflösung von Komponenten beim Parsen des JSON-Modells der Anwendung.

Alle im Modell vorhandenen Elemente enthalten ein `:type` Feld, das einen AEM Ressourcentyp verfügbar macht. Bei der Bereitstellung kann sich die Front-End-Komponente mit dem Fragment des Modells wiedergeben, das sie von den zugrunde liegenden Bibliotheken erhalten hat.

#### Zuordnung dynamischer Modelle zu Komponenten {#dynamic-model-to-component-mapping}

Weitere Informationen dazu, wie die Zuordnung des dynamischen Modells zu einer Komponente im JavaScript-SPA-SDK erfolgt AEM finden Sie im Artikel [Dynamisches Modell zu Komponentenzuordnung für SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

### Rahmenspezifische Ebene {#framework-specific-layer}

Für jedes Front-End-Framework muss eine dritte Ebene implementiert werden. Diese dritte Bibliothek ist verantwortlich für die Interaktion mit den zugrunde liegenden Bibliotheken und bietet eine Reihe von gut integrierten und einfach zu verwendenden Einstiegspunkten für die Interaktion mit dem Datenmodell.

Der Rest dieses Dokuments beschreibt die Anforderungen dieser speziellen Zwischenrahmen-Ebene und strebt eine Rahmenunabhängigkeit an. Unter Beachtung der folgenden Anforderungen kann eine Framework-spezifische Ebene bereitgestellt werden, auf der die Projektkomponenten mit den zugrunde liegenden Bibliotheken interagieren können, die für die Verwaltung des Datenmodells zuständig sind.

## Allgemeine Konzepte {#general-concepts}

### Seitenmodell {#page-model}

Die Inhaltsstruktur der Seite wird in AEM gespeichert. Das Modell der Seite wird verwendet, um SPA-Komponenten zuzuordnen und zu instanziieren. Die SPA-Entwickler erstellen SPA-Komponenten, die sie den AEM-Komponenten zuordnen. Dazu verwenden sie den Ressourcentyp (oder den Pfad zur AEM Komponente) als eindeutigen Schlüssel.

Die SPA-Komponenten müssen mit dem Seitenmodell übereinstimmen und mit allen inhaltlichen Änderungen entsprechend aktualisiert werden. Sie müssen ein Muster verwenden, das dynamische Komponenten nutzt, um Komponenten entsprechend der vorgegebenen Seitenmodellstruktur spontan zu instanziieren.

### Meta-Felder {#meta-fields}

The page model leverages the JSON Model Exporter, which is itself based on the [Sling Model](https://sling.apache.org/documentation/bundles/models.html) API. Die exportierbaren Sling-Modelle machen die folgende Liste von Feldern verfügbar, damit die zugrunde liegenden Bibliotheken das Datenmodell interpretieren können:

* `:type`: Typ der AEM Ressource (Standard = Ressourcentyp)
* `:children`: Hierarchische untergeordnete Elemente der aktuellen Ressource. Untergeordnete Elemente sind nicht Teil des inneren Inhalts der aktuellen Ressource (zu Elementen, die eine Seite darstellen).
* `:hierarchyType`: Hierarchischer Typ einer Ressource. Der `PageModelManager` derzeit unterstützte Seitentyp

* `:items`: Ressourcen für untergeordnete Inhalte der aktuellen Ressource (verschachtelte Struktur, nur auf Containern vorhanden)
* `:itemsOrder`: Sortierte Liste der untergeordneten Elemente. Das JSON-Map-Objekt garantiert nicht die Reihenfolge seiner Felder. Indem sowohl die Map als auch das aktuelle Array vorhanden sind, hat der Benutzer der API die Vorteile beider Strukturen
* `:path`: Inhaltspfad eines Elements (vorhanden auf Elementen, die eine Seite darstellen)

Siehe auch [Erste Schritte mit AEM Content Services](https://helpx.adobe.com/de/experience-manager/kt/sites/using/content-services-tutorial-use.html).

### Rahmenspezifisches Modul {#framework-specific-module}

Die Trennung von Anliegen erleichtert die Projektdurchführung. Daher sollte ein npm-spezifisches Paket bereitgestellt werden. Dieses Paket ist für das Aggregieren und Freigeben der Basismodule, Dienste und Komponenten verantwortlich. Diese Komponenten müssen die Verwaltungslogik des Datenmodells einschließen und Zugriff auf die Daten gewähren, die die Projektkomponente erwartet. Das Modul ist auch verantwortlich für die vorübergehende Offenlegung nützlicher Einstiegspunkte der zugrunde liegenden Bibliotheken.

Um die Interoperabilität der Bibliotheken zu erleichtern, empfiehlt Adobe dem Framework-spezifischen Modul, die folgenden Bibliotheken zu bündeln. Bei Bedarf kann die Ebene die zugrunde liegenden APIs einkapseln und anpassen, bevor sie dem Projekt bereitgestellt werden.

* [@adobe/aem-spa-page-model-manager](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager)
* [@adobe/aem-spa-component-mapping](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

#### Implementierungen {#implementations}

#### React {#react}

npm-Modul: [@adobe/aem-response-editable-components](https://www.npmjs.com/package/@adobe/aem-react-editable-components)

#### Angular {#angular}

npm-Modul: demnächst

## Hauptdienste und Komponenten {#main-services-and-components}

Die folgenden Einrichtungen sollten im Einklang mit den für jeden Rahmen spezifischen Leitlinien umgesetzt werden. Basierend auf der Rahmenarchitektur kann die Implementierung sehr unterschiedlich sein, aber die beschriebenen Funktionen müssen bereitgestellt werden.

### Modellanbieter {#the-model-provider}

Projektkomponenten müssen den Zugriff auf die Fragmente eines Modells an einen Modellanbieter delegieren. Der Modellanbieter überwacht dann die Änderungen, die an dem angegebenen Fragment des Modells vorgenommen wurden, und gibt das aktualisierte Modell an die delegierende Komponente zurück.

Dazu muss sich der Modellanbieter beim ` [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager)`Anbieter registrieren. Wenn eine Änderung eintritt, werden die aktualisierten Daten empfangen und an die delegierende Komponente übergeben. Standardmäßig wird die Eigenschaft benannt, die der Delegierungskomponente zur Verfügung gestellt wird, die das Fragment des Modells enthält `cqModel`. Die Implementierung kann diese Eigenschaft für die Komponente bereitstellen, sollte jedoch Aspekte wie die Integration mit der Framework-Architektur, die Erkennbarkeit und die Benutzerfreundlichkeit berücksichtigen.

### Komponenten-HTML-Dekorator {#the-component-html-decorator}

Der Komponenten-Dekorator ist für die Dekoration des äußeren HTML-Elements der einzelnen Komponenteninstanzen mit einer Reihe von Datenattributen und Klassennamen verantwortlich, die vom Seiten-Editor erwartet werden.

#### Komponentendeklaration {#component-declaration}

Die folgenden Metadaten müssen dem äußeren HTML-Element hinzugefügt werden, das von der Projektkomponente erzeugt wird. Sie ermöglichen es dem Seiten-Editor, die entsprechende Bearbeitungskonfiguration abzurufen.

* `data-cq-data-path`: Pfad zur Ressource relativ zum `jcr:content`

#### Erklärung und Platzhalter für Bearbeitungsfunktionen {#editing-capability-declaration-and-placeholder}

Die folgenden Metadaten und Klassennamen müssen dem äußeren HTML-Element hinzugefügt werden, das von der Komponente des Projekts erzeugt wird. Sie ermöglichen es dem Seiteneditor, Funktionen im Zusammenhang mit Angeboten anzuzeigen.

* `cq-placeholder`: Klassenname, der den Platzhalter für eine leere Komponente identifiziert
* `data-emptytext`: Beschriftung, die von der Überlagerung angezeigt wird, wenn eine Komponenteninstanz leer ist

**Platzhalter für leere Komponenten**

Jede Komponente muss mit einer Funktion erweitert werden, die das äußere HTML-Element mit Datenattributen und Klassennamen dekoriert, die für Platzhalter und zugehörige Überlagerungen spezifisch sind, wenn die Komponente als leer identifiziert wird.

**Die Leere einer Komponente**

* Ist die Komponente logisch leer?
* Welche Beschriftung sollte die Überlagerung anzeigen, wenn die Komponente leer ist?

### Container {#container}

Ein Container ist eine Komponente, die untergeordnete Komponenten enthält und rendert. Dazu durchläuft der Container die `:itemsOrder`- `:items` und `:children` -Eigenschaften seines Modells.

Der Container ruft die untergeordneten Komponenten dynamisch aus dem Bibliotheksspeicher ` [ComponentMapping](/help/sites-developing/spa-blueprint.md#componentmapping)` ab. Der Container erweitert dann die untergeordnete Komponente mit den Modellanbieterfunktionen und instanziiert sie schließlich.

### Seite      {#page}

Die `Page` Komponente erweitert die `Container` Komponente. Ein Container ist eine Komponente, mit der untergeordnete Komponenten einschließlich untergeordneter Seiten enthalten und wiedergegeben werden sollen. Dazu durchläuft der Container die `:itemsOrder`, `:items`und `:children` Eigenschaften seines Modells. Die `Page` Komponente ruft die untergeordneten Komponenten dynamisch aus dem Speicher der [ComponentMapping](/help/sites-developing/spa-blueprint.md#componentmapping) -Bibliothek ab. Der `Page` ist für die Instanziierung untergeordneter Komponenten verantwortlich.

### Responsives Raster {#responsive-grid}

Die Komponente &quot;Responsive Grid&quot;ist ein Container. Es enthält eine bestimmte Variante des Modellanbieters, der seine Spalten darstellt. Das Responsive Raster und seine Spalten sind dafür verantwortlich, das äußere HTML-Element der Projektkomponente mit den spezifischen Klassennamen zu dekorieren, die im Modell enthalten sind.

Die Komponente &quot;Responsive Grid&quot;sollte ihrem AEM vorab zugeordnet werden, da diese Komponente komplex und selten angepasst ist.

#### Spezifische Modellfelder {#specific-model-fields}

* `gridClassNames:` Klassennamen für das interaktive Raster bereitgestellt
* `columnClassNames:` Klassennamen für die reagierende Spalte bereitgestellt

Siehe auch npm resource [@adobe/aem-response-editable-components#srccomponent-responsivegridjsx](https://www.npmjs.com/package/@adobe/aem-react-editable-components#srccomponentsresponsivegridjsx)

#### Platzhalter für das Reponsiv-Raster {#placeholder-of-the-reponsive-grid}

Die SPA-Komponente wird einem grafischen Container wie dem Responsive Grid zugeordnet und muss einen virtuellen untergeordneten Platzhalter hinzufügen, wenn der Inhalt erstellt wird. When the content of the SPA is being authored by the Page Editor, that content is embedded into the editor using an iframe and the `data-cq-editor` attribute is added to the document node of that content. Wenn das `data-cq-editor` Attribut vorhanden ist, muss der Container ein HTML-Element enthalten, das den Bereich darstellt, mit dem der Autor interagiert, wenn eine neue Komponente in die Seite eingefügt wird.

Beispiel:

```
<div data-cq-data-path={"path/to/the/responsivegrid/*"} className="new section aem-Grid-newComponent"/>
```

>[!NOTE]
>
>Die im Beispiel verwendeten Klassennamen werden zurzeit vom Seiten-Editor erfordert.
>
>* `"new section"`: Zeigt an, dass das aktuelle Element der Platzhalter des Containers ist
>* `"aem-Grid-newComponent"`: Normalisiert die Komponente für das Layout-Authoring

>



#### Komponentenzuordnung {#component-mapping}

Die zugrunde liegende [`Component Mapping`](/help/sites-developing/spa-blueprint.md#componentmapping) Bibliothek und ihre `MapTo` Funktion können verkapselt und erweitert werden, um die Funktionen im Verhältnis zur Bearbeitungskonfiguration, die neben der aktuellen Komponentenklasse bereitgestellt wird, bereitzustellen.

```
const EditConfig = {

    emptyLabel: 'My Component',

    isEmpty: function() {
        return !this.props || !this.props.cqModel || this.props.cqModel.isEmpty;
    }
};

class MyComponent extends Component {

    render() {
        return <div className={'my-component'}></div>;
    }
}

MapTo('component/resource/path')(MyComponent, EditConfig);
```

In der obigen Implementierung wird die Projektkomponente mit der Leere-Funktion erweitert, bevor sie im [Komponentenzuordnungsspeicher](/help/sites-developing/spa-blueprint.md#componentmapping) registriert wird. Dies geschieht durch Umkapseln und Erweitern der [`ComponentMapping`](/help/sites-developing/spa-blueprint.md#componentmapping) Bibliothek, um die Unterstützung des `EditConfig` Konfigurationsobjekts einzuführen:

```
/**
 * Configuration object in charge of providing the necessary data expected by the page editor to initiate the authoring. The provided data will be decorating the associated component
 *
 * @typedef {{}} EditConfig
 * @property {String} [dragDropName]       If defined, adds a specific class name enabling the drag and drop functionality
 * @property {String} emptyLabel           Label to be displayed by the placeholder when the component is empty. Optionally returns an empty text value
 * @property {function} isEmpty            Should the component be considered empty. The function is called using the context of the wrapper component giving you access to the component model
 */

/**
 * Map a React component with the given resource types. If an {@link EditConfig} is provided the <i>clazz</i> is wrapped to provide edition capabilities on the AEM Page Editor
 *
 * @param {string[]} resourceTypes                      - List of resource types for which to use the given <i>clazz</i>
 * @param {class} clazz                                 - Class to be instantiated for the given resource types
 * @param {EditConfig} [editConfig]                     - Configuration object for enabling the edition capabilities
 * @returns {class}                                     - The resulting decorated Class
 */
ComponentMapping.map = function map (resourceTypes, clazz, editConfig) {};
```

## Vertrag mit dem Seiten-Editor {#contract-with-the-page-editor}

Die Projektkomponenten müssen mindestens die folgenden Datenattribute generieren, damit der Editor mit ihnen interagieren kann.

* `data-cq-data-path`: Relativer Pfad der Komponente, wie er vom `PageModel` (z. B. `"root/responsivegrid/image"`) bereitgestellt wird. Dieses Attribut sollte Seiten nicht hinzugefügt werden.

Zusammenfassend muss eine Projektkomponente den folgenden Vertrag einhalten, damit sie vom Seiteneditor als bearbeitbar interpretiert werden kann:

* Geben Sie die erwarteten Attribute an, um eine Front-End-Komponenteninstanz einer AEM Ressource zuzuordnen.
* Stellen Sie die erwartete Folge von Attributen und Klassennamen bereit, die das Erstellen von leeren Platzhaltern ermöglicht.
* Stellen Sie die erwarteten Klassennamen bereit, die Drag-and-Drop von Assets ermöglichen.

### Typische Struktur für HTML-Elemente {#typical-html-element-structure}

Das folgende Fragment zeigt die typische HTML-Darstellung einer Seiteninhaltsstruktur. Hier einige wichtige Punkte:

* Das responsive Rasterelement überträgt Klassennamen mit dem Präfix `aem-Grid--`
* The responsive column element carries class names prefixed with `aem-GridColumn--`
* Ein interaktives Raster, das auch die Spalte eines übergeordneten Rasters ist, wird umschlossen, da die beiden vorherigen Präfixe nicht im selben Element angezeigt werden
* Elements corresponding to editable resources carry a `data-cq-data-path` property. Weitere Informationen finden Sie im Abschnitt [Vertrag mit dem Seiteneditor](#contract-wtih-the-page-editor) in diesem Dokument.

```
<div data-cq-data-path="/content/page">
    <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
        <div class="aem-container aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/content/page/jcr:content/root/responsivegrid">
            <div class="aem-Grid aem-Grid--12 aem-Grid--default--12">
                <div class="cmp-image cq-dd-image aem-GridColumn aem-GridColumn--default--12" data-cq-data-path="/root/responsivegrid/image">
                    <img src="/content/we-retail-spa-sample/react/jcr%3acontent/root/responsivegrid/image.img.jpeg/1512113734019.jpeg">
                </div>
            </div>
        </div>
    </div>
</div>
```

## Navigation und Routing {#navigation-and-routing}

Die App besitzt das Routing. Der Front-End-Entwickler muss zunächst eine Navigationskomponente implementieren (die einer AEM Navigationskomponente zugeordnet ist). Diese Komponente rendert URL-Links, die zusammen mit einer Reihe von Routen verwendet werden, die Fragmente von Inhalten ein- oder ausblenden.

Die zugrunde liegende [ Bibliothek und ihr `PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) ` [ModelRouter](/help/sites-developing/spa-routing.md)` Modul (standardmäßig aktiviert) sind für das Vorab-Abrufen und das Bereitstellen des Zugriffs auf das mit einem bestimmten Ressourcenpfad verknüpfte Modell verantwortlich.

Die beiden Entitäten beziehen sich auf den Begriff Routing, aber die ` [ModelRouter](/help/sites-developing/spa-routing.md)` ist nur dafür verantwortlich, dass das Modell mit einem Datenmodell ` [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager)` geladen wird, das mit dem aktuellen Anwendungsstatus synchronisiert ist.

Weitere Informationen finden Sie im Routing [SPA Model](/help/sites-developing/spa-routing.md) .

## SPA in Aktion {#spa-in-action}

Erfahren Sie, wie eine einfache SPA funktioniert, und experimentieren Sie selbst mit einer SPA, indem Sie mit dem Dokument [Erste Schritte mit SPAs in AEM](/help/sites-developing/spa-getting-started-react.md) fortfahren.

## Weiterführende Literatur {#further-reading}

Weitere Informationen zu SPAs in AEM finden Sie in den folgenden Dokumenten:

* [SPA-Authoring-Übersicht](/help/sites-developing/spa-overview.md) für einen Überblick über SPAs in AEM und das Kommunikationsmodell
* [Erste Schritte mit SPAs in AEM](/help/sites-developing/spa-getting-started-react.md) für einen Leitfaden zu einer einfachen SPA und wie sie funktioniert
