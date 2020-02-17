---
title: Panoramabilder
description: Erfahren Sie mehr über das Arbeiten mit interaktiven Bildern in Dynamic Media.
uuid: ced3e5bd-93c8-4d5f-a397-1380d4d0a5e7
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 632a9074-b747-49a1-a57d-1f42bba1f4e9
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Panoramic images{#panoramic-images}

In diesem Abschnitt wird beschrieben, wie Sie mit dem Viewer für Panoramabilder Kugelpanoramen für ein immersives 360°-Betrachtungserlebnis eines Zimmers, einer Immobilie, eines Ortes oder einer Landschaft ausgeben können.

Informationen hierzu finden Sie in [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Hochladen von Assets für die Verwendung mit dem Viewer für Panoramabilder {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Damit hochgeladene Assets als Kreispanoramen gelten und mit dem Viewer für Panoramabilder verwendet werden können, muss mindestens eine der beiden folgenden Eigenschaften zutreffen:

* Ein Seitenverhältnis von 2.
Sie können die Standardeinstellung für das Seitenverhältnis in CRXDE Lite wie folgt überschreiben:
   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Tagged with the keywords `equirectangular`, or `spherical`and `panorama`, or `spherical` and `panoramic`. Weitere Informationen finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

Both the aspect ratio and keyword criteria apply to panoramic assets for the asset details page and the `Panoramic Media` WCM component.

Weitere Informationen über den Upload von Assets für die Verwendung mit dem Viewer für Panoramabilder finden Sie unter [Hochladen von Assets](/help/assets/managing-assets-touch-ui.md#uploading-assets).

## Konfigurieren von Dynamic Media Classic (Scene7) {#configuring-dynamic-media-classic-scene}

Damit der Viewer für Panoramabilder in AEM ordnungsgemäß funktioniert, müssen Sie die Viewer-Vorgabe für Panoramabilder mit Dynamic Media Classic (Scene7) und mit auf Dynamic Media Classic (Scene7) bezogenen Metadaten synchronisieren, damit die Viewer-Vorgaben in JCR aktualisiert werden. Konfigurieren Sie Dynamic Media Classic (Scene7) dafür wie folgt:

1. [Melden Sie sich bei Ihrer Dynamic Media Classic (scene7)-Instanz an, ](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) und zwar bei jedem Unternehmenskonto.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinrichtung > Image-Server]**.
1. Wählen Sie auf der Image-Server-Veröffentlichungsseite im Dropdownmenü **[!UICONTROL Veröffentlichungskontext]** oben die Option **[!UICONTROL Image-Serving]** aus.

1. Suchen Sie auf derselben Image-Server-Veröffentlichungsseite die Überschrift **[!UICONTROL Anfrage-Attribute]**.
1. Suchen Sie unter der Überschrift „Anfrage-Attribute“ die Option **[!UICONTROL Maximale Größe des Antwortbildes]**. Erhöhen Sie anschließend die Werte in den entsprechenden Feldern „Breite“ und „Höhe“ auf die größtmögliche Bildgröße für Panoramabilder.

   Bei Dynamic Media Classic (Scene7) liegt die Obergrenze bei 25.000.000 Pixel. Die maximal zulässige Größe für Bilder mit einem Seitenverhältnis von 2:1 beträgt 7000 x 3500. In der Regel ist für Desktopbildschirme jedoch eine Größe von 4096 x 2048 Pixel ausreichend.

   >[!NOTE]
   >
   >Es werden nur Bilder innerhalb der zulässigen Maximalgröße unterstützt. Anfragen zu Bildern oberhalb der Obergrenze geben einen „403“-Fehler zurück.

1. Gehen Sie unter der Überschrift „Anfrage-Attribute“ wie folgt vor:

   * Legen Sie den Anfragenverschleierungsmodus auf **[!UICONTROL Deaktiviert]** fest.
   * Legen Sie den Anfragensperrmodus auf **[!UICONTROL Deaktiviert]** fest.
   These settings are necessary for using the `Panoramic Media` WCM component in AEM.

1. Klicken Sie unten links auf der Image-Server-Veröffentlichungsseite auf **[!UICONTROL Speichern]**.

1. Klicken Sie rechts unten auf **[!UICONTROL Schließen]**.

### Fehlerbehebung in der WCM-Komponente für Panoramamedien {#troubleshooting-the-panoramic-media-wcm-component}

Wenn Sie ein Bild in der Panoramamedienkomponente in WCM abgelegt haben und der Platzhalter der Komponente ausgeblendet ist, helfen Ihnen möglicherweise die folgenden Schritte zur Fehlerbehebung:

* Wenn Ihnen ein 403-Fehler (Forbidden) angezeigt wird, liegt es möglicherweise daran, dass die angefragte Bildgröße den Grenzwert überschreitet. Überprüfen Sie die Einstellungen für **[!UICONTROL Maximale Größe des Antwortbildes]** in [Konfigurieren von Dynamic Media Classic (Scene7)](/help/assets/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

* Überprüfen Sie im Falle einer „ungültigen Sperre“ für das Asset oder einem auf der Seite angezeigten „Parsing-Fehler“ den Anfragenverschleierungs- sowie den Anfragensperrmodus, um sicherzustellen, dass diese Modi deaktiviert sind.
* Bei einer Fehlermeldung zu einer beschädigten Arbeitsfläche können Sie einen Dateipfad für Regeldefinitionen einrichten und CTN für die vorangegangenen Anforderungen für das Bild-Asset ungültig machen.
* Wenn die Bildqualität infolge einer Bildanforderung mit einer Größe, die den unterstützten Bereich überschreitet, sehr gering wird, stellen Sie sicher, dass die Einstellung **[!UICONTROL JPEG-Codierungsattribute > Qualität]** nicht leer ist. Eine typische Einstellung für das Feld **[!UICONTROL Qualität]** ist `95`. Sie finden die Einstellung auf der Image-Server-Veröffentlichungsseite. Weitere Informationen über den Zugriff auf die Seite finden Sie unter [Konfigurieren von Dynamic Media Classic (Scene7)](/help/assets/panoramic-images.md#configuring%20dynamic%20media%20classic%20(scene7)).

## Anzeigen einer Vorschau für Panoramabilder {#previewing-panoramic-images}

Informationen hierzu finden Sie im Abschnitt [Asset-Vorschau](/help/assets/previewing-assets.md).

## Veröffentlichen von Panoramabildern {#publishing-panoramic-images}

Siehe [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).
