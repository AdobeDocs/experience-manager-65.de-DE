---
title: Oak-Abfragen und Indizierung
description: Erfahren Sie, wie Sie Indizes in Adobe Experience Manager (AEM) 6.5 konfigurieren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/queries-and-indexing
feature: Configuring
exl-id: d9ec7728-84f7-42c8-9c80-e59e029840da
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '3034'
ht-degree: 99%

---

# Oak-Abfragen und Indizierung{#oak-queries-and-indexing}

>[!NOTE]
>
>In diesem Artikel geht es um die Konfiguration von Indizes in AEM 6. Informationen zur besten Vorgehensweise beim Optimieren von Abfragen- und Indizierungsleistung finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

## Einführung {#introduction}

Im Gegensatz zu Jackrabbit 2 indiziert Oak Inhalte nicht standardmäßig. Benutzerdefinierte Indizes müssen daher bei Bedarf erstellt werden, ähnlich wie bei herkömmlichen relationalen Datenbanken. Wenn für eine bestimmte Abfrage kein Index vorhanden ist, kann es sein, dass viele Knoten durchlaufen werden. Die Abfrage funktioniert möglicherweise immer noch, ist aber wahrscheinlich langsam.

Wenn Oak auf eine Abfrage ohne Index stößt, wird eine Protokollmeldung der Stufe WARNUNG ausgegeben:

```xml
*WARN* Traversed 1000 nodes with filter Filter(query=select ...) consider creating an index or changing the query
```

## Unterstützte Abfragesprachen {#supported-query-languages}

Die Oak-Abfrage-Engine unterstützt die folgenden Sprachen:

* XPath (empfohlen)
* SQL-2
* SQL (veraltet)
* JQOM

## Indextypen und Kostenberechnung {#indexer-types-and-cost-calculation}

Das auf Apache Oak basierende Backend ermöglicht die Einbindung verschiedener Indexer in das Repository.

Ein Indexer ist der **Eigenschaftenindex**, für den die Indexdefinition im Repository selbst gespeichert wird.

Implementierungen für **Apache Lucene** und **Solr** sind ebenfalls standardmäßig verfügbar und unterstützen die Volltextindizierung.

Der **Traversalindex** wird verwendet, wenn kein anderer Indexer verfügbar ist. Das bedeutet, dass der Inhalt nicht indiziert ist und Inhaltsknoten durchlaufen werden, um Übereinstimmungen mit der Abfrage zu finden.

Wenn für eine Abfrage mehrere Indexer verfügbar sind, schätzt jeder verfügbare Indexer die Kosten für die Ausführung der Abfrage. Oak wählt dann den Indexer mit den niedrigsten geschätzten Kosten aus.

![chlimage_1-148](assets/chlimage_1-148.png)

Die obige Abbildung ist eine allgemeine Darstellung des Abfrageausführungsmechanismus von Apache Oak.

Zunächst wird die Abfrage in eine abstrakte Syntaxstruktur geparst. Anschließend wird die Abfrage überprüft und in SQL-2 (die native Sprache für Oak-Abfragen) umgewandelt.

Anschließend wird jeder Index zur Schätzung der Kosten für die Abfrage herangezogen. Danach werden die Ergebnisse aus dem günstigsten Index abgerufen. Schließlich werden die Ergebnisse gefiltert, um sicherzustellen, dass die aktuelle Benutzerin bzw. der aktuelle Benutzer Lesezugriff auf das Ergebnis hat und dass das Ergebnis mit der vollständigen Abfrage übereinstimmt.

## Konfigurieren der Indizes {#configuring-the-indexes}

>[!NOTE]
>
>Bei großen Repositorys ist das Erstellen eines Index ein zeitaufwendiger Vorgang. Dies gilt sowohl für die erstmalige Indexerstellung als auch für eine Neuindizierung (Neuerstellung des Index nach Änderung der Definition). Weitere Informationen finden Sie unter [Fehlerbehebung bei Oak-Indizes](/help/sites-deploying/troubleshooting-oak-indexes.md) und [Verhindern einer langsamen Neuindizierung](/help/sites-deploying/troubleshooting-oak-indexes.md#preventing-slow-re-indexing).

Wenn große Repositorys neu indiziert werden müssen, insbesondere wenn MongoDB verwendet wird und eine Volltextindizierung erforderlich ist, empfiehlt es sich gegebenenfalls, eine Textvorextraktion durchzuführen, den Ausgangsindex mit „oak-run“ zu erstellen und anschließend eine Neuindizierung durchzuführen.

Indizes werden im Repository unter dem Knoten **Oak:index** als Knoten konfiguriert.

Der Typ des Indexknotens muss wie folgt lauten: **oak:QueryIndexDefinition.** Für jeden Indexer sind mehrere Konfigurationsoptionen als Knoteneigenschaften verfügbar. Weitere Informationen finden Sie unten in den Konfigurationsdetails für jeden Indexertyp.

### Der Eigenschaftenindex {#the-property-index}

Der Eigenschaftenindex ist für Abfragen nützlich, die Eigenschaftseinschränkungen aufweisen, aber keine Volltextelemente sind. Der Index kann wie folgt konfiguriert werden:

1. Öffnen Sie CRXDE, indem Sie zu `http://localhost:4502/crx/de/index.jsp` gehen.
1. Erstellen Sie einen Knoten unter **oak:index**
1. Nennen Sie den Knoten **PropertyIndex** und legen Sie den Knotentyp auf **oak:QueryIndexDefinition** fest
1. Legen Sie die folgenden Eigenschaften für den neuen Knoten fest:

   * **type:** `property` (vom Typ Zeichenfolge)
   * **propertyNames:** `jcr:uuid` (vom Typ „Name“)

   Bei diesem Beispiel wird die Eigenschaft `jcr:uuid` indiziert, die dazu dient, den UUID (Universally Unique Identifier) des verknüpften Knotens anzuzeigen.

1. Speichern Sie die Änderungen.

Der Eigenschaftenindex verfügt über die folgenden Konfigurationsoptionen:

* Die Eigenschaft **type** gibt den Indextyp an und muss in diesem Fall **property** lauten.

* Die Eigenschaft **propertyNames** gibt die Liste der Eigenschaften an, die im Index gespeichert werden. Wenn sie fehlt, wird der Knotenname als Referenzwert für den Eigenschaftsnamen verwendet. In diesem Beispiel wird die Eigenschaft **jcr:uuid**, deren Aufgabe darin besteht, die eindeutige Kennung (UUID) ihres Knotens anzuzeigen, zum Index hinzugefügt.

* Falls für die Kennzeichnung **unique** der Wert **true** festgelegt ist, wird dadurch eine Eindeutigkeitsbeschränkung auf den Eigenschaften-Index angewendet.

* Mit der Eigenschaft **declaringNodeTypes** können Sie einen bestimmten Knotentyp angeben, für den der Index ausschließlich gilt.
* Falls für das Flag **reindex** der Wert auf **true** festgelegt ist, wird eine vollständige Neuindizierung des Inhalts ausgelöst.

### Der Index „Geordnet“ {#the-ordered-index}

Der Index „Geordnet“ ist eine Erweiterung des Eigenschaftenindex. Er wird jedoch nicht mehr unterstützt. Indizes dieses Typs müssen durch den [Lucene-Eigenschaften-Index](#the-lucene-property-index) ersetzt werden.

### Der Lucene-Volltext-Index {#the-lucene-full-text-index}

AEM 6 beinhaltet einen auf Apache Lucene basierten Indexer.

Wenn ein Volltextindex konfiguriert ist, verwenden alle Abfragen mit einer Volltextbedingung den Volltextindex, unabhängig davon, ob andere Bedingungen indiziert sind oder ob eine Pfadbeschränkung vorliegt.

Wenn kein Volltextindex konfiguriert ist, funktionieren Abfragen mit Volltextbedingungen nicht erwartungsgemäß.

Da der Index über einen asynchronen Hintergrund-Thread aktualisiert wird, sind bestimmte Volltextsuchen für einen kurzen Zeitraum nicht verfügbar, bis die Prozesse im Hintergrund beendet sind.

Sie können einen Lucene-Volltextindex wie folgt konfigurieren:

1. Öffnen Sie CRXDE und erstellen Sie einen Knoten unter **oak:index**.
1. Nennen Sie den Knoten **LuceneIndex** und legen Sie den Knotentyp auf **oak:QueryIndexDefinition** fest
1. Fügen Sie dem Knoten folgende Eigenschaften hinzu:

   * **type:** `lucene` (vom Typ Zeichenfolge)
   * **async:** `async` (vom Typ Zeichenfolge)

1. Speichern Sie die Änderungen.

Der Lucene-Index verfügt über die folgenden Konfigurationsoptionen:

* Die Eigenschaft **type**, die den Indextyp angibt, muss auf **lucene** festgelegt sein
* Die Eigenschaft **async**, die auf **async** festgelegt sein muss. Dadurch wird der Indexaktualisierungsprozess an einen Hintergrund-Thread gesendet.
* Die Eigenschaft **includePropertyTypes**, die definiert, welche Untergruppe von Eigenschaftstypen im Index enthalten sind.
* Die Eigenschaft **excludePropertyNames**, die eine Liste mit Eigenschaftennamen definiert, nämlich Eigenschaften, die vom Index ausgeschlossen sein sollen.
* Das Flag **reindex**, das bei Festlegung auf **true** eine vollständige Neuindizierung des Inhalts auslöst.

### Grundlegendes zur Volltextsuche {#understanding-fulltext-search}

Die Dokumentation in diesem Abschnitt gilt beispielsweise für Apache Lucene, ElasticSearch und Volltextindizes von PostgreSQL, SQLite und MySQL.  Das folgende Beispiel gilt für AEM/Oak/Lucene.

<b>Zu indizierende Daten</b>

Der Ausgangspunkt sind die Daten, die indiziert werden müssen. Nehmen wir als Beispiel die folgenden Dokumente:

| <b>Dokument-ID</b> | <b>Pfad</b> | <b>Volltext</b> |
| --- | --- | --- |
| 100 | /content/rubik | „Rubik ist eine finnische Marke.“ |
| 200 | /content/rubiksCube | „Der Rubikwürfel wurde 1974 erfunden.“ |
| 300 | /content/cube | „Ein Würfel ist ein dreidimensionales Objekt.“ |


<b>Invertierter Index</b>

Der Indizierungsmechanismus teilt den Volltext in Wörter, genannt „Token“, auf und erstellt einen Index namens „invertierter Index“. Dieser Index enthält für jedes Wort die Liste der Dokumente, in denen es erscheint.

Kurze, häufige Wörter (auch „Stoppwörter“ genannt) werden nicht indiziert. Alle Token werden in Kleinbuchstaben umgewandelt und Wörter werden auf ihre Stammform reduziert.

Sonderzeichen wie *„-“* werden nicht indiziert.

| <b>Token</b> | <b>Dokument-IDs</b> |
| --- | --- |
| 194 | ..., 200, ... |
| Marke | ..., 100, ... |
| Würfel | ..., 200, 300,... |
| Dimension | 300 |
| beenden | ..., 100, ... |
| erfinden | 200 |
| Objekt | ..., 300, ... |
| Rubik | …, 100, 200, … |

Die Liste der Dokumente ist sortiert. Dies ist bei Abfragen nützlich.

<b>Suchen</b>

Nachfolgend finden Sie ein Beispiel für eine Abfrage. Beachten Sie, dass alle Sonderzeichen (z. B. *&#39;*) durch ein Leerzeichen ersetzt wurden:

```
/jcr:root/content//element(\*; cq:Page)`[` jcr:contains('Rubik s Cube')`]`
```

Die Wörter werden auf die gleiche Weise wie bei der Indizierung tokenisiert und gefiltert (z. B. werden Wörter bestehend aus nur einem Zeichen entfernt). In diesem Fall ist die Suche also nach:

```
+:fulltext:rubik +:fulltext:cube
```

Der Index konsultiert die Liste der Dokumente zu diesen Wörtern. Wenn es viele Dokumente gibt, können die Listen groß sein. Angenommen, sie enthalten etwa Folgendes:


| <b>Token</b> | <b>Dokument-IDs</b> |
| --- | --- |
| Rubik | 10, 100, 200, 1000 |
| Würfel | 30, 200, 300, 2000 |


Lucene wechselt zwischen den beiden Listen (oder geht nacheinander `n` Listen durch, wenn es nach `n` Wörtern sucht):

* Das Einlesen von „Rubik“ liefert den ersten Eintrag: es werden 10 gefunden
* Das Einlesen von „Würfel“ liefert den ersten Eintrag `>` = 10. 10 wird nicht gefunden, der Nächste ist 30.
* Beim Lesen in „Rubik“ wird der erste Eintrag `>` = 30 abgerufen. 100 wird gefunden.
* Beim Lesen in „Würfel“ wird der erste Eintrag `>` = 100 abgerufen. 200 wird gefunden.
* Beim Lesen in „Rubik“ wird der erste Eintrag `>` = 200 abgerufen. 200 wird gefunden. Also ist Dokument 200 eine Übereinstimmung für beide Begriffe. Dies wird gespeichert.
* Beim Lesen in „Rubik“ wird der nächste Eintrag abgerufen: 1000.
* Beim Lesen in „Würfel“ wird der erste Eintrag `>` = 1000 abgerufen. 2000 wird gefunden.
* Beim Lesen in „Rubik“ wird der erste Eintrag `>` = 2000 abgerufen, das Ende der Liste.
* Schließlich können Sie die Suche beenden.

Das einzige Dokument, das beide Begriffe enthält, ist 200, wie im folgenden Beispiel gezeigt:

| 200 | /content/rubiksCube | „Der Rubikwürfel wurde 1974 erfunden.“ |
| --- | --- | --- |

Wenn mehrere Einträge gefunden werden, werden sie nach ihrer Punktzahl sortiert.

### Der Lucene-Eigenschaftenindex {#the-lucene-property-index}

Seit **Oak 1.0.8** kann Lucene zum Erstellen von Indizes verwendet werden, die Eigenschaftsbeschränkungen beinhalten, bei denen es sich aber nicht um Volltext handelt.

Für einen Lucene-Eigenschaftenindex muss die Eigenschaft **fulltextEnabled** immer auf „false“ gesetzt sein.

Sehen wir uns folgende Beispielabfrage an: 

```xml
select * from [nt:base] where [alias] = '/admin'
```

Um einen Lucene-Eigenschaftsindex für die obige Abfrage zu definieren, können Sie die folgende Definition hinzufügen, indem Sie einen Knoten unter erstellen. **`oak:index`:**

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
>Verglichen mit dem normalen Eigenschaften-Index ist der Lucene-Eigenschaften-Index immer im asynchronen Modus konfiguriert. Daher entsprechen die vom Index zurückgegebenen Ergebnisse möglicherweise nicht immer dem aktuellen Stand des Repositorys.

>[!NOTE]
>
>Weitere Informationen zum Lucene-Eigenschaften-Index finden Sie auf der Dokumentationsseite zu [Apache Jackrabbit Oak Lucene](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Lucene-Analyzer {#lucene-analyzers}

Seit Version 1.2.0 unterstützt Oak Lucene-Analyzer.

Analyzer werden sowohl bei der Indizierung eines Dokuments als auch zum Zeitpunkt der Abfrage verwendet. Ein Analyzer überprüft den Text von Feldern und generiert einen Tokenstream. Lucene-Analyzer bestehen aus einer Reihe von Tokenizer- und Filterklassen.

Die Analyzer können über den Knoten `analyzers` (vom Typ `nt:unstructured`) in der `oak:index`-Definition konfiguriert werden.

Der Standard-Analyzer für einen Index wird im untergeordneten Knoten `default` des Analyzer-Knotens konfiguriert.

![chlimage_1-149](assets/chlimage_1-149.png)

>[!NOTE]
>
>Eine Liste der verfügbaren Analyzer finden Sie in der API-Dokumentation für die von Ihnen verwendete Lucene-Version.

#### Direktes Angeben der Analyzer-Klasse {#specifying-the-analyzer-class-directly}

Wenn Sie einen vordefinierten Analyzer verwenden möchten, können Sie ihn wie folgt konfigurieren:

1. Suchen Sie unter dem Knoten `oak:index` nach dem Index, mit dem der Analyzer verwendet werden soll.

1. Erstellen Sie unter dem Index einen untergeordneten Knoten `default` vom Typ `nt:unstructured`.

1. Fügen Sie dem Knoten „default“ eine Eigenschaft mit folgenden Eigenschaften hinzu:

   * **Name:** `class`
   * **Typ:** `String`
   * **Wert:** `org.apache.lucene.analysis.standard.StandardAnalyzer`

   Der Wert ist der Name der Analyzer-Klasse, die verwendet werden soll.

   Sie können auch einen Analyzer für eine bestimmte Lucene-Version festlegen, indem Sie die optionale String-Eigenschaft `luceneMatchVersion` verwenden. Eine gültige Syntax für die Verwendung mit Lucene 4.7 lautet:

   * **Name:** `luceneMatchVersion`
   * **Typ:** `String`
   * **Wert:** `LUCENE_47`

   Wenn `luceneMatchVersion` nicht angegeben ist, verwendet Oak die im Lieferumfang enthaltene Version von Lucene.

1. Wenn Sie eine Datei der Stoppwörter zu Analyzer-Konfigurationen hinzufügen möchten, können Sie einen Knoten unter dem Knoten `default` mit folgenden Eigenschaften erstellen:

   * **Name:** `stopwords`
   * **Typ:** `nt:file`

#### Erstellen von Analyzern durch Komposition {#creating-analyzers-via-composition}

Analyzer können auch anhand der Eigenschaften `Tokenizers`, `TokenFilters` und `CharFilters` zusammengestellt werden. Geben Sie dazu einen Analyzer an und erstellen Sie untergeordnete Knoten der optionalen Tokenizer und Filter, die in der aufgeführten Reihenfolge angewendet werden. Siehe auch [https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema](https://cwiki.apache.org/confluence/display/solr/AnalyzersTokenizersTokenFilters#Specifying_an_Analyzer_in_the_schema).

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

Der Name der Filter, charFilters und Tokenizer wird gebildet, indem die Factory-Suffixe entfernt werden. Ergebnis:

* `org.apache.lucene.analysis.standard.StandardTokenizerFactory` wird zu `standard`

* `org.apache.lucene.analysis.charfilter.MappingCharFilterFactory` wird zu `Mapping`

* `org.apache.lucene.analysis.core.StopFilterFactory` wird zu `Stop`

Für die Factory erforderliche Konfigurationsparameter werden als Eigenschaft des entsprechenden Knotens angegeben.

In Fällen wie beim Laden von Stoppwörtern, wo Inhalt aus externem Dateien geladen werden muss, kann der Inhalt durch Erstellen eines untergeordneten Knotens vom Typ `nt:file` für die betroffene Datei bereitgestellt werden.

### Der Solr-Index {#the-solr-index}

Der Solr-Index dient der Volltextsuche, kann aber auch zur Indexsuche nach Pfad, Eigenschaftsbeschränkungen und primären Typbeschränkungen verwendet werden. Das bedeutet, dass der Solr-Index in Oak für jede Art von JCR-Abfrage verwendet werden kann.

Die Integration in AEM erfolgt auf Repository-Ebene, sodass Solr einer der möglichen Indizes ist, die in Oak verwendet werden können, der neuen, mit AEM bereitgestellten Repository-Implementierung.

Es kann so konfiguriert werden, dass es als Remote-Server mit der AEM-Instanz funktioniert.

### Konfigurieren von AEM mit einem einzelnen Remote-Solr-Server {#configuring-aem-with-a-single-remote-solr-server}

AEM kann auch mit einer Remote-Solr-Server-Instanz konfiguriert werden:

1. Laden Sie die neueste Version von Solr herunter und extrahieren Sie sie. Weitere Informationen dazu finden Sie in der [Dokumentation zur Installation von Apache Solr](https://solr.apache.org/guide/6_6/installing-solr.html).
1. Erstellen Sie zwei Solr-Shards. Erstellen Sie dazu Ordner für jedes Shard in dem Ordner, in den Solr entpackt wurde:

   * Erstellen Sie für das erste Shard folgenden Ordner:

   `<solrunpackdirectory>\aemsolr1\node1`

   * Erstellen Sie für das zweite Shard folgenden Ordner: 

   `<solrunpackdirectory>\aemsolr2\node2`

1. Suchen Sie die Beispiel-Instanz im Solr-Paket. Sie befindet sich im Ordner „`example`“ im Stammverzeichnis des Pakets.
1. Kopieren Sie die folgenden Ordner von der Beispiel-Instanz in die beiden Shard-Ordner (`aemsolr1\node1` und `aemsolr2\node2`):

   * `contexts`
   * `etc`
   * `lib`
   * `resources`
   * `scripts`
   * `solr-webapp`
   * `webapps`
   * `start.jar`

1. Erstellen Sie in jedem der beiden Shard-Ordner einen Ordner mit dem Namen `cfg`.
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

1. Wählen Sie in der Dropdown-Liste unter dem **Oak Solr**-Server-Anbieter die Option **Remote Solr** aus.

1. Gehen Sie zu CRXDE und melden Sie sich als Admin an.
1. Erstellen Sie unter **oak:index** einen Knoten mit dem Namen **solrIndex** und legen Sie die folgenden Eigenschaften fest:

   * **type:** solr (vom Typ „String“)
   * **async:** async (vom Typ „String“)
   * **reindex:** true (vom Typ „Boolean“)

1. Speichern Sie die Änderungen.

#### Empfohlene Konfiguration für Solr {#recommended-configuration-for-solr}

Nachfolgend finden Sie ein Beispiel für eine Basiskonfiguration, die bei allen drei in diesem Artikel beschriebenen Solr-Bereitstellungen verwendet werden kann. Diese Konfiguration basiert auf den dedizierten Eigenschaftenindizes, die bereits in AEM vorhanden sind. Verwenden Sie sie nicht mit anderen Anwendungen.

Für die richtige Verwendung müssen Sie den Archivinhalt direkt im Solr-Basisverzeichnis speichern. Bei Bereitstellungen mit mehreren Knoten muss der Inhalt direkt in den Stammordner der einzelnen Knoten gespeichert werden.

Empfohlene Solr-Konfigurationsdateien

[Datei laden](assets/recommended-conf.zip)

### AEM-Indizierungs-Tools {#aem-indexing-tools}

In AEM 6.1 sind auch zwei Indizierungs-Tools aus AEM 6.0 integriert, die Teil der Adobe Consulting Services Commons-Tools sind:

1. **Explain Query**: ein Tool, das Admins das Verständnis erleichtert, wie Abfragen ausgeführt werden.
1. **Oak Index Manager**, eine Web-Benutzeroberfläche zur Pflege vorhandener Indizes

Navigieren Sie auf dem AEM-Begrüßungsbildschirm zu **Tools > Vorgänge > Dashboard > Diagnose**, um auf diese Tools zuzugreifen.

Weitere Informationen zur Verwendung finden Sie in der [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

#### Erstellen von Eigenschaftsindizes über OSGi {#creating-property-indexes-via-osgi}

Das ACS Commons-Paket stellt auch OSGi-Konfigurationen bereit, die zum Erstellen von Eigenschaftenindizes verwendet werden können.

Sie können über die Web-Konsole darauf zugreifen, indem Sie nach „**Ensure Oak Property Index**“ suchen.

![chlimage_1-150](assets/chlimage_1-150.png)

### Fehlerbehebung bei Indizierungsproblemen {#troubleshooting-indexing-issues}

Es können Situationen auftreten, in denen die Ausführung von Abfragen lange dauert und die allgemeine Systemreaktionszeit langsam ist.

In diesem Abschnitt werden einige Empfehlungen gegeben, wie vorzugehen ist, um die Ursache dieser Probleme zu finden und diese zu beheben.

#### Vorbereiten von Debugging-Informationen für Analysen {#preparing-debugging-info-for-analysis}

Am einfachsten kommen Sie an die benötigten Informationen für die ausgeführte Abfrage mit dem [Tool „Abfrage erläutern“](/help/sites-administering/operations-dashboard.md#explain-query). Damit können Sie die genauen Informationen erfassen, die zum Debugging einer langsamen Abfrage erforderlich sind, ohne die Informationen auf Protokollebene einsehen zu müssen. Dies ist hilfreich, wenn Sie wissen, welche Abfrage debuggt werden soll.

Wenn dies aus irgendeinem Grund nicht möglich ist, können Sie die Indizierungsprotokolle in einer einzigen Datei sammeln und sie zur Fehlerbehebung für Ihr vorliegendes Problem verwenden.

#### Aktivieren der Protokollierung {#enable-logging}

Zum Aktivieren der Protokollierung müssen Sie die **DEBUG**-Protokollebene für die Kategorien aktivieren, die sich auf Oak-Indizierung und -Abfragen beziehen. Diese Kategorien sind: 

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

Die Kategorie **com.day.cq.search** ist nur anwendbar, wenn Sie das von AEM bereitgestellte Dienstprogramm QueryBuilder verwenden.

>[!NOTE]
>
>Es ist wichtig, dass die Protokolle nur für die Dauer der Abfrage, deren Fehler Sie beheben möchten, auf DEBUG festgelegt werden. Andernfalls werden mit der Zeit eine große Zahl von Ereignissen in den Protokollen generiert. Wechseln Sie aus diesem Grund nach der Erfassung der erforderlichen Protokolle für die oben genannten Kategorien zurück zur Protokollierungsebene INFO.

Sie können die Protokollierung aktivieren, indem Sie folgende Schritte ausführen:

1. Lassen Sie Ihren Browser auf `https://serveraddress:port/system/console/slinglog` verweisen.
1. Klicken Sie auf die Schaltfläche **Neue Protokollierung hinzufügen** unten in der Konsole.
1. Fügen Sie die oben genannten Kategorien in der neu erstellten Reihe hinzu. Verwenden Sie das **+**-Symbol, um einer Protokollierung mehr als eine Kategorie hinzuzufügen. 
1. Wählen Sie **DEBUG** aus der Dropdown-Liste **Protokollebene** aus.
1. Geben Sie als Ausgabedatei `logs/queryDebug.log` an. Dadurch werden alle DEBUG-Ereignisse in einer Protokolldatei zusammengefasst.
1. Führen Sie die Abfrage aus oder geben Sie die Seite aus, auf der die Abfrage verwendet wird, die Sie debuggen möchten.
1. Wenn Sie die Abfrage ausgeführt haben, wechseln Sie zurück zur Protokollierungskonsole und ändern Sie die Protokollierungsebene der neu erstellten Protokollierung in **INFO**.

#### Indexkonfiguration {#index-configuration}

Die Art und Weise, wie die Abfrage ausgewertet wird, wird stark durch die Indexkonfiguration beeinflusst. Es ist wichtig, die Indexkonfiguration analysieren zu lassen oder an den Support zu senden. Sie können die Konfiguration entweder als Inhaltspaket abrufen oder eine JSON-Ausgabedarstellung abrufen.

Die Indexkonfiguration wird normalerweise unter dem Knoten `/oak:index` in CRXDE gespeichert. Sie können die JSON-Version unter folgender Adresse abrufen:

`https://serveraddress:port/oak:index.tidy.-1.json`

Wenn der Index an einem anderen Speicherort konfiguriert ist, ändern Sie den Pfad entsprechend.

#### MBean-Ausgabe {#mbean-output}

Manchmal ist es hilfreich, die Ausgabe von indexbezogenen MBeans zum Debugging bereitzustellen. Gehen Sie dazu wie folgt vor:

1. Wechseln Sie zur JMX-Konsole unter:
   `https://serveraddress:port/system/console/jmx`

1. Suchen Sie nach folgenden MBeans:

   * Lucene-Indexstatistiken
   * CopyOnRead-Unterstützungsstatistiken
   * Oak-Abfragestatistiken
   * IndexStats

1. Klicken Sie auf die einzelnen MBeans, um Leistungsstatistiken zu erhalten. Erstellen Sie einen Screenshot oder notieren Sie sich die Daten, falls Sie diese an den Support weitergeben müssen.

Sie können auch die JSON-Version dieser Statistiken unter folgenden URLs abrufen:

* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`
* `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak/%2522LuceneIndex%2522.tidy.-1.json`

Sie können die konsolidierte JMX-Ausgabe auch über `https://serveraddress:port/system/sling/monitoring/mbeans/org/apache/jackrabbit/oak.tidy.3.json` bereitstellen. Hierdurch werden alle Oak-spezifischen MBean-Details im JSON-Format erfasst.

#### Weitere Details {#other-details}

Sie können weitere Details sammeln, um das Problem zu beheben, z. B.:

1. Die Oak-Version, auf der Ihre Instanz ausgeführt wird. Öffnen Sie dazu CRXDE. Die Version wird unten rechts auf der Begrüßungsseite anzeigt. Sie können die Version auch im `org.apache.jackrabbit.oak-core`-Bundle überprüfen.
1. Die Ausgabe des QueryBuilder-Debugger zu der problematischen Abfrage. Der Debugger kann unter `https://serveraddress:port/libs/cq/search/content/querydebug.html` aufgerufen werden.
