---
title: Ideen-Funktion
description: Erfahren Sie, wie Sie die Ideen-Funktion hinzufügen und konfigurieren, mit der Community-Mitglieder Ideen erstellen, anzeigen, folgen, abstimmen und kommentieren können, die mit der Community geteilt wurden.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: e130bab4-524d-4413-ba8b-53d0ed9e8623
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---

# Ideen-Funktion {#ideation-feature}

## Einführung {#introduction}

Die Filterfunktion bietet angemeldeten Site-Besuchern (Community-Mitgliedern) in der Publish-Umgebung folgende Möglichkeiten:

* Erstellen Sie Ideen, die Sie mit der Community teilen können.
* Ideen anzeigen und kommentieren.
* Folgen Sie einer Idee.
* Abstimmung über eine Idee.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Filterfunktion zu einer AEM Site.
* Konfigurationseinstellungen für die Komponente &quot;Idee&quot;.

### Hinzufügen einer Idee zu einer Seite {#adding-a-ideation-to-a-page}

Möchten Sie im Autorenmodus einer Seite die Komponente `Ideation` hinzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Ideation`

Ziehen Sie sie an die gewünschte Stelle auf der Seite, auf der die Idee erscheinen soll.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/ideation.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Ideation` wie folgt angezeigt:

![ideation](assets/ideation.png)

### Konfigurieren einer Idee {#configuring-an-ideation}

Wählen Sie die platzierte Komponente `Ideation` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![ideation-settings](assets/ideation-settings.png)

#### Registerkarte &quot;Einstellungen&quot; {#settings-tab}

Legen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** Einstellungen für Ideen und Kommentare fest:

* **Zulassen der Anlagenminiatur**
* **Max. Größe der Miniaturansichten anhängen**
* **Min. Bildgröße für Miniatur**
* **Maximale Größe der Miniaturansichten**
* **Zulassen von privilegierten Mitgliedern**
* **Zulässige privilegierte Mitglieder**
* **Vom Benutzer generierten Inhalt im Bearbeitungsmodus des Autors blockieren**
* **Ideentitel**

* Der Anzeigetitel für die Idee. Der Standardwert ist `Ideation`.
* **Ideenbeschreibung**

  Eine Beschreibung, die als Untertitel für die Idee angezeigt wird. Der Standardwert ist keine Beschreibung.

* **Themen pro Seite**

  Definiert die Anzahl der pro Seite angezeigten Ideen/Beiträge. Der Standardwert ist 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss die Veröffentlichung von Ideen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen können. Die Option Standard ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, steht das Ideenforum neuen Ideen und Kommentaren offen. Die Option Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Ideen und Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Beschriftungen hinzufügen (siehe Registerkarte **[!UICONTROL Tag-Feld]** ). Die Option Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können der Idee oder dem Kommentar Dateianlagen hinzugefügt werden. Die Option Standard ist deaktiviert.

* **Maximale Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, können nicht angegebene nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Max. Größe der Bilddatei anhängen**

  Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Maximale Anzahl der Bytes, die eine hochgeladene Bilddatei aufweisen kann. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

  Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Kommentare, die zur Idee gepostet wurden. Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

  Sofern aktiviert, können Sie über die Kommentare einer Idee abstimmen. Die Option Standard ist deaktiviert.

* **Benutzern erlauben, Kommentare und Themen zu löschen**

  Wenn diese Option aktiviert ist, können Mitglieder die Kommentare und Ideen löschen, die sie veröffentlicht haben. Die Option Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Ideenbeiträge hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Die Option Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder per E-Mail über neue Beiträge benachrichtigt werden ([subscription](/help/communities/subscriptions.md)). Erfordert die Überprüfung von `Allow Following` und die Konfiguration von [E-Mail](/help/communities/email.md). Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

  Sofern aktiviert, können Sie über die Kommentare einer Idee abstimmen. Die Option Standard ist deaktiviert.

* **Anzeigemarke**

  Wenn diese Option aktiviert ist, zeigen Sie verdiente [Badges](/help/communities/implementing-scoring.md) mit der Idee eines Mitglieds an. Die Option Standard ist deaktiviert.

* **Antworten auf Listenseite nicht abrufen**

* **Zulassen von speziellen Inhalten**

  Wenn diese Option aktiviert ist, kann die Idee als [Inhalt mit Funktionen](/help/communities/featured.md) identifiziert werden. Die Option Standard ist deaktiviert.

* **Erwähnung aktivieren**
* **Max. Erwähnungen**
* **UI-Erwähnungsmuster**

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Benutzermoderation]** an, wie die veröffentlichten Ideen und Kommentare (benutzergenerierte Inhalte) verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Posts verweigern**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum erscheint. Die Option Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren von vertrauenswürdigen Mitgliedern ein Thema schließen, um weitere Bearbeitungen und Kommentare vorzunehmen, und ein Thema möglicherweise erneut öffnen. Die Option Standard ist deaktiviert.

* **Posts kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder Themen oder Kommentare anderer Mitglieder als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste mit Kennzeichnungsgründen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem Themen oder Kommentare als unangemessen gekennzeichnet werden. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

  Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Themas oder Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 ( einmal).

* **Kennzeichnungslimit**

  Geben Sie an, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor er in der öffentlichen Ansicht ausgeblendet wird. Wenn der Wert auf -1 festgelegt ist, wird das gekennzeichnete Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für Moderation sein. Der Standardwert ist 5.

#### Registerkarte &quot;Tag-Feld&quot; {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag-Feld]** sind die Tags, die angewendet werden können, sofern sie auf der Registerkarte **[!UICONTROL Einstellungen]** zulässig sind, entsprechend den ausgewählten Namespaces beschränkt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert ist. Die Tags, die angewendet werden können, beschränken sich auf die Tags innerhalb der aktivierten Namespace-Kategorien. Die Liste der Namespaces umfasst &quot;Standard-Tags&quot;(den Standard-Namespace) und &quot;Alle Tags einschließen&quot;. Der Standardwert ist &quot;none&quot;, was bedeutet, dass alle Namespaces zulässig sind.

* **Empfehlungslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht wird. Der Wert **-1** bedeutet keine Begrenzung. Der Standardwert ist 0.

#### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Geben Sie auf der Registerkarte **[!UICONTROL Sortiereinstellungen]** an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortieren nach**

  Aktivieren Sie alle zulässigen Sortieroptionen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

  Ziehen Sie den Mauszeiger nach unten, um eine der aktivierten Sortieroptionen auszuwählen, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für die Analytics-Sortierung auswählen**

  Ziehen Sie nach unten, um einen von `All, Last 24 Hours, Last 7 Days, Last 30 Days` auszuwählen. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Erstellen einer Idee {#creating-idea}

Wie bei allen Communities-Funktionen kann ein Besucher der Site, falls er nicht angemeldet ist, nur Ideen lesen und andere Meinungen ansehen (durch Kommentare und Abstimmung/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine Idee erstellen.

![create-new-ideas](assets/create-new-idea.png)

Vor dem Senden der Idee kann das Mitglied einen Entwurf speichern.

Durch Auswahl der Schaltfläche `Save as Draft` wird ein Entwurf gespeichert.

![save-ideas](assets/save-idea.png)

Wenn Sie gespeicherte Entwürfe auf der Registerkarte `My Drafts` anzeigen, wählen Sie `Read More` aus, um wieder in den Bearbeitungsmodus zu wechseln:

![edit-ideas](assets/edit-idea.png)

#### Feedback geben {#providing-feedback}

Sobald die Idee veröffentlicht wurde, können sich andere Mitglieder anmelden, die Idee ( `Read More`) öffnen und die Idee mögen, so zur Stimmenanzahl hinzufügen und Kommentare machen.

![feedback](assets/feedback-idea.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Ideen-Grundlagen](/help/communities/ideation.md) .

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
