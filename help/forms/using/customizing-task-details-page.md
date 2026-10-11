---
title: Anpassen der Aufgabendetailseite
description: Erfahren Sie, wie Sie die Aufgabendetailseite in AEM Forms Workspace anpassen, um die Standardinformationen zu einer Aufgabe zu ändern.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 48c24442-22d2-4d1a-9462-0aba78340281
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 100%
---
# Anpassen der Aufgabendetailseite {#customizing-the-task-details-page}

Die Aufgabendetailseite enthält Informationen über eine Aufgabe und die zugehörigen Prozesse. Sie können jedoch die Aufgabendetailseite anpassen, um Informationen hinzuzufügen oder zu löschen.

Sie können die folgenden Informationen zur Aufgabendetailseite hinzufügen:

* Informationen, die im JSON-Objekt einer Aufgabe verfügbar sind (Abschnitt „Aufgabe“ unter [AEM Forms Workspace – JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))
* Informationen, die im JSON-Objekt einer Prozessinstanz verfügbar sind (Abschnitt „Prozessinstanz“ unter [AEM Forms Workspace – JSON-Objektbeschreibung](/help/forms/using/html-workspace-json-object-description.md))

So passen Sie die Aufgabendetailseite an:

1. Folgen Sie den Anweisungen unter [Generische Schritte zur Anpassung von AEM Forms Workspace](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Wenn Sie zusätzliche Informationen anzeigen möchten, fügen Sie der Datei `translation.json` entsprechende Schlüssel-Wert-Paare unter `todo`-Block > `details`-Block > `app`-Block > [`required`-Block] hinzu.

   Der [`required`-Block] verweist auf verfügbare Blöcke, wie den task-Block für Aufgabeninformationen, den process-Block für Prozessinformationen und den currentpendingtask-Block für Informationen zu ausstehenden Aufgaben.

   Um beispielsweise Informationen über „Routenauswahl erforderlich“ auf der Aufgabendetailseite hinzuzufügen, können Sie das folgende Schlüssel-Wert-Paar im task-Block hinzufügen:

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
