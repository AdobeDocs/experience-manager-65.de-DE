---
title: Bewertungen Essentials
description: Erfahren Sie, wie Reviews in AEM Communities eine zusammengesetzte Komponente ist, die auf einem Kommentarsystem basiert, das eine oder mehrere Bewertungskomponenten (Tally-Komponenten) enthält.
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

# Bewertungen Essentials {#reviews-essentials}

Diese Funktion besteht aus zwei Komponenten, die zusammenarbeiten: Überprüfungen und Zusammenfassung der Überprüfungen.

Reviews ist eine zusammengesetzte Komponente, die auf einem [Kommentarsystem](essentials-comments.md) basiert, das eine oder mehrere Komponenten [Rating](rating-basics.md) (Tally) enthält.

Das anonyme Posten einer Überprüfung wird nicht unterstützt. Besucher der Site müssen sich registrieren und anmelden, um eine Überprüfung hinzuzufügen. Der angemeldete Besucher (Mitglied) kann seine Überprüfung jederzeit aktualisieren.

## Grundlagen für Client-seitige {#essentials-for-client-side}

### Bewertungen {#reviews}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>Sozial/Bewertungen/Komponenten/Hub/Bewertungen</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Ja - Eigenschaften können im Design<i>Modus bearbeitet </i>.</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td>cq.social.hbs.reviews</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/reviews.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/review.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/status.hbs<br /> /libs/social/reviews/components/hbs/reviews/review/toolbar.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/reviews/components/hbs/reviews/clientlibs/review.css</td>
  </tr>
  <tr>
   <td><strong>properties</strong></td>
   <td>Siehe <a href="reviews.md">Verwenden von Überprüfungen</a></td>
  </tr>
 </tbody>
</table>

### Bewertungszusammenfassung {#review-summary}

| **resourceType** | Sozial/Bewertungen/Komponenten/Hub/Zusammenfassung |
|---|---|
| [**inklusive**](scf.md#add-or-include-a-communities-component) | Ja - Eigenschaften können im Design-Modus bearbeitet werden. |
| [**clientlibs**](client-customize.md#clientlibs-for-scf) | cq.social.hbs.reviews |
| **Vorlagen** | /libs/social/reviews/components/hbs/summary/summary.hbs |
| **css** | /libs/social/reviews/components/hbs/reviews/clientlibs/review.css |
| **Eigenschaften** | Siehe [Verwenden von Überprüfungen](reviews.md) |

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [API überprüfen](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [Endpunkte überprüfen](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Reviews (UGC) {#accessing-posted-reviews-ugc}

UGC sollte mit einer der Standardmethoden für die Mäßigung moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](working-with-srp.md) für UGC den programmgesteuerten Zugriff auf UGC, unabhängig von der gewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe:

* [Speicherressourcenanbieter - Übersicht](srp.md) - Einführung und Repository-Nutzung - Übersicht.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.
