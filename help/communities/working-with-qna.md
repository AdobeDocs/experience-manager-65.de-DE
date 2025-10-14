---
title: Funktion für Fragen und Antworten im Forum
description: Erfahren Sie, wie Sie die Funktion „Ein Forum“ zu einer Seite hinzufügen, auf der angemeldete Community-Mitglieder Fragen stellen und beantworten können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 17081710-35e0-4f5b-9485-1f85c065fd70
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 1%

---

# Funktion für Fragen und Antworten im Forum{#q-a-forum-feature}

## Einführung {#introduction}

Die Funktion QnA (Questions and Answers)-Forum bietet Community-Mitgliedern einen Bereich, in dem sie Fragen stellen und beantworten können. Sie ermöglicht den Mitgliedern Folgendes:

* Fragen erstellen
* Hinzufügen von Inline-Bildern (mit Unterstützung für Drag &amp; Drop)
* Fragen anzeigen und beantworten
* Nach einer Frage suchen
* Hilfe bei der Moderation des QnA-Inhalts
* Ermitteln der besten Antworten
* QnA-Fragen von einer Seite auf eine andere verschieben

In der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Funktion „QnA-Forum“ zu einer AEM-Site.
* Konfigurationseinstellungen für die `QnA`Komponente.

## Hinzufügen eines Frage- und Antwortforums zu einer Seite {#adding-a-q-a-forum-to-a-page}

Um einer Seite im Autorenmodus eine `QnA` Komponente hinzuzufügen, verwenden Sie den Komponenten-Browser, um `Communities / QnA` zu finden, und ziehen Sie sie an die Position auf einer Seite, auf der das QnA-Forum angezeigt werden soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](/help/communities/qna-essentials.md#essentials-for-client-side) enthalten sind, wird die `QnA` Komponente wie folgt angezeigt:

![qna-component](assets/qna-component.png)

### Konfigurieren einer AA {#configuring-qna}

Wählen Sie die platzierte `QnA` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

![qna-config](assets/qna-config.png)

#### Registerkarte „Einstellungen“ {#settings-tab}

Geben Sie auf **Registerkarte** Einstellungen“ Einstellungen für Themen (Fragen) und Antworten (Antworten) an:

* **Miniaturansicht für Anhänge zulassen**

  Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Max. Größe für Miniaturansichten anhängen**

  Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Minimale Bildgröße für Miniaturansicht**

  Mindestgröße (in Byte) des Bildes zum Generieren der Miniaturansicht für Inline-Bilder. Der Standardwert ist 100000 Byte (100 KB).

* **Maximale Größe von Miniaturansichten**

  Maximale Größe (in Pixeln) des Miniaturbilds für Inline-Bild. Der Standardwert ist 800 x 800.

* **Themen pro Seite**

  Definiert die Anzahl der angezeigten Fragen/Beiträge pro Seite. Der Standardwert ist 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss das Posten von Themen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Die Auswahl von Standard ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, wird das Forum für neue Fragen und Kommentare geschlossen. Die Auswahl von Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Themen und Kommentare mit Markup eingegeben werden. Die Auswahl von Standard ist deaktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Labels hinzufügen (siehe **Tag-Feld** Registerkarte). Die Auswahl von Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können der Frage oder dem Kommentar Dateianhänge hinzugefügt werden. Die Auswahl von Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, wird folgende Funktion für Forumsbeiträge hinzugefügt, mit der Mitglieder über neue Beiträge [&#x200B; werden &#x200B;](/help/communities/notifications.md). Die Auswahl von Standard ist deaktiviert.

* **Anheften zulassen**

  Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste angeheftet werden. Die Auswahl von Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder über neue Beiträge per E-Mail benachrichtigt werden [Abonnement](/help/communities/subscriptions.md). Erfordert, dass „Zulassen“ aktiviert und [E-Mail konfiguriert](/help/communities/email.md) wird. Die Auswahl von Standard ist deaktiviert.

* **max. Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Punkttrennzeichen. Zum Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, können die nicht angegebenen nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass **alle**-Dateitypen zulässig sind.

* **Max. Größe der angehängten Bilddatei**

  Nur relevant, wenn Datei-Uploads zulassen aktiviert ist. Die maximale Anzahl von Byte, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

  Wenn diese Option aktiviert ist, können Sie Antworten auf Kommentare zu der Frage zulassen. Die Auswahl von Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, wird das Abstimmungsfeature in eine Frage eingefügt. Die Auswahl von Standard ist deaktiviert.

* **Benutzern das Löschen von Kommentaren und Themen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder ihre Kommentare und Fragen löschen. Die Auswahl von Standard ist deaktiviert.

* **Privilegierte Mitglieder zulassen**

  Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Blockieren von benutzergenerierten Inhalten im Authoring-Bearbeitungsmodus**

  Wenn aktiviert, blockiert benutzergenerierte Inhalte während der Bearbeitung im Autorenmodus.

* **Ausgewählte Antwort nach oben verschieben**

  Wenn diese Option aktiviert ist, wird als erste Antwort eine ausgewählte Antwort angezeigt. Die Auswahl von Standard ist deaktiviert.
* **Badges anzeigen**

  Wenn diese Option aktiviert ist, werden verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds angezeigt. Die Auswahl von Standard ist deaktiviert.

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option aktiviert ist, kann die Idee als [vorgestellter Inhalt“ identifiziert &#x200B;](/help/communities/featured.md). Die Auswahl von Standard ist deaktiviert.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (mit Vorname, Nachname, Benutzername) identifizieren und sie mit der allgemeinen @user-name-Syntax taggen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max Erwähnungen**

  Beschränken Sie die maximal zulässige Anzahl von Erwähnungen in einem Beitrag. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

#### Registerkarte „Benutzermoderation“ {#user-moderation-tab}

Geben Sie auf **Registerkarte** Benutzermoderation) an, wie die veröffentlichten Themen (Fragen) und Antworten (benutzergenerierte Inhalte) verwaltet werden sollen. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Antworten verweigern**

  Wenn diese Option aktiviert ist, dürfen Moderatoren vertrauenswürdiger Mitglieder gepostete Antworten ablehnen und verhindern, dass die Antworten im öffentlichen Frage- und Antwortforum angezeigt werden. Die Auswahl von Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder eine Frage (Thema) schließen, um sie weiter zu bearbeiten und zu beantworten, und auch eine Frage erneut öffnen. Die Auswahl von Standard ist deaktiviert.

* **Themen verschieben**
Wenn diese Option aktiviert ist, können Moderatoren auf Veröffentlichungsseite Fragen verschieben. Die Auswahl von Standard ist deaktiviert.

* **Flag-Posts**

  Wenn diese Option aktiviert ist, können Mitglieder Fragen oder Antworten anderer Personen als unangemessen kennzeichnen. Die Auswahl von Standard ist deaktiviert.

* **Verursacherliste kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem sie eine Frage oder Antwort als unangemessen kennzeichnen. Die Auswahl von Standard ist deaktiviert.

* **Grund für benutzerdefinierte Markierung**

  Wenn diese Option aktiviert ist, können Mitglieder ihren eigenen Grund für das Kennzeichnen einer Frage oder Antwort als unangemessen eingeben. Die Auswahl von Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft Mitglieder eine Frage oder Antwort markieren müssen, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungsgrenze**

  Geben Sie ein, wie oft eine Frage oder Antwort gekennzeichnet werden muss, bevor sie aus der öffentlichen Sicht ausgeblendet wird. Wenn auf -1 festgelegt, wird die markierte Frage oder Antwort nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für die Mäßigung sein. Der Standardwert ist 5.

#### Registerkarte „Tag-Feld“ {#tag-field-tab}

Auf der Registerkarte **Tag** sind die Tags, die angewendet werden können, wenn dies auf der Registerkarte **Einstellungen** zulässig ist, entsprechend den ausgewählten Namespaces beschränkt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die Tags, die angewendet werden können, sind auf die innerhalb der ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst „Standard-Tags“ (den Standard-Namespace) und „Alle Tags einschließen“. Standardmäßig ist „Keine“ aktiviert, was bedeutet, dass alle Namespaces zulässig sind.

* **Vorschlagslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht. Ein Wert von **-**&#x200B;1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

#### Registerkarte „Sortiereinstellungen“ {#sort-settings-tab}

Geben Sie auf **Registerkarte** Sortiereinstellungen“ an, wie die veröffentlichten Kommentare bei der Anzeige sortiert werden sollen.

* **Sortieren nach**

  Alle zulässigen Sortieroptionen überprüfen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

  Wählen Sie aus der Dropdown-Liste eine der aktivierten Sortieroptionen aus, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für die Analytics-Sortierung auswählen**

  Dropdown zur Auswahl eines der `All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Antworten identifizieren {#identifying-answers}

Eine Antwort kann mit der Schaltfläche `Select Answer` als richtige oder nützliche Antwort markiert werden. Wenn eine Frage als „Beantwortet“ markiert wurde, kann erst dann eine andere Antwort ausgewählt werden, wenn die Auswahl der ersten Antwort mithilfe der Schaltfläche `Unmark Chosen Answer` aufgehoben wurde.

Sobald dies als praktikable Antwort ausgewählt ist, kann die Auswahl mithilfe der Schaltfläche `Unmark Chosen Answer` aufgehoben werden.

Sobald eine Antwort als praktikable Antwort ausgewählt wurde, wird ein Hinweis darauf, dass die Frage `Answered` wurde, neben dem Fragethema auf der QnA-Hauptseite angezeigt.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorrechte verfügt, kann er die durch die Konfiguration der Komponente zulässigen Moderationsaufgaben ausführen, unabhängig davon, wer die Frage oder Antwort verfasst hat.

Sie können auch Antworten identifizieren.

#### Mitglieder {#members}

Wenn die Besuchenden der Site angemeldet sind, können sie je nach Konfiguration:

* Neue Frage posten.
* Fragen bearbeiten oder löschen, die sie verfasst haben.
* Markieren Sie Fragen oder Antworten anderer Mitglieder.
* Ermitteln von Antworten auf von ihnen verfasste Fragen.

#### Anonym {#anonymous}

Besucherinnen und Besucher der Website, die nicht angemeldet sind, können nur gepostete Fragen und Antworten lesen, diese übersetzen, falls sie unterstützt werden, aber weder eine Frage noch eine Antwort hinzufügen, noch Beiträge anderer Personen kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [QnA Essentials](/help/communities/qna-essentials.md) für Entwickler.

Informationen zur Moderation geposteter Themen und Kommentare finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging geposteter Themen und Kommentare finden Sie unter [Tagging von benutzergenerierten Inhalten](/help/communities/tag-ugc.md).
