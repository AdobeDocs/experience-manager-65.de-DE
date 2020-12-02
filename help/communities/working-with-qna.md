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
source-git-commit: c190d5f223c85f6c49fea1391d8a3d2baff20192
workflow-type: tm+mt
source-wordcount: '1380'
ht-degree: 21%

---


# Funktion „Fragen-und-Antworten-Forum“{#q-a-forum-feature}

## Einführung {#introduction}

Das Forum-Feature QnA (Fragen und Antworten) bietet Community-Mitgliedern einen Raum, Fragen zu stellen und zu beantworten. Es ermöglicht Mitgliedern Folgendes:

* Neue Fragen erstellen
* Inline-Bilder Hinzufügen (mit Unterstützung für Drag &amp; Drop)
* Ansicht und Fragen beantworten
* Nach einer Frage suchen
* Hilfe beim Moderieren des QnA-Inhalts
* Identifizieren Sie die besten Antworten.
* QnA-Fragen von einer Seite auf eine andere verschieben

Die Dokumentation beschreibt:

* Hinzufügen der Funktion des QnA-Forums zu einer AEM Site.
* Konfigurationseinstellungen für die Komponente `QnA`

## Hinzufügen eines Fragen-und-Antworten-Forums zu einer Seite {#adding-a-q-a-forum-to-a-page}

Um einer Seite im Autorenmodus eine `QnA`-Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach `Communities / QnA` und ziehen Sie sie auf eine Seite, auf der das QnA-Forum angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/qna-essentials.md#essentials-for-client-side) einbezogen werden, wird die `QnA`-Komponente wie folgt angezeigt:

![qna-Komponente](assets/qna-component.png)

### Konfigurieren von Fragen und Antworten {#configuring-qna}

Wählen Sie die platzierte Komponente `QnA` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

![qna-config](assets/qna-config.png)

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

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, ihrem Beitrag Tagbeschriftungen hinzuzufügen (siehe **Feld** Registerkarte). Die Option &quot;Standard&quot;ist deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass der Frage oder dem Kommentar Dateianlagen hinzugefügt werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Forumbeiträge hinzu, mit der Mitglieder über neue Beiträge benachrichtigt werden können. [](/help/communities/notifications.md) Die Option &quot;Standard&quot;ist deaktiviert.

* **Fixierung zulassen**

   Wenn diese Option aktiviert ist, können Forenthemen an den Anfang der Liste der Themen angefügt werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, per E-Mail über neue Beiträge informiert zu werden ([Abonnement](/help/communities/subscriptions.md)). Erfordert, dass Folgendes aktiviert und [E-Mail konfiguriert werden](/help/communities/email.md). Die Option &quot;Standard&quot;ist deaktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn `Allow File Uploads` markiert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Relevant nur, wenn `Allow File Uploads` markiert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, dürfen nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass** **alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximale Anzahl von Bytes, die eine hochgeladene Bilddatei haben kann. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, können Sie Antworten auf die zur Frage geposteten Kommentare zulassen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, schließen Sie die Funktion &quot;Abstimmung&quot;mit einer Frage ein. Die Option &quot;Standard&quot;ist deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Fragen löschen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Privilegierte Mitglieder zulassen**

   Wenn diese Option aktiviert ist, dürfen nur Privilegierte Mitglieder Inhalte erstellen.

* **Benutzergenerierte Inhalte im Autoren-Bearbeitungsmodus blockieren**

   Wenn diese Option aktiviert ist, wird der vom Benutzer erstellte Inhalt bei der Bearbeitung im Autorenmodus blockiert.

* **Ausgewählte Antwort an den Anfang verschieben**

   Wenn diese Option aktiviert ist, ist die erste angezeigte Antwort eine ausgewählte Antwort. Die Option &quot;Standard&quot;ist deaktiviert.
* **Abzeichen anzeigen**

   Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit dem Blog-Eintrag eines Mitglieds an. Die Option &quot;Standard&quot;ist deaktiviert.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [gekennzeichneter Inhalt](/help/communities/featured.md) identifiziert werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **Erwähnung aktivieren**

   Wenn diese Option aktiviert ist, können Benutzer der registrierten Community andere registrierte Mitglieder identifizieren (mit Vorname, Nachname, Benutzername) und sie mit einem Tag versehen, das die übliche @user-name-Syntax verwendet. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

   Schränken Sie die maximale Anzahl an Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

   Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@Erwähnung). Beispiel: `~{{familyName}}{{givenName}}`.

#### Benutzermoderation, Registerkarte {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation** an, wie die veröffentlichten Themen (Fragen) und Antworten (vom Benutzer generierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Antworten verweigern**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern gepostete Antworten ablehnen und verhindern, dass die Antwort im öffentlichen Frage-und-Antwort-Forum angezeigt wird. Die Option &quot;Standard&quot;ist deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern eine Frage (Thema) schließen, um weitere Bearbeitungen und Antworten vorzunehmen, und eine Frage erneut öffnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Verschieben von**
ThemenWenn diese aktiviert sind, können Sie Moderatoren auf der Seite des Veröffentlichungsmodus das Verschieben von Fragen zulassen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Posts kennzeichnen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, die Fragen oder Antworten anderer Personen als unangemessen zu kennzeichnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können die Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie eine Frage oder Antwort als unangemessen kennzeichnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung einer Frage oder Antwort als unangemessen einzugeben. Die Option &quot;Standard&quot;ist deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft eine Frage oder Antwort von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft eine Frage oder Antwort markiert werden muss, bevor sie aus der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird die gekennzeichnete Frage oder Antwort nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Unter der Registerkarte **Tag sind die Tags, die angewendet werden können, sofern sie unter der Registerkarte** Einstellungen **zulässig sind, je nach Namensraum begrenzt.**

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` unter der Registerkarte **Einstellungen** markiert ist. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namensraum-Kategorien. Die Liste der Namensraum umfasst &quot;Standard-Tags&quot;(den standardmäßigen Namensraum) und &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert **-**1 bedeutet keine Einschränkungen. Der Standardwert ist 0.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie unter der Registerkarte **Sortiereinstellungen** an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfolge**

   Aktivieren Sie alle zulässigen Sortierungsoptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

   Ziehen Sie nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden soll. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

   Ziehen Sie nach unten, um eine von `All, Last 24 Hours, Last 7 Days, Last 30 Days` auszuwählen. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Identifizieren von Antworten {#identifying-answers}

Eine Antwort kann mit der Schaltfläche `Select Answer` als richtige oder nützliche Antwort markiert werden. Nachdem eine Frage als &quot;Beantwortet&quot;markiert wurde, kann erst eine andere Antwort ausgewählt werden, nachdem die erste mit der Schaltfläche `Unmark Chosen Answer` deaktiviert wurde.

Nach Auswahl als praktikable Antwort kann die Auswahl mithilfe der Schaltfläche `Unmark Chosen Answer` aufgehoben werden.

Sobald eine Antwort als praktikable Antwort ausgewählt wurde, wird auf der Hauptseite der QnA neben dem Fragethema ein Hinweis darauf angezeigt, dass die Frage `Answered` lautet.

#### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderatoren- oder Administrationsrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer die Frage oder Antwort verfasst hat.

Sie können auch Antworten identifizieren.

#### Mitglieder {#members}

Wenn die Site-Besucher angemeldet sind, können sie je nach Konfiguration:

* Posten Sie eine neue Frage.
* Bearbeiten oder löschen Sie die von ihnen erstellten Fragen.
* Kennzeichnen Sie Fragen oder Antworten anderer Mitglieder.
* Finden Sie die Antworten auf die von Ihnen erstellten Fragen heraus.

#### Anonym {#anonymous}

Site-Besucher, die nicht angemeldet sind, können nur gepostete Fragen und Antworten lesen, sie übersetzen, wenn sie unterstützt werden, können aber weder eine Frage noch eine Antwort hinzufügen noch Beiträge anderer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [QnA Essentials](/help/communities/qna-essentials.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
