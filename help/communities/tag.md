---
title: Tag-Grundlagen
description: Erfahren Sie, wann Communities-Komponenten mit aktiviertem Tagging konfiguriert sind. Community-Mitglieder können Inhalte taggen, die sie in der Veröffentlichungsumgebung posten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 6e8af8cf-1239-46f9-b2fe-4aa80abc86ea
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 4%

---

# Tag-Grundlagen {#tag-essentials}

Wenn AEM Communities-Komponenten mit aktiviertem Tagging konfiguriert sind, können Community-Mitglieder den Inhalt taggen, den sie in der Veröffentlichungsumgebung posten.

Die zugrunde liegende Infrastruktur für Tags, die in der Veröffentlichungsumgebung angewendet werden, entspricht der für Tags, die in der Autorenumgebung auf Inhalte angewendet werden, wie z. B. Seiten und Assets:

* Informationen zum Erstellen und Verwalten von Tags finden Sie unter [Verwalten von Tags](../../help/sites-administering/tags.md) und [Tagging benutzergenerierter Inhalte](tag-ugc.md) (UGC).

* Informationen zum Tagging-Framework [ und zum Einschließen und Erweitern von Tags in [benutzerdefinierte Anwendungen](../../help/sites-developing/building.md) finden Sie unter [Tagging für Entwickler](../../help/sites-developing/tags.md) .](../../help/sites-developing/framework.md)

* Unter [Verwenden der Social Tag Cloud](tagcloud.md) finden Sie Informationen für Autoren dazu, wie eine `social tag cloud` -Komponente zu einer Seite hinzugefügt wird, um die auf UGC angewandten Tags in der Veröffentlichungsumgebung hervorzuheben.

Das Tagging von UGC kann beim Konfigurieren einer [Community-Site](sites-console.md#tagging) oder einer der folgenden Funktionen aktiviert werden:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md)
* [Fragen und Antworten](working-with-qna.md)

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

### Social Tag-Cloud {#social-tag-cloud}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/commons/components/hbs/tagcloud</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.tagcloud</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="tagcloud.md">Verwenden von Social Tag Cloud</a> .</td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Social Tag Cloud-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Social Tag-Manager](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

## Tag-Suche {#tag-searching}

Ab [Feature Pack 1](deploy-communities.md#latestfeaturepack) (FP1) wird die Tag-Suche mit [Tag-Titeln](../../help/sites-developing/framework.md#tag-characteristics) durchgeführt.

Vor FP1 wurde die Suche mit [Tag-IDs](../../help/sites-developing/framework.md#tagid) durchgeführt.
