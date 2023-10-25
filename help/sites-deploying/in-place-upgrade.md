---
title: Durchführen einer ersetzenden Aktualisierung
description: Erfahren Sie, wie Sie eine ersetzende Aktualisierung für AEM 6.5 durchführen.
topic-tags: upgrading
feature: Upgrading
exl-id: aef6ef00-993c-4252-b0ad-ddc4917beaf7
source-git-commit: e54c1d422f2bf676e8a7b0f50a101e495c869c96
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 53%

---

# Durchführen einer ersetzenden Aktualisierung{#performing-an-in-place-upgrade}

>[!NOTE]
>
>Auf dieser Seite wird das Aktualisierungsverfahren für AEM 6.5 beschrieben. Wenn Sie eine Installation haben, die auf einem Anwendungsserver bereitgestellt wird, lesen Sie [Aktualisierungsschritte für Anwendungsserverinstallationen](/help/sites-deploying/app-server-upgrade.md).

## Schritte vor der Aktualisierung {#pre-upgrade-steps}

Vor der Durchführung des Upgrades müssen einige Schritte ausgeführt werden. Siehe [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) und [Wartungsaufgaben vor einer Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) für weitere Informationen. Stellen Sie außerdem sicher, dass Ihr System die Anforderungen für die neue Version von AEM erfüllt. Erfahren Sie, wie Sie mit der Mustererkennung die Komplexität Ihrer Aktualisierung abschätzen können, und lesen Sie auch den Abschnitt &quot;Aktualisierungsumfang und -anforderungen&quot;unter [Planung der Aktualisierung](/help/sites-deploying/upgrade-planning.md) für weitere Informationen.

<!--Finally, note that the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migrationsvoraussetzungen {#migration-prerequisites}

* **Erforderliche Java-Mindestversion:** Das Migrationstool funktioniert nur mit Java-Versionen 7 und höher. Beachten Sie, dass für AEM 6.3 und höher die einzigen unterstützten Versionen JRE 8 von Oracle und JRE 7 und 8 von IBM sind.

* **Aktualisierte Instanz:** Wenn Sie ein Upgrade von einer Version durchführen **älter als 5.6** müssen Sie sicherstellen, dass Sie eine ersetzende Aktualisierung auf AEM 6.0 durchgeführt haben, indem Sie das in der Aktualisierungsdokumentation für 6.0 beschriebene Verfahren befolgen.

## Vorbereitung der „AEM Quickstart“-JAR-Datei {#prep-quickstart-file}

1. Beenden Sie die Instanz, falls sie gerade ausgeführt wird. 

1. Laden Sie die neue AEM-JAR-Datei herunter und ersetzen Sie damit die alte Datei außerhalb des Ordners `crx-quickstart`. 

1. Entpacken Sie die Quickstart-JAR-Datei, indem Sie Folgendes ausführen:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

## Migration des Content-Repositorys {#content-repository-migration}

Diese Migration ist nicht erforderlich, wenn Sie ein Upgrade von AEM 6.3 durchführen. Für Versionen, die älter als 6.3 sind, bietet Adobe ein Tool, mit dem das Repository zur neuen Version des Oak Segment Tar in AEM 6.3 migriert werden kann. Sie wird als Teil des Schnellstartpakets bereitgestellt und ist für alle Upgrades, die TarMK verwenden, obligatorisch. Upgrades für Umgebungen, die MongoMK verwenden, erfordern keine Repository-Migration. Weitere Informationen zu den Vorteilen des neuen Segment-TAR-Formats finden Sie unter [Häufig gestellte Fragen zur Migration zu Oak Segment Tar](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

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

Weitere Informationen über die Verwendung des crx2oak-Tools finden Sie unter „Verwenden des [CRX2Oak Migration Tools](/help/sites-deploying/using-crx2oak.md)“. crx2oak helper JAR kann bei Bedarf manuell aktualisiert werden, indem die Datei manuell durch neuere Versionen ersetzt wird, nachdem die Schnellstart-Datei entpackt wurde. Sie finden die Datei im AEM-Installationsordner unter:   `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. Die neueste Version des CRX2Oak-Migrations-Tools kann vom Adobe-Repository hier heruntergeladen werden: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

Wenn die Migration erfolgreich abgeschlossen wurde, wird das Tool mit einem Exit Code von null beendet. Beachten Sie zusätzlich etwaige WARN- und ERROR-Meldungen in der Datei `upgrade.log` im AEM-Installationsverzeichnis unter `crx-quickstart/logs`. Diese Meldungen führen Fehler auf, die nicht schwerwiegend sind und bei der Migration auftraten.

Prüfen Sie die Konfigurationsdateien unter dem Ordner `crx-quickstart/install`. Wenn eine Migration erforderlich war, werden diese entsprechend dem Ziel-Repository aktualisiert.

**Hinweis zu Datenspeichern:**

`FileDataStore` ist der neue Standard für Installationen von AEM 6.3 und es ist kein externer Datenspeicher erforderlich. Die Verwendung eines externen Datenspeichers wird als Best Practice für Produktionsimplementierungen empfohlen. Eine Aktualisierung ist jedoch nicht erforderlich. Aufgrund der Komplexität, die bereits bei der Aktualisierung von AEM vorhanden ist, empfiehlt Adobe, die Aktualisierung durchzuführen, ohne eine Datenspeichermigration vorzunehmen. Bei Bedarf kann anschließend eine Datenspeichermigration als separater Vorgang ausgeführt werden.

## Fehlerbehebung bei Migrationsproblemen {#troubleshooting-migration-issues}

Bitte überspringen Sie diesen Abschnitt, wenn Sie ein Upgrade von 6.3 durchführen. Während die bereitgestellten crx2oak-Profile den Anforderungen der meisten Kunden entsprechen sollten, sind manchmal zusätzliche Parameter erforderlich. Wenn während der Migration ein Fehler auftritt, sind für manche Aspekte Ihrer Umgebung möglicherweise zusätzliche Konfigurationsoptionen nötig. In diesem Fall tritt wahrscheinlich der folgende Fehler auf:

**Checkpoints werden nicht kopiert, da kein externer Datenspeicher angegeben wurde. Dadurch wird das gesamte Repository beim ersten Start neu indiziert. Verwenden Sie —skip-checkpoints , um die Migration zu erzwingen, oder finden Sie weitere Informationen unter https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration .**

Aus irgendeinem Grund benötigt der Migrationsprozess Zugriff auf Binärdateien im Datenspeicher und kann ihn nicht finden. Um Ihre Datenspeicher-Konfiguration zu spezifizieren, fügen Sie die folgenden Flags in den Abschnitt `<<ADDITIONAL_FLAGS>>` Ihres Migrationsbefehls ein:

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

## Durchführen des Upgrades {#performing-the-upgrade}

**Bei Verwendung von S3:**

1. Entfernen Sie etwaige JARs unter `crx-quickstart/install`, die mit einer früheren Version des S3 Connectors verknüpft sind.

1. Laden Sie die neueste Version des S3 Connectors 1.10.x von [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) herunter.

1. Extrahieren Sie das Paket in einem temporären Ordner und kopieren Sie den Inhalt von `jcr_root/libs/system/install` in den Ordner `crx-quickstart/install`.

### Bestimmen des korrekten Befehls zum Starten des Upgrades {#determining-the-correct-upgrade-start-command}

Um das Upgrade auszuführen, ist es wichtig, mit der Verwendung der JAR-Datei zu beginnen, AEM die Instanz aufzurufen. Lesen Sie für die Aktualisierung auf 6.5 auch die Informationen zu den Optionen für die Neustrukturierung und Migration des Inhalts unter [Lazy-Content-Migration](/help/sites-deploying/lazy-content-migration.md), die Sie mit dem Upgrade-Befehl auswählen können.

>[!IMPORTANT]
>
>Wenn Sie Oracle Java 11 ausführen (oder generell Java-Versionen aktueller als 8), werden zusätzliche Parameter zu Ihrer Befehlszeile hinzugefügt, sobald AEM gestartet wird. Weitere Informationen finden Sie unter [Überlegungen zu Java 11](/help/sites-deploying/custom-standalone-install.md#java-considerations).

Beachten Sie, dass das Starten von AEM ab dem Startskript die Aktualisierung nicht startet. Die meisten Kunden beginnen AEM mit der Verwendung des Startskripts und haben dieses Startskript so angepasst, dass es Switches für Umgebungskonfigurationen wie Speichereinstellungen, Sicherheitszertifikate usw. enthält. Daher empfiehlt Adobe, dieses Verfahren zu befolgen, um den richtigen Aktualisierungsbefehl zu ermitteln:

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

   Dadurch wird sichergestellt, dass alle richtigen Speichereinstellungen, benutzerdefinierten Ausführungsmodi und anderen Umgebungsparametern für die Aktualisierung angewendet werden. Nach Abschluss des Upgrades kann die Instanz bei zukünftigen Starts vom Startskript gestartet werden.

## Aktualisierte Codebase bereitstellen {#deploy-upgraded-codebase}

Sobald die ersetzende Aktualisierung abgeschlossen ist, sollte die aktualisierte Codebasis bereitgestellt werden. Informationen zur Aktualisierung der Code-Basis, sodass sie in der Zielversion von AEM funktioniert, finden Sie auf der Seite [Aktualisieren von Codes und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

## Prüfungen und Fehlerbehebung nach der Aktualisierung durchführen {#perform-post-upgrade-check-troubleshooting}

Siehe [Prüfungen und Fehlerbehebung nach einem Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
