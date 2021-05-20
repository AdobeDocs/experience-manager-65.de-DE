---
title: Erlebnis der veröffentlichten Site
seo-title: Erlebnis der veröffentlichten Site
description: Navigieren zu einer veröffentlichten Site
seo-description: Navigieren zu einer veröffentlichten Site
uuid: 44594e9e-27ad-475d-953d-3611b04f0df8
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: dd0cbc05-a361-46bc-b9f1-d045f8f23890
docset: aem65
exl-id: ebc4e1e7-34f0-4f4e-9f00-178dfda23ce4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 2%

---

# Erleben Sie die veröffentlichte Site {#experience-the-published-site}

## Navigieren Sie zur neuen Site auf der Veröffentlichungsinstanz {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Communities-Site veröffentlicht wurde, navigieren Sie zur URL, die beim Erstellen der Site angezeigt wird, aber auf dem Veröffentlichungsserver, z. B.:

* Autoren-URL = https://localhost:4502/content/sites/engage/en.html
* Veröffentlichungs-URL = https://localhost:4503/content/sites/engage/en.html

Um Verwirrungen zu vermeiden, welches Mitglied bei der Autoren- und Veröffentlichungsinstanz angemeldet ist, wird empfohlen, für jede Instanz unterschiedliche Browser zu verwenden.

Bei der ersten Ankunft auf der veröffentlichten Site wäre der Site-Besucher in der Regel nicht bereits angemeldet und anonym.

`https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}`

![authorVeröffentlicht](assets/authorpublished.png)

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

Durch eine bekannte Einschränkung wird der Community-Site-Inhalt anonymen Besuchern über JCR-Inhalt und JSON bereitgestellt, obwohl **Anonymen Zugriff zulassen** für den Site-Inhalt deaktiviert ist. Dieses Verhalten kann jedoch mithilfe von Sling-Einschränkungen als Problemumgehung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff anonymer Benutzer durch jcr-Inhalte und JSON zu schützen:

1. Wechseln Sie in der AEM-Autoreninstanz zu https:// Hostname: port/editor.html/content/site/sitename.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Navigieren Sie zu **Seiteneigenschaften**.

   ![page-properties](assets/page-properties.png)

1. Navigieren Sie zur Registerkarte **Erweitert**.

1. Aktivieren Sie **Authentifizierungspflicht**.

   ![site-authentication](assets/site-authentication.png)

1. Fügen Sie den Pfad der Anmeldeseite hinzu. Zum Beispiel **/content/....../GetStarted**.
1. Veröffentlichen Sie die Seite.

## Vertrauenswürdige Community-Mitglieder {#trusted-community-member}

Dieses Erlebnis setzt voraus, dass [Aaron McDonald](/help/communities/tutorials.md#demo-users) die Rollen von [Community Manager und Moderator](/help/communities/create-site.md#roles) zugewiesen wurde. Wenn nicht, kehren Sie zur Autorenumgebung zurück zu [ändern Sie die Site-Einstellungen](/help/communities/sites-console.md#modifying-site-properties) und wählen Sie Aaron McDonald als Community-Manager und Moderator aus.

Wählen Sie in der oberen rechten Ecke `Log in` aus und signieren Sie mit dem Benutzernamen (aaron.mcdonald@mailinator.com) und dem Kennwort (Kennwort). Beachten Sie die Möglichkeit, sich mit Twitter- oder Facebook-Anmeldeinformationen anzumelden.

![anmelden](assets/login.png)

Nachdem Sie sich als registriertes Community-Mitglied angemeldet haben, beachten Sie die folgenden Menüpunkte, um auf Ihre Community-Site zu klicken und sie zu erkunden:

* **** Mit der Option Profil können Sie Ihr Profil anzeigen und bearbeiten.
* [](/help/communities/configure-messaging.md) Die Option &quot;Nachrichten&quot;leitet Sie zum Abschnitt &quot;Direktnachrichten&quot;weiter, in dem Sie Folgendes tun können:

   1. Zeigen Sie die Direktnachrichten an, die Sie empfangen haben (Posteingang), gesendet (Gesendete Elemente) und gelöscht (Papierkorb).
   1. Erstellen Sie neue Direktnachrichten, die an Einzelpersonen und Gruppen gesendet werden.

* [](/help/communities/notifications.md) Die Option Benachrichtigungen leitet Sie zum Abschnitt Benachrichtigungen weiter, in dem Sie Ihre interessanten Ereignisse anzeigen und die Benachrichtigungseinstellungen bearbeiten können.
* [](/help/communities/published-site.md#moderationlink) Wenn Sie über Moderationsberechtigungen verfügen, leitet Sie die Administration zur Seite &quot;AEM Communities-Moderation&quot;weiter.

![adminscreen](assets/adminscreen.png)

Beachten Sie, dass die Kalenderseite die Startseite ist, da die ausgewählte Referenz-Site-Vorlage zuerst die Kalenderfunktion, gefolgt von der Aktivitäts-Stream-Funktion, der Forumsfunktion usw. enthält. Diese Struktur ist in der Konsole [Site-Vorlage](/help/communities/sites.md#edit-site-template) oder beim Ändern der Site-Eigenschaften in der Autorenumgebung sichtbar:

![sitetemplate](assets/sitetemplate.png)

>[!NOTE]
>
>Weitere Informationen zu Communities-Komponenten und -Funktionen finden Sie unter:
>
>* [Communities-Komponenten](/help/communities/author-communities.md)  (für Autoren)
>* [Komponenten-, Funktionen- und Funktionsgrundlagen](/help/communities/essentials.md)  (für Entwickler)


### Forum link {#forum-link}

Klicken Sie auf den Link Forum , um die grundlegende Forumsfunktion anzuzeigen.

Mitglieder können ein neues Thema posten oder einem Thema folgen.

Besucher der Site können Beiträge auf verschiedene Weise anzeigen und sortieren.

![forumlink](assets/forumlink.png)

### Gruppenlink {#groups-link}

Da Aaron ein Gruppenadministrator ist, kann Aaron durch Auswahl des Links Gruppen eine neue Community-Gruppe erstellen, indem es eine Gruppenvorlage und ein Bild auswählt, ob die Gruppe offen oder geheim ist, und Mitglieder einlädt.

Dies ist ein Beispiel, bei dem eine Gruppe in der Veröffentlichungsumgebung erstellt wird.

Gruppen können auch in der Autorenumgebung erstellt und innerhalb der Community-Site in der Autorenumgebung verwaltet werden ([Community-Gruppenkonsole](/help/communities/groups.md)). Das Erlebnis von [Erstellen von Gruppen für Autor](/help/communities/nested-groups.md) ist als Nächstes in diesem Tutorial verfügbar.

![grouplink](assets/grouplink.png)

Erstellen einer Referenzgruppe:

1. Wählen Sie **Neue Gruppe**
1. **Registerkarte „Settings“**

   * Gruppenname : `Sports`
   * Beschreibung : `A parent group for various sporting groups`.
   * Gruppen-URL-Name : `sports`
   * Wählen Sie `Open Group` aus (erlauben Sie jedem Community-Mitglied die Teilnahme, indem Sie Mitglied werden).

1. **Registerkarte &quot;Vorlage&quot;**

   * Wählen Sie `Reference Group` aus (enthält eine Gruppenfunktion in ihrer Struktur, um verschachtelte Gruppen zuzulassen)

1. Wählen Sie **Gruppe erstellen**

   ![creategroup](assets/creategroup.png)

Nachdem eine neue Gruppe erstellt wurde, wählen Sie **die neue Gruppe &quot;Sport**&quot;aus, um zwei Gruppen (verschachtelt) darin zu erstellen. Da eine Site-Struktur nicht mit der Funktion &quot;Gruppen&quot;beginnen kann, müssen Sie nach dem Öffnen der Gruppe &quot;Sport&quot;den Link Gruppen auswählen:

![grouplink1](assets/grouplink1.png)

Der zweite Satz von Links, beginnend mit `Blog`, gehört zur aktuell ausgewählten Gruppe, der Gruppe `Sports`. Durch Auswahl des Links &quot;Sport&quot; `Groups` können zwei Gruppen innerhalb der Gruppe &quot;Sport&quot;verschachtelt werden.

Fügen Sie beispielsweise zwei `new groups` hinzu.

* Eins mit dem Namen `Baseball`

   * Behalten Sie den Wert `Open Group` bei (erforderliche Mitgliedschaft).
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group` aus.

* Eins mit dem Namen `Gymnastics`

   * Ändern Sie die Einstellung in `Member Only Group` (eingeschränkte Mitgliedschaft).
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group` aus.

**Hinweis**:

* Eine Aktualisierung der Seite kann erforderlich sein, bevor beide Gruppen angezeigt werden.
* Diese Vorlage enthält die Gruppenfunktion *nicht*, sodass keine weitere Verschachtelung von Gruppen möglich ist.
* Bei der Autoreninstanz bietet die [Gruppenkonsole](/help/communities/groups.md) eine dritte Wahl - eine `Public Group` (optionale Mitgliedschaft).

Nachdem beide Gruppen erstellt wurden, wählen Sie die Baseball-Gruppe, eine offene Gruppe, und beachten Sie die Links:

`Discussions` `What's New` `Members`

Die Links der Gruppe werden unter den Links der Hauptseite angezeigt und zeigen Folgendes an:

![grouplink2](assets/grouplink2.png)

Navigieren Sie auf der Autoreninstanz mit Administratorrechten zur Konsole [Communities-Gruppen](/help/communities/members.md) und fügen Sie Weston McCall zur Gruppe `Community Engage Gymnastics <uid> Members` hinzu.

Melden Sie sich weiterhin als Aaron McDonald an und sehen Sie sich die Gruppen in der Sportgruppe als anonymen Site-Besucher an:

* Von der Startseite
* Link `Groups` auswählen
* Link `Sports` auswählen
* Link &quot;Sports&#39; `Groups`&quot;auswählen

Nur die Baseballgruppe wird sichtbar sein.

Melden Sie sich als Weston McCall (weston.mccall@dodgit.com / Kennwort) an und navigieren Sie zum selben Speicherort. Beachten Sie, dass Weston in der Lage ist, die Gruppe `Join` öffnen `Baseball` und entweder `enter or Leave` die private Gruppe `Gymnastics` zu verwenden.

![grouplink3](assets/grouplink3.png)

### Web Page link {#web-page-link}

Zeigen Sie die grundlegende Webseite der Site an, indem Sie den Link Webseite auswählen. Die standardmäßigen AEM-Authoring-Tools können verwendet werden, um Inhalte zu dieser Seite in der Autorenumgebung hinzuzufügen.

Wechseln Sie beispielsweise zur Instanz **author**, öffnen Sie den Ordner `engage` in der Konsole [Communities Sites](/help/communities/sites-console.md) und wählen Sie das Symbol **Site öffnen** aus, um in den Bearbeitungsmodus für Autoren zu wechseln. Wählen Sie dann den Vorschaumodus aus, um den Link `Web Page` auszuwählen, und wählen Sie dann den Bearbeitungsmodus, um die Komponenten Titel und Text hinzuzufügen. Veröffentlichen Sie zuletzt entweder nur die Seite oder die gesamte Site neu.

![webpagelink](assets/webpagelink.png)

### Moderationslink {#moderationlink}

Wenn das Community-Mitglied über Moderationsberechtigungen verfügt, wird der Moderations-Link angezeigt und durch seine Auswahl wird der veröffentlichte Community-Inhalt angezeigt und kann [moderiert](/help/communities/moderate-ugc.md) auf eine Weise sein, die der [Moderationskonsole](/help/communities/moderation.md) in der Autorenumgebung ähnelt.

Verwenden Sie die Zurück-Schaltfläche des Browsers, um zur veröffentlichten Site zurückzukehren. Die meisten Konsolen können nicht über die globale Navigation in der Veröffentlichungsumgebung aufgerufen werden. [](/help/communities/moderate-ugc.md)

![moderationlink](assets/moderationlink.png)

## Selbstregistrierung {#self-registration}

Nach dem Abmelden ist es möglich, eine neue Benutzerregistrierung zu erstellen.

* Wählen Sie nun eine der folgenden Optionen aus `Log In`
* Wählen Sie nun eine der folgenden Optionen aus `Sign up for a new account`

![registrierung](assets/registration.png)

![anmelden](assets/signup.png)

Standardmäßig ist die E-Mail-Adresse die Anmelde-ID. Wenn diese Option deaktiviert ist, kann der Besucher seine eigene Anmelde-ID (Benutzername) eingeben. Der Benutzername muss in der Veröffentlichungsumgebung eindeutig sein.

Nachdem Sie den Namen, die E-Mail-Adresse und das Kennwort des Benutzers angegeben haben, können Sie durch die Auswahl von `Sign Up` den Benutzer erstellen und signieren.

Nach der Anmeldung ist die erste angezeigte Seite ihre `Profile`-Seite, die sie personalisieren können.

![Profil](assets/profile.png)

Wenn das Mitglied seine Anmelde-ID vergisst, kann es mithilfe seiner E-Mail-Adresse abgerufen werden.

![forgotusername](assets/forgotusername.png)
