---
title: Stilkonstrukte für adaptive Formulare
seo-title: Stilkonstrukte für adaptive Formulare
description: Verwenden Sie LESS-Framework, um das Erscheinungsbild der adaptiven Formulare anzupassen.
seo-description: Verwenden Sie LESS-Framework, um das Erscheinungsbild der adaptiven Formulare anzupassen.
uuid: d2e45ad9-7322-43ce-a1dd-ad97e2eea742
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: ed50fa70-a8dd-4cc6-82a9-d59de0fa417d
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2324'
ht-degree: 90%

---


# Stilkonstrukte für adaptive Formulare{#styling-constructs-for-adaptive-forms}

## Voraussetzungen {#prerequisites}

Kenntnisse im Umgang mit CSS und von LESS-Framework.

## Was angepasst werden kann {#what-can-be-customized}

Der Artikel listet öffentlich verfügbare CSS-Klassen von adaptiven Formularen. Sie können diese Klassen nutzen, um verschiedene Komponenten eines adaptiven Formulars zu formatieren. Der Stil von Authoring-Komponenten, wie Dialogfelder und Statusleisten, die Warnungen anzeigen, gehen über den Rahmen dieses Artikels hinaus. Verwenden Sie diese Stilkonstrukte, um Stile (mit CSS oder früher) nur dann zu erstellen, wenn Sie mit dem [Design- Editor ](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/themes.html)keine Komponenten formatieren können.

## Anpassen von Stilen in adaptiven Formularen {#customizing-styles-in-adaptive-forms}

Das LESS-Framework vereinfacht das Anwendungsbeispiel, um Stile in adaptiven Formularen anzupassen. Mit dem Framework können Sie Stile mit einem Set von Variablen und Funktionen (mixins) definieren. Mit dem LESS-Framework können Sie die Größe des enthaltenen Codes reduzieren und dessen Wiederverwendbarkeit verbessern.

Sie können adaptive Formularstile wie folgt anpassen:

* Design ändern
* Ändern Sie den Stil der Komponente

## Designänderung  {#changing-theme}

Sie können das Design eines adaptiven Formulars ändern, um sicherzustellen, dass sein Erscheinungsbild mit den Webseiten konsistent ist, in denen das adaptive Formular eingebettet ist.

Änderungen des Gesamtaussehens des adaptiven Formulars mithilfe von CSS-Eigenschaften sind in der Regel Teil der Designänderungen. Wesentliche Änderungen am lo &quot;ok and sense of the adaptive form&quot;, wie Änderungen im Layout und der Platzierung von Komponenten, werden nicht als Designänderungen betrachtet.

Basierend auf dem Bootstrap, definiert der folgende Satz von CSS-Eigenschaften das Design einer Webseite:

* Hintergrundfarbe
* Rahmen (Typ, Farbe, Stärke)
* Schriftfarbe
* Erweiterte Umrandung
* Marge
* Schriftgrad
* LineHeight

Derzeit sind LESS-Variablen nur für diese Eigenschaften der verschiedenen Elemente in einem adaptiven Formular definiert.

## Änderung des Komponentenstils  {#changing-component-style}

Sie können Änderungen an Aussehen, Layout, Positionierung und Sichtbarkeit von Elementen vornehmen. Um diese Aufgabe zu erreichen, erstellen oder aktualisieren Sie Ihre benutzerdefinierten .css-Dateien, um die in diesem Artikel aufgeführten Stilkonstrukte einzuschließen.

Um ein Design auf ein adaptives Formular anzuwenden, öffnen Sie das adaptive Formular zum Bearbeiten, öffnen Sie den Container mit den Eigenschaften des adaptiven Formulars und geben Sie im Basisregister den Pfad der benutzerdefinierten CSS-Datei ein. Standard-Designkonstrukte des adaptiven Formulars und mit den in der benutzerdefinierten CSS-Datei aufgeführten Konstrukten überschriebene Konstrukte.

## Komponenten {#components}

Komponenten, die in diesem Artikel behandelt werden, verfügen über vordefinierte CSS-Klassen. Sie können die Variablen bearbeiten, um die Stile in den CSS-Klassen zu ändern. Alternativ dazu können Sie die gesamte Klasse neu definieren. In diesem Abschnitt werden die Klassen in den Komponenten und Stile, die Sie mithilfe von Variablen ändern können, beschrieben.

## Container-Stile {#container-styling}

Ein Container ist die Komponente der obersten Ebene. Andere Bedienfelder und Felder befinden sich unter der Container-Komponente.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guideContainerNode</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablenbeschreibung</strong></p> </td>
   <td><p><strong>Variablenbeschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>container-bgColor</code></p> </td>
   <td><p>Hintergrundfarbe des Containers</p> </td>
  </tr>
  <tr>
   <td><p><code>container-padding</code></p> </td>
   <td><p>Füllbereich für den Containers</p> </td>
  </tr>
  <tr>
   <td><p><code>container-margin</code></p> </td>
   <td><p>Rand für den Container</p> </td>
  </tr>
  <tr>
   <td><p><code>container-fontColor</code></p> </td>
   <td><p>Schriftfarbe für den Container</p> </td>
  </tr>
 </tbody>
</table>

## Feldstile {#field-styling}

Adaptive Formulare enthalten verschiedene Arten von Feldern. Jedes Feld verfügt über einen eindeutigen Klassennamen, der der Name des Feldes ist. Das Feld hat auch einen gemeinsamen Klassennamen `guideFieldNode`.

Felder enthalten Beschriftungen, Widgets, Hilfebeschreibung (lange und kurze Beschreibungen) und Feldhilfesymbole (Fragezeichen).

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guideFieldNode</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>field-padding</code><strong></strong></p> </td>
   <td><p>Auffüllung für das Feld</p> </td>
  </tr>
  <tr>
   <td><p><code>field-error-font-color</code></p> </td>
   <td><p>Schriftfarbe der Fehlermeldung des Felds</p> </td>
  </tr>
  <tr>
   <td><p><code>field-error-font-size</code></p> </td>
   <td><p>Schriftgröße der Fehlermeldung des Felds</p> </td>
  </tr>
 </tbody>
</table>

## Beschriftungsstile {#label-styling}

Das für das Feld verwendete HTML-Element **label** enthält die Klassen **left** oder **top**, je nachdem, ob sich die Beschriftung oben oder links befindet.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guideFieldLabel</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>label-font-color</code></p> </td>
   <td><p>Schriftfarbe für die Feldbeschriftung</p> </td>
  </tr>
  <tr>
   <td><p><code>label-font-size</code></p> </td>
   <td><p>Schriftgröße für die Feldbeschriftung</p> </td>
  </tr>
  <tr>
   <td><p><code>label-line-height</code></p> </td>
   <td>CSS-Zeilenhöheneigenschaft für die Feldbeschriftung </td>
  </tr>
  <tr>
   <td><p><code>label-font-weight</code></p> </td>
   <td>CSS-Schriftbreiteneigenschaft für die Feldbeschriftung </td>
  </tr>
  <tr>
   <td><p><code>label-margin</code></p> </td>
   <td><p>Rand für die Feldbeschriftung</p> </td>
  </tr>
 </tbody>
</table>

Die CSS-Regeln für die Beschriftung werden mit der Beschriftung **guideFieldLabel** angewendet. Wenn Sie ein Verfasser sind, überschreiben Sie diese Regel, um Ihre benutzerdefinierten Änderungen vorzunehmen.

## Widget-Stile {#widgets-styling}

Je nach Typ enthalten Widgets auch Klassen. Normalerweise beinhalten Widgets die `guideFieldWidget`-Klasse. Die Widgets, die mit HTML geliefert werden, verwenden normalerweise die standardmäßige HTML-Elementeingabe und -Auswahl. Der Stil wird entsprechend ausgeführt. Sie können ein benutzerdefiniertes Widget nicht anpassen, indem Sie die Variablen ändern.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guideFieldWidget</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen <code></code></strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-bg-color</code></p> </td>
   <td>Hintergrundfarbe für die Widgets (funktioniert nicht für Kontrollkästchen und Optionsfelder)</td>
  </tr>
  <tr>
   <td><p><code>widgets-border-color</code></p> </td>
   <td><p>Rahmenfarbe für dieses Widget</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border-thickness</code></p> </td>
   <td><p>Rahmengröße für die Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border-radius</code></p> </td>
   <td><p>Rahmenradius für die Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border-type</code></p> </td>
   <td><p>Rahmentyp für die Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widget-border-focus-type</code></p> </td>
   <td><p>Fokustyp für Widget-Rahmen</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-border</code></p> </td>
   <td><p>Konsolidierter Rahmenstil von Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-font-color</code></p> </td>
   <td><p>Farbe des Texts im Widget</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-font-size</code></p> </td>
   <td><p>Größe des Textes innerhalb des Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-line-height</code></p> </td>
   <td>CSS-Zeilenhöhen-Eigenschaft für das Widget </td>
  </tr>
  <tr>
   <td><p><code>widgets-padding</code></p> </td>
   <td><p>CSS-Auffüllung für das Widget</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-focus-border-color</code></p> </td>
   <td><p>Rahmenfarbe, wenn das Widget im Fokus ist</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-mandatory-border-color</code></p> </td>
   <td><p>Randfarbe des Widgets für die Pflichtfelder</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-mandatory-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe des Widgets für die Pflichtfelder</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-disabled-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für das Widget, wenn das Feld deaktiviert ist</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-disabled-font-color</code></p> </td>
   <td><p>Schriftfarbe für das Widget, wenn das Feld deaktiviert ist</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-disabled-border-color</code></p> </td>
   <td><p>Rahmenfarbe für das Widget, wenn das Feld deaktiviert ist</p> </td>
  </tr>
  <tr>
   <td><p><code>widget-height</code></p> </td>
   <td>Höhe des Widgets (funktioniert nicht für Kontrollkästchen und Optionsfelder)</td>
  </tr>
  <tr>
   <td><p><code>checkbutton-height</code></p> </td>
   <td><p>Höhe für Kontrollkästchen und Optionsfelder.</p> </td>
  </tr>
  <tr>
   <td><p><code>listboxwidget-height</code></p> </td>
   <td><p>Maximale Höhe für eine Mehrfachauswahl-Dropdown-Liste</p> </td>
  </tr>
 </tbody>
</table>

### Einschränkungen beim Widget-Stil  {#limitations-in-widget-styling}

Der Stil für fokussierte, deaktivierte und Pflichtfelder ist auf Variablen eingeschränkt. Sie können diese jedoch ändern, indem Sie die Stile überschreiben. Einschränkungen mithilfe von Variablen wird hauptsächlich dazu verwendet, um die Anzahl der Variablen zu kontrollieren. Die Einschränkung kann gelockert werden, wenn sich das Erscheinungsbild eines Felds drastisch ändert, da es sich in einem der zuvor besprochenen Status befindet.

## Hilfebeschreibung {#help-description}

Der Verfasser kann den Hilfeinhalt in den Feldern unter Verwendung der kurzen und langen Beschreibung angeben. Beide Komponenten haben eine gemeinsame Klasse `.guideHelpDescription` und eine andere Klasse `.long`/ `.short`, je nach Typ der Beschreibung. Der Hilfeinhalt wird in einem Absatzelement eingeschlossen, um den Stil der Beschreibung zu überschreiben. Die Hilfebeschreibung (lang und kurz) wird mithilfe der Variablen geändert. Angefangen wird mit Widgets-Hilfe, wie in der nachfolgenden Tabelle angegeben:

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-long-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe der langen Hilfe der Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-long-border-color</code></p> </td>
   <td><p>Rahmenfarbe der langen Hilfe der Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-long-border-indicator-color</code></p> </td>
   <td><p>Rahmenfarbe für linken Indikator der langen Hilfe der Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe der kurzen Hilfe der Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-color</code></p> </td>
   <td><p>Schriftfarbe der kurzen Hilfe der Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-tooltip-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe der kurzen QuickInfo-Hilfe der Widgets</p> </td>
  </tr>
  <tr>
   <td><p><code>widgets-help-short-tooltip-color</code></p> </td>
   <td><p>Schriftfarbe der kurzen QuickInfo-Hilfe·der Widgets</p> </td>
  </tr>
 </tbody>
</table>

## Geschäftsbedingungen  {#terms-and-conditions}

Mit dem Bedingungs-(TnC`` ``)Widget können Sie Bedingungen angeben. Sie können das Widget mithilfe von Variablen, die in der folgenden Tabelle beschrieben sind, anpassen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><code>tnc-unvisited</code></td>
   <td>Schriftfarbe des ungeöffneten tnc-Links.</td>
  </tr>
  <tr>
   <td><code>tnc-visited</code></td>
   <td>Schriftfarbe des geöffneten tnc-Links.</td>
  </tr>
 </tbody>
</table>

## Schaltfläche {#button}

Schaltflächen sind auch Widgets. Allerdings unterscheidet sich deren Stil von Widgets. In den adaptiven Formularen bildet Folgendes eine Schaltflächen:

* input[type = text]
* button
* Element mit Klasse .button

HTML-Code für Schaltfläche:

`<button type="button" >`

`<span class="iconButtonicon"></`

`span>`

`<span class="iconButtonlabel"></`

`span>`

`</button>`

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>iconButton-icon</code></p> </td>
   <td><p>Bietet Symbole für Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p><code>iconButton-label</code></p> </td>
   <td><p>Stilschaltflächen-Bezeichnung/Beschriftung</p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen <code></code></strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>button-border-size</code></p> </td>
   <td><p>Rahmengröße für die Schaltflächen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-border-type</code></p> </td>
   <td><p>Rahmentyp</p> </td>
  </tr>
  <tr>
   <td><p><code>button-padding</code></p> </td>
   <td><p>CSS-Auffüllung für die Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p><code>button-font-size</code></p> </td>
   <td><p>Schriftgröße für die Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p><code>button-background-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p><code>button-font-color</code></p> </td>
   <td><p>Schriftfarbe der Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p><code>button-border-color</code></p> </td>
   <td><p>Rahmenfarbe der Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p><code>button-large-padding</code></p> </td>
   <td><p>Auffüllung für große Schaltflächen (Schaltflächen mit Klasse .buttonlarge)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-large-font-size</code></p> </td>
   <td><p>Schriftgröße für große Schaltflächen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-small-padding</code></p> </td>
   <td><p>Auffüllung für kleine Schaltflächen (Schaltflächen mit Klasse .buttonsmall)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-small-font-size</code></p> </td>
   <td><p>Schriftgröße für kleine Schaltflächen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-info-background-color</code></p> </td>
   <td><p>Hintergrundfarbe für informative Schaltflächen (Schaltflächen mit Klasse .buttoninformative)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-info-font-color</code></p> </td>
   <td><p>Schriftfarbe für informative Schaltflächen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-info-border-color</code></p> </td>
   <td><p>Rahmenfarbe für informative Schaltflächen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-warning-background-color</code></p> </td>
   <td><p>Hintergrundfarbe für Warnungstilschaltflächen (Schaltflächen mit Klasse .buttonwarning)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-warning-font-color</code></p> </td>
   <td><p>Schriftfarbe für Warnungstilschaltflächen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-warning-border-color</code></p> </td>
   <td><p>Rahmenfarbe für Warnungstilschaltflächen</p> </td>
  </tr>
  <tr>
   <td><p><code>button-alert-background-color</code></p> </td>
   <td><p>Hintergrundfarbe für Warnschaltflächen (Schaltflächen mit Klasse .buttonalert)</p> </td>
  </tr>
  <tr>
   <td><p><code>button-alert-font-color</code></p> </td>
   <td><p>Schriftfarbe für Warnschaltflächen) </p> </td>
  </tr>
  <tr>
   <td><p><code>button-alert-border-color</code></p> </td>
   <td><p>Rahmenfarbe für Warnschaltflächen) </p> </td>
  </tr>
 </tbody>
</table>

## Fragezeichen {#question-mark}

Für die Widgets wird ein Fragezeichen angezeigt, wenn ein Verfasser eine lange Beschreibung im Hilfeinhalt hinzufügt. Das im Bootstrap bereitgestellte Standardsymbol wird verwendet. Um ein benutzerdefiniertes Symbol zu verwenden, können Sie die Bootstrap-Symbole anpassen.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guideHelpQuestionMark</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>questionmark-font-color</code></p> </td>
   <td><p>Farbe des Symbols</p> </td>
  </tr>
  <tr>
   <td><p><code>questionmark-hover-font-color</code></p> </td>
   <td><p>Farbe des Symbols, wenn mit der Maus darauf gezeigt wird</p> </td>
  </tr>
 </tbody>
</table>

## Tabelle {#table}

Sie können das Farbthema für Kopf- und Textzeilen in einer Tabelle ändern, indem Sie die folgenden Variablen verwenden.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>table-header-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Kopfzeile. Der Standardwert ist <code>#333</code>.<br /> </p> </td>
  </tr>
  <tr>
   <td><p><code>table-odd-row-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für die ungeraden Textzeile. Der Standardwert ist <code>rgb(255, 255, 255)</code>.</p> </td>
  </tr>
  <tr>
   <td><p><code>table-even-row-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für gerade Textzeile. Der Standardwert ist <code>#eee</code>.</p> </td>
  </tr>
 </tbody>
</table>

## Dateianhang {#file-attachment}

Mit dem Dateianhangswidget von adaptiven Formularen können Sie Dateien hochladen. Sie können außerdem das Widget mithilfe von Variablen anpassen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemPadding</code></p> </td>
   <td><p>Auffüllung für die im Widget angezeigten Dateien</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemBackground</code></p> </td>
   <td><p>Hintergrundfarbe für das Dateielement</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemBorderColor</code></p> </td>
   <td><p>Rahmenfarbe für den oberen Rahmen</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemColor</code></p> </td>
   <td><p>Schriftfarbe für das Dateielement</p> </td>
  </tr>
  <tr>
   <td><p><code>filePreviewIconColor</code></p> </td>
   <td><p>Farbe für das Vorschau-Symbol (Bootstrap-Symbol) im Widget</p> </td>
  </tr>
  <tr>
   <td><p><code>fileItemCommentHeight</code></p> </td>
   <td><p>Höhe des Kommentars für das Dateielement</p> </td>
  </tr>
 </tbody>
</table>

## Navigatorstile  {#navigator-styles}

Es gibt vier Arten von Navigatorregisterkarten. Dazu gehören Registerkarten links, oben, im Assistenten und im Akkordeon. Jeder Navigator beinhaltet eine andere Klasse.

<table>
 <tbody>
  <tr>
   <td><p><strong>Navigator</strong></p> </td>
   <td><p><strong>CSS-Klasse</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>Accordion</code></p> </td>
   <td><p>.accordion-navigators</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs on the left</code></p> </td>
   <td><p>.tab-navigators-vertical</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs on the top</code></p> </td>
   <td><p>.tab-navigators</p> </td>
  </tr>
  <tr>
   <td><p><code>Wizard</code></p> </td>
   <td><p>.wizard-navigators</p> </td>
  </tr>
 </tbody>
</table>

Im Folgenden wird der HTML-Code für das Registerkartennavigatorelement gezeigt (ähnlich der Bootstrap-Registerkarten):

`<li>`

`<a>tab title</a>`

`</li>`

`Accordion navigator is an exception, it has following barebone`

`structure:`

`<div class="accordion.navigators">`

`<div>`

`<div class = "guideHeader">`

`<a>`

`<span class = "guideSummary" ></code>`

`........................... repeatable buttons, if the repeatable configuration is set ................................`

`<div class = "repeatableButtons">`

`<button name="Add" class="Add"/>`

`<button name="Remove" class="Remove"/>`

`</div>`

`</a>`

`</div>`

`................................ panel content ..................................`

`</div>`

`</div>`

Sie können den Stil des Navigators mithilfe der CSS-Regeln, die die Elemente mithilfe der **untergeordneten** Selektoren auswählen, ändern. Wenn Sie beispielsweise einen textDecoration-Stil im Anker-Tag hinzufügen:

Registerkartennavigator oben:

`.tab-navigators`

`li a {`

`text-decoration:`

`underline;`

`}`

`Tab navigator on left:`

`.tab-navigators-vertical`

`li a {`

`text-decoration:`

`underline;`

`}`

`Accordion navigator:`

`.accordion-navigators .guideHeader a .guideSummary {`

`text-decoration:`

`underline;`

`}`

`Wizard navigator:`

`.wizard-navigators`

`li a {`

`text-decoration:`

`underline;`

`}`

Zusätzlich, gibt es Klassen für Stilregisterkartennavigatoren (links und oben), abhängig davon, ob sie verschachtelte/untergeordnete/Unter-Navigatoren haben.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>nested_true</code></p> </td>
   <td><p>Registerkartennavigatoren (links und oben) mit verschachtelten/untergeordneten/Unter-Navigatoren</p> </td>
  </tr>
  <tr>
   <td><p><code>nested_false</code></p> </td>
   <td><p>Registerkartennavigatoren (links und oben) mit verschachtelten/untergeordneten/Unter-Navigatoren</p> </td>
  </tr>
 </tbody>
</table>

Die guideNavIcon-Klasse bietet ein Standardsymbol für Registerkartennavigatoren (links und oben) und Assistentennavigatoren.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guideNavIcon</code></p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Sie können das Symbol für einen bestimmten Navigator ändern, indem Sie eine CSS-Klasse im Bedienfeld unter Authoring, Formularbeispiel &lt;CLASS_NAME> bereitstellen. Sie können ein **&lt;CLASS_NAME>_nav** für das Symbol des Navigators hinzufügen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><strong>Registerkartennavigatoren</strong></p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p><code>navigator-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für den gesamten Registerkartenavigator</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Registerkarte</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-font-color</code></p> </td>
   <td><p>Schriftfarbe für die Registerkarte</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-hover-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Registerkarte beim Maushover</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-hover-font-color</code></p> </td>
   <td><p>Schriftfarbe für die Registerkarte beim Maushover</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-active-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe, wenn das Bedienfeld im Fokus ist (aktiv)</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-active-font-color</code></p> </td>
   <td><p>Schriftfarbe, wenn das Bedienfeld im Fokus ist</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-completed-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe, wenn der Abschlussausdruck des Bedienfelds „true“ zurückgibt</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-completed-font-color</code></p> </td>
   <td><p>Schriftfarbe, wenn der Abschlussausdruck für das Bedienfelds „true“ zurückgibt</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-stepped-bg-color</code></p> </td>
   <td>Hintergrundfarbe, wenn das Bedienfeld einmal im Fokus war, aber der Abschlussausdruck „false“ zurückgibt </td>
  </tr>
  <tr>
   <td><p><code>tabs-stepped-font-color</code></p> </td>
   <td>Schriftartfarbe, wenn das Bedienfeld einmal im Fokus war, aber der Abschlussausdruck „false“ zurückgibt </td>
  </tr>
  <tr>
   <td><p><code>tabs-border-color</code></p> </td>
   <td><p>Rahmenfarbe für die Registerkarte</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-font-size</code></p> </td>
   <td><p>Schriftgröße für die Registerkarte</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-padding</code></p> </td>
   <td><p>Auffüllung für die Registerkarte</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-margin</code></p> </td>
   <td><p>Rand für die Registerkarte</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-vertical-margin</code></p> </td>
   <td><p>Rand für die vertikalen Registerkarten</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-border-thickness</code></p> </td>
   <td><p>Rahmengröße für die Registerkarten</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-min-height</code></p> </td>
   <td><p>Mindesthöhe der Registerkarten</p> </td>
  </tr>
  <tr>
   <td><p><code>heirarichal-indent</code></p> </td>
   <td><p>Einzug für die verschachtelten Registerkarten</p> </td>
  </tr>
  <tr>
   <td><p><strong>Assistentennavigatoren</strong></p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-navigator-bg-color</code></p> </td>
   <td>Hintergrundfarbe für den gesamten Assistentennavigator</td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für den Assistenten</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-font-color</code></p> </td>
   <td><p>Schriftfarbe für den Assistenten</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-active-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe, wenn das Bedienfeld im Fokus ist (aktiv)</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-active-font-color</code></p> </td>
   <td><p>Schriftfarbe, wenn das Bedienfeld im Fokus ist (fokussiert)</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-completed-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe, wenn der Abschlussausdruck des Bedienfelds „true“ zurückgibt</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-completed-font-color</code></p> </td>
   <td><p>Schriftfarbe, wenn der Abschlussausdruck für das Bedienfelds „true“ zurückgibt</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-stepped-bg-color</code></p> </td>
   <td>Hintergrundfarbe, wenn das Bedienfeld einmal im Fokus war, aber der Abschlussausdruck „false“ zurückgibt</td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-stepped-font-color</code></p> </td>
   <td><p>Schriftartfarbe, wenn das Bedienfeld einmal im Fokus war, aber der Abschlussausdruck „false“ zurückgibt </p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-border-color</code></p> </td>
   <td><p>Farbe für den Assistenten</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-font-size</code></p> </td>
   <td><p>Schriftgröße für den Assistenten</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-padding</code></p> </td>
   <td><p>Auffüllung für den Assistenten</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-tabs-border-thickness</code></p> </td>
   <td><p>Rahmengröße für den Assistenten</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-nav-bullet-border</code></p> </td>
   <td><p>Rahmenfarbe des Aufzählungszeichens für den Assistentennavigator (Präfix für Beschriftung/Bezeichnung)</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-progress-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe der Statusanzeige des Assistentennavigators</p> </td>
  </tr>
  <tr>
   <td><p><code>wizard-progress-color</code></p> </td>
   <td><p>Die Füllfarbe für die Statusanzeige</p> </td>
  </tr>
  <tr>
   <td><p><strong>Akkordeonnavigatoren</strong></p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p><code>accordion-tabs-padding</code></p> </td>
   <td><p>Auffüllung für Akkordeon</p> </td>
  </tr>
 </tbody>
</table>

## Bedienfeldstil {#panel-styling}

Ein Bedienfeld enthält eine optionale Symbolleiste und entsprechenden Inhalt.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guidePanelNode</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>panel-background-color</code></p> </td>
   <td><p>Hintergrundfarbe für das Bedienfeld</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-font-size</code></p> </td>
   <td><p>Schriftgröße für den Bedienfeldtext</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-font-color</code></p> </td>
   <td><p>Schriftfarbe für den Bedienfeldtext<br />  </p> </td>
  </tr>
  <tr>
   <td><p><code>panel-padding</code></p> </td>
   <td><p>Auffüllung im Bedienfeld</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-description-font-size</code></p> </td>
   <td><p>Schriftgröße der Bedienfeldbeschreibung</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-description-padding</code></p> </td>
   <td><p>Auffüllung der Bedienfeldbeschreibung</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-help-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Bedienfeldhilfe</p> </td>
  </tr>
  <tr>
   <td><p><code>panel-help-border-indicator-color</code></p> </td>
   <td><p>Indikatorrahmenfarbe für die Bedienfeldhilfe</p> </td>
  </tr>
 </tbody>
</table>

Der Bedienfeldknoten wird in Navigatoren und Inhalt unterteilt. Es`` `` gibt keine separate Stilkomponente für den Inhalt. Die beschriebenen Variablen werden auf den Navigator sowie Inhalte angewendet.

Die oberste Bedienfeld (RootPanel) verfügt nicht über diese Klasse.

## Mobile Stile {#mobile-styling}

## Kopfzeilenleiste {#header-bar}

Diese Variablen beeinflussen die Überschriftenleiste, die auf einem Mobilgerät oder Geräten mit kleinem Bildschirm, die Bedienfeldtitel und Navigatoren „Weiter“ und „Zurück“ beinhalten, sichtbar ist.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>guide-header-bar</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>headerbar-background-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Kopfzeilenleiste</p> </td>
  </tr>
  <tr>
   <td><p><code>headerbar-font-color</code></p> </td>
   <td><p>Schriftfarbe für den Text in der Kopfzeilenleiste</p> </td>
  </tr>
  <tr>
   <td><p><code>headerbar-padding</code></p> </td>
   <td><p>Auffüllung für die Kopfzeilenleiste</p> </td>
  </tr>
 </tbody>
</table>

## Scroll-Indikator  {#scroll-indicator}

Diese Variablen beeinflussen den Scroll-Indikator, der als orangefarbener Pfeil auf einem Mobilgerät oder auf Geräten mit kleinem Bildschirm angezeigt wird. Der Scroll-Indikator zeigt an, dass es Inhalt gibt, der über den sichtbaren Bereich des Bildschirms hinausgeht. Sie können nach unten blättern, um diesen Inhalt anzuzeigen. Wenn Sie das Ende des Inhalts erreichen, wird der Pfeil nicht mehr angezeigt.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>mobileScrollIndicator</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorBottom</code></p> </td>
   <td><p>Feste Position eines Scroll-Indikators von unten</p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorRight</code></p> </td>
   <td><p>Feste Position eines Scroll-Indikators von rechts</p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorWidth</code></p> </td>
   <td><p>Breite des Scroll-Indikators</p> </td>
  </tr>
  <tr>
   <td><p><code>scrollIndicatorHeight</code></p> </td>
   <td><p>Höhe des Scroll-Indikators</p> </td>
  </tr>
 </tbody>
</table>

## Feste spezifische Variablen für das Symbolleistenlayout für Mobilgeräte  {#mobile-fixed-toolbar-layout-specific-variables}

Diese Variablen in der folgenden Tabelle beeinflussen das feste Symbolleistenlayout für Mobilgeräte.

<table>
 <tbody>
  <tr>
   <td><p><strong>CSS-Klasse </strong></p> </td>
   <td><p><code>mobileToolbar</code></p> </td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarBottom</code></p> </td>
   <td><p>Feste Position der Symbolleiste auf einem Mobilgerät von unten</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarTop</code></p> </td>
   <td><p>Feste Position der Symbolleiste auf einem Mobilgerät von oben</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarLeft</code></p> </td>
   <td><p>Feste Position der Symbolleiste auf einem Mobilgerät von links</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileToolbarRight</code></p> </td>
   <td><p>Feste Position der Symbolleiste auf einem Mobilgerät von rechts</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileButtonIconTopMargin</code></p> </td>
   <td><p>Feste Position der Schaltflächensymbole auf der Symbolleiste von oben</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileButtonIconWidth</code></p> </td>
   <td><p>Die Breite der Schaltflächensymbole auf der Symbolleiste auf einem Mobilgerät</p> </td>
  </tr>
  <tr>
   <td><p><code>mobileButtonIconHeight</code></p> </td>
   <td><p>Höhe der Schaltflächensymbole auf der Symbolleiste auf einem Mobilgerät</p> </td>
  </tr>
  <tr>
   <td><p><code>mobilefixedtoolbarbgcolor</code></p> </td>
   <td><p>Hintergrundfarbe der Symbolleiste auf einem Mobilgerät</p> </td>
  </tr>
 </tbody>
</table>

## Designspezifische Variable  {#theme-specific-variable}

Das **Einfache Einschreibung**-Design unter /etc/clientlibs/fd/af/guidetheme/simpleEnrollment und die Kategorie `guide.theme.simpleEnrollment` führen auch einige Variablen ein. Wenn Sie ein Thema erstellen möchten, das die einfache Registrierung verbessert, können Sie die folgenden &quot;zusätzlichen Variablen verwenden:

<table>
 <tbody>
  <tr>
   <td><p><strong>Variablen </strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>button-focus-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für Schaltfläche im Fokus</p> </td>
  </tr>
  <tr>
   <td><p><code>button-hover-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für Schaltfläche beim Maushover</p> </td>
  </tr>
  <tr>
   <td><p><code>button-radius</code></p> </td>
   <td><p>Radius der Schaltfläche</p> </td>
  </tr>
  <tr>
   <td><p><code>navigation-button-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Navigationsschaltflächen (Zurück/Weiter)</p> </td>
  </tr>
  <tr>
   <td><p><code>navigation-button-bg-hover-color</code></p> </td>
   <td><p>Hintergrundfarbe für die Navigationsschaltflächen (Zurück/Weiter) beim Maushover</p> </td>
  </tr>
  <tr>
   <td><p><code>initial-nav-color</code></p> </td>
   <td><p>Hintergrundfarbe für Assistentennavigatoren und entsprechende Statusleiste beim ersten Rendern </p> </td>
  </tr>
  <tr>
   <td><p><code>active-nav-color</code></p> </td>
   <td>Hintergrundfarbe für aktuellen/aktiven Assistentennavigator und entsprechende Statusleiste </td>
  </tr>
  <tr>
   <td><p><code>visited-nav-color</code></p> </td>
   <td><p>Hintergrundfarbe für Assistentennavigatoren und entsprechende Statusleiste, die verwendet wurden.</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-bifercating-border-color</code></p> </td>
   <td><p>Hintergrundfarbe für sich gabelenden Container in Navigatoren und Bedienfeld</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-navigator-separator-color</code></p> </td>
   <td><p>Untere Rahmenfarbe für Seperatorregisterkarten für Registerkarten links (tabNavigators).</p> </td>
  </tr>
  <tr>
   <td><p><code>tabs-child-nav-bg-color</code></p> </td>
   <td><p>Hintergrundfarbe für Navigatoren mit verschachtelten/untergeordneten/Unter-Navigatoren</p> </td>
  </tr>
 </tbody>
</table>

