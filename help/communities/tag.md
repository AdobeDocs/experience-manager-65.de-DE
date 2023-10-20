---
title: Tag-Grundlagen
description: Erfahren Sie, wann Communities-Komponenten mit aktiviertem Tagging konfiguriert sind. Community-Mitglieder können Inhalte taggen, die sie in der Veröffentlichungsumgebung posten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 6e8af8cf-1239-46f9-b2fe-4aa80abc86ea
source-git-commit: f03d0ab9d0f491441378e16e1590d33651f064b5
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 3%

---

# Tag-Grundlagen {#tag-essentials}

Wenn AEM Communities-Komponenten mit aktiviertem Tagging konfiguriert sind, können Community-Mitglieder den Inhalt taggen, den sie in der Veröffentlichungsumgebung posten.

Die zugrunde liegende Infrastruktur für Tags, die in der Veröffentlichungsumgebung angewendet werden, entspricht der für Tags, die in der Autorenumgebung auf Inhalte angewendet werden, wie z. B. Seiten und Assets:

* Siehe [Verwalten von Tags](../../help/sites-administering/tags.md) und [Tagging benutzergenerierter Inhalte](tag-ugc.md) (UGC) für Informationen zum Erstellen und Verwalten von Tags.

* Siehe [Tagging für Entwickler](../../help/sites-developing/tags.md) für Informationen über [Tagging-Framework](../../help/sites-developing/framework.md) und die Erweiterung von Tags in [benutzerdefinierte Anwendungen](../../help/sites-developing/building.md).

* Siehe [Verwenden der Social Tag Cloud](tagcloud.md) für Informationen für Autoren zum Hinzufügen einer `social tag cloud` -Komponente auf eine Seite klicken, um die auf UGC angewandten Tags in der Veröffentlichungsumgebung hervorzuheben.

Das Tagging von benutzergenerierten Inhalten kann beim Konfigurieren eines [Community-Site](sites-console.md#tagging) oder einer der folgenden Funktionen:

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

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Social Tag Cloud-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Social Tag Manager](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

## Tag-Suche {#tag-searching}

Als [Feature Pack 1](deploy-communities.md#latestfeaturepack) (FP1) wird die Tag-Suche mithilfe von [Tag-Titel](../../help/sites-developing/framework.md#tag-characteristics).

Vor FP1 wurde die Suche mithilfe von [Tag-ID](../../help/sites-developing/framework.md#tagid).
