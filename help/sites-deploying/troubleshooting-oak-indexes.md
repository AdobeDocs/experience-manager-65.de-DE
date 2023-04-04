---
title: Fehlerbehebung bei Oak-Indizes
seo-title: Troubleshooting Oak Indexes
description: So erkennen und beheben Sie langsame Neuindizierung.
uuid: 6567ddae-128c-4302-b7e8-8befa66b1f43
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: ea70758f-6726-4634-bfb4-a957187baef0
exl-id: 85981463-189c-4f50-9d21-1d2f734b960a
source-git-commit: 9defa6d1843007e9375d839f72f6993c691a37c0
workflow-type: tm+mt
source-wordcount: '1474'
ht-degree: 39%

---

# Fehlerbehebung bei Oak-Indizes{#troubleshooting-oak-indexes}

## Langsame Neuindizierung  {#slow-re-indexing}

AEM interne Neuindizierungsprozess erfasst Repository-Daten und speichert sie in Oak-Indizes, um eine leistungsfähige Inhaltsabfrage zu unterstützen. Bei außergewöhnlichen Umständen kann der Vorgang langsam werden oder sogar anhalten. Diese Seite dient als Anleitung zur Fehlerbehebung, um zu ermitteln, ob die Indizierung langsam ist, die Ursache zu finden und das Problem zu beheben.

Es ist wichtig, zwischen einer Neuindizierung zu unterscheiden, die unangemessen lange dauert, und einer Neuindizierung, die viel Zeit in Anspruch nimmt, da sie große Mengen von Inhalten indiziert. Beispielsweise wird die Indexzeit von Inhalten mit der Menge an Inhalten skaliert, sodass große Produktionsspeicher für die Neuindizierung länger als kleine Entwicklungs-Repositorys benötigen.

Siehe [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md) für weitere Informationen zum Zeitpunkt und zur Neuindizierung von Inhalten.

## Anfängliche Erkennung {#initial-detection}

Um eine langsame Indizierung anfänglich zu erkennen, müssen die `IndexStats`-JMX-MBeans überprüft werden. Klicken Sie auf die betroffene AEM-Instanz und gehen Sie wie folgt vor:

1. Öffnen Sie die Web-Konsole und klicken Sie auf die Registerkarte „JMX“. Oder wechseln Sie zu https://&lt;Host>:&lt;Port>/system/console/jmx (z. B. [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
1. Navigieren Sie zu den `IndexStats`-MBeans.
1. Öffnen Sie die `IndexStats`-MBeans für `async` und `fulltext-async`.

1. Überprüfen Sie für beide MBeans, ob die Zeitstempel **Done** und **LastIndexTime** weniger als 45 Minuten zurückliegen.

1. Falls für eines der MBeans der Zeitstempel (**Done** oder **LastIndexedTime**) mehr als 45 Minuten zurückliegt, dauert der Indizierungsvorgang zu lange oder ist fehlgeschlagen. Dieses Problem führt dazu, dass die asynchronen Indizes veraltet sind.

## Indizierung wird nach einem erzwungenen Herunterfahren angehalten {#indexing-is-paused-after-a-forced-shutdown}

Bei erzwungenem Herunterfahren wird die asynchrone Indizierung AEM bis zu 30 Minuten nach dem Neustart ausgesetzt. Und normalerweise werden weitere 15 Minuten benötigt, um den ersten Neuindizierungsdurchgang abzuschließen, für insgesamt etwa 45 Minuten (zurück an die [Anfängliche Erkennung](/help/sites-deploying/troubleshooting-oak-indexes.md#initial-detection) 45 Minuten). Wenn die Indizierung nach einem erzwungenen Herunterfahren angehalten wird:

1. Ermitteln Sie zunächst, ob die AEM-Instanz erzwungen heruntergefahren wurde (der AEM-Prozess wurde erzwungen beendet oder ein Stromausfall trat ein), und starten Sie später erneut.

   * Hierfür kann die [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) überprüft werden.

1. Wenn das erzwungene Herunterfahren beim Neustart stattgefunden hat, setzt AEM die Neuindizierung automatisch für bis zu 30 Minuten aus.
1. Warten Sie etwa 45 Minuten, bis AEM normale asynchrone Indizierungsvorgänge wieder aufnehmen kann.

## Thread-Pool überlastet {#thread-pool-overloaded}

>[!NOTE]
>
>Stellen Sie bei AEM 6.1 sicher, dass [AEM 6.1 CFP 11](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de) installiert ist.

In Ausnahmefällen kann der Thread-Pool, der zur Verwaltung der asynchronen Indizierung verwendet wird, überlastet sein. Um den Indizierungsprozess zu isolieren, kann ein Thread-Pool konfiguriert werden, um zu verhindern, dass andere AEM die Fähigkeit von Oak beeinträchtigen, Inhalte zeitnah zu indizieren. Gehen Sie in solchen Fällen wie folgt vor:

1. Definieren Sie einen neuen, isolierten Thread-Pool für den Apache Sling Scheduler, der für die asynchrone Indizierung verwendet werden soll:

   * Nagivieren Sie auf der betroffenen AEM-Instanz zu „AEM-OSGi-Web-Konsole“ > „OSGi“ > „Konfiguration“ > „Apache Sling Scheduler“ oder zu https://&lt;Host>:&lt;Port>/system/console/configMgr (beispielsweise [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)).
   * Fügen Sie dem Feld &quot;Zulässige Thread-Pools&quot;einen Eintrag mit dem Wert &quot;oak&quot;hinzu.
   * Um die Änderungen zu speichern, klicken Sie auf **Speichern** unten rechts.

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. Vergewissern Sie sich, dass der neue Thread-Pool des Apache Sling Scheduler registriert ist und in der Web-Konsole &quot;Apache Sling Scheduler Status&quot;angezeigt wird.

   * Navigieren Sie zu „AEM-OSGi-Web-Konsole“ > „Status“ > „Sling Scheduler“ oder zu https://&lt;Host>:&lt;Port>/system/console/status-slingscheduler (beispielsweise [http://localhost:4502/system/console/status-slingscheduler](http://localhost:4502/system/console/status-slingscheduler)).
   * Stellen Sie sicher, dass die folgenden Pooleinträge vorhanden sind:

      * ApacheSlingoak
      * ApacheSlingdefault

   ![chlimage_1-120](assets/chlimage_1-120.png)

## Überwachungswarteschlange ist voll {#observation-queue-is-full}

Wenn in kurzer Zeit zu viele Änderungen und Zusagen am Repository vorgenommen werden, kann die Indizierung aufgrund einer vollständigen Beobachtungswarteschlange verzögert werden. Bestimmen Sie zunächst, ob die Beobachtungswarteschlange voll ist:

1. Wechseln Sie zur Web-Konsole und klicken Sie auf die Registerkarte „JMX“. Oder wechseln Sie zu https://&lt;Host>:&lt;Port>/system/console/jmx (beispielsweise [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
1. Öffnen Sie im Oak-Repository das Statistik-MBean und überprüfen Sie, ob einer der Werte für `ObservationQueueMaxLength` mehr als 10.000 beträgt.

   * Bei normalem Betrieb wird dieser Höchstwert letztendlich auf null reduziert (insbesondere im Abschnitt `per second`). Überprüfen Sie daher, ob der Sekundenwert für `ObservationQueueMaxLength` 0 beträgt.
   * Wenn die Werte 10.000 oder höher sind und stetig zunehmen, deutet dies darauf hin, dass mindestens eine (möglicherweise mehrere) Warteschlange nicht so schnell verarbeitet werden kann, wie neue Änderungen (Commits) auftreten.
   * Jede Beobachtungswarteschlange hat einen Grenzwert (standardmäßig 10.000). Wenn die Warteschlange diesen Grenzwert erreicht, wird die Verarbeitung beeinträchtigt.
   * Bei Verwendung von MongoMK verschlechtert sich die interne Leistung des Oak-Cache mit zunehmender Warteschlangengröße. Diese Korrelation zeigt sich in der größeren `missRate` beim `DocChildren`-Cache im Statistik-MBean `Consolidated Cache`.

1. Um zu vermeiden, dass akzeptable Überwachungswarteschlangenbeschränkungen überschritten werden, sollten Sie:

   * Verringern Sie die konstante Rate von Commits. Kurze Spitzen bei den Commits sind akzeptabel, aber die konstante Rate sollte reduziert werden.
   * Vergrößern Sie den `DiffCache` wie unter [Tipps zur Leistungsoptimierung > Mongo-Speicheroptimierung > Dokument-Cache-Größe](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/configuring/configuring-performance.html?lang=en) beschrieben.

## Identifizierung und Behebung eines feststeckenden Neuindizierungsprozesses {#identifying-and-remediating-a-stuck-re-indexing-process}

Eine Neuindizierung kann unter zwei Bedingungen als &quot;vollständig festgeklemmt&quot;betrachtet werden:

* Die Neuindizierung verläuft langsam bis zu dem Punkt, an dem in den Protokolldateien kein signifikanter Fortschritt bezüglich der Anzahl der durchquerten Knoten gemeldet wird.

   * Wenn beispielsweise im Laufe einer Stunde keine Nachrichten vorhanden sind oder der Fortschritt so langsam ist, dass die Fertigstellung mindestens eine Woche dauert.

* Die Neuindizierung bleibt in einer Endlosschleife stecken, wenn wiederholte Ausnahmen in den Protokolldateien angezeigt werden (z. B. `OutOfMemoryException`) im Indizierungs-Thread. Die Wiederholung einer oder mehrerer derselben Ausnahmen im Protokoll zeigt, dass Oak versucht, dasselbe wiederholt zu indizieren, aber bei demselben Problem versagt.

Gehen Sie wie folgt vor, um einen blockierten Neuindizierungsprozess zu identifizieren und zu beheben:

1. Um die Ursache für eine blockierte Indizierung zu ermitteln, müssen die folgenden Informationen erfasst werden:

   * Erfassen Sie 5 Minuten Thread-Dump, eine Thread-Dump alle 2 Sekunden.
   * [Festlegen der DEBUG-Ebene und der Protokolle für die Appender](/help/sites-deploying/configure-logging.md).

      * *org.apache.jackrabbit.oak.plugins.index.AsyncIndexUpdate*
      * *org.apache.jackrabbit.oak.plugins.index.IndexUpdate*
   * Erfassen Sie die Daten aus dem asynchronen `IndexStats`-MBean:

      * Navigieren Sie zu AEM OSGi-Web-Konsole > Hauptfenster > JMX > IndexStat > async

         oder gehen Sie zu [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Dasync%2Ctype%3DIndexStats)
   * Verwenden Sie den Befehl [oak-run.jar&#39;s console mode](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), um Details zum *`/:async`*-Knoten abzurufen.
   * Erfassen Sie anhand des `CheckpointManager`-MBean eine Liste der Repository-Checkpoints:

      * AEM OSGi-Web-Konsole > Hauptfenster > JMX > CheckpointManager > listCheckpoints()

         oder gehen Sie zu [http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager](http://localhost:4502/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3DSegment+node+store+checkpoint+management%2Ctype%3DCheckpointManager)



1. Wenn Sie alle in Schritt 1 genannten Informationen erfasst haben, starten Sie AEM neu.

   * Das Neustarten von AEM kann das Problem lösen, wenn eine hohe gleichzeitige Belastung vorliegt (Überlauf der Beobachtungswarteschlange oder Ähnliches).
   * Wenn ein Neustart das Problem nicht behebt, wenden Sie sich an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?lang=de&amp;support-solution=General&amp;support-tab=home#support) und geben Sie alle in Schritt 1 erfassten Informationen an.

## Sicheres Abbrechen der asynchronen Neuindizierung {#safely-aborting-asynchronous-re-indexing}

Die Neuindizierung kann sicher über die `async, async-reindex`und f `ulltext-async` Indizierungsspuren ( `IndexStats` Mbean). Weitere Informationen finden Sie auch in der Dokumentation zu Apache Oak im Abschnitt [Abbrechen der Neuindizierung](https://jackrabbit.apache.org/oak/docs/query/indexing.html#abort-reindex). Beachten Sie außerdem Folgendes:

* Die Neuindizierung von Lucene- und Lucene-Eigenschaftenindizes kann abgebrochen werden, da sie von Natur aus asynchron sind.
* Die Neuindizierung von Oak-Eigenschaftenindizes kann nur abgebrochen werden, wenn die Neuindizierung über die `PropertyIndexAsyncReindexMBean`.

Gehen Sie wie folgt vor, um die Neuindizierung sicher abzubrechen:

1. Identifizieren Sie das IndexStats-MBean, das die Neuindizierungsspur steuert, die angehalten werden muss.

   * Navigieren Sie über die JMX-Konsole zum gewünschten IndexStats-MBean. Wechseln Sie dazu entweder zu „AEM-OSGi-Web-Konsole“ > „Haupt“ > „JMX“ oder zu https://&lt;Host>:&lt;Port>/system/console/jmx (beispielsweise [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
   * Öffnen Sie das IndexStats-MBean basierend auf der Neuindizierungsspur, die Sie stoppen möchten ( `async`, `async-reindex`oder `fulltext-async`)

      * Um die richtige Spur und die zugehörige IndexStats-MBean-Instanz zu ermitteln, durchsuchen Sie die Oak-Indexeigenschaft „async“. Die Eigenschaft &quot;async&quot;enthält den Spur-Namen: `async`, `async-reindex`oder `fulltext-async`.
      * Die Spur ist auch verfügbar, indem Sie auf AEM Index Manager in der Spalte &quot;Async&quot;zugreifen. Um auf den Index-Manager zuzugreifen, navigieren Sie zu Vorgänge > Diagnose > Index-Manager.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Rufen Sie den Befehl `abortAndPause()` auf dem entsprechenden `IndexStats`-MBean auf.
1. Markieren Sie die Oak-Indexdefinition entsprechend, um zu verhindern, dass die Neuindizierung fortgesetzt wird, wenn die Indizierungsspur fortgesetzt wird.

   * Bei der Neuindizierung einer **vorhandene** index, setzen Sie die Eigenschaft reindex auf false

      * `/oak:index/someExistingIndex@reindex=false`
   * Oder andernfalls für eine **new** index, entweder:

      * Festlegen der Eigenschaft &quot;type&quot;auf disabled

         * `/oak:index/someNewIndex@type=disabled`
      * oder entfernen Sie die Indexdefinition vollständig

   Übertragen Sie die Änderungen nach Abschluss in das Repository.

1. Setzen Sie schließlich die asynchrone Indizierung auf der abgebrochenen Indizierungsspur fort.

   * Rufen Sie im `IndexStats`-MBean, das den`abortAndPause()`-Befehl in Schritt 2 ausgegeben hat, den `resume()`-Befehl auf.

## Verhindern einer langsamen Neuindizierung {#preventing-slow-re-indexing}

Es ist am besten, eine Neuindizierung in ruhigen Zeiträumen vorzunehmen (z. B. nicht während einer großen Inhaltsaufnahme) und idealerweise während Wartungsfenstern, wenn AEM Last bekannt und kontrolliert ist. Stellen Sie außerdem sicher, dass die Neuindizierung nicht während anderer Wartungsaktivitäten stattfindet.
