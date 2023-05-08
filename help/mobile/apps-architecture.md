---
title: Seitenvorlagen für mobile Apps
description: Auf dieser Seite erfahren Sie mehr über Seitenvorlagen. Seitenkomponenten, die Sie für Ihre App erstellen, basieren auf der Komponente /libs/mobileapps/components/angular/ng-page .
uuid: c53901c9-5974-4c6b-ac61-1c094a93c9d6
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: cfc7ad16-965e-4075-bc4d-5630abeaba55
exl-id: 397def36-45b2-47a7-b103-99ca22b6dae1
source-git-commit: 85d39e59b82fdfdcd310be61787a315668aebe38
workflow-type: tm+mt
source-wordcount: '2671'
ht-degree: 0%

---

# Seitenvorlagen für mobile Apps {#page-templates-for-mobile-apps}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

## Seitenvorlagen für mobile Apps {#page-templates-for-mobile-apps-1}

Seitenkomponenten, die Sie für Ihre App erstellen, basieren auf der Komponente /libs/mobileapps/components/angular/ng-page ([in CRXDE Lite auf einem lokalen Server öffnen](http://localhost:4502/crx/de/index.jsp#/libs/mobileapps/components/angular/ng-page)). Diese Komponente enthält die folgenden JSP-Skripte, die Ihre Komponente übernimmt oder überschreibt:

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

Bestimmt den Namen der Anwendung mithilfe des `applicationName` -Eigenschaft und stellt sie über pageContext bereit.

Enthält head.jsp und body.jsp.

### head.jsp {#head-jsp}

schreibt die `<head>` -Element der App-Seite.

Wenn Sie die Viewport-Meta-Eigenschaft der App überschreiben möchten, ist dies die Datei, die Sie überschreiben.

Befolgen Sie die Best Practices, indem die App den CSS-Teil der Client-Bibliotheken im Kopf einbezieht, während der JS-Code im schließenden &lt; `body>` -Element.

### body.jsp {#body-jsp}

Der Hauptteil einer Angular-Seite wird je nachdem, ob wcmMode erkannt wird (!= WCMMode.DISABLED), um zu bestimmen, ob die Seite zum Authoring oder als veröffentlichte Seite geöffnet ist.

**Autorenmodus**

Im Autorenmodus wird jede einzelne Seite separat gerendert. Angular behandelt weder das Routing zwischen Seiten noch eine NG-Ansicht zum Laden einer partiellen Vorlage, die die Komponenten der Seite enthält. Stattdessen wird der Inhalt der Seitenvorlage (template.jsp) serverseitig über die `cq:include` -Tag.

Diese Strategie ermöglicht die Autorenfunktionen (z. B. Hinzufügen und Bearbeiten von Komponenten im Absatzsystem, Sidekick, Designmodus usw.) , um ohne Änderung zu funktionieren. Seiten, die auf der clientseitigen Wiedergabe basieren, wie z. B. Seiten für Apps, funktionieren im Autorenmodus nicht gut AEM.

Beachten Sie, dass der Einschluss von template.jsp in einen `div` -Element, das die `ng-controller` Richtlinie. Diese Struktur ermöglicht die Verknüpfung der DOM-Inhalte mit dem Controller. Daher schlagen zwar Seiten fehl, die auf der Client-Seite selbst gerendert werden, doch funktionieren einzelne Komponenten, die dies tun, gut (siehe Abschnitt zu Komponenten unten).

```xml
<div ng-controller="<c:out value="${controllerNameStripped}"/>">
      <cq:include script="template.jsp"/>
</div>
```

**Veröffentlichungsmodus**

Im Veröffentlichungsmodus (z. B. wenn die App mit der Inhaltssynchronisierung exportiert wird) werden alle Seiten zu einer Einzelseiten-App (SPA). (Um mehr über SPA zu erfahren, verwenden Sie das Angular-Tutorial, insbesondere [https://docs.angularjs.org/tutorial/step_07](https://docs.angularjs.org/tutorial/step_07).

Es gibt nur eine HTML-Seite in einem SPA (eine Seite, die die `<html>` -Element). Diese Seite wird als &quot;Layoutvorlage&quot;bezeichnet. In der Angular-Terminologie ist es &quot;..eine Vorlage, die für alle Ansichten in unserer Anwendung verwendet wird.&quot; Betrachten Sie diese Seite als &quot;App-Seite der obersten Ebene&quot;. Die App-Seite der obersten Ebene ist standardmäßig die `cq:Page` -Knoten Ihrer Anwendung, der dem Stammverzeichnis am nächsten ist (und keine Umleitung ist).

Da sich der tatsächliche URI Ihrer App im Veröffentlichungsmodus nicht ändert, müssen Verweise auf externe Assets von dieser Seite relative Pfade verwenden. Daher wird eine spezielle Bildkomponente bereitgestellt, die diese Seite der obersten Ebene beim Rendern von Bildern für den Export berücksichtigt.

Als SPA generiert diese Layoutvorlagenseite einfach ein div -Element mit einer ng-view -Direktive.

```xml
 <div ng-view ng-class="transition"></div>
```

Der Angular Route-Dienst verwendet dieses Element, um den Inhalt jeder Seite in der App anzuzeigen, einschließlich des bearbeitbaren Inhalts der aktuellen Seite (in template.jsp enthalten).

Die Datei body.jsp enthält &quot;header.jsp&quot;und &quot;footer.jsp&quot;, die leer sind. Wenn Sie statischen Inhalt auf jeder Seite bereitstellen möchten, können Sie diese Skripte in Ihrer App überschreiben.

Schließlich sind die JavaScript-Client-Bibliotheken unten im &lt;body> -Element mit zwei speziellen JS-Dateien, die auf dem Server generiert werden: *&lt;page name=&quot;&quot;>*.angular-app-module.js und *&lt;page name=&quot;&quot;>*.angular-app-controller.js.

### angular-app-module.js.jsp {#angular-app-module-js-jsp}

Dieses Skript definiert das Angular-Modul der Anwendung. Die Ausgabe dieses Skripts ist mit dem Markup verknüpft, das der Rest der Vorlagenkomponente über die `html` -Element in ng-page.jsp, das das folgende Attribut enthält:

```xml
ng-app="<c:out value='${applicationName}'/>"
```

Dieses Attribut gibt Angular an, dass der Inhalt dieses DOM-Elements mit dem folgenden Modul verknüpft werden soll. Dieses Modul verknüpft die Ansichten (in AEM wären dies cq:Page -Ressourcen) mit den entsprechenden Controllern.

Dieses Modul definiert auch einen Controller der obersten Ebene mit dem Namen `AppController` , das die `wcmMode` zum Bereich hinzu und konfiguriert den URI, aus dem die Payloads für die Aktualisierung der Inhaltssynchronisierung abgerufen werden sollen.

Schließlich durchläuft dieses Modul jede untergeordnete Seite (einschließlich der eigenen Seite) und rendert den Inhalt des Routenfragments jeder Seite (über den Selektor und die Erweiterung angular-route-fragment.js ), einschließlich des Inhalts als Konfigurationseintrag zu Angular \$routeProvider. Mit anderen Worten: Der \$routeProvider teilt der App mit, welcher Inhalt gerendert werden soll, wenn ein bestimmter Pfad angefordert wird.

### angular-route-fragment.js.jsp {#angular-route-fragment-js-jsp}

Dieses Skript generiert ein JavaScript-Fragment, das folgende Form aufweisen muss:

```
.when('/<path>', {
    templateUrl: '<path to template>',
    controller: '<controller name>'
})
```

Dieser Code gibt $routeProvider (definiert in angular-app-module.js.jsp) an, dass &quot;/&lt;path>&quot; wird von der Ressource unter `templateUrl`und mit `controller` (auf die wir als Nächstes kommen).

Bei Bedarf können Sie dieses Skript überschreiben, um komplexere Pfade zu handhaben, einschließlich Pfaden mit Variablen. Ein Beispiel dafür finden Sie im Skript /apps/geometrixx-outdoors-app/components/angular/ng-template-page/angular-route-fragment.js.jsp , das mit AEM installiert wird:

```xml
// note the :id suffix on the path
.when('<c:out value="${resource.path}"/>/:id', {
    templateUrl: '<c:out value="${relativeResourcePath}"/>.template.html',
    controller: '<c:out value="${controllerNameStripped}"/>'
})
```

### angular-app-controllers.js.jsp {#angular-app-controllers-js-jsp}

In Angular verknüpfen Controller Variablen im \$scope, wodurch sie der Ansicht angezeigt werden. Das Skript angular-app-controllers.js.jsp folgt dem Muster, das von angular-app-module.js.jsp veranschaulicht wird, da es durch jede nachkommende Seite (einschließlich der Seite selbst) iteriert und das Controller-Fragment ausgibt, das jede Seite definiert (über controller.js.jsp). Das Modul, das es definiert, heißt `cqAppControllers` und müssen als Abhängigkeit vom App-Modul der obersten Ebene aufgeführt werden, damit die Seiten-Controller verfügbar gemacht werden.

### controller.js.jsp {#controller-js-jsp}

Das Skript controller.js.jsp generiert das Controller-Fragment für jede Seite. Dieses Controller-Fragment hat folgendes Format:

```
.controller('<c:out value="${controllerNameStripped}"/>', ['$scope', '$http',
    function($scope, $http) {
        var data = $http.get('<c:out value="${relativeResourcePath}"/>.angular.json' + cacheKiller);

        // component fragments which consume the contents of `data` go here
    }
])
```

Beachten Sie Folgendes: `data` wird das von der Angular zurückgegebene Promise zugewiesen. `$http.get` -Methode. Jede auf dieser Seite enthaltene Komponente kann bei Bedarf einen beliebigen .json-Inhalt verfügbar machen (über das angular.json.jsp-Skript) und nach der Auflösung auf den Inhalt dieser Anforderung reagieren. Die Anfrage erfolgt sehr schnell auf Mobilgeräten, da sie einfach auf das Dateisystem zugreift.

Damit eine Komponente auf diese Weise Teil des Controllers sein kann, sollte sie die Komponente /libs/mobileapps/components/angular/ng-component erweitern und die Komponente `frameworkType: angular` -Eigenschaft.

### template.jsp {#template-jsp}

Als Erstes, der in den Abschnitt body.jsp eingeführt wurde, enthält template.jsp einfach die ParSys der Seite. Im Veröffentlichungsmodus wird dieser Inhalt direkt referenziert (unter &lt;page-path>.template.html) und über die im \$routeProvider konfigurierte templateUrl in die SPA geladen wurden.

Die parsys in diesem Skript können so konfiguriert werden, dass sie jeden Komponententyp akzeptieren. Bei Komponenten, die für eine herkömmliche Website erstellt wurden (im Gegensatz zu SPA), ist jedoch Vorsicht geboten. Beispielsweise funktioniert die Foundation-Bildkomponente nur auf der App-Seite der obersten Ebene ordnungsgemäß, da sie nicht für Verweise auf Assets konzipiert ist, die sich in einer App befinden.

### angular-module-list.js.jsp {#angular-module-list-js-jsp}

Dieses Skript gibt einfach die Angular-Abhängigkeiten des Angular-App-Moduls der obersten Ebene aus. Es wird von angular-app-module.js.jsp referenziert.

### header.jsp {#header-jsp}

Ein Skript zum Platzieren von statischen Inhalten am Anfang der App. Dieser Inhalt wird von der obersten Ebene außerhalb des Bereichs der ng-Ansicht einbezogen.

### footer.jsp {#footer-jsp}

Ein Skript zum Platzieren von statischen Inhalten am unteren Rand der App. Dieser Inhalt wird von der obersten Ebene außerhalb des Bereichs der ng-Ansicht einbezogen.

### js_clientlibs.jsp {#js-clientlibs-jsp}

Überschreiben Sie dieses Skript, um Ihre JavaScript-clientlibs einzuschließen.

### css_clientlibs.jsp {#css-clientlibs-jsp}

Überschreiben Sie dieses Skript, um Ihre CSS-Clientlibs einzuschließen.

## App-Komponenten {#app-components}

App-Komponenten dürfen nicht nur auf einer AEM Instanz (Veröffentlichungs- oder Autoreninstanz) funktionieren, sondern auch, wenn der Anwendungsinhalt über die Inhaltssynchronisierung in das Dateisystem exportiert wird. Die Komponente muss daher die folgenden Merkmale aufweisen:

* Alle Assets, Vorlagen und Skripte in einer PhoneGap-Anwendung müssen relativ referenziert werden.
* Die Behandlung von Links unterscheidet sich, wenn die AEM-Instanz im Autoren- oder Veröffentlichungsmodus ausgeführt wird.

### Relative Assets {#relative-assets}

Der URI eines bestimmten Assets in einer PhoneGap-Anwendung unterscheidet sich nicht nur pro Plattform, sondern ist bei jeder Installation des Programms eindeutig. Beachten Sie beispielsweise den folgenden URI einer App, die im iOS Simulator ausgeführt wird:

`file:///Users/userId/Library/Application%20Support/iPhone%20Simulator/7.0.3/Applications/24BA22ED-7D06-4330-B7EB-F6FC73251CA3/Library/files/www/content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en/home.html`

Beachten Sie die GUID &quot;24BA22ED-7D06-4330-B7EB-F6FC73251CA3&quot;im Pfad.

Als PhoneGap-Entwickler befindet sich der Inhalt, mit dem Sie befasst sind, unter dem www-Verzeichnis. Verwenden Sie relative Pfade, um auf die App-Assets zuzugreifen.

Um das Problem zu beheben, verwendet Ihre PhoneGap-Anwendung das Muster der Einzelseiten-App (SPA), sodass sich der Basis-URI (ohne den Hash) nie ändert. Daher werden alle Assets, Vorlagen oder Skripte, auf die Sie verweisen, **muss relativ zu Ihrer Seite der obersten Ebene sein.** Die oberste Seite initialisiert das Angular-Routing und die Controller anhand von `*<name>*.angular-app-module.js` und `*<name>*.angular-app-controllers.js`. Diese Seite sollte die nächstgelegene Seite zum Stammverzeichnis des Repositorys sein, das *keine Erweiterung einer sling:redirect darstellt.

Für den Umgang mit relativen Pfaden stehen verschiedene Hilfsmethoden zur Verfügung:

* FrameworkContentExporterUtils.getTopLevelAppResource
* FrameworkContentExporterUtils.getRelativePathToRootLevel
* FrameworkContentExporterUtils.getPathToAsset

Um Beispiele für ihre Verwendung anzuzeigen, öffnen Sie die Quelle mobileapps unter /libs/mobileapps/components/angular.

### Links {#links}

Die Links müssen `ng-click="go('/path')"` -Funktion, um alle WCM-Modi zu unterstützen. Diese Funktion hängt vom Wert einer Perimeter-Variablen ab, um die Linkaktion korrekt zu bestimmen:

```xml
<c:choose><c:when test="${wcmMode}">
    <%-- WCMMode is enabled - page is being rendered in AEM --%>
    $scope.wcmMode = true;
</c:when><c:otherwise>
    <%-- WCMMode is disabled --%>
    $scope.wcmMode = false;
</c:otherwise></c:choose>
```

Wann `$scope.wcmMode == true` Wir behandeln jedes Navigationsereignis auf die übliche Weise, sodass das Ergebnis eine Änderung des Pfads und/oder Seitenanteils der URL darstellt.

Wenn `$scope.wcmMode == false`festgelegt ist, führt jedes Navigationsereignis zu einer Änderung des Hash-Teils der URL, der intern durch das Angular ngRoute-Modul aufgelöst wird.

### Komponentenskriptdetails {#component-script-details}

![chlimage_1-36](assets/chlimage_1-36.png)

#### ng-component.jsp {#ng-component-jsp}

Dieses Skript zeigt entweder den Komponenteninhalt oder einen geeigneten Platzhalter an, wenn der Bearbeitungsmodus erkannt wird.

#### template.jsp {#template-jsp-1}

Das Skript template.jsp rendert das Markup der Komponente. Wenn die betreffende Komponente von JSON-Daten aus AEM (z. B. &quot;ng-text&quot;) gesteuert wird: /libs/mobileapps/components/angular/ng-text/template.jsp), dann ist dieses Skript für die Verkabelung des Markups mit Daten verantwortlich, die vom Controller-Bereich der Seite verfügbar gemacht werden.

Leistungsanforderungen erfordern jedoch manchmal, dass keine clientseitige Vorlage (auch Datenbindung genannt) durchgeführt wird. In diesem Fall rendern Sie einfach das Markup der Komponente serverseitig und es ist im Inhalt der Seitenvorlage enthalten.

#### overhead.jsp {#overhead-jsp}

In Komponenten, die von JSON-Daten gesteuert werden (z. B. &quot;ng-text&quot;): /libs/mobileapps/components/angular/ng-text), overhead.jsp kann verwendet werden, um den gesamten Java-Code aus template.jsp zu entfernen. Anschließend wird er von template.jsp referenziert und alle Variablen, die er in der Anfrage verfügbar macht, sind zur Verwendung verfügbar. Diese Strategie fördert die Trennung von Logik und Präsentation und schränkt die Menge des Codes ein, der kopiert und eingefügt werden muss, wenn eine neue Komponente von einer vorhandenen abgeleitet wird.

#### controller.js.jsp {#controller-js-jsp-1}

Wie in AEM Seitenvorlagen beschrieben, kann jede Komponente ein JavaScript-Fragment ausgeben, um den JSON-Inhalt zu nutzen, der von der `data` Versprechen. Gemäß Angular-Konventionen sollte ein Controller nur zum Zuweisen von Variablen zum Bereich verwendet werden.

#### angular.json.jsp {#angular-json-jsp}

Dieses Skript ist als Fragment im seitenweiten Teil enthalten.&lt;page-name>.angular.json&#39; Datei, die für jede Seite exportiert wird, die ng-page erweitert. In dieser Datei kann der Komponentenentwickler jede JSON-Struktur bereitstellen, die für die Komponente erforderlich ist. Im Beispiel &quot;ng-text&quot;enthält diese Struktur einfach den Textinhalt der Komponente und eine Markierung, die angibt, ob die Komponente Rich-Text enthält oder nicht.

Die Produktkomponente &quot;Geometrixx Outdoors App&quot;ist ein komplexeres Beispiel (/apps/geometrixx-outdoors-app/components/angular/ng-product):

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

## Inhalt des Herunterladens von CLI Assets {#contents-of-the-cli-assets-download}

Laden Sie CLI-Assets aus der Apps-Konsole herunter, um sie für eine bestimmte Plattform zu optimieren, und erstellen Sie dann die App mithilfe der CLI (PhoneGap Command Line Integration)-API. Der Inhalt der ZIP-Datei, die Sie im lokalen Dateisystem speichern, weist die folgende Struktur auf:

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

Dies ist ein ausgeblendetes Verzeichnis, das je nach den aktuellen Betriebssystemeinstellungen möglicherweise nicht angezeigt wird. Sie sollten Ihr Betriebssystem so konfigurieren, dass dieses Verzeichnis sichtbar ist, wenn Sie die darin enthaltenen App-Hooks ändern möchten.

#### .cordova/hooks/ {#cordova-hooks}

Dieser Ordner enthält die [CLI-Hooks](https://cordova.apache.org/docs/en/10.x/guide/appdev/hooks/). Die Ordner im Hooks-Ordner enthalten node.js-Skripte, die an exakten Stellen während des Builds ausgeführt werden.

#### .cordova/hooks/after-platform_add/ {#cordova-hooks-after-platform-add}

Der Ordner after-platform_add enthält den `copy_AMS_Conifg.js` -Datei. Dieses Skript kopiert eine Konfigurationsdatei, um die Erfassung von Adobe Mobile Services-Analysen zu unterstützen.

#### .cordova/hooks/after-prepare/ {#cordova-hooks-after-prepare}

Das Verzeichnis &quot;after-prepare&quot;enthält die `copy_resource_files.js` -Datei. Dieses Skript kopiert eine Reihe von Symbol- und Begrüßungsbildschirmbildern an plattformspezifische Standorte.

#### .cordova/hooks/before_platform_add/ {#cordova-hooks-before-platform-add}

Der Ordner before_platform_add enthält den `install_plugins.js` -Datei. Dieses Skript durchläuft eine Liste von Cordova-Plug-in-Identifikatoren und installiert diejenigen, die es erkennt, sind noch nicht verfügbar.

Für diese Strategie ist es nicht erforderlich, dass Sie die Plug-ins gebündelt und installieren, damit sie jedes Mal AEM werden, wenn der Maven `content-package:install` ausgeführt wird. Die alternative Methode zur Überprüfung der Dateien in Ihrem SCM-System erfordert eine wiederholte Bündelung und Installation von Aktivitäten.

#### .cordova/hooks/Other Hooks {#cordova-hooks-other-hooks}

Schließen Sie bei Bedarf weitere Hooks ein. Die folgenden Hooks sind verfügbar (wie von der Phonegap-Beispielanwendung hello world App bereitgestellt):

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

Dieser Ordner ist leer, bis Sie die `phonegap run <platform>` -Befehl im Projekt. Zurzeit `<platform>` kann `ios` oder `android`.

Nachdem Sie die App für eine bestimmte Plattform erstellt haben, wird der entsprechende Ordner erstellt und der plattformspezifische App-Code enthält.

#### plugins/ {#plugins}

Das Plug-in-Verzeichnis wird von jedem Plug-in aufgefüllt, das im `.cordova/hooks/before_platform_add/install_plugins.js` Datei, nachdem Sie die `phonegap run <platform>` Befehl. Der Ordner ist zunächst leer.

#### www/ {#www}

Das Verzeichnis www enthält alle Webinhalte (HTML-, JS- und CSS-Dateien), die das Erscheinungsbild und Verhalten der App implementieren. Mit Ausnahme der unten beschriebenen Ausnahmen stammt dieser Inhalt aus AEM und wird über die Inhaltssynchronisierung in das statische Formular exportiert.

#### www/config.xml {#www-config-xml}

Die [PhoneGap-Dokumentation](https://docs.phonegap.com) bezeichnet diese Datei als &quot;globale Konfigurationsdatei&quot;. Die Datei &quot;config.xml&quot;enthält viele App-Eigenschaften, z. B. den Namen der App, die App-Voreinstellungen (z. B. ob eine iOS-Webansicht einen Bildlauf ermöglicht) und Plugin-Abhängigkeiten, die *only* Wird vom PhoneGap-Build verwendet.

Die Datei &quot;config.xml&quot;ist eine statische Datei in AEM und wird unverändert über die Inhaltssynchronisierung exportiert.

#### www/index.html {#www-index-html}

Die Datei index.html leitet zur Startseite der App weiter.

Die Datei &quot;config.xml&quot;enthält die `content` element:

`<content src="content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en.html" />`

In [die PhoneGap-Dokumentation](https://docs.phonegap.com)festgelegt ist, wird dieses Element als &quot;Die optionale &lt;content> -Element definiert die Startseite der App im Verzeichnis der Web-Assets der obersten Ebene. Der Standardwert ist index.html, der normalerweise im obersten www-Verzeichnis eines Projekts angezeigt wird.&quot;

Der PhoneGap-Build schlägt fehl, wenn keine index.html -Datei vorhanden ist. Daher ist diese Datei enthalten.

#### www/res {#www-res}

Das Verzeichnis res enthält Splash-Screen-Bilder und Symbole. Die `copy_resource_files.js` Skript kopiert die Dateien an ihre plattformspezifischen Speicherorte während der `after_prepare` Build-Phase.

#### www/etc {#www-etc}

Standardmäßig enthält AEM Knoten /etc statische clientlib-Inhalte. Das Verzeichnis &quot;etc&quot;enthält die Bibliotheken &quot;Topcoat&quot;, &quot;AngularJS&quot;und &quot;Geometrixx ng-clientlibsall&quot;.

#### www/apps {#www-apps}

Der Apps-Ordner enthält Code, der mit der Splash-Seite in Verbindung steht. Das eindeutige Merkmal der Begrüßungsseite einer AEM App besteht darin, dass die App ohne Benutzerinteraktion initialisiert wird. Der clientlib-Inhalt (sowohl CSS als auch JS) der App ist daher minimal, um die Leistung zu maximieren.

#### www/content {#www-content}

Der Inhaltsordner enthält den restlichen Webinhalt der App. Der Inhalt kann die folgenden Dateien enthalten, ist jedoch nicht darauf beschränkt:

* HTML-Seiteninhalt, der direkt in AEM erstellt wird
* Bild-Assets, die mit AEM Komponenten verknüpft sind
* JavaScript-Inhalte, die von serverseitigen Skripten generiert werden
* JSON-Dateien, die den Seiten- oder Komponenteninhalt beschreiben

#### www/package.json {#www-package-json}

Die Datei &quot;package.json&quot;ist eine Manifestdatei, in der die Dateien aufgelistet werden, die eine **full** Download der Inhaltssynchronisierung umfasst. Diese Datei enthält auch den Zeitstempel, mit dem die Payload der Inhaltssynchronisierung generiert wurde (`lastModified`). Diese Eigenschaft wird verwendet, wenn eine partielle Aktualisierung der App von AEM angefordert wird.

#### www/package-update.json {#www-package-update-json}

Wenn diese Payload ein Download der gesamten App ist, enthält dieses Manifest die genaue Auflistung der Dateien als `package.json`.

Wenn es sich bei dieser Payload jedoch um eine partielle Aktualisierung handelt, `package-update.json` enthält nur die Dateien, die in dieser bestimmten Payload enthalten sind.
