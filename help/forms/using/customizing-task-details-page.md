---
title: Anpassen der Aufgabendetailseite
description: Gehen Sie wie folgt vor, um die Aufgabendetailseite in AEM Forms Workspace anzupassen, um die Standardinformationen zu einer Aufgabe zu ändern.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 48c24442-22d2-4d1a-9462-0aba78340281
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 30%

---

# Anpassen der Aufgabendetailseite {#customizing-the-task-details-page}

Die Aufgabendetailseite enthält Informationen zu einer Aufgabe und ihren Prozessen. Sie können jedoch die Aufgabendetailseite anpassen, um Informationen hinzuzufügen oder zu löschen.

Sie können der Aufgabendetailseite die folgenden Informationen hinzufügen:

* Im JSON-Objekt einer Aufgabe verfügbare Informationen (Abschnitt &quot;Aufgabe&quot;unter [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))
* Informationen, die im JSON-Objekt einer Prozessinstanz verfügbar sind (Abschnitt &quot;Prozessinstanz&quot;unter [AEM Forms Workspace JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))

So passen Sie die Aufgabendetailseite an:

1. Folgen [Generische Schritte zur Anpassung von AEM Forms Workspace.](/help/forms/using/generic-steps-html-workspace-customization.md)
1. Um weitere Informationen anzuzeigen, fügen Sie der `translation.json` Datei unter `todo`block > `details`block > `app`block > [`required`block].

   Die [`required`block] bezieht sich auf verfügbare Bausteine, wie z. B. den Aufgabenblock für Aufgabeninformationen, den Prozessblock für Prozessinformationen und den derzeit ausstehenden Aufgabenblock für Informationen zu ausstehenden Aufgaben.

   Um beispielsweise Informationen zur Routenauswahl erforderlich auf der Aufgabendetailseite hinzuzufügen, können Sie das folgende Schlüssel-Wert-Paar zum Aufgabenblock hinzufügen:

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
