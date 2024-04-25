---
title: Dateibibliothek-Funktion
description: Mit der Funktion "Dateibibliothek"können angemeldete Site-Besucher Dateien hochladen, verwalten und herunterladen.
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

# Dateibibliothek-Funktion{#file-library-feature}

## Einführung {#introduction}

Die Dateibibliotheksfunktion bietet angemeldeten Site-Besuchern (Community-Mitgliedern) die Möglichkeit, Dateien innerhalb der Community-Site hochzuladen, zu verwalten und herunterzuladen.

In diesem Abschnitt der Dokumentation wird Folgendes beschrieben:

* Hinzufügen der Dateibibliotheksfunktion zu einer AEM Site.
* Konfigurationseinstellungen für `File Library` -Komponente.

### Hinzufügen einer Dateibibliothek zu einer Seite {#adding-a-file-library-to-a-page}

So fügen Sie eine `File Library` -Komponente auf einer Seite im Autorenmodus zu finden, die Komponente:

* `Communities / File Library`

Und ziehen Sie es an die gewünschte Stelle auf einer Seite.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](/help/communities/essentials-file-library.md#essentials-for-client-side) eingeschlossen sind, wird die `File Library` -Komponente angezeigt:

![file-library1](assets/file-library1.png)

### Konfigurieren der Dateibibliothek {#configuring-file-library}

Auswählen der platzierten `File Library` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![configure-new](assets/configure-new.png)

![file-library2](assets/file-library2.png)

#### Registerkarte &quot;Kommentare&quot; {#comments-tab}

Unter dem **Kommentare** -Registerkarte angeben, ob und wie Kommentare für hochgeladene Dateien angezeigt werden:

* **Kommentare zu Dateien zulassen**

  Wenn diese Option aktiviert ist, lassen Sie Kommentare zu hochgeladenen Dateien zu. Die Option Standard ist deaktiviert.

* **Kommentare pro Seite**

  Beschränkt die Anzahl der pro Seite angezeigten Kommentare und die angezeigte Anzahl der Antworten. Der Standardwert ist **10**.

* **Maximale Dateigröße**

  Dieser Wert begrenzt die Größe der hochgeladenen Datei. Der Standardwert ist 104857600 (10 MB).

* **Max. Nachrichtenlänge**

  Maximale Zeichenanzahl, die in das Textfeld eingegeben werden kann. Der Standardwert beträgt 4096 Zeichen.

* **Zulässige Dateitypen**

  Eine kommagetrennte Liste von Dateierweiterungen mit dem Trennzeichen &quot;Punkt&quot;. Beispiel: .jpg, .jpeg, .png, .doc, .docx, .pdf. Wenn Dateitypen angegeben sind, sind keine nicht angegebenen Dateitypen zulässig. Der Standardwert ist nicht so angegeben, dass alle Dateitypen zulässig sind.

* **Rich-Text-Editor**

  Wenn diese Option aktiviert ist, können Kommentare mit Markup eingegeben werden. Die Option Standard ist deaktiviert.

* **Kommentare löschen**

  Wenn diese Option aktiviert ist, können Benutzer ihre eigenen Kommentare löschen. Die Option Standard ist aktiviert.

* **Tagging zulassen**

  Wenn diese Option aktiviert ist, kann der Datei ein Tag hinzugefügt werden. Die Option Standard ist deaktiviert.

* **Zugelassene Namespaces**

  Wenn die Option Tagging zulassen aktiviert ist, sind die verfügbaren Tags auf die aktivierten Namespaces beschränkt. Wenn keine Namespaces aktiviert sind, sind alle zulässig. Der Standardwert ist alle Namespaces.

* **Empfehlungslimit**

  Wenn die Option Tagging zulassen aktiviert ist, beschränkt diese Einstellung die Anzahl der vorgeschlagenen Tags, die angezeigt werden sollen. Wenn auf -1 gesetzt, gibt es keine Begrenzung. Der Standardwert ist -1.

* **Abstimmung zulassen**

  Wenn diese Option aktiviert ist, ist die Möglichkeit, für eine Datei zu stimmen, aktiviert. Die Option Standard ist deaktiviert.

* **Folgende erlauben**

  Wenn diese Option aktiviert ist, fügen Sie die folgende Funktion für Blog-Artikel hinzu, mit der Mitglieder [benachrichtigt](/help/communities/notifications.md) von neuen Stellen. Die Option Standard ist deaktiviert.

* **Erwähnung aktivieren**

  Wenn diese Option aktiviert ist, können registrierte Community-Benutzer andere registrierte Mitglieder (unter Verwendung von Vorname, Nachname, Benutzername) identifizieren und sie mit der gemeinsamen Syntax @user-name versehen. Die getaggten Benutzer erhalten Benachrichtigungen über ihre Erwähnungen.

* **Max. Erwähnungen**

  Schränken Sie die maximale Anzahl der Erwähnungen ein, die in einem Beitrag zulässig sind. Der Standardwert ist 10.

* **Benutzeroberflächen-Erwähnungsmuster**

  Geben Sie die zulässige Musterzeichenfolge an, damit Sie den registrierten Benutzer in einem Beitrag mit Tags versehen (@mention). Zum Beispiel: `~{{familyName}}{{givenName}}`.

* **Threaded-Antworten zulassen**

  Ist diese Option aktiviert, können Antworten auf gepostete Kommentare zugelassen werden. Die Option Standard ist deaktiviert.

#### Registerkarte &quot;Benutzermoderation&quot; {#user-moderation-tab}

Unter dem **Benutzermoderation** -Tab konfigurieren Sie die Moderation von Kommentaren, falls Kommentare zulässig sind:

* **Vormoderation**

  Wenn diese Option aktiviert ist, müssen Kommentare genehmigt werden, bevor sie auf einer Veröffentlichungs-Site angezeigt werden. Die Option Standard ist deaktiviert.

* **Kommentare löschen**

  Wenn diese Option aktiviert ist, kann der Besucher, der den Kommentar veröffentlicht hat, ihn bei Bedarf löschen. Die Option Standard ist aktiviert.

* **Kommentare ablehnen**

  Ist diese Option aktiviert, können Moderatoren vertrauenswürdiger Mitglieder Kommentare ablehnen. Die Option Standard ist deaktiviert.

* **Kommentare schließen/erneut öffnen**

  Wenn diese Option aktiviert ist, können Moderatoren vertrauenswürdiger Mitglieder Kommentare schließen und erneut öffnen. Die Option Standard ist deaktiviert.

* **Kommentare kennzeichnen**

  Ist diese Option aktiviert, können Besucher Kommentare als unangemessen kennzeichnen. Die Option Standard ist deaktiviert.

* **Liste der Kennzeichnungsgründe**

  Wenn diese Option aktiviert ist, können Besucher aus einer Dropdown-Liste den Grund auswählen, aus dem ein Kommentar als unangemessen gekennzeichnet wird. Die Option Standard ist deaktiviert.

* **Grund für benutzerdefinierte Kennzeichnung**

  Wenn diese Option aktiviert ist, können Besucher einen eigenen Grund für die Kennzeichnung eines Kommentars als unangemessen eingeben. Die Option Standard ist deaktiviert.

* **Schwellenwert für Moderation**

  Geben Sie an, wie oft ein Kommentar von Besuchern gekennzeichnet werden muss, bevor Moderatoren benachrichtigt werden. Der Standardwert ist einmal (**1**).

* **Kennzeichnungslimit**

  Geben Sie an, wie oft ein Kommentar gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Diese Zahl muss größer oder gleich der Zahl **Schwellenwert für Moderation**. Der Standardwert ist 5.

### Registerkarte &quot;Sortiereinstellungen&quot; {#sort-settings-tab}

Sortieren nach

Als Standard festlegen

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zur Dateibibliothek](/help/communities/essentials-file-library.md) -Seite für Entwickler.

Informationen zur Moderation von veröffentlichten Themen und Kommentaren finden Sie unter [Moderieren benutzergenerierter Inhalte](/help/communities/moderate-ugc.md).

Informationen zum Tagging von veröffentlichten Themen und Kommentaren finden Sie unter [Tagging benutzergenerierter Inhalte](/help/communities/tag-ugc.md).
