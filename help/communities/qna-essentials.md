---
title: Grundlagen der quantitativen Lockerung
seo-title: Grundlagen der quantitativen Lockerung
description: Forumsfunktion für Fragen und Antworten
seo-description: Forumsfunktion für Fragen und Antworten
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
exl-id: a7b295c1-cc9d-4881-8016-804b21fc1098
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---

# Grundlagen der quantitativen Lockerung {#qna-essentials}

Diese Seite enthält die wichtigsten Informationen für die Arbeit mit der Forumsfunktion Fragen und Antworten (QnA).

## Grundlagen für Client-seitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> resourceType</td>
   <td>social/qna/components/hbs/qnaforum</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">einschließen</a></td>
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
   <td>Siehe <a href="working-with-qna.md">Fragen und Antworten Forum-Funktion</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [QnA-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [QnA-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Fragen/Antworten-Funktion {#qna-function}

Eine Community-Site-Struktur, die die [QnA-Funktion](functions.md#qna-function) enthält, verfügt über eine konfigurierte `QnA`-Komponente sowie Einstellungen, die sich auf die Moderation und das Tagging auswirken. Die Funktion QnA unterstützt die Identifizierung einer [berechtigten Mitgliederbenutzergruppe](users.md#privileged-members-group).

### Aufrufen von QnA-Forumsposten (UGC) {#accessing-qna-forum-posts-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für UGC den programmatischen Zugriff auf UGC, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format der UGC im Repository können sich ohne Warnung** ändern.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md)  - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md)  - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md)  - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
