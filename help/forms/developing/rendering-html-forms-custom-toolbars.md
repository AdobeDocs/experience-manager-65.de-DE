---
title: Rendern von HTML Forms mit CustomToolbars
seo-title: Rendering HTML Forms with CustomToolbars
description: Verwenden Sie den Forms-Service, um eine Symbolleiste anzupassen, die mit einem HTML-Formular gerendert wird. Sie können ein HTML-Formular mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API und einer Web Service-API rendern.
seo-description: Use the Forms service to customize a toolbar that is rendered with an HTML form. You can render an HTML Form with a custom toolbar using the Java API and a Web Service API.
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
workflow-type: ht
source-wordcount: '2345'
ht-degree: 100%

---

# Rendern von HTML Forms mit CustomToolbars {#rendering-html-forms-with-customtoolbars}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Rendern von HTML-Formularen mit benutzerdefinierten Symbolleisten {#rendering-html-forms-with-custom-toolbars}

Mit dem Forms-Service können Sie eine Symbolleiste anpassen, die mit einem HTML-Formular gerendert wird. Eine Symbolleiste kann angepasst werden, um ihr Erscheinungsbild zu ändern, indem Standard-CSS-Stile überschrieben werden, und um dynamisches Verhalten hinzuzufügen, indem Java-Skripte überschrieben werden. Eine Symbolleiste wird mithilfe einer XML-Datei namens „fscmenu.xml“ angepasst. Standardmäßig ruft der Forms-Service diese Datei von einem intern angegebenen URI-Speicherort ab.

>[!NOTE]
>
>Dieser URI-Speicherort befindet sich in der Datei „adobe-forms-core.jar“ innerhalb der Datei „adobe-forms-dsc.jar“. Die Datei „adobe-forms-dsc.jar“ befindet sich im Ordner „C:\Adobe\Adobe_Experience_Manager_forms\“ („C:\“ ist das Installationsverzeichnis). Sie können ein Dateiextraktions-Tool wie Win RAR verwenden, um folgende Datei zu öffnen: adobe.

Sie können die Datei „fscmenu.xml“ von diesem Speicherort kopieren, sie an Ihre Anforderungen anpassen und sie dann an einem benutzerdefinierten URI-Speicherort ablegen. Als Nächstes legen Sie mithilfe der Forms Service-API Laufzeitoptionen fest, damit der Forms-Service Ihre Datei „fscmenu.xml“ aus dem angegebenen Speicherort verwendet. Diese Aktionen führen dazu, dass der Forms-Service ein HTML-Formular rendert, das über eine benutzerdefinierte Symbolleiste verfügt.

Zusätzlich zur Datei „fscmenu.xml“ müssen Sie auch die folgenden Dateien abrufen:

* fscmenu.js
* fscattachments.js
* fscmenu.css
* fscmenu-v.css
* fscmenu-ie.css
* fscdialog.css

fscJS ist das Java-Skript, das mit jedem Knoten verknüpft ist. Es ist erforderlich, einen für den `div#fscmenu`-Knoten und optional für `ul#fscmenuItem`-Knoten bereitzustellen. Die JS-Dateien implementieren die Kernfunktionalität der Symbolleiste und die Standarddateien die Arbeit.

fscCSS ist ein Stylesheet, das mit einem bestimmten Knoten verknüpft ist. Die Stile in den CSS-Dateien geben das Erscheinungsbild der Symbolleiste an. *fscVCSS* ist ein Stylesheet für eine vertikale Symbolleiste, die links neben dem gerenderten HTML-Formular angezeigt wird. *fscIECSS* ist ein Stylesheet, das für HTML-Formulare verwendet wird, die in Internet Explorer gerendert werden.

Stellen Sie sicher, dass in der Datei „fscmenu.xml“ auf alle oben genannten Dateien verwiesen wird. Das heißt, geben Sie in der Datei „fscmenu.xml“ URI-Speicherorte an, um auf diese Dateien zu verweisen, damit der Forms-Service sie finden kann. Standardmäßig sind diese Dateien an URI-Speicherorten verfügbar, die mit den internen Schlüsselwörtern `FSWebRoot` oder `ApplicationWebRoot` beginnen.

Um die Symbolleiste anzupassen, ersetzen Sie die Schlüsselwörter durch das externe Schlüsselwort `FSToolBarURI`. Dieses Schlüsselwort stellt den URI dar, der zur Laufzeit an den Forms-Service übergeben wird (dieser Ansatz wird weiter unten in diesem Abschnitt gezeigt).

Sie können auch die absoluten Speicherorte dieser JS- und CSS-Dateien angeben, z. B. https://www.mycompany.com/scripts/misc/fscmenu.js. In diesem Fall müssen Sie das Schlüsselwort `FSToolBarURI` verwenden.

>[!NOTE]
>
>Es wird nicht empfohlen, die Art und Weise, wie auf diese Dateien verwiesen wird, zu vermischen. Das heißt, auf alle URIs sollte entweder mit dem Schlüsselwort `FSToolBarURI` oder durch Angabe einer absoluten Position verwiesen werden.

Sie können die JS- und CSS-Dateien abrufen, indem Sie die Datei „adobe-forms-&lt;appserver>.ear“ öffnen. Öffnen Sie in dieser Datei „adobe-forms-res.war“. Alle diese Dateien befinden sich in der WAR-Datei. Die Datei „adobe-forms-&lt;appserver>.ear“ befindet sich im Installationsordner für AEM Forms (C:\ ist das Installationsverzeichnis). Sie können die Datei „adobe-forms-&lt;appserver>.ear“ mit einem Dateiextraktions-Tool wie WinRAR öffnen.

Die folgende XML-Syntax zeigt ein Beispiel für eine Datei „fscmenu.xml“.

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

* Ändern Sie die Werte der Attribute `fscJS`, `fscCSS`, `fscVCSS` und `fscIECSS` (in der Datei „fscmenu.xml“), um die benutzerdefinierten Speicherorte der referenzierten Dateien mithilfe einer der in diesem Abschnitt beschriebenen Methoden (z. B. `fscJS="FSToolBarURI/scripts/fscmenu.js"`) wiederzugeben.
* Alle CSS- und JS-Dateien müssen angegeben werden. Wenn keine der Dateien geändert wird, geben Sie die Standarddatei am benutzerdefinierten Speicherort an. Sie können die Standarddateien abrufen, indem Sie verschiedene Dateien öffnen, wie in diesem Abschnitt beschrieben.
* Die Bereitstellung einer absoluten Referenz (z. B. https://www.example.com/scripts/custom-vertical-fscmenu.css) für jede Datei ist zulässig.
* Die JS- und CSS-Dateien, die der Knoten `div#fscmenu` erfordert, sind für die Symbolleistenfunktion unverzichtbar. Einzelne `ul#fscmenuItem`-Knoten können unterstützende JS- oder CSS-Dateien enthalten oder nicht.

**Ändern des Gebietsschemawerts**

Beim Anpassen einer Symbolleiste können Sie den Gebietsschemawert der Symbolleiste ändern. Das heißt, Sie können sie in einer anderen Sprache anzeigen. Die folgende Abbildung zeigt eine benutzerdefinierte Symbolleiste, die auf Französisch angezeigt wird.

>[!NOTE]
>
>Es ist nicht möglich, eine benutzerdefinierte Symbolleiste in mehreren Sprachen zu erstellen. Symbolleisten können basierend auf den Gebietsschemaeinstellungen keine anderen XML-Dateien verwenden.

Um den Gebietsschemawert einer Symbolleiste zu ändern, stellen Sie sicher, dass die Datei fscmenu.xml die Sprache enthält, die angezeigt werden soll. Die folgende XML-Syntax zeigt die Datei fscmenu.xml, die zum Anzeigen einer französischen Symbolleiste verwendet wird.

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

Geben Sie außerdem einen gültigen Gebietsschemawert an, indem Sie die `setLocale`-Methode für das `HTMLRenderSpec`-Objekt verwenden und einen Zeichenfolgenwert übergeben, der den Gebietsschema-Wert festlegt. Übergeben Sie beispielsweise `fr_FR`, um Französisch festzulegen. Der Forms-Service ist mit lokalisierten Symbolleisten gebündelt.

>[!NOTE]
>
>Bevor Sie ein HTML-Formular rendern, das eine benutzerdefinierte Symbolleiste verwendet, müssen Sie wissen, wie HTML-Formulare gerendert werden. (Siehe [Rendern von Formularen als HTML](/help/forms/developing/rendering-forms-html.md).)

Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein HTML-Formular mit einer benutzerdefinierten Symbolleiste zu rendern, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Java-API-Objekt.
1. Referenzieren Sie eine benutzerdefinierte fscmenu-XML-Datei.
1. Rendern Sie ein HTML-Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen eines Forms-Java-API-Objekts**

Bevor Sie einen vom Forms-Service unterstützten Vorgang programmgesteuert ausführen können, müssen Sie ein Forms-Client-Objekt erstellen.

**Referenzieren einer benutzerdefinierten fscmenu-XML-Datei**

Um ein HTML-Formular mit einer benutzerdefinierten Symbolleiste wiederzugeben, referenzieren Sie eine fscmenu-XML-Datei, die die Symbolleiste beschreibt. (Dieser Abschnitt enthält zwei Beispiele für eine fscmenu-XML-Datei.) Stellen Sie außerdem sicher, dass die Datei fscmenu.xml die Speicherorte aller referenzierten Dateien richtig angibt. Stellen Sie wie zuvor in diesem Abschnitt erwähnt sicher, dass alle Dateien durch das Keyword `FSToolBarURI` oder ihre absoluten Positionen referenziert werden.

**Rendern eines HTML-Formulars**

Um ein HTML-Formular zu rendern, geben Sie ein Formular-Design an, das in Designer erstellt und als XDP-Datei gespeichert wurde. Wählen Sie auch einen HTML-Transformationstyp aus. Sie können beispielsweise den HTML-Transformationstyp angeben, der dynamische HTML für Internet Explorer 5.0 oder höher rendert.

Für die Wiedergabe eines HTML-Formulars sind auch Werte erforderlich, z. B. URI-Werte für das Rendern anderer Formulartypen.

**Schreiben des Formulardaten-Streams in den Client-Webbrowser**

Wenn der Forms-Service ein HTML-Formular rendert, wird ein Formulardaten-Stream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen, damit das HTML-Formular für Benutzer sichtbar wird.

**Siehe auch**

[Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API](#render-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Web-Service-API](#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Rendern von Formularen als HTML](/help/forms/developing/rendering-forms-html.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API {#render-an-html-form-with-a-custom-toolbar-using-the-java-api}

Rendern eines HTML-Formular mit einer benutzerdefinierten Symbolleiste mithilfe der Forms-Service-API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms-Java-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Verweisen Sie auf eine benutzerdefinierte fscmenu-XML-Datei

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt mithilfe seines Konstruktors.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `setHTMLToolbar`-Methode des `HTMLRenderSpec`-Objekts auf und übergeben Sie einen `HTMLToolbar`-Aufzählungswert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der fscmenu-XML-Datei an, indem Sie die `setToolbarURI`-Methode des `HTMLRenderSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den URI-Speicherort der XML-Datei angibt.
   * Legen Sie ggf. den Gebietsschemawert fest, indem Sie die `setLocale`-Methode des `HTMLRenderSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt. Der Standardwert ist Englisch.

   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Quick Starts setzen diesen Wert auf `fr_FR`*.*

1. Rendern Sie ein HTML-Formular

   Rufen Sie die `renderHTMLForm`-Methode des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf ein Formular-Design verweisen, das Teil einer Forms-Applikation ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Aufzählungswert, der den HTML-Einstellungstyp angibt. Um beispielsweise ein HTML-Formular wiederzugeben, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * A `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den Kopfzeilenwert `HTTP_USER_AGENT` angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianhänge speichert. Dies ist ein optionaler Parameter, und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderHTMLForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstrom enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `getOutputContent`-Methode des `FormsResult`-Objekts aufrufen.
   * Rufen Sie den Content-Typ des `com.adobe.idp.Document`-Objekts ab, indem Sie seine `getContentType`-Methode aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine `setContentType`-Methode aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das verwendet wird, um den Formular-Datenstrom in den Client-Webbrowser zu schreiben, indem Sie die `getOutputStream`-Methode des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `getInputStream`-Methode des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es mit dem Formular-Datenstrom, indem Sie die `read`-Methode des `InputStream`-Objekts aufrufen und das Byte-Array als ein Argument übergeben.
   * Rufen Sie die `write`-Methode des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formular-Datenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Quick Start (SOAP-Modus): Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rendern eines HTML-Formulars mit einer benutzerdefinierten Symbolleiste mithilfe der Web-Service-API {#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api}

Rendern Sie ein HTML-Formular mit einer benutzerdefinierten Symbolleiste mithilfe der Forms Service-API (Web-Service):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms-Java-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Verweisen Sie auf eine benutzerdefinierte fscmenu-XML-Datei

   * Erstellen Sie ein `HTMLRenderSpec`-Objekt, indem Sie seinen Konstruktor verwenden.
   * Um ein HTML-Formular mit einer Symbolleiste wiederzugeben, rufen Sie die `setHTMLToolbar`-Methode des `HTMLRenderSpec`-Objekts auf und übergeben Sie einen `HTMLToolbar`-Aufzählungswert. Um beispielsweise eine vertikale HTML-Symbolleiste anzuzeigen, übergeben Sie `HTMLToolbar.Vertical`.
   * Geben Sie den Speicherort der fscmenu-XML-Datei an, indem Sie die `setToolbarURI`-Methode des `HTMLRenderSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den URI-Speicherort der XML-Datei angibt.
   * Legen Sie ggf. den Gebietsschemawert fest, indem Sie die `setLocale`-Methode des `HTMLRenderSpec`-Objekts aufrufen und einen Zeichenfolgenwert übergeben, der den Gebietsschemawert angibt. Der Standardwert ist Englisch.

   >[!NOTE]
   >
   >Die mit diesem Abschnitt verknüpften Quick Starts setzen diesen Wert auf `fr_FR`*.*

1. Rendern Sie ein HTML-Formular

   Rufen Sie die `renderHTMLForm`-Methode des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf ein Formular-Design verweisen, das Teil einer Forms-Applikation ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `TransformTo`-Aufzählungswert, der den HTML-Einstellungstyp angibt. Um beispielsweise ein HTML-Formular zu rendern, das mit dynamischem HTML für Internet Explorer 5.0 oder höher kompatibel ist, geben Sie `TransformTo.MSDHTML` an.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Das `HTMLRenderSpec`-Objekt, das HTML-Laufzeitoptionen speichert.
   * Ein Zeichenfolgenwert, der den `HTTP_USER_AGENT`-Kopfzeilenwert angibt, z. B. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322`). Wenn Sie diesen Wert nicht festlegen möchten, können Sie eine leere Zeichenfolge übergeben.
   * Ein `URLSpec`-Objekt, das URI-Werte speichert, die zum Rendern eines HTML-Formulars erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dieser Parameter ist optional und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der `renderHTMLForm`-Methode gefüllt wird. Dieser Parameterwert speichert das gerenderte Formular.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der `renderHTMLForm`-Methode gefüllt wird. Dieser Parameter speichert die XML-Ausgabedaten.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der `renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der `renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der `renderHTMLForm`-Methode gefüllt wird. Dieses Argument speichert den verwendeten HTML-Rendering-Wert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderHTMLForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert mit einem Formulardatenstrom übergeben wird, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt durch Abrufen des Werts des `value`-Datenelements des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, durch Aufrufen der `getOutputContent`-Methode des `FormsResult`-Objekts.
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts durch Aufrufen seiner `getContentType`-Methode ab.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse`-Objekts durch Aufrufen seiner `setContentType`-Methode und Übergeben des Inhaltstyps des `BLOB`-Objekt fest.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstroms in den Client-Webbrowser verwendet wird, durch Aufrufen der `getOutputStream`-Methode des `javax.servlet.http.HttpServletResponse`-Objekts.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `getBinaryData`-Methode des `BLOB`-Objekts. Diese Aufgabe weist den Inhalt des `FormsResult`-Objekts zum Byte-Array zu.
   * Rufen Sie die `write`-Methode des `javax.servlet.http.HttpServletResponse`-Objekts zum Senden des Formulardatenstroms an den Client-Webbrowser auf. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
