---
title: Lazy-Content-Migration
description: Erfahren Sie mehr über die Migration verzögerter Inhalte in Adobe Experience Manager 6.4.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: 946c7c2a-806b-4461-a38b-9c2e5ef1e958
source-git-commit: 3885cc51f7e821cdb352737336a29f9c4f0c2f41
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 24%

---

# Lazy-Content-Migration {#lazy-content-migration}

Aus Gründen der Abwärtskompatibilität, des Inhalts und der Konfiguration in **/etc** und **/content** Ab Adobe Experience Manager (AEM) 6.3 wird während des Upgrades nicht sofort berührt oder umgewandelt. Dadurch wird sichergestellt, dass die Abhängigkeiten von Kundenanwendungen von diesen Strukturen intakt bleiben. Die Funktionalität für diese Inhaltsstrukturen ist weiterhin identisch, auch wenn der Inhalt in einer vordefinierten AEM 6.5 an einem anderen Ort gehostet wird.

Möglicherweise können nicht alle Speicherorte automatisch umgewandelt werden. Es gibt aber auch einige verzögerte `CodeUpgradeTasks`, die auch als Lazy-Content-Migration bezeichnet werden. Kunden können diese automatischen Umwandlungen auslösen, indem sie die Instanz mit der folgenden Systemeigenschaft neu starten:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Dadurch wird die `CodeUpgradeTasks` während der Migration ausgeführt werden.

Das Ziel ist zwar eine effiziente Ausführung, aber dieser Aktualisierungsprozess ist synchron und führt daher abhängig von der Menge des zu verarbeitenden Inhalts zu Ausfallzeiten. Adobe empfiehlt, die Laufzeiten in einer Staging-Umgebung vor einem Produktionssystem zu bewerten, um ein entsprechendes Wartungsfenster zu planen.

Da dies normalerweise auch eine Anpassung der Anwendung erfordert, sollte diese Aktivität zusammen mit der entsprechenden Anwendungsbereitstellung durchgeführt werden.

Nachfolgend finden Sie eine vollständige Liste aller in Version 6.5 eingeführten `CodeUpgradeTasks`:

| **Name** | **Relevant** **für AEM Versionen vor** | **Migrationstyp** ** ** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Unmittelbar |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Unmittelbar | Ermittelt alle `LiveRelationShips` aus `VersionStorage`, die gelöscht wurden, und fügt die Ausschlusseigenschaft zum übergeordneten Element hinzu. |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Unmittelbar | Strukturiert Cloud-Dienste für die standardmäßige sichere Einrichtung um |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Unmittelbar | Entfernt eigenschaftsbasierte Verknüpfungen aus **/content** nach **/conf** (ersetzt durch den OSGi-Mechanismus) generiert die entsprechende OSGi-Konfiguration |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Unmittelbar | Aufgrund der Handhabung von merge_preserve überschreibt die standardmäßig sichere Ablehnungsregel die erteilten Berechtigungen, was dazu führt, dass bei der Aktualisierung neu angeordnet werden muss |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Unmittelbar | Erkennt Komponenten mit dem Html5SmartFile-Widget, sucht nach Benutzern der Komponente im Inhalt und strukturiert die Persistenz neu, indem die Binärdatei auf einer Ebene nach unten verschoben und nicht auf Komponentenebene gespeichert wird. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Unmittelbar | Verschiebt alte Stilprojekte aus **/etc/projects** nach **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Unmittelbar | Führt eine Containerschicht in die Hierarchie (Bereiche) ein und passt Verweise an. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Unmittelbar | Legt feste Ortsnamen für Zielkomponenten fest. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Unmittelbar | Komplexe Transformation von Workflow-Modellen, die aus 6.2-Strukturen, Instanzen, Benachrichtigungen bestehen und dann vom Backup-Speicherort aus zusammenführen **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets, benutzerdefinierte Metadatenschemata und Verarbeitungsprofile aus **/apps** nach **/conf** und übersetzt das Metadatenschema und die Metadatenprofilformulare von coral2 in coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets und benutzerdefinierte Suchfacetten aus **/apps** nach **/conf** und übersetzt das Metadatenschema und die Metadatenprofilformulare von coral2 in coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Unmittelbar | Aktualisiert InboxItems für die Sortierung von Inbox-Elementen (Anpassen von Metadaten für eine effiziente Sortierung) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Unmittelbar | Passt die Eigenschaft metadataSchema im Ordner an, indem relative Pfade zu **/conf** anstelle von **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Unmittelbar | Anpassen der Navigationsstruktur |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt benutzerdefinierte Konfigurationen für die Überwachungs-Dashboards aus **/libs** und **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Unmittelbar | Übersetzt die Eigenschaft processingProfile (bis 6.1 verwendet) in Assets so, dass sie mit der Struktur 6.3 und höher übereinstimmt. Passt außerdem die relativen Pfade des Profils an **/conf** anstelle von **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Unmittelbar | Aktualisierungsaufgabe, die veraltete Menüeinträge aus CRXDE Lite und Web-Konsole entfernt, wenn ein Upgrade durchgeführt wird. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Verzögert | Verschieben von SRP-Cloud-Konfigurationen, Konfigurationen von Community-Schlagwörtern, Bereinigung **/etc/social** und **/etc/enablement** (alle Verweise und Daten müssen angepasst werden, wenn die verzögerte Migration ausgeführt wird - kein Anwendungsabschnitt sollte mehr von dieser Struktur abhängig sein). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Verzögert | Bereinigungen **/etc/cloudsettings** (enthält ContextHub-Konfiguration). Die Konfiguration wird beim ersten Zugriff automatisch migriert. Falls die Migration verzögerter Inhalte zusammen mit der Aktualisierung dieses Inhalts in gestartet wird **/etc/cloudsettings** muss vor der Aktualisierung über das -Paket erhalten und neu installiert werden, damit die implizite Umwandlung eintritt, zusammen mit einer nachfolgenden Deinstallation des Pakets nach Abschluss. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Verzögert | Passt die alte Titelstruktur an den Titel im Benutzerprofilknoten an. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Verzögert | Migrieren von Commerce-Inhalten aus **/etc/commerce** nach **/var/commerce**. Während der Migration werden Inhalte verschoben und Verweise auf verschobene Inhalte aktualisiert, um den neuen Speicherort widerzuspiegeln. |
| `CQ65DMMigrationTask` | &lt; 6.5 | Verzögert | Migrieren von alten Katalogeinstellungen und Dynamic Media Cloud Services-Einstellungen aus **/etc** nach **/conf** |
| `CQ65LegacyClientlibsCleanupTask` | &lt; 6.5 | Verzögert | Bereinigen vorhandener Client-Bibliotheken unter **/etc/clientlibs** |
