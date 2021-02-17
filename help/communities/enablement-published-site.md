---
title: Erleben Sie die veröffentlichte Site
seo-title: Erleben Sie die veröffentlichte Site
description: Eine veröffentlichte Site zur Aktivierung aufrufen
seo-description: Eine veröffentlichte Site zur Aktivierung aufrufen
uuid: 1bfefa8a-fd9c-4ca8-b2ff-add79776c8ae
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 26715b94-e2ea-4da7-a0e2-3e5a367ac1cd
translation-type: tm+mt
source-git-commit: 4d21a61ed687caea2b1867d5321f75636f5310a3
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 2%

---



# Erleben Sie die veröffentlichte Site {#experience-the-published-site}


**[⇐ Erstellen und Zuweisen von Aktivierungsressourcen](resource.md)**

## Zu neuer Site bei Veröffentlichung suchen {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Community-Site und ihre Aktivierungsressourcen und der Lernpfad veröffentlicht wurden, ist es möglich, die Seite &quot;Aktivierungsübungen&quot;zu erleben.

Beginnen Sie damit, zu der URL zu navigieren, die beim Erstellen der Site angezeigt wird, jedoch auf dem Veröffentlichungsserver, z.

* Autor-URL = [http://localhost:4502/content/sites/enable/en.html](http://localhost:4502/content/sites/enable/en.html)
* Veröffentlichungs-URL = [http://localhost:4503/content/sites/enable/en.html](http://localhost:4503/content/sites/enable/en.html)

Wenn die Startseite [default](enablement-create-site.md#changethedefaulthomepage) festgelegt wurde, sollte die Site einfach [http://localhost:4503/](http://localhost:4503/) aufgerufen werden.

Bei der ersten Ankunft auf der veröffentlichten Site wäre der Site-Besucher normalerweise nicht bereits angemeldet und anonym.

**http://localhost:4503/content/sites/enable/en.html**

![enable-login](assets/enablement-login.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

Ein anonymer Site-Besucher wird sofort mit der Anmeldeseite für diese private Community-Site zur Aktivierung angezeigt. Beachten Sie, dass es keine Möglichkeit gibt, sich bei Facebook oder Twitter selbst zu registrieren oder sich anzumelden.

Beachten Sie, dass diese Startseite vier Menüelemente enthält: `Assignments, Ski Catalog, What's New` und `Discussions`, aber keine kann ohne Anmeldung erreicht werden.

>[!NOTE]
>
>Es ist möglich, anonymen Zugriff auf eine Aktivierungs-Site zu gewähren, ohne dass Site-Besucher sich selbst registrieren können.
>
>Wenn eine Aktivierungsressource auf `show in catalog` und `allow anonymous access` eingestellt ist, können anonyme Site-Besucher Ansichten im Katalog ausführen.

### Anonymen Zugriff auf JCR {#prevent-anonymous-access-on-jcr} verhindern

Durch eine bekannte Einschränkung wird der Inhalt der Community-Site anonymen Besuchern über jcr-Inhalte und json zugänglich gemacht, obwohl **[!UICONTROL Anonymen Zugriff zulassen]** für den Site-Inhalt deaktiviert ist. Dieses Verhalten kann jedoch mithilfe von Sling-Beschränkungen als Behelfslösung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff durch anonyme Benutzer durch jcr-Inhalte und json zu schützen:

1. Wechseln Sie in AEM Autoreninstanz zu https://&lt;Host>:&lt;Port>/editor.html/content/site/.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Gehen Sie zu **[!UICONTROL Seiteneigenschaften]**.

   ![page-properties](assets/page-properties.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Erweitert]**.
1. Aktivieren Sie **[!UICONTROL Authentifizierungsanforderung]**.

   ![site-authentication](assets/site-authentication.png)

1. hinzufügen den Pfad der Anmeldeseite. Beispiel: `/content/......./GetStarted`.
1. Veröffentlichen Sie die Seite.

## Eingeschriebenes Mitglied {#enrolled-member}

Dieses Erlebnis beruht darauf, dass die Benutzer `Riley Taylor` und `Sidney Croft` [erstellt und [ ](resource.md#settings) dem *Skiunterricht* Lernpfad durch ihre Mitgliedschaft in der *Community-Skiklasse* zugewiesen werden.](enablement-setup.md#publishcreateenablementmembers)

Anmelden mit

* `Username: riley`
* `Password: password`

Wenn das Profil nicht durch Selbstregistrierung erstellt wurde, wird bei der ersten Anmeldung eines Mitglieds dessen Profil angezeigt, sodass es überprüft und ggf. geändert werden kann.

Wenn sich das Mitglied das nächste Mal anmeldet, wird die durch das erste Menüelement identifizierte Startseite angezeigt.

![eingeschriebenes Mitglied](assets/enrolled-member.png)

### Zuweisungen {#assignments}

Auf der Seite &quot;Zuweisungen&quot;werden dem Mitglied alle Lernpfade und Aktivierungsressourcen angezeigt, die ihm speziell zugewiesen wurden.

Jede Zuweisung bietet grundlegende Informationen zu:

* Der Typ der Zuweisung
* Ob es sich um eine neue Zuweisung handelt
* Der Name
* Für die Art der Zuweisung relevante Details
* Aufgabenkontakt, Experte und Autor (falls vorhanden)

Der Zuweisungstyp wird durch ein Symbol in der oberen linken Ecke der Karte angezeigt. Das Bild einer Straße ist für einen Lernpfad mit der Anzahl der enthaltenen Aktivierungsressourcen gedacht.

![assign1](assets/assignment1.png)

Wenn Sie *Skiunterricht* auswählen, werden die beiden Aktivierungsressourcen angezeigt, auf die der Lernpfad verweist.

![assign2](assets/assignment2.png)

Wenn Sie *Skiunterricht 1* auswählen, wird die Detailseite der Aktivierungsressource geöffnet.

Auf der Detailseite kann das Mitglied lernen, [rate](rating.md) die Lektion und [Kommentare](comments.md) hinzufügen. Jede Aktivität eines Mitglieds wird im Abschnitt Neue Funktionen der Site angezeigt.

Interaktionen mit der Aktivierungsressource werden im Berichtsabschnitt vermerkt, auf den in der Autorendatei zugegriffen werden kann.

![assign3](assets/assignment3.png)

### Skikatalog {#ski-catalog}

Die Seite Skikatalog ist der Katalog der Aktivierungsressourcen, die mit Tags aus dem Namensraum `Tutorial` getaggt sind. Die beiden Ressourcen *Skiunterricht* werden mit dem Tag `Skiing` getaggt. Wenn also andere Tags als `All` oder `Tutorial: Sports / Skiing` ausgewählt sind, wird nichts angezeigt.

Wenn einem Mitglied weder direkt noch über einen Lernpfad Ressourcen für die Aktivierung zugewiesen wurden, ist es möglich, mit den in einem Katalog befindlichen Ressourcen für die Aktivierung zu interagieren und Feedback über Kommentare und Bewertungen bereitzustellen.

![ski-catalog](assets/ski-catalog.png)

### Diskussionen {#discussions}

Neben der Bewertung und dem Kommentieren von Aktivierungsressourcen ([bei Aktivierung](enablement-create-site.md#step33asettings)) enthält die Community-Site-Vorlage, aus der `Enablement Tutorial` erstellt wurde, die [Forumsfunktion](functions.md#forum-function) (Titel ist `Discussions)`.

Wählen Sie den Link `Discussions`und posten Sie ein Thema.

Melden Sie sich ab und melden Sie sich als Sidney Croft (Sidney / Passwort) an und beantworten Sie die Frage sowie Folgen Sie dem Thema.

Beachten Sie, dass es neben der Inline-Moderation Optionen gibt, das Thema in sozialen Medien freizugeben oder das Thema per E-Mail zu versenden.

![Diskussionen](assets/discussions.png)

### Neue Funktionen {#what-s-new}

Das Menüelement `What's New` ist der Titel der [Aktivität-Stream-Funktion](functions.md#activity-stream-function) in der Struktur dieser Community-Site.

Wählen Sie noch als Sidney angemeldet den Link `What's New` aus, um die Aktivität anzuzeigen.

![whats-new-menu](assets/whats-new-menu.png)

## Vertrauenswürdiges Community-Mitglied {#trusted-community-member}

Dieses Erlebnis setzt voraus, dass ` [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)` die Rollen von [Moderator](enablement-create-site.md#moderation) und [Ressourcenkontakt](resource.md#settings) zugewiesen wurden.

Anmelden mit

* `Username: quinn`
* `Password: password`

Nach der Anmeldung gibt es einen neuen Menüpunkt `Administration`, der angezeigt wird, weil dem Mitglied die Rolle des Moderators zugewiesen wurde.

![trust-member-homepage](assets/trusted-member-homepage.png)

Die Startseite wird durch den ersten Menüpunkt Zuweisungen gekennzeichnet. Quinn ist der Ansprechpartner für Moderator- und Aktivierungsressourcen und wurde nicht in Aktivierungsressourcen oder Lernpfaden eingeschrieben. Es ist daher nichts anzuzeigen.

### Administration {#administration}

Was es gibt, ist die Aktivität der beiden Lernenden, `Riley Taylor` und `Sidney Croft`. Durch Auswahl des Links `Administration` für den Zugriff auf die Moderationskonsole kann Quinn die [Massenmoderationskonsole](moderation.md) verwenden, um ihre Beiträge zu moderieren.

Wenn Sie das Symbol für das Seitenbedienfeld auswählen, werden die Filter geöffnet, die zum Durchsuchen von Community-Inhalten verwendet werden.

Wenn Sie den Mauszeiger über eine Kommentarkarte bewegen, werden Moderationsaktionen angezeigt.

![Administration](assets/administration.png)

## Berichte zum Autor {#reports-on-author}

Es gibt zwei Möglichkeiten, auf Berichte für Lernende zuzugreifen und Ressourcen zu aktivieren.

Navigieren Sie beim Autor zu den Communities, [Ressourcenkonsole ](resources.md)**, in denen die Aktivierungsressourcen verwaltet werden, und nach Auswahl einer Community-Site können Sie Berichte für**

* Alle Aktivierungsressourcen und Lernpfade
* Eine spezifische Aktivierungsressource oder ein Lernpfad

Navigieren Sie zur Konsole **Communities, [Berichte](reports.md)** und generieren Sie Berichte gemäß:

* Zuweisung zu aktivierenden Ressourcen und Lernpfaden
* Beiträge zu einer Community-Site über einen bestimmten Zeitraum
* Ansichten (Site-Besuche) einer Community-Site über einen bestimmten Zeitraum

* Beiträge und Ansichten können für alle Inhalte oder für bestimmte Inhalte verwendet werden:

   * Forum
   * Forumthema
   * Frage und Antwort
   * Frage
   * Blog
   * Blog-Artikel
   * Kalender
   * Kalenderereignis

### Ressourcenkonsole {#resources-console}

Mit ein wenig Aktivität und Interaktion mit den Ressourcen bei der Veröffentlichung lohnt es sich, die Berichte zum Autor anzuzeigen.

* Melden Sie sich beim Autor mit Administratorrechten an.
* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Communities]** > **[!UICONTROL Ressourcen]**.
* Wählen Sie die Site `Enablement Tutorial` aus.
* Klicken Sie auf das Symbol `Report`, um eine Zusammenfassung aller Ressourcen anzuzeigen.
* Wählen Sie eine Ressource und dann das `Report`-Symbol für einen Bericht über diese Ressource aus.

Beachten Sie, dass es wahrscheinlich zu früh ist, Daten aus Adobe Analytics anzuzeigen, die bis zu 12 Stunden dauern können. Es ist jedoch bereits ein einfacher SCORM-Berichte verfügbar.

#### Bericht zu den Ressourcen für Skifahrten {#ski-lessons-resource-report}

![ski-stunden-report](assets/ski-lessons-report.png)

#### Bericht &quot;Skilehrer/innen&quot;{#ski-lessons-user-report}

* Wählen Sie **[!UICONTROL Communities > Ressourcen]**

* Karte öffnen `Enablement Tutorial`
* Karte öffnen `Ski Lessons`
* Wählen Sie nun eine der folgenden Optionen aus `Report > User Report`

![ski-stunden-user-report](assets/ski-lessons-user-report.png)

### Berichte-Konsole {#reports-console}

Die Konsole &quot;Berichte&quot;ermöglicht die Erstellung von Berichten über

* **Zuweisungen** für eine beliebige Community-Site für eine Aktivierung
* **** Ansichten jeder Community-Site
* **Postings** für jede Community-Site

Für Zuweisungsberichte:

* Melden Sie sich beim Autor mit Administratorrechten an.
* Navigieren Sie zu **[!UICONTROL Communities]** > **[!UICONTROL Berichte]** > **[!UICONTROL Zuweisungsbericht]**.
* Wählen Sie eine **[!UICONTROL Site]** aus dem Pulldown-Menü (wählen Sie `Enablement Tutorial`).

* Wählen Sie **[!UICONTROL Gruppe]** (wählen Sie `Community Ski Class`)

* Wählen Sie eine **[!UICONTROL Zuweisung]** (wählen Sie `Ski Lessons` aus)

* Wählen Sie **[!UICONTROL Generieren]**

![report-zuweisung](assets/report-assignment.png)

Für Berichte zu Ansichten:

* Melden Sie sich beim Autor mit Administratorrechten an.
* Navigieren Sie zu **[!UICONTROL Communities]** > **[!UICONTROL Berichte]** > **[!UICONTROL Ansichten-Bericht]**.
* Wählen Sie eine **Site** aus dem Pulldown-Menü (wählen Sie `Enablement Tutorial`).

* Wählen Sie **[!UICONTROL Inhaltstyp]** (wählen Sie `all`).

* Wählen Sie einen **[!UICONTROL Datumsbereich]** aus (wählen Sie `Last 7 days` aus).

* Wählen Sie **[!UICONTROL Generate]**.

![report-Ansichten](assets/report-views.png)

**[⇐ Erstellen und Zuweisen von Aktivierungsressourcen](resource.md)**
