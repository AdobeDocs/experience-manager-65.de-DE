---
title: Erweitern und Konfigurieren des Design-Import-Tools für Landing-Pages
description: Erfahren Sie, wie Sie den Design Importer für Landing Pages konfigurieren.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 1b8c6075-13c6-4277-b726-8dea7991efec
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3442'
ht-degree: 91%

---

# Erweitern und Konfigurieren des Design-Import-Tools für Landing-Pages{#extending-and-configuring-the-design-importer-for-landing-pages}

In diesem Abschnitt wird beschrieben, wie Sie den Design Importer für Einstiegsseiten konfigurieren und bei Bedarf erweitern. Die Arbeit mit Landing Pages nach dem Import wird im Abschnitt [Landing Pages](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md) behandelt.

**Extrahieren der benutzerdefinierten Komponente mit dem Design Importer**

Im Folgenden finden Sie die logischen Schritte, damit der Design Importer Ihre benutzerdefinierte Komponente erkennt

1. Erstellen eines Taghandlers

   * Ein Taghandler ist ein POJO, das HTML-Tags eines bestimmten Typs handelt. Welche Arten von HTML-Tags Ihr TagHandler verarbeiten kann, wird über die OSGi-Eigenschaft „tagpattern.name“ in der TagHandlerFactory definiert. Im Grunde handelt es sich bei der OSGi-Eigenschaft um einen RegEx, der dem Eingabe-HTML-Tag entsprechen sollte, das Sie handeln möchten. Alle verschachtelten Tags würden zum Handling an den Taghandler übergeben werden. Wenn Sie sich beispielsweise für ein div registrieren, das eine verschachtelte &lt;p> -Tag &lt;p> -Tag auch an Ihren TagHandler gesendet werden und es liegt an Ihnen, wie Sie darauf achten möchten.
   * Die Oberfläche des Taghandlers ähnelt der Oberfläche eines SAX-Inhaltshandlers. Sie erhält für jedes HTML-Tag SAX-Ereignisse. Als Anbieterin bzw. Anbieter des Tag-Handlers müssen Sie bestimmte Lebenszyklusmethoden implementieren, die automatisch vom Design Importer-Framework aufgerufen werden.

1. Erstellen Sie die entsprechende TagHandlerFactory.

   * Bei der TagHandlerFactory handelt es sich um eine OSGi-Komponente (Singleton), die dafür verantwortlich ist, Instanzen des TagHandlers zu erzeugen.
   * Ihre TagHandlerFactory muss eine OSGi-Eigenschaft mit dem Namen „tagpattern.name“ bereitstellen, deren Wert mit dem Eingabe-HTML-Tag abgeglichen wird.
   * Wenn mehrere Taghandler mit dem Eingabe-HTML-Tag übereinstimmen, wird jener mit dem höheren Rang gewählt. Der Rang selbst wird in der OSGi-Eigenschaft **service.ranking** angegeben.
   * Die TagHandlerFactory ist eine OSGi-Komponente. Alle Verweise, die Sie für Ihren TagHandler bereitstellen möchten, müssen über diese Factory erfolgen.

1. Stellen Sie sicher, dass Ihre TagHandlerFactory einen höheren Rang hat, wenn Sie den Standard überschreiben möchten.

>[!CAUTION]
>
>Der Design Importer, der zum Importieren von Landing Pages verwendet wurde, [ist seit AEM 6.5 veraltet](/help/release-notes/deprecated-removed-features.md#deprecated-features).

## Vorbereiten von HTML für den Import {#preparing-the-html-for-import}

Nachdem Sie eine Import-Tool-Seite erstellt haben, können Sie Ihre vollständige HTML-Landingpage importieren. Um Ihre HTML-Einstiegsseite zu importieren, müssen Sie den Inhalt zunächst zu einem Designpaket packen. Das Design-Paket enthält Ihre HTML-Landingpage zusammen mit den referenzierten Assets (Bilder, CSS, Symbole, Skripte usw.).

Die folgende Schnellübersicht enthält ein Beispiel für die Vorbereitung Ihrer HTML für den Import:

Landingpage-Schnellübersicht

[Datei laden](assets/cheatsheet.zip)

### Layout und Anforderungen für ZIP-Dateien {#zip-file-layout-and-requirements}

>[!NOTE]
>
>An dieser Stelle dürfen ZIP-Dateien nur eine HTML-Seite oder einen Seitenbereich enthalten.

Ein Beispiel für ein ZIP-Layout:

* /index.html > Landingpage-HTML-Datei
* /css > , um es der CSS-clientlib hinzuzufügen
* /img > alle Bilder und Assets
* /js > zur Hinzufügung in die JS-clientlib

Das Layout basiert auf dem Boilerplate-Layout für HTML5. Lesen Sie mehr unter [https://html5boilerplate.com/](https://html5boilerplate.com/).

>[!NOTE]
>
>Mindestens **muss** das Design-Paket eine **index.html**-Datei auf der Stammebene enthalten. Wenn es für die zu importierende Landingpage auch eine mobile Version gibt, muss die ZIP-Datei eine **mobile.index.html** zusammen mit **index.html** auf der Stammebene enthalten.

### Vorbereiten der HTML-Landingpage {#preparing-the-landing-page-html}

Um die HTML importieren zu können, müssen Sie der Landingpage-HTML ein Arbeitsflächen-div hinzufügen.

Das Arbeitsflächen-div ist ein HTML-**div** mit `id="cqcanvas"`, das in das HTML-`<body>`-Tag eingefügt werden muss und das den Inhalt für die Konvertierung umgeben muss.

Ein Beispielausschnitt der Landingpage-HTML nach dem Hinzufügen des Arbeitsflächen-div ist wie folgt:

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

### Vorbereiten der HTML, um bearbeitbare AEM-Komponenten einzuschließen {#preparing-the-html-to-include-editable-aem-components}

Beim Import einer Landingpage haben Sie die Möglichkeit, die Seite unverändert zu importieren. Das bedeutet, dass Sie nach dem Import der Landingpage keines der importierten Elemente in AEM bearbeiten können (Sie können auf der Seite noch weitere AEM-Komponenten hinzufügen).

Bevor Sie die Einstiegsseite importieren, empfiehlt es sich, einige Teile der Einstiegsseite in bearbeitbare AEM-Komponenten zu konvertieren. Dadurch können Sie auch nach dem Import des Landingpage-Designs Teile der Landingpage schnell bearbeiten.

Sie tun dies, indem Sie in der zu importierenden HTML-Datei der entsprechenden Komponente die `data-cq-component` hinzufügen.

Im folgenden Abschnitt wird beschrieben, wie Sie Ihre HTML-Datei so bearbeiten, dass bestimmte Teile der Einstiegsseiten in andere bearbeitbare AEM-Komponenten konvertiert werden. Die Komponenten werden unter [Komponenten von Landing Pages](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md) detailliert beschrieben.

>[!NOTE]
>
>HTML-Markup zum Konvertieren von Teilen der Einstiegsseiten in AEM-Komponenten verfügt sowohl über eine lange als auch über eine kurze Tag-Deklarierung. Beide werden für jede Komponente beschrieben.

### Beschränkungen {#limitations}

Beachten Sie vor dem Import die folgenden Einschränkungen:

### Jedes Attribut wie die Klasse oder ID, das auf das Tag &amp;lt;body> angewendet wird, wird nicht beibehalten {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

Wenn beispielsweise ein beliebiges Attribut wie ID oder Klasse auf das Body-Tag angewendet wird, `<body id="container">` nach dem Import nicht beibehalten. Das importierte Design darf also über keine Abhängigkeiten bei den Attributen verfügen, die auf das `<body>`-Tag angewendet werden.

### Verschieben einer Zip-Datei per Drag-and-Drop {#drag-and-drop-zip}

Ein Upload durch Verschieben einer Zip-Datei per Drag-and-Drop wird für Internet Explorer und Firefox-Versionen vor 3.6 nicht unterstützt. Um beim Verwenden dieser Browser ein Design hochzuladen, klicken Sie auf die Dateiablagezone, um ein Dialogfeld zum Hochladen von Dateien zu öffnen und Ihr Design mithilfe dieses Dialogfelds hochzuladen.

Die Browser, die das Hochladen der Design-ZIP-Datei per Drag-and-Drop unterstützen, sind Chrome, Safari 5.x, Firefox 4 und höher.

### Modernizr wird nicht unterstützt {#modernizr-is-not-supported}

`Modernizr.js` ist ein JavaScript-basiertes Hilfsmittel, das native Browser-Funktionen erkennt und ermittelt, ob sie für HTML5-Elemente geeignet sind. Bei Designs, die Modernizr für die verbesserte Unterstützung älterer Browserversionen verwenden, können Fehler in der Einstiegsseitenlösung auftreten. `Modernizr.js`-Skripts werden vom Design-Importer nicht unterstützt.

### Seiteneigenschaften werden zum Importzeitpunkt des Design-Pakets nicht beibehalten {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

Jede Seiteneigenschaft (z. B. benutzerdefinierte Domain, Erzwingen von HTTPS usw.), die für eine Seite festgelegt wurde (die eine leere Landingpage-Vorlage verwendet), bevor das Design-Paket importiert wird, geht nach dem Importieren des Design-Pakets verloren. Daher wird empfohlen, die Seiteneigenschaften erst nach dem Importieren des Design-Pakets festzulegen.

### Nur von HTML-Markup ausgegangen {#html-only-markup-assumed}

Beim Importieren wird das Markup aus Sicherheitsgründen bereinigt, um den Import und die Veröffentlichung von ungültigem Markup zu verhindern. Dabei wird davon ausgegangen, dass sämtliches reines HTML-Markup und alle anderen Elemente wie Inline-SVG oder Web-Komponenten herausgefiltert werden.

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

So fügen Sie einen Text mit Farbe (in diesem Fall pink) hinzu, der im RTE-Editor bearbeitet werden kann:

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

HTML-Markup, um eine Bildkomponente (wcm/landingpage/components/image) in den HTML-Code im Design-Paket einzufügen:

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

#### Absolute „img src“-URL wird im div-Tag der Bildkomponente nicht unterstützt {#absolute-url-img-src-not-supported-within-image-component-div}

Wenn ein `<img>`-Tag mit einer absoluten URL-src für die Komponenten-Konverstierung ausgewählt wird, wird ein entsprechender Ausnahmefehler **UnsupportedTagContentException** ausgegeben. So wird das folgende Beispiel nicht unterstützt:

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

Ansonsten werden aber absolute URL-Bilder für img-Tags unterstützt, die nicht Teil des div-Tags der Bildkomponente sind.

### Aktionsaufruf-Komponenten {#call-to-action-components}

Sie können einen Teil einer Landingpage für den Import als „bearbeitbare Aktionsaufruf-Komponente“ markieren. Solche importierten Komponenten für den Aktionsaufruf (Call-to-Action, CTA) können nach dem Import der Landingpage bearbeitet werden. AEM enthält die folgenden CTA-Komponenten:

* Clickthrough-Link: Sie können einen Text-Link hinzufügen. Wer auf diesen klickt, wird zu einer Ziel-URL weitergeleitet.
* Grafischer Link: Sie können ein Bild hinzufügen. Wer darauf klickt, wird zu einer Ziel-URL weitergeleitet.

#### Clickthrough-Link {#click-through-link}

Diese CTA-Komponente kann dazu verwendet werden, der Landingpage einen Text-Link hinzuzufügen.

Unterstützte Eigenschaften

* Label mit Optionen für Fettschrift, Kursivschrift und Unterstreichen
* Ziel-URL mit Unterstützung für Drittanbieter- und AEM-URLs
* Seiten-Render-Optionen („Identisches Fenster“, „Neues Fenster“ usw.)

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

Diese Komponente kann in jeder eigenständigen Anwendung verwendet oder aus einer ZIP-Datei importiert werden.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### Grafischer Link {#graphical-link}

Diese CTA-Komponente kann dazu verwendet werden, ein beliebiges grafisches Bild mit Link auf der Einstiegsseite hinzuzufügen. Beim Bild kann es sich um eine einfache Schaltfläche oder um ein grafisches Bild als Hintergrund handeln. Wenn der Benutzer auf das Bild klickt, wird er zur in den Komponenteneigenschaften angegebenen Ziel-URL weitergeleitet. Es ist Teil der Gruppe „Aktionsaufruf“.

Unterstützte Eigenschaften

* Beschneiden von Bildern, Drehen
* Hover-Text, Beschreibung, Größe in px
* Ziel-URL mit Unterstützung für Drittanbieter- und AEM-URLs
* Seiten-Render-Optionen („Identisches Fenster“, „Neues Fenster“ usw.)

HTML-Tag mit in der importierten ZIP-Datei enthaltenem grafischen Link: Hier ordnet href der Ziel-URL zu, img src ist das Rendering-Bild, &quot;title&quot;wird als Hover-Text verwendet usw.

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
>Zum Beispiel: `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>Andere Möglichkeiten, mit CSS ein Bild mit einem Anchortag zu verknüpfen werden nicht unterstützt. So funktioniert z. B. nicht das Markup
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
* Mithilfe dieser Komponenten kann der Autor ein eigenständiges Formular entwerfen. Diese Felder entsprechen den Lead-Formular-Feldern. In eigenständigen oder importierten ZIP-Anwendungen können Benutzende mit den Formularfeldern „cq:form“ oder „cta lead“ weitere Felder hinzufügen und diese ihren Anforderungen entsprechend benennen und entwerfen.
* Weisen Sie Lead-Formular-Felder mit bestimmten vordefinierten Namen des CTA-Lead-Formulars zu, z. B. - firstName für Vorname im Lead-Formular usw.
* Felder, die nicht dem Lead-Formular zugewiesen sind, werden cq:form-Komponenten (Text, Optionsfeld, Kontrollkästchen, Dropdown, verborgenes Feld, Kennwort) zugeordnet.
* Benutzende können den Titel mit dem Tag „Beschriften“ und Stile mit dem Stilattribut „Klasse“ angeben (nur für CTA-Lead-Formular-Komponenten verfügbar).
* Die Dankeseite und die Abonnement-Liste können als versteckte Parameter des Formulars (vorhanden in der Datei „index.htm“) bereitgestellt werden oder über die Bearbeitungsleiste von „Start des Lead-Formulars“ hinzugefügt oder bearbeitet werden.

  &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

  &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* Beschränkungen wie „Erforderlich“ können in jeder der Komponenten unter „Konfiguration bearbeiten“ angegeben werden.

HTML-Tag mit in der importierten Zip enthaltenem grafischen Link: Hier verweist „firstName“ auf das Feld „firstName“ auf dem Lead-Formular usw. Eine Ausnahme bilden Kontrollkästchen. Die beiden folgenden Kontrollkästchen verweisen auf die Dropdown-Komponente „cq:form“.

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

Das AEM-parsys ist eine Container-Komponente, die andere AEM-Komponenten enthalten kann. Es ist möglich, der importierten HTML eine parsys-Komponente hinzuzufügen. Dadurch können Benutzende bearbeitbare AEM-Komponenten zur Landingpage hinzufügen bzw. daraus löschen, selbst nachdem sie importiert wurde.

Das Absatzsystem bietet Benutzenden die Möglichkeit, mithilfe des Sidekicks Komponenten hinzuzufügen.

HTML-Markup zum Einfügen einer parsys-Komponente (`foundation/components/parsys`) in das HTML im Designpaket:

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

Durch Integration des oben genannten Markups in den HTML-Code geschieht Folgendes:

* Es wird eine AEM-parsys-Komponente (foundation/components/parsys) in die Landingpage eingefügt, die nach dem Importieren des Design-Pakets erstellt wurde.
* Startet den Sidekick mit Standardkomponenten. Neue Komponenten können zur Landingpage hinzugefügt werden, indem Komponenten aus dem Sidekick in die parsys-Komponente gezogen werden.
* Zwei Titelkomponenten sind ebenfalls Teil des Absatzsystems.

### Ziel {#target}

Die target-Komponente zeigt den Inhalt eines Erlebnisses auf der Seite an. In einer Kampagne können mehrere Erlebnisse erstellt werden, und die Zielkomponente kann verschiedenen Besucherinnen und Besuchern der Seite dynamisch Inhalte aus verschiedenen Erlebnissen präsentieren.

HTML-Markup, um eine Zielkomponente in eine Kampagne einzufügen und dort verschiedene Erlebnisse zu erstellen:

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

## Weitere Importoptionen {#additional-importing-options}

Neben der Angabe, ob importierte Komponenten bearbeitbare AEM-Komponenten sind, können Sie vor dem Importieren des Design-Pakets auch Folgendes konfigurieren:

* Festlegen von Seiteneigenschaften durch Extrahieren der im HTML-Import definierten Metadaten
* Angeben der Zeichensatzkodierung im HTML-Code
* Überlagern der Seitenvorlage des Import-Tools

### Festlegen von Seiteneigenschaften durch Extrahieren der im HTML-Import definierten Metadaten {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

Die folgenden im Kopfteil des HTML-Imports deklarierten Metadaten werden vom Design-Import-Tool als Eigenschaft „jcr:description“ extrahiert und beibehalten:

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

Das im HTML-Tag festgelegte lang-Attribut wird vom Design-Import-Tool als Eigenschaft „jrc:language“ extrahiert und beibehalten:

* &lt;html lang=&quot;en&quot;>

### Angeben der Zeichensatzkodierung im HTML-Code {#specifying-the-charset-encoding-in-the-html}

Der Design Importer liest die im importierten HTML festgelegte Kodierung. Die Kodierung kann wie folgt festgelegt werden:

`<meta charset="UTF-8">`

*ODER*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

Wenn im HTML-Import keine Kodierung angegeben ist, ist die vom Design-Import-Tool festgelegte Standardkodierung UTF-8.

### Überlagern der Vorlage {#overlaying-template}

Die Vorlage für leere Landingpages kann überlagert werden, indem Sie eine Vorlage erstellen unter: `/apps/<appName>/designimporter/templates/<templateName>`

Die Schritte zum Erstellen einer Vorlage in AEM werden erläutert. [here](/help/sites-developing/templates.md).

### Verweisen auf eine Komponente von der Landingpage {#referring-a-component-from-landing-page}

Angenommen, Sie verfügen über eine Komponente, auf die Sie in Ihrem HTML mit dem data-cq-component-Attribut verweisen möchten, sodass der Design Importer an dieser Stelle eine Komponente rendert. Sie möchten z. B. auf die Tabellenkomponente (`resourceType = /libs/foundation/components/table`) verweisen. Sie müssen das HTML wie folgt ergänzen:

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

Der Pfad in „data-cq-component“ sollte der resourceType der Komponente sein.

### Best Practices {#best-practices}

Die Verwendung von CSS-Selektoren wie den folgenden wird bei Elementen, die für eine Komponentenkonvertierung beim Import vorgesehen sind, nicht empfohlen.

| E > F | ein einem E-Element untergeordnetes F-Element | [Untergeordneter Kombinator](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | ein F-Element, dem ein E-Element unmittelbar vorhergeht | [Angrenzender gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | F-Element, dem ein E-Element vorausgeht | [Allgemeiner gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | ein E-Element, Stamm des Dokuments | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | ein E-Element, das n-te untergeordnete Element des übergeordneten Elements | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | ein E-Element, das n-te untergeordnete Element des übergeordneten Elements, gerechnet ab dem letzten | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | E-Element, das n-te gleichrangige Element seines Typs | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | ein E-Element, das n-te gleichrangige Element seines Typs, gerechnet ab dem letzten | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

Dies liegt daran, dass dem generierten HTML-Code nach dem Import zusätzliche HTML-Elemente wie das &lt;div>-Tag hinzugefügt werden.

* Skripte, die auf einer ähnlichen Struktur wie der obigen basieren, werden ebenfalls nicht für Elemente empfohlen, die für die Konvertierung in AEM-Komponenten vorgesehen sind.
* Die Verwendung von Stilen in den Markup-Tags für die Komponentenkonvertierung wie &lt;div data-cq-component=&quot;&amp;ast;&quot;> wird nicht empfohlen.
* Beim Designlayout sollten die Best Practices für das HTML5-Boilerplate befolgt werden. Lesen Sie mehr unter [https://html5boilerplate.com/](https://html5boilerplate.com/).

## Konfigurieren von OSGi-Modulen {#configuring-osgi-modules}

Folgende Komponenten geben Eigenschaften an, die über die OSGi-Konsole konfiguriert werden können:

* Design-Import-Tool für Landingpages
* Builder für Landingpages
* Builder für Mobile-Landingpages
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
   <td>Design-Import-Tool für Landingpages</td>
   <td>Extraktionsfilter</td>
   <td>Die Liste der regulären Ausdrücke, die für das Filtern der Dateien beim Extrahieren verwendet werden. <br />Zip-Einträge, die einem der angegebenen Muster entsprechen, werden von der Extraktion ausgeschlossen.</td>
  </tr>
  <tr>
   <td>Builder für Landingpages</td>
   <td>Dateimuster</td>
   <td>Der Builder für die Landingpage kann so konfiguriert werden, dass er HTML-Dateien verwaltet, die einem bestimmten im Dateimuster definierten regulären Ausdruck entsprechen.</td>
  </tr>
  <tr>
   <td>Builder für Mobile-Landingpages</td>
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
   <td>Das Muster, das die gefundenen Übereinstimmungen ersetzt. Sie können Gruppenreferenzen für reguläre Ausdrücke wie $1, $2 verwenden. Zudem unterstützt dieses Muster Schlüsselwörter wie {designPath}, die während des Imports mit den tatsächlichen Werten aufgelöst werden.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>**Aktuelle Beschränkung des Eintrags-Präprozessors für Landing Pages:**
>Wenn Sie Änderungen am Suchmuster vornehmen müssen, müssen Sie beim Öffnen des Felix Property Editor manuell umgekehrte Schrägstriche einfügen, um die regex-Metazeichen auszukommentieren. Wenn Sie umgekehrte Schrägstriche nicht manuell einfügen, wird der reguläre Ausdruck als ungültig angesehen und ersetzt nicht die ältere Version.
>
>Beispiel: Die Standardkonfiguration lautet wie folgt:
>
>>`/\* *CQ_DESIGN_PATH *\*/ *(['"])`
>
>Und Sie müssen `CQ_DESIGN_PATH` mit `VIPURL` im Suchmuster ein, sollte Ihr Suchmuster wie folgt aussehen:
>
>`/\* *VIPURL *\*/ *(['"])`

## Fehlerbehebung {#troubleshooting}

Beim Importieren des Design-Pakets können verschiedene Fehler auftreten, die in diesem Abschnitt beschrieben werden.

### Initialisierung des Sidekicks mit für die Landingpage relevanten Komponenten {#initialization-of-sidekick-with-landing-page-relevant-components}

Wenn das Designpaket ein parsys-Komponenten-Markup enthält, werden nach dem Import im Sidekick für Einstiegsseiten relevante Komponenten angezeigt. Sie können neue Komponenten per Drag-and-Drop auf die parsys-Komponente in der Einstiegsseite ziehen. Sie können auch den Design-Modus aufrufen und dem Sidekick neue Komponenten hinzufügen.

### Während des Imports werden Fehlermeldungen angezeigt {#error-messages-displayed-during-import}

Wenn Fehler aufgetreten sind (das importierte Paket ist beispielsweise keine gültige ZIP-Datei), wird das Paket beim Design-Import nicht importiert. Stattdessen wird oben auf der Seite direkt über dem Drag-and-Drop-Feld eine Fehlermeldung angezeigt. Hier werden Beispiele für Fehlerszenarios aufgeführt. Wenn Sie den Fehler korrigiert haben, können Sie die aktualisierte ZIP-Datei erneut in dieselbe leere Landingpage importieren. In folgenden unterschiedlichen Szenarien werden Fehler gemeldet:

* Das importierte Design-Paket ist kein gültiges ZIP-Archiv.
* Das importierte Designpaket enthält kein index.html auf der obersten Ebene.

### Nach dem Import werden Warnmeldungen angezeigt {#warnings-displayed-after-import}

Wenn Warnungen angezeigt werden (z. B. „HTML verweist auf Bilder, die nicht im Paket enthalten sind“), importiert das Design-Import-Tool das ZIP-Archiv, zeigt aber gleichzeitig im Ergebnisbereich eine Liste mit Problemen/Warnungen an. Wenn Sie auf den Problem-Link klicken, wird eine Liste mit Warnungen angezeigt, die auf Probleme innerhalb des Design-Pakets verweisen. Unter anderem werden in folgenden Fällen vom Design Importer Warnmeldungen erzeugt und angezeigt:

* HTML verweist auf Bilder, die im Paket nicht vorhanden sind.
* HTML verweist auf Skripte, die im Paket nicht vorhanden sind.
* HTML verweist auf Stile, die im Paket nicht vorhanden sind.

### Speicherort für die Dateien im ZIP-Archiv in AEM {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

Nachdem die Landingpage importiert wurde, werden die Dateien (Bilder, CSS, JS usw.) im Design-Paket unter folgendem Pfad in AEM gespeichert:

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

Angenommen, die Landingpage wird im Rahmen der Kampagne erstellt. `We.Retail` und der Name der Landingpage lautet **myBlankLandingPage** der Speicherort, an dem die ZIP-Dateien gespeichert werden, lautet wie folgt:

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### Nicht beibehaltene Formatierung {#formatting-not-preserved}

Beachten Sie bei der CSS-Erstellung die folgenden Einschränkungen:

Bei einem Text und einem (bearbeitbaren) Bild wie:

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

`box img` wird dann im Design-Import-Tool verwendet. Die daraus resultierende Landinpage wird scheinbar ohne die entsprechende Formatierung angezeigt. Um dieses Problem zu umgehen, fügt AEM im CSS div-Tags hinzu. Schreiben Sie daher den Code entsprechend um. Andernfalls werden einige CSS-Regeln ungültig sein.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
>
>Designer sollten nur Code innerhalb der **id=cqcanvas** -Tag vom Importtool erkannt wird, andernfalls wird das Design nicht beibehalten.
