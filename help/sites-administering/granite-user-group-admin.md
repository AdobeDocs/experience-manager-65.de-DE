---
title: Granite-Vorgänge – Benutzer- und Gruppenverwaltung
seo-title: Granite Operations - User and Group Administration
description: Erfahren Sie mehr über die Benutzer- und Gruppenverwaltung von Granite.
seo-description: Learn about Granite user and group administration.
uuid: 7b6b7767-712c-4cc8-8d90-36f26280d6e3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 95ab2e54-0f8d-49e0-ad20-774875f6f80a
exl-id: f3477d21-7e9a-4588-94e8-496bc42434a8
feature: Security
source-git-commit: 7803f1df1e05dc838cb458026f8dbd27de9cb924
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 69%

---

# Granite-Vorgänge – Benutzer- und Gruppenverwaltung{#granite-operations-user-and-group-administration}

Da Granite die CRX-Repository-Implementierung der JCR-API-Spezifikation enthält, verfügt es über eine eigene Benutzer- und Gruppenverwaltung.

Diese Konten bilden die Grundlage der [AEM-Konten](/help/sites-administering/security.md). Sämtliche in der Granite-Verwaltung durchgeführten Kontoänderungen werden widergespiegelt, falls/wenn auf die Konten über die [AEM-Benutzerkonsole](/help/sites-administering/security.md#accessing-user-administration-with-the-security-console) (z.B. `http://localhost:4502/useradmin`) zugegriffen wird. In der Konsole AEM Benutzer können Sie auch die Berechtigungen und andere AEM verwalten.

Granite-Benutzer- und Gruppenverwaltungskonsolen sind beide über das **[Instrumente](/help/sites-administering/tools-consoles.md)** Konsole der Touch-optimierten Benutzeroberfläche:

![chlimage_1-72](assets/chlimage_1-72a.png)

Entweder **Benutzer** oder **Gruppen** über die Tools-Konsole die entsprechende Konsole öffnen. In beiden können Sie entweder über das Kontrollkästchen und dann über Aktionen in der Symbolleiste oder durch Öffnen der Kontodetails über den Link unter **Name**.

* [Benutzerverwaltung](#user-administration)

  ![chlimage_1-73](assets/chlimage_1-73a.png)

  Die **Benutzer** Konsolenlisten:

   * Benutzername
   * den Anmeldenamen (Kontonamen) des Benutzers;
   * Titel, die dem Konto zugewiesen wurden.

* [Gruppenverwaltung](#group-administration)

  ![chlimage_1-74](assets/chlimage_1-74a.png)

  Die **Gruppen** Konsolenlisten:

   * den Gruppennamen
   * die Gruppenbeschreibung
   * die Anzahl der Benutzer/Gruppen in der Gruppe

## Benutzerverwaltung {#user-administration}

### Hinzufügen neuer Benutzer {#adding-a-new-user}

1. Verwenden Sie die **Benutzer hinzufügen** Symbol:

   ![Benutzer hinzufügen](do-not-localize/chlimage_1-1.png)

1. Die **Benutzer erstellen** Das Formular wird geöffnet:

   ![chlimage_1-75](assets/chlimage_1-75a.png)

   Hier können Sie die Benutzerdetails für das Konto eingeben (die meisten entsprechen dem Standard und sind selbsterklärend):

   * **ID**

     Dies ist die eindeutige Kennung des Benutzerkontos. Diese Angabe ist obligatorisch und darf keine Leerzeichen enthalten.

   * **E-Mail-Adresse**
   * **Kennwort**

     Ein Kennwort muss angegeben werden.

   * **Kennwortwdh.**

     Diese zur Bestätigung des Kennworts erforderliche Angabe ist obligatorisch.

   * **Vorname**
   * **Nachname**
   * **Telefonnummer**
   * **Titel des Auftrags**
   * **Straße**
   * **Mobilgerät**
   * **Stadt**
   * **PLZ**
   * **Land**
   * **Status**
   * **Titel**
   * **Geschlecht**
   * **Info**
   * **Kontoeinstellungen**

      * **Status**
Sie können das Konto als **aktiv** oder **inaktiv** markieren.

   * **Foto**

     Hier können Sie ein Foto für einen Avatar hochladen.

     Akzeptierte Dateitypen: `.jpg .png .tif .gif`

     Bevorzugte Größe: `240x240px`

   * **Benutzer zu Gruppen hinzufügen**

     Wählen Sie über die Auswahl-Dropdown-Liste die Gruppen aus, denen der Benutzer als Mitglied angehören soll. Vor dem Speichern können Sie ggf. eine getroffene Auswahl mit dem **X** neben dem Namen aufheben.

   * **Gruppen**

     Eine Liste der Gruppen, in denen der Benutzer derzeit Mitglied ist. Verwenden Sie die **X** durch den Namen, der vor dem Speichern deaktiviert werden soll.

1. Wenn Sie das Benutzerkonto definiert haben, verwenden Sie:

   * **Abbrechen** , um die Registrierung abzubrechen.
   * **Speichern** , um die Registrierung abzuschließen. Die Erstellung des Benutzerkontos wird mit einer Meldung bestätigt.

### Bearbeiten vorhandener Benutzer {#editing-an-existing-user}

1. Rufen Sie die Benutzerdetails über den Link unterhalb des Benutzernamens in der Benutzer-Konsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Benutzer](#adding-a-new-user) bearbeiten.

1. Rufen Sie die Benutzerdetails über den Link unterhalb des Benutzernamens in der Benutzer-Konsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Benutzer](#adding-a-new-user) bearbeiten.

### Ändern von Kennwörtern vorhandener Benutzer {#changing-the-password-for-an-existing-user}

1. Rufen Sie die Benutzerdetails über den Link unterhalb des Benutzernamens in der Benutzer-Konsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Benutzer](#adding-a-new-user) bearbeiten. Unter **Kontoeinstellungen** ist ein Link **Kennwort ändern** vorhanden.

   ![chlimage_1-76](assets/chlimage_1-76a.png)

1. Das Dialogfeld **Kennwort ändern** wird geöffnet. Geben Sie das neue Kennwort zusammen mit Ihrem Kennwort ein und geben Sie es erneut ein. Bestätigen Sie die Änderungen mit **OK**.

   ![chlimage_1-77](assets/chlimage_1-77a.png)

   Über eine Meldung wird bestätigt, dass das Kennwort geändert wurde.

### Schnellgruppenzuweisung {#quick-group-assignment}

1. Verwenden Sie das Kontrollkästchen, um einen oder mehrere Benutzer zu kennzeichnen.
1. Verwenden Sie das Symbol **Gruppen**:

   ![Verwenden des Symbols Gruppen](do-not-localize/chlimage_1-2.png)

   Hierdurch wird die Dropdown-Liste für die Gruppenauswahl geöffnet:

   ![chlimage_1-78](assets/chlimage_1-78a.png)

1. Im Auswahlfeld können Sie per Aus-/Abwahl festlegen, welchen Gruppen das Benutzerkonto angehören soll.

1. Wählen Sie eine der folgenden Optionen aus, nachdem Sie die Gruppen zugewiesen oder deren Zuweisung aufgehoben haben:

   * **Abbrechen** zum Verwerfen der Änderungen
   * **Speichern** zum Bestätigen der Änderungen

### Löschen vorhandener Benutzerdetails {#deleting-existing-user-details}

1. Verwenden Sie das Kontrollkästchen, um einen oder mehrere Benutzer zu kennzeichnen.
1. Löschen Sie Benutzerdetails mit dem Symbol **Löschen**:

   ![Löschen vorhandener Benutzerdetails](do-not-localize/chlimage_1-3.png)

1. Sie werden zum Bestätigen des Löschvorgangs aufgefordert. Daraufhin wird durch eine Meldung bestätigt, dass der Löschvorgang tatsächlich durchgeführt wurde.

## Gruppenverwaltung {#group-administration}

### Hinzufügen einer neuen Gruppe {#adding-a-new-group}

1. Verwenden Sie das Symbol Gruppe hinzufügen :

   ![Neue Gruppe hinzufügen](do-not-localize/chlimage_1-4.png)

1. Die **Gruppe erstellen** Das Formular wird geöffnet:

   ![chlimage_1-79](assets/chlimage_1-79a.png)

   Hier können Sie die Gruppendetails eingeben:

   * **ID**

     Dies ist die eindeutige Kennung der Gruppe. Diese Angabe ist obligatorisch und darf keine Leerzeichen enthalten.

   * **Name**

     Der Name für die Gruppe; dieser wird in der Gruppenkonsole angezeigt.

   * **Beschreibung**

     Eine Beschreibung der Gruppe.

   * **Mitglieder zu Gruppe hinzufügen**

     Wählen Sie über die Auswahl-Dropdown-Liste die Benutzer aus, die der Gruppe hinzugefügt werden sollen. Vor dem Speichern können Sie ggf. eine getroffene Auswahl mit dem **X** neben dem Namen aufheben.

   * **Gruppenmitglieder**

     Eine Liste der Benutzer in der Gruppe. Verwenden Sie die **X** durch den Namen, der vor dem Speichern deaktiviert werden soll.

1. Wenn Sie die Gruppe definiert haben, verwenden Sie:

   * **Abbrechen** , um die Registrierung abzubrechen.
   * **Speichern** , um die Registrierung abzuschließen. Die Erstellung der Gruppe wird mit einer Meldung bestätigt.

### Bearbeiten vorhandener Gruppen {#editing-an-existing-group}

1. Rufen Sie die Gruppendetails über den Link unterhalb des Gruppennamens in der Gruppenkonsole auf.

1. Sie können nun die Details wie unter [Hinzufügen neuer Gruppen](#adding-a-new-group) bearbeiten.

### Kopieren einer vorhandenen Gruppe {#copying-an-existing-group}

1. Verwenden Sie das Kontrollkästchen, um eine Gruppe zu kennzeichnen.
1. Kopieren Sie Gruppendetails mit dem Symbol **Kopieren**:

   ![Vorhandene Gruppe kopieren](do-not-localize/chlimage_1-5.png)

1. Das Formular **Gruppeneinstellungen bearbeiten** wird geöffnet.

   Die Gruppenkennung entspricht der ursprünglichen, vorangestellt ist allerdings der Hinweis `Copy of`. Sie müssen die Kennung bearbeiten, da IDs keine Leerzeichen enthalten dürfen. Alle anderen Angaben bleiben gegenüber dem Original unverändert.

   Sie können nun die Details wie unter [Hinzufügen neuer Gruppen](#adding-a-new-group) bearbeiten.

### Löschen einer vorhandenen Gruppe {#deleting-an-existing-group}

1. Verwenden Sie das Kontrollkästchen, um eine oder mehrere Gruppen zu kennzeichnen.
1. Löschen Sie Gruppendetails mit dem Symbol **Löschen**:

   ![Löschen einer vorhandenen Gruppe](do-not-localize/chlimage_1-6.png)

1. Sie werden zum Bestätigen des Löschvorgangs aufgefordert. Daraufhin wird durch eine Meldung bestätigt, dass der Löschvorgang tatsächlich durchgeführt wurde.
