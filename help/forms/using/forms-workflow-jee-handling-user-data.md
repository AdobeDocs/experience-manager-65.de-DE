---
title: Forms JEE-Workflows| Verarbeiten von Benutzerdaten
seo-title: Forms JEE-Workflows| Verarbeiten von Benutzerdaten
description: Forms JEE-Workflows| Verarbeiten von Benutzerdaten
uuid: 3b06ef19-d3c4-411e-9530-2c5d2159b559
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5632a8df-a827-4e38-beaa-18b61c2208a3
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '1371'
ht-degree: 70%

---


# Forms JEE-Workflows| Verarbeiten von Benutzerdaten {#forms-jee-workflows-handling-user-data}

AEM Forms JEE Workflows bietet Tools zum Entwerfen, Erstellen und Verwalten von Geschäftsprozessen. Ein Workflow-Prozess besteht aus einer Reihe von Schritten, die in einer bestimmten Reihenfolge ausgeführt werden. Bei jedem Schritt wird eine bestimmte Aktivität ausgeführt, z. B. einem Benutzer eine Aufgabe zuweisen oder eine E-Mail verschicken. Ein Prozess kann mit Assets, Benutzerkonten und Diensten interagieren und mit einer der folgenden Methoden ausgelöst werden:

* Starten eines Prozesses von AEM Forms Workspace aus
* Verwenden des SOAP- oder RESTful-Service
* Senden eines adaptiven Formulars
* Verwenden eines überwachten Ordners
* E-Mail verwenden

Weitere Informationen zum Erstellen des AEM Forms JEE-Workflow finden Sie unter [Workbench Help](http://www.adobe.com/go/learn_aemforms_workbench_65).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Wenn ein Prozess ausgelöst wird und fortschreitet, erfasst er Daten zu den Prozessteilnehmern, Daten, die von Teilnehmern in dem mit dem Prozess verknüpften Formular eingegeben wurden, und Anhänge, die dem Formular hinzugefügt wurden. Die Daten werden in der AEM Forms JEE-Serverdatenbank gespeichert. Wenn sie konfiguriert sind, werden einige Daten wie Anlagen im Ordner des globalen Dokumentenspeichers (Global Document Storage, GDS) gespeichert. Der Ordner des globalen Dokumentenspeichers kann auf ein freigegebenes Dateisystem oder auf eine Datenbank konfiguriert werden.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Wenn ein Prozess ausgelöst wird, werden eine eindeutige Prozessinstanz-ID und eine langlebige Aufrufkennung generiert und der Prozessinstanz zugeordnet. Sie können auf Daten für eine Prozessinstanz basierend auf der Aufruf-ID mit langer Lebensdauer zugreifen und diese löschen. Sie können die langlebige Aufrufkennung einer Prozessinstanz mit dem Benutzernamen des Prozessinitiators oder der Prozessteilnehmer, die ihre Aufgaben übermittelt haben, definieren.

Sie können die Prozessinstanz-ID für einen Initiator in den folgenden Szenarien jedoch nicht identifizieren:

* **Prozess, die durch einen überwachten Ordner ausgelöst wurden**: Eine Prozessinstanz kann nicht über ihren Initiator identifiziert werden, wenn der Prozess von einem überwachten Ordner ausgelöst wird. In diesem Fall werden die Benutzerinformationen in den gespeicherten Daten codiert.
* **Von der AEM-Instanz veröffentlichter Prozess**: Alle Prozessinstanzen, die von der AEM-Veröffentlichungsinstanz ausgelöst wurden, erfassen keine Informationen zum Initiator. Benutzerdaten können jedoch in dem Formular, das mit dem Prozess verknüpft ist, der in den Workflow-Variablen gespeichert ist, erfasst werden.
* **Durch E-Mail initiierter Prozess**: Die E-Mail-ID des Absenders wird als Eigenschaft in einer undurchsichtigen Blockspalte der  `tb_job_instance` Datenbanktabelle erfasst, die nicht direkt abgefragt werden kann.

### Identifizieren Sie Prozessinstanz-IDs, wenn der Workflow-Initiator oder -Teilnehmer bekannt ist {#initiator-participant}

Führen Sie die folgenden Schritte durch, um Prozessinstanz-IDs für einen Workflow-Initiator oder einen Teilnehmer zu identifizieren:

1. Führen Sie den folgenden Befehl in der AEM Forms-Serverdatenbank aus, um die Hauptkennung für Workflow-Initiator oder -Teilnehmer aus der `edcprincipalentity`-Datenbanktabelle abzurufen.

   ```sql
   select id from edcprincipalentity where canonicalname='user_ID'
   ```

   Die Abfrage gibt die Prinzipal-ID für das angegebene `user_ID` zurück.

1. (**Für Workflow-Initiator**) Führen Sie den folgenden Befehl aus, um alle Aufgaben abzurufen, die mit der Prinzipal-ID für den Initiator aus der Datenbanktabelle `tb_task` verknüpft sind.

   ```sql
   select * from tb_task where start_task = 1 and create_user_id= 'initiator_principal_id'
   ```

   Die Abfrage gibt Aufgaben zurück, die von dem angegebenen `initiator`_ `principal_id` initiiert wurden. Die Aufgaben sind von zwei Arten:

   * **Abgeschlossene Aufgaben**: Diese Aufgaben wurden gesendet und zeigen einen alphanumerischen Wert im  `process_instance_id` Feld an. Notieren Sie alle Prozessinstanz-IDs für übermittelte Aufgaben und fahren Sie mit den Schritten fort.
   * **Aufgaben eingeleitet, aber nicht abgeschlossen**: Diese Aufgaben sind eingeleitet, aber noch nicht abgeschickt. Der Wert im Feld `process_instance_id` für diese Aufgaben ist **0** (zero). Beachten Sie in diesem Fall die entsprechenden Aufgaben-IDs und siehe [Arbeiten mit verwaisten Aufgaben](#orphan).

1. (**Für Workflow-Teilnehmer**) Führen Sie den folgenden Befehl aus, um Prozessinstanz-IDs abzurufen, die mit der Hauptkennung des Prozessteilnehmers für den Initiator aus der `tb_assignment`-Datenbanktabelle verknüpft sind.

   ```sql
   select distinct a.process_instance_id from tb_assignment a join tb_queue q on a.queue_id = q.id where q.workflow_user_id='participant_principal_id'
   ```

   Die Abfrage gibt Instanz-IDs für alle Prozesse zurück, die mit dem Teilnehmer verknüpft sind, einschließlich derjenigen, bei denen der Teilnehmer keine Aufgabe eingereicht hat.

   Notieren Sie alle Prozessinstanz-IDs für übermittelte Aufgaben und fahren Sie mit den Schritten fort.

   Beachten Sie bei verwaisten Aufgaben oder Aufgaben, bei denen `process_instance_id` 0 (null) ist, die entsprechenden Aufgaben-IDs und siehe [Arbeiten mit verwaisten Aufgaben](#orphan).

1. Befolgen Sie die Anweisungen im Abschnitt [Benutzerdaten aus Workflow-Instanzen basierend auf Prozessinstanz-IDs](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) löschen, um Benutzerdaten für identifizierte Prozessinstanz-IDs zu löschen.

### Identifizieren Sie Prozessinstanz-IDs, wenn Benutzerdaten in primitiven Variablen gespeichert werden {#primitive}

Ein Workflow kann so gestaltet werden, dass die Benutzerdaten in einer Variablen erfasst werden, die als Blob in der Datenbank gespeichert wird. In solchen Fällen können Sie Benutzerdaten nur abfragen, wenn sie in einer der folgenden primitiven Variablen gespeichert sind:

* **Zeichenfolge**: Enthält die Benutzer-ID direkt oder als Teilzeichenfolge und kann mit SQL abgefragt werden.
* **Nummerisch:** Enthält direkt die Benutzer-ID.
* **XML**: Enthält die Benutzer-ID als Teilzeichenfolge im Text, der als Textspalte in der Datenbank gespeichert ist und der wie Zeichenfolgen abgefragt werden kann.

Führen Sie die folgenden Schritte durch, um festzustellen, ob ein Workflow, der Daten in primitiven Variablen speichert, Daten für den Benutzer enthält:

1. Führen Sie den folgenden Datenbankbefehl aus:

   ```sql
   select database_table from omd_object_type where name='pt_<app_name>/<workflow_name>'
   ```

   Die Abfrage gibt einen Tabellennamen im Format `tb_<number>` für die angegebene Anwendung ( `app_name`) und den Workflow ( `workflow_name`) zurück.

   >[!NOTE]
   >
   >Der Wert der Eigenschaft `name`kann komplex sein, wenn der Workflow in Unterordnern innerhalb der Anwendung verschachtelt ist. Stellen Sie sicher, dass Sie den genauen vollständigen Pfad zum Workflow angeben, den Sie aus der Datenbanktabelle `omd_object_type` abrufen können.

1. Überprüfen Sie das Schema `tb_<number>`. Die Tabelle enthält Variablen, die Benutzerdaten für den angegebenen Workflow speichern. Die Variablen in der Tabelle entsprechen den Variablen im Workflow.

   Identifizieren und notieren Sie sich die Variable, die der Workflow-Variablen entspricht, die die Benutzer-ID enthält. Wenn die angegebene Variable vom Typ „primitive“ ist, können Sie eine Abfrage ausführen, um Workflow-Instanzen zu ermitteln, die einer Benutzer-ID zugeordnet sind.

1. Führen Sie den folgenden Datenbankbefehl aus: In diesem Befehl ist `user_var` die Variable vom Typ „primitive“, die die Benutzer-ID enthält.

   ```sql
   select process_instance_id from <tb_name> where <user_var>=<user_ID>
   ```

   Die Abfrage gibt alle Prozessinstanz-IDs zurück, die mit dem angegebenen `user_ID` verknüpft sind.

1. Befolgen Sie die Anweisungen im Abschnitt [Benutzerdaten aus Workflow-Instanzen basierend auf Prozessinstanz-IDs](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) löschen, um Benutzerdaten für identifizierte Prozessinstanz-IDs zu löschen.

### Purge user data from workflow instances based on process instance IDs (Bereinigen von Benutzerdaten von Workflow-Instanzen, basierend auf Prozessinstanz-IDs){#purge}

Nachdem Sie die Prozessinstanz-IDs identifiziert haben, die einem Benutzer zugeordnet sind, führen Sie folgende Schritte aus, um Benutzerdaten aus den jeweiligen Prozessinstanzen zu löschen.

1. Führen Sie den folgenden Befehl aus, um dauerhaft genutzte Aufrufkennung und Status für eine Prozessinstanz aus der Tabelle `tb_process_instance` abzurufen.

   ```sql
   select long_lived_invocation_id, status from tb_process_instance where id='process_instance_id'
   ```

   Die Abfrage gibt die langlebige Aufrufkennung und den Status für das angegebene `process_instance_id` zurück.

1. Erstellen Sie eine Instanz des öffentlichen `ProcessManager`-Clients ( `com.adobe.idp.workflow.client.ProcessManager`) mit einer `ServiceClientFactory`-Instanz mit den richtigen Verbindungseinstellungen.

   Weitere Informationen finden Sie in der Java API-Referenz unter [Class ProcessManager](https://helpx.adobe.com/de/experience-manager/6-3/forms/ProgramLC/javadoc/com/adobe/idp/workflow/client/ProcessManager.html).

1. Überprüfen Sie den Status der Workflow-Instanz. Wenn der Status nicht 2 (COMPLETE) oder 4 (BEENDET) ist, beenden Sie die Instanz zunächst, indem Sie die folgende Methode aufrufen:

   `ProcessManager.terminateProcess(<long_lived_invocation_id>)`.

1. Bereinigen Sie die Workflow-Instanz, indem Sie die folgende Methode aufrufen:

   `ProcessManager.purgeProcessInstance(<long_lived_invocation_id>)`

   Die Methode `purgeProcessInstance` löscht alle Daten für die angegebene Aufruf-ID vollständig aus der AEM Forms-Serverdatenbank und dem GDS, sofern konfiguriert.

### Arbeiten mit verwaisten Aufgaben {#orphan}

Verwaiste Aufgaben sind Aufgaben, deren Containing-Prozess initiiert, aber noch nicht übergeben wurde. in diesem Fall ist `process_instance_id` **0** (zero). Daher können Sie Benutzerdaten, die für verwaiste Aufgaben gespeichert wurden, nicht mithilfe von Prozessinstanz-IDs verfolgen. Sie können sie jedoch mithilfe der Aufgaben-ID für eine verwaiste Aufgabe verfolgen. Sie können die Aufgaben-IDs für einen Benutzer aus der `tb_task` ermitteln, wie in [Prozessinstanz-IDs identifizieren, wenn der Workflow-Initiator oder -Teilnehmer bekannt ist](/help/forms/using/forms-workflow-jee-handling-user-data.md#initiator-participant).

Sobald Sie die Aufgaben-IDs haben, führen Sie die folgenden Schritte aus, um die verknüpften Dateien und Daten mit einer verwaisten Aufgabe aus dem GDS und der Datenbank zu löschen.

1. Führen Sie den folgenden Befehl in der AEM Forms-Serverdatenbank aus, um IDs für die identifizierten Aufgaben-IDs abzurufen.

   ```sql
   select id from tb_form_data where task_id=<task_id>
   ```

   Die Abfrage gibt eine Liste von IDs zurück. Erstellen Sie für jede ID (`fd_id`), die in den Ergebnissen zurückgegeben wird, eine Liste der Sitzungs-ID-Zeichenfolgen wie folgt:

   * _ `wfattach<task_id>`
   * `_wftask<fd_id>`
   * `_wftaskformid<fd_id>`

1. Abhängig davon, ob Ihr GDS auf ein Dateisystem oder eine Datenbank verweist, führen Sie einen der folgenden Schritte aus:

   1. **GDS im Dateisystem**

      Im GDS-Dateisystem:

      1. Suchen Sie nach Dateien mit den folgenden Sitzungs-ID-Zeichenfolgen als ihre Erweiterungen:
      * `_wfattach<task_id>`
      * `_wftask<fd_id>`
      * `_wftaskformid<fd_id>`

      Die Dateien mit diesen Erweiterungen sind die Markierungsdateien. Sie werden mit Dateinamen im folgenden Format gespeichert:

      `<file_name_guid>.session<session_id_string>`

      1. Löschen Sie alle Marker-Dateien und andere Dateien mit dem exakten Dateinamen `<file_name_guid>` aus dem Dateisystem.
   1. **GDS in der Datenbank**

      Führen Sie den folgenden Befehle für jede Sitzungs-ID aus:

      ```sql
      delete from tb_dm_chunk where documentid in (select documentid from tb_dm_session_reference where sessionid=<session_id>)
      delete from tb_dm_session_reference where sessionid=<session_id>
      delete from tb_dm_deletion where sessionid=<session_id>
      ```




1. Führen Sie die folgenden Befehle aus, um Daten für Aufgaben-IDs aus der AEM Forms-Serverdatenbank zu löschen:

   ```sql
   delete from tb_task_acl where task_id=<task_id>
   delete from tb_task_attachment where task_id=<task_id>
   delete from tb_form_data where task_id=<task_id>
   delete from tb_assignment where task_id=<task_id>
   delete from tb_task where id=<task_id>
   ```

