---
title: Bewährte Verfahren zur Verarbeitung der verschiedenen unterstützten Dateiformate mit AEM Assets.
description: Bewährte Verfahren zur Verarbeitung der verschiedenen unterstützten Dateitypen mit AEM Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 70a88085a0fd6e949974aa7f1f92fdc3def3d98e

---


# Best Practices für Dateiformate in Assets {#assets-file-format-best-practices}

AEM Assets unterstützt viele proprietäre und Drittanbieter-Dateiformatbibliotheken, um benutzerseitigen Bedarf an Dateiunterstützung zu decken. Zu den unterstützten Adobe-Bibliotheken zählen Adobe Camera Raw, Gibson, Adobe PDF Rasterizer und Adobe InDesign Server. Außerdem unterstützt AEM Assets Drittanbieterbibliotheken, darunter ImageMagick, TwelveMonkeys usw.

Eine vollständige Liste der unterstützten Dateiformate finden Sie unter [Von Assets unterstützte Formate](/help/assets/assets-formats.md).

>[!TIP]
>
>Wenn Sie Experience Manager unter Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Adobe-Support, wenn Sie viele große PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Kundenbetreuer von Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Werkzeuge und Modelle für die proprietären Formate von Adobe auszuwählen.

## Adobe Camera Raw-Bibliothek {#adobe-camera-raw-library}

Zur optimalen Leistung empfiehlt Adobe die Verwendung der Adobe Camera Raw-Bibliothek für RAW- und DNG-Dateien.

Die Adobe Camera Raw-Bibliothek unterstützt das CMYK-Farbprofil als Eingabe. Sie generiert die Ausgabe jedoch im RGB-Farbraum und unterstützt nur Darstellungen im JPEG-Format. Sie behält nicht den Quelldatei-Farbraum (z. B. CMYK) in den Miniaturen bei.

For more information, see [Camera Raw support](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-Bibliothek {#adobe-pdf-rasterizer-library}

Um optimale Ergebnisse zu erzielen, sollte die Adobe PDF Rasterizer-Bibliothek für folgende Dateien verwendet werden:

* Große PDF-Dateien mit viel Inhalt
* AI-Dateien mit nicht standardmäßig generierten Miniaturbildern
* Für AI-Dateien mit SPOT (PMS)-Farben

Die Miniaturbilder und Vorschauen, die mit PDF-Rasterizer generiert werden, haben eine bessere Qualität als die standardmäßige Rasterausgabe. Die Adobe PDF Raster-Bibliothek unterstützt keine Farbraumkonvertierung. Unabhängig vom Farbraum der PDF-Quelldatei erzeugt Adobe PDF Raster nur RGB-Ausgaben.

## Adobe InDesign Server {#adobe-indesign-server}

Adobe empfiehlt, InDesign Server zu verwenden, um die InDesign-spezifischen Ausgaben von Adobe, darunter IDML und HTML, zu extrahieren. For more information, see [Adding AEM assets as references in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## Dynamic Media  {#dynamic-media}

Dynamic Media generiert und stellt mehrere Varianten von anspruchsvollem Inhalt über sein globales, skalierbares und leistungsoptimiertes Netzwerk bereit. Es dient der Bereitstellung interaktiver Erlebnisse und optimiert die Verwaltung digitaler Kampagnen. Weitere Informationen zur Aktivierung von Dynamic Media finden Sie unter [Konfigurieren von Dynamic Media](/help/assets/config-dynamic.md).

Derzeit unterstützt Dynamic Media Videos mit bis zu 20 GB Inhalt pro Datei.

## ImageMagick-Bibliothek {#imagemagick-library}

Adobe empfiehlt, die ImageMagick-Bibliothek für folgende Zwecke zu verwenden:

* Generieren von Miniaturausgabeformaten für EPS-Dateien
* Beibehaltung von Bildprofilinformationen
* Beibehaltung von Transparenz
* Verarbeitung von PSD- und PSB-Dateien

To know how to set up the ImageMagic library in AEM, see [Using ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Hinweise zur optimalen Verwendung finden Sie unter [Best Practices zur Konfiguration von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

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

For details, see [Imaging Transcoding Library](/help/assets/imaging-transcoding-library.md).
