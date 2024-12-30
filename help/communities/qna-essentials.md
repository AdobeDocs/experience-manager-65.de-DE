---
title: QnA Essentials
description: Lernen Sie die Grundlagen der Arbeit mit der Funktion „Questions and Answers“ (QnA)-Forum in Adobe Experience Manager Communities kennen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: a7b295c1-cc9d-4881-8016-804b21fc1098
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 2%

---

# QnA Essentials {#qna-essentials}

Diese Seite enthält die wesentlichen Informationen für die Arbeit mit der Funktion „Fragen und Antworten (QnA)“ im Forum.

## Grundlagen für Client-seitige {#essentials-for-client-side}

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
   <td> <a href="clientlibs.md">clientlibs</a></td>
   <td>CQ.CKEditor<br /> CQ.Social.HBS.Voting<br /> CQ.Social.HBS.QNA</td>
  </tr>
  <tr>
   <td> Vorlagen</td>
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td>
  </tr>
  <tr>
   <td> CSS</td>
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td>
  </tr>
  <tr>
   <td> properties</td>
   <td>Siehe <a href="working-with-qna.md">Frage- und Antwortforum-Funktion</a></td>
  </tr>
 </tbody>
</table>

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [QnA-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [QnA-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### Fragen/Antworten-Funktion {#qna-function}

Eine Community-Site-Struktur, die die [QnA](functions.md#qna-function)Funktion enthält, verfügt über eine konfigurierte `QnA`-Komponente und Einstellungen, die sich auf die Moderation und das Tagging auswirken. Die QnA-Funktion unterstützt die Identifizierung einer [privilegierten Benutzergruppe](users.md#privileged-members-group).

### Zugreifen auf und Forumsbeiträge (UGC) {#accessing-qna-forum-posts-ugc}

UGC sollte mit einer der Standardmethoden für die Mäßigung moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](working-with-srp.md) für UGC den programmgesteuerten Zugriff auf UGC, unabhängig von der gewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe:

* [Storage Resource Provider-Übersicht](srp.md) - Einführung und Übersicht über die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.
