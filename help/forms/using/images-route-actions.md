---
title: Anpassen der in Route-Aktionen verwendeten Bilder
description: Vorgehensweise zum Anpassen von Bildern, die in Route-Aktionen in LiveCycle AEM Forms Workspace verwendet werden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 687c6569-7189-4039-9c7a-bc29658a7756
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '288'
ht-degree: 100%

---

# Anpassen der in Route-Aktionen verwendeten Bilder {#customize-images-used-in-route-actions}

Um die in Route-Aktionen verwendeten Bilder anzupassen, führen Sie die Schritte in [Generische Schritte zur Anpassung](/help/forms/using/generic-steps-html-workspace-customization.md) und anschließend die Schritte in diesem Artikel durch.

## Bilder für Route-Aktionen {#images-for-route-actions}

1. Fügen Sie im CSS am folgenden Speicherort die Stile hinzu, die die Bilder für die neuen Route-Aktionen definieren:

   `/apps/ws/css/newStyle.css`

   Ein Beispiel: Fügen Sie einen neuen Stil mit dem Namen `myStyle1` wie unten gezeigt hinzu und laden Sie die Grafikdatei `myStyleIcon1.png` mithilfe eines WebDAV-Clients in den Ordner `/apps/ws/image` hoch.

   >[!NOTE]
   >
   >Weitere Informationen erhalten Sie unter [WebDAV-Zugriff](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=de).

   >[!NOTE]
   >
   >Verwenden Sie den Namen der Route-Aktion auch als den Stilnamen.

   ```css
   .myStyle1{
   
           background-image: url('../images/myStyleIcon1.png');
   
       }
   ```

## Popup für Aufgabenliste und Aufgabenaktion {#task-list-task-action-popup}

1. Erstellen Sie ein Tasklisten-Aktionspopup siehe [Erstellen von AEM Forms Workspace-Code](introduction-customizing-html-workspace.md#building-html-workspace-code). Dazu muss ein Dev-Paket verwendet werden.

1. Kopieren Sie `/libs/ws/js/runtime/templates/task.html` nach `/apps/ws/js/runtime/templates/task.html`.

1. Wenn der Name des CSS-Stils mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/task.html`:

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

1. Wenn der Name des CSS-Stils nicht mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/task.html`. Er fügt einen Stapel der `if-else`-Servlet-Bedingungen hinzu, um den Stil dem Route-Aktionsnamen zuzuordnen.

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

1. Wenn der Name des CSS-Stils mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/taskdetails.html`:

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

1. Wenn der Name des CSS-Stils nicht mit dem Namen der vom Server kommenden Route-Aktion übereinstimmt, ändern Sie den folgenden Code in `/apps/ws/js/runtime/templates/taskdetails.html`. Er fügt einen Stapel der `if-else`-Servlet-Bedingungen hinzu, um den Stil dem Route-Aktionsnamen zuzuordnen.

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

1. Öffnen Sie `/apps/ws/js/registry.js` zur Bearbeitung und suchen Sie den folgenden Text:
   `"text!/lc/libs/ws/js/runtime/templates/taskdetails.html"`

1. Ersetzen Sie den Text durch Folgendes:
   `"text!/lc/apps/ws/js/runtime/templates/taskdetails.html"`
