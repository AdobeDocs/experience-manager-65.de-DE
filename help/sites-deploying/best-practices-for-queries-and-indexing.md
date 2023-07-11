---
title: Best Practices für Abfragen und Indizierung
description: Dieser Artikel enthält Richtlinien zur Optimierung Ihrer Indizes und Abfragen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 6dfaa14d-5dcf-4e89-993a-8d476a36d668
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '4614'
ht-degree: 21%

---

# Best Practices für Abfragen und Indizierung{#best-practices-for-queries-and-indexing}

Neben dem Übergang zu Oak in AEM 6 wurden auch einige bedeutende Änderungen in Bezug auf die Verwaltung von Abfragen und Indizes vorgenommen. Unter Jackrabbit 2 wurden alle Inhalte standardmäßig indiziert und konnten frei abgefragt werden. In Oak müssen Indizes manuell unter dem Knoten `oak:index` erstellt werden. Eine Abfrage kann ohne Index ausgeführt werden. Bei großen Datensätzen wird sie jedoch langsam ausgeführt oder sogar abgebrochen.

In diesem Artikel wird beschrieben, wann Indizes erstellt werden müssen und wann diese nicht benötigt werden. Außerdem werden Tricks zum Vermeiden von unnötigen Abfragen sowie Tipps zur Optimierung Ihrer Indizes und Abfragen für eine möglichst optimale Leistung beschrieben.

Lesen Sie auch die [Oak-Dokumentation zum Schreiben von Abfragen und Indizes](/help/sites-deploying/queries-and-indexing.md). Außer den als neues Konzept in AEM 6 eingeführten Indizes gibt es syntaktische Unterschiede in Oak-Abfragen, die beim Migrieren von Code aus früheren AEM-Installationen berücksichtigt werden müssen.

## Wann Abfragen verwendet werden sollten {#when-to-use-queries}

### Repository- und Taxonomiedesign {#repository-and-taxonomy-design}

Bei der Erstellung der Taxonomie eines Repositorys müssen mehrere Faktoren berücksichtigt werden. Dazu gehören unter anderem Zugriffssteuerungen, Lokalisierung, Komponenten und die Vererbung von Seiteneigenschaften.

Beim Entwerfen einer Taxonomie, die diese Bedenken berücksichtigt, muss zudem auch die „Durchlauffähigkeit“ des Index-Designs beachtet werden. In diesem Zusammenhang ist die Durchlaufbarkeit die Fähigkeit einer Taxonomie, die den vorhersehbaren Zugriff auf Inhalte auf Grundlage ihres Pfads ermöglicht. Dies ermöglicht ein leistungsfähigeres System, das leichter zu verwalten ist als ein System, das viele Abfragen erfordert.

Bei der Erstellung einer Taxonomie ist es wichtig zu überlegen, ob die Reihenfolge wichtig ist. In Fällen, in denen keine explizite Reihenfolge erforderlich ist und viele Geschwisterknoten erwartet werden, wird empfohlen, einen ungeordneten Knotentyp zu verwenden, z. B. `sling:Folder` oder `oak:Unstructured`. In den Fällen, in denen eine Bestellung erforderlich ist, `nt:unstructured`und `sling:OrderedFolder` besser geeignet sind.

### Abfragen in Komponenten {#queries-in-components}

Da Abfragen eine der steuerpflichtigeren Vorgänge in einem AEM sein können, ist es empfehlenswert, sie in Ihren Komponenten zu vermeiden. Die Ausführung mehrerer Abfragen bei jedem Rendern einer Seite kann häufig die Leistung des Systems beeinträchtigen. Es gibt zwei Strategien, mit denen sich beim Rendering von Komponenten die Ausführung von Abfragen vermeiden lässt: **Durchlaufen von Knoten** und **Vorabrufen von Ergebnissen**.

#### Durchlaufen von Knoten {#traversing-nodes}

Wenn das Repository so konzipiert ist, dass eine vorherige Kenntnis des Speicherorts der erforderlichen Daten möglich ist, kann Code, der diese Daten aus den erforderlichen Pfaden abruft, bereitgestellt werden, ohne Abfragen ausführen zu müssen, um sie zu finden.

Ein Beispiel hierfür wäre das Rendern von Inhalten, die zu einer bestimmten Kategorie passen. Ein Ansatz wäre, den Inhalt mit einer Kategorieeigenschaft zu organisieren, die abgefragt werden kann, um eine Komponente zu füllen, die Elemente in einer Kategorie anzeigt.

Ein besserer Ansatz wäre, diesen Inhalt in einer Taxonomie nach Kategorie zu strukturieren, damit er manuell abgerufen werden kann.

Wenn der Inhalt beispielsweise in einer Taxonomie gespeichert ist, die Folgendem ähnelt:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

Die `/content/myUnstructuredContent/parentCategory/childCategory` -Knoten können einfach abgerufen werden, seine untergeordneten Elemente können analysiert und zum Rendern der Komponente verwendet werden.

Wenn Sie es mit einem kleinen oder homogenen Ergebnissatz zu tun haben, kann es auch schneller sein, das Repository zu durchlaufen und die erforderlichen Knoten zu sammeln, anstatt eine Abfrage zu erstellen, um denselben Ergebnissatz zurückzugeben. Generell sollten Abfragen vermieden werden, soweit dies möglich ist.

#### Vorabruf der Ergebnisse {#prefetching-results}

Manchmal lässt der Inhalt oder die Anforderungen um die Komponente die Verwendung von Knotendurchlauf zum Abrufen der erforderlichen Daten nicht zu. In diesen Fällen müssen die erforderlichen Abfragen vor dem Rendern der Komponente ausgeführt werden, damit eine optimale Leistung für den Endbenutzer gewährleistet ist.

Wenn die für die Komponente erforderlichen Ergebnisse zum Zeitpunkt der Erstellung berechnet werden können und es nicht zu erwarten ist, dass sich der Inhalt ändert, kann die Abfrage ausgeführt werden, wenn der Autor die Einstellungen im Dialogfeld anwendet.

Wenn sich die Daten oder Inhalte regelmäßig ändern, kann die Abfrage planmäßig oder über einen Listener für Aktualisierungen der zugrunde liegenden Daten ausgeführt werden. Anschließend können die Ergebnisse an einen freigegebenen Speicherort im Repository geschrieben werden. Alle Komponenten, die diese Daten benötigen, können dann die Werte aus diesem einzelnen Knoten beziehen, ohne eine Abfrage zur Laufzeit auszuführen.

## Abfrageoptimierung {#query-optimization}

Wenn eine Abfrage ausgeführt wird, bei der kein Index verwendet wird, werden Warnungen bezüglich der Knotendurchlauf protokolliert. Wenn es sich um eine Abfrage handelt, die häufig ausgeführt wird, erstellen Sie einen Index. Um festzustellen, welcher Index von einer bestimmten Abfrage verwendet wird, wird das [Tool „Abfrage erläutern“](/help/sites-administering/operations-dashboard.md#explain-query) empfohlen. Zum Erhalt weiterer Informationen kann die DEBUG-Protokollierung für die entsprechenden Such-APIs aktiviert werden.

>[!NOTE]
>
>Nach dem Ändern einer Indexdefinition muss der Index neu erstellt (neu indiziert) werden. Je nach Größe des Index kann es einige Zeit dauern, bis dies abgeschlossen ist.

Bei der Ausführung komplexer Abfragen kann es vorkommen, dass die Aufschlüsselung der Abfrage in mehrere kleinere Abfragen und die Verknüpfung der Daten über den Code nach der Tatsache leistungsfähiger ist. Für diese Fälle wird empfohlen, die Leistung der beiden Ansätze zu vergleichen, um festzustellen, welche Option für den betreffenden Anwendungsfall besser wäre.

AEM ermöglicht das Schreiben von Abfragen auf eine von drei Arten:

* Verwenden von [QueryBuilder-APIs](/help/sites-developing/querybuilder-api.md) (empfohlen)
* Verwenden von XPath (empfohlen)
* Verwenden von SQL2

Während alle Abfragen vor der Ausführung in SQL2 konvertiert werden, ist der Aufwand für die Abfragekonvertierung minimal und daher die größte Sorge bei der Auswahl einer Abfragesprache die Lesbarkeit und Komfort des Entwicklungsteams.

>[!NOTE]
>
>Bei Verwendung von QueryBuilder wird die Ergebnisanzahl standardmäßig ermittelt, die in Oak im Vergleich zu früheren Jackrabbit-Versionen langsamer ist. Um dies zu kompensieren, können Sie die [guessTotal-Parameter](/help/sites-developing/querybuilder-api.md#using-p-guesstotal-to-return-the-results).

### Das Tool „Abfrage erläutern“ {#the-explain-query-tool}

Wie bei jeder Abfragesprache besteht der erste Schritt zur Optimierung einer Abfrage darin, zu verstehen, wie sie ausgeführt wird. Dies ermöglicht das [Tool „Abfrage erläutern“](/help/sites-administering/operations-dashboard.md#explain-query), das zum Vorgangs-Dashboard gehört. Mithilfe dieses Tools kann eine Abfrage geladen und erläutert werden. Eine Warnung wird angezeigt, wenn die Abfrage Probleme mit einem großen Repository und einer langen Laufzeit sowie mit den verwendeten Indizes verursacht. Das Tool kann auch eine Liste langsamer und beliebter Abfragen laden, die dann erklärt und optimiert werden können.

### DEBUG-Protokollierung für Abfragen {#debug-logging-for-queries}

Um zusätzliche Informationen darüber zu erhalten, wie Oak auswählt, welchen Index verwendet werden soll und wie die Abfrage-Engine tatsächlich eine Abfrage ausführt, wird ein **DEBUG** Die Protokollierungskonfiguration kann für die folgenden Pakete hinzugefügt werden:

* org.apache.jackrabbit.oak.plugins.index
* org.apache.jackrabbit.oak.query
* com.day.cq.search

Entfernen Sie diese Protokollfunktion, wenn Sie das Debugging Ihrer Abfrage abgeschlossen haben. Es gibt tendenziell eine große Menge an Aktivität aus und kann schließlich Ihre Festplatte mit Protokolldateien füllen.

Weitere Informationen hierzu finden Sie im Abschnitt [Dokumentation zur Protokollierung](/help/sites-deploying/configure-logging.md).

### Indexstatistiken {#index-statistics}

Lucene registriert ein JMX-Bean, das Details zu indizierten Inhalten einschließlich der Größe und Anzahl der in den einzelnen Indizes vorhandenen Dokumente bereitstellt.

Ein Zugriff ist über die JMX-Konsole unter `https://server:port/system/console/jmx` möglich.

Nachdem Sie in der JMX-Konsole angemeldet sind, suchen Sie nach **Lucene-Indexstatistiken** um sie zu finden. Weitere Indexstatistiken finden Sie im **IndexStats** MBean.

Sehen Sie sich die MBean mit dem Namen **Oak Query Statistics**.

Wenn Sie mit einem Tool wie [Luke](https://code.google.com/archive/p/luke/)müssen Sie die Oak-Konsole verwenden, um den Index aus der `NodeStore` in ein Dateisystemverzeichnis. Anweisungen hierzu finden Sie im Abschnitt [Lucene-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

Sie können die Indizes in Ihrem System auch im JSON-Format extrahieren. Hierzu müssen Sie auf Folgendes zugreifen: `https://server:port/oak:index.tidy.-1.json`

### Abfragelimits {#query-limits}

**Während der Entwicklung**

Setzen Sie niedrige Schwellenwerte für `oak.queryLimitInMemory` (z. B. 10000) und Oak. `queryLimitReads` (z. B. 5000) und optimieren Sie die teure Abfrage, wenn auf eine UnsupportedOperationException -Ausnahme mit der Meldung &quot;Die Abfrage liest mehr als x Knoten...&quot;geklickt wird.

Auf diese Weise lassen sich ressourcenintensive Abfragen vermeiden (d. h. nicht durch einen Index unterlegt oder durch einen Index mit geringerer Abdeckung unterlegt). Beispielsweise würde eine Abfrage, die 1 Million Knoten liest, zu einer Erhöhung der E/A führen und die Gesamtleistung der Anwendung negativ beeinflussen. Jede Abfrage, die aufgrund der obigen Beschränkungen fehlschlägt, sollte analysiert und optimiert werden.

#### **Nach der Bereitstellung** {#post-deployment}

* Überwachen Sie die Protokolle auf Abfragen, die eine hohe Anzahl durchlaufener Knoten oder einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped.`
   * Optimieren Sie die Abfrage, um die Anzahl der durchsuchten Knoten zu reduzieren.

* Überwachen Sie die Protokolle auf Abfragen, die einen hohen Heap-Speicherverbrauch auslösen:

   * `*WARN* ... java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory. To avoid running out of memory, processing was stopped`
   * Optimieren Sie die Abfrage, um den Heap-Speicherverbrauch zu reduzieren.

Für die AEM-Versionen 6.0 bis 6.2 können Sie den Schwellenwert für das Durchlaufen von Knoten über JVM-Parameter im AEM-Startskript abstimmen, um zu verhindern, dass die Umgebung durch umfangreiche Abfragen überlastet wird.

Folgende Werte werden empfohlen:

* `-Doak.queryLimitInMemory=500000`
* `-Doak.queryLimitReads=100000`

In AEM 6.3 sind die beiden oben genannten Parameter vorkonfiguriert OOTB und können über die OSGi QueryEngineSettings beibehalten werden.

Weitere Informationen finden Sie unter: [https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Slow_Queries_and_Read_Limits)

## Tipps zum Erstellen effizienter Indizes {#tips-for-creating-efficient-indexes}

### Sollte ich einen Index erstellen? {#should-i-create-an-index}

Die erste Frage, die beim Erstellen oder Optimieren von Indizes gestellt werden muss, ist, ob sie für eine bestimmte Situation erforderlich sind. Wenn Sie die fragliche Abfrage nur einmal oder nur gelegentlich und zu einer Zeit außerhalb der Spitzenzeiten für das System über einen Batch-Prozess ausführen, ist es möglicherweise besser, überhaupt keinen Index zu erstellen.

Wenn ein Index erstellt wurde, muss mit jeder Aktualisierung der indizierten Daten auch der Index aktualisiert werden. Da dies Auswirkungen auf die Leistung des Systems hat, sollten Indizes nur erstellt werden, wenn sie erforderlich sind.

Außerdem sind Indizes nur nützlich, wenn die im Index enthaltenen Daten eindeutig genug sind, um sie zu rechtfertigen. Betrachten Sie einen Index in einem Buch und die Themen, die darin behandelt werden. Bei der Indizierung einer Reihe von Themen in einem Text gibt es in der Regel Hunderte oder Tausende von Einträgen, was es Ihnen ermöglicht, schnell zu einer Untergruppe von Seiten zu springen, um die gesuchten Informationen schnell zu finden. Wenn dieser Index nur zwei oder drei Einträge hätte, von denen jeder auf mehrere Hundert Seiten verweist, wäre der Index nicht nützlich. Dasselbe Konzept gilt für Datenbankindizes. Wenn es nur einige eindeutige Werte gibt, ist der Index nicht nützlich. Trotzdem kann ein Index auch zu groß werden, um nützlich zu sein. Informationen zu Indexstatistiken finden Sie unter [Indexstatistiken](/help/sites-deploying/best-practices-for-queries-and-indexing.md#index-statistics) höher.

### Lucene- oder Eigenschaftenindizes? {#lucene-or-property-indexes}

Lucene-Indizes wurden in Oak 1.0.9 eingeführt und bieten einige leistungsstarke Optimierungen gegenüber den Eigenschaftenindizes, die beim ersten Start von AEM 6 eingeführt wurden. Berücksichtigen Sie bei der Entscheidung, ob Lucene-Indizes oder Eigenschaftenindizes verwendet werden sollen, Folgendes:

* Lucene-Indizes bieten viel mehr Funktionen als Eigenschaftenindizes. Beispielsweise kann ein Eigenschaftenindex nur eine einzelne Eigenschaft indizieren, während ein Lucene-Index viele enthalten kann. Weitere Informationen zu allen in Lucene-Indizes verfügbaren Funktionen finden Sie im [Dokumentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).
* Lucene-Indizes sind asynchron. Dies bietet zwar eine erhebliche Leistungssteigerung, kann aber auch zu einer Verzögerung zwischen dem Schreiben von Daten in das Repository und dem Aktualisieren des Index führen. Wenn Abfragen zu 100 % genaue Ergebnisse zurückgeben müssen, ist ein Eigenschaftenindex erforderlich.
* Da Lucene-Indizes asynchron sind, können sie keine Eindeutigkeitseinschränkungen erzwingen. Wenn dies erforderlich ist, muss ein Eigenschaftenindex eingerichtet werden.

Im Allgemeinen wird empfohlen, Lucene-Indizes zu verwenden, es sei denn, es besteht eine zwingende Notwendigkeit, Eigenschaftenindizes zu verwenden, damit Sie die Vorteile einer höheren Leistung und Flexibilität nutzen können.

### Solr-Indizierung {#solr-indexing}

AEM unterstützt standardmäßig auch die Solr-Indizierung. Dies wird zur Unterstützung der Volltextsuche verwendet, kann aber auch zur Unterstützung beliebiger JCR-Abfragen verwendet werden. Solr sollte berücksichtigt werden, wenn die AEM Instanzen nicht über die CPU-Kapazität verfügen, um die Anzahl der Abfragen zu verarbeiten, die in suchintensiven Implementierungen wie suchgesteuerten Websites mit einer hohen Anzahl gleichzeitiger Benutzer erforderlich sind. Alternativ kann Solr in einem Crawler-basierten Ansatz implementiert werden, um einige der fortschrittlicheren Funktionen der Plattform zu nutzen.

Solr-Indizes können so konfiguriert werden, dass sie für Entwicklungsumgebungen eingebettet auf dem AEM-Server ausgeführt werden, oder sie können in eine Remote-Instanz abgeladen werden, um die Suchskalierbarkeit in der Produktions- und Staging-Umgebung zu verbessern. Während die Abladung der Suche die Skalierbarkeit verbessert, führt sie zu Latenzzeiten und wird daher nicht empfohlen, es sei denn, dies ist erforderlich. Weitere Informationen zum Konfigurieren der Solr-Integration und zum Erstellen von Solr-Indizes finden Sie unter [Dokumentation zu Oak-Abfragen und Indizierung](/help/sites-deploying/queries-and-indexing.md#the-solr-index).

>[!NOTE]
>
>Der integrierte Solr-Suchansatz ermöglicht es, die Indizierung auf einen Solr-Server auszulagern. Wenn die erweiterten Funktionen des Solr-Servers durch einen Crawler-basierten Ansatz verwendet werden, ist eine zusätzliche Konfiguration erforderlich.

Der Nachteil dieses Ansatzes besteht darin, dass AEM Abfragen zwar standardmäßig ACLs respektieren und so Ergebnisse verbergen, auf die ein Benutzer keinen Zugriff hat. Eine Externalisierung der Suche an einen Solr-Server unterstützt diese Funktion nicht. Wenn die Suche auf diese Weise externalisiert werden soll, muss besonders darauf geachtet werden, dass den Benutzern keine Ergebnisse angezeigt werden, die sie nicht sehen sollten.

Mögliche Anwendungsfälle, in denen dieser Ansatz sinnvoll sein kann, sind Fälle, in denen Suchdaten aus mehreren Quellen möglicherweise aggregiert werden müssen. Sie können beispielsweise eine Site auf AEM gehostet und eine zweite Site auf einer Drittanbieterplattform gehostet werden. Solr könnte so konfiguriert werden, dass der Inhalt beider Sites durchsucht und in einem aggregierten Index gespeichert wird. Dies würde Site-übergreifende Suchen ermöglichen.

### Designüberlegungen {#design-considerations}

In der Oak-Dokumentation für Lucene-Indizes werden verschiedene Überlegungen zum Erstellen von Indizes aufgeführt:

* Wenn die Abfrage unterschiedliche Pfadbeschränkungen verwendet, verwenden Sie `evaluatePathRestrictions`. Dadurch kann die Abfrage die Teilmenge der Ergebnisse unter dem angegebenen Pfad zurückgeben und sie dann anhand der Abfrage filtern. Andernfalls sucht die Abfrage nach allen Ergebnissen, die mit den Abfrageparametern im Repository übereinstimmen, und filtert sie dann anhand des Pfads.
* Wenn für die Abfrage die Sortierfunktion verwendet wird, ist eine explizite Eigenschaftendefinition erforderlich. Außerdem müssen Sie `ordered` auf `true` setzen. Dadurch können die Ergebnisse als solche im Index sortiert und bei der Ausführung der Abfrage bei kostspieligen Sortiervorgängen gespeichert werden.

* Setzen Sie nur das, was benötigt wird, in den Index. Das Hinzufügen nicht benötigter Funktionen oder Eigenschaften führt dazu, dass der Index wächst und die Leistung verlangsamt.
* In einem Eigenschaftenindex trägt ein eindeutiger Eigenschaftsname dazu bei, die Indexgröße zu reduzieren, aber für Lucene-Indizes sollten `nodeTypes` und `mixins` zum Erstellen kohäsiver Indizes verwendet werden. Die Abfrage nach einem bestimmten `nodeType` oder `mixin` ist leistungsstärker als eine `nt:base`-Abfrage. Definieren Sie bei diesem Ansatz `indexRules` für die fraglichen `nodeTypes`.

* Wenn Ihre Abfragen nur unter bestimmten Pfaden ausgeführt werden, erstellen Sie diese Indizes unter diesen Pfaden. Indizes müssen nicht im Stammverzeichnis des Repositorys gespeichert werden.
* Es wird empfohlen, einen einzigen Index zu verwenden, wenn alle zu indizierenden Eigenschaften miteinander verknüpft sind, damit Lucene so viele Eigenschaftsbeschränkungen wie möglich nativ bewerten kann. Außerdem verwendet eine Abfrage nur einen Index, auch wenn ein Join ausgeführt wird.

### CopyOnRead {#copyonread}

Wenn `NodeStore` remote gespeichert wird, kann die Option `CopyOnRead` aktiviert werden. Die Option bewirkt, dass der Remote-Index beim Lesen in das lokale Dateisystem geschrieben wird. Dies kann dazu beitragen, die Leistung von Abfragen zu verbessern, die häufig mit diesen Remote-Indizes ausgeführt werden.

Dies kann in der OSGi-Konsole unter der **LuceneIndexProvider** und ist standardmäßig ab Oak 1.0.13 aktiviert.

### Entfernen von Indizes {#removing-indexes}

Beim Entfernen eines Index wird immer empfohlen, den Index durch Einstellen der Eigenschaft `type` auf `disabled` vorübergehend zu deaktivieren und Tests durchzuführen, um vor dem Löschen eine ordnungsgemäße Funktionsweise der Anwendung sicherzustellen. Ein Index wird bei Deaktivierung nicht aktualisiert, sodass er möglicherweise nicht über den richtigen Inhalt verfügt, wenn er reaktiviert wird, und möglicherweise neu indiziert werden muss.

Nachdem Sie einen Eigenschaftenindex auf einer TarMK-Instanz entfernt haben, muss die Komprimierung ausgeführt werden, um den verwendeten Speicherplatz zurückzugewinnen. Bei Lucene-Indizes befindet sich der tatsächliche Indexinhalt im BlobStore, sodass eine automatische Datenspeicherbereinigung erforderlich ist.

Beim Entfernen eines Index auf einer MongoDB-Instanz sind die Löschkosten proportional zur Anzahl der Knoten im Index. Da das Löschen eines großen Index Probleme verursachen kann, wird empfohlen, den Index zu deaktivieren und ihn nur während eines Wartungsfensters zu löschen, indem ein Tool wie **oak-mongo.js**. Beachten Sie, dass dieser Ansatz nicht für reguläre Knoteninhalte verwendet werden sollte, da er zu Dateninkonsistenzen führen kann.

>[!NOTE]
>
>Weitere Informationen zu oak-mongo.js finden Sie im [Abschnitt zu den Befehlszeilen-Tools](https://jackrabbit.apache.org/oak/docs/command_line.html) der Oak-Dokumentation.

### JCR-Abfrage-Schnellübersicht {#jcrquerycheatsheet}

Um die Erstellung effizienter JCR-Abfragen und Indexdefinitionen zu unterstützen, kann die [JCR-Abfrage-Schnellübersicht](assets/JCR_query_cheatsheet-v1.1.pdf) heruntergeladen und während der Entwicklung als Referenz verwendet werden. Sie enthält Beispielabfragen für QueryBuilder, XPath und SQL-2, die mehrere Szenarien abdecken, welche sich hinsichtlich der Abfrageleistung unterschiedlich verhalten. Sie enthält auch Empfehlungen zum Erstellen oder Anpassen von Oak-Indizes. Der Inhalt dieser Schnellübersicht gilt für AEM 6.5 und AEM as a Cloud Service.

## Neuindizierung {#re-indexing}

In diesem Abschnitt werden die **only** akzeptable Gründe für die Neuindizierung von Oak-Indizes.

Außerhalb der unten aufgeführten Gründe bewirkt das Initiieren von Neuindizes von Oak-Indizes Folgendes: **not** das Verhalten ändern oder Probleme beheben und unnötigerweise die Belastung der AEM erhöhen.

Eine Neuindizierung von Oak-Indizes ist zu vermeiden, es sei denn, dies wird durch einen Grund in den unten stehenden Tabellen erläutert.

>[!NOTE]
>
>Bevor Sie die unten stehenden Tabellen durchsuchen, um festzustellen, ob eine Neuindizierung nützlich ist, **always** verify:
>
>* Die Abfrage ist korrekt.
>* Die Abfrage wird zum erwarteten Index aufgelöst (mithilfe von [Abfrage erläutern](/help/sites-administering/operations-dashboard.md#diagnosis-tools))
>* der Indizierungsprozess abgeschlossen ist
>

### Änderungen der Oak-Indexkonfiguration {#oak-index-configuration-changes}

Die einzigen akzeptablen, nicht fehlenden Bedingungen für die Neuindizierung von Oak-Indizes sind, wenn sich die Konfiguration eines Oak-Index geändert hat.

*Die Neuindizierung sollte immer unter gebührender Berücksichtigung der Auswirkungen auf die Gesamtleistung AEM und in Zeiten geringer Aktivität oder Wartungsfenster durchgeführt werden.*

Im Folgenden finden Sie Details zu möglichen Problemen sowie entsprechende Lösungen:

* [Definitionsänderung des Eigenschaftenindex](#property-index-definition-change)
* [Definitionsänderung des Lucene-Index](#lucene-index-definition-change)

#### Definitionsänderung des Eigenschaftenindex {#property-index-definition-change}

* Gilt für/wenn:

   * Alle Oak-Versionen
   * Nur [Eigenschaftenindizes](https://jackrabbit.apache.org/oak/docs/query/property-index.html)

* Symptome:

   * Knoten, die vor der Definitionsaktualisierung des Eigenschaftenindex vorhanden sind, fehlen in den Ergebnissen

* Überprüfen:

   * Bestimmen Sie, ob fehlende Knoten vor der Bereitstellung der aktualisierten Indexdefinition erstellt/geändert wurden.
   * Überprüfen Sie die Eigenschaften `jcr:created` oder `jcr:lastModified` aller fehlenden Knoten im Hinblick auf die Änderungszeit des Index.

* Beheben des Problems:

   * [Neuindizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md#how-to-re-index) Lucene-Index
   * Alternativ können Sie auf die fehlenden Knoten tippen (einen benignen Schreibvorgang durchführen)

      * Erfordert manuelle Änderungen oder benutzerdefinierten Code
      * Erfordert, dass der Satz fehlender Knoten bekannt ist.
      * Erfordert das Ändern einer beliebigen Eigenschaft auf dem Knoten

#### Definitionsänderung des Lucene-Index {#lucene-index-definition-change}

* Gilt für/wenn:

   * Alle Oak-Versionen
   * Ausschließlich [Lucene-Indizes](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptome:

   * Lucene-Index enthält keine erwarteten Ergebnisse
   * Die Abfrageergebnisse spiegeln nicht das erwartete Verhalten der Indexdefinition wider
   * Der Abfrageplan meldet keine erwartete Ausgabe basierend auf Indexdefinition

* Überprüfen:

   * Überprüfen Sie, ob die Indexdefinition mithilfe der Methode Lucene Index Statistics JMX Mbean (LuceneIndex) geändert wurde. `diffStoredIndexDefinition`.

* Beheben des Problems:

   * Oak-Versionen vor 1.6:

      * [Neuindizierung](#how-to-re-index) Lucene-Index

   * Oak-Versionen 1.6+

      * Wenn der vorhandene Inhalt von den Änderungen nicht betroffen ist, ist nur eine Aktualisierung erforderlich

         * [Aktualisieren](https://jackrabbit.apache.org/oak/docs/query/lucene.html#stored-index-definition) Sie den Lucene-Index, indem Sie [oak:queryIndexDefinition] @refresh=true einstellen.

      * Andernfalls [reindex](#how-to-re-index) Lucene-Index

         * Hinweis: Der Indexstatus der letzten guten Neuindizierung (oder anfänglichen Indizierung) wird verwendet, bis eine neue Neuindizierung ausgelöst wird

### Fehler und außergewöhnliche Situationen {#erring-and-exceptional-situations}

In der folgenden Tabelle werden die einzigen akzeptablen Fehler- und Ausnahmesituationen beschrieben, in denen die Neuindizierung von Oak-Indizes das Problem beheben kann.

Wenn bei AEM ein Problem auftritt, das nicht den unten beschriebenen Kriterien entspricht, führen Sie **not** indizieren Sie alle Indizes neu, da dies das Problem nicht behebt.

Im Folgenden finden Sie Details zu möglichen Problemen sowie entsprechende Lösungen:

* [Fehlende Lucene-Index-Binärdateien](#lucene-index-binary-is-missing)
* [Beschädigte Lucene-Index-Binärdateien](#lucene-index-binary-is-corrupt)

#### Fehlende Lucene-Index-Binärdateien {#lucene-index-binary-is-missing}

* Gilt für/wenn:

   * Alle Oak-Versionen
   * Ausschließlich [Lucene-Indizes](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptome:

   * Lucene-Index enthält keine erwarteten Ergebnisse

* Überprüfen:

   * Die Fehlerprotokolldatei enthält eine Ausnahme, die besagt, dass eine Binärdatei des Lucene-Index fehlt.

* Beheben des Problems:

   * Durchführen einer Repository-Durchlauf-Prüfung; Beispiel:

     [http://localhost:4502/system/console/repositorycheck](http://localhost:4502/system/console/repositorycheck)

     Durch das Durchlaufen des Repositorys wird bestimmt, ob andere Binärdateien (außer Lucene-Dateien) fehlen.

   * Wenn andere Binärdateien als Lucene-Indizes fehlen, stellen Sie diese anhand einer Sicherung wieder her.
   * Andernfalls [reindex](#how-to-re-index) *all* Lucene-Indizes
   * Hinweis:

     Diese Bedingung ist ein Hinweis auf einen falsch konfigurierten Datenspeicher, der dazu führen kann, dass ANY-Binärdateien (z. B. Asset-Binärdateien) fehlen.

     Stellen Sie in diesem Fall die letzte einwandfreie Version des Repositorys wieder her, um alle fehlenden Binärdateien wiederzugewinnen.

#### Beschädigte Lucene-Index-Binärdateien {#lucene-index-binary-is-corrupt}

* Gilt für/wenn:

   * Alle Oak-Versionen
   * Ausschließlich [Lucene-Indizes](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

* Symptome:

   * Lucene-Index enthält keine erwarteten Ergebnisse

* Überprüfen:

   * Die `AsyncIndexUpdate` (alle fünf Sekunden) schlägt mit einer Ausnahme in error.log fehl:

     `...a Lucene index file is corrupt...`

* Beheben des Problems:

   * Entfernen Sie die lokale Kopie des Lucene-Index

      1. AEM anhalten
      1. Löschen Sie die lokale Kopie des Lucene-Index unter `crx-quickstart/repository/index`.
      1. Starten Sie AEM neu.

   * Wenn das Problem hierdurch nicht behoben wird und die `AsyncIndexUpdate`-Ausnahmen bestehen bleiben, gehen Sie wie folgt vor:

      1. [Neuindizierung](#how-to-re-index) den fehlerhaften Index
      1. Öffnen Sie zudem ein Ticket beim [Adobe-Support](https://helpx.adobe.com/de/support.html).

### Neuindizierung {#how-to-re-index}

>[!NOTE]
>
>In AEM 6.5 [oak-run.jar ist die EINZIGE unterstützte Methode](/help/sites-deploying/indexing-via-the-oak-run-jar.md#reindexingapproachdecisiontree) für die Neuindizierung in MongoMK- oder RDBMK-Repositorys.

#### Neuindizieren von Eigenschaftenindizes {#re-indexing-property-indexes}

* Verwendung [oak-run.jar](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) Neuindizieren des Eigenschaftenindex
* Stellen Sie im Eigenschaftenindex die Eigenschaft „reindex-async“ auf „true“ ein:

   * `[oak:queryIndexDefinition]@reindex-async=true`

* Neuindizieren des Eigenschaftenindex asynchron mithilfe der Web-Konsole über die **PropertyIndexAsyncReindex** MBean;

  Beispiel,

  [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DPropertyIndexAsyncReindex)

#### Neuindizieren von Lucene-Eigenschaftenindizes {#re-indexing-lucene-property-indexes}

* Verwendung [oak-run.jar zu reindex](/help/sites-deploying/oak-run-indexing-usecases.md#usecase3reindexing) den Lucene-Eigenschaftsindex.
* Stellen Sie im Lucene-Eigenschaftsindex

   * `[oak:queryIndexDefinition]@reindex-async=true`

>[!NOTE]
>
>Im vorherigen Abschnitt werden die Anleitungen zur Neuindizierung von Oak aus der [Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) im Rahmen von AEM.

### Textvorextraktion von Binärdateien {#text-pre-extraction-of-binaries}

Bei der Textvorextraktion wird Text aus Binärdateien extrahiert und verarbeitet, direkt aus dem Datenspeicher über einen isolierten Prozess, und der extrahierte Text wird direkt zu nachfolgenden Neuindizierungen von Oak-Indizes weitergeleitet.

* Die Oak-Textvorextraktion wird für die Neuindizierung/Indizierung von Lucene-Indizes in Repositorys mit großen Dateimengen (Binärdateien) empfohlen, die extrahierbaren Text enthalten (z. B. PDF, Word Docs, PPTs, TXT usw.), der für die Volltextsuche über bereitgestellte Oak-Indizes qualifiziert ist. Beispiel: `/oak:index/damAssetLucene`.
* Die Textvorextraktion profitiert nur von der Neuindizierung/Indizierung von Lucene-Indizes und NICHT von Oak-Eigenschaftenindizes, da Eigenschaftenindizes keinen Text aus Binärdateien extrahieren.
* Die Textvorextraktion wirkt sich sehr positiv auf die Volltext-Neuindizierung von textbasierten Binärdateien (PDF, Doc, TXT usw.) aus, während ein Bilderrepository nicht die gleiche Effizienz genießt, da Bilder keinen extrahierbaren Text enthalten.
* Die Textvorextraktion führt die Extrahierung von Volltextsuchtext auf überaus effiziente Weise durch und stellt ihn dem Oak-Neuindizierungsprozess auf eine Weise zur Verfügung, die überaus effizient zu nutzen ist.

#### Wann kann die Textvorextraktion verwendet werden? {#when-can-text-pre-extraction-be-used}

Neuindizieren einer **vorhandene** Lucene-Index mit aktivierter Binärextraktion

* Neuindizierungsverarbeitung **all** Kandidateninhalt im Repository; Wenn die Binärdateien, aus denen Volltext extrahiert werden soll, zahlreich oder komplex sind, wird eine höhere Rechenlast für die Volltextextextextraktion auf AEM gelegt. Die Textvorextraktion verschiebt die &quot;rechnerisch kostspielige Arbeit&quot;der Textextraktion in einen isolierten Prozess, der direkt auf AEM Datenspeicher zugreift, wodurch Overhead- und Ressourcenkonflikte in AEM vermieden werden.

Unterstützung bei der Bereitstellung eines **new** Lucene-Index für AEM mit aktivierter Binärextraktion

* Wenn ein neuer Index (mit aktivierter binärer Extraktion) in AEM bereitgestellt wird, indiziert Oak automatisch alle Kandidateninhalte beim nächsten asynchronen Volltext-Index-Lauf. Aus den gleichen Gründen, die oben unter Neuindizierung beschrieben werden, kann dies zu einer übermäßigen Belastung der AEM führen.

#### Wann kann die Textvorextraktion NICHT verwendet werden? {#when-can-text-pre-extraction-not-be-used}

Die Textvorextraktion kann nicht für neue Inhalte verwendet werden, die zum Repository hinzugefügt werden, und ist auch nicht erforderlich.

Neue Inhalte werden dem Repository hinzugefügt und werden automatisch schrittweise durch den asynchronen Volltext-Indizierungsprozess indiziert (standardmäßig alle 5 Sekunden).

Unter normalen AEM, z. B. beim Hochladen von Assets über die Web-Benutzeroberfläche oder bei der programmatischen Aufnahme von Assets, wird AEM den neuen binären Inhalt automatisch und inkrementell in Volltext indizieren. Da die Datenmenge inkrementell und relativ gering ist (was ungefähr der Datenmenge entspricht, die in 5 Sekunden im Repository gespeichert werden kann), können AEM während der Indizierung die Volltextextextraktion aus den Binärdateien durchführen, ohne die Gesamtleistung des Systems zu beeinträchtigen.

#### Voraussetzungen für die Verwendung der Textvorextraktion {#prerequisites-to-using-text-pre-extraction}

* Sie werden einen Lucene-Index neu indizieren, der eine Volltext-Binärextrahierung durchführt, oder einen neuen Index bereitstellen, der Volltext-Indexbinärdateien vorhandener Inhalte enthält
* Der Inhalt (Binärdateien), aus dem Text vorextrahiert werden soll, muss sich im Repository befinden
* Ein Wartungsfenster zum Generieren der CSV-Datei UND zum Ausführen der endgültigen Neuindizierung
* Oak-Version: 1.0.18+, 1.2.3+
* Die folgende [oak-run.jar](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)-Version muss verwendet werden: 1.7.4 oder höher.
* Ordner/Freigabe eines Dateisystems zum Speichern des extrahierten Texts, auf den über die Indizierungs-AEM zugegriffen werden kann

   * Für die OSGi-Konfiguration Textvorextraktion ist ein Dateisystempfad zu den extrahierten Textdateien erforderlich, sodass sie direkt von der AEM-Instanz (lokale Festplatte oder Dateifreigabebereitstellung) aus zugänglich sein müssen

#### Durchführen der Textvorextraktion {#how-to-perform-text-pre-extraction}

>[!NOTE]
>
>***Die unten beschriebenen oak-run.jar-Befehle finden Sie vollständig aufgeführt unter [https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html)***.
>
>Die obige Grafik und die darunter stehenden Schritte erläutern und ergänzen die in der Apache Oak-Dokumentation dargelegten technischen Schritte zur Textvorextraktion.

![Prozessablauf der Textvorextraktion](assets/chlimage_1-139.png)

**Generieren einer Inhaltsliste für die Vorextraktion**

*Führen Sie Schritt 1 (a-b) während eines Wartungsfensters/einer Zeitspanne mit geringer Nutzung aus, da der Knotenspeicher während dieses Vorgangs durchlaufen wird, was zu einer erheblichen Belastung des Systems führen kann.*

1a. Ausführen `oak-run.jar --generate` , um eine Liste von Knoten zu erstellen, deren Text vorab extrahiert wird.

1b. Die Liste der Knoten (1a) wird im Dateisystem als CSV-Datei gespeichert

Der gesamte Knotenspeicher wird jedes Mal durchlaufen (wie durch die Pfade im oak-run-Befehl angegeben). `--generate` ausgeführt wird und eine **new** Die CSV-Datei wird erstellt. Die CSV-Datei lautet **not** wird zwischen diskreten Ausführungen des Textvorextraktionsprozesses wiederverwendet (Schritte 1 bis 2).

**Text vorab in Dateisystem extrahieren**

*Schritt 2 (a-c) kann während des normalen AEM ausgeführt werden, da nur mit dem Datenspeicher interagiert wird.*

2a. Ausführen `oak-run.jar --tika` , um Text für die in der CSV-Datei, die in (1b) generiert wurde, aufgezählten Binärknoten vorab zu extrahieren.

2b. Der in (2a) initiierte Prozess greift direkt auf die Binärknoten zu, die in der CSV-Datei im Datenspeicher definiert sind, und extrahiert Text.

2c. Extrahierter Text wird im Dateisystem in einem Format gespeichert, das vom Oak-Neuindizierungsprozess (3a) erfasst werden kann

Vorextrahierter Text ist in der CSV-Datei durch einen binären Fingerabdruck gekennzeichnet. Wenn die Binärdatei identisch ist, kann derselbe vorextrahierte Text für AEM Instanzen verwendet werden. Da AEM Publish normalerweise eine Untergruppe von AEM Author ist, kann der vorab extrahierte Text aus AEM Author häufig auch zur Neuindizierung von AEM Publish verwendet werden (vorausgesetzt, die AEM-Veröffentlichung hat Dateisystemzugriff auf die extrahierten Textdateien).

Vorab extrahierter Text kann schrittweise im Laufe der Zeit hinzugefügt werden. Bei der Textvorextraktion wird die Extraktion für zuvor extrahierte Binärdateien übersprungen. Daher empfiehlt es sich, vorab extrahierten Text beizubehalten, falls in Zukunft eine Neuindizierung erforderlich ist (vorausgesetzt, der extrahierte Inhalt ist nicht unnötig groß). Ziehen Sie sonst eine zwischenzeitliche Zip-Komprimierung des Inhalts in Betracht, da Text gut komprimiert werden kann.)

**Neuindizieren von Oak-Indizes, Abrufen von Volltext aus extrahierten Textdateien**

*Führen Sie die Neuindizierung (Schritte 3a-b) während einer Wartungs-/Nutzungsperiode durch, da der Knotenspeicher während dieses Vorgangs durchlaufen wird, was eine erhebliche Belastung des Systems verursachen kann.*

3a. [Neuindizierung](#how-to-re-index) von Lucene-Indizes werden in AEM aufgerufen.

3b. Die Apache Jackrabbit Oak DataStore PreExtractedTextProvider-OSGi-Konfiguration (zum Verweisen auf den extrahierten Text über einen Dateisystempfad) weist Oak an, Volltext aus den extrahierten Dateien zu beziehen, und vermeidet ein direktes Auffinden und Verarbeiten der im Repository gespeicherten Daten.
