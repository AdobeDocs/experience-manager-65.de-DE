---
title: Ausführen von AEM mit der TarMK-Cold-Standby-Funktion
description: Erfahren Sie, wie Sie ein TarMK-Cold-Standby-Setup erstellen, konfigurieren und verwalten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
feature: Configuring
exl-id: dadde3ee-d60c-4b87-9af0-a12697148161
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2666'
ht-degree: 100%

---

# Ausführen von AEM mit der TarMK-Cold-Standby-Funktion{#how-to-run-aem-with-tarmk-cold-standby}

## Einführung {#introduction}

Durch die Cold-Standby-Kapazität des Tar-Mikro-Kernels können eine oder mehrere Standby-Instanzen von Adobe Experience Manager (AEM) eine Verbindung mit einer primären Instanz herstellen. Die Synchronisierung ist dabei unidirektional, d. h. sie verläuft nur von der primären zur Standby-Instanz.

Die Standby-Instanz dient dazu, sicherzustellen, dass eine Live-Datenkopie des primären Repositorys vorhanden ist und ein schneller Wechsel ohne Datenverluste durchgeführt wird, wenn das primäre Repository aus irgendeinem Grund nicht verfügbar ist.

Inhalte werden linear zwischen der primären Instanz und den Standby-Instanzen synchronisiert. Dabei werden keine Integritätsprüfungen auf mögliche Datei- oder Repository-Beschädigungen durchgeführt. Aufgrund dieser Konfiguration sind die Standby-Instanzen exakte Kopien der primären Instanz. Sie können nicht dazu beitragen, Inkonsistenzen auf primären Instanzen zu verhindern.

>[!NOTE]
>
>Die Cold-Standby-Funktion ist für Szenarien bestimmt, in denen eine hohe Verfügbarkeit für **Autoreninstanzen** erforderlich ist. In Situationen, in den eine hohe Verfügbarkeit für **Veröffentlichungsinstanzen** unter Verwendung des Tar-Mikro-Kernels erforderlich ist, empfiehlt Adobe den Einsatz einer Veröffentlichungsfarm.
>
>Weitere Informationen zu verfügbaren Bereitstellungen finden Sie auf der Seite [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md). 

>[!NOTE]
>
>Wenn die Standby-Instanz eingerichtet oder vom primären Knoten abgeleitet ist, ermöglicht sie nur den Zugriff auf die folgende Konsole (für administrative Aktivitäten):
>
>* OSGI-Web-Konsole
>
>Andere Konsolen sind nicht verfügbar.

## Funktionsweise {#how-it-works}

Auf der primären AEM-Instanz ist ein TCP-Port geöffnet, der eingehende Nachrichten überwacht. Derzeit senden die sekundären Instanzen zwei Arten von Nachrichten an die primäre Instanz:

* Eine Nachricht, die die Segmentkennung des aktuellen Heads anfordert.
* Eine Nachricht, die Segmentdaten mit einer angegebenen ID anfordert.

Die Standby-Instanz fordert regelmäßig die Segment-ID des aktuellen Heads der primären Instanz an. Wenn das Segment ein lokal unbekanntes Segment ist, wird es abgerufen. Ist es bereits vorhanden, werden die Segmente verglichen und referenzierte Segmente werden bei Bedarf ebenfalls angefordert.

>[!NOTE]
>
>Standby-Instanzen empfangen keine Anfragen, da sie nur im Synchronisierungsmodus ausgeführt werden. Der einzige auf einer Standby-Instanz verfügbare Bereich ist die Web-Konsole, um die Konfiguration von Bundles und Diensten zu vereinfachen.

Eine typische TarMK-Cold-Standby-Bereitstellung: 

![chlimage_1](assets/chlimage_1.png)

## Weitere Merkmale {#other-characteristics}

### Stabilität {#robustness}

Der Datenfluss soll Verbindungs- und Netzwerkprobleme automatisch erkennen und beheben. Alle Pakete sind mit Prüfsummen gebündelt, und sobald Verbindungsprobleme oder beschädigte Pakete auftreten, werden Wiederholungsmechanismen ausgelöst.

#### Leistung {#performance}

Die Aktivierung der TarMK-Cold-Standby-Funktion auf der primären Instanz hat fast keine messbaren Auswirkungen auf die Leistung. Der zusätzliche CPU-Verbrauch ist gering, und die zusätzliche Festplatte bzw. die zusätzliche Netzwerk-E/A dürfte keine Leistungsprobleme verursachen.

Auf der Standby-Instanz muss während des Synchronisierungsvorgangs mit einer hohen CPU-Nutzung gerechnet werden. Da es sich nicht um einen Multithread-Prozess handelt, kann dieser nicht durch mehrere Kerne beschleunigt werden. Werden keine Daten geändert oder übertragen, tritt keine messbare Aktivität auf. Die Verbindungsgeschwindigkeit variiert je nach Hardware und Netzwerkumgebung. Sie hängt jedoch nicht von der Größe des Repositorys oder der SSL-Nutzung ab. Dies sollte berücksichtigt werden, wenn die erforderliche Zeit für die Erstsynchronisierung geschätzt wird oder wenn zwischenzeitlich auf dem primären Knoten eine große Menge von Daten geändert wurde.

#### Sicherheit {#security}

Wird davon ausgegangen, dass alle Instanzen, in derselben Intranet-Sicherheitszone ausgeführt werden, ist die Gefahr einer Sicherheitsverletzung deutlich geringer. Sie können trotzdem eine zusätzliche Sicherheitsebene hinzufügen, indem Sie SSL-Verbindungen zwischen den sekundären Instanzen und der primären Instanz aktivieren. So wird die Wahrscheinlichkeit reduziert, dass Daten durch einen Man-in-the-Middle-Angriff kompromittiert werden.

Darüber hinaus können Sie festlegen, welche Standby-Instanzen eine Verbindung herstellen dürfen, indem Sie die IP-Adressen eingehender Anforderungen beschränken. Damit dürfte sichergestellt sein, dass niemand im Intranet das Repository kopieren kann.

>[!NOTE]
>
>Es wird empfohlen, einen Lastenausgleich zwischen dem Dispatcher und den Servern hinzuzufügen, die Teil der Cold-Standby-Konfiguration bilden. Der Lastenausgleich sollte so konfiguriert werden, dass der Benutzer-Traffic nur zur **primären**-Instanz geleitet wird. Dies ist erforderlich, um Konsistenz zu gewährleisten und zu verhindern, dass Inhalte auf der Standby-Instanz mit anderen Mitteln als dem Cold-Standby-Mechanismus kopiert werden.

## Erstellen einer TarMK-Cold-Standby-Konfiguration für AEM {#creating-an-aem-tarmk-cold-standby-setup}

>[!CAUTION]
>
>Die PID für den Segment-Knotenspeicher und den Standby-Speicherdienst wurde in AEM 6.3 im Vergleich zu den vorherigen Versionen wie folgt geändert:
>
>* von org.apache.jackrabbit.oak.**plugins**.segment.standby.store.StandbyStoreService für org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService
>* von org.apache.jackrabbit.oak.**plugins**.segment.SegmentNodeStoreService für org.apache.jackrabbit.oak.segment.SegmentNodeStoreService
>
>Nehmen Sie die erforderlichen Konfigurationsanpassungen vor, um dieser Änderung Rechnung zu tragen.

Um eine TarMK-Cold-Standby-Konfiguration zu erstellen, müssen Sie zuerst die Standby-Instanzen erstellen. Erstellen Sie hierzu an einem neuen Speicherort eine Dateisystemkopie des gesamten Installationsordners der primären Instanz. Anschließend können Sie jede Instanz mit einem Ausführungsmodus starten, der die Rolle der Instanz angibt (`primary` oder `standby`).

Nachfolgend sind die erforderlichen Schritte zum Erstellen einer Konfiguration mit einer primären und einer sekundären Instanz beschrieben:

1. Installieren Sie AEM.

1. Beenden Sie die Instanz und kopieren Sie deren Installationsordner an den Speicherort, von dem aus die Cold-Standby-Instanz ausgeführt werden soll. Selbst wenn sie auf unterschiedlichen Rechnern ausgeführt wird, müssen Sie jedem Ordner einen beschreibenden Namen zuweisen (z. B. *aem-primary* oder *aem-standby*), um zwischen den Instanzen zu unterscheiden.
1. Navigieren Sie zum Installationsordner der primären Instanz und führen Sie folgende Schritte aus:

   1. Prüfen Sie, ob unter `aem-primary/crx-quickstart/install` möglicherweise vorherige OSGi-Konfigurationen vorhanden sind, und löschen Sie diese.

   1. Erstellen Sie unter `install.primary` einen Ordner namens `aem-primary/crx-quickstart/install`.

   1. Erstellen Sie unter `aem-primary/crx-quickstart/install/install.primary` die erforderlichen Konfigurationen für den bevorzugten Knotenspeicher und Datenspeicher.
   1. Erstellen Sie im selben Verzeichnis die Datei `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config` und konfigurieren Sie sie entsprechend. Weitere Informationen zu den Konfigurationsoptionen finden Sie unter [Konfiguration](/help/sites-deploying/tarmk-cold-standby.md#configuration).

   1. Wenn Sie eine AEM-TarMK-Instanz mit einem externen Datenspeicher verwenden, erstellen Sie unter `aem-primary/crx-quickstart/install` den Ordner `crx3` namens `crx3`.

   1. Speichern Sie die Konfigurationsdatei für den Datenspeicher im Ordner `crx3`.

   Wenn Sie beispielsweise eine AEM-TarMK-Instanz mit einer externen Datenspeicherdatei ausführen, benötigen Sie die folgenden Konfigurationsdateien:

   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
   * `aem-primary/crx-quickstart/install/install.primary/org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`
   * `aem-primary/crx-quickstart/install/crx3/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`

   Nachfolgend finden Sie Beispielkonfigurationen für die primäre Instanz:

   **Beispiel für** **org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config**

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

1. Starten Sie die primäre Instanz und stellen Sie dabei sicher, dass Sie den primären Ausführungsmodus festlegen:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Erstellen Sie einen neuen Apache Sling Logging Logger für das Paket **org.apache.jackrabbit.oak.segment**. Setzen Sie die Protokollstufe auf „Debugging“ und legen Sie fest, dass die Protokollausgabe in einer separaten Datei gespeichert wird, z. B. */logs/tarmk-coldstandby.log*.  Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md).
1. Navigieren Sie zum Speicherort der **Standby**-Instanz und starten Sie sie, indem Sie die JAR-Datei ausführen.
1. Erstellen Sie dieselbe Protokollierungskonfiguration wie für die primäre Instanz. Beenden Sie anschließend die Instanz.
1. Bereiten Sie dann die Standby-Instanz vor. Hierzu können Sie dieselben Schritte wie für die primäre Instanz ausführen:

   1. Löschen Sie alle Dateien, die möglicherweise unter `aem-standby/crx-quickstart/install` gespeichert sind.
   1. Erstellen Sie unter `install.standby` den Ordner `aem-standby/crx-quickstart/install`.

   1. Erstellen Sie zwei Konfigurationsdateien mit den folgenden Namen:

      * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`
      * `org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService.config`

   1. Erstellen Sie unter `crx3` einen Ordner namens `aem-standby/crx-quickstart/install`.

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

1. Starten Sie die **Standby**-Instanz im Standby-Ausführungsmodus:

   ```xml
   java -jar quickstart.jar -r standby,crx3,crx3tar
   ```

Der Dienst kann auch über die Web-Konsole konfiguriert werden. Führen Sie hierzu folgende Schritte aus:

1. Wechseln Sie zur Web-Konsole unter: *https://Server-Adresse:Serverport/system/console/configMgr*.
1. Suchen Sie nach einem Dienst mit dem Namen **Apache Jackrabbit Oak Segment Tar Cold Standby Service** und doppelklicken Sie darauf, um die Einstellungen zu bearbeiten.
1. Speichern Sie die Einstellungen und starten Sie die Instanzen neu, damit die neuen Einstellungen übernommen werden.

>[!NOTE]
>
>Sie können die Rolle einer Instanz jederzeit überprüfen, indem Sie in der Web-Konsole für die Sling-Einstellungen prüfen, ob die Ausführungsmodi **primär** oder **Standby** vorhanden sind.
>
>Wechseln Sie hierfür zu *https://localhost:4502/system/console/status-slingsettings* und überprüfen Sie die Zeile **„Run Modes“**.

## Erstsynchronisierung {#first-time-synchronization}

Wenn die Vorbereitung abgeschlossen ist und die Standby-Instanz zum ersten Mal gestartet wird, tritt erhöhter Netzwerk-Traffic zwischen den Instanzen auf, da die Standby-Instanzen mit der primären Instanz synchronisiert werden. Anhand der Protokolle können Sie den Status der Synchronisierung überprüfen.

Im Protokoll *tarmk-coldstandby.log* der Standby-Instanz werden dabei Einträge wie die folgenden angezeigt:

```xml
    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore trying to read segment ec1f739c-0e3c-41b8-be2e-5417efc05266

    *DEBUG* [nioEventLoopGroup-3-1] org.apache.jackrabbit.oak.segment.standby.codec.SegmentDecoder received type 1 with id ec1f739c-0e3c-41b8-be2e-5417efc05266 and size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.standby.store.StandbyStore got segment ec1f739c-0e3c-41b8-be2e-5417efc05266 with size 262144

    *DEBUG* [defaultEventExecutorGroup-2-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment ec1f739c-0e3c-41b8-be2e-5417efc05266 to /mnt/crx/author/crx-quickstart/repository/segmentstore/data00016a.tar
```

Im Protokoll *error.log* der Standby-Instanz wird folgender Eintrag angezeigt:

```xml
*INFO* [FelixStartLevel] org.apache.jackrabbit.oak.segment.standby.store.StandbyStoreService started standby sync with 10.20.30.40:8023 at 5 sec.
```

Im obigen Protokollausschnitt ist *10.20.30.40* die IP-Adresse der primären Instanz.

Im Protokoll *tarmk-coldstandby.log* der **primären** Instanz werden Einträge wie die folgenden angezeigt:

```xml
    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver got message 's.d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd' from client c7a7ce9b-1e16-488a-976e-627100ddd8cd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler request segment id d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.server.StandbyServerHandler sending segment d45f53e4-0c33-4d4d-b3d0-7c552c8e3bbd to /10.20.30.40:34998

    *DEBUG* [nioEventLoopGroup-3-2] org.apache.jackrabbit.oak.segment.standby.store.CommunicationObserver did send segment with 262144 bytes to client c7a7ce9b-1e16-488a-976e-627100ddd8cd
```

In diesem Fall ist der im Protokoll genannte „Client“ die **Standby**-Instanz.

Sobald diese Einträge nicht mehr im Protokoll angezeigt werden, können Sie davon ausgehen, dass der Synchronisierungsvorgang abgeschlossen ist.

Obwohl die obigen Einträge zeigen, dass der Abrufmechanismus ordnungsgemäß funktioniert, ist es häufig hilfreich festzustellen, ob bei Abrufvorgängen Daten synchronisiert werden. Suchen Sie hierzu nach Einträgen wie den folgenden:

```xml
*DEBUG* [defaultEventExecutorGroup-156-1] org.apache.jackrabbit.oak.segment.file.TarWriter Writing segment 3a03fafc-d1f9-4a8f-a67a-d0849d5a36d5 to /<<CQROOTDIRECTORY>>/crx-quickstart/repository/segmentstore/data00014a.tar
```

Außerdem werden bei der Ausführung über einen nicht freigegebenen `FileDataStore` Meldungen wie die folgenden angezeigt, die bestätigen, dass die Binärdateien ordnungsgemäß übertragen werden:

```xml
*DEBUG* [nioEventLoopGroup-228-1] org.apache.jackrabbit.oak.segment.standby.codec.ReplyDecoder received blob with id eb26faeaca7f6f5b636f0ececc592f1fd97ea1a9#169102 and size 169102
```

### Konfiguration {#configuration}

Die folgenden OSGi-Einstellungen sind für den Cold-Standby-Dienst verfügbar:

* **Konfiguration beibehalten:** Bei Aktivierung dieser Option wird die Konfiguration im Repository anstatt wie üblich in den OSGi-Konfigurationsdateien gespeichert. Adobe empfiehlt, diese Einstellung auf Produktionssystemen deaktiviert zu lassen, damit die Konfiguration der primären Instanz nicht von der Standby-Instanz abgerufen wird.

* **Modus (`mode`):** Wählt den Ausführungsmodus der Instanz aus.

* **Port (port):** Der für die Kommunikation zu verwendende Port. Der Standardwert lautet `8023`.

* **Primärer Host (`primary.host`):** Der Host der primären Instanz. Diese Einstellung gilt nur für die Standby-Instanz.
* **Synchronisierungsintervall (`interval`):** Diese Einstellung bestimmt das Zeitintervall zwischen Synchronisierungsanfragen und gilt nur für die Standby-Instanz.

* **Zulässige IP-Bereiche (`primary.allowed-client-ip-ranges`):** Die IP-Bereiche, von denen aus die primäre Instanz Verbindungen zulässt.
* **Sicher (`secure`):** Diese Einstellung dient zum Aktivieren der SSL-Verschlüsselung. Damit diese Einstellung verwendet werden kann, muss sie auf allen Instanzen aktiviert werden.
* **Lese-Timeout für Standby-Instanz (`standby.readtimeout`):** Der Timeout-Wert in Millisekunden für von der Standby-Instanz ausgegebene Anfragen. Der Standardwert ist 60000 (eine Minute).

* **Automatische Bereinigung der Standby-Instanz (`standby.autoclean`):** Ruft die Bereinigungsmethode auf, wenn die Größe des Speichers in einem Synchronisierungszyklus ansteigt.

>[!NOTE]
>
>Adobe empfiehlt, dass die primäre und die Standby-Instanz unterschiedliche Repository-IDs haben, damit sie für Dienste wie Offloading separat identifizierbar sind.
>
>Die beste Möglichkeit, dies sicherzustellen, ist das Löschen der *sling.id* von der Standby-Instanz und das Neustarten der Instanz.

## Failover-Verfahren {#failover-procedures}

Für den Fall, dass die primäre Instanz aus irgendeinem Grund ausfällt, können Sie festlegen, dass eine der Standby-Instanzen die Rolle der primären Instanz übernimmt. Hierzu müssen Sie den Ausführungsmodus für den Start wie nachfolgend beschrieben ändern:

>[!NOTE]
>
>Bearbeiten Sie die Konfigurationsdateien so, dass sie mit den für die primäre Instanz verwendeten Einstellungen übereinstimmen.

1. Navigieren Sie zum Speicherort der installierten Standby-Instanz und beenden Sie sie.

1. Wenn Sie bei der Einrichtung einen Lastenausgleich konfiguriert haben, können Sie jetzt die primäre Instanz aus der Konfiguration des Lastenausgleichs entfernen.
1. Erstellen Sie eine Sicherungskopie des Ordners `crx-quickstart`, der im Installationsordner der Standby-Instanz zu finden ist. Sie kann als Basis für die Konfiguration einer neuen Standby-Instanz verwendet werden.

1. Starten Sie die Instanz über den Ausführungsmodus `primary` neu:

   ```shell
   java -jar quickstart.jar -r primary,crx3,crx3tar
   ```

1. Fügen Sie die neu primäre Instanz zum Lastenausgleich hinzu.
1. Erstellen und starten Sie eine neue Standby-Instanz. Weitere Informationen finden Sie im oben beschriebenen Verfahren [Erstellen einer TarMK-Cold-Standby-Konfiguration für AEM](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup).

## Anwenden von Hotfixes auf ein Cold-Standby-Setup {#applying-hotfixes-to-a-cold-standby-setup}

Die empfohlene Methode zum Anwenden von Hotfixes auf ein Cold-Standby-Setup besteht darin, sie auf der primären Instanz zu installieren und sie dann mit den installierten Hotfixes in eine neue Cold-Standby-Instanz zu klonen.

Führen Sie hierzu die nachfolgend beschriebenen Schritte aus:

1. Beenden Sie den Synchronisierungsvorgang auf der Cold-Standby-Instanz. Wechseln Sie dazu zur JMX-Konsole und verwenden Sie das Bean **org.apache.jackrabbit.oak: Status (&quot;Standby&quot;)**. Weitere Informationen finden Sie im Abschnitt [Monitoring](#monitoring).
1. Beenden Sie die Cold-Standby-Instanz.
1. Installieren Sie den Hotfix auf der primären Instanz. Weitere Einzelheiten zum Installieren eines Hotfixes finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).
1. Testen Sie die Instanz nach der Installation auf mögliche Probleme.
1. Entfernen Sie die Cold-Standby-Instanz, indem Sie ihren Installationsordner löschen.
1. Stoppen Sie die primäre Instanz und klonen Sie sie, indem Sie eine Dateisystemkopie ihres gesamten Installationsordners an den Speicherort der Cold-Standby-Instanz erstellen.
1. Konfigurieren Sie den neu erstellten Klon so, dass er als Cold-Standby-Instanz agiert. Siehe [ Erstellen eines AEM-TarMK-Cold-Standby-Setups](/help/sites-deploying/tarmk-cold-standby.md#creating-an-aem-tarmk-cold-standby-setup).
1. Starten Sie sowohl die primäre als auch die Cold-Standby-Instanz.

## Monitoring {#monitoring}

Diese Funktion stellt Informationen mithilfe von JMX oder MBeans bereit. Auf diese Weise können Sie den aktuellen Status der Standby- und der primären Instanz mit der [JMX-Konsole](/help/sites-administering/jmx-console.md) überprüfen. Die entsprechenden Informationen sind in einem MBean vom Typ `type org.apache.jackrabbit.oak:type="Standby"` namens `Status` enthalten.

**Standby**

Beim Überwachen einer Standby-Instanz wird ein Knoten freigelegt. Die ID ist normalerweise eine generische UUID.

Dieser Knoten verfügt über fünf schreibgeschützte Attribute:

* `Running:` Ein boolescher Wert, der angibt, ob der Synchronisierungsvorgang ausgeführt wird oder nicht.

* `Mode:` Client: gefolgt von der UUID, die die Instanz identifiziert. Diese UUID ändert sich bei jeder Aktualisierung der Konfiguration.

* `Status:` Der aktuelle Status in Textform (z. B. `running` oder `stopped`).

* `FailedRequests:` Die Anzahl aufeinanderfolgender Fehler.
* `SecondsSinceLastSuccess:` Anzahl der Sekunden seit der letzten erfolgreichen Kommunikation mit dem Server. War keine erfolgreiche Kommunikation möglich, wird `-1` angezeigt.

Darüber hinaus gibt es drei aufrufbare Methoden:

* `start():` Startet den Synchronisierungsvorgang.
* `stop():` Beendet den Synchronisierungsvorgang.
* `cleanup():` Führt den Bereinigungsvorgang auf der Standby-Instanz durch.

**Primäre Instanz**

Beim Überwachen der primären Instanz wird eine Reihe allgemeiner Informationen über ein MBean angezeigt, dessen ID-Wert die Port-Nummer ist, die vom TarMK-Standby-Dienst verwendet wird (standardmäßig 8023). Die meisten Methoden und Attribute sind mit denen der Standby-Instanz identisch, einige unterscheiden sich jedoch:

* `Mode:` zeigt immer den Wert `primary` an.

Des Weiteren können Informationen für bis zu 10 Clients (Standby-Instanzen) abgerufen werden, die mit der primären Instanz verbunden sind. Die MBean-ID ist die UUID der Instanz. Für diese MBeans gibt es keine aufrufbaren Methoden, aber einige nützliche schreibgeschützte Attribute:

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
>Wenn Sie auf der primären Instanz die [Online-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md) ausführen, ist das im Folgenden vorgestellte manuelle Verfahren nicht erforderlich. Wenn Sie die Online-Revisionsbereinigung verwenden, wird auf der Standby-Instanz außerdem automatisch der Vorgang `cleanup ()` ausgeführt.

>[!NOTE]
>
>Führen Sie auf der Standby-Instanz keine Offline-Revisionsbereinigung aus. Diese ist nicht erforderlich und die Größe des Segmentspeichers wûrde dadurch nicht reduziert.

Adobe empfiehlt, regelmäßige Wartungen durchzuführen, um zu verhindern, dass das Repository im Laufe der Zeit zu groß wird. Um die Wartung des Cold-Standby-Repositorys manuell durchzuführen, führen Sie die folgenden Schritte aus:

1. Beenden Sie den Standby-Prozess auf der Standby-Instanz. Wechseln Sie dazu zur JMX-Konsole und verwenden Sie das Bean **org.apache.jackrabbit.oak: Status (&quot;Standby&quot;)**. Weitere Informationen finden Sie im obigen Abschnitt zum [Monitoring](/help/sites-deploying/tarmk-cold-standby.md#monitoring).

1. Beenden Sie die primäre AEM-Instanz.
1. Führen Sie das Oak-Komprimierungs-Tool auf der primären Instanz aus. Weitere Informationen finden Sie unter [Wartung des Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository).
1. Starten Sie die primäre Instanz.
1. Starten Sie den Standby-Prozess auf der Standby-Instanz. Verwenden Sie dazu dasselbe JMX-Bean wie im ersten Schritt beschrieben.
1. Überwachen Sie die Protokolle und warten Sie, bis die Synchronisierung abgeschlossen ist. Möglicherweise nimmt die Größe des Standby-Repositorys jetzt erheblich zu.
1. Führen Sie auf der Standby-Instanz den `cleanup()`-Vorgang aus. Verwenden Sie dazu dasselbe JMX-Bean wie im ersten Schritt beschrieben.

Es kann länger als üblich dauern, bis die Synchronisierung der Standby-Instanz mit der primären Instanz abgeschlossen ist, da bei der Offline-Komprimierung der Repository-Verlauf neu geschrieben wird und die Berechnung von Änderungen in den Repositorys deshalb länger dauert. Nach Abschluss dieses Vorgangs hat das Repository auf der Standby-Instanz etwa dieselbe Größe wie das Repository auf der primären Instanz.

Alternativ kann das primäre Repository manuell auf die Standby-Instanz kopiert werden, nachdem die Komprimierung auf der primären Instanz ausgeführt wurde, wodurch die Standby-Instanz im Wesentlichen bei jeder Komprimierungsausführung neu erstellt wird.

### Datenspeicherbereinigung {#data-store-garbage-collection}

Es ist wichtig, hin und wieder eine Speicherbereinigung für die Dateidatenspeicher-Instanzen durchzuführen, da andernfalls gelöschte Binärdateien im Dateisystem bleiben und mit der Zeit den Festplattenspeicherplatz belegen. Gehen Sie wie folgt vor, um eine Speicherbereinigung durchzuführen:

1. Führen Sie eine Wartung für das Repository der Cold-Standby-Instanz durch, wie im [obigen](/help/sites-deploying/tarmk-cold-standby.md#cold-standby-repository-maintenance) Abschnitt beschrieben.
1. Wenn die Wartung abgeschlossen und die Instanzen neu gestartet wurden, führen Sie die folgenden Schritte aus:

   * Führen Sie auf der primären Instanz die Speicherbereinigung für den Datenspeicher aus. Verwenden Sie hierzu das entsprechende JMX-Bean, wie in [diesem Artikel](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-jmx-console) beschrieben.
   * Auf der Standby-Instanz kann die Speicherbereinigung für den Datenspeicher nur über das MBean **BlobGarbageCollection** – `startBlobGC()` – ausgeführt werden. Das MBean **RepositoryManagement** ist auf der Standby-Instanz nicht verfügbar.

   >[!NOTE]
   >
   >Wenn Sie keinen freigegebenen Datenspeicher verwenden, muss die Speicherbereinigung zuerst auf der primären und dann auf der Standby-Instanz ausgeführt werden.
