---
title: AEM mit MongoDB
seo-title: AEM mit MongoDB
description: Erfahren Sie mehr zu den Aufgaben und Aspekten einer erfolgreichen Bereitstellung von AEM mit MongoDB.
seo-description: Erfahren Sie mehr zu den Aufgaben und Aspekten einer erfolgreichen Bereitstellung von AEM mit MongoDB.
uuid: 8028832d-10de-4811-a769-fab699c162ec
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: cd3b979f-53d4-4274-b4eb-a9533329192a
docset: aem65
exl-id: 70a39462-8584-4c76-a097-05ee436247b7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '6513'
ht-degree: 93%

---

# AEM mit MongoDB{#aem-with-mongodb}

Dieser Artikel vermittelt vertiefende Kenntnisse zu Aufgaben und Aspekten, die für eine erfolgreiche Bereitstellung von Adobe Experience Manager mit MongoDB erforderlich sind.

Weitere bereitstellungsbezogene Informationen finden Sie im Abschnitt [Bereitstellen und Verwalten](/help/sites-deploying/deploy.md) der Dokumentation.

## Verwenden von MongoDB mit AEM  {#when-to-use-mongodb-with-aem}

MongoDB wird typischerweise zur Unterstützung von AEM-Autorbereitstellungen eingesetzt, die eines der folgenden Kriterien erfüllen:

* Mehr als 1.000 eindeutige Benutzer pro Tag
* Mehr als 100 gleichzeitige Benutzer
* Große Anzahl von Seitenbearbeitungen
* Umfassende Rollouts oder Aktivierungen

Die oben genannten Kriterien gelten nur für Autoreninstanzen und nicht für Veröffentlichungsinstanzen, die allesamt TarMK-basiert sein sollten. Die Anzahl der Benutzer bezieht sich auf authentifizierte Benutzer, da Autoreninstanzen ausschließlich authentifizierten Zugriff zulassen.

Werden die Kriterien nicht erfüllt, wird zwecks Verfügbarkeit eine aktive TarMK-Bereitstellung bzw. eine Standby-TarMK-Bereitstellung empfohlen. Im Allgemeinen sollte MongoDB dann in Erwägung gezogen werden, wenn sich die Skalierungsanforderungen nicht mit einer einzelnen Hardwarekomponente erfüllen lassen.

>[!NOTE]
>
>Weitere Informationen zur Dimensionierung von Autoreninstanzen und Definition gleichzeitiger Benutzer finden Sie in den [Richtlinien zur Hardwaredimensionierung](/help/managing/hardware-sizing-guidelines.md#authors-working-in-parallel).

### Minimale MongoDB-Bereitstellung für AEM  {#minimal-mongodb-deployment-for-aem}

Unten ist eine minimale Bereitstellung für AEM auf MongoDB abgebildet. Zur Vereinfachung wurden die SSL-Beendigungs- und HTTP-Proxykomponenten verallgemeinert. Es besteht aus einem einzelnen MongoDB-Replikatsatz mit einer primären und zwei sekundären Sequenz.

![chlimage_1-4](assets/chlimage_1-4.png)

Eine minimale Bereitstellung setzt voraus, dass 3 `mongod`-Instanzen als Replikatgruppe konfiguriert sind. Eine Instanz wird als primäres Replikat gewählt, die beiden anderen sind sekundäre Replikate; die Wahl wird von `mongod` verwaltet. Angebunden an jede Instanz ist eine lokale Festplatte. Damit der Cluster die Last bewältigen kann, wird ein Mindestdurchsatz von 12 MB/s mit mehr als 3.000 IOPS (I/O Operations per Second) empfohlen.

Die AEM-Autoren sind mit den `mongod`-Instanzen verbunden, wobei jeweils eine Verbindung zu allen drei `mongod`-Instanzen besteht. Schreibvorgänge werden an das primäre Replikat gesendet und Lesevorgänge können von allen Instanzen verarbeitet werden. Der Traffic wird lastabhängig von einem Dispatcher auf eine der aktiven AEM-Autoreninstanzen verteilt. Der Oak-Datenspeicher ist ein `FileDataStore` und die MongoDB-Überwachung erfolgt je nach Bereitstellungsort über MMS oder MongoDB Ops Manager. Die Betriebssystemebene und Protokolle können über Drittanbieterlösungen wie Splunk oder Ganglia überwacht werden.

Bei dieser Bereitstellung sind alle Komponenten für eine erfolgreiche Implementierung erforderlich. Fehlt nur eine Komponente, ist die Implementierung nicht funktionsfähig.

### Betriebssysteme  {#operating-systems}

Eine Aufstellung der unterstützten Betriebssysteme für AEM 6 finden Sie auf der Seite [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

### Umgebungen {#environments}

Virtualisierte Umgebungen werden unterstützt, sofern eine gute Kommunikation zwischen den verschiedenen, für das Projekt verantwortlichen technischen Teams vorhanden ist. Hierzu gehören das Team, das für die Ausführung von AEM verantwortlich ist, das Team, das für das Betriebssystem zuständig ist, und das Team, das die virtualisierte Infrastruktur verwaltet.

Es gibt spezifische Anforderungen in Bezug auf die I/O-Kapazität der MongoDB-Instanzen, um die sich das Team, das die virtualisierte Umgebung verwaltet, kümmern muss. Wenn das Projekt auf eine Cloudbereitstellung wie Amazon Web Services zurückgreift, müssen die Instanzen zur Unterstützung der MongoDB-Instanzen mit ausreichend I/O-Kapazität und -Konsistenz bereitgestellt werden. Andernfalls arbeiten die MongoDB-Prozesse und das Oak-Repository unzuverlässig und nicht einwandfrei.

In virtualisierten Umgebungen erfordert MongoDB bestimmte I/O- und VM-Konfigurationen, um sicherzustellen, dass das MongoDB-Speichermodul nicht von den VMware-Richtlinien zur Ressourcenzuweisung gelähmt wird. Eine erfolgreiche Implementierung sorgt dafür, dass es keine Barrieren zwischen den verschiedenen Teams gibt und dass sich alle für das Erreichen der erforderlichen Leistung einsetzen.

## Hardwarehinweise {#hardware-considerations}

### Speicherung {#storage}

Um den Lese- und Schreibdurchsatz für eine optimale Leistung zu erreichen, ohne hierzu auf eine vorzeitige horizontale Skalierung angewiesen zu sein, setzt MongoDB im Allgemeinen SSD-Speicher oder Speicher mit einer SSD-ähnlichen Leistung voraus.

### RAM {#ram}

Die MongoDB-Versionen 2.6 und 3.0, die das MMAP-Speichermodul verwenden, erfordern, dass das Workingset der Datenbank und der zugehörigen Indizes zum RAM passt.

Unzureichender RAM führt zu einer deutlichen Leistungsminderung. Die Größe des Workingsets und der Datenbank hängt stark von der Anwendung ab. Zwar sind gewisse Schätzungen möglich, dennoch lässt sich die erforderliche RAM-Menge am zuverlässigsten bestimmen, indem Sie die AEM-Anwendung erstellen und einen Auslastungstest durchführen.

Für den Auslastungstest kann das folgende Verhältnis zwischen Workingset und Gesamtdatengröße angenommen werden:

* 1:10 für SSD-Speicher
* 1:3 für Festplattenspeicher

Dies bedeutet, dass im Falle von SSD-Bereitstellungen für eine 2 TB große Datenbank 200 GB RAM erforderlich sind.

Obwohl dieselben Beschränkungen für das WiredTiger-Speichermodul in MongoDB 3.0 gelten, ist die Korrelation zwischen Workingset, RAM und Seitenfehlern nicht so stark, da das WiredTiger- und das MMAP-Speichermodul Speicherzuordnungen auf unterschiedliche Art und Weise verwenden.

>[!NOTE]
>
>Adobe empfiehlt das WiredTiger-Speichermodul für AEM 6.1-Bereitstellungen mit MongoDB 3.0.

### Datenspeicher  {#data-store}

Aufgrund der Beschränkungen des MongoDB-Workingsets wird empfohlen, den Datenspeicher unabhängig von MongoDB zu verwalten. In den meisten Umgebungen sollte ein für alle AEM-Instanzen verfügbarer `FileDataStore` mit einem NAS verwendet werden. Für Situationen, in denen die Amazon-Webdienste verwendet werden, gibt es auch einen `S3 DataStore`. Wenn der Datenspeicher dennoch in MongoDB verwaltet wird, sollten die Größe des Datenspeichers zur Datenbankgesamtgröße hinzugerechnet und die Workingset-Berechnungen entsprechend angepasst werden. Dies bedeutet unter Umständen, dass deutlich mehr RAM bereitgestellt werden muss, um eine Leistung ohne Seitenfehler sicherzustellen.

## Überwachung {#monitoring}

Die Überwachung ist für eine erfolgreiche Implementierung des Projekts von entscheidender Bedeutung. Bei Vorhandensein ausreichender Kenntnisse ist es durchaus möglich, AEM ohne Überwachung auf MongoDB auszuführen. Über diese Kenntnisse verfügen im Normalfall Techniker, die sich auf diesen Bereich der Bereitstellung spezialisiert haben.

Typischerweise werden ein F&amp;E-Techniker, der am Apache Oak-Core arbeitet, sowie ein MongoDB-Spezialist einbezogen.

Ohne Überwachung auf allen Ebenen sind detaillierte Kenntnisse der Codebasis erforderlich, um Probleme diagnostizieren zu können. Sofern eine Überwachung stattfindet und geeignete Anleitungen in Bezug auf die wichtigsten Statistiken erfolgen, sind die Implementierungsteams in der Lage, angemessen auf Anomalien zu reagieren.

Zwar kann mit Befehlszeilentools ein schneller Überblick über die Funktionsweise eines Clusters erlangt werden, aber in Echtzeit und über mehrere Hosts hinweg ist ein solcher Vorgang praktisch unmöglich. Befehlszeilentools liefern nur selten historische Daten, die länger als ein paar Minuten zurückliegen, und erlauben nie eine Korrelation zwischen verschieden Metriktypen. Ein kurzer Zeitraum langsamer `mongod`-Hintergrundsynchronisierungen bedeutet zusätzlichen manuellen Aufwand, um I/O-Wartezeiten oder übermäßige Write-Level mit einer freigegebenen Speicherressource von einer scheinbar nicht verbundenen virtuellen Maschine in Beziehung zu setzen.

### MongoDB Cloud Manager {#mongodb-cloud-manager}

MongoDB Cloud Manager ist ein kostenloser Dienst von MongoDB zur Überwachung und Verwaltung von MongoDB-Instanzen. Er bietet eine Echtzeitansicht der Leistung und Integrität von MongoDB-Clustern. Zudem können Sie mit diesem Dienst cloud- und privat gehostete Instanzen verwalten, sofern die Instanz den Cloud Manager-Überwachungsserver erreichen kann.

Dazu muss ein Agent auf der MongoDB-Instanz installiert sein, der eine Verbindung zum Überwachungsserver herstellt. Es gibt drei Agentenebenen:

* Einen Automatisierungsagenten, der alle Vorgänge auf dem MongoDB-Server vollständig automatisieren kann
* Einen Überwachungsagenten, der die `mongod`-Instanz überwachen kann
* Einen Sicherungsagenten, der geplante Datensicherungen durchführen kann

Obwohl sich durch die Verwendung von Cloud Manager zur Wartungsautomatisierung eines MongoDB-Clusters viele der routinemäßigen Aufgaben vereinfachen, müssen Sie den Dienst weder hierfür noch für die Durchführung von Sicherungen einsetzen. Wenn Sie sich bei der Überwachung für Cloud Manager entscheiden, ist jedoch eine Überwachung erforderlich.

Weitere Informationen zu MongoDB Cloud Manager finden Sie in der [MongoDB-Dokumentation](https://docs.cloud.mongodb.com/).

### MongoDB Ops Manager {#mongodb-ops-manager}

MongoDB Ops Manager entspricht als Software MongoDB Cloud Manager. Im Anschluss an die Registrierung kann Ops Manager heruntergeladen und lokal in einem privaten Datenzentrum oder auf einem beliebigen Laptop oder Desktoprechner installiert werden. Zum Speichern von Daten wird eine lokale MongoDB-Datenbank verwendet; die Kommunikation funktioniert genauso wie zwischen Cloud Manager und verwalteten Servern. Im Falle von Sicherheitsrichtlinien, die die Nutzung eines Überwachungsagenten untersagen, sollten Sie MongoDB Ops Manager verwenden.

### Überwachung von Betriebssystemen  {#operating-system-monitoring}

Eine Überwachung auf Betriebssystemebene ist erforderlich, um einen AEM-MongoDB-Cluster auszuführen.

Ganglia ist ein gutes Beispiel für ein solches System. Dieses Tool gibt einen Überblick über das Spektrum und die Details der erforderlichen Informationen, die über grundlegende Integritätsmetriken wie CPU, durchschnittliche Auslastung und freier Festplattenspeicher hinausgehen. Zur Problemdiagnose sind Informationen auf geringerer Ebene wie Entropiepool-Level, I/O-Wartezeiten der CPU, Sockets im FIN_WAIT2-Status erforderlich.

### Log-Aggregation  {#log-aggregation}

Bei einem Cluster mehrerer Server gehört die zentrale Aggregation von Protokollen, auch als Log-Aggregation bezeichnet, zu den Anforderungen eines Produktionssystems. Software wie Splunk unterstützt die Log-Aggregation und ermöglicht es Teams, Verhaltensmuster der Anwendung zu analysieren, ohne Protokolle manuell zu sammeln.

## Checklisten {#checklists}

In diesem Abschnitt werden die verschiedenen Schritte behandelt, die Sie ausführen sollten, um sicherzustellen, dass Ihre AEM- und MongoDB-Bereitstellungen ordnungsgemäß eingerichtet sind, bevor Sie ein Projekt implementieren.

### Netzwerk {#network}

1. Als Erstes müssen alle Hosts über einen DNS-Eintrag verfügen.
1. Alle Hosts sollten anhand ihres DNS-Eintrags von allen anderen routbaren Hosts aufgelöst werden können.
1. Alle MongoDB-Hosts sind von allen anderen MongoDB-Hosts im selben Cluster routbar.
1. MongoDB-Hosts können Pakete an MongoDB Cloud Manager und die anderen Überwachungsserver weiterleiten.
1. AEM-Server können Pakete an alle MongoDB-Server weiterleiten.
1. Die Paketlatenz zwischen einem AEM-Server und einem MongoDB-Server liegt unter zwei Millisekunden, und zwar ohne Paketverlust und mit einer Standardverteilung von maximal einer Millisekunde.
1. Es dürfen maximal zwei Hops zwischen einem AEM- und MongoDB-Server vorhanden sein.
1. Es gibt maximal zwei Hops zwischen zwei MongoDB-Servern.
1. Die Router zwischen Hauptservern (MongoDB oder AEM oder beliebige Kombinationen) entsprechen maximal der OSI-Schicht 3.
1. Wenn VLAN-Trunking oder Netzwerk-Tunnelling verwendet wird, müssen diese die im Hinblick auf die Paketlatenz durchgeführten Prüfungen bestehen.

### AEM-Konfiguration  {#aem-configuration}

#### Knotenspeicherkonfiguration {#node-store-configuration}

Die AEM-Instanzen müssen zum Verwenden von AEM mit MongoMK konfiguriert sein. Die Basis der MongoMK-Implementierung in AEM ist der Knotenspeicher „Dokument“.

Weitere Informationen zum Konfigurieren von Knotenspeichern finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM](/help/sites-deploying/data-store-config.md).

Es folgt das Beispiel der Konfiguration eines Knotenspeichers „Dokument“ für eine minimale MongoDB-Bereitstellung:

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

wobei:

* `mongodburi`
Der MongoDB-Server, zu dem AEM eine Verbindung herstellen muss. Verbindungen werden zu allen bekannten Mitgliedern der standardmäßigen Replikatgruppe hergestellt. Wenn MongoDB Cloud Manager verwendet wird, ist die Serversicherheit aktiviert. Die Verbindungszeichenfolge muss daher einen geeigneten Benutzernamen und ein passendes Kennwort enthalten. Nicht-Enterprise-Versionen von MongoDB unterstützen ausschließlich die Authentifizierung per Benutzername und Kennwort. Weitere Informationen zur Syntax der Verbindungszeichenfolge finden Sie in der [Dokumentation](https://docs.mongodb.org/manual/reference/connection-string/).

* `db`
Der Name der Datenbank. Die Standardeinstellung für AEM ist 
`aem-author`.

* `customBlobStore`
Wenn Binärdateien im Zuge der Bereitstellung in der Datenbank gespeichert werden, werden diese Teil des Workingsets. Aus diesem Grund wird empfohlen, keine Binärdateien in MongoDB zu speichern und einen alternativen Datenspeicher wie einen 
`FileSystem` Datenspeicher auf einem NAS.

* `cache`
Die Cachegröße in Megabyte. Dies ist auf verschiedene Caches verteilt, die in der 
`DocumentNodeStore`. Die Standardgröße ist 256 MB. Allerdings profitiert die Oak-Leseleistung von einem größeren Cache.

* `blobCacheSize`
Häufig verwendete Blobs können von AEM im Cache gespeichert werden. So wird vermieden, dass sie erneut aus dem Datenspeicher abgerufen werden. Dies wirkt sich deutlich auf die Leistung aus, insbesondere beim Speichern von Blobs in der MongoDB-Datenbank. Alle dateisystembasierten Datenspeicher profitieren von einem Datenträgercache auf Betriebssystemebene.

#### Datenspeicherkonfiguration  {#data-store-configuration}

Der Datenspeicher dient zum Speichern von Dateien, die größer sind als der Schwellenwert. Unterhalb dieses Schwellenwerts werden Dateien als Eigenschaften im Knotenspeicher „Dokument“ gespeichert. Wenn der `MongoBlobStore` verwendet wird, wird in MongoDB eine dedizierte Sammlung zum Speichern der Blobs erstellt. Diese Sammlung trägt zum Workingset der `mongod`-Instanz bei und setzt eine höhere RAM-Menge für die `mongod`-Instanz voraus, um Leistungsprobleme zu vermeiden. Daher wird für Konfigurationen empfohlen, in Produktionsbereitstellungen auf `MongoBlobStore` zu verzichten und einen `FileDataStore` einzusetzen, der von einem von allen AEM-Instanzen genutzten NAS gestützt wird. Da der Cache auf Betriebssystemebene eine effiziente Verwaltung von Dateien ermöglicht, sollte die Mindestgröße einer Datei auf der Festplatte auf einen Wert eingestellt werden, der der Blockgröße der Festplatte nahekommt. So kann das Dateisystem effizient verwendet werden und das Workingset der `mongod`-Instanz wird nicht durch eine große Anzahl kleiner Dokumente übermäßig belastet.

Es folgt ein Beispiel einer typischen Datenspeicherkonfiguration für eine minimale AEM-Bereitstellung mit MongoDB:

```xml
# org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config
# The minimum size of an object that should be stored in this data store.
minRecordLength=4096
path=/datastore
maxCachedBinarySize=4096
cacheSizeInMB=128
```

wobei:

* `minRecordLength`
Größe in Byte. Kleinere oder diesem Wert entsprechende Binärdateien werden im Knotenspeicher „Dokument“ gespeichert. Anstelle der ID des Blobs wird der Inhalt der Binärdatei gespeichert. Bei Binärdateien, die größer als diese Größe sind, wird die ID der Binärdatei als Eigenschaft des Dokuments in der Knotensammlung gespeichert und der Hauptteil der Binärdatei wird im 
`FileDataStore` auf der Festplatte. 4096 Byte entspricht einer typischen Dateisystem-Blockgröße.

* `path`
Der Pfad zum Stamm des Datenspeichers. Bei einer MongoMK-Bereitstellung muss es sich hier um ein freigegebenes Dateisystem handeln, das für alle AEM-Instanzen verfügbar ist. Normalerweise wird ein Network Attached Storage(NAS)-Server verwendet. Bei Cloud-Implementierungen wie Amazon Web Services wird der 
`S3DataFileStore` ist auch verfügbar.

* `cacheSizeInMB`
Die Gesamtgröße des Binärdatencache in Megabyte. Sie wird verwendet, um Binärdateien zwischenzuspeichern, die kleiner sind als die 
`maxCacheBinarySize` -Einstellung.

* `maxCachedBinarySize`
Die maximale Größe in Byte der im Binärdatencache gespeicherten Binärdatei. Im Falle eines dateisystembasierten Datenspeichers sollten keine hohen Werten für den Datenspeichercache verwendet werden, da die Binärdateien bereits vom Betriebssystem im Cache gespeichert wurden.

#### Deaktivieren von Abfragehinweisen  {#disabling-the-query-hint}

Es wird empfohlen, den mit allen Abfragen gesendeten Abfragehinweis zu deaktivieren, indem Sie die Eigenschaft

`-Doak.mongo.disableIndexHint=true`

beim AEM-Start hinzufügen. Auf diese Weise führt MongoDB basierend auf internen Statistiken eine Berechnung für den am besten geeigneten Index durch.

Wenn die Abfragehinweise nicht deaktiviert werden, bleibt jedwede AEM-Leistungsoptimierung ohne Wirkung.

#### Aktivieren des persistenten Cache für MongoMK  {#enable-persistent-cache-for-mongomk}

Es wird empfohlen, eine Konfiguration mit persistentem Cache für MongoDB-Bereitstellungen zu aktivieren, um die Geschwindigkeit für Umgebungen mit höherer I/O-Leseleitung zu maximieren. Weitere Informationen finden Sie in der [Jackrabbit Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/nodestore/persistent-cache.html).

## MongoDB-Betriebssystemoptimierungen  {#mongodb-operating-system-optimizations}

### Betriebssystemunterstützung {#operating-system-support}

MongoDB 2.6 nutzt ein Speichermodul mit Speicherzuordnung, das auf einige Aspekte der Verwaltung der Betriebssystemebene zwischen RAM und Datenträger empfindlich reagiert. Die Abfrage- und Leseleistung der MongoDB-Instanz hängt davon ab, dass langsame I/O-Vorgänge, häufig auch als Seitenfehler bezeichnet, vermieden oder beseitigt werden. Hierbei handelt es sich um Seitenfehler, die insbesondere den `mongod`-Prozess betreffen. Sie sind nicht zu verwechseln mit Seitenfehlern auf Betriebssystemebene. 

Für einen schnellen Betrieb sollte die MongoDB-Datenbank nur auf die Daten zugreifen, die bereits im RAM vorhanden sind. Die Daten, auf die die Datenbank zugreifen muss, bestehen aus Indizes und Daten. Diese Sammlung von Indizes und Daten wird als Workingset (oder Arbeitsseiten) bezeichnet. Wenn das Workingset größer ist als der verfügbare RAM, muss MongoDB diese Daten von der Festplatte einlagern (Paging), was zu einer höheren Anzahl von I/O-Operationen führt. Außerdem werden andere bereits im Arbeitsspeicher vorhandene Daten entfernt. Wenn Daten aufgrund dieses Entfernvorgangs erneut von der Festplatte geladen werden müssen, überwiegen Seitenfehler und die Leistung nimmt ab. Bei einem dynamischen und variablen Workingset tritt bei Supportvorgängen eine größere Anzahl von Seitenfehlern auf.

MongoDB ist für diverse Betriebssysteme verfügbar, darunter eine Vielzahl von Linux-Varianten, Windows und Mac OS. Weitere Einzelheiten finden Sie unter [https://docs.mongodb.com/manual/installation/#supported-platforms](https://docs.mongodb.com/manual/installation/#supported-platforms). Für MongoDB bestehen für die verschiedenen Betriebssysteme unterschiedliche Empfehlungen auf Systemebene. Diese sind unter [https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration](https://docs.mongodb.com/manual/administration/production-checklist-operations/#operating-system-configuration) dokumentiert und werden hier lediglich zusammengefasst.

#### Linux {#linux}

* Schalten Sie THP (Transparent Huge Pages) und die Defragmentierung ab. Weitere Informationen finden Sie unter [Transparent Huge Pages Settings](https://docs.mongodb.com/manual/tutorial/transparent-huge-pages/).
* [Ändern Sie die Einstellungen für readahead](https://docs.mongodb.com/manual/administration/production-notes/#readahead) auf den Geräten, auf denen Ihre Datenbankdateien gespeichert werden, damit sie zu Ihren Anforderungen passen.

   * Wenn Ihr Arbeitssatz größer als der verfügbare RAM-Speicher und das Muster für den Dokumentzugriff zufällig ist, müssen Sie readahead für die MMAPv1 Storage Engine eventuell auf 32 oder 16 herabsetzen. Probieren Sie verschiedene Einstellungen aus, um den optimalen Wert zu ermitteln, der den residenten Speicher maximiert und die Anzahl der Seitenfehler verringert.
   * Legen Sie für die WiredTiger Storage Engine readahead auf „0“ fest, unabhängig vom Typ des Speichermediums (Spinning, SSD usw.). In der Regel können Sie die empfohlene readahead-Einstellung verwenden, sofern Tests keinen messbaren, wiederholbaren und zuverlässigen Vorteil eines höheren readahead-Werts nachweisen. Der [MongoDB Professional Support](https://docs.mongodb.com/manual/administration/production-notes/#readahead) kann Sie beim Konfigurieren von readahead mit anderen Werten unterstützen.

* Deaktivieren Sie das Tool Tuned, wenn Sie RHEL 7/CentOS 7 in einer virtuellen Umgebung ausführen.
* Wenn RHEL 7/CentOS 7 in einer virtuellen Umgebung ausgeführt wird, ruft das Tuned-Tool automatisch ein aus dem Leistungsdurchsatz abgeleitetes Leistungsprofil auf, das für die readahead-Einstellungen automatisch 4 MB festlegt. Dies kann sich negativ auf die Leistung auswirken.
* Verwenden Sie für SSD-Laufwerke den Noop Scheduler oder den Deadline Scheduler.
* Verwenden Sie für virtualisierte Laufwerke in Gast-VMs den Noop Scheduler.
* Deaktivieren Sie NUMA oder legen Sie für vm.zone_reclaim_mode „0“ fest und führen Sie [mongod](https://docs.mongodb.com/manual/administration/production-notes/#readahead)-Instanzen mit Node Interleaving aus. Siehe: [MongoDB and NUMA Hardware](https://docs.mongodb.com/manual/administration/production-notes/#readahead).

* Passen Sie die ulimit-Werte Ihrer Hardware für Ihre Anforderungen an. Falls mehrere [mongod](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod)- oder [mongos](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos)-Instanzen unter demselben Benutzer ausgeführt werden, erhöhen Sie die ulimit-Werte entsprechend. Siehe: [UNIX ulimit Settings](https://docs.mongodb.com/manual/reference/ulimit/).

* Verwenden Sie die Option „noatime“ für den Einhängepunkt [dbPath](https://docs.mongodb.com/manual/reference/configuration-options/#storage.dbPath).
* Konfigurieren Sie für Ihre Umgebung ausreichende Werte für Datei-Handles (fs.file-max), Kernel-PID-Limit (kernel.pid_max) und die maximalen Threads pro Prozess (kernel.threads-max). Für große Systeme bilden die folgenden Werte einen guten Ausgangspunkt:

   * Wert für fs.file-max: 98000,
   * Wert für kernel.pid_max: 64000,
   * Wert für andkernel.threads-max: 64000

* Stellen Sie sicher, dass für Ihr System der Auslagerungsspeicher konfiguriert ist. Detaillierte Informationen zu den Größenanforderungen finden Sie in der Dokumentation zu Ihrem Betriebssystem.
* Stellen Sie sicher, dass der Standardwert des Systems für TCP-Keepalive richtig festgelegt ist. Der Wert „300“ bietet häufig eine bessere Performance für Replikatsätze und freigegebene Cluster. Siehe: [Does TCP keepalive time affect MongoDB Deployments?](https://docs.mongodb.com/manual/faq/diagnostics/#faq-keepalive) in den häufig gestellten Fragen.

#### Windows {#windows}

* Deaktivieren Sie gegebenenfalls die Aktualisierung des NTFS-Attributs „Last Access Time“. Dies entspricht der Deaktivierung von atime auf Unix-artigen Systemen.

### WiredTiger {#wiredtiger}

Ab MongoDB 3.2 ist WiredTiger das standardmäßige Speichermodul für MongoDB. Dieses Modul bietet einige robuste und skalierbare Funktionen, durch die es für allgemeine Datenbank-Workloads deutlich besser geeignet ist. Diese Funktionen werden in den folgenden Abschnitten beschrieben.

#### Parallelität auf Dokumentebene (Document Level Concurrency)  {#document-level-concurrency}

WiredTiger steuert die Parallelität von Schreibvorgängen auf Dokumentebene. So können mehrere Clients gleichzeitig verschiedene Dokumente einer Sammlung ändern.

Für die meisten Lese- und Schreibvorgänge nutzt WiredTiger vollständige Parallelität. WiredTiger sperrt ausschließlich mit beabsichtigten Sperren auf der globalen, Datenbank- und Sammlungsebene. Wenn das Speichermodul Konflikte zwischen zwei Vorgängen erkennt, kommt es bei einem der Vorgänge zu einem Schreibkonflikt. MongoDB versucht dann, den Vorgang transparent erneut auszuführen. Für einige globale Vorgänge, in der Regel kurzlebige Vorgänge, die mehrere Datenbanken betreffen, ist weiterhin eine globale Instanz-weite Sperre erforderlich.

Für einige andere Vorgänge, wie das Löschen einer Sammlung, ist weiterhin eine exklusive Datenbanksperrung erforderlich.

#### Snapshots und Checkpoints  {#snapshots-and-checkpoints}

WiredTiger nutzt MultiVersion Concurrency Control (MVCC). Beim Start eines Vorgangs erstellt WiredTiger eine Momentaufnahme (Point-in-Time-Snapshot) der Daten für die Transaktion. Ein Snapshot enthält eine konsistente Darstellung der In-Memory-Daten.

Beim Schreiben auf die Festplatte schreibt WiredTiger alle in einem Snapshot enthaltenen Daten konsistent über alle Datendateien auf die Festplatte. Die jetzt [permanenten](https://docs.mongodb.com/manual/reference/glossary/#term-durable) Daten dienen als Checkpoint in den Datendateien. Dieser Checkpoint stellt sicher, dass die Datendateien bis einschließlich zum letzten Checkpoint konsistent sind. Checkpoints können daher als Wiederherstellungspunkte genutzt werden.

MongoDB konfiguriert WiredTiger dahingehend, dass Checkpoints (d. h. das Schreiben des Snapshots auf die Festplatte) in Intervallen von 60 Sekunden oder für jeweils 2 Gigabyte Journaldaten erstellt werden.

Während ein neuer Checkpoint geschrieben wird, ist der vorherige Checkpoint weiterhin gültig. Daher kann MongoDB den letzten gültigen Checkpoint nach einem Neustart auch dann wiederherstellen, wenn es während des Schreibens des neuen Checkpoints zu einem Fehler oder einem Absturz kommt.

Der neue Checkpoint wird verfügbar und permanent, sobald die Metadatentabelle von WiredTiger automatisch aktualisiert wurde und auf den neuen Checkpoint verweist. Sobald der neue Checkpoint verfügbar ist, gibt WiredTiger die Seiten des alten Checkpoints frei.

Wenn WiredTiger ohne [Journal](https://docs.mongodb.com/manual/reference/glossary/#term-durable) verwendet wird, kann MongoDB den letzten Checkpoint wiederherstellen. Um jedoch die Änderungen wiederherzustellen, die nach dem letzten Checkpoint durchgeführt wurden, müssen Sie mit [Journal](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal) arbeiten.

#### Journal {#journal}

WiredTiger verwendet ein Write-Ahead-Transaktionsprotokoll in Kombination mit [Checkpoints](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-checkpoints), um die Dauerhaftigkeit der Daten sicherzustellen.

Das WiredTiger-Journal speichert dauerhaft alle zwischen Checkpoints durchgeführten Datenänderungen. Wenn MongoDB zwischen Checkpoints beendet wird, wird das Journal genutzt, um alle seit dem letzten Checkpoint geänderten Daten wiederzugeben. Informationen zur Frequenz, in der MongoDB die Journaldaten auf die Festplatte schreibt, finden Sie unter [Journaling Process](https://docs.mongodb.com/manual/core/journaling/#journal-process).

Das WiredTiger-Journal wird mit der Datenkomprimierungsbibliothek [snappy](https://docs.mongodb.com/manual/core/journaling/#journal-process) komprimiert. Einen anderen Komprimierungsalgorithmus oder keine Komprimierung können Sie mit der Einstellung [storage.wiredTiger.engineConfig.journalCompressor](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.journalCompressor) festlegen.

Weitere Informationen finden Sie unter: [Journaling with WiredTiger](https://docs.mongodb.com/manual/core/journaling/#journaling-wiredtiger).

>[!NOTE]
>
>Die minimale Größe der Protokolldatensätze für WiredTiger beläuft sich auf 128 Byte. Wenn ein Protokolldatensatz 128 oder weniger Byte groß ist, führt WiredTiger keine Komprimierung des Datensatzes durch.
>
>Sie können das Journal deaktivieren, indem Sie für [storage.journal.enabled](https://docs.mongodb.com/manual/reference/configuration-options/#storage.journal.enabled) „false“ festlegen. So können Sie den Mehraufwand für die Pflege des Journals verringern.
>
>Wenn für [Standalone](https://docs.mongodb.com/manual/reference/glossary/#term-standalone)-Instanzen kein Journal verwendet wird, bedeutet dies, dass Sie einige Datenänderungen verlieren, falls MongoDB zwischen Checkpoints unerwartet beendet wird. Für Mitglieder von [Replikatsätzen](https://docs.mongodb.com/manual/reference/glossary/#term-replica-set) kann der Replikationsprozess gegebenenfalls eine ausreichend garantierte Dauerhaftigkeit sicherstellen.

#### Komprimierung {#compression}

Mit WiredTiger unterstützt MongoDB eine Komprimierung für alle Sammlungen und Indizes. Die Komprimierung minimiert die Speichernutzung zulasten der CPU-Nutzung.

WiredTiger nutzt standardmäßig die Blockkomprimierung der [snappy](https://docs.mongodb.com/manual/reference/glossary/#term-snappy)-Komprimierungsbibliothek für alle Sammlungen und die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für alle Indizes.

Für Sammlungen ist auch eine Blockkomprimierung mit [zlib](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) verfügbar. Einen anderen Komprimierungsalgorithmus oder keine Komprimierung können Sie mit der Einstellung [storage.wiredTiger.collectionConfig.blockCompressor](https://docs.mongodb.com/manual/reference/glossary/#term-zlib) festlegen.

Die [Präfixkomprimierung](https://docs.mongodb.com/manual/reference/glossary/#term-prefix-compression) für Indizes können Sie mit der Einstellung [storage.wiredTiger.indexConfig.prefixCompressions](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.indexConfig.prefixCompression) deaktivieren.

Komprimierungseinstellungen können auch während des Erstellens einer Sammlung oder eines Index für die jeweilige Sammlung oder den Index konfiguriert werden. Weitere Informationen finden Sie unter [Specify Storage Engine Options](https://docs.mongodb.com/manual/reference/method/db.createCollection/#create-collection-storage-engine-options) und im Beitrag zur [storageEngine-Option von db.collection.createIndex()](https://docs.mongodb.com/manual/reference/method/db.collection.createIndex/#createindex-options).

Für die meisten Workloads stellen die standardmäßigen Komprimierungseinstellungen einen Ausgleich zwischen Speichereffizienz und Verarbeitungsanforderungen her.

Auch das WiredTiger-Journal wird standardmäßig komprimiert. Weitere Informationen zur Journalkomprimierung finden Sie unter [Journal](https://docs.mongodb.com/manual/core/wiredtiger/#storage-wiredtiger-journal).

#### Speicherverwendung {#memory-use}

Mit WiredTiger verwendet MongoDB sowohl den internen Cache von WiredTiger als auch den Dateisystemcache.

Seit Version 3.4 verwendet der interne Cache von WiredTiger standardmäßig eine der beiden folgenden Größen:

* 50 % RAM minus 1 GB oder
* 256 MB

WiredTiger verwendet standardmäßig für alle Sammlungen die Snappy-Blockkomprimierung und für alle Indizes die Präfixkomprimierung. Die Standardwerte für die Komprimierung sind auf globaler Ebene konfigurierbar, können aber auch während des Erstellens einer Sammlung oder eines Index für die jeweilige Sammlung oder den Index konfiguriert werden.

Für Daten im internen WiredTiger-Cache werden andere Darstellungen verwendet als für das On-Disk-Format:

* Daten im Dateisystemcache sind dieselben wie im On-Disk-Format, einschließlich der Vorteile einer Komprimierung für Datendateien. Der Dateisystemcache wird durch das Betriebssystem verwendet, um die Anzahl der E/A-Vorgänge auf dem Datenträger zu reduzieren.

Die in den internen Cache von WiredTiger geladenen Indizes haben eine andere Datendarstellung als das On-Disk-Format, nutzen jedoch weiterhin die Indexpräfixkomprimierung, um die RAM-Verwendung zu reduzieren.

Bei der Indexpräfixkomprimierung werden häufige Präfixe der indizierten Felder dedupliziert.

Sammlungsdaten sind im internen Cache von WiredTiger unkomprimiert und verwenden eine andere Darstellung als das On-Disk-Format. Die Blockkomprimierung kann signifikante On-Disk-Speichereinsparungen bewirken, die Daten müssen jedoch unkomprimiert sein, damit der Server damit arbeiten kann.

Über den Dateisystemcache verwendet MongoDB automatisch den gesamten freien Speicher, der nicht vom WiredTiger-Cache oder von anderen Prozessen verwendet wird.

Informationen zum Anpassen der Größe des internen WiredTiger-Caches finden Sie unter [storage.wiredTiger.engineConfig.cacheSizeGB](https://docs.mongodb.com/manual/reference/configuration-options/#storage.wiredTiger.engineConfig.cacheSizeGB) und [--wiredTigerCacheSizeGB](https://docs.mongodb.com/manual/reference/program/mongod/#cmdoption-wiredtigercachesizegb). Legen Sie für die Größe des internen WiredTiger-Caches möglichst keinen Wert über dem Standardwert fest.

### NUMA {#numa}

Über NUMA (Non-Uniform Memory Access) kann ein Kernel bestimmen, wie Speicher den Prozessorkernen zugeordnet wird. Obwohl hiermit der Speicherzugriff für Kerne beschleunigt und deren Zugriff auf die erforderlichen Daten sichergestellt werden soll, verursacht NUMA einen MMAP-Konflikt. Wie? Durch die zusätzlich entstehende Latenz, denn Lesevorgänge können nicht vorhergesagt werden. Aus diesem Grund muss NUMA für den `mongod`-Prozess auf allen Betriebssystemen mit diesen Funktionen deaktiviert werden.

Kurz gesagt: In einer NUMA-Architektur ist der Speicher mit CPUs verbunden und die CPUs mit einem Bus. In einer SMP- oder UMA-Architektur ist der Speicher mit dem Bus verbunden und wird von den CPUs gemeinsam genutzt. Wenn ein Thread Speicher einer NUMA-CPU zuordnet, geschieht dies gemäß einer Richtlinie. Standardmäßig wird Speicher zugeordnet, der an die lokale CPU des Threads angebunden ist, es sei denn, es ist keine freie vorhanden. In einem solchen Fall wird dann Speicher von einer freien CPU verwendet, allerdings mit höherem Aufwand. Nach der Zuordnung wechselt der Speicher nicht mehr zwischen den CPUs. Die Zuordnung erfolgt anhand einer Richtlinie, die vom übergeordneten Thread vererbt wird. Letztendlich ist dies der Thread, über den der Prozess gestartet wurde.

In vielen Datenbanken, in denen der Rechner als Multicore-Uniform-Speicherarchitektur angesehen wird, führt dies dazu, dass zunächst die anfängliche CPU aufgefüllt wird und später die sekundäre CPU. Dies gilt insbesondere dann, wenn Speicherpuffer über einen zentralen Thread zugeordnet werden. Zur Lösung muss die NUMA-Richtlinie des Hauptthreads geändert werden, mit dem der `mongod`-Prozess gestartet wird.

Dies kann durch Ausführen des folgenden Befehls erreicht werden:

```shell
numactl --interleaved=all <mongod> -f config
```

Diese Richtlinie ordnet Speicher mittels Roundrobin-Methode über alle CPU-Knoten hinweg zu und stellt sicher, dass eine gleichmäßige Verteilung über alle Knoten erfolgt. Sie bietet keinen hochperformanten Speicherzugriff wie Systeme mit mehreren CPU-Hardwarekomponenten. Ungefähr die Hälfte der Speichervorgänge erfolgt langsamer und über den Bus, aber `mongod` ist nicht auf eine optimale NUMA-Nutzung ausgelegt. Daher handelt es sich um einen vernünftigen Kompromiss.

### NUMA-Probleme {#numa-issues}

Wenn der Prozess `mongod` von einem anderen Speicherort als dem Ordner `/etc/init.d` gestartet wird, wird er wahrscheinlich nicht mit der richtigen NUMA-Richtlinie gestartet. Je nach Standardrichtlinie können Probleme entstehen. Dies liegt daran, dass die verschiedenen Linux Package Manager-Installationsprogramme für MongoDB auch einen Dienst mit Konfigurationsdateien installieren, die sich in `/etc/init.d` befinden und den oben beschriebenen Schritt ausführen. Wenn Sie MongoDB direkt aus einem Archiv ( `.tar.gz`) installieren und ausführen, müssen Sie mongod manuell unter dem `numactl`-Prozess ausführen.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren NUMA-Richtlinien finden Sie in der [numactl-Dokumentation](https://linux.die.net/man/8/numactl).

Das Verhalten des MongoDB-Prozesses variiert abhängig von der jeweiligen Zuordnungsrichtlinie:

```

```

* `-membind=<nodes>`
Weisen Sie nur die aufgeführten Knoten zu. Mongod ordnet keinen Speicher auf aufgeführten Knoten zu und nutzt möglicherweise nicht sämtlichen verfügbaren Speicher.

* `-cpunodebind=<nodes>`
Führen Sie nur auf den Knoten aus. Mongod wird nur auf den aufgeführten Knoten ausgeführt und nutzt nur den auf diesen Knoten verfügbaren Speicher.

* `-physcpubind=<nodes>`
Führen Sie nur auf aufgelisteten CPUs (Kerne) aus. Mongod wird nur auf den aufgeführten CPUs ausgeführt und nutzt nur den auf diesen CPUs verfügbaren Speicher.

* `--localalloc`
Speicher wird immer auf dem aktuellen Knoten zugewiesen, aber es werden alle Knoten verwendet, auf denen der Thread ausgeführt wird. Wenn ein Thread die Zuordnung ausführt, wird nur der Speicher verwendet, der der CPU zur Verfügung steht.

* `--preferred=<node>`
Zwar wird die Zuordnung zu einem bestimmten Knoten vorgezogen, es wird aber auf einen anderen Knoten zurückgegriffen, wenn der bevorzugte Knoten voll ist. Ein Knoten kann mittels relativer Notation definiert werden. Außerdem werden die Threads auf allen Knoten ausgeführt.

Einige der Richtlinien können einen geringeren Wert als die für den `mongod`-Prozess verfügbare RAM-Gesamtmenge zur Folge haben. Im Gegensatz zu MySQL vermeidet MongoDB aktiv das Paging auf Betriebssystemebene, sodass der `mongod`-Prozess ggf. weniger Speicher erhält als verfügbar angezeigt wird.

#### Swapping {#swapping}

Aufgrund der speicherintensiven Natur von Datenbanken muss das Swapping auf Betriebssystemebene deaktiviert werden. Der MongoDB-Prozess vermeidet Swapping per Design.

#### Remote-Dateisysteme {#remote-filesystems}

Remote-Dateisysteme wie NFS werden nicht für die internen Datendateien von MongoDB (die mongod-Prozessdatenbankdateien) empfohlen, da sie zu viel Latenz verursachen. Dies ist nicht mit dem freigegebenen Dateisystem zu verwechseln, das zum Speichern von Oak-Blobs (FileDataStore) erforderlich ist. Dafür wird NFS empfohlen.

#### Read-Ahead {#read-ahead}

&quot;Read-Ahead&quot;muss so angepasst werden, dass beim Einfügen einer Seite mithilfe eines zufälligen Lesevorgangs unnötige Blöcke nicht von der Festplatte gelesen werden, was zu einem unnötigen Verbrauch von I/O-Bandbreite führt.

### Linux-Anforderungen {#linux-requirements}

#### Kernel-Mindestversionen {#minimum-kernel-versions}

* **2.6.23** für  `ext4` Dateisysteme

* **2.6.25** für  `xfs` Dateisysteme

#### Empfohlene Einstellungen für Datenbankfestplatten {#recommended-settings-for-database-disks}

**Deaktivieren von „atime“**

Es wird empfohlen, `atime` für die Festplatten mit den Datenbanken zu deaktivieren.

**Festlegen des NOOP-Festplatten-Schedulers**

Gehen Sie dazu wie folgt vor:

Überprüfen Sie zuerst, welcher I/O-Scheduler aktuell festgelegt ist. Dies kann durch Ausführen des folgenden Befehls erreicht werden:

```shell
cat /sys/block/sdg/queue/scheduler
```

Erhalten Sie `noop` als Antwort, sind keine weiteren Maßnahmen erforderlich.

Ist NOOP nicht als I/O-Scheduler eingerichtet, können Sie dies durch Ausführen von Folgendem ändern:

```shell
echo noop > /sys/block/sdg/queue/scheduler
```

**Anpassen des Read-Ahead-Werts**

Es wird ein Wert von 32 für die Festplatten empfohlen, von denen MongoDB-Datenbanken ausgeführt werden. Dies entspricht 16 Kilobyte. Sie können den Wert wie folgt festlegen:

```shell
sudo blockdev --setra <value> <device>
```

#### Aktivieren von NTP  {#enable-ntp}

Stellen Sie sicher, dass NTP auf dem Rechner installiert und aktiv ist, auf dem die MongoDB-Datenbank gehostet wird. Beispielsweise können Sie NTP über Yum Package Manager auf einem CentOS-Rechner installieren:

```shell
sudo yum install ntp
```

Nachdem der NTP-Daemon installiert und erfolgreich gestartet wurde, können Sie die Drift-Datei auf den Zeitversatz Ihres Servers überprüfen.

#### Deaktivieren von THP  {#disable-transparent-huge-pages}

Red Hat Linux nutzt einen Speicherverwaltungsalgorithmus mit der Bezeichnung THP (Transparent Huge Pages). Es wird empfohlen, diesen zu deaktivieren, wenn Sie das Betriebssystem für Datenbankworkloads einsetzen.

Eine Deaktivierung ist mithilfe der folgenden Vorgehensweise möglich:

1. Öffnen Sie die Datei `/etc/grub.conf` im Texteditor Ihrer Wahl.
1. Fügen Sie der Datei „grub.conf“ die folgende Zeile hinzu:

   ```xml
   transparent_hugepage=never
   ```

1. Überprüfen Sie abschließend, ob die Einstellung wirksam geworden ist, indem Sie Folgendes ausführen:

   ```shell
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Wenn THP deaktiviert ist, sollte die Ausgabe des oben stehenden Befehls wie folgt sein:

   ```xml
   always madvise [never]
   ```

>[!NOTE]
>
>Weitere Informationen zu THP finden Sie in diesem [Artikel](https://access.redhat.com/solutions/46111).

#### Deaktivieren von NUMA {#disable-numa}

Bei den meisten Installationen, bei denen NUMA aktiviert ist, deaktiviert der MongoDB-Daemon ihn automatisch, wenn er als Dienst aus dem Ordner `/etc/init.d` ausgeführt wird.

Sollte dies nicht der Fall sein, können Sie NUMA prozessweise deaktivieren. Zum Deaktivieren führen Sie diese Befehle aus:

```shell
numactl --interleave=all <path_to_process>
```

Dabei ist `<path_to_process>` der Pfad zum mongod -Prozess.

Deaktivieren Sie dann den „zone_reclaim“-Modus, indem Sie Folgendes ausführen:

```shell
echo 0 > /proc/sys/vm/zone_reclaim_mode
```

#### Optimieren der ulimit-Einstellungen für den mongod-Prozess {#tweak-the-ulimit-settings-for-the-mongod-process}

Linux ermöglicht mit dem Befehl `ulimit` eine konfigurierbare Steuerung der Ressourcenzuweisung. Dies kann auf Benutzer- oder Prozessbasis geschehen.

Sie sollten „ulimit“ für den mongod-Prozess gemäß den [MongoDB-empfohlenen ulimit-Einstellungen](https://docs.mongodb.org/manual/reference/ulimit/#recommended-ulimit-settings) konfigurieren.

#### Testen der MongoDB-I/O-Leistung  {#test-mongodb-i-o-performance}

MongoDB bietet ein Tool namens `mongoperf`, das zum Testen der I/O-Leistung entwickelt wurde. Sie sollten damit die Leistung aller MongoDB-Instanzen in Ihrer Infrastruktur testen.

Informationen zum Verwenden von `mongoperf` finden Sie in der [MongoDB-Dokumentation](https://docs.mongodb.org/manual/reference/program/mongoperf/).

>[!NOTE]
>
>`mongoperf` wurde als Indikator für die MongoDB-Leistung auf der Plattform, auf der MongoDB ausgeführt wird, entwickelt. Daher sollten die Ergebnisse nicht als definitiver Wert für die Leistung eines Produktionssystems angesehen werden.
>
>Um genauere Leistungsergebnisse zu erhalten, können Sie ergänzende Tests mit dem Linux-Tool `fio` durchführen.

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

Die gewünschte Ausgabe sollte 12 MB pro Sekunde und ca. 3.000 IOPS erreichen, bei geringer Variation zwischen der Anzahl der Threads.

## Schritte für virtualisierte Umgebungen  {#steps-for-virtualised-environments}

### VMware {#vmware}

Wenn Sie virtualisierte Umgebungen mithilfe von VMware ESX verwalten und bereitstellen, müssen Sie für MongoDB über die ESX-Konsole die folgenden Einstellungen vornehmen:

1. Deaktivieren Sie Memory-Ballooning.
1. Führen Sie eine Vorabzuweisung und Reservierung von Speicher für die virtuellen Maschinen durch, die die MongoDB-Datenbanken hosten sollen.
1. Weisen Sie dem `mongod`-Prozess über Storage I/O Control genügend I/O-Kapazität zu.
1. Garantieren Sie den MongoDB-Hostmaschinen CPU-Ressourcen, indem Sie die Option für die [CPU-Reservierung](https://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.vmadmin.doc_41/vsp_vm_guide/configuring_virtual_machines/t_allocate_cpu_resources.html) einstellen.

1. Ziehen Sie die Verwendung von Paravirtual-I/O-Treibern in Betracht. Weitere Informationen dazu finden Sie in diesem [Knowledgebase-Artikel](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=1010398).

### Amazon Web Services {#amazon-web-services}

Informationen zum Einrichten von MongoDB mit Amazon Web Services finden Sie im Artikel [Configure AWS Integration](https://docs.cloud.mongodb.com/tutorial/configure-aws-settings/) (Konfigurieren der AWS-Integration) auf der MongoDB-Website.

## Sichern von MongoDB vor der Bereitstellung {#securing-mongodb-before-deployment}

Tipps zum Sichern der Datenbankkonfiguration vor der Bereitstellung finden Sie in diesem Blogpost zum Thema [Sichere MongoDB-Bereitstellung](https://blogs.adobe.com/security/2015/07/securely-deploying-mongodb-3-0.html).

## Dispatcher {#dispatcher}

### Auswählen des Betriebssystems für Dispatcher  {#choosing-the-operating-system-for-the-dispatcher}

Auf dem Betriebssystem, das den Dispatcher hostet, muss die **Apache-HTTPD**-**Version 2.4 oder höher** ausgeführt werden, damit es den Anforderungen der MongoDB-Bereitstellung gerecht wird.

Stellen Sie zudem sicher, dass alle Bibliotheken im Build auf dem aktuellen Stand sind, um Auswirkungen auf die Sicherheit zu minimieren.

### Dispatcher-Konfiguration {#dispatcher-configuration}

Eine typische Dispatcherkonfiguration verarbeitet das 10- bis 20-Fache des Anforderungsdurchsatzes einer AEM-Einzelinstanz.

Da der Dispatcher hauptsächlich ohne Status ist, ist eine horizontale Skalierung problemlos möglich. Bei manchen Bereitstellungen müssen Autoren am Zugriff auf bestimmte Ressourcen gehindert werden. Daher wird ausdrücklich die Verwendung eines Dispatchers bei Autoreninstanzen empfohlen.

Wird AEM ohne Dispatcher ausgeführt, müssen SSL-Beendigung und Lastenausgleich von einer anderen Anwendung durchgeführt werden. Dies ist erforderlich, weil Sitzungen eine Affinität gegenüber der AEM-Instanz aufweisen müssen, auf der sie erstellt wurden. Dieses Konzept ist auch als Sticky-Verbindung bekannt. Hierdurch soll sichergestellt werden, dass Inhaltsaktualisierungen eine minimale Latenz aufweisen.

Weitere Informationen zur entsprechenden Konfiguration finden Sie in der [Dispatcherdokumentation](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html).

### Zusätzliche Konfiguration {#additional-configuration}

#### Sticky-Verbindungen   {#sticky-connections}

Sticky-Verbindungen stellen sicher, dass personalisierte Seiten und Sitzungsdaten für einen Benutzer in derselben AEM-Instanz erstellt werden. Diese Daten werden in der Instanz gespeichert, sodass nachfolgende Anforderungen dieses Benutzers auf dieselbe Instanz zurückgreifen.

Es wird empfohlen, Sticky-Verbindungen für alle Inner-Layer-Routinganforderungen an AEM-Instanzen zu aktivieren, damit spätere Anforderungen nach Möglichkeit dieselbe AEM-Instanz erreichen. Hierdurch wird Latenz minimiert, die sich andernfalls zeigt, wenn Inhalt zwischen Instanzen aktualisiert wird.

#### Lange Ablaufzeiträume  {#long-expires}

Standardmäßig besitzt Inhalt, der von einem AEM-Dispatcher gesendet wird, Last-Modified- und ETag-Header, ohne Angabe eines Ablaufzeitpunkts für den Inhalt. Zwar wird auf diese Weise sichergestellt, dass die Benutzeroberfläche immer die neueste Ressourcenversion erhält, allerdings bedeutet dies auch, dass der Browser einen GET-Vorgang durchführt, um zu überprüfen, ob die Ressource geändert wurde. Dies kann zu mehreren Anforderungen führen, auf die abhängig von der Seitenladezeit die HTTP-Antwort 304 (Nicht geändert) erfolgt. Bei Ressourcen, die bekanntermaßen nicht ablaufen, wird durch Festlegen eines Expires-Headers sowie Entfernen der Last-Modified- und ETag-Header der Inhalt im Cache gespeichert. Außerdem werden erst dann wieder weitere Aktualisierungsanforderungen gestellt, wenn das Datum im Expires-Header erfüllt wird.

Wird diese Methode verwendet, steht jedoch keine sinnvolle Möglichkeit zur Verfügung, um ein Ablaufen der Ressource im Browser zu bewirken, bevor der Expires-Header abgelaufen ist. Um diese Situation zu mildern, kann HtmlClientLibraryManager so konfiguriert werden, dass unveränderliche URLs für Clientbibliotheken verwendet werden.

Diese URLs ändern sich auf keinen Fall. Wenn sich der in der URL enthaltene Hauptteil der Ressource ändert, werden diese Änderungen automatisch in der URL widergespiegelt. So ist sichergestellt, dass der Browser die richtige Ressourcenversion anfordert.

Im Rahmen der Standardkonfiguration wird HtmlClientLibraryManager ein Selektor hinzugefügt. Als Selektor wird die Ressource im Cache des Dispatchers mit intaktem Selektor gespeichert. Mit diesem Selektor kann ebenfalls ein korrektes Ablaufverhalten sichergestellt werden. Der Standardselektor folgt dem Muster `lc-.*?-lc` . Die folgenden Apache-HTTPD-Konfigurationsrichtlinien stellen sicher, dass alle Anforderungen, die diesem Muster entsprechen, unter Berücksichtigung einer angemessenen Ablaufzeit erledigt werden.

```xml
Header set Expires "Tue, 20 Jan 2037 04:20:42 GMT" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header set Cache-Control "public, no-transform, max-age=267840000" "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset ETag "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Last-Modified "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
Header unset Pragma "expr=(%{REQUEST_STATUS} -eq 200) && (%{REQUEST_URI} =~ /.*lc-.*?-lc.*/)"
```

#### Option „nosniff“{#no-sniff}

Wenn Inhalt ohne Inhaltstyp (Content-Type) gesendet wird, versuchen viele Browser, den Inhaltstyp zu erraten, indem die ersten Byte des Inhalts gelesen werden. Dies wird als „Sniffing“ bezeichnet. Sniffing verursacht eine Sicherheitsschwachstelle, da Benutzer, die in das Repository schreiben können, womöglich schädlichen Inhalt ohne Inhaltstyp hochladen.

Daher wird empfohlen, den Header `no-sniff` zu den Ressourcen hinzuzufügen, die vom Dispatcher abgewickelt werden. Allerdings speichert der Dispatcher keine Header im Cache. Dies bedeutet, dass der Inhaltstyp von Inhalten des lokalen Dateisystems anhand der Erweiterung ermittelt wird und nicht über den ursprünglichen Content-Type-Header des entsprechenden AEM-Ursprungsservers.

Die Option „nosniff“ kann sicher aktiviert werden, wenn bekannt ist, dass die Webanwendung niemals im Cache gespeicherte Ressourcen ohne Dateityp bereitstellt.

Die Option „nosniff“ kann einschließend aktiviert werden:

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

#### Inhaltssicherheitsrichtlinie  {#content-security-policy}

Die standardmäßigen Dispatchereinstellungen ermöglichen das Öffnen einer Inhaltssicherheitsrichtlinie (Content Security Policy, CSP). Hierdurch kann eine Seite Ressourcen von allen Domänen gemäß den Standardrichtlinien der Browser-Sandbox laden.

Das Laden von Ressourcen ist dann einzuschränken, wenn vermieden werden soll, dass in die JavaScript-Engine Code von nicht vertrauenswürdigen oder nicht überprüften Fremdservern geladen wird.

CPS ermöglicht die Feinabstimmung von Richtlinien. In einer komplexen Anwendung müssen die CSP-Header jedoch mit Vorsicht entwickelt werden, da zu strenge Richtlinien die Benutzeroberfläche teilweise beschädigen können.

>[!NOTE]
>
>Weitere Informationen zur Funktionsweise finden Sie auf der [OWASP-Seite zum Thema Inhaltssicherheitsrichtlinie](https://www.owasp.org/index.php/Content_Security_Policy).

### Dimensionierung {#sizing}

Weitere Informationen zur Dimensionierung finden Sie in den [Richtlinien zur Hardwaredimensionierung](/help/managing/hardware-sizing-guidelines.md).

### MongoDB-Leistungsoptimierung  {#mongodb-performance-optimization}

Allgemeine Informationen zur MongoDB-Leistung finden Sie unter [Analysieren der MongoDB-Leistung](https://docs.mongodb.org/manual/administration/analyzing-mongodb-performance/).

## Bekannte Einschränkungen  {#known-limitations}

### Gleichzeitige Installationen {#concurrent-installations}

Die gleichzeitige Verwendung mehrerer AEM-Instanzen mit einer Datenbank wird zwar von MongoMK unterstützt, gleichzeitige Installationen allerdings nicht.

Um dieses Problem zu umgehen, führen Sie zuerst die Installation mit nur einer Instanz aus und fügen Sie dann nach Abschluss derselben weitere hinzu.

### Seitenname Länge {#page-name-length}

Wenn AEM auf einer MongoMK-Persistenzmanager-Bereitstellung ausgeführt wird, sind die Seitennamen [auf 150 Zeichen begrenzt.](/help/sites-authoring/managing-pages.md)

>[!NOTE]
>
>[Lesen Sie die MongoDB-](https://docs.mongodb.com/manual/reference/limits/) Dokumentation , um sich mit den bekannten Einschränkungen und Schwellenwerten von MongoDB selbst vertraut zu machen.
