---
title: Essentials des Kalenders
seo-title: Essentials des Kalenders
description: Übersicht über die Kalenderfunktion
seo-description: Übersicht über die Kalenderfunktion
uuid: 14ff7a83-b2a7-4f7e-8ee7-88f336329a1a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 88932a3c-ba7f-47ba-9e0b-206755c2d42e
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Essentials des Kalenders {#calendar-essentials}

Diese Seite enthält wichtige Informationen zum Arbeiten mit der Kalenderfunktion.

## Grundlagen für clientseitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/calendar/components/hbs/calendar</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>einschließbar</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.calendar</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/calendar.hbs</td>
   <td> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td>/libs/social/calendar/components/hbs/calendar/clientlibs/css/calendar.css<br /> /libs/social/calendar/components/hbs/calendar/clientlibs/css/jqueryui.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>siehe <a href="calendar.md">Verwenden von Kalendern</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Kalender-APIs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/calendar/client/api/package-summary.html)

* [Kalenderendpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/calendar/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Kalenderfunktion {#calendar-function}

Eine Community-Site-Struktur, die die [Kalenderfunktion](functions.md#calendar-function) enthält, verfügt über eine konfigurierte c- `alendar`Komponente. Die Kalenderfunktion unterstützt die Identifizierung einer [privilegierten Benutzergruppe](users.md#privileged-members-group).

### Zugriff auf Kalenderbeiträge {#accessing-calendar-posts-ugc}

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Speichers](working-with-srp.md) für UGC Programmierungszugriff auf UGC, unabhängig von der gewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

Siehe:

* [Übersicht über](srp.md) den Speicherressourcen-Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Richtlinien zum Kodieren
* [SocialUtils Refactoring](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden

