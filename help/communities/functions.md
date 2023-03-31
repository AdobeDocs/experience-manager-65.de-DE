---
title: Community-Funktionen
seo-title: Community Functions
description: Erfahren Sie, wie Sie auf die Konsole "Community-Funktionen"zugreifen
seo-description: Learn how to access the Community Functions console
uuid: d3d70134-f318-4709-a673-b01a3467d980
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 91833914-b811-4355-a97d-e1a9cb7441f1
docset: aem65
role: Admin
exl-id: 2395c895-c611-43ac-abb6-c2bc4b4a41f4
source-git-commit: 4dbbcc41757843d3b2d5a3bbb2656ef587e83d2c
workflow-type: tm+mt
source-wordcount: '2224'
ht-degree: 6%

---

# Community-Funktionen{#community-functions}

Die Art der Funktionen, die von einem Community-Erlebnis erwartet werden, ist bekannt. Community-Funktionen sind als Community-Funktionen verfügbar. Im Grunde sind es eine oder mehrere Seiten, die vorab mit dem Netzwerk verbunden sind, um eine Community-Funktion zu implementieren, die mehr erfordert, als einfach eine Komponente zu einer Seite im Autorenmodus hinzuzufügen. Sie sind die Bausteine, mit denen die Struktur eines [Community-Site-Vorlage](/help/communities/sites.md) von welchen Community-Sites [created](/help/communities/sites-console.md).

Nachdem eine Community-Site erstellt wurde, kann den resultierenden Seiten mithilfe der standardmäßigen [AEM Authoring-Modus](/help/sites-authoring/editing-content.md). In der Konsole Community-Funktionen sind verschiedene Community-Funktionen verfügbar.

>[!NOTE]
>
>Die Konsolen für die Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md)und [Community-Funktionen](/help/communities/functions.md) sind nur zur Verwendung in der Autorenumgebung vorgesehen.

## Community-Funktionskonsole {#community-functions-console}

So rufen Sie die Konsole für Community-Funktionen in der Autorenumgebung auf:

* Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Communities]** > **[!UICONTROL Community-Funktionen]**.

![Community-Funktionen](assets/community-functions.png)

## Vordefinierte Funktionen {#pre-built-functions}

Im Folgenden finden Sie eine kurze Beschreibung der Funktionen, die mit AEM Communities bereitgestellt werden. Jede Funktion umfasst eine oder mehrere AEM Seiten, die Communities-Komponenten enthalten, die mit einer Funktion verbunden sind, die einfach in eine Funktion integriert werden kann. [Community-Site-Vorlage](/help/communities/sites.md).

Eine Community-Site-Vorlage bietet die Struktur für eine Community-Site, einschließlich Anmeldung, Benutzerprofile, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen.

### Titel und URL-Einstellungen {#title-and-url-settings}

**Titel** und **URL** sind Eigenschaften, die allen Community-Funktionen gemeinsam sind.

Wenn eine Community-Funktion zu einer Community-Site-Vorlage hinzugefügt oder hinzugefügt wird, wenn [Ändern](/help/communities/sites-console.md#modifying-site-properties) Wenn die Struktur einer Community-Site festgelegt ist, wird das Dialogfeld der Funktion geöffnet, sodass Titel und URL konfiguriert werden können.

#### Konfiguration der Funktionsdetails {#configuration-function-details}

![title-url-details](assets/title-url-details.png)

* **Titel**

   (*Erforderlich*) Der Text, der im Menü der Funktionen für die Site angezeigt wird

* **URL**

   (*Erforderlich*) Der zum Generieren des URI verwendete Name. Der Name muss mit dem [Benennungskonventionen](/help/sites-developing/naming-conventions.md) von AEM und JCR auferlegt.

Beispielsweise können Sie die aus dem folgenden Beispiel erstellte Site verwenden: [Erste Schritte](/help/communities/getting-started.md) Tutorial, falls

* Titel = Webseite
* URL = Seite

Dann lautet die URL zur Seite https://localhost:4503/content/sites/engage/en/page.html

und der Menülink für die Seite wie folgt angezeigt wird:

![engage-page](assets/engage-page.png)

### Aktivitäts-Stream-Funktion {#activity-stream-function}

Die Aktivitäts-Stream-Funktion ist eine Seite mit einer [Aktivitäts-Streams-Komponente](/help/communities/activities.md) mit allen ausgewählten Ansichten (alle Aktivitäten, Benutzeraktivitäten und Folgeaktivitäten). Siehe auch [Grundlagen zum Aktivitäts-Stream](/help/communities/essentials-activities.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-1}

![function-details](assets/function-details.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Ansicht „Meine Aktivitäten“ anzeigen**

   Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten eine Registerkarte, auf der Aktivitäten basierend auf denen gefiltert werden, die innerhalb der Community vom aktuellen Mitglied generiert wurden. Standardmäßig ist ausgewählt.

* **Ansicht „Alle Aktivitäten“ anzeigen**

   Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten einen Tab, der alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Standardmäßig ist ausgewählt.

* **Ansicht „News-Feed“ anzeigen**

   Wenn diese Option aktiviert ist, enthalten die Aktivitätsseiten eine Registerkarte, auf der Aktivitäten nach denen gefiltert werden, denen das aktuelle Mitglied folgt. Standardmäßig ist ausgewählt.

### Blogfunktion {#blog-function}

Die Blogfunktion ist eine Seite mit einer [Blog-Komponente](/help/communities/blog-feature.md) konfiguriert für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation. Siehe auch [Blog-Grundlagen](/help/communities/blog-developer-basics.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![blog-component](assets/blog-component.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Artikel erstellen, indem sie die Auswahl einer [Gruppe privilegierter Mitglieder](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder erstellen. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, bietet der Blog Mitgliedern die Möglichkeit, Dateien hochzuladen. Standardmäßig ist ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option nicht ausgewählt ist, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht zulässig. Standardmäßig ist ausgewählt.

* **Feature-Inhalt zulassen**

   Wenn ausgewählt, wird der Blog als [präsentierte Inhalte](/help/communities/featured.md). Standardmäßig ist ausgewählt.

### Kalenderfunktion {#calendar-function}

Die Kalenderfunktion ist eine Seite mit einer [Kalenderkomponente](/help/communities/calendar.md) konfiguriert, um Tagging zuzulassen. Siehe auch [Kalendergrundlagen](/help/communities/calendar-basics-for-developers.md) für Entwickler.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![calendar-details](assets/calendar-details.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare eingefügt werden. Standardmäßig ist ausgewählt.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Artikel erstellen, indem sie die Auswahl einer [Gruppe privilegierter Mitglieder](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder erstellen. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, bietet der Blog Mitgliedern die Möglichkeit, Dateien hochzuladen. Standardmäßig ist ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option nicht ausgewählt ist, erlaubt der Blog Antworten (Kommentare) auf einen Artikel, aber Antworten auf Kommentare sind nicht zulässig. Standardmäßig ist ausgewählt.

* **Feature-Inhalt zulassen**

   Bei Auswahl dieser Option wird der Inhalt als [präsentierte Inhalte](/help/communities/featured.md). Standardmäßig ist ausgewählt.

### Funktion für spezielle Inhalte {#featured-content-function}

Die Funktion für speziellen Inhalt ist eine Seite mit einer [Komponente für spezielle Inhalte](/help/communities/featured.md) konfiguriert, damit Kommentare hinzugefügt und gelöscht werden können.

Die Möglichkeit, Inhalte pro Komponente zu verwenden, kann zulässig oder unzulässig sein (siehe [Blogfunktion](#blog-function), [Kalenderfunktion](#calendar-function), [Forumsfunktion](#forum-function), [Ideenfunktion](#ideation-function)und [QnA-Funktion](#qna-function)).

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für die [Titel und URL-Einstellungen](#title-and-url-settings).

### Dateibibliotheksfunktion {#file-library-function}

Die Dateibibliotheksfunktion ist eine Seite mit einer [Dateibibliothek-Komponente](/help/communities/file-library.md) konfiguriert, damit Kommentare hinzugefügt und gelöscht werden können.

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für die [Titel und URL-Einstellungen](#title-and-url-settings).

### Forumsfunktion {#forum-function}

Die Forumsfunktion ist eine Seite mit einer [Forumkomponente](/help/communities/forum.md) konfiguriert für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

#### Konfiguration der Funktionsdetails {#configuration-function-details-2}

![forum-component1](assets/forum-component1.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare eingefügt werden. Standardmäßig ist ausgewählt.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, können nur privilegierte Mitglieder Themen posten, indem sie die Auswahl einer [Gruppe privilegierter Mitglieder](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Standardmäßig ist ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option nicht ausgewählt ist, sind im Forum Kommentare zu einem Thema zulässig, Antworten auf diese Kommentare sind jedoch nicht zulässig. Standardmäßig ist ausgewählt.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, wird der Inhalt der Komponente als [präsentierte Inhalte](/help/communities/featured.md). Standardmäßig ist ausgewählt.

### Gruppenfunktion {#groups-function}

>[!CAUTION]
>
>Die Funktion &quot;Gruppen&quot;muss *not* die *first noch die einzige* in der Struktur einer Site oder in einer Community-Site-Vorlage verwendet werden.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](#page-function), muss zuerst eingeschlossen und aufgelistet werden.

Die Funktion &quot;Gruppen&quot;bietet Community-Mitgliedern die Möglichkeit, Untergruppen innerhalb der Community-Site in der Veröffentlichungsumgebung zu erstellen.

Abhängig von [settings](/help/communities/sites-console.md#groupmanagement) wenn die Funktion Gruppen in einer [Community-Site-Vorlage](/help/communities/sites.md), können die Gruppen öffentlich oder privat sein und eine oder mehrere Community-Gruppenvorlagen können so konfiguriert werden, dass sie eine Auswahl von Vorlagen bereitstellen, wenn die Community-Gruppe tatsächlich erstellt wird (z. B. aus der Veröffentlichungsumgebung). A [Community-Gruppenvorlage](/help/communities/tools-groups.md) gibt an, welche Communities-Funktionen für die Gruppenseiten erstellt werden, z. B. Foren und Kalender.

Wenn eine Community-Gruppe erstellt wird, wird eine Mitgliedergruppe für die neue Gruppe dynamisch erstellt, der Mitglieder zugewiesen oder hinzugefügt werden können. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

Als Communitys [Feature Pack 1](/help/communities/deploy-communities.md#latestfeaturepack), werden Community-Gruppen in der Autorenumgebung mit der [Communities Sites-Gruppenkonsole](/help/communities/groups.md), und kann in der Veröffentlichungsumgebung erstellt werden, wenn sie aktiviert ist.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet:

![group-template-config](assets/group-template-config.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Gruppenvorlagen auswählen**

   Eine Dropdown-Liste, die die Auswahl einer oder mehrerer aktivierter Gruppenvorlagen ermöglicht, aus denen der künftige Ersteller einer neuen Community-Gruppe (in der Veröffentlichungsumgebung) wählen kann.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, können nur privilegierte Mitglieder Themen posten, indem sie die Auswahl einer [Sicherheitsgruppe privilegierter Mitglieder](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Veröffentlichung der Kreation erlauben**

   Sofern ausgewählt, können autorisierte Community-Mitglieder eine Gruppe in der Veröffentlichungsumgebung erstellen. Wenn diese Option deaktiviert ist, können neue Gruppen (Untergruppen) nur in der Autorenumgebung über die Gruppenkonsole der Communities-Sites erstellt werden.
Standardmäßig ist ausgewählt.

### Ideen-Funktion {#ideation-function}

Die Ideenfunktion ist eine Seite mit einer [Ideenkomponente](/help/communities/ideation-feature.md).

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt sind:

![ideation-function](assets/ideation-function.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, können nur privilegierte Mitglieder Themen posten, indem sie die Auswahl einer [Sicherheitsgruppe privilegierter Mitglieder](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Standardmäßig ist ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option nicht ausgewählt ist, sind Antworten (Kommentare) auf ein Thema zulässig, Antworten auf Kommentare sind jedoch nicht zulässig. Standardmäßig ist ausgewählt.

* **Feature-Inhalt zulassen**

   Bei Auswahl dieser Option wird der Inhalt als [präsentierte Inhalte](/help/communities/featured.md). Standardmäßig ist ausgewählt.

### Leaderboard-Funktion {#leaderboard-function}

Die Leaderboard-Funktion ist eine Seite mit einer [Leaderboard-Komponente](/help/communities/enabling-leaderboard.md).

**NOTE**: Die Leaderboard-Komponente muss weiter konfiguriert werden *after* Eine Community-Site wird aus einer Community-Vorlage erstellt, die die Leaderboard-Funktion enthält. Geben Sie die Leaderboard-Komponente an [Regeln](/help/communities/enabling-leaderboard.md#rules-tab), die von der Konfiguration von [Scoring und Abzeichen](/help/communities/implementing-scoring.md) für die Community-Site.

Wenn eine Vorlage hinzugefügt wird, wird das folgende Dialogfeld geöffnet, in dem der Standardtitel und die URL-Namen sowie die standardmäßigen Anzeigeeinstellungen für die Vorlage festgelegt sind:

![Lederboard-Dialog](assets/leaderboard-dialog.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, wird eine Spalte für Badge-Symbole in die Leaderboard eingefügt.
Die Option Standard ist deaktiviert.

* **Abzeichennamen anzeigen**

   Wenn diese Option aktiviert ist, wird eine Spalte für den Badge-Namen in die Leaderboard eingefügt.
Die Option Standard ist deaktiviert.

* **Avatar anzeigen**

   Wenn diese Option aktiviert ist, wird das Avatarbild des Mitglieds in das Leaderboard eingefügt, neben dem Namen, der mit seinem Mitgliederprofil verknüpft ist.
Die Option Standard ist deaktiviert.

### Seitenfunktion {#page-function}

Die Seitenfunktion fügt der Community-Site eine leere Seite hinzu, auf der sie mit den Funktionen der Community-Site verknüpft ist: Login, Menü, Benachrichtigungen, Messaging, Design und Branding. Der Inhalt wird der Seite mithilfe der [Standard-AEM](/help/sites-authoring/editing-content.md).

Wenn sie einer Vorlage hinzugefügt wird, ist die einzige Konfiguration für die [Titel und URL-Einstellungen](#title-and-url-settings).

### Fragen/Antworten-Funktion {#qna-function}

Die Funktion &quot;Fragen und Antworten&quot;ist eine Seite mit einer [QnA-Komponente](/help/communities/working-with-qna.md) konfiguriert für Tagging, Datei-Uploads, Follower, Mitglieder zur Selbstbearbeitung, Abstimmung und Moderation.

Wenn sie einer Vorlage hinzugefügt wird, ermöglicht die Konfiguration die Beschränkung auf privilegierte Mitglieder:

![qna-dialog](assets/qna-dialog.png)

* [Titel und URL-Einstellungen](#title-and-url-settings)

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Themenantworten an den Anfang der Liste der Kommentare eingefügt werden. Standardmäßig ist ausgewählt.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Fragen posten, indem sie die Auswahl eines [Gruppe privilegierter Mitglieder](/help/communities/users.md#privileged-members-group). Wenn diese Option nicht ausgewählt ist, dürfen alle Community-Mitglieder Beiträge posten. Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Dateien hochladen. Standardmäßig ist ausgewählt.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option nicht ausgewählt ist, können im Forum Kommentare (Antworten) zu einer geposteten Frage eingesehen werden. Antworten auf Antworten sind jedoch nicht zulässig. Standardmäßig ist ausgewählt.

* **Feature-Inhalt zulassen**

   Bei Auswahl dieser Option wird der Inhalt als [präsentierte Inhalte](/help/communities/featured.md). Standardmäßig ist ausgewählt.

## Community-Funktion erstellen {#create-community-function}

Die Möglichkeit, eine Community-Funktion zu erstellen, wird durch Auswahl der `Create Community Function` -Symbol oben in der Konsole &quot;Community-Funktionen&quot;angezeigt. Mehrere Funktionen, die auf demselben AEM Blueprint basieren, können erstellt und dann durch Öffnen im Bearbeitungsmodus des Autors eindeutig angepasst werden.

![create-community-function](assets/create-community-function.png)

### Name der Community-Funktion {#community-function-name}

![function-name](assets/function-name.png)

Im Bereich &quot;Community Function Name&quot;werden ein Name, eine Beschreibung und ob die Funktion aktiviert oder deaktiviert ist konfiguriert:

* **Name der Community-Funktion**

   Der Funktionsname, der für die Anzeige und Speicherung verwendet wird.

* **Community-Funktionsbeschreibung**

   Die Funktionsbeschreibung für die Anzeige.

* **Deaktiviert/Aktiviert**

   Ein Umschalter steuert, ob die Funktion referenzierbar ist.

### AEM-Blueprint {#aem-blueprint}

![aem-blueprint](assets/aem-blueprint.png)

Im `AEM Blueprint` -Bedienfeld kann der Blueprint ausgewählt werden, der der zugrunde liegenden Implementierung der Community-Funktion entspricht.

Die Community-Funktion ist eine Mini-Site, die eine oder mehrere Seiten enthält und vorab für die Integration in eine Community-Site kabelgebunden ist, einschließlich Anmeldung, Benutzerprofile, Benachrichtigungen, Messaging, Site-Menü, Suche, Themen und Branding-Funktionen. Nach der Erstellung der Funktion ist es möglich, [Funktion öffnen](#open-community-function) im Bearbeitungsmodus des Autors und passen Sie die Seiten- oder Komponenteneinstellungen an.

Da die Community-Funktion als [Live Copy](/help/sites-administering/msm.md#live-copies) von [Blueprint](/help/sites-administering/msm-livecopy.md#creatingablueprint)können Rollout-Änderungen an einer Funktion vorgenommen werden, die sich auf alle Community-Site-Seiten auswirken, die von der [Community-Site-Vorlage](/help/communities/sites.md) oder [Community-Gruppenvorlage](/help/communities/tools-groups.md) , die die Funktion enthielt. Es ist auch möglich, die Zuordnung einer Seite zu ihrem übergeordneten Blueprint zu trennen, um Änderungen auf Seitenebene vorzunehmen.

Siehe auch [Multi-Site-Manager](/help/sites-administering/msm.md).

### Miniaturansicht {#thumbnail}

![function-thumbnail](assets/funtion-thumbnail.png)

Im Bereich &quot;Miniaturansicht&quot;kann ein Bild hochgeladen werden, das im [Community-Funktionskonsole](#community-functions-console).

## Community-Funktion öffnen {#open-community-function}

![open-function](assets/open-function.png)

Wählen Sie die `Open Community Function` -Symbol, um in den Bearbeitungsmodus für den Autor zu wechseln, um den Seiteninhalt zu erstellen und die Konfiguration der Funktionskomponente(n) zu ändern.

### Konfigurieren von Komponenten {#configuring-components}

Eine Community-Funktion wird als Live Copy eines AEM Blueprints implementiert, dessen Details unter [Multi-Site-Manager](/help/sites-administering/msm.md).

Es ist möglich, nicht nur Seiteninhalte zu erstellen, sondern Komponenten zu konfigurieren.

Wenn Sie eine Komponente auf einer Seite einer erstellten Community-Site konfigurieren, ist es möglicherweise erforderlich, den Vorgang abzubrechen. [Vererbung](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) , um die Komponente zu konfigurieren. Nach Abschluss der Konfiguration sollte die Vererbung wieder hergestellt werden.

Konfigurationsdetails finden Sie unter [Communities-Komponenten](/help/communities/author-communities.md) für Autoren.

## Community-Funktion bearbeiten {#edit-community-function}

![edit-function](assets/edit-function.png)

Wählen Sie die `Edit Community Function` -Symbol, um die Eigenschaften der Funktion mit denselben Bedienfeldern wie zu bearbeiten [Erstellen einer Community-Funktion](#create-community-function), einschließlich der Aktivierung oder Deaktivierung der Funktion .
