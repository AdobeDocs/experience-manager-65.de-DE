---
title: Kalenderfunktion
seo-title: Kalenderfunktion
description: Bietet Community-Ereignisinformationen im Kalenderformat
seo-description: Bietet Community-Ereignisinformationen im Kalenderformat
uuid: 262f6afa-d8aa-4815-8440-a8ed5668c76d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 70fa0b9c-cb98-45c4-9c94-bef4a9f3741e
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Kalenderfunktion{#calendar-feature}

## Einführung {#introduction}

Mit der Kalenderfunktion können der Community Veranstaltungsdaten im Kalenderformat bereitgestellt werden. So lassen sich entweder alle Site-Besucher oder nur angemeldete Besucher (Community-Mitglieder) einladen, die Veranstaltungen können jedoch nur von eigens autorisierten Mitgliedern bearbeitet werden.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Kalenderfunktion zu einer AEM-Site
* configuration settings for `Calendar`components

## Hinzufügen eines Kalenders zu einer Seite {#adding-a-calendar-to-a-page}

To add a `Calendar` component to a page in author mode, use the component browser to locate

* `Communities / Calendar`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite, beispielsweise in die Nähe einer Eigenschaft, die Benutzer bewerten sollen.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) are included, this is how the `Calendar` component will appear.

![chlimage_1-147](assets/chlimage_1-147.png)

### Konfigurieren eines Kalenders {#configuring-calendar}

Select the placed `Calendar`component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-148](assets/chlimage_1-148.png) ![chlimage_1-149](assets/chlimage_1-149.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie auf der Registerkarte **Einstellungen **an, ob Tags auf Kalendereinträge angewendet werden dürfen.

* **Ereignisse pro Seite** Legt die Anzahl der Veranstaltungen fest, die pro Seite angezeigt werden. Der Standardwert ist 10.

* **Moderiert** Ist diese Option aktiviert, müssen Kalendereinträge zunächst genehmigt werden, bevor sie öffentlich zugänglich gemacht werden. Diese Option ist standardmäßig deaktiviert.

* **Geschlossen** Ist diese Option aktiviert, können im Kalender keine neuen Veranstaltungseinträge und Kommentare erstellt werden. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor** Ist diese Option aktiviert, können Kalendereinträge und Kommentare mit Markup versehen werden. Diese Option ist standardmäßig aktiviert.

* **Tagging zulassen** Ist diese Option aktiviert, können Mitglieder ihren veröffentlichten Ereignissen Beschriftungen hinzufügen (siehe Registerkarte **Tag-Feld**). Diese Option ist standardmäßig aktiviert.

* **Datei-Uploads zulassen** Ist diese Option aktiviert, können Kalendereinträgen oder Kommentaren Dateien hinzugefügt werden. Diese Option ist standardmäßig aktiviert.

* **Folgende zulassen** Ist diese Option aktiviert, können Mitglieder Ereignissen folgen, die im Kalender veröffentlicht werden. Diese Option ist standardmäßig aktiviert.

* **Max. Dateigröße** Relevant nur, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen** Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Max. Größe** der Bilddatei anhängen ist nur relevant, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152****(2 MB).

* **Zulässige Deckblattbilder** Eine kommagetrennte Liste mit Bilddateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Der Standardwert ist `.jpg,.jpeg,.png,.gif,.bmp`.

* **Antworten mit Diskussionsfaden zulassen** Ist diese Option aktiviert, können im Kalenderereignis Kommentare hinterlassen werden. Diese Option ist standardmäßig aktiviert.

* **Benutzern das Löschen von Kommentaren und Ereignissen** gestatten Wenn diese Option aktiviert ist, gestatten Sie Mitgliedern, die von ihnen veröffentlichten Kommentare und Kalenderereignisse zu löschen. Der Standardwert ist** **markiert.

* **Abstimmung zulassen** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Kalenderereignissen hinzugefügt werden. Diese Option ist standardmäßig aktiviert.

* **Breadcrumbs anzeigen** Breadcrumbs werden auf der Ereignisseite angezeigt. Diese Option ist standardmäßig aktiviert.

* **Datumsbereichsfilter** Definiert die Anzahl der Tage, die dem aktuellen Datum hinzugefügt werden, um den &quot;An&quot;-Wert des Seitenfilters für Kalenderereignisse zu berechnen. Die Standardnummer ist 30.

* **Wenn Sie** die Option &quot;Vorgestellte Inhalte zulassen&quot;aktivieren, kann die Idee als [speziellen Inhalt](/help/communities/featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

Geben Sie auf der Registerkarte **Benutzermoderation **an, wie die veröffentlichten Themen und Antworten (vom Benutzer erstellte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

#### Registerkarte Benutzermoderation {#user-moderation-tab}

* **Posts ablehnen** Ist diese Option aktiviert, können moderierende Mitglieder Beiträge ablehnen und so verhindern, dass diese im Forum veröffentlicht werden. Diese Option ist standardmäßig aktiviert.

* **Ereignisse schließen/erneut öffnen** Ist diese Option aktiviert, können moderierende Mitglieder Veranstaltungen für die weitere Bearbeitung oder Kommentare schließen oder bereits geschlossene Veranstaltungen erneut öffnen. Diese Option ist standardmäßig aktiviert.

* **Posts kennzeichnen** Ist diese Option aktiviert, können Mitglieder Veranstaltungen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig aktiviert**.**

* **Liste mit Kennzeichnungsgründen** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Veranstaltung oder ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Veranstaltungen oder Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert**.**

* **Schwellenwert für Moderation** Geben Sie an, wie oft eine Veranstaltung oder ein Kommentar von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit** Geben Sie an, wie oft eine Veranstaltung oder ein Kommentar als unangemessen gekennzeichnet werden muss, bevor sie oder er aus dem öffentlichen Bereich ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Under the **Tag field** tab, the tags which may be applied, if allowed under the **Settings **tab, are limited according to namespaces chosen.

* **Zulässige Namespaces** Relevant, wenn sie unter der Registerkarte **Einstellungen **markiert `Allow Tagging` sind. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze** Geben Sie die Anzahl der Tags an, die Mitgliedern als Vorschlag angezeigt werden sollen, wenn sie Beiträge im Forum veröffentlichen. Der Standardwert ist **-**1 (keine Beschränkungen).

>[!NOTE]
>
>Unter [Verwalten von Tags](/help/sites-administering/tags.md) finden Sie Informationen darüber, wie Sie neue Tag-Namespaces (Taxonomie) hinzufügen können.

#### Registerkarte &quot;Übersetzung&quot; {#translation-tab}

Wenn auf der Registerkarte **Übersetzung **die Übersetzung für die Community-Site aktiviert ist, kann die Übersetzung so eingestellt werden, dass anstelle bestimmter Beiträge der gesamte Thread (Ereignis und Kommentare) übersetzt wird.

* **Alles übersetzen** Ist diese Option aktiviert, werden Veranstaltung und Kommentare in die Sprache des Benutzers übersetzt. Diese Option ist standardmäßig aktiviert.

## Site-Besuchererlebnis {#site-visitor-experience}

In der Veröffentlichungsumgebung erscheint im Kalender ein Suchfeld mit einem Standarddatumsbereich und allen Veranstaltungen, die in diesen Zeitraum fallen.

Wurde ein Kalenderereignis ausgewählt, werden Details, Beschreibung und Kommentare eingeblendet.

Die Verfügbarkeit weiterer Optionen hängt davon ab, ob der Site-Besucher Moderator, Administrator, Community-Mitglied, privilegiertes Mitglied oder anonymer Besucher ist.

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er [Moderationsaufgaben](/help/communities/moderate-ugc.md) für alle Kalenderereignisse und Kommentare der Veranstaltung durchführen (je nach Berechtigungen durch die Konfiguration der Komponente).

![chlimage_1-150](assets/chlimage_1-150.png)

#### Mitglieder {#members}

When the signed in user is a community member or [privileged member](/help/communities/users.md#privileged-members-group) (depending on configuration), they are able to select `New Event` to create and post a new calendar event.

Insbesondere ist Folgendes möglich:

* Erstellen eines neuen Kalenderereignisses
* Veröffentlichen eines Kommentars zu einem Kalenderereignis
* Bearbeiten eigener Kalenderereignisse oder Kommentare
* Löschen eigener Kalenderereignisse oder Kommentare
* Kennzeichnen von Kalenderereignissen oder Kommentaren anderer Mitglieder

![chlimage_1-151](assets/chlimage_1-151.png) ![chlimage_1-152](assets/chlimage_1-152.png)

#### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Veranstaltungen und Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Veranstaltungen oder Kommentare hinzufügen und keine Veranstaltungen und Kommentare anderer Benutzer kennzeichnen.

![chlimage_1-153](assets/chlimage_1-153.png)

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Calendar Essentials](/help/communities/calendar-basics-for-developers.md) page for developers.

Informationen zur Moderation von Kalenderereignissen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

For tagging calendar events and comments, see [Tagging User Generated Content](/help/communities/tag-ugc.md).

For translation of calendar events and comments, see [Translating User Generated Content](/help/communities/translate-ugc.md).
