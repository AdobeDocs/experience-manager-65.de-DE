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
feature: Panoramic Images,Asset Management
role: User, Admin
exl-id: 4d6fbeb1-94db-4154-9e41-b76033fb4398
source-git-commit: 363e5159d290ecfbf4338f6b9793e11b613389a5
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 100%

---

# Panoramabilder{#panoramic-images}

In diesem Abschnitt wird beschrieben, wie Sie mit dem Viewer für Panoramabilder Kugelpanoramen für ein intensives 360°-Betrachtungserlebnis eines Zimmers, einer Immobilie, eines Ortes oder einer Landschaft ausgeben können.

Informationen hierzu finden Sie unter [Verwalten von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md).

![panoramic-image2](assets/panoramic-image2.png)

## Hochladen von Assets für die Verwendung mit dem Viewer für Panoramabilder {#uploading-assets-for-use-with-the-panoramic-image-viewer}

Damit hochgeladene Assets als Kreispanoramen gelten und mit dem Viewer für Panoramabilder verwendet werden können, muss mindestens eine der beiden folgenden Eigenschaften zutreffen:

* Ein Seitenverhältnis von 2.
Die Standardeinstellung für das Seitenverhältnis von 2 in CRXDE Lite können Sie hier anpassen:
   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

* Mit den Keywords `equirectangular` oder `spherical` und `panorama` oder `spherical` und `panoramic` als Tags versehen. Weitere Informationen finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

Die Kriterien für das Seitenverhältnis sowie die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die WCM-Komponente `Panoramic Media`.

Weitere Informationen über den Upload von Assets für die Verwendung mit dem Viewer für Panoramabilder finden Sie unter [Hochladen von Assets](/help/assets/manage-assets.md#uploading-assets).

## Konfigurieren von Dynamic Media Classic {#configuring-dynamic-media-classic-scene}

Damit der Viewer für Panoramabilder in Adobe Experience Manager ordnungsgemäß funktioniert, müssen Sie die Viewer-Vorgabe für Panoramabilder mit Dynamic Media Classic und mit auf Dynamic Media Classic-spezifischen Metadaten synchronisieren, damit die Viewer-Vorgaben im JCR aktualisiert werden. Um diese Synchronisation durchzuführen, konfigurieren Sie Dynamic Media Classic wie folgt:

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Konto an.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Setup]** > **[!UICONTROL Anwendungseinrichtung]** > **[!UICONTROL Veröffentlichungseinrichtung]** > **[!UICONTROL Image-Server]**.
1. Wählen Sie auf der Image-Server-Veröffentlichungsseite im Dropdownmenü **[!UICONTROL Veröffentlichungskontext]** oben die Option **[!UICONTROL Image-Serving]** aus.

1. Suchen Sie auf derselben Image-Server-Veröffentlichungsseite die Überschrift **[!UICONTROL Anfrage-Attribute]**.
1. Suchen Sie unter der Überschrift „Anfrage-Attribute“ die Option **[!UICONTROL Maximale Größe des Antwortbildes]**. Erhöhen Sie anschließend die Werte in den entsprechenden Feldern „Breite“ und „Höhe“ auf die größtmögliche Bildgröße für Panoramabilder.

   Bei Dynamic Media Classic liegt die Obergrenze bei 25.000.000 Pixel. Die zulässige Maximalgröße für Bilder mit einem Seitenverhältnis von 2:1 ist 7000 x 3500. In der Regel ist für Desktopbildschirme jedoch eine Größe von 4096 x 2048 Pixel ausreichend.

   >[!NOTE]
   >
   >Es werden nur Bilder innerhalb der zulässigen Maximalgröße unterstützt. Anfragen zu Bildern oberhalb der Obergrenze geben einen „403“-Fehler zurück.

1. Gehen Sie unter der Überschrift „Anfrage-Attribute“ wie folgt vor:

   * Legen Sie den Anfragenverschleierungsmodus auf **[!UICONTROL Deaktiviert]** fest.
   * Legen Sie den Anfragensperrmodus auf **[!UICONTROL Deaktiviert]** fest.

   Diese Einstellungen sind für die Verwendung der `Panoramic Media`-WCM-Komponente in Experience Manager erforderlich.

1. Klicken Sie unten links auf der Image-Server-Veröffentlichungsseite auf **[!UICONTROL Speichern]**.

1. Klicken Sie rechts unten auf **[!UICONTROL Schließen]**.

### Fehlerbehebung in der WCM-Komponente für Panoramamedien {#troubleshooting-the-panoramic-media-wcm-component}

Wenn Sie ein Bild in der Panoramamedienkomponente in WCM abgelegt haben und der Platzhalter der Komponente ausgeblendet ist, helfen Ihnen möglicherweise die folgenden Schritte zur Fehlerbehebung:

* Wenn Ihnen ein 403-Fehler (Forbidden) angezeigt wird, liegt es möglicherweise daran, dass die angefragte Bildgröße den Grenzwert überschreitet. Überprüfen Sie die Einstellungen für **[!UICONTROL Maximale Größe des Antwortbildes]** in [Konfigurieren von Dynamic Media Classic](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene).

* Überprüfen Sie im Falle einer „ungültigen Sperre“ für das Asset oder einem auf der Seite angezeigten „Parsing-Fehler“ den Anfragenverschleierungs- sowie den Anfragensperrmodus, um sicherzustellen, dass diese Modi deaktiviert sind.
* Bei einer Fehlermeldung zu einer beschädigten Arbeitsfläche können Sie „Pfad der Regelsatzdefinitionsdatei und CTN ungültig machen“ für die vorangegangenen Anfragen für das Bild-Asset einrichten.
* Wenn die Bildqualität infolge einer Bildanforderung mit einer Größe, die den unterstützten Bereich überschreitet, sehr gering wird, stellen Sie sicher, dass die Einstellung **[!UICONTROL JPEG-Codierungsattribute > Qualität]** nicht leer ist. Eine typische Einstellung für das Feld **[!UICONTROL Qualität]** ist `95`. Sie finden die Einstellung auf der Image-Server-Veröffentlichungsseite. Weitere Informationen über den Zugriff auf die Seite finden Sie unter [Konfigurieren von Dynamic Media Classic](/help/assets/panoramic-images.md#configuring-dynamic-media-classic-scene).

## Vorschau von Panoramabildern {#previewing-panoramic-images}

Siehe [Anzeigen von Assets in der Vorschau](/help/assets/previewing-assets.md).

## Panoramabilder veröffentlichen {#publishing-panoramic-images}

Siehe [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).
