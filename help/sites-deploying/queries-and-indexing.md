---
title: Oak-Abfragen und Indizierung
description: Erfahren Sie, wie Sie Indizes in Adobe Experience Manager konfigurieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/queries-and-indexing
feature: Configuring
exl-id: d9ec7728-84f7-42c8-9c80-e59e029840da
source-git-commit: b66ec42c35b5b60804015d340b8194bbd6ef3e28
workflow-type: tm+mt
source-wordcount: '3033'
ht-degree: 24%

---

# Oak-Abfragen und Indizierung{#oak-queries-and-indexing}

>[!NOTE]
>
>In diesem Artikel geht es um die Konfiguration von Indizes in AEM 6. Informationen zur besten Vorgehensweise beim Optimieren von Abfragen- und Indizierungsleistung finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

## Einführung {#introduction}

Im Gegensatz zu Jackrabbit 2 indiziert Oak nicht standardmäßig Inhalte. Bei Bedarf müssen benutzerdefinierte Indizes erstellt werden, ähnlich wie bei herkömmlichen relationalen Datenbanken. Wenn für eine bestimmte Abfrage kein Index vorhanden ist, werden möglicherweise viele Knoten durchlaufen. Die Abfrage funktioniert möglicherweise weiterhin, ist aber wahrscheinlich langsam.

Wenn Oak auf eine Abfrage ohne Index stößt, wird eine Protokollmeldung auf WARN-Ebene ausgegeben:

```xml
*WARN* Traversed 1000 nodes with filter Filter(query=select ...) consider creating an index or changing the query
```

## Unterstützte Abfragesprachen {#supported-query-languages}

Die Oak-Abfrage-Engine unterstützt die folgenden Sprachen:

* XPath (empfohlen)
* SQL-2
* SQL (nicht mehr unterstützt)
* JQOM

## Indextypen und Kostenberechnung {#indexer-types-and-cost-calculation}

Das Apache Oak-basierte Backend ermöglicht das Einbinden verschiedener Indexer in das Repository.

Ein Indexer ist der **Eigenschaftsindex**, für die die Indexdefinition im Repository selbst gespeichert wird.

Implementierungen für **Apache Lucene** und **Solr** sind ebenfalls standardmäßig verfügbar und unterstützen die Volltextindizierung.

Der **Traversalindex** wird verwendet, wenn kein anderer Indexer verfügbar ist. Das bedeutet, dass der Inhalt nicht indiziert ist und Inhaltsknoten durchsucht werden, um Übereinstimmungen mit der Abfrage zu finden.

Wenn für eine Abfrage mehrere Indexer verfügbar sind, schätzt jeder verfügbare Indexer die Kosten für die Ausführung der Abfrage. Oak wählt dann den Indexer mit den niedrigsten geschätzten Kosten aus.

![chlimage_1-148](assets/chlimage_1-148.png)

Das obige Diagramm ist eine allgemeine Darstellung des Abfrageausführungsmechanismus von Apache Oak.

Zunächst wird die Abfrage in eine abstrakte Syntaxstruktur geparst. Anschließend wird die Abfrage überprüft und in SQL-2 umgewandelt, die für Oak-Abfragen die Muttersprache ist.

Anschließend wird jeder Index zur Schätzung der Kosten für die Abfrage herangezogen. Nach Abschluss werden die Ergebnisse aus dem billigsten Index abgerufen. Schließlich werden die Ergebnisse gefiltert, um sicherzustellen, dass der aktuelle Benutzer Lesezugriff auf das Ergebnis hat und dass das Ergebnis mit der vollständigen Abfrage übereinstimmt.

## Konfigurieren der Indizes {#configuring-the-indexes}

>[!NOTE]
>
>Für ein großes Repository ist das Erstellen eines Index ein zeitaufwendiger Vorgang. Dies gilt sowohl für die anfängliche Erstellung eines Index als auch für die Neuindizierung (Neuerstellung eines Index nach Änderung der Definition). Siehe auch [Fehlerbehebung bei Oak-Indizes](/help/sites-deploying/troubleshooting-oak-indexes.md) und [Langsame Neuindizierung verhindern](/help/sites-deploying/troubleshooting-oak-indexes.md#preventing-slow-re-indexing).

Wenn eine Neuindizierung in großen Repositorys erforderlich ist, insbesondere bei der Verwendung von MongoDB und für Volltext-Indizes, sollten Sie die Textvorextraktion erwägen und oak-run verwenden, um den anfänglichen Index zu erstellen und die Neuindizierung vorzunehmen.

Indizes werden als Knoten im Repository unter dem **Oak:index** Knoten.

Der Typ des Indexknotens muss **oak:QueryIndexDefinition.** Für jeden Indexer sind mehrere Konfigurationsoptionen als Knoteneigenschaften verfügbar. Weitere Informationen finden Sie unten in den Konfigurationsdetails für jeden Indextyp.

### Der Eigenschaftsindex {#the-property-index}

Der Eigenschaftsindex ist für Abfragen nützlich, die Eigenschaftseinschränkungen aufweisen, aber keine Volltext-Elemente sind. Der Index kann wie folgt konfiguriert werden:

1. Öffnen Sie CRXDE, indem Sie zu `http://localhost:4502/crx/de/index.jsp` gehen.
1. Erstellen Sie einen Knoten unter **oak:index**
1. Benennen Sie den Knoten . **PropertyIndex** und legen Sie den Knotentyp auf **oak:QueryIndexDefinition**
1. Legen Sie die folgenden Eigenschaften für den neuen Knoten fest:

   * **type:** `property` (vom Typ Zeichenfolge)
   * **propertyNames:** `jcr:uuid` (vom Typ „Name“)

   Dieses Beispiel indiziert die `jcr:uuid` -Eigenschaft, deren Auftrag darin besteht, die Universally Unique Identifier (UUID) des Knotens anzuzeigen, an den sie angehängt ist.

1. Speichern Sie die Änderungen.

Der Eigenschaftsindex verfügt über die folgenden Konfigurationsoptionen:

* Die **type** -Eigenschaft gibt den Indextyp an und muss in diesem Fall auf **property**

* Die **propertyNames** -Eigenschaft gibt die Liste der Eigenschaften an, die im Index gespeichert sind. Wenn es fehlt, wird der Knotenname als Referenzwert für den Eigenschaftsnamen verwendet. In diesem Beispiel wird die **jcr:uuid** -Eigenschaft, deren Auftrag darin besteht, die eindeutige Kennung (UUID) ihres Knotens anzuzeigen, wird zum Index hinzugefügt.

* Falls für die Kennzeichnung **unique** der Wert **true** festgelegt ist, wird dadurch eine Eindeutigkeitsbeschränkung auf den Eigenschaften-Index angewendet.

* Die **deklarierenNodeTypes** -Eigenschaft können Sie einen bestimmten Knotentyp angeben, für den der Index nur gilt.
* Die **reindex** Markierung, die, wenn auf **true**, Trigger eine vollständige Neuindizierung des Inhalts.

### Der sortierte Index {#the-ordered-index}

Der Index &quot;Geordnet&quot;ist eine Erweiterung des Eigenschaftenindex. Sie wird jedoch nicht mehr unterstützt. Indizes dieses Typs müssen durch die [Lucene-Eigenschaftsindex](#the-lucene-property-index).

### Der Lucene-Volltext-Index {#the-lucene-full-text-index}

AEM 6 beinhaltet einen auf Apache Lucene basierten Indexer.

Wenn ein Volltext-Index konfiguriert ist, verwenden alle Abfragen mit einer Volltext-Bedingung den Volltext-Index, unabhängig davon, ob andere indizierte Bedingungen vorliegen oder ob eine Pfadbeschränkung vorliegt.

Wenn kein Volltext-Index konfiguriert ist, funktionieren Abfragen mit Volltextbedingungen nicht erwartungsgemäß.

Da der Index über einen asynchronen Hintergrund-Thread aktualisiert wird, sind einige Volltextsuchen für einen kurzen Zeitraum nicht verfügbar, bis die Hintergrundprozesse abgeschlossen sind.

Sie können einen Lucene-Volltext-Index wie folgt konfigurieren:

1. Öffnen Sie CRXDE und erstellen Sie einen Knoten unter **oak:index**.
1. Benennen Sie den Knoten . **LuceneIndex** und legen Sie den Knotentyp auf **oak:QueryIndexDefinition**
1. Fügen Sie dem Knoten folgende Eigenschaften hinzu:

   * **type:** `lucene` (vom Typ Zeichenfolge)
   * **async:** `async` (vom Typ Zeichenfolge)

1. Speichern Sie die Änderungen.

Der Lucene-Index verfügt über die folgenden Konfigurationsoptionen:

* Die **type** -Eigenschaft, die den Indextyp angibt, auf **Lucene**
* Die **asynchron** -Eigenschaft, die auf **asynchron**. Dadurch wird der Indexaktualisierungsprozess an einen Hintergrund-Thread gesendet.
* Die **includePropertyTypes** -Eigenschaft, die definiert, welche Untergruppe von Eigenschaftstypen im Index enthalten sind.
* Die **excludePropertyNames** -Eigenschaft, die eine Liste von Eigenschaftsnamen definiert - Eigenschaften, die aus dem Index ausgeschlossen werden sollen.
* Die **reindex** Markierung, die bei Festlegung auf **true**, Trigger eine vollständige Neuindizierung des Inhalts.

### Volltextsuche {#understanding-fulltext-search}

Die Dokumentation in diesem Abschnitt bezieht sich beispielsweise auf Apache Lucene, Elasticsearch und Volltextindizes von PostgreSQL, SQLite und MySQL. Das folgende Beispiel ist für AEM / Oak / Lucene.

<b>Zu indizierende Daten</b>

Der Ausgangspunkt sind die Daten, die indiziert werden müssen. Nehmen wir als Beispiel die folgenden Dokumente:

| <b>Dokument-ID</b> | <b>Pfad</b> | <b>Volltext</b> |
| --- | --- | --- |
| 100 | /content/rubik | &quot;Rubik ist eine finnische Marke.&quot; |
| 200 | /content/rubiksCube | &quot;Der Rubikwürfel wurde 1974 erfunden.&quot; |
| 300 | /content/cube | &quot;Ein Cube ist ein dreidimensionales Objekt.&quot; |


<b>Invertierter Index</b>

Der Indizierungsmechanismus teilt den Volltext in Wörter namens &quot;Token&quot;auf und erstellt einen Index namens &quot;inverted index&quot;. Dieser Index enthält die Liste der Dokumente, in denen er für jedes Wort angezeigt wird.

Kurz, häufig verwendete Begriffe (auch &quot;Stoppwörter&quot; genannt) werden nicht indiziert. Alle Token werden in Kleinbuchstaben umgewandelt und die Zeichenfolge wird angewendet.

Sonderzeichen wie *&quot;-&quot;* nicht indiziert sind.

| <b>Token</b> | <b>Dokument-IDs</b> |
| --- | --- |
| 194 | ..., 200,... |
| Marke | ..., 100,... |
| Cube | ..., 200, 300,... |
| Dimension | 300 |
| Beenden | ..., 100,... |
| erfinden | 200 |
| Objekt | ..., 300,... |
| Rubik | ..., 100, 200,... |

Die Liste der Dokumente wird sortiert. Dies ist praktisch bei Abfragen.

<b>Suchen</b>

Nachfolgend finden Sie ein Beispiel für eine Abfrage. Beachten Sie, dass alle Sonderzeichen (z. B. *&#39;*) durch ein Leerzeichen ersetzt wurden:

```
/jcr:root/content//element(\*; cq:Page)`[` jcr:contains('Rubik s Cube')`]`
```

Die Wörter werden auf die gleiche Weise wie bei der Indizierung eingetauscht und gefiltert (z. B. wenn einzelne Zeichen entfernt werden). In diesem Fall ist die Suche also nach:

```
+:fulltext:rubik +:fulltext:cube
```

Der Index prüft die Liste der Dokumente für diese Wörter. Wenn es viele Dokumente gibt, kann die Liste groß sein. Angenommen, sie enthalten Folgendes:


| <b>Token</b> | <b>Dokument-IDs</b> |
| --- | --- |
| Rubik | 10, 100, 200, 1000 |
| Cube | 30, 200, 300, 2000 |


Lucene wechselt zwischen den beiden Listen (oder rundes Papierkorb) `n` Listen bei der Suche nach `n` Wörter):

* Lesen in der &quot;rubik&quot; bekommt den ersten Eintrag: es findet 10
* Lesen in &quot;Cube&quot;erhält den ersten Eintrag `>` = 10. 10 wird nicht gefunden, dann ist der nächste 30.
* Lesen in &quot;rubik&quot; erhält den ersten Eintrag `>` = 30: es findet 100.
* Lesen in &quot;Cube&quot;erhält den ersten Eintrag `>` = 100: es findet 200.
* Lesen in &quot;rubik&quot; erhält den ersten Eintrag `>` = 200. 200 wurde gefunden. Also ist Dokument 200 eine Übereinstimmung für beide Begriffe. Das erinnert sich.
* Lesen Sie in der &quot;rubik&quot; erhält den nächsten Eintrag: 1000.
* Lesen in &quot;Cube&quot;erhält den ersten Eintrag `>` = 1000: es findet 2000.
* Lesen in &quot;rubik&quot; erhält den ersten Eintrag `>` = 2000: Ende der Liste.
* Schließlich können Sie die Suche stoppen.

Das einzige Dokument, das beide Begriffe enthält, ist 200, wie im folgenden Beispiel gezeigt:

| 200 | /content/rubiksCube | &quot;Der Rubikwürfel wurde 1974 erfunden.&quot; |
| --- | --- | --- |

Wenn mehrere Einträge gefunden werden, werden sie nach Punktzahl sortiert.

### Der Lucene-Eigenschaftsindex {#the-lucene-property-index}

Seit **Oak 1.0.8** kann Lucene zum Erstellen von Indizes verwendet werden, die Eigenschaftenbeschränkungen beinhalten, die nicht Volltext sind.

Um einen Lucene-Eigenschaftsindex zu erhalten, muss die **fulltextEnabled** -Eigenschaft muss immer auf &quot;false&quot;gesetzt sein.

Sehen wir uns folgende Beispielabfrage an: 

```xml
select * from [nt:base] where [alias] = '/admin'
```

Um einen Lucene-Eigenschaftsindex für die obige Abfrage zu definieren, können Sie die folgende Definition hinzufügen, indem Sie einen Knoten unter **oak:index:**

* **Name:** `LucenePropertyIndex`
* **Typ:** `oak:QueryIndexDefinition`

Sobald der Knoten erstellt wurde, fügen Sie die folgenden Eigenschaften hinzu:

* **Typ:**

  ```xml
  lucene (of type String)
  ```

* **asynchron:**

  ```xml
  async (of type String)
  ```

* **fulltextEnabled:**

  ```xml
  false (of type Boolean)
  ```

* **includePropertyNames:** `["alias"] (of type String)`

>[!NOTE]
>
>Verglichen mit dem normalen Eigenschaften-Index ist der Lucene-Eigenschaften-Index immer im asynchronen Modus konfiguriert. Daher spiegeln die vom Index zurückgegebenen Ergebnisse möglicherweise nicht immer den aktuellsten Status des Repositorys wider.

>[!NOTE]
>
>Weitere Informationen zum Lucene-Eigenschaften-Index finden Sie auf der Dokumentationsseite zu [Apache Jackrabbit Oak Lucene](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Lucene Analyzer {#lucene-analyzers}

Seit Version 1.2.0 unterstützt Oak Lucene-Analyzer.

Analyzer werden sowohl bei der Indizierung eines Dokuments als auch bei der Abfrage verwendet. Ein Analyzer überprüft den Text von Feldern und generiert einen Token-Stream. Lucene-Analyzer bestehen aus einer Reihe von Token- und Filterklassen.

Die Analyzer können über die `analyzers` node (of type `nt:unstructured`) innerhalb der `oak:index` Definition.

Der Standard-Analyzer für einen Index wird im untergeordneten Knoten `default` des Analyzer-Knotens konfiguriert.

![chlimage_1-149](assets/chlimage_1-149.png)

>[!NOTE]
>
>Eine Liste der verfügbaren Analyzer finden Sie in der API-Dokumentation der verwendeten Lucene-Version.

#### Direktes Angeben der Analyzer-Klasse {#specifying-the-analyzer-class-directly}

Wenn Sie einen vordefinierten Analyzer verwenden möchten, können Sie ihn wie folgt konfigurieren:

1. Suchen Sie den Index, mit dem Sie den Analyzer verwenden möchten, unter der `oak:index` Knoten.

1. Erstellen Sie unter dem Index einen untergeordneten Knoten `default` vom Typ `nt:unstructured`.

1. Fügen Sie dem Knoten „default“ eine Eigenschaft mit folgenden Eigenschaften hinzu:

   * **Name:** `class`
   * **Typ:** `String`
   * **Wert:** `org.apache.lucene.analysis.standard.StandardAnalyzer`

   Der Wert ist der Name der Analyzer-Klasse, die Sie verwenden möchten.

   Sie können den Analyzer auch für eine bestimmte Lucene-Version festlegen, indem Sie die optionale `luceneMatchVersion` string -Eigenschaft. Eine gültige Syntax für die Verwendung mit Lucene 4.7 lautet:

   * **Name:** `luceneMatchVersion`
   * **Typ:** `String`
   * **Wert:** `LUCENE_47`

   Wenn `luceneMatchVersion` nicht angegeben ist, verwendet Oak die Version von Lucene, mit der es geliefert wird.

1. Wenn Sie den Analyzer-Konfigurationen eine Stoppwörter-Datei hinzufügen möchten, können Sie einen Knoten unter der `default` eine mit den folgenden Eigenschaften:

   * **Name:** `stopwords`
   * **Typ:** `nt:file`

#### Erstellen von Analyzern anhand der Komposition {#creating-analyzers-via-composition}

Analyzer können auch basierend auf `Tokenizers`, `TokenFilters`, und `CharFilters`. Sie können dies tun, indem Sie einen Analyzer angeben und untergeordnete Knoten der optionalen Tokenizer und Filter erstellen, die in der angegebenen Reihenfolge angewendet werden. Siehe auch [https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema](https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema)

Sehen Sie sich diese Knotenstruktur als Beispiel an:

* **Name:** `analyzers`

   * **Name:** `default`

      * **Name:** `charFilters`
      * **Typ:** `nt:unstructured`

         * **Name:** `HTMLStrip`
         * **Name:** `Mapping`

      * **Name:** `tokenizer`

         * **Eigenschaftsname:** `name`

            * **Typ:** `String`
            * **Wert:** `Standard`

      * **Name:** `filters`
      * **Typ:** `nt:unstructured`

         * **Name:** `LowerCase`
         * **Name:** `Stop`

            * **Eigenschaftsname:** `words`

               * **Typ:** `String`
               * **Wert:** `stop1.txt, stop2.txt`

            * **Name:** `stop1.txt`

               * **Typ:** `nt:file`

            * **Name:** `stop2.txt`

               * **Typ:** `nt:file`

Der Name der Filter, charFilters und Tokenizer wird gebildet, indem die Factory-Suffixe entfernt werden. So:

* `org.apache.lucene.analysis.standard.StandardTokenizerFactory` wird zu `standard`

* `org.apache.lucene.analysis.charfilter.MappingCharFilterFactory` wird zu `Mapping`

* `org.apache.lucene.analysis.core.StopFilterFactory` wird zu `Stop`

Jeder für die Factory erforderliche Konfigurationsparameter wird als Eigenschaft des betreffenden Knotens angegeben.

Für Fälle wie das Laden von Stoppwörtern, in denen Inhalte aus externen Dateien geladen werden müssen, kann der Inhalt bereitgestellt werden, indem ein untergeordneter Knoten von `nt:file` Typ der betreffenden Datei.

### Der Solr-Index {#the-solr-index}

Der Solr-Index dient der Volltextsuche, kann aber auch zur Indexsuche nach Pfad, Eigenschaftsbeschränkungen und primären Typbeschränkungen verwendet werden. Das bedeutet, dass der Solr-Index in Oak für jede Art von JCR-Abfrage verwendet werden kann.

Die Integration in AEM erfolgt auf Repository-Ebene, sodass Solr einer der möglichen Indizes ist, die in Oak verwendet werden können, der neuen, mit AEM gelieferten Repository-Implementierung.

Es kann so konfiguriert werden, dass es als Remote-Server mit der AEM-Instanz funktioniert.

### Konfigurieren von AEM mit einem einzelnen Remote-Solr-Server {#configuring-aem-with-a-single-remote-solr-server}

AEM kann auch mit einer Remote-Solr-Server-Instanz konfiguriert werden:

1. Laden Sie die neueste Version von Solr herunter und extrahieren Sie sie. Weitere Informationen dazu finden Sie im Abschnitt [Dokumentation zur Installation von Apache Solr](https://solr.apache.org/guide/6_6/installing-solr.html).
1. Erstellen Sie zwei Solr-Shards. Erstellen Sie dazu Ordner für jedes Shard in dem Ordner, in den Solr entpackt wurde:

   * Erstellen Sie für das erste Shard folgenden Ordner:

   `<solrunpackdirectory>\aemsolr1\node1`

   * Erstellen Sie für das zweite Shard folgenden Ordner: 

   `<solrunpackdirectory>\aemsolr2\node2`

1. Suchen Sie die Beispiel-Instanz im Solr-Paket. Sie befindet sich im Ordner &quot; `example`&quot; in der Wurzel des Pakets.
1. Kopieren Sie die folgenden Ordner von der Beispiel-Instanz in die Ordner der zwei Shards (`aemsolr1\node1` und `aemsolr2\node2`):

   * `contexts`
   * `etc`
   * `lib`
   * `resources`
   * `scripts`
   * `solr-webapp`
   * `webapps`
   * `start.jar`

1. Erstellen Sie einen Ordner mit dem Namen `cfg`&quot; in jedem der beiden Shard-Ordner.
1. Speichern Sie die Solr- und ZooKeeper-Konfigurationsdateien in den neu erstellten `cfg`-Ordnern.

   >[!NOTE]
   >
   >Weitere Informationen zur Solr- und ZooKeeper-Konfiguration finden Sie in der Dokumentation zur [Solr-Konfiguration](https://cwiki.apache.org/confluence/display/solr/ConfiguringSolr) bzw. im [ZooKeeper-Handbuch „Erste Schritte“](https://zookeeper.apache.org/doc/r3.1.2/zookeeperStarted.html).

1. Starten Sie den ersten Shard mit ZooKeeper-Unterstützung, indem Sie zu `aemsolr1\node1` wechseln und folgenden Befehl ausführen:

   ```xml
   java -Xmx2g -Dbootstrap_confdir=./cfg/oak/conf -Dcollection.configName=myconf -DzkRun -DnumShards=2 -jar start.jar
   ```

1. Starten Sie den zweiten Shard, indem Sie zu `aemsolr2\node2` wechseln und folgenden Befehl ausführen:

   ```xml
   java -Xmx2g -Djetty.port=7574 -DzkHost=localhost:9983 -jar start.jar
   ```

1. Wenn Sie beide Shards gestartet haben, testen Sie die ordnungsgemäße Funktion, indem Sie eine Verbindung zur Solr-Schnittstelle unter `http://localhost:8983/solr/#/` /#/ herstellen.
1. Starten Sie AEM und wechseln Sie zur Web-Konsole unter `http://localhost:4502/system/console/configMgr`
1. Legen Sie folgende Konfiguration unter **Oak Solr remote server configuration** fest:

   * Solr-HTTP-URL: `http://localhost:8983/solr/`

1. Auswählen **Remote Solr** in der Dropdownliste unter **Oak Solr** Server-Anbieter.

1. Gehen Sie zu CRXDE und melden Sie sich als Administrator an.
1. Erstellen Sie einen Knoten mit dem Namen **solrIndex** under **oak:index** und legen Sie die folgenden Eigenschaften fest:

   * **type:** solr (vom Typ „String“)
   * **async:** async (vom Typ „String“)
   * **reindex:** true (vom Typ „Boolean“)

1. Speichern Sie die Änderungen.

#### Empfohlene Konfiguration für Solr {#recommended-configuration-for-solr}

Nachfolgend finden Sie ein Beispiel für eine Basiskonfiguration, die mit allen drei Solr-Bereitstellungen verwendet werden kann, die in diesem Artikel beschrieben werden. Diese Konfiguration basiert auf den dedizierten Eigenschaften-Indizes, die bereits in AEM vorhanden sind, und sollte nicht mit anderen Anwendungen verwendet werden.

Um sie ordnungsgemäß zu verwenden, müssen Sie den Inhalt des Archivs direkt im Solr Home Directory platzieren. Bei Bereitstellungen mit mehreren Knoten sollte diese direkt unter den Stammordner jedes Knotens platziert werden.

Empfohlene Solr-Konfigurationsdateien

[Datei laden](assets/recommended-conf.zip)

### AEM-Indizierungs-Tools {#aem-indexing-tools}

In AEM 6.1 sind auch zwei Indizierungs-Tools aus AEM 6.0 integriert, die Teil der Adobe Consulting Services Commons-Tools sind:

1. **Explain Query**: ein Tool, das Admins das Verständnis erleichtert, wie Abfragen ausgeführt werden.
1. **Oak Index Manager**, eine Webbenutzeroberfläche zur Pflege vorhandener Indizes.

Sie können sie jetzt erreichen, indem Sie **Tools - Vorgänge - Dashboard - Diagnose** über den AEM Willkommensbildschirm aus.

Weitere Informationen zu ihrer Verwendung finden Sie unter [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

#### Erstellen von Eigenschaftenindizes über OSGi {#creating-property-indexes-via-osgi}

Das ACS Commons-Paket stellt auch OSGi-Konfigurationen bereit, die zum Erstellen von Eigenschaftenindizes verwendet werden können.

Sie können über die Web-Konsole darauf zugreifen, indem Sie nach **Oak-Eigenschaftenindex sicherstellen**&quot;.

![chlimage_1-150](assets/chlimage_1-150.png)

### Fehlerbehebung bei Indizierungsproblemen {#troubleshooting-indexing-issues}

Situationen können auftreten, in denen die Ausführung von Abfragen lange dauert und die allgemeine Systemreaktionszeit langsam ist.

In diesem Abschnitt finden Sie eine Reihe von Empfehlungen dazu, was getan werden muss, um die Ursache solcher Probleme aufzudecken, und Ratschläge dazu, wie sie gelöst werden können.

#### Vorbereiten von Debugging-Informationen für Analysen {#preparing-debugging-info-for-analysis}

Die einfachste Möglichkeit, die erforderlichen Informationen für die ausgeführte Abfrage zu erhalten, besteht darin, die [Tool &quot;Abfrage erläutern&quot;](/help/sites-administering/operations-dashboard.md#explain-query). Auf diese Weise können Sie die genauen Informationen erfassen, die zum Debuggen einer langsamen Abfrage erforderlich sind, ohne die Informationen auf Protokollebene einsehen zu müssen. Dies ist hilfreich, wenn Sie wissen, welche Abfrage debuggt werden soll.

Wenn dies aus irgendeinem Grund nicht möglich ist, können Sie die Indizierungsprotokolle in einer einzigen Datei sammeln und sie zur Fehlerbehebung für Ihr bestimmtes Problem verwenden.

#### Aktivieren der Protokollierung {#enable-logging}

Zum Aktivieren der Protokollierung müssen Sie **DEBUG** Ebenenprotokolle für die Kategorien, die sich auf Oak-Indizierung und -Abfragen beziehen. Diese Kategorien sind: 

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

Die **com.day.cq.search** -Kategorie ist nur anwendbar, wenn Sie das AEM bereitgestellte QueryBuilder-Dienstprogramm verwenden.

>[!NOTE]
>
>Es ist wichtig, dass die Protokolle nur für die Dauer der Ausführung der Abfrage, die Sie beheben möchten, auf DEBUG gesetzt werden. Andernfalls werden im Laufe der Zeit viele Ereignisse in den Protokollen generiert. Aus diesem Grund wechseln Sie nach der Erfassung der erforderlichen Protokolle für die oben genannten Kategorien zurück zur Protokollierung auf INFO-Ebene.

Sie können die Protokollierung aktivieren, indem Sie folgende Schritte ausführen:

1. Lassen Sie Ihren Browser auf `https://serveraddress:port/system/console/slinglog` verweisen.
1. Klicken Sie auf die Schaltfläche **Neue Protokollierung hinzufügen** unten in der Konsole.
1. Fügen Sie die oben genannten Kategorien in der neu erstellten Reihe hinzu. Verwenden Sie das **+**-Symbol, um einer Protokollierung mehr als eine Kategorie hinzuzufügen. 
1. Auswählen **DEBUG** aus dem **Protokollebene** Dropdown-Liste.
1. Geben Sie als Ausgabedatei `logs/queryDebug.log` an. Dadurch werden alle DEBUG-Ereignisse in einer Protokolldatei zusammengeführt.
1. Führen Sie die Abfrage aus oder geben Sie die Seite aus, auf der die Abfrage verwendet wird, die Sie debuggen möchten.
1. Wenn Sie die Abfrage ausgeführt haben, wechseln Sie zurück zur Protokollierungskonsole und ändern Sie die Protokollierungsebene der neu erstellten Protokollierung in **INFO**.

#### Indexkonfiguration {#index-configuration}

Die Art und Weise, wie die Abfrage ausgewertet wird, wird durch die Indexkonfiguration stark beeinflusst. Es ist wichtig, die Indexkonfiguration zu analysieren oder an die Unterstützung zu senden. Sie können die Konfiguration entweder als Inhaltspaket abrufen oder eine JSON-Ausgabe abrufen.

Normalerweise wird die Indizierungskonfiguration unter dem `/oak:index` -Knoten in CRXDE können Sie die JSON-Version abrufen unter:

`https://serveraddress:port/oak:index.tidy.-1.json`

Wenn der Index an einem anderen Speicherort konfiguriert ist, ändern Sie den Pfad entsprechend.

#### MBean-Ausgabe {#mbean-output}

Manchmal ist es hilfreich, die Ausgabe von indexbezogenen MBeans zum Debugging bereitzustellen. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur JMX-Konsole unter:
   `https://serveraddress:port/system/console/jmx`

1. Suchen Sie nach den folgenden MBeans:

   * Lucene-Indexstatistiken
   * CopyOnRead-Unterstützungsstatistiken
   * Oak Query Statistics
   * IndexStats

1. Klicken Sie auf die einzelnen MBeans, um Leistungsstatistiken zu erhalten. Erstellen Sie einen Screenshot oder notieren Sie ihn, falls eine Support-Übermittlung erforderlich ist.

Sie können auch die JSON-Version dieser Statistiken unter folgenden URLs abrufen:

* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`

Sie können die konsolidierte JMX-Ausgabe auch über `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak.tidy.3.json`. Hierdurch werden alle Oak-spezifischen MBean-Details im JSON-Format erfasst.

#### Weitere Details {#other-details}

Sie können zusätzliche Details sammeln, um das Problem zu beheben, z. B.:

1. Die Oak-Version, auf der Ihre Instanz ausgeführt wird. Öffnen Sie dazu CRXDE. Die Version wird unten rechts auf der Begrüßungsseite anzeigt. Sie können die Version auch im `org.apache.jackrabbit.oak-core`-Bundle überprüfen.
1. Die Ausgabe des QueryBuilder-Debugger zu der problematischen Abfrage. Der Debugger kann unter `https://serveraddress:port/libs/cq/search/content/querydebug.html` aufgerufen werden.
