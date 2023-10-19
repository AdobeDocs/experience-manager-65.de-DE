---
title: Grundlagen der quantitativen Lockerung
description: Lernen Sie die Grundlagen der Arbeit mit der Funktion Fragen und Antworten (QnA) Forum in Adobe Experience Manager Communities kennen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: a7b295c1-cc9d-4881-8016-804b21fc1098
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 2%

---

# Grundlagen der quantitativen Lockerung {#qna-essentials}

Diese Seite enthält die wichtigsten Informationen für die Arbeit mit der Forumsfunktion Fragen und Antworten (QnA).

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> resourceType</td>
   <td>social/qna/components/hbs/qnaforum</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">include</a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stimating<br /> cq.social.hbs.qna</td>
  </tr>
  <tr>
   <td> templates</td>
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td>
  </tr>
  <tr>
   <td> css</td>
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td>
  </tr>
  <tr>
   <td> properties</td>
   <td>Siehe <a href="working-with-qna.md">Frage- und Forumsfunktion</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [QnA-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [QnA-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Fragen/Antworten-Funktion {#qna-function}

Eine Community-Site-Struktur mit [QnA-Funktion](functions.md#qna-function) verfügt über eine konfigurierte `QnA` -Komponente sowie Einstellungen, die sich auf die Moderation und das Tagging auswirken. Die Funktion &quot;Fragen und Antworten&quot;unterstützt die Identifizierung einer [Berechtigte Mitgliederbenutzergruppe](users.md#privileged-members-group).

### Zugreifen auf QnA-Forumbeiträge (UGC) {#accessing-qna-forum-posts-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities: Verwendung einer [gemeinsamer Speicher](working-with-srp.md) für UGC umfasst den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können ohne Warnung geändert werden**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [Grundlagen zu SRP und UGC](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Methoden für Dienstprogramme zu aktuellen SRP-Dienstprogrammmethoden.
