---
title: QnA-Grundlagen
seo-title: QnA-Grundlagen
description: Forum "Fragen und Antworten"
seo-description: Forum "Fragen und Antworten"
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
translation-type: tm+mt
source-git-commit: ca15258a5dc7ca99b6c9d6ae85e42c77a3802c87
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---


# QnA Essentials {#qna-essentials}

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit dem Forum-Feature zu Fragen und Antworten (QnA).

## Grundlagen für clientseitige {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> resourceType</td>
   <td>social/qna/components/hbs/qnaforum</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">einschließbar</a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td>
   <td>cq.ckeditor<br /> cq.social.hbs.stimbe<br /> cq.social.hbs.qna</td>
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
   <td>Siehe <a href="working-with-qna.md">Funktion des Q&amp;A-Forums</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [QnA-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [QnA-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Fragen/Antworten-Funktion {#qna-function}

Eine Community-Site-Struktur, die die [QnA-Funktion](functions.md#qna-function) enthält, verfügt über eine konfigurierte `QnA`-Komponente sowie Einstellungen, die sich auf Moderation und Tagging auswirken. Die QnA-Funktion unterstützt die Identifizierung einer [privilegierten Benutzergruppe](users.md#privileged-members-group).

### Zugriff auf QnA-Forumsbeiträge (UGC) {#accessing-qna-forum-posts-ugc}

UGC sollte mithilfe einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Speichers](working-with-srp.md) für UGC Programmierungszugriff auf UGC, unabhängig von der gewählten Datenspeicherung (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

Siehe:

* [Übersicht über](srp.md)  den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md)  - SRP Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) -Codierungsrichtlinien.
* [SocialUtils Refactoring](socialutils.md)  - Zuordnen von nicht mehr unterstützten Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

