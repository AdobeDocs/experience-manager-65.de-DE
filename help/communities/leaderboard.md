---
title: Leaderboard-Grundlagen
description: Erfahren Sie, wie Sie die Bewertungen und Abzeichen für Communities konfigurieren, damit Sie mit der Leaderboard-Komponente in Adobe Experience Manager Communities arbeiten können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: fd1b1749-13f9-4079-ae39-348676105852
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 5%

---

# Leaderboard-Grundlagen {#leaderboard-essentials}

Diese Seite enthält die wichtigsten Informationen für die Arbeit mit der Leaderboard-Funktion.

Bevor Sie die Leaderboard-Komponente auf einer Seite einfügen, müssen Sie die [Bewertungen und Abzeichen der Gemeinschaften](implementing-scoring.md) konfigurieren.

Siehe [Grundlagen zu Scoring und Abzeichen](configure-scoring.md).

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/gamification/components/hbs/leaderboard</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>include</strong></a></td>
   <td>Nein</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.gamification.hbs.leaderboard</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/gamification/components/hbs/leaderboard/leaderboard.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/gamification/components/hbs/leaderboard/clientlibs/leaderboard.css</td>
  </tr>
  <tr>
   <td><strong> properties</strong></td>
   <td>Siehe <a href="enabling-leaderboard.md">Leaderboard-Funktion</a></td>
  </tr>
 </tbody>
</table>

* [Clientseitige Anpassungen](client-customize.md)

### Dateibibliotheksfunktion {#file-library-function}

Eine Community-Site-Struktur, die die [Leaderboard-Funktion](functions.md#leaderboard-function) enthält, enthält eine konfigurierte `leaderboard` -Komponente.
