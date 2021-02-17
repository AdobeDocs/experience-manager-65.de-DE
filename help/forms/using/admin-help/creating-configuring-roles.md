---
title: Rollen erstellen und konfigurieren
seo-title: Rollen erstellen und konfigurieren
description: Erfahren Sie, wie Sie Benutzer und Gruppen Rollen zuweisen, die bereits Teil der User Management-Datenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.
seo-description: Erfahren Sie, wie Sie Benutzer und Gruppen Rollen zuweisen, die bereits Teil der User Management-Datenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.
uuid: e8e4331d-48e1-4fa9-8f44-f885f4ab1a54
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 737fb4d1-adef-47e1-9a0d-8cddd13132cb
translation-type: tm+mt
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 51%

---


# Rollen erstellen und konfigurieren{#creating-and-configuring-roles}

Auf den Webseiten von User Management können Sie Benutzer und Gruppen Rollen zuordnen, die bereits Teil der User Management-Datenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.

In User Management sind zwei Rollentypen verfügbar:

**Veränderliche Rollen:** Dieser Rollentyp kann bearbeitet und gelöscht werden. Rollenberechtigungen können hinzugefügt und aus diesen Rollentypen gelöscht werden. Alle von Ihnen erstellten Rollen sind veränderliche Rollen. Sie können Benutzer und Gruppen, die veränderlichen Rollen zugewiesen sind, hinzufügen und entfernen.

**Unveränderliche Rollen:** Die Standardrollen, die in User Management enthalten sind, sind unveränderliche Rollen. Diese Rollen können nicht bearbeitet oder gelöscht werden. Sie können jedoch Benutzer und Gruppen, die unveränderlichen Rollen zugewiesen sind, hinzufügen und entfernen.

Über die AEM Forms-APIs können ebenfalls sowohl veränderliche als auch unveränderliche Rollen erstellt werden.

## Standardrollen {#default-roles}

Die folgenden Standardrollen sind in der User Management-Datenbank enthalten:

**Administration Console-Benutzer:** Kann auf Administration Console zugreifen.

**Anwendungsadministrator:** Kann alle Funktionen von Workbench verwenden. Kann die Seiten „Anwendungen“ und „Dienste“ in der Administration Console verwenden, um Laufzeiteigenschaften, Endpunkte und Sicherheit von Diensten zu konfigurieren.

**AEM Forms-Administrator:** Kann alle Aufgaben für alle installierten Dienste ausführen.

**Sicherheitsadministrator:** Steuert User Management-Einstellungen und verwaltet Benutzer und Gruppen, die mit einer User Manager-Domäne verknüpft sind

**Dienste-Benutzer:** Kann einen Dienst aufrufen und Ansicht ausführen

**Superadministrator:** Hat Zugriff auf alle Verwaltungsfunktionen im System, einschließlich Dienste

**Vertrauensadministrator:** Kann die PKI-Vertrauenseinstellungen und PKI-Berechtigungen verwalten, die über die Seite &quot;Trust Store-Verwaltung&quot;in Administration Console verwaltet werden

### Zusätzliche Standardrollen {#additional-default-roles}

Je nach den installierten AEM Forms-Komponenten können die folgenden zusätzlichen Standardrollen vorhanden sein:

**Anwendungsbenutzer zum Hochladen von Dokumenten:** Kann Dokumente mit Flex Remoting hochladen.

**Forms-Administrator:** Kann Einstellungen in Administration Console auf der Seite &quot;Forms&quot;Ansicht und Änderung vornehmen

**AEM Forms Contentspace-Administrator:** Kann Einstellungen auf der Seite &quot;Content Services&quot;(nicht mehr unterstützt) in Administration Console Ansicht und ändern

**AEM Forms Contentspace-Benutzer:** Kann sich auf den Contentspace-Webseiten (nicht mehr unterstützt) anmelden

**Documentum Connector-Administrator:** Kann Einstellungen auf der Seite &quot;Connector für EMC Documentum&quot;in Administration Console Ansicht und ändern.

**AEM Forms FileNet Connector-Administrator: Kann Einstellungen auf der Seite &quot;Connector für IBM FileNet&quot;in Administration Console Ansicht und ändern.** 

**AEM Formulare IBM CM Connector-Administrator:** Kann Einstellungen auf der Seite &quot;Connector für IBM Content Manager&quot;in Administration Console Ansicht und ändern

**Rights Management-Administrator:** Führt alle Aufgaben aus, die für alle Serverkonfigurationen auf den entsprechenden Rights Management-Seiten erforderlich sind

**Endbenutzer des Rights Managements:** Kann auf Rights Management-Webseiten für Endbenutzer zugreifen

**Rights Management-Einladungsbenutzer:** Kann Benutzer einladen

**Rights Management eingeladene und lokale Benutzer verwalten:** Kann Aufgaben durchführen, die zum Verwalten aller eingeladenen und lokalen Benutzer auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management-Richtliniensatzadministrator:** Führt alle Aufgaben aus, die für alle Richtliniensätze auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management Super Administrator:** Führt alle erforderlichen Aufgaben auf der Seite &quot;Rights Management&quot;aus

**AEM forms Workspace-Administrator:** Kann Einstellungen auf der Seite &quot;Workspace&quot;in Administration Console Ansicht und ändern

***Hinweis **: Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.*

**Workspace-Benutzer:** Kann sich bei der Workspace-Endbenutzeranwendung anmelden

**Output-Administrator:** Kann Einstellungen auf der Seite &quot;Ausgabe&quot;in Administration Console Ansicht und ändern

**PDFG-Administrator:** Kann Einstellungen auf der Seite &quot;PDF Generator&quot;in Administration Console Ansicht und ändern

**PDFG-Benutzer:** Kann auf alle nicht administrativen Funktionen für PDF Generator zugreifen

**Acrobat Reader DC Extensions-Webanwendung:** Kann die Acrobat Reader DC Extensions-Webanwendung verwenden

>[!NOTE]
>
>Benutzer mit bestimmten Arten von Administratorberechtigungen dürfen aus Sicherheitsgründen nicht auf Workspace-Webseiten für Endbenutzer zugreifen. Da sich diese Seiten außerhalb einer Firewall befinden können, ist das Zulassen von Aufgaben auf Administratorebene möglicherweise ein Sicherheitsrisiko. Nur Benutzer mit AEM Forms Workspace Administrator- oder AEM Forms Workspace User-Berechtigungen dürfen auf die Workspace-Webseiten für Endbenutzer zugreifen.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.

## Rollen erstellen {#create-a-role}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Neue Rolle“.
1. Geben Sie im Feld „Rollenname“ einen Namen für die Rolle und optional eine Beschreibung ein. Klicken Sie danach auf „Weiter“.

   >[!NOTE]
   >
   >Wenn Sie MySQL verwenden, dürfen Sie keine Rollennamen erstellen, die sich nur durch erweiterte Zeichen unterscheiden. Der Versuch, die Rolle „abcde“ zu erstellen, wenn die Rolle „âbcdè“ bereits vorhanden ist, führt zu einer Fehlermeldung.

1. Klicken Sie auf „Berechtigungen suchen“ und wählen Sie die gewünschten Berechtigungen für die Rolle aus.
1. Klicken Sie auf „OK“ und dann auf „Weiter“.
1. Weisen Sie diese Rolle Benutzern und Gruppen zu:

   * Klicken Sie auf „Benutzer/Gruppen suchen“.
   * Geben Sie im Feld „Suchen“ die gewünschten Suchkriterien ein.
   * Wählen Sie „Name“, „E-Mail“ oder „Benutzer-ID“ sowie „Benutzer“, „Gruppen“ oder „Benutzer und Gruppen“ aus.
   * Wählen Sie die Domäne und die Anzahl der anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie die Kontrollkästchen für die Benutzer und Gruppen, die Sie dieser Rolle zuweisen möchten, und klicken Sie auf „OK“.

1. Um Benutzer- und Gruppendetails anzuzeigen, wählen Sie die Entität aus.
1. Klicken Sie auf „OK“ und dann auf „Fertig stellen“.

## Rollen bearbeiten  {#edit-a-role}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der User Management-Datenbank vorhandenen Rollen angezeigt. Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie auf die Rolle, die Sie bearbeiten möchten, bearbeiten Sie die allgemeinen Einstellungen und klicken Sie auf „Speichern“.
1. Um die Rollenberechtigungen zu bearbeiten, klicken Sie auf die Registerkarte „Berechtigungen“.

   * Um neue Berechtigungen hinzuzufügen, klicken Sie auf „Berechtigungen suchen“, aktivieren die Kontrollkästchen für die gewünschten Berechtigungen, klicken Sie auf „OK“ und anschließend auf „Speichern“.
   * Um eine Berechtigung aus der Rolle zu löschen, aktivieren Sie das Kontrollkästchen für die Berechtigung, klicken auf „Löschen“ und anschließend auf „Speichern“.

1. Zum Verwalten der Rollenzuweisung klicken Sie auf die Registerkarte „Rollenbenutzer“ und führen die folgenden Aufgaben aus:

   * Um die Rolle neuen Benutzern und Gruppen zuzuweisen, klicken Sie auf „Benutzer/Gruppen suchen“ und geben die Suchinformationen ein. Aktivieren Sie die Kontrollkästchen für die Benutzer bzw. Gruppen, die dieser Rolle zugewiesen werden sollen, klicken Sie auf „OK“ und anschließend auf „Speichern“.
   * Um die Rolle zu entfernen, aktivieren Sie das Kontrollkästchen für die betreffenden Benutzer oder Gruppen, klicken auf „Zuweisung aufheben“ und anschließend auf „Speichern“.

## Rollen löschen  {#delete-a-role}

Sie können alle von Ihnen erstellten Rollen löschen, jedoch nicht die AEM Forms-Standardrollen, die im Produkt enthalten sind.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der User Management-Datenbank vorhandenen Rollen angezeigt. Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Aktivieren Sie das Kontrollkästchen der zu löschenden Rolle und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.

## Rollen Benutzern und Gruppen zuweisen  {#assign-a-role-to-users-and-groups}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Benutzer und Gruppen“.
1. Geben Sie Informationen zum Eingrenzen der Suche ein und klicken Sie auf „Suchen“. Die Suchergebnisse werden im unteren Seitenbereich angezeigt. Sie können die Liste durch Klicken auf die Spaltenüberschriften sortieren.
1. Aktivieren Sie die Kontrollkästchen der Benutzer und Gruppen, die Sie mit dieser Rolle verknüpfen möchten, und klicken Sie auf „Rolle zuweisen“.
1. Wählen Sie die Rolle aus, die Sie dem Benutzer bzw. der Gruppe zuweisen möchten, und klicken Sie auf „OK“.

Die Rollenzuweisung ist auch über die Seite „Rollenverwaltung“ möglich.

## Die einer Rolle zugewiesenen Benutzer oder Gruppen ermitteln  {#determine-who-is-assigned-to-a-role}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der User Management-Datenbank vorhandenen Rollen angezeigt. Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie auf der Seite „Rollendetails“ auf die Registerkarte „Rollenbenutzer“. Daraufhin wird eine Liste mit Benutzern und Gruppen angezeigt, die direkt mit der Rolle verknüpft sind.

## Rollenberechtigungen ändern  {#change-role-permissions}

Sie können die Berechtigungen für alle Rollen, die Sie erstellt haben, ändern. Sie können die Berechtigungen für die AEM Forms-Standardrollen, die in dem Produkt enthalten sind, nicht ändern.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der User Management-Datenbank vorhandenen Rollen angezeigt. Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Wählen Sie die Rolle aus, für die Sie Berechtigungen anzeigen möchten, und klicken Sie auf die Registerkarte „Berechtigungen“.
1. Um diese Berechtigungen zu ändern, klicken Sie auf „Berechtigungen suchen“, aktivieren die Kontrollkästchen für die zur Rolle hinzuzufügenden Berechtigungen, klicken auf „OK“ und anschließend auf „Speichern“.
1. Um eine Berechtigung zu löschen, wählen Sie die Berechtigung aus, klicken auf „Löschen“ und anschließend auf „Speichern“.

### AEM Forms-Berechtigungen  {#aem-forms-permissions}

**hinzufügen_REMOVE_ENDPOINT_PERM:** Hinzufügen, Entfernen und Ändern von Endpunkten für einen Dienst

**Admin Console Login:** Ansicht der Verwaltungskonsole

**Zertifikat ändern:** Ändern Sie die Vertrauenseinstellungen aller Zertifikate im Trust Store

**Zertifikat gelesen: Jedes Zertifikat im Trust Store** lesen

**Zertifikat schreiben:** Hinzufügen ein Zertifikat an den Trust Store

**Komponente Hinzufügen:Neue Komponente im System** installieren

**Komponente löschen: Komponenten im System** löschen

**Komponente lesen:Komponenten im System** lesen

**Contentspace-Administrator:** Berechtigung für Contentspace-Administrator (nicht mehr unterstützt)

**Contentspace-Konsolenanmeldung:** Berechtigung für die Anmeldung bei der Contentspace-Konsole (nicht mehr unterstützt)

**Core-Einstellungssteuerung:Einstellungen auf der Seite &quot;Core-Systemeinstellungen&quot;in Administration Console** verwalten

**CREATE_VERSION_PERM:** Neue Version eines Dienstes erstellen

**Berechtigung ändern:** Unterschriftsberechtigungen im Trust Store ändern

**Berechtigung gelesen:** Signaturberechtigung im Trust Store lesen

**Berechtigung schreiben:** Hinzufügen eine Berechtigung zum Signieren im Trust Store

**Zertifikatsperrliste ändern:Zertifikatsperrliste (Certificate Revocation Liste) im Trust Store** ändern

**CRL lesen:Zertifikatsperrlisten im Trust Store** lesen

**Zertifikatsperrliste schreiben:** Hinzufügen eine Zertifikatsperrliste in den Trust Store

**Delegate:ACL für eine Ressource** festlegen

**DELETE_VERSION_PERM:Dienstversion** löschen

**Dokument-Upload:Dokumente in AEM Formularen** hochladen

**Domänensteuerung:Einstellungen für jede User Management-Domäne, einschließlich Authentifizierungs- und Ordneranbietern,** erstellen, löschen oder ändern

**Ereignistyp bearbeiten:** Zu Ereignistypen bearbeiten

**Identitäts-Impersonation-Steuerelement:Identität** imitieren in User Manager

**INVOKE_PERM:** Alle Vorgänge für einen Dienst aufrufen

**LCDS-Datenmodellsteuerung:Datenmodelle** lesen und bereitstellen in Data Services

**License Manager-Update:Lizenzinformationen** aktualisieren

**MODIFY_CONFIG_PERM:Konfiguration eines Dienstes** ändern

**Ändern** der Version eines Dienstes

**PDFGAdminPermission:** PDFG-Administrator

**PDFGUserPermission:** PDFG-Benutzer

**PERM_DCTM_ADMIN:** Documentum Connector-Administrator

**PERM_FILENET_ADMIN:** FileNet Connector-Administrator

**PERM_FORMS_ADMIN:** Forms-Administrator

**PERM_IBMCM_ADMIN:** IBM CM Connector-Administrator

**PERM_OUTPUT_ADMIN:** Output-Administrator

**PERM_READER_EXTENSIONS_WEB_APPLICATION:** Verwenden der Acrobat Reader DC Extensions-Webanwendung

**PERM_SP_ADMIN:SharePoint-Connector-Einstellungen** verwalten

**PERM_WORKSPACE_ADMIN:Workspace-Einstellungen** verwalten

**PERM_WORKSPACE_USER:** Melden Sie sich bei der Workspace-Endbenutzeranwendung an

**Prinzipalsteuerung:Benutzer und Gruppen für jede Domäne** verwalten und Rollenzuweisungen für alle Benutzer und Gruppen in jeder Domäne verwalten

**Prozessaufzeichnung lesen/löschen:** Liste und Abrufen von Workflow-Prüfinstanzen

**PROCESS_OWNER_PERM:Trenddaten zur** Ansicht und Verwaltungsaktionen für einen Dienst, der aus einem Prozess erstellt wurde

**Lesen:Inhalt einer Ressource** lesen

**READ_PERM:Dienst** lesen oder Ansicht

**Verlängerung der Bestätigung:** erneute Zusicherungen in User Management

**Repository-Delegate:ACL für eine Ressource** festlegen

**Repository lesen:Inhalt einer Ressource** lesen

**Repository durchlaufen: Eine Ressource in eine Ressourcenanforderung** einschließen oder die Metadaten einer Liste lesen

**Repository schreiben:Repository-Metadaten und -Inhalte** schreiben

**Richtlinieneigentümer für Rights Management ändern:Richtlinieneigentümer** ändern

**Rights Management-Endbenutzerkonsole - Anmeldung:** Anmelden bei der Benutzeroberfläche für Endbenutzer des Rights Managements

**Rights Management - Konfiguration verwalten:Serverkonfiguration** verwalten

**Rights Management eingeladene und lokale Benutzer verwalten:eingeladene und lokale Benutzer** verwalten

**Rights Management - Richtliniensätze verwalten: Alle Richtlinien und Dokumente in einem Richtliniensatz** verwalten

**Rights Management-Richtliniensatz Hinzufügen Koordinator:** Hinzufügen, entfernen und ändern Sie die Berechtigungen für Richtliniensatzkoordinatoren

**Rights Management-Richtliniensatz Richtlinie erstellen: Neue Richtlinie für einen Richtliniensatz** erstellen

**Richtliniensatz löschen: Richtlinie** entfernen

**Rights Management-Richtliniensatz - Richtlinie bearbeiten: Richtlinie in einem Richtliniensatz** bearbeiten

**Rights Management-Richtliniensatz Dokument Publisher verwalten:** Beim Erstellen von Richtliniensätzen weisen Sie den Benutzern die Rolle des Dokument-Herausgebers zu. Der Dokumentherausgeber ist der Benutzer, der das Dokument mit einer Richtlinie schützt.

**Rights Management-Richtliniensatz - Koordinator entfernen: Richtliniensatzkoordinator aus einem Richtliniensatz** entfernen

**Rights Management-Richtliniensatz Dokument sperren: Zugriff auf Dokumente in einem Richtliniensatz** sperren

**Rights Management Policy Set Switch Policy:Richtlinien für ein Dokument** wechseln

**Rights Management-Richtliniensatz Widerrufen des Dokuments:** Aufhebung der Sperrung eines Dokuments

**Rights Management-Richtliniensatz-Ansicht Ereignis:Ereignis für** Ansichten und Dokumente für Richtlinien oder Dokumente in einem Richtliniensatz

**Rights Management Ansicht Server-Ereignis:alle Audit-Ereignis** suchen und Ansicht

**Rollensteuerung:Rollen in User Management** erstellen, löschen und ändern

**Dienst aktivieren:** Beginn aller Dienste, die sie für den Aufruf verfügbar machen

**Dienst-Hinzufügen:** Bereitstellung eines neuen Dienstes in der Dienstregistrierung. Das schließt das Hinzufügen neuer Prozesse und Prozessvarianten ein.

**Dienst deaktivieren:Dienst im System** beenden

**Dienst löschen: Alle Dienste im System** löschen, einschließlich Prozesse und Prozessvarianten

**Dienst aufrufen:** Rufen Sie alle Dienste in der Dienstregistrierung auf, die zur Laufzeit verfügbar sind

**Dienst ändern:** Ändern Sie die Konfigurationseigenschaften eines Dienstes im System. Dazu gehört auch das Sperren und Entsperren eines Dienstes in der integrierten Entwicklungsumgebung (IDE) sowie das Hinzufügen oder Entfernen von Endpunkten zu bzw. von einem Dienst.

**Dienst lesen:Alle Dienste im System** lesen. Dazu gehören alle Prozesse und Prozessvarianten.

**SERVICE_AGENT_PERM:** Ansicht-Daten und Interaktion mit Prozessinstanzen für einen Dienst, der aus einem Prozess erstellt wurde

**SERVICE_MANAGER_PERM:** Lastenausgleich und andere Verwaltungsaktionen für einen Dienst durchführen, der aus einem Prozess erstellt wurde

**Beginn_STOP_PERM:** Beginn oder Beenden eines Dienstes

**SUPERVISOR_PERM:Prozessinstanzdaten** für einen Dienst, der aus einem Prozess erstellt wurde

**Umgekehrt:Eine Ressource in eine Ressourcenanforderung** einschließen oder Metadaten einer Liste lesen

**Schreiben:Repository-Metadaten und -Inhalte** schreiben

**Dateien in Workbench öffnen**

Damit ein Benutzer die Inhalte der Ressourcenansicht in Workbench anzeigen und Dateien zum Anzeigen öffnen kann, muss der Benutzer über die folgenden Berechtigungen verfügen:

* Repository lesen
* Repository durchgehen
* Dienst aufrufen
* Dienst lesen

## Benutzer und Gruppen aus einer Rolle entfernen  {#remove-a-user-or-group-from-a-role}

Auf der Seite „Rollenverwaltung“ können Sie Benutzer und Gruppen aus einer bestimmten Rolle entfernen. Hat der Benutzer bzw. die Gruppe die Rollenzuweisung geerbt, kann die Rolle nicht auf Benutzer- bzw. Gruppenebene entfernt werden. Löschen Sie den Benutzer bzw. die Gruppe dann entweder aus der Vererbungsstruktur oder entfernen Sie die Rolle aus der übergeordneten Entität.

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der User Management-Datenbank vorhandenen Rollen angezeigt. Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie in der Rollenliste auf den Namen der zu aktualisierenden Rolle und klicken Sie dann auf die Registerkarte „Rollenbenutzer“. Daraufhin wird eine Liste mit Benutzern und Gruppen angezeigt, die mit der Rolle verknüpft sind.
1. Aktivieren Sie die Kontrollkästchen der Benutzer und Gruppen, die Sie aus der Rolle entfernen möchten, und klicken Sie auf „Zuweisung aufheben“.
1. Klicken Sie auf „Speichern“ und dann auf „OK“.

