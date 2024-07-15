---
title: Kommentare verwenden
description: Mit der Kommentarfunktion können angemeldete Site-Besucher ihre Meinungen und ihr Wissen austauschen
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

# Kommentare verwenden {#using-comments}

## Einführung {#introduction}

Die Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern (Mitgliedern), ihre Meinungen und Kenntnisse über Inhalte auf der Site zu teilen. Diese Funktion ist oft bereits in anderen Funktionen vorhanden, kann aber zu jeder Website hinzugefügt werden.

Das Dokument beschreibt:

* Hinzufügen von `Comments` zu einer Seite.
* Konfigurationseinstellungen für die Komponente `Comments` .

>[!NOTE]
>
>Das anonyme Posten eines Kommentars wird nicht unterstützt. Besucher der Site müssen sich registrieren (Mitglied werden) und sich anmelden, um teilnehmen zu können.

### Hinzufügen von Kommentaren zu einer Seite {#adding-comments-to-a-page}

Möchten Sie im Autorenmodus einer Seite die Komponente `Comments` hinzufügen, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Comments`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. an die Position relativ zur Funktion, zu der Benutzer Kommentare abgeben können, oder einfach am unteren Seitenrand.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [ erforderlichen clientseitigen Bibliotheken](/help/communities/essentials-comments.md#essentials-for-client-side) enthalten sind, wird die Komponente `Comments` so angezeigt.

![comments-component](assets/comments-component.png)

>[!NOTE]
>
>Auf einer Seite kann nur eine `Comments` -Komponente vorhanden sein. Beachten Sie, dass mehrere Communities-Funktionen bereits Kommentare enthalten, wie z. B. Blog, Kalender, Forum, Fragen und Antworten.

### Kommentare konfigurieren {#configuring-comments}

Wählen Sie die platzierte Komponente `Comments` aus, um auf das Symbol `Configure` zuzugreifen, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![Konfigurationssymbol](assets/configure.png)

![commentsettings](assets/commentssettings.png)

#### Registerkarte &quot;Kommentare&quot; {#comments-tab}

Geben Sie auf der Registerkarte **Kommentare** an, wie Kommentare von Besuchern eingegeben werden.

* **Antworten zulassen**

  Ist diese Option aktiviert, können Mitglieder auf vorhandene Kommentare antworten. Die Option Standard ist deaktiviert.

* **Kommentare pro Seite**

  Beschränkt die Anzahl der pro Seite angezeigten Kommentare und die angezeigte Anzahl der Antworten. Der Standardwert ist 10.

* **Datei-Uploads zulassen**

  Wenn diese Option aktiviert ist, wird die Option zum Hochladen einer Datei mit dem Texteingabefeld angezeigt. Die Option Standard ist deaktiviert.

* **Maximale Dateigröße**

  Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Dieser Wert begrenzt die Größe der hochgeladenen Datei. Der Standardwert ist 10 MB.

* **Max. Nachrichtenlänge**

  Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert beträgt 4096 Zeichen.

* **Zulässige Dateitypen**

  Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Eine kommagetrennte Liste von Dateinamenerweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, sind die nicht angegebenen nicht zulässig. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, werden Kommentare mit Markup eingegeben. Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, wird das Texteingabefeld angezeigt. Die Option Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Kommentare folgen. Die Option Standard ist deaktiviert.

* **Anzeigemarke**

  Wenn diese Option aktiviert ist, können Sie die Anzeige von verdienten und vergebenen Abzeichen zulassen. Die Option Standard ist deaktiviert.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Geben Sie auf der Registerkarte **Benutzermoderation** an, wie die veröffentlichten Kommentare verwaltet werden. Weitere Informationen finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Vormoderation**

  Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Die Option Standard ist deaktiviert.

* **Kommentare löschen**

  Wenn diese Option aktiviert ist, kann das Mitglied, das den Kommentar veröffentlicht hat, ihn löschen. Die Option Standard ist deaktiviert.

* **Kommentare ablehnen**

  Wenn diese Option aktiviert ist, können Moderatoren Kommentare ablehnen. Die Option Standard ist deaktiviert.

* **Kommentare schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren Kommentare schließen und erneut öffnen. Die Option Standard ist deaktiviert.

* **Kommentare kennzeichnen**

  Ist diese Option aktiviert, können Mitglieder Kommentare als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste mit Kennzeichnungsgründen**

  Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Kommentar als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

  Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie an, wie oft ein Kommentar von den Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **Kennzeichnungslimit**

  Geben Sie an, wie oft ein Kommentar gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Diese Zahl muss größer oder gleich dem **Moderationsschwellenwert** sein. Der Standardwert ist 5.

#### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Geben Sie auf der Registerkarte **Sortiereinstellungen** an, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfeld**

  Ziehen Sie nach unten, um einen von `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed` oder `Most Liked` auszuwählen.

* **Sortierreihenfolge**

  Ziehen Sie nach unten, um einen von `Ascending` oder `Descending` auszuwählen.

### Ändern zu einem benutzerdefinierten Kommentartyp {#changing-to-a-custom-comment-type}

Durch Änderung des Kommentarressourcentyps generiert das Kommentarsystem nicht mehr eine Instanz eines Kommentars, der den Standard verwendet, sondern eine, die von Entwicklern angepasst (erweitert) wurde.

Sobald die benutzerdefinierten Ressourcentypen bekannt sind, geben Sie den [Designmodus](/help/sites-authoring/default-components-designmode.md) ein und doppelklicken Sie auf die platzierte `Comments` -Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Geben Sie auf der Registerkarte **Ressourcentypen** den benutzerdefinierten Ressourcentyp für neue Instanzen der `Comments or Voting` -Komponenten an:

![resource-type](assets/resource-type.png)

* **Kommentar-Ressourcentyp**

  Navigieren Sie zum Ressourcentyp einer erweiterten `comment` -Komponente (einzelner Kommentar) in /apps. Zum Beispiel: `/apps/social/commons/components/hbs/comments/comment`

  Diese Ressource identifiziert den resourceType des UGC, der erstellt wurde, wenn ein Besucher einen Kommentar veröffentlicht.

* **Abstimmungs-Ressourcentyp**

  Navigieren Sie zum Ressourcentyp einer erweiterten `voting` -Komponente in /apps. Zum Beispiel: `/apps/social/components/hbs/voting`

  Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wurde, wenn ein Besucher eine Stimme sendet.

* **Kommentar-Systemressourcentyp**

  Navigieren Sie zum Ressourcentyp einer erweiterten `comments`Komponente (Kommentarsystem) in /apps. Lassen Sie das Feld leer, es sei denn, die Seitenvorlage [enthält dynamisch ](/help/communities/scf.md#add-or-include-a-communities-component) das Kommentarsystem im zugrunde liegenden Skript, anstatt zur Seite als Ressource hinzugefügt zu werden (Kommentarknoten). Erfahren Sie mehr über den [`{{include}}` Helper](/help/communities/handlebars-helpers.md#include).

### Site-Besuchererlebnis {#site-visitor-experience}

#### Moderatoren und Administratoren {#moderators-and-administrators}

Wenn der angemeldete Benutzer über Moderator- oder Administratorberechtigungen verfügt, kann er die durch die Konfiguration der Komponente zulässigen Moderationsaufgaben ausführen, unabhängig davon, wer den Kommentar verfasst hat.

#### Mitglieder {#members}

Wenn der Besucher der Site angemeldet ist, kann er je nach Konfiguration

* Post - ein neuer Kommentar
* Bearbeiten eigener Kommentare
* Löschen eigener Kommentare
* Andere Kommentare kennzeichnen

#### Anonym {#anonymous}

Besucher der Website, die nicht angemeldet sind, dürfen veröffentlichte Kommentare nur lesen und übersetzen, sofern sie unterstützt werden. Sie dürfen jedoch keinen Kommentar hinzufügen oder Kommentare anderer Benutzer kennzeichnen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Kommentar-Grundlagen](/help/communities/essentials-comments.md) .

Informationen zur Moderation von veröffentlichten Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zur Übersetzung von veröffentlichten Kommentaren finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
