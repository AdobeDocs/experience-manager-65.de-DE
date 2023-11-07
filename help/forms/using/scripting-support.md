---
title: Skriptunterstützung für HTML5-Formulare
seo-title: Scripting support for HTML5 forms
description: JavaScript, FormCalc-Eigenschaften und andere Methoden, die in HTML5 Forms unterstützt werden.
seo-description: JavaScript, FormCalc properties, and other methods that are supported in HTML5 Forms.
uuid: 697d5ec4-c818-41e4-b813-883c01b7ff3a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 4ef78c8c-783f-4aac-a499-692cd4acef75
feature: Mobile Forms
exl-id: bcb5afc5-2190-4269-aba2-63842db9df3f
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '3888'
ht-degree: 21%

---

# Skriptunterstützung für HTML5-Formulare {#scripting-support-for-html-forms}

Die folgenden JavaScript-, FormCalc-Eigenschaften und Methoden werden in HTML5-Formularen unterstützt:

## $event {#event}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft </th>
   <th>Beschreibung<br /> </th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td><code>prevText</code></td>
   <td>Gibt den Inhalt des Felds an, bevor er sich aufgrund der Aktionen eines Benutzers ändert. Dieser Wert kann ähnlich wie bei einer Funktion zum Rückgängigmachen zurückgerufen werden.</td>
   <td><p>Funktioniert nicht bei Dropdown-Listen und Listenfeldern. <code>PrevText </code>funktioniert in folgenden Fällen nicht:</p>
    <ul>
     <li>Beim Eingeben bestimmter Sonderzeichen (z. B. $, (,), &amp;, @ und viele andere) in numerischen Feldern in der iPad und </li>
     <li>Für das Datumsfeld (wenn das Datum über den Kalender eingegeben wird).<br /> </li>
    </ul> <p>Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.</p> </td>
  </tr>
  <tr>
   <td><code>target</code></td>
   <td>Gibt das Objekt an, auf das das Ereignis reagiert.</td>
   <td>Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.<br /> </td>
  </tr>
  <tr>
   <td><code>newtext</code></td>
   <td>Gibt den Inhalt des Feldes nach einer Änderung aufgrund von Benutzeraktionen an.</td>
   <td><p>Die Eigenschaft <code>newText</code> funktioniert in folgenden Fällen nicht ordnungsgemäß:</p>
    <ul>
     <li>Beim Auswählen und Ersetzen von Texten</li>
     <li>Beim Löschen, Kopieren und Einfügen von Texten.</li>
     <li>Beim Eingeben bestimmter Sonderzeichen (z. B. $, (, ), &amp;, @ und viele andere) in numerischen Feldern<br /> </li>
     <li>Bei Verwendung der Kombination Umschalt+Alphanumerisch. </li>
     <li>Beim Verwenden von Datums- und Uhrzeitfeldern</li>
    </ul>
    <div>
      Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.
    </div> </td>
  </tr>
  <tr>
   <td>ändern</td>
   <td>Gibt den Wert an, den ein Benutzer unmittelbar nach Ausführung der Aktion in ein Feld eingibt oder einfügt. </td>
   <td><p>Die Eigenschaft „Ändern“ funktioniert in folgenden Fällen nicht ordnungsgemäß:</p>
    <ul>
     <li>Beim Auswählen und Ersetzen von Texten</li>
     <li>Beim Löschen, Kopieren und Einfügen von Texten.</li>
     <li>Beim Eingeben bestimmter Sonderzeichen (z. B. $, (,), &amp;, @ und viele andere) in numerischen Feldern<br /> </li>
     <li>Bei Verwendung der Kombination Umschalt+Alphanumerisch. </li>
     <li>Beim Verwenden von Datums- und Uhrzeitfeldern</li>
    </ul> <p>Das Festlegen eines Werts mithilfe eines Skripts wird nicht unterstützt.</p> </td>
  </tr>
  <tr>
   <td>Keydown</td>
   <td>Bestimmt, ob ein Benutzer eine Auswahl durch Drücken einer Pfeiltaste trifft. Diese Eigenschaft ist nur für Listenfelder und Dropdownlisten verfügbar.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>modifier</td>
   <td>Bestimmt, ob die Modifikatortaste (z. B. Strg unter Microsoft® Windows®) gedrückt wird, wenn ein bestimmtes Ereignis ausgeführt wird.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

### $host {#host}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td><code>apptype</code></td>
   <td>Gibt den Anwendungstyp des Hosts zurück. Nur für Clientanwendungen verfügbar.</td>
   <td>Rückgabe <code>HTML 5</code>.</td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>Gibt den Namen der aktuellen Anwendung zurück.</td>
   <td>Gibt den Browsernamen und die Version zurück. Beim Browser Chrome wird beispielsweise folgender Wert zurückgegeben: <code>Chrome &lt;version&gt;.</code></td>
  </tr>
  <tr>
   <td><code>numPages</code></td>
   <td>Gibt die Anzahl der Seiten im Dokument zurück.</td>
   <td>Die Paginierungspolitik von HTML5-Formularen ist nicht mit der Paginierungsrichtlinie für PDF forms identisch. Die numPages-API kann daher in beiden Fällen unterschiedliche Werte zurückgeben.</td>
  </tr>
  <tr>
   <td><code>platform</code></td>
   <td>Gibt eine Zeichenfolge zurück, die die Plattform des Computers darstellt, auf dem das Skript ausgeführt wird.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>title</code></td>
   <td>Gibt den Titel des Dokuments an. Sie ist nur für Clientanwendungen verfügbar.</td>
   <td>Es wird der Titel des HTML-Dokuments im Formular zurückgegeben, nicht der Metadatentitel des Formulars, wie im Fall von PDF forms.</td>
  </tr>
  <tr>
   <td><code>version</code></td>
   <td>Gibt eine Zeichenfolge zurück, die die Versionsnummer der aktuellen Anwendung darstellt.</td>
   <td>Es wird die Version des Formulars zurückgegeben.</td>
  </tr>
  <tr>
   <td><code>calculationsEnabled</code></td>
   <td>Gibt an, ob Berechnungsskripten ausgeführt werden.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>validationsEnabled</code></td>
   <td>Gibt an, ob Überprüfungsskripten ausgeführt werden.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>pageUp</code></td>
   <td>Wechselt zur vorherigen Seite.</td>
   <td>HTML5-Formulare folgen nicht derselben Paginierungsrichtlinie wie PDF-Formulare. Daher unterscheidet sich die vorherige Seite eines HTML5-Formulars von der vorherigen Seite eines PDF-Formulars.</td>
  </tr>
  <tr>
   <td><code>pageDown</code></td>
   <td>Wechselt zur nächsten Formularseite. Verwenden Sie die pageDown-Methode zur Laufzeit.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>setFocus</code></td>
   <td>Legt den Tastaturfokus auf das angegebene Feld fest. Das Feld wird als Objekt oder durch den SOM-Ausdruck des Felds angegeben. Sie ist nur für Clientanwendungen verfügbar.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>resetdata</code></td>
   <td>Setzt die Felder auf ihre Standardwerte in einem Dokument zurück.</td>
   <td>Löscht alle Daten in einem Formular mit zusammengeführten Daten, anstatt sie auf Standardwerte zurückzusetzen.</td>
  </tr>
  <tr>
   <td><code>messageBox</code></td>
   <td>Zeigt ein Dialogfeld auf dem Bildschirm an. Sie ist nur für Client-Anwendungen verfügbar</td>
   <td>Das Meldungsfeld vom Typ Ja/Nein wird in OK/Abbrechen konvertiert. Das Meldungsfeld mit drei Schaltflächen wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td>currentPage</td>
   <td><p>Legt die derzeit aktive Seite eines Dokuments zur Laufzeit fest.</p> <p>Seitenzahlen sind 0-basiert, sodass die erste Seite eines Dokuments den Wert 0 zurückgibt.</p> <p>Die currentPage -Eigenschaft ist verfügbar, wenn layout:ready auf einem Client ausgeführt wird. Sie ist jedoch nicht verfügbar, wenn layout:ready auf dem Server ausgeführt wird, da die Eigenschaft erst ausgeführt wird, wenn das Formularlayout ausgeführt wird.</p> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

### field {#field}

<table>
 <tbody>
  <tr>
   <th><strong><span>Eigenschaft</span></strong></th>
   <th><strong><span>Beschreibung<br /> </span></strong></th>
   <th><strong><span>Ausnahme</span></strong></th>
  </tr>
  <tr>
   <td><code>presence</code></td>
   <td>Steuert die Beteiligung des verknüpften Objekts an verschiedenen Verarbeitungsphasen. Wenn das Objekt ein Container ist, erben die Inhalte des Containers alle Einschränkungen, die dieses Steuerelement anwendet.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>access</code></td>
   <td>Steuert den Benutzerzugriff auf den Inhalt.</td>
   <td>Funktioniert nicht mit die Ausschlussgruppe. Außerdem werden nicht interaktive und geschützte Objekte in HTML5-Formularen gleich behandelt.<br /> </td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td>Eine Kennung, die verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen.</td>
   <td>HTML5-Formulare lassen das Festlegen der name-Eigenschaft für Objekte nicht zu. Dies ist eine schreibgeschützte Eigenschaft für HTML5-Formulare.</td>
  </tr>
  <tr>
   <td><code>value</code></td>
   <td>Ein Inhaltselement, das eine Dateninhaltseinheit umfasst.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>rawValue</code></td>
   <td>Gibt den nicht formatierten Wert für dieses Feld an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>formattedValue</code></td>
   <td>Gibt den formatierten Wert für dieses Feld an.</td>
   <td>Das Festlegen des Werts <code>formattedValue</code> mithilfe eines Skripts wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td><code>editValue</code></td>
   <td>Gibt den bearbeiteten Wert für dieses Feld an.</td>
   <td>Das Festlegen des Werts <code>editValue </code> mithilfe eines Skripts wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td><code>formatMessage</code></td>
   <td>Gibt die Zeichenfolge der Meldung zur Formatprüfung für dieses Feld an.</td>
   <td>Das Festlegen des Werts <code>formatMessage </code> mithilfe eines Skripts wird nicht unterstützt.</td>
  </tr>
  <tr>
   <td><code>fillcolor</code></td>
   <td>Gibt den Wert der Hintergrundfarbe für dieses Feld an. Sie müssen die Eigenschaft border.fill.presence separat als sichtbar einstellen.</td>
   <td>Sie gibt die Standardfarbe des Feldes nicht richtig zurück.</td>
  </tr>
  <tr>
   <td><code>border</code></td>
   <td>Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>ui</code></td>
   <td>Das ui-Objekt umfasst die Beschreibung der Benutzeroberfläche eines Formularobjekts.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>mandatory</code></td>
   <td>Gibt den nullTest-Wert für das Feld an.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>borderColor</code></td>
   <td>Gibt den Rahmenfarbwert für dieses Feld an. Sie müssen die Eigenschaft border.edge.presence separat als sichtbar einstellen.</td>
   <td>Sie gibt die Standardfarbe des Feldes nicht richtig zurück.</td>
  </tr>
  <tr>
   <td><code>length</code></td>
   <td>Die Anzahl der Listenelemente.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>addItem</code></td>
   <td>Fügt dem aktuellen Feld neue Elemente hinzu.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>clearItem</code></td>
   <td>Entfernt alle Elemente aus dem Feld.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>boundItem</code></td>
   <td>Ruft den Bindewert eines bestimmten Anzeigeelements aus einer Dropdown-Liste oder einem Listenfeld ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>execCalculate</code></td>
   <td>Führt das Berechnungsskript des Felds aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>execValidate</code></td>
   <td>Führt das Überprüfungsskript des Felds aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>execEvent</code></td>
   <td>Führt das Ereignisskript des Objekts aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>getItemState</code></td>
   <td>Gibt den Auswahlstatus des angegebenen Elements aus</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>setItemState</code></td>
   <td>Legt den Auswahlstatus des angegebenen Elements fest.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>getDisplayItem</code></td>
   <td>Ruft den Elementanzeigetext für den angegebenen Elementindex ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>getSaveItem</code></td>
   <td>Ruft den Datenwert für den angegebenen Elementindex ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>deleteItem</code></td>
   <td>Löscht das Element am angegebenen Index.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td><code>setItems</code></td>
   <td>Legt die angegebenen Elemente im aktuellen Feld fest. Sie ersetzt bereits vorhandene Elemente.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Eine Messung der Höhe für das Layout.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Eine Maßeinheit für die Breite des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Gibt die X-Koordinate des Verankerungspunkts des Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung mit positioniertem Layout an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Gibt die Y-Koordinate für den Ankerpunkt eines Containers im Verhältnis zur oberen linken Ecke des übergeordneten Containers bei Platzierung mit einem positionierten Layout an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>caption</td>
   <td>Das caption -Objekt beschreibt eine beschreibende Bezeichnung, die mit einem Formularentwurfsobjekt verknüpft ist.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Das validate -Objekt steuert die Überprüfung von vom Benutzer bereitgestellten Daten in einem Formular. Das validate -Objekt kann während der Lebensdauer eines Formulars mehrmals aktiviert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>parentSubform</td>
   <td>Gibt das übergeordnete Teilformular (Seite) dieses Felds an.</td>
   <td>Gibt immer übergeordnete Teilformulare zurück statt zuerst übergeordnete Teilformulare ohne Scoping.<br /> </td>
  </tr>
  <tr>
   <td>selectedIndex</td>
   <td>Der Index des ersten ausgewählten Elements.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## Formular {#form}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| formNodes | Gibt eine Liste aller Formularmodellobjekte zurück, die an ein bestimmtes Datenobjekt gebunden sind. |  |

## InstanceManager {#instancemanager}

| Eigenschaft | Beschreibung |
|---|---|
| `name` | Ein Bezeichner, der verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen. |
| `occur` | Beschreibt die Einschränkungen in Bezug auf die Anzahl der zulässigen Instanzen für den zugehörigen einschließenden Container. |
| `min` | Gibt die Mindestanzahl der Instanzen an, die instanziiert werden können. |
| `max` | Gibt die Höchstanzahl der Instanzen an, die instanziiert werden können. |
| `count` | Gibt die aktuelle Anzahl der instanziierten Instanzen an. |
| `setInstances` | Fügt die angegebenen Teilformulare oder Teilformularsätze von diesem Knoten zurück oder entfernt diese. |
| `addInstance` | Fügt diese Knoten eine neue Instanz eines Teilformulars oder Teilformularsatzes hinzu. |
| `removeInstance` | Entfernt ein Teilformular oder einen Teilformularsatz von diesem Knoten. |
| `moveInstance` | Verschiebt ein untergeordnetes Objekt eines Formularmodellobjekts an eine andere angegebene Position innerhalb des Formularmodells. Die entsprechenden Datenmodellinformationen für das Objekt werden ebenfalls innerhalb des Datenmodells neu positioniert. |
| `insertInstance` | Fügt diesem Knoten eine neue Instanz eines Teilformulars oder Teilformularsatzes hinzu. |

## list {#list}

| Eigenschaft | Beschreibung |
|---|---|
| `length` | Die Anzahl der Elemente in der Liste. |
| `item` | Index auf der Basis Null zur Sammlung. |
| `append` | Fügt am Ende der Liste der Nodes eine Node an. |
| `remove` | Entfernt einen Knoten aus der Knotenliste. |
| `insert` | Fügt einen Knoten vor einem bestimmten Knoten in die Knotenliste ein. |

## Knoten {#node}

| Eigenschaft | Beschreibung | Ausnahme |
|---|---|---|
| createNode | Erstellt einen neuen Knoten basierend auf einem gültigen Klassennamen. | Ohne |
| `isContainer` | Gibt an, ob dieses Objekt ein Containerobjekt ist. | Ohne |
| `isNull` | Gibt an, ob der aktuelle Datenwert ein Nullwert ist. | Ohne |
| `resolveNode` | Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück. | Ohne |
| `resolveNodes` | Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück. | Ohne |
| oneOfChild | Erstellt einen neuen Knoten basierend auf einem gültigen Klassennamen. | Ohne |
| getElement | Gibt ein bestimmtes untergeordnetes Objekt zurück. | Ohne |
| getAttribute | Ruft einen angegebenen Eigenschaftswert ab. | Ohne |
| setAttribute | Legt den Wert einer angegebenen Eigenschaft fest. | Ohne |

## model {#model}

| Eigenschaft | Beschreibung | Ausnahme |
|---|---|---|
| nicht vorhanden | nicht vorhanden | nicht vorhanden |

## Teilformular {#subform}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td>instanceIndex</td>
   <td>Gibt den Index des Objekts relativ zu den anderen instanziierten Instanzen an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>execEvent</td>
   <td>Führt das Ereignisskript des Objekts aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>getInvalidObjects</td>
   <td>Gibt eine Liste von Nodes im Teilformular (einschließlich) zurück, bei denen der Validierungstest fehlgeschlagen ist.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Gibt den Rahmenfarbwert für dieses Feld an. Sie müssen die Eigenschaft border.edge.presence separat als sichtbar einstellen.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Eine Messung der Höhe für das Layout.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Eine Maßeinheit für die Breite des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Gibt die X-Koordinate des Verankerungspunkts des Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung mit positioniertem Layout an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Gibt die Y-Koordinate für den Ankerpunkt eines Containers im Verhältnis zur oberen linken Ecke des übergeordneten Containers bei Platzierung mit einem positionierten Layout an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Das validate -Objekt steuert die Überprüfung von vom Benutzer bereitgestellten Daten in einem Formular. Das validate -Objekt kann während der Lebensdauer eines Formulars mehrmals aktiviert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>name</td>
   <td>Eine Kennung, die verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Gibt die Sichtbarkeit eines Objekts an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>access</td>
   <td>Steuert den Benutzerzugriff auf den Inhalt eines Containers, z. B. eines Teilformulars.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>execValidate</td>
   <td>Berechnet den Index eines Teilformulars oder Teilformularsatzes anhand dessen Position im Verhältnis zu anderen Instanzen desselben Formularobjekts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>instanceManager</td>
   <td>Das instanceManager-Objekt verwaltet das Erstellen, Entfernen und Verschieben von Formularmodellobjekten in Instanzen.<br /> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

### absenden {#submit}

| Eigenschaft | Beschreibung |
|---|---|
| target | Die URL, an die die Daten gesendet werden. Das Auslassen dieses Attributs impliziert, dass die XFA-Verarbeitungsanwendung den URI mithilfe einer produktspezifischen Technik abruft, z. B. durch Zugriff auf produktspezifische Informationen im config-Objekt. |

## tree {#tree}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
   <th>Ausnahme</th>
  </tr>
  <tr>
   <td>Knoten</td>
   <td>Gibt eine Liste aller untergeordneten Objekte des aktuellen Objekts zurück.</td>
   <td>
    <ul>
     <li>Nicht unterstützt für xfa.nodes, desc</li>
     <li>Unterschiedliche Anzahl der für PDF und HTML übermittelten Knoten. </li>
    </ul> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Gibt den Namen dieses Knotens an.</td>
   <td>Das Festlegen des Namens mithilfe von Skripten ist im HTML nicht zulässig.</td>
  </tr>
  <tr>
   <td>parent</td>
   <td>Ruft die übergeordnete Node für diesen Knoten ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>index</td>
   <td>Gibt die Position dieses Knotens in seiner Sammlung von untergeordneten Knoten mit gleichen Namen im Bereich zurück.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>somExpression</td>
   <td>Ruft den SOM-Ausdruck für diesen Knoten ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>resolveNode</td>
   <td>Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>resolveNodes</td>
   <td>Wertet den angegebenen SOM-Ausdruck aus, angefangen mit dem aktuellen Objekt des XML-Formularobjektmodells, und gibt den Wert des im SOM-Ausdruck angegebenen Objekts zurück.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## subformset {#subformset}

| Eigenschaft | Beschreibung | Ausnahme |
|---|---|---|
| instanceManager | Das instanceManager-Objekt verwaltet das Erstellen, Entfernen und Verschieben von Formularmodellobjekten in Instanzen. | Ohne |

## content {#content}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| isNull | Gibt an, ob der aktuelle Datenwert der Nullwert ist. |  |

## dataValue {#datavalue}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| isNull | Gibt an, ob der aktuelle Datenwert der Nullwert ist. |  |

## edge {#edge}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft </strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft "Farbe"beschreibt eine eindeutige Farbe für das pattern-Objekt.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## fill {#fill}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Farbeigenschaften definieren eine eindeutige Füllfarbe.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## linear {#linear}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft "Farbe"beschreibt eine eindeutige Farbe für einen linearen Füllverlauf in einem Formular.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Zeile {#line}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge -Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie Farbe, Cap usw. werden nicht unterstützt.<br /> </td>
  </tr>
 </tbody>
</table>

## pattern {#pattern}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft "Farbe"beschreibt eine eindeutige Farbe für das pattern-Objekt. </td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## radial {#radial}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft "Farbe"beschreibt eine eindeutige Farbe für das radial-Objekt</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## stipple {#stipple}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft "Farbe"beschreibt eine eindeutige Farbe für das stipple -Objekt.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## draw {#draw}

<table>
 <tbody>
  <tr>
   <td>Eigenschaft</td>
   <td>Beschreibung</td>
   <td>Ausnahme</td>
  </tr>
  <tr>
   <td>ui</td>
   <td>Das ui-Objekt umfasst die Beschreibung der Benutzeroberfläche eines Formularobjekts.<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td>caption</td>
   <td>Das caption -Objekt beschreibt eine beschreibende Bezeichnung, die mit einem Formularentwurfsobjekt verknüpft ist.</td>
   <td> </td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Gibt die Sichtbarkeit eines Objekts an.</td>
   <td> </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Gibt eine Kennung an, die verwendet werden kann, um dieses Objekt oder Ereignis in Skriptausdrücken anzugeben.</td>
   <td>Das Festlegen des Werts zur Laufzeit wird nicht unterstützt</td>
  </tr>
  <tr>
   <td>value</td>
   <td>Das value -Objekt umfasst eine Dateninhaltseinheit.<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

## corner {#corner}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>Farbe</td>
   <td>Die Eigenschaft "Farbe"beschreibt eine eindeutige Farbe für das corner-Objekt.</td>
   <td>
    <ul>
     <li>Der Standardwert kann nicht abgerufen werden. </li>
     <li>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## checkButton {#checkbutton}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der das checkButton-Objekt umgibt. </td>
   <td>Die Änderungen werden im Modell übernommen und stehen für die Skripterstellung zur Verfügung, werden jedoch nicht mit HTML-Elementen synchronisiert. Daher werden die Änderungen nicht in der Benutzeroberfläche angezeigt.<br /> </td>
  </tr>
 </tbody>
</table>

## choiceList {#choicelist}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<br /> </strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der das choiceList-Objekt umgibt.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## dateTimeEdit {#datetimeedit}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| border | Das border-Objekt beschreibt den Rahmen, der das dateTimeEdit-Objekt umgibt. |  |

## Bild {#image}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>contentType</td>
   <td>Gibt den Inhaltstyp im referenzierten Dokument an, ausgedrückt als MIME-Typ.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>name<br /> </td>
   <td>Eine Kennung, die verwendet wird, um dieses Element in Skriptausdrücken eindeutig zu kennzeichnen.</td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## imageEdit {#imageedit}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| border | Das border-Objekt beschreibt den Rahmen, der das imageEdit-Objekt umgibt. |  |

## numericEdit {#numericedit}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| border | Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt. | keine |

## Objekt {#object}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>className</td>
   <td>Bestimmt den Namen der Klasse dieses Objekts.<br /> </td>
   <td>keine</td>
  </tr>
 </tbody>
</table>

## Rechteck {#rectangle}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge -Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie Farbe, Cap usw. werden nicht unterstützt.</td>
  </tr>
 </tbody>
</table>

## textEdit {#textedit}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>border</td>
   <td>Das border-Objekt beschreibt den Rahmen, der ein Objekt umgibt.<br /> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## exclGroup {#exclgroup}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>layout</td>
   <td>Gibt die von diesem Objekt zu verwendende Layoutstrategie an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>border</td>
   <td>Gibt den Rahmen für dieses Feld an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>mandatory</td>
   <td>Gibt den nullTest-Wert für das Feld an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>borderColor</td>
   <td>Gibt den Rahmenfarbwert für dieses Feld an. Bevor Sie die Farbe mithilfe eines Skripts ändern können, muss ein Rahmen definiert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>borderWidth</td>
   <td>Gibt die Rahmenbreite für dieses Feld an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>h</td>
   <td>Eine Messung der Höhe für das Layout.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>transient</td>
   <td>Gibt an, ob die verarbeitende Anwendung den Wert der Ausschlussgruppe im Rahmen eines Formularsende- oder -speichervorgangs speichern muss.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>w</td>
   <td>Eine Maßeinheit für die Breite des Layouts.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>x</td>
   <td>Gibt die X-Koordinate des Verankerungspunkts des Containers in Bezug auf die linke obere Ecke des übergeordneten Containers bei Platzierung mit positioniertem Layout an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>y</td>
   <td>Gibt die Y-Koordinate für den Ankerpunkt eines Containers im Verhältnis zur oberen linken Ecke des übergeordneten Containers bei Platzierung mit einem positionierten Layout an.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>caption</td>
   <td>Das caption -Objekt beschreibt eine beschreibende Bezeichnung, die mit einem Formularentwurfsobjekt verknüpft ist.<br /> </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>validate</td>
   <td>Das validate -Objekt steuert die Überprüfung von vom Benutzer bereitgestellten Daten in einem Formular. Das validate -Objekt kann während der Lebensdauer eines Formulars mehrmals aktiviert werden.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>dataNode</td>
   <td>Ruft die Daten-Node ab, an die eine Formular-Node nach der Zusammenführung gebunden ist.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>presence</td>
   <td>Gibt die Sichtbarkeit eines Objekts an.</td>
   <td> </td>
  </tr>
  <tr>
   <td>access</td>
   <td>Steuert den Benutzerzugriff auf den Inhalt eines Containers, z. B. eines Teilformulars.</td>
   <td>Wird für einzelne Elemente der exclgrp immer offen zurückgegeben. </td>
  </tr>
  <tr>
   <td>name</td>
   <td>Gibt eine Kennung an, die verwendet werden kann, um dieses Objekt oder Ereignis in Skriptausdrücken anzugeben.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>Mitglieder</td>
   <td>Geben Sie die Elemente der Ausschlussgruppe an. </td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>selectedMember</td>
   <td>Gibt das ausgewählte Element einer Ausschlussgruppe zurück.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>execCalculate</td>
   <td>Führt Skripten für das calculate-Ereignis des angegebenen Objekts und etwaiger untergeordneter Objekte aus.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>calculate</td>
   <td>Das calculate -Objekt steuert die Berechnung des Werts eines Felds.<br /> </td>
   <td>Ohne</td>
  </tr>
 </tbody>
</table>

## Bogen {#arc}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<strong></strong></strong></td>
   <td><strong>Beschreibung<strong></strong></strong></td>
   <td><strong>Ausnahme<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge -Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie Farbe, Cap usw. werden nicht unterstützt. </td>
  </tr>
 </tbody>
</table>

## border {#border}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft<strong></strong></strong></td>
   <td><strong>Beschreibung<strong></strong></strong></td>
   <td><strong>Ausnahme<strong></strong></strong></td>
  </tr>
  <tr>
   <td>edge</td>
   <td>Das edge -Objekt beschreibt einen Bogen, eine Linie oder eine Seite eines Rahmens oder Rechtecks.<br /> </td>
   <td>Attribute wie Farbe, Cap usw. werden nicht unterstützt. </td>
  </tr>
 </tbody>
</table>

## $layout {#layout}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Ausnahme</strong></td>
  </tr>
  <tr>
   <td>h</td>
   <td>Bestimmt die Höhe eines angegebenen Formularentwurfsobjekts.<br /> </td>
   <td>
    <ul>
     <li>Die Eigenschaft "Höhe"(h) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter "Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt"wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>w</td>
   <td>Bestimmt die Breite eines angegebenen Formularentwurfsobjekts.</td>
   <td>
    <ul>
     <li>Die Eigenschaft "Breite"(w) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter "Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt"wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>x</td>
   <td>Bestimmt die X-Koordinate eines angegebenen Formularentwurfsobjekts relativ zum übergeordneten Objekt.</td>
   <td>
    <ul>
     <li>Die Eigenschaft "X-Koordinate"(x) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter "Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt"wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>y</td>
   <td>Bestimmt die Y-Koordinate eines angegebenen Formularentwurfsobjekts relativ zum übergeordneten Objekt.</td>
   <td>
    <ul>
     <li>Die Eigenschaft Y-Koordinate (y) wird für Seiten- und Inhaltsbereiche nicht unterstützt. </li>
     <li>Parameter "Offset vom ersten Inhaltsbereich, in dem das XFA-Formularobjekt auftritt"wird nicht unterstützt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>pagecount</td>
   <td>Bestimmt die Anzahl der Seiten des aktuellen Formulars.</td>
   <td>
    <ul>
     <li>Die Methode layout.pageCount() gibt unterschiedliche Werte für PDF- und HTML-Formulare zurück.</li>
     <li>Wenn die Seitenzahl durch Ausblenden eines Objekts verringert wird, gibt die Methode abspagecount einen falschen Wert zurück.<br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>pageContent</td>
   <td>Ruft Formularentwurfsobjekttypen von einer angegebenen Seite eines Formulars ab.</td>
   <td>Ohne</td>
  </tr>
  <tr>
   <td>absPageCount</td>
   <td>Bestimmt die Seitenzahl des aktuellen Formulars.</td>
   <td>
    <ul>
     <li>Die Methode layout.pageCount() gibt unterschiedliche Werte für PDF- und HTML-Formulare zurück.</li>
     <li>Wenn die Seitenzahl durch Ausblenden eines Objekts verringert wird, gibt die Methode abspagecount einen falschen Wert zurück.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Elemente {#items}

| **Eigenschaft** | **Beschreibung** | **Ausnahme** |
|---|---|---|
| presence | Gibt die Sichtbarkeit eines Objekts an. | Ohne |

## FormCalc {#formcalc}

FormCalc ist eine XFA-spezifische Sprache zum Erstellen von e-form-zentrierten Logiken und Berechnungsstämmen. FormCalculation stellt einen leistungsstarken Satz von Build-Funktionen bereit.

### Von FormCalc unterstützte Funktionen {#formcalc-supported-functions}

### FormCalc-Ausdrucksunterstützung {#formcalc-expression-support}

<table>
 <tbody>
  <tr>
   <td><strong>Kategorie </strong></td>
   <td><strong>Beschreibung </strong></td>
   <td><strong>Beispiel </strong></td>
  </tr>
  <tr>
   <td>Einfacher Ausdruck</td>
   <td>Addieren, subtrahieren, multiplizieren, dividieren und Klammern</td>
   <td>(a+b)*3</td>
  </tr>
  <tr>
   <td>Variablendeklaration</td>
   <td>Variable definieren</td>
   <td>var a<br /> var a=3<br /> a=3</td>
  </tr>
  <tr>
   <td>Logischer Ausdruck</td>
   <td>
    <ul>
     <li>Logik (und/oder)</li>
     <li>Vergleich (größer/kleiner/gleich)</li>
    </ul> </td>
   <td>A oder 1<br /> 1 &lt;&gt; 2<br /> A NE B<br /> A oder 1<br /> 1 &lt;&gt; 2<br /> A NE B</td>
  </tr>
  <tr>
   <td>If-Ausdruck</td>
   <td><br type="_moz" /> </td>
   <td>if (a&gt;b) then 2 endif</td>
  </tr>
  <tr>
   <td>Zeit</td>
   <td><br type="_moz" /> </td>
   <td>while (i lt 5) do i = i + 1 endwhile</td>
  </tr>
  <tr>
   <td> für </td>
   <td><br type="_moz" /> </td>
   <td>for i = 100 downto 1 <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>for each</td>
   <td><br type="_moz" /> </td>
   <td>for each i in (1, 2, 3) <br /> do s = s + i endfor</td>
  </tr>
  <tr>
   <td>Funktionsdeklaration</td>
   <td>Definieren einer benutzerdefinierten Funktion in FormCalc</td>
   <td>func foo(n) do var f = n endfunc</td>
  </tr>
 </tbody>
</table>

### Acrobat API-Unterstützung {#acrobat-api-support}

1. **Arithmetische Funktionen**

   1. Abs()
   1. Avg()
   1. Obergrenze()
   1. Anzahl()
   1. Basis()
   1. Maximal()
   1. Min()
   1. Mod()
   1. Runden()
   1. Summe()

1. **Wissenschaftliche Funktionen**

   1. Acos()
   1. Asin()
   1. Atan()
   1. Atan2()
   1. Cos()
   1. Sin()
   1. Ocker()
   1. Exp()
   1. Protokoll()
   1. Pow()
   1. Sqrt()
   1. Deg2Rad()
   1. Rad2Deg()
   1. Pi()

1. **Finanzfunktionen**

   1. Apr()
   1. Cterm()
   1. Fv()
   1. Ipmt()
   1. Npv()
   1. Pmt()
   1. Ppmt()
   1. Pv()
   1. Rate()
   1. Begriff()

1. **Logische Funktionen**

   1. Choose()
   1. If()
   1. Oneof()
   1. In()

1. **Zeichenfolgen-Funktionen**

   1. Bei()
   1. Concat()
   1. Linksbündig()
   1. Len()
   1. Lower()
   1. Ltrim()
   1. Ersetzen()
   1. Richtig()
   1. Rtrim()
   1. Bereich()
   1. Stuff()
   1. Substr()
   1. Upper()
   1. WordNum()

1. **Datum und Uhrzeit**

   1. Datum()
   1. num2date()
   1. DateFmt()

<table>
 <tbody>
  <tr>
   <td><strong>API</strong></td>
   <td><strong>Beschreibung</strong></td>
   <td><strong>Abweichung</strong></td>
  </tr>
  <tr>
   <td>console.println()</td>
   <td>Diese Acrobat-API gibt die Ausgabe an die JavaScript-Konsole aus.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.alert()</td>
   <td>Diese Acrobat-API sendet eine Warnmeldung als JavaScript-Popup.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.beep()</td>
   <td>Lässt das System einen Ton abspielen.</td>
   <td>Es wird keine Aktion ausgeführt.</td>
  </tr>
  <tr>
   <td>app.execDialog()</td>
   <td>Stellt ein modales Dialogfeld für den Benutzer bereit. Modale Dialogfelder müssen vom Benutzer geschlossen werden, bevor die Host-Anwendung direkt erneut verwendet werden kann.</td>
   <td>Es wird keine Aktion ausgeführt.<br /> </td>
  </tr>
  <tr>
   <td>app.launchURL()</td>
   <td>Startet eine URL in einem Browserfenster.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setInterval()</td>
   <td>Gibt ein JavaScript-Skript und einen Zeitraum an. Das Skript wird jedes Mal ausgeführt, wenn der Zeitraum abgelaufen ist. Der Rückgabewert dieser Methode muss in einer JavaScript-Variablen gespeichert werden. Andernfalls unterliegt das Intervallobjekt der Garbage Collection, wodurch die Uhr angehalten wird. Um die periodische Ausführung zu beenden, übergeben Sie das zurückgegebene Intervallobjekt an clearInterval.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.setTimeOut()</td>
   <td>Gibt ein JavaScript-Skript und einen Zeitraum an. Das Skript wird nur einmal nach Ablauf des Zeitraums ausgeführt. Der Rückgabewert dieser Methode muss in einer JavaScript-Variablen gespeichert werden. Andernfalls unterliegt das Zeitüberschreitungsobjekt der Garbage Collection, wodurch die Uhr angehalten wird. Um das Timeout-Ereignis abzubrechen, übergeben Sie das zurückgegebene Timeout-Objekt an clearTimeOut.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.clearInterval()</td>
   <td>Bricht ein zuvor registriertes Intervall ab, das ursprünglich von der setInterval-Methode festgelegt wurde.</td>
   <td>In HTML5-Formularen funktioniert die API nicht ordnungsgemäß.</td>
  </tr>
  <tr>
   <td>app.clearTimeOut()</td>
   <td>Bricht ein zuvor registriertes Zeitüberschreitungsintervall ab. Ein solches Intervall wird zunächst von setTimeOut festgelegt.</td>
   <td>In HTML5-Formularen funktioniert die API nicht ordnungsgemäß.<br /> </td>
  </tr>
  <tr>
   <td>app.eval()</td>
   <td>Führt ein bestimmtes Skript aus.</td>
   <td> </td>
  </tr>
  <tr>
   <td>app.activeDocs</td>
   <td>Ein Array, das das Doc -Objekt für jedes aktive Dokument enthält. Wenn keine Dokumente aktiv sind, gibt activeDocs nichts zurück. Das heißt, es weist dasselbe Verhalten wie d = new Array(0) im Kern-JavaScript auf.</td>
   <td>Gibt ein leeres Array für HTML5-Formulare zurück.</td>
  </tr>
  <tr>
   <td>app.calculate</td>
   <td>Wenn "true"(Standardwert), können Berechnungen durchgeführt werden. Wenn "false", sind Berechnungen nicht zulässig.</td>
   <td>Immer true für HTML5 Forms.</td>
  </tr>
  <tr>
   <td>app.constants</td>
   <td>Ein Wrapper-Objekt zum Halten verschiedener Konstantenwerte. Derzeit gibt diese Eigenschaft ein Objekt mit einer einzelnen Eigenschaft "align"zurück.</td>
   <td>HTML5-Formulare geben ein leeres align-Objekt zurück.</td>
  </tr>
  <tr>
   <td>app.focusRect</td>
   <td>Aktiviert und deaktiviert das Fokusrechteck. Das Fokusrechteck ist die schwache gepunktete Linie um Schaltflächen, Kontrollkästchen, Optionsfelder und Signaturen, die angibt, dass das Formularfeld den Tastaturfokus hat. Der Wert true aktiviert das Fokusrechteck.</td>
   <td>Für HTML5-Formulare immer "true".</td>
  </tr>
  <tr>
   <td>app.formsVersion</td>
   <td>Die Versionsnummer der Viewer Forms-Software. Überprüfen Sie diese Eigenschaft, um festzustellen, ob Objekte, Eigenschaften oder Methoden in neueren Versionen der Software verfügbar sind, wenn Sie die Abwärtskompatibilität in Ihren Skripten beibehalten möchten.</td>
   <td>Immer 11.001.</td>
  </tr>
  <tr>
   <td>app.language</td>
   <td>Die Sprache des ausgeführten Acrobat-Viewers.</td>
   <td>Für HTML5-Formulare immer "ENU".</td>
  </tr>
 </tbody>
</table>

## Unterstützte XFA-Ereignisse {#supported-xfa-events}

Die folgenden clientseitigen XFA-Ereignisse werden unterstützt:

* Initialisieren
* Validieren
* Berechnen
* Klicken Sie auf
* Geben Sie ein
* Beenden
* Änderung
* ValidationState

>[!NOTE]
>
>HTML5-Formulare werden clientseitig (im Browser) wiedergegeben. Clientseitig verwenden **validate** und **calculate** Skripten anstelle von serverseitigen Skripten.
