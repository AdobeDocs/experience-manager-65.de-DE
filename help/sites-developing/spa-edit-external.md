---
title: Bearbeiten einer externen SPA in AEM
description: In diesem Dokument werden die empfohlenen Schritte zum Hochladen eines eigenständigen SPA zu einer AEM Instanz, zum Hinzufügen bearbeitbarer Inhaltsabschnitte und zum Aktivieren des Authoring beschrieben.
translation-type: tm+mt
source-git-commit: 431bed450ed5b0239d9191dcf061f01e64b8981a
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 99%

---

# Bearbeiten einer externen SPA in AEM {#editing-external-spa-within-aem}

Wenn Sie entscheiden, welchen Grad der Integration Sie zwischen Ihrer externen SPA und AEM haben möchten, müssen Sie die SPA oft in AEM anzeigen und bearbeiten können.

## Überblick {#overview}

In diesem Dokument werden die empfohlenen Schritte zum Hochladen eines eigenständigen SPA zu einer AEM Instanz, zum Hinzufügen bearbeitbarer Inhaltsabschnitte und zum Aktivieren des Authoring beschrieben.

## Voraussetzungen {#prerequisites}

Die Voraussetzungen sind einfach.

* Stellen Sie sicher, dass eine Instanz von AEM lokal ausgeführt wird.
* Erstellen Sie ein AEM-SPA-Projekt mit [dem AEM-Projektarchetyp.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de#available-properties)
   * Dies bildet die Grundlage des AEM-Projekts, das aktualisiert wird, um die externe SPA einzubeziehen.
   * Für die Beispiele in diesem Dokument verwenden wir das [WKND-SPA-Projekt](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=de#spa-editor) als Ausgangspunkt.
* Halten Sie die funktionierende, externe React SPA bereit, die Sie integrieren möchten.

## Hochladen der SPA in das AEM-Projekt {#upload-spa-to-aem-project}

Zunächst müssen Sie die externe SPA in Ihr AEM-Projekt hochladen.

1. Ersetzen Sie `src` im Projektordner `/ui.frontend` durch den Ordner `src` des React-Programms.
1. Schließen Sie alle weiteren Abhängigkeiten in der Datei `package.json` der App in die Datei `/ui.frontend/package.json` ein.
   * Stellen Sie sicher, dass die SDK-Abhängigkeiten der SPA den [empfohlenen Versionen](spa-getting-started-react.md#dependencies) entsprechen.
1. Fügen Sie alle Anpassungen in den Ordner `/public` ein.
1. Fügen Sie alle hinzugefügten Inline-Skripte oder Stile ein die Datei `/public/index.html` ein.

## Konfigurieren der Remote-SPA {#configure-remote-spa}

Da die externe SPA nun Teil Ihres AEM-Projekts ist, muss sie in AEM konfiguriert werden.

### Einschließen der Adobe SPA-SDK-Pakete {#include-spa-sdk-packages}

Um die AEM SPA-Funktionen nutzen zu können, gibt es Abhängigkeiten von den folgenden drei Paketen.

* [`@adobe/aem-react-editable-components`](https://github.com/adobe/aem-react-editable-components)
* [`@adobe/aem-spa-component-mapping`](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)
* [`@adobe/aem-spa-page-model-manager`](https://www.npmjs.com/package/@adobe/aem-spa-model-manager)

`@adobe/aem-spa-page-model-manager` stellt die API zum Initialisieren eines Modell-Managers und zum Abrufen des Modells aus der AEM-Instanz bereit. Dieses Modell kann dann zum Rendern von AEM-Komponenten mithilfe der APIs von `@adobe/aem-react-editable-components` und `@adobe/aem-spa-component-mapping` verwendet werden.

#### Installation {#installation}

Führen Sie den folgenden npm-Befehl aus, um die erforderlichen Pakete zu installieren.

```shell
npm install --save @adobe/aem-spa-component-mapping @adobe/aem-spa-page-model-manager @adobe/aem-react-editable-components
```

### ModelManager-Initialisierung {#model-manager-initialization}

Bevor die App gerendert wird, muss der [`ModelManager`](spa-blueprint.md#pagemodelmanager) initialisiert werden, um die Erstellung des AEM `ModelStore` zu verarbeiten.

Dies muss innerhalb der `src/index.js`-Datei Ihres Programms oder überall dort erfolgen, wo der Stamm des Programms gerendert wird.

Dazu können wir die `initializationAsync`-API verwenden, die von `ModelManager` bereitgestellt wird.

Der folgende Screenshot zeigt, wie die Initialisierung von `ModelManager` in einem einfachen React-Programm aktiviert wird. Die einzige Einschränkung ist, dass `initializationAsync` vor `ReactDOM.render()` aufgerufen werden muss.

![ModelManager initialisieren](assets/external-spa-initialize-modelmanager.png)

In diesem Beispiel wird `ModelManager` initialisiert und ein leerer `ModelStore` erstellt.

`initializationAsync` kann optional ein `options`-Objekt als Parameter akzeptieren:

* `path` - Bei der Initialisierung wird das Modell vom definierten Pfad abgerufen und im `ModelStore` gespeichert. Auf diese Weise können Sie bei Bedarf das `rootModel` bei der Initialisierung abrufen.
* `modelClient` - Ermöglicht die Bereitstellung eines benutzerdefinierten Clients, der für das Abrufen des Modells verantwortlich ist.
* `model` - Ein `model`-Objekt, das als Parameter übergeben wird und typischerweise bei der [Verwendung von SSR](spa-ssr.md) gefüllt wird.

### Bearbeitbare AEM-Blattkomponenten {#authorable-leaf-components}

1. Erstellen/identifizieren Sie eine AEM-Komponente, für die eine bearbeitbare React-Komponente erstellt werden soll. In diesem Beispiel verwenden wir die Textkomponente des WKND-Projekts.

   ![WKND-Textkomponente](assets/external-spa-text-component.png)

1. Erstellen Sie eine einfache React-Textkomponente in der SPA. In diesem Beispiel wurde eine neue Datei `Text.js` mit folgendem Inhalt erstellt.

   ![Text.js](assets/external-spa-textjs.png)

1. Erstellen Sie ein Konfigurationsobjekt, um die für die Aktivierung der AEM-Bearbeitung erforderlichen Attribute anzugeben.

   ![config-Objekt erstellen](assets/external-spa-config-object.png)

   * `resourceType` ist zwingend erforderlich, um die React-Komponente der AEM Komponente zuzuordnen und die Bearbeitung beim Öffnen im AEM-Editor zu ermöglichen.

1. Verwenden Sie die Wrapper-Funktion `withMappable`.

   ![withMappable verwenden](assets/external-spa-withmappable.png)

   Diese Wrapper-Funktion ordnet die React-Komponente dem in der Konfiguration angegebenen AEM-`resourceType` zu und aktiviert beim Öffnen im AEM-Editor die Bearbeitungsfunktionen. Bei eigenständigen Komponenten wird auch der Modellinhalt für den jeweiligen Knoten abgerufen.

   >[!NOTE]
   >
   >In diesem Beispiel gibt es unterschiedliche Versionen der Komponente: in AEM eingeschlossene und nicht eingeschlossene React-Komponenten. Die eingeschlossene Version muss verwendet werden, wenn die Komponente explizit verwendet wird. Wenn die Komponente Teil einer Seite ist, können Sie weiterhin die Standardkomponente verwenden (wie derzeit im SPA-Editor).

1. Rendern des Inhalts in der Komponente

   Die JCR-Eigenschaften der Textkomponente werden wie folgt in AEM angezeigt.

   ![Eigenschaften von Textkomponenten](assets/external-spa-text-properties.png)

   Diese Werte werden als Eigenschaften an die neu erstellte React-Komponente `AEMText` übergeben und können zum Rendern des Inhalts verwendet werden.

   ```javascript
   import React from 'react';
   import { withMappable } from '@adobe/aem-react-editable-components';
   
   export const TextEditConfig = {
       // Empty component placeholder label
       emptyLabel:'Text', 
       isEmpty:function(props) {
          return !props || !props.text || props.text.trim().length < 1;
       },
       // resourcetype of the AEM counterpart component
       resourceType:'wknd-spa-react/components/text'
   };
   
   const Text = ({ text }) => (<div>{text}</div>);
   
   export default Text;
   
   export const AEMText = withMappable(Text, TextEditConfig);
   ```

   So wird die Komponente angezeigt, wenn die AEM Konfigurationen abgeschlossen sind.

   ```javascript
   const Text = ({ cqPath, richText, text }) => {
      const richTextContent = () => (
         <div className="aem_text" id={cqPath.substr(cqPath.lastIndexOf('/') + 1)} data-rte-editelement dangerouslySetInnerHTML={{__html: text}}/>
      );
      return richText ? richTextContent() : (<div className="aem_text">{text}</div>);
   };
   ```

   >[!NOTE]
   >
   >In diesem Beispiel haben wir weitere Anpassungen an der gerenderten Komponente vorgenommen, um sie an die vorhandene Textkomponente anzupassen. Dies hat jedoch nichts mit dem Authoring in AEM zu tun.

#### Hinzufügen von bearbeitbaren Komponenten zur Seite {#add-authorable-component-to-page}

Nachdem die bearbeitbaren React-Komponenten erstellt wurden, können wir sie im gesamten Programm verwenden.

Nehmen wir eine Beispielseite, auf der wir einen Text aus dem WKND-SPA-Projekt hinzufügen müssen. In diesem Beispiel möchten wir den Text „Hello World!“ auf `/content/wknd-spa-react/us/en/home.html` anzeigen.

1. Legen Sie den Pfad der anzuzeigenden Knoten fest.

   * `pagePath`: Die Seite, die den Knoten enthält, in unserem Beispiel `/content/wknd-spa-react/us/en/home`
   * `itemPath`: Pfad zum Knoten innerhalb der Seite, in unserem Beispiel `root/responsivegrid/text`
      * Dieser besteht aus den Namen der enthaltenen Elemente auf der Seite.

   ![Pfad des Knotens](assets/external-spa-path.png)

1. Fügen Sie die Komponente an gewünschter Position in die Seite ein.

   ![Komponente zur Seite hinzufügen](assets/external-spa-add-component.png)

   Die `AEMText`-Komponente kann an der gewünschten Position in die Seite eingefügt werden, wobei die Werte `pagePath` und `itemPath` als Eigenschaften festgelegt sind. `pagePath` ist eine obligatorische Eigenschaft.

#### Überprüfen der Bearbeitung von Textinhalten in AEM {#verify-text-edit}

Wir können die Komponente jetzt in unserer laufenden AEM-Instanz testen.

1. Führen Sie den folgenden Maven-Befehl aus dem Verzeichnis `aem-guides-wknd-spa` aus, um das Projekt zu erstellen und in AEM bereitzustellen.

```shell
mvn clean install -PautoInstallSinglePackage
```

1. Navigieren Sie in Ihrer AEM-Instanz zu `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`.

![Bearbeiten der SPA in AEM](assets/external-spa-edit-aem.png)

Die `AEMText`-Komponente kann jetzt in AEM bearbeitet werden.

### In AEM bearbeitbare Seiten {#aem-authorable-pages}

1. Identifizieren Sie eine Seite, die zur Bearbeitung in der SPA hinzugefügt werden soll. In diesem Beispiel wird `/content/wknd-spa-react/us/en/home.html` verwendet.
1. Erstellen Sie eine neue Datei (z. B. `Page.js`) für die bearbeitbare Seitenkomponente. Hier können wir die in `@adobe/cq-react-editable-components` bereitgestellte Seitenkomponente wiederverwenden.
1. Wiederholen Sie Schritt 4 im Abschnitt [Bearbeitbare AEM-Blattkomponenten.](#authorable-leaf-components) Verwenden Sie die Wrapper-Funktion `withMappable` für die Komponente.
1. Wenden Sie wie zuvor `MapTo` auf die AEM-Ressourcentypen für alle untergeordneten Komponenten in der Seite an.

   ```javascript
   import { Page, MapTo, withMappable } from '@adobe/aem-react-editable-components';
   import Text, { TextEditConfig } from './Text';
   
   export default withMappable(Page);
   
   MapTo('wknd-spa-react/components/text')(Text, TextEditConfig);
   ```

   >[!NOTE]
   >
   >In diesem Beispiel verwenden wir die eingeschlossene React-Textkomponente anstelle der zuvor erstellten eingeschlossenen `AEMText`-Komponente. Das liegt daran, dass, wenn die Komponente Teil einer Seite/eines Containers und nicht eigenständig ist, der Container sich um die rekursive Zuordnung der Komponente und die Aktivierung der Authoring-Funktionen kümmert und der zusätzliche Wrapper nicht für jedes untergeordnete Element benötigt wird.

1. Um eine bearbeitbare Seite in der SPA hinzuzufügen, folgen Sie denselben Schritten wie im Abschnitt [Hinzufügen von bearbeitbaren Komponenten zur Seite.](#add-authorable-component-to-page) Hier können wir die `itemPath`-Eigenschaft jedoch überspringen.

#### Überprüfen des Seiteninhalts in AEM {#verify-page-content}

Um zu überprüfen, ob die Seite bearbeitet werden kann, folgen Sie denselben Schritten im Abschnitt [Überprüfen der Bearbeitung von Textinhalten in AEM.](#verify-text-edit)

![Bearbeiten einer Seite in AEM](assets/external-spa-edit-page.png)

Die Seite ist nun in AEM mit einem Layout-Container und einer untergeordneten Textkomponente bearbeitbar.

### Virtuelle Blattkomponenten {#virtual-leaf-components}

In den vorherigen Beispielen haben wir der SPA Komponenten mit vorhandenen AEM-Inhalten hinzugefügt. Es gibt jedoch Fälle, in denen der Inhalt noch nicht in AEM erstellt wurde, der jedoch später vom Inhaltsautor hinzugefügt werden muss. Um dies zu ermöglichen, kann der Front-End-Entwickler Komponenten an den entsprechenden Stellen in der SPA hinzufügen. Diese Komponenten zeigen Platzhalter an, wenn sie im Editor in AEM geöffnet werden. Sobald der Inhalt innerhalb dieser Platzhalter vom Inhaltsautor hinzugefügt wurde, werden Knoten in der JCR-Struktur erstellt und der Inhalt bleibt erhalten. Die erstellte Komponente ermöglicht dieselben Vorgänge wie die eigenständigen Blattkomponenten.

In diesem Beispiel verwenden wir die zuvor erstellte `AEMText`-Komponente erneut. Wir möchten auf der WKND-Startseite einen neuen Text unterhalb der bestehenden Textkomponente hinzufügen. Das Hinzufügen von Komponenten ist dasselbe wie bei normalen Blattkomponenten. `itemPath` kann jedoch auf den Pfad aktualisiert werden, in dem die neue Komponente hinzugefügt werden muss.

Da die neue Komponente unter dem vorhandenen Text unter `root/responsivegrid/text` hinzugefügt werden muss, lautet der neue Pfad `root/responsivegrid/{itemName}`.

```html
<AEMText
 pagePath='/content/wknd-spa-react/us/en/home'
 itemPath='root/responsivegrid/text_20' />
```

Die Komponente `TestPage` sieht nach dem Hinzufügen der virtuellen Komponente wie folgt aus.

![Testen der virtuellen Komponente](assets/external-spa-virtual-component.png)

>[!NOTE]
>
>Stellen Sie sicher, dass die Komponente `AEMText` in der Konfiguration ihre `resourceType`-Eigenschaft eingestellt hat, um diese Funktion zu aktivieren.

Sie können jetzt die Änderungen an AEM entsprechend den Schritten im folgenden Abschnitt bereitstellen: [Überprüfen der Bearbeitung von Textinhalten in AEM.](#verify-text-edit) Für den derzeit nicht vorhandenen `text_20`-Knoten wird ein Platzhalter angezeigt.

![Der text_20-Knoten in AEM](assets/external-spa-text20-aem.png)

Wenn der Inhaltsautor diese Komponente aktualisiert, wird unter `root/responsivegrid/text_20` in `/content/wknd-spa-react/us/en/home` ein neuer `text_20`-Knoten erstellt.

![Der text20-Knoten](assets/external-spa-text20-node.png)

#### Anforderungen und Einschränkungen {#limitations}

Es gibt eine Reihe von Anforderungen beim Hinzufügen von Komponenten für virtuelle Blätter sowie einige Einschränkungen.

* Die `pagePath`-Eigenschaft ist zum Erstellen einer virtuellen Komponente obligatorisch.
* Der im Pfad in `pagePath` angegebene Seitenknoten muss im AEM-Projekt vorhanden sein.
* Der Name des zu erstellenden Knotens muss im `itemPath` angegeben werden.
* Die Komponente kann auf jeder Ebene erstellt werden.
   * Wenn wir im vorherigen Beispiel `itemPath='text_20'` angeben, wird der neue Knoten direkt unter der Seite erstellt, d.h. `/content/wknd-spa-react/us/en/home/jcr:content/text_20`
* Der Pfad zum Knoten, in dem ein neuer Knoten erstellt wird, muss gültig sein, wenn er über `itemPath` bereitgestellt wird.
   * In diesem Beispiel muss `root/responsivegrid` vorhanden sein, damit der neue Knoten `text_20` dort erstellt werden kann.
* Es wird nur die Erstellung von Blattkomponenten unterstützt. Virtuelle Container und Seiten werden in zukünftigen Versionen unterstützt.

## Zusätzliche Anpassungen {#additional-customizations}

Wenn Sie den vorherigen Beispielen gefolgt sind, kann Ihre externe SPA jetzt in AEM bearbeitet werden. Es gibt jedoch zusätzliche Aspekte Ihrer externen SPA, die Sie weiter anpassen können.

### Stammknoten-ID {#root-node-id}

Standardmäßig wird davon ausgegangen, dass das React-Programm innerhalb einer `div` der Element-ID `spa-root` gerendert wird. Bei Bedarf können Sie dies anpassen.

Nehmen wir beispielsweise an, wir haben eine SPA, in der das Programm innerhalb einer `div` der Element-ID `root` gerendert wird. Dies muss in drei Dateien widergespiegelt werden.

1. Im `index.js` der React-Programm (oder wo `ReactDOM.render()` aufgerufen wird)

   ![ReactDOM.render() in der index.js](assets/external-spa-root-index.png)

1. In der `index.html` des React-Programms

   ![index.html des Programms](assets/external-spa-index.png)

1. Führen Sie im Hauptteil der Seitenkomponente der AEM-App zwei Schritte aus:

   1. Erstellen Sie ein neue Datei `body.html` für die Seitenkomponente.

   ![Eine neue body.html-Datei erstellen](assets/external-spa-update-body.gif)

   1. Fügen Sie das neue Stammelement in der neuen `body.html`-Datei hinzu.

   ![Stammelement zu body.html hinzufügen](assets/external-spa-add-root.png)

### Bearbeiten einer React-SPA mit Routing {#editing-react-spa-with-routing}

Wenn das externe React-SPA-Programm über mehrere Seiten verfügt, kann [sie mithilfe von Routing die zu rendernde Seite/Komponente bestimmen.](spa-routing.md) Der grundlegende Anwendungsfall ist der Abgleich der aktuell aktiven URL mit dem für eine Route bereitgestellten Pfad. Um die Bearbeitung in solchen Routing-fähigen Programmen zu ermöglichen, muss der Pfad, gegen den abgeglichen werden soll, transformiert werden, damit AEM-spezifische Informationen aufgenommen werden können.

Im folgenden Beispiel haben wir ein einfaches React-Programm mit zwei Seiten. Die Seite, die gerendert werden soll, wird durch den Abgleich des an den Router übergebenen Pfads mit der aktiven URL bestimmt. Wenn wir uns zum Beispiel auf `mydomain.com/test` befinden, wird `TestPage` gerendert.

![Routing in einer externen SPA](assets/external-spa-routing.png)

Um die Bearbeitung in AEM für diese Beispiel-SPA zu aktivieren, sind die folgenden Schritte erforderlich.

1. Identifizieren Sie die Ebene, die als Stamm in AEM fungieren würde.

   * Für unser Beispiel betrachten wir `wknd-spa-react/us/en` als die Wurzel der SPA. Das bedeutet, dass alles vor diesem Pfad nur AEM-Seiten/-Inhalte sind.

1. Erstellen Sie eine neue Seite auf der erforderlichen Ebene.

   * In diesem Beispiel lautet die zu bearbeitende Seite `mydomain.com/test`. `test` befindet sich im Stammpfad der App. Dies muss auch beim Erstellen der Seite in AEM beibehalten werden. Daher können wir eine neue Seite auf der im vorherigen Schritt definierten Stammebene erstellen.
   * Die neu erstellte Seite muss denselben Namen haben wie die zu bearbeitende Seite. In diesem Beispiel für `mydomain.com/test` muss die neue Seite `/path/to/aem/root/test` heißen.

1. Fügen Sie Helfer innerhalb des SPA-Routings hinzu.

   * Die neu erstellte Seite wird noch nicht mit dem erwarteten Inhalt in AEM gerendert. Dies liegt daran, dass der Router den Pfad `/test` erwartet, während der aktive Pfad in AEM `/wknd-spa-react/us/en/test` ist. Um den AEM-spezifischen Teil der URL aufzunehmen, müssen wir einige Helfer auf der SPA Seite hinzufügen.

   ![Routing-Helfer](assets/external-spa-router-helper.png)

   * Hierfür kann der `toAEMPath`-Helfer verwendet werden, der von `@adobe/cq-spa-page-model-manager` bereitgestellt wird. Er wandelt den für das Routing bereitgestellten Pfad so um, dass er AEM-spezifische Teile enthält, wenn das Programm auf einer AEM-Instanz geöffnet ist. Es werden drei Parameter akzeptiert:
      * Der für das Routing erforderliche Pfad
      * Die ursprüngliche URL der AEM-Instanz, in der die SPA bearbeitet wird
      * Das Projektstammverzeichnis in AEM, wie im ersten Schritt festgelegt
   * Diese Werte können für mehr Flexibilität als Umgebungsvariablen festgelegt werden.



1. Überprüfen Sie die Bearbeitung der Seite in AEM.

   * Stellen Sie das Projekt in AEM bereit und navigieren Sie zur neu erstellten `test`-Seite. Der Seiteninhalt wird jetzt gerendert und die AEM-Komponenten können bearbeitet werden.

## Zusätzliche Ressourcen {#additional-resources}

Das folgende Referenzmaterial kann hilfreich sein, um SPAs im Kontext der AEM zu verstehen.

* [AEM-Projekt-Archetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)
* [WKND-SPA-Projekt](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=de)
* [Erste Schritte mit SPAs in AEM unter Verwendung von React](spa-getting-started-react.md)
* [SPA-Referenzmaterialien (API-Referenzen)](spa-reference-materials.md)
* [SPA-Blueprint und PageModelManager](spa-blueprint.md#pagemodelmanager)
* [SPA-Modell-Routing ](spa-routing.md)
* [Single Page Applications (SPAs) und Server-seitiges Rendering ](spa-ssr.md)
