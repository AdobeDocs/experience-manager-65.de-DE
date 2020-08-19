---
title: Communities Abonnements
seo-title: Communities Abonnements
description: Community-Mitglieder interagieren mit anderen Mitgliedern per E-Mail
seo-description: Community-Mitglieder interagieren mit anderen Mitgliedern per E-Mail
uuid: a4b98769-c219-4e18-8e80-9a806ab979ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 33c85af4-4c56-487a-ba60-55211cb9f72c
translation-type: tm+mt
source-git-commit: 2fcd87cd1def7fc265ba40c83b50db86618f3b70
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# Communities Abonnements {#communities-subscriptions}

## Übersicht {#overview}

Ab Communities [FP1](deploy-communities.md#latestfeaturepack)können Community-Mitglieder mit der Community per E-Mail interagieren, indem sie eine Funktion verwenden, die als Abonnements bezeichnet wird.

Abonnement ähneln [Benachrichtigungen](notifications.md) , da Mitglieder bei der Bearbeitung von Blog-, Forum- oder QnA-Fragen abonnieren können.

Was Abonnement von Benachrichtigungen unterscheidet, ist:

* Mitglieder dürfen sich nicht an anderen Mitgliedern beteiligen.
* Die einzige Aktion, die Mitglieder ergreifen müssen, ist die Auswahl, `Email Subscriptions` wenn sie folgen.
* Wenn die E-Mail-Antwort konfiguriert ist, können Mitglieder Inhalte effektiv posten, indem sie einfach auf die empfangene E-Mail antworten.

### Voraussetzungen {#requirements}

**Email konfigurieren**

Die E-Mail-Adresse muss so konfiguriert sein, dass die Abonnement funktionsfähig sind und die Mitglieder eine E-Mail-Antwort erhalten.

Anweisungen zum Einrichten der E-Mail finden Sie unter E-Mail [konfigurieren](email.md).

**Abonnement aktivieren und Folgen**

Komponenten müssen konfiguriert werden, um Abonnement zu aktivieren *und* Folgendes zu ermöglichen. Funktionen, die Abonnement erlauben sind [Blog](blog-feature.md), [Forum](forum.md) und [QnA](working-with-qna.md).

## Abonnements aus folgenden {#subscriptions-from-following}

![abonnement-folgende](assets/subscription-following.png)

Über die Schaltfläche **Folgen** können Sie Einsendungen als Aktivitäten, Abonnements und/oder Benachrichtigungen folgen. Bei jeder Auswahl der Schaltfläche &quot; **Folgen** &quot;können Sie eine Auswahl ein- oder ausschalten.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Folgendem** geändert. Aus praktischen Gründen ist es möglich, alle Methoden `Unfollow All` zu deaktivieren.

Die Schaltfläche **Folgen** enthält die `Email Subscriptions` Option nur, wenn ein Forum, eine QnA oder ein Blog zur Aktivierung von E-Mail-Abonnements konfiguriert ist. Diese Schaltfläche wird angezeigt:

* Auf der Hauptseite der Funktion für das aktivierte Forum, QnA oder Blog sendet eine E-Mail für alle Aktivitäten unter dieser Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Servicequalität oder einen Blog-Artikel, wird eine E-Mail gesendet, wenn Aktivität für diesen bestimmten Eintrag besteht.

## Antwort per E-Mail {#reply-by-email}

Wenn E-Mail für die Beantwortung per E-Mail [](email.md#configure-polling-importer)konfiguriert ist, erhält das abonnierte Mitglied eine E-Mail mit dem veröffentlichten Inhalt und einem Link zum Online-Inhalt.

Wenn sie auf die E-Mail antworten, erscheinen die Inhalte, die sie in der Antwort eingeben, online als Inhalt.

![email-response](assets/email-reply.png)

Die Zeitdauer, die für die Veröffentlichung einer Antwort benötigt wird, wird durch das Aktualisierungsintervall [des](email.md#configure-polling-importer)Abfragenimporteurs gesteuert.

![QA](assets/qa.png)

