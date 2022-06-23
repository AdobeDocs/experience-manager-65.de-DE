---
title: Durchführen einer In-Place-Aktualisierung
description: Erfahren Sie, wie Sie ein Upgrade durchführen.
topic-tags: upgrading
feature: Upgrading
exl-id: aef6ef00-993c-4252-b0ad-ddc4917beaf7
source-git-commit: 6d2b7e341dcdedf3c000b9fb0ecd21722bdf2a27
workflow-type: tm+mt
source-wordcount: '1256'
ht-degree: 79%

---

# Durchführen einer In-Place-Aktualisierung{#performing-an-in-place-upgrade}

>[!NOTE]
>
>Auf dieser Seite wird das Aktualisierungsverfahren für AEM 6.5 beschrieben. Wenn Ihre Installation auf einem Anwendungsserver bereitgestellt wird, lesen Sie [Upgrade-Schritte für Anwendungsserverinstallationen](/help/sites-deploying/app-server-upgrade.md).

## Vorbereitung des Upgrades {#pre-upgrade-steps}

Vor der Durchführung eines Upgrades müssen einige Schritte ausgeführt werden. Weitere Informationen erhalten Sie unter [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) sowie [Wartungsmaßnahmen vor dem Upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md). Achten Sie außerdem darauf, dass Ihr System die Anforderungen für die aktuelle Version von AEM erfüllt. Erfahren Sie, wie Sie mit dem Musterdetektor die Komplexität Ihres Upgrades abschätzen können. Weitere Informationen finden Sie auch im Abschnitt „Aktualisierungsumfang und -anforderungen“ unter [Planung der Aktualisierung](/help/sites-deploying/upgrade-planning.md).

<!--Finally, note that the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Voraussetzungen für die Migration {#migration-prerequisites}

* **Mindestanforderung an die Java-Version:** Das Migrationstool funktioniert nur mit Java-Version 7 und höher. Beachten Sie, dass für AEM 6.3 und höher die einzigen unterstützten Versionen JRE 8 von Oracle und JRE 7 und 8 von IBM sind.

* **Aktualisierte Instanz:** Wenn Sie eine Version aktualisieren, die **älter als 5.6 ist**, überprüfen Sie, ob Sie gemäß dem in der Upgradedokumentation für Version 6.0 beschriebenen Verfahren ein Upgrade auf AEM 6.0 durchgeführt haben.

## Vorbereitung der „AEM Quickstart“-JAR-Datei {#prep-quickstart-file}

1. Beenden Sie die Instanz, falls sie gerade ausgeführt wird. 

1. Laden Sie die neue AEM-JAR-Datei herunter und ersetzen Sie damit die alte Datei außerhalb des Ordners `crx-quickstart`. 

1. Entpacken Sie die Quickstart-JAR-Datei, indem Sie Folgendes ausführen:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

## Inhaltsrepositorymigration {#content-repository-migration}

Diese Migration ist nicht erforderlich, wenn Sie eine Aktualisierung von AEM 6.3 durchführen. Für Versionen vor 6.3 bietet Adobe ein Tool, mit dem Sie das Repository in die neue Version von Oak Segment Tar von AEM 6.3 migrieren können. Es befindet sich im Schnellstartpaket und muss für alle Upgrades eingesetzt werden, die TarMK verwenden sollen. Upgrades für Umgebungen, die MongoMK verwenden, erfordern keine Repository-Migration. Weitere Informationen zu den Vorteilen des neuen Segment-Tar-Formats finden Sie unter [FAQ zur Migration zu Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

Die tatsächliche Migration wird mithilfe der standardmäßigen AEM Schnellstart-JAR-Datei durchgeführt, die mit einer neuen `-x crx2oak` -Option, die das crx2oak-Tool ausführt, um die Aktualisierung zu vereinfachen und sie stabiler zu machen.

>[!NOTE]
>
>Wenn Sie die Migration von TarMK-Repository-Inhalten mit der CRX2Oak-Schnellstarterweiterung durchführen, können Sie den Betriebsmodus **samplecontent** entfernen, indem Sie das Folgende zu der Migrations-Befehlszeile hinzufügen:
>
>* `--promote-runmode nosamplecontent`
>


Um den Befehl zu ermitteln, den Sie ausführen sollten, verwenden Sie den folgenden Befehl:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Wo `<<YOUR_PROFILE>>` und `<<ADDITIONAL_FLAGS>>` werden durch das Profil und die Flags ersetzt, die in der folgenden Tabelle aufgeführt sind:

<table>
 <tbody>
  <tr>
   <td><strong>Quell-Repository </strong></td>
   <td><strong>Ziel-Repository </strong></td>
   <td><strong>Profil</strong></td>
   <td><strong>Zusätzliche Flags</strong><br /> </td>
  </tr>
  <tr>
   <td>crx2 oder TarMK mit <code>FileDataStore</code></td>
   <td>TarMK</td>
   <td>segment-fds</td>
   <td>Siehe Abschnitt zur Fehlerbehebung unten</td>
  </tr>
  <tr>
   <td>crx2</td>
   <td>MongoMK</td>
   <td>mongo-from-crx2 </td>
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td>
  </tr>
  <tr>
   <td>TarMK oder crx2 mit <code>S3DataStore</code></td>
   <td>TarMK</td>
   <td>segment-custom-ds</td>
   <td>Siehe Abschnitt zur Fehlerbehebung unten</td>
  </tr>
  <tr>
   <td>TarMK ohne Datenspeicher</td>
   <td>TarMK</td>
   <td>segment-no-ds</td>
   <td> </td>
  </tr>
  <tr>
   <td>MongoMK</td>
   <td>MongoMK</td>
   <td>Keine Migration erforderlich</td>
   <td> </td>
  </tr>
 </tbody>
</table>

**Dabei gilt:**

* `mongo-host` die IP-Adresse des MongoDB-Servers ist (z. B. 127.0.0.1)

* `mongo-port` ist der MongoDB-Server-Port (z. B.: 27017)

* `mongo-database-name` steht für den Namen der Datenbank (z. B.: aem-author)

**Möglicherweise benötigen Sie auch zusätzliche Schalter für folgende Szenarien:** 

* Wenn Sie die Aktualisierung auf einem Windows-System durchführen, bei dem die Java-Speicherzuordnung nicht ordnungsgemäß durchgeführt wird, fügen Sie die `--disable-mmap` -Parameter auf den -Befehl.

* Wenn Sie Java 7 verwenden, fügen Sie die `-XX:MaxPermSize=2048m` Parameter direkt nach dem `-Xmx` Parameter.

Weitere Informationen über die Verwendung des crx2oak-Tools finden Sie unter „Verwenden des [CRX2Oak Migration Tools](/help/sites-deploying/using-crx2oak.md). crx2oak helper JAR kann bei Bedarf manuell aktualisiert werden, indem die Datei manuell durch neuere Versionen ersetzt wird, nachdem die Schnellstart-Datei entpackt wurde. Sie finden die Datei im AEM-Installationsordner unter: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. Die neueste Version des CRX2Oak-Migrationstools kann aus dem Adoben-Repository heruntergeladen werden unter: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

Wenn die Migration erfolgreich abgeschlossen wurde, wird das Tool mit einem Exit Code von null beendet. Beachten Sie zusätzlich etwaige WARN- und ERROR-Meldungen in der Datei `upgrade.log` im AEM-Installationsverzeichnis unter `crx-quickstart/logs`. Diese Meldungen führen Fehler auf, die nicht schwerwiegend sind und bei der Migration auftraten.

Überprüfen Sie die Konfigurationsdateien unter `crx-quickstart/install` Ordner. Wenn eine Migration erforderlich war, werden diese auf das Ziel-Repository aktualisiert.

**Ein Hinweis zu Datenspeichern:** 

`FileDataStore` ist der neue Standard für Installationen von AEM 6.3 und es ist kein externer Datenspeicher erforderlich. Während ein externer Datenspeicher für Produktionsbereitstellungen empfohlen wird, ist er bei Upgrades nicht Voraussetzung. Aufgrund der gegebenen Komplexität beim Upgrade von AEM empfehlen wir, das Upgrade ohne Datenspeicher-Migration durchzuführen. Falls erwünscht, kann danach eine separate Datenspeicher-Migration ausgeführt werden.

## Problembehebung bei der Migration {#troubleshooting-migration-issues}

Überspringen Sie diesen Abschnitt, wenn Sie von 6.3 aktualisieren. Die bereitgestellten crx2oak-Profile erfüllen die Anforderungen der meisten Kunden. In einigen Fällen sind jedoch zusätzliche Parameter erforderlich. Wenn während der Migration ein Fehler auftritt, sind für manche Aspekte Ihrer Umgebung möglicherweise zusätzliche Konfigurationsoptionen nötig. In diesem Fall tritt wahrscheinlich folgender Fehler auf:

**Checkpoints werden nicht kopiert, da kein externer Datenspeicher spezifiziert wurde. Dadurch wird das gesamte Repository beim ersten Start neu indiziert. Verwenden Sie „Checkpoints überspringen“, um die Migration zu erzwingen, oder lesen Sie https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration für weitere Informationen.** 

Während des Migrationsprozesses muss auf Binärdateien im Datenspeicher zugegriffen werden, was misslingt. Um Ihre Datenspeicherkonfiguration festzulegen, fügen Sie die folgenden Flags in die `<<ADDITIONAL_FLAGS>>` Abschnitt Ihres Migrationsbefehls:

**Für S3-Datenspeicher:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Wo `/path/to/SharedS3DataStore.config` den Pfad zu Ihrer S3-Datenspeicher-Konfigurationsdatei darstellt und `/path/to/datastore` stellt den Pfad zu Ihrem S3-Datenspeicher dar.

**Für Datei-Datenspeicher:**

```shell
--src-datastore=/path/to/datastore
```

Wo `/path/to/datastore` stellt den Pfad zum Dateidatenspeicher dar.

## Durchführen der Aktualisierung {#performing-the-upgrade}

**Wenn S3 verwendet wird:**

1. Entfernen Sie etwaige JARs unter `crx-quickstart/install`, die mit einer früheren Version des S3 Connectors verknüpft sind.

1. Laden Sie die neueste Version des S3-Connectors 1.10.x von herunter. [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/)

1. Extrahieren Sie das Paket in einen temporären Ordner und kopieren Sie den Inhalt von `jcr_root/libs/system/install` der `crx-quickstart/install` Ordner.

### Bestimmen des korrekten Befehls zum Starten des Upgrades {#determining-the-correct-upgrade-start-command}

Um das Upgrade durchzuführen, muss AEM mithilfe der JAR-Datei gestartet werden, um die Instanz zu öffnen. Informationen zur Aktualisierung auf 6.5 finden Sie auch unter anderen Optionen zur Inhaltsumstrukturierung und -migration unter [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md) die Sie mit dem Upgrade-Befehl auswählen können.

>[!IMPORTANT]
>
>Wenn Sie Oracle Java 11 ausführen (oder generell Java-Versionen aktueller als 8), werden zusätzliche Parameter zu Ihrer Befehlszeile hinzugefügt, sobald AEM gestartet wird. Weitere Informationen finden Sie unter [Überlegungen zu Java 11](/help/sites-deploying/custom-standalone-install.md#java-considerations).

Beachten Sie, dass beim Starten von AEM mit dem Start-Skript das Upgrade nicht gestartet wird. Die meisten Kunden starten AEM mithilfe des Start-Skripts und haben dieses Start-Skript so angepasst, dass Schalter für Umgebungskonfigurationen wie Speichereinstellungen, Sicherheitszertifikate usw. eingeschlossen sind. Aus diesem Grund empfehlen wir, dieser Anleitung zu folgen, um den korrekten Upgrade-Befehl zu bestimmen:

1. Führen Sie in einer aktiven AEM-Instanz Folgendes in der Befehlszeile aus: 

   ```shell
   ps -ef | grep java
   ```

1. Suchen Sie nach dem AEM-Prozess. Sie sieht ungefähr so aus:

   ```shell
   /usr/bin/java -server -Xmx1024m -XX:MaxPermSize=256M -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.2.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Passen Sie den Befehl an, indem Sie den Pfad zur vorhandenen JAR-Datei (in diesem Fall `crx-quickstart/app/aem-quickstart*.jar`) mit der neuen JAR ersetzen, welche dem Ordner `crx-quickstart` gleichgeordnet ist. Wenn wir unseren vorherigen Befehl als Beispiel heranziehen, würde unser Befehl folgendermaßen lauten:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar cq-quickstart-6.5.0.jar -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Dadurch wird sichergestellt, dass alle nötigen Speichereinstellungen, benutzerdefinierten Ausführungsmodi und andere Umgebungsparameter auf das Upgrade angewendet werden. Nach Abschluss des Upgrades kann die Instanz in Zukunft mit dem Start-Skript gestartet werden.

## Bereitstellen der aktualisierten Codebasis {#deploy-upgraded-codebase}

Nachdem der Upgrade-Prozess abgeschlossen ist, sollte die aktualisierte Codebasis bereitgestellt werden. Informationen zur Aktualisierung der Codebasis, sodass sie in der Zielversion von AEM funktioniert, finden Sie auf der Seite [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

## Überprüfungen und Fehlerbehebungen nach dem Upgrade {#perform-post-upgrade-check-troubleshooting}

Weitere Informationen finden Sie unter [Überprüfungen und Fehlerbehebungen nach dem Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
