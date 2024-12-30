---
title: Entwicklung von Communities
description: Erstellen und Anpassen von Community-Funktionen wie Foren, Benutzergruppen und mehr.
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

# Entwicklung von Communities  {#developing-communities}

## Überblick {#overview}

Adobe Experience Manager (AEM) Communities vereinfacht die Erstellung und Anpassung von Community-Funktionen wie Foren, Benutzergruppen, Blogs, Fragen und Antworten, Kalendern, Kommentaren, Rezensionen, Abstimmungen, Bewertungen und Zuweisungen. Diese Funktionen führen dazu, dass benutzergenerierte Inhalte (User-Generated Content, UGC) in die Veröffentlichungsumgebung eingegeben werden.

Die Grundlage einer [Community Site](overview.md#communitiessites) ist das [Social Component Framework](scf.md) (SCF). Die Erstellung einer Community-Site beginnt mit der Auswahl einer [Community-Site-Vorlage](sites-console.md) die aus „Community[Funktionen“ ](functions.md).

Einen Überblick und Tutorials zu den ersten Schritten finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Erste Schritte mit AEM Communities](getting-started.md)

>[!NOTE]
> 
>Es wird dringend empfohlen, mit den [ Versionen auf dem neuesten Stand zu ](deploy-communities.md#latest-releases).

## Empfohlene Bereitstellungen {#recommended-deployments}

* [Community-Inhaltsspeicher](working-with-srp.md): Erläutert die verfügbaren Optionen des Social Resource Providers (SRP) für einen gemeinsamen Speicher für benutzergenerierte Inhalte
* [Empfohlene Topologien für Communities](topologies.md): Erläutert Topologien basierend auf Anwendungsfall und SRP-Auswahl

## Social Component Framework {#social-component-framework}

* [Social Component Framework](scf.md): Übersicht über Framework und APIs.
* [SCF Handlebars Helpers](handlebars-helpers.md): Standard-Helper und Schreiben benutzerdefinierter Helper.
* [Client-seitige Anpassung](client-customize.md): Anpassen von Code, der im Browser ausgeführt wird.
* [Server-seitige Anpassung](server-customize.md): Anpassen von Code, der auf dem Server ausgeführt wird.
* [Storage Resource Provider (SRP)](srp.md): Überblick über den Community-Inhaltsspeicher.
* [Kodierrichtlinien](code-guide.md): Richtlinien, Tipps und Tricks.
* [Community-Komponentenhandbuch](components-guide.md): interaktives Entwicklungs-Tool.

## Komponenten-, Funktions- und Funktionsgrundlagen {#component-function-and-feature-essentials}

AEM Communities-Komponenten, -Funktionen und -Funktionen stellen die Bausteine für [Community-Sites](sites-console.md) bereit.

* [Komponenten-, Funktions- und Funktionsgrundlagen](essentials.md)
* [Clientlibs für Communities-Komponenten](clientlibs.md)
* [Community-Funktionen](functions.md)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Community-Site-Vorlagen](sites.md)

## Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Social-Media-Anmelden mit Facebook und Twitter](social-login.md)

## Community-Gruppen {#community-groups}

[Community-Gruppen](overview.md#communitygroups) sind das Konzept, das es Community-Mitgliedern ermöglicht, innerhalb der Community-Site Untergemeinschaften zu bilden. Die Erstellung einer Community-Gruppe kann in der Publishing- oder Authoring-Umgebung erfolgen.

* [Community-Hauptgruppen](essentials-groups.md)
* [group-Funktion](functions.md#groups-function)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Community-Gruppen für Autoren](creating-groups.md)

## Verwalten von Daten {#managing-data}

* [SRP und UGC Essentials](srp-and-ugc.md) - SRP API-Dienstprogrammmethoden und Beispiele
* [Tag Essentials](tag.md) - Möglichkeit für Community-Mitglieder, UGC und/oder katalogisierte Aktivierungsressourcen zu taggen

## Tutorials {#tutorials}

* [Client-seitige Tutorials](tutorials.md#client-side-customization)
* [Server-seitige Tutorials](tutorials.md#server-side-customization)
* [Anleitungen](tutorials.md#how-to-instructions)

## Fehlerbehebung {#troubleshooting}

* [Fehlerbehebung](troubleshooting.md)
* [Bekannte Probleme](/help/release-notes/release-notes.md)

## Verwandte Communities-Dokumentation {#related-communities-documentation}

* Unter [Bereitstellen von Communities](deploy-communities.md) erfahren Sie mehr über empfohlene Bereitstellungen und die Dispatcher-Konfiguration.

* Unter [Verwalten von Communities-Sites](administer-landing.md) erfahren Sie mehr über das Erstellen einer Community-Site, das Konfigurieren von Community-Site-Vorlagen, das Moderieren von Community-Inhalten, das Verwalten von Mitgliedern und das Konfigurieren von Nachrichten.

* Unter [Authoring von Communitys-Komponenten](author-communities.md) erfahren Sie, wie Sie Communities-Komponenten verwenden und konfigurieren.
