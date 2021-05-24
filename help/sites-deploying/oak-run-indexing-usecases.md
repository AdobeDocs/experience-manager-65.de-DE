---
title: Oak-run.jar – Indizierungsanwendungsfälle
seo-title: Oak-run.jar – Indizierungsanwendungsfälle
description: Erfahren Sie mehr über die verschiedenen Anwendungsfälle für die Durchführung der Indizierung mit dem Oak-run-Tool.
seo-description: Erfahren Sie mehr über die verschiedenen Anwendungsfälle für die Durchführung der Indizierung mit dem Oak-run-Tool.
uuid: 3c50080d-1e0d-4886-8d37-269f06881eb4
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 084075b8-826d-4f27-9342-35f33368f24f
noindex: true
exl-id: d25e3070-080a-4594-8fdb-9f09164135fc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 87%

---

# Oak-run.jar – Indizierungsanwendungsfälle{#oak-run-jar-indexing-use-cases}

Oak-run unterstützt Indizierungen über die Befehlszeile, ohne dass diese über die JMX-Konsole von AEM ausgeführt werden müssen.

Die übergeordneten Vorteile der Verwendung des Oak-run.jar-Indexbefehls zur Verwaltung von Oak-Indizes sind:

1. Der Oak-run-Indexbefehl bietet ein neues Indizierungs-Tool für AEM 6.4.
1. Oak-run verkürzt die Neuindizierungszeit, was sich insbesondere bei großen Repositorys auszahlt.
1. Oak-run verringert den Ressourcenverbrauch während der Neuindizierung in AEM, was die Gesamtleistung des Systems verbessert.
1. Oak-run bietet eine Out-of-Band-Neuindizierung und unterstützt damit Szenarios, in denen die Produktion verfügbar sein muss und keine Wartungs- oder Ausfallzeiten eingeplant werden können.

In den folgenden Abschnitten finden Sie Beispielbefehle. Der Oak-run-Befehl „index“ unterstützt alle NodeStore- und BlobStore-Setups. Die folgenden Beispiele beziehen sich auf Setups mit FileDataStore und SegmentNodeStore.

## Anwendungsfall 1 - Prüfung der Indexkonsistenz {#usercase1indexconsistencycheck}

Dies ist ein Anwendungsfall, in dem der Index beschädigt wurde. In einigen Fällen ist es nicht möglich festzustellen, welcher Index beschädigt wurde. Hierzu stellt Adobe Tools für folgende Aufgaben bereit:

1. Konsistenzprüfungen aller Indizes und Erstellung eines Berichts über die gültigen und ungültigen Indizes. 
1. Das Tool kann auch verwendet werden, wenn kein Zugriff auf AEM möglich ist. 
1. Die Verwendung ist einfach.

Die Überprüfung auf beschädigte Indizes kann über den Vorgang `--index-consistency-check` durchgeführt werden:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Dadurch wird ein Bericht in `indexing-result/index-consistency-check-report.txt` generiert. Unten sehen Sie ein Beispiel für diesen Bericht:

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Vorteile {#uc1benefits}

Diese Tools können jetzt durch den Support und den Systemadministrator verwendet werden, um schnell zu ermitteln, welche Indizes beschädigt sind, um diese dann neu zu indizieren.

## Anwendungsfall 2 - Indexstatistiken {#usecase2indexstatistics}

Für die Diagnose von Problemen mit der Abfrageperformance benötigt Adobe häufig die vorhandene Indexdefinition sowie zu Indizes gehörende Statistiken aus dem Setup von Kunden. Bisher waren diese Informationen über mehrere Ressourcen verstreut. Um die Fehlerbehebung zu erleichtern, bietet Adobe Tools, die folgende Aufgaben durchführen:

1. Dump aller im System vorhandener Indexdefinitionen in einer einzigen JSON-Datei. 

1. Dump wichtiger Statistiken aus vorhandenen Indizes. 

1. Dump von Indexinhalten für Offline-Analysen. 

1. Kann auch verwendet werden, wenn kein Zugriff auf AEM möglich ist. 

Die obigen Vorgänge können jetzt mit den folgenden Indexbefehlen ausgeführt werden:

* `--index-info` - Sammelt und speichert verschiedene Statistiken im Zusammenhang mit den Indizes.

* `--index-definitions` - Sammelt und sichert Indexdefinitionen

* `--index-dump` - Dumps-Indexinhalt

Unten sehen Sie ein Beispiel dafür, wie der Befehl in der Praxis arbeitet:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

Die Berichte werden in `indexing-result/index-info.txt` und `indexing-result/index-definitions.json` generiert

Außerdem werden einige Informationen über die Web-Konsole bereitgestellt und befinden sich in der vom Dump erzeugten ZIP-Datei. Der Zugriff ist über folgende URL möglich:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Vorteile {#uc2benefits}

Dieses Werkzeug aktiviert die schnelle Sammlung aller erforderlichen Details, die mit Index- oder Abfrageproblemen zusammenhängen, und verkürzt die für das Extrahieren dieser Informationen benötigte Zeit.

## Anwendungsfall 3 - Neuindizierung {#usecase3reindexing}

Je nach [Szenario](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing) ist es in einigen Fällen notwendig, eine Neuindizierung durchzuführen. Zurzeit erfolgt die Neuindizierung durch Festlegen der `reindex`-Markierung auf `true` im Indexdefinitionsknoten über CRXDE oder über die Index Manager-Benutzeroberfläche. Nach dem Setzen des Flags wird die Neuindizierung asynchron ausgeführt.

Einige wichtige Aspekte der Neuindizierung:

* Die Neuindizierung verläuft in `DocumentNodeStore`-Setups weitaus langsamer als in `SegmentNodeStore`-Setups, in denen der gesamte Inhalt lokal gespeichert ist. 

* Während der Neuindizierung wird zurzeit der asynchrone Indexer blockiert, weshalb alle anderen asynchronen Indizes veralten, weil sie während der Indizierung nicht mehr aktualisiert werden. Wenn das System verwendet wird, kann es aus diesem Grund passieren, dass Benutzer keine aktuellen Ergebnisse sehen. 
* Bei der Neuindizierung muss das gesamte Repository durchlaufen werden, was eine hohe Verarbeitungslast für das AEM-Setup bedeuten und sich negativ auf die Benutzerfreundlichkeit auswirken kann.
* Für eine `DocumentNodeStore`-Installation, in der die Neuindizierung sehr lange dauern kann, muss die Indizierung komplett neu gestartet werden, falls die Verbindung zur Mongo-Datenbank während des Vorgangs unterbrochen wird.

* In manchen Fällen benötigt die Neuindizierung viel Zeit, weil eine Textextraktion stattfindet. Dies gilt vor allem für Setups mit vielen PDF-Dateien. Hier kann sich die für die Textextraktion erforderliche Zeit auf die für die Indizierung benötigte Zeit auswirken.

Um diese Ziele zu erreichen, unterstützt das Oak-run-Tool verschiedene Indizierungsmodi, die in den einzelnen Fällen verwendet werden können. Der Oak-run-Befehl „index“ bietet folgende Vorteile:

* **Out-of-Band-Neuindizierung** – Die Oak-run-Neuindizierung kann getrennt von einem ausgeführten AEM-Setup ausgeführt werden. Dies minimiert die Auswirkungen auf die verwendete AEM-Instanz. 

* **Out-of-Lane-Neuindizierung** – Die Neuindizierung hat keine Auswirkungen auf Indizierungsvorgänge. Dies bedeutet, dass der asynchrone Indexer andere Indizes weiterhin indizieren kann. 

* **Vereinfachte Neuindizierung für DocumentNodeStore-Installationen** – Für `DocumentNodeStore`-Installationen kann die Neuindizierung mit einem einzigen Befehl ausgeführt werden, der sicherstellt, dass die Neuindizierung auf die optimalste Weise erfolgt.

* **Unterstützt die Aktualisierung der Indexdefinitionen und das Erstellen neuer Indexdefinitionen** 

### Neuindizierung – DocumentNodeStore {#reindexdocumentnodestore}

Für `DocumentNodeStore`-Installationen kann die Neuindizierung über einen einzelnen Oak-run-Befehl ausgeführt werden:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Dies bietet die folgenden Vorteile

* Minimale Auswirkung auf das Ausführen von AEM-Instanzen. Die meisten Lesevorgänge können von Sekundärservern ausgeführt werden und ausgeführte AEM-Caches sind nicht von all den für die Neuindizierung erforderlichen Durchläufen betroffen. 
* Benutzer können über die Option `--index-definitions-file` auch eine JSON eines neuen oder aktualisierten Index bereitstellen.

### Neuindizierung – SegmentNodeStore {#reindexsegmentnodestore}

Für `SegmentNodeStore`-Installationen kann die Neuindizierung auf eine der folgenden Weisen durchgeführt werden:

#### Online-Neuindizierung – SegmentNodeStore {#onlinereindexsegmentnodestore}

Das übliche Verfahren, bei dem das Flag `reindex` gesetzt wird.

#### Online-Neuindizierung – SegmentNodeStore – Die AEM-Instanz wird ausgeführt {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

In `SegmentNodeStore`-Installationen kann nur ein Prozess im Lese-/Schreibmodus auf Segmentdateien zugreifen. Aus diesem Grund sind für einige Vorgänge der Oak-run-Indizierung weitere manuelle Schritte erforderlich.

Hierzu gehören:

1. Schritttext
1. Verbinden Sie `oak-run` mit dem von AEM verwendeten Repository im schreibgeschützten Modus und führen Sie die Neuindizierung durch. Beispiel: 

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Importieren Sie nach dem Ausführen des obigen Befehls die erstellten Indexdateien mit dem Vorgang `IndexerMBean#importIndex` aus dem Pfad, unter dem Oak-run die Indexdateien gespeichert hat.

In diesem Szenario ist es nicht erforderlich, den AEM-Server zu stoppen oder eine neue Instanz bereitzustellen. Da für die Indizierung jedoch das gesamte Repository durchlaufen werden muss, erhöht sich die E/A-Last der Installation, was sich negativ auf die Performance auswirkt.

#### Online-Neuindizierung – SegmentNodeStore – Die AEM-Instanz ist beendet {#onlinereindexsegmentnodestoreaeminstanceisdown}

Für `SegmentNodeStore`-Installationen kann die Neuindizierung über einen einzigen Oak-run-Befehl ausgeführt werden: Die AEM-Instanz muss allerdings heruntergefahren werden.

Sie können die Neuindizierung mit dem folgenden Befehl auslösen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

Der Unterschied zwischen diesem und dem oben erläuterten Ansatz besteht darin, dass das Erstellen des Checkpoints und das Importieren des Index automatisch erfolgen. Der Nachteil besteht darin, dass AEM während des Prozesses beendet sein muss.

#### Out-of-Band-Neuindizierung – SegmentNodeStore {#outofbandreindexsegmentnodestore}

In diesem Szenario können Sie die Neuindizierung in einem geklonten Setup durchführen, um die Auswirkungen auf die laufende AEM-Instanz zu minimieren:

1. Erstellen Sie den Checkpoint über einen JMX-Vorgang. Hierzu können Sie in der [JMX-Konsole](/help/sites-administering/jmx-console.md) nach `CheckpointManager` suchen. Klicken Sie dann auf den Vorgang **createCheckpoint(long p1)** und verwenden Sie einen hohen Wert für die Gültigkeit in Sekunden (z. B. **2592000**).
1. Kopieren Sie den Ordner `crx-quickstart` auf einen neuen Computer.
1. Führen Sie die Neuindizierung über den Oak-run-Befehl „index“ durch. 

1. Kopieren Sie die generierten Indexdateien auf den AEM-Server. 

1. Importieren Sie die Indexdateien über JMX. 

In diesem Szenario wird davon ausgegangen, dass der Zugriff auf den Datenspeicher in einer anderen Instanz möglich ist. Dies ist nicht möglich, wenn `FileDataStore` in einer Cloud-basierten Speicherlösung wie EBS platziert ist. Dies schließt das Szenario aus, in dem `FileDataStore` ebenfalls geklont wird. Wenn die Indexdefinition keine Volltextindizierung durchführt, ist kein Zugriff auf `DataStore` erforderlich.

## Anwendungsfall 4 – Aktualisieren der Indexdefinitionen {#usecase4updatingindexdefinitions}

Zurzeit können Sie Änderungen der Indexdefinitionen über das Paket [ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) versenden. Dies ermöglicht den Versand der Indexdefinitionen über das Inhaltspaket, das später neu indiziert werden muss, indem das Flag `reindex` auf `true` gesetzt wird.

Dies funktioniert gut für kleinere Installationen, bei denen die Neuindizierung nicht viel Zeit in Anspruch nimmt. Bei sehr großen Repositorys benötigt die Neuindizierung jedoch erheblich mehr Zeit. Für diese Fälle kann jetzt das Oak-run-Tool für die Indizierung genutzt werden.

Oak-run unterstützt jetzt die Bereitstellung von Indexdefinitionen im JSON-Format und das Erstellen des Index im Out-of-Band-Modus, in dem keine Änderungen an einer Liveinstanz ausgeführt werden.

Für diesen Anwendungsfall kommt der folgende Prozess zum Tragen:

1. Ein Entwickler aktualisiert die Indexdefinitionen auf einer lokalen Instanz und generiert dann eine JSON-Indexdefinitionsdatei über die Option `--index-definitions` .

1. Die aktualisierte JSON-Datei erhält der Systemadministrator. 
1. Der Systemadministrator verfolgt den Out-of-Band-Ansatz und bereitet den Index in einer anderen Installation vor. 
1. Sobald dies abgeschlossen ist, werden die erstellten Indexdateien in eine laufende AEM-Installation importiert.
