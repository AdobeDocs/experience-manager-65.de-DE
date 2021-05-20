---
title: Generische Schritte zur Anpassung von AEM Forms Workspace
seo-title: Generische Schritte zur Anpassung von AEM Forms Workspace
description: Erste Schritte zur Anpassung der AEM Forms Workspace-Benutzeroberfläche.
seo-description: Erste Schritte zur Anpassung der AEM Forms Workspace-Benutzeroberfläche.
uuid: da6310b4-1c58-468d-85c6-975fd2c141f9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: dd3218c4-2bb2-40fc-9141-5823b0ea4224
docset: aem65
exl-id: 45e50b47-1b36-4937-9e1a-cc7bfb953861
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 40%

---

# Generische Schritte zur Anpassung von AEM Forms Workspace {#generic-steps-for-aem-forms-workspace-customization}

Für jede Anpassung gelten die folgenden generischen Schritte:

1. Melden Sie sich bei CRXDE Lite an, indem Sie auf `https://'[server]:[port]'/lc/crx/de/index.jsp` zugreifen.
1. Erstellen Sie einen Ordner `sling:Folder` mit dem Namen `ws` unter `/apps`, falls noch nicht vorhanden. Um einen Ordner `sling:Folder` zu erstellen, klicken Sie mit der rechten Maustaste auf den Ordner `apps` und wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Knoten erstellen]** aus. Geben Sie den Namen als `ws` ein, wählen Sie den Typ als `sling:Folder` aus und klicken Sie auf **[!UICONTROL OK]**. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Navigieren Sie zu `/apps/ws` und navigieren Sie zur Registerkarte **[!UICONTROL Zugriffssteuerung]** .
1. Wählen Sie die Option **[!UICONTROL Repository]** aus. Klicken Sie in der Liste **[!UICONTROL Zugriffssteuerung]** auf **[!UICONTROL +]** , um einen neuen Eintrag hinzuzufügen. Klicken Sie erneut auf **[!UICONTROL +]**.
1. Suchen und wählen Sie den Prinzipal **PERM_WORKSPACE_USER** aus.

   ![Wählen Sie PERM_WORKSPACE_USER als Teil von allgemeinen Schritten, um HTML Workspace anzupassen](assets/perm_workspace_user.png)

1. Weisen Sie dem Prinzipal die Berechtigung `jcr:read` zu.
1. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Kopieren Sie die Dateien `GET.jsp`, `index` und `html.jsp` aus dem Ordner `/libs/ws` in den Ordner `/apps/ws` .
1. Kopieren Sie den Ordner `/libs/ws/locales` im Ordner `/apps/ws` . Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. Aktualisieren Sie die Verweise und relativen Pfade in der Datei `GET.jsp` wie unten gezeigt und klicken Sie auf **[!UICONTROL Alle speichern]**.

   ```javascript
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Führen Sie die folgenden Schritte für CSS-Anpassungen aus:

   1. Navigieren Sie zum Ordner `/apps/ws` und erstellen Sie einen neuen Ordner mit dem Namen `css`.

   1. Erstellen Sie im Ordner `css` eine neue Datei mit dem Namen `newStyle.css`.

   1. Öffnen Sie `/apps/ws/html`.jsp und wechseln Sie von

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
   >Platzieren Sie den Eintrag der benutzerdefinierten CSS-Datei nach dem Eintrag von style.css, wie oben gezeigt.

1. Ändern Sie in der Datei „apps/ws/html.jsp“ von

   ```jsp
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   in

   ```jsp
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Gehen Sie folgendermaßen vor:

   1. Erstellen Sie einen Ordner mit dem Namen `js` unter `/apps/ws`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Erstellen Sie einen Ordner mit dem Namen `libs` unter `/apps/ws/js`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Kopieren Sie den Ordner `/libs/ws/js/libs/jqueryui` in `/apps/ws/js/libs`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Führen Sie die folgenden Schritte für HTML-Anpassungen aus:

   1. Erstellen Sie unter `/apps/ws/js` einen Ordner mit dem Namen `runtime`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Erstellen Sie unter `/apps/ws/js/runtime` einen Ordner mit dem Namen `templates`. Klicken Sie auf **[!UICONTROL Alle speichern]**.

   1. Kopieren Sie `/libs/ws/js/main.js` nach `/apps/ws/js/main.js`.

   1. Kopieren Sie /libs/ws/js/registry.js nach `/apps/ws/js/registry.js`.

1. Klicken Sie auf **[!UICONTROL Alle speichern]**, löschen Sie den Cache und aktualisieren Sie AEM Forms Workspace.

   Greifen Sie auf die URL `https://'[server]:[port]'/lc/ws` zu und melden Sie sich mit Administrator-/Passwort-Anmeldeinformationen an. Der Browser leitet zu `https://'[server]:[port]'/lc/apps/ws/index.html` um.
