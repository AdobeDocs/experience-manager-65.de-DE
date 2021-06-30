---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites, Experience Manager 6.5
audience: end-user
user-guide-title: AEM 6.5-Implementierungsanleitung
breadcrumb-title: Implementierungsanleitung
user-guide-description: Erfahren Sie mehr über die Installation, Bereitstellung und Architektur von Adobe Experience Manager 6.5, einschließlich der Adobe Managed Services-Cloud-Implementierung.
feature: Bereitstellen
role: Architect
source-git-commit: 5536ee27ad51356c2dcd0f0f36b91025bf1d228c
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 92%

---


# AEM 6.5 Bereitstellen des Benutzerhandbuchs {#deploying}

+ [Bereitstellungshandbuch für Benutzer](home.md)
+ Einführung in die AEM-Plattform {#introduction}
   + [Einführung in die AEM-Plattform](platform.md)
   + [Technische Anforderungen](technical-requirements.md)
   + [Speicherelemente in AEM 6.5](storage-elements-in-aem-6.md)
   + [AEM mit MongoDB](aem-with-mongodb.md)
+ Bereitstellen von AEM {#deploying}
   + [Bereitstellen und Verwalten](deploy.md)
   + [Empfohlene Bereitstellungen](recommended-deploys.md)
   + [Anwendungsserver-Installation](application-server-install.md)
   + [Benutzerdefinierte Standalone-Installation](custom-standalone-install.md)
   + [Start und Stopp über die Befehlszeile](command-line-start-and-stop.md)
   + [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](data-store-config.md)
   + [Revisionsbereinigung](revision-cleanup.md)
   + [Oak-Abfragen und Indizierung](queries-and-indexing.md)
   + [Ausführen von AEM mit der TarMK-Cold-Standby-Funktion](tarmk-cold-standby.md)
   + [RDBMS-Unterstützung in AEM 6.5](rdbms-support-in-aem.md)
   + [Indizieren mit dem Oak-run JAR](indexing-via-the-oak-run-jar.md)
   + [Oak-run.jar – Indizierungsanwendungsfälle](oak-run-indexing-usecases.md)
   + [Fehlerbehebung bei Oak-Indizes](troubleshooting-oak-indexes.md)
   + [Aktivieren der aggregierten Sammlung von Nutzungsstatistiken](opt-in-aggregated-usage-statistics.md)
   + [Fehlerbehebung](troubleshooting.md)
+ Konfigurieren von AEM {#configuring}
   + [Grundlegende Konfigurationskonzepte](configuring.md)
   + [Protokollierung](configure-logging.md)
   + [Konfigurieren von OSGi](configuring-osgi.md)
   + [OSGi-Konfigurationseinstellungen](osgi-configuration-settings.md)
   + [Ausführungsmodi](configure-runmodes.md)
   + [Web-Konsole](web-console.md)
   + [Replikation](replication.md)
   + [Replizieren mit MSSL](mssl-replication.md)
   + [Fehlerbehebung bei Replikationsproblemen](troubleshoot-rep.md)
   + [Ablauf statischer Objekte](expiration-static-objects.md)
   + [Versionsbereinigung](version-purging.md)
   + [Überwachung und Wartung der AEM-Instanz](monitoring-and-maintaining.md)
   + [Abladen von Aufträgen](offloading.md)
   + [Single Sign-On](single-sign-on.md)
   + [Ressourcenzuordnung](resource-mapping.md)
   + [Aktivieren von HTTP über SSL](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/ssl-by-default.html)
   + [Konsistenz- und Ausnahmeprüfungen](consistency-check.md)
   + [Leistungsrichtlinien](performance-guidelines.md)
   + [Leistungsoptimierung](configuring-performance.md)
   + [Handbuch zur Leistung von Assets](assets-performance-sizing.md)
   + [Artikel mit Anleitungen für die Konfiguration](ht-deploy.md)
   + [Konfigurieren der Web-Konsole](configuring-web-console.md)
+ Aktualisieren auf AEM 6.5 {#upgrading}
   + [Aktualisieren auf AEM 6.5](upgrade.md)
   + [Planung der Aktualisierung](upgrade-planning.md)
   + [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor ](pattern-detector.md)
   + [Abwärtskompatibilität in AEM 6.5](backward-compatibility.md)
   + [Aktualisierungsverfahren](upgrade-procedure.md)
   + [Durchführen einer In-Place-Aktualisierung](in-place-upgrade.md)
   + [Verwenden der Offline-Neuindizierung, um Ausfallzeiten während eines Upgrades zu reduzieren](upgrade-offline-reindexing.md)
   + [Lazy-Content-Migration](lazy-content-migration.md)
   + [Verwendung des CRX2Oak-Migrationstools](using-crx2oak.md)
   + [Wartungsaufgaben vor einer Aktualisierung](pre-upgrade-maintenance-tasks.md)
   + [Prüfungen und Fehlerbehebung nach einer Aktualisierung](post-upgrade-checks-and-troubleshooting.md)
   + [Aktualisieren von benutzerdefinierten Suchformularen](upgrading-custom-search-forms.md)
   + [Nachhaltige Aktualisierungen](sustainable-upgrades.md)
   + [Aktualisierung von Code und Anpassungen](upgrading-code-and-customizations.md)
   + [Schritte zur Aktualisierung von Installationen auf Anwendungsservern](app-server-upgrade.md)
   + [Liste der nach dem Upgrade deinstallierten veralteten Bundles](obsolete-bundles.md)
+ Repository-Neustrukturierung {#restructuring}
   + [Repository-Neustrukturierung in AEM 6.5](repository-restructuring.md)
   + [Repository-Neustrukturierung für alle Lösungen in AEM 6.5](all-repository-restructuring-in-aem-6-5.md)
   + [Repository-Neustrukturierung in AEM 6.5](sites-repository-restructuring-in-aem-6-5.md)
   + [Assets-Repository-Neustrukturierung in AEM 6.5](assets-repository-restructuring-in-aem-6-5.md)
   + [Dynamic Media: Repository-Neustrukturierung in AEM 6.5](dynamicmedia-repository-restructuring-in-aem-6-5.md)
   + [Forms-Repository-Neustrukturierung in AEM 6.5](forms-repository-restructuring-in-aem-6-5.md)
   + [E-Commerce-Repository-Neustrukturierung in AEM 6.5](ecommerce-repository-restructuring-in-aem-6-5.md)
   + [Repository-Neustrukturierung für AEM Communities in 6.5](communities-repository-restructuring-in-aem-6-5.md)
+ Best Practices {#practices}
   + [Best Practices für die Bereitstellung](best-practices.md)
   + [Leistungsübersicht](performance-tree.md)
   + [Best Practices für Leistungstests](best-practices-for-performance-testing.md)
   + [Best Practices für Abfragen und Indizierung](best-practices-for-queries-and-indexing.md)
   + [Empfehlungen für Kunden zur Benutzeroberfläche](ui-recommendations.md)
   + [Leistung und Skalierbarkeit](performance.md)
