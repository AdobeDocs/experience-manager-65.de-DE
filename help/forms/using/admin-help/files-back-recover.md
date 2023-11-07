---
title: Zu sichernde und wiederherzustellende Dateien
description: In diesem Dokument werden die Anwendung und die Datendateien beschrieben, die gesichert werden müssen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d2dd381d-a7d2-4fec-a8ba-7ca037fd9dc1
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '2065'
ht-degree: 18%

---

# Zu sichernde und wiederherzustellende Dateien {#files-to-back-up-and-recover}

Die zu sichernden Anwendungen und Datendateien werden in den folgenden Abschnitten ausführlicher beschrieben.

Beachten Sie die folgenden Punkte bezüglich Sicherung und Wiederherstellung:

* Die Datenbank sollte vor dem Ordner des globalen Dokumentenspeichers und AEM Repository gesichert werden.
* Wenn Sie die Knoten in einer geclusterten Umgebung für die Sicherung herunterfahren müssen, stellen Sie sicher, dass die sekundären Knoten vor dem primären Knoten heruntergefahren werden. Andernfalls kann es zu Unregelmäßigkeiten im Cluster oder im Server kommen. Außerdem sollte der primäre Knoten vor allen sekundären Knoten in Betrieb genommen werden.
* Für den Wiederherstellungsvorgang eines Clusters sollte der Anwendungsserver für jeden Knoten im Cluster angehalten werden.

## Ordner des globalen Dokumentenspeichers {#global-document-storage-directory}

Der globale Dokumentenspeicher ist ein Ordner zum Speichern dauerhaft genutzter Dateien in einem Prozess. Die Lebensdauer langlebiger Dateien soll einen oder mehrere Starts eines AEM Forms-Systems umfassen und kann Tage und sogar Jahre umfassen. Diese dauerhaft genutzten Dateien können PDF, Richtlinien und Formularvorlagen enthalten. Langlebige Dateien sind ein wichtiger Bestandteil des Gesamtstatus vieler AEM Formularbereitstellungen. Wenn einige oder alle dauerhaft genutzten Dokumente verloren gehen oder beschädigt sind, kann der Formularserver instabil werden.

Eingabedokumente für den asynchronen Auftragsaufruf werden ebenfalls im globalen Dokumentenspeicher gespeichert und müssen zur Verarbeitung von Anforderungen verfügbar sein. Daher ist es wichtig, dass Sie die Zuverlässigkeit des Dateisystems, das als Host für den globalen Dokumentenspeicher dient, berücksichtigen und ein redundantes Array unabhängiger Festplatten (RAID) oder andere Technologien entsprechend Ihren Qualitäts- und Service-Anforderungen verwenden.

Der Speicherort des globalen Dokumentenspeichers wird während der AEM Formularinstallation oder später mithilfe von Administration Console bestimmt. Zusätzlich zu einem Speicherort mit hoher Verfügbarkeit für den globalen Dokumentenspeicher können Sie auch den Datenbankspeicher für Dokumente aktivieren. Siehe [Sicherungsoptionen bei Verwendung der Datenbank für die Dokumentenspeicherung](files-back-recover.md#backup-options-when-database-is-used-for-document-storage).

### Speicherort des globalen Dokumentenspeichers {#gds-location}

Wenn Sie die Speicherorteinstellung während der Installation leer lassen, wird als Speicherort standardmäßig ein Ordner unter der Installation des Anwendungsservers verwendet. Sie müssen den folgenden Ordner für Ihren Anwendungsserver sichern:

* (JBoss) `[appserver root]/server/'server'/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

Wenn Sie den Speicherort des globalen Dokumentenspeichers in einen nicht standardmäßigen Speicherort geändert haben, können Sie ihn wie folgt bestimmen:

* Melden Sie sich bei Administration Console an und klicken Sie auf Einstellungen > Core-Systemeinstellungen > Konfigurationen.
* Notieren Sie den Speicherort, der im Feld Ordner des globalen Dokumentenspeichers angegeben ist.

In einer Clusterumgebung verweist der globale Dokumentenspeicher normalerweise auf einen Ordner, der im Netzwerk freigegeben ist und auf den jeder Clusterknoten Lese-/Schreibzugriff hat.

Der Speicherort des globalen Dokumentenspeichers kann während einer Wiederherstellung geändert werden, wenn der ursprüngliche Speicherort nicht mehr verfügbar ist. (Siehe [Ändern des GDS-Speicherorts während der Wiederherstellung](/help/forms/using/admin-help/recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).)

### Sicherungsoptionen bei Verwendung der Datenbank für die Dokumentenspeicherung {#backup-options-when-database-is-used-for-document-storage}

Sie können die Dokumentenspeicherung AEM Formulare in der AEM Forms-Datenbank mithilfe der Administration Console aktivieren. Obwohl diese Option alle permanenten Dokumente in der Datenbank speichert, erfordert AEM Formulare weiterhin den dateisystembasierten Ordner des globalen Dokumentenspeichers, da dieser zum Speichern permanenter und temporärer Dateien und Ressourcen im Zusammenhang mit Sitzungen und Aufrufen von AEM Formularen verwendet wird.

Wenn Sie die Option „Dokumentenspeicherung in der Datenbank aktivieren“ in den Kernsystemeinstellungen in der Administration-Console oder mithilfe von Configuration Manager auswählen, lässt AEM Forms den Snapshot-Sicherungsmodus und den kontinuierlichen Sicherungsmodus nicht zu. Daher ist keine Verwaltung von Sicherungsmodi erforderlich, wenn Sie AEM Forms verwenden. Wenn Sie diese Option verwenden, sollten Sie den globalen Dokumentenspeicher nur einmal sichern, nachdem Sie die Option aktiviert haben. Wenn Sie AEM Formulare aus einer Sicherung wiederherstellen, müssen Sie den Sicherungsordner für den globalen Dokumentenspeicher nicht umbenennen oder den globalen Dokumentenspeicher wiederherstellen.

## AEM Repository {#aem-repository}

AEM Repository (crx-repository) wird erstellt, wenn crx-repository bei der Installation AEM Formulare konfiguriert ist. Der Speicherort des CRX-Repository-Ordners wird während des AEM Forms-Installationsprozesses bestimmt. AEM Sicherung und Wiederherstellung des Repositorys zusammen mit der Datenbank und dem globalen Dokumentenspeicher sind für konsistente AEM Formulardaten in AEM Formularen erforderlich. AEM Repository enthält Daten für Correspondence Management Solution, Forms Manager und AEM Forms Workspace.

### Correspondence Management Solution {#correspondence-management-solution}

Correspondence Management Solution zentralisiert und verwaltet die Erstellung, Zusammenstellung und Bereitstellung sicherer, personalisierter und interaktiver Schriftstücke. Dadurch können Sie Korrespondenz aus vorab genehmigten und benutzerdefinierten Inhalten in einem optimierten Prozess von der Erstellung bis zur Archivierung schnell zusammenführen. Dadurch erhalten Ihre Kunden eine zeitnahe, genaue, bequeme, sichere und relevante Kommunikation. Ihr Unternehmen maximiert den Wert von Kundeninteraktionen und minimiert Kosten und Risiken mit einem Prozess, der für Einfachheit, Geschwindigkeit und Produktivität optimiert ist.

Eine einfache Einrichtung der Correspondence Management Solution umfasst eine Autoreninstanz und eine Veröffentlichungsinstanz auf demselben Computer oder auf verschiedenen Computern

### Forms Manager {#forms-manager}

Forms Manager optimiert den Prozess der Aktualisierung, Verwaltung und Zurücksetzung von Formularen.

### AEM Forms Workspace {#html-workspace}

AEM Forms Workspace entspricht den Funktionen von Flex Workspace (nicht mehr unterstützt für AEM Forms on JEE) und bietet neue Funktionen zur Erweiterung und Integration von Workspace und zur benutzerfreundlicheren Gestaltung.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

Sie ermöglicht die Aufgabenverwaltung auf Clients ohne Flash Player und Adobe Reader. Es erleichtert die Wiedergabe von HTML Forms neben PDF forms und Flex forms.

## AEM Formulardatenbank {#aem-forms-database}

Die AEM Forms-Datenbank speichert Inhalte wie Formularartefakte, Dienstkonfigurationen, Prozessstatus und Datenbankverweise auf Dateien im Ordner des globalen Dokumentenspeichers und im Stammordner für Inhalte (für Content Services). Datenbanksicherungen können in Echtzeit ohne Dienstunterbrechung durchgeführt werden. Die Wiederherstellung kann zu einem bestimmten Zeitpunkt oder zu einer bestimmten Änderung erfolgen. In diesem Abschnitt wird beschrieben, wie Sie Ihre Datenbank so konfigurieren, dass sie in Echtzeit gesichert werden kann.

In einem ordnungsgemäß konfigurierten AEM Forms-System können der Systemadministrator und der Datenbankadministrator problemlos zusammenarbeiten, um das System in einem konsistenten, bekannten Zustand wiederherzustellen.

Um die Datenbank in Echtzeit zu sichern, müssen Sie entweder den Snapshot-Modus verwenden oder Ihre Datenbank so konfigurieren, dass sie im angegebenen Protokollmodus ausgeführt wird. Dadurch können Ihre Datenbankdateien gesichert werden, während die Datenbank geöffnet ist und zur Verwendung verfügbar ist. Darüber hinaus behält die Datenbank ihre Rollback- und Transaktionsprotokolle bei, wenn sie in diesen Modi ausgeführt wird.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content Management System, das mit LiveCycle installiert wird. Sie ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Siehe [Adobe-Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html).

### DB2 {#db2}

Konfigurieren Sie Ihre DB2-Datenbank für die Ausführung im Archivprotokollmodus.

>[!NOTE]
>
Wenn Ihre AEM Forms-Umgebung von einer früheren Version von AEM Forms aktualisiert wurde und DB2 verwendet, wird die Online-Sicherung nicht unterstützt. In diesem Fall müssen Sie AEM Formulare herunterfahren und eine Offline-Sicherung durchführen. Zukünftige Versionen von AEM Forms unterstützen die Online-Sicherung für Upgrade-Kunden.

IBM verfügt über eine Suite von Tools und Hilfesystemen, die Datenbankadministratoren bei der Verwaltung ihrer Sicherungs- und Wiederherstellungsaufgaben unterstützen:

* IBM DB2 Archive Log Accelerator
* IBM DB2 Data Archive Expert

DB2 verfügt über integrierte Funktionen zum Sichern einer Datenbank in Tivoli Storage Manager. Mit Tivoli Storage Manager können DB2-Backups auf anderen Medien oder auf der lokalen Festplatte gespeichert werden.

### Oracle {#oracle}

Verwenden Sie Snapshot-Sicherungen oder konfigurieren Sie Ihre Oracle-Datenbank so, dass sie im Archivprotokollmodus ausgeführt wird. (Siehe [Oracle Backup: Eine Einführung](https://www.databasedesign-resource.com/oracle-backup.md)) Weitere Informationen zum Sichern und Wiederherstellen Ihrer Oracle-Datenbank finden Sie auf diesen Sites:

[Oracle Backup und Wiederherstellung:](https://www.oracle.com/technetwork/database/features/availability/br-overview-097160.html) Erläutert die Konzepte der Sicherung und Wiederherstellung sowie die gängigsten Verfahren zur Verwendung von Recovery Manager (RMAN) für die Sicherung, Wiederherstellung und Berichterstellung und liefert detailliertere Informationen zur Planung einer Sicherungs- und Wiederherstellungsstrategie.

[Oracle Database Backup and Recovery User&#39;s Guide:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10642.pdf) Enthält ausführliche Informationen zur RMAN-Architektur, zu Sicherungs- und Wiederherstellungskonzepten und -mechanismen, zu erweiterten Wiederherstellungsverfahren wie Point-in-Time-Recovery- und Datenbank-Flashback-Funktionen sowie zur Leistungsoptimierung bei Sicherung und Wiederherstellung. Es umfasst auch benutzerverwaltete Backup- und Recovery-Vorgänge, bei denen die Betriebssysteme des Hosts anstelle von RMAN verwendet werden. Dieses Volumen ist für die Sicherung und Wiederherstellung komplexerer Datenbankbereitstellungen und für erweiterte Wiederherstellungsszenarien unerlässlich.

[Oracle Database Backup and Recovery Reference:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10643.pdf) Bietet vollständige Informationen über Syntax und Semantik für alle RMAN-Befehle und beschreibt die Datenbankansichten, die für die Berichterstellung zu Sicherungs- und Wiederherstellungsaktivitäten verfügbar sind.

### SQL Server {#sql-server}

Verwenden Sie Snapshot-Sicherungen oder konfigurieren Sie Ihre SQL Server-Datenbank für die Ausführung im Transaktionsprotokollmodus.

SQL Server bietet außerdem zwei Sicherungs- und Wiederherstellungswerkzeuge:

* SQL Server Management Studio (GUI)
* T-SQL (Befehlszeile)

Weitere Informationen finden Sie unter [Sicherung und Wiederherstellung](https://msdn.microsoft.com/de-de/library/ms187048(v=SQL.90).aspx).

### MySQL {#mysql}

Verwenden Sie MySQLAdmin oder ändern Sie die INI-Dateien in Windows, um Ihre MySQL-Datenbank für die Ausführung im binären Protokollmodus zu konfigurieren. (Siehe [Binäre MySQL-Protokollierung](https://dev.mysql.com/doc/refman/5.1/en/binary-log.html). Ein Hot Backup-Tool für MySQL ist auch in der InnoBase-Software verfügbar. (Siehe [Innobase Hot Backup](https://www.innodb.com/hot-backup/features.md).

>[!NOTE]
>
Der binäre Standardprotokolliermodus für MySQL ist &quot;Statement&quot;, der nicht mit den von Content Services (nicht mehr unterstützt) verwendeten Tabellen kompatibel ist. Die Verwendung der binären Protokollierung in diesem Standardmodus führt dazu, dass Content Services (nicht mehr unterstützt) fehlschlägt. Wenn Ihr System Content Services (nicht mehr unterstützt) enthält, verwenden Sie den Protokollierungsmodus &quot;Gemischt&quot;. Um die Protokollierung im Modus „Gemischt“ zu aktivieren, fügen Sie der Datei „my.ini“ folgende Argumente hinzu:  `binlog_format=mixed log-bin=logname`

Sie können das Dienstprogramm mysqldump verwenden, um die vollständige Datenbanksicherung abzurufen. Vollständige Sicherungen sind erforderlich, aber sie sind nicht immer praktisch. Sie erzeugen große Backup-Dateien und benötigen Zeit zum Generieren. Um eine inkrementelle Sicherung durchzuführen, stellen Sie sicher, dass Sie den Server mit der Option - `log-bin` starten, wie im vorherigen Abschnitt beschrieben. Bei jedem Neustart des MySQL-Servers wird das Schreiben in das aktuelle Binärprotokoll beendet und ein neues erstellt, das ab dann als aktuelles Binärprotokoll gilt. Über den Befehl `FLUSH LOGS SQL` können Sie diesen Wechsel manuell erzwingen. Nach der ersten vollständigen Sicherung erfolgen nachfolgende inkrementelle Sicherungen mithilfe von „mysqladmin“ und dem Befehl `flush-logs`, der die nächste Protokolldatei generiert.

Siehe [Backup Strategy Summary](https://dev.mysql.com/doc/refman/5.5/en/backup-strategy-summary.html).

```text
binlog_format=mixed
log-bin=logname
```

## Stammordner für Inhalte (nur Content Services) {#content-storage-root-directory-content-services-only}

Der Stammordner für Inhalte enthält das Repository für Content Services (nicht mehr unterstützt), in dem alle Dokumente, Artefakte und Indizes gespeichert sind. Die Ordnerstruktur des Stammordners für Inhalte muss gesichert werden. In diesem Abschnitt wird beschrieben, wie Sie den Speicherort des Stammordners für Inhalte für eigenständige und Clusterumgebungen ermitteln.

### Speicherort des Stammordners für Inhalte (eigenständige Umgebung) {#content-storage-root-location-stand-alone-environment}

Der Stammordner für Inhalte wird bei der Installation von Content Services (nicht mehr unterstützt) erstellt. Der Speicherort des Stammordners für Inhalte wird während des AEM Forms-Installationsprozesses bestimmt.

Der Standardspeicherort für das Stammverzeichnis der Inhaltsablage ist `[aem-forms root]/lccs_data`.

Sichern Sie die folgenden Ordner im Stammordner für Inhalte:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Wenn der Ordner &quot;/backup-lucene-indexes&quot;nicht vorhanden ist, sichern Sie den Ordner &quot;/lucene-indexes&quot;, auch im Stammordner für Inhalte. Wenn der Ordner &quot;/backup-lucene-indexes&quot;vorhanden ist, sichern Sie den Ordner &quot;/lucene-indexes&quot;nicht, da dies zu Fehlern führen kann.

### Speicherort des Stammordners für Inhalte (Clusterumgebung) {#content-storage-root-location-clustered-environment}

Wenn Sie Content Services (nicht mehr unterstützt) in einer Clusterumgebung installieren, wird der Stammordner für Inhalte in zwei separate Ordner unterteilt:

**Stammordner für Inhalte:** Normalerweise ein freigegebener Netzwerkordner, auf den alle Knoten im Cluster Lese-/Schreibzugriff besitzen.

**Indexstammverzeichnis:** Ein Ordner, der auf jedem Knoten im Cluster erstellt wird und immer denselben Pfad und Ordnernamen hat

Der Standardspeicherort für das Stammverzeichnis der Inhaltsablage ist `[GDS root]/lccs_data`, wobei `[GDS root]` der Speicherort ist, der unter [GDS-Speicherort](files-back-recover.md#gds-location) beschrieben ist. Sichern Sie die folgenden Ordner im Stammordner für Inhalte:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Wenn der Ordner &quot;/backup-lucene-indexes&quot;nicht vorhanden ist, sichern Sie den Ordner &quot;/lucene-indexes&quot;, auch im Stammordner für Inhalte. Wenn der Ordner &quot;/backup-lucene-indexes&quot;vorhanden ist, sichern Sie den Ordner &quot;/lucene-indexes&quot;nicht, da dies zu Fehlern führen kann.

Der Standardspeicherort für das Index-Stammverzeichnis ist `[aem-forms root]/lucene-indexes` auf jedem Knoten.

## Vom Kunden installierte Schriftarten {#customer-installed-fonts}

Wenn Sie zusätzliche Schriftarten in Ihrer AEM Forms-Umgebung installiert haben, müssen Sie sie separat sichern. Sichern Sie alle Ordner mit Adobe- und Kundenschriftarten, die in Administration Console unter &quot;Einstellungen&quot;> &quot;Core System&quot;> &quot;Konfigurationen&quot;angegeben sind. Stellen Sie sicher, dass Sie den gesamten Schriftartenordner sichern.

>[!NOTE]
>
Standardmäßig befinden sich die mit AEM Formularen installierten Adobe-Schriftarten im `[aem-forms root]/fonts` Verzeichnis.

Wenn Sie das Betriebssystem auf dem Hostcomputer neu initialisieren und Schriftarten aus dem vorherigen Betriebssystem verwenden möchten, sollte auch der Inhalt des Ordners für Systemschriftarten gesichert werden. (Spezifische Anweisungen finden Sie in der Dokumentation für Ihr Betriebssystem.)
