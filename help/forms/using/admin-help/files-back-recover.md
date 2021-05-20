---
title: Zu sichernde und wiederherzustellende Dateien
seo-title: Zu sichernde und wiederherzustellende Dateien
description: Dieses Dokument beschreibt die Anwendungs- und Datendateien, die gesichert werden müssen.
seo-description: Dieses Dokument beschreibt die Anwendungs- und Datendateien, die gesichert werden müssen.
uuid: ba04adb9-675a-48f2-ad52-39c1266e423b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6f9a294d-24bd-4e4b-b929-2809f5e6cef9
exl-id: d2dd381d-a7d2-4fec-a8ba-7ca037fd9dc1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2187'
ht-degree: 89%

---

# Zu sichernde und wiederherzustellende Dateien {#files-to-back-up-and-recover}

Die zu sichernden Anwendungs- und Datendateien werden in den folgenden Abschnitten detailliert beschrieben.

Berücksichtigen Sie folgende Punkte zu Sicherung und Wiederherstellung:

* Die Datenbank sollte vor GDS und AEM-Repository gesichert werden.
* Wenn Sie die Knoten in einer Clusterumgebung zur Sicherung herunterfahren müssen, stellen Sie sicher, dass die sekundären Knoten vor dem primären Knoten heruntergefahren werden. Andernfalls kann es zu Unregelmäßigkeiten im Cluster oder im Server kommen. Außerdem sollte der primäre Knoten vor jedem sekundären Knoten live geschaltet werden.
* Für den Wiederherstellungsvorgang eines Clusters sollte der Anwendungsserver für jeden Knoten im Cluster angehalten werden.

## Ordner des globalen Dokumentenspeichers {#global-document-storage-directory}

Der globale Dokumentenspeicher ist ein Ordner zum Speichern dauerhaft in einem Prozess genutzter Dateien. Die Gültigkeitsdauer dauerhaft genutzter Dateien soll mehrere Starts eines AEM Forms-Systems betragen und kann Tage bis hin zu Jahren umfassen. Zu diesen Dateien zählen PDFs, Richtlinien und Formularvorlagen. Dauerhaft genutzte Dateien bilden einen wichtigen Teil des Gesamtstatus zahlreicher AEM Forms-Bereitstellungen. Wenn einige oder alle dauerhaft genutzten Dokumente verloren gehen oder beschädigt werden, kann der Formularserver instabil werden.

Eingabedokumente für den asynchronen Auftragsaufruf werden ebenfalls im globalen Dokumentenspeicher gespeichert und müssen verfügbar sein, damit Anforderungen verarbeitet werden können. Deshalb ist es wichtig, die Zuverlässigkeit des Dateisystems zu berücksichtigen, in dem sich der globale Dokumentenspeicher befindet, der auf RAID-Datenträgern (Redundant Array of Independent Disks) oder mithilfe einer anderen Technologie gespeichert werden sollte, die Ihre Qualitäts- und Dienstanforderungen erfüllt.

Der Speicherort des globalen Dokumentenspeichers wird während des Installationsprozesses von AEM Forms oder später mithilfe von Administration Console festgelegt. Zusätzlich zur Beibehaltung eines Speicherorts für den GDS mit einer hohen Verfügbarkeit können Sie außerdem den Datenbankspeicher für Dokumente aktivieren. Siehe [Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird](files-back-recover.md#backup-options-when-database-is-used-for-document-storage).

### Speicherort des globalen Dokumentenspeichers  {#gds-location}

Wenn Sie die Speicherorteinstellung bei der Installation leer lassen, wird als Speicherort standardmäßig ein Ordner im Installationsordner des Anwendungsservers gewählt. Sie müssen für Ihren Anwendungsserver den folgenden Ordner sichern:

* (JBoss) `[appserver root]/server/'server'/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

Wenn der Speicherort des globalen Dokumentenspeichers vom Standardspeicherort abweicht, können Sie ihn wie folgt bestimmen:

* Melden Sie sich bei Administration Console an und klicken Sie auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
* Notieren Sie den im Feld „Ordner des globalen Dokumentenspeichers“ angegebenen Speicherort.

In einer Clusterumgebung befindet sich der globale Dokumentenspeicher normalerweise in einem Ordner, der im Netzwerk freigegeben ist und auf das alle Clusterknoten Lese-/Schreibzugriff haben.

Der Speicherort des globalen Dokumentenspeichers muss ggf. während einer Wiederherstellung geändert werden, wenn der ursprüngliche Speicherort nicht mehr verfügbar ist. (Siehe [Speicherort des globalen Dokumentenspeichers während der Wiederherstellung ändern](/help/forms/using/admin-help/recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).)

### Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird  {#backup-options-when-database-is-used-for-document-storage}

Sie können mithilfe von Administration Console in der AEM Forms-Datenbank AEM Forms-Dokumentenspeicher aktivieren. Obwohl bei dieser Option alle permanenten Dokumente in der Datenbank erhalten bleiben, erfordert AEM Forms den dateisystembasierten GDS-Ordner, da dieser zum Speichern permanenter und temporärer Dateien und Ressourcen, die mit AEM Forms-Sitzungen und -Aufrufen zusammenhängen, verwendet wird.

Wenn Sie die Option „Dokumentspeicher in der Datenbank aktivieren“ in den Core-Systemeinstellungen in Administration Console wählen oder Configuration Manager verwenden, sind in AEM Forms der Snapshot-Sicherungsmodus und der kontinuierliche Sicherungsmodus nicht zulässig. Daher ist keine Verwaltung von Sicherungsmodi erforderlich, wenn Sie AEM Forms verwenden. Wenn Sie diese Option verwenden, sollten Sie den globalen Dokumentenspeicher nur sichern, nachdem Sie die Option aktiviert haben. Wenn Sie AEM Forms aus einer Sicherung wiederherstellen, müssen Sie den Sicherungsordner für den GDS nicht umbenennen oder wiederherzustellen.

## AEM-Repository  {#aem-repository}

AEM-Repository (CRX-Repository) wird erstellt, wenn CRX-Repository bei der Installation von AEM Forms konfiguriert wurde. Der Speicherort des CRX-Repository-Ordners wird während des Installationsprozesses von AEM Forms bestimmt. Das Sichern und Wiederherstellen des AEM-Repository zusammen mit Datenbank und GDS ist für konsistente AEM Forms-Daten in AEM Forms erforderlich. AEM-Repository enthält Daten für Correspondence Management Solution, Forms Manager und AEM Forms Workspace.

### Correspondence Management Solution {#correspondence-management-solution}

Mit der Correspondence Management Solution lässt sich die Generierung, Zusammenstellung und Verteilung sicherer, personalisierter und interaktiver Schriftstücke zentralisieren und verwalten. Sie erhalten die Möglichkeit, ein Schriftstück in einem von der Generierung bis zur Archivierung gestrafften Prozess zügig aus vorab genehmigten wie aus benutzerdefinierten Inhalten zusammenzustellen. Dadurch ist die Kommunikation mit Ihren Kunden pünktlich, präzise, bequem, sicher und relevant. Mit einem auf leichte Handhabung, Geschwindigkeit und Produktivität ausgelegten Prozess kann Ihr Unternehmen den Wert der Kundeninteraktion in größtmöglichem Umfang nutzen und dabei zugleich Kosten und Risiken minimieren.

Zu einem einfachen Setup der Correspondence Management Solution gehört eine Autorinstanz und eine Veröffentlichungsinstanz auf demselben Computer oder auf verschiedenen Computern.

### Forms Manager  {#forms-manager}

Forms Manager optimiert den Prozess zur Aktualisierung, Verwaltung und Zurücknahme von Formularen.

### Arbeitsablauf in AEM Forms  {#html-workspace}

AEM Forms Workspace entspricht dem Funktionsumfang von Flex Workspace (für AEM Forms on JEE nicht mehr unterstützt). Es verfügt zusätzlich über neue Funktionen zur Erweiterung und Integration von Workspace und macht die Anwendung so benutzerfreundlicher.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

Dies ermöglicht die Aufgabenverwaltung auf Clients ohne Flash Player und Adobe Reader. So wird die Wiedergabe von HTML-Formularen zusätzlich zu PDF- und Flex-Formularen erleichtert.

## AEM Forms-Datenbank  {#aem-forms-database}

In der AEM Forms-Datenbank werden Inhalte wie Formularartefakte, Dienstkonfigurationen, Prozesszustände und Datenbankverweise auf Dateien im Ordner des globalen Dokumentenspeichers und im Stammordner für Inhalte (für Content Services) gespeichert. Datenbanksicherungen können in Echtzeit und ohne Dienstunterbrechung und Wiederherstellungen bezogen auf einen bestimmten Zeitpunkt oder eine bestimmte Änderung erfolgen. In diesem Abschnitt wird beschrieben, wie die Datenbank für eine Sicherung in Echtzeit konfiguriert werden muss.

Bei einem ordnungsgemäß konfigurierten AEM Forms-System können der Systemadministrator und der Datenbankadministrator problemlos zusammenarbeiten, um das System in einem als funktionierend bekannten Zustand wiederherzustellen.

Um die Datenbank in Echtzeit zu sichern, müssen Sie den Snapshot-Modus wählen oder die Datenbank für die Ausführung im angegebenen Protokollmodus konfigurieren. Dadurch können Datenbankdatendateien gesichert werden, während die Datenbank geöffnet und verfügbar ist. Darüber hinaus bleiben die Wiederherstellungs- und Transaktionsprotokolle der Datenbank in diesen Modi erhalten.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Inhaltsverwaltungssystem, das mit LiveCycle installiert wird. Es ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Siehe[ Adobe-Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html). Informationen zum Konfigurieren von Content Services (nicht mehr unterstützt) finden Sie unter [Content Services verwalten](https://help.adobe.com/en_US/livecycle/9.0/admin_contentservices.pdf).

### DB2 {#db2}

Konfigurieren Sie DB2-Datenbank für die Ausführung im Archivprotokollmodus.

>[!NOTE]
>
>Wenn Ihre AEM Forms-Umgebung von einer früheren Version von AEM Forms aktualisiert wurde und DB2 verwendet, wird keine Onlinesicherung unterstützt. In diesem Fall müssen Sie AEM Forms herunterfahren und eine Offlinesicherung durchführen. In zukünftigen Versionen von AEM Forms werden Onlinesicherungen für Upgradekunden unterstützt.

IBM bietet eine Zusammenstellung von Werkzeugen und Hilfesystemen an, die Datenbankadministratoren bei der Verwaltung von Sicherungs- und Wiederherstellungsaufgaben unterstützt:

* IBM DB2 Archive Log Accelerator (siehe [IBM DB2 Archive Log Accelerator for z/OS User&#39;s Guide](https://publib.boulder.ibm.com/infocenter/dzichelp/v2r2/topic/com.ibm.db2tools.alc.doc.ug/alcugb20.pdf?noframes=true).)
* IBM DB2 Data Archive expert (siehe [IBM DB2 Data Archive Expert User&#39;s Guide and Reference](https://publib.boulder.ibm.com/infocenter/mptoolic/v1r0/topic/com.ibm.db2tools.aeu.doc.ug/ahxugb13.pdf?noframes=true).)

DB2 verfügt über integrierte Funktionen zum Sichern einer Datenbank in Tivoli Storage Manager. Durch die Verwendung von Tivoli Storage Manager können DB2-Sicherungen auf anderen Medien oder den lokalen Festplattenlaufwerken gespeichert werden.

Weitere Informationen zum Sichern und Wiederherstellen von DB2-Datenbanken finden Sie unter [Entwickeln einer Sicherungs- und Wiederherstellungsstrategie für DB2.](https://publib.boulder.ibm.com/infocenter/db2luw/v9/index.jsp?topic=/com.ibm.db2.udb.admin.doc/doc/c0005945.htm)

### Oracle {#oracle}

Verwenden Sie Snapshot-Sicherungen oder konfigurieren Sie Ihre Oracle-Datenbank für die Ausführung im Archivprotokollmodus. (Siehe [Oracle Backup: Eine Einführung](https://www.databasedesign-resource.com/oracle-backup.md)) Weitere Informationen zum Sichern und Wiederherstellen von Oracle-Datenbanken finden Sie an folgenden Stellen:

[Oracle Backup and Recovery: ](https://www.oracle.com/technetwork/database/features/availability/br-overview-097160.html)Erläutert die Konzepte bei Sicherung und Wiederherstellung und beschreibt detailliert die gängigsten Verfahren zum Verwenden von Recovery Manager (RMAN) für die Sicherung, Wiederherstellung und Berichterstellung und bietet weitere Informationen zum Entwickeln einer Sicherungs- und Wiederherstellungsstrategie.

[Oracle Database Backup and Recovery User&#39;s Guide:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10642.pdf) Bietet ausführliche Informationen zur RMAN-Architektur, zu Sicherungs- und Wiederherstellungskonzepten und -mechanismen, zu erweiterten Wiederherstellungsverfahren (z. B. zeitpunktbasierter Wiederherstellung und Datenbank-Flashback-Funktionen) sowie zur Systemleistungsoptimierung bei Sicherung und Wiederherstellung. Ferner werden vom Benutzer verwaltete Sicherungen und Wiederherstellungen mithilfe von Funktionen des Hostbetriebssystems anstelle von RMAN behandelt. Dieses Handbuch enthält wesentliche Informationen zu Sicherung und Wiederherstellung bei komplexeren Datenbankbereitstellungen und zu erweiterten Wiederherstellungsszenarien.

[Oracle Database Backup and Recovery Reference:](https://download.oracle.com/docs/cd/E11882_01/backup.112/e10643.pdf) Bietet ausführliche Informationen zur Syntax und Semantik aller RMAN-Befehle und beschreibt die Datenbankansichten, die für die Erstellung von Berichten zu Sicherungs- und Wiederherstellungsaktionen zur Verfügung stehen.

### SQL Server  {#sql-server}

Verwenden Sie Snapshot-Sicherungen oder konfigurieren Sie Ihre SQL Server-Datenbank für die Ausführung im Transaktionsprotokollmodus.

SQL Server bietet auch zwei Sicherungs- und Wiederherstellungswerkzeuge:

* SQL Server Management Studio (grafische Benutzeroberfläche)
* T-SQL (Befehlszeile)

Weitere Informationen finden Sie unter [Backup and Restore](https://msdn.microsoft.com/en-us/library/ms187048(v=SQL.90).aspx).

### MySQL {#mysql}

Verwenden Sie MySQLAdmin oder ändern Sie die INI-Dateien unter Windows so, dass die MySQL-Datenbank im binären Protokollmodus ausgeführt wird. (Siehe[ Binäre Protokollierung in MySQL](https://dev.mysql.com/doc/refman/5.1/en/binary-log.html).) Ein Werkzeug für die Sicherung bei laufendem Betrieb für MySQL steht außerdem von InnoBase Software zur Verfügung. (Siehe [Innobase-Sicherungen im laufenden Betrieb (Hot Backup)](https://www.innodb.com/hot-backup/features.md).)

>[!NOTE]
>
>Der binäre Standardprotokolliermodus für MySQL ist „Statement“. Dieser Modus ist mit von Content Services (nicht mehr unterstützt) verwendeten Tabellen nicht kompatibel. Durch die Verwendung der binären Protokollierung in diesem Standardmodus schlägt Content Services (nicht mehr unterstützt) fehl. Wenn Ihr System Content Services (nicht mehr unterstützt) enthält, verwenden Sie den Protokollmodus „Gemischt“. Um die Protokollierung im Modus „Gemischt“ zu aktivieren, fügen Sie der Datei „my.ini“ folgende Argumente hinzu:  `binlog_format=mixed log-bin=logname`

Mit dem Dienstprogramm „mysqldump“ können Sie eine vollständige Datenbanksicherung erstellen. Vollständige Sicherungen sind erforderlich, aber nicht immer zweckmäßig. Sie erzeugen große Sicherungsdateien und ihre Erzeugung nimmt viel Zeit in Anspruch. Stellen Sie für eine inkrementelle Sicherung sicher, dass Sie den Server mit der Option - `log-bin` starten, wie im vorherigen Abschnitt beschrieben. Bei jedem Neustart des MySQL-Servers wird das Schreiben in das aktuelle Binärprotokoll beendet und ein neues erstellt, das ab dann als aktuelles Binärprotokoll gilt. Mit dem Befehl `FLUSH LOGS SQL` können Sie einen Wechsel manuell erzwingen. Nach der ersten vollständigen Sicherung erfolgen nachfolgende inkrementelle Sicherungen mithilfe von „mysqladmin“ und dem Befehl `flush-logs`, der die nächste Protokolldatei generiert.

Siehe [Backup Strategy Summary](https://dev.mysql.com/doc/refman/5.5/en/backup-strategy-summary.html).

```text
binlog_format=mixed
log-bin=logname
```

## Stammordner für Inhalte (nur Content Services)  {#content-storage-root-directory-content-services-only}

Der Stammordner für Inhalte enthält das Repository für Content Services (nicht mehr unterstützt), in dem alle Dokumente, Artefakte und Indizes gespeichert werden. Die Struktur des Stammordners für Inhalte muss gesichert werden. In diesem Abschnitt wird beschrieben, wie der Speicherort des Stammordners für Inhalte für eigenständige und Clusterumgebungen bestimmt wird.

### Speicherort des Stammordners für Inhalte (eigenständige Umgebung)  {#content-storage-root-location-stand-alone-environment}

Der Stammordner für Inhalte wird bei der Installation von Content Services (nicht mehr unterstützt) erstellt. Der Speicherort des Stammordners für Inhalte wird während des Installationsprozesses von AEM Forms bestimmt.

Der Standardspeicherort für den Stammordner für Inhalte ist `[aem-forms root]/lccs_data`.

Sichern Sie folgende Ordner, die sich im Stammordner für Inhalte befinden:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Wenn der Ordner „/backup-lucene-indexes“ nicht vorhanden ist, sichern Sie den Ordner „/lucene-indexes“ (ebenfalls im Stammordner für Inhalte). Wenn der Ordner „/backup-lucene-indexes“ vorhanden ist, sichern Sie nicht den Ordner „/lucene-indexes“, weil dies zu Fehlern führen kann.

### Speicherort des Stammordners für Inhalte (Clusterumgebung)  {#content-storage-root-location-clustered-environment}

Bei der Installation von Content Services (nicht mehr unterstützt) in einer Clusterumgebung wird der Stammordner für Inhalte in zwei gesonderte Ordner aufgeteilt:

**Stammordner für Inhalte:** Normalerweise ein freigegebener Netzwerkordner, auf den alle Knoten im Cluster Lese-/Schreibzugriff besitzen.

**Indexstammordner:** Ein Ordner, der auf jedem Knoten im Cluster erstellt wird und immer denselben Pfad und Ordnernamen hat.

Der Standardspeicherort für den Stammordner für Inhalte ist `[GDS root]/lccs_data`, wobei `[GDS root]` der unter [GDS-Speicherort](files-back-recover.md#gds-location) beschriebene Speicherort ist. Sichern Sie folgende Ordner, die sich im Stammordner für Inhalte befinden:

/audit.contentstore

/contentstore

/contentstore.deleted

/backup-lucene-indexes

Wenn der Ordner „/backup-lucene-indexes“ nicht vorhanden ist, sichern Sie den Ordner „/lucene-indexes“ (ebenfalls im Stammordner für Inhalte). Wenn der Ordner „/backup-lucene-indexes“ vorhanden ist, sichern Sie nicht den Ordner „/lucene-indexes“, weil dies zu Fehlern führen kann.

Der Standardspeicherort für den Indexstammordner ist `[aem-forms root]/lucene-indexes` auf jedem Knoten.

## Vom Kunden installierte Schriftarten {#customer-installed-fonts}

Wenn Sie zusätzliche Schriftarten in Ihrer AEM Forms-Umgebung installiert haben, müssen diese gesondert gesichert werden. Sichern Sie alle Ordner mit Adobe- und Kundenschriften, die in Administration Console unter „Einstellungen“ > „Core-System“ > „Konfigurationen“ angegeben sind. Stellen Sie sicher, dass der gesamte Schriftartenordner gesichert wird.

>[!NOTE]
>
>Standardmäßig befinden sich die mit AEM Formularen installierten Adobe-Schriftarten im Ordner `[aem-forms root]/fonts` .

Wenn das Betriebssystem auf dem Hostcomputer neu initialisiert wird und Sie Schriftarten des vorherigen Betriebssystems verwenden möchten, muss der Inhalt des Ordners mit den Systemschriftarten ebenfalls gesichert werden. (Spezifische Anweisungen finden Sie in der Dokumentation zum Betriebssystem.)
