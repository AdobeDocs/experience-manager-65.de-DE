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
source-git-commit: d6c8bbb9aa763a2eb6660b6b6755aba75241e394

---


# Konfiguration von Aktivierungsfunktionen {#configuring-enablement-features}

## Überblick {#overview}

Die Aktivierungsfunktionen bieten die Möglichkeit, [Aktivierungsgemeinschaften](overview.md#enablement-community)zu erstellen.

* Für diese Funktion sind zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung erforderlich.

Die Verwendung der Aktivierungsfunktionen erfordert Folgendes:

Installation von:

* **SCORM** Sharable Content Object Reference Model (SCORM) ist eine Sammlung von Standards und Spezifikationen für eLearning. SCORM definiert auch, wie Inhalte in eine übertragbare ZIP-Datei verpackt werden können.

* **MySQL** MySQL ist eine relationale Datenbank, die in erster Linie für die SCORM-Verfolgung und die Berichte-Daten für die Aktivierung sowie für die Verfolgung des Videofortschritts verwendet wird. Für das SCORM for enable feature pack ist der JDBC-Treiber für MySQL erforderlich.

* **FFmpeg** FFmpeg ist eine Lösung zum Konvertieren und Streaming von Audio und Video und wird, wenn sie installiert ist, für die ordnungsgemäße Transkodierung von [Video-Assets](../../help/sites-authoring/default-components-foundation.md#video)verwendet. Bei Aktivierungs-Communities wird sie in der Autorenressource verwendet, um Metadaten für hochgeladene Umgebung abzurufen und eine Miniaturansicht zu generieren, die bei der Auflistung der Ressource angezeigt werden soll.

Einrichtung von:

* **Community-Manager** Für Communities, die eine Aktivierung ermöglichen, können nur Mitgliedern der `Community Enablement Managers` Benutzergruppe die Rolle zugewiesen werden. `Community Site Enablement Manager`Zu deren Berechtigungen können die Inhaltserstellung, -zuweisungen und -verwaltung in der Umgebung &quot;Veröffentlichen&quot;gehören.

Optionale Konfiguration von:

* **Die Adobe Analytics**-Integration mit Adobe Analytics bietet umfassende Funktionen für Berichte und unterstützt die Video Heartbeat-Erweiterung zu Analytics.

* **Dispatcher**

## Konfigurationsschritte {#configuration-steps}

Im Folgenden werden die Schritte beschrieben, die für die Aktivierung von Communities erforderlich sind.

Jeder Schritt ist mit der Dokumentation verknüpft, die die erforderlichen Details enthält.

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[Installieren Sie den JDBC-Treiber für MySQL](deploy-communities.md#jdbc-driver-for-mysql)**Use Web Console (Bundles):*http://localhost:4502/system/console/bundles*Installieren *vor*der Installation des SCORM-Pakets

1. **[SCORM-Paket](deploy-communities.md#scorm-package)**mit Package Manager installieren:*http://localhost:4502/crx/packmgr/*

**Auf jedem Server:**

1. **[MySQL, MySQL Workbench installieren](mysql.md)**

1. **[MySQL-DatenbankenSQL-Skripten](mysql.md#database-setup)**ausführen, die von der Autoreninstanz heruntergeladen wurdenMySQL Workbench verwenden

**Auf demselben Server, auf dem die Autoreninstanz gehostet wird:**

1. **[Installieren von FFmpeg](ffmpeg.md)**

**In allen Autoren-/Veröffentlichungsinstanzen:**

1. **[JDBC-Verbindungspool](mysql.md#configure-jdbc-connections)**Verwenden Sie Web Console (configMgr):*http://localhost:4502/system/console/configMgr*

1. **[SCORM-Engine-Dienst](mysql.md#aem-communities-scormengine-service)**Web Console (configMgr) konfigurieren:*http://localhost:4502/system/console/configMgr*

1. **[CSRF-Filter](mysql.md#adobe-granite-csrf-filter)**mithilfe von Web Console (configMgr) konfigurieren:*http://localhost:4502/system/console/configMgr*

**Auf Autoreninstanz:**

1. (*Optional*) Analytics-Dienst **[](analytics.md)**mithilfe von Tools, Bereitstellung, Cloud-Services-Konsole konfigurieren:*http://localhost:4502/etc/cloudservices/sitecatalyst.html*

1. **[FFmpeg](ffmpeg.md#configure-ffmpeg-transcoding-service)**mithilfe der Konsole &quot;Workflow/Modelle&quot;konfigurieren

1. **[Tunnel-Dienst](deploy-communities.md#tunnel-service-on-author)**Web-Konsole verwenden (configMgr) aktivieren:*http://localhost:4502/system/console/configMgr*

1. **[Community-Administratoren](users.md#creating-community-members)**erstellen Für die Authoring-Umgebung verwenden Sie die klassische Sicherheitskonsole der Benutzeroberfläche: http://localhost:4502/useradmin **erstellen Sie Benutzer mit dem Pfad = /home/users/community

   * Hinzufügen Mitglieder zu folgenden Gruppen:

      * Community-Aktivierungsmanager
      * Communities Administratoren

## Dispatcher {#dispatcher}

Wenn die Bereitstellung [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html)enthält, müssen die Abschnitte `clientheader` `filter` und Abschnitte geändert werden, damit die Aktivierungsfunktionen ordnungsgemäß funktionieren. Siehe [Konfigurieren von Dispatcher für Communities](dispatcher.md#enablement).
