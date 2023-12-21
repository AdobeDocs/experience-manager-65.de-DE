---
title: Erstellen von CSS-Stilen für HTML5-Formulare
description: Erfahren Sie, wie Sie das Erscheinungsbild von HTML5-Formularen ändern können, indem Sie die CSS-Klasse ändern, die mit dem HTML-Formularelement verknüpft ist.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: a8d986ab-2a4c-488b-957e-4606f7391bd3
feature: HTML5 Forms
exl-id: 8cc90ff7-284e-41cd-bfda-7fa09371e270
source-git-commit: 524475c8f9dbd02bae30ecd558a376505fbe0aed
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 33%

---

# Erstellen von CSS-Stilen für HTML5-Formulare {#creating-css-styles-for-html-forms}

HTML5-Ausgabedarstellung einer XFA-basierten Formularvorlage besteht aus mehreren HTML-Elementen. Diese Elemente werden in einer Reihenfolge angeordnet. Jedes Element hat klar definierte CSS-Klassen. Sie können diese CSS-Klasse verwenden, um das Erscheinungsbild eines Elements auszuwählen und zu ändern.

>[!NOTE]
>
>Ändern Sie in den CSS-Klassen nicht den Wert der Attribute für Breite, Höhe, Rahmendicke, Oben, Links, Rechts, Unten, Abstand, Rand und andere Position und Größe. Jede Änderung der Position und der Größenattribute bringt Änderungen am Layout des Formulars mit sich.

## CSS-Klassen für Elemente  {#css-classes-nbsp-for-elements-nbsp}

Jedes Element enthält klar definierte CSS-Klassen. Sie können diese Klassen ändern, um das Erscheinungsbild eines Elements zu ändern. Mit Ausnahme des Feld- und Zeichenelements hat jedes Element zwei CSS-Klassen: Type-Klasse und Name-Klasse.

* Die **Typ-Klasse** stellt den Typ des XFA-Feldes dar. Sie können die `type`-Klasse außer Kraft setzen, um den Stil aller Elemente eines bestimmten Typs zu ändern.

* Die **Name-Klasse:** entspricht dem Namen des XFA-Feldes. Sie können die `name`-Klasse überschreiben, um einen benutzerdefinierten zu ändern und auf ein Element anzuwenden.

>[!NOTE]
>
>Einige XFA-Elemente haben keinen Namen. Um die Stile solcher Komponenten zu ändern, ändern Sie alle Komponenten dieses Typs.

Für die Seiten, die nicht in AEM Forms Designer benannt sind, werden die Seiten in einem HTML5-Formular in der steigenden Reihenfolge ihrer Anzahl benannt. Beispiel: Für ein HTML5-Formular mit zwei Seiten werden die Seiten Seite1, Seite2 benannt.

## Feldelement {#field-element}

Das Feldelement enthält zwei verschachtelte Elemente: Widget und Beschriftung.

**Widget-Element**

Das Widget-Element enthält das Element der Benutzeroberfläche für die Interaktion mit Benutzern. Es enthält drei CSS-Klassen:

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

Neben der type- und name-Klasse enthält die Feldkomponente auch eine zusätzliche CSS-Klasse mit dem Namen **subtype**. Ein Untertyp gibt an, welcher Feldtyp es ist, z. B. NumericField, DateField, TextField. Sie können die Untertypklasse überschreiben, um die Formatierung aller Felder des Typs &quot;Untertyp&quot;zu ändern.

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
   <td>Benutzerdefinierter Name<br /> oder<br /> Seite&lt;pagenumber&gt; (Standard)</td>
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
   <td>Beschriftung</td>
   <td>caption</td>
   <td>nicht vorhanden</td>
  </tr>
  <tr>
   <td>Widget</td>
   <td>Widget</td>
   <td>Der Widget-Entwickler definiert sie (für benutzerdefinierte Widgets siehe die Tabelle im folgenden Abschnitt)</td>
  </tr>
 </tbody>
</table>

## CSS-Klassen für verschiedene Felder {#css-classes-for-different-fields}

AEM Forms Designer unterstützt verschiedene Feldtypen in einem Formular wie NumericField, DecimalField und Date Field. Alle diese Felder in HTML enthalten die oben genannten CSS-Klassen. Je nach Feldtyp enthalten sie auch einige zusätzliche Klassen.

Jedem Feld ist ein Widget zugeordnet, das das UI-Element darstellt. Die Klassen der einzelnen Felder und die mit jedem Feld verknüpften Widgets sind unten aufgeführt.

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

Mit AEM Forms Designer können Sie statische Zeichenelemente wie Text und Bilder einfügen. Für jedes Zeichenelement wird eine separate CSS-Klasse mit diesem Element verknüpft. Die Liste der CSS-Klassen für Zeichenelemente ist unten aufgeführt. Jedem draw-Element ist eine draw-Klasse zugeordnet.

| **Zeichentyp** | **CSS-Klasse** |
|---|---|
| Text | text |
| Bild | image |
| Rechteck | Rechteck |
| Line | Zeile |

## Formatieren anderer Formularteile {#styling-other-parts-of-the-form}

Neben dem Aussehen der Benutzerflächen-Komponenten im HTML-Formular können Sie auch den Stil von Elementen wie Inline-Fehler, Inline-Warnungen und Felder mit Überprüfungsfehlern ändern.

`Styling Inline Errors`

Wenn die Überprüfung eines Felds zu einem Fehler führt, wird ein Inline-Fehler angezeigt, wenn das Feld aktiv ist. Um den Stil von Inline-Fehlern zu ändern, überschreiben Sie die CSS-ID **error-msg**.

`Styling Inline Warnings`

Wenn die Überprüfung eines Felds zu einer Warnung führt, wird eine Inline-Warnung angezeigt, wenn das Feld aktiv ist. Um den Stil dieser Inline-Warnungen zu ändern, überschreiben Sie die CSS-ID **warning-msg**.

`Styling Fields with Validation Errors`

Wenn die Überprüfung eines Feldes fehlschlägt, wird der Stil des Widgets geändert. Diese Änderung des Stils wird ausgeführt, indem die CSS-Klasse **widgetError** auf die Widget-Komponente angewendet wird. Um den Standardstil zu ändern, muss die Klasse **widgetError** außer Kraft gesetzt werden.
