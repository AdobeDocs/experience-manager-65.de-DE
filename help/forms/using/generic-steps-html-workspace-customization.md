---
title: Generische Schritte zur Anpassung von AEM Forms Workspace
description: Erste Schritte zur Anpassung der Adobe Experience Manager Forms Workspace-Benutzeroberfläche.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 45e50b47-1b36-4937-9e1a-cc7bfb953861
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
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
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 100%
---
# Generische Schritte zur Anpassung von AEM Forms Workspace {#generic-steps-for-aem-forms-workspace-customization}

Für jede Anpassung gelten die folgenden generischen Schritte:

1. Melden Sie sich bei CRXDE Lite an, indem Sie auf `https://'[server]:[port]'/lc/crx/de/index.jsp` zugreifen.
1. Erstellen Sie einen Ordner `sling:Folder` mit dem Namen `ws` unter `/apps`, falls er noch nicht existiert. Um einen Ordner `sling:Folder` zu erstellen, klicken Sie mit der rechten Maustaste auf den Ordner `apps` und wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Knoten erstellen]**. Geben Sie den Namen als `ws` an, wählen Sie als Typ `sling:Folder` und klicken Sie auf **[!UICONTROL OK]**. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Wechseln Sie zu `/apps/ws` und navigieren Sie zur Registerkarte **[!UICONTROL Zugriffssteuerung]**.
1. Wählen Sie die Option **[!UICONTROL Repository]**. Klicken Sie in der Liste **[!UICONTROL Zugriffssteuerung]** auf **[!UICONTROL +]**, um einen Eintrag hinzuzufügen. Klicken Sie erneut auf **[!UICONTROL +]**.
1. Suchen Sie den Prinzipal **PERM_WORKSPACE_USER** und wählen Sie ihn aus.

   ![Wählen Sie PERM_WORKSPACE_USER als Teil von allgemeinen Schritten, um HTML Workspace anzupassen](assets/perm_workspace_user.png)

1. Erteilen Sie dem Prinzipal die Berechtigung `jcr:read`.
1. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Kopieren Sie die Dateien `GET.jsp`, `index` und `html.jsp` aus dem Ordner `/libs/ws` in den Ordner `/apps/ws`.
1. Kopieren Sie den Ordner `/libs/ws/locales` in den Ordner `/apps/ws`. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Aktualisieren Sie die Verweise und relativen Pfade in der Datei `GET.jsp`, wie unten gezeigt, und klicken Sie auf **[!UICONTROL Alles speichern]**.

   ```javascript
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Führen Sie die folgenden Schritte für CSS-Anpassungen aus:

   1. Navigieren Sie zum Ordner `/apps/ws` und erstellen Sie einen Ordner mit dem Namen `css`.

   1. Erstellen Sie im Ordner `css` eine Datei mit dem Namen `newStyle.css`.

   1. Öffnen Sie `/apps/ws/html`.jsp und ändern Sie von

   ```javascript
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   in

   ```javascript
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >Platzieren Sie den Eintrag für die benutzerdefinierte CSS-Datei hinter demjenigen für die Datei „style.css“, wie oben gezeigt.

1. Ändern Sie in der Datei „apps/ws/html.jsp“ von

   ```jsp
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   in

   ```jsp
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Gehen Sie folgendermaßen vor:

   1. Erstellen Sie in `/apps/ws` einen Ordner mit dem Namen `js`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Erstellen Sie in `/apps/ws/js` einen Ordner mit dem Namen `libs`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Kopieren Sie den Ordner `/libs/ws/js/libs/jqueryui` nach `/apps/ws/js/libs`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Führen Sie die folgenden Schritte für HTML-Anpassungen aus:

   1. Erstellen Sie unter `/apps/ws/js` einen Ordner mit dem Namen `runtime`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Erstellen Sie unter `/apps/ws/js/runtime` einen Ordner mit dem Namen `templates`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Kopieren Sie `/libs/ws/js/main.js` nach `/apps/ws/js/main.js`.

   1. Kopieren Sie /libs/ws/js/registry.js nach `/apps/ws/js/registry.js`.

1. Klicken Sie auf **[!UICONTROL Alle speichern]**, löschen Sie den Cache und aktualisieren Sie den AEM Forms Workspace.

   Greifen Sie auf die URL `https://'[server]:[port]'/lc/ws` zu und melden Sie sich mit Administrator/Kennwort-Anmeldeinformationen an. Der Browser leitet Sie zu `https://'[server]:[port]'/lc/apps/ws/index.html` weiter.
