---
title: Konfiguration von Aktivierungsfunktionen
seo-title: Configuring Enablement Features
description: Aktivierungsfunktionen in Communities konfigurieren
seo-description: Configure enablement features in Communities
uuid: 27be3128-1a7d-412e-99a9-6e3b3b0aec1c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 765a3d9b-4552-403e-872c-fdf684ac271d
role: Admin
exl-id: b635e2ed-4637-4b2f-a746-ec8dc7541bab
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 5%

---

# Konfiguration von Aktivierungsfunktionen {#configuring-enablement-features}

## Übersicht {#overview}

Die Aktivierungsfunktionen ermöglichen die Erstellung von [Aktivierungsgemeinschaften](overview.md#enablement-community).

* Diese Funktion erfordert zusätzliche Lizenzen für die Verwendung in einer Produktionsumgebung.

Die Verwendung der Aktivierungsfunktionen erfordert Folgendes:

Installation von:

* **SCORM**

   Sharable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für das E-Learning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei gepackt werden können.

* **MySQL**

   MySQL ist eine relationale Datenbank, die hauptsächlich für SCORM-Tracking- und Reporting-Daten zur Aktivierung sowie Tabellen zur Verfolgung des Videofortschritts verwendet wird. Für das SCORM zur Aktivierung des Feature Packs ist der MySQL JDBC-Treiber erforderlich.

* **FFmpeg**

   FFmpeg ist eine Lösung für das Konvertieren und Streaming von Audio und Video und wird, falls installiert, für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video). Für Aktivierungs-Communities wird sie in der Autorenumgebung verwendet, um Metadaten für hochgeladene Ressourcen abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Ressource angezeigt wird.

Einrichtung von:

* **Community-Manager**

   Für Aktivierungs-Communities benötigen Sie nur Mitglieder der `Community Enablement Managers` der Benutzergruppe kann die Rolle von `Community Site Enablement Manager`, zu deren Berechtigungen die Inhaltserstellung, -zuweisungen und -verwaltung in der Veröffentlichungsumgebung gehören können.

Optionale Konfiguration von:

* **Adobe Analytics**

   Die Integration mit Adobe Analytics bietet umfassende Berichterstellungsfunktionen und unterstützt die Video Heartbeat-Erweiterung zu Analytics.

* **Dispatcher**

## Konfigurationsschritte {#configuration-steps}

Im Folgenden werden die Schritte beschrieben, die für die Aktivierung von Communities erforderlich sind.

Jeder Schritt verlinkt zu einer Dokumentation, die die erforderlichen Details enthält.

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Treiber für MySQL installieren](deploy-communities.md#jdbc-driver-for-mysql)**

   Web-Konsole (Bundles) verwenden: *http://localhost:4502/system/console/bundles*

   Installieren *before* Installieren des SCORM-Pakets

1. **[SCORM-Paket installieren](deploy-communities.md#scorm-package)**


   Verwenden Sie Package Manager: *http://localhost:4502/crx/packmgr/*

**Auf jedem Server:**

1. **[MySQL, MySQL Workbench installieren](mysql.md)**

1. **[MySQL-Datenbanken installieren](mysql.md#database-setup)**

   Ausführen von SQL-Skripten, die von der Autoreninstanz heruntergeladen wurden

   MySQL Workbench verwenden

**Auf derselben Server-Hosting-Autoreninstanz:**

1. **[Installieren von FFmpeg](ffmpeg.md)**

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Verbindungspool konfigurieren](mysql.md#configure-jdbc-connections)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[SCORM-Engine-Dienst konfigurieren](mysql.md#aem-communities-scormengine-service)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[CSRF-Filter konfigurieren](mysql.md#adobe-granite-csrf-filter)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

**In der Autoreninstanz:**

1. (*Optional*) **[Konfigurieren des Analytics-Dienstes](analytics.md)**

   Verwenden Sie Tools, Bereitstellung, Cloud Services-Konsole: *http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[FFmpeg konfigurieren](ffmpeg.md#configure-ffmpeg-transcoding-service)**

   Verwenden der Konsole &quot;Workflow/Modelle&quot;

1. **[Aktivieren des Tunneldienstes](deploy-communities.md#tunnel-service-on-author)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[Community-Administratoren erstellen](users.md#creating-community-members)**

   Verwenden Sie für die Autorenumgebung die Sicherheitskonsole der klassischen Benutzeroberfläche: *http://localhost:4502/useradmin*

   Benutzer mit Pfad erstellen = /home/users/community

   * Fügen Sie den folgenden Gruppen Mitglieder hinzu:

      * Community-Aktivierungsmanager
      * Communities-Administratoren

## Dispatcher {#dispatcher}

Wann die Bereitstellung [AEM Dispatcher](https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html), damit die Aktivierungsfunktionen ordnungsgemäß funktionieren, muss die `clientheader` und `filter` -Abschnitte müssen geändert werden. Siehe [Konfigurieren des Dispatchers für Communities](dispatcher.md#enablement).
