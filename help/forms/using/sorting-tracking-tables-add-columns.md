---
title: Anpassen von Verfolgungstabellen
seo-title: Anpassen von Verfolgungstabellen
description: Gehen Sie wie folgt vor, um die Anzeige der Details von Benutzerprozessen in der Aufgabentabelle zu speichern, die auf der Registerkarte „Verfolgung“ in AEM Forms Workspace angezeigt wird.
seo-description: Gehen Sie wie folgt vor, um die Anzeige der Details von Benutzerprozessen in der Aufgabentabelle zu speichern, die auf der Registerkarte „Verfolgung“ in AEM Forms Workspace angezeigt wird.
uuid: 13d6ebf2-99d5-434f-85f9-b0cba5f5751a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: bb7a6e9f-4f28-4d97-8a0c-949259fd6857
exl-id: 9ab657cc-fa8e-4168-8a68-e38ac5c51b29
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 79%

---

# Anpassen von Verfolgungstabellen{#customize-tracking-tables}

Die Registerkarte &quot;Tracking&quot;in AEM Forms Workspace wird verwendet, um die Details der Prozessinstanzen anzuzeigen, an denen der angemeldete Benutzer beteiligt ist. Um die Verfolgungstabellen anzuzeigen, wählen Sie zunächst einen Prozessnamen im linken Fensterbereich aus, um die zugehörige Instanzenliste im mittleren Bereich anzuzeigen. Wählen Sie eine Prozessinstanz aus, um im rechten Fensterbereich eine Tabelle von Aufgaben anzuzeigen, die von dieser Instanz generiert werden. Standardmäßig enthalten die Tabellenspalten die folgenden Aufgabenattribute (das entsprechende Attribut im Aufgabenmodell wird in Klammern angegeben):

* ID ( `taskId`)
* Name ( `stepName`)
* Anweisungen ( `instructions`)
* Ausgewählte Aktion ( `selectedRoute`)
* Erstellungszeit ( `createTime`)
* Abschlusszeit ( `completeTime`)
* Inhaber ( `currentAssignment.queueOwner`)

Die übrigen Attribute im Aufgabenmodell, die für die Anzeige in der Aufgabentabelle verfügbar sind, lauten:

<table>
 <tbody>
  <tr>
   <td><p>actionInstanceId</p> </td>
   <td><p>isOpenFullScreen</p> </td>
   <td><p>reminderCount</p> </td>
  </tr>
  <tr>
   <td><p>classOfTask</p> </td>
   <td><p>isOwner</p> </td>
   <td><p>routeList</p> </td>
  </tr>
  <tr>
   <td><p>consultGroupId</p> </td>
   <td><p>isRouteSelectionRequired</p> </td>
   <td><p>savedFormCount</p> </td>
  </tr>
  <tr>
   <td><p>contentType</p> </td>
   <td><p>isShowAttachments</p> </td>
   <td><p>serializedImageTicket</p> </td>
  </tr>
  <tr>
   <td><p>createTime</p> </td>
   <td><p>isStartTask</p> </td>
   <td><p>serviceName</p> </td>
  </tr>
  <tr>
   <td><p>creationId</p> </td>
   <td><p>isVisible</p> </td>
   <td><p>serviceTitle</p> </td>
  </tr>
  <tr>
   <td><p>currentAssignment</p> </td>
   <td><p>nextReminder</p> </td>
   <td><p>showACLActions</p> </td>
  </tr>
  <tr>
   <td><p>deadline</p> </td>
   <td><p>numForms</p> </td>
   <td><p>showDirectActions</p> </td>
  </tr>
  <tr>
   <td><p>description</p> </td>
   <td><p>numFormsToBeSaved</p> </td>
   <td><p>status</p> </td>
  </tr>
  <tr>
   <td><p>displayName</p> </td>
   <td><p>outOfOfficeUserId</p> </td>
   <td><p>summaryUrl</p> </td>
  </tr>
  <tr>
   <td><p>forwardGroupId</p> </td>
   <td><p>outOfOfficeUserName</p> </td>
   <td><p>supportsSave</p> </td>
  </tr>
  <tr>
   <td><p>isApprovalUI</p> </td>
   <td><p>priority</p> </td>
   <td><p>taskACL</p> </td>
  </tr>
  <tr>
   <td><p>isCustomUI</p> </td>
   <td><p>processInstanceId</p> </td>
   <td><p>taskFormType</p> </td>
  </tr>
  <tr>
   <td><p>isDefaultImage</p> </td>
   <td><p>processInstanceStatus</p> </td>
   <td><p>taskUserInfo</p> </td>
  </tr>
  <tr>
   <td><p>isLocked</p> </td>
   <td><p>processVariables</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p>isMustOpenToComplete</p> </td>
   <td><p>readerSubmitOptions</p> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Für die folgenden Anpassungen in der Aufgabentabelle müssen Sie semantische Änderungen im Quellcode vornehmen. Siehe [Einführung in das Anpassen von AEM Forms Workspace](/help/forms/using/introduction-customizing-html-workspace.md), wie Sie semantische Änderungen mit dem Workspace-SDK vornehmen und ein minimiertes Paket aus der geänderten Quelle erstellen können.

## Ändern von Tabellenspalten und ihrer Reihenfolge {#changing-table-columns-and-their-order}

1. Um die in der Tabelle angezeigten Aufgabenattribute und ihre Reihenfolge zu ändern, konfigurieren Sie die Datei /ws/js/runtime/templates/processinstancehistory.html:

   ```html
   <table>
       <thead>
           <tr>
               <!-- put the column headings in order here, for example-->
               <th><%= $.t('history.fixedTaskTableHeader.taskName')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskInstructions')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskRoute')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskCreateTime')%></th>
               <th><%= $.t('history.fixedTaskTableHeader.taskCompleteTime')%></th>
           </tr>
       </thead>
   </table>
   ```

   ```html
   <table>
       <tbody>
           <%_.each(obj, function(task){%>
           <tr>
               <!-- Put the task attributes in the order of headings, for example -->
               <td><%= task.stepName %></td>
               <td><%= task.instructions %></td>
               <td><%= !task.selectedRoute?'':(task.selectedRoute=='null'?'Default':task.selectedRoute) %></td>
               <td><%= task.createTime?task.formattedCreateTime:'' %></td>
               <td><%= task.completeTime? task.formattedCompleteTime:'' %></td>
           </tr>
           <%});%>
       </tbody>
   </table>
   ```

## Sortieren einer Verfolgungstabelle {#sorting-a-tracking-table}

So sortieren Sie die Aufgabenlistentabelle durch Klicken auf die Spaltenüberschrift:

1. Registrieren Sie einen Klick-Handler für `.fixedTaskTableHeader th` in der Datei `js/runtime/views/processinstancehistory.js`.

   ```javascript
   events: {
       //other handlers
       "click .fixedTaskTableHeader th": "onTaskTableHeaderClick",
       //other handlers
   }
   ```

   Rufen Sie im -Handler die Funktion `onTaskTableHeaderClick` von `js/runtime/util/history.js` auf.

   ```javascript
   onTaskTableHeaderClick: function (event) {
           history.onTaskTableHeaderClick(event);
   }
   ```

1. Zeigen Sie die `TaskTableHeaderClick`-Methode in `js/runtime/util/history.js` an.

   Die Methode sucht nach dem task-Attribut im Klick-Ereignis, sortiert die tasklist nach diesem Attribut und gibt die Aufgabentabelle mit der sortierten tasklist aus.

   Die Sortierung erfolgt mit der Backbone-Sortierfunktion auf der tasklist-Sammlung, indem eine Komparator-Funktion bereitgestellt wird.

   ```javascript
       return {
           //other methods
           onTaskTableHeaderClick  : onTaskTableHeaderClick,
           //other methods
       };
   ```

   ```javascript
   onTaskTableHeaderClick = function (event) {
           var target = $(event.target),
            comparator,
               attribute;
           if(target.hasClass('taskName')){
            attribute = 'stepName';
           } else if(target.hasClass('taskInstructions')){
               attribute = 'instructions';
           } else if(target.hasClass('taskRoute')){
               attribute = 'selectedRoute';
           } else if(target.hasClass('taskCreateTime')){
               attribute = 'createTime';
           } else if(target.hasClass('taskCompleteTime')){
               attribute = 'completeTime';
           }
           taskList.comparator = function (task) {
            return task.get(attribute);
           };
           taskList.sort();
           render();
       };
   ```
