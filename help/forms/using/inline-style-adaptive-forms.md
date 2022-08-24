---
title: Inline-Stile für Komponenten adaptiver Formulare
seo-title: Inline CSS properties for adaptive form components
description: Sie können für ein adaptives Formular benutzerdefinierte Stile und für einzelne Komponenten auch Inline-CSS-Eigenschaften anwenden.
seo-description: While you can apply custom styles on an adaptive form, you can also apply inline CSS properties on individual components of an adaptive form.
uuid: e863780e-2250-4bea-9569-22be5638d54e
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 21dec713-c76d-408b-baea-fc585377b429
docset: aem65
feature: Adaptive Forms
exl-id: 67cfecb8-c31d-4192-904d-7bfaa1a31ea5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 100%

---

# Inline-Stile für Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

Sie können die Darstellung und das Design eines adaptiven Formulars definieren, indem Sie die Stile mithilfe des Designs mithilfe des [Designeditors](../../forms/using/themes.md) angeben. Außerdem können Sie Inline-CSS-Stile auf einzelne Komponenten anwenden und die Änderungen direkt in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

Hinzufügen von Inline-Stilen zu einer Komponente:

1. Öffnen Sie das Formular im Formular-Editor und ändern Sie den Modus in Stilmodus. Um den Stilmodus zu aktivieren, tippen Sie in der Symbolleiste der Seite auf ](assets/canvas-drop-down.png)Arbeitsfläche-Dropdown![ > **Stil**.
1. Wählen Sie eine Komponente auf der Seite aus und tippen Sie auf die Schaltfläche „Bearbeiten“ ![Bearbeiten-Schaltfläche](assets/edit-button.png). In der Randleiste geöffnete Stileigenschaften.

   Sie können auch Komponenten aus der Hierarchiestruktur in der Seitenleiste auswählen. Die Hierarchiestruktur für das Formular ist als „Formularobjekte“ in der Seitenleiste verfügbar.

   Sie können auch Komponenten in der Seitenleiste auswählen. Im Modus Stil können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Allerdings führt „Formularobjekte“ in der Seitenleiste Komponenten wie Felder und Bereiche auf. Felder und Bereiche sind generische Komponenten, die Komponenten wie Textfelder und Optionsschaltflächen enthalten können.

   Wenn Sie eine Komponente aus der Seitenleiste auswählen, sehen Sie alle aufgelisteten Unterkomponenten sowie die Eigenschaften der ausgewählten Komponente. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Randleiste, um CSS-Eigenschaften festzulegen. Sie können Eigenschaften wie die folgenden angeben:

   * Abmessungen und Position (Anzeigeeinstellung, Auffüllung, Höhe, Breite, Ränder, Position, Z-Index, „Float“, „Clear“, Überlauf)
   * Text (Schriftfamilie, Stärke, Farbe, Größe, Zeilenhöhe und Ausrichtung)
   * Hintergrund (Bild und Verlauf, Hintergrundfarbe)
   * Rahmen (Breite, Stil, Farbe, Radius)
   * Effekte (Schatten, Deckkraft)
   * Erweitert (Ermöglicht das Schreiben benutzerdefinierten CSS für die Komponente)

1. Ebenso können Sie Stile auf andere Teile einer Komponente wie Widget, Beschriftung und Hilfe anwenden.
1. Tippen Sie auf **Fertig**, um die Änderungen zu bestätigen, oder auf **Abbrechen**, um die Änderungen zu verwerfen.

## Beispiel: Inline-Formatvorlagen für eine Feldkomponente {#example-inline-styles-for-a-field-component}

Die folgenden Bilder zeigen ein Textfeld, bevor und nachdem Inline-Stile darauf angewendet wurden.

![Textfeldkomponente vor der Anwendung von Inline-Formatierung](assets/no-style.png)

Textfeldkomponente vor der Anwendung von Inline-Stil-Eigenschaften

Beachten Sie die Änderung im Textfeldstil in der folgenden Abbildung, nachdem die folgenden CSS-Eigenschaften angewendet wurden.

<table>
 <tbody>
  <tr>
   <td><p>Selektor</p> </td>
   <td><p>CSS-Eigenschaft</p> </td>
   <td><p>Wert</p> </td>
   <td><p>Ergebnis</p> </td>
  </tr>
  <tr>
   <td><p>Feld</p> </td>
   <td><p>border</p> </td>
   <td><p>Border width =2px</p> <p>Border style=Solid</p> <p>Border color=#1111</p> </td>
   <td><p>Erstellt einen schwarzen, 2px breiten Rahmen um das Feld</p> </td>
  </tr>
  <tr>
   <td><p>Textfeld</p> </td>
   <td><p>background-color</p> </td>
   <td><p>#6495ED</p> </td>
   <td><p>Ändert die Hintergrundfarbe zu Kornblumenblau (#6495ED)</p> <p>Hinweis: Sie können einen Farbnamen oder seinen Hexadezimalcode im Wertefeld angeben.</p> </td>
  </tr>
  <tr>
   <td><p>Bezeichnung</p> </td>
   <td><p>Abmessungen &amp; Position &gt; width</p> </td>
   <td><p>100px</p> </td>
   <td><p>Stellt die Breite als 100px für die Beschriftung ein</p> </td>
  </tr>
  <tr>
   <td>Feld Hilfe Symbol</td>
   <td>Text &gt; Schriftfarbe</td>
   <td>#2ECC40</td>
   <td>Ändert die Farbe des Hilfesymbols.</td>
  </tr>
  <tr>
   <td><p>Lange Beschreibung</p> </td>
   <td><p>text-align</p> </td>
   <td><p>center</p> </td>
   <td><p>Richtet die Langbeschreibung für die Hilfe mittig aus</p> </td>
  </tr>
 </tbody>
</table>

![Textfelddesign nach der Anwendung von Inline-Formatierung](assets/applied-style.png)

Textfeldkomponente nach der Anwendung der Inline-Stil-Eigenschaften

Wenn Sie den obigen Schritten folgen, können Sie andere Komponenten wie Bereiche, Sendeschaltflächen und Optionsschaltflächen auswählen und formatieren.

>[!NOTE]
>
>Designeigenschaften variieren je nach ausgewählter Komponente.
