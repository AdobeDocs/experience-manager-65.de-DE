---
title: Grundlagen zu Social-Diagrammen
seo-title: Grundlagen zu Social-Diagrammen
description: Komponente folgen und folgende Komponentenübersicht
seo-description: Komponente folgen und folgende Komponentenübersicht
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Grundlagen zu Social-Diagrammen {#social-graph-essentials}

The ability for a Community member to follow [activities](essentials-activities.md) as well as be followed is established through two components:

Die `follow`Komponente muss mit einer anderen Ressource verknüpft sein, und diese Zuordnung ist bereits für bestehende Communities Mitglieder und Funktionen auf einer [Community-Site](overview.md#communitiessites)eingerichtet.

The `following`component lists the members that are either following the current member or are being followed by the current member. Dieses Sozialdiagramm der Mitgliederbeziehungen untereinander ist Teil des Benutzerprofils, das für eine Community-Site bereitgestellt wird.

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
   <td>Siehe <a href="socialgraph.md">Verwenden von Social-Diagrammen</a></td>
  </tr>
  <tr>
   <td><strong> optional<br /> , Eigenschaft</strong></td>
   <td>
    <ul>
     <li>Name: <strong><code>outgoing</code></strong></li>
     <li>Type: Boolean</li>
     <li>Wert:<br />
      <ul>
       <li><i>true </i>- die <code>following</code> Komponente listet die Mitglieder auf, die das derzeit angemeldete Mitglied sind <code>follows</code></li>
       <li><i>false </i>- die <code>following</code> Komponente listet die Mitglieder auf, <code>follow </code>die das derzeit angemeldete Mitglied sind</li>
      </ul> </li>
    </ul> <p>Wenn die Eigenschaft fehlt, wird standardmäßig <i>true</i> verwendet. Derzeit ist es nicht möglich, diese Eigenschaft im Bearbeitungsdialogfeld im Autorenmodus festzulegen. Die Eigenschaft muss einer Instanz des <code>following </code>Knotens mit <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>hinzugefügt werden.</p> </td>
  </tr>
 </tbody>
</table>

### Folgen {#follow}

| **resourceType** | social/socialgraph/components/hbs/following |
|---|---|
| [**einschließbar **](scf.md#add-or-include-a-communities-component) | Nein |
| **templates** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Social Graph-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Social Graph-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Serverseitige Anpassungen](server-customize.md)

