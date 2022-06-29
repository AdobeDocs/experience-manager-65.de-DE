---
title: Gruppen konfigurieren und erstellen
seo-title: Creating and configuring groups
description: Erfahren Sie, wie Sie Gruppen manuell oder dynamisch erstellen, eine Gruppe bearbeiten, Details zu einer Gruppe anzeigen oder eine Gruppe löschen.
seo-description: Learn how to create groups manually or dynamically, edit a group, view details about a group, or delete a group.
uuid: 8532d72b-270a-4fcf-b7a5-56fca979a5fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 2058b501-65ce-4ad3-8e1b-b2eab896f70f
exl-id: 72edd8d1-8573-4942-8ced-1a100af58d78
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1569'
ht-degree: 100%

---

# Gruppen konfigurieren und erstellen{#creating-and-configuring-groups}

Wenn Sie Benutzergruppen erstellen, können Sie Rollen einer Gruppe anstatt einzelnen Benutzern zuzuweisen.

Es gibt zwei verschiedene Typen von Gruppen. Sie können eine Gruppe manuell erstellen und Benutzer und andere Gruppen hinzufügen. Oder Sie erstellen eine dynamische Gruppe, die automatisch alle Benutzer umfasst, die bestimmte Kriterien (Regeln) erfüllen.

Für Benutzer kann es zu langsameren Reaktionszeiten kommen, wenn sie vielen Gruppen (z. B. 500 oder mehr) angehören oder wenn die Gruppen tief verschachtelt sind (z. B. 30 Ebenen). Wenn dieses Problem auftritt, können Sie AEM Forms so konfigurieren, dass Informationen aus bestimmten Domains vorher abgerufen werden. (Siehe [AEM Forms zum vorherigen Abrufen von Domain-Informationen konfigurieren](/help/forms/using/admin-help/configure-aem-forms-prefetch-domain.md#configure-aem-forms-to-prefetch-domain-information).)

## Gruppen manuell erstellen {#create-a-group-manually}

Wenn Sie eine Gruppe manuell erstellen, können Sie dieser Gruppe Benutzer und andere Gruppen hinzufügen und der Gruppe Rollen zuweisen. Sie können die Gruppe auch mit einer übergeordneten Gruppe verknüpfen.

Wenn Sie Content Services (nicht mehr unterstützt) verwenden, können Sie auf der Seite „Domain-Verwaltung“ die Option „Wählen Sie diese Option, um für Benutzer und Gruppen ein Pushing in registrierte externe Prinzipalspeicheranbieter durchzuführen“ wählen, um ein Pushing der Informationen für alle neu erstellten Benutzer und Gruppen in Content Services (nicht mehr unterstützt) durchzuführen.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“ und dann auf „Neue Gruppe“.
1. Nehmen Sie unter „Allgemeine Einstellungen“ die gewünschten Einstellungen vor und klicken Sie auf „Weiter“. Kanonischer Name und Gruppenname sind obligatorische Attribute.

   Der kanonische Name ist ein eindeutiger Bezeichner der Gruppe. Jede Gruppe und jeder Benutzer in einer Domain muss einen eindeutigen kanonischen Namen haben. Aktivieren Sie das Kontrollkästchen „Von System erstellt“, damit Benutzer-Management einen eindeutigen Wert zuweist, oder deaktivieren Sie das Kontrollkästchen und geben Sie einen benutzerdefinierten Wert für den kanonischen Namen an.

   Vermeiden Sie den Unterstrich (_) in kanonischen Namen z. B. `sample_group`. Wenn Sie Gruppen nach kanonischen Namen suchen, werden solche mit Unterstrich nicht zurückgegeben.

1. Um Benutzer und Gruppen zu dieser neuen Gruppe hinzuzufügen, klicken Sie auf „Benutzer/Gruppen suchen“ und führen folgende Schritte durch:

   * Geben Sie im Feld „Suchen“ die gewünschten Suchkriterien ein.
   * Wählen Sie in der Liste „in“ entweder „Benutzer“, „Gruppen“ oder „Benutzer und Gruppen“ aus.
   * Wählen Sie in der Liste „Verwendet“ den Suchparameter „Name“, „E-Mail“ oder „Benutzer-ID“ aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie im Suchergebnis die Kontrollkästchen der Benutzer und Gruppen, die Sie dieser neuen Gruppe hinzufügen möchten, und klicken Sie auf „OK“.

1. Klicken Sie auf Weiter.
1. Um diese neue Gruppe zu anderen, bestehenden Gruppen hinzuzufügen, klicken Sie auf „Gruppen suchen“ und führen folgende Schritte durch:

   * Geben Sie im Feld „Suchen“ die gewünschten Suchkriterien ein.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie im Suchergebnis die Kontrollkästchen der Gruppen, zu denen die neue Gruppe gehören soll, und klicken Sie auf „OK“.

1. Klicken Sie auf Weiter.
1. Um der Gruppe Rollen zuzuweisen, klicken Sie auf „Rollen suchen“, aktivieren die Kontrollkästchen der für die Gruppe zuzuweisenden Rollen und klicken Sie auf „OK“. Benutzer in der Gruppe übernehmen Rollen, die auf Gruppenebene zugewiesen werden.
1. Klicken Sie auf Beenden.

## Dynamische Gruppe erstellen {#create-a-dynamic-group}

Bei einer dynamischen Gruppe wählen Sie die Benutzer für die Gruppe nicht einzeln aus. Stattdessen legen Sie einen Regelsatz fest und alle Benutzer, die diesen Regeln entsprechen, werden automatisch zu der dynamischen Gruppe hinzugefügt.

Sie haben zwei Möglichkeiten zum Erstellen dynamischer Gruppen:

* Aktivieren Sie die automatische Erstellung dynamischer Gruppen auf Basis von E-Mail-Domains (z. B. @adobe.com). Wenn Sie diese Funktion aktivieren, erstellt User Management eine dynamische Gruppe für jede eindeutige E-Mail-Domain in der AEM Forms-Datenbank. Verwenden Sie einen Cron-Ausdruck, um anzugeben, wie oft User Management die AEM Forms-Datenbank nach neuen E-Mail-Domains durchsuchen soll. Diese dynamischen Gruppen werden der lokalen Domain „DefaultDom“ hinzugefügt und erhalten die Bezeichnung „Alle Benutzer mit einer *`[email domain]`*-E-Mail-ID“.
* Erstellen Sie eine dynamische Gruppe auf der Grundlage von bestimmten Kriterien, wie E-Mail-Domain des Benutzers, Beschreibung, allgemeinem Namen, kanonischem Namen und Domain-Namen. Damit er in eine dynamische Gruppe aufgenommen werden kann, muss ein Benutzer alle angegebenen Kriterien erfüllen. Zum Festlegen einer „oder“-Bedingung erstellen Sie zwei separate dynamische Gruppen und fügen sie beide einer lokalen Gruppe hinzu. Verwenden Sie diese Vorgehensweise beispielsweise, um eine Gruppe von Benutzern zu erstellen, die zur E-Mail-Domain „@adobe.com“ gehören oder deren kanonischer Name ou=adobe.com enthält. Die Benutzer müssten jedoch nicht unbedingt beide Bedingungen erfüllen.

Eine dynamische Gruppe enthält nur Benutzer. Sie kann keine anderen Gruppen enthalten. Eine dynamische Gruppe kann jedoch zu einer übergeordneten Gruppe gehören.

### Dynamische Gruppen auf Basis von E-Mail-Domains automatisch erstellen {#automatically-create-dynamic-groups-based-on-email-domains}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Erweiterte Systemattribute konfigurieren“.
1. Aktivieren Sie unter „Automatische Erstellung einer dynamischen Gruppe“ das Kontrollkästchen.
1. Geben Sie an, wann User Manager auf neue E-Mail-Domains prüfen soll. Diese Zeit sollte nach der Domain-Synchronisierungszeit liegen, da die Erstellung dynamischer Gruppen nur sinnvoll ist, wenn die Domain-Synchronisierung abgeschlossen ist.

   * Um die automatische tägliche Synchronisierung zu aktivieren, geben die Uhrzeit im 24-Stunden-Format in das Feld „Täglich um“ ein. Wenn Sie die Einstellungen speichern, wird dieser Wert in einen Cron-Ausdruck konvertiert, der im Feld unten angezeigt wird.
   * Um die Synchronisierung an einem bestimmten Tag der Woche bzw. des Monats oder an einem bestimmten Monat zu planen, wählen Sie „Cron-Ausdruck“ aus und geben den entsprechenden Ausdruck in das Feld ein. Der Standardwert ist `0 00 4 ? * *`(d. h. jeden Tag um 4 Uhr nachprüfen).

      Die Verwendung des Cron-Ausdrucks basiert auf dem Open-Source-Auftragsplanungssystem Quartz, Version 1.4.0.

1. Klicken Sie auf Speichern.

### Dynamische Gruppen auf Basis von bestimmten Kriterien erstellen {#create-a-dynamic-group-based-on-specified-criteria}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Klicken Sie auf „Neue dynamische Gruppe“.
1. Füllen Sie den Abschnitt „Allgemeine Einstellungen“ aus. „Gruppenname“ ist ein obligatorisches Attribut. Sie können die Gruppe einer beliebigen konfigurierten Domain zuordnen.
1. Geben Sie unter „Kriterien für dynamische Gruppen“ ein oder mehrere Attribute zum Ausfüllen der dynamischen Gruppe an.

   >[!NOTE]
   >
   >Wenn das Gleichheitszeichen mit den Attributen „E-Mail“, „Beschreibung“ oder „Kanonischer Name“ verwendet wird, muss bei den Attributen die Groß- und Kleinschreibung beachtet werden. Bei den Operatoren „Beginnt mit“, „Endet mit“ oder „Enthält“ muss die Groß- und Kleinschreibung nicht beachtet werden.

   **E-Mail:** Die E-Mail-Domain des Benutzers, z. B. `@adobe.com`.

   **Beschreibung**: Beschreibung des Benutzers, z. B. „Informatiker“.

   **Kanonischer Name:** Der kanonische Name des Benutzers, z. B. `ou=adobe.com`.

   **Domain-Name**: Der Name der Domain, zu der der Benutzer gehört, z. B. `DefaultDom`. Bei dem Attribut „Domain-Name“ muss die Groß- und Kleinschreibung beachtet werden, wenn der Operator „Enthält“ verwendet wird. Bei den Operatoren „Beginnt mit“, „Endet mit“ oder „Enthält“ muss die Groß- und Kleinschreibung nicht beachtet werden.

1. Klicken Sie auf Testen. Auf der Testseite werden die ersten 200 Benutzer, die den angegebenen Kriterien entsprechen, angezeigt. Klicken Sie auf Schließen.
1. Wenn bei dem Test die erwarteten Ergebnisse ausgegeben werden, klicken Sie auf „Weiter“. Bearbeiten Sie andernfalls die Kriterien der dynamischen Gruppe und führen Sie den Test erneut durch.
1. Um die dynamische Gruppe zu einer übergeordneten Gruppe hinzuzufügen, klicken Sie auf „Gruppen suchen“ und führen folgende Schritte durch:

   * Geben Sie im Feld „Suchen“ die gewünschten Suchkriterien ein.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie im Suchergebnis die Kontrollkästchen der Gruppen, zu denen die dynamische Gruppe gehören soll, und klicken Sie auf „OK“.

1. Klicken Sie auf Weiter.
1. Um der Gruppe Rollen zuzuweisen, klicken Sie auf „Rollen suchen“, aktivieren die Kontrollkästchen der für die Gruppe zuzuweisenden Rollen und klicken Sie dann auf „OK“. Benutzer in der Gruppe übernehmen Rollen, die auf Gruppenebene zugewiesen werden.
1. Klicken Sie auf Beenden.

## Details zu einer Gruppe anzeigen {#view-details-about-a-group}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Wählen Sie in der Liste „In“ die Option „Gruppe“ aus und klicken Sie dann auf „Suchen“. Die Suchergebnisse werden im unteren Seitenbereich angezeigt. Sie können die Liste durch Klicken auf die Spaltenüberschriften sortieren.
1. Klicken Sie auf den Namen der Gruppe, zu der Details angezeigt werden sollen. Die Seite „Gruppendetails“ wird angezeigt.
1. Um direkte Mitglieder der Gruppe anzuzeigen, klicken Sie auf „Untergeordnete Prinzipale“.

## Eine Gruppe bearbeiten {#edit-a-group}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Führen Sie zum Suchen der zu bearbeitenden Gruppe die folgenden Schritte aus:

   * Geben Sie im Feld „Suchen“ die gewünschten Suchkriterien ein.
   * Wählen Sie in der Liste „Verwendet“ den Suchparameter „Name“ oder „E-Mail“ aus.
   * Wählen Sie in der Liste „In“ den Eintrag „Gruppen“ aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf „Suchen“.
   * Klicken Sie im Suchergebnis auf den Namen der zu bearbeitenden Gruppe.

1. Bearbeiten Sie auf der Registerkarte „Details“ die allgemeinen Einstellungen und klicken Sie auf „Speichern“.
1. Um die verknüpften Gruppen zu bearbeiten, klicken Sie auf die Registerkarte „Übergeordnete Gruppen“ und führen folgende Schritte durch:

   * Wenn Sie Gruppen suchen möchten, die zur Verknüpfung hinzugefügt werden sollen, klicken Sie auf „Gruppen suchen“ und geben die Suchinformationen ein.
   * Um Gruppen hinzuzufügen, aktivieren Sie die Kontrollkästchen der hinzuzufügenden Gruppen und klicken Sie erst auf „OK“ und anschließend auf „Speichern“.
   * Zum Löschen einer verknüpften Gruppe aktivieren Sie das Kontrollkästchen der zu löschenden Gruppe, klicken erst auf „Löschen“, dann auf „OK“ und anschließend auf „Speichern“.

1. Um die in der Gruppe enthaltenen Benutzer und Gruppen zu bearbeiten, klicken Sie auf die Registerkarte „Untergeordnete Prinzipale“ und führen die folgenden Schritte aus:

   * Um hinzuzufügende Benutzer und Gruppen zu suchen, klicken Sie auf „Benutzer/Gruppen suchen“ und geben die Suchinformationen ein.
   * Um einen Benutzer oder eine Gruppe hinzuzufügen, aktivieren Sie das zugehörige Kontrollkästchen und klicken auf „OK“ und anschließend auf „Speichern“.
   * Zum Löschen eines Benutzers oder einer Gruppe aktivieren Sie das Kontrollkästchen des Benutzers oder der Gruppe und klicken erst auf „Löschen“, dann auf „OK“ und anschließend auf „Speichern“.

1. Um die Rollenzuweisungen zu bearbeiten, klicken Sie auf die Registerkarte „Rollenzuweisungen“.

   * Um Rollen zu suchen, die der Gruppe zugewiesen werden sollen, klicken Sie auf „Rollen suchen“.
   * Um eine Rolle hinzuzufügen, aktivieren Sie das Kontrollkästchen für die Rolle und klicken auf „OK“ und anschließend auf „Speichern“.
   * Um die Zuweisung einer Rolle aufzuheben, aktivieren Sie das Kontrollkästchen für die Rolle und klicken auf „Zuweisung aufheben“ und anschließend auf „Speichern“.

## Eine Gruppe löschen {#delete-a-group}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Wählen Sie in der Liste „In“ die Option „Gruppen“ aus und klicken Sie dann auf „Suchen“.
1. Aktivieren Sie das Kontrollkästchen der zu löschenden Gruppe und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.
