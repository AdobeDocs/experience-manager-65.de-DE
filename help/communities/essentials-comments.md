---
title: Grundlagen zu Kommentaren
seo-title: Grundlagen zu Kommentaren
description: Komponentenübersicht Kommentare
seo-description: Komponentenübersicht Kommentare
uuid: 58b7bb58-f598-4bcb-93ae-b7795cab51cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 18f54a1c-52aa-414d-b494-1f19b5c10345
exl-id: 8b4034f7-2f97-45ad-96d4-51cfbeae5991
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 5%

---

# Kommentare Grundlagen {#comments-essentials}

Auf dieser Seite finden Sie die Grundlagen zum Arbeiten mit dem Kommentarsystem (Kommentarkomponente) und Optionen zum Verwalten des benutzergenerierten Inhalts (UGC), der erstellt wird, wenn Mitglieder Kommentare oder Antworten posten.

Die Kommentarkomponente erstellt ein Kommentarsystem, bei dem jeder einzelne Beitrag durch eine Kommentarkomponente (Singular) dargestellt wird. Es ist das Kommentarsystem, das auf der Seite enthalten ist. Das Kommentarsystem erstellt die einzelnen Kommentare beim Aufrufen.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td> social/commons/components/hbs/comments</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td>
   <td>Ja - Eigenschaften können im <i>design </i>mode bearbeitet werden</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.comments<br /> cq.social.hbs.stimating</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/commons/components/hbs/comments/comments.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>CSS</strong></td>
   <td> /libs/social/commons/components/hbs/comments/clientlibs/commentsystem.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td> Siehe <a href="comments.md">Verwenden von Kommentaren</a></td>
  </tr>
 </tbody>
</table>

[Clientseitige Anpassungen](client-customize.md)

### Eine Instanz pro Seite {#one-instance-per-page}

Paginierung und die Verwendung von URLs zum Zwischenspeichern und Verknüpfen erfordern, dass die URL pro Kommentar-System eindeutig ist. Daher ist pro Seite nur eine Instanz eines Kommentarsystems zulässig.

Andere Funktionen beinhalten bereits das Kommentarsystem. Diese sind:

* [Blog](blog-developer-basics.md)
* [Kalender](calendar-basics-for-developers.md)
* [Dateibibliothek](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [Frage und Antwort](qna-essentials.md)
* [Reviews](reviews-basics.md)

### Liste mit Kenn-zeichnungsgründen {#flag-reason-list}

Die Liste der Kennzeichnungsgründe kann angepasst werden, indem Sie Ihrer App flagreasonlist.hbs hinzufügen, um die Inhalte zu überschreiben.

* `/libs/social/commons/components/hbs/comments/comment/flagreasonlist.hbs`

Dies gilt für alle Komponenten, die ein Kommentarsystem erweitern.

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Kommentar-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/comments/api/package-summary.html)

* [Kommentare Endpoints](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/comments/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Kommentare (UGC) {#accessing-posted-comments-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für UGC den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können sich ohne Warnung** ändern.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md)  - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md)  - Coding Guidelines.
* [SocialUtils-Refaktorierung](socialutils.md)  - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
