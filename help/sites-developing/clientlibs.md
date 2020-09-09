---
title: Verwendung clientseitiger Bibliotheken
seo-title: Verwendung clientseitiger Bibliotheken
description: AEM stellt clientseitige Bibliotheksordner zur Verfügung, mit denen Sie Ihren clientseitigen Code im Repository speichern, in Kategorien gruppieren und definieren können, wann und wie jede Codekategorie dem Client bereitgestellt werden soll.
seo-description: AEM stellt clientseitige Bibliotheksordner zur Verfügung, mit denen Sie Ihren clientseitigen Code im Repository speichern, in Kategorien gruppieren und definieren können, wann und wie jede Codekategorie dem Client bereitgestellt werden soll.
uuid: f12b13cc-6651-4c9a-9c52-19a22bb82b28
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 3d14837d-41a8-480a-83ba-392e32f84c65
docset: aem65
translation-type: tm+mt
source-git-commit: 5d33b48000cf607eb77c626ec539280cadab378e
workflow-type: tm+mt
source-wordcount: '2889'
ht-degree: 59%

---


# Verwendung clientseitiger Bibliotheken{#using-client-side-libraries}

Moderne Websites beruhen in hohem Maße auf der clientseitigen Verarbeitung durch einen komplexen JavaScript- und CSS-Code. Die Organisation und Optimierung der Bereitstellung dieses Codes kann äußerst kompliziert sein.

Um Abhilfe zu schaffen, stellt AEM **clientseitige Bibliotheksordner** zur Verfügung, mit denen Sie Ihren clientseitigen Code im Repository speichern, in Kategorien gruppieren und definieren können, wann und wie jede Codekategorie dem Client bereitgestellt werden soll. Das clientseitige Bibliotheksystem übernimmt dann das Erstellen der korrekten Links in der endgültigen Webseite, um den korrekten Code zu laden.

## Funktionsweise clientseitiger Bibliotheken in AEM {#how-client-side-libraries-work-in-aem}

The standard way to include a client-side library (that is, a JS or CSS file) in the HTML of a page is simply to include a `<script>` or `<link>` tag in the JSP for that page, containing the path to the file in question. Beispiel:

```xml
...
<head>
   ...
   <script type="text/javascript" src="/etc/clientlibs/granite/jquery/source/1.8.1/jquery-1.8.1.js"></script>
   ...
</head>
...
```

Obwohl diese Vorgehensweise in AEM funktioniert, kann sie zu Problemen führen, wenn die Seiten und die darin enthaltenen Komponenten zu komplex werden. Dann besteht die Gefahr, dass mehrere Kopien derselben JS-Bibliothek in der endgültigen HTML-Ausgabe enthalten sind. Um dies zu vermeiden und einen logischen Aufbau clientseitiger Bibliotheken zu ermöglichen, verwendet AEM **clientseitige Bibliotheksordner**.

Ein clientseitiger Bibliotheksordner ist ein Repository-Knoten des Typs `cq:ClientLibraryFolder`. Seine Definition in [CND-Notation](https://jackrabbit.apache.org/node-type-notation.html) ist

```shell
[cq:ClientLibraryFolder] > sling:Folder
  - dependencies (string) multiple
  - categories (string) multiple
  - embed (string) multiple
  - channels (string) multiple
```

By default, `cq:ClientLibraryFolder` nodes can be placed anywhere within the `/apps`, `/libs` and `/etc` subtrees of the repository (these defaults, and other settings can be controlled through the **Adobe Granite HTML Library Manager** panel of the [System Console](https://localhost:4502/system/console/configMgr)).

Each `cq:ClientLibraryFolder` is populated with a set of JS and/or CSS files, along with a few supporting files (see below). The properties of the `cq:ClientLibraryFolder` are configured as follows:

* `categories`: Identifiziert die Kategorien, in die der Satz der JS- und/oder CSS-Dateien in diesem `cq:ClientLibraryFolder` Herbst fällt. Da die Eigenschaft `categories` mehrere Werte aufweisen kann, kann ein Bibliotheksordner zu mehreren Kategorien gehören (weiter unten sehen Sie, warum dies nützlich sein kann).

* `dependencies`: Eine Liste anderer Client-Bibliothekskategorien, von denen dieser Bibliotheksordner abhängt. For example, given two `cq:ClientLibraryFolder` nodes `F` and `G`, if a file in `F` requires another file in `G` in order to function properly, then at least one of the `categories` of `G` should be among the `dependencies` of `F`.

* `embed`: Wird zum Einbetten von Code aus anderen Bibliotheken verwendet. Wenn Node F die Knoten G und H einbettet, ist das resultierende HTML eine Inhaltskonzentration der Knoten G und H.
* `allowProxy`: Wenn sich eine Client-Bibliothek unter `/apps`befindet, erlaubt diese Eigenschaft den Zugriff darauf über das Proxy-Servlet. See [Locating a Client Library Folder and Using the Proxy Client Libraries Servlet](/help/sites-developing/clientlibs.md#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet) below.

## Referenzieren von clientseitigen Bibliotheken {#referencing-client-side-libraries}

Da HTL die bevorzugte Technologie zur Entwicklung von AEM Sites ist, sollte HTL verwendet werden, um clientseitige Bibliotheken in AEM einzuschließen. Sie können jedoch auch JSP verwenden.

### Verwendung von HTL {#using-htl}

In HTL werden Client-Bibliotheken über eine durch AEM bereitgestellte Hilfsvorlage geladen, auf die über [`data-sly-use`](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#use) zugegriffen werden kann. In dieser Datei sind drei Vorlagen verfügbar, die über [`data-sly-call`](https://helpx.adobe.com/experience-manager/htl/using/block-statements.html#template-call) abgerufen werden können:

* **css** - Lädt nur die CSS-Dateien der referenzierten Client-Bibliotheken.
* **js** - Lädt nur die JavaScript-Dateien der referenzierten Clientbibliotheken.
* **all** - Lädt alle Dateien der referenzierten Client-Bibliotheken (sowohl CSS als auch JavaScript).

Jede Hilfsvorlage erwartet eine `categories`-Option für das Referenzieren der gewünschten Client-Bibliotheken. Bei dieser Option kann es sich um einen Zeichenfolgenwertbereich handeln oder um eine Zeichenfolge, die eine CSV-Liste enthält.

For further details and exmple of usage, see the document [Getting Started with the HTML Template Language](https://helpx.adobe.com/experience-manager/htl/using/getting-started.html#loading-client-libraries).

### Verwendung von JSP {#using-jsp}

Add a `ui:includeClientLib` tag to your JSP code to add a link to client libraries in the generated HTML page. To reference the libraries, you use the value of the `categories` property of the `ui:includeClientLib` node.

```
<%@taglib prefix="ui" uri="https://www.adobe.com/taglibs/granite/ui/1.0" %>
<ui:includeClientLib categories="<%= categories %>" />
```

For example, the `/etc/clientlibs/foundation/jquery` node is of type `cq:ClientLibraryFolder` with a categories property of value `cq.jquery`. Der folgende Code in einer JSP-Datei referenziert die Bibliotheken:

```xml
<ui:includeClientLib categories="cq.jquery"/>
```

Die generierte HTML-Seite enthält den folgenden Code:

```xml
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
```

Ausführliche Informationen wie Attribute zum Filtern von JS, CSS oder Themenbibliotheken finden Sie unter [ui:includeClientLib](/help/sites-developing/taglib.md#lt-ui-includeclientlib).

>[!CAUTION]
>
>`<cq:includeClientLib>`, die in der Vergangenheit häufig zur Einbindung von Client-Bibliotheken verwendet wurde, ist seit AEM 5.6 veraltet. [ `<ui:includeClientLib>`](/help/sites-developing/taglib.md#lt-ui-includeclientlib) sollte stattdessen wie oben beschrieben verwendet werden.

## Erstellen von Client-Bibliotheksordnern {#creating-client-library-folders}

Erstellen Sie einen `cq:ClientLibraryFolder`-Knoten, um JavaScript- und CSS-Bibliotheken zu definieren und HTML-Seiten zur Verfügung zu stellen. Verwenden Sie die `categories`-Eigenschaft des Knotens, um festzulegen, zu welchen Bibliothekskategorien er gehört.

Der Knoten enthält eine oder mehrere Quelldateien, die zur Laufzeit zu einer einzelnen JS- und/oder CSS-Datei zusammengeführt werden. The name of the generated file is the node name with either the `.js` or `.css` file name extension. For example, the library node named `cq.jquery` results in the generated file named `cq.jquery.js` or `cq.jquery.css`.

Client-Bibliotheksordner enthalten die folgenden Elemente:

* Die zusammenzuführenden JS- und/oder CSS-Quelldateien.
* Ressourcen, die CSS-Styles unterstützen, z. B. Bilddateien.

   **Hinweis:** Sie können Quelldateien mit Unterordnern organisieren.
* Eine Datei `js.txt` und/oder `css.txt`, die die Quelldateien angibt, die in die generierten JS- und/oder CSS Dateien zusammengeführt werden sollen.

![clientlibarch](assets/clientlibarch.png)

Weitere Informationen zu Anforderungen speziell für Client-Bibliotheken für Widgets finden Sie unter [Verwendung und Erweiterung von Widgets](/help/sites-developing/widgets.md).

Der Webclient benötigt eine Zugriffsberechtigung auf den Knoten `cq:ClientLibraryFolder`. Sie können auch Bibliotheken aus geschützten Bereichen des Repositorys bereitstellen (siehe „Einbetten von Code aus anderen Bibliotheken“ unten).

### Überschreiben von Bibliotheken in /lib {#overriding-libraries-in-lib}

Client library folders located below `/apps` take precedence over same-named folders that are similarly located in `/libs`. Zum Beispiel `/apps/cq/ui/widgets` hat Vorrang vor `/libs/cq/ui/widgets`. When these libraries belong to the same category, the library below `/apps` is used.

### Finden eines Client-Bibliotheksordners und Verwendung des Proxy-Servlets für Client-Bibliotheken {#locating-a-client-library-folder-and-using-the-proxy-client-libraries-servlet}

In previous versions, client library folders were located below `/etc/clientlibs` in the repository. This is still supported, however it is recommended that client libraries now be located under `/apps`. This is to locate the client libraries near the other scripts, which are generally found below `/apps` and `/libs`.

>[!NOTE]
>
>Statische Ressourcen unter dem Clientbibliotheksordner müssen sich in einem Ordner mit dem Namen *resources* befinden. Wenn Sie nicht über die statischen Ressourcen, wie z. B. Bilder, in den *Ordnerressourcen* verfügen, kann auf diese nicht in einer Veröffentlichungsinstanz verwiesen werden. Hier ein Beispiel: https://localhost:4503/etc.clientlibs/geometrixx/components/clientlibs/resources/example.gif

>[!NOTE]
>
>In order to better isolate code from content and configuration, it is recommended to locate client libraries under `/apps` and expose them via `/etc.clientlibs` by leveraging the `allowProxy` property.

In order for the client libraries under `/apps` to be accessible, a proxy servelt is used. The ACLs are still enforced on the client library folder, but the servlet allows for the content to be read via `/etc.clientlibs/` if the `allowProxy` property is set to `true`.

Eine statische Ressource kann nur über den Proxy abgerufen werden, wenn sie sich unter einer Ressource unter dem Client-Bibliotheksordner befindet.

Beispiel:

* You have a clientlib in `/apps/myproject/clientlibs/foo`
* You have a static image in `/apps/myprojects/clientlibs/foo/resources/icon.png`

Then you set the `allowProxy` property on `foo` to true.

* You can then request `/etc.clientlibs/myprojects/clientlibs/foo.js`
* You can then reference the image via `/etc.clientlibs/myprojects/clientlibs/foo/resources/icon.png`

>[!CAUTION]
>
>Bei der Verwendung von Proxyclient-Bibliotheken erfordert die AEM Dispatcher-Konfiguration möglicherweise ein Update, um sicherzustellen, dass die URIs mit der Erweiterung clientlibs zulässig sind.

>[!CAUTION]
>
>Adobe recommends locating client libraries under `/apps` and making them available using the proxy servlet. However keep in mind that best practice still requires that public sites never include anything that is served directly over an `/apps` or `/libs` path.

### Erstellen eines Client-Bibliotheksordners {#create-a-client-library-folder}

1. Open CRXDE Lite in a web browser ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Wählen Sie den Ordner aus, in dem Sie den Client-Bibliotheksordner platzieren möchten, und klicken Sie auf **Erstellen > Knoten erstellen**.
1. Geben Sie einen Namen für die Bibliotheksdatei ein und wählen Sie in der Typenliste `cq:ClientLibraryFolder` aus. Klicken Sie auf **OK** und dann auf **Alle speichern**.
1. Um die Kategorien festzulegen, zu denen die Bibliothek gehört, wählen Sie den Knoten `cq:ClientLibraryFolder` aus, fügen Sie die folgende Eigenschaft hinzu und klicken Sie auf **Alle speichern**:

   * Name: categories
   * Typ: String
   * Wert: Kategoriename
   * Multi: Auswählen

1. Fügen Sie die Quelldateien auf beliebige Weise zum Bibliotheksordner hinzu. Sie können zum Beispiel einen WebDav-Client verwenden, um Dateien zu kopieren, oder eine Datei erstellen und den Inhalt manuell eingeben.

   **Hinweis:** Sie können Quelldateien bei Bedarf in Unterordnern organisieren.

1. Wählen Sie den Client-Bibliotheksordner aus und klicken Sie auf **Erstellen > Datei erstellen**.
1. Geben Sie in das Dateinamenfeld einen der folgenden Dateinamen ein und klicken Sie auf „OK“:

   * **`js.txt`:** Verwenden Sie diesen Dateinamen, um eine JavaScript-Datei zu erzeugen.
   * **`css.txt`:** Verwenden Sie diesen Dateinamen, um ein Cascading Style Sheet zu erzeugen.

1. Öffnen Sie die Datei und geben Sie den folgenden Text ein, um das Stammverzeichnis des Pfads der Quelldateien anzugeben:

   `#base=*[root]*`

   Replace * `[root]`* with the path to the folder that contains the source files, relative to the TXT file. Verwenden Sie beispielsweise den folgenden Text, wenn sich die Quelldateien im selben Ordner wie die TXT-Datei befinden:

   `#base=.`

   Der folgende Code legt den Ordner „mobile“ unter dem Knoten `cq:ClientLibraryFolder` als Stammverzeichnis fest:

   `#base=mobile`

1. On the lines below `#base=[root]`, type the paths of the source files relative to the root. Geben Sie dabei jeden Dateinamen in einer separaten Zeile ein.
1. Klicken Sie auf **Alle speichern**.

### Verknüpfung mit Abhängigkeiten {#linking-to-dependencies}

Wenn der Code in Ihrem Client-Bibliotheksordner auf andere Bibliotheken verweist, müssen Sie die anderen Bibliotheken als Abhängigkeiten angeben. Durch das JSP-Tag `ui:includeClientLib`, das Ihren Client-Bibliotheksordner referenziert, enthält der HTML-Code einen Link auf Ihre generierte Bibliotheksdatei sowie die Abhängigkeiten.

The dependencies must be another `cq:ClientLibraryFolder`. Fügen Sie Ihrem `cq:ClientLibraryFolder`-Knoten eine Eigenschaft mit den folgenden Attributen hinzu, um Abhängigkeiten anzugeben:

* **Name:** dependencies
* **Typ:** String[]
* **Werte:** Der Wert der Kategorieeigenschaft des cq:ClientLibraryFolder-Knotens, von dem der aktuelle Bibliotheksordner abhängig ist.

For example, the / `etc/clientlibs/myclientlibs/publicmain` has a dependency on the `cq.jquery` library. Die JSP, die die Haupt-Client-Bibliothek referenziert, erzeugt HTML-Code, der den folgenden Code enthält:

```xml
<script src="/etc/clientlibs/foundation/cq.jquery.js" type="text/javascript">
<script src="/etc/clientlibs/mylibs/publicmain.js" type="text/javascript">
```

### Einbetten von Code aus anderen Bibliotheken {#embedding-code-from-other-libraries}

Sie können Code aus einer Client-Bibliothek in eine andere Client-Bibliothek einbetten. Zur Laufzeit wird der Code der eingebetteten Bibliothek in die generierten JS- und CSS-Dateien der einbettenden Bibliothek eingefügt.

Das Einbetten von Code ist nützlich, um Zugriff auf Bibliotheken zu ermöglichen, die in sicheren Bereichen des Repositorys gespeichert sind.

#### Anwendungsspezifische Client-Bibliotheksordner {#app-specific-client-library-folders}

It is a best practice to keep all application-related files in their application folder below `/app`. It is also a best practice to deny access for web site visitors to the `/app` folder. To satisfy both best practices, create a client library folder below the `/etc` folder that embeds the client library that is below `/app`.

Verwenden Sie die Eigenschaft &quot;Kategorien&quot;, um den einzubettenden Clientbibliotheksordner zu identifizieren. Um die Bibliothek einzubetten, fügen Sie dem einbettenden `cq:ClientLibraryFolder`-Knoten eine Eigenschaft mit den folgenden Eigenschaftsattributen hinzu:

* **Name:** embed
* **Typ:** String[]
* **Wert:** Der Wert der Eigenschaft &quot;Kategorien&quot;des einzubettenden `cq:ClientLibraryFolder` Knotens.

#### Minimieren von Anfragen durch Einbetten {#using-embedding-to-minimize-requests}

In some cases you may find that the final HTML generated for typical page by your publish instance includes a relatively large number of `<script>` elements, particularly if your site is using client context information for analaytics or targeting. For example, in a non-optimized project you might find the following series of `<script>` elements in the HTML for a page:

```xml
<script type="text/javascript" src="/etc/clientlibs/granite/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/utils.js"></script>
<script type="text/javascript" src="/etc/clientlibs/granite/jquery/granite.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/jquery.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/shared.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/personalization/kernel.js"></script>
```

In solchen Fällen kann es nützlich sein, den gesamten benötigten Client-Bibliothekscode in einer einzelnen Datei zu kombinieren, um die Anzahl der Anfragen in beide Richtungen beim Laden einer Seite zu reduzieren. To do this you can `embed` the required libraries into you app-specific client library using the embed property of the `cq:ClientLibraryFolder` node.

Die folgenden Client-Bibliothekskategorien sind in AEM bereits vorhanden. Sie sollten nur die Kategorien einbetten, die für die Funktion Ihrer Website erforderlich sind. Sie sollten jedoch **die hier angegebene Reihenfolge einhalten**:

1. `browsermap.standard`
1. `browsermap`
1. `jquery-ui`
1. `cq.jquery.ui`
1. `personalization`
1. `personalization.core`
1. `personalization.core.kernel`
1. `personalization.clientcontext.kernel`
1. `personalization.stores.kernel`
1. `personalization.kernel`
1. `personalization.clientcontext`
1. `personalization.stores`
1. `cq.collab.comments`
1. `cq.collab.feedlink`
1. `cq.collab.ratings`
1. `cq.collab.toggle`
1. `cq.collab.forum`
1. `cq.cleditor`

#### Pfade in CSS-Dateien {#paths-in-css-files}

Wenn Sie CSS-Dateien einbetten, verwendet der generierte CSS-Code Pfade zu Ressourcen, die relativ zur einbettenden Bibliothek sind. For example, the publicly-accessible library `/etc/client/libraries/myclientlibs/publicmain` embeds the `/apps/myapp/clientlib` client library:

![screen_shot_2012-05-29at20122pm](assets/screen_shot_2012-05-29at20122pm.png)

Die Datei `main.css` enthält den folgenden Stil:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

Die CSS-Datei, die der `publicmain`-Knoten generiert, enthält den folgenden Stil mit der URL des Originalbilds:

```xml
body {
  padding: 0;
  margin: 0;
  background: url(../../../apps/myapp/clientlib/styles/images/bg-full.jpg) no-repeat center top;
  width: 100%;
}
```

### Verwenden einer Bibliothek für bestimmte Mobile-Gruppen {#using-a-library-for-specific-mobile-groups}

Verwenden Sie die Eigenschaft `channels` eines Client-Bibliotheksordners, um die Mobile-Gruppe zu identifizieren, die die Bibliothek verwendet. Die Eigenschaft `channels` ist hilfreich, wenn Bibliotheken derselben Kategorie für verschiedene Geräte entwickelt wurden.

To associate a client library folder with a device group, add a property to your `cq:ClientLibraryFolder` node with the following attributes:

* **Name:** kanal
* **Typ:** String[]
* **Werte:** Der Name der mobilen Gruppe. Um den Bibliotheksordner aus einer Gruppe auszuschließen, setzen Sie ein Ausrufezeichen („!“) vor den Namen.

For example, the following table lists the value of the `channels` property for each client library folder of the `cq.widgets` category:

| Client-Bibliotheksordner | Wert der Eigenschaft „channels“ |
|---|---|
| `/libs/cq/analytics/widgets` | `!touch` |
| `/libs/cq/analytics/widgets/themes/default` | `!touch` |
| `/libs/cq/cloudserviceconfigs/widgets` | `!touch` |
| `/libs/cq/searchpromote/widgets` | `!touch` |
| `/libs/cq/searchpromote/widgets/themes/default` | *[kein Wert]* |
| `/libs/cq/touch/widgets` | `touch` |
| `/libs/cq/touch/widgets/themes/default` | `touch` |
| `/libs/cq/ui/widgets` | `!touch` |
| `/libs/cq/ui/widgets/themes/default` | `!touch` |

## Verwendung von Präprozessoren {#using-preprocessors}

AEM allows for pluggable preprocessors and ships with support for [YUI Compressor](https://github.com/yui/yuicompressor#yui-compressor---the-yahoo-javascript-and-css-compressor) for CSS and JavaScript and [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/) for JavaScript with YUI set as AEM&#39;s default preprocessor.

Die austauschbaren Präprozessoren bieten flexible Einsatzmöglichkeiten, z. B.:

* Definition von ScriptProcessors, die Skriptquellen verarbeiten können
* Prozessoren sind mit Optionen konfigurierbar
* Prozessoren können zur Minimierung, aber auch für nicht minimierte Fälle verwendet werden
* Die clientlib kann den zu verwendenden Prozessor festlegen

>[!NOTE]
>
>Standardmäßig verwendet AEM YUI Compressor. In der [GitHub-Dokumentation zu YUI Compressor](https://github.com/yui/yuicompressor/issues) finden Sie eine Liste bekannter Probleme. Ein Wechsel zu GCC Compressor für bestimmte clientlibs kann einige Probleme beheben, die mit YUI auftreten.

>[!CAUTION]
>
>Platzieren Sie eine minimierte Bibliothek nicht in einer Client-Bibliothek. Stellen Sie stattdessen die Rohbibliothek bereit. Wenn eine Minimierung erforderlich ist, können Sie die Möglichkeiten der Präprozessoren verwenden.

### Verwendung {#usage}

Sie können die Präprozessorkonfiguration pro Client-Bibliothek oder systemweit festlegen.

* Add the multivalue properties `cssProcessor` and `jsProcessor` on the clientlibrary node

* Oder definieren Sie die standardmäßige Systemkonfiguration über die OSGi-Konfiguration im **HTML Library Manager**

Eine Vorprozessorkonfiguration auf dem Knoten clientlib hat Vorrang vor der OSGI-Konfiguration.

### Format und Beispiele {#format-and-examples}

#### Format {#format}

```xml
config:= mode ":" processorName options*;
mode:= "default" | "min";
processorName := "none" | <name>;
options := ";" option;
option := name "=" value;
```

#### YUI Compressor für CSS-Minimierung und GCC für JS {#yui-compressor-for-css-minification-and-gcc-for-js}

```xml
cssProcessor: ["default:none", "min:yui"]
jsProcessor: ["default:none", "min:gcc;compilationLevel=advanced"]
```

#### Typescript zur Vorverarbeitung und GCC zur Minimierung und Verschleierung {#typescript-to-preprocess-and-then-gcc-to-minify-and-obfuscate}

```xml
jsProcessor: [
   "default:typescript",
   "min:typescript",
   "min:gcc;obfuscate=true"
]
```

#### Weitere GCC-Optionen {#additional-gcc-options}

```xml
failOnWarning (defaults to "false")
languageIn (defaults to "ECMASCRIPT5")
languageOut (defaults to "ECMASCRIPT5")
compilationLevel (defaults to "simple") (can be "whitespace", "simple", "advanced")
```

Weitere Informationen zu GCC-Optionen finden Sie in der [GCC-Dokumentation](https://developers.google.com/closure/compiler/docs/compilation_levels).

### Festlegen des Systemstandard-Minimierers {#set-system-default-minifier}

YUI ist in AEM der Standardminimierer. Um stattdessen GCC festzulegen, führen Sie die folgenden Schritte aus.

1. Go to Apache Felix Config Manager at [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
1. Find and edit the **Adobe Granite HTML Library Manager**.
1. Aktivieren Sie die Option **Minimieren** (wenn nicht bereits aktiviert).
1. Set the value **JS Processor Default Configs** to `min:gcc`.

   Options can be passed if separated with a semicolon e.g. `min:gcc;obfuscate=true`.

1. Klicken Sie auf **Speichern**, um die Änderungen zu speichern.

## Debugging-Tools {#debugging-tools}

AEM bietet eine Vielzahl von Tools zum Debuggen und Testen von Client-Bibliotheksordnern an.

### Eingebettete Dateien anzeigen {#see-embedded-files}

Wenn Sie den Ursprung von eingebettetem Code nachvollziehen oder sicherstellen möchten, dass eingebettete Client-Bibliotheken die erwarteten Ergebnisse produzieren, können Sie die Namen der Dateien anzeigen, die zur Laufzeit eingebettet werden. Um die Dateinamen anzuzeigen, hängen Sie den Parameter `debugClientLibs=true` an die URL Ihrer Webseite an. The library that is generated contains `@import` statements instead of the embedded code.

In the example in the previous [Embedding Code From Other Libraries](/help/sites-developing/clientlibs.md#embedding-code-from-other-libraries) section, the `/etc/client/libraries/myclientlibs/publicmain` client library folder embeds the `/apps/myapp/clientlib` client library folder. Wenn Sie den Parameter an die Webseite anhängen, wird der folgende Link im Quellcode der Seite erzeugt:

```xml
<link rel="stylesheet" href="/etc/clientlibs/mycientlibs/publicmain.css">
```

Wenn Sie die Datei `publicmain.css` öffnen, sehen Sie den folgenden Code:

```xml
@import url("/apps/myapp/clientlib/styles/main.css");
```

1. Hängen Sie in der Adressleiste Ihres Webbrowsers den folgenden Text an die URL Ihres HTML-Codes an:

   `?debugClientLibs=true`
1. Öffnen Sie den Seiten-Quellcode, nachdem die Seite geladen wurde.
1. Klicken Sie auf den Link, der als href für das Link-Element angegeben ist, um die Datei zu öffnen und den Quellcode anzuzeigen.

### Ermitteln der Client-Bibliotheken {#discover-client-libraries}

The `/libs/cq/granite/components/dumplibs/dumplibs` component generates a page of information about all client library folders on the system. The `/libs/granite/ui/content/dumplibs` node has the component as a resource type. Um die Seite zu öffnen, verwenden Sie die folgende URL (d. h. den Host und Port ändern Sie nach Bedarf):

`https://<host>:<port>/libs/granite/ui/content/dumplibs.test.html`

Zu den Informationen gehören der Bibliothekspfad und -typ (CSS oder JS) und die Werte der Bibliotheksattribute, wie z. B. Kategorien und Abhängigkeiten. Nachfolgende Tabellen auf der Seite zeigen die Bibliotheken in jeder Kategorie und jedem Kanal.

### Anzeigen der generierten Ausgabe {#see-generated-output}

The `dumplibs` component includes a test selector that displays the source code that is generated for `ui:includeClientLib` tags. Die Seite enthält Code für verschiedene Kombinationen von js-, css- und themed-Attributen.

1. Wählen Sie eine der folgenden Methoden, um die Testausgabeseite zu öffnen:

   * From the `dumplibs.html` page, click the link in the **Click here for output testing** text.

   * Öffnen Sie die folgende URL in Ihrem Webbrowser (verwenden Sie je nach Bedarf einen anderen Host und Port):

      * `http://<host>:<port>/libs/granite/ui/content/dumplibs.html`

   Die Standardseite zeigt die Ausgabe für Tags ohne Wert für das category-Attribut.

1. To see the output for a category, type the value of the client library&#39;s `categories` property and click **Submit Query**.

## Konfiguration des Umgangs mit Bibliotheken für Entwicklung und Produktion {#configuring-library-handling-for-development-and-production}

Der HTML Library Manager-Service verarbeitet `cq:ClientLibraryFolder`-Tags und generiert die Bibliotheken zur Laufzeit. Vom Typ der Umgebung (Entwicklung oder Produktion) hängt ab, wie Sie den Dienst konfigurieren sollten:

* Verbesserung der Sicherheit: Debugging deaktivieren
* Verbesserung der Leistung: Freie Bereiche entfernen und Bibliotheken komprimieren.
* Lesbarkeit verbessern: Freie Bereiche beibehalten und nicht komprimieren.

Weitere Informationen zur Konfiguration des Services finden Sie unter [AEM HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md#aemhtmllibrarymanager).
