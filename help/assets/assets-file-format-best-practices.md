---
title: Empfohlene Verfahren zur Verarbeitung der unterstützten Dateiformate
description: Bewährte Verfahren zur Verarbeitung der verschiedenen unterstützten Dateitypen mit [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5069c2cd26e84866d72a61d36de085dadd556cdd
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 47%

---


# Best Practices für Dateiformate in Assets {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] unterstützt viele proprietäre und Drittanbieter-Dateiformatbibliotheken, um benutzerseitigen Bedarf an Dateiunterstützung zu decken. The supported Adobe libraries include, [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer, and [!DNL Adobe InDesign Server]. In addition, [!DNL Experience Manager Assets] supports third-party libraries, including [!DNL ImageMagick], [!DNL TwelveMonkeys], and so on.

Eine vollständige Liste der unterstützten Dateiformate finden Sie unter [Von Assets unterstützte Formate](/help/assets/assets-formats.md).

>[!TIP]
>
>If you are using [!DNL Experience Manager] on Adobe Managed Services (AMS), reach out to Adobe Customer Care if you plan to process lots of large PSD or PSB files. Wenden Sie sich an den Kundenbetreuer der Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Tools und Modelle für die proprietären Formate der Adobe auszuwählen. [!DNL Experience Manager] kann keine sehr hochauflösenden PSB-Dateien mit mehr als 30000 x 23000 Pixel verarbeiten.

## [!DNL Adobe Camera Raw] library {#adobe-camera-raw-library}

Für eine optimale Leistung empfiehlt Adobe die Verwendung der [!DNL Adobe Camera Raw] Bibliothek für RAW- und DNG-Dateien.

[!DNL Adobe Camera Raw] library unterstützt CMYK-Profil als Eingabe. Sie generiert die Ausgabe jedoch im RGB-Farbraum und unterstützt nur Darstellungen im JPEG-Format. Sie behält nicht den Quelldatei-Farbraum (z. B. CMYK) in den Miniaturen bei.

For more information, see [Camera Raw support](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-Bibliothek {#adobe-pdf-rasterizer-library}

Um optimale Ergebnisse zu erzielen, sollte die Adobe PDF Rasterizer-Bibliothek für folgende Dateien verwendet werden:

* Große PDF-Dateien mit viel Inhalt
* AI-Dateien mit nicht standardmäßig generierten Miniaturbildern
* Für AI-Dateien mit SPOT (PMS)-Farben

Die Miniaturbilder und Vorschauen, die mit PDF-Rasterizer generiert werden, haben eine bessere Qualität als die standardmäßige Rasterausgabe. Die Adobe PDF Rasterbibliothek unterstützt keine Farbraumkonvertierung. Unabhängig vom Farbraum der PDF-Quelldatei erzeugt Adobe PDF Rasterizer nur RGB-Ausgabe.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe empfiehlt, dass Sie [!DNL Adobe InDesign Server] zum Extrahieren [!DNL Adobe InDesign]spezifischer Darstellungen wie IDML und HTML verwenden. For more information, see [Adding Experience Manager assets as references in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] generiert und stellt mehrere Varianten von anspruchsvollem Inhalt über sein globales, skalierbares und leistungsoptimiertes Netzwerk bereit. Es dient der Bereitstellung interaktiver Erlebnisse und optimiert die Verwaltung digitaler Kampagnen. For details around enabling [!DNL Dynamic Media], see [Configuring Dynamic Media](/help/assets/config-dynamic.md).

Currently, [!DNL Dynamic Media] can support videos up to 15 GB of content per file.

## ImageMagick-Bibliothek {#imagemagick-library}

Adobe empfiehlt, die ImageMagick-Bibliothek für folgende Zwecke zu verwenden:

* Generieren von Miniaturausgabeformaten für EPS-Dateien.
* Beibehaltung von Bildprofilinformationen.
* Beibehaltung von Transparenz.
* Verarbeitung von PSD- und PSB-Dateien.

To know how to set up the [!DNL ImageMagick] library in [!DNL Experience Manager], see [Using ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Hinweise zur optimalen Verwendung finden Sie unter [Best Practices zur Konfiguration von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

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
