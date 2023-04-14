---
title: Adobe Experience Manager mit MongoDB
description: Erfahren Sie mehr über die Aufgaben und Überlegungen, die für eine erfolgreiche Bereitstellung von Adobe Experience Manager mit MongoDB erforderlich sind.
uuid: 8028832d-10de-4811-a769-fab699c162ec
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: cd3b979f-53d4-4274-b4eb-a9533329192a
docset: aem65
exl-id: 70a39462-8584-4c76-a097-05ee436247b7
source-git-commit: af60428255fb883265ade7b2d9f363aacb84b9ad
workflow-type: tm+mt
source-wordcount: '6408'
ht-degree: 16%

---

# Adobe Experience Manager mit MongoDB{#aem-with-mongodb}

Dieser Artikel soll das Wissen über Aufgaben und Überlegungen verbessern, die für die erfolgreiche Bereitstellung von AEM (Adobe Experience Manager) mit MongoDB erforderlich sind.

Weitere Informationen zur Bereitstellung finden Sie im Abschnitt [Bereitstellung und Wartung](/help/sites-deploying/deploy.md) Abschnitt der Dokumentation.

## Verwendung von MongoDB mit AEM {#when-to-use-mongodb-with-aem}

MongoDB wird normalerweise zur Unterstützung AEM Autorenbereitstellungen verwendet, wenn eines der folgenden Kriterien erfüllt ist:

* mehr als 1000 Unique Users pro Tag;
* mehr als 100 gleichzeitige Benutzer;
* Hohe Anzahl von Seitenbearbeitungen;
* Große Rollouts oder Aktivierungen.

Die oben genannten Kriterien gelten nur für die Autoreninstanzen und nicht für Veröffentlichungsinstanzen, die alle auf TarMK basieren sollten. Die Anzahl der Benutzer bezieht sich auf authentifizierte Benutzer, da Autoreninstanzen keinen nicht authentifizierten Zugriff zulassen.

Wenn die Kriterien nicht erfüllt sind, wird eine aktive/Standby-Bereitstellung von TarMK/TarMK empfohlen, um die Verfügbarkeit zu verbessern. Im Allgemeinen sollte MongoDB in Situationen berücksichtigt werden, in denen die Skalierungsanforderungen größer sind als mit einem einzelnen Hardwareelement möglich.

>[!NOTE]
>
>Weitere Informationen zur Größenanpassung von Autoreninstanzen und zur Definition gleichzeitiger Benutzer finden Sie in der [Richtlinien zur Hardware-Skalierung](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel).

### Minimale MongoDB-Bereitstellung für AEM {#minimal-mongodb-deployment-for-aem}

Nachfolgend finden Sie eine minimale Bereitstellung für AEM auf MongoDB. Zur Vereinfachung wurden SSL-Terminierung und HTTP-Proxy-Komponenten verallgemeinert. Die Bereitstellung besteht aus einer einzigen MongoDB-Replikatgruppe mit einem primären Replikat und zwei sekundären Replikaten.

![chlimage_1-4](assets/chlimage_1-4.png)

Eine minimale Bereitstellung erfordert drei `mongod` Instanzen, die als Replikatsatz konfiguriert sind. Eine Instanz wird primär gewählt, während die anderen Instanzen sekundär sind, wobei die Wahl von `mongod`. Angebunden an jede Instanz ist eine lokale Festplatte. So kann der Cluster die Auslastung unterstützen. Es wird ein Mindestdurchsatz von 12 MB pro Sekunde mit mehr als 3000 I/O Operations per Second (IOPS) empfohlen.

Die AEM-Autoren sind mit den `mongod`-Instanzen verbunden, wobei jeweils eine Verbindung zu allen drei `mongod`-Instanzen besteht. Schreibvorgänge werden an die primäre Instanz gesendet und Lesevorgänge können von jeder der Instanzen gelesen werden. Der Traffic wird basierend auf dem Laden durch einen Dispatcher an eine der aktiven AEM Autoreninstanzen verteilt. Der Oak-Datenspeicher ist ein `FileDataStore`, und die MongoDB-Überwachung wird von MMS oder MongoDB Ops Manager abhängig vom Speicherort der Bereitstellung bereitgestellt. Die Betriebssystemebene und die Protokollüberwachung werden von Drittanbieterlösungen wie Splunk oder Ganglia bereitgestellt.

In dieser Bereitstellung sind alle Komponenten für eine erfolgreiche Implementierung erforderlich. Jede fehlende Komponente lässt die Implementierung nicht funktionsfähig.

### Betriebssysteme {#operating-systems}

Eine Aufstellung der unterstützten Betriebssysteme für AEM 6 finden Sie auf der Seite [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Umgebungen {#environments}

Virtualisierte Umgebungen werden unterstützt, sofern eine gute Kommunikation zwischen den verschiedenen technischen Teams besteht, die das Projekt durchführen. Zu diesem Support gehören das Team, das AEM führt, das Team, das Eigentümer des Betriebssystems ist, und das Team, das die virtualisierte Infrastruktur verwaltet.

Es gibt spezifische Anforderungen an die I/O-Kapazität der MongoDB-Instanzen, die vom Team verwaltet werden müssen, das die virtualisierte Umgebung verwaltet. Wenn das Projekt eine Cloud-Implementierung wie Amazon Web Services verwendet, müssen Instanzen mit ausreichender I/O-Kapazität und Konsistenz bereitgestellt werden, um die MongoDB-Instanzen zu unterstützen. Andernfalls führen die MongoDB-Prozesse und das Oak-Repository unzuverlässig und fehlerhaft aus.

In virtualisierten Umgebungen erfordert MongoDB spezifische I/O- und VM-Konfigurationen, um sicherzustellen, dass die Speichermodul-Engine von MongoDB nicht durch VMWare-Richtlinien zur Ressourcenzuordnung beeinträchtigt wird. Eine erfolgreiche Implementierung stellt sicher, dass es keine Hindernisse zwischen den verschiedenen Teams gibt und alle sich für die erforderliche Leistung angemeldet haben.

## Hardwareaspekte {#hardware-considerations}

### Speicherung {#storage}

Um den Lese- und Schreibdurchsatz für optimale Leistung ohne vorzeitige horizontale Skalierung zu erreichen, benötigt MongoDB im Allgemeinen SSD-Speicher oder -Speicher mit einer SSD-gleichwertigen Leistung.

### RAM {#ram}

MongoDB-Versionen 2.6 und 3.0, die die MMAP-Speicher-Engine verwenden, erfordern, dass der Arbeitssatz der Datenbank und deren Indizes in RAM passen.

Unzureichender RAM führt zu einer deutlichen Leistungsminderung. Die Größe des Workflows und der Datenbank hängt stark von der Anwendung ab. Während einige Schätzungen vorgenommen werden können, ist die zuverlässigste Methode, die erforderliche RAM-Menge zu bestimmen, die Erstellung der AEM-Anwendung und die Belastungsprüfung.

Um den Lasttest zu unterstützen, kann das folgende Verhältnis zwischen Arbeitssatz und Gesamtdatenbankgröße angenommen werden:

* 1:10 für SSD-Speicher
* 1:3 für Festplattenspeicher

Diese Verhältnisse bedeuten, dass für SSD-Bereitstellungen 200 GB RAM für eine 2 TB große Datenbank erforderlich sind.

Die gleichen Einschränkungen gelten für das WiredTiger-Speichermodul in MongoDB 3.0, aber die Korrelation zwischen Arbeitsset, RAM und Seitenfehlern ist nicht so stark. WiredTiger verwendet die Speicherzuordnung nicht auf die gleiche Weise wie die MMAP-Speicher-Engine.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung der WiredTiger-Speicher-Engine für AEM 6.1-Bereitstellungen, die MongoDB 3.0 verwenden.

### Datenspeicher {#data-store}

Aufgrund der Einschränkungen des MongoDB-Arbeitssatzes wird empfohlen, den Datenspeicher unabhängig von der MongoDB zu verwalten. In den meisten Umgebungen ist ein `FileDataStore` Verwenden Sie einen NAS, der für alle AEM Instanzen verfügbar ist. Wird Amazon Web Services genutzt, steht auch ein `S3 DataStore` zur Verfügung. Wenn der Datenspeicher aus irgendeinem Grund innerhalb von MongoDB verwaltet wird, sollte die Größe des Datenspeichers der gesamten Datenbankgröße hinzugefügt und die Arbeitsset-Berechnungen entsprechend angepasst werden. Diese Größenanpassung kann bedeuten, dass mehr RAM bereitgestellt wird, um die Leistung ohne Seitenfehler zu gewährleisten.

## Überwachung {#monitoring}

Überwachung ist für eine erfolgreiche Umsetzung des Projekts von entscheidender Bedeutung. Mit ausreichendem Wissen ist es möglich, AEM auf MongoDB ohne Überwachung auszuführen. Diese Kenntnisse finden sich jedoch normalerweise in Ingenieuren, die für jeden Abschnitt des Einsatzes spezialisiert sind.

Dieses Fachwissen umfasst in der Regel einen F&amp;E-Ingenieur, der am Apache Oak Core arbeitet, und einen MongoDB-Spezialisten.

Ohne Überwachung auf allen Ebenen sind detaillierte Kenntnisse der Codebasis erforderlich, um Probleme zu diagnostizieren. Durch die vorhandene Überwachung und geeignete Anleitungen zu den wichtigsten Statistiken können Implementierungsteams angemessen auf Anomalien reagieren.

Es ist zwar möglich, Befehlszeilen-Tools zu verwenden, um einen schnellen Überblick über den Betrieb eines Clusters zu erhalten, doch ist es fast unmöglich, dies in Echtzeit über viele Hosts durchzuführen. Befehlszeilen-Tools geben nur selten historische Informationen nach einigen Minuten zurück und ermöglichen nie eine Kreuzkorrelation zwischen verschiedenen Metriktypen. Ein kurzer Zeitraum langsamer `mongod`-Hintergrundsynchronisierungen bedeutet zusätzlichen manuellen Aufwand, um I/O-Wartezeiten oder übermäßige Write-Level mit einer freigegebenen Speicherressource von einer scheinbar nicht verbundenen virtuellen Maschine in Beziehung zu setzen.

### MongoDB Cloud Manager {#mongodb-cloud-manager}

MongoDB Cloud Manager ist ein kostenloser Dienst von MongoDB, der die Überwachung und Verwaltung von MongoDB-Instanzen ermöglicht. Es bietet einen Überblick über die Leistung und den Zustand des MongoDB-Clusters in Echtzeit. Es verwaltet sowohl Cloud- als auch privat gehostete Instanzen, sofern die Instanz den Cloud Manager-Überwachungsserver erreichen kann.

Voraussetzung ist die Installation eines Agenten auf der MongoDB-Instanz, der mit dem Überwachungsserver verbunden ist. Es gibt drei Ebenen des Agenten:

* Ein Automatisierungsagent, der alles auf dem MongoDB-Server vollständig automatisieren kann,
* Einen Überwachungsagenten, der die `mongod`-Instanz überwachen kann
* Ein Backup-Agent, der geplante Sicherungen der Daten durchführen kann.

Obwohl die Verwendung von Cloud Manager zur Wartungsautomatisierung eines MongoDB-Clusters viele der Routineaufgaben vereinfacht, ist dies nicht erforderlich und wird auch nicht für die Sicherung verwendet. Bei der Wahl von Cloud Manager zur Überwachung ist jedoch eine Überwachung erforderlich.

Weitere Informationen zu MongoDB Cloud Manager finden Sie in der [MongoDB-Dokumentation](https://docs.cloud.mongodb.com/).

### MongoDB Ops Manager {#mongodb-ops-manager}

MongoDB Ops Manager ist dieselbe Software wie MongoDB Cloud Manager. Nach der Registrierung kann Ops Manager lokal in einem privaten Rechenzentrum oder auf einem anderen Laptop oder Desktop-Computer heruntergeladen und installiert werden. Es verwendet eine lokale MongoDB-Datenbank, um Daten zu speichern und auf dieselbe Weise wie Cloud Manager mit den verwalteten Servern zu kommunizieren. Wenn Sie Sicherheitsrichtlinien haben, die einen Überwachungsagenten verbieten, sollte MongoDB Ops Manager verwendet werden.

### Betriebssystemüberwachung {#operating-system-monitoring}

Zum Ausführen eines AEM MongoDB-Clusters ist eine Überwachung auf Betriebssystemebene erforderlich.

Ganglia ist ein gutes Beispiel für ein solches System und liefert ein Bild über die Bandbreite und Details der benötigten Informationen, die über grundlegende Gesundheitsmetriken wie CPU, Lastdurchschnitt und freien Speicherplatz hinausgehen. Um Probleme zu diagnostizieren, sind niedrigere Informationen wie Entropy-Pool-Ebenen, CPU-I/O-Wartezeit, Sockets im FIN_WAIT2-Status erforderlich.

### Logaggregate {#log-aggregation}

Bei einem Cluster aus mehreren Servern ist die zentrale Protokollaggregation eine Voraussetzung für ein Produktionssystem. Software wie Splunk unterstützt die Protokollierung und ermöglicht es Teams, die Verhaltensmuster der Anwendung zu analysieren, ohne die Protokolle manuell erfassen zu müssen.

## Checklisten {#checklists}

In diesem Abschnitt werden die verschiedenen Schritte beschrieben, die Sie unternehmen sollten, um sicherzustellen, dass Ihre AEM- und MongoDB-Bereitstellungen vor der Implementierung Ihres Projekts ordnungsgemäß eingerichtet sind.

### Netzwerk {#network}

1. Stellen Sie zunächst sicher, dass alle Hosts einen DNS-Eintrag haben.
1. Alle Hosts sollten durch ihren DNS-Eintrag von allen anderen routbaren Hosts aufgelöst werden können
1. Alle MongoDB-Hosts sind von allen anderen MongoDB-Hosts im selben Cluster routbar
1. MongoDB-Hosts können Pakete an MongoDB Cloud Manager und die anderen Überwachungsserver weiterleiten
1. AEM Server können Pakete an alle MongoDB-Server weiterleiten
1. Die Paketlatenz zwischen einem beliebigen AEM-Server und einem MongoDB-Server ist kleiner als zwei Millisekunden, ohne Paketverlust und mit einer Standardverteilung von einer Millisekunde oder weniger.
1. Stellen Sie sicher, dass zwischen einem AEM und einem MongoDB-Server nicht mehr als zwei Hopfen vorhanden sind.
1. Zwischen zwei MongoDB-Servern gibt es nicht mehr als zwei Hopfen
1. Es gibt keine Router, die höher sind als OSI Level 3 zwischen Kernservern (MongoDB oder AEM oder einer Kombination).
1. Wenn VLAN-Trunking oder eine Netzwerktunnelung verwendet wird, muss es den Paketlatenzprüfungen entsprechen.

### AEM {#aem-configuration}

#### Knotenspeicherkonfiguration {#node-store-configuration}

Die AEM Instanzen müssen für die Verwendung von AEM mit MongoMK konfiguriert werden. Die Grundlage der MongoMK-Implementierung in AEM ist der Document Node Store.

Weitere Informationen zum Konfigurieren von Knotenspeichern finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM](/help/sites-deploying/data-store-config.md).

Nachfolgend finden Sie ein Beispiel für die Konfiguration des Knotenspeichers für eine minimale MongoDB-Bereitstellung:

```xml
# org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config
#MongoDB server details
mongodburi=mongodb://aem:aempassword@mongodbserver1.customer.com:27000,mongodbserver2.customer.com:27000

#Name of MongoDB database to use
db=aem

#Store binaries in custom BlobStore e.g. FileDataStore
customBlobStore=true

cache=2048
blobCacheSize=1024
```

Dabei gilt:

* `mongodburi`
Der MongoDB-AEM muss eine Verbindung herstellen. Verbindungen werden zu allen bekannten Mitgliedern des standardmäßigen Replikatsatzes hergestellt. Wenn MongoDB Cloud Manager verwendet wird, ist die Serversicherheit aktiviert. Daher muss die Verbindungszeichenfolge einen geeigneten Benutzernamen und ein passendes Kennwort enthalten. Nicht-Enterprise-Versionen von MongoDB unterstützen nur die Authentifizierung von Benutzernamen und Passwörtern. Weitere Informationen zur Syntax der Verbindungszeichenfolge finden Sie im Abschnitt [Dokumentation](https://docs.mongodb.org/manual/reference/connection-string/).

* `db`
Der Name der Datenbank. Der Standardwert für AEM lautet 
`aem-author`.

* `customBlobStore`
Wenn die Bereitstellung Binärdateien in der Datenbank speichert, sind sie Teil des Workflows. Aus diesem Grund wird empfohlen, Binärdateien nicht in MongoDB zu speichern, sondern stattdessen einen alternativen Datenspeicher wie einen 
`FileSystem`-Datenspeicher in einem NAS.

* `cache`
Die Cachegröße in Megabyte. Dieser Bereich ist auf verschiedene Caches verteilt, die im 
`DocumentNodeStore`. Die Standardgröße ist 256 MB. Die Leistung des Oak-Lesens profitiert jedoch von einem größeren Cache.

* `blobCacheSize`
Häufig verwendete Blobs können von AEM im Cache gespeichert werden. So wird vermieden, dass sie erneut aus dem Datenspeicher abgerufen werden. Dies wirkt sich stärker auf die Leistung aus, insbesondere beim Speichern von Blobs in der MongoDB-Datenbank. Alle dateisystembasierten Datenspeicher profitieren vom Datenträgercache auf Betriebssystemebene.

#### Datenspeicherkonfiguration {#data-store-configuration}

Der Datenspeicher dient zum Speichern von Dateien mit einer Größe, die größer als ein Schwellenwert ist. Unter diesem Schwellenwert werden Dateien als Eigenschaften im Knotenspeicher &quot;Dokument&quot;gespeichert. Wenn der `MongoBlobStore` verwendet wird, wird in MongoDB eine dedizierte Sammlung zum Speichern der Blobs erstellt. Diese Sammlung trägt zum Arbeitssatz der `mongod` -Instanz und erfordert, dass `mongod` verfügt über mehr RAM, um Leistungsprobleme zu vermeiden. Aus diesem Grund wird empfohlen, die `MongoBlobStore` für Produktionsbereitstellungen und -nutzung `FileDataStore` unterstützt durch einen NAS, der von allen AEM Instanzen gemeinsam genutzt wird. Da der Cache auf Betriebssystemebene bei der Verwaltung von Dateien effizient ist, sollte die Mindestgröße einer Datei auf dem Datenträger auf die Blockgröße der Festplatte eingestellt werden. Dadurch wird sichergestellt, dass das Dateisystem effizient verwendet wird und viele kleine Dokumente nicht übermäßig zum Arbeitsbereich der `mongod` -Instanz.

Es folgt ein Beispiel einer typischen Datenspeicherkonfiguration für eine minimale AEM-Bereitstellung mit MongoDB:

```xml
# org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config
# The minimum size of an object that should be stored in this data store.
minRecordLength=4096
path=/datastore
maxCachedBinarySize=4096
cacheSizeInMB=128
```

Dabei gilt:

* `minRecordLength`
Größe in Byte. Binärdateien, die kleiner oder gleich dieser Größe sind, werden mit dem Document Node Store gespeichert. Anstatt die Kennung des Blob zu speichern, wird der Inhalt der Binärdatei gespeichert. Bei Binärdateien, die größer als diese Größe sind, wird die ID der Binärdatei als Eigenschaft des Dokuments in der Knotensammlung gespeichert. Und der Hauptteil der Binärdatei wird im 
`FileDataStore` auf der Festplatte. 4096 Byte entspricht einer typischen Dateisystem-Blockgröße.

* `path`
Der Pfad zum Stamm des Datenspeichers. Bei einer MongoMK-Bereitstellung muss dieser Pfad ein freigegebenes Dateisystem sein, das für alle AEM Instanzen verfügbar ist. Normalerweise wird ein NAS-Server (Network Attached Storage) verwendet. Bei Cloud-Implementierungen wie Amazon Web Services ist der 
`S3DataFileStore` ebenfalls verfügbar.

* `cacheSizeInMB`
Die Gesamtgröße des Binärdatencache in Megabyte. Damit werden Binärdateien im Cache gespeichert, deren Wert unterhalb der 
Einstellung `maxCacheBinarySize` liegt.

* `maxCachedBinarySize`
Die maximale Größe in Byte der im Binärdatencache gespeicherten Binärdatei. Wenn ein dateisystembasierter Datenspeicher verwendet wird, wird die Verwendung hoher Werte für den Datenspeicher-Cache nicht empfohlen, da die Binärdateien bereits vom Betriebssystem zwischengespeichert werden.

#### Deaktivieren des Abfragehinweises {#disabling-the-query-hint}

Es wird empfohlen, den mit allen Abfragen gesendeten Abfragehinweis zu deaktivieren, indem Sie die Eigenschaft `-Doak.mongo.disableIndexHint=true` wenn Sie AEM beginnen. Dadurch wird sichergestellt, dass MongoDB anhand interner Statistiken den am besten geeigneten Index berechnet.

Wenn der Abfragehinweis nicht deaktiviert ist, hat eine Leistungsoptimierung von Indizes keine Auswirkungen auf die Leistung von AEM.

#### Persistenten Cache für MongoMK aktivieren {#enable-persistent-cache-for-mongomk}

Es wird empfohlen, eine persistente Cache-Konfiguration für MongoDB-Bereitstellungen zu aktivieren, um die Geschwindigkeit für Umgebungen mit hoher I/O-Leseleistung zu maximieren. Weitere Informationen finden Sie unter [Jackrabbit Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/nodestore/persistent-cache.html).

## MongoDB-Betriebssystemoptimierungen {#mongodb-operating-system-optimizations}

### Betriebssystemunterstützung {#operating-system-support}

MongoDB 2.6 verwendet eine Speichermodul-Engine, die für einige Aspekte der Verwaltung auf Betriebssystemebene zwischen RAM und Datenträger sensibilisiert ist. Die Abfrage- und Leseleistung der MongoDB-Instanz beruht darauf, langsame I/O-Vorgänge, die häufig als Seitenfehler bezeichnet werden, zu vermeiden oder zu beseitigen. Bei diesen Problemen handelt es sich um Seitenfehler, die für die `mongod` insbesondere Verwechseln Sie nicht mit Seitenfehlern auf Betriebssystemebene.

Für einen schnellen Betrieb sollte die MongoDB-Datenbank nur auf Daten zugreifen, die sich bereits im RAM befinden. Die Daten, auf die sie zugreifen muss, bestehen aus Indizes und Daten. Diese Sammlung von Indizes und Daten wird als Arbeitssatz bezeichnet. Wenn der Arbeitssatz größer als der verfügbare RAM ist, muss MongoDB diese Daten von einem Datenträger eintragen, der I/O-Kosten verursacht, und andere Daten, die bereits im Speicher sind, entfernen. Wenn die Entfernung dazu führt, dass Daten von der Festplatte neu geladen werden, dominieren Seitenfehler und die Leistung verschlechtert sich. Wenn der Arbeitssatz dynamisch und variabel ist, treten mehr Seitenfehler auf, um Vorgänge zu unterstützen.

MongoDB läuft auf verschiedenen Betriebssystemen, einschließlich einer Vielzahl von Linux®-Versionen, Windows und macOS. Siehe [https://docs.mongodb.com/manual/installation/#supported-platforms](https://docs.mongodb.com/manual/installation/#supported-platforms) für weitere Details. Je nach Wahl Ihres Betriebssystems bietet MongoDB verschiedene Empfehlungen auf Betriebssystemebene. Die Dokumentation finden Sie unter [https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration](https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration) und zusammengefasst hier aus Gründen der Bequemlichkeit.

#### Linux® {#linux}

* Deaktivieren Sie transparente hugepages und defrag. Siehe [Transparent Huge Pages Settings](https://docs.mongodb.com/manual/tutorial/transparent-huge-pages/) für weitere Informationen.
* [Anpassen der readahead-Einstellungen](https://docs.mongodb.com/manual/administration/production-notes/#readahead) auf den Geräten, auf denen Ihre Datenbankdateien gespeichert werden, sodass Sie zu Ihrem Anwendungsfall passen.

   * Wenn für die MMAPv1-Speicher-Engine der verfügbare Arbeitsspeicher größer ist und das Zugriffsmuster für Dokumente zufällig ist, sollten Sie erwägen, die Vorausplanung auf 32 oder 16 zu reduzieren. Bewerten Sie verschiedene Einstellungen, damit Sie einen optimalen Wert finden können, der den residierenden Speicher maximiert und die Anzahl der Seitenfehler verringert.
   * Legen Sie für die WiredTiger-Speicher-Engine readahead auf 0 fest, unabhängig vom Speichermedientyp (Spinnen, SSD usw.). Verwenden Sie im Allgemeinen die empfohlene readahead-Einstellung, es sei denn, Tests zeigen einen messbaren, wiederholbaren und zuverlässigen Nutzen in einem höheren readahead-Wert. [MongoDB Professional Support](https://docs.mongodb.com/manual/administration/production-notes/#readahead) kann Ratschläge und Anleitungen zu readahead-Konfigurationen ungleich null geben.

* Deaktivieren Sie das angepasste Tool, wenn Sie RHEL 7/CentOS 7 in einer virtuellen Umgebung ausführen.
* Wenn RHEL 7/CentOS 7 in einer virtuellen Umgebung ausgeführt wird, ruft das angepasste Tool automatisch ein aus dem Leistungsdurchsatz abgeleitetes Leistungsprofil auf, das die readahead-Einstellungen automatisch auf 4 MB festlegt. Diese Einstellung kann sich negativ auf die Leistung auswirken.
* Verwenden Sie die Noop- oder Deadline-Scheduler für SSD-Laufwerke.
* Verwenden Sie den noop Disk Scheduler für virtualisierte Laufwerke in Gast-VMs.
* NUMA deaktivieren oder festlegen `vm.zone_reclaim_mode` auf 0 und ausführen [mongod](https://docs.mongodb.com/manual/administration/production-notes/#readahead) Instanzen mit Knotenwechselschaltung. Siehe: [MongoDB und NUMA Hardware](https://docs.mongodb.com/manual/administration/production-notes/#readahead) für weitere Informationen.

* Passen Sie die ulimit -Werte auf Ihrer Hardware so an, dass sie Ihrem Anwendungsfall entsprechen. Wenn mehrere [mongod](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) oder [mongos](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos) -Instanzen unter demselben Benutzer ausgeführt werden, skalieren Sie die ulimit -Werte entsprechend. Siehe: [UNIX® ulimit Settings](https://docs.mongodb.com/manual/reference/ulimit/) für weitere Informationen.

* Verwenden Sie noatime für die [dbPath](https://docs.mongodb.com/manual/reference/configuration-options/#storage.dbPath) Einhängepunkt.
* Konfigurieren Sie ausreichende Dateigriffe (fs.file-max), die Pid-Grenze des Kernels (kernel.pid_max) und die maximalen Threads pro Prozess (kernel.threads-max) für Ihre Implementierung. Für große Systeme bieten die folgenden Werte einen guten Ausgangspunkt:

   * fs.file-max -Wert 98000,
   * kernel.pid_max -Wert von 64000,
   * andkernel.threads-max -Wert von 64000

* Stellen Sie sicher, dass auf Ihrem System der Austauschraum konfiguriert ist. Weitere Informationen zur geeigneten Größe finden Sie in der Dokumentation Ihres Betriebssystems .
* Vergewissern Sie sich, dass der standardmäßige TCP-Keepalive des Systems korrekt eingestellt ist. Der Wert 300 bietet häufig eine bessere Leistung für Replikatsätze und freigegebene Cluster. Siehe: [Beeinflusst die TCP-Lebensdauer MongoDB-Bereitstellungen?](https://docs.mongodb.com/manual/faq/diagnostics/#faq-keepalive) in den häufig gestellten Fragen für weitere Informationen.

#### Windows {#windows}

* Deaktivieren Sie gegebenenfalls die Aktualisierung des NTFS-Attributs „Last Access Time“. Diese Einstellung entspricht der Deaktivierung von atime auf Unix-ähnlichen Systemen.

### WiredTiger {#wiredtiger}

Ab MongoDB 3.2 ist die standardmäßige Speichermodul-Engine für MongoDB die WiredTiger-Speicher-Engine. Diese Engine bietet einige robuste und skalierbare Funktionen, wodurch sie für allgemeine Datenbankarbeitslasten viel besser geeignet ist. Die folgenden Abschnitte beschreiben diese Funktionen.

#### Parallelität auf Dokumentebene {#document-level-concurrency}

WiredTiger verwendet die Parallelitätssteuerung auf Dokumentebene für Schreibvorgänge. Dadurch können mehrere Clients verschiedene Dokumente einer Sammlung gleichzeitig ändern.

Für die meisten Lese- und Schreibvorgänge verwendet WiredTiger eine optimistische Parallelitätssteuerung. WiredTiger verwendet nur Intent-Sperren auf globaler, Datenbank- und Sammlungsebene. Wenn das Speicher-Engine Konflikte zwischen zwei Vorgängen erkennt, kommt es zu einem Schreibkonflikt, der dazu führt, dass MongoDB diesen Vorgang transparent erneut versucht. Einige globale Vorgänge, normalerweise kurzlebige Vorgänge mit mehreren Datenbanken, erfordern weiterhin eine globale &quot;Instanz-weite&quot;Sperre.

Für einige andere Vorgänge wie das Ablegen einer Sammlung ist weiterhin eine exklusive Datenbanksperre erforderlich.

#### Schnappschüsse und Checkpoints {#snapshots-and-checkpoints}

WiredTiger verwendet die MultiVersion Concurrency Control (MVCC). Zu Beginn eines Vorgangs liefert WiredTiger einen Point-in-Time-Schnappschuss der Daten für die Transaktion. Ein Snapshot zeigt eine konsistente Ansicht der Arbeitsspeicherdaten.

Beim Schreiben auf die Festplatte schreibt WiredTiger alle in einem Snapshot enthaltenen Daten konsistent über alle Datendateien auf die Festplatte. Die jetzt [permanenten](https://docs.mongodb.com/manual/reference/glossary/#term-durable) Daten dienen als Checkpoint in den Datendateien. Der Checkpoint stellt sicher, dass die Datendateien bis einschließlich zum letzten Checkpoint konsistent sind. Das heißt, Checkpoints können als Wiederherstellungspunkte dienen.

MongoDB konfiguriert WiredTiger so, dass Checkpoints (d. h. das Schreiben der Momentaufnahmen-Daten auf die Festplatte) in Intervallen von 60 Sekunden oder 2 GB Journaldaten erstellt werden.

Während des Schreibens eines neuen Checkpoints ist der vorherige Checkpoint weiterhin gültig. Selbst wenn MongoDB beim Schreiben eines neuen Checkpoints beendet oder auf einen Fehler stößt, kann MongoDB nach dem Neustart vom letzten gültigen Checkpoint abgerufen werden.

Der neue Checkpoint wird verfügbar und dauerhaft, wenn die Metadatentabelle von WiredTiger automatisch aktualisiert wird, um auf den neuen Checkpoint zu verweisen. Sobald der neue Checkpoint verfügbar ist, gibt WiredTiger Seiten von den alten Checkpoints frei.

Verwenden von WiredTiger, auch ohne [Journaling](https://docs.mongodb.com/manual/reference/glossary/#term-durable), kann MongoDB vom letzten Checkpoint abgerufen werden. Um jedoch Änderungen wiederherzustellen, die nach dem letzten Checkpoint vorgenommen wurden, führen Sie mit [Journaling](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Journal {#journal}

WiredTiger verwendet eine Write-Ahead-Transaktionsanmeldung-Kombination mit [Checkpoints](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-checkpoints) zur Gewährleistung der Datenbeständigkeit.

Das WiredTiger-Journal behält alle Datenänderungen zwischen Checkpoints bei. Wenn MongoDB zwischen Checkpoints beendet wird, verwendet es das Journal, um alle seit dem letzten Checkpoint geänderten Daten wiederzugeben. Informationen zur Häufigkeit, mit der MongoDB die Journaldaten auf die Festplatte schreibt, finden Sie unter [Journalprozess](https://docs.mongodb.com/manual/core/journaling/#journal-process).

Das WiredTiger-Journal wird mithilfe der [snappy](https://docs.mongodb.com/manual/core/journaling/#journal-process) Komprimierungsbibliothek. Verwenden Sie zum Angeben eines alternativen Komprimierungsalgorithmus oder einer Komprimierung die [storage.wiredTiger.engineConfig.journalCompressor](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.journalCompressor) -Einstellung.

Siehe [Journaling with WiredTiger](https://docs.mongodb.com/manual/core/journaling/#journaling-wiredtiger).

>[!NOTE]
>
>Die minimale Protokolldatensatzgröße für WiredTiger beträgt 128 Byte. Wenn ein Protokolldatensatz 128 Byte oder kleiner ist, komprimiert WiredTiger diesen Datensatz nicht.
>
>Sie können das Journal deaktivieren, indem Sie für [storage.journal.enabled](https://docs.mongodb.com/manual/reference/configuration-options/#storage.journal.enabled) „false“ festlegen. So können Sie den Mehraufwand für die Pflege des Journals verringern.
>
>Für [standalone](https://docs.mongodb.com/manual/reference/glossary/#term-standalone) -Instanzen bedeutet die Nichtverwendung des -Journals, dass Sie einige Datenänderungen verlieren, wenn MongoDB unerwartet zwischen Checkpoints beendet wird. Für Mitglieder von [Replikatsätze](https://docs.mongodb.com/manual/reference/glossary/#term-replica-set)kann der Replikationsprozess ausreichende Dauerhaltbarkeitsgarantien bieten.

#### Komprimierung {#compression}

Mit WiredTiger unterstützt MongoDB die Komprimierung für alle Sammlungen und Indizes. Die Komprimierung minimiert den Speicherverbrauch auf Kosten zusätzlicher CPU.

WiredTiger nutzt standardmäßig die Blockkomprimierung der [snappy](https://docs.mongodb.com/manual/reference/glossary/#term-snappy)-Komprimierungsbibliothek für alle Sammlungen und die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für alle Indizes.

Blockkomprimierung für Sammlungen mit [zlib](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) ist auch verfügbar. Verwenden Sie zum Angeben eines alternativen Komprimierungsalgorithmus oder einer Komprimierung die [storage.wiredTiger.collectionConfig.blockCompressor](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) -Einstellung.

Die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für Indizes können Sie mit der Einstellung [storage.wiredTiger.indexConfig.prefixCompression](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.indexConfig.prefixCompression) deaktivieren.

Die Komprimierungseinstellungen können während der Sammlung- und Indexerstellung auch pro Sammlung und Index konfiguriert werden. Siehe [Festlegen der Speicher-Engine-Optionen](https://docs.mongodb.com/manual/reference/method/db.createCollection/#create-collection-storage-engine-options) und [db.collection.createIndex() storageEngine](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/#createindex-options) -Option.

Bei den meisten Arbeitslasten stimmen die Standardkomprimierungseinstellungen über die Speichereffizienz und die Verarbeitungsanforderungen ab.

Das WiredTiger-Journal wird ebenfalls standardmäßig komprimiert. Informationen zur Journalkomprimierung finden Sie unter [Protokoll](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Speichernutzung {#memory-use}

Bei WiredTiger verwendet MongoDB sowohl den internen Cache von WiredTiger als auch den Dateisystemcache.

Ab Version 3.4 verwendet der interne Cache von WiredTiger standardmäßig den größeren von:

* 50 % RAM minus 1 GB oder
* 256 MB

WiredTiger verwendet standardmäßig die Snappy-Blockkomprimierung für alle Sammlungen und die Präfixkomprimierung für alle Indizes. Die Komprimierungsstandardwerte können global konfiguriert werden und können während der Sammlung- und Indexerstellung auch pro Sammlung und Index festgelegt werden.

Für Daten im internen Cache von WiredTiger werden unterschiedliche Darstellungen verwendet, verglichen mit dem On-Disk-Format:

* Die Daten im Dateisystem-Cache sind mit dem On-Disk-Format identisch, einschließlich der Vorteile einer Komprimierung für Datendateien. Der Dateisystemcache wird vom Betriebssystem verwendet, um die I/O der Festplatte zu reduzieren.

Indizes, die im internen Cache von WiredTiger geladen werden, weisen eine andere Datendarstellung auf als das On-Disk-Format, können aber dennoch die Indexpräfixkomprimierung nutzen, um die RAM-Nutzung zu reduzieren.

Die Indexpräfixkomprimierung dedupliziert allgemeine Präfixe aus indizierten Feldern.

Sammlungsdaten im internen Cache von WiredTiger sind unkomprimiert und verwenden eine andere Darstellung als das On-Disk-Format. Die Blockkomprimierung kann erhebliche Speichereinsparungen auf der Festplatte ermöglichen, doch müssen die Daten unkomprimiert werden, damit sie vom Server bearbeitet werden können.

Über den Dateisystemcache verwendet MongoDB automatisch alle freien Speicher, die nicht vom WiredTiger-Cache oder anderen Prozessen verwendet werden.

Informationen zum Anpassen der Größe des internen WiredTiger-Cache finden Sie unter [storage.wiredTiger.engineConfig.cacheSizeGB](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.cacheSizeGB) und [—wiredTigerCacheSizeGB](https://docs.mongodb.com/manual/reference/program/mongod/#cmdoption-wiredtigercachesizegb). Vermeiden Sie es, die interne Cachegröße von WiredTiger über den Standardwert zu erhöhen.

### NUMA {#numa}

NUMA (Non-Uniform Memory Access) ermöglicht es einem Kernel zu verwalten, wie Speicher den Prozessorkernen zugeordnet wird. Obwohl dieser Prozess versucht, den Speicherzugriff für Kerne zu beschleunigen, um sicherzustellen, dass sie auf die erforderlichen Daten zugreifen können, stört NUMA MMAP die Einführung zusätzlicher Latenzzeiten, da Lesevorgänge nicht vorhergesagt werden können. Daher muss NUMA für die Variable `mongod` auf allen leistungsfähigen Betriebssystemen.

Im Wesentlichen ist in einer NUMA-Architektur Speicher mit CPUs verbunden und CPUs sind mit einem Bus verbunden. In einer SMP- oder UMA-Architektur wird der Speicher mit dem Bus verbunden und von CPUs gemeinsam genutzt. Wenn ein Thread Speicher auf einer NUMA-CPU zuweist, wird er gemäß einer Richtlinie zugewiesen. Die Standardeinstellung besteht darin, Speicher zuzuweisen, der an die lokale CPU des Threads angehängt ist, es sei denn, es ist kein freier Speicher vorhanden. In diesem Fall wird Speicher von einer kostenlosen CPU zu höheren Kosten verwendet. Nach der Zuordnung bewegt sich der Speicher nicht zwischen den CPUs. Die Zuordnung wird von einer Richtlinie vorgenommen, die vom übergeordneten Thread übernommen wurde. Letztendlich ist dies der Thread, der den Prozess gestartet hat.

In vielen Datenbanken, die den Computer als eine mehrfache, einheitliche Speicherarchitektur betrachten, führt dieses Szenario dazu, dass die anfängliche CPU zuerst voll wird und die sekundäre CPU-Ausfüllung später. Dies gilt insbesondere dann, wenn ein zentraler Thread für die Zuordnung von Speicherpuffern verantwortlich ist. Die Lösung besteht darin, die NUMA-Richtlinie des Haupt-Threads zu ändern, der zum Starten der `mongod` verarbeiten, indem Sie den folgenden Befehl ausführen:

```shell
numactl --interleaved=all <mongod> -f config
```

Diese Richtlinie ordnet Speicher in einem runden Rund-Rund-Rund-Rund-Rad über alle CPU-Knoten zu, wodurch eine gleichmäßige Verteilung über alle Knoten gewährleistet ist. Sie generiert nicht den höchsten Leistungszugriff auf den Speicher wie in Systemen mit mehreren CPU-Hardware. Etwa die Hälfte der Speichervorgänge sind langsamer und über dem Bus, aber `mongod` wurde nicht so geschrieben, dass NUMA optimal in die Zielgruppe aufgenommen wurde, sodass es sich um einen vernünftigen Kompromiss handelt.

### NUMA-Probleme {#numa-issues}

Wenn die Variable `mongod` Der Prozess wird von einem anderen Speicherort als dem `/etc/init.d` -Ordner, ist es wahrscheinlich, dass er nicht mit der richtigen NUMA-Richtlinie gestartet wurde. Je nach Standardrichtlinie können Probleme entstehen. Der Grund dafür ist, dass die verschiedenen Linux® Package Manager-Installationsprogramme für MongoDB auch einen Dienst mit Konfigurationsdateien in `/etc/init.d` die den oben beschriebenen Schritt ausführen. Wenn Sie MongoDB direkt aus einem Archiv installieren und ausführen ( `.tar.gz`), müssen Sie mongod manuell unter der `numactl` Prozess.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren NUMA-Richtlinien finden Sie in der [numactl-Dokumentation](https://linux.die.net/man/8/numactl).

Der MongoDB-Prozess verhält sich bei verschiedenen Zuordnungsrichtlinien unterschiedlich:

```

```

* `-membind=<nodes>`
Die Zuordnung erfolgt nur auf den aufgeführten Knoten. Mongod weist auf den aufgelisteten Knoten keinen Speicher zu und verwendet möglicherweise nicht den gesamten verfügbaren Speicher.

* `-cpunodebind=<nodes>`
Führen Sie nur auf den Knoten aus. Mongod wird nur auf den angegebenen Knoten ausgeführt und verwendet nur den auf diesen Knoten verfügbaren Speicher.

* `-physcpubind=<nodes>`
Führen Sie nur auf aufgelisteten CPUs (Kerne) aus. Mongod wird nur auf den aufgelisteten CPUs ausgeführt und verwendet nur den Speicher, der auf diesen CPUs verfügbar ist.

* `--localalloc`
Speicher wird immer auf dem aktuellen Knoten zugewiesen, aber es werden alle Knoten verwendet, auf denen der Thread ausgeführt wird. Wenn ein Thread die Zuordnung durchführt, wird nur der für diese CPU verfügbare Speicher verwendet.

* `--preferred=<node>`
Zwar wird die Zuordnung zu einem bestimmten Knoten vorgezogen, es wird aber auf einen anderen Knoten zurückgegriffen, wenn der bevorzugte Knoten voll ist. Es kann eine relative Notation zum Definieren eines Knotens verwendet werden. Außerdem werden die Threads auf allen Knoten ausgeführt.

Einige der Richtlinien können einen geringeren Wert als die für den `mongod`-Prozess verfügbare RAM-Gesamtmenge zur Folge haben. Im Gegensatz zu MySQL vermeidet MongoDB aktiv Paging auf Betriebssystemebene, und daher wird die `mongod` -Prozess kann weniger Speicher erhalten, der verfügbar ist.

#### Tausch {#swapping}

Aufgrund der speicherintensiven Natur von Datenbanken muss der Austausch auf Betriebssystemebene deaktiviert werden. Der MongoDB-Prozess vermeidet einen Austausch per Design.

#### Remote-Dateisysteme {#remote-filesystems}

Remote-Dateisysteme wie NFS werden für die internen Datendateien von MongoDB (die Datenbankdateien des mongod-Prozesses) nicht empfohlen, weil sie zu viel Latenz verursachen. Verwechseln Sie nicht mit dem freigegebenen Dateisystem, das für die Speicherung von Oak Blob (FileDataStore) erforderlich ist, wobei NFS empfohlen wird.

#### Read-Ahead {#read-ahead}

Passen Sie &quot;Read ahead&quot; an, damit unnötige Blöcke nicht von der Festplatte gelesen werden, wenn eine Seite mit einem zufälligen Lesevorgang eingebunden wird. Solche Ergebnisse bedeuten einen unnötigen Verbrauch von I/O-Bandbreite.

### Linux®-Anforderungen {#linux-requirements}

#### Mindestkernversionen {#minimum-kernel-versions}

* **2.6.23** für `ext4`-Dateisysteme

* **2.6.25** für `xfs`-Dateisysteme

#### Empfohlene Einstellungen für Datenbankdiscs {#recommended-settings-for-database-disks}

**Deaktivieren von atime**

Es wird empfohlen, `atime` ist für die Festplatten, die die Datenbanken enthalten, deaktiviert.

**NOOP-Festplatten-Scheduler festlegen**

Gehen Sie folgendermaßen vor:

Überprüfen Sie zunächst die E/A-Planung, die durch Ausführen des folgenden Befehls festgelegt wird:

```shell
cat /sys/block/sdg/queue/scheduler
```

Wenn die Antwort `noop`, gibt es nichts mehr, was Sie tun müssen.

Ist NOOP nicht als I/O-Scheduler eingerichtet, können Sie dies durch Ausführen von Folgendem ändern:

```shell
echo noop > /sys/block/sdg/queue/scheduler
```

**Anpassen des Read-Ahead-Werts**

Es wird empfohlen, den Wert 32 für die Festplatten zu verwenden, auf denen MongoDB-Datenbanken ausgeführt werden. Dieser Wert beträgt 16 KB. Sie können sie wie folgt festlegen:

```shell
sudo blockdev --setra <value> <device>
```

#### NTP aktivieren {#enable-ntp}

Vergewissern Sie sich, dass NTP auf dem Computer installiert ist, auf dem die MongoDB-Datenbanken gehostet werden. Sie können es beispielsweise mit dem yum Package Manager auf einem CentOS-Computer installieren:

```shell
sudo yum install ntp
```

Nachdem der NTP-Daemon installiert und erfolgreich gestartet wurde, können Sie die Drift-Datei auf den Zeitversatz Ihres Servers überprüfen.

#### Transparente große Seiten deaktivieren {#disable-transparent-huge-pages}

Red Hat® Linux® verwendet einen Speicherverwaltungsalgorithmus namens Transparent Huge Pages (THP). Es wird empfohlen, diesen zu deaktivieren, wenn Sie das Betriebssystem für Datenbank-Workloads einsetzen.

Eine Deaktivierung ist mithilfe der folgenden Vorgehensweise möglich:

1. Öffnen Sie die Datei `/etc/grub.conf` in einem beliebigen Texteditor.
1. Fügen Sie der Datei „grub.conf“ die folgende Zeile hinzu:

   ```xml
   transparent_hugepage=never
   ```

1. Überprüfen Sie abschließend, ob die Einstellung wirksam wurde, indem Sie Folgendes ausführen:

   ```shell
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Wenn THP deaktiviert ist, sollte die Ausgabe des obigen Befehls wie folgt lauten:

   ```xml
   always madvise [never]
   ```

>[!NOTE]
>
>Weitere Informationen zu THP finden Sie in diesem [Artikel](https://access.redhat.com/solutions/46111).

#### Deaktivieren von NUMA {#disable-numa}

Bei den meisten Installationen, bei denen NUMA aktiviert ist, deaktiviert der MongoDB-Daemon ihn automatisch, wenn er als Dienst von der `/etc/init.d` Ordner.

Ist dies nicht der Fall, können Sie NUMA auf Prozessebene deaktivieren. Um sie zu deaktivieren, führen Sie die folgenden Befehle aus:

```shell
numactl --interleave=all <path_to_process>
```

`<path_to_process>` steht dabei für den Pfad zum mongod-Prozess.

Deaktivieren Sie dann den „zone_reclaim“-Modus, indem Sie Folgendes ausführen:

```shell
echo 0 > /proc/sys/vm/zone_reclaim_mode
```

#### Optimieren der ulimit-Einstellungen für den mongod-Prozess {#tweak-the-ulimit-settings-for-the-mongod-process}

Linux® ermöglicht eine konfigurierbare Steuerung der Ressourcenzuweisung über die `ulimit` Befehl. Diese Konfiguration kann auf Benutzer- oder Prozessbasis vorgenommen werden.

Es wird empfohlen, ulimit für den mongod -Prozess entsprechend der Variablen [MongoDB Empfohlene ulimit-Einstellungen](https://docs.mongodb.org/manual/reference/ulimit/#recommended-ulimit-settings).

#### Testen der MongoDB I/O-Leistung {#test-mongodb-i-o-performance}

MongoDB bietet ein Tool namens `mongoperf`, das zum Testen der I/O-Leistung entwickelt wurde. Sie sollten damit die Leistung aller MongoDB-Instanzen in Ihrer Infrastruktur testen.

Informationen zum Verwenden von `mongoperf` finden Sie in der [MongoDB-Dokumentation](https://docs.mongodb.org/manual/reference/program/mongoperf/).

>[!NOTE]
>
>Die `mongoperf` ist ein Indikator für die MongoDB-Leistung auf der Plattform, auf der sie ausgeführt wird. Daher sollten die Ergebnisse nicht als endgültig für die Leistung eines Produktionssystems betrachtet werden.
>
>Für genauere Leistungsergebnisse können Sie ergänzende Tests mit der `fio` Linux®-Tool.

**Testen der Leseleistung auf den virtuellen Maschinen einer Bereitstellung**

Nachdem Sie das Tool installiert haben, wechseln Sie zum MongoDB-Datenbankverzeichnis, um die Tests auszuführen. Starten Sie dann den ersten Test, indem Sie `mongoperf` mit der folgenden Konfiguration ausführen:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true}" | mongoperf
```

Die gewünschte Ausgabe sollte bis zu zwei Gigabyte pro Sekunde (2 GB/s) sowie 500.000 IOPS bei 32 Threads für alle MongoDB-Instanzen erreichen.

Führen Sie einen zweiten Test durch (dieses Mal mit den speicherzugeordneten Dateien), indem Sie den Parameter `mmf:true` festlegen:

```shell
echo "{nThreads:32,fileSizeMB:1000,r:true,mmf:true}" | mongoperf
```

Die Ausgabe des zweiten Tests sollte deutlich höher sein als die erste und die Leistung in Bezug auf die Speicherübertragung angeben.

>[!NOTE]
Überprüfen Sie während der Tests die I/O-Nutzungsstatistik für die fraglichen virtuellen Maschinen in Ihrem zur Betriebssystemüberwachung eingesetzten System. Wenn für die I/O-Lesevorgänge ein Testergebnis von unter 100 % ausgegeben wird, liegt womöglich ein Problem bei der virtuellen Maschine vor.

**Testen der Schreibleistung der primären MongoDB-Instanz**

Überprüfen Sie als Nächstes die I/O-Schreibleistung der primären MongoDB-Instanz, indem Sie `mongoperf` mit denselben Einstellungen über das MongoDB-Datenbankverzeichnis ausführen:

```shell
echo "{nThreads:32,fileSizeMB:1000,w:true}" | mongoperf
```

Die gewünschte Ausgabe sollte 12 Megabyte pro Sekunde betragen und etwa 3000 IOPS erreichen, wobei die Anzahl der Threads nur geringfügig variiert.

## Schritte für virtualisierte Umgebungen {#steps-for-virtualised-environments}

### VMWare {#vmware}

Wenn Sie virtualisierte Umgebungen mit WMWare ESX verwalten und bereitstellen, stellen Sie sicher, dass Sie in der ESX-Konsole die folgenden Einstellungen für den MongoDB-Vorgang ausführen:

1. Deaktivieren Sie Memory-Ballooning.
1. Vorteilen und Reservieren von Speicher für die virtuellen Maschinen, die die MongoDB-Datenbanken hosten
1. Weisen Sie dem `mongod`-Prozess über Storage I/O Control genügend I/O-Kapazität zu.
1. Garantieren Sie den MongoDB-Hostmaschinen CPU-Ressourcen, indem Sie die Option für die [CPU-Reservierung](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.hostclient.doc/GUID-6C9023B2-3A8F-48EB-8A36-44E3D14958F6.html?hWord=N4IghgNiBc4RB7AxmALgUwAQGEAKBVTAJ3QGcEBXIpMkAXyA) einstellen.

1. Ziehen Sie die Verwendung von Paravirtual-I/O-Treibern in Betracht. Siehe [Knowledgebase-Artikel](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1010398).

### Amazon Web Services {#amazon-web-services}

Informationen zum Einrichten von MongoDB mit Amazon Web Services finden Sie im Artikel [Configure AWS Integration](https://docs.cloud.mongodb.com/tutorial/configure-aws-settings/) (Konfigurieren der AWS-Integration) auf der MongoDB-Website.

## Sichern von MongoDB vor der Bereitstellung {#securing-mongodb-before-deployment}

Siehe diesen Beitrag auf [Sichere Bereitstellung von MongoDB](https://blogs.adobe.com/security/2015/07/securely-deploying-mongodb-3-0.html) für Ratschläge zur Sicherung der Konfiguration Ihrer Datenbanken vor der Bereitstellung.

## Dispatcher {#dispatcher}

### Auswählen des Betriebssystems für den Dispatcher {#choosing-the-operating-system-for-the-dispatcher}

Um Ihre MongoDB-Bereitstellung ordnungsgemäß bereitzustellen, muss das Betriebssystem, das den Dispatcher hostet, ausgeführt werden **Apache httpd** **Version 2.4 oder höher.**

Stellen Sie außerdem sicher, dass alle in Ihrem Build verwendeten Bibliotheken auf dem neuesten Stand sind, um die Auswirkungen auf die Sicherheit zu minimieren.

### Dispatcher-Konfiguration {#dispatcher-configuration}

Eine typische Dispatcher-Konfiguration liefert zwischen zehn- und zwanzigmal so viel wie der Anforderungsdurchsatz einer einzelnen AEM.

Da der Dispatcher statuslos ist, kann er mit Leichtigkeit horizontal skaliert werden. In einigen Implementierungen müssen Autoren vom Zugriff auf bestimmte Ressourcen ausgeschlossen sein. Es wird empfohlen, einen Dispatcher mit den Autoreninstanzen zu verwenden.

Das Ausführen von AEM ohne Dispatcher erfordert die SSL-Beendigung und den Lastenausgleich, die von einer anderen Anwendung durchgeführt werden müssen. Dies ist erforderlich, da Sitzungen eine Affinität zu der AEM Instanz aufweisen müssen, auf der sie erstellt werden. Dies ist ein Konzept, das als Sticky-Verbindungen bezeichnet wird. Der Grund besteht darin, sicherzustellen, dass Aktualisierungen des Inhalts nur eine minimale Latenz aufweisen.

Weitere Informationen zur entsprechenden Konfiguration finden Sie in der [Dispatcherdokumentation](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de).

### Zusätzliche Konfiguration {#additional-configuration}

#### Sticky-Verbindungen  {#sticky-connections}

Sticky-Verbindungen stellen sicher, dass personalisierte Seiten und Sitzungsdaten für einen Benutzer alle auf derselben Instanz von AEM erstellt werden. Diese Daten werden in der -Instanz gespeichert, sodass nachfolgende Anforderungen desselben Benutzers an dieselbe Instanz zurückgegeben werden.

Es wird empfohlen, Sticky-Verbindungen für alle inneren Ebenen zu aktivieren, die Anforderungen an die AEM-Instanzen leiten, sodass nachfolgende Anforderungen dieselbe AEM erreichen. Auf diese Weise wird die Latenz minimiert, die andernfalls beim Aktualisieren von Inhalten zwischen Instanzen erkennbar ist.

#### Lange Ablaufzeit {#long-expires}

Standardmäßig enthält von einem AEM Dispatcher gesendete Inhalte die Header &quot;Zuletzt geändert&quot;und &quot;Etag&quot;, wobei kein Hinweis auf das Ablaufdatum des Inhalts vorhanden ist. Dadurch wird sichergestellt, dass die Benutzeroberfläche immer die neueste Version der Ressource erhält. Dies bedeutet auch, dass der Browser einen GET-Vorgang ausführt, um zu sehen, ob sich die Ressource geändert hat. Daher kann es je nach Seitenladung zu mehreren Anfragen kommen, auf die die HTTP-Antwort 304 (Nicht geändert) beträgt. Bei Ressourcen, die nicht ablaufen, wird der Inhalt zwischengespeichert, wenn Sie eine Expires -Kopfzeile festlegen und die Header Last-Modified und ETag entfernen. Außerdem werden keine weiteren Aktualisierungsanfragen gestellt, bis das Datum in der Überschrift Läuft ab erfüllt ist.

Die Verwendung dieser Methode bedeutet jedoch, dass es keine vernünftige Möglichkeit gibt, die Ressource im Browser ablaufen zu lassen, bevor der Expires-Header abläuft. Um diesen Workflow zu umgehen, kann der HtmlClientLibraryManager so konfiguriert werden, dass unveränderliche URLs für Client-Bibliotheken verwendet werden.

Diese URLs werden garantiert nicht geändert. Wenn sich der Hauptteil der in der URL enthaltenen Ressource ändert, werden die Änderungen in der URL widergespiegelt, um sicherzustellen, dass der Browser die richtige Version der Ressource anfordert.

Die Standardkonfiguration fügt dem HtmlClientLibraryManager einen Selektor hinzu. Als Selektor wird die Ressource im Dispatcher zwischengespeichert, wobei der Selektor intakt ist. Dieser Selektor kann auch verwendet werden, um das richtige Ablaufverhalten sicherzustellen. Der Standardselektor folgt dem Muster `lc-.*?-lc`. Die folgenden Apache httpd-Konfigurationsanweisungen stellen sicher, dass alle Anforderungen, die diesem Muster entsprechen, mit einer angemessenen Ablaufzeit verarbeitet werden.

```xml
Header set Expires "Tue, 20 Jan 2037 04:20:42 GMT" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header set Cache-Control "public, no-transform, max-age=267840000" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset ETag "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Last-Modified "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Pragma "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
```

#### No Sniff {#no-sniff}

Wenn Inhalte ohne Content-Typ gesendet werden, versuchen viele Browser, den Inhaltstyp zu erraten, indem sie die ersten Byte des Inhalts lesen. Diese Methode wird als &quot;Sniffing&quot;bezeichnet. Sniffing eröffnet eine Sicherheitslücke, da Benutzer, die in das Repository schreiben können, möglicherweise schädliche Inhalte ohne Inhaltstyp hochladen können.

Aus diesem Grund ist es ratsam, eine `no-sniff` -Kopfzeile zu den Ressourcen, die vom Dispatcher bereitgestellt werden. Der Dispatcher speichert jedoch keine Header zwischen. Daher bedeutet dies, dass jeder Inhalt, der aus dem lokalen Dateisystem bereitgestellt wird, seinen Inhaltstyp durch seine Erweiterung bestimmt, anstatt den ursprünglichen Content-Type-Header vom AEM Herkunftsserver zu verwenden.

Kein Sniff kann sicher aktiviert werden, wenn bekannt ist, dass die Webanwendung keine zwischengespeicherten Ressourcen ohne Dateityp bereitstellt.

Sie können &quot;No Sniff&quot;einschließen:

```xml
Header set X-Content-Type-Options "nosniff"
```

Sie kann auch selektiv aktiviert werden:

```xml
RewriteCond %{REQUEST_URI} \.(?:js|jsonp)$ [OR]
RewriteCond %{QUERY_STRING} (callback|jsonp|cb)=\w+
RewriteRule .* - [E=jsonp_request:1]
Header set X-Content-Type-Options "nosniff"  env=jsonp_request
Header setifempty Content-Type application/javascript env=jsonp_request
```

#### Inhaltssicherheitsrichtlinie {#content-security-policy}

Die standardmäßigen Dispatcher-Einstellungen ermöglichen das Öffnen der Inhaltssicherheitsrichtlinie, auch als CSP bezeichnet. Mit diesen Einstellungen kann eine Seite Ressourcen aus allen Domänen laden, die den Standardrichtlinien der Browser-Sandbox unterliegen.

Es ist wünschenswert, den Speicherort von Ressourcen zu beschränken, um zu verhindern, dass Code von nicht vertrauenswürdigen oder nicht verifizierten ausländischen Servern in die JavaScript-Engine geladen wird.

CSP ermöglicht eine Feinabstimmung von Richtlinien. In einer komplexen Anwendung müssen CSP-Header jedoch mit Vorsicht entwickelt werden, da zu restriktive Richtlinien Teile der Benutzeroberfläche beschädigen können.

>[!NOTE]
Weitere Informationen zur Funktionsweise finden Sie unter [OWASP-Seite für Content Security Policy](https://owasp.deteact.com/cheat/cheatsheets/Content_Security_Policy_Cheat_Sheet.html).

### Größe {#sizing}

Weitere Informationen zur Größenanpassung finden Sie unter [Richtlinien zur Hardware-Skalierung](/help/managing/hardware-sizing-guidelines.md).

### MongoDB-Leistungsoptimierung {#mongodb-performance-optimization}

Allgemeine Informationen zur MongoDB-Leistung finden Sie unter [Analysieren der MongoDB-Leistung](https://docs.mongodb.org/manual/administration/analyzing-mongodb-performance/).

## Bekannte Einschränkungen {#known-limitations}

### Gleichzeitige Installationen {#concurrent-installations}

Die gleichzeitige Verwendung mehrerer AEM Instanzen mit einer einzigen Datenbank wird von MongoMK unterstützt, gleichzeitige Installationen jedoch nicht.

Um dieses Problem zu umgehen, führen Sie die Installation zunächst mit einem einzelnen Mitglied aus und fügen Sie die anderen hinzu, nachdem die Installation des ersten beendet wurde.

### Länge des Seitennamens {#page-name-length}

Wenn AEM auf einer MongoMK-Persistenz-Manager-Bereitstellung ausgeführt wird, sind [Seitennamen auf 150 Zeichen beschränkt](/help/sites-authoring/managing-pages.md).

>[!NOTE]
Siehe [MongoDB-Dokumentation](https://docs.mongodb.com/manual/reference/limits/) damit Sie sich mit den bekannten Einschränkungen und Schwellenwerten von MongoDB vertraut machen können.
