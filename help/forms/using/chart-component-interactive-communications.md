---
title: Verwenden von Diagrammen mit interaktiver Kommunikation
seo-title: Chart component in Interactive Communications
description: Mithilfe von Diagrammen in einer interaktiven Kommunikation können Sie große Informationsmengen zu einem einfach zu analysierenden visuellen Format zusammenfassen
seo-description: AEM Forms provides a chart component that you can use to create charts in your Interactive Communication. This document explains basic and agent configurations of the chart component.
uuid: 978aa431-9a5b-4964-b37c-7bfa8c3f49b9
content-type: reference
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e21714ad-d445-4aff-b0db-d577061e0907
docset: aem65
feature: Interactive Communication
exl-id: 0f877a15-a17f-427f-8d89-62ada4d20918
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '2608'
ht-degree: 84%

---

# Verwenden von Diagrammen mit interaktiver Kommunikation{#using-charts-in-interactive-communications}

Ein Diagramm oder Diagramm ist eine visuelle Darstellung von Daten. Sie fasst große Mengen von Informationen in ein leicht verständliches visuelles Format zusammen, sodass die Empfänger der interaktiven Kommunikation komplexe Daten besser visualisieren, interpretieren und analysieren können.

Beim Erstellen einer interaktiven Kommunikation können Sie Diagramme hinzufügen, um zweidimensionale Daten vom Formulardatenmodell der Vorlage für die interaktive Kommunikation visuell darzustellen. Mit der Diagrammkomponente können Sie die folgenden Diagrammtypen hinzufügen und konfigurieren: Kreis, Spalte, Ring, Balken, Linie, Linie und Punkt, Punkt, Bereich und Quadrant.

## Hinzufügen und Konfigurieren eines Diagramms in einer interaktiven Kommunikation {#add-and-configure-chart-in-an-interactive-communication}

Führen Sie die folgenden Schritte aus, um ein Diagramm in einer interaktiven Kommunikation hinzuzufügen und zu konfigurieren:

1. Tippen Sie auf **Komponenten** aus dem Sidekick der interaktiven Kommunikation.
1. Ziehen Sie die **Diagrammkomponente** per Drag-and-Drop auf eine der folgenden Komponenten:

   * Druckkanal: Zielbereich oder Bildfeld
   * Web-Kanal: Bedienfeld oder Zielbereich

1. Tippen Sie auf die Diagrammkomponente im Editor für interaktive Kommunikation und wählen Sie **[!UICONTROL Konfigurieren (]** ![configure_icon](assets/configure_icon.png)) in der Symbolleiste „Komponenten“.

   Die Diagrammeigenschaften werden im linken Bereich angezeigt.

   ![Grundlegende Eigenschaften eines Zeilentypdiagramms im Druckkanal](assets/chart_properties_print_new.png)

   Grundlegende Eigenschaften eines Zeilentypdiagramms im Druckkanal

   ![Grundlegende Eigenschaften eines Zeilentypdiagramms im Webkanal](assets/chart_properties_web_new.png)

   Grundlegende Eigenschaften eines Zeilentypdiagramms im Webkanal

1. Konfigurieren Sie die [Diagrammeigenschaften](../../forms/using/chart-component-interactive-communications.md#configure-chart-properties) basierend auf dem Kanaltyp.
1. (Nur Druckkanal) Legen Sie in den **[!UICONTROL Agenteneinstellungen]** fest, ob der Agent dieses Diagramm verwenden muss. Wenn die Option **[!UICONTROL Obligatorisch für Agenten, dieses Diagramm zu verwenden]** nicht ausgewählt ist, kann der Agent zum Ein- bzw. Ausblenden des Diagramms auf das Augensymbol für das Diagramm auf der Registerkarte **[!UICONTROL Inhalt]** der Benutzeroberfläche für Agenten tippen.

   ![chart_agentproperties](assets/chart_agentproperties.png)

1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Tabelleneigenschaften zu speichern.

   Tippen Sie auf **[!UICONTROL Vorschau]**, um das Erscheinungsbild und die mit der Grafik verknüpften Daten anzuzeigen. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Eigenschaften des Diagramms neu zu konfigurieren.

## Konfigurieren von Diagrammeigenschaften {#configure-chart-properties}

Konfigurieren Sie beim Erstellen von Diagrammen für Druck- und Web-Kanäle die folgenden Eigenschaften:

<table>
 <tbody>
  <tr>
   <td>Feld</td>
   <td>Beschreibung</td>
   <td>Kanaltyp</td>
  </tr>
  <tr>
   <td>Name</td>
   <td>Bezeichner für das Diagrammelement. Der in diesem Feld angegebene Name des Diagramms ist nicht im Diagramm sichtbar. Er wird verwendet, wenn von anderen Komponenten, Skripten und SOM-Ausdrücken auf das Element verwiesen wird.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Diagrammtyp</td>
   <td>Gibt den Diagrammtyp an, den Sie erstellen möchten. Die verfügbaren Optionen sind Torten-, Spalten-, Ring-, Balken-, Linien-, Linien- und Punkt-, Punkt- und Flächendiagramm.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Serie &gt; Multiserie</td>
   <td>Wählen Sie diese Option, um mehrere Serien für die auf der X- und Y-Achse dargestellten Sammlungselemente des Formulardatenmodells hinzuzufügen.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Serie &gt; Datenmodellobjekt</td>
   <td>Name des Sammlungselements des Formulardatenmodells, das dem Diagramm mehrere Serien hinzufügen soll.<br /> Wählen Sie eine übergeordnete Objekteigenschaft des Formulardatenmodells für die Eigenschaften, die auf der X- und Y-Achse dargestellt werden, um eine aussagekräftige Serie zu bilden. Das Datenmodellobjekt, das Sie binden, muss vom Typ Zahl, Zeichenfolge oder Datum sein.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Gestapelt anzeigen</td>
   <td>Auswählen, um die Werte jeder Serie übereinander zu stapeln.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>X-Achse &gt; Titel</td>
   <td>Name für die X-Achse.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>X-Achse &gt; Datenmodellobjekt</td>
   <td><p>Name des Formulardatenmodellsammlungselements, das auf der X-Achse abgetragen werden soll.</p> <p>Wählen Sie zwei Sammlungs-/Array-Typ-Eigenschaften desselben übergeordneten Datenmodellobjekts, die in Bezug zueinander bedeutungsvoll sind, um sie auf der X- und Y-Achse eines Diagramms darzustellen. Das Datenmodellobjekt, das Sie binden, muss vom Typ Zahl, Zeichenfolge oder Datum sein.</p> </td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Y-Achse &gt; Titel</td>
   <td>Name für die Y-Achse. </td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Y-Achse &gt; Datenmodellobjekt</td>
   <td><p>Formulardatenmodellsammlungselement, das auf der Y-Achse abgetragen werden soll. Im Druckkanal muss das Datenmodellobjekt für die Y-Achse vom Typ Zahl sein.</p> <p>Wählen Sie zwei Sammlungs-/Array-Typ-Eigenschaften desselben übergeordneten Datenmodellobjekts, deren Beziehung zueinander bedeutungsvoll ist, um sie auf der X- und Y-Achse eines Diagramms darzustellen. </p> </td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Y-Achse &gt; Funktion</td>
   <td>Statistische/benutzerdefinierte Funktion, die für die Berechnung der Werte auf der Y-Achse zu verwenden ist.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Objekt ausblenden</td>
   <td>Wählen Sie diese Option, um das Diagramm in der endgültigen Ausgabe auszublenden.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Titel des Diagramms. </td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>Höhe</td>
   <td>Höhe des Diagramms in Pixel.</td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>Breite</td>
   <td>Breite des Diagramms in Pixel. Sie können die Breite des Diagramms im Webkanal mithilfe der Stil-Ebene oder durch Anwenden eines Designs steuern.</td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>Obligatorischer Seitenumbruch vor</td>
   <td>Wählen Sie diese Option aus, um vor dem Diagramm einen obligatorischen Seitenumbruch hinzuzufügen und das Diagramm oben auf einer neuen Seite einzufügen. </td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>Obligatorischer Seitenumbruch nach</td>
   <td>Wählen Sie diese Option aus, um vor dem Diagramm einen obligatorischen Seitenumbruch hinzuzufügen und das Diagramm oben auf einer neuen Seite einzufügen. </td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>Einzug</td>
   <td>Einzug des Diagramms links auf der Seite. </td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>QuickInfo</td>
   <td><p>Format, in dem die QuickInfo beim Mouseover auf einem Datenpunkt im Diagramm in Webkanal angezeigt wird. Der Standardwert ist ${x}(${y}). Je nach Diagrammtyp werden die Variablen ${x} und ${y} dynamisch durch die entsprechenden Werte für die X-Achse und Y-Achse ersetzt und in der QuickInfo angezeigt, wenn Sie die Maus über einen Punkt, ein Segment oder einen Balken in der Quickinfo bewegen.</p> <p>Um die QuickInfo zu deaktivieren, lassen Sie die <span class="uicontrol">QuickInfo</code> Feld leer. Diese Option ist nicht auf Linien- und Bereichsdiagramme anwendbar. Beispiel: <a href="#chartoutputprintweb">Beispiel 1: Diagrammausgabe in Druck und Web</a>.</p> </td>
   <td>Web</td>
  </tr>
  <tr>
   <td>Diagrammspezifische Konfigurationen</td>
   <td><p>Neben den allgemeinen Konfigurationen sind die folgenden spezifischen Diagrammkonfiguration verfügbar:</p>
    <ul>
     <li><strong>Legende anzeigen: </strong>Zeigt eine Legende für das Torten- oder Ringdiagramm an, wenn aktiviert.</li>
     <li><strong>Legendenposition: </strong>Legt die Position der Legende in Bezug auf das Diagramm fest. Die verfügbaren Optionen sind rechts, links, oben und unten. Verwenden Sie die rechte Legende im Druckkanal.</li>
     <li><strong>Innerer Radius</strong>: Für Ringdiagramme verfügbar, um den Radius (in Pixeln) für den inneren Kreis des Diagramms anzugeben.</li>
     <li><strong>Linienfarbe</strong>: Verfügbar für Liniendiagramme, Linien- und Punktdiagramme sowie Bereichsdiagramme, um den hexadezimalen Farbwert für die Linie im Diagramm anzugeben.</li>
     <li><strong>Punktfarbe</strong>: Verfügbar für Punktdiagramme sowie Linien- und Punktdiagramme, um den hexadezimalen Farbwert für den Punkt im Diagramm anzugeben.<br /> </li>
     <li><strong>Linienfarbe</strong>: Verfügbar für Bereichsdiagramme, um den hexadezimalen Farbwert für den Bereich unter der Linie im Diagramm anzugeben.</li>
     <li><strong>Referenzpunkt und Bindungstyp: </strong>Verfügbar für Quadrantendiagramme, um<strong> </strong>den Bindungstyp für den Referenzpunkt angeben. Verwenden Sie die statische Text- oder Datenmodellobjekteigenschaft, um den Wert für den Referenzpunkt zu definieren.</li>
     <li><strong>Bezugspunkt &gt; X-Achse: </strong>Verfügbar für Quadrantendiagramme, wenn Sie <span class="uicontrol">Statisch</code> aus der Dropdownliste Bindungstyp , um den X-Achsenwert für den Referenzpunkt anzugeben.</li>
     <li><strong>Bezugspunkt &gt; Y-Achse: </strong>Verfügbar für Quadrantendiagramme, wenn Sie <span class="uicontrol">Statisch</code> aus der Dropdownliste Bindungstyp , um den Wert der Y-Achse für den Referenzpunkt anzugeben.</li>
     <li><strong>Referenzpunkt &gt; Datenmodellobjekt für Serie: </strong>Verfügbar für mehrere Serien-Quadranten-Diagramme, wenn Sie <span class="uicontrol">Datenmodellobjekt</code> aus der Dropdownliste Bindungstyp aus. Definieren Sie die Formulareigenschaft des Formdatenmodells, um die Serie für den Referenzpunkt zu identifizieren. </li>
     <li><strong>Referenzpunkt &gt; Datenmodellobjektwert für Serie: </strong>Verfügbar für mehrere Serien-Quadranten-Diagramme, wenn Sie <span class="uicontrol">Datenmodellobjekt</code> aus der Dropdownliste Bindungstyp aus. Die Eigenschaft des Formulardatenmodellobjekts für Serien und der in diesem Feld angegebene Wert werden verwendet, um die Serie für den Referenzpunkt zu identifizieren.</li>
     <li><strong>Referenz-Punkt &gt; Datenmodellobjekt für Referenzpunkt: </strong>Verfügbar für Quadrantendiagramme, wenn Sie <span class="uicontrol">Datenmodellobjekt</code> aus der Dropdownliste Bindungstyp aus. Definieren Sie eine Objekteigenschaft des Formulardatenmodells, die eine Geschwister-Entität der auf der X-Achse und der Y-Achse dargestellten Eigenschaften darstellt. Definieren Sie für mehrere Serien außerdem eine Datenmodellobjekteigenschaft, die eine untergeordnete Entität der für die Serie definierten Datenmodellobjekteigenschaft ist.</li>
     <li><strong>Reference Point &gt; Data Model Object Value for Reference Point: </strong>Verfügbar für Quadrantendiagramme, wenn Sie <span class="uicontrol">Datenmodellobjekt</code> aus der Dropdownliste Bindungstyp aus. Verwenden Sie die Objekteigenschaft des Formulardatenmodells für den Referenzpunkt und den in diesem Feld definierten Wert, um den Referenzpunkt für das Diagramm zu identifizieren.<br /> <strong>Quadrantenbeschriftungen &gt; Oben links</strong>: Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten oben links anzugeben.</li>
     <li><strong>Quadrantenbeschriftungen &gt; Oben rechts</strong>: Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten oben rechts anzugeben.</li>
     <li><strong>Quadranten Beschriftungen &gt; Unten rechts: </strong>Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten unten rechts anzugeben.</li>
     <li><strong>Quadranten Beschriftungen &gt; Unten links: </strong>Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten unten links anzugeben.</li>
    </ul> </td>
   <td>Druck und Web</td>
  </tr>
 </tbody>
</table>

## Funktionen im Diagramm verwenden {#use-functions-in-chart}

Sie können ein Diagramm so konfigurieren, dass es mithilfe statistischer Funktionen Werte aus den Quelldaten für die Darstellung im Diagramm berechnet. Durch Anwenden von Funktionen in einem Diagramm können Sie Daten grafisch darstellen, die nicht direkt vom Formulardatenmodell bereitgestellt werden.

![Funktionen in Diagrammen](assets/functions_charts_new.png)

Auch wenn die Diagrammkomponente mit einigen eingebauten Funktionen ausgestattet ist, können Sie [eigene Funktionen](#customfunctionsweb) schreiben und sie für die Verwendung in der Diagrammkonfiguration im Web-Kanal verfügbar machen.

Die folgenden Funktionen sind standardmäßig in der Diagrammkomponente verfügbar:

**Mittelwert (Durchschnitt)** Gibt den Durchschnitt der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Summe** Gibt die Summe aller Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Maximum** Gibt das Maximum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Häufigkeit** Gibt die Anzahl der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Bereich** Gibt die Differenz zwischen dem Maximum und dem Minimum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Median** Gibt den Wert zurück, der höhere und niedrigere Werte auf der X- oder Y-Achse bei einem bestimmten Wert auf der anderen Achse in der Mitte trennt.

**Minimum** Gibt das Minimum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**Modus** Gibt den Wert mit den meisten Vorkommnissen auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

Weitere Informationen finden Sie in [Beispiel 2: Anwendung von Summen- und Häufigkeitsfunktionen in einem Liniendiagramm](#applicationsumfrequency).

### Benutzerdefinierte Funktionen im Web-Kanal {#customfunctionsweb}

Neben den Standardfunktionen in Diagrammen können Sie auch benutzerdefinierte Funktionen in JavaScript™ schreiben und in der Funktionsliste der Diagrammkomponente für den Webkanal verfügbar machen.

Eine Funktion akzeptiert ein Array oder Werte und einen Kategorienamen als Eingaben und gibt einen Wert zurück. Beispiel:

```javascript
Multiply(valueArray, category) {
 var val = 1;
 _.each(valueArray, function(value) {
 val = val * value;
 });
 return val;
}
```

Nachdem Sie eine benutzerdefinierte Funktion geschrieben haben, führen Sie die folgenden Schritte aus, um sie für die Verwendung in der Diagrammkonfiguration verfügbar zu machen:

1. Fügen Sie die benutzerdefinierte Funktion in der Client-Bibliothek hinzu, die mit der relevanten interaktiven Kommunikation verknüpft ist. Weitere Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md) und [Verwenden von Client-seitigen Bibliotheken](/help/sites-developing/clientlibs.md).

1. Um die benutzerdefinierte Funktion in der Dropdownliste „Funktion“ anzuzeigen, erstellen Sie in CRXDe Lite einen `nt:unstructured`-Knoten im Apps-Ordener mit den folgenden Eigenschaften:

   * Fügen Sie die Eigenschaft `guideComponentType` mit einem Wert wie `fd/af/reducer` hinzu. (mandatory)

   * Fügen Sie die Eigenschaft `value` zu einem vollständig qualifizierten Namen der benutzerdefinierten JavaScript™-Funktion hinzu. (obligatorisch) und setzen Sie den Wert auf den Namen der benutzerdefinierten Funktion, z. B. Multiplizieren, fest.
   * Fügen Sie die Eigenschaft `jcr:description` mit dem Wert hinzu, den Sie als Name der benutzerdefinierten Funktion anzeigen möchten, die in der Dropdown-Liste „Funktion“ angezeigt wird. Beispiel:**Multiplizieren**. 

   * Fügen Sie die Eigenschaft `qtip` mit einem Wert hinzu, der eine kurze Beschreibung der benutzerdefinierten Funktion darstellt. Es wird als QuickInfo angezeigt, wenn der Mauszeiger über den Funktionsnamen in der Dropdown-Liste **Funktion** bewegt wird.

1. Klicks **Alle speichern** , um die Konfiguration zu speichern.

Die Funktion ist jetzt für die Verwendung im Diagramm verfügbar.

## Beispiel 1: Diagrammausgabe in Druck und Web {#chartoutputprintweb}

Auf der Registerkarte „Grundeinstellungen“ definieren Sie die Art des Diagramms, die Quellformulardatenmodelleigenschaften, die Daten enthalten, sowie die Beschriftungen, die auf der X-Achse und Y-Achse des Diagramms dargestellt werden können. Optional definieren Sie hier auch die statistische Funktion, um die Werte für die grafische Darstellung auf dem Diagramm zu berechnen.

Im Folgenden wird das Minimum der erfoderlichen Informationen in den Grundeinstellungen anhand des Beispiels einer Kreditkartenabrechnung, die mit einer interaktiven Kommunikation erstellt wurde, detailliert erläutert. Angenommen, Sie möchten ein Diagramm erstellen, in dem die Höhe der verschiedenen Ausgaben in der Anweisung dargestellt wird. Sie möchten verschiedene Arten von Diagrammen für die Druck- und Webausgabe der interaktiven Kommunikation verwenden.

### Säulendiagramm zum Ausdrucken {#columnchartprint}

Um dies zu erreichen, geben Sie die folgenden Eigenschaften an:

* **[!UICONTROL Name]** - Geben Sie den Namen für das Diagramm an.
* **[!UICONTROL Diagrammtyp]** - Wählen Sie **Säulen** aus der Dropdown-Liste aus.
* **[!UICONTROL Titel]** - Geben Sie für die X-Achse „Art der Ausgabe“ und für die Y-Achse „Transaktionsbetrag“ an.
* **[!UICONTROL Datenmodellobjekte]** - Wählen Sie die Eigenschaften der Datenmodellobjekte aus, um Datenbindungen für die X-Achse (Art der Ausgabe) und die Y-Achse (Transaktionsbetrag) zu erstellen.

![Säulendiagramm in der Druckausgabe einer interaktiven Kommunikation](assets/sample_chart_print_column_new.png)

Säulendiagramm in der Druckausgabe einer interaktiven Kommunikation

### Ringdiagramm für Webausgabe {#donutchartweb}

Um dies zu erreichen, geben Sie die folgenden Eigenschaften an:

* **[!UICONTROL Name]** - Geben Sie den Namen für das Diagramm an.
* **[!UICONTROL Diagrammtyp]** - Wählen Sie **[!UICONTROL Ring]** aus der Dropdown-Liste aus.
* **[!UICONTROL Datenmodellobjekte]** - Wählen Sie die Eigenschaften der Datenmodellobjekte aus, um Datenbindungen für die X-Achse (Art der Ausgabe) und die Y-Achse (Transaktionsbetrag) zu erstellen.
* **[!UICONTROL Innerer Radius]** - Geben Sie 150 als Wert für den inneren Radius an, um den Radius (in Pixel) des inneren Kreises des Diagramms festzulegen.
* **[!UICONTROL QuickInfo]** - Verwenden Sie das Standardformat ${x}(${y}) zur Anzeige der QuickInfo. Die QuickInfo wird wie folgt angezeigt: Art der Ausgabe (Transaktionsbetrag). Beispiel: Debit für Bitcoin (10000).

![Ringdiagramm in der Webausgabe einer interaktiven Kommunikation](assets/sample_chart_web_new.png)

Ringdiagramm in der Webausgabe einer interaktiven Kommunikation

## Beispiel 2: Anwendung von Summen- und Häufigkeitsfunktionen in einem Liniendiagramm {#applicationsumfrequency}

Durch Anwenden von Funktionen in einem Diagramm können Sie Daten darstellen, die nicht direkt vom Formulardatenmodell bereitgestellt werden. In diesem Beispiel verwenden wir ein Kreditkartenabrechnungsbeispiel, um zu verstehen, wie Summen- und Häufigkeitsfunktionen auf das Diagramm angewendet werden können.

![Liniendiagramm ohne Funktion mit zwei „Debit für AirBnB“-Transaktionen](assets/line_chart_web_new.png)

Liniendiagramm ohne Funktion mit zwei „Debit für AirBnB“-Transaktionen

### Sum-Funktion {#sum-function}

Sie können die Funktion sum anwenden, um Werte mehrerer Instanzen derselben Dateneigenschaft hinzuzufügen und sie nur einmal anzuzeigen. Im folgenden Diagramm wird zum Beispiel die Summenfunktion auf die Y-Achse angewendet, um die Summe der drei „Debit für AirBnB“-Transaktionen (2050 und 1050) zu addieren und nur eine Transaktion (3100) anzuzeigen.

Die Summenfunktion kann Diagramme nützlicher machen, wenn Sie die Summe für viele Instanzen derselben Dateneigenschaft sortieren und anzeigen möchten.

![Liniendiagrammsumme](assets/line_chart_web_sum_new.png)

### Häufigkeitsfunktion {#frequency-function}

Die Häufigkeitsfunktion gibt die Anzahl der Werte auf der X-Achse für einen bestimmten Wert auf der anderen Achse an. Bei Anwendung der Häufigkeitsfunktion auf der Y-Achse (Transaktionsbetrag) zeigt das Diagramm an, dass zwei „Debit für AirBnB“-Transaktionen und der Rest der Transaktionsarten einmal aufgetreten sind.

![Liniendiagrammhäufigkeit](assets/line_chart_web_functions_frequency_new.png)

## Beispiel 3: Mehrreihen-Quadrantendiagramm in der Webausgabe {#example-multi-series-quadrant-chart-in-web}

Das Diagramm zeigt den Betrag für die Transaktionen, die in einem bestimmten Datumsbereich durchgeführt wurden. Das Quadrantendiagramm bietet die Möglichkeit, den Diagrammbereich in vier beschriftete Abschnitte zu unterteilen. Das Diagramm verwendet einen statischen Bezugspunkt für die X- und Y-Achse. Verwenden Sie die Funktion der mehreren Reihen, um Daten auf Grundlage des Namens der Bank zu sortieren.

Um dies zu erreichen, geben Sie die folgenden Eigenschaften an:

* **Name:** Geben Sie den Namen für das Diagramm an.
* **Diagrammtyp:** Wählen Sie **Quadrant** aus der Dropdown-Liste aus.

* Aktivieren Sie das Kontrollkästchen **Mehrere Reihen**.
* **Datenmodellobjekt**: Geben Sie die Datenmodellobjekteigenschaft für die Reihe an. Die Datenmodellobjekteigenschaft für den Namen der Bank ist ein übergeordnetes Element der Datenmodellobjekteigenschaften, die in der X- und Y-Achse dargestellt werden.
* **Datenmodellobjekte:** Wählen Sie die Eigenschaften der Datenmodellobjekte aus, um Datenbindungen für die X-Achse (Transaktionsdatum) und die Y-Achse (Transaktionsbetrag) zu erstellen.
* Im Abschnitt **Referenzpunkt** wählen Sie **Statisch** als Bindungstyp.

* Geben Sie die Werte für die Referenzpunkte der X- und Y-Achse an.
* Geben Sie die Beschriftungen für die Quadranten oben links, oben rechts, unten rechts und unten links an.
* Aktivieren Sie das Kontrollkästchen **Legenden anzeigen**, um die Farbcodes für die Banknamen anzuzeigen.

![Quadrantendiagramme](assets/charts_quadrant_example_new.png)
