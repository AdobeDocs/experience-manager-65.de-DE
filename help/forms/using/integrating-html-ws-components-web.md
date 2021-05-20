---
title: Integrieren von AEM Forms Workspace-Komponenten in Webanwendungen
seo-title: Integrieren von AEM Forms Workspace-Komponenten in Webanwendungen
description: Wiederverwenden von AEM Forms Workspace-Komponenten in eigenen Webapps, um Funktion zu nutzen und Integration bereitzustellen.
seo-description: Wiederverwenden von AEM Forms Workspace-Komponenten in eigenen Webapps, um Funktion zu nutzen und Integration bereitzustellen.
uuid: bb9b8aa0-3f41-4f44-8eb7-944e778ee8a6
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 6be87939-007e-42c7-8a41-e34ac2b8bed4
exl-id: bb4a500d-c34f-4586-83f0-ad7ef69b4fb1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 74%

---

# Integrieren von AEM Forms Workspace-Komponenten in Webanwendungen {#integrating-aem-forms-workspace-components-in-web-applications}

Sie können die AEM Forms Workspace [Komponenten](/help/forms/using/description-reusable-components.md) in Ihrer eigenen Webanwendung verwenden. In der folgenden Beispielimplementierung werden Komponenten aus einem AEM Forms Workspace-Dev-Paket verwendet, das auf einer CRX™-Instanz installiert ist, um eine Webanwendung zu erstellen. Passen Sie die unten gezeigte Lösung an Ihre spezifischen Anforderungen an. Die Beispielimplementierung verwendet die Komponenten `UserInfo`, `FilterList` und `TaskList`innerhalb eines Webportals erneut.

1. Melden Sie sich bei der CRXDE Lite-Umgebung unter `https://'[server]:[port]'/lc/crx/de/` an. Stellen Sie sicher, dass AEM Forms Workpace Dev-Paket installiert ist.
1. Erstellen Sie einen Pfad `/apps/sampleApplication/wscomponents`.
1. Kopieren Sie CSS, Bilder, js/libs, js/runtime und js/registry.js

   * von `/libs/ws`
   * in `/apps/sampleApplication/wscomponents`.

1. Erstellen Sie im Ordner /apps/sampleApplication/wscomponents/js eine Datei mit dem Namen demomain.js. Kopieren Sie Code aus /libs/ws/js/main.js in demomain.js.
1. Entfernen Sie in demomain.js den Code zum Initialisieren des Routers und fügen Sie folgenden Code hinzu:

   ```javascript
   require(['initializer','runtime/util/usersession'],
       function(initializer, UserSession) {
           UserSession.initialize(
               function() {
                   // Render all the global components
                   initializer.initGlobal();
               });
       });
   ```

1. Erstellen Sie einen Knoten unter /content mit dem Namen `sampleApplication` und geben Sie `nt:unstructured` ein. Fügen Sie in den Eigenschaften dieses Knotens `sling:resourceType` des Typs String und des Werts `sampleApplication` hinzu. Fügen Sie der Zugriffsteuerungsliste dieses Knotens den Eintrag `PERM_WORKSPACE_USER` hinzu, um jcr:read-Zugriff zuzulassen. Fügen Sie außerdem in der Zugriffssteuerungsliste von `/apps/sampleApplication` einen Eintrag für `PERM_WORKSPACE_USER` hinzu, um jcr:read-Berechtigungen zuzulassen.
1. Aktualisieren Sie in `/apps/sampleApplication/wscomponents/js/registry.js` Pfade für Vorlagenwerte von `/lc/libs/ws/` auf `/lc/apps/sampleApplication/wscomponents/` .
1. Fügen Sie in der JSP-Datei Ihrer Portalstartseite unter `/apps/sampleApplication/GET.jsp` den folgenden Code hinzu, um die erforderlichen Komponenten in das Portal einzuschließen.

   ```jsp
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div>
   <div class="filterListView gcomponent" data-name="filterlist"></div>
   <div class="taskListView gcomponent" data-name="tasklist"></div>
   ```

   Schließen Sie außerdem die CSS-Dateien ein, die für die AEM Forms Workspace-Komponenten erforderlich sind.

   >[!NOTE]
   >
   >Beim render-Prozess wird jede Komponente dem Komponenten-Tag (der Klasse gcomponent) hinzugefügt. Stellen Sie sicher, dass Ihre Startseite die betreffenden Tags enthält. Weitere Informationen zu diesen Basissteuerungstags finden Sie in der Datei von AEM Forms Workspace `html.jsp`.

1. Um die Komponenten anzupassen, können Sie die vorhandenen Ansichten für die erforderliche Komponente wie folgt erweitern:

   ```javascript
   define([
       ‘jquery’,
       ‘underscore’,
       ‘backbone’,
       ‘runtime/views/userinfo'],
       function($, _, Backbone, UserInfo){
           var demoUserInfo = UserInfo.extend({
               //override the functions to customize the functionality
               render: function() {
                   UserInfo.prototype.render.call(this); // call the render function of the super class
                   …
                   //other tasks
                   …
               }
           });
           return demoUserInfo;
   });
   ```

1. Ändern Sie das Portal-CSS, um das Layout, die Positionierung und den Stil der erforderlichen Komponenten im Portal zu konfigurieren. Beispiel: Sie möchten die Hintergrundfarbe Schwarz in diesem Portal behalten, um die Komponente userInfo gut sichtbar darzustellen. Sie können dies tun, indem Sie die Hintergrundfarbe in `/apps/sampleApplication/wscomponents/css/style.css` wie folgt ändern:

   ```css
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC
       position: relative;
       margin: 0 auto;
   }
   ```
