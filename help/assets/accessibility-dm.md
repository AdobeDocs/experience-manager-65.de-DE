---
title: Barrierefreiheit in Dynamic Media
description: Erfahren Sie mehr über die Unterstützung der Barrierefreiheit in Dynamic Media- und Dynamic Media-Viewern.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibility
role: User, Admin
exl-id: bbdb800c-b6f8-4506-b8ac-daf64edcd6c0
source-git-commit: 01de1d5064f5ebf00acd2fe9f138d852f41f7273
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 64%

---

# Barrierefreiheit in [!DNL Dynamic Media] {#working-with-three-d-assets-dm}

[!DNL Dynamic Media] unterstützt Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.

## Unterstützung für Barrierefreiheit über die Tastatur in [!DNL Dynamic Media]

weil [!DNL Dynamic Media] ist ein Plug-in für [!DNL Adobe Experience Manager Assets], ist das Verhalten des Tastatursteuerelements größtenteils mit dem in [!DNL Experience Manager Assets]. Beispiel: die `Cancel` Schaltfläche in [!DNL Dynamic Media] hat dieselbe Fokushervorhebung wie in [!DNL Experience Manager Assets]und reagiert auf die `Spacebar` Schlüssel wie in [!DNL Experience Manager Assets]. Weitere Informationen finden Sie in [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Keystrokes, die von einzelnen Benutzeroberflächenelementen in [!DNL Dynamic Media] sind klar und leicht zu entdecken. Tastatursteuerung in [!DNL Dynamic Media] umfasst ungefähr Folgendes:

* Möglichkeit zur Verwendung von `Tab`- und `Shift+Tab`-Tastenkombinationen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Mithilfe von `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tabulatorreihenfolge weitergeschaltet. Durch die Verwendung von `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Die Fokusverschiebung folgt der natürlichen Position der Elemente der Benutzeroberfläche auf dem Bildschirm und bewegt sich in einer Reihenfolge von links nach rechts und dann von oben nach unten. Wenn in einem Feld ein Fehler auftritt, können Sie außerdem `Tab` drücken, um den Fokus darauf zu verschieben.
* Möglichkeit, mit den Tasten `Spacebar` und `Enter` Standardelemente der Benutzeroberfläche zu aktivieren, z. B. Schaltflächen und Dropdown-Listen.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Element der Benutzeroberfläche mit Eingabefokus erhält eine visuelle Fokusanzeige als Rahmen, der um das Element der Benutzeroberfläche gerendert wird.
* Im Hotspot-Editor können Sie einige benutzerdefinierte Tastenkombinationen wie Pfeiltasten verwenden, um mit komplexen Elementen der Benutzeroberfläche zu interagieren und Hotspots neu zu positionieren.
* Im interaktiven Video-Editor können Sie mit dem `Spacebar` ein Bild auswählen und es einem Segment hinzufügen. Darüber hinaus haben Sie die Möglichkeit, das ausgewählte Element mit der Taste `Backspace` aus der Registerkarte **[!UICONTROL Inhalt]** zu löschen. Drücken Sie nach Wunsch auch die Taste `Tab`, um zwischen interaktiven Elementen auf der Seite zu navigieren.
* Im Editor für Bildzuschnitt/smartes Zuschneiden können Sie Folgendes ausführen:
   * Mit den Pfeiltasten können Sie die Bildgröße zuschneiden oder das Bild neu positionieren oder beides.
   * Der erste `Tab`-Stopp markiert den gesamten Bildrahmen. Mit den Pfeiltasten auf der Tastatur können Sie den Rahmen dann neu positionieren.
   * Die folgenden vier `Tab`-Stopps sind die vier Ecken des Rahmens. Wenn der Fokus auf eine Rahmenecke gelegt wird, wird die Ecke hervorgehoben. Auch hier können Sie die fokussierte Ecke mit den Pfeiltasten auf der Tastatur verschieben.
Siehe [Bearbeiten des smarten Zuschnitts oder smarten Farb-/Bildmusters eines einzelnen Bildes](/help/assets/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Unterstützung der Technologie in [!DNL Dynamic Media] {#assistive-technology-support-for-dm}

[!DNL Dynamic Media] Benutzeroberflächen-Elemente können mit Hilfstechnologien wie Bildschirmlesehilfen verwendet werden. Beispielsweise werden Orientierungspunkte auf einer Seite erkannt, wenn Sie mithilfe des Tastaturbefehls `D` durch Orientierungspunkte oder mithilfe des Tastaturbefehls `R` durch Regionen navigieren. Außerdem wird die Überschrift vorgelesen, wenn Sie mit dem Tastaturbefehl für Überschriften `H` navigieren.

## Unterstützung für Barrierefreiheit über die Tastatur in [!DNL Dynamic Media] Viewer {#keyboard-accessibility-for-dm-viewers}

Alle nativen [!DNL Dynamic Media] Viewer-Komponenten unterstützen den Tastaturzugriff für Ihre Kunden.

Weitere Informationen finden Sie unter [Tastaturbedienung und Navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html?lang=de) im Dynamic Media Viewers-Referenzhandbuch.

## Unterstützung der Technologie in [!DNL Dynamic Media] Viewer {#assistive-technology-support-for-dm-viewers}

Alle [!DNL Dynamic Media] Viewer-Komponenten unterstützen ARIA (Accessible Rich Internet Applications)-Rollen und -Attribute, um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.
Weitere Informationen finden Sie im Hilfethema **Unterstützung für Hilfstechnologien** im Dynamic Media Viewers-Referenzhandbuch. Sehen Sie beispielsweise [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html?lang=de) für den Video-Viewer oder [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html#viewers-for-aem-assets-only) für den interaktiven Bild-Viewer.

## Unterstützung für geschlossene Untertitel in Dynamic Media {#closed-caption-support}

Dynamic Media unterstützt die Bereitstellung von Videos und adaptiven Videosets mit verdeckten Untertiteln. Die Untertitel müssen über dem Videoinhalt angezeigt werden.

Siehe [Video in Dynamic Media - Hinzufügen von Untertiteln oder Untertiteln zu Videos](/help/assets/video.md#adding-captions-to-video).

>[!MORELIKETHIS]
>
>* [Barrierefreiheit für Adobe-lösungen](https://www.adobe.com/accessibility.html)
>* [Barrierefreiheit in [!DNL Experience Manager Assets]](/help/assets/accessibility.md)

