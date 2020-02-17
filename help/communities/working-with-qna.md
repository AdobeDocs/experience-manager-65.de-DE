---
title: Funktion „Fragen-und-Antworten-Forum“
seo-title: Funktion „Fragen-und-Antworten-Forum“
description: Hinzufügen der Funktion des QnA-Forums zu einer Seite
seo-description: Hinzufügen der Funktion des QnA-Forums zu einer Seite
uuid: e0d95009-0d04-4fa7-8d05-5948c4e37f08
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 6e6ffe09-c50b-4238-8b8c-597c133d0a9e
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Funktion „Fragen-und-Antworten-Forum“{#q-a-forum-feature}

## Einführung {#introduction}

Das Forum-Feature QnA (Fragen und Antworten) bietet Community-Mitgliedern einen Raum, Fragen zu stellen und zu beantworten. Es ermöglicht Mitgliedern Folgendes:

* Neue Fragen erstellen
* Inline-Bilder hinzufügen (mit Unterstützung für Drag &amp; Drop)
* Fragen anzeigen und beantworten
* Nach einer Frage suchen
* Hilfe beim Moderieren des QnA-Inhalts
* Identifizieren Sie die besten Antworten.
* QnA-Fragen von einer Seite auf eine andere verschieben

Die Dokumentation beschreibt:

* Hinzufügen der Funktion „Fragen-und-Antworten-Forum“ zu einer AEM-Site.
* configuration settings for the `QnA`component.

## Hinzufügen eines Fragen-und-Antworten-Forums zu einer Seite {#adding-a-q-a-forum-to-a-page}

Um einer Seite im Autorenmodus eine `QnA` Komponente hinzuzufügen, verwenden Sie den Komponenten-Browser, um sie zu suchen `Communities / QnA`und auf eine Seite zu ziehen, auf der das QnA-Forum angezeigt werden soll.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/qna-essentials.md#essentials-for-client-side) are included, this is how the `QnA`component appears:

![chlimage_1](assets/chlimage_1.png)

### Konfigurieren von Fragen und Antworten {#configuring-qna}

Select the placed `QnA` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-1](assets/chlimage_1-1.png) ![qna-config](assets/qna-config.png)

#### Registerkarte „Settings“{#settings-tab}

Legen Sie auf der Registerkarte **Einstellungen** die Einstellungen für Themen (Fragen) und Antworten fest:

* **Anhangminiatur zulassen**

   Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Anhangminiaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds der Anlage. Der Standardwert ist 800 x 800.

* **Minimale Bildgröße für Miniaturansicht**

   Mindestgröße (in Byte) des Bildes für die Erstellung von Miniaturbildern für Inline-Bilder. Der Standardwert ist 100000 Byte (100 KB).

* **Max. Miniaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds für Inline-Bilder. Der Standardwert ist 800 x 800.

* **Themen pro Seite**

   Definiert die Anzahl der Fragen/Beiträge pro Seite. Der Standardwert ist 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungssite angezeigt werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, wird das Forum für neue Fragen und Kommentare geschlossen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **Tagging zulassen**

   If checked, allow members to add tag labels to their post (see **Tag field** tab). Die Option &quot;Standard&quot;ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass der Frage oder dem Kommentar Dateianlagen hinzugefügt werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Die Option &quot;Standard&quot;ist deaktiviert.

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste angefügt werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, per E-Mail über neue Beiträge informiert zu werden ([Abonnement](/help/communities/subscriptions.md)). Erfordert, dass Folgendes zugelassen und [E-Mail-Konfiguration](/help/communities/email.md)konfiguriert wird. Die Option &quot;Standard&quot;ist deaktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste mit Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, dürfen nicht angegebene nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass** **alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximale Anzahl von Bytes, die eine hochgeladene Bilddatei haben kann. Der Standardwert ist 2097152****(2 MB).

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, können Sie Antworten auf die zur Frage geposteten Kommentare zulassen. Die Option &quot;Standard&quot;ist deaktiviert.
* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, schließen Sie die Funktion &quot;Abstimmung&quot;mit einer Frage ein. Die Option &quot;Standard&quot;ist deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Fragen löschen. Die Standardeinstellung ist** **deaktiviert.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Benutzergenerierte Inhalte im Autoren-Bearbeitungsmodus blockieren**

   Wenn diese Option aktiviert ist, wird der vom Benutzer erstellte Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **Ausgewählte Antwort an den Anfang verschieben**Wenn aktiviert, ist die erste angezeigte Antwort eine ausgewählte Antwort. Die Option &quot;Standard&quot;ist deaktiviert.
* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Die Option &quot;Standard&quot;ist deaktiviert.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [spezieller Inhalt](/help/communities/featured.md)identifiziert werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **Erwähnung aktivieren**

   Wenn diese Option aktiviert ist, können Benutzer der registrierten Community andere registrierte Mitglieder identifizieren (mit Vorname, Nachname, Benutzername) und sie mit einem Tag versehen, das die übliche @user-name-Syntax verwendet. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

   Schränken Sie die maximale Anzahl an Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

   Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@Erwähnung). Beispiel: ~{{familyName}}{{vorname}}.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Under the **User Moderation** tab, specify how the posted topics (questions) and answers (user generated content) are managed. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Antworten verweigern**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern gepostete Antworten ablehnen und verhindern, dass die Antwort im öffentlichen Frage-und-Antwort-Forum angezeigt wird. Die Option &quot;Standard&quot;ist deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern eine Frage (Thema) schließen, um weitere Bearbeitungen und Antworten vorzunehmen, und eine Frage erneut öffnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Themen** verschieben Wenn diese Option aktiviert ist, können Sie Moderatoren auf Veröffentlichungsseite das Verschieben von Fragen zulassen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Posts kennzeichnen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, die Fragen oder Antworten anderer Personen als unangemessen zu kennzeichnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern in einer Dropdownliste gestatten, ihren Grund für die Kennzeichnung einer Frage oder Antwort als unangemessen auszuwählen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung einer Frage oder Antwort als unangemessen einzugeben. Die Option &quot;Standard&quot;ist deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft eine Frage oder Antwort von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft eine Frage oder Antwort markiert werden muss, bevor sie aus der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird die gekennzeichnete Frage oder Antwort nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Under the **Tag field** tab, the tags that can be applied, if allowed under the **Settings **tab, are limited according to namespaces chosen.

* **Zulässige Namespaces** Relevant, wenn sie unter der Registerkarte **Einstellungen **markiert `Allow Tagging` sind. Die Tags, die angewendet werden können, sind auf die Tags innerhalb der aktivierten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) und &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Der Wert **-**1 bedeutet keine Einschränkungen. Der Standardwert ist 0.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie auf der Registerkarte &quot; **Sortiereinstellungen** &quot;an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfolge**

   Aktivieren Sie alle zulässigen Sortieroptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

   Ziehen Sie nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden soll. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

   Wählen Sie aus einer Dropdown-Liste `All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Identifizieren von Antworten {#identifying-answers}

Eine Antwort kann mit der `Select Answer` Schaltfläche als richtige oder nützliche Antwort gekennzeichnet werden. Nachdem eine Frage als &quot;Beantwortet&quot;markiert wurde, kann erst eine andere Antwort ausgewählt werden, wenn die erste mit der `Unmark Chosen Answer`Schaltfläche deaktiviert wurde.

Nach Auswahl als brauchbare Antwort kann die Auswahl mithilfe der `Unmark Chosen Answer` Schaltfläche aufgehoben werden.

Sobald eine Antwort als praktikable Antwort ausgewählt wurde, wird auf der Hauptseite der QnA neben dem Fragethema ein Hinweis darauf angezeigt, dass die Frage angezeigt `Answered`wurde.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderatoren- oder Administrationsrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer die Frage oder Antwort verfasst hat.

Sie können auch Antworten identifizieren.

#### Mitglieder {#members}

Wenn die Besucher der Site angemeldet sind, können sie je nach Konfiguration:

* Veröffentlichen neuer Fragen.
* Bearbeiten oder Löschen selbst gestellter Fragen.
* Flag Fragen oder Antworten anderer Mitglieder.
* Antworten auf von ihnen erstellte Fragen zu finden.

#### Anonym {#anonymous}

Site-Besucher, die nicht angemeldet sind, können nur gepostete Fragen und Antworten lesen, sie übersetzen, wenn sie unterstützt werden, können aber weder eine Frage noch eine Antwort hinzufügen noch Beiträge anderer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

More information can be found on the [QnA Essentials](/help/communities/qna-essentials.md) page for developers.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
