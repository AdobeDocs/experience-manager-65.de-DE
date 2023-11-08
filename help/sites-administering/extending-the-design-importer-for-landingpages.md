---
title: Erweitern und Konfigurieren des Design-Import-Tools für Landing-Pages
description: Erfahren Sie, wie Sie den Design Importer für Landingpages konfigurieren.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 1b8c6075-13c6-4277-b726-8dea7991efec
source-git-commit: e2a3470784beb04c2179958ac6cb98861acfaa71
workflow-type: tm+mt
source-wordcount: '3493'
ht-degree: 44%

---

# Erweitern und Konfigurieren des Design-Import-Tools für Landing-Pages{#extending-and-configuring-the-design-importer-for-landing-pages}

In diesem Abschnitt wird beschrieben, wie Sie den Design Importer für Einstiegsseiten konfigurieren und bei Bedarf erweitern. Die Arbeit mit Landingpages nach dem Import wird im Abschnitt [Landingpages.](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)

**Extrahieren der benutzerdefinierten Komponente durch den Design Importer**

Im Folgenden finden Sie die logischen Schritte, damit der Design Importer Ihre benutzerdefinierte Komponente erkennt

1. Erstellen eines Taghandlers

   * Ein Taghandler ist ein POJO, das HTML-Tags eines bestimmten Typs handelt. Die &quot;Art&quot;von HTML-Tags, die Ihr TagHandler verarbeiten kann, wird über die OSGi-Eigenschaft &quot;tagpattern.name&quot;von TagHandlerFactory definiert. Im Grunde handelt es sich bei der OSGi-Eigenschaft um einen RegEx, der dem Eingabe-HTML-Tag entsprechen sollte, das Sie handeln möchten. Alle verschachtelten Tags würden zum Handling an den Taghandler übergeben werden. Wenn Sie sich beispielsweise für ein div registrieren, das eine verschachtelte &lt;p> -Tag &lt;p> -Tag auch an Ihren TagHandler gesendet werden und es liegt an Ihnen, wie Sie sich darum kümmern möchten.
   * Die Oberfläche des Taghandlers ähnelt der Oberfläche eines SAX-Inhaltshandlers. Sie erhält für jedes HTML-Tag SAX-Ereignisse. Als Tag-Handler-Anbieter müssen Sie bestimmte Lebenszyklusmethoden implementieren, die automatisch vom Design Importer-Framework aufgerufen werden.

1. Erstellen Sie die entsprechende TagHandlerFactory.

   * Die Tag-Handler-Factory ist eine OSGi-Komponente (Singleton), die für das Erstellen von Instanzen Ihres Tag-Handlers verantwortlich ist.
   * Ihre TagHandlerFactory muss eine OSGi-Eigenschaft mit dem Namen „tagpattern.name“ bereitstellen, deren Wert mit dem Eingabe-HTML-Tag abgeglichen wird.
   * Wenn mehrere Taghandler mit dem Eingabe-HTML-Tag übereinstimmen, wird jener mit dem höheren Rang gewählt. Der Rang selbst wird in der OSGi-Eigenschaft **service.ranking** angegeben.
   * Die TagHandlerFactory ist eine OSGi-Komponente. Alle Verweise, die Sie für Ihren TagHandler bereitstellen möchten, müssen über diese Factory erfolgen.

1. Stellen Sie sicher, dass Ihre TagHandlerFactory einen höheren Rang hat, wenn Sie den Standard überschreiben möchten.

>[!CAUTION]
>
>Der Design Importer, der zum Importieren von Landingpages verwendet wird, [ist seit AEM 6.5 veraltet](/help/release-notes/deprecated-removed-features.md#deprecated-features).

## Vorbereiten der HTML für den Import {#preparing-the-html-for-import}

Nachdem Sie eine Importtool-Seite erstellt haben, können Sie Ihre vollständige HTML-Landingpage importieren. Um Ihre HTML-Einstiegsseite zu importieren, müssen Sie den Inhalt zunächst zu einem Designpaket packen. Das Designpaket enthält Ihre HTML-Landingpage zusammen mit den referenzierten Assets (Bilder, CSS, Symbole, Skripte usw.).

Das folgende Spickzettel enthält ein Beispiel für die Vorbereitung Ihrer HTML für den Import:

Landingpage-Spickzettel

[Datei laden](assets/cheatsheet.zip)

### Zip-Datei-Layout und -Anforderungen {#zip-file-layout-and-requirements}

>[!NOTE]
>
>An dieser Stelle dürfen ZIP-Dateien nur eine HTML-Seite oder einen Seitenbereich enthalten.

Ein Beispiel für ein Zip-Layout:

* /index.html -> Landingpage-HTML-Datei
* /css -> zum Hinzufügen zur CSS-clientlib
* /img -> alle Bilder und Assets
* /js -> zum Hinzufügen zur JS-clientlib

Das Layout basiert auf dem Boilerplate-Layout für HTML5. Lesen Sie mehr unter [https://html5boilerplate.com/](https://html5boilerplate.com/).

>[!NOTE]
>
>Mindestens das Designpaket **must** enthalten **index.html** -Datei auf der Stammebene. Wenn die zu importierende Landingpage auch eine mobile Version aufweist, muss die ZIP-Datei eine **mobile.index.html** zusammen mit **index.html** auf der Stammebene.

### Vorbereiten der HTML-Landingpage {#preparing-the-landing-page-html}

Um die HTML importieren zu können, müssen Sie der Landingpage-HTML ein Leinwand-div hinzufügen.

Das Arbeitsflächen-div ist ein HTML-**div** mit `id="cqcanvas"`, das in das HTML-`<body>`-Tag eingefügt werden muss und das den Inhalt für die Konvertierung umgeben muss.

Ein Beispielausschnitt der Landingpage-HTML nach dem Hinzufügen des Leinwand-div ist wie folgt:

```xml
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
  <meta name="description" content="">
</head>
<body>
 <div id="cqcanvas">
  <!-- HTML content intended for conversion -->
 </div>
</body>
</html>
```

### Vorbereiten des HTML auf das Einschließen bearbeitbarer AEM {#preparing-the-html-to-include-editable-aem-components}

Beim Import einer Landingpage haben Sie die Möglichkeit, die Seite unverändert zu importieren. Das bedeutet, dass Sie nach dem Import der Landingpage keines der importierten Elemente in AEM bearbeiten können (Sie können auf der Seite noch weitere AEM hinzufügen).

Bevor Sie die Einstiegsseite importieren, empfiehlt es sich, einige Teile der Einstiegsseite in bearbeitbare AEM-Komponenten zu konvertieren. Auf diese Weise können Sie Teile der Landingpage auch nach dem Import des Landingpage-Designs schnell bearbeiten.

Sie tun dies, indem Sie in der zu importierenden HTML-Datei der entsprechenden Komponente die `data-cq-component` hinzufügen.

Im folgenden Abschnitt wird beschrieben, wie Sie Ihre HTML-Datei so bearbeiten, dass bestimmte Teile der Einstiegsseiten in andere bearbeitbare AEM-Komponenten konvertiert werden. Die Komponenten werden detailliert beschrieben unter [Einstiegsseiten-Komponenten](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md).

>[!NOTE]
>
>HTML-Markup zum Konvertieren von Teilen der Einstiegsseiten in AEM-Komponenten verfügt sowohl über eine lange als auch über eine kurze Tag-Deklarierung. Beide werden für jede Komponente beschrieben.

### Beschränkungen {#limitations}

Beachten Sie vor dem Import die folgenden Einschränkungen:

### Sämtliche Attribute wie „class“ oder „id“, die auf das     &amp;lt;body>-Tag angewendet werden, werden nicht beibehalten. {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

Wenn beispielsweise ein beliebiges Attribut wie ID oder Klasse auf das Body-Tag angewendet wird, `<body id="container">` nach dem Import nicht beibehalten. Das importierte Design darf also über keine Abhängigkeiten bei den Attributen verfügen, die auf das `<body>`-Tag angewendet werden.

### Verschieben einer Zip-Datei per Drag-and-Drop {#drag-and-drop-zip}

Ein Upload durch Verschieben einer Zip-Datei per Drag-and-Drop wird für Internet Explorer und Firefox-Versionen vor 3.6 nicht unterstützt. Um bei Verwendung dieser Browser ein Design hochzuladen, klicken Sie auf den Bereich der Dropdatei, um ein Dialogfeld zum Hochladen von Dateien zu öffnen und Ihr Design mithilfe dieses Dialogfelds hochzuladen.

Die Browser, die &quot;Drag &amp; Drop&quot;der Design-ZIP unterstützen, sind Chrome, Safari5.x, Firefox 4 und höher.

### Modernizr wird nicht unterstützt {#modernizr-is-not-supported}

`Modernizr.js` ist ein JavaScript-basiertes Tool, das native Funktionen von Browsern erkennt und erkennt, ob diese für HTML5-Elemente geeignet sind oder nicht. Bei Designs, die Modernizr für die verbesserte Unterstützung älterer Browserversionen verwenden, können Fehler in der Einstiegsseitenlösung auftreten. `Modernizr.js`-Skripts werden vom Design-Importer nicht unterstützt.

### Seiteneigenschaften werden beim Import des Designpakets nicht beibehalten {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

Jede Seiteneigenschaft (z. B. benutzerdefinierte Domäne, Erzwingen von HTTPS usw.), die für eine Seite festgelegt ist (die eine leere Landingpage-Vorlage verwendet), bevor das Designpaket importiert wird, geht verloren, nachdem das Design importiert wurde. Daher wird empfohlen, die Seiteneigenschaften nach dem Import des Designpakets festzulegen.

### Nur Markup für HTML angenommen {#html-only-markup-assumed}

Beim Import wird das Markup aus Sicherheitsgründen bereinigt, um den Import und die Veröffentlichung von ungültigem Markup zu vermeiden. Dabei wird davon ausgegangen, dass das reine HTML-Markup und alle anderen Elementformen wie Inline-SVG oder Webkomponenten herausgefiltert werden.

### Text {#text}

HTML-Markup zum Einfügen einer text-Komponente (`foundation/components/text`) in das HTML im Designpaket:

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Eine bearbeitbare AEM-text-Komponente (`sling:resourceType=foundation/components/text`) wird in der Landingpage erstellt, die nach dem Import des Designpakets erstellt wurde.
* Die Eigenschaft `text` der erstellten Komponente „text“ wird auf das im `div` eingeschlossene HTML gesetzt.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**Text mit einer Liste**

So fügen Sie einen Text mit einer Liste hinzu:

* 1st
* 2nd

die im RTE-Editor bearbeitet werden können:

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**Text mit Farbe**

So fügen Sie einen Text mit Farbe (rosa) hinzu, der im RTE-Editor bearbeitet werden kann:

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### Titel {#title}

HTML-Markup, um eine title-Komponente (`wcm/landingpage/components/title`) in das HTML im Designpaket einzufügen:

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Eine bearbeitbare AEM-title-Komponente (`sling:resourceType=wcm/landingpage/components/title`) wird in der Landingpage erstellt, die nach dem Import des Designpakets erstellt wurde.
* Stellt die Eigenschaft `jcr:title` der erstellten title-Komponente auf den Text ein, der im div in das Überschriften-Tag eingeschlossen ist.
* Stellt die Eigenschaft `type` des Überschriften-Tags ein, in diesem Fall `h1`.

Die Titelkomponente unterstützt sieben Typen: `h1, h2, h3, h4, h5, h6` und `default`.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### Bild {#image}

HTML Markup zum Einfügen einer Bildkomponente (foundation/components/image) in die HTML innerhalb des Designpakets:

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Eine bearbeitbare AEM-image-Komponente (`sling:resourceType=foundation/components/image`) wird in der Landingpage erstellt, die nach dem Import des Designpakets erstellt wurde.
* Stellt die Eigenschaft `fileReference` der erstellten image-Komponente auf den Pfad ein, in den das im src-Attribut angegebene Bild importiert wird.
* Setzt die Eigenschaft `alt` auf den Wert des alt-Attributs im img-Tag.
* Setzt die Eigenschaft `title` auf den Wert des title-Attributs im img-Tag.
* Setzt die Eigenschaft `width` auf den Wert des width-Attributs im img-Tag.
* Setzt die Eigenschaft `height` auf den Wert des height-Attributs im img-Tag.

**Kurze Komponenten-Tag-Deklaration:**

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### Absolute URL img src wird in der Bildkomponente Div nicht unterstützt {#absolute-url-img-src-not-supported-within-image-component-div}

Wenn ein `<img>`-Tag mit einer absoluten URL-src für die Komponenten-Konverstierung ausgewählt wird, wird ein entsprechender Ausnahmefehler **UnsupportedTagContentException** ausgegeben. So wird das folgende Beispiel nicht unterstützt:

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

Andernfalls werden jedoch absolute URL-Bilder für img-Tags unterstützt, die nicht Teil des Bildkomponente-div sind.

### Aktionsaufruf-Komponenten {#call-to-action-components}

Sie können einen Teil der zu importierenden Landingpage als &quot;bearbeitbare Aktionsaufruf-Komponente&quot;markieren. Solche importierten Aktionsaufruf-Komponenten können nach dem Import der Landingpage bearbeitet werden. AEM enthält die folgenden CTA-Komponenten:

* Clickthrough-Link - Ermöglicht den Zusatz eines Textlinks, der den Besucher zu einer Ziel-URL führt, wenn er darauf klickt.
* Grafischer Link - Ermöglicht das Hinzufügen eines Bildes, das den Besucher durch Klicken auf eine Ziel-URL weiterleitet.

#### Click Through-Link {#click-through-link}

Diese CTA-Komponente kann dazu verwendet werden, der Landingpage einen Text-Link hinzuzufügen.

Unterstützte Eigenschaften

* Beschriftung mit Optionen für Fettschrift, Kursivschrift und Unterstreichung
* Target-URL, unterstützt Drittanbieter- und AEM-URL
* Seitenrendering-Optionen (gleiches Fenster, neues Fenster usw.)

HTML-Tag mit in der importierten Zip enthaltener Click Through-Komponente: Hier ordnet href der Ziel-URL zu, &quot;Produktdetails anzeigen&quot;wird der Beschriftung zugeordnet usw.

```xml
<div id="cqcanvas">
.
.
                <div data-cq-component="clickThroughLink">
        <a href="/content/we-retail/us/en/products/equipment/snow-sports/flying-snowboard.html">View Product Details  ></a>
  </div>
.
.
</div>
```

Diese Komponente kann in jeder eigenständigen Anwendung verwendet oder aus der ZIP-Datei importiert werden.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### Grafischer Link {#graphical-link}

Diese CTA-Komponente kann dazu verwendet werden, ein beliebiges grafisches Bild mit Link auf der Einstiegsseite hinzuzufügen. Beim Bild kann es sich um eine einfache Schaltfläche oder um ein grafisches Bild als Hintergrund handeln. Wenn der Benutzer auf das Bild klickt, wird er zur in den Komponenteneigenschaften angegebenen Ziel-URL weitergeleitet. Sie ist Teil der Gruppe &quot;Aktionsaufruf&quot;.

Unterstützte Eigenschaften

* Bild beschneiden, drehen
* Hover-Text, Beschreibung, Größe in px
* Target-URL, unterstützt Drittanbieter- und AEM-URL
* Seitenrendering-Optionen (gleiches Fenster, neues Fenster usw.)

HTML-Tag mit in der importierten Zip enthaltenem grafischen Link: Hier ordnet href der Ziel-URL zu, img src ist das Rendering-Bild, &quot;title&quot;wird als Hover-Text verwendet usw.

```xml
<div id="cqcanvas">
  <div data-cq-component="clickThroughGraphicalLink"><a href="https://www.adobe.com/go/wem"><img src="img/call-to-action-button.png" title="Click Here to Learn More" /></a></div>
</div>
```

**Kurze Komponenten-Tag-Deklaration**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughGraphicalLink"><img src="linkimage.png" alt="Click Through Graphical Link shorthand"/></a>
```

>[!NOTE]
>
>Um einen Link „clickthroughgraphical“ zu erstellen, müssen Sie ein Anchortag und das Bild-Tg in einem div mit dem Attribut `data-cq-component="clickthroughgraphicallink"` einschließen.
>
>Beispiel: `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>Andere Möglichkeiten zum Verknüpfen eines Bildes mit einem Anker-Tag mithilfe von CSS werden nicht unterstützt. Beispielsweise funktioniert das folgende Markup nicht:
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>mit einem verknüpften `css .hasbackground { background-image: pathtoimage }`
>

### Lead-Formular {#lead-form}

Ein Lead-Formular ist ein Formular, das dazu verwendet wird, die Informationen eines Besuchers/Leads zu sammeln. Diese Informationen können gespeichert und später dazu verwendet werden, anhand dieser Informationen effizientes Marketing durchzuführen. Die Informationen enthalten im Allgemeinen Titel, Namen, E-Mail, Geburtsdatum, Adresse, Interessen usw. Sie sind Teil der Gruppe „CTA-Lead-Formular“.

**Unterstützte Funktionen**

* Vordefinierte Lead-Felder (Vorname, Nachname, Adresse, Geburtsdatum, Geschlecht, Info, Benutzer-ID, E-Mail-ID, Sende-Schaltfläche) sind im Sidekick verfügbar. Platzieren Sie die erforderliche Komponente einfach per Drag-and-Drop in Ihrem Lead-Formular.
* Mithilfe dieser Komponenten kann der Autor ein eigenständiges Formular entwerfen. Diese Felder entsprechen den Lead-Formular-Feldern. In eigenständigen oder importierten ZIP-Anwendungen können Benutzer zusätzliche Felder mithilfe von cq:form- oder cta lead form-Formularfeldern hinzufügen, sie benennen und entsprechend den Anforderungen entwerfen.
* Weisen Sie Lead-Formular-Felder mit bestimmten vordefinierten Namen des CTA-Lead-Formulars zu, z. B. - firstName für Vorname im Lead-Formular usw.
* Felder, die nicht dem Lead-Formular zugeordnet sind, werden cq:form-Komponenten zugeordnet - Text, Optionsfeld, Kontrollkästchen, Dropdown, ausgeblendet, Kennwort.
* Benutzende können den Titel mit dem Tag „Beschriften“ und Stile mit dem Stilattribut „Klasse“ angeben (nur für CTA-Lead-Formular-Komponenten verfügbar).
* Die Dankeseite und die Abonnement-Liste können als versteckte Parameter des Formulars (vorhanden in der Datei „index.htm“) bereitgestellt werden oder über die Bearbeitungsleiste von „Start des Lead-Formulars“ hinzugefügt oder bearbeitet werden.

  &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

  &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* Beschränkungen wie „Erforderlich“ können in jeder der Komponenten unter „Konfiguration bearbeiten“ angegeben werden.

HTML-Tag mit in der importierten Zip enthaltenem grafischen Link: Hier wird &quot;firstName&quot;dem Lead-Formular &quot;firstName&quot;usw. zugeordnet, mit Ausnahme von Kontrollkästchen - diese beiden Kontrollkästchen werden der Dropdown-Komponente cq:form zugeordnet.

```xml
<div id="cqcanvas">
   <div id="form_wrapper">
    <h2>NEWSLETTER SIGN UP</h2>
       <div data-cq-component="leadFormGeneration">
       <form method="post" action="#" onsubmit="return popupBox()">
       <label for="firstName" class="checkText">
        FIRST NAME
       </label><br />
       <input name="firstName" class="text pink" type="text" /><br />
       <label for="lastName" class="checkText">
        LAST NAME
       </label><br />
       <input name="lastName" class="text pink" type="text" /><br />
       <label for="emailId" class="checkText">
        EMAIL ADDRESS
       </label><br />
       <input name="emailId" class="text pink" type="text" /><br />

       <div class="checkboxes">
       <input type="checkbox" class="check" name="send_news" /> <label for="send_news" class="checkText">Send me the latest We.Retail news and announcements.</label><br />
       <input type="checkbox" class="check" name="send_offers" /> <label for="send_offers" class="checkText">Send me We.Retail deals and special offers.</label><br />
       </div>
       <input type="submit" name="submit" class="submit pink" value="Sign Up >" />
       </form>
     </div>
   </div>
```

### Parsys {#parsys}

Das AEM-parsys ist eine Container-Komponente, die andere AEM-Komponenten enthalten kann. Es ist möglich, in das importierte HTML eine parsys-Komponente einzufügen. Dadurch kann der Benutzer bearbeitbare AEM zur Landingpage hinzufügen/löschen, selbst wenn sie importiert wurde.

Das Absatzsystem bietet Benutzern die Möglichkeit, mithilfe des Sidekicks Komponenten hinzuzufügen.

HTML-Markup zum Einfügen einer parsys-Komponente (`foundation/components/parsys`) in das HTML im Designpaket:

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

Das Einschließen des obigen Markups in die HTML führt zu folgenden Aufgaben:

* Fügt eine AEM parsys-Komponente (foundation/components/parsys) in die Landingpage ein, die nach dem Import des Designpakets erstellt wurde.
* Startet den Sidekick mit Standardkomponenten. Neue Komponenten können zur Landingpage hinzugefügt werden, indem Komponenten aus dem Sidekick auf die parsys-Komponente gezogen werden.
* Zwei title-Komponenten sind ebenfalls Teil des parsys.

### Ziel {#target}

Die target-Komponente zeigt den Inhalt eines Erlebnisses auf der Seite an. In einer Kampagne können viele Erlebnisse erstellt werden, und die Zielkomponente kann verschiedenen Benutzern, die die Seite besuchen, dynamisch Inhalte aus verschiedenen Erlebnissen anzeigen.

Das HTML-Markup zum Einfügen einer Zielkomponente und zum Erstellen verschiedener Erlebnisse in einer Kampagne:

```xml
<div data-cq-component="target">
 <section data-cq-component="experience" data-cq-experience="default">
  <p data-cq-component="text">Default content. Select this campaign in client context to view other experiences</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="over-30">
  <p data-cq-component="text">Content for Over 30</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="under-30">
  <p data-cq-component="text">Content for Under 30</p>
 </section>
</div>
```

## Zusätzliche Importoptionen {#additional-importing-options}

Neben der Angabe, ob importierte Komponenten bearbeitbar AEM sind, können Sie vor dem Import des Designpakets auch Folgendes konfigurieren:

* Festlegen von Seiteneigenschaften durch Extrahieren der in der importierten HTML definierten Metadaten.
* Gibt die Zeichensatzkodierung im HTML an.
* Überlagern der Importtool-Seitenvorlage.

### Festlegen von Seiteneigenschaften durch Extrahieren von in importierten HTML definierten Metadaten {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

Die folgenden im Kopf der importierten HTML deklarierten Metadaten werden vom Design Importer als Eigenschaft &quot;jcr:description&quot;extrahiert und beibehalten:

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

Das im HTML-Tag festgelegte Attribut lang wird vom Design Importer als Eigenschaft &quot;jcr:language&quot;extrahiert und beibehalten

* &lt;html lang=&quot;en&quot;>

### Festlegen der Zeichensatzkodierung im HTML-Code {#specifying-the-charset-encoding-in-the-html}

Der Design Importer liest die im importierten HTML festgelegte Kodierung. Die Kodierung kann wie folgt festgelegt werden:

`<meta charset="UTF-8">`

*ODER*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

Wenn in der importierten HTML keine Kodierung angegeben ist, ist die vom Design Importer festgelegte Standardkodierung UTF-8.

### Vorlage überlagern {#overlaying-template}

Die Vorlage für leere Landingpages kann überlagert werden, indem Sie eine Vorlage erstellen unter: `/apps/<appName>/designimporter/templates/<templateName>`

Die Schritte zum Erstellen einer Vorlage in AEM werden erläutert. [here](/help/sites-developing/templates.md).

### Verweisen auf eine Komponente von der Landingpage {#referring-a-component-from-landing-page}

Angenommen, Sie verfügen über eine Komponente, auf die Sie in Ihrem HTML mit dem data-cq-component-Attribut verweisen möchten, sodass der Design Importer an dieser Stelle eine Komponente rendert. Sie möchten beispielsweise auf die Tabellenkomponente verweisen ( `resourceType = /libs/foundation/components/table`). Sie müssen das HTML wie folgt ergänzen:

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

Der Pfad in der data-cq-component sollte der resourceType der Komponente sein.

### Best Practices {#best-practices}

Die Verwendung von CSS-Selektoren, die den folgenden ähneln, wird nicht für die Verwendung mit Elementen empfohlen, die beim Import zur Komponentenkonvertierung markiert sind.

| E > F | ein einem E-Element untergeordnetes F-Element | [Untergeordneter Kombinator](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | ein F-Element, dem ein E-Element unmittelbar vorhergeht | [Angrenzender gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | ein F-Element, dem ein E-Element vorangestellt ist | [Allgemeiner gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | ein E-Element, Stamm des Dokuments | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | ein E-Element, das n. untergeordnete Element des übergeordneten Elements | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | ein E-Element, das n. untergeordnete Element des übergeordneten Elements, das vom letzten Element gezählt wird | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | ein E-Element, das n. gleichrangige Element seines Typs | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | ein E-Element, das n. gleichrangige Element seines Typs, das vom letzten Element gezählt wird | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

Dies liegt daran, dass zusätzliche HTML-Elemente wie &lt;div> werden nach dem Import zum generierten HTML-Code hinzugefügt.

* Skripte, die sich auf eine ähnliche Struktur wie die oben stehende stützen, werden ebenfalls nicht zur Verwendung mit Elementen empfohlen, die zur Konvertierung in AEM Komponenten markiert sind.
* Die Verwendung von Stilen in den Markup-Tags für die Komponentenkonvertierung wie &lt;div data-cq-component=&quot;&amp;ast;&quot;> wird nicht empfohlen.
* Beim Designlayout sollten die Best Practices für das HTML5-Boilerplate befolgt werden. Lesen Sie mehr unter [https://html5boilerplate.com/](https://html5boilerplate.com/).

## Konfigurieren von OSGi-Modulen {#configuring-osgi-modules}

Folgende Komponenten geben Eigenschaften an, die über die OSGi-Konsole konfiguriert werden können:

* Landingpage Design Importer
* Builder für Landingpages
* Builder für mobile Landingpages
* Eintrags-Präprozessor für Landingpages

In der folgenden Tabelle werden die Eigenschaften kurz beschrieben:

<table>
 <tbody>
  <tr>
   <td><strong>Komponente</strong></td>
   <td><strong>Eigenschaftsname</strong></td>
   <td><strong>Beschreibung der Eigenschaft </strong></td>
  </tr>
  <tr>
   <td>Landingpage Design Importer</td>
   <td>Filter extrahieren</td>
   <td>Die Liste der regulären Ausdrücke, die für das Filtern der Dateien beim Extrahieren verwendet werden. <br />Zip-Einträge, die einem der angegebenen Muster entsprechen, werden von der Extraktion ausgeschlossen.</td>
  </tr>
  <tr>
   <td>Builder für Landingpages</td>
   <td>Dateimuster</td>
   <td>Der Builder für die Landingpage kann so konfiguriert werden, dass er HTML-Dateien verwaltet, die einem bestimmten im Dateimuster definierten regulären Ausdruck entsprechen.</td>
  </tr>
  <tr>
   <td>Builder für mobile Landingpages</td>
   <td>Dateimuster</td>
   <td>Der Builder für die Landingpage kann so konfiguriert werden, dass er HTML-Dateien verwaltet, die einem bestimmten im Dateimuster definierten regulären Ausdruck entsprechen.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Gerätegruppen</td>
   <td>Die Liste der zu unterstützenden Gerätegruppen.</td>
  </tr>
  <tr>
   <td>Eintrags-Präprozessor für Landingpages</td>
   <td>Suchmuster </td>
   <td>Das Muster, nach dem im Inhalt der Einträge im Archiv gesucht wird. Dieser reguläre Ausdruck wird Zeile für Zeile mit dem Eintragsinhalt abgeglichen. Bei einer Übereinstimmung wird der übereinstimmende Text durch das angegebene Ersetzungsmuster ersetzt.<br /> <br /> Beachten Sie den unten stehenden Hinweis bezüglich aktuellen Beschränkungen für den Eintrags-Präprozessor für die Einstiegsseite.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Ersetzungsmuster</td>
   <td>Das Muster, das die gefundenen Übereinstimmungen ersetzt. Sie können Gruppenreferenzen für reguläre Ausdrücke wie $1, $2 verwenden. Außerdem unterstützt dieses Muster Suchbegriffe wie {designPath} die beim Import mit dem tatsächlichen Wert aufgelöst werden.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>**Aktuelle Beschränkung des Eintrags-Präprozessors für Landingpages:**
>Wenn Sie Änderungen am Suchmuster vornehmen müssen, müssen Sie beim Öffnen des Felix Property Editor manuell umgekehrte Schrägstriche einfügen, um die regex-Metazeichen auszukommentieren. Wenn Sie umgekehrte Schrägstriche nicht manuell hinzufügen, wird der Regex als ungültig betrachtet und ersetzt nicht das ältere.
>
>Wenn die Standardkonfiguration beispielsweise
>
>>`/\* *CQ_DESIGN_PATH *\*/ *(['"])`
>
>Und Sie müssen im Suchmuster `CQ_DESIGN_PATH` durch `VIPURL` ersetzen, dann sollte Ihr Suchmuster wie folgt aussehen:
>
>`/\* *VIPURL *\*/ *(['"])`

## Fehlerbehebung {#troubleshooting}

Beim Import des Designpakets können mehrere Fehler auftreten, die in diesem Abschnitt beschrieben werden.

### Initialisierung des Sidekicks mit relevanten Komponenten der Einstiegsseite {#initialization-of-sidekick-with-landing-page-relevant-components}

Wenn das Designpaket ein parsys-Komponenten-Markup enthält, werden nach dem Import im Sidekick für Einstiegsseiten relevante Komponenten angezeigt. Sie können neue Komponenten per Drag-and-Drop auf die parsys-Komponente in der Einstiegsseite ziehen. Sie können auch den Design-Modus aufrufen und dem Sidekick neue Komponenten hinzufügen.

### Während des Imports werden Fehlermeldungen angezeigt {#error-messages-displayed-during-import}

Wenn Fehler aufgetreten sind (das importierte Paket beispielsweise ist keine gültige ZIP-Datei), importiert der Design-Import das Paket nicht. Stattdessen wird oben auf der Seite direkt über dem Drag &amp; Drop-Feld eine Fehlermeldung angezeigt. Hier werden Beispiele für Fehlerszenarios aufgeführt. Nachdem Sie den Fehler korrigiert haben, können Sie die aktualisierte ZIP-Datei erneut auf dieselbe leere Landingpage importieren. Folgende Szenarien weisen Fehler auf:

* Das importierte Designpaket ist kein gültiges ZIP-Archiv.
* Das importierte Designpaket enthält kein index.html auf der obersten Ebene.

### Nach dem Import werden Warnmeldungen angezeigt {#warnings-displayed-after-import}

Wenn Warnhinweise vorhanden sind (z. B. bezieht sich HTML auf Bilder, die nicht im Paket enthalten sind), importiert das Design Importer die ZIP-Datei, zeigt aber gleichzeitig eine Liste mit Problemen/Warnungen im Ergebnisfenster an. Wenn Sie auf den Link Probleme klicken, wird eine Liste mit Warnungen angezeigt, die auf alle Probleme innerhalb des Designpakets hinweisen. Unter anderem werden in folgenden Fällen vom Design Importer Warnmeldungen erzeugt und angezeigt:

* HTML verweist auf Bilder, die im Paket nicht vorhanden sind.
* HTML verweist auf Skripte, die im Paket nicht vorhanden sind.
* HTML verweist auf Stile, die im Paket nicht vorhanden sind.

### Wo werden die Dateien der ZIP-Datei in AEM gespeichert? {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

Nachdem die Landingpage importiert wurde, werden die Dateien (Bilder, CSS, JS usw.) im Designpaket an folgendem Speicherort in AEM gespeichert:

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

Angenommen, die Landingpage wird unter der Kampagne We.Retail erstellt und der Name der Landingpage lautet **myBlankLandingPage** der Speicherort, an dem die ZIP-Dateien gespeichert werden, lautet wie folgt:

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### Formatierung nicht beibehalten {#formatting-not-preserved}

Beachten Sie beim Erstellen Ihres CSS die folgenden Einschränkungen:

Wenn ein Text- und (bearbeitbares) Bild wie folgt aussehen:

```xml
<div class="box">
<p><div data-cq-component="image"><img src="assets/image.jpg" width="115"
height="116" /></div>Some Text </p>
</div>
```

mit einem wie folgt auf die Klasse `box` angewendeten CSS:

```xml
.box

{ width: 450px; padding:10px; border: 1px #C5DBE7 solid; margin: 0px auto 0 auto; background-image:url(assets/box.gif); background-repeat:repeat-x,y; font-family:Verdana, Arial, Helvetica, sans-serif; font-size:12px; color:#6D6D6D; }
```

Dann `box img` im Design Importer verwendet wird, scheint die resultierende Landingpage die Formatierung nicht beibehalten zu haben. Um dies zu umgehen, fügt AEM div-Tags in das CSS hinzu und schreibt den Code entsprechend neu. Andernfalls sind einige CSS-Regeln ungültig.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
>
>Designer sollten nur Code innerhalb der **id=cqcanvas** -Tag vom Importtool erkannt wird, andernfalls wird das Design nicht beibehalten.
