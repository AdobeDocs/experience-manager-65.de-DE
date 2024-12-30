---
title: Ideenmerkmal
description: Erfahren Sie, wie Sie die Funktion „Ideen“ hinzufügen und konfigurieren, mit der Community-Mitglieder Ideen erstellen, anzeigen, verfolgen, abstimmen und Kommentare zu Ideen abgeben können, die mit der Community geteilt werden.
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

# Ideenmerkmal {#ideation-feature}

## Einführung {#introduction}

Die Ideenfunktion bietet einen Bereich für angemeldete Site-Besucher (Community-Mitglieder) in der Publish-Umgebung, um:

* Ideen entwickeln, um sie mit der Community zu teilen.
* Ideen anzeigen und kommentieren.
* Folge einer Idee.
* Über eine Idee abstimmen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Ideenfunktion zu einer AEM-Site.
* Konfigurationseinstellungen für die Ideenkomponente.

### Hinzufügen einer Idee zu einer Seite {#adding-a-ideation-to-a-page}

Um einer Seite im Autorenmodus eine `Ideation` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach

* `Communities / Ideation`

Und ziehen Sie es auf eine Seite, wo die Idee erscheinen soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen ](/help/communities/ideation.md#essentials-for-client-side) enthalten sind, wird die `Ideation` Komponente wie folgt angezeigt:

![Idee](assets/ideation.png)

### Ideen konfigurieren {#configuring-an-ideation}

Wählen Sie die platzierte `Ideation` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

![ideation-settings](assets/ideation-settings.png)

#### Registerkarte „Einstellungen“ {#settings-tab}

Geben Sie auf **[!UICONTROL Registerkarte]** Einstellungen“ Einstellungen für Ideen und Kommentare an:

* **Miniaturansicht für Anhänge zulassen**
* **Max. Größe für Miniaturansichten anhängen**
* **Minimale Bildgröße für Miniaturansicht**
* **Maximale Größe von Miniaturansichten**
* **Privilegierte Mitglieder zulassen**
* **Zulässige privilegierte Mitglieder**
* **Blockieren von benutzergenerierten Inhalten im Authoring-Bearbeitungsmodus**
* **Ideentitel**

* Der Anzeigetitel für die Idee. Der Standardwert ist `Ideation`.
* **Ideenbeschreibung**

  Eine Beschreibung, die als Untertitel für die Idee angezeigt werden soll. Der Standardwert ist keine Beschreibung.

* **Themen pro Seite**

  Definiert die Anzahl der angezeigten Ideen/Beiträge pro Seite. Der Standardwert ist 10.

* **Moderiert**

  Wenn diese Option aktiviert ist, muss das Posten von Ideen und Kommentaren genehmigt werden, bevor sie auf einer Veröffentlichungs-Site erscheinen können. Standard ist deaktiviert.

* **Geschlossen**

  Wenn diese Option aktiviert ist, wird das Ideenforum für neue Ideen und Kommentare geschlossen. Standard ist deaktiviert.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Ideen und Kommentare mit Markup eingegeben werden. Standard ist deaktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder ihren Beiträgen Tag-Labels hinzufügen (siehe **[!UICONTROL Tag-Feld]** Registerkarte). Standard ist deaktiviert.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, können der Idee oder dem Kommentar Dateianhänge hinzugefügt werden. Standard ist deaktiviert.

* **max. Dateigröße**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Zulässige Dateitypen**

  Nur relevant, wenn `Allow File Uploads` aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Punkttrennzeichen. Zum Beispiel .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, können die nicht angegebenen nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Max. Größe der angehängten Bilddatei**

  Nur relevant, wenn Datei-Uploads zulassen aktiviert ist. Maximale Anzahl an Byte, die eine hochgeladene Bilddatei aufweisen darf. Der Standardwert ist 2097152 (2 MB).

* **Antworten zulassen**

  Wenn diese Option aktiviert ist, können Sie Antworten auf Kommentare zulassen, die zu der Idee gepostet wurden. Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, können Sie über die Kommentare einer Idee abstimmen. Standard ist deaktiviert.

* **Benutzern das Löschen von Kommentaren und Themen ermöglichen**

  Wenn diese Option aktiviert ist, können Mitglieder die von ihnen geposteten Kommentare und Ideen löschen. Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, können Sie die folgende Funktion für Ideenbeiträge einbeziehen, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Standard ist deaktiviert.

* **E-Mail-Abonnements zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder über neue Beiträge per E-Mail benachrichtigt werden [Abonnement](/help/communities/subscriptions.md). Erfordert, dass `Allow Following` überprüft und [E-Mail konfiguriert](/help/communities/email.md). Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, können Sie über die Kommentare einer Idee abstimmen. Standard ist deaktiviert.

* **Badges anzeigen**

  Wenn diese Option aktiviert ist, werden [ und zugewiesene ](/help/communities/implementing-scoring.md) mit der Idee eines Mitglieds angezeigt. Standard ist deaktiviert.

* **Auf der Listingseite werden keine Antworten angezeigt**

* **Erlauben Sie vorgestellte Inhalte**

  Wenn diese Option aktiviert ist, kann die Idee als [vorgestellter Inhalt“ identifiziert ](/help/communities/featured.md). Standard ist deaktiviert.

* **Erwähnung aktivieren**
* **Max Erwähnungen**
* **UI-Erwähnungsmuster**

#### Registerkarte „Benutzermoderation“ {#user-moderation-tab}

Geben **[!UICONTROL auf der Registerkarte]** Benutzermoderation) an, wie die veröffentlichten Ideen und Kommentare (benutzergenerierte Inhalte) verwaltet werden sollen. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Beiträge verweigern**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Beiträge ablehnen und verhindern, dass der Beitrag im öffentlichen Forum angezeigt wird. Standard ist deaktiviert.

* **Themen schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder ein Thema für weitere Bearbeitungen und Kommentare schließen und ein Thema auch erneut öffnen. Standard ist deaktiviert.

* **Flag-Posts**

  Wenn diese Option aktiviert ist, können Mitglieder andere Themen oder Kommentare als unangemessen kennzeichnen. Standard ist deaktiviert.

* **Verursacherliste kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem sie ein Thema oder einen Kommentar als unangemessen kennzeichnen. Standard ist deaktiviert.

* **Grund für benutzerdefinierte Markierung**

  Wenn diese Option aktiviert ist, können Mitglieder ihren eigenen Grund für das Kennzeichnen eines Themas oder Kommentars als unangemessen eingeben. Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Thema oder Kommentar von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist 1 (einmal).

* **Kennzeichnungsgrenze**

  Geben Sie ein, wie oft ein Thema oder Kommentar gekennzeichnet werden muss, bevor es/er aus der öffentlichen Ansicht ausgeblendet wird. Wenn auf -1 festgelegt, wird das markierte Thema oder der Kommentar nie aus der öffentlichen Ansicht ausgeblendet. Andernfalls muss diese Zahl größer oder gleich dem Schwellenwert für die Mäßigung sein. Der Standardwert ist 5.

#### Registerkarte „Tag-Feld“ {#tag-field-tab}

Auf der Registerkarte **[!UICONTROL Tag]** sind die Tags, die angewendet werden können, wenn dies auf der Registerkarte **[!UICONTROL Einstellungen]** zulässig ist, entsprechend den ausgewählten Namespaces begrenzt.

* **Zugelassene Namespaces**

  Relevant, wenn `Allow Tagging` auf der Registerkarte **[!UICONTROL Einstellungen]** aktiviert ist. Die Tags, die angewendet werden können, sind auf die innerhalb der geprüften Namespace-Kategorien beschränkt. Die Liste der Namespaces umfasst „Standard-Tags“ (den Standard-Namespace) und „Alle Tags einschließen“. Standardmäßig ist „Keine“ aktiviert, was bedeutet, dass alle Namespaces zulässig sind.

* **Vorschlagslimit**

  Geben Sie die Anzahl der Tags ein, die als Vorschlag für das Mitglied angezeigt werden sollen, das im Forum veröffentlicht. Ein Wert von **-1** bedeutet keine Beschränkung. Der Standardwert ist 0.

#### Registerkarte „Sortiereinstellungen“ {#sort-settings-tab}

Geben Sie auf **[!UICONTROL Registerkarte]** Sortiereinstellungen“ an, wie die veröffentlichten Kommentare bei der Anzeige sortiert werden sollen.

* **Sortieren nach**

  Alle zulässigen Sortieroptionen überprüfen: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Der Standardwert ist `Newest, Oldest, Last Updated`.

* **Als Standard festlegen**

  Wählen Sie aus der Dropdown-Liste eine der aktivierten Sortieroptionen aus, die als Standard angezeigt werden sollen. Der Standardwert ist `Newest`.

* **Zeitoptionen für die Analytics-Sortierung auswählen**

  Ziehen Sie nach unten, um einen von `All, Last 24 Hours, Last 7 Days, Last 30 Days` auszuwählen. Der Standardwert ist `All`.

## Site-Besuchererlebnis {#site-visitor-experience}

### Idee wird erstellt {#creating-idea}

Wie bei allen Communities-Funktionen darf ein Site-Besucher, wenn er nicht angemeldet ist, nur Ideen lesen und andere Meinungen anzeigen (durch Kommentare und Abstimmungen/Gefällt mir).

Nach der Anmeldung kann ein Mitglied eine Idee erstellen.

![create-new-idea](assets/create-new-idea.png)

Bevor Sie die Idee einreichen, kann das Mitglied einen Entwurf speichern.

Durch Auswahl der Schaltfläche `Save as Draft` wird ein Entwurf gespeichert.

![save-idea](assets/save-idea.png)

Wählen Sie beim Anzeigen gespeicherter Entwürfe auf der Registerkarte `My Drafts` die Option `Read More` aus, um den Bearbeitungsmodus erneut aufzurufen:

![edit-idea](assets/edit-idea.png)

#### Bereitstellen von Feedback {#providing-feedback}

Sobald die Idee veröffentlicht wurde, können sich andere Mitglieder anmelden, die Idee öffnen (`Read More`) und die Idee mögen, sodass die Stimmenanzahl erhöht wird, und Kommentare abgeben.

![Feedback](assets/feedback-idea.png)

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Ideation Essentials](/help/communities/ideation.md) für Entwickler.

Informationen zur Moderation geposteter Themen und Kommentare finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging geposteter Themen und Kommentare finden Sie unter [Tagging von benutzergenerierten Inhalten](/help/communities/tag-ugc.md).
