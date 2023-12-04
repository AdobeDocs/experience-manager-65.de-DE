---
title: Sichern der Adobe Experience Manager Forms-Daten
description: In diesem Dokument werden die Schritte beschrieben, die zum Ausführen einer Onlinesicherung der Adobe Experience Manager (AEM) Forms-Datenbank, des globalen Dokumentenspeichers und des Stammordners für Inhalte erforderlich sind.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 536615a4-ab42-4b72-83b1-fad110b011ee
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '1515'
ht-degree: 10%

---

# Sichern der Adobe Experience Manager (AEM) Forms-Daten {#backing-up-the-aem-forms-data}

<!-- back up is two words when used as a verb; backup is one word when used as an adjective or noun. -->

In diesem Abschnitt werden die Schritte beschrieben, die zum Ausführen einer Onlinesicherung der AEM Forms-Datenbank, des globalen Dokumentenspeichers und des Stammordners für Inhalte erforderlich sind.

Nachdem AEM Forms installiert und in Produktionsbereichen bereitgestellt wurde, sollte der Datenbankadministrator eine vollständige Erstsicherung (Cold-Backup) der Datenbank durchführen. Die Datenbank muss für diese Sicherung heruntergefahren werden. Anschließend sollten regelmäßig differenzielle oder inkrementelle (oder heiße) Sicherungen der Datenbank durchgeführt werden.

Um eine erfolgreiche Sicherung und Wiederherstellung sicherzustellen, muss stets eine Systemabbildsicherung verfügbar sein. Wenn dann ein Verlust eintritt, können Sie Ihre gesamte Umgebung in einem konsistenten Zustand wiederherstellen.

Durch die gleichzeitige Sicherung der Datenbank mit den Sicherungen des Ordners des globalen Dokumentenspeichers, AEM und des Stammordners für Inhalte können diese Systeme bei Bedarf synchronisiert werden.

Das in diesem Abschnitt beschriebene Sicherungsverfahren erfordert, dass Sie in den abgesicherten Sicherungsmodus wechseln, bevor Sie die AEM Forms-Datenbank, AEM Repository, den globalen Dokumentenspeicher und den Stammordner für Inhalte sichern. Nach Abschluss der Sicherung müssen Sie den abgesicherten Sicherungsmodus beenden. Der abgesicherte Sicherungsmodus wird verwendet, um dauerhaft genutzte Dokumente zu kennzeichnen, die sich im globalen Dokumentenspeicher befinden. Dieser Modus stellt sicher, dass der automatisierte Dateibereinigungsmechanismus (der Datei-Wächter) abgelaufene Dateien erst löscht, wenn der abgesicherte Sicherungsmodus verfügbar ist. Die Sicherung des globalen Dokumentenspeichers muss mit einer Datenbanksicherung synchronisiert werden.

Wie oft der GDS-Speicherort gesichert werden muss, hängt davon ab, wie AEM Forms verwendet wird und welche Sicherungsfenster verfügbar sind. Das Sicherungsfenster kann durch langlebige Prozesse beeinflusst werden, da sie mehrere Tage lang ausgeführt werden können. Wenn Sie Dateien in diesem Ordner kontinuierlich ändern, hinzufügen und entfernen, sollten Sie den Speicherort des globalen Dokumentenspeichers häufiger sichern.

Wenn die Datenbank, wie im vorherigen Abschnitt beschrieben, im Protokollierungsmodus ausgeführt wird, müssen die Datenbankprotokolle ebenfalls häufig gesichert werden, damit sie bei einem Medienfehler zur Wiederherstellung der Datenbank verwendet werden können.

>[!NOTE]
>
>Dateien, auf die nicht verwiesen wird, bleiben möglicherweise nach dem Wiederherstellungsprozess im Ordner des globalen Dokumentenspeichers erhalten. Dies ist derzeit eine bekannte Einschränkung.

## Sichern Sie die Ordner &quot;Datenbank&quot;, &quot;Ordner des globalen Dokumentenspeichers&quot;, &quot;AEM&quot;und &quot;Stammordner für Inhalte&quot;. {#back-up-the-database-gds-aem-repository-and-content-storage-root-directories}

Versetzen Sie AEM Forms entweder in den abgesicherten Sicherungsmodus (Snapshot-Modus) oder in den kontinuierlichen Sicherungsmodus. Stellen Sie Folgendes sicher, bevor Sie AEM Forms auf einen der Sicherungsmodi einstellen:

* Überprüfen Sie die Systemversion und zeichnen Sie die Patches oder Updates auf, die seit der letzten vollständigen Systemabbildsicherung angewendet wurden.
* Wenn Sie Sicherungen im Rollierenden oder Snapshot-Modus verwenden, stellen Sie sicher, dass Ihre Datenbank mit den richtigen Protokolleinstellungen für Hot-Backups der Datenbank konfiguriert ist. (Siehe [AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).

Beachten Sie zusätzlich die folgenden Richtlinien für den Sicherungs-/Wiederherstellungsprozess.

* Sichern Sie den Ordner des globalen Dokumentenspeichers mithilfe eines verfügbaren Betriebssystems oder eines Backup-Dienstprogramms eines Drittanbieters. (Siehe [GDS-Speicherort](/help/forms/using/admin-help/files-back-recover.md#gds-location).
* (Optional) Sichern Sie den Stammordner für Inhalte mithilfe eines verfügbaren Betriebssystems oder eines Sicherungs- und Dienstprogramms eines Drittanbieters. (Siehe [Speicherort des Stammordners für Inhalte (eigenständige Umgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-stand-alone-environment) oder [Speicherort des Stammordners für Inhalte (Clusterumgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-clustered-environment).)
* Sichern Sie Autoren- und Veröffentlichungsinstanzen ( crx -repository backup).

  Um die Correspondence Management Solution-Umgebung zu sichern, führen Sie die Schritte für die Autoren- und Veröffentlichungsinstanzen aus, wie unter [Sichern und Wiederherstellen](/help/sites-administering/backup-and-restore.md).

  Beachten Sie beim Sichern der Autoren- und Veröffentlichungsinstanzen die folgenden Punkte:

   * Stellen Sie sicher, dass die Sicherung für Autoren- und Veröffentlichungsinstanzen synchronisiert wird, um gleichzeitig zu starten. Sie können zwar weiterhin Autoren- und Veröffentlichungsinstanzen verwenden, während die Sicherung durchgeführt wird, es wird jedoch empfohlen, keine Assets während der Sicherung zu veröffentlichen, um nicht erfasste Änderungen zu vermeiden. Warten Sie, bis die Sicherung der Autoren- und Veröffentlichungsinstanzen beendet ist, bevor Sie neue Assets veröffentlichen.
   * Die vollständige Sicherung des Autorknotens umfasst die Sicherung von Forms Manager- und AEM Forms Workspace-Daten.
   * Workbench-Entwickler können ihre Prozesse weiterhin lokal bearbeiten. Sie sollten während der Backup-Phase keine neuen Prozesse bereitstellen.
   * Die Entscheidung über die Dauer jeder Sicherungssitzung (für den kontinuierlichen Sicherungsmodus) sollte auf der Gesamtzeit basieren, die zum Sichern aller Daten in AEM Forms benötigt wird (DB, GDS, AEM Repository und alle anderen zusätzlichen benutzerdefinierten Daten).

Sichern Sie die AEM Forms-Datenbank, einschließlich aller Transaktionsprotokolle. Siehe [AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).

Weitere Informationen finden Sie im entsprechenden Knowledge Base-Artikel für Ihre Datenbank:
<!-- The four URLs below are all 404s; checked July 19, 2023 -->
* [Oracle Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403624)
* [MySQL-Sicherung und -Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403625)
* [Microsoft® SQL Server-Sicherung und -Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403623)
* [DB2® Backup und Recovery für AEM Forms](https://www.adobe.com/go/kb403626)

Diese Artikel enthalten Anleitungen zu grundlegenden Datenbankfunktionen für die Sicherung und Wiederherstellung von Daten. Sie sind nicht als allumfassende technische Leitfäden für die Sicherungs- und Wiederherstellungsfunktion der Datenbank eines bestimmten Anbieters gedacht. Sie beschreiben Befehle, die zum Erstellen einer zuverlässigen Datenbank-Backup-Strategie für Ihre AEM Forms-Anwendungsdaten erforderlich sind.

>[!NOTE]
>
>Die Datenbanksicherung muss abgeschlossen sein, bevor Sie mit der Sicherung des globalen Dokumentenspeichers beginnen. Wenn die Datenbanksicherung nicht abgeschlossen ist, sind Ihre Daten nicht synchronisiert.

### Sicherungsmodi aktivieren {#entering-the-backup-modes}

Sie können entweder Administration Console, den Befehl LCBackupMode oder die mit der AEM Forms-Installation verfügbare API verwenden, um in den Sicherungsmodus zu wechseln und ihn zu verlassen. Für die kontinuierliche Sicherung ist die Option Administration Console nicht verfügbar. Sie sollten entweder die Befehlszeilenoption oder die API verwenden. <!-- Fix broken link For information about using the API to enter and leave backup modes, see AEM Forms API Reference on Help and Tutorials page. -->

>[!NOTE]
>
>Wenn Sie SSL auf dem Forms-Server konfiguriert haben, können Sie den Forms-Server nicht mithilfe des Skripts &quot;LCBackupMode.CMD&quot;im Sicherungsmodus ausführen.

**Administration Console verwenden, um den abgesicherten Sicherungsmodus zu aktivieren**

1. Melden Sie sich bei der Administration-Console an.
1. Klicken Sie auf Einstellungen > Core-Systemeinstellungen > Backup-Dienstprogramme.
1. Wählen Sie im abgesicherten Sicherungsmodus arbeiten aus und klicken Sie auf OK.

   Durch diese Methode wird AEM Forms unbegrenzt in den Sicherungsmodus versetzt (kein Timeout), und der Snapshot-Modus wird gestartet, anstatt dass ein kontinuierlicher Sicherungsmodus durchgeführt wird.

**Verwenden der Befehlszeilenoption, um in den abgesicherten Sicherungsmodus zu wechseln**

Sie können die Befehlszeilenschnittstelle verwenden `LCBackupMode` Skripten, um AEM Forms in den abgesicherten Sicherungsmodus zu versetzen.

1. Legen Sie „ADOBE_LIVECYCLE“ fest und starten Sie den Anwendungsserver.
1. Zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` wechseln.
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.
1. Führen Sie an der Befehlszeile den folgenden Befehl in einer einzelnen Zeile aus:

   * (Windows) `LCBackupMode.cmd enter [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `] [-label=`*Label-Name* `] [-timeout=`*Sekunden* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh enter [-host=`*hostname* `] [-port=`*portnumber* `] [-user=`*Benutzername* `] [-password=`*password* `] [-label=`*labelname* `]`

   Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

   `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

   `port` ist der WebServices-Anschluss des Anwendungsservers, auf dem AEM Forms ausgeführt wird.

   `user` ist der Benutzername des AEM Forms-Administrators.

   `password` ist das Kennwort des AEM Forms-Administrators.

   `label` ist die Textbeschriftung dieser Sicherung (kann eine beliebige Zeichenfolge sein).

   `timeout` ist die Anzahl der Sekunden, nach denen der Backup-Modus automatisch beendet wird. Es kann 0-10.080 sein. Wenn der Wert 0 beträgt, was der Standardwert ist, wird der Sicherungsmodus nie unterbrochen.

   Weitere Informationen zur Befehlszeilenschnittstelle für den Sicherungsmodus finden Sie in der Datei &quot;Bitte lesen&quot;im Ordner &quot;BackupRestoreCommandline&quot;.

### Sicherungsmodi verlassen {#leaving-backup-modes}

Sie können entweder die Administration Console oder die Befehlszeilenoption verwenden, um den Sicherungsmodus zu deaktivieren.

**Den abgesicherten Sicherungsmodus deaktivieren (Snapshot-Modus)**

Führen Sie die folgenden Aufgaben aus, um mit Administration Console den abgesicherten Sicherungsmodus (Snapshot-Modus) für AEM Forms zu deaktivieren.

1. Melden Sie sich bei der Administration-Console an.
1. Klicken Sie auf Einstellungen > Core-Systemeinstellungen > Backup-Dienstprogramme.
1. Deaktivieren Sie &quot;Im abgesicherten Sicherungsmodus arbeiten&quot;und klicken Sie auf &quot;OK&quot;.

**Alle Sicherungsmodi beibehalten**

Sie können die Befehlszeilenschnittstelle verwenden, um den abgesicherten Sicherungsmodus (Snapshot-Modus) für AEM Forms zu deaktivieren oder die aktuelle Sicherungsmodussitzung (kontinuierlicher Modus) zu beenden. Sie können die Administration Console nicht verwenden, um den kontinuierlichen Sicherungsmodus zu deaktivieren. Im kontinuierlichen Sicherungsmodus sind die Steuerelemente &quot;Backup Utilities&quot;in Administration Console deaktiviert. Verwenden Sie entweder den API-Aufruf oder den Befehl LCBackupMode .

1. Zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` wechseln.
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.

   >[!NOTE]
   >
   >Legen Sie den Ordner JAVA_HOME wie im entsprechenden Kapitel für Ihren Anwendungsserver in beschrieben fest. [Vorbereiten der Installation von AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de)*.*

1. Führen Sie den folgenden Befehl in einer einzelnen Zeile aus:

   * (Windows) `LCBackupMode.cmd leaveContinuousCoverage [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh leaveContinuousCoverage [-Host=`*hostname* `] [-port=`*portnumber* `] [-user=`*Benutzername* `] [-password=`*password* `]`

     Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

     `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

     `port` ist der Anschluss, an dem AEM Forms auf dem Anwendungsserver ausgeführt wird.

     `user` ist der Benutzername des AEM Forms-Administrators.

     `password` ist das Kennwort des AEM Forms-Administrators.

     `leaveContinuousCoverage` Verwenden Sie diese Option, um den kontinuierlichen Sicherungsmodus vollständig zu deaktivieren.

   >[!NOTE]
   >
   >Solange der Sicherungsmodus deaktiviert ist, kann die kontinuierliche Abdeckung nicht wiederhergestellt werden. Alle Änderungen während dieser Zeit sind nicht geschützt.

   >[!NOTE]
   >
   >Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, sind der Snapshot-Sicherungsmodus und der kontinuierliche Sicherungsmodus nicht verfügbar.

   Weitere Informationen zur Befehlszeilenschnittstelle für den Sicherungsmodus finden Sie in der Datei &quot;readme&quot;im Ordner &quot;BackupRestoreCommandline&quot;.
