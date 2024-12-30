---
title: Tag Essentials
description: Erfahren Sie, wie Community-Komponenten mit aktiviertem Tagging konfiguriert werden und Community-Mitglieder Inhalte taggen können, die sie in der Veröffentlichungsumgebung posten.
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

# Tag Essentials {#tag-essentials}

Wenn AEM Communities-Komponenten mit aktiviertem Tagging konfiguriert sind, können Community-Mitglieder den Inhalt, den sie in der Veröffentlichungsumgebung posten, mit Tags versehen.

Die zugrunde liegende Infrastruktur für Tags, die in der Veröffentlichungsumgebung angewendet werden, ist dieselbe wie für Tags, die auf Inhalte in der Autorenumgebung, z. B. Seiten und Assets, angewendet werden:

* Informationen [ Erstellen und Verwalten von Tags finden ](../../help/sites-administering/tags.md) unter Verwalten [ Tags und Tagging ](tag-ugc.md) benutzergenerierten Inhalten UGC).

* Unter [Tagging für Entwickler](../../help/sites-developing/tags.md) finden Sie Informationen über das [Tagging-Framework](../../help/sites-developing/framework.md) sowie die Einbeziehung und Erweiterung von Tags in [benutzerdefinierten Anwendungen](../../help/sites-developing/building.md).

* Informationen [ Autoren zum Hinzufügen einer `social tag cloud`-Komponente zu einer Seite, um die Tags hervorzuheben, die in der Veröffentlichungsumgebung auf benutzergenerierten Inhalt (UGC) angewendet werden, finden Sie unter „Verwenden von Social Tag ](tagcloud.md)&quot;.

Das Tagging von benutzergenerierten Inhalten kann bei der Konfiguration einer [Community-Site](sites-console.md#tagging) oder einer der folgenden Funktionen aktiviert werden:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md)
* [Fragen und Antworten](working-with-qna.md)

## Grundlagen für Client-seitige {#essentials-for-client-side}

### Social Tag-Cloud {#social-tag-cloud}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/commons/components/hbs/tagcloud</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td>
   <td>cq.social.hbs.tagcloud</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/tagcloud.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/commons/components/hbs/tagcloud/clientlibs/tagcloud.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="tagcloud.md">Verwenden von Social Tag Cloud</a></td>
  </tr>
 </tbody>
</table>

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Social Tag Cloud-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagcloud/api/package-summary.html)

* [Social Tag Manager](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/tagging/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

## Tag-Suche {#tag-searching}

Ab [Feature Pack 1](deploy-communities.md#latestfeaturepack) (FP1) wird die Tag-Suche mit „Tag[Titeln“ ](../../help/sites-developing/framework.md#tag-characteristics).

Vor FP1 wurde die Suche mit „Tag[IDs“ ](../../help/sites-developing/framework.md#tagid).
