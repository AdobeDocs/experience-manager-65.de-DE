---
title: Entwickeln von Communities
seo-title: Developing Communities
description: Community-Funktionen wie Foren, Benutzergruppen und mehr erstellen und anpassen
seo-description: Create and customize community features such as forums, user groups, and more
uuid: 51dc54da-9090-4d36-adf9-72d5479062a5
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: fbfe8097-3c3f-4a05-97ad-1ce526362a26
exl-id: 3ed3768a-1b3c-45a1-a34c-61694cd407d9
source-git-commit: d1b4cf87291f7e4a0670a21feca1ebf8dd5e0b5e
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 10%

---

# Entwickeln von Communities  {#developing-communities}

## Übersicht {#overview}

AEM Communities vereinfacht die Erstellung und Anpassung von Community-Funktionen wie Foren, Benutzergruppen, Blogs, Fragen und Antworten, Kalendern, Kommentaren, Rezensionen, Abstimmungen, Bewertungen und Zuweisungen. Diese Funktionen führen dazu, dass benutzergenerierte Inhalte (UGC) in die Veröffentlichungsumgebung eingegeben werden.

Die Grundlage eines [Community-Site](overview.md#communitiessites) ist die [Social-Komponenten-Framework](scf.md) (SCF). Die Erstellung einer Community-Site beginnt mit der Auswahl eines [Community-Site-Vorlage](sites-console.md) , das aus [Community-Funktionen](functions.md).

Einen Überblick und die ersten Schritte finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Einstieg in AEM Communities](getting-started.md)
* [Erste Schritte mit AEM Communities zur Aktivierung](getting-started-enablement.md)

>[!NOTE]
> 
>Es wird dringend empfohlen, mit dem [neueste Versionen](deploy-communities.md#latest-releases).

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
* [Handbuch zu Community-Komponenten](components-guide.md): interaktives Entwicklungstool.

## Komponenten, Funktionen und Funktionsgrundlagen {#component-function-and-feature-essentials}

AEM Communities-Komponenten, -Funktionen und -Funktionen stellen die Bausteine für [Community-Sites](sites-console.md).

* [Komponenten, Funktionen und Funktionsgrundlagen](essentials.md)
* [Clientlibs für Communities-Komponenten](clientlibs.md)
* [Community-Funktionen](functions.md)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Community-Site-Vorlagen](sites.md)

## Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Anmeldung über Social Media mit Facebook und Twitter](social-login.md)

## Community-Gruppen {#community-groups}

[Community-Gruppen](overview.md#communitygroups) ist das Konzept, es Community-Mitgliedern zu ermöglichen, Untergruppen innerhalb der Community-Site zu bilden. Die Erstellung einer Community-Gruppe kann in der Veröffentlichungs- oder Autorenumgebung erfolgen.

* [Community-Gruppengrundlagen](essentials-groups.md)
* [Gruppenfunktion](functions.md#groups-function)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Community-Gruppen für Autoren](creating-groups.md)

## Verwalten von Daten {#managing-data}

* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - Methoden und Beispiele für SRP-API-Dienstprogramme
* [Tag-Grundlagen](tag.md) - Möglichkeit für Community-Mitglieder, UGC und/oder katalogisierte Aktivierungsressourcen zu taggen

## Tutorials {#tutorials}

* [Clientseitige Tutorials](tutorials.md#client-side-customization)
* [Serverseitige Tutorials](tutorials.md#server-side-customization)
* [Anleitungen](tutorials.md#how-to-instructions)

## Fehlerbehebung {#troubleshooting}

* [Fehlerbehebung](troubleshooting.md)
* [Bekannte Probleme](/help/release-notes/release-notes.md)

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Besuch [Bereitstellen von Communities](deploy-communities.md) , um mehr über empfohlene Bereitstellungen und die Dispatcher-Konfiguration zu erfahren.

* Besuch [Verwalten von Communities-Sites](administer-landing.md) , um mehr über die Erstellung einer Community-Site, die Konfiguration von Community-Site-Vorlagen, die Moderation von Community-Inhalten, die Verwaltung von Mitgliedern und die Konfiguration von Messaging zu erfahren.

* Besuch [Erstellen von Communities-Komponenten](author-communities.md) , um zu erfahren, wie Sie Communities-Komponenten erstellen und konfigurieren.
