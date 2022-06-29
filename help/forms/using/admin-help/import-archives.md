---
title: Archive importieren und verwalten
seo-title: Import and manage archives
description: Erfahren Sie, wie Sie Archive importieren und verwalten.
seo-description: Learn how to import and manage archives.
uuid: aa1613dd-6350-49a7-9643-44365e2acdcc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b6f6463a-2ae4-43d2-8d16-cc20a954e50e
exl-id: 0c15677a-ee17-425e-a261-fb3ae8688eb2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1454'
ht-degree: 100%

---

# Archive importieren und verwalten {#import-and-manage-archives}

Verwenden Sie die Registerkarte „Archive“, um LCAs, die in Workbench erstellt wurden, zu importieren und zu verwalten.

## Ein Archiv importieren {#import-an-archive}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“ und klicken Sie dann auf die Registerkarte „Archive“.
1. Wählen Sie Importieren.
1. Klicken Sie auf „Durchsuchen“, um das zu importierende Archiv auszuwählen, und klicken Sie dann auf „Vorschau“.
1. Prüfen Sie die Liste der Ressourcen und Objekte, die mit dem Archiv installiert werden. Stellen Sie sicher, dass keine Konflikte mit vorhandenen Ressourcen, Objekten und Dienstkonfigurationen vorliegen, weil es keine Möglichkeit gibt, den Vorgang rückgängig zu machen.

   Wenn Sie sich für den Import der Dienstkonfigurationen entscheiden, importiert AEM Forms alle Prozesskonfigurationsdateien (Endpunkte, Sicherheitsprofile und Dienstkonfigurationsparameter), die von den Prozessen im LifeCycle-Archiv (LCA) verwendet werden.

1. Wählen Sie Importieren.
1. Überprüfen Sie die Importergebnisse und klicken Sie entweder auf „Konfiguration überspringen“, um den Importprozess fertig zu stellen, oder klicken Sie auf Konfigurieren, um das Archiv zu konfigurieren.

   >[!NOTE]
   >
   >Wenn Sie auf „Konfiguration überspringen“ klicken, können Sie das Archiv später immer noch konfigurieren.

1. Wenn Sie auf „Konfigurieren“ klicken, wird die Seite zum Konfigurieren von Endpunkten angezeigt, auf der Sie alle erforderlichen Änderungen vornehmen können:

   * Zum Umbenennen eines Endpunktes oder zum Bearbeiten seiner Beschreibung klicken Sie darauf.
   * Zum Hinzufügen eines Task Manager-Endpunktes klicken Sie auf „Task Manager hinzufügen“. Einzelheiten zu den Task Manager-Einstellungen finden Sie unter „[Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)“.
   * Zum Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ klicken Sie auf „WatchedFolder hinzufügen“. Einzelheiten zu den Einstellungen für überwachte Ordner finden Sie im Kapitel zu den [Einstellungen für Endpunkte des Typs „Überwachter Ordner](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)“.
   * Zum Hinzufügen eines E-Mail-Endpunktes klicken Sie auf „E-Mail hinzufügen“. Weitere Informationen zu E-Mail-Einstellungen finden Sie unter [E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings).
   * Zum Hinzufügen eines EJB-Endpunktes klicken Sie auf „EJB hinzufügen“ und geben einen Namen und eine Beschreibung für den Endpunkt ein.
   * Zum Hinzufügen eines SOAP-Endpunktes klicken Sie auf „SOAP hinzufügen“ und geben einen Namen und eine Beschreibung für den Endpunkt ein.
   * Zum Hinzufügen eines Remoting-Endpunktes klicken Sie auf „Remoting hinzufügen“. Einzelheiten zu den Remoting-Einstellungen finden Sie unter [Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Zum Hinzufügen eines REST-Endpunktes klicken Sie auf „REST hinzufügen“ und geben einen Namen und eine Beschreibung für den Endpunkt ein. Beachten Sie die REST-Aufruf-URL, die auf der Seite „REST-Endpunkt hinzufügen“ angezeigt wird.
   * Aktivieren Sie zum Entfernen eines Endpunktes das Kontrollkästchen neben diesem und klicken Sie auf „Entfernen“.

1. Klicken Sie auf Weiter.
1. Wenn ein Prozess oder Dienst im LCA über Konfigurationsparameter verfügt, wird eine Seite zum Konfigurieren der Parameter angezeigt, auf der Sie die Dienstparameter konfigurieren können. Im Anschluss klicken Sie dann auf „Weiter“.
1. Auf der Seite zum Konfigurieren des Sicherheitsprofils können Sie alle erforderlichen Änderungen vornehmen:

   * **Authentifizierung von Aufrufern erforderlich:** Diese Einstellung zeigt an, ob der Dienst mit oder ohne Anmeldeinformationen aufgerufen werden kann.

      Wenn *Aufrufer müssen sich zurzeit authentifizieren* angezeigt wird, muss der Aufrufer des Dienstes authentifiziert werden und der Benutzerprinzipal für diesen Aufrufer muss zum Aufrufen des Dienstes berechtigt sein. Andernfalls wird der Aufrufversuch verweigert. Klicken Sie auf „Nicht authentifizierte Aufrufer zulassen“, um den Zwang zur Authentifizierung aufzuheben.

      Wenn *Aufrufer müssen sich nicht authentifizieren* angezeigt wird, muss der Aufrufer des Dienstes nicht authentifiziert sein. Das Aufrufen des Dienstes ist immer erfolgreich, da die Authentifizierung nicht überprüft wird. Klicken Sie auf „Authentifizierung von Aufrufern erforderlich“, um die Authentifizierung zu erzwingen.

   * **Ausführen als:** Definiert die von einem Dienst verwendete Laufzeitidentität, nachdem er aufgerufen wurde. Klicken Sie zum Ändern dieser Option auf „Ändern“. Wählen Sie unter folgenden Optionen:

      **Nicht angegeben:** Das Standardverhalten wird verwendet.

      **Aufrufender:** Verwendet dieselbe Identität wie der Benutzer, von dem der Dienst aufgerufen wurde.

      **System:** Führt den Dienst mit vollem Berechtigungsumfang aus. Dies ist die Standardeinstellung für Prozesse mit langer Lebensdauer.

      **Benannter Benutzer:** Ermöglicht das Ausführen des Dienstes als ein bestimmter Benutzer. Dies ist die Standardeinstellung für Prozesse mit kurzer Lebensdauer. Wenn Sie diese Option aktivieren, klicken Sie auf „Benutzer auswählen“, um die Seite „Prinzipal auswählen“ anzuzeigen, auf der Sie nach dem Benutzer suchen und ihn auswählen können.

   * Um dem Sicherheitsprofil einen Prinzipal hinzuzufügen, klicken Sie auf „Prinzipal hinzufügen“ und wählen dann den Benutzer oder die Gruppe aus, der bzw. die als Prinzipal hinzugefügt werden soll. Klicken Sie auf „Weiter“ und wählen Sie die Berechtigungen aus, die diesem Prinzipal zugewiesen werden sollen:

      **INVOKE_PERM:** Aufrufen aller Vorgänge für den Dienst

      **MODIFY_CONFIG_PERM:**&#x200B;Ändern der Konfiguration eines Dienstes

      **SUPERVISOR_PERM:** Anzeigen der Prozessinstanzdaten für einen Dienst, der aus einem Prozess erstellt wurde

      **START_STOP_PERM:** Starten und Beenden eines Dienstes

      **ADD_REMOVE_ENDPOINTS_PERM:** Hinzufügen, Entfernen und Ändern von Endpunkten für einen Dienst

      **CREATE_VERSION_PERM:** Erstellen einer neuen Version des Dienstes

      **DELETE_VERSION_PERM:** Löschen einer Version des Dienstes

      **MODIFY_VERSION_PERM:**&#x200B;Ändern einer Version des Dienstes

      **READ_PERM:** Anzeigen des Dienstes

      Klicken Sie auf „Fertig gestellt“, um den Prinzipal dem Sicherheitsprofil hinzuzufügen.

1. Klicken Sie auf „Fertig stellen“, um die Konfiguration abzuschließen.

## Konfigurieren Sie die AEM Forms, die Teil von Archivdateien sind. {#configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“ und klicken Sie dann auf die Registerkarte „Archive“.
1. Wählen Sie auf der Seite „Archivverwaltung“ die zu konfigurierende Archivdatei aus.
1. Wählen Sie auf der Seite „Archiv anzeigen“ die hervorgehobene Archivressource aus.
1. Konfigurieren Sie die importierte Prozessarchivdatei.

## Den Konfigurationsassistenten zum Konfigurieren die AEM Forms, die Teil von Archivdateien sind, verwenden {#use-the-configuration-wizard-to-configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“ und klicken Sie dann auf die Registerkarte „Archive“.
1. Klicken Sie zum Konfigurieren neben der Archivdatei auf „Konfigurieren“.
1. Die Seite zum Konfigurieren von Endpunkten wird angezeigt, auf der Sie alle erforderlichen Änderungen vornehmen können:

   * Zum Umbenennen eines Endpunktes oder zum Bearbeiten seiner Beschreibung klicken Sie darauf.
   * Zum Hinzufügen eines Task Manager-Endpunktes klicken Sie auf „Task Manager hinzufügen“. Einzelheiten zu den Task Manager-Einstellungen finden Sie unter „[Task Manager-Endpunkte konfigurieren](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)“.
   * Zum Hinzufügen eines Endpunkts vom Typ „Überwachter Ordner“ klicken Sie auf „WatchedFolder hinzufügen“. Einzelheiten zu den Einstellungen für überwachte Ordner finden Sie im Kapitel zu den [Einstellungen für Endpunkte des Typs „Überwachter Ordner](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)“.
   * Zum Hinzufügen eines E-Mail-Endpunktes klicken Sie auf „E-Mail hinzufügen“. Weitere Informationen zu E-Mail-Einstellungen finden Sie unter [E-Mail-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings).
   * Zum Hinzufügen eines EJB-Endpunktes klicken Sie auf „EJB hinzufügen“ und geben einen Namen und eine Beschreibung für den Endpunkt ein.
   * Zum Hinzufügen eines SOAP-Endpunktes klicken Sie auf „SOAP hinzufügen“ und geben einen Namen und eine Beschreibung für den Endpunkt ein.
   * Zum Hinzufügen eines Remoting-Endpunktes klicken Sie auf „Remoting hinzufügen“. Einzelheiten zu den Remoting-Einstellungen finden Sie unter [Remoting-Endpunkteinstellungen](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Zum Hinzufügen eines REST-Endpunktes klicken Sie auf „REST hinzufügen“ und geben einen Namen und eine Beschreibung für den Endpunkt ein. Beachten Sie die REST-Aufruf-URL, die auf der Seite „REST-Endpunkt hinzufügen“ angezeigt wird.
   * Aktivieren Sie zum Entfernen eines Endpunktes das Kontrollkästchen neben diesem und klicken Sie auf „Entfernen“.

1. Klicken Sie auf Weiter.
1. Wenn ein Prozess oder Dienst im LCA über Konfigurationsparameter verfügt, wird eine Seite zum Konfigurieren der Parameter angezeigt, auf der Sie die Dienstparameter konfigurieren können. Im Anschluss klicken Sie dann auf „Weiter“.
1. Auf der Seite zum Konfigurieren des Sicherheitsprofils können Sie alle erforderlichen Änderungen vornehmen:

   * **Authentifizierung von Aufrufern erforderlich:** Diese Einstellung zeigt an, ob der Dienst mit oder ohne Anmeldeinformationen aufgerufen werden kann.

      Wenn *Aufrufer müssen sich zurzeit authentifizieren* angezeigt wird, muss der Aufrufer des Dienstes authentifiziert werden und der Benutzerprinzipal für diesen Aufrufer muss zum Aufrufen des Dienstes berechtigt sein. Andernfalls wird der Aufrufversuch verweigert. Klicken Sie auf „Nicht authentifizierte Aufrufer zulassen“, um den Zwang zur Authentifizierung aufzuheben.

      Wenn *Aufrufer müssen sich nicht authentifizieren* angezeigt wird, kann der Aufrufer des Dienstes authentifiziert sein, muss es aber nicht. Das Aufrufen des Dienstes ist immer erfolgreich, da die Authentifizierung nicht überprüft wird. Klicken Sie auf „Authentifizierung von Aufrufern erforderlich“, um die Authentifizierung zu erzwingen.

   * **Ausführen als:** Definiert die von einem Dienst verwendete Laufzeitidentität, nachdem er aufgerufen wurde. Klicken Sie zum Ändern dieser Option auf „Ändern“. Wählen Sie unter folgenden Optionen:

      **Nicht angegeben:** Das Standardverhalten wird verwendet.

      **Aufrufender:** Verwendet dieselbe Identität wie der Benutzer, von dem der Dienst aufgerufen wurde.

      **System:** Führt den Dienst mit vollem Berechtigungsumfang aus. Dies ist die Standardeinstellung für Prozesse mit langer Lebensdauer.

      **Benannter Benutzer:** Ermöglicht das Ausführen des Dienstes als ein bestimmter Benutzer. Dies ist die Standardeinstellung für Prozesse mit kurzer Lebensdauer. Wenn Sie diese Option aktivieren, klicken Sie auf „Benutzer auswählen“, um die Seite „Prinzipal auswählen“ anzuzeigen, auf der Sie nach dem Benutzer suchen und ihn auswählen können.

   * Um dem Sicherheitsprofil einen Prinzipal hinzuzufügen, klicken Sie auf „Prinzipal hinzufügen“ und wählen dann den Benutzer oder die Gruppe aus, der bzw. die als Prinzipal hinzugefügt werden soll. Klicken Sie auf „Weiter“ und wählen Sie die Berechtigungen aus, die diesem Prinzipal zugewiesen werden sollen:

      **INVOKE_PERM:** Aufrufen aller Vorgänge für den Dienst

      **MODIFY_CONFIG_PERM:**&#x200B;Ändern der Konfiguration eines Dienstes

      **SUPERVISOR_PERM:** Anzeigen der Prozessinstanzdaten für einen Dienst, der aus einem Prozess erstellt wurde

      **START_STOP_PERM:** Starten und Beenden eines Dienstes

      **ADD_REMOVE_ENDPOINTS_PERM:** Hinzufügen, Entfernen und Ändern von Endpunkten für einen Dienst

      **CREATE_VERSION_PERM:** Erstellen einer neuen Version des Dienstes

      **DELETE_VERSION_PERM:** Löschen einer Version des Dienstes

      **MODIFY_VERSION_PERM:**&#x200B;Ändern einer Version des Dienstes

      **READ_PERM:** Anzeigen des Dienstes

      Klicken Sie auf „Fertig gestellt“, um den Prinzipal dem Sicherheitsprofil hinzuzufügen.

## Ein Archiv entfernen {#remove-an-archive}

>[!NOTE]
>
>Um ein Archiv zu entfernen, das in einem Drittanbieter-Repository (EMC Documentum Content Server, IBM FileNet Content Manager oder IBM Content Manager) gespeicherte Elemente enthält, müssen Sie mithilfe von Workbench auch die Elementdateien aus dem Repository löschen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Archivverwaltung“.
1. Aktivieren Sie auf der Seite Archivverwaltung das Kontrollkästchen für das zu entfernende Archiv und klicken Sie auf „Entfernen“.
