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
exl-id: b447e545-f73e-4fde-a001-86e0e1cf4a12
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 51%

---

# Rollen erstellen und konfigurieren{#creating-and-configuring-roles}

Auf den Webseiten von User Management können Sie Benutzer und Gruppen Rollen zuordnen, die bereits Teil der User Management-Datenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.

In User Management sind zwei Rollentypen verfügbar:

**Veränderliche Rollen:** Dieser Rollentyp kann bearbeitet und gelöscht werden. Außerdem können Rollenberechtigungen hinzugefügt und aus diesen Rollentypen gelöscht werden. Alle von Ihnen erstellten Rollen sind veränderliche Rollen. Sie können Benutzer und Gruppen, die veränderlichen Rollen zugewiesen sind, hinzufügen und entfernen.

**Unveränderliche Rollen:** Die Standardrollen, die in User Management enthalten sind, sind unveränderliche Rollen. Diese Rollen können nicht bearbeitet oder gelöscht werden. Sie können jedoch Benutzer und Gruppen, die unveränderlichen Rollen zugewiesen sind, hinzufügen und entfernen.

Über die AEM Forms-APIs können ebenfalls sowohl veränderliche als auch unveränderliche Rollen erstellt werden.

## Standardrollen {#default-roles}

Die folgenden Standardrollen sind in der User Management-Datenbank enthalten:

**Administration Console-Benutzer:**  Kann auf Administration Console zugreifen.

**Anwendungsadministrator:** Kann alle Funktionen von Workbench verwenden. Kann die Seiten „Anwendungen“ und „Dienste“ in der Administration Console verwenden, um Laufzeiteigenschaften, Endpunkte und Sicherheit von Diensten zu konfigurieren.

**AEM Forms-Administrator:** Kann alle Aufgaben für alle installierten Dienste ausführen.

**Sicherheitsadministrator:** Steuert die User Management-Einstellungen und verwaltet Benutzer und Gruppen, die mit einer User Manager-Domäne verknüpft sind.

**Dienstbenutzer:** Kann jeden Dienst anzeigen und aufrufen

**Superadministrator:** Hat Zugriff auf alle Verwaltungsfunktionen im System, einschließlich Dienste

**Trust Administrator:** Kann die auf der Seite &quot;Trust Store-Verwaltung&quot;in Administration Console verwalteten PKI-Vertrauenseinstellungen und PKI-Berechtigungen verwalten.

### Zusätzliche Standardrollen {#additional-default-roles}

Je nach den installierten AEM Forms-Komponenten können die folgenden zusätzlichen Standardrollen vorhanden sein:

**Document Upload Application User:**  Kann Dokumente mit Flex Remoting hochladen.

**Forms-Administrator:** Kann Einstellungen in Administration Console auf der Seite &quot;Forms&quot;anzeigen und ändern.

**AEM Forms Contentspace-Administrator:** Kann Einstellungen auf der Seite &quot;Content Services&quot;(nicht mehr unterstützt) in Administration Console anzeigen und ändern.

**AEM forms Contentspace-Benutzer:** Kann sich bei den Contentspace-Webseiten (nicht mehr unterstützt) anmelden

**Documentum Connector-Administrator:** Kann Einstellungen auf der Seite &quot;Connector für EMC Documentum&quot;in Administration Console anzeigen und ändern.

**AEM FileNet Connector-Administrator:**  Kann Einstellungen auf der Seite &quot;Connector für IBM FileNet&quot;in Administration Console anzeigen und ändern.

**AEM forms IBM CM Connector Administrator:**  Kann Einstellungen auf der Seite &quot;Connector für IBM Content Manager&quot;in Administration Console anzeigen und ändern.

**Rights Management-Administrator:** Führt alle Aufgaben aus, die für alle Serverkonfigurationen auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management-Endbenutzer:** Kann auf Rights Management-Webseiten für Endbenutzer zugreifen

**Einladungs-Benutzer für Rights Management:** Kann Benutzer einladen

**Rights Management Eingeladene und lokale Benutzer verwalten:**  Kann Aufgaben durchführen, die zur Verwaltung aller eingeladenen und lokalen Benutzer auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management-Richtliniensatzadministrator:** Führt alle Aufgaben aus, die für alle Richtliniensätze auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management Super Administrator:** Führt alle erforderlichen Aufgaben auf der Rights Management-Seite aus.

**AEM forms Workspace-Administrator:** Kann Einstellungen auf der Workspace-Seite in Administration Console anzeigen und ändern.

***Hinweis **: Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.*

**Workspace-Benutzer:** Kann sich bei der Workspace-Endbenutzeranwendung anmelden

**Output Administrator:** Kann Einstellungen auf der Output-Seite in Administration Console anzeigen und ändern.

**PDFG-Administrator:** Kann Einstellungen auf der Seite &quot;PDF Generator&quot;in Administration Console anzeigen und ändern.

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

**ADD_REMOVE_ENDPOINT_PERM:** Hinzufügen, Entfernen und Ändern von Endpunkten für einen Dienst

**Admin Console Login:** Administration Console anzeigen

**Zertifikat ändern:** Ändern Sie die Vertrauenseinstellungen aller Zertifikate im Trust Store.

**Zertifikat lesen:** Jedes Zertifikat im Trust Store lesen

**Zertifikat schreiben:** Fügen Sie dem Trust Store ein Zertifikat hinzu.

**Komponente hinzufügen:** Installieren Sie eine neue Komponente im System

**Komponenten löschen:** Löschen von Komponenten im System

**Komponente lesen:** Beliebige Komponente im System lesen

**Contentspace-Administrator:** Berechtigung für Contentspace-Administrator (nicht mehr unterstützt)

**Contentspace Console-Anmeldung:** Berechtigung für die Anmeldung bei der Contentspace Console (nicht mehr unterstützt)

**Core Settings Control:** Verwalten Sie die Einstellungen auf der Seite &quot;Core-Systemeinstellungen&quot;in Administration Console.

**CREATE_VERSION_PERM:** Erstellen einer neuen Version eines Dienstes

**Berechtigungen ändern:** Ändern Sie alle Berechtigungen zum Signieren im Trust Store.

**Berechtigung lesen:** Beliebige Berechtigung zum Signieren im Trust Store lesen

**Berechtigung schreiben:** Fügen Sie dem Trust Store eine Berechtigung zum Signieren hinzu.

**CRL-Änderung:** Ändern Sie alle Zertifikatsperrlisten (CRL) im Trust Store.

**CRL lesen:** Beliebige Zertifikatsperrliste im Trust Store lesen

**CRL schreiben:** Fügen Sie dem Trust Store eine Zertifikatsperrliste hinzu.

**Delegieren:** Einrichten einer ACL für eine Ressource

**DELETE_VERSION_PERM:** Löschen einer Dienstversion

**Dokument-Upload:** Hochladen von Dokumenten in AEM Formularen

**Domänensteuerung:** Erstellen, Löschen oder Ändern von Einstellungen für jede User Management-Domäne, einschließlich Authentifizierung und Ordneranbietern

**Ereignistyp Bearbeiten:** Bearbeiten auf Ereignistypen

**Identitäts-Identitätssteuerung:** Identitätswechsel in User Manager

**INVOKE_PERM:** Aufrufen aller Vorgänge für einen Dienst

**LCDS-Datenmodellsteuerung:** Datenmodelle in Data Services lesen und bereitstellen

**License Manager-Update:** Lizenzinformationen aktualisieren

**MODIFY_CONFIG_PERM:** Ändern der Konfiguration eines Dienstes

**** Ändern der Version eines Dienstes

**PDFGAdminPermission:** PDFG-Administrator

**PDFGUserPermission:** PDFG-Benutzer

**PERM_DCTM_ADMIN:** Documentum Connector-Administrator

**PERM_FILENET_ADMIN:** FileNet Connector-Administrator

**PERM_FORMS_ADMIN:** Forms-Administrator

**PERM_IBMCM_ADMIN:** IBM CM Connector-Administrator

**PERM_OUTPUT_ADMIN:** Output-Administrator

**PERM_READER_EXTENSIONS_WEB_APPLICATION:** Verwenden der Acrobat Reader DC Extensions-Webanwendung

**PERM_SP_ADMIN:** SharePoint-Connector-Einstellungen verwalten

**PERM_WORKSPACE_ADMIN:** Workspace-Einstellungen verwalten

**PERM_WORKSPACE_USER:** Melden Sie sich bei der Workspace-Endbenutzeranwendung an

**Prinzipalsteuerung:** Verwalten Sie Benutzer und Gruppen für jede Domäne und verwalten Sie die Rollenzuweisungen für alle Benutzer und Gruppen in jeder Domäne

**Prozessaufzeichnung lesen/löschen:** Auflisten und Abrufen von Workflow-Prüfinstanzen

**PROCESS_OWNER_PERM:** Trenddaten anzeigen und Verwaltungsaktionen für einen Dienst ausführen, der aus einem Prozess erstellt wurde

**Lesen:** Lesen des Inhalts einer Ressource

**READ_PERM:** Dienst lesen oder anzeigen

**Assertion erneuern:** Verlängern Sie Zusicherungen in User Management

**Repository-Delegate:** Eine ACL für eine Ressource festlegen

**Repository lesen:** Lesen des Inhalts einer Ressource

**Repository-Verlauf:** Fügen Sie eine Ressource in eine Listenressourcenanforderung ein oder lesen Sie die Metadaten einer Ressource

**Repository schreiben:** Repository-Metadaten und -Inhalte schreiben

**Rights Management Change Policy Owner:** Ändern des Richtlinieneigentümers

**Anmeldung bei der Rights Management-Endbenutzerkonsole:** Melden Sie sich bei der Rights Management-Endbenutzeroberfläche an

**Rights Management-Verwaltungskonfiguration:** Serverkonfiguration verwalten

**Rights Management Eingeladene und lokale Benutzer verwalten:** Eingeladene und lokale Benutzer verwalten

**Rights Management Richtliniensätze verwalten:** Verwalten Sie alle Richtlinien und Dokumente innerhalb eines Richtliniensatzes.

**Rights Management Policy Set - Koordinator hinzufügen:** Berechtigungen für Richtliniensatzkoordinatoren hinzufügen, entfernen und ändern

**Rights Management-Richtliniensatz Richtlinie erstellen:** Erstellen Sie eine neue Richtlinie für einen Richtliniensatz

**Rights Management-Richtliniensatz Richtlinie löschen:** Entfernen Sie eine Richtlinie aus einem Richtliniensatz

**Rights Management-Richtliniensatz Richtlinie bearbeiten:** Bearbeiten einer Richtlinie in einem Richtliniensatz

**Rights Management-Richtliniensatz Dokumentherausgeber verwalten:** Beim Erstellen von Richtliniensätzen weisen Sie Benutzern die Rolle des Dokumentherausgebers zu. Der Dokumentherausgeber ist der Benutzer, der das Dokument mit einer Richtlinie schützt.

**Richtliniensatz Rights Management entfernen Koordinator:** Entfernen Sie einen Richtliniensatzkoordinator aus einem Richtliniensatz

**Rights Management Policy Set Revoke Document:** Sperren des Zugriffs auf Dokumente in einem Richtliniensatz

**Rights Management Policy Set Switch Policy:** Richtlinien für ein Dokument wechseln

**DokumentRichtliniensatz Dokumentsperren:** Dokumentsperrung aufheben

**Rights Management Policy Set View Event:** Anzeigen von Richtlinien- und Dokumentereignissen für Richtlinien oder Dokumente in einem Richtliniensatz

**Rights Management View Server Events:** Suchen und Anzeigen aller Prüfereignisse

**Rollensteuerung:** Erstellen, Löschen und Ändern von Rollen in User Management

**Dienst aktivieren:** Starten Sie einen beliebigen Dienst, damit er für den Aufruf verfügbar wird.

**Dienst hinzufügen:** Stellen Sie einen neuen Dienst in der Dienstregistrierung bereit. Das schließt das Hinzufügen neuer Prozesse und Prozessvarianten ein.

**Dienst deaktivieren:** Alle Dienste im System beenden

**Löschen von Diensten:**  Löschen Sie alle Dienste im System, einschließlich Prozessen und Prozessvarianten

**Dienstaufruf:**  Rufen Sie alle Dienste in der Dienstregistrierung auf, die zur Laufzeit verfügbar sind

**Dienst ändern:** Ändern Sie die Konfigurationseigenschaften eines Dienstes im System. Dazu gehört auch das Sperren und Entsperren eines Dienstes in der integrierten Entwicklungsumgebung (IDE) sowie das Hinzufügen oder Entfernen von Endpunkten zu bzw. von einem Dienst.

**Dienst lesen:** Alle Dienste im System lesen. Dazu gehören alle Prozesse und Prozessvarianten.

**SERVICE_AGENT_PERM:** Daten anzeigen und mit Prozessinstanzen für einen Dienst interagieren, der aus einem Prozess erstellt wurde

**SERVICE_MANAGER_PERM:** Durchführen von Lastenausgleich und anderen Verwaltungsaktionen für einen Dienst, der aus einem Prozess erstellt wurde

**START_STOP_PERM:** Starten oder Beenden eines Dienstes

**SUPERVISOR_PERM:** Prozessinstanzdaten für einen Dienst anzeigen, der aus einem Prozess erstellt wurde

**Durchlaufen:** Eine Ressource in eine Ressourcenanforderung für eine Liste einschließen oder die Metadaten einer Ressource lesen

**Schreiben:** Repository-Metadaten und -Inhalte schreiben

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
