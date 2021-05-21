---
title: Best Practices für SEO und URL-Verwaltung
seo-title: Best Practices für SEO und URL-Verwaltung
description: Erfahren Sie mehr über Best Practices für SEO und Empfehlungen zu deren Erreichung bei einer AEM-Implementierung.
seo-description: Erfahren Sie mehr über Best Practices für SEO und Empfehlungen zu deren Erreichung bei einer AEM-Implementierung.
uuid: 943e76c4-bd88-4b52-bb43-db375eb89d23
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 7c8f2cec-870b-41a8-8d98-70e29b495587
docset: aem65
exl-id: b138f6d1-0870-4071-b96e-4a759ad9a76e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3119'
ht-degree: 100%

---

# Best Practices für SEO und URL-Verwaltung{#seo-and-url-management-best-practices}

Suchmaschinenoptimierung (SEO) ist zu einem wichtigen Thema für viele Marketer geworden. Deshalb müssen SEO-Thematiken bei vielen AEM-Projekten berücksichtigt werden.

Dieses Dokument beschreibt zunächst einige [Best Practices für SEO](#seo-best-practices) und Empfehlungen zu deren Erreichung bei einer AEM-Implementierung. Anschließend beschäftigt sich das Dokument intensiver mit einigen der [komplexeren Implementierungsschritte](#aem-configurations) aus dem ersten Abschnitt.

## Best Practices für SEO  {#seo-best-practices}

Dieser Abschnitt beschreibt einige allgemeine Best Practices für SEO

### URLs  {#urls}

Hinsichtlich URLs bestehen einige allgemein akzeptierte Best Practices.

Wenn Sie URLs für Ihr AEM-Projekt bewerten, stellen Sie sich die folgenden Fragen:

„Wäre ein Benutzer in der Lage zu beschreiben, worum es auf der Seite geht, wenn er nur die URL und nicht den Inhalt der Seite sähe?“

Wenn die Antwort „ja“ lautet, ist es wahrscheinlich, dass die URL für Suchmaschinen gut funktioniert.

Im Folgenden finden Sie einige allgemeine Tipps zum Erstellen von URLs für SEO:

* Verwenden Sie Bindestriche, um Wörter voneinander zu trennen.

   * Verwenden Sie Bindestriche (-) als Trenner zwischen Seitennamen.
   * Vermeiden Sie Binnenmajuskeln, Unterstriche und Leerzeichen.

* Vermeiden Sie, wenn möglich, die Verwendung von Abfrageparametern. Falls erforderlich, begrenzen Sie diese auf maximal zwei.

   * Verwenden Sie eine Verzeichnisstruktur, um die Informationsarchitektur, falls vorhanden, darzustellen.
   * Wenn eine Verzeichnisstruktur keine Option ist, verwenden Sie Sling-Selektoren anstelle von Abfragefolgen. Zusätzlich zu den gebotenen SEO-Vorteilen ermöglichen Sling-Selektoren dem Dispatcher außerdem die Zwischenspeicherung der Seiten.

* Je leichter es für Menschen ist, die URL zu lesen, desto besser. Die Verwendung von Keywords in der URL macht diese wertvoller.

   * Selektoren, die einen semantischen Wert bieten, sind auf Seiten, die Selektoren verwenden, zu bevorzugen.
   * Wenn ein Mensch Ihre URL nicht lesen kann, kann eine Suchmaschine das auch nicht.
   * Beispiel:

      `mybrand.com/products/product-detail.product-category.product-name.html`
wird vorgezogen gegenüber 
`mybrand.com/products/product-detail.1234.html`

* Vermeiden Sie Sub-Domains wo möglich, da Suchmaschinen diese als unterschiedliche Einheiten einordnen und so den SEO-Wert der Website fragmentieren.

   * Nutzen Sie stattdessen Unterpfade auf erster Ebene. Verwenden Sie beispielsweise `www.mybrand.com/es/home.html` statt `es.mybrand.com/home.html`.

   * Planen Sie die Inhaltshierarchie passend zur der Art und Weise, wie die Inhalte dargestellt werden, gemäß dieser Richtlinie.

* Die Effektivität von Keywords in URLs nimmt bei mit zunehmender Länge der URL und späterer Position des Keywords ab. Anders ausgedrückt, kürzer ist besser.

   * Nutzen Sie die von AEM zur Verfügung gestellten Techniken und Funktionen zum Kürzen von URLs, um unnötige URL-Elemente zu entfernen.
   * Beispiel: `mybrand.com/en/myPage.html` wird `mybrand.com/content/my-brand/en/myPage.html` vorgezogen.

* Verwenden Sie kanonische URLs.

   * Wenn eine URL von unterschiedlichen Pfaden aus oder mit unterschiedlichen Parametern oder Selektoren bedient werden kann, stellen Sie sicher, dass Sie ein Tag `rel=canonical` auf der Seite verwenden.

   * Dieses kann im Code für die AEM-Vorlage enthalten sein.

* Passen Sie URLs wann immer möglich an Seitentitel an.

   * Inhaltsautoren sollten dazu ermutigt werden, diese Praxis zu befolgen.

* Unterstützen Sie das Ignorieren von Groß- und Kleinschreibung in URL-Anfragen.

   * Konfigurieren Sie den Dispatcher so, dass alle eingehenden Anfragen in Kleinbuchstaben umgeschrieben werden.
   * Schulen Sie die Autoren darin, sämtliche Seiten mit Kleinbuchstaben zu erstellen.

* Stellen Sie sicher, dass jede Seite nur von einem Protokoll bedient wird.

   * Manchmal werden Websites über `http` bedient, bis ein Benutzer eine Seite erreicht, die beispielsweise ein Zahlungsformular oder Anmeldeformular enthält, weswegen die Seite in das `https`-Format wechselt. Wenn von dieser Seite aus verlinkt wird und der Benutzer auf `http`-Seiten zurückkehren und auf diese über `https` zugreifen kann, verfolgt die Suchmaschine diese als zwei getrennte Seiten.

   * Google bevorzugt derzeit `https`-Seiten gegenüber `http`-Seiten. Aus diesem Grund ist es häufig für alle Beteiligten einfacher, die ganze Website über `https` zu bedienen.

### Server-Konfiguration {#server-configuration}

Hinsichtlich der Server-Konfiguration können Sie mit den folgenden Schritten gewährleisten, dass nur korrekte Inhalte durchsucht werden:

* Verwenden Sie eine `robots.txt`-Datei, um Crawling von nicht indizierten Inhalten zu vermeiden.

   * Blockieren Sie **sämtliches** Crawling in den Testumgebungen.

* Richten Sie beim Launch einer neuen Website mit aktualisierten URLs eine 301-Weiterleitung ein, um sicherzustellen, dass das derzeitige SEO-Ranking nicht verloren geht.
* Fügen Sie der Website ein Favicon hinzu.
* Implementieren Sie eine XML-Sitemap, um Suchmaschinen das Durchsuchen des Inhalts zu erleichtern. Sorgen Sie dafür, dass mobile und/oder responsive Sites über eine mobile Sitemap verfügen.

## AEM-Konfigurationen {#aem-configurations}

In diesem Abschnitt werden die notwendigen Implementierungsschritte für die AEM-Konfiguration zur Befolgung dieser SEO-Empfehlungen erläutert.

### Verwenden von Sling-Selektoren {#using-sling-selectors}

Früher war die Verwendung von Abfrageparametern allgemein akzeptierte Praxis bei der Erstellung einer Web-Anwendung für Unternehmen.

In den letzten Jahren geht der Trend jedoch dahin, diese zu entfernen, um URLs lesbarer zu gestalten. Bei vielen Plattform beinhaltet dies die Einführung von Weiterleitungen auf dem Webserver oder dem Content Delivery Network (CDN), Sling macht dies jedoch zu einem geradlinigeren Prozess. Sling-Selektoren:

* verbessern die Lesbarkeit der URL;
* ermöglichen es, die Seiten auf dem Dispatcher zwischenzuspeichern, was häufig die Sicherheit erhöht;
* ermöglichen es, Inhalte direkt zu bearbeiten, anstelle der Verwendung eines allgemeinen Servlets zur Inhaltsabfrage. Dadurch erhalten Sie die Vorteile von ACLs, die Sie auf das Repository anwenden, und Filter, die Sie für den Dispatcher verwenden.

#### Verwenden von Selektoren für Servlets   {#using-selectors-for-servlets}

AEM bietet uns zwei Optionen zum Schreiben von Servlets:

* **Container**-Servlets;
* **Sling**-Servlets.

Das folgende Beispiel zeigt, wie diesen beiden Mustern folgende Servlets registriert werden, sowie den Vorteil, der durch die Verwendung von Sling-Servlets erzielt wird.

#### Container-Servlets (eine Ebene nach unten)   {#bin-servlets-one-level-down}

**Container**-Servlets folgen dem Muster, das viele Entwickler für die J2EE-Programmierung verwenden. Das Servlet wird an einem bestimmten Punkt des Pfades registriert, was im Falle von AEM häufig unter `/bin` geschieht, und Sie extrahieren die erforderlichen Abfrageparameter aus der Abfragezeichenfolge.

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

Es gibt einige Aspekte, die bei diesem Ansatz berücksichtigt werden sollten:

* Die URL selbst verliert an SEO-Wert. Die auf die Website zugreifenden Benutzer, einschließlich Suchmaschinen, erhalten keinerlei semantischen Wert von der URL, da die URL einen Programmierungspfad darstellt und nicht die Inhaltshierarchie.
* Die Anwesenheit von Abfrageparametern in der URL bedeutet, dass der Dispatcher nicht in der Lage ist die Antwort zwischenzuspeichern.
* Wenn Sie dieses Servlet sicher möchten, müssen Sie Ihre eigene benutzerdefinierte Sicherheitslogik in dieses Servlet implementieren.
* Der Dispatcher muss (sorgfältig) konfiguriert sein, um `/bin/myApp/myServlet` freizulegen. Das Freilegen von `/bin` würde Zugang zu Servlets erlauben, die nicht für Besucher der Website offen sein sollten.

#### Sling-Servlets (eine Ebene nach unten) {#sling-servlets-one-level-down}

**Sling**-Servlets ermöglichen die Registrierung von Servlets auf gegensätzliche Art und Weise. Anstatt ein Servlet zu adressieren und den Inhalt festzulegen, welchen dieses basierend auf den Abfrageparametern rendern soll, adressieren Sie den gewünschten Inhalt und legen das Servlet fest, das den Inhalt basierend auf den Sling-Selektoren rendern soll.

Der SCR-Vermerk für diese Art von Servlet sieht in etwa so aus:

```
@SlingServlet(resourceTypes = "myBrand/components/pages/myPageType", selectors = "myRenderer", extensions = "json”, methods=”GET”)
```

In diesem Fall ist die Ressource, welche die URL bedient (eine Instanz der `myPageType`-Ressource) in dem Servlet automatisch zugänglich. Um darauf zuzugreifen, rufen Sie Folgendes ab:

```
Resource myPage = req.getResource();
```

Die daraus resultierende URL könnte beispielsweise in etwa so aussehen:

`https://www.mydomain.com/content/my-brand/my-page.myRenderer.json`

Die Vorteile dieses Ansatzes:

* Sie können den SEO-Wert, der durch die auf der Site-Hierarchie und im Seitennamen vorhandenen Semantiken erzielt wird, mit einbeziehen.
* Da keine Abfrageparameter vorhanden sind, kann der Dispatcher die Antwort zwischenspeichern. Zusätzlich machen jegliche Updates auf der adressierten Seite diese Zwischenspeicherung ungültig, wenn die Seite aktiviert wird.
* Alle auf `/content/my-brand/my-page` angewandten ACLs werden aktiv, wenn ein Benutzer versucht, auf dieses Servlet zuzugreifen.
* Der Dispatcher ist bereits konfiguriert, um diesen Inhalt als Bestandteil der Bedienung der Website zu bedienen. Es ist keine zusätzliche Konfiguration notwendig.

### Umschreiben der URL {#url-rewriting}

In AEM werden all Ihre Websites unter `/content/my-brand/my-content` gespeichert. Während dies aus der Perspektive der Repository-Datenverwaltung nützlich sein kann, ist dies nicht notwendigerweise die Art und Weise, wie Ihre Kunden die Website sehen sollen, und kann im Widerspruch zu den SEO-Richtlinien stehen, URLs so kurz wie möglich zu halten. Zusätzlich kann es sein, dass Sie mehrere Websites von derselben AEM-Instanz und zwei unterschiedlichen Domain-Namen aus bedienen.

Dieser Abschnitt erläutert die verfügbaren AEM-Optionen zum Verwalten und der Präsentation dieser URLs gegenüber dem Benutzer auf leichter lesbare, SEO-freundliche Weise.

#### Vanity-URLs {#vanity-urls}

Wenn ein Autor wünscht, dass die Seite von einem zweiten Ort aus für Werbezwecke zugänglich ist, können die auf Seitenbasis definierten Vanity-URLs von AEM nützlich sein. Um einer Seite eine Vanity-URL hinzuzufügen, rufen Sie sie in der Konsole **Sites** auf und bearbeiten Sie die Seiteneigenschaften. Unten auf der Registerkarte **Allgemein** sehen Sie einen Abschnitt, dem Vanity-URLs hinzugefügt werden können. Bedenken Sie, dass die Zugänglichkeit einer Seite über mehr als eine URL den SEO-Wert der Seite fragmentiert. Der Seite sollte also ein kanonisches URL-Tag hinzugefügt werden, um dieses Problem zu vermeiden.

#### Lokalisierte Seitennamen {#localized-page-names}

Sie möchten eventuell lokalisierte Seitennamen für Benutzer übersetzter Inhalte anzeigen. Beispiel:

* Anstatt einen Spanisch sprechenden Benutzer zur folgenden URL zu leiten:
   `www.mydomain.com/es/home.html`

* wäre folgende URL besser:
   `www.mydomain.com/es/casa.html`.

Die Herausforderung bei der Lokalisierung des Seitennamens besteht darin, dass viele der für die AEM-Plattform erhältlichen Lokalisierungs-Tools für die Synchronisierung von Inhalten identische Seitennamen für verschiedene Sprachen benötigen.

Die Eigenschaft `sling:alias` ermöglicht beides. `sling:alias` kann jeder Ressource als Eigenschaft hinzugefügt werden, um einen Alias für die Ressource zu erlauben. Im vorangegangenen Beispiel hätten Sie Folgendes:

* Eine Seite im JCR unter:
   `…/es/home`

* Dieser fügen Sie dann eine Eigenschaft hinzu:
   `sling:alias` = `casa`

Dies würde es den AEM-Übersetzungs-Tools wie dem Multi-Site-Manager ermöglichen, eine Beziehung zwischen folgenden Seiten beizubehalten:

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

* `/etc/map`.

Zuordnungsdefinitionen können in diesem Verzeichnis hinzugefügt werden, um eingehende Anfragen zuzuordnen, URLs auf Seiten in AEM umzuschreiben oder beides.

Um eine neue Zuordnung zu erstellen, erstellen Sie einen neuen Knoten `sling:Mapping` in diesem Verzeichnis unter `/http` oder `/https`. Basierend auf den Eigenschaften `sling:match` und `sling:internalRedirect`, die für diesen Knoten eingestellt sind, leitet AEM sämtlichen Traffic für die passende URL an den in der Eigenschaft `internalRedirect` spezifizierten Wert weiter.

Während dies der Ansatz ist, der in der offiziellen AEM- und Sling-Dokumentation aufgeführt wird, ist die von dieser Implementierung bereitgestellte Unterstützung für reguläre Ausdrücke im Vergleich zu den Optionen begrenzt, die durch die direkte Verwendung von `SlingResourceResolver` zur Verfügung gestellt werden. Außerdem kann die Implementierung von Zuordnungen auf diese Art zu Problemen mit der Invalidierung des Dispatcher-Cache führen.

Ein Beispiel dafür, wie dieses Problem auftritt:

1. Ein Besucher fordert auf Ihrer Website `https://www.mydomain.com/my-page.html` an.
1. Der Dispatcher leitet diese Anfrage an den Veröffentlichungs-Server weiter.
1. Der Veröffentlichungs-Server verwendet `/etc/map`, löst die Anfrage zu `/content/my-brand/my-page` auf und stellt die Seite dar.

1. Der Dispatcher speichert die Antwort unter `/my-page.html` und leitet die Antwort zurück an den Benutzer.
1. Ein Inhaltsautor ändert diese Seite und aktiviert sie.
1. Der Flush-Agent des Dispatchers sendet eine Anfrage zur Invalidierung von `/content/my-brand/my-page`**.** Da der Dispatcher auf diesem Pfad keine Seite gespeichert hat, bleibt der alte Inhalt gespeichert und ist nicht mehr aktuell.

Es gibt Möglichkeiten, benutzerdefinierte Dispatch-Flush-Regeln zu konfigurieren, welche die kürzere URL zur Invalidierung des Cache an die längere URL weiterleiten.

Es gibt jedoch einfachere Möglichkeiten, dies zu lösen:

1. **SlingResourceResolver-Regeln**

   Verwenden Sie die Web-Konsole (zum Beispiel localhost:4502/system/console/configMgr) zur Konfiguration von Sling Resource Resolver:

   * **Apache Sling Resource Resolver Factory**

      `(org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl)`.
   Es wird empfohlen, die zur Kürzung von URLs zu regulären Ausdrücken notwendigen Zuordnungen zu erstellen und diese Konfigurationen dann unter einem OsgiConfignod, `config.publish`, zu definieren, der im Build enthalten ist.

   Anstatt Zuordnungen in `/etc/map` zu definieren, können diese direkt den Eigenschaften der **URL-Zuordnungen** (`resource.resolver.mapping`) zugeordnet werden:

   ```xml
   resource.resolver.mapping="[/content/my-brand/(.*)</$1]"
   ```

   In diesem einfachen Beispiel entfernen Sie `/content/my-brand/` von der Position am Anfang einer beliebigen URL.

   Dadurch würde eine URL umgewandelt:

   * von `/content/my-brand/my-page.html`
   * in `/my-page.html`

   Dies steht im Einklang mit den empfohlenen Verfahren, URLs so kurz wie möglich zu halten.

1. **Zuordnen von URL-Output auf Seiten**

   Nachdem Sie die Zuordnungen im Apache Sling Resource Resolver definiert haben, müssen Sie diese Zuordnungen in den Komponenten verwenden, um zu gewährleisten, dass die URLs auf Ihren Seiten kurz und ordentlich sind. Sie können dies durch die Verwendung der Zuordnungsfunktion `ResourceResolver` tun.

   Wenn Sie beispielsweise eine benutzerdefinierte Navigationskomponente implementieren, welche die untergeordneten Elemente der aktuellen Seite auflistet, können Sie die Zuordnungsmethode wie folgt verwenden:

   ```
   for (Page child : children) {
     String childUrl = resourceResolver.map(request, child.getPath());
     //Output the childUrl on the page here
   }
   ```

#### Apache HTTP-Server mod_rewrite   {#apache-http-server-mod-rewrite}

Bisher haben Sie die Zuordnungen gemeinsam mit der Logik in den Komponenten implementiert, um diese Zuordnungen bei der Ausgabe von URLs auf Seiten zu verwenden.

Das letzte Teil des Puzzles besteht darin, diese gekürzten URLs zu verwalten, wenn sie beim Dispatcher ankommen, wobei `mod_rewrite` ins Spiel kommt. Der größte Vorteil bei der Verwendung von `mod_rewrite` besteht darin, dass die URLs zurück in ihre Langform gebracht werden, *bevor* sie an das Dispatcher-Modul gesendet werden. Das bedeutet, dass der Dispatcher die lange URL vom Veröffentlichungs-Server abfragt und diese entsprechend zwischenspeichert. Sämtliche vom Veröffentlichungs-Server ausgehenden Dispatcher-Flush-Anfragen können diesen Inhalt erfolgreich ungültig machen.

Um diese Regeln zu implementieren, können Sie `RewriteRule`-Elemente unter Ihrem virtuellen Host in der Apache HTTP Server-Konfiguration hinzufügen. Wenn Sie gekürzte URLs aus dem vorherigen Beispiel erweitern möchten, können Sie eine Regel implementieren, die folgendermaßen aussieht:

```
<VirtualHost *:80>
  ServerName www.mydomain.com
  RewriteEngine on
  RewriteRule ^/(.*)$ /content/my-brand/$1 [PT,L]
  …
</VirtualHost>
```

### Kanonische URL-Tags   {#canonical-url-tags}

Kanonische URL-Tags sind Link-Tags die in der Kopfzeile des HTML-Dokuments eingegeben werden und festlegen, wie Suchmaschinen die Seite bei der Indizierung des Inhalts behandeln sollen. Ihr Vorteil besteht darin, dass sichergestellt wird, dass eine Seite (verschiedene Versionen davon) auf gleiche Weise indiziert wird, auch wenn die auf die Seite verweisende URL Unterschiede enthält.

Bietet eine Website beispielsweise eine druckfreundliche Version einer Seite an, könnte eine Suchmaschine diese Seite getrennt von der regulären Version der Seite indizieren. Das kanonische Tag erklärt der Suchmaschine, dass es sich um dieselbe Seite handelt.

Beispiele:

* https://www.mydomain.com/my-brand/my-page.html
* https://www.mydomain.com/my-brand/my-page.print.html

Bei beiden würde das folgende Tag der Kopfzeile der Seite hinzugefügt:

```xml
<link rel=”canonical” href=”my-brand/my-page.html”/>
```

Das `href`-Attribut kann relativ oder absolut sein. Der Code sollte im Seiten-Layout inbegriffen sein, um die kanonische URL und das Ausgabe-Tag zu bestimmen.

### Konfigurieren des Dispatchers für das Ignorieren von Groß- und Kleinschreibung {#configuring-the-dispatcher-for-case-insensitivity}

Die Best Practice besteht darin, alle Seiten mit Kleinbuchstaben zu bedienen. Sie wollen jedoch vermeiden, dass der Benutzer einen 404-Fehler erhält, wenn er versucht, unter Verwendung von Großbuchstaben in der URL auf die Website zuzugreifen. Aus diesem Grund empfiehlt Adobe, dass Sie eine Umschreiberegel in der Apache HTTP Server-Konfiguration hinzufügen, um alle eingehenden URLs in Kleinbuchstaben darzustellen. Darüber hinaus müssen Autoren dahingehend geschult werden, Seiten nur mit Namen in Kleinbuchstaben zu erstellen.

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

Suchmaschinen *sollten* das Vorhandensein einer Datei `robots.txt` im Stammverzeichnis der Website überprüfen, bevor die Website durchsucht wird. „Sollten“ wird hier betont, weil die meistverwendeten Suchmaschinen wie Google, Yahoo oder Bing dies befolgen, einige andere Suchmaschinen jedoch nicht.

Die einfachste Möglichkeit, den Zugang zu der gesamten Website zu blockieren, ist eine Datei namens `robots.txt` im Stammverzeichnis der Website zu platzieren, die Folgendes enthält:

```xml
User-agent: *
Disallow: /
```

Wahlweise können Sie in einer Live-Umgebung bestimmte Pfade ablehnen, die nicht indiziert werden sollen.

Der Nachteil der Platzierung einer Datei `robots.txt` im Stammverzeichnis der Website besteht darin, dass Dispatcher-Flush-Anfragen diese Datei löschen könnten und die URL-Zuordnungen den Site-Stamm wahrscheinlich an einen anderen Ort als `DOCROOT` verschieben, wie in der Apache HTTP Server-Konfiguration festgelegt. Aus diesem Grund ist es üblich, diese Datei in der Autoreninstanz am Site-Stamm zu platzieren und sie in der Veröffentlichungsinstanz zu replizieren.

### Erstellen einer XML-Sitemap in AEM   {#building-an-xml-sitemap-on-aem}

Crawler verwenden XML-Sitemaps, um die Websitestrukturen besser zu verstehen. Während es keine Garantie dafür gibt, dass die Bereitstellung einer Sitemap zu verbesserten SEO-Rankings führt, ist dies dennoch eine allgemein anerkannte Best Practice. Sie können die XML-Datei manuell auf einem Webserver als Sitemap verwalten, es wird jedoch empfohlen, die Sitemap programmatisch zu generieren, was gewährleistet, dass die Sitemap automatisch Änderungen widerspiegelt, sobald sie von den Autoren vorgenommen werden.

Um eine Sitemap programmatisch zu generieren, registrieren Sie einen Sling-Servlet-Listener für eine `sitemap.xml`-Anfrage. Das Servlet kann dann die über die Servlet-API bereitgestellten Ressourcen verwenden, um die aktuelle Seite und deren untergeordnete Elemente zu sehen, und gibt dabei XML aus. Die XML-Datei wird dann vom Dispatcher zwischengespeichert. Auf diesen Ort sollte in den Sitemap-Eigenschaften der Datei `robots.txt` verwiesen werden. Zusätzlich muss eine benutzerdefinierte Flush-Regel implementiert werden, um zu gewährleisten, dass diese Datei geleert wird, wann immer eine neue Seite aktiviert wird.

>[!NOTE]
>
>Sie können ein Sling-Servlet registrieren, um auf den `sitemap`-Selektor mit der Endung `xml` zu warten. Dies führt zur Verarbeitung der Anfrage durch das Servlet, wenn eine URL angefordert wird, die wie folgt endet:
>    `/<path-to>/page.sitemap.xml`
>Sie können die angeforderte Ressource von der Anfrage erhalten und eine Sitemap für diesen Punkt im Inhaltsbaum generieren, indem Sie die JCR-APIs verwenden.
>Ein solcher Ansatz ist dann vorteilhaft, wenn mehrere Sites von derselben Instanz bedient werden. Eine Anfrage an `/content/siteA.sitemap.xml` würde eine Sitemap für `siteA` generieren, während eine Anfrage an `/content/siteB.sitemap.xml` eine Sitemap für `siteB` generieren würde, ohne dass zusätzlicher Code geschrieben werden muss.

### Erstellen von 301-Weiterleitungen für veraltete URLs {#creating-redirects-for-legacy-urls}

Beim Start einer Website mit einer neuen Struktur ist die Implementierung und Prüfung von 301-Weiterleitungen in Apache HTTP Server aus zwei Gründen wichtig:

* Die veralteten URLs bauen über die Zeit hinweg SEO-Wert auf. Durch Implementierung einer Umleitung kann die Suchmaschine diesen Wert auf die neue URL anwenden.
* Benutzer der Website könnten Lesezeichen für diese Seiten erstellt haben. Durch die Implementierung von Umleitungen kann sichergestellt werden, dass der Benutzer auf den Bereich der Site weitergeleitet wird, der seinem ursprünglichen Zielort am ehesten gerecht wird.

Werfen Sie einen Blick in den Abschnitt mit zusätzlichen Ressourcen für Anleitungen zur Implementierung von 301 Weiterleitungen, sowie einem Werkzeug zum Testen der Weiterleitung.

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
* [https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/](https://www.internetmarketingninjas.com/blog/search-engine-optimization/301-redirects/)
* [https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/dispatcher/redirectTester)
* [https://adobe-consulting-services.github.io/](https://adobe-consulting-services.github.io/)
