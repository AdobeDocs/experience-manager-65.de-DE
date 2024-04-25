---
title: Blog-Funktion
description: Erfahren Sie, wie die Blog-Funktion die Bereitstellung von Community-Informationen in einem Journaling-Format unterstützt. Die Einträge werden von autorisierten Benutzern in der Veröffentlichungsumgebung vorgenommen.
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

Die Blog-Funktion für AEM Communities wurde von einer Authoring-Aktivität zu einer echten Community-Aktivität, die in der Veröffentlichungsumgebung stattfindet, geändert.

Die Blog-Funktion unterstützt die Bereitstellung von Community-Informationen in einem Journaling-Format. Blogeinträge werden in der Veröffentlichungsumgebung von autorisierten Mitgliedern (registrierte, angemeldete Benutzer) vorgenommen.

Die Blogfunktion bietet :

* Publishing-seitige Erstellung von Blogartikeln und Kommentaren
* Rich-Text-Bearbeitung
* Inline-Bilder (mit Drag &amp; Drop-Unterstützung)
* Eingebetteter Inhalt in sozialen Netzwerken ([Unterstützung für Einbettung](/help/communities/blog-developer-basics.md#allowing-rich-media))
* Entwurfsmodus
* Geplante Veröffentlichung
* Erstellen Sie im Namen (a [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) kann Inhalte im Namen eines anderen Community-Mitglieds erstellen)
* [In-Kontext- und Massenmoderation](/help/communities/moderate-ugc.md) von Blogartikeln und Kommentaren

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Blog-Funktion zu einer AEM Site
* Konfigurationseinstellungen für Blogkomponenten

>[!NOTE]
>
>Die Komponenten `Journal` und `Journal Sidebar` werden `Blog` und `Blog Sidebar`.
>
>Die Blogfunktion in AEM 6.0 und früheren Versionen wurde entfernt. Sie basierte auf einer Vorlage und erlaubte es Autoren nur, Inhalte in der Autorenumgebung zu erstellen.

## Hinzufügen von Blog-Komponenten zu einer Seite {#adding-blog-components-to-a-page}

Wenn Sie im Autorenmodus einen Blog zu einer Seite hinzufügen möchten, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Blog`
* `Communities / Blog Sidebar`

Ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der der Blog erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](/help/communities/blog-developer-basics.md#essentials-for-client-side) enthalten sind, wird die `Blog` -Komponente wird wie folgt angezeigt:

![add-blog-component](assets/add-blog-component.png)

### Blog konfigurieren {#configuring-blog}

Auswählen der platzierten `Blog` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

![Blog-Einstellungen](assets/blog-configure.png)

#### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Unter dem **Einstellungen** -Registerkarte die grundlegenden Funktionen des Blogs festlegen:

* **Miniaturansicht des Anhangs zulassen**

  Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Maximale Größe der Miniaturansichten anhängen**

  Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Mindestbildgröße für Miniaturansichten**

  Mindestgröße (in Byte) des Bildes zum Generieren von Miniaturansichten für Inline-Bilder. Der Standardwert ist 100000 Bytes (100 KB).

* **Maximale Größe der Miniaturansichten**

  Maximale Größe (in Pixel) des Miniaturbilds für Inline-Bilder. Der Standardwert ist 800 x 800.

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Zugelassene berechtigte Mitglieder**

  Fügen Sie die berechtigten Mitglieder hinzu, die Inhalte erstellen dürfen.

* **Blockieren benutzergenerierter Inhalte im Bearbeitungsmodus des Autors**

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

  Definiert die Anzahl der Blogeinträge/Kommentare, die pro Seite angezeigt werden. Der Standardwert lautet 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss das Posten von Blogeinträgen und Kommentaren genehmigt werden, bevor sie auf einer veröffentlichten Site erscheinen. Die Standardeinstellung ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, ist der Blog für neue Blog-Einträge und Kommentare geschlossen. Die Option Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Blogeinträge und Kommentare mit Markup eingegeben werden. Die Option Standard ist aktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe **Tag-Feld** Registerkarte). Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Sie einem Blogeintrag oder Kommentar Dateianlagen hinzufügen. Die Option Standard ist deaktiviert.

* **Maximale Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, können nicht angegebene Dateitypen nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

  Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

  Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die auf den Blogeintrag gepostet wurden. Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, fügen Sie die Funktion Abstimmung in einen Blogeintrag ein. Die Option Standard ist deaktiviert.

* **Benutzern das Löschen von Kommentaren und Themen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Blogeinträge löschen, die sie veröffentlicht haben. Die Option Standard ist deaktiviert.

* **Folgende erlauben**

  Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder [benachrichtigt](/help/communities/notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](/help/communities/subscriptions.md)). Erfordert `Allow Following` zu überprüfen und [E-Mail konfiguriert](/help/communities/email.md). Die Option Standard ist deaktiviert.

* **Anzeigemarken**

  Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds. Die Option Standard ist deaktiviert.

* **Antworten auf Listenseite nicht abrufen**

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, wird die Idee als [präsentierte Inhalte](/help/communities/featured.md). Die Option Standard ist deaktiviert.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (unter Verwendung von Vorname, Nachname, Benutzername) identifizieren und sie mit der gemeinsamen Syntax @user-name versehen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre eigenen Erwähnungen.

* **Max. Erwähnungen**

  Schränken Sie die maximale Anzahl der Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **Benutzeroberflächen-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag mit Tags zu versehen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **Benutzermoderation** -Registerkarte die Moderationseinstellungen angeben:

* **Posts verweigern**

  Wenn diese Option aktiviert ist, dürfen Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Option Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Die Option Standard ist deaktiviert.

* **Posts kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste der Kennzeichnungsgründe**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

  Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Schwellenwert für Moderation**

  Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **Kennzeichnungslimit**

  Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 festgelegt ist, wird das gekennzeichnete Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Unter dem **Tag-Feld** Registerkarte angeben, welche Tags angewendet werden können, wenn **Tagging zulassen** auf der **Einstellungen** tab :

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` wird unter dem **Einstellungen** Registerkarte. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) und &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **Empfehlungslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert -1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

### Konfigurieren der Blog-Seitenleiste {#configuring-blog-sidebar}

Wenn Sie auf die `Blog Sidebar` -Komponente ein Dialogfeld zum Bearbeiten geöffnet.

Unter dem **Journal-Seitenleisten-Einstellungen** -Registerkarte das Datumsformat für Archive angeben und angeben, welche Art von Einträgen in der Seitenleiste angezeigt werden sollen:

![blog-component-sidebar](assets/blog-component-sidebar.png)

* **Datumsformat**

  Das Format, das zur Anzeige für Archive von Blogeinträgen verwendet wird. Das Format verwendet Platzhalter, die der Java™-Konvention folgen.

   * jjjj : vollständiges Jahr, z. B. &quot;2015&quot;
   * yy : kurze Jahreszahl, z. B. &#39;15&#39;
   * MMMMM : Vollmonat, z. B. Juni
   * MMM : kurzer Monat, wie Juni
   * MM : Monatsnummer, z. B. 06

  Der Standardwert ist &quot;jjjj MMMMM&quot;, der beispielsweise &quot;Juni 2015&quot;anzeigen würde.

* **Ansichtstyp**

  Der Titel und der Typ der in der Seitenleiste anzuzeigenden Blogeinträge. Die Wahl liegt zwischen

   * Autoren
   * Kategorien
   * Archive

* **Blog-Komponentenpfad**

  *(Optional)* Der Speicherort der Blog-Ressource, von der aus Blog-Artikel aufgelistet werden sollen. Wenn dieses Feld leer gelassen wird, wird die Komponente resourceType verwendet. `social/journal/components/hbs/journal` wird auf derselben Seite angezeigt.

   * Beispiel: `/content/sites/engage/en/blog/jcr:content/content/primary/blog`

* **Empfehlungslimit**

  Die Anzahl der anzuzeigenden Blogartikel. Der Wert -1 bedeutet keine Begrenzung. Der Standardwert ist -1.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung zeigt die Blogfunktion den neuesten Blogartikel gefolgt von älteren Blogartikeln in absteigender Reihenfolge der Erstellung an. Blog-Seitenleisten ermöglichen es Site-Besuchern, Filter anzuwenden, um die Auswahl der angezeigten Blog-Artikel zu beschränken.

Dem Blogartikel folgt ein Link zum Posten oder Anzeigen von Kommentaren.

Wenn ein Blogartikel ausgewählt ist, werden der Blogartikel und die Kommentare angezeigt (sofern aktiviert).

Andere Möglichkeiten hängen davon ab, ob der Besucher der Site Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonym ist.

### Arbeiten mit Artikeln {#working-with-articles}

Beim Erstellen eines Blogartikels haben Sie folgende Möglichkeiten:

1. Sofort veröffentlichen
1. Entwurf veröffentlichen
1. An einem geplanten Datum und zu einer geplanten Uhrzeit veröffentlichen

Die Blogartikel werden auf der entsprechenden Registerkarte (Veröffentlicht, Entwürfe oder Geplant) für Mitglieder angezeigt, die in der Lage sind, sie in der Veröffentlichungsumgebung zu erstellen.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorberechtigungen verfügt, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) (wie durch die Konfiguration der Komponente erlaubt) auf allen Blogartikeln und Kommentaren, die in einem Blog veröffentlicht werden.

![moderator-homepage](assets/moderator-homepage.png)

#### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied ist oder [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) (je nach Konfiguration) können sie `New Article` , um einen neuen Blogartikel zu erstellen und zu posten.

Insbesondere können sie:

* Erstellen eines Blogartikels
* Posten eines neuen Blogartikels im Namen eines anderen Mitglieds
* Posten eines Kommentars zu einem Blogartikel
* Bearbeiten eigener Blogartikel oder Kommentare
* Löschen eigener Blogartikel oder Kommentare
* Kennzeichnen von Blogartikeln oder Kommentaren anderer Benutzer

![member-homepage](assets/member-homepage.png)

![create-blog](assets/create-blog.png)

#### Anonym {#anonymous}

Besucher der Website, die nicht angemeldet sind, dürfen nur veröffentlichte Blogartikel und Kommentare lesen, sie übersetzen, falls unterstützt, aber keine Blog-Artikel oder -Kommentare hinzufügen oder die Artikel oder Kommentare anderer kennzeichnen.

![anonymous-user-view](assets/anonymous-user-view.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Blog-Grundlagen](/help/communities/blog-developer-basics.md) -Seite für Entwickler.

Informationen zur Moderation von Blogeinträgen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von Blogeinträgen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von Blogeinträgen und Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
