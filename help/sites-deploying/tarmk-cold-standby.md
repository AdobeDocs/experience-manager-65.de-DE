---
title: Ausführen von AEM mit der TarMK-Cold-Standby-Funktion
description: Erfahren Sie, wie Sie eine TarMK-Cold-Standby-Einrichtung erstellen, konfigurieren und verwalten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: dadde3ee-d60c-4b87-9af0-a12697148161
source-git-commit: b66ec42c35b5b60804015d340b8194bbd6ef3e28
workflow-type: tm+mt
source-wordcount: '2671'
ht-degree: 33%

---

# Ausführen von AEM mit der TarMK-Cold-Standby-Funktion{#how-to-run-aem-with-tarmk-cold-standby}

## Einführung {#introduction}

Die Cold-Standby-Kapazität des Tar-Mikrokernels ermöglicht es einer oder mehreren Standby-Adobe Experience Manager-Instanzen (AEM), eine Verbindung zu einer primären Instanz herzustellen. Der Synchronisierungsprozess ist nur eine Möglichkeit, was bedeutet, dass er nur von der primären zu den Standby-Instanzen ausgeführt wird.

Die Standby-Instanzen sollen eine Live-Datenkopie des Master-Repositorys garantieren und einen schnellen Wechsel ohne Datenverlust sicherstellen, falls der Master aus irgendeinem Grund nicht verfügbar ist.

Inhalte werden linear zwischen der primären Instanz und den Standby-Instanzen synchronisiert. Dabei werden keine Integritätsprüfungen auf mögliche Datei- oder Repository-Beschädigungen durchgeführt. Aufgrund dieses Designs sind Standby-Instanzen exakte Kopien der primären Instanz und können nicht dazu beitragen, Inkonsistenzen auf primären Instanzen zu vermeiden.

>[!NOTE]
>
>Die Cold-Standby-Funktion soll Szenarien absichern, in denen eine hohe Verfügbarkeit erforderlich ist. **Autor** Instanzen. Für Situationen, in denen eine hohe Verfügbarkeit erforderlich ist **Veröffentlichen** -Instanzen, die den Tar-Mikrokernel verwenden, empfiehlt Adobe die Verwendung einer Veröffentlichungsfarm.
>
>Weitere Informationen zu verfügbaren Bereitstellungen finden Sie auf der Seite [Verfügbare Bereitstellungen](/help/sites-deploying/recommended-deploys.md). 

>[!NOTE]
>
>Wenn die Standby-Instanz eingerichtet ist oder vom Primären Knoten abgeleitet wird, ermöglicht sie nur den Zugriff auf die folgende Konsole (für administrative Aktivitäten):
>
>* OSGI-Web-Konsole
>
>Andere Konsolen sind nicht verfügbar.

## Funktionsweise {#how-it-works}

Auf der primären AEM-Instanz ist ein TCP-Port geöffnet, der eingehende Nachrichten überwacht. Derzeit gibt es zwei Arten von Nachrichten, die die Slaves an den Master senden:

* eine Meldung, die die Segment-ID der aktuellen Kopfzeile anfordert
* eine Meldung, die Segmentdaten mit einer angegebenen ID anfordert

Die Standby-Instanz fordert regelmäßig die Segment-ID des aktuellen Heads der primären Instanz an. Wenn das Segment lokal unbekannt ist, wird es abgerufen. Wenn es bereits vorhanden ist, werden die Segmente verglichen und Referenzsegmente werden bei Bedarf ebenfalls angefordert.

>[!NOTE]
>
>Standby-Instanzen empfangen keine Anforderungen, da sie nur im Synchronisierungsmodus ausgeführt werden. Der einzige auf einer Standby-Instanz verfügbare Abschnitt ist die Web-Konsole, um die Konfiguration von Bundles und Diensten zu erleichtern.

Eine typische TarMK-Cold-Standby-Bereitstellung: 

![chlimage_1](assets/chlimage_1.png)

## Sonstige Merkmale {#other-characteristics}

### Stabilität {#robustness}

Der Datenfluss ist so konzipiert, dass Verbindungs- und netzwerkbezogene Probleme automatisch erkannt und behandelt werden. Alle Pakete werden mit Prüfsummen gebündelt und bei Verbindungsproblemen oder beschädigten Paketen werden Wiederholungsmechanismen ausgelöst.

#### Leistung {#performance}

Die Aktivierung der TarMK-Cold-Standby-Funktion auf der primären Instanz hat fast keine messbaren Auswirkungen auf die Leistung. Der zusätzliche CPU-Verbrauch ist gering und die zusätzliche Festplatte und Netzwerk-I/O sollten keine Leistungsprobleme verursachen.

Auf der Standby-Instanz können Sie während des Synchronisierungsprozesses mit einem hohen CPU-Verbrauch rechnen. Da es sich bei dem Vorgang nicht um einen Multithread-Prozess handelt, kann er nicht durch die Verwendung mehrerer Kerne beschleunigt werden. Wenn keine Daten geändert oder übertragen werden, gibt es keine messbare Aktivität. Die Verbindungsgeschwindigkeit variiert je nach Hardware- und Netzwerkumgebung, hängt jedoch nicht von der Größe des Repositorys oder der SSL-Nutzung ab. Berücksichtigen Sie dies bei der Schätzung der für eine Erstsynchronisierung benötigten Zeit oder bei der zwischenzeitlichen Änderung vieler Daten auf dem primären Knoten.

#### Sicherheit {#security}

Wird davon ausgegangen, dass alle Instanzen, in derselben Intranet-Sicherheitszone ausgeführt werden, ist die Gefahr einer Sicherheitsverletzung deutlich geringer. Sie können jedoch eine zusätzliche Sicherheitsschicht hinzufügen, indem Sie SSL-Verbindungen zwischen den Slaves und dem Master aktivieren. Dadurch wird die Möglichkeit verringert, dass die Daten von einem Mann in der Mitte kompromittiert werden.

Darüber hinaus können Sie festlegen, welche Standby-Instanzen eine Verbindung herstellen dürfen, indem Sie die IP-Adressen eingehender Anforderungen beschränken. Dies sollte helfen sicherzustellen, dass niemand im Intranet das Repository kopieren kann.

>[!NOTE]
>
>Es wird empfohlen, einen Lastenausgleich zwischen dem Dispatcher und den Servern hinzuzufügen, die Teil des Cold Standby-Setups sind. Der Lastenausgleich sollte so konfiguriert werden, dass der Benutzer-Traffic nur zum **primary** -Instanz. Dies ist erforderlich, um Konsistenz zu gewährleisten und zu verhindern, dass Inhalte auf der Standby-Instanz mit anderen Mitteln als dem Cold Standby-Mechanismus kopiert werden.

## Erstellen eines AEM TarMK Cold Standby-Setups {#creating-an-aem-tarmk-cold-standby-setup}

>[!CAUTION]
>
>Die PID für den Segment-Knotenspeicher und den Standby-Store-Dienst wurde in AEM 6.3 im Vergleich zu den vorherigen Versionen wie folgt geändert:
>
>* von org.apache.jackrabbit.oak.**plugins**.segment.standby.store.StandbyStoreService für org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService
>* von org.apache.jackrabbit.oak.**plugins**.segment.SegmentNodeStoreService für org.apache.jackrabbit.oak.segment.SegmentNodeStoreService
>
>Nehmen Sie die erforderlichen Konfigurationsanpassungen vor, damit sie diese Änderung widerspiegeln.

Um ein TarMK-Cold-Standby-Setup zu erstellen, erstellen Sie zunächst die Standby-Instanzen, indem Sie eine Dateisystemkopie des gesamten Installationsordners der primären Instanz an einen neuen Speicherort erstellen. Sie können dann jede Instanz mit einem Ausführungsmodus starten, der ihre Rolle angibt ( `primary` oder `standby`).

Nachstehend finden Sie die Vorgehensweise, die zum Erstellen eines Setups mit einer Master- und einer Standby-Instanz befolgt werden muss:

1. Installieren Sie AEM.

1. Fahren Sie die Instanz herunter und kopieren Sie den Installationsordner an den Speicherort, von dem aus die Cold-Standby-Instanz ausgeführt wird. Auch wenn Sie von verschiedenen Computern aus arbeiten, geben Sie jedem Ordner einen beschreibenden Namen (wie *aem-primary* oder *aem-standby*), um zwischen den Instanzen zu unterscheiden.
1. Wechseln Sie zum Installationsordner der primären Instanz und gehen Sie wie folgt vor:

   1. Prüfen und löschen Sie alle vorherigen OSGi-Konfigurationen, die Sie möglicherweise unter haben `aem-primary/crx-quickstart/install`

   1. Erstellen Sie unter `install.primary` den Ordner `aem-primary/crx-quickstart/install`.

   1. Erstellen Sie die erforderlichen Konfigurationen für den bevorzugten Knotenspeicher und Datenspeicher unter `aem-primary/crx-quickstart/install/install.primary`
   1. Erstellen Sie im selben Verzeichnis die Datei `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config` und konfigurieren Sie sie entsprechend. Weitere Informationen zu den Konfigurationsoptionen finden Sie unter [Konfiguration](/help/sites-deploying/tarmk-cold-standby.md#configuration).

   1. Wenn Sie eine AEM-TarMK-Instanz mit einem externen Datenspeicher verwenden, erstellen Sie unter `aem-primary/crx-quickstart/install` den Ordner `crx3` namens `crx3`.

   1. Speichern Sie die Konfigurationsdatei für den Datenspeicher im Ordner `crx3`.

   Wenn Sie beispielsweise eine AEM TarMK-Instanz mit einem externen Dateidatenspeicher ausführen, benötigen Sie diese Konfigurationsdateien:

   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   * `aem-primary/crx-quickstart/install/crx3/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`

   Nachfolgend finden Sie Beispielkonfigurationen für die primäre Instanz:

   **Beispiel für** **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   customBlobStore=B"true"
   standby=B"false"
   ```

   **Beispiel für org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   mode="primary"
   port=I"8023"
   ```

   **Beispiel für org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   path="./crx-quickstart/repository/datastore"
   minRecordLength=I"16384"
   ```

1. Starten Sie die Primärherstellung, um sicherzustellen, dass Sie den primären Ausführungsmodus angeben:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Erstellen Sie einen Apache Sling Logging Logger für die **org.apache.jackrabbit.oak.segment** Paket. Setzen Sie die Protokollebene auf &quot;Debuggen&quot;und verweisen Sie die Protokollausgabe auf eine separate Protokolldatei, z. B. */logs/tarmk-coldstandby.log*. Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
1. Navigieren Sie zum Speicherort der **Standby** und starten Sie sie, indem Sie die JAR-Datei ausführen.
1. Erstellen Sie dieselbe Protokollierungskonfiguration wie für die primäre Instanz. Beenden Sie dann die Instanz.
1. Bereiten Sie dann die Standby-Instanz vor. Führen Sie dazu die gleichen Schritte wie für die primäre Instanz aus:

   1. Löschen Sie alle Dateien, die Sie möglicherweise unter `aem-standby/crx-quickstart/install`.
   1. Erstellen Sie unter `install.standby` den Ordner `aem-standby/crx-quickstart/install`.

   1. Erstellen Sie zwei Konfigurationsdateien mit den folgenden Namen:

      * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
      * `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`

   1. Erstellen Sie unter `crx3` den Ordner `aem-standby/crx-quickstart/install`.

   1. Erstellen Sie die Datenspeicherkonfiguration und speichern Sie sie unter `aem-standby/crx-quickstart/install/crx3`. Für dieses Beispiel müssen Sie die folgende Datei erstellen:

      * org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config

   1. Bearbeiten Sie die Dateien und erstellen Sie die erforderlichen Konfigurationen.

   Nachfolgend finden Sie Beispiel-Konfigurationsdateien für eine typische Standby-Instanz:

   **Beispiel für org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   name="Oak-Tar"
   service.ranking=I"100"
   standby=B"true"
   customBlobStore=B"true"
   ```

   **Beispiel für org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   mode="standby"
   primary.host="127.0.0.1"
   port=I"8023"
   secure=B"false"
   interval=I"5"
   standby.autoclean=B"true"
   ```

   **Beispiel für org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config**

   ```xml
   org.apache.sling.installer.configuration.persist=B"false"
   path="./crx-quickstart/repository/datastore"
   minRecordLength=I"16384"
   ```

1. Starten Sie die **Standby** -Instanz mithilfe des Standby-Ausführungsmodus:

   ```xml
   java -jar quickstart.jar -r standby,crx3,crx3tar
   ```

Der Dienst kann auch über die Web-Konsole konfiguriert werden, indem Sie:

1. Wechseln Sie zur Web-Konsole unter: *https://Server-Adresse:Serverport/system/console/configMgr*.
1. Suchen nach einem Dienst namens **Apache Jackrabbit Oak Segment Tar Cold Standby Service** und doppelklicken Sie darauf, um die Einstellungen zu bearbeiten.
1. Speichern Sie die Einstellungen und starten Sie die Instanzen neu, damit die neuen Einstellungen übernommen werden.

>[!NOTE]
>
>Sie können die Rolle einer Instanz jederzeit überprüfen, indem Sie überprüfen, ob die **primary** oder **Standby** Ausführungsmodi in der Sling Settings Web Console.
>
>Wechseln Sie hierfür zu *https://localhost:4502/system/console/status-slingsettings* und überprüfen Sie die Zeile **„Run Modes“**.

## Erstmalige Synchronisation {#first-time-synchronization}

Nachdem die Vorbereitung abgeschlossen und die Standby-Instanz zum ersten Mal gestartet wurde, kommt es zu einem starken Netzwerk-Traffic zwischen den Instanzen, da die Standby-Instanz bis zur primären Instanz aufruft. Sie können die Protokolle konsultieren, um den Status der Synchronisation zu beobachten.

Im Standby *tarmk-coldstandby.log*, können Sie Einträge wie die folgenden sehen:

```xml
    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore trying to read segment ec1f739c-0e3c-41b8-be2e-5417efc05266

    *DEBUG* [nioEventLoopGroup-3-1] org.apache.jackrabbit.oak.segment.standby.codec.SegmentDecoder received type 1 with id ec1f739c-0e3c-41b8-be2e-5417efc05266 and size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore got segment ec1f739c-0e3c-41b8-be2e-5417efc05266 with size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment ec1f739c-0e3c-41b8-be2e-5417efc05266 to /mnt/crx/author/crx-quickstart/repository/segmentstore/data00016a.tar
```

Im Standby *error.log* sollten Sie einen Eintrag wie den folgenden sehen:

```xml
*INFO* [FelixStartLevel] org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService started standby sync with 10.20.30.40:8023 at 5 sec.
```

Im obigen Protokollausschnitt *10 20 30 40* ist die IP-Adresse der primären Instanz.

Im **primary** *tarmk-coldstandby.log*, sehen Sie Einträge wie die folgenden:

```xml
    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver got message 's.d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd' from client c7a7ce9b-1e16-488a-976e-627100ddd8cd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler request segment id d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler sending segment d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd to /10.20.30.40:34998

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver did send segment with 262144 bytes to client c7a7ce9b-1e16-488a-976e-627100ddd8cd
```

In diesem Fall ist der im Protokoll erwähnte &quot;Client&quot;der **Standby** -Instanz.

Sobald diese Einträge nicht mehr im Protokoll angezeigt werden, können Sie sicher davon ausgehen, dass der Synchronisierungsprozess abgeschlossen ist.

Obwohl die obigen Einträge zeigen, dass der Abrufmechanismus ordnungsgemäß funktioniert, ist es häufig hilfreich festzustellen, ob bei Abrufvorgängen Daten synchronisiert werden. Suchen Sie hierzu nach Einträgen wie den folgenden:

```xml
*DEBUG* [defaultEventExecutorGroup-156-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment 3a03fafc-d1f9-4a8f-a67a-d0849d5a36d5 to /<<CQROOTDIRECTORY>>/crx-quickstart/repository/segmentstore/data00014a.tar
```

Außerdem bei Ausführung mit einer nicht freigegebenen `FileDataStore`, Meldungen wie die folgende bestätigen, dass die Binärdateien ordnungsgemäß übertragen werden:

```xml
*DEBUG* [nioEventLoopGroup-228-1] org.apache.jackrabbit.oak.segment.standby.codec.ReplyDecoder received blob with id eb26faeaca7f6f5b636f0ececc592f1fd97ea1a9#169102 and size 169102
```

### Konfiguration {#configuration}

Die folgenden OSGi-Einstellungen sind für den Cold Standby-Dienst verfügbar:

* **Persist-Konfiguration:** Wenn diese Option aktiviert ist, wird die Konfiguration im Repository statt der herkömmlichen OSGi-Konfigurationsdateien gespeichert. Adobe empfiehlt, diese Einstellung auf Produktionssystemen deaktiviert zu lassen, damit die primäre Konfiguration nicht von der Standby-Instanz abgerufen wird.

* **Modus (`mode`):** Dadurch wird der Ausführungsmodus der Instanz ausgewählt.

* **Port (port):** Der für die Kommunikation zu verwendende Port. Der Standardwert lautet `8023`.

* **Primärer Host (`primary.host`):** Der Host der primären Instanz. Diese Einstellung gilt nur für die Standby-Instanz.
* **Synchronisierungsintervall (`interval`):** Diese Einstellung bestimmt das Zeitintervall zwischen Synchronisierungsanfragen und gilt nur für die Standby-Instanz.

* **Zulässige IP-Bereiche (`primary.allowed-client-ip-ranges`):** - die IP-Bereiche, aus denen die primäre Instanz Verbindungen zulässt.
* **Sicher (`secure`):** Diese Einstellung dient zum Aktivieren der SSL-Verschlüsselung. Um diese Einstellung verwenden zu können, muss sie auf allen Instanzen aktiviert sein.
* **Lese-Timeout für Standby-Instanz (`standby.readtimeout`):** Der Timeout-Wert in Millisekunden für von der Standby-Instanz ausgegebene Anfragen. Der Standardwert ist 60000 (eine Minute).

* **Automatische Bereinigung der Standby-Instanz (`standby.autoclean`):** Ruft die Bereinigungsmethode auf, wenn die Größe des Speichers in einem Synchronisierungszyklus ansteigt.

>[!NOTE]
>
>Adobe empfiehlt, dass die primäre Instanz und die Standby-Instanz unterschiedliche Repository-IDs aufweisen, damit sie für Dienste wie die Abladung getrennt identifiziert werden können.
>
>Die beste Möglichkeit, dies zu gewährleisten, besteht darin, *sling.id* auf der Standby-Instanz angezeigt und starten Sie die Instanz neu.

## Failover-Verfahren {#failover-procedures}

Falls die primäre Instanz aus irgendeinem Grund fehlschlägt, können Sie eine der Standby-Instanzen so einrichten, dass sie die Rolle der primären Instanz übernimmt, indem Sie den Start-Ausführungsmodus wie unten beschrieben ändern:

>[!NOTE]
>
>Bearbeiten Sie die Konfigurationsdateien so, dass sie mit den für die primäre Instanz verwendeten Einstellungen übereinstimmen.

1. Navigieren Sie zum Speicherort der installierten Standby-Instanz und beenden Sie sie.

1. Wenn Sie bei der Einrichtung einen Lastenausgleich konfiguriert haben, können Sie jetzt die primäre Instanz aus der Konfiguration des Lastenausgleichs entfernen.
1. Sichern Sie die `crx-quickstart` Ordner aus dem Installationsordner von Standby. Sie kann als Basis für die Konfiguration einer neuen Standby-Instanz verwendet werden.

1. Starten Sie die Instanz mit dem `primary` Ausführungsmodus:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Fügen Sie die neue primäre Instanz zum Lastenausgleich hinzu.
1. Erstellen und starten Sie eine neue Standby-Instanz. Weitere Informationen finden Sie im oben beschriebenen Verfahren [Erstellen einer TarMK-Cold-Standby-Konfiguration für AEM](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup).

## Anwenden von Hotfixes auf ein Cold Standby-Setup {#applying-hotfixes-to-a-cold-standby-setup}

Die empfohlene Methode zum Anwenden von Hotfixes auf ein Cold-Standby-Setup besteht darin, sie auf der primären Instanz zu installieren und sie dann in einer neuen Cold-Standby-Instanz mit installierten Hotfixes zu klonen.

Gehen Sie dazu wie folgt vor:

1. Beenden Sie den Synchronisierungsvorgang auf der Cold-Standby-Instanz. Wechseln Sie dazu zur JMX-Konsole und verwenden Sie das Bean **org.apache.jackrabbit.oak: Status (&quot;Standby&quot;)**. Weitere Informationen finden Sie im Abschnitt [Monitoring](#monitoring).
1. Beenden Sie die Cold-Standby-Instanz.
1. Installieren Sie den Hotfix auf der primären Instanz. Weitere Einzelheiten zum Installieren eines Hotfixes finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).
1. Testen Sie die Instanz nach der Installation auf mögliche Probleme.
1. Entfernen Sie die Cold-Standby-Instanz, indem Sie den Installationsordner löschen.
1. Beenden Sie die primäre Instanz und klonen Sie sie, indem Sie eine Dateisystemkopie des gesamten Installationsordners an den Speicherort der Cold-Standby-Instanz erstellen.
1. Konfigurieren Sie den neu erstellten Klon so, dass er als Cold-Standby-Instanz fungiert. Siehe [Erstellen eines AEM TarMK Cold Standby-Setups.](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup)
1. Starten Sie sowohl die primäre Instanz als auch die Cold-Standby-Instanz.

## Monitoring {#monitoring}

Diese Funktion stellt Informationen mithilfe von JMX oder MBeans bereit. Auf diese Weise können Sie den aktuellen Status der Standby- und Master-Instanz mithilfe der [JMX-Konsole](/help/sites-administering/jmx-console.md). Die entsprechenden Informationen sind in einem MBean vom Typ `type org.apache.jackrabbit.oak:type="Standby"` namens `Status` enthalten.

**Standby**

Unter Beobachtung einer Standby-Instanz stellen Sie einen Knoten bereit. Die ID ist normalerweise eine generische UUID.

Dieser Knoten verfügt über fünf schreibgeschützte Attribute:

* `Running:` Ein boolescher Wert, der angibt, ob der Synchronisierungsvorgang ausgeführt wird oder nicht.

* `Mode:` Client: gefolgt von der UUID, die die Instanz identifiziert. Diese UUID ändert sich jedes Mal, wenn die Konfiguration aktualisiert wird.

* `Status:` Der aktuelle Status in Textform (z. B. `running` oder `stopped`).

* `FailedRequests:` Die Anzahl aufeinanderfolgender Fehler.
* `SecondsSinceLastSuccess:` Anzahl der Sekunden seit der letzten erfolgreichen Kommunikation mit dem Server. Es wird angezeigt `-1` wenn keine erfolgreiche Kommunikation stattgefunden hat.

Darüber hinaus gibt es drei aufrufbare Methoden:

* `start():` Startet den Synchronisierungsvorgang.
* `stop():` Beendet den Synchronisierungsvorgang.
* `cleanup():` Führt den Bereinigungsvorgang auf der Standby-Instanz durch.

**Primäre Instanz**

Die Beobachtung der primären Instanz zeigt einige allgemeine Informationen über ein MBean an, dessen ID-Wert die Portnummer ist, die der TarMK-Standby-Dienst verwendet (standardmäßig 8023). Die meisten Methoden und Attribute sind mit denen der Standby-Instanz identisch, einige unterscheiden sich jedoch:

* `Mode:` zeigt immer den Wert an `primary`.

Darüber hinaus können Informationen für bis zu zehn Clients (Standby-Instanzen) abgerufen werden, die mit dem Master verbunden sind. Die MBean-ID ist die UUID der Instanz. Es gibt keine aufrufbaren Methoden für diese MBeans, aber einige nützliche schreibgeschützte Attribute:

* `Name:` Dies ist die ID des Clients.
* `LastSeenTimestamp:` Der Zeitstempel der letzten Anforderungen in Textform.
* `LastRequest:` Die letzte Anforderung des Clients.
* `RemoteAddress:` Die IP-Adresse des Clients.
* `RemotePort:` Der vom Client für die letzte Anforderung verwendete Port.
* `TransferredSegments:` Die Gesamtanzahl der an diesen Client übertragenen Segmente.
* `TransferredSegmentBytes:`Die Gesamtzahl der an diesen Client übertragenen Byte.

## Wartung des Cold-Standby-Repositorys {#cold-standby-repository-maintenance}

### Revisionsbereinigung {#revision-clean}

>[!NOTE]
>
>Wenn Sie auf der primären Instanz die [Online-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md) ausführen, ist das im Folgenden vorgestellte manuelle Verfahren nicht erforderlich. Wenn Sie die Online-Revisionsbereinigung verwenden, wird die `cleanup ()` -Vorgang auf der Standby-Instanz wird automatisch ausgeführt.

>[!NOTE]
>
>Führen Sie auf der Standby-Instanz keine Offline-Revisionsbereinigung aus. Sie ist nicht erforderlich und reduziert nicht die Größe des Segmentspeichers.

Adobe empfiehlt eine regelmäßige Wartung, um ein übermäßiges Repository-Wachstum im Laufe der Zeit zu vermeiden. Gehen Sie wie folgt vor, um die Wartung des Cold-Standby-Repositorys manuell durchzuführen:

1. Beenden Sie den Standby-Prozess auf der Standby-Instanz. Wechseln Sie dazu zur JMX-Konsole und verwenden Sie das Bean **org.apache.jackrabbit.oak: Status (&quot;Standby&quot;)**. Weitere Informationen finden Sie im obigen Abschnitt zum [Monitoring](/help/sites-deploying/tarmk-cold-standby.md#monitoring).

1. Beenden Sie die primäre AEM.
1. Führen Sie das Oak-Komprimierungs-Tool auf der primären Instanz aus. Weitere Informationen finden Sie unter [Wartung des Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
1. Starten Sie die primäre Instanz.
1. Starten Sie den Standby-Prozess auf der Standby-Instanz mit demselben JMX-Bean, wie im ersten Schritt beschrieben.
1. Überwachen Sie die Protokolle und warten Sie, bis die Synchronisierung abgeschlossen ist. Es ist möglich, dass im Standby-Repository derzeit ein beträchtliches Wachstum zu verzeichnen ist.
1. Führen Sie auf der Standby-Instanz den `cleanup()`-Vorgang aus. Verwenden Sie dazu dasselbe JMX-Bean wie im ersten Schritt beschrieben.

Es kann länger als üblich dauern, bis die Synchronisierung der Standby-Instanz mit der primären Instanz abgeschlossen ist, da bei der Offline-Komprimierung der Repository-Verlauf neu geschrieben wird und die Berechnung von Änderungen in den Repositorys deshalb länger dauert. Nach Abschluss dieses Prozesses ist die Größe des Repositorys auf der Standby-Instanz ungefähr genauso groß wie das Repository auf der primären Instanz.

Alternativ kann das primäre Repository nach der Komprimierung auf der primären Instanz manuell in die Standby-Instanz kopiert werden, wodurch die Standby-Instanz bei jeder Ausführung der Komprimierung neu erstellt wird.

### Datenspeicherbereinigung {#data-store-garbage-collection}

Es ist wichtig, von Zeit zu Zeit die Speicherbereinigung in Dateidatenspeicher-Instanzen auszuführen, da andernfalls gelöschte Binärdateien im Dateisystem verbleiben und schließlich das Laufwerk füllen. Gehen Sie wie folgt vor, um eine Speicherbereinigung durchzuführen:

1. Führen Sie eine Wartung für das Repository der Cold-Standby-Instanz durch, wie im [obigen](/help/sites-deploying/tarmk-cold-standby.md#cold-standby-repository-maintenance) Abschnitt beschrieben.
1. Nach Abschluss des Wartungsvorgangs und Neustart der Instanzen:

   * Führen Sie auf der primären Instanz die automatische Datenspeicherbereinigung über das relevante JMX-Bean aus, wie unter [diesem Artikel](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-jmx-console).
   * Auf der Standby-Instanz ist die automatische Datenspeicherbereinigung nur über die **BlobGarbageCollection** MBean - `startBlobGC()`. Die **RepositoryManagement** MBean ist nicht auf der Standby-Instanz verfügbar.

   >[!NOTE]
   >
   >Wenn Sie keinen freigegebenen Datenspeicher verwenden, führen Sie die Speicherbereinigung zuerst auf der primären und dann auf der Standby-Instanz aus.
