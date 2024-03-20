---
title: Sichern der Adobe Experience Manager Forms-Daten
description: In diesem Dokument werden die Schritte zum Erstellen einer Online-Sicherung (bei laufendem Betrieb) der Adobe Experience Manager (AEM) Forms-Datenbank, des GDS sowie der Stammordner für Inhalte beschrieben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 536615a4-ab42-4b72-83b1-fad110b011ee
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1515'
ht-degree: 96%

---

# Sichern der Adobe Experience Manager (AEM) Forms-Daten {#backing-up-the-aem-forms-data}

<!-- back up is two words when used as a verb; backup is one word when used as an adjective or noun. -->

In diesem Abschnitt werden die Schritte zum Erstellen einer Online-Sicherung (bei laufendem Betrieb) der AEM Forms-Datenbank, des GDS sowie der Stammordner für Inhalte beschrieben.

Im Anschluss an die Installation und Bereitstellung von AEM Forms in Produktionsbereichen müssen Datenbankadmins eine vollständige Erstsicherung (nicht bei laufendem Betrieb) der Datenbank durchführen. Für diese Sicherung muss die Datenbank heruntergefahren werden. Anschließend müssen in regelmäßigen Abständen differenzielle oder inkrementelle Sicherungen (bei laufendem Betrieb) der Datenbank erfolgen.

Damit eine erfolgreiche Sicherung und Wiederherstellung sichergestellt ist, muss jederzeit eine Systemabbildsicherung verfügbar sein. So können Sie beim Auftreten von Datenverlusten die gesamte Umgebung in einem konsistenten Zustand wiederherstellen.

Durch das gleichzeitige Sichern von GDS, AEM-Repository und dem Stammordner für Inhalte zusammen mit der Datenbank wird die Synchronisierung dieser Systeme im Falle einer Wiederherstellung erleichtert.

Das in diesem Abschnitt beschriebene Sicherungsverfahren erfordert, dass Sie in den abgesicherten Sicherungsmodus wechseln, bevor Sie die AEM Forms-Datenbank, das AEM-Repository, den GDS sowie die Stammordner für Inhalte sichern. Nach Abschluss der Sicherung müssen Sie den abgesicherten Sicherungsmodus beenden. Der abgesicherte Sicherungsmodus dient zum Markieren langlebiger und dauerhaft genutzter Dokumente im GDS. Dieser Modus stellt sicher, dass der automatisierte Dateibereinigungsmechanismus (der Datei-Wächter) abgelaufene Dateien erst löscht, wenn der abgesicherte Sicherungsmodus beendet wurde. Die GDS-Sicherung muss mit einer Datenbanksicherung synchronisiert werden.

Wie oft der GDS-Speicherort gesichert werden muss, hängt davon ab, wie AEM Forms verwendet wird und welche Sicherungsfenster verfügbar sind. Das Sicherungsfenster kann durch langlebige Prozesse beeinflusst werden, da diese ggf. mehrere Tage lang ausgeführt werden. Wenn Sie laufend Dateien in diesem Ordner ändern, hinzufügen und entfernen, sollte der GDS öfter gesichert werden.

Wenn die Datenbank (wie im vorherigen Abschnitt beschrieben) im Protokollierungsmodus ausgeführt wird, müssen die Datenbankprotokolle ebenfalls häufig gesichert werden, damit sie bei einem Medienfehler zur Wiederherstellung der Datenbank verwendet werden können.

>[!NOTE]
>
>Dateien, auf die nicht verwiesen wird, bleiben möglicherweise nach dem Wiederherstellungsprozess im GDS-Verzeichnis erhalten. Dies ist derzeit eine bekannte Einschränkung.

## Sichern von Datenbank, GDS, AEM-Repository sowie Stammordnern für Inhalte {#back-up-the-database-gds-aem-repository-and-content-storage-root-directories}

Versetzen Sie AEM Forms entweder in den abgesicherten Sicherungsmodus (Snapshot-Modus) oder in den kontinuierlichen Sicherungsmodus. Bevor Sie festlegen, dass AEM Forms in einen der Sicherungsmodi versetzt wird, stellen Sie Folgendes sicher:

* Überprüfen Sie die Systemversion und notieren Sie Patches und Aktualisierungen, die seit der letzten vollständigen Systemabbildsicherung angewendet wurden.
* Stellen Sie bei Verwendung kontinuierlicher Sicherungen bzw. Sicherungen im Snapshot-Modus sicher, dass die Datenbank mit den ordnungsgemäßen Protokollierungseinstellungen für Datenbanksicherungen im laufenden Betrieb konfiguriert ist. (Siehe [AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).)

Beachten Sie zusätzlich die folgenden Richtlinien für den Sicherungs-/Wiederherstellungsprozess.

* Sichern Sie das GDS-Verzeichnis mithilfe eines Sicherungsprogramms des Betriebssystems oder eines anderen Anbieters. (Siehe [GDS-Speicherort](/help/forms/using/admin-help/files-back-recover.md#gds-location).)
* (Optional) Sichern Sie den Stammordner für Inhalte mithilfe eines Sicherungsprogramms des Betriebssystems oder eines anderen Anbieters. (Siehe [Speicherort des Stammordners für Inhalte (eigenständige Umgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-stand-alone-environment) oder [Speicherort des Stammordners für Inhalte (Clusterumgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-clustered-environment).)
* Sichern Sie Autoren- und Veröffentlichungsinstanzen ( crx -repository backup).

  Um die Correspondence Management Solution-Umgebung zu sichern, führen Sie die Schritte für Autoren- und Veröffentlichungsinstanzen durch wie unter [Sichern und Wiederherstellen](/help/sites-administering/backup-and-restore.md) beschrieben.

  Beachten Sie beim Sichern der Autoren- und Veröffentlichungsinstanzen die folgenden Punkte:

   * Stellen Sie sicher, dass die Sicherung für Autoren- und Veröffentlichungsinstanzen so synchronisiert sind, dass sie gleichzeitig starten. Obwohl Sie Autoren- und Veröffentlichungsinstanzen während der Sicherung weiter verwenden können, wird empfohlen, dabei kein Medienelement zu veröffentlichen, um nicht gespeicherte Änderungen zu vermeiden. Warten Sie also, bis die Sicherung der Autoren- und Veröffentlichungsinstanzen beendet ist, bevor Sie neue Medienelemente veröffentlichen.
   * Die vollständige Sicherung des Autorknotens umfasst die Sicherung von Forms Manager- und AEM Forms Workspace-Daten.
   * Workbench-Entwicklerinnen und -Entwickler können ihre Prozesse weiterhin lokal bearbeiten. Sie sollten während der Sicherung jedoch keine neuen Prozesse bereitstellen.
   * Die Entscheidung über die Dauer der einzelnen Sicherungssitzungen (für den kontinuierlichen Sicherungsmodus) sollte auf der Gesamtzeit basieren, die zum Sichern aller Daten in AEM Forms erforderlich ist (DB, GDS, AEM-Repository und alle anderen zusätzlichen benutzerdefinierten Daten).

Sichern Sie die AEM Forms-Datenbank, einschließlich aller Transaktionsprotokolle. Siehe [AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).

Weitere Informationen finden Sie im entsprechenden Knowledgebase-Artikel für Ihre Datenbank:
<!-- The four URLs below are all 404s; checked July 19, 2023 -->
* [Oracle-Backup und -Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403624)
* [MySQL-Backup und -Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403625)
* [Microsoft® SQL Server-Backup und -Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403623)
* [DB2®-Backup und -Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403626)

Diese Artikel enthalten Anleitungen zu grundlegenden Datenbankfunktionen für die Sicherung und Wiederherstellung von Daten. Sie sind nicht als allumfassende technische Handbücher für die Sicherungs- und Wiederherstellungsfunktion der Datenbank eines bestimmten Anbieters gedacht. Es handelt sich lediglich um allgemeine Informationen zu Befehlen, die zum Erstellen einer zuverlässigen Datenbanksicherungsstrategie für Ihre AEM Forms-Anwendungsdaten erforderlich sind.

>[!NOTE]
>
>Die Datenbanksicherung muss abgeschlossen sein, bevor Sie mit der Sicherung des globalen Dokumentenspeichers beginnen. Wenn die Datenbanksicherung nicht abgeschlossen ist, sind Ihre Daten nicht synchronisiert.

### Wechseln in die Sicherungsmodi {#entering-the-backup-modes}

Sie können entweder die Administration Console, den Befehl „LCBackupMode“ oder die mit der AEM Forms-Installation verfügbare API verwenden, um in den Sicherungsmodus zu wechseln bzw. ihn zu verlassen. Für die kontinuierliche (rollierende) Sicherung ist die Option Administrationskonsole nicht verfügbar. Sie sollten entweder die Befehlszeilenoption oder die API verwenden. <!-- Fix broken link For information about using the API to enter and leave backup modes, see AEM Forms API Reference on Help and Tutorials page. -->

>[!NOTE]
>
>Wenn Sie SSL auf dem Forms-Server konfiguriert haben, können Sie den Formular-Server nicht mithilfe des Skripts „LCBackupMode.CMD“ im Sicherungsmodus ausführen.

**Verwenden der Administrationskonsole, um den abgesicherten Sicherungsmodus zu aktivieren**

1. Melden Sie sich bei der Administration-Console an.
1. Klicken Sie auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Backup-Dienstprogramme“.
1. Wählen Sie „Im abgesicherten Sicherungsmodus arbeiten“ aus und klicken Sie auf „OK“.

   Durch diese Methode wird AEM Forms unbegrenzt in den Sicherungsmodus versetzt (kein Timeout) und verwendet den Snapshot-Modus anstatt eines rollierenden Sicherungsmodus.

**Verwenden der Befehlszeilenoption, um in den abgesicherten Sicherungsmodus zu wechseln**

Sie können die `LCBackupMode`-Skripte verwenden, um AEM Forms über die Befehlszeilenschnittstelle in den abgesicherten Sicherungsmodus zu versetzen.

1. Legen Sie „ADOBE_LIVECYCLE“ fest und starten Sie den Anwendungsserver.
1. Zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` wechseln.
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.
1. Führen Sie an der Befehlszeile den folgenden Befehl in einer einzelnen Zeile aus:

   * (Windows) `LCBackupMode.cmd enter [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `] [-label=`*Label-Name* `] [-timeout=`*Sekunden* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh enter [-host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Passwort* `] [-label=`*Beschriftungsname* `]`

   Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

   `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

   `port` ist der WebServices-Anschluss des Anwendungs-Servers, auf dem AEM Forms ausgeführt wird.

   `user` ist der Benutzername der oder des AEM Forms-Admins.

   `password` ist das Kennwort der oder des AEM Forms-Admins.

   `label` ist die Textbeschriftung dieser Sicherung (kann eine beliebige Zeichenfolge sein).

   `timeout` ist die Anzahl der Sekunden, nach denen der Backup-Modus automatisch beendet wird. Sie kann zwischen 0 und 10.080 liegen. Wenn der Wert 0 beträgt, was der Standardwert ist, wird der Sicherungsmodus nie unterbrochen.

   Weitere Informationen zum Wechseln in den Sicherungsmodus über die Befehlszeilenschnittstelle finden Sie in der Readme-Datei im Verzeichnis „BackupRestoreCommandline“.

### Verlassen der Sicherungsmodi {#leaving-backup-modes}

Sie können entweder die Administrationskonsole oder die Befehlszeilenoption verwenden, um den Sicherungsmodus zu deaktivieren.

**Verlassen des abgesicherten Sicherungsmodus (Snapshot-Modus)**

Führen Sie die folgenden Aufgaben aus, um mit der Administrationskonsole den abgesicherten Sicherungsmodus (Snapshot-Modus) für AEM Forms zu deaktivieren.

1. Melden Sie sich bei der Administration-Console an.
1. Klicken Sie auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Backup-Dienstprogramme“.
1. Deaktivieren Sie „Im abgesicherten Sicherungsmodus arbeiten“ und klicken Sie auf „OK“.

**Verlassen aller Sicherungsmodi**

Sie können die Befehlszeilenschnittstelle verwenden, um den abgesicherten Sicherungsmodus (Snapshot-Modus) für AEM Forms zu deaktivieren bzw. die aktuelle Sicherungsmodussitzung (rollierender Modus) zu beenden. Sie können die Administrationskonsole nicht verwenden, um den rollierenden Sicherungsmodus zu deaktivieren. Im rollierenden Sicherungsmodus sind die Steuerelemente von „Backup-Dienstprogramme“ in Administration Console deaktiviert. Verwenden Sie entweder den API-Aufruf oder den Befehl „LCBackupMode“.

1. Zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` wechseln.
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.

   >[!NOTE]
   >
   >Legen Sie den Ordner JAVA_HOME wie im entsprechenden Kapitel für Ihren Anwendungsserver in beschrieben fest. [Vorbereiten der Installation von AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_de)*.*

1. Führen Sie den folgenden Befehl in einer einzelnen Zeile durch:

   * (Windows) `LCBackupMode.cmd leaveContinuousCoverage [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `]`
   * (Linux®, UNIX®) `LCBackupMode.sh leaveContinuousCoverage [-Host=`*Host-Name* `] [-port=`*Port-Nummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `]`

     Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

     `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

     `port` ist der Port, über den AEM Forms auf dem Anwendungs-Server ausgeführt wird.

     `user` ist der Benutzername der oder des AEM Forms-Admins.

     `password` ist das Kennwort der oder des AEM Forms-Admins.

     `leaveContinuousCoverage` Verwenden Sie diese Option, um den kontinuierlichen Sicherungsmodus vollständig zu deaktivieren.

   >[!NOTE]
   >
   >Solange der Backup-Modus deaktiviert ist, kann die kontinuierliche Sicherung nicht erneut hergestellt werden. Alle Änderungen, die währenddessen vorgenommen werden, werden nicht gespeichert.

   >[!NOTE]
   >
   >Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, sind der Snapshot-Backup-Modus und der rollierende Backup-Modus nicht möglich.

   Weitere Informationen zum Wechseln in den Sicherungsmodus über die Befehlszeilenschnittstelle finden Sie in der Readme-Datei im Verzeichnis „BackupRestoreCommandline“.
