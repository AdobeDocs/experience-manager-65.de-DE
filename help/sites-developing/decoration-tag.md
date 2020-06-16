---
title: Decoration-Tag
description: Wenn eine Komponente einer Webseite gerendert wird, kann ein HTML-Element generiert werden, das die gerenderte Komponente in sich einschließt. Für Entwickler bietet AEM eine klare und einfache Logik für die Steuerung von Decoration-Tags, die enthaltene Komponenten einschließen.
translation-type: tm+mt
source-git-commit: be1c0e21216b1014a36f88d13557f6e1d7a87c0a
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 79%

---


# Decoration-Tag{#decoration-tag}

Wenn eine Komponente einer Webseite gerendert wird, kann ein HTML-Element generiert werden, das die gerenderte Komponente in sich einschließt. Dies dient in erster Linie zwei Zwecken:

* Eine Komponente kann nur bearbeitet werden, wenn sie in einem HTML-Element eingeschlossen ist.
* Das einschließende Element wird verwendet, um HTML-Klassen anzuwenden, die Folgendes bieten:

   * Layoutinformationen
   * Styling-Informationen

Für Entwickler bietet AEM eine klare und einfache Logik für die Steuerung von Decoration-Tags, die enthaltene Komponenten einschließen. Ob und wie das Decoration-Tag gerendert wird, hängt von zwei Faktoren ab, die auf dieser Seite genauer erläutert werden:

* Die Komponenten selbst können ihr Decoration-Tag mit einer Gruppe von Eigenschaften konfigurieren.
* Die Skripte, die Komponenten enthalten (HTL, JSP, Dispatcher usw.) können die Eigenschaften des Decoration-Tags mit include-Parametern definieren.

## Empfehlungen {#recommendations}

Es folgen einige allgemeine Empfehlungen, wann Sie ein einschließendes Element verwenden sollten, um unerwartete Probleme zu vermeiden:

* Das einschließende Element sollte unabhängig von WCMModes (Bearbeitungs- oder Vorschaumodus), Instanzen (Autor oder Veröffentlichung) oder Umgebung (Staging oder Produktion) vorhanden bzw. nicht vorhanden sein, damit der CSS- und JavaScript-Code der Seite stets gleich funktionieren.
* Das einschließende Element sollte allen bearbeitbaren Komponenten hinzugefügt werden, sodass der Seiten-Editor sie korrekt initialisieren und aktualisieren kann.
* Bei nicht bearbeitbaren Komponenten kann das einschließende Element weggelassen werden, wenn es keinen bestimmten Zweck erfüllt, um das Markup nicht unnötig zu vergrößern.

## Komponentensteuerung {#component-controls}

Die folgenden Eigenschaften und Knoten können auf Komponenten angewendet werden, um das Verhalten ihrer Decoration-Tags zu steuern:

* **`cq:noDecoration {boolean}`:**Diese Eigenschaft kann einer Komponente hinzugefügt werden. Wenn der Wert „true“ lautet, darf AEM keine einschließenden Elemente für die Komponente generieren.

* **`cq:htmlTag`node :**Dieser Knoten kann unter einer Komponente hinzugefügt werden und die folgenden Eigenschaften aufweisen:

   * **`cq:tagName {String}`:**Damit können Sie ein eigenes HTML-Tag angeben, das die Komponenten anstatt des standardmäßigen DIV-Elements einschließen soll.
   * **`class {String}`:**Damit können Sie css-Klassennamen angeben, die dem einschließenden Element hinzugefügt werden sollen.
   * Andere Eigenschaftsnamen werden als HTML-Attribute mit demselben angegebenen String-Wert hinzugefügt.

## Skript-Steuerung {#script-controls}

The wrapper behavior does differ however depending on if [HTL](/help/sites-developing/decoration-tag.md#htl) or [JSP](/help/sites-developing/decoration-tag.md#jsp) is used to include the element.

### HTL {#htl}

Im Allgemeinen lässt sich das Wrapper-Verhalten in HTL wie folgt beschreiben:

* No wrapper DIV is rendered by default (when just doing `data-sly-resource="foo"`).
* Alle wcm-Modi (deaktiviert, Vorschau, Bearbeiten für Autor oder Veröffentlichung) werden identisch dargestellt.

Das Verhalten des Wrappers kann auch vollständig kontrolliert werden.

* Das HTL-Skript hat die vollständige Kontrolle über das resultierende Verhalten des Wrapper-Tags.
* Component properties (like `cq:noDecoration` and `cq:tagName`) can also define the wrapper tag.

Sie können das Verhalten der Wrapper-Tags von HTL-Skripten und der zugehörigen Logik vollständig kontrollieren.

For further information about developing in HTL see the [HTL documentation](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html).

#### Entscheidungsbaum {#decision-tree}

Dieser Entscheidungsbaum fasst die Logik zusammen, die das Verhalten der Wrapper-Tags bestimmt.

![chlimage_1-75](assets/chlimage_1-75a.png)

#### Nutzungsszenarien {#use-cases}

Die folgenden drei Anwendungsfälle stellen Beispiele dafür dar, wie die Wrapper-Tags behandelt werden, und zeigen außerdem, wie einfach es ist, das gewünschte Verhalten der Wrapper-Tags zu steuern.

In allen Beispielen werden die folgende Inhaltsstruktur und die folgenden Komponenten angenommen:

```
/content/test/
  @resourceType = "test/components/one"
  child/
    @resourceType = "test/components/two"
```

```
/apps/test/components/
  one/
    one.html
  two/
    two.html
    cq:htmlTag/
      @cq:tagName = "article"
      @class = "component-two"
```

#### Anwendungsfall 1: Einfügen einer Komponente zur Wiederverwendung von Code {#use-case-include-a-component-for-code-reuse}

Der häufigste Anwendungsfall besteht darin, dass eine Komponente eine andere Komponente enthält, damit Code erneut verwendet werden kann. In diesem Fall soll die enthaltene Komponente nicht mit ihrer eigenen Symbolleiste und ihrem eigenen Dialogfeld bearbeitbar sein, sodass kein Wrapper notwendig ist. Das `cq:htmlTag` der Komponente wird ignoriert. Dies gilt als das Standardverhalten.

`one.html: <sly data-sly-resource="child"></sly>`

`two.html: Hello World!`

Ergebnisausgabe am `/content/test.html`:

**`Hello World!`**

Ein Beispiel wäre eine Komponente, die eine Core-Image-Komponente enthält, um ein Bild anzuzeigen. In diesem Fall wird in der Regel eine synthetische Ressource verwendet, die darin besteht, eine virtuelle untergeordnete Komponente einzuschließen, indem ein Map-Objekt, das alle Eigenschaften darstellt, die die Komponente hätte.

#### Anwendungsfall 2: Eine bearbeitbare Komponente einfügen {#use-case-include-an-editable-component}

Bei einem weiteren häufigen Anwendungsfall enthalten Containerkomponenten bearbeitbare untergeordnete Komponenten z. B. einen Layout-Container. In diesem Fall benötigt jedes enthaltene untergeordnete Element einen Wrapper, damit der Editor funktioniert (es sei denn, dies ist explizit mit der Eigenschaft `cq:noDecoration` deaktiviert).

Da die eingefügte Komponente in diesem Fall eine unabhängige Komponente ist, benötigt sie ein Wrapper-Element, damit der Editor funktioniert und um Layout und Style anzuwenden. To trigger this behavior, there&#39;s the `decoration=true` option.

`one.html: <sly data-sly-resource="${'child' @ decoration=true}"></sly>`

`two.html: Hello World!`

Ergebnisausgabe am `/content/test.html`:

**`<article class="component-two">Hello World!</article>`**

#### Anwendungsfall 3: Benutzerdefiniertes Verhalten {#use-case-custom-behavior}

Es sind unendlich viele komplexe Anwendungsfälle möglich, die einfach umgesetzt werden können, indem HTL Folgendes explizit angibt:

* **`decorationTagName='ELEMENT_NAME'`** So definieren Sie den Elementnamen des Wrapper.
* **`cssClassName='CLASS_NAME'`** So definieren Sie die CSS-Klassennamen, die darauf eingestellt werden sollen.

`one.html: <sly data-sly-resource="${'child' @ decorationTagName='aside', cssClassName='child'}"></sly>`

`two.html: Hello World!`

Ergebnis `/content/test.html`:

**`<aside class="child">Hello World!</aside>`**

## JSP {#jsp}

When including a component using `cq:includ`e or `sling:include`, the default behavior in AEM is to use a DIV to wrap the element. Sie können dieses Verhalten jedoch auf zwei Arten anpassen:

* Geben Sie mit `cq:noDecoration` explizit an, dass AEM die Komponente nicht einschließen soll.
* Use a custom HTML tag to wrap the component using `cq:htmlTag`/ `cq:tagName` or `decorationTagName`.

### Entscheidungsbaum {#decision-tree-1}

The following decision tree illustrates how `cq:noDecoration`, `cq:htmlTag`, `cq:tagName`, and `decorationTagName` affect the wrapper behavior.

![chlimage_1-3](assets/chlimage_1-3a.jpeg)

