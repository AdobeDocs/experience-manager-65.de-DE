---
title: Entwicklungsländer
seo-title: Entwicklungsländer
description: Community-Funktionen wie Foren, Benutzergruppen und mehr erstellen und anpassen
seo-description: Community-Funktionen wie Foren, Benutzergruppen und mehr erstellen und anpassen
uuid: 51dc54da-9090-4d36-adf9-72d5479062a5
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: fbfe8097-3c3f-4a05-97ad-1ce526362a26
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 10%

---


# Developing Communities {#developing-communities}

## Überblick {#overview}

AEM Communities vereinfacht die Erstellung und Anpassung von Community-Funktionen wie Foren, Benutzergruppen, Blogs, Fragen und Antworten, Kalender, Kommentare, Rezensionen, Abstimmungen, Bewertungen und Zuweisungen. Diese Funktionen führen dazu, dass benutzergenerierte Inhalte (UGC) in die Umgebung &quot;Veröffentlichen&quot;eingegeben werden.

Die Grundlage einer [Community-Site](overview.md#communitiessites) ist das [Social-Komponenten-Framework](scf.md) (SCF). Die Erstellung einer Community-Site beginnt mit der Auswahl einer [Community-Site-Vorlage](sites-console.md), die aus [Community-Funktionen](functions.md) besteht.

Einen Überblick und die ersten Schritte finden Sie unter:

* [Übersicht über AEM Communities](overview.md)
* [Einstieg in AEM Communities](getting-started.md)
* [Erste Schritte mit AEM Communities zur Aktivierung](getting-started-enablement.md)

>[!NOTE]
> 
>Es wird dringend empfohlen, mit den [aktuellen Versionen](deploy-communities.md#latest-releases) auf dem Laufenden zu bleiben.

## Empfohlene Bereitstellungen {#recommended-deployments}

* [Community Content Datenspeicherung](working-with-srp.md): beschreibt die verfügbaren SRP-Optionen für einen UGC-gemeinsamen Store
* [Empfohlene Topologien für Communities](topologies.md): diskutiert Topologien auf der Grundlage von Anwendungsfällen und SRP-Auswahl.

## Social Component Framework {#social-component-framework}

* [Social-Komponenten-Framework](scf.md): Überblick über Framework und APIs.
* [SCF Handlebars Helpers](handlebars-helpers.md): Standard-Helfer und wie Sie benutzerdefinierte Helfer schreiben.
* [Clientseitige Anpassung](client-customize.md): Anpassen von Code, der im Browser ausgeführt wird.
* [Serverseitige Anpassung](server-customize.md): Anpassen von Code, der auf dem Server ausgeführt wird.
* [Datenspeicherung Resource Provider (SRP)](srp.md): Überblick über die Datenspeicherung von Community-Inhalten.
* [Kodierungsleitlinien](code-guide.md): Richtlinien, Tipps und Tricks.
* [Leitfaden](components-guide.md) zu Community-Komponenten: interaktives Entwicklungstool.

## Komponenten, Funktionen und Funktionsgrundlagen {#component-function-and-feature-essentials}

Komponenten, Funktionen und Funktionen von AEM Communities stellen die Bausteine für [Community-Sites](sites-console.md) bereit.

* [Komponenten, Funktionen und Funktionen](essentials.md)
* [Clientlibs für Communities-Komponenten](clientlibs.md)
* [Community-Funktionen](functions.md)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Community-Site-Vorlagen](sites.md)

## Community-Mitglieder {#community-members}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Social-Anmeldung bei Facebook und Twitter](social-login.md)

## Community-Gruppen {#community-groups}

[Community-](overview.md#communitygroups) Gruppierung ist das Konzept, dass Community-Mitgliedern erlaubt wird, Untergemeinschaften innerhalb der Community-Site zu bilden. Die Erstellung einer Community-Gruppe kann in der Umgebung &quot;Veröffentlichen&quot;oder &quot;Autor&quot;erfolgen.

* [Community-Gruppengrundlagen](essentials-groups.md)
* [Gruppenfunktion](functions.md#groups-function)
* [Community-Gruppen-Vorlagen](tools-groups.md)
* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Community-Gruppen für Autoren](creating-groups.md)

## Verwalten von Daten {#managing-data}

* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP API-Dienstprogrammmethoden und Beispiele
* [Tag Essentials](tag.md)  - Möglichkeit für Community-Mitglieder, UGC- und/oder katalogisierte Ressourcen für die Aktivierung zu taggen

## Tutorials {#tutorials}

* [clientseitige Übungen](tutorials.md#client-side-customization)
* [Serverseitige Übungen](tutorials.md#server-side-customization)
* [Anleitungen](tutorials.md#how-to-instructions)

## Fehlerbehebung {#troubleshooting}

* [Fehlerbehebung](troubleshooting.md)
* [Bekannte Probleme](/help/release-notes/known-issues.md)

## Communities-Dokumentation zu ähnlichen Themen {#related-communities-documentation}

* Besuchen Sie [Communities](deploy-communities.md) bereitstellen, um mehr über empfohlene Bereitstellungen und Dispatcher-Konfiguration zu erfahren.

* Besuchen Sie [Sites der Administrationsgemeinschaften](administer-landing.md), um mehr über die Erstellung einer Community-Site, die Konfiguration von Community-Site-Vorlagen, die Moderation von Community-Inhalten, die Verwaltung von Mitgliedern und die Konfiguration von Messaging zu erfahren.

* Unter [Komponenten für Authoring-Communities](author-communities.md) erfahren Sie, wie Sie mit Communities-Komponenten erstellen und konfigurieren.

