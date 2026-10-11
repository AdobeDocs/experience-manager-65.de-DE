---
title: Aktivitäts-Stream-Grundlagen
description: Liste der letzten Aktivitäten, die ein Mitglied ausgeführt hat, oder Liste der letzten Aktivitäten in einem einzelnen Inhalts-Thread
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: d98bcbe4-3f80-49ec-b40c-417be0d97350
solution: Experience Manager
feature: Communities
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 2%
---
# Aktivitäts-Stream-Grundlagen {#activity-stream-essentials}

Die Aktivitäten eines angemeldeten Community-Mitglieds, z. B. das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der auf verschiedene Arten gefiltert und angezeigt werden kann, indem die Aktivitäts-Streams-Komponente konfiguriert wird.

Die Möglichkeit, zu folgen, fügt weitere Aktivitäten hinzu, wenn Community-Mitglieder Postings von Interesse oder anderen Community-Mitgliedern folgen.

Alle [Community-Sites](/help/communities/overview.md#communitiessites) enthalten eine Benutzerprofilseite für das angemeldete Mitglied, auf der Mitgliederaktivitäten auf die gleiche Weise angezeigt werden.

## Konzepte {#concepts}

Ein *Aktivitäts-Stream* ist die Liste der letzten Aktivitäten, die von einem Mitglied durchgeführt wurden, oder eine Liste der letzten Aktivitäten in einem einzelnen Thread mit Inhalten, wie z. B. ein Forumsthema oder ein Blog.

Ein Mitglied kann einem Aktivitäts-Stream folgen, indem es entweder einer anderen Person oder einem Inhalt folgt.

Ein *News-Feed* ist eine Zusammenführung der Aktivitäts-Streams, auf die ein Mitglied folgt, zu einem einzigen Stream.

Ein *[Sozialdiagramm](/help/communities/essentials-socialgraph.md)* erfasst die folgenden Beziehungen von einem Mitglied zum anderen.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/activityStreams/components/hbs/activityStreams</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientlibs</strong></a></td>
   <td>CQ.social.hbs.ActivityStreams</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
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

* [Client-seitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Aktivitäts-Streams-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Activity Streams-Listener-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Server-seitige Anpassungen](/help/communities/server-customize.md)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Eine Community-Site-Struktur mit der [Aktivitäts-Stream](/help/communities/functions.md#activity-stream-function)-Funktion enthält eine konfigurierte `activity streams`.
