---
title: Komponenten, Funktionen und Funktionsgrundlagen
seo-title: Komponenten, Funktionen und Funktionsgrundlagen
description: Funktionsweise von Community-Sites, -Vorlagen und -Gruppen
seo-description: Funktionsweise von Community-Sites, -Vorlagen und -Gruppen
uuid: 6edfca2d-fe5b-4261-b033-51dc2f9dbfd7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 2d308756-79d1-4d69-b51c-d4b6e692a137
exl-id: a43c1c4d-a6c2-4ef9-9047-a945978e618b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 18%

---

# Komponenten-, Funktionen- und Funktionsgrundlagen {#component-function-and-feature-essentials}

AEM Communities-Funktionen erfordern, dass Site-Besucher Mitglieder werden und sich bei der [Community-Site](overview.md#communitiessites) anmelden, bevor sie Inhalte posten können. Daher sind [Community-Site-Vorlagen](sites.md), von denen eine Community-Site [erstellt](sites-console.md) ist, so konzipiert, dass sie eine Anmeldungsfunktion sowie Benutzerprofile, Messaging, Suche, Moderation und Übersetzung enthalten.

Eine Community-Site unterstützt Mitglieder, die Community-Gruppen erstellen, wenn die [Community-Gruppen-Funktion](functions.md#groups-function) in der ausgewählten Community-Site-Vorlage enthalten ist.

Im Folgenden finden Sie Links zu wichtigen Informationen zu Communities-Komponenten, -Funktionen und -Funktionen.

## Basiskomponenten {#base-components}

* [Kommentare](essentials-comments.md)
* [Reviews](reviews-basics.md)
* [Tally](tally.md)

   * [Likes](essentials-liking.md)
   * [Bewertung](rating-basics.md)
   * [Abstimmung](essentials-voting.md)
   * *Umfrage (nicht mehr verfügbar)*

## Komponenten mit Funktionen {#components-with-functions}

* [Aktivitäts-Streams](essentials-activities.md)
* [Zuweisungen](essentials-assignments.md)
* [Blog](blog-developer-basics.md) ( `Journal`)

* [Kalender](calendar-basics-for-developers.md)
* [Katalog](catalog-developer-essentials.md)
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
* [Storage Resource Provider](srp-and-ugc.md) `(SRP)`

* [Tagging](tag.md)

## Javadocs {#javadocs}

Die [Online-Javadocs](../../help/sites-developing/reference-materials.md) spiegeln die APIs wider, die in AEM Version 6.3 verfügbar sind.
Communities-APIs befinden sich in `com.adobe.cq.social.*`-Paketen.

Für jedes [Feature Pack](deploy-communities.md#latestfeaturepack) wird eine JavaScript-JAR bereitgestellt. Weitere Informationen finden Sie unter [Verwenden von Maven für Communities](maven.md#javadocs).

## Zusätzliche Informationen {#additional-information}

* [Social Component Framework (SCF)](scf.md)

   * [Clientseitige Anpassungen](client-customize.md)
   * [Serverseitige Anpassungen](server-customize.md)
   * [Übersicht über den Speicheranbieter](srp.md)

* [Kodierungsrichtlinien ](code-guide.md)
* [Tutorials](tutorials.md)
* [Fehlerbehebung](troubleshooting.md)
