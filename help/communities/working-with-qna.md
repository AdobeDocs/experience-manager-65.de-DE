---
title: Frage- und Forumsfunktion
description: Erfahren Sie, wie Sie die Funktion "Fragen-und-Antworten-Forum"zu einer Seite hinzufügen, auf der angemeldete Community-Mitglieder Fragen stellen und beantworten können.
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

# Frage- und Forumsfunktion{#q-a-forum-feature}

## Einführung {#introduction}

Das Forum-Feature Fragen und Antworten bietet Community-Mitgliedern die Möglichkeit, Fragen zu stellen und zu beantworten. Mitglieder können:

* Fragen erstellen
* Inline-Bilder hinzufügen (mit Unterstützung für Drag &amp; Drop)
* Fragen anzeigen und beantworten
* Suchen nach Fragen
* Moderieren des QnA-Inhalts
* Identifizieren der besten Antworten
* Verschieben von Fragen zur Abfrage von einer Seite auf eine andere

Die Dokumentation beschreibt:

* Hinzufügen der Funktion &quot;Fragen und Antworten&quot;zu einer AEM Site.
* Konfigurationseinstellungen für `QnA`-Komponente.

## Hinzufügen eines Fragen- und Verwaltungsforums zu einer Seite {#adding-a-q-a-forum-to-a-page}

So fügen Sie eine `QnA` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um `Communities / QnA` und ziehen Sie sie an die gewünschte Stelle auf einer Seite, auf der das Forum zur Frage der Antworten erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](/help/communities/qna-essentials.md#essentials-for-client-side) eingeschlossen sind, wird die `QnA` -Komponente angezeigt:

![qna-component](assets/qna-component.png)

### Konfigurieren von Fragen und Antworten {#configuring-qna}

Auswählen der platzierten `QnA` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

![qna-config](assets/qna-config.png)

#### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Unter dem **Einstellungen** Registerkarte Einstellungen für Themen (Fragen) und Antworten (Antworten) festlegen:

* **Miniaturansicht des Anhangs zulassen**

  Wenn diese Option aktiviert ist, wird eine Miniaturansicht des angehängten Bildes erstellt.

* **Maximale Größe der Miniaturansichten anhängen**

  Maximale Größe (in Pixel) des Miniaturbilds des Anhangs. Der Standardwert ist 800 x 800.

* **Mindestbildgröße für Miniaturansichten**

  Mindestgröße (in Byte) des Bildes zum Generieren von Miniaturansichten für Inline-Bilder. Der Standardwert ist 100000 Bytes (100 KB).

* **Maximale Größe der Miniaturansichten**

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

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe **Tag-Feld** Registerkarte). Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können der Frage oder dem Kommentar Dateianlagen hinzugefügt werden. Die Option Standard ist deaktiviert.

* **Folgende erlauben**

  Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumsbeiträge hinzu, mit der Mitglieder [benachrichtigt](/help/communities/notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **Zulassen von Pinnwänden**

  Wenn diese Option aktiviert ist, können Forumsthemen an den Anfang der Themenliste gesetzt werden. Die Option Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](/help/communities/subscriptions.md)). Erfordert, dass Folgendes aktiviert wird und [E-Mail konfiguriert](/help/communities/email.md). Die Option Standard ist deaktiviert.

* **Maximale Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, können nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass **all** -Dateitypen sind zulässig.

* **Maximale Dateigröße für Bildanhang**

  Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Die maximale Anzahl von Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

  Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die auf die Frage gepostet wurden. Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, fügen Sie die Funktion Abstimmung einer Frage hinzu. Die Option Standard ist deaktiviert.

* **Benutzern das Löschen von Kommentaren und Themen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Fragen löschen. Die Option Standard ist deaktiviert.

* **Zulassen von privilegierten Mitgliedern**

  Wenn diese Option aktiviert ist, dürfen nur privilegierte Mitglieder Inhalte erstellen.

* **Vom Benutzer generierte Inhalte im Bearbeitungsmodus des Autors blockieren**

  Wenn diese Option aktiviert ist, wird benutzergenerierter Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **Ausgewählte Antwort nach oben verschieben**

  Wenn diese Option aktiviert ist, ist die erste angezeigte Antwort eine ausgewählte Antwort. Die Option Standard ist deaktiviert.
* **Anzeigemarken**

  Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](/help/communities/implementing-scoring.md) mit dem Blogeintrag eines Mitglieds. Die Option Standard ist deaktiviert.

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, kann die Idee als [präsentierte Inhalte](/help/communities/featured.md). Die Option Standard ist deaktiviert.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (unter Verwendung von Vorname, Nachname, Benutzername) identifizieren und sie mit der gemeinsamen Syntax @user-name versehen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

  Schränken Sie die maximale Anzahl der Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **Benutzeroberflächen-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag mit Tags zu versehen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **Benutzermoderation** festlegen, wie die veröffentlichten Themen (Fragen) und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Antworten verweigern**

  Wenn diese Option aktiviert ist, dürfen Moderatoren von vertrauenswürdigen Mitgliedern gepostete Antworten ablehnen und verhindern, dass die Antworten im öffentlichen Frage- und A-Forum erscheinen. Die Option Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder eine Frage (Thema) schließen, um weitere Bearbeitungen und Antworten vorzunehmen, und eine Frage erneut öffnen. Die Option Standard ist deaktiviert.

* **Verschieben von Themen**
Wenn diese Option aktiviert ist, können Moderatoren auf Veröffentlichungsseite Fragen verschieben. Die Option Standard ist deaktiviert.

* **Posts kennzeichnen**

  Ist diese Option aktiviert, können Mitglieder Fragen oder Antworten anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste der Kennzeichnungsgründe**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Frage oder Antwort als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

  Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung einer Frage oder Antwort als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Schwellenwert für Moderation**

  Geben Sie an, wie oft eine Frage oder Antwort von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

  Geben Sie an, wie oft eine Frage oder Antwort gekennzeichnet werden muss, bevor sie aus der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 gesetzt ist, wird die gekennzeichnete Frage oder Antwort nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Unter dem **Tag-Feld** Registerkarte die Tags, die angewendet werden können, sofern dies unter der Variablen **Einstellungen** Registerkarte, sind entsprechend den ausgewählten Namespaces begrenzt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` wird unter dem **Einstellungen** Registerkarte. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) und &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **Empfehlungslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert **-**1 bedeutet keine Beschränkungen. Der Standardwert ist 0.

#### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Unter dem **Sortiereinstellungen** festlegen, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortieren nach**

  Aktivieren Sie alle zulässigen Sortieroptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

  Ziehen Sie den Mauszeiger nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

  Dropdown-Liste zur Auswahl eines von `All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Antworten identifizieren {#identifying-answers}

Eine Antwort kann mithilfe der `Select Answer` Schaltfläche. Nachdem eine Frage als beantwortet markiert wurde, kann eine andere Antwort erst ausgewählt werden, nachdem die erste mit der Funktion `Unmark Chosen Answer` Schaltfläche.

Nach Auswahl als praktikable Antwort kann die Auswahl mithilfe der Variablen `Unmark Chosen Answer` Schaltfläche.

Sobald eine Antwort als praktikable Antwort ausgewählt wurde, ein Hinweis darauf, dass die Frage `Answered` wird neben dem Fragethema auf der Hauptseite der Fragen angezeigt.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorberechtigungen verfügt, kann er die durch die Konfiguration der Komponente zulässigen Moderationsaufgaben ausführen, unabhängig davon, wer die Frage oder Antwort verfasst hat.

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

Weitere Informationen finden Sie im [Grundlagen der quantitativen Lockerung](/help/communities/qna-essentials.md) -Seite für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
