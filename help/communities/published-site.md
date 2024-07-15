---
title: Erlebnis der veröffentlichten Site
description: Erfahren Sie, wie Sie zu der URL navigieren, die beim Erstellen einer Site, aber auf dem Veröffentlichungsserver angezeigt wird.
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

# Erlebnis der veröffentlichten Site {#experience-the-published-site}

## Navigieren zu neuer Site in Publish {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Communities-Site veröffentlicht wurde, navigieren Sie zur URL, die beim Erstellen der Site angezeigt wird, aber auf dem Veröffentlichungsserver, z. B.:

* Autoren-URL = https://localhost:4502/content/sites/engage/en.html
* PUBLISH URL = https://localhost:4503/content/sites/engage/en.html

Um Verwirrungen zu vermeiden, welches Mitglied bei der Autoren- und Veröffentlichungsinstanz angemeldet ist, wird empfohlen, für jede Instanz unterschiedliche Browser zu verwenden.

Wenn der Besucher zum ersten Mal auf die veröffentlichte Site gelangt, wird er normalerweise nicht bereits angemeldet und anonym.

`https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}`

![authorPublish](assets/authorpublished.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

Einem anonymen Site-Besucher wird in der Benutzeroberfläche Folgendes angezeigt:

* Titel der Site (Tutorial &quot;Erste Schritte&quot;)
* Kein Profillink
* Keine Nachrichtenverbindung
* Kein Benachrichtigungslink
* Suchfeld
* Anmelde-Link
* Das Markenbanner
* Menülinks für die Komponenten, die in der Referenz-Site-Vorlage enthalten sind.

Wenn Sie verschiedene Links auswählen, befinden sie sich im schreibgeschützten Modus.

### Verhindern des anonymen Zugriffs auf JCR {#prevent-anonymous-access-on-jcr}

Durch eine bekannte Einschränkung wird der Community-Site-Inhalt anonymen Besuchern über JCR-Inhalt und JSON bereitgestellt, obwohl **anonymen Zugriff zulassen** für den Site-Inhalt deaktiviert ist. Dieses Verhalten kann jedoch mithilfe von Sling-Einschränkungen als Problemumgehung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff anonymer Benutzer durch jcr-Inhalte und JSON zu schützen:

1. Wechseln Sie auf AEM Autoreninstanz zu https:// Hostname: port/editor.html/content/site/sitename.html.

   >[!NOTE]
   >
   >Besuchen Sie nicht die lokalisierte Site.

1. Wechseln Sie zu **Seiteneigenschaften**.

   ![page-properties](assets/page-properties.png)

1. Navigieren Sie zur Registerkarte **Erweitert**.

1. Aktivieren Sie **Authentifizierungspflicht**.

   ![Site-Authentifizierung](assets/site-authentication.png)

1. Fügen Sie den Pfad der Anmeldeseite hinzu. Beispiel: **/content/......../GetStarted**.
1. Veröffentlichen Sie die Seite.

## Vertrauenswürdiger Community-Mitglied {#trusted-community-member}

Dieses Erlebnis setzt voraus, dass [Aaron McDonald](/help/communities/tutorials.md#demo-users) die Rollen von [Community-Manager und -Moderator](/help/communities/create-site.md#roles) zugewiesen wurde. Wenn nicht, kehren Sie zur Autorenumgebung zurück, um die Site-Einstellungen zu ändern](/help/communities/sites-console.md#modifying-site-properties) und wählen Sie Aaron McDonald als Community-Manager und Moderator aus.[

Wählen Sie oben rechts `Log in` aus und signieren Sie mit dem Benutzernamen (aaron.mcdonald@mailinator.com) und dem Kennwort (Kennwort). Beachten Sie die Möglichkeit, sich mit Twitter- oder Facebook-Anmeldeinformationen anzumelden.

![anmelden](assets/login.png)

Nachdem Sie sich als registriertes Community-Mitglied angemeldet haben, beachten Sie die folgenden Menüpunkte, um auf Ihre Community-Site zu klicken und sie zu erkunden:

* Mit der Option **Profil** können Sie Ihr Profil anzeigen und bearbeiten.
* Die Option [Nachrichten](/help/communities/configure-messaging.md) leitet Sie zum Abschnitt für Direktnachrichten weiter, in dem Sie Folgendes tun können:

   1. Zeigen Sie die Direktnachrichten an, die Sie empfangen haben (Posteingang), gesendet (Gesendete Elemente) und gelöscht (Papierkorb).
   1. Erstellen Sie neue Direktnachrichten, damit Sie sie an Einzelpersonen und Gruppen senden können.

* Die Option [Benachrichtigungen](/help/communities/notifications.md) leitet Sie zum Benachrichtigungsabschnitt weiter, in dem Sie Ihre interessanten Ereignisse anzeigen und Benachrichtigungseinstellungen bearbeiten können.
* [Administration](/help/communities/published-site.md#moderationlink) leitet Sie zur Seite &quot;AEM Communities-Moderation&quot;, wenn Sie über Moderationsberechtigungen verfügen.

![adminscreen](assets/adminscreen.png)

Beachten Sie, dass die Kalenderseite die Startseite ist, da die ausgewählte Referenz-Site-Vorlage zuerst die Kalenderfunktion, gefolgt von der Aktivitäts-Stream-Funktion, der Forumsfunktion usw. enthält. Diese Struktur ist in der Konsole [Site-Vorlage](/help/communities/sites.md#edit-site-template) oder beim Ändern der Site-Eigenschaften in der Autorenumgebung sichtbar:

![sitetemplate](assets/sitetemplate.png)

>[!NOTE]
>
>Weitere Informationen zu Communities-Komponenten und -Funktionen finden Sie unter:
>
>* [Communities-Komponenten](/help/communities/author-communities.md) (für Autoren)
>* [Komponenten-, Funktionen- und Funktionsgrundlagen](/help/communities/essentials.md) (für Entwickler)

### Forum-Link {#forum-link}

Klicken Sie auf den Link Forum , um die grundlegende Forumsfunktion anzuzeigen.

Mitglieder können ein neues Thema posten oder einem Thema folgen.

Besucher der Site können Beiträge auf verschiedene Weise anzeigen und sortieren.

![forumlink](assets/forumlink.png)

### Gruppenlink {#groups-link}

Da Aaron ein Gruppenadministrator ist, kann Aaron durch Auswahl des Gruppenlinks eine Community-Gruppe erstellen, indem es eine Gruppenvorlage und ein Bild auswählt, ob die Gruppe offen oder geheim ist, und Mitglieder einlädt.

Dies ist ein Beispiel, bei dem eine Gruppe in der Veröffentlichungsumgebung erstellt wird.

Gruppen können auch in der Autorenumgebung erstellt und innerhalb der Community-Site in der Autorenumgebung verwaltet werden ([Community-Gruppenkonsole](/help/communities/groups.md)). Das Erlebnis von [Erstellen von Gruppen auf der Autoreninstanz](/help/communities/nested-groups.md) ist als Nächstes in diesem Tutorial beschrieben.

![grouplink](assets/grouplink.png)

Erstellen einer Referenzgruppe:

1. Wählen Sie **Neue Gruppe** aus
1. **Registerkarte &quot;Einstellungen&quot;**

   * Gruppenname : `Sports`
   * Beschreibung : `A parent group for various sporting groups`.
   * Gruppen-URL-Name : `sports`
   * Wählen Sie `Open Group` aus (erlauben Sie jedem Community-Mitglied die Teilnahme, indem es Mitglied wird)

1. **Registerkarte &quot;Vorlage&quot;**

   * Wählen Sie `Reference Group` aus (enthält eine Gruppenfunktion in ihrer Struktur, um verschachtelte Gruppen zuzulassen)

1. Wählen Sie **Gruppe erstellen**

   ![creategroup](assets/creategroup.png)

Nachdem die neue Gruppe erstellt wurde, wählen Sie **die neue Gruppe &quot;Sport&quot;** aus, um zwei Gruppen (verschachtelt) darin zu erstellen. Da eine Site-Struktur nicht mit der Funktion &quot;Gruppen&quot;beginnen kann, müssen Sie nach dem Öffnen der Gruppe &quot;Sport&quot;den Link Gruppen auswählen:

![grouplink1](assets/grouplink1.png)

Der zweite Satz von Links, beginnend mit `Blog`, gehört zur aktuell ausgewählten Gruppe, der Gruppe `Sports`. Durch Auswahl des Links &quot;Sport&#39; `Groups`&quot;können zwei Gruppen innerhalb der Gruppe &quot;Sport&quot;verschachtelt werden.

Fügen Sie als Beispiel zwei `new groups` hinzu.

* Eins namens `Baseball`

   * Behalten Sie den Wert als `Open Group` (erforderliche Mitgliedschaft) bei.
   * Wählen Sie auf der Registerkarte &quot;Vorlagen&quot;die Option `Conversational Group` aus.

* Eins namens `Gymnastics`

   * Ändern Sie die Einstellung in &quot;`Member Only Group`&quot;(eingeschränkte Mitgliedschaft).
   * Wählen Sie auf der Registerkarte &quot;Vorlagen&quot;die Option `Conversational Group` aus.

**Hinweis**:

* Eine Aktualisierung der Seite kann erforderlich sein, bevor beide Gruppen angezeigt werden.
* Diese Vorlage enthält die Gruppenfunktion *nicht*, sodass keine weitere Verschachtelung von Gruppen möglich ist.
* Beim Autor bietet die [Gruppenkonsole](/help/communities/groups.md) eine dritte Auswahl - eine `Public Group` (optionale Mitgliedschaft).

Nachdem beide Gruppen erstellt wurden, wählen Sie die Baseball-Gruppe, eine offene Gruppe, und beachten Sie die Links:

`Discussions` `What's New` `Members`

Die Links der Gruppe werden unter den Links der Hauptseite angezeigt und zeigen Folgendes an:

![grouplink2](assets/grouplink2.png)

Navigieren Sie bei Autor mit Administratorrechten zur Konsole [Communities-Gruppen](/help/communities/members.md) und fügen Sie Weston McCall zur Gruppe `Community Engage Gymnastics <uid> Members` hinzu.

Melden Sie sich weiterhin als Aaron McDonald an und sehen Sie sich die Gruppen in der Sportgruppe als anonymen Site-Besucher an:

* Von der Startseite
* Link `Groups` auswählen
* Link `Sports` auswählen
* Link &quot;Sport&#39; `Groups`&quot;auswählen

Nur die Baseballgruppe ist sichtbar.

Melden Sie sich als Weston McCall (weston.mccall@dodgit.com / Kennwort) an und navigieren Sie zum selben Speicherort. Beachten Sie, dass Weston in der Lage ist, die geöffnete Gruppe `Baseball` und entweder `enter or Leave` die private Gruppe `Gymnastics` mit `Join` zu versehen.

![grouplink3](assets/grouplink3.png)

### Web-Seiten-Link {#web-page-link}

Zeigen Sie die grundlegende Webseite der Site an, indem Sie den Link Webseite auswählen. Die standardmäßigen AEM-Authoring-Tools können verwendet werden, um Inhalte zu dieser Seite in der Autorenumgebung hinzuzufügen.

Rufen Sie beispielsweise die Instanz **author** auf, öffnen Sie den Ordner `engage` in der Konsole [Communities-Sites-Konsole](/help/communities/sites-console.md) und wählen Sie das Symbol **Site öffnen** aus, um in den Bearbeitungsmodus für Autoren zu wechseln. Wählen Sie dann den Vorschaumodus aus, damit Sie den Link `Web Page` auswählen und dann den Bearbeitungsmodus auswählen können, um die Komponenten Titel und Text hinzuzufügen. Veröffentlichen Sie zuletzt entweder nur die Seite oder die gesamte Site neu.

![webpagelink](assets/webpagelink.png)

### Moderationslink {#moderationlink}

Wenn das Community-Mitglied über Moderationsberechtigungen verfügt, ist der Moderations-Link sichtbar. Wenn Sie den Link auswählen, wird der gepostete Community-Inhalt angezeigt. Er kann [moderiert](/help/communities/moderate-ugc.md) werden, ähnlich wie in der [Moderationskonsole](/help/communities/moderation.md) in der Autorenumgebung.

Verwenden Sie die Zurück-Schaltfläche des Browsers, um zur veröffentlichten Site zurückzukehren. Die meisten Konsolen können nicht über die globale Navigation in der Veröffentlichungsumgebung aufgerufen werden.

![moderationlink](assets/moderationlink.png)

## Selbstregistrierung {#self-registration}

Nach dem Abmelden kann eine Benutzerregistrierung erstellt werden.

* Klicken Sie auf `Log In`
* Klicken Sie auf `Sign up for a new account`

![Registrierung](assets/registration.png)

![signup](assets/signup.png)

Standardmäßig ist die E-Mail-Adresse die Anmelde-ID. Wenn diese Option deaktiviert ist, kann der Besucher seine eigene Anmelde-ID (Benutzername) eingeben. Der Benutzername muss in der Veröffentlichungsumgebung eindeutig sein.

Nachdem Sie den Namen, die E-Mail-Adresse und das Kennwort des Benutzers angegeben haben, wird durch die Auswahl von `Sign Up` der Benutzer erstellt und zum Signieren aktiviert.

Nach dem Anmelden ist die erste angezeigte Seite ihre `Profile`-Seite, die sie personalisieren können.

![profile](assets/profile.png)

Wenn das Mitglied seine Anmelde-ID vergisst, kann es mithilfe seiner E-Mail-Adresse abgerufen werden.

![vergessusername](assets/forgotusername.png)
