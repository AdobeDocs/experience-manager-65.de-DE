---
title: Aktivität Stream Essentials
seo-title: Aktivität Stream Essentials
description: Liste der zuletzt durchgeführten Aktivitäten eines Mitglieds oder einer Liste der letzten Aktivitäten in einem einzigen Inhaltsthread
seo-description: Liste der zuletzt durchgeführten Aktivitäten eines Mitglieds oder einer Liste der letzten Aktivitäten in einem einzigen Inhaltsthread
uuid: 30c5ac08-0af0-4670-9d81-0beb5c93e00a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8714b456-527a-457b-82c4-21bd445dfd9c
docset: aem65
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 2%

---


# Aktivität Stream Essentials {#activity-stream-essentials}

Die Aktivitäten eines in einem Community-Mitglied unterschriebenen Mitglieds, wie z.B. das Posten in einem Forum oder Blog, werden in einem Stream gesammelt, der durch die Konfiguration der Aktivität Streams-Komponente gefiltert und auf verschiedene Weise angezeigt werden kann.

Die Möglichkeit zu folgen, fügt weitere Aktivitäten hinzu, wenn Community-Mitglieder Beiträge von Interesse oder andere Community-Mitglieder folgen.

Alle [Community-Sites](/help/communities/overview.md#communitiessites) beinhalten eine Benutzerseite für das angemeldete Profil, auf der die Mitgliederseiten auf dieselbe Weise angezeigt werden.

## Konzepte {#concepts}

Ein *Aktivität-Stream* ist die Liste der letzten Aktivitäten, die von einem Mitglied oder einer Liste der letzten Aktivitäten an einem einzigen Inhaltsthread wie einem Forenthema oder einem Blog durchgeführt wurden.

Ein Mitglied kann einem Aktivitäten-Stream folgen, indem es entweder einer anderen Einzelperson oder einem anderen Inhalt folgt.

Ein *News-Feed* ist eine Zusammenführung der Aktivitäten-Streams, denen ein Mitglied gefolgt ist, in einem Stream.

Ein *[Social Graph](/help/communities/essentials-socialgraph.md)* erfasst die folgenden Beziehungen eines Mitglieds zum anderen.

## Grundlagen für clientseitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/activitystreams/components/hbs/activitystreams</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.activitystreams</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="/help/communities/activities.md">Aktivität Streams-Funktion</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Aktivität Streams API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Aktivität Streams Listener API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Serverseitige Anpassungen](/help/communities/server-customize.md)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Eine Community-Site-Struktur, die die [Aktivität-Stream-Funktion](/help/communities/functions.md#activity-stream-function) enthält, enthält eine konfigurierte `activity streams`-Komponente.
