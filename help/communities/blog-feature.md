---
title: Blog-Funktion
description: Erfahren Sie, wie die Blog-Funktion die Bereitstellung von Community-Informationen in einem Journalformat unterstützt. Einträge werden von autorisierten Benutzenden in der Publish-Umgebung vorgenommen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 4650ac36-5506-4efc-be35-fac9e5a58f3d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1696'
ht-degree: 1%

---

# Blog-Funktion {#blog-feature}

## Einführung {#introduction}

Die Blog-Funktion für AEM Communities hat sich von einer Authoring-Aktivität zu einer echten Community-Aktivität geändert, die in der Publish-Umgebung stattfindet.

Die Blog-Funktion unterstützt die Bereitstellung von Community-Informationen in einem Journalformat. Blogeinträge werden in der Publish-Umgebung von autorisierten Mitgliedern (registrierte, angemeldete Benutzer) vorgenommen.

Die Blog-Funktion bietet :

* Publish-seitige Erstellung von Blog-Artikeln und -Kommentaren
* Rich-Text-Bearbeitung
* Inline-Bilder (mit Unterstützung für Drag &amp; Drop)
* Eingebettete Inhalte in sozialen Netzwerken ([oEmbed-Unterstützung](/help/communities/blog-developer-basics.md#allowing-rich-media))
* Entwurfsmodus
* Geplante Veröffentlichung
* Im Auftrag erstellen (ein [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) kann Inhalte im Auftrag eines anderen Community-Mitglieds erstellen)
* [Kontext- und Massenmoderation](/help/communities/moderate-ugc.md) von Blog-Artikeln und -Kommentaren

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Blog-Funktion zu einer AEM-Site
* Konfigurationseinstellungen für Blog-Komponenten

>[!NOTE]
>
>Die Komponenten `Journal` und `Journal Sidebar` sind `Blog` und `Blog Sidebar`.
>
>Die Blog-Funktion aus AEM 6.0 und früheren Versionen wurde entfernt. Sie basierte auf einer Vorlage und erlaubte es Autoren nur, Inhalte in der Autorenumgebung zu erstellen.

## Hinzufügen von Blog-Komponenten zu einer Seite {#adding-blog-components-to-a-page}

Wenn Sie einen Blog zu einer Seite im Autorenmodus hinzufügen möchten, verwenden Sie den Komponenten-Browser, um Folgendes zu suchen

* `Communities / Blog`
* `Communities / Blog Sidebar`

Und ziehen Sie sie in Position auf einer Seite, wo der Blog erscheinen soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](/help/communities/blog-developer-basics.md#essentials-for-client-side) enthalten sind, wird die `Blog` wie folgt angezeigt:

![add-blog-component](assets/add-blog-component.png)

### Blog konfigurieren {#configuring-blog}

Wählen Sie die platzierte `Blog` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

![Blog-Einstellungen](assets/blog-configure.png)

#### Registerkarte „Einstellungen“ {#settings-tab}

Geben **auf der Registerkarte** Einstellungen“ die grundlegenden Funktionen des Blogs an:

* **Miniaturansicht für Anhänge zulassen**

  Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Größe für Miniaturansichten anhängen**

  Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Minimale Bildgröße für Miniaturansicht**

  Mindestgröße (in Byte) des Bildes zum Generieren der Miniaturansicht für Inline-Bilder. Der Standardwert ist 100000 Byte (100 KB).

* **Maximale Größe von Miniaturansichten**

  Maximale Größe (in Pixeln) des Miniaturbilds für Inline-Bild. Der Standardwert ist 800 x 800.

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Zulässige privilegierte Mitglieder**

  Fügen Sie die privilegierten Mitglieder hinzu, die Inhalte erstellen dürfen.

* **Blockieren von benutzergenerierten Inhalten im Authoring-Bearbeitungsmodus**

  Wenn aktiviert, blockiert benutzergenerierte Inhalte während der Bearbeitung im Autorenmodus.

* **Journaltitel**

  Der Blogtitel, der auf der Seite angezeigt werden soll.

>[!NOTE]
>
>Der Journaltitel wird verwendet, um automatisch eine URL für den Blog zu erstellen.
>
>Aus dem hier angegebenen Journaltitel werden maximal 50 Zeichen (zusätzlich 5 Zeichen für Eindeutigkeit) verwendet, um eine URL für den Blog zu erstellen.

* **Journalbeschreibung**

  Die Blog-Beschreibung.

* **Themen pro Seite**

  Definiert die Anzahl der angezeigten Blog-Einträge/Kommentare pro Seite. Der Standardwert lautet 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss das Posten von Blogeinträgen und Kommentaren genehmigt werden, bevor sie auf einer veröffentlichten Website erscheinen. Die Standardeinstellung ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, wird der Blog für neue Blog-Einträge und -Kommentare geschlossen. Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Blogeinträge und Kommentare mit Markup eingegeben werden. Die Standardeinstellung ist aktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Labels hinzufügen (siehe **Tag-Feld** Registerkarte). Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Dateianhänge zu einem Blogeintrag oder Kommentar hinzugefügt werden. Standard ist deaktiviert.

* **max. Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Punkttrennzeichen. Zum Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, können die nicht angegebenen Dateitypen nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Max. Größe der angehängten Bilddatei**

  Nur relevant, wenn Datei-Uploads zulassen aktiviert ist. Maximale Anzahl an Byte, die eine hochgeladene Bilddatei aufweisen darf. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

  Wenn diese Option aktiviert ist, können Sie Antworten auf Kommentare zulassen, die im Blog-Eintrag gepostet werden. Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, wird die Abstimmungsfunktion in einen Blog-Eintrag eingefügt. Standard ist deaktiviert.

* **Benutzern das Löschen von Kommentaren und Themen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Blog-Einträge löschen, die sie veröffentlicht haben. Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, können Sie die folgende Funktion für Blog-Artikel einschließen, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) können. Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder über neue Beiträge per E-Mail benachrichtigt werden [Abonnement](/help/communities/subscriptions.md). Erfordert, dass `Allow Following` überprüft und [E-Mail konfiguriert](/help/communities/email.md). Standard ist deaktiviert.

* **Badges anzeigen**

  Wenn diese Option aktiviert ist, werden verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds angezeigt. Standard ist deaktiviert.

* **Auf der Listingseite werden keine Antworten angezeigt**

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option aktiviert ist, wird die Idee als [vorgestellter Inhalt“ &#x200B;](/help/communities/featured.md). Standard ist deaktiviert.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (mit Vorname, Nachname, Benutzername) identifizieren und sie mit der allgemeinen @user-name-Syntax taggen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre eigenen Erwähnungen.

* **Max Erwähnungen**

  Beschränken Sie die maximal zulässige Anzahl von Erwähnungen in einem Beitrag. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

#### Registerkarte „Benutzermoderation“ {#user-moderation-tab}

Geben Sie auf **Registerkarte** Benutzermoderation“ die Moderationseinstellungen an:

* **Beiträge verweigern**

  Wenn diese Option aktiviert ist, dürfen Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder ein Thema für weitere Bearbeitungen und Kommentare schließen und ein Thema auch erneut öffnen. Standard ist deaktiviert.

* **Flag-Posts**

  Wenn diese Option aktiviert ist, können Mitglieder andere Themen oder Kommentare als unangemessen kennzeichnen. Standard ist deaktiviert.

* **Verursacherliste kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem sie ein Thema oder einen Kommentar als unangemessen kennzeichnen. Standard ist deaktiviert.

* **Grund für benutzerdefinierte Markierung**

  Wenn diese Option aktiviert ist, können Mitglieder ihren eigenen Grund für das Kennzeichnen eines Themas oder Kommentars als unangemessen eingeben. Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungsgrenze**

  Geben Sie ein, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor es/er aus der öffentlichen Ansicht ausgeblendet wird. Wenn auf -1 festgelegt, wird das markierte Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für die Mäßigung sein. Der Standardwert ist 5.

#### Registerkarte „Tag-Feld“ {#tag-field-tab}

Geben Sie auf der Registerkarte **Tag** an, welche Tags angewendet werden können, wenn **Tagging zulassen** auf der Registerkarte **Einstellungen** aktiviert ist:

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die Tags, die angewendet werden können, sind auf die Tags innerhalb der ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst „Standard-Tags“ (den Standard-Namespace) und „Alle Tags einschließen“. Standardmäßig ist „Keine“ aktiviert, was bedeutet, dass alle Namespaces zulässig sind.

* **Vorschlagslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht. Ein Wert von -1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

### Konfigurieren der Blog-Seitenleiste {#configuring-blog-sidebar}

Wenn Sie auf die `Blog Sidebar` doppelklicken, wird ein Dialogfeld „Bearbeiten“ geöffnet.

Geben **auf der Registerkarte** Journal-Seitenleisteneinstellungen) das Datumsformat für Archive und den Typ der Einträge an, die in der Seitenleiste angezeigt werden sollen:

![blog-component-sidebar](assets/blog-component-sidebar.png)

* **Datumsformat**

  Das Format, das für die Anzeige von Archiven von Blog-Einträgen verwendet wird. Das Format verwendet Platzhalter gemäß der Java™-Konvention.

   * JJJJ : Gesamtjahr, wie &#39;2015&#39;
   * YY : Kurzes Jahr, wie „15“
   * MMMM : voller Monat, wie Juni
   * MMM : Kurzer Monat, wie Juni
   * MM : Monatsnummer, z. B. 06

  Der Standardwert ist „JJJJ-MMMM“, das z. B. „2015 Juni“ anzeigen würde

* **Ansichtstyp**

  Der Titel und der Typ der Blog-Einträge, die in der Seitenleiste angezeigt werden sollen. Sie haben die Wahl zwischen

   * Autoren
   * Kategorien
   * Archive

* **Blog-Komponentenpfad**

  *(Optional)* Der Speicherort der Blog-Ressource, aus der Blog-Artikel aufgelistet werden sollen. Wenn das Feld leer gelassen wird, wird die Komponente von resourceType `social/journal/components/hbs/journal` verwendet, die auf derselben Seite angezeigt wird.

   * Zum Beispiel: `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **Vorschlagslimit**

  Die Anzahl der anzuzeigenden Blog-Artikel. Ein Wert von -1 bedeutet keine Beschränkung. Der Standardwert ist -1.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung zeigt die Blogfunktion den neuesten Blogartikel gefolgt von älteren Blogartikeln in absteigender Reihenfolge der Erstellung an. In den Seitenleisten des Blogs können Besuchende der Site Filter anwenden, um die Auswahl der angezeigten Blog-Artikel zu begrenzen.

Auf den Blog-Artikel folgt ein Link zum Posten oder Anzeigen von Kommentaren.

Wenn ein Blog-Artikel ausgewählt wird, werden der Blog-Artikel und die Kommentare angezeigt (sofern aktiviert).

Andere Funktionen hängen davon ab, ob der Site-Besucher ein Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Benutzer ist.

### Arbeiten mit Artikeln {#working-with-articles}

Beim Erstellen eines Blog-Artikels haben Sie die Wahl, Folgendes zu tun:

1. Publish Sofort
1. Publish a Draft
1. Publish zu einem geplanten Zeitpunkt

Die Blog-Artikel werden unter der entsprechenden Registerkarte (Veröffentlicht, Entwürfe oder Geplant) für Mitglieder angezeigt, die in der Lage sind, in der Veröffentlichungsinstanz zu erstellen.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorrechte verfügt, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) (gemäß der Konfiguration der Komponente) für alle Blog-Artikel und -Kommentare ausführen, die in einem Blog veröffentlicht wurden.

![moderator-homepage](assets/moderator-homepage.png)

#### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied oder [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) ist (je nach Konfiguration), kann er `New Article` auswählen, um einen neuen Blog-Artikel zu erstellen und zu posten.

Insbesondere können sie:

* Erstellen eines Blog-Artikels
* Einen neuen Blog-Artikel im Namen eines anderen Mitglieds posten
* Kommentar zu einem Blog-Artikel posten
* Bearbeiten eines eigenen Blog-Artikels oder Kommentars
* Löschen eines eigenen Blog-Artikels oder Kommentars
* Markieren von Blog-Artikeln oder Kommentaren anderer Benutzer

![member-homepage](assets/member-homepage.png)

![create-blog](assets/create-blog.png)

#### Anonym {#anonymous}

Besucherinnen und Besucher der Website, die nicht angemeldet sind, dürfen nur gepostete Blog-Artikel und -Kommentare lesen, diese übersetzen, falls sie unterstützt werden, aber keinen Blog-Artikel oder -Kommentar hinzufügen oder die Artikel oder Kommentare anderer kennzeichnen.

![anonymous-user-view](assets/anonymous-user-view.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Blog Essentials](/help/communities/blog-developer-basics.md) für Entwickler.

Informationen zur Moderation von Blogeinträgen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von Blogeinträgen und Kommentaren finden Sie unter [Tagging von benutzergenerierten Inhalten](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von Blogeinträgen und Kommentaren finden Sie unter [Übersetzen von benutzergenerierten Inhalten](/help/communities/translate-ugc.md).
