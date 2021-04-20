---
title: Communities-Abonnements
seo-title: Communities-Abonnements
description: Community-Mitglieder interagieren mit anderen Mitgliedern per E-Mail
seo-description: Community-Mitglieder interagieren mit anderen Mitgliedern per E-Mail
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 2%

---


# Communities-Abonnements {#communities-subscriptions}

## Überblick {#overview}

Ab Communities [FP1](deploy-communities.md#latestfeaturepack) können Community-Mitglieder mit der Community per E-Mail interagieren, indem sie eine Funktion verwenden, die als Abonnements bezeichnet wird.

Abonnement sind ähnlich wie [Benachrichtigungen](notifications.md), da Mitglieder abonnieren können, wenn sie Blog-Artikel, Forenthemen oder Fragen zur Servicequalität befolgen.

Was Abonnement von Benachrichtigungen unterscheidet, ist:

* Mitglieder dürfen sich nicht an anderen Mitgliedern beteiligen.
* Die einzige Aktion, die Mitglieder ergreifen müssen, ist `Email Subscriptions` auszuwählen, wenn sie darauf folgen.
* Wenn die E-Mail-Antwort konfiguriert ist, können Mitglieder Inhalte effektiv posten, indem sie einfach auf die empfangene E-Mail antworten.

### Voraussetzungen {#requirements}

**Email konfigurieren**

Die E-Mail-Adresse muss so konfiguriert sein, dass die Abonnement funktionsfähig sind und die Mitglieder eine E-Mail-Antwort erhalten.

Anweisungen zum Einrichten der E-Mail finden Sie unter [Konfigurieren der E-Mail](email.md).

**Abonnement aktivieren und Folgen**

Komponenten müssen so konfiguriert sein, dass die folgenden Abonnement aktiviert werden: *und*. Zu den Funktionen, die Abonnement zulassen, gehören [blog](blog-feature.md), [forum](forum.md) und [QnA](working-with-qna.md).

## Abonnement von{#subscriptions-from-following}

![Abonnement-folgende](assets/subscription-following.png)

Mit der Schaltfläche **Folgen** können Sie Einsendungen als Aktivitäten, Abonnements und/oder Benachrichtigungen verfolgen. Jedes Mal, wenn die Schaltfläche **Folgen** ausgewählt ist, können Sie eine Auswahl ein- oder ausschalten.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Nach** geändert. Aus praktischen Gründen können Sie `Unfollow All` auswählen, um alle Methoden auszuschalten.

Die Schaltfläche **Folgen** enthält die Option `Email Subscriptions` nur, wenn ein Forum, eine QnA oder ein Blog zur Aktivierung von E-Mail-Abonnements konfiguriert ist. Diese Schaltfläche wird angezeigt:

* Auf der Hauptseite der Funktion für das aktivierte Forum, QnA oder Blog sendet eine E-Mail für alle Aktivitäten unter dieser Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Servicequalität oder einen Blog-Artikel, wird eine E-Mail gesendet, wenn Aktivität für diesen bestimmten Eintrag besteht.

## Antwort per E-Mail {#reply-by-email}

Wenn E-Mail für die Antwort per E-Mail konfiguriert ist [erhält das abonnierte Mitglied eine E-Mail mit dem veröffentlichten Inhalt und einem Link zum Online-Inhalt.](email.md#configure-polling-importer)

Wenn sie auf die E-Mail antworten, erscheinen die Inhalte, die sie in der Antwort eingeben, online als Inhalt.

![email-response](assets/email-reply.png)

Die Zeitdauer, die benötigt wird, um eine Antwort zu veröffentlichen, wird durch das Update-Intervall des [Abfragenimporteurs](email.md#configure-polling-importer) gesteuert.

![QA](assets/qa.png)

