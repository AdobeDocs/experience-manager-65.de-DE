---
title: Grundlagen zum Aktivitäts-Stream
description: Liste der letzten Aktivitäten, die von einem Mitglied oder einer Liste der letzten Aktivitäten in einem einzigen Inhaltsthread durchgeführt wurden
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: d98bcbe4-3f80-49ec-b40c-417be0d97350
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# Grundlagen zum Aktivitäts-Stream {#activity-stream-essentials}

Die Aktivitäten eines angemeldeten Community-Mitglieds, z. B. das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der durch die Konfiguration der Aktivitäts-Streams-Komponente auf unterschiedliche Weise gefiltert und angezeigt werden kann.

Die Möglichkeit, zu folgen, fügt weitere Aktivitäten hinzu, wenn Community-Mitglieder Beiträge von Interesse oder anderen Community-Mitgliedern folgen.

Alle [Community-Sites](/help/communities/overview.md#communitiessites) enthalten eine Benutzerprofilseite für das angemeldete Mitglied, auf die die Mitgliederaktivitäten auf die gleiche Weise angezeigt werden.

## Konzepte {#concepts}

Ein *Aktivitäts-Stream* ist die Liste der letzten Aktivitäten, die von einem Mitglied ausgeführt wurden, oder eine Liste der letzten Aktivitäten in einem einzelnen Inhaltsthread, z. B. einem Forenthema oder einem Blog.

Ein Mitglied kann einem Aktivitäts-Stream folgen, indem es entweder einer anderen Person oder einem Inhalt folgt.

Ein *News-Feed* ist eine Zusammenführung der Aktivitäts-Streams, auf die ein Mitglied in einem einzigen Stream folgt.

Ein *[soziales Diagramm](/help/communities/essentials-socialgraph.md)* erfasst die folgenden Beziehungen zwischen einem Mitglied.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/activitystreams/components/hbs/activitystreams</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
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

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Aktivitäts-Streams-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [Aktivitäts-Streams-Listener-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Serverseitige Anpassungen](/help/communities/server-customize.md)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Eine Community-Site-Struktur, die die [Aktivitäts-Stream-Funktion](/help/communities/functions.md#activity-stream-function) enthält, enthält eine konfigurierte `activity streams` -Komponente.
