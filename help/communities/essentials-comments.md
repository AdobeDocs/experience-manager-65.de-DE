---
title: Kommentare Essentials
seo-title: Kommentare Essentials
description: Übersicht über Kommentarkomponenten
seo-description: Übersicht über Kommentarkomponenten
uuid: 58b7bb58-f598-4bcb-93ae-b7795cab51cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 18f54a1c-52aa-414d-b494-1f19b5c10345
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 5%

---


# Kommentare Essentials {#comments-essentials}

Auf dieser Seite finden Sie die Grundlagen für die Arbeit mit dem Kommentarsystem (Kommentarkomponente) und Optionen für die Verwaltung des benutzergenerierten Inhalts (UGC), der erzeugt wird, wenn Mitglieder Kommentare oder Antworten posten.

Die Kommentarkomponente stellt ein Kommentarsystem bereit, bei dem jeder einzelne Beitrag durch eine Kommentarkomponente (Singular) dargestellt wird. Es ist das Kommentarsystem, das auf der Seite enthalten ist. Das Kommentarsystem erstellt die einzelnen Kommentare, wenn sie aufgerufen werden.

## Grundlagen für clientseitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td> social/commons/components/hbs/comments</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
   <td>Ja - Eigenschaften können im <i>Designmodus bearbeitet </i>werden</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.comments<br /> cq.social.hbs.stimmte</td>
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

Paginierung und die Verwendung von URLs zum Zwischenspeichern und Verknüpfen erfordern, dass die URL für jedes Kommentarsystem eindeutig ist. Daher ist pro Seite nur eine Instanz eines Kommentarsystems zulässig.

Andere Funktionen sind bereits das Kommentarsystem. Diese sind:

* [Blog](blog-developer-basics.md)
* [Kalender](calendar-basics-for-developers.md)
* [Dateibibliothek](essentials-file-library.md)
* [Forum](essentials-forum.md)
* [Frage und Antwort](qna-essentials.md)
* [Beurteilungen](reviews-basics.md)

### Liste mit Kenn-zeichnungsgründen {#flag-reason-list}

Die Liste des Kennzeichnergrunds kann angepasst werden, indem Sie Ihrer App die Datei &quot;flagreasonlist.hbs&quot;hinzufügen, um den Inhalt zu überschreiben

* `/libs/social/commons/components/hbs/comments/comment/flagreasonlist.hbs`

Dies gilt für alle Komponenten, die ein Kommentarsystem erweitern.

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Kommentar-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/comments/api/package-summary.html)

* [Kommentare Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/commons/comments/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugriff auf gepostete Kommentare (UGC) {#accessing-posted-comments-ugc}

UGC sollte mithilfe einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Speichers](working-with-srp.md) für UGC Programmierungszugriff auf UGC, unabhängig von der gewählten Datenspeicherung (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

Siehe:

* [Übersicht über](srp.md) den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Coding-Richtlinien.
* [SocialUtils Refactoring](socialutils.md) - Zuordnen von nicht mehr unterstützten Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

