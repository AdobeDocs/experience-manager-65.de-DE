---
title: Tally Essentials
description: Erfahren Sie, wie Tally eine abstrakte Klasse ist, die eine Standardmethode zur Erfassung von Feedback von Mitgliedern darüber bietet, wie sie bestimmte Produkte und Services bewerten.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 0b508df9-1a24-4728-a254-f913eeb9b391
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Tally Essentials {#tally-essentials}

Tally ist eine abstrakte Klasse, die eine Standardmethode zur Erfassung von Feedback von Mitgliedern darüber bietet, wie sie bestimmte Produkte und Services bewerten. Anonymes Feedback wird nicht unterstützt. Besucher der Site müssen sich registrieren und sich anmelden, um teilnehmen und sich anmelden zu können, um ihr Feedback zu ändern. Die Anmeldung erleichtert die Moderation und erhöht den Wert des Feedbacks, indem mehrere Beiträge verhindert werden.

Eine benutzerdefinierte Tally-Komponente kann durch Erweitern der abstrakten Tally-Klasse erstellt werden.

[Gefällt mir](essentials-liking.md) ist eine Tallyimplementierung, die einfach eine positive Meinung ausdrückt.

[Voting](essentials-voting.md) ist eine Tally-Implementierung, die einfach darin besteht, eine positive oder negative Meinung zu äußern.

[Bewertung](rating-basics.md) ist eine Implementierung einer Tabelle, die ein Sternsystem verwendet, um eine Reihe von Meinungen von positiv bis negativ auszudrücken.

Ab AEM 6.1 ist die Umfragekomponente nicht mehr verfügbar.

[Bewertungen](reviews-basics.md) ist eine SCF-Komponente, die aus [Kommentaren](essentials-comments.md) und [Bewertung](rating-basics.md) besteht.

## Grundlagen für Client-seitige Unterstützung {#essentials-for-client-side}

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige Unterstützung {#essentials-for-server-side}

* [Tally-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally Endpoints](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Tabellen (UGC) {#accessing-posted-tallies-ugc}

UGC sollte mit einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Stores](working-with-srp.md) für benutzergenerierte Inhalte den programmatischen Zugriff auf benutzergenerierte Inhalte, unabhängig von der ausgewählten Speicheroption (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können sich ohne Warnung ändern**.

Siehe:

* [Übersicht über den Speicheranbieter](srp.md) - Übersicht über die Einführung und die Repository-Nutzung.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Dienstprogrammmethoden und Beispiele.
* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Codierungsrichtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnen veralteter Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.
