---
title: Blog-Grundlagen
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

# Blog-Grundlagen {#blog-essentials}

Ab AEM 6.1 Communities ist ein Blog eine Community-Aktivität. Blogartikel werden jetzt aus der Veröffentlichungsumgebung gepostet, wo zuvor nur Blogartikel in der Autorenumgebung erstellt und veröffentlicht werden konnten.

Blog-Artikel können jetzt von jedem Community-Mitglied erstellt werden, es sei denn, sie sind auf privilegierte Mitglieder beschränkt.

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit der Blog-Funktion.

>[!NOTE]
>
>Die zugrunde liegende Infrastruktur der Blog-Funktion ist die Journalfunktion.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

Die Blogfunktion besteht aus zwei Hauptkomponenten, die durch Hinzufügen der [Blog-Funktion](/help/communities/functions.md#blog-function) oder Hinzufügen der Komponenten zu einer Seite im Bearbeitungsmodus für Autoren verfügbar sind.

### Blog {#blog}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/journal/components/hbs/journal</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
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
   <td>siehe <a href="/help/communities/blog-feature.md">Blog-Funktion</a></td>
  </tr>
 </tbody>
</table>

### Blog-Seitenleiste {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**include**](/help/communities/scf.md#add-or-include-a-communities-component) | Nein |
| [**clientllibs**](/help/communities/clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **Eigenschaften** | siehe [Blog-Funktion](/help/communities/blog-feature.md) |

* [Clientseitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Blog-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Blog-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](/help/communities/server-customize.md)

### Blogfunktion {#blog-function}

Eine Community-Site-Struktur, die die [Blog-Funktion](/help/communities/functions.md#blog-function) enthält, hat die Komponenten `Blog` und `Blog Sidebar` konfiguriert. Die Blog-Funktion unterstützt das Identifizieren einer [berechtigten Mitgliederbenutzergruppe](/help/communities/users.md#privileged-members-group).

### Zugreifen auf Blogeinträge (UGC) {#accessing-blog-entries-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](/help/communities/working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe :

* [Übersicht über den Speicheranbieter](/help/communities/srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](/help/communities/srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](/help/communities/accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](/help/communities/socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

## Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der Bereitstellung um eine Veröffentlichungsfarm handelt, müssen Sie einen primären Herausgeber identifizieren, der die Abfrage für Artikel durchführt, deren Veröffentlichung geplant ist.

Weitere Informationen finden Sie unter [Primärer Herausgeber](/help/communities/deploy-communities.md#primary-publisher) .

## Zulassen von Rich Media {#allowing-rich-media}

Die AEM Plattform blockiert Links von anderen Websites, um XSS-Angriffe zu verhindern, wie unter

* [Schützen vor Cross-Site-Scripting (XSS)](/help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Ab AEM 6.2 sind die zuvor manuell vorzunehmenden Änderungen in der standardmäßigen AntiSamy-Konfigurationsdatei enthalten.

Rich-Media wird durch die Auswahl des Symbols `Embed Media from External Sites` in einen Blogartikel eingebettet:

![media](assets/media-icon.png)
