---
title: Durchführen einer ersetzenden Aktualisierung
description: Erfahren Sie, wie Sie eine ersetzende Aktualisierung für AEM 6.5 durchführen.
topic-tags: upgrading
feature: Upgrading
exl-id: aef6ef00-993c-4252-b0ad-ddc4917beaf7
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 100%

---

# Durchführen einer ersetzenden Aktualisierung{#performing-an-in-place-upgrade}

>[!NOTE]
>
>Auf dieser Seite wird das Aktualisierungsverfahren für AEM 6.5 beschrieben. Wenn Ihre Installation auf einem Anwendungs-Server bereitgestellt wird, lesen Sie [Aktualisierungsschritte für Anwendungs-Server-Installationen](/help/sites-deploying/app-server-upgrade.md).

## Schritte vor der Aktualisierung {#pre-upgrade-steps}

Bevor Sie die Aktualisierung durchführen, müssen Sie einige Schritte ausführen. Weitere Informationen finden Sie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) und [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md). Stellen Sie außerdem sicher, dass Ihr System die Anforderungen für die neue AEM-Version erfüllt. Erfahren Sie, wie Sie mithilfe der Mustererkennung die Komplexität Ihres Updates abschätzen können, und lesen Sie auch den Abschnitt „Aktualisierungsumfang und -anforderungen“ unter [Planung der Aktualisierung](/help/sites-deploying/upgrade-planning.md).

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migrationsvoraussetzungen {#migration-prerequisites}

* **Erforderliche Java-Mindestversion:** Das Migrations-Tool funktioniert nur mit Java-Versionen 7 und höher. Beachten Sie, dass für AEM 6.3 und höher die einzigen unterstützten Versionen JRE 8 von Oracle und JRE 7 und 8 von IBM sind.

* **Aktualisierte Instanz:** Wenn Sie ein Upgrade von einer Version **älter als 5.6** durchführen, müssen Sie sicherstellen, dass eine ersetzende Aktualisierung auf AEM 6.0 durchgeführt wird, indem Sie das in der Aktualisierungsdokumentation für Version 6.0 beschriebene Verfahren befolgen.

## Vorbereitung der „AEM Quickstart“-JAR-Datei {#prep-quickstart-file}

1. Beenden Sie die Instanz, falls sie gerade ausgeführt wird. 

1. Laden Sie die neue AEM-JAR-Datei herunter und ersetzen Sie damit die alte Datei außerhalb des Ordners `crx-quickstart`. 

1. Entpacken Sie die Quickstart-JAR-Datei, indem Sie Folgendes ausführen:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

## Migration des Content-Repositorys {#content-repository-migration}

Diese Migration ist nicht erforderlich, wenn Sie ein Upgrade von AEM 6.3 durchführen. Für Versionen älter als 6.3 bietet Adobe ein Tool, mit dem Sie das Repository in die neue Version von Oak Segment Tar von AEM 6.3 migrieren können. Es wird als Teil des Schnellstartpakets bereitgestellt und ist für alle Upgrades, die TarMK verwenden, obligatorisch. Upgrades für Umgebungen, die MongoMK verwenden, erfordern keine Repository-Migration. Weitere Informationen zu den Vorteilen des neuen Segment-TAR-Formats finden Sie in den [häufig gestellten Fragen zur Migration zu Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

Die tatsächliche Migration wird mithilfe der standardmäßigen quickstart-JAR-Datei für AEM durchgeführt, und zwar mit der neuen Option `-x crx2oak`, mit der das crx2oak-Tool ausgeführt wird, um die Aktualisierung einfacher und zuverlässiger zu machen.

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

Dabei werden `<<YOUR_PROFILE>>` und `<<ADDITIONAL_FLAGS>>` durch das Profil und die Flags in der folgenden Tabelle ersetzt:

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
   <td>Siehe Fehlerbehebung unten</td>
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
   <td>Siehe Fehlerbehebung unten</td>
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

* `mongo-host` ist die IP-Adresse des MongoDB-Servers (z. B. 127.0.0.1)

* `mongo-port` ist der MongoDB-Server-Port (z. B.: 27017)

* `mongo-database-name` steht für den Namen der Datenbank (z. B.: aem-author)

**Möglicherweise benötigen Sie auch zusätzliche Schalter für folgende Szenarien:** 

* Wenn Sie das Upgrade auf einem Windows-System durchführen, auf dem die Java-Speicherzuordnung nicht korrekt durchgeführt wird, fügen Sie dem Befehl den Parameter `--disable-mmap` hinzu.

Weitere Informationen über die Verwendung des crx2oak-Tools finden Sie unter „Verwenden des [CRX2Oak Migration Tools](/help/sites-deploying/using-crx2oak.md)“. crx2oak helper JAR kann bei Bedarf manuell aktualisiert werden, indem die Datei manuell durch neuere Versionen ersetzt wird, nachdem die Schnellstart-Datei entpackt wurde. Sie finden die Datei im AEM-Installationsordner unter: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. Die neueste Version des CRX2Oak-Migrations-Tools kann vom Adobe-Repository hier heruntergeladen werden: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

Wenn die Migration erfolgreich abgeschlossen wurde, wird das Tool mit einem Exit Code von null beendet. Beachten Sie zusätzlich etwaige WARN- und ERROR-Meldungen in der Datei `upgrade.log` im AEM-Installationsverzeichnis unter `crx-quickstart/logs`. Diese Meldungen führen Fehler auf, die nicht schwerwiegend sind und bei der Migration auftraten.

Prüfen Sie die Konfigurationsdateien unter dem Ordner `crx-quickstart/install`. Wenn eine Migration erforderlich war, werden diese entsprechend dem Ziel-Repository aktualisiert.

**Hinweis zu Datenspeichern:**

`FileDataStore` ist der neue Standard für Installationen von AEM 6.3 und es ist kein externer Datenspeicher erforderlich. Die Verwendung eines externen Datenspeichers wird als Best Practice für Produktionsbereitstellungen empfohlen. Eine Aktualisierung ist jedoch nicht erforderlich. Aufgrund der Komplexität, die bereits bei der Aktualisierung von AEM vorhanden ist, empfiehlt Adobe, die Aktualisierung durchzuführen, ohne eine Datenspeichermigration vorzunehmen. Bei Bedarf kann anschließend eine Datenspeichermigration als separater Vorgang ausgeführt werden.

## Fehlerbehebung bei Migrationsproblemen {#troubleshooting-migration-issues}

Überspringen Sie diesen Abschnitt, wenn Sie ein Upgrade von 6.3 durchführen. Während die mitgelieferten crx2oak-Profile die Anforderungen der meisten Kundinnen und Kunden erfüllen sollten, gibt es Fälle, in denen zusätzliche Parameter erforderlich sind. Wenn während der Migration ein Fehler auftritt, sind für manche Aspekte Ihrer Umgebung möglicherweise zusätzliche Konfigurationsoptionen nötig. Wenn dies der Fall ist, werden Sie wahrscheinlich auf den folgenden Fehler stoßen:

**Checkpoints werden nicht kopiert, da kein externer Datenspeicher angegeben wurde. Dadurch wird das gesamte Repository beim ersten Start neu indiziert. Verwenden Sie „--skip-checkpoints“, um die Migration zu erzwingen, oder finden Sie weitere Informationen unter https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration.**

Aus irgendeinem Grund benötigt der Migrationsprozess Zugriff auf Binärdateien im Datenspeicher und kann diese nicht finden. Um Ihre Datenspeicher-Konfiguration zu spezifizieren, fügen Sie die folgenden Flags in den Abschnitt `<<ADDITIONAL_FLAGS>>` Ihres Migrationsbefehls ein:

**Für S3-Datenspeicher:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Dabei entspricht `/path/to/SharedS3DataStore.config` dem Pfad zur Konfigurationsdatei Ihres S3-Datenspeichers und `/path/to/datastore` dem Pfad zu Ihrem S3-Datenspeicher.

**Für Datei-Datenspeicher:**

```shell
--src-datastore=/path/to/datastore
```

Dabei entspricht `/path/to/datastore` dem Pfad zu Ihrem Datei-Datenspeicher.

## Durchführen der Aktualisierung {#performing-the-upgrade}

**Bei Verwendung von S3:**

1. Entfernen Sie etwaige JARs unter `crx-quickstart/install`, die mit einer früheren Version des S3 Connectors verknüpft sind.

1. Laden Sie die neueste Version des S3 Connectors 1.10.x von [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) herunter.

1. Extrahieren Sie das Paket in einem temporären Ordner und kopieren Sie den Inhalt von `jcr_root/libs/system/install` in den Ordner `crx-quickstart/install`.

### Bestimmen des korrekten Befehls zum Starten des Upgrades {#determining-the-correct-upgrade-start-command}

Um das Upgrade durchzuführen, muss AEM mithilfe der JAR-Datei gestartet werden, um die Instanz zu öffnen. Lesen Sie für die Aktualisierung auf 6.5 auch die Informationen zu den Optionen für die Neustrukturierung und Migration des Inhalts unter [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md), die Sie mit dem Upgrade-Befehl auswählen können.

>[!IMPORTANT]
>
>Wenn Sie Oracle Java 11 ausführen (oder generell Java-Versionen höher als 8), müssen beim Starten von AEM zusätzliche Schalter zur Befehlszeile hinzugefügt werden. Weitere Informationen finden Sie unter [Überlegungen zu Java 11](/help/sites-deploying/custom-standalone-install.md#java-considerations).

Beachten Sie, dass der Start von AEM über das Startskript das Upgrade nicht startet. Die meisten Kundinnen und Kunden starten AEM per Startskript und haben dieses Startskript so angepasst, dass es Schalter für Umgebungskonfigurationen wie Speichereinstellungen, Sicherheitszertifikate usw. enthält. Aus diesem Grund empfiehlt Adobe die folgende Vorgehensweise, um den richtigen Upgrade-Befehl zu ermitteln:

1. Führen Sie in einer aktiven AEM-Instanz Folgendes in der Befehlszeile aus: 

   ```shell
   ps -ef | grep java
   ```

1. Suchen Sie nach dem AEM-Prozess. Er sieht in etwa so aus:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Passen Sie den Befehl an, indem Sie den Pfad zur vorhandenen JAR-Datei (in diesem Fall `crx-quickstart/app/aem-quickstart*.jar`) mit der neuen JAR ersetzen, welche dem Ordner `crx-quickstart` gleichgeordnet ist. Wenn wir unseren vorherigen Befehl als Beispiel heranziehen, würde unser Befehl folgendermaßen lauten:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar cq-quickstart-6.5.0.jar -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Dadurch wird sichergestellt, dass alle richtigen Speichereinstellungen, benutzerdefinierten Ausführungsmodi und anderen Umgebungsparametern für das Upgrade angewendet werden. Nach Abschluss des Upgrades kann die Instanz bei zukünftigen Starts vom Startskript gestartet werden.

## Bereitstellen einer aktualisierten Code-Basis {#deploy-upgraded-codebase}

Sobald die ersetzende Aktualisierung abgeschlossen ist, sollte die aktualisierte Code-Basis bereitgestellt werden. Informationen zur Aktualisierung der Code-Basis, sodass sie in der Zielversion von AEM funktioniert, finden Sie auf der Seite [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

## Durchführen von Prüfungen und Fehlerbehebung nach einer Aktualisierung {#perform-post-upgrade-check-troubleshooting}

Siehe [Prüfungen und Fehlerbehebung nach einer Aktualisierung](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
