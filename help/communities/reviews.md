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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Verwenden von Bewertungen und Bewertungszusammenfassung (Anzeige) {#using-reviews-and-reviews-summary-display}

The `Reviews`component is a composite of [ `Comments`](comments.md) and [ `Rating`](rating.md) components ready for use.

The `Reviews Summary (Display)` component provides a summary of an active or closed instance of a `Reviews` component for display elsewhere on the site.

>[!NOTE]
>
>Das anonyme Posten von Bewertungen wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können. Angemeldete Besucher können ihre Bewertungen jederzeit aktualisieren.

## Hinzufügen einer Bewertung zu einer Seite {#adding-a-review-to-a-page}

Wenn Sie einer Seite im Autorenmodus eine `Reviews` Komponente hinzufügen möchten, verwenden Sie den Komponenten-Browser, um sie zu suchen `Communities / Reviews` und an ihre Position auf einer Seite zu ziehen, z. B. eine Position relativ zur Funktion, die Benutzer überprüfen können.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](reviews-basics.md#essentials-for-client-side) are included, this is how the `Reviews`component will appear.

![chlimage_1-340](assets/chlimage_1-340.png)

## Konfigurieren von Bewertungen {#configuring-reviews}

Select the placed `Reviews` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-341](assets/chlimage_1-341.png)

Under the **[!UICONTROL Allowed Ratings]** tab, specify the complete list of ratings to be shown to members. The first rating should be an overall/general rating, as it is the rating which provides the average rating for the `Review Summary (Display)` component. Die nächsten beiden Ratings in der Standardkonfiguration sollten einen anderen Titel erhalten als &quot;Unterbewertung 1&quot;oder &quot;Unterbewertung 2&quot;.

![chlimage_1-342](assets/chlimage_1-342.png)

* **[!UICONTROL Zulässige Bewertungen]**

   Eine Liste der Bewertungen, aus denen ein Mitglied wählen kann.

    Verwenden Sie die Schaltflächen zur Bearbeitung der angezeigten Auswahl (Pfeil nach oben, Pfeil nach unten und Schaltfläche zum Löschen).

   Klicken Sie auf **[!UICONTROL Element hinzufügen]**, um eine weitere Bewertungsmöglichkeit hinzuzufügen.

Under the **[!UICONTROL Required Ratings]** tab, re-enter items from the list of **[!UICONTROL Allowed Ratings]** that are required to be rated. Wird ein Element lediglich auf der Registerkarte „Zulässige Bewertungen“ genannt, können die Mitglieder dieses Element unbewertet lassen.

Auf der Webseite werden erforderliche Bewertungen durch einen Stern gekennzeichnet. Ist die Bewertung eines Elements erforderlich, das jedoch nicht bewertet wurde, erhält das Mitglied eine Meldung und kann das Formular erst absenden, wenn das erforderliche Element bewertet wurde.

![chlimage_1-343](assets/chlimage_1-343.png)

* **[!UICONTROL Erforderliche Bewertungen]**

   Eine Untergruppe zulässiger Ratings, die angibt, welche Ratings erforderlich sind.

    Verwenden Sie die Schaltflächen zur Bearbeitung der angezeigten Auswahl (Pfeil nach oben, Pfeil nach unten und Schaltfläche zum Löschen).

   Klicken Sie auf **[!UICONTROL Element hinzufügen]**, um eine weitere Antwortmöglichkeit hinzuzufügen.

>[!NOTE]
>
>If an item is entered on the **[!UICONTROL Required Ratings]** tab that is not specified on the **[!UICONTROL Allowed Ratings]** tab, then it is not included in the items to rate.

Under the **[!UICONTROL Reviews]** tab, specify how reviews are handled.

![chlimage_1-344](assets/chlimage_1-344.png)

* **[!UICONTROL Antworten zulassen]** Ist diese Option aktiviert, können Bewertungen kommentiert werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Geschlossen]** Ist diese Option aktiviert, können in der Bewertung keine neuen Bewertungen und Kommentare erstellt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Datei-Uploads zulassen]** Ist diese Option aktiviert, können der Bewertung Dateianhänge hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

* **Max. Dateigröße ******Nur relevant, wenn die Option „Datei-Uploads zulassen“ aktiviert ist. Dieses Feld begrenzt die Größe (in Byte) einer hochgeladenen Datei. Der Standardwert ist 10 MB.

* **[!UICONTROL Maximale Nachrichtenlänge]** Die Anzahl der Zeichen, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **[!UICONTROL Zulässige Dateitypen]****** Nur relevant, wenn die Option „Datei-Uploads zulassen“ aktiviert ist. Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **[!UICONTROL Rich-Text-Editor]** Ist diese Option aktiviert, können Beiträge mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Abstimmung zulassen]** Ist diese Option aktiviert, kann die Funktion „Abstimmung“ Themen hinzugefügt werden. Diese Option ist standardmäßig deaktiviert.

Under the **[!UICONTROL User Moderation]** tab, specify how the posted reviews are managed. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](moderate-ugc.md).

![chlimage_1-345](assets/chlimage_1-345.png)

* **[!UICONTROL Vor der Moderation]** Ist diese Option aktiviert, müssen Bewertungen vor ihrer Veröffentlichung zunächst genehmigt werden. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen löschen]** Ist diese Option aktiviert, kann das Mitglied, das die Bewertung veröffentlicht hat, diese auch wieder löschen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen ablehnen]** Ist diese Option aktiviert, können Moderatoren Bewertungen ablehnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen schließen/erneut öffnen]** Ist diese Option aktiviert, können Moderatoren Bewertungen schließen oder erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Bewertungen kennzeichnen]** Ist diese Option aktiviert, können Mitglieder Bewertungen als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Liste mit Kennzeichnungsgründen]** Ist diese Option aktiviert, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem eine Bewertung als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Grund für benutzerdefinierte Kennzeichnung]** Ist diese Option aktiviert, können Mitglieder einen eigenen Grund dafür eingeben, warum sie Bewertungen als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL Schwellenwert für Moderation]** Geben Sie an, wie oft eine Bewertung von Mitgliedern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **[!UICONTROL Kennzeichnungslimit]** Geben Sie an, wie oft eine Bewertung als unangemessen gekennzeichnet werden muss, bevor sie aus dem öffentlichen Bereich ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **[!UICONTROL Schwellenwert für Moderation]** sein. Der Standardwert ist 5.

### Hinzufügen einer Bewertungszusammenfassung (Anzeige) zu einer Seite {#adding-a-review-summary-display-to-a-page}

To add a `Reviews Summary (Display)` component to a page in author mode, locate the component

* `Communities / Reviews Summary (Display)`

und ziehen Sie sie an eine Stelle, an der die Zusammenfassung einer aktiven oder geschlossenen Bewertung angezeigt werden soll.

For necessary information, visit [Communities Components Basics](basics.md).

When the [required client-side libraries](reviews-basics.md#essentials-for-client-side) are included, this is how the `Reviews Summary (Display)`component will appear.

![chlimage_1-346](assets/chlimage_1-346.png)

>[!NOTE]
>
>Der Durchschnitt spiegelt das Stimmenverhältnis für das erste aufgelistete Element auf der Registerkarte „Zulässige Bewertungen“ derjenigen Bewertungen wider, die hier zusammengefasst werden.

### Konfigurieren von Bewertungszusammenfassungen (Anzeige) {#configuring-reviews-summary-display}

Select the placed `Reviews Summary (Display)` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-347](assets/chlimage_1-347.png)

Auf der Registerkarte **[!UICONTROL Bewertungszusammenfassung]** können Sie Folgendes festlegen:

![chlimage_1-348](assets/chlimage_1-348.png)

* `Review Path`

   Geben Sie die platzierte Instanz der `reviews`Komponente ein oder suchen Sie nach dieser, um sie zusammenzufassen, wenn sie der Webseite der [Geometrixx-Engage-Site hinzugefügt wird. Der Pfad lautet beispielsweise](getting-started.md) :

   /content/sites/engagement/de/page/jcr:content/content/primary/reviews

* `Include histogram`

   Wenn diese Option aktiviert ist, fügen Sie ein Balkendiagramm hinzu, das angibt, wie viele Sternbewertungen in den zusammengefassten Reviews vorhanden sind. Diese Option ist standardmäßig deaktiviert.

### Ändern in einen benutzerdefinierten Bewertungstyp {#changing-to-a-custom-review-type}

Grundlage der Komponente „Bewertungen“ ist das Kommentarsystem.

Durch Änderung des Kommentarressourcentyps generiert das Kommentarsystem nicht mehr mithilfe des Standardsystems eine Instanz eines Kommentars, sondern mithilfe einer Einstellung, die von Entwicklern definiert (erweitert) wurde.

Once the custom resource types is known, enter [Design Mode](../../help/sites-authoring/default-components-designmode.md) and double click on the placed `Comments` component to open a dialog with an additional tab.

Under the **[!UICONTROL Resource Types]** tab, specify the custom resourceType for new instances of the `Comments or Voting`components:

![chlimage_1-349](assets/chlimage_1-349.png)

* **[!UICONTROL Kommentarressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `comment`Komponente (ein einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wird, wenn ein Besucher einen Kommentar veröffentlicht.

* **[!UICONTROL Abstimmungs-Ressourcentyp]**

   Navigieren Sie zum resourceType einer erweiterten `voting`Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wird, wenn ein Besucher eine Stimme veröffentlicht.

* **[!UICONTROL System-Ressourcen-Typ kommentieren]**

   Navigieren Sie zum resourceType einer erweiterten `comments`Komponente (Kommentarsystem) in /apps. Leave blank unless the page template [dynamically includes](scf.md#add-or-include-a-communities-component) the Comment System in the underlying script instead of being added to the page as a resource (comments node). Weitere Informationen erhalten Sie in den Hilfethemen des[{{include}}-Helpers](handlebars-helpers.md#include)

## Site-Besuchererlebnis {#site-visitor-experience}

### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer die Bewertung verfasst hat.

### Mitglieder {#members}

Abhängig von der Konfiguration können angemeldete Besucher Folgendes tun:

* Eine neue Überprüfung posten
* Eigene Prüfung bearbeiten
* Eine eigene Überprüfung löschen
* Kommentare zur Überprüfung anderer Personen kennzeichnen

Pro Mitglied ist nur eine Bewertung zulässig.  Das Mitglied kann seine Meinung jedoch jederzeit ändern.

### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Bewertungen lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Bewertungen hinzufügen und keine Kommentare anderer Benutzer kennzeichnen.

## Zusätzliche Informationen {#additional-information}

More information may be found on the [Review Essentials](reviews-basics.md) page for developers.

For moderation of posted comments, see [Moderating User Generated Content](moderate-ugc.md).

Informationen zur Übersetzung von Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](translate-ugc.md).
