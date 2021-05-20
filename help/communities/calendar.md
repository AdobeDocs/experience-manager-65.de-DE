---
title: Kalenderfunktion
seo-title: Kalenderfunktion
description: Stellt Community-Ereignisinformationen im Kalenderformat bereit
seo-description: Stellt Community-Ereignisinformationen im Kalenderformat bereit
uuid: 262f6afa-d8aa-4815-8440-a8ed5668c76d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 70fa0b9c-cb98-45c4-9c94-bef4a9f3741e
docset: aem65
exl-id: c9b34b00-525d-4ca3-bd18-11bb7ce66787
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
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

Um eine Komponente `Calendar` im Autorenmodus zu einer Seite hinzuzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Calendar`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite, beispielsweise in die Nähe einer Eigenschaft, die Benutzer bewerten sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Calendar` so angezeigt.

![calendar-component](assets/calendar-component.png)

### Konfigurieren eines Kalenders {#configuring-calendar}

Wählen Sie die platzierte Komponente `Calendar` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

![configure-calendar](assets/configure-calendar1.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **Einstellungen** an, ob Tags auf Kalendereinträge angewendet werden sollen.

* **Ereignisse pro Seite**

   Definiert die Anzahl der pro Seite angezeigten Ereignisse. Der Standardwert ist 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss die Veröffentlichung von Kalenderereignissen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Diese Option ist standardmäßig deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, ist der Kalender für neue Ereigniseinträge und -kommentare gesperrt. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Kalenderereignisse und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig aktiviert.

* **Tagging zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder den von ihnen geposteten Ereignissen Tag-Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld** ). Diese Option ist standardmäßig aktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass Dateianlagen zu einem Kalenderereignis oder Kommentar hinzugefügt werden. Diese Option ist standardmäßig aktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Ereignisse verfolgen, die in den Kalender veröffentlicht wurden. Diese Option ist standardmäßig aktiviert.

* **Max. Dateigröße**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152** **(2 MB).

* **Zugelassene Bildtypen für Deckblätter**

   Eine kommagetrennte Liste von Bilddateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Der Standardwert ist `.jpg,.jpeg,.png,.gif,.bmp`.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zum Kalenderereignis veröffentlicht wurden. Diese Option ist standardmäßig aktiviert.

* **Benutzern das Löschen von Anmerkungen und Ereignissen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die von ihnen veröffentlichten Kommentare und Kalenderereignisse löschen. Die Standardeinstellung ist &quot;markiert&quot;.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, nehmen Sie die Abstimmungsfunktion in ein Kalenderereignis auf. Diese Option ist standardmäßig aktiviert.

* **Breadcrumbs anzeigen**

   Breadcrumbs auf Ereignisseite anzeigen. Diese Option ist standardmäßig aktiviert.

* **Datumsbereich-Filter**

   Definiert die Anzahl der Tage, die zum aktuellen Datum hinzugefügt werden, um den &quot;An&quot;-Wert des Seitenfilters für die Auflistung von Kalenderereignissen zu berechnen. Die Standardnummer ist 30.

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert werden. Diese Option ist standardmäßig deaktiviert.

Geben Sie auf der Registerkarte **Benutzermoderation** an, wie die veröffentlichten Themen und Antworten (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

#### Registerkarte Benutzermoderation {#user-moderation-tab}

* **Posts ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig aktiviert.

* **Ereignisse schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder ein Ereignis schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Ereignis auch erneut öffnen. Diese Option ist standardmäßig aktiviert.

* **Posts kennzeichnen**

   Ist diese Option aktiviert, können Mitglieder Ereignisse oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig aktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Ereignisse oder Kommentare als unangemessen gekennzeichnet werden. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Ereignisses oder Kommentars als unangemessen eingeben. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Ereignis oder Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Ereignis oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot;{#tag-field-tab}

Auf der Registerkarte **Tag-Feld** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **Einstellungen** aktiviert) verwendet werden können.

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` auf der Registerkarte **Einstellungen** aktiviert ist. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Standardwert ist **-**1 (keine Beschränkungen).

>[!NOTE]
>
>Unter [Verwalten von Tags](/help/sites-administering/tags.md) finden Sie Informationen darüber, wie Sie neue Tag-Namespaces (Taxonomie) hinzufügen können.

#### Registerkarte &quot;Übersetzung&quot;{#translation-tab}

Auf der Registerkarte **Übersetzung** können Sie festlegen, ob bei für die Community-Site aktivierten Übersetzungsoption anstatt bestimmter Einträge der gesamte Thread (Veranstaltung und Kommentare) übersetzt werden soll.

* **Alles übersetzen**

   Wenn diese Option aktiviert ist, werden Ereignis und Kommentare in die bevorzugte Sprache des Benutzers übersetzt. Diese Option ist standardmäßig aktiviert.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung erscheint im Kalender ein Suchfeld mit einem Standarddatumsbereich und allen Veranstaltungen, die in diesen Zeitraum fallen.

Wurde ein Kalenderereignis ausgewählt, werden Details, Beschreibung und Kommentare eingeblendet.

Die Verfügbarkeit weiterer Optionen hängt davon ab, ob der Site-Besucher Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Besucher ist.

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) für alle Kalenderereignisse und Kommentare der Veranstaltung durchführen (je nach Berechtigungen durch die Konfiguration der Komponente).

![moderators-view](assets/moderators-view.png)

#### Mitglieder {#members}

Wenn der angemeldete Benutzer Community-Mitglied oder [privilegiertes Mitglied](/help/communities/users.md#privileged-members-group) ist (je nach Konfiguration), kann er `New Event` auswählen, um ein neues Kalenderereignis zu erstellen und zu posten.

Insbesondere können sie:

* Neues Kalenderereignis erstellen
* Posten eines Kommentars zu einem Kalenderereignis
* Bearbeiten von eigenen Kalenderereignissen oder Kommentaren
* Löschen eines eigenen Kalenderereignisses oder Kommentars
* Kennzeichnen von Kalenderereignissen oder Kommentaren anderer Benutzer

![create-event](assets/configure-calendar2.png)

![event-post](assets/configure-calendar3.png)

#### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Veranstaltungen und Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Veranstaltungen oder Kommentare hinzufügen und keine Veranstaltungen und Kommentare anderer Benutzer kennzeichnen.

![anonymous-user-view](assets/anonymous-user-view1.png)

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Kalendergrundlagen](/help/communities/calendar-basics-for-developers.md) für Entwickler.

Informationen zur Moderation von Kalenderereignissen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von Kalenderereignissen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).

Informationen zur Übersetzung von Kalenderereignissen und Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
