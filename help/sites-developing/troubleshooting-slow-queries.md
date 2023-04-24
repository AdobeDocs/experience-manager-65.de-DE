---
title: Fehlerbehebung bei langsamen Abfragen
seo-title: Troubleshooting Slow Queries
description: Fehlerbehebung bei langsamen Abfragen
seo-description: null
uuid: ad09546a-c049-44b2-99a3-cb74ee68f040
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: c01e42ff-e338-46e6-a961-131ef943ea91
exl-id: 3405cdd3-3d1b-414d-9931-b7d7b63f0a6f
source-git-commit: a296e459461973fc2dbd0641c6fdda1d89d8d524
workflow-type: tm+mt
source-wordcount: '2262'
ht-degree: 33%

---

# Fehlerbehebung bei langsamen Abfragen{#troubleshooting-slow-queries}

## Langsame Abfrageklassifizierungen {#slow-query-classifications}

Es gibt drei Hauptklassifizierungen langsamer Abfragen in AEM, die nach Schweregrad aufgelistet sind:

1. **Abfragen ohne Index**

   * Abfragen, die **not** in einen Index auflösen und den JCR-Inhalt durchlaufen, um Ergebnisse zu erfassen

1. **Unzulänglich eingeschränkte Abfragen (oder Bereiche)**

   * Abfragen, die zu einem Index aufgelöst werden, aber alle Indexeinträge durchlaufen müssen, um Ergebnisse zu erfassen

1. **Abfragen mit großen Ergebnismengen**

   * Abfragen, die eine große Anzahl von Ergebnissen zurückgeben

Die ersten beiden Classifications von Abfragen (indexlos und schlecht eingeschränkt) sind langsam. Sie sind langsam, da sie die Oak-Abfrage-Engine zwingen, jede **Potenzial** result (Inhaltsknoten oder Indexeintrag), um zu identifizieren, welche zum **tatsächlich** Ergebnismenge.

Die Untersuchung jedes potenziellen Ergebnisses wird als Durchlaufen bezeichnet.

Da jedes potenzielle Ergebnis überprüft werden muss, steigen die Kosten zur Bestimmung des tatsächlichen Ergebnissatzes linear mit der Anzahl potenzieller Ergebnisse.

Durch das Hinzufügen von Abfragebeschränkungen und das Anpassen von Indizes können die Indexdaten in einem optimierten Format gespeichert werden, das einen schnellen Abruf der Ergebnisse ermöglicht und die lineare Inspektion potenzieller Ergebnismengen verringert oder beseitigt.

In AEM 6.3 schlägt die Abfrage standardmäßig fehl und löst eine Ausnahme aus, wenn ein Durchlauf von 100.000 erreicht wird. Diese Beschränkung existiert nicht standardmäßig in AEM Versionen vor AEM 6.3, kann jedoch über die OSGi-Konfiguration Apache Jackrabbit Query Engine Settings und das JMX-Bean QueryEngine Settings (Eigenschaft LimitReads) festgelegt werden.

### Erkennen von Abfragen ohne Index {#detecting-index-less-queries}

#### Während der Entwicklung {#during-development}

Erklären **all** Abfragen und stellen sicher, dass ihre Abfragepläne nicht die **/&amp;ast; traverse** Erklärung. Beispiel für das Durchlaufen eines Abfrageplans:

* **PLAN:** `[nt:unstructured] as [a] /* traverse "/content//*" where ([a].[unindexedProperty] = 'some value') and (isdescendantnode([a], [/content])) */`

#### Nach der Bereitstellung {#post-deployment}

* Überwachen Sie `error.log` nach Index-losen Durchlaufabfragen:

   * `*INFO* org.apache.jackrabbit.oak.query.QueryImpl Traversal query (query without index) ... ; consider creating and index`
   * Diese Meldung wird nur protokolliert, wenn kein Index verfügbar ist und die Abfrage potenziell viele Knoten durchläuft. Nachrichten werden nicht protokolliert, wenn ein Index verfügbar ist, aber die Anzahl der Durchläufe ist gering und daher schnell.

* Besuchen Sie die AEM-Betriebskonsole [Abfrageleistung](/help/sites-administering/operations-dashboard.md#query-performance) und [erklären Sie](/help/sites-administering/operations-dashboard.md#explain-query) langsame Abfragen, die einen Durchlauf durchführen werden oder keine Index-Abfrageerklärungen aufweisen.

### Erkennen schlecht eingeschränkter Abfragen {#detecting-poorly-restricted-queries}

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

Diese Abfrage wird auf den Index `cqPageLucene` aufgelöst. Da jedoch keine Eigenschaftsindexregel für `jcr:content` oder `cq:tags` vorhanden ist, wird bei der Prüfung der Einschränkung jeder Datensatz im Index `cqPageLucene` auf Übereinstimmung geprüft. Enthält der Index 1 Million `cq:Page` Knoten, werden dann 1 Million Datensätze überprüft, um die Ergebnismenge zu bestimmen.

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

Weitere Abfrageeinschränkungen reduzieren die zulässigen Ergebnismengen und optimieren die Abfrageoptimierung weiter.

Gleichermaßen ohne zusätzliche Indexregel für `cq:tags` -Eigenschaft, selbst eine Volltextabfrage mit einer Beschränkung auf `cq:tags` würde nur schlecht funktionieren, da Ergebnisse aus dem Index alle Volltext-Übereinstimmungen zurückgeben würden. Die Einschränkung auf cq:tags würde anschließend gefiltert werden.

Eine weitere Ursache für die Filterung nach dem Index ist Zugriffssteuerungslisten, die bei der Entwicklung häufig übersehen werden. Versuchen Sie sicherzustellen, dass die Abfrage keine Pfade zurückgibt, auf die der Benutzer möglicherweise nicht zugreifen kann. Dies kann durch eine bessere Inhaltsstruktur sowie durch Bereitstellung relevanter Pfadbeschränkungen für die Abfrage erfolgen.

Eine nützliche Möglichkeit, festzustellen, ob der Lucene-Index viele Ergebnisse zurückgibt, um eine kleine Teilmenge als Abfrageergebnis zurückzugeben, besteht darin, DEBUG-Protokolle für `org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex`. Auf diese Weise können Sie sehen, wie viele Dokumente aus dem Index geladen werden. Die Anzahl der Ergebnisse im Vergleich zur Anzahl der geladenen Dokumente sollte nicht unverhältnismäßig sein. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).

#### Nach der Bereitstellung {#post-deployment-1}

* Überwachen Sie das `error.log` für Durchlaufabfragen:

   * `*WARN* org.apache.jackrabbit.oak.spi.query.Cursors$TraversingCursor Traversed ### nodes ... consider creating an index or changing the query`

* Besuchen Sie die in der AEM-Betriebskonsole [Abfrageleistung](/help/sites-administering/operations-dashboard.md#query-performance) und [erklären](/help/sites-administering/operations-dashboard.md#explain-query) Sie langsame Abfragen, wobei Sie nach Abfrageplänen suchen, die Abfrageeigenschaftseinschränkungen nicht in Indexeigenschaftsregeln auflösen.

### Erkennen von Abfragen mit großen Ergebnismengen {#detecting-large-result-set-queries}

#### Während der Entwicklung {#during-development-2}

Setzen Sie niedrige Schwellenwerte für oak.queryLimitInMemory (z. B. 10000) und oak.queryLimitReads (z. B. 5000) und optimieren Sie die teure Abfrage, wenn Sie auf eine UnsupportedOperationException klicken, die besagt: &quot;Die Abfrage liest mehr als x Knoten...&quot;.

Die Festlegung niedriger Schwellenwerte verhindert ressourcenintensive Abfragen (d. h. nicht durch einen Index unterlegt oder durch einen Index mit geringerer Abdeckung unterlegt). Beispielsweise würde eine Abfrage, die eine Million Knoten liest, zu vielen I/O führen und die Gesamtleistung der Anwendung negativ beeinflussen. Daher sollten alle Abfragen, die aufgrund der obigen Beschränkungen fehlschlagen, analysiert und optimiert werden.

#### Nach der Bereitstellung {#post-deployment-2}

* Überwachen Sie die Protokolle auf Abfragen, die eine hohe Anzahl durchlaufener Knoten oder einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * Optimieren Sie die Abfrage, sodass Sie die Anzahl der durchsuchten Knoten reduzieren.

* Überwachen Sie die Protokolle auf Abfragen, die einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimieren Sie die Abfrage, sodass Sie den Heap-Speicherverbrauch reduzieren.

Für die AEM-Versionen 6.0 bis 6.2 können Sie den Schwellenwert für das Durchlaufen von Knoten über JVM-Parameter im AEM-Startskript abstimmen, um zu verhindern, dass die Umgebung durch umfangreiche Abfragen überlastet wird. Folgende Werte werden empfohlen:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3 sind die beiden oben genannten Parameter standardmäßig vorkonfiguriert und können über die OSGi QueryEngineSettings geändert werden.

Weitere Informationen finden Sie unter: [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Optimierung der Abfrageleistung {#query-performance-tuning}

Das Motto der Optimierung der Abfrageleistung in AEM lautet:

**&quot;Je mehr Einschränkungen, desto besser.&quot;**

Im Folgenden werden die empfohlenen Anpassungen zur Gewährleistung der Abfrageleistung beschrieben. Passen Sie zuerst die Abfrage an, eine weniger störende Aktivität, und passen Sie bei Bedarf die Indexdefinitionen an.

### Anpassen der Abfrage-Anweisung {#adjusting-the-query-statement}

AEM unterstützt die folgenden Abfragesprachen:

* Query Builder
* JCR-SQL2
* XPath

Im folgenden Beispiel wird Query Builder verwendet, da es die gängigste Abfragesprache ist, die von AEM-Entwicklern verwendet wird. Die gleichen Prinzipien gelten jedoch für JCR-SQL2 und XPath.

1. Fügen Sie eine Knotentyp-Einschränkung hinzu, damit die Abfrage zu einem vorhandenen Lucene-Eigenschaftsindex aufgelöst wird.

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

1. Passen Sie die Knotentyp-Einschränkung der Abfrage an, sodass die Abfrage zu einem vorhandenen Lucene-Eigenschaftsindex aufgelöst wird.

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

   `nt:hierarchyNode` ist der übergeordnete Knotentyp von `cq:Page`. Annahmen `jcr:content/contentType=article-page` wird nur auf `cq:Page` -Knoten über die benutzerdefinierte Anwendung der Adobe zurückgibt diese Abfrage nur `cq:Page` Knoten, `jcr:content/contentType=article-page`. Dieser Fluss ist jedoch eine suboptimale Einschränkung, da:

   * Andere Knoten übernehmen von `nt:hierarchyNode` (z. B. `dam:Asset`), was unnötig zum Satz potenzieller Ergebnisse hinzufügt.
   * Es gibt keinen von AEM bereitgestellten Index für `nt:hierarchyNode`. Ein Index ist jedoch für `cq:Page` vorhanden.
   Wenn Sie `type=cq:Page` setzen, wird die Abfrage auf `cq:Page`-Knoten beschränkt und auf cqPageLucene von AEM aufgelöst. Dadurch werden die Ergebnisse auf eine Untergruppe von Knoten (nur cq:Page-Knoten) in AEM beschränkt.

1. Sie können auch die Eigenschaftsbeschränkungen so anpassen, dass die Abfrage zu einem vorhandenen Eigenschaftsindex aufgelöst wird.

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

   Ändern der Eigenschaftsbeschränkung von `jcr:content/contentType` (ein benutzerdefinierter Wert) zur bekannten Eigenschaft hinzu. `sling:resourceType` ermöglicht die Auflösung der Abfrage in den Eigenschaftenindex `slingResourceType` , der den gesamten Inhalt nach `sling:resourceType`.

   Eigenschaftenindizes (im Gegensatz zu Lucene-Eigenschaftsindizes) werden am besten verwendet, wenn die Abfrage nicht nach Knotentyp erkennt und eine einzelne Eigenschaftsbeschränkung den Ergebnissatz dominiert.

1. Fügen Sie der Abfrage die strengste Pfadbeschränkung hinzu. Beispielsweise soll `/content/my-site/us/en` gegenüber `/content/my-site` oder `/content/dam` gegenüber `/` bevorzugt werden.

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

   Pfadbeschränkung von `path=/content`nach `path=/content/my-site/us/en` ermöglicht es den Indizes, die Anzahl der zu prüfenden Indexeinträge zu reduzieren. Wenn die Abfrage den Pfad gut einschränken kann, über `/content` oder `/content/dam`, stellen Sie sicher, dass der Index `evaluatePathRestrictions=true`.

   Beachten Sie, dass die Verwendung von `evaluatePathRestrictions` den Index vergrößert.

1. Vermeiden Sie nach Möglichkeit Abfragefunktionen und Abfragevorgänge wie: `LIKE` und `fn:XXXX` da ihre Kosten mit der Anzahl der einschränkungsbasierten Ergebnisse skaliert werden.

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

   Die Bedingung LIKE wird langsam geprüft, da kein Index verwendet werden kann, wenn der Text mit einem Platzhalter (&quot;%...&#39;) beginnt. Die Bedingung jcr: ermöglicht die Verwendung eines Volltext-Index und wird daher bevorzugt. Dazu muss der aufgelöste Lucene-Eigenschaftsindex über indexRule verfügen für `jcr:content/contentType` mit `analayzed=true`.

   Das Verwenden von Abfragefunktionen wie `fn:lowercase(..)` kann schwieriger zu optimieren sein, da es keine schnelleren Äquivalente gibt (abgesehen von komplexeren und aufdringlichen Indexanalysekonfigurationen). Es ist am besten, andere Scoping-Einschränkungen zu identifizieren, um die Gesamtabfrageleistung zu verbessern, sodass die Funktionen auf die kleinstmögliche Anzahl möglicher Ergebnisse angewendet werden müssen.

1. ***Diese Anpassung ist für Query Builder spezifisch und gilt nicht für JCR-SQL2 oder XPath.***

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

   `p.guessTotal=100` weist Query Builder an, nur die ersten 100 Ergebnisse zu erfassen. Und um eine boolesche Markierung zu setzen, die angibt, ob mindestens ein weiteres Ergebnis vorhanden ist (aber nicht wie viele weitere Ergebnisse, da die Zählung dieser Zahl zu Langsamkeit führt). Diese Optimierung eignet sich hervorragend für Anwendungsfälle für Paginierung oder unendliches Laden, bei denen nur eine Ergebnisuntergruppe inkrementell angezeigt wird.

## Vorhandene Indexverfeinerung {#existing-index-tuning}

1. Wenn die optimale Abfrage in einen Eigenschaftsindex aufgelöst wird, bleibt nichts zu tun, da Eigenschaftenindizes nur geringfügig angepasst werden können.
1. Andernfalls sollte die Abfrage auf einen Lucene-Eigenschaftsindex aufgelöst werden. Wenn kein Index aufgelöst werden kann, springen Sie zu Erstellen eines neuen Index .
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

1. Stellen Sie den XPath (oder JCR-SQL2) dem Oak Index Definition Generator unter `https://oakutils.appspot.com/generate/index` damit Sie die optimierte Definition des Lucene-Eigenschaftsindex generieren können. <!-- The above URL is 404 as of April 24, 2023 -->

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

1. Führen Sie manuell die generierte Definition additiv mit dem vorhandenen Lucene-Eigenschaftsindex zusammen. Achten Sie darauf, vorhandene Konfigurationen nicht zu entfernen, da sie möglicherweise für andere Abfragen verwendet werden.

   1. Suchen Sie den vorhandenen Lucene-Eigenschaftsindex, der cq:Page abdeckt (mithilfe des Index-Managers). In diesem Fall, `/oak:index/cqPageLucene`.
   1. Identifizieren Sie die Konfigurationsunterschiede zwischen der optimierten Indexdefinition (Schritt 4) und dem vorhandenen Index (/oak:index/cqPageLucene) und fügen Sie die fehlenden Konfigurationen aus dem optimierten Index zur vorhandenen Indexdefinition hinzu.
   1. Gemäß AEM Best Practices für die Neuindizierung ist entweder eine Aktualisierung oder eine Neuindizierung in der richtigen Reihenfolge, je nachdem, ob sich diese Indexkonfigurationsänderung auf vorhandenen Inhalt auswirken könnte.

## Erstellen eines neuen Index {#create-a-new-index}

1. Stellen Sie sicher, dass die Abfrage nicht in einen vorhandenen Lucene-Eigenschaftsindex aufgelöst wird. Ist dies der Fall, lesen Sie den obigen Abschnitt zur Optimierung und zum vorhandenen Index.
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

1. Stellen Sie den XPath (oder JCR-SQL2) dem Oak Index Definition Generator unter `https://oakutils.appspot.com/generate/index` damit Sie die optimierte Definition des Lucene-Eigenschaftsindex generieren können. <!-- The above URL is 404 as of April 24, 2023 -->

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

1. Stellen Sie die generierte Definition des Lucene-Eigenschaftsindex bereit.

   Fügen Sie die vom Oak Index Definition Generator bereitgestellte XML-Definition für den neuen Index zum AEM-Projekt hinzu, das Oak-Indexdefinitionen verwaltet (denken Sie daran, behandeln Sie Oak-Indexdefinitionen als Code, da der Code von ihnen abhängt).

   Stellen Sie den neuen Index bereit und testen Sie ihn nach dem üblichen AEM Softwareentwicklungs-Lebenszyklus und überprüfen Sie, ob die Abfrage in den Index aufgelöst wird und die Abfrage leistungsfähig ist.

   Bei der ersten Bereitstellung dieses Index füllt AEM den Index mit den erforderlichen Daten.

## Wann sind indexlose und Durchlaufabfragen zulässig? {#when-index-less-and-traversal-queries-are-ok}

Aufgrund AEM flexiblen Inhaltsarchitektur ist es schwierig, vorherzusagen und sicherzustellen, dass sich die Durchläufe von Inhaltsstrukturen im Laufe der Zeit nicht zu einer inakzeptablen Größe entwickeln.

Stellen Sie daher sicher, dass Indizes Abfragen erfüllen, es sei denn, die Kombination aus Pfadbeschränkung und Knotentyp-Beschränkung gewährleistet, dass **weniger als 20 Knoten werden je durchlaufen.**

## Tools zur Abfrageentwicklung {#query-development-tools}

### Unterstützte Adobe {#adobe-supported}

* **Query Builder-Debugger**

   * Eine WebUI für die Ausführung von Query Builder-Abfragen und die Generierung des unterstützenden XPath (zur Verwendung in „Abfrage erläutern“ oder im Oak Index Definition Generator).
   * AEM [/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)

* **CRXDE Lite - Abfrage-Tool**

   * Eine WebUI zum Ausführen von XPath- und JCR-SQL2-Abfragen.
   * AEM [/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp) > Tools > Abfrage..

* **[Abfrage erläutern](/help/sites-administering/operations-dashboard.md#explain-query)**

   * Ein Dashboard für AEM Vorgänge , das eine detaillierte Erläuterung (Abfrageplan, Abfragezeit und Anzahl der Ergebnisse) für eine gegebene XPATH- oder JCR-SQL2-Abfrage bereitstellt.

* **[Langsame/beliebte Abfragen](/help/sites-administering/operations-dashboard.md#query-performance)**

   * Ein Dashboard AEM Vorgänge , in dem die zuletzt durchgeführten langsamen und beliebten Abfragen für AEM aufgelistet werden.

* **[Index-Manager](/help/sites-administering/operations-dashboard.md#the-index-manager)**

   * Eine AEM Operations-WebUI, die die Indizes auf der AEM-Instanz anzeigt; erleichtert das Verständnis der vorhandenen Indizes; kann als Ziel ausgewählt oder erweitert werden.

* **[Protokollierung](/help/sites-administering/operations-dashboard.md#log-messages)**

   * Query Builder-Protokollierung

      * `DEBUG @ com.day.cq.search.impl.builder.QueryImpl`
   * Oak Query-Ausführungsprotokollierung

      * `DEBUG @ org.apache.jackrabbit.oak.query`


* **OSGi-Konfiguration der Apache Jackrabbit Query Engine-Einstellungen**

   * OSGi-Konfiguration, die das Fehlerverhalten für das Durchlaufen von Abfragen konfiguriert.
   * AEM [/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService](http://localhost:4502/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService)

* **NodeCounter JMX MBean**

   * JMX MBean, mit dem die Anzahl der Knoten in Inhaltsbäumen in AEM geschätzt wird.
   * AEM [/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter)

### Community-Unterstützung {#community-supported}

* **Oak Index Definition Generator unter`https://oakutils.appspot.com/generate/index`** <!-- The above URL is 404 as of April 24, 2023 -->

   * Generieren Sie optimale Lucence-Eigenschafts-Indizes aus XPath- oder JCR-SQL2-Abfragen.

* **[AEM-Chrome-Plug-in](https://chrome.google.com/webstore/detail/aem-chrome-plug-in/ejdcnikffjleeffpigekhccpepplaode?hl=de-DE)**

   * Eine Webbrowser-Erweiterung für Google Chrome, die Protokolldaten für einzelne Anfragen, z. B. ausgeführte Abfragen und ihre Abfragepläne, in der Entwicklerkonsole des Browsers ausgibt.
   * [Sling Log Tracer 1.0.2+](https://sling.apache.org/downloads.cgi) muss dazu installiert und in AEM aktiviert sein.
