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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Dateibibliothek{#file-library-feature}

## Einführung {#introduction}

Mithilfe der Dateibibliothek können angemeldete Besucher der Site (Community-Mitglieder) Dateien auf die Community-Site hochladen, sie dort verwalten oder von dort herunterladen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Dateibibliotheksfunktion zu einer AEM-Site
* Konfigurationseinstellungen für die Komponente `File Library`

### Hinzufügen einer Dateibibliothek zu einer Seite {#adding-a-file-library-to-a-page}

To add a `File Library` component to a page in author mode, locate the component

* `Communities / File Library`

und ziehen Sie die Komponente an die gewünschte Stelle auf der Seite.

For necessary information, visit [Communities Components Basics](/help/communities/basics.md).

When the [required client-side libraries](/help/communities/essentials-file-library.md#essentials-for-client-side) are included, this is how the `File Library` component will appear :

![chlimage_1-145](assets/chlimage_1-145.png)

### Konfigurieren der Dateibibliothek {#configuring-file-library}

Select the placed `File Library` component to access and select the `Configure` icon which opens the edit dialog.

![chlimage_1-146](assets/chlimage_1-146.png) ![forum-config-1](assets/forum-config-1.png)

#### Registerkarte &quot;Kommentare&quot; {#comments-tab}

Geben Sie unter der Registerkarte **Kommentare **an, ob und wie Kommentare für hochgeladene Dateien angezeigt werden:

* **Kommentare in Dateien zulassen** Ist diese Option aktiviert, werden Kommentare zu hochgeladenen Dateien zugelassen. Diese Option ist standardmäßig deaktiviert.

* **Kommentare pro Seite** Mit dieser Option wird die Anzahl der Kommentare und Antworten beschränkt, die pro Seite angezeigt werden. Der Standardwert ist **10**.

* **Max. Dateigröße** Dieser Wert beschränkt die Größe der hochgeladenen Datei. Die Standardbeschränkung ist 104857600 (10 MB).

* **Maximale Nachrichtenlänge** Die Anzahl der Zeichen, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **Zulässige Dateitypen** Eine kommagetrennte Liste der zulässigen Dateierweiterungen inklusive Punkt. Beispiel: .jpg, .jpeg., png, .doc, .docx, .pdf. Wurden Dateitypen festgelegt, können Dateien nicht angegebenen Typs nicht hochgeladen werden. Der Standardwert ist nicht angegeben, sodass** **alle Dateitypen zulässig sind.

* **Rich-Text-Editor** Ist diese Option aktiviert, können Kommentare mit Markup versehen werden. Diese Option ist standardmäßig deaktiviert.

* **Kommentare** löschen Wenn diese aktiviert sind, können Benutzer ihre eigenen Kommentare löschen. Diese Option ist standardmäßig aktiviert.

* **Tagging zulassen** Ist diese Option aktiviert, können Dateien Kennzeichnungen zugewiesen werden. Diese Option ist standardmäßig deaktiviert.

* **Zulässige Namespaces** Wenn Tagging zulassen aktiviert ist, sind die verfügbaren Tags auf die aktivierten Namespaces beschränkt. Wenn keine aktiviert ist, sind alle zulässig. In der Standardeinstellung werden alle Namespaces zugelassen.

* **Empfehlungsgrenze** Ist die Option „Tagging zulassen“ aktiviert, wird mit dieser Einstellung die Anzahl der vorgeschlagenen Tags eingegrenzt. Wurde der Wert „-1“ festgelegt, werden beliebig viele Tags eingeblendet. Der Standardwert ist -1.

* **Abstimmung** zulassen Wenn diese Option aktiviert ist, wird die Möglichkeit zur Auswahl einer Datei aktiviert. Diese Option ist standardmäßig deaktiviert.

* **Zulassen** Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) werden können. Diese Option ist standardmäßig deaktiviert.

* **Erwähnung** aktivieren Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder identifizieren (unter Verwendung von Vorname, Nachname, Benutzername) und sie mit der gemeinsamen @user-name-Syntax markieren. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**: Die maximale Anzahl an Erwähnungen, die in einem Beitrag zulässig sind, beschränken. Der Standardwert ist 10.

* **Benutzeroberflächenbeschreibungsmuster** Geben Sie die zulässige Musterzeichenfolge an, um den registrierten Benutzer in einem Beitrag zu taggen (@Erwähnung). Beispiel: ~{{familyName}}{{vorname}}.

* **Threaded Replies** zulassen Wenn diese aktiviert sind, erlauben Sie Antworten auf gepostete Kommentare. Diese Option ist standardmäßig deaktiviert.

#### Registerkarte Benutzermoderation {#user-moderation-tab}

Legen Sie auf der Registerkarte **Benutzermoderation** fest, wie Kommentare moderiert werden sollen, falls diese zugelassen sind:

* **Vor der Moderation** Ist diese Option aktiviert, müssen Kommentare vor ihrer Veröffentlichung zunächst genehmigt werden. Diese Option ist standardmäßig deaktiviert.

* **Kommentare löschen** Ist diese Option aktiviert, kann der Besucher, der den Kommentar veröffentlicht hat, diesen auch wieder löschen. Diese Option ist standardmäßig aktiviert.

* **Kommentare ablehnen** Ist diese Option aktiviert, können ausgewählte Mitglieder Kommentare ablehnen. Diese Option ist standardmäßig deaktiviert.

* **Kommentare schließen/erneut öffnen** Ist diese Option aktiviert, können ausgewählte Mitglieder Kommentare schließen oder erneut öffnen. Diese Option ist standardmäßig deaktiviert.

* **Kommentare kennzeichnen** Ist diese Option aktiviert, können Besucher Kommentare als unangemessen kennzeichnen. Diese Option ist standardmäßig deaktiviert.

* **Liste mit Kennzeichnungsgründen** Ist diese Option aktiviert, können Besucher aus einer Dropdown-Liste den Grund auswählen, aus dem ein Kommentar als unangemessen gekennzeichnet wird. Diese Option ist standardmäßig deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung** Ist diese Option aktiviert, können Besucher einen eigenen Grund dafür eingeben, warum sie Kommentare als unangemessen kennzeichnen möchten. Diese Option ist standardmäßig deaktiviert.

* **Schwellenwert für Moderation** Geben Sie an, wie oft ein Kommentar von Besuchern als unangemessen gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (**1**).

* **Kennzeichnungslimit** Geben Sie an, wie oft ein Kommentar als unangemessen gekennzeichnet werden muss, bevor er aus dem öffentlichen Bereich ausgeblendet wird. Dieser Wert muss größer als der oder gleich dem **Schwellenwert für Moderation** sein. Der Standardwert ist 5.

### Sortiereinstellungen, Registerkarte {#sort-settings-tab}

Sortierfolge

Als Standard festlegen

### Zusätzliche Informationen {#additional-information}

More information may be found on the [File Library Essentials](/help/communities/essentials-file-library.md) page for developers.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderation benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
