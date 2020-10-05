---
title: Anpassungsfähige Formulare in externe Webseiten einbetten
seo-title: Anpassungsfähige Formulare in externe Webseiten einbetten
description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten
seo-description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe HTML-Seite einbetten
uuid: d81032dd-af80-4f4b-a717-ee1b89fd3d3d
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: d739c6da-3b41-4452-8728-d7cd1a3ae20b
docset: aem65
translation-type: tm+mt
source-git-commit: ade3747ba608164a792a62097b82c55626245891
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 68%

---


# Anpassungsfähige Formulare in externe Webseiten einbetten{#embed-adaptive-form-in-external-web-page}

Sie können [adaptive Formulare in eine AEM-Siteseite](/help/forms/using/embed-adaptive-form-aem-sites.md) oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren..

## Voraussetzungen {#prerequisites}

Führen Sie folgende Schritte aus, bevor Sie ein adaptives Formular in eine externe Webseite einbetten:

* Veröffentlichen Sie das einzubettende adaptive Formular in der Veröffentlichungsinstanz von AEM Forms Server.
* Erstellen Sie auf Ihrer Website eine Webseite oder legen Sie sie fest, um das adaptive Formular zu hosten. Ensure that the webpage can [read jQuery files from a CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) or has a local copy of the jQuery embeded. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* When AEM server and the web page are on different domains, perform the steps listed in sectiion, [enable AEM Forms to serve adaptive forms to a cross domain site](#cross-site).

## Adaptives Formular einbetten {#embed-adaptive-form}

Sie können ein adaptives Formular einbetten, indem Sie einige Zeilen JavaScript in die Webseite einfügen. Die API im Code sendet eine HTTP-Anforderung an den AEM-Server für adaptive Formularressourcen und fügt das adaptive Formular in den angegebenen Formularcontainer ein.

Einbetten des adaptiven Formulars:

1. Erstellen Sie eine Webseite auf Ihrer Website mit folgendem Code:

   ```html
   <!doctype html>
   <html>
     <head>
       <title>This is the title of the webpage!</title>
       <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
     </head>
     <body>
     <div class="customafsection"/>
       <p>This section is replaced with the adaptive form.</p>
   
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
       if(options.path) {
           // options.path refers to the publish URL of the adaptive form
           // For Example: https:myserver:4503/content/forms/af/ABC, where ABC is the adaptive form
           // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path
           var path = options.path;
           path += "/jcr:content/guideContainer.html";
           $.ajax({
               url  : path ,
               type : "GET",
               data : {
                   // Set the wcmmode to be disabled
                   wcmmode : "disabled"
                   // Set the data reference, if any
                  // "dataRef": options.dataRef
                   // Specify a different theme for the form object
                 //  "themeOverride" : options.themepath
               },
               async: false,
               success: function (data) {
                   // If jquery is loaded, set the inner html of the container
                   // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                   // For example: document.getElementById().innerHTML
                   if(window.$ && options.CSS_Selector){
                       // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                       $(options.CSS_Selector).html(data);
                   }
               },
               error: function (data) {
                   // any error handler
               }
           });
       } else {
           if (typeof(console) !== "undefined") {
               console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
           }
       }
    }(options);
   
    </script>
     </body>
   </html>
   ```

1. Im eingebetteten Code:

   * Change value of the *options.path* variable with the path of the publish URL of the adaptive form. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Erwähnen Sie immer den vollständigen Namen des adaptiven Formulars einschließlich der Erweiterung.   Beispiel: Der oben aufgeführte Code und das adaptive Formular befinden sich auf demselben AEM Formularserver, sodass im Beispiel der Kontextpfad des adaptiven Formulars /content/forms/af/locbasic.html verwendet wird.
   * Ersetzen Sie *options.dataRef* durch Attribute, die mit der URL übertragen werden sollen. You can use the dataref variable to [prefill an adaptive form](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Ersetzen Sie *options.themePath* durch den Pfad zu einem anderen Design als dem im adaptiven Formular konfigurierten Design. Alternativ können Sie den Designpfad mit dem Anforderungsattribut angeben.
   * CSS_Selector ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Beispiel: Die CSS-Klasse &quot;.customafsection&quot;ist im obigen Beispiel der CSS-Selektor.

Das adaptive Formular wird in die Webseite eingebettet. Beobachten Sie Folgendes im eingebetteten adaptiven Formular:

* Die Kopf- und Fußzeile im adaptiven Originalformular werden nicht vom eingebetteten Formular übernommen.
* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im adaptiven Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Regeln für adaptive Formulare bleiben erhalten und sind im eingebetteten Formular voll funktionsfähig.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten adaptiven Formular nicht.
* Wenn Adobe Analytics im ursprünglichen Formular konfiguriert ist, werden die Analysedaten im Adobe Analytics-Server erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

## Mustertopologie {#sample-topology}

Die externe Webseite, in die das adaptive Formular eingebettet wird, sendet Anforderungen an den AEM-Server, der sich in der Regel hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anforderungen sicher auf den AEM-Server geleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Schauen wir uns ein Beispiel an, wie Sie einen Apache 2.4-Reverse-Proxy-Server ohne Dispatcher einrichten können. In this example, you will host the AEM server with `/forms` context path and map `/forms` for the reverse proxy. It ensures that any request for `/forms` on Apache server are directed to the AEM instance. This topology helps reduces the number of rules at the dispatcher layer as all request prefixed with `/forms` route to the AEM server.

1. Öffnen Sie die Konfigurationsdatei `httpd.conf` und heben Sie den Kommentar für die folgenden Codezeilen auf. Alternativ können Sie die folgenden Codezeilen in die Datei einfügen.

   ```text
   LoadModule proxy_html_module modules/mod_proxy_html.so
   LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Richten Sie Proxy-Regeln ein, indem Sie die folgenden Codezeilen in der Konfigurationsdatei `httpd-proxy.conf` hinzufügen.

   ```text
   ProxyPass /forms https://[AEM_Instance]/forms
   ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Replace `[AEM_Instance]` with the AEM server publish URL in the rules.

Wenn Sie den AEM-Server nicht auf einem Kontextpfad bereitstellen, lauten die Proxyregeln auf der Apache-Ebene wie folgt:

```text
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json

ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie der Zulassungsliste auf der Dispatcher-Ebene die URLs &quot;Senden&quot;, &quot;Vorausfüllen&quot;und andere URLs hinzufügen.

## Best Practices {#best-practices}

Berücksichtigen Sie beim Einbetten eines adaptiven Formulars in eine Webseite die folgenden Richtlinien:

* Stellen Sie sicher, dass die Formatierungsregeln in den Webseite-CSS nicht mit den Formularobjekt-CSS in Konflikt stehen. Um dies zu vermeiden, können Sie die Webseite-CSS im Design für das adaptive Formular mithilfe der AEM-Clientbibliothek wiederverwenden. Weitere Informationen zur Verwendung der Client-Bibliothek in den Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](../../forms/using/themes.md).
* Verwenden Sie für den Formularcontainer auf der Webseite die gesamte Fensterbreite. So wird sichergestellt, dass die für mobile Geräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formularcontainer nicht die gesamte Fensterbreite einnimmt, müssen Sie benutzerdefinierte CSS schreiben, damit sich das Formular an verschiedene mobile Geräte anpasst.
* Use `[getData](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` API to get the XML or JSON representation of form data in client.
* Use `[unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` API to unload the adaptive form from HTML DOM.
* Richten Sie beim Senden der Antwort vom AEM den Header access-control-Herkunft ein.

## Bereitstellung adaptiver Formulare auf einer domänenübergreifenden Site durch AEM Forms {#cross-site}

1. On AEM author instance, go to AEM Web Console Configuration Manager at `https://'[server]:[port]'/system/console/configMgr`.
1. Suchen Sie die Konfiguration **Apache Sling Referrer Filter** und öffnen Sie sie.
1. Geben Sie im Feld Zulässige Hosts die Domäne an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungsdomänen anzugeben.

