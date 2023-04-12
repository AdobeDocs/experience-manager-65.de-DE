---
title: Responsives Design für Web-Seiten
seo-title: Responsive design for web pages
description: Responsives Design ermöglicht die effektive Darstellung derselben Seiten auf mehreren Geräten in verschiedenen Ausrichtungen
seo-description: With responsive design, the same pages can be effectively displayed on multiple devices in multiple orientations
uuid: 3d324557-e7ff-4c82-920f-9b5a906925e8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: 532544b0-1932-419a-b6bd-ecf57a926fef
legacypath: /content/docs/en/aem/6-0/develop/mobile/responsive
exl-id: c705710b-a94a-4f4f-affa-ddd4fc6cb0ec
source-git-commit: e05f6cd7cf17f4420176cf76f28cb469bcee4a0a
workflow-type: tm+mt
source-wordcount: '5336'
ht-degree: 43%

---

# Responsives Design für Web-Seiten{#responsive-design-for-web-pages}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten erforderlich ist (z. B. _React_). [Weitere Informationen](/help/sites-developing/spa-overview.md)

>[!NOTE]
>
>Verschiedene Beispiele basieren auf dem Geometrixx-Beispielinhalt, der nicht mehr mit AEM (Adobe Experience Manager) ausgeliefert wird und durch We.Retail ersetzt wurde. Im Dokument [We.Retail-Referenzimplementierung](/help/sites-developing/we-retail.md#we-retail-geometrixx) finden Sie Informationen zum Herunterladen und Installieren von Geometrixx.

Gestalten Sie Ihre Webseiten so, dass sie sich an den Client-Viewport anpassen, in dem sie angezeigt werden. Responsives Design ermöglicht die effektive Darstellung derselben Web-Seiten auf verschiedenen Geräten in beiden Ausrichtungen. Die folgende Abbildung zeigt einige Möglichkeiten, wie eine Seite auf Änderungen der Viewport-Größe reagieren kann:

* Layout: Verwenden Sie einspaltige Layouts für kleinere Viewports und mehrspaltige Layouts für größere Viewports.
* Textgröße: Verwenden Sie in größeren Viewports eine größere Textgröße (falls zutreffend, z. B. Überschriften).
* Inhalt: Nur die wichtigsten Inhalte bei der Anzeige auf kleineren Geräten einschließen.
* Navigation: Gerätespezifische Tools werden für den Zugriff auf andere Seiten bereitgestellt.
* Bilder: Stellen Sie anhand der Fenstergröße dem Client-Darstellungsfeld entsprechende Bilddarstellungen zur Verfügung.

![chlimage_1-4](assets/chlimage_1-4a.png)

Entwickeln Sie Adobe Experience Manager-Anwendungen (AEM), die HTML5-Seiten generieren, die sich an verschiedene Fenstergrößen und Ausrichtungen anpassen. Beispielsweise entsprechen die folgenden Darstellungsfeldbreiten verschiedenen Gerätetypen und -ausrichtungen

* Maximale Breite von 480 Pixel (Telefon, Hochformat)
* Maximale Breite von 767 Pixel (Telefon, Querformat)
* Breite zwischen 768 Pixel und 979 Pixel (Tablet, Hochformat)
* Breite zwischen 980 Pixel und 1199 Pixel (Tablet, Querformat)
* Breite von 1200 Pixel oder höher (Desktop)

Weitere Informationen finden Sie unter den folgenden Themen zur Implementierung von responsivem Design:

* [Medienabfragen](/help/sites-developing/responsive.md#using-media-queries)
* [Fließende Raster](/help/sites-developing/responsive.md#developing-a-fluid-grid)
* [Adaptive Bilder](/help/sites-developing/responsive.md#using-adaptive-images)

Nutzen Sie beim Design den **[!UICONTROL Sidekick]**, um eine Vorschau Ihrer Seiten in verschiedenen Bildschirmgrößen anzuzeigen.

## Vor der Entwicklung {#before-you-develop}

Vor der Entwicklung eines AEM-Programms, das Ihre Web-Seiten unterstützt, müssen Sie einige Design-Entscheidungen treffen. Sie müssen beispielsweise über die folgenden Informationen verfügen:

* Auf welche Geräte der Entwicklungsprozess ausgerichtet ist.
* Die Größe der Zieldarstellungsfelder.
* Die Seiten-Layouts für die berücksichtigten Zieldarstellungsfelder.

### Programmstruktur {#application-structure}

Die typische AEM-Programmstruktur unterstützt alle Implementierungen responsiven Designs:

* Seitenkomponenten befinden sich unter /apps/*application_name*/components
* Vorlagen befinden sich unter /apps/*application_name*/templates
* Designs befinden sich unter /etc/designs

## Verwenden von Medienabfragen {#using-media-queries}

Medienabfragen ermöglichen die selektive Verwendung von CSS-Stilen für das Seiten-Rendering. AEM-Entwicklungs-Tools und -funktionen ermöglichen Ihnen die effektive und effiziente Implementierung von Medienabfragen in Programmen.

Die W3C-Gruppe stellt die [Medienabfragen](https://www.w3.org/TR/mediaqueries-3/)-Empfehlung zur Verfügung, die diese CSS3-Funktion und die Syntax beschreibt.

### Erstellen der CSS-Datei {#creating-the-css-file}

Definieren Sie in Ihrer CSS-Datei Medienabfragen anhand der Eigenschaften der Geräte, die Sie als Ziel auswählen. Die folgende Implementierungsstrategie kann für die Verwaltung der Stile der verschiedenen Medienabfragen verwendet werden:

* Verwenden Sie einen ClientLibraryFolder, um das CSS zu definieren, das beim Rendern der Seite assembliert wird.
* Definieren Sie die Medienabfragen und die zugehörigen Stile in separaten CSS-Dateien. Es ist nützlich, Dateinamen zu verwenden, die die Gerätefunktionen der Medienabfrage darstellen.
* Definieren Sie Stile, die alle Geräte gemeinsam haben, in einer separaten CSS-Datei.
* Ordnen Sie in der Datei css.txt des ClientLibraryFolder die CSS-Listendateien wie in der assemblierten CSS-Datei erforderlich an.

Die `We.Retail` Im Medienbeispiel wird diese Strategie verwendet, um Stile im Site-Design zu definieren. Die von `We.Retail` ist `*/apps/weretail/clientlibs/clientlib-site/less/grid.less`.

In der folgenden Tabelle werden die Dateien im untergeordneten css-Ordner aufgeführt.

<table>
 <tbody>
  <tr>
   <th>Dateiname</th>
   <th>Beschreibung</th>
   <th>Medienabfrage</th>
  </tr>
  <tr>
   <td>style.css</td>
   <td>Allgemeine Stile.</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>bootstrap.css</td>
   <td>Allgemeine Stile, die vom Twitter-Bootstrap definiert werden.</td>
   <td>Nicht zutreffend</td>
  </tr>
  <tr>
   <td>responsive-1200px.css</td>
   <td>Stile für alle Medien, die mindestens 1200 Pixel breit sind.</td>
   <td><p>@media (min-width: 1200px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-980px-1199px.css</td>
   <td>Stile für Medien, die zwischen 980 Pixel und 1199 Pixel breit sind.</td>
   <td><p>@media (min-width: 980px) and (max-width: 1199px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-768px-979px.css</td>
   <td>Stile für Medien, die zwischen 768 Pixel und 979 Pixel breit sind. </td>
   <td><p>@media (min-width: 768px) and (max-width: 979px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-767px-max.css</td>
   <td>Stile für alle Medien, die weniger als 768 Pixel breit sind.</td>
   <td><p>@media (max-width: 767px) {<br /> ...<br /> }</p> </td>
  </tr>
  <tr>
   <td>responsive-480px.css</td>
   <td>Stile für alle Medien, die weniger als 481 Pixel breit sind.</td>
   <td>@media (max-width: 480px) {<br /> ...<br /> }</td>
  </tr>
 </tbody>
</table>

Die Datei „css.txt“ im Ordner `/etc/designs/weretail/clientlibs` führt die CSS-Dateien auf, die der Client-Bibliotheksordner enthält. Die Reihenfolge der Dateien implementiert Stilpriorität. Stile sind spezifischerer, da die Gerätegröße sinkt.

`#base=css`

```
style.css
 bootstrap.css
```

```
responsive-1200px.css
 responsive-980px-1199px.css
 responsive-768px-979px.css
 responsive-767px-max.css
 responsive-480px.css
```

**Tipp**: Anhand aussagekräftiger Namen können Sie die jeweilige Darstellungsfeldgröße leicht identifizieren.

### Verwenden von Medienabfragen mit AEM Seiten {#using-media-queries-with-aem-pages}

Schließen Sie den Client-Bibliotheksordner in das JSP-Skript Ihrer Seitenkomponente ein. Dies hilft bei der Erstellung der CSS-Datei, die die Medienabfragen enthält und auf die Datei verweist.

```xml
<ui:includeClientLib categories="apps.weretail.all"/>
```

>[!NOTE]
>
>Der Client-Bibliotheksordner `apps.weretail.all` bettet die Bibliothek „clientlibs“ ein.

Das JSP-Skript generiert den folgenden HTML-Code, der auf die Stylesheets verweist:

```xml
<link rel="stylesheet" href="/etc/designs/weretail/clientlibs-all.css" type="text/css">
<link href="/etc/designs/weretail.css" rel="stylesheet" type="text/css">
```

## Anzeigen der Vorschau für bestimmte Geräte {#previewing-for-specific-devices}

Zeigen Sie eine Vorschau Ihrer Seiten in unterschiedlichen Darstellungsfeldgrößen an, damit Sie das Verhalten Ihres responsiven Designs testen können. Im **[!UICONTROL Vorschaumodus]** umfasst der **[!UICONTROL Sidekick]** zur Auswahl von Geräten ein Dropdown-Menü **[!UICONTROL Geräte]**. Wenn Sie ein Gerät auswählen, passt sich die Seite der jeweiligen Darstellungsfeldgröße an.

![chlimage_1-5](assets/chlimage_1-5a.png)

Zur Aktivierung der Gerätevorschau im **[!UICONTROL Sidekick]** müssen Sie die Seite und den Service **[!UICONTROL MobileEmulatorProvider]** konfigurieren. Eine andere Seitenkonfiguration kontrolliert die Liste von Geräten, die in der Liste **[!UICONTROL Geräte]** angezeigt wird.

### Hinzufügen der Liste „Geräte“ {#adding-the-devices-list}

Die Liste **[!UICONTROL Geräte]** wird im **[!UICONTROL Sidekick]** angezeigt, wenn Ihre Seite das JSP-Skript enthält, das die Liste **[!UICONTROL Geräte]** rendert. Fügen Sie das Skript `/libs/wcm/mobile/components/simulator/simulator.jsp` dem Abschnitt `head` Ihrer Seite hinzu, um im **[!UICONTROL Sidekick]** die Liste **[!UICONTROL Geräte]** hinzuzufügen.

Fügen Sie folgenden Code in das JSP-Skript ein, das den Abschnitt `head` definiert:

`<cq:include script="/libs/wcm/mobile/components/simulator/simulator.jsp"/>`

Öffnen Sie die Datei `/apps/weretail/components/page/head.jsp` in CRXDE Lite, um ein Beispiel zu sehen.

### Registrieren von Seitenkomponenten für die Simulation {#registering-page-components-for-simulation}

Registrieren Sie Ihre Seitenkomponenten beim Factory-Service „MobileEmulatorProvider“ und definieren Sie die Eigenschaft `mobile.resourceTypes`, um zur Unterstützung Ihrer Seiten den Gerätesimulator zu aktivieren.

Beim Arbeiten mit AEM gibt es mehrere Methoden zum Verwalten der Konfigurationseinstellungen für diese Dienste. see [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) für ausführliche Informationen.

Erstellen Sie beispielsweise einen Knoten ` [sling:OsgiConfig](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository)` in Ihrem Programm:

* Übergeordneter Ordner: `/apps/application_name/config`
* Name: `com.day.cq.wcm.mobile.core.impl.MobileEmulatorProvider-*alias*`

   Das Suffix - `*alias*` ist erforderlich, weil der Service „MobileEmulatorProvider“ ein Factory-Service ist. Verwenden Sie einen beliebigen eindeutigen Alias für diese Factory.

* jcr:primaryType: `sling:OsgiConfig`

Fügen Sie folgende Knoteneigenschaft hinzu:

* Name: `mobile.resourceTypes`
* Typ: `String[]`
* Wert: Die Pfade zu den Seitenkomponenten, die Ihre Web-Seiten rendern. Das Programm „geometrixx-media“ verwendet beispielsweise die folgenden Werte:

   ```
   geometrixx-media/components/page
    geometrixx-unlimited/components/pages/page
    geometrixx-unlimited/components/pages/coverpage
    geometrixx-unlimited/components/pages/issue
   ```

### Angeben der Gerätegruppen {#specifying-the-device-groups}

Zur Angabe der Gerätegruppen, die in der Liste „Geräte“ angezeigt werden, fügen Sie dem Knoten `cq:deviceGroups` der Stammseite Ihrer Website eine Eigenschaft `jcr:content` hinzu. Der Wert der Eigenschaft ist ein Array von Pfaden zu den Gerätegruppenknoten.

Die Gerätegruppenknoten befinden sich im `/etc/mobile/groups` Ordner.

Beispielsweise ist die Stammseite der Geometrixx Media-Website `/content/geometrixx-media`. Der Knoten `/content/geometrixx-media/jcr:content` umfasst die folgende Eigenschaft:

* Name: `cq:deviceGroups`
* Typ: `String[]`
* Wert: `/etc/mobile/groups/responsive`

Verwenden Sie die Tools-Konsole, um [Erstellen und Bearbeiten von Gerätegruppen](/help/sites-developing/groupfilters.md).

>[!NOTE]
>
>Für Gerätegruppen, die Sie für responsives Design verwenden, bearbeiten Sie die Gerätegruppe und wählen Sie auf der Registerkarte Allgemein die Option Emulator deaktivieren aus. Diese Option verhindert, dass das Emulator-Karussell angezeigt wird, was für responsives Design nicht relevant ist.

## Verwenden adaptiver Bilder {#using-adaptive-images}

Sie können Medienabfragen verwenden, um eine Bildressource auszuwählen, die auf der Seite angezeigt werden soll. Jede Ressource, die eine Medienabfrage verwendet, um ihre Verwendung an Bedingungen zu knüpfen, wird jedoch zum Client heruntergeladen. Die Medienabfrage bestimmt lediglich, ob die heruntergeladene Ressource angezeigt wird.

Bei großen Ressourcen wie Bildern ist das Herunterladen aller Ressourcen keine effiziente Nutzung der Datenpipeline des Kunden. Verwenden Sie JavaScript, um die Ressourcenanforderung selektiv herunterzuladen, nachdem die Medienabfragen die Auswahl vorgenommen haben.

Die folgende Strategie lädt eine einzelne Ressource, die mithilfe von Medienabfragen ausgewählt wird:

1. Fügen Sie für jede Version der Ressource ein DIV-Element hinzu. Schließen Sie den URI der Ressource als Wert eines Attributwerts ein. Das Attribut wird vom Browser nicht als Ressource interpretiert.
1. Fügen Sie jedem DIV-Element eine Medienabfrage hinzu, die für die Ressource geeignet ist.
1. Wenn das Dokument geladen oder die Größe des Fensters geändert wird, testet JavaScript-Code die Medienabfrage jedes DIV-Elements.
1. Bestimmen Sie anhand der Ergebnisse der Abfragen, welche Ressource eingeschlossen werden soll.
1. Fügen Sie ein HTML-Element in das DOM ein, das auf die Ressource verweist.

### Medienabfragen mit JavaScript bewerten {#evaluating-media-queries-using-javascript}

Implementierungen der [MediaQueryList-Benutzeroberfläche](https://drafts.csswg.org/cssom-view/#the-mediaquerylist-interface) , die das W3C definiert, ermöglicht es Ihnen, Medienabfragen mithilfe von JavaScript zu evaluieren. Sie können Logik auf die Medienabfrageergebnisse anwenden und Skripte ausführen, die für das aktive Fenster bestimmt sind:

* Browser, die die MediaQueryList-Benutzeroberfläche implementieren, unterstützen die Funktion `window.matchMedia()`. Diese Funktion testet Medienabfragen anhand einer gegebenen Zeichenfolge. Die Funktion gibt ein `MediaQueryList`-Objekt zurück, das Zugriff auf die Abfrageergebnisse bietet.

* Für Browser, die die -Oberfläche nicht implementieren, können Sie eine `matchMedia()` Poly-Füllung, z. B. [matchMedia.js](https://github.com/paulirish/matchMedia.js), eine frei verfügbare JavaScript-Bibliothek.

#### Auswählen von medienspezifischen Ressourcen {#selecting-media-specific-resources}

W3C [Musterelement](https://html.spec.whatwg.org/multipage/embedded-content.html#the-picture-element) verwendet Medienabfragen, um die Quelle zu bestimmen, die für Bildelemente verwendet werden soll. Das Bildelement verwendet Elementattribute, um Medienabfragen Bildpfaden zuzuordnen.

Die kostenlose [picturefill.js-Bibliothek](https://github.com/scottjehl/picturefill) bietet ähnliche Funktionen wie der vorgeschlagene `picture` und verwendet eine ähnliche Strategie. Die Bibliothek „picturefill.js“ ruft `window.matchMedia` auf, um die Medienabfragen zu prüfen, die für einen Satz von `div`-Elementen definiert ist. Alle `div`-Elemente geben auch eine Bildquelle an. Die Quelle wird verwendet, wenn die Medienabfrage des `div`-Elements `true` zurückgibt.

Die Bibliothek `picturefill.js` erfordert HTML-Code, der dem folgenden Beispiel ähnlich ist:

```xml
<div data-picture>
    <div data-src='path to default image'></div>
    <div data-src='path to small image'    data-media="(media query for phone)"></div>
    <div data-src='path to medium image'   data-media="(media query for tablet)"></div>
    <div data-src='path to large image'     data-media="(media query for monitor)"></div>
</div>
```

Wenn die Seite gerendert wird, fügt „picturefull.js“ ein `img`-Element als letztes untergeordnetes Element des Elements `<div data-picture>` ein:

```xml
<div data-picture>
    <div data-src='path to default image'></div>
    <div data-src='path to small image'    data-media="(media query for phone)"></div>
    <div data-src='path to medium image'   data-media="(media query for tablet)"></div>
    <div data-src='path to large image'     data-media="(media query for monitor)"></div>
    <img src="path to medium image">
</div>
```

Auf einer AEM-Seite ist der Wert des Attributs `data-src` der Pfad zu einer Ressource im Repository.

### Implementieren von adaptiven Bildern in AEM {#implementing-adaptive-images-in-aem}

Um adaptive Bilder in Ihre AEM zu implementieren, müssen Sie die erforderlichen JavaScript-Bibliotheken hinzufügen und das erforderliche HTML-Markup in Ihre Seiten einfügen.

**Bibliotheken**

Rufen Sie die folgenden JavaScript-Bibliotheken ab und fügen Sie sie in einen Client-Bibliotheksordner ein:

* [matchMedia.js](https://github.com/paulirish/matchMedia.js) (für Browser, die die MediaQueryList-Benutzeroberfläche nicht implementieren)
* [picturefill.js](https://github.com/scottjehl/picturefill)
* jquery.js (verfügbar über den Client-Bibliotheksordner `/etc/clientlibs/granite/jquery` (Kategorie = jquery)
* [jquery.debouncedresize.js](https://github.com/louisremi/jquery-smartresize) (ein jquery-Ereignis, das auftritt, nachdem die Größe des Fensters verändert wurde)

**Tipp:** Durch [Einbettung](/help/sites-developing/clientlibs.md#embedding-code-from-other-libraries) können Sie automatisch mehrere Client-Bibliotheksordner zusammenfassen.

**HTML**

Erstellen Sie eine Komponente, die die erforderlichen div-Elemente generiert, die der picturefill.js-Code erwartet. Auf einer AEM-Seite ist der Wert des Attributs „data-src“ der Pfad zu einer Ressource im Repository. Beispielsweise kann eine Seitenkomponente die Medienabfragen und die zugeordneten Pfade für Bilddarstellungen in DAM fest programmieren. Alternativ können Sie eine benutzerdefinierte Bildkomponente erstellen, die es Autoren ermöglicht, Bilddarstellungen auszuwählen oder Laufzeit-Render-Optionen anzugeben.

Im folgenden HTML-Beispiel werden zwei DAM-Ausgabeformate desselben Bildes ausgewählt.

```xml
<div data-picture>
    <div data-src='/content/dam/geometrixx-media/articles/meridien.png'></div>
    <div data-src='/content/dam/geometrixx-media/articles/meridien.png/jcr:content/renditions/cq5dam.thumbnail.319.319.png'    data-media="(min-width: 769px)"></div>
    <div data-src='/content/dam/geometrixx-media/articles/meridien.png/jcr:content/renditions/cq5dam.thumbnail.140.100.png'   data-media="(min-width: 481px)"></div>
</div>
```

>[!NOTE]
>
>Die Foundation-Komponente für adaptive Bilder implementiert adaptive Bilder:
>
>* Client-Bibliotheksordner: `/libs/foundation/components/adaptiveimage/clientlibs`
>* Skript, das den HTML-Code generiert: `/libs/foundation/components/adaptiveimage/adaptiveimage.jsp`
>
>Der folgende Abschnitt enthält Details zu dieser Komponente.

### Grundlegendes zum Bild-Rendering in AEM {#understanding-image-rendering-in-aem}

Um das Bild-Rendering anzupassen, sollten Sie die standardmäßige AEM Implementierung des statischen Bild-Renderings kennen. AEM stellt die Bildkomponente und ein Image-Rendering-Servlet bereit, das zusammenarbeitet, um Bilder für Webseiten zu rendern. Die folgenden Ereignissequenzen treten auf, wenn die Bildkomponente im Absatzsystem der Seite enthalten ist:

1. Authoring: Autoren bearbeiten die Bildkomponente, um die Bilddatei anzugeben, die in eine HTML-Seite aufgenommen werden soll. Der Dateipfad wird als Eigenschaftswert des Komponentenknotens Bild gespeichert.
1. Seitenanforderung: Die JSP der Seitenkomponente generiert den HTML-Code. Die JSP der Bildkomponente generiert und fügt der Seite ein img -Element hinzu.
1. Bildanforderung: Der Webbrowser lädt die Seite und fordert das Bild gemäß dem src-Attribut des img-Elements an.
1. Bild-Rendering: Das Image-Rendering-Servlet gibt das Bild an den Webbrowser zurück.

![chlimage_1-6](assets/chlimage_1-6a.png)

Beispielsweise erzeugt das JSP der Bildkomponente das folgende HTML-Element:

`<img title="My Image" alt="My Image" class="cq-dd-image" src="/content/mywebsite/en/_jcr_content/par/image_0.img.jpg/1358372073597.jpg">`

Wenn der Browser die Seite lädt, fordert er das Bild mit dem Wert des src-Attributs als URL an. Sling dekomprimiert die URL:

* Ressource: `/content/mywebsite/en/_jcr_content/par/image_0`
* Dateierweiterung: `.jpg`
* Selektor: `img`
* Suffix: `1358372073597.jpg`

Der Knoten `image_0` hat einen `jcr:resourceType`-Wert von `foundation/components/image`, der einen `sling:resourceSuperType`-Wert von `foundation/components/parbase` hat. Die parbase-Komponente enthält das Skript img.GET.java , das mit dem Selektor und der Dateinamenerweiterung der Anfrage-URL übereinstimmt. CQ verwendet dieses Skript (Servlet) zum Rendern des Bildes.

Öffnen Sie mit CRXDE Lite die Datei `/libs/foundation/components/parbase/img.GET.java`, um den Quell-Code des Skripts zu anzuzeigen.

## Skalieren von Bildern für die aktuelle Darstellungsfeldgröße {#scaling-images-for-the-current-viewport-size}

Skalieren Sie Bilder zur Laufzeit entsprechend den Eigenschaften des Client-Viewports, um Bilder bereitzustellen, die den Prinzipien des responsiven Designs entsprechen. Verwenden Sie dasselbe Designmuster wie das statische Bild-Rendering, indem Sie ein Servlet und eine Authoring-Komponente verwenden.

Die Komponente muss die folgenden Aufgaben ausführen:

* Speichern Sie den Pfad und die gewünschten Dimensionen der Bildressource als Eigenschaftswerte.
* Generieren von `div`-Elementen, die Medienselektoren und Service-Aufrufe für das Rendering des Bildes umfassen

>[!NOTE]
>
>Der Webclient verwendet die JavaScript-Bibliotheken &quot;matchMedia&quot;und &quot;Picturefill&quot;(oder ähnliche Bibliotheken), um die Medienauswahl zu bewerten.

Das Servlet, das die Bildanforderung verarbeitet, muss die folgenden Aufgaben ausführen:

* Rufen Sie den Pfad und die Abmessungen des Bildes aus den Komponenteneigenschaften ab.
* Skalieren Sie das Bild entsprechend den Eigenschaften und geben Sie das Bild zurück.

**Verfügbare Lösungen**

AEM installiert die folgenden Implementierungen, die Sie verwenden oder erweitern können.

* Die Foundation-Komponente für adaptive Bilder, die Medienabfragen generiert, und HTTP-Anforderungen an das Servlet für adaptive Bildkomponenten, das die Bilder skaliert.
* Das Geometrixx Commons-Paket installiert die Beispiel-Servlets für das Image Reference Modification Servlet, die die Bildauflösung ändern.

### Grundlegendes zur Komponente für adaptive Bilder {#understanding-the-adaptive-image-component}

Die Komponente für adaptive Bilder generiert Aufrufe an „Adaptive Image Component Servlet“ zum Rendern eines Bildes, dessen Größe an den Gerätebildschirm angepasst ist. Die Komponente umfasst die folgenden Ressourcen:

* JSP: Fügt div -Elemente hinzu, die Medienabfragen mit -Aufrufen verknüpfen, um das Servlet der adaptiven Bildkomponente zu erhalten.
* Client-Bibliotheken: Der Ordner clientlibs ist ein `cq:ClientLibraryFolder` , das die JavaScript-Bibliothek matchMedia-Polyfill und eine modifizierte JavaScript-Bibliothek &quot;Picturefill&quot;zusammenstellt.
* Dialogfeld bearbeiten: Der Knoten `cq:editConfig` überschreibt die CQ-Foundation-Bildkomponente, damit das Drop-Ziel anstelle einer Foundation-Bildkomponente eine Komponente für adaptive Bilder erstellt.

#### Hinzufügen der DIV-Elemente {#adding-the-div-elements}

Das Skript „adaptive-image.jsp“ enthält den folgenden Code, der div-Elemente und Medienabfragen generiert:

```
<div data-picture data-alt='<%= alt %>'>
    <div data-src='<%= path + ".img.320.low." + extension + suffix %>'       data-media="(min-width: 1px)"></div>                                        <%-- Small mobile --%>
    <div data-src='<%= path + ".img.320.medium." + extension + suffix %>'    data-media="(min-width: 320px)"></div>  <%-- Portrait mobile --%>
    <div data-src='<%= path + ".img.480.medium." + extension + suffix %>'    data-media="(min-width: 321px)"></div>  <%-- Landscape mobile --%>
    <div data-src='<%= path + ".img.476.high." + extension + suffix %>'      data-media="(min-width: 481px)"></div>   <%-- Portrait iPad --%>
    <div data-src='<%= path + ".img.620.high." + extension + suffix %>'      data-media="(min-width: 769px)"></div>  <%-- Landscape iPad --%>
    <div data-src='<%= path + ".img.full.high." + extension + suffix %>'     data-media="(min-width: 1025px)"></div> <%-- Desktop --%>

    <%-- Fallback content for non-JS browsers. Same img src as the initial, unqualified source element. --%>
    <noscript>
        <img src='<%= path + ".img.320.low." + extension + suffix %>' alt='<%= alt %>'>
    </noscript>
</div>
```

Die Variable `path` enthält den Pfad der aktuellen Ressource (der Komponentenknoten für adaptive Bilder). Der Code generiert eine Reihe von `div`-Elementen mit der folgenden Struktur:

`<div data-scr = "*path-to-parent-node*.adaptive-image.adapt.*width*.*quality*.jpg" data-media="*media query*"></div>`

Der Wert des Attributs `data-scr` ist eine URL, die Sling auflöst, um „Adaptive Image Component Servlet“ zu erhalten, das das Bild rendert. Das Datenmedienattribut umfasst die Medienabfrage, die anhand der Client-Eigenschaften geprüft wird.

Der folgende HTML-Code ist ein Beispiel für die `div`-Elemente, die das JSP generiert:

```xml
<div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.320.low.jpg'></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.320.medium.jpg'    data-media="(min-width: 320px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.480.medium.jpg'    data-media="(min-width: 321px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.476.high.jpg'     data-media="(min-width: 481px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.620.high.jpg'     data-media="(min-width: 769px)"></div>
    <div data-src='/content/geometrixx-media/en/events/the-lineup-you-ve-been-waiting-for/jcr:content/article-content-par/adaptive_image.adapt.full.high.jpg'     data-media="(min-width: 1025px)"></div>
```

#### Ändern der Bildgrößenselektoren {#changing-the-image-size-selectors}

Wenn Sie die Adaptive Image-Komponente anpassen und die Breitenselektoren ändern, müssen Sie auch das Adaptive Image Component Servlet konfigurieren, um die Breiten zu unterstützen.

### Das Servlet der Adaptive Image Component {#understanding-the-adaptive-image-component-servlet}

„Adaptive Component Servlet“ ändert die Größe eines JPEG-Bilds in eine gegebene Breite und legt die JPEG-Qualität fest.

#### Die Benutzeroberfläche von „Adaptive Image Component Servlet“ {#the-interface-of-the-adaptive-image-component-servlet}

Das Servlet für die Adaptive Bildkomponente ist an das standardmäßige Sling-Servlet gebunden und unterstützt die Dateierweiterungen .jpg, .jpeg, .gif und .png . Der Servlet-Selektor ist img.

>[!CAUTION]
>
>Animierte GIF-Dateien werden in AEM für adaptive Ausgabedarstellungen nicht unterstützt.

Deshalb löst Sling HTTP-Anforderungs-URLs im folgenden Format in dieses Servlet auf:

`*path-to-node*.img.*extension*`

Beispielsweise leitet Sling HTTP-Anfragen mit der URL `http://localhost:4502/content/geometrixx/adaptiveImage.img.jpg` an „Adaptive Image Component Servlet“ weiter.

Zwei zusätzliche Selektoren geben die gewünschte Bildbreite und JPEG-Qualität an. Im folgenden Beispiel wird ein Bild mit einer Breite von 480 Pixel und mittlerer Qualität angefordert:

`http://localhost:4502/content/geometrixx/adaptiveImage.adapt.480.MEDIUM.jpg`

**Unterstützte Bildeigenschaften**

Das Servlet akzeptiert eine begrenzte Anzahl von Bildbreiten und -qualitäten. Die folgenden Breiten werden standardmäßig unterstützt (in Pixel):

* vollständig
* 320
* 480
* 476
* 620

Der vollständige Wert zeigt keine Skalierung an.

Die folgenden Werte für die JPEG-Qualität werden unterstützt:

* LOW
* MEDIUM
* HOCH

Die numerischen Werte sind 0,4, 0,82 bzw. 1,0.

**Ändern der standardmäßig unterstützten Breiten**

Verwenden Sie die Web-Konsole ([http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)) oder einen sling:OsgiConfig -Knoten verwenden, um die unterstützten Breiten des Adobe CQ Adaptive Image Component Servlet zu konfigurieren.

Informationen zum Konfigurieren AEM Services finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

<table>
 <tbody>
  <tr>
   <th> </th>
   <th>Web-Konsole</th>
   <th>sling:OsgiConfig</th>
  </tr>
  <tr>
   <th>Name des Service oder Knotens</th>
   <td>Der Service-Name auf der Registerkarte „Konfiguration“ lautet „Adobe CQ Adaptive Image Component Servlet“.</td>
   <td>com.day.cq.wcm.foundation.impl. AdaptiveImageComponentServlet</td>
  </tr>
  <tr>
   <th>Eigenschaft</th>
   <td><p>Unterstützte Breiten</p>
    <ul>
     <li>Um eine unterstützte Breite hinzuzufügen, klicken Sie auf die Schaltfläche „+“ und geben Sie eine positive ganze Zahl ein.</li>
     <li>Um eine unterstützte Breite zu entfernen, klicken Sie auf die zugehörige Schaltfläche „-“.</li>
     <li>Um eine unterstützte Breite zu ändern, bearbeiten Sie den Feldwert.</li>
    </ul> </td>
   <td><p>adapt.supported.widths</p>
    <ul>
     <li>Die Eigenschaft ist ein Zeichenfolgenwert mit mehreren Werten.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

#### Implementierungsdetails {#implementation-details}

Die Klasse `com.day.cq.wcm.foundation.impl.AdaptiveImageComponentServlet` erweitert die Klasse [AbstractImageServlet](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html). Der Quellcode des AdaptiveImageComponentServlet befindet sich im `/libs/foundation/src/impl/src/com/day/cq/wcm/foundation/impl` Ordner.

Die Klasse verwendet Felix SCR-Anmerkungen, um den Ressourcentyp und die Dateierweiterung zu konfigurieren, mit der das Servlet verknüpft ist, sowie den Namen des ersten Selektors.

```java
@Component(metatype = true, label = "Adobe CQ Adaptive Image Component Servlet",
        description = "Render adaptive images in a variety of qualities")
@Service
@Properties(value = {
    @Property(name = "sling.servlet.resourceTypes", value = "foundation/components/adaptiveimage", propertyPrivate = true),
    @Property(name = "sling.servlet.selectors", value = "img", propertyPrivate = true),
    @Property(name = "sling.servlet.extensions", value ={
            "jpg",
            "jpeg",
            "png",
            "gif"
    }, propertyPrivate = true)
})
```

Das Servlet verwendet die SCR-Anmerkung Eigenschaft , um die standardmäßige unterstützte Bildqualität und -dimensionen festzulegen.

```java
@Property(value = {
            "320", // iPhone portrait
            "480", // iPhone landscape
            "476", // iPad portrait
            "620" // iPad landscape
    },
            label = "Supported Widths",
            description = "List of widths this component is permitted to generate.")
```

Die Klasse `AbstractImageServlet` stellt die Methode `doGet` zur Verfügung, die die HTTP-Anfrage verarbeitet. Diese Methode bestimmt die Ressource, die der Anfrage zugeordnet ist, ruft Ressourceneigenschaften aus dem Repository ab und gibt sie in einem [ImageContext](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.ImageContext.html)-Objekt zurück.

>[!NOTE]
>
>Die Klasse [com.day.cq.commons.DownloadResource](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/DownloadResource.html) stellt die `getFileReference method` zur Verfügung, die den Wert der Eigenschaft `fileReference` der Ressource abruft.

Die Klasse `AdaptiveImageComponentServlet` überschreibt die Methode `createLayer`. Die Methode ruft den Pfad der Bildressource und die angeforderte Bildbreite vom `ImageContext`-Objekt ab. Dann ruft sie die Methoden der Klasse `info.geometrixx.commons.impl.AdaptiveImageHelper` auf, die die tatsächliche Bildskalierung durchführen.

Die Klasse „AdaptiveImageComponentServlet“ überschreibt auch die Methode „writeLayer“. Diese Methode wendet die JPEG-Qualität auf das Bild an.

### Image Reference Modification Servlet (Geometrixx Common) {#image-reference-modification-servlet-geometrixx-common}

Das Beispiel-Image Reference Modification Servlet generiert Größenattribute für das img-Element, um ein Bild auf der Web-Seite zu skalieren.

#### Servlet aufrufen {#calling-the-servlet}

Das Servlet ist an `cq:page`-Ressourcen gebunden und unterstützt das Dateiformat JPG. Der Servlet-Selektor ist `image`. Deshalb löst Sling HTTP-Anforderungs-URLs im folgenden Format in dieses Servlet auf:

`path-to-page-node.image.jpg`

Beispielsweise leitet Sling HTTP-Anfragen mit der URL `http://localhost:4502/content/geometrixx/en.image.jpg` an „Image Reference Modification Servlet“ weiter.

Drei zusätzliche Selektoren geben die angeforderte Bildbreite, -höhe und (optional) -Qualität an. Im folgenden Beispiel wird ein Bild mit einer Breite von 770 Pixel, einer Höhe von 360 Pixel und mittlerer Qualität angefordert.

`http://localhost:4502/content/geometrixx/en.image.770.360.MEDIUM.jpg`

**Unterstützte Bildeigenschaften**

Das Servlet akzeptiert eine begrenzte Anzahl von Bilddimensionen und Qualitätswerten.

Die folgenden Werte werden standardmäßig unterstützt (widthxheight):

* 256x192
* 370x150
* 480 x 200
* 127x127
* 770 x 360
* 620x290
* 480 x 225
* 320x150
* 375x175
* 303x142
* 1170x400
* 940x340
* 770x300
* 480 x 190

Die folgenden Werte für die Bildqualität werden unterstützt:

* niedrig
* mittel
* hoch

Beim Arbeiten mit AEM gibt es mehrere Methoden zum Verwalten der Konfigurationseinstellungen für diese Dienste. see [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) für ausführliche Informationen.

#### Bildressource festlegen {#specifying-the-image-resource}

Der Bildpfad, die Abmessungen und die Qualitätswerte müssen als Eigenschaften eines Knotens im Repository gespeichert werden:

* Der Knotenname ist `image`.
* Der übergeordnete Knoten ist der Knoten `jcr:content` einer Ressource `cq:page`.

* Der Bildpfad wird als Wert einer Eigenschaft mit der Bezeichnung `fileReference` gespeichert.

Verwenden Sie beim Bearbeiten einer Seite den **Sidekick** zum Angeben von Bildern und zum Hinzufügen des Knotens `image` zu den Seiteneigenschaften:

1. Klicken Sie im **Sidekick** auf die Registerkarte **Seite** und klicken Sie dann auf **Seiteneigenschaften**.
1. Klicken Sie auf die Registerkarte **Bild** und geben Sie das Bild an.
1. Klicken Sie auf **OK**.

#### Implementierungsdetails {#implementation-details-1}

Die Klasse „info.geometrixx.commons.impl.servlets.ImageReferenceModificationServlet“ erweitert die Klasse [AbstractImageServlet](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html). Wenn Sie das Paket cq-geometrixx-commons-pkg installiert haben, befindet sich der Quellcode von ImageReferenceModificationServlet im Ordner `/apps/geometrixx-commons/src/core/src/main/java/info/geometrixx/commons/impl/servlets` Ordner.

Die Klasse verwendet Felix SCR-Anmerkungen, um den Ressourcentyp und die Dateierweiterung zu konfigurieren, mit der das Servlet verknüpft ist, sowie den Namen des ersten Selektors.

```java
@Component(metatype = true, label = "Adobe CQ Image Reference Modification Servlet",
        description = "Render the image associated with a page in a variety of dimensions and qualities")
@Service
@Properties(value = {
    @Property(name = "sling.servlet.resourceTypes", value = NameConstants.NT_PAGE, propertyPrivate = true),
    @Property(name = "sling.servlet.selectors", value = "image", propertyPrivate = true),
    @Property(name = "sling.servlet.extensions", value = "jpg", propertyPrivate = true)
})
```

Das Servlet verwendet die SCR-Anmerkung Eigenschaft , um die standardmäßige unterstützte Bildqualität und -dimensionen festzulegen.

```java
@Property(label = "Image Quality",
            description = "Quality must be a double between 0.0 and 1.0", value = "0.82")
@Property(value = {
                "256x192", // Category page article list images
                "370x150", // "Most popular" desktop & iPad & carousel min-width: 1px
                "480x200", // "Most popular" phone
                "127x127", // article summary phone square images
                "770x360", // article summary, desktop
                "620x290", // article summary, tablet
                "480x225", // article summary, phone (landscape)
                "320x150", // article summary, phone (portrait) and fallback
                "375x175", // 2-column article summary, desktop
                "303x142", // 2-column article summary, tablet
                "1170x400", // carousel, full
                "940x340",  // carousel min-width: 980px
                "770x300",  // carousel min-width: 768px
                "480x190"   // carousel min-width: 480px
            },
            label = "Supported Resolutions",
            description = "List of resolutions this component is permitted to generate.")
```

Die Klasse `AbstractImageServlet` stellt die Methode `doGet` zur Verfügung, die die HTTP-Anfrage verarbeitet. Diese Methode bestimmt die Ressource, die dem Aufruf zugeordnet ist, ruft Ressourceneigenschaften aus dem Repository ab und speichert sie in einem [ImageContext](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.ImageContext.html)-Objekt.

Die Klasse `ImageReferenceModificationServlet` überschreibt die Methode `createLayer` und implementiert die Logik, die die zu rendernde Bildressource festlegt. Die Methode ruft einen untergeordneten Knoten des Knotens `jcr:content` der Seite mit der Bezeichnung `image` ab. Aus diesem `image`-Knoten wird ein [Bildobjekt](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/foundation/Image.html) erstellt und die Methode `getFileReference` gibt den Pfad zur Bilddatei aus der Eigenschaft `fileReference` des Bildknotens zurück.

>[!NOTE]
>Die Klasse [com.day.cq.commons.DownloadResource](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/DownloadResource.html) stellt die Methode „getFileReference“ zur Verfügung.

## Entwickeln eines fließenden Rasters {#developing-a-fluid-grid}

AEM ermöglicht Ihnen die effiziente und effektive Implementierung fließender Raster. Auf dieser Seite wird beschrieben, wie Sie fließende Raster oder eine vorhandene Rasterimplementierung (z. B. [Bootstrap](https://github.com/topics/twitter-bootstrap?l=css)) in Ihr AEM-Programm integrieren.

Wenn Sie nicht mit fließenden Rastern vertraut sind, lesen Sie den Abschnitt [Einführung in fließende Raster](/help/sites-developing/responsive.md#developing-a-fluid-grid) unten auf dieser Seite. Diese Einführung bietet einen Überblick über fließende Raster und Anleitungen zu ihrer Konzeption.

### Definieren des Rasters mithilfe einer Seitenkomponente {#defining-the-grid-using-a-page-component}

Verwenden Sie Seitenkomponenten, um die HTML-Elemente zu generieren, die die Inhaltsbausteine der Seite definieren. Der ClientLibraryFolder, auf den die Seite verweist, stellt das CSS bereit, das das Layout der Inhaltsbausteine steuert:

* Seitenkomponente: Fügt div -Elemente hinzu, die Zeilen von Inhaltsbausteinen darstellen. Die div -Elemente, die Inhaltsbausteine darstellen, enthalten eine parsys-Komponente, in der Autoren Inhalte hinzufügen.
* Client-Bibliotheksordner: Stellt die CSS-Datei zur Verfügung, die die Medienabfragen und Stile für die div-Elemente enthält.

Beispielsweise enthält die Beispielanwendung „geometrixx-media“ die Komponente „media-home“. Diese Seitenkomponente fügt zwei Skripte hinzu, die zwei `div`-Elemente der Klasse `row-fluid` generieren:

* Die erste Zeile enthält ein `div`-Element der Klasse `span12` (der Inhalt umfasst 12 Spalten). Das `div`-Element enthält die parsys-Komponente.

* Die zweite Zeile enthält zwei `div`-Elemente, eines der Klasse `span8` und eines der Klasse `span4`. Jedes `div`-Element enthält die parsys-Komponente.

```xml
<div class="page-content">
    <div class="row-fluid">
        <div class="span12">
            <cq:include path="grid-12-par" resourceType="foundation/components/parsys" />
        </div>
    </div>
    <div class="row-fluid">
        <div class="span8">
            <cq:include path="grid-8-par" resourceType="foundation/components/parsys" />
        </div>
        <div class="span4">
            <cq:include path="grid-4-par" resourceType="foundation/components/parsys" />
        </div>
    </div>
</div>
```

>[!NOTE]
>
>Wenn eine Komponente verschiedene `cq:include`-Elemente umfasst, die auf die Parsys-Komponente verweisen, müssen alle `path`-Attribute unterschiedliche Werte aufweisen.

#### Skalieren des Seitenkomponentenrasters {#scaling-the-page-component-grid}

Das Design, das der Seitenkomponente „geometrixx-media“ (`/etc/designs/geometrixx-media`) zugeordnet ist, umfasst den ClientLibraryFolder `clientlibs`. Dieser ClientLibraryFolder definiert CSS-Stile für `row-fluid`-Klassen, `span*`-Klassen und `span*`-Klassen, die untergeordnete Elemente von `row-fluid`-Klassen sind. Medienabfragen ermöglichen die Neudefinition von Stilen für verschiedene Darstellungsfeldgrößen.

Das folgende Beispiel-CSS ist eine Teilmenge dieser Stile. Diese Untergruppe konzentriert sich auf die Klassen `span12`, `span8` und `span4` sowie Medienabfragen für zwei Darstellungsfeldgrößen. Beachten Sie die folgenden Eigenschaften des CSS:

* Die `.span`-Stile definieren Elementbreiten anhand absoluter Zahlenwerte.
* Die `.row-fluid .span*` Stile definieren Elementbreiten als Prozentsatz des übergeordneten Elements. Prozentsätze werden aus den absoluten Breiten berechnet.
* Medienabfragen für größere Viewports weisen größere absolute Breiten zu.

>[!NOTE]
>
>Das Geometrixx Media-Beispiel integriert die [Bootstrap](https://getbootstrap.com/2.0.2/) JavaScript-Framework in die fließende Rasterimplementierung. Das Bootstrap-Framework stellt die Datei „bootstrap.css“ zur Verfügung.

```xml
/* default styles (no media queries) */
 .span12 { width: 940px }
 .span8 { width: 620px }
 .span4 { width: 300px }
 .row-fluid .span12 { width: 100% }
 .row-fluid .span8 { width: 65.95744680851064% }
 .row-fluid .span4 { width: 31.914893617021278% }

@media (min-width: 768px) and (max-width: 979px) {
 .span12 { width: 724px; }
 .span8 {     width: 476px; }
 .span4 {     width: 228px; }
 .row-fluid .span12 {     width: 100%;}
 .row-fluid .span8 {     width: 65.74585635359117%; }
 .row-fluid .span4 {     width: 31.491712707182323%; }
}

@media (min-width: 1200px) {
 .span12 { width: 1170px }
 .span8 { width: 770px }
 .span4 { width: 370px }
 .row-fluid .span12 { width: 100% }
 .row-fluid .span8 { width: 65.81196581196582% }
 .row-fluid .span4 { width: 31.623931623931625% }
}
```

#### Neupositionieren von Inhalten im Seitenkomponentenraster {#repositioning-content-in-the-page-component-grid}

Die Seiten der Beispielanwendung &quot;Geometrixx Media&quot;verteilen Zeilen von Inhaltsbausteinen horizontal in einem breiten Viewport. In kleineren Viewports werden dieselben Blöcke vertikal verteilt. Das folgende Beispiel-CSS zeigt die Stile, die dieses Verhalten für den HTML-Code implementieren, den die Medien-Homepage-Komponente generiert:

* Das standardmäßige CSS für die Seite „media-welcome“ weist den `float:left`-Stil `span*`-Klassen zu, die in `row-fluid`-Klassen enthalten sind.

* Medienabfragen für kleinere Darstellungsfelder weisen denselben Klassen den `float:none`-Stil zu.

```xml
/* default styles (no media queries) */
    .row-fluid [class*="span"] {
        width: 100%;
        float: left;
}

@media (max-width: 767px) {
    [class*="span"], .row-fluid [class*="span"] {
        float: none;
        width: 100%;
    }
}
```

#### Modularisieren der Seitenkomponenten {#tip-modularize-your-page-components}

Modularisieren Sie Ihre Komponenten, damit Sie den Code effizient nutzen können. Ihre Site verwendet wahrscheinlich mehrere verschiedene Seitentypen, z. B. eine Begrüßungsseite, eine Artikelseite oder eine Produktseite. Jeder Seitentyp enthält verschiedene Inhaltstypen und verwendet wahrscheinlich unterschiedliche Layouts. Wenn jedoch bestimmte Elemente eines Layouts auf mehreren Seiten verwendet werden, können Sie den Code wiederverwenden, der diesen Teil des Layouts implementiert.

**Seitenkomponentenüberlagerungen verwenden**

Erstellen Sie eine Hauptseitenkomponente, die Skripte für die Generierung der einzelnen Bestandteile einer Seite bietet (z. B. die Abschnitte `head` und `body` sowie die Abschnitte `header`, `content` und `footer` im Hauptteil).

Erstellen Sie andere Seitenkomponenten, die die Hauptseitenkomponente als `cq:resourceSuperType` verwenden. Diese Komponenten umfassen Skripte, die die Skripte der Hauptseite je nach Bedarf überschreiben.

Beispielsweise umfasst das Programm „geometrixx-media“ die Seitenkomponente (`sling:resourceSuperType` ist die Foundation-Seitenkomponente). Einige untergeordnete Komponenten (z. B. „article“, „category“ und „media-home“) verwenden diese Seitenkomponente als `sling:resourceSuperType`. Jede untergeordnete Komponente enthält eine Datei content.jsp , die die Datei content.jsp der Seitenkomponente überschreibt.

**Skripte wiederverwenden**

Erstellen Sie mehrere JSP-Skripte, die Zeilen- und Spaltenkombinationen generieren, die für mehrere Seitenkomponenten gleich sind. Beispielsweise verweisen sowohl das Skript `content.jsp` des Artikels als auch die media-home-Komponenten auf das Skript `8x4col.jsp`.

**Organisieren von CSS-Stilen nach der Zieldarstellungsfeldgröße**

Schließen Sie CSS-Stile und Medienabfragen für verschiedene Darstellungsfeldgrößen in separate Dateien ein. Verwenden Sie Client-Bibliotheksordner, um sie zu verketten.

### Einfügen von Komponenten in das Seitenraster {#inserting-components-into-the-page-grid}

Wenn Komponenten einen einzelnen Inhaltsblock generieren, steuert normalerweise das von der Seitenkomponente erstellte Raster die Platzierung des Inhalts.

Als Autor kann der Inhaltsbaustein in verschiedenen Größen und relativen Positionen dargestellt werden. Der Inhaltstext sollte keine relativen Anweisungen verwenden, um auf andere Inhaltsbausteine zu verweisen.

Bei Bedarf sollte die Komponente alle CSS- oder JavaScript-Bibliotheken bereitstellen, die für den von ihr generierten HTML-Code erforderlich sind. Verwenden Sie einen Client-Bibliotheksordner innerhalb der Komponente, damit die CSS- und JS-Dateien generiert werden. Um die Dateien verfügbar zu machen, [Erstellen einer Abhängigkeit oder Einbetten der Bibliothek](/help/sites-developing/clientlibs.md#creating-client-library-folders) in einem anderen Client-Bibliotheksordner unterhalb des Ordners /etc gespeichert.

**Unterraster**

Wenn die Komponente mehrere Inhaltsblöcke enthält, fügen Sie die Inhaltsbausteine innerhalb einer Zeile hinzu, um ein Unterraster auf der Seite zu erstellen:

* Verwenden Sie dieselben Klassennamen wie die übergeordnete Seitenkomponente, damit Sie div-Elemente als Zeilen und Inhaltsbausteine ausdrücken können.
* Um das vom CSS des Seitenentwurfs implementierte Verhalten zu überschreiben, verwenden Sie einen zweiten Klassennamen für das div-Element der Zeile und geben Sie die zugehörige CSS in einem Client-Bibliotheksordner an.

Beispielsweise generiert die Komponente `/apps/geometrixx-media/components/2-col-article-summary` zwei Inhaltsspalten. Der HTML-Code, den sie generiert, weist die folgende Struktur auf:

```xml
<div class="row-fluid mutli-col-article-summary">
    <div class="span6">
        <article>
            <div class="article-summary-image">...</div>
            <div class="social-header">...</div>
            <div class="article-summary-description">...</div>
            <div class="social">...</div>
        </article>
    </div>
</div>
```

Die `.row-fluid .span6`-Selektoren des CSS der Seite gelten für die `div`-Elemente derselben Klasse und Struktur in diesem HTML-Code. Allerdings umfasst die Komponente auch den Client-Bibliotheksordner /apps/geometrixx-media/components/2-col-article-summary/clientlibs:

* Das CSS verwendet dieselben Medienabfragen wie die Seitenkomponente, um die Änderungen im Layout an denselben jeweiligen Seitenbreiten umzusetzen.
* Selektoren nutzen die Klasse `multi-col-article-summary` des `div`-Elements der Zeile, um das Verhalten der Klasse `row-fluid` der Seite zu überschreiben.

Beispielsweise sind in der Datei `/apps/geometrixx-media/components/2-col-article-summary/clientlibs/css/responsive-480px.css` die folgenden Stile enthalten:

```xml
@media (max-width: 480px) {
    .mutli-col-article-summary .article-summary-image {
        float: left;
        width: 127px;
    }
    .mutli-col-article-summary .article-summary-description {
        width: auto;
        margin-left: 127px;
    }
    .mutli-col-article-summary .article-summary-description h4 {
        padding-left: 10px;
    }
    .mutli-col-article-summary .article-summary-text {
        margin-left: 127px;
        min-height: 122px;
        top: 0;
    }
}
```

## Einführung zu fließenden Rastern {#introduction-to-fluid-grids}

Fließende Raster ermöglichen die Anpassung von Seitenlayouts an die Dimensionen des Client-Viewports. Raster bestehen aus logischen Spalten und Zeilen, die die Inhaltsblöcke auf der Seite positionieren.

* Spalten bestimmen die horizontalen Positionen und Breiten von Inhaltsbausteinen.
* Zeilen bestimmen die relative vertikale Position von Inhaltsbausteinen.

Mithilfe der HTML5-Technologie können Sie das Raster implementieren und bearbeiten, um Seitenlayouts an verschiedene Darstellungsfeldgrößen anzupassen:

* HTML `div` -Elemente enthalten Inhaltsblöcke, die sich über einige Spalten erstrecken.
* Eines oder mehrere dieser div -Elemente enthalten eine Zeile, wenn sie ein gemeinsames übergeordnetes div -Element teilen.

### Verwenden separater Breiten {#using-discrete-widths}

Verwenden Sie für jeden Bereich der Viewport-Breiten, die Sie als Ziel auswählen, eine statische Seitenbreite und Inhaltsblöcke mit konstanter Breite. Bei der manuellen Größenanpassung eines Browser-Fensters treten Änderungen an der Inhaltsgröße bei separaten Fensterbreiten (auch als Haltepunkte bezeichnet) auf. Daher werden Seitenentwürfe genauer eingehalten, wodurch das Benutzererlebnis maximiert wird.

#### Skalieren des Rasters {#scaling-the-grid}

Verwenden Sie Raster zum Skalieren von Inhaltsbausteinen, um sie an verschiedene Darstellungsfeldgrößen anzupassen. Inhaltsbausteine erstrecken sich über eine bestimmte Anzahl von Spalten. Wenn sich die Spaltenbreiten erhöhen oder verringern, um an verschiedene Darstellungsfeldgrößen anzupassen, werden die Inhaltsblöcke entsprechend vergrößert oder verkleinert. Die Skalierung kann sowohl große als auch mittlere Viewports unterstützen, die groß genug sind, um die nebeneinander platzierte Platzierung von Inhaltsbausteinen zu ermöglichen.

![](do-not-localize/chlimage_1-1a.png)

#### Neupositionieren von Inhalten im Raster {#repositioning-content-in-the-grid}

Die Größe von Inhaltsbausteinen kann durch eine minimale Breite beschränkt werden, über die die Skalierung nicht mehr effektiv ist. Bei kleineren Viewports kann das Raster verwendet werden, um Inhaltsblöcke vertikal und nicht horizontal zu verteilen.

![](do-not-localize/chlimage_1-2a.png)

### Entwerfen des Rasters {#designing-the-grid}

Legen Sie die Spalten und Zeilen fest, in denen die Inhaltsblöcke auf Ihren Seiten positioniert werden sollen. Ihre Seiten-Layouts bestimmen die Anzahl der Spalten und Zeilen, die sich über Ihr Raster erstrecken.

**Spaltenanzahl**

Fügen Sie genügend Spalten hinzu, um die Inhaltsbausteine für alle Darstellungsfeldgrößen in allen Layouts horizontal zu positionieren. Verwenden Sie mehr Spalten als derzeit erforderlich, damit Sie künftige Seitenentwürfe aufnehmen können.

**Zeileninhalt**

Verwenden Sie Zeilen, um die vertikale Positionierung von Inhaltsbausteinen zu steuern. Legen Sie die Inhaltsbausteine fest, die dieselbe Zeile aufweisen:

* Inhaltsbausteine, die sich in einem der Layouts horizontal nebeneinander befinden, befinden sich in derselben Zeile.
* Inhaltsbausteine, die sich horizontal (breitere Darstellungsfelder) und vertikal (kleinere Darstellungsfelder) nebeneinander befinden, befinden sich in derselben Zeile.

### Rasterimplementierungen {#grid-implementations}

Erstellen Sie CSS-Klassen und -Stile, damit Sie das Layout der Inhaltsbausteine auf einer Seite steuern können. Seitenentwürfe basieren häufig auf der relativen Größe und Position von Inhaltsbausteinen im Viewport. Der Viewport bestimmt die tatsächliche Größe der Inhaltsbausteine. Ihr CSS muss die relativen und absoluten Größen berücksichtigen. Sie können ein fließendes Raster mit drei CSS-Typen implementieren:

* Eine Klasse für ein `div`-Element, das ein Container für alle Zeilen ist. Diese Klasse legt die absolute Breite des Rasters fest.
* Eine Klasse für `div`-Elemente, die eine Zeile darstellen. Diese Klasse steuert die horizontale bzw. vertikale Positionierung der Inhaltsblöcke, die sie umfasst.
* Klassen für `div`-Elemente, die Inhaltsblöcke mit verschiedenen Breiten darstellen. Breiten werden als Prozentsatz des übergeordneten Elements (der Zeile) ausgedrückt.

Zielgerichtete Darstellungsfeldbreiten (und die zugehörigen Medienabfragen) markieren diskrete Breiten, die für ein Seitenlayout verwendet werden.

#### Breiten von Inhaltsblöcken {#widths-of-content-blocks}

Im Allgemeinen wird die `width` Die Stile von Inhaltsblockklassen basieren auf den folgenden Eigenschaften Ihrer Seite und Ihres Rasters:

* Die absolute Seitenbreite, die Sie für jede Targeting-Darstellungsfeldgröße verwenden. Bekannte Werte.
* Die absolute Breite der Rasterspalten für jede Seitenbreite. Sie bestimmen diese Werte.
* Die relative Breite jeder Spalte als Prozentsatz der gesamten Seitenbreite. Sie berechnen diese Werte.

Das CSS umfasst eine Reihe von Medienabfragen, die die folgende Struktur verwenden:

```xml
@media(query_for_targeted_viewport){

  .class_for_container{ width:absolute_page_width }
  .class_for_row { width:100%}

  /* several selectors for content blocks   */
  .class_for_content_block1 { width:absolute_block_width1 }
  .class_for_content_block2 { width:absolute_block_width2 }
  ...

  /* several selectors for content blocks inside rows */
  .class_for_row .class_for_content_block1 { width:relative_block_width1 }
  .class_for_row .class_for_content_block2 { width:relative_block_width2 }
  ...
}
```

Verwenden Sie den folgenden Algorithmus als Ausgangspunkt für die Entwicklung der Elementklassen und CSS-Stile für Ihre Seiten.

1. Definieren Sie einen Klassennamen für das div-Element, das alle Zeilen enthält, z. B. `content.`.
1. Definieren Sie eine CSS-Klasse für div-Elemente, die Zeilen darstellen, z. B. `row-fluid`.
1. Definieren Sie Klassennamen für Inhaltsblockelemente. Eine Klasse ist für alle möglichen Breiten in Bezug auf Spaltenbereiche erforderlich. Verwenden Sie beispielsweise die `span3` -Klasse `div` Elemente, die sich über drei Spalten erstrecken, verwenden Sie `span4` Klassen für Bereiche mit vier Spalten. Definieren Sie so viele Klassen wie Spalten in Ihrem Raster vorhanden sind.

1. Fügen Sie für jede angestrebte Darstellungsfeldgröße die entsprechende Medienabfrage zu Ihrer CSS-Datei hinzu. Fügen Sie in jeder Medienabfrage die folgenden Elemente hinzu:

   * Einen Selektor für die Klasse `content`, z. B. `.content{}`.
   * Selektoren für die span-Klassen, z. B `.span3{ }`.
   * Einen Selektor für die Klasse `row-fluid`, z. B. `.row-fluid{ }`.
   * Selektoren für span-Klassen, die sich in row-fluid-Klassen befinden, z. B. `.row-fluid span3 { }`.

1. Fügen Sie jedem Selektor width-Stile hinzu:

   1. Legen Sie für die Breite von `content`-Selektoren die absolute Größe der Seite fest, z. B. `width:480px`.
   1. Setzen Sie die Breite aller Zeilenflüssigkeitsselektoren auf 100 %.
   1. Legen Sie die Breite aller span-Selektoren auf die absolute Breite des Inhaltsbausteins fest. Ein triviales Raster verwendet gleichmäßig verteilte Spalten mit derselben Breite: `(absolute width of page)/(number of columns)`.
   1. Legen Sie die Breite der `.row-fluid .span`-Selektoren als Prozentsatz der Gesamtbreite fest. Berechnen Sie diese Breite mithilfe der Formel `(absolute span width)/(absolute page width)*100`.

#### Positionieren von Inhaltsblöcken in Zeilen {#positioning-content-blocks-in-rows}

Verwenden Sie den Float-Stil des `.row-fluid` -Klasse, damit Sie steuern können, ob die Inhaltsbausteine in einer Zeile horizontal oder vertikal angeordnet sind.

* Die Stile `float:left` und `float:right` bedingen die horizontale Verteilung untergeordneter Elemente (Inhaltsblöcke).

* Der Stil `float:none` bedingt die vertikale Verteilung untergeordneter Elemente.

Fügen Sie den Stil dem `.row-fluid`-Selektor in den Medienabfragen hinzu. Legen Sie den Wert entsprechend dem Seiten-Layout fest, das Sie für die Medienabfrage verwenden. Das folgende Diagramm zeigt beispielsweise eine Zeile, die Inhalte für breite Viewports horizontal und für schmale Viewports vertikal verteilt.

![](do-not-localize/chlimage_1-3a.png)

Dieses Verhalten kann durch die folgende CSS implementiert werden:

```xml
@media (min-width: 768px) and (max-width: 979px) {
   .row-fluid {
       width:100%;
       float:left
   }
}

@media (max-width:480px){
    .row-fluid {
       width:100%;
       float:none
   }
}
```

#### Zuweisen von Klassen zu Inhaltsblöcken {#assigning-classes-to-content-blocks}

Legen Sie für das Seitenlayout jeder gewünschten Darstellungsfeldgröße die Anzahl der Spalten fest, die jeder Inhaltsbaustein umfasst. Bestimmen Sie dann, welche Klasse für die div-Elemente dieser Inhaltsbausteine verwendet werden soll.

Wenn Sie die div-Klassen eingerichtet haben, können Sie das Raster mithilfe Ihrer AEM-Anwendung implementieren.
