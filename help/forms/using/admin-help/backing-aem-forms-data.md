---
title: Sichern der AEM Forms-Daten
seo-title: Sichern der AEM Forms-Daten
description: In diesem Dokument werden die Schritte zum Erstellen einer Onlinesicherung (bei laufendem Betrieb) der AEM Forms-Datenbank, des globalen Dokumentenspeichers sowie des Stammordners für Inhalte beschrieben.
seo-description: In diesem Dokument werden die Schritte zum Erstellen einer Onlinesicherung (bei laufendem Betrieb) der AEM Forms-Datenbank, des globalen Dokumentenspeichers sowie des Stammordners für Inhalte beschrieben.
uuid: ac7856be-e3b7-4b81-b8b9-fc909b5907b4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 52187196-b091-4683-85ae-cc7c250dee54
exl-id: 536615a4-ab42-4b72-83b1-fad110b011ee
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 92%

---

# Sichern der AEM Forms-Daten {#backing-up-the-aem-forms-data}

In diesem Abschnitt werden die Schritte zum Erstellen einer Onlinesicherung (bei laufendem Betrieb) der AEM Forms-Datenbank, des globalen Dokumentenspeichers sowie des Stammordners für Inhalte beschrieben.

Im Anschluss an die Installation und Bereitstellung von AEM Forms in Produktionsbereichen muss der Datenbankadministrator eine vollständige Erstsicherung (nicht bei laufendem Betrieb) der Datenbank durchführen. Für diese Sicherung muss die Datenbank heruntergefahren werden. Anschließend müssen in regelmäßigen Abständen differenzielle oder inkrementelle Sicherungen (im laufenden Betrieb) der Datenbank erfolgen.

Damit eine erfolgreiche Sicherung und Wiederherstellung sichergestellt ist, muss jederzeit eine Systemabbildsicherung verfügbar sein. So können Sie bei Eintritt von Datenverlusten die gesamte Umgebung in einem konsistenten Zustand wiederherstellen.

Durch das gleichzeitige Sichern von GDS, AEM-Repository und des Stammordners für Inhalte zusammen mit der Datenbank wird die Synchronisierung dieser Systeme im Falle einer Wiederherstellung erleichtert.

Das in diesem Abschnitt beschriebene Sicherungsverfahren erfordert, dass Sie in den abgesicherten Sicherungsmodus wechseln, bevor Sie die AEM Forms-Datenbank, AEM-Repository, GDS-Ordner sowie den Stammordner für Inhalte sichern. Nach Abschluss der Sicherung müssen Sie den abgesicherten Sicherungsmodus beenden. Der abgesicherte Sicherungsmodus dient zum Markieren dauerhaft genutzter Dokumente im globalen Dokumentenspeicher. Dies stellt sicher, dass die automatisierte Dateibereinigungsfunktion abgelaufene Dateien erst löscht, nachdem der abgesicherte Sicherungsmodus beendet wurde. Dies ist erforderlich, damit die Sicherung des globalen Dokumentenspeichers mit einer Datenbanksicherung synchron bleibt.

Die Häufigkeit der Sicherung des Ordners des globalen Dokumentenspeichers hängt von der Verwendung von AEM Forms und der Verfügbarkeit der Sicherungszeitfenster ab. Das Sicherungszeitfenster kann durch lang andauernde Prozesse beeinflusst werden, weil diese ggf. über Tage hinweg ausgeführt werden. Wenn Sie laufend Dateien in diesem Ordner ändern, hinzufügen und entfernen, sollte der globale Dokumentenspeicher öfter gesichert werden.

Wenn die Datenbank (wie im vorhergehenden Abschnitt beschrieben) in einem Protokollmodus ausgeführt wird, müssen die Datenbankprotokolle ebenfalls häufig gesichert werden, damit sie im Falle eines Datenträgerfehlers zum Wiederherstellen der Datenbank verwendet werden können.

>[!NOTE]
>
>Dateien, auf die nicht verwiesen wird, können nach dem Wiederherstellungsvorgang ggf. noch immer im Ordner des globalen Dokumentenspeichers vorhanden sein. Für dieses Problem gibt es derzeit noch keine Lösung.

## Datenbank, GDS, AEM-Repository sowie Stammordner für Inhalte sichern {#back-up-the-database-gds-aem-repository-and-content-storage-root-directories}

Sie müssen AEM Forms entweder in den abgesicherten Sicherungsmodus (Snapshot-Modus) oder in den kontinuierlichen Sicherungsmodus versetzen. Bevor Sie festlegen, dass AEM Forms in einen der Sicherungsmodi versetzt wird, stellen Sie Folgendes sicher:

* Überprüfen Sie die Systemversion und notieren Sie Patches und Aktualisierungen, die seit der letzten vollständigen Systemabbildsicherung angewendet wurden.
* Stellen Sie bei Verwendung kontinuierlicher Sicherungen bzw. Sicherungen im Snapshot-Modus sicher, dass die Datenbank mit den ordnungsgemäßen Protokolliereinstellungen für Datenbanksicherungen im laufenden Betrieb konfiguriert ist. (Siehe[ AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).)

Zusätzlich dazu sollten Sie die folgenden Richtlinien für den Sicherungs-/Wiederherstellungsprozess beachten.

* Sichern Sie den Ordner des globalen Dokumentenspeichers mithilfe eines Sicherungsprogramms des Betriebssystems oder eines anderen Anbieters. (Siehe [GDS-Speicherort](/help/forms/using/admin-help/files-back-recover.md#gds-location).)
* (Optional) Sichern Sie den Stammordner für Inhalte mithilfe eines Sicherungsprogramms des Betriebssystems oder eines anderen Anbieters. (Siehe [Speicherort des Stammordners für Inhalte (eigenständige Umgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-stand-alone-environment)) oder [Speicherort des Stammordners für Inhalte (Clusterumgebung)](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-location-clustered-environment).)
* Sichern Sie   Autoren- und Veröffentlichungsinstanzen ( crx -repository backup).

   Um die Correspondence Management Solution zu sichern, führen Sie die Schritte für Autor- und Veröffentlichungsinstanzen durch wie hier beschrieben: [Backup and Restore](/help/sites-administering/backup-and-restore.md).

   Berücksichtigen Sie folgende Punkte, wenn Sie Autor- und Veröffentlichungsinstanzen sichern:

   * Stellen Sie sicher, dass die Sicherung für  Autoren- und Veröffentlichungsinstanzen werden synchronisiert, um gleichzeitig zu starten. Obwohl Sie Autoren- und Veröffentlichungsinstanzen während der Sicherung weiterhin verwenden können, wird empfohlen, während des Backups kein Asset zu veröffentlichen, um nicht erfasste Änderungen zu vermeiden. Warten Sie bis die Sicherung der Autor- und Veröffentlichungsinstanzen beendet ist, bevor Sie neue Elemente veröffentlichen.
   * Die vollständige Sicherung des Autorknotens umfasst die Sicherung der Daten von Forms Manager und AEM Forms Workspace.
   * Workbench-Entwickler können an ihre Prozesse weiterhin lokal bearbeiten. Sie sollten während der Sicherung jedoch keine neuen Prozesse bereitstellen.
   * Die Entscheidung über die Dauer der einzelnen Sicherungssitzungen (für den kontinuierlichen Sicherungsmodus) sollte auf der Gesamtzeit basieren, die zum Sichern aller Daten in AEM Forms erforderlich ist (DB, GDS, AEM-Repository und alle anderen zusätzlichen benutzerdefinierten Daten).

Sie sollten die AEM Forms-Datenbank samt Transaktionsprotokollen sichern. (Siehe[ AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).) Weitere Informationen finden Sie in den für Ihre Datenbank zutreffenden Knowledgebase-Artikeln:

* [Oracle-Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403624)
* [Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403625)
* [Microsoft SQL Server-Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403623)
* [DB2 Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403626)

Diese Artikel bieten Anleitungen zu grundlegenden Datenbankfeatures für die Sicherung und Wiederherstellung von Daten. Sie sind nicht als vollständige technische Leitfäden für die Sicherungs- und Wiederherstellungsfunktionen bestimmter Datenbankhersteller konzipiert. Es handelt sich lediglich um allgemeine Informationen zu Befehlen, die zum Erstellen einer zuverlässigen Datenbanksicherungsstrategie für Ihre AEM Forms-Anwendungsdaten erforderlich sind.

>[!NOTE]
>
>Die Sicherung des globalen Dokumentenspeichers darf erst nach Abschluss der Datenbanksicherung erfolgen. Wenn die Datenbanksicherung nicht abgeschlossen ist, sind Ihre Daten nicht synchron.

### In den Sicherungsmodus wechseln  {#entering-the-backup-modes}

Sie können entweder Administration Console, den Befehl „LCBackupMode“ oder die mit der AEM Forms-Installation verfügbare API verwenden, um den Sicherungsmodus zu aktivieren und zu deaktivieren. Beachten Sie, dass die Administration Console-Option für die kontinuierliche Sicherung nicht verfügbar ist. Sie sollten daher entweder die Befehlszeilenoption oder die API verwenden. <!-- Fix broken link For information about using the API to enter and leave backup modes, see AEM forms API Reference on Help and Tutorials page. -->

>[!NOTE]
>
>Wenn Sie SSL auf dem Formularserver konfiguriert haben, können Sie den Formularserver nicht mithilfe des Skripts „LCBackupMode.CMD“ im Sicherungsmodus ausführen.

**Administration Console verwenden, um den abgesicherten Sicherungsmodus zu aktivieren**

1. Melden Sie sich bei Administration Console an.
1. Klicken Sie in auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Sicherungsdienstprogramme“.
1. Aktivieren Sie „Im abgesicherten Sicherungsmodus arbeiten“ und klicken Sie auf „OK“.

   Diese Methode versetzt AEM Forms dauerhaft in den Sicherungsmodus (ohne Zeitlimit) und verwendet den Snapshot-Modus, d. h. nicht den kontinuierlichen Sicherungsmodus.

**Befehlszeilenoption verwenden, um den abgesicherten Sicherungsmodus zu aktivieren**

Sie können die `LCBackupMode`-Skripte verwenden, um AEM Forms über die Befehlszeilenschnittstelle in den abgesicherten Sicherungsmodus zu versetzen.

1. Legen Sie „ADOBE_LIVECYCLE“ fest und starten Sie den Anwendungsserver.
1. Gehen Sie zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` .
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.
1. Führen Sie an der Befehlszeile den folgenden Befehl in einer einzelnen Zeile aus:

   * (Windows) `LCBackupMode.cmd enter [-Host=`*Hostname* `] [-port=`*Anschlussnummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `] [-label=`*Beschriftungsname* `] [-timeout=`*Sekunden* `]`
   * (Linux, UNIX) `LCBackupMode.sh enter [-host=`*Hostname* `] [-port=`*Anschlussnummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `] [-label=`*Beschriftungsname* `]`

   Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

   `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

   `port` ist der WebServices-Anschluss des Anwendungsservers, auf dem AEM Forms ausgeführt wird.

   `user` ist der Benutzername des AEM Forms-Administrators.

   `password` ist das Kennwort des AEM Forms-Administrators.

   `label` ist die Textbeschriftung dieser Sicherung (kann eine beliebige Zeichenfolge sein).

   `timeout` ist die Anzahl der Sekunden, nach denen der Sicherungsmodus automatisch beendet wird. Es kann zwischen 0 und 10.080 liegen. Bei 0 gibt es für den Sicherungsmodus kein Zeitlimit (Standardeinstellung).

   Weitere Informationen zum Wechseln in den Sicherungsmodus über die Befehlszeilenschnittstelle finden Sie in der Datei „Bitte-lesen“ im Ordner „BackupRestoreCommandline“.

### Sicherungsmodus deaktivieren  {#leaving-backup-modes}

Sie können entweder Administration Console oder die Befehlszeilenoption verwenden, um den Sicherungsmodus zu deaktivieren.

**Den abgesicherten Sicherungsmodus (Snapshot-Modus) deaktivieren**

Führen Sie die folgenden Schritte aus, um AEM Forms über Administration Console aus dem abgesicherten Sicherungsmodus (Snapshot-Modus) zu nehmen.

1. Melden Sie sich bei Administration Console an.
1. Klicken Sie in auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Sicherungsdienstprogramme“.
1. Deaktivieren Sie „Im abgesicherten Sicherungsmodus arbeiten“ und klicken Sie auf „OK“.

**Alle Sicherungsmodi deaktivieren**

Sie können die Befehlszeilenschnittstelle verwenden, um den abgesicherten Sicherungsmodus (Snapshot-Modus) für AEM Forms zu deaktivieren bzw. die aktuelle Sicherungsmodussitzung (kontinuierlicher Modus) zu beenden. Beachten Sie, dass Sie Administration Console nicht verwenden können, um den kontinuierlichen Sicherungsmodus zu deaktivieren. Während des kontinuierlichen Sicherungsmodus sind die Steuerungen der Sicherungsdienstprogramme in Administration Console deaktiviert. Sie müssen entweder den API-Aufruf oder den „LCBackupMode“-Befehl verwenden.

1. Gehen Sie zum Ordner `*[aem-forms root]*/sdk/misc/Foundation/BackupRestoreCommandline` .
1. Bearbeiten Sie je nach Betriebssystem das Skript `LCBackupMode.cmd` oder `LCBackupMode.sh`, um für Ihr System geeignete Standardwerte anzugeben.

   >[!NOTE]
   >
   >Sie müssen den Ordner „JAVA_HOME“ so festlegen, wie es im entsprechenden Kapitel für Ihren Anwendungsserver in [Vorbereiten der AEM Forms-Installation beschrieben ist](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63)*.*

1. Rufen Sie den folgenden Befehl in einer einzelnen Zeile auf:

   * (Windows) `LCBackupMode.cmd leaveContinuousCoverage [-Host=`*Hostname* `] [-port=`*Anschlussnummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `]`
   * (Linux, UNIX) `LCBackupMode.sh leaveContinuousCoverage [-Host=`*Hostname* `] [-port=`*Anschlussnummer* `] [-user=`*Benutzername* `] [-password=`*Kennwort* `]`

      Die Parameter in den vorherigen Befehlen sind wie folgt definiert:

      `Host` ist der Name des Hosts, auf dem AEM Forms ausgeführt wird.

      `port` ist der Anschluss, an dem AEM Forms auf dem Anwendungsserver ausgeführt wird.

      `user` ist der Benutzername des AEM Forms-Administrators.

      `password` ist das Kennwort des AEM Forms-Administrators.

      `leaveContinuousCoverage` Verwenden Sie diese Option, um den kontinuierlichen Sicherungsmodus vollständig zu deaktivieren.
   >[!NOTE]
   >
   >Während der Zeit, in der der Sicherungsmodus deaktiviert ist, kann die kontinuierliche Sicherung nicht erneut hergestellt werden. Alle Änderungen, die währenddessen vorgenommen werden, werden nicht gespeichert.

   >[!NOTE]
   >
   >Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, sind der Snapshot-Sicherungsmodus und der kontinuierliche Sicherungsmodus nicht möglich.

   Weitere Informationen zum Wechseln in den Sicherungsmodus über die Befehlszeilenschnittstelle finden Sie in der Datei „Bitte-lesen“ im Ordner „BackupRestoreCommandline“.
