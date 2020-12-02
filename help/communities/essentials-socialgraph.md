---
title: Grundlagen zu Social-Diagrammen
seo-title: Grundlagen zu Social-Diagrammen
description: Folgen Sie der Komponente und der folgenden Komponentenübersicht
seo-description: Folgen Sie der Komponente und der folgenden Komponentenübersicht
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 13%

---


# Grundlagen zu Social-Diagrammen {#social-graph-essentials}

Die Fähigkeit eines Community-Mitglieds, [Aktivitäten](essentials-activities.md) zu befolgen, wird durch zwei Komponenten ermittelt:

Die `following`-Komponente muss mit einer anderen Ressource verknüpft sein. Diese Zuordnung ist bereits für bestehende Communities-Mitglieder und -Funktionen auf einer [Community-Site](overview.md#communitiessites) eingerichtet.

Die `following`-Komponente Liste die Member, die dem aktuellen Member folgen oder denen das aktuelle Member folgt. Dieses Sozialdiagramm der Mitgliederbeziehungen untereinander ist Teil des Benutzerprofils, das für eine Community-Site bereitgestellt wird.

## Grundlagen für clientseitige {#essentials-for-client-side}

### Folgende {#following}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/socialgraph/components/hbs/relations</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
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
   <td>Siehe <a href="socialgraph.md">Soziales Diagramm verwenden</a></td>
  </tr>
  <tr>
   <td><strong> optional<br />-Eigenschaft</strong></td>
   <td>
    <ul>
     <li>Name: <strong><code>outgoing</code></strong></li>
     <li>Typ: Boolesch</li>
     <li>Wert:<br />
      <ul>
       <li><i>True  </i>- Die  <code>following</code> Komponente Liste die Mitglieder, die das derzeit angemeldete Mitglied sind. <code>follows</code></li>
       <li><i>FALSE  </i>- Die  <code>following</code> Komponente Liste die Mitglieder,  <code>follow </code>die derzeit angemeldet sind.</li>
      </ul> </li>
    </ul> <p>Die Standardeinstellung ist <i>true</i>, wenn die Eigenschaft fehlt. Derzeit ist es nicht möglich, diese Eigenschaft im Bearbeitungsdialogfeld im Autorenmodus festzulegen. Die Eigenschaft muss mit <code>following </code>CRXDE|Lite<a href="../../help/sites-developing/developing-with-crxde-lite.md"> einer Instanz des Knotens hinzugefügt werden.</a></p> </td>
  </tr>
 </tbody>
</table>

### Folgen {#follow}

| **resourceType** | `social/socialgraph/components/hbs/following` |
|---|---|
| [**einschließbar**](scf.md#add-or-include-a-communities-component) | Nein |
| **templates** | `/libs/social/socialgraph/components/hbs/following/following.hbs` |
| **css** | `/libs/social/socialgraph/components/hbs/following/clientlibs/following.css` |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Social Graph-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Social Graph-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Serverseitige Anpassungen](server-customize.md)

