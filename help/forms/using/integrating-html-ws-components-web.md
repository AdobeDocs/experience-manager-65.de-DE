---
title: Integrieren von AEM Forms Workspace-Komponenten in Web-Anwendungen
description: Wiederverwenden von AEM Forms Workspace-Komponenten in Ihren eigenen Web-Anwendungen, um Funktionen zu nutzen und eine enge Integration zu ermöglichen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: bb4a500d-c34f-4586-83f0-ad7ef69b4fb1
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 91%
---
# Integrieren von AEM Forms Workspace-Komponenten in Web-Anwendungen {#integrating-aem-forms-workspace-components-in-web-applications}

Sie können AEM Forms Workspace-[Komponenten](/help/forms/using/description-reusable-components.md) in Ihrer eigenen Web-Anwendung verwenden. In der folgenden Beispielimplementierung werden Komponenten aus einem AEM Forms-Workspace-Entwicklungspaket genutzt, das auf einer CRX™-Instanz installiert ist, um eine Web-Anwendung zu erstellen. Passen Sie die unten gezeigte Lösung an Ihre Anforderungen an. In der Beispielimplementierung werden die Komponenten `UserInfo`, `FilterList` und `TaskList` innerhalb eines Webportals wiederverwendet.

1. Melden Sie sich in der CRXDE Lite-Umgebung unter `https://'[server]:[port]'/lc/crx/de/` an. Stellen Sie sicher, dass AEM Forms Workpace Dev-Paket installiert ist.
1. Erstellen Sie einen Pfad `/apps/sampleApplication/wscomponents`.
1. Kopieren Sie CSS, Bilder, js/libs, js/runtime und js/registry.js

   * von `/libs/ws`
   * zu `/apps/sampleApplication/wscomponents`.

1. Erstellen Sie eine Datei „demomain.js“ im Ordner /apps/sampleApplication/wscomponents/js. Kopieren Sie den Code aus /libs/ws/js/main.js in „demomain.js“.
1. Entfernen Sie in „demomain.js“ den Code zum Initialisieren des Routers und fügen Sie den folgenden Code hinzu:

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

1. Erstellen Sie einen Knoten unter „/content“ mit dem Namen `sampleApplication` und dem Typ `nt:unstructured`. Fügen Sie in den Eigenschaften dieses Knotens `sling:resourceType` vom Typ String und dem Wert `sampleApplication` hinzu. Fügen Sie der Zugriffssteuerungsliste dieses Knotens den Eintrag für hinzu, `PERM_WORKSPACE_USER` jcr:read-Berechtigungen zulässt. Fügen Sie außerdem in der Zugriffssteuerungsliste von `/apps/sampleApplication` einen Eintrag für `PERM_WORKSPACE_USER` hinzu, der JCR3:readBerechtigungen zulässt.
1. Aktualisieren Sie in `/apps/sampleApplication/wscomponents/js/registry.js` die Pfade `/lc/libs/ws/` zu `/lc/apps/sampleApplication/wscomponents/` für die Vorlagenwerte.
1. Fügen Sie in die JSP-Datei Ihrer Portal-Startseite unter `/apps/sampleApplication/GET.jsp` den folgenden Code ein, um die erforderlichen Komponenten innerhalb des Portals aufzunehmen.

   ```jsp
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div>
   <div class="filterListView gcomponent" data-name="filterlist"></div>
   <div class="taskListView gcomponent" data-name="tasklist"></div>
   ```

   Schließen Sie auch die CSS-Dateien ein, die für die AEM Forms Workspace-Komponenten erforderlich sind.

   >[!NOTE]
   >
   >Jede Komponente wird beim Rendern zum Komponenten-Tag (mit Klasse „gcomponent“) hinzugefügt. Stellen Sie sicher, dass Ihre Startseite diese Tags enthält. Weitere Informationen zu diesen Basissteuerungstags finden Sie in der Datei von AEM Forms Workspace `html.jsp`.

1. Um die Komponenten anzupassen, können Sie die vorhandenen Ansichten für die erforderliche Komponente wie folgt erweitern:

   ```javascript
   define([
       'jquery',
       'underscore',
       'backbone',
       'runtime/views/userinfo'],
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

1. Ändern Sie das Portal-CSS, um das Layout, die Positionierung und den Stil der erforderlichen Komponenten im Portal zu konfigurieren. Sie möchten beispielsweise die Hintergrundfarbe für dieses Portal schwarz halten, um die Komponente „userInfo“ gut sichtbar darzustellen. Sie können dies tun, indem Sie die Hintergrundfarbe in `/apps/sampleApplication/wscomponents/css/style.css` wie folgt ändern:

   ```css
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC
       position: relative;
       margin: 0 auto;
   }
   ```
