---
title: Anpassen der Aufgabendetailseite
seo-title: Anpassen der Aufgabendetailseite
description: Gehen Sie wie folgt vor, um durch Anpassen der Aufgabendetailseite in AEM Forms Workspace die Standardinformationen zu einer Aufgabe zu ändern.
seo-description: Gehen Sie wie folgt vor, um durch Anpassen der Aufgabendetailseite in AEM Forms Workspace die Standardinformationen zu einer Aufgabe zu ändern.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Customizing the task details page {#customizing-the-task-details-page}

Die Aufgabendetailseite enthält Informationen über eine Aufgabe und die zugehörigen Prozesse. Sie können jedoch die Aufgabendetailseite anpassen, um Informationen hinzuzufügen oder zu löschen.

Sie können die folgenden Informationen der Aufgabendetailseite hinzufügen:

* Verfügbare Informationen im JSON-Objekt einer Aufgabe (Abschnitt „Aufgabe“ in [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))
* Verfügbare Informationen im JSON-Objekt einer Prozessinstanz (Abschnitt „Prozessinstanz“ in [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))

So passen Sie die Aufgabendetailseite an:

1. Folgen Sie den Anweisungen unter [Generische Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. To show any additional information, add corresponding key-value pairs to the `translation.json` file at `todo`block > `details`block > `app`block > [ `required`block].

   The [ `required`block] refers to available blocks, such as the task block for task information, process block for process information, and currentpendingtask block for pending tasks information.

   Um beispielsweise Informationen über „Routenauswahl erforderlich“ auf der Aufgabendetailseite hinzuzufügen, können Sie das folgende Schlüssel-Wert-Paar im Aufgabenblock hinzufügen:

   ```
   "todo" : {
       .
       .
       .
       "details" : {
           .
           .
           "task" : {
               .
               .
               "RouteSelectionRequired" : "Route Selection Required"
           }
       }
   }
   ```

   >[!NOTE]
   >
   >Fügen Sie entsprechende Schlüssel-Wert-Paare für alle unterstützten Sprachen hinzu.

1. Kopieren `/libs/ws/js/runtime/templates/taskdetails.html` nach `/apps/ws/js/runtime/templates/taskdetails.html`.

   Hinzufügen die neuen Informationen an `/apps/ws/js/runtime/templates/taskdetails.html`. Beispiel:

   ```css
   <div class="detailsContainer">
       .
       .
       <ul>
           .
           .
           <li>
               <label for="routeSelectionRequired" title="<%= $.t('todo.details.task.RouteSelectionRequired')%>"><%= $.t('todo.details.task.RouteSelectionRequired')%></label>
               <div>
                   <span id="routeSelectionRequired"><%= isRouteSelectionRequired != null ? isRouteSelectionRequired : ''%></span>
               </div>
           </li>
           .
           .
       </ul>
   </div>
   ```

1. Öffnen Sie /apps/ws/js/registry.js zur Bearbeitung.

   Search and replace `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` with `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>To customize the task details page with tasks created in the **Start Process** tab of AEM Forms workspace, add the new information to `/apps/ws/js/runtime/templates/startprocess.html`.
>
>To add new styles for the information added in the details page, modify the CSS file by using the *User interface changes* section in [Workspace Customization](changing-locale-user-interface.md).
