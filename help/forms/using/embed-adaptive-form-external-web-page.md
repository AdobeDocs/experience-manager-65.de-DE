---
title: Anpassungsfähige Formulare in externe Web-Seiten einbetten
seo-title: Embed adaptive form in external web page
description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten
seo-description: Learn how to embed an adaptive form in an external HTML web page
uuid: d81032dd-af80-4f4b-a717-ee1b89fd3d3d
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: d739c6da-3b41-4452-8728-d7cd1a3ae20b
docset: aem65
feature: Adaptive Forms
exl-id: 2a237f74-fdfc-4e28-841c-f69afb7b99cf
source-git-commit: f114456d5571620772341cba9bd8203d91d0b053
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 62%

---

# Anpassungsfähige Formulare in externe Web-Seiten einbetten{#embed-adaptive-form-in-external-web-page}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

Sie können [adaptive Formulare in eine AEM Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md) oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzende können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren..

## Voraussetzungen {#prerequisites}

Führen Sie die folgenden Schritte aus, bevor Sie ein adaptives Formular in eine externe Website einbetten

* Veröffentlichen Sie das einzubettende adaptive Formular in der Veröffentlichungsinstanz von AEM Forms Server.
* Erstellen Sie auf Ihrer Website eine Webseite oder legen Sie sie fest, um das adaptive Formular zu hosten. Stellen Sie sicher, dass die Webseite [jQuery-Dateien von einem CDN lesen](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) kann oder eine lokale Kopie von jQuery eingebettet hat. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* Wenn AEM-Server und die Web-Seite sich in verschiedenen Domains befinden, führen Sie die im Abschnitt [Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms](#cross-site) beschriebenen Schritte aus.

## Adaptives Formular einbetten {#embed-adaptive-form}

Sie können ein adaptives Formular einbetten, indem Sie einige Zeilen JavaScript in die Web-Seite einfügen. Die API im Code sendet eine HTTP-Anforderung an den AEM-Server für adaptive Formularressourcen und fügt das adaptive Formular in den angegebenen Formularcontainer ein.

Einbetten des adaptiven Formulars:

1. Erstellen Sie eine Web-Seite auf Ihrer Website mit dem folgenden Code:

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
           // options.path refers to the path of the adaptive form
           // For Example: /content/forms/af/ABC, where ABC is the adaptive form
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

   * Ersetzen Sie den Wert der Variablen *options.path* durch die Veröffentlichungs-URL des adaptiven Formulars. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Geben Sie immer den vollständigen Namen des adaptiven Formulars einschließlich der Erweiterung an. Beispielsweise befinden sich der Code und das adaptive Formular im Beispiel oben auf demselben AEM Forms-Server, daher wird im Kontextpfad dieses Beispiels der Pfad „/content/forms/af/locbasic.html“ für das adaptive Formular verwendet.
   * Ersetzen Sie *options.dataRef* durch Attribute, die mit der URL übertragen werden sollen. Sie können die Variable dataref zum [Vorausfüllen eines adaptiven Formulars](/help/forms/using/prepopulate-adaptive-form-fields.md) verwenden.
   * Ersetzen *options.themePath* mit dem Pfad zu einem anderen Design als dem im adaptiven Formular konfigurierten Design. Alternativ können Sie den Designpfad mit dem Anfrageattribut angeben.
   * CSS_Selector ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Im obigen Beispiel ist die CSS-Klasse „.customafsection“ der CSS-Selektor.

Das adaptive Formular ist in die Webseite eingebettet. Beachten Sie Folgendes im eingebetteten adaptiven Formular:

* Kopf- und Fußzeile im ursprünglichen adaptiven Formular sind nicht im eingebetteten Formular enthalten.
* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im ursprünglichen adaptiven Formular konfigurierte Sendeaktion wird im eingebetteten Formular beibehalten.
* Die Regeln für adaptive Formulare werden beibehalten und im eingebetteten Formular vollständig verwendet.
* Erlebnis-Targeting und im ursprünglichen adaptiven Formular konfigurierte A/B-Tests funktionieren im eingebetteten Formular nicht.
* Wenn Adobe Analytics im Originalformular konfiguriert ist, werden die Analysedaten auf dem Adobe Analytics-Server erfasst. Sie ist jedoch nicht im Forms-Analysebericht verfügbar.

## Beispieltopologie {#sample-topology}

Die externe Webseite, die das adaptive Formular einbettet, sendet Anforderungen an den AEM-Server, der sich normalerweise hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anfragen sicher an den AEM-Server weitergeleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Sehen wir uns ein Beispiel an, wie Sie einen Apache 2.4 Reverse-Proxy-Server ohne Dispatcher einrichten können. In diesem Beispiel hosten Sie den AEM-Server mit dem Kontextpfad `/forms` und weisen `/forms` für den Reverse-Proxy zu. Dadurch wird sichergestellt, dass alle Anforderungen für `/forms` auf dem Apache-Server an die AEM-Instanz geleitet werden. Diese Topologie hilft dabei, die Anzahl der Regeln auf der Dispatcher-Ebene zu reduzieren, da alle Anforderungen mit dem Präfix `/forms` an den AEM-Server weitergeleitet werden.

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

   Ersetzen Sie in den Regeln `[AEM_Instance]` durch die Veröffentlichungs-URL des AEM-Servers.

Wenn Sie den AEM-Server nicht in einem Kontextpfad bereitstellen, lauten die Proxy-Regeln auf Apache-Ebene wie folgt:

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
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs für Senden, Vorausfüllen und andere Funktionen auf der Dispatcher-Ebene in die Positivliste eintragen.

## Best Practices {#best-practices}

Beachten Sie beim Einbetten eines adaptiven Formulars in eine Webseite die folgenden Best Practices:

* Stellen Sie sicher, dass die Stilregeln, die in der CSS der Webseite definiert sind, nicht mit dem CSS des Formularobjekts in Konflikt stehen. Um Konflikte zu vermeiden, können Sie das CSS der Webseite im Thema für adaptive Formulare mithilfe AEM Client-Bibliothek wiederverwenden. Informationen zur Verwendung der Client-Bibliothek in Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](../../forms/using/themes.md).
* Stellen Sie sicher, dass der Formularcontainer auf der Webseite die gesamte Fensterbreite verwendet. Dadurch wird sichergestellt, dass die für Mobilgeräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formular-Container nicht die gesamte Fensterbreite benötigt, müssen Sie benutzerdefiniertes CSS schreiben, damit das Formular an verschiedene Mobilgeräte angepasst werden kann.
* Verwenden Sie die API `[getData](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)`, um die XML- oder JSON-Darstellung der Formulardaten im Client abzurufen.
* Verwenden Sie die API `[unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)`, um das adaptive Formular aus HTML DOM zu entfernen.
* Richten Sie den Header „access-control-origin“ ein, wenn Sie eine Antwort vom AEM-Server senden.

## Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms {#cross-site}

1. Gehen Sie in der AEM-Veröffentlichungsinstanz zum Konfigurations-Manager der AEM-Web-Konsole unter `https://'[server]:[port]'/system/console/configMgr`.
1. Suchen Sie die Konfiguration **Apache Sling Referrer Filter** und öffnen Sie sie.
1. Geben Sie im Feld Zulässige Hosts die Domain an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungs-Domains anzugeben.
