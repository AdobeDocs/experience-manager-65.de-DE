---
title: Vorschau von 3D-Assets
description: 'Erfahren Sie, wie Sie eine Vorschau von 3D-Assets anzeigen können   '
contentOwner: Rick Brough
docset: aem65
feature: 3D-Assets
role: User
exl-id: fdebbc2b-c04d-4cdd-b7c2-8e9a2a854e79
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 98%

---

# Vorschau von 3D-Assets in Adobe Experience Manager{#previewing-3d-assets-aem}

Experience Manager unterstützt das Hochladen, Bereitstellen und interaktive Anzeigen einer Vorschau von 3D-Assets als Teil des Authoring-Prozesses.

Der interaktive 3D-Viewer ist auf der Seite „Asset-Details“ in Experience Manager verfügbar. Der Viewer bietet unter anderem eine Reihe interaktiver Kamera-Steuerelemente, mit denen Sie die Kamera um das 3D-Asset drehen sowie Zoom- und Schwenkvorgänge durchführen können.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/assets-3d.md). -->

## Unterstützte Formate für die 3D-Vorschau in Experience Manager {#supported-3d-previewing-assets}

Die interaktive 3D-Vorschau unterstützt die folgenden Dateiformate:

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Hinweise |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary |  |
| GLTF | GL-Übertragungsformat | model/gltf+json | Siehe **Hinweis** unten. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | Unterstützung nur für die Erfassung; Vorschau nicht verfügbar. |
| USDZ | Universelles Scene Description-Zip-Archiv | model/vnd.usdz+zip | Unterstützung nur für die Erfassung; Vorschau nicht verfügbar. |

>[!NOTE]
>
>Wenn Materialien nicht in der Vorschau eines gLTF-Modells wiedergegeben werden, stellen Sie sicher, dass sie ordnungsgemäß benannt sind und sich in einem `textures`-Ordner befinden, der sich im selben Stammordner wie das Modell befindet, ähnlich wie im Folgenden beschrieben:

    Asset (folder)
    model.gltf
    model.bin
    textures (folder)
    material_0_baseColor.jpeg
    material_0_normal.jpeg

## Leistungsaspekte bei der Vorschau von 3D-Assets in Experience Manager {#performance-3d-previewing-assets}

Die Zeit, die zum Öffnen eines 3D-Assets auf der Seite mit den Asset-Details benötigt wird, hängt von verschiedenen Faktoren ab, z. B. Bandbreite, Bildkomplexität und Latenzen zum Server.

Wenn Sie die Kamera interaktiv bearbeiten, muss darüber hinaus die Kapazität des Client-Computers – etwa Workstation, Notebook oder Mobilgerät mit Touch-Funktion – berücksichtigt werden. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

**So erstellen Sie eine Vorschau von 3D-Assets in Experience Manager:**

1. Stellen Sie sicher, dass Sie 3D-Assets in Adobe Experience Manager hochgeladen haben.
Siehe [Unterstützte Formate für die 3D-Vorschau](#supported-3d-previewing-assets) und [Hochladen von Assets](/help/assets/manage-assets.md#uploading-assets).
1. Tippen Sie in Adobe Experience Manager auf der Seite **[!UICONTROL Navigation]** auf **[!UICONTROL Assets > Dateien]**.

   ![Navigationsseite](/help/assets/assets-dm/navigation-assets.png)

1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste „Ansicht“ auf **[!UICONTROL Kartenansicht]** und navigieren Sie dann zu einem 3D-Asset, das Sie in der Vorschau anzeigen möchten.

   ![3D-Kartenauswahl](/help/assets/assets-dm/3d-card-select.png)
   _Tippen Sie in der Kartenansicht auf die Karte des 3D-Assets, das Sie in der Vorschau anzeigen möchten._

1. Tippen Sie auf die Karte des 3D-Assets.

   ![Interaktive 3D-Vorschau](/help/assets/assets-dm/3d-preview.png)
   _Interaktive Vorschau eines 3D-Assets auf der Seite mit der Detailansicht des Assets._
1. Führen Sie auf der Seite mit der Detailansicht des Assets für das 3D-Asset einen der folgenden Schritte aus:

   | Anzeigen | Beschreibung | Mausaktion | Touchscreen-Aktion |
   | --- | --- | --- | --- |
   | **Kamera drehen** | Drehen Sie die Ansicht um die 3D-Szene und Objekte. | Klicken und ziehen Sie mit der linken Maustaste. | Drücken und ziehen Sie mit einem Finger. |
   | **Kamera schwenken** | Schwenken Sie nach links, rechts, oben und unten. | Klicken und ziehen Sie mit der rechten Maustaste. | Drücken und ziehen Sie mit zwei Fingern. |
   | **Kamera zoomen** | Verschieben Sie Bereiche in die 3D-Szene ein- und aus ihnen. | Scrollen Sie mit dem Mausrad. | Bewegen Sie zwei Finger auseinander- bzw. zusammen. |
   | **Kamera neu zentrieren** | Zentrieren Sie die Kamera neu auf einen Punkt an einem Objekt in der 3D-Szene. | Doppelklicken. | Doppeltippen. |
   | **Zurücksetzen** | Tippen Sie unten rechts auf der Seite auf das Symbol „Zurücksetzen“, um den Zielpunkt der Ansicht wieder in die Mitte des 3D-Assets zu setzen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen. |  |  |
   | **Vollbildmodus** | Um in den Vollbildmodus zu wechseln, tippen Sie unten rechts auf Seite auf das Symbol „Vollbild“. |  |  |

1. Tippen Sie zum Abschluss unten rechts auf der Seite auf **[!UICONTROL Schließen]**.
