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
source-git-commit: 9e941ce092f7d3248c11886d6bf1e54f2e726362
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 38%

---


# Funktion „Forum“{#forum-feature}

## Einführung {#introduction}

Die Forumsfunktion bietet einen Bereich, in dem angemeldete Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung Folgendes tun können:

* Erstellen neuer Themen
* Ansicht und Beantwortung von Themen
* Thema
* Forum suchen
* Hilfe beim Moderieren des Foruminhalts
* Verschieben von Forumthemen von einer Seite auf eine andere

Dieser Abschnitt der Dokumentation beschreibt:

* Hinzufügen der Forumsfunktion zu einer AEM-Site.
* Configuration settings for the `Forum` component.

### Hinzufügen eines Forums zu einer Seite {#adding-a-forum-to-a-page}

To add a `Forum` component to a page in author mode, use the component browser to locate

* `Communities / Forum`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite, auf der das Forum angezeigt werden soll.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/essentials-forum.md#essentials-for-client-side) are included, this is how the `Forum` component will appear:

![chlimage_1-60](assets/chlimage_1-60.png)

### Konfigurieren eines Forums {#configuring-a-forum}

Select the placed `Forum` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-61](assets/chlimage_1-61.png)

![forum-config](assets/forum-config.png)

#### Registerkarte „Settings“{#settings-tab}

Legen Sie auf der Registerkarte **Einstellungen** die Einstellungen für Themen und Antworten fest:

* **Anhangminiatur zulassen**

   Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Anhangminiaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds der Anlage. Der Standardwert ist 800 x 800.

* **Min. Bildgröße für Miniaturansichten**
* **Max. Miniaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds für Inline-Bild. Der Standardwert ist 800 x 800.

* **Themen pro Seite**

   Legt fest, wie viele Themen/Posts pro Seite angezeigt werden. Der Standardwert ist 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungssite angezeigt werden. Diese Option ist standardmäßig deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, wird das Forum für neue Themen und Kommentare geschlossen. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **Tagging zulassen**

   If checked, allow members to add tag labels to their post (see **Tag field** tab). Diese Option ist standardmäßig deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass dem Thema oder Kommentar Dateianlagen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Forenthemen an den Anfang der Liste der Themen gebunden werden. Diese Option ist standardmäßig deaktiviert.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [spezieller Inhalt](/help/communities/featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern per E-Mail ([Abonnement](/help/communities/subscriptions.md)) eine Benachrichtigung über neue Beiträge erlauben. Muss überprüft `Allow Following` und [E-Mail konfiguriert](/help/communities/email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Max. Größe** der Bilddatei anhängen ist nur relevant, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option aktiviert ist, können Sie Antworten auf Kommentare zulassen, die zum Thema gepostet wurden. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die Funktion &quot;Abstimmung&quot;in ein Thema ein. Diese Option ist standardmäßig deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, die von ihnen veröffentlichten Kommentare und Themen zu löschen. Diese Option ist standardmäßig deaktiviert.

* **Breadcrumbs anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie Navigationsbreadcrumbs auf Themenseiten an. Diese Option ist standardmäßig aktiviert.

* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur Privilegierte Mitglieder Inhalte erstellen.

* **Zugelassene privilegierte Mitglieder**

   Hinzufügen die privilegierten Mitglieder, die Inhalte erstellen dürfen.

* **Benutzergenerierte Inhalte im Autoren-Bearbeitungsmodus blockieren**

   Wenn diese Option aktiviert ist, wird der vom Benutzer erstellte Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **Erwähnung aktivieren**

   Wenn diese Option aktiviert ist, können Benutzer der registrierten Community andere registrierte Mitglieder identifizieren (mit Vorname, Nachname, Benutzername) und sie mit einem Tag versehen, das die übliche @user-name-Syntax verwendet. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

   Schränken Sie die maximale Anzahl an Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

   Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@Erwähnung). Beispiel `~{{familyName}}{{givenName}}`.

>[!NOTE]
>
>Es kann erforderlich sein, Kommentare zu einem Thema sowohl zu prüfen `AllowThreaded Replies` als auch `Allow users to Delete Comments and Topics` zu aktivieren.


#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Under the **User Moderation** tab, specify how the posted topics and replies (user generated content) are managed. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Posts ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge verweigern und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren mit vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Änderungen und Kommentare vorzunehmen, und ein Thema erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **Themen verschieben**

   Wenn diese Option aktiviert ist, können Sie Moderatoren auf der Seite der Veröffentlichung das Verschieben von Themen zulassen. Diese Option ist standardmäßig aktiviert.

* **Posts kennzeichnen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, die Themen oder Kommentare anderer als unangemessen zu kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können die Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie ein Thema oder einen Kommentar als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen einzugeben. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Thema oder Kommentar markiert werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Auf der Registerkarte **Tag-Feld** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **Einstellungen** aktiviert) verwendet werden können.

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` unter der Registerkarte **Einstellungen** markiert wurde. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namensraum umfasst &quot;Standard-Tags&quot;(den standardmäßigen Namensraum) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Standardwert ist **-**1 (keine Beschränkungen).

#### Registerkarte &quot;Übersetzung&quot; {#translation-tab}

Auf der Registerkarte **Übersetzung** können Sie festlegen, ob bei für die Community-Site aktivierter Übersetzungsoption der gesamte Thread oder nur bestimmte Posts übersetzt werden sollen.

* **Alles übersetzen**

   Wenn diese Option aktiviert ist, wird der Forum-Thread in die bevorzugte Sprache des Benutzers übersetzt. Diese Option ist standardmäßig deaktiviert.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie auf der Registerkarte &quot; **Sortiereinstellungen** &quot;an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfolge**

   Aktivieren Sie alle zulässigen Sortierungsoptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

   Ziehen Sie nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden soll. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

   Ziehen Sie nach unten, um eine der folgenden Optionen auszuwählen: `All, Last 24 Hours, Last 7 Days, Last 30 Days`.

   Der Standardwert ist `All`.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Forumsgrundlagen](/help/communities/essentials-forum.md).

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von veröffentlichten Themen und Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
