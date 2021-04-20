---
title: 'Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API '
seo-title: 'Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API '
description: Erfahren Sie mehr über die Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API.
seo-description: Erfahren Sie mehr über die Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API.
uuid: c500d71e-ceee-493a-9e4d-7016745c544c
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: extending-assets
discoiquuid: 03502b41-b448-47ab-9729-e0a66a3389fa
docset: aem65
feature: Content Fragments
role: Business Practitioner, Administrator
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '1864'
ht-degree: 94%

---


# Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API {#content-fragments-support-in-aem-assets-http-api}

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

Die Adobe Experience Manager (AEM) [Assets REST API](/help/assets/mac-api-assets.md) ermöglicht es Entwicklern, über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen) direkt auf AEM Inhalte zuzugreifen.

Die API ermöglicht es Ihnen, AEM als Headless-CMS (Content Management System) auszuführen, indem Sie einer Javascript-Frontend-Applikation Content Services bereitstellen. Oder jedem anderen Programm, das HTTP-Anfragen ausführen und JSON-Antworten verarbeiten kann.

Beispielsweise benötigen Framework-basierte oder benutzerdefinierte Single Page Applications (SPA), die über die HTTP-API bereitgestellten Inhalte häufig im JSON-Format.

AEM Core-Komponenten bieten eine sehr umfassende, flexible und anpassbare API, die für diesen Zweck erforderliche Read-Vorgänge bereitstellen kann und deren JSON-Ausgabe angepasst werden kann. Sie erfordern jedoch AEM WCM (Web-Content-Management)-Know-how für die Implementierung, da sie auf (API-)Seiten gehostet werden müssen, die auf dedizierten AEM-Vorlagen basieren. Nicht jede SPA-Entwicklungsorganisation hat Zugriff auf diese Ressourcen.

Hier kann die Assets-REST-API eingesetzt werden. Damit können Entwickler direkt auf Assets (z. B. Bilder und Inhaltsfragmente) zugreifen, ohne sie zuerst in eine Seite einzubetten, und ihre Inhalte im serialisierten JSON-Format bereitstellen. (Beachten Sie, dass Sie die JSON-Ausgabe nicht über die Assets-REST-API anpassen können). Mit der Assets-REST-API können Entwickler Inhalte ändern, indem sie neue Assets, Inhaltsfragmente und Ordner erstellen, aktualisieren oder vorhandene Assets, Inhaltsfragmente und Ordner löschen.

Die Assets-REST-API:

* folgt dem [HATEOAS-Prinzip](https://de.wikipedia.org/wiki/HATEOAS)

* implementiert das [SIREN-Format](https://github.com/kevinswiber/siren)

## Voraussetzungen {#prerequisites}

Die Assets-REST-API ist in jeder standardmäßigen Installation einer aktuellen AEM-Version verfügbar.

## Schlüsselkonzepte {#key-concepts}

Die Assets-REST-API bietet [REST](https://de.wikipedia.org/wiki/Representational_State_Transfer)-ähnlichen Zugriff auf Assets, die in einer AEM-Instanz gespeichert sind. Sie verwendet den `/api/assets`-Endpunkt und benötigt für den Zugriff auf das Asset dessen Pfad (ohne das Präfix `/content/dam`).

Die HTTP-Methode ermittelt den auszuführenden Vorgang:

* **GET**: Zum Abrufen einer JSON-Darstellung eines Assets bzw. Ordners
* **POST**: Zum Erstellen neuer Assets oder Ordner
* **PUT**: Zum Aktualisieren der Eigenschaften eines Assets oder Ordners
* **DELETE**: Zum Löschen eines Assets oder Ordners

>[!NOTE]
>
>Mit dem Anfragetext und/oder den URL-Parametern können Sie einige dieser Vorgänge konfigurieren. Sie definieren damit beispielsweise, dass ein Ordner oder ein Asset über eine **POST**-Anfrage erstellt werden soll.

Das genaue Format der unterstützten Anforderungen ist in der [API-Referenzdokumentation](/help/assets/assets-api-content-fragments.md#api-reference) definiert.

### Transaktionsverhalten {#transactional-behavior}

Alle Anfragen sind atomisch.

Dies bedeutet, dass die folgenden (`write`)-Anfragen nicht in einer einzelnen Transaktion kombiniert werden können, die als einzelne Entität ausgeführt werden oder fehlschlagen könnte.

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
   <td><p>Optimiert für den Einsatz in einer Single Page Application (SPA) oder in einem beliebigen anderen Kontext (Inhalt verbrauchend).</p> <p>Kann auch Layoutinformationen enthalten.</p> </td>
  </tr>
  <tr>
   <td>Unterstützte Vorgänge</td>
   <td><p>Erstellen, Lesen, Aktualisieren, Löschen.</p> <p>Weitere Vorgänge abhängig von Entitätstyp.</p> </td>
   <td>Schreibgeschützt.</td>
  </tr>
  <tr>
   <td>Zugriff</td>
   <td><p>Direkter Zugriff möglich.</p> <p>Verwendet den Endpunkt <code>/api/assets </code> und ist <code>/content/dam</code> zugeordnet (im Repository).</p> <p>So greifen Sie beispielsweise auf Folgendes zu:<code class="code">
       /content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten</code><br /><br /> <code>/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.model.json</code></p> </td>
   <td><p>Muss über eine AEM-Komponente auf einer AEM-Seite referenziert werden.</p> <p>Verwendet den Selektor <code>.model</code>, um die JSON-Darstellung zu erstellen.</p> <p>Eine Beispiel-URL würde wie folgt aussehen:<br /> <code>https://localhost:4502/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.model.json</code></p> </td>
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
>* [Erklärung: CORS/AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
>* [Video: Entwicklung für CORS mit AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

>



In Umgebungen mit bestimmten Authentifizierungsanforderungen wird OAuth empfohlen.

## Verfügbare Funktionen {#available-features}

Inhaltsfragmente sind eine bestimmte Art von Assets. Informationen finden Sie unter [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md).

Weitere Informationen zu den über die APIs verfügbaren Funktionen:

* [Verfügbare Funktionen](/help/assets/mac-api-assets.md#assets) der Assets-REST-API
* [Entitätstypen](/help/assets/assets-api-content-fragments.md#entity-types)

### Paging {#paging}

Die Assets-REST-API unterstützt Paging (für GET-Anfragen) über die URL-Parameter:

* `offset`: Die Nummer der ersten (untergeordneten) Entität, die abgerufen werden soll
* `limit`: Die maximale Anzahl von zurückgegebenen Entitäten.

Die Antwort enthält Paging-Informationen im Bereich `properties` der SIREN-Ausgabe. Diese Eigenschaft `srn:paging` enthält die Gesamtzahl der (untergeordneten) Entitäten (`total`), den Offset und das Limit ( `offset`, `limit`), wie in der Anfrage angegeben.

>[!NOTE]
>
>Paging wird normalerweise auf Container-Entitäten (d. h. Ordner oder Assets mit Ausgabedarstellungen) angewendet, da sie auf die untergeordneten Objekte des angeforderten Elements verweisen.

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

Die Binärdaten eines Assets werden als SIREN-Link vom Typ `content` bereitgestellt (auch als `rel attribute` bekannt).

Assets können mehrere Ausgabeformate aufweisen. Diese werden in der Regel als untergeordnete Entitäten bereitgestellt. Eine Ausnahme stellt die Ausgabedarstellung der Miniaturansichten dar, die als Link vom Typ `thumbnail` (`rel="thumbnail"`) bereitgestellt wird.

### Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) ist ein spezieller Asset-Typ. Es kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.

Da es einige Unterschiede zu *Standard*-Assets (z. B. Bildern oder Audio) aufweist, gelten einige zusätzliche Regeln für die Verarbeitung.

#### Darstellung  {#representation}

Inhaltsfragmente:

* stellen keine Binärdaten bereit.
* sind vollständig in der JSON-Ausgabe enthalten (innerhalb der Eigenschaft `properties`).

* Gelten auch als atomisch, d. h. die Elemente und Varianten werden als Teil der Eigenschaften des Fragments anstatt als Links oder untergeordnete Entitäten bereitgestellt. Dies ermöglicht einen effiziente Zugriff auf die Payload eines Fragments.

#### Inhaltsmodelle und Inhaltsfragmente   {#content-models-and-content-fragments}

Derzeit werden die Modelle, die die Struktur eines Inhaltsfragments definieren, nicht über eine HTTP-API bereitgestellt. Daher benötigt der *Benutzer* (zumindest einige) Informationen über das Modell eines Fragments. Die meisten Informationen kann er jedoch aus der Payload ableiten. So sind z. B. Datentypen Teil der Definition.

Zum Erstellen eines neuen Inhaltsfragments muss der Pfad (des internen Repositorys) angegeben werden.

#### Zugehörige Inhalte {#associated-content}

Zugehöriger Inhalt wird derzeit nicht bereitgestellt.

## Verwenden {#using}

Die Verwendung unterscheidet sich je nachdem, ob Sie eine AEM-Autoren- oder Veröffentlichungsumgebung zusammen mit Ihrem spezifischen Verwendungsszenario verwenden.

* Die Erstellung ist nur in einer Autoreninstanz möglich ([und derzeit gibt es keine Möglichkeit, ein Fragment mit dieser API für die Veröffentlichungsinstanz zu replizieren](/help/assets/assets-api-content-fragments.md#limitations)). 
* Die Bereitstellung ist in beiden Umgebungen möglich, da AEM angeforderte Inhalte nur im JSON-Format bereitstellt.

   * Das Speichern und Bereitstellen über eine AEM-Autoreninstanz sollte für Mediathekanwendungen hinter einer Firewall ausreichen.
   * Für die Live-Web-Bereitstellung wird eine AEM-Veröffentlichungsinstanz empfohlen.

>[!CAUTION]
>
>Die Dispatcher-Konfiguration auf AEM-Cloud-Instanzen blockiert möglicherweise den Zugriff auf `/api`.

>[!NOTE]
>
>Weitere Informationen finden Sie in der [API-Referenz](/help/assets/assets-api-content-fragments.md#api-reference). Besonders interessant: [Adobe Experience Manager Assets API – Inhaltsfragmente](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html).

### Lesen/Bereitstellen {#read-delivery}

Nutzung erfolgt über:

`GET /{cfParentPath}/{cfName}.json`

Beispiel:

`https://localhost:4502/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.json`

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

Dies kann einfach der Titel oder die Beschreibung eines Inhaltsfragments bzw. ein einzelnes Element oder alle Elementwerte und/oder Metadaten sein. Es ist auch obligatorisch, eine gültige `cq:model`-Eigenschaft für Aktualisierungen bereitzustellen.

### Löschen {#delete}

Nutzung erfolgt über:

`DELETE /{cfParentPath}/{cfName}`

## Beschränkungen {#limitations}

Es gibt einige Beschränkungen:

* **Varianten können weder geschrieben noch aktualisiert werden.** Werden diese Varianten einer Payload hinzugefügt (z. B. für Aktualisierungen), werden sie ignoriert. Jedoch ist die Variante über die Bereitstellung verfügbar (`GET`).

* **Inhaltsfragmentmodelle werden derzeit nicht unterstützt**: sie können weder gelesen noch erstellt werden. Zum Erstellen eines neuen oder Aktualisieren eines vorhandenen Inhaltsfragments müssen Entwickler den richtigen Pfad zum Inhaltsfragmentmodell kennen. Derzeit ist dies lediglich über die Verwaltungsoberfläche möglich.
* **Verweise werden ignoriert**. Zurzeit sind keine Überprüfungen für Verweise auf vorhandene Inhaltsfragmente verfügbar. Wenn Sie beispielsweise ein Inhaltsfragment löschen, treten möglicherweise Probleme auf einer Seite auf, die einen Verweis enthält.

## Status-Codes und Fehlermeldungen {#status-codes-and-error-messages}

Unter den entsprechenden Voraussetzungen werden möglicherweise die folgenden Status-Codes angezeigt:

* **200 (OK)**

   Wird zurückgegeben, wenn:

   * ein Inhaltsfragment per `GET` angefordert wurde

   * ein Inhaltsfragment per `PUT` aktualisiert wurde

* **201 (Erstellt)**

   Wird zurückgegeben, wenn:

   * ein Inhaltsfragment per `POST` erstellt wurde

* **404 (Nicht gefunden)**

   Wird zurückgegeben, wenn:

   * das angeforderte Inhaltsfragment nicht vorhanden ist

* **500 (Interner Server-Fehler)**

   >[!NOTE]
   >
   >Dieser Fehler wird zurückgegeben:
   >
   >
   >
   >    * wenn ein Fehler, der mit keinem bestimmten Code identifiziert werden kann, aufgetreten ist
   >    * wenn als Payload „null“ angegeben ist


   Nachfolgend finden Sie allgemeine Szenarien, in denen dieser Fehlerstatus in Kombination mit der Fehlermeldung (monospace) zurückgegeben wird:

   * Übergeordneter Ordner ist nicht vorhanden (wenn ein Inhaltsfragment per `POST` erstellt wurde)
   * Kein Inhaltsfragmentmodell bereitgestellt (Null-Wert), Ressource ist ungültig (mögliches Berechtigungsproblem) oder die Ressource ist keine gültige Fragmentvorlage:

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`
      * `Cannot adapt the resource '/foo/bar/qux' to a content fragment template`
   * Das Inhaltsfragment konnte nicht erstellt werden (möglicherweise ein Berechtigungsproblem):

      * `Could not create content fragment`
   * Titel oder Beschreibung konnte nicht aktualisiert werden:

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

## API-Referenz   {#api-reference}

Hier finden Sie detaillierte API-Referenzen:

* [Adobe Experience Manager Assets API – Inhaltsfragmente](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)

   * [Verfügbare Funktionen](/help/assets/mac-api-assets.md#assets)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen finden Sie unter:

* [Assets-HTTP-API – Dokumentation ](/help/assets/mac-api-assets.md)
* [AEM Gem-Sitzung: OAuth](https://helpx.adobe.com/de/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)

