---
title: Erweitern und Konfigurieren des Design-Importtools für Einstiegsseiten
seo-title: Erweitern und Konfigurieren des Design-Importtools für Einstiegsseiten
description: Erfahren Sie, wie Sie den Design Importer für Einstiegsseiten konfigurieren.
seo-description: Erfahren Sie, wie Sie den Design Importer für Einstiegsseiten konfigurieren.
uuid: a2dd0c30-03e4-4e52-ba01-6b0b306c90fc
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: e02f5484-fbc2-40dc-8d06-ddb53fd9afc2
docset: aem65
exl-id: 1b8c6075-13c6-4277-b726-8dea7991efec
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '3522'
ht-degree: 77%

---

# Erweitern und Konfigurieren des Design-Importtools für Einstiegsseiten{#extending-and-configuring-the-design-importer-for-landing-pages}

In diesem Abschnitt wird beschrieben, wie Sie den Design Importer für Einstiegsseiten konfigurieren und bei Bedarf erweitern. Das Arbeiten mit Einstiegsseiten nach dem Import wird unter [Einstiegsseiten](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md) erläutert.

**Extrahieren der benutzerdefinierten Komponente durch den Design Importer**

Nutzen Sie die folgenden logischen Schritte, um Ihre benutzerdefinierte Komponente durch den Design Importer erkennen zu lassen

1. Erstellen eines Taghandlers

   * Ein Taghandler ist ein POJO, das HTML-Tags eines bestimmten Typs handelt. Welche HTML-Tags Ihr Taghandler handeln kann, wird über die OSGi-Eigenschaft „tagpattern.name“ in der TagHandlerFactory definiert. Im Grunde handelt es sich bei der OSGi-Eigenschaft um einen RegEx, der dem Eingabe-HTML-Tag entsprechen sollte, das Sie handeln möchten. Alle verschachtelten Tags würden zum Handling an den Taghandler übergeben werden. Wenn Sie sich z. B. für ein div registrieren, das ein verschachteltes &lt;p>-Tag enthält, wird das &lt;p>-Tag ebenfalls an den Taghandler übermittelt und Sie können entscheiden, wie Sie damit umgehen möchten.
   * Die Oberfläche des Taghandlers ähnelt der Oberfläche eines SAX-Inhaltshandlers. Sie erhält für jedes HTML-Tag SAX-Ereignisse. Als Anbieter eines Taghandlers müssen Sie bestimmte Lebenszyklusmethoden implementieren, die automatisch vom Design-Importer-Framework abgerufen werden.

1. Erstellen Sie die entsprechende TagHandlerFactory.

   * Bei der TagHandlerFactory handelt es sich um eine OSGi-Komponente (Singleton), die dafür verantwortlich ist, Instanzen des Taghandlers zu erzeugen.
   * Ihre TagHandlerFactory muss eine OSGi-Eigenschaft mit dem Namen „tagpattern.name“ bereitstellen, deren Wert mit dem Eingabe-HTML-Tag abgeglichen wird.
   * Wenn mehrere Taghandler mit dem Eingabe-HTML-Tag übereinstimmen, wird jener mit dem höheren Rang gewählt. Der Rang selbst wird als OSGi-Eigenschaft **service.ranking** bereitgestellt.
   * Die TagHandlerFactory ist eine OSGi-Komponente. Sämtliche Verweise auf den Taghandler müssen über diese Factory erfolgen.

1. Stellen Sie sicher, dass Ihre TagHandlerFactory einen höheren Rang hat, wenn Sie den Standard überschreiben möchten.

>[!CAUTION]
>
>Das Design-Importtool, das zum Import von Landingpages verwendet wurde, [ist ab AEM 6.5 veraltet](/help/release-notes/deprecated-removed-features.md#deprecated-features).

## Vorbereiten des HTML für den Import {#preparing-the-html-for-import}

Wenn Sie eine leere Importer-Seite erstellt haben, können Sie Ihre komplette HTML-Einstiegsseite importieren. Um Ihre HTML-Einstiegsseite zu importieren, müssen Sie den Inhalt zunächst zu einem Designpaket packen. Das Designpaket enthält Ihre HTML-Einstiegsseite sowie die Assets, auf die verwiesen wird (Bilder, CSS, Symbole, Skripts usw.).

Der folgende Spickzettel enthält ein Beispiel dafür, wie Sie Ihr HTML für den Import vorbereiten können:

Landingpage-Spickzettel

[Datei laden](assets/cheatsheet.zip)

### Zip-Datei-Layout und -Anforderungen {#zip-file-layout-and-requirements}

>[!NOTE]
>
>Zurzeit können Zip-Dateien nur eine HTML-Seite oder einen Teil einer Seite enthalten.

Unten sehen Sie ein Beispiellayout einer Zip-Datei:

* /index.html -> HTML-Datei der Einstiegsseite
* /css -> für das Hinzufügen zur CSS-clientlib
* /img -> alle Bilder und Assets
* /js -> für das Hinzufügen zur JS-clientlib

Das Layout basiert auf dem Boilerplate-Layout für HTML5. Weitere Informationen finden Sie unter [https://html5boilerplate.com/](https://html5boilerplate.com/)

>[!NOTE]
>
>Das Designpaket **muss** auf jeden Fall im Stammverzeichnis eine Datei **index.html** enthalten. Wenn die zu importierende Einstiegsseite auch über eine mobile Version verfügt, muss die Zip-Datei im Stammverzeichnis über eine Datei **mobile.index.html** sowie eine Datei **index.html** verfügen.

### Vorbereiten des Einstiegsseiten-HTML {#preparing-the-landing-page-html}

Um das HTML importieren zu können, benötigen Sie ein Leinwand-div zum Einstiegsseiten-HTML.

Das Leinwand-div ist ein HTML **div** mit `id="cqcanvas"` , das in das HTML-Tag `<body>` eingefügt werden muss und den Inhalt für die Konvertierung umgeben muss.

Ein Beispiel-Snippet des Einstiegsseiten-HTML nach dem Hinzufügen des Leinwand-div sieht wie folgt aus:

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

### Vorbereiten der HTML, sodass es bearbeitbare AEM-Komponenten enthält  {#preparing-the-html-to-include-editable-aem-components}

Wenn Sie eine Einstiegsseite importieren, können Sie die Seite im aktuellen Zustand importieren, was bedeutet, dass Sie nach dem Import der Einstiegsseite in AEM keine Änderungen an den importierten Elementen vornehmen können (Sie können der Seite jedoch weitere AEM-Komponenten hinzufügen).

Bevor Sie die Einstiegsseite importieren, empfiehlt es sich, einige Teile der Einstiegsseite in bearbeitbare AEM-Komponenten zu konvertieren. Dadurch können Sie auch nach dem Import des Einstiegsseitendesigns Teile der Einstiegsseite schnell bearbeiten.

Sie tun dies, indem Sie in der zu importierenden HTML-Datei der entsprechenden Komponente die `data-cq-component` hinzufügen.

Im folgenden Abschnitt wird beschrieben, wie Sie Ihre HTML-Datei so bearbeiten, dass bestimmte Teile der Einstiegsseiten in andere bearbeitbare AEM-Komponenten konvertiert werden. Die Komponenten werden im Detail unter [Komponenten von Einstiegsseiten](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md) beschrieben.

>[!NOTE]
>
>HTML-Markup zum Konvertieren von Teilen der Einstiegsseiten in AEM-Komponenten verfügt sowohl über eine lange als auch über eine kurze Tag-Deklarierung. Beide werden für jede Komponente beschrieben.

### Beschränkungen {#limitations}

Beachten Sie vor dem Import die folgenden Beschränkungen:

### Sämtliche Attribute wie „class“ oder „id“, die auf das   &amp;lt;body>-Tag angewendet werden, werden nicht beibehalten.  {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

Wenn ein beliebiges Attribut wie ID oder Klasse auf das Body-Tag angewendet wird, z. B. `<body id="container">`, wird es nach dem Import nicht mehr beibehalten. Daher sollte das importierte Design keine Abhängigkeiten von den Attributen haben, die auf das Tag `<body>` angewendet werden.

### Drag-and-Drop-Zip {#drag-and-drop-zip}

Das Hochladen von ZIP-Dateien per Drag-and-Drop wird für Internet Explorer und Firefox Version 3.6 und frühere Versionen nicht unterstützt. Wenn Sie einen dieser Browser verwenden, klicken Sie beim Upload eines Designs auf die Dateiablagezone, um ein Dialogfeld für den Dateiupload zu öffnen und Ihr Design so hochzuladen.

Unterstützt wird der Drag-and-Drop-Upload der Design-Zip von folgenden Browsern: Chrome, Safari 5.x, Firefox 4 und höher.

### Modernizr wird nicht unterstützt {#modernizr-is-not-supported}

`Modernizr.js` ist ein Javascript-basiertes Hilfsmittel, das native Browserfunktionen erkennt und ermittelt, ob sie für HTML5-Elemente geeignet sind. Bei Designs, die Modernizr für die verbesserte Unterstützung älterer Browserversionen verwenden, können Fehler in der Einstiegsseitenlösung auftreten. `Modernizr.js`-Skripts werden vom Design-Importer nicht unterstützt.

### Seiteneigenschaften bleiben beim Import von Designpaketen nicht erhalten {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

Jede Seiteneigenschaft (z. B. „Benutzerdefinierte Domäne“, „HTTPS erzwingen“ usw.), die für eine (mit der Vorlage „Leere Startseite“ erstellte) Seite vor dem Import des Designpakets festgelegt wurde, geht verloren, nachdem das Design importiert wurde. Aus diesem Grund wird empfohlen, die Seiteneigenschaften nach dem Import des Designpakets festzulegen.

### Nur HTML-Markup angenommen  {#html-only-markup-assumed}

Nach dem Importieren wird das Markup aus Sicherheitsgründen bereinigt, um den Import und die Veröffentlichung von ungültigem Markup zu verhindern. Dabei wird davon ausgegangen, dass sämtliches reines HTML-Markup und alle anderen Elemente Wie Inline-SVG oder Webkomponenten herausgefiltert werden.

### Text {#text}

HTML-Markup zum Einfügen einer text-Komponente (`foundation/components/text`) in das HTML im Designpaket:

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Erstellt eine bearbeitbare AEM-Textkomponente ( `sling:resourceType=foundation/components/text`) in der Landingpage, die nach dem Import des Designpakets erstellt wurde.
* Die Eigenschaft `text` der erstellten Komponente „text“ wird auf das im `div` eingeschlossene HTML gesetzt.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**Text mit einer Liste**

So fügen Sie Text mit einer Liste hinzu:

* 1.
* 2.

der in einem RTE-Editor bearbeitet werden kann:

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**Text mit Farbe**

So fügen Sie Text mit Farbe (pink) hinzu, der im RTE-Editor bearbeitet werden kann:

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### Titel {#title}

HTML-Markup zum Einfügen einer Titelkomponente ( `wcm/landingpage/components/title`) in den HTML-Code im Designpaket:

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Erstellt eine bearbeitbare AEM ( `sling:resourceType=wcm/landingpage/components/title`) in der Landingpage, die nach dem Import des Designpakets erstellt wurde.
* Stellt die Eigenschaft `jcr:title`   der erstellten title-Komponente auf den Text ein, der im div in das Überschriften-Tag eingeschlossen ist.
* Stellt die Eigenschaft `type` des Überschriften-Tags ein, in diesem Fall `h1`.

Die Titelkomponente unterstützt 7 Typen: `h1, h2, h3, h4, h5, h6` und `default`.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### Bild {#image}

HTML-Markup zum Einfügen einer image-Komponente (foundation/components/image) in das HTML im Designpaket:

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Erstellt eine bearbeitbare AEM Bildkomponente ( `sling:resourceType=foundation/components/image`) in der Landingpage, die nach dem Import des Designpakets erstellt wurde.
* Stellt die Eigenschaft `fileReference` der erstellten image-Komponente auf den Pfad ein, in den das im src-Attribut angegebene Bild importiert wird.
* Legt für die Eigenschaft `alt` den Wert des alt-Attributs im img-Tag fest.
* Legt für die Eigenschaft `title` den Wert des title-Attributs im img-Tag fest.
* Legt für die Eigenschaft `width` den Wert des width-Attributs im img-Tag fest.
* Legt für die Eigenschaft `height` den Wert des Attributs height im img -Tag fest.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### Absoluter URL „img src“ wird im div der image-Komponente nicht unterstützt  {#absolute-url-img-src-not-supported-within-image-component-div}

Wenn ein `<img>` -Tag mit einer absoluten URL-src für die Komponentenkonvertierung versucht wird, wird eine geeignete **UnsupportedTagContentException** -Ausnahme ausgelöst. So wird das folgende Beispiel nicht unterstützt:

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

Andernfalls werden absolute URL-Bilder für img-Tags unterstützt, die nicht Teil des Bildkomponenten-div sind.

### Aktionsaufruf-Komponenten (CTA)  {#call-to-action-components}

Sie können einen Teil einer zu importierenden Einstiegsseite als „bearbeitbare Aktionsaufruf-Komponente“ markieren. Solche importierten Aktionsaufruf-Komponenten können nach dem Import der Einstiegsseite bearbeitet werden. AEM enthält die folgenden CTA-Komponenten:

* Click Through-Link - Sie können einen Textlink hinzufügen. Wenn der Besucher auf diesen klickt, wird er zu einer Ziel-URL weitergeleitet.
* Grafischer Link – Sie können ein Bild hinzufügen. Wenn der Besucher darauf klickt, wird er zu einer Ziel-URL weitergeleitet.

#### Click Through-Link  {#click-through-link}

Diese CTA-Komponente kann dazu verwendet werden, der Einstiegsseite einen Textlink hinzuzufügen.

Unterstützte Eigenschaften

* Etikett mit Optionen für fette, kursive oder unterstrichene Schrift
* Ziel-URL, unterstützt Drittanbieter- und AEM-URL
* Seiten-Render-Optionen („Identisches Fenster“, „Neues Fenster“ usw.)

HTML-Tag mit in der importierten Zip enthaltener Click Through-Komponente: Hier verweist „href“ auf die Ziel-URL, „Produktdetails anzeigen“ auf Etikett usw.

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

Diese Komponente kann in jeder eigenständigen Anwendung verwendet oder aus einer Zip-Datei importiert werden.

**Kurze Komponenten-Tag-Deklaration**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### Grafischer Link {#graphical-link}

Diese CTA-Komponente kann dazu verwendet werden, ein beliebiges grafisches Bild mit Link auf der Einstiegsseite hinzuzufügen. Beim Bild kann es sich um eine einfache Schaltfläche oder um ein grafisches Bild als Hintergrund handeln. Wenn der Benutzer auf das Bild klickt, wird er zur in den Komponenteneigenschaften angegebenen Ziel-URL weitergeleitet. All diese Beispiele sind Teil der Gruppe „Aktionsaufruf“.

Unterstützte Eigenschaften

* Beschneiden und Drehen von Bildern
* Hovertext, Beschreibung, Größe in Pixeln
* Ziel-URL, unterstützt Drittanbieter- und AEM-URL
* Seiten-Render-Optionen („Identisches Fenster“, „Neues Fenster“ usw.)

HTML-Tag mit in der importierten Zip enthaltenem grafischen Link: Hier verweist „href“ auf die Ziel-URL, „img src“ ist das Render-Bild, „title“ wird als Hovertext verwendet usw.

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
>Um einen Clickthrough-grafischen Link zu erstellen, müssen Sie ein Anker-Tag und das Bild-Tag in ein div mit dem Attribut `data-cq-component="clickthroughgraphicallink"` einschließen.
>
>Beispiel:`<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>Andere Möglichkeiten, mit CSS ein Bild mit einem Anchortag zu verknüpfen werden nicht unterstützt. So funktioniert z. B. das folgende Markup nicht:
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>mit zugewiesenem `css .hasbackground { background-image: pathtoimage }`


### Lead-Formular {#lead-form}

Ein Lead-Formular ist ein Formular, das dazu verwendet wird, die Informationen eines Besuchers/Leads zu sammeln. Diese Informationen können gespeichert und später dazu verwendet werden, anhand dieser Informationen effizientes Marketing durchzuführen. Die Informationen enthalten im Allgemeinen Titel, Namen, E-Mail, Geburtsdatum, Adresse, Interessen usw. Sie ist Teil der Gruppe &quot;CTA-Lead-Formular&quot;.

**Unterstützte Funktionen**

* Vordefinierte Lead-Felder - Vorname, Nachname, Adresse, Dob, Geschlecht, Info, UserId, emailId, Senden-Schaltfläche sind im Sidekick verfügbar. Platzieren Sie die erforderliche Komponente einfach per Drag-and-Drop in Ihrem Lead-Formular.
* Mithilfe dieser Komponenten kann der Autor ein eigenständiges Formular entwerfen. Diese Felder entsprechen den Lead-Formular-Feldern. In eigenständigen oder importierten Zip-Anwendungen kann der Benutzer mit den Formularfeldern „cq:form“ oder „cta lead“ weitere Felder hinzufügen und diese seinen Anforderungen entsprechend benennen und entwerfen.
* Weisen Sie Lead-Formular-Felder mithilfe bestimmter vordefinierter Namen des CTA-Lead-Formulars zu, z. B. - firstName für Vorname im Lead-Formular usw.
* Felder, die nicht dem Lead-Formular zugewiesen sind, werden cq:form-Komponenten zugewiesen: Text, Optionsschalter, Kontrollkästchen, Dropdown, Verborgen, Kennwort.
* Benutzer können den Titel mit dem Tag „label“ und Stile mit dem Stilattribut „class“ angeben (nur für CTA-Lead-Formular-Komponenten verfügbar).
* Die Dankeseite und die Abonnementliste können als ausgeblendeter Parameter des Formulars (in der index.htm) bereitgestellt oder über die Bearbeitungsleiste von &quot;Start des Lead-Formulars&quot;hinzugefügt/bearbeitet werden.

   &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot; />

   &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot; />

* Einschränkungen wie - erforderlich können aus der Bearbeitungskonfiguration jeder Komponente bereitgestellt werden.

HTML-Tag mit in der importierten Zip enthaltenem grafischen Link: Hier wird „firstName“ dem Feld „firstName“ auf dem Lead-Formular zugewiesen usw. Eine Ausnahme bilden Kontrollkästchen. Diese beiden Kontrollkästchen werden der Dropdown-Komponente „cq:form“ zugewiesen.

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

### ParSys {#parsys}

Das AEM-parsys ist eine Container-Komponente, die andere AEM-Komponenten enthalten kann. Es ist möglich, in das importierte HTML eine parsys-Komponente einzufügen. Dadurch kann der Benutzer auch nach dem Import der Einstiegsseite AEM-Komponenten hinzufügen/löschen.

Das Absatzsystem bietet Benutzern die Möglichkeit, Komponenten über den Sidekick hinzuzufügen.

HTML-Markup zum Einfügen einer parsys-Komponente (`foundation/components/parsys`) in das HTML im Designpaket:

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

Durch die Integration des oben genannten Markups in das HTML passiert Folgendes:

* Fügt eine AEM-parsys-Komponente (foundation/components/parsys) in die Einstiegsseite ein, die nach dem Import des Designpakets erstellt wurde.
* Startet den Sidekick mit Standardkomponenten. Neue Komponenten können der Einstiegsseite hinzugefügt werden, indem sie aus dem Sidekick auf die parsys-Komponente gezogen werden.
* Zwei title-Komponenten sind ebenfalls Teil des parsys.

### Target {#target}

Die target-Komponente zeigt den Inhalt eines Erlebnisses auf der Seite an. In einer Kampagne können mehrere Erlebnisse erstellt werden und die Zielkomponente kann verschiedenen Besuchern der Seite dynamisch Inhalte aus verschiedenen Erlebnissen anzeigen.

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

Sie können nicht nur angeben, ob es sich bei importierten Komponenten um bearbeitbare AEM-Komponenten handeln soll, sondern auch die folgenden Optionen konfigurieren, bevor Sie das Designpaket importieren:

* Einrichten von Seiteneigenschaften durch Extrahieren der im importierten HTML definierten Metadaten
* Angeben der charset-Kodierung im HTML
* Überlagern der Importer-Seitenvorlage

### Einrichten von Seiteneigenschaften durch Extrahieren der im importierten HTML definierten Metadaten  {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

Die folgenden im Kopf des importierten HTML deklarierten Metadaten werden vom Design Importer als Eigenschaft „jcr:description“ extrahiert und beibehalten:

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

Das im HTML-Tag festgelegte lang-Attribut wird vom Design Importer als Eigenschaft „jrc:language“ extrahiert und beibehalten:

* &lt;html lang=&quot;en&quot;>

### Angeben der charset-Kodierung im HTML {#specifying-the-charset-encoding-in-the-html}

Der Design Importer liest die im importierten HTML festgelegte Kodierung. Die Kodierung kann wie folgt festgelegt werden:

`<meta charset="UTF-8">`

*ODER*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

Wenn im importierten HTML keine Kodierung festgelegt ist, wird vom Design Importer UTF-8 als Standardkodierung festgelegt.

### Überlagern von Vorlagen  {#overlaying-template}

Die Vorlage für leere Einstiegsseiten kann überlagert werden, indem Sie eine neue Vorlage erstellen unter: `/apps/<appName>/designimporter/templates/<templateName>`

Die Schritte zum Erstellen einer neuen Vorlage in AEM werden [hier](/help/sites-developing/templates.md) erläutert.

### Verweisen auf eine Komponente von der Einstiegsseite {#referring-a-component-from-landing-page}

Angenommen, Sie verfügen über eine Komponente, auf die Sie in Ihrem HTML mit dem data-cq-component-Attribut verweisen möchten, sodass der Design Importer an dieser Stelle eine Komponente rendert. Sie möchten beispielsweise auf die Tabellenkomponente ( `resourceType = /libs/foundation/components/table`) verweisen. Sie müssen das HTML wie folgt ergänzen:

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

Beim Pfad in der data-cq-component muss es sich um den resourceType der Komponente handeln.

### Best Practices {#best-practices}

Die Verwendung von CSS-Auswahlen, die den folgenden ähneln, wird bei der Verwendung mit Elementen, die für die Komponentenkonvertierung oder den Import markiert sind, nicht empfohlen.

| E > F | ein einem E-Element untergeordnetes F-Element | [Untergeordneter Kombinator](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E > F | ein F-Element, dem ein E-Element unmittelbar vorhergeht | [Angrenzender gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | ein F-Element, dem ein E-Element vorhergeht | [Allgemeiner gleichrangiger Kombinator](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | ein E-Element, Stamm des Dokuments | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | ein E-Element, das n. untergeordnete Element des übergeordneten Elements | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | ein E-Element, das n. untergeordnete Element des übergeordneten Element, mit der Zählung beim letzten beginnend | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | ein E-Element, das n. gleichrangige Element seines Typs | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | ein E-Element, das n. gleichrangige Element seines Typs, mit der Zählung beim letzten beginnend | [Strukturelle Pseudoklassen](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

Dies liegt daran, dass dem generierten HTML nach dem Import zusätzliche HTML-Elemente wie das &lt;div>-Tag hinzugefügt werden.

* Skripts, die auf einer ähnlichen Struktur basieren, werden ebenfalls nicht für die Verwendung mit Elementen empfohlen, die für die Konvertierung in AEM-Komponenten vorgesehen sind.
* Die Verwendung von Stilen auf den Markup-Tags für die Komponentenkonvertierung wie &lt;div data-cq-component=&quot;&amp;ast;&quot;> wird nicht empfohlen.
* Beim Designlayout sollten die Best Practices für das HTML5-Boilerplate befolgt werden. Mehr dazu unter: [https://html5boilerplate.com/](https://html5boilerplate.com/).

## Konfigurieren von OSGi-Modulen {#configuring-osgi-modules}

Die Komponenten, die Eigenschaften verfügbar machen, die über die OSGi-Konsole konfigurierbar sind, lauten wie folgt:

* Design Importer für die Einstiegsseite
* Builder für die Einstiegsseite
* Builder für mobile Einstiegsseiten
* Eintrags-Präprozessor für Einstiegsseite

In der folgenden Tabelle finden Sie eine Kurzbeschreibung der Eigenschaften:

<table>
 <tbody>
  <tr>
   <td><strong>Komponente</strong></td>
   <td><strong>Eigenschaftsname</strong></td>
   <td><strong>Beschreibung der Eigenschaft </strong></td>
  </tr>
  <tr>
   <td>Design Importer für die Einstiegsseite</td>
   <td>Filter extrahieren</td>
   <td>Die Liste der regulären Ausdrücke, die für das Filtern der Dateien beim Extrahieren verwendet werden. <br />Zip-Einträge, die einem der angegebenen Muster entsprechen, werden von der Extraktion ausgeschlossen.</td>
  </tr>
  <tr>
   <td>Builder für die Einstiegsseite</td>
   <td>Dateimuster</td>
   <td>Der Builder für die Einstiegsseite kann so konfiguriert werden, dass er HTML-Dateien verarbeitet, die einem regulären Ausdruck entsprechen, wie vom Dateimuster definiert.</td>
  </tr>
  <tr>
   <td>Builder für mobile Einstiegsseiten</td>
   <td>Dateimuster</td>
   <td>Der Builder für die Einstiegsseite kann so konfiguriert werden, dass er HTML-Dateien verarbeitet, die einem regulären Ausdruck entsprechen, wie vom Dateimuster definiert.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Gerätegruppen</td>
   <td>Die Liste der zu unterstützenden Gerätegruppen.</td>
  </tr>
  <tr>
   <td>Eintrags-Präprozessor für Einstiegsseite</td>
   <td>Suchmuster </td>
   <td>Das Muster, nach dem im Inhalt der Einträge im Archiv gesucht wird. Dieser reguläre Ausdruck wird Zeile für Zeile mit dem Eintragsinhalt abgeglichen. Bei Übereinstimmung wird der übereinstimmende Text durch das angegebene Ersatzmuster ersetzt.<br /> <br /> Beachten Sie den unten stehenden Hinweis bezüglich aktuellen Beschränkungen für den Eintrags-Präprozessor für die Einstiegsseite.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Ersetzungsmuster</td>
   <td>Das Muster, das die gefundenen Übereinstimmungen ersetzt. Sie können Regex-Gruppenverweise wie $1, $2 verwenden. Darüber hinaus unterstützt dieses Muster Suchbegriffe wie {designPath}, die beim Import mit dem tatsächlichen Wert aufgelöst werden.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>**Aktuelle Beschränkungen des Eintrags-Präprozessors für Einstiegsseiten:**
>Wenn Sie Änderungen am Suchmuster vornehmen müssen, müssen Sie beim Öffnen des Felix Property Editor manuell umgekehrte Schrägstriche einfügen, um die regex-Metazeichen auszukommentieren. Wenn Sie nicht manuell umgekehrte Schrägstriche einfügen, wird der regex als ungültig betrachtet und ersetzt nicht die ältere Version.
>
>Beispiel: Wenn die Standardkonfiguration wie folgt ist:
>`/\* *CQ_DESIGN_PATH *\*/ *(['"])`
>
>Und Sie müssen >`CQ_DESIGN_PATH` mit `VIPURL` im Suchmuster verwenden, sollte Ihr Suchmuster wie folgt aussehen:
`/\* *VIPURL *\*/ *(['"])`

## Fehlerbehebung {#troubleshooting}

Beim Import des Designpakets können verschiedene Fehler auftreten, die in diesem Abschnitt beschrieben werden.

### Initialisierung des Sidekicks mit für Einstiegsseiten relevanten Komponenten  {#initialization-of-sidekick-with-landing-page-relevant-components}

Wenn das Designpaket ein parsys-Komponenten-Markup enthält, werden nach dem Import im Sidekick für Einstiegsseiten relevante Komponenten angezeigt. Sie können neue Komponenten per Drag-and-Drop auf die parsys-Komponente in der Einstiegsseite ziehen. Sie können auch den Designmodus aufrufen und dem Sidekick neue Komponenten hinzufügen.

### Während des Imports werden Fehlermeldungen angezeigt {#error-messages-displayed-during-import}

Bei Fehlern (z. B. wenn das importierte Paket keine gültige ZIP-Datei ist) importiert der Design-Import das Paket nicht und zeigt stattdessen oben auf der Seite direkt über dem Drag &amp; Drop-Feld eine Fehlermeldung an. Hier werden Beispiele für Fehlerszenarios aufgeführt. Wenn Sie den Fehler korrigiert haben, können Sie die aktualisierte Zip-Datei erneut in dieselbe leere Einstiegsseite importieren. Unter anderem werden in den folgenden Szenarios Fehler gemeldet:

* Das importierte Designpaket ist kein gültiges Zip-Archiv.
* Das importierte Designpaket enthält auf der obersten Ebene kein index.html.

### Nach dem Import werden Warnmeldungen angezeigt {#warnings-displayed-after-import}

Im Falle von Warnungen (z. B. HTML bezieht sich auf Bilder, die nicht im Paket enthalten sind) importiert der Design Importer die ZIP-Datei, zeigt aber gleichzeitig eine Liste von Problemen/Warnungen im Ergebnisbereich an. Wenn Sie auf den Link Probleme klicken, wird eine Liste mit Warnungen angezeigt, die auf alle Probleme innerhalb des Designpakets hinweisen. Unter anderem werden in folgenden Fällen vom Design Importer Warnmeldungen erzeugt und angezeigt:

* HTML bezieht sich auf Bilder, die nicht im Paket enthalten sind.
* HTML bezieht sich auf Skripte, die im Paket nicht vorhanden sind.
* HTML bezieht sich auf Stile, die nicht im Paket vorhanden sind.

### Wo werden die Dateien aus der Zip-Datei in AEM gespeichert? {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

Nach dem Import der Einstiegsseite werden die Dateien (Bilder, CSS, JS usw.) innerhalb des Designpakets in AEM in folgendem Verzeichnis gespeichert:

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

Angenommen, die Einstiegsseite wird unter der Kampagne We.Retail erstellt und der Name der Einstiegsseite lautet **myBlankLandingPage**. In diesem Fall werden die Zip-Dateien in folgendem Verzeichnis gespeichert:

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### Formatierung bleibt nicht erhalten {#formatting-not-preserved}

Beachten Sie beim Erstellen Ihres CSS die folgenden Beschränkungen:

Bei einem Text und einem (bearbeitbaren) Bild wie nachfolgend gezeigt:

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

wird `box img` im Design Importer verwendet. Die daraus resultierende Einstiegsseite wird ohne Formatierung angezeigt. Um dies zu umgehen, beachten Sie, dass AEM im CSS div-Tags hinzufügt, und schreiben Sie den Code entsprechend um. Andernfalls sind einige CSS-Regeln ungültig.

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
Außerdem sollten Designer beachten, dass nur Code innerhalb des Tags **id=cqcanvas** vom Importer erkannt wird. Andernfalls wird Design nicht beibehalten.
