---
title: Verwenden von Kommentaren
description: Mithilfe der Kommentarfunktion können angemeldete Site-Besucher ihre Meinungen und ihr Wissen teilen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 30baebd9-13c5-4fde-a494-85601abc32a5
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 2%

---

# Verwenden von Kommentaren {#using-comments}

## Einführung {#introduction}

Die Funktion „Kommentare“ wird verwendet, um angemeldeten Besuchern (Mitgliedern) der Site zu ermöglichen, ihre Meinungen und ihr Wissen zu Inhalten auf der Site zu teilen. Diese Funktion ist häufig bereits in anderen Funktionen vorhanden, kann jedoch zu jeder Website hinzugefügt werden.

In dem Dokument wird Folgendes beschrieben:

* Hinzufügen von `Comments` zu einer Seite.
* Konfigurationseinstellungen für die `Comments`.

>[!NOTE]
>
>Das anonyme Posten eines Kommentars wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglied werden) und sich anmelden, um teilzunehmen.

### Kommentare zu einer Seite hinzufügen {#adding-comments-to-a-page}

Um einer Seite im Autorenmodus eine `Comments` Komponente hinzuzufügen, suchen Sie im Komponenten-Browser nach

* `Communities / Comments`

und ziehen Sie sie auf eine Seite, z. B. eine Position relativ zum Feature, zu der Benutzende einen Kommentar abgeben können, oder einfach unten auf der Seite.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](/help/communities/essentials-comments.md#essentials-for-client-side) enthalten sind, wird die `Comments` Komponente wie folgt angezeigt.

![comments-component](assets/comments-component.png)

>[!NOTE]
>
>Auf einer Seite darf nur eine `Comments` Komponente vorhanden sein. Beachten Sie, dass mehrere Communities-Funktionen bereits Kommentare enthalten, z. B. einen Blog, einen Kalender, ein Forum, eine QnA und Bewertungen.

### Kommentare konfigurieren {#configuring-comments}

Wählen Sie die platzierte `Comments` aus, auf die Sie zugreifen möchten, und wählen Sie das `Configure` aus, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurationssymbol](assets/configure.png)

![CommentsSettings](assets/commentssettings.png)

#### Registerkarte „Kommentare“ {#comments-tab}

Geben Sie auf **Registerkarte** Kommentare“ an, wie Kommentare von Besuchern eingegeben werden sollen.

* **Antworten zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder auf vorhandene Kommentare antworten. Die Auswahl von Standard ist deaktiviert.

* **Kommentare pro Seite**

  Beschränkt die Anzahl der angezeigten Kommentare pro Seite und die Anzahl der angezeigten Antworten. Der Standardwert ist 10.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, wird die Option zum Hochladen einer Datei mit dem Texteingabefeld angezeigt. Die Auswahl von Standard ist deaktiviert.

* **max. Dateigröße**

  Nur relevant, wenn Datei-Uploads zulassen aktiviert ist. Dieser Wert begrenzt die Größe der hochgeladenen Datei. Das Standardlimit ist 10 MB.

* **Max. Nachrichtenlänge**

  Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **Zulässige Dateitypen**

  Nur relevant, wenn Datei-Uploads zulassen aktiviert ist. Eine kommagetrennte Liste von Dateinamenerweiterungen mit dem Punkttrennzeichen. Zum Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn irgendwelche Dateitypen angegeben werden, dann sind die nicht angegebenen nicht zulässig. Der Standardwert ist nicht angegeben, sodass alle Dateitypen zulässig sind.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, werden Kommentare mit Markup eingegeben. Die Auswahl von Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, wird die Option, nach oben oder unten zu wählen, mit dem Texteingabefeld angezeigt. Die Auswahl von Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Kommentaren folgen. Die Auswahl von Standard ist deaktiviert.

* **Badges anzeigen**

  Wenn diese Option aktiviert ist, können verdiente und verliehene Abzeichen angezeigt werden. Die Auswahl von Standard ist deaktiviert.

#### Registerkarte „Benutzermoderation“ {#user-moderation-tab}

Geben **auf der Registerkarte** User Moderation“ an, wie die veröffentlichten Kommentare verwaltet werden sollen. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Vormoderation**

  Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Die Auswahl von Standard ist deaktiviert.

* **Kommentare löschen**

  Wenn diese Option aktiviert ist, kann das Mitglied, das den Kommentar veröffentlicht hat, ihn löschen. Die Auswahl von Standard ist deaktiviert.

* **Kommentare ablehnen**

  Wenn diese Option aktiviert ist, können Moderatoren Kommentare ablehnen. Die Auswahl von Standard ist deaktiviert.

* **Kommentare schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren Kommentare schließen und erneut öffnen. Die Auswahl von Standard ist deaktiviert.

* **Kennzeichnen von Kommentaren**

  Wenn diese Option aktiviert ist, können Mitglieder Kommentare als unangemessen kennzeichnen. Die Auswahl von Standard ist deaktiviert.

* **Verursacherliste kennzeichnen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste auswählen, warum sie einen Kommentar als unangebracht kennzeichnen möchten. Die Auswahl von Standard ist deaktiviert.

* **Grund für benutzerdefinierte Markierung**

  Wenn diese Option aktiviert ist, können Mitglieder ihren eigenen Grund eingeben, warum sie einen Kommentar als unangemessen kennzeichnen. Die Auswahl von Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Kommentar von den Mitgliedern markiert werden muss, bevor Moderatoren benachrichtigt werden. Standard ist Einmal (1).

* **Kennzeichnungsgrenze**

  Geben Sie ein, wie oft ein Kommentar gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Diese Zahl muss größer oder gleich dem **Moderationsschwellenwert“**. Der Standardwert ist 5.

#### Registerkarte „Sortiereinstellungen“ {#sort-settings-tab}

Geben Sie auf **Registerkarte** Sortiereinstellungen“ an, wie die veröffentlichten Kommentare bei der Anzeige sortiert werden sollen.

* **Sortierfeld**

  Ziehen Sie den Mauszeiger nach unten, um eine der `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed` oder `Most Liked` auszuwählen.

* **Sortierreihenfolge**

  Ziehen Sie nach unten, um eine der `Ascending` oder `Descending` auszuwählen.

### Wechseln zu einem benutzerdefinierten Kommentartyp {#changing-to-a-custom-comment-type}

Durch das Ändern des Ressourcentyps für Kommentare generiert das Kommentarsystem keine Instanz eines Kommentars mehr mit der Standardeinstellung, sondern eine, die von Entwicklerinnen und Entwicklern angepasst (erweitert) wurde.

Sobald die benutzerdefinierten Ressourcentypen bekannt sind, wechseln Sie [Design-Modus](/help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Comments`, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Geben **auf der Registerkarte** Ressourcentypen“ den benutzerdefinierten resourceType für neue Instanzen der `Comments or Voting` Komponenten an:

![resource-type](assets/resource-type.png)

* **Kommentar-Ressourcentyp**

  Navigieren Sie zum resourceType einer erweiterten `comment`-Komponente (einzelner Kommentar) in /apps. Zum Beispiel: `/apps/social/commons/components/hbs/comments/comment`

  Diese Ressource identifiziert den resourceType des UGC, der erstellt wird, wenn ein Besucher einen Kommentar postet.

* **Abstimmungsressourcentyp**

  Navigieren Sie zum resourceType einer erweiterten `voting` in /apps. Zum Beispiel: `/apps/social/components/hbs/voting`

  Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wird, wenn ein Besucher eine Abstimmung postet.

* **Systemressourcentyp kommentieren**

  Navigieren Sie zum resourceType einer erweiterten Komponente `comments`Kommentarsystem) in /apps. Leer lassen, es sei denn, [&#x200B; Seitenvorlage fügt &#x200B;](/help/communities/scf.md#add-or-include-a-communities-component) Kommentarsystem dem zugrunde liegenden Skript hinzu, anstatt zur Seite als Ressource hinzugefügt zu werden (Knoten „comments„). Weitere Informationen finden Sie im Abschnitt über den [`{{include}}` Helper](/help/communities/handlebars-helpers.md#include).

### Site-Besuchererlebnis {#site-visitor-experience}

#### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorrechte verfügt, kann er die durch die Konfiguration der Komponente zulässigen Moderationsaufgaben ausführen, unabhängig davon, wer den Kommentar verfasst hat.

#### Mitglieder {#members}

Wenn der Site-Besucher angemeldet ist, kann er je nach Konfiguration

* Einen neuen Kommentar posten
* Bearbeiten eines eigenen Kommentars
* Eigenen Kommentar löschen
* Kennzeichnet Kommentare anderer Benutzer.

#### Anonym {#anonymous}

Website-Besucherinnen und -Besucher, die nicht angemeldet sind, dürfen nur gepostete Kommentare lesen, diese übersetzen, falls sie unterstützt werden, aber keinen Kommentar hinzufügen oder die Kommentare anderer kennzeichnen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Comments Essentials](/help/communities/essentials-comments.md) für Entwickler.

Informationen zur Moderation geposteter Kommentare finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zur Übersetzung von geposteten Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
