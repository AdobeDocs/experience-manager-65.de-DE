---
title: Entwickeln von Communities
seo-title: Entwickeln von Communities
description: Community-Funktionen wie Foren, Benutzergruppen und mehr erstellen und anpassen
seo-description: Community-Funktionen wie Foren, Benutzergruppen und mehr erstellen und anpassen
uuid: 51dc54da-9090-4d36-adf9-72d5479062a5
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: fbfe8097-3c3f-4a05-97ad-1ce526362a26
exl-id: 3ed3768a-1b3c-45a1-a34c-61694cd407d9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 10%

---

# Entwicklung von Communities {#developing-communities}

## Überblick {#overview}

AEM Communities vereinfacht die Erstellung und Anpassung von Community-Funktionen wie Foren, Benutzergruppen, Blogs, Fragen und Antworten, Kalendern, Kommentaren, Rezensionen, Abstimmungen, Bewertungen und Zuweisungen. Diese Funktionen führen dazu, dass benutzergenerierte Inhalte (UGC) in die Veröffentlichungsumgebung eingegeben werden.

Die Grundlage einer [Community-Site](overview.md#communitiessites) ist das [Social-Komponenten-Framework](scf.md) (SCF). Die Erstellung einer Community-Site beginnt mit der Auswahl einer [Community-Site-Vorlage](sites-console.md), die aus [Community-Funktionen](functions.md) besteht.

Einen Überblick und die ersten Schritte finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Einstieg in AEM Communities](getting-started.md)
* [Erste Schritte mit AEM Communities zur Aktivierung](getting-started-enablement.md)

>[!NOTE]
> 
>Es wird dringend empfohlen, mit den [aktuellen Versionen](deploy-communities.md#latest-releases) auf dem Laufenden zu bleiben.

## Empfohlene Bereitstellungen {#recommended-deployments}

* [Community-Inhaltsspeicherung](working-with-srp.md): beschreibt die verfügbaren SRP-Optionen für einen UGC Common Store
* [Empfohlene Topologien für Communities](topologies.md): Erörtert Topologien basierend auf Anwendungsfall und SRP-Auswahl

## Social Component Framework {#social-component-framework}

* [Social Component Framework](scf.md): Übersicht über Framework und APIs.
* [SCF Handlebars Helpers](handlebars-helpers.md): Standard-Helfer und wie Sie benutzerdefinierte Helfer schreiben.
* [Clientseitige Anpassung](client-customize.md): Anpassen des Codes, der im Browser ausgeführt wird.
* [Serverseitige Anpassung](server-customize.md): Anpassen des Codes, der auf dem Server ausgeführt wird.
* [Storage Resource Provider (SRP)](srp.md): Übersicht über die Speicherung von Community-Inhalten.
* [Kodierungsrichtlinien](code-guide.md): Richtlinien, Tipps und Tricks.
* [Handbuch](components-guide.md) zu Community-Komponenten: interaktives Entwicklungstool.

## Komponenten-, Funktionen- und Funktionsgrundlagen {#component-function-and-feature-essentials}

AEM Communities-Komponenten, -Funktionen und -Funktionen stellen die Bausteine für [Community-Sites](sites-console.md) bereit.

* [Komponenten, Funktionen und Funktionsgrundlagen](essentials.md)
* [Clientlibs für Communities-Komponenten](clientlibs.md)
* [Community-Funktionen](functions.md)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Community-Site-Vorlagen](sites.md)

## Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Anmeldung über Social Media mit Facebook und Twitter](social-login.md)

## Community-Gruppen {#community-groups}

[Community-](overview.md#communitygroups) Gruppierungen ermöglichen es Community-Mitgliedern, Untergruppen innerhalb der Community-Site zu bilden. Die Erstellung einer Community-Gruppe kann in der Veröffentlichungs- oder Autorenumgebung erfolgen.

* [Community-Gruppengrundlagen](essentials-groups.md)
* [Gruppenfunktion](functions.md#groups-function)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Community-Gruppen für Autoren](creating-groups.md)

## Verwalten von Daten {#managing-data}

* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP API-Dienstprogrammmethoden und Beispiele
* [Tag-Grundlagen](tag.md)  - Möglichkeit für Community-Mitglieder, benutzergenerierte Inhalte und/oder katalogisierte Aktivierungsressourcen zu taggen

## Tutorials {#tutorials}

* [Clientseitige Tutorials](tutorials.md#client-side-customization)
* [Serverseitige Tutorials](tutorials.md#server-side-customization)
* [Anleitungen](tutorials.md#how-to-instructions)

## Fehlerbehebung {#troubleshooting}

* [Fehlerbehebung](troubleshooting.md)
* [Bekannte Probleme](/help/release-notes/known-issues.md)

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Besuchen Sie [Communities bereitstellen](deploy-communities.md) , um mehr über die empfohlenen Bereitstellungen und die Dispatcher-Konfiguration zu erfahren.

* Besuchen Sie [Verwalten von Communities-Sites](administer-landing.md) , um mehr über die Erstellung einer Community-Site, die Konfiguration von Community-Site-Vorlagen, die Moderation von Community-Inhalten, die Verwaltung von Mitgliedern und die Konfiguration von Messaging zu erfahren.

* Besuchen Sie [Erstellen von Communities-Komponenten](author-communities.md) , um zu erfahren, wie Sie Communities-Komponenten erstellen und konfigurieren.
