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
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Communities-Benachrichtigungen{#communities-notifications}

## Überblick {#overview}

AEM Communities bietet einen Benachrichtigungsabschnitt, der Ereignisse anzeigt, die für das in Community-Mitgliedern signierte Mitglied von Interesse sind.

Benachrichtigungen ähneln [Aktivitäten](/help/communities/essentials-activities.md) und [Abonnements](/help/communities/subscriptions.md) , die sich aus

* das Mitglied, das Inhalte veröffentlicht
* das Mitglied, das sich für ein anderes Mitglied entschieden hat
* das Mitglied, das sich dafür entschieden hat, bestimmten Themen, Artikeln und anderen Inhaltsthreads zu folgen
* das Mitglied-Tagging (@Erwähnung) eines anderen Community-Mitglieds in einem vom Benutzer erstellten Inhalt

Was unterscheidet Benachrichtigungen von Aktivitäten und Abonnements

* ein Link zum Abschnitt &quot;Benachrichtigungen&quot;immer in der Kopfzeile einer Community-Site vorhanden ist

   * Aktivitäten erfordern, dass die [Aktivitätsstream-Funktion](/help/communities/functions.md#activity-stream-function) in die Struktur der Community-Site einbezogen wird.
   * Abonnements müssen [per E-Mail konfiguriert werden](/help/communities/email.md)

* Die Implementierung von Benachrichtigungen erfolgt über skalierbare und Plugin-fähige Kanäle.

   * Aktivitäten stehen nur im Internet zur Verfügung
   * Abonnements sind nur per E-Mail verfügbar

Ab Communities [FP1](/help/communities/deploy-communities.md#latestfeaturepack)sind die verfügbaren Benachrichtigungskanäle

* den Webkanal, auf den über den `Notifications` Link zugegriffen wird
* der E-Mail-Kanal, der verfügbar ist, wenn E-Mail richtig konfiguriert ist

Zukünftige Kanäle sind Mobil und Desktop.

### Voraussetzungen {#requirements}

**Email konfigurieren**

Die E-Mail-Benachrichtigung muss so konfiguriert sein, dass der E-Mail-Kanal funktioniert.

Anweisungen zum Einrichten der E-Mail finden Sie unter E-Mail [konfigurieren](/help/communities/analytics.md).

**Verfolgung aktivieren**

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind zulässig: [Blog](/help/communities/blog-feature.md), [Forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [Kalender](/help/communities/calendar.md), [Dateibibliothek](/help/communities/file-library.md)[](/help/communities/comments.md)undKommentare.

Beachten Sie, dass

* Komponenten, die in Community- [Sitevorlagen](/help/communities/sites.md) und [Gruppenvorlagen](/help/communities/tools-groups.md) verwendet werden, können bereits konfiguriert werden, um Folgendes zuzulassen

* Mitgliederprofile sind bereits so konfiguriert, dass andere Mitglieder folgen können

## Benachrichtigungen von {#notifications-from-following}

![chlimage_1-243](assets/chlimage_1-243.png)

Mit der Schaltfläche **Folgen **können Sie Einträge als Aktivitäten, Abonnements und/oder Benachrichtigungen verfolgen. Jedes Mal, wenn die Schaltfläche **Folgen **ausgewählt ist, können Sie eine Auswahl ein- oder ausschalten. Die `Email Subscriptions` Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Folgendem** geändert. Aus praktischen Gründen ist es möglich, alle Methoden `Unfollow All` zu deaktivieren.

Die Schaltfläche **Folgen **wird angezeigt

* beim Anzeigen des Profils eines anderen Mitglieds
* auf einer Hauptseite mit Funktionen wie Foren, QnA und Blogs

   * folgt allen Aktivitäten für diese allgemeine Funktion

* für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Beantwortung einer Frage oder einen Blog-Artikel

   * alle Aktivitäten für diesen spezifischen Eintrag

## Verwalten von Benachrichtigungseinstellungen {#managing-notification-settings}

Wenn Sie auf der Seite &quot;Benachrichtigungen&quot;den Link &quot;Benachrichtigungseinstellungen&quot;auswählen, können Sie verwalten, wie Benachrichtigungen empfangen werden.

Der Webkanal ist immer aktiviert.

![chlimage_1-244](assets/chlimage_1-244.png)

Der E-Mail-Kanal, der auf einer ordnungsgemäßen [Konfiguration von E-Mail](/help/communities/email.md)beruht, bietet dieselben Einstellungen wie für den Webkanal.

Der E-Mail-Kanal ist standardmäßig deaktiviert.

![chlimage_1-245](assets/chlimage_1-245.png)

Es kann von einem Mitglied aktiviert werden, hängt aber dennoch von der Konfiguration der E-Mail ab.

![chlimage_1-246](assets/chlimage_1-246.png)

## Ansehen der Benachrichtigungen {#viewing-notifications}

### Webbenachrichtigungen {#web-notifications}

Ein [Assistent, der eine Community-Site](/help/communities/sites-console.md) erstellt hat, enthält jetzt einen Link zur `Notifications` Funktion in der Kopfzeilenleiste der Site oberhalb des Banners. Im Gegensatz zu Nachrichten werden Benachrichtigungen für jede Community-Site erstellt, während Nachrichten während des Site-Erstellungsprozesses aktiviert werden müssen.

Wenn Sie die veröffentlichte Site besuchen, werden bei Auswahl des `Notifications` Links alle Benachrichtigungen für das Mitglied angezeigt.

![chlimage_1-247](assets/chlimage_1-247.png)

### E-Mail-Benachrichtigungen {#email-notifications}

Wenn der E-Mail-Kanal aktiviert ist, erhält das Mitglied eine E-Mail, die einen Link zum Inhalt im Web enthält.

![chlimage_1-248](assets/chlimage_1-248.png)

## E-Mail-Benachrichtigungen anpassen {#customize-email-notifications}

Organisationen können die E-Mail-Benachrichtigungen anpassen, indem sie die Vorlagen [überlagern](/help/communities/client-customize.md#overlays) unter **/libs/settings/community/templates/email/html**.

Um beispielsweise die Benachrichtigungen zu Erwähnungen und E-Mails (für eine Communities-Komponente) zu ändern, fügen Sie eine **-if **Bedingung für die **Erwähnung** in den Vorlagen der Komponenten hinzu, für die Sie die **Unterstützung von @mentions** aktiviert haben.

Um die E-Mail-Benachrichtigungsvorlage für &quot;@mension&quot;in Blog-Kommentaren zu ändern, platzieren Sie die Vorlage &quot;Out-of-the-Box&quot; unter: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/de**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

