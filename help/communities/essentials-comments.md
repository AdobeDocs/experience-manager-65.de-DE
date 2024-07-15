---
title: Kommentare Grundlagen
description: Erfahren Sie mehr über die Arbeit mit dem Kommentarsystem (Komponente Kommentare) und die Verwaltung des benutzergenerierten Inhalts (UGC) in Community-Mitgliedern-Beiträgen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8b4034f7-2f97-45ad-96d4-51cfbeae5991
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 4%

---

# Kommentare Grundlagen {#comments-essentials}

Auf dieser Seite finden Sie die Grundlagen zum Arbeiten mit dem Kommentarsystem (Kommentarkomponente) und Optionen zum Verwalten des benutzergenerierten Inhalts (UGC), der erstellt wird, wenn Mitglieder Kommentare oder Antworten posten.

Die Kommentarkomponente erstellt ein Kommentarsystem, bei dem jeder einzelne Beitrag durch eine Kommentarkomponente (Singular) dargestellt wird. Es ist das Kommentar-System, das auf der Seite enthalten ist. Das Kommentarsystem erstellt die einzelnen Kommentare beim Aufrufen.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td> social/commons/components/hbs/comments</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Ja - Eigenschaften können im Modus <i>design </i> bearbeitet werden</td>
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
* [Fragen und Antworten](qna-essentials.md)
* [Bewertungen](reviews-basics.md)

### Liste mit Kenn-zeichnungsgründen {#flag-reason-list}

Die Liste der Kennzeichnungsgründe kann angepasst werden, indem Sie Ihrer App flagreasonlist.hbs hinzufügen, um die Inhalte zu überschreiben.

* `/libs/social/commons/components/hbs/comments/comment/flagreasonlist.hbs`

Dies gilt für alle Komponenten, die ein Kommentarsystem erweitern.

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Kommentar-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/comments/api/package-summary.html)

* [Kommentar-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/comments/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Kommentare (UGC) {#accessing-posted-comments-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Übersicht über die Einführung und die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
