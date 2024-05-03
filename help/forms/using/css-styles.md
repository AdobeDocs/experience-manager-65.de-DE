---
title: Erstellen von CSS-Stilen für HTML5-Formulare
description: Erfahren Sie, wie Sie das Erscheinungsbild von HTML5-Formularen ändern, indem Sie die CSS-Klasse ändern, die mit dem HTML-Formularelement verknüpft ist.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: a8d986ab-2a4c-488b-957e-4606f7391bd3
feature: HTML5 Forms
exl-id: 8cc90ff7-284e-41cd-bfda-7fa09371e270
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 100%

---

# Erstellen von CSS-Stilen für HTML5-Formulare {#creating-css-styles-for-html-forms}

Die HTML5-Wiedergabe einer XFA-basierten Formularvorlage besteht aus mehreren HTML-Elementen. Diese Elemente werden in einer Reihenfolge angeordnet. Jedes Element hat klar definierte CSS-Klassen. Sie können die CSS-Klassen verwenden, um das Erscheinungsbild eines Elements zu ändern.

>[!NOTE]
>
>In den CSS-Klassen dürfen die Werte der Attribute für Breite, Höhe, Rahmenstärke, oberen Bereich, linken Bereich, rechten Bereich, unteren Bereich, Abstand und Rand sowie für andere Positions- und Größenattribute nicht geändert werden. Änderungen an den Positions- und Größenattributen ziehen Änderungen am Layout des Formulars nach sich.

## CSS-Klassen für Elemente {#css-classes-nbsp-for-elements-nbsp}

Jedes Element enthält klar definierte CSS-Klassen. Sie können diese Klassen ändern, um das Erscheinungsbild eines Elements zu ändern. Mit Ausnahme des Feld- und Zeichenelements hat jedes Element zwei CSS-Klassen: Type-Klasse und Name-Klasse.

* Die **Typ-Klasse** stellt den Typ des XFA-Feldes dar. Sie können die `type`-Klasse außer Kraft setzen, um den Stil aller Elemente eines bestimmten Typs zu ändern.

* Die **Name-Klasse:** entspricht dem Namen des XFA-Feldes. Sie können die `name`-Klasse überschreiben, um einen benutzerdefinierten zu ändern und auf ein Element anzuwenden.

>[!NOTE]
>
>Manche XFA-Elemente haben keinen Namen. Um den Stil dieser Komponenten zu ändern, müssen Sie alle Komponenten dieses Typs ändern.

Die Seiten, die in AEM Forms Designer nicht benannt wurden, werden in einem HTML5-Formular in aufsteigenden Reihenfolge ihrer Zahl benannt. Beispiel: Für ein HTML5-Formular mit zwei Seiten werden die Seiten Seite1, Seite2 benannt.

## Feldelement {#field-element}

Das Feldelement enthält zwei verschachtelte Elemente: Widget und Beschriftung.

**Widget-Element**

Das Widget-Element enthält das Element der Benutzeroberfläche für die Interaktion mit den Benutzenden. Es enthält drei CSS-Klassen:

* **Widget:** Diese Klasse hat jedes Widget.
* **name**: Die „name“-Klasse enthalten alle Widgets von AEM. Für benutzerdefinierte Widgets stellt der Widget-Entwickler die name-Klasse bereit.
* **type**: Jedes Widget hat ein Benutzeroberflächenelement. Diese Klasse definiert den Typ des Elements der Benutzeroberfläche.

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

Zusätzlich zu den Klassen „type“ und „name“ enthält die Feldkomponente noch eine weitere CSS-Klasse: **subtype**. Eine subtype-Klasse zeigt an, um welchen Feldtyp es sich handelt, z. B. NumericField, DateField, TextField. Sie können die subtype-Klasse außer Kraft setzen, um die Stile aller Felder des Typs „subtype“ zu ändern.

## CSS-Klassen für verschiedene Komponenten {#css-classes-for-different-components}

<table>
 <tbody>
  <tr>
   <td><strong>Komponente</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Name</strong></td>
  </tr>
  <tr>
   <td>Seite</td>
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
   <td>Teilformular</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Ausschlussgruppe</td>
   <td>exclgroup</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Draw</td>
   <td>draw</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>Feld</td>
   <td>field</td>
   <td>Benutzerdefinierter Name</td>
  </tr>
  <tr>
   <td>caption</td>
   <td>caption</td>
   <td>nicht vorhanden</td>
  </tr>
  <tr>
   <td>Widget</td>
   <td>widget</td>
   <td>Von der Entwicklerin bzw. dem Entwickler des Widgets definiert (Informationen zu benutzerdefinierten Widgets finden Sie im folgenden Abschnitt.)</td>
  </tr>
 </tbody>
</table>

## CSS-Klassen für verschiedene Felder {#css-classes-for-different-fields}

Der AEM Forms Designer unterstützt unterschiedliche Typen von Feldern in einem Formular wie NumericField, DecimalField und DateField. All diese Felder in HTML enthalten die oben genannten CSS-Klassen. Je nach Feldtyp enthalten sie auch ein paar zusätzliche Klassen.

Jedes Feld verfügt über ein zugehöriges Widget, das das Benutzeroberflächen-Element darstellt. Die Klassen jedes Feldes und die mit den Feldern verknüpften Widgets sind unten aufgeführt.

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
   <td>inputtype = text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DateTimeField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfieldwidget</td>
   <td>inputtype = text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DecimalField<br type="_moz" /> </td>
   <td>numericfield<br type="_moz" /> </td>
   <td>numericInput<br type="_moz" /> </td>
   <td>numericfieldwidget<br type="_moz" /> </td>
   <td>inputtype = text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>DropDown<br type="_moz" /> </td>
   <td>choicelist<br type="_moz" /> </td>
   <td>dropDownListWidget<br type="_moz" /> </td>
   <td>choicelistwidget<br type="_moz" /> </td>
   <td>auswählen</td>
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
   <td>inputtype = text<br type="_moz" /> </td>
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
   <td>inputtype = text<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>TimeField<br type="_moz" /> </td>
   <td>textfield<br type="_moz" /> </td>
   <td>textField<br type="_moz" /> </td>
   <td>textfieldwidget<br type="_moz" /> </td>
   <td>inputtype = text<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

## CSS-Klassen für verschiedene Zeichenelemente {#css-classes-for-different-draw-elements}

Mithilfe des AEM Forms Designer können Sie statische Zeichenelemente wie Text und Bilder einfügen. Jedes Zeichenelement ist mit einer separaten CSS-Klasse verknüpft. Die Liste der CSS-Klassen für Zeichenelemente ist unten aufgeführt. Jedes Zeichenelement ist mit einer Zeichenklasse verknüpft.

| **Zeichentyp** | **CSS-Klasse** |
|---|---|
| Text | text |
| Bild | image |
| rectangle | rectangle |
| Line | Zeile |

## Gestalten des Stils anderer Formularteile {#styling-other-parts-of-the-form}

Neben dem Aussehen der Benutzerflächen-Komponenten im HTML-Formular können Sie auch den Stil von Elementen wie Inline-Fehler, Inline-Warnungen und Felder mit Überprüfungsfehlern ändern.

`Styling Inline Errors`

Wenn die Überprüfung eines Feldes einen Fehler ergibt, wird ein Inline-Fehler angezeigt, wenn das Feld aktiv ist. Um den Stil von Inline-Fehlern zu ändern, muss die CSS-ID **error-msg** überschrieben werden.

`Styling Inline Warnings`

Wenn die Überprüfung eines Feldes eine Warnung ergibt, wird eine Inline-Warnung angezeigt, wenn das Feld aktiv ist. Um den Stil von Inline-Warnungen zu ändern, muss die CSS-ID **warning-msg** überschrieben werden.

`Styling Fields with Validation Errors`

Wenn die Überprüfung eines Feldes fehlschlägt, wird der Stil des Widgets geändert. Diese Änderung des Stils wird ausgeführt, indem die CSS-Klasse **widgetError** auf die Widget-Komponente angewendet wird. Um den Standardstil zu ändern, muss die Klasse **widgetError** außer Kraft gesetzt werden.
