---
title: Erstellen benutzerdefinierter Popups mithilfe der Schnellansicht
seo-title: Verwenden der Schnellansicht zum Erstellen benutzerdefinierter Popups
description: Die standardmäßige Schnellansicht wird in E-Commerce-Erlebnissen eingesetzt, in denen ein Popup-Fenster mit Produktinformationen angezeigt wird, um eine Kaufentscheidung zu fördern. Sie können benutzerdefinierte Inhalte auslösen, die in Popups angezeigt werden.
seo-description: Die standardmäßige Schnellansicht wird in E-Commerce-Erlebnissen eingesetzt, in denen ein Popup-Fenster mit Produktinformationen angezeigt wird, um eine Kaufentscheidung zu fördern. Sie können benutzerdefinierte Inhalte auslösen, die in Popups angezeigt werden.
uuid: b906cfff-ac44-4989-b6da-8a9bbf02af03
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 4bcab3f4-500f-432e-b16b-cdc26b9bab4d
feature: Viewer
role: Business Practitioner, Administrator
exl-id: 4e7f17ea-6985-4644-b91c-2c1299d01321
source-git-commit: c59ec6e2429095c07c9b2d6bb83dad6ab4f80aa0
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 68%

---

# Verwenden der Schnellansicht zum Erstellen benutzerdefinierter Popups {#using-quickviews-to-create-custom-pop-ups}

Die standardmäßige Schnellansicht wird in E-Commerce-Erlebnissen eingesetzt, in denen ein Popup-Fenster mit Produktinformationen angezeigt wird, um eine Kaufentscheidung zu fördern. Sie können jedoch benutzerdefinierte Inhalte auslösen, die in Popups angezeigt werden. Je nach Viewer können Benutzer mit dieser Funktion auf einen Hotspot, eine Miniaturansicht oder eine Imagemap tippen, um Informationen oder verwandte Inhalte anzuzeigen.

Die Schnellansicht wird von den folgenden Viewern in Dynamic Media unterstützt:

* Interaktive Bilder (klickbare Hotspots)
* Interaktives Video (klickbare Miniaturbilder während der Videowiedergabe)
* Karussellbanner (klickbare Hotspots oder Imagemaps)

Auch wenn die Funktionalität der Viewer unterschiedlich ist, ist der Prozess zum Erstellen einer Schnellansicht für alle drei unterstützten Viewer identisch.

**So erstellen Sie mithilfe der Schnellansicht benutzerdefinierte Popups:**

1. Erstellen Sie eine Schnellansicht für ein hochgeladenes Asset.

   In der Regel erstellen Sie eine Schnellansicht, wenn Sie ein Asset zur Verwendung mit dem Viewer bearbeiten, den Sie benutzen.

   <table>
    <tbody>
    <tr>
    <td><strong>Derzeit verwendeter Viewer</strong></td>
    <td><strong>Führen Sie diese Schritte aus, wenn Sie die Schnellansicht erstellen möchten</strong></td>
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

1. Rufen Sie den Einbettungs-Code für den Viewer ab, um den Viewer in Ihre Website zu integrieren.

   <table>
    <tbody>
    <tr>
    <td><strong>Derzeit verwendeter Viewer</strong><br /> </td>
    <td><strong>Führen Sie diese Schritte aus, wenn Sie den Viewer in Ihre Website integrieren möchten</strong></td>
    </tr>
    <tr>
    <td>Interaktives Bild</td>
    <td><a href="/help/assets/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Integrieren eines interaktiven Bildes auf Ihrer Website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Interaktives Video<br /> </td>
    <td><a href="/help/assets/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Integrieren eines interaktiven Videos mit Ihrer Website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Karussellbanner</td>
    <td><a href="/help/assets/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Hinzufügen eines Karussellbanners zu Ihrer Website</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Der Viewer, den Sie jetzt verwenden, muss wissen, wie die Schnellansicht verwendet werden soll.

   Der Viewer verwendet einen Handler mit dem Namen `QuickViewActive`.

   ****
BeispielAngenommen, Sie verwenden den folgenden Einbettungscode auf Ihrer Web-Seite für ein interaktives Bild:

   ![chlimage_1-291](assets/chlimage_1-291.png)

   Der Handler wird mit `setHandlers` in den Viewer geladen:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Unter Verwendung des obigen Einbettungscode-Beispiels gibt es den folgenden Code:**

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

   Hier finden Sie weitere Informationen zur Methode `setHandlers()`:

   * Interaktiver Bild-Viewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html?lang=de)
   * Interaktiver Video-Viewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html?lang=de)

1. Jetzt müssen Sie den Handler `quickViewActivate` konfigurieren.

   Der Handler `quickViewActivate` steuert die Schnellansicht im Viewer. Der Handler enthält die Variablenliste und die Funktionsaufrufe, die mit der Schnellansicht verwendet werden. Der Einbettungscode stellt die Zuordnung für die SKU-Variable bereit, die in der Schnellansicht festgelegt wurde, und einen Beispielaufruf der Funktion `loadQuickView` .

   **Variablenzuordnung**
Ordnen Sie Variablen für die Verwendung auf Ihrer Web-Seite dem in der Schnellansicht enthaltenen SKU-Wert und den allgemeinen Variablen zu:

   `var *variable1*= inData.*quickviewVariable*`

   Der bereitgestellte Einbettungs-Code enthält ein Zuordnungsbeispiel für die SKU-Variable:

   `var sku=inData.sku`

   Ordnen Sie weitere Variablen aus der Schnellansicht wie folgt zu:

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Funktionsaufruf**
Der Handler benötigt außerdem einen Funktionsaufruf, damit die Schnellansicht funktioniert. Die Host-Seite muss auf diese Funktion zugreifen können. Der Einbettungs-Code bietet ein Beispiel für einen Funktionsaufruf:

   `loadQuickView(sku)`

   Im Beispiel für einen Funktionsaufruf wird davon ausgegangen, dass die Funktion `loadQuickView()` vorhanden und verfügbar ist.

   Hier finden Sie weitere Informationen zur Methode `quickViewActivate`:

   * Interaktiver Bild-Viewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html?lang=de)
   * Interaktiver Video-Viewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html?lang=de)
   * Unterstützung interaktiver Daten im interaktiven Video-Viewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html?lang=de)

1. Gehen Sie folgendermaßen vor:

   * Entfernen Sie im Einbettungs-Code die Auskommentierung des Abschnitts „setHandlers“.
   * Ordnen Sie alle weiteren Variablen zu, die in der Schnellansicht enthalten sind.

      * Aktualisieren Sie den Aufruf `loadQuickView(sku,*var1*,*var2*)`, wenn Sie weitere Variablen hinzufügen.
   * Erstellen Sie auf der Seite eine einfache `loadQuickView` ()-Funktion außerhalb des Viewers.

      Die folgende Funktion schreibt z. B. den SKU-Wert in die Browser-Konsole:

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Laden Sie eine HTML-Testseite auf einen Webserver hoch und öffnen Sie sie.

      Mit den zugeordneten Variablen aus der Schnellansicht und dem Funktionsaufruf schreibt die Browser-Konsole den Variablenwert mithilfe der Beispielfunktion in die Browser-Konsole.



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

   Eines der Elemente wird mit einer ID festgelegt, die mit dem SKU-Wert aktualisiert wird, wenn der Benutzer eine Schnellansicht aufruft. Das Beispiel beinhaltet auch eine einfache Schaltfläche, um das Popup-Fenster wieder auszublenden.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Fügen Sie eine Funktion hinzu, damit Sie den SKU-Wert im Popup-Fenster aktualisieren können. das Popup-Fenster sichtbar machen, indem die in Schritt 5 erstellte einfache Funktion ersetzt wird. durch Folgendes ersetzen:

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

   Einige Viewer, wie der interaktive Video-Viewer, unterstützen die Anzeige im Vollbildmodus. Wenn Sie das Popup-Fenster jedoch verwenden, wie in den vorherigen Schritten beschrieben, wird es im Vollbildmodus hinter dem Viewer angezeigt.

   Damit das Popup-Fenster sowohl im Standard- als auch im Vollbildmodus im Vordergrund angezeigt wird, müssen Sie das Popup mit dem Viewer-Container verbinden. Verwenden Sie eine zweite Handler-Methode, `initComplete`.

   Der Handler `initComplete` wird aufgerufen, nachdem der Viewer initialisiert wurde.

   ```xml
   "initComplete":function() { code block }
   ```

   Hier finden Sie weitere Informationen zur Methode `init()`:

   * Interaktiver Bild-Viewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html?lang=de)
   * Interaktiver Video-Viewer: [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html?lang=de)

1. Verwenden Sie den folgenden Code, um das in den vorherigen Schritten beschriebene Popup-Fenster an den Viewer anzuhängen:

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   Im obigen Code wurde Folgendes ausgeführt:

   * Benutzerdefiniertes Popup identifiziert.
   * Es aus dem DOM entfernt.
   * Den Viewer-Container identifiziert.
   * Das Popup mit dem Viewer-Container verbunden.

1. Der gesamte setHandlers-Code wird in etwa wie folgt angezeigt (interaktiver Video-Viewer wurde verwendet):

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

   **Beispiel**
Dieses Beispiel verwendet den interaktiven Bild-Viewer.

   `s7interactiveimageviewer.init()`

   Nachdem Sie den Viewer in Ihre Host-Seite eingebettet haben, prüfen Sie, ob die Viewer-Instanz erstellt wird und die Handler geladen werden, bevor der Viewer mit `init()` aufgerufen wird.
