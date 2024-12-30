---
title: Tally Essentials
description: Erfahren Sie, wie Tally eine abstrakte Klasse ist, die eine Standardmethode zum Sammeln von Feedback von Mitgliedern darüber bietet, wie sie bestimmte Produkte und Services schätzen.
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

Tally ist eine abstrakte Klasse, die eine Standardmethode zum Sammeln von Feedback von Membern darüber bietet, wie sie bestimmte Produkte und Services bewerten. Anonymes Feedback wird nicht unterstützt. Besuchende der Site müssen sich registrieren und anmelden, um teilzunehmen, und sich anmelden, um ihr Feedback zu ändern. Die Anforderung, sich anzumelden, erleichtert die Moderation und erhöht den Wert des Feedbacks, indem mehrere Beiträge verhindert werden.

Eine benutzerdefinierte Tally-Komponente kann durch Erweitern der abstrakten Tally-Klasse erstellt werden.

[Gefällt mir](essentials-liking.md) ist eine Umsetzung von Tally, die eine einfache Form der Äußerung einer positiven Meinung ist.

[Abstimmung](essentials-voting.md) ist eine Umsetzung der Stimmenauszählung, die eine einfache Form der Äußerung einer positiven oder negativen Meinung ist.

[Rating](rating-basics.md) ist eine Implementierung von Tally, die ein Sternsystem verwendet, um eine Reihe von Meinungen von positiv bis negativ auszudrücken.

Ab AEM 6.1 ist die Umfragekomponente nicht mehr verfügbar.

[Reviews](reviews-basics.md) ist eine SCF-Komponente, die eine Mischung aus [Kommentare](essentials-comments.md) und [Bewertung](rating-basics.md) ist.

## Grundlagen für Client-seitige {#essentials-for-client-side}

* [Client-seitige Anpassungen](client-customize.md)

## Grundlagen für Server-seitige {#essentials-for-server-side}

* [Tally-APIs](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tally-Endpunkte](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Server-seitige Anpassungen](server-customize.md)

### Zugreifen auf gepostete Abrechnungen (UGC) {#accessing-posted-tallies-ugc}

UGC sollte mit einer der Standardmethoden für die Mäßigung moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [Common Store](working-with-srp.md) für UGC den programmgesteuerten Zugriff auf UGC, unabhängig von der gewählten Speicheroption (z. B. ASRP, MSRP oder JSRP).

**Speicherort und Format des benutzergenerierten Inhalts im Repository können sich ohne Warnung ändern**.

Siehe:

* [Speicherressourcenanbieter - Übersicht](srp.md) - Einführung und Repository-Nutzung - Übersicht.
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP-Hilfsmethoden und -Beispiele.
* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - Codierungs-Richtlinien.
* [SocialUtils-Refaktorierung](socialutils.md) - Zuordnung veralteter Hilfsmethoden zu aktuellen SRP-Hilfsmethoden.
