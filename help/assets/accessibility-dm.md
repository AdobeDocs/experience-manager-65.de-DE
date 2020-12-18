---
title: Zugänglichkeit in Dynamic Media
description: Weitere Informationen zur Barrierefreiheitsunterstützung in Dynamic Media- und Dynamic Media-Viewern
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: e95f26cc1a084358b6bcb78605e3acb98f257b66
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# Barrierefreiheit in [!DNL Dynamic Media] {#working-with-three-d-assets-dm}

[!DNL Dynamic Media] unterstützt Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.

## Unterstützung für die Barrierefreiheit von Tastaturen in [!DNL Dynamic Media]

Da [!DNL Dynamic Media] ein Plug-in für [!DNL Adobe Experience Manager Assets] ist, ist der Großteil des Tastatursteuerverhaltens exakt dasselbe wie in [!DNL Experience Manager Assets]. Beispielsweise hat die Schaltfläche `Cancel` in [!DNL Dynamic Media] dieselbe Fokusmarkierung wie in [!DNL Experience Manager Assets] und reagiert auf die `Spacebar`-Taste wie in [!DNL Experience Manager Assets]. Siehe [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Tastenanschläge, die von einzelnen Benutzeroberflächenelementen in [!DNL Dynamic Media] unterstützt werden, sind in den meisten Fällen offensichtlich und leicht zu entdecken. Die Tastatursteuerung in [!DNL Dynamic Media] lautet wie folgt:

* Möglichkeit zur Verwendung von `Tab`- und `Shift+Tab`-Tastenanschlägen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Mithilfe von `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tab-Reihenfolge weitergeleitet. Durch die Verwendung von `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Der Fokusdurchlauf folgt der natürlichen Elementposition der Benutzeroberfläche auf dem Bildschirm und bewegt sich in der Reihenfolge von links nach rechts und von oben nach unten. Wenn außerdem ein Feld einen Fehler enthält, können Sie `Tab` drücken, um den Fokus darauf zu verschieben.
* Möglichkeit, mit den Tasten `Spacebar` und `Enter` Standardelemente der Benutzeroberfläche zu aktivieren, z. B. Schaltflächen, Dropdown-Listen usw.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Element der Benutzeroberfläche mit Eingabefokus erhält möglicherweise eine visuelle Fokusanzeige als Rahmen, der um das Element der Benutzeroberfläche gerendert wird.
* Im Hotspot-Editor können Sie einige benutzerdefinierte Tastenkombinationen wie Pfeiltasten verwenden, um mit komplexen Elementen der Benutzeroberfläche zu interagieren und Hotspots neu zu positionieren.
* Im interaktiven Video-Editor können Sie mit dem `Spacebar` ein Bild auswählen und es einem Segment hinzufügen. Darüber hinaus haben Sie die Möglichkeit, das ausgewählte Element mit der Taste `Backspace` aus der Registerkarte **[!UICONTROL Inhalt]** zu löschen. Drücken Sie nach Wunsch auch die Taste `Tab`, um zwischen interaktiven Elementen auf der Seite zu navigieren.
* Im Bildzuschneideeditor haben Sie folgende Möglichkeiten:
   * Verwenden Sie die Pfeiltasten, um die Rahmengröße zu beschneiden, das Bild neu zu positionieren oder beides.
   * Der erste `Tab`-Stopp markiert den gesamten Bildrahmen. Mit den Pfeiltasten auf der Tastatur können Sie den Rahmen dann neu positionieren.
   * Die folgenden vier `Tab`-Haltepunkte sind die vier Ecken des Rahmens. Wenn der Fokus auf eine Rahmenecke gelegt wird, ist die Ecke Hervorhebung. Auch hier können Sie die fokussierte Ecke mit den Pfeiltasten auf der Tastatur verschieben.
Siehe [Bearbeiten des intelligenten Zuschnitts oder intelligenten Farbfelds eines einzelnen Bildes](/help/assets/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Unterstützung von unterstützender Technologie in [!DNL Dynamic Media] {#assistive-technology-support-for-dm}

[!DNL Dynamic Media] Benutzeroberflächenelemente können mit Hilfstechnologien wie Bildschirmlesehilfen verwendet werden. Beispielsweise werden Landmarks auf einer Seite erkannt, wenn Sie mithilfe des Tastaturbefehls `D` oder mit dem Tastaturbefehl `R` durch Bereiche navigieren. Die Überschrift wird auch beim Navigieren mit dem Tastaturbefehl für Überschriften `H` erläutert.

## Unterstützung für die Barrierefreiheit von Tastaturen in [!DNL Dynamic Media]-Viewern {#keyboard-accessibility-for-dm-viewers}

Alle standardmäßigen [!DNL Dynamic Media]-Viewer-Komponenten unterstützen die Barrierefreiheit der Tastatur für Ihre Kunden.

Siehe [Tastaturzugriff und Navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) im Dynamic Media Viewer-Referenzhandbuch.

## Unterstützung von unterstützender Technologie in [!DNL Dynamic Media] Viewern {#assistive-technology-support-for-dm-viewers}

Alle [!DNL Dynamic Media]-Viewer-Komponenten unterstützen ARIA-Rollen und -Attribute (Accessible Rich Internet Applications), um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.
Weitere Informationen finden Sie im Hilfethema **Support für Hilfstechnologien** im Dynamic Media Viewer-Referenzhandbuch. Siehe z. B. [Unterstützung bei der Hilfstechnologie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) für den Video-Viewer oder [Unterstützung bei der Hilfstechnologie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) für den interaktiven Bild-Viewer.

>[!MORELIKETHIS]
>
>* [Zugänglichkeit für Adoben](https://www.adobe.com/accessibility.html)
>* [Barrierefreiheit in  [!DNL Experience Manager Assets]](/help/assets/accessibility.md)

