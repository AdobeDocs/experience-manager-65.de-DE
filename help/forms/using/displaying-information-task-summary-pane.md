---
title: Anzeigen von Informationen in der Aufgabenzusammenfassung
seo-title: Displaying information in the Task Summary pane
description: In AEM Forms Workspace kann ein Bedienfeld zur Aufgabenzusammenfassung konfiguriert werden, um die Aufgabe zusammenzufassen oder eine beliebige Website anzuzeigen.
seo-description: In AEM Forms workspace, a Task Summary pane can be configured to summarize the task or display any other web page.
uuid: 2fcc3d9f-0ec2-4250-8dc1-9746fd72ea60
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 90d0f584-b598-4b21-85d7-31da5f13d404
exl-id: 0b3087fe-a3fb-4eac-ad4b-c123526e8195
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '277'
ht-degree: 100%

---

# Anzeigen von Informationen in der Aufgabenzusammenfassung {#displaying-information-in-the-task-summary-pane}

Wenn Sie eine Aufgabe in AEM Forms Workspace öffnen, kann eine Zusammenfassung der Aufgabe in einem entsprechenden Fenster angezeigt werden. Diese zusätzlichen und wichtigen Informationen zu einer Aufgabe sind nützlich für den Endbenutzer von AEM Forms Workspace.

AEM Forms Workspace gibt Ihnen die Möglichkeit, eine Web-Seite zu wählen, die in der Aufgabenzusammenfassung angezeigt werden soll. Es kann ein Vorgang erstellt werden, um eine Aufgabenzusammenfassung mithilfe von Workbench anzuzeigen.

1. Erstellen Sie in Workbench einen Assign Task-Prozess. Weitere Informationen zum Prozess „Assign Task“ finden Sie im Dienstreferenzthema der [Workbench-Hilfe](https://help.adobe.com/de_DE/AEMForms/6.1/WorkbenchHelp/).

   >[!NOTE]
   >
   >Wenn eine Aufgabenzusammenfassungs-URL vorhanden ist, wird standardmäßig diese Ansicht statt der Formularansicht geöffnet. In diesem Fall wird, auch wenn ein Benutzer in Assign Task die Option „Open the form in maximized mode“ aktiviert, das Formular nicht im maximierten Modus geöffnet.

1. Konfigurieren Sie das URL-Feld für die Aufgabenzusammenfassung. Sie können einen Literalwert, eine Vorlage, eine Variable oder einen XPath-Ausdruck angeben.
1. Nachfolgend finden Sie ein Beispiel für die Anzeige von Informationen auf der Aufgabenzusammenfassungsseite.

   * Melden Sie sich bei der CRXDE Lite-Umgebung unter `https://'[server]:[port]'/lc/crx/de` an.
   * `Create a node`**SampleSummary** ` under `/content` with type `nt:unstructured`. In the properties of this node, add `sling:resourceType` of type String and value `SampleSummary`. In the Access Control List of this node, add an entry for `PERM_WORKSPACE_USER` allowing `jcr:read` privileges.`
   * `Create a folder`**SampleSummary** unter `/apps`. Fügen Sie in der Zugriffssteuerungsliste von `/apps/SampleSummary` einen Eintrag für `PERM_WORKSPACE_USER` hinzu, wobei die Berechtigungen `jcr:readprivileges` zugelassen werden.
   * `Create a file `html.esp` at `/apps/SampleSummary`. For example, add the following lines in `html.esp`.`

   ```html
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

   * Legen Sie im Schritt „Aufgabe zuweisen“ den Wert der Aufgabenzusammenfassungs-URL auf `/lc/content/SampleSummary.html` fest.
   * Wenn die Aufgabe, die mit diesem Schritt „Aufgabe zuweisen“ verknüpft ist, in AEM Forms Workspace geöffnet wird, wird `html.esp` in `/apps/SampleSummary` in der Aufgabenzusammenfassung gerendert.
