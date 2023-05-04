---
title: Wiederherstellen der AEM Forms-Daten
seo-title: Recovering the AEM forms data
description: In diesem Dokument werden die Schritte beschrieben, die zum Wiederherstellen der AEM Formulardaten erforderlich sind.
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
ht-degree: 21%

---

# Wiederherstellen der AEM Forms-Daten {#recovering-the-aem-forms-data}

In diesem Abschnitt werden die Schritte beschrieben, die zum Wiederherstellen der AEM Formulardaten erforderlich sind. Siehe auch [Besondere Hinweise für Sicherung und Wiederherstellung](/help/forms/using/admin-help/backup-recovery-strategy-aem-forms.md#special-considerations-for-backup-and-recovery).

>[!NOTE]
>
>Die Ordner &quot;Datenbank&quot;, &quot;Ordner des globalen Dokumentenspeichers&quot;, &quot;AEM Repository&quot;und &quot;Stammordner für Inhalte&quot;müssen auf einem Computer wiederhergestellt werden, der denselben DNS-Namen wie das Original hat.

AEM Formulare sollten zuverlässig von folgenden Fehlern wiederhergestellt werden:

**Datenträgerausfall:** Zum Wiederherstellen des Datenbankinhalts ist das letzte Sicherungsmedium erforderlich.

**Datenbeschädigung:** Dateisysteme zeichnen erfolgte Transaktionen nicht auf und können unbeabsichtigt benötigte Prozessdaten überschreiben.

**Benutzerfehler:** Die Wiederherstellung ist auf die Daten beschränkt, die von der Datenbank zur Verfügung gestellt werden. Falls die Daten gespeichert wurden und verfügbar sind, wird die Wiederherstellung vereinfacht.

**Stromausfall, Systemabsturz:** Dateisystem-APIs sind bei unerwarteten Systemausfällen häufig nicht stabil. Wenn ein Stromausfall oder ein Systemabsturz auftritt, ist der in der Datenbank gespeicherte Dokumentinhalt wahrscheinlich aktueller als der in einem Dateisystem gespeicherte Inhalt.

Wenn Sie den kontinuierlichen Sicherungsmodus verwenden, befinden Sie sich nach der Wiederherstellung noch im Sicherungsmodus. Wenn Sie den Snapshot-Sicherungsmodus verwenden, befinden Sie sich nach der Wiederherstellung nicht im Sicherungsmodus.

Beim Wiederherstellen von einem Backup auf ein neues System können die folgenden Konfigurationen unterschiedlich sein. Dieser Unterschied sollte sich nicht auf eine erfolgreiche Wiederherstellung der AEM Forms-Anwendung auswirken:

* IP-Adresse
* Physische Systemkonfiguration (CPUs, Festplatte, Speicher)
* GDS-Speicherort

>[!NOTE]
>
>Die Sicherung des Stammordners für Inhalte muss an dem Speicherort des Ordners wiederhergestellt werden, der während der Konfiguration von Content Services festgelegt wurde.

Wenn ein einzelner Knoten eines Clusters mit mehreren Knoten fehlschlägt und die verbleibenden Knoten des Clusters ordnungsgemäß funktionieren, führen Sie das Wiederherstellungsverfahren für einzelne Clusterknoten durch.

## AEM Formulardaten wiederherstellen {#recover-the-aem-forms-data}

1. Beenden Sie die AEM Forms-Dienste und den Anwendungsserver bei Ausführung.
1. Erstellen Sie bei Bedarf das physische System aus einem Systembild neu. Dieser Schritt ist beispielsweise möglicherweise nicht erforderlich, wenn der Grund für die Wiederherstellung ein fehlerhafter Datenbankserver ist.
1. Wenden Sie Patches oder Aktualisierungen auf AEM Formulare an, die seit der Erstellung des Bildes angewendet wurden. Diese Informationen wurden im Sicherungsverfahren erfasst. AEM Formulare müssen auf dieselbe Patch-Ebene gepatcht werden wie bei der Sicherung des Systems.
1. (WebSphere® Application Server) Wenn Sie auf eine neue Instanz von WebSphere® Application Server wiederherstellen, führen Sie den Befehl restoreConfig.bat/sh aus.
1. Zum Wiederherstellen der AEM Forms-Datenbank müssen Sie zuerst einen Datenbankwiederherstellungsvorgang unter Verwendung der Datenbanksicherungsdateien ausführen und anschließend die Protokolle zum Wiederholen von Transaktionen auf die wiederhergestellte Datenbank anwenden. (Siehe [AEM Formulardatenbank](/help/forms/using/admin-help/files-back-recover.md#aem-forms-database). Weitere Informationen finden Sie in einem dieser Knowledge Base-Artikel:

   * [DB2](/help/forms/using/admin-help/files-back-recover.md#db2)
   * [Oracle-Backup und Wiederherstellung für AEM Forms](/help/forms/using/admin-help/files-back-recover.md#oracle)
   * [Microsoft](/help/forms/using/admin-help/files-back-recover.md#sql-server)
   * [Backup und Wiederherstellung für AEM Forms](/help/forms/using/admin-help/files-back-recover.md#mysql)

1. Rufen Sie den Ordner des globalen Dokumentenspeichers ab, indem Sie zunächst den Inhalt des Ordners des globalen Dokumentenspeichers in der bestehenden Installation AEM Formulare löschen und dann den Inhalt des Ordners des globalen Dokumentenspeichers aus dem gesicherten Ordner des globalen Dokumentenspeichers kopieren. Informationen zum Speicherort des Ordners des globalen Dokumentenspeichers finden Sie unter [Speicherort des globalen Dokumentenspeichers während der Wiederherstellung ändern](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery).
1. Benennen Sie den wiederherzustellenden Ordner des globalen Dokumentenspeichers wie in den folgenden Beispielen gezeigt um:

   >[!NOTE]
   >
   >Wenn der Ordner &quot;/restore&quot;bereits vorhanden ist, sichern Sie ihn und löschen Sie ihn dann, bevor Sie den Ordner &quot;/backup&quot;umbenennen, der die neuesten Daten enthält.

   * (JBoss®) Umbenennen `[appserver root]/server/'server'/svcnative/DocumentStorage/backup` an:

      `[appserver root]/server/'server'/svcnative/DocumentStorage/restore`.

   * (WebLogic) Benennen Sie `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/backup` um in:

      `[appserverdomain]/'server'/adobe/AEMformsserver/DocumentStorage/restore`.

   * (WebSphere®) Umbenennen `[appserver root]/installedApps/adobe/'server'/DocumentStorage/backup` an:

      `[appserver root]/installedApps/adobe/'server'/DocumentStorage/restore`.

1. Stellen Sie den Stammordner für Inhalte wieder her, indem Sie zunächst den Inhalt des Stammordners für Inhalte aus der bestehenden Installation von AEM Formularen löschen und dann den Inhalt wiederherstellen, indem Sie die Aufgaben für eigenständige oder Clusterumgebungen ausführen:

   >[!NOTE]
   >
   >Die Sicherung des Stammordners für Inhalte muss an dem Speicherort des Stammordners für Inhalte wiederhergestellt werden, der während der Konfiguration von Content Services (nicht mehr unterstützt) festgelegt wurde.

   **Eigenständig:** Während des Wiederherstellungsprozesses werden alle Ordner wiederhergestellt, die gesichert wurden. Wenn diese Ordner wiederhergestellt werden und der Ordner /backup-lucene-indexes vorhanden ist, benennen Sie ihn in /lucene-indexes um. Andernfalls sollte der Ordner lucene-indexes bereits vorhanden sein und es ist keine Aktion erforderlich.

   **Cluster:** Während des Wiederherstellungsprozesses werden alle Ordner wiederhergestellt, die gesichert wurden. Um den Indexstammordner wiederherzustellen, führen Sie die folgenden Schritte für jeden Knoten des Clusters aus:

   * Löschen Sie alle Inhalte im Indexstammverzeichnis.
   * Wenn der Ordner /backup-lucene-indexes vorhanden ist, kopieren Sie den Inhalt des Ordners *Stammordner für Inhalte* Ordner &quot;/backup-lucene-indexes&quot;in den Ordner &quot;Index Root&quot;und löschen Sie die *Stammordner für Inhalte* Ordner &quot;/backup-lucene-indexes&quot;.
   * Wenn der Ordner /lucene-indexes vorhanden ist, kopieren Sie den Inhalt der *Stammordner für Inhalte* Ordner /lucene-indexes in den Indexstammordner.

1. Wiederherstellen/Wiederherstellen des CRX-Repositorys.

   * **Eigenständig**

      *Autor- und Veröffentlichungsinstanzen wiederherstellen*: Bei einem Systemausfall können Sie das Repository im letzten gesicherten Zustand wiederherstellen, indem Sie die hier beschrieben Schritte ausführen: [Backup and Restore.](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html)

      Bei der vollständigen Wiederherstellung des Autorknotens werden auch die Daten von Forms Manager und AEM Forms Workspace wiederhergestellt.

   * **Cluster**

      Informationen zur Wiederherstellung in einer Clusterumgebung finden Sie unter [Strategie für Sicherung und Wiederherstellung in einer Clusterumgebung](/help/forms/using/admin-help/strategy-backup-restore-clustered-environment.md#strategy-for-backup-and-restore-in-a-clustered-environment).

1. Löschen Sie alle temporären AEM Formulare, die im Ordner &quot;java.io.temp&quot;oder im temporären Ordner der Adobe erstellt wurden.
1. Starten Sie AEM Forms (siehe [Starten und Stoppen von Services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))<!-- BROKEN LINK and the application server(s) (see [Maintaining the Application Server](/help/forms/using/admin-help/topics/maintaining-the-application-server.md))-->.

## Speicherort des globalen Dokumentenspeichers während der Wiederherstellung ändern {#changing-the-gds-location-during-recovery}

Wenn der globale Dokumentenspeicher an einem anderen Speicherort als dem ursprünglichen Speicherort wiederhergestellt wird, führen Sie das Skript &quot;LCSetGDS&quot;aus, um den globalen Dokumentenspeicher auf den neuen Speicherort festzulegen. Das Skript befindet sich im Ordner `[aem-forms root]\sdk\misc\Foundation\SetGDSCommandline`. Das Skript benötigt die zwei Parameter `defaultGDS` und `newGDS`. Lesen Sie die Datei `ReadMe.txt` im selben Ordner für Anweisungen zum Ausführen des Skripts.

>[!NOTE]
>
>Wenn Sie die Dokumentenspeicherung in der Datenbank aktiviert haben, müssen Sie den Speicherort des globalen Dokumentenspeichers nicht ändern.

>[!NOTE]
>
>Dies ist der einzige Umstand, unter dem Sie dieses Skript verwenden sollten, um den Speicherort des globalen Dokumentenspeichers zu ändern. Um den Speicherorts für den Ordner des globalen Dokumentenspeichers zu ändern, während AEM Forms ausgeführt wird, verwenden Sie Administration Console. (Siehe [Allgemeine AEM Forms-Einstellungen konfigurieren](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).)

>[!NOTE]
>
>Die Komponentenbereitstellung schlägt unter Windows fehl, wenn sich der Ordner des globalen Dokumentenspeichers im Stammordner des Laufwerks befindet (z. B. D:\). Beim globalen Dokumentenspeicher müssen Sie sicherstellen, dass sich der Ordner nicht im Stammverzeichnis des Laufwerks befindet, sondern in einem Unterverzeichnis. Der Ordner sollte beispielsweise D:\GDS and not simply D:\ lauten.

## Wiederherstellen des globalen Dokumentenspeichers in einer Clusterumgebung {#recovering-the-gds-to-a-clustered-environment}

Um den Speicherort des globalen Dokumentenspeichers in einer Clusterumgebung zu ändern, fahren Sie den gesamten Cluster herunter und führen Sie das Skript LCSetGDS auf einem einzelnen Knoten des Clusters aus. (Siehe [Speicherort des globalen Dokumentenspeichers während der Wiederherstellung ändern](recovering-aem-forms-data.md#changing-the-gds-location-during-recovery). Starten Sie nur diesen Knoten. Wenn dieser Knoten vollständig gestartet ist, können andere Knoten im Cluster sicher gestartet werden und verweisen ordnungsgemäß auf den neuen globalen Dokumentenspeicher.

>[!NOTE]
>
>Wenn Sie nicht sicherstellen können, dass ein Knoten vollständig gestartet wird, bevor Sie andere Knoten starten, müssen Sie das Skript LCSetGDS auf jedem Knoten im Cluster ausführen, bevor Sie den Cluster starten.
