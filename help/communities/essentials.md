---
title: Komponenten, Funktionen und Funktionsgrundlagen
description: Funktionsweise von Community-Sites, Vorlagen und Gruppen
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

# Komponenten, Funktionen und Funktionsgrundlagen  {#component-function-and-feature-essentials}

Adobe Experience Manager (AEM) Communities-Funktionen erfordern, dass Site-Besucher Mitglieder werden und sich bei der [Community-Site](overview.md#communitiessites) anmelden, bevor sie Inhalte veröffentlichen können. Daher sind [Community-Site-Vorlagen](sites.md), aus denen eine Community-Site [erstellt wurde](sites-console.md), so konzipiert, dass sie eine Anmeldefunktion und Benutzerprofile, Messaging, Suche, Moderation und Übersetzung enthalten.

Eine Community-Site unterstützt Mitglieder, die Community-Gruppen erstellen, wenn die Funktion [Community-Gruppen](functions.md#groups-function) in der ausgewählten Community-Site-Vorlage enthalten ist.

Im Folgenden finden Sie Links zu wichtigen Informationen zu Communities-Komponenten, -Funktionen und -Funktionen.

## Basiskomponenten {#base-components}

* [Kommentare](essentials-comments.md)
* [Bewertungen](reviews-basics.md)
* [Tally](tally.md)

   * [Likes](essentials-liking.md)
   * [Bewertung](rating-basics.md)
   * [Abstimmung](essentials-voting.md)
   * *Umfrage (nicht mehr verfügbar)*

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
* [Komponenten-Sideloading](sideloading.md)
* [Messaging](essentials-messaging.md)
* [Rich-Text-Editor](rte.md)
* [Scoring und Abzeichen](configure-scoring.md)
* [Suchen](search-implementation.md)
* [Soziales Diagramm](essentials-socialgraph.md)
* [Speicherressourcenanbieter](srp-and-ugc.md) `(SRP)`

* [Tagging](tag.md)

## Javadocs {#javadocs}

Die [Online-JavaAdocs](../../help/sites-developing/reference-materials.md) entsprechen den APIs, die in AEM Version 6.3 verfügbar sind.
Communities-APIs befinden sich in `com.adobe.cq.social.*` -Paketen.

Für jedes [Feature Pack](deploy-communities.md#latestfeaturepack) wird eine JavaScript-JAR bereitgestellt. Weitere Informationen finden Sie unter [Verwenden von Maven für Communities](maven.md#javadocs).

## Zusätzliche Informationen {#additional-information}

* [Social Component Framework (SCF)](scf.md)

   * [Clientseitige Anpassungen](client-customize.md)
   * [Serverseitige Anpassungen](server-customize.md)
   * [Übersicht über den Speicheranbieter](srp.md)

* [Codierungsrichtlinien ](code-guide.md)
* [Tutorials](tutorials.md)
* [Fehlerbehebung](troubleshooting.md)
