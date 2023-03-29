---
title: Persistente GraphQL-Abfragen
description: Erfahren Sie, wie Sie GraphQL-Abfragen in Adobe Experience Manager beibehalten, um die Leistung zu optimieren. Persistente Abfragen können von Clientanwendungen mithilfe der HTTP-GET-Methode angefordert werden. Die Antwort kann auf den Dispatcher- und CDN-Ebenen zwischengespeichert werden, wodurch die Leistung der Clientanwendungen verbessert wird.
source-git-commit: ad0f0bd8b0c230e002c734adca87da22bfa3a7cd
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 73%

---

# Persistente GraphQL-Abfragen {#persisted-queries-caching}

Persistente Abfragen sind GraphQL-Abfragen, die auf dem Server mit Adobe Experience Manager (AEM) as a Cloud Service erstellt und gespeichert werden. Sie können von Client-Programmen mit einer GET-Anfrage angefragt werden. Die Antwort einer GET-Anfrage kann auf den Ebenen Dispatcher und Content Delivery Network (CDN) zwischengespeichert werden, wodurch die Leistung der anfragenden Client-Anwendung verbessert wird. Dies unterscheidet sich von standardmäßigen GraphQL-Abfragen, die mit POST-Anfragen ausgeführt werden, bei denen die Antwort nicht einfach zwischengespeichert werden kann.

<!--
>[!NOTE]
>
>Persisted Queries are recommended. See [GraphQL Query Best Practices (Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) for details, and the related Dispatcher configuration.
-->

Die [GraphiQL-IDE](/help/sites-developing/headless/graphql-api/graphiql-ide.md) ist in AEM verfügbar, damit Sie (persistente) GraphQL-Abfragen entwickeln und testen können, bevor Sie sie [in Ihre Produktionsumgebung übertragen](#transfer-persisted-query-production). Für Fälle, in denen eine Anpassung erforderlich ist (z. B. wenn [Cache anpassen](/help/sites-developing/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)) können Sie die API verwenden; sehen Sie sich das Beispiel cURL an, das in [Beibehalten einer GraphQL-Abfrage](#how-to-persist-query).

## Persistente Abfragen und Endpunkte {#persisted-queries-and-endpoints}

Persistente Abfragen müssen immer den Endpunkt verwenden, der mit der [entsprechenden Sites-Konfiguration](/help/sites-developing/headless/graphql-api/graphql-endpoint.md) verknüpft ist. Sie können also entweder eine oder beide dieser Optionen verwenden:

* Globale Konfiguration und Endpunkt
Die Abfrage hat Zugriff auf alle Inhaltsfragmentmodelle.
* Spezifische Sites-Konfigurationen und -Endpunkte
Das Erstellen einer persistenten Abfrage für eine bestimmte Sites-Konfiguration erfordert einen entsprechenden Sites-konfigurationsspezifischen Endpunkt (um Zugriff auf die zugehörigen Inhaltsfragmentmodelle zu gewähren).
Um beispielsweise eine persistente Abfrage speziell für die WKND-Website-Konfiguration zu erstellen, müssen eine entsprechende WKND-spezifische Sites-Konfiguration und ein WKND-spezifischer Endpunkt im Voraus erstellt werden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Aktivieren der Inhaltsfragmentfunktionen im Konfigurations-Browser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser).
>
>**Persistente GraphQL-Abfragen** müssen für die entsprechende Sites-Konfiguration aktiviert werden.

Wenn es beispielsweise eine bestimmte Abfrage namens `my-query` gibt, die ein `my-model`-Modell aus der Sites-Konfiguration `my-conf` verwendet:

* Sie können eine Abfrage mit dem `my-conf`-spezifischen Endpunkt erstellen und die Abfrage wird dann wie folgt gespeichert:
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* Sie können dieselbe Abfrage mit dem `global`-Endpunkt erstellen, die Abfrage wird dann jedoch wie folgt gespeichert:
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Hierbei handelt es sich um zwei verschiedene Abfragen, die unter verschiedenen Pfaden gespeichert werden.
>
>Sie verwenden zufällig dasselbe Modell – aber über verschiedene Endpunkte.

## Beibehalten einer GraphQL-Abfrage {#how-to-persist-query}

Es wird empfohlen, Abfragen zunächst in einer AEM-Autorenumgebung beizubehalten und dann die [Abfrage](#transfer-persisted-query-production) in Ihre AEM-Veröffentlichungsumgebung der Produktion für die Verwendung durch Programme zu übertragen.

Es gibt verschiedene Methoden zum Beibehalten von Abfragen:

* GraphiQL-IDE – siehe [Speichern persistenter Abfragen](/help/sites-developing/headless/graphql-api/graphiql-ide.md#saving-persisted-queries) (bevorzugte Methode)
* cURL - siehe folgendes Beispiel
* Andere Tools, einschließlich [Postman](https://www.postman.com/)

Die GraphiQL-IDE ist die **bevorzugte** Methode zum Erstellen persistenter Abfragen. So behalten Sie eine bestimmte Abfrage bei: **cURL** Befehlszeilen-Tool:

1. Bereiten Sie die Abfrage mittels einer PUT-Anfrage an die neue Endpunkt-URL `/graphql/persist.json/<config>/<persisted-label>` vor.

   Erstellen Sie beispielsweise eine persistente Abfrage:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. Überprüfen Sie an dieser Stelle die Antwort.

   Prüfen Sie zum Beispiel auf Erfolg:

   ```json
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Sie können die persistente Abfrage dann ausführen, indem Sie die URL `/graphql/execute.json/<shortPath>` per GET-Anfrage abrufen.

   Verwenden Sie zum Beispiel die persistente Abfrage:

   ```shell
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Aktualisieren Sie eine persistente Abfrage mittels POST-Anfrage an einen bereits vorhandenen Abfragepfad.

   Verwenden Sie zum Beispiel die persistente Abfrage:

   ```shell
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. Erstellen Sie eine umschlossene einfache Abfrage.

   Beispiel:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Erstellen Sie eine umschlossene Abfrage mit Cache-Steuerung.

   Beispiel:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Erstellen Sie eine persistente Abfrage mit Parametern:

   Beispiel:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```


## Ausführen einer persistenten Abfrage {#execute-persisted-query}

Um eine persistente Abfrage auszuführen, sendet ein Client-Programm eine GET-Anfrage mit der folgenden Syntax:

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

Dabei ist `PERSISTENT_PATH` ein gekürzter Pfad zum Speicherort der persistenten Abfrage.

1. Zum Beispiel ist `wknd` der Konfigurationsname und `plain-article-query` der Name der persistenten Abfrage. So führen Sie die Abfrage aus:

   ```shell
   $ curl -X GET \
       https://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Ausführen einer Abfrage mit Parametern.

   >[!NOTE]
   >
   > Die Abfragevariablen und -werte müssen beim Ausführen einer persistenten Abfrage ordnungsgemäß [codiert](#encoding-query-url) sein.

   Beispiel:

   ```bash
   $ curl -X GET \
       "https://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   Siehe [Verwenden von Abfragevariablen](#query-variables) für weitere Details.

## Verwenden von Abfragevariablen {#query-variables}

Abfragevariablen können mit persistenten Abfragen verwendet werden. Die Abfragevariablen werden an die Anfrage mit einem Semikolon (`;`) unter Verwendung des Variablennamens und -werts angehängt. Mehrere Variablen werden durch Semikolons getrennt.

Die Struktur sieht wie folgt aus:

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

Die folgende Abfrage enthält beispielsweise die Variable `activity`, um eine Liste nach einem Aktivitätswert zu filtern:

```graphql
query getAdventuresByActivity($activity: String!) {
      adventureList (filter: {
        adventureActivity: {
          _expressions: [
            {
              value: $activity
            }
          ]
        }
      }){
        items {
          _path
        adventureTitle
        adventurePrice
        adventureTripLength
      }
    }
  }
```

Aus dieser Abfrage kann unter einem Pfad `wknd/adventures-by-activity` eine persistente Abfrage erstellt werden. Um die persistente Abfrage für `activity=Camping` aufzurufen, müsste die Anfrage wie folgt aussehen:

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

Beachten Sie Folgendes: `%3B` ist die UTF-8-Codierung für `;`, und `%3D` ist die Codierung für `=`. Die Abfragevariablen und alle Sonderzeichen müssen [ordnungsgemäß codiert sein](#encoding-query-url), damit die persistente Abfrage ausgeführt wird.

## Caching persistenter Abfragen {#caching-persisted-queries}

Beständige Abfragen werden empfohlen, da sie im [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=en) und CDN-Ebenen (Content Delivery Network), die letztendlich die Leistung der anfragenden Client-Anwendung verbessern.

Standardmäßig werden AEM Cache basierend auf einer TTL-Definition (Time To Live) ungültig. Diese TTLs können durch die folgenden Parameter definiert werden. Auf diese Parameter kann auf verschiedene Weise zugegriffen werden, wobei die Namen je nach verwendetem Mechanismus variieren:

| Cachetyp | [HTTP-Header](https://developer.mozilla.org/de-de/docs/Web/HTTP/Headers/Cache-Control)  | cURL  | OSGi-Konfiguration  |
|--- |--- |--- |--- |--- |
| Browser | `max-age` | `cache-control : max-age` | `cacheControlMaxAge` |
| CDN | `s-maxage` | `surrogate-control : max-age` | `surrogateControlMaxAge` |
| CDN | `stale-while-revalidate` | `surrogate-control : stale-while-revalidate ` | `surrogateControlStaleWhileRevalidate` |
| CDN | `stale-if-error` | `surrogate-control : stale-if-error` | `surrogateControlStaleIfError` |

### Autoreninstanzen {#author-instances}

Für Autoreninstanzen sind die Standardwerte:

* `max-age`  : 60
* `s-maxage` : 60
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Diese:

* kann nicht mit einer OSGi-Konfiguration überschrieben werden
* kann durch eine Anfrage überschrieben werden, die HTTP-Header-Einstellungen mithilfe von cURL definiert; Es sollten geeignete Einstellungen für `cache-control` und/oder `surrogate-control`; Beispiele finden Sie unter [Verwalten des Cache auf der Ebene der persistenten Abfrage](#cache-persisted-query-level)

<!-- CQDOC-20186 -->
<!-- following entry is only when the GraphiQL IDE is ready; add cross-reference too -->
<!--
* can be overwritten if you specify values in the **Headers** dialog of the [GraphiQL IDE](#http-cache-headers-graphiql-ide)
-->

### Veröffentlichungsinstanzen {#publish-instances}

Für Veröffentlichungsinstanzen sind die Standardwerte:

* `max-age`  : 60
* `s-maxage` : 7200
* `stale-while-revalidate` : 86400
* `stale-if-error` : 86400

Diese können überschrieben werden:

<!-- CQDOC-20186 -->
<!-- following entry is only when the GraphiQL IDE is ready -->
<!--
* [from the GraphQL IDE](#http-cache-headers-graphiql-ide)
-->

* [auf der Ebene der persistenten Abfrage](#cache-persisted-query-level); Hierzu gehört das Posten der Abfrage an AEM mithilfe von cURL in Ihrer Befehlszeilenschnittstelle und das Veröffentlichen der beständigen Abfrage.

* [mit einer OSGi-Konfiguration](#cache-osgi-configration)

<!-- CQDOC-20186 -->
<!-- keep for future use; check link -->
<!--
### Managing HTTP Cache Headers in the GraphiQL IDE {#http-cache-headers-graphiql-ide}

The GraphiQL IDE - see [Saving Persisted Queries](/help/sites-developing/headless/graphql-api/graphiql-ide.md#managing-cache)
-->

### Verwalten des Cache auf der Ebene der persistenten Abfrage {#cache-persisted-query-level}

Dazu gehört das Posten der Abfrage an AEM mithilfe von cURL in Ihrer Befehlszeilenschnittstelle.

Beispiel für die PUT-Methode (create):

```bash
curl -u admin:admin -X PUT \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

Beispiel für die POST-Methode (update):

```bash
curl -u admin:admin -X POST \
--url "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
--header "Content-Type: application/json" \
--data '{ "query": "{articleList { items { _path author } } }", "cache-control": { "max-age": 300 }, "surrogate-control": {"max-age":600, "stale-while-revalidate":1000, "stale-if-error":1000} }'
```

Die `cache-control` kann zum Zeitpunkt der Erstellung (PUT) oder später (z. B. über eine POST-Anfrage) festgelegt werden. Die Cache-Steuerung ist beim Erstellen der persistenten Abfrage optional, da AEM den Standardwert bereitstellen kann. Siehe [Beibehalten einer GraphQL-Abfrage](#how-to-persist-query), zum Beispiel für die Beibehaltung einer Abfrage mit cURL.

### Verwalten des Cache mit einer OSGi-Konfiguration {#cache-osgi-configration}

Um den Cache global zu verwalten, können Sie [Konfigurieren der OSGi-Einstellungen](/help/sites-deploying/configuring-osgi.md) für **Konfigurationen für beständige Abfragen**. Andernfalls verwendet diese OSGi-Konfiguration die [Standardwerte für Veröffentlichungsinstanzen](#publish-instances).

>[!NOTE]
>
>Die OSGi-Konfiguration ist nur für Veröffentlichungsinstanzen geeignet. Die Konfiguration ist in Autoreninstanzen vorhanden, wird jedoch ignoriert.

## Codieren der Abfrage-URL zur Verwendung in einer Mobile App {#encoding-query-url}

Damit die Abfrage-URL von einer Anwendung verwendet werden kann, müssen alle Sonderzeichen, die beim Erstellen von Abfragevariablen verwendet werden – d. h. Semikolons (`;`), Gleichheitszeichen (`=`), Schrägstriche (`/`) – konvertiert werden, sodass die entsprechende UTF-8-Codierung verwendet wird.

Beispiel:

```bash
curl -X GET \ "https://localhost:4502/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

Die URL kann in die folgenden Teile unterteilt werden:

| URL-Teil | Beschreibung |
|----------| -------------|
| `/graphql/execute.json` | Endpunkt der persistenten Abfrage |
| `/wknd/adventure-by-path` | Pfad der persistenten Abfrage |
| `%3B` | Codierung von `;` |
| `adventurePath` | Abfragevariable |
| `%3D` | Codierung von `=` |
| `%2F` | Codierung von `/` |
| `%2Fcontent%2Fdam...` | Codierter Pfad zum Inhaltsfragment |

Im Klartext sieht der Anfrage-URI wie folgt aus:

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

Um eine persistente Abfrage in einer Client-Anwendung zu verwenden, sollte für [JavaScript](https://github.com/adobe/aem-headless-client-js), [Java](https://github.com/adobe/aem-headless-client-java) oder [NodeJS](https://github.com/adobe/aem-headless-client-nodejs) das AEM-Headless-Client-SDK verwendet werden. Das Headless-Client-SDK codiert in der Anfrage automatisch alle Abfragevariablen entsprechend.

## Übertragen einer persistenten Abfrage in die Produktionsumgebung  {#transfer-persisted-query-production}

Persistente Abfragen sollten immer in einem AEM-Autoren-Service erstellt und dann in einem AEM-Veröffentlichungs-Service veröffentlicht (repliziert) werden. Häufig werden persistente Abfragen in niedrigeren Umgebungen wie lokalen Umgebungen oder Entwicklungsumgebungen erstellt und getestet. Anschließend müssen persistente Abfragen in Umgebungen höherer Ebene übertragen werden, um sie letztendlich in einer AEM-Publishing-Produktionsumgebung verfügbar zu machen, auf die Client-Anwendungen zugreifen können.

### Verpacken von persistenten Abfragen

Persistente Abfragen können in [AEM-Pakete](/help/sites-administering/package-manager.md) integriert werden. AEM-Pakete können dann heruntergeladen und in verschiedenen Umgebungen installiert werden. AEM-Pakete können auch von einer AEM-Autorenumgebung in AEM-Veröffentlichungsumgebungen repliziert werden.

So erstellen Sie ein Paket:

1. Navigieren Sie zu **Tools** > **Implementierung** > **Pakete**.
1. Erstellen Sie ein neues Paket durch Tippen auf **Paket erstellen**. Dadurch wird ein Dialogfeld zum Definieren des Pakets geöffnet.
1. Geben Sie im Dialogfeld zur Paketdefinition unter **Allgemein** einen **Namen** wie „wknd-persistent-queries“ ein.
1. Geben Sie eine Versionsnummer wie „1.0“ ein.
1. Fügen Sie unter **Filter** einen neuen **Filter** hinzu. Wählen Sie über die Pfadsuche den Ordner `persistentQueries` unterhalb der Konfiguration aus. Für die Konfiguration von `wknd` lautet der vollständige Pfad beispielsweise `/conf/wknd/settings/graphql/persistentQueries`.
1. Tippen Sie auf **Speichern**, um die neue Paketdefinition zu speichern und das Dialogfeld zu schließen.
1. Tippen Sie in der neu erstellten Paketdefinition auf **Erstellen**.

Nachdem das Paket erstellt wurde, können Sie Folgendes tun:

* Das Paket **herunterladen** und in eine andere Umgebung hochladen.
* Das Paket **replizieren**, indem Sie auf **Mehr** > **Replizieren** tippen. Dadurch wird das Paket in der verbundenen AEM-Publishing-Umgebung repliziert.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
