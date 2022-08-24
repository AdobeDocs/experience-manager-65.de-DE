---
title: Entwerfen barrierefreier HTML5-Formulare
seo-title: Designing accessible HTML5 forms
description: HTML5-Formulare verwenden den ARIA-HTML5-Standard für Barrierefreiheit. Diese Formulare unterstützen Registerkartennavigation und sind zertifiziert für ihre Kompatibilität mit üblichen Bildschirmlesehilfen.
seo-description: HTML5 forms use the ARIA HTML5 accessibility standard. These forms support tabbed navigation and are certified to be compatible with common screen readers.
uuid: 1ce5ba39-69ea-4d0e-96ea-e2a38b21d6b7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8711ad33-396b-4572-b2ee-71e9f45f4ebe
docset: aem65
feature: Mobile Forms
exl-id: fca2f9b2-11a2-4db0-a370-c4046f32be63
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 100%

---

# Entwerfen barrierefreier HTML5-Formulare {#designing-accessible-html-forms}

Für HTML5-Formulare wird der ARIA-HTML5-Standard für Barrierefreiheit verwendet, um die HTML-Formulare barrierefrei zu gestalten. Diese Formulare unterstützen Registerkartennavigation (außer Mozilla Firefox) und sind zertifiziert für ihre Kompatibilität mit üblichen Bildschirmlesehilfen. Um ein HTML5-Formular mit Barrierefreiheitsmerkmalen zu generieren, entwerfen Sie die XFA-Formularvorlage nach einigen grundlegenden Entwurfsrichtlinien. Die Entwurfsrichtlinien umfassen das Konfigurieren der richtigen Registerkartenreihenfolge und die Bereitstellung des Sprechtext-Inhalts für jedes Formularsteuerelement. AEM Forms Designer unterstützt das Festlegen dieser Formularsteuerungsattribute zum Erstellen eines barrierefreien PDF- und HTML5-Formulars.

*Hinweis: Die Registerkartennavigation deckt keine geschützten Felder ab, wie etwa Berechnungsfelder, die Wertesummen anzeigen. Damit die Bildschirmlesehilfe den Wert eines geschützten Felds liest, platzieren Sie ein leeres schreibgeschütztes Feld entweder auf oder neben dem geschützten Feld. Weisen Sie den Wert des geschützten Feldes dem neuen schreibgeschützten Feld zu. Die Bildschirmlesehilfe oder die Registerkartennavigation können dieses schreibgeschützte Feld erfassen und als Wert des geschützten Felds wiedergeben.*

AEM Forms Designer enthält einige Sprechtextoptionen, die an Bildschirmlesehilfen übergeben werden können. Für jedes Objekt in einem Formular kann der Benutzer eine oder mehrere Einstellungen für den Text der Bildschirmlesehilfe angeben:

* Benutzerdefinierter Bildschirmlesehilfen-Text, der mithilfe der Palette „Ein-/Ausgabehilfe“ festgelegt werden kann. Autoren können die Namen von Schaltflächen und Feldern sowie deren Zweck kommentieren.
* QuickInfos, die in der Palette „Ein-/Ausgabehilfe“ eingestellt werden können.
* Beschriftungen für Felder im Formular.
* Namen von Objekten (wie im Feld „Name“ der Registerkarte „Bindung“ angegeben).

![Barrierefreiheit](assets/accessibility.png)

Wenn mehrere Optionen wie QuickInfos Bildschirmlesehilfen-Text, und Beschriftung in einem Formularsteuerelement zur Verfügung stehen, verwendet die Bildschirmlesehilfe nur eine dieser Eigenschaften. Die Standardreihenfolge ist benutzerdefinierter Bildschirmlesehilfen-Text, QuickInfo, Beschriftung und Name. Diese Standardreihenfolge können Sie über die Option Bildschirmlesehilfen-**Rangfolge** in der Palette „Ein-/Ausgabehilfe“ außer Kraft setzen.
