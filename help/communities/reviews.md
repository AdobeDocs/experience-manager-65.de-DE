---
title: Verwenden von Bewertungen und Bewertungszusammenfassung (Anzeige)
seo-title: Verwenden von Bewertungen und Bewertungszusammenfassung (Anzeige)
description: Hinzufügen der Komponenten "Review and Reviews Summary"zu einer Seite
seo-description: Hinzufügen der Komponenten "Review and Reviews Summary"zu einer Seite
uuid: bd1ccee7-b26b-4a27-b1ea-89609f5080af
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bf4e7809-8def-4647-aaa6-3ac36865511f
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 39%

---


# Verwenden von Bewertungen und Bewertungszusammenfassung (Anzeige) {#using-reviews-and-reviews-summary-display}

Die Komponente `Reviews` ist ein Composite von Komponenten [Kommentare](comments.md) und [Bewertung](rating.md), die einsatzbereit sind.

Die Komponente `Reviews Summary (Display)` stellt eine Zusammenfassung einer aktiven oder geschlossenen Instanz einer Komponente `Reviews` bereit, die an einer anderen Stelle auf der Site angezeigt werden kann.

>[!NOTE]
>
>Das anonyme Posten von Bewertungen wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können. Angemeldete Besucher können ihre Bewertungen jederzeit aktualisieren.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-review-to-a-page}

Um einer Seite im Autorenmodus eine `Reviews`-Komponente hinzuzufügen, suchen Sie im Komponentenbrowser nach `Communities / Reviews` und ziehen Sie sie auf eine Seite, z. B. eine Position relativ zur Funktion, die Benutzer überprüfen müssen.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](reviews-basics.md#essentials-for-client-side) einbezogen werden, wird die `Reviews`-Komponente so angezeigt.

![create-review](assets/create-review.png)

## Konfigurieren von Bewertungen {#configuring-reviews}

Wählen Sie die platzierte Komponente `Reviews` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

Geben Sie unter der Registerkarte **[!UICONTROL Zulässige Bewertungen]** die vollständige Liste der Bewertungen an, die den Mitgliedern angezeigt werden sollen. Das erste Rating sollte ein allgemeines Rating sein, da es das Rating ist, das das durchschnittliche Rating für die Komponente `Review Summary (Display)` liefert. Die nächsten beiden Ratings in der Standardkonfiguration sollten einen anderen Titel erhalten als &quot;Unterbewertung 1&quot;oder &quot;Unterbewertung 2&quot;.

![allowed-rating](assets/configure-review1.png)

* **[!UICONTROL Zulässige Bewertungen]**

   Eine Liste von Ratings, aus denen ein Mitglied wählen kann.

    Verwenden Sie die Schaltflächen zur Bearbeitung der angezeigten Auswahl (Pfeil nach oben, Pfeil nach unten und Schaltfläche zum Löschen).

   Klicken Sie auf **[!UICONTROL Element hinzufügen]**, um eine weitere Bewertungsmöglichkeit hinzuzufügen.

Geben Sie unter der Registerkarte **[!UICONTROL Erforderliche Bewertungen]** erneut Elemente aus der Liste **[!UICONTROL Zulässige Bewertungen]** ein, die bewertet werden müssen. Wird ein Element lediglich auf der Registerkarte „Zulässige Bewertungen“ genannt, können die Mitglieder dieses Element unbewertet lassen.

Auf der Webseite werden erforderliche Bewertungen durch einen Stern gekennzeichnet. Ist die Bewertung eines Elements erforderlich, das jedoch nicht bewertet wurde, erhält das Mitglied eine Meldung und kann das Formular erst absenden, wenn das erforderliche Element bewertet wurde.

![required-rating](assets/configure-review2.png)

* **[!UICONTROL Erforderliche Bewertungen]**

   Eine Untergruppe zulässiger Ratings, die angibt, welche Ratings erforderlich sind.

    Verwenden Sie die Schaltflächen zur Bearbeitung der angezeigten Auswahl (Pfeil nach oben, Pfeil nach unten und Schaltfläche zum Löschen).

   Klicken Sie auf **[!UICONTROL Element hinzufügen]**, um eine weitere Antwortmöglichkeit hinzuzufügen.

>[!NOTE]
>
>Wenn auf der Registerkarte **[!UICONTROL Erforderliche Bewertungen]** ein Element eingegeben wird, das nicht auf der Registerkarte **[!UICONTROL Zulässige Bewertungen]** angegeben ist, wird es nicht in den zu bewertenden Elementen berücksichtigt.

Geben Sie unter der Registerkarte **[!UICONTROL Reviews]** an, wie Reviews verarbeitet werden.

![Bewertungen](assets/configure-review3.png)

* **[!UICONTROL Antworten zulassen]**

   Wenn diese Option aktiviert ist, erlauben Sie Antworten auf Überprüfungen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]**

   Wenn diese Option aktiviert ist, wird die Überprüfung für neue Überprüfungen und Antworten abgeschlossen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]**

   Wenn diese Option aktiviert ist, lassen Sie das Hochladen von Dateianlagen für die Überprüfung zu. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn **[!UICONTROL Datei-Uploads zulassen]** aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 10 MB.

* **[!UICONTROL Maximale Nachrichtenlänge]**

   Maximale Anzahl von Zeichen, die in das Textfeld eingegeben werden können. Der Standardwert ist 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]**

   Relevant nur, wenn **[!UICONTROL Datei-Uploads zulassen]** aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]**

   Wenn diese Option aktiviert ist, können Beiträge mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]**

   Wenn diese Option aktiviert ist, schließen Sie die Funktion &quot;Abstimmung&quot;für ein Thema ein. Diese Option ist standardmäßig deaktiviert.

Geben Sie unter der Registerkarte **[!UICONTROL Benutzermoderation]** an, wie die veröffentlichten Reviews verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

![user-moderation](assets/configure-review4.png)

* **[!UICONTROL Vor der Moderation]**

   Wenn diese Option aktiviert ist, müssen Überprüfungen genehmigt werden, bevor sie auf einer Veröffentlichungssite angezeigt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen löschen]**

   Wenn diese Option aktiviert ist, kann das Mitglied, das die Überprüfung veröffentlicht hat, sie löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen ablehnen]**

   Wenn diese Option aktiviert ist, können Moderatoren Reviews ablehnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen schließen/erneut öffnen]**

   Wenn diese Option aktiviert ist, können Moderatoren Prüfungen schließen und erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen kennzeichnen]**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, Überprüfungen als unangemessen zu kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kenn-zeichnungsgründen]**

   Wenn diese Option aktiviert ist, können die Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie eine Überprüfung als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung einer Überprüfung als unangemessen einzugeben. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]**

   Geben Sie an, wie oft eine Überprüfung von Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **[!UICONTROL Kennzeichnungslimit]**

   Geben Sie an, wie oft eine Überprüfung markiert werden muss, bevor sie aus der öffentlichen Ansicht ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **[!UICONTROL Schwellenwert für Moderation]** sein. Der Standardwert ist 5.

### Hinzufügen einer Bewertungszusammenfassung (Anzeige) zu einer Seite {#adding-a-review-summary-display-to-a-page}

Um eine `Reviews Summary (Display)`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente

* `Communities / Reviews Summary (Display)`

und ziehen Sie sie an eine Stelle, an der die Zusammenfassung einer aktiven oder geschlossenen Bewertung angezeigt werden soll.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](reviews-basics.md#essentials-for-client-side) einbezogen werden, wird die `Reviews Summary (Display)`Komponente so angezeigt.

![review-summary](assets/configure-review5.png)

>[!NOTE]
>
>Der Durchschnitt spiegelt das Stimmenverhältnis für das erste aufgelistete Element auf der Registerkarte „Zulässige Bewertungen“ derjenigen Bewertungen wider, die hier zusammengefasst werden.

### Konfigurieren von Bewertungszusammenfassungen (Anzeige) {#configuring-reviews-summary-display}

Wählen Sie die platzierte Komponente `Reviews Summary (Display)` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

Auf der Registerkarte **[!UICONTROL Bewertungszusammenfassung]** können Sie Folgendes festlegen:

![review-summary](assets/configure-review6.png)

* `Review Path`

   Geben Sie die platzierte Instanz der Komponente `reviews`ein oder suchen Sie sie, um sie zusammenzufassen, wenn sie der Webseite der [Geometrixx Engage-Site hinzugefügt wird,](getting-started.md) der Pfad lautet:

   `/content/sites/engage/en/page/jcr:content/content/primary/reviews`

* `Include histogram`

   Wenn diese Option aktiviert ist, fügen Sie ein Balkendiagramm hinzu, das angibt, wie viele Sternbewertungen in den zusammengefassten Reviews vorhanden sind. Diese Option ist standardmäßig deaktiviert.

### Ändern in einen benutzerdefinierten Bewertungstyp {#changing-to-a-custom-review-type}

Grundlage der Komponente „Bewertungen“ ist das Kommentarsystem.

Durch Änderung des Kommentarressourcentyps generiert das Kommentarsystem nicht mehr mithilfe des Standardsystems eine Instanz eines Kommentars, sondern mithilfe einer Einstellung, die von Entwicklern definiert (erweitert) wurde.

Sobald die benutzerdefinierten Ressourcentypen bekannt sind, geben Sie [Designmodus](../../help/sites-authoring/default-components-designmode.md) ein und klicken Sie mit der Dublette auf die platzierte `Comments`-Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Geben Sie auf der Registerkarte **[!UICONTROL Ressourcentypen]** den benutzerdefinierten resourceType für neue Instanzen der `Comments or Voting`-Komponenten an:

![comments-stimmberechtigt](assets/configure-review7.png)

* **[!UICONTROL Kommentarressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `comment`Komponente (einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`.

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wird, wenn ein Besucher einen Kommentar veröffentlicht.

* **[!UICONTROL Abstimmungs-Ressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `voting`Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`.

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wird, wenn ein Besucher eine Abstimmung veröffentlicht.

* **[!UICONTROL System-Ressourcen-Typ kommentieren]**

   Navigieren Sie zum resourceType einer erweiterten `comments`Komponente (Kommentarsystem) in /apps. Lassen Sie das Feld leer, es sei denn, die Seitenvorlage [enthält dynamisch](scf.md#add-or-include-a-communities-component) das Kommentarsystem im zugrunde liegenden Skript, anstatt der Seite als Ressource (Kommentarknoten) hinzugefügt zu werden. Weitere Informationen erhalten Sie in den Hilfethemen des[{{include}}-Helpers](handlebars-helpers.md#include).

## Site-Besuchererlebnis {#site-visitor-experience}

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer die Bewertung verfasst hat.

### Mitglieder  {#members}

Wenn der Site-Besucher angemeldet ist, kann es je nach Konfiguration zu Folgendem kommen:

* Eine neue Überprüfung posten
* Eigene Prüfung bearbeiten
* Eine eigene Überprüfung löschen
* Kommentare zur Überprüfung anderer Personen kennzeichnen

Pro Mitglied ist nur eine Bewertung zulässig.  Das Mitglied kann seine Meinung jedoch jederzeit ändern.

### Anonym  {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Bewertungen lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Bewertungen hinzufügen und keine Kommentare anderer Benutzer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Grundlegende Elemente überprüfen](reviews-basics.md) für Entwickler.

Moderation geposteter Kommentare finden Sie unter [Moderieren von benutzergenerierten Inhalten](moderate-ugc.md).

Informationen zur Übersetzung von Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
