---
title: Die veröffentlichte Site
seo-title: Die veröffentlichte Site
description: Eine veröffentlichte Site zur Aktivierung aufrufen
seo-description: Eine veröffentlichte Site zur Aktivierung aufrufen
uuid: 1bfefa8a-fd9c-4ca8-b2ff-add79776c8ae
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 26715b94-e2ea-4da7-a0e2-3e5a367ac1cd
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---



# Die veröffentlichte Site {#experience-the-published-site}


**[⇐ Erstellen und Zuweisen von Aktivierungsressourcen](resource.md)**

## Neue Site bei Veröffentlichung suchen {#browse-to-new-site-on-publish}

Nachdem die neu erstellte Community-Site und ihre Aktivierungsressourcen und der Lernpfad veröffentlicht wurden, ist es möglich, die Seite &quot;Aktivierungsübungen&quot;zu erleben.

Beginnen Sie damit, zu der URL zu navigieren, die beim Erstellen der Site angezeigt wird, jedoch auf dem Veröffentlichungsserver, z.

* author URL = [http://localhost:4502/content/sites/enable/en.html](http://localhost:4502/content/sites/enable/en.html)
* publish URL = [http://localhost:4503/content/sites/enable/en.html](http://localhost:4503/content/sites/enable/en.html)

Wenn die [Standardstartseite festgelegt](enablement-create-site.md#changethedefaulthomepage)wurde, sollte die Site einfach zu [http://localhost:4503/](http://localhost:4503/) navigieren.

Bei der ersten Ankunft auf der veröffentlichten Site wurde der Site-Besucher in der Regel nicht bereits angemeldet und wäre anonym.

**http://localhost:4503/content/sites/enable/en.html**

![chlimage_1-433](assets/chlimage_1-433.png)

## Anonymer Site-Besucher {#anonymous-site-visitor}

Ein anonymer Sitebesucher wird sofort mit der Anmeldeseite für diese private Community-Site zur Aktivierung angezeigt. Beachten Sie, dass es keine Möglichkeit gibt, sich bei Facebook oder Twitter selbst zu registrieren oder sich anzumelden.

Beachten Sie, dass auf dieser Homepage vier Menüelemente angezeigt werden: `Assignments, Ski Catalog, What's New` und `Discussions`, jedoch ohne Anmeldung nicht erreicht werden.

>[!NOTE]
>
>Es ist möglich, anonymen Zugriff auf eine Aktivierungs-Site zu gewähren, ohne dass Site-Besucher sich selbst registrieren können.
>Wenn eine Aktivierungsressource auf `show in catalog` und festgelegt ist, können anonyme Site-Besucher Ressourcen im Katalog anzeigen. `allow anonymous access`Dies ist möglich.

### Anonymen Zugriff auf JCR verhindern {#prevent-anonymous-access-on-jcr}

Eine bekannte Einschränkung setzt den Inhalt der Community-Site anonymen Besuchern durch jcr-Inhalte und json aus, obwohl der anonyme Zugriff **[!UICONTROL für den Site-Inhalt deaktiviert]** ist. Dieses Verhalten kann jedoch mithilfe von Sling-Beschränkungen als Behelfslösung gesteuert werden.

Gehen Sie wie folgt vor, um den Inhalt Ihrer Community-Site vor dem Zugriff durch anonyme Benutzer durch jcr-Inhalte und json zu schützen:

1. Wechseln Sie in der AEM-Autoreninstanz zu https://&lt;Host>:&lt;Port>/editor.html/content/site/&lt;sitename>.html.

   >[!NOTE]
   >
   >Gehen Sie nicht zur lokalisierten Site.

1. Gehen Sie zu **[!UICONTROL Seiteneigenschaften]**.

   ![page-properties-1](assets/page-properties-1.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Erweitert]**.
1. Enable **[!UICONTROL Authentication Requirement]**.

   ![site-authentication-1](assets/site-authentication-1.png)

1. Fügen Sie den Pfad der Anmeldeseite hinzu. Beispiel, `/content/......./GetStarted`.
1. Veröffentlichen Sie die Seite.

## Eingeschriebenes Mitglied {#enrolled-member}

Diese Erfahrung beruht darauf, dass Benutzer `Riley Taylor` und `Sidney Croft` durch ihre Mitgliedschaft in der [Community Ski Class](enablement-setup.md#publishcreateenablementmembers) -Gruppe [erstellt](resource.md#settings) und dem *Skilehrpfad* ** zugewiesenwerden.

Anmelden mit

* `Username: riley`
* `Password: password`

Wenn das Benutzerprofil nicht durch die Selbstregistrierung erstellt wurde, wird bei der ersten Anmeldung eines Mitglieds dessen Profilseite angezeigt, damit es überprüft und gegebenenfalls geändert werden kann.

Wenn sich das Mitglied das nächste Mal anmeldet, wird die durch das erste Menüelement identifizierte Homepage angezeigt.

![chlimage_1-434](assets/chlimage_1-434.png)

### Zuweisungen {#assignments}

Auf der Seite &quot;Zuweisungen&quot;werden dem Mitglied alle Lernpfade und Aktivierungsressourcen angezeigt, die ihm speziell zugewiesen wurden.

Jede Zuweisung bietet grundlegende Informationen zu

* Der Typ der Zuweisung
* Ob es sich um eine neue Zuweisung handelt
* Der Name
* Für die Art der Zuweisung relevante Details
* Aufgabenkontakt, Experte und Autor (falls vorhanden)

Der Zuweisungstyp wird durch ein Symbol in der oberen linken Ecke der Karte angezeigt. Das Bild einer Straße ist für einen Lernpfad mit der Anzahl der enthaltenen Aktivierungsressourcen gedacht.

![chlimage_1-435](assets/chlimage_1-435.png)

Wenn Sie *Skiunterricht* auswählen, werden die beiden Aktivierungsressourcen angezeigt, auf die der Lernpfad verweist.

![chlimage_1-436](assets/chlimage_1-436.png)

Wenn Sie *Skiunterricht 1* auswählen, wird die Seite mit den Details zur Aktivierung der Ressource geöffnet.

Auf der Seite &quot;Details&quot;kann das Mitglied lernen, die Lektion [bewerten](rating.md) und [Kommentare](comments.md)hinzufügen. Jede Mitgliederaktivität wird im Abschnitt Neue Funktionen der Site angezeigt.

Interaktionen mit der Aktivierungsressource werden im Abschnitt Bericht vermerkt, auf den in der Autorenumgebung zugegriffen werden kann.

![chlimage_1-437](assets/chlimage_1-437.png)

### Skikatalog {#ski-catalog}

Die Seite Skikatalog ist der Katalog der Aktivierungsressourcen, die mit Tags aus dem `Tutorial` Namespace getaggt sind. Die beiden *Ski-Lektionen* -Ressourcen sind mit dem `Skiing` Tag versehen, sodass, wenn keine anderen Tags ausgewählt `All` oder `Tutorial: Sports / Skiing` ausgewählt sind, nichts angezeigt wird.

Wenn einem Mitglied weder direkt noch über einen Lernpfad Ressourcen für die Aktivierung zugewiesen wurden, ist es möglich, mit den in einem Katalog befindlichen Ressourcen für die Aktivierung zu interagieren und Feedback über Kommentare und Bewertungen bereitzustellen.

![chlimage_1-438](assets/chlimage_1-438.png)

### Diskussionen {#discussions}

Neben der Bewertung und dem Kommentar zu ([wenn aktiviert](enablement-create-site.md#step33asettings)) Aktivierungsressourcen enthält die Community-Site-Vorlage, aus der `Enablement Tutorial` erstellt wurde, die [Forumsfunktion](functions.md#forum-function) (Titel ist `Discussions)`).

Wählen Sie den `Discussions`Link aus und veröffentlichen Sie ein Thema.

Melden Sie sich ab und melden Sie sich als Sidney Croft (Sidney / Passwort) an und beantworten Sie die Frage sowie Folgen Sie dem Thema.

Beachten Sie, dass es neben der Inline-Moderation Optionen gibt, das Thema in sozialen Medien freizugeben oder das Thema per E-Mail zu versenden.

![chlimage_1-439](assets/chlimage_1-439.png)

### Neuerungen {#what-s-new}

Der `What's New` Menüpunkt ist der Titel der [Aktivitätsstream-Funktion](functions.md#activity-stream-function) in der Struktur dieser Community-Site.

Wählen Sie den Link, über den die Aktivität angezeigt werden soll, und zwar noch als Sidney. `What's New`

![chlimage_1-440](assets/chlimage_1-440.png)

## Vertrauenswürdiger Community-Mitglied {#trusted-community-member}

Dieses Erlebnis setzt voraus, dass die Rollen des ` [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)`Moderators[ und des ](enablement-create-site.md#moderation)Ressourcenkontakts[](resource.md#settings) zugewiesen wurden.

Anmelden mit

* `Username: quinn`
* `Password: password`

Nach der Anmeldung wird ein neuer Menüpunkt angezeigt, `Administration`der angezeigt wird, weil dem Mitglied die Rolle des Moderators zugewiesen wurde.

![chlimage_1-441](assets/chlimage_1-441.png)

Die Homepage wird durch den ersten Menüpunkt Zuweisungen gekennzeichnet. Quinn ist der Ansprechpartner für Moderator- und Aktivierungsressourcen und wurde nicht in Aktivierungsressourcen oder Lernpfaden eingeschrieben. Es ist daher nichts anzuzeigen.

### Administration {#administration}

Da die Aktivitäten der beiden Lernenden aktiv sind `Riley Taylor` und der `Sidney Croft. By s`Link für den Zugriff auf die Moderationskonsole `Administration`ausgewählt wird, kann Quinn ihre Beiträge über die [Massenmoderationskonsole](moderation.md) moderieren.

Wenn Sie das Symbol für das Seitenbedienfeld auswählen, werden die Filter geöffnet, die zum Durchsuchen von Community-Inhalten verwendet werden.

Wenn Sie den Mauszeiger über eine Kommentarkarte bewegen, werden Moderationsaktionen angezeigt.

![chlimage_1-442](assets/chlimage_1-442.png)

## Berichte zum Autor {#reports-on-author}

Es gibt zwei Möglichkeiten, auf Berichte zu Lernenden und Aktivierungsressourcen zuzugreifen.

Navigieren Sie beim Autor zur **Communities, zur[Ressourcenkonsole](resources.md)**, in der die Aktivierungsressourcen verwaltet werden, und nach Auswahl einer Community-Site können Sie Berichte für

* Alle Aktivierungsressourcen und Lernpfade
* Eine spezifische Aktivierungsressource oder ein Lernpfad

Navigieren Sie zur **Communities-,[Reports-Konsole](reports.md)**und erstellen Sie Berichte gemäß

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

Bei etwas Aktivität und Interaktion mit den Ressourcen bei der Veröffentlichung lohnt es sich, die Berichte zum Autor anzuzeigen.

* Autor
* Anmelden mit Administratorrechten
* Navigieren Sie vom Hauptmenü zu **[!UICONTROL Communities > Ressourcen]**
* Wählen Sie die `Enablement Tutorial` Site
* Wählen Sie das `Report`Symbol für eine Zusammenfassung aller Ressourcen aus.
* Wählen Sie eine Ressource und dann das `Report`Symbol für einen Bericht zu dieser Ressource aus

Beachten Sie, dass es wahrscheinlich zu früh ist, Daten aus Adobe Analytics anzuzeigen, was bis zum Auftreten von Daten zwischen 1 und 12 Stunden dauern kann. Es stehen jedoch bereits grundlegende SCORM-Berichte zur Verfügung.

#### Bericht über die Ressourcen für Skifahrten {#ski-lessons-resource-report}

![chlimage_1-443](assets/chlimage_1-443.png)

#### Bericht &quot;Skilehrer&quot; {#ski-lessons-user-report}

* Wählen Sie **[!UICONTROL Communities > Ressourcen]**

* Karte öffnen `Enablement Tutorial`
* Karte öffnen `Ski Lessons`
* `select Report, User Report`

![chlimage_1-444](assets/chlimage_1-444.png)

### Berichte-Konsole {#reports-console}

Die Berichtskonsole ermöglicht die Erstellung von Berichten über

* **Zuweisungen** für eine beliebige Community-Site für eine Aktivierung
* **Ansichten** jeder Community-Site
* **Beiträge** für jede Community-Site

Für Zuweisungsberichte:

* Autor
* Anmelden mit Administratorrechten
* Navigieren Sie zu **[!UICONTROL Communities > Berichte > Zuweisungsbericht]**
* Wählen Sie eine **[!UICONTROL Site]** aus dem Pulldown-Menü (wählen Sie `Enablement Tutorial`)

* Gruppe **[!UICONTROL auswählen]** (auswählen `Community Ski Class`)

* Wählen Sie eine **[!UICONTROL Zuweisung]** aus (wählen Sie `Ski Lessons`)

* Wählen Sie **[!UICONTROL Generieren]**

![chlimage_1-445](assets/chlimage_1-445.png)

Für Berichte zu Ansichten:

* Autor
* Anmelden mit Administratorrechten
* Navigieren Sie zu **[!UICONTROL Communities > Berichte > Ansichtsbericht]**
* Wählen Sie eine **Site **aus dem Pulldown-Menü (wählen Sie`Enablement Tutorial`)

* Content- **[!UICONTROL Typ]** auswählen (wählen Sie `all`)

* Wählen Sie einen **[!UICONTROL Datumsbereich]** aus (wählen Sie `Last 7 days`)

* Wählen Sie **[!UICONTROL Generieren]**

![chlimage_1-446](assets/chlimage_1-446.png)

**[⇐ Erstellen und Zuweisen von Aktivierungsressourcen](resource.md)**
