---
title: Konfiguration von Aktivierungsfunktionen
seo-title: Konfiguration von Aktivierungsfunktionen
description: Aktivierungsfunktionen in Communities konfigurieren
seo-description: Aktivierungsfunktionen in Communities konfigurieren
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Konfiguration von Aktivierungsfunktionen {#configuring-enablement-features}

## Überblick {#overview}

Die Aktivierungsfunktionen bieten die Möglichkeit, [Aktivierungsgemeinschaften](overview.md#enablement-community)zu erstellen.

* Diese Funktion erfordert zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung.

Die Verwendung der Aktivierungsfunktionen erfordert Folgendes:

Installation von:

* **SCORM** Sharable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für eLearning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei verpackt werden können.

* **MySQL** MySQL ist eine relationale Datenbank, die hauptsächlich für die SCORM-Verfolgung und Berichterstellung von Daten für die Aktivierung sowie für Tabellen zur Verfolgung des Videofortschritts verwendet wird. Das SCORM for enable feature pack erfordert den MySQL JDBC-Treiber.

* **FFmpeg** FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird, wenn sie installiert ist, für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video)verwendet. Bei Aktivierungsgemeinschaften wird es in der Autorenumgebung zum Abrufen von Metadaten für hochgeladene Ressourcen sowie zum Generieren einer Miniaturansicht verwendet, die bei der Auflistung der Ressource angezeigt werden soll.

Einrichtung von:

* **Community-Manager** Für Aktivierungsgemeinschaften können nur Mitgliedern der `Community Enablement Managers` Benutzergruppe die Rolle zugewiesen werden, `*Community Site* Enablement Manager`deren Berechtigungen die Inhaltserstellung, -zuweisungen und -verwaltung in der Veröffentlichungsumgebung umfassen können.

Optionale Konfiguration von:

* **Die Adobe Analytics**-Integration mit Adobe Analytics bietet umfassende Berichterstellungsfunktionen und unterstützt die Video Heartbeat-Erweiterung zu Analytics.

* **Dispatcher**

## Konfigurationsschritte {#configuration-steps}

Im Folgenden werden die Schritte beschrieben, die für die Aktivierung von Communities erforderlich sind.

Jeder Schritt ist mit der Dokumentation verknüpft, die die erforderlichen Details enthält.

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Treiber für MySQL](deploy-communities.md#jdbc-driver-for-mysql)**Verwenden der Web-Konsole (Pakete) installieren:*http://localhost:4502/system/console/bundles*Installieren *vor*der Installation des SCORM-Pakets

1. **[SCORM-Paket](deploy-communities.md#scorm-package)**installieren Package Manager verwenden:*http://localhost:4502/crx/packmgr/*

**Auf jedem Server:**

1. **[MySQL, MySQL Workbench installieren](mysql.md)**

1. **[MySQL-DatenbankenSQL-Skripten](mysql.md#database-setup)**ausführen, die von der Autoreninstanz heruntergeladen wurdenMySQL Workbench verwenden

**Auf demselben Server, auf dem die Autoreninstanz gehostet wird:**

1. **[install FFmpeg](ffmpeg.md)**

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Verbindungspool](mysql.md#configure-jdbc-connections)**Webkonsole verwenden (configMgr):*http://localhost:4502/system/console/configMgr*

1. **[SCORM-Engine-Dienst](mysql.md#aem-communities-scormengine-service)**Web Console (configMgr) verwenden:*http://localhost:4502/system/console/configMgr*

1. **[CSRF-Filter](mysql.md#adobe-granite-csrf-filter)**mithilfe von Web Console (configMgr) konfigurieren:*http://localhost:4502/system/console/configMgr*

**Auf Autoreninstanz:**

1. (*optional*) Analytics-Dienst **[](analytics.md)**mithilfe von Tools, Bereitstellung, Cloud-Services-Konsole konfigurieren:*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[FFmpeg](ffmpeg.md#configure-ffmpeg-transcoding-service)**Verwenden der Konsole Workflow/Modelle konfigurieren

1. **[Tunnel-Dienst](deploy-communities.md#tunnel-service-on-author)**Web-Konsole verwenden (configMgr) aktivieren:*http://localhost:4502/system/console/configMgr*

1. **[Community-Administratoren](users.md#creating-community-members)**erstellen Für Authoring-Umgebung verwenden Sie die klassische Sicherheitskonsole der Benutzeroberfläche: http://localhost:4502/useradmin **erstellen Sie Benutzer mit dem Pfad = /home/users/community

   * Mitglieder zu folgenden Gruppen hinzufügen:

      * Community-Aktivierungsmanager
      * Communities Administratoren

## Dispatcher {#dispatcher}

Wenn die Bereitstellung den Dispatcher[von ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)AEM enthält, müssen die Funktionen `clientheader`und `filter`Abschnitte geändert werden, damit die Aktivierungsfunktionen ordnungsgemäß funktionieren. Siehe [Konfigurieren von Dispatcher für Communities](dispatcher.md#enablement).
