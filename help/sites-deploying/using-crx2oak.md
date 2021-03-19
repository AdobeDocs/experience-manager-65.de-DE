---
title: Verwendung des CRX2Oak-Migrationstools
seo-title: Verwendung des CRX2Oak-Migrationstools
description: Erlernen Sie den Umgang mit dem CRX2OAK-Migrationstool.
seo-description: Erlernen Sie den Umgang mit dem CRX2OAK-Migrationstool.
uuid: 9b788981-4ef0-446e-81f0-c327cdd3214b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: e938bdc7-f8f5-4da5-81f6-7f60c6b4b8e6
feature: Aktualisieren
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 70%

---


# Verwendung des CRX2OAK-Migrationstools{#using-the-crx-oak-migration-tool}

## Einführung {#introduction}

CRX2Oak ist ein Tool für die Migration von Daten zwischen verschiedenen Repositorys.

Es kann zur Migration von Daten aus älteren CQ-Versionen, die auf Apache Jackrabbit 2 basieren, nach Oak verwendet werden, sowie zum Kopieren von Daten zwischen Oak-Repositorys.

Die aktuelle CRX2OAK-Version kann unter der folgenden Adresse vom öffentlichen Adobe-Repository heruntergeladen werden:[ https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/)

Die Liste der Änderungen und Fehlerbehebungen für die aktuelle Version finden Sie in den [Versionshinweisen zu CRX2OAK](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/crx2oak.html).

>[!NOTE]
>
>Weitere Informationen zu Apache Oak sowie zu den Grundkonzepten der AEM-Persistenz finden Sie unter [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md).

## Anwendungsfälle zu Migration {#migration-use-cases}

Dieses Tool kann für folgende Anwendungsfälle verwendet werden:

* Migration von älteren CQ 5-Versionen nach AEM 6
* Kopieren von Daten zwischen mehreren Oak-Repositorys
* Konvertieren von Daten zwischen unterschiedlichen Oak-Mikrokernel-Implementierungen.

Die Unterstützung für die Migration von Repositorys mit externen BLOB-Speichern (allgemein als Datenspeicher bekannt) wird in unterschiedlicher Form bereitgestellt. Ein möglicher Migrationspfad ist von einem CRX2-Repository, das einen externen `FileDataStore` nutzt, auf ein Oak-Repository, das einen `S3DataStore` verwendet.

Das nachfolgende Diagramm zeigt alle von CRX2Oak unterstützten Migrationsoptionen:

![chlimage_1-151](assets/chlimage_1-151.png)

## Funktionen {#features}

CRX2OAK wird bei AEM-Aktualisierungen aufgerufen. Dabei kann der Benutzer ein vordefiniertes Migrationsprofil angeben, das die Rekonfiguration von Persistenzmodi automatisiert. Dies wird als Quickstart-Modus bezeichnet.

Das Tool kann auch separat ausgeführt werden, für den Fall, dass eine umfassendere Anpassung erforderlich ist. Beachten Sie jedoch, dass in diesem Modus Änderungen nur am Repository vorgenommen werden und dass jede weitere Neukonfiguration von AEM manuell durchgeführt werden muss. Dies wird als Standalone-Modus bezeichnet.

Eine weitere Besonderheit besteht darin, dass mit den Standardeinstellungen des Standalone-Modus nur der Knotenspeicher migriert wird und dass das neue Repository den alten Binärspeicher wiederverwendet.

### Automatisierter Quickstart-Modus  {#automated-quickstart-mode}

Ab AEM 6.3 kann das CRX2OAK-Tool benutzerdefinierte Migrationsprofile verarbeiten. Diese können so konfiguriert werden, dass alle Migrationsoptionen bereits verfügbar sind. Damit wird die Flexibilität gesteigert und eine Automatisierung der AEM-Konfiguration ermöglicht. Funktionen wie diese stehen nicht zur Verfügung, wenn Sie das Tool im Standalone-Modus verwenden.

Um CRX2OAK in den Quickstart-Modus zu schalten, müssen Sie den Pfad zum Ordner „crx-quickstart“ im AEM-Installationsverzeichnis mithilfe der folgenden Betriebssystemvariablen definieren:

**Für UNIX-basierte Systeme und Mac OS:**

```shell
export SLING_HOME="/path/to/crx-quickstart"
```

**Für Windows:**

```shell
SET "SLING_HOME=/path/to/crx-quickstart"
```

#### Unterstützung für die Fortsetzung der Migration  {#resume-support}

Die Migration kann jederzeit unterbrochen und anschließend wieder fortgesetzt werden.

#### Anpassbare Aktualisierungslogik  {#customizable-upgrade-logic}

Mithilfe von `CommitHooks` kann auch eine benutzerdefinierte Java-Logik implementiert werden. Benutzerdefinierte `RepositoryInitializer`-Klassen können implementiert werden, um das Repository mit benutzerdefinierten Werten zu initialisieren.

#### Unterstützung für Speicherzuordnungsvorgänge {#support-for-memory-mapped-operations}

CRX2OAK unterstützt standardmäßig auch Speicherzuordnungsvorgänge. Durch die Speicherzuordnung wird die Leistung erheblich verbessert. Diese Funktion sollte deshalb nach Möglichkeit verwendet werden.

>[!CAUTION]
>
>Beachten Sie jedoch, dass Speicherzuordnungsvorgänge für Windows-Plattformen nicht unterstützt werden. Es wird daher empfohlen, den Parameter **—disable-mmap** bei der Migration unter Windows hinzuzufügen.

#### Selektive Migration von Inhalten {#selective-migration-of-content}

Standardmäßig migriert das Tool das gesamte Repository unter dem Pfad `"/"`. Sie haben jedoch die vollständige Kontrolle darüber, welche Inhalte migriert werden sollen.

Wenn für die neue Instanz ein Teil des Inhalts nicht erforderlich ist, können Sie den Parameter `--exclude-path` verwenden, um den Inhalt auszuschließen und den Aktualisierungsvorgang zu optimieren.

#### Zusammenführung von Pfaden {#path-merging}

Wenn Daten zwischen zwei Repositorys kopiert werden müssen und Sie über einen Content-Pfad verfügen, der in beiden Instanzen unterschiedlich ist, können Sie sie im Parameter `--merge-path` definieren. CRX2OAK kopiert dann nur die neuen Knoten in das Ziel-Repository und behält die alten im anderen Repository bei.

![chlimage_1-152](assets/chlimage_1-152.png)

#### Versionsunterstützung {#version-support}

Standardmäßig erstellt AEM eine Version jedes Knotens oder jeder Seite, der bzw. die geändert wird, und speichert diese/n im Repository. Diese Versionen können dann zum Wiederherstellen eines früheren Status der Seite verwendet werden.

Allerdings werden diese Versionen nie bereinigt, auch wenn die Originalseite gelöscht wird. Bei Repositorys, die bereits lange Zeit verwendet werden, muss bei der Migration möglicherweise ein hohes Volumen von redundanten Daten verarbeitet werden. Schuld daran sind verwaiste Versionen.

Eine nützliche Funktion für diese Arten von Situationen ist das Hinzufügen des Parameters `--copy-versions`. Sie kann zum Überspringen der Versionsknoten während der Migration oder zum Kopieren eines Repositorys verwendet werden.

Sie können auch festlegen, ob verwaiste Versionen kopiert werden sollen, indem Sie `--copy-orphaned-versions=true` hinzufügen.

Beide Parameter unterstützen auch das Datumsformat `YYYY-MM-DD`, falls Sie Versionen spätestens zu einem bestimmten Datum kopieren möchten.

![chlimage_1-153](assets/chlimage_1-153.png)

#### Open-Source-Version {#open-source-version}

Eine Open-Source-Version von CRX2OAK ist als „Oak-Upgrade“ verfügbar. Es unterstützt alle Funktionen, mit Ausnahme der folgenden:

* CRX2-Unterstützung
* Unterstützung für Migrationsprofilen
* Unterstützung für die automatisierte AEM-Neukonfiguration

Weitere Informationen finden Sie in der [Apache-Dokumentation](https://jackrabbit.apache.org/oak/docs/migration.html).

## Parameter {#parameters}

### Knotenspeicheroptionen {#node-store-options}

* `--cache`: Die Cache-Größe in MB (der Standardwert beträgt `256`)

* `--mmap`: Aktivieren des Zugriffs auf die Speicherdatei für die Segmentspeicherung
* `--src-password:` Das Kennwort für die RDB-Quell-Datenbank

* `--src-user:` Der Benutzer für die Quell-RDB

* `--user`: Der Benutzer für die Ziel-RDB

* `--password`: Kennwort für die Zielgruppe RDB.

### Migrationsoptionen {#migration-options}

* `--early-shutdown`: Fährt das JCR2-Quell-Repository nach dem Kopieren der Knoten herunter, bevor die CommitHooks angewendet werden
* `--fail-on-error`: Erzwingt ein Fehlschlagen der Migration, wenn die Knoten nicht aus dem Quell-Repository gelesen werden können.
* `--ldap`: Migriert LDAP-Benutzer von einer CQ 5.x-Instanz zu einer Oak-basierten Instanz. Dies funktioniert jedoch nur, wenn der Identitätsanbieter in der Oak-Konfiguration als „ldap“ angegeben ist. Weitere Informationen finden Sie in der [LDAP-Dokumentation](/help/sites-administering/ldap-config.md).

* `--ldap-config:` Verwenden Sie dies in Verbindung mit dem  `--ldap` Parameter für CQ 5.x-Repositorys, die mehrere LDAP-Server zur Authentifizierung verwendet haben. Sie können damit auf die Konfigurationsdateien von CQ 5.x `ldap_login.conf` oder `jaas.conf` verweisen. Das Format ist `--ldapconfig=path/to/ldap_login.conf`.

### Optionen für die Versionsspeicherung {#version-store-options}

* `--copy-orphaned-versions`: Überspringt Kopieren verwaister Versionen. Folgende Parameter werden unterstützt: `true`, `false` und `yyyy-mm-dd`. Standardwert ist `true`.

* `--copy-versions:` Kopiert die Datenspeicherung der Version. Parameter: `true`, `false`, `yyyy-mm-dd`. Standardwert ist `true`.

#### Pfadoptionen {#path-options}

* `--include-paths:` Kommagetrennte Liste von Pfaden, die beim Kopieren einbezogen werden sollen
* `--merge-paths`: Durch Kommas getrennte Liste von Pfaden, die beim Kopieren zusammengeführt werden sollen
* `--exclude-paths:` Eine kommagetrennte Liste der beim Kopieren auszuschließenden Pfade.

### Quell BLOB-Speicheroptionen {#source-blob-store-options}

* `--src-datastore:` Der als Quelle zu verwendende Datenspeicher-Ordner  `FileDataStore`

* `--src-fileblobstore`: Der als Quelle zu verwendende Datenspeicher-Ordner  `FileBlobStore`

* `--src-s3datastore`: Der für die Quelle zu verwendende Datenspeicher-Ordner  `S3DataStore`

* `--src-s3config`: Die Konfigurationsdatei für die Quelle  `S3DataStore`.

### Ziel BLOB-Speicheroptionen {#destination-blobstore-options}

* `--datastore:` Der als Zielgruppe zu verwendende Datenspeicherordner  `FileDataStore`

* `--fileblobstore:` Der als Zielgruppe zu verwendende Datenspeicherordner  `FileBlobStore`

* `--s3datastore`: Der für die Zielgruppe zu verwendende Datenspeicherordner  `S3DataStore`

* `--s3config`: Die Konfigurationsdatei für die Zielgruppe  `S3DataStore`.

### Hilfeoptionen {#help-options}

* `-?, -h, --help:` Zeigt Hilfeinformationen an.

## Debugging {#debugging}

Sie können für den Migrationsvorgang auch Informationen zur Fehlerbehebung aktivieren, sodass potenziell auftretende Fehler behoben werden können. Hierzu gibt es verschiedene Optionen, je nachdem, in welchem Modus das Tool ausgeführt werden soll:

<table>
 <tbody>
  <tr>
   <td><strong>CRX2Oak-Modus</strong></td>
   <td><strong>Aktion</strong></td>
  </tr>
  <tr>
   <td>Quickstart-Modus</td>
   <td>Sie können die Optionen <strong>—log-level TRACE</strong> oder <strong>—log-level DEBUG </strong>zur Befehlszeile hinzufügen, wenn CRX2Oak ausgeführt wird. In diesem Modus werden Protokolle automatisch zur Datei <strong>upgrade.log</strong> umgeleitet.</td>
  </tr>
  <tr>
   <td>Standalone-Modus</td>
   <td><p>hinzufügen Sie die Optionen <strong>—trace</strong> in die CRX2Oak-Befehlszeile, um TRACE-Ereignis in der Standardausgabe anzuzeigen (Sie müssen die Protokolle selbst mithilfe des Umleitungszeichens umleiten: '&gt;' oder 'tee' Befehl für spätere Überprüfung).</p> </td>
  </tr>
 </tbody>
</table>

## Weitere Überlegungen {#other-considerations}

Bei der Migration auf eine MongoDB-Replikatgruppe muss der Parameter `WriteConcern` für alle Verbindungen mit der Mongo-Datenbank auf `2` gesetzt werden.

Hierzu können Sie den Parameter `w=2` wie nachfolgend gezeigt am Ende der Verbindungszeichenfolge hinzufügen:

```xml
java -Xmx4092m -XX:MaxPermSize=1024m -jar crx2oak.jar crx-quickstart/repository/ mongodb://localhost:27017/aem-author?replicaset=replica1&w=2
```

>[!NOTE]
>
>Weitere Informationen finden Sie in der Dokumentation zur MongoDB-Verbindungszeichenfolge unter [WriteConcerns](https://docs.mongodb.org/manual/reference/connection-string/#write-concern-options).

