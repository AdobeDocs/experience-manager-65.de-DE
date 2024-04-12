---
title: Optimieren von GraphQL-Abfragen
description: Erfahren Sie, wie Sie GraphQL-Abfragen beim Filtern, Paging und Sortieren Ihrer Inhaltsfragmente in Adobe Experience Manager as a Cloud Service optimieren können, um Headless-Inhalte bereitzustellen.
exl-id: 47d0570b-224e-4109-b94e-ccc369d7ac5f
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1949'
ht-degree: 100%

---

# Optimieren von GraphQL-Abfragen {#optimizing-graphql-queries}

>[!NOTE]
>
>Bevor Sie diese Optimierungsempfehlungen anwenden, empfehlen wir Ihnen, [Ihre Inhaltsfragmente für Paging und Sortierung in der GraphQL-Filterung zu aktualisieren](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md), um eine optimale Leistung zu erzielen.

Diese Richtlinien helfen Ihnen, Leistungsprobleme bei GraphQL-Abfragen zu vermeiden.

## GraphQL-Checkliste {#graphql-checklist}

Die folgende Checkliste soll Ihnen dabei helfen, die Konfiguration und Verwendung von GraphQL in Adobe Experience Manager (AEM) as a Cloud Service zu optimieren.

### Erste Grundsätze {#first-principles}

#### Verwenden persistierter GraphQL-Abfragen {#use-persisted-graphql-queries}

**Empfehlung**

Die Verwendung persistierter GraphQL-Abfragen wird ausdrücklich empfohlen.

Persistierte GraphQL-Abfragen tragen durch Verwendung des Content Delivery Network (CDN) dazu bei, die Last bei der Abfrageausführung zu reduzieren. Client-Anwendungen fordern persistierte Abfragen mit GET-Anfragen an, um eine schnelle Edge-fähige Ausführung zu ermöglichen.

**Weitere Informationen**

Siehe:

* [Persistierte GraphQL-Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md)
* [Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md)

#### Installieren des GraphQL-Indexpakets {#install-graphql-index-package}

**Empfehlung**

Kundinnen und Kunden, die GraphQL verwenden, *müssen* das GraphQL-Indexpaket für Experience Manager-Inhaltsfragmente installieren. Auf diese Weise können Sie die erforderliche Indexdefinition auf der Grundlage der tatsächlich verwendeten Funktionen hinzufügen. Wenn dieses Paket nicht installiert wird, kann es zu langsamen oder fehlgeschlagenen GraphQL-Abfragen kommen.

Die für Ihr Service Pack geeignete Version finden Sie in den Versionshinweisen. Das neueste Service Pack finden Sie beispielsweise unter [Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package).

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

**Weitere Informationen**
Siehe:

* [Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package)

### Cache-Strategie {#cache-strategy}

Zur Optimierung können auch verschiedene Caching-Methoden verwendet werden.

#### Aktivieren von AEM Dispatcher-Caching {#enable-aem-dispatcher-caching}

**Empfehlung**

[AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) ist der Cache der ersten Ebene im AEM-Dienst, vor dem CDN-Cache.

**Weitere Informationen**

Siehe:

* [Persistierte GraphQL-Abfragen – Aktivieren der Caching-Funktion im Dispatcher](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphql-persisted-queries-enabling-caching-dispatcher)

#### Verwenden eines Content Delivery Network (CDN) {#use-cdn}

**Empfehlung**

GraphQL-Abfragen und ihre JSON-Antworten können im Cache gespeichert werden, wenn sie bei Verwendung eines CDN als `GET`-Anfragen anvisiert werden. Im Gegensatz dazu können nicht zwischengespeicherte Anfragen sehr aufwendig (ressourcenintensiv) sein und möglicherweise nur langsam verarbeitet werden, was weitere nachteilige Auswirkungen auf die Ursprungsressourcen bedeuten kann.

**Weitere Informationen**

Siehe:

* [Verwenden von CDN in AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn)

#### Festlegen von HTTP-Cache-Control-Headern {#set-http-cache-control-headers}

**Empfehlung**

Bei der Verwendung persistierter GraphQL-Abfragen mit einem CDN wird empfohlen, geeignete HTTP-Cache-Control-Header festzulegen.

Jede persistierte Abfrage kann über einen eigenen spezifischen Satz von Cache-Control-Headern verfügen. Die Header können über die [GraphQL-API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) festgelegt werden.

Sie können auch mithilfe des Befehlszeilen-Tools **cURL** festgelegt werden: Verwenden Sie beispielsweise eine `PUT`-Anfrage zum Erstellen einer umschlossenen einfachen Abfrage mit Cache-Steuerung.

```shell
$ curl -X PUT \
    -H 'authorization: Basic YWRtaW46YWRtaW4=' \
    -H "Content-Type: application/json" \
    "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
    -d \
'{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
```

<!-- or the [AEM GraphiQL IDE](/help/sites-developing/headless/graphql-api/graphiql-ide.md#managing-cache). 
-->

**Weitere Informationen**

Siehe:

* [Caching persistenter Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md#caching-persisted-queries)
* [Beibehalten einer GraphQL-Abfrage](/help/sites-developing/headless/graphql-api/persisted-queries.md#how-to-persist-query)
<!--
* [Managing cache for your persisted queries](/help/sites-developing/headless/graphql-api/graphiql-ide.md#managing-cache)
-->

<!--
#### Use AEM GraphQL pre-caching {#use-aem-graphql-pre-caching}

**Recommendation**

This capability allows AEM to further cache content within the scope of GraphQL queries that can then be assembled as blocks in JSON output rather than line by line. 

**Further Reference**

Contact Adobe to enable this capability for your AEM Cloud Service program and environments. 
-->

### GraphQL-Abfrageoptimierung {#graphql-query-optimization}

Auf einer AEM-Instanz mit einer großen Anzahl von Inhaltsfragmenten, die dasselbe Modell verwenden, können GraphQL-Listenabfragen kostenintensiv sein (im Hinblick auf Ressourcen).

Das liegt daran, dass *alle* Fragmente, die dasselbe in der GraphQL-Abfrage verwendete Modell nutzen, in den Speicher geladen werden müssen. Dies erfordert Zeit und Speicherplatz. Eine Filterung, die die Anzahl der Elemente in der (endgültigen) Ergebnismenge verringern kann, kann nur **nach** dem Laden des gesamten Ergebnissatzes in den Speicher angewendet werden.

Dies kann den Eindruck erwecken, dass die Leistung auch bei kleinen Ergebnismengen schlecht ist. In Wirklichkeit wird das langsame Tempo jedoch durch die Größe des ursprünglichen Ergebnissatzes verursacht, da dieser intern verarbeitet werden muss, bevor die Filterung angewendet werden kann.

Um Leistungs- und Speicherprobleme zu vermeiden, muss diese anfängliche Ergebnismenge so klein wie möglich gehalten werden.

AEM bietet zwei Methoden zur Optimierung von GraphQL-Abfragen:

* [Hybride Filterung](#use-aem-graphql-hybrid-filtering)
* [Paging](#use-aem-graphql-pagination) (oder Paginierung)

   * [Sortierung](#use-graphql-sorting) ist nicht direkt mit der Optimierung verbunden, sondern mit dem Paging

Jede Methode beinhaltet eigene Anwendungsfälle und Einschränkungen. In diesem Abschnitt finden Sie Informationen zur hybriden Filterung und zum Paging sowie einige [Best Practices](#best-practices) zur Optimierung von GraphQL-Abfragen.

#### Verwenden der AEM GraphQL-Hybrid-Filterung {#use-aem-graphql-hybrid-filtering}

**Empfehlung**

Hybride Filterung kombiniert JCR-Filterung mit AEM-Filterung.

Dabei wird ein JCR-Filter (in Form einer Abfragebegrenzung) angewendet, bevor der Ergebnissatz zur AEM-Filterung in den Speicher geladen wird. Dadurch soll der in den Speicher geladene Ergebnissatz verringert werden, da der JCR-Filter überflüssige Ergebnisse davor entfernt.

>[!NOTE]
>
>Aus technischen Gründen (z. B. Flexibilität oder Verschachtelung von Fragmenten) kann AEM nicht die gesamte Filterung an JCR delegieren.

Bei dieser Methode wird die Flexibilität bewahrt, die GraphQL-Filter bieten, während gleichzeitig ein möglichst großer Teil der Filterung an JCR delegiert wird.

>[!NOTE]
>
>Die AEM-Hybridfilterung erfordert die Aktualisierung vorhandener Inhaltsfragmente

**Weitere Informationen**

Siehe:

* [Aktualisieren von Inhaltsfragmenten für Paging und Sortierung in der GraphQL-Filterung](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md)
* [Beispielabfrage mit Filterung nach _tags-ID und Ausschluss von Varianten](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-filtering-tag-not-variations)

#### Verwenden der GraphQL-Seitennummerierung {#use-aem-graphql-pagination}

**Empfehlung**

Die Reaktionszeit komplexer Abfragen mit großen Ergebnismengen kann durch die Segmentierung von Antworten in Blöcke mithilfe der Seitennummerierung (ein GraphQL-Standard) verbessert werden.

GraphQL in AEM unterstützt zwei Arten der Seitennummerierung:

* [Limit-/Offset-basierte Seitennummerierung](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#list-offset-limit)
Diese Methode wird für Listenabfragen verwendet; diese enden mit `List`. Zum Beispiel: `articleList`.
Um sie zu verwenden, müssen Sie die Position des ersten Elements angeben, das zurückgegeben werden soll (`offset`) und die Anzahl der zurückzugebenden Elemente (`limit` oder Seitengröße).

* [Cursor-basierte Paginierung](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#paginated-first-after) (dargestellt durch `first` und `after`) 
Bei dieser Methode wird für jedes Element eine eindeutige ID bereitgestellt; auch als Cursor bezeichnet.
In der Abfrage geben Sie den Cursor des letzten Elements der vorherigen Seite sowie die Seitengröße (die maximale Anzahl der zurückzugebenden Elemente) an.

  Da die Cursor-basierte Paginierung nicht zu den Datenstrukturen von listenbasierten Abfragen passt, hat AEM den Abfragetyp `Paginated` eingeführt, zum Beispiel `articlePaginated`. Die verwendeten Datenstrukturen und Parameter entsprechen der [GraphQL Cursor ConnectionSpecification](https://relay.dev/graphql/connections.htm).

  >[!NOTE]
  >
  >AEM unterstützt derzeit Forward Paging (unter Verwendung der Parameter `after`/`first`).
  >
  >Backward Paging (mithilfe der Parameter `before`/`last`) wird nicht unterstützt.

**Weitere Informationen**

Siehe:

* [Beispielhafte Paginierungsabfrage mit „first“ und „after“](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-pagination-first-after)

#### Verwenden der GraphQL-Sortierung {#use-graphql-sorting}

**Empfehlung**

Die Sortierung ist ebenfalls ein GraphQL-Standard und ermöglicht es, dass Clients JSON-Inhalte in sortierter Reihenfolge empfangen. Dies kann die Notwendigkeit einer weiteren Verarbeitung auf dem Client verringern.

Die Sortierung ist nur dann effizient, wenn sich alle Sortierungskriterien auf Fragmente der obersten Ebene beziehen.

Wenn die Sortierreihenfolge ein oder mehrere Felder enthält, die sich auf einem verschachtelten Fragment befinden, müssen alle Fragmente, die das Modell der obersten Ebene gemeinsam verwenden, in den Speicher geladen werden. Dies führt zu Leistungseinbußen.

>[!NOTE]
>
>Die Sortierung der Felder der obersten Ebene wirkt sich ebenfalls (wenn auch geringfügig) auf die Leistung aus.

**Weitere Informationen**

Siehe:

* [Beispielabfrage mit Filterung nach _tags-ID und Ausschließen von Varianten und Sortieren nach Namen](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-filtering-tag-not-variations)

## Best Practices {#best-practices}

Das Hauptziel aller Optimierungsempfehlungen besteht darin, die anfängliche Ergebnismenge zu reduzieren. Die hier aufgeführten Best Practices bieten Möglichkeiten dazu. Sie können (und sollten) kombiniert werden.

### Nur nach Eigenschaften der obersten Ebene filtern {#filter-top-level-properties-only}

Derzeit funktioniert das Filtern auf JCR-Ebene nur für Fragmente der obersten Ebene.

Wenn sich ein Filter auf die Felder eines verschachtelten Fragments bezieht, muss AEM alle Fragmente, die das zugrunde liegende Modell gemeinsam nutzen, wieder in den Speicher laden.

Sie können diese GraphQL-Abfragen dennoch optimieren, indem Sie Filterausdrücke für Felder von Fragmenten der obersten Ebene und für Felder verschachtelter Fragmente mit dem [AND-Operator](#logical-operations-in-filter-expressions) kombinieren.

### Inhaltsstruktur verwenden {#use-content-structure}

In AEM wird generell empfohlen, die Repository-Struktur zu verwenden, um den Umfang der zu verarbeitenden Inhalte einzugrenzen.

Diese Methode sollte auch auf GraphQL-Abfragen angewendet werden.

Dies kann durch Anwendung eines Filters auf das Feld `_path` des Fragments der obersten Ebene geschehen:

```graphql
{
  someList(filter: {
    _path: {
      _expressions: [ 
        {
          value: "/content/dam/some/sub/path/",
          _operator: STARTS_WITH
        }
      ]
    }
  }) {
    items {
      # ...
    }
  }
}
```

>[!NOTE]
>
>Die Endung `/` auf `value` ist erforderlich, um die beste Leistung zu erzielen.

### Verwenden Sie Paging {#use-paging}

Sie können auch Paging verwenden, um die anfängliche Ergebnismenge zu reduzieren; insbesondere dann, wenn Ihre Anforderungen keine Filterung und Sortierung verwenden.

Wenn Sie verschachtelte Fragmente filtern oder sortieren, können die paginierten Abfragen immer noch langsam sein, da AEM möglicherweise weiterhin größere Mengen von Fragmenten in den Speicher laden muss. Wenn Sie also Filtern und Paging kombinieren, sollten Sie die Filterregeln beachten (wie oben erwähnt).

Für das Paging ist die Sortierung gleichermaßen wichtig, da paginierte Ergebnisse immer sortiert werden, entweder explizit oder implizit.

Wenn Sie in erster Linie daran interessiert sind, nur die ersten Seiten abzurufen, gibt es keinen signifikanten Unterschied zwischen der Verwendung der `...List`- oder `...Paginated`-Abfragen. Wenn Ihre Anwendung jedoch daran interessiert ist, mehr als ein oder zwei Seiten zu lesen, sollten Sie die `...Paginated`-Abfrage in Erwägung ziehen, da sie bei den späteren Seiten deutlich besser funktioniert.

### Logische Vorgänge in Filterausdrücken {#logical-operations-in-filter-expressions}

Wenn Sie verschachtelte Fragmente filtern, können Sie weiterhin die JCR-Filterung nutzen, indem Sie einen begleitenden Filter für ein Feld der obersten Ebene bereitstellen, das mithilfe des `AND`-Operators kombiniert wird.

Ein typischer Anwendungsfall bestünde darin, den Umfang der Abfrage mithilfe eines Filters auf das Feld `_path` des Fragments der obersten Ebene einzugrenzen und dann zusätzliche Felder zu filtern, die sich möglicherweise auf der obersten Ebene oder in einem verschachtelten Fragment befinden.

In diesem Fall würden die verschiedenen Filterausdrücke mit `AND` kombiniert. Daher kann der Filter auf `_path` die anfängliche Ergebnismenge effektiv einschränken. Alle anderen Filter auf Feldern der obersten Ebene können ebenfalls dazu beitragen, den anfänglichen Ergebnissatz zu reduzieren, sofern sie mit `AND` kombiniert werden.

Filterausdrücke, die mit `OR` kombiniert sind, können nicht optimiert werden, wenn verschachtelte Fragmente vorliegen. `OR`-Ausdrücke können nur optimiert werden, wenn *keine* verschachtelten Fragmente vorliegen.

### Vermeidung von Filtern bei mehrzeiliger Textfelder {#avoid-filtering-multiline-textfields}

Die Felder eines mehrzeiligen Textfelds (HTML, Markdown, Plain text, JSON) können nicht über eine JCR-Abfrage gefiltert werden, da der Inhalt dieser Felder dynamisch berechnet werden muss.

Wenn Sie weiterhin ein mehrzeiliges Textfeld filtern müssen, sollten Sie die Größe des ursprünglichen Ergebnissatzes einschränken, indem Sie zusätzliche Filterausdrücke hinzufügen und sie mit `AND` kombinieren. Die Begrenzung des Umfangs durch Filterung des Felds `_path` ist auch ein guter Ansatz.

### Vermeidung von Filtern bei virtueller Felder {#avoid-filtering-virtual-fields}

Virtuelle Felder (die meisten Felder, die mit `_` beginnen) werden während der Ausführung einer GraphQL-Abfrage berechnet und befinden sich daher außerhalb des Bereichs der JCR-basierten Filterung.

Eine wichtige Ausnahme bildet das Feld `_path`, das effektiv verwendet werden kann, um die Größe des ursprünglichen Ergebnissatzes zu reduzieren – falls der Inhalt entsprechend strukturiert ist (siehe [Verwenden der Inhaltsstruktur](#use-content-structure)).

### Filter: Ausnahmen {#filtering-exclusions}

Es gibt mehrere andere Situationen, in denen ein Filterausdruck nicht auf der JCR-Ebene bewertet werden kann (und daher vermieden werden sollte, um die beste Leistung zu erzielen):

* Filterausdrücke in einem `Float`-Wert, der die Filteroption `_sensitiveness` verwendet, wobei `_sensitiveness` auf alles andere als `0.0` festgelegt ist.

* Filterausdrücke in einem `String`-Wert, die die Filteroption `_ignoreCase` nutzen.

* Filtern von `null`-Werten.

* Filtern von Arrays mit `_apply: ALL_OR_EMPTY`.

* Filtern von Arrays mit `_apply: INSTANCES`, `_instances: 0`.

* Filterausdrücke mit dem `CONTAINS_NOT`-Operator.

* Filterausdrücke in einem `Calendar`-, `Date`- oder `Time`-Wert, die den `NOT_AT`-Operator nutzen.

### Minimieren der Verschachtelung von Inhaltsfragmenten {#minimize-content-fragment-nesting}

Die Verschachtelung von Inhaltsfragmenten ist eine hervorragende Möglichkeit, benutzerdefinierte Inhaltsstrukturen zu modellieren. Sie können sogar ein Fragment mit einem verschachtelten Fragment haben, das auch ein verschachteltes Fragment hat, und dies iterieren.

Das Erstellen einer Struktur mit zu vielen Ebenen kann jedoch die Verarbeitungszeiten für eine GraphQL-Abfrage erhöhen, da GraphQL die gesamte Hierarchie aller verschachtelten Inhaltsfragmente durchlaufen muss.

Tiefes Verschachteln kann sich auch nachteilig auf die Inhaltsverwaltung auswirken. Im Allgemeinen wird empfohlen, die Verschachtelung von Inhaltsfragmenten auf weniger als fünf oder sechs Ebenen zu beschränken.

### Nicht alle Formate ausgeben (mehrzeilige Textelemente) {#do-not-output-all-formats}

AEM GraphQL kann Text zurückgeben, der im Datentyp **[Mehrzeiliger Text](/help/assets/content-fragments/content-fragments-models.md#data-types)** in mehreren Formaten verfasst wurde: Rich-Text, einfacher Text und Markdown.

Die Ausgabe aller drei Formate erhöht die Größe der Textausgabe in JSON um den Faktor drei. Dies kann zusammen mit generell großen Ergebnismengen aus sehr breiten Abfragen große JSON-Antworten generieren, die daher lange für die Berechnung benötigen. Es ist besser, die Ausgabe auf die Textformate zu beschränken, die für das Rendern des Inhalts erforderlich sind.

### Ändern von Inhaltsfragmenten {#modifying-content-fragments}

Nehmen Sie Änderungen an Inhaltsfragmenten und deren Ressourcen nur mithilfe der AEM-Benutzeroberfläche oder APIs vor. Nehmen Sie keine Änderungen direkt in JCR vor.

### Testen von Abfragen {#test-your-queries}

Die Verarbeitung von GraphQL-Abfragen ähnelt der Verarbeitung von Suchabfragen und ist wesentlich komplexer als einfache API-Anfragen vom Stil GET-all-content.

Eine sorgfältige Planung, Prüfung und Optimierung Ihrer Abfragen in einer kontrollierten, produktionsfremden Umgebung ist von entscheidender Bedeutung für den späteren Erfolg bei der Verwendung in der Produktion.
