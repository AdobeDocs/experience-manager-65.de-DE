---
title: Blog-Grundlagen
description: Erfahren Sie, wie Sie die Blog-Funktion zu einer Seite hinzufügen, damit angemeldete Community-Mitglieder Blog-Artikel posten können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 51f616e8-4aba-47f6-b948-d5147d84bbb6
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 2%

---

# Blog-Grundlagen {#blog-essentials}

Ab AEM 6.1 Communities ist ein Blog eine Community-Aktivität. Blogartikel werden jetzt aus der Veröffentlichungsumgebung gepostet, wo zuvor nur Blogartikel in der Autorenumgebung erstellt und veröffentlicht werden konnten.

Blog-Artikel können jetzt von jedem Community-Mitglied erstellt werden, es sei denn, sie sind auf privilegierte Mitglieder beschränkt.

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit der Blog-Funktion.

>[!NOTE]
>
>Die zugrunde liegende Infrastruktur der Blog-Funktion ist die Journalfunktion.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

Die Blog-Funktion besteht aus zwei Hauptkomponenten, die durch Hinzufügen der [Blog-Funktion](/help/communities/functions.md#blog-function) oder indem Sie die Komponenten im Bearbeitungsmodus des Autors zu einer Seite hinzufügen.

### Blog {#blog}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/journal/components/hbs/journal</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stimating<br /> cq.social.hbs.journal</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>see <a href="/help/communities/blog-feature.md">Blog-Funktion</a></td>
  </tr>
 </tbody>
</table>

### Blog-Seitenleiste {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**einschließen**](/help/communities/scf.md#add-or-include-a-communities-component) | Nein |
| [**clientllibs**](/help/communities/clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **Eigenschaften** | see [Blog-Funktion](/help/communities/blog-feature.md) |

* [Clientseitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Blog-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Blog-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](/help/communities/server-customize.md)

### Blogfunktion {#blog-function}

Eine Community-Site-Struktur mit [Blog-Funktion](/help/communities/functions.md#blog-function) has `Blog` und `Blog Sidebar` konfigurierte Komponenten. Die Blog-Funktion unterstützt die Identifizierung einer [Berechtigte Mitgliederbenutzergruppe](/help/communities/users.md#privileged-members-group).

### Zugreifen auf Blogeinträge (UGC) {#accessing-blog-entries-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Ab AEM 6.1 Communities: Verwendung einer [gemeinsamer Speicher](/help/communities/working-with-srp.md) für UGC umfasst den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können ohne Warnung geändert werden**.

Siehe :

* [Übersicht über den Speicheranbieter](/help/communities/srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [Grundlagen zu SRP und UGC](/help/communities/srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](/help/communities/accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](/help/communities/socialutils.md) - Zuordnung veralteter Methoden für Dienstprogramme zu aktuellen SRP-Dienstprogrammmethoden.

## Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der Bereitstellung um eine Veröffentlichungsfarm handelt, müssen Sie einen primären Herausgeber identifizieren, der die Abfrage für Artikel durchführt, deren Veröffentlichung geplant ist.

Siehe [Primärer Herausgeber](/help/communities/deploy-communities.md#primary-publisher) für weitere Details.

## Zulassen von Rich Media {#allowing-rich-media}

Die AEM Plattform blockiert Links von anderen Websites, um XSS-Angriffe zu verhindern, wie unter

* [Protect gegen Cross-Site Scripting (XSS)](/help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Ab AEM 6.2 sind die zuvor manuell vorzunehmenden Änderungen in der standardmäßigen AntiSamy-Konfigurationsdatei enthalten.

Rich-Media wird in einen Blog-Artikel eingebettet, indem Sie `Embed Media from External Sites` icon :

![media](assets/media-icon.png)
