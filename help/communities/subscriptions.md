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

Ab Communities [FP1](deploy-communities.md#latestfeaturepack) können Community-Mitglieder über E-Mails mit der Community interagieren und eine Funktion verwenden, die als Abonnements bezeichnet wird.

Abonnements ähneln [Benachrichtigungen](notifications.md) da sich Mitglieder abonnieren können, wenn sie Blog-Artikeln, Forumsthemen oder Fragen zur QnA folgen.

Abonnements unterscheiden sich von Benachrichtigungen wie folgt:

* Mitglieder dürfen sich nicht anmelden, wenn sie anderen Mitgliedern folgen.
* Die einzige Aktion, die Mitglieder ausführen müssen, besteht darin, `Email Subscriptions` auszuwählen, wenn sie Folgendes tun.
* Wenn die E-Mail-Antwort konfiguriert ist, können Mitglieder effektiv Inhalte posten, indem sie einfach auf die empfangene E-Mail antworten.

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

Die E-Mail muss konfiguriert werden, damit Abonnements funktionieren und Mitglieder per E-Mail antworten können.

Anweisungen zum Einrichten von E-Mails finden Sie unter [Konfigurieren von E-](email.md)).

**Abonnements aktivieren und folgen**

Komponenten müssen so konfiguriert sein, dass Abonnements *und* aktiviert werden. Zu den Funktionen, die Abonnements ermöglichen[&#x200B; gehören &#x200B;](blog-feature.md), [forum](forum.md) und [QnA](working-with-qna.md).

## Abonnements von {#subscriptions-from-following}

![subscription-following](assets/subscription-following.png)

Die **Follow**-Schaltfläche bietet die Möglichkeit, Einträgen in Form von Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn die **Folgen**-Schaltfläche ausgewählt ist, kann eine Auswahl ein- oder ausgeschaltet werden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in &quot;**&quot;**. Der Einfachheit halber können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die **Folgen**-Schaltfläche enthält die `Email Subscriptions`-Option nur, wenn ein Forum, eine QnA oder ein Blog so konfiguriert ist, dass E-Mail-Abonnements aktiviert werden. Diese Schaltfläche wird angezeigt:

* Auf der Hauptseite der Funktion für das aktivierte Forum, die QNa oder den Blog wird eine E-Mail für alle Aktivitäten unter dieser Funktion gesendet.

* Für einen bestimmten Eintrag, z. B. ein Forumsthema, eine Frage oder einen Blog-Artikel, wird eine E-Mail gesendet, wenn eine Aktivität für diesen bestimmten Eintrag vorhanden ist.

## Per E-Mail antworten {#reply-by-email}

Wenn die E[Mail für die Antwort per E-Mail konfiguriert ist](email.md#configure-polling-importer) erhält das Abonnentenmitglied eine E-Mail mit dem geposteten Inhalt und einem Link zum Online-Inhalt.

Wenn sie auf die E-Mail antworten, wird der Inhalt, den sie in der Antwort eingeben, als Inhalt online angezeigt.

![email-reply](assets/email-reply.png)

Die Zeit, die zum Senden einer Antwort benötigt wird, wird durch das Aktualisierungsintervall des [Abruf-Importtools](email.md#configure-polling-importer) gesteuert.

![QA](assets/qa.png)
