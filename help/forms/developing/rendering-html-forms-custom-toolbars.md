---
title: Rendern von HTML Forms mit CustomToolbars
seo-title: Rendern von HTML Forms mit CustomToolbars
description: Verwenden Sie den Forms-Dienst, um eine Symbolleiste anzupassen, die mit einem HTML-Formular wiedergegeben wird. Sie können ein HTML-Formular mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API und einer Web Service-API rendern.
seo-description: Verwenden Sie den Forms-Dienst, um eine Symbolleiste anzupassen, die mit einem HTML-Formular wiedergegeben wird. Sie können ein HTML-Formular mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API und einer Web Service-API rendern.
uuid: b9c9464e-ff19-4051-a39b-4ec71c512d10
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 7eb0e8a8-d76a-43f7-a012-c21157b14cd4
role: Developer
exl-id: 0b992b1c-3878-447a-bccc-7034aa3e98bc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2384'
ht-degree: 1%

---

# Rendern von HTML Forms mit CustomToolbars {#rendering-html-forms-with-customtoolbars}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Rendern von HTML Forms mit benutzerdefinierten Symbolleisten {#rendering-html-forms-with-custom-toolbars}

Mit dem Forms-Dienst können Sie eine Symbolleiste anpassen, die mit einem HTML-Formular wiedergegeben wird. Eine Symbolleiste kann angepasst werden, um ihr Erscheinungsbild zu ändern, indem Standard-CSS-Stile überschrieben werden und um dynamisches Verhalten durch Überschreiben von Java-Skripten hinzuzufügen. Eine Symbolleiste wird mithilfe einer XML-Datei namens fscmenu.xml angepasst. Standardmäßig ruft der Forms-Dienst diese Datei von einem intern angegebenen URI-Speicherort ab.

>[!NOTE]
>
>Dieser URI-Speicherort befindet sich in der Datei &quot;adobe-forms-core.jar&quot;, die sich in der Datei &quot;adobe-forms-dsc.jar&quot;befindet. Die Datei &quot;adobe-forms-dsc.jar&quot;befindet sich unter C:\Adobe\Adobe_Experience_Manager_forms\ folder (C:\ is the installation directory). Sie können ein Dateiextraktions-Tool wie Win RAR verwenden, um das Adobe zu öffnen.

Sie können die Datei fscmenu.xml von diesem Speicherort kopieren, sie an Ihre Anforderungen anpassen und sie dann an einem benutzerdefinierten URI-Speicherort ablegen. Als Nächstes legen Sie mithilfe der Forms Service-API Laufzeitoptionen fest, die dazu führen, dass der Forms-Dienst Ihre Datei fscmenu.xml vom angegebenen Speicherort aus nutzt. Diese Aktionen führen dazu, dass der Forms-Dienst ein HTML-Formular wiedergibt, das über eine benutzerdefinierte Symbolleiste verfügt.

Zusätzlich zur Datei &quot;fscmenu.xml&quot;müssen Sie auch die folgenden Dateien abrufen:

* fscmenu.js
* fscattachments.js
* fscmenu.css
* fscmenu-v.css
* fscmenu-ie.css
* fscdialog.css

fscJS ist das Java-Skript, das mit jedem Knoten verknüpft ist. Es ist erforderlich, einen für den Knoten `div#fscmenu` und optional für Knoten `ul#fscmenuItem` anzugeben. Die JS-Dateien implementieren die Kernfunktionalität der Symbolleiste und die Standarddateien funktionieren.

fscCSS ist ein Stylesheet, das mit einem bestimmten Knoten verknüpft ist. Die Stile in den CSS-Dateien geben das Erscheinungsbild der Symbolleiste an. ** fscVCSS ist ein Stylesheet für eine vertikale Symbolleiste, das links neben dem wiedergegebenen HTML-Formular angezeigt wird. ** fscIECSS ist ein Stylesheet, das für HTML-Formulare verwendet wird, die in Internet Explorer wiedergegeben werden.

Stellen Sie sicher, dass alle oben genannten Dateien in der Datei &quot;fscmenu.xml&quot;referenziert sind. Das heißt, geben Sie in der Datei &quot;fscmenu.xml&quot;URI-Speicherorte an, die auf diese Dateien verweisen, damit der Forms-Dienst sie finden kann. Standardmäßig sind diese Dateien an URI-Speicherorten verfügbar, die mit internen Keywords `FSWebRoot` oder `ApplicationWebRoot` beginnen.

Um die Symbolleiste anzupassen, ersetzen Sie die Suchbegriffe durch den externen Suchbegriff `FSToolBarURI`. Dieses Schlüsselwort stellt den URI dar, der zur Laufzeit an den Forms-Dienst übergeben wird (dieser Ansatz wird weiter unten in diesem Abschnitt gezeigt).

Sie können auch die absoluten Speicherorte dieser JS- und CSS-Dateien angeben, z. B. https://www.mycompany.com/scripts/misc/fscmenu.js. In diesem Fall müssen Sie das `FSToolBarURI`-Keyword nicht verwenden.

>[!NOTE]
>
>Es wird nicht empfohlen, die Referenzierung dieser Dateien zu verändern. Das heißt, alle URIs sollten entweder mit dem `FSToolBarURI`-Keyword oder einem absoluten Speicherort referenziert werden.

Sie können die JS- und CSS-Dateien abrufen, indem Sie die Datei &quot;adobe-forms-&lt;Anwendungsserver>.ear&quot;öffnen. Öffnen Sie in dieser Datei adobe-forms-res.war. Alle diese Dateien befinden sich in der WAR-Datei. Die Datei &quot;adobe-forms-&lt;Anwendungsserver>.ear&quot;befindet sich im Installationsordner für AEM Formulare (C:\ is the installation directory). Sie können die Datei &quot;adobe-forms-&lt;Anwendungsserver>.ear&quot;mit einem Dateiextraktions-Tool wie WinRAR öffnen.

Die folgende XML-Syntax zeigt eine Beispieldatei &quot;fscmenu.xml&quot;.

```html
 <div id="fscmenu" fscJS="FSToolBarURI/scripts/fscmenu.js" fscCSS="FSToolBarURI/fscmenu.css" fscVCSS="FSToolBarURI/fscmenu-v.css" fscIECSS="FSToolBarURI/fscmenu-ie.css">
         <ul class="fscmenuItem" id="Home">
             <li>
                 <a href="#" fscTarget="_top" tabindex="1">Home</a>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Upload" fscJS="FSToolBarURI/scripts/fscattachments.js" fscCSS="FSToolBarURI/fscdialog.css">
             <li>
                 <a tabindex="2">Upload Attachments</a>
                 <ul class="fscmenuPopup" id="fscUploadAttachments">
                     <li>
                         <a href="javascript:doUploadDialog();" tabindex="3">Add ...</a>
                     </li>
                     <li>
                         <a href="javascript:doDeleteDialog();" tabindex="4">Delete ...</a>
                     </li>
                 </ul>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Download">
             <li>
                 <a tabindex="100">Download Attachments</a>
                 <ul class="fscmenuPopup">
                     <li>
                         <a tabindex="101">None available</a>
                     </li>
                 </ul>
             </li>
         </ul>
     </div>
```

>[!NOTE]
>
>Der fett gedruckte Text stellt die URIs für die CSS- und JS-Dateien dar, auf die verwiesen werden muss.

Die folgenden Elemente beschreiben, wie Sie eine Symbolleiste anpassen können:

* Ändern Sie die Werte der Attribute `fscJS`, `fscCSS`, `fscVCSS`, `fscIECSS` (in der Datei &quot;fscmenu.xml&quot;) so, dass sie die benutzerdefinierten Speicherorte der referenzierten Dateien widerspiegeln, indem Sie eine der in diesem Abschnitt beschriebenen Methoden verwenden (z. B. `fscJS="FSToolBarURI/scripts/fscmenu.js"`).
* Alle CSS- und JS-Dateien müssen angegeben werden. Wenn keine der Dateien geändert wird, geben Sie die Standarddatei am benutzerdefinierten Speicherort an. Sie können die Standarddateien abrufen, indem Sie verschiedene Dateien öffnen, wie in diesem Abschnitt beschrieben.
* Die Bereitstellung einer absoluten Referenz (z. B. https://www.example.com/scripts/custom-vertical-fscmenu.css) für jede Datei ist zulässig.
* Die JS- und CSS-Dateien, die der Knoten `div#fscmenu` erfordert, sind für die Symbolleistenfunktion unerlässlich. Einzelne `ul#fscmenuItem` -Knoten können oder nicht unterstützende JS- oder CSS-Dateien haben.

**Ändern des lokalen Werts**

Beim Anpassen einer Symbolleiste können Sie den Gebietsschemawert der Symbolleiste ändern. Das heißt, Sie können es in einer anderen Sprache anzeigen. Die folgende Abbildung zeigt eine benutzerdefinierte Symbolleiste, die auf Französisch angezeigt wird.

>[!NOTE]
>
>Es ist nicht möglich, eine benutzerdefinierte Symbolleiste in mehreren Sprachen zu erstellen. Symbolleisten können basierend auf den Gebietsschemaeinstellungen keine anderen XML-Dateien verwenden.

Um den Gebietsschemawert einer Symbolleiste zu ändern, stellen Sie sicher, dass die Datei fscmenu.xml die Sprache enthält, die angezeigt werden soll. Die folgende XML-Syntax zeigt die Datei &quot;fscmenu.xml&quot;, die zum Anzeigen einer französischen Symbolleiste verwendet wird.

```html
 <div id="fscmenu" fscJS="FSToolBarURI/scripts/fscmenu.js" fscCSS="FSToolBarURI/fscmenu.css" fscVCSS="FSToolBarURI/fscmenu-v.css" fscIECSS="FSToolBarURI/fscmenu-ie.css">
         <ul class="fscmenuItem" id="Home">
             <li>
                 <a href="#" fscTarget="_top" tabindex="1">Accueil</a>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Upload" fscJS="FSToolBarURI/scripts/fscattachments.js" fscCSS="FSToolBarURI/fscdialog.css">
             <li>
                 <a tabindex="2">Télécharger les pièces jointes</a>
                 <ul class="fscmenuPopup" id="fscUploadAttachments">
                     <li>
                         <a href="javascript:doUploadDialog();" tabindex="3">Ajouter...</a>
                     </li>
                     <li>
                         <a href="javascript:doDeleteDialog();" tabindex="4">Supprimer...</a>
                     </li>
                 </ul>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Download">
             <li>
                 <a tabindex="100">Télécharger les pièces jointes</a>
                 <ul class="fscmenuPopup">
                     <li>
                         <a tabindex="101">Aucune disponible</a>
                     </li>
                 </ul>
             </li>
         </ul>
     </div>
```

>[!NOTE]
>
>Die Lernprogramme, die mit diesem Abschnitt verknüpft sind, verwenden diese XML-Datei, um eine benutzerdefinierte französische Symbolleiste anzuzeigen, wie in der vorherigen Abbildung gezeigt.

Geben Sie außerdem einen gültigen Gebietsschemawert an, indem Sie die `setLocale` -Methode des Objekts `HTMLRenderSpec` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt. Übergeben Sie beispielsweise `fr_FR`, um Französisch anzugeben. Der Forms-Dienst ist mit lokalisierten Symbolleisten gebündelt.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular wiedergeben, das eine benutzerdefinierte Symbolleiste verwendet, müssen Sie wissen, wie HTML-Formulare wiedergegeben werden. (Siehe [Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md).)

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein HTML-Formular mit einer benutzerdefinierten Symbolleiste wiederzugeben:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Java API-Objekt.
1. Referenzieren Sie eine benutzerdefinierte XML-Datei fscmenu .
1. Wiedergabe eines HTML-Formulars
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen eines Forms Java API-Objekts**

Bevor Sie einen vom Forms-Dienst unterstützten Vorgang programmgesteuert ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**Referenzieren einer benutzerdefinierten XML-Datei fscmenu**

Um ein HTML-Formular wiederzugeben, das eine benutzerdefinierte Symbolleiste enthält, verweisen Sie auf eine XML-Datei fscmenu , die die Symbolleiste beschreibt. (Dieser Abschnitt enthält zwei Beispiele für eine XML-Datei fscmenu .) Stellen Sie außerdem sicher, dass die Datei fscmenu.xml die Speicherorte aller referenzierten Dateien richtig angibt. Stellen Sie wie bereits zuvor in diesem Abschnitt erwähnt sicher, dass alle Dateien entweder durch das `FSToolBarURI`-Keyword oder durch ihre absoluten Speicherorte referenziert werden.

**HTML-Formular wiedergeben**

Um ein HTML-Formular wiederzugeben, geben Sie einen Formularentwurf an, der in Designer erstellt und als XDP-Datei gespeichert wurde. Wählen Sie auch einen HTML-Transformationstyp aus. Sie können beispielsweise den HTML-Transformationstyp angeben, der ein dynamisches HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte für die Wiedergabe anderer Formulartypen.

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein HTML-Formular wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen, damit das HTML-Formular für Benutzer sichtbar wird.

**Siehe auch**

[Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API](#render-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Webdienst-API](#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API {#render-an-html-form-with-a-custom-toolbar-using-the-java-api}

Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Forms Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Java API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Referenzieren einer benutzerdefinierten XML-Datei fscmenu

   * Erstellen Sie ein `HTMLRenderSpec` -Objekt mithilfe des zugehörigen Konstruktors.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `setHTMLToolbar` -Methode des Objekts `HTMLRenderSpec` auf und übergeben Sie einen `HTMLToolbar`-Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der XML-Datei fscmenu an, indem Sie die Methode `setToolbarURI` des Objekts `HTMLRenderSpec` aufrufen und einen string -Wert übergeben, der den URI-Speicherort der XML-Datei angibt.
   * Falls zutreffend, legen Sie den Gebietsschemawert fest, indem Sie die `setLocale` -Methode des Objekts `HTMLRenderSpec` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt. Der Standardwert ist Englisch.

   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Schnellstarts setzen diesen Wert auf `fr_FR`*.*

1. HTML-Formular wiedergeben

   Rufen Sie die `renderHTMLForm` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` -Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderHTMLForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `FormsResult` -Methode des Objekts &quot;s `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `com.adobe.idp.Document` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `com.adobe.idp.Document` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `read` -Methode des Objekts `InputStream` aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.ServletOutputStream` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Schnellstart (SOAP-Modus): Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Webdienst-API {#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api}

Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Forms Service-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Java API-Objekts

   Erstellen Sie ein `FormsService` -Objekt und legen Sie Authentifizierungswerte fest.

1. Referenzieren einer benutzerdefinierten XML-Datei fscmenu

   * Erstellen Sie ein `HTMLRenderSpec` -Objekt mithilfe des zugehörigen Konstruktors.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `setHTMLToolbar` -Methode des Objekts `HTMLRenderSpec` auf und übergeben Sie einen `HTMLToolbar`-Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der XML-Datei fscmenu an, indem Sie die Methode `setToolbarURI` des Objekts `HTMLRenderSpec` aufrufen und einen string -Wert übergeben, der den URI-Speicherort der XML-Datei angibt.
   * Falls zutreffend, legen Sie den Gebietsschemawert fest, indem Sie die `setLocale` -Methode des Objekts `HTMLRenderSpec` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt. Der Standardwert ist Englisch.

   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Schnellstarts setzen diesen Wert auf `fr_FR`*.*

1. HTML-Formular wiedergeben

   Rufen Sie die `renderHTMLForm` -Methode des Objekts `FormsService` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein string -Wert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322`). Wenn Sie diesen Wert nicht festlegen möchten, können Sie eine leere Zeichenfolge übergeben.
   * Ein `URLSpec` -Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dieser Parameter ist optional und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der `renderHTMLForm` -Methode gefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der `renderHTMLForm` -Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der `renderHTMLForm` -Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der `renderHTMLForm` -Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der `renderHTMLForm` -Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Rendering-Wert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderHTMLForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` -Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` -Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `BLOB` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `BLOB` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `getBinaryData`-Methode des Objekts `BLOB`. Diese Aufgabe weist den Inhalt des Objekts `FormsResult` dem Byte-Array zu.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.http.HttpServletResponse` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
