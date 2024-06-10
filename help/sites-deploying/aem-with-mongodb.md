---
title: Adobe Experience Manager mit MongoDB
description: Erfahren Sie mehr über die Aufgaben und Überlegungen, die für eine erfolgreiche Bereitstellung von Adobe Experience Manager mit MongoDB erforderlich sind.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: 70a39462-8584-4c76-a097-05ee436247b7
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: a8203a6bccff821dd6ca3f63c196829379aabe55
workflow-type: ht
source-wordcount: '6192'
ht-degree: 100%

---

# Adobe Experience Manager mit MongoDB{#aem-with-mongodb}

Dieser Artikel soll das Wissen über Aufgaben und Überlegungen verbessern, die für die erfolgreiche Bereitstellung von AEM (Adobe Experience Manager) mit MongoDB erforderlich sind.

Weitere Informationen zur Bereitstellung finden Sie im Abschnitt [Bereitstellung und Wartung](/help/sites-deploying/deploy.md) der Dokumentation.

## Wann MongoDB mit AEM verwendet werden sollte {#when-to-use-mongodb-with-aem}

MongoDB wird normalerweise zur Unterstützung von AEM-Authoring-Bereitstellungen verwendet, wenn eines der folgenden Kriterien erfüllt ist:

* mehr als 1000 Unique Users pro Tag;
* mehr als 100 gleichzeitige Benutzerinnen und Benutzer;
* hohe Anzahl von Seitenbearbeitungen;
* große Rollouts oder Aktivierungen.

Die oben genannten Kriterien gelten nur für die Autoreninstanzen und nicht für Veröffentlichungsinstanzen, die alle auf TarMK basieren sollten. Die Anzahl der Benutzer bzw. Benutzerinnen bezieht sich auf authentifizierte Benutzer bzw. Benutzerinnen, da Authoring-Instanzen keinen nicht-authentifizierten Zugriff zulassen.

Werden die Kriterien nicht erfüllt, wird zwecks Verfügbarkeit eine aktive TarMK-Bereitstellung bzw. eine Standby-TarMK-Bereitstellung empfohlen. Im Allgemeinen sollte MongoDB in Situationen berücksichtigt werden, in denen die Skalierungsanforderungen größer sind, als mit einem einzelnen Hardware-Element erzielt werden kann.

>[!NOTE]
>
>Weitere Informationen zur Größenanpassung von Authoring-Instanzen und zur Definition gleichzeitiger Benutzer bzw. Benutzerinnen finden Sie in den [Richtlinien zur Hardware-Skalierung](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel).

### Minimale MongoDB-Bereitstellung für AEM {#minimal-mongodb-deployment-for-aem}

Nachfolgend wird eine minimale Bereitstellung für AEM auf MongoDB aufgeführt. Zur Vereinfachung wurden SSL-Terminierung und HTTP-Proxy-Komponenten verallgemeinert. Die Bereitstellung besteht aus einer einzigen MongoDB-Replikatgruppe mit einem primären Replikat und zwei sekundären Replikaten.

![chlimage_1-4](assets/chlimage_1-4.png)

Eine minimale Bereitstellung setzt voraus, dass `mongod`-Instanzen als Replikatgruppe konfiguriert sind. Eine Instanz wird als primäres Replikat gewählt, die beiden anderen sind sekundäre Replikate; die Wahl wird von `mongod` verwaltet. Angebunden an jede Instanz ist eine lokale Festplatte. So kann der Cluster die Auslastung unterstützen. Es wird ein Mindestdurchsatz von 12 MB pro Sekunde mit mehr als 3000 I/O Operations per Second (IOPS) empfohlen.

Die AEM-Autoren sind mit den `mongod`-Instanzen verbunden, wobei jeweils eine Verbindung zu allen drei `mongod`-Instanzen besteht. Schreibvorgänge werden an die primäre Instanz gesendet und Lesevorgänge können von jeder der Instanzen gelesen werden. Der Traffic wird basierend auf dem Laden durch einen Dispatcher an eine der aktiven AEM-Authoring-Instanzen verteilt. Der Oak-Datenspeicher ist ein `FileDataStore` und die MongoDB-Überwachung erfolgt je nach Bereitstellungsort über MMS oder MongoDB Ops Manager. Die Betriebssystemebene und die Protokollüberwachung werden von Drittanbieterlösungen wie Splunk oder Ganglia bereitgestellt.

In dieser Bereitstellung sind alle Komponenten für eine erfolgreiche Implementierung erforderlich. Jede fehlende Komponente macht die Implementierung funktionsunfähig.

### Betriebssysteme {#operating-systems}

Eine Aufstellung der unterstützten Betriebssysteme für AEM 6 finden Sie auf der Seite [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Umgebungen {#environments}

Virtualisierte Umgebungen werden unterstützt, sofern eine gute Kommunikation zwischen den verschiedenen technischen Teams besteht, die das Projekt durchführen. Zu diesem Support gehören das Team, das AEM führt, das Team, das Eigentümer des Betriebssystems ist, und das Team, das die virtualisierte Infrastruktur verwaltet.

Es gibt spezifische Anforderungen an die E/A-Kapazität der MongoDB-Instanzen, die von dem Team verwaltet werden müssen, das die virtualisierte Umgebung verwaltet. Wenn das Projekt eine Cloud-Implementierung wie Amazon Web Services verwendet, müssen Instanzen mit ausreichender I/O-Kapazität und Konsistenz bereitgestellt werden, um die MongoDB-Instanzen zu unterstützen. Andernfalls ist die Leistung der MongoDB-Prozesse und des Oak-Repositorys unzuverlässig und unregelmäßig.

In virtualisierten Umgebungen erfordert MongoDB spezifische I/O- und VM-Konfigurationen, um sicherzustellen, dass die Speichermodul-Engine von MongoDB nicht durch VMware-Richtlinien zur Ressourcenzuordnung beeinträchtigt wird. Eine erfolgreiche Implementierung stellt sicher, dass es keine Hindernisse zwischen den verschiedenen Teams gibt und alle am gleichen Strang ziehen, um die erforderliche Leistung zu liefern.

## Hardware-Überlegungen {#hardware-considerations}

### Speicherung {#storage}

Um den Lese- und Schreibdurchsatz für optimale Leistung ohne vorzeitige horizontale Skalierung zu erreichen, benötigt MongoDB im Allgemeinen SSD-Speicher oder Speicher mit einer SSD-gleichwertigen Leistung.

### RAM {#ram}

MongoDB-Versionen 2.6 und 3.0, die die MMAP-Speicher-Engine verwenden, erfordern, dass der Arbeitssatz der Datenbank und deren Indizes in den Arbeitsspeicher passen.

Unzureichender Arbeitsspeicher führt zu einer deutlichen Leistungsminderung. Die Größe des Workflows und der Datenbank hängt stark von der Anwendung ab. Während einige Schätzungen vorgenommen werden können, ist die zuverlässigste Methode, den erforderlichen Arbeitsspeicher zu bestimmen, die AEM-Anwendung zu erstellen und Lasttests durchzuführen.

Um den Lasttestvorgang zu unterstützen, kann das folgende Verhältnis zwischen dem Arbeitssatz und der gesamten Datenbankgröße angenommen werden:

* 1:10 für SSD-Speicher
* 1:3 für Festplattenspeicher

Diese Verhältnisse bedeuten, dass für SSD-Bereitstellungen 200 GB RAM für eine 2 TB große Datenbank erforderlich sind.

Die gleichen Einschränkungen gelten für das WiredTiger-Speichermodul in MongoDB 3.0, aber die Korrelation zwischen Arbeitsset, RAM und Seitenfehlern ist nicht so stark. WiredTiger verwendet die Speicherzuordnung nicht auf die gleiche Weise wie die MMAP-Speicher-Engine.

>[!NOTE]
>
>Adobe empfiehlt die Verwendung der WiredTiger-Speicher-Engine für AEM 6.1-Bereitstellungen, die MongoDB 3.0 verwenden.

### Datenspeicher {#data-store}

Aufgrund der Beschränkungen des MongoDB-Arbeitssets wird empfohlen, den Datenspeicher unabhängig von MongoDB zu verwalten. In den meisten Umgebungen sollte ein für alle AEM-Instanzen verfügbarer `FileDataStore` mit einem NAS verwendet werden. Wird Amazon Web Services genutzt, steht auch ein `S3 DataStore` zur Verfügung. Wenn der Datenspeicher aus irgendeinem Grund innerhalb von MongoDB verwaltet wird, sollte die Größe des Datenspeichers der gesamten Datenbankgröße hinzugefügt und die Arbeitsset-Berechnungen entsprechend angepasst werden. Diese Größenanpassung kann bedeuten, dass mehr Arbeitsspeicher bereitgestellt wird, um die Leistung ohne Seitenfehler zu gewährleisten.

## Überwachung {#monitoring}

Überwachung ist für eine erfolgreiche Umsetzung des Projekts von entscheidender Bedeutung. Mit ausreichendem Wissen ist es möglich, AEM auf MongoDB ohne Überwachung auszuführen. Diese Kenntnisse sind jedoch normalerweise bei Technikerpersonal vorhanden, das auf jeden Abschnitt des Einsatzes spezialisiert ist.

Für dieses Wissen ist in der Regel eine Ingenieurin oder ein Ingenieur aus der F&amp;E von Apache Oak Core und eine Spezialistin oder ein Spezialist für MongoDB erforderlich.

Ohne Überwachung auf allen Ebenen sind detaillierte Kenntnisse der Codebasis erforderlich, um Probleme zu diagnostizieren. Durch die vorhandene Überwachung und geeignete Anleitungen zu den wichtigsten Statistiken können Implementierungsteams angemessen auf Anomalien reagieren.

Es ist zwar möglich, Befehlszeilen-Tools zu verwenden, um einen schnellen Überblick über den Betrieb eines Clusters zu erhalten, doch ist es fast unmöglich, dies in Echtzeit über viele Hosts hinweg durchzuführen. Befehlszeilen-Tools geben nur selten historische Informationen nach einigen Minuten zurück und ermöglichen nie eine Kreuzkorrelation zwischen verschiedenen Metriktypen. Ein kurzer Zeitraum langsamer `mongod`-Hintergrundsynchronisierungen bedeutet zusätzlichen manuellen Aufwand, um I/O-Wartezeiten oder übermäßige Write-Level mit einer freigegebenen Speicherressource von einer scheinbar nicht verbundenen virtuellen Maschine in Beziehung zu setzen.

### MongoDB Cloud Manager {#mongodb-cloud-manager}

MongoDB Cloud Manager ist ein kostenloser Dienst von MongoDB, der die Überwachung und Verwaltung von MongoDB-Instanzen ermöglicht. Er bietet einen Überblick über die Leistung und den Zustand des MongoDB-Clusters in Echtzeit. Es verwaltet sowohl Cloud- als auch privat gehostete Instanzen, sofern die Instanz den Cloud Manager-Überwachungsserver erreichen kann.

Voraussetzung ist die Installation eines Agenten auf der MongoDB-Instanz, der mit dem Überwachungsserver verbunden ist. Es gibt drei Ebenen des Agenten:

* Ein Automatisierungsagent, der alles auf dem MongoDB-Server vollständig automatisieren kann
* Einen Überwachungsagenten, der die `mongod`-Instanz überwachen kann
* Ein Backup-Agent, der geplante Sicherungen der Daten durchführen kann.

Obwohl die Verwendung von Cloud Manager zur Wartungsautomatisierung eines MongoDB-Clusters viele der Routineaufgaben vereinfacht, ist dies nicht erforderlich und wird auch nicht für Backups verwendet. Wenn Sie sich bei der Überwachung für Cloud Manager entscheiden, ist jedoch eine Überwachung erforderlich.

Weitere Informationen zu MongoDB Cloud Manager finden Sie in der [MongoDB-Dokumentation](https://docs.cloud.mongodb.com/).

### MongoDB Ops Manager {#mongodb-ops-manager}

MongoDB Ops Manager ist dieselbe Software wie MongoDB Cloud Manager. Nach der Registrierung kann Ops Manager lokal in einem privaten Rechenzentrum oder auf einem anderen Laptop oder Desktop-Computer heruntergeladen und installiert werden. Es verwendet eine lokale MongoDB-Datenbank, um Daten zu speichern und auf dieselbe Weise wie Cloud Manager mit den verwalteten Servern zu kommunizieren. Wenn Sie Sicherheitsrichtlinien haben, die einen Überwachungsagenten verbieten, sollte MongoDB Ops Manager verwendet werden.

### Betriebssystemüberwachung {#operating-system-monitoring}

Zum Ausführen eines AEM MongoDB-Clusters ist eine Überwachung auf Betriebssystemebene erforderlich.

Ganglia ist ein gutes Beispiel für ein solches System und liefert ein Bild über die Bandbreite und Details der benötigten Informationen, die über grundlegende Zustandsdaten wie CPU, durchschnittliche Auslastung und freien Speicherplatz hinausgehen. Um Probleme zu diagnostizieren, sind niedrigere Informationen wie Entropy-Pool-Ebenen, CPU-I/O-Wartezeit und Sockets im FIN_WAIT2-Status erforderlich.

### Protokollaggregation {#log-aggregation}

Bei einem Cluster aus mehreren Servern ist die zentrale Protokollaggregation eine Voraussetzung für ein Produktionssystem. Software wie Splunk unterstützt die Protokollierung und ermöglicht es Teams, die Verhaltensmuster der Anwendung zu analysieren, ohne die Protokolle manuell erfassen zu müssen.

## Checklisten {#checklists}

In diesem Abschnitt werden die verschiedenen Schritte beschrieben, die Sie unternehmen sollten, um sicherzustellen, dass Ihre AEM- und MongoDB-Bereitstellungen vor der Implementierung Ihres Projekts ordnungsgemäß eingerichtet sind.

### Netzwerk {#network}

1. Stellen Sie zunächst sicher, dass alle Hosts einen DNS-Eintrag haben.
1. Alle Hosts sollten durch ihren DNS-Eintrag von allen anderen routbaren Hosts aufgelöst werden können
1. Alle MongoDB-Hosts sind von allen anderen MongoDB-Hosts im selben Cluster routbar
1. MongoDB-Hosts können Pakete an MongoDB Cloud Manager und die anderen Überwachungs-Server weiterleiten
1. AEM Server können Pakete an alle MongoDB-Server weiterleiten
1. Die Paketlatenz zwischen einem beliebigen AEM-Server und einem MongoDB-Server ist kleiner als zwei Millisekunden, ohne Paketverlust und mit einer Standardverteilung von einer Millisekunde oder weniger.
1. Stellen Sie sicher, dass zwischen einem AEM- und einem MongoDB-Server nicht mehr als zwei Hops vorhanden sind.
1. Zwischen zwei MongoDB-Servern gibt es nicht mehr als zwei Hops.
1. Es gibt keine Router, die höher sind als OSI Level 3 zwischen Kern-Servern (MongoDB oder AEM oder einer Kombination).
1. Wenn VLAN-Trunking oder eine Netzwerktunnelung verwendet wird, muss dies den Paketlatenzprüfungen entsprechen.

### AEM-Konfiguration {#aem-configuration}

#### Knotenspeicherkonfiguration {#node-store-configuration}

Die AEM-Instanzen müssen für die Verwendung von AEM mit MongoMK konfiguriert werden. Die Grundlage der MongoMK-Implementierung in AEM ist der Knotenspeicher „Dokument“.

Weitere Informationen zum Konfigurieren von Knotenspeichern finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM](/help/sites-deploying/data-store-config.md).

Nachfolgend finden Sie ein Beispiel für die Konfiguration des Knotenspeichers für eine minimale MongoDB-Bereitstellung:

```xml
# org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config
#MongoDB server details
mongodburi=mongodb://aem:aempassword@mongodbserver1.customer.com:27000,mongodbserver2.customer.com:27000

#Name of MongoDB database to use
db=aem

#Store binaries in custom BlobStore for example, FileDataStore
customBlobStore=true

cache=2048
blobCacheSize=1024
```

Dabei gilt:

* `mongodburi`
Der MongoDB-AEM, zu dem AEM eine Verbindung herstellen muss. Verbindungen werden zu allen bekannten Mitgliedern des standardmäßigen Replikatsatzes hergestellt. Wenn MongoDB Cloud Manager verwendet wird, ist die Serversicherheit aktiviert. Daher muss die Verbindungszeichenfolge einen geeigneten Benutzernamen und ein passendes Passwort enthalten. Nicht-Enterprise-Versionen von MongoDB unterstützen nur die Authentifizierung von Benutzernamen und Passwörtern. Weitere Informationen zur Syntax der Verbindungszeichenfolge finden Sie im Abschnitt [Dokumentation](https://docs.mongodb.org/manual/reference/connection-string/).

* `db`
Der Name der Datenbank. Der Standardwert für AEM lautet `aem-author`.

* `customBlobStore`
Wenn Binärdateien im Zuge der Bereitstellung in der Datenbank gespeichert werden, werden sie Teil des Arbeitssatzes. Aus diesem Grund sollten Binärdateien nicht in MongoDB gespeichert werden. Stattdessen werden alternative Datenspeicher wie ein `FileSystem`-Datenspeicher in einem NAS empfohlen.

* `cache`
Die Cache-Größe in Megabyte. Dieser Wert ist verteilt über diverse Cache-Speicher im `DocumentNodeStore`. Die Standardgröße ist 256 MB. Die Leistung des Oak-Lesens profitiert jedoch von einem größeren Cache.

* `blobCacheSize`
Häufig verwendete Blobs können von AEM im Cache gespeichert werden. So wird vermieden, dass sie erneut aus dem Datenspeicher abgerufen werden. Dies wirkt sich stärker auf die Performance aus, insbesondere beim Speichern von Blobs in der MongoDB-Datenbank. Alle dateisystembasierten Datenspeicher profitieren vom Datenträger-Cache auf Betriebssystemebene.

#### Datenspeicherkonfiguration {#data-store-configuration}

Der Datenspeicher dient zum Speichern von Dateien mit einer Größe, die größer als ein Schwellenwert ist. Unter diesem Schwellenwert werden Dateien als Eigenschaften im Knotenspeicher „Dokument“ gespeichert. Wenn der `MongoBlobStore` verwendet wird, wird in MongoDB eine dedizierte Sammlung zum Speichern der Blobs erstellt. Diese Sammlung trägt zum Workingset der `mongod`-Instanz bei und setzt einen größeren Arbeitsspeicher für die `mongod`-Instanz voraus, um Leistungsprobleme zu vermeiden. Daher wird für Konfigurationen empfohlen, in Produktionsbereitstellungen auf `MongoBlobStore` zu verzichten und einen `FileDataStore` einzusetzen, der von einem von allen AEM-Instanzen genutzten NAS gestützt wird. Da der Cache auf Betriebssystemebene bei der Verwaltung von Dateien effizient ist, sollte die Mindestgröße einer Datei auf dem Datenträger auf die Blockgröße der Festplatte eingestellt werden. Dadurch wird sichergestellt, dass das Dateisystem effizient verwendet wird und viele kleine Dokumente nicht übermäßig zum Workingset der `mongod`-Instanz beitragen.

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
Größe in Byte. Binärdateien, die gleich wie oder kleiner als diese Größe sind, werden mit dem Knotenspeicher „Dokument“ gespeichert. Anstatt die Kennung des Blob zu speichern, wird der Inhalt der Binärdatei gespeichert. Bei Binärdateien, die größer als diese Größe sind, wird die ID der Binärdatei als Eigenschaft des Dokuments in der Knotensammlung gespeichert. Und der Hauptteil der Binärdatei wird im `FileDataStore` auf der Festplatte gespeichert. 4096 Byte entspricht einer typischen Dateisystem-Blockgröße.

* `path`
Der Pfad zum Stamm des Datenspeichers. Bei einer MongoMK-Bereitstellung muss dieser Pfad ein freigegebenes Dateisystem sein, das für alle AEM-Instanzen verfügbar ist. Normalerweise wird ein NAS-Server (Network Attached Storage) verwendet. Für Cloudbereitstellungen wie Amazon Web Services steht zudem der `S3DataFileStore` zur Verfügung.

* `cacheSizeInMB`
Die Gesamtgröße des Binärdatencache in Megabyte. Damit werden Binärdateien im Cache gespeichert, deren Wert unterhalb der Einstellung `maxCacheBinarySize` liegt.

* `maxCachedBinarySize`
Die maximale Größe in Byte der im Binärdatencache gespeicherten Binärdatei. Wenn ein dateisystembasierter Datenspeicher verwendet wird, wird die Verwendung hoher Werte für den Datenspeicher-Cache nicht empfohlen, da die Binärdateien bereits vom Betriebssystem zwischengespeichert werden.

#### Deaktivieren des Abfragehinweises {#disabling-the-query-hint}

Es wird empfohlen, den mit allen Abfragen gesendeten Abfragehinweis zu deaktivieren, indem Sie die Eigenschaft `-Doak.mongo.disableIndexHint=true` beim Starten von AEM hinzufügen. Dadurch wird sichergestellt, dass MongoDB anhand interner Statistiken den am besten geeigneten Index berechnet.

Wenn der Abfragehinweis nicht deaktiviert ist, hat eine Leistungsoptimierung von Indizes keine Auswirkungen auf die Leistung von AEM.

#### Aktivieren des persistenten Cache für MongoMK {#enable-persistent-cache-for-mongomk}

Es wird empfohlen, eine persistente Cache-Konfiguration für MongoDB-Bereitstellungen zu aktivieren, um die Geschwindigkeit für Umgebungen mit hoher I/O-Leseleistung zu maximieren. Weitere Informationen finden Sie in der [Jackrabbit Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/nodestore/persistent-cache.html).

## MongoDB-Betriebssystemoptimierungen {#mongodb-operating-system-optimizations}

### Betriebssystemunterstützung {#operating-system-support}

MongoDB 2.6 nutzt ein Speichermodul mit Speicherzuordnung, das auf einige Aspekte der Verwaltung der Betriebssystemebene zwischen RAM und Datenträger empfindlich reagiert. Die Abfrage- und Leseleistung der MongoDB-Instanz beruht darauf, langsame I/O-Vorgänge, die häufig als Seitenfehler bezeichnet werden, zu vermeiden oder zu beseitigen. Bei diesen Problemen handelt es sich um Seitenfehler, die insbesondere für den Prozess `mongod` gelten. Verwechseln Sie sie nicht mit Seitenfehlern auf Betriebssystemebene.

Für einen schnellen Betrieb sollte die MongoDB-Datenbank nur auf Daten zugreifen, die sich bereits im RAM befinden. Die Daten, auf die sie zugreifen muss, bestehen aus Indizes und Daten. Diese Sammlung von Indizes und Daten wird als Arbeitssatz bezeichnet. Wenn der Arbeitssatz größer als der verfügbare RAM ist, muss MongoDB diese Daten von der Festplatte auslagern, was I/O-Kosten verursacht, und andere Daten, die bereits im Speicher sind, entfernen. Wenn die Entfernung dazu führt, dass Daten von der Festplatte neu geladen werden, dominieren Seitenfehler und die Leistung sinkt. Bei einem dynamischen und variablen Arbeitssatz tritt bei Support-Vorgängen eine größere Anzahl von Seitenfehlern auf.

MongoDB läuft auf verschiedenen Betriebssystemen, einschließlich einer Vielzahl von Linux®-Versionen, Windows und macOS. Siehe [https://docs.mongodb.com/manual/installation/#supported-platforms](https://docs.mongodb.com/manual/installation/#supported-platforms) für weitere Details. Je nach Wahl Ihres Betriebssystems bietet MongoDB verschiedene Empfehlungen auf Betriebssystemebene. Diese sind unter [https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration](https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration) dokumentiert und werden hier lediglich zusammengefasst.

#### Linux® {#linux}

* Deaktivieren Sie transparente Hugepages und Defragmentierung. Siehe [Transparente Huge Pages Einstellungen](https://docs.mongodb.com/manual/tutorial/transparent-huge-pages/) für weitere Informationen.
* [Passen Sie die Einstellungen für readahead](https://docs.mongodb.com/manual/administration/production-notes/#readahead) auf den Geräten an, auf denen Ihre Datenbankdateien gespeichert werden, sodass Sie zu Ihrem Anwendungsfall passen.

   * Wenn Ihr Arbeitssatz größer als der verfügbare Arbeitsspeicher und das Muster für den Dokumentzugriff zufällig ist, müssen Sie readahead für die MMAPv1-Speicher-Engine eventuell auf 32 oder 16 herabsetzen. Evaluieren Sie verschiedene Einstellungen, damit Sie einen optimalen Wert finden können, der den residierenden Speicher maximiert und die Anzahl der Seitenfehler verringert.
   * Für die WiredTiger-Speicher-Engine setzen Sie readahead auf 0, unabhängig von der Art des Speichermediums (Spinning, SSD, etc.). Verwenden Sie im Allgemeinen die empfohlene readahead-Einstellung, es sei denn, Tests zeigen einen messbaren, wiederholbaren und zuverlässigen Nutzen in einem höheren readahead-Wert. [Der professionelle Support von MongoDB](https://docs.mongodb.com/manual/administration/production-notes/#readahead) kann Sie beim Konfigurieren von readahead mit anderen Werten unterstützen.

* Deaktivieren Sie das angepasste Tool, wenn Sie RHEL 7 / CentOS 7 in einer virtuellen Umgebung ausführen.
* Wenn RHEL 7 / CentOS 7 in einer virtuellen Umgebung ausgeführt wird, ruft das angepasste Tool automatisch ein aus dem Leistungsdurchsatz abgeleitetes Leistungsprofil auf, das die readahead-Einstellungen automatisch auf 4 MB festlegt. Diese Einstellung kann sich negativ auf die Leistung auswirken.
* Verwenden Sie die Noop- oder Deadline-Scheduler für SSD-Laufwerke.
* Verwenden Sie den Noop-Festplatten-Scheduler für virtualisierte Laufwerke in Gast-VMs.
* Deaktivieren Sie NUMA oder setzen Sie `vm.zone_reclaim_mode` auf 0 und führen Sie [mongod](https://docs.mongodb.com/manual/administration/production-notes/#readahead)-Instanzen mit „node interleaving“ aus. Siehe: [MongoDB- und NUMA-Hardware](https://docs.mongodb.com/manual/administration/production-notes/#readahead) für weitere Informationen.

* Passen Sie die ulimit-Werte auf Ihrer Hardware so an, dass sie Ihrem Anwendungsfall entsprechen. Wenn mehrere [mongod](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod)- oder [mongos](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos)-Instanzen unter demselben Benutzer bzw. derselben Benutzerin ausgeführt werden, skalieren Sie die ulimit-Werte entsprechend. Siehe: [UNIX® ulimit-Einstellungen](https://docs.mongodb.com/manual/reference/ulimit/) für weitere Informationen.

* Verwenden Sie „noatime“ für den Einhängepunkt [dbPath](https://docs.mongodb.com/manual/reference/configuration-options/#storage.dbPath).
* Konfigurieren Sie für Ihre Implementierung ausreichende Werte für Datei-Handles (fs.file-max), Kernel-PID-Limit (kernel.pid_max) und die maximalen Threads pro Prozess (kernel.threads-max). Für große Systeme bieten die folgenden Werte einen guten Ausgangspunkt:

   * Wert für fs.file-max: 98000,
   * Wert für kernel.pid_max: 64000,
   * Wert für andkernel.threads-max: 64000

* Stellen Sie sicher, dass für Ihr System der Auslagerungsspeicher konfiguriert ist. Detaillierte Informationen zu den Größenanforderungen finden Sie in der Dokumentation zu Ihrem Betriebssystem.
* Stellen Sie sicher, dass der Standardwert des Systems für TCP-Keepalive richtig festgelegt ist. Der Wert „300“ bietet häufig eine bessere Performance für Replikatsätze und freigegebene Cluster. Siehe: [Wirkt sich die TCP-Keepalive-Zeit auf MongoDB-Bereitstellungen aus? ](https://docs.mongodb.com/manual/faq/diagnostics/#faq-keepalive) in den häufig gestellten Fragen für weitere Informationen.

#### Windows {#windows}

* Deaktivieren Sie gegebenenfalls die Aktualisierung des NTFS-Attributs „Last Access Time“. Diese Einstellung entspricht der Deaktivierung von atime auf Unix-ähnlichen Systemen.

### WiredTiger {#wiredtiger}

Ab MongoDB 3.2 ist WiredTiger die standardmäßige Speicher-Engine für MongoDB. Diese Engine bietet einige robuste und skalierbare Funktionen, wodurch sie für allgemeine Datenbank-Workloads deutlich besser geeignet ist. Die folgenden Abschnitte beschreiben diese Funktionen.

#### Parallelität auf Dokumentebene {#document-level-concurrency}

WiredTiger verwendet die Parallelitätssteuerung auf Dokumentebene für Schreibvorgänge. Dadurch können mehrere Clients verschiedene Dokumente einer Sammlung gleichzeitig ändern.

Für die meisten Lese- und Schreibvorgänge verwendet WiredTiger eine optimistische Parallelitätssteuerung. WiredTiger verwendet nur Absichtssperren auf globaler, Datenbank- und Sammlungsebene. Wenn die Speicher-Engine Konflikte zwischen zwei Vorgängen erkennt, kommt es zu einem Schreibkonflikt, der dazu führt, dass MongoDB diesen Vorgang transparent erneut versucht. Einige globale Vorgänge, normalerweise kurzlebige Vorgänge mit mehreren Datenbanken, erfordern weiterhin eine globale „instanzübergreifende“ Sperre.

Für einige andere Vorgänge wie das Ablegen einer Sammlung ist weiterhin eine exklusive Datenbanksperre erforderlich.

#### Snapshots und Checkpoints {#snapshots-and-checkpoints}

WiredTiger nutzt MultiVersion Concurrency Control (MVCC). Beim Start eines Vorgangs erstellt WiredTiger eine Momentaufnahme (Point-in-Time-Snapshot) der Daten für die Transaktion. Ein Snapshot enthält eine konsistente Darstellung der In-Memory-Daten.

Beim Schreiben auf die Festplatte schreibt WiredTiger alle in einem Snapshot enthaltenen Daten konsistent über alle Datendateien auf die Festplatte. Die jetzt [permanenten](https://docs.mongodb.com/manual/reference/glossary/#term-durable) Daten dienen als Checkpoint in den Datendateien. Der Checkpoint stellt sicher, dass die Datendateien bis einschließlich zum letzten Checkpoint konsistent sind. Das heißt, Checkpoints können als Wiederherstellungspunkte dienen.

MongoDB konfiguriert WiredTiger so, dass Checkpoints (d. h. das Schreiben des Snapshots auf die Festplatte) in Intervallen von 60 Sekunden oder für jeweils 2 GB Journaldaten erstellt werden.

Während des Schreibens eines neuen Checkpoints ist der vorherige Checkpoint weiterhin gültig. Daher kann MongoDB den letzten gültigen Checkpoint nach einem Neustart auch dann wiederherstellen, wenn es während des Schreibens des neuen Checkpoints zu einem Fehler oder einem Absturz kommt.

Der neue Checkpoint wird verfügbar und dauerhaft, wenn die Metadatentabelle von WiredTiger automatisch aktualisiert wird, um auf den neuen Checkpoint zu verweisen. Sobald der neue Checkpoint verfügbar ist, gibt WiredTiger die Seiten des alten Checkpoints frei.

Wenn WiredTiger ohne [Journal](https://docs.mongodb.com/manual/reference/glossary/#term-durable) verwendet wird, kann MongoDB den letzten Checkpoint wiederherstellen. Um jedoch die Änderungen wiederherzustellen, die nach dem letzten Checkpoint durchgeführt wurden, müssen Sie mit [Journal](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal) arbeiten.

#### Journal {#journal}

WiredTiger verwendet ein Write-Ahead-Transaktionsprotokoll in Kombination mit [Checkpoints](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-checkpoints), um die Dauerhaftigkeit der Daten sicherzustellen.

Das WiredTiger-Journal speichert dauerhaft alle zwischen Checkpoints durchgeführten Datenänderungen. Wenn MongoDB zwischen Checkpoints beendet wird, verwendet es das Journal, um alle seit dem letzten Checkpoint geänderten Daten wiederzugeben. Informationen zur Häufigkeit, mit der MongoDB die Journaldaten auf die Festplatte schreibt, finden Sie unter [Journalprozess](https://docs.mongodb.com/manual/core/journaling/#journal-process).

Das WiredTiger-Journal wird mit der Datenkomprimierungsbibliothek [snappy](https://docs.mongodb.com/manual/core/journaling/#journal-process) komprimiert. Verwenden Sie zum Angeben eines alternativen Komprimierungsalgorithmus oder keiner Komprimierung die Einstellung [storage.wiredTiger.engineConfig.journalCompressor](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.journalCompressor).

Siehe [Journaling mit WiredTiger](https://docs.mongodb.com/manual/core/journaling/#journaling-wiredtiger).

>[!NOTE]
>
>Die minimale Protokolldatensatzgröße für WiredTiger beträgt 128 Bytes. Wenn ein Protokolldatensatz 128 Bytes oder kleiner ist, komprimiert WiredTiger diesen Datensatz nicht.
>
>Sie können das Journal deaktivieren, indem Sie für [storage.journal.enabled](https://docs.mongodb.com/manual/reference/configuration-options/#storage.journal.enabled) „false“ festlegen. So können Sie den Mehraufwand für die Pflege des Journals verringern.
>
>Wenn für [eigenständige](https://docs.mongodb.com/manual/reference/glossary/#term-standalone) Instanzen kein Journal verwendet wird, bedeutet dies, dass Sie einige Datenänderungen verlieren, falls MongoDB zwischen Checkpoints unerwartet beendet wird. Für Mitglieder von [Replikatsätzen](https://docs.mongodb.com/manual/reference/glossary/#term-replica-set) kann der Replikationsprozess ausreichende Dauerhaltbarkeitsgarantien bieten.

#### Komprimierung {#compression}

Mit WiredTiger unterstützt MongoDB die Komprimierung für alle Sammlungen und Indizes. Die Komprimierung minimiert die Speichernutzung zulasten der CPU-Nutzung.

WiredTiger nutzt standardmäßig die Blockkomprimierung der [snappy](https://docs.mongodb.com/manual/reference/glossary/#term-snappy)-Komprimierungsbibliothek für alle Sammlungen und die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für alle Indizes.

Für Sammlungen ist auch eine Blockkomprimierung mit [zlib](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) verfügbar. Verwenden Sie zum Angeben eines alternativen Komprimierungsalgorithmus oder keiner Komprimierung die Einstellung [storage.wiredTiger.collectionConfig.blockCompressor](https://docs.mongodb.com/manual/reference/glossary/#term-zlib).

Die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für Indizes können Sie mit der Einstellung [storage.wiredTiger.indexConfig.prefixCompression](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.indexConfig.prefixCompression) deaktivieren.

Die Komprimierungseinstellungen können während der Sammlung- und Indexerstellung auch pro Sammlung und Index konfiguriert werden. Siehe [Festlegen der Speicher-Engine-Optionen](https://docs.mongodb.com/manual/reference/method/db.createCollection/#create-collection-storage-engine-options) und [db.collection.createIndex() storageEngine](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/#createindex-options)-Option.

Für die meisten Arbeitslasten bieten die Standardkomprimierungseinstellungen ein ausgewogenes Verhältnis zwischen Speichereffizienz und Verarbeitungsanforderungen.

Das WiredTiger-Journal wird ebenfalls standardmäßig komprimiert. Informationen zur Journalkomprimierung finden Sie unter [Journal](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Speichernutzung {#memory-use}

Bei WiredTiger verwendet MongoDB sowohl den internen Cache von WiredTiger als auch den Dateisystemcache.

Seit Version 3.4 verwendet der interne Cache von WiredTiger standardmäßig eine der beiden folgenden Größen:

* 50 % RAM minus 1 GB oder
* 256 MB

WiredTiger verwendet standardmäßig die Snappy-Blockkomprimierung für alle Sammlungen und die Präfixkomprimierung für alle Indizes. Die Standardwerte für die Komprimierung sind auf globaler Ebene konfigurierbar, können aber auch während des Erstellens einer Sammlung oder eines Index für die jeweilige Sammlung oder den Index konfiguriert werden.

Für Daten im internen WiredTiger-Cache werden andere Darstellungen verwendet als für das Format auf der Festplatte:

* Die Daten im Dateisystem-Cache sind mit dem Format auf der Festplatte identisch, einschließlich der Vorteile einer Komprimierung für Datendateien. Der Dateisystemcache wird vom Betriebssystem verwendet, um die I/O der Festplatte zu reduzieren.

Indizes, die im internen Cache von WiredTiger geladen werden, weisen eine andere Datendarstellung auf als das On-Disk-Format, können aber dennoch die Indexpräfixkomprimierung nutzen, um die RAM-Nutzung zu reduzieren.

Die Indexpräfixkomprimierung dedupliziert allgemeine Präfixe aus indizierten Feldern.

Sammlungsdaten im internen Cache von WiredTiger sind unkomprimiert und verwenden eine andere Darstellung als das On-Disk-Format. Die Blockkomprimierung kann erhebliche Speichereinsparungen auf der Festplatte ermöglichen, doch müssen die Daten unkomprimiert werden, damit sie vom Server bearbeitet werden können.

Über den Dateisystemcache verwendet MongoDB automatisch alle freien Speicher, die nicht vom WiredTiger-Cache oder anderen Prozessen verwendet werden.

Informationen zum Anpassen der Größe des internen WiredTiger-Cache finden Sie unter [storage.wiredTiger.engineConfig.cacheSizeGB](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.cacheSizeGB) und [—wiredTigerCacheSizeGB](https://docs.mongodb.com/manual/reference/program/mongod/#cmdoption-wiredtigercachesizegb). Vermeiden Sie es, den internen Cache von WiredTiger über seinen Standardwert hinaus zu erhöhen.

### NUMA {#numa}

NUMA (Non-Uniform Memory Access) ermöglicht es einem Kernel zu verwalten, wie Speicher den Prozessorkernen zugeordnet wird. Obwohl dieser Prozess versucht, den Speicherzugriff für die Kerne zu beschleunigen, um sicherzustellen, dass sie auf die benötigten Daten zugreifen können, beeinträchtigt NUMA MMAP und führt zusätzliche Latenzzeiten ein, da Lesevorgänge nicht vorhergesagt werden können. Daher muss NUMA für den `mongod`-Prozess auf allen fähigen Betriebssystemen deaktiviert werden.

Im Wesentlichen ist in einer NUMA-Architektur der Speicher mit den CPUs verbunden und die CPUs sind mit einem Bus verbunden. In einer SMP- oder UMA-Architektur ist der Speicher mit dem Bus verbunden und wird von den CPUs gemeinsam genutzt. Wenn ein Thread Speicher auf einer NUMA-CPU zuweist, wird er gemäß einer Richtlinie zugewiesen. Standardmäßig wird Speicher zugeordnet, der an die lokale CPU des Threads angebunden ist, es sei denn, es ist keine freie vorhanden. In einem solchen Fall wird dann Speicher von einer freien CPU verwendet, allerdings mit höherem Aufwand. Nach der Zuordnung wechselt der Speicher nicht mehr zwischen den CPUs. Die Zuordnung erfolgt anhand einer Richtlinie, die vom übergeordneten Thread vererbt wird. Letztendlich ist dies der Thread, über den der Prozess gestartet wurde.

In vielen Datenbanken, die den Computer als eine mehrfache, einheitliche Speicherarchitektur betrachten, führt dieses Szenario dazu, dass die anfängliche CPU zuerst voll wird und die sekundäre CPU erst später gefüllt wird. Dies gilt insbesondere dann, wenn ein zentraler Thread für die Zuordnung von Speicherpuffern verantwortlich ist. Zur Lösung muss mithilfe des folgenden Befehls die NUMA-Richtlinie des Haupt-Threads geändert werden, mit dem der `mongod`-Prozess gestartet wird:

```shell
numactl --interleaved=all <mongod> -f config
```

Diese Richtlinie ordnet Speicher in einem Rundlaufverfahren über alle CPU-Knoten zu, wodurch eine gleichmäßige Verteilung über alle Knoten gewährleistet ist. Sie erzeugt nicht den leistungsfähigsten Speicherzugriff, wie in Systemen mit Mehrfach-CPU-Hardware. Ungefähr die Hälfte der Speichervorgänge erfolgt langsamer und über den Bus, aber `mongod` ist nicht auf eine optimale NUMA-Nutzung ausgelegt. Daher handelt es sich um einen vernünftigen Kompromiss.

### NUMA-Probleme {#numa-issues}

Wenn der `mongod`-Prozess über einen anderen Speicherort als vom Ordner `/etc/init.d` gestartet wird, ist davon auszugehen, dass der Start nicht mit der richtigen NUMA-Richtlinie erfolgt ist. Je nach Standardrichtlinie können Probleme entstehen. Dies liegt daran, dass die verschiedenen Linux® Package Manager-Installer für MongoDB auch einen Dienst installieren, dessen Konfigurationsdateien sich in `/etc/init.d` befinden und die oben beschriebenen Schritte ausführen. Wenn Sie MongoDB direkt aus einem Archiv (`.tar.gz`) installieren und ausführen, müssen Sie mongod unter dem Prozess `numactl` manuell ausführen.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren NUMA-Richtlinien finden Sie in der [numactl-Dokumentation](https://linux.die.net/man/8/numactl).

Das Verhalten des MongoDB-Prozesses kann abhängig von der jeweiligen Zuordnungsrichtlinie variieren:

```

```

* `-membind=<nodes>`
Die Zuordnung erfolgt nur auf den aufgeführten Knoten. Mongod ordnet keinen Speicher auf aufgeführten Knoten zu und nutzt möglicherweise nicht sämtlichen verfügbaren Speicher.

* `-cpunodebind=<nodes>`
Nur auf den Knoten ausführen. Mongod wird nur auf den angegebenen Knoten ausgeführt und nutzt nur den auf diesen Knoten verfügbaren Speicher.

* `-physcpubind=<nodes>`
Nur auf aufgelisteten CPUs (Kernen) ausführen. Mongod wird nur auf den aufgeführten CPUs ausgeführt und nutzt nur den auf diesen CPUs verfügbaren Speicher.

* `--localalloc`
Speicher wird immer auf dem aktuellen Knoten zugewiesen, aber es werden alle Knoten verwendet, auf denen der Thread ausgeführt wird. Wenn ein Thread die Zuordnung ausführt, wird nur der Speicher verwendet, der der CPU zur Verfügung steht.

* `--preferred=<node>`
Zwar wird die Zuordnung zu einem bestimmten Knoten vorgezogen, es wird aber auf einen anderen Knoten zurückgegriffen, wenn der bevorzugte Knoten voll ist. Für die Definition eines Knotens kann eine relative Notation verwendet werden. Außerdem werden die Threads auf allen Knoten ausgeführt.

Einige der Richtlinien können einen geringeren Wert als die für den `mongod`-Prozess verfügbare RAM-Gesamtmenge zur Folge haben. Im Gegensatz zu MySQL vermeidet MongoDB aktiv das Paging auf Betriebssystemebene, sodass der `mongod`-Prozess ggf. weniger Speicher erhält als verfügbar angezeigt wird.

#### Austausch {#swapping}

Aufgrund der speicherintensiven Natur von Datenbanken muss der Austausch auf Betriebssystemebene deaktiviert werden. Der MongoDB-Prozess vermeidet das Austauschen von vornherein.

#### Remote-Dateisysteme {#remote-filesystems}

Remote-Dateisysteme wie NFS werden für die internen Datendateien von MongoDB (die Datenbankdateien des mongod-Prozesses) nicht empfohlen, weil sie zu viel Latenz verursachen. Dies ist nicht mit dem freigegebenen Dateisystem zu verwechseln, das zum Speichern von Oak-Blobs (FileDataStore) erforderlich ist. Dafür wird NFS empfohlen.

#### Read-Ahead {#read-ahead}

Passen Sie „Read-Ahead“ an, damit nicht unnötige Blöcke von der Festplatte gelesen werden, wenn eine Seite mit einem zufälligen Lesevorgang eingebunden wird. Solche Ergebnisse bedeuten einen unnötigen Verbrauch von I/O-Bandbreite.

### Linux®-Anforderungen {#linux-requirements}

#### Minimale Kernelversionen {#minimum-kernel-versions}

* **2.6.23** für `ext4`-Dateisysteme

* **2.6.25** für `xfs`-Dateisysteme

#### Empfohlene Einstellungen für Datenbank-Festplatten {#recommended-settings-for-database-disks}

**Deaktivieren von atime**

Es wird empfohlen, `atime` für die Festplatten mit den Datenbanken zu deaktivieren.

**NOOP-Festplatten-Planung einstellen**

Gehen Sie folgendermaßen vor:

Überprüfen Sie zunächst die I/O-Planung, die durch Ausführen des folgenden Befehls eingestellt wird:

```shell
cat /sys/block/sdg/queue/scheduler
```

Wenn die Antwort `noop` lautet, gibt es nichts mehr, was Sie tun müssen.

Ist NOOP nicht als I/O-Scheduler eingerichtet, können Sie dies durch Ausführen von Folgendem ändern:

```shell
echo noop > /sys/block/sdg/queue/scheduler
```

**Anpassen des Werts für „Weiterlesen“**

Es wird empfohlen, für die Festplatten, auf denen MongoDB-Datenbanken ausgeführt werden, den Wert 32 zu verwenden. Dieser Wert beträgt 16 KB. Sie können ihn wie folgt festlegen:

```shell
sudo blockdev --setra <value> <device>
```

#### NTP aktivieren {#enable-ntp}

Vergewissern Sie sich, dass NTP auf dem Computer installiert ist, auf dem die MongoDB-Datenbanken gehostet werden. Beispielsweise können Sie NTP über Yum Package Manager auf einem CentOS-Rechner installieren:

```shell
sudo yum install ntp
```

Nachdem der NTP-Daemon installiert und erfolgreich gestartet wurde, können Sie die Drift-Datei auf den Zeitversatz Ihres Servers überprüfen.

#### Transparent Huge Pages deaktivieren {#disable-transparent-huge-pages}

Red Hat® Linux® nutzt einen Speicherverwaltungsalgorithmus mit der Bezeichnung THP (Transparent Huge Pages). Es wird empfohlen, diesen zu deaktivieren, wenn Sie das Betriebssystem für Datenbank-Workloads einsetzen.

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

In den meisten Installationen mit NUMA-Aktivierung wird NUMA automatisch vom MongoDB-Daemon deaktiviert, sofern die Ausführung als Dienst über den Ordner `/etc/init.d` erfolgt.

Wenn dies nicht der Fall ist, können Sie NUMA auf Prozessebene deaktivieren. Zum Deaktivieren führen Sie diese Befehle aus:

```shell
numactl --interleave=all <path_to_process>
```

`<path_to_process>` steht dabei für den Pfad zum mongod-Prozess.

Deaktivieren Sie dann den „zone_reclaim“-Modus, indem Sie Folgendes ausführen:

```shell
echo 0 > /proc/sys/vm/zone_reclaim_mode
```

#### Optimieren der ulimit-Einstellungen für den mongod-Prozess {#tweak-the-ulimit-settings-for-the-mongod-process}

Linux® ermöglicht eine konfigurierbare Kontrolle über die Ressourcenzuweisung mithilfe des Befehls `ulimit`. Dies kann auf Benutzer- oder Prozessbasis geschehen.

Es wird empfohlen, „ulimit“ für den mongod-Prozess gemäß den [MongoDB-empfohlenen ulimit-Einstellungen](https://docs.mongodb.org/manual/reference/ulimit/#recommended-ulimit-settings) zu konfigurieren.

#### Testen der MongoDB-I/O-Leistung {#test-mongodb-i-o-performance}

MongoDB bietet ein Tool namens `mongoperf`, das zum Testen der I/O-Leistung entwickelt wurde. Sie sollten damit die Leistung aller MongoDB-Instanzen in Ihrer Infrastruktur testen.

Informationen zum Verwenden von `mongoperf` finden Sie in der [MongoDB-Dokumentation](https://docs.mongodb.org/manual/reference/program/mongoperf/).

>[!NOTE]
>
>`mongoperf` ist ein Indikator für die MongoDB-Leistung auf der Plattform, auf der sie ausgeführt wird. Folglich sollten die Ergebnisse nicht als endgültig für die Leistung eines Produktionssystems angesehen werden.
>
>Um genauere Leistungsergebnisse zu erhalten, können Sie ergänzende Tests mit dem Linux®-Tool `fio` durchführen.

**Testen der Leseleistung auf den virtuellen Maschinen einer Bereitstellung**

Wechseln Sie nach der Installation des Tools in das MongoDB-Datenbankverzeichnis, um die Tests durchzuführen. Starten Sie dann den ersten Test, indem Sie `mongoperf` mit der folgenden Konfiguration ausführen:

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
>
>Überprüfen Sie während der Tests die I/O-Nutzungsstatistik für die fraglichen virtuellen Maschinen in Ihrem zur Betriebssystemüberwachung eingesetzten System. Wenn für die I/O-Lesevorgänge ein Testergebnis von unter 100 % ausgegeben wird, liegt womöglich ein Problem bei der virtuellen Maschine vor.

**Testen der Schreibleistung der primären MongoDB-Instanz**

Überprüfen Sie als Nächstes die I/O-Schreibleistung der primären MongoDB-Instanz, indem Sie `mongoperf` mit denselben Einstellungen über das MongoDB-Datenbankverzeichnis ausführen:

```shell
echo "{nThreads:32,fileSizeMB:1000,w:true}" | mongoperf
```

Die gewünschte Ausgabe sollte 12 MB pro Sekunde betragen und etwa 3000 IOPS erreichen, wobei die Anzahl der Threads nur geringfügig variiert.

## Schritte für virtualisierte Umgebungen {#steps-for-virtualised-environments}

### VMware {#vmware}

Wenn Sie virtualisierte Umgebungen mithilfe von VMware ESX verwalten und bereitstellen, müssen Sie für den MongoDB-Betrieb die folgenden Einstellungen über die ESX-Konsole vornehmen:

1. Deaktivieren Sie Memory-Ballooning.
1. Führen Sie eine Vorabzuweisung und Reservierung von Speicher für die virtuellen Computer durch, die die MongoDB-Datenbanken hosten sollen.
1. Weisen Sie dem `mongod`-Prozess über Storage I/O Control genügend E/A-Kapazität zu.
1. Garantieren Sie den MongoDB-Hostmaschinen CPU-Ressourcen, indem Sie die Option [CPU-Reservierung](https://docs.vmware.com/de/VMware-vSphere/7.0/com.vmware.vsphere.hostclient.doc/GUID-6C9023B2-3A8F-48EB-8A36-44E3D14958F6.html?hWord=N4IghgNiBc4RB7AxmALgUwAQGEAKBVTAJ3QGcEBXIpMkAXyA) verwenden.

1. Ziehen Sie die Verwendung von Paravirtual-E/A-Treibern in Betracht. <!-- URL is a 404 See [knowledgebase article](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1010398).-->

### Amazon Web Services {#amazon-web-services}

Informationen zum Einrichten von MongoDB mit Amazon Web Services finden Sie im Artikel [Configure AWS Integration](https://www.mongodb.com/docs/cloud-manager/tutorial/configure-aws-integration/) (Konfigurieren der AWS-Integration) auf der MongoDB-Website.

## Sichern von MongoDB vor der Bereitstellung {#securing-mongodb-before-deployment}

In diesem Beitrag über die [sichere Bereitstellung von MongoDB](https://blogs.adobe.com/security/2015/07/securely-deploying-mongodb-3-0.html) finden Sie Hinweise, wie Sie die Konfiguration Ihrer Datenbanken vor der Bereitstellung sichern können.

## Dispatcher {#dispatcher}

### Auswählen des Betriebssystems für den Dispatcher {#choosing-the-operating-system-for-the-dispatcher}

Damit Ihre MongoDB-Bereitstellung ordnungsgemäß funktioniert, muss auf dem Betriebssystem, auf dem der Dispatcher läuft, **Apache httpd** **Version 2.4 oder höher laufen.**

Stellen Sie zudem sicher, dass alle Bibliotheken im Build auf dem aktuellen Stand sind, um Auswirkungen auf die Sicherheit zu minimieren.

### Dispatcher-Konfiguration {#dispatcher-configuration}

Eine typische Dispatcher-Konfiguration verarbeitet das zehn- bis 20-Fache des Anforderungsdurchsatzes einer AEM-Einzelinstanz.

Da der Dispatcher hauptsächlich ohne Status ist, kann er mit Leichtigkeit horizontal skaliert werden. In einigen Bereitstellungen müssen Autorinnen und Autoren am Zugriff auf bestimmte Ressourcen gehindert werden. Es wird empfohlen, einen Dispatcher mit den Authoring-Instanzen zu verwenden.

Wenn AEM ohne Dispatcher ausgeführt wird, müssen die SSL-Beendigung und der Lastenausgleich von einer anderen Anwendung durchgeführt werden. Dies ist erforderlich, weil Sitzungen eine Affinität gegenüber der AEM-Instanz aufweisen müssen, auf der sie erstellt wurden. Dieses Konzept ist auch als Sticky-Verbindung bekannt. Damit soll sichergestellt werden, dass die Aktualisierungen der Inhalte mit minimaler Latenz erfolgen.

Weitere Informationen zur entsprechenden Konfiguration finden Sie in der [Dispatcherdokumentation](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher).

### Zusätzliche Konfiguration {#additional-configuration}

#### Sticky-Verbindungen  {#sticky-connections}

Sticky-Verbindungen stellen sicher, dass personalisierte Seiten und Sitzungsdaten für einen Benutzer bzw. eine Benutzerin alle auf derselben Instanz von AEM erstellt werden. Diese Daten werden in der Instanz gespeichert, sodass nachfolgende Anforderungen desselben Benutzers bzw. Benutzerin an dieselbe Instanz zurückgegeben werden.

Es wird empfohlen, Sticky-Verbindungen für alle inneren Ebenen zu aktivieren, die Routing-Anfragen an die AEM-Instanzen weiterleiten, damit nachfolgende Anfragen dieselbe AEM-Instanz erreichen. Auf diese Weise wird die Latenz minimiert, die andernfalls beim Aktualisieren von Inhalten zwischen Instanzen erkennbar ist.

#### Langes Ablaufdatum {#long-expires}

Standardmäßig werden Inhalte, die von einem AEM-Dispatcher gesendet werden, mit „Zuletzt geändert“ und „eTag“ versehen, ohne dass ein Hinweis auf den Ablauf des Inhalts erfolgt. Dadurch wird sichergestellt, dass die Benutzeroberfläche immer die neueste Version der Ressource erhält. Dies bedeutet auch, dass der Browser einen GET-Vorgang ausführt, um zu sehen, ob sich die Ressource geändert hat. Daher kann es je nach Seitenladezeit zu mehreren Anfragen kommen, auf die die HTTP-Antwort „304 (Nicht geändert)“ beträgt. Bei Ressourcen, die nicht ablaufen, wird der Inhalt zwischengespeichert, wenn Sie eine Ablaufdatum-Kopfzeile festlegen und die Kopfzeilen „Zuletzt geändert“ und „eTag“ entfernen. Und es werden keine weiteren Aktualisierungsanforderungen gestellt, bis das Datum in der Ablaufdatum-Kopfzeile erreicht ist.

Die Verwendung dieser Methode bedeutet jedoch, dass es keine vernünftige Möglichkeit gibt, die Ressource im Browser ablaufen zu lassen, bevor der Zeitraum für die Ablaufdatum-Kopfzeile abläuft. Um diesen Workflow zu umgehen, kann der HtmlClientLibraryManager so konfiguriert werden, dass unveränderliche URLs für Client-Bibliotheken verwendet werden.

Diese URLs werden garantiert nicht geändert. Wenn sich der Inhalt der in der URL enthaltenen Ressource ändert, werden die Änderungen in der URL wiedergegeben, sodass der Browser die richtige Version der Ressource anfordert.

Die Standardkonfiguration fügt dem HtmlClientLibraryManager einen Selektor hinzu. Als Selektor wird die Ressource im Dispatcher zwischengespeichert, wobei der Selektor intakt ist. Dieser Selektor kann auch verwendet werden, um das richtige Ablaufverhalten sicherzustellen. Der Standardselektor folgt dem Muster `lc-.*?-lc`. Die folgenden Apache-httpd-Konfigurationsanweisungen stellen sicher, dass alle Anforderungen, die diesem Muster entsprechen, mit einer angemessenen Ablaufzeit verarbeitet werden.

```xml
Header set Expires "Tue, 20 Jan 2037 04:20:42 GMT" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header set Cache-Control "public, no-transform, max-age=267840000" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset ETag "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Last-Modified "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Pragma "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
```

#### No Sniff {#no-sniff}

Wenn Inhalte ohne Inhaltstyp gesendet werden, versuchen viele Browser, den Inhaltstyp zu erraten, indem sie die ersten Bytes des Inhalts lesen. Diese Methode wird als „Sniffing“ bezeichnet. Sniffing eröffnet eine Sicherheitslücke, da Benutzer bzw. Benutzerinnen, die in das Repository schreiben können, möglicherweise schädliche Inhalte ohne Inhaltstyp hochladen können.

Daher wird empfohlen, die Kopfzeile `no-sniff` zu den Ressourcen hinzuzufügen, die vom Dispatcher abgewickelt werden. Allerdings speichert der Dispatcher keine Kopfzeilen im Cache. Daher bedeutet dies, dass jeder Inhalt, der aus dem lokalen Dateisystem bereitgestellt wird, seinen Inhaltstyp durch seine Erweiterung bestimmt, anstatt die ursprüngliche Inhaltstyp-Kopfzeile vom AEM-Ursprungsservers zu verwenden.

Die Option „No sniff“ kann sicher aktiviert werden, wenn bekannt ist, dass die Web-Applikation niemals zwischengespeicherten Ressourcen ohne Dateityp bereitstellt.

Sie können „No sniff“ einschließend aktivieren:

```xml
Header set X-Content-Type-Options "nosniff"
```

Sie kann aber auch selektiv aktiviert werden:

```xml
RewriteCond %{REQUEST_URI} \.(?:js|jsonp)$ [OR]
RewriteCond %{QUERY_STRING} (callback|jsonp|cb)=\w+
RewriteRule .* - [E=jsonp_request:1]
Header set X-Content-Type-Options "nosniff"  env=jsonp_request
Header setifempty Content-Type application/javascript env=jsonp_request
```

#### Inhaltssicherheitsrichtlinie {#content-security-policy}

Die standardmäßigen Dispatcher-Einstellungen ermöglichen eine offene Inhaltssicherheitsrichtlinie, auch als CSP (Content Security Policy) bezeichnet. Diese Einstellungen ermöglichen es einer Seite, Ressourcen von allen Domains gemäß den Standardrichtlinien der Browser-Sandbox zu laden.

Es ist wünschenswert einzuschränken, von wo Ressourcen geladen werden können, um zu verhindern, dass Code von nicht vertrauenswürdigen oder nicht verifizierten fremden Servern in die JavaScript-Engine geladen wird.

CSP ermöglicht eine Feinabstimmung von Richtlinien. In einer komplexen Anwendung müssen CSP-Header jedoch mit Vorsicht entwickelt werden, da zu restriktive Richtlinien Teile der Benutzeroberfläche beschädigen können.

>[!NOTE]
>
>Weitere Informationen zur Funktionsweise finden Sie auf der [OWASP-Seite zum Thema Inhaltssicherheitsrichtline](https://owasp.deteact.com/cheat/cheatsheets/Content_Security_Policy_Cheat_Sheet.html).

### Dimensionierung {#sizing}

Weitere Informationen zur Dimensionierung finden Sie unter [Richtlinien zur Hardware-Dimensionierung](/help/managing/hardware-sizing-guidelines.md).

### MongoDB-Leistungsoptimierung {#mongodb-performance-optimization}

Allgemeine Informationen zur MongoDB-Leistung finden Sie unter [Analysieren der MongoDB-Leistung](https://docs.mongodb.org/manual/administration/analyzing-mongodb-performance/).

## Bekannte Einschränkungen {#known-limitations}

### Gleichzeitige Installationen {#concurrent-installations}

Die gleichzeitige Verwendung mehrerer AEM Instanzen mit einer einzigen Datenbank wird von MongoMK zwar unterstützt, parallele Installationen jedoch nicht.

Um dieses Problem zu umgehen, führen Sie zuerst die Installation mit nur einer Instanz aus und fügen Sie erst nach deren Abschluss weitere hinzu.

### Länge des Seitennamens {#page-name-length}

Wenn AEM auf einer MongoMK-Persistenz-Manager-Bereitstellung ausgeführt wird, sind [Seitennamen auf 150 Zeichen beschränkt](/help/sites-authoring/managing-pages.md).

>[!NOTE]
>
>Lesen Sie die [MongoDB-Dokumentation](https://docs.mongodb.com/manual/reference/limits/), damit Sie sich mit den bekannten Einschränkungen und Schwellenwerten von MongoDB vertraut machen können.
