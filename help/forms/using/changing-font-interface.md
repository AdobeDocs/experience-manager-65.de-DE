---
title: Ändern der Schriftart auf der Benutzeroberfläche
description: So ändern Sie die Schriftarten in der Benutzeroberfläche selektiv.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 226f70f0-8eb4-4724-b496-5801dc6b436f
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 47%

---

# Ändern der Schriftart auf der Benutzeroberfläche{#changing-the-font-on-the-interface}

Sie können die in AEM Forms Workspace angezeigte Schriftart ändern. Schriftarten, die in einem bestimmten Bereich der Benutzeroberfläche verwendet werden, werden im entsprechenden Abschnitt des Stylesheets definiert. Sie können die Schriftarten in der Benutzeroberfläche selektiv ändern.

Führen Sie die Anweisungen unter [Generische Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md) aus. Befolgen Sie bei Bedarf außerdem die Schritte zum Anpassen von CSS, HTML oder beidem.

1. Ändern Sie die Schriftfamilie in einem vorhandenen Stil oder fügen Sie sie hinzu.
1. Ändern oder fügen Sie die Schriftfamilie inline für das HTML-Element hinzu.
1. Fügen Sie einen Stil hinzu und verwenden Sie ihn für das HTML-Element.

Um beispielsweise die Schriftart für den Anker-Text in der Navigationsleiste oben in Courier New zu ändern, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei CRXDE Lite an, indem Sie auf `https://'[server]:[port]'/lc/crx/de/index.jsp` zugreifen.
1. Führen Sie einen der folgenden Schritte aus:

   1. Um die Schriftfamilie in einem vorhandenen Stil zu ändern, fügen Sie Folgendes in der Datei newStyle.css unter /apps/ws/css hinzu.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, kopieren Sie die Datei `/libs/ws/js/runtime/templates/appnavigation.html` nach`/apps/ws/js/runtime/templates/appnavigation.html`.

      aktualisieren Sie die Datei „/apps/ws/js/runtime/templates/appnavigation.html“ wie folgt:

      ```jsp
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      Öffnen Sie die Datei „/apps/ws/js/registry.js“ zur Bearbeitung und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` durch `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. Um einen Stil hinzuzufügen, der die Schriftfamilie definiert, fügen Sie Folgendes in der Datei newStyle.css unter /apps/ws/css hinzu.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, fügen Sie Folgendes in der Datei &quot;appnavigation.html&quot;unter /apps/ws/js/runtime/templates hinzu.

      ```jsp
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. Starten Sie den Arbeitsbereich neu und löschen Sie den Browsercache, damit die Änderungen sichtbar sind.

![change_font_before](assets/change_font_before.png)

Obere Navigationsleiste vor Schriftartanpassung

![change_font_after](assets/change_font_after.png)

Obere Navigationsleiste nach der Schriftartanpassung
