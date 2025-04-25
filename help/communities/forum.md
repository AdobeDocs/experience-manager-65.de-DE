---
title: Forenfunktion
description: Erfahren Sie, wie Sie die Forenfunktion hinzufügen und konfigurieren, die angemeldeten Community-Mitgliedern einen Bereich zum Erstellen, Anzeigen, Verfolgen, Suchen oder Antworten auf Themen bereitstellt.
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

# Forenfunktion{#forum-feature}

## Einführung {#introduction}

Die Forenfunktion bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Publish-Umgebung, um:

* Erstellen von Themen
* Themen anzeigen und beantworten
* Einem Thema folgen
* Forum durchsuchen
* Helfen Sie, den Foreninhalt zu moderieren
* Verschieben von Forenthemen von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Forenfunktion zu einer AEM-Site.
* Konfigurationseinstellungen für die `Forum`.

### Hinzufügen eines Forums zu einer Seite {#adding-a-forum-to-a-page}

Um einer Seite im Autorenmodus eine `Forum` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach

* `Communities / Forum`

Und ziehen Sie es auf eine Seite, auf der das Forum erscheinen soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen ](/help/communities/essentials-forum.md#essentials-for-client-side) enthalten sind, wird die `Forum` Komponente wie folgt angezeigt:

![forum-component](assets/forum-component.png)

### Konfigurieren eines Forums {#configuring-a-forum}

Wählen Sie die platzierte `Forum` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

![forum-config](assets/forum-config.png)

#### Registerkarte „Einstellungen“ {#settings-tab}

Geben Sie auf **Registerkarte** Einstellungen“ Einstellungen für Themen und Antworten an:

* **Miniaturansicht für Anhänge zulassen**

  Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Größe für Miniaturansichten anhängen**

  Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Minimale Bildgröße für Miniaturansicht**
* **Maximale Größe von Miniaturansichten**

  Maximale Größe (in Pixeln) des Miniaturbilds für Inline-Bild. Der Standardwert ist 800 x 800.

* **Themen pro Seite**

  Legt fest, wie viele Themen/Posts pro Seite angezeigt werden. Der Standardwert ist 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden können. Standard ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, wird das Forum für neue Themen und Kommentare geschlossen. Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Standard ist deaktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Labels hinzufügen (siehe **Tag-Feld** Registerkarte). Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können Dateianhänge zum Thema oder Kommentar hinzugefügt werden. Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, wird folgende Funktion für Forumsbeiträge hinzugefügt, mit der Mitglieder über neue Beiträge [ werden ](/help/communities/notifications.md). Standard ist deaktiviert.

* **Anheften zulassen**

  Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste angeheftet werden. Standard ist deaktiviert.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option aktiviert ist, kann die Idee als [vorgestellter Inhalt“ identifiziert ](/help/communities/featured.md). Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder über neue Beiträge per E-Mail benachrichtigt werden [Abonnement](/help/communities/subscriptions.md). Erfordert, dass `Allow Following` überprüft und [E-Mail konfiguriert](/help/communities/email.md). Standard ist deaktiviert.

* **max. Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Punkttrennzeichen. Zum Beispiel .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, können die nicht angegebenen nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Max. Größe der angehängten Bilddatei**
Nur relevant, wenn Datei-Uploads zulassen aktiviert ist. Maximale Anzahl an Byte, die eine hochgeladene Bilddatei aufweisen darf. Der Standardwert ist 2097152 (2 MB).

* **Thread-Antworten zulassen**

  Wenn diese Option aktiviert ist, können Sie Antworten auf Kommentare zulassen, die zum Thema gepostet werden. Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, wird die Abstimmungsfunktion in ein Thema aufgenommen. Standard ist deaktiviert.

* **Benutzern das Löschen von Kommentaren und Themen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder die von ihnen geposteten Kommentare und Themen löschen. Standard ist deaktiviert.

* **Breadcrumbs anzeigen**

  Wenn diese Option aktiviert ist, werden Navigations-Breadcrumbs auf Themenseiten angezeigt. Die Standardeinstellung ist aktiviert.

* **Badges anzeigen**

  Wenn diese Option aktiviert ist, werden verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds angezeigt. Standard ist deaktiviert.

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Zulässige privilegierte Mitglieder**

  Fügen Sie die privilegierten Mitglieder hinzu, die Inhalte erstellen dürfen.

* **Blockieren von benutzergenerierten Inhalten im Authoring-Bearbeitungsmodus**

  Wenn aktiviert, blockiert benutzergenerierte Inhalte während der Bearbeitung im Autorenmodus.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (mit Vorname, Nachname, Benutzername) identifizieren und sie mit der allgemeinen @user-name-Syntax taggen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max Erwähnungen**

  Beschränken Sie die maximal zulässige Anzahl von Erwähnungen in einem Beitrag. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

>[!NOTE]
>
>Möglicherweise müssen sowohl `AllowThreaded Replies` als auch `Allow users to Delete Comments and Topics` überprüft werden, um Kommentare zu einem Thema zu aktivieren.

#### Registerkarte „Benutzermoderation“ {#user-moderation-tab}

Geben **auf der Registerkarte** Benutzermoderation) an, wie die veröffentlichten Themen und Antworten (benutzergenerierte Inhalte) verwaltet werden sollen. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Beiträge verweigern**

  Wenn diese Option aktiviert ist, dürfen Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder ein Thema für weitere Bearbeitungen und Kommentare schließen und ein Thema auch erneut öffnen. Standard ist deaktiviert.

* **Themen verschieben**

  Wenn diese Option aktiviert ist, können Moderatoren auf der Veröffentlichungsseite Themen verschieben. Die Standardeinstellung ist aktiviert.

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

Auf der Registerkarte **Tag** sind die Tags, die angewendet werden können, wenn dies auf der Registerkarte **Einstellungen** zulässig ist, entsprechend den ausgewählten Namespaces begrenzt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die Tags, die angewendet werden können, sind auf die innerhalb der geprüften Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst „Standard-Tags“ (den Standard-Namespace) und „Alle Tags einschließen“. Standardmäßig ist „Keine“ aktiviert, was bedeutet, dass alle Namespaces zulässig sind.

* **Vorschlagslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht. Der Standardwert ist **-**&#x200B;1 (keine Beschränkungen).

#### Registerkarte „Übersetzung“ {#translation-tab}

Wenn die Übersetzung für die Community **Site auf der Registerkarte Übersetzung** aktiviert ist, kann die Übersetzung so eingestellt werden, dass das gesamte Thema oder ausgewählte Beiträge übersetzt werden.

* **Alle übersetzen**

  Wenn diese Option aktiviert ist, wird der Forum-Thread in die bevorzugte Sprache des Benutzers übersetzt. Standard ist deaktiviert.

#### Registerkarte „Sortiereinstellungen“ {#sort-settings-tab}

Geben Sie auf **Registerkarte** Sortiereinstellungen“ an, wie die veröffentlichten Kommentare bei der Anzeige sortiert werden sollen.

* **Sortieren nach**

  Markieren Sie alle zulässigen Sortieroptionen : `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

  Wählen Sie aus der Dropdown-Liste eine der aktivierten Sortieroptionen aus, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für die Analytics-Sortierung auswählen**

  Wählen Sie eine der folgenden Optionen aus: `All, Last 24 Hours, Last 7 Days, Last 30 Days`.

  Der Standardwert ist `All`.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Forum Essentials](/help/communities/essentials-forum.md) für Entwickler.

Informationen zur Moderation geposteter Themen und Kommentare finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging geposteter Themen und Kommentare finden Sie [Tagging von benutzergenerierten Inhalten](/help/communities/tag-ugc.md).

Informationen zur Übersetzung geposteter Themen und Kommentare finden Sie unter [Übersetzen von benutzergenerierten Inhalten](/help/communities/translate-ugc.md).
