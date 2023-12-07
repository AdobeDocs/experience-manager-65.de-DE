---
title: Communities-Benachrichtigungen
description: AEM Communities verfügt über Benachrichtigungen, die für das angemeldete Community-Mitglied interessante Ereignisse anzeigen
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: cadb62c9-210d-4204-8abc-d0cf70960392
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 1%

---

# Communities-Benachrichtigungen {#communities-notifications}

## Übersicht {#overview}

AEM Communities bietet einen Benachrichtigungsabschnitt, in dem Ereignisse angezeigt werden, die für das angemeldete Community-Mitglied von Interesse sind.

Benachrichtigungen ähneln [activities](/help/communities/essentials-activities.md) und [subscriptions](/help/communities/subscriptions.md) wie sie sich aus folgenden Quellen ergeben können:

* Das Mitglied, das Inhalte veröffentlicht.
* Das Mitglied, das sich dafür entscheidet, einem anderen Mitglied zu folgen.
* Das Mitglied, das bestimmte Themen, Artikel und andere Threads von Inhalten verfolgt.
* Das Mitglied-Tagging (@mention) ist ein weiteres Community-Mitglied in einem benutzergenerierten Inhalt.

Unterscheidet Benachrichtigungen von Aktivitäten und Abonnements:

* Ein Link zum Benachrichtigungsabschnitt ist immer in der Kopfzeile einer Community-Site vorhanden:

   * Die Aktivitäten erfordern die [Aktivitäts-Stream-Funktion](/help/communities/functions.md#activity-stream-function) in die Struktur der Community-Site aufgenommen werden.
   * Abonnements erforderlich [E-Mail-Konfiguration](/help/communities/email.md).

* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und Pluggable Kanäle:

   * Aktivitäten sind nur im Internet verfügbar.
   * Abonnements sind nur per E-Mail verfügbar.

Als Communitys [FP1](/help/communities/deploy-communities.md#latestfeaturepack), stehen folgende Benachrichtigungskanäle zur Verfügung:

* Der Webkanal, auf den mithilfe der `Notifications` -Link.
* Der E-Mail-Kanal, der verfügbar ist, wenn die E-Mail richtig konfiguriert ist.

Zukünftige Kanäle sind Mobilgeräte und Desktop.

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit der E-Mail-Kanal funktioniert.

Anweisungen zum Einrichten von E-Mails finden Sie unter [E-Mail konfigurieren](/help/communities/analytics.md).

**Aktivieren Sie die Folgen**

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Funktionen, die Folgendes ermöglichen [Blog](/help/communities/blog-feature.md), [Forum](/help/communities/forum.md), [Fragen und Antworten](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [filelibraryLibrary](/help/communities/file-library.md), und [Kommentare](/help/communities/comments.md).

**Hinweis**:

* In der Community verwendete Komponenten [Site-Vorlagen](/help/communities/sites.md) und [Gruppenvorlagen](/help/communities/tools-groups.md) kann bereits für folgende Konfigurationen konfiguriert sein.

* Mitgliederprofile sind bereits so konfiguriert, dass andere Mitglieder folgen können.

## Benachrichtigungen aus folgenden {#notifications-from-following}

![Benachrichtigungen](assets/notifications.png)

Die **[!UICONTROL Folgen]** -Schaltfläche bietet die Möglichkeit, auf Einträge als Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn **[!UICONTROL Folgen]** ausgewählt ist, können Sie die Auswahl ein- oder ausschalten. Die `Email Subscriptions` Die Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **[!UICONTROL Folgende]**. Zur Vereinfachung können Sie `Unfollow All` , um alle Methoden auszuschalten.

Die **[!UICONTROL Folgen]** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs:

   * Folgt allen Aktivitäten für diese allgemeine Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blogartikel:

   * Folgt allen Aktivitäten für diesen spezifischen Eintrag.

## Verwalten von Benachrichtigungseinstellungen {#managing-notification-settings}

Über den Link Benachrichtigungseinstellungen auf der Seite Benachrichtigungen können die einzelnen Mitglieder verwalten, wie Benachrichtigungen empfangen werden.

Der Webkanal ist immer aktiviert.

![notifications14](assets/notifications1.png)

Der E-Mail-Kanal, der ordnungsgemäß ausgeführt werden muss [E-Mail-Konfiguration](/help/communities/email.md), stellt dieselben Einstellungen wie für den Webkanal bereit.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![notifications2](assets/notifications2.png)

Es kann von einem Mitglied aktiviert werden, hängt aber dennoch von der E-Mail-Konfiguration ab.

![notifications3](assets/notifications3.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Webbenachrichtigungen {#web-notifications}

A [Assistent erstellte Community-Site](/help/communities/sites-console.md) enthält jetzt einen Link zum `Notifications` in der Kopfzeilenleiste der Site oberhalb des Banners. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Site-Erstellungsprozesses aktiviert werden müssen.

Wählen Sie beim Besuch der veröffentlichten Site die `Notifications` zeigt alle Benachrichtigungen für das Mitglied an.

![notifications4](assets/notifications4.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail, die einen Link zum Inhalt im Web enthält.

![notifications5](assets/notifications5.png)

## E-Mail-Benachrichtigungen anpassen {#customize-email-notifications}

Organisationen können die E-Mail-Benachrichtigungen durch [Überlagerung](/help/communities/client-customize.md#overlays) die Vorlagen unter **/libs/settings/community/templates/email/html**.

Um beispielsweise die Erwähnungen für E-Mail-Benachrichtigungen (für eine Communities-Komponente) zu ändern, fügen Sie eine **if** Bedingung für Verb **mention** in den Vorlagen der Komponenten, für die Sie die **@mentions** unterstützen.

Um die E-Mail-Benachrichtigungsvorlage für @mention in Blogkommentaren zu ändern, müssen Sie die vordefinierte Vorlage unter folgender Adresse einfügen: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```
