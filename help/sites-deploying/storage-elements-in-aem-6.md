---
title: Speicherelemente in AEM 6.5
seo-title: Speicherelemente in AEM 6.5
description: Erfahren Sie mehr über die in AEM 6.5 verfügbaren Implementierungen von Knotenspeicher und über die Wartung des Repositorys.
seo-description: Erfahren Sie mehr über die in AEM 6.5 verfügbaren Implementierungen von Knotenspeicher und über die Wartung des Repositorys.
uuid: 3b018830-c42e-48e0-9b6f-cd230b02d914
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 0aa2c22f-32bb-4e50-8328-63ed73c0f19e
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
exl-id: 52437eb5-f9fb-4945-9950-5a1562fe878d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 81%

---

# Speicherelemente in AEM 6.5{#storage-elements-in-aem}

In diesem Artikel werden folgende Themen behandelt:

* [Überblick über Speicher in AEM 6](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Wartung von Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## Überblick über Speicher in AEM 6 {#overview-of-storage-in-aem}

Eine der wichtigsten Änderungen in AEM 6 sind die Innovationen auf Repository-Ebene.

Derzeit sind in AEM 6 zwei Implementierungen von Knotenspeicher verfügbar: TAR-Speicher und MongoDB-Speicher.

### TAR-Speicher  {#tar-storage}

#### Ausführen einer neu installierten AEM-Instanz mit TAR-Speicher {#running-a-freshly-installed-aem-instance-with-tar-storage}

>[!CAUTION]
>
>Die PID für den Segment-Knotenspeicher wurde von org.apache.jackrabbit.oak geändert.**plugins**.segment.SegmentNodeStoreService in früheren Versionen von AEM 6 zu org.apache.jackrabbit.oak.segment.SegmentNodeStoreService in AEM 6.3. Stellen Sie sicher, dass Sie die erforderlichen Konfigurationsanpassungen vornehmen, um diese Änderung widerzuspiegeln.

Standardmäßig verwendet AEM 6 den TAR-Speicher zum Speichern von Knoten und Binärdateien und verwendet dabei die Standardkonfigurationsoptionen. Führen Sie folgende Schritte aus, um die Speichereinstellungen manuell zu konfigurieren:

1. Laden Sie die Datei „quickstart.jar“ von AEM 6 herunter und speichern Sie diese in einem neuen Ordner.
1. Entpacken Sie AEM, indem Sie Folgendes ausführen:

   `java -jar cq-quickstart-6.jar -unpack`

1. Erstellen Sie einen Ordner mit dem Namen `crx-quickstart\install` im Installationsverzeichnis.

1. Erstellen Sie die Datei `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg` im neu erstellten Ordner.

1. Bearbeiten Sie die Datei und legen Sie die Konfigurationsoptionen fest. Folgende Optionen sind für Segment-Knotenspeicher verfügbar, auf der die Implementierung von TAR-Speicher in AEM basiert:

   * `repository.home`: Pfad zum Repository-Stammverzeichnis, in dem diverse Repository-bezogene Daten gespeichert werden. Standardmäßig werden Segmentdateien im Verzeichnis crx-quickstart/segmentstore gespeichert.
   * `tarmk.size` : Maximale Größe eines Segments in MB. Die Standardgröße ist 256 MB.

1. Starten Sie AEM.

### Mongo-Speicher {#mongo-storage}

#### Ausführen einer neu installierten AEM-Instanz mit Mongo-Speicher {#running-a-freshly-installed-aem-instance-with-mongo-storage}

AEM 6 kann für die Ausführung mit MongoDB-Speicher konfiguriert werden, wie nachfolgend beschrieben:

1. Laden Sie die quickstart.jar von AEM 6 herunter und speichern Sie diese in einem neuen Ordner.
1. Entpacken Sie AEM, indem Sie folgenden Befehl ausführen:

   `java -jar cq-quickstart-6.jar -unpack`

1. Stellen Sie sicher, dass MongoDB installiert ist und eine Instanz von `mongod` ausgeführt wird. Weitere Informationen finden Sie unter [Installieren von MongoDB](https://docs.mongodb.org/manual/installation/).
1. Erstellen Sie einen Ordner mit dem Namen `crx-quickstart\install` im Installationsverzeichnis.
1. Konfigurieren Sie den Knotenspeicher. Erstellen Sie dazu eine Konfigurationsdatei mit dem Namen der Konfiguration, die Sie im Verzeichnis `crx-quickstart\install` verwenden möchten.

   Der Document Node Store (die Grundlage für AEM MongoDB-Speicherimplementierung) verwendet eine Datei namens `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.cfg`

1. Bearbeiten Sie die Datei und legen Sie die Konfigurationsoptionen fest. Die folgenden Optionen sind verfügbar:

   * `mongouri`: Die für die Verbindung zur Mongo-Datenbank erforderliche [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/). Standard: `mongodb://localhost:27017`
   * `db` : Name der Mongo-Datenbank. Standardmäßig wird bei AEM 6-Installationen **aem-author** als Datenbankname verwendet.
   * `cache`: Cache-Größe in MB. Dieser Wert verteilt sich auf die verschiedenen in DocumentNodeStore verwendeten Caches. Standard: 256.
   * `changesSize`: Größe (in MB) der begrenzten Sammlung, die in Mongo zum Zwischenspeichern unterschiedlicher Ausgaben verwendet wird. Standard: 256.
   * `customBlobStore`: Boolescher Wert, der angibt, dass ein benutzerdefinierter Datenspeicher verwendet wird. Der Standardwert lautet „false“.

1. Erstellen Sie eine Konfigurationsdatei mit der PID des Datenspeichers, in dem Sie die Datei verwenden und bearbeiten möchten, um die Konfigurationsoptionen festzulegen. Weitere Informationen finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern](/help/sites-deploying/data-store-config.md).

1. Starten Sie die JAR-Datei von AEM 6 vom MongoDB-Speicher-Backend aus, indem Sie Folgendes ausführen:

   ```shell
   java -jar cq-quickstart-6.jar -r crx3,crx3mongo
   ```

   Dabei ist **`-r`** der Backend-Ausführungsmodus. In diesem Beispiel beginnt dieser mit MongoDB-Unterstützung.

#### Deaktivieren von Transparent Huge Pages  {#disabling-transparent-huge-pages}

Red Hat Linux nutzt einen Speicherverwaltungsalgorithmus mit der Bezeichnung THP (Transparent Huge Pages). Während AEM feinkörnige Lese- und Schreibvorgänge durchführt, ist THP für große Operationen optimiert. Aus diesem Grund wird empfohlen, dass Sie THP auf Tar- und Mongospeicher deaktivieren. Um den Algorithmus zu deaktivieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die Datei `/etc/grub.conf` im Texteditor Ihrer Wahl.
1. Fügen Sie der Datei **grub.conf** die folgende Zeile hinzu:

   ```
   transparent_hugepage=never
   ```

1. Überprüfen Sie abschließend, ob die Einstellung wirksam geworden ist, indem Sie Folgendes ausführen:

   ```
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Wenn THP deaktiviert ist, sollte die Ausgabe des oben stehenden Befehls wie folgt sein:

   ```
   always madvise [never]
   ```

>[!NOTE]
>
>Zusätzlich können Sie auch die folgenden Ressourcen konsultieren:
>
>* Weitere Informationen zu Transparent Huge Pages unter Red Hat Linux finden Sie in diesem [Artikel](https://access.redhat.com/solutions/46111).
>* Tipps zur Linux-Optimierung finden Sie in diesem [Artikel](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html).

>



## Wartung von Repositorys {#maintaining-the-repository}

Bei jeder Repository-Aktualisierung wird eine neue Inhaltsrevision erstellt. Dadurch wächst bei jeder Aktualisierung die Größe des Repositorys. Um ein unkontrolliertes Repository-Wachstum zu vermeiden, müssen alte Revisionen bereinigt werden, um Festplattenressourcen freizugeben. Diese Wartungsfunktionalität wird als Revisionsbereinigung bezeichnet. Bei der Revisionsbereinigung wird durch Löschen veralteter Daten aus dem Repository Festplattenspeicher zurückgewonnen. Weitere Informationen zur Revisionsbereinigung finden Sie auf der [Seite über die Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md).
