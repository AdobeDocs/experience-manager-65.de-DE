---
title: Best Practices zur Verarbeitung der unterstützten Dateiformate
description: Best Practices zur Verarbeitung der verschiedenen unterstützten Dateitypen mithilfe von  [!DNL Experience Manager Assets].
contentOwner: AG
role: Administrator
feature: Asset Management,Entwicklertools
exl-id: da080f12-4cf7-4c26-901b-cd40d9c00bcb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 46%

---

# Best Practices für Dateiformate in Assets {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] unterstützt viele proprietäre und Drittanbieter-Dateiformatbibliotheken, um benutzerseitigen Bedarf an Dateiunterstützung zu decken. Zu den unterstützten Adobe-Bibliotheken gehören [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer und [!DNL Adobe InDesign Server]. Darüber hinaus unterstützt [!DNL Experience Manager Assets] Drittanbieterbibliotheken, einschließlich [!DNL ImageMagick], [!DNL TwelveMonkeys] usw.

Eine vollständige Liste der unterstützten Dateiformate finden Sie unter [Von Assets unterstützte Formate](/help/assets/assets-formats.md).

>[!TIP]
>
>Wenn Sie [!DNL Experience Manager] in Adobe Managed Services (AMS) verwenden, wenden Sie sich an die Kundenunterstützung von Adobe, wenn Sie eine Vielzahl großer PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Kundenbetreuer von Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Tools und Modelle für die proprietären Formate von Adobe auszuwählen. [!DNL Experience Manager] kann keine sehr hochauflösenden PSB-Dateien verarbeiten, die mehr als 30000 x 23000 Pixel sind.

## [!DNL Adobe Camera Raw] Bibliothek  {#adobe-camera-raw-library}

Für optimale Leistung empfiehlt Adobe die Verwendung der [!DNL Adobe Camera Raw]-Bibliothek für RAW- und DNG-Dateien.

[!DNL Adobe Camera Raw] -Bibliothek unterstützt das CMYK-Farbprofil als Eingabe. Sie generiert die Ausgabe jedoch im RGB-Farbraum und unterstützt nur Darstellungen im JPEG-Format. Sie behält nicht den Quelldatei-Farbraum (z. B. CMYK) in den Miniaturen bei.

Weitere Informationen finden Sie unter [Camera Raw Unterstützung](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-Bibliothek {#adobe-pdf-rasterizer-library}

Um optimale Ergebnisse zu erzielen, sollte die Adobe PDF Rasterizer-Bibliothek für folgende Dateien verwendet werden:

* Große PDF-Dateien mit viel Inhalt
* AI-Dateien mit nicht standardmäßig generierten Miniaturbildern
* Für AI-Dateien mit SPOT (PMS)-Farben

Die Miniaturbilder und Vorschauen, die mit PDF-Rasterizer generiert werden, haben eine bessere Qualität als die standardmäßige Rasterausgabe. Die Adobe PDF Rasterizer-Bibliothek unterstützt keine Farbraumkonvertierung. Unabhängig vom Farbraum der PDF-Quelldatei erzeugt Adobe PDF Rasterizer nur RGB-Ausgaben.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe empfiehlt die Verwendung von [!DNL Adobe InDesign Server] zum Extrahieren von [!DNL Adobe InDesign]-spezifischen Ausgabeformaten wie IDML und HTML. Weitere Informationen finden Sie unter [Hinzufügen von Experience Manager-Assets als Referenzen in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] generiert und stellt mehrere Varianten von anspruchsvollem Inhalt über sein globales, skalierbares und leistungsoptimiertes Netzwerk bereit. Es dient der Bereitstellung interaktiver Erlebnisse und optimiert die Verwaltung digitaler Kampagnen. Weitere Informationen zur Aktivierung von [!DNL Dynamic Media] finden Sie unter [Konfigurieren von Dynamic Media](/help/assets/config-dynamic.md).

Derzeit kann [!DNL Dynamic Media] Videos mit bis zu 15 GB Inhalt pro Datei unterstützen.

## ImageMagick-Bibliothek {#imagemagick-library}

Adobe empfiehlt, die ImageMagick-Bibliothek für folgende Zwecke zu verwenden:

* Generieren von Miniaturausgabeformaten für EPS-Dateien.
* Beibehaltung von Bildprofilinformationen.
* Beibehaltung von Transparenz.
* Verarbeitung von PSD- und PSB-Dateien.

Informationen zum Einrichten der [!DNL ImageMagick]-Bibliothek in [!DNL Experience Manager] finden Sie unter [Verwenden von ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Hinweise zur optimalen Verwendung finden Sie unter [Best Practices zur Konfiguration von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Imaging Transcoding Library {#image-transcoding-library}

Die Adobe Imaging Transcoding Library ist eine Bildverarbeitungslösung, die zentrale Bildbearbeitungsfunktionen wie Bildkodierung, -transkodierung, Neuberechnung, Größenanpassung usw. durchführt.

Die Imaging Transcoding Library unterstützt folgende MIME-Typen:

* JPG/JPEG
* PNG (8 und 16 Bit)
* GIF
* BMP
* TIFF/Komprimiertes TIFF (außer 32-Bit-Tiff und PTiff).
* ICO
* ICN

Weitere Informationen finden Sie unter [Imaging Transcoding Library](/help/assets/imaging-transcoding-library.md).
