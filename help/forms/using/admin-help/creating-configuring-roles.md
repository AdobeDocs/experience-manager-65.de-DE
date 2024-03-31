---
title: Erstellen und Konfigurieren von Rollen
description: Erfahren Sie, wie Sie Benutzerinnen bzw. Benutzern und Gruppen Rollen zuweisen, die bereits Teil der Benutzerverwaltungsdatenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b447e545-f73e-4fde-a001-86e0e1cf4a12
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2483'
ht-degree: 100%

---

# Erstellen und Konfigurieren von Rollen{#creating-and-configuring-roles}

Auf den Web-Seiten zur Benutzerverwaltung können Sie Benutzenden und Gruppen Rollen zuweisen, die bereits Teil der Benutzerverwaltungsdatenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.

In der Benutzerverwaltung sind zwei Rollentypen verfügbar:

**Veränderliche Rollen**: Dieser Rollentyp kann bearbeitet und gelöscht werden, und Rollenberechtigungen können zu diesen Rollentypen hinzugefügt und aus ihnen gelöscht werden. Alle von Ihnen erstellten Rollen sind veränderliche Rollen. Sie können Benutzerinnen bzw. Benutzer und Gruppen hinzufügen oder entfernen, die veränderlichen Rollen zugewiesen sind.

**Unveränderliche Rollen**: Die in User Management enthaltenen Standardrollen sind unveränderliche Rollen. Diese Rollen können nicht bearbeitet oder gelöscht werden. Sie können jedoch Benutzerinnen bzw. Benutzer und Gruppen hinzufügen oder entfernen, die unveränderlichen Rollen zugewiesen sind.

Über die AEM Forms-APIs können ebenfalls sowohl veränderliche als auch unveränderliche Rollen erstellt werden.

## Standardrollen {#default-roles}

Die folgenden Standardrollen sind in der Benutzerverwaltungsdatenbank enthalten.

**Administration-Console-Benutzer**: Kann auf die Administration-Console zugreifen.

**Programmadministrator**: Kann alle Funktionen von Workbench verwenden. Kann die Seiten „Anwendungen“ und „Dienste“ in der Administration Console verwenden, um Laufzeiteigenschaften, Endpunkte und Sicherheit von Diensten zu konfigurieren.

**AEM Forms-Administrator**: Kann alle Aufgaben für alle installierten Services ausführen.

**Sicherheitsadministrator**: Steuert User Management-Einstellungen und verwaltet Benutzer und Gruppen, die mit User Manager-Domains verbunden sind

**Service-Benutzer**: Kann alle Services anzeigen und aufrufen

**Superadministrator**: Hat Zugriff auf alle Verwaltungsfunktionen im System, einschließlich der Services

**Vertrauensadministrator**: Kann die PKI-Vertrauenseinstellungen und -Berechtigungen verwalten, die über die Seite „Trust Store-Verwaltung“ in der Administration-Console verwaltet werden

### Zusätzliche Standardrollen {#additional-default-roles}

Je nach installierten AEM Forms-Komponenten können die folgenden zusätzlichen Standardrollen vorhanden sein

**Benutzer des Dokumenten-Upload-Programms**: Kann Dokumente mithilfe von Flex Remoting hochladen.

**Forms-Administrator**: Kann Einstellungen auf der Seite „Forms“ in der Administration-Console anzeigen und ändern

**AEM Forms-Contentspace-Administrator**: Kann Einstellungen in der Administration-Console auf der Seite „Content Services“ (nicht mehr unterstützt) anzeigen und ändern

**AEM Forms-Contentspace-Benutzer**: Kann sich bei den Contentspace-Web-Seiten (nicht mehr unterstützt) anmelden

**Documentum Connector-Administrator**: Kann Einstellungen auf der Seite „Connector for EMC Documentum“ in der Administration-Console anzeigen und ändern

**AEM Forms-FileNet-Connector-Administrator**: Kann Einstellungen auf der Seite „Connector for IBM FileNet“ in der Administration-Console anzeigen und ändern

**AEM Forms-IBM-CM-Connector-Administrator**: Kann Einstellungen auf der Seite „Connector for IBM Content Manager“ in der Administration-Console anzeigen und ändern

**Rights Management-Administrator**: Führt alle Aufgaben aus, die für alle Server-Konfigurationen auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management-Endbenutzer**: Kann auf Rights Management-Web-Seiten für Endbenutzer zugreifen

**Rights Management – Benutzer einladen**: Kann Benutzer einladen

**Rights Management – Eingeladene und lokale Benutzer verwalten**: Kann Aufgaben ausführen, die zur Verwaltung aller eingeladenen und lokalen Benutzer auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management-Richtliniensatzadministrator**: Führt alle Aufgaben aus, die für alle Richtliniensätze auf den entsprechenden Rights Management-Seiten erforderlich sind

**Rights Management-Superadministrator**: Führt alle Aufgaben aus, die auf der Rights Management-Seite erforderlich sind

**AEM Forms-Workspace-Administrator**: Kann Einstellungen auf der Workspace-Seite in der Administration-Console anzeigen und ändern

***Hinweis **: Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.*

**Workspace-Benutzer**: Kann sich beim Workspace-Programm für Endbenutzer anmelden

**Ausgabe-Administrator**: Kann Einstellungen auf der Seite „Ausgabe“ in der Administration-Console anzeigen und ändern

**PDFG-Administrator**: Kann die Einstellungen auf der Seite „PDF Generator“ in der Administration-Console anzeigen und ändern

**PDFG-Benutzer**: Kann auf alle nicht verwaltungsbezogenen Funktionen von PDF Generator zugreifen

**Acrobat Reader DC Extensions-Web-Programm**: Kann das Web-Programm Acrobat Reader DC Extensions verwenden

>[!NOTE]
>
>Benutzende mit bestimmten Arten von Administratorberechtigungen dürfen aus Sicherheitsgründen nicht auf Workspace-Web-Seiten für Endbenutzende zugreifen. Da sich diese Seiten außerhalb einer Firewall befinden können, ist das Zulassen von Aufgaben auf Administratorebene möglicherweise ein Sicherheitsrisiko. Nur Benutzerinnen und Benutzer mit AEM Forms Workspace Administrator- oder AEM Forms Workspace User-Berechtigungen dürfen auf die Workspace-Web-Seiten für Endbenutzerinnen und Endbenutzer zugreifen.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

## Erstellen einer Rolle {#create-a-role}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Neue Rolle“.
1. Geben Sie im Feld „Rollenname“ einen Namen für die Rolle und optional eine Beschreibung ein. Klicken Sie danach auf „Weiter“.

   >[!NOTE]
   >
   >Wenn Sie MySQL verwenden, dürfen Sie keine Rollennamen erstellen, die sich nur durch erweiterte Zeichen unterscheiden.  Zum Beispiel führt der Versuch, die Rolle „abcde“ zu erstellen, wenn die Rolle „âbcdè“ bereits vorhanden ist, zu einem Fehler.

1. Klicken Sie auf „Berechtigungen suchen“ und wählen Sie die gewünschten Berechtigungen für die Rolle aus.
1. Klicken Sie auf „OK“ und dann auf „Weiter“.
1. So weisen Sie diese Rolle Benutzenden und Gruppen zu:

   * Klicken Sie auf „Benutzer/Gruppen suchen“.
   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie „Name“, „E-Mail“ oder „Benutzer-ID“ sowie „Benutzer“, „Gruppen“ oder „Benutzer und Gruppen“ aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie die Kontrollkästchen für die Benutzenden und Gruppen, die Sie dieser Rolle zuweisen möchten, und klicken Sie auf „OK“.

1. Wählen Sie die Entität aus, um Benutzer- und Gruppendetails anzuzeigen.
1. Klicken Sie auf „OK“ und dann auf „Beenden“.

## Bearbeiten einer Rolle {#edit-a-role}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der Benutzerverwaltungsdatenbank vorhandenen Rollen angezeigt.  Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie auf die Rolle, die Sie bearbeiten möchten, bearbeiten Sie die allgemeinen Einstellungen und klicken Sie auf „Speichern“.
1. Um die Rollenberechtigungen zu bearbeiten, klicken Sie auf die Registerkarte „Berechtigungen“ und führen die folgenden Aufgaben aus:

   * Um neue Berechtigungen hinzuzufügen, klicken Sie auf „Berechtigungen suchen“, aktivieren die Kontrollkästchen für die gewünschten Berechtigungen, klicken auf „OK“ und anschließend auf „Speichern“.
   * Um eine Berechtigung aus der Rolle zu löschen, aktivieren Sie das Kontrollkästchen für die Berechtigung, klicken auf „Löschen“ und anschließend auf „Speichern“.

1. Zum Verwalten der Rollenzuweisung klicken Sie auf die Registerkarte „Rollenbenutzer“ und führen die folgenden Aufgaben aus:

   * Um die Rolle neuen Benutzenden und Gruppen zuzuweisen, klicken Sie auf „Benutzer/Gruppen suchen“ und geben die Suchinformationen ein.  Aktivieren Sie die Kontrollkästchen für die Benutzenden bzw. Gruppen, die dieser Rolle zugewiesen werden sollen, klicken Sie auf „OK“ und anschließend auf „Speichern“.
   * Um die Rolle zu entfernen, aktivieren Sie das Kontrollkästchen für die betreffenden Benutzenden oder Gruppen, klicken auf „Zuweisung aufheben“ und anschließend auf „Speichern“.

## Löschen einer Rolle {#delete-a-role}

Sie können alle von Ihnen erstellten Rollen löschen, jedoch nicht die AEM Forms-Standardrollen, die im Produkt enthalten sind.

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der Benutzerverwaltungsdatenbank vorhandenen Rollen angezeigt.  Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Aktivieren Sie das Kontrollkästchen der zu löschenden Rolle und klicken Sie erst auf „Löschen“ und anschließend auf „OK“.

## Zuweisen einer Rolle an Benutzende und Gruppen {#assign-a-role-to-users-and-groups}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Benutzer und Gruppen“.
1. Geben Sie Informationen zum Eingrenzen der Suche ein und klicken Sie auf „Suchen“.  Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
1. Aktivieren Sie die Kontrollkästchen der Benutzenden und Gruppen, die Sie mit dieser Rolle verknüpfen möchten, und klicken Sie auf „Rolle zuweisen“.
1. Wählen Sie die Rolle aus, die Sie der Person bzw. Gruppe zuweisen möchten, und klicken Sie auf „OK“.

Die Rollenzuweisung ist auch über die Seite „Rollenverwaltung“ möglich.

## Ermitteln der einer Rolle zugewiesenen Benutzenden oder Gruppen {#determine-who-is-assigned-to-a-role}

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der Benutzerverwaltungsdatenbank vorhandenen Rollen angezeigt.  Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie auf der Seite „Rollendetails“ auf die Registerkarte „Rollenbenutzer“.  Daraufhin wird eine Liste mit Benutzenden und Gruppen angezeigt, die direkt mit der Rolle verknüpft sind.

## Ändern von Rollenberechtigungen {#change-role-permissions}

Sie können die Berechtigungen für alle Rollen ändern, die Sie erstellt haben.  Sie können die Berechtigungen für die AEM Forms-Standardrollen, die in dem Produkt enthalten sind, nicht ändern.

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der Benutzerverwaltungsdatenbank vorhandenen Rollen angezeigt.  Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Wählen Sie die Rolle aus, für die Sie Berechtigungen anzeigen möchten, und klicken Sie auf die Registerkarte „Berechtigungen“.
1. Um diese Berechtigungen zu ändern, klicken Sie auf „Berechtigungen suchen“, aktivieren die Kontrollkästchen für die zur Rolle hinzuzufügenden Berechtigungen, klicken auf „OK“ und anschließend auf „Speichern“.
1. Um eine Berechtigung zu löschen, wählen Sie die Berechtigung aus, klicken Sie auf „Löschen“ und anschließend auf „Speichern“.

### AEM Forms-Berechtigungen {#aem-forms-permissions}

**ADD_REMOVE_ENDPOINTS_PERM**: Hinzufügen, Entfernen und Ändern von Endpunkten für einen Service

**Admin Console-Anmeldung**: Administration-Console anzeigen

**Zertifikat ändern**: Ändern der Vertrauenseinstellungen eines beliebigen Zertifikats im Trust Store

**Zertifikat lesen**: Lesen eines beliebigen Zertifikats im Trust Store

**Zertifikat schreiben**: Dem Trust Store ein Zertifikat hinzufügen

**Komponenten hinzufügen**: Eine neue Komponente im System installieren

**Komponenten löschen**: Beliebige Komponenten im System löschen

**Komponente lesen**: Beliebige Komponenten im System lesen

**Contentspace-Administrator**: Berechtigung für Administrator von Contentspace (nicht mehr unterstützt)

**Contentspace Console-Anmeldung**: Berechtigung für Anmeldung bei Contentspace Console (nicht mehr unterstützt)

**Core-Systemeinstellungen steuern**: Die Einstellungen auf der Seite „Core-Systemeinstellungen“ in der Administration-Console verwalten

**CREATE_VERSION_PERM**: Erstellen einer Version eines Service

**Berechtigung ändern**: Beliebige Berechtigungen für die Signierung im Trust Store ändern

**Berechtigung lesen**: Beliebige Berechtigungen für die Signierung im Trust Store lesen

**Berechtigung schreiben**: Dem Trust Store eine Berechtigung für die Signierung hinzufügen

**CRL ändern**: Beliebige Zertifikatsperrlisten (CRLs) im Trust Store ändern

**CRL lesen**: Beliebige CRLs im Trust Store lesen

**CRL schreiben**: Dem Trust Store eine CRL hinzufügen

**Delegieren**: Eine Zugriffssteuerungsliste (ACL) für eine Ressource festlegen

**DELETE_VERSION_PERM**: Version eines Services löschen

**Dokument hochladen**: Dokumente in AEM Forms hochladen

**Domain-Steuerung**: Einstellungen für alle User Management-Domains erstellen, löschen oder ändern, einschließlich der Authentifizierungs- und Ordneranbieter

**Ereignistypen bearbeiten**: Ereignistypen bearbeiten

**Vortäuschen falscher Identitäten kontrollieren**: Identität in User Manager imitieren

**INVOKE_PERM**: Aufrufen aller Vorgänge für den Service

**LCDS-Datenmodell kontrollieren**: Datenmodelle in Data Services lesen und bereitstellen

**License Manager aktualisieren**: Lizenzinformationen aktualisieren

**MODIFY_CONFIG_PERM**: Ändern der Konfiguration eines Services

**TERM**: Ändern der Version eines Services

**PDFGAdminPermission**: PDFG-Administrator

**PDFGUserPermission**: PDFG-Benutzer

**PERM_DCTM_ADMIN**: Documentum Connector-Administrator

**PERM_FILENET_ADMIN**: FileNet-Connector-Administrator

**PERM_FORMS_ADMIN**: Forms-Administrator

**PERM_IBMCM_ADMIN**: IBM-CM-Connector-Administrator

**PERM_OUTPUT_ADMIN**: Ausgabe-Administrator

**PERM_READER_EXTENSIONS_WEB_APPLICATION**: Verwenden des Acrobat Reader DC Extensions-Web-Programms

**PERM_SP_ADMIN**: Einstellungen für SharePoint Connector verwalten

**PERM_WORKSPACE_ADMIN**: Einstellungen für Workspace verwalten

**PERM_WORKSPACE_USER**: Beim Workspace-Programm für Endbenutzer anmelden

**Prinzipalsteuerung**: Benutzer und Gruppen für alle Domains verwalten und Rollenzuweisungen für alle Benutzer und Gruppen in allen Domains verwalten

**Prozessaufzeichnung lesen/löschen**: Workflow-Überwachungsinstanzen auflisten und abrufen

**PROCESS_OWNER_PERM** Trenddaten anzeigen und Verwaltungsaktionen für einen Service ausführen, der aus einem Prozess erstellt wurde

**Lesen**: Lesen des Inhalts einer Ressource

**READ_PERM**: lesen oder einen Service anzeigen

**Einstellung erneuern**: Bestätigungen in User Management erneuern

**Repository delegieren**: Festlegen einer ACL für eine Ressource

**Repository lesen**: Inhalt einer Ressource lesen

**Repository durchlaufen**: Eine Ressource in eine Listenressourcenanforderung einschließen oder die Metadaten einer Ressource lesen

**Repository schreiben**: Repository-Metadaten und -Inhalte schreiben

**Rights Management – Richtlinieneigentümer ändern**: Richtlinieneigentümer ändern

**Anmeldung bei der Rights Management-Endbenutzerkonsole**: Anmelden bei der Rights Management-Benutzeroberfläche für Endbenutzer

**Rights Management-Verwaltungskonfiguration**: Server-Konfiguration verwalten

**Rights Management – Eingeladene und lokale Benutzer verwalten**: Eingeladene und lokale Benutzer verwalten

**Rights Management – Richtliniensätze verwalten**: Alle Richtlinien und Dokumente in einem Richtliniensatz verwalten

**Rights Management-Richtliniensatz – Koordinator hinzufügen**: Berechtigungen für Richtliniensatzkoordinatoren hinzufügen, entfernen und ändern

**Rights Management-Richtliniensatz – Richtlinie erstellen**: Richtlinie für einen Richtliniensatz erstellen

**Rights Management-Richtliniensatz – Richtlinie löschen**: Richtlinie aus einem Richtliniensatz entfernen

**Rights Management-Richtliniensatz – Richtlinie bearbeiten**: Eine Richtlinie in einem Richtliniensatz bearbeiten

**Rights Management-Richtliniensatz – Dokumentherausgeber verwalten**: Beim Erstellen von Richtliniensätzen weisen Sie Benutzern die Rolle des Dokumentherausgebers zu. Der Dokumentherausgeber ist der Benutzer, der das Dokument mit einer Richtlinie schützt.

**Rights Management-Richtliniensatz – Koordinator entfernen**: Richtliniensatzkoordinator aus einem Richtliniensatz entfernen

**Rights Management-Richtliniensatz – Dokument widerrufen**: Widerrufen des Zugriffs auf Dokumente in einem Richtliniensatz

**Rights Management-Richtliniensatz – Richtlinie wechseln**: Richtlinien für ein Dokument wechseln

**Rights Management-Richtliniensatz – Dokumentwiderruf aufheben**: Widerruf eines Dokuments aufheben

**Rights Management-Richtliniensatz – Ereignis anzeigen**: Richtlinien- und Dokumentereignisse für Richtlinien oder Dokumente in Richtliniensätzen anzeigen

**Rights Management – Server-Ereignisse anzeigen**: Suchen und Anzeigen aller Prüfereignisse

**Rollenkontrolle**: Erstellen, Löschen und Ändern von Rollen in User Management

**Service aktivieren**: Einen beliebigen Dienst starten und zum Aufrufen bereitstellen

**Service hinzufügen**: Bereitstellen eines neuen Services in der Service-Registrierung. Das schließt das Hinzufügen neuer Prozesse und Prozessvarianten ein.

**Service deaktivieren**: Alle Servsice im System beenden

**Service löschen**: Löschen eines beliebigen Services im System, einschließlich Prozesse und Prozessvarianten

**Service aufrufen**: Jeden zur Laufzeit in der Service-Registrierung verfügbaren Service aufrufen.

**Service ändern**: Ändern der Konfigurationseigenschaften eines beliebigen Services im System. Dazu gehört auch das Sperren und Entsperren eines Dienstes in der integrierten Entwicklungsumgebung (IDE) sowie das Hinzufügen oder Entfernen von Endpunkten zu bzw. von einem Dienst.

**Service lesen**: Einen beliebigen Service im System lesen. Dazu gehören alle Prozesse und Prozessvarianten.

**SERVICE_AGENT_PERM**: Daten anzeigen und mit Prozessinstanzen für einen Service interagieren, der aus einem Prozess erstellt wurde.

**SERVICE_MANAGER_PERM**: Lastenausgleich und andere Verwaltungsaktionen für einen Service ausführen, der aus einem Prozess erstellt wurde

**START_STOP_PERM**: Starten und Beenden eines Services

**SUPERVISOR_PERM**: Prozessinstanzdaten für einen Service anzeigen, der aus einem Prozess erstellt wurde

**Durchqueren**: Eine Ressource in eine Listenressourcenanforderung einbeziehen oder die Metadaten einer Ressource lesen

**Schreiben**: Schreiben von Repository-Metadaten und -Inhalten

**Dateien in Workbench öffnen**

Um den Inhalt der Ressourcenansicht in Workbench anzuzeigen und Dateien zur Anzeige zu öffnen, werden die folgenden Berechtigungen benötigt:

* Repository lesen
* Repository durchgehen
* Dienst aufrufen
* Dienst lesen

## Entfernen von Benutzenden oder Gruppen aus einer Rolle {#remove-a-user-or-group-from-a-role}

Auf der Seite „Rollenverwaltung“ können Sie Benutzende und Gruppen aus einer bestimmten Rolle entfernen. Wenn die Person oder Gruppe die Rollenzuweisung geerbt hat, können Sie die Rolle nicht auf Benutzer- oder Gruppenebene entfernen. Entfernen Sie entweder die Person oder die Gruppe aus dem Vererbungsbaum oder entfernen Sie die Rolle aus dem übergeordneten Element.

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Rollenverwaltung“ und dann auf „Rollenname“.

   Standardmäßig werden auf der Seite „Rollenverwaltung“ alle in der Benutzerverwaltungsdatenbank vorhandenen Rollen angezeigt.  Ist diese Rollenliste sehr umfangreich, können Sie den Suchbereich im oberen Teil der Seite verwenden, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie in der Rollenliste auf den Namen der zu aktualisierenden Rolle und klicken Sie dann auf die Registerkarte „Rollenbenutzer“. Eine Liste der mit der Rolle verknüpften Benutzenden und Gruppen wird angezeigt.
1. Aktivieren Sie die Kontrollkästchen der Benutzenden und Gruppen, die aus der Rolle entfernt werden sollen, und klicken Sie auf „Zuweisung aufheben“.
1. Klicken Sie auf „Speichern“ und dann auf „OK“.
