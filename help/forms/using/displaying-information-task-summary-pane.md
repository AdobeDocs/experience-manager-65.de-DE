---
title: Anzeigen von Informationen in der Aufgabenzusammenfassung
seo-title: Anzeigen von Informationen in der Aufgabenzusammenfassung
description: In AEM Forms Workspace kann ein Bedienfeld zur Aufgabenzusammenfassung konfiguriert werden, um die Aufgabe zusammenzufassen oder eine beliebige Website anzuzeigen.
seo-description: In AEM Forms Workspace kann ein Bedienfeld zur Aufgabenzusammenfassung konfiguriert werden, um die Aufgabe zusammenzufassen oder eine beliebige Website anzuzeigen.
uuid: 2fcc3d9f-0ec2-4250-8dc1-9746fd72ea60
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 90d0f584-b598-4b21-85d7-31da5f13d404
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Anzeigen von Informationen in der Aufgabenzusammenfassung {#displaying-information-in-the-task-summary-pane}

Wenn Sie eine Aufgabe in AEM Forms Workspace öffnen, kann eine Zusammenfassung der Aufgabe in einem entsprechenden Fenster angezeigt werden. Diese zusätzlichen und wichtigen Informationen zu einer Aufgabe sind nützlich für den Endbenutzer von AEM Forms Workspace.

Mit AEM Forms Workspace können Sie eine Webseite Ihrer Wahl im Bereich Aufgabenzusammenfassung anzeigen. Es kann ein Vorgang erstellt werden, um eine Aufgabenzusammenfassung mithilfe von Workbench anzuzeigen.

1. Erstellen Sie in Workbench einen Assign Task-Prozess. Weitere Informationen zum Prozess „Assign Task“ finden Sie im Dienstreferenzthema der [Workbench-Hilfe](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/).

   >[!NOTE]
   >
   >Wenn eine Aufgabenzusammenfassungs-URL vorhanden ist, wird standardmäßig diese Ansicht statt der Formularansicht geöffnet. In diesem Fall wird, auch wenn ein Benutzer in Assign Task die Option „Open the form in maximized mode“ aktiviert, das Formular nicht im maximierten Modus geöffnet.

1. Konfigurieren Sie das URL-Feld für die Aufgabenzusammenfassung. Sie können einen Literalwert, eine Vorlage, eine Variable oder einen XPath-Ausdruck angeben.
1. Nachfolgend finden Sie ein Beispiel für die Anzeige von Informationen auf der Aufgabenzusammenfassungsseite.

   * Log in to CRXDE Lite environment at `https://[server]:[port]/lc/crx/de`.
   * `Create a node`**SampleSummary **` under `/` with type `content:`. In the properties of this node, add `unstructuredsling:` of type String and value ``. In the Access Control List of this node, add an entry for `resourceTypeSampleSummaryPERM_WORKSPACE_` allowing `USERjcr:read` privileges.`
   * `Create a folder`**BeispielSummary **unter`/apps`. In the Access Control List of`/apps/SampleSummary`, add an entry for`PERM_WORKSPACE_USER`allowing`jcr:readprivileges`.
   * `Create a file `html.esp` at `/apps/`. For example, add the following lines in `SampleSummaryhtml.esp`.`

   ```
   <html>
       <body>
           <h1>Sample Summary</h1>
           <br/>
           <p>Hello Sir!
               <br/>
               This is sample summary page for this task.
           </p>
       </body>
   </html>
   ```

   * Set the value of task summary url as `/lc/content/SampleSummary.html` in Assign Task step.
   * When the task associated with this Assign Task step is opened in AEM Forms workspace, the `html.esp` at `/apps/SampleSummary` is rendered in task summary pane.


[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
