---
title: Optimieren von GraphQL-Abfragen
description: Erfahren Sie, wie Sie Ihre GraphQL-Abfragen beim Filtern, Paging und Sortieren Ihrer Inhaltsfragmente in Adobe Experience Manager as a Cloud Service für die Bereitstellung Headless Content optimieren können.
exl-id: 47d0570b-224e-4109-b94e-ccc369d7ac5f
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1966'
ht-degree: 63%

---

# Optimieren von GraphQL-Abfragen {#optimizing-graphql-queries}

>[!NOTE]
>
>Bevor Sie diese Optimierungsempfehlungen anwenden, sollten Sie [Aktualisieren Ihrer Inhaltsfragmente für Paging und Sortierung in GraphQL-Filterung](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md) für beste Leistung.

Diese Richtlinien helfen Ihnen bei der Vermeidung von Leistungsproblemen bei Ihren GraphQL-Abfragen.

## GraphQL-Checkliste {#graphql-checklist}

Die folgende Checkliste soll Ihnen dabei helfen, die Konfiguration und Verwendung von GraphQL in Adobe Experience Manager (AEM) as a Cloud Service zu optimieren.

### Erste Grundsätze {#first-principles}

#### Verwenden persistenter GraphQL-Abfragen {#use-persisted-graphql-queries}

**Empfehlung**

Die Verwendung von persistenten GraphQL-Abfragen wird dringend empfohlen.

Beständige GraphQL-Abfragen helfen durch die Verwendung des Content Delivery Network (CDN) bei der Reduzierung der Abfrageleistung. Clientanwendungen fordern persistente Abfragen mit GET-Anforderungen an, um eine schnelle Edge-fähige Ausführung zu ermöglichen.

**Weitere Informationen**

Siehe:

* [Persistente GraphQL-Abfragen](/help/sites-developing/headless/graphql-api/persisted-queries.md).
* [Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md)

#### Installieren des GraphQL Index-Pakets {#install-graphql-index-package}

**Empfehlung**

Kunden, die GraphQL verwenden *must* Installieren Sie das Experience Manager-Inhaltsfragment mit dem GraphQL-Indexpaket. Auf diese Weise können Sie die erforderliche Indexdefinition auf der Grundlage der tatsächlich verwendeten Funktionen hinzufügen. Wenn dieses Paket nicht installiert wird, kann es zu langsamen oder fehlgeschlagenen GraphQL-Abfragen kommen.

Die für Ihr Service Pack geeignete Version finden Sie in den Versionshinweisen . Das neueste Service Pack finden Sie beispielsweise unter [Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package) .

>[!NOTE]
>
>Installieren Sie dieses Paket nur einmal pro Instanz. Es muss nicht mit jedem Service Pack neu installiert werden.

**Weitere Informationen**
Siehe:

* [Installieren des GraphQL-Indexpakets für Experience Manager-Inhaltsfragmente](/help/release-notes/release-notes.md#install-aem-graphql-index-add-on-package)

### Cache-Strategie {#cache-strategy}

Zur Optimierung können auch verschiedene Methoden der Zwischenspeicherung verwendet werden.

#### Aktivieren AEM Dispatcher-Caching {#enable-aem-dispatcher-caching}

**Empfehlung**

[AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) ist der Zwischenspeicher der ersten Ebene im AEM-Dienst vor dem CDN-Cache.

**Weitere Informationen**

Siehe:

* [Persistente GraphQL-Abfragen - Aktivierung der Zwischenspeicherung im Dispatcher](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#graphql-persisted-queries-enabling-caching-dispatcher)

#### Verwenden eines Content Delivery Network (CDN) {#use-cdn}

**Empfehlung**

GraphQL-Abfragen und ihre JSON-Antworten können zwischengespeichert werden, wenn sie als Ziel ausgewählt werden. `GET` Anfragen bei Verwendung eines CDN. Im Gegensatz dazu können nicht zwischengespeicherte Anfragen sehr (ressourcenintensiv) teuer und langsam verarbeitet werden, was weitere nachteilige Auswirkungen auf die Ressourcen des Ursprungs haben kann.

**Weitere Informationen**

Siehe:

* [Verwenden von CDN in AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de#using-dispatcher-with-a-cdn)

#### Festlegen von HTTP-Cache-Steuerelement-Headern {#set-http-cache-control-headers}

**Empfehlung**

Bei der Verwendung von persistenten GraphQL-Abfragen mit einem CDN wird empfohlen, geeignete HTTP-Cache-Steuerelement-Header festzulegen.

Jede beibehaltene Abfrage kann über einen eigenen Satz von Cache-Steuerelement-Headern verfügen. Die Kopfzeilen können über die [GraphQL-API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md).

Sie können auch mithilfe der **cURL** Befehlszeilen-Tool. Verwenden Sie beispielsweise eine `PUT` Anfrage zum Erstellen einer umschlossenen einfachen Abfrage mit Cache-Steuerung.

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

Jede Methode beinhaltet eigene Anwendungsfälle und Einschränkungen. In diesem Abschnitt finden Sie Informationen zum Hybrid-Filter und zum Paging sowie einige der [Best Practices](#best-practices) zur Verwendung bei der Optimierung von GraphQL-Abfragen.

#### Verwenden AEM GraphQL Hybrid-Filterung {#use-aem-graphql-hybrid-filtering}

**Empfehlung**

Hybride Filterung kombiniert JCR-Filterung mit AEM-Filterung.

Dabei wird ein JCR-Filter (in Form einer Abfragebegrenzung) angewendet, bevor der Ergebnissatz zur AEM-Filterung in den Speicher geladen wird. Dadurch soll der in den Speicher geladene Ergebnissatz verringert werden, da der JCR-Filter überflüssige Ergebnisse davor entfernt.

>[!NOTE]
>
>Aus technischen Gründen (z. B. Flexibilität oder Verschachtelung von Fragmenten) kann AEM nicht die gesamte Filterung an JCR delegieren.

Bei dieser Methode wird die Flexibilität bewahrt, die GraphQL-Filter bieten, während gleichzeitig ein möglichst großer Teil der Filterung an JCR delegiert wird.

>[!NOTE]
>
>AEM Hybrid-Filterung erfordert die Aktualisierung vorhandener Inhaltsfragmente

**Weitere Informationen**

Siehe:

* [Aktualisieren Ihrer Inhaltsfragmente für Paging und Sortierung in GraphQL-Filterung](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md)
* [Beispielabfrage mit Filterung nach _tags-ID und Ausschluss von Varianten](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-filtering-tag-not-variations)

#### GraphQL-Paginierung verwenden {#use-aem-graphql-pagination}

**Empfehlung**

Die Reaktionszeit komplexer Abfragen mit großen Ergebnismengen kann durch die Segmentierung von Antworten in Blöcke mithilfe der Paginierung (ein GraphQL-Standard) verbessert werden.

GraphQL in AEM unterstützt zwei Arten der Paginierung:

* [Limit-/Offset-basierte Paginierung](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#list-offset-limit)
Diese Methode wird für Listenabfragen verwendet; diese enden mit `List`; Beispiel: `articleList`.
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

#### GraphQL-Sortierung verwenden {#use-graphql-sorting}

**Empfehlung**

Die GraphQL-Standardsortierung ermöglicht es Kunden, JSON-Inhalte in sortierter Reihenfolge zu erhalten. Dies kann die Notwendigkeit einer weiteren Verarbeitung auf dem Client verringern.

Die Sortierung ist nur dann effizient, wenn sich alle Sortierungskriterien auf Fragmente der obersten Ebene beziehen.

Wenn die Sortierreihenfolge ein oder mehrere Felder enthält, die sich auf einem verschachtelten Fragment befinden, müssen alle Fragmente, die das Modell der obersten Ebene gemeinsam verwenden, in den Speicher geladen werden. Dies führt zu Leistungseinbußen.

>[!NOTE]
>
>Die Sortierung der Felder der obersten Ebene wirkt sich ebenfalls (wenn auch geringfügig) auf die Leistung aus.

**Weitere Informationen**

Siehe:

* [Beispielabfrage mit Filtern nach _tags-ID und Ausschließen von Varianten und Sortieren nach Namen](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md#sample-filtering-tag-not-variations)

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

Das Verschachteln von Inhaltsfragmenten ist eine hervorragende Möglichkeit, benutzerdefinierte Inhaltsstrukturen zu modellieren. Sie können sogar ein Fragment mit einem verschachtelten Fragment mit einem verschachtelten Fragment haben, das ... usw. aufweist.

Das Erstellen einer Struktur mit zu vielen Ebenen kann jedoch die Verarbeitungszeiten für eine GraphQL-Abfrage erhöhen, da GraphQL die gesamte Hierarchie aller verschachtelten Inhaltsfragmente durchlaufen muss.

Tiefes Verschachteln kann sich auch nachteilig auf die Inhaltsverwaltung auswirken. Im Allgemeinen wird empfohlen, die Verschachtelung von Inhaltsfragmenten auf weniger als fünf oder sechs Ebenen zu beschränken.

### Nicht alle Formate ausgeben (mehrzeilige Textelemente) {#do-not-output-all-formats}

AEM GraphQL kann Text zurückgeben, der im **[Mehrzeiliger Text](/help/assets/content-fragments/content-fragments-models.md#data-types)** Datentyp in mehreren Formaten: Rich-Text, Einfacher Text und Markdown.

Die Ausgabe aller drei Formate erhöht die Größe der Textausgabe in JSON um den Faktor drei. Dies kann zusammen mit im Allgemeinen großen Ergebnismengen aus sehr breiten Abfragen sehr große JSON-Antworten generieren, die daher lange für die Berechnung benötigen. Es ist besser, die Ausgabe auf die Textformate zu beschränken, die für die Wiedergabe des Inhalts erforderlich sind.

### Ändern von Inhaltsfragmenten {#modifying-content-fragments}

Ändern Sie nur Inhaltsfragmente und deren Ressourcen mithilfe der AEM-Benutzeroberfläche oder APIs. Nehmen Sie keine Änderungen direkt in JCR vor.

### Abfragen testen {#test-your-queries}

Die Verarbeitung von GraphQL-Abfragen ähnelt der Verarbeitung von Suchabfragen und ist wesentlich komplexer als einfache API-Anfragen für GET-alle-Inhalte.

Eine sorgfältige Planung, Prüfung und Optimierung Ihrer Abfragen in einer kontrollierten Nicht-Produktionsumgebung ist für den späteren Erfolg bei der Verwendung in der Produktion von entscheidender Bedeutung.
