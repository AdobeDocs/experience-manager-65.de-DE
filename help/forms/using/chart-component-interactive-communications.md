---
title: Verwenden von Diagrammen mit interaktiver Kommunikation
seo-title: Diagrammkomponente in interaktiver Kommunikation
description: Mithilfe von Diagrammen in einer interaktiven Kommunikation können Sie große Mengen von Informationen zu einem einfach zu analysierenden visuellen Format zusammenfassen.
seo-description: AEM Forms bietet eine Diagrammkomponente, die Sie verwenden können, um Diagramme in Ihrer interaktiven Kommunikation zu erstellen. In diesem Dokument werden die grundlegenden und Agentenkonfigurationen der Diagrammkomponente erläutert.
uuid: 978aa431-9a5b-4964-b37c-7bfa8c3f49b9
content-type: reference
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e21714ad-d445-4aff-b0db-d577061e0907
docset: aem65
feature: Interactive Communication
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2648'
ht-degree: 25%

---


# Verwenden von Diagrammen mit interaktiver Kommunikation{#using-charts-in-interactive-communications}

Ein Diagramm ist eine visuelle Darstellung von Daten. Es verdichtet große Mengen an Informationen in ein leicht verständliches visuelles Format, sodass die Empfänger der interaktiven Kommunikation komplexe Daten besser visualisieren, interpretieren und analysieren können.

Beim Erstellen einer interaktiven Kommunikation können Sie Diagramme hinzufügen, um zweidimensionale Daten vom Formulardatenmodell der Vorlage für die interaktive Kommunikation visuell darzustellen. Mit der Diagrammkomponente können Sie die folgenden Diagrammtypen hinzufügen und konfigurieren: Torten, Spalten, Donut, Balken, Linie, Linie und Punkt, Punkt, Bereich und Quadrant.

## hinzufügen und Konfigurieren von Diagrammen in einer interaktiven Kommunikation{#add-and-configure-chart-in-an-interactive-communication}

Führen Sie die folgenden Schritte aus, um ein Diagramm in einer interaktiven Kommunikation hinzuzufügen und zu konfigurieren:

1. Tippen Sie im Sidekick der interaktiven Kommunikation auf **Komponenten**.
1. Ziehen Sie die Komponente **Diagramm** auf eine der folgenden Komponenten:

   * Kanal drucken: Zielgruppen- oder Bildfeld
   * Web-Kanal: Bereich oder Zielgruppe

1. Tippen Sie auf die Diagrammkomponente im Editor für interaktive Kommunikation und wählen Sie **[!UICONTROL Konfigurieren (]** ![configure_icon](assets/configure_icon.png)) in der Komponenten-Symbolleiste.

   Die Diagrammeigenschaften werden im linken Bereich angezeigt.

   ![Grundlegende Eigenschaften eines Zeilentypdiagramms im Druckkanal](assets/chart_properties_print_new.png)

   Grundlegende Eigenschaften eines Zeilentypdiagramms im Druckkanal

   ![Grundlegende Eigenschaften eines Zeilentypdiagramms im Webkanal](assets/chart_properties_web_new.png)

   Grundlegende Eigenschaften eines Zeilentypdiagramms im Webkanal

1. Konfigurieren Sie die Diagrammeigenschaften [je nach Kanal-Typ.](../../forms/using/chart-component-interactive-communications.md#configure-chart-properties)
1. (Nur Kanal drucken) Geben Sie unter **[!UICONTROL Agenteneinstellungen]** an, ob dieses Diagramm vom Agenten verwendet werden muss. Wenn die Option &quot;i **[!UICONTROL t ist obligatorisch, damit der Agent dieses Diagramm verwenden kann]**&quot;nicht ausgewählt ist, kann der Agent auf das Augensymbol für das Diagramm auf der Registerkarte **[!UICONTROL Inhalt]** der Agent-Benutzeroberfläche tippen, um das Diagramm ein- oder auszublenden.

   ![chart_agentproperties](assets/chart_agentproperties.png)

1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Diagrammeigenschaften zu speichern.

   Tippen Sie auf **[!UICONTROL Vorschau]**, um das Erscheinungsbild und die mit dem Diagramm verknüpften Daten Ansicht. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Eigenschaften des Diagramms neu zu konfigurieren.

## Diagrammeigenschaften {#configure-chart-properties} konfigurieren

Konfigurieren Sie beim Erstellen von Diagrammen für Druck- und Web-Kanal die folgenden Eigenschaften:

<table>
 <tbody>
  <tr>
   <td>Feld</td>
   <td>Beschreibung</td>
   <td>Kanaltyp</td>
  </tr>
  <tr>
   <td>Name</td>
   <td>Bezeichner für das Diagrammelement. Der Name des in diesem Feld angegebenen Diagramms ist im Diagramm nicht sichtbar. Es wird verwendet, wenn auf das Element von anderen Komponenten, Skripten und SOM-Ausdrücken verwiesen wird.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Diagrammtyp</td>
   <td>Diagrammtyp, den Sie erstellen möchten. Die verfügbaren Optionen sind Tortendiagramm, Spalte, Donut, Balken, Linie, Linie und Punkt, Punkt und Bereich.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Serie &gt; Mehrere Reihen</td>
   <td>Wählen Sie diese Option, um mehrere Serien für die auf der X- und Y-Achse dargestellten Sammlungselemente des Formulardatenmodells hinzuzufügen.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Serie &gt; Datenmodellobjekt</td>
   <td>Name des Collection-Elements des Formulardatenmodells, das dem Diagramm mehrere Reihen hinzufügen soll.<br /> Wählen Sie eine Objekteigenschaft des übergeordneten Formulardatenmodells für die Eigenschaften, die auf der X- und Y-Achse dargestellt werden, um eine aussagekräftige Reihe zu bilden. Das Datenmodellobjekt, das Sie binden, muss vom Typ "Number", "String"oder "Date"sein.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Gestapelt anzeigen</td>
   <td>Auswählen, um die Werte jeder Serie übereinander zu stapeln.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>X-Achse &gt; Titel</td>
   <td>Titel für die X-Achse.</td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>X-Achse &gt; Datenmodellobjekt</td>
   <td><p>Name des auf der X-Achse abzubildenden Collection-Elements des Formulardatenmodells.</p> <p>Wählen Sie zwei Eigenschaften für den Sammlungs-/Array-Typ des gleichen übergeordneten Datenmodellobjekts aus, die im Verhältnis zueinander aussagekräftig sind, um sie auf der X- und Y-Achse eines Diagramms darzustellen. Das Datenmodellobjekt, das Sie binden, muss vom Typ "Number", "String"oder "Date"sein.</p> </td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Y-Achse &gt; Titel</td>
   <td>Titel für die Y-Achse. </td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Y-Achse &gt; Datenmodellobjekt</td>
   <td><p>Auf der Y-Achse aufzuzeichnendes Element des Formulardatenmodells. Im Kanal "Drucken"sollte das Datenmodellobjekt für die Y-Achse vom Typ "Zahl"sein.</p> <p>Wählen Sie zwei Eigenschaften für den Sammlungs-/Array-Typ des gleichen übergeordneten Datenmodellobjekts aus, die im Verhältnis zueinander aussagekräftig sind, um sie auf der X- und Y-Achse eines Diagramms darzustellen. </p> </td>
   <td>Druck und Web</td>
  </tr>
  <tr>
   <td>Y-Achse &gt; Funktion</td>
   <td>Statistische/benutzerdefinierte Funktion zur Berechnung der Werte auf der y-Achse.</td>
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
   <td>Einzug des Diagramms von links auf der Seite. </td>
   <td>Druck</td>
  </tr>
  <tr>
   <td>QuickInfo</td>
   <td><p>Format, in dem die QuickInfo auf einem Datenpunkt im Diagramm im Web Kanal angezeigt wird. Der Standardwert ist ${x}(${y}). Je nach Diagrammtyp werden die Variablen ${x}und ${y} dynamisch durch die entsprechenden Werte auf der X- und Y-Achse ersetzt und in der QuickInfo angezeigt, wenn Sie mit der Maus auf einen Punkt, eine Leiste oder ein Segment im Diagramm zeigen.</p> <p>Um die QuickInfo zu deaktivieren, lassen Sie das Feld <span class="uicontrol">QuickInfo</code> leer. Diese Option ist nicht auf Linien- und Bereichsdiagramme anwendbar. Beispiel: Diagrammausgabe in Druck und Web</a>.<a href="#chartoutputprintweb"></a></p> </td>
   <td>Web</td>
  </tr>
  <tr>
   <td>Diagrammspezifische Konfigurationen</td>
   <td><p>Neben den allgemeinen Konfigurationen sind die folgenden spezifischen Diagrammkonfiguration verfügbar:</p>
    <ul>
     <li><strong>Legende anzeigen:  </strong>Zeigt eine Legende für das Kreisdiagramm oder Ringdiagramm an, wenn diese aktiviert ist.</li>
     <li><strong>Legendenposition:  </strong>Gibt die Position der Legende in Bezug auf das Diagramm an. Die verfügbaren Optionen sind rechts, links, oben und unten. Es wird empfohlen, die rechte Legende im Kanal zu verwenden.</li>
     <li><strong>Innerer Radius</strong>: Verfügbar für Ringdiagramme, um den Radius (in Pixel) des inneren Kreises im Diagramm anzugeben.</li>
     <li><strong>Linienfarbe</strong>: Verfügbar für Linien-, Linien- und Punktdiagramme sowie Flächendiagramme, um die Farbe für die Linie im Diagramm anzugeben.</li>
     <li><strong>Punktfarbe</strong>: Verfügbar für Punkt- und Linien- und Punktdiagramme, um die Farbe für die Punkte im Diagramm anzugeben.<br /> </li>
     <li><strong>Bereichsfarbe</strong>: Verfügbar für Flächendiagramme, um die Farbe für den Bereich unter der Linie im Diagramm anzugeben.</li>
     <li><strong>Referenzpunkt &gt; Bindungstyp:  </strong>Verfügbar für Quadrantendiagramme <strong> </strong>zur Angabe des Bindungstyps für den Referenzpunkt. Verwenden Sie die Objekteigenschaft für statischen Text oder Datenmodell, um den Wert für den Referenzpunkt zu definieren.</li>
     <li><strong>Bezugspunkt &gt; X-Achse:  </strong>Verfügbar für Quadrantendiagramme, wenn Sie in der Dropdown-Liste "Bindungstyp"die Option " <span class="uicontrol"></code> Statikmethode"wählen, um den X-Achsen-Wert für den Referenzpunkt anzugeben.</code></li>
     <li><strong>Bezugspunkt &gt; Y-Achse:  </strong>Verfügbar für Quadrantendiagramme, wenn Sie in der Dropdown-Liste "Bindungstyp"die Option " <span class="uicontrol"></code> Statikmethode"wählen, um den Y-Achsenwert für den Referenzpunkt anzugeben.</code></li>
     <li><strong>Referenzpunkt &gt; Datenmodellobjekt für Serie:  </strong>Verfügbar für mehrere Reihen Quadrante Diagramme, wenn Sie in der Dropdown-Liste "Bindungstyp"die Option " <span class="uicontrol">Datenmodellobjekt"</code> auswählen. Definieren Sie die Formulareigenschaft des Formdatenmodells, um die Serie für den Referenzpunkt zu identifizieren. </code></li>
     <li><strong>Referenzpunkt &gt; Datenmodellobjektwert für Serie:  </strong>Verfügbar für mehrere Reihen Quadrante Diagramme, wenn Sie in der Dropdown-Liste "Bindungstyp"die Option " <span class="uicontrol">Datenmodellobjekt"</code> auswählen. Verwenden Sie die Objekteigenschaft des Formulardatenmodells für Reihen und den in diesem Feld definierten Wert, um die Reihe für den Referenzpunkt zu identifizieren.</code></li>
     <li><strong>Referenzpunkt &gt; Datenmodellobjekt für Referenzpunkt:  </strong>Verfügbar für Quadrantendiagramme, wenn Sie in der Dropdown-Liste "Bindungstyp"die Option " <span class="uicontrol">Datenmodellobjekt"</code> auswählen. Definieren Sie eine Objekteigenschaft des Formulardatenmodells, die den auf der X- und Y-Achse dargestellten Eigenschaften gleicht. Definieren Sie außerdem für mehrere Reihen eine Datenmodellobjekteigenschaft, die eine untergeordnete Entität der für die Serie definierten Datenmodellobjekteigenschaft ist.</code></li>
     <li><strong>Referenzpunkt &gt; Datenmodellobjektwert für Referenzpunkt:  </strong>Verfügbar für Quadrantendiagramme, wenn Sie in der Dropdown-Liste "Bindungstyp"die Option " <span class="uicontrol">Datenmodellobjekt"</code> auswählen. Verwenden Sie die Objekteigenschaft des Formulardatenmodells für den Referenzpunkt und den in diesem Feld definierten Wert, um den Referenzpunkt für das Diagramm zu identifizieren.<br /> <strong>Quadrante Beschriftungen &gt; Oben links: </strong> Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten links oben anzugeben.</code></li>
     <li><strong>Quadrante Beschriftungen &gt; Oben rechts: </strong> Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten rechts oben anzugeben.</li>
     <li><strong>Quadrante Beschriftungen &gt; Unten rechts:  </strong>Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten unten rechts anzugeben.</li>
     <li><strong>Quadrante Beschriftungen &gt; Unten links:  </strong>Verfügbar für Quadrantendiagramme, um den Namen für den Quadranten unten links anzugeben.</li>
    </ul> </td>
   <td>Druck und Web</td>
  </tr>
 </tbody>
</table>

## Funktionen im Diagramm verwenden {#use-functions-in-chart}

Sie können das Diagramm so konfigurieren, dass Sie mit statistischen Funktionen Werte aus Quelldaten zur grafischen Darstellung im Diagramm berechnen können. Durch Anwenden von Funktionen in einem Diagramm können Sie Daten darstellen, die nicht direkt vom Formulardatenmodell bereitgestellt werden.

![Funktionen in Diagrammen](assets/functions_charts_new.png)

Die Diagrammkomponente enthält zwar einige integrierte Funktionen, Sie können aber [benutzerdefinierte Funktionen](#customfunctionsweb) schreiben und sie für die Verwendung in der Diagrammkonfiguration im Web Kanal verfügbar machen.

Die folgenden Funktionen sind standardmäßig in der Diagrammkomponente verfügbar:

**Mittelwert (Durchschnitt)** Gibt den Durchschnitt der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**** SumGibt die Summe aller Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**** MaximumGibt das Maximum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**** FrequencyGibt die Anzahl der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**** RangeGibt die Differenz zwischen dem Maximum und Minimum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**** MedianGibt den Wert zurück, der auf der X- oder Y-Achse höhere und niedrigere Werte auf der anderen Achse halbiert.

**** MinimumGibt das Minimum der Werte auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

**** ModeGibt den Wert mit den meisten Vorkommen auf der X- oder Y-Achse für einen bestimmten Wert auf der anderen Achse zurück.

Weitere Informationen finden Sie unter [Beispiel 2: Anwendung von Summe- und Frequenzfunktionen in einem Liniendiagramm](#applicationsumfrequency).

### Benutzerdefinierte Funktionen im Web-Kanal {#customfunctionsweb}

Neben der Verwendung der Standardfunktionen in Diagrammen können Sie benutzerdefinierte Funktionen in JavaScript™ schreiben und in der Liste der Funktionen in der Diagrammkomponente freigeben.

Eine Funktion akzeptiert ein Array oder Werte und einen Kategorienamen als Eingabe und gibt einen Wert zurück. Beispiel:

```javascript
Multiply(valueArray, category) {
 var val = 1;
 _.each(valueArray, function(value) {
 val = val * value;
 });
 return val;
}
```

Wenn Sie eine benutzerdefinierte Funktion geschrieben haben, können Sie die folgenden Schritte ausführen, um sie für die Verwendung in der Diagrammkonfiguration freizugeben:

1. Fügen Sie die benutzerdefinierte Funktion in der Client-Bibliothek hinzu, die mit der entsprechenden interaktiven Kommunikation verknüpft ist. Weitere Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md) und [Verwenden clientseitiger Bibliotheken](/help/sites-developing/clientlibs.md).

1. Um die benutzerdefinierte Funktion in der Dropdown-Liste Funktion anzuzeigen, erstellen Sie in CRXDe Lite einen Knoten `nt:unstructured` im Anwendungsordner mit den folgenden Eigenschaften:

   * hinzufügen Eigenschaft `guideComponentType` mit dem Wert `fd/af/reducer`. (mandatory)

   * hinzufügen Eigenschaft `value` auf einen vollständig qualifizierten Namen der benutzerdefinierten JavaScript™-Funktion. (obligatorisch) und setzen Sie den Wert auf den Namen der benutzerdefinierten Funktion, z. B. Multiplizieren, fest.
   * hinzufügen Eigenschaft `jcr:description` mit dem Wert, der als Name der benutzerdefinierten Funktion angezeigt werden soll, der in der Dropdown-Liste Funktion angezeigt wird. Beispiel:**Multiplizieren**. 

   * hinzufügen Eigenschaft `qtip` mit einem Wert, der eine kurze Beschreibung der benutzerdefinierten Funktion enthält. Es wird als QuickInfo angezeigt, wenn der Mauszeiger über den Funktionsnamen in der Dropdown-Liste **Funktion** bewegt wird.

1. Klicken Sie auf **Alle speichern**, um die Konfiguration zu speichern.

Die Funktion steht nun zur Verwendung im Diagramm zur Verfügung.

## Beispiel 1: Diagrammausgabe in Druck und Web {#chartoutputprintweb}

Auf der Registerkarte Einfach definieren Sie den Diagrammtyp, die Eigenschaften des Quellformulardaten-Modells, die Daten enthalten, die Beschriftungen, die auf der X- und Y-Achse des Diagramms dargestellt werden sollen, und optional die statistische Funktion, um die Werte für die Darstellung im Diagramm zu berechnen.

Anhand eines Kartenausweises, der mithilfe einer interaktiven Kommunikation generiert wurde, sollten wir uns ausführlich mit den erforderlichen Informationen in den grundlegenden Eigenschaften auskennen. Wenn Sie ein Diagramm generieren möchten, um die Höhe der verschiedenen Ausgaben in der Abrechnung darzustellen. Sie können verschiedene Diagrammarten für Druck- und Webausgabe der interaktiven Kommunikation verwenden.

### Säulendiagramm für Drucken {#columnchartprint}

Geben Sie dazu die folgenden Eigenschaften an:

* **[!UICONTROL Name]** : Geben Sie den Namen für das Diagramm an.
* **[!UICONTROL Diagrammtyp]** : Wählen Sie  **** Spalten aus der Dropdown-Liste aus.
* **[!UICONTROL Titel]** : Geben Sie den Ausgabentyp für die X-Achse und den Transaktionsbetrag für die Y-Achse an.
* **[!UICONTROL Datenmodellobjekte]** : Wählen Sie die Objekteigenschaften des Datenmodells aus, um Datenbindungen für die X-Achse (Ausgabetyp) und die Y-Achse (Transaktionsbetrag) zu erstellen.

![Spaltendiagramm im Kanal &quot;Drucken&quot;einer interaktiven Kommunikation](assets/sample_chart_print_column_new.png)

Spaltendiagramm im Kanal &quot;Drucken&quot;einer interaktiven Kommunikation

### Ringdiagramm für Web {#donutchartweb}

Geben Sie dazu die folgenden Eigenschaften an:

* **[!UICONTROL Name]** : Geben Sie den Namen für das Diagramm an.
* **[!UICONTROL Diagrammtyp]** : Wählen Sie in der Dropdown-Liste  **** Donutt aus.
* **[!UICONTROL Datenmodellobjekte]** : Wählen Sie die Objekteigenschaften des Datenmodells aus, um Datenbindungen für die X-Achse (Ausgabetyp) und die Y-Achse (Transaktionsbetrag) zu erstellen.
* **[!UICONTROL Innerer Radius]** : Geben Sie den Wert &quot;Innerer Radius&quot;als 150 an, um den Radius (in Pixel) des inneren Kreises im Diagramm anzugeben.
* **[!UICONTROL QuickInfo]**  - Verwenden Sie das Standardformat ${x}(${y}), um die QuickInfo anzuzeigen. Die QuickInfo wird wie folgt angezeigt: Ausgabentyp(Transaktionsbetrag). Beispiel: Debit for Bitcoin(10000).

![Ringdiagramm im Web-Kanal einer interaktiven Kommunikation](assets/sample_chart_web_new.png)

Ringdiagramm im Web-Kanal einer interaktiven Kommunikation

## Beispiel 2: Anwendung von Summen- und Häufigkeitsfunktionen in einem Liniendiagramm {#applicationsumfrequency}

Durch Anwenden von Funktionen in einem Diagramm können Sie Daten darstellen, die nicht direkt vom Formulardatenmodell bereitgestellt werden. In diesem Beispiel verwenden wir ein Beispiel für einen Kreditkartenauszug, um zu verstehen, wie Summen- und Häufigkeitsfunktionen auf das Diagramm angewendet werden können.

![Liniendiagramm ohne Funktion mit zwei &quot;Debit for AirBnB&quot;-Transaktionen](assets/line_chart_web_new.png)

Liniendiagramm ohne Funktion mit zwei &quot;Debit for AirBnB&quot;-Transaktionen

### Summenfunktion {#sum-function}

Sie können die Summenfunktion anwenden, um Werte mehrerer Instanzen derselben Dateneigenschaft zusammenzufassen, und sie nur einmal anzeigen. Im folgenden Diagramm wird beispielsweise die Funktion Summe auf der Y-Achse angewendet, um den Betrag der beiden Debit-Vorgänge für AirBnB (2050 und 1050) hinzuzufügen und nur eine Transaktion (3100) anzuzeigen.

Die Summenfunktion kann Diagramme nützlicher machen, wenn Sie die Summe für viele Instanzen derselben Dateneigenschaft sortieren und anzeigen möchten.

![Liniendiagrammsumme](assets/line_chart_web_sum_new.png)

### Häufigkeitsfunktion {#frequency-function}

Die Funktion Frequenz gibt die Anzahl der Werte der Y-Achse für einen bestimmten Wert auf der anderen Achse zurück. Mit der Anwendung der Funktion Häufigkeit auf der Y-Achse (Transaktionsbetrag) zeigt das Diagramm an, dass es zwei Vorfälle von Debit für AirBnB-Transaktionen und ein Vorkommen der übrigen Arten von Transaktionen gab.

![Liniendiagrammfrequenz](assets/line_chart_web_functions_frequency_new.png)

## Beispiel 3: Quadrantendiagramm mit mehreren Reihen im Web {#example-multi-series-quadrant-chart-in-web}

Das Diagramm zeigt den Betrag für Transaktionen in einem bestimmten Datumsbereich an. Das Quadrantendiagramm bietet die Möglichkeit, den Diagrammbereich in vier beschriftete Abschnitte zu unterteilen. Das Zeichen verwendet einen statischen Bezugspunkt für die X- und Y-Achse. Verwenden Sie die Funktion für mehrere Reihen, um Daten basierend auf dem Namen der Bank zu trennen.

Geben Sie dazu die folgenden Eigenschaften an:

* **Name:** Geben Sie den Namen für das Diagramm an.
* **Diagrammtyp:** Wählen Sie  **** Quadrantaus der Dropdown-Liste.

* Aktivieren Sie das Kontrollkästchen **Mehrere Reihen**.
* **Datenmodellobjekt**: Geben Sie die Datenmodell-Objekteigenschaft für die Serie an. Die Datenmodell-Objekteigenschaft für den Banknamen ist eine übergeordnete Eigenschaft der Datenmodellobjekteigenschaften, die in der X- und Y-Achse dargestellt werden.
* **Datenmodellobjekte:** Wählen Sie die Datenmodellobjekteigenschaften aus, um Datenbindungen für die X-Achse (Transaktionsdatum) und die Y-Achse (Transaktionsbetrag) zu erstellen.
* Wählen Sie im Abschnitt **Referenzpunkt** **Statisch** als Bindungstyp.

* Geben Sie die Werte für die Referenzpunkte der X- und Y-Achse an.
* Geben Sie die quadranten Beschriftungen für Quadranten oben links, oben rechts, unten rechts und unten links an.
* Aktivieren Sie das Kontrollkästchen **Legenden anzeigen**, um die Farbcodes für die Namen der Banken anzuzeigen.

![Quadrantendiagramme](assets/charts_quadrant_example_new.png)

