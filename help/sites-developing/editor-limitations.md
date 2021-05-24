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
exl-id: fd64f5dc-dfff-466b-8cdd-3c24ea1a15c8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 94%

---

# Editor-Einschränkungen{#editor-limitations}

Der Editor in der Touch-optimierten Benutzeroberfläche nutzt Überlagerungen, um mit dem Inhalt eines iframe zu interagieren. Diese Interaktion verursacht einige Einschränkungen für die Verwendung des Editors sowie für Entwickler. Auf dieser Seite werden diese Einschränkungen zusammengefasst und, wo möglich, Lösungen bzw. Problemumgehungen zur Verfügung gestellt.

## Funktionale Einschränkungen   {#functional-limitations}

Autoren sehen sich bei der Arbeit mit dem Editor zur Bearbeitung von Seiten möglicherweise mit den folgenden funktionalen Einschränkungen konfrontiert.

### Links nicht aktiv   {#links-not-active}

Beim [Bearbeiten einer Seite](/help/sites-authoring/editing-content.md) sind Links nicht aktiv.

* [Wechseln Sie in den Modus **Vorschau**](/help/sites-authoring/editing-content.md#preview-mode), um anhand der Links in den Inhalten zu navigieren.

### Strukturseiten {#structure-pages}

Seiten dürfen nicht `structure` genannt werden. Seiten mit dem Namen `structure` können im Seiteneditor nicht bearbeitet werden.

## CSS-Einschränkungen {#css-limitations}

Entwickler sehen sich hinsichtlich der Interaktionen des Editors mit CSS möglicherweise mit den folgenden Einschränkungen konfrontiert.

### Absolut positionierte Elemente   {#absolutely-positioned-elements}

Absolut positionierte Elemente können Probleme bei der Positionierung ihrer Überlagerung verursachen.

* Ist dies der Fall, müssen Sie darauf achten, dass die Abmessungen des absolut positionierten Elements korrekt sind, weil der Editor eine Überlagerung mit den gleichen Abmessungen erstellt.

### vh-Einheiten   {#vh-units}

`vh`-Einheiten werden nicht unterstützt, da die iframe-Höhe von AEM automatisch angepasst werden muss.

### Feste Hintergrundbilder {#fixed-background-images}

Feste Hintergrundbilder werden beim Scrollen nicht als fest angezeigt, weil sie in einen iframe eingebettet sind.

* Wird in der Kopfzeile **Seite als veröffentlicht anzeigen** ausgewählt, wird die Seite korrekt angezeigt.

### 100 % Höhe {#height}

100 % Höhe wird im Hauptteilelement einer Seite nicht unterstützt.

* Eine Umgehung ist möglich, um einen Vollbildtext zu implementieren, indem das Hauptteilelement wie folgt &quot;gestreckt&quot;wird:

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
