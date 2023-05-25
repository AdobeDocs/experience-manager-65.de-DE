---
title: Optimieren von GraphQL-Abfragen
description: Erfahren Sie, wie Sie Ihre GraphQL-Abfragen beim Filtern, Paging und Sortieren Ihrer Inhaltsfragmente in Adobe Experience Manager as a Cloud Service für die Headless-Content-Bereitstellung optimieren können.
source-git-commit: 1481d613783089046b44d4652d38f7b4b16acc4d
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 58%

---


# Optimieren von GraphQL-Abfragen {#optimizing-graphql-queries}

>[!NOTE]
>
>Bevor Sie diese Optimierungsempfehlungen anwenden, sollten Sie [Aktualisieren Ihrer Inhaltsfragmente für Paging und Sortierung in GraphQL-Filterung](/help/sites-developing/headless/graphql-api/graphql-optimized-filtering-content-update.md) für beste Leistung.

Auf einer AEM Instanz mit einer großen Anzahl von Inhaltsfragmenten, die vom selben Modell gemeinsam verwendet werden, können GraphQL-Listenabfragen (im Hinblick auf Ressourcen) teuer werden.

Der Grund dafür ist, dass *all* Fragmente, die ein in der GraphQL-Abfrage verwendetes Modell gemeinsam verwenden, müssen in den Speicher geladen werden. Dies verbraucht sowohl Zeit als auch Speicher. Eine Filterung, die die Anzahl der Elemente in der (endgültigen) Ergebnismenge verringern kann, kann nur **nach** dem Laden des gesamten Ergebnissatzes in den Speicher angewendet werden.

Dieser Prozess kann den Eindruck erwecken, dass auch kleine Ergebnismengen zu schlechter Leistung führen können. In Wirklichkeit wird die Langsamkeit jedoch durch die Größe der ursprünglichen Ergebnismenge verursacht, da sie intern verarbeitet werden muss, bevor die Filterung angewendet werden kann.

Um Leistungs- und Speicherprobleme zu vermeiden, muss diese anfängliche Ergebnismenge so klein wie möglich gehalten werden.

AEM bietet zwei Methoden zur Optimierung von GraphQL-Abfragen:

* [Hybride Filterung](#hybrid-filtering)
* [Paging](#paging) (oder Paginierung)

   * [Sortierung](#sorting) ist nicht direkt mit der Optimierung verbunden, sondern mit dem Paging

Jede Methode beinhaltet eigene Anwendungsfälle und Einschränkungen. In diesem Dokument finden Sie Informationen zur hybriden Filterung und zum Paging sowie einige [Best Practices](#best-practices), um GraphQL-Abfragen zu optimieren.

## Hybride Filterung {#hybrid-filtering}

Hybride Filterung kombiniert JCR-Filterung mit AEM-Filterung.

Dabei wird ein JCR-Filter (in Form einer Abfragebegrenzung) angewendet, bevor der Ergebnissatz zur AEM-Filterung in den Speicher geladen wird. Dieser Prozess dient dazu, den in den Speicher geladenen Ergebnissatz zu reduzieren, da der JCR-Filter überflüssige Ergebnisse zuvor entfernt.

>[!NOTE]
>
>Aus technischen Gründen (z. B. Flexibilität, Verschachtelung von Fragmenten) kann AEM die gesamte Filterung nicht an JCR delegieren.

Bei dieser Methode wird die Flexibilität bewahrt, die GraphQL-Filter bieten, während gleichzeitig ein möglichst großer Teil der Filterung an JCR delegiert wird.

## Paging {#paging}

GraphQL in AEM unterstützt zwei Arten der Paginierung:

* [begrenzungs-/offset-basierte Paginierung](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#list-offset-limit)
Dieser Seitentyp wird für Listenabfragen verwendet. diese Abfragen enden mit 
`List`; Beispiel: `articleList`.
Um sie zu verwenden, müssen Sie die Position des ersten Elements angeben, das zurückgegeben werden soll (`offset`) und die Anzahl der zurückzugebenden Elemente (`limit` oder Seitengröße).

* [Cursorbasierte Paginierung](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#paginated-first-after) (vertreten durch `first`und `after`) Dieser Seitentyp stellt eine eindeutige ID für jedes Element bereit. auch als Cursor bezeichnet.
In der Abfrage geben Sie den Cursor des letzten Elements der vorherigen Seite sowie die Seitengröße (die maximale Anzahl der zurückzugebenden Elemente) an.

   Da die Cursor-basierte Paginierung nicht zu den Datenstrukturen von listenbasierten Abfragen passt, hat AEM den Abfragetyp `Paginated` eingeführt, zum Beispiel `articlePaginated`. Die verwendeten Datenstrukturen und Parameter entsprechen der [GraphQL Cursor ConnectionSpecification](https://relay.dev/graphql/connections.htm).

   >[!NOTE]
   >
   >AEM unterstützt derzeit Forward Paging (unter Verwendung der Parameter `after`/`first`).
   >
   >Backward Paging (mithilfe der Parameter `before`/`last`) wird nicht unterstützt.

## Sortierung {#sorting}

Die Sortierung ist nur dann effizient, wenn sich alle Sortierungskriterien auf Fragmente der obersten Ebene beziehen.

Wenn die Sortierreihenfolge ein oder mehrere Felder enthält, die sich auf einem verschachtelten Fragment befinden, müssen alle Fragmente, die das Modell der obersten Ebene gemeinsam verwenden, in den Speicher geladen werden. Dieser Fluss verursacht negative Auswirkungen auf die Leistung.

>[!NOTE]
>
>Die Sortierung der Felder der obersten Ebene wirkt sich ebenfalls (wenn auch geringfügig) auf die Leistung aus.

## Best Practices {#best-practices}

Das Hauptziel aller Optimierungsmaßnahmen besteht darin, die anfängliche Ergebnismenge zu reduzieren. Die hier aufgeführten Best Practices bieten Möglichkeiten dazu. Sie können (und sollten) kombiniert werden.

### Nur nach Eigenschaften der obersten Ebene filtern {#filter-top-level-properties-only}

Derzeit funktioniert das Filtern auf JCR-Ebene nur für Fragmente der obersten Ebene.

Wenn sich ein Filter auf die Felder eines verschachtelten Fragments bezieht, muss AEM alle Fragmente, die das zugrunde liegende Modell gemeinsam nutzen, wieder in den Speicher laden.

Sie können diese GraphQL-Abfragen weiterhin optimieren, indem Sie Filterausdrücke für Felder von Fragmenten der obersten Ebene und für Felder verschachtelter Fragmente mit der [AND-Operator](#logical-operations-in-filter-expressions).

### Inhaltsstruktur verwenden {#use-content-structure}

In AEM wird empfohlen, die Repository-Struktur zu verwenden, um den Umfang der zu verarbeitenden Inhalte einzugrenzen.

Wenden Sie diesen Ansatz auf GraphQL-Abfragen an, indem Sie einen Filter auf die `_path` -Feld des Fragments der obersten Ebene:

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

Wenn Sie verschachtelte Fragmente filtern oder sortieren, können paginierte Abfragen immer noch langsam sein, da AEM immer noch größere Mengen von Fragmenten in den Speicher laden muss. Wenn Sie also Filtern und Paging kombinieren, sollten Sie die Filterregeln beachten (wie oben erwähnt).

Für das Paging ist die Sortierung gleichermaßen wichtig, da paginierte Ergebnisse immer sortiert werden, entweder explizit oder implizit.

Wenn Sie in erster Linie daran interessiert sind, nur die ersten Seiten abzurufen, gibt es keinen signifikanten Unterschied zwischen der Verwendung der `...List`- oder `...Paginated`-Abfragen. Wenn Ihre Anwendung jedoch daran interessiert ist, mehr als ein oder zwei Seiten zu lesen, sollten Sie die `...Paginated`-Abfrage in Erwägung ziehen, da sie bei den späteren Seiten deutlich besser funktioniert.

### Logische Vorgänge in Filterausdrücken {#logical-operations-in-filter-expressions}

Wenn Sie nach verschachtelten Fragmenten filtern, können Sie dennoch die JCR-Filterung anwenden, indem Sie einen begleitenden Filter für ein Feld der obersten Ebene bereitstellen, das mithilfe der `AND` Operator.

Ein typischer Anwendungsfall besteht darin, den Umfang der Abfrage mithilfe eines Filters auf die `_path` -Feld des Fragments der obersten Ebene. Filtern Sie dann nach zusätzlichen Feldern, die sich möglicherweise auf der obersten Ebene oder in einem verschachtelten Fragment befinden.

In diesem Fall würden die verschiedenen Filterausdrücke mit `AND` kombiniert. Daher kann der Filter auf `_path` die anfängliche Ergebnismenge effektiv einschränken. Alle anderen Filter auf Feldern der obersten Ebene können ebenfalls dazu beitragen, den anfänglichen Ergebnissatz zu reduzieren, sofern sie mit `AND` kombiniert werden.

Filterausdrücke, die mit `OR` kombiniert sind, können nicht optimiert werden, wenn verschachtelte Fragmente vorliegen. Solche `OR` -Ausdrücke können nur optimiert werden, wenn *no* verschachtelte Fragmente sind beteiligt.

### Vermeidung von Filtern bei mehrzeiliger Textfelder {#avoid-filtering-multiline-textfields}

Die Felder eines mehrzeiligen Textfelds (HTML, Markdown, plaintext, json) können nicht über eine JCR-Abfrage gefiltert werden, da der Inhalt dieser Felder dynamisch berechnet werden muss.

Wenn Sie weiterhin nach einem mehrzeiligen Textfeld filtern müssen, sollten Sie die Größe des ursprünglichen Ergebnissatzes einschränken, indem Sie zusätzliche Filterausdrücke hinzufügen und sie mit `AND`. Die Begrenzung des Umfangs durch Filterung des Felds `_path` ist auch ein guter Ansatz.

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

* Ausdrücke in einer `Calendar`, `Date`oder `Time` -Wert, der `NOT_AT` Operator.
