---
title: Grundlagen zur Abstimmung
description: Erfahren Sie, wie Sie die Abstimmungskomponente verwenden, mit der Mitglieder ein bestimmtes Inhaltselement bewerten können, indem sie Pfeile nach oben oder unten auswählen, um ihre Meinung anzugeben.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: e8ff751f-404a-498d-8e90-62a13ab593ff
solution: Experience Manager
feature: Communities
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%
---
# Grundlagen zur Abstimmung {#voting-essentials}

Die Abstimmkomponente, eine [tally](tally.md)-Unterklasse, ist ein nützliches Tool, das es Mitgliedern ermöglicht, ein bestimmtes Inhaltselement zu bewerten, indem sie einfach Pfeile nach oben oder unten auswählen, um ihre Meinung anzugeben.

Die Platzierung mehrerer Instanzen einer Abstimmkomponente auf derselben Seite ist zulässig. Jede Instanz muss mit einer eindeutigen `tally name`-Eigenschaft konfiguriert werden.

Die anonyme Abgabe einer Stimme wird nicht unterstützt. Besuchende der Website müssen sich nur einmal registrieren und anmelden, um an der Abstimmung teilzunehmen. Der angemeldete Besucher (Mitglied) kann seine Stimme jederzeit ändern.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/tally/components/hbs/vote</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Ja - Eigenschaften können im Design<i>Modus bearbeitet </i>.</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> CQ.social.hbs.vote</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td><p> /libs/social/tally/components/hbs/voting/voting.hbs<br /> /libs/social/tally/components/hbs/voting/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/voting/clientlibs/votingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td><p>Siehe <a href="voting.md">Verwenden von Abstimmungen</a></p> </td>
  </tr>
 </tbody>
</table>

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Tally-APIs](https://experienceleague.adobe.com/en/tools/aem-api-documentation/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally-Endpunkte](https://experienceleague.adobe.com/en/tools/aem-api-documentation/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### Zugriff auf veröffentlichte Abstimmungen (UGC) {#accessing-posted-voting-ugc}

UGC sollte mit einer der Standardmethoden für die Mäßigung moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](working-with-srp.md) für benutzergenerierten Inhalt programmgesteuerten Zugriff auf benutzergenerierten Inhalt, unabhängig von der ausgewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe:

* [Storage Resource Provider-Übersicht](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.
