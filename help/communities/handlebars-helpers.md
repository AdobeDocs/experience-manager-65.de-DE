---
title: SCF Handlebars Helfers
seo-title: SCF Handlebars Helfers
description: Handlebars Helper-Methoden zur Erleichterung der Arbeit mit SCF
seo-description: Handlebars Helper-Methoden zur Erleichterung der Arbeit mit SCF
uuid: 9c514199-871e-4b68-8147-2052d2eeda15
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8b6c1697-d693-41f4-8337-f41658465107
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 9%

---


# SCF Handlebars Helpers {#scf-handlebars-helpers}

| **[⇐ Essentials](essentials.md)** | **[Serverseitige Anpassung ⇒](server-customize.md)** |
|---|---|
|  | **[Clientseitige Anpassung ⇒](client-customize.md)** |

Handlebars Helpers (Helpers) sind Methoden, die von Handlebars-Skripten aufgerufen werden können, um die Arbeit mit SCF-Komponenten zu erleichtern.

Die Implementierung umfasst eine clientseitige und eine serverseitige Definition. Entwickler können auch benutzerdefinierte Helfer erstellen.

Die mit AEM Communities gelieferten benutzerdefinierten SCF-Helfer werden in der [Client-Bibliothek](../../help/sites-developing/clientlibs.md) definiert:

* `/etc/clientlibs/social/commons/scf/helpers.js`

>[!NOTE]
>
>Installieren Sie unbedingt das [neueste Communities Feature Pack](deploy-communities.md#latestfeaturepack).

## Abkürzung {#abbreviate}

Ein Helfer, der eine abgekürzte Zeichenfolge zurückgibt, die den Eigenschaften maxWords und maxLength entspricht.

Die abzukürzende Zeichenfolge wird als Kontext bereitgestellt. Wenn kein Kontext angegeben ist, wird eine leere Zeichenfolge zurückgegeben.

Zuerst wird der Kontext auf maxLength zugeschnitten, dann wird der Kontext in Wörter unterteilt und auf maxWords reduziert.

Wenn safeString auf true festgelegt ist, ist die zurückgegebene Zeichenfolge ein SafeString.

### Parameter {#parameters}

* **context**: Zeichenfolge

   (Optional) Die Standardeinstellung ist eine leere Zeichenfolge

* **maxLength**: Nummer

   (Optional) Der Standardwert ist die Länge des Kontexts.

* **maxWords**: Nummer

   (Optional) Die Standardeinstellung ist die Anzahl der Wörter in der zugeschnittenen Zeichenfolge.

* **safeString**: Boolesch

   (Optional) Gibt einen Handlebars.SafeString() zurück, wenn true. Der Standardwert lautet false.

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

## Content-loadmore {#content-loadmore}

Ein Helfer, um zwei Bereiche unter einem div hinzuzufügen, einer für den Volltext und der andere für den less-Text, mit der Möglichkeit, zwischen den beiden Ansichten umzuschalten.

### Parameter {#parameters-1}

* **context**: Zeichenfolge

   (Optional) Der Standardwert ist die leere Zeichenfolge.

* **numChars**: Nummer

   (Optional) Die Anzahl der Zeichen, die angezeigt werden, wenn kein Volltext angezeigt wird. Der Standardwert ist 100.

* **moreText**: Zeichenfolge

   (Optional) Der anzuzeigende Text, der angibt, dass mehr Text angezeigt werden soll. Der Standardwert ist &quot;mehr&quot;.

* **ellipsesText**: Zeichenfolge

   (Optional) Der anzuzeigende Text, der angibt, dass ausgeblendeter Text vorhanden ist. Der Standardwert ist &quot;...&quot;.

* **safeString**: Boolesch

   (Optional) Ein boolescher Wert, der angibt, ob Handlebars.SafeString() angewendet werden soll, bevor das Ergebnis zurückgegeben wird. Der Standardwert lautet false.

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

Ein Helfer zum Zurückgeben einer formatierten Datums-Zeichenfolge.

### Parameter {#parameters-2}

* **context**: Nummer

   (Optional) ein Millisekunden-Wertversatz vom 1. Januar 1970 (Epoche). Der Standardwert ist das aktuelle Datum.

* **format**: Zeichenfolge

   (Optional) Das anzuwendende Datumsformat. Der Standardwert ist &quot;YYYY-MM-DDTHH:mm:ss.sssZ&quot;und das Ergebnis wird als &quot;2015-03-18T18:17:13-07:00&quot;angezeigt.

### Beispiele {#examples-1}

```
{{dateUtil this.memberSince format="dd MMM yyyy, hh:mm"}}

// returns "18 Mar 2015, 18:17"
```

```
{{dateUtil this.birthday format="MM-DD-YYYY"}}

// returns "03-18-2015"
```

## Ist {#equals}

Ein Helfer zum Zurückgeben von Inhalten, abhängig von einer Gleichheitsbedingung.

### Parameter {#parameters-3}

* **lvalue**: Zeichenfolge

   Der zu vergleichende linke Wert.

* **rvalue**: Zeichenfolge

   Der zu vergleichende rechte Wert.

### Beispiel {#example-1}

```
{{#equals  value "some-value"}}
  <div>They are EQUAL!</div>
{{else}}
  <div>They are NOT equal!</div>
{{/equals}}
```

## If-wcm-mode {#if-wcm-mode}

Ein Blockhelfer, der den aktuellen Wert von [WCM-Modus](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) gegen eine durch eine Zeichenfolge getrennte Liste von Modi testet.

### Parameter {#parameters-4}

* **context**: Zeichenfolge

   (Optional) Die zu übersetzende Zeichenfolge. Erforderlich, wenn kein Standardwert angegeben wurde.

* **Modus**: Zeichenfolge

   (Optional) Eine kommagetrennte Liste von [WCM-Modi](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html), um zu testen, falls festgelegt.

### Beispiel {#example-2}

```xml
{{#if-wcm-mode mode="DESIGN, EDIT"}}
 ...
{{else}}
 ...
{{/if-wcm-mode}}
```

## i18n {#i-n}

Dieser Helfer setzt den Handlebars Helper &#39;i18n&#39; außer Kraft.

Siehe auch [Internationalisierende Zeichenfolgen in JavaScript-Code](../../help/sites-developing/i18n-dev.md#internationalizing-strings-in-javascript-code).

### Parameter {#parameters-5}

* **context**: Zeichenfolge

   (Optional) Die zu übersetzende Zeichenfolge. Erforderlich, wenn kein Standardwert angegeben wurde.

* **Standard**: Zeichenfolge

   (Optional) Die zu übersetzende Standardzeichenfolge. Erforderlich, wenn kein Kontext angegeben wurde.

* **Kommentar**: Zeichenfolge

   (Optional) Ein Übersetzungshinweis

### Beispiel {#example-3}

```
{{i18n "hello"}}
{{i18n "hello" comment="greeting" default="bonjour"}}
```

## Einbeziehen {#include}

Ein Helfer zum Einbeziehen einer Komponente als nicht vorhandene Ressource in eine Vorlage.

Dadurch kann die Ressource programmgesteuert einfacher angepasst werden, als es für eine Ressource möglich ist, die als JCR-Knoten hinzugefügt wird. Siehe [Hinzufügen oder Einschließen einer Communities-Komponente](scf.md#add-or-include-a-communities-component).

Es sind nur einige ausgewählte Communities-Komponenten inklusive. Für AEM 6.1 sind die folgenden inklusiven Werte: [comments](essentials-comments.md), [rating](rating-basics.md), [reviews](reviews-basics.md) und [stimating](essentials-voting.md).

Dieser Helfer, der nur serverseitig geeignet ist, bietet Funktionen, die [cq:include](../../help/sites-developing/taglib.md) für JSP-Skripten ähneln.

### Parameter {#parameters-6}

* **context**: Zeichenfolge oder Objekt

   (Optional, sofern kein relativer Pfad angegeben wird)

   Verwenden Sie `this`, um den aktuellen Kontext zu übergeben.

   Verwenden Sie `this.id`, um die Ressource unter `id` abzurufen, um den angeforderten resourceType zu rendern.

* **resourceType**: Zeichenfolge

   (Optional) Der Ressourcentyp wird standardmäßig vom Kontext zum Ressourcentyp gewählt.

* **template**: Zeichenfolge

   Pfad zum Komponentenskript.

* **path**: Zeichenfolge

   (Erforderlich) Der Pfad zur Ressource. Wenn der Pfad relativ ist, muss ein Kontext angegeben werden. Andernfalls wird die leere Zeichenfolge zurückgegeben.

* **authoringDisabled**: Boolesch

   (Optional) Der Standardwert ist &quot;false&quot;. Nur zur internen Verwendung.

### Beispiel {#example-4}

```
{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}
```

Dies beinhaltet eine neue Kommentarkomponente unter `this.id` + /comments.

## IncludeClientLib {#includeclientlib}

Ein Helfer mit einer AEM HTML-Client-Bibliothek, bei der es sich um eine JS-, CSS- oder Designbibliothek handeln kann. Für mehrere Inklusionen verschiedener Typen, z. B. js und css, muss dieses Tag im Handlebars-Skript mehrmals verwendet werden.

Dieser Helfer, der nur serverseitig geeignet ist, bietet Funktionen, die bei JSP-Skripten [ui:includeClientLib](../../help/sites-developing/taglib.md) ähneln.

### Parameter {#parameters-7}

* **Kategorien**: Zeichenfolge

   (Optional) Eine Liste kommagetrennter Client-Lib-Kategorien. Dies bezieht alle Javascript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien mit ein. Der Designname wird aus der Abfrage extrahiert.

* **Thema**: Zeichenfolge

   (Optional) Eine Liste kommagetrennter Client-Lib-Kategorien. Dies beinhaltet alle designbezogenen Bibliotheken (CSS und JS) für die entsprechenden Kategorien. Der Designname wird aus der Abfrage extrahiert.

* **js**: Zeichenfolge

   (Optional) Eine Liste kommagetrennter Client-Lib-Kategorien. Dies bezieht alle Javascript-Bibliotheken für die betreffenden Kategorien mit ein.

* **css**: Zeichenfolge

   (Optional) Eine Liste kommagetrennter Client-Lib-Kategorien. Dies bezieht alle CSS-Bibliotheken für die betreffenden Kategorien mit ein.

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

## PrettyTime {#pretty-time}

Ein Helfer, der anzeigt, wie viel Zeit bis zu einem Cutoff-Punkt vergangen ist, nach dem ein reguläres Datumsformat angezeigt wird.

Beispiel:

* Vor 12 Stunden
* Vor 7 Tagen

### Parameter {#parameters-8}

* **context**: Nummer

   Eine Zeit in der Vergangenheit, die mit &quot;jetzt&quot; zu vergleichen ist. Die Zeit wird als Millisekunden-Wertversatz ab dem 1. Januar 1970 (Epoche) ausgedrückt.

* **daysCutoff**: Nummer

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

## Xss-html {#xss-html}

Ein Helfer, der eine Quellzeichenfolge für HTML-Elementinhalte kodiert, um den Schutz vor XSS zu unterstützen.

HINWEIS: dies ist kein Validator und soll nicht zum Schreiben von Attributwerten verwendet werden.

### Parameter {#parameters-9}

* **context**: object

   Der zu kodierende HTML.

### Beispiel {#example-6}

```
<p>{{xss-html forum-ugc}}</p>
```

## Xss-htmlAttr {#xss-htmlattr}

Ein Helfer, der eine Quellzeichenfolge für das Schreiben in einen HTML-Attributwert kodiert, um XSS abzuwehren.

HINWEIS: dies ist kein Validator und ist nicht zum Schreiben von mit Aktionen versehenen Attributen (href, src, Ereignis Handler) zu verwenden.

### Parameter {#parameters-10}

* **context**: Objekt

   Der zu kodierende HTML.

### Beispiel {#example-7}

```
<div id={{xss-htmlAttr id}} />
```

## Xss-jsString {#xss-jsstring}

Ein Helfer, der eine Quellzeichenfolge für das Schreiben in JavaScript-Zeichenfolgeninhalt kodiert, um XSS zu schützen.

HINWEIS: dies ist kein Validator und ist nicht zum Schreiben in beliebiges JavaScript zu verwenden.

### Parameter {#parameters-11}

* **context**: Objekt

   Der zu kodierende HTML.

### Beispiel {#example-8}

```
var input = {{xss-jsString topic-title}}
```

## Xss-validHref {#xss-validhref}

Ein Helfer, der eine URL für das Schreiben als HTML-href- oder -srce-Attributwert anerkennt, um XSS zu schützen.

HINWEIS: kann eine leere Zeichenfolge zurückgeben

### Parameter {#parameters-12}

* **context**: Objekt

   Die zu bereinigende URL.

### Beispiel {#example-9}

```
<a href="{{xss-validHref url}}">my link</a>
```

## Handlebars.js Grundlegende Übersicht {#handlebars-js-basic-overview}

Eine kurze Übersicht über Hilfsfunktionen aus der [Handlebars.js-Dokumentation](https://handlebarsjs.com/expressions.html):

* Ein Handlebars Helper-Aufruf ist ein einfacher Bezeichner (der *name* des Helfers), gefolgt von einem oder mehreren durch Leerzeichen getrennten Parametern.
* Parameter können ein einfaches String-, number-, boolean- oder JSON-Objekt sowie eine optionale Sequenz von Schlüssel-Wert-Paaren (Hash-Argumente) als letzte Parameter sein.
* Die Schlüssel in Hashargumenten müssen einfache Bezeichner sein.
* Die Werte in den Hash-Argumenten sind Handlebars-Ausdruck: einfache Bezeichner, Pfade oder Zeichenfolgen.
* Der aktuelle Kontext, `this`, ist immer für Handlebars Helpers verfügbar.
* Der Kontext kann ein String-, number-, boolean- oder JSON-Datenobjekt sein.
* Es ist möglich, ein im aktuellen Kontext verschachteltes Objekt als Kontext zu übergeben, z. B. `this.url` oder `this.id` (siehe folgende Beispiele von einfachen und Blockhelfern).

* Blockhelfer sind Funktionen, die von jeder beliebigen Stelle in der Vorlage aufgerufen werden können. Sie können einen Vorlagenblock jedes Mal mit einem anderen Kontext null oder mehrmals aufrufen. Sie enthalten einen Kontext zwischen {{#*name*}} und {{/*name*}}.

* Handlebars bietet einen endgültigen Parameter für Helfer namens &#39;options&#39;. Das Sonderobjekt &#39;options&#39; enthält

   * Optionale private Daten (options.data)
   * Optionale Eigenschaften von Schlüsselwerten aus dem Aufruf (options.hash)
   * Möglichkeit zum Aufrufen selbst (options.fn())
   * Möglichkeit zum Aufrufen des Umkehrs (options.inverse())

* Es wird empfohlen, dass der HTML-String-Inhalt, der von einem Helfer zurückgegeben wird, ein SafeString ist.

### Ein Beispiel für einen einfachen Helfer aus der Handlebars.js-Dokumentation: {#an-example-of-a-simple-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link_to', function(title, options) {
    return new Handlebars.SafeString('<a href="/posts' + this.url + '">' + title + "!</a>");
});

var context = {posts: [
    {url: "/hello-world",
      body: "Hello World!"}
  ] };

// when link_to is called, posts is the current context
var source = '<ul>{{#posts}}<li>{{{link_to "Post"}}}</li>{{/posts}}</ul>'

var template = Handlebars.compile(source);

template(context);
```

Rendering:

&lt;ul>
&lt;li>&lt;a href=&quot;/posts/hello-world&quot;>Posten!&lt;/a>&lt;/li>
&lt;/ul>

### Beispiel eines Blockhelpers aus der Dokumentation zu Handlebars.js: {#an-example-of-a-block-helper-from-handlebars-js-documentation}

```
Handlebars.registerHelper('link', function(options) {
    return new Handlebars.SafeString('<a href="/people/' + this.id + '">' + options.fn(this) + '</a>');
});

var data = { "people": [
  { "name": "Alan", "id": 1 },
  { "name": "Yehuda", "id": 2 }
]};

// when link is called, people is the current context
var source = "<ul>{{#people}}<li>{{#link}}{{name}}{{/link}}</li>{{/people}}</ul>";

var template = Handlebars.compile(source);

template(data);
```

Rendering:
&lt;ul>
&lt;li>&lt;a href=&quot;/people/1&quot;>Alan&lt;/a>&lt;/li>
&lt;li>&lt;a href=&quot;/people/2&quot;>Yehuda&lt;/a>&lt;/li>
&lt;/ul>

## Benutzerspezifische SCF-Helfer {#custom-scf-helpers}

Benutzerspezifische Helfer müssen auf der Server- und Clientseite implementiert werden, besonders bei der Datenübergabe. Bei SCF werden die meisten Vorlagen serverseitig kompiliert und gerendert, während der Server das HTML für eine bestimmte Komponente generiert, wenn die Seite angefordert wird.

### Benutzerspezifische Helfer auf Serverseite {#server-side-custom-helpers}

Um einen benutzerdefinierten SCF-Helfer auf der Serverseite zu implementieren und zu registrieren, implementieren Sie einfach die Java-Schnittstelle [TemplateHelper](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/handlebars/api/TemplateHelper.html), stellen Sie sie zu einem [OSGi-Dienst](../../help/sites-developing/the-basics.md#osgi) ein und installieren Sie sie als Teil eines OSGi-Bundles.

Beispiel:

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
>Für die clientseitige Erstellung muss auch ein Helfer erstellt werden.
>
>Die Komponente wird für den angemeldeten Benutzer clientseitig wiedergegeben. Wenn der clientseitige Helfer nicht gefunden wird, wird die Komponente ausgeblendet.

### Clientseitige benutzerdefinierte Helfer {#client-side-custom-helpers}

Die clientseitigen Helfer sind Handlebars-Skripte, die durch Aufrufen von `Handlebars.registerHelper()` registriert wurden.
Beispiel:

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

Die benutzerdefinierten clientseitigen Helfer müssen einer benutzerdefinierten Client-Bibliothek hinzugefügt werden.
clientlib muss:

* Schließen Sie eine Abhängigkeit von `cq.social.scf` ein.
* Laden nach dem Laden der Handlebars.
* Sei [einschließlich](clientlibs.md).

Hinweis: Die SCF-Helfer sind in `/etc/clientlibs/social/commons/scf/helpers.js` definiert.

| **[⇐ Essentials](essentials.md)** | **[Serverseitige Anpassung ⇒](server-customize.md)** |
|---|---|
|  | **[Clientseitige Anpassung ⇒](client-customize.md)** |

