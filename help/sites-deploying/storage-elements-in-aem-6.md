---
title: Speicherelemente in AEM 6.5
description: Erfahren Sie mehr über die in AEM 6.5 verfügbaren Implementierungen des Knotenspeichers und über die Pflege des Repositorys.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
exl-id: 52437eb5-f9fb-4945-9950-5a1562fe878d
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 100%

---

# Speicherelemente in AEM 6.5{#storage-elements-in-aem}

Dieser Artikel behandelt Folgendes:

* [Überblick über Speicher in AEM 6](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Warten von Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## Überblick über Speicher in AEM 6 {#overview-of-storage-in-aem}

Eine der wichtigsten Änderungen in AEM 6 sind die Innovationen auf Repository-Ebene.

Derzeit stehen in AEM 6 zwei Knotenspeicher zur Verfügung: der TAR-Speicher und der MongoDB-Speicher.

### Tar-Speicher {#tar-storage}

#### Ausführen einer neu installierten AEM-Instanz mit TAR-Speicher {#running-a-freshly-installed-aem-instance-with-tar-storage}

>[!CAUTION]
>
>Die PID für den Segment-Knotenspeicher wurde von org.apache.jackrabbit.oak.**plugins**.segment.SegmentNodeStoreService in früheren Versionen von AEM 6 auf org.apache.jackrabbit.oak.segment.SegmentNodeStoreService in AEM 6.3 geändert. Stellen Sie sicher, dass die erforderlichen Konfigurationsanpassungen vorgenommen werden, damit die Änderungen übernommen werden.

Standardmäßig verwendet AEM 6 den TAR-Speicher zum Speichern von Knoten und Binärdateien mit den Standardkonfigurationsoptionen. Sie können die Speichereinstellungen manuell wie folgt konfigurieren:

1. Laden Sie die AEM 6-Schnellstart-JAR-Datei herunter und legen Sie sie in einem neuen Ordner ab.
1. Entpacken Sie AEM durch Ausführen:

   `java -jar cq-quickstart-6.jar -unpack`

1. Erstellen Sie den Ordner `crx-quickstart\install` im Installationsverzeichnis.

1. Erstellen Sie die Datei `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg` im neu erstellten Ordner.

1. Bearbeiten Sie die Datei, um die Konfigurationsoptionen festzulegen. Die folgenden Optionen sind für den Segmentknotenspeicher verfügbar, der die Grundlage für TAR-Speicherimplementierung von AEM bildet:

   * `repository.home`: Pfad zum Repository-Stammverzeichnis, in dem Repository-bezogene Daten gespeichert werden. Standardmäßig werden Segmentdateien im Verzeichnis crx-quickstart/segmentstore gespeichert.
   * `tarmk.size`: Maximale Größe eines Segments in MB. Die Standardgröße ist 256 MB.

1. Starten Sie AEM.

### Mongo-Speicher {#mongo-storage}

#### Ausführen einer neu installierten AEM-Instanz mit Mongo-Speicher {#running-a-freshly-installed-aem-instance-with-mongo-storage}

AEM 6 kann für die Ausführung mit MongoDB-Speicher konfiguriert werden, wie nachfolgend beschrieben:

1. Laden Sie die AEM 6-Schnellstart-JAR-Datei herunter und legen Sie sie in einem neuen Ordner ab.
1. Entpacken Sie AEM, indem Sie den folgenden Befehl ausführen:

   `java -jar cq-quickstart-6.jar -unpack`

1. Vergewissern Sie sich, dass MongoDB installiert ist und eine Instanz von `mongod` ausgeführt wird. Weitere Informationen finden Sie unter [Installieren von MongoDB](https://docs.mongodb.org/manual/installation/).
1. Erstellen Sie den Ordner `crx-quickstart\install` im Installationsverzeichnis.
1. Konfigurieren Sie den Knotenspeicher. Erstellen Sie dazu eine Konfigurationsdatei mit dem Namen der Konfiguration, die Sie im Verzeichnis `crx-quickstart\install` verwenden möchten.

   Der Document-Knotenspeicher (auf dem die Implementierung von MongoDB-Speicher in AEM basiert) verwendet die Datei `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.cfg`.

1. Bearbeiten Sie die Datei, um die gewünschten Konfigurationsoptionen festzulegen. Die folgenden Optionen sind verfügbar:

   * `mongouri`: Die für die Verbindung mit der Mongo-Datenbank erforderliche [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/). Standard: `mongodb://localhost:27017`
   * `db`: Name der Mongo-Datenbank. Standardmäßig wird bei AEM 6-Installationen **aem-author** als Datenbankname verwendet.
   * `cache`: Die Cachegröße in Megabyte. Dieser Wert verteilt sich auf die verschiedenen in DocumentNodeStore verwendeten Caches. Der Standardwert lautet 256.
   * `changesSize`: Größe (in MB) der begrenzten Sammlung, die in Mongo zum Caching unterschiedlicher Ausgaben verwendet wird. Der Standardwert lautet 256.
   * `customBlobStore`: Boolescher Wert, der angibt, dass ein benutzerdefinierter Datenspeicher verwendet wird. Der Standardwert lautet „false“.

1. Erstellen Sie eine Konfigurationsdatei mit der PID des Datenspeichers, den Sie verwenden möchten, und bearbeiten Sie die Datei, um die Konfigurationsoptionen festzulegen. Weitere Informationen finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern](/help/sites-deploying/data-store-config.md).

1. Starten Sie die JAR-Datei von AEM 6 mit einem MongoDB-Speicher-Backend, indem Sie Folgendes ausführen:

   ```shell
   java -jar cq-quickstart-6.jar -r crx3,crx3mongo
   ```

   Wenn der Backend-Ausführungsmodus **`-r`** ist, beginnt das Beispiel mit der MongoDB-Unterstützung.

#### Deaktivieren von Transparent Huge Pages {#disabling-transparent-huge-pages}

Red Hat® Linux® nutzt einen Speicherverwaltungsalgorithmus mit der Bezeichnung THP (Transparent Huge Pages). Während AEM feinkörnige Lese- und Schreibvorgänge durchführt, ist THP für große Operationen optimiert. Es wird daher empfohlen, THP sowohl auf Tar- als auch auf Mongo-Speicher zu deaktivieren. Gehen Sie wie folgt vor, um den Algorithmus zu deaktivieren:

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
>Sehen Sie sich die folgenden Ressourcen an:
>
>* Weitere Informationen zu Transparent Huge Pages unter Red Hat® Linux® finden Sie in diesem [Artikel](https://access.redhat.com/solutions/46111).
>* Tipps zum Linux®-Tuning finden Sie in diesem [Artikel](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-performance.html?lang=de).
>

## Warten von Repositorys {#maintaining-the-repository}

Jede Aktualisierung des Repositorys erzeugt eine Inhaltsrevision. Daher wächst das Repository nach jeder Aktualisierung. Um ein unkontrolliertes Repository-Wachstum zu vermeiden, müssen alte Revisionen bereinigt werden, um Festplattenressourcen freizugeben. Diese Wartungsfunktionalität wird als Revisionsbereinigung bezeichnet. Bei der Revisionsbereinigung wird durch Löschen veralteter Daten aus dem Repository Festplattenspeicher zurückgewonnen. Weitere Informationen zur Revisionsbereinigung finden Sie auf der [Seite über die Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).
