---
title: Entwerfen barrierefreier HTML5-Formulare
description: HTML5-Formulare verwenden den ARIA HTML5-Barrierefreiheitsstandard. Diese Formulare unterstützen die Navigation mit Registerkarten und sind zertifiziert für die Kompatibilität mit gängigen Bildschirmlesehilfen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: Mobile Forms
exl-id: fca2f9b2-11a2-4db0-a370-c4046f32be63
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 27%

---

# Entwerfen barrierefreier HTML5-Formulare {#designing-accessible-html-forms}

Für HTML5-Formulare wird der ARIA-HTML5-Standard für Barrierefreiheit verwendet, um die HTML-Formulare barrierefrei zu gestalten. Diese Formulare unterstützen Registerkartennavigation (außer Mozilla FireFox) und sind für die Kompatibilität mit gängigen Bildschirmlesehilfen zertifiziert. Um ein HTML5-Formular mit Barrierefreiheitsmerkmalen zu generieren, entwerfen Sie die XFA-Formularvorlage nach einigen grundlegenden Entwurfsrichtlinien. Die Entwurfsrichtlinien umfassen das Konfigurieren der richtigen Registerkartenreihenfolge und die Bereitstellung des Sprechtext-Inhalts für jedes Formularsteuerelement. AEM Forms Designer unterstützt das Festlegen dieser Formularsteuerungsattribute zum Erstellen eines barrierefreien PDF- und HTML5-Formulars.

*Hinweis:Die Registerkartennavigation deckt keine geschützten Felder ab, z. B. Berechnungsfelder, die die Summe der Werte anzeigen. Damit die Bildschirmlesehilfe den Wert eines geschützten Felds lesen kann, platzieren Sie ein leeres schreibgeschütztes Feld entweder auf dem geschützten Feld oder neben dem Feld. Weisen Sie den Wert des geschützten Felds dem neuen schreibgeschützten Feld zu. Die Bildschirmlesehilfe oder die Registerkartennavigation können dieses schreibgeschützte Feld auswählen und als Wert des geschützten Felds ausdrücken.*

AEM Forms Designer enthält mehrere Sprachtext-Optionen, die an Bildschirmlesehilfen übergeben werden können. Für jedes Objekt in einem Formular kann der Benutzer eine von mehreren Einstellungen für den Text der Bildschirmlesehilfe angeben:

* Benutzerdefinierter Bildschirmlesehilfen-Text, der über die Palette &quot;Ein-/Ausgabehilfe&quot;festgelegt werden kann. Autoren können die Namen von Schaltflächen und Feldern und ihren Zweck kommentieren.
* QuickInfos, die in der Palette &quot;Ein-/Ausgabehilfe&quot;festgelegt werden können.
* Beschriftungen für Felder im Formular.
* Namen von Objekten, wie in der Option &quot;Name&quot;der Registerkarte &quot;Bindung&quot;angegeben.

![Barrierefreiheit](assets/accessibility.png)

Wenn in einem Formularsteuerelement mehrere Optionen wie QuickInfos, Bildschirmtext und Beschriftung verfügbar sind, verwendet der Reader &quot;Reader&quot;nur eine dieser Eigenschaften. Die Standardreihenfolge lautet &quot;Benutzerdefinierter Bildschirmtext&quot;, &quot;QuickInfo&quot;, &quot;Beschriftung&quot;und &quot;Reader&quot;. Diese Standardreihenfolge können Sie über die Option Bildschirmlesehilfen-**Rangfolge** in der Palette „Ein-/Ausgabehilfe“ außer Kraft setzen.
