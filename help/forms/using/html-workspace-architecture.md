---
title: AEM Forms Workspace-Architektur
seo-title: AEM Forms Workspace Architecture
description: Grundlegende Informationen und Überblick über die Architektur von LiveCycle AEM Forms workspace.
seo-description: Conceptual information and overview of the architecture of LiveCycle AEM Forms workspace.
uuid: e1a48452-ed44-4ea7-ba38-d961c8faafa5
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: c3a312fb-f684-477d-916d-2d3c99aa7607
exl-id: c6f216d4-781c-4356-b9f0-3324903a28e7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '219'
ht-degree: 100%

---

# AEM Forms Workspace-Architektur {#aem-forms-workspace-architecture}

AEM Forms Workspace ist eine Webanwendung, die auf CRX™ gehostet wird. Wenn Workspace in einem Browser geöffnet wird, wird auf eine CRX-Ressource zugegriffen und die Anwendung als HTML-Seite im Browser angezeigt.

Die Anwendung greift auf den AEM Forms-Server an den REST-Endpunkten zu, um folgende Aktionen auszuführen:

* Abrufen von Benutzeraufgaben, Verarbeiten von Startpunkten, Verlauf und Benutzerinformationen
* Ausführen von Aktionen für die Aufgaben
* Abfrage von Aufgaben in der Datenbank
* Aktualisieren von Benutzereinstellungen und mehr

Der AEM Forms Server greift auf die AEM Forms-Datenbank über JDBC zu. Die Datenbank erfasst Aufgaben, Prozesse und deren Instanzen, Benutzer und zugehörige Informationen.

AEM Forms Workspace ist aus modularen JavaScript™-Komponenten aufgebaut, die in anderen Web-Anwendungen individuell angepasst und wiederverwendet werden können. Die Komponenten basieren auf Backbone, einer JavaScript-Bibliothek, die eine Struktur für Webanwendungen zur Verfügung stellt. Einen ausführlicher Artikel, der die Interaktion von Komponenten mit Backbone beschreibt, finden Sie [hier](/help/forms/using/backbone-interaction.md). Die Organisation der Komponenten in der CRX-Ordnerstruktur wird in [diesem](/help/forms/using/folder-structure.md) Artikel behandelt.

Pakete, die für AEM Forms Workspace gesendet werden:

* `adobe-lc-workspace-pkg-<version>.zip`: Dies ist ein CRX-Paket, das heißt, es kann mithilfe des Package Manager in CRX bereitgestellt werden.
* `adobe-lc-workspace-<version>-src.zip`: Dies ist ein Archiv, das den vollständigen Code von AEM Forms Workspace und Skripte enthält, um die Bereitstellungspakete (Lieferpaket, Debugging-Paket und Entwicklungspaket) zu erstellen.
