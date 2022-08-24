---
title: Ideen-Funktion
seo-title: Ideation Feature
description: Hinzufügen und Konfigurieren der Funktion "Idee"
seo-description: Adding and configuring the Ideation feature
uuid: 38468290-6d00-4ee4-91d8-7c2e8ae32712
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a3f5a21d-2df6-4663-a1ea-3a067c46f860
docset: aem65
exl-id: e130bab4-524d-4413-ba8b-53d0ed9e8623
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 32%

---

# Ideen-Funktion {#ideation-feature}

## Einführung    {#introduction}

Die Filterfunktion bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Veröffentlichungsumgebung für:

* Erstellen Sie Ideen, die Sie mit der Community teilen können.
* Ideen anzeigen und kommentieren.
* Folgen Sie einer Idee.
* Stimmen Sie über eine Idee ab.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Filterfunktion zu einer AEM Site.
* Konfigurationseinstellungen für die Komponente &quot;Idee&quot;.

### Hinzufügen einer Idee zu einer Seite {#adding-a-ideation-to-a-page}

So fügen Sie eine `Ideation` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Ideation`

und ziehen Sie sie an die gewünschte Stelle auf der Seite, auf der die Idee erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](/help/communities/ideation.md#essentials-for-client-side) eingeschlossen sind, wird die `Ideation` wird angezeigt:

![Idee](assets/ideation.png)

### Konfigurieren einer Idee {#configuring-an-ideation}

Wählen Sie die platzierte `Ideation` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

![ideation-settings](assets/ideation-settings.png)

#### Registerkarte „Settings“ {#settings-tab}

Unter dem **[!UICONTROL Einstellungen]** Registerkarte Einstellungen für Ideen und Kommentare festlegen:

* **Anhangminiatur zulassen**
* **Max. Anhangminiaturgröße**
* **Minimale Bildgröße für Miniaturansicht**
* **Max. Miniaturgröße**
* **Privilegierte Mitglieder zulassen**
* **Zugelassene privilegierte Mitglieder**
* **Benutzergenerierte Inhalte im Autoren-Bearbeitungsmodus blockieren**
* **Ideen-Titel**

* Der Anzeigetitel für die Idee. Der Standardwert ist `Ideation`.
* **Ideen-Beschreibung**

   Eine Beschreibung, die als Untertitel für die Idee angezeigt wird. Der Standardwert ist keine Beschreibung.

* **Themen pro Seite**

   Definiert die Anzahl der pro Seite angezeigten Ideen/Beiträge. Der Standardwert ist 10.

* **Moderiert**

   Wenn diese Option aktiviert ist, muss die Veröffentlichung von Ideen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen. Diese Option ist standardmäßig deaktiviert.

* **Geschlossen**

   Wenn diese Option aktiviert ist, steht das Ideenforum neuen Ideen und Kommentaren offen. Diese Option ist standardmäßig deaktiviert.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Ideen und Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **Tagging zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder ihrem Beitrag Tag-Beschriftungen hinzufügen (siehe **[!UICONTROL Tag-Feld]** Registerkarte). Diese Option ist standardmäßig deaktiviert.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, können der Idee oder dem Kommentar Dateianlagen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Mit diesem Feld lässt sich die Größe (in Byte) der hochgeladenen Dateien beschränken. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

   Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Maximale Dateigröße für Bildanhang**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Die maximal zulässige Anzahl von Bytes einer Bilddatei. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zur Idee gepostet wurden. Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Sofern aktiviert, können Sie über die Kommentare einer Idee abstimmen. Diese Option ist standardmäßig deaktiviert.

* **Benutzern das Löschen von Anmerkungen und Themen ermöglichen**

   Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Ideen löschen, die sie veröffentlicht haben. Diese Option ist standardmäßig deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Ideenbeiträge hinzu, mit der Mitglieder [benachrichtigt](/help/communities/notifications.md) von neuen Stellen. Diese Option ist standardmäßig deaktiviert.

* **E-Mail-Abonnements zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge informiert werden ([Abonnement](/help/communities/subscriptions.md)). Erfordert `Allow Following` zu überprüfen und [E-Mail konfiguriert](/help/communities/email.md). Diese Option ist standardmäßig deaktiviert.

* **Abstimmung zulassen**

   Sofern aktiviert, können Sie über die Kommentare einer Idee abstimmen. Diese Option ist standardmäßig deaktiviert.

* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, zeigen Sie Earned und Assored [Badges](/help/communities/implementing-scoring.md) mit der Idee eines Mitglieds. Diese Option ist standardmäßig deaktiviert.

* **Antworten auf Listenseite nicht abrufen**

* **Feature-Inhalt zulassen**

   Wenn diese Option aktiviert ist, kann die Idee als [präsentierte Inhalte](/help/communities/featured.md). Diese Option ist standardmäßig deaktiviert.

* **Erwähnung aktivieren**
* **Max. Erwähnungen**
* **UI-Erwähnungsmuster**

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **[!UICONTROL Benutzermoderation]** -Registerkarte angeben, wie die veröffentlichten Ideen und Kommentare (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Posts ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Diese Option ist standardmäßig deaktiviert.

* **Themen schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **Posts kennzeichnen**

   Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der gekennzeichnete Kommentar nie ausgeblendet. In allen anderen Fällen muss der Wert größer als der oder gleich dem „Schwellenwert für Moderation“ sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** wird eingeschränkt, welche Tags je nach ausgewähltem Namespace (falls auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert) verwendet werden können.

* **Zulässige Namespaces**

   Relevant, wenn `Allow Tagging` wird unter dem **[!UICONTROL Einstellungen]** Registerkarte. Die verwendbaren Tags sind auf die ausgewählten Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) sowie &quot;Alle Tags einschließen&quot;. Standardmäßig ist die Option nicht aktiviert, es sind also alle Namespaces zulässig.

* **Empfehlungsgrenze**

   Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Ein Wert von **-1** bedeutet keine Begrenzung. Der Standardwert ist 0.

#### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Unter dem **[!UICONTROL Sortiereinstellungen]** festlegen, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfolge**

   Aktivieren Sie alle zulässigen Sortieroptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

   Ziehen Sie den Mauszeiger nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für Analytics-Sortierung auswählen**

   Ziehen Sie nach unten, um eines von `All, Last 24 Hours, Last 7 Days, Last 30 Days`. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Erstellen einer Idee {#creating-idea}

Wie bei allen Communities-Funktionen kann ein Besucher der Site, falls er nicht angemeldet ist, nur Ideen lesen und andere Meinungen ansehen (durch Kommentare und Abstimmung/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine neue Idee erstellen.

![create-new-ideas](assets/create-new-idea.png)

Vor dem Senden der Idee kann das Mitglied einen Entwurf speichern.

Durch Auswahl der `Save as Draft` -Schaltfläche verwenden, wird ein Entwurf gespeichert.

![save-ideas](assets/save-idea.png)

Beim Anzeigen gespeicherter Entwürfe im `My Drafts` Registerkarte, wählen Sie `Read More` , um wieder in den Bearbeitungsmodus zu wechseln:

![edit-ideas](assets/edit-idea.png)

#### Feedback geben {#providing-feedback}

Sobald die Idee veröffentlicht wurde, können sich andere Mitglieder anmelden und die Idee öffnen ( `Read More`) und wie die Idee, so zur Stimmenanzahl, und Kommentare.

![Feedback,](assets/feedback-idea.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Ideengrundlagen](/help/communities/ideation.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
