---
title: Kommentare Essentials
description: Erfahren Sie mehr über die Arbeit mit dem Kommentarsystem (Komponente „Kommentare„) und die Verwaltung von benutzergenerierten Inhalten (UGC) in Community-Mitgliederbeiträgen.
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

# Kommentare Essentials {#comments-essentials}

Auf dieser Seite finden Sie die Grundlagen für die Arbeit mit dem Kommentarsystem (Kommentarkomponente) und Optionen für die Verwaltung des benutzergenerierten Inhalts (UGC), der erzeugt wird, wenn Mitglieder Kommentare oder Antworten posten.

Die Kommentarkomponente richtet ein Kommentarsystem ein, sodass jeder einzelne Beitrag von einer Kommentarkomponente (Singular) repräsentiert wird. Es ist das Kommentarsystem, das auf der Seite steht. Das Kommentarsystem erstellt die einzelnen Kommentare beim Aufrufen.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td> social/commons/components/hbs/comments</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>Einschließlich</strong></a></td>
   <td>Ja - Eigenschaften können im Design<i>Modus bearbeitet </i>.</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td>CQ.CKEditor<br /> CQ.Social.HBS.Comments<br /> CQ.Social.HBS.Voting</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
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

[Client-seitige Anpassungen](client-customize.md)

### Eine Instanz pro Seite {#one-instance-per-page}

Paginierung und die Verwendung von URLs für das Caching und die Verknüpfung erfordern, dass die URL pro Kommentarsystem eindeutig ist. Daher ist pro Seite nur eine Instanz eines Kommentarsystems zulässig.

Andere Funktionen umfassen bereits das Kommentarsystem. Diese sind:

* [Blog](blog-developer-basics.md)
* [Kalender](calendar-basics-for-developers.md)
* [Dateibibliothek](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [Fragen und Antworten](qna-essentials.md)
* [Bewertungen](reviews-basics.md)

### Liste mit Kenn-zeichnungsgründen {#flag-reason-list}

Die Liste der Kennzeichnungsgründe kann angepasst werden, indem flagreasonlist.hbs zu Ihrer App hinzugefügt wird, um den Inhalt zu überschreiben

* `/libs/social/commons/components/hbs/comments/comment/flagreasonlist.hbs`

Dies gilt für jede Komponente, die ein Kommentarsystem erweitert.

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Comments-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/comments/api/package-summary.html)

* [Comments-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/commons/comments/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Kommentare (UGC) {#accessing-posted-comments-ugc}

UGC sollte mit einer der Standardmethoden für die Mäßigung moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](working-with-srp.md) für UGC den programmgesteuerten Zugriff auf UGC, unabhängig von der gewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe:

* [Speicherressourcenanbieter - Übersicht](srp.md) - Einführung und Repository-Nutzung - Übersicht.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.
