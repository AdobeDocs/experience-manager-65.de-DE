---
title: Dateibibliothek
seo-title: Dateibibliothek
description: Mit der Funktion "Dateibibliothek"können angemeldete Site-Besucher Dateien hochladen, verwalten und herunterladen
seo-description: Mit der Funktion "Dateibibliothek"können angemeldete Site-Besucher Dateien hochladen, verwalten und herunterladen
uuid: e78a90bd-f1d3-44f8-98eb-1498a55e8217
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ea2b23af-49c3-409b-a041-43c42d846f21
docset: aem65
translation-type: tm+mt
source-git-commit: cdbe098ada0b6c50952284f92cc2063435034a38
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 38%

---


# Dateibibliothek{#file-library-feature}

## Einführung {#introduction}

Mithilfe der Dateibibliothek können angemeldete Besucher der Site (Community-Mitglieder) Dateien auf die Community-Site hochladen, sie dort verwalten oder von dort herunterladen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben::

* Hinzufügen der Dateibibliotheksfunktion zu einer AEM Site.
* Konfigurationseinstellungen für die Komponente `File Library`.

### Hinzufügen einer Dateibibliothek zu einer Seite {#adding-a-file-library-to-a-page}

Um eine `File Library`-Komponente zu einer Seite im Autorenmodus hinzuzufügen, suchen Sie die Komponente:

* `Communities / File Library`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/essentials-file-library.md#essentials-for-client-side) einbezogen werden, wird die `File Library`-Komponente wie folgt angezeigt:

![file-library1](assets/file-library1.png)

### Konfigurieren der Dateibibliothek {#configuring-file-library}

Wählen Sie die platzierte Komponente `File Library` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure-new](assets/configure-new.png)

![file-library2](assets/file-library2.png)

#### Kommentar, Registerkarte {#comments-tab}

Legen Sie auf der Registerkarte **Kommentare** fest, ob und wie Kommentare zu hochgeladenen Dateien angezeigt werden:

* **Kommentare in Dateien zulassen**

   Wenn diese Option aktiviert ist, sollten Sie Kommentare zu hochgeladenen Dateien zulassen. Diese Option ist standardmäßig deaktiviert.

* **Kommentare pro Seite**

   Begrenzt die Anzahl der pro Seite angezeigten Kommentare sowie die Anzahl der angezeigten Antworten. Der Standardwert ist **10**.

* **Max. Dateigröße**

   Dieser Wert begrenzt die Größe der hochgeladenen Datei. Die Standardbeschränkung ist 104857600 (10 MB).

* **Maximale Nachrichtenlänge**

   Maximale Anzahl von Zeichen, die in das Textfeld eingegeben werden können. Der Standardwert ist 4096 Zeichen.

* **Zulässige Dateitypen**

   Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Rich-Text-Editor**

   Wenn diese Option aktiviert ist, können Kommentare mit Markup eingegeben werden. Diese Option ist standardmäßig deaktiviert.

* **Kommentare löschen**

   Wenn diese Option aktiviert ist, können Benutzer ihre eigenen Kommentare löschen. Diese Option ist standardmäßig aktiviert.

* **Tagging zulassen**

   Wenn diese Option aktiviert ist, wird die Möglichkeit aktiviert, der Datei ein Tag hinzuzufügen. Diese Option ist standardmäßig deaktiviert.

* **Zulässige Namespaces**

   Wenn &quot;Tagging zulassen&quot;aktiviert ist, sind die verfügbaren Tags auf die aktivierten Namensraum beschränkt. Wenn keine aktiviert ist, sind alle zulässig. In der Standardeinstellung werden alle Namespaces zugelassen.

* **Empfehlungsgrenze**

   Wenn &quot;Tagging zulassen&quot;aktiviert ist, wird durch diese Einstellung die Anzahl der vorgeschlagenen Tags begrenzt, die angezeigt werden sollen. Wurde der Wert „-1“ festgelegt, werden beliebig viele Tags eingeblendet. Der Standardwert ist -1.

* **Abstimmung zulassen**

   Wenn diese Option aktiviert ist, wird die Möglichkeit zur Auswahl einer Datei aktiviert. Diese Option ist standardmäßig deaktiviert.

* **Folgende zulassen**

   Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder über neue Beiträge benachrichtigt werden können. [](/help/communities/notifications.md) Diese Option ist standardmäßig deaktiviert.

* **Erwähnung aktivieren**

   Wenn diese Option aktiviert ist, können Benutzer der registrierten Community andere registrierte Mitglieder identifizieren (mit Vorname, Nachname, Benutzername) und sie mit einem Tag versehen, das die übliche @user-name-Syntax verwendet. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

   Schränken Sie die maximale Anzahl an Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

   Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@Erwähnung). Beispiel: ~{{familyName}}{{vorname}}.

* **Antworten mit Diskussionsfaden zulassen**

   Wenn diese Option aktiviert ist, können Sie Antworten auf veröffentlichte Kommentare zulassen. Diese Option ist standardmäßig deaktiviert.

#### Benutzermoderation, Registerkarte {#user-moderation-tab}

Legen Sie auf der Registerkarte **Benutzermoderation** fest, wie Kommentare moderiert werden sollen, falls diese zugelassen sind:

* **Vor der Moderation**

   Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungssite angezeigt werden. Diese Option ist standardmäßig deaktiviert.

* **Kommentare löschen**

   Wenn diese Option aktiviert ist, kann der Besucher, der den Kommentar veröffentlicht hat, ihn löschen. Diese Option ist standardmäßig aktiviert.

* **Kommentare ablehnen**

   Wenn diese Option aktiviert ist, können Moderatoren mit vertrauenswürdigen Mitgliedern Kommentare ablehnen. Diese Option ist standardmäßig deaktiviert.

* **Kommentare schließen/erneut öffnen**

   Wenn diese Option aktiviert ist, lassen Sie es Moderatoren vertrauenswürdiger Mitglieder zu, Kommentare zu schließen und erneut zu öffnen. Diese Option ist standardmäßig deaktiviert.

* **Kommentare kennzeichnen**

   Wenn diese Option aktiviert ist, können Besucher Kommentare als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Liste mit Kenn-zeichnungsgründen**

   Wenn diese Option aktiviert ist, können Besucher aus einer Dropdown-Liste auswählen, aus welchem Grund sie einen Kommentar als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

   Wenn diese Option aktiviert ist, können Besucher ihren eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen eingeben. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation**

   Geben Sie an, wie oft ein Kommentar von Besuchern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (**1**).

* **Kennzeichnungslimit**

   Geben Sie an, wie oft ein Kommentar markiert werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **Schwellenwert für Moderation** sein. Der Standardwert ist 5.

### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Sortierfolge

Als Standard festlegen

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Essentials zur Dateibibliothek](/help/communities/essentials-file-library.md) für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
