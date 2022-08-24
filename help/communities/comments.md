---
title: Verwenden von Kommentaren
seo-title: Using Comments
description: Mit der Kommentarfunktion können angemeldete Site-Besucher ihre Meinungen und ihr Wissen austauschen
seo-description: Comments feature lets signed-in site visitors share their opinions and knowledge
uuid: 40acd962-846c-483c-b789-aab3a7d2b31b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 216cfb3e-777e-4773-afba-749debdca000
docset: aem65
exl-id: 30baebd9-13c5-4fde-a494-85601abc32a5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 31%

---

# Verwenden von Kommentaren {#using-comments}

## Einführung    {#introduction}

Die Kommentarfunktion ermöglicht es angemeldeten Site-Besuchern (Mitgliedern), ihre Meinung und ihre Kenntnisse bezüglich der Site-Inhalte kundzutun. Diese Funktion ist in der Regel bereits in anderen Funktionen enthalten, kann jedoch auch beliebigen Websites hinzugefügt werden.

Das Dokument beschreibt:

* Hinzufügen `Comments` auf eine Seite.
* Konfigurationseinstellungen für `Comments` -Komponente.

>[!NOTE]
>
>Das anonyme Posten von Kommentaren wird nicht unterstützt. Besucher der Website müssen sich registrieren (Mitglieder werden) und anmelden, um Kommentare verfassen zu können.

### Hinzufügen von Kommentaren zu einer Seite {#adding-comments-to-a-page}

So fügen Sie eine `Comments` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Comments`

und ziehen Sie sie an die gewünschte Stelle auf einer Seite, z. B. in die Nähe einer Eigenschaft, die Benutzer kommentieren sollen, oder fügen Sie die Komponente am Ende der Seite ein.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](/help/communities/essentials-comments.md#essentials-for-client-side) eingeschlossen sind, wird die `Comments` -Komponente angezeigt.

![comments-component](assets/comments-component.png)

>[!NOTE]
>
>Nur eine `Comments` -Komponente auf einer Seite vorhanden sein. Beachten Sie, dass mehrere Communities-Funktionen bereits Kommentare enthalten, wie z. B. Blog, Kalender, Forum, Fragen und Antworten.

### Konfigurieren von Kommentaren {#configuring-comments}

Wählen Sie die platzierte `Comments` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![Symbol zum Konfigurieren](assets/configure.png)

![Kommentareinstellungen](assets/commentssettings.png)

#### Registerkarte &quot;Kommentare&quot; {#comments-tab}

Legen Sie auf der Registerkarte **Kommentare** fest, wie Benutzer Kommentare eingeben sollen.

* **Antworten zulassen**

   Ist diese Option aktiviert, können Mitglieder auf vorhandene Kommentare antworten. Die Option Standard ist deaktiviert.

* **Kommentare pro Seite**

   Beschränkt die Anzahl der pro Seite angezeigten Kommentare und die angezeigte Anzahl der Antworten. Der Standardwert ist 10.

* **Datei-Uploads zulassen**

   Wenn diese Option aktiviert ist, wird die Option zum Hochladen einer Datei mit dem Texteingabefeld angezeigt. Die Option Standard ist deaktiviert.

* **Max. Dateigröße**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Dieser Wert begrenzt die Größe der hochgeladenen Datei. Der Standardwert ist 10 MB.

* **Maximale Nachrichtenlänge**

   Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **Zulässige Dateitypen**

   Nur relevant, wenn die Option Datei-Uploads zulassen aktiviert ist. Eine kommagetrennte Liste von Dateinamenerweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, sind die nicht angegebenen nicht zulässig. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, werden Kommentare mit Markup eingegeben. Die Option Standard ist deaktiviert.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, wird das Texteingabefeld angezeigt. Die Option Standard ist deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Kommentare folgen. Die Option Standard ist deaktiviert.

* **Abzeichen anzeigen**

   Wenn diese Option aktiviert ist, können Sie die Anzeige von verdienten und vergebenen Abzeichen zulassen. Die Option Standard ist deaktiviert.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **Benutzermoderation** Registerkarte angeben, wie die veröffentlichten Kommentare verwaltet werden. Weitere Informationen finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

* **Vor der Moderation**

   Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Die Option Standard ist deaktiviert.

* **Kommentare löschen**

   Wenn diese Option aktiviert ist, kann das Mitglied, das den Kommentar veröffentlicht hat, ihn löschen. Die Option Standard ist deaktiviert.

* **Kommentare ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare ablehnen. Die Option Standard ist deaktiviert.

* **Kommentare schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, können Moderatoren Kommentare schließen und erneut öffnen. Die Option Standard ist deaktiviert.

* **Kommentare kennzeichnen**

   Ist diese Option aktiviert, können Mitglieder Kommentare als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Mitglieder aus einer Dropdown-Liste den Grund auswählen, aus dem ein Kommentar als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Mitglieder einen eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Kommentar von den Mitgliedern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (1).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Kommentar gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **Schwellenwert für Moderation** sein. Der Standardwert ist 5.

#### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Unter dem **Sortiereinstellungen** festlegen, wie die veröffentlichten Kommentare sortiert werden, wenn sie angezeigt werden.

* **Sortierfeld**

   Ziehen Sie nach unten, um eines von `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`oder `Most Liked`.

* **Sortierreihenfolge**

   Ziehen Sie nach unten, um eines von `Ascending` oder `Descending`.

### Ändern in einen benutzerdefinierten Kommentartyp {#changing-to-a-custom-comment-type}

Durch Änderung des Kommentarressourcentyps generiert das Kommentarsystem nicht mehr eine Instanz eines Kommentars, der den Standard verwendet, sondern eine, die von Entwicklern angepasst (erweitert) wurde.

Sobald die benutzerdefinierten Ressourcentypen bekannt sind, geben Sie [Designmodus](/help/sites-authoring/default-components-designmode.md) und doppelklicken Sie auf die platzierte `Comments` -Komponente, um ein Dialogfeld mit einer zusätzlichen Registerkarte zu öffnen.

Unter dem **Ressourcentypen** Registerkarte den benutzerdefinierten resourceType für neue Instanzen der `Comments or Voting` Komponenten:

![resource-type](assets/resource-type.png)

* **Kommentarressourcentyp**

   Navigieren Sie zum resourceType eines erweiterten `comment` Komponente (einzelner Kommentar) in /apps. Beispiel: `/apps/social/commons/components/hbs/comments/comment`

   Diese Ressource identifiziert den resourceType des UGC, der erstellt wurde, wenn ein Besucher einen Kommentar veröffentlicht.

* **Abstimmungs-Ressourcentyp**

   Navigieren Sie zum resourceType eines erweiterten `voting` -Komponente in /apps. Beispiel: `/apps/social/components/hbs/voting`

   Diese Ressource identifiziert den Ressourcentyp des UGC, der erstellt wurde, wenn ein Besucher eine Stimme sendet.

* **Ressourcentyp des Kommentars**

   Navigieren Sie zum resourceType eines erweiterten `comments`-Komponente (Kommentarsystem) in /apps. Leer lassen, es sei denn, die Seitenvorlage [dynamisch enthält](/help/communities/scf.md#add-or-include-a-communities-component) das Kommentar-System im zugrunde liegenden Skript, anstatt als Ressource (Kommentarknoten) zur Seite hinzugefügt zu werden. Weitere Informationen finden Sie unter [{{include}} Helper](/help/communities/handlebars-helpers.md#include).

### Site-Besuchererlebnis {#site-visitor-experience}

#### Moderatoren und Administratoren {#moderators-and-administrators}

Verfügt der angemeldete Benutzer über Moderator- oder Administratorrechte, kann er Moderationsaufgaben ausführen, die ihm durch die Komponentenkonfiguration gestattet werden, unabhängig davon, wer den Kommentar verfasst hat.

#### Mitglieder {#members}

Abhängig von der Konfiguration können angemeldete Besucher Folgendes tun:

* Posten eines neuen Kommentars
* Bearbeiten eigener Kommentare
* Löschen eigener Kommentare
* Andere Kommentare kennzeichnen

#### Anonym {#anonymous}

Nicht registrierte oder angemeldete Besucher können veröffentlichte Kommentare lediglich lesen und übersetzen (falls unterstützt), jedoch keine eigenen Kommentare hinzufügen und keine Kommentare anderer Benutzer kennzeichnen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zu Kommentaren](/help/communities/essentials-comments.md) für Entwickler.

Informationen zur Moderation von geposteten Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zur Übersetzung von Kommentaren finden Sie unter [Übersetzung benutzergenerierter Inhalte](/help/communities/translate-ugc.md).
