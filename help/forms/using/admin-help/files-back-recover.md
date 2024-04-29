---
title: Zu sichernde und wiederherzustellende Dateien
description: Dieses Dokument beschreibt die Anwendungs- und Datendateien, die gesichert werden müssen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d2dd381d-a7d2-4fec-a8ba-7ca037fd9dc1
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '2017'
ht-degree: 100%

---

# Zu sichernde und wiederherzustellende Dateien {#files-to-back-up-and-recover}

Die zu sichernden Anwendungs- und Datendateien werden in den folgenden Abschnitten ausführlicher beschrieben.

Berücksichtigen Sie die folgenden Punkte zur Sicherung und Wiederherstellung:

* Die Datenbank sollte vor dem globalen Dokumentenspeicher (GDS) und AEM-Repository gesichert werden.
* Wenn Sie die Knoten in einer geclusterten Umgebung für die Sicherung herunterfahren müssen, stellen Sie sicher, dass die sekundären Knoten vor dem primären Knoten heruntergefahren werden. Andernfalls kann es zu Unregelmäßigkeiten im Cluster oder im Server kommen. Außerdem sollte der primäre Knoten vor allen sekundären Knoten in Betrieb genommen werden.
* Für den Wiederherstellungsvorgang eines Clusters sollte der Anwendungs-Server für jeden Knoten im Cluster angehalten werden.

## Ordner des globalen Dokumentenspeichers {#global-document-storage-directory}

Der globale Dokumentenspeicher ist ein Verzeichnis zum Speichern dauerhaft genutzter Dateien in einem Prozess. Die Lebensdauer dauerhaft genutzter (langlebiger) Dateien soll sich über einen oder mehrere Starts eines AEM Forms-Systems erstrecken und kann Tage bis hin zu Jahren umfassen. Zu diesen Dateien zählen PDFs, Richtlinien und Formularvorlagen. Dauerhaft genutzte Dateien bilden einen wichtigen Teil des Gesamtstatus zahlreicher AEM Forms-Bereitstellungen. Wenn einige oder alle dauerhaft genutzten Dokumente verloren gehen oder beschädigt werden, kann der Formular-Server instabil werden.

Eingabedokumente für den asynchronen Vorgangsaufruf werden ebenfalls im globalen Dokumentenspeicher gespeichert und müssen verfügbar sein, damit Anfragen verarbeitet werden können. Deshalb ist es wichtig, die Zuverlässigkeit des Dateisystems zu berücksichtigen, auf dem sich der globale Dokumentenspeicher befindet, und RAID-Datenträger (Redundant Array of Independent Disks) oder eine andere Technologie einzusetzen, die Ihre Anforderungen an Qualität und Service-Level erfüllt.

Der Speicherort des globalen Dokumentenspeichers wird während der Installation von AEM Forms oder später mithilfe der Administrationskonsole festgelegt. Zusätzlich zur Beibehaltung eines Speicherorts mit hoher Verfügbarkeit für den globalen Dokumentenspeicher können Sie außerdem den Datenbankspeicher für Dokumente aktivieren. (Siehe [Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird](files-back-recover.md#backup-options-when-database-is-used-for-document-storage).)

### Speicherort des globalen Dokumentenspeichers {#gds-location}

Wenn Sie die Speicherorteinstellung bei der Installation leer lassen, wird als Speicherort standardmäßig ein Verzeichnis im Installationsordner des Anwendungs-Servers gewählt. Sichern Sie das folgende Verzeichnis für Ihren Anwendungs-Server:

* (JBoss) `[appserver root]/server/'server'/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

Wenn der Speicherort des globalen Dokumentenspeichers vom Standardspeicherort abweicht, können Sie ihn wie folgt bestimmen:

* Melden Sie sich bei der Administrationskonsole an und klicken Sie auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
* Notieren Sie sich den im Feld „Ordner des globalen Dokumentenspeichers“ angegebenen Speicherort.

In einer Cluster-Umgebung befindet sich der globale Dokumentenspeicher normalerweise in einem Verzeichnis, das im Netzwerk freigegeben ist und auf das alle Cluster-Knoten Lese-/Schreibzugriff haben.

Der Speicherort des globalen Dokumentenspeichers muss ggf. während einer Wiederherstellung geändert werden, wenn der ursprüngliche Speicherort nicht mehr verfügbar ist. (Siehe [Ändern des GDS-Speicherorts während der Wiederherstellung](/help/forms/using/admin-help/recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).)

### Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird {#backup-options-when-database-is-used-for-document-storage}

Sie können mithilfe der Administrationskonsole den AEM Forms-Dokumentenspeicher in der AEM Forms-Datenbank aktivieren. Obwohl bei dieser Option alle permanenten Dokumente in der Datenbank erhalten bleiben, ist AEM Forms auf den dateisystembasierten Ordner des Dokumentenspeichers angewiesen. Dieser wird nämlich zum Speichern permanenter und temporärer Dateien und Ressourcen verwendet, die mit AEM Forms-Sitzungen und -Aufrufen zusammenhängen.

Wenn Sie die Option „Dokumentenspeicherung in der Datenbank aktivieren“ in den Kernsystemeinstellungen in der Administration-Console oder mithilfe von Configuration Manager auswählen, lässt AEM Forms den Snapshot-Sicherungsmodus und den kontinuierlichen Sicherungsmodus nicht zu. Daher ist keine Verwaltung von Sicherungsmodi erforderlich, wenn Sie AEM Forms verwenden. Wenn Sie diese Option verwenden, sollten Sie den globalen Dokumentenspeicher nur einmal sichern, nachdem Sie die Option aktiviert haben. Wenn Sie AEM Forms aus einer Sicherung wiederherstellen, müssen Sie weder das Sicherungsverzeichnis für den globalen Dokumentenspeicher umbenennen noch den globalen Dokumentenspeicher wiederherstellen.

## AEM-Repository {#aem-repository}

Das AEM-Repository (CRX-Repository) wird erstellt, wenn das CRX-Repository bei der Installation von AEM Forms konfiguriert wurde.  Der Speicherort des CRX-Repository-Verzeichnisses wird während des Installationsprozesses von AEM Forms bestimmt.  Das Sichern und Wiederherstellen des AEM-Repositorys zusammen mit Datenbank und GDS ist für konsistente AEM Forms-Daten in AEM Forms erforderlich.  Das AEM-Repository enthält Daten für Correspondence Management Solution, Forms Manager und AEM Forms Workspace.

### Correspondence Management Solution {#correspondence-management-solution}

Mit der Correspondence Management Solution lässt sich die Generierung, Zusammenstellung und Bereitstellung sicherer, personalisierter und interaktiver Korrespondenzen zentralisieren und verwalten.  Es ermöglicht Ihnen, in einem optimierten Prozess von der Erstellung bis zur Archivierung schnell Korrespondenzen aus vorab genehmigten und individuell erstellten Inhalten zusammenzustellen. Dadurch ist die Kommunikation mit Ihren Kundinnen und Kunden pünktlich, präzise, bequem, sicher und relevant.  Ihr Unternehmen maximiert den Wert von Kundeninteraktionen und minimiert Kosten und Risiken durch einen Prozess, der für Einfachheit, Geschwindigkeit und Produktivität optimiert ist. 

Zu einem einfachen Setup der Correspondence Management Solution gehören eine Autoreninstanz und eine Veröffentlichungsinstanz auf demselben Computer oder auf verschiedenen Computern.

### Forms Manager {#forms-manager}

Forms Manager optimiert den Prozess zur Aktualisierung, Verwaltung und Zurücknahme von Formularen.

### AEM Forms Workspace {#html-workspace}

AEM Forms Workspace entspricht dem Funktionsumfang von Flex Workspace (für AEM Forms auf JEE nicht mehr unterstützt). Es verfügt zusätzlich über neue Funktionen zur Erweiterung und Integration von Workspace und macht die Anwendung so benutzerfreundlicher.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

Dies ermöglicht das Aufgaben-Management auf Clients ohne Flash Player und Adobe Reader. So wird die Wiedergabe von HTML-Formularen zusätzlich zu PDF- und Flex-Formularen erleichtert.

## AEM Forms-Datenbank {#aem-forms-database}

In der AEM Forms-Datenbank werden Inhalte wie Formularartefakte, Dienstkonfigurationen, Prozesszustände und Datenbankverweise auf Dateien im Verzeichnis des globalen Dokumentenspeichers und im Stammverzeichnis für Inhalte (für Content Services) gespeichert.  Datenbanksicherungen können in Echtzeit und ohne Dienstunterbrechung durchgeführt werden und Wiederherstellungen können bezogen auf einen bestimmten Zeitpunkt oder eine bestimmte Änderung erfolgen.  In diesem Abschnitt wird beschrieben, wie die Datenbank für eine Sicherung in Echtzeit konfiguriert werden muss.

Bei einem ordnungsgemäß konfigurierten AEM Forms-System können Systemadmins problemlos zusammenarbeiten, um das System in einem als funktionierend bekannten Zustand wiederherzustellen.

Um die Datenbank in Echtzeit zu sichern, müssen Sie den Snapshot-Modus wählen oder die Datenbank für die Ausführung im angegebenen Protokollmodus konfigurieren.  Dadurch können Datenbankdateien gesichert werden, während die Datenbank geöffnet und verfügbar ist.  Darüber hinaus bleiben die Rollback- und Transaktionsprotokolle der Datenbank in diesen Modi erhalten.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Content-Management-System, das mit LiveCycle installiert wird. Es ermöglicht Benutzenden, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Siehe [Adobe-Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html).

### DB2 {#db2}

Konfigurieren Sie die DB2-Datenbank für die Ausführung im Archivprotokollmodus.

>[!NOTE]
>
>Wenn Ihre AEM Forms-Umgebung von einer früheren Version von AEM Forms aktualisiert wurde und DB2 verwendet, wird keine Online-Sicherung unterstützt.  In diesem Fall müssen Sie AEM Forms herunterfahren und eine Offline-Sicherung durchführen.  In zukünftigen Versionen von AEM Forms werden Online-Sicherungen für Upgrade-Kundinnen und -Kunden unterstützt.

IBM bietet eine Zusammenstellung von Werkzeugen und Hilfesystemen an, die Datenbankadmins bei der Verwaltung von Sicherungs- und Wiederherstellungsaufgaben unterstützt:

* IBM DB2 Archive Log Accelerator
* IBM DB2 Data Archive Expert

DB2 verfügt über integrierte Funktionen zum Sichern einer Datenbank in Tivoli Storage Manager.  Durch die Verwendung von Tivoli Storage Manager können DB2-Sicherungen auf anderen Medien oder den lokalen Festplattenlaufwerken gespeichert werden.

### Oracle {#oracle}

Verwenden Sie Snapshot-Sicherungen oder konfigurieren Sie Ihre Oracle-Datenbank für die Ausführung im Archivprotokollmodus.  (Siehe [Oracle Backup: Eine Einführung](https://www.databasedesign-resource.com/oracle-backup.md)) Weitere Informationen zum Sichern und Wiederherstellen von Oracle-Datenbanken finden Sie auf den folgenden Sites:

[Oracle Backup and Recovery:](https://www.oracle.com/technetwork/database/features/availability/br-overview-097160.html) Erläutert die Konzepte bei Sicherung und Wiederherstellung und beschreibt detailliert die gängigsten Verfahren zum Verwenden von Recovery Manager (RMAN) für die Sicherung, Wiederherstellung und Berichterstellung und bietet weitere Informationen zum Entwickeln einer Sicherungs- und Wiederherstellungsstrategie.

[Oracle Database Backup and Recovery User&#39;s Guide:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10642.pdf) Bietet ausführliche Informationen zur RMAN-Architektur, zu Sicherungs- und Wiederherstellungskonzepten und -mechanismen, zu erweiterten Wiederherstellungsverfahren (z. B. zeitpunktbasierter Wiederherstellung und Datenbank-Flashback-Funktionen) sowie zur Systemleistungsoptimierung bei Sicherungen und Wiederherstellungen. Ferner werden von Benutzenden verwaltete Sicherungen und Wiederherstellungen mithilfe von Funktionen des Host-Betriebssystems anstelle von RMAN behandelt.  Dieser Artikel enthält wesentliche Informationen zu Sicherung und Wiederherstellung bei komplexeren Datenbankbereitstellungen und zu erweiterten Wiederherstellungsszenarien.

[Oracle Database Backup and Recovery Reference:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10643.pdf) Bietet ausführliche Informationen zur Syntax und Semantik aller RMAN-Befehle und beschreibt die Datenbankansichten, die für die Erstellung von Berichten zu Sicherungs- und Wiederherstellungsaktionen zur Verfügung stehen.

### SQL Server {#sql-server}

Verwenden Sie Snapshot-Sicherungen oder konfigurieren Sie Ihre SQL Server-Datenbank für die Ausführung im Transaktionsprotokollmodus.

SQL Server bietet ebenfalls zwei Tools zur Sicherung und Wiederherstellung:

* SQL Server Management Studio (grafische Benutzeroberfläche)
* T-SQL (Befehlszeile)

Weitere Informationen finden Sie unter [Sicherung und Wiederherstellung](https://msdn.microsoft.com/de-de/library/ms187048(v=SQL.90).aspx).

### MySQL {#mysql}

Verwenden Sie MySQLAdmin oder ändern Sie die INI-Dateien unter Windows so, dass die MySQL-Datenbank im binären Protokollmodus ausgeführt wird.  (Siehe [Binäre Protokollierung in MySQL](https://dev.mysql.com/doc/refman/5.1/en/binary-log.html).)  Ein Tool für die Sicherung bei laufendem Betrieb für MySQL ist außerdem bei InnoBase Software verfügbar.  (Siehe [Innobase-Sicherungen im laufenden Betrieb [Hot Backup]](https://www.innodb.com/hot-backup/features.md).)

>[!NOTE]
>
>Der binäre Standardprotokollierungsmodus für MySQL ist „Statement“. Dieser Modus ist mit den von Content Services (nicht mehr unterstützt) verwendeten Tabellen nicht kompatibel.  Durch die Verwendung der binären Protokollierung in diesem Standardmodus schlägt Content Services (nicht mehr unterstützt) fehl.  Wenn Ihr System Content Services (nicht mehr unterstützt) enthält, verwenden Sie den Protokollmodus „Gemischt“.  Um die Protokollierung im Modus „Gemischt“ zu aktivieren, fügen Sie der Datei „my.ini“ das folgende Argument hinzu: `binlog_format=mixed log-bin=logname`

Mit dem Dienstprogramm „mysqldump“ können Sie eine vollständige Datenbanksicherung erstellen.  Vollständige Sicherungen sind zwar erforderlich, aber nicht immer praktisch.  Sie generieren große Sicherungsdateien, und ihre Erzeugung nimmt viel Zeit in Anspruch.  Um eine inkrementelle Sicherung durchzuführen, stellen Sie sicher, dass Sie den Server mit der Option - `log-bin` starten, wie im vorherigen Abschnitt beschrieben. Bei jedem Neustart des MySQL-Servers wird das Schreiben in das aktuelle Binärprotokoll beendet und ein neues erstellt, das ab dann als aktuelles Binärprotokoll gilt. Über den Befehl `FLUSH LOGS SQL` können Sie diesen Wechsel manuell erzwingen. Nach der ersten vollständigen Sicherung erfolgen nachfolgende inkrementelle Sicherungen mithilfe von „mysqladmin“ und dem Befehl `flush-logs`, der die nächste Protokolldatei generiert.

Siehe [Zusammenfassung der Sicherungsstrategien](https://dev.mysql.com/doc/refman/5.5/en/backup-strategy-summary.html).

```text
binlog_format=mixed
log-bin=logname
```

## Stammverzeichnis für Inhalte (nur Content Services) {#content-storage-root-directory-content-services-only}

Das Stammverzeichnis für Inhalte enthält das Repository für Content Services (nicht mehr unterstützt), in dem alle Dokumente, Artefakte und Indizes gespeichert werden.  Die Struktur des Stammverzeichnisses für Inhalte muss gesichert werden.  In diesem Abschnitt wird beschrieben, wie der Speicherort des Stammverzeichnisses für Inhalte für eigenständige Umgebungen und Cluster-Umgebungen bestimmt wird.

### Speicherort des Stammverzeichnisses für Inhalte (eigenständige Umgebung) {#content-storage-root-location-stand-alone-environment}

Das Stammverzeichnis für Inhalte wird bei der Installation von Content Services (nicht mehr unterstützt) erstellt.  Der Speicherort des Stammverzeichnisses für Inhalte wird während des Installationsprozesses von AEM Forms bestimmt.

Der Standardspeicherort für das Stammverzeichnis der Inhaltsablage ist `[aem-forms root]/lccs_data`.

Sichern Sie folgende Verzeichnisse, die sich im Stammverzeichnis für Inhalte befinden:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Wenn das Verzeichnis „/backup-lucene-indexes“ nicht vorhanden ist, sichern Sie das Verzeichnis „/lucene-indexes“ (ebenfalls im Stammverzeichnis für Inhalte).  Wenn das Verzeichnis „/backup-lucene-indexes“ vorhanden ist, sollten Sie das Verzeichnis „/lucene-indexes“ nicht sichern, weil dies zu Fehlern führen kann.

### Speicherort des Stammverzeichnisses für Inhalte (Cluster-Umgebung) {#content-storage-root-location-clustered-environment}

Bei der Installation von Content Services (nicht mehr unterstützt) in einer Cluster-Umgebung wird das Stammverzeichnis für Inhalte in zwei gesonderte Verzeichnisse aufgeteilt:

**Stammordner für Inhalte:** Normalerweise ein freigegebener Netzwerkordner, auf den alle Knoten im Cluster Lese-/Schreibzugriff besitzen.

**Indexstammverzeichnis:** Ein Verzeichnis, das auf jedem Knoten im Cluster erstellt wird und immer denselben Pfad und Verzeichnisnamen hat.

Der Standardspeicherort für das Stammverzeichnis der Inhaltsablage ist `[GDS root]/lccs_data`, wobei `[GDS root]` der Speicherort ist, der unter [GDS-Speicherort](files-back-recover.md#gds-location) beschrieben ist. Sichern Sie folgende Verzeichnisse, die sich im Stammverzeichnis für Inhalte befinden:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Wenn das Verzeichnis „/backup-lucene-indexes“ nicht vorhanden ist, sichern Sie das Verzeichnis „/lucene-indexes“ (ebenfalls im Stammverzeichnis für Inhalte).  Wenn das Verzeichnis „/backup-lucene-indexes“ vorhanden ist, sollten Sie das Verzeichnis „/lucene-indexes“ nicht sichern, weil dies zu Fehlern führen kann.

Der Standardspeicherort für das Index-Stammverzeichnis ist `[aem-forms root]/lucene-indexes` auf jedem Knoten.

## Von Kundinnen und Kunden installierte Schriftarten {#customer-installed-fonts}

Wenn Sie zusätzliche Schriftarten in Ihrer AEM Forms-Umgebung installiert haben, müssen diese gesondert gesichert werden. Sichern Sie alle Verzeichnisse mit Adobe- und Kundenschriftarten, die in der Administrationskonsole unter „Einstellungen“ > „Core-System“ > „Konfigurationen“ angegeben sind. Stellen Sie sicher, dass Sie das gesamte Schriftartenverzeichnis sichern.

>[!NOTE]
>
>Standardmäßig befinden sich die Adobe-Schriftarten, die zusammen mit AEM Forms installiert werden, im Verzeichnis `[aem-forms root]/fonts`.

Wenn das Betriebssystem auf dem Host-Computer neu initialisiert wird und Sie Schriftarten des vorherigen Betriebssystems verwenden möchten, muss der Inhalt des Verzeichnisses mit den Systemschriftarten ebenfalls gesichert werden. (Spezifische Anweisungen finden Sie in der Dokumentation zu Ihrem Betriebssystem.)
