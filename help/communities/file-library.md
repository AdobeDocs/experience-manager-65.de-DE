---
title: Dateibibliotheksfunktion
description: Mit der Funktion „Dateibibliothek“ können angemeldete Site-Besucher Dateien hochladen, verwalten und herunterladen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 05cfaab5-a12d-475f-9095-a9fb13571d0a
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 2%

---

# Dateibibliotheksfunktion{#file-library-feature}

## Einführung {#introduction}

Die Dateibibliotheksfunktion bietet einen Ort für angemeldete Site-Besucher (Community-Mitglieder), an dem Sie Dateien innerhalb der Community-Site hochladen, verwalten und herunterladen können.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Dateibibliotheksfunktion zu einer AEM-Site.
* Konfigurationseinstellungen für die `File Library`.

### Hinzufügen einer Dateibibliothek zu einer Seite {#adding-a-file-library-to-a-page}

Suchen Sie die Komponente , um einer Seite im Autorenmodus eine `File Library` Komponente hinzuzufügen:

* `Communities / File Library`

Und ziehen Sie es auf eine Seite.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen ](/help/communities/essentials-file-library.md#essentials-for-client-side) enthalten sind, wird die `File Library` Komponente wie folgt angezeigt:

![file-library1](assets/file-library1.png)

### Konfigurieren der Dateibibliothek {#configuring-file-library}

Wählen Sie die platzierte `File Library` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![configure-new](assets/configure-new.png)

![file-library2](assets/file-library2.png)

#### Registerkarte „Kommentare“ {#comments-tab}

Geben Sie auf **Registerkarte** Kommentare“ an, ob und wie Kommentare für hochgeladene Dateien angezeigt werden sollen:

* **Kommentare zu Dateien zulassen**

  Wenn diese Option aktiviert ist, können Sie Kommentare zu hochgeladenen Dateien zulassen. Standard ist deaktiviert.

* **Kommentare pro Seite**

  Beschränkt die Anzahl der angezeigten Kommentare pro Seite und die Anzahl der angezeigten Antworten. Der Standardwert lautet **10**.

* **max. Dateigröße**

  Dieser Wert begrenzt die Größe der hochgeladenen Datei. Das Standardlimit ist 104857600 (10 MB).

* **Max. Nachrichtenlänge**

  Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert ist 4096 Zeichen.

* **Zulässige Dateitypen**

  Eine kommagetrennte Liste von Dateierweiterungen mit dem Punkttrennzeichen. Zum Beispiel .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben werden, sind alle Dateitypen, die nicht angegeben sind, nicht zulässig. Die Standardeinstellung ist nicht so festgelegt, dass alle Dateitypen zulässig sind.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Kommentare mit Markup eingegeben werden. Standard ist deaktiviert.

* **Kommentare löschen**

  Wenn diese Option aktiviert ist, können Benutzer ihre eigenen Kommentare löschen. Die Standardeinstellung ist aktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, kann der Datei ein Tag hinzugefügt werden. Standard ist deaktiviert.

* **Zugelassene Namespaces**

  Wenn Tagging zulassen aktiviert ist, sind die verfügbaren Tags auf die ausgewählten Namespaces beschränkt. Wenn keine Namespaces aktiviert sind, sind alle zulässig. Die Standardeinstellung ist „Alle Namespaces“.

* **Vorschlagslimit**

  Wenn Tagging zulassen aktiviert ist, beschränkt diese Einstellung die Anzahl der vorgeschlagenen Tags, die angezeigt werden sollen. Bei -1 gibt es keine Beschränkung. Der Standardwert ist -1.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, kann für eine Datei gestimmt werden. Standard ist deaktiviert.

* **Folgendes zulassen**

  Wenn diese Option aktiviert ist, können Sie die folgende Funktion für Blog-Artikel einschließen, mit der Mitglieder über neue Beiträge [benachrichtigt](/help/communities/notifications.md) können. Standard ist deaktiviert.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (mit Vorname, Nachname, Benutzername) identifizieren und sie mit der allgemeinen @user-name-Syntax taggen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max Erwähnungen**

  Beschränken Sie die maximal zulässige Anzahl von Erwähnungen in einem Beitrag. Der Standardwert ist 10.

* **UI-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, damit Sie den registrierten Benutzer in einem Beitrag taggen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

* **Thread-Antworten zulassen**

  Wenn diese Option aktiviert ist, können Antworten auf gepostete Kommentare zugelassen werden. Standard ist deaktiviert.

#### Registerkarte „Benutzermoderation“ {#user-moderation-tab}

Konfigurieren **auf der Registerkarte** Benutzermoderation“ die Moderation von Kommentaren, wenn Kommentare zulässig sind:

* **Vormoderation**

  Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Standard ist deaktiviert.

* **Kommentare löschen**

  Wenn diese Option aktiviert ist, kann der Besucher, der den Kommentar gepostet hat, ihn bei Bedarf löschen. Die Standardeinstellung ist aktiviert.

* **Kommentare ablehnen**

  Wenn diese Option aktiviert ist, können vertrauenswürdige Mitglied-Moderatoren Kommentare ablehnen. Standard ist deaktiviert.

* **Kommentare schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können vertrauenswürdige Mitglied-Moderatoren Kommentare schließen und erneut öffnen. Standard ist deaktiviert.

* **Kennzeichnen von Kommentaren**

  Wenn diese Option aktiviert ist, können Besucher Kommentare als unangemessen kennzeichnen. Standard ist deaktiviert.

* **Verursacherliste kennzeichnen**

  Wenn diese Option aktiviert ist, können Besucher aus einer Dropdown-Liste den Grund auswählen, aus dem sie einen Kommentar als unangemessen kennzeichnen. Standard ist deaktiviert.

* **Grund für benutzerdefinierte Markierung**

  Wenn diese Option aktiviert ist, können Besucher ihren eigenen Grund eingeben, warum sie einen Kommentar als unangemessen kennzeichnen. Standard ist deaktiviert.

* **Moderationsschwellenwert**

  Geben Sie ein, wie oft ein Kommentar von Besuchern markiert werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist „one time“ (**1**).

* **Kennzeichnungsgrenze**

  Geben Sie ein, wie oft ein Kommentar gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Diese Zahl muss größer oder gleich dem **Moderationsschwellenwert“**. Der Standardwert ist 5.

### Registerkarte „Sortiereinstellungen“ {#sort-settings-tab}

Sortieren nach

Als Standard festlegen

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [File Library Essentials](/help/communities/essentials-file-library.md) für Entwickler.

Informationen zur Moderation geposteter Themen und Kommentare finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging geposteter Themen und Kommentare finden Sie [Tagging von benutzergenerierten Inhalten](/help/communities/tag-ugc.md).
