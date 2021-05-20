---
title: Grundlagen zum Aktivitäts-Stream
seo-title: Grundlagen zum Aktivitäts-Stream
description: Liste der letzten Aktivitäten, die von einem Mitglied durchgeführt wurden, oder Liste der letzten Aktivitäten in einem einzelnen Inhaltsthread
seo-description: Liste der letzten Aktivitäten, die von einem Mitglied durchgeführt wurden, oder Liste der letzten Aktivitäten in einem einzelnen Inhaltsthread
uuid: 30c5ac08-0af0-4670-9d81-0beb5c93e00a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8714b456-527a-457b-82c4-21bd445dfd9c
docset: aem65
exl-id: d98bcbe4-3f80-49ec-b40c-417be0d97350
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 2%

---

# Aktivitäts-Stream-Grundlagen {#activity-stream-essentials}

Die Aktivitäten eines angemeldeten Community-Mitglieds, z. B. das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der durch die Konfiguration der Aktivitäts-Streams-Komponente auf unterschiedliche Weise gefiltert und angezeigt werden kann.

Die Möglichkeit, zu folgen, fügt weitere Aktivitäten hinzu, wenn Community-Mitglieder Beiträge von Interesse oder anderen Community-Mitgliedern folgen.

Alle [Community-Sites](/help/communities/overview.md#communitiessites) enthalten eine Benutzerprofilseite für das angemeldete Mitglied, auf die die Mitgliederaktivitäten auf die gleiche Weise angezeigt werden.

## Konzepte  {#concepts}

Ein *Aktivitäts-Stream* ist die Liste der letzten Aktivitäten, die von einem Mitglied durchgeführt wurden, oder eine Liste der letzten Aktivitäten in einem einzelnen Inhaltsthread, z. B. einem Forenthema oder einem Blog.

Ein Mitglied kann einem Aktivitäts-Stream folgen, indem es entweder einer anderen Person oder einem Inhalt folgt.

Ein *News-Feed* ist eine Zusammenführung der Aktivitäts-Streams, auf die ein Mitglied folgt, in einem einzigen Stream.

Ein *[Social Graph](/help/communities/essentials-socialgraph.md)* erfasst die folgenden Beziehungen eines Mitglieds zum anderen.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/activitystreams/components/hbs/activitystreams</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td>
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
   <td>Siehe <a href="/help/communities/activities.md">Aktivitäts-Streams-Funktion</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Aktivitäts-Streams-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Activity Streams Listener-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Serverseitige Anpassungen](/help/communities/server-customize.md)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Eine Community-Site-Struktur, die die [Aktivitäts-Stream-Funktion](/help/communities/functions.md#activity-stream-function) enthält, enthält eine konfigurierte `activity streams`-Komponente.
