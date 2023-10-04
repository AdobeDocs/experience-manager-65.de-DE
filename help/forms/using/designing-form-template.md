---
title: Entwerfen von Formularvorlagen für HTML5-Formulare
description: AEM Forms kann XFA-Formularvorlagen im HTML5-Format wiedergeben. Formularentwickler können Formularvorlagen mit Designer entwerfen und die HTML5-Render-Funktion nutzen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: Mobile Forms
exl-id: 7c8d501f-c953-495e-8bac-1f66fd99c783
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 70%

---

# Entwerfen von Formularvorlagen für HTML5-Formulare{#designing-form-templates-for-html-forms}

Die HTML5 forms-Komponente in AEM kann XFA-Formularvorlagen im HTML5-Format wiedergeben. Formularentwickler können Formularvorlagen mit [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de) entwerfen und die HTML5-Renderfunktion nutzen. Diese Formularvorlagen können sich zusammen mit ihren Assets in AEM Repository oder Dateisystem befinden oder über HTTP verfügbar gemacht werden. Wenn Sie beabsichtigen, Ihre Formulare mithilfe von Forms Manager zu verwalten, müssen sich die Vorlagen und Assets im AEM-Repository befinden.

Obwohl das Verhalten von HTML5-Formularen und PDF-Formularen sich stark ähnelt, gibt es mehrere Funktionen in beiden Formaten, die nicht im anderen Format verfügbar sind. Beispielsweise ist die Anwendung von Barcodes auf einem PDF-Formular in Adobe Reader und auf einem Formular für Mobilgeräte unterschiedlich, ebenso wie es bei digitalen Signaturen Unterschiede gibt. Weitere Informationen zu diesen Unterschieden finden Sie unter [Funktionsunterschiede zwischen HTML5- und PDF-Formularen](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Allgemeine XFA-Funktionen finden Sie in den folgenden Best Practices und Richtlinien zum Entwerfen eines Formulars, das in beiden Formaten funktioniert.

## Best Practices {#best-practices}

Die meisten Schritte zum Entwerfen einer Formularvorlage, wie Schemabindungen oder Schreiben von Formularlogik, sind identisch. Aufgrund der inhärenten Unterschiede zwischen der Render- und Scripting-Engine eines Thick Client wie Adobe Reader und browserbasierten Formularen gibt jedoch es einige Empfehlungen, die im Artikel [Empfohlene Vorgehensweisen](/help/forms/using/design-accessible-html5-forms.md) beschrieben werden. Diese empfohlenen Vorgehensweisen helfen Ihnen, Formularvorlagen zu entwickeln, die in beiden Formaten wie erwartet funktionieren.

### Funktionen in AEM Forms Designer für HTML5-Formulare {#capabilities-in-aem-forms-designer-for-html-forms}

#### Vorschau von HTML {#preview-html}

Die Registerkarte Vorschau-HTML wird im Designmodus hinzugefügt, damit Formularentwickler während des Entwurfsprozesses eine Vorschau der Formulare im HTML5-Format anzeigen können. Weitere Informationen zum Aktivieren und Konfigurieren dieser Funktion in AEM Forms Designer finden Sie unter [Vorschau von HTML](../../forms/using/preview-xdp-forms-html.md).

#### Scribble-Signatur {#scribble-signature}

Das Hauptziel für HTML5-Formulare sind Touch-Geräte. Daher wird ein neues Scribble-Signatur-Steuerelement in AEM Forms Designer hinzugefügt. Sie können das Scribble-Signatur-Steuerelement anklicken oder per Drag-und-Drop auf Ihre Formularvorlage ziehen und konfigurieren. Es wird in der HTML5-Darstellung als Scribble-Feld gerendert und kann für Scribble-Signaturen auf Touch-Geräten verwendet werden. Auf Desktop-Rechnern kann es per Maussteuerung als Scribble-Feld verwendet werden. Weitere Informationen dazu, wie Sie diese Funktion nutzen, finden Sie unter [XFA-Scribble-Feld](../../forms/using/scribble-signature.md).

![4](assets/4.png)

#### Rich-Text-Format {#rich-text-format}

Sie können ein Textfeld in ein Rich-Text-Feld konvertieren. Hierdurch wird dem Textfeld eine Liste von Formatierungsoptionen hinzugefügt. Um es zu konvertieren, öffnen Sie Forms Designer und tippen Sie auf das Textfeld in der **[!UICONTROL Design-Ansicht]**. Wählen Sie auf der Registerkarte **[!UICONTROL Feld]** in der Dropdown-Liste **[!UICONTROL Feldformat]** die Option **[!UICONTROL Rich-Text]**. Wenn das XFA-Formular jetzt als HTML5-Formular gerendert wird, wird das Feld als Rich-Text-Feld gerendert. Tippen Sie auf ![Maximieren](assets/maximize_icon.svg), um weitere Formatierungsoptionen anzuzeigen.
