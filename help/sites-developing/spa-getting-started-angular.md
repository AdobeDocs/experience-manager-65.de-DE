---
title: Erste Schritte mit SPAs in AEM – Angular
description: Dieser Artikel beschreibt eine Beispiel-SPA, erläutert, wie sie zusammengestellt wird, und ermöglicht es Ihnen, unter Verwendung des Angular-Frameworks schnell mit Ihrer eigenen SPA zu arbeiten.
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
docset: aem65
exl-id: 9528d92b-0989-4e2d-83be-ba6c07c845e2
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 89%

---

# Erste Schritte mit SPAs in AEM – Angular{#getting-started-with-spas-in-aem-angular}

Single Page Applications (SPAs) können ansprechende Erlebnisse für Website-Benutzer bieten. Entwicklerinnen und Entwickler möchten Sites mithilfe von SPA-Frameworks erstellen können, während Autorinnen und Autoren in der Lage sein wollen, Inhalte innerhalb von AEM für eine mit SPA-Frameworks erstellte Site nahtlos zu bearbeiten.

Die SPA-Autorenfunktion bietet eine umfassende Lösung zur Unterstützung von SPAs in AEM. Dieser Artikel beschreibt eine vereinfachte SPA-Anwendung im Angular-Framework, erläutert, wie sie zusammengestellt wird, und ermöglicht es Ihnen, rasch mit Ihrer eigenen SPA zu arbeiten.

>[!NOTE]
>
>Dieser Artikel basiert auf dem Angular-Framework. Das entsprechende Dokument für das React-Framework finden Sie unter [Erste Schritte mit SPAs in AEM – React](/help/sites-developing/spa-getting-started-react.md).

>[!NOTE]
>
>Der SPA Editor ist die empfohlene Lösung für Projekte, die SPA Framework-basiertes Client-seitiges Rendering erfordern (z. B. React oder Angular).

## Einführung {#introduction}

Dieser Artikel fasst die grundlegenden Funktionen einer einfachen SPA und die Grundlagen zusammen, die Sie für deren Nutzung benötigen.

Weitere Details zur Funktionsweise von SPAs in AEM finden Sie in den folgenden Dokumenten:

* [Einführung in SPAs und exemplarische Anleitung](/help/sites-developing/spa-walkthrough.md)
* [Einführung in die SPA-Erstellung](/help/sites-developing/spa-overview.md)
* [SPA-Blueprint](/help/sites-developing/spa-blueprint.md)

>[!NOTE]
>
>Um Inhalte in einem SPA erstellen zu können, muss der Inhalt in AEM gespeichert und durch das Inhaltsmodell verfügbar gemacht werden.
>
>Eine SPA, die außerhalb von AEM entwickelt wurde, wird nicht autorisiert, wenn der Content-Modell-Vertrag nicht eingehalten wird.

Dieses Dokument erläutert die Struktur einer vereinfachten SPA und veranschaulicht ihre Funktionsweise, sodass Sie diese Informationen in Ihrer eigenen SPA anwenden können.

## Abhängigkeiten, Konfiguration und Aufbau {#dependencies-configuration-and-building}

Zusätzlich zur erwarteten Angular-Abhängigkeit kann die Beispiel-SPA zusätzliche Bibliotheken nutzen, um die Erstellung der SPA effizienter zu gestalten.

### Abhängigkeiten {#dependencies}

Die `package.json`-Datei definiert die Anforderungen des übergeordneten SPA-Pakets. Die als Minimum erforderlichen AEM-Abhängigkeiten sind hier aufgelistet.

```
"dependencies": {
  "@adobe/aem-angular-editable-components": "~1.0.3",
  "@adobe/aem-spa-component-mapping": "~1.0.5",
  "@adobe/aem-spa-page-model-manager": "~1.0.3"
}
```

Der `aem-clientlib-generator` wird genutzt, um die Erstellung von Client-Bibliotheken als Teil des Build-Prozesses automatisch zu gestalten.

`"aem-clientlib-generator": "^1.4.1",`

Weitere Details dazu können [hier auf GitHub](https://github.com/wcm-io-frontend/aem-clientlib-generator) gefunden werden.

>[!CAUTION]
>
>`aem-clientlib-generator` muss mindestens Version 1.4.1 sein.

Der `aem-clientlib-generator` wird in der Datei `clientlib.config.js` wie folgt konfiguriert.

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

Bei der Erstellung der Anwendung wird neben dem aem-clientlib-generator zur automatischen Client-Bibliothekserstellung auch [Webpack](https://webpack.js.org/) für die Übertragung verwendet. Daher sieht der Build-Befehl ungefähr so aus:

`"build": "ng build --build-optimizer=false && clientlib",`

Sobald das Paket erstellt wurde, kann es in eine AEM-Instanz hochgeladen werden.

### AEM-Projektarchetyp {#aem-project-archetype}

Für jedes AEM-Projekt sollte der [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) genutzt werden, der SPA-Projekte mithilfe von React oder Angular unterstützt und das SPA-SDK verwendet.

## Anwendungsstruktur {#application-structure}

Wenn Sie die Abhängigkeiten einbeziehen und Ihre App wie beschrieben erstellen, erhalten Sie ein funktionierendes SPA-Paket, das Sie in Ihre AEM-Instanz hochladen können.

Im nächsten Abschnitt dieses Dokuments erfahren Sie, wie eine SPA in AEM strukturiert ist, welche wichtigen Dateien die Anwendung steuern und wie sie zusammenarbeiten.

Eine vereinfachte Bildkomponente wird als Beispiel verwendet, aber alle Komponenten der Anwendung basieren auf dem gleichen Konzept.

### app.module.ts {#app-module-ts}

Der Einstiegspunkt in die SPA ist die hier gezeigte Datei `app.module.ts`, die sich auf den wichtigen Inhalt konzentriert.

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

Die `app.module.ts`-Datei ist der Ausgangspunkt der Anwendung; sie enthält die anfängliche Projektkonfiguration und nutzt `AppComponent` zum Bootstrapping der Anwendung.

#### Statische Instanziierung {#static-instantiation}

Wenn die Komponente mit der Komponentenvorlage statisch instanziiert wird, muss der Wert vom Modell an die Eigenschaften der Komponente übergeben werden. Die Werte des Modells werden als Attribute übergeben, um später als Komponenteneigenschaften verfügbar zu sein.

### app.component.ts {#app-component-ts}

Sobald `app.module.ts` das Bootstrapping für `AppComponent` vornimmt, kann die Anwendung initialisiert werden. Das wird hier in einer vereinfachten Version gezeigt, damit wir uns auf die wichtigen Inhalte konzentrieren können.

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

Durch die Verarbeitung der Seite ruft `app.component.ts` die hier aufgeführte `main-content.component.ts` in einer vereinfachten Version auf.

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

Die `Page` besteht aus Komponenten. Nach der Aufnahme von JSON kann die Seite `Page` diese Komponenten verarbeiten (z. B. `image.component.ts`), wie hier dargestellt.

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

Die zentrale Idee von SPAs in AEM besteht darin, SPA-Komponenten zu AEM-Komponenten zuzuordnen und die Komponente zu aktualisieren, wenn der Inhalt geändert wird (und umgekehrt). Eine Zusammenfassung dieses Kommunikationsmodells finden Sie im Dokument [SPA-Editor – Überblick](/help/sites-developing/spa-overview.md).

`MapTo('my-angular-app/components/image')(Image, ImageEditConfig);`

Die `MapTo`-Methode ordnet die SPA-Komponente der AEM-Komponente zu. Sie unterstützt die Verwendung einer einzelnen Zeichenfolge oder eines Arrays von Zeichenfolgen.

`ImageEditConfig` ist ein Konfigurationsobjekt, das dazu beiträgt, die Authoring-Funktionen einer Komponente zu aktivieren, indem die erforderlichen Metadaten bereitgestellt werden, damit der Editor Platzhalter generieren kann

Wenn kein Inhalt vorhanden ist, werden Etiketten als Platzhalter bereitgestellt, um den leeren Inhalt darzustellen.

#### Dynamisch übergebene Eigenschaften {#dynamically-passed-properties}

Die vom Modell stammenden Daten werden als Eigenschaften der Komponente dynamisch übergeben.

### image.component.html {#image-component-html}

Schließlich kann das Bild in `image.component.html` gerendert werden.

```
// image.component.html
<img [src]="src" [alt]="alt" [title]="title"/>
```

## Freigeben von Informationen zwischen SPA-Komponenten {#sharing-information-between-spa-components}

Regelmäßig müssen Komponenten in einer SPA Daten austauschen. Es gibt mehrere empfohlene Methoden, um dies zu erreichen, wie im Folgenden in der Reihenfolge zunehmender Komplexität aufgeführt.

* **Option 1:** Zentralisieren Sie die Logik und senden Sie sie an die erforderlichen Komponenten, indem Sie beispielsweise eine util-Klasse als reine objektorientierte Lösung verwenden.
* **Option 2:** Geben Sie Komponentenstatus mithilfe einer Statusbibliothek wie NgRx frei.
* **Option 3:** Nutzen Sie die Objekthierarchie durch Anpassen und Erweitern der Container-Komponente.

## Nächste Schritte {#next-steps}

Eine schrittweise Anleitung zum Erstellen einer eigenen SPA finden Sie unter [Erste Schritte mit dem AEM-SPA-Editor – WKND-Events-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=de).

Weitere Informationen dazu, wie Sie sich für die Entwicklung von SPAs für AEM organisieren können, finden Sie im Artikel [Entwickeln von SPAs für AEM](/help/sites-developing/spa-architecture.md).

Weitere Informationen zum dynamischen Modell für die Komponentenzuordnung und dazu, wie es mit SPAs in AEM funktioniert, finden Sie im Artikel [Dynamisches Modell für die Komponentenzuordnung bei SPAs](/help/sites-developing/spa-dynamic-model-to-component-mapping.md).

Wenn Sie SPA in AEM für ein anderes Framework als React oder Angular implementieren möchten oder einfach einen tiefen Einblick in die Funktionsweise des SPA SDK für AEM erhalten möchten, lesen Sie den Abschnitt [SPA Blueprint](/help/sites-developing/spa-blueprint.md) Artikel.
