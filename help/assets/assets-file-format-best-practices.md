---
title: Empfohlene Verfahren zur Verarbeitung der unterstützten Dateiformate
description: Bewährte Verfahren zur Verarbeitung der verschiedenen unterstützten Dateitypen unter Verwendung von [!DNL Experience Manager Assets].
contentOwner: AG
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 47%

---


# Best Practices für Dateiformate in Assets {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] unterstützt viele proprietäre und Drittanbieter-Dateiformatbibliotheken, um benutzerseitigen Bedarf an Dateiunterstützung zu decken. Zu den unterstützten Adoben-Bibliotheken gehören [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer und [!DNL Adobe InDesign Server]. Darüber hinaus unterstützt [!DNL Experience Manager Assets] Bibliotheken von Drittanbietern, einschließlich [!DNL ImageMagick], [!DNL TwelveMonkeys] usw.

Eine vollständige Liste der unterstützten Dateiformate finden Sie unter [Von Assets unterstützte Formate](/help/assets/assets-formats.md).

>[!TIP]
>
>Wenn Sie [!DNL Experience Manager] unter Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Kundendienst, wenn Sie eine große Anzahl von PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Kundenbetreuer der Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Tools und Modelle für die proprietären Formate der Adobe auszuwählen. [!DNL Experience Manager] kann keine sehr hochauflösenden PSB-Dateien mit mehr als 30000 x 23000 Pixel verarbeiten.

## [!DNL Adobe Camera Raw] library  {#adobe-camera-raw-library}

Für eine optimale Leistung empfiehlt Adobe die Verwendung der [!DNL Adobe Camera Raw]-Bibliothek für RAW- und DNG-Dateien.

[!DNL Adobe Camera Raw] library unterstützt CMYK-Profil als Eingabe. Sie generiert die Ausgabe jedoch im RGB-Farbraum und unterstützt nur Darstellungen im JPEG-Format. Sie behält nicht den Quelldatei-Farbraum (z. B. CMYK) in den Miniaturen bei.

Weitere Informationen finden Sie unter [Camera Raw support](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-Bibliothek {#adobe-pdf-rasterizer-library}

Um optimale Ergebnisse zu erzielen, sollte die Adobe PDF Rasterizer-Bibliothek für folgende Dateien verwendet werden:

* Große PDF-Dateien mit viel Inhalt
* AI-Dateien mit nicht standardmäßig generierten Miniaturbildern
* Für AI-Dateien mit SPOT (PMS)-Farben

Die Miniaturbilder und Vorschauen, die mit PDF-Rasterizer generiert werden, haben eine bessere Qualität als die standardmäßige Rasterausgabe. Die Adobe PDF Rasterbibliothek unterstützt keine Farbraumkonvertierung. Unabhängig vom Farbraum der PDF-Quelldatei erzeugt Adobe PDF Rasterizer nur RGB-Ausgabe.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe empfiehlt, [!DNL Adobe InDesign Server] zu verwenden, um [!DNL Adobe InDesign]-spezifische Darstellungen wie IDML und HTML zu extrahieren. Weitere Informationen finden Sie unter [Hinzufügen von Experience Manager-Assets als Referenzen in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] generiert und stellt mehrere Varianten von anspruchsvollem Inhalt über sein globales, skalierbares und leistungsoptimiertes Netzwerk bereit. Es dient der Bereitstellung interaktiver Erlebnisse und optimiert die Verwaltung digitaler Kampagnen. Weitere Informationen zum Aktivieren von [!DNL Dynamic Media] finden Sie unter [Konfigurieren von Dynamic Media](/help/assets/config-dynamic.md).

Zurzeit kann [!DNL Dynamic Media] Videos mit bis zu 15 GB Inhalt pro Datei unterstützen.

## ImageMagick-Bibliothek {#imagemagick-library}

Adobe empfiehlt, die ImageMagick-Bibliothek für folgende Zwecke zu verwenden:

* Generieren von Miniaturausgabeformaten für EPS-Dateien.
* Beibehaltung von Bildprofilinformationen.
* Beibehaltung von Transparenz.
* Verarbeitung von PSD- und PSB-Dateien.

Informationen zum Einrichten der Bibliothek [!DNL ImageMagick] in [!DNL Experience Manager] finden Sie unter [Verwenden von ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Hinweise zur optimalen Verwendung finden Sie unter [Best Practices zur Konfiguration von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Imaging Transcoding Library {#image-transcoding-library}

Die Adobe Imaging Transcoding Library ist eine Bildverarbeitungslösung, die Bildbearbeitungsfunktionen wie Bildkodierung, Transkodierung, Neuberechnung, Größenanpassung usw. ausführt.

Die Imaging Transcoding Library unterstützt folgende MIME-Typen:

* JPG/JPEG
* PNG (8 und 16 Bit)
* GIF
* BMP
* TIFF/Komprimiertes TIFF (außer 32-Bit-Tiff und PTiff).
* ICO
* ICN

Weitere Informationen finden Sie unter [Imaging Transcoding Library](/help/assets/imaging-transcoding-library.md).
