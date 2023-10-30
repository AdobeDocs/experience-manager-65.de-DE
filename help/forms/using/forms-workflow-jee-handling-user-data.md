---
title: Forms JEE-Workflows   Verarbeiten von Benutzerdaten
description: AEM Forms JEE-Workflows zum Entwerfen, Erstellen und Verwalten von Geschäftsprozessen.
uuid: 3b06ef19-d3c4-411e-9530-2c5d2159b559
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5632a8df-a827-4e38-beaa-18b61c2208a3
role: Admin
exl-id: 847fa303-8d1e-4a17-b90d-5f9da5ca2d77
source-git-commit: 0e5b89617d481c69882ec5d4658e76855aa9b691
workflow-type: tm+mt
source-wordcount: '1370'
ht-degree: 53%

---

# Forms JEE-Workflows   Verarbeiten von Benutzerdaten {#forms-jee-workflows-handling-user-data}

JEE-Workflows in AEM Forms bieten Tools zum Entwerfen, Erstellen und Verwalten von Geschäftsprozessen. Ein Workflow-Prozess besteht aus einer Reihe von Schritten, die in einer angegebenen Reihenfolge ausgeführt werden. Jeder Schritt führt eine bestimmte Aktion aus, z. B. das Zuweisen einer Aufgabe zu einer Benutzerin bzw. einem Benutzer oder das Senden einer E-Mail-Nachricht. Ein Prozess kann mit Assets, Benutzerkonten und Diensten interagieren und mit einer der folgenden Methoden ausgelöst werden:

* Starten eines Prozesses aus AEM Forms Workspace
* Verwenden des SOAP- oder RESTful-Dienstes
* Senden eines adaptiven Formulars
* Verwenden eines überwachten Ordners
* Email verwenden

Weitere Informationen zum Erstellen von JEE-Workflow-Prozessen in AEM Forms finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_65_de).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Wenn ein Prozess ausgelöst wird und im weiteren Verlauf erfasst er Daten zu den Prozessteilnehmern, Daten, die von Teilnehmern in das mit dem Prozess verknüpfte Formular eingegeben werden, und Anhänge, die dem Formular hinzugefügt werden. Die Daten werden in der AEM Forms JEE-Serverdatenbank gespeichert, und falls konfiguriert, werden einige Daten wie Anhänge im Ordner des globalen Dokumentenspeichers (GDS) gespeichert. Der Ordner des globalen Dokumentenspeichers kann auf einem freigegebenen Dateisystem oder in einer Datenbank konfiguriert werden.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Wenn ein Prozess ausgelöst wird, werden eine eindeutige Prozessinstanz-ID und eine Aufruf-ID mit langer Lebensdauer generiert und der Prozessinstanz zugeordnet. Sie können auf Daten für eine Prozessinstanz basierend auf der Aufruf-ID mit langer Lebensdauer zugreifen und diese löschen. Sie können die Aufruf-ID mit langer Lebensdauer einer Prozessinstanz vom Benutzernamen des Prozessinitiators oder der Prozessteilnehmer, die ihre Aufgaben eingereicht haben, ableiten.

Sie können die Prozessinstanz-ID für einen Initiator jedoch in den folgenden Szenarien nicht identifizieren:

* **Prozess, der durch einen überwachten Ordner ausgelöst wird**: Eine Prozessinstanz kann nicht mit ihrem Initiator identifiziert werden, wenn der Prozess durch einen überwachten Ordner ausgelöst wird. In diesem Fall werden die Benutzerinformationen in den gespeicherten Daten codiert.
* **Von der Veröffentlichungs-AEM-Instanz initiierte Prozesse**: Alle Prozessinstanzen, die von AEM Veröffentlichungsinstanz ausgelöst werden, erfassen keine Informationen zum Initiator. Benutzerdaten können jedoch in dem Formular erfasst werden, das dem Prozess zugeordnet ist und in Workflow-Variablen gespeichert wird.
* **Prozess, der über E-Mails initiiert wird**: Die E-Mail-ID des Absenders wird als Eigenschaft in einer opaken BLOB-Spalte der Datenbanktabelle `tb_job_instance` erfasst, die nicht direkt abgefragt werden kann.

### Identifizieren von Prozessinstanz-IDs, wenn der Workflow-Initiator oder -Teilnehmer bekannt ist {#initiator-participant}

Führen Sie die folgenden Schritte aus, um Prozessinstanz-IDs für einen Workflow-Initiator oder einen Teilnehmer zu identifizieren:

1. Führen Sie den folgenden Befehl in der AEM Forms-Server-Datenbank aus, um die Prinzipal-ID für den Workflow-Initiator oder -Teilnehmer aus der Datenbanktabelle `edcprincipalentity` abzurufen.

   ```sql
   select id from edcprincipalentity where canonicalname='user_ID'
   ```

   Die Abfrage gibt die Prinzipal-ID für die angegebene `user_ID` zurück.

1. (**Für Workflow-Initiator**) Führen Sie den folgenden Befehl aus, um alle Aufgaben abzurufen, die mit der Prinzipal-ID für den Initiator aus der Datenbanktabelle `tb_task` verknüpft sind.

   ```sql
   select * from tb_task where start_task = 1 and create_user_id= 'initiator_principal_id'
   ```

   Die Abfrage gibt die Aufgaben zurück, die für die angegebene `initiator`_ `principal_id` initiiert werden. Die Aufgaben sind von zwei Arten:

   * **Erledigte Aufgaben**: Diese Aufgaben wurden übergeben, und für sie wird im Feld `process_instance_id` ein alphanumerischer Wert angezeigt. Notieren Sie alle Prozessinstanz-IDs für übermittelte Aufgaben und fahren Sie mit den Schritten fort.
   * **Aufgaben eingeleitet, aber nicht abgeschlossen**: Diese Aufgaben sind eingeleitet, aber noch nicht abgeschickt. Der Wert im Feld `process_instance_id` für diese Aufgaben ist **0** (Null). Beachten Sie in diesem Fall die entsprechenden Aufgaben-IDs und siehe [Arbeiten mit verwaisten Aufgaben](#orphan).

1. (**Für Workflow-Teilnehmer**) Führen Sie den folgenden Befehl aus, um Prozessinstanz-IDs abzurufen, die mit der Prinzipal-ID des Prozessteilnehmers für den Initiator aus der Datenbanktabelle `tb_assignment` verknüpft sind.

   ```sql
   select distinct a.process_instance_id from tb_assignment a join tb_queue q on a.queue_id = q.id where q.workflow_user_id='participant_principal_id'
   ```

   Die Abfrage gibt Instanz-IDs für alle Prozesse zurück, die mit dem Teilnehmer verbunden sind, einschließlich der Prozesse, bei denen der Teilnehmer keine Aufgabe eingereicht hat.

   Notieren Sie alle Prozessinstanz-IDs für übermittelte Aufgaben und fahren Sie mit den Schritten fort.

   Für verwaiste Aufgaben oder Aufgaben, bei denen `process_instance_id` 0 (Null) ist, notieren Sie sich die entsprechenden Aufgaben-IDs und lesen Sie [Arbeiten mit verwaisten Aufgaben](#orphan).

1. Befolgen Sie die Anweisungen im Abschnitt [Bereinigen von Benutzerdaten aus Workflow-Instanzen basierend auf Prozessinstanz-IDs](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge), um Benutzerdaten für identifizierte Prozessinstanz-IDs zu löschen.

### Identifizieren Sie Prozessinstanz-IDs, wenn Benutzerdaten in primitiven Variablen gespeichert werden {#primitive}

Ein Workflow kann so gestaltet werden, dass die Benutzerdaten in einer Variablen erfasst werden, die als Blob in der Datenbank gespeichert wird. In solchen Fällen können Sie Benutzerdaten nur abfragen, wenn sie in einer der folgenden Variablen vom Typ &quot;Primitive&quot;gespeichert sind:

* **Zeichenfolge**: Enthält die Benutzer-ID direkt oder als Unterzeichenfolge und kann mit SQL abgefragt werden.
* **Numerisch**: Enthält die Benutzer-ID direkt.
* **XML**: Enthält die Benutzer-ID als Teilzeichenfolge im Text, der als Textspalten in der Datenbank gespeichert ist, und kann wie Zeichenfolgen abgefragt werden.

Führen Sie die folgenden Schritte aus, um zu ermitteln, ob ein Workflow, der Daten in Variablen vom Typ &quot;Primitive&quot;speichert, Daten für den Benutzer enthält:

1. Führen Sie den folgenden Datenbankbefehl aus:

   ```sql
   select database_table from omd_object_type where name='pt_<app_name>/<workflow_name>'
   ```

   Die Abfrage gibt einen Tabellennamen im `tb_<number>`-Format für das angegebene Programm (`app_name`) und den Workflow (`workflow_name`) zurück.

   >[!NOTE]
   >
   >Der Wert der Eigenschaft `name`kann komplex sein, wenn der Workflow in Unterordnern innerhalb der Anwendung verschachtelt ist. Stellen Sie sicher, dass Sie den genauen vollständigen Pfad zum Workflow angeben, den Sie aus der Datenbanktabelle `omd_object_type` abrufen können.

1. Überprüfen Sie das Tabellenschema `tb_<number>`. Die Tabelle enthält Variablen, die Benutzerdaten für den angegebenen Workflow speichern. Die Variablen in der Tabelle entsprechen den Variablen im Workflow.

   Identifizieren und beachten Sie die Variable, die der Workflow-Variablen entspricht, die die Benutzer-ID enthält. Wenn die identifizierte Variable vom Typ &quot;primitiv&quot;ist, können Sie eine Abfrage ausführen, um Workflow-Instanzen zu bestimmen, die mit einer Benutzer-ID verknüpft sind.

1. Führen Sie den folgenden Datenbankbefehl aus: In diesem Befehl ist `user_var` die Variable vom Typ „primitive“, die die Benutzer-ID enthält.

   ```sql
   select process_instance_id from <tb_name> where <user_var>=<user_ID>
   ```

   Die Abfrage gibt alle Prozessinstanz-IDs zurück, die der angegebenen `user_ID` zugeordnet sind.

1. Folgen Sie den Anweisungen im Abschnitt [Purge user data from workflow instances based on process instance IDs (Bereinigen von Benutzerdaten von Workflow-Instanzen, basierend auf Prozessinstanz-IDs)](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge), um Benutzerdaten für identifizierte Prozessinstanz-IDs zu löschen.

### Bereinigen von Benutzerdaten aus Workflow-Instanzen basierend auf Prozessinstanz-IDs {#purge}

Nachdem Sie die mit einem Benutzer verknüpften Prozessinstanz-IDs identifiziert haben, führen Sie die folgenden Schritte aus, um Benutzerdaten aus den entsprechenden Prozessinstanzen zu löschen.

1. Führen Sie den folgenden Befehl aus, um die langlebige Aufruf-ID und den Status für eine Prozessinstanz aus der Tabelle `tb_process_instance` abzurufen.

   ```sql
   select long_lived_invocation_id, status from tb_process_instance where id='process_instance_id'
   ```

   Die Abfrage gibt die langlebige Aufruf-ID und den Status für die angegebene `process_instance_id` zurück.

1. Erstellen Sie eine Instanz des öffentlichen `ProcessManager`-Clients (`com.adobe.idp.workflow.client.ProcessManager`) unter Verwendung einer `ServiceClientFactory`-Instanz mit den richtigen Verbindungseinstellungen.

   Weitere Informationen finden Sie in der Java-API-Referenz für [Class ProcessManager](https://helpx.adobe.com/de/experience-manager/6-3/forms/ProgramLC/javadoc/com/adobe/idp/workflow/client/ProcessManager.html).

1. Überprüfen Sie den Status der Workflow-Instanz. Wenn der Status nicht 2 (COMPLETE) oder 4 (TERMINATED) ist, beenden Sie die Instanz zuerst, indem Sie die folgende Methode aufrufen:

   `ProcessManager.terminateProcess(<long_lived_invocation_id>)`.

1. Bereinigen Sie die Workflow-Instanz, indem Sie die folgende Methode aufrufen:

   `ProcessManager.purgeProcessInstance(<long_lived_invocation_id>)`

   Die Methode `purgeProcessInstance` löscht alle Daten für die angegebene Aufruf-ID vollständig aus der AEM Forms-Serverdatenbank und dem GDS, sofern konfiguriert.

### Arbeiten mit verwaisten Aufgaben {#orphan}

Verwaiste Aufgaben sind die Aufgaben, deren Prozess initiiert, aber noch nicht eingereicht wurde. In diesem Fall ist die `process_instance_id` **0** (Null). Daher können Sie Benutzerdaten, die für verwaiste Aufgaben gespeichert wurden, nicht mithilfe von Prozessinstanz-IDs nachverfolgen. Sie können sie jedoch mithilfe der Aufgaben-ID für eine verwaiste Aufgabe nachverfolgen. Sie können die Aufgaben-IDs für einen Benutzer aus der `tb_task` ermitteln, wie in [Prozessinstanz-IDs identifizieren, wenn der Workflow-Initiator oder -Teilnehmer bekannt ist](/help/forms/using/forms-workflow-jee-handling-user-data.md#initiator-participant).

Nachdem Sie über die Aufgaben-IDs verfügen, führen Sie die folgenden Schritte aus, um die zugehörigen Dateien und Daten mit einer verwaisten Aufgabe aus dem GDS und der Datenbank zu bereinigen.

1. Führen Sie den folgenden Befehl in der AEM Forms-Serverdatenbank aus, um IDs für die identifizierten Aufgaben-IDs abzurufen.

   ```sql
   select id from tb_form_data where task_id=<task_id>
   ```

   Die Abfrage gibt eine Liste von IDs zurück. Erstellen Sie für jede ID (`fd_id`), die in den Ergebnissen zurückgegeben wird, eine Liste der Sitzungs-ID-Zeichenfolgen wie folgt:

   * _ `wfattach<task_id>`
   * `_wftask<fd_id>`
   * `_wftaskformid<fd_id>`

1. Führen Sie je nachdem, ob Ihr GDS auf ein Dateisystem oder eine Datenbank verweist, einen der folgenden Schritte aus:

   1. **GDS im Dateisystem**

      Im GDS-Dateisystem:

      1. Suchen Sie nach Dateien mit den folgenden Sitzungs-ID-Zeichenfolgen als ihre Erweiterungen:

      * `_wfattach<task_id>`
      * `_wftask<fd_id>`
      * `_wftaskformid<fd_id>`

      Die Dateien mit diesen Erweiterungen sind die Markierungsdateien. Sie werden mit Dateinamen im folgenden Format gespeichert:

      `<file_name_guid>.session<session_id_string>`

      1. Löschen Sie alle Markierungsdateien und andere Dateien mit dem genauen Dateinamen wie `<file_name_guid>` aus dem Dateisystem.

   1. **GDS in Datenbank**

      Führen Sie die folgenden Befehle für jede Sitzungs-ID aus:

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
