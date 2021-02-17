---
title: Kalenderfunktion
seo-title: Kalenderfunktion
description: Bietet Community-Ereignis-Informationen im Kalenderformat
seo-description: Bietet Community-Ereignis-Informationen im Kalenderformat
uuid: 262f6afa-d8aa-4815-8440-a8ed5668c76d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 70fa0b9c-cb98-45c4-9c94-bef4a9f3741e
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 46%

---


# Kalenderfunktion {#calendar-feature}

## Einführung {#introduction}

Mit der Kalenderfunktion können der Community Veranstaltungsdaten im Kalenderformat bereitgestellt werden. So lassen sich entweder alle Site-Besucher oder nur angemeldete Besucher (Community-Mitglieder) einladen, die Veranstaltungen können jedoch nur von eigens autorisierten Mitgliedern bearbeitet werden.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Kalenderfunktion zu einer AEM Site
* Konfigurationseinstellungen für `Calendar`-Komponenten

## Hinzufügen eines Kalenders zu einer Seite {#adding-a-calendar-to-a-page}

Um einer Seite im Autorenmodus eine `Calendar`-Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach

* `Communities / Calendar`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite, beispielsweise in die Nähe einer Eigenschaft, die Benutzer bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) einbezogen werden, wird die `Calendar`-Komponente so angezeigt.

![calendar-component](assets/calendar-component.png)

### Konfigurieren eines Kalenders {#configuring-calendar}

Wählen Sie die platzierte Komponente `Calendar` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

![configure-calendar](assets/configure-calendar1.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie unter der Registerkarte **Einstellungen** an, ob Tags auf Kalendereinträge angewendet werden dürfen.

* **Ereignisse pro Seite**

   Definiert die Anzahl der pro Seite angezeigten Ereignisse. Der Standardwert ist 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss die Veröffentlichung von Kalenderkommentaren und Ereignissen genehmigt werden, bevor sie auf einer Veröffentlichungssite erscheinen. Diese Option ist standardmäßig deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, wird der Ereignis für neue Einträge und Kommentare geschlossen. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Kalenderkommentare und Ereignisse mit Markup eingegeben werden. Diese Option ist standardmäßig aktiviert.

* **Tagging zulassen**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern gestatten, den von ihnen geposteten Ereignissen Tagbeschriftungen hinzuzufügen (siehe **Feld** Registerkarte). Diese Option ist standardmäßig aktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass Dateianlagen zu einem Ereignis oder Kommentar im Kalender hinzugefügt werden. Diese Option ist standardmäßig aktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, den im Kalender veröffentlichten Ereignissen zu folgen. Diese Option ist standardmäßig aktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn `Allow File Uploads` markiert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Relevant nur, wenn `Allow File Uploads` markiert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152****(2 MB).

* **Zugelassene Bildtypen für Deckblätter**

   Eine kommagetrennte Liste von Bilddateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Der Standardwert ist `.jpg,.jpeg,.png,.gif,.bmp`.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option aktiviert ist, können Sie Antworten auf Kommentare zulassen, die an das Kalender-Ereignis gesendet wurden. Diese Option ist standardmäßig aktiviert.

* **Benutzern das Löschen von Anmerkungen und Ereignissen ermöglichen**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern das Löschen der geposteten Kommentare und Kalenderdaten gestatten. Der Standardwert ist** **markiert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die Funktion &quot;Abstimmung&quot;in ein Ereignis ein. Diese Option ist standardmäßig aktiviert.

* **Breadcrumbs anzeigen**

   Breadcrumbs auf Ereignisseite anzeigen. Diese Option ist standardmäßig aktiviert.

* **Datumsbereich-Filter**

   Definiert die Anzahl der Tage, die zum aktuellen Ereignis hinzugefügt werden, um den &quot;An&quot;-Wert des Seitenfilters für die Kalenderauflistungen zu berechnen. Die Standardnummer ist 30.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [gekennzeichneter Inhalt](/help/communities/featured.md) identifiziert werden. Diese Option ist standardmäßig deaktiviert.

Geben Sie auf der Registerkarte **Benutzermoderation** an, wie die veröffentlichten Themen und Antworten (vom Benutzer generierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

#### Benutzermoderation, Registerkarte {#user-moderation-tab}

* **Posts ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge verweigern und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig aktiviert.

* **Ereignisse schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren mit vertrauenswürdigen Mitgliedern ein Ereignis schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und auch ein Ereignis erneut öffnen. Diese Option ist standardmäßig aktiviert.

* **Posts kennzeichnen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, die Ereignisse oder Kommentare anderer als unangemessen zu kennzeichnen. Diese Option ist standardmäßig aktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können die Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie ein Ereignis oder einen Kommentar als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung eines Ereignisses oder Kommentars als unangemessen einzugeben. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Ereignis oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Ereignis oder Kommentar markiert werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Auf der Registerkarte **Tag-Feld** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **Einstellungen** aktiviert) verwendet werden können.

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` unter der Registerkarte **Einstellungen** markiert ist. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namensraum umfasst &quot;Standard-Tags&quot;(den standardmäßigen Namensraum) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Standardwert ist **-**1 (keine Beschränkungen).

>[!NOTE]
>
>Unter [Verwalten von Tags](/help/sites-administering/tags.md) finden Sie Informationen darüber, wie Sie neue Tag-Namespaces (Taxonomie) hinzufügen können.

#### Registerkarte Übersetzung {#translation-tab}

Auf der Registerkarte **Übersetzung** können Sie festlegen, ob bei für die Community-Site aktivierten Übersetzungsoption anstatt bestimmter Einträge der gesamte Thread (Veranstaltung und Kommentare) übersetzt werden soll.

* **Alles übersetzen**

   Wenn diese Option aktiviert ist, werden die Ereignisse und Kommentare in die vom Benutzer bevorzugte Sprache übersetzt. Diese Option ist standardmäßig aktiviert.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung erscheint im Kalender ein Suchfeld mit einem Standarddatumsbereich und allen Veranstaltungen, die in diesen Zeitraum fallen.

Wurde ein Kalenderereignis ausgewählt, werden Details, Beschreibung und Kommentare eingeblendet.

Die Verfügbarkeit weiterer Optionen hängt davon ab, ob der Site-Besucher Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Besucher ist.

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) für alle Kalenderereignisse und Kommentare der Veranstaltung durchführen (je nach Berechtigungen durch die Konfiguration der Komponente).

![moderators-Ansicht](assets/moderators-view.png)

#### Mitglieder {#members}

Wenn der angemeldete Benutzer ein Community-Mitglied oder [ein privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) ist (je nach Konfiguration), können sie `New Event` auswählen, um ein neues Kalendersymbol zu erstellen und zu posten.

Insbesondere können sie

* Erstellen eines neuen Ereignisses
* Veröffentlichen eines Kommentars in einem Kalender-Ereignis
* Bearbeiten eines eigenen Ereignisses oder Kommentars
* Löschen eines eigenen Ereignisses oder Kommentars
* Ereignisse oder Kommentare anderer kennzeichnen

![create-Ereignis](assets/configure-calendar2.png)

![Ereignis-Post](assets/configure-calendar3.png)

#### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Veranstaltungen und Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Veranstaltungen oder Kommentare hinzufügen und keine Veranstaltungen und Kommentare anderer Benutzer kennzeichnen.

![anonymous-user-Ansicht](assets/anonymous-user-view1.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Calendar Essentials](/help/communities/calendar-basics-for-developers.md) für Entwickler.

Informationen zur Moderation von Kalenderereignissen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Taggen von Kalenderinhalten und -kommentaren finden Sie unter [Tagging von benutzergenerierten Ereignissen](/help/communities/tag-ugc.md).

Eine Übersetzung der Kalenderinhalte und Ereignisse finden Sie unter [Übersetzen benutzergenerierter ](/help/communities/translate-ugc.md).
