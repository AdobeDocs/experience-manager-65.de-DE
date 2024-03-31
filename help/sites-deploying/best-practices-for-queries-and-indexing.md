---
title: Best Practices für Abfragen und Indizierung
description: Dieser Artikel enthält Richtlinien zur Optimierung Ihrer Indizes und Abfragen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 6dfaa14d-5dcf-4e89-993a-8d476a36d668
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '4520'
ht-degree: 98%

---

# Best Practices für Abfragen und Indizierung{#best-practices-for-queries-and-indexing}

Neben dem Übergang zu Oak in AEM 6 wurden auch einige bedeutende Änderungen in Bezug auf die Verwaltung von Abfragen und Indizes vorgenommen. Unter Jackrabbit 2 wurden sämtlichee Inhalte standardmäßig indiziert und waren frei abrufbar. In Oak müssen Indizes manuell unter dem Knoten `oak:index` erstellt werden. Eine Abfrage kann zwar ohne Index ausgeführt werden, aber bei großen Datensätzen ist dieser Vorgang sehr langsam und kann sogar zu einem Abbruch führen.

In diesem Artikel wird beschrieben, wann Indizes zu erstellen sind und wann auf sie verzichtet werden kann. Außerdem finden Sie hierin Tricks zum Vermeiden von nicht benötigten Abfragen sowie Tipps zur Funktionsoptimierung von Indizes und Abfragen.

Darüber hinaus sollten Sie die [Oak-Dokumentation zum Erstellen von Abfragen und Indizes](/help/sites-deploying/queries-and-indexing.md) lesen. Außer den als neues Konzept in AEM 6 eingeführten Indizes gibt es syntaktische Unterschiede in Oak-Abfragen, die beim Migrieren von Code aus früheren AEM-Installationen berücksichtigt werden müssen.

## Wann Abfragen verwendet werden sollten {#when-to-use-queries}

### Repository- und Taxonomie-Design {#repository-and-taxonomy-design}

Bei der Erstellung der Taxonomie eines Repositorys müssen mehrere Faktoren berücksichtigt werden. Hierzu gehören u. a. die Zugriffssteuerung, Lokalisierung, Vererbung von Komponenten- und Seiteneigenschaften.

Beim Entwerfen einer Taxonomie, die diese Bedenken berücksichtigt, muss zudem auch die „Durchlauffähigkeit“ des Index-Designs beachtet werden. In diesem Zusammenhang ist die Durchlauffähigkeit die Fähigkeit einer Taxonomie, einen vorhersehbaren Zugriff auf Inhalte auf der Grundlage ihres Pfads zu ermöglichen. Dies ermöglicht ein leistungsfähigeres System, das einfacher unterhalten werden kann als ein System, für das eine Vielzahl von Abfragen ausgeführt werden muss.

Auch muss beim Entwerfen einer Taxonomie bedacht werden, ob eine Sortierung wichtig ist. Wenn auf eine explizite Sortierung verzichtet werden kann und eine große Anzahl gleichgeordneter Knoten erwartet wird, sind unsortierte Knotentypen wie `sling:Folder` oder `oak:Unstructured` vorzuziehen. Ist eine Sortierung erforderlich, sind `nt:unstructured` und `sling:OrderedFolder` besser geeignet.

### Abfragen in Komponenten {#queries-in-components}

Da Abfragen zu den stärker belastenden Vorgängen in einem AEM-System gehören können, empfiehlt es sich, diese in Ihren Komponenten zu vermeiden. Wenn beim Rendern einer Seite mehrere Abfragen gleichzeitig ausgeführt werden, kann dies die Leistung des Systems beeinträchtigen. Es gibt zwei Strategien, mit denen sich beim Rendering von Komponenten die Ausführung von Abfragen vermeiden lässt: **Durchlaufen von Knoten** und **Vorabrufen von Ergebnissen**.

#### Durchlaufen von Knoten {#traversing-nodes}

Wenn das Repository so konzipiert ist, dass eine vorherige Kenntnis des Speicherorts der erforderlichen Daten möglich ist, kann Code, der diese Daten aus den erforderlichen Pfaden abruft, bereitgestellt werden, ohne erst Abfragen ausführen zu müssen, um sie zu finden.

Ein Beispiel hierfür wäre das Rendern von Inhalten, die zu einer bestimmten Kategorie passen. Ein Ansatz wäre, den Inhalt mit einer Kategorieeigenschaft zu organisieren, die abgefragt werden kann, um eine Komponente mit Elementen einer Kategorie aufzufüllen.

Ein besserer Ansatz wäre, diesen Inhalt in einer Taxonomie nach Kategorie zu strukturieren, damit er manuell abgerufen werden kann.

Nahmen wir beispielsweise an, der Inhalt wird in einer Taxonomie gespeichert ist, die Folgendem ähnelt:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

In diesem Fall lässt sich der Knoten `/content/myUnstructuredContent/parentCategory/childCategory` einfach abrufen, und seine untergeordneten Elemente können analysiert und zum Rendern der Komponente verwendet werden.

Bei einem kleinen oder homogenen Ergebnissatz kann es auch schneller sein, das Repository zu durchlaufen und dabei die erforderlichen Knoten zu erfassen, statt eine Abfrage zu erstellen, die denselben Ergebnissatz zurückgibt. Generell gilt, dass Abfragen nach Möglichkeit vermieden werden sollten.

#### Vorabruf der Ergebnisse {#prefetching-results}

Mitunter lassen die Inhalte oder Anforderungen im Zusammenhang mit der Komponente nicht zu, dass Knoten zum Abrufen der erforderlichen Daten durchlaufen werden. In solchen Fällen müssen die erforderlichen Abfragen vor dem Rendern der Komponente ausgeführt werden, damit eine optimale Leistung für die Endbenutzenden sichergestellt werden kann.

Sofern die für die Komponente erforderlichen Ergebnisse zum Zeitpunkt der Erstellung ermittelt werden können und nicht von einer Änderung des Inhalts auszugehen ist, kann die Abfrage ausgeführt werden, wenn der Autor oder die Autorin Einstellungen im Dialogfeld anwendet.

Wenn sich die Daten oder Inhalte regelmäßig ändern, kann die Abfrage planmäßig oder über einen Listener für Aktualisierungen der zugrunde liegenden Daten ausgeführt werden. Anschließend können die Ergebnisse an einen freigegebenen Speicherort im Repository geschrieben werden. Alle Komponenten, die diese Daten benötigen, können dann die Werte aus diesem einzelnen Knoten beziehen, ohne eine Abfrage zur Laufzeit auszuführen.

## Abfrageoptimierung {#query-optimization}

Beim Ausführen einer indexfreien Abfrage werden Warnungen in Bezug auf das Durchlaufen von Knoten protokolliert. Wenn es sich um eine Abfrage handelt, die häufig ausgeführt wird, erstellen Sie einen Index. Um festzustellen, welcher Index von einer bestimmten Abfrage verwendet wird, wird das [Tool „Abfrage erläutern“](/help/sites-administering/operations-dashboard.md#explain-query) empfohlen. Zum Erhalt weiterer Informationen kann die DEBUG-Protokollierung für die entsprechenden Such-APIs aktiviert werden.

>[!NOTE]
>
>Nach dem Ändern einer Indexdefinition muss der Index neu erstellt (neu indiziert) werden. Je nach Größe des Index kann es einige Zeit dauern, bis dies erfolgt ist.

Beim Ausführen komplexer Abfragen kann es Fälle geben, in denen es effizienter ist, die Abfrage in mehrere kleinere Abfragen aufzuteilen und die Daten später mithilfe von Code zusammenzuführen. Für solche Fälle wird empfohlen, die Leistung der beiden Ansätze miteinander zu vergleichen, um die für den jeweiligen Anwendungsfall besser geeignete Option zu ermitteln.

In AEM können Abfragen mit einer der drei folgenden Methoden geschrieben werden:

* Verwenden von [QueryBuilder-APIs](/help/sites-developing/querybuilder-api.md) (empfohlen)
* Verwenden von XPath (empfohlen)
* Verwenden von SQL2

Zwar werden alle Abfragen vor der Ausführung in SQL2 konvertiert, jedoch ist der Mehraufwand durch die Abfragenkonvertierung nur minimal. Daher stehen beim Auswählen einer Abfragesprache in erster Linie die Lesbarkeit und der Komfort für das Entwicklungs-Team im Vordergrund.

>[!NOTE]
>
>Bei Verwendung von QueryBuilder wird die Ergebnisanzahl standardmäßig ermittelt, was in Oak langsamer ist als in früheren Versionen von Jackrabbit. Um dies zu kompensieren, können Sie den [Parameter guessTotal](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results) verwenden.

### Das Tool „Abfrage erläutern“ {#the-explain-query-tool}

Wie bei jeder anderen Abfragesprache besteht der erste Schritt zur Optimierung einer Abfrage darin, zu verstehen, wie sie ausgeführt wird. Dies ermöglicht das [Tool „Abfrage erläutern“](/help/sites-administering/operations-dashboard.md#explain-query), das zum Vorgangs-Dashboard gehört. Mithilfe dieses Tools kann eine Abfrage geladen und erläutert werden. Neben der Ausführungsdauer und den verwendeten Indizes wird eine Warnung angezeigt, falls die Abfrage bei einem großen Repository Probleme verursachen würde. Das Tool kann auch eine Liste langsamer und gängiger Abfragen laden, die dann erläutert und optimiert werden können.

### DEBUG-Protokollierung für Abfragen {#debug-logging-for-queries}

Um weitere Informationen darüber zu erhalten, wie Oak den zu verwendenden Index auswählt und wie das Abfragemodul eine Abfrage tatsächlich ausführt, kann für die folgenden Pakete eine **DEBUG**-Protokollierungskonfiguration hinzugefügt werden:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

Entfernen Sie diese Protokollfunktion, wenn Sie das Debugging Ihrer Abfrage abgeschlossen haben. Sie gibt tendenziell eine große Menge an Aktivität aus und kann schließlich Ihre Festplatte mit Protokolldateien füllen.

Weitere Informationen hierzu finden Sie in der [Dokumentation zur Protokollierung](/help/sites-deploying/configure-logging.md).

### Indexstatistiken {#index-statistics}

Lucene registriert ein JMX-Bean, das Details zum indizierten Inhalt enthält, einschließlich Größe und Anzahl der in jedem Index vorhandenen Dokumente.

Ein Zugriff ist über die JMX-Konsole unter `https://server:port/system/console/jmx` möglich.

Wenn Sie bei der JMX-Konsole angemeldet sind, suchen Sie nach **Lucene-Indexstatistiken**, um es zu finden. Weitere Indexstatistiken finden Sie im MBean **IndexStats**.

Um Abfragestatistiken zu erhalten, sehen Sie sich das MBean mit der Bezeichnung **Oak Query Statistics** an.

Um Ihre Indizes mit einem Tool wie [Luke](https://code.google.com/archive/p/luke/) durchzugehen, müssen Sie die Oak-Konsole aufrufen und den Index vom `NodeStore` in einem Dateisystemverzeichnis sichern. Anweisungen hierzu finden Sie in der [Lucene-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

Sie können die Indizes in Ihrem System auch im JSON-Format extrahieren. Dazu müssen Sie auf `https://server:port/oak:index.tidy.-1.json` zugreifen.

### Abfragelimits {#query-limits}

**Während der Entwicklung**

Legen Sie niedrige Schwellenwerte für `oak.queryLimitInMemory` (z. B. 10000) und oak. `queryLimitReads` (beispielsweise 5000) fest und optimieren Sie die ressourcenintensive Abfrage, wenn die UnsupportedOperationException „The query read more than x nodes …“ auftritt.

Dies verhindert ressourcenintensive Abfragen (d. h. nicht durch einen Index oder einen Index mit geringerer Abdeckung unterlegt).  Beispielsweise würde eine Abfrage, die 1 Million Knoten liest, zu einer Erhöhung der E/A führen und die Gesamtleistung der Anwendung negativ beeinflussen. Jede Abfrage, die aufgrund der obigen Beschränkungen fehlschlägt, sollte analysiert und optimiert werden.

#### **Nach der Bereitstellung** {#post-deployment}

* Überwachen Sie die Protokolle auf Abfragen, die eine hohe Anzahl durchlaufener Knoten oder einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * Optimieren Sie die Abfrage so, dass die Anzahl der durchlaufenen Knoten reduziert wird.

* Überwachen Sie die Protokolle auf Abfragen, die einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimieren Sie die Abfrage, um den Heap-Speicherverbrauch zu reduzieren.

Für die AEM-Versionen 6.0 bis 6.2 können Sie den Schwellenwert für das Durchlaufen von Knoten über JVM-Parameter im AEM-Startskript abstimmen, um zu verhindern, dass die Umgebung durch umfangreiche Abfragen überlastet wird.

Folgende Werte werden empfohlen:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3 sind die beiden oben genannten Parameter standardmäßig vorkonfiguriert und können über die OSGi QueryEngineSettings beibehalten werden.

Weitere Informationen finden Sie unter: [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Tipps zum Erstellen effizienter Indizes {#tips-for-creating-efficient-indexes}

### Sollte ich einen Index erstellen? {#should-i-create-an-index}

Die erste Frage, die beim Erstellen oder Optimieren von Indizes gestellt werden muss, bezieht sich darauf, ob Indizes für eine bestimmte Situation wirklich erforderlich sind.  Wenn Sie eine Abfrage nur einmal oder gelegentlich außerhalb der systembezogenen Stoßzeiten durch einen Batch-Prozess ausführen, kann es besser sein, auf die Indexerstellung komplett zu verzichten.

Wenn ein Index erstellt wurde, muss mit jeder Aktualisierung der indizierten Daten auch der Index aktualisiert werden. Da sich dies auf die Leistung des Systems auswirkt, sollten Indizes nur dann erstellt werden, wenn sie erforderlich sind.

Darüber hinaus sind Indizes nur dann nützlich, wenn die im Index enthaltenen Daten so einzigartig sind, dass sie diesen Vorgang rechtfertigen. Denken Sie in diesem Zusammenhang an einen Index in einem Buch und die Themen, die er abdeckt: Bei der Indizierung verschiedener Themen in einem Text gibt es gewöhnlich Hunderte oder Tausende von Einträgen, über die Sie schnell zu einzelnen Seiten und damit zur gesuchten Information springen können. Wenn dieser Index nur zwei oder drei Einträge hätte, von denen jeder auf mehrere hundert Seiten verweist, wäre der Index nicht nützlich.  Dasselbe Konzept gilt für Datenbankindizes. Sind nur einige eindeutige Werte vorhanden, ist der Index nicht nützlich. Dabei kann ein Index auch zu umfangreich werden und dadurch seine Nützlichkeit verlieren.  Informationen zu Indexstatistiken finden Sie weiter oben unter [Indexstatistiken](/help/sites-deploying/best-practices-for-queries-and-indexing.md#index-statistics).

### Lucene- oder Eigenschaftenindizes? {#lucene-or-property-indexes}

Lucene-Indizes wurden in Oak 1.0.9 eingeführt und bieten einige Optimierungsvarianten, die gegenüber den bei der Ersteinführung von AEM 6 enthaltenen Eigenschaftenindizes leistungsstärker sind. Bei der Entscheidung zwischen Lucene-Indizes oder Eigenschaftenindizes sollten die folgenden Aspekte berücksichtigt werden:

* Lucene-Indizes bieten deutlich mehr Funktionen als Eigenschaftenindizes. Beispielsweise kann ein Eigenschaftenindex nur eine einzelne Eigenschaft indizieren, während ein Lucene-Index eine Vielzahl von Eigenschaften umfassen kann. Weitere Informationen zu den in Lucene-Indizes verfügbaren Funktionen finden Sie in der [Dokumentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).
* Lucene-Indizes sind asynchron. Dies ist zwar mit einer erheblichen Leistungssteigerung verbunden, kann aber auch zu einer Verzögerung zwischen dem Schreiben von Daten in das Repository und dem Aktualisieren des Index führen. Wenn Abfragen zu 100 % genaue Ergebnisse zurückgeben müssen, ist ein Eigenschaftenindex erforderlich.
* Da Lucene-Indizes asynchron sind, können sie keine Eindeutigkeitseinschränkungen erzwingen. Sofern erforderlich, muss ein Eigenschaftenindex angelegt werden.

Im Allgemeinen wird empfohlen, Lucene-Indizes zu verwenden, es sei denn, es besteht eine zwingende Notwendigkeit, Eigenschaftenindizes zu verwenden, damit Sie von höherer Leistung und Flexibilität profitieren können.

### Solr-Indizierung {#solr-indexing}

AEM unterstützt zudem standardmäßig die Solr-Indizierung. Diese dient zur Unterstützung der Volltextsuche, kann aber auch für beliebige JCR-Abfragen verwendet werden. Solr sollte in Betracht gezogen werden, wenn die CPU-Kapazität der AEM-Instanzen nicht für die benötigte Anzahl an Anfragen in suchintensiven Bereitstellungen wie suchgesteuerten Websites mit einer hohen Anzahl gleichzeitiger Benutzerinnen und Benutzer ausreicht. Solr kann auch in einem Crawler-basierten Ansatz implementiert werden, um einige der hochmodernen Funktionen dieser Plattform nutzen zu können.

Solr-Indizes können so konfiguriert werden, dass sie eingebettet auf dem AEM-Server für Entwicklungsumgebungen ausgeführt werden, oder sie können auf eine Remote-Instanz abgeladen werden, um die Suchskalierbarkeit in der Produktions- und Staging-Umgebung zu verbessern. Zwar wird die Skalierbarkeit durch Abladen von Suchvorgängen optimiert, allerdings führt dies zu Latenzzeiten, und deshalb wird von einem solchen Vorgehen, sofern nicht erforderlich, abgeraten. Weitere Informationen zum Konfigurieren einer Solr-Integration und zum Erstellen von Solr-Indizes finden Sie in der [Dokumentation zu Oak-Abfragen und -Indizierung](/help/sites-deploying/queries-and-indexing.md#the-solr-index).

>[!NOTE]
>
>Der integrierte Solr-Suchansatz ermöglicht es, die Indizierung auf einen Solr-Server auszulagern. Wenn die hochmodernen Funktionen des Solr-Servers über einen Crawler-basierten Ansatz verwendet werden, sind zusätzliche Konfigurationsvorgänge erforderlich.

Der Nachteil dieses Ansatzes besteht darin, dass AEM-Abfragen zwar standardmäßig ACLs respektieren und so Ergebnisse verbergen, auf die Benutzende keinen Zugriff haben, jedoch die Externalisierung der Suche auf einen Solr-Server diese Funktion nicht unterstützt. Wenn Suchvorgänge auf eine solche Art und Weise externalisiert werden sollen, muss besonders darauf geachtet werden, dass den Benutzerinnen und Benutzern nur die für sie vorgesehenen Ergebnisse angezeigt werden.

Mögliche Anwendungsfälle, in denen dieser Ansatz sinnvoll sein kann, sind etwa Fälle, in denen Suchdaten aus mehreren Quellen aggregiert werden müssen. Angenommen, Sie verfügen über eine auf AEM gehostete Site und über eine zweite, auf einer Drittanbieterplattform gehostete Site.  Solr könnte so konfiguriert werden, dass der Inhalt beider Sites durchsucht und in einem aggregierten Index gespeichert wird. Dies würde Site-übergreifende Suchvorgänge ermöglichen.

### Design-Überlegungen {#design-considerations}

In der Oak-Dokumentation für Lucene-Indizes sind verschiedene Überlegungen aufgeführt, die beim Design von Indizes angestellt werden sollten:

* Verwendet die Abfrage verschiedene Pfadeinschränkungen, verwenden Sie `evaluatePathRestrictions`. Dadurch kann die Abfrage eine Teilmenge von Ergebnissen unter dem angegebenen Pfad zurückgeben und diese dann anhand der Abfrage filtern. Andernfalls sucht die Abfrage nach allen Ergebnissen im Repository, die den Abfrageparametern entsprechen, und filtert diese dann basierend auf dem Pfad.
* Wenn für die Abfrage die Sortierfunktion verwendet wird, ist eine explizite Eigenschaftendefinition erforderlich. Außerdem müssen Sie `ordered` auf `true` setzen. So können Ergebnisse im Index sortiert werden und ressourcenintensive Sortiervorgänge zum Zeitpunkt der Abfrageausführung eingespart werden.

* Nehmen Sie nur das in den Index auf, was erforderlich ist. Durch das Hinzufügen nicht benötigter Funktionen oder Eigenschaften wird zum einen der Index größer, zum anderen nimmt die Geschwindigkeit ab.
* In einem Eigenschaftenindex trägt ein eindeutiger Eigenschaftsname dazu bei, die Indexgröße zu reduzieren, aber für Lucene-Indizes sollten `nodeTypes` und `mixins` zum Erstellen kohäsiver Indizes verwendet werden. Die Abfrage nach einem bestimmten `nodeType` oder `mixin` ist leistungsstärker als eine `nt:base`-Abfrage. Definieren Sie bei diesem Ansatz `indexRules` für die fraglichen `nodeTypes`.

* Wenn Ihre Abfragen nur unter bestimmten Pfaden ausgeführt werden, erstellen Sie diese Indizes unter diesen Pfaden. Indizes müssen nicht im Stammverzeichnis des Repositorys gespeichert werden.
* Verwenden Sie einen einzigen Index, wenn alle zu indizierenden Eigenschaften miteinander zusammenhängen, damit Lucene so viele Eigenschaftseinschränkungen wie möglich nativ bewerten kann. Darüber hinaus wird selbst im Falle einer Zusammenführung nur ein Index für eine Abfrage genutzt.

### CopyOnRead {#copyonread}

Wenn `NodeStore` remote gespeichert wird, kann die Option `CopyOnRead` aktiviert werden. Diese Option bewirkt, dass der Remote-Index beim Lesen in das lokale Dateisystem geschrieben wird. Hierdurch kann sich die Leistung bei Abfragen, die häufig mit diesen Remote-Indizes ausgeführt werden, verbessern.

Dies kann in der OSGi-Konsole unter dem Dienst **LuceneIndexProvider** konfiguriert werden und ist standardmäßig ab Oak 1.0.13 aktiviert.

### Entfernen von Indizes {#removing-indexes}

Beim Entfernen eines Index wird immer empfohlen, den Index durch Einstellen der Eigenschaft `type` auf `disabled` vorübergehend zu deaktivieren und Tests durchzuführen, um vor dem Löschen eine ordnungsgemäße Funktionsweise der Anwendung sicherzustellen. Ein Index wird nicht aktualisiert, wenn er deaktiviert ist, sodass er möglicherweise nicht über den richtigen Inhalt verfügt, wenn er reaktiviert wird, und neu indiziert werden muss.

Nachdem Sie einen Eigenschaftenindex auf einer TarMK-Instanz entfernt haben, muss eine Komprimierung durchgeführt werden, um belegten Festplattenspeicher wieder freizugeben. Bei Lucene-Indizes befindet sich der tatsächliche Indexinhalt im BlobStore, sodass eine automatische Datenspeicherbereinigung erforderlich ist.

Beim Entfernen eines Index in einer MongoDB-Instanz verhält sich der Löschaufwand proportional zur Anzahl der Knoten im Index. Da das Löschen eines großen Index Probleme verursachen kann, wird empfohlen, den Index zu deaktivieren und ihn nur während eines Wartungsfensters mit einem Tool wie **oak-mongo.js** zu löschen. Beachten Sie, dass dieser Ansatz nicht für reguläre Knoteninhalte verwendet werden sollte, da er Dateninkonsistenzen verursachen kann.

>[!NOTE]
>
>Weitere Informationen zu oak-mongo.js finden Sie im [Abschnitt zu den Befehlszeilen-Tools](https://jackrabbit.apache.org/oak/docs/command_line.html) der Oak-Dokumentation.

### JCR-Abfrage-Schnellübersicht {#jcrquerycheatsheet}

Um die Erstellung effizienter JCR-Abfragen und Indexdefinitionen zu unterstützen, kann die [JCR-Abfrage-Schnellübersicht](assets/JCR_query_cheatsheet-v1.1.pdf) heruntergeladen und während der Entwicklung als Referenz verwendet werden. Sie enthält Beispielabfragen für QueryBuilder, XPath und SQL-2, die mehrere Szenarien abdecken, welche sich hinsichtlich der Abfrageleistung unterschiedlich verhalten. Sie enthält auch Empfehlungen zum Erstellen oder Anpassen von Oak-Indizes. Der Inhalt dieser Schnellübersicht gilt für AEM 6.5 und AEM as a Cloud Service.

## Neuindizierung {#re-indexing}

In diesem Abschnitt werden die **einzigen** akzeptablen Gründe für eine Neuindizierung von Oak-Indizes beschrieben.

Außer in den unten aufgeführten Fällen werden durch eine Neuindizierung von Oak-Indizes **keine** Änderungen am Verhalten ausgelöst bzw. keine Probleme behoben; stattdessen wird die AEM-Last erhöht.

Eine Neuindizierung von Oak-Indizes muss vermieden werden, sofern nicht einer der in den folgenden Tabellen genannten Gründe vorliegt.

>[!NOTE]
>
>Bevor Sie anhand der nachstehenden Tabellen ermitteln, ob eine Neuindizierung sinnvoll ist, stellen Sie **immer ** Folgendes sicher:
>
>* Die Abfrage ist korrekt.
>* Die Abfrage wird in den erwarteten Index aufgelöst (mithilfe von [Abfrage erläutern](/help/sites-administering/operations-dashboard.md#diagnosis-tools)).
>* Der Indizierungsprozess ist abgeschlossen.
>

### Konfigurationsänderungen von Oak-Indizes {#oak-index-configuration-changes}

Die Neuindizierung von Oak-Indizes ist nur dann sinnvoll, wenn sich die Konfiguration für einen Oak-Index geändert hat.

*Vor einer Neuindizierung sollten die damit verbundenen Auswirkungen auf die AEM-Gesamtleistung angemessen berücksichtigt werden. Darüber hinaus sollte die Neuindizierung in Zeiträumen geringer Aktivität oder während Wartungsfenstern stattfinden.*

Im Folgenden finden Sie Details zu möglichen Problemen sowie entsprechende Lösungen:

* [Definitionsänderung des Eigenschaftenindex](#property-index-definition-change)
* [Definitionsänderung des Lucene-Index](#lucene-index-definition-change)

#### Definitionsänderung des Eigenschaftenindex {#property-index-definition-change}

* Gilt für folgende Fälle:

   * Alle Oak-Versionen
   * Nur [Eigenschaftenindizes](https://jackrabbit.apache.org/oak/docs/query/property-index.html)

* Symptome:

   * Knoten, die bereits vor der Definitionsaktualisierung des Eigenschaftenindex vorhanden waren, fehlen in den Ergebnissen.

* So kann dies überprüft werden:

   * Bestimmen Sie, ob die fehlenden Knoten vor der Bereitstellung der aktualisierten Indexdefinition erstellt/geändert wurden.
   * Überprüfen Sie die Eigenschaften `jcr:created` oder `jcr:lastModified` aller fehlenden Knoten im Hinblick auf die Änderungszeit des Index.

* Beheben des Problems:

   * [Indizieren](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-re-index) Sie den Lucene-Index neu.
   * Alternativ können Sie einen Schreibvorgang ohne Auswirkungen für den fehlenden Knoten durchführen.

      * Erfordert manuelle Änderungen oder benutzerdefinierten Code
      * Erfordert, dass der Satz fehlender Knoten bekannt ist.
      * Erfordert das Ändern einer beliebigen Eigenschaft auf dem Knoten

#### Definitionsänderung des Lucene-Index {#lucene-index-definition-change}

* Gilt für folgende Fälle:

   * Alle Oak-Versionen
   * Ausschließlich [Lucene-Indizes](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptome:

   * Der Lucene-Index enthält keine erwarteten Ergebnisse.
   * Die Abfrageergebnisse spiegeln nicht das erwartete Verhalten der Indexdefinition wider.
   * Der Abfrageplan berichtet nicht die erwartete, auf der Indexdefinition basierende Ausgabe.

* So kann dies überprüft werden:

   * Überprüfen Sie, ob die Indexdefinition mit den Lucene-Indexstatistiken JMX MBean (LuceneIndex), Methode `diffStoredIndexDefinition`, geändert wurde.

* Beheben des Problems:

   * Oak-Versionen vor 1.6:

      * [Indizieren](#how-to-re-index) Sie den Lucene-Index neu.

   * Oak-Versionen ab 1.6:

      * Wenn sich Änderungen nicht auf den vorhandenen Inhalt auswirken, ist lediglich eine Aktualisierung erforderlich.

         * [Aktualisieren](https://jackrabbit.apache.org/oak/docs/query/lucene.html#stored-index-definition) Sie den Lucene-Index, indem Sie [oak:queryIndexDefinition] @refresh=true einstellen.

      * Ansonsten sollte eine [Neuindizierung](#how-to-re-index) des Lucene-Index vorgenommen werden.

         * Hinweis: Der Indexstatus der letzten erfolgreichen Neuindizierung (oder Erstindizierung) wird so lange verwendet, bis eine Neuindizierung ausgelöst wird.

### Fehler- und Ausnahmesituationen {#erring-and-exceptional-situations}

In der folgenden Tabelle werden die einzigen akzeptablen Fehler- und Ausnahmesituationen beschrieben, in denen das Problem durch Neuindizieren der Oak-Indizes behoben wird.

Wenn in AEM ein Problem auftritt, das nicht den nachfolgend beschriebenen Kriterien entspricht, indizieren Sie Indizes **nicht** neu, da das Problem hierdurch nicht gelöst wird.

Im Folgenden finden Sie Details zu möglichen Problemen sowie entsprechende Lösungen:

* [Fehlende Lucene-Index-Binärdateien](#lucene-index-binary-is-missing)
* [Beschädigte Lucene-Index-Binärdateien](#lucene-index-binary-is-corrupt)

#### Fehlende Lucene-Index-Binärdateien {#lucene-index-binary-is-missing}

* Gilt für folgende Fälle:

   * Alle Oak-Versionen
   * Ausschließlich [Lucene-Indizes](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptome:

   * Der Lucene-Index enthält keine erwarteten Ergebnisse.

* So kann dies überprüft werden:

   * Die Fehlerprotokolldatei enthält eine Ausnahme, die besagt, dass eine Binärdatei des Lucene-Index fehlt.

* Beheben des Problems:

   * Durchführen einer Repository-Durchlauf-Prüfung; Beispiel:

     [http://localhost:4502/system/console/repositorycheck](http://localhost:4502/system/console/repositorycheck)

     Durch das Durchlaufen des Repositorys wird bestimmt, ob andere Binärdateien (außer Lucene-Dateien) fehlen.

   * Wenn andere Binärdateien als Lucene-Indizes fehlen, stellen Sie diese anhand einer Sicherung wieder her.
   * [Indizieren](#how-to-re-index) Sie andernfalls *alle* Lucene-Indizes neu.
   * Hinweis:

     Dieser Zustand ist ein Anzeichen für einen falsch konfigurierten Datenspeicher, was dazu führen kann, dass beliebige Binärdateien (z. B. Asset-Binärdateien) verloren gehen.

     Stellen Sie in diesem Fall die letzte einwandfreie Version des Repositorys wieder her, um alle fehlenden Binärdateien wiederzugewinnen.

#### Beschädigte Lucene-Index-Binärdateien {#lucene-index-binary-is-corrupt}

* Gilt für folgende Fälle:

   * Alle Oak-Versionen
   * Ausschließlich [Lucene-Indizes](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptome:

   * Der Lucene-Index enthält keine erwarteten Ergebnisse.

* So kann dies überprüft werden:

   * `AsyncIndexUpdate` (alle fünf Sekunden) schlägt mit folgender Ausnahme im Fehlerprotokoll fehl:

     `...a Lucene index file is corrupt...`

* Beheben des Problems:

   * Entfernen Sie die lokale Kopie des Lucene-Index.

      1. Stoppen Sie AEM.
      1. Löschen Sie die lokale Kopie des Lucene-Index unter `crx-quickstart/repository/index`.
      1. Starten Sie AEM neu.

   * Wenn das Problem hierdurch nicht behoben wird und die `AsyncIndexUpdate`-Ausnahmen bestehen bleiben, gehen Sie wie folgt vor:

      1. [Indizieren](#how-to-re-index) Sie den fehlerhaften Index neu.
      1. Öffnen Sie zudem ein Ticket beim [Adobe-Support](https://helpx.adobe.com/de/support.html).

### Neuindizieren {#how-to-re-index}

>[!NOTE]
>
>In AEM 6.5 ist [oak-run.jar die EINZIGE unterstützte Methode](/help/sites-deploying/indexing-via-the-oak-run-jar.md#reindexingapproachdecisiontree) für die Neuindizierung von MongoMK- oder RDBMK-Repositorys.

#### Neuindizieren von Eigenschaftenindizes {#re-indexing-property-indexes}

* Verwenden Sie [oak-run.jar](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing), um den Eigenschaftenindex neu zu indizieren
* Stellen Sie im Eigenschaftenindex die Eigenschaft „reindex-async“ auf „true“ ein.

   * `[oak:queryIndexDefinition]@reindex-async=true`

* Indizieren Sie den Eigenschaftenindex asynchron mithilfe der Web-Konsole über das MBean **PropertyIndexAsyncReindex**;

  Beispiel,

  [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex)

#### Neuindizieren von Lucene-Eigenschaftsindizes {#re-indexing-lucene-property-indexes}

* Verwenden Sie [oak-run.jar zum Neuindizieren](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) des Lucene-Eigenschaftsindex.
* Stellen Sie im Lucene-Eigenschaftenindex die Eigenschaft „async-reindex“ auf „true“ ein.

   * `[oak:queryIndexDefinition]@reindex-async=true`

>[!NOTE]
>
>Im vorherigen Abschnitt wurden die Anleitungen zur Neuindizierung von Oak aus der [Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) im AEM-Kontext zusammengefasst und formuliert.

### Textvorextraktion von Binärdateien {#text-pre-extraction-of-binaries}

Bei der Textvorextraktion wird Text aus Binärdateien extrahiert und verarbeitet, direkt aus dem Datenspeicher über einen isolierten Prozess, und der extrahierte Text wird dann direkt zu nachfolgenden Neuindizierungen von Oak-Indizes weitergeleitet.

* Die Oak-Textvorextraktion wird für die Neuindizierung/Indizierung von Lucene-Indizes in Repositorys mit großen Dateimengen (Binärdateien) empfohlen, die extrahierbaren Text enthalten (z. B. PDF, Word Docs, PPTs und TXT), der für die Volltextsuche über bereitgestellte Oak-Indizes qualifiziert ist. Beispiel: `/oak:index/damAssetLucene`.
* Von einer Textvorextraktion profitiert lediglich die Neuindizierung/Indizierung von Lucene-Indizes, aber NICHT von Oak-Eigenschaftenindizes, da Eigenschaftenindizes keinen Text aus Binärdateien extrahieren.
* Die Textvorextraktion wirkt sich enorm positiv auf die Volltext-Neuindizierung von textlastigen Binärdateien (PDF, DOC und TXT) aus, während ein Repository von Bildern hier nicht dieselbe Effizienz bietet, da Bilder keinen extrahierbaren Text enthalten.
* Bei der Textvorextraktion wird der mit der Volltextsuche in Zusammenhang stehende Text überaus effizient extrahiert und gegenüber dem Oak-Prozess zur Neuindizierung/Indizierung auf eine Art und Weise offengelegt, die eine extrem effiziente Nutzung ermöglicht.

#### Wann KANN die Textvorextraktion verwendet werden? {#when-can-text-pre-extraction-be-used}

Neuindizieren eines **vorhandenen** Lucene-Index mit aktivierter Binärextraktion

* Neuindizierung **aller** infrage kommenden Inhalte im Repository (wenn die Binärdateien für die Volltext-Extraktion zahlreich oder komplex sind, bedeutet dies für AEM einen höheren Rechenaufwand). Bei der Textvorextraktion werden die „rechenintensiven Arbeiten“ für die Textextraktion in einen isolierten Prozess mit direktem Zugriff auf den AEM-Datenspeicher ausgelagert, wodurch Mehraufwand und Ressourcenkonflikte in AEM vermieden werden.

Unterstützung bei der Bereitstellung eines **neuen** Lucene-Index in AEM mit aktivierter Binärdateiextraktion

* Wenn ein neuer Index (mit aktivierter Binärdateiextraktion) in AEM bereitgestellt wird, indiziert Oak automatisch sämtliche infrage kommenden Inhalte bei der nächsten asynchronen Volltextindizierung. Aus den gleichen Gründen, wie oben unter „Neuindizieren“ beschrieben, kann dies zu einer AEM-Überbelastung führen.

#### Wann kann die Textvorextraktion NICHT verwendet werden? {#when-can-text-pre-extraction-not-be-used}

Die Textvorextraktion kann nicht für neue Inhalte verwendet werden, die zum Repository hinzugefügt werden, dies ist aber auch nicht notwendig.

Neue Inhalte, die dem Repository hinzugefügt werden, werden nämlich automatisch und schrittweise durch die asynchrone Volltextindizierung indiziert (standardmäßig alle 5 Sekunden).

Bei normalem AEM-Betrieb, etwa beim Hochladen von Assets über die Web-Benutzeroberfläche oder bei der programmgesteuerten Aufnahme von Assets, führt AEM eine automatische und schrittweise Volltextindizierung des neuen Binärinhalts durch. Da die Datenmenge inkrementell und relativ klein ist (in etwa die Datenmenge, die in 5 Sekunden in das Repository persistiert werden kann), kann AEM während der Indizierung eine Volltextextraktion aus den Binärdateien durchführen, ohne die Gesamtleistung des Systems zu beeinträchtigen.

#### Voraussetzungen für die Verwendung der Textvorextraktion {#prerequisites-to-using-text-pre-extraction}

* Sie müssen einen Lucene-Index neu indizieren, der eine Volltext-Binärextraktion durchführt, oder einen neuen Index bereitstellen, der einen Volltextindex für die Binärdateien des vorhandenen Inhalts erstellt.
* Die Inhalte (Binärdateien) für die Textextraktion müssen sich im Repository befinden.
* Es muss ein Wartungsfenster vorhanden sein, um die CSV-Datei zu generieren und die abschließende Neuindizierung durchzuführen.
* Die folgenden Oak-Versionen müssen verwendet werden: 1.0.18 oder höher, 1.2.3 oder höher.
* Die folgende [oak-run.jar](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)-Version muss verwendet werden: 1.7.4 oder höher.
* Es muss ein Ordner oder eine Freigabe im Dateisystem vorhanden sein, um extrahierten Text zu speichern, der über die indizierende(n) AEM-Instanz(en) zugänglich ist.

   * Für die OSGi-Konfiguration zur Textvorextraktion ist ein Dateisystempfad zu den extrahierten Textdateien erforderlich. Sie müssen also direkt von der AEM-Instanz (lokale Festplatte oder Bereitstellung der Dateifreigabe) aus zugänglich sein.

#### Durchführen der Textvorextraktion {#how-to-perform-text-pre-extraction}

>[!NOTE]
>
>***Die unten beschriebenen oak-run.jar-Befehle finden Sie vollständig aufgeführt unter [https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html)***.
>
>Die obige Grafik und die darunter stehenden Schritte erläutern und ergänzen die in der Apache Oak-Dokumentation dargelegten technischen Schritte zur Textvorextraktion.

![Prozessablauf der Textvorextraktion](assets/chlimage_1-139.png)

**Generieren einer Inhaltsliste für die Vorextraktion**

*Führen Sie Schritt 1 (a-b) während eines Wartungsfensters oder in einem Zeitraum geringer Aktivität aus, da während dieses Vorgangs der Knotenspeicher durchlaufen wird, was eine erhebliche Belastung des Systems verursachen kann.*

1a. Führen Sie `oak-run.jar --generate` aus, um eine Liste der Knoten mit vorextrahiertem Text zu erstellen.

1b. Die Liste der Knoten (1a) wird im Dateisystem als CSV-Datei gespeichert

Der gesamte Knotenspeicher wird jedes Mal durchlaufen (wie in den Pfaden des oak-run-Befehls angegeben), wenn `--generate` ausgeführt und eine **neue** CSV-Datei erstellt wird. Die CSV-Datei wird zwischen den diskreten Ausführungen des Textextraktionsprozesses (Schritte 1–2) **nicht** wiederverwendet.

**Vorextrahieren von Text für das Dateisystem**

*Schritt 2 (a-c) kann während des normalen Betriebs von AEM ausgeführt werden, da lediglich eine Interaktion mit dem Datenspeicher stattfindet.*

2a. Führen Sie `oak-run.jar --tika` aus, um Text für die in der unter (1b) generierten CSV-Datei genannten Binärknoten vorzuextrahieren.

2b. Der in (2a) initiierte Prozess greift direkt auf die Binärknoten zu, die in der CSV-Datei im Datenspeicher definiert sind, und extrahiert Text.

2c. Der extrahierte Text wird im Dateisystem in einem Format gespeichert, das vom Oak-Neuindizierungsprozess (3a) aufgenommen werden kann.

Vorextrahierter Text ist in der CSV-Datei durch einen binären Fingerabdruck gekennzeichnet. Wenn die Binärdatei identisch ist, kann derselbe vorextrahierte Text über mehrere AEM-Instanzen hinweg verwendet werden. Da AEM Publish normalerweise ein Teil von AEM Author ist, kann mit dem aus AEM Author vorextrahierten Text häufig auch AEM Publish neu indiziert werden (sofern AEM Publish über Dateisystemzugriff auf die extrahierten Textdateien verfügt).

Vorextrahierter Text kann im Laufe der Zeit schrittweise hinzugefügt werden. Bei der Textvorextraktion wird die Extraktion für zuvor extrahierte Binärdateien übersprungen. Daher hat es sich bewährt, vorextrahierten Text für den Fall aufzubewahren, dass zukünftig eine Neuindizierung erforderlich sein sollte (vorausgesetzt, der extrahierte Inhalt ist nicht unnötig groß. Ziehen Sie sonst eine zwischenzeitliche Zip-Komprimierung des Inhalts in Betracht, da Text gut komprimiert werden kann.)

**Neuindizieren von Oak-Indizes mit Beziehen von Volltext aus extrahierten Textdateien**

*Führen Sie die Neuindizierung (Schritte 3a-b) während eines Wartungsfensters oder in einem Zeitraum geringer Aktivität durch, da während dieses Vorgangs der Knotenspeicher durchlaufen wird, was zu einer erheblichen Belastung des Systems führen kann.*

3a. Die [Neuindizierung](#how-to-re-index) von Lucene-Indizes wird in AEM aufgerufen.

3b. Die Apache Jackrabbit Oak DataStore PreExtractedTextProvider-OSGi-Konfiguration (zum Verweisen auf den extrahierten Text über einen Dateisystempfad) weist Oak an, Volltext aus den extrahierten Dateien zu beziehen, und vermeidet ein direktes Auffinden und Verarbeiten der im Repository gespeicherten Daten.
