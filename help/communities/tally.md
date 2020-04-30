---
title: Tally Essentials
seo-title: Tally Essentials
description: Übersicht über Tally-Klassen
seo-description: Übersicht über Tally-Klassen
uuid: c369c6a1-9ced-4b5c-af43-8c03236eaa52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9941ba90-3d40-4c90-bca8-5db49603cbfa
translation-type: tm+mt
source-git-commit: 77d00c1d6e94b257aa0533ca88b5f9a12dba0054

---


# Tally Essentials {#tally-essentials}

Tally ist eine abstrakte Klasse, die eine Standardmethode zur Erfassung von Feedback von Mitgliedern darüber bietet, wie sie bestimmte Produkte und Dienstleistungen schätzen. Anonymes Feedback wird nicht unterstützt. Der Site-Besucher muss sich registrieren und sich anmelden, um teilzunehmen und sich anzumelden, um sein Feedback zu ändern. Die Anforderung, sich anzumelden, erleichtert die Moderation und verbessert den Wert des Feedbacks, indem mehrere Beiträge verhindert werden.

Eine benutzerdefinierte Tally-Komponente kann durch Erweitern der abstrakten Tally-Klasse erstellt werden.

[Gefällt](essentials-liking.md) ist eine Umsetzung der Tally, die einfach eine Form der positiven Meinung ist.

[Die Abstimmung](essentials-voting.md) ist eine Umsetzung einer Aussage, die einfach eine positive oder negative Meinung ausdrückt.

[Rating](rating-basics.md) ist eine Implementierung von Tally, die ein Sternsystem verwendet, um eine Reihe von Meinungen von positiv bis negativ auszudrücken.

Ab AEM 6.1 ist die Umfragekomponente nicht mehr verfügbar.

[Reviews](reviews-basics.md) ist eine SCF-Komponente, die eine Mischung aus [Kommentaren](essentials-comments.md) und [Bewertungen](rating-basics.md)darstellt.

## Grundlagen für clientseitige {#essentials-for-client-side}

* [Clientseitige Anpassungen](client-customize.md)

## Grundlagen für serverseitige {#essentials-for-server-side}

* [Tally-APIs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Tal-Endpunkte](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Serverseitige Anpassungen](server-customize.md)

### Zugriff auf gepostete Talks (UGC) {#accessing-posted-tallies-ugc}

UGC sollte mithilfe einer der Standardmethoden für die Moderation moderiert werden.
Siehe [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Ab AEM 6.1 Communities umfasst die Verwendung eines [gemeinsamen Speichers](working-with-srp.md) für UGC Programmierungszugriff auf UGC, unabhängig von der gewählten Datenspeicherung (wie ASRP, MSRP oder JSRP).

**Speicherort und Format des UGC im Repository können ohne Warnung** geändert werden.

Siehe:

* [Übersicht über](srp.md) den Datenspeicherung Resource Provider - Einführung und Übersicht über die Repository-Nutzung
* [SRP und UGC Essentials](srp-and-ugc.md) - SRP Dienstprogrammmethoden und Beispiele.
* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md) - Coding-Richtlinien.
* [SocialUtils Refactoring](socialutils.md) - Zuordnen von nicht mehr unterstützten Dienstprogrammmethoden zu aktuellen SRP-Dienstprogrammmethoden.

