---
title: Grundlagen zu Bewertungen
description: Erfahren Sie, wie Reviews in AEM Communities eine zusammengesetzte Komponente ist, die auf einem Kommentarsystem basiert, das eine oder mehrere Bewertungskomponenten (Tally) enthält.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 91e0e245-a2f1-4bd7-b38f-7641fd94a547
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 2%

---

# Grundlagen zu Bewertungen {#reviews-essentials}

Diese Funktion besteht aus zwei Komponenten, die zusammenarbeiten: Rezensionen und Rezensionen.

Bewertungen sind eine zusammengesetzte Komponente, die auf einem [Kommentar-System](essentials-comments.md) basiert, das eine oder mehrere [Bewertung](rating-basics.md) -Komponenten (Tally) enthält.

Das anonyme Posten eines Reviews wird nicht unterstützt. Besucher der Site müssen sich registrieren und sich anmelden, um einen Review hinzuzufügen. Der angemeldete Besucher (Mitglied) kann seine Überprüfung jederzeit aktualisieren.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

### Bewertungen {#reviews}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/views/components/hbs/views</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Ja - Eigenschaften können im Modus <i>design </i> bearbeitet werden</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.reviews</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/reviews.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/review.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/status.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/toolbar.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/clientlibs/review.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="reviews.md">Verwenden von Bewertungen</a> .</td>
  </tr>
 </tbody>
</table>

### Bewertungszusammenfassung {#review-summary}

| **resourceType** | social/views/components/hbs/summary |
|---|---|
| [**include**](scf.md#add-or-include-a-communities-component) | Ja - Eigenschaften können im *design *mode bearbeitet werden |
| [**clientllibs**](client-customize.md#clientlibs-for-scf) | cq.social.hbs.reviews |
| **templates** | /libs/social/reviews/components/hbs/summary/summary.hbs |
| **css** | /libs/social/reviews/components/hbs/reviews/clientlibs/review.css |
| **Eigenschaften** | Siehe [Verwenden von Bewertungen](reviews.md) . |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [API überprüfen](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [Prüfungs-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Bewertungen (UGC) {#accessing-posted-reviews-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Übersicht über die Einführung und die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
