---
title: Zugänglichkeit in [!DNL Dynamic Media]
description: Informationen zur Barrierefreiheit in Viewern für dynamische Medien und dynamische Medien
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 383f84b1a984683b3e2ce60f1a3f2191749a1561
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 1%

---


# Zugänglichkeit in [!DNL Dynamic Media] {#working-with-three-d-assets-dm}

[!DNL Dynamic Media] unterstützt Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.

## Unterstützung für die Barrierefreiheit von Tastaturen in [!DNL Dynamic Media]

Da [!DNL Dynamic Media] es sich um ein Plug-in handelt, ist [!DNL Adobe Experience Manager Assets]das Verhalten der Tastatursteuerung im Wesentlichen identisch mit dem Verhalten in [!DNL Experience Manager Assets]. Beispielsweise hat die `Cancel` Schaltfläche in [!DNL Dynamic Media] dieselbe Fokushervorhebung wie in [!DNL Experience Manager Assets]und reagiert auf die `Spacebar` Taste wie in [!DNL Experience Manager Assets]. Siehe [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Tastenanschläge, die von einzelnen Benutzeroberflächenelementen unterstützt werden, [!DNL Dynamic Media] sind in den meisten Fällen offensichtlich und leicht zu entdecken. Die Tastatursteuerung in [!DNL Dynamic Media] umfasst Folgendes:

* Möglichkeit zur Verwendung `Tab` und `Shift+Tab` Verwendung von Tastenanschlägen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Durch Verwendung `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tab-Reihenfolge weitergeleitet. Durch die Verwendung `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Der Fokusdurchlauf folgt der natürlichen Elementposition der Benutzeroberfläche auf dem Bildschirm und bewegt sich in der Reihenfolge von links nach rechts und von oben nach unten. Wenn außerdem ein Feld einen Fehler enthält, können Sie die Taste drücken, `Tab` um den Fokus darauf zu verschieben.
* Möglichkeit, mit der `Spacebar` und- `Enter` Taste Standard-Benutzeroberflächenelemente wie Schaltflächen, Dropdown-Listen usw. zu aktivieren.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Element der Benutzeroberfläche mit Eingabefokus erhält möglicherweise eine visuelle Fokusanzeige als Rahmen, der um das Element der Benutzeroberfläche gerendert wird.
* Im Hotspot-Editor können Sie einige benutzerdefinierte Tastenkombinationen wie Pfeiltasten verwenden, um mit komplexen Elementen der Benutzeroberfläche zu interagieren und Hotspots neu zu positionieren.
* Im Interaktiven Video-Editor können Sie mit der `Spacebar` einen Bildausschnitt auswählen und einem Segment hinzufügen. Darüber hinaus haben Sie die Möglichkeit, das ausgewählte Element mithilfe der `Backspace` Taste aus der Registerkarte &quot; **[!UICONTROL Inhalt]** &quot;zu löschen. Drücken Sie außerdem nach Wunsch die `Tab` Funktionen, um zwischen interaktiven Elementen auf der Seite zu navigieren.
* Im Bildzuschneideeditor haben Sie folgende Möglichkeiten:
   * Verwenden Sie die Pfeiltasten, um die Rahmengröße zu beschneiden, das Bild neu zu positionieren oder beides.
   * Der erste `Tab` Punkt markiert den gesamten Bildrahmen. Mit den Pfeiltasten auf der Tastatur können Sie den Rahmen dann neu positionieren.
   * Die nächsten vier `Tab` Haltestellen sind die vier Ecken des Rahmens. Wenn der Fokus auf eine Rahmenecke gelegt wird, ist die Ecke Hervorhebung. Auch hier können Sie die fokussierte Ecke mit den Pfeiltasten auf der Tastatur verschieben.
See [Editing the smart crop or smart swatch of a single image](/help/assets/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Unterstützung der Technologie in [!DNL Dynamic Media] {#assistive-technology-support-for-dm}

[!DNL Dynamic Media] Benutzeroberflächenelemente können mit Hilfstechnologien wie Bildschirmlesehilfen verwendet werden. Beispielsweise werden Landmarken auf einer Seite erkannt, wenn Sie mithilfe von Tastaturbefehlen `D` oder -regionen mithilfe von Tastaturbefehlen durch Landmarken navigieren `R`. Die Überschrift wird auch beim Navigieren mit dem Tastaturbefehl für Überschriften `H`erläutert.

## Unterstützung für die Barrierefreiheit von Tastaturen in [!DNL Dynamic Media] Viewern {#keyboard-accessibility-for-dm-viewers}

Alle vordefinierten [!DNL Dynamic Media] Viewer-Komponenten unterstützen die Barrierefreiheit der Tastatur für Ihre Kunden.

Siehe [Barrierefreiheit und Navigation](https://docs.adobe.com/content/help/de-DE/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) über die Tastatur im Viewer-Referenzhandbuch für dynamische Medien.

## Unterstützung von Technologien in [!DNL Dynamic Media] Viewern {#assistive-technology-support-for-dm-viewers}

Alle [!DNL Dynamic Media] Viewer-Komponenten unterstützen ARIA-Rollen und -Attribute (Accessible Rich Internet Applications), um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.
Weitere Informationen finden Sie im Hilfethema zur Unterstützung **der** unterstützenden Technologie in einem Viewer-Thema zum Anpassen im Referenzhandbuch für Dynamische Medien-Viewer. Weitere Informationen finden Sie unter [Unterstützung](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) der Technologie für den Video-Viewer oder Unterstützung [der](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) Technologie für den Viewer für interaktive Bilder.

>[!MORELIKETHIS]
>
>* [Zugänglichkeit für Adoben](https://www.adobe.com/accessibility.html)
>* [Zugänglichkeit in [!DNL Experience Manager Assets]](/help/assets/accessibility.md)

