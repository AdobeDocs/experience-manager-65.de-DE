---
title: Erscheinungsbild-Framework für adaptive und HTML5-Formulare
seo-title: Erscheinungsbild-Framework für adaptive und HTML5-Formulare
description: Mobile Forms rendert Formularvorlagen als HTML5-Formulare. Diese Formulare verwenden jQuery, Backbone.js- und Underscore.js-Dateien für das Erscheinungsbild und um Skripten zu aktivieren.
seo-description: Mobile Forms rendert Formularvorlagen als HTML5-Formulare. Diese Formulare verwenden jQuery, Backbone.js- und Underscore.js-Dateien für das Erscheinungsbild und um Skripten zu aktivieren.
uuid: 183b8d71-44fc-47bf-8cb2-1cf920ffd23a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 3c2a44a7-24e7-49ee-bf18-eab0e44efa42
exl-id: 3458471a-9815-463e-8044-68631073863c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 93%

---

# Erscheinungsbild-Framework für adaptive und HTML5-Formulare {#appearance-framework-for-adaptive-and-html-forms}

Formulare (adaptive Formulare und HTML5-Formulare) verwenden [jQuery](https://jquery.com/)-, [Backbone.js](https://backbonejs.org/)- und [Underscore.js](https://underscorejs.org/)-Bibliotheken für das Erscheinungsbild und die Skripterstellung. Die Formulare verwenden auch die Architektur von [jQuery UI](https://jqueryui.com/)-**Widgets** für alle interaktiven Elemente (beispielsweise Felder und Schaltflächen) im Formular. Durch diese Architektur stehen Formularentwicklern eine umfangreiche Auswahl von jQuery-Widgets und -Plug-Ins in Formularen zur Verfügung. Sie können ebenfalls formularspezifische Logik beim Erfassen von Benutzerdaten implementieren, wie etwa „leadDigits/trailDigits“-Einschränkungen, oder Bildklassen implementieren. Formularentwickler können benutzerdefinierte Erscheinungsbilder erstellen und verwenden, um die Datenerfassungserfahrung zu verbessern und sie benutzerfreundlicher zu gestalten.

Dieser Artikel richtet sich an Entwickler mit genügend Wissen zu jQuery und jQuery-Widgets. Er enthält Informationen zum Erscheinungsbild-Framework und ermöglicht es Entwicklern, ein anderes Erscheinungsbild für ein Formularfeld zu erstellen.

Das Erscheinungsbild-Framework stützt sich bei der Erfassung von Benutzerinteraktionen mithilfe eines Formulars auf verschiedenen Optionen, Ereignisse (Auslöser) und Funktionen und reagiert auf die Änderungen des Modells, um den Benutzer zu informieren. Zusätzlich gilt Folgendes:

* Das Framework stellt einen Optionssatz für das Erscheinungsbild eines Felds bereit. Diese Optionen sind Schlüssel-Wert-Paare und in zwei Kategorien unterteilt: „Allgemeine Optionen“ und „Feldtypspezifische Optionen“.
* Das Erscheinungsbild löst als Teil des Kontrakts eine Reihe von Ereignissen wie „enter“, „exit“ und so weiter aus.
* Das Erscheinungsbild muss einen Funktionssatz implementieren. Einige der Funktionen sind allgemein, während andere spezifisch für die Feldtypfunktion sind.

## Allgemeine Optionen  {#common-options}

Im Folgenden die globalen Optionen. Diese Optionen sind für jedes Feld verfügbar.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft </th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>name</td>
   <td>Ein Bezeichner, mit dem dieses Objekt oder Ereignis in Skriptausdrücken angegeben wird. Diese Eigenschaft gibt beispielsweise den Namen der Host-Anwendung an.</td>
  </tr>
  <tr>
   <td>value</td>
   <td>Tatsächlicher Wert des Felds. </td>
  </tr>
  <tr>
   <td>displayValue</td>
   <td>Der Wert des Felds wird angezeigt. </td>
  </tr>
  <tr>
   <td>screenReaderText</td>
   <td>Bildschirmlesehilfen verwenden diesen Wert, um Informationen über das Feld vorzulesen. Das Formular stellt den Wert bereit und Sie können den Wert überschreiben.<br /> </td>
  </tr>
  <tr>
   <td>tabIndex</td>
   <td>Die Position des Felds in der Tab-Abfolge des Formulars. Überschreiben Sie den tabIndex nur, wenn Sie die Standardreihenfolge der Registerkarten im Formular ändern möchten.</td>
  </tr>
  <tr>
   <td>role</td>
   <td>Rolle des Elements, z. B. Überschrift oder Tabelle.</td>
  </tr>
  <tr>
   <td>height</td>
   <td>Die Höhe des Widgets. Sie wird in Pixeln angegeben. </td>
  </tr>
  <tr>
   <td>Breite</td>
   <td>Die Breite des Widgets. Sie wird in Pixeln angegeben.</td>
  </tr>
  <tr>
   <td>access</td>
   <td>Steuert den Benutzerzugriff auf den Inhalt eines Containers, beispielsweise ein Teilformular.</td>
  </tr>
  <tr>
   <td>paraStyles</td>
   <td>Die Para-Eigenschaft eines XFA-Elements des Widgets.</td>
  </tr>
  <tr>
   <td>dir</td>
   <td>Die Richtung des Textes. Mögliche Werte sind: ltr (links nach rechts) und rtl (rechts nach links).</td>
  </tr>
 </tbody>
</table>

Zusätzlich zu diesen Optionen stellt das Framework einige andere Optionen bereit, die je nach Typ des Felds variieren. Die Details zu den feldspezifischen Optionen sind unten aufgeführt.

### Interaktion mit Formularframework  {#interaction-with-forms-framework}

Um mit dem Formularframework zu interagieren, löst ein Widget einige Ereignisse aus, die das Formularskript aktivieren. Wenn das Widget diese Ereignisse nicht erzeugt, funktionieren einige der Skripte nicht, die im Formular für dieses Feld eingegeben wurden.

#### Vom Widget ausgelöste Ereignisse  {#events-triggered-by-widget}

<table>
 <tbody>
  <tr>
   <th>Ereignis </th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>XFA_ENTER_EVENT</td>
   <td>Das Ereignis wird ausgelöst, wenn das Feld im Fokus ist. Dadurch kann Skript „eingegeben“ werden, der im Feld ausgeführt wird. Die Syntax zum Auslösen des Ereignisses ist<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_ENTER_EVENT)<br /> </td>
  </tr>
  <tr>
   <td>XFA_EXIT_EVENT</td>
   <td>Dieses Ereignis wird ausgelöst, wenn der Benutzer das Feld verlässt. Dadurch kann die Engine den Wert des Feldes festlegen und ihr „exit“-Skript ausführen. Die Syntax zum Auslösen des Ereignisses ist<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_EXIT_EVENT)<br /> </td>
  </tr>
  <tr>
   <td>XFA_CHANGE_EVENT</td>
   <td>Das Ereignis wird ausgelöst, damit die Engine ihr „change“-Skript ausführen kann, das für das Feld eingegeben wurde. Die Syntax zum Auslösen des Ereignisses ist<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_CHANGE_EVENT)<br /> </td>
  </tr>
  <tr>
   <td>XFA_CLICK_EVENT</td>
   <td>Das Ereignis wird ausgelöst, wenn das Feld angeklickt wird. Dadurch kann die Engine das „click“-Skript ausführen, das für das Feld eingegeben wurde. Die Syntax zum Auslösen des Ereignisses ist<br /> (Widget)._trigger(xfalib.ut.XfaUtil.prototype.XFA_CLICK_EVENT)<br /> </td>
  </tr>
 </tbody>
</table>

#### Vom Widget implementierte APIs {#apis-implemented-by-widget}

Die Erscheinungsbild-Framework ruft einige Funktionen des Widgets auf, die in den benutzerdefinierten Widgets implementiert sind. Das Widget muss die folgenden Funktionen implementieren:

<table>
 <tbody>
  <tr>
   <th>Funktion</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>focus : function()</td>
   <td>Fokus wird auf das gelegt.</td>
  </tr>
  <tr>
   <td>click : function()</td>
   <td>Fokus wird auf das Feld gelegt und XFA_CLICK_EVENT wird aufgerufen.</td>
  </tr>
  <tr>
   <td><p>markError:function(errorMessage, errorType)<br /> <br /> <em>erorrMessage: string </em>der den Fehler<br /> <em>errorType darstellt: string ("warning"/"error")</em></p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare.</p> </td>
   <td>Sendet Fehlermeldung und Fehlertyp an das Widget. Das Widget zeigt den Fehler an.</td>
  </tr>
  <tr>
   <td><p>clearError: function()</p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare.</p> </td>
   <td>Wird aufgerufen, wenn die Fehler im Feld behoben wurden. Das Widget blendet den Fehler aus.</td>
  </tr>
 </tbody>
</table>

## Optionen je nach Feldtyp  {#options-specific-to-type-of-field}

Alle benutzerdefinierten Widgets sollten mit den oben genannten Spezifikationen übereinstimmen. Um die Funktionen von verschiedenen Feldern zu nutzen, muss das Widget den Richtlinien des jeweiligen Felds entsprechen.

### TextEdit: Text Field {#textedit-text-field}

<table>
 <tbody>
  <tr>
   <th>Option</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>multiLine</td>
   <td>„True“, wenn das Feld die Eingabe eines Zeilenumbruchzeichens unterstützt, andernfalls „false“.</td>
  </tr>
  <tr>
   <td>maxChars</td>
   <td>Maximale Anzahl der Zeichen, die in das Feld eingegeben werden können.</td>
  </tr>
  <tr>
   <td><p>limitLengthToVisibleArea</p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare.</p> </td>
   <td>Gibt das Verhalten des Textfelds an, wenn die Textbreite die Breite des Widgets überschreitet.</td>
  </tr>
 </tbody>
</table>

### ChoiceList: DropDownList, ListBox  {#choicelist-dropdownlist-listbox}

<table>
 <tbody>
  <tr>
   <th>Option</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Wert<br /> </td>
   <td>Array der ausgewählten Werte.<br /> </td>
  </tr>
  <tr>
   <td>items<br /> </td>
   <td>Array von Objekten, die als Optionen angezeigt werden sollen. Jedes Objekt enthält zwei Eigenschaften:<br />„save“ (zu speichernder Wert), „display“ (anzuzeigender Wert).<br /> <br />  </td>
  </tr>
  <tr>
   <td><p>standardmäßig als bearbeitbar</p> <p><strong>Hinweis</strong>: Gilt nur für HTML5-Formulare.<br /> </p> </td>
   <td>„True“: Die Eingabe von benutzerdefiniertem Text im Widget wird aktiviert.<br />  </td>
  </tr>
  <tr>
   <td>displayValue<br /> </td>
   <td>Anzuzeigendes Werte-Array.<br /> </td>
  </tr>
  <tr>
   <td>multiselect<br /> </td>
   <td>„True“, wenn Mehrfachauswahlen zulässig sind, andernfalls „false“.<br />  </td>
  </tr>
 </tbody>
</table>

#### API {#api}

<table>
 <tbody>
  <tr>
   <th>Funktion</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td><p>addItem:<em> function(itemValues)<br /> itemValues: Objekt, das die Werte für „display“ und „save“ enthält <br /> {sDisplayVal: &lt;displayValue&gt;, sSaveVal: &lt;save Value&gt;}</em></p> </td>
   <td>Fügt der Liste ein Element hinzu.</td>
  </tr>
  <tr>
   <td>deleteItem<em>: function(nIndex)<br /> nIndex: Index des Elements, das aus der Liste entfernt werden soll<br /> </em><br /> <br /> </td>
   <td>Löscht eine Option aus der Liste.</td>
  </tr>
  <tr>
   <td>clearItems:<code> function()</code></td>
   <td>Löscht alle Optionen aus der Liste.</td>
  </tr>
 </tbody>
</table>

### NumericEdit: NumericField, DecimalField  {#numericedit-numericfield-decimalfield}

| Optionen | Beschreibung |
|---|---|
| dataType | String, der, der den Datentyp des Felds darstellt (ganze Zahl/Dezimalzahl). |
| leadDigits | Maximale führende Ziffern der Dezimalzahl. |
| fracDigits | Maximale Bruchzahlen in der Dezimalzahl. |
| zero | Die Zeichenfolgendarstellung von Null im Gebietsschema des Felds. |
| decimal | Die Zeichenfolgendarstellung von Dezimalzahlen im Gebietsschema des Felds. |

### CheckButton: RadioButton, CheckBox  {#checkbutton-radiobutton-checkbox}

<table>
 <tbody>
  <tr>
   <th>Optionen</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>values</td>
   <td><p>Werte-Array(an/aus/neutral).</p> <p>Werte-Array für die verschiedenen Statusangaben des CheckButton. Wert[0] steht für den Status AN, Wert[1] steht für den Status AUS,<br /> Wert[2] steht für den Status NEUTRAL. Die Länge des Werte-Arrays entspricht dem Wert der Status-Option.<br /> </p> </td>
  </tr>
  <tr>
   <td>states</td>
   <td><p>Zahl der zulässigen Zustände. </p> <p>Zwei für adaptive Formulare (Ein, Aus) und drei für HTML5-Formulare (Ein, Aus, Neutral).</p> </td>
  </tr>
  <tr>
   <td>state</td>
   <td><p>Aktueller Status des Elements.</p> <p>Zwei für adaptive Formulare (Ein, Aus) und drei für HTML5-Formulare (Ein, Aus, Neutral).</p> </td>
  </tr>
 </tbody>
</table>

### DateTimeEdit: (DateField) {#datetimeedit-datefield}

| Option | Beschreibung |
|---|---|
| Tage | Lokalisierte Tagesnamen für dieses Feld. |
| months | Lokalisierte Monatsnamen für dieses Feld. |
| zero | Der lokalisierte Text für die Zahl 0. |
| clearText | Der lokalisierte Text für die Schaltfläche „Löschen“.  |
