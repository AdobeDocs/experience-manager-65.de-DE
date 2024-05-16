---
title: Forms JEE-Workflows   Verarbeiten von Benutzerdaten
description: Erfahren Sie, wie Sie JEE-Workflows in AEM Forms zum Entwerfen, Erstellen und Verwalten von Geschäftsprozessen verwenden.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
exl-id: 847fa303-8d1e-4a17-b90d-5f9da5ca2d77
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1379'
ht-degree: 100%

---

# Forms JEE-Workflows   Verarbeiten von Benutzerdaten {#forms-jee-workflows-handling-user-data}

JEE-Workflows in AEM Forms bieten Tools zum Entwerfen, Erstellen und Verwalten von Geschäftsprozessen. Ein Workflow-Prozess besteht aus einer Reihe von Schritten, die in einer festgelegten Reihenfolge ausgeführt werden. Jeder Schritt führt eine bestimmte Aktion aus, z. B. das Zuweisen einer Aufgabe zu einer Benutzerin bzw. einem Benutzer oder das Senden einer E-Mail-Nachricht. Ein Prozess kann mit Assets, Benutzerkonten und Diensten interagieren und kann mit einer der folgenden Methoden ausgelöst werden:

* Starten eines Prozesses aus AEM Forms Workspace
* Verwenden des SOAP- oder RESTful-Dienstes
* Senden eines adaptiven Formulars
* Verwenden eines überwachten Ordners
* Verwenden von E-Mail

Weitere Informationen zum Erstellen von JEE-Workflow-Prozessen in AEM Forms finden Sie in der [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_65_de).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Beim Auslösen und im weiteren Verlauf eines Prozesses werden Daten zu den Prozessteilnehmenden, Daten, die von den Teilnehmenden in das mit dem Prozess verknüpfte Formular eingegebene werden, und Anhänge, die dem Formular hinzugefügt werden, erfasst. Die Daten werden in der JEE-Server-Datenbank in AEM Forms gespeichert und falls konfiguriert, werden einige Daten wie Anhänge im Verzeichnis „Global Document Storage“ (GDS) gespeichert. Das GDS-Verzeichnis kann auf einem gemeinsam genutzten Dateisystem oder einer Datenbank konfiguriert werden.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Wenn ein Prozess ausgelöst wird, werden eine eindeutige Prozessinstanz-ID und eine Aufruf-ID mit langer Lebensdauer generiert und der Prozessinstanz zugeordnet. Sie können auf Daten für eine Prozessinstanz basierend auf der Aufruf-ID mit langer Lebensdauer zugreifen und diese löschen. Sie können die Aufruf-ID mit langer Lebensdauer einer Prozessinstanz vom Benutzernamen des Prozessinitiators oder der Prozessteilnehmer, die ihre Aufgaben eingereicht haben, ableiten.

In den folgenden Szenarien können Sie die Prozessinstanz-ID für eine Initiatorin oder einen Initiator jedoch nicht ermitteln:

* **Prozess, der durch einen überwachten Ordner ausgelöst wurde**: Eine Prozessinstanz kann nicht über ihre Initiatorin oder ihren Initiator identifiziert werden, wenn der Prozess von einem überwachten Ordner ausgelöst wird.  In diesem Fall werden die Benutzerinformationen in den gespeicherten Daten codiert.
* **Von der AEM-Veröffentlichungsinstanz initiierter Prozess**: Alle von der AEM-Veröffentlichungsinstanz ausgelösten Prozessinstanzen erfassen keine Informationen über die Initiatorin oder den Initiator. Allerdings können im vorgangsbezogenen Formular ggf. Benutzerdaten erfasst und in Workflow-Variablen gespeichert werden.
* **Prozess, der über E-Mails initiiert wird**: Die E-Mail-ID des Absenders wird als Eigenschaft in einer opaken BLOB-Spalte der Datenbanktabelle `tb_job_instance` erfasst, die nicht direkt abgefragt werden kann.

### Identifizieren von Prozessinstanz-IDs, wenn die Workflow-Initiatorin bzw. der Workflow-Initiator oder die bzw. der Workflow-Teilnehmende bekannt ist {#initiator-participant}

Führen Sie die folgenden Schritte aus, um Prozessinstanz-IDs für eine Workflow-Initiatorin bzw. einen Workflow-Initiator bzw. eine Teilnehmerin oder einen Teilnehmer zu ermitteln:

1. Führen Sie den folgenden Befehl in der AEM Forms-Server-Datenbank aus, um die Prinzipal-ID für die Workflow-Initiatorin bzw. den Workflow-Initiator oder die Workflow-Teilnehmerin bzw. den Workflow-Teilnehmer aus der Datenbanktabelle `edcprincipalentity` abzurufen.

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

   Die Abfrage gibt Instanz-IDs für alle mit der Teilnehmerin oder dem Teilnehmer verknüpften Prozesse zurück, einschließlich derjenigen, für die die Teilnehmerin bzw. der Teilnehmer keine Aufgabe übermittelt hat.

   Notieren Sie alle Prozessinstanz-IDs für übermittelte Aufgaben und fahren Sie mit den Schritten fort.

   Für verwaiste Aufgaben oder Aufgaben, bei denen `process_instance_id` 0 (Null) ist, notieren Sie sich die entsprechenden Aufgaben-IDs und lesen Sie [Arbeiten mit verwaisten Aufgaben](#orphan).

1. Folgen Sie den Anweisungen im Abschnitt [Bereinigen von Benutzerdaten von Workflow-Instanzen, basierend auf Prozessinstanz-IDs](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge), um Benutzerdaten für identifizierte Prozessinstanz-IDs zu löschen.

### Identifizieren Sie Prozessinstanz-IDs, wenn Benutzerdaten in primitiven Variablen gespeichert werden {#primitive}

Ein Workflow kann so gestaltet werden, dass die Benutzerdaten in einer Variablen erfasst werden, die als Blob in der Datenbank gespeichert wird. In solchen Fällen können Sie Benutzerdaten nur abfragen, wenn sie in einer der folgenden Variablen vom primitiven Typ gespeichert sind:

* **Zeichenfolge**: Enthält die Benutzer-ID direkt oder als Unterzeichenfolge und kann per SQL abgefragt werden.
* **Numerisch**: Enthält direkt die Benutzer-ID.
* **XML**: Enthält die Benutzer-ID als Unterzeichenfolge innerhalb des als Textspalten in der Datenbank gespeicherten Textes und kann wie Zeichenfolgen abgefragt werden.

Führen Sie die folgenden Schritte aus, um zu ermitteln, ob ein Workflow, der Daten in Variablen vom primitiven Typ speichert, Daten für die Benutzerin oder den Benutzer enthält:

1. Führen Sie den folgenden Datenbankbefehl aus:

   ```sql
   select database_table from omd_object_type where name='pt_<app_name>/<workflow_name>'
   ```

   Die Abfrage gibt einen Tabellennamen im `tb_<number>`-Format für das angegebene Programm (`app_name`) und den Workflow (`workflow_name`) zurück.

   >[!NOTE]
   >
   >Der Wert der Eigenschaft `name` kann komplex sein, wenn der Workflow in Unterordnern innerhalb der Anwendung verschachtelt ist. Stellen Sie sicher, dass Sie den genauen vollständigen Pfad zum Workflow angeben, den Sie aus der Datenbanktabelle `omd_object_type` abrufen können.

1. Überprüfen Sie das Tabellenschema `tb_<number>`. Die Tabelle enthält Variablen, die Benutzerdaten für den angegebenen Workflow speichern. Die Variablen in der Tabelle entsprechen den Variablen im Workflow.

   Identifizieren und notieren Sie die Variable, die der Workflow-Variable entspricht, die die Benutzer-ID enthält. Wenn die identifizierte Variable vom primitiven Typ ist, können Sie eine Abfrage ausführen, um Workflow-Instanzen zu ermitteln, die einer Benutzer-ID zugeordnet sind.

1. Führen Sie den folgenden Datenbankbefehl aus: In diesem Befehl ist `user_var` die Variable vom Typ „primitive“, die die Benutzer-ID enthält.

   ```sql
   select process_instance_id from <tb_name> where <user_var>=<user_ID>
   ```

   Die Abfrage gibt alle Prozessinstanz-IDs zurück, die der angegebenen `user_ID` zugeordnet sind.

1. Folgen Sie den Anweisungen im Abschnitt [Bereinigen von Benutzerdaten von Workflow-Instanzen, basierend auf Prozessinstanz-IDs](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge), um Benutzerdaten für identifizierte Prozessinstanz-IDs zu löschen.

### Bereinigen von Benutzerdaten von Workflow-Instanzen, basierend auf Prozessinstanz-IDs {#purge}

Nachdem Sie nun die Prozessinstanz-IDs identifiziert haben, die einer Benutzerin oder einem Benutzer zugeordnet sind, gehen Sie wie folgt vor, um Benutzerdaten aus den jeweiligen Prozessinstanzen zu löschen.

1. Führen Sie den folgenden Befehl aus, um die langlebige Aufruf-ID und den Status für eine Prozessinstanz aus der Tabelle `tb_process_instance` abzurufen.

   ```sql
   select long_lived_invocation_id, status from tb_process_instance where id='process_instance_id'
   ```

   Die Abfrage gibt die langlebige Aufruf-ID und den Status für die angegebene `process_instance_id` zurück.

1. Erstellen Sie eine Instanz des öffentlichen `ProcessManager`-Clients (`com.adobe.idp.workflow.client.ProcessManager`) unter Verwendung einer `ServiceClientFactory`-Instanz mit den richtigen Verbindungseinstellungen.

   Weitere Informationen finden Sie in der Java™ API-Referenz für [Class ProcessManager](https://helpx.adobe.com/de/experience-manager/6-3/forms/ProgramLC/javadoc/com/adobe/idp/workflow/client/ProcessManager.html).

1. Überprüfen Sie den Status der Workflow-Instanz. Wenn der Status nicht 2 (COMPLETE) oder 4 (TERMINATED) ist, beenden Sie die Instanz zuerst, indem Sie die folgende Methode aufrufen:

   `ProcessManager.terminateProcess(<long_lived_invocation_id>)`.

1. Bereinigen Sie die Workflow-Instanz, indem Sie die folgende Methode aufrufen:

   `ProcessManager.purgeProcessInstance(<long_lived_invocation_id>)`

   Die Methode `purgeProcessInstance` löscht alle Daten für die angegebene Aufruf-ID vollständig aus der AEM Forms-Server-Datenbank und dem GDS, sofern konfiguriert.

### Arbeiten mit verwaisten Aufgaben {#orphan}

Verwaiste Aufgaben sind Aufgaben, deren enthaltener Prozess initiiert, aber noch nicht übermittelt wurde. In diesem Fall ist die `process_instance_id` **0** (Null). Daher ist es nicht möglich, für verwaiste Aufgaben gespeicherte Benutzerdaten mithilfe der Prozessinstanz-IDs zu verfolgen. Sie können sie jedoch mithilfe der Aufgaben-ID für eine verwaiste Aufgabe verfolgen.  Sie können die Aufgaben-IDs für einen Benutzer aus der `tb_task` ermitteln, wie in [Prozessinstanz-IDs identifizieren, wenn der Workflow-Initiator oder -Teilnehmer bekannt ist](/help/forms/using/forms-workflow-jee-handling-user-data.md#initiator-participant).

Sobald Sie über die Aufgaben-IDs verfügen, gehen Sie wie folgt vor, um die zugehörigen Dateien und Daten mit einer verwaisten Aufgabe aus GDS und der Datenbank zu löschen.

1. Führen Sie den folgenden Befehl in der AEM Forms-Server-Datenbank aus, damit Sie IDs für die identifizierten Aufgaben-IDs abrufen können.

   ```sql
   select id from tb_form_data where task_id=<task_id>
   ```

   Die Abfrage gibt eine Liste von IDs zurück.  Erstellen Sie für jede ID (`fd_id`), die in den Ergebnissen zurückgegeben wird, eine Liste der Sitzungs-ID-Zeichenfolgen wie folgt:

   * _ `wfattach<task_id>`
   * `_wftask<fd_id>`
   * `_wftaskformid<fd_id>`

1. Führen Sie einen der folgenden Schritte aus, je nachdem, ob Ihr GDS auf ein Dateisystem oder eine Datenbank verweist:

   1. **GDS im Dateisystem**

      Im GDS-Dateisystem:

      1. Suchen Sie nach Dateien mit den folgenden Sitzungs-ID-Zeichenfolgen als ihre Erweiterungen:

      * `_wfattach<task_id>`
      * `_wftask<fd_id>`
      * `_wftaskformid<fd_id>`

      Die Dateien mit diesen Erweiterungen sind die Markierungsdateien. Sie werden mit Dateinamen im folgenden Format gespeichert:

      `<file_name_guid>.session<session_id_string>`

      1. Löschen Sie alle Markierungsdateien und andere Dateien mit dem genauen Dateinamen wie `<file_name_guid>` aus dem Dateisystem.

   1. **GDS in der Datenbank**

      Führen Sie für jede Sitzungs-ID die folgenden Befehle aus:

      ```sql
      delete from tb_dm_chunk where documentid in (select documentid from tb_dm_session_reference where sessionid=<session_id>)
      delete from tb_dm_session_reference where sessionid=<session_id>
      delete from tb_dm_deletion where sessionid=<session_id>
      ```

1. Führen Sie die folgenden Befehle aus, um Daten für Aufgaben-IDs aus der AEM Forms-Server-Datenbank zu löschen:

   ```sql
   delete from tb_task_acl where task_id=<task_id>
   delete from tb_task_attachment where task_id=<task_id>
   delete from tb_form_data where task_id=<task_id>
   delete from tb_assignment where task_id=<task_id>
   delete from tb_task where id=<task_id>
   ```
