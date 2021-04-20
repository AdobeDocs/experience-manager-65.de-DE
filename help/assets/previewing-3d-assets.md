---
title: Vorschau von 3D-Assets
description: 'Erfahren Sie, wie Sie eine Vorschau von 3D-Assets anzeigen können '
contentOwner: Rick Brough
docset: aem65
feature: 3D Assets
role: Business Practitioner
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 100%

---


# Vorschau von 3D-Assets in AEM {#previewing-3d-assets-aem}

Adobe Experience Manager unterstützt das Hochladen, Bereitstellen und interaktive Anzeigen einer Vorschau von 3D-Assets als Teil des Authoring-Prozesses.

Der interaktive 3D-Viewer ist auf der Seite „Asset-Details“ in AEM verfügbar. Der Viewer bietet unter anderem eine Reihe interaktiver Kamera-Steuerelemente, mit denen Sie die Kamera um das 3D-Asset drehen sowie Zoom- und Schwenkvorgänge durchführen können.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/assets-3d.md). -->

## Unterstützte Formate für die 3D-Vorschau in AEM {#supported-3d-previewing-assets}

Die interaktive 3D-Vorschau unterstützt die folgenden Dateiformate:

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Hinweise |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary |  |
| GLTF | GL-Übertragungsformat | model/gltf+json | Siehe **Hinweis** unten. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | Unterstützung nur für die Erfassung; Vorschau nicht verfügbar. |
| USDZ | Universelles Scene Description-Zip-Archiv | model/vnd.usdz+zip | Unterstützung nur für die Erfassung; Vorschau nicht verfügbar. |

**Hinweis**: Wenn Materialien nicht in der Vorschau eines gLTF-Modells wiedergegeben werden, stellen Sie sicher, dass sie ordnungsgemäß benannt sind und sich in einem `textures`-Ordner befinden, der sich im selben Stammordner wie das Modell befindet, ähnlich wie im Folgenden beschrieben:

    Asset (folder)
    model.gltf
    model.bin
    textures (folder)
    material_0_baseColor.jpeg
    material_0_normal.jpeg

## Leistungsaspekte bei der Vorschau von 3D-Assets in AEM {#performance-3d-previewing-assets}

Die Zeit, die zum Öffnen eines 3D-Assets auf der Seite mit den Asset-Details benötigt wird, hängt von verschiedenen Faktoren ab, z. B. Bandbreite, Bildkomplexität und Latenzen zum Server.

Wenn Sie die Kamera interaktiv bearbeiten, muss darüber hinaus die Kapazität des Client-Computers – etwa Workstation, Notebook oder Mobilgerät mit Touch-Funktion – berücksichtigt werden. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

**Vorschau von 3D-Assets in AEM**

1. Laden Sie 3D-Assets in AEM hoch.
Siehe [Unterstützte Formate für die 3D-Vorschau](#supported-3d-previewing-assets) und [Hochladen von Assets](/help/assets/manage-assets.md#uploading-assets).
1. Tippen Sie in AEM auf der **[!UICONTROL Navigationsseite]** auf **[!UICONTROL Assets > Dateien.]**

   ![Navigationsseite](/help/assets/assets-dm/navigation-assets.png)

1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste „Ansicht“ auf **[!UICONTROL Kartenansicht]** und navigieren Sie dann zu einem 3D-Asset, das Sie in der Vorschau anzeigen möchten.

   ![3D-Kartenauswahl](/help/assets/assets-dm/3d-card-select.png)
   _Tippen Sie in der Kartenansicht auf die Karte des 3D-Assets, das Sie in der Vorschau anzeigen möchten._

1. Tippen Sie auf die Karte des 3D-Assets, um das Asset auf der Seite mit der Detailansicht des Assets zu öffnen.

   ![Interaktive 3D-Vorschau](/help/assets/assets-dm/3d-preview.png)
   _Interaktive Vorschau eines 3D-Assets auf der Seite mit der Detailansicht des Assets._
1. Führen Sie auf der Seite mit der Detailansicht des Assets für das 3D-Asset einen der folgenden Schritte aus:
   * **Kamera drehen**: Drehen Sie Ihre Ansicht in der 3D-Szene um die Objekte herum.
      * _Maus_: Klicken und ziehen Sie mit der linken Maustaste.
      * _Touchscreen_: Drücken und ziehen Sie mit einem Finger.
   * **Kamera schwenken**: Schwenken Sie die Ansicht nach links, rechts, oben oder unten.
      * _Maus_: Klicken und ziehen Sie mit der rechten Maustaste.
      * _Touchscreen_: Drücken und ziehen Sie mit zwei Fingern.
   * **Kamera zoomen**: Zoomen Sie Ihre Kamera, um sich in Bereiche der 3D-Szene hinein- und herauszubewegen.
      * _Maus_: Scrollen Sie mit dem Mausrad.
      * _Touchscreen_: Führen Sie mit zwei Fingern Pinch-Gesten aus.
   * **Kamera neu zentrieren**: Zentrieren Sie Ihre Kamera neu auf einen Punkt auf einem Objekt in der 3D-Szene.
      * _Maus_: Doppelklicken Sie.
      * _Touchscreen_: Doppeltippen Sie.
   * **Zurücksetzen**: Tippen Sie unten rechts auf der Seite auf das Symbol „Zurücksetzen“, um den Zielpunkt der Ansicht wieder in die Mitte des 3D-Assets zu setzen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen.
   * **Vollbildmodus**: Um in den Vollbildmodus zu wechseln, tippen Sie unten rechts auf Seite auf das Symbol „Vollbild“.

1. Tippen Sie zum Abschluss unten rechts auf der Seite auf **[!UICONTROL Schließen.]**
