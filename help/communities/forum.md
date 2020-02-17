---
title: Funktion „Forum“
seo-title: Funktion „Forum“
description: Hinzufügen und Konfigurieren der Forumsfunktion
seo-description: Hinzufügen und Konfigurieren der Forumsfunktion
uuid: e69be4e1-c9d5-4d51-8e7e-609e5460e378
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d936cef5-ad76-482d-97bf-c40137185812
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Funktion „Forum“{#forum-feature}

## Einführung {#introduction}

Die Forumsfunktion bietet einen Bereich, in dem angemeldete Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung Folgendes tun können:

* Erstellen neuer Themen
* Einsehen von und Reagieren auf Themen
* Verfolgen eines Themas
* Durchsuchen eines Forums
* Unterstützung bei der Moderation der Forumsinhalte
* Verschieben von Forumsthemen von einer Seite auf eine andere

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Forumsfunktion zu einer AEM-Site
* Konfigurationseinstellungen für die Komponente `Forum`

### Hinzufügen eines Forums zu einer Seite {#adding-a-forum-to-a-page}

To add a `Forum` component to a page in author mode, use the component browser to locate

* `Communities / Forum`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite, auf der das Forum angezeigt werden soll.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/essentials-forum.md#essentials-for-client-side) are included, this is how the `Forum`component will appear :

![chlimage_1-104](assets/chlimage_1-104.png)

### Konfigurieren eines Forums {#configuring-a-forum}

Select the placed `Forum` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-105](assets/chlimage_1-105.png) ![forum-config](assets/forum-config.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie unter der Registerkarte **Einstellungen **Einstellungen für Themen und Antworten Einstellungen an:

* **Miniaturansicht der Anlage zulassen**Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.
* **Maximale Größe** der Miniaturansicht der Anlage (in Pixel). Der Standardwert ist 800 x 800.

* **Min. Bildgröße für Miniaturansichten**
* **Maximale Größe** der Miniaturansicht des Inline-Bildes (in Pixel). Der Standardwert ist 800 x 800.

* **Themen pro Seite**Definiert die Anzahl der Themen/Beiträge pro Seite. Der Standardwert ist 10.
* **Moderiert** Ist diese Option aktiviert, müssen Themen zunächst genehmigt werden, bevor sie öffentlich zugänglich gemacht werden. Diese Option ist standardmäßig deaktiviert.

* **Geschlossen** Ist diese Option aktiviert, können im Forum keine neuen Themen und Kommentare erstellt werden. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor** Ist diese Option aktiviert, können Themen und Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **Tagging zulassen** Ist diese Option aktiviert, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld**). Diese Option ist standardmäßig deaktiviert.

* **Datei-Uploads zulassen** Ist diese Option aktiviert, können Themen oder Kommentaren Dateien hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Zulassen** Wenn diese Option aktiviert ist, fügen Sie folgende Funktion für Forumbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **Veröffentlichen** zulassen Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste eingefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Wenn Sie** die Option &quot;Vorgestellte Inhalte zulassen&quot;aktivieren, kann die Idee als [speziellen Inhalt](/help/communities/featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **E-Mail-Abonnements** zulassen Wenn diese Option aktiviert ist, erlauben Sie Mitgliedern, über neue Beiträge per E-Mail ([Abonnement](/help/communities/subscriptions.md)) benachrichtigt zu werden. Muss überprüft `Allow Following` und [E-Mail konfiguriert](/help/communities/email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße** Relevant nur, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen** Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass** **alle Dateitypen zulässig sind.

* **Max. Größe** der Bilddatei anhängen ist nur relevant, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152****(2 MB).

* **Antworten mit Diskussionsfaden zulassen** Ist diese Option aktiviert, können Kommentare zum Thema hinterlassen werden. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Themen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen** Ist diese Option aktiviert, können Mitglieder von ihnen veröffentlichte Kommentare und Themen löschen. Diese Option ist standardmäßig deaktiviert.

* **Breadcrumbs anzeigen** Ist diese Option aktiviert, werden Breadcrumbs für die Navigation auf den Themenseiten eingeblendet. Diese Option ist standardmäßig aktiviert.

* **Anzeigen von Abzeichen** Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **Privilegierte Mitglieder** zulassen Wenn diese Option aktiviert ist, dürfen nur Privilegierte Mitglieder Inhalte erstellen.

* **Zulässige privilegierte Mitglieder**Fügen Sie die privilegierten Mitglieder hinzu, die Inhalte erstellen dürfen.
* **Blockieren benutzergenerierter Inhalte im Bearbeitungsmodus**&quot;Autor&quot;Blockieren Sie,wenn diese Option aktiviert ist, beim Bearbeiten im Autorenmodus den vom Benutzer erstellten Inhalt.

* **Erwähnung** aktivieren Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder identifizieren (unter Verwendung von Vorname, Nachname, Benutzername) und sie mit der gemeinsamen @user-name-Syntax markieren. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**: Die maximale Anzahl an Erwähnungen, die in einem Beitrag zulässig sind, beschränken. Der Standardwert ist 10.

* **Benutzeroberflächenbeschreibungsmuster** Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@Erwähnung). Beispiel `~{{familyName}}{{givenName}}`.

>[!NOTE]
>
>Es kann erforderlich sein, Kommentare zu einem Thema sowohl zu prüfen `AllowThreaded Replies` als auch `Allow users to Delete Comments and Topics` zu aktivieren.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation **an, wie die veröffentlichten Themen und Antworten (vom Benutzer erstellte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Posts ablehnen** Ist diese Option aktiviert, können moderierende Mitglieder Beiträge ablehnen und so verhindern, dass diese im Forum veröffentlicht werden. Diese Option ist standardmäßig deaktiviert.

* **Themen schließen/erneut öffnen** Ist diese Option aktiviert, können moderierende Mitglieder Themen für die weitere Bearbeitung oder Kommentare schließen oder bereits geschlossene Themen erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **Themen** verschieben Wenn diese Option aktiviert ist, können Sie Moderatoren auf der Veröffentlichungsseite das Verschieben von Themen zulassen. Diese Option ist standardmäßig aktiviert.

* **Posts kennzeichnen** Ist diese Option aktiviert, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Liste mit Kennzeichnungsgründen** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Thema oder ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Themen oder Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation** Geben Sie an, wie oft ein Thema oder ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit** Geben Sie an, wie oft ein Thema oder ein Kommentar als unangemessen gekennzeichnet werden muss, bevor es oder er aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Under the **Tag field** tab, the tags which may be applied, if allowed under the **Settings **tab, are limited according to namespaces chosen.

* **Zulässige Namespaces** Relevant, wenn sie unter der Registerkarte **Einstellungen **markiert `Allow Tagging` sind. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Der Standardwert ist **-**1 (keine Beschränkungen).

#### Registerkarte &quot;Übersetzung&quot; {#translation-tab}

Wenn die Übersetzung für die Community-Site aktiviert ist, kann unter der Registerkarte **Übersetzung **die Übersetzung auf das gesamte Thema oder ausgewählte Beiträge eingestellt werden.

* **Alles übersetzen** Ist diese Option aktiviert, wird der Forums-Thread in die Sprache des Benutzers übersetzt. Diese Option ist standardmäßig deaktiviert.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie unter der Registerkarte **Sortiereinstellungen **an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortieren nach** Aktivieren aller zulässigen Sortierungsoptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard**-Pulldown festlegen, um eine der aktivierten Sortieroptionen als Standard festzulegen. Der Standardwert ist `Newest`.

* **Wählen Sie die Zeitoptionen für die Analytics-Sortierung** Pulldown aus, um eine von `All, Last 24 Hours, Last 7 Days, Last 30 Days`auszuwählen. Der Standardwert ist `All`.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Forumsgrundlagen](/help/communities/essentials-forum.md).

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von veröffentlichten Themen und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
