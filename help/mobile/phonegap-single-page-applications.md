---
title: Single Page Applications (SPA)
description: Auf dieser Seite erfahren Sie mehr über Single Page Applications, d. h. Sie können eine Anwendung erstellen, die mit einer Desktop- oder Mobile App identisch ist.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: daf7bf39-a105-46eb-ab7b-1c59484949e2
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 3%

---

# Single Page Applications (SPA){#single-page-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

[Single Page Applications](https://en.wikipedia.org/wiki/Single-page_application) (SPA) haben eine kritische Masse erreicht und gelten weithin als das effektivste Muster für die Erstellung nahtloser Erlebnisse mit Web-Technologie. Wenn Sie einem SPA-Muster folgen, können Sie eine Anwendung erstellen, die mit einer Desktop- oder mobilen Anwendung identisch ist, aber aufgrund ihrer Grundlage in offenen Webstandards eine Vielzahl von Geräteplattformen und Formfaktoren erreicht.

Im Allgemeinen scheinen SPA leistungsfähiger als herkömmliche seitenbasierte Websites zu sein, da sie normalerweise eine vollständige HTML-Seite **nur einmal** laden (einschließlich CSS, JS und unterstützender Schriftartinhalte) und dann nur genau das laden, was bei jeder Änderung des Status in der App erforderlich ist. Was für diese Statusänderung erforderlich ist, kann je nach ausgewählter Technologie variieren, enthält jedoch in der Regel ein einziges HTML-Fragment, um die vorhandene „Ansicht“ zu ersetzen, und die Ausführung eines JS-Codeblocks, um die neue Ansicht zu verkabeln und ggf. ein Client-seitiges Vorlagenrendering durchzuführen. Die Geschwindigkeit dieser Statusänderung kann noch weiter verbessert werden, indem Vorlagen-Caching-Mechanismen unterstützt werden oder sogar der Offline-Zugriff auf Vorlageninhalte, wenn Adobe PhoneGap verwendet wird.

AEM 6.1 unterstützt die Erstellung und Verwaltung von SPA über AEM Apps. Dieser Artikel bietet eine Einführung in die Konzepte hinter der SPA und deren Verwendung von [AngularJS](https://angularjs.org/), um Ihre Marke in App Store und Google Play zu integrieren.

## SPA in AEM Apps {#spa-in-aem-apps}

Das Single Page Application Framework in AEM Apps ermöglicht die hohe Leistung einer AngularJS-App und versetzt Autorinnen und Autoren (oder andere nicht-technische Mitarbeiter) in die Lage, den Inhalt der App über die Touch-optimierte Drag-and-Drop-Editor-Umgebung zu erstellen und zu verwalten, die traditionell für die Verwaltung von Websites reserviert war. Haben Sie bereits eine mit AEM erstellte Site? Die Wiederverwendung von Inhalten, Komponenten, Workflows, Assets und Berechtigungen ist mit AEM-Programmen ein Kinderspiel.

## AngularJS-Anwendungsmodul {#angularjs-application-module}

AEM Apps übernimmt einen Großteil der AngularJS-Konfiguration für Sie, einschließlich der Zusammenstellung des Top-Level-Moduls Ihrer App. Standardmäßig heißt dieses Modul „AEMAngularApp“ und das Skript, das für seine Erstellung verantwortlich ist, kann unter /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp gefunden (und überlagert) werden.

Bei der Initialisierung Ihrer App müssen Sie unter anderem angeben, von welchen AngularJS-Modulen die App abhängt. Die Liste der von Ihrer App verwendeten Module wird durch ein Skript unter /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp festgelegt und kann von der Seitenkomponente Ihrer eigenen Apps überlagert werden, um alle zusätzlichen AngularJS-Module abzurufen, die für Ihre App erforderlich sind. Vergleichen Sie als Beispiel das obige Skript mit der Geometrixx-Implementierung (unter /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp).

Um die Navigation zwischen den verschiedenen Zuständen in Ihrer App zu unterstützen, durchläuft das angular-App-Modulskript alle untergeordneten Seiten Ihrer App-Seite der obersten Ebene, um eine Reihe von „Routen“ zu generieren, und konfiguriert jeden Pfad auf dem Angular-$routeProvider-Service. Ein Beispiel dafür finden Sie im angular-App-Modulskript , das vom Geometrixx Outdoors-App-Beispiel generiert wurde: (Link erfordert eine lokale Instanz) [http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

Nach dem Eintauchen in die generierte AEMAngularApp finden Sie eine Reihe von Routen, die wie folgt angegeben sind:

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

Insbesondere das obige Beispiel veranschaulicht ein Beispiel für die Übergabe eines -Parameters als Teil des Pfads. In diesem Beispiel wird angegeben, dass ein Pfad, der dem angegebenen Muster (/content/phonegap/geometrixx-outdoors/en/home/products/:id) entspricht, von der Vorlage home/products.template.html verarbeitet und mit dem Controller „contentphonegapgeometrixxoutdoorsenhomeproducts“ verwendet werden soll.

Die Vorlage, die geladen werden soll, wenn diese Route angefordert wird, wird durch die TemplateUrl-Eigenschaft angegeben. Diese Vorlage enthält die HTML von AEM-Komponenten, die auf der Seite enthalten sind, sowie alle AngularJS-Anweisungen, die für die Verkabelung auf der Client-Seite der Anwendung erforderlich sind. Ein Beispiel für eine AngularJS-Direktive in einer Geometrixx-Komponente finden Sie in Zeile 45 der Datei template.jsp des Wischkarussells (/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp).

## Seiten-Controller {#page-controllers}

In den Angular-Eigenausdrücken ist „ein Controller eine JavaScript-Konstruktorfunktion, die verwendet wird, um den Angular-Umfang zu erweitern“. ([source](https://docs.angularjs.org/guide/controller)) Jede Seite in einer AEM-App wird automatisch mit einem Controller verkabelt, der durch einen beliebigen Controller erweitert werden kann, der eine `frameworkType` von `angular` angibt. Sehen Sie sich als Beispiel die Komponente „ng-text“ an (/libs/mobileapps/components/angular/ng-text), einschließlich des Knotens cq:template, der sicherstellt, dass diese Komponente jedes Mal, wenn sie zu einer Seite hinzugefügt wird, diese wichtige Eigenschaft enthält.

Für ein komplexeres Beispiel öffnen Sie das Skript ng-template-page controller.jsp (unter /apps/geometrixx-outdoors-app/components/angular/ng-template-page). Von besonderem Interesse ist der JavaScript-Code, den es bei der Ausführung generiert und der wie folgt gerendert wird:

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

Im obigen Beispiel wird der Parameter aus dem `$routeParams`-Service übernommen und dann in die Verzeichnisstruktur eingebettet, in der die JSON-Daten gespeichert werden. Wenn Sie die SKU-`id` auf diese Weise handhaben, können Sie eine einzelne Produktvorlage bereitstellen, die die Produktdaten für potenziell Tausende von verschiedenen Produkten rendern kann. Dies ist ein weitaus besser skalierbares Modell, bei dem für jedes Element in einer (potenziell) umfangreichen Produktdatenbank eine individuelle Route erforderlich ist.

Hier sind auch zwei Komponenten am Werk: ng-product erweitert den Umfang mit den Daten, die es aus dem obigen `$http`-Aufruf extrahiert. Auf dieser Seite befindet sich auch ein ng-image , das wiederum den Umfang um den Wert erweitert, den es aus der Antwort abruft. Aufgrund des `$http`-Service von Angular wartet jede Komponente geduldig, bis die Anfrage abgeschlossen ist und das erstellte Versprechen erfüllt wird.

## Die nächsten Schritte {#the-next-steps}

Wenn Sie sich mit den Single Page Applications vertraut gemacht haben, lesen Sie [Entwickeln von Apps mit PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md).
