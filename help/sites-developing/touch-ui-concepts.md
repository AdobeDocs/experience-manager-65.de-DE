---
title: Konzepte der Touch-optimierten Benutzeroberfläche von Adobe Experience Manager
description: Mit Adobe Experience Manager 5.6 führte Adobe eine neue Touch-optimierte Benutzeroberfläche mit responsivem Design für die Autorenumgebung ein
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: f13ac6c2-16ab-422d-9005-ab0b49172271
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2147'
ht-degree: 26%

---

# Konzepte der Touch-optimierten Benutzeroberfläche von Adobe Experience Manager{#concepts-of-the-aem-touch-enabled-ui}

Adobe Experience Manager (AEM) verfügt über eine Touch-optimierte Benutzeroberfläche mit [responsives Design](/help/sites-authoring/responsive-layout.md) für die Autorenumgebung, die sowohl für Touch- als auch für Desktop-Geräte entwickelt wurde.

>[!NOTE]
>
>Die Touch-optimierte Benutzeroberfläche ist die standardmäßige Benutzeroberfläche von AEM. Die klassische Benutzeroberfläche ist seit AEM 6.4 veraltet.

Die Touch-optimierte Benutzeroberfläche umfasst Folgendes:

* Suite-Kopfzeile:
   * Zeigt das Logo an.
   * Enthält einen Link zu „Globale Navigation“.
   * Bietet einen Link zu anderen generischen Aktionen, z. B. Suche, Hilfe, Experience Cloud-Lösungen, Benachrichtigungen und Benutzereinstellungen.
* Leiste auf der linken Seite (Anzeige bei Bedarf, kann ausgeblendet werden):
   * Zeitleiste
   * Verweise
   * Filter
* Die Navigationskopfzeile, die ebenfalls kontextabhängig ist und Folgendes anzeigen kann:
   * Gibt an, welche Konsole Sie derzeit verwenden, oder Ihren Standort oder beides in dieser Konsole
   * Auswahl für die linke Leiste
   * Breadcrumb
   * Zugriff auf geeignete Aktionen vom Typ **Erstellen**
   * Anzeigen von Auswahlen
* Der Inhaltsbereich, der:
   * Listet die Inhaltselemente auf (z. B. Seiten, Assets, Forumsbeiträge usw.)
   * Kann nach Bedarf formatiert werden, z. B. Spalte, Karte oder Liste
   * Nutzung eines responsiven Designs (Größe der Anzeige wird je nach Gerät bzw. Fenstergröße automatisch angepasst)
   * Scrollen unendlich (keine Seitennummerierung mehr, alle Elemente werden in einem Fenster aufgelistet)

![chlimage_1-79](assets/chlimage_1-79.png)

>[!NOTE]
>
>Fast alle AEM Funktionen wurden auf die Touch-optimierte Benutzeroberfläche portiert. In einigen wenigen Fällen wird die Funktionalität jedoch auf die klassische Benutzeroberfläche zurückgesetzt. Siehe [Funktionsstatus der Touch-optimierten Benutzeroberfläche](/help/release-notes/touch-ui-features-status.md) für weitere Informationen.

Die Touch-optimierte Benutzeroberfläche wurde von Adobe entwickelt, um die Konsistenz des Benutzererlebnisses über mehrere Produkte hinweg zu gewährleisten. Er basiert auf:

* **Coral-Benutzeroberfläche** (CUI) eine Implementierung des visuellen Adobe-Stils für die Touch-optimierte Benutzeroberfläche. Die Coral-Benutzeroberfläche bietet alles, was Ihr Produkt/Projekt/Ihre Webanwendung benötigt, um den visuellen Stil der Benutzeroberfläche zu übernehmen.
* **Granite-Benutzeroberfläche** -Komponenten werden mit der Coral-Benutzeroberfläche erstellt.

Die Grundprinzipien der Touch-optimierten Benutzeroberfläche sind:

* Mobilgeräte zuerst (mit Blick auf Desktop)
* Responsives Design
* Kontextbezogene Anzeige
* Wiederverwendbar
* Einschließen der eingebetteten Referenzdokumentation
* Einschließen eingebetteter Tests
* Bottom-up-Design, um sicherzustellen, dass diese Prinzipien auf jedes Element und jede Komponente angewendet werden

Einen weiteren Überblick über die Struktur der Touch-optimierten Benutzeroberfläche finden Sie unter [Struktur der AEM Touch-optimierten Benutzeroberfläche](/help/sites-developing/touch-ui-structure.md).

## AEM Technologiestapel {#aem-technology-stack}

AEM verwendet die Granite-Plattform als Basis und die Granite-Plattform umfasst unter anderem das Java™ Content Repository.

![chlimage_1-80](assets/chlimage_1-80.png)

## Granite {#granite}

Granite ist ein Adobe zum Öffnen des Webstapels und bietet verschiedene Komponenten, darunter:

* Ein Anwendungs-Starter
* Ein OSGi-Framework, in dem alles bereitgestellt wird
* Mehrere OSGi-Kompendium-Dienste zur Unterstützung von Bauanwendungen
* Ein umfassendes Protokollierungs-Framework mit verschiedenen Protokollierungs-APIs
* Die CRX-Repository-Implementierung der JCR-API-Spezifikation
* Das Apache Sling Web Framework
* Zusätzliche Teile des aktuellen CRX-Produkts

>[!NOTE]
>
>Granite wird als offenes Entwicklungsprojekt innerhalb der Adobe ausgeführt: Beiträge zum Code, Diskussionen und Probleme werden aus dem gesamten Unternehmen übernommen.
>
>Granite ist jedoch **not** ein Open-Source-Projekt. Es basiert stark auf mehreren Open-Source-Projekten (insbesondere Apache Sling, Felix, Jackrabbit und Lucene), aber Adobe zeichnet eine klare Linie zwischen dem, was öffentlich ist und dem, was intern ist.

## Granite-Benutzeroberfläche {#granite-ui}

Die Granite-Engineering-Plattform bietet außerdem ein Framework für die Foundation-Benutzeroberfläche. Die wichtigsten Ziele sind:

* Bereitstellen granularer UI-Widgets
* Implementieren Sie die Benutzeroberflächenkonzepte und illustrieren Sie die Best Practices (Rendern von langen Listen, Filtern von Listen, CRUD von Objekten, CUD-Assistenten usw.)
* Bereitstellung einer erweiterbaren und Plug-in-basierten Verwaltungsbenutzeroberfläche

Diese erfüllen die Anforderungen:

* Respektieren von &quot;mobile first&quot;
* Erweiterbar
* Überschreiben einfach

![chlimage_1-81](assets/chlimage_1-81.png)
GraniteUI.pdf

[Datei abrufen](assets/graniteui.pdf)
Die Granite-Benutzeroberfläche:

* Verwendet die RESTful-Architektur von Sling
* Implementiert Komponentenbibliotheken zum Erstellen inhaltsorientierter Webanwendungen
* Bietet granulare UI-Widgets
* Bietet eine standardmäßige, standardisierte Benutzeroberfläche
* Ist erweiterbar
* Wird sowohl für mobile als auch für Desktop-Geräte entwickelt (berücksichtigt zuerst mobile Geräte)
* Kann in jeder beliebigen Granite-basierten Plattform/jedem beliebigen Produkt/Projekt verwendet werden, z. B. AEM

![chlimage_1-82](assets/chlimage_1-82.png)

* [Granite-Benutzeroberfläche – Foundation-Komponenten](#granite-ui-foundation-components) Diese Bibliothek mit Grundlagenkomponenten kann von anderen Bibliotheken verwendet oder erweitert werden.
* [Granite-Benutzeroberfläche – Verwaltungskomponenten](#granite-ui-administration-components)

### Client-seitig und Server-seitig {#client-side-vs-server-side}

Die Client-Server-Kommunikation in der Granite-Benutzeroberfläche besteht aus Hypertext, nicht aus Objekten. Daher ist es nicht erforderlich, dass der Client die Geschäftslogik versteht

* Der Server ergänzt die HTML mit semantischen Daten.
* Der Client reichert den Hypertext mit Hypermedia (Interaktion) an

![chlimage_1-83](assets/chlimage_1-83.png)

#### Clientseite {#client-side}

Dabei wird eine Erweiterung des HTML-Vokabulars verwendet, vorausgesetzt der Autor kann seine Absicht zum Erstellen einer interaktiven Webanwendung zum Ausdruck bringen. Dies ist ein ähnlicher Ansatz wie [WAI-ARIA](https://www.w3.org/TR/wai-aria/) und [Mikroformate](https://microformats.org/).

Sie besteht in erster Linie aus einer Sammlung von Interaktionsmustern (z. B. asynchrones Senden eines Formulars), die von JS- und CSS-Codes interpretiert werden und clientseitig ausgeführt werden. Die Rolle der Client-Seite besteht darin, das Markup für Interaktivität zu verbessern (das vom Server als Hypermedia-Angebot angegeben wird).

Die Client-Seite ist unabhängig von jeder Server-Technologie. Solange der Server das entsprechende Markup bereitstellt, kann die Client-Seite seine Rolle erfüllen.

Derzeit werden die JS- und CSS-Codes als Granite bereitgestellt [clientlibs](/help/sites-developing/clientlibs.md) unter der Kategorie:

`granite.ui.foundation and granite.ui.foundation.admin`

Die Bereitstellung erfolgt im Rahmen des Inhaltspakets:

`granite.ui.content`

#### Serverseitig {#server-side}

Dies wird durch eine Sammlung von Sling-Komponenten gebildet, die es dem Autor ermöglichen, *zusammensetzen* eine schnelle Webapp. Der Entwickler entwickelt Komponenten, der Autor stellt die Komponenten zu einer Webanwendung zusammen. Die Rolle der Server-Seite besteht darin, dem Client das Hypermedia-Angebot (Markup) zu geben.

Derzeit befinden sich die Komponenten im Granite-Repository unter:

`/libs/granite/ui/components/foundation`

Dies wird als Teil des Inhaltspakets bereitgestellt:

`granite.ui.content`

### Unterschiede zur klassischen Benutzeroberfläche {#differences-with-the-classic-ui}

Die Unterschiede zwischen der Granite-Benutzeroberfläche und ExtJS (für die klassische Benutzeroberfläche verwendet) sind ebenfalls interessant:

<table>
 <tbody>
  <tr>
   <td><strong>ExtJS</strong></td>
   <td><strong>Granite-Benutzeroberfläche</strong></td>
  </tr>
  <tr>
   <td>Remote-Prozessaufruf<br /> </td>
   <td>Staatliche Übergänge</td>
  </tr>
  <tr>
   <td>Datenübertragungsobjekte</td>
   <td>Hypermedia</td>
  </tr>
  <tr>
   <td>Client kennt die Server-Interna</td>
   <td>Der Client kennt keine Interna</td>
  </tr>
  <tr>
   <td>„FAT-Client“</td>
   <td>„Thin-Client“</td>
  </tr>
  <tr>
   <td>Spezialisierte Client-Bibliotheken</td>
   <td>Universelle Client-Bibliotheken</td>
  </tr>
 </tbody>
</table>

### Foundation-Komponenten der Granite-Benutzeroberfläche {#granite-ui-foundation-components}

Die [Foundation-Komponenten der Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) stellen die grundlegenden Bausteine bereit, die zum Erstellen einer beliebigen Benutzeroberfläche erforderlich sind. Dazu gehören unter anderem:

* Schaltfläche
* Hyperlink
* Benutzer-Avatar

Die Foundation-Komponenten finden Sie unter:

`/libs/granite/ui/components/foundation`

Diese Bibliothek enthält eine Granite-UI-Komponente für jedes Coral-Element. Eine Komponente ist inhaltsgesteuert, wobei sich ihre Konfiguration im Repository befindet. Dies ermöglicht die Erstellung einer Granite-Benutzeroberflächen-Anwendung, ohne dass manuell HTML-Markup geschrieben werden muss.

Zweck:

* Komponentenmodell für HTML-Elemente
* Komponentenkomposition
* Automatische Tests von Einheiten und Funktionen

Implementierung:

* Repository-basierte Komposition und Konfiguration
* Verwenden der von der Granite-Plattform bereitgestellten Testeinrichtungen
* JSP-Vorlage

Diese Bibliothek mit Foundation-Komponenten kann von anderen Bibliotheken verwendet oder erweitert werden.

### ExtJS und zugehörige Granite-UI-Komponenten {#extjs-and-corresponding-granite-ui-components}

Bei der Aktualisierung von ExtJS-Code zur Verwendung der Granite-Benutzeroberfläche bietet die folgende Liste einen praktischen Überblick über ExtJS-xtypes und Knotentypen mit den entsprechenden Granite-UI-Ressourcentypen.

| **ExtJS xtype** | **Ressourcentyp der Granite-Benutzeroberfläche** |
|---|---|
| `button` | `granite/ui/components/foundation/form/button` |
| `checkbox` | `granite/ui/components/foundation/form/checkbox` |
| `componentstyles` | `cq/gui/components/authoring/dialog/componentstyles` |
| `cqinclude` | `granite/ui/components/foundation/include` |
| `datetime` | `granite/ui/components/foundation/form/datepicker` |
| `dialogfieldset` | `granite/ui/components/foundation/form/fieldset` |
| `hidden` | `granite/ui/components/foundation/form/hidden` |
| `html5smartfile, html5smartimage` | `granite/ui/components/foundation/form/fileupload` |
| `multifield` | `granite/ui/components/foundation/form/multifield` |
| `numberfield` | `granite/ui/components/foundation/form/numberfield` |
| `pathfield, paragraphreference` | `granite/ui/components/foundation/form/pathbrowser` |
| `selection` | `granite/ui/components/foundation/form/select` |
| `sizefield` | `cq/gui/components/authoring/dialog/sizefield` |
| `tags` | `granite/ui/components/foundation/form/autocomplete``cq/gui/components/common/datasources/tags` |
| `textarea` | `granite/ui/components/foundation/form/textarea` |
| `textfield` | `granite/ui/components/foundation/form/textfield` |

| **Knotentyp** | **Ressourcentyp der Granite-Benutzeroberfläche** |
|---|---|
| `cq:WidgetCollection` | `granite/ui/components/foundation/container` |
| `cq:TabPanel` | `granite/ui/components/foundation/container``granite/ui/components/foundation/layouts/tabs` |
| `cq:panel` | `granite/ui/components/foundation/container` |

### Granite-Benutzeroberfläche – Verwaltungskomponenten {#granite-ui-administration-components}

Die [Verwaltungskomponenten der Granite-Benutzeroberfläche](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) auf den Foundation-Komponenten aufbauen, um allgemeine Bausteine bereitzustellen, die von jeder Administration-Anwendung implementiert werden können. Dazu gehören unter anderem:

* Globale Navigationsleiste
* Leiste (Skelett)
* Suchbereich

Zweck:

* Einheitliches Erscheinungsbild für Verwaltungsanwendungen
* RAD für Applikationen zur Administration

Implementierung:

* Vordefinierte Komponenten mit den Foundation-Komponenten
* Komponenten können angepasst werden

## Coral-Benutzeroberfläche {#coral-ui}

CoralUI.pdf

[Datei abrufen](assets/coralui.pdf)
Die Coral-Benutzeroberfläche (CUI) ist eine Implementierung des visuellen Adobe-Stils für die Touch-optimierte Benutzeroberfläche, der für Konsistenz des Benutzererlebnisses über mehrere Produkte hinweg sorgt. Die Coral-Benutzeroberfläche bietet alles, was Sie benötigen, um den visuellen Stil der Authoring-Umgebung zu übernehmen.

>[!CAUTION]
>
>Die Coral-Benutzeroberfläche ist eine UI-Bibliothek, die AEM Kunden zum Erstellen von Anwendungen und Webschnittstellen innerhalb der Grenzen ihrer lizenzierten Nutzung des Produkts zur Verfügung gestellt wird.
>
>Die Nutzung der Coral-Benutzeroberfläche ist nur unter folgenden Bedingungen bzw. für folgende Zwecke zulässig:
>
>
>* Wenn es versandt und mit AEM gebündelt wurde.
>* Wird verwendet, wenn die vorhandene Benutzeroberfläche der Authoring-Umgebung erweitert wird.
>* Begleitmaterial, Anzeigen und Präsentationen von Adobe
>* Die Benutzeroberfläche von Anwendungen mit Adobe-Branding (die Schriftart darf nicht für andere Zwecke verfügbar sein).
>* Mit geringfügigen Anpassungen.
>
>Die Verwendung der Coral-Benutzeroberfläche sollte in folgenden Fällen vermieden werden:
>
>* Dokumente und andere nicht mit Adobe in Verbindung stehende Elemente.
>* Umgebungen zur Inhaltserstellung (in denen die vorhergehenden Elemente möglicherweise von anderen generiert werden).
>* Anwendungen/Komponenten/Webseiten, die nicht eindeutig mit Adobe verbunden sind.
>

Die Coral-Benutzeroberfläche ist eine Sammlung von Bausteinen für die Entwicklung von Web-Anwendungen.

![chlimage_1-84](assets/chlimage_1-84.png)

Sie ist vollständig modular konzipiert und jedes Modul stellt basierend auf seiner primäre Rolle eine eigene Ebene dar. Obwohl die Ebenen so konzipiert wurden, dass sie sich gegenseitig unterstützen, können sie bei Bedarf auch unabhängig voneinander verwendet werden. Dies ermöglicht die Implementierung des Coral-Benutzererlebnisses in jeder HTML-fähigen Umgebung.

In der Coral-Benutzeroberfläche ist es nicht erforderlich, ein bestimmtes Entwicklungsmodell und/oder eine bestimmte Plattform zu verwenden. Hauptziel von Coral ist die Bereitstellung eines einheitlichen und sauberen HTML5-Markups, unabhängig von der eigentlichen Methode, mit der dieses Markup ausgegeben wird. Er kann für Client- oder Server-seitiges Rendering, Vorlagen, JSP, PHP oder auch Adobe Flash-RIA-Anwendungen verwendet werden, um nur einige zu nennen.

### HTML-Elemente - Markup-Ebene {#html-elements-the-markup-layer}

Die HTML-Elemente bieten ein einheitliches Erscheinungsbild für alle Elemente der grundlegenden Benutzeroberfläche (einschließlich Navigationsleiste, Schaltfläche, Menü, Leiste usw.).

Auf der grundlegendsten Ebene ist ein HTML-Element ein HTML-Tag mit einem dedizierten Klassennamen. Komplexere Elemente können aus mehreren Tags zusammengestellt werden, die ineinander geschachtelt sind (auf spezifische Weise).

Das CSS wird verwendet, um das eigentliche Erscheinungsbild bereitzustellen. Um das Erscheinungsbild einfach anzupassen (z. B. beim Branding), werden tatsächliche Stilwerte als Variablen deklariert, die durch die [WENIGER](https://lesscss.org/) Präprozessor während der Laufzeit.

Zweck:

* Grundlegende Benutzeroberflächen-Elemente mit einem gemeinsamen Erscheinungsbild bereitstellen
* Standardrastersystem bereitstellen

Implementierung:

* HTML-Tags mit Stilen, die von [Bootstrap](https://twitter.github.com/bootstrap/)
* Klassen werden in LESS-Dateien definiert
* Symbole werden als Schriftspritzen definiert

Beispiel für verwendeten Markup-Code:

```xml
<button class="btn btn-large btn-primary" type="button">Large button</button>
<button class="btn btn-large" type="button">Large button</button>
```

Darstellung:

![chlimage_1-85](assets/chlimage_1-85.png)

Das Erscheinungsbild wird in LESS definiert und es besteht eine Bindung an ein Element nach dem dedizierten Klassennamen (der folgende Auszug wurde gekürzt):

```xml
.btn {
    font-size: @baseFontSize;
    line-height: @baseLineHeight;
    .buttonBackground(@btnBackground,
                                @btnBackgroundHighlight,
                                @grayDark, 0 1px 1px rgba(255,255,255,.75));
```

Die tatsächlichen Werte werden in einer LESS-Variablendatei definiert (der folgende Auszug wurde gekürzt):

```xml
@btnBackgroundHighlight: darken(@white, 10%);
@btnPrimaryBackgroundHighlight: spin(@btnPrimaryBackground, 20%);
@baseFontSize: 17px;
@baseFontFamily: @sansFontFamily;
```

### Element-Plugins {#element-plugins}

Viele HTML-Elemente müssen eine gewisse Dynamik aufweisen, z. B. das Öffnen und Schließen von Popup-Menüs. Dies ist die Rolle der Element-Plug-ins, die solche Aufgaben durch Manipulation des DOM mit JavaScript ausführen.

Ein Plug-in ist entweder:

* Für den Betrieb mit einem bestimmten DOM-Element entwickelt. Für ein Dialogfeld-Plug-in wird beispielsweise `DIV class=dialog` erwartet.
* Es ist generischer Art. Über einen Layout-Manager wird beispielsweise das Layout für eine Liste mit `DIV`- oder `LI`-Elementen bereitgestellt.

Das Plug-in-Verhalten kann mit Parametern angepasst werden, indem Sie:

* Übergeben der Parameter mit einem JavaScript-Aufruf
* Verwenden von dedizierten `data-*`-Attributen, die an den HTML-Markup-Code gebunden sind

Entwickler können für jedes Plug-in den besten Ansatz wählen, aber die Faustregel lautet:

* `data-*`-Attribute für Optionen, die sich auf das HTML-Layout beziehen. So legen Sie beispielsweise die Anzahl der Spalten fest
* API-Optionen/-Klassen für Funktionen im Zusammenhang mit Daten. Beispiel: Erstellung der Liste der anzuzeigenden Elemente

Dasselbe Konzept wird für die Implementierung der Formularüberprüfung verwendet. Für ein Element, das validiert werden soll, müssen Sie das erforderliche Eingabeformular als benutzerdefiniertes `data-*`-Attribut angeben. Dieses Attribut wird dann als Option für ein Validierungs-Plug-in verwendet.

>[!NOTE]
>
>Die HTML5-native Formularvalidierung sollte nach Möglichkeit immer verwendet und erweitert werden.

Zweck:

* Dynamisches Verhalten für HTML-Elemente bereitstellen
* Bereitstellung benutzerdefinierter Layouts, die mit reinem CSS nicht möglich sind
* Formularüberprüfung durchführen
* Erweiterte DOM-Manipulation durchführen

Implementierung:

* jQuery-Plug-in, gebunden an bestimmte DOM-Elemente
* Verwenden von `data-*`-Attributen zum Anpassen des Verhaltens

Ein Auszug aus Markup-Beispiel-Code (beachten Sie die als Daten-&#42;-Attribute angegebenen Optionen):

```xml
<ul data-column-width="220" data-layout="card" class="cards">
  <li class="item">
    <div class="thumbnail">
      <img href="/a.html" src="/a.thumb.319.319..png">
      <div class="caption">
        <h4>Toolbar</h4>
          <p><small>toolbar</small><br></p>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="thumbnail">
      <img href="/a.html" src="/a.thumb.319.319..png">
      <div class="caption">
        <h4>Toolbar</h4>
        <p><small>toolbar</small><br></p>
      </div>
    </div>
  </li>
```

Aufruf des jQuery-Plug-ins:

```
$('.cards').cardlayout ();
```

Dies zeigt Folgendes:

![chlimage_1-86](assets/chlimage_1-86.png)

Die `cardLayout` -Plug-in legt die im `UL` -Elemente basierend auf ihren jeweiligen Höhen und unter Berücksichtigung der Breite des Elternteils.

### HTML-Elemente-Widgets {#html-elements-widgets}

Ein Widget kombiniert ein oder mehrere grundlegende Elemente mit einem JavaScript-Plug-in, um UI-Elemente auf &quot;höherer Ebene&quot;zu bilden. Dadurch können komplexere Verhaltensweisen sowie ein komplexeres Erscheinungsbild implementiert werden, als ein einzelnes Element liefern könnte. Gute Beispiele hierfür sind die Tag-Auswahl oder Leisten-Widgets.

Ein Widget kann benutzerdefinierte Ereignisse sowohl auslösen als auch darauf lauschen, um eine Kooperation mit anderen Widgets der Seite zu ermöglichen. Einige Widgets sind native jQuery-Widgets, die die Coral-HTML-Elemente verwenden.

Zweck:

* Implementieren von UI-Elementen auf höherer Ebene mit komplexem Verhalten
* Auslösen und Verarbeiten von Ereignissen

Implementierung:

* jQuery-Plug-in + HTML Markup
* Kann Client-/Server-seitige Vorlagen verwenden

Beispiel-Markup:

```
<input type="text" name="tags" placeholder="Tags" class="tagManager"/>
```

Aufruf des jQuery-Plug-ins (mit Optionen):

```
$(".tagManager").tagsManager({
        prefilled: ["Pisa", "Rome"] })
```

Das Plug-in gibt HTML Markup aus (dieses Markup verwendet grundlegende Elemente, die intern andere Plug-ins verwenden können):

```
<span>Pisa</code>
<a title="Removing tag" tagidtoremove="0"
   id="myRemover_0" class="myTagRemover" href="#">x</a></code>

<span id="myTag_1" class="myTag"><span>Rome</code>
<a title="Removing tag" tagidtoremove="1"
   id="myRemover_1" class="myTagRemover" href="#">x</a></code>

<input type="text" data-original-title="" class="input-medium tagManager"
       placeholder="Tags" name="tags" data-provide="typeahead" data-items="6"
       autocomplete="off">
```

Dies zeigt Folgendes:

![chlimage_1-87](assets/chlimage_1-87.png)

### Dienstprogrammbibliothek {#utility-library}

Diese Bibliothek ist eine Sammlung von JavaScript-Helper-Plug-ins und/oder Funktionen, die:

* Benutzeroberflächenunabhängig
* Entscheidend für die Erstellung von Web-Anwendungen mit vollem Funktionsumfang

Dazu gehören die XSS-Handhabung und der Ereignisbus.

Die HTML-Element-Plug-ins und Widgets können zwar auf Funktionen der Dienstprogrammbibliothek beruhen, die Dienstprogrammbibliothek kann jedoch keine feste Abhängigkeit von den Elementen und Widgets selbst aufweisen.

Zweck:

* Bereitstellung von allgemeiner Funktionalität
* Implementierung des Ereignisbus
* Clientseitige Vorlagen
* XSS

Implementierung:

* jQuery-Plug-ins oder AMD-konforme JavaScript-Module
