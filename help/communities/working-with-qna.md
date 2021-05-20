---
title: Funktion „Fragen-und-Antworten-Forum“
seo-title: Funktion „Fragen-und-Antworten-Forum“
description: Hinzufügen der Funktion "Fragen und Antworten"zu einer Seite
seo-description: Hinzufügen der Funktion "Fragen und Antworten"zu einer Seite
uuid: e0d95009-0d04-4fa7-8d05-5948c4e37f08
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 6e6ffe09-c50b-4238-8b8c-597c133d0a9e
docset: aem65
exl-id: 17081710-35e0-4f5b-9485-1f85c065fd70
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1380'
ht-degree: 21%

---

# Funktion „Fragen-und-Antworten-Forum“{#q-a-forum-feature}

## Einführung {#introduction}

Das Forum-Feature Fragen und Antworten bietet Community-Mitgliedern die Möglichkeit, Fragen zu stellen und zu beantworten. Mitglieder können:

* Neue Fragen erstellen
* Inline-Bilder hinzufügen (mit Unterstützung für Drag &amp; Drop)
* Fragen anzeigen und beantworten
* Suchen nach Fragen
* Moderieren des QnA-Inhalts
* Identifizieren der besten Antworten
* Verschieben von Fragen zur Abfrage von einer Seite auf eine andere

Die Dokumentation beschreibt:

* Hinzufügen der Funktion &quot;Fragen und Antworten&quot;zu einer AEM Site.
* Konfigurationseinstellungen für die Komponente `QnA`.

## Hinzufügen eines Fragen-und-Antworten-Forums zu einer Seite {#adding-a-q-a-forum-to-a-page}

Um eine `QnA`-Komponente im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie im Komponenten-Browser nach `Communities / QnA` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das QnA-Forum angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/qna-essentials.md#essentials-for-client-side) enthalten sind, wird die Komponente `QnA` wie folgt angezeigt:

![qna-component](assets/qna-component.png)

### Konfigurieren von Fragen und Antworten {#configuring-qna}

Wählen Sie die platzierte Komponente `QnA` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

![qna-config](assets/qna-config.png)

#### Registerkarte „Settings“{#settings-tab}

Legen Sie auf der Registerkarte **Einstellungen** die Einstellungen für Themen (Fragen) und Antworten fest:

* **Anhangminiatur zulassen**

   Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Anhangminiaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Minimale Bildgröße für Miniaturansicht**

   Mindestgröße (in Byte) des Bildes zum Generieren von Miniaturansichten für Inline-Bilder. Der Standardwert ist 100000 Bytes (100 KB).

* **Max. Miniaturgröße**

   Maximale Größe (in Pixel) des Miniaturbilds für Inline-Bilder. Der Standardwert ist 800 x 800.

* **Themen pro Seite**

   Definiert die Anzahl der Fragen/Beiträge, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Option Standard ist deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, können im Forum keine neuen Fragen und Kommentare gestellt werden. Die Option Standard ist deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **Tagging zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld** ). Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können der Frage oder dem Kommentar Dateianlagen hinzugefügt werden. Die Option Standard ist deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder [benachrichtigt](/help/communities/notifications.md) über neue Beiträge werden können. Die Option Standard ist deaktiviert.

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste gesetzt werden. Die Option Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge benachrichtigt werden ([subscription](/help/communities/subscriptions.md)). Erfordert die Aktivierung von &quot;Folgende zulassen&quot;und [E-Mail-Konfiguration](/help/communities/email.md). Die Option Standard ist deaktiviert.

* **Max. Dateigröße**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, dürfen nicht angegebene nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Die maximale Anzahl von Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die auf die Frage gepostet wurden. Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die Funktion Abstimmung einer Frage hinzu. Die Option Standard ist deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Fragen löschen. Die Option Standard ist deaktiviert.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Benutzergenerierte Inhalte im Autoren-Bearbeitungsmodus blockieren**

   Wenn diese Option aktiviert ist, wird benutzergenerierter Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **Ausgewählte Antwort an den Anfang verschieben**

   Wenn diese Option aktiviert ist, ist die erste angezeigte Antwort eine ausgewählte Antwort. Die Option Standard ist deaktiviert.
* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie verdiente und zugewiesene [Badges](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds an. Die Option Standard ist deaktiviert.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [spezieller Inhalt](/help/communities/featured.md) identifiziert werden. Die Option Standard ist deaktiviert.

* **Erwähnung aktivieren**

   Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (unter Verwendung von Vorname, Nachname, Benutzername) identifizieren und sie mit der gemeinsamen Syntax @user-name versehen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

   Schränken Sie die maximale Anzahl der Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

   Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag mit Tags zu versehen (@mention). Beispiel: `~{{familyName}}{{givenName}}`.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation** an, wie die veröffentlichten Themen (Fragen) und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Antworten verweigern**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern gepostete Antworten ablehnen und verhindern, dass die Antwort im öffentlichen Frage- und beantwortet-Forum erscheint. Die Option Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder eine Frage (Thema) schließen, um weitere Bearbeitungen und Antworten vorzunehmen, und eine Frage erneut öffnen. Die Option Standard ist deaktiviert.

* **Themen verschiebenIst diese Option aktiviert, können Moderatoren auf Veröffentlichungsseite Fragen verschieben.**
Die Option Standard ist deaktiviert.

* **Posts kennzeichnen**

   Ist diese Option aktiviert, können Mitglieder Fragen oder Antworten anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Frage oder Antwort als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung einer Frage oder Antwort als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft eine Frage oder Antwort von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft eine Frage oder Antwort gekennzeichnet werden muss, bevor sie aus der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird die gekennzeichnete Frage oder Antwort nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot;{#tag-field-tab}

Auf der Registerkarte **Tag-Feld** sind die Tags, die angewendet werden können, sofern sie auf der Registerkarte **Einstellungen** zulässig sind, entsprechend den ausgewählten Namespaces beschränkt.

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) und &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert **-**1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

#### Registerkarte &quot;Sortiereinstellungen&quot;{#sort-settings-tab}

Geben Sie auf der Registerkarte **Sortiereinstellungen** an, wie die veröffentlichten Kommentare sortiert werden sollen, wenn sie angezeigt werden.

* **Sortierfolge**

   Aktivieren Sie alle zulässigen Sortieroptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

   Ziehen Sie den Mauszeiger nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

   Wählen Sie im Dropdown-Menü einen von `All, Last 24 Hours, Last 7 Days, Last 30 Days` aus. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Identifizieren von Antworten {#identifying-answers}

Eine Antwort kann mithilfe der Schaltfläche `Select Answer` als richtige oder nützliche Antwort markiert werden. Nachdem eine Frage als beantwortet markiert wurde, kann erst eine andere Antwort ausgewählt werden, nachdem die erste über die Schaltfläche `Unmark Chosen Answer` deaktiviert wurde.

Nach Auswahl als praktikable Antwort kann die Auswahl mithilfe der Schaltfläche `Unmark Chosen Answer` aufgehoben werden.

Nachdem eine Antwort als praktikable Antwort ausgewählt wurde, wird neben dem Fragethema auf der Hauptseite der Fragen ein Hinweis darauf angezeigt, dass die Frage `Answered` war.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderatoren- oder Administrationsrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer die Frage oder Antwort verfasst hat.

Sie können auch Antworten identifizieren.

#### Mitglieder {#members}

Wenn die Besucher der Site angemeldet sind, können sie je nach Konfiguration:

* Posten Sie eine neue Frage.
* Bearbeiten oder löschen Sie die von ihnen erstellten Fragen.
* Kennzeichnen Sie Fragen oder Antworten anderer Mitglieder.
* Ermitteln Sie Antworten auf von ihnen erstellte Fragen.

#### Anonym {#anonymous}

Besucher der Website, die nicht angemeldet sind, können nur veröffentlichte Fragen und Antworten lesen, sie übersetzen, sofern sie unterstützt werden. Sie können jedoch weder eine Frage hinzufügen noch eine Antwort hinzufügen oder Beiträge anderer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [QnA Essentials](/help/communities/qna-essentials.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
