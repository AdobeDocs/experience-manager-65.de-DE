---
title: Strategie für Sicherung und Wiederherstellung in einer Cluster-Umgebung
description: Wenn Ihre AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank speichert, müssen Sie eine Strategie implementieren, um diese Daten zu sichern und sicherzustellen, dass sie mit den AEM Forms-Daten synchronisiert bleiben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 98c96349-f253-475f-b646-352269814a38
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 100%

---

# Strategie für Sicherung und Wiederherstellung in einer Cluster-Umgebung {#strategy-for-backup-and-restore-in-a-clustered-environment}

>[!NOTE]
>
>Wenn Ihre AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank speichert, müssen Sie eine Strategie implementieren, um diese Daten zu sichern und sicherzustellen, dass sie mit den AEM Forms-Daten synchronisiert bleiben. Außerdem muss die Anwendung so konzipiert sein, dass sie robust genug ist, um ein Szenario zu handhaben, in dem die zusätzlichen Datenbanken nicht mehr synchronisiert werden. Es wird dringend empfohlen, alle Datenbankoperationen im Kontext einer Transaktion durchzuführen, um einen konsistenten Zustand zu gewährleisten.

Sie müssen die folgenden Teile des AEM Forms-Systems sichern, um im Falle eines Fehlers eine Systemwiederherstellung durchführen zu können.

* Von AEM-Formularen verwendete Datenbank
* Globaler Dokumentenspeicher mit langlebigen Daten und anderen persistenten Dokumenten
* AEM-Datenbank (crx-repository)

>[!NOTE]
>
>Sie müssen alle anderen Daten sichern, die von Ihrer AEM Forms-Einrichtung verwendet werden, z. B. Kundenschriftarten, Verbindungsdaten usw.

## Sichern einer Cluster-Umgebung {#back-up-a-clustered-environment}

In diesem Thema werden die folgenden Strategien zum Sichern von AEM Forms-Cluster-Umgebungen erläutert:

* Offline-Sicherung mit Ausfallzeit
* Offline-Sicherung ohne Ausfallzeiten (Sichern eines sekundären Knotens, der heruntergefahren wurde)
* Online-Sicherung ohne Ausfallzeit, aber mit Verzögerung
* Sichern Sie die Eigenschaftendatei des Bootstrap.

### Offline-Sicherung mit Ausfallzeit {#offline-backup-with-downtime}

1. Fahren Sie das gesamte Cluster und die zugehörigen Dienste herunter. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie auf jedem Knoten die Datenbank, den globalen Dokumentenspeicher und die Connectoren. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Um das AEM-Repository offline zu sichern, führen Sie die folgenden Schritte aus:

   1. Sichern Sie für jeden Cluster-Knoten die Datei, die die Cluster-Knoten-ID enthält.
   1. Sichern Sie alle Dateien eines beliebigen sekundären Cluster-Knotens, einschließlich der Unterordner.
   1. Sichern Sie Repository/System-ID jedes Clusterknotens separat.

   Ausführliche Anweisungen finden Sie unter [Sichern und Wiederherstellen](https://helpx.adobe.com/de/experience-manager/kb/CRXBackupAndRestoreProcedure.html).

1. Sichern Sie alle anderen Daten, z. B. Kundenschriftarten.
1. Starten Sie das Cluster erneut.

### Offline-Sicherung ohne Ausfallzeiten {#offline-backup-with-no-downtime}

1. Wechseln Sie in den kontinuierlichen Sicherungsmodus. (siehe [Wechseln in die Sicherungsmodi](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Verlassen Sie den kontinuierlichen Sicherungsmodus nach einer Wiederherstellung.

1. Beenden Sie die sekundären Knoten des Clusters mit Bezug zu AEM. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie auf jedem Knoten die Datenbank, den globalen Dokumentenspeicher und die Connectoren. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Um das AEM-Repository offline zu sichern, führen Sie die folgenden Schritte aus:

   1. Sichern Sie für jeden Cluster-Knoten die Datei, die die Cluster-Knoten-ID enthält.
   1. Sichern Sie alle Dateien eines beliebigen sekundären Cluster-Knotens, einschließlich der Unterordner.
   1. Sichern Sie Repository/System.id jedes Clusterknotens separat.

   Ausführliche Anweisungen finden Sie unter [Sichern und Wiederherstellen](https://helpx.adobe.com/de/experience-manager/kb/CRXBackupAndRestoreProcedure.html).

1. Sichern Sie alle anderen Daten, z. B. Kundenschriftarten.
1. Starten Sie das Cluster erneut.

### Online-Sicherung ohne Ausfallzeit, aber mit Verzögerung {#online-backup-with-no-downtime-but-delay-in-response}

1. Wechseln Sie in den kontinuierlichen Sicherungsmodus. (siehe [Wechseln in die Sicherungsmodi](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Verlassen Sie den kontinuierlichen Sicherungsmodus nach einer Wiederherstellung.

1. Beenden Sie die sekundären Knoten des Clusters mit Bezug zu AEM. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie auf jedem Knoten die Datenbank, den globalen Dokumentenspeicher und die Connectoren. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Um das AEM-Repository online zu sichern, führen Sie die folgenden Schritte aus:

   1. Sichern Sie für jeden Cluster-Knoten die Datei, die „cluster_node.id“ enthält.
   1. Sichern Sie Repository/System.id jedes Cluster-Knotens separat.
   1. Führen Sie auf einem beliebigen Sekundärknoten ein Online-Backup des Repositorys durch. Detaillierte Schritte siehe „Online-Backup“.

1. Sichern Sie alle anderen Daten, z. B. Kundenschriftarten.
1. Starten Sie das Cluster erneut.

### Sichern Sie die Eigenschaftendatei des Bootstrap. {#back-up-the-bootstrap-properties-file}

Wenn Sie einen AEM-Cluster erstellen, wird auf dem Anwendungsserver eine Eigenschaftsdatei für alle Sekundärknoten erstellt. Es wird empfohlen, die Eigenschaftendatei des Bootstrap zu sichern. Sie finden die Datei unter folgendem Speicherort auf Ihrem Anwendungsserver:

* JBoss®: im Verzeichnis „BIN“
* WebLogic: im Domain-Ordner
* WebSphere®: im Profilverzeichnis

Sie müssen die Datei für das Notfallwiederherstellungsszenario des AEM-Sekundärknotens sichern und sie an dem angegebenen Speicherort auf dem Anwendungsserver ersetzen, wenn sie wiederhergestellt wird.

## Wiederherstellung in einer Cluster-Umgebung {#recovery-in-a-clustered-environment}

Wenn der gesamte Cluster oder ein einzelner Knoten fehlschlägt, stellen Sie ihn mithilfe der Sicherung wieder her.

Um einen einzelnen Knoten wiederherzustellen, beenden Sie den einzelnen Knoten und führen Sie das Wiederherstellungsverfahren für einen einzelnen Knoten aus.

Führen Sie die folgenden Schritte aus, wenn der gesamte Cluster aufgrund von Fehlern, wie z. B. einem Datenbankabsturz, ausfällt. Die Wiederherstellung hängt von der verwendeten Sicherungsmethode ab.

### Wiederherstellen eines einzelnen Knotens {#restoring-a-single-node}

1. Beenden Sie den beschädigten Knoten.

   >[!NOTE]
   >
   >Wenn der beschädigte Knoten ein AEM-Primärknoten ist, fahren Sie den gesamten Clusterknoten herunter.

1. Erstellen Sie das physische System aus einem Systembild neu.
1. Wenden Sie Patches oder Aktualisierungen auf AEM Forms an, die seit der Erstellung des Bildes angewendet wurden. Diese Informationen wurden während des Sicherungsverfahrens erfasst. AEM Forms müssen auf derselben Patch-Ebene wiederhergestellt werden, auf der das System gesichert wurde.
1. (*Optional*) Wenn alle anderen Knoten problemlos funktionieren, ist es möglich, dass auch das AEM-Repository beschädigt ist. In diesem Fall wird in der Datei error.log des AEM-Repositorys eine Meldung zur Aufhebung der Synchronisierung des Repositorys angezeigt.

   Führen Sie die folgenden Schritte aus, um das Repository wiederherzustellen.

   >[!NOTE]
   >
   >Wenn eine komprimierte CRX-Repository-Sicherung online durchgeführt wurde, dekomprimieren Sie sie an einem beliebigen Ort und folgen Sie dem Offline-Wiederherstellungsprozess.

   1. Löschen Sie die Ordner „repository“, „shared“, „version“ und „workspaces“ im Ordner „clusterNode“ des Knotens.
   1. Stellen Sie die Sicherung des Cluster-Knotens (einschließlich Unterverzeichnissen) auf dem Knoten wieder her.
   1. Löschen Sie die Datei clusterNode/revision.log auf dem Knoten.
   1. Löschen Sie die .lock-Datei auf dem Knoten, falls vorhanden.
   1. Löschen Sie repository/system.id auf dem Knoten, falls vorhanden.
   1. Löschen Sie die Dateien &amp;ast;&amp;ast;/listener.properties auf dem Knoten, falls vorhanden.
   1. Stellen Sie repository/cluster_node.id für einzelne Cluster-Knoten wieder her.

>[!NOTE]
>
>Bedenken Sie die folgenden Punkte:

* Wenn der fehlgeschlagene Knoten ein AEM-Primärknoten war, kopieren Sie den gesamten Inhalt des sekundären Repository-Ordners („crx-repository\crx.0000“, wobei „0000“ eine beliebige Zahl sein kann) in den Repository-Ordner „crx-repository\“ und löschen Sie den sekundären Repository-Ordner.
* Bevor Sie einen Clusterknoten neu starten, stellen Sie sicher, dass Sie das Repository „/clustered.txt“ auf dem Primärknoten löschen.
* Stellen Sie sicher, dass der primäre Knoten zuerst gestartet wird, und starten Sie die anderen Knoten erst, wenn er vollständig hochgefahren ist.

### Wiederherstellen des gesamten Clusters {#restoring-the-entire-cluster}

1. Beenden Sie alle Cluster-Knoten.
1. Erstellen Sie das physische System von einem Systemabbild neu.
1. Wenden Sie Patches oder Aktualisierungen auf AEM Forms an, die seit der Erstellung des Bildes angewendet wurden. Diese Informationen wurden in Schritt 1 des Backups erfasst. AEM Forms müssen auf derselben Patch-Ebene wiederhergestellt werden, auf der das System gesichert wurde.
1. Stellen Sie die Datenbank, den globalen Dokumentenspeicher und Connectoren wieder her.
1. Führen Sie die folgenden Schritte aus, um das AEM-Repository offline wiederherzustellen:

   >[!NOTE]
   >
   >Wenn eine komprimierte CRX-Repository-Sicherung online durchgeführt wurde, dekomprimieren Sie sie an einem beliebigen Ort und folgen Sie dem Offline-Wiederherstellungsprozess.

   1. Löschen Sie auf allen Clusterknoten die Ordner „repository“, „shared“, „version“ und „workspaces“ im Ordner „clusterNode“.
   1. Löschen Sie alle Dateien und Ordner im freigegebenen Ordner.
   1. Stellen Sie die Sicherung des Cluster-Knotens (einschließlich Unterverzeichnissen) auf einem Cluster-Knoten wieder her.
   1. Kopieren Sie alle Dateien des wiederhergestellten Cluster-Knotens auf alle anderen Cluster-Knoten. Danach enthält jeder Cluster-Knoten dieselben Daten.
   1. Löschen Sie die Datei clusterNode/revision.log auf allen Cluster-Knoten.
   1. Löschen Sie die .lock-Datei auf allen Cluster-Knoten, falls vorhanden.
   1. Löschen Sie Datei repository/system.id auf allen Cluster-Knoten, falls vorhanden.
   1. Löschen Sie die Dateien „*/listener.properties“ auf allen Cluster-Knoten, falls vorhanden.
   1. Stellen Sie repository/cluster_node.id für einzelne Cluster-Knoten wieder her.

>[!NOTE]
>
>Bedenken Sie die folgenden Punkte:

* Wenn der ausgefallene Knoten ein AEM-Primärknoten war, kopieren Sie den gesamten Inhalt aus dem sekundären Repository-Ordner (er hat die Form „crx-repository\crx.0000“, wobei „0000“ beliebigen Ziffern entsprechen kann) in den Repository-Ordner „crx-repository\“.
* Bevor Sie einen Cluster-Knoten neu starten, achten Sie darauf, dass Sie das Repository „/clustered.txt“ vom primären Knoten löschen.
* Stellen Sie sicher, dass der primäre Knoten zuerst gestartet wird, und starten Sie die anderen Knoten erst, wenn er vollständig hochgefahren ist.

## Sichern und Wiederherstellen des Veröffentlichungsknotens der Correspondence Management Solution {#back-up-and-restore-correspondence-management-solution-publish-node}

Der Veröffentlichungsknoten hat in einer Cluster-Umgebung keine Primär-/Sekundärbeziehung.. Sie können eine Sicherung eines beliebigen Publish-Knotens mit [Sichern und Wiederherstellen](https://helpx.adobe.com/de/experience-manager/kb/CRXBackupAndRestoreProcedure.html) durchführen.

### Wiederherstellen eines einzelnen Veröffentlichungsknotens {#recover-a-single-publisher-node}

1. Beenden Sie den Knoten, der wiederhergestellt werden muss, und führen Sie keine Publishing-Aktivität durch, bis der Knoten wieder aktiv ist.
1. Stellen Sie den Publish-Knoten mithilfe von [Wiederherstellen des Backups](https://helpx.adobe.com/de/experience-manager/kb/CRXBackupAndRestoreProcedure.html) wieder her.

### Wiederherstellen eines Clusters {#recover-a-cluster}

1. Beenden Sie den Cluster.
1. Stellen Sie den Publish-Knoten mithilfe von [Wiederherstellen des Backups](https://helpx.adobe.com/de/experience-manager/kb/CRXBackupAndRestoreProcedure.html) wieder her.
1. Starten Sie den primären Knoten und anschließend den sekundären Knoten des Author-Clusters.
