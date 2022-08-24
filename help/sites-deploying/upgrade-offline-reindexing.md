---
title: Verwenden der Offline-Neuindizierung, um Ausfallzeiten während eines Upgrades zu reduzieren
description: Erfahren Sie, wie Sie die Offline-Neuindizierungsmethode verwenden können, um den Systemausfall bei einer AEM Aktualisierung zu reduzieren.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
feature: Upgrading
exl-id: 85bc041e-0ab1-42de-8bcc-c98a175d7494
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 1%

---

# Verwenden der Offline-Neuindizierung, um Ausfallzeiten während eines Upgrades zu reduzieren {#offline-reindexing-to-reduce-downtime-during-upgrades}

## Einführung    {#introduction}

Eine der Hauptschwierigkeiten bei der Aktualisierung von Adobe Experience Manager ist die Ausfallzeit der Autorenumgebung bei einer ersetzenden Aktualisierung. Inhaltsautoren können während eines Upgrades nicht auf die Umgebung zugreifen. Daher ist es wünschenswert, die für die Durchführung des Upgrades benötigte Zeit zu minimieren. Bei großen Repositorys, insbesondere bei AEM Assets-Projekten, die in der Regel über große Datenspeicher und eine hohe Anzahl von Asset-Uploads pro Stunde verfügen, dauert die Neuindizierung von Oak-Indizes einen erheblichen Prozentsatz der Aktualisierungszeit.

In diesem Abschnitt wird beschrieben, wie Sie mit dem Oak-run-Tool das Repository neu indizieren. **before** Führen Sie das Upgrade durch und reduzieren Sie so die Ausfallzeit während des eigentlichen Upgrades. Die angezeigten Schritte können auf [Lucene](https://jackrabbit.apache.org/oak/docs/query/lucene.html) Indizes für Versionen AEM 6.4 und höher.

## Übersicht {#overview}

Neue Versionen der AEM führen Änderungen an Oak-Indexdefinitionen ein, wenn der Funktionssatz erweitert wird. Änderungen an den Oak-Indizes erzwingen eine Neuindizierung, wenn die AEM Instanz aktualisiert wird. Die Neuindizierung ist für Asset-Bereitstellungen teuer, da Text in Assets (z. B. Text in der PDF-Datei) extrahiert und indiziert wird. Bei MongoMK-Repositorys werden Daten über das Netzwerk persistiert, was die Dauer der Neuindizierung weiter erhöht.

Das Problem, mit dem die meisten Kunden während eines Upgrades konfrontiert sind, besteht darin, das Ausfallzeitfenster zu reduzieren. Die Lösung besteht darin, **überspringen** die Neuindizierungsaktivität während des Upgrades. Dies kann durch die Erstellung der neuen Indizes erreicht werden **before** , um das Upgrade durchzuführen, und importieren Sie es dann einfach während des Upgrades.

## Ansatz {#approach}

![offline-reindexing-upgrade-text-extract](assets/offline-reindexing-upgrade-process.png)

Die Idee besteht darin, den Index vor der Aktualisierung anhand der Indexdefinitionen der Ziel-AEM-Version mithilfe der [Oak-run](/help/sites-deploying/indexing-via-the-oak-run-jar.md) -Tool. Das obige Diagramm zeigt den Offline-Neuindizierungsansatz.

Darüber hinaus ist dies die Reihenfolge der Schritte, wie im Ansatz beschrieben:

1. Text aus Binärdateien wird zuerst extrahiert
2. Zielindex-Definitionen werden erstellt
3. Offline-Indizes werden erstellt
4. Die Indizes werden dann während des Aktualisierungsprozesses importiert

### Textextraktion {#text-extraction}

Um die vollständige Indizierung in AEM zu aktivieren, wird Text aus Binärdateien wie PDF extrahiert und zum Index hinzugefügt. Dies ist normalerweise ein teurer Schritt im Indizierungsprozess. Die Textextraktion ist ein Optimierungsschritt, der insbesondere für die Neuindizierung von Asset-Repositorys empfohlen wird, da dort eine große Anzahl von Binärdateien gespeichert wird.

![offline-reindexing-upgrade-text-extract](assets/offline-reindexing-upgrade-text-extraction.png)

Der im System gespeicherte Text aus Binärdateien kann mithilfe des Oak-run-Tools mit der tika-Bibliothek extrahiert werden. Ein Klon der Produktionssysteme kann vor der Aktualisierung genommen werden und für diesen Textextraktionsprozess verwendet werden. Dieser Prozess erstellt dann den Textspeicher, indem Sie die folgenden Schritte ausführen:

**1. Repository durchlaufen und Details der Binärdateien erfassen**

Dieser Schritt erzeugt eine CSV-Datei mit mehreren Binärdateien, die einen Pfad und eine Blob-ID enthalten.

Führen Sie den folgenden Befehl aus dem Verzeichnis aus, aus dem Sie den Index erstellen möchten. Im folgenden Beispiel wird von dem Basisverzeichnis des Repositorys ausgegangen.

```
java java -jar oak-run.jar tika <nodestore path> --fds-path <datastore path> --data-file text-extraction/oak-binary-stats.csv --generate
```

Wo `nodestore path` ist die `mongo_ur` oder `crx-quickstart/repository/segmentstore/`

Verwenden Sie die `--fake-ds-path=temp` Parameter anstelle von `–fds-path` um den Prozess zu beschleunigen.

**2. Verwenden Sie den binären Textspeicher, der im vorhandenen Index verfügbar ist.**

Ziehen Sie die Indexdaten aus dem vorhandenen System und extrahieren Sie den Textspeicher.

Sie können die vorhandenen Indexdaten mit dem folgenden Befehl ablegen:

```
java -jar oak-run.jar index <nodestore path> --fds-path=<datastore path> --index-dump
```

Wo `nodestore path` ist die `mongo_ur` oder `crx-quickstart/repository/segmentstore/`

Verwenden Sie dann die obige Indexablage, um den Store zu füllen:

```
java -jar oak-run.jar tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --index-dir ./indexing-result/index-dumps/<oak-index-name>/data populate
```

Wo `oak-index-name` ist der Name des Volltextindex, z. B. &quot;lucene&quot;.

**3. Führen Sie den Textextraktionsvorgang mit der Tika-Bibliothek für die im obigen Schritt ausgeblendeten Binärdateien aus.**

```
java -cp oak-run.jar:tika-app-1.21.jar org.apache.jackrabbit.oak.run.Main tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --fds-path <datastore path> extract
```

Wo `datastore path` ist der Pfad zum binären Datenspeicher.

Der erstellte Textspeicher kann in Zukunft für Neuindizierungsszenarien aktualisiert und wiederverwendet werden.

Weitere Informationen zum Textextraktionsprozess finden Sie unter [Oak-run-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html).

### Offline-Neuindizierung {#offline-reindexing}

![offline-reindexing-upgrade-offline-reindexing](assets/offline-reindexing-upgrade-offline-reindexing.png)

Erstellen Sie den Lucene-Index offline vor dem Upgrade. Bei Verwendung von MongoMK wird empfohlen, das Programm direkt auf einem der MongoMk-Knoten auszuführen, da dadurch Netzwerkaufwand vermieden werden.

Gehen Sie wie folgt vor, um den Index offline zu erstellen:

**1. Generieren von Oak Lucene-Indexdefinitionen für die AEM Zielversion**

Dump der vorhandenen Indexdefinitionen. Indexdefinitionen, die geändert wurden, wurden mithilfe des Adobe Granite-Repository-Bundles der Ziel-AEM-Version und oak-run generiert.

So legen Sie die Indexdefinition aus der **source** Führen Sie AEM Instanz diesen Befehl aus:

>[!NOTE]
>
>Weitere Informationen zu den Definitionen der Dumpingindex finden Sie im [Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#async-index-data).

```
java -jar oak-run.jar index --fds-path <datastore path> <nodestore path> --index-definitions
```

Wo `datastore path` und `nodestore path` aus dem **source** AEM Instanz.

Generieren Sie dann Indexdefinitionen aus dem **target** AEM Version mit dem Granite-Repository-Bundle der Zielversion.

```
java -cp oak-run.jar:bundle-com.adobe.granite.repository.jar org.apache.jackrabbit.oak.index.IndexDefinitionUpdater --in indexing-definitions_source.json --out merge-index-definitions_target.json --initializer com.adobe.granite.repository.impl.GraniteContent
```

>[!NOTE]
>
> Der obige Prozess zur Indexdefinitionserstellung wird nur aus dem `oak-run-1.12.0` ab Version. Das Targeting erfolgt mithilfe des Granite-Repository-Bundles. `com.adobe.granite.repository-x.x.xx.jar`.

Die oben genannten Schritte erstellen eine JSON-Datei mit dem Namen `merge-index-definitions_target.json` , die Indexdefinition.

**2. Checkpoint im Repository erstellen**

Checkpoint in der Produktion erstellen **source** AEM Instanz mit langer Lebensdauer. Dies sollte vor dem Klonen des Repositorys durchgeführt werden.

Über die JMX-Konsole unter `http://serveraddress:serverport/system/console/jmx`, gehen Sie zu `CheckpointMBean` und erstellen Sie einen Checkpoint mit einer ausreichend langen Lebensdauer (z. B. 200 Tage). Rufen Sie dazu auf `CheckpointMBean#createCheckpoint` mit `17280000000` als Argument für die Lebensdauer in Millisekunden.

Kopieren Sie danach die neu erstellte Checkpoint-ID und validieren Sie die Lebensdauer mit JMX `CheckpointMBean#listCheckpoints`.

>[!NOTE]
>
> Dieser Checkpoint wird gelöscht, wenn der Index später importiert wird.

Weitere Informationen finden Sie unter [Checkpoint-Erstellung](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#out-of-band-create-checkpoint) aus der Oak-Dokumentation.

**Offline-Indizierung für die generierten Indexdefinitionen durchführen**

Die Neuindizierung von Lucene kann offline mit oak-run durchgeführt werden. Dieser Prozess erstellt Indexdaten auf der Festplatte unter `indexing-result/indexes`. Sie **not** in das Repository schreiben und daher keine Unterbrechung der laufenden AEM-Instanz erforderlich machen. Der erstellte Textspeicher wird in diesen Prozess eingebunden:

```
java -Doak.indexer.memLimitInMB=500 -jar oak-run.jar index <nodestore path> --reindex --doc-traversal-mode --checkpoint <checkpoint> --fds-path <datastore path> --index-definitions-file merge-index-definitions_target.json --pre-extracted-text-dir text-extraction/store

Sample <checkpoint> looks like r16c85700008-0-8
—fds-path: path to data store.
--pre-extracted-text-dir: Directory of pre-extracted text.
merge-index-definitions_target: JSON file having merged definitions for the target AEM instance. indexes in this file will be re-indexed.
```

Verwendung der `--doc-traversal-mode` -Parameter ist bei MongoMK-Installationen praktisch, da dadurch die Neuindizierungszeit erheblich verbessert wird, indem Repository-Inhalte in eine lokale Flatfile gespoolt werden. Es ist jedoch zusätzlicher Speicherplatz erforderlich, der doppelt so groß ist wie das Repository.

Im Fall von MongoMK kann dieser Prozess beschleunigt werden, wenn dieser Schritt in einer Instanz ausgeführt wird, die näher an der MongoDB-Instanz liegt. Auf demselben Computer kann der Netzwerkaufwand vermieden werden.

Weitere technische Details finden Sie im Abschnitt [Oak-run-Dokumentation für die Indizierung](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html).

### Importieren von Indizes {#importing-indexes}

Mit AEM 6.4 und neueren Versionen verfügt AEM über die integrierte Funktion zum Importieren von Indizes von der Festplatte bei der Startsequenz. Der Ordner `<repository>/indexing-result/indexes` wird beim Start auf das Vorhandensein von Indexdaten überwacht. Sie können den vorab erstellten Index an den oben genannten Speicherort kopieren, während Sie [Aktualisierungsprozess](in-place-upgrade.md#performing-the-upgrade) bevor Sie mit der neuen Version der **target** AEM. AEM importiert es in das Repository und entfernt den entsprechenden Checkpoint aus dem System. Eine Neuindizierung wird somit vollständig vermieden.

## Zusätzliche Tipps und Fehlerbehebung {#troubleshooting}

Unten finden Sie einige hilfreiche Tipps und Anweisungen zur Fehlerbehebung.

### Verringerung der Auswirkungen auf das Live-Produktionssystem {#reduce-the-impact-on-the-live-production-system}

Es wird empfohlen, das Produktionssystem zu klonen und den Offline-Index mithilfe des Klons zu erstellen. Dadurch werden mögliche Auswirkungen auf das Produktionssystem beseitigt. Der für den Indeximport erforderliche Checkpoint muss jedoch im Produktionssystem vorhanden sein. Daher ist es wichtig, einen Checkpoint zu erstellen, bevor der Klon genommen wird.

### Runbook und Testlauf vorbereiten {#prepare-a-runbook-and-trial-run}

Es wird empfohlen, einen [Runbook](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/upgrade-planning.html#building-the-upgrade-and-rollback-runbook) und führen einige Tests durch, bevor Sie die Aktualisierung in der Produktion durchführen.

### Doc Traversal-Modus mit Offline-Indizierung {#doc-traversal-mode-with-offline-indexing}

Die Offline-Indizierung erfordert mehrere Durchläufe des gesamten Repositorys. Bei MongoMK-Installationen wird über das Netzwerk auf das Repository zugegriffen, was sich auf die Leistung des Indizierungsprozesses auswirkt. Eine Option besteht darin, den Offline-Indizierungsprozess auf der MongoDB-Replikation selbst auszuführen, wodurch der Netzwerkaufwand entfällt. Eine weitere Option ist die Verwendung des Dokumentendurchlaufmodus.

Der Doc traversal -Modus kann angewendet werden, indem der Befehlszeilenparameter hinzugefügt wird. `—doc-traversal` zum Oak-run-Befehl für die Offline-Indizierung. Dieser Modus spoolt eine Kopie des gesamten Repositorys auf der lokalen Festplatte als flache Datei und verwendet sie zum Ausführen der Indizierung.
