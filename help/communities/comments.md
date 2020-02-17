---
title: Verwenden von Kommentaren
seo-title: Verwenden von Kommentaren
description: Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern, ihre Meinung und ihr Wissen zu teilen
seo-description: Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern, ihre Meinung und ihr Wissen zu teilen
uuid: 40acd962-846c-483c-b789-aab3a7d2b31b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 216cfb3e-777e-4773-afba-749debdca000
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Verwenden von Kommentaren{#using-comments}

## Einführung {#introduction}

Die Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern (Mitgliedern), ihre Meinung und ihre Kenntnisse bezüglich der Site-Inhalte kundzutun. Diese Funktion ist in der Regel bereits in anderen Funktionen enthalten, kann jedoch auch beliebigen Websites hinzugefügt werden.

Das Dokument beschreibt:

* adding `Comments`to a page.
* configuration settings for the `Comments`component.

>[!NOTE]
>
>Das anonyme Posten von Kommentaren wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

### Hinzufügen von Kommentaren zu einer Seite {#adding-comments-to-a-page}

To add a `Comments`component to a page in author mode, use the component browser to locate

* `Communities / Comments`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. in die Nähe einer Eigenschaft, die Benutzer kommentieren sollen, oder fügen Sie die Komponente am Ende der Seite ein.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/essentials-comments.md#essentials-for-client-side) are included, this is how the `Comments`component appears.

![chlimage_1-143](assets/chlimage_1-143.png)

>[!NOTE]
>
>Only one `Comments`component may exist on a page. Beachten Sie, dass mehrere Communities-Funktionen bereits Kommentare enthalten, z. B. ein Blog, ein Kalender, ein Forum, eine QnA-Datei und Rezensionen.

### Konfigurieren von Kommentaren {#configuring-comments}

Select the placed `Comments` component to access and select the `Configure` icon which opens the edit dialog.

![Symbolkommentare](assets/configure.png) ![konfigurieren](assets/commentssettings.png)

#### Registerkarte &quot;Kommentare&quot; {#comments-tab}

Legen Sie auf der Registerkarte **Kommentare** fest, wie Benutzer Kommentare eingeben sollen.

* **Antworten zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder auf vorhandene Kommentare antworten. Die Option &quot;Standard&quot;ist deaktiviert.

* **Kommentare pro Seite**

   Begrenzt die Anzahl der pro Seite angezeigten Kommentare und die Anzahl der angezeigten Antworten. Der Standardwert ist 10.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, wird das Textfeld zum Hochladen einer Datei angezeigt. Die Option &quot;Standard&quot;ist deaktiviert.

* **Max. Dateigröße**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Dieser Wert begrenzt die Größe der hochgeladenen Datei. Der Standardwert ist 10 MB.

* **Maximale Nachrichtenlänge**

   Maximale Anzahl von Zeichen, die in das Textfeld eingegeben werden können. Der Standardwert ist 4096 Zeichen.

* **Zulässige Dateitypen**

   Relevant nur, wenn &quot;Datei-Uploads zulassen&quot;aktiviert ist. Eine kommagetrennte Liste mit Dateinamenerweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, sind nicht angegebene Dateitypen nicht zulässig. Der Standardwert ist nicht angegeben, sodass** **alle Dateitypen zulässig sind.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, werden Kommentare mit Markup eingegeben. Die Option &quot;Standard&quot;ist deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, wird das Textfeld angezeigt, in dem die Option für die Abstimmung aktiviert oder deaktiviert ist. Die Option &quot;Standard&quot;ist deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, können Sie den Mitgliedern Kommentare folgen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, lassen Sie die Anzeige von verdienten und zuerkannten Abzeichen zu. Die Option &quot;Standard&quot;ist deaktiviert.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation **an, wie die veröffentlichten Kommentare verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Vor der Moderation** Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungssite angezeigt werden. Die Option &quot;Standard&quot;ist deaktiviert.

* **Kommentare löschen**

   Wenn diese Option aktiviert ist, kann das Mitglied, das den Kommentar veröffentlicht hat, ihn löschen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Kommentare ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare ablehnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Kommentare schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare schließen und erneut öffnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Kommentare kennzeichnen**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, Kommentare als unangemessen zu kennzeichnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste auswählen, aus welchem Grund sie einen Kommentar als unangemessen kennzeichnen. Die Option &quot;Standard&quot;ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Sie Mitgliedern gestatten, einen eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen einzugeben. Die Option &quot;Standard&quot;ist deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Kommentar von den Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Kommentar markiert werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **Schwellenwert für Moderation** sein. Der Standardwert ist 5.

#### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Geben Sie unter der Registerkarte **Sortiereinstellungen **an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfeld**

   Ziehen Sie nach unten, um einen von `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`oder `Most Liked`auszuwählen.

* **Sortierreihenfolge**

   Ziehen Sie nach unten, um einen von `Ascending` oder `Descending`auszuwählen.

### Ändern in einen benutzerdefinierten Kommentartyp {#changing-to-a-custom-comment-type}

Durch Änderung des Kommentarressource-Typs generiert das Kommentarsystem nicht mehr eine Instanz eines Kommentars, die standardmäßig verwendet wird, sondern eine Instanz, die von Entwicklern angepasst (erweitert) wurde.

Once the custom resource types are known, enter [Design Mode](/help/sites-authoring/default-components-designmode.md) and double click the placed `Comments` component to open a dialog with an extra tab.

Under the **Resource Types **tab, specify the custom resourceType for new instances of the `Comments or Voting`components:

![chlimage_1-144](assets/chlimage_1-144.png)

* **Kommentarressourcentyp**

   Navigieren Sie zum resourceType einer erweiterten `comment`Komponente (ein einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wird, wenn ein Besucher einen Kommentar veröffentlicht.

* **Abstimmungs-Ressourcentyp**

   Navigieren Sie zum resourceType einer erweiterten `voting`Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wird, wenn ein Besucher eine Stimme veröffentlicht.

* **System-Ressourcen-Typ kommentieren**

   Navigieren Sie zum resourceType einer erweiterten `comments`Komponente (Kommentarsystem) in /apps. Leave blank unless the page template [dynamically includes](/help/communities/scf.md#add-or-include-a-communities-component) the Comment System in the underlying script instead of being added to the page as a resource (comments node). Weitere Informationen erhalten Sie in den Hilfethemen des[{{include}}-Helpers](/help/communities/handlebars-helpers.md#include).

### Site-Besuchererlebnis {#site-visitor-experience}

#### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer den Kommentar verfasst hat.

#### Mitglieder {#members}

Abhängig von der Konfiguration können angemeldete Besucher Folgendes tun:

* Veröffentlichen neuer Kommentare
* Bearbeiten eigener Kommentare
* Löschen eigener Kommentare
* Kennzeichnen von Kommentaren anderer Mitglieder

#### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Kommentare hinzufügen und keine Kommentare anderer Benutzer kennzeichnen.

### Zusätzliche Informationen {#additional-information}

More information may be found on the [Comments Essentials](/help/communities/essentials-comments.md) page for developers.

For moderation of posted comments, see [Moderating User Generated Content](/help/communities/moderate-ugc.md).

Informationen zur Übersetzung von Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
