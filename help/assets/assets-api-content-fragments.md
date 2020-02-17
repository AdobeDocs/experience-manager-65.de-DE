---
title: Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API
seo-title: Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API
description: Erfahren Sie mehr über die Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API.
seo-description: Erfahren Sie mehr über die Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API.
uuid: c500d71e-ceee-493a-9e4d-7016745c544c
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: extending-assets
discoiquuid: 03502b41-b448-47ab-9729-e0a66a3389fa
docset: aem65
translation-type: tm+mt
source-git-commit: eb36f8fe6b08e03eb25e96ed1c31957f7d5aff27

---


# Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API{#content-fragments-support-in-aem-assets-http-api}

## Überblick {#overview}

>[!NOTE]
>
>Die [Assets-HTTP-API](/help/assets/mac-api-assets.md) umfasst:
>
>* Assets-REST-API
>* einschließlich Unterstützung für Inhaltsfragmente
>
>
Die aktuelle Implementierung der AEM Assets-HTTP-API ist REST.

The Adobe Experience Manager (AEM) [Assets REST API](/help/assets/mac-api-assets.md) allows developers to access content (stored in AEM) directly over the HTTP API, via CRUD operations (Create, Read, Update, Delete).

Die API ermöglicht es Ihnen, AEM als Headless-CMS (Content Management System) auszuführen, indem Sie einer Javascript-Frontend-Applikation Content Services bereitstellen. Oder jeder anderen Applikation, die HTTP-Anforderungen ausführen und JSON-Antworten verarbeiten kann.

Beispielsweise benötigen frameworkbasierte oder benutzerdefinierte Single-Page-Applikationen (SPA), die über die HTTP-API bereitgestellten Inhalte häufig im JSON-Format.

Die AEM-Core-Komponenten bieten eine sehr umfassende, flexible und anpassbare API, die für diesen Zweck erforderliche Lese-Vorgänge bereitstellen kann und deren JSON-Ausgabe angepasst werden kann. Für die Implementierung ist jedoch AEM WCM (Web Content Management)-Know-how erforderlich, da sie auf (API-)Seiten gehostet werden müssen, die auf dedizierten AEM-Vorlagen basieren. Nicht jede SPA-Entwicklungsorganisation hat Zugriff auf diese Ressourcen.

Hier kann die Assets-REST-API eingesetzt werden. Damit können Entwickler direkt auf Assets (z. B. Bilder und Inhaltsfragmente) zugreifen, ohne sie zuerst in eine Seite einzubetten, und ihre Inhalte im serialisierten JSON-Format bereitstellen. (Beachten Sie, dass Sie die JSON-Ausgabe nicht über die Assets-REST-API anpassen können). Mit der Assets-REST-API können Entwickler Inhalte ändern, indem sie neue Assets erstellen, aktualisieren oder vorhandene Assets, Inhaltsfragmente und Ordner löschen.

Die Assets-REST-API:

* folgt dem [HATEOAS-Prinzip](https://en.wikipedia.org/wiki/HATEOAS)

* implementiert das [SIREN-Format](https://github.com/kevinswiber/siren)

## Voraussetzungen {#prerequisites}

Die Assets-REST-API ist in jeder standardmäßigen Installation einer aktuellen AEM-Version verfügbar.

## Schlüsselkonzepte {#key-concepts}

Die Assets-REST-API bietet [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)-ähnlichen Zugriff auf Assets, die in einer AEM-Instanz gespeichert sind. It uses the `/api/assets` endpoint and requires the path of the asset to access it (without the leading `/content/dam`).

Die HTTP-Methode ermittelt den auszuführenden Vorgang:

* **GET** - zum Abrufen einer JSON-Darstellung eines Assets oder Ordners
* **POST** - zum Erstellen neuer Assets oder Ordner
* **PUT** - zum Aktualisieren der Eigenschaften eines Assets oder Ordners
* **LÖSCHEN** - Löschen eines Assets oder Ordners

>[!NOTE]
>
>Mit dem Anforderungstext und/oder den URL-Parametern können Sie einige dieser Vorgänge konfigurieren. Sie definieren damit beispielsweise, dass ein Ordner oder ein Asset über eine **POST**-Anforderung erstellt werden soll.

Das genaue Format der unterstützten Anforderungen ist in der [API-Referenzdokumentation](/help/assets/assets-api-content-fragments.md#api-reference) definiert.

### Transaktionsverhalten {#transactional-behavior}

Alle Anforderungen sind atomisch.

Dies bedeutet, dass die folgenden (`write`-)Anforderungen nicht in einer einzelnen Transaktion kombiniert werden können, die als einzelne Entität ausgeführt werden oder fehlschlagen könnte.

### AEM (Assets)-REST-API und AEM-Komponenten im Vergleich {#aem-assets-rest-api-versus-aem-components}

<table>
 <tbody>
  <tr>
   <td>Aspekt</td>
   <td>Assets-REST-API<br /> </td>
   <td>AEM-Komponente<br /> (Komponenten mit Sling-Modellen)</td>
  </tr>
  <tr>
   <td>Geeignete Nutzungsszenarien</td>
   <td>Universell.</td>
   <td><p>Optimiert für den Einsatz in einer Single-Page-Applikation (SPA) oder in einem beliebigen anderen Kontext (Inhalt verbrauchend).</p> <p>Kann auch Layoutinformationen enthalten.</p> </td>
  </tr>
  <tr>
   <td>Unterstützte Vorgänge</td>
   <td><p>Erstellen, Lesen, Aktualisieren, Löschen.</p> <p>Weitere Vorgänge abhängig von Entitätstyp.</p> </td>
   <td>Schreibgeschützt.</td>
  </tr>
  <tr>
   <td>Zugriff</td>
   <td><p>Direkter Zugriff möglich.</p> <p>Uses the <code>/api/assets </code>endpoint, mapped to <code>/content/dam</code> (in the repository).</p> <p><code class="code">
       /content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten</code><br /> So greifen Sie beispielsweise auf Folgendes zu: anfordern:<br /> <code>/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.model.json</code></p> </td>
   <td><p>Muss über eine AEM-Komponente auf einer AEM-Seite referenziert werden.</p> <p>Uses the <code>.model</code> selector to create the JSON representation.</p> <p>Eine Beispiel-URL würde wie folgt aussehen:<br /> <code>https://localhost:4502/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.model.json</code></p> </td>
  </tr>
  <tr>
   <td>Sicherheit</td>
   <td><p>Mehrere Optionen sind möglich.</p> <p>OAuth wird vorgeschlagen und kann separat von der obigen Standardeinrichtung konfiguriert werden.</p> </td>
   <td>Verwendet die oben beschriebene Standardeinrichtung von AEM.</td>
  </tr>
  <tr>
   <td>Anmerkungen zur Architektur</td>
   <td><p>Der Schreibzugriff gilt in der Regel für eine Autoreninstanz.</p> <p>Der Lesezugriff kann auch an eine Veröffentlichungsinstanz weitergeleitet werden.</p> </td>
   <td>Da dieser Vorgang schreibgeschützt ist, wird er in der Regel für Veröffentlichungsinstanzen verwendet.</td>
  </tr>
  <tr>
   <td>Ausgabe</td>
   <td>JSON-basierte SIREN-Ausgabe: ausführlich, aber leistungsstark. Ermöglicht die Navigation innerhalb des Inhalts.</td>
   <td>JSON-basierte proprietäre Ausgabe über Sling-Modelle konfigurierbar. Die Navigation durch die Inhaltsstruktur ist schwer zu implementieren (jedoch nicht unmöglich).</td>
  </tr>
 </tbody>
</table>

### Sicherheit {#security}

Wenn die Assets-REST-API in einer Umgebung ohne spezifische Authentifizierungsanforderungen verwendet wird, muss der CORS-Filter von AEM richtig konfiguriert werden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* [Erklärung: CORS/AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html) 
>* [Video: Entwicklung für CORS mit AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
>



In Umgebungen mit bestimmten Authentifizierungsanforderungen wird OAuth empfohlen.

## Verfügbare Funktionen {#available-features}

Inhaltsfragmente sind eine bestimmte Art von Assets. Informationen finden Sie unter [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments.md).

Weitere Informationen zu den über die APIs verfügbaren Funktionen:

* [Verfügbare Funktionen](/help/assets/mac-api-assets.md#available-features) der Assets-REST-API
* [Entitätstypen](/help/assets/assets-api-content-fragments.md#entity-types)

### Paging {#paging}

Die Assets-REST-API unterstützt Paging (für GET-Anforderungen) über die URL-Parameter:

* `offset` - die Nummer der ersten abzurufenden (untergeordneten) Entität
* `limit` - die maximale Anzahl zurückgegebener Entitäten

The response will contain paging information as part of the `properties` section of the SIREN output. This `srn:paging` property contains the total number of (child) entities ( `total`), the offset and the limit ( `offset`, `limit`) as specified in the request.

>[!NOTE]
>
>Paging wird normalerweise auf Containerentitäten (d. h. Ordner oder Assets mit Ausgabeformaten) angewendet, da sie auf die untergeordneten Objekte des angeforderten Elements verweisen.

#### Beispiel: Paging {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```
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

## Entitätstypen {#entity-types}

### Ordner {#folders}

Ordner dienen als Container für Assets und andere Ordner. Ihre Struktur entspricht den Inhaltsrepositorys von AEM.

Die Assets-REST-API gewährt Zugriff auf die Eigenschaften eines Ordners, z. B. Name, Titel, usw. Assets werden als untergeordnete Entitäten von Ordnern bereitgestellt.

>[!NOTE]
>
>Je nach Asset-Typ enthält die Liste der untergeordneten Entitäten möglicherweise bereits die gesamten Eigenschaften, die die untergeordnete Entität definieren. Alternativ werden einer Entität in dieser Liste der untergeordneten Entitäten möglicherweise nicht alle Eigenschaften bereitgestellt.

### Assets {#assets}

Wenn ein Asset angefordert wird, gibt die Antwort die Metadaten (z. B. Titel, Name und andere Informationen) wie vom entsprechenden Assets-Schema definiert zurück.

The binary data of an asset is exposed as a SIREN link of type `content` (also known as the `rel attribute`).

Assets können mehrere Ausgabeformate aufweisen. These are typically exposed as child entities, one exception being a thumbnail rendition, which is exposed as a link of type `thumbnail` ( `rel="thumbnail"`).

### Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments.md) ist ein spezieller Asset-Typ. Sie können zum Zugriff auf strukturierte Daten wie Texte, Zahlen, Daten usw. verwendet werden.

Da es einige Unterschiede zu *Standard*-Assets (z. B. Bildern oder Audio) aufweist, gelten einige zusätzliche Regeln für die Verarbeitung.

#### Darstellung {#representation}

Inhaltsfragmente:

* stellen keine Binärdaten bereit.
* Are completely contained in the JSON output (within the `properties` property).

* Gelten auch als atomisch, d. h. die Elemente und Varianten werden als Teil der Eigenschaften des Fragments anstatt als Links oder untergeordnete Entitäten bereitgestellt. Dies ermöglicht einen effiziente Zugriff auf die Nutzlast eines Fragments.

#### Inhaltsmodelle und Inhaltsfragmente {#content-models-and-content-fragments}

Derzeit werden die Modelle, die die Struktur eines Inhaltsfragments definieren, nicht über eine HTTP-API bereitgestellt. Daher benötigt der *Benutzer* (zumindest einige) Informationen über das Modell eines Fragments. Die meisten Informationen kann er jedoch aus der Nutzlast ableiten. So sind z. B. Datentypen Teil der Definition.

Zum Erstellen eines neuen Inhaltsfragments muss der Pfad (des internen Repositorys) angegeben werden.

#### Zugehörige Inhalte {#associated-content}

Zugehöriger Inhalt wird derzeit nicht bereitgestellt.

## Verwendung {#using}

Die Verwendung unterscheidet sich je nachdem, ob Sie eine AEM-Autoren- oder Veröffentlichungsumgebung zusammen mit Ihrem spezifischen Verwendungsszenario verwenden.

* Die Erstellung ist nur in einer Autoreninstanz möglich ([und derzeit gibt es keine Möglichkeit, ein Fragment mit dieser API für die Veröffentlichungsinstanz zu replizieren](/help/assets/assets-api-content-fragments.md#limitations)). 
* Die Bereitstellung ist in beiden Umgebungen möglich, da AEM angeforderte Inhalte nur im JSON-Format bereitstellt.

   * Das Speichern und Bereitstellen über eine AEM-Autoreninstanz sollte für Mediathekanwendungen hinter einer Firewall ausreichen.
   * Für die Live-Web-Bereitstellung wird eine AEM-Veröffentlichungsinstanz empfohlen.

>[!CAUTION]
>
>Die Dispatcher-Konfiguration auf AEM-Cloudinstanzen blockiert möglicherweise den Zugriff auf `/api`.

>[!NOTE]
>
>Weitere Informationen finden Sie in der [API-Referenz](/help/assets/assets-api-content-fragments.md#api-reference). Besonders interessant: [Adobe Experience Manager Assets API – Inhaltsfragmente](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html).

### Lesen/Bereitstellen {#read-delivery}

Nutzung erfolgt über:

`GET /{cfParentPath}/{cfName}.json`

Beispiel:

`https://localhost:4502/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.json`

Die Antwort ist serialisierter JSON mit dem im Inhaltsfragment strukturierten Inhalt. Verweise werden als Referenz-URLs bereitgestellt. 

Zwei Arten von Lesevorgängen sind möglich:

* Beim Lesen eines spezifischen Inhaltsfragments über einen Pfad gibt diese Methode die JSON-Darstellung des Inhaltsfragments zurück. 
* Ordner mit Inhaltsfragmenten nach Pfad lesen: gibt die JSON-Darstellungen aller Inhaltsfragmente im Ordner zurück.

### Erstellen {#create}

Nutzung erfolgt über:

`POST /{cfParentPath}/{cfName}`

Der Hauptteil muss eine JSON-Darstellung des zu erstellenden Inhaltsfragments enthalten – einschließlich des anfänglichen Inhalts, der für Inhaltsfragmentelemente festgelegt werden soll. It is mandatory to set the `cq:model` property and it must point to a valid content fragment model. Andernfalls tritt ein Fehler auf. It is also necessary to add a header `Content-Type` which is set to `application/json`.

### Update {#update}

Nutzung erfolgt über

`PUT /{cfParentPath}/{cfName}`

Der Hauptteil muss eine JSON-Darstellung davon enthalten, was für das angegebene Inhaltsfragment aktualisiert werden soll.

Dies kann einfach der Titel oder die Beschreibung eines Inhaltsfragments bzw. ein einzelnes Element oder alle Elementwerte und/oder Metadaten sein. It is also mandatory to provide a valid `cq:model` property for updates.

### Löschen {#delete}

Nutzung erfolgt über:

`DELETE /{cfParentPath}/{cfName}`

## Beschränkungen {#limitations}

Es gibt einige Einschränkungen: 

* **Varianten können weder geschrieben noch aktualisiert werden.** Werden diese Varianten einer Nutzlast hinzugefügt (z. B. für Aktualisierungen), werden sie ignoriert. Jedoch ist die Variante über die Bereitstellung verfügbar ( `GET`).

* **Inhaltsfragmentmodelle werden derzeit nicht unterstützt**: sie können weder gelesen noch erstellt werden. Zum Erstellen eines neuen oder Aktualisieren eines vorhandenen Inhaltsfragments müssen Entwickler den richtigen Pfad zum Inhaltsfragmentmodell kennen. Derzeit ist dies lediglich über die Verwaltungsoberfläche möglich. 
* **Verweise werden ignoriert**. Zurzeit sind keine Überprüfungen für Verweise auf vorhandene Inhaltsfragmente verfügbar. Wenn Sie beispielsweise ein Inhaltsfragment löschen, treten möglicherweise Probleme auf einer Seite auf, die einen Verweis enthält.

## Statuscodes und Fehlermeldungen {#status-codes-and-error-messages}

Unter den entsprechenden Voraussetzungen werden möglicherweise die folgenden Statuscodes angezeigt:

1. 202 (OK)

   Wird zurückgegeben, wenn:

   * requesting a content fragment via `GET`

   * successfully updating a content fragment via `PUT`

1. 201 (Erstellt)

   Wird zurückgegeben, wenn:

   * successfully creating a content fragment via `POST`

1. 404 (Nicht gefunden)

   Wird zurückgegeben, wenn:

   * das angeforderte Inhaltsfragment nicht vorhanden ist

1. 500 (Interner Serverfehler)

   >[!NOTE]
   >
   >Dieser Fehler wird zurückgegeben:
   >
   >
   >
   >    * wenn ein Fehler, der mit keinem bestimmten Code identifiziert werden kann, aufgetreten ist 
   >    * wenn als Nutzlast „null“ angegeben ist


   Nachfolgend finden Sie allgemeine Szenarien, in denen dieser Fehlerstatus in Kombination mit der Fehlermeldung (monospace) zurückgegeben wird:

   * Übergeordneter Ordner ist nicht vorhanden (wenn ein Inhaltsfragment per `POST` erstellt wurde)
   * Kein Inhaltsfragmentmodell bereitgestellt (Null-Wert), Ressource ist ungültig (mögliches Berechtigungsproblem) oder die Ressource ist keine gültige Fragmentvorlage:

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`
      * `Cannot adapt the resource '/foo/bar/qux' to a content fragment template`
   * Das Inhaltsfragment konnte nicht erstellt werden (möglicherweise ein Berechtigungsproblem):

      * `Could not create content fragment`
   * Titel oder Beschreibung und konnte nicht aktualisiert werden:

      * `Could not set value on content fragment`
   * Metadaten konnten nicht festgelegt werden:

      * `Could not set metadata on content fragment`
   * Inhaltselement wurde nicht gefunden oder konnte nicht aktualisiert werden

      * `Could not update content element`
      * `Could not update fragment data of element`
   Die detaillierten Fehlermeldungen werden im Allgemeinen im folgenden Typ zurückgegeben:

   ```xml
   {
     "class": "core/response",
     "properties": {
       "path": "/api/assets/foo/bar/qux",
       "location": "/api/assets/foo/bar/qux.json",
       "parentLocation": "/api/assets/foo/bar.json",
       "status.code": 500,
       "status.message": "...{error message}.."
     }
   }
   ```

## API-Referenz {#api-reference}

Hier finden Sie detaillierte API-Referenzen:

* [Adobe Experience Manager Assets API – Inhaltsfragmente](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)

   * [Verfügbare Funktionen](/help/assets/mac-api-assets.md#available-features)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen finden Sie unter:

* [Assets-HTTP-API – Dokumentation ](/help/assets/mac-api-assets.md)
* [AEM Gem-Sitzung: OAuth](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html) 

