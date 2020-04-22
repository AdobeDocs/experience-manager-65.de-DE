---
title: Community-Funktionen
seo-title: Community-Funktionen
description: Erfahren Sie, wie Sie auf die Community Functions-Konsole zugreifen.
seo-description: Erfahren Sie, wie Sie auf die Community Functions-Konsole zugreifen.
uuid: d3d70134-f318-4709-a673-b01a3467d980
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 91833914-b811-4355-a97d-e1a9cb7441f1
docset: aem65
translation-type: tm+mt
source-git-commit: 58a06c1a16c62bffad2893fbec0b32d2ce7267a7

---


# Community-Funktionen{#community-functions}

Die Art der Funktionen, die von einer Community-Erfahrung erwartet werden, sind bekannt. Community-Funktionen sind als Community-Funktionen verfügbar. Sie sind im Wesentlichen eine oder mehrere Seiten, die vorab verkabelt sind, um eine Community-Funktion zu implementieren, die mehr erfordert, als einfach eine Komponente zu einer Seite im Autorenmodus hinzuzufügen. Sie sind die Bausteine, mit denen die Struktur einer [Community-Site-Vorlage](/help/communities/sites.md) definiert wird, aus der Community-Sites [erstellt](/help/communities/sites-console.md)werden.

Nachdem eine Community-Site erstellt wurde, können den resultierenden Seiten Inhalte mithilfe des Standard- [AEM-Authoring-Modus](/help/sites-authoring/editing-content.md)hinzugefügt werden. Verschiedene Community-Funktionen stehen zur Verfügung, wie in der Community-Funktionkonsole zu sehen ist.

>[!NOTE]
>
>Die Konsolen zum Erstellen von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md)und [Community-Funktionen](/help/communities/functions.md) sind nur für die Verwendung in der Autoren-Umgebung vorgesehen.


## Community Functions Console {#community-functions-console}

In der Umgebung &quot;author&quot;zur Konsole der Community-Funktionen:

* Aus globaler Navigation: **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Community-Funktionen]**.

![chlimage_1-106](assets/chlimage_1-106.png)

## Vordefinierte Funktionen {#pre-built-functions}

Im Folgenden finden Sie eine kurze Beschreibung der Funktionen, die mit AEM Communities bereitgestellt werden. Jede Funktion umfasst eine oder mehrere AEM-Seiten, die Communities-Komponenten enthalten, die in eine Funktion verkettet sind, die leicht in eine [Community-Site-Vorlage](/help/communities/sites.md)integriert werden kann.

Eine Community-Site-Vorlage bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Profile, Benachrichtigungen, Nachrichten, Site-Menü, Suche, Themen und Branding-Funktionen.

### Titel- und URL-Einstellungen {#title-and-url-settings}

**Titel **und **URL **sind Eigenschaften, die allen Community-Funktionen gemein sind.

Wenn eine Community-Funktion zu einer Community-Site-Vorlage hinzugefügt oder hinzugefügt wird, wenn die Struktur einer Community-Site [geändert](/help/communities/sites-console.md#modifying-site-properties) wird, wird der Dialog der Funktion geöffnet, damit Titel und URL konfiguriert werden können.

#### Konfiguration der Funktionsdetails {#configuration-function-details}

![chlimage_1-107](assets/chlimage_1-107.png)

* **Titel**

   (*Erforderlich*) Der Text, der im Menü der Funktionen für die Site angezeigt wird

* **URL**

   (*Erforderlich*) Der Name, mit dem der URI generiert wird. Der Name muss den [Benennungskonventionen](/help/sites-developing/naming-conventions.md) von AEM und JCR entsprechen.

Verwenden Sie zum Beispiel die Site, die nach dem Tutorial [Erste](/help/communities/getting-started.md) Schritte erstellt wurde, wenn

* Titel = Webseite
* URL = Seite

Dann lautet die URL zur Seite https://localhost:4503/content/sites/engage/en/page.html

und der Menülink für die Seite wie folgt angezeigt wird:

![chlimage_1-108](assets/chlimage_1-108.png)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Die Stream-Funktion &quot;Aktivität&quot;ist eine Seite mit einer [Aktivität Streams-Komponente](/help/communities/activities.md) mit allen ausgewählten Ansichten (alle Aktivitäten, Aktivitäten und folgende). Siehe auch [Aktivität Stream Essentials](/help/communities/essentials-activities.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-1}

![chlimage_1-109](assets/chlimage_1-109.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Ansicht „Meine Aktivitäten“ anzeigen**

   Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basieren, die vom aktuellen Mitglied innerhalb der Community generiert wurden. Diese Option ist standardmäßig ausgewählt.

* **Ansicht „Alle Aktivitäten“ anzeigen**

   Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte mit allen Aktivitäten, die in der Community generiert wurden, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig ausgewählt.

* **Ansicht „News-Feed“ anzeigen**

   Wenn diese Option aktiviert ist, enthalten die Seiten &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basieren, die vom aktuellen Member ausgeführt werden. Diese Option ist standardmäßig ausgewählt.

### Zuweisungsfunktion {#assignments-function}

Die Zuweisungsfunktion ist die grundlegende Funktion, die eine [Community-Site für die Aktivierung](/help/communities/overview.md#enablement-community)definiert. Es ermöglicht die Zuweisung von Ressourcen zur Aktivierung an Community-Mitglieder. Siehe auch Grundlegende [Zuweisungen](/help/communities/essentials-assignments.md) für Entwickler.

Diese Funktion ist als Funktion des [Aktivierungs-Add-ons](/help/communities/enablement.md)verfügbar. Für das Aktivieren-Add-on sind zusätzliche Lizenzen für die Verwendung in einer Produktions-Umgebung erforderlich.

Wenn Sie einer Vorlage hinzugefügt werden, erfolgt die einzige Konfiguration für die [Titel- und URL-Einstellungen](#title-and-url-settings).

### Blogfunktion {#blog-function}

Die Blog-Funktion ist eine Seite mit einer [Blog-Komponente](/help/communities/blog-feature.md) , die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist. Siehe auch [Blog Essentials](/help/communities/blog-developer-basics.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-110](assets/chlimage_1-110.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem die Auswahl einer Gruppe [privilegierter Mitglieder](/help/communities/users.md#privileged-members-group)erlaubt wird. Wenn diese Option nicht ausgewählt ist, können alle Community-Mitglieder erstellen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder im Blog Dateien hochladen. Diese Option ist standardmäßig ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn nicht ausgewählt, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht zulässig. Diese Option ist standardmäßig ausgewählt.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, wird der Blog als [spezieller Inhalt](/help/communities/featured.md)identifiziert. Diese Option ist standardmäßig ausgewählt.

### Kalenderfunktion {#calendar-function}

Die Kalenderfunktion ist eine Seite mit einer [Kalenderkomponente](/help/communities/calendar.md) , die für das Tagging konfiguriert wurde. Siehe auch [Calendar Essentials](/help/communities/calendar-basics-for-developers.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-111](assets/chlimage_1-111.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare gebunden werden. Diese Option ist standardmäßig ausgewählt.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem die Auswahl einer Gruppe [privilegierter Mitglieder](/help/communities/users.md#privileged-members-group)erlaubt wird. Wenn diese Option nicht ausgewählt ist, können alle Community-Mitglieder erstellen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder im Blog Dateien hochladen. Diese Option ist standardmäßig ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn nicht ausgewählt, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht zulässig. Diese Option ist standardmäßig ausgewählt.

* **Feature-Inhalt zulassen**

   Bei Auswahl dieser Option wird der Inhalt als [spezieller Inhalt](/help/communities/featured.md)identifiziert. Diese Option ist standardmäßig ausgewählt.

### Katalogfunktion {#catalog-function}

Die Katalogfunktion ermöglicht es [Mitgliedern der Community](/help/communities/overview.md#enablement-community) , die Aktivierungsressourcen zu durchsuchen, die ihnen nicht zugewiesen sind. Siehe [Tagging-Aktivierungsressourcen](/help/communities/tag-resources.md) und [KatalogEssentials](/help/communities/catalog-developer-essentials.md) für Entwickler.

Alle Aktivierungsressourcen und Lernpfade für die Community-Site werden in allen Katalogen angezeigt, wenn deren Eigenschaft auf &quot;true&quot;gesetzt ` [Show in Catalog](/help/communities/resources.md)`ist. Um explizit Ressourcen und Lernpfade einzubeziehen, müssen Sie einen [Vorfilter](/help/communities/catalog-developer-essentials.md#pre-filters) auf den Katalog anwenden.

Wenn eine Vorlage hinzugefügt wird, ermöglicht die Konfiguration die Angabe von Tag-Namensräumen, die zum Konfigurieren des Tag-Filters verwendet werden, der den Site-Besuchern angezeigt wird:

![Katalogfunktion](assets/catalog-function.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Alle Namespaces auswählen**

   Die ausgewählten Tag-Namensraum definieren, welche Tags von Besuchern zum Filtern der Liste der im Katalog aufgelisteten Aktivierungsressourcen ausgewählt werden können.
Wenn diese Option aktiviert ist, sind alle für die Community-Site zulässigen Tag-Namensraum verfügbar.
Wenn diese Option deaktiviert ist, können Sie einen oder mehrere für die Community-Site zulässige Namensraum auswählen.
Diese Option ist standardmäßig ausgewählt.

### Funktion für spezielle Inhalte {#featured-content-function}

Die Funktion für speziellen Inhalt ist eine Seite mit einer Komponente [für](/help/communities/featured.md) speziellen Inhalt, die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Die Funktion zum Feature von Inhalten kann pro Komponente zugelassen oder deaktiviert werden (siehe [Blog-Funktion](#blog-function), [Kalenderfunktion](#calendar-function), [Forumsfunktion](#forum-function), [Ideenfunktion](#ideation-function)und [QnA-Funktion](#qna-function)).

Wenn Sie einer Vorlage hinzugefügt werden, erfolgt die einzige Konfiguration für die [Titel- und URL-Einstellungen](#title-and-url-settings).

### Dateibibliotheksfunktion {#file-library-function}

Die Dateibibliotheksfunktion ist eine Seite mit einer [Dateibibliothekskomponente](/help/communities/file-library.md) , die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Wenn Sie einer Vorlage hinzugefügt werden, erfolgt die einzige Konfiguration für die [Titel- und URL-Einstellungen](#title-and-url-settings).

### Forumsfunktion {#forum-function}

Die Forumsfunktion ist eine Seite mit einer [Forumkomponente](/help/communities/forum.md) , die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-2}

![chlimage_1-112](assets/chlimage_1-112.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare gebunden werden. Diese Option ist standardmäßig ausgewählt.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Mitgliedergruppe](/help/communities/users.md#privileged-members-group)erlaubt. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn sie nicht ausgewählt ist, erlaubt das Forum Kommentare zu einem Thema, aber Antworten auf diese Kommentare sind nicht zulässig. Diese Option ist standardmäßig ausgewählt.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, wird der Inhalt der Komponente als [speziellen Inhalt](/help/communities/featured.md)identifiziert. Diese Option ist standardmäßig ausgewählt.

### Gruppenfunktion {#groups-function}

>[!CAUTION]
>
>Die Funktion groups darf *nicht *die *erste oder einzige* Funktion in der Struktur einer Site oder in einer Community-Site-Vorlage sein.
>
>Jede andere Funktion, wie die [Seitenfunktion](#page-function), muss eingeschlossen und zuerst aufgeführt werden.


Die Gruppenfunktion bietet Community-Mitgliedern die Möglichkeit, Untergruppen auf der Community-Site in der Umgebung zum Veröffentlichen zu erstellen.

Je nach [Einstellungen](/help/communities/sites-console.md#groupmanagement) , wenn die Funktion &quot;Gruppen&quot;in einer [Community-Site-Vorlage](/help/communities/sites.md)enthalten ist, können die Gruppen öffentlich oder privat sein, und eine oder mehrere Community-Gruppenvorlagen können so konfiguriert werden, dass eine Auswahl von Vorlagen bereitgestellt wird, wenn die Community-Gruppe erstellt wird (z. B. aus der Umgebung &quot;Veröffentlichen&quot;). Eine [Community-Gruppenvorlage](/help/communities/tools-groups.md) gibt an, welche Communities-Funktionen für die Gruppenseiten erstellt werden, z. B. Foren und Kalender.

Wenn eine Community-Gruppe erstellt wird, wird eine Mitgliedsgruppe dynamisch für die neue Gruppe erstellt, der Mitglieder zugewiesen oder hinzugefügt werden können. For more information, see [Managing Users and User Groups](/help/communities/users.md).

Ab [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack)für Communities werden Community-Gruppen in der Autorengruppe mithilfe der Gruppenkonsole [der](/help/communities/groups.md)Communities-Sites erstellt und können in der Umgebung zum Veröffentlichen erstellt werden, wenn diese aktiviert ist.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![chlimage_1-113](assets/chlimage_1-113.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Gruppenvorlagen auswählen**

   Eine Dropdown-Liste, die die Auswahl einer oder mehrerer aktivierter Gruppenvorlagen ermöglicht, aus denen der künftige Ersteller einer neuen Community-Umgebung (in der Veröffentlichungsgruppe) wählen kann.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Sicherheitsgruppe](/help/communities/users.md#privileged-members-group)erlaubt. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Veröffentlichung der Kreation erlauben**

   Wenn diese Option aktiviert ist, können autorisierte Community-Mitglieder eine Gruppe in der Umgebung &quot;Veröffentlichen&quot;erstellen. Wenn diese Option deaktiviert ist, können neue Gruppen (Untergruppen) nur in der Umgebung &quot;Autor&quot;in der Konsole &quot;Communities Sites&quot;erstellt werden.
Diese Option ist standardmäßig ausgewählt.

### Ideen-Funktion {#ideation-function}

Die Ideationsfunktion ist eine Seite mit einer [Ideationskomponente](/help/communities/ideation-feature.md).

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem die standardmäßigen Titel- und URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt werden:

![chlimage_1-114](assets/chlimage_1-114.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, erlaubt das Forum nur privilegierten Mitgliedern, Themen zu posten, indem es die Auswahl einer [privilegierten Sicherheitsgruppe](/help/communities/users.md#privileged-members-group)erlaubt. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Diese Option ist standardmäßig ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option nicht ausgewählt ist, sind Antworten (Kommentare) auf ein Thema zulässig, Antworten auf Kommentare sind jedoch nicht zulässig. Diese Option ist standardmäßig ausgewählt.

* **Feature-Inhalt zulassen**

   Bei Auswahl dieser Option wird der Inhalt als [spezieller Inhalt](/help/communities/featured.md)identifiziert. Diese Option ist standardmäßig ausgewählt.

### Leaderboard-Funktion {#leaderboard-function}

Die Lederboard-Funktion ist eine Seite mit einer [Leaderboard-Komponente](/help/communities/enabling-leaderboard.md).

**HINWEIS**: Die Komponente Leaderboard muss weiter konfiguriert werden, *nachdem* eine Community-Site aus einer Community-Vorlage mit der Funktion Leaderboard erstellt wurde. Geben Sie die [Regeln](/help/communities/enabling-leaderboard.md#rules-tab)der Komponente &quot;Leaderboard&quot;an, die von der Konfiguration der [Bewertung und Abzeichen](/help/communities/implementing-scoring.md) für die Community-Site abhängen.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem die standardmäßigen Titel- und URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt werden:

![chlimage_1-115](assets/chlimage_1-115.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, wird eine Spalte für Symbole mit Zeichen in die Lederboard aufgenommen.
Die Option &quot;Standard&quot;ist deaktiviert.

* **Abzeichennamen anzeigen**

   Wenn diese Option aktiviert ist, wird eine Spalte für den Namen des Kennzeichens in der Leiste angezeigt.
Die Option &quot;Standard&quot;ist deaktiviert.

* **Avatar anzeigen**

   Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds neben dem Namen des Mitglieds mit dem Profil des Mitglieds verknüpft.
Die Option &quot;Standard&quot;ist deaktiviert.

### Seitenfunktion {#page-function}

Die Seitenfunktion fügt der Community-Site eine leere Seite hinzu, auf der sie in die Funktionen der Community-Site verdrahtet wird: Login, Menü, Benachrichtigungen, Messaging, Theming und Branding. Inhalte werden der Seite mithilfe des [Standard-AEM-Authoring-Modus](/help/sites-authoring/editing-content.md)hinzugefügt.

Wenn Sie einer Vorlage hinzugefügt werden, erfolgt die einzige Konfiguration für die [Titel- und URL-Einstellungen](#title-and-url-settings).

### Fragen/Antworten-Funktion {#qna-function}

Die QnA-Funktion ist eine Seite mit einer [QnA-Komponente](/help/communities/working-with-qna.md) , die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist.

Wenn eine Vorlage hinzugefügt wird, erlaubt die Konfiguration die Beschränkung auf privilegierte Mitglieder:

![chlimage_1-116](assets/chlimage_1-116.png)

* [Titel- und URL-Einstellungen](#title-and-url-settings)

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare gebunden werden. Diese Option ist standardmäßig ausgewählt.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, erlaubt das QnA-Forum nur privilegierten Mitgliedern, Fragen zu stellen, indem es die Auswahl einer [privilegierten Mitgliedergruppe](/help/communities/users.md#privileged-members-group)erlaubt. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge veröffentlichen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder im QnA-Forum Dateien hochladen. Diese Option ist standardmäßig ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn nicht ausgewählt, erlaubt das QnA-Forum Kommentare (Antworten) zu einer geposteten Frage, aber Antworten auf Antworten sind nicht erlaubt. Diese Option ist standardmäßig ausgewählt.

* **Feature-Inhalt zulassen**

   Bei Auswahl dieser Option wird der Inhalt als [spezieller Inhalt](/help/communities/featured.md)identifiziert. Diese Option ist standardmäßig ausgewählt.

## Community-Funktion erstellen {#create-community-function}

Die Möglichkeit, eine Community-Funktion zu erstellen, wird durch Auswahl des `Create Community Function` Symbols oben in der Community Functions-Konsole erreicht. Mehrere Funktionen, die auf demselben AEM-Blueprint basieren, können erstellt und dann durch Öffnen im Autorenbearbeitungsmodus eindeutig angepasst werden.

![chlimage_1-117](assets/chlimage_1-117.png)

### Name der Community-Funktion {#community-function-name}

![chlimage_1-118](assets/chlimage_1-118.png)

Im Bedienfeld &quot;Community-Funktionsname&quot;werden ein Name und eine Beschreibung sowie die Konfiguration der Funktion aktiviert oder deaktiviert:

* **Name der Community-Funktion**

   Der für die Anzeige und Datenspeicherung verwendete Funktionsname.

* **Community-Funktionsbeschreibung**

   Die Funktionsbeschreibung für die Anzeige.

* **Deaktiviert/aktiviert**

   Ein Umschalter, der steuert, ob die Funktion referenzierbar ist.

### AEM-Blueprint {#aem-blueprint}

![chlimage_1-119](assets/chlimage_1-119.png)

Auf dem `AEM Blueprint` Bedienfeld können Sie den Entwurf auswählen, der die zugrunde liegende Implementierung der Community-Funktion ist.

Die Community-Funktion ist eine Mini-Site, die eine oder mehrere Seiten umfasst, die vorab für die Einbindung in eine Community-Site verkabelt wurden, einschließlich Anmeldung, Profil, Benachrichtigungen, Nachrichten, Site-Menü, Suche, Themen und Branding-Funktionen. Nachdem die Funktion erstellt wurde, ist es möglich, die Funktion [im Autorenbearbeitungsmodus zu](#open-community-function) öffnen und die Seiten- oder Komponenteneinstellungen anzupassen.

Da die Community-Funktion als [Live-Kopie](/help/sites-administering/msm.md#live-copies) eines [Blueprints](/help/sites-administering/msm-livecopy.md#creatingablueprint)implementiert wird, ist es möglich, Änderungen an einer Funktion zu implementieren, die alle Community-Site-Seiten betreffen, die aus der [Community-Site-Vorlage](/help/communities/sites.md) oder [Community-Gruppenvorlage](/help/communities/tools-groups.md) , die die Funktion enthält, erstellt wurden. Es ist auch möglich, die Verknüpfung einer Seite mit dem übergeordneten Entwurf zu trennen, um Änderungen auf Seitenebene vorzunehmen.

Siehe auch [Multi-Site-Manager](/help/sites-administering/msm.md).

### Miniaturansicht   {#thumbnail}

![chlimage_1-120](assets/chlimage_1-120.png)

Im Bereich &quot;Miniaturansicht&quot;kann ein Bild hochgeladen werden, um es in der Konsole &quot; [Community-Funktionen&quot;anzuzeigen](#community-functions-console).

## Community-Funktion öffnen {#open-community-function}

![chlimage_1-121](assets/chlimage_1-121.png)

Wählen Sie das `Open Community Function` Symbol aus, um zum Authoring des Seiteninhalts und zum Ändern der Konfiguration der Funktionskomponente(n) in den Bearbeitungsmodus zu wechseln.

### Konfigurieren von Komponenten {#configuring-components}

Eine Community-Funktion wird als Live Copy eines AEM-Blueprints implementiert, dessen Details unter [Multi-Site-Manager](/help/sites-administering/msm.md)dokumentiert sind.

Es ist möglich, nicht nur Seiteninhalte zu erstellen, sondern Komponenten zu konfigurieren.

Wenn Sie eine Komponente auf einer Seite einer erstellten Community-Site konfigurieren, ist es ggf. erforderlich, die [Vererbung](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) abzubrechen, um die Komponente zu konfigurieren. Die Vererbung sollte nach Abschluss der Konfiguration wiederhergestellt werden.

Konfigurationsdetails finden Sie unter [Communities-Komponenten](/help/communities/author-communities.md) für Autoren.

## Community-Funktion bearbeiten {#edit-community-function}

![chlimage_1-122](assets/chlimage_1-122.png)

Wählen Sie das `Edit Community Function` Symbol aus, um die Eigenschaften der Funktion in denselben Bedienfeldern zu bearbeiten wie beim [Erstellen einer Community-Funktion](#create-community-function), einschließlich Aktivieren oder Deaktivieren der Funktion.
