---
title: Ideenfunktion
seo-title: Ideenfunktion
description: Hinzufügen und Konfigurieren der Ideenfunktion
seo-description: Hinzufügen und Konfigurieren der Ideenfunktion
uuid: 38468290-6d00-4ee4-91d8-7c2e8ae32712
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a3f5a21d-2df6-4663-a1ea-3a067c46f860
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Ideenfunktion{#ideation-feature}

## Einführung {#introduction}

Die Ideationsfunktion bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung in:

* Ideen zum Austausch mit der Community erstellen
* Ideen anzeigen und kommentieren
* folgen
* Abstimmung über eine Idee

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Ideenfunktion zu einer AEM-Site
* Konfigurationseinstellungen für die Ideenkomponente

### Adding a Ideation to a Page {#adding-a-ideation-to-a-page}

To add a `Ideation` component to a page in author mode, use the component browser to locate

* `Communities / Ideation`

und ziehen Sie es auf eine Seite, auf der die Idee erscheinen soll.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/ideation.md#essentials-for-client-side) are included, this is how the `Ideation`component will appear :

![chlimage_1-71](assets/chlimage_1-71.png)

### Konfigurieren einer Idee {#configuring-an-ideation}

Select the placed `Ideation` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-72](assets/chlimage_1-72.png) ![ideation-settings](assets/ideation-settings.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie unter der Registerkarte **Einstellungen **die Einstellungen für Ideen und Kommentare an:

* **Anhangminiatur zulassen**
* **Max. Anhangminiaturgröße**
* **Minimale Bildgröße für Miniaturansicht**
* **Max. Miniaturgröße**
* **Privilegierte Mitglieder zulassen**
* **Zugelassene privilegierte Mitglieder**
* **Benutzergenerierte Inhalte im Autoren-Bearbeitungsmodus blockieren**
* **Ideen-Titel**

* Der Anzeigentitel der Idee. Der Standardwert ist `Ideation`.
* **Ideen-Beschreibung**

   Eine Beschreibung, die als Untertitel für die Idee angezeigt wird. Standard ist keine Beschreibung.

* **Themen pro Seite**

   Definiert die Anzahl der pro Seite angezeigten Ideen/Beiträge. Der Standardwert ist 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss die Veröffentlichung von Ideen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungssite erscheinen. Diese Option ist standardmäßig deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, wird das Ideenforum für neue Ideen und Kommentare gesperrt. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Ideen und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **Tagging zulassen**

   If checked, allow members to add tag labels to their post (see **Tag field** tab). Diese Option ist standardmäßig deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass der Idee oder dem Kommentar Dateianlagen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Relevant nur, wenn `Allow File Uploads` aktiviert. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass** **alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152****(2 MB).

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, lassen Sie Antworten auf die Kommentare zu der Idee zu. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, können Sie über die Kommentare zu einer Idee abstimmen. Diese Option ist standardmäßig deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die geposteten Kommentare und Ideen löschen. Diese Option ist standardmäßig deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie folgende Funktion für Ideenbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, per E-Mail über neue Beiträge informiert zu werden ([Abonnement](/help/communities/subscriptions.md)). Muss überprüft `Allow Following` und [E-Mail konfiguriert](/help/communities/email.md)werden. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, können Sie über die Kommentare zu einer Idee abstimmen. Diese Option ist standardmäßig deaktiviert.

* **Abzeichen anzeigen**

   Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit der Idee eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **Antworten nicht auf Listenseite abrufen**

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [spezieller Inhalt](/help/communities/featured.md)identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **Erwähnung aktivieren**
* **Max. Erwähnungen**
* **UI-Erwähnungsmuster**

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation **an, wie die veröffentlichten Ideen und Kommentare (vom Benutzer erstellte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Posts ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge verweigern und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren mit vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Änderungen und Kommentare vorzunehmen, und ein Thema erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **Posts kennzeichnen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, Themen oder Kommentare anderer als unangemessen zu kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie ein Thema oder einen Kommentar als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen einzugeben. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Thema oder Kommentar markiert werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Tag-Feld, Registerkarte {#tag-field-tab}

Under the **Tag field** tab, the tags which may be applied, if allowed under the **Settings **tab, are limited according to namespaces chosen.

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` unter der Registerkarte **Einstellungen** markiert wurde. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert **-**1 bedeutet keine Begrenzung. Der Standardwert ist 0.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie unter der Registerkarte **Sortiereinstellungen **an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfolge**

   Aktivieren Sie alle zulässigen Sortieroptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

   Ziehen Sie nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden soll. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

   Ziehen Sie nach unten, um einen von `All, Last 24 Hours, Last 7 Days, Last 30 Days`auszuwählen. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Erstellen einer Idee {#creating-idea}

Wie bei allen Community-Funktionen kann ein Besucher nur Ideen lesen und andere Meinungen anzeigen, wenn er nicht angemeldet ist (durch Kommentare und Abstimmung/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine neue Idee erstellen.

![chlimage_1-73](assets/chlimage_1-73.png)

Bevor Sie die Idee einreichen, kann das Mitglied einen Entwurf speichern.

Durch Auswahl der `Save as Draft` Schaltfläche wird ein Entwurf gespeichert.

![chlimage_1-74](assets/chlimage_1-74.png)

Wenn Sie gespeicherte Entwürfe auf der `My Drafts` Registerkarte anzeigen, wählen Sie `Read More` die Option, um wieder in den Bearbeitungsmodus zu wechseln:

![chlimage_1-75](assets/chlimage_1-75.png)

#### Feedback bereitstellen {#providing-feedback}

Sobald die Idee veröffentlicht ist, können sich andere Mitglieder anmelden, die Idee ( `Read More`) öffnen und die Idee mögen, um so zur Stimmenauszählung hinzuzufügen und Kommentare.

![chlimage_1-76](assets/chlimage_1-76.png)

### Zusätzliche Informationen {#additional-information}

More information may be found on the [Ideation Essentials](/help/communities/ideation.md) page for developers.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
