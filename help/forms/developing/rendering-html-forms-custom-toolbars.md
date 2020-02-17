---
title: Wiedergabe von HTML-Formularen mit CustomToolbars
seo-title: Wiedergabe von HTML-Formularen mit CustomToolbars
description: 'null'
seo-description: 'null'
uuid: b9c9464e-ff19-4051-a39b-4ec71c512d10
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 7eb0e8a8-d76a-43f7-a012-c21157b14cd4
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Wiedergabe von HTML-Formularen mit CustomToolbars {#rendering-html-forms-with-customtoolbars}

## Wiedergabe von HTML-Formularen mit benutzerdefinierten Symbolleisten {#rendering-html-forms-with-custom-toolbars}

Mit dem Forms-Dienst können Sie eine Symbolleiste anpassen, die mit einem HTML-Formular wiedergegeben wird. Eine Symbolleiste kann angepasst werden, um ihr Erscheinungsbild zu ändern, indem Standard-CSS-Stile außer Kraft gesetzt und dynamisches Verhalten durch Überschreiben von Java-Skripten hinzugefügt werden. Eine Symbolleiste wird mithilfe einer XML-Datei mit dem Namen &quot;fscmenu.xml&quot;angepasst. Standardmäßig ruft der Forms-Dienst diese Datei von einem intern angegebenen URI-Speicherort ab.

>[!NOTE]
>
>Dieser URI-Speicherort befindet sich in der Datei &quot;adobe-forms-core.jar&quot;, die sich in der Datei &quot;adobe-forms-dsc.jar&quot;befindet. Die Datei &quot;adobe-forms-dsc.jar&quot;befindet sich unter C:\Adobe\Adobe_Experience_Manager_forms\ folder (C:\ is the installation directory). Sie können ein Dateiextrahierungstool wie Win RAR verwenden, um das adobe zu öffnen.

Sie können die Datei &quot;fscmenu.xml&quot;von dieser Position aus kopieren, sie an Ihre Anforderungen anpassen und sie dann an einem benutzerdefinierten URI-Speicherort ablegen. Legen Sie dann mithilfe der Forms Service API Laufzeitoptionen fest, die dazu führen, dass der Forms-Dienst die Datei &quot;fscmenu.xml&quot;vom angegebenen Speicherort aus verwendet. Diese Aktionen führen dazu, dass der Forms-Dienst ein HTML-Formular mit einer benutzerdefinierten Symbolleiste wiedergibt.

Zusätzlich zur Datei &quot;fscmenu.xml&quot;müssen Sie auch die folgenden Dateien abrufen:

* fscmenu.js
* fscattachments.js
* fscmenu.css
* fscmenu-v.css
* fscmenu-ie.css
* fscdialog.css

fscJS ist das Java-Skript, das jedem Knoten zugeordnet ist. Es ist erforderlich, eine für die `div#fscmenu` Node und optional für `ul#fscmenuItem` Nodes bereitzustellen. Die JS-Dateien implementieren die Kern-Symbolleistenfunktion, und die Standarddateien funktionieren.

fscCSS ist ein Stylesheet, das mit einem bestimmten Knoten verknüpft ist. Die Stile in den CSS-Dateien geben das Erscheinungsbild der Symbolleiste an. *fscVCSS* ist ein Stylesheet für eine vertikale Symbolleiste, die links neben dem wiedergegebenen HTML-Formular angezeigt wird. *fscIECSS* ist ein Stylesheet, das für HTML-Formulare verwendet wird, die in Internet Explorer wiedergegeben werden.

Stellen Sie sicher, dass in der Datei &quot;fscmenu.xml&quot;auf alle oben genannten Dateien verwiesen wird. Das heißt, in der Datei &quot;fscmenu.xml&quot;geben Sie URI-Speicherorte an, die auf diese Dateien verweisen, damit der Forms-Dienst sie finden kann. Standardmäßig sind diese Dateien an URI-Positionen verfügbar, beginnend mit internen Suchbegriffen `FSWebRoot` oder `ApplicationWebRoot`.

Um die Symbolleiste anzupassen, ersetzen Sie die Suchbegriffe mit dem externen Suchbegriff `FSToolBarURI`. Dieser Suchbegriff stellt den URI dar, der zur Laufzeit an den Forms-Dienst übergeben wird (dieser Ansatz wird weiter unten in diesem Abschnitt gezeigt).

Sie können auch die absoluten Speicherorte dieser JS- und CSS-Dateien angeben, z. B. https://www.mycompany.com/scripts/misc/fscmenu.js. In diesem Fall müssen Sie den `FSToolBarURI` Suchbegriff nicht verwenden.

>[!NOTE]
>
>Es wird nicht empfohlen, die Arten zu mischen, auf die diese Dateien verwiesen werden. Das heißt, alle URIs sollten entweder mit dem `FSToolBarURI` Suchbegriff oder einem absoluten Speicherort referenziert werden.

Sie können die JS- und CSS-Dateien abrufen, indem Sie die Datei &quot;adobe-forms-.ear&quot;öffnen. Öffnen Sie in dieser Datei adobe-forms-res.war. Alle diese Dateien befinden sich in der WAR-Datei. Die Datei &quot;adobe-forms-&lt;Anwendungsserver>.ear&quot;befindet sich im AEM Forms-Installationsordner (C:\ is the installation directory). Sie können die Datei &quot;adobe-forms-&lt;Anwendungsserver>.ear&quot;mit einem Dateiextraktionstool wie WinRAR öffnen.

Die folgende XML-Syntax zeigt eine Beispieldatei &quot;fscmenu.xml&quot;.

```as3
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

* Ändern Sie die Werte von `fscJS`, `fscCSS``fscVCSS`und `fscIECSS` Attributen (in der Datei &quot;fscmenu.xml&quot;), um die benutzerdefinierten Speicherorte der referenzierten Dateien anzuzeigen, indem Sie eine der in diesem Abschnitt beschriebenen Methoden verwenden (z. B. `fscJS="FSToolBarURI/scripts/fscmenu.js"`).
* Alle CSS- und JS-Dateien müssen angegeben werden. Wenn keine der Dateien geändert wurde, geben Sie die Standarddatei am benutzerdefinierten Speicherort an. Sie können die Standarddateien abrufen, indem Sie verschiedene Dateien öffnen, wie in diesem Abschnitt beschrieben.
* Die Angabe eines absoluten Verweises (z. B. https://www.example.com/scripts/custom-vertical-fscmenu.css) für jede Datei ist zulässig.
* Die JS- und CSS-Dateien, die der `div#fscmenu` Knoten benötigt, sind unverzichtbar für die Symbolleistenfunktion. Einzelne `ul#fscmenuItem` Knoten können JS- oder CSS-Dateien unterstützen oder nicht.

**Ändern des lokalen Werts**

Beim Anpassen einer Symbolleiste können Sie den Gebietsschemawert der Symbolleiste ändern. Das heißt, man kann es in einer anderen Sprache anzeigen. Die folgende Abbildung zeigt eine benutzerdefinierte Symbolleiste, die auf Französisch angezeigt wird.

>[!NOTE]
>
>Es ist nicht möglich, eine benutzerdefinierte Symbolleiste in mehr als einer Sprache zu erstellen. Symbolleisten können keine unterschiedlichen XML-Dateien verwenden, die auf den Gebietsschemaeinstellungen basieren.

Um den Gebietsschemawert einer Symbolleiste zu ändern, stellen Sie sicher, dass die Datei &quot;fscmenu.xml&quot;die anzuzeigende Sprache enthält. Die folgende XML-Syntax zeigt die Datei &quot;fscmenu.xml&quot;, mit der eine französische Symbolleiste angezeigt wird.

```as3
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
>Die mit diesem Abschnitt verknüpften Kurzanleitungen verwenden diese XML-Datei, um eine benutzerdefinierte französische Symbolleiste anzuzeigen, wie in der vorherigen Abbildung gezeigt.

Geben Sie außerdem einen gültigen Gebietsschemawert an, indem Sie die `HTMLRenderSpec` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt. `setLocale` Geben Sie beispielsweise Französisch `fr_FR` an. Der Forms-Dienst ist mit lokalisierten Symbolleisten gebündelt.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular wiedergeben, das eine benutzerdefinierte Symbolleiste verwendet, müssen Sie wissen, wie HTML-Formulare wiedergegeben werden. (Siehe [Wiedergabe von Formularen als HTML](/help/forms/developing/rendering-forms-html.md).)

For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein HTML-Formular mit einer benutzerdefinierten Symbolleiste:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Java-API-Objekt für Forms.
1. Verweisen Sie auf eine benutzerdefinierte XML-Datei fscmenu.
1. Wiedergabe eines HTML-Formulars
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Java-API-Objekt für Forms erstellen**

Bevor Sie einen vom Forms-Dienst unterstützten Vorgang programmatisch ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**Verweisen auf eine benutzerdefinierte XML-Datei fscmenu**

Um ein HTML-Formular mit einer benutzerdefinierten Symbolleiste wiederzugeben, verweisen Sie auf eine XML-Datei fscmenu, die die Symbolleiste beschreibt. (Dieser Abschnitt enthält zwei Beispiele für eine XML-Datei &quot;fscmenu&quot;.) Stellen Sie außerdem sicher, dass die Datei &quot;fscmenu.xml&quot;die Speicherorte aller referenzierten Dateien korrekt angibt. Wie oben in diesem Abschnitt erwähnt, stellen Sie sicher, dass alle Dateien entweder vom `FSToolBarURI` Suchbegriff oder von ihrem absoluten Speicherort referenziert werden.

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

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Wiedergeben interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Wiedergabe von Formularen als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API {#render-an-html-form-with-a-custom-toolbar-using-the-java-api}

Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Forms Service API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Java-API-Objekt für Forms erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen auf eine benutzerdefinierte XML-Datei fscmenu

   * Create an `HTMLRenderSpec` object by using its constructor.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec` Methode des `setHTMLToolbar` Objekts auf und übergeben Sie einen `HTMLToolbar` Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der XML-Datei &quot;fscmenu&quot;an, indem Sie die `HTMLRenderSpec` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den URI-Speicherort der XML-Datei angibt `setToolbarURI` .
   * Legen Sie ggf. den Wert für das Gebietsschema fest, indem Sie die `HTMLRenderSpec` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt, `setLocale` um ihn zu übergeben. Der Standardwert ist Englisch.
   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Schnellstarts setzen diesen Wert auf `fr_FR`*.*

1. HTML-Formular wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `renderHTMLForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo` Enum-Wert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`an.
   * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` Objekt.
   * Das `HTMLRenderSpec` Objekt, in dem HTML-Laufzeitoptionen gespeichert werden.
   * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec` Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   Die `renderHTMLForm` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formulardatenstream, indem Sie die `InputStream` `read` Objektmethode aufrufen und das Bytearray als Argument übergeben.
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Kurzanleitung (SOAP-Modus): Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Web-Service-API {#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api}

Wiedergabe eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Forms Service API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Java-API-Objekt für Forms erstellen

   Erstellen Sie ein `FormsService` Objekt und legen Sie Authentifizierungswerte fest.

1. Verweisen auf eine benutzerdefinierte XML-Datei fscmenu

   * Create an `HTMLRenderSpec` object by using its constructor.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `HTMLRenderSpec` Methode des `setHTMLToolbar` Objekts auf und übergeben Sie einen `HTMLToolbar` Enum-Wert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der XML-Datei &quot;fscmenu&quot;an, indem Sie die `HTMLRenderSpec` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den URI-Speicherort der XML-Datei angibt `setToolbarURI` .
   * Legen Sie ggf. den Wert für das Gebietsschema fest, indem Sie die `HTMLRenderSpec` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt, `setLocale` um ihn zu übergeben. Der Standardwert ist Englisch.
   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Schnellstarts setzen diesen Wert auf `fr_FR`*.*

1. HTML-Formular wiedergeben

   Rufen Sie die `FormsService` Objektmethode `renderHTMLForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo` Enum-Wert, der den HTML-Präferenztyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML`an.
   * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Das `HTMLRenderSpec` Objekt, in dem HTML-Laufzeitoptionen gespeichert werden.
   * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT` Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322`). Sie können eine leere Zeichenfolge übergeben, wenn Sie diesen Wert nicht festlegen möchten.
   * Ein `URLSpec` Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dieser Parameter ist optional und Sie können angeben, `null` ob Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das durch die `renderHTMLForm` Methode gefüllt wird. Dieser Parameterwert speichert das wiedergegebene Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das durch die `renderHTMLForm` Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` Objekt, das durch die `renderHTMLForm` Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das durch die `renderHTMLForm` Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das durch die `renderHTMLForm` Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Renderwert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das die Ergebnisse dieses Vorgangs enthält.
   Die `renderHTMLForm` Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` Objektdatenelements abrufen `value` .
   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des `BLOB` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `BLOB` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
