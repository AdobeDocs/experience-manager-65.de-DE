---
title: Verwenden der Offline-Neuindizierung, um Ausfallzeiten während eines Upgrades zu reduzieren
description: Erfahren Sie, wie Sie die Offline-Neuindizierungsmethode verwenden können, um den Systemausfall bei einem AEM-Upgrade zu minimieren.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
feature: Upgrading
exl-id: 85bc041e-0ab1-42de-8bcc-c98a175d7494
source-git-commit: a5f3e33a6abe7ac1bbd610a8528fd599d1ffd2aa
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 100%

---

# Verwenden der Offline-Neuindizierung, um Ausfallzeiten während eines Upgrades zu reduzieren {#offline-reindexing-to-reduce-downtime-during-upgrades}

## Einführung {#introduction}

Eine der Hauptschwierigkeiten beim Upgrade von Adobe Experience Manager ist die Ausfallzeit der Autorenumgebung bei einem In-Place-Upgrade. Inhaltsautoren können während eines Upgrades nicht auf die Umgebung zugreifen. Daher ist es wünschenswert, die für die Durchführung des Upgrades benötigte Zeit zu minimieren Bei großen Repositorys, insbesondere bei AEM Assets-Projekten, die in der Regel über große Datenspeicher und eine hohe Anzahl von Asset-Uploads pro Stunde verfügen, dauert die Neuindizierung von Oak-Indizes einen erheblichen Prozentsatz der Upgrade-Zeit.

In diesem Abschnitt wird beschrieben, wie Sie mit dem Oak-run-Tool das Repository **vor** der Durchführung des Upgrades neu indizieren und so die Ausfallzeit während des eigentlichen Upgrades reduzieren können. Die angezeigten Schritte können auf [Lucene](https://jackrabbit.apache.org/oak/docs/query/lucene.html)-Indizes für Versionen AEM 6.4 und höher angewendet werden.

## Übersicht {#overview}

In neuen Versionen von AEM werden Änderungen an Oak-Indexdefinitionen eingeführt, wenn der Funktionssatz erweitert wird. Änderungen an den Oak-Indizes erzwingen eine Neuindizierung beim Upgrade der AEM-Instanz. Bei der Bereitstellung von Assets ist eine Neuindizierung aufwendig, da Text in Assets (z. B. Text in einer PDF-Datei) extrahiert und indiziert wird. Bei MongoMK-Repositorys werden die Daten über das Netzwerk vorgehalten, was den Zeitaufwand für die Neuindizierung weiter erhöht.

Das Problem, mit dem die meisten Kunden während eines Upgrades konfrontiert sind, ist die Verringerung der Ausfallzeiten. Die Lösung besteht darin, die Aktivität „Neuindizierung“ während des Upgrades zu **überspringen**. Dies kann erreicht werden, indem die neuen Indizes **vor** dem Upgrade erstellt und dann während des Upgrades einfach importiert werden.

## Ansatz {#approach}

![offline-reindexing-upgrade-text-extract](assets/offline-reindexing-upgrade-process.png)

Die Idee ist, den Index vor dem Upgrade zu erstellen, und zwar anhand der Indexdefinitionen der Ziel-AEM-Version unter Verwendung des [Oak-run](/help/sites-deploying/indexing-via-the-oak-run-jar.md)-Tools. Das obige Diagramm zeigt den Ansatz der Offline-Neuindizierung.

Außerdem ist dies die Reihenfolge der Schritte, wie sie in dem Ansatz beschrieben sind:

1. Zuerst wird der Text aus den Binärdateien extrahiert
2. Ziel-Indexdefinitionen werden erstellt
3. Offline-Indizes werden erstellt
4. Die Indizes werden dann während des Upgrade-Prozesses importiert

### Textextraktion {#text-extraction}

Um eine vollständige Indizierung in AEM zu ermöglichen, wird Text aus Binärdateien wie PDF extrahiert und dem Index hinzugefügt. Dies ist in der Regel ein aufwendiger Schritt im Indizierungsprozess. Die Textextraktion ist ein Optimierungsschritt, der insbesondere für die Neuindizierung von Asset-Repositorys empfohlen wird, da in diesen eine große Anzahl von Binärdateien gespeichert ist.

![offline-reindexing-upgrade-text-extract](assets/offline-reindexing-upgrade-text-extraction.png)

Text aus im System gespeicherten Binärdateien kann mit dem Oak-run-Tool und der Bibliothek tika extrahiert werden. Vor dem Upgrade kann ein Klon des Produktionssystems erstellt werden, der für diesen Textextraktionsprozess verwendet werden kann. Dieser Prozess erstellt dann den Textspeicher, indem er die folgenden Schritte durchläuft:

**1. Durchlaufen des Repository und Erfassen von Details der Binärdateien**

Dieser Schritt erzeugt eine CSV-Datei mit einem Tupel von Binärdateien, das einen Pfad und eine Blob-ID enthält.

Führen Sie den folgenden Befehl in dem Verzeichnis aus, in dem Sie den Index erstellen möchten. Im folgenden Beispiel wird von dem Basisverzeichnis des Repositorys ausgegangen.

```
java java -jar oak-run.jar tika <nodestore path> --fds-path <datastore path> --data-file text-extraction/oak-binary-stats.csv --generate
```

Wo `nodestore path` die `mongo_ur` oder `crx-quickstart/repository/segmentstore/` ist

Verwenden Sie den Parameter `--fake-ds-path=temp` anstelle von `–fds-path`, um den Prozess zu beschleunigen.

**2. Verwenden Sie den binären Textspeicher wieder, der im vorhandenen Index verfügbar ist.**

Entladen Sie die Indexdaten aus dem bestehenden System und extrahieren Sie den Textspeicher.

Sie können die vorhandenen Indexdaten mit dem folgenden Befehl entladen:

```
java -jar oak-run.jar index <nodestore path> --fds-path=<datastore path> --index-dump
```

Wo `nodestore path` die `mongo_ur` oder `crx-quickstart/repository/segmentstore/` ist

Verwenden Sie dann den obigen Index-Dump, um den Speicher aufzufüllen:

```
java -jar oak-run.jar tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --index-dir ./indexing-result/index-dumps/<oak-index-name>/data populate
```

Wo `oak-index-name` der Name des Volltextindex ist, z. B. „lucene“.

**3. Ausführen des Textextraktionsvorgangs mit der Tika-Bibliothek für die im obigen Schritt ausgelassenen Binärdateien**

```
java -cp oak-run.jar:tika-app-1.21.jar org.apache.jackrabbit.oak.run.Main tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --fds-path <datastore path> extract
```

Wo `datastore path` der Pfad zum binären Datenspeicher ist.

Der erstellte Textspeicher kann aktualisiert und für künftige Neuindizierungsszenarien wiederverwendet werden.

Weitere Einzelheiten über den Textextraktionsprozess finden Sie in der [Dokumentation zu Oak-run](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html).

### Offline-Neuindizierung {#offline-reindexing}

![offline-reindexing-upgrade-offline-reindexing](assets/offline-reindexing-upgrade-offline-reindexing.png)

Erstellen Sie den Lucene-Index vor dem Upgrade offline. Bei der Verwendung von MongoMK wird empfohlen, es direkt auf einem der MongoMk-Knoten laufen zu lassen, da dies einen zu großen Netzwerk-Overhead vermeidet.

Um den Index offline zu erstellen, führen Sie die folgenden Schritte aus:

**1. Generieren von Oak Lucene-Indexdefinitionen für die AEM-Zielversion**

Entladen Sie die vorhandenen Indexdefinitionen. Geänderte Indexdefinitionen wurden mit dem Adobe Granite Repository-Paket der AEM-Zielversion und Oak-run erzeugt.

Führen Sie diesen Befehl aus, um die Indexdefinition aus der AEM-**Quell**-Instanz zu entladen:

>[!NOTE]
>
>Weitere Einzelheiten zum Entladen von Indexdefinitionen finden Sie in der [Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#async-index-data).

```
java -jar oak-run.jar index --fds-path <datastore path> <nodestore path> --index-definitions
```

Wobei `datastore path` und `nodestore path` aus der AEM-**Quell**-Instanz stammen.

Generieren Sie dann Indexdefinitionen aus der AEM-**Ziel**-Version unter Verwendung des Granite-Repository-Pakets der Zielversion.

```
java -cp oak-run.jar:bundle-com.adobe.granite.repository.jar org.apache.jackrabbit.oak.index.IndexDefinitionUpdater --in indexing-definitions_source.json --out merge-index-definitions_target.json --initializer com.adobe.granite.repository.impl.GraniteContent
```

>[!NOTE]
>
>Das oben beschriebene Verfahren zur Erstellung von Indexdefinitionen wird erst ab der Version `oak-run-1.12.0` unterstützt. Das Targeting erfolgt mithilfe des Granite-Repository-Pakets `com.adobe.granite.repository-x.x.xx.jar`.

Die oben genannten Schritte erstellen eine JSON-Datei mit dem Namen `merge-index-definitions_target.json`, die Indexdefinition.

**2. Erstellen eines Checkpoints im Repository**

Erstellen Sie einen Checkpoint in der AEM-Produktions-**Quell**-Instanz mit einer langen Lebensdauer. Dies sollte vor dem Klonen des Repositorys geschehen.

Gehen Sie über die JMX-Konsole von `http://serveraddress:serverport/system/console/jmx` nach `CheckpointMBean` und erstellen Sie einen Checkpoint mit einer ausreichend langen Lebensdauer (z. B. 200 Tage). Rufen Sie dazu `CheckpointMBean#createCheckpoint` mit `17280000000` als Argument für die Lebenszeitdauer in Millisekunden auf.

Kopieren Sie anschließend die neu erstellte Checkpoint-ID und validieren Sie die Lebensdauer mit JMX `CheckpointMBean#listCheckpoints`.

>[!NOTE]
>
>Dieser Checkpoint wird gelöscht, wenn der Index später importiert wird.

Weitere Einzelheiten finden Sie in der Oak-Dokumentation im Abschnitt [Checkpoint-Erstellung](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#out-of-band-create-checkpoint).

**Durchführen der Offline-Indizierung für die generierten Indexdefinitionen**

Die Neuindizierung von Lucene kann offline mit Oak-run durchgeführt werden. Dieser Prozess erstellt Indexdaten auf der Festplatte unter `indexing-result/indexes`. Er schreibt **nicht** in das Repository und erfordert daher nicht das Anhalten der laufenden AEM-Instanz. Der erstellte Textspeicher wird in diesen Prozess eingespeist:

```
java -Doak.indexer.memLimitInMB=500 -jar oak-run.jar index <nodestore path> --reindex --doc-traversal-mode --checkpoint <checkpoint> --fds-path <datastore path> --index-definitions-file merge-index-definitions_target.json --pre-extracted-text-dir text-extraction/store

Sample <checkpoint> looks like r16c85700008-0-8
—fds-path: path to data store.
--pre-extracted-text-dir: Directory of pre-extracted text.
merge-index-definitions_target: JSON file having merged definitions for the target AEM instance. indexes in this file will be re-indexed.
```

Die Verwendung des `--doc-traversal-mode`-Parameters ist bei MongoMK-Installationen praktisch, da er die Neuindizierung erheblich beschleunigt, indem er Repository-Inhalte in eine lokale flache Datei spoolt. Allerdings wird dafür zusätzlicher Speicherplatz benötigt, der doppelt so groß ist wie das Repository.

Im Falle von MongoMK kann dieser Prozess beschleunigt werden, wenn dieser Schritt in einer Instanz ausgeführt wird, die näher an der MongoDB-Instanz liegt. Wenn er auf demselben Computer ausgeführt wird, kann ein zu großer Netzwerk-Overhead vermieden werden.

Weitere technische Details finden Sie in der [Oak-run-Dokumentation zur Indizierung](Https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html).

### Importieren von Indizes {#importing-indexes}

In AEM 6.4 und neueren Versionen verfügt AEM über die integrierte Fähigkeit, Indizes bei der Startsequenz von einem Datenträger zu importieren. Der Ordner `<repository>/indexing-result/indexes` wird beim Start auf das Vorhandensein von Indexdaten überwacht. Sie können den vorab erstellten Index während des [Upgrade-Prozesses](in-place-upgrade.md#performing-the-upgrade) in den oben genannten Speicherort kopieren, bevor Sie mit der neuen Version des AEM-**Ziel**-Jar beginnen. AEM importiert es in das Repository und entfernt den entsprechenden Checkpoint aus dem System. Eine Neuindizierung wird somit vollständig vermieden.

## Zusätzliche Tipps und Fehlerbehebung {#troubleshooting}

Nachfolgend finden Sie einige hilfreiche Tipps und Anleitungen zur Fehlerbehebung.

### Verringerung der Auswirkungen auf das Live-Produktionssystem {#reduce-the-impact-on-the-live-production-system}

Es wird empfohlen, das Produktionssystem zu klonen und den Offline-Index mithilfe des Klons zu erstellen. Dadurch werden mögliche Auswirkungen auf das Produktionssystem vermieden. Der für den Indeximport erforderliche Checkpoint muss jedoch im Produktionssystem vorhanden sein. Daher ist es wichtig, einen Checkpoint zu erstellen, bevor der Klon angelegt wird.

### Vorbereiten eines Runbooks und Testlauf {#prepare-a-runbook-and-trial-run}

Es wird empfohlen, ein [Runbook](https://docs.adobe.com/content/help/de/experience-manager-65/deploying/upgrading/upgrade-planning.html#building-the-upgrade-and-rollback-runbook) vorzubereiten und einige Testläufe durchzuführen, bevor das Upgrade in der Produktion ausgeführt wird.

### doc-traversal-mode mit Offline-Indizierung {#doc-traversal-mode-with-offline-indexing}

Die Offline-Indizierung erfordert mehrere Durchläufe durch das gesamte Repository. Bei MongoMK-Installationen erfolgt der Zugriff auf das Repository über das Netzwerk, was die Leistung des Indizierungsprozesses beeinträchtigt. Eine Option besteht darin, den Offline-Indizierungsprozess auf der MongoDB-Replik selbst auszuführen, wodurch der Netzwerk-Overhead entfällt. Eine weitere Möglichkeit ist die Verwendung des doc-traversal-mode.

Der doc-traversal-mode kann durch Hinzufügen des Befehlszeilenparameters `—doc-traversal` zum Befehl oak-run für die Offline-Indizierung angewendet werden. Dieser Modus spoolt eine Kopie des gesamten Repositorys auf der lokalen Festplatte als flache Datei und verwendet diese für die Indizierung.
