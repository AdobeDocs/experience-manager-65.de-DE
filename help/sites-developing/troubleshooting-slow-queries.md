---
title: Fehlerbehebung bei langsamen Abfragen
seo-title: Fehlerbehebung bei langsamen Abfragen
description: 'null'
seo-description: 'null'
uuid: ad09546a-c049-44b2-99a3-cb74ee68f040
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: c01e42ff-e338-46e6-a961-131ef943ea91
translation-type: tm+mt
source-git-commit: 6d8680bcfb03197ac33bc7efb0e40796e38fef20
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 70%

---


# Fehlerbehebung bei langsamen Abfragen{#troubleshooting-slow-queries}

## Klassifikation langsamer Abfragen {#slow-query-classifications}

Es gibt 3 Hauptklassifikationen von langsamen Abfragen in AEM, die hier nach Schweregrad aufgelistet sind:

1. **Abfragen ohne Index**

   * Abfragen, die **nicht** auf einen Index aufgelöst werden und den JCR-Inhalt nach Ergebnissen durchsuchen

1. **Abfragen mit schlechter Einschränkung (oder schlechtem Bereich)**

   * Abfragen, die auf einen Index aufgelöst werden, aber alle Indexeinträge durchlaufen müssen, um Ergebnisse zu sammeln

1. **Abfragen mit vielen Ergebnissen**

   * Abfragen, die sehr viele Ergebnisse zurückgeben

The first 2 classifications of queries (index-less and poorly restricted) are slow, because they force the Oak query engine to inspect each **potential** result (content node or index entry) to identify which belong in the **actual** result set.

Das Untersuchen aller potenziellen Ergebnisse wird als Durchlaufen bezeichnet.

Da jedes potenzielle Ergebnis überprüft werden muss, steigen die Kosten zur Bestimmung der tatsächlichen Ergebnismenge linear zur Anzahl der potenziellen Ergebnisse.

Durch Abfragebeschränkungen und Tuning von Indizes können die Indexdaten in einem optimierten Format gespeichert werden, das schnell Ergebnisse produziert und eine lineare Inspektion potenzieller Ergebnismengen unnötig macht.

In AEM 6.3 schlägt die Abfrage standardmäßig fehl und löst einen Ausnahmefehler aus, wenn 100.000 potenzielle Ergebnisse durchlaufen wurden. Diese Beschränkung ist in AEM Versionen vor AEM 6.3 nicht standardmäßig vorhanden, kann jedoch über die Apache Jackrabbit Abfrage Engine Settings OSGi-Konfiguration und QueryEngineSettings JMX Bean (Eigenschaft LimitReads) festgelegt werden.

### Erkennen von Abfragen ohne Index {#detecting-index-less-queries}

#### Während der Entwicklung {#during-development}

Explain **all** queries and ensure their query plans do not contain the **/&amp;ast; traverse** explanation in them. Beispiel für das Durchlaufen eines Abfrageplans:

* **PLAN:** `[nt:unstructured] as [a] /* traverse "/content//*" where ([a].[unindexedProperty] = 'some value') and (isdescendantnode([a], [/content])) */`

#### Nach der Bereitstellung {#post-deployment}

* Überwachen Sie `error.log` nach Index-losen Durchlaufabfragen:

   * `*INFO* org.apache.jackrabbit.oak.query.QueryImpl Traversal query (query without index) ... ; consider creating and index`
   * Diese Meldung wird nur aufgezeichnet, wenn kein Index verfügbar ist und die Abfrage möglicherweise viele Knoten durchlaufen wird. Meldungen werden nicht aufgezeichnet, wenn ein Index verfügbar ist oder die zu durchlaufende Knotenanzahl gering und somit schnell zu durchlaufen ist.

* Visit the AEM [Query Performance](/help/sites-administering/operations-dashboard.md#query-performance) operations console and [Explain](/help/sites-administering/operations-dashboard.md#explain-query) slow queries looking for traversal or no index query explanations.

### Erkennen von schlecht eingeschränkten Abfragen {#detecting-poorly-restricted-queries}

#### Während der Entwicklung {#during-development-1}

Erklären Sie alle Abfragen und stellen Sie sicher, dass sie auf einen Index aufgelöst werden, der den Eigenschaftsbeschränkungen der Abfrage entspricht.

* Bei einer idealen Abdeckung des Abfrageplans sind `indexRules` für alle Eigenschaftsbeschränkungen vorhanden, mindestens aber für die strengsten Eigenschaftsbeschränkungen in der Abfrage.
* Abfragen, die Ergebnisse sortieren, sollten auf einen Lucene-Eigenschaftsindex mit Indexregeln für die Sortierungseigenschaften aufgelöst werden, die `orderable=true.` setzen.

#### For example, the default `cqPageLucene` does not have an index rule for `jcr:content/cq:tags` {#for-example-the-default-cqpagelucene-does-not-have-an-index-rule-for-jcr-content-cq-tags}

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

Diese Abfrage wird auf den Index `cqPageLucene` aufgelöst. Da jedoch keine Eigenschaftsindexregel für `jcr:content` oder `cq:tags` vorhanden ist, wird bei der Prüfung der Einschränkung jeder Datensatz im Index `cqPageLucene` auf Übereinstimmung geprüft. Wenn also der Index 1 Million `cq:Page`-Knoten enthält, werden 1 Million Datensätze geprüft, um die Ergebnismenge zu bestimmen.

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

The addition of the indexRule for `jcr:content/cq:tags` in the `cqPageLucene` index allows `cq:tags` data to be stored in an optimized way.

When a query with the `jcr:content/cq:tags` restriction is performed, the index can look up results by value. Wenn also 100 `cq:Page`-Knoten den Wert `myTagNamespace:myTag` aufweisen, werden nur diese 100 Ergebnisse zurückgegeben. Die übrigen 999.000 werden aus den Einschränkungsprüfungen ausgeschlossen, was die Leistung um den Faktor 10.000 verbessert.

Selbstverständlich verringern weitere Abfragebeschränkungen die möglichen Ergebnismengen und führen zu weiterer Abfrageoptimierung.

Similarly, without an additional index rule for the `cq:tags` property, even a fulltext query with a restriction on `cq:tags` would perform poorly as results from the index would return all fulltext matches. Die Beschränkung auf cq:tags würde danach gefiltert.

Eine weitere Ursache von Filtern nach dem Index sind Zugangssteuerungslisten, die oft bei der Entwicklung übergangen werden. Stellen Sie sicher, dass die Abfrage keine Pfade zurückgibt, die dem Benutzer nicht zugänglich sind. Dies kann meist durch eine bessere Inhaltsstruktur sowie durch Bereitstellung relevanter Pfadbeschränkungen bei der Abfrage realisiert werden.

A useful way to identify if the Lucene index is returning a lot of results to return a very small subset as query result is to enable DEBUG logs for `org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex` and see how many documents are being loaded from the index. Die Anzahl der Ergebnisse sollte nicht zu weit unter der Anzahl der geladenen Dokumente liegen. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).

#### Nach der Bereitstellung {#post-deployment-1}

* Monitor the `error.log` for traversal queries:

   * `*WARN* org.apache.jackrabbit.oak.spi.query.Cursors$TraversingCursor Traversed ### nodes ... consider creating an index or changing the query`

* Visit the AEM [Query Performance](/help/sites-administering/operations-dashboard.md#query-performance) operations console and [Explain](/help/sites-administering/operations-dashboard.md#explain-query) slow queries looking for query plans that do not resolve query property restrictions to index property rules.

### Erkennen von Abfragen mit vielen Ergebnissen {#detecting-large-result-set-queries}

#### Während der Entwicklung {#during-development-2}

Legen Sie niedrige Schwellenwerte für oak.queryLimitInMemory (z. B. 10000) und oak.queryLimitReads (z. B. 5000) fest und optimieren Sie die ressourcenintensive Abfrage, wenn die UnsupportedOperationException-Ausnahme „The query read more than x nodes...“ auftritt.

Dies trägt zur Vermeidung ressourcenintensiver Abfragen bei (d. h. keine Sicherung durch einen Index oder Sicherung durch einen weniger abdeckenden Index). Beispielsweise führt eine Abfrage, die 1 Million Knoten liest, zu einer großen E/A-Menge – mit negativen Folgen für die Gesamtleistung der Anwendung. Jede Abfrage, die aufgrund eines überschrittenen Limits fehlschlägt, sollte also analysiert und optimiert werden.

#### Nach der Bereitstellung {#post-deployment-2}

* Überwachen Sie die Protokolle auf Abfragen, die einen großen Node-Traversal- oder großen Heap-Speicherverbrauch auslösen: &quot;

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * Optimieren Sie die Abfrage, um die Anzahl durchlaufener Knoten zu reduzieren.

* Überwachen Sie die Protokolle auf Abfragen, die einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimieren Sie die Abfrage, um den Heap-Speicherverbrauch zu reduzieren.

Bei AEM 6.0-6.2-Versionen können Sie den Schwellenwert für die Node-Traversal mithilfe von JVM-Parametern im Skript &quot;AEM Beginn&quot;anpassen, um zu verhindern, dass große Abfragen die Umgebung überladen. Folgende Werte werden empfohlen:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3 sind die beiden oben stehenden Parameter standardmäßig vorkonfiguriert und können über die OSGi QueryEngineSettings bearbeitet werden.

More information available under : [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Verbesserung der Abfrageleistung {#query-performance-tuning}

Das Motto der Abfrageleistungsoptimierung in AEM lautet:

**„Je mehr Einschränkungen, desto besser.“**

Im Folgenden werden einige empfohlene Anpassungen zur Verbesserung der Abfrageleistung beschrieben. Passen Sie zunächst die Abfrage an (ein geringfügiger Eingriff) und anschließend, wenn nötig, die Index-Definitionen.

### Anpassen der Abfrage {#adjusting-the-query-statement}

AEM unterstützt die folgenden Abfragesprachen:

* Query Builder
* JCR-SQL2
* XPath

Im folgenden Beispiel wird Query Builder verwendet, da es von AEM-Entwicklern am häufigsten verwendet wird. Die Prinzipien sind jedoch auch auf JCR-SQL2 und XPath anwendbar.

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

   Setting `type=cq:Page` restricts this query to only `cq:Page` nodes, and resolves the query to AEM&#39;s cqPageLucene, limiting the results to a subset of nodes (only `cq:Page` nodes) in AEM.

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

   `nt:hierarchyNode` ist der übergeordnete Knoten von `cq:Page`und vorausgesetzt, dass `jcr:content/contentType=article-page` nur auf `cq:Page` Knoten über unsere benutzerdefinierte Anwendung angewendet wird, gibt diese Abfrage nur `cq:Page` Knoten zurück, wo `jcr:content/contentType=article-page`. Dies ist jedoch aus folgenden Gründen eine suboptimale Beschränkung:

   * Other node inherit from `nt:hierarchyNode` (eg. `dam:Asset`), die zu den möglichen Ergebnissen unnötigerweise hinzufügt.
   * No AEM-provided index exists for `nt:hierarchyNode`, however as there a provided index for `cq:Page`.
   Wenn Sie `type=cq:Page` setzen, wird die Abfrage auf `cq:Page`-Knoten beschränkt und auf cqPageLucene von AEM aufgelöst. Dadurch werden die Ergebnisse auf eine Untergruppe von Knoten (nur cq:Page-Knoten) in AEM beschränkt.

1. Sie können auch die Eigenschaftseinschränkungen so anpassen, dass die Abfrage zu einem vorhandenen Eigenschaftsindex aufgelöst wird.

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

   Changing the property restriction from `jcr:content/contentType` (a custom value) to the well known property `sling:resourceType` lets the query to resolve to the property index `slingResourceType` which indexes all content by `sling:resourceType`.

   Eigenschaftsindizes (anstelle von Lucene-Eigenschaftsindizes) eignen sich am besten, wenn die Abfrage nicht nach Knotentyp unterscheidet und eine einzige Eigenschaftsbeschränkung die Ergebnismenge beherrscht.

1. Fügen Sie die strengstmögliche Pfadbeschränkung zur Abfrage hinzu. Nehmen wir zum Beispiel an, Sie bevorzugen `/content/my-site/us/en` lieber `/content/my-site`oder `/content/dam` lieber `/`.

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

   Scoping the path restriction from `path=/content`to `path=/content/my-site/us/en` allows the indexes to reduce the number of index entries that need to be inspected. When the query can restrict the path very well, beyond just `/content` or `/content/dam`, ensure the index has `evaluatePathRestrictions=true`.

   Note using `evaluatePathRestrictions` increases the index size.

1. Falls möglich, vermeiden Sie Abfragefunktionen/-operationen wie `LIKE` und `fn:XXXX`, da ihre Kosten mit der Anzahl der einschränkungsbasierten Ergebnisse skalieren.

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

   Die LIKE-Bedingung ist nur langsam auszuwerten, da kein Index verwendet werden kann, wenn der Text mit einem Platzhalter (&quot;%...&quot;) Beginn. Die Bedingung jcr: ermöglicht die Verwendung eines Volltext-Index und wird daher bevorzugt. This requires the resolved Lucene Property Index to have indexRule for `jcr:content/contentType` with `analayzed=true`.

   Using query functions like `fn:lowercase(..)` may be harder to optimize as there are not faster equivalents (outside more complex and obtrusive index analyzer configurations). Es ist ratsam, andere Scoping-Beschränkungen zu identifizieren, damit die Funktionen mit der kleinstmöglichen Ergebnismenge arbeiten, um die Abfrageleistung insgesamt zu verbessern.

1. ***Diese Anpassung ist nur im Query Builder möglich und gilt nicht für JCR-SQL2 oder XPath.***

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

   `p.guessTotal=100` sorgt dafür, dass Query Builder nur die ersten 100 Ergebnisse erfasst, und setzt einen booleschen Wert, der angibt, ob mindestens ein weiteres Ergebnis vorliegt (jedoch nicht die Anzahl der weiteren Ergebnisse, da das Zählen den Vorgang verlangsamen würde). Diese Optimierung eignet sich hervorragend für Anwendungsfälle mit Paginierung oder endlosem Laden, wenn nur eine Teilmenge der Ergebnisse schrittweise angezeigt wird.

## Anpassen vorhandener Indizes {#existing-index-tuning}

1. Wenn die optimale Abfrage auf einen Eigenschaftsindex aufgelöst wird, gibt es nichts mehr zu tun, da Eigenschaftsindizes nur minimale Anpassungsmöglichkeiten bieten.
1. Andernfalls sollte die Abfrage in einen Lucene-Eigenschaftenindex aufgelöst werden. Wenn kein Index aufgelöst werden kann, springen Sie zu „Erstellen eines neuen Index“.
1. Wandeln Sie bei Bedarf die Abfrage in XPath oder JCR-SQL2 um.

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

1. Stellen Sie den XPath (oder JCR-SQL2) dem [Oak Index Definition Generator](https://oakutils.appspot.com/generate/index) bereit, um die optimierte Lucene-Eigenschaftsindex-Definition zu generieren.

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

1. Fügen Sie die generierte Definition manuell in den vorhandenen Lucene-Eigenschaftenindex ein. Achten Sie darauf, dass Sie keine vorhandenen Konfigurationen entfernen, da sie zum Erfüllen anderer Abfragen verwendet werden können.

   1. Suchen Sie nach dem vorhandenen Lucene-Eigenschaftsindex, der cq:Page abdeckt (mit Index Manager). In diesem Fall, `/oak:index/cqPageLucene`.
   1. Finden Sie die Konfigurationsunterschiede zwischen der optimierten Indexdefinition (Schritt 4) und dem vorhandenen Index (/oak:index/cqPageLucene) und fügen Sie die fehlenden Konfigurationen aus dem optimierten Index zur vorhandenen Indexdefinition hinzu.
   1. Gemäß der Best Practices zur Neuindizierung in AEM müssen Sie entweder eine Aktualisierung oder eine Neuindizierung durchführen, je nachdem, ob vorhandene Inhalte von dieser Indexkonfigurationsänderung betroffen sind.

## Create a New Index {#create-a-new-index}

1. Vergewissern Sie sich, dass die Abfrage nicht auf einen vorhandenen Lucene-Eigenschaftsindex aufgelöst wird. In diesem Fall finden Sie weitere Informationen im vorherigen Abschnitt zur Anpassung eines vorhandenen Index.
1. Wandeln Sie bei Bedarf die Abfrage in XPath oder JCR-SQL2 um.

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

1. Stellen Sie den XPath (oder JCR-SQL2) dem [Oak Index Definition Generator](https://oakutils.appspot.com/generate/index) bereit, um die optimierte Lucene-Eigenschaftsindex-Definition zu generieren.

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

   Stellen Sie den neuen Index bereit und testen Sie ihn entsprechend dem üblichen Lebenszyklus für AEM-Softwareentwicklung. Prüfen Sie, ob die Abfrage auf den Index aufgelöst wird und gute Leistung zeigt.

   Nach der Erstbereitstellung dieses Index füllt AEM ihn mit den erforderlichen Daten aus.

## Wann sind indexlose und übergreifende Abfragen OK? {#when-index-less-and-traversal-queries-are-ok}

Aufgrund der flexiblen Inhaltsarchitektur von AEM ist es schwer vorherzusagen und zu verhindern, dass der Durchlauf von Inhaltsstrukturen im Laufe der Zeit auf eine inakzeptable Größe anwächst.

Therefore, ensure an indexes satisfy queries, except if the combination of path restriction and nodetype restriction guarantees that **less than 20 nodes are ever traversed.**

## Abfragen-Entwicklungswerkzeuge {#query-development-tools}

### Adobe-Unterstützung {#adobe-supported}

* **Query Builder-Debugger**

   * Eine WebUI für die Ausführung von Query Builder-Abfragen und die Generierung des unterstützenden XPath (zur Verwendung in „Abfrage erläutern“ oder im Oak Index Definition Generator).
   * Located on AEM at [/libs/cq/search/content/querydebug.html](http://localhost:4502/libs/cq/search/content/querydebug.html)

* **CRXDE Lite – Abfragewerkzeug**

   * Eine WebUI für die Ausführung von XPath- und JCR-SQL2-Abfragen.
   * Located on AEM at [/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp) > Tools > Query...

* **[Abfrage erläutern](/help/sites-administering/operations-dashboard.md#explain-query)**

   * Ein AEM Operations-Dashboard, das für jede XPATH- oder JCR-SQL2-Abfrage eine detaillierte Erklärung bietet (Abfrageplan, Abfragezeit und Anzahl der Ergebnisse).

* **[Langsame/beliebte Abfragen](/help/sites-administering/operations-dashboard.md#query-performance)**

   * Ein AEM Operations-Dashboard, das langsame und beliebte Abfragen ausführt, die kürzlich auf AEM ausgeführt wurden.

* **[Index-Manager](/help/sites-administering/operations-dashboard.md#the-index-manager)**

   * Eine AEM Operations-WebUI, die die Indizes in der AEM-Instanz anzeigt. Sie bietet Informationen zu bereits vorhandenen Indizes und kann angesprochen oder erweitert werden.

* **[Protokollierung](/help/sites-administering/operations-dashboard.md#log-messages)**

   * Query Builder-Protokollierung

      * `DEBUG @ com.day.cq.search.impl.builder.QueryImpl`
   * Oak Query-Ausführungsprotokollierung

      * `DEBUG @ org.apache.jackrabbit.oak.query`


* **Apache Jackrabbit Query Engine-Einstellungen – OSGi-Konfiguration**

   * OSGi-Konfiguration, die das Verhalten im Fehlerfall bei Durchlaufabfragen konfiguriert.
   * Located on AEM at [/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService](http://localhost:4502/system/console/configMgr#org.apache.jackrabbit.oak.query.QueryEngineSettingsService)

* **NodeCounter JMX Mbean**

   * JMX MBean wird verwendet, um die Anzahl der Knoten in Content-Baumstrukturen in AEM zu schätzen.
   * Located on AEM at [/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DnodeCounter%2Ctype%3DNodeCounter)

### Community-Unterstützung {#community-supported}

* **[Oak Index Definition Generator](https://oakutils.appspot.com/generate/index)**

   * Generieren Sie optimale Lucence-Eigenschafts-Indizes aus XPath- oder JCR-SQL2-Abfragen.

* **[AEM-Chrome-Plug-in](https://chrome.google.com/webstore/detail/aem-chrome-plug-in/ejdcnikffjleeffpigekhccpepplaode?hl=en-US)**

   * Eine Webbrowser-Erweiterung für Google Chrome, die Protokolldaten für einzelne Anfragen, z. B. ausgeführte Abfragen und ihre Abfragepläne, in der Entwicklerkonsole des Browsers ausgibt.
   * [Sling Log Tracer 1.0.2+](https://sling.apache.org/downloads.cgi) muss dazu installiert und in AEM aktiviert sein.
