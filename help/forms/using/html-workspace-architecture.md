---
title: Architektur von AEM Forms Workspace
description: Grundlegende Informationen und Überblick über die Architektur von LiveCycle AEM Forms Workspace.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: c6f216d4-781c-4356-b9f0-3324903a28e7
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 31%

---

# Architektur von AEM Forms Workspace {#aem-forms-workspace-architecture}

AEM Forms Workspace ist eine Webanwendung, die auf CRX™ gehostet wird. Wenn Workspace in einem Browser geöffnet wird, wird auf eine CRX-Ressource zugegriffen und die Anwendung wird im Browser als HTML-Seite gerendert.

Das Programm greift auf den AEM Forms-Server an REST-Endpunkten zu, um Folgendes zu tun:

* Abrufen von Benutzeraufgaben, Verarbeiten von Startpunkten, Prozessverlauf und Benutzerinformationen
* Ausführen von Aktionen für Aufgaben
* Abfragen in der Datenbank
* Aktualisieren von Benutzereinstellungen und mehr

Der AEM Forms-Server greift über JDBC auf die AEM Forms-Datenbank zu. Die Datenbank enthält Aufgaben, Prozesse und ihre Instanzen, Benutzer und zugehörige Informationen.

AEM Forms Workspace ist aus modularen JavaScript™-Komponenten aufgebaut, die in anderen Web-Anwendungen individuell angepasst und wiederverwendet werden können. Die Komponenten basieren auf BackBone, einer JavaScript-Bibliothek, die Webanwendungen strukturiert. Ein detaillierter Artikel, der die Interaktion von Komponenten mit BackBone beschreibt, ist [here](/help/forms/using/backbone-interaction.md). Die Organisation der Komponenten in der CRX-Ordnerstruktur wird im Abschnitt [this](/help/forms/using/folder-structure.md) Artikel.

Für AEM Forms Workspace bereitgestellte Pakete:

* `adobe-lc-workspace-pkg-<version>.zip`: Dies ist ein CRX-Paket, das heißt, es kann mithilfe des Package Manager in CRX bereitgestellt werden.
* `adobe-lc-workspace-<version>-src.zip`: Dies ist ein Archiv, das den vollständigen Code von AEM Forms Workspace und Skripte enthält, um die Bereitstellungspakete (Lieferpaket, Debugging-Paket und Entwicklungspaket) zu erstellen.
