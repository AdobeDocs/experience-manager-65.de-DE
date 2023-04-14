---
title: Best Practices für SEO und URL-Verwaltung
description: Erfahren Sie mehr über Best Practices und Empfehlungen für SEO bei einer AEM Implementierung.
topic-tags: managing
content-type: reference
docset: aem65
exl-id: b138f6d1-0870-4071-b96e-4a759ad9a76e
source-git-commit: af60428255fb883265ade7b2d9f363aacb84b9ad
workflow-type: tm+mt
source-wordcount: '3678'
ht-degree: 56%

---

# Best Practices für SEO und URL-Verwaltung{#seo-and-url-management-best-practices}

SEO (Search Engine Optimization) ist für viele Marketing-Experten zu einem wichtigen Thema geworden. Daher müssen SEO-Bedenken bei vielen AEM Projekten berücksichtigt werden.

In diesem Dokument werden zunächst einige [Best Practices für SEO](#seo-best-practices) und Empfehlungen für eine AEM Implementierung. Anschließend beschäftigt sich das Dokument intensiver mit einigen der [komplexeren Implementierungsschritte](#aem-configurations) aus dem ersten Abschnitt.

## Best Practices für SEO {#seo-best-practices}

Dieser Abschnitt beschreibt einige allgemeine Best Practices für SEO

### URLs {#urls}

Es gibt einige anerkannte Best Practices für URLs.

Wenn Sie URLs für Ihr AEM-Projekt bewerten, stellen Sie sich die folgenden Fragen:

&quot;Wenn ein Benutzer diese URL und keinen Inhalt auf der Seite gesehen hat, könnte er diese Seite beschreiben?&quot;

Wenn die Antwort „ja“ lautet, ist es wahrscheinlich, dass die URL für Suchmaschinen gut funktioniert.

Im Folgenden finden Sie einige allgemeine Tipps zum Erstellen Ihrer URLs für SEO:

* Verwenden Sie Bindestriche, um Wörter zu trennen.

   * Benennen Sie Seiten mit Bindestrichen (-) als Trennzeichen.
   * Vermeiden Sie die Verwendung von Binnenmajuskeln, Unterstrichen und Leerzeichen.

* Vermeiden Sie, wenn möglich, die Verwendung von Abfrageparametern. Beschränken Sie sie bei Bedarf auf zwei oder weniger.

   * Verwenden Sie die Verzeichnisstruktur, um die Informationsarchitektur anzugeben, sofern verfügbar.
   * Wenn eine Verzeichnisstruktur keine Option ist, verwenden Sie Sling-Selektoren in der URL statt Abfragezeichenfolgen. Zusätzlich zum SEO-Wert, den sie bereitstellen, machen Sling-Selektoren Seiten auch für den Dispatcher zwischenspeicherbar.

* Je menschlesbarer eine URL ist, desto besser. Suchbegriffe, die in der URL vorhanden sind, erhöhen den Wert.

   * Bei der Verwendung von Selektoren auf einer Seite werden Selektoren bevorzugt, die semantischen Wert bieten.
   * Wenn ein Mensch Ihre URL nicht lesen kann, kann eine Suchmaschine auch nicht lesen.
   * Beispiel:
      `mybrand.com/products/product-detail.product-category.product-name.html`
wird vorgezogen gegenüber 
`mybrand.com/products/product-detail.1234.html`

* Vermeiden Sie nach Möglichkeit Subdomains, da Suchmaschinen sie als verschiedene Entitäten behandeln und so den SEO-Wert der Site fragmentieren.

   * Nutzen Sie stattdessen Unterpfade auf erster Ebene. Verwenden Sie beispielsweise `www.mybrand.com/es/home.html` statt `es.mybrand.com/home.html`.

   * Planen Sie Ihre Inhaltshierarchie entsprechend dieser Richtlinie so, dass sie der Darstellung des Inhalts entspricht.

* Die Effektivität von Keywords in URLs nimmt bei mit zunehmender Länge der URL und späterer Position des Keywords ab. Mit anderen Worten, kürzer ist besser.

   * Verwenden Sie die von AEM bereitgestellten Methoden und Funktionen zur URL-Verkürzung, um unnötige URL-Teile zu entfernen.
   * Beispiel: `mybrand.com/en/myPage.html` wird `mybrand.com/content/my-brand/en/myPage.html` vorgezogen.

* Verwenden Sie kanonische URLs.

   * Wenn eine URL von unterschiedlichen Pfaden aus oder mit unterschiedlichen Parametern oder Selektoren bedient werden kann, stellen Sie sicher, dass Sie ein Tag `rel=canonical` auf der Seite verwenden.

   * Schließen Sie kanonische URLs in den Code für die AEM ein.

* Passen Sie URLs nach Möglichkeit mit Seitentiteln an.

   * Autoren von Inhalten sollten ermutigt werden, diese Vorgehensweise zu befolgen.

* Unterstützung der Groß-/Kleinschreibung bei URL-Anfragen.

   * Konfigurieren Sie den Dispatcher so, dass alle eingehenden Anfragen in Kleinbuchstaben umgeschrieben werden.
   * Trainieren Sie Inhaltsautoren, um alle Seiten mit Kleinbuchstaben zu erstellen.

* Stellen Sie sicher, dass jede Seite nur von einem Protokoll bedient wird.

   * Manchmal werden Websites über `http` bedient, bis ein Benutzer eine Seite erreicht, die beispielsweise ein Zahlungsformular oder Anmeldeformular enthält, weswegen die Seite in das `https`-Format wechselt. Wenn der Benutzer von dieser Seite aus verlinkt wird, ob er zu `http` Seiten und deren Zugriff über `https`, verfolgt die Suchmaschine sie als zwei separate Seiten.

   * Google bevorzugt derzeit `https`-Seiten gegenüber `http`-Seiten. Sie tragen dazu bei, das Leben aller einfacher zu gestalten, um die gesamte Website über `https`.

### Server-Konfiguration {#server-configuration}

Hinsichtlich der Server-Konfiguration können Sie mit den folgenden Schritten gewährleisten, dass nur korrekte Inhalte durchsucht werden:

* Verwenden Sie eine `robots.txt`-Datei, um Crawling von nicht indizierten Inhalten zu vermeiden.

   * Block **all** Crawling in Testumgebungen.

* Implementieren Sie beim Start einer neuen Website mit aktualisierten URLs 301-Umleitungen, um sicherzustellen, dass Ihr vorhandenes SEO-Ranking nicht verloren geht.
* Fügen Sie eine Favicon für Ihre Site hinzu.
* Um Suchmaschinen das Durchsuchen Ihres Inhalts zu erleichtern, implementieren Sie eine XML-Sitemap. Stellen Sie sicher, dass eine mobile Sitemap für mobile und/oder responsive Sites enthalten ist.

## AEM-Konfigurationen {#aem-configurations}

In diesem Abschnitt werden die Implementierungsschritte zum Konfigurieren von AEM mit den folgenden SEO-Empfehlungen beschrieben.

### Verwenden von Sling-Selektoren {#using-sling-selectors}

Früher war die Verwendung von Abfrageparametern die akzeptierte Praxis bei der Erstellung einer Web-Anwendung für Unternehmen.

Der Trend der letzten Jahre bestand darin, Parameter zu entfernen, um URLs leichter lesbar zu machen. Auf vielen Plattformen umfasst dieser Löschvorgang die Implementierung von Weiterleitungen auf dem Webserver oder dem Content Delivery Network (CDN), aber Sling macht den Prozess einfach. Sling-Selektoren:

* Verbessern der URL-Lesbarkeit.
* Damit können Sie Ihre Seiten im Dispatcher zwischenspeichern und die Sicherheit verbessern.
* Ermöglicht es Ihnen, den Inhalt direkt zu adressieren, anstatt über ein generisches Servlet zu verfügen, das Inhalte abruft. Damit erhalten Sie die Vorteile von ACLs, die Sie auf Ihr Repository anwenden, sowie von Filtern, die Sie auf den Dispatcher anwenden.

#### Verwenden von Selektoren für Servlets {#using-selectors-for-servlets}

AEM bietet uns zwei Optionen beim Schreiben von Servlets:

* **bin** Servlets
* **Sling** Servlets

Die folgenden Beispiele veranschaulichen die Registrierung von Servlets, die diesen beiden Mustern folgen, und die Vorteile, die sich aus der Verwendung von Sling-Servlets ergeben.

#### Container-Servlets (eine Ebene nach unten) {#bin-servlets-one-level-down}

**Container**-Servlets folgen dem Muster, das viele Entwickler für die J2EE-Programmierung verwenden. Das Servlet wird an einem bestimmten Pfad registriert, der sich in AEM Regel unter `/bin`und Sie extrahieren die erforderlichen Anforderungsparameter aus der Abfragezeichenfolge.

Der SCR-Vermerk für diese Art von Servlet sieht in etwa so aus:

```
@SlingServlet(paths = "/bin/myApp/myServlet", extensions = "json", methods = "GET")
```

Sie extrahieren dann die Parameter aus der Abfragezeichenfolge über das `SlingHttpServletRequest`-Objekt, das beispielsweise in der `doGet`-Methode mit eingeschlossen ist:

```
String myParam = req.getParameter("myParam");
```

Die daraus resultierende URL könnte beispielsweise in etwa so aussehen:

`https://www.mydomain.com/bin/myApp/myServlet.json?myParam=myValue`

Bei diesem Ansatz sind einige Punkte zu berücksichtigen:

* Die URL selbst verliert den SEO-Wert. Benutzer, die auf die Site zugreifen, einschließlich Suchmaschinen, erhalten keinen semantischen Wert aus der URL, da die URL einen programmatischen Pfad und nicht die Inhaltshierarchie darstellt.
* Das Vorhandensein von Abfrageparametern in der URL bedeutet, dass der Dispatcher die Antwort nicht zwischenspeichern kann.
* Wenn Sie dieses Servlet sichern möchten, implementieren Sie Ihre eigene benutzerdefinierte Sicherheitslogik in das Servlet.
* Der Dispatcher muss (sorgfältig) konfiguriert werden, um `/bin/myApp/myServlet` offenzulegen. Das Freilegen von `/bin` würde Zugang zu Servlets erlauben, die nicht für Besucher der Website offen sein sollten.

#### Sling-Servlets (eine Ebene nach unten) {#sling-servlets-one-level-down}

**Sling**-Servlets ermöglichen die Registrierung von Servlets auf gegensätzliche Art und Weise. Anstatt ein Servlet zu adressieren und den Inhalt anzugeben, den das Servlet basierend auf den Abfrageparametern rendern soll, adressieren Sie den gewünschten Inhalt. Und Sie geben das Servlet an, das den Inhalt basierend auf Sling-Selektoren rendern soll.

Der SCR-Vermerk für diese Art von Servlet sieht in etwa so aus:

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json", methods="GET")
```

In diesem Fall die Ressource, an die sich die URL richtet - eine Instanz der `myPageType` resource - ist im Servlet automatisch zugänglich. Um darauf zuzugreifen, rufen Sie Folgendes auf:

```
Resource myPage = req.getResource();
```

Die daraus resultierende URL könnte beispielsweise in etwa so aussehen:

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

Die Vorteile dieses Ansatzes sind:

* Sie können den SEO-Wert, gewonnen durch die Semantik in Ihrer Site-Hierarchie und im Seitennamen, backen.
* Da keine Abfrageparameter vorhanden sind, kann der Dispatcher die Antwort zwischenspeichern. Auch machen jegliche Updates der adressierten Seite diesen Cache ungültig, wenn die Seite aktiviert wird.
* Alle auf `/content/my-brand/my-page` angewandten ACLs werden aktiv, wenn ein Benutzer versucht, auf dieses Servlet zuzugreifen.
* Der Dispatcher ist bereits so konfiguriert, dass dieser Inhalt als Funktion der Bereitstellung der Website bereitgestellt wird. Es ist keine zusätzliche Konfiguration erforderlich.

### Umschreiben der URL {#url-rewriting}

In AEM werden all Ihre Websites unter `/content/my-brand/my-content` gespeichert. Dieser Speicherort ist zwar aus Sicht der Repository-Datenverwaltung nützlich, Sie möchten jedoch nicht unbedingt, dass Ihre Kunden Ihre Site sehen. Und es kann im Widerspruch zu den SEO-Richtlinien stehen, URLs so kurz wie möglich zu halten. Überdies kann es sein, dass Sie mehrere Websites von derselben AEM-Instanz und zwei unterschiedlichen Domain-Namen aus bedienen.

Dieser Abschnitt erläutert die verfügbaren AEM-Optionen zum Verwalten und zur Präsentation dieser URLs gegenüber dem Benutzer auf leichter lesbare, SEO-freundliche Weise.

#### Vanity-URLs {#vanity-urls}

Wenn ein Autor wünscht, dass die Seite von einem zweiten Ort aus für Werbezwecke zugänglich ist, können die auf Seitenbasis definierten Vanity-URLs von AEM nützlich sein. Um einer Seite eine Vanity-URL hinzuzufügen, rufen Sie sie in der Konsole **Sites** auf und bearbeiten Sie die Seiteneigenschaften. Unten auf der Registerkarte **Allgemein** sehen Sie einen Abschnitt, dem Vanity-URLs hinzugefügt werden können. Bedenken Sie, dass die Zugänglichkeit einer Seite über mehr als eine URL den SEO-Wert der Seite fragmentiert. Der Seite sollte also ein kanonisches URL-Tag hinzugefügt werden, um dieses Problem zu vermeiden.

#### Lokalisierte Seitennamen {#localized-page-names}

Vielleicht möchten Sie den Benutzern von übersetzten Inhalten lokalisierte Seitennamen anzeigen. Beispiel:

* Anstatt einen Spanisch sprechenden Benutzer zur folgenden URL zu leiten:
   `www.mydomain.com/es/home.html`

* wäre folgende URL besser:
   `www.mydomain.com/es/casa.html`.

Die Herausforderung bei der Lokalisierung des Seitennamens besteht darin, dass viele der auf der AEM Plattform verfügbaren Lokalisierungs-Tools darauf angewiesen sind, dass die Seitennamen in allen Sprachen übereinstimmen, damit die Inhalte synchronisiert bleiben.

Die `sling:alias` -Eigenschaft ermöglicht es Ihnen, Adobe-Kuchen zu essen. Sie können `sling:alias` als Eigenschaft zu einer beliebigen Ressource, um einen Alias für die Ressource zu ermöglichen. Im vorherigen Beispiel hätten Sie Folgendes:

* Eine Seite im JCR unter:
   `…/es/home`

* Dieser fügen Sie dann eine Eigenschaft hinzu:
   `sling:alias` = `casa`

Dieser Ablauf ermöglicht es den AEM Übersetzungs-Tools wie dem Multi-Site-Manager, weiterhin eine Beziehung zwischen folgenden Seiten zu pflegen:

* `/en/home`

* `/es/home`

während es Benutzern ermöglicht wird, in ihrer Muttersprache mit dem Seitennamen zu interagieren.

>[!NOTE]
>
>Die `sling:alias`-Eigenschaft kann [beim Bearbeiten der Seiteneigenschaften mithilfe der Alias-Eigenschaft](/help/sites-authoring/editing-page-properties.md#advanced) festgelegt werden.

#### /etc/map {#etc-map}

Bei der Standardinstallation von AEM:

* für die OSGi-Konfiguration
   **Apache Sling Resource Resolver Factory**
( 
`org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl`)

* ist der Standardwert der Eigenschaft
   **Zuordnungsspeicherort** ( `resource.resolver.map.location`)

* ist standardmäßig auf `/etc/map` eingestellt.

Zuordnungsdefinitionen können in diesem Verzeichnis hinzugefügt werden, um eingehende Anfragen zuzuordnen, URLs auf Seiten in AEM umzuschreiben oder beides.

Um eine neue Zuordnung zu erstellen, erstellen Sie einen neuen Knoten `sling:Mapping` an diesem Speicherort unter `/http` oder `/https`. Basierend auf den Eigenschaften `sling:match` und `sling:internalRedirect`, die für diesen Knoten eingestellt sind, leitet AEM sämtlichen Traffic für die passende URL an den in der Eigenschaft `internalRedirect` spezifizierten Wert weiter.

Während dieser Ansatz in der offiziellen AEM und der Sling-Dokumentation dokumentiert ist, ist die von dieser Implementierung bereitgestellte Unterstützung für reguläre Ausdrücke im Vergleich zu den Optionen, die mit der `SlingResourceResolver` direkt. Außerdem kann diese Art der Implementierung von Zuordnungen zu Problemen mit der Invalidierung des Dispatcher-Caches führen.

Ein Beispiel dafür, wie dieses Problem auftritt:

1. Ein Besucher fordert auf Ihrer Website `https://www.mydomain.com/my-page.html` an.
1. Der Dispatcher leitet diese Anfrage an den Veröffentlichungs-Server weiter.
1. Der Veröffentlichungs-Server verwendet `/etc/map`, löst die Anfrage zu `/content/my-brand/my-page` auf und rendert die Seite.

1. Der Dispatcher speichert die Antwort unter `/my-page.html` und gibt die Antwort an den Benutzer zurück.
1. Ein Inhaltsautor ändert diese Seite und aktiviert sie.
1. Der Flush-Agent des Dispatchers sendet eine Anfrage zur Invalidierung von `/content/my-brand/my-page`**.** Da der Dispatcher unter diesem Pfad keine Seite zwischengespeichert hat, bleibt der alte Inhalt zwischengespeichert und ist veraltet.

Es gibt Möglichkeiten, benutzerdefinierte Dispatch-Flush-Regeln zu konfigurieren, welche die kürzere URL zur Invalidierung des Caches der längeren URL zuordnen.

Es gibt jedoch auch eine einfachere Möglichkeit, dieses Problem zu beheben:

1. **SlingResourceResolver-Regeln**

   Mithilfe der Webkonsole (z. B. localhost:4502/system/console/configMgr) können Sie den Sling Resource Resolver konfigurieren:

   * **Apache Sling Resource Resolver Factory**

      `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.
   Adobe empfiehlt, die zum Verkürzen von URLs als reguläre Ausdrücke erforderlichen Zuordnungen zu erstellen und diese Konfigurationen dann unter einem OsgiConfignod zu definieren. `config.publish` , die in Ihrem Build enthalten ist.

   Anstatt Zuordnungen in `/etc/map` zu definieren, können diese direkt den Eigenschaften der **URL-Zuordnungen** (`resource.resolver.mapping`) zugeordnet werden:

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   In diesem einfachen Beispiel entfernen Sie `/content/my-brand/` von der Position am Anfang einer beliebigen URL.

   Er konvertiert eine URL:

   * von `/content/my-brand/my-page.html`
   * in `/my-page.html`

   Diese Konversion entspricht der empfohlenen Vorgehensweise, URLs so kurz wie möglich zu halten.

1. **Zuordnen der URL-Ausgabe auf Seiten**

   Nachdem Sie Ihre Zuordnungen im Apache Sling Resource Resolver definiert haben, verwenden Sie diese Zuordnungen in Ihren Komponenten, um sicherzustellen, dass die URLs, die Sie auf Ihren Seiten ausgeben, kurz und ordentlich sind. Sie können dieses Hosting mithilfe der Zuordnungsfunktion der `ResourceResolver`.

   Wenn Sie beispielsweise eine benutzerdefinierte Navigationskomponente implementieren, welche die untergeordneten Elemente der aktuellen Seite auflistet, können Sie die Zuordnungsmethode wie folgt verwenden:

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Apache HTTP-Server mod_rewrite {#apache-http-server-mod-rewrite}

Bisher haben Sie Zuordnungen zusammen mit der Logik in Ihren Komponenten implementiert, um diese Zuordnungen bei der Ausgabe von URLs auf Seiten zu verwenden.

Das letzte Teil des Puzzles besteht darin, diese gekürzten URLs zu verwalten, wenn sie beim Dispatcher ankommen, wobei `mod_rewrite` ins Spiel kommt. Der größte Vorteil bei der Verwendung von `mod_rewrite` besteht darin, dass die URLs zurück in ihre lange Form gebracht werden, *bevor* sie an das Dispatcher-Modul gesendet werden. Dieser Ablauf bedeutet, dass der Dispatcher die lange URL vom Veröffentlichungsserver anfordert und sie entsprechend zwischenspeichert. Daher können alle Dispatcher-Flush-Anfragen, die vom Veröffentlichungsserver eingehen, diesen Inhalt erfolgreich ungültig machen.

Um diese Regeln zu implementieren, können Sie `RewriteRule`-Elemente unter Ihrem virtuellen Host in der Apache HTTP Server-Konfiguration hinzufügen. Wenn Sie gekürzte URLs aus dem vorherigen Beispiel erweitern möchten, können Sie eine Regel implementieren, die folgendermaßen aussieht:

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Kanonische URL-Tags {#canonical-url-tags}

Kanonische URL-Tags sind Link-Tags, die in der Kopfzeile des HTML-Dokuments eingegeben werden und festlegen, wie Suchmaschinen die Seite bei der Indizierung des Inhalts behandeln sollen. Der Vorteil, den sie bieten, besteht darin, dass sichergestellt wird, dass eine Seite (verschiedene Versionen davon) auf gleiche Weise indiziert wird, auch wenn die auf die Seite verweisende URL Unterschiede enthält.

Bietet eine Website beispielsweise eine druckfreundliche Version einer Seite an, könnte eine Suchmaschine diese Seite getrennt von der regulären Version der Seite indizieren. Das kanonische Tag teilt der Suchmaschine mit, dass es sich um dieselbe Seite handelt.

Beispiele:

* `https://www.mydomain.com/my-brand/my-page.html`
* `https://www.mydomain.com/my-brand/my-page.print.html`

Bei beiden würde das folgende Tag der Kopfzeile der Seite hinzugefügt:

```xml
<link rel="canonical" href="my-brand/my-page.html"/>
```

Das `href`-Attribut kann relativ oder absolut sein. Der Code sollte im Seiten-Layout inbegriffen sein, um die kanonische URL und das Ausgabe-Tag zu bestimmen.

### Konfigurieren des Dispatchers für das Ignorieren von Groß- und Kleinschreibung {#configuring-the-dispatcher-for-case-insensitivity}

Die Best Practice besteht darin, alle Seiten mit Kleinbuchstaben zu bedienen. Sie möchten jedoch nicht, dass ein Benutzer einen 404-Wert erhält, wenn er mithilfe von Großbuchstaben in seiner URL auf Ihre Website zugreift. Aus diesem Grund empfiehlt Adobe, dass Sie eine Umschreiberegel in der Apache HTTP Server-Konfiguration hinzufügen, um alle eingehenden URLs in Kleinbuchstaben darzustellen. Darüber hinaus müssen Autoren dahingehend geschult werden, Seiten nur mit Namen in Kleinbuchstaben zu erstellen.

Um Apache so zu konfigurieren, dass sämtlicher eingehender Traffic in Kleinbuchstaben erfolgt, fügen Sie der Konfiguration `vhost` Folgendes hinzu:

```xml
RewriteEngine On
RewriteMap lowercase int:tolower
```

Fügen Sie zusätzlich Folgendes am Anfang der Datei `htaccess` hinzu:

```xml
RewriteCond $1 [A-Z]
RewriteRule ^(.*)$ /${lowercase:$1} [R=301,L]
```

### Implementieren von robots.txt zum Schutz von Entwicklungsumgebungen {#implementing-robots-txt-to-protect-development-environments}

Suchmaschinen *sollten* das Vorhandensein einer Datei `robots.txt` im Stammverzeichnis der Website überprüfen, bevor die Website durchsucht wird. Während große Suchmaschinen wie Google, Yahoo oder Bing diese Datei respektieren, ist dies bei einigen ausländischen Suchmaschinen nicht der Fall.

Die einfachste Möglichkeit, den Zugang zu der gesamten Website zu blockieren, ist eine Datei namens `robots.txt` im Stammverzeichnis der Website zu platzieren, die Folgendes enthält:

```xml
User-agent: *
Disallow: /
```

Wahlweise können Sie in einer Live-Umgebung bestimmte Pfade ablehnen, die nicht indiziert werden sollen.

Der Nachteil bei der Platzierung der `robots.txt` -Datei im Stammverzeichnis der Site ist, dass Dispatcher-Flush-Anfragen diese Datei löschen können. Außerdem platzieren URL-Zuordnungen wahrscheinlich den Site-Stamm an einem anderen Ort als dem `DOCROOT` wie in der Apache HTTP Server-Konfiguration definiert. Aus diesem Grund ist es üblich, diese Datei in der Autoreninstanz am Site-Stamm zu platzieren und sie in der Veröffentlichungsinstanz zu replizieren.

### Erstellen einer XML-Sitemap in AEM {#building-an-xml-sitemap-on-aem}

Crawler verwenden XML-Sitemaps, um die Website-Strukturen besser zu verstehen. Auch wenn es keine Garantie dafür gibt, dass die Bereitstellung einer Sitemap zu verbesserten SEO-Rankings führt, ist dies dennoch eine allgemein anerkannte Best Practice. Sie können eine XML-Datei auf dem Webserver manuell verwalten, um sie als Sitemap zu verwenden. Adobe empfiehlt jedoch, die Sitemap programmatisch zu generieren, um sicherzustellen, dass die Sitemap beim Erstellen von Inhalten automatisch deren Änderungen widerspiegelt.

AEM verwendet das [Apache Sling Sitemap-Modul](https://github.com/apache/sling-org-apache-sling-sitemap), um XML-Sitemaps zu generieren, die Entwicklern und Bearbeitern eine Vielzahl von Optionen zur Verfügung stellen, um die XML-Sitemap einer Website auf dem neuesten Stand zu halten.

>[!NOTE]
>
>Als Produktfunktion seit Adobe Experience Manager-Version 6.5.11.0 verfügbar.
> 
>Bei älteren Versionen können Sie ein Sling-Servlet selbst registrieren, um auf eine `sitemap.xml` aufrufen. Verwenden Sie die über die Servlet-API bereitgestellte Ressource, um die aktuelle Seite und ihre untergeordneten Elemente zu suchen und eine `sitemap.xml` -Datei.

Das Apache Sling Sitemap-Modul unterscheidet zwischen einer Top-Level-Sitemap und einer verschachtelten Sitemap, die beide für jede Ressource erzeugt werden, bei der die Eigenschaft `sling:sitemapRoot` auf `true` gesetzt ist. Im Allgemeinen werden Sitemaps mithilfe von Selektoren im Pfad der Top-Level-Sitemap der Baumstruktur gerendert, bei der es sich um die Ressource handelt, die keinen anderen Sitemap-Stamm-Vorgänger hat. Dieser Stamm der Top-Level-Sitemap legt auch den Sitemap-Index offen, der normalerweise von einem Website-Verantwortlichen im Konfigurationsportal der Suchmaschine konfiguriert oder zur Datei `robots.txt` der Site hinzugefügt wird.

Nehmen wir zum Beispiel eine Website, die den Stamm einer Top-Level-Sitemap bei `my-page` und den Stamm einer verschachtelten Sitemap bei `my-page/news` definiert, um eine eigene Sitemap für die Seiten im Teilbaum Nachrichten zu erstellen. Die resultierenden, relevanten URLs wären

* `https://www.mydomain.com/my-brand/my-page.sitemap-index.xml`
* `https://www.mydomain.com/my-brand/my-page.sitemap.xml`
* `https://www.mydomain.com/my-brand/my-page.sitemap.news-sitemap.html`

>[!NOTE]
>
>Die Selektoren `sitemap` und `sitemap-index` können bei benutzerdefinierten Implementierungen zu Problemen führen. Wenn Sie die Produktfunktion nicht verwenden möchten, konfigurieren Sie Ihr eigenes Servlet, das diese Selektoren mit einem `service.ranking` größer als 0 bedient.

In der Standardkonfiguration bietet das Dialogfeld Seiteneigenschaften die Option, eine Seite als Sitemap-Stammordner zu markieren und so wie oben beschrieben, eine Sitemap für sich selbst und die untergeordneten Elemente zu generieren. Dieses Verhalten wird durch Implementierungen der `SitemapGenerator`-Schnittstelle implementiert und kann durch Hinzufügen alternativer Implementierungen erweitert werden. Da jedoch die Häufigkeit, mit der die XML-Sitemaps neu generiert werden, von den Content-Authoring-Workflows und -Workloads abhängt, werden keine `SitemapScheduler` Konfiguration. Dadurch wird die Funktion effektiv zum Opt-in.

Um den Hintergrundauftrag zu aktivieren, der die XML-Sitemaps generiert, muss ein `SitemapScheduler` muss konfiguriert werden. Erstellen Sie dazu eine OSGi-Konfiguration für die PID `org.apache.sling.sitemap.impl.SitemapScheduler`. Der Planungsausdruck `0 0 0 * * ?` kann als Ausgangspunkt verwendet werden, um alle XML-Sitemaps einmal täglich um Mitternacht neu zu erzeugen.

![Apache Sling Sitemap – Planung](assets/sling-sitemap-scheduler.png)

Der Sitemap-Generierungsauftrag kann sowohl auf Autoren- als auch auf Veröffentlichungsebeneninstanzen ausgeführt werden. Normalerweise wird empfohlen, die Generierung auf Instanzen der Veröffentlichungsstufe auszuführen, da ordnungsgemäße kanonische URLs nur dort generiert werden können (da die Sling Resource Mapping-Regeln normalerweise nur auf Instanzen der Veröffentlichungsstufe vorhanden sind). Es ist jedoch möglich, eine benutzerdefinierte Implementierung des Externalisierungsmechanismus einzubinden, der zum Generieren der kanonischen URLs verwendet wird, indem die [SitemapLinkExternalizer](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/sitemap/externalizer/SitemapLinkExternalizer.html) -Schnittstelle. Wenn eine benutzerdefinierte Implementierung die kanonischen URLs einer Sitemap auf den Instanzen der Autorenstufe generieren kann, wird die `SitemapScheduler` kann für den Autorenausführungsmodus konfiguriert werden. Außerdem kann die Arbeitslast der XML-Sitemap-Generierung auf die Instanzen des Autorendienstclusters verteilt werden. In diesem Szenario muss Vorsicht bei der Bearbeitung von Inhalten gelten, die noch nicht veröffentlicht, geändert oder nur für eine begrenzte Benutzergruppe sichtbar sind.

AEM Sites enthält eine Standardimplementierung eines `SitemapGenerator`, der durch einen Seitenbaum navigiert, um eine Sitemap zu generieren. Er ist so vorkonfiguriert, dass nur die kanonischen URLs einer Site und ggf. Sprachalternativen ausgegeben werden. Er kann bei Bedarf auch so konfiguriert werden, dass er das Datum der letzten Änderung einer Seite enthält. Aktivieren Sie dazu die _Zuletzt geändert hinzufügen_ der _Adobe AEM SEO - Seitenstruktur Sitemap Generator_ Konfiguration und Auswahl einer _Zuletzt geänderte Quelle_. Wenn die Sitemaps auf der Veröffentlichungsebene erstellt werden, wird empfohlen, das Datum `cq:lastModified` zu verwenden.

![Konfiguration von Adobe AEM SEO - Page Tree Sitemap Generator](assets/sling-sitemap-pagetreegenerator.png)

Um den Inhalt einer Sitemap zu begrenzen, können bei Bedarf die folgenden Service-Schnittstellen implementiert werden:

* der [SitemapPageFilter](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/sitemap/SitemapPageFilter.html) kann implementiert werden, um Seiten aus XML-Sitemaps zu entfernen, die vom AEM Sites-spezifischen Sitemap-Generator erzeugt wurden
* ein [SitemapProductFilter](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/sitemap/SitemapProductFilter.html) oder [SitemapCategoryFilter](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/sitemap/SitemapCategoryFilter.html) kann implementiert werden, um Produkte oder Kategorien aus XML-Sitemaps herauszufiltern, die von den für [Commerce-Integrations-Frameworks](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/home.html?lang=de) spezifischen Sitemap-Generatoren erzeugt wurden.

Wenn die Standardimplementierungen in einem bestimmten Anwendungsfall nicht funktionieren oder die Erweiterungspunkte nicht flexibel genug sind, implementieren Sie eine benutzerdefinierte `SitemapGenerator` um die volle Kontrolle über den Inhalt einer generierten Sitemap zu übernehmen. Im folgenden Beispiel wird die standardmäßige Implementierungslogik für AEM Sites verwendet. Dabei wird der [ResourceTreeSitemapGenerator](https://javadoc.io/doc/org.apache.sling/org.apache.sling.sitemap/latest/org/apache/sling/sitemap/spi/generator/ResourceTreeSitemapGenerator.html) als Ausgangspunkt verwendet, um einen Seitenbaum zu durchlaufen:

```
import java.util.Optional;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.sitemap.SitemapException;
import org.apache.sling.sitemap.builder.Sitemap;
import org.apache.sling.sitemap.builder.Url;
import org.apache.sling.sitemap.spi.common.SitemapLinkExternalizer;
import org.apache.sling.sitemap.spi.generator.ResourceTreeSitemapGenerator;
import org.apache.sling.sitemap.spi.generator.SitemapGenerator;
import org.jetbrains.annotations.NotNull;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.adobe.aem.wcm.seo.sitemap.PageTreeSitemapGenerator;
import com.day.cq.wcm.api.Page;

@Component(
    service = SitemapGenerator.class,
    property = { "service.ranking:Integer=20" }
)
public class SitemapGeneratorImpl extends ResourceTreeSitemapGenerator {

    private static final Logger LOG = LoggerFactory.getLogger(SitemapGeneratorImpl.class);

    @Reference
    private SitemapLinkExternalizer externalizer;
    @Reference
    private PageTreeSitemapGenerator defaultGenerator;

    @Override
    protected void addResource(@NotNull String name, @NotNull Sitemap sitemap, Resource resource) throws SitemapException {
        Page page = resource.adaptTo(Page.class);
        if (page == null) {
            LOG.debug("Skipping resource at {}: not a page", resource.getPath());
            return;
        }
        String location = externalizer.externalize(resource);
        Url url = sitemap.addUrl(location + ".html");
        // add any additional content to the Url like lastmod, change frequency, etc
    }

    @Override
    protected final boolean shouldFollow(@NotNull Resource resource) {
        return super.shouldFollow(resource)
            && Optional.ofNullable(resource.adaptTo(Page.class)).map(this::shouldFollow).orElse(Boolean.TRUE);
    }

    private boolean shouldFollow(Page page) {
        // add additional conditions to stop traversing some pages
        return !defaultGenerator.isProtected(page);
    }

    @Override
    protected final boolean shouldInclude(@NotNull Resource resource) {
        return super.shouldInclude(resource)
            && Optional.ofNullable(resource.adaptTo(Page.class)).map(this::shouldInclude).orElse(Boolean.FALSE);
    }

    private boolean shouldInclude(Page page) {
        // add additional conditions to stop including some pages
        return defaultGenerator.isPublished(page)
            && !defaultGenerator.isNoIndex(page)
            && !defaultGenerator.isRedirect(page)
            && !defaultGenerator.isProtected(page);
    }
}
```

Darüber hinaus kann die für XML-Sitemaps implementierte Funktionalität auch in verschiedenen Nutzungsszenarien verwendet werden, z. B. um den kanonischen Link oder die Sprachalternativen zum Seiten-Header hinzuzufügen. Siehe [SeoTags](https://javadoc.io/doc/com.adobe.cq.wcm/com.adobe.aem.wcm.seo/latest/com/adobe/aem/wcm/seo/SeoTags.html) -Schnittstelle für weitere Informationen.

### Erstellen von 301-Weiterleitungen für veraltete URLs {#creating-redirects-for-legacy-urls}

Beim Start einer Website mit einer neuen Struktur ist die Implementierung und Prüfung von 301-Weiterleitungen in Apache HTTP Server aus zwei Gründen wichtig:

* Die veralteten URLs bauen über die Zeit hinweg SEO-Wert auf. Durch Implementierung einer Umleitung kann die Suchmaschine diesen Wert auf die neue URL anwenden.
* Benutzer der Website könnten Lesezeichen für diese Seiten erstellt haben. Durch Implementierung von Umleitungen können Sie sicherstellen, dass der Benutzer auf die Seite auf der neuen Site geleitet wird, die am ehesten dem entspricht, wo er versucht hat, auf die alte Site zu gelangen.

Werfen Sie einen Blick in den Abschnitt mit zusätzlichen Ressourcen, der Anleitungen zur Implementierung von Weiterleitungen des Typs 301 sowie ein Werkzeug zum Testen der Weiterleitung enthält.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen finden Sie in den folgenden zusätzlichen Ressourcen:

* [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md)
* [https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url](https://moz.com/blog/seo-cheat-sheet-anatomy-of-a-url)
* [https://moz.com/blog/15-seo-best-practices-for-structuring-urls](https://moz.com/blog/15-seo-best-practices-for-structuring-urls)
* [https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/](https://mysiteauditor.com/blog/top-10-most-important-seo-tips-for-url-optimization/)
* [https://sling.apache.org/documentation/the-sling-engine/servlets.html](https://sling.apache.org/documentation/the-sling-engine/servlets.html)
* [https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
* [https://httpd.apache.org/docs/current/mod/mod_rewrite.html](https://httpd.apache.org/docs/current/mod/mod_rewrite.html)
* [https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps](https://moz.com/blog/canonical-url-tag-the-most-important-advancement-in-seo-practices-since-sitemaps)
* [https://www.robotstxt.org/robotstxt.html](https://www.robotstxt.org/robotstxt.html)
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)
