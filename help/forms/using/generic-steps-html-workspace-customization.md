---
title: Generische Schritte zur Anpassung von AEM Forms Workspace
description: Erste Schritte zur Anpassung der Benutzeroberfläche von Adobe Experience Manager Forms Workspace.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 45e50b47-1b36-4937-9e1a-cc7bfb953861
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 68%

---

# Generische Schritte zur Anpassung von AEM Forms Workspace {#generic-steps-for-aem-forms-workspace-customization}

Die allgemeinen Schritte zur Durchführung von Anpassungen sind:

1. Melden Sie sich bei CRXDE Lite an, indem Sie auf `https://'[server]:[port]'/lc/crx/de/index.jsp` zugreifen.
1. Erstellen Sie eine `sling:Folder` Ordner mit dem Namen `ws` at `/apps`, wenn sie nicht vorhanden ist. Um einen `sling:Folder`-Ordner zu erstellen, klicken Sie mit der rechten Maustaste auf den Ordner `apps` und wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Knoten erstellen]**. Geben Sie den Namen als `ws`Wählen Sie Typ aus als `sling:Folder`und klicken Sie auf **[!UICONTROL OK]**. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Wechseln Sie zu `/apps/ws` und navigieren Sie zur Registerkarte **[!UICONTROL Zugriffssteuerung]**.
1. Wählen Sie die Option **[!UICONTROL Repository]**. Im **[!UICONTROL Zugriffssteuerung]** Liste, klicken Sie **[!UICONTROL +]** , um einen Eintrag hinzuzufügen. Klicken Sie erneut auf **[!UICONTROL +]**.
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

   1. Navigieren Sie zum `/apps/ws` Ordner erstellen und einen Ordner mit dem Namen `css`.

   1. Im `css` Ordner erstellen, eine Datei mit dem Namen `newStyle.css`.

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

1. Ändern Sie in der Datei /apps/ws/html.jsp von

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

1. Klicks **[!UICONTROL Alle speichern]**, leeren Sie den Cache und aktualisieren Sie den AEM Forms-Arbeitsbereich.

   Greifen Sie auf die URL `https://'[server]:[port]'/lc/ws` zu und melden Sie sich mit Administrator/Kennwort-Anmeldeinformationen an. Der Browser leitet Sie zu `https://'[server]:[port]'/lc/apps/ws/index.html` weiter.
