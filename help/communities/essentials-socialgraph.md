---
title: Grundlagen zu Social-Diagrammen
description: Erfahren Sie mehr über die Grundlagen des Social-Diagramms mit den Komponenten "Folgende"und "Folgen"auf einer Community-Site.
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

# Grundlagen zu Social-Diagrammen  {#social-graph-essentials}

Die Fähigkeit eines Community-Mitglieds, [Aktivitäten](essentials-activities.md) zu folgen und ihnen zu folgen, wird durch zwei Komponenten festgelegt:

Die Komponente `following` muss mit einer anderen Ressource verknüpft sein, und diese Zuordnung ist bereits für bestehende Community-Mitglieder und -Funktionen auf einer [Community-Site](overview.md#communitiessites) eingerichtet.

Die Komponente `following` listet die Mitglieder auf, die dem aktuellen Mitglied folgen oder dem aktuellen Mitglied folgen. Dieses soziale Diagramm der Beziehungen zwischen Mitgliedern ist in das für eine Community-Site eingerichtete Benutzerprofil aufgenommen.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

### Folgende {#following}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/socialgraph/components/hbs/relations</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.socialgraph</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="socialgraph.md">Verwenden des Social-Diagramms</a></td>
  </tr>
  <tr>
   <td><strong> optional<br /> Eigenschaft</strong></td>
   <td>
    <ul>
     <li>Name: <strong><code>outgoing</code></strong></li>
     <li>Typ: Boolesch</li>
     <li>Wert:<br />
      <ul>
       <li><i>True </i> - Die Komponente <code>following</code> listet die Mitglieder auf, die das angemeldete Mitglied sind <code>follows</code></li>
       <li><i>False </i> - Die Komponente <code>following</code> listet die Mitglieder auf, die <code>follow </code>das angemeldete Mitglied sind</li>
      </ul> </li>
    </ul> <p>Der Standardwert ist <i>true</i> , wenn die Eigenschaft fehlt. Es ist nicht möglich, diese Eigenschaft im Bearbeitungsdialogfeld im Autorenmodus festzulegen. Die Eigenschaft muss mithilfe von <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a> einer Instanz des Knotens <code>following</code> hinzugefügt werden.</p> </td>
  </tr>
 </tbody>
</table>

### Folgen {#follow}

| **resourceType** | `social/socialgraph/components/hbs/following` |
|---|---|
| [**include**](scf.md#add-or-include-a-communities-component) | Nein |
| **templates** | `/libs/social/socialgraph/components/hbs/following/following.hbs` |
| **css** | `/libs/social/socialgraph/components/hbs/following/clientlibs/following.css` |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Social Graph-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Social-Graph-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Serverseitige Anpassungen](server-customize.md)
