---
title: Blog-Grundlagen
seo-title: Blog-Grundlagen
description: Blog-Übersicht
seo-description: Blog-Übersicht
uuid: 714cf70c-76a0-4be6-9163-a31ac6bd1643
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eece7b8f-6ccd-4037-8713-0cd36cfd9e73
docset: aem65
exl-id: 51f616e8-4aba-47f6-b948-d5147d84bbb6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 4%

---

# Blog-Grundlagen {#blog-essentials}

Ab AEM 6.1 Communities ist ein Blog eine Community-Aktivität. Blogartikel werden jetzt aus der Veröffentlichungsumgebung gepostet, wo zuvor nur Blogartikel in der Autorenumgebung erstellt und veröffentlicht werden konnten.

Blog-Artikel können jetzt von jedem Community-Mitglied erstellt werden, es sei denn, sie sind auf privilegierte Mitglieder beschränkt.

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit der Blog-Funktion.

>[!NOTE]
>
>Die zugrunde liegende Infrastruktur der Blog-Funktion ist die Journalfunktion.

## Grundlagen für Client-seitige {#essentials-for-client-side}

Die Blog-Funktion besteht aus zwei Hauptkomponenten, die verfügbar sind, indem die [Blog-Funktion](/help/communities/functions.md#blog-function) hinzugefügt oder die Komponenten einer Seite im Bearbeitungsmodus für Autoren hinzugefügt werden.

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
   <td>Siehe <a href="/help/communities/blog-feature.md">Blog-Funktion</a></td>
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
| **Eigenschaften** | Siehe [Blog-Funktion](/help/communities/blog-feature.md) |

* [Clientseitige Anpassungen](/help/communities/client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Blog-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Blog-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](/help/communities/server-customize.md)

### Blogfunktion {#blog-function}

Eine Community-Site-Struktur, die die [Blog-Funktion](/help/communities/functions.md#blog-function) enthält, hat die Komponenten `Blog` und `Blog Sidebar` konfiguriert. Die Blog-Funktion unterstützt die Identifizierung einer [berechtigten Mitgliederbenutzergruppe](/help/communities/users.md#privileged-members-group).

### Zugreifen auf Blogeinträge (UGC) {#accessing-blog-entries-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](/help/communities/working-with-srp.md) für UGC den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können sich ohne Warnung** ändern.

Siehe :

* [Übersicht über den Speicheranbieter](/help/communities/srp.md)  - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](/help/communities/srp-and-ugc.md)  - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](/help/communities/accessing-ugc-with-srp.md)  - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](/help/communities/socialutils.md)  - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

## Primärer Herausgeber {#primary-publisher}

Wenn es sich bei der Bereitstellung um eine Veröffentlichungsfarm handelt, müssen Sie einen primären Herausgeber identifizieren, der nach Artikeln fragt, deren Veröffentlichung geplant ist.

Weitere Informationen finden Sie unter [Primär Publisher](/help/communities/deploy-communities.md#primary-publisher) .

## Zulassen von Rich Media {#allowing-rich-media}

Die AEM Plattform blockiert Links von anderen Websites, um XSS-Angriffe zu verhindern, wie unter

* [Schutz vor Cross-Site Scripting (XSS)](/help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Ab AEM 6.2 sind die zuvor manuell vorzunehmenden Änderungen in der standardmäßigen AntiSamy-Konfigurationsdatei enthalten.

Rich-Media wird in einen Blog-Artikel eingebettet, indem Sie das Symbol `Embed Media from External Sites` auswählen:

![media](assets/media-icon.png)
