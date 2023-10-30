---
title: Importieren und Verwalten von Archiven
description: Erfahren Sie, wie Sie Archive importieren und verwalten. Archiviert Importe und verwaltet in Workbench erstellte LCAs. Sie können ein Archiv importieren, konfigurieren, verwenden und löschen.
uuid: aa1613dd-6350-49a7-9643-44365e2acdcc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b6f6463a-2ae4-43d2-8d16-cc20a954e50e
exl-id: 0c15677a-ee17-425e-a261-fb3ae8688eb2
source-git-commit: 6caf3ef4a00275f0f73be52b6a9ccba77d277f1a
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 22%

---

# Importieren und Verwalten von Archiven {#import-and-manage-archives}

Verwenden Sie die Registerkarte &quot;Archive&quot;, um in Workbench erstellte LCAs zu importieren und zu verwalten.

## Archiv importieren {#import-an-archive}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;und dann auf die Registerkarte &quot;Archive&quot;.
1. Wählen Sie Importieren.
1. Klicken Sie auf Durchsuchen , um das zu importierende Archiv zu suchen, und klicken Sie dann auf Vorschau .
1. Überprüfen Sie die Liste der Ressourcen und Objekte, die mit dem Archiv installiert werden. Stellen Sie sicher, dass keine Konflikte mit vorhandenen Ressourcen, Objekten und Dienstkonfigurationen auftreten, da keine Rückgängig-Funktion verfügbar ist.

   Wenn Sie die Dienstkonfigurationen importieren möchten, importiert AEM Formulare alle Prozesskonfigurationsdateien (Endpunkte, Sicherheitsprofile und Dienstkonfigurationsparameter), die von den Prozessen in der LCA verwendet werden.

1. Wählen Sie Importieren.
1. Überprüfen Sie die Importergebnisse und klicken Sie entweder auf Konfiguration überspringen , um den Importvorgang abzuschließen, oder auf Konfigurieren , um das Archiv zu konfigurieren.

   >[!NOTE]
   >
   >Wenn Sie auf Konfiguration überspringen klicken, können Sie das Archiv später konfigurieren.

1. Wenn Sie auf &quot;Konfigurieren&quot;klicken, wird die Seite &quot;Endpunkte konfigurieren&quot;angezeigt, auf der Sie erforderliche Änderungen vornehmen können:

   * Um einen Endpunkt umzubenennen oder seine Beschreibung zu bearbeiten, klicken Sie darauf.
   * Um einen Task Manager-Endpunkt hinzuzufügen, klicken Sie auf TaskManager hinzufügen. Weitere Informationen zu den Task Manager-Einstellungen finden Sie unter [Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints).
   * Um einen Endpunkt des Typs &quot;überwachter Ordner&quot;hinzuzufügen, klicken Sie auf &quot;WatchedFolder hinzufügen&quot;. Einzelheiten zu den Einstellungen für überwachte Ordner finden Sie im Kapitel zu den [Einstellungen für Endpunkte des Typs „Überwachter Ordner](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)“.
   * Um einen E-Mail-Endpunkt hinzuzufügen, klicken Sie auf E-Mail hinzufügen . Weitere Informationen zu den E-Mail-Einstellungen finden Sie unter [E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings).
   * Um einen EJB-Endpunkt hinzuzufügen, klicken Sie auf &quot;EJB hinzufügen&quot;und geben Sie einen Namen und eine Beschreibung für den Endpunkt an.
   * Um einen SOAP-Endpunkt hinzuzufügen, klicken Sie auf SOAP hinzufügen und geben Sie einen Namen und eine Beschreibung für den Endpunkt an.
   * Um einen Remoting-Endpunkt hinzuzufügen, klicken Sie auf Remoting hinzufügen . Weitere Informationen zu den Remoting-Einstellungen finden Sie unter [Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Um einen REST-Endpunkt hinzuzufügen, klicken Sie auf &quot;REST hinzufügen&quot;und geben Sie einen Namen und eine Beschreibung für den Endpunkt an. Beachten Sie die REST-Aufruf-URL, die auf der Seite REST-Endpunkt hinzufügen angezeigt wird.
   * Um einen Endpunkt zu entfernen, aktivieren Sie das Kontrollkästchen neben diesem und klicken Sie auf &quot;Entfernen&quot;.

1. Klicken Sie auf Weiter.
1. Wenn ein Prozess oder Dienst in der LCA über Konfigurationsparameter verfügt, wird die Seite Parameter konfigurieren angezeigt, auf der Sie die Dienstparameter konfigurieren und auf Weiter klicken.
1. Nehmen Sie auf der Seite &quot;Sicherheitsprofil konfigurieren&quot;alle erforderlichen Änderungen vor:

   * **Authentifizierung von Aufrufern erforderlich:** Diese Einstellung gibt an, ob der Dienst mit oder ohne Anmeldeinformationen aufgerufen werden kann.

     Wenn *Aufrufer müssen sich derzeit authentifizieren* angezeigt wird, muss der Aufrufer des Dienstes authentifiziert werden und der Benutzerprinzipal für diesen Aufrufer muss berechtigt sein, den Dienst aufzurufen. Andernfalls wird der Aufrufversuch verweigert. Um die Authentifizierung zu entfernen, klicken Sie auf &quot;Nicht authentifizierte Aufrufer zulassen&quot;.

     Wenn *Aufrufer müssen sich nicht authentifizieren* angezeigt wird, muss der Aufrufer des Dienstes nicht authentifiziert werden. Der Aufruf des Dienstes ist immer erfolgreich, da es keine Autorisierungsüberprüfung gibt. Klicken Sie auf &quot;Authentifizierung von Aufrufern erforderlich&quot;.

   * **Ausführen als:** Gibt die Laufzeitidentität an, die von einem Dienst verwendet wird, nachdem er aufgerufen wurde. Um diese Option zu ändern, klicken Sie auf Ändern. Wählen Sie unter folgenden Optionen:

     **Nicht angegeben:** Das Standardverhalten wird verwendet.

     **Aufrufender:** Verwendet dieselbe Identität wie der Benutzer, von dem der Dienst aufgerufen wurde.

     **System:** Führt den Dienst mit vollem Berechtigungsumfang aus. Dies ist die Standardeinstellung für Prozesse mit langer Lebensdauer.

     **Benannter Benutzer:** Ermöglicht das Ausführen des Dienstes als ein bestimmter Benutzer. Dies ist die Standardeinstellung für Prozesse mit kurzer Lebensdauer. Wenn Sie diese Option auswählen, klicken Sie auf Benutzer auswählen , um die Seite &quot;Prinzipal auswählen&quot;anzuzeigen, auf der Sie nach dem Benutzer suchen und diesen auswählen können.

   * Um dem Sicherheitsprofil einen Prinzipal hinzuzufügen, klicken Sie auf &quot;Prinzipal hinzufügen&quot;und wählen Sie den Benutzer oder die Gruppe aus, der bzw. die als Prinzipal hinzugefügt werden soll. Klicken Sie auf Weiter und wählen Sie dann die Berechtigungen aus, die Sie diesem Prinzipal zuweisen möchten:

     **INVOKE_PERM:** Aufrufen aller Vorgänge für den Dienst

     **MODIFY_CONFIG_PERM:**&#x200B;Ändern der Konfiguration eines Dienstes

     **SUPERVISOR_PERM:** Anzeigen der Prozessinstanzdaten für einen Dienst, der aus einem Prozess erstellt wurde

     **START_STOP_PERM:** Starten und Beenden eines Dienstes

     **ADD_REMOVE_ENDPOINTS_PERM:** Hinzufügen, Entfernen und Ändern von Endpunkten für einen Dienst

     **CREATE_VERSION_PERM:** Erstellen einer neuen Version des Dienstes

     **DELETE_VERSION_PERM:** Löschen einer Version des Dienstes

     **MODIFY_VERSION_PERM:**&#x200B;Ändern einer Version des Dienstes

     **READ_PERM:** Anzeigen des Dienstes

     Klicken Sie auf Abgeschlossen , um den Prinzipal dem Sicherheitsprofil hinzuzufügen.

1. Klicken Sie auf Abgeschlossen , um die Konfiguration abzuschließen.

## AEM Formulare konfigurieren, die Teil einer Archivdatei sind {#configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;und dann auf die Registerkarte &quot;Archive&quot;.
1. Wählen Sie auf der Seite Archivverwaltung die zu konfigurierende Archivdatei aus.
1. Wählen Sie auf der Seite Archiv anzeigen die hervorgehobene Archivressource aus.
1. Konfigurieren Sie die importierte Prozessarchivdatei.

## Verwenden Sie den Konfigurationsassistenten zum Konfigurieren der AEM Formulare, die Teil einer Archivdatei sind {#use-the-configuration-wizard-to-configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;und dann auf die Registerkarte &quot;Archive&quot;.
1. Klicken Sie neben der zu konfigurierenden Archivdatei auf Konfigurieren .
1. Die Seite &quot;Endpunkte konfigurieren&quot;wird angezeigt, auf der Sie erforderliche Änderungen vornehmen können:

   * Um einen Endpunkt umzubenennen oder seine Beschreibung zu bearbeiten, klicken Sie darauf.
   * Um einen Task Manager-Endpunkt hinzuzufügen, klicken Sie auf TaskManager hinzufügen. Weitere Informationen zu den Task Manager-Einstellungen finden Sie unter [Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints).
   * Um einen Endpunkt des Typs &quot;überwachter Ordner&quot;hinzuzufügen, klicken Sie auf &quot;WatchedFolder hinzufügen&quot;. Einzelheiten zu den Einstellungen für überwachte Ordner finden Sie im Kapitel zu den [Einstellungen für Endpunkte des Typs „Überwachter Ordner](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)“.
   * Um einen E-Mail-Endpunkt hinzuzufügen, klicken Sie auf E-Mail hinzufügen . Weitere Informationen zu den E-Mail-Einstellungen finden Sie unter [E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings).
   * Um einen EJB-Endpunkt hinzuzufügen, klicken Sie auf &quot;EJB hinzufügen&quot;und geben Sie einen Namen und eine Beschreibung für den Endpunkt an.
   * Um einen SOAP-Endpunkt hinzuzufügen, klicken Sie auf SOAP hinzufügen und geben Sie einen Namen und eine Beschreibung für den Endpunkt an.
   * Um einen Remoting-Endpunkt hinzuzufügen, klicken Sie auf Remoting hinzufügen . Weitere Informationen zu den Remoting-Einstellungen finden Sie unter [Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Um einen REST-Endpunkt hinzuzufügen, klicken Sie auf &quot;REST hinzufügen&quot;und geben Sie einen Namen und eine Beschreibung für den Endpunkt an. Beachten Sie die REST-Aufruf-URL, die auf der Seite REST-Endpunkt hinzufügen angezeigt wird.
   * Um einen Endpunkt zu entfernen, aktivieren Sie das Kontrollkästchen neben diesem und klicken Sie auf &quot;Entfernen&quot;.

1. Klicken Sie auf Weiter.
1. Wenn ein Prozess oder Dienst in der LCA über Konfigurationsparameter verfügt, wird die Seite Parameter konfigurieren angezeigt, auf der Sie die Dienstparameter konfigurieren und auf Weiter klicken.
1. Auf der Seite &quot;Sicherheitsprofil konfigurieren&quot;können Sie alle erforderlichen Änderungen vornehmen:

   * **Authentifizierung von Aufrufern erforderlich:** Diese Einstellung gibt an, ob der Dienst mit oder ohne Anmeldeinformationen aufgerufen werden kann.

     Wenn *Aufrufer müssen sich derzeit authentifizieren* angezeigt wird, muss der Aufrufer des Dienstes authentifiziert werden und der Benutzerprinzipal für diesen Aufrufer muss berechtigt sein, den Dienst aufzurufen. Andernfalls wird der Aufrufversuch verweigert. Um die Authentifizierung zu entfernen, klicken Sie auf &quot;Nicht authentifizierte Aufrufer zulassen&quot;.

     Wenn *Aufrufer müssen sich nicht authentifizieren* angezeigt wird, kann der Aufrufer des Dienstes authentifiziert werden oder nicht. Der Aufruf des Dienstes ist immer erfolgreich, da es keine Autorisierungsüberprüfung gibt. Klicken Sie auf &quot;Authentifizierung von Aufrufern erforderlich&quot;.

   * **Ausführen als:** Gibt die Laufzeitidentität an, die von einem Dienst verwendet wird, nachdem er aufgerufen wurde. Um diese Option zu ändern, klicken Sie auf Ändern. Wählen Sie unter folgenden Optionen:

     **Nicht angegeben:** Das Standardverhalten wird verwendet.

     **Aufrufender:** Verwendet dieselbe Identität wie der Benutzer, von dem der Dienst aufgerufen wurde.

     **System:** Führt den Dienst mit vollem Berechtigungsumfang aus. Dies ist die Standardeinstellung für Prozesse mit langer Lebensdauer.

     **Benannter Benutzer:** Ermöglicht das Ausführen des Dienstes als ein bestimmter Benutzer. Dies ist die Standardeinstellung für Prozesse mit kurzer Lebensdauer. Wenn Sie diese Option auswählen, klicken Sie auf Benutzer auswählen , um die Seite &quot;Prinzipal auswählen&quot;anzuzeigen, auf der Sie nach dem Benutzer suchen und diesen auswählen können.

   * Um dem Sicherheitsprofil einen Prinzipal hinzuzufügen, klicken Sie auf &quot;Prinzipal hinzufügen&quot;und wählen Sie den Benutzer oder die Gruppe aus, der bzw. die als Prinzipal hinzugefügt werden soll. Klicken Sie auf Weiter und wählen Sie dann die Berechtigungen aus, die Sie diesem Prinzipal zuweisen möchten:

     **INVOKE_PERM:** Aufrufen aller Vorgänge für den Dienst

     **MODIFY_CONFIG_PERM:**&#x200B;Ändern der Konfiguration eines Dienstes

     **SUPERVISOR_PERM:** Anzeigen der Prozessinstanzdaten für einen Dienst, der aus einem Prozess erstellt wurde

     **START_STOP_PERM:** Starten und Beenden eines Dienstes

     **ADD_REMOVE_ENDPOINTS_PERM:** Hinzufügen, Entfernen und Ändern von Endpunkten für einen Dienst

     **CREATE_VERSION_PERM:** Erstellen einer neuen Version des Dienstes

     **DELETE_VERSION_PERM:** Löschen einer Version des Dienstes

     **MODIFY_VERSION_PERM:**&#x200B;Ändern einer Version des Dienstes

     **READ_PERM:** Anzeigen des Dienstes

     Klicken Sie auf Abgeschlossen , um den Prinzipal dem Sicherheitsprofil hinzuzufügen.

## Archiv entfernen {#remove-an-archive}

>[!NOTE]
>
>Um ein Archiv zu entfernen, das in einem Drittanbieter-Repository (EMC Documentum Content Server, IBM FileNet Content Manager oder IBM Content Manager) gespeicherte Assets enthält, müssen Sie die Asset-Dateien auch mithilfe von Workbench aus dem Repository löschen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Archivverwaltung&quot;.
1. Aktivieren Sie auf der Seite Archivverwaltung das Kontrollkästchen für das zu entfernende Archiv und klicken Sie auf Entfernen .
