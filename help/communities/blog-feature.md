---
title: Blogfunktion
seo-title: Blogfunktion
description: Community-Informationen im Journalformat
seo-description: Community-Informationen im Journalformat
uuid: 7323063f-81e8-45c3-9035-bf7df6124830
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cf8b3d72-30ba-40ca-ae48-b61abbb28802
docset: aem65
exl-id: 4650ac36-5506-4efc-be35-fac9e5a58f3d
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 47%

---

# Blogfunktion {#blog-feature}

## Einführung {#introduction}

Die Blogfunktion für AEM Communities wurde von einer Erstellungsaktivität in eine richtige Community-Aktivität umgewandelt, die in der Veröffentlichungsumgebung stattfindet.

Die Blogfunktion unterstützt die Bereitstellung von Community-Informationen in einem Aufzeichnungsformat. Blogeinträge werden in der Veröffentlichungsumgebung von autorisierten Mitgliedern (registrierten, angemeldeten Benutzern) vorgenommen.

Die Blogfunktion bietet Folgendes:

* Erstellung von Blogartikeln und -kommentaren in der Veröffentlichungsumgebung
* Bearbeiten von Rich-Text
* Inline-Bilder (mit Drag-and-Drop-Unterstützung)
* Eingebetteter Inhalt in sozialen Netzwerken ([Unterstützung von oEmbed](/help/communities/blog-developer-basics.md#allowing-rich-media))
* Entwurfsmodus
* Geplantes Veröffentlichen
* Erstellen im Auftrag (ein [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) kann Inhalte im Namen eines anderen Community-Mitglieds erstellen)
* [In-Kontext- und Massenmoderation](/help/communities/moderate-ugc.md) von Blogartikeln und -kommentaren

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben::

* Hinzufügen der Blog-Funktion zu einer AEM Site
* Konfigurationseinstellungen für Blogkomponenten

>[!NOTE]
>
>Die Komponenten `Journal` und `Journal Sidebar` haben die Titel `Blog` und `Blog Sidebar`.
>
>Die Blogfunktion in AEM 6.0 und älteren Versionen wurde eingestellt. Sie beruhte auf einer Vorlage und beschränkte das Verfassen von Inhalten ausschließlich auf die Autorenumgebung.

## Hinzufügen von Blog-Komponenten zu einer Seite {#adding-blog-components-to-a-page}

Wenn Sie im Autorenmodus einen Blog zu einer Seite hinzufügen möchten, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Blog`
* `Communities / Blog Sidebar`

und ziehen Sie die Elemente an die jeweilige Position auf der Seite, auf der das Blog angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/blog-developer-basics.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Blog` so angezeigt:

![add-blog-component](assets/add-blog-component.png)

### Konfigurieren eines Blogs {#configuring-blog}

Wählen Sie die platzierte Komponente `Blog` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

![Blog-Einstellungen](assets/blog-configure.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **Einstellungen** die grundlegenden Eigenschaften des Blogs an:

* **Anhangminiatur zulassen**

   Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Anhangminiaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Minimale Bildgröße für Miniaturansicht**

   Mindestgröße (in Byte) des Bildes zum Generieren von Miniaturansichten für Inline-Bilder. Der Standardwert ist 100000 Bytes (100 KB).

* **Max. Miniaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds für Inline-Bilder. Der Standardwert ist 800 x 800.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Zugelassene privilegierte Mitglieder**

   Fügen Sie die berechtigten Mitglieder hinzu, die Inhalte erstellen dürfen.

* **Benutzergenerierte Inhalte im Autoren-Bearbeitungsmodus blockieren**

   Wenn diese Option aktiviert ist, wird benutzergenerierter Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **Journaltitel**

   Der Blogtitel, der auf der Seite angezeigt werden soll.

>[!NOTE]
>
>Der Journaltitel wird verwendet, um automatisch eine URL für den Blog zu erstellen.
>
>Maximal 50 Zeichen (mit 5 zusätzlichen Zeichen für Eindeutigkeit) werden aus dem hier angegebenen Journaltitel verwendet, um eine URL für den Blog zu erstellen.

* **Journalbeschreibung**

   Die Blogbeschreibung.

* **Themen pro Seite**

   Definiert die Anzahl der Blogeinträge/Kommentare, die pro Seite angezeigt werden. Standard: 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss das Posten von Blogeinträgen und Kommentaren genehmigt werden, bevor sie auf einer veröffentlichten Site erscheinen. Die Standardeinstellung ist deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, ist der Blog für neue Blog-Einträge und Kommentare geschlossen. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Blogeinträge und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig aktiviert.

* **Tagging zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld** ). Diese Option ist standardmäßig deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie einem Blogeintrag oder Kommentar Dateianlagen hinzufügen. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die auf den Blogeintrag gepostet wurden. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die Funktion Abstimmung in einen Blogeintrag ein. Diese Option ist standardmäßig deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Blogeinträge löschen, die sie veröffentlicht haben. Diese Option ist standardmäßig deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder [benachrichtigt](/help/communities/notifications.md) über neue Beiträge werden können. Diese Option ist standardmäßig deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge benachrichtigt werden ([subscription](/help/communities/subscriptions.md)). Erfordert die Überprüfung von `Allow Following` und die Konfiguration von [E-Mail](/help/communities/email.md). Diese Option ist standardmäßig deaktiviert.

* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie verdiente und zugewiesene [Badges](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **Keine Antworten auf der Listenseite erhalten**

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **Erwähnung aktivieren**

   Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (unter Verwendung von Vorname, Nachname, Benutzername) identifizieren und sie mit der gemeinsamen Syntax @user-name versehen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

   Schränken Sie die maximale Anzahl der Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

   Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag mit Tags zu versehen (@mention). Beispiel: ~{{familyName}{{givenName}}.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation** die Moderationseinstellungen an:

* **Posts ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **Posts kennzeichnen**

   Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot;{#tag-field-tab}

Auf der Registerkarte **Tag-Feld** können Sie angeben, welche Tags verwendet werden dürfen, wenn die Option **Tagging zulassen** auf der Registerkarte **Einstellungen** aktiviert wurde:

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert -1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

### Konfigurieren einer Blog-Seitenleiste {#configuring-blog-sidebar}

Wenn Sie auf die Komponente `Blog Sidebar` doppelklicken, wird ein Dialogfeld zum Bearbeiten geöffnet.

Auf der Registerkarte **Journal-Sidebar-Einstellungen** können Sie das Datumsformat für Archive festlegen und angeben, welche Eintragstypen in der Seitenleiste aufgeführt werden sollen:

![blog-component-sidebar](assets/blog-component-sidebar.png)

* **Datumsformat**

   Das Format, das für die Anzeige von Archiven von Blogeinträgen verwendet wird. In diesem Format finden sich Platzhalter, die der Java-Konvention folgen.

   * JJJJ: lange Jahresangabe, z. B. 2015
   * JJ: kurze Jahresangabe, z. B. 15
   * MMMMM: vollständiger Monat, z. B. Juni
   * MMM: abgekürzter Monat, z. B. Jun
   * MM: Monatszahl, z. B. 06

   Der Standardwert ist &quot;jjjj MMMMM&quot;, der beispielsweise &quot;Juni 2015&quot;anzeigen würde.

* **Ansichtstyp**

   Der Titel und der Typ der Blogeinträge, die in der Seitenleiste angezeigt werden sollen. Die können aus folgenden Kategorien wählen:

   * Autoren
   * Kategorien
   * Archive

* **Pfad der Blopg-Komponente**

   *(Optional)* Der Speicherort der Blog-Ressource, von der aus Blog-Artikel aufgelistet werden sollen. Wenn Sie das Feld leer lassen, wird die Komponente von resourceType `social/journal/components/hbs/journal` verwendet, die auf derselben Seite angezeigt wird.

   * Beispiel: `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **Empfehlungsgrenze**

   Die Anzahl der anzuzeigenden Blogartikel. Der Wert -1 bedeutet keine Begrenzung. Der Standardwert ist -1.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung wird bei der Blogfunktion der neueste Blogartikel angezeigt, gefolgt von älteren Einträgen, die absteigend nach Erstellungsdatum sortiert sind. Blog-Seitenleisten ermöglichen es Besuchern der Site, einen Filter anzuwenden, um die Auswahl der anzuzeigenden Artikel einzuschränken.

Dem Blogartikel folgt ein Link, über den Kommentare gelesen oder verfasst werden können.

Wurde ein Blogartikel ausgewählt, werden der Artikel sowie zugehörige Kommentare eingeblendet (falls aktiviert).

Die Verfügbarkeit weiterer Optionen hängt davon ab, ob der Site-Besucher Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Besucher ist.

### Arbeiten mit Artikeln  {#working-with-articles}

Beim Erstellen eines neuen Blogartikels haben Sie folgende Möglichkeiten:

1. Sofort veröffentlichen
1. Einen Entwurf veröffentlichen
1. An einem geplanten Datum und zu einer geplanten Uhrzeit veröffentlichen

Die Blogartikel erscheinen auf der entsprechenden Registerkarte („Veröffentlicht“, „Entwürfe“ oder „Geplant“) und können von Mitgliedern bei der Veröffentlichung bearbeitet werden.

#### Moderatoren und Administratoren  {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) für alle Blogartikel und Komponenten des Blogs durchführen (je nach Berechtigungen durch die Konfiguration der Komponente).

![moderator-homepage](assets/moderator-homepage.png)

#### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied oder [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) ist (je nach Konfiguration), kann er `New Article` auswählen, um einen neuen Blog-Artikel zu erstellen und zu posten.

Insbesondere können sie:

* Erstellen eines neuen Blogartikels
* Posten eines neuen Blogartikels im Namen eines anderen Mitglieds
* Posten eines Kommentars zu einem Blogartikel
* Bearbeiten eigener Blogartikel oder Kommentare
* Löschen eigener Blogartikel oder Kommentare
* Kennzeichnen von Blogartikeln oder -kommentaren anderer Benutzer

![member-homepage](assets/member-homepage.png)

![create-blog](assets/create-blog.png)

#### Anonym {#anonymous}

Nicht angemeldete Besucher können veröffentlichte Blogartikel und Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Artikel oder Kommentare hinzufügen und keine Artikel und Kommentare anderer Benutzer kennzeichnen.

![anonymous-user-view](assets/anonymous-user-view.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Blog-Grundlagen](/help/communities/blog-developer-basics.md).

Informationen zur Moderation von Blogartikeln und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von Blogartikeln und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von Blogartikeln und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
