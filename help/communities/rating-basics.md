---
title: Bewertungsgrundlagen
description: Erfahren Sie, wie mit der Komponente Bewertung, einer Tally-Unterklasse, angemeldete Community-Mitglieder eine Funktion auf der Website bewerten können.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 49456944-ff0d-4507-b3b8-143c90067573
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# Bewertungsgrundlagen {#rating-essentials}

Die Bewertungskomponente, eine Unterklasse [tally](tally.md), ermöglicht angemeldeten Community-Mitgliedern, eine Funktion auf der Website zu bewerten.

Das Platzieren mehrerer Instanzen einer Abstimmungskomponente auf derselben Seite ist zulässig. Jede Instanz muss mit einer eindeutigen `tally name` -Eigenschaft konfiguriert werden.

Das anonyme Posten einer Bewertung wird nicht unterstützt. Besucher der Site müssen sich nur einmal registrieren und sich anmelden, um an einer Bewertung teilnehmen zu können. Der angemeldete Besucher (Mitglied) kann seine Bewertung jederzeit ändern.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td> social/tally/components/hbs/rating</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Ja - Eigenschaften können im Modus <i>design </i> bearbeitet werden</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.rating</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td><p> /libs/social/tally/components/hbs/rating/rating.hbs<br /> /libs/social/tally/components/hbs/rating/display.hbs<br /> /libs/social/tally/components/hbs/rating/histogram.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/rating/clientlibs/ratingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td><p>Siehe <a href="rating.md">Verwenden von Bewertung</a> .</p> </td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Tally-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally Endpoints](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Bewertungen (UGC) {#accessing-posted-ratings-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
