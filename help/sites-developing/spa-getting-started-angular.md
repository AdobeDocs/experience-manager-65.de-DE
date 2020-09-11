---
title: Erste Schritte mit SPAs in AEM - Angular
seo-title: Erste Schritte mit SPAs in AEM - Angular
description: In diesem Artikel wird eine Beispielanwendung für die SPA vorgestellt, erklärt, wie sie zusammengestellt wird, und es wird Ihnen ermöglicht, mit dem Angular-Framework schnell eine eigene SPA-Anwendung einzurichten.
seo-description: In diesem Artikel wird eine Beispielanwendung für die SPA vorgestellt, erklärt, wie sie zusammengestellt wird, und es wird Ihnen ermöglicht, mit dem Angular-Framework schnell eine eigene SPA-Anwendung einzurichten.
uuid: d3d2fa63-68c8-4a48-8c8d-045f4f8db937
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 9cdd7648-d67e-414d-aedf-a5687da39326
docset: aem65
translation-type: tm+mt
source-git-commit: 4c9a0bd73e8d87d3869c6a133f5d1049f8430cd1
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 31%

---


# Getting Started with SPAs in AEM - Angular{#getting-started-with-spas-in-aem-angular}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwickler möchten in der Lage sein, Websites mithilfe von SPA-Frameworks zu erstellen, und Autoren möchten Inhalte innerhalb von AEM für eine Website, die mit SPA-Frameworks erstellt wurde, nahtlos bearbeiten.

Die SPA-Erstellungsfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. In diesem Artikel wird eine vereinfachte SPA-Anwendung für das Angular-Framework vorgestellt, die erklärt, wie sie zusammengestellt wird, sodass Sie sich schnell mit Ihrer eigenen SPA vertraut machen können.

>[!NOTE]
>
>Dieser Artikel basiert auf dem Angular-Framework. Das entsprechende Dokument für das React Framework finden Sie unter [Erste Schritte mit SPAs in AEM - Reaktion](/help/sites-developing/spa-getting-started-react.md).

>[!NOTE]
>
>Der SPA-Editor ist die empfohlene Lösung für Projekte, bei denen clientseitiges Rendering (z.B. React oder Angular) durch das SPA-Framework erforderlich ist.

## Einführung {#introduction}

Dieser Artikel fasst die grundlegenden Funktionen einer einfachen SPA und die Grundlagen zusammen, die Sie für deren Nutzung benötigen.

Weitere Informationen über die Funktionsweise von BSG in AEM finden Sie in den folgenden Dokumenten:

* [Einführung und exemplarische Vorgehensweisen zu SPA](/help/sites-developing/spa-walkthrough.md)
* [Einführung in die SPA-Erstellung](/help/sites-developing/spa-overview.md)
* [SPA-Blueprint](/help/sites-developing/spa-blueprint.md)

>[!NOTE]
>
>Um Inhalt in einer SPA zu erstellen, muss der Inhalt in AEM gespeichert und durch das Inhaltsmodell verfügbar gemacht werden.
>
>Eine SPA, die außerhalb von AEM entwickelt wurde, wird nicht autorisiert, wenn der Content-Modell-Vertrag nicht eingehalten wird.

In diesem Dokument wird die Struktur eines vereinfachten BSG erläutert, wie es funktioniert, sodass Sie dieses Verständnis auf Ihr eigenes BSG anwenden können.

## Abhängigkeiten, Konfiguration und Aufbau {#dependencies-configuration-and-building}

Zusätzlich zur erwarteten Angular-Abhängigkeit kann die Beispiel-SPA zusätzliche Bibliotheken nutzen, um die Erstellung der SPA effizienter zu gestalten.

### Abhängigkeiten {#dependencies}

Die `package.json` Datei definiert die Anforderungen des gesamten SPA-Pakets. Die erforderlichen AEM Abhängigkeiten sind hier aufgelistet.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
```

The `aem-clientlib-generator` is leveraged to make the creation of client libraries automatic as part of the build process.

`"aem-clientlib-generator": "^1.4.1",`

Weitere Details dazu können [hier auf GitHub](https://github.com/wcm-io-frontend/aem-clientlib-generator) gefunden werden.

>[!CAUTION]
>
>Die Mindestversion der `aem-clientlib-generator` erforderlichen Version ist 1.4.1.

The `aem-clientlib-generator` is configured in the `clientlib.config.js` file as follows.

```
module.exports = {
    // default working directory (can be changed per 'cwd' in every asset option)
    context: __dirname,

    // path to the clientlib root folder (output)
    clientLibRoot: "./../content/jcr_root/apps/my-angular-app/clientlibs",

    libs: {
        name: "my-angular-app",
        allowProxy: true,
        categories: ["my-angular-app"],
        embed: ["my-angular-app.responsivegrid"],
        jsProcessor: ["min:gcc"],
        serializationFormat: "xml",
        assets: {
            js: [
                "dist/**/*.js"
            ],
            css: [
                "dist/**/*.css"
            ]
        }
    }
};
```

### Erstellung {#building}

Bei der Erstellung der App wird neben dem aem-clientlib-generator zur automatischen Client-Bibliothekserstellung auch [Webpack](https://webpack.js.org/) für die Übertragung verwendet. Daher ähnelt der Aufbaubefehl dem folgenden:

`"build": "ng build --build-optimizer=false && clientlib",`

Sobald das Paket erstellt wurde, kann es in eine AEM-Instanz hochgeladen werden.

### AEM-Projektarchetyp {#aem-project-archetype}

Jedes AEM Projekt sollte den [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)nutzen, der SPA-Projekte mit React oder Angular unterstützt und das SPA-SDK nutzt.

## Anwendungsstruktur {#application-structure}

Wenn Sie die Abhängigkeiten einbeziehen und Ihre App wie oben beschrieben erstellen, erhalten Sie ein funktionierendes SPA-Paket, das Sie in Ihre AEM Instanz hochladen können.

Im nächsten Abschnitt dieses Dokuments erfahren Sie, wie eine SPA in AEM strukturiert ist, welche wichtigen Dateien die Anwendung antreiben und wie sie zusammenarbeiten.

Eine vereinfachte Bildkomponente wird als Beispiel verwendet, aber alle Komponenten der Anwendung basieren auf demselben Konzept.

### app.module.ts {#app-module-ts}

The entry point into the SPA is the `app.module.ts` file shown here simplified to focus on the important content.

```
// app.module.ts
import { BrowserModule, BrowserTransferStateModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { SpaAngularEditableComponentsModule } from '@adobe/aem-angular-editable-components';
import { AppRoutingModule } from './app-routing.module';

@NgModule({
  imports: [ BrowserModule.withServerTransition({ appId: 'my-angular-app' }),
    SpaAngularEditableComponentsModule,
    AppRoutingModule,
    BrowserTransferStateModule ],
  providers: ...,
  declarations: [ ... ],
  entryComponents: [ ... ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```

Die `app.module.ts` Datei ist der Ausgangspunkt der App und enthält die anfängliche Projektkonfiguration und dient zum Bootstrapping der App `AppComponent` .

#### Statische Instanziierung {#static-instantiation}

Wenn die Komponente mit der Komponentenvorlage statisch instanziiert wird, muss der Wert vom Modell an die Eigenschaften der Komponente übergeben werden. Die Werte des Modells werden als Attribute übergeben, die später als Komponenteneigenschaften verfügbar sein sollen.

### app.component.ts {#app-component-ts}

Sobald `app.module.ts` Bootstraps `AppComponent`gestartet wurden, kann die App initialisiert werden, was hier in einer vereinfachten Version angezeigt wird, um sich auf wichtige Inhalte zu konzentrieren.

```
// app.component.ts
import { Component } from '@angular/core';
import { ModelManager } from '@adobe/aem-spa-page-model-manager';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-root',
  template: `
    <router-outlet></router-outlet>
  `
})

export class AppComponent {
  items;
  itemsOrder;
  path;

  constructor() {
    ModelManager.initialize().then(this.updateData.bind(this));
  }

  private updateData(model) {
    this.path = model[Constants.PATH_PROP];
    this.items = model[Constants.ITEMS_PROP];
    this.itemsOrder = model[Constants.ITEMS_ORDER_PROP];
  }
}
```

### main-content.component.ts {#main-content-component-ts}

Durch die Verarbeitung der Seite werden `app.component.ts` Aufrufe in einer vereinfachten Version `main-content.component.ts` angezeigt.

```
import { Component } from '@angular/core';
import { ModelManagerService }     from '../model-manager.service';
import { ActivatedRoute } from '@angular/router';
import { Constants } from "@adobe/aem-angular-editable-components";

@Component({
  selector: 'app-main',
  template: `
    <aem-page class="structure-page" [attr.data-cq-page-path]="path" [cqPath]="path" [cqItems]="items" [cqItemsOrder]="itemsOrder" ></aem-page>
  `
})

export class MainContentComponent {
  items;
  itemsOrder;
  path;

  constructor( private route: ActivatedRoute,
    private modelManagerService: ModelManagerService) {
    this.modelManagerService.getData({ path: this.route.snapshot.data.path }).then((data) => {
      this.path = data[Constants.PATH_PROP];
      this.items = data[Constants.ITEMS_PROP];
      this.itemsOrder = data[Constants.ITEMS_ORDER_PROP];
    });
  }
}
```

Der `MainComponent` nimmt die JSON-Repräsentation des Seitenmodells auf und verarbeitet den Inhalt, um jedes Element der Seite zu umhüllen/dekorieren. Weitere Details zum `Page` finden Sie im Dokument [SPA-Blueprint](/help/sites-developing/spa-blueprint.md#main-pars-header-1694932501).

### image.component.ts {#image-component-ts}

Das `Page` besteht aus Komponenten. Mit der Integration von JSON `Page` können diese Komponenten verarbeitet werden, wie hier `image.component.ts` dargestellt.

```
/// image.component.ts
import { Component, Input } from '@angular/core';

const ImageEditConfig = {

    emptyLabel: 'Image',

    isEmpty: function(cqModel) {
        return !cqModel || !cqModel.src || cqModel.src.trim().length < 1;
    }
};

@Component({
  selector: 'app-image',
  templateUrl: './image.component.html',
})

export class ImageComponent {
  @Input() src: string;
  @Input() alt: string;
  @Input() title: string;
}

MapTo('my-angular-app/components/image')(ImageComponent, ImageEditConfig);
```

Die zentrale Idee von SPAs in AEM ist die Idee, SPA-Komponenten auf AEM-Komponenten abzubilden und die Komponente zu aktualisieren, wenn der Inhalt geändert wird (und umgekehrt). See the document [SPA Editor Overview](/help/sites-developing/spa-overview.md) for an summary of this communication model.

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

Die `MapTo`-Methode ordnet die SPA-Komponente der AEM-Komponente zu. Es unterstützt die Verwendung einer einzelnen Zeichenfolge oder eines Arrays von Zeichenfolgen.

`ImageEditConfig` ist ein Konfigurationsobjekt, das dazu beiträgt, die Authoring-Funktionen einer Komponente zu aktivieren, indem die erforderlichen Metadaten bereitgestellt werden, damit der Editor Platzhalter generieren kann

Wenn kein Inhalt vorhanden ist, werden Etiketten als Platzhalter bereitgestellt, um den leeren Inhalt darzustellen.

#### Dynamisch weitergegebene Eigenschaften {#dynamically-passed-properties}

Die vom Modell stammenden Daten werden dynamisch als Eigenschaften der Komponente übergeben.

### image.component.html {#image-component-html}

Schließlich kann das Bild gerendert werden `image.component.html`.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Freigeben von Informationen zwischen SPA-Komponenten {#sharing-information-between-spa-components}

Es ist regelmäßig erforderlich, dass Komponenten in einer Einzelseitenanwendung Informationen austauschen. Es gibt mehrere empfohlene Methoden, um dies zu tun, wie folgt in steigender Reihenfolge der Komplexität aufgeführt.

* **Option 1:** Zentralisieren Sie die Logik und senden Sie sie an die erforderlichen Komponenten, indem Sie beispielsweise eine util-Klasse als reine objektorientierte Lösung verwenden.
* **Option 2:** Freigeben von Komponentenstatus mithilfe einer Statusbibliothek wie NgRx
* **Option 3:** Nutzen Sie die Objekthierarchie durch Anpassen und Erweitern der Container-Komponente.

## Nächste Schritte {#next-steps}

Eine schrittweise Anleitung zum Erstellen Ihrer eigenen SPA finden Sie im Lernprogramm [Erste Schritte mit dem AEM SPA Editor - WKND Ereignisse](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-spa-wknd-tutorial-develop.html).

Weitere Informationen darüber, wie Sie sich für die Entwicklung von SPAs organisieren können, finden Sie AEM Artikel [Entwickeln von SPAs für AEM](/help/sites-developing/spa-architecture.md).

Weitere Informationen zum dynamischen Modell für die Komponentenzuordnung und zur Funktionsweise in SPAs in AEM finden Sie im Artikel [Dynamisches Modell für Komponentenzuordnung für SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Wenn Sie SPAs in AEM für ein anderes Framework als React oder Angular implementieren möchten oder einfach einen tiefen Einblick in die Funktionsweise des SPA SDK for AEM haben möchten, lesen Sie den Artikel [SPA Blueprint](/help/sites-developing/spa-blueprint.md) .
