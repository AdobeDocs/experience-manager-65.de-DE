---
title: Inline-Stile für Komponenten adaptiver Formulare
description: Sie können zwar benutzerdefinierte Stile auf ein adaptives Formular anwenden, Sie können aber auch Inline-CSS-Eigenschaften auf einzelne Komponenten eines adaptiven Formulars anwenden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 67cfecb8-c31d-4192-904d-7bfaa1a31ea5
source-git-commit: d85fc98d9a31bc4014aef4311ba0f838c7ef619a
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 38%

---

# Inline-Stile für Komponenten adaptiver Formulare {#inline-styling-of-adaptive-form-components}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/inline-style-adaptive-forms.html) |
| AEM 6.5 | Dieser Artikel |

Sie können das Erscheinungsbild und den Stil eines adaptiven Formulars definieren, indem Sie Stile angeben, indem Sie [Design-Editor](../../forms/using/themes.md). Außerdem können Sie Inline-CSS-Stile auf einzelne adaptive Formularkomponenten anwenden und die Änderungen sofort in der Vorschau anzeigen. Inline-Stile überschreiben die Formatierung, die im Design bereitgestellt wird.

## Verwenden von Inline-CSS-Eigenschaften {#apply-inline-css-properties}

Hinzufügen von Inline-Stilen zu einer Komponente:

1. Öffnen Sie das Formular im Formular-Editor und ändern Sie den Modus in den Formatierungsmodus. Um den Stilmodus zu ändern, wählen Sie in der Seitensymbolleiste die Option ![Arbeitsfläche-Dropdown](assets/canvas-drop-down.png) > **Stil**.
1. Wählen Sie eine Komponente auf der Seite aus und klicken Sie auf die Schaltfläche &quot;Bearbeiten&quot; ![edit-button](assets/edit-button.png). Die Stileigenschaften werden in der Seitenleiste geöffnet.

   Sie können auch Komponenten aus der Formularhierarchie in der Seitenleiste auswählen. Die Hierarchie des Formulars ist als Formularobjekte in der Seitenleiste verfügbar.

   Sie können auch eine Komponente in der Seitenleiste auswählen. Im Modus Stil können Sie Komponenten sehen, die unter „Formularobjekte“ aufgeführt sind. Die Liste &quot;Formularobjekte&quot;in der Seitenleiste listet jedoch Komponenten wie Felder und Bereiche auf. Felder und Bedienfelder sind allgemeine Komponenten, die Komponenten wie Textfelder und Optionsfelder enthalten können.

   Wenn Sie eine Komponente aus der Seitenleiste auswählen, werden alle aufgelisteten Unterkomponenten und die Eigenschaften der ausgewählten Komponente angezeigt. Sie können eine bestimmte Unterkomponente auswählen und formatieren.

1. Klicken Sie auf eine Registerkarte in der Seitenleiste, um CSS-Eigenschaften anzugeben. Sie können Eigenschaften wie die folgenden angeben:

   * Abmessungen und Position (Anzeigeeinstellung, Auffüllung, Höhe, Breite, Ränder, Position, Z-Index, „Float“, „Clear“, Überlauf)
   * Text (Schriftfamilie, Stärke, Farbe, Größe, Zeilenhöhe und Ausrichtung)
   * Hintergrund (Bild und Verlauf, Hintergrundfarbe)
   * Rahmen (Breite, Stil, Farbe, Radius)
   * Effekte (Schatten, Deckkraft)
   * Erweitert (Ermöglicht das Schreiben benutzerdefinierten CSS für die Komponente)

1. Ebenso können Sie Stile auf andere Teile einer Komponente wie Widget, Beschriftung und Hilfe anwenden.
1. Auswählen **Fertig** zur Bestätigung der Änderungen oder **Abbrechen** , um die Änderungen zu verwerfen.

## Beispiel: Inline-Formatvorlagen für eine Feldkomponente {#example-inline-styles-for-a-field-component}

Die folgenden Bilder zeigen ein Textfeld, bevor und nachdem Inline-Stile darauf angewendet wurden.

![Textfeldkomponente vor der Anwendung von Inline-Formatierung](assets/no-style.png)

Textfeldkomponente vor dem Anwenden von Inline-Stil-Eigenschaften

Beachten Sie die Änderung des Textfeldstils, die in der folgenden Abbildung gezeigt wird, nachdem die folgenden CSS-Eigenschaften angewendet wurden.

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
   <td><p>Border width =2px</p> <p>Border style=Solid</p> <p>Rahmenfarbe=#1111</p> </td>
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
   <td>Feld Hilfe Symbol</td>
   <td>Text &gt; Schriftfarbe</td>
   <td>#2ECC40</td>
   <td>Ändert die Farbe des Hilfesymbol-Gesichts.</td>
  </tr>
  <tr>
   <td><p>Lange Beschreibung</p> </td>
   <td><p>text-align</p> </td>
   <td><p>Zentriert</p> </td>
   <td><p>Richtet die lange Beschreibung der Hilfe zentriert aus</p> </td>
  </tr>
 </tbody>
</table>

![Textfelddesign nach der Anwendung von Inline-Formatierung](assets/applied-style.png)

Textfeldkomponente nach dem Anwenden von Inline-Stileigenschaften

Mit den oben beschriebenen Schritten können Sie andere Komponenten wie Bedienfelder, Senden-Schaltflächen und Optionsfelder auswählen und formatieren.

>[!NOTE]
>
>Designeigenschaften variieren je nach ausgewählter Komponente.
