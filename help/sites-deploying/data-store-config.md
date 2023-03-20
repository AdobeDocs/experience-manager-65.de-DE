---
title: Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6
description: Erfahren Sie, wie Sie Knotenspeicher und Datenspeicher konfigurieren und wie Sie die automatische Datenspeicherbereinigung durchführen.
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: c1c90d6a-ee5a-487d-9a8a-741b407c8c06
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '3521'
ht-degree: 58%

---

# Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6 {#configuring-node-stores-and-data-stores-in-aem}

## Einführung {#introduction}

In Adobe Experience Manager (AEM) können Binärdaten unabhängig von den Inhaltsknoten gespeichert werden. Die Binärdaten werden in einem Datenspeicher gespeichert, während Inhaltsknoten in einem Knotenspeicher gespeichert werden.

Sowohl Datenspeicher als auch Knotenspeicher können mit der OSGi-Konfiguration konfiguriert werden. Jede OSGi-Konfiguration wird mithilfe einer beständigen Kennung (PID) referenziert.

## Konfigurationsschritte {#configuration-steps}

Führen Sie die folgenden Schritte aus, um sowohl den Knotenspeicher als auch den Datenspeicher zu konfigurieren:

1. Kopieren Sie die AEM Schnellstart-JAR-Datei in den Installationsordner.
1. Erstellen Sie einen Ordner `crx-quickstart/install` im Installationsverzeichnis.
1. Konfigurieren Sie zunächst den Knotenspeicher, indem Sie eine Konfigurationsdatei mit dem Namen der zu verwendenden Knotenspeicher-Option im Verzeichnis `crx-quickstart/install` erstellen.

   Der Knotenspeicher „Dokument“ (die Basis der AEM-MongoMK-Implementierung) nutzt etwa die Datei `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`.

1. Bearbeiten Sie die Datei und legen Sie die Konfigurationsoptionen fest.
1. Erstellen Sie eine Konfigurationsdatei mit der PID des Datenspeichers, den Sie verwenden möchten. Bearbeiten Sie die Datei, um die Konfigurationsoptionen festzulegen.

   >[!NOTE]
   >
   >Weitere Informationen zu Konfigurationsoptionen finden Sie unter [Knotenspeicher-Konfigurationen](#node-store-configurations) und [Datenspeicher-Konfigurationen](#data-store-configurations).

1. Starten Sie AEM.

## Knotenspeicherkonfigurationen {#node-store-configurations}

>[!CAUTION]
>
>Neuere Versionen von Oak verwenden ein neues Benennungsschema und -format für OSGi-Konfigurationsdateien. Das neue Namensschema erfordert, dass die Konfigurationsdatei **.config** und das neue Format erfordert die Eingabe von Werten und ist [hier dokumentiert](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format).
>
>Wenn Sie von einer älteren Oak-Version aktualisieren, stellen Sie sicher, dass Sie zunächst den Ordner `crx-quickstart/install` sichern. Stellen Sie nach dem Upgrade den Inhalt des Ordners in der aktualisierten Installation wieder her und ändern Sie die Erweiterung der Konfigurationsdateien von **.cfg** zu **.config**.
>
>Falls Sie diesen Artikel lesen, um ein Upgrade von einem **AEM 5.x** installieren, konsultieren Sie die [Upgrade](https://experienceleague.adobe.com/docs/?lang=de) Dokumentation zuerst.

### Segmentknotenspeicher {#segment-node-store}

Der Segmentknotenspeicher ist die Grundlage für die TarMK-Implementierung der Adobe in AEM6. Zur Konfiguration wird die PID `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` verwendet.

>[!CAUTION]
>
>Die PID für den Segment-Knotenspeicher hat sich von `org.apache.jackrabbit.oak.plugins.segment.SegmentNodeStoreService in previous versions` in AEM 6 zu `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService` in AEM 6.3 geändert. Stellen Sie sicher, dass Sie die erforderlichen Konfigurationsanpassungen vornehmen, um diese Änderung widerzuspiegeln.

Sie können die folgenden Optionen konfigurieren:

* `repository.home`: Pfad zum Repository-Stammverzeichnis, in dem Repository-bezogene Daten gespeichert werden. Standardmäßig werden Segmentdateien im Verzeichnis `crx-quickstart/segmentstore` gespeichert.

* `tarmk.size`: Maximale Größe eines Segments in MB. Der standardmäßige Maximalwert lautet 256 MB.
* `customBlobStore`: Boolescher Wert, der angibt, dass ein benutzerdefinierter Datenspeicher verwendet wird. Der Standardwert ist „true“ für AEM 6.3 und höhere Versionen. Vor AEM 6.3 war die Standardeinstellung „false“.

Es folgt eine Beispieldatei für `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`:

```shell
#Path to repo
repository.home="crx-quickstart/repository"

#Max segment size
tarmk.size=I"256"

#Custom data store
customBlobStore=B"true"
```

#### Knotenspeicher &quot;Dokument&quot; {#document-node-store}

Der Knotenspeicher &quot;document&quot;bildet die Grundlage AEM MongoMK-Implementierung. Verwendet wird dabei die PID* *`org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService`. Folgende Konfigurationsoptionen sind verfügbar:

* `mongouri`: Die für die Verbindung zur Mongo-Datenbank erforderliche [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/). Standard: `mongodb://localhost:27017`

* `db`: Name der Mongo-Datenbank. Der Standardwert ist **Oak** ``. However, new AEM 6 installations use **aem-author** `` als standardmäßigen Datenbanknamen.

* `cache`: Cache-Größe in MB. Dieser Wert verteilt sich auf die verschiedenen in DocumentNodeStore verwendeten Caches. Standard: `256`

* `changesSize`: Größe (in MB) der begrenzten Sammlung, die in Mongo zum Zwischenspeichern unterschiedlicher Ausgaben verwendet wird. Standard: `256`

* `customBlobStore`: Boolescher Wert, der angibt, dass ein benutzerdefinierter Datenspeicher verwendet wird. Der Standardwert lautet `false`.

Es folgt eine Beispieldatei für `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`:

```shell
#Mongo server details
mongouri="mongodb://localhost:27017"

#Name of Mongo database to use
db="aem-author"

#Store binaries in custom BlobStore
customBlobStore=B"false"
```

## Datenspeicherkonfigurationen {#data-store-configurations}

Für den Umgang mit einer großen Anzahl von Binärdateien wird empfohlen, anstelle der standardmäßigen Knotenspeicher einen externen Datenspeicher zu verwenden, um die Leistung zu maximieren.

Wenn Ihr Projekt beispielsweise viele Medien-Assets benötigt, wird durch das Speichern unter dem Dateispeicher oder dem S3-Datenspeicher der Zugriff schneller erfolgt, als direkt in einer MongoDB zu speichern.

Der Dateidatenspeicher bietet eine bessere Leistung als MongoDB. Die Sicherungs- und Wiederherstellungsvorgänge von Mongo sind bei einer großen Anzahl von Assets ebenfalls langsamer.

Details zu den verschiedenen Datenspeichern und Konfigurationen werden nachfolgend beschrieben.

>[!NOTE]
>
>Um benutzerdefinierte Datenspeicher zu aktivieren, müssen Sie sicherstellen, dass `customBlobStore` auf `true` in der entsprechenden Knotenspeicher-Konfigurationsdatei ([Segmentknotenspeicher](/help/sites-deploying/data-store-config.md#segment-node-store) oder [Knotenspeicher &quot;document&quot;](/help/sites-deploying/data-store-config.md#document-node-store)).

### Dateidatenspeicher {#file-data-store}

Dies ist die Implementierung von [FileDataStore](https://jackrabbit.apache.org/api/trunk/org/apache/jackrabbit/core/data/FileDataStore.html) vorhanden in Jackrabbit 2. Es bietet eine Möglichkeit, die Binärdaten als normale Dateien im Dateisystem zu speichern. Verwendet wird dabei die PID `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore`.

Die folgenden Konfigurationsoptionen sind verfügbar:

* `repository.home`: Pfad zum Repository-Stammverzeichnis, in dem diverse Repository-bezogene Daten gespeichert werden. Standardmäßig werden Binärdateien im Verzeichnis `crx-quickstart/repository/datastore` gespeichert.

* `path`: Pfad zum Verzeichnis, unter dem Dateien gespeichert werden. Sofern angegeben, hat dieser Wert Vorrang gegenüber `repository.home`.

* `minRecordLength`: Mindestgröße in Byte einer im Datenspeicher abgelegten Datei. Binärinhalte, die unterhalb dieses Werts liegen, werden als Inline-Elemente dargestellt.

>[!NOTE]
>
>Wenn Sie einen NAS verwenden, um freigegebene Dateidatenspeicher zu speichern, stellen Sie sicher, dass Sie nur leistungsstarke Geräte verwenden, um Leistungsprobleme zu vermeiden.

## Amazon S3-Datenspeicher {#amazon-s-data-store}

AEM kann so konfiguriert werden, dass Daten im Simple Storage Service (S3) von Amazon gespeichert werden. Zur Konfiguration wird die PID `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` verwendet.

Um die S3-Datenspeicherfunktion zu aktivieren, muss ein Feature Pack mit dem S3-Datenspeicher-Connector heruntergeladen und installiert werden. Gehen Sie zum [Adobe-Repository](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) und laden Sie die neueste Version der 1.10.x-Versionen des Feature Packs herunter (z. B. com.adobe.granite.oak.s3connector-1.10.0.zip). Außerdem müssen Sie das neueste AEM Service Pack herunterladen und installieren, das auf der Seite [AEM 6.5 - Versionshinweise](/help/release-notes/release-notes.md) Seite.

>[!NOTE]
>
>Bei Verwendung von AEM mit TarMK werden die Binärdateien standardmäßig im `FileDataStore` gespeichert. Um TarMK mit dem S3-Datenspeicher zu verwenden, müssen Sie AEM die `crx3tar-nofds` runmode, z. B.:

```shell
java -jar <aem-jar-file>.jar -r crx3tar-nofds
```

Nach dem Download können Sie den S3-Connector wie folgt installieren und konfigurieren:

1. Extrahieren Sie den Inhalt der ZIP-Datei des Feature Packs in einen temporären Ordner.

1. Wechseln Sie zum temporären Ordner und navigieren Sie zum folgenden Speicherort:

   ```xml
   jcr_root/libs/system/install
   ```

   Kopieren Sie alle Inhalte vom oben genannten Speicherort nach `<aem-install>/crx-quickstart/install.`

1. Wenn AEM bereits für Tar- oder MongoDB-Speicher konfiguriert ist, entfernen Sie etwaig vorhandene Konfigurationsdateien aus dem Ordner ***&lt;aem-install>***/*crx-quickstart*/*install*, bevor Sie fortfahren. Die zu entfernenden Dateien sind:

   * `For MongoMK: org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`
   * `For TarMK: org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Kehren Sie zum temporären Verzeichnis mit dem extrahierten Feature Pack zurück und kopieren Sie den Inhalt des folgenden Ordners:

   * `jcr_root/libs/system/config`

   in

   * `<aem-install>/crx-quickstart/install`

   Stellen Sie sicher, dass Sie nur die für die aktuelle Konfiguration benötigten Konfigurationsdateien kopieren. Kopieren Sie sowohl bei einem dedizierten Datenspeicher als auch bei einem freigegebenen Datenspeicher die Datei `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config`.

   >[!NOTE]
   >
   >Führen Sie bei einer Clustereinrichtung die oben genannten Schritte für alle Knoten des Clusters einzeln durch. Stellen Sie außerdem sicher, dass Sie dieselben S3-Einstellungen für alle Knoten verwenden.

1. Bearbeiten Sie die Datei und fügen Sie die für Ihr Setup erforderlichen Konfigurationsoptionen hinzu.
1. Starten Sie AEM.

## Aktualisieren auf eine neue Version des 1.10.x S3-Connectors {#upgrading-to-a-new-version-of-the-s-connector}

Gehen Sie wie folgt vor, um auf eine neue Version des S3-Connectors 1.10.x (z. B. von 1.10.0 auf 1.10.4) zu aktualisieren:

1. Halten Sie die AEM-Instanz an.

1. Navigieren Sie im AEM-Installationsordner zu `<aem-install>/crx-quickstart/install/15` und sichern Sie die dort vorhandenen Inhalte.
1. Löschen Sie nach der Sicherung die alte Version des S3-Connectors und die entsprechenden abhängigen Elemente, indem Sie die JAR-Dateien aus dem Ordner `<aem-install>/crx-quickstart/install/15` entfernen, z. B.:

   * **oak-blob-cloud-1.6.1.jar**
   * **aws-java-sdk-osgi-1.10.76.jar**

   >[!NOTE]
   >
   >Die oben aufgeführten Dateinamen dienen nur zu Veranschaulichungszwecken.

1. Laden Sie die neueste Version des Feature Packs 1.10.x aus dem [Adobe-Repository](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) herunter.
1. Entpacken Sie den Inhalt in einen anderen Ordner und navigieren Sie dann zu `jcr_root/libs/system/install/15`.
1. Kopieren Sie die JAR-Dateien nach **&lt;aem-install>**/crx-quickstart/install/15 im AEM-Installationsverzeichnis.
1. Starten Sie AEM und überprüfen Sie die Funktionsweise des Connectors.

Sie können die Konfigurationsdatei mit den unten beschriebenen Optionen verwenden.

<!--
* accessKey: The AWS access key.
* secretKey: The AWS secret access key. **Note:** When the `accessKey` or `secretKey` is not specified then the [IAM role](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) is used for authentication.
* s3Bucket: The bucket name.
* s3Region: The bucket region.
* path: The path of the data store. The default is **&lt;AEM install folder&gt;/repository/datastore**
* minRecordLength: The minimum size of an object that should be stored in the data store. The minimum/default is **16KB.**
* maxCachedBinarySize: Binaries with size less than or equal to this size will be stored in memory cache. The size is in bytes. The default is **17408 **(17 KB).
* cacheSize: The size of the cache. The value is specified in bytes. The default is **64GB**.
* secret: Only to be used if using binaryless replication for shared datastore setup.
* stagingSplitPercentage: The percentage of cache size configured to be used for staging asynchronous uploads. The default value is **10**.
* uploadThreads: The number of uploads threads that are used for asynchronous uploads. The default value is **10**.
* stagingPurgeInterval: The interval in seconds for purging finished uploads from the staging cache. The default value is **300** seconds (5 minutes).
* stagingRetryInterval: The retry interval in seconds for failed uploads. The default value is **600** seconds (10 minutes).
-->

### Dateioptionen für die S3-Connector-Konfiguration {#s3-connector-configuration-file-options}

>[!NOTE]
>
>Der S3-Connector unterstützt sowohl die IAM-Benutzerauthentifizierung als auch die IAM-Rollenauthentifizierung. Um die IAM-Rollenauthentifizierung zu verwenden, lassen Sie die Werte `accessKey` und `secretKey` aus Ihrer Konfigurationsdatei weg. Der S3-Connector wird dann standardmäßig auf die [IAM-Rolle](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) gesetzt, die der Instanz zugewiesen wurde.

| Schlüssel | Beschreibung | Standard | Erforderlich |
| --- | --- | --- | --- |
| accessKey | Greifen Sie auf die Schlüssel-ID für den IAM-Benutzer zu, der Zugriff auf den Bucket hat. |  | Ja, wenn keine IAM-Rollen verwendet werden. |
| secretKey | Geheimer Zugriffsschlüssel für den IAM-Benutzer mit Zugriff auf den Bucket. |  | Ja, wenn keine IAM-Rollen verwendet werden. |
| cacheSize | Die Größe (in Byte) des lokalen Caches. | 64 GB | Anzahl  |
| connectionTimeout | Legen Sie die Wartezeit (in Millisekunden) bis zum Timeout beim erstmaligen Herstellen einer Verbindung fest. | 10000 | Anzahl  |
| maxCachedBinarySize | Binärdateien mit einer Größe, die kleiner oder gleich diesem Wert ist (in Byte), werden im Arbeitsspeicher-Cache gespeichert. | 17408 (17 KB) | Anzahl  |
| maxConnections | Legen Sie die maximale Anzahl der zulässigen offenen HTTP-Verbindungen fest. | 50 | Anzahl  |
| maxErrorRetry | Legen Sie die maximale Anzahl von Wiederholungsversuchen für fehlgeschlagene (wiederholbare) Anfragen fest. | 3 | Anzahl  |
| minRecordLength | Die Mindestgröße eines Objekts (in Bytes), das im Datenspeicher gespeichert werden soll. | 16384 | Anzahl  |
| path | Der lokale Pfad des AEM-Datenspeichers. | `crx-quickstart/repository/datastore` | Anzahl  |
| proxyHost | Legen Sie den optionalen Proxy-Host fest, über den der Client eine Verbindung herstellt. |  | Anzahl  |
| proxyPort | Legen Sie den optionalen Proxy-Port fest, über den der Client eine Verbindung herstellt. |  | Anzahl  |
| s3Bucket | Name des S3-Buckets. |  | Ja |
| s3EndPoint | Endpunkt der S3 REST-API. |  | Anzahl  |
| s3Region | Region, in der sich der Bucket befindet. Weitere Informationen finden Sie auf dieser [Seite](https://docs.aws.amazon.com/general/latest/gr/s3.html). | Region, in der die AWS-Instanz ausgeführt wird. | Anzahl  |
| socketTimeout | Legen Sie die Wartezeit (in Millisekunden) für Daten fest, die über eine eingerichtete, offene Verbindung übertragen werden sollen, bevor die Verbindung unterbrochen und geschlossen wird. | 50000 | Anzahl  |
| stagingPurgeInterval | Das Intervall (in Sekunden) zum endgültigen Löschen fertiggestellter Uploads aus dem Staging-Cache. | 300 | Anzahl  |
| stagingRetryInterval | Das Intervall (in Sekunden) zum Wiederholen fehlgeschlagener Uploads. | 600 | Anzahl  |
| stagingSplitPercentage | Der Prozentsatz von `cacheSize` zur Verwendung für das Staging asynchroner Uploads. | 10 | Anzahl  |
| uploadThreads | Die Anzahl der Upload-Threads, die für asynchrone Uploads verwendet werden. | 10 | Anzahl  |
| writeThreads | Die Anzahl der parallelen Threads, die zum Schreiben über S3 Transfer Manager verwendet werden. | 10 | Anzahl  |

<!---
### Bucket region options {#bucket-region-options}

<table>
 <tbody>
  <tr>
   <td>US Standard</td>
   <td><code>us-standard</code></td>
  </tr>
  <tr>
   <td>US West</td>
   <td><code>us-west-2</code></td>
  </tr>
  <tr>
   <td>US West (Northern California)</td>
   <td><code>us-west-1</code></td>
  </tr>
  <tr>
   <td>EU (Ireland)<br /> </td>
   <td><code>EU</code></td>
  </tr>
  <tr>
   <td>Asia Pacific (Singapore)<br /> </td>
   <td><code>ap-southeast-1</code></td>
  </tr>
  <tr>
   <td>Asia Pacific (Sydney)<br /> </td>
   <td><code>ap-southeast-2</code></td>
  </tr>
  <tr>
   <td>Asia Pacific (Tokyo)</td>
   <td><code>ap-northeast-1</code></td>
  </tr>
  <tr>
   <td>South America (Sao Paolo)<br /> </td>
   <td><code>sa-east-1</code></td>
  </tr>
 </tbody>
</table>
-->

### Datenspeicher-Caching {#data-store-caching}

>[!NOTE]
>
>Die Datenspeicher-Implementierungen von `S3DataStore`, `CachingFileDataStore` und `AzureDataStore` unterstützen das Caching lokaler Dateisysteme. Die `CachingFileDataStore`-Implementierung ist nützlich, wenn sich der Datenspeicher auf NFS (Network File System) befindet.

Beim Aktualisieren von einer älteren Cache-Implementierung (vor Oak 1.6) gibt es einen Unterschied in der Struktur des Cache-Verzeichnisses des lokalen Dateisystems. In der alten Cachestruktur wurden sowohl die heruntergeladenen als auch die hochgeladenen Dateien direkt unter den Cachepfad gestellt. In der neuen Struktur werden Downloads und Uploads voneinander getrennt und in zwei Verzeichnissen namens `upload` und `download` unter dem Cachepfad gespeichert. Der Aktualisierungsprozess sollte nahtlos sein, und alle ausstehenden Uploads sollten für den Upload geplant werden und alle zuvor heruntergeladenen Dateien im Cache werden bei der Initialisierung im Cache gespeichert.

Sie können den Cache auch offline upgraden, indem Sie den Befehl `datastorecacheupgrade` von oak-run ausführen. Weitere Einzelheiten zum Ausführen des Befehls finden Sie in der [Readme](https://svn.apache.org/repos/asf/jackrabbit/oak/trunk/oak-run/README.md)-Datei für das oak-run-Modul.

Der Cache hat eine Größenbeschränkung und kann mithilfe des cacheSize-Parameters konfiguriert werden.

#### Downloads {#downloads}

Der lokale Cache wird auf den Datensatz der angeforderten Datei/des angeforderten Blob überprüft, bevor auf ihn über den DataStore zugegriffen wird. Wenn der Cache das konfigurierte Limit überschreitet (siehe `cacheSize` -Parameter) beim Hinzufügen einer Datei zum Cache hinzugefügt werden, werden einige der Dateien entfernt, um Speicherplatz zurückzugewinnen.

#### Asynchrone Uploads {#async-upload}

Der Cache unterstützt asynchrone Uploads in den DataStore. Die Dateien werden lokal im Cache (im Dateisystem) bereitgestellt und ein asynchroner Auftrag startet das Hochladen der Datei. Die Anzahl der asynchronen Uploads ist durch die Größe des Staging-Cache begrenzt. Die Größe des Staging-Cache wird mithilfe des `stagingSplitPercentage`-Parameters konfiguriert. Dieser Parameter definiert den Prozentsatz der Cachegröße, der für den Staging-Cache verwendet werden soll. Außerdem wird der Prozentsatz des für Downloads verfügbaren Cache wie folgt berechnet: **(100 - `stagingSplitPercentage`) &#42;`cacheSize`**.

Asynchrone Uploads verlaufen in mehreren Threads und die Anzahl der Threads wird mithilfe des `uploadThreads`-Parameters konfiguriert.

Die Dateien werden nach Abschluss der Uploads in den Haupt-Download-Cache verschoben. Wenn die Größe des Staging-Cache die Grenze überschreitet, werden die Dateien synchron in den DataStore hochgeladen, bis die vorherigen asynchronen Uploads abgeschlossen sind und wieder Speicherplatz im Staging-Cache verfügbar ist. Die hochgeladenen Dateien werden aus dem Staging-Bereich durch einen periodischen Auftrag entfernt, dessen Intervall durch den `stagingPurgeInterval`-Parameter konfiguriert ist.

Fehlgeschlagene Uploads (etwa aufgrund von Netzwerkstörungen) werden in eine Warteschlange gestellt und regelmäßig wiederholt. Das Wiederholungsintervall wird mithilfe des `stagingRetryInterval parameter` konfiguriert.

#### Konfiguration der Binärdatei-losen Replikation mit Amazon S3 {#configuring-binaryless-replication-with-amazon-s}

Um die Binärdatei-lose Replikation mit S3 zu konfigurieren, sind die folgenden Schritte erforderlich:

1. Installieren Sie die Autoren- und Veröffentlichungsinstanzen und stellen Sie sicher, dass sie ordnungsgemäß gestartet wurden.
1. Gehen Sie zu den Einstellungen für den Replikationsagenten, indem Sie eine Seite in *https://localhost:4502/etc/replication/agents.author/publish.html* öffnen.
1. Wählen Sie im Abschnitt **Einstellungen** die Schaltfläche **Bearbeiten**.
1. Ändern Sie die Option für den **Serialisierungs** typ in **Nicht binär**.

1. Fügen Sie den Parameter `binaryless` = `true` dem Transport-URI hinzu. Nach dieser Änderung sollte der URI ungefähr wie folgt aussehen:

   *https://localhost:4503/bin/receive?sling:authRequestLogin=1&amp;binaryless=true*

1. Starten Sie alle Autoren- und Veröffentlichungsinstanzen neu, damit die Änderungen wirksam werden.

#### Erstellen eines Clusters mit S3 und MongoDB {#creating-a-cluster-using-s-and-mongodb}

1. Entpacken Sie den CQ-Schnellstart mit dem folgenden Befehl:

   `java -jar cq-quickstart.jar -unpack`

1. Nachdem AEM entpackt wurde, erstellen Sie einen Ordner im Installationsverzeichnis *crx-quickstart*/*install*.

1. Erstellen Sie diese beiden Dateien im Ordner `crx-quickstart`:

   * *org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService*.*config*

   * *org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore*.*config*

   Nachdem die Dateien erstellt wurden, fügen Sie die Konfigurationsoptionen nach Bedarf hinzu.

1. Installieren Sie die beiden Pakete, die für den S3-Datenspeicher erforderlich sind, wie oben beschrieben.
1. Stellen Sie sicher, dass MongoDB installiert ist und eine `mongod`-Instanz ausgeführt wird.
1. Starten Sie AEM mit dem folgenden Befehl:

   `java -Xmx1024m -jar cq-quickstart.jar -r crx3,crx3mongo`

1. Wiederholen Sie die Schritte 1 bis 4 für die zweite AEM.
1. Starten Sie die zweite AEM.

#### Konfigurieren eines freigegebenen Datenspeichers {#configuring-a-shared-data-store}

1. Erstellen Sie zunächst die Konfigurationsdatei für den Datenspeicher auf jeder Instanz, die zum Freigeben des Datenspeichers erforderlich ist:

   * Wenn Sie einen `FileDataStore` verwenden, erstellen Sie eine Datei mit dem Namen `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` und legen Sie diese im Ordner `<aem-install>/crx-quickstart/install` ab.

   * Wird S3 als Datenspeicher verwendet, erstellen Sie eine Datei mit dem Namen `rg.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.config` im Ordner `<aem-install>/crx-quickstart/install`, wie oben erläutert.

1. Ändern Sie die Konfigurationsdateien des Datenspeichers in jeder Instanz so, dass sie auf denselben Datenspeicher verweisen. Weitere Informationen finden Sie unter [diesem Artikel](/help/sites-deploying/data-store-config.md#data-store-configurations).
1. Wenn die Instanz von einem vorhandenen Server geklont wurde, müssen Sie die `clusterId` der neuen Instanz verwenden, indem Sie das neueste oak-run-Tool verwenden, während das Repository offline ist. Der auszuführende Befehl lautet:

   ```xml
   java -jar oak-run.jar resetclusterid < repository path | Mongo URI >
   ```

   >[!NOTE]
   >
   >Wenn ein Segment-Knotenspeicher konfiguriert ist, muss der Repository-Pfad angegeben werden. Standardmäßig lautet der Pfad `<aem-install-folder>/crx-quickstart/repository/segmentstore.`. Ist ein Knotenspeicher „Dokument“ konfiguriert, können Sie einen [URI im Format einer Mongo-Verbindungszeichenfolge](https://docs.mongodb.org/manual/reference/connection-string/) verwenden.

   >[!NOTE]
   >
   >Das oak-run-Tool kann über diese Adresse heruntergeladen werden:
   >
   >
   >[https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-run/)
   >
   >
   >Je nach der Oak-Version, die Sie für Ihre AEM-Installation verwenden, müssen verschiedene Versionen des Tools verwendet werden. Überprüfen Sie die nachstehende Liste der Versionsanforderungen, bevor Sie das Tool verwenden:
   >
   >
   >
   >    * Setzen Sie für die Oak-Versionen **1.2.x** das oak-run-Tool der Version **1.2.12 oder höher** ein.
   >    * Für **neuere** Oak-Versionen verwenden Sie die oak-run-Version, die dem Oak-Core der AEM-Installation entspricht.


1. Validieren Sie abschließend die Konfiguration. Suchen Sie zur Validierung nach einer eindeutigen Datei, die dem Datenspeicher von jedem Repository hinzugefügt wird, das sie weitergibt. Das Format der Dateien ist `repository-[UUID]`, wobei die UUID für eine eindeutige Kennung jedes Repositorys steht.

   Daher sollte eine ordnungsgemäße Konfiguration so viele eindeutige Dateien enthalten wie Repositorys, die den Datenspeicher gemeinsam nutzen.

   Die Dateien werden je nach Datenspeicher unterschiedlich gespeichert:

   * Für den `FileDataStore` werden die Dateien unter dem Stammverzeichnis des Datenspeicherordners erstellt.
   * Für den `S3DataStore` werden die Dateien im konfigurierten S3-Bucket unter dem `META`-Ordner erstellt.

## Azure-Datenspeicher {#azure-data-store}

AEM kann so konfiguriert werden, dass Daten im Azure-Speicherdienst von Microsoft® gespeichert werden. Zur Konfiguration wird die PID `org.apache.jackrabbit.oak.plugins.blob.datastore.AzureDataStore.config` verwendet.

Um die Azure-Datenspeicherfunktion zu aktivieren, muss ein Feature Pack mit dem Azure Connector heruntergeladen und installiert werden. Gehen Sie zum [Adobe-Repository](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.azureblobconnector/) und laden Sie die neueste Version der 1.6.x-Versionen des Feature Packs herunter (z. B. com.adobe.granite.oak.azureblobconnector-1.6.3.zip).

>[!NOTE]
>
>Bei Verwendung von AEM mit TarMK werden die Binärdateien standardmäßig im FileDataStore gespeichert. Um TarMK mit dem Azure DataStore zu verwenden, müssen Sie AEM verwenden. `crx3tar-nofds` runmode, z. B.:

```shell
java -jar <aem-jar-file>.jar -r crx3tar-nofds
```

Nach dem Download können Sie den Azure-Connector wie folgt installieren und konfigurieren:

1. Extrahieren Sie den Inhalt der ZIP-Datei des Feature Packs in einen temporären Ordner.

1. Gehen Sie zum temporären Ordner und kopieren Sie den Inhalt von `jcr_root/libs/system/install` in den Ordner `<aem-install>crx-quickstart/install`.
1. Wenn AEM bereits für Tar- oder MongoDB-Speicher konfiguriert ist, entfernen Sie etwaig vorhandene Konfigurationsdateien aus dem Ordner `/crx-quickstart/install`, bevor Sie fortfahren. Die zu entfernenden Dateien sind:

   FürMongoMK:

   `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

   Für TarMK:

   `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`

1. Kehren Sie zu dem temporären Verzeichnis mit dem extrahierten Feature Pack zurück und kopieren Sie den Inhalt von `jcr_root/libs/system/config` in den Ordner `<aem-install>/crx-quickstart/install`.
1. Bearbeiten Sie die Konfigurationsdatei und fügen Sie die für Ihr Setup erforderlichen Konfigurationsoptionen hinzu.
1. Starten Sie AEM.

Sie können die Konfigurationsdatei mit den folgenden Optionen verwenden:

* azureSas=&quot;&quot;: In der Connector-Version 1.6.3 wurde Unterstützung für Azure Shared Access Signature (SAS) hinzugefügt. **Wenn in der Konfigurationsdatei sowohl SAS als auch Speicheranmeldeinformationen vorhanden sind, hat SAS Priorität.** Weitere Informationen zu SAS finden Sie in der [offiziellen Dokumentation](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview). Stellen Sie sicher, dass &#39;=&#39; wie folgt mit Escapezeichen versehen ist &#39;\=&#39;.

* azureBlobEndpoint=&quot;&quot;: Der Azure-Blob-Endpunkt, z. B. https://&lt;Speicherkonto>.blob.core.windows.net.
* accessKey=&quot;&quot;: Der Speicherkontoname. Weitere Informationen zu den Anmeldedaten für die Microsoft® Azure-Authentifizierung finden Sie im Abschnitt [amtliche Dokumentation](https://azure.microsoft.com/de-de/documentation/articles/storage-create-storage-account).

* secretKey=&quot;&quot;: Der Speicherzugriffsschlüssel. Stellen Sie sicher, dass &#39;=&#39; wie folgt mit Escapezeichen versehen ist &#39;\=&#39;.
* container=&quot;&quot;: Der Name des Microsoft® Azure Blob Storage-Containers. Der Container ist eine Gruppierung einer Gruppe von Blobs. Weitere Informationen finden Sie im Abschnitt [amtliche Dokumentation](https://learn.microsoft.com/en-us/rest/api/storageservices/Naming-and-Referencing-Containers--Blobs--and-Metadata?redirectedfrom=MSDN).
* maxConnections=&quot;&quot;: Die gleichzeitige Anzahl gleichzeitiger Anfragen pro Vorgang. Der Standardwert lautet 1.
* maxErrorRetry=&quot;&quot;: Die Anzahl der Wiederholungen pro Anfrage. Der Standardwert lautet 3.
* socketTimeout=&quot;&quot;: Das Zeitüberschreitungsintervall, in Millisekunden, für die Anfrage. Der Standardwert lautet 5 Minuten.

Neben den oben aufgeführten Einstellungen können auch die folgenden Einstellungen konfiguriert werden:

* path: Der Pfad des Datenspeichers. Standard: `<aem-install>/repository/datastore.`
* RecordLength: Die Mindestgröße eines Objekts, das im Datenspeicher gespeichert werden soll. Der Standardwert lautet 16 KB.
* maxCachedBinarySize: Binärdateien mit einer Größe kleiner oder gleich dieser Größe werden im Arbeitsspeicher-Cache gespeichert. Die Größe wird in Byte angegeben. Der Standardwert lautet 17408 (17 KB).
* cacheSize: Die Größe des Cache. Der Wert wird in Byte angegeben. Der Standardwert lautet 64 GB.
* secret: Darf nur bei einer nicht binären Replikation für freigegebene Datenspeicher verwendet werden.
* stagingSplitPercentage: Der Prozentsatz der Cachegröße, der zum Staging asynchroner Uploads konfiguriert ist. Der Standardwert lautet 10.
* uploadThreads: Die Anzahl der Uploadthreads für asynchrone Uploads. Der Standardwert lautet 10.
* stagingPurgeInterval: Das Intervall in Sekunden zum endgültigen Löschen abgeschlossener Uploads aus dem Staging-Cache. Der Standardwert lautet 300 Sekunden (5 Minuten).
* stagingRetryInterval: Das Wiederholungsintervall in Sekunden für fehlgeschlagene Uploads. Der Standardwert lautet 600 Sekunden (10 Minuten).

>[!NOTE]
>
>Alle Einstellungen sollten in Anführungszeichen gesetzt werden, z. B.:

```shell
accessKey="ASDASDERFAERAER"
secretKey="28932hfjlkwdo8fufsdfas\=\="
```

## Automatische Datenspeicherbereinigung {#data-store-garbage-collection}

Im Rahmen der automatischen Datenspeicherbereinigung werden nicht verwendete Dateien aus dem Datenspeicher entfernt. Dabei wird wertvoller Festplattenspeicher freigegeben.

Sie können die automatische Datenspeicherbereinigung wie folgt ausführen:

1. Wechseln Sie zur JMX-Konsole unter *https://&lt;serveraddress:port>/system/console/jmx*
1. Suchen nach **RepositoryManagement.** Sobald Sie das MBean &quot;Repository Manager&quot;gefunden haben, klicken Sie darauf, um die verfügbaren Optionen aufzurufen.
1. Scrollen Sie zum Ende der Seite und klicken Sie auf die Schaltfläche **startDataStoreGC(boolean markOnly)** Link.
1. Geben Sie im folgenden Dialogfeld für den Parameter `false` den Wert `markOnly` ein und klicken Sie auf **Invoke**:

   ![chlimage_1-9](assets/chlimage_1-9.png)

   >[!NOTE]
   >
   >Die `markOnly` -Parameter gibt an, ob die Sweep-Phase der Speicherbereinigung ausgeführt wird oder nicht.

## Datenspeicherbereinigung für einen freigegebenen Datenspeicher {#data-store-garbage-collection-for-a-shared-data-store}

>[!NOTE]
>
>Beim Ausführen der Speicherbereinigung in einem geclusterten oder freigegebenen Datenspeicher zeigt das Protokoll bei der Einrichtung (mit Mongo oder Segment Tar) möglicherweise Warnungen bezüglich der Unfähigkeit, bestimmte Blob-IDs zu löschen. Blob-IDs, die in einer vorherigen Speicherbereinigung gelöscht wurden, werden fälschlicherweise erneut von anderen Cluster- oder freigegebenen Knoten referenziert, die keine Informationen über die ID-Löschungen haben. Daher wird bei der automatischen Bereinigung eine Warnung protokolliert, wenn versucht wird, eine bereits im vorherigen Durchgang gelöschte ID zu entfernen. Dieses Verhalten wirkt sich weder auf die Leistung noch auf die Funktionalität aus.

>[!NOTE]
>
>Wenn Sie ein freigegebenes Datenspeicher-Setup verwenden und die automatische Speicherbereinigung deaktiviert ist, kann das Ausführen der Aufgabe „Lucene-Binärdatei-Bereinigung“ plötzlich den verwendeten Speicherplatz erhöhen. Deaktivieren Sie BlobTracker für alle Autoren- und Veröffentlichungsinstanzen, indem Sie Folgendes tun:
>
>1. Halten Sie die AEM-Instanz an.
>2. Fügen Sie den `blobTrackSnapshotIntervalInSecs=L"0"`-Parameter in der Datei `crx-quickstart/install/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` hinzu. Für diesen Parameter ist Oak 1.12.0, 1.10.2 oder höher erforderlich.
>3. Starten Sie die AEM-Instanz neu.


In neueren AEM-Versionen kann die automatische Datenspeicherbereinigung auch in einem Datenspeicher durchgeführt werden, der von mehreren Repositorys genutzt wird. Um die automatische Datenspeicherbereinigung in einem freigegebenen Datenspeicher ausführen zu können, gehen Sie wie folgt vor:

1. Stellen Sie sicher, dass alle für die Datenspeicherbereinigung konfigurierten Wartungsaufgaben auf allen Repository-Instanzen, die den Datenspeicher gemeinsam nutzen, deaktiviert sind.
1. Führen Sie die unter [Binäre Speicherbereinigung](/help/sites-deploying/data-store-config.md#data-store-garbage-collection) einzeln auf **all** Repository-Instanzen, die den Datenspeicher gemeinsam nutzen. Achten Sie jedoch darauf, den Wert `true` für den Parameter `markOnly` einzugeben, bevor Sie auf die Schaltfläche „Invoke“ klicken:

   ![chlimage_1-10](assets/chlimage_1-10.png)

1. Führen Sie nach Abschluss des obigen Verfahrens auf allen Instanzen die Datenspeicherbereinigung erneut aus. **any** der Instanzen:

   1. Wechseln Sie zur JMX-Konsole und wählen Sie das MBean Repository Manager aus.
   1. Klicken Sie auf **Klicken Sie auf startDataStoreGC(boolean markOnly)** Link.
   1. Geben Sie im folgenden Dialogfeld für den Parameter `false` erneut den Wert `markOnly` ein.
   Alle gefundenen Dateien werden mit der zuvor verwendeten Markierungsphase zusammengestellt und der Rest, der nicht verwendet wird, wird aus dem Datenspeicher gelöscht.
