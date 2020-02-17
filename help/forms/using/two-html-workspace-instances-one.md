---
title: Hosten von zwei AEM Forms Workspace-Instanzen auf einem Server
seo-title: Hosten von zwei AEM Forms Workspace-Instanzen auf einem Server
description: Wie können LC-Adminstratoren HTML Workspace anpassen, um zwei Instanzen auf einem Server zu hosten, auf die über unterschiedliche URLs zugegriffen werden kann?
seo-description: Wie können LC-Adminstratoren HTML Workspace anpassen, um zwei Instanzen auf einem Server zu hosten, auf die über unterschiedliche URLs zugegriffen werden kann?
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Hosten von zwei AEM Forms Workspace-Instanzen auf einem Server {#hosting-two-aem-forms-workspace-instances-on-one-server}

Die Standardinstallation und -einstellungen von AEM Forms lassen nur die Bereitstellung einer AEM Forms Workspace-Instanz auf dem Server zu. Möglicherweise müssen Sie jedoch zwei verschiedene Instanzen von AEM Forms Workspace auf einem AEM Forms-Server hosten. Sie können auf die beiden Instanzen über unterschiedliche URLs zugreifen.

AEM Forms-Administratoren passen Workspace an, um zwei unterschiedliche URLs zu erstellen und zwei Workspace-Instanzen auf demselben Server bereitzustellen. In diesem Artikel zur Anpassung gehen wir davon aus, dass die beiden Arbeitsbereiche an- `https://[server]:[port]/lc/ws` und `https://[server]:[port]:/lc/ws2`zugänglich sind.

Führen Sie folgende Schritte aus, um AEM Forms Workspace zu konfigurieren.

1. Installieren Sie das Dev-Paket von AEM Forms Workspace auf dem Server. Anweisungen zum Erstellen finden Sie unter [Dev-Paket](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p).
1. Melden Sie sich bei CRXDE Lite als Administrator an, indem Sie darauf zugreifen `https://[server]:[port]/lc/crx/de/index.jsp`.
1. Kopieren Sie den Knoten „ws“ unter „/content“ und fügen Sie ihn unter „/content“ ein. Benennen Sie den Knoten in „ws2“ um. Klicken Sie auf **[!UICONTROL Alle speichern]**. Ändern Sie in den Eigenschaften dieses Knotens den Wert `sling:resourceType` in „ws2“. Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Kopieren Sie den Ordner „ws“ unter „/libs“ und fügen Sie ihn unter „/apps “ein. Benennen Sie den Ordner in „ws2“ um. Klicken Sie auf **[!UICONTROL Alle speichern]**.
1. In `GET.jsp` at `/apps/ws2`, make the following code changes. Ersetzen Sie den Code

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" /><html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" />
   ```

   durch den folgenden Code

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. In `registry.js` at `/apps/ws2/js`, change path of templates to refer to templates at `/apps/ws2/js/runtime/templates`. Ersetzen Sie den folgenden Code

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/libs/ws/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

   durch den folgenden Code

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/apps/ws2/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

1. Ändern Sie in `userinfo.js` at `/apps/ws2/js/runtime/models` und `/apps/ws2/js/runtime/views`die Zeichenfolge `/lc/content/ws` in `lc/content/ws2`.

1. Ändern Sie `/apps/ws2/js/runtime/services/service.js`den Pfad in der `getLocalizationData` Funktion in `/lc/apps/ws2/Locale.html`.

1. To refer to `pdf.html` of the new Workspace, change the path of `pdf.html` in `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. To refer to `pdf.html` of the new Workspace, change paths of `pdf.html` and `WsNextAdapter.swf` in `startprocess.html`, `taskdetails.html`, and `processinstancehistory.html` at `/apps/ws2/js/runtime/templates`.

1. Copy `/etc/map/ws` folder and paste at `/etc/map`. Benennen Sie den neuen Ordner in „ws2“ um. Klicken Sie auf „Alle speichern“.

1. In properties of `ws2`, change value of `sling:redirect` to `content/ws2`.

1. Ändern Sie den Wert von `sling:match` in `^[^/\||]/[^/\||]/ws2$`.

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
