---
title: Ändern der Schriftart auf der Benutzeroberfläche
seo-title: Ändern der Schriftart auf der Benutzeroberfläche
description: Die Schriftarten auf der Benutzeroberfläche selektiv ändern
seo-description: Die Schriftarten auf der Benutzeroberfläche selektiv ändern
uuid: 421fdd24-441a-4092-8c52-f3ed3d5d5671
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 9fcb80b4-cbc2-48a5-afd1-4f3bc50bc503
docset: aem65
exl-id: 226f70f0-8eb4-4724-b496-5801dc6b436f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 79%

---

# Ändern der Schriftart auf der Benutzeroberfläche{#changing-the-font-on-the-interface}

Sie können die Schriftart ändern, die in AEM Forms Workspace angezeigt wird. Schriftarten, die in einem bestimmten Bereich der Benutzeroberfläche verwendet werden, werden im entsprechenden Abschnitt des Stylesheets definiert. Sie können die Schriftarten auf der Benutzeroberfläche selektiv ändern.

Führen Sie die [Generischen Schritte zur Anpassung von AEM Forms Workspace](../../forms/using/generic-steps-html-workspace-customization.md) aus und führen Sie je nach Ihren Anforderungen die Schritte zum Anpassen von CSS, HTML oder beidem aus.

1. Ändern Sie die Schriftfamilie in einem vorhandenen Stil oder fügen Sie sie hinzu.
1. Ändern Sie die Schriftfamilie inline für das HTML-Element oder fügen Sie sie hinzu.
1. Fügen Sie einen Stil hinzu und verwenden Sie ihn für das HTML-Element.

Um beispielsweise die Schriftart für den Anker-Text in der Navigationsleiste oben in Courier New zu ändern, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei CRXDE Lite an, indem Sie auf `https://'[server]:[port]'/lc/crx/de/index.jsp` zugreifen.
1. Führen Sie einen der folgenden Schritte aus:

   1. Um die Schriftfamilie in einem vorhandenen Stil zu ändern, fügen Sie Folgendes in der Datei „newStyle.css“ bei „/apps/ws/css“ hinzu.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, kopieren Sie die Datei `/libs/ws/js/runtime/templates/appnavigation.html` in `/apps/ws/js/runtime/templates/appnavigation.html`.

      aktualisieren Sie die Datei „/apps/ws/js/runtime/templates/appnavigation.html“ wie folgt:

      ```jsp
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      Öffnen Sie die Datei /apps/ws/js/registry.js zur Bearbeitung und ersetzen Sie `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` durch `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. Um einen Stil hinzuzufügen, der die Schriftfamilie definiert, fügen Sie Folgendes in der Datei „newStyle.css“ bei „/apps/ws/css“ hinzu.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      Um die Schriftfamilie für das HTML-Element inline hinzuzufügen, fügen Sie Folgendes in der Datei „appnavigation.html“ bei „/apps/ws/js/runtime/templates“ hinzu.

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

1. Starten Sie Workspace neu und löschen Sie den Browser-Cache, damit die Änderungen sichtbar werden.

![change_font_before](assets/change_font_before.png)

Obere Navigationsleiste vor Schriftartanpassung

![change_font_after](assets/change_font_after.png)

Obere Navigationsleiste nach der Schriftartanpassung
