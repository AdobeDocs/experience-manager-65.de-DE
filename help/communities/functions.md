---
title: Community-Funktionen
description: Erfahren Sie, wie Sie auf die Konsole "Community-Funktionen"zugreifen
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

Die Art der Funktionen, die von einem Community-Erlebnis erwartet werden, ist bekannt. Community-Funktionen sind als Community-Funktionen verfügbar. Im Grunde sind es eine oder mehrere Seiten, die vorab mit dem Netzwerk verbunden sind, um eine Community-Funktion zu implementieren, die mehr erfordert, als einfach eine Komponente zu einer Seite im Autorenmodus hinzuzufügen. Sie sind die Bausteine, mit denen die Struktur einer [Community-Site-Vorlage](/help/communities/sites.md) definiert wird, aus der Community-Sites [erstellt wurden](/help/communities/sites-console.md).

Nachdem eine Community-Site erstellt wurde, kann den resultierenden Seiten mithilfe des standardmäßigen [AEM Authoring-Modus](/help/sites-authoring/editing-content.md) Inhalt hinzugefügt werden. In der Konsole Community-Funktionen sind verschiedene Community-Funktionen verfügbar.

>[!NOTE]
>
>Die Konsolen zum Erstellen von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Community-Funktionskonsole {#community-functions-console}

So rufen Sie die Konsole für Community-Funktionen in der Autorenumgebung auf:

* Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Community-Funktionen]**.

![community-function](assets/community-functions.png)

## Vordefinierte Funktionen {#pre-built-functions}

Im Folgenden finden Sie eine kurze Beschreibung der Funktionen, die mit AEM Communities bereitgestellt werden. Jede Funktion enthält eine oder mehrere AEM Seiten, die Communities-Komponenten enthalten, die mit einer Funktion verbunden sind, die einfach in eine [Community-Site-Vorlage](/help/communities/sites.md) integriert werden kann.

Eine Community-Site-Vorlage bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerprofile, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

### Titel und URL-Einstellungen {#title-and-url-settings}

**Titel** und **URL** sind Eigenschaften, die allen Community-Funktionen gemein sind.

Wenn eine Community-Funktion zu einer Community-Site-Vorlage hinzugefügt oder hinzugefügt wird, wenn [die Struktur einer Community-Site ändert](/help/communities/sites-console.md#modifying-site-properties), wird das Dialogfeld der Funktion geöffnet, sodass Titel und URL konfiguriert werden können.

#### Konfiguration der Funktionsdetails {#configuration-function-details}

![title-url-details](assets/title-url-details.png)

* **Titel**

  (*Erforderlich*) Der Text, der im Menü der Funktionen für die Site angezeigt wird

* **URL**

  (*Erforderlich*) Der Name, mit dem der URI generiert wird. Der Name muss den von AEM und JCR festgelegten [Benennungskonventionen](/help/sites-developing/naming-conventions.md) entsprechen.

Wenn Sie beispielsweise die Site verwenden, die anhand des Tutorials [Erste Schritte](/help/communities/getting-started.md) erstellt wurde,

* Titel = Webseite
* URL = Seite

Dann lautet die URL zur Seite https://localhost:4503/content/sites/engage/en/page.html

und der Menülink für die Seite wie folgt angezeigt wird:

![engage-page](assets/engage-page.png)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Die Aktivitäts-Stream-Funktion ist eine Seite mit der Komponente [Aktivitäts-Streams](/help/communities/activities.md) mit allen ausgewählten Ansichten (alle Aktivitäten, Benutzeraktivitäten und Folgeaktivitäten). Siehe auch [Aktivitäts-Stream-Grundlagen](/help/communities/essentials-activities.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-1}

![function-details](assets/function-details.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Ansicht &quot;Meine Aktivitäten&quot;** anzeigen

  Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten eine Registerkarte, auf der Aktivitäten basierend auf denen gefiltert werden, die innerhalb der Community vom aktuellen Mitglied generiert wurden. Die Option Standard ist ausgewählt.

* **Ansicht &quot;Alle Aktivitäten&quot;anzeigen**

  Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten einen Tab, der alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Die Option Standard ist ausgewählt.

* **Ansicht &quot;News Feed&quot;anzeigen**

  Wenn diese Option aktiviert ist, enthalten die Aktivitätsseiten eine Registerkarte, auf der Aktivitäten nach denen gefiltert werden, denen das aktuelle Mitglied folgt. Die Option Standard ist ausgewählt.

### Blogfunktion {#blog-function}

Die Blog-Funktion ist eine Seite mit einer [Blog-Komponente](/help/communities/blog-feature.md), die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist. Siehe auch [Blog-Grundlagen](/help/communities/blog-developer-basics.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![blog-component](assets/blog-component.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem er die Auswahl einer [privilegierten Mitgliedergruppe](/help/communities/users.md#privileged-members-group) ermöglicht. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder erstellen. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Dateien im Blog hochladen. Die Option Standard ist ausgewählt.

* **Ermöglichen von gefilterten Antworten**

  Wenn diese Option nicht ausgewählt ist, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht zulässig. Die Option Standard ist ausgewählt.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, wird der Blog als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert. Die Option Standard ist ausgewählt.

### Kalenderfunktion {#calendar-function}

Die Kalenderfunktion ist eine Seite mit einer [Kalenderkomponente](/help/communities/calendar.md), die für das Tagging konfiguriert ist. Siehe auch [Kalendergrundlagen](/help/communities/calendar-basics-for-developers.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![calendar-details](assets/calendar-details.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Ping zulassen**

  Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare eingefügt werden. Die Option Standard ist ausgewählt.

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, erlaubt der Blog nur privilegierten Mitgliedern, Artikel zu erstellen, indem er die Auswahl einer [privilegierten Mitgliedergruppe](/help/communities/users.md#privileged-members-group) ermöglicht. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder erstellen. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Dateien im Blog hochladen. Die Option Standard ist ausgewählt.

* **Ermöglichen von gefilterten Antworten**

  Wenn diese Option nicht ausgewählt ist, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht zulässig. Die Option Standard ist ausgewählt.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, wird der Inhalt als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert. Die Option Standard ist ausgewählt.

### Funktion für spezielle Inhalte {#featured-content-function}

Die Funktion für speziellen Inhalt ist eine Seite mit der Komponente [Vorgestellter Inhalt](/help/communities/featured.md) , die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Die Möglichkeit, Inhalt zu verwenden, kann pro Komponente erlaubt oder untersagt sein (siehe [Blog-Funktion](#blog-function), [Kalenderfunktion](#calendar-function), [Forumsfunktion](#forum-function), [Ideenfunktion](#ideation-function) und [QnA-Funktion](#qna-function)).

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für den [Titel und URL-Einstellungen](#title-and-url-settings).

### Dateibibliotheksfunktion {#file-library-function}

Die Dateibibliotheksfunktion ist eine Seite mit einer [Dateibibliothekskomponente](/help/communities/file-library.md), die so konfiguriert ist, dass Kommentare hinzugefügt und gelöscht werden können.

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für den [Titel und URL-Einstellungen](#title-and-url-settings).

### Forumsfunktion {#forum-function}

Die Forumsfunktion ist eine Seite mit einer [Forumkomponente](/help/communities/forum.md), die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-2}

![forum-component1](assets/forum-component1.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Ping zulassen**

  Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare eingefügt werden. Die Option Standard ist ausgewählt.

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, dürfen privilegierte Mitglieder nur Themen posten, indem sie die Auswahl einer [privilegierten Mitgliedergruppe](/help/communities/users.md#privileged-members-group) ermöglichen. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Die Option Standard ist ausgewählt.

* **Ermöglichen von gefilterten Antworten**

  Wenn diese Option nicht ausgewählt ist, sind im Forum Kommentare zu einem Thema zulässig, Antworten auf diese Kommentare sind jedoch nicht zulässig. Die Option Standard ist ausgewählt.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, wird der Inhalt der Komponente als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert. Die Option Standard ist ausgewählt.

### Gruppenfunktion {#groups-function}

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;darf *nicht* die Funktion &quot;*first&quot;und nicht die einzige Funktion &quot;*&quot;in der Struktur einer Site oder in einer Community-Site-Vorlage sein.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](#page-function), muss zuerst eingeschlossen und aufgeführt werden.

Die Funktion &quot;Gruppen&quot;bietet Community-Mitgliedern die Möglichkeit, Untergruppen innerhalb der Community-Site in der Veröffentlichungsumgebung zu erstellen.

Je nach [Einstellungen](/help/communities/sites-console.md#groupmanagement) , wenn die Funktion &quot;Gruppen&quot;in einer [Community-Site-Vorlage](/help/communities/sites.md) enthalten ist, können die Gruppen öffentlich oder privat sein und eine oder mehrere Community-Gruppenvorlagen können so konfiguriert werden, dass sie eine Auswahl von Vorlagen bereitstellen, wenn die Community-Gruppe tatsächlich erstellt wird (z. B. in der Veröffentlichungsumgebung). Eine [Community-Gruppenvorlage](/help/communities/tools-groups.md) gibt an, welche Communities-Funktionen für die Gruppenseiten erstellt werden, z. B. Foren und Kalender.

Wenn eine Community-Gruppe erstellt wird, wird eine Mitgliedergruppe für die neue Gruppe dynamisch erstellt, der Mitglieder zugewiesen oder hinzugefügt werden können. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

Ab Communities [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack) werden Community-Gruppen in der Autorenumgebung mithilfe der [Gruppenkonsole der Communities-Sites](/help/communities/groups.md) erstellt und können bei Aktivierung in der Veröffentlichungsumgebung erstellt werden.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![group-template-config](assets/group-template-config.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Gruppenvorlagen auswählen**

  Eine Dropdown-Liste, die die Auswahl einer oder mehrerer aktivierter Gruppenvorlagen ermöglicht, aus denen der künftige Ersteller einer neuen Community-Gruppe (in der Veröffentlichungsumgebung) wählen kann.

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, dürfen privilegierte Mitglieder nur Themen posten, indem sie die Auswahl einer Sicherheitsgruppe mit [berechtigten Mitgliedern](/help/communities/users.md#privileged-members-group) ermöglichen. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Publish-Erstellung zulassen**

  Sofern ausgewählt, können autorisierte Community-Mitglieder eine Gruppe in der Veröffentlichungsumgebung erstellen. Wenn diese Option deaktiviert ist, können neue Gruppen (Untergruppen) nur in der Autorenumgebung über die Gruppenkonsole der Communities-Sites erstellt werden.
Die Option Standard ist ausgewählt.

### Ideen-Funktion {#ideation-function}

Die Ideenfunktion ist eine Seite mit einer [Ideationskomponente](/help/communities/ideation-feature.md).

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage angegeben sind:

![ideation-function](assets/ideation-function.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, dürfen privilegierte Mitglieder nur Themen posten, indem sie die Auswahl einer Sicherheitsgruppe mit [berechtigten Mitgliedern](/help/communities/users.md#privileged-members-group) ermöglichen. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Die Option Standard ist ausgewählt.

* **Ermöglichen von gefilterten Antworten**

  Wenn diese Option nicht ausgewählt ist, sind Antworten (Kommentare) auf ein Thema zulässig, Antworten auf Kommentare sind jedoch nicht zulässig. Die Option Standard ist ausgewählt.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, wird der Inhalt als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert. Die Option Standard ist ausgewählt.

### Leaderboard-Funktion {#leaderboard-function}

Die Leaderboard-Funktion ist eine Seite mit einer [Leaderboard-Komponente](/help/communities/enabling-leaderboard.md).

**HINWEIS**: Die Leaderboard-Komponente muss weiter konfiguriert werden *nach*. Eine Community-Site wird aus einer Community-Vorlage erstellt, die die Leaderboard-Funktion enthält. Geben Sie die [Regeln](/help/communities/enabling-leaderboard.md#rules-tab) der Leaderboard-Komponente an, die von der Konfiguration von [Scoring und Badges](/help/communities/implementing-scoring.md) für die Community-Site abhängen.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage angegeben sind:

![Leaderboard-dialog](assets/leaderboard-dialog.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Anzeigemarke**

  Wenn diese Option aktiviert ist, wird eine Spalte für Badge-Symbole in die Leaderboard eingefügt.
Die Option Standard ist deaktiviert.

* **Anzeigename**

  Wenn diese Option aktiviert ist, wird eine Spalte für den Badge-Namen in die Leaderboard eingefügt.
Die Option Standard ist deaktiviert.

* **Avatar anzeigen**

  Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds in das Leaderboard eingefügt, neben dem Namen des Mitglieds, der mit seinem Mitgliederprofil verknüpft ist.
Die Option Standard ist deaktiviert.

### Seitenfunktion {#page-function}

Die Seitenfunktion fügt der Community-Site eine leere Seite hinzu, die in die Funktionen der Community-Site eingebunden ist: Anmeldung, Menü, Benachrichtigungen, Messaging, Themen und Branding. Der Inhalt wird der Seite mit dem [standardmäßigen AEM Authoring-Modus](/help/sites-authoring/editing-content.md) hinzugefügt.

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für den [Titel und URL-Einstellungen](#title-and-url-settings).

### Fragen/Antworten-Funktion {#qna-function}

Die QnA-Funktion ist eine Seite mit einer [QnA-Komponente](/help/communities/working-with-qna.md), die für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation konfiguriert ist.

Wenn sie einer Vorlage hinzugefügt wird, ermöglicht die Konfiguration die Beschränkung auf privilegierte Mitglieder:

![qna-dialog](assets/qna-dialog.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Ping zulassen**

  Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare eingefügt werden. Die Option Standard ist ausgewählt.

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, dürfen privilegierte Mitglieder nur Fragen posten, indem sie die Auswahl einer [privilegierten Mitgliedergruppe](/help/communities/users.md#privileged-members-group) ermöglichen. Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Die Option Standard ist ausgewählt.

* **Ermöglichen von gefilterten Antworten**

  Wenn diese Option nicht ausgewählt ist, können im Forum Kommentare (Antworten) zu einer geposteten Frage eingesehen werden. Antworten auf Antworten sind jedoch nicht zulässig. Die Option Standard ist ausgewählt.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, wird der Inhalt als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert. Die Option Standard ist ausgewählt.

## Community-Funktion erstellen {#create-community-function}

Die Möglichkeit, eine Community-Funktion zu erstellen, wird durch die Auswahl des Symbols `Create Community Function` oben in der Community-Funktionskonsole erreicht. Mehrere Funktionen, die auf demselben AEM Blueprint basieren, können erstellt und dann durch Öffnen im Bearbeitungsmodus des Autors eindeutig angepasst werden.

![create-community-function](assets/create-community-function.png)

### Name der Community-Funktion {#community-function-name}

![function-name](assets/function-name.png)

Im Bereich &quot;Community Function Name&quot;werden ein Name, eine Beschreibung und ob die Funktion aktiviert oder deaktiviert ist konfiguriert:

* **Community-Funktionsname**

  Der Funktionsname, der für die Anzeige und Speicherung verwendet wird.

* **Beschreibung der Community-Funktion**

  Die Funktionsbeschreibung für die Anzeige.

* **Deaktiviert/Aktiviert**

  Ein Umschalter steuert, ob die Funktion referenzierbar ist.

### AEM-Blueprint {#aem-blueprint}

![aem-blueprint](assets/aem-blueprint.png)

Im Bedienfeld `AEM Blueprint` können Sie den Blueprint auswählen, der der zugrunde liegenden Implementierung der Community-Funktion entspricht.

Die Community-Funktion ist eine Mini-Site, die eine oder mehrere Seiten enthält und vorab für die Integration in eine Community-Site kabelgebunden ist, einschließlich Anmeldung, Benutzerprofile, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen. Nachdem die Funktion erstellt wurde, ist es möglich, die Funktion ](#open-community-function) im Bearbeitungsmodus des Autors zu öffnen und die Seiten- oder Komponenteneinstellungen anzupassen.[

Da die Community-Funktion als [Live Copy](/help/sites-administering/msm.md#live-copies) eines [Blueprint](/help/sites-administering/msm-livecopy.md#creatingablueprint) implementiert ist, ist es möglich, Änderungen an einer Funktion zu implementieren, die sich auf alle Community-Site-Seiten auswirken, die aus der [Community-Site-Vorlage](/help/communities/sites.md) oder der [Community-Gruppenvorlage](/help/communities/tools-groups.md) erstellt wurden, die die Funktion enthielt. Es ist auch möglich, die Zuordnung einer Seite zu ihrem übergeordneten Blueprint zu trennen, um Änderungen auf Seitenebene vorzunehmen.

Siehe auch [Multi Site Manager](/help/sites-administering/msm.md).

### Miniaturansicht {#thumbnail}

![function-thumbnail](assets/funtion-thumbnail.png)

Im Bedienfeld &quot;Miniaturansichten&quot;kann ein Bild hochgeladen werden, das in der Konsole [Community-Funktionen](#community-functions-console) angezeigt wird.

## Community-Funktion öffnen {#open-community-function}

![open-function](assets/open-function.png)

Wählen Sie das Symbol &quot;`Open Community Function`&quot;, um in den Bearbeitungsmodus für den Autor zu wechseln, damit der Seiteninhalt bearbeitet und die Konfiguration der Funktionskomponenten geändert werden kann.

### Konfigurieren von Komponenten {#configuring-components}

Eine Community-Funktion wird als Live Copy eines AEM Blueprints implementiert, deren Details unter [Multi Site Manager](/help/sites-administering/msm.md) dokumentiert sind.

Es ist möglich, nicht nur Seiteninhalte zu erstellen, sondern Komponenten zu konfigurieren.

Wenn Sie eine Komponente auf einer Seite einer erstellten Community-Site konfigurieren, ist es möglicherweise erforderlich, die [Vererbung](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) abzubrechen, um die Komponente zu konfigurieren. Die Vererbung sollte nach Abschluss der Konfiguration wieder hergestellt werden.

Konfigurationsdetails finden Sie unter [Communities-Komponenten](/help/communities/author-communities.md) für Autoren.

## Community-Funktion bearbeiten {#edit-community-function}

![edit-function](assets/edit-function.png)

Wählen Sie das Symbol `Edit Community Function` aus, um die Eigenschaften der Funktion in denselben Bedienfeldern wie beim Erstellen einer Community-Funktion](#create-community-function) zu bearbeiten, einschließlich der Aktivierung oder Deaktivierung der Funktion.[
