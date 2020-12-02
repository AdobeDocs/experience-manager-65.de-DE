---
title: Tag Essentials
seo-title: Tag Essentials
description: Tag-Übersicht
seo-description: Tag-Übersicht
uuid: a5d52319-f821-4608-b0ab-abc8a1374343
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d355a3ee-c8a8-4a07-8d28-d1a99bda315c
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 4%

---


# Tag Essentials {#tag-essentials}

Wenn AEM Communities-Komponenten mit aktiviertem Tagging konfiguriert sind, können Community-Mitglieder den Inhalt taggen, den sie in der Umgebung veröffentlichen veröffentlichen.

Die zugrunde liegende Infrastruktur für Tags, die in der Umgebung &quot;Veröffentlichen&quot;angewendet werden, ist die gleiche wie für Tags, die in der Autoreninhalt-Umgebung angewendet werden, wie z. B. Seiten und Assets:

* Informationen zum Erstellen und Verwalten von Tags finden Sie unter [Verwalten von Tags](../../help/sites-administering/tags.md) und [Tagging von benutzergenerierten Inhalten](tag-ugc.md) (UGC).

* Weitere Informationen zum [Tagging-Framework](../../help/sites-developing/framework.md) sowie zum Einschließen und Erweitern von Tags in [benutzerdefinierten Anwendungen](../../help/sites-developing/building.md) finden Sie unter [Tagging für Entwickler](../../help/sites-developing/tags.md).

* Unter [Verwenden der Social Tag Cloud](tagcloud.md) finden Sie Informationen für Autoren dazu, wie Sie einer Seite eine `social tag cloud`-Komponente hinzufügen können, um die Tags hervorzuheben, die in der Umgebung &quot;Veröffentlichen&quot;auf UGC angewendet wurden.

* Informationen zum Tagging von Ressourcen für Kataloge finden Sie unter [Tagging-Aktivierungsressourcen](tag-resources.md).

Das Tagging von UGC kann aktiviert werden, wenn eine [Community-Site](sites-console.md#tagging) oder eine der folgenden Funktionen konfiguriert wird:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md)
* [Frage und Antwort](working-with-qna.md)

## Grundlagen für clientseitige {#essentials-for-client-side}

### Social-Tag-Cloud {#social-tag-cloud}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/commons/components/hbs/tagcloud</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
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

* [Social Tag-Manager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

## Tag-Suche {#tag-searching}

Ab [Feature Pack 1](deploy-communities.md#latestfeaturepack) (FP1) wird die Tag-Suche mit [Tag-Titeln](../../help/sites-developing/framework.md#tag-characteristics) durchgeführt.

Vor FP1 wurde die Suche mit [Tag-IDs](../../help/sites-developing/framework.md#tagid) durchgeführt.
