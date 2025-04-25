---
title: Blog Essentials
description: Erfahren Sie, wie Sie die Blog-Funktion zu einer Seite hinzufügen, damit angemeldete Community-Mitglieder Blog-Artikel posten können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 51f616e8-4aba-47f6-b948-d5147d84bbb6
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 3%

---

# Blog Essentials {#blog-essentials}

Ab AEM 6.1 Communities ist ein Blog eine Community-Aktivität. Blog-Artikel werden jetzt aus der Veröffentlichungsumgebung gepostet, in der zuvor Blog-Artikel nur in der Autorenumgebung erstellt und veröffentlicht werden konnten.

Blog-Artikel können jetzt von jedem Community-Mitglied erstellt werden, es sei denn, sie sind auf privilegierte Mitglieder beschränkt.

Diese Seite enthält die wichtigsten Informationen zur Arbeit mit der Blog-Funktion.

>[!NOTE]
>
>Die zugrunde liegende Infrastruktur der Blog-Funktion ist die Journalfunktion.

## Grundlagen für Client-seitige {#essentials-for-client-side}

Die Blog-Funktion besteht aus zwei Hauptkomponenten, die verfügbar sind, indem die [Blog-Funktion](/help/communities/functions.md#blog-function) oder indem die Komponenten im Authoring-Bearbeitungsmodus zu einer Seite hinzugefügt werden.

### Blog {#blog}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/journal/components/hbs/journal</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientlibs</strong></a></td>
   <td>CQ.CKEditor<br /> CQ.Social.HBS.Voting<br /> CQ.Social.HBS.Journal</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="/help/communities/blog-feature.md">Blog-Funktion</a></td>
  </tr>
 </tbody>
</table>

### Blog-Seitenleiste {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**inklusive**](/help/communities/scf.md#add-or-include-a-communities-component) | Nein |
| [**clientlibs**](/help/communities/clientlibs.md) | cq.social.hbs.journal_sidebar |
| **Vorlagen** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **Eigenschaften** | Siehe [Blog-Funktion](/help/communities/blog-feature.md) |

* [Client-seitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Blog-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Blog-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](/help/communities/server-customize.md)

### Blogfunktion {#blog-function}

Für eine Community-Site-Struktur mit der Funktion [Blog](/help/communities/functions.md#blog-function) sind `Blog` und `Blog Sidebar` Komponenten konfiguriert. Die Blog-Funktion unterstützt die Identifizierung einer [privilegierten Benutzergruppe](/help/communities/users.md#privileged-members-group).

### Zugreifen auf Blogeinträge (UGC) {#accessing-blog-entries-ugc}

UGC sollte mit einer der Standardmethoden für die Mäßigung moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](/help/communities/working-with-srp.md) für UGC den programmgesteuerten Zugriff auf UGC, unabhängig von der gewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe :

* [Storage Resource Provider-Übersicht](/help/communities/srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](/help/communities/srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](/help/communities/accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](/help/communities/socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.

## Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der Bereitstellung um eine Veröffentlichungsfarm handelt, muss ein primärer Herausgeber identifiziert werden, der Artikel, die veröffentlicht werden sollen, abfragt.

Weitere Informationen finden Sie unter {[&#128279;](/help/communities/deploy-communities.md#primary-publisher)}Primärer Herausgeber.

## Zulassen von Rich Media {#allowing-rich-media}

Die AEM-Plattform blockiert Links von anderen Websites, um XSS-Angriffe zu verhindern, wie unter beschrieben.

* [Schützen vor Cross-Site-Scripting (XSS)](/help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Ab AEM 6.2 werden die Änderungen, die bisher manuell vorgenommen werden mussten, in die standardmäßige AntiSamy-Konfigurationsdatei aufgenommen.

Rich-Media wird durch Auswahl von `Embed Media from External Sites` in einen Blog-Artikel eingebettet:

![media](assets/media-icon.png)
