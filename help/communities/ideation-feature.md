---
title: Ideenfunktion
seo-title: Ideenfunktion
description: Hinzufügen und Konfigurieren der Funktion "Idee"
seo-description: Hinzufügen und Konfigurieren der Funktion "Idee"
uuid: 38468290-6d00-4ee4-91d8-7c2e8ae32712
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a3f5a21d-2df6-4663-a1ea-3a067c46f860
docset: aem65
translation-type: tm+mt
source-git-commit: f62fb1eb760ddd7baee9ba5a631ff4b921e2d08b
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 32%

---


# Ideenfunktion {#ideation-feature}

## Einführung {#introduction}

Die Funktion &quot;Zielversion&quot;bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Umgebung &quot;Veröffentlichen&quot;für:

* Erstellen Sie Ideen, die Sie mit der Community teilen können.
* Ansicht und Kommentar zu Ideen.
* Folgen Sie einer Idee.
* Stimmen Sie über eine Idee ab.

Dieser Abschnitt der Dokumentation beschreibt:

* Hinzufügen der Suchfunktion zu einer AEM Site.
* Konfigurationseinstellungen für die Ideenkomponente.

### Hinzufügen einer Idee zu einer Seite {#adding-a-ideation-to-a-page}

Um einer Seite im Autorenmodus eine `Ideation`-Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach

* `Communities / Ideation`

und ziehen Sie es auf eine Seite, auf der die Idee erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/ideation.md#essentials-for-client-side) einbezogen werden, wird die `Ideation`-Komponente wie folgt angezeigt:

![ideation](assets/ideation.png)

### Konfigurieren einer Idee {#configuring-an-ideation}

Wählen Sie die platzierte Komponente `Ideation` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![ideation-settings](assets/ideation-settings.png)

#### Registerkarte „Settings“{#settings-tab}

Geben Sie unter der Registerkarte **[!UICONTROL Einstellungen]** die Einstellungen für Ideen und Kommentare an:

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

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, ihrem Beitrag Tagbeschriftungen hinzuzufügen (siehe **[!UICONTROL Feld]** Registerkarte). Diese Option ist standardmäßig deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können Sie zulassen, dass der Idee oder dem Kommentar Dateianlagen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn `Allow File Uploads` markiert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Relevant nur, wenn `Allow File Uploads` markiert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, lassen Sie Antworten auf die Kommentare zu der Idee zu. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, können Sie über die Kommentare zu einer Idee abstimmen. Diese Option ist standardmäßig deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die geposteten Kommentare und Ideen löschen. Diese Option ist standardmäßig deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Ideenbeiträge hinzu, mit der Mitglieder über neue Beiträge benachrichtigt werden können. [](/help/communities/notifications.md) Diese Option ist standardmäßig deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, per E-Mail über neue Beiträge informiert zu werden ([Abonnement](/help/communities/subscriptions.md)). Erfordert die Überprüfung von `Allow Following` und [E-Mail-Konfiguration](/help/communities/email.md). Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, können Sie über die Kommentare zu einer Idee abstimmen. Diese Option ist standardmäßig deaktiviert.

* **Abzeichen anzeigen**

   Wenn aktiviert, zeigen Sie verdiente und zugewiesene [Abzeichen](/help/communities/implementing-scoring.md) mit der Idee eines Mitglieds an. Diese Option ist standardmäßig deaktiviert.

* **Antworten nicht auf Listenseite abrufen**

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [gekennzeichneter Inhalt](/help/communities/featured.md) identifiziert werden. Diese Option ist standardmäßig deaktiviert.

* **Erwähnung aktivieren**
* **Max. Erwähnungen**
* **UI-Erwähnungsmuster**

#### Benutzermoderation, Registerkarte {#user-moderation-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** an, wie die veröffentlichten Ideen und Kommentare (vom Benutzer generierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Posts ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge verweigern und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren mit vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Änderungen und Kommentare vorzunehmen, und ein Thema erneut öffnen. Diese Option ist standardmäßig deaktiviert.

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

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` unter der Registerkarte **[!UICONTROL Einstellungen]** markiert ist. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namensraum umfasst &quot;Standard-Tags&quot;(den standardmäßigen Namensraum) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert **-1** bedeutet keine Begrenzung. Der Standardwert ist 0.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie unter der Registerkarte **[!UICONTROL Sortiereinstellungen]** an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfolge**

   Aktivieren Sie alle zulässigen Sortierungsoptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

   Ziehen Sie nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden soll. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

   Ziehen Sie nach unten, um eines von `All, Last 24 Hours, Last 7 Days, Last 30 Days` auszuwählen. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Erstellen einer Idee {#creating-idea}

Wie bei allen Community-Funktionen, wenn nicht angemeldet, kann ein Site-Besucher nur Ideen lesen und Ansicht andere Meinungen (durch Kommentare und Abstimmung/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine neue Idee erstellen.

![create-new-concept](assets/create-new-idea.png)

Bevor Sie die Idee einreichen, kann das Mitglied einen Entwurf speichern.

Durch Auswahl der Schaltfläche `Save as Draft` wird ein Entwurf gespeichert.

![save-concept](assets/save-idea.png)

Wenn Sie gespeicherte Entwürfe auf der Registerkarte `My Drafts` anzeigen, wählen Sie `Read More` aus, um erneut in den Bearbeitungsmodus zu wechseln:

![edit-concept](assets/edit-idea.png)

#### Feedback {#providing-feedback} bereitstellen

Sobald die Idee veröffentlicht ist, können sich andere Mitglieder anmelden, die Idee ( `Read More`) öffnen und die Idee, so hinzufügen, um die Stimmenanzahl, und Kommentare.

![Feedback,](assets/feedback-idea.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Grundlegende Ideen](/help/communities/ideation.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
