---
title: Community-Gruppengrundlagen
description: Erfahren Sie, wie autorisierte Benutzer die Funktion Community-Gruppen verwenden können, um eine Subcommunity auf einer Community-Site dynamisch zu erstellen.
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

# Community-Gruppengrundlagen  {#community-group-essentials}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht die dynamische Erstellung einer Subcommunity auf einer Community-Site durch autorisierte Benutzer aus der Veröffentlichungs- und Autorenumgebung.

Als Communitys [Feature Pack 1](deploy-communities.md#latestfeaturepack)kann es sein, dass Gruppen in anderen Gruppen verschachtelt sind.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

### Community-Gruppen-Mitgliederliste {#community-groups-member-list}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/group/components/hbs/communityGroupmemberList</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.communitygroups</td>
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
   <td>cq.social.hbs.communitygroups</td>
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

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Community-Gruppen-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/group/client/api/package-summary.html)

* [Community-Gruppenendpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/group/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Gruppenfunktion {#groups-function}

Eine Community-Site-Struktur mit [Gruppenfunktion](functions.md#groups-function) unterstützt die Erstellung neuer `community groups` aus der Veröffentlichungs- und Autorenumgebung. Die erstellte Community-Gruppe umfasst eine `community groups member list` -Komponente, die die Mitglieder der Gruppe auflistet.

Ein oder mehrere [Community-Gruppenvorlagen](tools-groups.md), die das Design der Community-Gruppenseiten bereitstellen, können für die Funktion Gruppen konfiguriert werden. Dies gilt, wenn die Funktion zu einem [Community-Site-Vorlage](sites.md) oder in einer Community-Gruppenvorlage verschachtelt sind.

Die Einbeziehung mehrerer Community-Gruppenvorlagen führt zu einer Auswahl. Das heißt, die Auswahl des Designs wird dem autorisierten Benutzer zum Zeitpunkt der Erstellung einer Community-Gruppe für die Community-Site angezeigt. Siehe Abschnitt zu [Community-Gruppen](creating-groups.md) für Autoren.

### Verschachtelte Gruppen {#nested-groups}

Als Communitys [FP1](deploy-communities.md#latestfeaturepack)kann eine Gruppenfunktion in eine Gruppenvorlage aufgenommen werden, sodass verschachtelte Gruppen (Untergruppen) möglich sind.

Wenn eine Community-Site oder eine Gruppenvorlage die Funktion Gruppen enthält, können Sie Folgendes tun:

* Erstellen Sie eine Subcommunity in der Autorenumgebung.

* Erstellen Sie eine Gruppe in der Veröffentlichungsumgebung, sofern diese so konfiguriert ist, dass sie dies zulässt.

Beim Erstellen einer Gruppe in der Autorenumgebung ist es erforderlich, zuerst die Community-Site zu veröffentlichen und dann die Gruppe zu veröffentlichen. Durch das Veröffentlichen der Community-Site werden die Seiten der Gruppe veröffentlicht, ohne dass die Mitgliedergruppen der Subcommunity erstellt werden, für die ACLs festgelegt sind. Daher kann eine eingeschränkte (geheime) Gruppe sichtbar sein, bis die Gruppe explizit veröffentlicht wird.

## Links und zugehörige Informationen {#links-and-related-information}

* [Verwalten von Benutzern und Benutzergruppen](users.md)
* [Communities-Gruppenkonsole](groups.md)
* [Gruppenfunktion](functions.md#groups-function)
* [Gruppenvorlagen](tools-groups.md)
