---
title: Wiederherstellen der AEM Forms-Daten
seo-title: Recovering the AEM forms data
description: In diesem Dokument werden die Schritte beschrieben, die zum Wiederherstellen der AEM Forms-Daten erforderlich sind.
seo-description: This document describes the steps required to recover the AEM forms data.
uuid: b5735196-5a8d-4358-884f-e9b8d8f4f682
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4e093114-219b-4018-9530-9002eb665448
exl-id: 9e648bab-9284-4fda-abb4-8bd7cd085981
source-git-commit: 3d713021ac410ca2925a282c5dfca98ed4e483ee
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 99%

---

# Wiederherstellen der AEM Forms-Daten {#recovering-the-aem-forms-data}

In diesem Abschnitt werden die Schritte beschrieben, die zum Wiederherstellen der AEM Forms-Daten erforderlich sind. Siehe auch [Besondere Hinweise für Sicherung und Wiederherstellung](/help/forms/using/admin-help/backup-recovery-strategy-aem-forms.md#special-considerations-for-backup-and-recovery).

>[!NOTE]
>
>Der Computer, auf dem Datenbank, globaler Dokumentenspeicher, AEM-Repository und Stammordner für Inhalte wiederhergestellt werden, muss denselben DNS-Namen wie der ursprüngliche haben.

AEM Forms sollte nach einem der folgenden Ereignisse zuverlässig wiederhergestellt werden:

**Datenträgerausfall:** Zum Wiederherstellen des Datenbankinhalts ist das letzte Sicherungsmedium erforderlich.

**Datenbeschädigung:** Dateisysteme zeichnen erfolgte Transaktionen nicht auf und können unbeabsichtigt benötigte Prozessdaten überschreiben.

**Benutzerfehler:** Die Wiederherstellung ist auf die Daten beschränkt, die von der Datenbank zur Verfügung gestellt werden. Falls die Daten gespeichert wurden und verfügbar sind, wird die Wiederherstellung vereinfacht.

**Stromausfall, Systemabsturz:** Dateisystem-APIs sind bei unerwarteten Systemausfällen häufig nicht stabil. Wenn ein Stromausfall oder ein Systemabsturz auftritt, ist der in der Datenbank gespeicherte Dokumentinhalt wahrscheinlich aktueller als in einem Dateisystem gespeicherte Inhalte.

Wenn Sie den kontinuierlichen Sicherungsmodus verwenden, befinden Sie sich nach der Wiederherstellung noch im Sicherungsmodus. Wenn Sie dagegen den Snapshot-Sicherungsmodus verwenden, befinden Sie sich nach der Wiederherstellung nicht im Sicherungsmodus.

Beim Wiederherstellen von einem Backup auf ein neues System können die folgenden Konfigurationen unterschiedlich sein. Hiervon sollte eine erfolgreiche Wiederherstellung der AEM Forms-Anwendung unberührt bleiben:

* IP-Adresse
* Physische Systemkonfiguration (CPUs, Festplatte, Speicher)
* Speicherort des globalen Dokumentenspeichers

>[!NOTE]
>
>Das Backup des Stammordners für Inhalte muss an dem Speicherort des Ordners wiederhergestellt werden, der während der Konfiguration von Content Services festgelegt wurde.

Wenn ein einzelner Knoten eines Clusters mit mehreren Knoten ausgefallen ist, die verbliebenen Cluster-Knoten aber ordnungsgemäß weiter funktionieren, führen Sie das Wiederherstellungsverfahren für einen einzelnen Cluster-Knoten durch.

## Wiederherstellen der AEM Forms-Daten {#recover-the-aem-forms-data}

1. Beenden Sie die AEM Forms-Dienste und den Anwendungs-Server, falls er ausgeführt wird.
1. Erstellen Sie bei Bedarf das physische System aus einem Systembild neu. Zum Beispiel ist dieser Schritt möglicherweise nicht erforderlich, wenn der Grund für die Wiederherstellung ein fehlerhafter Datenbank-Server ist.
1. Wenden Sie Patches oder Aktualisierungen auf AEM Forms an, die seit der Erstellung des Bildes angewendet wurden. Diese Informationen wurden im Sicherungsverfahren erfasst. Bei AEM Forms müssen Patches entsprechend dem Patch-Level zum Zeitpunkt der Systemsicherung angewendet werden.
1. (WebSphere® Anwendungs-Server) Wenn Sie eine neue Instanz des WebSphere® Anwendungs-Servers wiederherstellen, führen Sie den Befehl „restoreConfig.bat/sh“ aus.
1. Zum Wiederherstellen der AEM Forms-Datenbank müssen Sie zuerst einen Datenbankwiederherstellungsvorgang unter Verwendung der Datenbanksicherungsdateien ausführen und anschließend die Protokolle zum Wiederholen von Transaktionen auf die wiederhergestellte Datenbank anwenden. (Siehe [AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).) Weitere Informationen finden Sie in einem dieser Knowledgebase-Artikel:

   * [DB2](/help/forms/using/admin-help/files-back-recover.md#db2)
   * [Oracle-Backup und Wiederherstellung für AEM Forms](/help/forms/using/admin-help/files-back-recover.md#oracle)
   * [Microsoft](/help/forms/using/admin-help/files-back-recover.md#sql-server)
   * [MySQL-Backup und Wiederherstellung für AEM Forms](/help/forms/using/admin-help/files-back-recover.md#mysql)

1. Stellen Sie das Verzeichnis des globalen Dokumentenspeichers (GDS) wieder her, indem Sie zunächst den Inhalt des GDS-Verzeichnisses auf der vorhandenen Installation von AEM Forms löschen und dann den Inhalt des GDS-Verzeichnisses aus dem gesicherten GDS kopieren. Falls Sie den Speicherort des GDS-Verzeichnisses geändert haben, lesen Sie [Ändern des GDS-Speicherorts während der Wiederherstellung](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).
1. Benennen Sie den wiederherzustellenden Ordner des globalen Dokumentenspeichers wie in den folgenden Beispielen gezeigt um:

   >[!NOTE]
   >
   >Wenn der Ordner „/restore“ bereits vorhanden ist, sichern Sie ihn zuerst und löschen ihn dann, bevor Sie den Ordner „/backup“, der die neuesten Daten enthält, umbenennen.

   * (JBoss®) Benennen Sie `[appserver root]/server/'server'/svcnative/DocumentStorage/backup` um in:

     `[appserver root]/server/'server'/svcnative/DocumentStorage/restore`.

   * (WebLogic) Benennen Sie `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/backup` um in:

     `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/restore`.

   * (WebSphere®) Benennen Sie `[appserver root]/installedApps/adobe/'server'/DocumentStorage/backup` um in:

     `[appserver root]/installedApps/adobe/'server'/DocumentStorage/restore`.

1. Stellen Sie den Stammordner für Inhalte wieder her, indem Sie zunächst den Inhalt des Stammordners für Inhalte aus der bestehenden Installation von AEM Forms löschen und dann den Inhalt wiederherstellen, indem Sie die Aufgaben für eigenständige bzw. Cluster-Umgebungen ausführen:

   >[!NOTE]
   >
   >Das Backup des Stammordners für Inhalte muss an dem Speicherort des Stammordners für Inhalte wiederhergestellt werden, der während der Konfiguration von Content Services (nicht mehr unterstützt) festgelegt wurde.

   **Eigenständig:** Während des Wiederherstellungsprozesses werden alle Ordner wiederhergestellt, die gesichert wurden. Wenn diese Ordner wiederhergestellt werden und der Ordner „/backup-lucene-indexes“ vorhanden ist, benennen Sie ihn in „/lucene-indexes“ um. Andernfalls sollte der Ordner „/lucene-indexes“ bereits vorhanden sein, sodass keine Aktion erforderlich ist.

   **Cluster:** Während des Wiederherstellungsprozesses werden alle Ordner wiederhergestellt, die gesichert wurden. Um den Indexstammordner wiederherzustellen, führen Sie die folgenden Schritte für jeden Knoten des Clusters aus:

   * Löschen Sie den gesamten Inhalt des Indexstammordners.
   * Wenn der Ordner „/backup-lucene-indexes“ vorhanden ist, kopieren Sie den Inhalt des Ordners „*Stammordner für Inhalte*/backup-lucene-indexes“ in den Indexstammordner und löschen Sie den Ordner „*Stammordner für Inhalte*/backup-lucene-indexes“.
   * Wenn der Ordner „/lucene-indexes“ vorhanden ist, kopieren Sie den Inhalt des Ordners „*Stammordner für Inhalte*/lucene-indexes“ in den Indexstammordner.

1. Wiederherstellen des CRX-Repositorys.

   * **Eigenständig**

     *Autor- und Veröffentlichungsinstanzen wiederherstellen*: Bei einem Systemausfall können Sie das Repository im letzten gesicherten Zustand wiederherstellen, indem Sie die hier beschrieben Schritte ausführen: [Backup and Restore.](https://helpx.adobe.com/de/experience-manager/kb/CRXBackupAndRestoreProcedure.html)

     Bei der vollständigen Wiederherstellung des Authoring-Knotens werden auch die Daten von Forms Manager und AEM Forms Workspace wiederhergestellt.

   * **Cluster**

     Für die Wiederherstellung in einer Clusterumgebung finden Sie weitere Informationen unter [Strategie für Sicherung und Wiederherstellung in einer Cluster-Umgebung](/help/forms/using/admin-help/strategy-backup-restore-clustered-environment.md#strategy-for-backup-and-restore-in-a-clustered-environment).

1. Löschen Sie alle temporären AEM Forms-Dateien, die im Ordner „java.io.temp“ oder im temporären Adobe-Ordner erstellt wurden.
1. Starten Sie AEM Forms (siehe [Starten und Stoppen von Services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))<!-- BROKEN LINK and the application server(s) (see [Maintaining the Application Server](/help/forms/using/admin-help/topics/maintaining-the-application-server.md))-->.

## Ändern des GDS-Speicherorts während der Wiederherstellung {#changing-the-gds-location-during-recovery}

Falls der globale Dokumentenspeicher an einem anderen als dem ursprünglichen Speicherort wiederhergestellt wird, führen Sie das Skript „LCSetGDS“ aus, um den globalen Dokumentenspeicher auf den neuen Speicherort festzulegen. Das Skript befindet sich im Ordner `[aem-forms root]\sdk\misc\Foundation\SetGDSCommandline`. Das Skript benötigt die zwei Parameter `defaultGDS` und `newGDS`. Lesen Sie die Datei `ReadMe.txt` im selben Ordner für Anweisungen zum Ausführen des Skripts.

>[!NOTE]
>
>Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, müssen Sie den Speicherort des globalen Dokumentenspeichers nicht ändern.

>[!NOTE]
>
>Dies ist der einzige Umstand, unter dem dieses Skript zum Ändern des Speicherorts für den Ordner des globalen Dokumentenspeichers verwendet werden sollte. Um den Speicherorts für den Ordner des globalen Dokumentenspeichers zu ändern, während AEM Forms ausgeführt wird, verwenden Sie Administration Console. (Siehe [Allgemeine AEM Forms-Einstellungen konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).)

>[!NOTE]
>
>Die Komponentenbereitstellung schlägt unter Windows fehl, wenn sich der Ordner des globalen Dokumentenspeichers im Stammordner des Laufwerks befindet (z. B. D:\). Beim globalen Dokumentenspeicher müssen Sie daher sicherstellen, dass sich der Ordner nicht im Stammordners des Laufwerks befindet, sondern in einem Unterverzeichnis. Der Ordner sollte beispielsweise „D:\GDS“ und nicht einfach „D:\“ lauten.

## Wiederherstellen des globalen Dokumentenspeichers in einer Cluster-Umgebung {#recovering-the-gds-to-a-clustered-environment}

Um den Speicherort des globalen Dokumentenspeichers in einer Cluster-Umgebung zu ändern, fahren Sie den gesamten Cluster herunter und führen Sie das Skript „LCSetGDS“ auf einem einzelnen Knoten des Clusters aus. (Siehe [Ändern des GDS-Speicherorts während der Wiederherstellung](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).) Starten Sie nur diesen Knoten. Sobald dieser Knoten vollständig gestartet ist, können andere Knoten im Cluster sicher gestartet werden. Die Knoten verweisen dann korrekt auf den neuen globalen Dokumentenspeicher.

>[!NOTE]
>
>Wenn Sie nicht sicherstellen können, dass ein Knoten vollständig gestartet wird, bevor Sie andere Knoten starten, müssen Sie auf jedem Knoten im Cluster das Skript „LCSetGDS“ ausführen, bevor Sie den Cluster starten.
