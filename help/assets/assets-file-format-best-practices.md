---
title: Best Practices für die Verarbeitung der unterstützten Dateiformate
description: Best Practices für die Verarbeitung der verschiedenen unterstützten Dateitypen mithilfe von  [!DNL Experience Manager Assets].
contentOwner: AG
role: Admin
feature: Asset Management,Developer Tools
exl-id: da080f12-4cf7-4c26-901b-cd40d9c00bcb
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 100%

---

# Best Practices für Dateiformate in Assets {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] unterstützt viele proprietäre und Drittanbieter-Dateiformatbibliotheken, um benutzerseitigen Bedarf an Dateiunterstützung zu decken. Zu den unterstützten Adobe-Bibliotheken zählen [!DNL Adobe Camera Raw], Gibson, Adobe PDF Rasterizer und [!DNL Adobe InDesign Server]. Außerdem unterstützt [!DNL Experience Manager Assets] Drittanbieterbibliotheken wie [!DNL ImageMagick], [!DNL TwelveMonkeys] usw.

Eine vollständige Liste der unterstützten Dateiformate finden Sie unter [Von Assets unterstützte Formate](/help/assets/assets-formats.md).

>[!TIP]
>
>Wenn Sie [!DNL Experience Manager] in Adobe Managed Services (AMS) verwenden, wenden Sie sich an den Kunden-Support von Adobe, wenn Sie viele große PSD- oder PSB-Dateien verarbeiten möchten. Wenden Sie sich an den Support-Mitarbeiter von Adobe, um diese Best Practices für Ihre AMS-Bereitstellung zu implementieren und die bestmöglichen Tools und Modelle für die proprietären Formate von Adobe auszuwählen. [!DNL Experience Manager] kann keine extrem hochauflösenden PSB-Dateien mit mehr als 30.000 x 23.000 Pixel verarbeiten.

## [!DNL Adobe Camera Raw]-Bibliothek {#adobe-camera-raw-library}

Zur Leistungsoptimierung empfiehlt Adobe die Verwendung der [!DNL Adobe Camera Raw]-Bibliothek für RAW- und DNG-Dateien.

Die [!DNL Adobe Camera Raw]-Bibliothek unterstützt das CMYK-Farbprofil als Eingabe. Allerdings generiert es die Ausgabe im RGB-Farbraum und unterstützt nur die Ausgabe im JPEG-Format. Der Farbraum der Quelldatei (z. B. CMYK) wird in den Miniaturansichten nicht beibehalten.

Weitere Informationen finden Sie unter [Camera Raw-Unterstützung](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-Bibliothek {#adobe-pdf-rasterizer-library}

Damit Sie optimale Ergebnisse erzielen, empfiehlt Adobe die Verwendung der Adobe PDF Rasterizer-Bibliothek für die folgenden Dateien:

* Umfangreiche, inhaltsintensive PDF-Dateien
* KI-Dateien mit Miniaturansichten werden nicht standardmäßig generiert
* Für KI-Dateien mit SPOT-Farben (PMS)

Die Miniaturbilder und Vorschauen, die mit PDF-Rasterizer generiert werden, haben eine bessere Qualität als die standardmäßige Rasterausgabe. Die Adobe PDF Rasterizer-Bibliothek unterstützt keine Farbraumkonvertierung. Ungeachtet des Farbraums der Quell-PDF-Datei generiert Adobe PDF Rasterizer nur eine RGB-Ausgabe.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe empfiehlt, mithilfe von [!DNL Adobe InDesign Server] [!DNL Adobe InDesign]-spezifische Ausgabedarstellungen wie IDML und HTML zu extrahieren. Weitere Informationen finden Sie unter [Hinzufügen von Experience Manager-Assets als Referenzen in Adobe InDesign](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] generiert und stellt mehrere Varianten von anspruchsvollem Inhalt über sein globales, skalierbares und leistungsoptimiertes Netzwerk bereit. Es dient der Bereitstellung interaktiver Erlebnisse und optimiert die Verwaltung digitaler Kampagnen. Weitere Informationen zur Aktivierung von [!DNL Dynamic Media] finden Sie unter [Konfigurieren von Dynamic Media](/help/assets/config-dynamic.md).

Derzeit unterstützt [!DNL Dynamic Media] Videos mit bis zu 15 GB Inhalt pro Datei.

## ImageMagick-Bibliothek {#imagemagick-library}

Adobe empfiehlt, die ImageMagick-Bibliothek für folgende Zwecke zu verwenden:

* Zum Generieren von Miniatur-Ausgabedarstellungen für EPS-Dateien.
* Beibehaltung von Bildprofilinformationen.
* Beibehaltung von Transparenz.
* Verarbeitung von PSD- und PSB-Dateien.

Informationen dazu, wie die [!DNL ImageMagick]-Bibliothek in [!DNL Experience Manager] eingerichtet wird, finden Sie unter [Verwenden von ImageMagick](/help/assets/media-handlers.md#an-example-using-imagemagick). Informationen zur optimalen Verwendung finden Sie unter [Best Practices für die Konfiguration von ImageMagick](/help/assets/best-practices-for-imagemagick.md).

## Image Transcoding Library {#image-transcoding-library}

Bei der Adobe Imaging Transcoding Library handelt es sich um eine Lösung zur Bildverarbeitung, die essenzielle Bildfunktionen übernimmt, darunter Bildkodierung, -transkodierung, Größenanpassung usw.

Die Imaging Transcoding Library unterstützt die folgenden MIME-Typen:

* JPG/JPEG
* PNG (8 Bit und 16 Bit)
* GIF
* BMP
* TIFF/Komprimiertes TIFF (außer 32-Bit-Tiff und PTiff).
* ICO
* ICN

Weitere Informationen finden Sie unter [Imaging Transcoding Library](/help/assets/imaging-transcoding-library.md).
