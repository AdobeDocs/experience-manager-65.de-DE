---
title: Community-Hauptgruppen
description: Erfahren Sie, wie autorisierte Benutzer die Funktion „Community-Gruppen“ verwenden können, um eine Untergemeinschaft innerhalb einer Community-Site dynamisch zu erstellen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: f45ae7be-a500-463a-ab3e-81f281651a9d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# Community-Hauptgruppen  {#community-group-essentials}

Die Funktion „Community-Gruppen“ bietet die Möglichkeit, dass autorisierte Benutzer aus der Veröffentlichungs- und Autorenumgebung innerhalb einer Community-Site eine Untergemeinschaft dynamisch erstellen.

Ab Communities [Feature Pack 1](deploy-communities.md#latestfeaturepack) ist es möglich, dass Gruppen in anderen Gruppen verschachtelt sind.

## Grundlagen für Client-seitige {#essentials-for-client-side}

### Community Groups Member List {#community-groups-member-list}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/group/components/hbs/communityGroupMemberList</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td>
   <td>cq.social.hbs.communitygroups</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
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
   <td> <a href="clientlibs.md"><strong>clientlibs</strong></a></td>
   <td>cq.social.hbs.communitygroups</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td> /libs/social/group/components/hbs/communitygroups/communitygroups.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/group/components/hbs/communitygroupmemberlist/clientlibs/communitygroups.css</td>
  </tr>
 </tbody>
</table>

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Community-Gruppen-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/group/client/api/package-summary.html)

* [Community-Gruppenendpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/group/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### group-Funktion {#groups-function}

Eine Community-Site-Struktur mit einer Funktion [Gruppen](functions.md#groups-function) unterstützt die Erstellung neuer `community groups` aus der Veröffentlichungs- und Autorenumgebung. Die erstellte Community-Gruppe enthält eine `community groups member list`-Komponente, in der die Mitglieder der Gruppe aufgeführt sind.

Für [&#x200B; Funktion Gruppen können eine oder mehrere &#x200B;](tools-groups.md) (Community-Gruppenvorlagen) konfiguriert werden, die das Design der Community-Gruppenseiten bereitstellen. Dies ist der Fall, wenn die Funktion zu einer [Community-Site-Vorlage](sites.md) hinzugefügt oder in einer Community-Gruppenvorlage verschachtelt wird.

Das Einschließen mehrerer Community-Gruppenvorlagen führt zu einer Auswahl. Das heißt, die Auswahl des Designs, das dem autorisierten Benutzer zum Zeitpunkt der Erstellung einer Community-Gruppe für die Community-Site präsentiert wird. Weitere Informationen finden Sie im Abschnitt [Community-](creating-groups.md)) für Autoren.

### Verschachtelte Gruppen {#nested-groups}

Ab Communities [FP1](deploy-communities.md#latestfeaturepack) ist es möglich, dass eine Gruppenfunktion in eine Gruppenvorlage aufgenommen wird, wodurch verschachtelte Gruppen (Untergemeinschaften) berücksichtigt werden.

Wenn eine Community-Site oder Gruppenvorlage die Funktion Gruppen enthält, können Sie:

* Erstellen Sie eine Untergemeinschaft in der Autorenumgebung.

* Erstellen Sie eine Gruppe in der Veröffentlichungsumgebung, wenn sie so konfiguriert ist, dass sie dies zulässt.

Beim Erstellen einer Gruppe in der Autorenumgebung ist es erforderlich, zunächst die Community-Site und anschließend die Gruppe zu veröffentlichen. Das Veröffentlichen der Community-Site veröffentlicht die Seiten der Gruppe, ohne die Mitgliedergruppen der Untergemeinschaft zu erstellen, auf die die ACLs festgelegt sind. Daher kann eine eingeschränkte (geheime) Gruppe sichtbar sein, bis die Gruppe explizit veröffentlicht wird.

## Links und zugehörige Informationen {#links-and-related-information}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Communities-Gruppenkonsole](groups.md)
* [group-Funktion](functions.md#groups-function)
* [Gruppenvorlagen](tools-groups.md)
