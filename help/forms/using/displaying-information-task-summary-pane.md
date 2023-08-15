---
title: Anzeigen von Informationen in der Aufgabenzusammenfassung
seo-title: Displaying information in the Task Summary pane
description: In AEM Forms Workspace kann ein Bereich "Aufgabenzusammenfassung"konfiguriert werden, um die Aufgabe zusammenzufassen oder eine beliebige andere Webseite anzuzeigen.
seo-description: In AEM Forms workspace, a Task Summary pane can be configured to summarize the task or display any other web page.
uuid: 2fcc3d9f-0ec2-4250-8dc1-9746fd72ea60
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 90d0f584-b598-4b21-85d7-31da5f13d404
exl-id: 0b3087fe-a3fb-4eac-ad4b-c123526e8195
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 37%

---

# Anzeigen von Informationen in der Aufgabenzusammenfassung {#displaying-information-in-the-task-summary-pane}

Wenn Sie eine Aufgabe in AEM Forms Workspace öffnen, kann ein Bereich &quot;Aufgabenzusammenfassung&quot;eine Zusammenfassung der Aufgabe anzeigen. Diese zusätzlichen und relevanten Informationen für eine Aufgabe bieten dem Endbenutzer von AEM Forms Workspace einen Mehrwert.

Mit AEM Forms Workspace können Sie eine Webseite Ihrer Wahl im Bereich &quot;Aufgabenzusammenfassung&quot;anzeigen. Es kann ein Vorgang erstellt werden, um eine Aufgabenzusammenfassung mithilfe von Workbench anzuzeigen.

1. Erstellen Sie einen Prozess &quot;Assign Task&quot;in Workbench. Weitere Informationen zum Vorgang &quot;Assign Task&quot;finden Sie unter Dienstreferenz-Thema unter [Workbench-Hilfe](https://help.adobe.com/de_DE/AEMForms/6.1/WorkbenchHelp/).

   >[!NOTE]
   >
   >Wenn eine TaskSummary-URL vorhanden ist, wird die Ansicht &quot;Task Summary&quot;standardmäßig anstelle der Ansicht &quot;Form&quot;geöffnet. In diesem Fall wird das Formular nicht im maximierten Modus geöffnet, selbst wenn ein Benutzer die Option &quot;Formular im maximierten Modus öffnen&quot;in &quot;Aufgabe zuweisen&quot;aktiviert hat.

1. Konfigurieren Sie das Feld &quot;Task Summary URL&quot;. Sie können einen Literalwert, eine Vorlage, eine Variable oder einen XPath-Ausdruck angeben.
1. Nachfolgend finden Sie ein Beispiel für die Anzeige der Informationen auf der Seite &quot;Aufgabenzusammenfassung&quot;.

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
