---
title: Rendern von HTML Forms mit CustomToolbars
seo-title: Rendern von HTML Forms mit CustomToolbars
description: Verwenden Sie den Forms-Dienst, um eine Symbolleiste anzupassen, die mit einem HTML-Formular wiedergegeben wird. Sie können ein HTML-Formular mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API und einer Webdienst-API wiedergeben.
seo-description: Verwenden Sie den Forms-Dienst, um eine Symbolleiste anzupassen, die mit einem HTML-Formular wiedergegeben wird. Sie können ein HTML-Formular mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API und einer Webdienst-API wiedergeben.
uuid: b9c9464e-ff19-4051-a39b-4ec71c512d10
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 7eb0e8a8-d76a-43f7-a012-c21157b14cd4
role: Entwickler
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2385'
ht-degree: 1%

---


# Rendern von HTML-Forms mit CustomToolbars {#rendering-html-forms-with-customtoolbars}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

## Rendern von HTML Forms mit benutzerdefinierten Symbolleisten {#rendering-html-forms-with-custom-toolbars}

Mit dem Forms-Dienst können Sie eine Symbolleiste anpassen, die mit einem HTML-Formular wiedergegeben wird. Eine Symbolleiste kann angepasst werden, um ihr Erscheinungsbild zu ändern, indem Standard-CSS-Stile außer Kraft gesetzt und dynamisches Verhalten durch Überschreiben von Java-Skripten hinzugefügt werden. Eine Symbolleiste wird mithilfe einer XML-Datei mit dem Namen &quot;fscmenu.xml&quot;angepasst. Standardmäßig ruft der Forms-Dienst diese Datei von einem intern angegebenen URI-Speicherort ab.

>[!NOTE]
>
>Dieser URI-Speicherort befindet sich in der Datei &quot;adobe-forms-core.jar&quot;, die sich in der Datei &quot;adobe-forms-dsc.jar&quot;befindet. Die Datei &quot;adobe-forms-dsc.jar&quot;befindet sich unter C:\Adobe\Adobe_Experience_Manager_forms\ folder (C:\ is the installation directory). Sie können ein Dateiwerkzeug wie Win RAR verwenden, um das adobe zu öffnen.

Sie können die Datei &quot;fscmenu.xml&quot;von dieser Position aus kopieren, sie an Ihre Anforderungen anpassen und sie dann an einem benutzerdefinierten URI-Speicherort ablegen. Legen Sie dann mithilfe der Forms Service API Laufzeitoptionen fest, die dazu führen, dass der Forms-Dienst die Datei &quot;fscmenu.xml&quot;vom angegebenen Speicherort aus verwendet. Diese Aktionen führen dazu, dass der Forms-Dienst ein HTML-Formular mit einer benutzerdefinierten Symbolleiste wiedergibt.

Zusätzlich zur Datei &quot;fscmenu.xml&quot;müssen Sie auch die folgenden Dateien abrufen:

* fscmenu.js
* fscattachments.js
* fscmenu.css
* fscmenu-v.css
* fscmenu-ie.css
* fscdialog.css

fscJS ist das Java-Skript, das jedem Knoten zugeordnet ist. Es ist erforderlich, einen Knoten für den Knoten `div#fscmenu` und optional für `ul#fscmenuItem`-Knoten bereitzustellen. Die JS-Dateien implementieren die Kern-Symbolleistenfunktion, und die Standarddateien funktionieren.

fscCSS ist ein Stylesheet, das mit einem bestimmten Knoten verknüpft ist. Die Stile in den CSS-Dateien geben das Erscheinungsbild der Symbolleiste an. ** fscVCSS ist ein Stylesheet für eine vertikale Symbolleiste, das links neben dem gerenderten HTML-Formular angezeigt wird. ** fscIECSS ist ein Stylesheet, das für HTML-Formulare verwendet wird, die in Internet Explorer wiedergegeben werden.

Vergewissern Sie sich, dass in der Datei &quot;fscmenu.xml&quot;auf alle oben genannten Dateien verwiesen wird. Das heißt, in der Datei &quot;fscmenu.xml&quot;geben Sie URI-Speicherorte an, die auf diese Dateien verweisen, damit der Forms-Dienst sie finden kann. Standardmäßig sind diese Dateien an URI-Positionen verfügbar, beginnend mit internen Suchbegriffen `FSWebRoot` oder `ApplicationWebRoot`.

Um die Symbolleiste anzupassen, ersetzen Sie die Suchbegriffe mit dem externen Suchbegriff `FSToolBarURI`. Dieser Suchbegriff stellt den URI dar, der zur Laufzeit an den Forms-Dienst übergeben wird (dieser Ansatz wird weiter unten in diesem Abschnitt gezeigt).

Sie können auch die absoluten Speicherorte dieser JS- und CSS-Dateien angeben, z. B. https://www.mycompany.com/scripts/misc/fscmenu.js. In diesem Fall müssen Sie das Schlüsselwort `FSToolBarURI` nicht verwenden.

>[!NOTE]
>
>Es wird nicht empfohlen, die Arten zu mischen, auf die diese Dateien verwiesen werden. Das heißt, alle URIs sollten entweder mit dem Schlüsselwort `FSToolBarURI` oder einem absoluten Speicherort referenziert werden.

Sie können die JS- und CSS-Dateien abrufen, indem Sie die Datei &quot;adobe-forms-.ear&quot;öffnen. Öffnen Sie in dieser Datei &quot;adobe-forms-res.war&quot;. Alle diese Dateien befinden sich in der WAR-Datei. Die Datei &quot;adobe-forms-&lt;Anwendungsserver>.ear&quot;befindet sich im Installationsordner für AEM Formulare (C:\ is the installation directory). Sie können die Datei &quot;adobe-forms-&lt;Anwendungsserver>.ear&quot;mit einem Extraktion-Tool wie WinRAR öffnen.

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
>Der fettgedruckte Text stellt die URIs der CSS- und JS-Dateien dar, auf die verwiesen werden muss.

Die folgenden Elemente beschreiben, wie Sie eine Symbolleiste anpassen können:

* Ändern Sie die Werte der Attribute `fscJS`, `fscCSS`, `fscVCSS`, `fscIECSS` (in der Datei &quot;fscmenu.xml&quot;), um die benutzerdefinierten Speicherorte der referenzierten Dateien anzuzeigen, indem Sie eine der in diesem Abschnitt beschriebenen Methoden verwenden (z. B. `fscJS="FSToolBarURI/scripts/fscmenu.js"`).
* Alle CSS- und JS-Dateien müssen angegeben werden. Wenn keine der Dateien geändert wurde, geben Sie die Standarddatei am benutzerdefinierten Speicherort an. Sie können die Standarddateien abrufen, indem Sie verschiedene Dateien öffnen, wie in diesem Abschnitt beschrieben.
* Die Angabe eines absoluten Verweises (z. B. https://www.example.com/scripts/custom-vertical-fscmenu.css) für eine beliebige Datei ist zulässig.
* Die JS- und CSS-Dateien, die der Knoten `div#fscmenu` benötigt, sind für die Symbolleistenfunktion unverzichtbar. Einzelne `ul#fscmenuItem`-Knoten können JS- oder CSS-Dateien unterstützen oder nicht.

**Ändern des lokalen Werts**

Beim Anpassen einer Symbolleiste können Sie den Gebietsschemawert der Symbolleiste ändern. Das heißt, man kann es in einer anderen Sprache anzeigen. Die folgende Abbildung zeigt eine benutzerdefinierte Symbolleiste, die auf Französisch angezeigt wird.

>[!NOTE]
>
>Es ist nicht möglich, eine benutzerdefinierte Symbolleiste in mehr als einer Sprache zu erstellen. Symbolleisten können keine unterschiedlichen XML-Dateien verwenden, die auf den Gebietsschemaeinstellungen basieren.

Um den Gebietsschemawert einer Symbolleiste zu ändern, stellen Sie sicher, dass die Datei &quot;fscmenu.xml&quot;die anzuzeigende Sprache enthält. Die folgende XML-Syntax zeigt die Datei &quot;fscmenu.xml&quot;, mit der eine französische Symbolleiste angezeigt wird.

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
>Die mit diesem Abschnitt verknüpften Quick-Beginn verwenden diese XML-Datei, um eine benutzerdefinierte französische Symbolleiste anzuzeigen, wie in der vorherigen Abbildung gezeigt.

Geben Sie außerdem einen gültigen Gebietsschemawert an, indem Sie die `HTMLRenderSpec`-Methode des Objekts `setLocale` aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt. Geben Sie beispielsweise `fr_FR` an, um Französisch anzugeben. Der Forms-Dienst ist mit lokalisierten Symbolleisten gebündelt.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular wiedergeben, das eine benutzerdefinierte Symbolleiste verwendet, müssen Sie wissen, wie HTML-Formulare wiedergegeben werden. (Siehe [Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md).)

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein HTML-Formular mit einer benutzerdefinierten Symbolleiste:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Java API-Objekt.
1. Verweisen Sie auf eine benutzerdefinierte XML-Datei fscmenu.
1. Wiedergabe eines HTML-Formulars
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Forms Java API-Objekt erstellen**

Bevor Sie einen vom Forms-Dienst unterstützten Vorgang programmatisch ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**Verweisen auf eine benutzerdefinierte XML-Datei fscmenu**

Um ein HTML-Formular mit einer benutzerdefinierten Symbolleiste wiederzugeben, verweisen Sie auf eine XML-Datei fscmenu, die die Symbolleiste beschreibt. (Dieser Abschnitt enthält zwei Beispiele für eine XML-Datei &quot;fscmenu&quot;.) Stellen Sie außerdem sicher, dass die Datei &quot;fscmenu.xml&quot;die Speicherorte aller referenzierten Dateien korrekt angibt. Wie oben in diesem Abschnitt erwähnt, stellen Sie sicher, dass alle Dateien entweder durch das `FSToolBarURI`-Schlüsselwort oder durch ihre absoluten Speicherorte referenziert werden.

**HTML-Formular wiedergeben**

Um ein HTML-Formular wiederzugeben, geben Sie einen Formularentwurf an, der in Designer erstellt und als XDP-Datei gespeichert wurde. Wählen Sie auch einen HTML-Konvertierungstyp aus. Sie können beispielsweise den HTML-Umwandlungstyp angeben, der ein dynamisches HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte wie URI-Werte für die Wiedergabe anderer Formulartypen erforderlich.

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein HTML-Formular wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie an den Client-Webbrowser schreiben müssen, damit das HTML-Formular für Benutzer sichtbar wird.

**Siehe auch**

[Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API](#render-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Web-Service-API](#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interaktive PDF forms wiedergeben](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Forms als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API {#render-an-html-form-with-a-custom-toolbar-using-the-java-api}

Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Forms Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Java API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen auf eine benutzerdefinierte XML-Datei fscmenu

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt mit dem Konstruktor.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec`-Methode des Objekts `setHTMLToolbar` auf und übergeben Sie einen `HTMLToolbar`-Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der XML-Datei &quot;fscmenu&quot;an, indem Sie die `setToolbarURI`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den URI-Speicherort der XML-Datei angibt.`HTMLRenderSpec`
   * Legen Sie ggf. den Gebietsschemawert fest, indem Sie die `HTMLRenderSpec`-Methode des Objekts und einen Zeichenfolgenwert, der den Gebietsschemawert angibt, aufrufen. `setLocale` Der Standardwert ist Englisch.

   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Quick-Beginn setzen diesen Wert auf `fr_FR`*.*

1. HTML-Formular wiedergeben

   Rufen Sie die `renderHTMLForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderHTMLForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse`-Methode des Objekts `getOutputStream` aufrufen.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es mit dem Formulardatenstream, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Quick Beginn (SOAP-Modus): Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Webdienst-API {#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api}

Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Forms Service API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Java API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Verweisen auf eine benutzerdefinierte XML-Datei fscmenu

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt mit dem Konstruktor.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec`-Methode des Objekts `setHTMLToolbar` auf und übergeben Sie einen `HTMLToolbar`-Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der XML-Datei &quot;fscmenu&quot;an, indem Sie die `setToolbarURI`-Methode des Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den URI-Speicherort der XML-Datei angibt.`HTMLRenderSpec`
   * Legen Sie ggf. den Gebietsschemawert fest, indem Sie die `HTMLRenderSpec`-Methode des Objekts und einen Zeichenfolgenwert, der den Gebietsschemawert angibt, aufrufen. `setLocale` Der Standardwert ist Englisch.

   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Quick-Beginn setzen diesen Wert auf `fr_FR`*.*

1. HTML-Formular wiedergeben

   Rufen Sie die `renderHTMLForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Enum-Wert, der den HTML-Voreinstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Header-Wert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322`). Sie können eine leere Zeichenfolge übergeben, wenn Sie diesen Wert nicht festlegen möchten.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dieser Parameter ist optional und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das mit der `renderHTMLForm`-Methode gefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das mit der `renderHTMLForm`-Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das mit der `renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das mit der `renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das mit der `renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Renderwert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderHTMLForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder`-Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse`-Methode des Objekts `getOutputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
