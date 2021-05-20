---
title: Wiederherstellen der AEM Forms-Daten
seo-title: Wiederherstellen der AEM Forms-Daten
description: In diesem Dokument werden die zum Wiederherstellen der AEM Forms-Daten erforderlichen Schritte beschrieben.
seo-description: In diesem Dokument werden die zum Wiederherstellen der AEM Forms-Daten erforderlichen Schritte beschrieben.
uuid: b5735196-5a8d-4358-884f-e9b8d8f4f682
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4e093114-219b-4018-9530-9002eb665448
exl-id: 9e648bab-9284-4fda-abb4-8bd7cd085981
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 95%

---

# Wiederherstellen der AEM Forms-Daten {#recovering-the-aem-forms-data}

In diesem Abschnitt werden die zum Wiederherstellen der AEM Forms-Daten erforderlichen Schritte beschrieben. Weitere Informationen finden Sie außerdem unter [Besondere Überlegungen zur Sicherung und Wiederherstellung](/help/forms/using/admin-help/backup-recovery-strategy-aem-forms.md#special-considerations-for-backup-and-recovery).

>[!NOTE]
>
>Der Computer, auf dem Datenbank, GDS, AEM-Repository und Stammordner für Inhalte wiederhergestellt werden, muss denselben DNS-Namen wie ursprünglich haben.

AEM Forms sollte nach einem der folgenden Ereignisse zuverlässig wiederhergestellt werden:

**Datenträgerausfall:** Zum Wiederherstellen des Datenbankinhalts ist das letzte Sicherungsmedium erforderlich.

**Datenbeschädigung:** Dateisysteme zeichnen erfolgte Transaktionen nicht auf und können unbeabsichtigt benötigte Prozessdaten überschreiben.

**Benutzerfehler:** Die Wiederherstellung ist auf die Daten beschränkt, die von der Datenbank zur Verfügung gestellt werden. Falls die Daten gespeichert wurden und verfügbar sind, wird die Wiederherstellung vereinfacht.

**Stromausfall, Systemabsturz:** Dateisystem-APIs sind bei unerwarteten Systemausfällen häufig nicht stabil. Bei einem Stromausfall oder Systemabsturz ist es wahrscheinlicher, dass in der Datenbank gespeicherte Dokumentinhalte aktuell sind als in einem Dateisystem gespeicherte Inhalte.

Wenn Sie im kontinuierlichen Sicherungsmodus arbeiten, befinden Sie sich auch nach der Wiederherstellung in diesem Modus. Wenn Sie im Snapshot-Sicherungsmodus arbeiten, befinden Sie sich nach der Wiederherstellung nicht im Sicherungsmodus.

Beim Wiederherstellen aus einer Sicherung auf ein neues System können die folgenden Konfigurationen abweichen. Hiervon sollte eine erfolgreiche Wiederherstellung der AEM Forms-Anwendung unberührt bleiben:

* IP-Adresse
* Physische Systemkonfiguration (Prozessoren, Festplatte, Arbeitsspeicher)
* Speicherort des globalen Dokumentenspeichers

>[!NOTE]
>
>Die Sicherung des Stammordners für Inhalte muss an dem Speicherort des Ordners wiederhergestellt werden, der während der Content Services-Konfiguration festgelegt wurde.

Wenn ein einzelner Knoten eines Clusters mit mehreren Knoten ausgefallen ist, die verbliebenen Clusterknoten aber ordnungsgemäß weiter funktionieren, führen Sie das Wiederherstellungsverfahren für einen einzelnen Clusterknoten durch.

## Wiederherstellen der AEM Forms-Daten {#recover-the-aem-forms-data}

1. Beenden Sie die AEM Forms-Dienste und den Anwendungsserver, falls er ausgeführt wird.
1. Erstellen Sie bei Bedarf das physische System aus einem Systemabbild neu. Dieses Schritt ist ggf. nicht erforderlich, wenn der Grund für die Wiederherstellung ein fehlerhafter Datenbankserver ist.
1. Wenden Sie Patches oder Aktualisierungen für AEM Forms an, die seit der Erstellung des Abbilds angewendet wurden. Diese Informationen wurden im Sicherungsverfahren erfasst. Auf AEM Forms müssen Patches entsprechend dem Patchlevel zum Zeitpunkt der Systemsicherung angewendet werden.
1. (WebSphere Application Server) Wenn Sie die Wiederherstellung auf eine neue Instanz von WebSphere Application Server durchführen, führen Sie den Befehl „restoreConfig.bat/sh“ aus.
1. Zum Wiederherstellen der AEM Forms-Datenbank müssen Sie zuerst einen Datenbankwiederherstellungsvorgang unter Verwendung der Datenbanksicherungsdateien ausführen und anschließend die Protokolle zum Wiederholen von Transaktionen auf die wiederhergestellte Datenbank anwenden. (Siehe [AEM Forms-Datenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database).) Weitere Informationen finden Sie in einem dieser Knowledgebase-Artikel:

   * [Oracle-Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403624)
   * [Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403625)
   * [Microsoft SQL Server-Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403623)
   * [DB2 Backup und Wiederherstellung für AEM Forms](https://www.adobe.com/go/kb403626)

1. Stellen Sie den Ordner des globalen Dokumentenspeichers wieder her, indem Sie zuerst den Inhalt des Ordners des globalen Dokumentenspeichers in der vorhandenen Installation von AEM Forms löschen und dann den Inhalt des globalen Dokumentenspeichers aus dem gesicherten Ordner des globalen Dokumentenspeichers kopieren. Wenn Sie den Speicherort des Ordners des globalen Dokumentenspeichers geändert haben, lesen Sie [Speicherort des globalen Dokumentenspeichers während der Wiederherstellung ändern](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).
1. Benennen Sie den Sicherungsordner des globalen Dokumentspeichers, der wiederhergestellt werden soll, wie in den folgenden Beispielen gezeigt um:

   >[!NOTE]
   >
   >Wenn den Ordner „/restore“ bereits vorhanden ist, sichern Sie ihn zuerst und löschen ihn dann, bevor Sie den Ordner „/backup“, der die neuesten Daten enthält, umbenennen.

   * (JBoss) Benennen Sie `[appserver root]/server/'server'/svcnative/DocumentStorage/backup` um in:

      `[appserver root]/server/'server'/svcnative/DocumentStorage/restore`.

   * (WebLogic) Benennen Sie `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/backup` um in:

      `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/restore`.

   * (WebSphere) Benennen Sie `[appserver root]/installedApps/adobe/'server'/DocumentStorage/backup` um in:

      `[appserver root]/installedApps/adobe/'server'/DocumentStorage/restore`.

1. Stellen Sie den Stammordner für Inhalte wieder her, indem Sie zuerst den Inhalt des Stammordners für Inhalte in der vorhandenen Installation von AEM Forms löschen und dann unter Ausführung der Schritte für eigenständige oder Clusterumgebungen wiederherstellen:

   >[!NOTE]
   >
   >Die Sicherung des Stammordners für Inhalte muss an dem Speicherort des Stammordners für Inhalte wiederhergestellt werden, der während der Content Services-Konfiguration (nicht mehr unterstützt) festgelegt wurde.

   **Eigenständig:** Während des Wiederherstellungsprozesses werden alle Ordner wiederhergestellt, die gesichert wurden. Wenn diese Ordner wiederhergestellt werden und der Ordner „/backup-lucene-indexes“ vorhanden ist, benennen Sie ihn in „/lucene-indexes“ um. Andernfalls sollte der Ordner „/lucene-indexes“ bereits vorhanden sein, sodass keine Aktion erforderlich ist.

   **Cluster:** Während des Wiederherstellungsprozesses werden alle Ordner wiederhergestellt, die gesichert wurden. Führen Sie zum Wiederherstellen des Indexstammordners die folgenden Schritte auf jedem Knoten des Clusters aus:

   * Löschen Sie den gesamten Inhalt des Indexstammordners.
   * Wenn der Ordner „/backup-lucene-indexes“ vorhanden ist, kopieren Sie den Inhalt des Ordners „*Stammordner für Inhalte*/backup-lucene-indexes“ in den Indexstammordner und löschen Sie den Ordner „*Stammordner für Inhalte*/backup-lucene-indexes“.
   * Wenn der Ordner „/lucene-indexes“ vorhanden ist, kopieren Sie den Inhalt des Ordners „*Stammordner für Inhalte*/lucene-indexes“ in den Indexstammordner.

1. Wiederherstellen der CRX-Repository

   * **Eigenständig**

      *Autor- und Veröffentlichungsinstanzen wiederherstellen*: Bei einem Systemausfall können Sie das Repository im letzten gesicherten Zustand wiederherstellen, indem Sie die hier beschrieben Schritte ausführen: [Backup and Restore.](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)

      Bei der vollständigen Wiederherstellung des Autorknotens werden auch die Daten von Forms Manager und AEM Forms Workspace wiederhergestellt.

   * **Cluster**

      Für die Wiederherstellung in einer Clusterumgebung finden Sie weitere Informationen unter [Strategie für Sicherung und Wiederherstellung in einer Clusterumgebung](/help/forms/using/admin-help/strategy-backup-restore-clustered-environment.md#strategy-for-backup-and-restore-in-a-clustered-environment).

1. Löschen Sie alle temporären AEM Forms-Dateien, die im Ordner „java.io.temp“ oder im temporären Adobe-Ordner erstellt wurden.
1. Starten Sie AEM Formulare (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))<!-- BROKEN LINK and the application server(s) (see [Maintaining the Application Server](/help/forms/using/admin-help/topics/maintaining-the-application-server.md))-->.

## Speicherort des globalen Dokumentenspeichers während der Wiederherstellung ändern {#changing-the-gds-location-during-recovery}

Falls der globale Dokumentenspeicher an anderen als dem ursprünglichen Speicherort wiederhergestellt wird, führen Sie das Skript „LCSetGDS“ aus, um den globalen Dokumentenspeicher auf den neuen Speicherort festzulegen. Das Skript befindet sich im Ordner `[aem-forms root]\sdk\misc\Foundation\SetGDSCommandline` . Das Skript akzeptiert zwei Parameter: `defaultGDS` und `newGDS`. Lesen Sie die Datei `ReadMe.txt` im selben Ordner für Anweisungen zum Ausführen des Skripts.

>[!NOTE]
>
>Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, müssen Sie den GDS-Speicherort nicht ändern.

>[!NOTE]
>
>Dies ist der einzige Umstand, unter dem dieses Skript zum Ändern des Speicherorts für den Ordner des globalen Dokumentenspeichers verwendet werden sollte. Um den Speicherorts für den Ordner des globalen Dokumentenspeichers zu ändern, während AEM Forms ausgeführt wird, verwenden Sie Administration Console. (Siehe [Allgemeine AEM Forms-Einstellungen konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).)

>[!NOTE]
>
>Die Komponentenbereitstellung schlägt unter Windows fehl, wenn sich der Ordner des globalen Dokumentenspeichers im Stammordner des Laufwerks befindet (z. B. D:\) Beim globalen Dokumentenspeicher müssen Sie sicherstellen, dass sich der Ordner nicht im Stammordner des Laufwerks befindet, sondern in einem Unterordner. Der Ordner sollte beispielsweise „D:\GDS“ und nicht einfach „D:\“ lauten.

## Globalen Dokumentenspeicher in einer Clusterumgebung wiederherstellen  {#recovering-the-gds-to-a-clustered-environment}

Fahren Sie zum Ändern des Speicherortes des globalen Dokumentenspeichers den gesamten Cluster herunter und führen Sie das Skript LCSetGDS auf einem einzelnen Knoten des Clusters aus. (Siehe [Speicherort des globalen Dokumentenspeichers während der Wiederherstellung ändern](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).) Starten Sie nur diesen Knoten. Sobald dieser Knoten vollständig gestartet ist, können andere Knoten im Cluster sicher gestartet werden. Die Knoten verweisen dann korrekt auf den neuen Speicherort des globalen Dokumentenspeichers.

>[!NOTE]
>
>Wenn der vollständige Abschluss des Starts eines einzelnen Knotens vor dem Starten anderer Knoten nicht sichergestellt werden kann, müssen Sie das Skript LCSetGDS auf allen Knoten im Cluster ausführen, bevor Sie den Cluster starten.
