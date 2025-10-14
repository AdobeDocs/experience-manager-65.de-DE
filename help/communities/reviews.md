---
title: Verwenden der Zusammenfassung von Überprüfungen und Überprüfungen (Anzeige)
description: Erfahren Sie, wie Sie die Übersichtskomponenten „Überprüfungen“ und „Überprüfungen“ zu einer Seite hinzufügen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 170414a6-c40b-4ad2-9294-7c2266850c3d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 1%

---

# Verwenden der Zusammenfassung von Überprüfungen und Überprüfungen (Anzeige) {#using-reviews-and-reviews-summary-display}

Die `Reviews` Komponente ist eine Kombination aus [Kommentaren](comments.md) und [Bewertung](rating.md) Komponenten, die einsatzbereit sind.

Die `Reviews Summary (Display)`-Komponente bietet eine Zusammenfassung einer aktiven oder geschlossenen Instanz einer `Reviews`-Komponente zur Anzeige an einer anderen Stelle auf der Site.

>[!NOTE]
>
>Das anonyme Posten einer Überprüfung wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglied werden) und sich anmelden, um teilzunehmen. Der angemeldete Besucher kann seine Überprüfung jederzeit aktualisieren.

## Hinzufügen einer Überprüfung zu einer Seite {#adding-a-review-to-a-page}

Um einer Seite im Autorenmodus eine `Reviews` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach `Communities / Reviews` und ziehen Sie sie an die gewünschte Position auf der Seite (z. B. relativ zur Funktion).

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](reviews-basics.md#essentials-for-client-side) enthalten sind, wird die `Reviews` Komponente wie folgt angezeigt.

![create-review](assets/create-review.png)

## Konfigurieren von Überprüfungen {#configuring-reviews}

Wählen Sie die platzierte `Reviews` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

Geben Sie auf **[!UICONTROL Registerkarte]** Zulässige Bewertungen“ die vollständige Liste der den Mitgliedern anzuzeigenden Bewertungen an. Das erste Rating sollte ein Gesamt-/allgemeines Rating sein, da es sich um das Rating handelt, das das durchschnittliche Rating für die `Review Summary (Display)` Komponente liefert. Die nächsten beiden Bewertungen in der Standardkonfiguration sollten einen anderen Titel erhalten als „Unterbewertung 1“ oder „Unterbewertung 2“.

![allowed-rating](assets/configure-review1.png)

* **[!UICONTROL Zulässige Bewertungen]**

  Eine Liste von Bewertungen, aus denen ein Mitglied auswählen kann.

  Mit den Schaltflächen Nach oben, Nach unten und Löschen können Sie die sichtbaren Auswahlen ändern.

  Klicken Sie **[!UICONTROL Element hinzufügen]**, um eine weitere Bewertungsauswahl hinzuzufügen.

Geben Sie auf **[!UICONTROL Registerkarte]** Erforderliche Bewertungen“ Elemente aus der Liste der **[!UICONTROL Zulässigen Bewertungen]**, die für die Bewertung erforderlich sind, erneut ein. Wenn ein Element nur auf der Registerkarte Zulässige Bewertungen angegeben wird, kann es beim Senden durch das Mitglied unmarkiert bleiben.

Auf der Website sind die erforderlichen Bewertungen mit einem Sternchen gekennzeichnet. Wenn ein Element erforderlich ist und nicht markiert bleibt, wird eine Meldung an das Mitglied angezeigt und die Übermittlung wird abgelehnt, bis alle erforderlichen Bewertungen markiert sind.

![required-rating](assets/configure-review2.png)

* **[!UICONTROL Erforderliche Bewertungen]**

  Eine Untergruppe zulässiger Berechtigungen, die angibt, welche Berechtigungen erforderlich sind.

  Mit den Schaltflächen Nach oben, Nach unten und Löschen können Sie die sichtbaren Auswahlen ändern.

  Klicken Sie **[!UICONTROL Element hinzufügen]**, um eine weitere Antwortauswahl hinzuzufügen.

>[!NOTE]
>
>Wenn auf der Registerkarte **[!UICONTROL Erforderliche Bewertungen]** ein Element eingegeben wird, das auf der Registerkarte **[!UICONTROL Zulässige]** nicht angegeben ist, wird es nicht in die zu bewertenden Elemente aufgenommen.

Geben Sie auf **[!UICONTROL Registerkarte]**&#x200B;Überprüfungen“ an, wie Überprüfungen verarbeitet werden sollen.

![Bewertungen](assets/configure-review3.png)

* **[!UICONTROL Antworten zulassen]**

  Wenn diese Option aktiviert ist, können Sie Antworten auf Überprüfungen zulassen. Standard ist deaktiviert.

* **[!UICONTROL Geschlossen]**

  Wenn diese Option aktiviert ist, wird die Überprüfung für neue Überprüfungen und Antworten geschlossen. Standard ist deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**

  Wenn diese Option aktiviert ist, können Dateianhänge zur Überprüfung hochgeladen werden. Standard ist deaktiviert.

* **max. Dateigröße**

  Nur relevant, wenn **[!UICONTROL Datei-Uploads zulassen]** aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 10 MB.

* **[!UICONTROL Max. Nachrichtenlänge]**

  Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]**

  Nur relevant, wenn **[!UICONTROL Datei-Uploads zulassen]** aktiviert ist. Eine kommagetrennte Liste von Dateierweiterungen mit dem Punkttrennzeichen. Zum Beispiel .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn irgendwelche Dateitypen angegeben werden, dann sind die nicht angegebenen nicht zulässig. Der Standardwert ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]**

  Wenn diese Option aktiviert ist, können Beiträge mit Aufschlag eingegeben werden. Standard ist deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**

  Wenn diese Option aktiviert ist, wird die Abstimmungsfunktion für ein Thema einbezogen. Standard ist deaktiviert.

Geben **[!UICONTROL auf der Registerkarte]** User Moderation“ an, wie die veröffentlichten Reviews verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

![User-Moderation](assets/configure-review4.png)

* **[!UICONTROL Vormoderation]**

  Wenn diese Option aktiviert ist, müssen Überprüfungen genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Standard ist deaktiviert.

* **[!UICONTROL Überprüfungen löschen]**

  Wenn diese Option aktiviert ist, kann das Mitglied, das die Überprüfung veröffentlicht hat, sie löschen. Standard ist deaktiviert.

* **[!UICONTROL Rezensionen verweigern]**

  Wenn diese Option aktiviert ist, können Moderatoren Überprüfungen verweigern. Standard ist deaktiviert.

* **[!UICONTROL Rezensionen schließen/erneut öffnen]**

  Wenn diese Option aktiviert ist, können Moderatoren Reviews schließen und erneut öffnen. Standard ist deaktiviert.

* **[!UICONTROL Flag-Überprüfungen]**

  Wenn diese Option aktiviert ist, können Mitglieder Reviews als unangemessen kennzeichnen. Standard ist deaktiviert.

* **[!UICONTROL Verursacherliste kennzeichnen]**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste auswählen, warum sie eine Überprüfung als unangemessen kennzeichnen möchten. Standard ist deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Markierung]**

  Wenn diese Option aktiviert ist, können Mitglieder ihren eigenen Grund eingeben, aus dem eine Überprüfung als unangemessen markiert wird. Standard ist deaktiviert.

* **[!UICONTROL Moderationsschwellenwert]**

  Geben Sie an, wie oft Mitglieder eine Überprüfung kennzeichnen müssen, bevor Moderatoren benachrichtigt werden. Standard ist Einmal (1).

* **[!UICONTROL Kennzeichnungsgrenze]**

  Geben Sie an, wie oft eine Überprüfung gekennzeichnet werden muss, bevor sie aus der öffentlichen Ansicht ausgeblendet wird. Diese Zahl muss größer oder gleich dem **[!UICONTROL Moderationsschwellenwert“]**. Der Standardwert ist 5.

### Hinzufügen einer Prüfungszusammenfassung (Anzeige) zu einer Seite {#adding-a-review-summary-display-to-a-page}

Suchen Sie die Komponente, um einer Seite im Autorenmodus eine `Reviews Summary (Display)` Komponente hinzuzufügen

* `Communities / Reviews Summary (Display)`

und ziehen Sie sie auf eine Seite, auf der eine Zusammenfassung einer aktiven oder geschlossenen Überprüfung angezeigt werden soll.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](basics.md).

Wenn die [erforderlichen Client-seitigen Bibliotheken](reviews-basics.md#essentials-for-client-side) enthalten sind, wird die Komponente `Reviews Summary (Display)`auf diese Weise angezeigt.

![review-summary](assets/configure-review5.png)

>[!NOTE]
>
>Der „Durchschnitt“ spiegelt die Stimmen für den ersten Eintrag wider, der auf den Registerkarten „Zulässige Bewertungen“ der zusammenfassenden Überprüfung aufgeführt ist.

### Konfigurieren der Reviews-Zusammenfassung (Anzeige) {#configuring-reviews-summary-display}

Wählen Sie die platzierte `Reviews Summary (Display)` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

Auf der Registerkarte **[!UICONTROL Zusammenfassung überprüfen]**

![review-summary](assets/configure-review6.png)

* `Review Path`

  Geben Sie die platzierte Instanz der `reviews`-Komponente ein oder navigieren Sie zu ihr, um sie zusammenzufassen. Wenn sie beispielsweise zur Web-Seite der [Geometrixx Engage-Site hinzugefügt wird, lautet &#x200B;](getting-started.md) Pfad:

  `/content/sites/engage/en/page/jcr:content/content/primary/reviews`

* `Include histogram`

  Wenn diese Option aktiviert ist, wird ein Balkendiagramm angezeigt, das angibt, wie viele Sterne in den zusammengefassten Bewertungen enthalten sind. Standard ist deaktiviert.

### Wechsel zu einem benutzerdefinierten Überprüfungstyp {#changing-to-a-custom-review-type}

Die Komponente Überprüfungen verwendet das Kommentarsystem.

Durch das Ändern des Ressourcentyps für Kommentare generiert das Kommentarsystem keine Instanz eines Kommentars mehr mit der Standardeinstellung, sondern eine, die von Entwicklerinnen und Entwicklern angepasst (erweitert) wurde.

Wenn die benutzerdefinierten Ressourcentypen bekannt sind, wechseln Sie [Design-Modus](../../help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Comments`, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Geben **[!UICONTROL auf der Registerkarte]** Ressourcentypen“ den benutzerdefinierten resourceType für neue Instanzen der `Comments or Voting` Komponenten an:

![comments-vote](assets/configure-review7.png)

* **[!UICONTROL Kommentar-Ressourcentyp]**

  Navigieren Sie zum resourceType einer erweiterten `comment` (einzelner Kommentar) in /apps. Zum Beispiel: `/apps/social/commons/components/hbs/comments/comment`.

  Diese Ressource identifiziert den resourceType des UGC, der erstellt wird, wenn ein Besucher einen Kommentar postet.

* **[!UICONTROL Abstimmungsressourcentyp]**

  Navigieren Sie in /apps zum resourceType `voting` erweiterten Komponente . Zum Beispiel: `/apps/social/components/hbs/voting`.

  Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wird, wenn ein Besucher eine Abstimmung postet.

* **[!UICONTROL Systemressourcentyp kommentieren]**

  Navigieren Sie zum resourceType einer erweiterten Komponente `comments`Kommentarsystem) in /apps. Leer lassen, es sei denn, [&#x200B; Seitenvorlage fügt &#x200B;](scf.md#add-or-include-a-communities-component) Kommentarsystem dem zugrunde liegenden Skript hinzu, anstatt zur Seite als Ressource hinzugefügt zu werden (Knoten „comments„). Weitere Informationen finden Sie im Abschnitt über den [`{{include}}` Helper](handlebars-helpers.md#include).

## Site-Besuchererlebnis {#site-visitor-experience}

### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorrechte verfügt, kann er die durch die Konfiguration der Komponente zulässigen Moderationsaufgaben ausführen, unabhängig davon, wer die Überprüfung verfasst hat.

### Mitglieder {#members}

Wenn der Site-Besucher angemeldet ist, kann er je nach Konfiguration:

* Neue Überprüfung posten
* Eigene Überprüfung bearbeiten
* Eigene Überprüfung löschen
* Kennzeichnen der Kommentare anderer Benutzer zur Überprüfung

Pro Mitglied ist nur eine Bewertung zulässig. Das Mitglied kann seine Bewertung jederzeit ändern.

### Anonym {#anonymous}

Besuchende der Site, die nicht angemeldet sind, dürfen nur gepostete Rezensionen lesen, diese übersetzen, falls sie unterstützt werden, aber keine Bewertung oder Rezension hinzufügen oder die Rezensionskommentare anderer Personen kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Grundlagen überprüfen](reviews-basics.md) für Entwickler.

Informationen zur Moderation geposteter Kommentare finden Sie unter [Moderieren benutzergenerierter Inhalte](moderate-ugc.md).

Informationen zur Übersetzung von geposteten Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](translate-ugc.md).
