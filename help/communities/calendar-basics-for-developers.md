---
title: Grundlagen zum Kalender
description: Erfahren Sie, wie Sie in Experience Manager Communities mit der Kalenderfunktion arbeiten. Der Kalender unterstützt die Identifizierung privilegierter Benutzergruppen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 069e379d-c6fd-49ca-b337-df6fd466e023
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 2%

---

# Grundlagen zum Kalender {#calendar-essentials}

Diese Seite enthält wichtige Informationen zum Arbeiten mit der Kalenderfunktion.

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>Sozial/Kalender/Komponenten/Hub/Kalender</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inklusive</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td>
   <td>cq.social.hbs.calendar</td>
  </tr>
  <tr>
   <td> <strong>Vorlagen</strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/calendar.hbs</td>
   <td> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/clientlibs/css/calendar.css<br /> /libs/social/calendar/components/hbs/calendar/clientlibs/css/jqueryui.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="calendar.md">Verwenden von Kalendern</a></td>
  </tr>
 </tbody>
</table>

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Kalender-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/api/package-summary.html)

* [Kalenderendpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### Kalenderfunktion {#calendar-function}

Für eine Community-Site-Struktur mit der [Kalenderfunktion](functions.md#calendar-function) ist eine `calendar` konfiguriert. Die Kalenderfunktion unterstützt die Identifizierung einer [privilegierten Benutzergruppe](users.md#privileged-members-group).

### Zugriff auf Kalenderbeiträge (UGC) {#accessing-calendar-posts-ugc}

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](working-with-srp.md) für UGC den programmgesteuerten Zugriff auf UGC, unabhängig von der gewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicherressourcenanbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden
