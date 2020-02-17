---
title: Die veröffentlichte Site
seo-title: Die veröffentlichte Site
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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Die veröffentlichte Site {#experience-the-published-site}

## Neue Site bei Veröffentlichung suchen {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Communities-Site veröffentlicht wurde, navigieren Sie zur URL, die beim Erstellen der Site angezeigt wird, jedoch auf dem Veröffentlichungsserver, z.

* author URL = https://localhost:4502/content/sites/engage/en.html
* publish URL = https://localhost:4503/content/sites/engage/en.html

Um Verwirrung darüber zu vermeiden, welches Mitglied bei Autor und Veröffentlichung angemeldet ist, wird empfohlen, für jede Instanz verschiedene Browser zu verwenden.

Bei der ersten Ankunft auf der veröffentlichten Site wurde der Site-Besucher in der Regel nicht bereits angemeldet und wäre anonym.

`https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}`

![chlimage_1-31](assets/chlimage_1-31.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

Ein anonymer Site-Besucher sieht Folgendes in der Benutzeroberfläche:

* Titel der Site. Erste Schritte-Lernprogramm
* Kein Profillink
* Keine Nachrichten
* Kein Benachrichtigungslink
* Suchfeld
* Link anmelden
* Das Markenbanner
* Menüverknüpfungen für die in der Referenz-Site-Vorlage enthaltenen Komponenten

Wenn Sie verschiedene Links auswählen, befinden Sie sich im schreibgeschützten Modus.

### Anonymen Zugriff auf JCR verhindern {#prevent-anonymous-access-on-jcr}

Eine bekannte Einschränkung setzt den Inhalt der Community-Site anonymen Besuchern durch jcr-Inhalte und json aus, obwohl der anonyme Zugriff **für den Site-Inhalt deaktiviert** ist. Dieses Verhalten kann jedoch mithilfe von Sling-Beschränkungen als Behelfslösung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff durch anonyme Benutzer durch jcr-Inhalte und json zu schützen:

1. Wechseln Sie in der AEM-Autoreninstanz zu https://&lt;Host>:&lt;Port>/editor.html/content/site/&lt;sitename>.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Gehen Sie zu **Seiteneigenschaften**.

   ![site-authentication](assets/site-authentication.png)

1. Gehen Sie zu **Erweitert **Registerkarte.

   ![page-properties](assets/page-properties.png)

1. Enable **Authentication Requirement**.
1. Fügen Sie den Pfad der Anmeldeseite hinzu. For example,**/content/......./GetStarted**.
1. Veröffentlichen Sie die Seite.

## Vertrauenswürdiger Community-Mitglied {#trusted-community-member}

Diese Erfahrung setzt voraus, dass [Aaron McDonald](/help/communities/tutorials.md#demo-users) die Rollen von [Community Manager und Moderator](/help/communities/create-site.md#roles)zugewiesen wurde. Andernfalls kehren Sie zur Autorenumgebung zurück, um die Site-Einstellungen[ zu ](/help/communities/sites-console.md#modifying-site-properties)ändern, und wählen Sie Aaron McDonald als Community Manager und Moderator aus.

Wählen Sie in der oberen rechten Ecke den Benutzernamen &quot;aaron.mcdonald@mailinator.com&quot; `Log in`und das Kennwort &quot;password&quot;aus und melden Sie sich an. Beachten Sie die Möglichkeit, sich mit Twitter- oder Facebook-Anmeldedaten anzumelden.

![chlimage_1-32](assets/chlimage_1-32.png)

Nachdem Sie sich als registriertes Community-Mitglied angemeldet haben, beachten Sie die folgenden Menüpunkte, um auf Ihre Community-Site zu klicken und sie zu erkunden:

* **Mit der Profiloption** können Sie Ihr Profil anzeigen und bearbeiten.
* [Die Option &quot;Nachrichten](/help/communities/configure-messaging.md) &quot;leitet Sie zum Abschnitt &quot;Direktnachrichten&quot;weiter, in dem Sie Folgendes ausführen können:

1. Zeigen Sie die Direktnachrichten an, die Sie erhalten haben (Posteingang), gesendet (Gesendete Artikel) und gelöscht (Papierkorb).
1. Erstellen Sie neue Direktnachrichten, die an Personen und Gruppen gesendet werden.

* [Die Option &quot;Benachrichtigungen](/help/communities/notifications.md) &quot;leitet Sie zum Abschnitt &quot;Benachrichtigungen&quot;weiter, in dem Sie Ihre interessanten Ereignisse anzeigen und die Benachrichtigungseinstellungen bearbeiten können.
* [Administration](/help/communities/published-site.md#moderationlink) leitet Sie zur AEM Communities-Moderationsseite weiter, wenn Sie über Moderationsberechtigungen verfügen.

![chlimage_1-33](assets/chlimage_1-33.png)

Beachten Sie, dass die Seite &quot;Kalender&quot;die Homepage ist, da die ausgewählte Referenz-Site-Vorlage zuerst die Funktion &quot;Kalender&quot;enthielt, gefolgt von der Funktion &quot;Aktivitäts-Stream&quot;, der Funktion &quot;Forum&quot;usw. Diese Struktur ist in der Konsole [Site-Vorlage](/help/communities/sites.md#edit-site-template) oder beim Ändern der Site-Eigenschaften in der Autorenumgebung sichtbar:

![chlimage_1-34](assets/chlimage_1-34.png)

>[!NOTE]
>
>Weitere Informationen zu Communities-Komponenten und -Funktionen finden Sie unter
>
>* [Communities-Komponenten](/help/communities/author-communities.md) (für Autoren)
>* [Komponenten-, Funktionen- und Funktionsgrundlagen](/help/communities/essentials.md) (für Entwickler)
>



### Forum-Link {#forum-link}

Zeigen Sie die grundlegende Funktion des Forums an, indem Sie den Link Forum auswählen.

Mitglieder können ein neues Thema posten oder einem Thema folgen.

Site-Besucher können Beiträge auf verschiedene Weise anzeigen und sortieren.

![chlimage_1-35](assets/chlimage_1-35.png)

### Gruppen-Link {#groups-link}

Da Aaron ein Gruppenadministrator ist, kann Aaron mithilfe des Links Gruppen eine neue Community-Gruppe erstellen, indem es eine Gruppenvorlage, ein Bild, ob die Gruppe offen oder geheim ist, und einladende Mitglieder auswählt.

Dies ist ein Beispiel, bei dem eine Gruppe in der Veröffentlichungsumgebung erstellt wird.

Gruppen können auch in der Autorenumgebung erstellt und innerhalb der Community-Site in der Autorenumgebung ( [Community Groups-Konsole](/help/communities/groups.md)) verwaltet werden. Die Erfahrung mit dem [Erstellen von Gruppen unter Autor](/help/communities/nested-groups.md) ist als Nächstes in dieser Übung.

![chlimage_1-36](assets/chlimage_1-36.png)

Erstellen einer Referenzgruppe:

1. Neue **Gruppe auswählen**
1. **Registerkarte „Settings“**

   * Gruppenname : `Sports`
   * Beschreibung : `A parent group for various sporting groups`
   * Gruppen-URL-Name : `sports`
   * auswählen `Open Group` (die Teilnahme von Community-Mitgliedern durch Beitritt zulassen)

1. **Registerkarte &quot;Vorlage&quot;**

   * select `Reference Group` (enthält eine Gruppenfunktion in ihrer Struktur, um verschachtelte Gruppen zuzulassen)

1. Gruppe **erstellen auswählen**

![chlimage_1-37](assets/chlimage_1-37.png)

Nachdem eine neue Gruppe erstellt wurde, **wählen Sie die neue Sportgruppe** aus, um zwei Gruppen (verschachtelt) darin zu erstellen. Da eine Site-Struktur nicht mit der Funktion &quot;Gruppen&quot;beginnen kann, muss nach dem Öffnen der Gruppe &quot;Sport&quot;der Link &quot;Gruppen&quot;ausgewählt werden:

![chlimage_1-38](assets/chlimage_1-38.png)

Der zweite Satz von Links, beginnend mit `Blog`, gehört zur aktuell ausgewählten Gruppe, der `Sports`Gruppe. Durch Auswahl des `Groups` Links &quot;Sport&quot;können zwei Gruppen innerhalb der Gruppe &quot;Sport&quot;verschachtelt werden.

Fügen Sie als Beispiel zwei n `ew groups.`

* einer `Baseball`

   * als `Open Group` (erforderliche) Mitgliedschaft festlegen
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group`

* einer `Gymnastics`

   * ihre Einstellung auf `Member Only Group` (eingeschränkte Mitgliedschaft) ändern
   * Wählen Sie auf der Registerkarte Vorlagen die Option `Conversational Group`

**Hinweis **:

* eine Aktualisierung der Seite erforderlich ist, bevor beide Gruppen angezeigt werden
* Diese Vorlage enthält *nicht *die Funktion groups, sodass keine weitere Verschachtelung von Gruppen möglich ist
* bei Autoren bietet die [Gruppenkonsole](/help/communities/groups.md) eine dritte Option - eine `Public Group` (optionale Mitgliedschaft)

Nachdem beide Gruppen erstellt wurden, wählen Sie die Baseball-Gruppe, eine offene Gruppe, und beachten Sie deren Links:

`Discussions` `What's New` `Members`

Die Links der Gruppe werden unterhalb der Links der Haupt-Site angezeigt und führen zur folgenden Anzeige:

![chlimage_1-39](assets/chlimage_1-39.png)

Unter &quot;Autor&quot;- mit Administratorrechten navigieren Sie zur [Communities Groups-Konsole](/help/communities/members.md) und fügen Sie der `Community Engage Gymnastics <uid> Members` Gruppe Weston McCall hinzu.

Melden Sie sich weiterhin bei der Veröffentlichung als Aaron McDonald an und sehen Sie sich die Gruppen in der Sports Group als anonymen Site-Besucher an:

* von der Homepage
* select `Groups`link
* select `Sports`link
* den `Groups`Link &quot;Sport&quot;auswählen

Nur die Baseballgruppe wird angezeigt.

Melden Sie sich als Weston McCall (weston.mccall@dodgit.com / Kennwort) an und navigieren Sie zum gleichen Speicherort. Beachten Sie, dass Weston in der Lage ist, `Join` die offene `Baseball` Gruppe und entweder `enter or Leave` die private `Gymnastics`Gruppe.

![chlimage_1-40](assets/chlimage_1-40.png)

### Link zur Webseite {#web-page-link}

Zeigen Sie die grundlegende Webseite der Site an, indem Sie den Link &quot;Webseite&quot;auswählen. Die standardmäßigen AEM-Authoring-Werkzeuge können verwendet werden, um dieser Seite Inhalte in der Autorenumgebung hinzuzufügen.

Rufen Sie beispielsweise die **Autoreninstanz** auf, öffnen Sie den `engage` Ordner in der Konsole[&quot; ](/help/communities/sites-console.md)Communities Sites&quot;und klicken Sie auf das Symbol zum **Öffnen der Site** , um in den Bearbeitungsmodus für Autoren zu wechseln. Wählen Sie dann den Vorschaumodus, um die `Web Page`Verknüpfung auszuwählen, und wählen Sie dann den Bearbeitungsmodus, um Titel- und Textkomponenten hinzuzufügen. Als letztes veröffentlichen Sie entweder nur die Seite oder die gesamte Site erneut.

![chlimage_1-41](assets/chlimage_1-41.png)

### Moderationslink {#moderationlink}

Wenn das Community-Mitglied über Moderationsberechtigungen verfügt, wird der Link &quot;Moderation&quot;angezeigt. Wenn Sie ihn auswählen, werden die veröffentlichten Community-Inhalte angezeigt und können ähnlich wie die [Moderationskonsole](/help/communities/moderate-ugc.md) in der Autorenumgebung [moderiert](/help/communities/moderation.md) werden.

Verwenden Sie die Zurück-Schaltfläche des Browsers, um zur veröffentlichten Site zurückzukehren. Die meisten Konsolen sind von der globalen Navigation in der Veröffentlichungsumgebung aus nicht zugänglich. [](/help/communities/moderate-ugc.md)

![chlimage_1-42](assets/chlimage_1-42.png)

## Selbstregistrierung {#self-registration}

Nach dem Abmelden ist es möglich, eine neue Benutzerregistrierung zu erstellen.

* auswählen `Log In`
* auswählen `Sign up for a new account`

![chlimage_1-43](assets/chlimage_1-43.png) ![chlimage_1-44](assets/chlimage_1-44.png)

Standardmäßig ist die E-Mail-Adresse die Anmelde-ID. Wenn diese Option deaktiviert ist, kann der Besucher seine eigene Anmelde-ID (Benutzername) eingeben. Der Benutzername muss in der Veröffentlichungsumgebung eindeutig sein.

Nachdem Sie den Namen, die E-Mail-Adresse und das Kennwort des Benutzers angegeben haben, `Sign Up`wird durch Auswahl dieser Option der Benutzer erstellt und für die Unterzeichnung aktiviert.

Nach dem Anmelden ist die erste angezeigte Seite ihre `Profile`Seite, die sie personalisieren können.

![chlimage_1-45](assets/chlimage_1-45.png)

Wenn das Mitglied seine Anmelde-ID vergisst, ist es möglich, wiederherzustellen, wenn ihre E-Mail-Adresse verwendet wird.

![chlimage_1-46](assets/chlimage_1-46.png)

