---
title: Verwenden von Schnellansichten zum Erstellen von benutzerdefinierten Popups
seo-title: Verwenden von Schnellansichten zum Erstellen von benutzerdefinierten Popups
description: Die standardmäßige Schnellansicht wird in eCommerce-Anwendungen eingesetzt, in denen ein Popupfenster mit Produktinformationen angezeigt wird, um eine Kaufentscheidung zu fördern. Sie können benutzerdefinierte Inhalte auslösen, die in Popups angezeigt werden.
seo-description: Die standardmäßige Schnellansicht wird in eCommerce-Anwendungen eingesetzt, in denen ein Popupfenster mit Produktinformationen angezeigt wird, um eine Kaufentscheidung zu fördern. Sie können benutzerdefinierte Inhalte auslösen, die in Popups angezeigt werden.
uuid: b906cfff-ac44-4989-b6da-8a9bbf02af03
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4bcab3f4-500f-432e-b16b-cdc26b9bab4d
translation-type: tm+mt
source-git-commit: 73c2b5ee4d60eae253af537ccadccd9952300d3a

---


# Verwenden von Schnellansichten zum Erstellen von benutzerdefinierten Popups {#using-quickviews-to-create-custom-pop-ups}

Die standardmäßige Schnellansicht wird in eCommerce-Anwendungen eingesetzt, in denen ein Popupfenster mit Produktinformationen angezeigt wird, um eine Kaufentscheidung zu fördern. Sie können jedoch benutzerdefinierte Inhalte auslösen, die in Popups angezeigt werden. Abhängig von dem von Ihnen verwendeten Viewer, können Benutzer mit dieser Funktion auf einen Hotspot, ein Miniaturbild oder auf eine Imagemap klicken, um Informationen oder zugehörige Inhalte anzuzeigen.

Schnellansichten werden in Dynamic Media von folgenden Viewern unterstützt:

* Interaktive Bilder (klickbare Hotspots)
* Interaktives Video (klickbare Miniaturbilder während der Videowiedergabe)
* Karussellbanner (klickbare Hotspots oder Imagemaps)

Auch wenn die Funktionalität der Viewer unterschiedlich ist, ist der Prozess zum Erstellen einer Schnellansicht für alle drei unterstützten Viewer identisch.

**So erstellen Sie mit QuickViews benutzerdefinierte Popups**

1. Erstellen Sie eine Schnellansicht für ein hochgeladenes Asset.

   In der Regel erstellen Sie eine Schnellansicht, wenn Sie ein Asset zur Verwendung mit dem Viewer bearbeiten, den Sie benutzen.

   <table>
    <tbody>
    <tr>
    <td><strong>Derzeit verwendeter Viewer </strong></td>
    <td><strong>Führen Sie die folgenden Schritte aus, um die Schnellansicht zu erstellen</strong></td>
    </tr>
    <tr>
    <td>Interaktive Bilder</td>
    <td><a href="/help/assets/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">Hinzufügen von Hotspots zu einem Bildbanner</a>.</td>
    </tr>
    <tr>
    <td>Interaktive Videos</td>
    <td><a href="/help/assets/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">Hinzufügen von Interaktivität zum Video</a>.</td>
    </tr>
    <tr>
    <td>Karussellbanner</td>
    <td><a href="/help/assets/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">Hinzufügen von Hotspots oder Imagemaps zu einem Bildbanner</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Rufen Sie den Einbettungscode für den Viewer ab, um den Viewer in Ihre Website zu integrieren.

   <table>
    <tbody>
    <tr>
    <td><strong>Derzeit verwendeter Viewer</strong><br />  </td>
    <td><strong>Führen Sie die folgenden Schritte aus, um den Viewer in Ihre Website zu integrieren</strong></td>
    </tr>
    <tr>
    <td>Interaktives Bild</td>
    <td><a href="/help/assets/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Integrieren eines interaktiven Bildes auf Ihrer Website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Interaktive Videos<br /> </td>
    <td><a href="/help/assets/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Integrating an interactive video with your website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Karussell-Banner</td>
    <td><a href="/help/assets/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Adding a carousel banner to your website page</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Der Viewer, den Sie verwenden, muss jetzt erfahren, wie die Schnellansicht verwendet werden soll.

   Hierzu nutzt der Viewer einen Handler namens `QuickViewActive`.

   **Beispiel** Angenommen, Sie verwenden auf Ihrer Webseite für ein interaktives Bild den folgenden Einbettungscode:

   ![chlimage_1-291](assets/chlimage_1-291.png)

   Der Handler wird mit `setHandlers` in den Viewer geladen:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Mithilfe des obigen Beispiel für Einbettungscode haben wir den folgenden Code:**

   ```xml
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   Learn more about `setHandlers()` method at the following:

   * Interaktiver Bild-Viewer: [https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/r_html5_aem_int_image_viewer_javascriptapiref_sethandlers.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_aem_int_image_viewer_javascriptapiref_sethandlers.html)
   * Interaktiver Video-Viewer: [https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/r_html5_aem_int_video_javascriptapiref_sethandlers.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_aem_int_video_javascriptapiref_sethandlers.html)

1. Jetzt müssen Sie den Handler `quickViewActivate` konfigurieren.

   The `quickViewActivate` handler controls the Quickviews in the viewer. Der Handler enthält die Variablenliste und die Funktionsaufrufe, die mit der Schnellansicht verwendet werden. The embed code provides mapping for the SKU variable set in the Quickview as well as a sample `loadQuickView` function call.

   **Variablenzuordnung** Ordnen Sie den in der Schnellansicht enthaltenen SKU-Wert- und allgemeinen Variablen für die Verwendung auf Ihrer Webseite zu:

   `var *variable1*= inData.*quickviewVariable*`

   Der bereitgestellte Einbettungscode enthält ein Zuordnungsbeispiel für die SKU-Variable:

   `var sku=inData.sku`

   Ordnen Sie weitere Variablen aus der Schnellansicht wie folgt zu:

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Funktionsaufruf** Der Handler benötigt außerdem einen Funktionsaufruf, damit die Schnellansicht funktioniert. Die Hostseite muss auf diese Funktion zugreifen können. Der Einbettungscode bietet ein Beispiel für einen Funktionsaufruf:

   `loadQuickView(sku)`

   The sample function call assumes the function `loadQuickView()` exists and is accessible.

   Learn more about `quickViewActivate` method at the following:

   * Interaktiver Bild-Viewer: [https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/c_html5_aem_interactive_image_event_callbacks.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_aem_interactive_image_event_callbacks.html)
   * Interaktiver Video-Viewer: [https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/c_html5_aem_int_video_event_callbacks.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_aem_int_video_event_callbacks.html)
   * Interaktive Datenunterstützung im interaktiven Video-Viewer: [https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/c_html5_aem_int_video_int_data_support.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_aem_int_video_int_data_support.html)

1. Gehen Sie folgendermaßen vor:

   * Entfernen Sie im Einbettungscode die Auskommentierung des Abschnitts „setHandlers“.
   * Ordnen Sie alle weiteren Variablen zu, die in der Schnellansicht enthalten sind.

      * Update the `loadQuickView(sku,*var1*,*var2*)` call if you are adding additional variables.
   * Create a simple `loadQuickView` () function on page, outside of the viewer.

      Die folgende Funktion schreibt z. B. den SKU-Wert in die Browserkonsole:

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Laden Sie eine HTML-Testseite auf einen Webserver hoch und öffnen Sie sie.

      Mit den zugeordneten Variablen aus der Schnellansicht und dem Funktionsaufruf schreibt die Browserkonsole den Variablenwert mithilfe der Beispielfunktion in die Browserkonsole.



1. Sie können jetzt eine Funktion verwenden, um ein einfaches Popup in der Schnellansicht aufzurufen. Im folgenden Beispiel wird ein `DIV` für ein Popup verwendet.
1. Gestalten Sie das Popup-`DIV` wie folgt. Fügen Sie gegebenenfalls Ihren eigenen Stil hinzu.

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Platzieren Sie das Popup-`DIV` im Body-Bereich Ihrer HTML-Seite.

   Für eines der Elemente ist eine ID festgelegt, die mit den SKU-Wert aktualisiert wird, wenn der Benutzer eine Schnellansicht aufruft. Das Beispiel beinhaltet auch eine einfache Schaltfläche, um das Popup-Fenster wieder auszublenden.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Fügen Sie eine Funktion hinzu, um den SKU-Wert im Popupfenster zu aktualisieren. Machen Sie das Popupfenster sichtbar, indem Sie die in Schritt 5 erstellte einfache Funktion durch Folgendes ersetzen:

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Laden Sie eine HTML-Testseite auf Ihren Webserver hoch und öffnen Sie sie. Der Viewer zeigt das Popup-`DIV` an, wenn ein Benutzer eine Schnellansicht aufruft.
1. **Anzeigen des benutzerdefinierten Popup-Fensters im Vollbildmodus**

   Einige Viewer, wie der interaktive Video-Viewer, unterstützen die Anzeige im Vollbildmodus. Wenn Sie das Popupfenster jedoch verwenden, wie in den vorherigen Schritten beschrieben, wird es im Vollbildmodus hinter dem Viewer angezeigt.

   Damit das Popupfenster sowohl im Standard- als auch im Vollbildmodus im Vordergrund angezeigt wird, müssen Sie das Popup mit dem Viewer-Container verbinden. Hierzu können Sie eine zweite Handlermethode nutzen, `initComplete`.

   Der Handler `initComplete` wird aufgerufen, nachdem der Viewer initialisiert wurde.

   ```xml
   "initComplete":function() { code block }
   ```

   Learn more about `init()` method at the following:

   * Interaktiver Bild-Viewer: [https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/r_html5_aem_int_image_viewer_javascriptapiref_init.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_aem_int_image_viewer_javascriptapiref_init.html)
   * Interaktiver Video-Viewer: [https://marketing.adobe.com/resources/help/de_DE/s7/viewers_ref/r_html5_aem_int_video_javascriptapiref_init.html](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/r_html5_aem_int_video_javascriptapiref_init.html)

1. Um das in den vorherigen Schritten beschriebene Popupfenster mit dem Viewer zu verbinden, verwenden Sie den folgenden Code: 

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   Im obigen Code haben wir Folgendes gemacht:

   * Unser benutzerdefiniertes Popupfenster identifiziert.
   * Es aus dem DOM entfernt.
   * Den Viewer-Container identifiziert.
   * Das Popup mit dem Viewer-Container verbunden.

1. Ihr fertiger setHandlers-Code sollte nun etwa wie folgt aussehen (für den interaktiven Video-Viewer):

   ```xml
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. Nachdem die Handler geladen wurden, initialisieren Sie den Viewer:

   `*viewerInstance.*init()`

   **Beispiel** Dieses Beispiel verwendet den interaktiven Bild-Viewer.

   `s7interactiveimageviewer.init()`

   Nachdem Sie den Viewer in Ihre Hostseite eingebettet haben, prüfen Sie, ob die Viewer-Instanz erstellt wird und die Handler geladen werden, bevor der Viewer mit `init()` () aufgerufen wird.

