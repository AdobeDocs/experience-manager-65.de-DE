---
title: Upgrade-Verfahren
description: Erfahren Sie mehr über das Verfahren zum Aktualisieren von Adobe Experience Manager (AEM).
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
exl-id: 5242600c-2281-46f9-a347-d985b4e319b3
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 21%

---

# Upgrade-Verfahren {#upgrade-procedure}

>[!NOTE]
>
>Für das Upgrade sind Ausfallzeiten für die Autorenstufe erforderlich, da die meisten Adobe Experience Manager (AEM)-Upgrades direkt durchgeführt werden. Durch Befolgen dieser Best Practices können Sie Ausfallzeiten der Veröffentlichungsstufe minimieren oder vermeiden.

Beim Aktualisieren Ihrer AEM-Umgebungen müssen Sie die Unterschiede beim Ansatz zwischen dem Aktualisieren von Autorenumgebungen oder Veröffentlichungsumgebungen berücksichtigen, um Ausfallzeiten für Autoren und Endbenutzer zu minimieren. Auf dieser Seite wird das allgemeine Verfahren zum Aktualisieren einer AEM Topologie beschrieben, die derzeit mit einer Version von AEM 6.x ausgeführt wird. Da der Prozess zwischen der Autoren- und Veröffentlichungsstufe und Mongo- und TarMK-basierten Implementierungen unterschiedlich ist, wurde jede Ebene und jeder Mikrokernel in einem separaten Abschnitt aufgelistet. Bei der Ausführung Ihrer Bereitstellung empfiehlt Adobe zunächst die Aktualisierung Ihrer Autorenumgebung, um festzustellen, ob sie erfolgreich ist, und dann den Übergang zu den Veröffentlichungsumgebungen.

<!--
>[!IMPORTANT]
>
>The downtime during the upgrade can be significally reduced by indexing the repository before performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)
-->

## TarMK-Autorenebene {#tarmk-author-tier}

### Starttopologie {#starting-topology}

In diesem Abschnitt wird von einer Topologie mit einem Autorenserver ausgegangen, der auf TarMK mit einem Cold Standby ausgeführt wird. Die Replikation erfolgt vom Autorenserver an die TarMK-Veröffentlichungsfarm. Dieser Ansatz ist zwar hier nicht dargestellt, kann aber auch für Bereitstellungen verwendet werden, die Abladungen verwenden. Stellen Sie sicher, dass Sie die Offloading-Instanz auf der neuen Version upgraden oder neu erstellen, bevor Sie Replikationsagenten, die auf der Autoreninstanz deaktiviert waren, neu aktivieren.

![tarmk_starting_topology](assets/tarmk_starting_topology.jpg)

### Vorbereiten des Upgrades {#upgrade-preparation}

![upgrade-preparation-author](assets/upgrade-preparation-author.png)

1. Beenden Sie die Inhaltserstellung.

1. Beenden Sie die Standby-Instanz.

1. Deaktivieren Sie Replikationsagenten auf der Autoreninstanz.

1. Führen Sie die [Wartungsaufgaben vor dem Upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) aus.

### Ausführen des Upgrades {#upgrade-execution}

![execute_upgrade](assets/execute_upgrade.jpg)

1. Führen Sie die [Ersetzende Aktualisierung](/help/sites-deploying/in-place-upgrade.md).
1. Aktualisieren des Dispatcher-Moduls *falls erforderlich*.

1. QA validiert die Aktualisierung.

1. Fahren Sie die Autoreninstanz herunter.

### Bei erfolgreichem Upgrade {#if-successful}

![if_successful](assets/if_successful.jpg)

1. Kopieren Sie die aktualisierte Instanz, um eine Cold Standby-Instanz zu erstellen.

1. Starten Sie die Autoreninstanz.

1. Starten Sie die Standby-Instanz.

### Bei fehlgeschlagenem Upgrade (Rollback) {#if-unsuccessful-rollback}

![rollback](assets/rollback.jpg)

1. Starten Sie die Cold-Standby-Instanz als neuen Primären.

1. Erstellen Sie die Autorenumgebung aus der Cold-Standby-Instanz neu.

## MongoMK-Autorencluster {#mongomk-author-cluster}

### Starttopologie {#starting-topology-1}

In diesem Abschnitt wird von einer Topologie mit einem MongoMK-Autoren-Cluster mit mindestens zwei AEM-Autoreninstanzen ausgegangen, gesichert von mindestens zwei MongoMK-Datenbanken. Die Autoreninstanzen nutzen einen gemeinsamen Datenspeicher. Diese Schritte gelten für S3- und Dateidatenspeicher. Die Replikation erfolgt von den Autorenservern zur TarMK-Veröffentlichungsfarm.

![mongo-topology](assets/mongo-topology.jpg)

### Vorbereiten des Upgrades {#upgrade-preparation-1}

![mongo-upgrade_prep](assets/mongo-upgrade_prep.jpg)

1. Beenden Sie die Inhaltserstellung.
1. Klonen Sie den Datenspeicher für die Sicherung.
1. Beenden Sie alle bis auf eine AEM Autoreninstanz, Ihren primären Autor.
1. Entfernen Sie alle bis auf einen MongoDB-Knoten aus der Replikatgruppe, Ihrer primären Mongo-Instanz.
1. Aktualisieren Sie die `DocumentNodeStoreService.cfg` -Datei auf der primären Autoreninstanz, um die Replikatgruppe Ihrer einzelnen Mitglieder widerzuspiegeln.
1. Starten Sie die primäre Autoreninstanz neu, um sicherzustellen, dass sie ordnungsgemäß neu gestartet wird.
1. Deaktivieren Sie Replikationsagenten auf der primären Autoreninstanz.
1. Ausführen [Wartungsaufgaben vor der Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) auf der primären Autoreninstanz.
1. Aktualisieren Sie bei Bedarf MongoDB auf der primären Mongo-Instanz auf Version 3.2 mit WiredTiger.

### Ausführen des Upgrades {#Upgrade-execution-1}

![mongo-execution](assets/mongo-execution.jpg)

1. Führen Sie einen [Ersetzende Aktualisierung](/help/sites-deploying/in-place-upgrade.md) auf der primären Autoreninstanz.
1. Aktualisieren des Dispatchers oder Webmoduls *falls erforderlich*.
1. QA validiert die Aktualisierung.

### Bei erfolgreichem Upgrade {#if-successful-1}

![mongo-secondaries](assets/mongo-secondaries.jpg)

1. Erstellen Sie neue 6.5-Autoreninstanzen, die mit der aktualisierten Mongo-Instanz verbunden sind.

1. Erstellen Sie die MongoDB-Knoten neu, die aus dem Cluster entfernt wurden.

1. Aktualisieren Sie die `DocumentNodeStoreService.cfg` -Dateien, um die vollständige Replikatgruppe widerzuspiegeln.

1. Starten Sie die Autoreninstanzen einzeln neu.

1. Entfernen Sie den geklonten Datenspeicher. 

### Bei fehlgeschlagenem Upgrade (Rollback)  {#if-unsuccessful-rollback-2}

![mongo-rollback](assets/mongo-rollback.jpg)

1. Konfigurieren Sie die sekundären Autoreninstanzen neu, um eine Verbindung zum geklonten Datenspeicher herzustellen.

1. Fahren Sie die aktualisierte primäre Instanz im Autorenmodus herunter.

1. Beenden Sie die upgegradete primäre Mongo-Instanz.

1. Starten Sie die sekundären Mongo-Instanzen mit einer dieser Instanzen als neue primäre Instanz.

1. Konfigurieren Sie die `DocumentNodeStoreService.cfg` -Dateien in den sekundären Autoreninstanzen auf den Replikatsatz der noch nicht aktualisierten Mongo-Instanzen verweisen.

1. Starten Sie die sekundären Autoreninstanzen.

1. Bereinigen Sie die aktualisierten Autoreninstanzen, den Mongo-Knoten und den Datenspeicher.

## TarMK-Veröffentlichungsfarm {#tarmk-publish-farm}

### TarMK-Veröffentlichungsfarm {#tarmk-publish-farm-1}

Die angenommene Topologie für diesen Abschnitt besteht aus zwei TarMK-Veröffentlichungsinstanzen, die von Dispatchern angeführt werden, die wiederum mit einem Lastenausgleich konfrontiert sind. Die Replikation erfolgt vom Autorenserver zur TarMK-Veröffentlichungsfarm.

![tarmk-pub-farmv5](assets/tarmk-pub-farmv5.png)

### Ausführen des Upgrades {#upgrade-execution-2}

![upgrade-publish2](assets/upgrade-publish2.png)

1. Beenden Sie den Traffic zur Veröffentlichungsinstanz 2 am Load Balancer.
1. Ausführen [Wartung vor der Aktualisierung](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) auf Publish 2.
1. Führen Sie einen [Ersetzende Aktualisierung](/help/sites-deploying/in-place-upgrade.md) auf Publish 2.
1. Aktualisieren des Dispatchers oder Webmoduls *falls erforderlich*.
1. Leeren Sie den Dispatcher-Cache.
1. QA validiert Publish 2 über den Dispatcher hinter der Firewall.
1. Veröffentlichung beenden 2.
1. Kopieren Sie die Veröffentlichungsinstanz 2 .
1. Starten Sie Publish 2.

### Bei erfolgreichem Upgrade {#if-successful-2}

![upgrade-publish1](assets/upgrade-publish1.png)

1. Aktivieren Sie Traffic auf Publish 2.
1. Beenden Sie den Traffic auf Publish 1.
1. Beenden Sie die Veröffentlichungsinstanz 1.
1. Ersetzen Sie die Veröffentlichungsinstanz 1 durch eine Kopie von Veröffentlichung 2.
1. Aktualisieren des Dispatchers oder Webmoduls *falls erforderlich*.
1. Leeren Sie den Dispatcher-Cache für Publish 1.
1. Veröffentlichung starten 1.
1. QA validiert die Veröffentlichung 1 über den Dispatcher hinter der Firewall.

### Bei fehlgeschlagenem Upgrade (Rollback) {#if-unsuccessful-rollback-1}

![pub_rollback](assets/pub_rollback.jpg)

1. Erstellen Sie eine Kopie von Publish 1.
1. Ersetzen Sie die Instanz im Veröffentlichungsmodus 2 durch eine Kopie im Veröffentlichungsmodus 1.
1. Leeren Sie den Dispatcher-Cache für Publish 2.
1. Starten Sie Publish 2.
1. QA validiert Publish 2 über den Dispatcher hinter der Firewall.
1. Aktivieren Sie Traffic auf Publish 2.

## Abschließende Upgrade-Schritte {#final-upgrade-steps}

1. Aktivieren Sie Traffic auf Publish 1.
1. QA führt die endgültige Validierung über eine öffentliche URL durch.
1. Aktivieren Sie Replikationsagenten aus der Autorenumgebung.
1. Setzt die Inhaltserstellung fort.
1. Führen Sie [Prüfungen nach dem Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) durch.

![final](assets/final.jpg)
