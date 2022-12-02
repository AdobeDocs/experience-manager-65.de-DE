---
title: Fehlerbehebung bei Oak-Indizes
seo-title: Troubleshooting Oak Indexes
description: Erkennen und Beheben einer langsamen Neuindizierung
seo-description: How to detect and fix slow re-indexing.
uuid: 6567ddae-128c-4302-b7e8-8befa66b1f43
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: ea70758f-6726-4634-bfb4-a957187baef0
exl-id: 85981463-189c-4f50-9d21-1d2f734b960a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 100%

---

# Fehlerbehebung bei Oak-Indizes{#troubleshooting-oak-indexes}

## Langsame Neuindizierung  {#slow-re-indexing}

Bei der internen AEM-Neuindizierung werden Repository-Daten gesammelt und in Oak-Indizes gespeichert, die die performante Abfrage von Inhalt unterstützen. Bei außergewöhnlichen Umständen kann der Vorgang langsam werden oder sogar anhalten. Diese Seite dient als Leitfaden zur Fehlerbehebung und soll Sie dabei unterstützen, langsame Indizierungen und deren Ursache zu erkennen und zu beheben.

Dabei muss zwischen Neuindizierungen unterschieden werden, die ungewöhnliche lange dauern, und Neuindizierungen, die aufgrund der sehr großen Menge an Inhalt lange brauchen. Die für die Inhaltsindizierung benötigte Zeit ist beispielsweise abhängig von der Menge an Inhalt. Daher dauert die Neuindizierung großer Produktions-Repositorys länger als die Indizierung kleiner Entwicklungs-Repositorys.

Weitere Informationen dazu, wann und wie Sie Inhalt neu indizieren, finden Sie unter [Best Practices für Abfragen und Indizierung](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

## Anfängliche Erkennung {#initial-detection}

Um eine langsame Indizierung anfänglich zu erkennen, müssen die `IndexStats`-JMX-MBeans überprüft werden. Klicken Sie auf die betroffene AEM-Instanz und gehen Sie wie folgt vor:

1. Öffnen Sie die Web-Konsole und klicken Sie auf die Registerkarte „JMX“. Oder wechseln Sie zu https://&lt;Host>:&lt;Port>/system/console/jmx (z. B. [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
1. Navigieren Sie zu den `IndexStats`-MBeans.
1. Öffnen Sie die `IndexStats`-MBeans für `async` und `fulltext-async`.

1. Überprüfen Sie für beide MBeans, ob die Zeitstempel **Done** und **LastIndexTime** weniger als 45 Minuten zurückliegen.

1. Falls für eines der MBeans der Zeitstempel (**Done** oder **LastIndexedTime**) mehr als 45 Minuten zurückliegt, dauert der Indizierungsvorgang zu lange oder ist fehlgeschlagen. Dies führt dazu, dass die asynchronen Indizes veraltet sind.

## Indizierung wird nach erzwungenem Abschalten angehalten {#indexing-is-paused-after-a-forced-shutdown}

Nach einem erzwungenen Abschalten hält AEM die asynchrone Indizierung bis zu 30 Minuten nach dem Neustart an und benötigt in der Regel weitere 15 Minuten, also insgesamt 45 Minuten, um den ersten Indizierungsdurchgang abzuschließen. (Dies entspricht dem Zeitrahmen von 45 Minuten für die [anfängliche Erkennung](/help/sites-deploying/troubleshooting-oak-indexes.md#initial-detection)). Falls Sie vermuten, dass die Indizierung nach einem erzwungenen Abschalten angehalten wurde, gehen Sie wie folgt vor:

1. Finden Sie zuerst heraus, ob das Abschalten der AEM-Instanz erzwungen wurde (das Ende des AEM-Vorgangs wurde erzwungen oder ein Stromausfall trat auf) und diese anschließend neu gestartet wurde.

   * Hierfür kann die [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) überprüft werden.

1. Falls das Abschalten erzwungen wurde, wurde die Neuindizierung von AEM beim Neustart automatisch für bis zu 30 Minuten angehalten.
1. Warten Sie ungefähr 45 Minuten, dass AEM den normalen asynchronen Indizierungsvorgang wieder aufnimmt.

## Thread-Pool überlastet {#thread-pool-overloaded}

>[!NOTE]
>
>Stellen Sie bei AEM 6.1 sicher, dass [AEM 6.1 CFP 11](https://helpx.adobe.com/de/experience-manager/release-notes-aem-6-1-cumulative-fix-pack.html) installiert ist.

Bei außergewöhnlichen Umständen kann der zum Verwalten der asynchronen Indizierung verwendete Thread-Pool überlastet sein. Um den Indizierungsvorgang zu isolieren, kann ein Thread-Pool konfiguriert werden, der verhindert, dass andere AEM-Vorgänge die zügige Inhaltsindizierung von Oak beeinträchtigen. Gehen Sie dazu wie folgt vor:

1. Definieren Sie einen neuen, isolierten Thread-Pool für den Apache Sling Scheduler:

   * Nagivieren Sie auf der betroffenen AEM-Instanz zu „AEM-OSGi-Web-Konsole“ > „OSGi“ > „Konfiguration“ > „Apache Sling Scheduler“ oder zu https://&lt;Host>:&lt;Port>/system/console/configMgr (beispielsweise [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)).
   * Geben Sie in das Feld „Allowed Thread Pools“ den Wert „Oak“ ein.
   * Klicken Sie unten rechts auf „Save“, um die Änderungen zu speichern.

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. Überprüfen Sie, dass der neue Thread-Pool in Apache Sling Scheduler registriert ist und in der Statusanzeige der Web-Konsole von Apache Sling Scheduler angezeigt wird.

   * Navigieren Sie zu „AEM-OSGi-Web-Konsole“ > „Status“ > „Sling Scheduler“ oder zu https://&lt;Host>:&lt;Port>/system/console/status-slingscheduler (beispielsweise [http://localhost:4502/system/console/status-slingscheduler](http://localhost:4502/system/console/status-slingscheduler)).
   * Vergewissern Sie sich, dass die folgenden Pool-Einträge vorhanden sind:

      * ApacheSlingoak
      * ApacheSlingdefault

   ![chlimage_1-120](assets/chlimage_1-120.png)

## Überwachungswarteschlange ist voll {#observation-queue-is-full}

Falls am Repository in kurzer Zeit zu viele Änderungen oder Commits erfolgen, kann dies die Indizierung verzögern, da die Überwachungswarteschlange voll ist. Stellen Sie zuerst fest, ob die Überwachungswarteschlange voll ist:

1. Wechseln Sie zur Web-Konsole und klicken Sie auf die Registerkarte „JMX“. Oder wechseln Sie zu https://&lt;Host>:&lt;Port>/system/console/jmx (beispielsweise [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
1. Öffnen Sie im Oak-Repository das Statistik-MBean und überprüfen Sie, ob einer der Werte für `ObservationQueueMaxLength` mehr als 10.000 beträgt.

   * Bei normalem Betrieb wird dieser Höchstwert letztendlich auf null reduziert (insbesondere im Abschnitt `per second`). Überprüfen Sie daher, ob der Sekundenwert für `ObservationQueueMaxLength` 0 beträgt.
   * Falls die Werte 10.000 oder mehr betragen und ständig steigen, deutet dies darauf hin, dass mindestens eine Warteschlange nicht so schnell verarbeitet werden kann wie neue Änderungen (Commits) erfolgen.
   * Jede Beobachtungswarteschlange hat einen Grenzwert (standardmäßig 10,000). Wenn dieser Grenzwert erreicht ist, verschlechtert sich die Verarbeitung der Warteschlange.
   * Bei Verwendung von MongoMK verschlechtert sich die interne Leistung des Oak-Cache mit zunehmender Warteschlangengröße. Diese Korrelation zeigt sich in der größeren `missRate` beim `DocChildren`-Cache im Statistik-MBean `Consolidated Cache`.

1. Folgende Vorgehensweise ist empfohlen, um das Überschreiten der akzeptablen Grenzwerte für die Überwachungswarteschlange zu vermeiden:

   * Reduzieren Sie die konstante Commit-Rate. Kurzfristige Commit-Spitzen sind akzeptabel, aber die konstante Rate muss reduziert werden.
   * Vergrößern Sie den `DiffCache` wie unter [Tipps zur Leistungsoptimierung > Mongo-Speicheroptimierung > Dokument-Cache-Größe](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html#main-pars_text_3) beschrieben.

## Erkennen und Beheben von Unterbrechungen beim Neuindizierungsvorgang {#identifying-and-remediating-a-stuck-re-indexing-process}

Die Neuindizierung gilt unter zwei Bedingungen als „vollständig unterbrochen“:

* Die Neuindizierung ist sehr langsam. In den Protokolldateien wird kein wirklicher Fortschritt bei der Anzahl der durchsuchten Knoten erfasst.

   * Beispiel: Falls innerhalb einer Stunde keine Meldungen erfolgen oder der Fortschritt so langsam ist, dass der Vorgang mindestens eine Woche dauert.

* Die Neuindizierung hängt in einer endlosen Schleife, wenn wiederholte Ausnahmen in den Protokolldateien des Indizierungs-Thread angezeigt werden (beispielsweise `OutOfMemoryException`). Die Wiederholung der gleichen Ausnahmen im Protokoll deutet auf Oak-Versuche hin, die gleichen Daten wiederholt zu indizieren, wobei immer der gleiche Fehler auftritt.

Gehen Sie wie folgt vor, um einen unterbrochenen Neuindizierungsvorgang zu identifizieren und zu beheben:

1. Um die Ursache einer unterbrochenen Indizierung zu finden, benötigen Sie folgende Informationen:

   * Erfassen Sie 5 Minuten lang Thread-Dumps, eine Thread-Dump alle 2 Sekunden.
   * [Legen Sie DEBUG-Stufen und Protokolle für die Appender](/help/sites-deploying/configure-logging.md) fest.

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

   * Durch Neustarten von AEM kann das Problem im Fall von hohen gleichzeitigen Lasten (überlaufende Überwachungswarteschlange oder Ähnliches) eventuell behoben werden.
   * Wenn ein Neustart das Problem nicht behebt, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/marketing-cloud/contact-support.html) und geben Sie alle in Schritt 1 erfassten Informationen an.

## Sicheres Abbrechen der asynchronen Neuindizierung {#safely-aborting-asynchronous-re-indexing}

Die Neuindizierung kann sicher über die Index-Spuren `async, async-reindex` und `ulltext-async` (`IndexStats`-MBean) abgebrochen, d. h. vor dem Abschluss gestoppt werden. Weitere Informationen finden Sie auch in der Dokumentation zu Apache Oak im Abschnitt [Abbrechen der Neuindizierung](https://jackrabbit.apache.org/oak/docs/query/indexing.html#abort-reindex). Berücksichtigen Sie zusätzlich Folgendes:

* Die Neuindizierung von Lucene-Indizes und Lucene-Eigenschaftenindizes kann abgebrochen werden, da sie asynchron ist.
* Die Neuindizierung von Oak-Eigenschaftenindizes kann nur abgebrochen werden, wenn sie über das `PropertyIndexAsyncReindexMBean` initiiert wurde.

Um die Neuindizierung sicher abzubrechen, führen Sie folgende Schritte aus:

1. Identifizieren Sie das indexStats-MBean, das die Neuindizierungsspur steuert, die Sie stoppen möchten.

   * Navigieren Sie über die JMX-Konsole zum gewünschten IndexStats-MBean. Wechseln Sie dazu entweder zu „AEM-OSGi-Web-Konsole“ > „Haupt“ > „JMX“ oder zu https://&lt;Host>:&lt;Port>/system/console/jmx (beispielsweise [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)).
   * Öffnen Sie das entsprechende IndexStats-MBean, je nach der Neuindizierungsspur, die Sie stoppen möchten (`async`, `async-reindex` oder `fulltext-async`).

      * Um die richtige Spur und die zugehörige IndexStats-MBean-Instanz zu ermitteln, durchsuchen Sie die Oak-Indexeigenschaft „async“. Die Eigenschaft „async“ enthält den Spurnamen: `async`, `async-reindex` oder `fulltext-async`.
      * Sie können auch über den AEM-Index-Manager in der Spalte „Asynchron“ auf die Spur zugreifen. Um auf den Index-Manager zuzugreifen, wechseln Sie zu „Vorgänge“ > „Diagnose“ > „Index-Manager“.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Rufen Sie den Befehl `abortAndPause()` auf dem entsprechenden `IndexStats`-MBean auf.
1. Markieren Sie die entsprechende Oak-Index-Definition, um zu verhindern, dass die Neuindizierung fortgesetzt wird, wenn die Index-Spur fortgesetzt wird.

   * Wenn Sie einen **vorhandenen** Index neu indizieren, setzen Sie die Eigenschaft für die Neuindizierung auf „false“.

      * `/oak:index/someExistingIndex@reindex=false`
   * Bei einem **neuen** Index gehen Sie wie folgt vor:

      * Setzen Sie die Type-Eigenschaft auf „disabled“

         * `/oak:index/someNewIndex@type=disabled`
      * oder entfernen Sie die Indexdefinition vollständig.

   Speichern Sie die Änderungen nach Beendigung des Vorgangs im Repository.

1. Setzen Sie dann die asynchrone Indizierung auf den abgebrochenen Index-Spuren fort.

   * Rufen Sie im `IndexStats`-MBean, das den`abortAndPause()`-Befehl in Schritt 2 ausgegeben hat, den `resume()`-Befehl auf.

## Verhindern der langsamen Neuindizierung {#preventing-slow-re-indexing}

Die Neuindizierung empfiehlt sich zu ruhigen Zeiten (also nicht während der Verarbeitung großer Inhaltsmengen) und idealerweise während eines Wartungsfensters, wenn die AEM-Last bekannt und unter Kontrolle ist. Vergewissern Sie sich außerdem, dass Ihre Neuindizierung nicht während anderer Wartungstätigkeiten stattfindet.
