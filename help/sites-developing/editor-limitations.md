---
title: Editor-Einschränkungen
seo-title: Editor-Einschränkungen
description: Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit dem Inhalt eines iframe zu interagieren. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler.
seo-description: Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit dem Inhalt eines iframe zu interagieren. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler.
uuid: ff524530-3f3a-4c5b-9f94-4aa9aeb9d461
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
discoiquuid: d748decb-a614-4c9e-a502-d6176b720f1a
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Editor-Einschränkungen{#editor-limitations}

Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit dem Inhalt eines iframe zu interagieren. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler. Auf dieser Seite werden diese Einschränkungen zusammengefasst und, wo möglich, Lösungen bzw. Problemumgehungen zur Verfügung gestellt.

## Funktionale Einschränkungen {#functional-limitations}

Autoren sehen sich bei der Arbeit mit dem Editor zur Bearbeitung von Seiten möglicherweise mit den folgenden funktionalen Einschränkungen konfrontiert.

### Links nicht aktiv {#links-not-active}

When [editing a page](/help/sites-authoring/editing-content.md), links are not active.

* [Wechseln Sie zum **Vorschaumodus**](/help/sites-authoring/editing-content.md#preview-mode) , um mithilfe der Links in Ihrem Inhalt zu navigieren.

## CSS-Einschränkungen {#css-limitations}

Entwickler sehen sich hinsichtlich der Interaktionen des Editors mit CSS möglicherweise mit den folgenden Einschränkungen konfrontiert.

### Absolut positionierte Elemente {#absolutely-positioned-elements}

Absolut positionierte Elemente können Probleme bei der Positionierung ihrer Überlagerung verursachen.

* Ist dies der Fall, müssen Sie darauf achten, dass die Abmessungen des absolut positionierten Elements korrekt sind, weil der Editor eine Überlagerung mit den gleichen Abmessungen erstellt.

### vh-Einheiten {#vh-units}

`vh` Einheiten werden nicht unterstützt, da die iframe-Höhe automatisch von AEM angepasst werden muss.

### Feste Hintergrundbilder {#fixed-background-images}

Feste Hintergrundbilder werden beim Scrollen nicht als fest angezeigt, weil sie in einen iframe eingebettet sind.

* Selecting **View Page as Published** in the header bar actions displays the page properly.

### 100 % Höhe {#height}

100 % Höhe wird im Hauptteilelement einer Seite nicht unterstützt.

* Eine Umgehung ist möglich, um einen Vollbildkörper zu implementieren, indem das Textelement wie folgt &quot;gestreckt&quot;wird:

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

