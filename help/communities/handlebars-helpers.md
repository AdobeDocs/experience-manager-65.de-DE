---
title: SCF Handlebars-Helfer
description: Handlebars-Hilfsmethoden zur Erleichterung der Arbeit mit SCF
topic-tags: developing
content-type: reference
exl-id: bfb95cae-4b0f-4521-a113-042dc4005a63
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1445'
ht-degree: 4%

---

# SCF Handlebars-Helfer {#scf-handlebars-helpers}

| **[⇐ Feature Essentials](essentials.md)** | **[Server-seitige ⇒](server-customize.md)** |
|---|---|
|   | **[Client-seitige ⇒](client-customize.md)** |

Handlebars-Helfer (Helper) sind Methoden, die von Handlebars-Skripten aus aufgerufen werden können, um die Arbeit mit SCF-Komponenten zu erleichtern.

Die Implementierung umfasst eine Client- und eine Server-seitige Definition. Es ist auch möglich, dass Entwicklerinnen und Entwickler benutzerdefinierte Helper erstellen.

Die benutzerdefinierten SCF-Helper, die mit AEM Communities bereitgestellt werden, sind in der [Client-Bibliothek](../../help/sites-developing/clientlibs.md) definiert:

* `/etc/clientlibs/social/commons/scf/helpers.js`

>[!NOTE]
>
>Installieren Sie unbedingt das [neueste Communities Feature Pack](deploy-communities.md#latestfeaturepack).

## kürzen {#abbreviate}

Ein Helper zum Zurückgeben einer abgekürzten Zeichenfolge, die den Eigenschaften maxWords und maxLength entspricht.

Die Zeichenfolge, die abgekürzt werden soll, wird als Kontext bereitgestellt. Wenn kein Kontext angegeben wird, wird eine leere Zeichenfolge zurückgegeben.

Zuerst wird der Kontext auf maxLength gekürzt, dann wird der Kontext in Wörter aufgeteilt und auf maxWords reduziert.

Wenn safeString auf „true“ gesetzt ist, dann ist die zurückgegebene Zeichenfolge ein SafeString.

### Parameter {#parameters}

* **context**: Zeichenfolge

  (Optional) Standard ist die leere Zeichenfolge

* **maxLength**: Zahl

  (Optional) Standard ist die Länge des Kontexts.

* **maxWords**: Zahl

  (Optional) Der Standardwert ist die Anzahl der Wörter in der gekürzten Zeichenfolge.

* **safeString**: Boolesch

  (Optional) Gibt eine Handlebars.SafeString() zurück, wenn „true“. Der Standardwert ist „false“.

### Beispiele {#examples}

```
{{abbreviate subject maxWords=2}}

/*
If subject =
    "AEM Communities - Site Creation Wizard"

Then abbreviate would return
    "AEM Communities".
*/
```

```
{{{abbreviate message safeString=true maxLength=30}}}

/*
If message =
    "The goal of AEM Communities is to quickly create a community engagement site."

Then abbreviate would return
    "The goal of AEM Communities is"
*/
```

## content-loadmore {#content-loadmore}

Ein Helper zum Hinzufügen von zwei Bereichen unter einem div, einer für den Volltext und einer für den weniger Text, mit der Möglichkeit, zwischen den beiden Ansichten umzuschalten.

### Parameter {#parameters-1}

* **context**: Zeichenfolge

  (Optional) Der Standardwert ist die leere Zeichenfolge.

* **numChars**: Zahl

  (Optional) Die Anzahl der Zeichen, die angezeigt werden, wenn kein Volltext angezeigt wird. Der Standardwert ist 100.

* **moreText**: Zeichenfolge

  (Optional) Der anzuzeigende Text, der angibt, dass mehr Text angezeigt werden soll. Der Standardwert ist „more“.

* **ellipsesText**: Zeichenfolge

  (Optional) Der anzuzeigende Text, der angibt, dass ein ausgeblendeter Text vorhanden ist. Der Standardwert lautet &quot;…“.

* **safeString**: Boolesch

  (Optional) Boolescher Wert, der angibt, ob Handlebars.SafeString() vor der Rückgabe des Ergebnisses angewendet werden soll. Der Standardwert ist „false“.

### Beispiel {#example}

```
{{content-loadmore  context numChars=32  moreText="go on"  ellipsesText="..." }}

/*
If context =
    "Here is the initial less content and this is more content."

Then content-loadmore would return
    "Here is the initial less content<span class="moreelipses">...</span> <span class="scf-morecontent"><span>and this is more content.</span>  <a href="" class="scf-morelink" evt="click=toggleContent">go on</a></span>"
*/
```

## DateUtil {#dateutil}

Ein Helper zum Zurückgeben einer formatierten Datumszeichenfolge.

### Parameter {#parameters-2}

* **context**: number

  (Optional) Ein Millisekundenwert, der ab dem 1. Januar 1970 (Epoche) versetzt wurde. Standard ist das aktuelle Datum.

* **format**: Zeichenfolge

  (Optional) Das anzuwendende Datumsformat. Der Standardwert ist &quot;`YYYY-MM-DDTHH:mm:ss.sssZ`&quot;, und das Ergebnis wird als &quot;`2015-03-18T18:17:13-07:00`&quot; angezeigt.

### Beispiele {#examples-1}

```
{{dateUtil this.memberSince format="dd MMM yyyy, hh:mm"}}

// returns "18 Mar 2015, 18:17"
```

```
{{dateUtil this.birthday format="MM-DD-YYYY"}}

// returns "03-18-2015"
```

## Gleich {#equals}

Ein Helper zum Zurückgeben von Inhalten abhängig von einer bedingten Gleichheit.

### Parameter {#parameters-3}

* **lvalue**: Zeichenfolge

  Der zu vergleichende Wert auf der linken Seite.

* **rvalue**: Zeichenfolge

  Der zu vergleichende Wert auf der rechten Seite.

### Beispiel {#example-1}

```
{{#equals  value "some-value"}}
  <div>They are EQUAL!</div>
`{{else}}`
  <div>They are NOT equal!</div>
{{/equals}}
```

## if-wcm-mode {#if-wcm-mode}

Ein Block-Helper, der den aktuellen Wert von [WCM-Modus](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) anhand einer durch eine Zeichenfolge getrennten Liste von Modi testet.

### Parameter {#parameters-4}

* **context**: Zeichenfolge

  (Optional) Die zu übersetzende Zeichenfolge. Erforderlich, wenn kein Standardwert angegeben wurde.

* **mode**: Zeichenfolge

  (Optional) Eine kommagetrennte Liste von [WCM-Modi](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/WCMMode.html) um zu testen, ob sie festgelegt sind.

### Beispiel {#example-2}

```xml
{{#if-wcm-mode mode="DESIGN, EDIT"}}
 ...
{else}}
 ...
`{{/if-wcm-mode}}`
```

## i18n {#i-n}

Dieser Helper überschreibt den Handlebars-Helper „i18n“.

Siehe auch [Internationalisieren von Zeichenfolgen in JavaScript-Code](../../help/sites-developing/i18n-dev.md#internationalizing-strings-in-javascript-code).

### Parameter {#parameters-5}

* **context**: Zeichenfolge

  (Optional) Die zu übersetzende Zeichenfolge. Erforderlich, wenn kein Standardwert angegeben wurde.

* **default**: Zeichenfolge

  (Optional) Die zu übersetzende Standardzeichenfolge. Erforderlich, wenn kein Kontext angegeben wurde.

* **comment**: Zeichenfolge

  (Optional) Ein Übersetzungshinweis

### Beispiel {#example-3}

```
{{i18n "hello"}}
{{i18n "hello" comment="greeting" default="bonjour"}}
```

## Einschließen {#include}

Ein Helper zum Einschließen einer Komponente als nicht vorhandene Ressource in einer Vorlage.

Mit dieser Methode kann die Ressource programmgesteuert einfacher angepasst werden, als dies für eine Ressource möglich ist, die als JCR-Knoten hinzugefügt wird. Siehe [Hinzufügen oder Einschließen einer Communities-Komponente](scf.md#add-or-include-a-communities-component).

Es stehen nur einige ausgewählte Communities-Komponenten zum Einschließen zur Verfügung. <!-- OBSOLETE/OLD  NEED TO UPDATE FOR 6.5  For AEM 6.1, those that are includable are [comments](essentials-comments.md), [rating](rating-basics.md), [reviews](reviews-basics.md), and [voting](essentials-voting.md). -->

Dieser Helper, der nur für die Serverseite geeignet ist, bietet für JSP-Skripte ähnliche Funktionen [cq:include](../../help/sites-developing/taglib.md).

### Parameter {#parameters-6}

* **context**: Zeichenfolge oder Objekt

  (Optional, sofern kein relativer Pfad angegeben wird)

  Verwenden Sie `this`, um den aktuellen Kontext zu übergeben.

  Verwenden Sie `this.id`, um die Ressource unter `id` für das Rendern des angeforderten resourceType abzurufen.

* **resourceType**: Zeichenfolge

  (Optional) Der Ressourcentyp ist standardmäßig auf den Ressourcentyp aus dem Kontext festgelegt.

* **template**: Zeichenfolge

  Pfad zum Komponentenskript.

* **path**: Zeichenfolge

  (Erforderlich) Der Pfad zur Ressource. Wenn der Pfad relativ ist, muss ein Kontext angegeben werden, andernfalls wird die leere Zeichenfolge zurückgegeben.

* **authoringDisabled**: Boolesch

  (Optional) Der Standardwert ist „false“. Nur zur internen Verwendung.

### Beispiel {#example-4}

```
{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}
```

Beinhaltet eine neue Kommentarkomponente unter `this.id` + /comments.

## includeClientLib {#includeclientlib}

Ein Helper mit einer AEM-HTML-Client-Bibliothek, bei der es sich um eine JS-, CSS- oder Design-Bibliothek handeln kann. Für mehrere Einschlüsse verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals im Handlebars-Skript verwendet werden.

Dieser Helper, der nur für die Serverseite geeignet ist, bietet für JSP[Skripte ähnliche Funktionen wie ui:includeClientLib](../../help/sites-developing/taglib.md).

### Parameter {#parameters-7}

* **categories**: Zeichenfolge

  (Optional) Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Schließen Sie alle JavaScript- und CSS-Bibliotheken für die angegebenen Kategorien ein. Der Designname wird aus der Abfrage extrahiert.

* **theme**: String

  (Optional) Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Schließen Sie alle designbezogenen Bibliotheken (CSS und JS) für die jeweiligen Kategorien ein. Der Designname wird aus der Abfrage extrahiert.

* **js**: Zeichenfolge

  (Optional) Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Umfasst alle JavaScript-Bibliotheken für die angegebenen Kategorien.

* **css**: Zeichenfolge

  (Optional) Eine durch Kommas getrennte Liste der Client-Bibliothekskategorien. Umfasst alle CSS-Bibliotheken für die angegebenen Kategorien.

### Beispiele {#examples-2}

```
// all: js + theme (theme-js + css)
{{includeClientLib categories="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// only js libs
{{includeClientLib js="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/socialgraph.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// theme only (theme-js + css)
{{includeClientLib theme="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
    <script src="/etc/clientlibs/social/hbs/tally/voting.js" type="text/javascript"></script>
    <script src="/etc/clientlibs/social/hbs/comments.js" type="text/javascript"></script>

// css only
{{includeClientLib css="cq.social.hbs.comments, cq.social.hbs.voting"}}

// returns
    <link href="/etc/clientlibs/social/hbs/tally/voting.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/socialgraph.css" rel="stylesheet" type="text/css">
    <link href="/etc/clientlibs/social/hbs/comments.css" rel="stylesheet" type="text/css">
```

## hübsche Zeit {#pretty-time}

Ein Helper, der anzeigt, wie viel Zeit bis zu einem Cutoff-Punkt vergangen ist. Danach wird ein reguläres Datumsformat angezeigt.

Zum Beispiel:

* vor 12 Stunden
* vor 7 Tagen

### Parameter {#parameters-8}

* **context**: number

  Eine Zeit in der Vergangenheit, die mit „jetzt“ verglichen werden kann. Die Zeit wird als Millisekundenwert-Offset vom 1. Januar 1970 (Epoche) angegeben.

* **daysCutoff**: Zahl

  Die Anzahl der Tage vor dem Wechsel zu einem tatsächlichen Datum. Der Standardwert ist 60.

### Beispiel {#example-5}

```
{{pretty-time this.published daysCutoff=7}}

/*
Depending on how long in the past, may return

  "3 minutes ago"

  "3 hours ago"

  "3 days ago"
*/
```

## xss-html {#xss-html}

Ein Helper, der eine Quellzeichenfolge für das HTML von Elementinhalten kodiert, um XSS zu verhindern.

HINWEIS: Dieser Helper ist kein Validator und darf nicht zum Schreiben von Attributwerten verwendet werden.

### Parameter {#parameters-9}

* **context**: Objekt

  Die zu kodierende HTML.

### Beispiel {#example-6}

```
<p>{{xss-html forum-ugc}}</p>
```

## Xss-htmlAttr {#xss-htmlattr}

Ein Helper, der eine Quellzeichenfolge zum Schreiben in einen HTML-Attributwert codiert, um XSS zu verhindern.

HINWEIS: Dieser Helper ist kein Validator und darf nicht zum Schreiben von verwertbaren Attributen (href, src, Ereignis-Handler) verwendet werden.

### Parameter {#parameters-10}

* **context**: Objekt

  Die zu kodierende HTML.

### Beispiel {#example-7}

```
<div id={{xss-htmlAttr id}} />
```

## Xss-jsString {#xss-jsstring}

Ein Helper, der eine Quellzeichenfolge zum Schreiben in JavaScript-Zeichenfolgeninhalte kodiert, um XSS zu verhindern.

HINWEIS: Dieser Helper ist kein Validator und darf nicht zum Schreiben in beliebige JavaScript verwendet werden.

### Parameter {#parameters-11}

* **context**: Objekt

  Die zu kodierende HTML.

### Beispiel {#example-8}

```
var input = {{xss-jsString topic-title}}
```

## Xss-validHref {#xss-validhref}

Ein Helper, der eine URL bereinigt, damit sie als HTML href- oder srce-Attributwert geschrieben wird, um XSS zu verhindern.

HINWEIS: Dieser Helper kann eine leere Zeichenfolge zurückgeben.

### Parameter {#parameters-12}

* **context**: Objekt

  Die zu bereinigende URL.

### Beispiel {#example-9}

```
<a href="{{xss-validHref url}}">my link</a>
```

## Grundlegende Übersicht über Handlebars.js {#handlebars-js-basic-overview}

* Ein Handlebars-Helper-Aufruf ist eine einfache Kennung (*name* des Helpers), gefolgt von null oder mehr durch Leerzeichen getrennten Parametern.
* Parameter können ein einfaches String-, Number-, Boolean- oder JSON-Objekt und eine optionale Sequenz von Schlüssel-Wert-Paaren (Hash-Argumente) als letzte Parameter sein.
* Die Schlüssel in Hash-Argumenten müssen einfache Kennungen sein.
* Die Werte in Hash-Argumenten sind Handlebars-Ausdrücke: einfache Kennungen, Pfade oder Zeichenfolgen.
* Der aktuelle Kontext `this` ist für Handlebars-Helfer immer verfügbar.
* Der Kontext kann eine Zeichenfolge, eine Zahl, ein boolescher Wert oder ein JSON-Datenobjekt sein.
* Es ist möglich, ein im aktuellen Kontext verschachteltes Objekt als Kontext zu übergeben, z. B. `this.url` oder `this.id` (siehe die folgenden Beispiele für einfache und Block-Helper).

* Block-Helper sind Funktionen, die von einer beliebigen Stelle in der Vorlage aufgerufen werden können. Sie können einen Block der Vorlage null oder mehr Mal mit jeweils einem anderen Kontext aufrufen. Sie enthalten einen Kontext zwischen `{{#*name*}}` und `{{/*name*}}`.

* Handlebars stellen einen endgültigen Parameter für Helper mit dem Namen „options“ bereit. Das spezielle Objekt „options“ umfasst

   * Optionale private Daten (options.data)
   * Optionale Schlüssel-Wert-Eigenschaften aus dem Aufruf (options.hash)
   * Möglichkeit, sich selbst aufzurufen (options.fn())
   * Möglichkeit, die Inverse von sich selbst aufzurufen (options.inverse())

* Es wird empfohlen, dass der von einem Helper zurückgegebene HTML-Zeichenfolgeninhalt ein SafeString ist.

### Ein Beispiel für einen einfachen Helper aus der Dokumentation zu Handlebars.js: {#an-example-of-a-simple-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link_to', function(title, options) {
    return new Handlebars.SafeString('<a href="/posts' + this.url + '">' + title + "!</a>");
});

var context = {posts: [
    {url: "/hello-world",
      body: "Hello World!"}
  ] };

// when link_to is called, posts is the current context
var source = '<ul>`{{#posts}}`<li>{{{link_to "Post"}}}</li>`{{/posts}}`</ul>'

var template = Handlebars.compile(source);

template(context);
```

würde Folgendes rendern:

&lt;ul>
&lt;li>&lt;a href=&quot;/posts/hello-world“>Beitrag!&lt;/a>&lt;/li>
&lt;/ul>

### Beispiel für einen Block-Helper aus der Dokumentation zu Handlebars.js: {#an-example-of-a-block-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link', function(options) {
    return new Handlebars.SafeString('<a href="/people/' + this.id + '">' + options.fn(this) + '</a>');
});

var data = { "people": [
  { "name": "Alan", "id": 1 },
  { "name": "Yehuda", "id": 2 }
]};

// when link is called, people is the current context
var source = "<ul>`{{#people}}`<li>`{{#link}}``{{name}}``{{/link}}`</li>`{{/people}}`</ul>";

var template = Handlebars.compile(source);

template(data);
```

würde Folgendes rendern:
&lt;ul>
&lt;li>&lt;a href=&quot;/people/1“>Alan&lt;/a>&lt;/li>
&lt;li>&lt;a href=&quot;/people/2“>Yehuda&lt;/a>&lt;/li>
&lt;/ul>

## Benutzerdefinierte SCF-Helfer {#custom-scf-helpers}

Benutzerdefinierte Helper müssen Server- und Client-seitig implementiert werden, insbesondere bei der Übergabe von Daten. Bei SCF werden die meisten Vorlagen Server-seitig kompiliert und gerendert, da der Server die HTML für eine bestimmte Komponente generiert, wenn die Seite angefordert wird.

### Server-seitige benutzerdefinierte Helper {#server-side-custom-helpers}

Um einen benutzerdefinierten SCF-Helper Server-seitig zu implementieren und zu registrieren, implementieren Sie einfach die Java™-Schnittstelle [TemplateHelper](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/handlebars/api/TemplateHelper.html), machen Sie sie zu einem [OSGi-Service](../../help/sites-developing/the-basics.md#osgi) und installieren Sie sie als Teil eines OSGi-Bundles.

Zum Beispiel:

### FooTextHelper.java {#footexthelper-java}

```java
/** Custom Handlebars Helper */

package com.my.helpers;

import java.io.IOException;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

import com.adobe.cq.social.handlebars.api.TemplateHelper;
import com.github.jknack.handlebars.Options;

@Service
@Component
public class FooTextHelper implements TemplateHelper<String>{

    @Override
    public CharSequence apply(String context, Options options) throws IOException {
        return "foo-" + context;
    }

    @Override
    public String getHelperName() {
        return "foo-text";
    }

    @Override
    public Class<String> getContextType() {
        return String.class;
    }
}
```

>[!NOTE]
>
>Ein für die Server-Seite erstellter Helper muss auch für die Client-Seite erstellt werden.
>
>Die Komponente wird für den angemeldeten Benutzer Client-seitig erneut gerendert. Wenn der Client-seitige Helper nicht gefunden wird, verschwindet die Komponente.

### Client-seitige benutzerdefinierte Helper {#client-side-custom-helpers}

Die Client-seitigen Helper sind Handlebars-Skripte, die durch Aufrufen von `Handlebars.registerHelper()` registriert werden.
Zum Beispiel:

### custom-helpers.js {#custom-helpers-js}

```
function(Handlebars, SCF, $CQ) {

    Handlebars.registerHelper('foo-text', function(context, options) {
        if (!context) {
            return "";
        }
        return "foo-" + context;
    });

})(Handlebars, SCF, $CQ);
```

Die benutzerdefinierten Client-seitigen Helper müssen zu einer benutzerdefinierten Client-Bibliothek hinzugefügt werden.
Die clientlib muss:

* Fügen Sie eine Abhängigkeit von `cq.social.scf` hinzu.
* Laden, nachdem Handlebars geladen wurde.
* [enthalten](clientlibs.md).

Hinweis: Die SCF-Helfer sind in `/etc/clientlibs/social/commons/scf/helpers.js` definiert.

| **[⇐ Feature Essentials](essentials.md)** | **[Server-seitige ⇒](server-customize.md)** |
|---|---|
|   | **[Client-seitige ⇒](client-customize.md)** |
