---
title: Oak-run.jar – Indizierungsanwendungsfälle
description: Erfahren Sie mehr über die verschiedenen Anwendungsfälle für die Indizierung mit dem Oak-run-Tool.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
noindex: true
exl-id: d25e3070-080a-4594-8fdb-9f09164135fc
source-git-commit: 2a97935a81cf9c0a1a832dd27b62d388805863e0
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 27%

---

# Oak-run.jar – Indizierungsanwendungsfälle{#oak-run-jar-indexing-use-cases}

Oak-run unterstützt Indizierungs-Anwendungsfälle über die Befehlszeile, ohne die Ausführung dieser Anwendungsfälle über AEM JMX-Konsole steuern zu müssen.

Die übergreifenden Vorteile bei der Verwendung des oak-run.jar-Befehls „index“ für die Verwaltung von Oak-Indizes:

1. Der Oak-run-Indexbefehl bietet ein neues Indizierungs-Toolset für AEM 6.4.
1. Oak-run verkürzt die Zeit bis zur Neuindizierung, wodurch die Neuindizierungszeiten in größeren Repositorys reduziert werden.
1. Oak-run reduziert den Ressourcenverbrauch während der Neuindizierung in AEM, was zu einer insgesamt besseren Systemleistung führt.
1. Oak-run bietet Out-of-Band-Neuindizierung und unterstützt Situationen, in denen die Produktion verfügbar sein muss und keine Wartung oder Ausfallzeiten tolerieren kann, die andernfalls für die Neuindizierung erforderlich wären.

In den folgenden Abschnitten finden Sie Beispielbefehle. Der Oak-run-Indexbefehl unterstützt alle NodeStore- und BlobStore-Setups. Die folgenden Beispiele beziehen sich auf Setups mit FileDataStore und SegmentNodeStore.

## Nutzungsszenario 1 - Prüfung der Indexkonsistenz {#usercase1indexconsistencycheck}

Dies ist ein Anwendungsfall im Zusammenhang mit Indexbeschädigung. Manchmal war es nicht möglich festzustellen, welche der Indizes beschädigt sind. Daher bietet Adobe Tools, die Folgendes ermöglichen:

1. Konsistenzprüfungen aller Indizes und Erstellung eines Berichts über die gültigen und ungültigen Indizes. 
1. Das Tool kann auch verwendet werden, wenn kein Zugriff auf AEM möglich ist. 
1. Die Verwendung ist einfach.

Die Überprüfung auf beschädigte Indizes kann über `--index-consistency-check` -Vorgang:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Dadurch wird ein Bericht in `indexing-result/index-consistency-check-report.txt`. Unten finden Sie einen Beispielbericht:

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

Diese Tools können jetzt vom Support und vom Systemadministrator verwendet werden, um schnell zu ermitteln, welche Indizes beschädigt sind, und sie dann neu indizieren.

## Anwendungsfall 2: Indexstatistiken {#usecase2indexstatistics}

Für die Diagnose einiger Fälle rund um die Abfrageleistung benötigte Adobe häufig eine vorhandene Indexdefinition und indexbezogene Statistiken aus der Kundeneinrichtung. Bisher wurden diese Informationen über mehrere Ressourcen verteilt. Um die Fehlerbehebung zu vereinfachen, hat Adobe Tools erstellt, die Folgendes ermöglichen:

1. Dump aller im System vorhandenen Indexdefinitionen in einer einzigen JSON-Datei;

1. Dump wichtiger Statistiken aus vorhandenen Indizes. 

1. Dump von Indexinhalten für Offline-Analysen. 

1. Kann auch verwendet werden, wenn AEM nicht verfügbar ist

Die oben genannten Vorgänge können jetzt über die folgenden Vorgangsindex-Befehle ausgeführt werden:

* `--index-info` – Sammelt verschiedene indexbezogene Statistiken und gibt deren Speicherinhalt aus

* `--index-definitions` – Sammelt Indexdefinitionen und gibt deren Speicherinhalt aus

* `--index-dump` – Gibt den Speicherinhalt von Indexinhalten aus

Unten sehen Sie ein Beispiel dafür, wie der Befehl in der Praxis arbeitet:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

Die Berichte werden in `indexing-result/index-info.txt` und `indexing-result/index-definitions.json` erstellt.

Darüber hinaus werden dieselben Details über die Web-Konsole bereitgestellt und wären Teil der Zip-Datei für die Konfiguration. Sie können unter folgendem Pfad darauf zugreifen:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Vorteile {#uc2benefits}

Diese Tools ermöglichen die schnelle Erfassung aller erforderlichen Details im Zusammenhang mit Indizierungs- oder Abfrageproblemen und verkürzen die Zeit, die mit dem Extrahieren dieser Informationen verbracht wird.

## Anwendungsfall 3: Neuindizierung {#usecase3reindexing}

Je nach [Szenarien](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing)manchmal muss eine Neuindizierung durchgeführt werden. Derzeit erfolgt die Neuindizierung durch Festlegen der `reindex` Markierung auf `true` im Indexdefinitionsknoten über CRXDE oder über die Index-Manager-Benutzeroberfläche. Nachdem das Flag gesetzt wurde, erfolgt die Neuindizierung asynchron.

Einige Hinweise zur Neuindizierung:

* Die Neuindizierung verläuft in `DocumentNodeStore`-Setups weitaus langsamer als in `SegmentNodeStore`-Setups, in denen der gesamte Inhalt lokal gespeichert ist. 

* Beim aktuellen Design wird der asynchrone Indexer blockiert, während die Neuindizierung erfolgt. Alle anderen asynchronen Indizes werden veraltet und werden während der Indizierung nicht aktualisiert. Wenn das System verwendet wird, sehen Benutzer daher möglicherweise keine aktuellen Ergebnisse.
* Bei der Neuindizierung muss das gesamte Repository durchlaufen werden, was eine hohe Verarbeitungslast für das AEM-Setup bedeuten und sich negativ auf die Benutzerfreundlichkeit auswirken kann.
* Für eine `DocumentNodeStore`-Installation, in der die Neuindizierung sehr lange dauern kann, muss die Indizierung komplett neu gestartet werden, falls die Verbindung zur Mongo-Datenbank während des Vorgangs unterbrochen wird.

* Manchmal kann die Neuindizierung aufgrund der Textextraktion lange dauern. Dies ist spezifisch für Setups mit vielen PDF-Dateien, bei denen sich die für die Textextraktion aufgewendete Zeit auf die Indizierungszeit auswirken kann.

Um diese Ziele zu erreichen, unterstützt das Oak-run-Index-Tool verschiedene Neuindizierungsmodi, die bei Bedarf verwendet werden können. Der oak-run-Indexbefehl bietet folgende Vorteile:

* **Out-of-Band-Neuindizierung** – Die Oak-run-Neuindizierung kann getrennt von einem ausgeführten AEM-Setup ausgeführt werden. Dies minimiert die Auswirkungen auf die verwendete AEM-Instanz. 

* **Out-of-Lane-Neuindizierung** - Die Neuindizierung erfolgt ohne Auswirkungen auf Indizierungsvorgänge. Dies bedeutet, dass der asynchrone Indexer andere Indizes weiterhin indizieren kann. 

* **Vereinfachte Neuindizierung für DocumentNodeStore-Installationen** – Für `DocumentNodeStore`-Installationen kann die Neuindizierung mit einem einzigen Befehl ausgeführt werden, der sicherstellt, dass die Neuindizierung auf die optimalste Weise erfolgt.

* **Unterstützt die Aktualisierung der Indexdefinitionen und das Erstellen neuer Indexdefinitionen** 

### Neuindizierung – DocumentNodeStore {#reindexdocumentnodestore}

Für `DocumentNodeStore` Die Neuindizierung von Installationen kann über einen einzigen Oak-run-Befehl erfolgen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Dies bietet die folgenden Vorteile

* Minimale Auswirkung auf AEM Instanzen. Die meisten Lesevorgänge können von sekundären Servern durchgeführt werden und laufende AEM Caches sind nicht negativ betroffen, da alle für die Neuindizierung erforderlichen Durchläufe durchlaufen werden.
* Benutzer können auch eine JSON-Datei eines neuen oder aktualisierten Index über die `--index-definitions-file` -Option.

### Neuindizierung – SegmentNodeStore {#reindexsegmentnodestore}

Für `SegmentNodeStore`-Installationen kann die Neuindizierung auf eine der folgenden Weisen durchgeführt werden:

#### Online-Neuindizierung – SegmentNodeStore {#onlinereindexsegmentnodestore}

Gehen Sie wie gewohnt vor, um die Neuindizierung durchzuführen, indem Sie `reindex` Markierung.

#### Online-Neuindizierung – SegmentNodeStore – Die AEM-Instanz wird ausgeführt {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

Für `SegmentNodeStore` installiert ist, kann nur ein Prozess auf Segmentdateien im Lese- und Schreibmodus zugreifen. Daher erfordern einige Vorgänge bei der Oak-run-Indizierung zusätzliche manuelle Schritte.

Dies würde Folgendes umfassen:

1. Schritttext
1. Verbinden Sie die `oak-run` auf dasselbe Repository zugreifen, das von AEM im schreibgeschützten Modus verwendet wird, und eine Indizierung durchführen. Ein Beispiel dafür, wie Sie dies erreichen:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Importieren Sie schließlich die erstellten Indexdateien über die `IndexerMBean#importIndex` -Vorgang aus dem Pfad, in dem oak-run die Indizierungsdateien nach dem Ausführen des obigen Befehls gespeichert hat.

In diesem Szenario müssen Sie den AEM-Server nicht stoppen oder eine neue Instanz bereitstellen. Da die Indizierung jedoch das Durchlaufen des gesamten Repositorys beinhaltet, würde sich die I/O-Belastung der Installation erhöhen und die Laufzeitleistung negativ beeinflussen.

#### Online-Neuindizierung - SegmentNodeStore - Die AEM Instanz ist beendet. {#onlinereindexsegmentnodestoreaeminstanceisdown}

Für `SegmentNodeStore` -Installationen, kann die Neuindizierung über einen einzigen Oak-run-Befehl erfolgen. Die AEM-Instanz muss jedoch heruntergefahren werden.

Sie können die Neuindizierung des Triggers mit dem folgenden Befehl durchführen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

Der Unterschied zwischen diesem und dem oben erläuterten Ansatz besteht darin, dass die Erstellung von Checkpoints und der Import von Indizes automatisch erfolgen. Der Nachteil ist, dass AEM während des Prozesses ausfallen muss.

#### Out-Band-Neuindizierung - SegmentNodeStore {#outofbandreindexsegmentnodestore}

In diesem Anwendungsfall können Sie eine Neuindizierung an einem geklonten Setup durchführen, um die Auswirkungen auf die laufende AEM zu minimieren:

1. Erstellen Sie einen Checkpoint über einen JMX-Vorgang. Hierzu können Sie in der [JMX-Konsole](/help/sites-administering/jmx-console.md) nach `CheckpointManager` suchen. Klicken Sie dann auf die **createCheckpoint(long p1)** Vorgang mit einem hohen Ablaufwert in Sekunden (z. B. **259200**).
1. Kopieren Sie den Ordner `crx-quickstart` auf einen neuen Computer.
1. Führen Sie die Neuindizierung über den Oak-run-Indexbefehl durch.

1. Kopieren Sie die generierten Indexdateien auf den AEM-Server. 

1. Importieren Sie die Indexdateien über JMX.

In diesem Anwendungsfall wird davon ausgegangen, dass der Datenspeicher auf einer anderen Instanz zugänglich ist, was unter Umständen nicht möglich ist, wenn `FileDataStore` wird auf einer Cloud-basierten Speicherlösung wie EBS platziert. Dies schließt das Szenario aus, in dem auch `FileDataStore` geklont wird. Wenn die Indexdefinition keine Volltextindizierung durchführt, ist kein Zugriff auf den `DataStore` erforderlich.

## Anwendungsfall 4 – Aktualisieren der Indexdefinitionen {#usecase4updatingindexdefinitions}

Derzeit können Sie Indexdefinitionsänderungen über [ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) Paket. Dadurch kann der Versand der Indexdefinitionen über das Inhaltspaket erfolgen, was später eine Neuindizierung erfordert, indem die Variable `reindex` Markierung auf `true`.

Dies funktioniert bei kleineren Installationen, bei denen die Neuindizierung nicht lange dauert. Bei großen Repositorys erfolgt die Neuindizierung jedoch über einen wesentlich größeren Zeitraum. Für solche Fälle können wir jetzt das Oak-Run-Index-Tool verwenden.

Oak-run unterstützt jetzt die Bereitstellung von Indexdefinitionen im JSON-Format und die Erstellung von Index im Out-of-Band-Modus, bei dem keine Änderungen an einer Live-Instanz vorgenommen werden.

Der für diesen Anwendungsfall zu berücksichtigende Prozess ist:

1. Ein Entwickler aktualisiert die Indexdefinitionen auf einer lokalen Instanz und generiert dann eine JSON-Indexdefinitionsdatei über die `--index-definitions` option

1. Die aktualisierte JSON-Datei erhält die bzw. der Systemadmin. 
1. Die bzw. der Systemadmin verfolgt den Out-of-Band-Ansatz und bereitet den Index in einer anderen Installation vor. 
1. Nach Abschluss dieses Vorgangs werden die generierten Indexdateien bei einer laufenden AEM-Installation importiert.
