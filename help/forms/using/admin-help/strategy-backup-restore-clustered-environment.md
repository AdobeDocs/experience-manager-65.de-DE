---
title: Strategie für Sicherung und Wiederherstellung in einer Clusterumgebung
seo-title: Strategie für Sicherung und Wiederherstellung in einer Clusterumgebung
description: Wenn in Ihrer AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank gespeichert werden, müssen Sie eine Strategie zum Sichern dieser Daten implementieren und sicherstellen, dass diese mit den AEM Forms-Daten synchronisiert bleiben.
seo-description: Wenn in Ihrer AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank gespeichert werden, müssen Sie eine Strategie zum Sichern dieser Daten implementieren und sicherstellen, dass diese mit den AEM Forms-Daten synchronisiert bleiben.
uuid: c29b989c-30ed-4a8e-bab8-9b7746291a33
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c332985b-4556-4056-961a-fce2356da88d
exl-id: 98c96349-f253-475f-b646-352269814a38
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 73%

---

# Strategie für Sicherung und Wiederherstellung in einer Clusterumgebung {#strategy-for-backup-and-restore-in-a-clustered-environment}

>[!NOTE]
>
>Wenn in Ihrer AEM Forms-Implementierung zusätzliche benutzerdefinierte Daten in einer anderen Datenbank gespeichert werden, müssen Sie eine Strategie zum Sichern dieser Daten implementieren und sicherstellen, dass diese mit den AEM Forms-Daten synchronisiert bleiben. Darüber hinaus muss die Anwendung so ausgelegt sein, dass sie robust genug ist, um in einem Szenario zu funktionieren, in dem die zusätzlichen Datenbanken nicht mehr synchronisiert sind. Es wird dringend empfohlen, alle Datenbankvorgänge im Kontext einer Transaktion durchzuführen, um einen konsistenten Zustand aufrechtzuerhalten.

Sie müssen die folgenden Teile des AEM Forms-Systems sichern, um es bei einem Fehler wiederherstellen zu können:

* Von AEM Forms verwendete Datenbank
* GDS mit langlebigen Daten und anderen permanenten Dokumenten
* AEM-Datenbank (CRX-Repository)

>[!NOTE]
>
>Sie müssen alle weiteren Daten sichern, die von Ihrer AEM Forms-Konfiguration verwendet werden, beispielsweise Kundenschriftarten, Connectors-Daten usw.

## Sichern einer Clusterumgebung {#back-up-a-clustered-environment}

Dieses Thema behandelte die folgenden Vorgehensweisen, um eine AEM Forms-Clusterumgebung zu sichern:

* Offlinesicherung mit Ausfallzeiten
* Offlinesicherung ohne Ausfallzeiten (Sicherung eines sekundären Knotens, der heruntergefahren wird)
* Onlinesicherung ohne Ausfallzeiten aber mit verzögerter Antwort
* Sichern der Bootstrap-Eigenschaftendatei

### Offlinesicherung mit Ausfallzeiten  {#offline-backup-with-downtime}

1. Deaktivieren Sie den gesamten Cluster und damit zusammenhängende Dienste. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie von jedem Knoten Datenbank, GDS und Connectors. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Führen Sie die folgenden Schritte aus, um das AEM-Repository offline zu sichern:

   1. Sichern Sie für jeden Clusterknoten die Datei, die die Clusterknoten-ID enthält.
   1. Sichern Sie alle Dateien eines jeden sekundären Clusterknotens, einschließlich Unterverzeichnissen.
   1. Sichern Sie Repository/System-ID jedes Clusterknotens separat.

   Ausführliche Anweisungen finden Sie unter[ Sicherung und Wiederherstellung](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html).

1. Sichern Sie alle weiteren Daten, z. B. Kundenschriftarten.
1. Starten Sie den Cluster neu.

### Offlinesicherung ohne Ausfallzeiten  {#offline-backup-with-no-downtime}

1. Starten Sie den kontinuierlichen Sicherungsmodus. (siehe [In den Sicherungsmodus wechseln](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Beachten Sie, dass der kontinuierliche Sicherungsmodus nach einer Wiederherstellung beendet werden muss.

1. Beenden Sie jeden der sekundären Knoten des Clusters in Bezug auf AEM. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie von jedem Knoten Datenbank, GDS und Connectors. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Führen Sie die folgenden Schritte aus, um das AEM-Repository offline zu sichern:

   1. Sichern Sie für jeden Clusterknoten die Datei, die die Clusterknoten-ID enthält.
   1. Sichern Sie alle Dateien eines jeden sekundären Clusterknotens, einschließlich Unterverzeichnissen.
   1. Sichern Sie Repository/System.id jedes Clusterknotens separat.

   Ausführliche Anweisungen finden Sie unter[ Sicherung und Wiederherstellung](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html).

1. Sichern Sie alle weiteren Daten, z. B. Kundenschriftarten.
1. Starten Sie den Cluster neu.

### Onlinesicherung ohne Ausfallzeiten aber mit verzögerter Antwort  {#online-backup-with-no-downtime-but-delay-in-response}

1. Starten Sie den kontinuierlichen Sicherungsmodus. (siehe [In den Sicherungsmodus wechseln](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Beachten Sie, dass der kontinuierliche Sicherungsmodus nach einer Wiederherstellung beendet werden muss.

1. Beenden Sie jeden der sekundären Knoten des Clusters in Bezug auf AEM. (siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Sichern Sie von jedem Knoten Datenbank, GDS und Connectors. (siehe [Zu sichernde und wiederherzustellende Dateien](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Führen Sie die folgenden Schritte aus, um das AEM-Repository online zu sichern:

   1. Sichern Sie für jeden Clusterknoten die Datei, die cluster_node.id enthält.
   1. Sichern Sie Repository/System.id jedes Clusterknotens separat.
   1. Führen Sie auf einem sekundären Knoten eine Online-Sicherung des Repositorys durch, um detaillierte Schritte zu erhalten. Siehe Online-Sicherung.

1. Sichern Sie alle weiteren Daten, z. B. Kundenschriftarten.
1. Starten Sie den Cluster neu.

### Sichern der Bootstrap-Eigenschaftendatei  {#back-up-the-bootstrap-properties-file}

Wenn wir einen AEM-Cluster erstellen, wird eine Eigenschaftendatei für alle sekundären Knoten auf dem Anwendungsserver erstellt. Es wird empfohlen, die Bootstrap-Eigenschaftendatei zu sichern. Sie finden die Datei im folgenden Verzeichnis auf Ihrem Anwendungsserver:

* JBoss: im BIN-Ordner
* WebLogic: im Domänenordner
* WebSphere: im Profilordner

Sie müssen die Datei für das Disaster Recovery-Szenario AEM sekundären Knotens sichern und sie an dem angegebenen Speicherort auf dem Anwendungsserver ersetzen, wenn sie wiederhergestellt wird.

## Wiederherstellung in einer Clusterumgebung {#recovery-in-a-clustered-environment}

Im Falle eines Ausfalls des gesamten Clusters oder eines einzelnen Knotens, müssen Sie mithilfe der Sicherung eine Wiederherstellung durchführen.

Für die Wiederherstellung eines einzelnen Knotens, müssen Sie nur den Knoten abschalten und den Wiederherstellungsvorgang für einen Knoten ausführen.

Falls der gesamte Cluster aufgrund eines Fehler, wie dem Ausfall der Datenbank, ausfällt, müssen Sie die folgenden Schritte ausführen. Die Wiederherstellung hängt von der verwendeten Sicherungsmethode ab.

### Wiederherstellung eines einzelnen Knotens  {#restoring-a-single-node}

1. Schalten Sie den beschädigten Knoten ab.

   >[!NOTE]
   >
   >Wenn der beschädigte Knoten ein AEM primären Knoten ist, fahren Sie den gesamten Clusterknoten herunter.

1. Erstellen Sie bei Bedarf das physische System von einem Systemabbild neu.
1. Wenden Sie Patches oder Aktualisierungen für AEM Forms an, die seit der Erstellung des Abbilds angewendet wurden. Diese Informationen wurden im Sicherungsverfahren erfasst. AEM Forms muss entsprechend dem Patchlevel zum Zeitpunkt der Systemsicherung wiederhergestellt werden.
1. (*Optional*) Wenn alle anderen Knoten problemlos funktionieren, kann es ebenfalls sein, dass das AEM-Repository beschädigt ist. In diesem Fall sehen Sie die Nachricht „repository unsync“ in der error.log- Datei des AEM-Repositorys.

   Um das Repository wiederherzustellen, führen Sie die folgenden Schritte durch.

   >[!NOTE]
   >
   >Wenn eine komprimierte CRX-Repository-Sicherung online gestellt wurde, entpacken Sie diese an einem beliebigen Ort und führen Sie den Offline-Wiederherstellungsprozess durch.

   1. Löschen Sie die Ordner „repository“, „shared“, „version“, und „workspaces“ im Ordner „clusterNode“ des Knotens.
   1. Stellen Sie die Sicherung des Clusterknotens (einschließlich Unterordner) auf dem Knoten wieder her.
   1. Löschen Sie die Datei „clusterNode/revision.log“ auf dem Knoten.
   1. Entfernen Sie „.lock“ auf dem Knoten, wenn vorhanden.
   1. Löschen Sie „repository/system.id“ auf dem Knoten, wenn vorhanden.
   1. Löschen Sie die Dateien &amp;ast;&amp;ast;/listener.properties auf dem Knoten, falls vorhanden.
   1. Stellen Sie „repository/cluster_node.id“ für einzelne Clusterknoten wieder her.

>[!NOTE]
>
>Beachten Sie folgende Punkte:

* Wenn der fehlerhafte Knoten ein AEM primären Knoten war, kopieren Sie den gesamten Inhalt aus dem sekundären Repository-Ordner (crx-repository\crx.0000, wobei 0000 beliebige Ziffern sein können) in den Ordner crx-repository\ repository und löschen Sie den sekundären Repository-Ordner.
* Bevor Sie einen Clusterknoten neu starten, stellen Sie sicher, dass Sie das Repository /clustered.txt vom primären Knoten löschen.
* Stellen Sie sicher, dass der primäre Knoten zuerst gestartet wird, und starten Sie nach dem vollständigen Start andere Knoten.

### Wiederherstellen des gesamten Clusters {#restoring-the-entire-cluster}

1. Beenden Sie alle Clusterknoten.
1. Erstellen Sie das physische System von einem Systemabbild neu.
1. Wenden Sie Patches oder Aktualisierungen für AEM Forms an, die seit der Erstellung des Abbilds angewendet wurden. Diese Informationen wurden in Schritt 1 des Sicherungsverfahrens erfasst. AEM Forms muss entsprechend dem Patchlevel zum Zeitpunkt der Systemsicherung wiederhergestellt werden.
1. Stellen Sie Datenbank, GDS und Connectors wieder her.
1. Führen Sie folgende Schritte aus, um das AEM-Repository offline wiederherzustellen:

   >[!NOTE]
   >
   >Wenn eine komprimierte CRX-Repository-Sicherung online gestellt wurde, entpacken Sie diese an einem beliebigen Ort und führen Sie den Offline-Wiederherstellungsprozess durch.

   1. Löschen Sie die Ordner „repository“, „shared“, „version“, und „workspaces“ im Ordner „clusterNode“ auf allen Knoten.
   1. Löschen Sie alle Dateien und Ordner im Ordner „shared“.
   1. Stellen Sie die Sicherung des Clusterknotens (einschließlich Unterordner) auf einem Clusterknoten wieder her.
   1. Kopieren Sie alle Dateien des wiederhergestellten Clusterknotens auf allen anderen Clusterknoten. Sobald dies abgeschlossen ist, enthält jeder Clusterknoten dieselben Daten.
   1. Löschen Sie die Datei „clusterNode/revision.log“ auf allen Clusterknoten.
   1. Entfernen Sie das „.lock“ auf allen Clusterknoten, wenn vorhanden.
   1. Löschen Sie „repository/system.id“ auf allen Clusterknoten, wenn vorhanden.
   1. Löschen Sie die Dateien &amp;ast;&amp;ast;/listener.properties auf allen Clusterknoten, falls vorhanden.
   1. Stellen Sie „repository/cluster_node.id“ für einzelne Clusterknoten wieder her.

>[!NOTE]
>
>Beachten Sie folgende Punkte:

* Wenn der fehlerhafte Knoten ein AEM primären Knoten war, kopieren Sie den gesamten Inhalt aus dem sekundären Repository-Ordner (es sieht aus wie crx-repository\crx.0000, wobei 0000 beliebige Ziffern sein kann) in den Ordner crx-repository\ repository .
* Bevor Sie einen Clusterknoten neu starten, stellen Sie sicher, dass Sie das Repository /clustered.txt vom primären Knoten löschen.
* Stellen Sie sicher, dass der primäre Knoten zuerst gestartet wird, und starten Sie nach dem vollständigen Start andere Knoten.

## Sichern und Wiederherstellen des Veröffentlichungsknotens der Correspondence Management Solution {#back-up-and-restore-correspondence-management-solution-publish-node}

Der Veröffentlichungsknoten weist in einer Clusterumgebung keine primäre sekundäre Beziehung auf. Sie können einen beliebigen Veröffentlichungsknoten sichern, indem Sie diese Anweisungen befolgen: [Sicherung und Wiederherstellung](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html).

### Wiederherstellen eines einzelnen Veröffentlichungsknotens  {#recover-a-single-publisher-node}

1. Beenden Sie den Knoten, der wiederhergestellt werden muss, und vermeiden Sie jede Veröffentlichungsaktivität, bis der Knoten wieder bereit ist.
1. Stellen Sie den Veröffentlichungsknoten mit [Wiederherstellen des Backups] (https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html#Restoring the Backup) wieder her.

### Wiederherstellen eines Clusters {#recover-a-cluster}

1. Beenden Sie den Cluster.
1. Stellen Sie den Veröffentlichungsknoten mit [Wiederherstellen des Backups] (https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html#Restoring the Backup) wieder her.
1. Starten Sie den primären Knoten, gefolgt vom sekundären Knoten des Autoren-Clusters.
