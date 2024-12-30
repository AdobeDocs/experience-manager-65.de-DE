---
title: Grundlagen zur Interaktion
description: Erfahren Sie, wie Sie die Komponente „Gefällt mir“ verwenden, ein nützliches Tool, mit dem Mitglieder eine positive Meinung zu bestimmten Inhalten äußern können, indem sie auf das Herz-Symbol klicken.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
pagetitle: Liking Essentials
exl-id: ef314385-cd5c-411c-91df-83691a81c1bc
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 1%

---

# Grundlagen zur Interaktion {#liking-essentials}

Die Komponente „Gefällt mir[, eine ](tally.md) Unterklasse, ist ein nützliches Tool, mit dem Mitglieder eine positive Meinung über ein bestimmtes Inhaltselement ausdrücken können, indem sie einfach das Herzsymbol auswählen.

Die Platzierung mehrerer Instanzen einer verknüpfenden Komponente auf derselben Seite ist zulässig. Jede Instanz muss mit einer eindeutigen `tally name`-Eigenschaft konfiguriert werden.

Das anonyme Posten eines Like wird nicht unterstützt. Besuchende der Site müssen sich registrieren und anmelden, um an der Verknüpfung teilzunehmen. Der angemeldete Besucher (Mitglied) kann jederzeit wie ein- und ausschalten.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/tally/components/hbs/liking</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Ja - Eigenschaften können im Design<i>Modus bearbeitet </i>.</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td> cq.social.hbs.liking</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td><p> /libs/social/tally/components/hbs/liking/liking.hbs<br /> /libs/social/tally/components/hbs/liking/activity-icon.hbs<br /> /libs/social/tally/components/hbs/liking/activity-title.hbs</p> </td>
  </tr>
  <tr>
   <td><strong>CSS</strong></td>
   <td> /libs/social/tally/components/hbs/liking/clientlibs/likingcomponent.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td><p>Siehe <a href="liking.md">Verwendung von „Gefällt mir</a></p> </td>
  </tr>
 </tbody>
</table>

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Tally-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### Zugriff auf veröffentlichte Abstimmungen (UGC) {#accessing-posted-voting-ugc}

UGC sollte mit einer der Standardmethoden für die Mäßigung moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](working-with-srp.md) für UGC den programmgesteuerten Zugriff auf UGC, unabhängig von der gewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe:

* [Storage Resource Provider-Übersicht](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.
