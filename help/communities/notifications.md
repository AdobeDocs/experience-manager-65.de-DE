---
title: Communities-Benachrichtigungen
description: AEM Communities verfügt über Benachrichtigungen, die Ereignisse anzeigen, die für das angemeldete Community-Mitglied von Interesse sind
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: cadb62c9-210d-4204-8abc-d0cf70960392
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 1%

---

# Communities-Benachrichtigungen {#communities-notifications}

## Überblick {#overview}

AEM Communities bietet einen Benachrichtigungsabschnitt, der Ereignisse anzeigt, die für die angemeldeten Community-Mitglieder von Interesse sind.

Benachrichtigungen ähneln [Aktivitäten](/help/communities/essentials-activities.md) und [Abonnements](/help/communities/subscriptions.md) da sie aus folgenden Gründen auftreten können:

* Das Mitglied, das den Inhalt postet.
* Das Mitglied, das einem anderen Mitglied folgt.
* Das Mitglied, das bestimmte Themen, Artikel und andere Threads von Inhalten verfolgt.
* Das Mitglied, das (@mention) ein anderes Community-Mitglied in einem benutzergenerierten Inhalt taggt.

Was Benachrichtigungen von Aktivitäten und Abonnements unterscheidet, ist:

* Ein Link zum Benachrichtigungsabschnitt ist immer in der Kopfzeile einer Community-Site vorhanden:

   * Aktivitäten erfordern, dass [Aktivitäts-Stream-Funktion](/help/communities/functions.md#activity-stream-function) in die Struktur der Community-Site aufgenommen wird.
   * Abonnements erfordern [Konfiguration der E-Mail](/help/communities/email.md).

* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und steckbare Kanäle:

   * Aktivitäten sind nur im Internet verfügbar.
   * Abonnements sind nur per E-Mail verfügbar.

Ab Communities [FP1](/help/communities/deploy-communities.md#latestfeaturepack) stehen folgende Benachrichtigungskanäle zur Verfügung:

* Der Web-Kanal, auf den über den Link `Notifications` zugegriffen wird.
* Der E-Mail-Kanal ist verfügbar, wenn die E-Mail ordnungsgemäß konfiguriert ist.

Zukünftige Kanäle sind Mobile und Desktop.

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit der E-Mail-Kanal für Benachrichtigungen funktioniert.

Anweisungen zum Einrichten von E-Mails finden Sie unter [Konfigurieren von E-](/help/communities/analytics.md)).

**Enable Follow**

Komponenten müssen so konfiguriert sein, dass Folgendes aktiviert wird. Funktionen, die Folgendes ermöglichen[ sind ](/help/communities/blog-feature.md)blog[, forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [filelilibrary](/help/communities/file-library.md) und [comments](/help/communities/comments.md).

**Hinweis**:

* Komponenten, die in Community[Site-Vorlagen](/help/communities/sites.md) und [Gruppenvorlagen](/help/communities/tools-groups.md) verwendet werden, sind möglicherweise bereits so konfiguriert, dass sie folgenden Elementen entsprechen.

* Mitgliederprofile sind bereits so konfiguriert, dass andere Mitglieder folgen können.

## Benachrichtigungen von Folgendem {#notifications-from-following}

![Benachrichtigungen](assets/notifications.png)

Die **[!UICONTROL Follow]**-Schaltfläche bietet die Möglichkeit, Einträgen in Form von Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn die **[!UICONTROL Folgen]**-Schaltfläche ausgewählt ist, kann eine Auswahl ein- oder ausgeschaltet werden. Die `Email Subscriptions` ist nur vorhanden, wenn konfiguriert.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in &quot;**[!UICONTROL &quot;]**. Der Einfachheit halber können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **[!UICONTROL Folgen]** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Haupt-Funktionsseite wie Foren, QNa und Blogs:

   * Führt alle Aktivitäten für diese allgemeine Funktion aus.

* Für einen bestimmten Eintrag, z. B. ein Forumsthema, eine Frage oder einen Blog-Artikel:

   * Führt alle Aktivitäten für diesen bestimmten Eintrag aus.

## Benachrichtigungseinstellungen verwalten {#managing-notification-settings}

Durch Auswahl des Links Benachrichtigungseinstellungen auf der Seite Benachrichtigungen können Sie für jedes Mitglied verwalten, wie Benachrichtigungen empfangen werden.

Der Web-Kanal ist immer aktiviert.

![Notifications14](assets/notifications1.png)

Der E-Mail-Kanal, der auf der ordnungsgemäßen [Konfiguration von E-](/help/communities/email.md)) basiert, bietet dieselben Einstellungen wie für den Web-Kanal.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![notifications2](assets/notifications2.png)

Er kann von einem Mitglied aktiviert werden, hängt jedoch weiterhin von der Konfiguration der E-Mail ab.

![notifications3](assets/notifications3.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Web-Benachrichtigungen {#web-notifications}

Eine [vom Assistenten erstellte Community](/help/communities/sites-console.md)Site enthält jetzt einen Link zur `Notifications` Funktion in der Kopfzeilenleiste der Site über dem Banner. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Erstellungsprozesses der Site aktiviert werden müssen.

Wenn Sie die veröffentlichte Site besuchen, werden bei Auswahl des Links `Notifications` alle Benachrichtigungen für das Mitglied angezeigt.

![notifications4](assets/notifications4.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail, die einen Link zum Inhalt im Web enthält.

![Notifications5](assets/notifications5.png)

## E-Mail-Benachrichtigungen anpassen {#customize-email-notifications}

Unternehmen können die E-Mail-Benachrichtigungen anpassen, indem [ die Vorlagen unter **/libs/settings/community/templates/email/html ](/help/communities/client-customize.md#overlays).**.

Um beispielsweise die Erwähnungen in E-Mail-Benachrichtigungen zu ändern (für eine Communities-Komponente), fügen Sie eine **Wenn**-Bedingung für **Erwähnung** in den Vorlagen der Komponenten hinzu, für die Sie die **@mentions** Unterstützung aktiviert haben.

Um die Vorlage für E-Mail-Benachrichtigungen für die @mention in Blog-Kommentaren zu ändern, fügen Sie eine vordefinierte Vorlage ein unter: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```
