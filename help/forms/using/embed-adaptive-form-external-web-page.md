---
title: Anpassungsfähige Formulare in externe Web-Seiten einbetten
description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms
exl-id: 2a237f74-fdfc-4e28-841c-f69afb7b99cf
source-git-commit: 65c5a4442f17e6bc52deaa1588f535a05698083f
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 38%

---

# Anpassungsfähige Formulare in externe Web-Seiten einbetten{#embed-adaptive-form-in-external-web-page}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird ein älterer Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

Sie können [adaptive Formulare in eine AEM Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md) oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzende können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

## Voraussetzungen {#prerequisites}

Führen Sie die folgenden Schritte aus, bevor Sie ein adaptives Formular in eine externe Website einbetten

* Veröffentlichen Sie das adaptive Formular, das in die Veröffentlichungsinstanz des AEM Forms-Servers eingebettet werden soll.
* Erstellen oder identifizieren Sie eine Webseite auf Ihrer Website, auf der Sie das adaptive Formular hosten können. Stellen Sie sicher, dass die Webseite [jQuery-Dateien aus einem CDN lesen](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) oder eine lokale Kopie der jQuery eingebettet hat. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* Wenn sich der AEM-Server und die Webseite auf unterschiedlichen Domänen befinden, führen Sie die im Abschnitt aufgeführten Schritte aus. [AEM Forms aktivieren, um adaptive Formulare für eine domänenübergreifende Site bereitzustellen](#cross-site).

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

   * Ändern Sie den Wert der *options.path* mit dem Pfad der Veröffentlichungs-URL des adaptiven Formulars. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Geben Sie immer den vollständigen Namen des adaptiven Formulars einschließlich der Erweiterung an. Beispielsweise befinden sich der obige Code und das adaptive Formular auf demselben AEM Forms-Server, sodass das Beispiel den Kontextpfad des adaptiven Formulars verwendet `/content/forms/af/locbasic.html`.
   * Ersetzen Sie *options.dataRef* durch Attribute, die mit der URL übertragen werden sollen. Sie können die Variable dataref zum [Vorausfüllen eines adaptiven Formulars](/help/forms/using/prepopulate-adaptive-form-fields.md) verwenden.
   * Ersetzen *options.themePath* mit dem Pfad zu einem anderen Design als dem im adaptiven Formular konfigurierten Design. Alternativ können Sie den Designpfad mit dem Anfrageattribut angeben.
   * CSS_Selector ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Im obigen Beispiel ist die CSS-Klasse „.customafsection“ der CSS-Selektor.

Das adaptive Formular ist in die Webseite eingebettet. Beachten Sie Folgendes im eingebetteten adaptiven Formular:

* Die Kopf- und Fußzeile im ursprünglichen adaptiven Formular sind nicht im eingebetteten Formular enthalten.
* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im ursprünglichen adaptiven Formular konfigurierte Sendeaktion wird im eingebetteten Formular beibehalten.
* Die Regeln für adaptive Formulare werden beibehalten und im eingebetteten Formular vollständig verwendet.
* Erlebnis-Targeting und im ursprünglichen adaptiven Formular konfigurierte A/B-Tests funktionieren im eingebetteten Formular nicht.
* Wenn Adobe Analytics im Originalformular konfiguriert ist, werden die Analysedaten vom Adobe Analytics-Server erfasst. Sie ist jedoch nicht im Forms-Analysebericht verfügbar.

## Beispieltopologie {#sample-topology}

Die externe Webseite, die das adaptive Formular einbettet, sendet Anforderungen an den AEM-Server, der sich normalerweise hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anfragen sicher an den AEM-Server weitergeleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Sehen wir uns ein Beispiel an, wie Sie einen Apache 2.4-Reverse-Proxy-Server ohne Dispatcher einrichten können. In diesem Beispiel hosten Sie den AEM mit `/forms` Kontextpfad und Zuordnung `/forms` für den Reverse-Proxy. Dadurch wird sichergestellt, dass alle Anfragen an `/forms` auf dem Apache-Server werden zur AEM-Instanz weitergeleitet. Diese Topologie hilft dabei, die Anzahl der Regeln auf der Dispatcher-Ebene zu reduzieren, da alle Anforderungen mit dem Präfix `/forms` zum AEM Server weitergeleitet.

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

Wenn Sie den AEM-Server nicht auf einem Kontextpfad bereitstellen, lauten die Proxy-Regeln auf der Apache-Ebene wie folgt:

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
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs zum Senden, Vorbefüllen und andere URLs zur Zulassungsliste auf der Dispatcher-Ebene hinzufügen.

## Best Practices {#best-practices}

Beachten Sie beim Einbetten eines adaptiven Formulars in eine Webseite die folgenden Best Practices:

* Stellen Sie sicher, dass die Stilregeln, die in der CSS der Webseite definiert sind, nicht mit dem CSS des Formularobjekts in Konflikt stehen. Um Konflikte zu vermeiden, können Sie das CSS der Web-Seite im Thema für adaptive Formulare mithilfe der AEM Client-Bibliothek wiederverwenden. Informationen zur Verwendung der Client-Bibliothek in Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](../../forms/using/themes.md).
* Stellen Sie sicher, dass der Formularcontainer auf der Webseite die gesamte Fensterbreite verwendet. Dadurch wird sichergestellt, dass die für Mobilgeräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formular-Container nicht die gesamte Fensterbreite benötigt, müssen Sie benutzerdefiniertes CSS schreiben, damit das Formular an verschiedene Mobilgeräte angepasst werden kann.
* Verwenden Sie die API `[getData](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)`, um die XML- oder JSON-Darstellung der Formulardaten im Client abzurufen.
* Verwenden Sie die API `[unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)`, um das adaptive Formular aus HTML DOM zu entfernen.
* Richten Sie den Header access-control-origin ein, wenn Sie eine Antwort von einem AEM-Server senden.

## Aktivieren Sie AEM Forms, um adaptive Formulare für eine domänenübergreifende Site bereitzustellen {#cross-site}

1. Gehen Sie in der AEM-Veröffentlichungsinstanz zum Konfigurations-Manager der AEM-Web-Konsole unter `https://'[server]:[port]'/system/console/configMgr`.
1. Suchen Sie die Konfiguration **Apache Sling Referrer Filter** und öffnen Sie sie.
1. Geben Sie im Feld Zulässige Hosts die Domain an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungs-Domains anzugeben.
