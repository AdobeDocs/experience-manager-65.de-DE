---
title: Lazy-Content-Migration
description: Erfahren Sie mehr über die Lazy-Content-Migration in Adobe Experience Manager 6.4.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: 946c7c2a-806b-4461-a38b-9c2e5ef1e958
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 100%

---

# Lazy-Content-Migration {#lazy-content-migration}

Aus Gründen der Abwärtskompatibilität werden Inhalte und Konfigurationen in **/etc** und **/content** ab Adobe Experience Manager (AEM) 6.3 beim Upgrade nicht sofort behandelt oder konvertiert. Damit wird sichergestellt, dass Abhängigkeiten in Kundenanwendungen von diesen Strukturen intakt bleiben. Die Funktionalität in Bezug auf diese Inhaltsstrukturen ist immer noch die gleiche, auch wenn der Inhalt in AEM 6.5 standardmäßig an anderer Stelle gehostet wird.

Möglicherweise können nicht alle Speicherorte automatisch umgewandelt werden. Es gibt aber auch einige verzögerte `CodeUpgradeTasks`, die auch als Lazy-Content-Migration bezeichnet werden. Kunden können diese automatischen Umwandlungen auslösen, indem sie die Instanz mit der folgenden Systemeigenschaft neu starten:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Dadurch werden während der Migration `CodeUpgradeTasks` ausgeführt.

Auch wenn eine effiziente Durchführung angestrebt wird, ist dieser Upgrade-Prozess synchron und erfordert daher eine Ausfallzeit, die vom Umfang des Inhalts abhängt, der verarbeitet werden muss. Adobe empfiehlt, die Laufzeiten in einer Staging-Umgebung zu ermitteln, bevor die Durchführung im Produktionssystem erfolgt, um ein passendes Wartungsfenster planen zu können.

Da hierbei in der Regel auch die Anwendung angepasst werden muss, sollte diese Aktivität zusammen mit der entsprechenden Anwendungsbereitstellung durchgeführt werden.

Nachfolgend finden Sie eine vollständige Liste aller in Version 6.5 eingeführten `CodeUpgradeTasks`:

| **Name** | **Relevant** **für AEM-Versionen vor** | **Migrationstyp** ** ** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Unmittelbar |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Unmittelbar | Ermittelt alle `LiveRelationShips` aus `VersionStorage`, die gelöscht wurden, und fügt die Ausschlusseigenschaft zum übergeordneten Element hinzu. |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Unmittelbar | Strukturiert „cloudservices“ für ein standardmäßig sicheres Setup um |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Unmittelbar | Entfernt auf Eigenschaften basierende Verknüpfungen von **/content** mit **/conf** (wird durch den OSGi-Mechanismus ersetzt), generiert die entsprechende OSGi-Konfiguration |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Unmittelbar | Aufgrund der merge_preserve-Behandlung überschreibt die Ablehnungsregel für die standardmäßige Sicherheit vorhandene Berechtigungen, die beim Upgrade neu angeordnet werden müssen |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Unmittelbar | Ermittelt Komponenten, die das Html5SmartFile-Widget verwenden, sucht nach der Verwendung der Komponenten im Inhalt und strukturiert die Persistenz neu, indem die Binärdatei um eine Ebene nach unten verschoben und nicht auf Komponentenebene gespeichert wird. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Unmittelbar | Verschiebt alte Projekte aus **/etc/projects** nach **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Unmittelbar | Erstellt eine Container-Ebene in der Hierarchie (Bereiche) und passt Verweise an. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Unmittelbar | Legt feste Speicherortnamen für Zielkomponenten fest. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Unmittelbar | Komplexe Umwandlung von Strukturen, Instanzen, Benachrichtigungen von Workflow-Modellen vor 6.2 und anschließendes erneutes Zusammenführen vom Sicherungsordner aus **/var/backup**. |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets, benutzerdefinierte Metadaten-Schemata und Verarbeitungsprofile von **/apps** nach **/conf** und überführt das Metadatenschema und Metadatenprofilformulare von coral2 in coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets und benutzerdefinierte Suchfacetten von **/apps** nach **/conf** und überführt das Metadatenschema und Metadatenprofilformulare von coral2 in coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Unmittelbar | Aktualisiert InboxItems zum Sortieren von Posteingangselementen (Anpassen der Metadaten für eine effiziente Sortierung) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Unmittelbar | Passt die metadataSchema-Eigenschaft für Ordner an, indem relative Pfade zu **/conf** statt zu **/apps** führen |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Unmittelbar | Passt die Navigationsstruktur an |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt benutzerdefinierte Konfigurationen für Überwachungs-Dashboards von **/libs** und **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Unmittelbar | Überführt die processingProfile-Eigenschaft (wurde bis 6.1 verwendet) in Assets in die ab 6.3 verwendete Struktur. Passt außerdem die relativen Pfade des Profils an, die zu **/conf** statt zu **/apps** führen. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Unmittelbar | Upgrade-Aufgabe, die bei einem Upgrade veraltete Menüeinträge aus CRXDE Lite und der Web-Konsole entfernt. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Verzögert | Verschiebt SRP-Cloud-Konfigurationen sowie Community-Schlagwortkonfigurationen und bereinigt **/etc/social** und **/etc/enablement** (alle Verweise und Daten müssen angepasst werden, wenn die Lazy-Migration ausgeführt wird – es dürfen keine Anwendungsteile weiterhin von dieser Struktur abhängig sein). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Verzögert | Bereinigt **/etc/cloudsettings** (enthält die ContextHub-Konfiguration). Die Konfiguration wird beim ersten Zugriff automatisch migriert. Für den Fall, dass die Lazy-Content-Migration zusammen mit dem Upgrade gestartet wird, muss vor dem Upgrade der Inhalt in **/etc/cloudsettings** über ein Paket gesichert und dann erneut installiert werden, damit die implizite Umwandlung stattfindet. Das Paket muss schließlich nach Abschluss des Vorgangs deinstalliert werden. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Verzögert | Passt die alte Titelstruktur an den Titel im Benutzerprofilknoten an. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Verzögert | Migrieren von Commerce-Inhalten aus **/etc/commerce** nach **/var/commerce**. Während der Migration werden Inhalte verschoben und Verweise auf verschobene Inhalte aktualisiert, um den neuen Speicherort widerzuspiegeln. |
| `CQ65DMMigrationTask` | &lt; 6.5 | Verzögert | Migrieren von alten Katalogeinstellungen und Dynamic Media Cloud Services-Einstellungen aus **/etc** nach **/conf** |
| `CQ65LegacyClientlibsCleanupTask` | &lt; 6.5 | Verzögert | Bereinigen vorhandener Client-Bibliotheken unter **/etc/clientlibs** |
