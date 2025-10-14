---
title: Grundlagen zu Social Graph
description: Erfahren Sie mehr über die Grundlagen des sozialen Diagramms, indem Sie die folgenden und folgenden Komponenten auf einer Community-Site verwenden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: c037a788-c943-4f95-a028-1fcb0ef48f86
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 4%

---

# Grundlagen zu Social Graph  {#social-graph-essentials}

Die Fähigkeit eines Mitglieds der Community, [Aktivitäten](essentials-activities.md) zu verfolgen, wird durch zwei Komponenten festgelegt:

Die `following`-Komponente muss mit einer anderen Ressource verknüpft sein, und diese Verknüpfung wurde bereits für bestehende Community-Mitglieder und -Funktionen auf einer [Community-Site“ &#x200B;](overview.md#communitiessites).

Die `following`-Komponente listet die Elemente auf, die entweder auf das aktuelle Element folgen oder auf die das aktuelle Element folgt. Dieses soziale Diagramm von Beziehungen zwischen Mitgliedern ist im Benutzerprofil enthalten, das für eine Community-Site erstellt wurde.

## Grundlagen für Client-seitige {#essentials-for-client-side}

### Folgende {#following}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/socialGraph/components/hbs/relations</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td>
   <td>cq.social.hbs.socialgraph</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="socialgraph.md">Verwenden von Social Graph</a></td>
  </tr>
  <tr>
   <td><strong> optional<br /> Eigenschaft</strong></td>
   <td>
    <ul>
     <li>Name: <strong><code>outgoing</code></strong></li>
     <li>Typ: Boolesch</li>
     <li>Wert:<br />
      <ul>
       <li><i>True </i>- Die <code>following</code>-Komponente listet die Mitglieder auf, die das angemeldete Mitglied sind <code>follows</code></li>
       <li><i>False </i>- Die <code>following</code>-Komponente listet die Mitglieder auf, die <code>follow </code> angemeldetes Mitglied sind</li>
      </ul> </li>
    </ul> <p>Die Standardeinstellung ist <i>true</i>, wenn die Eigenschaft fehlt. Es ist nicht möglich, diese Eigenschaft mithilfe des Bearbeitungsdialogfelds im Autorenmodus festzulegen. Die Eigenschaft muss mithilfe von „CRXDE|Lite“ zu einer Instanz des <code>following</code>-<a href="../../help/sites-developing/developing-with-crxde-lite.md"> hinzugefügt </a>.</p> </td>
  </tr>
 </tbody>
</table>

### Folgen {#follow}

| **resourceType** | `social/socialgraph/components/hbs/following` |
|---|---|
| [**inklusive**](scf.md#add-or-include-a-communities-component) | Nein |
| **Vorlagen** | `/libs/social/socialgraph/components/hbs/following/following.hbs` |
| **css** | `/libs/social/socialgraph/components/hbs/following/clientlibs/following.css` |

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Social-Graph-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Endpunkte für soziale Diagramme](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Server-seitige Anpassungen](server-customize.md)
