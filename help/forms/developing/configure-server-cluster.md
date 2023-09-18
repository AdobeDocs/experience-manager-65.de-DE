---
title: Konfigurieren und Fehlerbehebung für einen AEM Forms on JEE-Servercluster
description: Erfahren Sie, wie Sie einen Adobe Experience Manager (AEM) Forms on JEE-Servercluster konfigurieren und Fehler beheben.
exl-id: 230fc2f1-e6e5-4622-9950-dae9449ed3f6
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '3959'
ht-degree: 45%

---

# Konfigurieren von und Fehlerbehebung für AEM Forms auf einem JEE-Server-Cluster {#configuring-troubleshooting-aem-forms-jee-server-cluster}

## Vorausgesetztes Wissen {#prerequisites}

Kenntnis der Datenbankserver und Webumgebungen von Adobe Experience Manager (AEM) Forms on JEE, JBoss®, WebSphere® und WebLogic-Anwendungsservern, Red Hat® Linux®, SUSE® Linux®, Microsoft® Windows, IBM® AIX® oder Sun Solaris™, Oracle, IBM® DB2® oder SQL Server.

## Benutzerebene {#user-level}

Erweitert

Ein AEM Forms on JEE-Cluster ist eine Topologie, die es AEM Forms on JEE ermöglicht, gegenüber einem Cluster resistent zu sein. Außerdem ermöglicht es die Topologie, die Systemkapazität über die Fähigkeiten eines einzelnen Knotens hinaus zu skalieren. Ein Cluster kombiniert mehrere Knoten in einem einzigen logischen System, das Daten teilt und es Transaktionen ermöglicht, sich in ihrer Ausführung über mehrere Knoten zu erstrecken. Ein Cluster ist die gängigste Methode zur Skalierung von AEM Forms on JEE, da jede Kombination von Services, die eine beliebige Kombination von Arbeitslasten verarbeitet, unterstützt werden kann. Ein AEM Forms on JEE-Cluster eignet sich nicht unbedingt für alle Bereitstellungsarten, und eine nicht geclusterte Architektur mit einem Lastenausgleich für Server kann geeignet sein.

In diesem Dokument werden die spezifischen Konfigurationsanforderungen und potenziellen Problembereiche beschrieben, auf die Sie möglicherweise mit einem AEM Forms on JEE-Cluster stoßen.

## Was befindet sich in einem Cluster? {#what-is-in-cluster}

Die AEM Forms on JEE-Clusterknoten kommunizieren untereinander und teilen Informationen, damit der Cluster als Ganzes einen einheitlichen Konfigurations- und Anwendungszustand erhält. Das Teilen von Informationen innerhalb des Clusters erfolgt auf verschiedene Arten gleichzeitig, die in verschiedenen Kontexten verwendet werden. Die grundlegenden Methoden zum Teilen von Informationen sind in der folgenden Abbildung dargestellt:

![Anwendungsserver-Cluster](assets/application-server-cluster.jpg)

### Programm-Server-Cluster {#application-server-cluster}

Ein AEM Forms on JEE-Cluster stützt sich auf die Clustering-Funktionen des zugrunde liegenden Anwendungsservers. Anwendungsserver-Cluster ermöglichen die Verwaltung der Clusterkonfiguration als Ganzes und bieten Clusterdienste auf niedriger Ebene wie Java™ Naming and Directory Interface (JNDI), die es Softwarekomponenten ermöglichen, sich im Cluster zu finden. Die Komplexität der Clusterdienste und die zugrunde liegenden technischen Abhängigkeiten, die der Anwendungsserver hat, hängen vom Anwendungsserver ab. WebSphere® und WebLogic verfügen über ausgereifte Verwaltungsfunktionen für Cluster, während JBoss® einen grundlegenden Ansatz verfolgt.

### GemFire-Cache {#gemfire-cache}

Der GemFire-Cache ist ein verteilter Cache-Mechanismus, der in jedem Cluster-Knoten implementiert ist. Die Knoten finden einander und erstellen einen einzigen logischen Cache, der zwischen den Knoten kohärent gehalten wird. Die Knoten, die sich gegenseitig finden, fügen sich zusammen, um einen einzelnen fiktiven Cache zu verwalten, der in Abbildung 1 als Cloud angezeigt wird. Im Gegensatz zum globalen Dokumentenspeicher und der Datenbank ist der Cache eine reine fiktive Entität. Der tatsächlich zwischengespeicherte Inhalt wird im Speicher und im `LC_TEMP`-Verzeichnis auf jedem der Cluster-Knoten gespeichert.

### Datenbank {#database}

Die AEM Forms on JEE-Datenbank, auf die über die JDBC-Datenquellen IDP_DS, EDC_DS und andere zugegriffen wird, wird von allen Knoten des Clusters gemeinsam genutzt. Die persistentesten Daten zum Zustand von AEM Forms on JEE, z. B. welche Transaktionen ausgeführt werden, die Benutzerdaten, die mit laufenden Transaktionen verknüpft sind, und Daten dazu, wie Systemeinstellungen festgelegt wurden, befinden sich in dieser Datenbank.

### Globaler Dokumentenspeicher {#global-document-storage}

Der globale Dokumentenspeicher (GDS) ist ein dateisystembasierter Speicherbereich, der von Document Manager (IDPDocument-Klasse) in AEM Forms on JEE verwendet wird. Der globale Dokumentenspeicher speichert kurzlebige und dauerhaft genutzte Dateien, auf die alle Knoten des Clusters zugreifen können müssen.

### Sonstige Elemente {#other-items}

Zusätzlich zu diesen gemeinsam genutzten Hauptressourcen gibt es weitere Elemente mit einem bestimmten Cluster-Verhalten, z. B. Quartz. Quartz ist ein Planungs-Subsystem, das von AEM Forms on JEE verwendet wird. Es verwendet Datenbanktabellen, um sein Wissen darüber, was geplant ist und welche geplanten Aktivitäten ausgeführt werden, zu speichern. Quartz muss für Installationen und Cluster mit einem Knoten anders konfiguriert werden und sich von anderen AEM Forms on JEE-Einstellungen leiten lassen.

## Häufige Konfigurationsprobleme {#common-configuration}

Eines der frustrierendsten Dinge bei der Wartung oder Fehlerbehebung eines AEM Forms auf einem JEE-Cluster ist, dass es keinen einzigen Ort gibt, um sich zu vergewissern, dass der Cluster gesund ist. Um sicherzugehen, dass im Cluster alles gut ist, müssen einige Untersuchungen und Analysen durchgeführt werden. Abhängig davon, was mit der Cluster-Konfiguration nicht stimmt, gibt es mehrere Arten von Fehlern bei der Cluster-Operationen. Die folgende Abbildung zeigt einen schlecht konfigurierten Cluster, in dem mehrere der freigegebenen Ressourcen nicht ordnungsgemäß freigegeben sind.

![Schlecht konfigurierter Cluster](assets/bad-configuration-cluster.png)

Machen Sie sich mit der Funktionsweise von Clustering und den möglichen Elementen vertraut, nach denen Sie in einem Cluster suchen und überprüfen können, selbst wenn Sie nicht beabsichtigen, AEM Forms on JEE in einem Cluster auszuführen. Der Grund dafür ist, dass einige Teile von AEM Forms on JEE möglicherweise ihre Hinweise auf eine falsche Funktionsweise in einem Cluster nehmen und sich mit dem nicht erwarteten Clusterverhalten befassen.

Was stimmt also nicht mit der Freigabekonfiguration aus der Abbildung oben? In den folgenden Abschnitten werden die Probleme beschrieben:

### (1) GemFire-Cluster-Konfiguration {#gemfire-cluster-configuration}

Mehrere Dinge können beim GemFire-Cache schiefgehen. Zwei typische Szenarien sind:

* Knoten, die sich finden sollten, sind dazu nicht in der Lage.

* Knoten, die gruppiert sind, können sich gegenseitig finden und einen Cache freigeben, wenn sie dies nicht tun sollten.

Wenn Sie Knoten haben, die Sie streben zu gruppieren, müssen diese sich im Netzwerk finden. Standardmäßig wird dies mit UDP-Multicast-Nachrichten durchgeführt. Jeder Knoten sendet Broadcast-Nachrichten, die darauf hinweisen, dass er vorhanden ist, und jeder Knoten, der eine solche Nachricht erhält, beginnt mit den anderen Knoten zu sprechen, die er findet. Diese Art der automatischen Entdeckung ist üblich, und viele Arten von Software und Geräten tun dies.

Ein häufiges Problem bei der automatischen Erkennung besteht darin, dass Multicast-Nachrichten vom Netzwerk gefiltert werden können. Dies kann Teil einer Netzwerkrichtlinie sein, oder aufgrund von Software-Firewall-Regeln oder weil sie nicht über das Netzwerk navigieren können, das zwischen Knoten vorhanden ist. Aufgrund der allgemeinen Schwierigkeit, die automatische Entdeckung von UDP in komplexen Netzwerken zu verwenden, ist es gängige Praxis für Produktionsbereitstellungen, eine alternative Erkennungsmethode zu verwenden: TCP-Locators. Eine allgemeine Diskussion der TCP-Locators finden Sie in den Referenzen.

**Woher weiß ich, ob ich Locators oder UDP verwende?**

Die folgenden JVM-Eigenschaften steuern die Methode, die der GemFire-Cache verwendet, um andere Knoten zu finden.

Multicast-Einstellungen:

* `adobe.cache.multicast-port`: Der Multicast-Anschluss, der zum Kommunizieren mit anderen Mitgliedern des gelieferten Systems verwendet wird. Wenn dieser auf null festgelegt ist, wird Multicast für die Mitgliedererkennung und für die Verteilung deaktiviert.

* `gemfire.mcast-address` (optional): Überschreibt die Standard-IP-Adresse, die von Gemfire verwendet wird.

TCP-Locator-Einstellungen:

* `adobe.cache.cluster-locators`: Die IP-Adresse/der Hostname des TCP-Locators und des TCP-Locator-Ports für alle Locators, die von den Systemmitgliedern zur Kommunikation mit laufenden Locators verwendet werden.

Die Liste muss alle derzeit verwendeten Locators enthalten und für jedes Mitglied des Cluster-Systems konsistent konfiguriert sein.

Wenn die TCP-Locator-Liste leer ist, werden keine Locators und stattdessen die Multicast-Methode verwendet.

**Wie kann ich überprüfen, ob mein TCP-Locator ausgeführt wird?**

Wenn Sie TCP-Locators verwenden, sollten Sie als erstes Ihre TCP-Locators in der folgenden JVM-Eigenschaft auf allen Cluster-Knoten auflisten lassen:

`-Dadobe.cache.cluster-locators=aix01.adobe.com[22345],aix02.adobe.com[22345]`

Es ist nicht erforderlich, die Locators auf den Cluster-Knoten von AEM Forms auf JEE auszuführen. Sie können auf anderen Systemen, die nicht zum Cluster gehören, ausgeführt werden. Locators können von mehreren Systemen ausgeführt werden. Außerdem gilt es als Best Practice, Locators an zwei Standorten auszuführen, da ein einzelner Fehler der Locators möglicherweise zu einem Problem beim Neustart des Clusters führen könnte. Auf allen Systemen, auf denen Locators ausgeführt werden, sollten Sie sicherstellen können, dass sie mit den folgenden Befehlen auf diesen Computern ausgeführt werden:

`netstat -an | grep 22345`

Die erwartete Antwort sollte lauten:

`tcp 0 0 *.22345 *.* LISTEN`

Ein weiterer Überprüfungsbefehl ist:

`ps -ef | grep gemfire`

Die erwartete Antwort sollte ungefähr so aussehen:

`livecycl 331984 1 0 10:14:51 pts/0 0:03 java -cp ./gemfire.jar: -Dgemfire.license-type=production -Dlocators=localhost[22345] com.gemstone.gemfire.distributed.Locator 22345`

**Wie kann ich sehen, welche Knoten GemFire als im Cluster befindlich betrachtet?**

GemFire erzeugt Protokollierungsinformationen, mit denen festgestellt werden kann, welche Cluster-Mitglieder vom GemFire-Cache gefunden und übernommen wurden. Dies kann verwendet werden, um zu überprüfen, ob alle richtigen Clustermitglieder gefunden wurden und ob keine zusätzliche oder falsche Clusterknotenerkennung stattfindet. Die Protokolldatei für GemFire befindet sich im konfigurierten temporären Ordner von AEM Forms on JEE:

`.../LC_TEMP/adobeZZ__123456/Caching/Gemfire.log`

Die numerische Zeichenfolge nach `adobeZZ_` ist eindeutig für den Server-Knoten. Daher müssen Sie den tatsächlichen Inhalt Ihres temporären Ordners durchsuchen. Die beiden Zeichen nach `adobe` hängen vom Anwendungsservertyp ab: entweder `wl`, `jb`oder `ws`.

Die folgenden Beispielprotokolle zeigen, was passiert, wenn ein Cluster mit zwei Knoten sich selbst findet.

Auf dem ersten Knoten, AP-HP8:

```xml
[config 2011/08/05 09:28:09.143 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] This member, ap-hp8(4268):18763, is becoming group coordinator.
[info 2011/08/05 09:28:09.151 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Entered into membership in group GF6.5.1.17 with ID ap-hp8(4268)<v0>:18763/56449.
[info 2011/08/05 09:28:09.152 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Starting DistributionManager ap-hp8(4268)<v0>:18763/56449.
[info 2011/08/05 09:28:09.153 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Initial (membershipManager) view =  [ap-hp8(4268)<v0>:18763/56449]
[info 2011/08/05 09:28:09.153 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Admitting member <ap-hp8(4268)<v0>:18763/56449>. Now there are 1 non-admin member(s).
[info 2011/08/05 09:28:09.154 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] ap-hp8(4268)<v0>:18763/56449 is the elder and the only member.
[info 2011/08/05 09:28:09.163 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] Did not hear back from any other system. I am the first one.
[info 2011/08/05 09:28:09.164 EDT GemfireCacheAdapter <server.startup : 0> tid=0x65] DistributionManager ap-hp8(4268)<v0>:18763/56449 started on 239.192.81.1[33456]. There were 0 other DMs. others: []
[info 2011/08/05 09:28:20.841 EDT GemfireCacheAdapter <Pooled Message Processor 1> tid=0xc4] New administration member detected at ap-hp7(2821)<v1>:19498/59136.
```

Auf dem anderen Knoten: AP-HP7:

```xml
[info 2011/08/05 09:28:09.830 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Attempting to join distributed system whose membership coordinator is ap-hp8(4268)<v0>:18763 using membership ID ap-hp7(2821):19498
[info 2011/08/05 09:28:10.058 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Entered into membership in group GF6.5.1.17 with ID ap-hp7(2821)<v1>:19498/59136.
[info 2011/08/05 09:28:10.059 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Starting DistributionManager ap-hp7(2821)<v1>:19498/59136.
[info 2011/08/05 09:28:10.060 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Initial (membershipManager) view =  [ap-hp8(4268)<v0>:18763/56449, ap-hp7(2821)<v1>:19498/59136]
[info 2011/08/05 09:28:10.060 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Admitting member <ap-hp8(4268)<v0>:18763/56449>. Now there are 1 non-admin member(s).
[info 2011/08/05 09:28:10.060 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] Admitting member <ap-hp7(2821)<v1>:19498/59136>. Now there are 2 non-admin member(s).
[info 2011/08/05 09:28:10.128 EDT GemfireCacheAdapter <server.startup : 0> tid=0x64] DistributionManager ap-hp7(2821)<v1>:19498/59136 started on 239.192.81.1[33456]. There were 1 other DMs. others: [ap-hp8(4268)<v0>:18763/56449]
```

**Was ist, wenn GemFire Knoten findet, die es nicht finden sollte?**

Jeder einzelne Cluster, der ein Unternehmensnetzwerk teilt, sollte einen separaten Satz von TCP-Locators verwenden, wenn TCP-Locators verwendet werden, oder eine separate UDP-Anschlussnummer, wenn eine Multicast-UDP-Konfiguration verwendet wird. Da die automatische Erkennung von UDP die Standardkonfiguration für AEM Forms on JEE ist und derselbe Standardanschluss 33456 von mehreren Clustern verwendet wird, ist es möglich, dass Cluster, die nicht versuchen sollten, zu kommunizieren, dies unerwartet tun. Beispielsweise sollten die Produktions- und QA-Cluster getrennt bleiben, können jedoch über UDP-Multicast eine Verbindung zueinander herstellen.

Die häufigste Situation, in der Sie doppelte Ports in einem Netzwerk entdecken könnten, zu dem GemFire nicht ordnungsgemäß Clustering betreibt, ist die Bootstrap eines Clusters. Sie können feststellen, dass der Bootstrap-Prozess ohne eindeutige Ursache fehlschlägt. In der Regel treten Fehler wie diese auf:

```xml
Caused by: com.ibm.ejs.container.UnknownLocalException: nested exception is: com.adobe.pof.schema.ObjectTypeNotFoundException: Object Type: dsc.sc_service_configuration not found.
                at com.adobe.pof.schema.POFDefaultDomain.getObjectType(POFDefaultDomain.java:93)
                at com.adobe.idp.dsc.initializer.DSCInitializerBean.serviceConfigAuditAttributeExists(DSCInitializerBean.java:225)
                at com.adobe.idp.dsc.initializer.DSCInitializerBean.installSchema(DSCInitializerBean.java:186)
                at com.adobe.idp.dsc.initializer.DSCInitializerBean.bootstrap(DSCInitializerBean.java:94)
                at com.adobe.idp.dsc.initializer.EJSLocalStatelessDSCInitializerBeanLocalEJB_7bb34e85.bootstrap(Unknown Source)
                at com.adobe.livecycle.bootstrap.bootstrappers.DSCBootstrapper.bootstrap(DSCBootstrapper.java:68)
```

In diesem Fall arbeitet der Bootstrapper mit GemFire, um auf die erforderlichen Tabellen zuzugreifen. Außerdem besteht eine Inkonsistenz zwischen den Tabellen, auf die über JDBC zugegriffen wird, und den zwischengespeicherten Tabelleninformationen, die von GemFire zurückgegeben werden, das von einem anderen Cluster mit einer anderen zugrunde liegenden Datenbank stammt.

Obwohl ein doppelter Port oft während des Bootstrap sichtbar wird, ist es möglich, dass diese Situation später auftaucht. Dies kann vorkommen, wenn ein Cluster nach dem Herunterfahren neu gestartet wird, wenn die Bootstrap des anderen Clusters erfolgt ist. Oder wenn die Netzwerkkonfiguration geändert wird, um zuvor isolierte Cluster für Multicast-Zwecke für einander sichtbar zu machen.

Um diese Situationen zu diagnostizieren, sehen Sie sich die GemFire-Protokolle an und überlegen Sie sorgfältig, ob nur die erwarteten Knoten gefunden werden. Um das Problem zu beheben, muss die `adobe.cache.multicast-port` -Eigenschaft auf einen anderen Wert für einen oder beide Cluster fest.

### 2) GDS-Freigabe {#gds-sharing}

Die Freigabe des globalen Dokumentenspeichers wird außerhalb von AEM Forms on JEE selbst auf der O/S-Ebene konfiguriert, wo Sie dafür sorgen müssen, dass dieselbe freigegebene Ordnerstruktur für alle Clusterknoten verfügbar ist. Auf Systemen vom Typ Windows erfolgt dies durch Einrichten einer Dateifreigabe entweder von einem Knoten zum anderen oder von einem Remote-Dateisystem wie einer NAS-Einheit zu allen Knoten. Auf UNIX®-Systemen wird die Freigabe des globalen Dokumentenspeichers in der Regel über die NFS-Dateifreigabe durchgeführt, entweder von einem Knoten zum anderen oder über eine NAS-Einheit.

Ein möglicher Fehlermodus für den Cluster ist, wenn diese Remote-Dateifreigabe nicht verfügbar ist oder geringfügige Probleme aufweist. Eine Remote-Bereitstellung kann aufgrund von Netzwerkproblemen, Sicherheitseinstellungen oder einer falschen Konfiguration fehlschlagen. Ein Neustart des Systems kann dazu führen, dass Änderungen der Konfiguration, die Tage oder Wochen zuvor vorgenommen wurden, in Kraft treten, was zu Überraschungen führen kann.

**Was würde passieren, wenn eine NFS-Freigabe nicht bereitgestellt werden kann?**

Unter UNIX® kann die Art und Weise, wie NFS-Bereitstellungen der Verzeichnisstruktur zugeordnet sind, die Verfügbarkeit eines scheinbar nutzbaren GDS-Ordners ermöglichen, selbst wenn die Bereitstellung fehlschlägt. Ziehen Sie dies in Betracht:

* NAS-Server: Freigegebener NFS-Ordner /u01/iapply/livecycle_gds
* Knoten 1: ein Bereitstellungspunkt zum freigegebenen Ordner (auf dem DB-Server gehostet), der sich hier befindet: /u01/iapply/livecycle_gds
* Knoten 2: ein Bereitstellungspunkt zum freigegebenen Ordner (auf dem DB-Server gehostet), der sich hier befindet: /u01/iapply/livecycle_gds

* LCES gibt den Pfad zum globalen Dokumentenspeicher an: /u01/iapply/livecycle_gds

Wenn die Bereitstellung auf Knoten 1 fehlschlägt, enthält die Verzeichnisstruktur weiterhin einen Pfad `/u01/iapply/livecycle_gds` zum leeren Bereitstellungspunkt hinzu, und der Knoten scheint korrekt ausgeführt zu werden. Da der Inhalt des globalen Dokumentenspeichers jedoch nicht tatsächlich für den anderen Knoten freigegeben wird, funktioniert der Cluster nicht ordnungsgemäß. Dies kann vorkommen und hat zur Folge, dass der Cluster auf mysteriöse Weise ausfällt.

Es empfiehlt sich, die Elemente so anzuordnen, dass der Linux®-Bereitstellungspunkt nicht als Stammverzeichnis des globalen Dokumentenspeichers verwendet wird, sondern stattdessen ein Ordner darin als GDS-Stammordner verwendet wird:

* Wenn Sie über einen NFS-Server verfügen, kann dieser über ein Verzeichnis verfügen: /some/storage/lc_cluster_dev/LC_GDS
* Und auf Ihrem Cluster-Knoten haben Sie einen Bereitstellungspunkt: /u01/iapply/shared
* Stellen Sie nfs_server: /some/storage/lc_cluster_dev/u01/iapply/shared bereit
* Lassen Sie Ihren globalen Dokumentenspeicher auf /u01/iapply/shared/LC_GDS verweisen

Wenn die Bereitstellung jetzt aus irgendeinem Grund nicht erfolgreich ist, enthält der Bare-Bereitstellungspunkt keinen Ordner &quot;LC_GDS&quot;und Ihr Cluster schlägt vorhersehbar fehl, da er keinen GDS finden kann.

**Wie kann ich sicherstellen, dass alle Knoten denselben globalen Dokumentenspeicher sehen und über Berechtigungen verfügen?**

Die Überprüfung des Zugriffs und der Freigabe des globalen Dokumentenspeichers erfolgt am besten durch Zugriff auf jeden Knoten als interaktiver Benutzer. Sie können dies entweder über SSH oder Telnet zu UNIX®-Knoten oder über Remote-Desktop zu Windows-Systemen tun. Sie sollten in der Lage sein, auf jedem Knoten zum konfigurierten Ordner des globalen Dokumentenspeichers oder Dateisystem zu navigieren und Testdateien von jedem Knoten aus zu erstellen, der in allen anderen Knoten sichtbar ist.

Achten Sie auf die Benutzer-ID, unter der AEM Forms auf JEE ausgeführt wird. Bei Turnkey-Installationen unter Windows handelt es sich um einen lokalen Administrator. Unter UNIX® kann es sich um einen bestimmten Dienstbenutzer handeln, der im Startskript oder in der Anwendungsserverkonfiguration konfiguriert ist. Es ist wichtig, dass diese Benutzer-ID in der Lage ist, GDS-Dateien auf allen Knoten gleichermaßen zu erstellen und zu bearbeiten.

Auf UNIX®-Systemen verweigern NFS-Konfigurationen häufig das Stammeigentum oder die Root-Zugriffsrechte für Dateien und Objekte. Wenn Sie den Anwendungsserver als Stammbenutzer ausführen, müssen Sie möglicherweise Optionen auf dem NFS-Server, dem Knoten, der die Dateien bereitstellt, oder beides angeben. Dies ermöglicht den bilateralen Zugriff und die Kontrolle von Dateien, die von einem Knoten erstellt und von einem anderen aufgerufen werden.

### (3) Freigabe von Datenbanken {#database-sharing}

Damit ein Cluster ordnungsgemäß funktioniert, muss dieselbe Datenbank von allen Clustermitgliedern gemeinsam genutzt werden. Die Möglichkeiten, dies falsch zu machen, umfassen im Wesentlichen:

* versehentlich IDP_DS, EDC_DS, AdobeDefaultSA_DS oder andere erforderliche Datenquellen auf separaten Cluster-Knoten unterschiedlich festlegen, sodass die Knoten auf verschiedene Datenbanken verweisen.
* versehentlich mehrere separate Knoten so einstellen, dass sie eine Datenbank gemeinsam nutzen, obwohl sie das nicht sollten.

Abhängig von Ihrem Programm-Server kann es normal sein, dass die JDBC-Verbindung auf Cluster-Ebene definiert wird, sodass unterschiedliche Definitionen auf verschiedenen Knoten nicht möglich sind. Bei JBoss® ist es jedoch gänzlich möglich, Dinge so einzurichten, dass eine Datenquelle, wie IDP_DS, auf eine Datenbank auf Knoten 1 verweist, aber auf etwas Anderes auf Knoten 2 verweist.

Das umgekehrte Problem ist häufiger. Dies ist eine Situation, in der mehrere eigenständige (oder Cluster) AEM Forms on JEE-Knoten versehentlich auf dasselbe Schema verweisen, wenn sie nicht vorgesehen sind. Dies geschieht meistens, wenn eine DBA unwissentlich die Verbindungsinformationen einer einzelnen AEM Forms on JEE-Datenbank an sowohl das DEV- als auch das QA-Setup-Team weitergibt. Weder Team erkennt, dass die DEV- und QA-Instanzen separate Datenbanken erfordern.

## Programm-Server-Cluster {#application-server-cluster-1}

Um einen erfolgreichen AEM Forms on JEE-Cluster zu erhalten, muss der Anwendungsserver konfiguriert und ordnungsgemäß als Cluster ausgeführt werden. In WebSphere® und WebLogic ist dies ein unkomplizierter, gut dokumentierter Prozess. In JBoss® ist die Clusterkonfiguration ein wenig praktischer, und es kann eine Herausforderung sein, sicherzustellen, dass die Knoten so konfiguriert sind, dass sie als Cluster fungieren und tatsächlich suchen und miteinander kommunizieren. JBoss® ist intern auf JGroups angewiesen, die UDP-Multicast verwenden, um mit Peer-Knoten zu suchen und zu koordinieren. Einige der mit GemFire erwähnten Probleme können auftreten, z. B. Knoten, die sich nicht finden, wann sie es sollten, oder sich gegenseitig finden, wenn sie es nicht sollten.

Verweise:

* [Hochverfügbare Unternehmensdienste über JBoss®-Cluster](https://docs.jboss.org/jbossas/jboss4guide/r4/html/cluster.chapt.html)

* [Oracle WebLogic Server-mithilfe von Clustern](https://docs.oracle.com/cd/E12840_01/wls/docs103/pdf/cluster.pdf)

### Wie kann ich überprüfen, ob JBoss® richtig Clustering betreibt? {#check-jboss-clustering}

Wenn JBoss® beim Entdecken von Clustermitgliedern gestartet wird, werden INFO-Level-Meldungen über den Knoten, der dem Cluster beitritt, in der Protokolldatei/Konsole protokolliert.

Wenn bei Ausführung ein Cluster-Name über die Befehlszeilenoption -g angegeben wurde, werden Meldungen ähnlich den folgenden angezeigt:

```xml
GMS: address is 10.36.34.44:55200 (cluster=QE_cluster)
GMS: address is 10.36.34.44:55200 (cluster=QE_cluster-HAPartitionCache)
and ones like:

[org.jboss.ha.framework.interfaces.HAPartition.QE_cluster] (JBoss System Threads(1)-3) Number of cluster members: 1
2011-07-14 11:34:03,072 INFO  [org.jboss.ha.framework.interfaces.HAPartition.QE_cluster] (JBoss System Threads(1)-3) Other members: 0
2011-07-14 11:34:03,138 INFO  [org.jboss.cache.RPCManagerImpl] (main) Received new cluster view: [10.36.34.44:55200|0] [10.36.34.44:55200]
2011-07-14 11:34:03,139 INFO  [org.jboss.cache.RPCManagerImpl] (main) Cache local address is 10.36.34.44:55200
```

### Quartz Scheduler {#quartz-scheduler}

Im Allgemeinen soll die Verwendung des internen Quartz Scheduler durch AEM Forms on JEE in einem Cluster automatisch der globalen Clusterkonfiguration von AEM Forms on JEE im Allgemeinen folgen. Es gibt jedoch einen Fehler, Nr. 2794033, der dazu führt, dass die automatische Cluster-Konfiguration von Quartz fehlschlägt, wenn für Gemfire anstelle einer Multicast-Autodiscovery TCP-Locators verwendet werden. In diesem Fall wird Quartz fälschlicherweise in einem nicht geclusterten Modus ausgeführt. Dies führt zu Deadlocks und Datenbeschädigungen in den Quartz-Tabellen. Die Auswirkungen sind in Version 8.2.x schlechter als in Version 9.0, da Quartz nicht mehr so häufig verwendet wird, aber noch in Gebrauch ist.

Für dieses Problem sind folgende Fehlerbehebungen verfügbar: 8.2.1.2 QF2.143 und 9.0.0.2 QF2.44.

Das Problem lässt sich umgehen, indem diese beiden Eigenschaften festgelegt werden:

* `-Dadobe.cache.cluster.locators=xxx`

* `-Dadobe.cache.cluster-locators=xxx`

Eine Einstellung verwendet einen Punkt zwischen &quot;Cluster&quot;und &quot;Locators&quot;und die andere verwendet einen Bindestrich. Dies lässt sich einfach durchführen und ist weniger riskant als das Anwenden eines Software-Patches. Allerdings entsteht dabei auf künstliche Weise eine verwirrende, zusätzliche, falsch benannte Konfigurationseinstellung.

### Wie kann ich überprüfen, ob Quartz als einzelner Knoten oder als Cluster ausgeführt wird? {#check-quartz}

Um zu bestimmen, wie Quartz sich selbst konfiguriert hat, müssen Sie sich die vom AEM Forms on JEE Scheduler-Service beim Start generierten Nachrichten ansehen. Diese Meldungen werden mit dem Schweregrad „INFO“ erzeugt. Um die Nachrichten zu erhalten, kann es erforderlich sein, die Protokollebene anzupassen und neu zu starten. In der AEM Forms on JEE-Startsequenz beginnt die Quartz-Initialisierung mit der folgenden Zeile:

INFO  `[com.adobe.idp.scheduler.SchedulerServiceImpl]` IDPSchedulerService onLoad Es ist wichtig, diese erste Zeile in den Protokollen zu finden. Der Grund dafür ist, dass einige Anwendungsserver auch Quartz verwenden und ihre Quartz-Instanzen nicht mit den vom AEM Forms on JEE Scheduler-Dienst verwendeten Instanzen verwechselt werden sollten. Dies ist der Hinweis, dass der Scheduler-Dienst gestartet wird und die Zeilen, die darauf folgen, zeigen Ihnen, ob er ordnungsgemäß im Clustermodus gestartet wird. In dieser Sequenz werden mehrere Nachrichten angezeigt. Die letzte „started“-Nachricht zeigt die Konfiguration von Quartz an:

Hier wird der Name der Quartz-Instanz angegeben: `IDPSchedulerService_$_ap-hp8.ottperflab.adobe.com1312883903975`. Der Name der Quartz-Instanz des Planers beginnt immer mit der Zeichenfolge `IDPSchedulerService_$_`. Die Zeichenfolge, die am Ende dieses Abschnitts angehängt wird, teilt Ihnen mit, ob Quartz im Clustermodus ausgeführt wird. Die lange eindeutige Kennung, die aus dem Hostnamen des Knotens und einer langen Zeichenfolge von Ziffern generiert wurde, hier `ap-hp8.ottperflab.adobe.com1312883903975`, zeigt an, dass die Ausführung in einem Cluster erfolgt. Wenn es als einzelner Knoten verwendet wird, ist die Kennung eine zweistellige Zahl, &quot;20&quot;:

INFO  `[org.quartz.core.QuartzScheduler]` Scheduler `IDPSchedulerService_$_20` gestarted.
Diese Prüfung muss auf allen Clusterknoten separat durchgeführt werden, da die Planung jedes Knotens unabhängig voneinander bestimmt, ob er im Clustermodus ausgeführt werden soll.

### Welche Probleme entstehen, wenn Quartz im falschen Modus ausgeführt wird? {#quartz-running-in-wrong-mode}

Wenn Quartz für die Ausführung als einzelner Knoten eingerichtet ist, aber in einem Cluster ausgeführt wird und Quartz-Datenbanktabellen für andere Knoten freigegeben werden, führt dies zu einem unzuverlässigen Betrieb des AEM Forms on JEE Scheduler-Dienstes. Und es wird oft von Datenbankblockaden begleitet. Dies ist eine typische Stapelverfolgung, die Sie in dieser Situation möglicherweise sehen:

```xml
[1/20/11 10:40:57:584 EST] 00000035 ErrorLogger   E org.quartz.core.ErrorLogger schedulerError An error occured while marking executed job complete. job= 'Asynchronous.TaskFormDataSaved:12955380518320.5650479324757354'
 org.quartz.JobPersistenceException: Couldn't remove trigger: ORA-00060: deadlock detected while waiting for resource  [See nested exception: java.sql.SQLException: ORA-00060: deadlock detected while waiting for resource ]
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.removeTrigger(JobStoreSupport.java:1405)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.triggeredJobComplete(JobStoreSupport.java:2888)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport$38.execute(JobStoreSupport.java:2872)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport$40.execute(JobStoreSupport.java:3628)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.executeInNonManagedTXLock(JobStoreSupport.java:3662)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.executeInNonManagedTXLock(JobStoreSupport.java:3624)
        at org.quartz.impl.jdbcjobstore.JobStoreSupport.triggeredJobComplete(JobStoreSupport.java:2868)
        at org.quartz.core.QuartzScheduler.notifyJobStoreJobComplete(QuartzScheduler.java:1698)
        at org.quartz.core.JobRunShell.run(JobRunShell.java:273)
        at org.quartz.simpl.SimpleThreadPool$WorkerThread.run(SimpleThreadPool.java:529)
Caused by: java.sql.SQLException: ORA-00060: deadlock detected while waiting for resource
```

### Wie synchronisiere ich Systemzeitgeber in einem Cluster? {#synchronize-system-clocks-cluster}

Damit ein Cluster reibungslos funktioniert, müssen die Uhren auf allen Clusterknoten eng synchronisiert werden. Dies kann nicht ausreichend von Hand durchgeführt werden und muss von einer Form von Zeitsynchronisierungsdienst durchgeführt werden, der regelmäßig ausgeführt wird. Die Zeitgeber sämtlicher Knoten müssen im Sekundenbereich übereinstimmen. Es empfiehlt sich, nicht nur die Clusterknoten, sondern auch den Lastenausgleich, den Datenbankserver, den GDS-NAS-Server und alle anderen Komponenten zu synchronisieren.

Die Windows-Zeitsynchronisierung erfolgt in der Regel zum Domain-Controller. UNIX®-Systeme können mit NTP mit einer anderen Zeitquelle synchronisiert werden. Es ist am besten, wenn alle Systeme - sowohl die AEM Forms on JEE-Knoten als auch andere Systemkomponenten - nach Möglichkeit mit derselben Quelle synchronisieren.

Selbst in den temporärsten Testumgebungen reicht es nicht aus, die Uhren auf den Knoten manuell festzulegen. Die manuelle Einstellung der Uhren bietet nicht genügend präzise Synchronisation, und die Uhren auf den beiden Knoten driften unweigerlich relativ zueinander, sogar über einen Zeitraum von nur einem Tag. Ein aktiver Zeitsynchronisierungsmechanismus ist für einen zuverlässigen Cluster-Betrieb unerlässlich.

### Lastenausgleich {#load-balancer}

Eine typische Anforderung für einen Cluster, der benutzerinteraktive Dienste bereitstellt, ist ein HTTP-Lastenausgleich, der HTTP-Anforderungen über den Cluster verteilt. Für eine erfolgreiche Verwendung eines Lastenausgleichs mit einem AEM Forms on JEE-Cluster muss Folgendes konfiguriert werden:

* Sitzungspersistenz

* URL-Neuschreibungsregeln

* Konsistenzprüfung des Knotens

### Was sollte ich mit meiner Lastenausgleich-Konsistenzprüffunktion machen? {#load-balancer-health-check}

Einige Lastenausgleichsmodule können so konfiguriert werden, dass sie eine periodische Konsistenzprüfung der Knoten durchführen, bei denen ein Lastenausgleich erfolgt. Normalerweise ist dies eine URL zu einer Anwendungsfunktion, auf die der Lastenausgleich zugreifen versucht. Wenn die Belastung erfolgreich ist, wird davon ausgegangen, dass der Knoten in Ordnung ist, und er verbleibt im Lastenausgleich. Wenn die URL nicht geladen werden kann, wird davon ausgegangen, dass der Knoten fehlerhaft ist, und er wird aus dem Lastenausgleich ausgeschlossen. Im Allgemeinen ist die Konsistenzprüfungs-URL mit der Anmeldeseite von AEM Forms on JEE AdminUI verbunden. Dies stellt jedoch keine ideale Konsistenzprüfung für ein Cluster-Mitglied dar. Es wäre besser, einen kurzlebigen Prozess zu implementieren und als Konsistenzprüffunktion die REST-API-URL zu verwenden.

## Temporärer Dateipfad und ähnliche Cluster-Einstellungen {#temporary-file-path-cluster-settings}

Bestimmte Dateipfadeinstellungen in AEM Forms on JEE werden Cluster-weit festgelegt und haben für jeden Knoten dieselbe wirksame Einstellung, werden jedoch auf jedem Knoten unabhängig voneinander interpretiert, um auf lokale Dateien zu verweisen. Die wichtigsten sind die Einstellungen für den Schriftpfad und die temporären Verzeichniseinstellungen. Gehen Sie in der Admin-Benutzeroberfläche zum Bildschirm „Kernkonfigurationen“ (Startseite > Einstellungen > Kernsystem > Kernkonfigurationen).

Die folgenden Einstellungen sollten überprüft werden:

1. Speicherort des temporären Ordners
1. Speicherort des Ordners für Adobe-Serverschriftarten
1. Speicherort des Ordners für Kundenschriftarten
1. Speicherort des Ordners für Systemschriftarten
1. Speicherort der Konfigurationsdatei für Daten-Services

Der Cluster verfügt für jede dieser Konfigurationseinstellungen über nur eine Pfadeinstellung. Der Speicherort für den temporären Ordner kann beispielsweise `/home/project/QA2/LC_TEMP`. In einem Cluster ist es erforderlich, dass für jeden Knoten tatsächlich auf diesen bestimmten Pfad zugegriffen werden kann. Wenn ein Knoten den erwarteten temporären Dateipfad hat und ein anderer nicht, funktioniert der Knoten, der dies nicht tut, falsch.

Obwohl diese Dateien und Pfade möglicherweise von den Knoten oder separat oder auf Remote-Dateisystemen gemeinsam genutzt werden, empfiehlt es sich, lokale Kopien auf dem Festplattenspeicher des lokalen Knotens zu erstellen.

Insbesondere der Pfad des temporären Verzeichnisses sollte nicht zwischen Knoten freigegeben werden. Ein Verfahren, das dem beschriebenen ähnelt, um zu überprüfen, ob der globale Dokumentenspeicher verwendet werden soll, um zu überprüfen, ob der temporäre Ordner nicht freigegeben wird. Wechseln Sie zu jedem Knoten, erstellen Sie eine temporäre Datei im Pfad, der durch die Pfadeinstellung angegeben wird, und stellen Sie dann sicher, dass die anderen Knoten die Datei nicht teilen. Der Pfad des temporären Verzeichnisses sollte, wenn möglich, für jeden Knoten auf den lokalen Festplattenspeicher verweisen und er sollte überprüft werden.

Stellen Sie für jede der Pfadeinstellungen sicher, dass der Pfad tatsächlich vorhanden ist und von jedem Knoten im Cluster aus zugänglich ist. Verwenden Sie dabei die effektive Benutzeridentität, unter der AEM Forms on JEE ausgeführt wird. Die Inhalte des Schriftartenverzeichnisses müssen lesbar sein. Das temporäre Verzeichnis muss Lese- und Schreibzugriff sowie Steuerungselemente zulassen.
