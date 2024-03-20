---
title: Editor-Einschränkungen
description: Der Editor in der Touch-optimierten Benutzeroberfläche verwendet Überlagerungen, um mit Inhalten zu interagieren, die in einem iframe enthalten sind. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
exl-id: fd64f5dc-dfff-466b-8cdd-3c24ea1a15c8
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 59%

---

# Editor-Einschränkungen{#editor-limitations}

Der Editor in der Touch-optimierten Benutzeroberfläche verwendet Überlagerungen, um mit Inhalten zu interagieren, die in einem iframe enthalten sind. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler. Diese Seite fasst diese Einschränkungen zusammen und bietet nach Möglichkeit Lösungen oder Umgehungen.

## Funktionale Einschränkungen {#functional-limitations}

Autoren sehen sich bei der Arbeit mit dem Editor zur Bearbeitung von Seiten möglicherweise mit den folgenden funktionalen Einschränkungen konfrontiert.

### Links nicht aktiv {#links-not-active}

Beim [Bearbeiten einer Seite](/help/sites-authoring/editing-content.md) sind Links nicht aktiv.

* [Wechseln Sie in den Modus **Vorschau**](/help/sites-authoring/editing-content.md#preview-mode), um anhand der Links in den Inhalten zu navigieren.

### Strukturseiten {#structure-pages}

Seiten können nicht benannt werden `structure`. Seiten, die `structure` im Seiteneditor nicht bearbeitbar sind.

## CSS-Einschränkungen {#css-limitations}

Entwickler sehen sich hinsichtlich der Interaktionen des Editors mit CSS möglicherweise mit den folgenden Einschränkungen konfrontiert.

### Absolut positionierte Elemente {#absolutely-positioned-elements}

Absolut positionierte Elemente können Probleme bei der Position ihrer Überlagerung verursachen.

* Stellen Sie in diesem Fall sicher, dass die Dimensionen des absolut positionierten Elements korrekt sind, da der Editor eine Überlagerung mit exakt denselben Dimensionen erstellt.

### vh-Einheiten {#vh-units}

`vh` -Einheiten werden nicht unterstützt, da die iframe-Höhe automatisch von Adobe Experience Manager (AEM) angepasst werden muss.

### Feste Hintergrundbilder {#fixed-background-images}

Feste Hintergrundbilder werden beim Scrollen möglicherweise nicht als fest angezeigt, da sie in einen iframe eingebettet sind.

* Wird in der Kopfzeile **Seite als veröffentlicht anzeigen** ausgewählt, wird die Seite korrekt angezeigt.

### 100 % Höhe {#height}

100 % Höhe wird im Hauptteilelement einer Seite nicht unterstützt.

* Eine Problemumgehung ist möglich, einen Vollbildtext zu implementieren, indem das Textelement wie folgt &quot;gestreckt&quot;wird:

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Ausblenden des Seitenrands {#margin-collapsing}

Probleme beim Ausblenden des Seitenrands treten auf, wenn das erste untergeordnete Element des Hauptteilelements einen Seitenrand aufweist.

* Die Lösung besteht darin, auf Ebene des Hauptteilelements einen Clearfix wie folgt einzufügen:

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
