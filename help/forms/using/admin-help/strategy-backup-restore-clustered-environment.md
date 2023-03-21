---
title: Strategie für Sicherung und Wiederherstellung in einer Cluster-Umgebung
seo-title: Strategy for backup and restore in a clustered environment
description: Wenn Ihre AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank speichert, müssen Sie eine Strategie implementieren, um diese Daten zu sichern und sicherzustellen, dass sie mit den AEM Formulardaten synchronisiert bleiben.
seo-description: If your AEM forms implementation stores additional custom data in a different database, you must implement a strategy to back up this data ensuring that it remains in sync with the AEM forms data.
uuid: c29b989c-30ed-4a8e-bab8-9b7746291a33
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c332985b-4556-4056-961a-fce2356da88d
exl-id: 98c96349-f253-475f-b646-352269814a38
source-git-commit: 4fa868f3ae4778d3a637e90b91f7c5909fe5f8aa
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 21%

---

# Strategie für Sicherung und Wiederherstellung in einer Cluster-Umgebung {#strategy-for-backup-and-restore-in-a-clustered-environment}

>[!NOTE]
>
>Wenn Ihre AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank speichert, müssen Sie eine Strategie implementieren, um diese Daten zu sichern und sicherzustellen, dass sie mit den AEM Formulardaten synchronisiert bleiben. Außerdem muss die Anwendung so konzipiert sein, dass sie robust genug ist, um ein Szenario zu handhaben, in dem die zusätzlichen Datenbanken nicht mehr synchronisiert werden. Es wird dringend empfohlen, alle Datenbankoperationen im Kontext einer Transaktion durchzuführen, um einen konsistenten Zustand zu gewährleisten.

Sie müssen die folgenden Teile des AEM Forms-Systems sichern, um sich von einem Fehler wiederherzustellen:

* Von AEM Formularen verwendete Datenbank
* GDS mit langlebigen Daten und anderen persistenten Dokumenten
* AEM Datenbank (crx-repository)

>[!NOTE]
>
>Sie müssen alle anderen Daten sichern, die von Ihrer AEM Forms-Einrichtung verwendet werden, z. B. Kundenschriftarten, Verbindungsdaten usw.

## Sichern einer Clusterumgebung {#back-up-a-clustered-environment}

In diesem Thema werden die folgenden Strategien zum Sichern von AEM Forms-Clusterumgebungen erläutert:

* Offlinesicherung mit Ausfallzeiten
* Offline-Sicherung ohne Ausfallzeiten (Sichern eines sekundären Knotens, der heruntergefahren wurde)
* Online-Backup ohne Ausfallzeit, aber mit Verzögerung
* Sichern Sie die Eigenschaftendatei des Bootstrap.

### Offlinesicherung mit Ausfallzeiten {#offline-backup-with-downtime}

1. Fahren Sie den gesamten Cluster und die zugehörigen Dienste herunter. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie auf jedem Knoten die Datenbank, den globalen Dokumentenspeicher und die Connectoren. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Um AEM Repository offline zu sichern, führen Sie die folgenden Schritte aus:

   1. Sichern Sie für jeden Clusterknoten die Datei, die die Clusterknoten-ID enthält.
   1. Sichern Sie alle Dateien eines beliebigen sekundären Cluster-Knotens, einschließlich der Unterordner.
   1. Sichern Sie Repository/System-ID jedes Clusterknotens separat.

   Ausführliche Anweisungen finden Sie unter [Sicherung und Wiederherstellung](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html).

1. Sichern Sie alle anderen Daten, z. B. Kundenschriftarten.
1. Starten Sie den Cluster erneut.

### Offlinesicherung ohne Ausfallzeiten {#offline-backup-with-no-downtime}

1. Wechseln Sie in den kontinuierlichen Sicherungsmodus. (siehe [Wechseln der Sicherungsmodi](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Verlassen Sie den kontinuierlichen Sicherungsmodus nach einer Wiederherstellung.

1. Beenden Sie alle sekundären Knoten des Clusters bezüglich AEM. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie auf jedem Knoten die Datenbank, den globalen Dokumentenspeicher und die Connectoren. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Um AEM Repository offline zu sichern, führen Sie die folgenden Schritte aus:

   1. Sichern Sie für jeden Clusterknoten die Datei, die die Clusterknoten-ID enthält.
   1. Sichern Sie alle Dateien eines beliebigen sekundären Cluster-Knotens, einschließlich der Unterordner.
   1. Sichern Sie Repository/System.id jedes Clusterknotens separat.

   Ausführliche Anweisungen finden Sie unter [Sicherung und Wiederherstellung](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html).

1. Sichern Sie alle anderen Daten, z. B. Kundenschriftarten.
1. Starten Sie den Cluster erneut.

### Online-Backup ohne Ausfallzeit, aber mit Verzögerung {#online-backup-with-no-downtime-but-delay-in-response}

1. Wechseln Sie in den kontinuierlichen Sicherungsmodus. (siehe [Wechseln der Sicherungsmodi](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Verlassen Sie den kontinuierlichen Sicherungsmodus nach einer Wiederherstellung.

1. Beenden Sie alle sekundären Knoten des Clusters bezüglich AEM. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie auf jedem Knoten die Datenbank, den globalen Dokumentenspeicher und die Connectoren. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Um AEM Repository online zu sichern, führen Sie die folgenden Schritte aus:

   1. Sichern Sie für jeden Clusterknoten die Datei, die &quot;cluster_node.id&quot;enthält.
   1. Sichern Sie Repository/System.id jedes Cluster-Knotens separat.
   1. Führen Sie auf einem beliebigen Sekundärknoten ein Online-Backup des Repositorys durch. Detaillierte Schritte siehe „Online-Backup“.

1. Sichern Sie alle anderen Daten, z. B. Kundenschriftarten.
1. Starten Sie den Cluster erneut.

### Sichern Sie die Eigenschaftendatei des Bootstrap. {#back-up-the-bootstrap-properties-file}

Wenn Sie einen AEM-Cluster erstellen, wird auf dem Anwendungsserver eine Eigenschaftsdatei für alle Sekundärknoten erstellt. Es wird empfohlen, die Eigenschaftendatei des Bootstrap zu sichern. Sie finden die Datei unter folgendem Speicherort auf Ihrem Anwendungsserver:

* JBoss®: im Verzeichnis &quot;BIN&quot;
* WebLogic: im Domain-Ordner
* WebSphere®: im Profilverzeichnis

Sichern Sie die Datei für das Disaster Recovery-Szenario AEM sekundären Knotens und ersetzen Sie sie bei der Wiederherstellung am angegebenen Speicherort auf dem Anwendungsserver.

## Wiederherstellung in einer Clusterumgebung {#recovery-in-a-clustered-environment}

Wenn der gesamte Cluster oder ein einzelner Knoten fehlschlägt, stellen Sie ihn mithilfe der Sicherung wieder her.

Beenden Sie für die Wiederherstellung eines einzelnen Knotens den einzelnen Knoten und führen Sie das Wiederherstellungsverfahren für einen einzelnen Knoten aus.

Führen Sie die folgenden Schritte aus, falls der gesamte Cluster aufgrund von Fehlern wie Datenbankabstürzen fehlschlägt. Die Wiederherstellung hängt von der verwendeten Sicherungsmethode ab.

### Wiederherstellen eines einzelnen Knotens {#restoring-a-single-node}

1. Stoppen Sie den beschädigten Knoten.

   >[!NOTE]
   >
   >Wenn der beschädigte Knoten ein AEM-Primärknoten ist, fahren Sie den gesamten Clusterknoten herunter.

1. Erstellen Sie das physische System aus einem Systembild neu.
1. Wenden Sie Patches oder Aktualisierungen auf AEM Formulare an, die seit der Erstellung des Bildes angewendet wurden. Diese Informationen wurden während des Sicherungsverfahrens erfasst. AEM Formulare müssen auf derselben Patch-Ebene wiederhergestellt werden, auf der das System gesichert wurde.
1. (*Optional*) Wenn alle anderen Knoten problemlos funktionieren, ist es möglich, dass auch das AEM Repository beschädigt ist. In diesem Fall wird in der Datei error.log des AEM-Repositorys eine Meldung zur Aufhebung der Synchronisierung des Repositorys angezeigt.

   Führen Sie die folgenden Schritte aus, um das Repository wiederherzustellen.

   >[!NOTE]
   >
   >Wenn eine komprimierte CRX-Repository-Sicherung online durchgeführt wurde, dekomprimieren Sie sie an einem beliebigen Ort und folgen Sie dem Offline-Wiederherstellungsprozess.

   1. Löschen Sie die Ordner &quot;repository&quot;, &quot;shared&quot;, &quot;version&quot;und &quot;workspaces&quot;im Ordner &quot;clusterNode&quot;des Knotens.
   1. Stellen Sie die Sicherung des Clusterknotens (einschließlich Unterverzeichnissen) auf dem Knoten wieder her.
   1. Löschen Sie die Datei clusterNode/revision.log auf dem Knoten.
   1. Löschen Sie die .lock-Datei auf dem Knoten, falls vorhanden.
   1. Löschen Sie repository/system.id auf dem Knoten, falls vorhanden.
   1. Löschen Sie die Dateien &amp;ast;&amp;ast;/listener.properties auf dem Knoten, falls vorhanden.
   1. Stellen Sie repository/cluster_node.id für einzelne Clusterknoten wieder her.

>[!NOTE]
>
>Beachten Sie die folgenden Punkte:

* Wenn der fehlgeschlagene Knoten ein AEM-Primärknoten war, kopieren Sie den gesamten Inhalt des sekundären Repository-Ordners („crx-repository\crx.0000“, wobei „0000“ eine beliebige Zahl sein kann) in den Repository-Ordner „crx-repository\“ und löschen Sie den sekundären Repository-Ordner.
* Bevor Sie einen Clusterknoten neu starten, stellen Sie sicher, dass Sie das Repository „/clustered.txt“ auf dem Primärknoten löschen.
* Stellen Sie sicher, dass der primäre Knoten zuerst gestartet wird und nach dem Start andere Knoten starten.

### Wiederherstellen des gesamten Clusters {#restoring-the-entire-cluster}

1. Beenden Sie alle Clusterknoten.
1. Erstellen Sie das physische System von einem Systemabbild neu.
1. Wenden Sie Patches oder Aktualisierungen auf AEM AEM-Formulare an, die seit der Erstellung des Bildes angewendet wurden. Diese Informationen wurden in Schritt 1 des Sicherungsverfahrens erfasst. AEM Formulare müssen auf derselben Patch-Ebene wiederhergestellt werden, auf der das System gesichert wurde.
1. Stellen Sie die Datenbank, den globalen Dokumentenspeicher und Connectoren wieder her.
1. Führen Sie die folgenden Schritte aus, um das AEM Repository offline wiederherzustellen:

   >[!NOTE]
   >
   >Wenn eine komprimierte CRX-Repository-Sicherung online durchgeführt wurde, dekomprimieren Sie sie an einem beliebigen Ort und folgen Sie dem Offline-Wiederherstellungsprozess.

   1. Löschen Sie auf allen Clusterknoten die Ordner &quot;repository&quot;, &quot;shared&quot;, &quot;version&quot;und &quot;workspaces&quot;im Ordner &quot;clusterNode&quot;.
   1. Löschen Sie alle Dateien und Ordner im freigegebenen Ordner.
   1. Stellen Sie die Sicherung des Clusterknotens (einschließlich Unterverzeichnissen) auf einem Clusterknoten wieder her.
   1. Kopieren Sie alle Dateien des wiederhergestellten Clusterknotens auf alle anderen Clusterknoten. Danach enthält jeder Clusterknoten dieselben Daten.
   1. Löschen Sie die Datei clusterNode/revision.log auf allen Clusterknoten.
   1. Löschen Sie die .lock-Datei auf allen Clusterknoten, falls vorhanden.
   1. Löschen Sie repository/system.id alle Clusterknoten, falls vorhanden.
   1. Löschen Sie die Dateien „*/listener.properties“ auf allen Cluster-Knoten, falls vorhanden.
   1. Stellen Sie repository/cluster_node.id für einzelne Clusterknoten wieder her.

>[!NOTE]
>
>Beachten Sie die folgenden Punkte:

* Wenn der ausgefallene Knoten ein AEM-Primärknoten war, kopieren Sie den gesamten Inhalt aus dem sekundären Repository-Ordner (er hat die Form „crx-repository\crx.0000“, wobei „0000“ beliebigen Ziffern entsprechen kann) in den Repository-Ordner „crx-repository\“.
* Bevor Sie einen Cluster-Knoten neu starten, achten Sie darauf, dass Sie das Repository „/clustered.txt“ vom primären Knoten löschen.
* Stellen Sie sicher, dass der primäre Knoten zuerst gestartet wird und nach dem Start andere Knoten starten.

## Sichern und Wiederherstellen des Veröffentlichungsknotens der Correspondence Management Solution {#back-up-and-restore-correspondence-management-solution-publish-node}

Der Veröffentlichungsknoten hat in einer Cluster-Umgebung keine Primär-/Sekundärbeziehung.. Sie können eine Sicherung eines beliebigen Herausgeberknotens durchführen, indem Sie Folgendes durchführen: [Sicherung und Wiederherstellung](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html).

### Wiederherstellen eines einzelnen Veröffentlichungsknotens {#recover-a-single-publisher-node}

1. Beenden Sie den Knoten, der abgerufen werden muss, und führen Sie keine Veröffentlichungsaktivität durch, bis der Knoten wieder aktiv ist.
1. Wiederherstellen des Veröffentlichungsknotens mithilfe von [Wiederherstellen des Backups](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html).

### Wiederherstellen eines Clusters {#recover-a-cluster}

1. Beenden Sie den Cluster.
1. Wiederherstellen des Veröffentlichungsknotens mithilfe von [Wiederherstellen des Backups](https://helpx.adobe.com/experience-manager/kb/CRXBackupAndRestoreProcedure.html).
1. Starten Sie den primären Knoten und anschließend den sekundären Knoten des Autoren-Clusters.
