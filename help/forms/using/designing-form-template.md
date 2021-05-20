---
title: Entwerfen von Formularvorlagen für HTML5-Formulare
seo-title: Entwerfen von Formularvorlagen für HTML5-Formulare
description: AEM Forms ermöglicht die Wiedergabe von XFA-Formularvorlagen im HTML5-Format. Formularentwickler können Formularvorlagen mit Designer entwerfen und die HTML5-Renderfunktion nutzen.
seo-description: AEM Forms ermöglicht die Wiedergabe von XFA-Formularvorlagen im HTML5-Format. Formularentwickler können Formularvorlagen mit Designer entwerfen und die HTML5-Renderfunktion nutzen.
uuid: 4f6b7231-4479-400a-adcd-c68064f06b4e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: f2e9dbe4-e210-41f3-8878-2fc4d166e63c
docset: aem65
feature: Mobile Forms
exl-id: 7c8d501f-c953-495e-8bac-1f66fd99c783
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 57%

---

# Entwerfen von Formularvorlagen für HTML5-Formulare{#designing-form-templates-for-html-forms}

Die HTML5-Formularkomponente in AEM ermöglicht, XFA-Formularvorlagen im HTML5-Format zu rendern. Formularentwickler können Formularvorlagen mit [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) entwerfen und die HTML5-Renderfunktion nutzen. Diese Formularvorlagen können sich zusammen mit ihren Assets im AEM Repository-Dateisystem befinden oder über HTTP bereitgestellt werden. Wenn Sie Ihre Formulare jedoch mit Forms Manager verwalten möchten, sollten sich die Vorlagen und Assets im AEM Repository befinden.

Obwohl das Verhalten von HTML5-Formularen und PDF-Formularen sich stark ähnelt, gibt es mehrere Funktionen in beiden Formaten, die nicht im anderen Format verfügbar sind. Beispielsweise variiert die Anwendung von Barcodes auf ein PDF-Formular in Adobe Reader von einem Mobile-Formular aus oder die digitale Unterzeichnung eines Formulars variiert auch zwischen den Formaten. Weitere Informationen zu diesen Varianten finden Sie unter [Funktionsunterschiede zwischen HTML5-Formularen und PDF forms](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Allgemeine XFA-Funktionen finden Sie in den folgenden empfohlenen Verfahrensweisen und Richtlinien zum Entwerfen eines Formulars, das in beiden Formaten funktioniert.

## Best Practices {#best-practices}

Die meisten Schritte um die Entwicklung einer Formularvorlage, wie Schemabindungen oder das Schreiben von Formularlogik, sind identisch. Aufgrund der inhärenten Unterschiede zwischen der Render- und Scripting-Engine eines Thick Client wie Adobe Reader und browserbasierten Formularen gibt jedoch es einige Empfehlungen, die im Artikel [Empfohlene Vorgehensweisen](/help/forms/using/design-accessible-html5-forms.md) beschrieben werden. Mithilfe dieser Best Practices können Sie Formularvorlagen so entwerfen, dass sie in beiden Formaten wie erwartet funktionieren.

### Funktionen in AEM Forms Designer für HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

#### HTML-Vorschau {#preview-html}

Die HTML-Vorschau-Registerkarte wurde im Designmodus für Formularentwickler hinzugefügt, um eine Vorschau von Formularen im HTML5-Format während des Entwurfsprozesses zu ermöglichen. Weitere Informationen dazu, wie Sie diese Funktion in AEM Forms Designer aktivieren und konfigurieren, finden Sie unter [HTML-Vorschau](../../forms/using/preview-xdp-forms-html.md).

#### Scribble-Signatur {#scribble-signature}

Das Hauptziel für HTML5-Formulare sind Touch-Geräte. Daher wurde ein neues Scribble-Signatur-Steuerelement in AEM Forms Designer hinzugefügt. Sie können auf das Scribble-Signatur-Steuerelement klicken oder es per Drag-and-Drop auf Ihre Formularvorlage ziehen und konfigurieren. Sie wird in der HTML5-Ausgabe als Scribble-Feld gerendert und kann für die Scribble-Signatur auf Touch-Geräten verwendet werden. Auf Desktop-Rechnern kann es per Maussteuerung als Scribble-Feld verwendet werden. Weitere Informationen zur Verwendung dieser Funktion finden Sie unter [XFA Scribble Field](../../forms/using/scribble-signature.md).

![4](assets/4.png)

#### Rich-Text-Format {#rich-text-format}

Sie können ein Textfeld in ein Rich-Text-Feld konvertieren. Hierdurch wird dem Textfeld eine Liste von Formatierungsoptionen hinzugefügt. Um zu konvertieren, öffnen Sie Forms Designer und tippen Sie auf das Textfeld in **[!UICONTROL Designansicht]**. Wählen Sie auf der Registerkarte **[!UICONTROL Feld]** die Option **[!UICONTROL Rich Text]** aus der Dropdownliste **[!UICONTROL Feldformat]** aus. Wenn das XFA-Formular jetzt als HTML5-Formular wiedergegeben wird, wird das Feld als Rich-Text-Feld gerendert. Tippen Sie auf ![Maximieren](assets/maximize_icon.svg), um weitere Formatierungsoptionen anzuzeigen.
