---
title: Tag-Grundlagen
seo-title: Tag-Grundlagen
description: Tag-Übersicht
seo-description: Tag-Übersicht
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
exl-id: 6e8af8cf-1239-46f9-b2fe-4aa80abc86ea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 4%

---

# Tag-Grundlagen {#tag-essentials}

Wenn AEM Communities-Komponenten mit aktiviertem Tagging konfiguriert sind, können Community-Mitglieder den Inhalt taggen, den sie in der Veröffentlichungsumgebung posten.

Die zugrunde liegende Infrastruktur für Tags, die in der Veröffentlichungsumgebung angewendet werden, entspricht der für Tags, die in der Autorenumgebung auf Inhalte angewendet werden, wie z. B. Seiten und Assets:

* Informationen zum Erstellen und Verwalten von Tags finden Sie unter [Verwalten von Tags](../../help/sites-administering/tags.md) und [Tagging benutzergenerierter Inhalte](tag-ugc.md) (UGC).

* Informationen zum [Tagging-Framework](../../help/sites-developing/framework.md) sowie zum Einschließen und Erweitern von Tags in [benutzerdefinierten Anwendungen](../../help/sites-developing/building.md) finden Sie unter ](../../help/sites-developing/tags.md) .[

* Informationen für Autoren zum Hinzufügen einer `social tag cloud`-Komponente zu einer Seite finden Sie unter [Verwenden der Social Tag Cloud](tagcloud.md) , um die auf UGC angewandten Tags in der Veröffentlichungsumgebung hervorzuheben.

* Informationen zum Tagging von Ressourcen für Kataloge finden Sie unter [Tagging von Aktivierungsressourcen](tag-resources.md) .

Das Tagging von UGC kann beim Konfigurieren einer [Community-Site](sites-console.md#tagging) oder einer der folgenden Funktionen aktiviert werden:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md)
* [Frage und Antwort](working-with-qna.md)

## Grundlagen für Client-seitige {#essentials-for-client-side}

### Social-Tag-Cloud {#social-tag-cloud}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/commons/components/hbs/tagcloud</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td>
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
   <td>Siehe <a href="tagcloud.md">Verwenden der Social Tag Cloud</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Social Tag Cloud-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Social Tag Manager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

## Tag-Suche {#tag-searching}

Ab [Feature Pack 1](deploy-communities.md#latestfeaturepack) (FP1) wird die Tag-Suche mit [Tag-Titeln](../../help/sites-developing/framework.md#tag-characteristics) durchgeführt.

Vor FP1 wurde die Suche mit [Tag-IDs](../../help/sites-developing/framework.md#tagid) durchgeführt.
