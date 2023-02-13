---
title: Benutzer hinzufügen und konfigurieren
seo-title: Adding and configuring users
description: Mit den Benutzerverwaltungs-Einstellungen in der Administration Console können Sie Benutzer erstellen oder löschen sowie weitere Benutzereinstellungen konfigurieren.
seo-description: The User Management settings in the administration console allow you to create or delete users  and configure other user settings.
uuid: fe650cdb-7d0d-4f38-9899-e5349559ed32
contentOwner: admin
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
discoiquuid: 20ca99e3-4843-4254-b3e9-0255cc752363
exl-id: 50eea35d-d844-4f4b-9cbe-7d84bd6b1e3b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1739'
ht-degree: 100%

---

# Hinzufügen und Konfigurieren von Benutzenden {#adding-and-configuring-users}

Benutzer- und Gruppeninformationen werden in einem Speichersystem von Drittanbietern (z. B. einem LDAP-Ordner) verwaltet. User Management schreibt nicht in das Speichersystem von Drittanbietern. Statt dessen synchronisiert User Management die Benutzer- und Gruppeninformationen mit seiner Datenbank

## Benutzer erstellen {#create-a-user}

Beim Erstellen von Benutzern können Sie diese Gruppen hinzufügen und ihnen Rollen zuweisen.

1. Klicken Sie in Administration-Console auf **[!UICONTROL Einstellungen > User Management > „Benutzer und Gruppen]** und dann auf **[!UICONTROL Neuer Benutzer]**.
1. Geben Sie unter **[!UICONTROL Allgemeine Einstellungen]** die angeforderten Informationen ein und klicken Sie auf **[!UICONTROL Weiter]**. Informationen zu diesen Einstellungen finden Sie unter [Benutzereinstellungen](adding-configuring-users.md#user-settings).
1. (Optional) Um den Benutzer einer Gruppe hinzuzufügen, klicken Sie auf **[!UICONTROL Gruppen suchen]** und führen folgende Aufgaben durch:

   * Geben Sie in das Feld **[!UICONTROL Suchen]** den vollständigen Gruppennamen oder einen Teil des Gruppennamens ein.
   * Wählen Sie die zu suchende Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf **[!UICONTROL Suchen]**.
   * (Optional) Um Gruppendetails anzuzeigen, wählen Sie den Gruppennamen aus und klicken auf **[!UICONTROL OK]**, um zur Suchergebnisseite zurückzukehren.
   * Aktivieren Sie das Kontrollkästchen für die Gruppe und klicken Sie auf **[!UICONTROL OK]**.
   * Klicken Sie auf **[!UICONTROL Weiter]**.

1. (Optional) Um dem Benutzer Rollen zuzuweisen, klicken Sie auf **[!UICONTROL Rollen suchen]**, markieren Sie die Kontrollkästchen der zuzuweisenden Rollen und klicken dann auf **[!UICONTROL OK]**.
1. Klicken Sie auf **[!UICONTROL Beenden]**.

   >[!NOTE]
   >
   >Wenn ein Anmeldeproblem auftritt, lesen Sie[ AEM Forms on JEE-Benutzeranmeldung schlägt auf AEM Forms on OSGi fehlt](https://helpx.adobe.com/de/aem-forms/kb/AEM-users-fails-to-login.html).

## Benutzereinstellungen {#user-settings}

Geben Sie die folgenden Einstellungen an, wenn Sie einen Benutzer erstellen oder bearbeiten.

**Kanonischer Name**: (Obligatorisch) Eindeutiger Bezeichner für den Benutzer. Jeder Benutzer und jede Gruppe in einer Domain muss einen eindeutigen kanonischen Namen haben. Aktivieren Sie das Kontrollkästchen „Von System erstellt“, damit Benutzer-Management einen eindeutigen Wert zuweist, oder deaktivieren Sie das Kontrollkästchen und geben Sie einen benutzerdefinierten Wert für den kanonischen Namen an.

Vermeiden Sie den Unterstrich (_) in kanonischen Namen z. B. `sample_user`. Wenn Sie Benutzer nach kanonischen Namen suchen, werden solche mit Unterstrich nicht zurückgegeben.

**Vorname**: (Obligatorisch) Der Vorname des Benutzers

**Nachname**: (Obligatorisch) Der Nachname des Benutzers

**Allgemeiner Name**: Vollständiger Name bzw. Anzeigename des Benutzers. Beispiel: Vorname = Gloria, Nachname = Rios, dann Allgemeiner Name = Gloria Rios.

**E-Mail**: Die E-Mail-Adresse des Benutzers

**Telefon**: Telefonnummer des Benutzers

**Beschreibung**: Optionale Beschreibung. Geben Sie hier eine passende Beschreibung ein.

**Adresse**: Die Anschrift des Benutzers

**Firma**: Firma, der der Benutzer angehört

**E-Mail-Aliasse**: Die E-Mail-Aliasse des Benutzers. Trennen Sie die E-Mail-Aliasse durch Kommas.

**Domain**: Domain, der der Benutzer angehört

**Gebietsschema**: Das ISO-Gebietsschema des Benutzers

**Geschäftskalenderschlüssel**: Ermöglicht das Zuordnen eines Geschäftskalenders zu einem Benutzer auf Grundlage des Wertes dieser Einstellung. Im Geschäftskalender werden Arbeits- und freie Tage definiert. AEM Forms kann Geschäftskalender zum Berechnen künftiger Termine und Zeiten für Ereignisse wie Erinnerungen, Fristen und Eskalationen verwenden. Die Methode zum Zuweisen von Geschäftskalenderschlüsseln zu Benutzern ist davon abhängig, ob eine Unternehmens-, eine lokale oder eine Hybrid-Domain verwendet wird. (Siehe [Hinzufügen von Domains](/help/forms/using/admin-help/adding-domains.md#adding-domains).)

Wenn Sie eine lokale oder Hybrid-Domain verwenden, werden Informationen zu Benutzern nur in der User Management-Datenbank gespeichert. Legen Sie für diese Benutzer den Geschäftskalenderschlüssel auf eine Zeichenfolge fest. Anschließend ordnen Sie den Geschäftskalenderschlüssel (die Zeichenfolge) einem Geschäftskalender im Arbeitsablauf für Formulare zu.

Wenn Sie eine Unternehmens-Domain verwenden, befinden sich Informationen zu Benutzern in einem Speichersystem von Drittanbietern (z. B. einem LDAP-Ordner). User Management synchronisiert Benutzerinformationen aus dem Ordner mit der User Management-Datenbank. Mit dieser Funktion können Sie einen Geschäftskalenderschlüssel einem Feld im LDAP-Ordner zuordnen. Wenn beispielsweise jeder Benutzerdatensatz im Ordner das Feld „country“ enthält und Sie Geschäftskalender auf Grundlage des Landes zuweisen möchten, in dem sich der Benutzer befindet, geben Sie den Feldnamen „country“ als Wert für die Einstellung „Geschäftskalender“ an. Anschließend können Sie die Geschäftskalenderschlüssel (die für das Feld „country“ im LDAP-Ordner definierten Werte) Geschäftskalendern im Arbeitsablauf für Formulare zuordnen.

Weitere Informationen zu Geschäftskalendern, einschließlich dem Zuordnen von Geschäftskalenderschlüsseln zu Geschäftskalendern, finden Sie unter [Geschäftskalender konfigurieren](/help/forms/using/admin-help/configuring-business-calendars.md#configuring-business-calendars).

Der Name darf nicht länger als 53 Zeichen sein. Ein kürzerer Name verhindert Probleme beim Anzeigen des Geschäftskalenderschlüssels auf den Seiten in Process Management in Administration Console.

**Benutzer-ID**: (Obligatorisch) Benutzer-ID, mit dem sich der Benutzer anmeldet. Bei der Benutzer-ID muss die Groß-/Kleinschreibung zwar nicht beachtet werden, aber sie muss innerhalb der Domain eindeutig sein.

Verwenden Sie bei Unternehmens-Domains als Benutzer-ID ein Nicht-DN-Attribut, da sich der definierte Name (DN) eines Benutzers ändern kann, wenn er in einen anderen Unternehmensbereich wechselt. Diese Einstellung hängt vom Ordnerserver ab. Für Active Directory 2003 lautet der Wert `objectGUID`, für Sun™ One lautet er `nsuniqueID` und für eDirectory `guid`.

Stellen Sie sicher, dass die Benutzer-ID eindeutig ist. Verwenden Sie keine Benutzer-ID, die einem gelöschten Benutzer zugewiesen war.

AEM Forms kann nicht zwischen Benutzerkonten aus verschiedenen Domains mit identischen Benutzer-IDs und Kennwörtern unterscheiden. Zur Vermeidung dieses Problems erstellen Sie keine Konten mit identischen Benutzer-IDs in mehreren Domains.

Wenn Sie eine SQL Server-Datenbank nutzen, darf die Benutzer-ID nicht mehr als 255 Zeichen lang sein.

Bei Verwendung von MySQL darf die Benutzer-ID erweiterte Zeichen enthalten. Bei einem Vergleich zwischen zwei derartigen Zeichenfolgen, wie z. B. „abcde“ und „âbcdè“, werden sie aber als identisch bewertet. Wenn der Datenbank ein neuer Benutzer hinzugefügt wurde, wird beispielsweise beim Synchronisieren ein Vergleich ausgeführt, um festzustellen, ob ein Benutzer mit derselben Benutzer-ID in der Datenbank vorhanden ist. Wenn der Benutzer *abcde* bereits in der Datenbank vorhanden ist, wenn der neue Benutzer *âbcdè* hinzugefügt wird, kann der Vergleichsvorgang die beiden Namen nicht unterscheiden. Es wird angenommen, dass der Benutzer bereits in der Datenbank vorhanden ist, weshalb der neue Benutzer ignoriert und nicht hinzugefügt wird.

Vermeiden Sie das Erstellen von Benutzernamen, die mit einem Nummernzeichen beginnen (#). Beim Suchen nach Aufgaben werden keine Ergebnisse für diese Benutzernamen ausgegeben. (Siehe [Mit Aufgaben arbeiten](/help/forms/using/admin-help/tasks.md#working-with-tasks).)

**Kennwort und Kennwort bestätigen**: Kennwort, das der Benutzer zum Anmelden verwendet. Es muss mindestens acht Zeichen lang sein. Für Benutzer in einer Hybrid-Domain ist kein Kennwort erforderlich.

## Details zu Benutzern anzeigen {#view-details-about-a-user}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Benutzer und Gruppen“.
1. Geben Sie Informationen zum Eingrenzen der Suche ein, wählen Sie in der Liste „in“ die Option „Benutzer“ aus und klicken Sie dann auf „Suchen“. Die Suchergebnisse werden im unteren Seitenbereich angezeigt. Sie können die Liste durch Klicken auf die Spaltenüberschriften sortieren.
1. Klicken Sie auf den Namen des Benutzers, zu dem Details angezeigt werden sollen. Auf der Seite „Benutzer bearbeiten“ werden Details zum Benutzer wie die folgenden angezeigt:

   * Allgemeine Kenndaten wie Name, E-Mail-Adresse, Postanschrift, Domain und Firma
   * Dem Benutzer zugewiesene Rollen
   * Gruppen, bei denen der Benutzer Mitglied ist

## Kennwörter für lokale Benutzer ändern {#change-the-password-for-a-local-user}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Benutzer und Gruppen]**.
1. Geben Sie Informationen ein, um die Suche auf einen bestimmten Benutzer einzugrenzen, und klicken Sie auf **[!UICONTROL Suchen]**. Die Suchergebnisse werden im unteren Seitenbereich angezeigt. Sie können die Liste durch Klicken auf die Spaltenüberschriften sortieren.
1. Klicken Sie auf den Namen des Benutzers und anschließend auf **[!UICONTROL Kennwort ändern]**.
1. Geben Sie das neue Kennwort ein, bestätigen Sie es durch erneute Eingabe und klicken Sie auf **[!UICONTROL OK]**. Das Kennwort muss mindestens acht Zeichen lang sein.

## Eigenschaften eines Benutzers bearbeiten {#edit-a-user-s-properties}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Benutzer und Gruppen]**.
1. Führen Sie zum Suchen des zu bearbeitenden Benutzers die folgenden Schritte aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld **[!UICONTROL Suchen]** ein.
   * Wählen Sie in der Liste **[!UICONTROL Verwendet]** den Suchparameter **[!UICONTROL Name]**, **[!UICONTROL E-Mail]** oder **[!UICONTROL Benutzer-ID]** aus.
   * Wählen Sie in der Liste **[!UICONTROL In]** den Eintrag **[!UICONTROL Benutzer]** aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf **[!UICONTROL Suchen]**.

1. Klicken Sie auf den zu bearbeitenden Benutzer.
1. Bearbeiten Sie bei einem Benutzer, der zu einer lokalen oder Hybrid-Domain gehört, auf der Registerkarte **[!UICONTROL Details]** die Angaben unter **[!UICONTROL Allgemeine Einstellungen]** und **[!UICONTROL Anmeldeeinstellungen]** und klicken Sie auf **[!UICONTROL Speichern]**. Informationen zu diesen Einstellungen finden Sie unter [Benutzereinstellungen](adding-configuring-users.md#user-settings). Die allgemeinen und Anmeldeeinstellungen von Benutzern, die zu einer Unternehmens-Domain gehören, können nicht bearbeitet werden.
1. Um die Gruppeneinstellungen des Benutzers zu bearbeiten, klicken Sie auf die Registerkarte **[!UICONTROL Gruppenmitgliedschaft]** und führen Sie die folgenden Aufgaben aus:

   * Klicken Sie auf **[!UICONTROL Gruppen suchen]** und füllen Sie die Suchinformationen aus.
   * Um den Benutzer einer neuen Gruppe hinzuzufügen, aktivieren Sie das Kontrollkästchen der Gruppe, klicken auf **[!UICONTROL OK]** und anschließend auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Lokale Benutzer können keinen Ordnergruppen hinzugefügt werden. Ordnerbenutzer können jedoch lokalen Gruppen hinzugefügt werden.

   * Um den Benutzer aus einer Gruppe zu entfernen, aktivieren Sie das Kontrollkästchen für die Gruppe, klicken auf **[!UICONTROL Löschen]** und anschließend auf **[!UICONTROL Speichern]**.


1. Um die Rollen des Benutzers zu bearbeiten, klicken Sie auf die Registerkarte **[!UICONTROL Rollenzuweisungen]** und führen die folgenden Aufgaben aus:

   * Um eine Liste der Rollen anzuzeigen, klicken Sie auf **[!UICONTROL Rollen suchen]**.
   * Um eine Rolle hinzuzufügen, aktivieren Sie das Kontrollkästchen für die Rolle und klicken auf **[!UICONTROL OK]** und anschließend auf **[!UICONTROL Speichern]**.
   * Um eine Rolle zu entfernen, aktivieren Sie das Kontrollkästchen für die Rolle, klicken auf **[!UICONTROL Zuweisung aufheben]** und anschließend auf **[!UICONTROL Speichern]**.

## Benutzer löschen {#delete-a-user}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Benutzer und Gruppen]**.
1. Führen Sie zum Suchen des zu löschenden Benutzers die folgenden Schritte aus:

   * Geben Sie die gewünschten Suchkriterien in das Feld **[!UICONTROL Suchen]** ein.
   * Wählen Sie in der Liste **[!UICONTROL Verwendet]** den Suchparameter **[!UICONTROL Name]**, **[!UICONTROL E-Mail]** oder **[!UICONTROL Benutzer-ID]** aus.
   * Wählen Sie in der Liste **[!UICONTROL In]** den Eintrag **[!UICONTROL Benutzer]** aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Elemente aus und klicken Sie auf **[!UICONTROL Suchen]**.

1. Aktivieren Sie das Kontrollkästchen des Benutzers und klicken Sie erst auf **[!UICONTROL Löschen]** und anschließend auf **[!UICONTROL OK]**.

>[!NOTE]
>
>Mit AEM Forms on JEE können Benutzer des AEM-Forms-Add-Ons, die auf OSGi ausgeführt werden, als AEM-Benutzer erkannt werden. Dies ist in Fällen erforderlich, in denen eine einmalige Anmeldung für AEM Forms on JEE und AEM Forms-Add-On auf OSGi erforderlich ist (z. B. HTML Workspace). Der oben genannte Löschvorgang entfernt einen Benutzer nur von AEM Forms on JEE. Der Benutzer wird nicht aus dem AEM Forms Add-On auf der OSGi-Umgebung gelöscht. Aber jeder Anmeldeversuch nach dem Löschen des Benutzers (ein Anmeldeversuch bei AEM Forms Add-On-JEE-Server oder AEM Forms-Add-On auf einer OSGi-Umgebung), wird verweigert.

## Benutzerdefinierten Anmeldungsfehlerhandler erstellen {#create-custom-login-error-handler}

Wenn ein Benutzer ohne die erforderlichen - und CQ-Berechtigungen versucht, sich bei den folgenden in CQ eingebetteten AEM Forms-Anwendungen anzumelden, wird er auf die standardmäßige CQ-Seite mit dem Fehler 404 und dem Fehlerprotokoll weitergeleitet:

* Correspondence Management Solution
* AEM Forms Workspace

   ***Hinweis **: Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.*

* Forms Manager
* Prozessberichterstellung

In CQ steht ein Mechanismus zur Verfügung, mit dem das JSP für den standardmäßigen 404-Handler außer Kraft gesetzt werden kann.

Detaillierte Informationen zum Anpassen der Seite für den Fehlerhandler finden Sie unter [Im Fehlerhandler angezeigte Seiten anpassen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de) in der Dokumentation zu Adobe Experience Manager.
