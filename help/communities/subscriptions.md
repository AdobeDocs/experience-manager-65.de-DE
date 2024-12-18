---
title: Communities-Abonnements
description: Community-Mitglieder interagieren per E-Mail mit anderen Mitgliedern
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 338be220-659a-459c-8e90-55e3a11ddeb0
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---

# Communities-Abonnements {#communities-subscriptions}

## Überblick {#overview}

Ab Communities [FP1](deploy-communities.md#latestfeaturepack) können Community-Mitglieder per E-Mail mit der Community interagieren, indem sie eine Funktion verwenden, die als Abonnements bezeichnet wird.

Abonnements ähneln [Benachrichtigungen](notifications.md) , da Mitglieder sich abonnieren können, wenn sie Blog-Artikel, Forenthemen oder Fragen zur Frage stellen.

Unterscheidet Anmeldungen von Benachrichtigungen:

* Die Mitglieder dürfen sich nicht an anderen Mitgliedern beteiligen.
* Die einzige Aktion, die Mitglieder ergreifen müssen, ist, beim Befolgen `Email Subscriptions` auszuwählen.
* Wenn die E-Mail-Antwort konfiguriert ist, können Mitglieder Inhalte effektiv posten, indem sie einfach auf die erhaltene E-Mail antworten.

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit Abonnements funktionieren und Mitglieder per E-Mail antworten können.

Anweisungen zum Einrichten von E-Mails finden Sie unter [E-Mail konfigurieren](email.md).

**Abonnements aktivieren und befolgen**

Komponenten müssen so konfiguriert sein, dass die folgenden Abonnements aktiviert werden: *und*. Funktionen, die Abonnements zulassen, sind [blog](blog-feature.md), [forum](forum.md) und [QnA](working-with-qna.md).

## Abonnements aus folgenden {#subscriptions-from-following}

![subscription-following](assets/subscription-following.png)

Die Schaltfläche **Folgen** bietet die Möglichkeit, Einträgen als Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn die Schaltfläche **Befolgen** ausgewählt wird, kann eine Auswahl ein- oder ausgeschaltet werden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Folgt**. Aus praktischen Gründen können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **Folgen** enthält nur dann die Option `Email Subscriptions`, wenn ein Forum, eine Fragen-und-Antworten-Frage oder ein Blog zur Aktivierung von E-Mail-Abonnements konfiguriert ist. Diese Schaltfläche wird angezeigt:

* Auf der Hauptseite mit den Funktionen für das aktivierte Forum, Fragen und Antworten oder Blog Wird eine E-Mail für alle Aktivitäten unter dieser Funktion senden.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blog-Artikel Wird eine E-Mail senden, wenn Aktivitäten für diesen bestimmten Eintrag vorhanden sind.

## Antwort per E-Mail {#reply-by-email}

Wenn die E-Mail [für die Antwort per E-Mail konfiguriert ist](email.md#configure-polling-importer), erhält das Abonnent eine E-Mail mit dem veröffentlichten Inhalt und einen Link zum Online-Inhalt.

Wenn sie auf die E-Mail antworten, erscheint der von ihnen in der Antwort eingegebene Inhalt als Online-Inhalt.

![email-response](assets/email-reply.png)

Die Zeit, die für die Veröffentlichung einer Antwort benötigt wird, wird durch das Aktualisierungsintervall des [Abruf-Importtools](email.md#configure-polling-importer) gesteuert.

![QA](assets/qa.png)
