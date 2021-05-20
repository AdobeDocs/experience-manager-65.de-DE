---
title: Communities-Benachrichtigungen
seo-title: Communities-Benachrichtigungen
description: AEM Communities verfügt über Benachrichtigungen, die Ereignisse anzeigen, die für das angemeldete Community-Mitglied von Interesse sind
seo-description: AEM Communities verfügt über Benachrichtigungen, die Ereignisse anzeigen, die für das angemeldete Community-Mitglied von Interesse sind
uuid: 2f5ea4b5-7308-414e-a3f8-2e8aa76b1ef4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ab9088b7-a691-4153-ac82-1e8c0a19ed5d
docset: aem65
role: Administrator
exl-id: cadb62c9-210d-4204-8abc-d0cf70960392
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 2%

---

# Communities-Benachrichtigungen {#communities-notifications}

## Überblick {#overview}

AEM Communities bietet einen Benachrichtigungsabschnitt, in dem Ereignisse angezeigt werden, die für das angemeldete Community-Mitglied von Interesse sind.

Benachrichtigungen ähneln [Aktivitäten](/help/communities/essentials-activities.md) und [Abonnements](/help/communities/subscriptions.md), da sie sich aus Folgendem ergeben können:

* Das Mitglied, das Inhalte veröffentlicht.
* Das Mitglied, das sich dafür entscheidet, einem anderen Mitglied zu folgen.
* Das Mitglied, das bestimmte Themen, Artikel und andere Threads von Inhalten verfolgt.
* Das Mitglied-Tagging (@mention) ist ein weiteres Community-Mitglied in einem benutzergenerierten Inhalt.

Unterscheidet Benachrichtigungen von Aktivitäten und Abonnements:

* Ein Link zum Benachrichtigungsabschnitt ist immer in der Kopfzeile einer Community-Site vorhanden:

   * Für Aktivitäten muss die [Aktivitäts-Stream-Funktion](/help/communities/functions.md#activity-stream-function) in die Struktur der Community-Site aufgenommen werden.
   * Abonnements erfordern [Konfiguration von email](/help/communities/email.md).

* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und Pluggable Kanäle:

   * Aktivitäten sind nur im Internet verfügbar.
   * Abonnements sind nur per E-Mail verfügbar.

Ab Communities [FP1](/help/communities/deploy-communities.md#latestfeaturepack) stehen folgende Benachrichtigungskanäle zur Verfügung:

* Der Webkanal, auf den über den Link `Notifications` zugegriffen wird.
* Der E-Mail-Kanal, der verfügbar ist, wenn die E-Mail richtig konfiguriert ist.

Zukünftige Kanäle sind Mobilgeräte und Desktop.

### Voraussetzungen {#requirements}

**E-Mail konfigurieren**

E-Mail muss konfiguriert werden, damit der E-Mail-Kanal funktioniert.

Anweisungen zum Einrichten von E-Mails finden Sie unter [Konfigurieren von E-Mail](/help/communities/analytics.md).

**Aktivieren Sie die Folgen**

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind möglich: [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [filelibrary](/help/communities/file-library.md) und [comments](/help/communities/comments.md).

**Hinweis**:

* Komponenten, die in der Community [Site-Vorlagen](/help/communities/sites.md) und [Gruppenvorlagen](/help/communities/tools-groups.md) verwendet werden, können bereits für das Befolgen konfiguriert sein.

* Mitgliederprofile sind bereits so konfiguriert, dass andere Mitglieder folgen können.

## Benachrichtigungen aus folgenden {#notifications-from-following}

![Benachrichtigungen](assets/notifications.png)

Die Schaltfläche **[!UICONTROL Folgen]** bietet die Möglichkeit, Einträgen als Aktivitäten, Abonnements und/oder Benachrichtigungen zu folgen. Jedes Mal, wenn die Schaltfläche **[!UICONTROL Folgen]** ausgewählt wird, können Sie eine Auswahl ein- oder ausschalten. Die Auswahl `Email Subscriptions` ist nur bei Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **[!UICONTROL Nach]**. Zur Vereinfachung können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **[!UICONTROL Folgen]** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs:

   * Folgt allen Aktivitäten für diese allgemeine Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blogartikel:

   * Folgt allen Aktivitäten für diesen spezifischen Eintrag.

## Verwalten von Benachrichtigungseinstellungen {#managing-notification-settings}

Über den Link Benachrichtigungseinstellungen auf der Seite Benachrichtigungen können die einzelnen Mitglieder verwalten, wie Benachrichtigungen empfangen werden.

Der Webkanal ist immer aktiviert.

![notifications14](assets/notifications1.png)

Der E-Mail-Kanal, der auf einer ordnungsgemäßen [Konfiguration von E-Mail](/help/communities/email.md) basiert, bietet dieselben Einstellungen wie für den Webkanal.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![notifications2](assets/notifications2.png)

Es kann von einem Mitglied aktiviert werden, hängt aber dennoch von der E-Mail-Konfiguration ab.

![notifications3](assets/notifications3.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Webbenachrichtigungen {#web-notifications}

Ein [Assistent, der die Community-Site](/help/communities/sites-console.md) erstellt hat, enthält jetzt einen Link zur Funktion `Notifications` in der Kopfzeilenleiste der Site oberhalb des Banners. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Site-Erstellungsprozesses aktiviert werden müssen.

Beim Besuch der veröffentlichten Site werden durch Auswahl des Links `Notifications` alle Benachrichtigungen für das Mitglied angezeigt.

![notifications4](assets/notifications4.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail mit einem Link zum Inhalt im Web.

![notifications5](assets/notifications5.png)

## Anpassen von E-Mail-Benachrichtigungen {#customize-email-notifications}

Unternehmen können die E-Mail-Benachrichtigungen durch [Überlagerungen](/help/communities/client-customize.md#overlays) der Vorlagen unter **/libs/settings/community/templates/email/html** anpassen.

Um beispielsweise die Benachrichtigungsinhalte zu Erwähnungen (für eine Communities-Komponente) zu ändern, fügen Sie in den Vorlagen der Komponenten, für die Sie die Unterstützung für **@Erwähnungen** aktiviert haben, eine **if**-Bedingung für Verb **mention** hinzu.

Um die E-Mail-Benachrichtigungsvorlage für @mention in Blogkommentaren zu ändern, müssen Sie die vordefinierte Vorlage unter folgender Adresse einfügen: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```
