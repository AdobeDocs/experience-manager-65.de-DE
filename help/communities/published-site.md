---
title: Erleben Sie die veröffentlichte Site
description: Erfahren Sie, wie Sie zur URL navigieren, die beim Erstellen einer Site, aber auf dem Veröffentlichungsserver angezeigt wird.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: ebc4e1e7-34f0-4f4e-9f00-178dfda23ce4
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 1%

---

# Erleben Sie die veröffentlichte Site {#experience-the-published-site}

## Zu neuer Site auf Publish navigieren {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Communities-Site veröffentlicht wurde, navigieren Sie zur URL, die beim Erstellen der Site, aber beispielsweise auf dem Veröffentlichungs-Server angezeigt wird:

* Autoren-URL = https://localhost:4502/content/sites/engage/en.html
* PUBLISH URL = https://localhost:4503/content/sites/engage/en.html

Um Verwirrung darüber zu vermeiden, welcher Member bei der Autoren- und Veröffentlichungsinstanz angemeldet ist, wird empfohlen, für jede Instanz unterschiedliche Browser zu verwenden.

Beim ersten Eintreffen auf der veröffentlichten Site ist der Site-Besucher in der Regel noch nicht angemeldet und anonym.

`https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}`

![authorPublished](assets/authorpublished.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

Ein anonymer Site-Besucher sieht Folgendes in der Benutzeroberfläche:

* Titel der Site (Tutorial Erste Schritte)
* Kein Profillink
* Link für keine Nachrichten
* Kein Benachrichtigungs-Link
* Suchfeld
* Anmelde-Link
* Das Markenbanner
* Menülinks für die Komponenten, die in der Referenz-Site-Vorlage enthalten sind.

Wenn Sie verschiedene Links auswählen, stellen Sie fest, dass sie sich im schreibgeschützten Modus befinden.

### Anonymen Zugriff auf JCR verhindern {#prevent-anonymous-access-on-jcr}

Eine bekannte Einschränkung macht den Inhalt der Community-Site für anonyme Besucher über JCR-Inhalt und JSON verfügbar, obwohl **anonymen Zugriff zulassen** für den Inhalt der Site deaktiviert ist. Dieses Verhalten kann jedoch mithilfe von Sling-Einschränkungen als Problemumgehung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff durch anonyme Benutzer über JCR-Inhalt und JSON zu schützen:

1. Navigieren Sie in der AEM-Autoreninstanz zu https:// hostname:port/editor.html/content/site/sitename.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Navigieren Sie zu **Seiteneigenschaften**.

   ![page-properties](assets/page-properties.png)

1. Navigieren Sie zur Registerkarte **Erweitert**.

1. Aktivieren **Authentifizierungspflicht**.

   ![site-authentication](assets/site-authentication.png)

1. Den Pfad der Anmeldeseite hinzufügen. Beispiel: **/content/……./Erste Schritte**.
1. Veröffentlichen Sie die Seite.

## Mitglied der vertrauenswürdigen Community {#trusted-community-member}

Bei dieser Erfahrung wird davon [, dass &#x200B;](/help/communities/tutorials.md#demo-users)Aaron McDonald) die Rolle des [Community-Managers und -Moderators](/help/communities/create-site.md#roles) zugewiesen wurde. Kehren Sie andernfalls zur Autorenumgebung zurück, um [Site-Einstellungen ändern](/help/communities/sites-console.md#modifying-site-properties) und wählen Sie Aaron McDonald als Community-Manager und Moderator aus.

Klicken Sie in der rechten oberen Ecke auf `Log in` und melden Sie sich mit Ihrem Benutzernamen (aaron.mcdonald@mailinator.com) und Kennwort (Kennwort) an. Beachten Sie die Möglichkeit, sich mit Twitter- oder Facebook-Anmeldeinformationen anzumelden.

![anmelden](assets/login.png)

Sobald Sie als registriertes Community-Mitglied angemeldet sind, beachten Sie die folgenden Menüelemente, um auf Ihre Community-Site zu klicken und sie zu erkunden:

* **Profil** Option ermöglicht die Anzeige und Bearbeitung Ihres Profils.
* [Nachrichten](/help/communities/configure-messaging.md) leitet Sie zum Abschnitt „Direktnachrichten“, in dem Sie Folgendes tun können:

   1. Zeigen Sie die Direktnachrichten an, die Sie erhalten haben (Posteingang), gesendet haben (gesendete Elemente) und gelöscht haben (Papierkorb).
   1. Erstellen Sie neue Direktnachrichten, damit Sie sie an Einzelpersonen und Gruppen senden können.

* [Benachrichtigungen](/help/communities/notifications.md) leitet Sie zum Abschnitt „Benachrichtigungen“, wo Sie wichtige Ereignisse anzeigen und Benachrichtigungseinstellungen bearbeiten können.
* [Administration](/help/communities/published-site.md#moderationlink) leitet Sie zur Seite &quot;AEM Communities-Moderation“ weiter, wenn Sie über Moderationsberechtigungen verfügen.

![adminscreen](assets/adminscreen.png)

Beachten Sie, dass die Kalenderseite die Startseite ist, da die ausgewählte Referenz-Site-Vorlage zuerst die Kalenderfunktion enthält, gefolgt von Aktivitäts-Stream-Funktion, Forenfunktion usw. Diese Struktur ist in der Konsole [Site-Vorlage](/help/communities/sites.md#edit-site-template) oder beim Ändern der Site-Eigenschaften in der Autorenumgebung sichtbar:

![SiteTemplate](assets/sitetemplate.png)

>[!NOTE]
>
>Weitere Informationen zu Komponenten und Funktionen von Communities finden Sie unter:
>
>* [Communities-Komponenten](/help/communities/author-communities.md) (für Autoren)
>* [Komponenten-, Funktions- und Feature Essentials](/help/communities/essentials.md) (für Entwickler)

### Link zum Forum {#forum-link}

Zeigen Sie die grundlegende Forenfunktion an, indem Sie auf den Link Forum klicken.

Mitglieder können ein neues Thema posten oder einem Thema folgen.

Besuchende der Website können Beiträge anzeigen und auf verschiedene Weise sortieren.

![forumlink](assets/forumlink.png)

### Gruppen-Link {#groups-link}

Da Aaron ein Gruppenadministrator ist, kann Aaron durch Auswahl des Links Gruppen eine Community-Gruppe erstellen, indem er eine Gruppenvorlage und ein Bild auswählt, unabhängig davon, ob die Gruppe offen oder geheim ist, und Mitglieder einlädt.

Dies ist ein Beispiel für eine Gruppe, die in der Veröffentlichungsumgebung erstellt wird.

Gruppen können auch in der Autorenumgebung erstellt und auf der Community-Site in der Autorenumgebung verwaltet werden ([Community-](/help/communities/groups.md)). Die Erfahrung mit [Erstellen von Gruppen auf der Autoreninstanz](/help/communities/nested-groups.md) wird als Nächstes in diesem Tutorial erläutert.

![groupLink](assets/grouplink.png)

Erstellen Sie eine Referenzgruppe:

1. Wählen Sie **Neue Gruppe**
1. **Registerkarte „Einstellungen**

   * Gruppenname : `Sports`
   * Beschreibung : `A parent group for various sporting groups`.
   * Gruppen-URL-Name : `sports`
   * `Open Group` auswählen (durch Beitritt jedes Community-Mitglieds zulassen)

1. **Registerkarte „Vorlage“**

   * `Reference Group` auswählen (enthält eine Gruppenfunktion in ihrer Struktur, um verschachtelte Gruppen zuzulassen)

1. Wählen Sie **Gruppe erstellen**

   ![createGroup](assets/creategroup.png)

Nachdem eine neue Gruppe erstellt wurde, wählen **die neue Sportgruppe aus** um zwei Gruppen (verschachtelt) darin zu erstellen. Da eine Site-Struktur nicht mit der Gruppenfunktion beginnen kann, muss nach dem Öffnen der Sportgruppe der Link Gruppen ausgewählt werden:

![groupLink1](assets/grouplink1.png)

Der zweite Satz von Links, beginnend mit `Blog`, gehört zur aktuell ausgewählten Gruppe, der `Sports`. Durch Auswahl des Links `Groups` des Sports ist es möglich, zwei Gruppen innerhalb der Sports Group zu verschachteln.

Fügen Sie beispielsweise zwei `new groups` hinzu.

* Eine namens `Baseball`

   * Legen Sie ihn als `Open Group` fest (erforderliche Mitgliedschaft).
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group` aus.

* Eine namens `Gymnastics`

   * Ändern Sie die Einstellung in `Member Only Group` (eingeschränkte Mitgliedschaft).
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group` aus.

**Hinweis**:

* Eine Aktualisierung der Seite kann erforderlich sein, bevor beide Gruppen angezeigt werden.
* Diese Vorlage enthält *nicht* die Gruppenfunktion, sodass keine weitere Verschachtelung von Gruppen möglich ist.
* In der Autoreninstanz bietet die [Gruppenkonsole](/help/communities/groups.md) eine dritte Möglichkeit - eine `Public Group` (optionale Mitgliedschaft).

Nachdem beide Gruppen erstellt wurden, wählen Sie die Baseballgruppe aus, eine offene Gruppe, und beachten Sie deren Links:

`Discussions` `What's New` `Members`

Die Links der Gruppe werden unter den Links der Haupt-Site angezeigt und führen zu folgender Anzeige:

![groupLink2](assets/grouplink2.png)

Navigieren Sie in der Autoreninstanz mit Administratorrechten zur [Communities-](/help/communities/members.md)-Konsole und fügen Sie Weston McCall zur `Community Engage Gymnastics <uid> Members` hinzu.

Melden Sie sich als Aaron McDonald ab und sehen Sie sich die Gruppen in der Sports Group als anonymen Site-Besucher an:

* Von Startseite
* `Groups` Link auswählen
* `Sports` Link auswählen
* Wählen Sie den `Groups`-Link des Sports aus

Nur die Baseballgruppe ist sichtbar.

Melden Sie sich als Weston McCall (weston.mccall@dodgit.com / Kennwort) an und navigieren Sie zum selben Speicherort. Beachten Sie, dass Weston in der Lage ist, die offene `Baseball`-Gruppe und entweder `enter or Leave` die private `Gymnastics`-Gruppe zu `Join`.

![groupLink3](assets/grouplink3.png)

### Webseitenlink {#web-page-link}

Zeigen Sie die grundlegende Webseite der Website an, indem Sie auf den Link Web-Seite klicken. Mit den standardmäßigen AEM-Authoring-Tools können Sie dieser Seite in der Authoring-Umgebung Inhalte hinzufügen.

Gehen Sie beispielsweise zur **author**-Instanz, öffnen Sie den `engage` Ordner in der [Communities-Sites-](/help/communities/sites-console.md), wählen Sie das Symbol **Site öffnen** aus, um in den Autorenbearbeitungsmodus zu wechseln. Wählen Sie dann Vorschaumodus, sodass Sie den `Web Page` Link auswählen können, und anschließend Bearbeitungsmodus, um Titel- und Textkomponenten hinzuzufügen. Veröffentlichen Sie abschließend entweder nur die Seite oder die gesamte Site erneut.

![webpagelink](assets/webpagelink.png)

### Moderationslink {#moderationlink}

Wenn das Community-Mitglied über Moderationsberechtigungen verfügt, ist der Link Moderation sichtbar. Wenn Sie auf den Link klicken, werden die geposteten Community-Inhalte angezeigt und können [&#128279;](/help/communities/moderation.md) ähnlich wie bei der [Moderationskonsole](/help/communities/moderate-ugc.md) in der Autorenumgebung „moderiert werden.

Verwenden Sie die Schaltfläche Zurück des Browsers, um zur veröffentlichten Site zurückzukehren. Die meisten Konsolen sind in der Veröffentlichungsumgebung nicht über die globale Navigation zugänglich.

![ModerationLink](assets/moderationlink.png)

## Selbstregistrierung {#self-registration}

Nach dem Abmelden ist es möglich, eine Benutzerregistrierung zu erstellen.

* Klicken Sie auf `Log In`
* Klicken Sie auf `Sign up for a new account`

![Registrierung](assets/registration.png)

![Anmeldung](assets/signup.png)

Standardmäßig ist die E-Mail-Adresse die Anmelde-ID. Wenn diese Option deaktiviert ist, kann der Besucher seine eigene Anmelde-ID (Benutzername) eingeben. Der Benutzername muss in der Veröffentlichungsumgebung eindeutig sein.

Nachdem Sie den Namen, die E-Mail-Adresse und das Kennwort des Benutzers angegeben haben, wird der Benutzer durch Auswahl von `Sign Up` erstellt und zum Signieren aktiviert.

Nach der Anmeldung wird als erste Seite die `Profile` Seite angezeigt, die personalisiert werden kann.

![profile](assets/profile.png)

Wenn das Mitglied seine Anmelde-ID vergisst, ist es möglich, sie mithilfe seiner E-Mail-Adresse wiederherzustellen.

![forgotUserName](assets/forgotusername.png)
