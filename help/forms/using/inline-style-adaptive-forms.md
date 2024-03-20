---
title: Inline-Stile für Komponenten adaptiver Formulare
description: Sie können zwar benutzerdefinierte Stile auf ein adaptives Formular anwenden, Sie können aber auch Inline-CSS-Eigenschaften auf einzelne Komponenten eines adaptiven Formulars anwenden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 67cfecb8-c31d-4192-904d-7bfaa1a31ea5
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 77%

---

# Inline-Stile für Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/inline-style-adaptive-forms.html) |
| AEM 6.5 | Dieser Artikel |

Sie können das Erscheinungsbild und den Stil eines adaptiven Formulars definieren, indem Sie Stile angeben, indem Sie [Design-Editor](../../forms/using/themes.md). Außerdem können Sie Inline-CSS-Stile auf einzelne adaptive Formularkomponenten anwenden und die Änderungen sofort in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

So fügen Sie Inline-Stile zu einer Komponente hinzu:

1. Öffnen Sie das Formular im Formulareditor und ändern Sie den Modus in den Stilmodus. Um den Stilmodus zu aktivieren, tippen Sie in der Symbolleiste der Seite auf ](assets/canvas-drop-down.png)canvas-drop-down![ > **Stil**.
1. Wählen Sie eine Komponente auf der Seite aus und wählen Sie die Schaltfläche „Bearbeiten“ ![edit-button](assets/edit-button.png). In der Seitenleiste geöffnete Stileigenschaften.

   Sie können auch Komponenten aus der Hierarchiestruktur in der Seitenleiste auswählen. Die Hierarchiestruktur für das Formular ist als „Formularobjekte“ in der Seitenleiste verfügbar.

   Sie können auch eine Komponente in der Seitenleiste auswählen. Im Modus Stil können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Allerdings führt „Formularobjekte“ in der Seitenleiste Komponenten wie Felder und Bereiche auf. Felder und Bereiche sind generische Komponenten, die Komponenten wie Textfelder und Optionsschaltflächen enthalten können.

   Wenn Sie eine Komponente aus der Seitenleiste auswählen, werden alle aufgelisteten Unterkomponenten und die Eigenschaften der ausgewählten Komponente angezeigt. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Seitenleiste, um CSS-Eigenschaften festzulegen. Sie können Eigenschaften wie die folgenden angeben:

   * Abmessungen und Position (Anzeigeeinstellung, Auffüllung, Höhe, Breite, Ränder, Position, Z-Index, „Float“, „Clear“, Überlauf)
   * Text (Schriftfamilie, Stärke, Farbe, Größe, Zeilenhöhe und Ausrichtung)
   * Hintergrund (Bild und Verlauf, Hintergrundfarbe)
   * Rahmen (Breite, Stil, Farbe, Radius)
   * Effekte (Schatten, Deckkraft)
   * Erweitert (Ermöglicht das Schreiben benutzerdefinierten CSS für die Komponente)

1. Ebenso können Sie Stile auf andere Teile einer Komponente wie Widget, Beschriftung und Hilfe anwenden.
1. Wählen Sie **Fertig**, um die Änderungen zu bestätigen, oder **Abbrechen**, um die Änderungen zu verwerfen.

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
   <td><p>Dimensionen und Position &gt; Breite</p> </td>
   <td><p>100 px</p> </td>
   <td><p>Stellt die Breite für die Beschriftung auf 100 px ein</p> </td>
  </tr>
  <tr>
   <td>Feldhilfesymbol</td>
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
