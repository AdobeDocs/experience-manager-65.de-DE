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
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Konfiguration von Aktivierungsfunktionen {#configuring-enablement-features}

## Überblick {#overview}

Die Aktivierungsfunktionen bieten die Möglichkeit, [Aktivierungsgemeinschaften](overview.md#enablement-community)zu erstellen.

* Für diese Funktion sind zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung erforderlich.

Die Verwendung der Aktivierungsfunktionen erfordert Folgendes:

Installation von:

* **SCORM**

   Sharable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für eLearning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei verpackt werden können.

* **MySQL**

   MySQL ist eine relationale Datenbank, die primär für die SCORM-Verfolgung und Berichte-Daten für die Aktivierung sowie für Tabellen zur Verfolgung des Videofortschritts verwendet wird. Für das SCORM for enable feature pack ist der JDBC-Treiber für MySQL erforderlich.

* **FFmpeg**

   FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird, wenn sie installiert ist, für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video)verwendet. Bei Aktivierungs-Communities wird sie in der Autorenressource verwendet, um Metadaten für hochgeladene Umgebung abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Ressource angezeigt werden soll.

Einrichtung von:

* **Community-Manager**

   Bei aktivierten Communities können nur Mitglieder der `Community Enablement Managers` Benutzergruppe die Rolle zugewiesen werden, `Community Site Enablement Manager`deren Berechtigungen die Inhaltserstellung, Zuweisungen und Mitgliederverwaltung in der Umgebung &quot;Veröffentlichen&quot;umfassen können.

Optionale Konfiguration von:

* **Adobe Analytics**

   Die Integration mit Adobe Analytics bietet umfassende Funktionen zum Berichte und unterstützt die Video Heartbeat-Erweiterung zu Analytics.

* **Dispatcher**

## Konfigurationsschritte {#configuration-steps}

Im Folgenden werden die Schritte beschrieben, die für die Aktivierung von Communities erforderlich sind.

Jeder Schritt ist mit der Dokumentation verknüpft, die die erforderlichen Details enthält.

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Treiber für MySQL installieren](deploy-communities.md#jdbc-driver-for-mysql)**

   Web-Konsole verwenden (Pakete): *http://localhost:4502/system/console/bundles* Installieren *vor* der Installation des SCORM-Pakets

1. **[SCORM-Paket](deploy-communities.md#scorm-package)**mit Package Manager installieren:*http://localhost:4502/crx/packmgr/*

**Auf jedem Server:**

1. **[MySQL, MySQL Workbench installieren](mysql.md)**

1. **[MySQL-Datenbanken installieren](mysql.md#database-setup)**

   SQL-Skripten ausführen, die von der Autoreninstanz heruntergeladen wurdenMySQL Workbench verwenden

**Auf demselben Server, auf dem die Autoreninstanz gehostet wird:**

1. **[Installieren von FFmpeg](ffmpeg.md)**

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Verbindungspool konfigurieren](mysql.md#configure-jdbc-connections)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[SCORM-Engine-Dienst konfigurieren](mysql.md#aem-communities-scormengine-service)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[CSRF-Filter konfigurieren](mysql.md#adobe-granite-csrf-filter)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

**Auf Autoreninstanz:**

1. (*Optional*) Analytics-Dienst **[konfigurieren](analytics.md)**

   Verwenden Sie Tools, Bereitstellung, Cloud Services-Konsole: *http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[FFmpeg konfigurieren](ffmpeg.md#configure-ffmpeg-transcoding-service)**

   Arbeitsablauf/Modelle-Konsole verwenden

1. **[Tunnel-Dienst aktivieren](deploy-communities.md#tunnel-service-on-author)**

   Web-Konsole verwenden (configMgr): *http://localhost:4502/system/console/configMgr*

1. **[Community-Administratoren erstellen](users.md#creating-community-members)**

   Für die Umgebung von Autoren verwenden Sie die klassische Sicherheitskonsole der Benutzeroberfläche: http://localhost:4502/useradmin ** erstellen Sie Benutzer mit dem Pfad = /home/users/community

   * Hinzufügen Mitglieder zu folgenden Gruppen:

      * Community-Aktivierungsmanager
      * Communities Administratoren

## Dispatcher {#dispatcher}

Wenn die Bereitstellung [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)enthält, müssen die Abschnitte `clientheader` `filter` und Abschnitte geändert werden, damit die Aktivierungsfunktionen ordnungsgemäß funktionieren. Siehe [Konfigurieren von Dispatcher für Communities](dispatcher.md#enablement).
