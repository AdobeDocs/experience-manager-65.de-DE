---
title: Abstimmungsgrundlagen
description: Erfahren Sie, wie Sie die Komponente Abstimmung verwenden, mit der Mitglieder einen bestimmten Inhalt bewerten können, indem Sie Pfeile nach oben oder unten auswählen, um ihre Meinung anzugeben.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: e8ff751f-404a-498d-8e90-62a13ab593ff
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 1%

---

# Abstimmungsgrundlagen {#voting-essentials}

Die Abstimmungskomponente, eine Unterklasse [tally](tally.md), ist ein nützliches Werkzeug, mit dem Mitglieder einen bestimmten Inhalt bewerten können, indem sie einfach Pfeile nach oben oder unten auswählen, um ihre Meinung anzugeben.

Das Platzieren mehrerer Instanzen einer Abstimmungskomponente auf derselben Seite ist zulässig. Jede Instanz muss mit einer eindeutigen `tally name` -Eigenschaft konfiguriert werden.

Die anonyme Veröffentlichung einer Abstimmung wird nicht unterstützt. Besucher der Website müssen sich registrieren und sich anmelden, um nur einmal an der Abstimmung teilnehmen zu können. Der angemeldete Besucher (Mitglied) kann seine Stimme jederzeit ändern.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/tally/components/hbs/stimmberechtigt</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Ja - Eigenschaften können im Modus <i>design </i> bearbeitet werden</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.voting</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td><p> /libs/social/tally/components/hbs/voting/voting.hbs<br /> /libs/social/tally/components/hbs/voting/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/voting/clientlibs/votingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td><p>Siehe <a href="voting.md">Verwenden der Abstimmung</a> .</p> </td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Tally-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally Endpoints](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Abstimmung (UGC) {#accessing-posted-voting-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
