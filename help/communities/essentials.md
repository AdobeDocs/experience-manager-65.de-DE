---
title: Komponenten-, Funktions- und Funktionsgrundlagen
description: Funktionsweise von Community-Sites, -Vorlagen und -Gruppen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: a43c1c4d-a6c2-4ef9-9047-a945978e618b
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---

# Komponenten-, Funktions- und Funktionsgrundlagen  {#component-function-and-feature-essentials}

Adobe Experience Manager (AEM) Communities-Funktionen erfordern, dass Besuchende der Site Mitglied werden und sich bei der [Community-Site](overview.md#communitiessites) anmelden, bevor sie Inhalte posten können. Daher [Community-Site-Vorlagen](sites.md) aus denen eine Community-Site [erstellt](sites-console.md) erstellt wird, so konzipiert, dass sie eine Anmeldefunktion und Benutzerprofile, Messaging, Suche, Moderation und Übersetzung enthalten.

Eine Community-Site unterstützt Mitglieder beim Erstellen von Community[Gruppen, wenn die Funktion &#x200B;](functions.md#groups-function)Community-Gruppen“ in der ausgewählten Community-Site-Vorlage enthalten ist.

Im Folgenden finden Sie Links zu wichtigen Informationen zu Komponenten, Funktionen und Funktionen von Communities.

## Basiskomponenten {#base-components}

* [Kommentare](essentials-comments.md)
* [Bewertungen](reviews-basics.md)
* [Strichliste](tally.md)

   * [Likes](essentials-liking.md)
   * [Bewertung](rating-basics.md)
   * [Abstimmung](essentials-voting.md)
   * *Abfrage (nicht mehr verfügbar)*

## Komponenten mit Funktionen {#components-with-functions}

* [Aktivitäts-Streams](essentials-activities.md)
* [Blog](blog-developer-basics.md) ( `Journal`)

* [Kalender](calendar-basics-for-developers.md)
* [Präsentierter Inhalt](essentials-featured.md)
* [Dateibibliothek](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [Gruppen](essentials-groups.md)
* [Ideen](ideation.md)
* [Leaderboard](leaderboard.md)
* [Fragen und Antworten](qna-essentials.md) `(QnA)`

## Funktionen {#features}

* [Client-Bibliotheken](clientlibs.md)
* [Community-Sites](sites-for-developers.md)
* [Komponenten-OSGi-Ereignisse](events.md)
* [Komponenten-Seitenladevorgang](sideloading.md)
* [Messaging](essentials-messaging.md)
* [Rich-Text-Editor](rte.md)
* [Punktzahl und Abzeichen](configure-scoring.md)
* [Suchen](search-implementation.md)
* [Soziales Diagramm](essentials-socialgraph.md)
* [Speicherressourcenanbieter](srp-and-ugc.md) `(SRP)`

* [Tagging](tag.md)

## Javadocs {#javadocs}

Die [Online](../../help/sites-developing/reference-materials.md)Javadocs spiegeln die in der Version AEM 6.3 verfügbaren APIs wider.
Communities-APIs sind in `com.adobe.cq.social.*` Paketen enthalten.

Für jedes [Feature Pack](deploy-communities.md#latestfeaturepack) wird eine JavaDoc-JAR bereitgestellt. Weitere Informationen finden Sie unter [Verwenden von Maven für Communities](maven.md#javadocs).

## Zusätzliche Informationen {#additional-information}

* [Social Component Framework (SCF)](scf.md)

   * [Client-seitige Anpassungen](client-customize.md)
   * [Server-seitige Anpassungen](server-customize.md)
   * [Speicherressourcenanbieter - Übersicht](srp.md)

* [Codierungsrichtlinien &#x200B;](code-guide.md)
* [Tutorials](tutorials.md)
* [Fehlerbehebung](troubleshooting.md)
