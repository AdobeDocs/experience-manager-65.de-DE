---
title: Lazy-Content-Migration
description: Erfahren Sie mehr über die Migration von verzögertem Inhalt in Adobe Experience Manager 6.4.
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
ht-degree: 23%

---

# Lazy-Content-Migration {#lazy-content-migration}

Aus Gründen der Abwärtskompatibilität, Inhalte und Konfiguration in **/etc** und **/content** Ab Adobe Experience Manager (AEM) 6.3 wird mit dem Upgrade nicht sofort angetastet oder umgewandelt. Dadurch wird sichergestellt, dass die Abhängigkeiten von Kundenanwendungen von diesen Strukturen erhalten bleiben. Die Funktionalität für diese Inhaltsstrukturen ist immer noch dieselbe, obwohl der Inhalt in einer vorkonfigurierten AEM 6.5 an einem anderen Ort gehostet würde.

Möglicherweise können nicht alle Speicherorte automatisch umgewandelt werden. Es gibt aber auch einige verzögerte `CodeUpgradeTasks`, die auch als Lazy-Content-Migration bezeichnet werden. Kunden können diese automatischen Umwandlungen auslösen, indem sie die Instanz mit der folgenden Systemeigenschaft neu starten:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Dies verursacht die `CodeUpgradeTasks` Wird während der Migration ausgeführt.

Das Ziel ist eine effiziente Ausführung, aber dieser Upgrade-Prozess ist synchron und bringt daher je nach Menge der zu verarbeitenden Inhalte Ausfallzeiten mit sich. Adobe empfiehlt, die Laufzeiten in einer Staging-Umgebung vor einem Produktionssystem zu evaluieren, um ein entsprechendes Wartungsfenster zu planen.

Da dies normalerweise auch eine Anpassung der Anwendung erfordert, sollte diese Aktivität zusammen mit der entsprechenden Anwendungsbereitstellung ausgeführt werden.

Nachfolgend finden Sie eine vollständige Liste aller in Version 6.5 eingeführten `CodeUpgradeTasks`:

| **Name** | **relevant** **Für AEM-Versionen vor** | **Migrationstyp** ** ** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Unmittelbar |  |
| `Cq60MSMContentUpgrade` | &lt; 6,0 | Unmittelbar | Ermittelt alle `LiveRelationShips` aus `VersionStorage`, die gelöscht wurden, und fügt die Ausschlusseigenschaft zum übergeordneten Element hinzu. |
| `Cq61CloudServicesContentUpgrade` | &lt; 6,1 | Unmittelbar | Strukturiert Cloud-Services für sicheres Standard-Setup um. |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Unmittelbar | Entfernt eine eigenschaftsbasierte Verknüpfung aus **/content** bis **/conf** (ersetzt durch den OSGi-Mechanismus), generiert die entsprechende OSGi-Konfiguration |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Unmittelbar | Aufgrund der Handhabung von merge_preserve überschreibt die sichere Standardregel Ablehnen erteilte Berechtigungen, was dazu führt, dass beim Upgrade eine Neuanordnung erforderlich ist |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Unmittelbar | Erkennt Komponenten mithilfe des HTML5SmartFile-Widgets, sucht nach der Verwendung der Komponente im Inhalt und strukturiert die Persistenz neu, verschiebt die Binärdatei effektiv um eine Ebene nach unten und speichert sie nicht auf Komponentenebene. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Unmittelbar | Verschiebt Projekte des alten Stils aus **/etc/projects** bis **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Unmittelbar | Führt eine Container-Ebene in die Hierarchie (Bereiche) ein und passt Verweise an. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Unmittelbar | Legt feste Ortsnamen auf Zielkomponenten fest. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Unmittelbar | Komplexe Transformation von Workflow-Modellen, die älter sind als 6.2-Strukturen, -Instanzen, -Benachrichtigungen und das anschließende Zurückführen vom Backup-Speicherort aus **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets, benutzerdefinierte Metadatenschemata und Verarbeitungsprofile aus **/apps** bis **/conf** und übersetzt das Metadatenschema und die Metadatenprofil-Formulare von Coral2 nach Coral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt Assets und benutzerdefinierte Suchfacetten aus **/apps** bis **/conf** und übersetzt das Metadatenschema und die Metadatenprofil-Formulare von Coral2 nach Coral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Unmittelbar | Aktualisiert InboxItems für die Sortierung von Inbox-Items (Anpassen von Metadaten für eine effiziente Sortierung) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Unmittelbar | Passt die Eigenschaft „metadataSchema“ für einen Ordner an, indem relative Pfade ersetzt werden durch **/conf** anstelle von **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Unmittelbar | Anpassen der Navigationsstruktur |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Unmittelbar | Verschiebt benutzerdefinierte Konfigurationen für die Überwachungs-Dashboards von **/libs** und **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Unmittelbar | Übersetzt die Eigenschaft „processingProfile“ (bis 6.1 verwendet) in Assets so, dass sie mit der Struktur von 6.3 und höher übereinstimmt. Passt auch die relativen Pfade des Profils an **/conf** anstelle von **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Unmittelbar | Upgrade-Task, der bei einem Upgrade veraltete CRXDE Lite- und Web-Konsolen-Menüeinträge entfernt. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Verzögert | Verschieben von SRP-Cloud-Konfigurationen, Community-Schlagwortkonfigurationen, bereinigt **/etc/social** und **/etc/enable** (Alle Verweise und Daten müssen bei der Ausführung der verzögerten Migration angepasst werden - kein Anwendungsteil sollte mehr von dieser Struktur abhängig sein). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Verzögert | Bereinigt **/etc/cloudsettings** (enthält ContextHub-Konfiguration). Die Konfiguration wird beim ersten Zugriff automatisch migriert. Falls die Lazy-Content-Migration zusammen mit der Aktualisierung dieses Inhalts in gestartet wird **/etc/cloudsettings** Muss über das Paket vor dem Upgrade beibehalten und neu installiert werden, damit die implizite Transformation und die nachfolgende Deinstallation des Pakets nach Abschluss wirksam werden. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Verzögert | Passt die alte Titelstruktur im Benutzerprofilknoten an den Titel an. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Verzögert | Migrieren von Commerce-Inhalten aus **/etc/commerce** nach **/var/commerce**. Während der Migration werden Inhalte verschoben und Verweise auf verschobene Inhalte aktualisiert, um den neuen Speicherort widerzuspiegeln. |
| `CQ65DMMigrationTask` | &lt; 6.5 | Verzögert | Migrieren von alten Katalogeinstellungen und Dynamic Media Cloud Services-Einstellungen aus **/etc** nach **/conf** |
| `CQ65LegacyClientlibsCleanupTask` | &lt; 6.5 | Verzögert | Bereinigen vorhandener Client-Bibliotheken unter **/etc/clientlibs** |
