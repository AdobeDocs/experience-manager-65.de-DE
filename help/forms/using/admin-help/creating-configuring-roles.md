---
title: Erstellen und Konfigurieren von Rollen
seo-title: Creating and configuring roles
description: Erfahren Sie, wie Sie Benutzer und Gruppen Rollen zuweisen, die bereits Teil der User Management-Datenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.
seo-description: Learn how to associate users and groups with roles that are already part of the User Management database. You can also create, edit, and delete roles.
uuid: e8e4331d-48e1-4fa9-8f44-f885f4ab1a54
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 737fb4d1-adef-47e1-9a0d-8cddd13132cb
exl-id: b447e545-f73e-4fde-a001-86e0e1cf4a12
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '2523'
ht-degree: 54%

---

# Erstellen und Konfigurieren von Rollen{#creating-and-configuring-roles}

Auf den User Management-Webseiten können Sie Benutzer und Gruppen Rollen zuordnen, die bereits Teil der User Management-Datenbank sind. Sie können auch Rollen erstellen, bearbeiten und löschen.

User Management verfügt über zwei Arten von Rollen:

**Veränderliche Rollen**: Dieser Rollentyp kann bearbeitet und gelöscht werden, und Rollenberechtigungen können zu diesen Rollentypen hinzugefügt und aus ihnen gelöscht werden. Jede Rolle, die Sie erstellen, gilt als veränderliche Rolle. Sie können Benutzer und Gruppen hinzufügen oder entfernen, die veränderlichen Rollen zugewiesen sind.

**Unveränderliche Rollen**: Die in User Management enthaltenen Standardrollen sind unveränderliche Rollen. Diese Rollen können nicht bearbeitet oder gelöscht werden. Sie können jedoch Benutzer und Gruppen hinzufügen oder entfernen, die unveränderlichen Rollen zugewiesen sind.

Sowohl veränderliche als auch unveränderliche Rollen können auch über die AEM Forms-APIs erstellt werden.

## Standardrollen {#default-roles}

Die folgenden Standardrollen sind in der User Management-Datenbank enthalten.

**Administration-Console-Benutzer**: Kann auf die Administration-Console zugreifen.

**Programmadministrator**: Kann alle Funktionen von Workbench verwenden. Kann die Seiten „Anwendungen“ und „Dienste“ in der Administration Console verwenden, um Laufzeiteigenschaften, Endpunkte und Sicherheit von Diensten zu konfigurieren.

**AEM Forms-Administrator**: Kann alle Aufgaben für alle installierten Services ausführen.

**Sicherheitsadministrator**: Steuert User Management-Einstellungen und verwaltet Benutzer und Gruppen, die mit User Manager-Domains verbunden sind

**Service-Benutzer**: Kann alle Services anzeigen und aufrufen

**Superadministrator**: Hat Zugriff auf alle Verwaltungsfunktionen im System, einschließlich der Services

**Vertrauensadministrator**: Kann die PKI-Vertrauenseinstellungen und -Berechtigungen verwalten, die über die Seite „Trust Store-Verwaltung“ in der Administration-Console verwaltet werden

### Zusätzliche Standardrollen {#additional-default-roles}

Je nach den installierten AEM Formularkomponenten können die folgenden zusätzlichen Standardrollen enthalten sein

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
>Benutzer mit bestimmten Arten von Administratorberechtigungen können aus Sicherheitsgründen nicht auf die Workspace-Webseiten für Endbenutzer zugreifen. Da diese Seiten außerhalb einer Firewall vorhanden sein können, kann das Zulassen von Aufgaben auf Administratorebene ein Sicherheitsrisiko darstellen. Nur Benutzer mit den Berechtigungen AEM Workspace Administrator oder AEM forms Workspace User können auf die Workspace-Webseiten für Endbenutzer zugreifen.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.

## Rollen erstellen {#create-a-role}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Neue Rolle&quot;.
1. Geben Sie in das Feld &quot;Rollenname&quot;einen Namen für die Rolle ein, geben Sie optional eine Beschreibung der Rolle ein und klicken Sie auf &quot;Weiter&quot;.

   >[!NOTE]
   >
   >Bei Verwendung von MySQL können Sie nicht zwei Rollen erstellen, die denselben Namen, aber unterschiedliche erweiterte Zeichen haben. Wenn Sie beispielsweise versuchen, eine Rolle mit dem Namen &quot;abcde&quot;zu erstellen, wenn bereits eine namens &quot;âbcdè&quot;vorhanden ist, wird ein Fehler ausgegeben.

1. Klicken Sie auf Berechtigungen suchen und wählen Sie die Berechtigungen aus, die der Rolle hinzugefügt werden sollen.
1. Klicken Sie auf OK und dann auf Weiter.
1. Weisen Sie diese Rolle Benutzern und Gruppen zu:

   * Klicken Sie auf Benutzer/Gruppen suchen .
   * Geben Sie die gewünschten Suchkriterien in das Feld „Suchen“ ein.
   * Wählen Sie &quot;Name&quot;, &quot;E-Mail&quot;oder &quot;Benutzer-ID&quot;und dann &quot;Benutzer&quot;, &quot;Gruppen&quot;oder &quot;Benutzer und Gruppen&quot;aus.
   * Wählen Sie die Domain und die Anzahl der anzuzeigenden Suchergebnisse aus und klicken Sie auf „Suchen“.
   * Aktivieren Sie die Kontrollkästchen der Benutzer und Gruppen, denen diese Rolle zugewiesen werden soll, und klicken Sie auf &quot;OK&quot;.

1. Um Benutzer- und Gruppendetails anzuzeigen, wählen Sie die Entität aus.
1. Klicken Sie auf OK und dann auf Fertigstellen.

## Rollen bearbeiten {#edit-a-role}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Rollenname&quot;.

   Standardmäßig werden auf der Seite &quot;Rollenverwaltung&quot;alle Rollen in der User Management-Datenbank angezeigt. Wenn die Liste der Rollen groß ist, verwenden Sie den Suchbereich oben auf der Seite, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie auf die zu bearbeitende Rolle, bearbeiten Sie die allgemeinen Einstellungen und klicken Sie auf &quot;Speichern&quot;.
1. Um Rollenberechtigungen zu bearbeiten, klicken Sie auf die Registerkarte Berechtigungen und führen die folgenden Schritte aus:

   * Um neue Berechtigungen hinzuzufügen, klicken Sie auf &quot;Berechtigungen suchen&quot;, aktivieren die Kontrollkästchen für die hinzuzufügenden Berechtigungen, klicken auf &quot;OK&quot;und anschließend auf &quot;Speichern&quot;.
   * Um eine Berechtigung aus der Rolle zu löschen, aktivieren Sie das Kontrollkästchen für die Berechtigung, klicken auf &quot;Löschen&quot;und anschließend auf &quot;Speichern&quot;.

1. Um zu verwalten, wem die Rolle zugewiesen ist, klicken Sie auf die Registerkarte Rollenbenutzer und führen die folgenden Aufgaben aus:

   * Um die Rolle neuen Benutzern und Gruppen zuzuweisen, klicken Sie auf &quot;Benutzer/Gruppen suchen&quot;und füllen Sie die Suchinformationen aus. Aktivieren Sie das Kontrollkästchen für jeden Benutzer und jede Gruppe, dem diese Rolle zugewiesen werden soll, klicken Sie auf &quot;OK&quot;und anschließend auf &quot;Speichern&quot;.
   * Um die Rolle zu entfernen, aktivieren Sie das Kontrollkästchen der Benutzer oder Gruppen, klicken auf &quot;Zuweisung aufheben&quot;und anschließend auf &quot;Speichern&quot;.

## Rollen löschen {#delete-a-role}

Sie können alle von Ihnen erstellten Rollen löschen, jedoch nicht die standardmäßigen AEM Formulare, die im Produkt enthalten sind.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Rollenname&quot;.

   Standardmäßig werden auf der Seite &quot;Rollenverwaltung&quot;alle Rollen in der User Management-Datenbank angezeigt. Wenn die Liste der Rollen groß ist, verwenden Sie den Suchbereich oben auf der Seite, um nach einem bestimmten Rollennamen zu suchen.

1. Aktivieren Sie das Kontrollkästchen der zu löschenden Rolle und klicken Sie auf &quot;Löschen&quot;und anschließend auf &quot;OK&quot;.

## Rollen Benutzern und Gruppen zuweisen {#assign-a-role-to-users-and-groups}

1. Klicken Sie in der Administration-Console auf „Einstellungen“ > „Benutzerverwaltung“ > „Benutzer und Gruppen“.
1. Geben Sie Informationen zur Eingrenzung der Suche an und klicken Sie auf &quot;Suchen&quot;. Die Suchergebnisse werden unten auf der Seite aufgelistet. Sie können die Liste sortieren, indem Sie auf eine der Spaltenüberschriften klicken.
1. Aktivieren Sie die Kontrollkästchen neben den Benutzern und Gruppen, die einer Rolle zugeordnet werden sollen, und klicken Sie auf Rolle zuweisen .
1. Wählen Sie die Rolle aus, die dem Benutzer oder der Gruppe zugewiesen werden soll, und klicken Sie auf &quot;OK&quot;.

Sie können Rollen auch über die Seite &quot;Rollenverwaltung&quot;zuweisen.

## Bestimmen, wer einer Rolle zugewiesen ist {#determine-who-is-assigned-to-a-role}

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Rollenname&quot;.

   Standardmäßig werden auf der Seite &quot;Rollenverwaltung&quot;alle Rollen in der User Management-Datenbank angezeigt. Wenn die Liste der Rollen groß ist, verwenden Sie den Suchbereich oben auf der Seite, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie auf der Seite Rollendetails auf die Registerkarte Rollenbenutzer . Eine Liste der Benutzer und Gruppen, die direkt mit der Rolle verknüpft sind, wird angezeigt.

## Rollenberechtigungen ändern {#change-role-permissions}

Sie können die Berechtigungen für alle von Ihnen erstellten Rollen ändern. Sie können die Berechtigungen für die standardmäßigen AEM Forms-Rollen, die im Produkt enthalten sind, nicht ändern.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Rollenname&quot;.

   Standardmäßig werden auf der Seite &quot;Rollenverwaltung&quot;alle Rollen in der User Management-Datenbank angezeigt. Wenn die Liste der Rollen groß ist, verwenden Sie den Suchbereich oben auf der Seite, um nach einem bestimmten Rollennamen zu suchen.

1. Wählen Sie die Rolle aus, für die Berechtigungen angezeigt werden sollen, und klicken Sie auf die Registerkarte Berechtigungen .
1. Um diese Berechtigungen zu ändern, klicken Sie auf &quot;Berechtigungen suchen&quot;, aktivieren die Kontrollkästchen der Berechtigungen, die der Rolle hinzugefügt werden sollen, klicken Sie auf &quot;OK&quot;und klicken Sie auf &quot;Speichern&quot;.
1. Um eine Berechtigung zu löschen, wählen Sie die Berechtigung aus, klicken auf &quot;Löschen&quot;und anschließend auf &quot;Speichern&quot;.

### Berechtigungen für AEM {#aem-forms-permissions}

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

**CREATE_VERSION_PERM:** Erstellen einer Version eines Dienstes

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

**Rights Management Policy Set Create Policy:** Erstellen einer Richtlinie für einen Richtliniensatz

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

Um den Inhalt der Ressourcenansicht in Workbench anzuzeigen und Dateien zur Anzeige zu öffnen, benötigt ein Benutzer die folgenden Berechtigungen:

* Repository lesen
* Repository durchlaufen
* Dienst aufrufen
* Dienst lesen

## Einen Benutzer oder eine Gruppe aus einer Rolle entfernen {#remove-a-user-or-group-from-a-role}

Auf der Seite &quot;Rollenverwaltung&quot;können Sie Benutzer und Gruppen aus einer bestimmten Rolle entfernen. Wenn der Benutzer oder die Gruppe die Rollenzuweisung geerbt hat, können Sie die Rolle nicht auf Benutzer- oder Gruppenebene entfernen. Entfernen Sie entweder den Benutzer oder die Gruppe aus dem Vererbungsbaum oder entfernen Sie die Rolle aus dem übergeordneten Element.

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Rollenverwaltung&quot;und dann auf &quot;Rollenname&quot;.

   Standardmäßig werden auf der Seite &quot;Rollenverwaltung&quot;alle Rollen in der User Management-Datenbank angezeigt. Wenn die Liste der Rollen groß ist, verwenden Sie den Suchbereich oben auf der Seite, um nach einem bestimmten Rollennamen zu suchen.

1. Klicken Sie in der Liste der Rollen auf den Namen der zu aktualisierenden Rolle und dann auf die Registerkarte Rollenbenutzer . Eine Liste der mit der Rolle verknüpften Benutzer und Gruppen wird angezeigt.
1. Aktivieren Sie die Kontrollkästchen der Benutzer und Gruppen, die aus der Rolle entfernt werden sollen, und klicken Sie auf Zuweisung aufheben .
1. Klicken Sie auf Speichern und dann auf OK.
