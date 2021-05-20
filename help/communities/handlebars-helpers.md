---
title: SCF Handlebars Helpers
seo-title: SCF Handlebars Helpers
description: Handlebars Helper-Methoden zur Erleichterung der Arbeit mit SCF
seo-description: Handlebars Helper-Methoden zur Erleichterung der Arbeit mit SCF
uuid: 9c514199-871e-4b68-8147-2052d2eeda15
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8b6c1697-d693-41f4-8337-f41658465107
exl-id: bfb95cae-4b0f-4521-a113-042dc4005a63
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 9%

---

# SCF Handlebars Helpers {#scf-handlebars-helpers}

| **[⇐ Funktionsgrundlagen](essentials.md)** | **[Server-seitige Anpassung imetall](server-customize.md)** |
|---|---|
|  | **[Client-seitige Anpassung imetall](client-customize.md)** |

Handlebars Helpers (helpers) sind Methoden, die von Handlebars-Skripten aufgerufen werden können, um die Arbeit mit SCF-Komponenten zu erleichtern.

Die Implementierung umfasst eine Client-seitige und eine Server-seitige Definition. Es ist auch möglich, dass Entwickler benutzerdefinierte Helfer erstellen.

Die benutzerdefinierten SCF-Helfer, die mit AEM Communities bereitgestellt werden, sind in der [Client-Bibliothek](../../help/sites-developing/clientlibs.md) definiert:

* `/etc/clientlibs/social/commons/scf/helpers.js`

>[!NOTE]
>
>Installieren Sie unbedingt das [neueste Feature Pack für Communities](deploy-communities.md#latestfeaturepack).

## Abkürzung {#abbreviate}

Hilfsmittel zum Zurückgeben einer abgekürzten Zeichenfolge, die den Eigenschaften maxWords und maxLength entspricht.

Die abzukürzende Zeichenfolge wird als Kontext bereitgestellt. Wenn kein Kontext angegeben wird, wird eine leere Zeichenfolge zurückgegeben.

Zunächst wird der Kontext auf maxLength reduziert, dann wird der Kontext in Wörter aufgeteilt und auf maxWords reduziert.

Wenn safeString auf &quot;true&quot;gesetzt ist, ist die zurückgegebene Zeichenfolge ein SafeString.

### Parameter {#parameters}

* **context**: Zeichenfolge

   (Optional) Der Standardwert ist die leere Zeichenfolge.

* **maxLength**: Zahl

   (Optional) Der Standardwert ist die Länge des Kontexts.

* **maxWords**: Zahl

   (Optional) Die Standardeinstellung ist die Anzahl der Wörter in der gekürzten Zeichenfolge.

* **safeString**: Boolesch

   (Optional) Gibt einen Handlebars.SafeString() zurück, wenn &quot;true&quot;. Der Standardwert lautet false.

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

Ein Hilfsprogramm zum Hinzufügen von zwei Bereichen unter einem div, einer für den Volltext und der andere für den weniger Text, mit der Möglichkeit, zwischen den beiden Ansichten umzuschalten.

### Parameter {#parameters-1}

* **context**: Zeichenfolge

   (Optional) Der Standardwert ist die leere Zeichenfolge.

* **numChars**: Zahl

   (Optional) Die Anzahl der Zeichen, die angezeigt werden sollen, wenn kein Volltext angezeigt wird. Der Standardwert ist 100.

* **moreText**: Zeichenfolge

   (Optional) Der anzuzeigende Text, der angibt, dass mehr Text angezeigt werden soll. Der Standardwert ist &quot;more&quot;.

* **ellipsesText**: Zeichenfolge

   (Optional) Der Text, der anzeigt, dass ausgeblendeter Text vorhanden ist. Der Standardwert ist &quot;...&quot;.

* **safeString**: Boolesch

   (Optional) Boolescher Wert, der angibt, ob Handlebars.SafeString() angewendet werden soll, bevor das Ergebnis zurückgegeben wird. Der Standardwert lautet false.

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

Hilfsmittel zum Zurückgeben einer formatierten Datums-Zeichenfolge.

### Parameter {#parameters-2}

* **context**: Zahl

   (Optional) ein Millisekunden-Wert, der vom 1. Januar 1970 (Epoche) versetzt wurde. Der Standardwert ist das aktuelle Datum.

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

## Gleich {#equals}

Hilfsmittel zum Zurückgeben von Inhalten in Abhängigkeit von einer Gleichheitsbedingung.

### Parameter {#parameters-3}

* **value**: Zeichenfolge

   Der zu vergleichende linke Wert.

* **rvalue**: Zeichenfolge

   Der zu vergleichende Wert auf der rechten Seite.

### Beispiel {#example-1}

```
{{#equals  value "some-value"}}
  <div>They are EQUAL!</div>
{{else}}
  <div>They are NOT equal!</div>
{{/equals}}
```

## If-wcm-mode {#if-wcm-mode}

Ein Block-Helfer, der den aktuellen Wert von [WCM-Modus](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html) anhand einer durch Zeichenfolgen getrennten Liste von Modi testet.

### Parameter {#parameters-4}

* **context**: Zeichenfolge

   (Optional) Die zu übersetzende Zeichenfolge. Erforderlich, wenn kein Standardwert angegeben wurde.

* **mode**: Zeichenfolge

   (Optional) Eine kommagetrennte Liste von [WCM-Modi](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/WCMMode.html), die getestet werden sollen, falls festgelegt.

### Beispiel {#example-2}

```xml
{{#if-wcm-mode mode="DESIGN, EDIT"}}
 ...
{{else}}
 ...
{{/if-wcm-mode}}
```

## i18n {#i-n}

Dieser Helfer überschreibt den Handlebars-Helfer &#39;i18n&#39;.

Siehe auch [Internationalisierung von Zeichenfolgen in JavaScript-Code](../../help/sites-developing/i18n-dev.md#internationalizing-strings-in-javascript-code).

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

Hilfsmittel zum Einfügen einer Komponente als nicht vorhandene Ressource in eine Vorlage.

Dadurch kann die Ressource programmgesteuert einfacher angepasst werden als für eine Ressource, die als JCR-Knoten hinzugefügt wird. Siehe [Hinzufügen oder Einfügen einer Communities-Komponente](scf.md#add-or-include-a-communities-component).

Es sind nur einige ausgewählte Communities-Komponenten eingeschlossen. Für AEM 6.1 sind die inkludierten [Kommentare](essentials-comments.md), [Bewertung](rating-basics.md), [Bewertungen](reviews-basics.md) und [Abstimmung](essentials-voting.md).

Dieser Helfer, der nur serverseitig geeignet ist, bietet Funktionen, die [cq:include](../../help/sites-developing/taglib.md) für JSP-Skripte ähneln.

### Parameter {#parameters-6}

* **context**: Zeichenfolge oder Objekt

   (Optional, sofern kein relativer Pfad angegeben wird)

   Verwenden Sie `this` , um den aktuellen Kontext zu übergeben.

   Verwenden Sie `this.id`, um die Ressource unter `id` zum Rendern des angeforderten Ressourcentyps abzurufen.

* **resourceType**: Zeichenfolge

   (Optional) Der Ressourcentyp wird standardmäßig auf Ressourcentyp aus dem Kontext festgelegt.

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

Dies umfasst eine neue Kommentarkomponente unter `this.id` + /comments.

## IncludeClientLib {#includeclientlib}

Ein Hilfsprogramm, das eine AEM HTML-Client-Bibliothek enthält, die eine JS-, CSS- oder Design-Bibliothek sein kann. Für mehrere Einschlüsse verschiedener Typen, z. B. js und css, muss dieses Tag mehrmals im Handlebars-Skript verwendet werden.

Dieser Helfer, der nur serverseitig geeignet ist, bietet Funktionen, die [ui:includeClientLib](../../help/sites-developing/taglib.md) für JSP-Skripte ähneln.

### Parameter {#parameters-7}

* **categories**: Zeichenfolge

   (Optional) Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Dateien und CSS-Bibliotheken für die betreffenden Kategorien mit ein. Der Designname wird aus der Abfrage extrahiert.

* **Design**: Zeichenfolge

   (Optional) Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies beinhaltet alle designbezogenen Bibliotheken (CSS und JS) für die entsprechenden Kategorien. Der Designname wird aus der Abfrage extrahiert.

* **js**: Zeichenfolge

   (Optional) Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle Javascript-Bibliotheken für die betreffenden Kategorien mit ein.

* **css**: Zeichenfolge

   (Optional) Eine Liste mit kommagetrennten Client-Bibliothekskategorien. Dies bezieht alle CSS-Bibliotheken für die betreffenden Kategorien mit ein.

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

## Pretty-time {#pretty-time}

Ein Hilfsmittel, mit dem angezeigt wird, wie viel Zeit bis zu einem Cutoff-Punkt vergangen ist, nach dem ein reguläres Datumsformat angezeigt wird.

Beispiel:

* Vor 12 Stunden
* Vor 7 Tagen

### Parameter {#parameters-8}

* **context**: Zahl

   Eine Zeit in der Vergangenheit, um mit &quot;jetzt&quot;zu vergleichen. Die Zeit wird als Millisekunden-Wertversatz ab dem 1. Januar 1970 (Epoche) ausgedrückt.

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

## Xss-html {#xss-html}

Ein Hilfsprogramm, das eine Quellzeichenfolge für HTML-Elementinhalte codiert, um den Schutz vor XSS zu unterstützen.

HINWEIS: Dies ist kein Validator und sollte nicht zum Schreiben von Attributwerten verwendet werden.

### Parameter {#parameters-9}

* **context**: Objekt

   Der zu kodierende HTML-Code.

### Beispiel {#example-6}

```
<p>{{xss-html forum-ugc}}</p>
```

## Xss-htmlAttr {#xss-htmlattr}

Ein Hilfsprogramm, das eine Quellzeichenfolge zum Schreiben in einen HTML-Attributwert kodiert, um den Schutz vor XSS zu unterstützen.

HINWEIS: Dies ist kein Validator und sollte nicht zum Schreiben von umsetzbaren Attributen (href, src, event handlers) verwendet werden.

### Parameter {#parameters-10}

* **context**: Objekt

   Der zu kodierende HTML-Code.

### Beispiel {#example-7}

```
<div id={{xss-htmlAttr id}} />
```

## Xss-jsString {#xss-jsstring}

Ein Hilfsprogramm, das eine Quellzeichenfolge zum Schreiben in JavaScript-Zeichenfolgeninhalte kodiert, um den Schutz vor XSS zu unterstützen.

HINWEIS: Dies ist kein Validator und soll nicht zum Schreiben in beliebiges JavaScript verwendet werden.

### Parameter {#parameters-11}

* **context**: Objekt

   Der zu kodierende HTML-Code.

### Beispiel {#example-8}

```
var input = {{xss-jsString topic-title}}
```

## Xss-validHref {#xss-validhref}

Ein Helfer, der eine URL zum Schreiben als HTML-href- oder -srce-Attributwert bereinigt, um den Schutz vor XSS zu unterstützen.

HINWEIS: dies kann eine leere Zeichenfolge zurückgeben

### Parameter {#parameters-12}

* **context**: Objekt

   Die URL, die bereinigt werden soll.

### Beispiel {#example-9}

```
<a href="{{xss-validHref url}}">my link</a>
```

## Handlebars.js Grundlegende Übersicht {#handlebars-js-basic-overview}

Ein kurzer Überblick über Hilfsfunktionen aus der [Handlebars.js-Dokumentation](https://handlebarsjs.com/expressions.html):

* Ein Handlebars helper -Aufruf ist eine einfache Kennung (der *Name* des Helfers), gefolgt von null oder mehr durch Leerzeichen getrennten Parametern.
* Parameter können ein einfaches String-, number-, boolesches oder JSON-Objekt sowie eine optionale Sequenz von Schlüssel-Wert-Paaren (Hash-Argumenten) als letzte Parameter sein.
* Die Schlüssel in Hash-Argumenten müssen einfache Bezeichner sein.
* Die Werte in den Hash-Argumenten sind Handlebars-Ausdrücke: einfache Bezeichner, Pfade oder Zeichenfolgen.
* Der aktuelle Kontext, `this`, ist immer für Handlebars-Helfer verfügbar.
* Der Kontext kann ein String-, number-, boolesches oder JSON-Datenobjekt sein.
* Es ist möglich, ein im aktuellen Kontext verschachteltes Objekt als Kontext zu übergeben, z. B. `this.url` oder `this.id` (siehe die folgenden Beispiele für einfache und Blockhilfen).

* Block Helpers sind Funktionen, die von überall in der Vorlage aufgerufen werden können. Sie können einen Block der Vorlage jedes Mal null oder mehrmals mit einem anderen Kontext aufrufen. Sie enthalten einen Kontext zwischen {{#*name*}} und {{/*name*}}.

* Handlebars bietet einen letzten Parameter für Hilfedateien namens &quot;options&quot;. Das Sonderobjekt &#39;options&#39; enthält

   * Optionale private Daten (options.data)
   * Optionale Tastenwerteigenschaften aus dem Aufruf (options.hash)
   * Möglichkeit, sich selbst aufzurufen (options.fn())
   * Möglichkeit, das Umkehren von sich selbst aufzurufen (options.inverse())

* Es wird empfohlen, dass der HTML String-Inhalt, der von einem Helfer zurückgegeben wird, ein SafeString ist.

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

würde rendern:

&lt;ul>
&lt;li>&lt;a href=&quot;/posts/hello-world&quot;>Post!&lt;/a>&lt;/li>
&lt;/ul>

### Ein Beispiel für einen Block-Helfer aus der Handlebars.js-Dokumentation: {#an-example-of-a-block-helper-from-handlebars-js-documentation}

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

würde rendern:
&lt;ul>
&lt;li>&lt;a href=&quot;/people/1&quot;>Alan&lt;/a>&lt;/li>
&lt;li>&lt;a href=&quot;/people/2&quot;>Yehuda&lt;/a>&lt;/li>
&lt;/ul>

## Benutzerdefinierte SCF-Helfer {#custom-scf-helpers}

Benutzerdefinierte Helfer müssen sowohl serverseitig als auch Client-seitig implementiert werden, insbesondere bei der Übergabe von Daten. Bei SCF werden die meisten Vorlagen serverseitig kompiliert und gerendert, da der Server den HTML-Code für eine bestimmte Komponente generiert, wenn die Seite angefordert wird.

### Serverseitige benutzerdefinierte Helfer {#server-side-custom-helpers}

Um einen benutzerdefinierten SCF-Helfer serverseitig zu implementieren und zu registrieren, implementieren Sie einfach die Java-Schnittstelle [TemplateHelper](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/handlebars/api/TemplateHelper.html), machen Sie sie zu einem [OSGi-Dienst](../../help/sites-developing/the-basics.md#osgi) und installieren Sie sie als Teil eines OSGi-Bundles.

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
>Ein für die serverseitige Benutzeroberfläche erstellter Helfer muss auch für die Client-Seite erstellt werden.
>
>Die Komponente wird für den angemeldeten Benutzer clientseitig erneut gerendert. Wenn der clientseitige Helfer nicht gefunden wird, verschwindet die Komponente.

### Clientseitige benutzerdefinierte Helfer {#client-side-custom-helpers}

Die clientseitigen Helfer sind Handlebars-Skripte, die durch Aufrufen von `Handlebars.registerHelper()` registriert werden.
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
Die clientlib muss:

* Fügen Sie eine Abhängigkeit von `cq.social.scf` hinzu.
* Laden nach Laden der Handlebars.
* Sei [included](clientlibs.md).

Hinweis: Die SCF-Helfer sind in `/etc/clientlibs/social/commons/scf/helpers.js` definiert.

| **[⇐ Funktionsgrundlagen](essentials.md)** | **[Server-seitige Anpassung imetall](server-customize.md)** |
|---|---|
|  | **[Client-seitige Anpassung imetall](client-customize.md)** |
