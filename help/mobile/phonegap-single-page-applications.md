---
title: Single Page Applications
seo-title: Einzelseitenanwendungen
description: Auf dieser Seite erfahren Sie mehr über Einzelseitenanwendungen, d. h. Sie können eine Anwendung erstellen, die genauso wie eine Desktop- oder Mobilanwendung funktioniert.
seo-description: Auf dieser Seite erfahren Sie mehr über Einzelseitenanwendungen, d. h. Sie können eine Anwendung erstellen, die genauso wie eine Desktop- oder Mobilanwendung funktioniert.
uuid: d1865e79-6e7c-4149-95c0-556e61478b01
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: a5b5e40e-2457-45fe-9632-baf5008fe8bf
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 3%

---


# Einzelseiten-Webanwendungen{#single-page-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

[Einzelseitenanwendungen](https://en.wikipedia.org/wiki/Single-page_application)  (SPA) haben eine kritische Masse erreicht, die weithin als das effektivste Muster für die Erstellung nahtloser Erlebnisse mit Webtechnologie angesehen wird. Indem Sie ein SPA Muster befolgen, können Sie eine Anwendung erstellen, die genauso wie eine Desktop- oder Mobilanwendung funktioniert, aber aufgrund ihrer Grundlage in offenen Webstandards eine Vielzahl von Geräteplattformen und Formularfaktoren erreicht.

Im Allgemeinen werden SPA leistungsfähiger als herkömmliche seitenbasierte Websites, da sie in der Regel eine vollständige HTML-Seite **nur einmal laden (einschließlich CSS, JS und unterstützender Schriftartinhalte) und dann nur genau das laden, was bei jeder Statusänderung in der App erforderlich ist.** Was für diese Statusänderung erforderlich ist, kann je nach ausgewählter Technologie variieren, enthält jedoch in der Regel ein einzelnes HTML-Fragment, um die vorhandene &quot;Ansicht&quot;zu ersetzen, und die Ausführung eines JS-Codeblocks, um die neue Ansicht zu verkabeln und gegebenenfalls eine clientseitige Vorlagendarstellung durchzuführen. Die Geschwindigkeit dieser Statusänderung kann durch die Unterstützung von Vorlagenzwischenspeicherungsmechanismen noch weiter verbessert werden, oder sogar durch den Offline-Zugriff auf Vorlageninhalte, wenn Adobe PhoneGap verwendet wird.

AEM 6.1 unterstützt das Erstellen und Verwalten von SPA über AEM Apps. Dieser Artikel enthält eine Einführung in die Konzepte hinter der SPA und wie sie [AngularJS](https://angularjs.org/) nutzen, um Ihre Marke in den App Store und Google Play zu bringen.

## SPA in AEM Apps {#spa-in-aem-apps}

Das Einzelseitenanwendungs-Framework in AEM Apps ermöglicht die hohe Leistung einer AngularJS-App und ermöglicht Autoren (oder anderen nicht-technischen Mitarbeitern) die Erstellung und Verwaltung der App-Inhalte über die Touch-optimierte Drag &amp; Drop-Editor-Umgebung, die traditionell für die Verwaltung von Websites reserviert ist. Haben Sie bereits eine Website mit AEM? Sie werden feststellen, dass die Wiederverwendung von Inhalten, Komponenten, Workflows, Assets und Berechtigungen mit AEM Apps einfach ist.

## AngularJS-Anwendungsmodul {#angularjs-application-module}

AEM Apps verarbeitet einen Großteil der AngularJS-Konfiguration für Sie, einschließlich des Zusammenbaus des obersten Moduls Ihrer App. Standardmäßig heißt dieses Modul &quot;AEMAngularApp&quot;, und das für die Erstellung verantwortliche Skript finden Sie unter /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp.

Teil der Initialisierung Ihrer App ist die Angabe, von welchen AngularJS-Modulen die App abhängt. Die Liste der von Ihrer App verwendeten Module wird von einem Skript unter /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp angegeben und kann von der Seitenkomponente Ihrer eigenen Apps überlagert werden, um alle weiteren AngularJS-Module abzurufen, die Ihre App benötigt. Vergleichen Sie beispielsweise das obige Skript mit der Geometrixx-Implementierung (unter /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp).

Zur Unterstützung der Navigation zwischen den verschiedenen Status in Ihrer App durchläuft das Skript des Angular-App-Moduls alle untergeordneten Seiten Ihrer App-Seite auf der obersten Ebene, um eine Reihe von Routen zu generieren und die einzelnen Pfade im $routeProvider-Dienst von Angular zu konfigurieren. Ein Beispiel dafür, wie dies in der Praxis aussieht, finden Sie im App-Beispiel für das Angular-App-Modul-Skript, das vom Geometrixx Outdoors-App-Beispiel generiert wurde: (Link erfordert eine lokale Instanz) [http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

Wenn Sie die generierte AEMAngularApp betrachten, finden Sie eine Reihe von Routen, die wie folgt spezifiziert sind:

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

Das obige Beispiel veranschaulicht insbesondere ein Beispiel für die Übergabe eines Parameters als Teil des Pfads. In diesem Beispiel geben wir an, dass, wenn ein Pfad, der dem angegebenen Muster entspricht (/content/phonegap/geometrixx-outdoors/en/home/products/:id) angefordert wird, von der Vorlage home/products.template.html verarbeitet werden sollte und der Controller &quot;contentphonegapgeometrixxoutdoorsenhomeproducts&quot;verwendet wird.

Die Vorlage, die geladen werden soll, wenn diese Route angefordert wird, wird von der templateUrl-Eigenschaft angegeben. Diese Vorlage enthält den HTML-Code aus AEM Komponenten, die auf der Seite enthalten sind, sowie alle AngularJS-Anweisungen, die zur Verkabelung der Clientseite der Anwendung erforderlich sind. Ein Beispiel für eine AngularJS-Direktive in einer Geometrixx finden Sie in Zeile 45 der Datei &quot;template.jsp&quot;(/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp).

## Seitencontroller {#page-controllers}

In Angulas eigenen Worten: &quot;Ein Controller ist eine JavaScript-Konstruktorfunktion, mit der der Angular-Umfang erweitert wird.&quot; ([source](https://docs.angularjs.org/guide/controller)) Jede Seite in einer AEM App wird automatisch an einen Controller verdrahtet, der von jedem Controller, der einen `frameworkType` von `angular` angibt, erweitert werden kann. Sehen Sie sich die ng-text-Komponente als Beispiel an (/libs/mobileapps/components/angular/ng-text), einschließlich des cq:template-Knotens, der sicherstellt, dass jede Komponente, die einer Seite hinzugefügt wird, diese wichtige Eigenschaft enthält.

Für ein komplexeres Beispiel für einen Controller öffnen Sie das Skript &quot;ng-template-page controller.jsp&quot;(unter /apps/geometrixx-outdoors-app/components/angular/ng-template-page). Von besonderem Interesse ist der JavaScript-Code, den er bei Ausführung generiert, der wie folgt rendert:

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

Im obigen Beispiel werden Sie bemerken, dass wir einen Parameter aus dem `$routeParams`-Dienst nehmen und ihn dann in die Verzeichnisstruktur massieren, in der unsere JSON-Daten gespeichert sind. Indem wir uns mit dem sku `id` auf diese Weise befassen, sind wir in der Lage, eine einzige Produktvorlage zu liefern, die die Produktdaten für potenziell Tausende von verschiedenen Produkten wiedergeben kann. Dies ist ein weitaus skalierbareres Modell, das eine individuelle Route für jeden Artikel in einer (potenziell) umfangreichen Produktdatenbank erfordert.

Es gibt auch zwei Komponenten: ng-product erweitert den Bereich mit den Daten, die es aus dem oben stehenden `$http`-Aufruf extrahiert. Es gibt auch ein ng-Bild auf dieser Seite, das wiederum den Umfang mit dem Wert, den es aus der Antwort abruft, erweitert. Aufgrund des Angular-Dienstes `$http` wartet jede Komponente geduldig, bis die Anforderung abgeschlossen ist und das erstellte Versprechen erfüllt wird.

## Die nächsten Schritte {#the-next-steps}

Sobald Sie Informationen zu Einzelseitenanwendungen erhalten haben, finden Sie unter [Entwickeln von Apps mit PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md).
