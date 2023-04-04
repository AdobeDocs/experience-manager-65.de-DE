---
title: Speicherelemente in AEM 6.5
seo-title: Storage Elements in AEM 6.5
description: Erfahren Sie mehr über die in AEM 6.5 verfügbaren Implementierung des Knotenspeichers und über die Wartung des Repositorys.
seo-description: Learn about the node storage implementations available in AEM 6.5 and how to maintain the repository.
uuid: 3b018830-c42e-48e0-9b6f-cd230b02d914
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0aa2c22f-32bb-4e50-8328-63ed73c0f19e
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
exl-id: 52437eb5-f9fb-4945-9950-5a1562fe878d
source-git-commit: 9defa6d1843007e9375d839f72f6993c691a37c0
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 46%

---

# Speicherelemente in AEM 6.5{#storage-elements-in-aem}

Dieser Artikel behandelt Folgendes:

* [Überblick über Speicher in AEM 6](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Warten von Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## Überblick über Speicher in AEM 6 {#overview-of-storage-in-aem}

Eine der wichtigsten Änderungen in AEM 6 sind die Innovationen auf Repository-Ebene.

Derzeit sind in AEM6 zwei Implementierungen für den Knotenspeicher verfügbar: Tar-Speicher und MongoDB-Speicher.

### Tar-Speicher {#tar-storage}

#### Ausführen einer neu installierten AEM-Instanz mit TAR-Speicher {#running-a-freshly-installed-aem-instance-with-tar-storage}

>[!CAUTION]
>
>Die PID für den Segment-Knotenspeicher wurde von org.apache.jackrabbit.oak.**plugins**.segment.SegmentNodeStoreService in früheren Versionen von AEM 6 zu org.apache.jackrabbit.oak.segment.SegmentNodeStoreService in AEM 6.3. Stellen Sie sicher, dass die erforderlichen Konfigurationsanpassungen vorgenommen werden, damit die Änderungen übernommen werden.

Standardmäßig verwendet AEM 6 den TAR-Speicher zum Speichern von Knoten und Binärdateien und verwendet dabei die Standardkonfigurationsoptionen. Sie können die Speichereinstellungen manuell wie folgt konfigurieren:

1. Laden Sie die AEM 6-Schnellstart-JAR herunter und legen Sie sie in einem neuen Ordner ab.
1. Entpacken Sie AEM durch Ausführen:

   `java -jar cq-quickstart-6.jar -unpack`

1. Erstellen Sie den Ordner `crx-quickstart\install` im Installationsverzeichnis.

1. Erstellen Sie die Datei `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg` im neu erstellten Ordner.

1. Bearbeiten Sie die Datei und legen Sie die Konfigurationsoptionen fest. Die folgenden Optionen sind für den Segment-Knotenspeicher verfügbar, der die Grundlage für AEM Tar-Speicherimplementierung bildet:

   * `repository.home`: Pfad zum Repository-Stammverzeichnis, unter dem verschiedene Repository-bezogene Daten gespeichert werden. Standardmäßig werden Segmentdateien im Verzeichnis crx-quickstart/segmentstore gespeichert.
   * `tarmk.size`: Maximale Größe eines Segments in MB. Die Standardgröße ist 256 MB.

1. Starten Sie AEM.

### Mongo-Speicher {#mongo-storage}

#### Ausführen einer neu installierten AEM-Instanz mit Mongo-Speicher {#running-a-freshly-installed-aem-instance-with-mongo-storage}

AEM 6 kann für die Ausführung mit MongoDB-Speicher konfiguriert werden, wie nachfolgend beschrieben:

1. Laden Sie die AEM 6-Schnellstart-JAR herunter und legen Sie sie in einem neuen Ordner ab.
1. Entpacken Sie AEM, indem Sie den folgenden Befehl ausführen:

   `java -jar cq-quickstart-6.jar -unpack`

1. Vergewissern Sie sich, dass MongoDB installiert ist und eine Instanz von `mongod` ausgeführt wird. Weitere Informationen finden Sie unter [Installieren von MongoDB](https://docs.mongodb.org/manual/installation/).
1. Erstellen Sie den Ordner `crx-quickstart\install` im Installationsverzeichnis.
1. Konfigurieren Sie den Knotenspeicher, indem Sie eine Konfigurationsdatei mit dem Namen der Konfiguration erstellen, die Sie im `crx-quickstart\install` Verzeichnis.

   Der Document-Knotenspeicher (auf dem die Implementierung von MongoDB-Speicher in AEM basiert) verwendet die Datei `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.cfg`.

1. Bearbeiten Sie die Datei und legen Sie die Konfigurationsoptionen fest. Die folgenden Optionen sind verfügbar:

   * `mongouri`: Die für die Verbindung mit der Mongo-Datenbank erforderliche [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/). Standard: `mongodb://localhost:27017`
   * `db`: Name der Mongo-Datenbank. Standardmäßig wird bei AEM 6-Installationen **aem-author** als Datenbankname verwendet.
   * `cache`: Die Cachegröße in Megabyte. Diese Cachegröße wird auf verschiedene im DocumentNodeStore verwendete Caches verteilt. Der Standardwert lautet 256.
   * `changesSize`: Größe (in MB) der begrenzten Sammlung, die in Mongo zum Caching unterschiedlicher Ausgaben verwendet wird. Der Standardwert lautet 256.
   * `customBlobStore`: Boolescher Wert, der angibt, dass ein benutzerdefinierter Datenspeicher verwendet wird. Der Standardwert ist &quot;false&quot;.

1. Erstellen Sie eine Konfigurationsdatei mit der PID des Datenspeichers, den Sie verwenden möchten, und bearbeiten Sie die Datei, um die Konfigurationsoptionen festzulegen. Weitere Informationen finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern](/help/sites-deploying/data-store-config.md).

1. Starten Sie die JAR-Datei von AEM 6 mit einem MongoDB-Speicher-Backend, indem Sie Folgendes ausführen:

   ```shell
   java -jar cq-quickstart-6.jar -r crx3,crx3mongo
   ```

   wobei der Backend-Ausführungsmodus **`-r`**, beginnt das Beispiel mit der MongoDB-Unterstützung.

#### Deaktivieren von Transparent Huge Pages {#disabling-transparent-huge-pages}

Red Hat® Linux® verwendet einen Speicherverwaltungsalgorithmus namens Transparent Huge Pages (THP). Während AEM feinkörnige Lese- und Schreibvorgänge durchführt, ist THP für große Operationen optimiert. Daher wird empfohlen, THP sowohl im Tar- als auch im Mongo-Speicher zu deaktivieren. Gehen Sie wie folgt vor, um den Algorithmus zu deaktivieren:

1. Öffnen Sie die Datei `/etc/grub.conf` in einem beliebigen Texteditor.
1. Fügen Sie der Datei **grub.conf** die folgende Zeile hinzu:

   ```
   transparent_hugepage=never
   ```

1. Überprüfen Sie abschließend, ob die Einstellung wirksam wurde, indem Sie Folgendes ausführen:

   ```
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Wenn THP deaktiviert ist, sollte die Ausgabe des obigen Befehls wie folgt lauten:

   ```
   always madvise [never]
   ```

>[!NOTE]
>
>Lesen Sie die folgenden Ressourcen:
>
>* Weitere Informationen zu Transparent Huge Pages unter Red Hat® Linux® finden Sie in diesem [Artikel](https://access.redhat.com/solutions/46111).
* Tipps zur Linux®-Optimierung finden Sie hier . [Artikel](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=en).
>


## Warten von Repositorys {#maintaining-the-repository}

Jede Aktualisierung des Repositorys erstellt eine Inhaltsüberarbeitung. Daher wächst das Repository nach jeder Aktualisierung. Um ein unkontrolliertes Wachstum des Repositorys zu vermeiden, müssen alte Revisionen bereinigt werden, um Festplattenressourcen freizugeben. Diese Wartungsfunktionalität wird als Revisionsbereinigung bezeichnet. Der Mechanismus zur Revisionsbereinigung gewinnt Speicherplatz zurück, indem veraltete Daten aus dem Repository entfernt werden. Weitere Informationen zur Revisionsbereinigung finden Sie auf der [Seite über die Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).
