---
title: Die Anatomie einer App
seo-title: Die Anatomie einer App
description: Diese Seite enthält eine Beschreibung der Seitenkomponenten, die Sie für Ihre App erstellen, basierend auf der Komponente "/libs/mobileapps/components/angular/ng-page"(CRXDE Lite auf einem lokalen Server).
seo-description: Diese Seite enthält eine Beschreibung der Seitenkomponenten, die Sie für Ihre App erstellen, basierend auf der Komponente "/libs/mobileapps/components/angular/ng-page"(CRXDE Lite auf einem lokalen Server).
uuid: 4c1a74c1-85af-4a79-b723-e9fbfc661d35
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 55667e62-a61b-4794-b292-8d54929c41ac
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '2721'
ht-degree: 1%

---


# Die Anatomie einer App{#the-anatomy-of-an-app}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

## Seitenvorlagen für mobile Apps {#page-templates-for-mobile-apps}

Die Seitenkomponenten, die Sie für Ihre App erstellen, basieren auf der Komponente &quot;/libs/mobileapps/components/angular/ng-page&quot;([Öffnen in CRXDE Lite auf einem lokalen Server](http://localhost:4502/crx/de/index.jsp#/libs/mobileapps/components/angular/ng-page)). Diese Komponente enthält die folgenden JSP-Skripte, die Ihre Komponente entweder übernimmt oder außer Kraft setzt:

* ng-page.jsp
* head.jsp
* body.jsp
* angular-app-module.js.jsp
* angular-route-fragment.js.jsp
* angular-app-controllers.js.jsp
* controller.js.jsp
* template.jsp
* angular-module-list.js.jsp
* header.jsp
* footer.jsp
* js_clientlibs.jsp
* css_clientlibs.jsp

### ng-page.jsp {#ng-page-jsp}

Bestimmt den Namen der Anwendung mithilfe der Eigenschaft `applicationName` und stellt sie über pageContext bereit.

Enthält head.jsp und body.jsp.

### head.jsp {#head-jsp}

Schreibt das `<head>`-Element der App-Seite heraus.

Wenn Sie die Viewport-Metadateneigenschaft der App überschreiben möchten, ist dies die Datei, die Sie überschreiben.

Nach den bewährten Verfahren enthält die App den css-Teil der Clientbibliotheken im Kopfabschnitt, während die JS im schließenden &lt; `body>`-Element enthalten ist.

### body.jsp {#body-jsp}

Der Hauptteil einer Angular-Seite wird je nachdem, ob wcmMode erkannt wird (!!= WCMMode.DISABLED), um zu bestimmen, ob die Seite zum Authoring oder als veröffentlichte Seite geöffnet wird.

**Autorenmodus**

Im Autorenmodus wird jede einzelne Seite separat gerendert. &quot;Angular&quot;behandelt kein Routing zwischen Seiten und auch keine ng-Ansicht zum Laden einer Teilvorlage, die die Seitenkomponenten enthält. Stattdessen wird der Inhalt der Seitenvorlage (template.jsp) über das `cq:include`-Tag serverseitig eingeschlossen.

Diese Strategie aktiviert die Autorenfunktionen (z. B. Hinzufügen und Bearbeiten von Komponenten im Absatzsystem, Sidekick, Designmodus usw.) , um ohne Änderung zu funktionieren. Seiten, die auf der clientseitigen Wiedergabe basieren, z. B. für Apps, funktionieren im Autorenmodus nicht gut AEM.

Beachten Sie, dass der include template.jsp in ein `div`-Element mit der Direktive `ng-controller` eingeschlossen ist. Diese Struktur ermöglicht die Verknüpfung des DOM-Inhalts mit dem Controller. Obwohl Seiten, die sich auf der Client-Seite wiedergeben, fehlschlagen, funktionieren einzelne Komponenten, die dies tun, einwandfrei (siehe Abschnitt zu Komponenten unten).

```xml
<div ng-controller="<c:out value="${controllerNameStripped}"/>">
      <cq:include script="template.jsp"/>
</div>
```

**Veröffentlichungsmodus**

Im Veröffentlichungsmodus (z. B. wenn die App mit der Inhaltssynchronisierung exportiert wird) werden alle Seiten zu einer einseitigen App (SPA). (Um mehr über SPA zu erfahren, verwenden Sie das Angular-Lernprogramm, insbesondere [https://docs.angularjs.org/tutorial/step_07](https://docs.angularjs.org/tutorial/step_07).)

Es gibt nur eine HTML-Seite in einem SPA (eine Seite, die das `<html>`-Element enthält). Diese Seite wird als &quot;Layoutvorlage&quot;bezeichnet. In Angular Terminologie ist es &quot;...eine Vorlage, die allen Ansichten in unserer Anwendung gemein ist.&quot; Betrachten Sie diese Seite als &quot;App-Seite der obersten Ebene&quot;. Die App-Seite auf der obersten Navigationsebene ist normalerweise der `cq:Page`-Knoten Ihrer Anwendung, der dem Stammordner am nächsten ist (und keine Umleitung ist).

Da sich der tatsächliche URI Ihrer App im Veröffentlichungsmodus nicht ändert, müssen Verweise auf externe Assets auf dieser Seite relative Pfade verwenden. Daher wird eine spezielle Bildkomponente bereitgestellt, die diese Seite der obersten Ebene beim Rendern von Bildern zum Exportieren berücksichtigt.

Als SPA generiert diese Layoutvorlagenseite einfach ein div-Element mit einer ng-Ansicht-Direktive.

```xml
 <div ng-view ng-class="transition"></div>
```

Der Angular Route Service verwendet dieses Element, um den Inhalt jeder Seite in der App anzuzeigen, einschließlich des maßgeblichen Inhalts der aktuellen Seite (in template.jsp enthalten).

Die Datei &quot;body.jsp&quot;enthält &quot;header.jsp&quot;und &quot;footer.jsp&quot;, die leer sind. Wenn Sie statischen Inhalt auf jeder Seite bereitstellen möchten, können Sie diese Skripten in Ihrer App überschreiben.

Schließlich sind clientlibs für javascript am unteren Rand des Elements &lt;body> enthalten, darunter zwei spezielle JS-Dateien, die auf dem Server generiert werden: *&lt;Seitenname>*.angular-app-module.js und *&lt;Seitenname>*.angular-app-controller.js.

### angular-app-module.js.jsp {#angular-app-module-js-jsp}

Dieses Skript definiert das Angular-Modul der Anwendung. Die Ausgabe dieses Skripts ist mit dem Markup verknüpft, das der Rest der Vorlagenkomponente über das `html`-Element in ng-page.jsp generiert, das das folgende Attribut enthält:

```xml
ng-app="<c:out value='${applicationName}'/>"
```

Dieses Attribut gibt Angular an, dass der Inhalt dieses DOM-Elements mit dem folgenden Modul verknüpft werden soll. Dieses Modul verknüpft die Ansichten (in AEM wären dies cq:Page resources) mit den entsprechenden Controllern.

Dieses Modul definiert auch einen obersten Controller mit dem Namen `AppController`, der die Variable `wcmMode` dem Bereich anzeigt und den URI konfiguriert, aus dem die Nutzdaten für Inhaltssynchronisierung abgerufen werden.

Zuletzt durchläuft dieses Modul jede untergeordnete Seite (einschließlich der Seite selbst) und rendert den Inhalt der Route-Ausrichtung jeder Seite (über den &quot;angular-route-fragment.js selector &amp; extension&quot;), einschließlich des &quot;config&quot;-Eintrags zum $routeProvider von Angular. Mit anderen Worten, der $routeProvider teilt der App mit, welche Inhalte gerendert werden sollen, wenn ein bestimmter Pfad angefordert wird.

### angular-route-fragment.js.jsp {#angular-route-fragment-js-jsp}

Dieses Skript generiert ein JavaScript-Fragment, das das folgende Formular enthalten muss:

```
.when('/<path>', {
    templateUrl: '<path to template>',
    controller: '<controller name>'
})
```

Dieser Code gibt $routeProvider (definiert in angular-app-module.js.jsp) an, dass &#39;/&lt;path>&#39; von der Ressource unter `templateUrl` verarbeitet und von `controller` verdrahtet werden soll (woraufhin wir zur nächsten gelangen).

Bei Bedarf können Sie dieses Skript überschreiben, um komplexere Pfade zu bearbeiten, einschließlich solcher mit Variablen. Ein Beispiel hierfür finden Sie im Skript /apps/geometrixx-outdoors-app/components/angular/ng-template-page/angular-route-fragment.js.jsp, das mit AEM installiert ist:

```xml
// note the :id suffix on the path
.when('<c:out value="${resource.path}"/>/:id', {
    templateUrl: '<c:out value="${relativeResourcePath}"/>.template.html',
    controller: '<c:out value="${controllerNameStripped}"/>'
})
```

### angular-app-controllers.js.jsp {#angular-app-controllers-js-jsp}

In Angular verbinden Controller Variablen im $scope und setzen sie der Ansicht aus. Das angular-app-controllers.js.jsp-Skript folgt dem von angular-app-module.js.jsp illustrierten Muster, da es jede untergeordnete Seite (einschließlich der Seite selbst) durchläuft und das von den einzelnen Seiten definierte Steuerelement-Fragment (über controller.js.jsp) ausgibt. Das Modul, das es definiert, heißt `cqAppControllers` und muss als Abhängigkeit des App-Moduls der obersten Ebene aufgeführt werden, damit die Seiten-Controller verfügbar gemacht werden.

### controller.js.jsp {#controller-js-jsp}

Das Skript controller.js.jsp generiert das Steuerelement-Fragment für jede Seite. Dieses Steuerelement-Fragment hat das folgende Formular:

```
.controller('<c:out value="${controllerNameStripped}"/>', ['$scope', '$http',
    function($scope, $http) {
        var data = $http.get('<c:out value="${relativeResourcePath}"/>.angular.json' + cacheKiller);

        // component fragments which consume the contents of `data` go here
    }
])
```

Beachten Sie, dass der Variablen `data` das von der Angular `$http.get`-Methode zurückgegebene Versprechen zugewiesen wird. Jede auf dieser Seite enthaltene Komponente kann bei Bedarf JSON-Inhalte verfügbar machen (über das Skript &quot;angular.json.jsp&quot;) und beim Auflösen auf den Inhalt dieser Anforderung reagieren. Die Anfrage erfolgt sehr schnell auf mobilen Geräten, da sie einfach auf das Dateisystem zugreift.

Damit eine Komponente auf diese Weise Teil des Controllers sein kann, sollte sie die Komponente /libs/mobileapps/components/angular/ng-component erweitern und die Eigenschaft `frameworkType: angular` einschließen.

### template.jsp {#template-jsp}

Als Erstes im Abschnitt body.jsp eingeführt, enthält template.jsp einfach die Parsys der Seite. Im Veröffentlichungsmodus wird dieser Inhalt direkt (unter &lt;page-path>.template.html) referenziert und über die auf $routeProvider konfigurierte templateUrl in die SPA geladen.

Die Parsys in diesem Skript können so konfiguriert werden, dass sie jeden beliebigen Komponententyp akzeptieren. Allerdings muss bei der Behandlung von Komponenten, die für eine herkömmliche Website erstellt wurden (im Gegensatz zu SPA), Vorsicht geboten werden. Beispielsweise funktioniert die Bildkomponente der Stiftung nur auf der App-Seite der obersten Ebene korrekt, da sie nicht dazu bestimmt ist, auf Assets zu verweisen, die sich in einer App befinden.

### angular-module-list.js.jsp {#angular-module-list-js-jsp}

Dieses Skript gibt einfach die Angular-Abhängigkeiten des Angular-App-Moduls der obersten Ebene aus. Es wird von angular-app-module.js.jsp referenziert.

### header.jsp {#header-jsp}

Ein Skript zum Platzieren von statischem Inhalt am Anfang der App. Dieser Inhalt wird auf der Seite auf der obersten Ebene außerhalb des Bereichs der ng-Ansicht eingeschlossen.

### footer.jsp {#footer-jsp}

Ein Skript zum Platzieren von statischem Inhalt am unteren Rand der App. Dieser Inhalt wird auf der Seite auf der obersten Ebene außerhalb des Bereichs der ng-Ansicht eingeschlossen.

### js_clientlibs.jsp {#js-clientlibs-jsp}

Überschreiben Sie dieses Skript, um Ihre JavaScript-clientlibs einzuschließen.

### css_clientlibs.jsp {#css-clientlibs-jsp}

Überschreiben Sie dieses Skript, um Ihre CSS-clientlibs einzuschließen.

## App-Komponenten {#app-components}

App-Komponenten dürfen nicht nur auf einer AEM Instanz (Veröffentlichungs- oder Autoreninstanz) funktionieren, sondern auch, wenn der Anwendungsinhalt über die Inhaltssynchronisierung in das Dateisystem exportiert wird. Das Bauteil muss daher folgende Merkmale aufweisen:

* Auf alle Assets, Vorlagen und Skripten in einer PhoneGap-Anwendung muss relativ verwiesen werden.
* Die Behandlung von Links unterscheidet sich, wenn die AEM Instanz im Autor- oder Veröffentlichungsmodus ausgeführt wird.

### Relative Assets {#relative-assets}

Der URI eines Assets in einer PhoneGap-Anwendung unterscheidet sich nicht nur pro Plattform, sondern ist bei jeder Installation der App eindeutig. Beachten Sie beispielsweise den folgenden URI einer App, die im iOS-Simulator ausgeführt wird:

`file:///Users/userId/Library/Application%20Support/iPhone%20Simulator/7.0.3/Applications/24BA22ED-7D06-4330-B7EB-F6FC73251CA3/Library/files/www/content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en/home.html`

Beachten Sie die GUID &#39;24BA22ED-7D06-4330-B7EB-F6FC73251CA3&#39; im Pfad.

Als PhoneGap-Entwickler befindet sich der Inhalt, mit dem Sie sich beschäftigen, unterhalb des www-Ordners. Verwenden Sie relative Pfade, um auf die App-Assets zuzugreifen.

Um das Problem zu verschärfen, verwendet Ihre PhoneGap-Anwendung das Muster der einseitigen App (SPA), sodass sich der Basis-URI (ohne Hash) nie ändert. Daher muss jedes Asset, jede Vorlage oder jedes Skript, das bzw. das Sie mit **referenzieren, relativ zu Ihrer Seite der obersten Ebene sein. **Die Seite auf der obersten Ebene initialisiert das Angular-Routing und die Steuerungen anhand von `*<name>*.angular-app-module.js` und `*<name>*.angular-app-controllers.js`. Diese Seite sollte die nächstgelegene Seite zum Stammverzeichnis des Repositorys sein, die *nicht *erweitert ein sling:redirect.

Für den Umgang mit relativen Pfaden stehen verschiedene Hilfsmethoden zur Verfügung:

* FrameworkContentExporterUtils.getTopLevelAppResource
* FrameworkContentExporterUtils.getRelativePathToRootLevel
* FrameworkContentExporterUtils.getPathToAsset

Um Beispiele für ihre Verwendung anzuzeigen, öffnen Sie die mobileapps-Quelle unter /libs/mobileapps/components/angular.

### Links {#links}

Links müssen die Funktion `ng-click="go('/path')"` verwenden, um alle WCM-Modi zu unterstützen. Diese Funktion hängt vom Wert einer Variablen zum Festlegen der Linkaktion ab:

```xml
<c:choose><c:when test="${wcmMode}">
    <%-- WCMMode is enabled - page is being rendered in AEM --%>
    $scope.wcmMode = true;
</c:when><c:otherwise>
    <%-- WCMMode is disabled --%>
    $scope.wcmMode = false;
</c:otherwise></c:choose>
```

Bei `$scope.wcmMode == true` behandeln wir jedes Navigationselement wie gewohnt, sodass das Ereignis eine Änderung des Pfads und/oder Seitenbereichs der URL darstellt.

Wenn `$scope.wcmMode == false`, führt jedes Navigations-Ereignis zu einer Änderung des Hash-Teils der URL, der intern durch das ngRoute-Modul von Angular aufgelöst wird.

### Komponentenskriptdetails {#component-script-details}

![chlimage_1-144](assets/chlimage_1-144.png)

#### ng-component.jsp {#ng-component-jsp}

Dieses Skript zeigt entweder den Komponenteninhalt oder einen geeigneten Platzhalter an, wenn der Bearbeitungsmodus erkannt wird.

#### template.jsp {#template-jsp-1}

Das Skript template.jsp rendert das Markup der Komponente. Wenn die betreffende Komponente durch JSON-Daten aus AEM (z. B. &#39;ng-text&#39;) angetrieben wird: /libs/mobileapps/components/angular/ng-text/template.jsp), wird dieses Skript für die Verdrahtung des Markups mit Daten verantwortlich sein, die vom Kontrollbereich der Seite bereitgestellt werden.

Leistungsanforderungen erfordern jedoch manchmal, dass keine clientseitige Vorlagenbildung (auch Datenbindung genannt) durchgeführt wird. In diesem Fall rendern Sie einfach das Markup der Komponente auf der Serverseite und es ist im Inhalt der Seitenvorlage enthalten.

#### overhead.jsp {#overhead-jsp}

In Komponenten, die von JSON-Daten gesteuert werden (z. B. &quot;ng-text&quot;): /libs/mobileapps/components/angular/ng-text), overhead.jsp kann verwendet werden, um den gesamten Java-Code aus template.jsp zu entfernen. Anschließend wird auf sie von template.jsp verwiesen, und alle Variablen, die sie in der Anforderung bereitstellt, stehen zur Verwendung bereit. Diese Strategie fördert die Trennung der Logik von der Darstellung und schränkt die Menge des Codes ein, der kopiert und eingefügt werden muss, wenn eine neue Komponente von einer vorhandenen abgeleitet wird.

#### controller.js.jsp {#controller-js-jsp-1}

Wie in AEM Seitenvorlagen beschrieben, kann jede Komponente ein JavaScript-Fragment ausgeben, um den von dem Versprechen `data` bereitgestellten JSON-Inhalt zu verbrauchen. Nach Angular-Konventionen sollte ein Controller nur zum Zuweisen von Variablen zum Gültigkeitsbereich verwendet werden.

#### angular.json.jsp {#angular-json-jsp}

Dieses Skript ist als Fragment in der Datei &quot;&lt;page-name>.angular.json&quot;auf der Seite enthalten, das für jede Seite exportiert wird, die die ng-page erweitert. In dieser Datei kann der Komponentenentwickler jede JSON-Struktur bereitstellen, die die Komponente benötigt. Im Beispiel &quot;ng-text&quot;enthält diese Struktur lediglich den Textinhalt der Komponente und ein Flag, das angibt, ob die Komponente Rich Text enthält.

Die Produktkomponente &quot;Geometrixx outdoors-App&quot;ist ein komplexeres Beispiel (/apps/geometrixx-outdoors-app/components/angular/ng-product):

```xml
{
    "content-par/ng-product": {
        "items": [{
            "name": "Cajamara",
            "description": "Bike",
            "summaryHTML": "",
            "price": "$610.00",
            "SKU": "eqsmcj",
            "numberOfLikes": "0",
            "numberOfComments": "0"
        }]
    },
    "content-par/ng-product/ng-image": {
        "items": [{
            "hasContent": true,
            "imgSrc": "home/products/eq/eqsm/eqsmcj/jcr_content/content-par/ng-product/ng-image.img.jpg/1377771306985.jpg",
            "description": "",
            "alt": "Cajamara",
            "title": "Cajamara",
            "hasLink": false,
            "linkPath": "",
            "attributes": [{
                "attributeName": "class",
                "attributeValue": "cq-dd-image"
            }]
        }]
    }
}
```

## Inhalt der heruntergeladenen CLI-Elemente {#contents-of-the-cli-assets-download}

Laden Sie CLI-Assets von der Apps-Konsole herunter, um sie für eine bestimmte Plattform zu optimieren, und erstellen Sie dann die App mit der PhoneGap-Befehlszeilenintegration (CLI)-API. Der Inhalt der ZIP-Datei, die Sie im lokalen Dateisystem speichern, hat folgende Struktur:

```xml
.cordova/
  |- hooks/
     |- after_prepare/
     |- before_platform_add/
     |- Other Hooks
plugins/
www/
  |- config.xml
  |- index.html
  |- res/
  |- etc/
  |- apps/
  |- content/
  |- package.json
  |- package-update.json
```

### .cordova {#cordova}

Dies ist ein ausgeblendeter Ordner, der je nach den aktuellen Betriebssystemeinstellungen möglicherweise nicht angezeigt wird. Sie sollten Ihr Betriebssystem so konfigurieren, dass dieses Verzeichnis angezeigt wird, wenn Sie die darin enthaltenen App-Haken ändern möchten.

#### .cordova/hooks/ {#cordova-hooks}

Dieser Ordner enthält die [CLI-Haken](https://devgirl.org/2013/11/12/three-hooks-your-cordovaphonegap-project-needs/). Die Ordner im Verzeichnis &quot;hoks&quot;enthalten &quot;node.js&quot;-Skripten, die an exakten Punkten während der Erstellung ausgeführt werden.

#### .cordova/hooks/after-platform_add/ {#cordova-hooks-after-platform-add}

Der Ordner after-platform_add enthält die Datei `copy_AMS_Conifg.js`. Dieses Skript kopiert eine Konfigurationsdatei, um die Adobe Mobile Services-Analyse zu unterstützen.

#### .cordova/hooks/after-prepare/ {#cordova-hooks-after-prepare}

Der Ordner after-prepare enthält die Datei `copy_resource_files.js`. Dieses Skript kopiert eine Reihe von Symbol- und Startbildschirmbildern an plattformspezifische Positionen.

#### .cordova/hooks/before_platform_add/ {#cordova-hooks-before-platform-add}

Der Ordner before_platform_add enthält die Datei `install_plugins.js`. Dieses Skript durchläuft eine Liste von Cordova Plug-in-IDs, wobei diejenigen installiert werden, die es erkennt, dass sie nicht bereits verfügbar sind.

Für diese Strategie ist es nicht erforderlich, dass Sie die Plugins bündeln und installieren, um sie bei jeder Ausführung des Befehls Maven `content-package:install` zu AEM. Die alternative Methode zum Prüfen der Dateien in Ihrem SCM-System erfordert die wiederholte Bündelung und Installation von Aktivitäten.

#### .cordova/hooks/other hoks {#cordova-hooks-other-hooks}

Schließen Sie bei Bedarf andere Haken ein. Die folgenden Haken sind verfügbar (wie von der Phonegap-Musteranwendung hello world bereitgestellt):

* after_build
* before_build
* after_compile
* before_compile
* after_docs
* before_docs
* after_emulate
* before_emulate
* after_platform_add
* before_platform_add
* after_platform_ls
* before_platform_ls
* after_platform_rm
* before_platform_rm
* after_plugin_add
* before_plugin_add
* after_plugin_ls
* before_plugin_ls
* after_plugin_rm
* before_plugin_rm
* after_prepare
* before_prepare
* after_run
* before_run

#### platforms/ {#platforms}

Dieser Ordner ist leer, bis Sie den Befehl `phonegap run <platform>` für das Projekt ausführen. Derzeit kann `<platform>` entweder `ios` oder `android` sein.

Nachdem Sie die App für eine bestimmte Plattform erstellt haben, wird der entsprechende Ordner erstellt und enthält den plattformspezifischen App-Code.

#### plugins/ {#plugins}

Der Ordner &quot;plugins&quot;wird von jedem Plugin gefüllt, das in der Datei `.cordova/hooks/before_platform_add/install_plugins.js` aufgeführt ist, nachdem Sie den Befehl `phonegap run <platform>` ausgeführt haben. Der Ordner ist zunächst leer.

#### www/ {#www}

Der Ordner www enthält alle Webinhalte (HTML-, JS- und CSS-Dateien), die das Erscheinungsbild und Verhalten der App implementieren. Mit Ausnahme der unten beschriebenen Ausnahmen stammt dieser Inhalt aus AEM und wird über die Inhaltssynchronisierung in sein statisches Formular exportiert.

#### www/config.xml {#www-config-xml}

Die [PhoneGap-Dokumentation](https://docs.phonegap.com) verweist auf diese Datei als &#39;globale Konfigurationsdatei&#39;. Die Datei &quot;config.xml&quot;enthält viele App-Eigenschaften, wie den Namen der App, die App-Voreinstellungen (z. B. ob eine iOS-Webansicht einen Überlauf zulässt) und Plugin-Abhängigkeiten, die *nur* vom PhoneGap-Build genutzt werden.

Die Datei &quot;config.xml&quot;ist eine statische Datei in AEM und wird wie bisher über die Inhaltssynchronisierung exportiert.

#### www/index.html {#www-index-html}

Die Datei &quot;index.html&quot;leitet zur Startseite der App um.

Die Datei &quot;config.xml&quot;enthält das Element `content`:

`<content src="content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en.html" />`

In [der PhoneGap-Dokumentation](https://docs.phonegap.com) wird dieses Element als &quot;Das optionale &lt;content>-Element definiert die Startseite der App im Web-Asset-Ordner der obersten Ebene. Der Standardwert ist &quot;index.html&quot;, der normalerweise im obersten www-Ordner eines Projekts angezeigt wird.&quot;

Der PhoneGap-Build schlägt fehl, wenn keine Datei &quot;index.html&quot;vorhanden ist. Daher ist diese Datei enthalten.

#### www/res {#www-res}

Der Ordner res enthält Startbildschirmbilder und Symbole. Das Skript `copy_resource_files.js` kopiert die Dateien während der Erstellungsphase an ihre plattformspezifischen Speicherorte.`after_prepare`

#### www/etc {#www-etc}

Standardmäßig enthält der Knoten /etc AEM statischen clientlib-Inhalt. Der Ordner &quot;etc&quot;enthält die Bibliotheken &quot;Topcoat&quot;, &quot;AngularJS&quot;und &quot;Geometrixx ng-clientlibsall&quot;.

#### www/apps {#www-apps}

Der Apps-Ordner enthält Code, der sich auf die Begrüßungsseite bezieht. Das einzigartige Merkmal der Begrüßungsseite einer AEM App ist, dass die App ohne Benutzerinteraktion initialisiert wird. Der clientlib-Inhalt (sowohl CSS als auch JS) der App ist daher minimal, um die Leistung zu maximieren.

#### www/content {#www-content}

Der Inhaltsordner enthält den Rest des Webinhalts der App. Der Inhalt kann die folgenden Dateien umfassen, ist jedoch nicht darauf beschränkt:

* HTML-Seiteninhalt, der direkt in AEM erstellt wird
* Mit AEM Komponenten verknüpfte Bildelemente
* JavaScript-Inhalte, die serverseitige Skripten generieren
* JSON-Dateien, die den Seiten- oder Komponenteninhalt beschreiben

#### www/package.json {#www-package-json}

Die Datei &quot;package.json&quot;ist eine Manifestdatei, mit der die Dateien Liste werden, die ein **vollständiger** Content Sync-Download enthält. Diese Datei enthält auch den Zeitstempel, mit dem die Inhaltssynchronisierungs-Payload generiert wurde ( `lastModified`). Diese Eigenschaft wird beim Anfordern von Teilaktualisierungen der App von AEM verwendet.

#### www/package-update.json {#www-package-update-json}

Wenn es sich bei dieser Nutzlast um einen Download der gesamten App handelt, enthält dieses Manifest die exakte Auflistung der Dateien als `package.json`.

Wenn es sich bei dieser Payload jedoch um eine Teilaktualisierung handelt, enthält `package-update.json` nur die Dateien, die in dieser bestimmten Payload enthalten sind.

### Die nächsten Schritte {#the-next-steps}

Sobald Sie die Anatomie einer App kennen, finden Sie weitere Informationen unter [Einzelseitenanwendungen](/help/mobile/phonegap-single-page-applications.md).
