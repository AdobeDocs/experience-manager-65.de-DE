---
title: Vorschau von 3D-Assets
description: Erfahren Sie, wie Sie eine Vorschau von 3D-Assets anzeigen können
contentOwner: Rick Brough
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Vorschau von 3D-Assets{#previewing-3d-assets}

Experience Manager unterstützt das Hochladen, Bereitstellen und interaktive Anzeigen einer Vorschau von 3D-Assets als Teil des Authoring-Prozesses.

Der interaktive 3D-Viewer ist auf der Seite „Asset-Details“ in AEM verfügbar. Der Viewer bietet unter anderem eine Reihe interaktiver Kamera-Steuerelemente, mit denen Sie die Kamera um das 3D-Asset drehen sowie Zoom- und Schwenkvorgänge durchführen können.

## Unterstützte Formate für die 3D-Vorschau{#supported-3d-previewing-assets}

Die interaktive 3D-Vorschau unterstützt die folgenden Dateiformate:

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Hinweise |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-inary |  |
| GLTF | GL-Übertragungsformat | model/gltf+json | Siehe **Hinweis** unten. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | Unterstützung nur für die Aufnahme; Vorschau nicht verfügbar. |
| USDZ | Universelles Scene Description Zip-Archiv | model/vnd.usdz+zip | Unterstützung nur für die Aufnahme; Vorschau nicht verfügbar. |

**Hinweis**: Wenn Materialien nicht in der Vorschau eines gLTF-Modells wiedergegeben werden, stellen Sie sicher, dass sie ordnungsgemäß benannt sind und sich in einem `textures` Ordner befinden, der sich im selben Stammordner wie das Modell befindet, ähnlich wie im Folgenden:

    Asset (Ordner)
    model.
    gltfmodel.
    bintextures (Ordner)
    material_0_baseColor.
    jpegmaterial_0_normal.jpeg

## Performance considerations when you preview 3D assets{#performance-3d-previewing-assets}

Die Zeit, die zum Öffnen eines 3D-Assets auf der Seite mit den Asset-Details benötigt wird, hängt von verschiedenen Faktoren ab, z. B. Bandbreite, Bildkomplexität und Latenzen zum Server.

Darüber hinaus sind die Funktionen des Client-Computers - wie eine Workstation, ein Notebook oder ein mobiles Touch-Gerät - auch bei einer interaktiven Manipulation der Kamera wichtig. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

**So zeigen Sie eine Vorschau von 3D-Assets an**

1. Laden Sie 3D-Assets in AEM hoch.
Siehe [Unterstützte Formate für die 3D-Vorschau](#supported-3d-previewing-assets) und [Hochladen von Assets](/help/assets/managing-assets-touch-ui.md#uploading-assets).
1. Tippen Sie in AEM auf der **[!UICONTROL Navigationsseite]** auf **[!UICONTROL Assets > Dateien]**.

   ![Navigationsseite](/help/assets/assets-dm/navigation-assets.png)

1. Tippen Sie in der rechten oberen Ecke der Seite aus der Dropdownliste Ansicht auf **[!UICONTROL Kartenansicht]** und navigieren Sie dann zu einem 3D-Asset, das Sie in der Vorschau anzeigen möchten.

   ![3D-Kartenauswahl](/help/assets/assets-dm/3d-card-select.png)
   _Tippen Sie in der Kartenansicht auf die Karte des 3D-Assets, das Sie in der Vorschau anzeigen möchten._

1. Tippen Sie auf die Karte des 3D-Assets, um sie auf der Seite mit den Asset-Details zu öffnen.

   ![Interaktive 3D-Vorschau](/help/assets/assets-dm/3d-preview.png)
   _Interaktive Vorschau eines 3D-Assets auf der Seite mit den Asset-Details._
1. Führen Sie auf der Seite mit den Asset-Details für das 3D-Asset einen der folgenden Schritte aus:
   * **Drehen Sie Ihre Kamera**- Drehen Sie Ihre Ansicht um die 3D-Szene und -Objekte.
      * _Maus_: Klicken Sie mit der linken Maustaste und ziehen Sie.
      * _Touchscreen_: Drücken Sie mit einem Finger und ziehen Sie.
   * **Schwenken Sie die Kamera**- Schwenken Sie die Ansicht nach links, rechts, oben oder unten.
      * _Maus_: Klicken Sie mit der rechten Maustaste und ziehen Sie.
      * _Touchscreen_: Drücken Sie die Zwei-Finger-Taste und ziehen Sie.
   * **Zoomen Sie Ihre Kamera**- Zoomen Sie Ihre Kamera, um sich in- und außerhalb der 3D-Szene zu bewegen.
      * _Maus_: Bildlaufrad
      * _Touchscreen_: Zweifinger-Pinch
   * **Setzen Sie die Kamera** neu ein - geben Sie die Kamera bis zu einem Punkt auf einem Objekt in der 3D-Szene ein.
      * _Maus_: Doppelklicken Sie auf.
      * _Touchscreen_: Doppeltippen.
   * **Zurücksetzen**: Tippen Sie unten rechts auf der Seite auf das Symbol &quot;Zurücksetzen&quot;, um den Ansichtszielpunkt wieder in der Mitte des 3D-Assets anzuzeigen. Mit Zurücksetzen wird die Kamera auch näher oder weiter entfernt, um das Asset in seiner Gesamtheit und in einer angemessenen Anzeigegröße anzuzeigen.
   * **Vollbildmodus**: Um in den Vollbildmodus zu wechseln, tippen Sie in der rechten unteren Ecke der Seite auf das Symbol &quot;Vollbild&quot;.

1. When you are finished, near the upper-right corner of the page, tap **[!UICONTROL Close]**.
