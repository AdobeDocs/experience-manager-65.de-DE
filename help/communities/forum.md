---
title: Forumsfunktion
description: Erfahren Sie, wie Sie die Forumsfunktion hinzufügen und konfigurieren, die angemeldeten Community-Mitgliedern einen Bereich bietet, in dem sie Themen erstellen, anzeigen, folgen, suchen oder beantworten können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2b1a4917-9db6-436a-a5fd-c102fe41fb9d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 2%

---

# Forumsfunktion{#forum-feature}

## Einführung {#introduction}

Die Forumsfunktion bietet angemeldeten Site-Besuchern (Community-Mitgliedern) in der Publish-Umgebung folgende Möglichkeiten:

* Erstellen von Themen
* Themen anzeigen und beantworten
* Thema folgen
* Forum durchsuchen
* Moderieren von Forumsinhalten
* Verschieben von Forumthemen von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Forumsfunktion zu einer AEM Site.
* Konfigurationseinstellungen für die Komponente `Forum` .

### Hinzufügen eines Forums zu einer Seite {#adding-a-forum-to-a-page}

Möchten Sie im Autorenmodus einer Seite die Komponente `Forum` hinzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Forum`

Ziehen Sie es an die gewünschte Stelle auf einer Seite, auf der das Forum erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/essentials-forum.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Forum` wie folgt angezeigt:

![forum-component](assets/forum-component.png)

### Konfigurieren eines Forums {#configuring-a-forum}

Wählen Sie die platzierte Komponente `Forum` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![forum-config](assets/forum-config.png)

#### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Legen Sie auf der Registerkarte **Einstellungen** Einstellungen für Themen und Antworten fest:

* **Zulassen der Anlagenminiatur**

  Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Größe der Miniaturansichten anhängen**

  Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Min. Bildgröße für Miniatur**
* **Maximale Größe der Miniaturansichten**

  Maximale Größe (in Pixel) des Miniaturbilds für Inline-Bilder. Der Standardwert ist 800 x 800.

* **Themen pro Seite**

  Legt fest, wie viele Themen/Posts pro Seite angezeigt werden. Der Standardwert ist 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen können. Die Option Standard ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, können im Forum keine neuen Themen und Kommentare erstellt werden. Die Option Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld** ). Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können dem Thema oder Kommentar Dateianlagen hinzugefügt werden. Die Option Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Die Option Standard ist deaktiviert.

* **Ping zulassen**

  Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste gesetzt werden. Die Option Standard ist deaktiviert.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, kann die Idee als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert werden. Die Option Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge benachrichtigt werden ([subscription](/help/communities/subscriptions.md)). Erfordert die Überprüfung von `Allow Following` und die Konfiguration von [E-Mail](/help/communities/email.md). Die Option Standard ist deaktiviert.

* **Maximale Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, können nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Max. Größe der Bilddatei anhängen**
Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **Ermöglichen von gefilterten Antworten**

  Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zum Thema gepostet wurden. Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, fügen Sie die Abstimmungsfunktion in ein Thema ein. Die Option Standard ist deaktiviert.

* **Benutzern erlauben, Kommentare und Themen zu löschen**

  Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Themen löschen. Die Option Standard ist deaktiviert.

* **Breadcrumbs anzeigen**

  Wenn diese Option aktiviert ist, zeigen Sie Navigations-Breadcrumbs auf Themenseiten an. Die Option Standard ist aktiviert.

* **Anzeigemarke**

  Wenn diese Option aktiviert ist, zeigen Sie verdiente und zugewiesene [Badges](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds an. Die Option Standard ist deaktiviert.

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Zulässige privilegierte Mitglieder**

  Fügen Sie die berechtigten Mitglieder hinzu, die Inhalte erstellen dürfen.

* **Blockieren benutzergenerierter Inhalte im Bearbeitungsmodus für Autoren**

  Wenn diese Option aktiviert ist, wird benutzergenerierter Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (unter Verwendung von Vorname, Nachname, Benutzername) identifizieren und sie mit der gemeinsamen Syntax @user-name versehen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

  Schränken Sie die maximale Anzahl der Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag mit Tags zu versehen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

>[!NOTE]
>
>Es kann erforderlich sein, sowohl `AllowThreaded Replies` als auch `Allow users to Delete Comments and Topics` zu überprüfen, um Kommentare zu einem Thema zu aktivieren.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation** an, wie die veröffentlichten Themen und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Posts verweigern**

  Wenn diese Option aktiviert ist, dürfen Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Option Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Die Option Standard ist deaktiviert.

* **Verschieben von Themen**

  Wenn diese Option aktiviert ist, können Moderatoren auf der Veröffentlichungsseite Themen verschieben. Die Option Standard ist aktiviert.

* **Posts kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste mit Kennzeichnungsgründen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

  Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

  Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 festgelegt ist, wird das gekennzeichnete Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Auf der Registerkarte **Tag-Feld** sind die Tags, die angewendet werden können, sofern sie auf der Registerkarte **Einstellungen** zulässig sind, entsprechend den ausgewählten Namespaces beschränkt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) und &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **Empfehlungslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Standardwert ist **-**1 (keine Beschränkungen).

#### Tab &quot;Übersetzung&quot; {#translation-tab}

Wenn auf der Registerkarte **Übersetzung** die Übersetzung für die Community-Site aktiviert ist, kann die Übersetzung so eingestellt werden, dass das gesamte Thema oder ausgewählte Beiträge übersetzt werden.

* **Alle übersetzen**

  Wenn diese Option aktiviert ist, wird der Forum-Thread in die bevorzugte Sprache des Benutzers übersetzt. Die Option Standard ist deaktiviert.

#### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Geben Sie auf der Registerkarte **Sortiereinstellungen** an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortieren nach**

  Aktivieren Sie alle zulässigen Sortieroptionen : `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

  Ziehen Sie den Mauszeiger nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für die Analytics-Sortierung auswählen**

  Ziehen Sie die Maus nach unten, um eine der folgenden Optionen auszuwählen: `All, Last 24 Hours, Last 7 Days, Last 30 Days`.

  Der Standardwert ist `All`.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Forumsgrundlagen](/help/communities/essentials-forum.md) .

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von veröffentlichten Themen und Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
