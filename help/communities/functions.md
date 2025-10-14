---
title: Community-Funktionen
description: Erfahren Sie, wie Sie auf die Community-Funktionen zugreifen
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 2395c895-c611-43ac-abb6-c2bc4b4a41f4
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2215'
ht-degree: 2%

---

# Community-Funktionen{#community-functions}

Die von einem Community-Erlebnis erwarteten Funktionen sind bekannt. Community-Funktionen sind als Community-Funktionen verfügbar. Im Wesentlichen handelt es sich um eine oder mehrere Seiten, die vorkonfiguriert sind, um eine Community-Funktion zu implementieren, die mehr erfordert als nur das Hinzufügen einer Komponente zu einer Seite im Autorenmodus. Sie sind die Bausteine, die zum Definieren der Struktur einer [Community-Site-Vorlage](/help/communities/sites.md) verwendet werden, aus der Community-Sites [erstellt](/help/communities/sites-console.md).

Sobald eine Community-Site erstellt wurde, können den resultierenden Seiten mithilfe des standardmäßigen [AEM-Authoring-Modus Inhalte hinzugefügt &#x200B;](/help/sites-authoring/editing-content.md). In der Konsole „Community-Funktionen“ stehen verschiedene Community-Funktionen zur Verfügung.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur für die Autorenumgebung vorgesehen.

## Community-Funktionskonsole {#community-functions-console}

So gelangen Sie in der Autorenumgebung zur Community-Funktionskonsole:

* Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Community-Funktionen]**.

![Community-Funktionen](assets/community-functions.png)

## Vordefinierte Funktionen {#pre-built-functions}

Im Folgenden finden Sie eine kurze Beschreibung der Funktionen, die mit AEM Communities bereitgestellt werden. Jede Funktion enthält eine oder mehrere AEM-Seiten mit Communities-Komponenten, die zu einer Funktion zusammengefügt wurden, die einfach in eine [Community-Site-Vorlage“ integriert &#x200B;](/help/communities/sites.md) kann.

Eine Community-Site-Vorlage stellt die Struktur für eine Community-Site bereit, einschließlich Anmeldung, Benutzerprofilen, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

### Titel- und URL-Einstellungen {#title-and-url-settings}

**Title** und **URL** sind Eigenschaften, die für alle Community-Funktionen gelten.

Wenn eine Community-Funktion zu einer Community-Site-Vorlage hinzugefügt oder beim [&#x200B; (Ändern](/help/communities/sites-console.md#modifying-site-properties) der Struktur einer Community-Site hinzugefügt wird, wird das Dialogfeld der Funktion geöffnet, sodass der Titel und die URL konfiguriert werden können.

#### Konfiguration der Funktionsdetails {#configuration-function-details}

![title-url-details](assets/title-url-details.png)

* **Titel**

  (*Erforderlich*) Der Text, der im Menü mit den Funktionen für die Site angezeigt wird

* **URL**

  (*Erforderlich*) Der Name, der zum Generieren des URI verwendet wird. Der Name muss den [Namenskonventionen“ entsprechen](/help/sites-developing/naming-conventions.md) die von AEM und JCR vorgeschrieben sind.

Verwenden Sie beispielsweise die Site, die nach dem Tutorial [Erste Schritte](/help/communities/getting-started.md) erstellt wurde, wenn

* Titel = Webseite
* URL = Seite

Die URL zur Seite lautet dann https://localhost:4503/content/sites/engage/en/page.html

und der Menülink für die Seite wird wie folgt angezeigt:

![ENGAGE-PAGE](assets/engage-page.png)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Die Aktivitäts-Stream-Funktion ist eine Seite mit einer [Aktivitäts-Streams-Komponente](/help/communities/activities.md) auf der alle Ansichten ausgewählt sind (alle Aktivitäten, Benutzeraktivitäten und Folgendes). Siehe auch [Activity Stream Essentials](/help/communities/essentials-activities.md) für Entwickler.

Beim Hinzufügen zu einer Vorlage wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-1}

![function-details](assets/function-details.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Ansicht „Meine Aktivitäten“ anzeigen**

  Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten eine Registerkarte, auf der Aktivitäten anhand der Community-Inhalte gefiltert werden, die vom aktuellen Mitglied generiert wurden. Standard ist ausgewählt.

* **Ansicht „Alle Aktivitäten“ anzeigen**

  Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten eine Registerkarte mit allen Aktivitäten, die in der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Standard ist ausgewählt.

* **Ansicht „Nachrichten-Feed“ anzeigen**

  Wenn diese Option aktiviert ist, enthalten die Aktivitätsseiten eine Registerkarte, auf der die Aktivitäten nach den Aktivitäten des aktuellen Mitglieds gefiltert werden. Standard ist ausgewählt.

### Blogfunktion {#blog-function}

Die Blog-Funktion ist eine Seite mit einer [Blog-Komponente](/help/communities/blog-feature.md) die für Tagging, Datei-Uploads, Follower und Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist. Siehe auch [Blog Essentials](/help/communities/blog-developer-basics.md) für Entwickler.

Beim Hinzufügen zu einer Vorlage wird das folgende Dialogfeld geöffnet:

![blog-component](assets/blog-component.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, können im Blog nur privilegierte Mitglieder Artikel erstellen, indem eine [Gruppe privilegierter Mitglieder“ ausgewählt &#x200B;](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, können alle Community-Mitglieder erstellen. Die Auswahl von Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Standard ist ausgewählt.

* **Thread-Antworten zulassen**

  Wenn diese Option nicht ausgewählt ist, ermöglicht der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht erlaubt. Standard ist ausgewählt.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option ausgewählt ist, wird der Blog als [vorgestellter Inhalt“ &#x200B;](/help/communities/featured.md). Standard ist ausgewählt.

### Kalenderfunktion {#calendar-function}

Die Kalenderfunktion ist eine Seite mit einer [Kalenderkomponente](/help/communities/calendar.md) die für Tagging konfiguriert ist. Siehe auch [Calendar Essentials](/help/communities/calendar-basics-for-developers.md) für Entwickler.

Beim Hinzufügen zu einer Vorlage wird das folgende Dialogfeld geöffnet:

![calendar-details](assets/calendar-details.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Anheften zulassen**

  Wenn diese Option ausgewählt ist, können im Forum Themenantworten an den Anfang der Liste der Kommentare angeheftet werden. Standard ist ausgewählt.

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, können im Blog nur privilegierte Mitglieder Artikel erstellen, indem eine [Gruppe privilegierter Mitglieder“ ausgewählt &#x200B;](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, können alle Community-Mitglieder erstellen. Die Auswahl von Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Standard ist ausgewählt.

* **Thread-Antworten zulassen**

  Wenn diese Option nicht ausgewählt ist, ermöglicht der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht erlaubt. Standard ist ausgewählt.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option ausgewählt ist, wird der Inhalt als [vorgestellter Inhalt“ &#x200B;](/help/communities/featured.md). Standard ist ausgewählt.

### Vorgestellte Inhaltsfunktion {#featured-content-function}

Die Funktion für vorgestellte Inhalte ist eine Seite mit einer [Komponente für vorgestellte Inhalte](/help/communities/featured.md) die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Die Funktion zum Anzeigen von Inhalten kann pro Komponente zulässig oder nicht zulässig sein (siehe [Blog-Funktion](#blog-function), [Kalenderfunktion](#calendar-function), [Forumsfunktion](#forum-function), [Ideationsfunktion](#ideation-function) und [QnA-Funktion](#qna-function)).

Wenn sie zu einer Vorlage hinzugefügt werden, ist die einzige Konfiguration für die [Titel- und URL-Einstellungen](#title-and-url-settings).

### Dateibibliotheksfunktion {#file-library-function}

Die Dateibibliotheksfunktion ist eine Seite mit einer [Dateibibliothekskomponente](/help/communities/file-library.md), die das Hinzufügen und Löschen von Kommentaren ermöglicht.

Wenn sie zu einer Vorlage hinzugefügt werden, ist die einzige Konfiguration für die [Titel- und URL-Einstellungen](#title-and-url-settings).

### Forumsfunktion {#forum-function}

Die Forenfunktion ist eine Seite mit einer [Forenkomponente](/help/communities/forum.md) die für Tagging, Datei-Uploads, Follower und Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist.

Beim Hinzufügen zu einer Vorlage wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-2}

![forum-component1](assets/forum-component1.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Anheften zulassen**

  Wenn diese Option ausgewählt ist, können im Forum Themenantworten an den Anfang der Liste der Kommentare angeheftet werden. Standard ist ausgewählt.

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem die Auswahl einer [privilegierten Mitgliedergruppe“ &#x200B;](/help/communities/users.md#privileged-members-group) wird. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Auswahl von Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder im Forum Dateien hochladen. Standard ist ausgewählt.

* **Thread-Antworten zulassen**

  Wenn diese Option nicht ausgewählt ist, ermöglicht das Forum Kommentare zu einem Thema, aber Antworten auf diese Kommentare sind nicht zulässig. Standard ist ausgewählt.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option aktiviert ist, wird der Inhalt der Komponente als [vorgestellter Inhalt“ &#x200B;](/help/communities/featured.md). Standard ist ausgewählt.

### group-Funktion {#groups-function}

>[!CAUTION]
>
>Die Gruppenfunktion darf *nicht* die *erste oder einzige* Funktion in der Struktur einer Site oder in einer Community-Site-Vorlage sein.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](#page-function), muss eingeschlossen und zuerst aufgeführt werden.

Die Funktion „Gruppen“ bietet den Community-Mitgliedern die Möglichkeit, innerhalb der Community-Site in der Veröffentlichungsumgebung Untergruppen zu erstellen.

Je nach [Einstellungen](/help/communities/sites-console.md#groupmanagement) wenn die Funktion Gruppen in einer [Community-Site-Vorlage](/help/communities/sites.md) enthalten ist, können die Gruppen öffentlich oder privat sein und eine oder mehrere Community-Gruppenvorlagen können so konfiguriert werden, dass sie eine Auswahl von Vorlagen bereitstellen, wenn die Community-Gruppe tatsächlich erstellt wird (z. B. aus der Veröffentlichungsumgebung). Eine [Community-Gruppenvorlage](/help/communities/tools-groups.md) gibt an, welche Communities-Funktionen für die Gruppenseiten wie Foren und Kalender erstellt werden.

Wenn eine Community-Gruppe erstellt wird, wird dynamisch eine Mitgliedergruppe für die neue Gruppe erstellt, der Mitglieder zugewiesen oder hinzugefügt werden können. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

Ab Communities [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack) werden Community-Gruppen in der Autorenumgebung mithilfe der [Communities Sites&#39; Groups-Konsole &#x200B;](/help/communities/groups.md) und können bei Aktivierung in der Veröffentlichungsumgebung erstellt werden.

Beim Hinzufügen zu einer Vorlage wird das folgende Dialogfeld geöffnet:

![group-template-config](assets/group-template-config.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Gruppenvorlagen auswählen**

  Eine Dropdown-Liste, die die Auswahl einer oder mehrerer aktivierter Gruppenvorlagen ermöglicht, aus denen der zukünftige Ersteller einer neuen Community-Gruppe (in der Veröffentlichungsumgebung) wählen kann.

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Mitglieder - Sicherheitsgruppe](/help/communities/users.md#privileged-members-group) erlaubt. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Auswahl von Standard ist deaktiviert.

* **Publish-Erstellung zulassen**

  Wenn diese Option aktiviert ist, können autorisierte Community-Mitglieder in der Veröffentlichungsumgebung eine Gruppe erstellen. Wenn diese Option deaktiviert ist, können neue Gruppen (Untergruppen) nur in der Autorenumgebung über die Konsole „Sites-Gruppen“ der Communities-Sites erstellt werden.
Standard ist ausgewählt.

### Ideen-Funktion {#ideation-function}

Die Ideationsfunktion ist eine Seite mit einer [Ideationskomponente](/help/communities/ideation-feature.md).

Wenn sie zu einer Vorlage hinzugefügt werden, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die Standardanzeigeeinstellungen für die Vorlage angegeben werden:

![ideation-function](assets/ideation-function.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Mitglieder - Sicherheitsgruppe](/help/communities/users.md#privileged-members-group) erlaubt. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Auswahl von Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option ausgewählt ist, bietet die Idee Mitgliedern die Möglichkeit, Dateien hochzuladen. Standard ist ausgewählt.

* **Thread-Antworten zulassen**

  Wenn diese Option nicht ausgewählt ist, ermöglicht die Idee Antworten (Kommentare) auf ein Thema, aber Antworten auf Kommentare sind nicht zulässig. Standard ist ausgewählt.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option ausgewählt ist, wird der Inhalt als [vorgestellter Inhalt“ &#x200B;](/help/communities/featured.md). Standard ist ausgewählt.

### Leaderboard-Funktion {#leaderboard-function}

Die Leaderboard-Funktion ist eine Seite mit einer [Leaderboard-Komponente](/help/communities/enabling-leaderboard.md).

**HINWEIS**: Die Leaderboard-Komponente muss weiter konfiguriert werden *nachdem* Community-Site aus einer Community-Vorlage erstellt wurde, die die Leaderboard-Funktion enthält. Geben Sie die [&#x200B; der Leaderboard-Komponente an](/help/communities/enabling-leaderboard.md#rules-tab) die von der Konfiguration [Bewertung und Abzeichen](/help/communities/implementing-scoring.md) für die Community-Site abhängen.

Wenn sie zu einer Vorlage hinzugefügt werden, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die Standardanzeigeeinstellungen für die Vorlage angegeben werden:

![leaderboard-dialog](assets/leaderboard-dialog.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Badge anzeigen**

  Wenn diese Option aktiviert ist, wird eine Spalte für Abzeichen-Symbole in der Leaderboard eingefügt.
Die Auswahl von Standard ist deaktiviert.

* **Badge-Name anzeigen**

  Wenn diese Option aktiviert ist, wird eine Spalte für den Badge-Namen in der Leaderboard-Liste angezeigt.
Die Auswahl von Standard ist deaktiviert.

* **Avatar anzeigen**

  Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds in der Rangliste neben dem Namen des Mitglieds und dem Link zu seinem Mitgliederprofil angezeigt.
Die Auswahl von Standard ist deaktiviert.

### Seitenfunktion {#page-function}

Die Seitenfunktion fügt der Community-Site eine leere Seite hinzu, die mit den Funktionen der Community-Site verkabelt ist: Anmeldung, Menü, Benachrichtigungen, Messaging, Design und Branding. Inhalte werden der Seite mit dem [standardmäßigen AEM-Authoring-Modus](/help/sites-authoring/editing-content.md) hinzugefügt.

Wenn sie zu einer Vorlage hinzugefügt werden, ist die einzige Konfiguration für die [Titel- und URL-Einstellungen](#title-and-url-settings).

### Fragen/Antworten-Funktion {#qna-function}

Die QnA-Funktion ist eine Seite mit einer [QnA-Komponente](/help/communities/working-with-qna.md) die für das Tagging, Datei-Uploads, die Nachverfolgung und die Selbstbearbeitung, Abstimmung und Moderation von Mitgliedern konfiguriert ist.

Wenn sie zu einer Vorlage hinzugefügt werden, ermöglicht die Konfiguration die Beschränkung auf privilegierte Mitglieder:

![qna-dialog](assets/qna-dialog.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Anheften zulassen**

  Wenn diese Option ausgewählt ist, können im Forum Themenantworten an den Anfang der Liste der Kommentare angeheftet werden. Standard ist ausgewählt.

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option ausgewählt ist, erlaubt das QnA-Forum nur privilegierten Mitgliedern, Fragen zu stellen, indem die Auswahl einer [privilegierten Mitgliedergruppe“ &#x200B;](/help/communities/users.md#privileged-members-group) wird. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Auswahl von Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option ausgewählt ist, bietet das QnA-Forum Mitgliedern die Möglichkeit, Dateien hochzuladen. Standard ist ausgewählt.

* **Thread-Antworten zulassen**

  Wenn diese Option nicht ausgewählt ist, ermöglicht das QnA-Forum Kommentare (Antworten) zu einer geposteten Frage, Antworten auf Antworten sind jedoch nicht zulässig. Standard ist ausgewählt.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option ausgewählt ist, wird der Inhalt als [vorgestellter Inhalt“ &#x200B;](/help/communities/featured.md). Standard ist ausgewählt.

## Community-Funktion erstellen {#create-community-function}

Sie können eine Community-Funktion erstellen, indem Sie oben in der Konsole „Community-Funktionen“ auf das `Create Community Function` klicken. Es können mehrere auf derselben AEM-Blueprint basierende Funktionen erstellt und dann durch Öffnen im Authoring-Bearbeitungsmodus individuell angepasst werden.

![create-community-function](assets/create-community-function.png)

### Name der Community-Funktion {#community-function-name}

![function-name](assets/function-name.png)

Im Bedienfeld Community-Funktionsname werden ein Name, eine Beschreibung und Angaben dazu konfiguriert, ob die Funktion aktiviert oder deaktiviert ist:

* **Community-Funktionsname**

  Der Funktionsname, der für die Anzeige und Speicherung verwendet wird.

* **Beschreibung der Community-Funktion**

  Die Funktionsbeschreibung für die Anzeige.

* **Deaktiviert/Aktiviert**

  Ein Umschalter, der steuert, ob die Funktion referenzierbar ist.

### AEM-Blueprint {#aem-blueprint}

![aem-blueprint](assets/aem-blueprint.png)

Im `AEM Blueprint` Panel kann der Blueprint ausgewählt werden, der der Implementierung der Community-Funktion zugrunde liegt.

Die Community-Funktion ist eine Mini-Site mit einer oder mehreren Seiten, die vorab für die Aufnahme auf einer Community-Site ausgelegt sind, einschließlich Anmeldung, Benutzerprofilen, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen. Nachdem die Funktion erstellt wurde, können Sie [Funktion öffnen](#open-community-function) im Autorenbearbeitungsmodus die Seiten- oder Komponenteneinstellungen anpassen.

Da die Community-Funktion als [Live Copy](/help/sites-administering/msm.md#live-copies) einer [Blueprint](/help/sites-administering/msm-livecopy.md#creatingablueprint) implementiert ist, ist es möglich, Änderungen an einer Funktion vorzunehmen, die sich auf alle Community-Site-Seiten auswirkt, die aus der [Community-Site-Vorlage](/help/communities/sites.md) oder [Community-Gruppenvorlage](/help/communities/tools-groups.md) erstellt wurden, die die Funktion enthielt. Es ist auch möglich, eine Seite von der übergeordneten Blueprint zu trennen, um Änderungen auf Seitenebene vorzunehmen.

Siehe auch [Multi Site Manager](/help/sites-administering/msm.md).

### Miniaturansicht {#thumbnail}

![function-thumbnail](assets/funtion-thumbnail.png)

Im Bedienfeld „Miniaturansicht“ kann ein Bild hochgeladen werden, um es in der [Community-Funktionskonsole“ &#x200B;](#community-functions-console).

## Community-Funktion öffnen {#open-community-function}

![open-function](assets/open-function.png)

Wählen Sie das Symbol `Open Community Function` aus, um in den Bearbeitungsmodus für Autoren zu wechseln und den Seiteninhalt zu verfassen und die Konfiguration der Funktionskomponenten zu ändern.

### Konfigurieren von Komponenten {#configuring-components}

Eine Community-Funktion wird als Live Copy eines AEM-Blueprints implementiert, dessen Details unter [Multi-Site-Manager](/help/sites-administering/msm.md) dokumentiert sind.

Es ist möglich, nicht nur Seiteninhalte zu erstellen, sondern Komponenten zu konfigurieren.

Wenn Sie eine Komponente auf einer Seite einer erstellten Community-Site konfigurieren, kann es erforderlich sein, die [Vererbung“ abzubrechen](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) um die Komponente zu konfigurieren. Die Vererbung sollte nach Abschluss der Konfiguration wiederhergestellt werden.

Konfigurationsdetails finden Sie unter [Communities-Komponenten](/help/communities/author-communities.md) für Autoren.

## Community-Funktion bearbeiten {#edit-community-function}

![edit-function](assets/edit-function.png)

Wählen Sie das Symbol `Edit Community Function` aus, um die Eigenschaften der Funktion zu bearbeiten, indem Sie dieselben Bedienfelder verwenden wie [Community-Funktion erstellen](#create-community-function) einschließlich der Aktivierung oder Deaktivierung der Funktion.
