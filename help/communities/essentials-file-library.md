---
title: Grundlagen zur Dateibibliothek
description: Erfahren Sie mehr über die Grundlagen der Arbeit mit der Dateibibliothek-Funktion in Adobe Experience Manager Communities.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 6d653331-c1ce-4ccb-bb45-656b6413ac3e
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 2%

---

# Grundlagen zur Dateibibliothek {#file-library-essentials}

Diese Seite enthält die grundlegenden Informationen für die Arbeit mit der Dateibibliotheksfunktion.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/filelibrary/components/hbs/filelibrary</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stimating<br /> cq.social.hbs.filelilibrary</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/filelibrary/components/hbs/filelibrary/filelibrary.hbs<br /> /libs/social/filelibrary/components/hbs/folder/folder.hbs<br /> /libs/social/filelibrary/components/hbs/folder/item.hbs<br /> /libs/social/filelibrary/components/hbs/document/document.hbs<br /> /libs/social/filelibrary/components/hbs/document/item.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/filelibrary/components/hbs/filelibrary/clientlibs/filelibrary.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="file-library.md">Funktion "Dateibibliothek"</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Dateibibliothek-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/filelibrary/client/api/package-summary.html)

* [Dateibibliothek-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/filelibrary/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Dateibibliotheksfunktion {#file-library-function}

Eine Community-Site-Struktur, die die [Funktion &quot;Dateibibliothek&quot;](functions.md#file-library-function) enthält, enthält eine konfigurierte `file library` -Komponente.

### Zugreifen auf für Dateibibliotheken gepostete Kommentare {#accessing-comments-posted-for-file-libraries-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
