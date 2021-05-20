---
title: Grundlagen zu Bewertungen
seo-title: Grundlagen zu Bewertungen
description: Komponenten für Bewertungen und Bewertungszusammenfassungen
seo-description: Komponenten für Bewertungen und Bewertungszusammenfassungen
uuid: 540c106e-ee3b-4261-82b2-a909d254dbf7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 62669a9d-2107-4644-a4bf-143d0ac148b3
exl-id: 91e0e245-a2f1-4bd7-b38f-7641fd94a547
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 6%

---

# Grundlagen der Bewertungen {#reviews-essentials}

Diese Funktion besteht aus zwei Komponenten, die zusammenarbeiten: Bewertungen und Rezensionszusammenfassung.

Reviews ist eine zusammengesetzte Komponente, die auf einem [Kommentar-System](essentials-comments.md) basiert, das eine oder mehrere [rating](rating-basics.md) (Tally)-Komponenten enthält.

Das anonyme Posten von Bewertungen wird nicht unterstützt. Besucher der Site müssen sich registrieren und sich anmelden, um einen Review hinzuzufügen. Der angemeldete Besucher (Mitglied) kann seine Überprüfung jederzeit aktualisieren.

## Grundlagen für Client-seitige {#essentials-for-client-side}

### Reviews {#reviews}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/views/components/hbs/views</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließen</strong></a></td>
   <td>Ja - Eigenschaften können im <i>design </i>mode bearbeitet werden</td>
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
   <td>Siehe <a href="reviews.md">Verwenden von Reviews</a></td>
  </tr>
 </tbody>
</table>

### Bewertungszusammenfassung {#review-summary}

| **resourceType** | social/views/components/hbs/summary |
|---|---|
| [**einschließen**](scf.md#add-or-include-a-communities-component) | Ja - Eigenschaften können im *design *mode bearbeitet werden |
| [**clientllibs**](client-customize.md#clientlibs-for-scf) | cq.social.hbs.reviews |
| **templates** | /libs/social/reviews/components/hbs/summary/summary.hbs |
| **css** | /libs/social/reviews/components/hbs/reviews/clientlibs/review.css |
| **Eigenschaften** | Siehe [Verwenden von Reviews](reviews.md) |

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Überprüfungs-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/api/package-summary.html)

* [Endpunkte überprüfen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/review/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Bewertungen (UGC) {#accessing-posted-reviews-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für UGC den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können sich ohne Warnung** ändern.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md)  - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md)  - Coding Guidelines.
* [SocialUtils-Refaktorierung](socialutils.md)  - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
