---
title: Blogfunktion
seo-title: Blogfunktion
description: Gemeinschaftsinformationen in journalistischer Form
seo-description: Gemeinschaftsinformationen in journalistischer Form
uuid: 7323063f-81e8-45c3-9035-bf7df6124830
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: cf8b3d72-30ba-40ca-ae48-b61abbb28802
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Blogfunktion{#blog-feature}

## Einführung {#introduction}

Die Blogfunktion für AEM Communities wurde von einer Erstellungsaktivität in eine richtige Community-Aktivität umgewandelt, die in der Veröffentlichungsumgebung stattfindet.

Die Blogfunktion unterstützt die Bereitstellung von Community-Informationen in einem Aufzeichnungsformat. Blog-Einträge werden in der Veröffentlichungsumgebung von autorisierten Mitgliedern (registrierte, angemeldete Benutzer) vorgenommen.

Die Blogfunktion bietet Folgendes:

* Erstellung von Blogartikeln und -kommentaren in der Veröffentlichungsumgebung
* Bearbeiten von Rich-Text
* Inline-Bilder (mit Drag-and-Drop-Unterstützung)
* Eingebetteter Inhalt in sozialen Netzwerken ([Unterstützung von oEmbed](/help/communities/blog-developer-basics.md#allowing-rich-media))
* Entwurfsmodus
* Geplantes Veröffentlichen
* Erstellen im Auftrag (ein [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) kann Inhalte im Namen eines anderen Community-Mitglieds erstellen)
* [In-Kontext- und Massenmoderation](/help/communities/moderate-ugc.md) von Blogartikeln und -kommentaren

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Blogfunktion zu einer AEM-Site
* Konfigurationseinstellungen für Blog-Komponenten

>[!NOTE]
>
>Die Komponenten `Journal`und `Journal Sidebar` sind mit `Blog` und `Blog Sidebar`.
>
>Die Blogfunktion in AEM 6.0 und älteren Versionen wurde eingestellt. Sie beruhte auf einer Vorlage und beschränkte das Verfassen von Inhalten ausschließlich auf die Autorenumgebung.

## Hinzufügen von Blog-Komponenten zu einer Seite {#adding-blog-components-to-a-page}

Wenn Sie im Autorenmodus einen Blog zu einer Seite hinzufügen möchten, suchen Sie im Komponentenbrowser nach

* `Communities / Blog`
* `Communities / Blog Sidebar`

und ziehen Sie die Elemente an die jeweilige Position auf der Seite, auf der das Blog angezeigt werden soll.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/blog-developer-basics.md#essentials-for-client-side) are included, this is how the `Blog`component will appear :

![chlimage_1-229](assets/chlimage_1-229.png)

Und wie das `Blog Sidebar` aussehen wird:

![chlimage_1-230](assets/chlimage_1-230.png)

### Konfigurieren eines Blogs {#configuring-blog}

Select the placed `Blog` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-231](assets/chlimage_1-231.png) ![Blog-Einstellungen](assets/blog-configure.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **Einstellungen** die grundlegenden Eigenschaften des Blogs an:

* **&quot;Miniaturansicht** zulassen&quot;Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Maximale Größe** der Miniaturansicht der Anlage (in Pixel). Der Standardwert ist 800 x 800.
* **Min. Bildgröße für Miniaturansichten**. Mindestgröße (in Byte) des Bildes für die Erstellung von Miniaturbildern für Inline-Bilder. Der Standardwert ist 100000 Byte (100 KB).
* **Maximale Größe** der Miniaturansicht des Inline-Bildes (in Pixel). Der Standardwert ist 800 x 800.
* **Privilegierte Mitglieder** zulassen Wenn diese Option aktiviert ist, dürfen nur Privilegierte Mitglieder Inhalte erstellen.
* **Zulässige privilegierte Mitglieder** Fügen Sie die privilegierten Mitglieder hinzu, die Inhalte erstellen dürfen.
* **Blockieren benutzergenerierter Inhalte im Bearbeitungsmodus**&quot;Autor&quot;Blockieren Sie,wenn diese Option aktiviert ist, beim Bearbeiten im Autorenmodus den vom Benutzer erstellten Inhalt.

* **Journaltitel** Der Blogname, der auf der Seite angezeigt werden soll.

>[!NOTE]
>
>Mit dem Journaltitel wird automatisch eine URL für das Blog erstellt.
>Maximal 50 Zeichen (mit 5 zusätzlichen Zeichen zur Eindeutigkeit) werden aus dem hier angegebenen Zeitschriftentitel verwendet, um eine URL für das Blog zu erstellen.

* **Journalbeschreibung**Die Blog-Beschreibung.
* **Themen pro Seite** Definiert die Anzahl der Blogeinträge/Kommentare, die pro Seite angezeigt werden. Der Standardwert lautet 10.

* **Moderiert** Wenn diese Option aktiviert ist, muss die Veröffentlichung von Blog-Einträgen und Kommentaren genehmigt werden, bevor sie auf einer veröffentlichten Site erscheinen. Die Standardeinstellung ist deaktiviert.

* **Geschlossen** Ist diese Option aktiviert, können in dem Blog keine neuen Einträge oder Kommentare mehr veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor** Ist diese Option aktiviert, können Blogeinträge und -kommentare mit Markup versehen werden. Diese Option ist standardmäßig aktiviert.

* **Tagging zulassen** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld**). Diese Option ist standardmäßig deaktiviert.

* **Datei-Uploads zulassen** Ist diese Option aktiviert, können Blogeinträgen oder -kommentaren Dateien hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße** Relevant nur, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen** Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass** **alle Dateitypen zulässig sind.

* **Max. Größe** der Bilddatei anhängen ist nur relevant, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152****(2 MB).

* **Antworten zulassen** Ist diese Option aktiviert, können Antworten auf Kommentare zum Blogeintrag veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Blogeinträgen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen** Ist diese Option aktiviert, können Mitglieder Kommentare zu von ihnen veröffentlichten Blogeinträgen löschen. Der Standardwert ist** **nicht markiert.

* **Zulassen** Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **E-Mail-Abonnements** zulassen Wenn diese Option aktiviert ist, erlauben Sie Mitgliedern, über neue Beiträge per E-Mail ([Abonnement](/help/communities/subscriptions.md)) benachrichtigt zu werden. Muss überprüft `Allow Following` und [E-Mail konfiguriert](/help/communities/email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **Anzeigen von Abzeichen** Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **Keine Antworten auf der Listenseite erhalten**
* **Wenn Sie** die Option &quot;Vorgestellte Inhalte zulassen&quot;aktivieren, kann die Idee als [speziellen Inhalt](/help/communities/featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **Erwähnung** aktivieren Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder identifizieren (unter Verwendung von Vorname, Nachname, Benutzername) und sie mit der gemeinsamen @user-name-Syntax markieren. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**: Die maximale Anzahl an Erwähnungen, die in einem Beitrag zulässig sind, beschränken. Der Standardwert ist 10.

* **Benutzeroberflächenbeschreibungsmuster** Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@Erwähnung). Beispiel: ~{{familyName}}{{vorname}}.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation** die Moderationseinstellungen an:

* **Posts ablehnen** Ist diese Option aktiviert, können moderierende Mitglieder Beiträge ablehnen und so verhindern, dass diese im Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **Themen schließen/erneut öffnen** Ist diese Option aktiviert, können moderierende Mitglieder Themen für die weitere Bearbeitung oder Kommentare schließen oder bereits geschlossene Themen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **Posts kennzeichnen** Ist diese Option aktiviert, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert**.**

* **Liste mit Kennzeichnungsgründen** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Thema oder ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Themen oder Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert**.**

* **Schwellenwert für Moderation** Geben Sie an, wie oft ein Thema oder ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit** Geben Sie an, wie oft ein Thema oder ein Kommentar als unangemessen gekennzeichnet werden muss, bevor es oder er aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Auf der Registerkarte **Tag-Feld** können Sie angeben, welche Tags verwendet werden dürfen, wenn die Option **Tagging zulassen** auf der Registerkarte **Einstellungen** aktiviert wurde:

* **Zulässige Namespaces** Relevant, wenn sie unter der Registerkarte **Einstellungen **markiert `Allow Tagging` sind. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Der Wert -1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

### Konfigurieren einer Blog-Seitenleiste {#configuring-blog-sidebar}

When you double-click the `Blog Sidebar` component, an edit dialog opens up.

Auf der Registerkarte **Journal-Sidebar-Einstellungen** können Sie das Datumsformat für Archive festlegen und angeben, welche Eintragstypen in der Seitenleiste aufgeführt werden sollen:

![blog-component-sidebar](assets/blog-component-sidebar.png)

* **Datumsformat** Das Format, das für die Anzeige von Blogeintragsarchiven verwendet werden soll. In diesem Format finden sich Platzhalter, die der Java-Konvention folgen.

   * JJJJ: lange Jahresangabe, z. B. 2015
   * JJ: kurze Jahresangabe, z. B. 15
   * MMMMM: vollständiger Monat, z. B. Juni
   * MMM: abgekürzter Monat, z. B. Jun
   * MM: Monatszahl, z. B. 06
   Der Standardwert ist &quot;yyyy MMMMM&quot;, der beispielsweise &quot;Juni 2015&quot;anzeigen würde.

* **Ansichtstyp** Titel und Typ der Blog-Einträge, die in der Seitenleiste angezeigt werden sollen. Die können aus folgenden Kategorien wählen:

   * Autoren
   * Kategorien
   * Archive

* **Blopg-Komponentenpfad**
   *(Optional)* Der Speicherort der Blog-Ressource, aus der Blog-Artikel aufgelistet werden sollen. Wenn Sie das Feld leer lassen, verwenden Sie die Komponente von resourceType `social/journal/components/hbs/journal` , die auf derselben Seite angezeigt wird.

   * for example, `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **Empfehlung begrenzen** Die Anzahl der anzuzeigenden Blog-Artikel. Der Wert -1 bedeutet keine Begrenzung. Der Standardwert ist -1.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung wird bei der Blogfunktion der neueste Blogartikel angezeigt, gefolgt von älteren Einträgen, die absteigend nach Erstellungsdatum sortiert sind. Blog-Seitenleisten ermöglichen es Besuchern der Site, einen Filter anzuwenden, um die Auswahl der anzuzeigenden Artikel einzuschränken.

Dem Blogartikel folgt ein Link, über den Kommentare gelesen oder verfasst werden können.

Wurde ein Blogartikel ausgewählt, werden der Artikel sowie zugehörige Kommentare eingeblendet (falls aktiviert).

Die Verfügbarkeit weiterer Optionen hängt davon ab, ob der Site-Besucher Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Besucher ist.

### Arbeiten mit Artikeln {#working-with-articles}

Wenn Sie einen neuen Blogartikel erstellen, können Sie aus folgenden Optionen wählen:

1. Sofort veröffentlichen
1. Einen Entwurf veröffentlichen
1. An einem geplanten Datum und zu einer geplanten Uhrzeit veröffentlichen

Die Blogartikel erscheinen auf der entsprechenden Registerkarte („Veröffentlicht“, „Entwürfe“ oder „Geplant“) und können von Mitgliedern bei der Veröffentlichung bearbeitet werden.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) für alle Blogartikel und Komponenten des Blogs durchführen (je nach Berechtigungen durch die Konfiguration der Komponente).

![chlimage_1-232](assets/chlimage_1-232.png)

#### Mitglieder {#members}

When the signed in user is a community member or [privileged member](/help/communities/users.md#privileged-members-group) (depending on configuration), they are able to select `New Article` to create and post a new blog article.

Insbesondere ist Folgendes möglich:

* Erstellen eines neuen Blogartikels
* Veröffentlichen eines neuen Blogartikels im Namen eines anderen Mitglieds
* Veröffentlichen eines Kommentars zu einem Blogartikel
* Bearbeiten eigener Blogartikel oder Kommentare
* Löschen eigener Blogartikel oder Kommentare
* Kennzeichnen von Blogartikeln oder Kommentaren anderer Mitglieder

![chlimage_1-233](assets/chlimage_1-233.png) ![chlimage_1-234](assets/chlimage_1-234.png)

#### Anonym {#anonymous}

Nicht angemeldete Besucher können veröffentlichte Blogartikel und Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Artikel oder Kommentare hinzufügen und keine Artikel und Kommentare anderer Benutzer kennzeichnen.

![chlimage_1-235](assets/chlimage_1-235.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Blog-Grundlagen](/help/communities/blog-developer-basics.md).

Informationen zur Moderation von Blogartikeln und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von Blogartikeln und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von Blogartikeln und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
