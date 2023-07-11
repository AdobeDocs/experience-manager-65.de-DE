---
title: Single Page Applications (SPA)
description: Auf dieser Seite erfahren Sie mehr über Einzelseitenanwendungen, d. h. Sie können eine Anwendung erstellen, die genauso wie eine Desktop- oder mobile Anwendung funktioniert.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: daf7bf39-a105-46eb-ab7b-1c59484949e2
source-git-commit: 1ef5593495b4bf22d2635492a360168bccc1725d
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 1%

---

# Single Page Applications (SPA){#single-page-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, die ein Framework-basiertes clientseitiges Rendering von Einzelseiten-Apps erfordern (z. B. React). [Weitere Informationen](/help/sites-developing/spa-overview.md)

[Einzelseiten-Apps](https://en.wikipedia.org/wiki/Single-page_application) (SPA) eine kritische Masse erreicht haben, die weithin als das effektivste Muster für die Erstellung nahtloser Erlebnisse mit Webtechnologie angesehen wird. Durch Befolgen eines SPA können Sie eine Anwendung erstellen, die eine identische Leistung wie eine Desktop- oder mobile Anwendung erbringt, aber aufgrund ihrer Grundlage in offenen Webstandards eine Vielzahl von Geräteplattformen und Formfaktoren erreicht.

Im Allgemeinen SPA leistungsfähiger als herkömmliche seitenbasierte Websites, da sie normalerweise eine vollständige HTML-Seite laden **nur einmal** (einschließlich CSS, JS und unterstützenden Schriftartinhalt) und dann nur genau das laden, was bei jeder Statusänderung in der App erforderlich ist. Was für diese Statusänderung erforderlich ist, kann je nach gewählter Technologie variieren, enthält jedoch in der Regel ein einzelnes HTML-Fragment, um die vorhandene &quot;Ansicht&quot;zu ersetzen, und die Ausführung eines JS-Codeblocks, um die neue Ansicht abzuschließen und gegebenenfalls eine clientseitige Vorlagendarstellung durchzuführen. Die Geschwindigkeit dieser Statusänderung kann durch die Unterstützung von Vorlagen-Caching-Mechanismen oder sogar durch den Offline-Zugriff auf Vorlageninhalte bei Verwendung von Adobe PhoneGap noch weiter verbessert werden.

AEM 6.1 unterstützt die Erstellung und Verwaltung von SPA über AEM Apps. Dieser Artikel bietet eine Einführung in die Konzepte hinter dem SPA und deren Verwendung [AngularJS](https://angularjs.org/) , um Ihre Marke in die App Store und Google Play zu bringen.

## SPA in AEM Apps {#spa-in-aem-apps}

Das Single Page Application Framework in AEM Apps ermöglicht die hohe Leistung einer AngularJS-App und ermöglicht es Autoren (oder anderen nicht-technischen Mitarbeitern), den Inhalt der App über die Touch-optimierte Drag &amp; Drop-Editorumgebung zu erstellen und zu verwalten, die traditionell für die Verwaltung von Websites reserviert ist. Sie haben bereits eine Website mit AEM erstellt? Die Wiederverwendung von Inhalten, Komponenten, Workflows, Assets und Berechtigungen ist in AEM Apps einfach.

## AngularJS-Anwendungsmodul {#angularjs-application-module}

AEM Apps verarbeitet einen Großteil der AngularJS-Konfiguration für Sie, einschließlich des Zusammenbaus des obersten Moduls Ihrer App. Standardmäßig trägt dieses Modul den Namen &quot;AEMAngularApp&quot;und das für seine Erstellung verantwortliche Skript befindet sich unter /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp.

Teil der Initialisierung Ihrer App ist die Angabe der AngularJS-Module, von denen die App abhängig ist. Die Liste der von Ihrer App verwendeten Module wird von einem Skript unter /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp angegeben und kann von der Seitenkomponente Ihrer eigenen Apps überlagert werden, um alle zusätzlichen AngularJS-Module abzurufen, die für Ihre App erforderlich sind. Vergleichen Sie beispielsweise das obige Skript mit der Geometrixx-Implementierung (unter /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp).

Um die Navigation zwischen den verschiedenen Status in Ihrer App zu unterstützen, durchläuft das Skript angular-app-module alle nachfolgenden Seiten Ihrer App-Seite auf der obersten Ebene, um einen Satz von &quot;Routen&quot;zu generieren und jeden Pfad im Dienst &quot;Angular $routeProvider&quot;zu konfigurieren. Ein Beispiel dafür, wie dies in der Praxis aussieht, finden Sie im angular-App-Modulskript, das vom Geometrixx Outdoors-App-Beispiel generiert wurde: (Link erfordert eine lokale Instanz) [http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

Beim Einblick in die generierte AEMAngularApp finden Sie eine Reihe von Routen, die wie folgt spezifiziert sind:

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

Das obige Beispiel veranschaulicht insbesondere ein Beispiel für die Übergabe eines Parameters als Teil des Pfads. In diesem Beispiel wird angegeben, dass, wenn ein Pfad angefordert wird, der dem angegebenen Muster (/content/phonegap/geometrixx-outdoors/en/home/products/:id) entspricht, von der Vorlage home/products.template.html verarbeitet werden sollte und den Controller &quot;contentphonegapgeometrixxoutdoorsenhomeproducts&quot;verwendet werden sollte.

Die Vorlage, die geladen werden soll, wenn diese Route angefordert wird, wird durch die Eigenschaft templateUrl angegeben. Diese Vorlage enthält die HTML aus AEM Komponenten, die auf der Seite enthalten waren, sowie alle AngularJS-Anweisungen, die für die Verkabelung der Clientseite der Anwendung erforderlich sind. Ein Beispiel für eine AngularJS-Direktive in einer Geometrixx-Komponente finden Sie in Zeile 45 der Datei template.jsp des Swipe-Karussells (/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp).

## Seitenverantwortliche {#page-controllers}

In Angular ist eine eigene Wörterbuchfunktion &quot;ein Controller ist eine JavaScript-Konstruktorfunktion, die zum Erweitern des Angular-Umfangs verwendet wird.&quot; ([source](https://docs.angularjs.org/guide/controller)) Jede Seite in einer AEM App wird automatisch mit einem Controller verbunden, der von jedem Controller, der eine `frameworkType` von `angular`. Sehen Sie sich die ng-text-Komponente als Beispiel an (/libs/mobileapps/components/angular/ng-text), einschließlich des Knotens cq:template , der sicherstellt, dass jedes Mal, wenn diese Komponente zu einer Seite hinzugefügt wird, diese wichtige Eigenschaft enthält.

Für ein komplexeres Controller-Beispiel öffnen Sie das Skript ng-template-page controller.jsp (unter /apps/geometrixx-outdoors-app/components/angular/ng-template-page). Besonders interessant ist der JavaScript-Code, den er bei Ausführung generiert und wie folgt rendert:

```xml
// Controller for page 'products'
.controller('contentphonegapgeometrixxoutdoorsenhomeproducts', ['$scope', '$http', '$routeParams',
    function($scope, $http, $routeParams) {
        var sku = $routeParams.id;
        var productPath = '/' + sku.substring(0, 2) + '/' + sku.substring(0, 4) + '/' + sku;
        var data = $http.get('home/products' + productPath + '.angular.json' + cacheKiller);

        /* ng-product component controller (path: content-par/ng-product) */
        data.then(function(response) {
            $scope.contentparngproduct = response.data["content-par/ng-product"].items;
        });

        /* ng-image component controller (path: content-par/ng-product/ng-image) */
        data.then(function(response) {
            $scope.contentparngproductngimage = response.data["content-par/ng-product/ng-image"].items;
        });
    }
])
```

Im obigen Beispiel wird der Parameter aus dem `$routeParams` wird ausgeführt und dann in die Verzeichnisstruktur massiert, in der die JSON-Daten gespeichert werden. Durch den Umgang mit der SKU `id` auf diese Weise können Sie eine einzelne Produktvorlage bereitstellen, die die Produktdaten für potenziell Tausende von verschiedenen Produkten rendern kann. Dies ist ein weitaus skalierbareres Modell, das eine individuelle Route für jedes Element in einer (potenziell) massiven Produktdatenbank erfordert.

Hier arbeiten auch zwei Komponenten: ng-product erweitert den Umfang mit den Daten, die es aus dem oben stehenden Abschnitt extrahiert `$http` aufrufen. Es gibt auch ein ng-image auf dieser Seite, das wiederum den Bereich mit dem Wert erweitert, den es aus der Antwort abruft. Durch Angular `$http` -Dienst verwenden, wartet jede Komponente geduldig, bis die Anfrage abgeschlossen ist und das von ihr erstellte Versprechen erfüllt ist.

## Die nächsten Schritte {#the-next-steps}

Sobald Sie sich mit Single Page Applications vertraut gemacht haben, finden Sie weitere Informationen unter [Entwickeln von Apps mit PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md).
