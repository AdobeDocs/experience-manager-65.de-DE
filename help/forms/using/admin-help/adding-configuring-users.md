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
source-git-commit: 4fa868f3ae4778d3a637e90b91f7c5909fe5f8aa
workflow-type: tm+mt
source-wordcount: '1735'
ht-degree: 45%

---

# Hinzufügen und Konfigurieren von Benutzenden {#adding-and-configuring-users}

Benutzer- und Gruppeninformationen werden in einem Speichersystem von Drittanbietern verwaltet, z. B. in einem LDAP-Ordner. User Management schreibt nicht in das Speichersystem von Drittanbietern. Stattdessen synchronisiert User Management die Benutzer- und Gruppeninformationen mit einer eigenen Datenbank

## Benutzer erstellen {#create-a-user}

Wenn Sie Benutzer erstellen, können Sie diese Gruppen hinzufügen und ihnen Rollen zuweisen.

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
   >Wenn Sie bei dem Benutzer ein Anmeldeproblem feststellen, lesen Sie [AEM Forms on JEE-Benutzer meldet sich nicht auf OSGi-Seite bei AEM Forms an](https://helpx.adobe.com/de/aem-forms/kb/AEM-users-fails-to-login.html).

## Benutzereinstellungen {#user-settings}

Geben Sie beim Erstellen oder Bearbeiten eines Benutzers die folgenden Einstellungen an.

**Kanonischer Name**: (Obligatorisch) Eindeutiger Bezeichner für den Benutzer. Jeder Benutzer und jede Gruppe in einer Domain muss einen eindeutigen kanonischen Namen haben. Aktivieren Sie das Kontrollkästchen Systemgeneriert , damit User Management einen eindeutigen Wert zuweist, oder deaktivieren Sie das Kontrollkästchen und geben Sie einen benutzerdefinierten Wert für den kanonischen Namen an.

Vermeiden Sie den Unterstrich (_) in kanonischen Namen z. B. `sample_user`. Wenn Sie Benutzer nach kanonischen Namen suchen, werden solche mit Unterstrich nicht zurückgegeben.

**Vorname:** (Obligatorisch) Der Vorname des Benutzers

**Nachname:** (Obligatorisch) Familienname des Benutzers

**Allgemeiner Name**: Vollständiger Name bzw. Anzeigename des Benutzers. Beispiel: Vorname = Gloria, Nachname = Rios, dann Allgemeiner Name = Gloria Rios.

**E-Mail:** E-Mail-Adresse des Benutzers

**Telefon:** Telefonnummer des Benutzers

**Beschreibung**: Optionale Beschreibung. Verwenden Sie dieses Feld entsprechend den Anforderungen Ihres Unternehmens.

**Adresse:** Postanschrift des Benutzers

**Organisation:** Organisation, zu der der Benutzer gehört

**E-Mail-Aliase:** E-Mail-Alias des Benutzers. Trennen Sie die E-Mail-Aliase durch Kommas.

**Domain**: Domain, der der Benutzer angehört

**Gebietsschema:** ISO-Gebietsschema des Benutzers

**Geschäftskalenderschlüssel**: Ermöglicht das Zuordnen eines Geschäftskalenders zu einem Benutzer auf Grundlage des Wertes dieser Einstellung. Geschäftskalender definieren Geschäftstage und geschäftsfreie Tage. AEM Formulare können bei der Berechnung künftiger Daten und Zeiten für Ereignisse wie Erinnerungen, Fristen und Eskalationen Geschäftskalender verwenden. Die Methode zum Zuweisen von Geschäftskalenderschlüsseln zu Benutzern ist davon abhängig, ob eine Unternehmens-, eine lokale oder eine Hybrid-Domain verwendet wird. (Siehe [Hinzufügen von Domains](/help/forms/using/admin-help/adding-domains.md#adding-domains).)

Wenn Sie eine lokale oder Hybrid-Domain verwenden, werden Informationen zu Benutzern nur in der User Management-Datenbank gespeichert. Legen Sie für diese Benutzer den Geschäftskalenderschlüssel auf eine Zeichenfolge fest. Ordnen Sie dann den Geschäftskalenderschlüssel (die Zeichenfolge) einem Geschäftskalender im Arbeitsablauf für Formulare zu.

Wenn Sie eine Unternehmens-Domain verwenden, befinden sich Informationen zu Benutzern in einem Speichersystem von Drittanbietern (z. B. einem LDAP-Ordner). User Management synchronisiert Benutzerinformationen aus dem Ordner mit der User Management-Datenbank. Mit dieser Funktion können Sie einen Geschäftskalenderschlüssel einem Feld im LDAP-Ordner zuordnen. Angenommen, jeder Benutzerdatensatz in Ihrem Verzeichnis enthält ein Feld &quot;country&quot;und Sie möchten Geschäftskalender auf Grundlage des Landes zuweisen, in dem sich der Benutzer befindet. In diesem Fall geben Sie den Feldnamen country als Wert für die Einstellung Geschäftskalenderschlüssel an. Anschließend können Sie die Geschäftskalenderschlüssel (die für das Feld country im LDAP-Ordner definierten Werte) Geschäftskalendern im Arbeitsablauf für Formulare zuordnen.

Weitere Informationen zu Geschäftskalendern, einschließlich der Zuordnung von Geschäftskalenderschlüsseln zu Geschäftskalendern, finden Sie unter [Konfigurieren von Geschäftskalendern](/help/forms/using/admin-help/configuring-business-calendars.md#configuring-business-calendars).

Begrenzen Sie den Namen auf weniger als 53 Zeichen. Ein kürzerer Name verhindert Probleme beim Anzeigen des Geschäftskalenderschlüssels auf den Seiten &quot;Process Management&quot;in Administration Console.

**Benutzer-ID**: (Obligatorisch) Benutzer-ID, mit dem sich der Benutzer anmeldet. Bei der Benutzer-ID muss die Groß-/Kleinschreibung zwar nicht beachtet werden, aber sie muss innerhalb der Domain eindeutig sein.

Verwenden Sie in Unternehmensdomänen als Benutzer-ID ein Nicht-DN-Attribut, da sich der DN eines Benutzers ändern kann, wenn er in einen anderen Teil der Organisation wechselt. Diese Einstellung hängt vom Ordnerserver ab. Für Active Directory 2003 lautet der Wert `objectGUID`, für Sun™ One lautet er `nsuniqueID` und für eDirectory `guid`.

Stellen Sie sicher, dass die Benutzer-ID eindeutig ist. Verwenden Sie keinen Benutzer, der einem gelöschten Benutzer zugewiesen wurde.

AEM Forms kann nicht zwischen Benutzerkonten aus verschiedenen Domains mit identischen Benutzer-IDs und Kennwörtern unterscheiden. Zur Vermeidung dieses Problems erstellen Sie keine Konten mit identischen Benutzer-IDs in mehreren Domains.

Bei Verwendung von SQL Server als Datenbank ist es nicht möglich, eine Benutzer-ID zu erstellen, die 255 Zeichen überschreitet.

Bei Verwendung von MySQL kann die Benutzer-ID erweiterte Zeichen enthalten. Wenn jedoch ein Vergleich zwischen zwei Zeichenfolgen wie abcde und âbcdè durchgeführt wird, werden diese als identisch betrachtet. Wenn beispielsweise bei der Synchronisierung ein neuer Benutzer zur Datenbank hinzugefügt wurde, wird ein Vergleich durchgeführt, um zu überprüfen, ob ein Benutzer mit derselben Benutzer-ID in der Datenbank vorhanden ist. Wenn Benutzer *abcde* in der Datenbank vorhanden ist, wenn der neue Benutzer *âbcdè* hinzugefügt wurde, kann der Vergleich nicht zwischen den beiden Namen unterscheiden. Es wird davon ausgegangen, dass der Benutzer in der Datenbank vorhanden ist und der neue Benutzer ignoriert und nicht hinzugefügt wird.

Vermeiden Sie das Erstellen von Benutzernamen, die mit einem Nummernzeichen (#) beginnen. Beim Ausführen von Aufgabensuchen werden für diese Benutzernamen keine Ergebnisse zurückgegeben. (Siehe [Arbeiten mit Aufgaben](/help/forms/using/admin-help/tasks.md#working-with-tasks).

**Kennwort und Kennwort bestätigen:** Kennwort, das der Benutzer zum Anmelden verwendet. Er muss mindestens acht Zeichen lang sein. Für Benutzer in einer Hybrid-Domain ist kein Kennwort erforderlich.

## Details zu einem Benutzer anzeigen {#view-details-about-a-user}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Benutzer und Gruppen“.
1. Geben Sie Informationen zur Eingrenzung der Suche an, wählen Sie in der Liste &quot;In&quot;die Option &quot;Benutzer&quot;aus und klicken Sie auf &quot;Suchen&quot;. Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
1. Klicken Sie auf den Namen des Benutzers, zu dem Details angezeigt werden sollen. Auf der Seite &quot;Benutzer bearbeiten&quot;werden Details wie die folgenden zum Benutzer angezeigt:

   * Allgemeine Kenndaten wie Name, E-Mail-Adresse, Postanschrift, Domain und Firma
   * Dem Benutzer zugewiesene Rollen
   * Gruppen, denen der Benutzer angehört

## Kennwort für einen lokalen Benutzer ändern {#change-the-password-for-a-local-user}

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Benutzer und Gruppen]**.
1. Geben Sie Informationen ein, um die Suche auf einen bestimmten Benutzer einzugrenzen, und klicken Sie auf **[!UICONTROL Suchen]**. Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
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
   >Lokale Benutzer können nicht zu Ordnergruppen hinzugefügt werden. Ordnerbenutzer können jedoch lokalen Gruppen hinzugefügt werden.

   * Um den Benutzer aus einer Gruppe zu entfernen, aktivieren Sie das Kontrollkästchen für die Gruppe, klicken auf **[!UICONTROL Löschen]** und anschließend auf **[!UICONTROL Speichern]**.


1. Um die Benutzerrollen zu bearbeiten, klicken Sie auf die **[!UICONTROL Rollenzuweisungen]** und führen Sie die folgenden Aufgaben aus:

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
>Mit AEM Forms on JEE können Benutzer des AEM Forms-Add-ons, das auf einem OSGi ausgeführt wird, auch als AEM Benutzer erkannt werden. Dies ist für Fälle erforderlich, in denen eine einmalige Anmeldung zwischen AEM Forms on JEE und AEM Forms-Add-On erforderlich ist, das auf einem OSGi ausgeführt wird (z. B. HTML Workspace). Der oben genannte Löschvorgang entfernt einen Benutzer nur aus AEM Forms on JEE. Der Benutzer wird nicht aus dem AEM Forms-Add-on gelöscht, das in der OSGi-Umgebung ausgeführt wird. Jeder Anmeldeversuch, der nach dem Löschen des Benutzers unternommen wurde (Anmeldeversuch an den AEM Forms Add-on JEE-Server oder AEM Forms Add-On in der OSGi-Umgebung), wird jedoch verweigert.

## Benutzerdefinierten Login-Fehler-Handler erstellen {#create-custom-login-error-handler}

Wenn ein Benutzer ohne die erforderlichen AEM Formulare und CQ-Berechtigungen versucht, sich bei den folgenden in CQ eingebetteten Anwendungen anzumelden, wird der Benutzer zur standardmäßigen CQ 404-Seite mit der Fehlerverfolgung weitergeleitet:

* Correspondence Management-Lösung
* Arbeitsbereich für AEM Formulare

   ***Hinweis **: Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.*

* Forms Manager
* Prozessberichterstellung

CQ bietet einen Mechanismus zum Außerkraftsetzen der standardmäßigen 404-Handler-JSP.

Weitere Informationen zum Anpassen der Seite zur Fehlerbehebung finden Sie unter [Anpassen der vom Fehler-Handler angezeigten Seiten](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/customizing-errorhandler-pages.html?lang=en) in der Adobe Experience Manager-Dokumentation.
