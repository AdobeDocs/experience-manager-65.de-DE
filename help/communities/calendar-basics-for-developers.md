---
title: Kalendergrundlagen
description: Erfahren Sie, wie Sie mit der Kalenderfunktion in Experience Manager Communities arbeiten. Der Kalender unterstützt die Identifizierung von privilegierten Benutzergruppen.
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

# Kalendergrundlagen {#calendar-essentials}

Diese Seite enthält wichtige Informationen zum Arbeiten mit der Kalenderfunktion.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/calendar/components/hbs/calendar</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
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

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Kalender-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/api/package-summary.html)

* [Kalenderendpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/calendar/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Kalenderfunktion {#calendar-function}

Eine Community-Site-Struktur mit der [Kalenderfunktion](functions.md#calendar-function) hat eine `calendar` -Komponente konfiguriert. Die Kalenderfunktion unterstützt das Identifizieren einer [berechtigten Mitgliederbenutzergruppe](users.md#privileged-members-group).

### Zugriff auf Kalenderbeiträge (UGC) {#accessing-calendar-posts-ugc}

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Übersicht über die Einführung und die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden
