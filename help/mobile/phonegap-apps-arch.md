---
title: Die Anatomie einer App
description: Diese Seite enthält eine Beschreibung der Seitenkomponenten, die Sie für Ihre App erstellen und die auf der Komponente /libs/mobileapps/components/angular/ng-page (CRXDE Lite auf einem lokalen Server) basieren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: ab4f1c61-be83-420e-a339-02cf1f33efed
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '2584'
ht-degree: 0%

---

# Die Anatomie einer App{#the-anatomy-of-an-app}

{{ue-over-mobile}}

## Seitenvorlagen für Mobile Apps {#page-templates-for-mobile-apps}

Seitenkomponenten, die Sie für Ihre App erstellen, basieren auf der Komponente /libs/mobileapps/components/angular/ng-page ([auf einem lokalen CRXDE Lite-Server ](http://localhost:4502/crx/de/index.jsp#/libs/mobileapps/components/angular/ng-page)). Diese Komponente enthält die folgenden JSP-Skripte, die Ihre Komponente entweder erbt oder überschreibt:

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

Bestimmt mithilfe der `applicationName`-Eigenschaft den Namen der Anwendung und stellt ihn über pageContext zur Verfügung.

Enthält head.jsp und body.jsp.

### head.jsp {#head-jsp}

Schreibt das `<head>` der App-Seite aus.

Wenn Sie die Viewport-Meta-Eigenschaft der App überschreiben möchten, ist dies die Datei, die Sie überschreiben.

Gemäß den Best Practices enthält die App den CSS-Teil der Client-Bibliotheken im Head, während die JS-Datei im schließenden &lt; `body>`-Element enthalten ist.

### body.jsp {#body-jsp}

Der Hauptteil einer Angular-Seite wird unterschiedlich gerendert, je nachdem, ob wcmMode erkannt wird (!= WCMode.DISABLED), um zu bestimmen, ob die Seite für das Authoring oder als veröffentlichte Seite geöffnet wird.

**Autorenmodus**

Im Autorenmodus wird jede einzelne Seite separat gerendert. Angular übernimmt weder das Routing zwischen Seiten, noch wird eine NG-Ansicht zum Laden einer partiellen Vorlage verwendet, die die Seitenkomponenten enthält. Stattdessen wird der Inhalt der Seitenvorlage (template.jsp) Server-seitig über das `cq:include`-Tag eingebunden.

Diese Strategie ermöglicht es den Autorenfunktionen (z. B. Hinzufügen und Bearbeiten von Komponenten im Absatzsystem, Sidekick, Designmodus usw.), ohne Änderungen zu funktionieren. Seiten, die auf Client-seitiges Rendering angewiesen sind, z. B. solche für Apps, funktionieren im AEM-Autorenmodus nicht gut.

Der include template.jsp ist in ein `div`-Element eingeschlossen, das die `ng-controller`-Anweisung enthält. Diese Struktur ermöglicht die Verknüpfung der DOM-Inhalte mit dem Controller. Daher schlagen Seiten, die sich selbst auf der Client-Seite rendern, zwar fehl, einzelne Komponenten, die dies tun, funktionieren jedoch einwandfrei (siehe den Abschnitt zu Komponenten unten).

```xml
<div ng-controller="<c:out value="${controllerNameStripped}"/>">
      <cq:include script="template.jsp"/>
</div>
```

**Publish-Modus**

Im Veröffentlichungsmodus (z. B. wenn die App mithilfe der Inhaltssynchronisierung exportiert wird) werden alle Seiten zu einer Einzelseiten-App (SPA). (Weitere Informationen zu SPA finden Sie im Angular-Tutorial, insbesondere unter [https://docs.angularjs.org/tutorial/step_07](https://docs.angularjs.org/tutorial/step_07).)

Eine SPA enthält nur eine HTML-Seite (eine Seite, die das `<html>` enthält). Diese Seite wird als „Layout-Vorlage“ bezeichnet. In der Angular-Terminologie ist dies &quot;…eine Vorlage, die für alle Ansichten in unserer Anwendung gleich ist“. Diese Seite als „App-Seite der obersten Ebene“ betrachten. Standardmäßig ist die App-Seite der obersten Ebene der `cq:Page` Knoten Ihres Programms, der dem Stamm am nächsten ist (und keine Umleitung darstellt).

Da sich der tatsächliche URI Ihrer App im Veröffentlichungsmodus nicht ändert, müssen Verweise auf externe Assets von dieser Seite relative Pfade verwenden. Daher wird eine spezielle Bildkomponente bereitgestellt, die diese Seite der obersten Ebene beim Rendern von Bildern für den Export berücksichtigt.

Als SPA generiert diese Layoutvorlagenseite einfach ein div-Element mit einer ng-view-Direktive.

```xml
 <div ng-view ng-class="transition"></div>
```

Der Angular-Routendienst verwendet dieses Element, um den Inhalt aller Seiten in der App anzuzeigen, einschließlich des bearbeitbaren Inhalts der aktuellen Seite (in template.jsp).

Die Datei body.jsp enthält die Dateien header.jsp und footer.jsp, die leer sind. Wenn Sie statischen Inhalt auf jeder Seite bereitstellen möchten, können Sie diese Skripte in Ihrer App überschreiben.

Schließlich sind JavaScript-Client-Bibliotheken am unteren Rand des Elements &lt;body> enthalten, einschließlich zweier spezieller JS-Dateien, die auf dem Server generiert werden: *&lt;page name>*.angular-app-module.js und *&lt;page name>*.angular-app-controllers.js.

### angular-app-module.js.jsp {#angular-app-module-js-jsp}

Dieses Script definiert das Angular-Modul der Anwendung. Die Ausgabe dieses Skripts ist mit dem Markup verknüpft, das der Rest der Vorlagenkomponente über das `html`-Element in ng-page.jsp generiert, das das folgende Attribut enthält:

```xml
ng-app="<c:out value='${applicationName}'/>"
```

Dieses Attribut gibt Angular an, dass der Inhalt dieses DOM-Elements mit dem folgenden Modul verknüpft werden soll. Dieses Modul verknüpft die Ansichten (in AEM wären dies cq:Page-Ressourcen) mit den entsprechenden Controllern.

Dieses Modul definiert auch einen Controller der obersten Ebene mit dem Namen `AppController`, der die `wcmMode` für den Bereich bereitstellt, und konfiguriert den URI, von dem die Payloads für die Inhaltssynchronisierung-Aktualisierung abgerufen werden sollen.

Schließlich durchläuft dieses Modul jede untergeordnete Seite (einschließlich sich selbst) und rendert den Inhalt des Routenfragments jeder Seite (über den Selektor und die Erweiterung &quot;angular-route-fragment.js„), einschließlich als Konfigurationseintrag für Angular $routeProvider. Mit anderen Worten: Der $routeProvider teilt der App mit, welcher Inhalt gerendert werden soll, wenn ein bestimmter Pfad angefordert wird.

### angular-route-fragment.js.jsp {#angular-route-fragment-js-jsp}

Dieses Skript generiert ein JavaScript-Fragment, das die folgende Form aufweisen muss:

```
.when('/<path>', {
    templateUrl: '<path to template>',
    controller: '<controller name>'
})
```

Dieser Code gibt $routeProvider (definiert in angular-app-module.js.jsp) an, dass &#39;/&lt;path>&#39; von der Ressource unter `templateUrl` verarbeitet und durch `controller` verkabelt werden soll (worauf wir als Nächstes kommen).

Bei Bedarf können Sie dieses Skript überschreiben, um komplexere Pfade zu verarbeiten, einschließlich solcher mit Variablen. Ein Beispiel dafür finden Sie im Skript /apps/geometrixx-outdoors-app/components/angular/ng-template-page/angular-route-fragment.js.jsp, das mit AEM installiert wird:

```xml
// note the :id suffix on the path
.when('<c:out value="${resource.path}"/>/:id', {
    templateUrl: '<c:out value="${relativeResourcePath}"/>.template.html',
    controller: '<c:out value="${controllerNameStripped}"/>'
})
```

### angular-app-controllers.js.jsp {#angular-app-controllers-js-jsp}

Beim Angular vernetzen Controller Variablen im $scope und stellen sie der Ansicht zur Verfügung. Das Skript angular-app-controllers.js.jsp folgt dem von angular-app-module.js.jsp dargestellten Muster, indem es jede untergeordnete Seite (einschließlich sich selbst) durchläuft und das von jeder Seite definierte Controller-Fragment ausgibt (über controller.js.jsp). Das von ihm definierte Modul heißt `cqAppControllers` und muss als Abhängigkeit vom App-Modul der obersten Ebene aufgelistet werden, damit die Seiten-Controller verfügbar gemacht werden.

### controller.js.jsp {#controller-js-jsp}

Das Skript controller.js.jsp generiert das Controller-Fragment für jede Seite. Dieses Controller-Fragment hat die folgende Form:

```
.controller('<c:out value="${controllerNameStripped}"/>', ['$scope', '$http',
    function($scope, $http) {
        var data = $http.get('<c:out value="${relativeResourcePath}"/>.angular.json' + cacheKiller);

        // component fragments which consume the contents of `data` go here
    }
])
```

Der `data`-Variable wird die von der Angular-`$http.get` zurückgegebene Zusage zugewiesen. Jede auf dieser Seite enthaltene Komponente kann bei Bedarf JSON-Inhalte verfügbar machen (über das Skript angular.json.jsp ) und die Inhalte dieser Anfrage bearbeiten, wenn sie aufgelöst wird. Die Anfrage ist auf Mobilgeräten sehr schnell, da sie einfach auf das Dateisystem zugreift.

Damit eine Komponente auf diese Weise Teil des Controllers ist, sollte sie die Komponente /libs/mobileapps/components/angular/ng-component erweitern und die Eigenschaft `frameworkType: angular` einschließen.

### template.jsp {#template-jsp}

Die Datei „template.jsp“, die zuerst im Abschnitt body.jsp eingeführt wurde, enthält einfach das ParSys der Seite. Im Veröffentlichungsmodus wird dieser Inhalt direkt referenziert (unter &lt;page-path>.template.html) und über die im $routeProvider konfigurierte templateUrl in die SPA geladen.

Das parsys in diesem Skript kann so konfiguriert werden, dass es jeden Komponententyp akzeptiert. Bei Komponenten, die für eine herkömmliche Website (im Gegensatz zu SPA) erstellt wurden, muss jedoch Vorsicht geboten sein. Beispielsweise funktioniert die Foundation-Bildkomponente nur auf der App-Seite der obersten Ebene ordnungsgemäß, da sie nicht für Verweise auf Assets konzipiert ist, die sich in einer App befinden.

### angular-module-list.js.jsp {#angular-module-list-js-jsp}

Dieses Script gibt einfach die Angular-Abhängigkeiten des Angular-App-Moduls der obersten Ebene aus. Es wird von angular-app-module.js.jsp referenziert.

### header.jsp {#header-jsp}

Ein Skript, um statische Inhalte am Anfang der App zu platzieren. Dieser Inhalt wird von der Seite der obersten Ebene außerhalb des Bereichs von ng-view eingeschlossen.

### footer.jsp {#footer-jsp}

Ein Skript zum Platzieren von statischen Inhalten am unteren Rand der App. Dieser Inhalt wird von der Seite der obersten Ebene außerhalb des Bereichs von ng-view eingeschlossen.

### js_clientlibs.jsp {#js-clientlibs-jsp}

Überschreiben Sie dieses Skript, um Ihre JavaScript-Client-Bibliotheken einzuschließen.

### css_clientlibs.jsp {#css-clientlibs-jsp}

Überschreiben Sie dieses Skript, um Ihre CSS-Client-Bibliotheken einzuschließen.

## Mobile-App-Komponenten {#app-components}

Mobile-App-Komponenten müssen nicht nur in einer AEM-Instanz (Veröffentlichungs- oder Autoreninstanz) funktionieren, sondern auch, wenn der Programminhalt über die Inhaltssynchronisierung in das Dateisystem exportiert wird. Die Komponente muss daher die folgenden Merkmale aufweisen:

* Alle Assets, Vorlagen und Skripte in einer PhoneGap-Anwendung müssen relativ referenziert werden.
* Die Handhabung von Links unterscheidet sich, wenn die AEM-Instanz im Autoren- oder Veröffentlichungsmodus ausgeführt wird.

### Relative Assets {#relative-assets}

Der URI eines bestimmten Assets in einer PhoneGap-Anwendung unterscheidet sich nicht nur pro Plattform, sondern ist in jeder Installation der App eindeutig. Beachten Sie beispielsweise den folgenden URI einer App, die im iOS-Simulator ausgeführt wird:

`file:///Users/userId/Library/Application%20Support/iPhone%20Simulator/7.0.3/Applications/24BA22ED-7D06-4330-B7EB-F6FC73251CA3/Library/files/www/content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en/home.html`

Beachten Sie die GUID „24BA22ED-7D06-4330-B7EB-F6FC73251CA3“ im Pfad.

Als PhoneGap-Entwickler befinden sich die Inhalte, um die Sie sich kümmern, unter dem Verzeichnis www . Verwenden Sie relative Pfade, um auf die App-Assets zuzugreifen.

Um das Problem zu verschlimmern, verwendet Ihre PhoneGap-Anwendung das SPA-Muster (Single Page App), sodass der Basis-URI (ohne den Hash) sich nie ändert. Daher müssen alle Assets, Vorlagen oder Skripte, auf die Sie verweisen **&#x200B; relativ zu Ihrer Top-Level-Seite sein. &#x200B;** Die Seite der obersten Ebene initialisiert das Angular-Routing und die Controller aufgrund von `*<name>*.angular-app-module.js` und `*<name>*.angular-app-controllers.js`. Diese Seite sollte die Seite sein, die dem Stamm des Repositorys am nächsten ist und *keine* Sling:Redirect-Erweiterung ermöglicht.

Für die Behandlung relativer Pfade stehen verschiedene Hilfsmethoden zur Verfügung:

* FrameworkContentExporterUtils.getTopLevelAppResource
* FrameworkContentExporterUtils.getRelativePathToRootLevel
* FrameworkContentExporterUtils.getPathToAsset

Um Beispiele für ihre Verwendung zu sehen, öffnen Sie die Mobile-Apps-Quelle unter /libs/mobileapps/components/angular.

### Links {#links}

Links müssen die `ng-click="go('/path')"`-Funktion verwenden, um alle WCM-Modi zu unterstützen. Diese Funktion hängt vom Wert einer Scope-Variablen ab, um die Link-Aktion korrekt zu bestimmen:

```xml
<c:choose><c:when test="${wcmMode}">
    <%-- WCMMode is enabled - page is being rendered in AEM --%>
    $scope.wcmMode = true;
</c:when><c:otherwise>
    <%-- WCMMode is disabled --%>
    $scope.wcmMode = false;
</c:otherwise></c:choose>
```

Bei der `$scope.wcmMode == true` behandeln wir jedes Navigationsereignis auf die übliche Weise, sodass sich der Pfad und/oder der Seitenteil der URL ändern.

Alternativ führt jedes Navigationsereignis, falls `$scope.wcmMode == false`, zu einer Änderung des Hash-Teils der URL, die intern vom Angular nRoute-Modul aufgelöst wird.

### Details zum Komponentenskript {#component-script-details}

![chlimage_1-144](assets/chlimage_1-144.png)

#### ng-component.jsp {#ng-component-jsp}

Dieses Skript zeigt entweder den Komponenteninhalt oder einen geeigneten Platzhalter an, wenn der Bearbeitungsmodus erkannt wird.

#### template.jsp {#template-jsp-1}

Das Skript „template.jsp“ rendert das Markup der Komponente. Wenn die betreffende Komponente durch JSON-Daten gesteuert wird, die aus AEM extrahiert wurden (z. B. „ng-text“: /libs/mobileapps/components/angular/ng-text/template.jsp), ist dieses Skript für die Verkabelung des Markups mit Daten verantwortlich, die vom Controller-Umfang der Seite verfügbar gemacht werden.

Allerdings schreiben die Leistungsanforderungen manchmal vor, dass keine Client-seitigen Vorlagen (auch als Datenbindung bezeichnet) ausgeführt werden. In diesem Fall rendern Sie einfach das Markup der Komponente auf der Server-Seite und sie wird in den Inhalt der Seitenvorlage aufgenommen.

#### overhead.jsp {#overhead-jsp}

In Komponenten, die von JSON-Daten gesteuert werden (z. B. „ng-text“: /libs/mobileapps/components/angular/ng-text), kann „overhead.jsp“ verwendet werden, um den gesamten Java-Code aus „template.jsp“ zu entfernen. Es wird dann von „template.jsp“ referenziert, und alle Variablen, die es in der Anfrage bereitstellt, sind zur Verwendung verfügbar. Diese Strategie fördert die Trennung der Logik von der Präsentation und begrenzt den Code, der kopiert und eingefügt werden muss, wenn eine neue Komponente von einer vorhandenen abgeleitet wird.

#### controller.js.jsp {#controller-js-jsp-1}

Wie unter AEM-Seitenvorlagen beschrieben, kann jede Komponente ein JavaScript-Fragment ausgeben, um den JSON-Inhalt zu nutzen, der von der `data` bereitgestellt wird. Nach den Angular-Konventionen sollte ein Controller nur zum Zuweisen von Variablen zum Bereich verwendet werden.

#### angular.json.jsp {#angular-json-jsp}

Dieses Skript wird als Fragment in die seitenweite Datei &quot;&lt;page-name>.angular.json“ eingefügt, die für jede Seite exportiert wird, die ng-page erweitert. In dieser Datei kann der Komponentenentwickler jede JSON-Struktur verfügbar machen, die für die Komponente erforderlich ist. Im „ng-text“-Beispiel enthält diese Struktur einfach den Textinhalt der Komponente und ein Flag, das angibt, ob die Komponente Rich-Text enthält oder nicht.

Die Produktkomponente &quot;Geometrixx Outdoors-App“ ist ein komplexeres Beispiel (/apps/geometrixx-outdoors-app/components/angular/ng-product):

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

## Inhalt der CLI Assets Download {#contents-of-the-cli-assets-download}

Laden Sie CLI-Assets von der Apps-Konsole herunter, um sie für eine bestimmte Plattform zu optimieren, und erstellen Sie dann die App mithilfe der PhoneGap Command Line Integration (CLI)-API. Der Inhalt der ZIP-Datei, die Sie im lokalen Dateisystem speichern, weist die folgende Struktur auf:

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

Dies ist ein ausgeblendeter Ordner, der je nach den aktuellen Betriebssystemeinstellungen möglicherweise nicht angezeigt wird. Sie sollten Ihr Betriebssystem so konfigurieren, dass dieses Verzeichnis sichtbar ist, wenn Sie die darin enthaltenen App-Hooks ändern möchten.

#### .cordova/hooks/ {#cordova-hooks}

Dieses Verzeichnis enthält die [CLI-Hooks](https://cordova.apache.org/docs/en/10.x/guide/appdev/hooks/). Die Ordner im Verzeichnis hooks enthalten Node.js-Skripte, die während des Builds an genau diesem Punkt ausgeführt werden.

#### .cordova/hooks/after-platform_add/ {#cordova-hooks-after-platform-add}

Der Ordner „after-platform_add“ enthält die `copy_AMS_Conifg.js`. Dieses Skript kopiert eine Konfigurationsdatei, um die Erfassung von Adobe Mobile Services Analytics zu unterstützen.

#### .cordova/hooks/after-preparation/ {#cordova-hooks-after-prepare}

Das Verzeichnis nach der Vorbereitung enthält die `copy_resource_files.js`. Dieses Skript kopiert mehrere Symbol- und Splash-Screen-Bilder in plattformspezifische Speicherorte.

#### .cordova/hooks/before_platform_add/ {#cordova-hooks-before-platform-add}

Der Ordner before_platform_add enthält die `install_plugins.js`. Dieses Skript durchläuft eine Liste von Cordova-Plug-in-Bezeichnern und installiert diejenigen, die es erkennt, sind noch nicht verfügbar.

Bei dieser Strategie müssen Sie die Plug-ins nicht jedes Mal in AEM bündeln und installieren, wenn der Maven-`content-package:install` ausgeführt wird. Die alternative Strategie, die Dateien in Ihr SCM-System einzuchecken, erfordert wiederholte Bündelungs- und Installationsaktivitäten.

#### .cordova/hooks/other hooks {#cordova-hooks-other-hooks}

Schließen Sie ggf. weitere Hooks ein. Die folgenden Hooks sind verfügbar (wie von der PhoneGap-Beispiel-Hello-World-App bereitgestellt):

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
* after_preparation
* before_preparation
* after_run
* before_run

#### Plattformen/ {#platforms}

Dieses Verzeichnis ist leer, bis Sie den `phonegap run <platform>`-Befehl für das Projekt ausführen. Derzeit kann `<platform>` entweder `ios` oder `android` sein.

Nachdem Sie die App für eine bestimmte Plattform erstellt haben, wird das entsprechende Verzeichnis erstellt, das den plattformspezifischen App-Code enthält.

#### plugins/ {#plugins}

Das Plug-in-Verzeichnis wird von jedem Plug-in gefüllt, das in der `.cordova/hooks/before_platform_add/install_plugins.js`-Datei aufgeführt ist, nachdem Sie den `phonegap run <platform>` Befehl ausgeführt haben. Das Verzeichnis ist zunächst leer.

#### www/ {#www}

Das www-Verzeichnis enthält alle Web-Inhalte (HTML-, JS- und CSS-Dateien), die das Erscheinungsbild und Verhalten der App implementieren. Mit Ausnahme der unten beschriebenen Ausnahmen stammt dieser Inhalt von AEM und wird über die Inhaltssynchronisierung in seine statische Form exportiert.

#### www/config.xml {#www-config-xml}

In der PhoneGap-Dokumentation (`https://docs.phonegap.com`) wird diese Datei als „globale Konfigurationsdatei“ bezeichnet. Die Datei config.xml enthält viele App-Eigenschaften, z. B. den Namen der App, die „Voreinstellungen“ der App (z. B. ob eine iOS-Webansicht einen Überlauf zulässt) und Plug-in-Abhängigkeiten, die *nur* vom PhoneGap-Build genutzt werden.

Die Datei config.xml ist eine statische Datei in AEM und wird wie besehen über die Inhaltssynchronisierung exportiert.

#### www/index.html {#www-index-html}

Die Datei „index.html“ wird zur Startseite der App weitergeleitet.

Die Datei config.xml enthält das `content`:

`<content src="content/phonegap/geometrixx/apps/ng-geometrixx-outdoors/en.html" />`

In der PhoneGap-Dokumentation (`https://docs.phonegap.com`) wird dieses Element als „Das optionale &lt;content>-Element definiert die Startseite der App im Web-Asset-Verzeichnis der obersten Ebene. Der Standardwert ist index.html, die normalerweise im obersten www-Verzeichnis eines Projekts angezeigt wird.“

Der PhoneGap-Build schlägt fehl, wenn keine index.html-Datei vorhanden ist. Daher ist diese Datei enthalten.

#### www/res {#www-res}

Das Verzeichnis res enthält Startbildschirmbilder und Symbole. Das `copy_resource_files.js`-Skript kopiert die Dateien während der `after_prepare`-Build-Phase an ihre plattformspezifischen Speicherorte.

#### www/etc {#www-etc}

Standardmäßig enthält der Knoten &quot;/etc“ in AEM statische Clientlib-Inhalte. Das etc-Verzeichnis enthält die Topcoat-, AngularJS- und Geometrixx ng-clientlibsall-Bibliotheken.

#### www/apps {#www-apps}

Das Anwendungsverzeichnis enthält Code, der mit der Splash-Seite in Verbindung steht. Die einzigartige Eigenschaft der Splash-Seite einer AEM-App besteht darin, dass sie die App ohne Benutzerinteraktion initialisiert. Der Client-Bibliotheksinhalt (CSS und JS) der App ist daher minimal, um die Leistung zu maximieren.

#### www/content {#www-content}

Das Inhaltsverzeichnis enthält den Rest des Web-Inhalts der App. Der Inhalt kann die folgenden Dateien enthalten, ist aber nicht darauf beschränkt:

* HTML von Seiteninhalten, die direkt in AEM verfasst werden
* Bild-Assets, die AEM-Komponenten zugeordnet sind
* JavaScript-Inhalte, die von serverseitigen Skripten generiert werden
* JSON-Dateien, die Seiten- oder Komponenteninhalte beschreiben

#### www/package.json {#www-package-json}

Die Datei package.json ist eine Manifestdatei, die die Dateien auflistet, die ein Download **vollständigen** Inhaltssynchronisierung enthält. Diese Datei enthält auch den Zeitstempel, mit dem die Inhaltssynchronisierungs-Payload generiert wurde ( `lastModified`). Diese Eigenschaft wird verwendet, wenn Teilaktualisierungen der App von AEM angefordert werden.

#### www/package-update.json {#www-package-update-json}

Wenn es sich bei dieser Payload um einen Download der gesamten App handelt, enthält dieses Manifest die genaue Auflistung der Dateien als `package.json`.

Wenn es sich bei dieser Payload jedoch um eine partielle Aktualisierung handelt, enthält `package-update.json` nur die Dateien, die in dieser bestimmten Payload enthalten sind.

### Die nächsten Schritte {#the-next-steps}

Wenn Sie sich mit der Anatomie einer App vertraut gemacht haben, lesen Sie [Single Page Applications](/help/mobile/phonegap-single-page-applications.md).
