---
title: Composite-Komponenten in SPA
description: Erfahren Sie, wie Sie Ihre eigenen Composite-Komponenten erstellen, Komponenten, die aus anderen Komponenten bestehen und mit dem AEM Single-Page Application (SPA) Editor arbeiten.
translation-type: tm+mt
source-git-commit: 431bed450ed5b0239d9191dcf061f01e64b8981a
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Composite-Komponenten in SPA {#composite-components-in-spas}

Composite-Komponenten nutzen den modularen Charakter AEM Komponenten, indem sie mehrere Basiskomponenten zu einer einzigen Komponente kombinieren. Ein gängiges Composite-Komponenten-Anwendungsbeispiel ist die Kartenkomponente, die aus einer Kombination der Bild- und Textkomponenten besteht.

Wenn Composite-Komponenten ordnungsgemäß im AEM Single Page Application (SPA) Editor-Framework implementiert sind, können die Inhaltsersteller die Komponenten wie jede andere Komponente per Drag &amp; Drop verschieben. Sie haben jedoch weiterhin die Möglichkeit, die einzelnen Komponenten, aus denen die Composite-Komponente besteht, einzeln zu bearbeiten.

Dieser Artikel zeigt, wie Sie eine Composite-Komponente zu Ihrer Einzelseitenanwendung hinzufügen können, um nahtlos mit dem AEM SPA Editor zu arbeiten.

## Nutzungsszenario  {#use-case}

In diesem Artikel wird die typische Kartenkomponente als Anwendungsbeispiel verwendet. Karten sind für viele digitale Erlebnisse ein gemeinsames Element der Benutzeroberfläche und bestehen normalerweise aus einem Bild und einem zugehörigen Text oder einer zugehörigen Beschriftung. Ein Autor möchte die gesamte Karte per Drag &amp; Drop verschieben, aber das Kartenbild einzeln bearbeiten und den zugehörigen Text anpassen können.

## Voraussetzungen {#prerequisites}

Die folgenden Modelle zur Unterstützung der Anwendungsfälle von Composite-Komponenten erfordern die folgenden Voraussetzungen.

* Ihre AEM Entwicklungsinstanz wird lokal an Port 4502 mit einem Beispielprojekt ausgeführt.
* Sie haben eine funktionierende externe React-App [aktiviert, die in AEM bearbeitet werden kann.](spa-edit-external.md)
* Die React-App wird mithilfe der RemotePage-Komponente im AEM-Editor [geladen.](spa-remote-page.md)

## Hinzufügen von Composite-Komponenten zu einer SPA {#adding-composite-components}

Es gibt drei verschiedene Modelle für die Implementierung der Composite-Komponente, je nach Ihrer SPA Implementierung in AEM.

* [Die Komponente ist in Ihrem AEM Projekt nicht vorhanden.](#component-does-not-exist)
* [Die Komponente ist in Ihrem AEM Projekt vorhanden, der erforderliche Inhalt jedoch nicht.](#content-does-not-exist)
* [Die Komponente und der erforderliche Inhalt sind beide in Ihrem AEM Projekt vorhanden.](#both-exist)

Die folgenden Abschnitte zeigen Beispiele für die Implementierung der einzelnen Fälle mit der Kartenkomponente als Beispiel.

### Die Komponente ist in Ihrem AEM Projekt nicht vorhanden. {#component-does-not-exist}

Beginn durch Erstellen der Komponenten, aus denen die Composite-Komponente besteht, d. h. der Bildkomponenten und des Textes.

1. Erstellen Sie die Textkomponente in Ihrem AEM Projekt.
1. hinzufügen Sie die entsprechende `resourceType` aus dem Projekt im Knoten `editConfig` der Komponente.

   ```text
    resourceType: 'wknd-spa/components/text' 
   ```

1. Verwenden Sie den Helfer `withMappable`, um die Bearbeitung für die Komponente zu aktivieren.

   ```text
   export const AEMText = withMappable(Text, TextEditConfig); 
   ```

Die Textkomponente ähnelt der folgenden.

```javascript
import React from 'react';
import { withMappable } from '@adobe/aem-react-editable-components';

export const TextEditConfig = {
  emptyLabel: 'Text',
  isEmpty: function(props) {
    return !props || !props.text || props.text.trim().length < 1;
  },
  resourceType: 'wknd-spa/components/text'
};

export const Text = ({ cqPath, richText, text }) => {
  const richTextContent = () => (
    <div className="aem_text"
      id={cqPath.substr(cqPath.lastIndexOf('/') + 1)}
      data-rte-editelement
      dangerouslySetInnerHTML={{__html: text}} />
  );
  return richText ? richTextContent() : (
     <div className="aem_text">{text}</div>
  );
};

export const AEMText = withMappable(Text, TextEditConfig);
```

Wenn Sie eine Bildkomponente auf ähnliche Weise erstellen, können Sie sie dann mit der Komponente `AEMText` zu einer neuen Kartenkomponente kombinieren und die Bild- und Textkomponenten als untergeordnete Elemente verwenden.

```javascript
import React from 'react';
import { AEMText } from './AEMText';
import { AEMImage } from './AEMImage';

export const AEMCard = ({ pagePath, itemPath}) => (
  <div>
    <AEMText
       pagePath={pagePath}
       itemPath={`text`} />
    <AEMImage
       pagePath={pagePath}
       itemPath={`image`} />
   </div>
);
```

Diese resultierende Composite-Komponente kann nun an einer beliebigen Stelle in der App platziert werden. Im SPA Editor werden Platzhalter für einen Text und eine Bildkomponente hinzugefügt. Im folgenden Beispiel wird die Kartenkomponente der Startseite unter dem Titel hinzugefügt.

```javascript
function Home() {
  return (
    <div className="Home">
      <h2>Current Adventures</h2>
      <AEMCard
        pagePath='/content/wknd-spa/home' />
    </div>
  );
}
```

Dadurch wird ein leerer Platzhalter für einen Text und ein Bild im Editor angezeigt. Beim Eingeben von Werten für diese mithilfe des Editors werden sie auf dem angegebenen Seitenpfad gespeichert, d. h. `/content/wknd-spa/home` auf der Stammebene mit den unter `itemPath` angegebenen Namen.

![Komponente der Composite-Karte im Editor](assets/composite-card.png)

### Die Komponente ist in Ihrem AEM Projekt vorhanden, der erforderliche Inhalt jedoch nicht. {#content-does-not-exist}

In diesem Fall wird die Kartenkomponente bereits in Ihrem AEM Projekt erstellt, das Titel- und Bildknoten enthält. Die untergeordneten Knoten (Text und Bild) haben die entsprechenden Ressourcentypen.

![Knotenstruktur der Kartenkomponente](assets/composite-node-structure.png)

Sie können es dann zu Ihrer SPA hinzufügen und den Inhalt abrufen.

1. Erstellen Sie eine entsprechende Komponente in der SPA für diese Komponente. Stellen Sie sicher, dass die untergeordneten Komponenten den entsprechenden AEM Ressourcentypen im SPA Projekt zugeordnet sind. In diesem Beispiel verwenden wir die gleichen Komponenten wie `AEMText` und `AEMImage` wie im vorherigen Fall [detailliert.](#component-does-not-exist)

   ```javascript
   import React from 'react';
   import { Container, withMappable, MapTo } from '@adobe/aem-react-editable-components';
   import { Text, TextEditConfig } from './AEMText';
   import Image, { ImageEditConfig } from './AEMImage';
   
   export const AEMCard = withMappable(Container, {
     resourceType: 'wknd-spa/components/imagecard'
   });
   
   MapTo('wknd-spa/components/text')(Text, TextEditConfig);
   MapTo('wknd-spa/components/image')(Image, ImageEditConfig);
   ```

1. Da für die Komponente `imagecard` kein Inhalt vorhanden ist, fügen Sie die Karte der Seite hinzu. Schließen Sie den vorhandenen Container aus AEM in den SPA ein.
   * Wenn bereits ein Container im AEM vorhanden ist, können wir ihn stattdessen in die SPA einbeziehen und die Komponente dem Container aus AEM hinzufügen.
   * Stellen Sie sicher, dass die Kartenkomponente dem entsprechenden Ressourcentyp im SPA zugeordnet ist.

   ```javascript
   <ResponsiveGrid
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid' />
   ```

1. hinzufügen die erstellte Komponente `wknd-spa/components/imagecard` den zulässigen Komponenten für die Container-Komponente [in der Seitenvorlage.](/help/sites-authoring/templates.md)

Jetzt kann die Komponente `imagecard` direkt zum Container im AEM Editor hinzugefügt werden.

![Composite-Karte im Editor](assets/composite-card.gif)

### Die Komponente und der erforderliche Inhalt sind beide in Ihrem AEM Projekt vorhanden. {#both-exist}

Wenn der Inhalt in AEM vorhanden ist, kann er direkt in die SPA einbezogen werden, indem der Pfad zum Inhalt angegeben wird.

```javascript
<AEMCard
    pagePath='/content/wknd-spa/home'
    itemPath='root/responsivegrid/imagecard' />
```

![Composite-Pfad in der Knotenstruktur](assets/composite-path.png)

Die `AEMCard`-Komponente entspricht der Definition [im vorherigen Anwendungsfall.](#content-does-not-exist) Hier ist der im obigen Verzeichnis im AEM Projekt definierte Inhalt in der SPA enthalten.
