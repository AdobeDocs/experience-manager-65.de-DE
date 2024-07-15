---
title: Entwickeln von Communities
description: Erstellen und passen Sie Community-Funktionen wie Foren, Benutzergruppen und mehr an.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 3ed3768a-1b3c-45a1-a34c-61694cd407d9
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 5%

---

# Entwickeln von Communities  {#developing-communities}

## Überblick {#overview}

Adobe Experience Manager (AEM) Communities vereinfachen die Erstellung und Anpassung von Community-Funktionen wie Foren, Benutzergruppen, Blogs, Fragen und Antworten, Kalendern, Kommentaren, Rezensionen, Abstimmungen, Bewertungen und Zuweisungen. Diese Funktionen führen dazu, dass benutzergenerierte Inhalte (UGC) in die Veröffentlichungsumgebung eingegeben werden.

Die Grundlage einer [Community-Site](overview.md#communitiessites) ist das [Social-Komponenten-Framework](scf.md) (SCF). Die Erstellung einer Community-Site beginnt mit der Auswahl einer [Community-Site-Vorlage](sites-console.md), die aus [Community-Funktionen](functions.md) besteht.

Einen Überblick und die ersten Schritte finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Erste Schritte mit AEM Communities](getting-started.md)

>[!NOTE]
> 
>Es wird dringend empfohlen, mit den [neuesten Versionen](deploy-communities.md#latest-releases) auf dem Laufenden zu bleiben.

## Empfohlene Bereitstellungen {#recommended-deployments}

* [Community-Inhaltsspeicherung](working-with-srp.md): beschreibt die verfügbaren SRP (Social Resource Provider)-Optionen für einen UGC Common Store
* [Empfohlene Topologien für Communities](topologies.md): Erörtert Topologien basierend auf Anwendungsfall und SRP-Auswahl

## Social Component Framework {#social-component-framework}

* [Social Component Framework](scf.md): Überblick über Framework und APIs.
* [SCF Handlebars Helpers](handlebars-helpers.md): Standard-Helfer und das Schreiben benutzerdefinierter Helfer.
* [Clientseitige Anpassung](client-customize.md): Anpassen des Codes, der im Browser ausgeführt wird.
* [Serverseitige Anpassung](server-customize.md): Anpassen des Codes, der auf dem Server ausgeführt wird.
* [Speicher Resource Provider (SRP)](srp.md): Überblick über die Speicherung von Community-Inhalten.
* [Kodierungsrichtlinien](code-guide.md): Richtlinien, Tipps und Tricks.
* [Handbuch zu Community-Komponenten](components-guide.md): interaktives Entwicklungstool.

## Komponenten-, Funktionen- und Funktionsgrundlagen {#component-function-and-feature-essentials}

AEM Communities-Komponenten, -Funktionen und -Funktionen stellen die Bausteine für [Community-Sites](sites-console.md) bereit.

* [Komponenten, Funktionen und Funktionsgrundlagen](essentials.md)
* [Clientlibs für Communities-Komponenten](clientlibs.md)
* [Community-Funktionen](functions.md)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Community-Site-Vorlagen](sites.md)

## Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Social-Anmeldung mit Facebook und Twitter](social-login.md)

## Community-Gruppen {#community-groups}

[Community-Gruppen](overview.md#communitygroups) ermöglichen es Community-Mitgliedern, Untergruppen innerhalb der Community-Site zu bilden. Die Erstellung einer Community-Gruppe kann in der Veröffentlichungs- oder Autorenumgebung erfolgen.

* [Community-Gruppengrundlagen](essentials-groups.md)
* [Gruppenfunktion](functions.md#groups-function)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Community-Gruppen für Autoren](creating-groups.md)

## Verwalten von Daten {#managing-data}

* [SRP und UGC Essentials](srp-and-ugc.md) - Methoden und Beispiele für SRP-API-Dienstprogramme
* [Tag Essentials](tag.md) - Möglichkeit für Community-Mitglieder, UGC und/oder katalogisierte Aktivierungsressourcen zu taggen

## Tutorials {#tutorials}

* [Clientseitige Tutorials](tutorials.md#client-side-customization)
* [Serverseitige Tutorials](tutorials.md#server-side-customization)
* [Anleitungen](tutorials.md#how-to-instructions)

## Fehlerbehebung {#troubleshooting}

* [Fehlerbehebung](troubleshooting.md)
* [Bekannte Probleme](/help/release-notes/release-notes.md)

## Verwandte Communities - Dokumentation {#related-communities-documentation}

* Unter [Bereitstellen von Communities](deploy-communities.md) finden Sie Informationen zu empfohlenen Bereitstellungen und zur Dispatcher-Konfiguration.

* Unter [Verwalten von Communities-Sites](administer-landing.md) erfahren Sie mehr über die Erstellung einer Community-Site, die Konfiguration von Community-Site-Vorlagen, die Moderation von Community-Inhalten, die Verwaltung von Mitgliedern und die Konfiguration von Messaging.

* Unter [Authoring von Communities-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten erstellen und konfigurieren.
