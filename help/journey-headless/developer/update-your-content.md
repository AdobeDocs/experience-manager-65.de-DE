---
title: Aktualisieren Ihres Inhalts über AEM Assets-APIs
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie, wie Sie mit der REST-API auf die Inhalte Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können.
source-git-commit: 7f43d9d6b631b26f7b9293aa109498d0c8040436
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 93%

---

# Aktualisieren Ihres Inhalts über AEM Assets-APIs {#update-your-content}

In diesem Teil der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie Sie mit der REST-API auf die Inhalte Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Headless-Tour, [Zugriff auf Ihre Inhalte über AEM-Bereitstellungs-APIs](access-your-content.md) haben Sie erfahren, wie Sie über die AEM-GraphQL-API auf Ihre Headless-Inhalte in AEM zugreifen können. Nun sollten Sie:

* über ein hohes Maß an Verständnis von GraphQL verfügen,
* verstehen, wie die AEM-GraphQL-API funktioniert,
* einige praktische Beispielabfragen verstehen.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie Ihre vorhandenen Headless-Inhalte in AEM über die REST-API aktualisieren können.

## Ziel {#objective}

* **Zielgruppe**: Fortgeschrittene
* **Ziele**: Sie erfahren, wie Sie mit der REST-API auf die Inhalte Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können:
   * Einführung in die AEM Assets-HTTP-API.
   * Einführung und Diskussion der Unterstützung von Inhaltsfragmenten in der API.
   * Veranschaulichende Details zur API.

<!--
  * Look at sample code to see how things work in practice.
-->

## Warum Sie die Assets-HTTP-API für Inhaltsfragmente benötigen {#why-http-api}

Im vorherigen Teil der Headless-Tour haben Sie erfahren, wie Sie mit der AEM-GraphQL-API Inhalte mithilfe von Abfragen abrufen können.

Warum ist also eine weitere API erforderlich?

Die Assets-HTTP-API ermöglicht nicht nur das **Lesen** Ihrer Inhalte, sondern auch das **Erstellen**, **Aktualisieren** und **Löschen** von Inhalten – Aktionen, die mit der GraphQL-API nicht möglich sind.

Die Assets-REST-API ist bei jeder nativen Installation einer aktuellen Adobe Experience Manager-Version verfügbar.

## Assets-HTTP-API {#assets-http-api}

Die Assets-HTTP-API umfasst die:

* Assets-REST-API
* einschließlich Unterstützung für Inhaltsfragmente

Die aktuelle Implementierung der Assets-HTTP-API basiert auf dem Architekturstil **REST** und ermöglicht den Zugriff auf (in AEM gespeicherte) Inhalte über **CRUD**-Vorgänge (Create, Read, Update, Delete, also Erstellen, Lesen, Aktualisieren, Löschen).

Mit diesem Vorgang ermöglicht Ihnen die API den Betrieb von Adobe Experience Manager als Headless-CMS (Content Management System) durch Bereitstellung von Content Services für eine JavaScript-Frontend-Anwendung. Oder jedem anderen Programm, das HTTP-Anfragen ausführen und JSON-Antworten verarbeiten kann. Beispielsweise benötigen Framework-basierte oder benutzerdefinierte Single Page Applications (SPAs) die über die API bereitgestellten Inhalte häufig im JSON-Format.

<!--
>[!NOTE]
>
>It is not possible to customize JSON output from the Assets REST API. 

The Assets REST API:

* follows the HATEOAS principle
* implements the SIREN format

## Key Concepts {#key-concepts}

The Assets REST API offers REST-style access to assets stored within an AEM instance. 

It uses the `/api/assets` endpoint and requires the path of the asset to access it (without the leading `/content/dam`). 

* This means that to access the asset at:
  * `/content/dam/path/to/asset`
* You need to request:
  * `/api/assets/path/to/asset` 

For example, to access `/content/dam/wknd/en/adventures/cycling-tuscany`, request `/api/assets/wknd/en/adventures/cycling-tuscany.json` 

>[!NOTE]
>Access over:
>
>* `/api/assets` **does not** need the use of the `.model` selector.
>* `/content/path/to/page` **does** require the use of the `.model` selector.

The HTTP method determines the operation to be executed:

* **GET** - to retrieve a JSON representation of an asset or a folder
* **POST** - to create new assets or folders
* **PUT** - to update the properties of an asset or folder
* **DELETE** - to delete an asset or folder

>[!NOTE]
>
>The request body and/or URL parameters can be used to configure some of these operations; for example, define that a folder or an asset should be created by a **POST** request.

The exact format of supported requests is defined in the API Reference documentation. 

### Transactional Behavior {#transactional-behavior}

All requests are atomic.

This means that subsequent (`write`) requests cannot be combined into a single transaction that could succeed or fail as a single entity.

### Security {#security}

If the Assets REST API is used within an environment without specific authentication requirements, AEM's CORS filter needs to be configured correctly.

>[!NOTE]
>
>For further information see:
>
>* CORS/AEM explained
>* Video - Developing for CORS with AEM

In environments with specific authentication requirements, OAuth is recommended.

## Available Features {#available-features}

Content Fragments are a specific type of Asset, see Working with Content Fragments.

For further information about features available through the API see:

* The Assets REST API (Additional Resources) 
* Entity Types, where the features specific to each supported type (as relevant to Content Fragments) are explained 

### Paging {#paging}

The Assets REST API supports paging (for GET requests) via the URL parameters:

* `offset` - the number of the first (child) entity to retrieve
* `limit` - the maximum number of entities returned

The response will contain paging information as part of the `properties` section of the SIREN output. This `srn:paging` property contains the total number of (child) entities ( `total`), the offset and the limit ( `offset`, `limit`) as specified in the request.

>[!NOTE]
>
>Paging is typically applied on container entities (i.e. folders or assets with renditions), as it relates to the children of the requested entity.

#### Example: Paging {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```json
...
"properties": {
    ...
    "srn:paging": {
        "total": 7,
        "offset": 2,
        "limit": 3
    }
    ...
}
...
```

## Entity Types {#entity-types}

### Folders {#folders}

Folders act as containers for assets and other folders. They reflect the structure of the AEM content repository.

The Assets REST API exposes access to the properties of a folder; for example its name, title, etc. Assets are exposed as child entities of folders, and sub-folders.

>[!NOTE]
>
>Depending on the asset type of the child assets and folders the list of child entities may already contain the full set of properties that defines the respective child entity. Alternatively, only a reduced set of properties may be exposed for an entity in this list of child entities.

### Assets {#assets}

If an asset is requested, the response will return its metadata; such as title, name and other information as defined by the respective asset schema.

The binary data of an asset is exposed as a SIREN link of type `content`.

Assets can have multiple renditions. These are typically exposed as child entities, one exception being a thumbnail rendition, which is exposed as a link of type `thumbnail` ( `rel="thumbnail"`).
-->

## Assets-HTTP-API und Inhaltsfragmente {#assets-http-api-content-fragments}

Inhaltsfragmente werden für die Headless-Bereitstellung verwendet. Ein Inhaltsfragment ist ein spezieller Asset-Typ. Sie können für den Zugriff auf strukturierte Daten wie z. B. Texte, Zahlen und Daten verwendet werden.

<!--
As there are several differences to *standard* assets (such as images or audio), some additional rules apply to handling them.

### Representation {#representation}

Content fragments:

* Do not expose any binary data.
* Are completely contained in the JSON output (within the `properties` property).

* Are also considered atomic, i.e. the elements and variations are exposed as part of the fragment's properties vs. as links or child entities. This allows for efficient access to the payload of a fragment.

### Content Models and Content Fragments {#content-models-and-content-fragments}

Currently the models that define the structure of a content fragment are not exposed through an HTTP API. Therefore the *consumer* needs to know about the model of a fragment (at least a minimum) - although most information can be inferred from the payload; as data types, etc. are part of the definition.

To create a new content fragment, the (internal repository) path of the model has to be provided.

### Associated Content {#associated-content}

Associated content is currently not exposed.
-->

## Verwenden der Assets REST-API {#using-aem-assets-rest-api}

### Zugriff {#access}

Die Assets REST-API verwendet den `/api/assets`-Endpunkt und benötigt für den Zugriff auf das Asset dessen Pfad (ohne das Präfix `/content/dam`).

* Das bedeutet, dass Sie für den Zugriff auf das Asset unter
   * `/content/dam/path/to/asset`
* Folgendes anfordern müssen:
   * `/api/assets/path/to/asset`

Um beispielsweise auf `/content/dam/wknd/en/adventures/cycling-tuscany`zuzugreifen, fordern Sie `/api/assets/wknd/en/adventures/cycling-tuscany.json` an.

>[!NOTE]
>Der Zugriff über:
>
>* `/api/assets` **erfordert keine** Verwendung des `.model`-Selektors.
>* `/content/path/to/page` **erfordert** die Verwendung des `.model`-Selektors.


### Vorgang {#operation}

Die HTTP-Methode ermittelt den auszuführenden Vorgang:

* **GET**: Zum Abrufen einer JSON-Darstellung eines Assets bzw. Ordners
* **POST**: Zum Erstellen neuer Assets oder Ordner
* **PUT**: Zum Aktualisieren der Eigenschaften eines Assets oder Ordners
* **DELETE**: Zum Löschen eines Assets oder Ordners

>[!NOTE]
>
>Mit dem Anfragetext und/oder den URL-Parametern können Sie einige dieser Vorgänge konfigurieren. Sie definieren damit beispielsweise, dass ein Ordner oder ein Asset über eine **POST**-Anfrage erstellt werden soll.

Das genaue Format der unterstützten Anforderungen ist in der API-Referenzdokumentation definiert.

Die Verwendung unterscheidet sich je nachdem, ob Sie eine AEM-Autoren- oder Veröffentlichungsumgebung zusammen mit Ihrem spezifischen Verwendungsszenario verwenden.

* Es wird dringend empfohlen, dass die Erstellung in einer Autoreninstanz erfolgt (und derzeit gibt es keine Möglichkeit, ein Fragment mit dieser API für die Veröffentlichungsinstanz zu replizieren).
* Die Bereitstellung ist in beiden Umgebungen möglich, da AEM angeforderte Inhalte nur im JSON-Format bereitstellt.

   * Das Speichern und Bereitstellen über eine AEM-Autoreninstanz sollte für Mediathekanwendungen hinter einer Firewall ausreichen.

   * Für die Live-Web-Bereitstellung wird eine AEM-Veröffentlichungsinstanz empfohlen.

>[!CAUTION]
>
>Die Dispatcher-Konfiguration auf AEM Instanzen blockiert möglicherweise den Zugriff auf `/api`.

>[!NOTE]
>
>Weitere Informationen finden Sie in der API-Referenz. Besonders interessant: [Adobe Experience Manager Assets API – Inhaltsfragmente](https://www.adobe.io/experience-manager/reference-materials/6-5/assets-api-content-fragments/index.html).

### Lesen/Bereitstellen {#read-delivery}

Nutzung erfolgt über:

`GET /{cfParentPath}/{cfName}.json`

Beispiel:

`http://<host>/api/assets/wknd/en/adventures/cycling-tuscany.json`

Die Antwort ist serialisiertes JSON mit dem im Inhaltsfragment strukturierten Inhalt. Verweise werden als Referenz-URLs bereitgestellt.

Zwei Arten von Lesevorgängen sind möglich:

* Beim Lesen eines spezifischen Inhaltsfragments über einen Pfad gibt diese Methode die JSON-Darstellung des Inhaltsfragments zurück.
* Beim Lesen eines Ordners mit Inhaltsfragmenten über einen Pfad gibt diese Methode die JSON-Darstellung aller Inhaltsfragmente in diesem Ordner zurück.

### Erstellen {#create}

Nutzung erfolgt über:

`POST /{cfParentPath}/{cfName}`

Der Hauptteil muss eine JSON-Darstellung des zu erstellenden Inhaltsfragments enthalten – einschließlich des anfänglichen Inhalts, der für Inhaltsfragmentelemente festgelegt werden soll. Sie müssen die Eigenschaft `cq:model` festlegen und auf ein gültiges Inhaltsfragmentmodell verweisen. Andernfalls tritt ein Fehler auf. Außerdem müssen Sie eine Kopfzeile vom Typ `Content-Type` hinzufügen, für die `application/json` festgelegt ist.

### Aktualisieren {#update}

Nutzung erfolgt über

`PUT /{cfParentPath}/{cfName}`

Der Hauptteil muss eine JSON-Darstellung davon enthalten, was für das angegebene Inhaltsfragment aktualisiert werden soll.

Dies kann einfach der Titel oder die Beschreibung eines Inhaltsfragments bzw. ein einzelnes Element oder alle Elementwerte und/oder Metadaten sein.

### Löschen {#delete}

Nutzung erfolgt über:

`DELETE /{cfParentPath}/{cfName}`

Weitere Informationen zur Verwendung der AEM Assets REST-API finden Sie unter:

* Adobe Experience Manager Assets-HTTP-API (Zusätzliche Ressourcen)
* Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API (Zusätzliche Ressourcen)

## Wie geht es weiter {#whats-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Tour abgeschlossen haben, sollten Sie über die folgenden Kenntnisse verfügen:

* die Grundlagen der AEM Assets-HTTP-API verstehen,
* verstehen, wie Inhaltsfragmente in dieser API unterstützt werden.

<!--
* Have experience with sample code and know how the API works in practice.
-->

<!-- The "How to put it all together" page isn't going to be published until the first public release of the Headless SDK. Temporarily commenting out the reference below. -->

<!--You should continue your AEM headless journey by next reviewing the document [How to Put It All Together - Your App and Your Content in AEM Headless](put-it-all-together.md) where you learn how to take your AEM Headless project and prepare it for going live.-->

Sie sollten Ihre AEM Headless-Tour fortsetzen, indem Sie sich das Dokument [So gehen Sie mit Ihrer Headless-Anwendung live](go-live.md) ansehen, in dem Sie mit Ihrem AEM Headless-Projekt tatsächlich live gehen.

## Zusätzliche Ressourcen {#additional-resources}

* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Inhaltsfragment-REST-API](/help/assets/assets-api-content-fragments.md)
   * [API-Referenz](/help/assets/assets-api-content-fragments.md#api-reference)
* [Adobe Experience Manager Assets API – Inhaltsfragmente](https://www.adobe.io/experience-manager/reference-materials/6-5/assets-api-content-fragments/index.html)
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
* [AEM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
* [Erklärung: CORS/AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [Video: Entwicklung für CORS mit AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
