---
title: Erstellen von CSS-Stilen für HTML5-Formulare
seo-title: Erstellen von CSS-Stilen für HTML5-Formulare
description: Erfahren Sie, wie Sie das Erscheinungsbild von HTML5-Formularen ändern, indem Sie die CSS-Klasse ändern, die mit dem HTML-Formularelement verknüpft ist.
seo-description: Erfahren Sie, wie Sie das Erscheinungsbild von HTML5-Formularen ändern, indem Sie die CSS-Klasse ändern, die mit dem HTML-Formularelement verknüpft ist.
uuid: 43c689b4-243c-43de-a8be-1eef10d75295
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: a8d986ab-2a4c-488b-957e-4606f7391bd3
feature: Mobile Forms
exl-id: 8cc90ff7-284e-41cd-bfda-7fa09371e270
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 90%

---

# Erstellen von CSS-Stilen für HTML5-Formulare {#creating-css-styles-for-html-forms}

HTML5-Wiedergabe eines XFA-basierten Formularvorlage besteht aus mehreren HTML-Elementen. Diese Elemente werden in einer Reihenfolge angeordnet. Jedes Element hat klar definierte CSS-Klassen. Sie können die CSS-Klassen verwenden, um das Aussehen eines Elements zu ändern.

>[!NOTE]
>
>In den CSS-Klassen dürfen die Werte der Attribute für Breite, Höhe, Rahmenstärke, oberen Bereich, linken Bereich, rechten Bereich, unteren Bereich, Abstand und Rand nicht geändert werden. Änderungen an der Position und den Größenattributen ziehen Änderungen am Layout des Formulars nach sich.

## CSS-Klassen für Elemente  {#css-classes-nbsp-for-elements-nbsp}

Jedes Element enthält klar definierte CSS-Klassen. Die Klassen können geändert werden, um das Aussehen eines Elements zu ändern. Mit Ausnahme des Feld- und Zeichenelements hat jedes Element zwei CSS-Klassen: Type-Klasse und Name-Klasse.

* Die **Typ-Klasse** stellt den Typ des XFA-Feldes dar. Sie können die `type`-Klasse außer Kraft setzen, um den Stil aller Elemente eines bestimmten Typs zu ändern.

* Die **Name-Klasse:** entspricht dem Namen des XFA-Feldes. Sie können die `name`-Klasse überschreiben, um einen benutzerdefinierten zu ändern und auf ein Element anzuwenden.

>[!NOTE]
>
>Manche XFA-Elemente haben keinen Namen. Um den Stil dieser Komponenten zu ändern, müssen Sie alle Komponenten dieses Typs ändern.

Die Seiten, die in AEM Forms Designer nicht benannt wurden, werden in einem HTML5-Formular in aufsteigenden Reihenfolge ihrer Zahl benannt. Beispiel: Für ein HTML5-Formular mit zwei Seiten werden die Seiten Seite1, Seite2 benannt.

## Feldelement {#field-element}

Das Feldelement enthält zwei verschachtelte Elemente: Widget und Beschriftung.

**Widget-Element**

Das Widget-Element enthält das Element der Benutzeroberfläche für die Interaktion mit dem Benutzer. Es enthält drei CSS-Klassen:

* **Widget**: Jedes Widget hat diese Klasse.
* **name**: Alle Widgets, die mit AEM ausgeliefert werden, enthalten die name-Klasse des Widgets. Für benutzerdefinierte Widgets stellt der Widget-Entwickler die name-Klasse bereit.
* **Typ**: Jedes Widget verfügt über ein Element der Benutzeroberfläche. Diese Klasse definiert den Typ des Elements der Benutzeroberfläche.

```xml
<!--field with caption-->
<div class="field numericfield NumericField3 ">
     <div class="caption">
        caption content
     </div>
     <div class="widget numericfieldwidget numericInput">
       widget content
     </div>
</div>

<!--field without caption-->
<div class="widget numericfieldwidget numericInput">
   widget content
</div>
```

Zusätzlich zu der type- und name-Klasse enthält die Feldkomponente noch eine weitere CSS-Klasse: **subtype**. Eine subtype-Klasse zeigt an, welcher Feldtyp es ist, z. B. NumericField, DateField, TextField. Sie können die subtype-Klasse außer Kraft setzen, um die Stile aller Felder des Typs „subtype“ zu ändern.

## CSS-Klassen für verschiedene Komponenten  {#css-classes-for-different-components}

<table>
 <tbody>
  <tr>
   <td><strong>Komponente</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Name</strong></td>
  </tr>
  <tr>
   <td>Seite </td>
   <td>page</td>
   <td>Benutzerdefinierter Name<br /> oder<br /> Seite&lt;Seitenzahl&gt; (Standard)</td>
  </tr>
  <tr>
   <td>Inhaltsbereich</td>
   <td>contentarea</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Teilformular</td>
   <td>subform</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Ausschlussgruppe</td>
   <td>exclgroup</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Zeichenelement</td>
   <td>draw</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Feld</td>
   <td>field</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Beschriftung</td>
   <td>caption</td>
   <td>nicht vorhanden</td>
  </tr>
  <tr>
   <td>Widget</td>
   <td>Widget</td>
   <td>Vom Widget-Entwickler definiert (Informationen zu benutzerdefinierten Widgets finden Sie im folgenden Abschnitt)</td>
  </tr>
 </tbody>
</table>

## CSS-Klassen für verschiedene Felder  {#css-classes-for-different-fields}

Der AEM Forms Designer unterstützt unterschiedliche Typen von Feldern in einem Formular wie NumericField, DecimalField und DateField. All diese Felder enthalten in HTML die oben genannten CSS-Klassen. Je nach Typ des Feldes enthalten sie auch ein paar zusätzliche Klassen.

Jedes Feld verfügt über ein zugehöriges Widget, das das Benutzeroberflächen-Element darstellt. Die Klassen jedes Feldes und die mit den Feldern verknüpfte Widgets sind unten aufgeführt.

<table>
 <tbody>
  <tr>
   <td><strong>Feldtyp</strong></td>
   <td><strong>Untertyp</strong></td>
   <td><strong>Widget-Name</strong></td>
   <td><strong>Widget-Typ</strong></td>
   <td><strong>HTML-Benutzeroberflächen-Tag</strong></td>
  </tr>
  <tr>
   <td>Schaltfläche<br type="_moz" /> </td>
   <td>nicht vorhanden</td>
   <td>xfaButton<br type="_moz" /> </td>
   <td>buttonfieldwidget<br type="_moz" /> </td>
   <td>input type=button<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>CheckButton<br type="_moz" /> </td>
   <td>checkboxfield<br /> </td>
   <td>XfaCheckBox<br type="_moz" /> </td>
   <td>checkboxfieldwidget<br type="_moz" /> </td>
   <td>input type=checkbox<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DateField<br type="_moz" /> </td>
   <td>datefield<br type="_moz" /> </td>
   <td>dateField<br type="_moz" /> </td>
   <td>datefieldwidget<br type="_moz" /> </td>
   <td>input type=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DateTimeField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfieldwidget</td>
   <td>input type=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DecimalField<br type="_moz" /> </td>
   <td>numericfield<br type="_moz" /> </td>
   <td>numericInput<br type="_moz" /> </td>
   <td>numericfieldwidget<br type="_moz" /> </td>
   <td>input type=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DropDown<br type="_moz" /> </td>
   <td>choicelist<br type="_moz" /> </td>
   <td>dropDownListWidget<br type="_moz" /> </td>
   <td>choicelistwidget<br type="_moz" /> </td>
   <td>select</td>
  </tr>
  <tr>
   <td>ListBox<br type="_moz" /> </td>
   <td>choicelist<br type="_moz" /> </td>
   <td>listBoxWidget<br type="_moz" /> </td>
   <td>choicelistwidget<br type="_moz" /> </td>
   <td>ol</td>
  </tr>
  <tr>
   <td>NumericField<br type="_moz" /> </td>
   <td>numericfield<br type="_moz" /> </td>
   <td>numericInput<br type="_moz" /> </td>
   <td>numericfieldwidget<br type="_moz" /> </td>
   <td>input type=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>PasswordField<br type="_moz" /> </td>
   <td>passwordfield<br type="_moz" /> </td>
   <td>defaultWidget<br type="_moz" /> </td>
   <td>passwordfieldwidget<br type="_moz" /> </td>
   <td>input type=password<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>RadioButton<br type="_moz" /> </td>
   <td>radiofield<br type="_moz" /> </td>
   <td>XfaCheckBox<br type="_moz" /> </td>
   <td>radiofieldwidget<br type="_moz" /> </td>
   <td>input type=radio<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>TextField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfieldwidget<br type="_moz" /> </td>
   <td>input type=text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>TimeField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfieldwidget<br type="_moz" /> </td>
   <td>input type=text<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

## CSS-Klassen für verschiedene Zeichenelemente {#css-classes-for-different-draw-elements}

Mithilfe des AEM Forms Designer können Sie statische Zeichenelemente wie Text und Bilder einfügen. Jedes Zeichenelement ist mit einer separaten CSS-Klasse verknüpft. Die Liste der CSS-Klassen für Zeichenelemente ist unten aufgeführt. Jedes Zeichnenelement ist mit einer draw-Klasse verknüpft.

| **Zeichentyp** | **CSS-Klasse** |
|---|---|
| Text | text |
| Bild | image |
| Rechteck | rectangle |
| Linie | Zeile |

## Gestalten des Stils anderer Formularteile {#styling-other-parts-of-the-form}

Neben dem Erscheinungsbild von Benutzeroberflächen-Komponenten im HTML-Formular können Sie den Stil von Elementen wie Inline-Fehler, Inline-Warnungen und Felder mit Überprüfungsfehlern ändern.

`Styling Inline Errors`

Wenn die Überprüfung eines Feldes einen Fehler ergibt, wird ein Inline-Fehler angezeigt, wenn das Feld aktiv ist. Um den Stil von Inline-Fehlern zu ändern, muss die CSS-ID **error-msg** außer Kraft gesetzt werden.

`Styling Inline Warnings`

Wenn die Überprüfung eines Feldes eine Warnung ergibt, wird eine Inline-Warnung angezeigt, wenn das Feld aktiv ist. Um den Stil von Inline-Warnungen zu ändern, muss die CSS-ID **warning-msg** außer Kraft gesetzt werden.

`Styling Fields with Validation Errors`

Wenn die Überprüfung eines Feldes fehlschlägt, wird der Stil des Widgets geändert. Diese Stiländerung erfolgt durch Anwenden einer CSS-Klasse **widgetError** auf die Widget-Komponente. Um den Standardstil zu ändern, überschreiben Sie die Klasse **widgetError** .
