---
title: Anpassen der Aufgabendetailseite
seo-title: Customizing the task details page
description: Gehen Sie wie folgt vor, um durch Anpassen der Aufgabendetailseite in AEM Forms Workspace die Standardinformationen zu einer Aufgabe zu ändern.
seo-description: How-to customize the task details page in AEM Forms workspace to modify the default information displayed about a task.
uuid: d85fae55-8e66-4595-8560-5485622b6841
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 16e57cf6-aaa1-406d-a6ad-71ec60b15386
exl-id: 48c24442-22d2-4d1a-9462-0aba78340281
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '263'
ht-degree: 100%

---

# Anpassen der Aufgabendetailseite {#customizing-the-task-details-page}

Die Aufgabendetailseite enthält Informationen über eine Aufgabe und die zugehörigen Prozesse. Sie können jedoch die Aufgabendetailseite anpassen, um Informationen hinzuzufügen oder zu löschen.

Sie können die folgenden Informationen der Aufgabendetailseite hinzufügen:

* Verfügbare Informationen im JSON-Objekt einer Aufgabe (Abschnitt „Aufgabe“ in [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))
* Verfügbare Informationen im JSON-Objekt einer Prozessinstanz (Abschnitt „Prozessinstanz“ in [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))

So passen Sie die Aufgabendetailseite an:

1. Folgen Sie den Anweisungen unter [Generische Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Wenn Sie zusätzliche Informationen anzeigen möchten, fügen Sie der Datei `translation.json` entsprechende Schlüssel-Wert-Paare an der Stelle `todo`-Block > `details`-Block > `app`-Block > [ `required`-Block] hinzu.

   Der [ `required`-Block] verweist auf verfügbare Blöcke, wie den task-Block für Aufgabeninformationen, den process-Block für Prozessinformationen und den currentpendingtask-Block für Informationen zu ausstehenden Aufgaben.

   Um beispielsweise Informationen über „Routenauswahl erforderlich“ auf der Aufgabendetailseite hinzuzufügen, können Sie das folgende Schlüssel-Wert-Paar im Aufgabenblock hinzufügen:

   ```json
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

1. Kopieren Sie `/libs/ws/js/runtime/templates/taskdetails.html` nach `/apps/ws/js/runtime/templates/taskdetails.html`.

   Fügen Sie die neuen Informationen zu `/apps/ws/js/runtime/templates/taskdetails.html` hinzu. Beispiel:

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

   Suchen und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/taskdetails.html` durch `text!/lc/apps/ws/js/runtime/templates/taskdetails.html`.

>[!NOTE]
>
>Um die Aufgabendetailseite mit Aufgaben anzupassen, die auf der Registerkarte **Startprozess** in AEM Forms Workspace erstellt wurden, fügen Sie die neuen Informationen zu `/apps/ws/js/runtime/templates/startprocess.html` hinzu.
>
>Um neue Stile für die auf der Detailseite hinzugefügten Informationen hinzuzufügen, ändern Sie die CSS-Datei entsprechend dem Abschnitt *Änderungen der Benutzeroberfläche* in [Anpassung von Workspace](changing-locale-user-interface.md).
