---
title: Community-Gruppengrundlagen
seo-title: Community-Gruppengrundlagen
description: Dynamisches Erstellen von Community-Sites
seo-description: Dynamisches Erstellen von Community-Sites
uuid: 168e7aeb-6e9a-468d-8ac4-274007cea252
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4f85cd3c-5158-4f23-abe2-7e375fd0c8d4
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Community-Gruppengrundlagen {#community-group-essentials}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern aus der Veröffentlichungs- und Autorenumgebung erstellt zu werden.

Ab Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack)können Gruppen innerhalb anderer Gruppen verschachtelt werden

## Grundlagen für clientseitige {#essentials-for-client-side}

### Community Groups-Mitgliederliste {#community-groups-member-list}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/group/components/hbs/communityGroupmitgliedlist</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.communityGroups</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/communitygroupmemberlist.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/memberList.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="creating-groups.md">Community-Gruppe</a></td>
  </tr>
 </tbody>
</table>

### Community-Gruppen {#community-groups}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/group/components/hbs/communityGroups</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.communityGroups</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/group/components/hbs/communitygroups/communitygroups.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/communitygroups.css</td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Community-Gruppen-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/group/client/api/package-summary.html)

* [Community-Gruppen-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/group/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Gruppenfunktion {#groups-function}

Eine Community-Site-Struktur, die eine [Gruppenfunktion](functions.md#groups-function) enthält, unterstützt die Erstellung neuer Elemente `community groups` aus der Veröffentlichungs- und Autorenumgebung. Die erstellte Community-Gruppe enthält eine `community groups member list` Komponente, die die Mitglieder der Gruppe auflistet.

Eine oder mehrere [Community-Gruppenvorlagen](tools-groups.md), die das Design der Community-Gruppenseite(n) bereitstellen, können für die Funktion &quot;Gruppen&quot;konfiguriert werden, wenn die Funktion einer [Community-Site-Vorlage](sites.md) hinzugefügt oder in einer Community-Gruppenvorlage verschachtelt wird.

Die Einbeziehung mehrerer Community-Gruppenvorlagen führt dazu, dass dem autorisierten Benutzer zum Zeitpunkt der Erstellung einer neuen Community-Gruppe für die Community-Site eine Auswahl an Designs angezeigt wird, wie im Abschnitt über [Community-Gruppen](creating-groups.md) für Autoren dargestellt.

### Verschachtelte Gruppen {#nested-groups}

Ab Communities [FP1](deploy-communities.md#latestfeaturepack)ist es möglich, eine Funktion &quot;Gruppen&quot;in eine Gruppenvorlage einzubinden und somit verschachtelte Gruppen (Untergruppen) zu ermöglichen.

Wenn eine Community-Site oder Gruppenvorlage die Funktion Gruppen enthält, können Sie

* Erstellen einer Untergemeinschaft in der Autorenumgebung
* Erstellen Sie eine Gruppe in der Veröffentlichungsumgebung, sofern diese für ihre Verwendung konfiguriert ist

Wenn Sie eine Gruppe in der Autorenumgebung erstellen, müssen Sie zuerst die Community-Site veröffentlichen und dann die Gruppe veröffentlichen. Durch das Veröffentlichen der Community-Site werden die Seiten der Gruppe veröffentlicht, ohne dass die Untergruppen der Community erstellt werden, in denen die ACLs festgelegt sind. Daher kann eine eingeschränkte (geheime) Gruppe sichtbar sein, bis die Gruppe explizit veröffentlicht wird.

## Links und zugehörige Informationen {#links-and-related-information}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Communities-Gruppenkonsole](groups.md)
* [Gruppenfunktion](functions.md#groups-function)
* [Gruppenvorlagen](tools-groups.md)

