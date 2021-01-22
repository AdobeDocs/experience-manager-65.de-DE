---
title: Erleben Sie die veröffentlichte Site
seo-title: Erleben Sie die veröffentlichte Site
description: Auf einer veröffentlichten Site navigieren
seo-description: Auf einer veröffentlichten Site navigieren
uuid: 44594e9e-27ad-475d-953d-3611b04f0df8
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: dd0cbc05-a361-46bc-b9f1-d045f8f23890
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 2%

---


# Erleben Sie die veröffentlichte Site {#experience-the-published-site}

## Zu neuer Site bei Veröffentlichung suchen {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Communities-Site veröffentlicht wurde, navigieren Sie zur URL, die beim Erstellen der Site angezeigt wird, jedoch auf dem Veröffentlichungsserver, z. B.:

* Autor-URL = https://localhost:4502/content/sites/engage/en.html
* Veröffentlichungs-URL = https://localhost:4503/content/sites/engage/en.html

Um Verwirrung darüber zu vermeiden, welches Mitglied bei Autor und Veröffentlichung angemeldet ist, wird empfohlen, für jede Instanz verschiedene Browser zu verwenden.

Bei der ersten Ankunft auf der veröffentlichten Site wäre der Site-Besucher normalerweise nicht bereits angemeldet und anonym.

`https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}`

![herausgegeben](assets/authorpublished.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

In der Benutzeroberfläche sieht ein anonymer Site-Besucher Folgendes:

* Titel der Site (Tutorial &quot;Erste Schritte&quot;)
* Kein Profil-Link
* Keine Nachrichten-Verknüpfung
* Kein Benachrichtigungslink
* Suchfeld
* Link zur Anmeldung
* Das Markenbanner
* Menüverknüpfungen für die Komponenten, die in der Referenz-Site-Vorlage enthalten sind.

Wenn Sie verschiedene Links auswählen, befinden Sie sich im schreibgeschützten Modus.

### Anonymen Zugriff auf JCR {#prevent-anonymous-access-on-jcr} verhindern

Durch eine bekannte Einschränkung wird der Inhalt der Community-Site anonymen Besuchern über jcr-Inhalte und json zugänglich gemacht, obwohl **Anonymen Zugriff zulassen** für den Site-Inhalt deaktiviert ist. Dieses Verhalten kann jedoch mithilfe von Sling-Beschränkungen als Behelfslösung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff durch anonyme Benutzer durch jcr-Inhalte und json zu schützen:

1. Wechseln Sie auf der AEM Author-Instanz zu https:// Hostname:port/editor.html/content/site/sitename.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Gehen Sie zu **Seiteneigenschaften**.

   ![page-properties](assets/page-properties.png)

1. Navigieren Sie zur Registerkarte **Erweitert**.

1. Aktivieren Sie **Authentifizierungsanforderung**.

   ![site-authentication](assets/site-authentication.png)

1. hinzufügen den Pfad der Anmeldeseite. Beispiel: **/content/......./GetStarted**.
1. Veröffentlichen Sie die Seite.

## Vertrauenswürdiges Community-Mitglied {#trusted-community-member}

Dieses Erlebnis setzt voraus, dass Aaron McDonald](/help/communities/tutorials.md#demo-users) die Rollen von [Community Manager und Moderator](/help/communities/create-site.md#roles) zugewiesen wurden. [ Andernfalls kehren Sie zur Autorendatei zurück, um die Site-Einstellungen zu ändern. Wählen Sie dann Aaron McDonald als Community Manager und Moderator aus.[](/help/communities/sites-console.md#modifying-site-properties)

Wählen Sie in der oberen rechten Ecke `Log in` und melden Sie sich mit dem Benutzernamen (aaron.mcdonald@mailinator.com) und dem Kennwort (Kennwort) an. Beachten Sie die Möglichkeit, sich mit Twitter- oder Facebook-Anmeldedaten anzumelden.

![anmelden](assets/login.png)

Nachdem Sie sich als registriertes Community-Mitglied angemeldet haben, beachten Sie die folgenden Menüpunkte, um auf Ihre Community-Site zu klicken und sie zu erkunden:

* **Mit der** Profileoption können Sie Ihr Profil Ansicht und bearbeiten.
* [Die ](/help/communities/configure-messaging.md) Option &quot;Nachrichten&quot;leitet Sie zum Abschnitt &quot;Direktnachrichten&quot;weiter, in dem Sie Folgendes ausführen können:

   1. Ansicht der Direktnachrichten, die Sie erhalten haben (Posteingang), gesendet (Gesendete Artikel) und gelöscht (Papierkorb).
   1. Erstellen Sie neue Direktnachrichten, die an Personen und Gruppen gesendet werden.

* [Mit der Option &quot;](/help/communities/notifications.md) Benachrichtigungen&quot;gelangen Sie zum Abschnitt &quot;Benachrichtigungen&quot;, in dem Sie Ihre interessanten Ereignisse Ansicht und die Benachrichtigungseinstellungen bearbeiten können.
* [Wenn Sie über Moderationsberechtigungen verfügen, führt ](/help/communities/published-site.md#moderationlink) Administration Sie zur Seite &quot;AEM Communities-Moderation&quot;.

![adminscreen](assets/adminscreen.png)

Beachten Sie, dass die Kalenderseite die Startseite ist, da die gewählte Referenz-Site-Vorlage zuerst die Kalenderfunktion enthielt, gefolgt von der Aktivität-Stream-Funktion, der Forumsfunktion usw. Diese Struktur ist in der Konsole [Site-Vorlage](/help/communities/sites.md#edit-site-template) oder beim Ändern der Site-Eigenschaften in der Authoring-Umgebung sichtbar:

![sitetemplate](assets/sitetemplate.png)

>[!NOTE]
>
>Weitere Informationen zu Communities-Komponenten und -Funktionen finden Sie unter:
>
>* [Communities-Komponenten](/help/communities/author-communities.md)  (für Autoren)
>* [Komponenten-, Funktionen- und Funktionsgrundlagen](/help/communities/essentials.md)  (für Entwickler)


### Forum-Link {#forum-link}

Ansicht der Basisforumsfunktion durch Auswahl des Forumslinks.

Mitglieder können ein neues Thema posten oder einem Thema folgen.

Site-Besucher können Beiträge auf verschiedene Weise Ansicht leisten und sortieren.

![forumlink](assets/forumlink.png)

### Gruppen-Link {#groups-link}

Da Aaron ein Gruppenadministrator ist, kann Aaron durch Auswahl des Links Gruppen eine neue Community-Gruppe erstellen, indem es eine Gruppenvorlage, ein Bild, ob die Gruppe offen oder geheim ist, und einladende Mitglieder auswählt.

Dies ist ein Beispiel, bei dem eine Gruppe in der Umgebung zum Veröffentlichen erstellt wird.

Gruppen können auch in der Umgebung &quot;Autor&quot;erstellt und innerhalb der Community-Site in der Umgebung &quot;Autor&quot;verwaltet werden ([Community Groups-Konsole](/help/communities/groups.md)). Das Erlebnis [Erstellen von Gruppen unter author](/help/communities/nested-groups.md) wird als Nächstes in dieser Übung angezeigt.

![Grouplink](assets/grouplink.png)

Erstellen einer Referenzgruppe:

1. Wählen Sie **Neue Gruppe**
1. **Registerkarte „Settings“**

   * Gruppenname : `Sports`
   * Beschreibung : `A parent group for various sporting groups`.
   * Gruppen-URL-Name : `sports`
   * Wählen Sie `Open Group` (die Teilnahme eines beliebigen Community-Mitglieds durch Beitritt zulassen)

1. **Registerkarte &quot;Vorlage&quot;**

   * Wählen Sie `Reference Group` (enthält eine Gruppenfunktion in ihrer Struktur, um verschachtelte Gruppen zuzulassen)

1. Wählen Sie **Gruppe erstellen**

   ![creategroup](assets/creategroup.png)

Nachdem eine neue Gruppe erstellt wurde, wählen Sie **die neue Sportgruppe** aus, um zwei Gruppen (verschachtelt) darin zu erstellen. Da eine Site-Struktur nicht mit der Funktion &quot;Gruppen&quot;beginnen kann, muss nach dem Öffnen der Gruppe &quot;Sport&quot;der Link &quot;Gruppen&quot;ausgewählt werden:

![grouplink1](assets/grouplink1.png)

Der zweite Satz von Links, beginnend mit `Blog`, gehört zur aktuell ausgewählten Gruppe, der `Sports` Gruppe. Durch Auswahl des Links &quot;Sport&quot; `Groups` können zwei Gruppen innerhalb der Gruppe &quot;Sport&quot;verschachtelt werden.

Fügen Sie als Beispiel zwei `new groups` hinzu.

* Einen Namen mit dem Namen `Baseball`

   * Lassen Sie es als `Open Group` (erforderliche Mitgliedschaft) eingestellt.
   * Wählen Sie auf der Registerkarte &quot;Vorlagen&quot;die Option `Conversational Group`.

* Einen Namen mit dem Namen `Gymnastics`

   * Ändern Sie die Einstellung in `Member Only Group` (eingeschränkte Mitgliedschaft).
   * Wählen Sie auf der Registerkarte &quot;Vorlagen&quot;die Option `Conversational Group`.

**Hinweis**:

* Eine Aktualisierung der Seite kann erforderlich sein, bevor beide Gruppen angezeigt werden.
* Diese Vorlage enthält die Funktion groups nicht *, sodass keine weitere Verschachtelung von Gruppen möglich ist.*
* Beim Autor bietet die [Gruppenkonsole](/help/communities/groups.md) eine dritte Auswahl - eine `Public Group` (optionale Mitgliedschaft).

Nachdem beide Gruppen erstellt wurden, wählen Sie die Baseball-Gruppe, eine offene Gruppe, und beachten Sie die Links:

`Discussions` `What's New` `Members`

Die Links der Gruppe werden unterhalb der Links der Haupt-Site angezeigt und führen zur folgenden Anzeige:

![grouplink2](assets/grouplink2.png)

Unter &quot;Autor - mit Administratorrechten&quot;navigieren Sie zur Konsole [Communities Gruppen](/help/communities/members.md) und fügen Sie Weston McCall der Gruppe `Community Engage Gymnastics <uid> Members` hinzu.

Melden Sie sich bei der Veröffentlichung als Aaron McDonald an und Ansicht der Gruppen in der Gruppe &quot;Sport&quot;als anonymer Site-Besucher:

* Von Startseite
* Link `Groups` auswählen
* Link `Sports` auswählen
* Link &quot;Sport&quot; `Groups` auswählen

Nur die Baseballgruppe wird angezeigt.

Melden Sie sich als Weston McCall (weston.mccall@dodgit.com / Kennwort) an und navigieren Sie zum gleichen Speicherort. Beachten Sie, dass Weston in der Lage ist, `Join` die offene `Baseball` Gruppe und entweder `enter or Leave` die private `Gymnastics` Gruppe zu verwenden.

![grouplink3](assets/grouplink3.png)

### Webseitenlink {#web-page-link}

Ansicht der grundlegenden Webseite, die in der Site enthalten ist, durch Auswahl des Links &quot;Webseite&quot;. Die standardmäßigen AEM Authoring-Werkzeuge können verwendet werden, um dieser Umgebung Inhalte hinzuzufügen.

Gehen Sie beispielsweise zur Instanz **author**, öffnen Sie den Ordner `engage` in der Konsole [Communities Sites](/help/communities/sites-console.md) und klicken Sie auf das Symbol **Site öffnen**, um in den Bearbeitungsmodus für Autoren zu wechseln. Wählen Sie dann den Vorschau-Modus aus, um den Link `Web Page` auszuwählen, und wählen Sie dann den Bearbeitungsmodus, um Titel- und Textkomponenten hinzuzufügen. Als letztes veröffentlichen Sie entweder nur die Seite oder die gesamte Site erneut.

![webpagelink](assets/webpagelink.png)

### Moderationslink {#moderationlink}

Wenn das Community-Mitglied über Moderationsberechtigungen verfügt, wird der Link Moderation angezeigt. Wenn Sie ihn auswählen, wird der gepostete Community-Inhalt angezeigt und es ist [moderiert](/help/communities/moderate-ugc.md) auf eine ähnliche Weise wie die [Moderationskonsole](/help/communities/moderation.md) in der Authoring-Umgebung zulässig.

Verwenden Sie die Zurück-Schaltfläche des Browsers, um zur veröffentlichten Site zurückzukehren. Die meisten Konsolen sind in der Umgebung &quot;Veröffentlichen&quot;nicht über die globale Navigation zugänglich. [](/help/communities/moderate-ugc.md)

![moderationlink](assets/moderationlink.png)

## Selbstregistrierung {#self-registration}

Nach dem Abmelden ist es möglich, eine neue Benutzerregistrierung zu erstellen.

* Wählen Sie nun eine der folgenden Optionen aus `Log In`
* Wählen Sie nun eine der folgenden Optionen aus `Sign up for a new account`

![registrierung](assets/registration.png)

![anmelden](assets/signup.png)

Standardmäßig ist die E-Mail-Adresse die Anmelde-ID. Wenn diese Option deaktiviert ist, kann der Besucher seine eigene Anmelde-ID (Benutzername) eingeben. Der Benutzername muss in der Umgebung zum Veröffentlichen eindeutig sein.

Nachdem Sie den Namen, die E-Mail-Adresse und das Kennwort des Benutzers angegeben haben, können Sie den Benutzer durch Auswahl von `Sign Up` signieren.

Nach dem Anmelden ist die erste angezeigte Seite ihre `Profile`-Seite, die sie personalisieren können.

![Profil](assets/profile.png)

Wenn das Mitglied seine Anmelde-ID vergisst, ist es möglich, wiederherzustellen, wenn ihre E-Mail-Adresse verwendet wird.

![forgotusername](assets/forgotusername.png)

