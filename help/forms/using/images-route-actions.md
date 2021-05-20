---
title: In Route-Aktionen verwendete Bilder anpassen
seo-title: In Route-Aktionen verwendete Bilder anpassen
description: Vorgehensweise zum Anpassen von Bildern, die in Route-Aktionen in LiveCycle AEM Forms Workspace verwendet werden.
seo-description: Vorgehensweise zum Anpassen von Bildern, die in Route-Aktionen in LiveCycle AEM Forms Workspace verwendet werden.
uuid: 42608376-587e-4b57-a9d5-8f9ebd981426
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 10158c13-47b4-43e3-ac47-690f3cbab158
exl-id: 687c6569-7189-4039-9c7a-bc29658a7756
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 53%

---

# In Route-Aktionen verwendete Bilder anpassen {#customize-images-used-in-route-actions}

Um die in Route-Aktionen verwendeten Bilder anzupassen, führen Sie die Schritte in [Generische Schritte zur Anpassung](/help/forms/using/generic-steps-html-workspace-customization.md) und anschließend die Schritte in diesem Artikel durch.

## Bilder für Route-Aktionen  {#images-for-route-actions}

1. Fügen Sie in CSS am folgenden Speicherort die Stile hinzu, die die Bilder für die neuen Route-Aktionen definieren:

   `/apps/ws/css/newStyle.css`

   Beispiel: Fügen Sie einen neuen Stil mit dem Namen `myStyle1`hinzu, wie unten dargestellt, und laden Sie die Bilddatei `myStyleIcon1.png` mithilfe eines WebDAV-Clients in den Ordner `/apps/ws/image`s hoch.

   >[!NOTE]
   >
   >Weitere Informationen zum WebDAV-Zugriff finden Sie unter [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

   >[!NOTE]
   >
   >Verwenden Sie den Route-Aktionsnamen auch als den Stilnamen.

   ```css
   .myStyle1{
   
           background-image: url('../images/myStyleIcon1.png');
   
       }
   ```

## Popup bei Tasklist-Aufgabenaktion  {#task-list-task-action-popup}

1. Erstellen Sie ein Tasklisten-Aktionspopup (siehe [Erstellen von AEM Forms Workspace-Code](introduction-customizing-html-workspace.md#building-html-workspace-code). Dazu muss ein Dev-Paket verwendet werden.)

1. Kopieren Sie `/libs/ws/js/runtime/templates/task.html` nach `/apps/ws/js/runtime/templates/task.html`.

1. Wenn der Name des CSS-Stils mit dem Route-Aktionsnamen vom Server übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/task.html`:

   ```jsp
   <%if(routeList == null){%>
               <li>
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li>
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   
   To
   
   <%if(routeList == null){%>
               <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
               </li>
               <%}else{%>
               <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
               <li class="<%= availableCommands.directCommands[i]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                   <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
               </li>
               <%}%>
               <%}%>
   ```

1. Wenn der Name des CSS-Stils sich vom Route-Aktionsnamen des Servers unterscheidet, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/task.html`. Er fügt einen Stapel der `if-else`-Servlet-Bedingungen hinzu, um den Stil dem Route-Aktionsnamen zuzuordnen.

```jsp
<%if(routeList == null){%>
            <li>
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
            <li>
                <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
            </li>
            <%}%>
            <%}%>

To

<%if(routeList == null){%>
            <li class="<%= availableCommands.directCommands[0]%>" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0]+'.value')%>">
                <a href="javascript:void(0);" title="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%>" value="<%= availableCommands.directCommands[0]%>" data-action="route"><%= $.t('taskaction.directcommand.'+availableCommands.directCommands[0])%></a>
            </li>
            <%}else{%>
            <%for(var i = 0; i<availableCommands.directCommands.length; i++){%>
                <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                     <li class="myStyle1" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                     <li class="myStyle2" alt="<%= $.t('taskaction.directcommand.'+availableCommands.directCommands[i]+'.value')%>">
                         <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                     </li>
                <%}%>
            <%}%>
            <%}%>
```

## Popup bei Aufgabendetails-Aufgabenaktion {#task-details-task-action-popup}

1. Kopieren Sie `/libs/ws/js/runtime/templates/taskdetails.html` nach `/apps/ws/js/runtime/templates/taskdetails.html`.

1. Wenn der Name des CSS-Stils mit dem Route-Aktionsnamen vom Server übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/taskdetails.html`:

   ```jsp
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                       <%}%>
   ```

1. Wenn der Name des CSS-Stils sich vom Route-Aktionsnamen des Servers unterscheidet, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/taskdetails.html`. Er fügt einen Stapel der `if-else`-Servlet-Bedingungen hinzu, um den Stil dem Route-Aktionsnamen zuzuordnen.

   ```jsp
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                           <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route"><%= availableCommands.directCommands[i]%></a>
                           </li>
                       <%}%>
   
   To
   
   <%for (var i = 0; i < availableCommands.directCommands.length; i++) {%>
                   <%if(availableCommands.directCommands[i].equals("myAction1")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle1" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}else if(availableCommands.directCommands[i].equals("myAction2")){%>
                       <li class="routeAction">
                               <a href="javascript:void(0);" title="<%= availableCommands.directCommands[i]%>" value="<%= availableCommands.directCommands[i]%>" data-action="route">
                               <i class="myStyle2" value="<%= availableCommands.directCommands[i]%>" data-action="route"/>
                               </a>
                           </li>
                   <%}%>
               <%}%>
   ```

1. Öffnen Sie `/apps/ws/js/registry.js` zur Bearbeitung und suchen Sie nach folgendem Text:
   `"text!/lc/libs/ws/js/runtime/templates/taskdetails.html"`

1. Ersetzen Sie den Text durch Folgendes:
   `"text!/lc/apps/ws/js/runtime/templates/taskdetails.html"`
