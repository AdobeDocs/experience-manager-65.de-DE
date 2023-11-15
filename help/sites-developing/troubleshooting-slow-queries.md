---
title: Fehlerbehebung bei langsamen Abfragen
seo-title: Troubleshooting Slow Queries
description: Erfahren Sie, wie Sie in Adobe Experience Manager Probleme mit langsamen Abfragen beheben können.
seo-description: null
uuid: ad09546a-c049-44b2-99a3-cb74ee68f040
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: c01e42ff-e338-46e6-a961-131ef943ea91
exl-id: 3405cdd3-3d1b-414d-9931-b7d7b63f0a6f
source-git-commit: 7f35fdee9dbca9dfd3992b56579d6d06633f8dec
workflow-type: tm+mt
source-wordcount: '2268'
ht-degree: 97%

---

# Fehlerbehebung bei langsamen Abfragen{#troubleshooting-slow-queries}

## Klassifizierungen langsamer Abfragen {#slow-query-classifications}

Es gibt drei Hauptklassifizierungen langsamer Abfragen in AEM, die nach Schweregrad aufgelistet sind:

1. **Abfragen ohne Index**

   * Abfragen, die **nicht** auf einen Index auflösen und den Inhalt des JCR durchlaufen, um Ergebnisse zu sammeln

1. **Abfragen mit schlechter Einschränkung (oder schlechtem Bereich)**

   * Abfragen, die auf einen Index aufgelöst werden, aber alle Indexeinträge durchlaufen müssen, um Ergebnisse zu sammeln

1. **Abfragen mit vielen Ergebnissen**

   * Abfragen, die eine große Anzahl von Ergebnissen zurückgeben

Die ersten beiden Klassifizierungen von Abfragen (ohne Index und mit schlechter Einschränkung) sind langsam. Sie sind langsam, weil sie die Oak-Abfrage-Engine zwingen, jedes **potenzielle** Ergebnis (Inhaltsknoten oder Indexeintrag) zu untersuchen, um festzustellen, welche in die **eigentliche** Ergebnismenge gehören.

Die Untersuchung jedes potenziellen Ergebnisses wird als „Durchlaufen“ bezeichnet.

Da jedes potenzielle Ergebnis überprüft werden muss, steigen die Kosten zur Bestimmung des tatsächlichen Ergebnissatzes linear mit der Anzahl potenzieller Ergebnisse.

Durch das Hinzufügen von Abfragebeschränkungen und das Anpassen von Indizes können die Indexdaten in einem optimierten Format gespeichert werden, das einen schnellen Abruf der Ergebnisse ermöglicht und die lineare Inspektion potenzieller Ergebnismengen verringert oder beseitigt.

In AEM 6.3 schlägt eine Abfrage standardmäßig fehl und löst einen Ausnahmefehler aus, wenn 100.000 potenzielle Ergebnisse durchlaufen wurden. Dieser Grenzwert gilt in AEM-Versionen vor AEM 6.3 standardmäßig nicht, kann jedoch über die Einstellungen der Apache Jackrabbit-Abfrage-Engine in der OSGi-Konfiguration und dem QueryEngineSettings-JMX-Bean (Eigenschaft LimitReads) festgelegt werden.

### Erkennen von Abfragen ohne Index {#detecting-index-less-queries}

#### Während der Entwicklung {#during-development}

Erklären Sie **alle** Abfragen und stellen Sie sicher, dass ihre Abfragepläne nicht die Erklärung **/* traverse** enthalten. Beispiel für das Durchlaufen eines Abfrageplans:

* **PLAN:** `[nt:unstructured] as [a] /* traverse "/content//*" where ([a].[unindexedProperty] = 'some value') and (isdescendantnode([a], [/content])) */`

#### Nach der Bereitstellung {#post-deployment}

* Überwachen Sie `error.log` nach Index-losen Durchlaufabfragen:

   * `*INFO* org.apache.jackrabbit.oak.query.QueryImpl Traversal query (query without index) ... ; consider creating and index`
   * Diese Meldung wird nur protokolliert, wenn kein Index verfügbar ist und die Abfrage potenziell viele Knoten durchläuft. Nachrichten werden nicht protokolliert, wenn ein Index verfügbar ist, aber die Anzahl der Durchläufe gering und daher schnell ist.

* Besuchen Sie die AEM-Betriebskonsole [Abfrageleistung](/help/sites-administering/operations-dashboard.md#query-performance) und [erklären Sie](/help/sites-administering/operations-dashboard.md#explain-query) langsame Abfragen, die einen Durchlauf durchführen werden oder keine Index-Abfrageerklärungen aufweisen.

### Erkennen von Abfragen mit schlechter Einschränkung {#detecting-poorly-restricted-queries}

#### Während der Entwicklung {#during-development-1}

Erklären Sie alle Abfragen und stellen Sie sicher, dass sie in einen Index aufgelöst werden, der an die Eigenschaftsbeschränkungen der Abfrage angepasst ist.

* Bei einer idealen Abdeckung des Abfrageplans sind `indexRules` für alle Eigenschaftsbeschränkungen vorhanden, mindestens aber für die strengsten Eigenschaftsbeschränkungen in der Abfrage.
* Abfragen, die Ergebnisse sortieren, sollten auf einen Lucene-Eigenschaftsindex mit Indexregeln für die Sortierungseigenschaften aufgelöst werden, die `orderable=true.` setzen.

#### Der standardmäßige `cqPageLucene` beispielsweise hat keine Indexregel für `jcr:content/cq:tags` {#for-example-the-default-cqpagelucene-does-not-have-an-index-rule-for-jcr-content-cq-tags}

Vor dem Hinzufügen der cq:tags-Indexregel

* **cq:tags-Index-Regel**

   * Nicht standardmäßig vorhanden

* **Query Builder-Abfrage**

  ```js
  type=cq:Page
  property=jcr:content/cq:tags
  property.value=my:tag
  ```

* **Abfrageplan**

  `[cq:Page] as [a] /* lucene:cqPageLucene(/oak:index/cqPageLucene) *:* where [a].[jcr:content/cq:tags] = 'my:tag' */`

Diese Abfrage wird auf den Index `cqPageLucene` aufgelöst. Da jedoch keine Eigenschaftsindexregel für `jcr:content` oder `cq:tags` vorhanden ist, wird bei der Prüfung der Einschränkung jeder Datensatz im Index `cqPageLucene` auf Übereinstimmung geprüft. Wenn also der Index 1 Million `cq:Page`-Knoten enthält, werden 1 Million Datensätze geprüft, um die Ergebnismenge zu ermitteln.

Nach dem Hinzufügen der cq:tags-Indexregel

* **cq:tags-Index-Regel**

  ```js
  /oak:index/cqPageLucene/indexRules/cq:Page/properties/cqTags
  @name=jcr:content/cq:tags
  @propertyIndex=true
  ```

* **Query Builder-Abfrage**

  ```js
  type=cq:Page
  property=jcr:content/cq:tags
  property.value=myTagNamespace:myTag
  ```

* **Abfrageplan**

  `[cq:Page] as [a] /* lucene:cqPageLucene(/oak:index/cqPageLucene) jcr:content/cq:tags:my:tag where [a].[jcr:content/cq:tags] = 'my:tag' */`

Durch Hinzufügen der indexRule für `jcr:content/cq:tags` im Index `cqPageLucene` können `cq:tags`-Daten optimal gespeichert werden.

Wenn eine Abfrage mit der Einschränkung `jcr:content/cq:tags` durchgeführt wird, kann der Index Ergebnisse nach Wert abfragen. Wenn also 100 `cq:Page`-Knoten den Wert `myTagNamespace:myTag` aufweisen, werden nur diese 100 Ergebnisse zurückgegeben. Die übrigen 999.000 werden aus den Einschränkungsprüfungen ausgeschlossen, was die Leistung um den Faktor 10.000 verbessert.

Weitere Abfragebeschränkungen verringern die möglichen Ergebnismengen und erlauben eine weitere Abfrageoptimierung.

Ebenso würde ohne eine weitere Indexregel für die Eigenschaft `cq:tags` selbst eine Volltextabfrage mit einer Einschränkung auf `cq:tags` schlecht abschneiden, da die Ergebnisse aus dem Index alle Volltexttreffer zurückgeben würden. Die Einschränkung auf cq:tags würde anschließend gefiltert werden.

Eine weitere Ursache für ein Filtern nach dem Index sind Zugangssteuerungslisten, die bei der Entwicklung oft übersehen werden. Versuchen Sie sicherzustellen, dass die Abfrage keine Pfade zurückgibt, auf die die Benutzenden möglicherweise nicht zugreifen können. Dies kann durch eine bessere Inhaltsstruktur sowie durch Bereitstellung relevanter Pfadbeschränkungen für die Abfrage erfolgen.

Eine nützliche Methode, um festzustellen, ob der Lucene-Index viele Ergebnisse zurückgibt, von denen nur eine kleine Teilmenge als Abfrageergebnis zurückgegeben wird, besteht darin, DEBUG-Protokolle für `org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex` zu aktivieren. Auf diese Weise können Sie sehen, wie viele Dokumente aus dem Index geladen werden. Die Anzahl der letztendlichen Ergebnisse sollte nicht unverhältnismäßig gering im Vergleich zur Anzahl der geladenen Dokumente sein. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).

#### Nach der Bereitstellung {#post-deployment-1}

* Überwachen Sie das `error.log` für Durchlaufabfragen:

   * `*WARN* org.apache.jackrabbit.oak.spi.query.Cursors$TraversingCursor Traversed ### nodes ... consider creating an index or changing the query`

* Besuchen Sie die in der AEM-Betriebskonsole [Abfrageleistung](/help/sites-administering/operations-dashboard.md#query-performance) und [erklären](/help/sites-administering/operations-dashboard.md#explain-query) Sie langsame Abfragen, wobei Sie nach Abfrageplänen suchen, die Abfrageeigenschaftseinschränkungen nicht in Indexeigenschaftsregeln auflösen.

### Erkennen von Abfragen mit großen Ergebnismengen {#detecting-large-result-set-queries}

#### Während der Entwicklung {#during-development-2}

Setzen Sie niedrige Schwellenwerte für oak.queryLimitInMemory (z. B. 10000) und oak.queryLimitReads (z. B. 5000) und optimieren Sie die teure Abfrage, wenn Sie auf eine UnsupportedOperationException treffen, die besagt: „Die Abfrage las mehr als x Knoten …“.

Die Festlegung niedriger Schwellenwerte verhindert ressourcenintensive Abfragen (d. h. nicht durch einen Index unterlegt oder durch einen Index mit geringerer Abdeckung unterlegt). Beispielsweise würde eine Abfrage, die eine Million Knoten liest, zu vielen E/A führen und die Gesamtleistung der Anwendung negativ beeinflussen. Daher sollte jede Abfrage, die aufgrund der obigen Beschränkungen fehlschlägt, analysiert und optimiert werden.

#### Nach der Bereitstellung {#post-deployment-2}

* Überwachen Sie die Protokolle auf Abfragen, die eine hohe Anzahl durchlaufener Knoten oder einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * Optimieren Sie die Abfrage so, dass Sie die Anzahl der durchlaufenen Knoten reduzieren.

* Überwachen Sie die Protokolle auf Abfragen, die einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimieren Sie die Abfrage, um den Heap-Speicherverbrauch zu reduzieren.

Für die AEM-Versionen 6.0 bis 6.2 können Sie den Schwellenwert für das Durchlaufen von Knoten über JVM-Parameter im AEM-Startskript abstimmen, um zu verhindern, dass die Umgebung durch umfangreiche Abfragen überlastet wird. Folgende Werte werden empfohlen:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3 sind die beiden oben stehenden Parameter standardmäßig vorkonfiguriert und können über die OSGi QueryEngineSettings bearbeitet werden.

Weitere Informationen finden Sie unter: [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Optimierung der Abfrageleistung {#query-performance-tuning}

Das Motto der Optimierung der Abfrageleistung in AEM lautet:

**„Je mehr Einschränkungen, desto besser.“**

Im Folgenden werden die empfohlenen Anpassungen zur Gewährleistung einer guten Abfrageleistung beschrieben. Passen Sie zunächst die Abfrage an (ein geringfügiger Eingriff) und anschließend, wenn nötig, die Index-Definitionen.

### Anpassen der Abfrageanweisung {#adjusting-the-query-statement}

AEM unterstützt die folgenden Abfragesprachen:

* Query Builder
* JCR-SQL2
* XPath

Im folgenden Beispiel wird Query Builder als die gängigste Abfragesprache verwendet, die von AEM-Entwicklern verwendet wird. Die gleichen Prinzipien gelten jedoch für JCR-SQL2 und XPath.

1. Fügen Sie eine Knotentyp-Einschränkung hinzu, sodass die Abfrage auf einen vorhandenen Lucene-Eigenschaftsindex aufgelöst wird.

* **Nicht optimierte Abfrage**

  ```js
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Optimierte Abfrage**

  ```js
  type=cq:Page
  property=jcr:content/contentType
  property.value=article-page
  ```

  Bei Abfragen ohne Knotentyp-Einschränkung muss AEM den nodetype `nt:base` annehmen. Da jeder Knoten in AEM davon ein Untertyp ist, führt dies effektiv zu keiner Knotentyp-Einschränkung.

  Wenn Sie `type=cq:Page` setzen, wird die Abfrage auf `cq:Page`-Knoten beschränkt und auf cqPageLucene von AEM aufgelöst. Dadurch werden die Ergebnisse auf eine Untergruppe von Knoten (nur `cq:Page`-Knoten) in AEM beschränkt.

1. Passen Sie die Knotentyp-Einschränkung der Abfrage an, sodass sie auf einen vorhandenen Lucene-Eigenschaftsindex aufgelöst wird.

* **Nicht optimierte Abfrage**

  ```js
  type=nt:hierarchyNode
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Optimierte Abfrage**

  ```js
  type=cq:Page
  property=jcr:content/contentType
  property.value=article-page
  ```

  `nt:hierarchyNode` ist der übergeordnete Knotentyp von `cq:Page`. Unter der Annahme, dass `jcr:content/contentType=article-page` über die benutzerdefinierte Anwendung von Adobe nur auf `cq:Page`-Knoten angewendet wird, gibt diese Abfrage nur `cq:Page`-Knoten zurück, bei denen `jcr:content/contentType=article-page` gilt. Dieser Fluss ist jedoch aus folgenden Gründen eine suboptimale Beschränkung:

   * Andere Knoten erben von `nt:hierarchyNode` (z. B. `dam:Asset`), wodurch die Menge der möglichen Ergebnisse unnötig vergrößert wird.
   * Es gibt keinen von AEM bereitgestellten Index für `nt:hierarchyNode`. Ein Index ist jedoch für `cq:Page` vorhanden.

  Wenn Sie `type=cq:Page` setzen, wird die Abfrage auf `cq:Page`-Knoten beschränkt und auf cqPageLucene von AEM aufgelöst. Dadurch werden die Ergebnisse auf eine Untergruppe von Knoten (nur cq:Page-Knoten) in AEM beschränkt.

1. Sie können auch die Eigenschaftsbeschränkungen anpassen, sodass die Abfrage auf einen vorhandenen Eigenschaftsindex aufgelöst wird.

* **Nicht optimierte Abfrage**

  ```js
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Optimierte Abfrage**

  ```js
  property=jcr:content/sling:resourceType
  property.value=my-site/components/structure/article-page
  ```

  Durch das Ändern der Eigenschaftsbeschränkung von `jcr:content/contentType` (ein benutzerdefinierter Wert) auf die bekannte Eigenschaft `sling:resourceType` kann die Abfrage auf den Eigenschaftsindex `slingResourceType`, der alle Inhalte nach `sling:resourceType` indiziert, aufgelöst werden.

  Eigenschaftsindizes (im Gegensatz zu Lucene-Eigenschaftsindizes) eignen sich am besten, wenn die Abfrage nicht nach Knotentyp unterscheidet und eine einzige Eigenschaftsbeschränkung die Ergebnismenge beherrscht.

1. Fügen Sie der Abfrage die strengstmögliche Pfadbeschränkung hinzu. Beispielsweise soll `/content/my-site/us/en` gegenüber `/content/my-site` oder `/content/dam` gegenüber `/` bevorzugt werden.

* **Nicht optimierte Abfrage**

  ```js
  type=cq:Page
  path=/content
  property=jcr:content/contentType
  property.value=article-page
  ```

* **Optimierte Abfrage**

  ```js
  type=cq:Page
  path=/content/my-site/us/en
  property=jcr:content/contentType
  property.value=article-page
  ```

  Wenn Sie die Pfadbeschränkung von `path=/content` auf `path=/content/my-site/us/en` ändern, können die Indizes die Anzahl der zu prüfenden Indexeinträge senken. Wenn die Abfrage den Pfad besser als nur mit `/content` oder `/content/dam` einschränken kann, stellen Sie sicher, dass für den Index `evaluatePathRestrictions=true` gilt.

  Beachten Sie, dass die Verwendung von `evaluatePathRestrictions` den Index vergrößert.

1. Wenn möglich, vermeiden Sie Abfragefunktionen und Abfrageoperationen wie `LIKE` und `fn:XXXX`, da deren Kosten mit der Anzahl der einschränkungsbasierten Ergebnisse steigen.

* **Nicht optimierte Abfrage**

  ```js
  type=cq:Page
  property=jcr:content/contentType
  property.operation=like
  property.value=%article%
  ```

* **Optimierte Abfrage**

  ```js
  type=cq:Page
  fulltext=article
  fulltext.relPath=jcr:content/contentType
  ```

  Die Bedingung LIKE wird langsam geprüft, da kein Index verwendet werden kann, wenn der Text mit einem Platzhalter (&quot;%...&#39;) beginnt. Die Bedingung jcr: ermöglicht die Verwendung eines Volltext-Index und wird daher bevorzugt. Der aufgelöste Lucene-Eigenschaftsindex benötigt dazu indexRule für `jcr:content/contentType` mit `analayzed=true`.

  Das Verwenden von Abfragefunktionen wie `fn:lowercase(..)` kann schwieriger zu optimieren sein, da es keine schnelleren Äquivalente gibt (abgesehen von komplexeren und aufdringlicheren Indexanalysekonfigurationen). Es ist am besten, andere Scoping-Einschränkungen zu identifizieren, um die Gesamtabfrageleistung zu verbessern, sodass die Funktionen nur auf die kleinstmögliche Anzahl möglicher Ergebnisse angewendet werden müssen.

1. ***Diese Anpassung ist nur in Query Builder möglich und gilt nicht für JCR-SQL2 oder XPath.***

   Verwenden Sie [guessTotal in Query Builder](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results), wenn die vollständige Ergebnismenge **nicht** sofort benötigt wird.

   * **Nicht optimierte Abfrage**

     ```js
     type=cq:Page
     path=/content
     ```

   * **Optimierte Abfrage**

     ```js
     type=cq:Page
     path=/content
     p.guessTotal=100
     ```

   Wenn die Abfrage schnell ausgeführt wird, aber sehr viele Ergebnisse zurückgibt, stellt p.`guessTotal` eine wichtige Optimierung für Query Builder-Abfragen dar.

   `p.guessTotal=100` weist Query Builder an, nur die ersten 100 Ergebnisse zu erfassen. Und dazu, eine boolesche Markierung zu setzen, die angibt, ob mindestens ein weiteres Ergebnis vorhanden ist (aber nicht wie viele weitere Ergebnisse, da die Zählung dieser Zahl zu einer Verlangsamung führt). Diese Optimierung eignet sich hervorragend für Anwendungsfälle mit Paginierung oder endlosem Laden, bei denen nur eine Teilmenge der Ergebnisse schrittweise angezeigt wird.

## Vorhandene Indexabstimmung {#existing-index-tuning}

1. Wenn die optimale Abfrage auf einen Eigenschaftsindex aufgelöst wird, gibt es nichts mehr zu tun, da Eigenschaftsindizes nur minimale Anpassungsmöglichkeiten bieten.
1. Andernfalls sollte die Abfrage auf einen Lucene-Eigenschaftsindex aufgelöst werden. Wenn kein Index aufgelöst werden kann, springen Sie zu Erstellen eines Index .
1. Konvertieren Sie die Abfrage nach Bedarf in XPath oder JCR-SQL2.

   * **Query Builder-Abfrage**

     ```js
     query type=cq:Page
     path=/content/my-site/us/en
     property=jcr:content/contentType
     property.value=article-page
     orderby=@jcr:content/publishDate
     orderby.sort=desc
     ```

   * **Aus der Query Builder-Abfrage generierter XPath**

     ```js
     /jcr:root/content/my-site/us/en//element(*, cq:Page)[jcr:content/@contentType = 'article-page'] order by jcr:content/@publishDate descending
     ```

1. Geben Sie den XPath (oder JCR-SQL2) an den Oak Index Definition Generator unter `https://oakutils.appspot.com/generate/index` weiter, damit Sie die optimierte Lucene-Eigenschaftsindex-Definition generieren können. <!-- The above URL is 404 as of April 24, 2023 -->

   **Generierte Lucene-Eigenschaftsindex-Definition**

   ```xml
   - evaluatePathRestrictions = true
   - compatVersion = 2
   - type = "lucene"
   - async = "async"
   - jcr:primaryType = oak:QueryIndexDefinition
       + indexRules
       + cq:Page
           + properties
           + contentType
               - name = "jcr:content/contentType"
               - propertyIndex = true
           + publishDate
               - ordered = true
               - name = "jcr:content/publishDate"
   ```

1. Führen Sie manuell die generierte Definition additiv mit dem vorhandenen Lucene-Eigenschaftsindex zusammen. Achten Sie darauf, dass Sie keine vorhandenen Konfigurationen entfernen, da sie möglicherweise zum Erfüllen anderer Abfragen verwendet werden.

   1. Suchen Sie nach dem vorhandenen Lucene-Eigenschaftsindex, der cq:Page abdeckt (mithilfe von Index Manager). In diesem Fall, `/oak:index/cqPageLucene`.
   1. Identifizieren Sie die Konfigurationsunterschiede zwischen der optimierten Indexdefinition (Schritt 4) und dem vorhandenen Index (/oak:index/cqPageLucene) und fügen Sie die fehlenden Konfigurationen aus dem optimierten Index zur vorhandenen Indexdefinition hinzu.
   1. Gemäß der Best Practices zur Neuindizierung in AEM müssen Sie entweder eine Aktualisierung oder eine Neuindizierung durchführen, je nachdem, ob vorhandene Inhalte von dieser Indexkonfigurationsänderung betroffen sind oder nicht.

## Erstellen eines neuen Index {#create-a-new-index}

1. Vergewissern Sie sich, dass die Abfrage nicht auf einen vorhandenen Lucene-Eigenschaftsindex aufgelöst wird. Ist dies der Fall, lesen Sie den obigen Abschnitt zur Optimierung und zum vorhandenen Index.
1. Konvertieren Sie die Abfrage nach Bedarf in XPath oder JCR-SQL2.

   * **Query Builder-Abfrage**

     ```js
     type=myApp:Author
     property=firstName
     property.value=ira
     ```

   * **Aus der Query Builder-Abfrage generierter XPath**

     ```js
     //element(*, myApp:Page)[@firstName = 'ira']
     ```

1. Geben Sie den XPath (oder JCR-SQL2) an den Oak Index Definition Generator unter `https://oakutils.appspot.com/generate/index` weiter, damit Sie die optimierte Lucene-Eigenschaftsindex-Definition generieren können. <!-- The above URL is 404 as of April 24, 2023 -->

   **Generierte Lucene-Eigenschaftsindex-Definition**

   ```xml
   - compatVersion = 2
   - type = "lucene"
   - async = "async"
   - jcr:primaryType = oak:QueryIndexDefinition
       + indexRules
       + myApp:AuthorModel
           + properties
           + firstName
               - name = "firstName"
               - propertyIndex = true
   ```

1. Stellen Sie die generierte Lucene-Eigenschaftsindex-Definition bereit.

   Fügen Sie die XML-Definition hinzu, die der Oak Index Definition Generator für den neuen Index für das AEM-Projekt, der Oak Index-Definitionen verwaltet, bereitgestellt hat. (Denken Sie daran, Oak Index-Definitionen als Code zu behandeln, da Code davon abhängt).

   Stellen Sie den neuen Index bereit, testen Sie ihn nach dem üblichen Lebenszyklus für die AEM-Software-Entwicklung und überprüfen Sie, ob die Abfrage auf den Index aufgelöst wird und leistungsstark ist.

   Bei der ersten Bereitstellung dieses Index füllt AEM den Index mit den erforderlichen Daten.

## Wann sind indexlose und Durchlaufabfragen sinnvoll? {#when-index-less-and-traversal-queries-are-ok}

Aufgrund der flexiblen Inhaltsarchitektur von AEM ist es schwierig, die Durchläufe von Inhaltsstrukturen vorherzusagen und sicherzustellen, dass sie nicht im Laufe der Zeit auf eine inakzeptable Größe anwachsen.

Stellen Sie daher sicher, dass Indizes Abfragen erfüllen, es sei denn, die Kombination aus Pfad- und Knotentyp-Beschränkungen garantiert, dass **nie mehr als 20 Knoten durchlaufen werden.**

## Tools zur Abfrageentwicklung {#query-development-tools}

### Unterstützt von Adobe {#adobe-supported}

* **Query Builder-Debugger**

   * Eine WebUI für die Ausführung von Query Builder-Abfragen und die Generierung des unterstützenden XPath (zur Verwendung in „Abfrage erläutern“ oder im Oak Index Definition Generator).
   * In AEM unter [/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)

* **CRXDE Lite – Abfrage-Tool**

   * Eine WebUI zum Ausführen von XPath- und JCR-SQL2-Abfragen.
   * In AEM unter [/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp) > „Tools“ > „Abfrage…“

* **[Abfrage erläutern](/help/sites-administering/operations-dashboard.md#explain-query)**

   * Ein AEM Operations-Dashboard, das für jede XPATH- oder JCR-SQL2-Abfrage eine detaillierte Erklärung bietet (Abfrageplan, Abfragezeit und Anzahl der Ergebnisse).

* **[Langsame/beliebte Abfragen](/help/sites-administering/operations-dashboard.md#query-performance)**

   * Ein AEM Operations-Dashboard, das langsame und beliebte Abfragen auflistet, die kürzlich auf AEM ausgeführt wurden.

* **[Index-Manager](/help/sites-administering/operations-dashboard.md#the-index-manager)**

   * Eine AEM Operations-WebUI, die die Indizes auf der AEM-Instanz anzeigt; erleichtert das Verständnis, welche Indizes vorhanden sind; kann angesprochen oder erweitert werden.

* **[Protokollierung](/help/sites-administering/operations-dashboard.md#log-messages)**

   * Query Builder-Protokollierung

      * `DEBUG @ com.day.cq.search.impl.builder.QueryImpl`

   * Oak Query-Ausführungsprotokollierung

      * `DEBUG @ org.apache.jackrabbit.oak.query`

* **OSGi-Konfiguration der Apache Jackrabbit Query Engine-Einstellungen**

   * OSGi-Konfiguration, die das Fehlerverhalten bei Durchlaufabfragen konfiguriert.
   * In AEM unter [/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService](http://localhost:4502/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService)

* **NodeCounter JMX MBean**

   * JMX MBean wird verwendet, um die Anzahl der Knoten in Inhaltsstrukturen in AEM zu schätzen.
   * In AEM unter [/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter)

### Community-Unterstützung {#community-supported}

* **Oak Index Definition Generator unter`https://oakutils.appspot.com/generate/index`** <!-- The above URL is 404 as of April 24, 2023 -->

   * Generieren Sie optimale Lucence-Eigenschafts-Indizes aus XPath- oder JCR-SQL2-Abfragen.

* **[AEM-Chrome-Plug-in](https://chrome.google.com/webstore/detail/aem-chrome-plug-in/ejdcnikffjleeffpigekhccpepplaode?hl=de-DE)**

   * Eine Webbrowser-Erweiterung für Google Chrome, die Protokolldaten für einzelne Anfragen, z. B. ausgeführte Abfragen und ihre Abfragepläne, in der Entwicklerkonsole des Browsers ausgibt.
   * [Sling Log Tracer 1.0.2+](https://sling.apache.org/downloads.cgi) muss dazu installiert und in AEM aktiviert sein.
