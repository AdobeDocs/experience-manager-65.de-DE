---
title: Single Page Applications
seo-title: Einzelseitenanwendungen
description: Auf dieser Seite erfahren Sie mehr über Einzelseitenanwendungen, d. h. Sie können eine Anwendung erstellen, die genauso wie eine Desktop- oder mobile Anwendung funktioniert.
seo-description: Auf dieser Seite erfahren Sie mehr über Einzelseitenanwendungen, d. h. Sie können eine Anwendung erstellen, die genauso wie eine Desktop- oder mobile Anwendung funktioniert.
uuid: d1865e79-6e7c-4149-95c0-556e61478b01
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: a5b5e40e-2457-45fe-9632-baf5008fe8bf
exl-id: daf7bf39-a105-46eb-ab7b-1c59484949e2
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 3%

---

# Single Page Applications{#single-page-applications}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

[Single Page Applications](https://en.wikipedia.org/wiki/Single-page_application)  (SPA) haben eine kritische Masse erreicht, die weithin als das effektivste Muster für die Erstellung nahtloser Erlebnisse mit Web-Technologie betrachtet wird. Durch Befolgen eines SPA können Sie eine Anwendung erstellen, die eine identische Leistung wie eine Desktop- oder mobile Anwendung erbringt, aber aufgrund ihrer Grundlage in offenen Webstandards eine Vielzahl von Geräteplattformen und Formfaktoren erreicht.

Im Allgemeinen sind SPA leistungsfähiger als herkömmliche seitenbasierte Websites, da sie normalerweise eine vollständige HTML-Seite **nur einmal** laden (einschließlich CSS, JS und unterstützenden Schriftartinhalten) und dann nur genau das laden, was bei jeder Statusänderung in der App erforderlich ist. Was für diese Statusänderung erforderlich ist, kann je nach gewählter Technologie variieren, enthält jedoch in der Regel ein einzelnes HTML-Fragment, um die vorhandene &quot;Ansicht&quot;zu ersetzen, und die Ausführung eines JS-Codeblocks, um die neue Ansicht abzuschließen und gegebenenfalls eine clientseitige Vorlagendarstellung durchzuführen. Die Geschwindigkeit dieser Statusänderung kann durch die Unterstützung von Vorlagen-Caching-Mechanismen oder sogar durch den Offline-Zugriff auf Vorlageninhalte bei Verwendung von Adobe PhoneGap noch weiter verbessert werden.

AEM 6.1 unterstützt die Erstellung und Verwaltung von SPA über AEM Apps. Dieser Artikel bietet eine Einführung in die Konzepte hinter dem SPA und wie sie [AngularJS](https://angularjs.org/) nutzen, um Ihre Marke in den App Store und Google Play zu bringen.

## SPA in AEM Apps {#spa-in-aem-apps}

Das Single Page Application Framework in AEM Apps ermöglicht die hohe Leistung einer AngularJS-App und ermöglicht es Autoren (oder anderen nicht-technischen Mitarbeitern), den Inhalt der App über die Touch-optimierte Drag &amp; Drop-Editorumgebung zu erstellen und zu verwalten, die traditionell für die Verwaltung von Websites reserviert ist. Sie haben bereits eine Website mit AEM erstellt? Sie werden feststellen, dass die Wiederverwendung Ihrer Inhalte, Komponenten, Workflows, Assets und Berechtigungen in AEM Apps einfach ist.

## AngularJS-Anwendungsmodul {#angularjs-application-module}

AEM Apps verarbeitet einen Großteil der AngularJS-Konfiguration für Sie, einschließlich des Zusammenbaus des obersten Moduls Ihrer App. Standardmäßig trägt dieses Modul den Namen &quot;AEMAngularApp&quot;und das für die Erstellung verantwortliche Skript befindet sich unter /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp.

Teil der Initialisierung Ihrer App ist die Angabe, von welchen AngularJS-Modulen die App abhängig ist. Die Liste der von Ihrer App verwendeten Module wird von einem Skript unter /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp angegeben und kann von der Seitenkomponente Ihrer eigenen Apps überlagert werden, um alle zusätzlichen AngularJS-Module abzurufen, die für Ihre App erforderlich sind. Vergleichen Sie beispielsweise das obige Skript mit der Geometrixx-Implementierung (unter /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp).

Um die Navigation zwischen den verschiedenen Status in Ihrer App zu unterstützen, durchläuft das Skript angular-app-module alle nachfolgenden Seiten Ihrer App-Seite auf der obersten Ebene, um einen Satz von &quot;Routen&quot;zu generieren und jeden Pfad auf dem Dienst &quot;Angular $routeProvider&quot;zu konfigurieren. Ein Beispiel dafür, wie dies in der Praxis aussieht, finden Sie im angular-app-module -Skript, das vom Geometrixx Outdoors-App-Beispiel generiert wurde: (Link erfordert eine lokale Instanz) [http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

Beim Einblick in die generierte AEMAngularApp finden Sie eine Reihe von Routen, die wie folgt spezifiziert sind:

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

Das obige Beispiel veranschaulicht insbesondere ein Beispiel für die Übergabe eines Parameters als Teil des Pfads. In diesem Beispiel zeigen wir an, dass, wenn ein Pfad angefordert wird, der dem angegebenen Muster (/content/phonegap/geometrixx-outdoors/en/home/products/:id) entspricht, er von der Vorlage home/products.template.html verarbeitet werden sollte und den Controller &quot;contentphonegapgeometrixxoutdoorsenhomeproducts&quot;verwendet werden sollte.

Die Vorlage, die geladen werden soll, wenn diese Route angefordert wird, wird durch die Eigenschaft templateUrl angegeben. Diese Vorlage enthält den HTML-Code aus AEM Komponenten, die auf der Seite enthalten waren, sowie alle AngularJS-Anweisungen, die für die Verkabelung der Clientseite der Anwendung erforderlich sind. Ein Beispiel für eine AngularJS-Direktive in einer Geometrixx-Komponente finden Sie in Zeile 45 der Datei template.jsp des Swipe-Karussells (/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp).

## Seitenverantwortliche {#page-controllers}

In Angular ist eine eigene Wörterbuchfunktion &quot;ein Controller ist eine JavaScript-Konstruktorfunktion, die zum Erweitern des Angular-Umfangs verwendet wird.&quot; ([source](https://docs.angularjs.org/guide/controller)) Jede Seite in einer AEM App wird automatisch mit einem Controller verbunden, der von jedem Controller, der einen `frameworkType` von `angular` angibt, erweitert werden kann. Sehen Sie sich die ng-text-Komponente als Beispiel an (/libs/mobileapps/components/angular/ng-text), einschließlich des Knotens cq:template , der sicherstellt, dass jede Komponente, die zu einer Seite hinzugefügt wird, diese wichtige Eigenschaft enthält.

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

Im obigen Beispiel werden Sie feststellen, dass wir einen Parameter aus dem `$routeParams`-Dienst nehmen und ihn dann in die Verzeichnisstruktur massieren, in der unsere JSON-Daten gespeichert sind. Indem wir uns auf diese Weise mit der SKU `id` beschäftigen, können wir eine einzige Produktvorlage bereitstellen, die die Produktdaten für potenziell Tausende von verschiedenen Produkten rendern kann. Dies ist ein viel skalierbareres Modell, das eine individuelle Route für jedes Element in einer (potenziell) massiven Produktdatenbank erfordert.

Hier arbeiten auch zwei Komponenten: ng-product erweitert den Bereich mit den Daten, die es aus dem obigen `$http`-Aufruf extrahiert. Es gibt auch ein ng-image auf dieser Seite, das wiederum den Bereich mit dem Wert erweitert, den es aus der Antwort abruft. Aufgrund des Angular `$http` wartet jede Komponente geduldig, bis die Anfrage abgeschlossen ist und das von ihr erstellte Versprechen erfüllt ist.

## Die nächsten Schritte {#the-next-steps}

Sobald Sie sich mit den Single Page Applications vertraut gemacht haben, finden Sie weitere Informationen unter [Entwickeln von Apps mit PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md).
