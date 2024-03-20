---
title: Hinzufügen und Konfigurieren von Benutzenden
description: Mit den Benutzerverwaltungs-Einstellungen in der Administration Console können Sie Benutzende erstellen oder löschen sowie weitere Benutzereinstellungen konfigurieren.
contentOwner: admin
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
exl-id: 50eea35d-d844-4f4b-9cbe-7d84bd6b1e3b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1727'
ht-degree: 100%

---

# Hinzufügen und Konfigurieren von Benutzenden {#adding-and-configuring-users}

Benutzer- und Gruppeninformationen werden in einem Speichersystem von Drittanbietern verwaltet, z. B. in einem LDAP-Verzeichnis. User Management schreibt nicht in das Speichersystem von Drittanbietern. Stattdessen synchronisiert User Management die Benutzer- und Gruppeninformationen mit einer eigenen Datenbank

## Erstellen von neuen Benutzern bzw. Benutzerinnen {#create-a-user}

Wenn Sie Benutzer bzw. Benutzerinnen erstellen, können Sie diese zu Gruppen hinzufügen und ihnen Rollen zuweisen.

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
   >Wenn ein Anmeldeproblem auftritt, lesen Sie [AEM Forms on JEE-Benutzeranmeldung schlägt auf AEM Forms on OSGi fehl](https://helpx.adobe.com/de/aem-forms/kb/AEM-users-fails-to-login.html).

## Benutzereinstellungen {#user-settings}

Geben Sie beim Erstellen oder Bearbeiten eines Benutzers bzw. einer Benutzerin die folgenden Einstellungen an.

**Kanonischer Name**: (Obligatorisch) Eindeutiger Bezeichner für den Benutzer. Jeder Benutzer und jede Gruppe in einer Domain muss einen eindeutigen kanonischen Namen haben. Aktivieren Sie das Kontrollkästchen „Systemgeneriert“, damit User Management einen eindeutigen Wert zuweist, oder deaktivieren Sie das Kontrollkästchen und geben Sie einen benutzerdefinierten Wert für den kanonischen Namen an.

Vermeiden Sie den Unterstrich (_) in kanonischen Namen z. B. `sample_user`. Wenn Sie Benutzer nach kanonischen Namen suchen, werden solche mit Unterstrich nicht zurückgegeben.

**Vorname:** (Obligatorisch) Vorname der Benutzerin oder des Benutzers

**Nachname:** (Obligatorisch) Nachname der Benutzerin oder des Benutzers

**Allgemeiner Name**: Vollständiger Name bzw. Anzeigename des Benutzers. Beispiel: Vorname = Gloria, Nachname = Rios, dann Allgemeiner Name = Gloria Rios.

**E-Mail:** E-Mail-Adresse der Benutzerin oder des Benutzers

**Telefon:** Telefonnummer der Benutzerin oder des Benutzers

**Beschreibung**: Optionale Beschreibung. Verwenden Sie dieses Feld gemäß den Anforderungen Ihrer Organisation.

**Adresse:** Anschrift der Benutzerin oder des Benutzers

**Organisation:** Organisation, zu der der Benutzer oder die Benutzerin gehört

**E-Mail-Aliase:** E-Mail-Aliase der Benutzerin oder des Benutzers. Trennen Sie die E-Mail-Aliase durch Kommas.

**Domain**: Domain, der der Benutzer angehört

**Gebietsschema:** ISO-Gebietsschema der Benutzerin oder des Benutzers

**Geschäftskalenderschlüssel**: Ermöglicht das Zuordnen eines Geschäftskalenders zu einem Benutzer auf Grundlage des Wertes dieser Einstellung. Geschäftskalender definieren Geschäftstage und geschäftsfreie Tage. AEM-Formulare können bei der Berechnung künftiger Daten und Zeiten für Ereignisse wie Erinnerungen, Fristen und Eskalationen Geschäftskalender verwenden. Die Methode zum Zuweisen von Geschäftskalenderschlüsseln zu Benutzern ist davon abhängig, ob eine Unternehmens-, eine lokale oder eine Hybrid-Domain verwendet wird. (Siehe [Hinzufügen von Domains](/help/forms/using/admin-help/adding-domains.md#adding-domains).)

Wenn Sie eine lokale oder Hybrid-Domain verwenden, werden Informationen zu Benutzern nur in der User Management-Datenbank gespeichert. Legen Sie für diese Benutzer bzw. Benutzerinnen den Geschäftskalenderschlüssel auf eine Zeichenfolge fest. Ordnen Sie dann den Geschäftskalenderschlüssel (die Zeichenfolge) einem Geschäftskalender im Arbeitsablauf für Formulare zu.

Wenn Sie eine Unternehmens-Domain verwenden, befinden sich Informationen zu Benutzern in einem Speichersystem von Drittanbietern (z. B. einem LDAP-Ordner). User Management synchronisiert Benutzerinformationen aus dem Verzeichnis mit der User Management-Datenbank. Mit dieser Funktion können Sie einen Geschäftskalenderschlüssel einem Feld im LDAP-Verzeichnis zuordnen. Angenommen, jeder Benutzerdatensatz in Ihrem Verzeichnis enthält das Feld „Land“, und Sie möchten Geschäftskalender auf Grundlage des Landes zuweisen, in dem sich die Benutzerin bzw. der Benutzer befindet. In diesem Fall geben Sie den Feldnamen „Land“ als Wert für die Einstellung „Geschäftskalenderschlüssel“ an. Anschließend können Sie die Geschäftskalenderschlüssel (die für das Feld „Land“ im LDAP-Verzeichnis definierten Werte) Geschäftskalendern im Arbeitsablauf für Formulare zuordnen.

Weitere Informationen zu Geschäftskalendern, einschließlich der Zuordnung von Geschäftskalenderschlüsseln zu Geschäftskalendern, finden Sie unter [Konfigurieren von Geschäftskalendern](/help/forms/using/admin-help/configuring-business-calendars.md#configuring-business-calendars).

Begrenzen Sie den Namen auf weniger als 53 Zeichen. Ein kürzerer Name verhindert Probleme beim Anzeigen des Geschäftskalenderschlüssels auf den Seiten „Process Management“ in Administration-Console.

**Benutzer-ID**: (Obligatorisch) Benutzer-ID, mit dem sich der Benutzer anmeldet. Bei der Benutzer-ID muss die Groß-/Kleinschreibung zwar nicht beachtet werden, aber sie muss innerhalb der Domain eindeutig sein.

Verwenden Sie bei Unternehmens-Domains als Benutzer-ID ein Nicht-DN-Attribut, da sich der definierte Name (DN) einer Benutzerin oder eines Benutzers ändern kann, wenn sie bzw. er in einen anderen Unternehmensbereich wechselt. Dieser Wert hängt vom Verzeichnis-Server ab. Für Active Directory 2003 lautet der Wert `objectGUID`, für Sun™ One lautet er `nsuniqueID` und für eDirectory `guid`.

Stellen Sie sicher, dass die Benutzer-ID eindeutig ist. Verwenden Sie keine Benutzer-ID, die einer gelöschten Person zugewiesen war.

AEM Forms kann nicht zwischen Benutzerkonten aus verschiedenen Domains mit identischen Benutzer-IDs und Kennwörtern unterscheiden. Zur Vermeidung dieses Problems erstellen Sie keine Konten mit identischen Benutzer-IDs in mehreren Domains.

Bei Verwendung von SQL Server als Datenbank ist es nicht möglich, eine Benutzer-ID zu erstellen, die 255 Zeichen überschreitet.

Bei Verwendung von MySQL kann die Benutzer-ID erweiterte Zeichen enthalten. Wenn jedoch ein Vergleich zwischen zwei Zeichenfolgen wie „abcde“ und „âbcdè“ durchgeführt wird, werden diese als identisch betrachtet. Wenn beispielsweise bei einer Synchronisierung eine neue Benutzerin oder ein neuer Benutzer zur Datenbank hinzugefügt wurde, wird ein Vergleich durchgeführt, um zu überprüfen, ob eine Person mit derselben Benutzer-ID in der Datenbank vorhanden ist. Falls die Person *abcde* bereits in der Datenbank vorhanden ist, wenn eine neue Person namens *âbcdè* hinzugefügt wird, kann der Vergleichsvorgang die beiden Namen nicht unterscheiden. Es wird also angenommen, dass die Person in der Datenbank vorhanden ist, sodass die neue Person ignoriert und nicht hinzugefügt wird.

Vermeiden Sie das Erstellen von Benutzernamen, die mit einem Nummernzeichen (#) beginnen. Beim Ausführen von Aufgabensuchen werden für diese Benutzernamen keine Ergebnisse zurückgegeben. (Siehe [Arbeiten mit Aufgaben](/help/forms/using/admin-help/tasks.md#working-with-tasks).)

**„Passwort“ und „Passwort bestätigen“**: Passwort, das die Benutzerin oder der Benutzer zum Anmelden verwendet. Es muss mindestens acht Zeichen lang sein. Für Benutzer in einer Hybrid-Domain ist kein Kennwort erforderlich.

## Anzeigen von Details zu Benutzenden {#view-details-about-a-user}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Benutzer und Gruppen“.
1. Geben Sie Informationen zur Eingrenzung der Suche an, wählen Sie in der Liste „In“ die Option „Benutzer“ aus und klicken Sie auf „Suchen“. Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
1. Klicken Sie auf den Namen der Person, zu der Details angezeigt werden sollen. Auf der Seite „Benutzer bearbeiten“ werden Details wie die folgenden zu der Person angezeigt:

   * Allgemeine Kenndaten wie Name, E-Mail-Adresse, Postanschrift, Domain und Firma
   * Der Person zugewiesene Rollen
   * Gruppen, bei denen die Person Mitglied ist

## Ändern des Passwort für lokale Benutzende {#change-the-password-for-a-local-user}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Benutzer und Gruppen]**.
1. Geben Sie Informationen ein, um die Suche auf einen bestimmten Benutzer einzugrenzen, und klicken Sie auf **[!UICONTROL Suchen]**. Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
1. Klicken Sie auf den Namen des Benutzers und anschließend auf **[!UICONTROL Kennwort ändern]**.
1. Geben Sie das neue Kennwort ein, bestätigen Sie es durch erneute Eingabe und klicken Sie auf **[!UICONTROL OK]**. Das Passwort muss mindestens acht Zeichen lang sein.

## Bearbeiten der Eigenschaften einer Benutzerin oder eines Benutzers {#edit-a-user-s-properties}

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
   >Lokale Benutzerinnen oder Benutzer können nicht zu Ordnergruppen hinzugefügt werden. Ordnerbenutzerinnen und -benutzer können jedoch zu lokalen Gruppen hinzugefügt werden.

   * Um den Benutzer aus einer Gruppe zu entfernen, aktivieren Sie das Kontrollkästchen für die Gruppe, klicken auf **[!UICONTROL Löschen]** und anschließend auf **[!UICONTROL Speichern]**.

1. Um die Rollen der Benutzerin bzw. des Benutzers zu bearbeiten, klicken Sie auf die Registerkarte **[!UICONTROL Rollenzuweisungen]** und führen die folgenden Aufgaben aus:

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
>Mit AEM Forms on JEE können Benutzerinnen und Benutzer des AEM Forms-Add-ons, das auf einem OSGi ausgeführt wird, auch als AEM-Benutzerin bzw. -Benutzer erkannt werden. Dies ist in Fällen erforderlich, in denen Single Sign-on zwischen AEM Forms on JEE und dem AEM Forms-Add-On auf einem OSGi erforderlich ist (z. B. HTML Workspace). Der oben genannte Löschvorgang entfernt eine Benutzerin bzw. einen Benutzer nur aus AEM Forms on JEE. Die Person wird nicht aus dem AEM Forms-Add-on gelöscht, das in der OSGi-Umgebung ausgeführt wird. Jeder Anmeldeversuch, der nach dem Löschen der Person unternommen wurde (Anmeldeversuch beim AEM Forms-Add-on JEE-Server oder AEM Forms-Add-On in der OSGi-Umgebung), wird jedoch verweigert.

## Erstellen eines benutzerdefinierten Anmeldungsfehler-Handlers {#create-custom-login-error-handler}

Wenn eine Benutzerin oder ein Benutzer ohne die erforderlichen Berechtigungen für AEM Forms und CQ versucht, sich bei den folgenden in CQ eingebetteten Anwendungen anzumelden, erfolgt eine Weiterleitung zur standardmäßigen 404-Seite von CQ mit dem folgenden Fehlerprotokoll:

* Lösung „Correspondence Management“
* AEM Forms Workspace

  ***Hinweis **: Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.*

* Forms Manager
* Prozessberichterstellung

CQ bietet einen Mechanismus zum Außerkraftsetzen der standardmäßigen 404-Handler-JSP.

Detaillierte Informationen zum Anpassen der Seite für den Fehler-Handler finden Sie unter [Anpassen von Seiten, die im Fehler-Handler angezeigt werden](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/customizing-errorhandler-pages.html?lang=de) in der Dokumentation zu Adobe Experience Manager.
