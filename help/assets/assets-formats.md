---
title: Unterstützte Dateiformate und MIME-Typen
description: Von [!DNL Assets] and [!DNL Dynamic Media] unterstützte Dateiformate und MIME-Typen sowie die für jedes Format unterstützten Funktionen.
contentOwner: AG
mini-toc-levels: 1
role: User, Admin
feature: Asset Management,Renditions
exl-id: a4bcf67b-54f4-4681-9e42-fd4753acde1a
source-git-commit: c8e83622070572d104f2cdc20c592ac2e9d0d31b
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 60%

---

# Unterstützte Formate in [!DNL Adobe Experience Manager Assets] {#assets-supported-formats}

[!DNL Experience Manager Assets] unterstützt eine breite Palette von Dateiformaten und jede Funktionalität bietet unterschiedliche Unterstützung für verschiedene MIME-Typen. Um [!DNL Assets] in andere standardkonforme DAM-Lösungen (Digital Asset Management) und Desktop-Software zu integrieren, verwenden Sie die [!DNL Extensible Metadata Platform]-Adobe (XMP).

Die Legende gibt den Grad der Unterstützung an.

| Unterstützungsebene | Beschreibung |
| :-----------: | ------------------------------ |
| ✓ | Unterstützt |
| * | Mit Funktionen von Zusatzmodulen unterstützt |
| − | Nicht zutreffend |

## Unterstützte Rasterbildformate in [!DNL Experience Manager] {#supported-raster-image-formats}

Folgende Rasterbildformate werden in [!DNL Assets] unterstützt:

| Format | Speicherung | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturansichten | Bearbeiten | Metadaten-Writeback | Insights |
| ------------ | :------: | :-----------------: | :-----------------: | :------------------: | :------: | :----------------: | :------: |
| PNG | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| GIF | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten |
| TIFF | verwalten | verwalten | verwalten | verwalten | - | verwalten | verwalten |
| JPEG | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| BMP | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten |
| PNM | verwalten | verwalten | - | - | - | - | verwalten |
| PGM | verwalten | verwalten | - | - | - | - | verwalten |
| PBM | verwalten | verwalten | - | - | - | - | verwalten |
| PPM | verwalten | verwalten | - | - | - | - | verwalten |
| PSD ‡ | verwalten | verwalten | verwalten | verwalten | - | - | verwalten |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten | - | verwalten | - |
| PICT | - | - | - | - | - | - | verwalten |
| PSB | verwalten | verwalten | verwalten | verwalten | - | - | - |

‡ Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Folgende Rasterbildformate werden in [!DNL Dynamic Media] unterstützt:

| Format | Upload<br> (Eingabeformat) | Erstellen<br> image<br> preset<br> (Ausgabeformat) | Vorschau<br> dynamische<br> Ausgabedarstellung | Bereitstellung<br> dynamischer<br> Ausgabedarstellung | Download<br> dynamische<br> Ausgabedarstellung |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | verwalten | verwalten | verwalten | verwalten | verwalten |
| GIF | verwalten | verwalten | verwalten | verwalten | verwalten |
| TIFF | verwalten | verwalten | verwalten | verwalten | verwalten |
| JPEG | verwalten | verwalten | verwalten | verwalten | verwalten |
| BMP | verwalten | - | - | - | - |
| PSD ‡ | verwalten | - | - | - | - |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten | verwalten |
| PICT | verwalten | - | - | - | - |

‡ Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Berücksichtigen Sie zusätzlich zu den oben genannten Informationen Folgendes:

* Die Unterstützung für EPS-Dateien gilt nur für Rasterbilder. Zum Beispiel wird die Erstellung von Miniaturansichten für Vektorbilder im EPS-Format nicht standardmäßig unterstützt. Um die Unterstützung hinzuzufügen, [konfigurieren Sie ImageMagick](best-practices-for-imagemagick.md). Informationen zur Integration von Drittanbieter-Tools zur Aktivierung zusätzlicher Funktionen finden Sie unter [Befehlszeilenbasierter Medien-Handler](media-handlers.md#command-line-based-media-handler).

* Metadaten-Writeback funktioniert für das PSB-Dateiformat, wenn es zum Handler `NComm` hinzugefügt wird.

* Informationen zum Verwenden von [!DNL Dynamic Media] für die Vorschau und Generierung dynamischer Ausgabeformate für EPS-Dateien finden Sie unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Metadaten-Writeback für EPS-Dateien wird ab Version 3.0 von PostScript Document Structuring Convention (PS-Adobe) unterstützt.

## Unterstützte 3D-Formate {#support-3d-formats}

Die folgende Liste von 3D-Formaten wird unterstützt.

Siehe [Arbeiten mit 3D-Assets in Dynamic Media](/help/assets/assets-3d.md).

| Format | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Miniaturansicht, Vorschau | 3D-Vorschau | Bereitstellung von Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | verwalten | verwalten | verwalten |  | verwalten | verwalten | - | - |
| gLB | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten | verwalten |
| gLTF | verwalten | verwalten | verwalten |  | verwalten | - | verwalten | - |
| OBJ | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten | verwalten |
| STL | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten | verwalten |
| USDz | verwalten | verwalten | verwalten | verwalten | verwalten | - | - | verwalten |

## Nicht unterstützte Rasterbildformate in Dynamic Media {#unsupported-image-formats-dynamic-media}

In der folgenden Liste werden die Untertypen von Rasterbilddateiformaten beschrieben, die in Dynamic Media nicht unterstützt werden.**

Siehe auch [Erkennung nicht unterstützter Dateiformate für Dynamic Media](https://helpx.adobe.com/experience-manager/kb/detect-unsupported-assets-for-dynamic-media.html).

* PNG-Dateien mit einer IDAT-Blockgröße größer als 100 MB.
* PSB-Dateien.
* PSD-Dateien mit einem anderen Farbraum als CMYK, RGB, Graustufen oder Bitmap werden nicht unterstützt. DuoTone-, Lab- und indizierte Farbräume werden nicht unterstützt.
* PSD-Dateien mit einer Bittiefe größer als 16.
* TIFF-Dateien mit Gleitkommadaten.
* TIFF-Dateien mit Lab-Farbraum.

<!-- Topic commented out for now as of March 31, 2020. The topic may still need adjustment so it can be published live, or it may be moved into a KB article instead. Just waiting on feedback in CQDOC-15657. - Rick
## Unsupported raster image formats in Dynamic Media (#unsupported-image-formats-dynamic-media)

The following table describes the sub-types of raster image formats that are *not* supported in Dynamic Media. The table also describes suggested methods you can use to detect such files.

| Format | What is unsupported? | Suggested detection method |
|---|---|---|
| JPEG  | Files where the initial three bytes is incorrect. | To identify a JPEG file, its initial three bytes must be `ff d8 ff`. If they are anything else, then it is not classified as a JPEG.<br>&bull; There is no software tool that can help with this issue.<br>&bull; A small C++/java program which reads the initial three bytes of a file should be able to detect these types of files.<br>&bull; It may be better to track the source of such files and look at the tool generating the file. |
| PNG |  Files that have an IDAT chunk size greater than 100 MB. | You can detect this issue using [libpng](http://www.libpng.org/pub/png/libpng.html) in C++. |
| PSB |  | Use exiftool if the file type is PSB.<br>Example in an ExifTool log:<br>1. File type: `PSB` |
| PSD | Files with a color space other than CMYK, RGB, Grayscale, or Bitmap are not supported.<br>DuoTone, Lab, and Indexed color spaces are not supported. | Use ExifTool if Color mode is Duotone.<br>Example in an ExifTool log:<br>1. Color mode: `Duotone` |
|  | Files with abrupt endings. | Adobe is unable to detect this condition. Also, such files cannot be opened with Adobe PhotoShop. Adobe suggests you examine the tool that was used to create such a file and troubleshoot at the source. |
|  | Files that have a bit depth greater than 16. | Use ExifTool if the bit depth is greater than 16.<br>Example in an ExifTool log:<br>1. Bit depth: `32` |
|  | File that have Lab color space. | Use exiftool if the color mode is Lab.<br>Example in an ExifTool log:<br>1. Color mode: `Lab` |
| TIFF | Files that have floating point data. That is, a TIFF file with 32-bit depth is not supported. | Use ExifTool if the MIME type is `image/tiff` and the SampleFormat has `Float` in its value. Example in an ExifTool log:<br>1. MIME type: `image/tiff`<br>Sample format: `Float #`<br>2. MIME type: `image/tiff`<br>Sample format: `Float; Float; Float; Float` |
|  | Files that have Lab color space. | Use ExifTool if the color mode is Lab.<br>Example in an ExifTool log:<br>1. Color mode: `Lab` |
-->

## Unterstützte PDF Rasterizer-Bibliothek {#supported-pdf-rasterizer-library}

Die Adobe PDF Rasterizer-Bibliothek generiert hochwertige Miniaturansichten und Vorschauen für große und inhaltsintensive [!DNL Adobe Illustrator]- und PDF-Dateien. Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für folgende Dateien:

* Inhaltsintensive KI-/PDF-Dateien, die ressourcenintensiv verarbeitet werden können.
* AI-/PDF-Dateien, für die standardmäßig keine Miniaturansichten generiert werden.
* AI-Dateien mit PMS-Farben (Pantone Matching System)

Siehe [Verwenden von PDF Rasterizer](aem-pdf-rasterizer.md).

## Unterstützte Bildtranskodierungsbibliothek {#supported-image-transcoding-library}

Bei der Adobe Imaging Transcoding Library handelt es sich um eine Lösung zur Bildverarbeitung, die essenzielle Bildfunktionen übernimmt, darunter Bildkodierung, -transkodierung, -Resampling und Größenanpassung.

Die Imaging Transcoding Library unterstützt Dateien in den Formaten JPG/JPEG, PNG (8-Bit und 16-Bit), GIF, BMP, TIFF/Komprimiertes TIFF (außer 32-Bit-TIFF- und PTIFF-Dateien), ICO sowie ICN MIME-Typen.

Siehe [Imaging Transcoding Library](imaging-transcoding-library.md).

## Unterstützung von Camera Raw {#supported-camera-raw}

Die [!DNL Adobe Camera Raw]-Bibliothek ermöglicht [!DNL Assets] die Aufnahme von Rohbildern. Siehe [Camera Raw Unterstützung](camera-raw.md).

## Unterstützte Dokumentenformate [!DNL Assets] {#supported-document-formats}

Folgende Dokumentenformate werden für Asset-Management-Funktionen unterstützt:

| Format | Speicherung | [Metadatenverwaltung](metadata.md) | Extraktion im Volltext<br> | [Metadatenextraktion](metadata.md) | Generierung von Miniaturansichten<br> | [Subasset-Extraktion](managing-linked-subassets.md) | [Metadaten-Writeback](xmp-writeback.md) | [Connected Assets](use-assets-across-connected-assets-instances.md) |
|---|---|---|---|---|---|---|---|---|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | - | verwalten | verwalten | verwalten | verwalten | - |
| DOC | verwalten | verwalten | verwalten | verwalten | - | - | - | verwalten |
| DOCX | verwalten | verwalten | verwalten | verwalten | - | - | - | verwalten |
| ODT | verwalten | verwalten | verwalten | - | - | - | - | verwalten |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| HTML | verwalten | verwalten | verwalten | - | - | - | - | verwalten |
| RTF | verwalten | verwalten | verwalten | - | - | - | - | verwalten |
| TXT | verwalten | verwalten | verwalten | - | - | - | - | verwalten |
| XLS | verwalten | verwalten | verwalten | - | - | - | - | verwalten |
| XLSX | verwalten | verwalten | verwalten | verwalten | - | - | - | verwalten |
| ODS | verwalten | verwalten | verwalten | - | - | - | - | - |
| PPT | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten |
| PPTX | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten |
| ODP | verwalten | verwalten | verwalten | - | - | - | - | - |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | verwalten | verwalten | - | verwalten | verwalten | verwalten | verwalten | - |
| PS | verwalten | verwalten | - | - | - | - | - | - |
| QXP | verwalten | verwalten | - | - | - | - | - | - |
| EPUB | verwalten | verwalten | - | verwalten | verwalten | - | - | - |

## Unterstützte Dokumentformate in Dynamic Media {#supported-document-formats-dynamic-media}

| Format | Upload<br> (Eingabeformat) | Erstellen<br> image<br> preset<br> (Ausgabeformat) | Vorschau<br> dynamische<br> Ausgabedarstellung | Bereitstellung<br> dynamischer<br> Ausgabedarstellung | Download<br> dynamische<br> Ausgabedarstellung |
|---|:---:|:---:|:---:|:---:|:---:|
| [KI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | - | - | - | - |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | verwalten | verwalten | verwalten | verwalten | verwalten |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | verwalten | - | - | - | - |

Berücksichtigen Sie zusätzlich zu den oben genannten Funktionen Folgendes:

* Um mithilfe von Dynamic Media dynamische Ausgaben für PDF-Dateien zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Um mithilfe von Dynamic Media dynamische Ausgaben für AI-Dateien in der Vorschau anzuzeigen und zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) 

* Informationen zum Generieren dynamischer Ausgabeformate für INDD-Dateien mit Dynamic Media finden Sie unter [InDesign (INDD)-Dateiformat](../assets/managing-image-presets.md#indesign-indd-file-format).

## Unterstützte Multimediaformate {#supported-multimedia-formats}

|  | Speicher | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturansichten | FFmpeg-Transkodierung |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | verwalten | verwalten | - | - | * |
| MIDI | verwalten | verwalten | - | - | * |
| 3GP | verwalten | verwalten | - | - | * |
| MP3 | verwalten | verwalten | verwalten | - | * |
| MPG | verwalten | verwalten | - | - | * |
| OGA | verwalten | verwalten | - | - | * |
| OGG | verwalten | verwalten | - | - | * |
| RA | verwalten | verwalten | - | - | * |
| WAV | verwalten | verwalten | - | - | * |
| WMA | verwalten | verwalten | - | - | * |
| DVI | verwalten | verwalten | - | * | * |
| FLV | verwalten | verwalten | - | * | * |
| M4V | verwalten | verwalten | - | * | * |
| MPEG | verwalten | verwalten | - | * | * |
| OGV | verwalten | verwalten | - | * | * |
| MOV | verwalten | verwalten | - | * | * |
| WMV | verwalten | verwalten | - | * | * |
| SWF | verwalten | verwalten | - | - | - |

## Unterstützte Eingabevideoformate in Dynamic Media zum Transkodieren {#supported-input-video-formats-for-dynamic-media-transcoding}

| Videodateierweiterung | Container | Empfohlene Video-Codecs | Nicht unterstützte Video-Codecs |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (alle Profile) | - |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (Vektoranimationsdateien) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft® Screen (MSS2), Microsoft® Foto Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| M4V | Apple iTunes | H264/AVC | - |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft® Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 | - |
| OGV, OGG | Ogg | Theora, VP3, Dirac | - |
| MKV | Matroska | H264/AVC | - |

## Unterstützte Archivformate {#supported-archive-formats}

Die unterstützten Archivformate und die Anwendbarkeit gemeinsamer DAM-Workflows werden in der folgenden Tabelle behandelt.

| Formate | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Bereitstellung dynamischer Medien |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | verwalten | verwalten | verwalten | verwalten | verwalten | - |
| JAR | verwalten | verwalten | verwalten | verwalten | verwalten | - |
| RAR | verwalten | verwalten | verwalten | verwalten | verwalten | - |
| TAR | verwalten | verwalten | verwalten | verwalten | verwalten | - |
| ZIP | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |

## Weitere unterstützte Formate {#other-supported-formats}

Die Anwendbarkeit der gängigen DAM-Funktionen für einige spezifische Dateiformate wird nachfolgend beschrieben.

| Formate | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Bereitstellung dynamischer Medien |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| SVG | verwalten | verwalten | verwalten | verwalten | verwalten | - |
| CSS | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| VTT | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| XML | verwalten | verwalten | verwalten | verwalten | verwalten | verwalten |
| Javascript (wenn mit eigener Bereitstellungsdomäne konfiguriert) | - | - | - | - | - | verwalten |

>[!NOTE]
>
>Das Hochladen und Verteilen von JavaScript-Dateien ist möglicherweise nicht sicher. Bei Bedarf können Sie Überlagerungen verwenden, um zu verhindern, dass Benutzer JS-Dateien hochladen.

## Unterstützte MIME-Typen {#supported-mime-types}

Standardmäßig erkennt [!DNL Experience Manager] den Dateityp mit der Dateierweiterung . [!DNL Experience Manager] kann es aus dem Inhalt der Dateien erkennen. Wählen Sie für letztere die Option [!UICONTROL MIME aus Inhalt erkennen] in [!UICONTROL Day CQ DAM Mime Type Service] in der Web-Konsole [!DNL Experience Manager].

Eine Liste der unterstützten MIME-Typen ist in CRXDE Lite unter `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes` verfügbar.

| Dateierweiterung | MIME-Typ/Internetmedientyp | Standardmäßiger jobParam-Wert | Zulässiger jobParam-Wert |
|---|---|---|---|
| Bild | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | Der standardmäßige jobParam-Wert gilt für alle Assets mit Bild-MIME-Typ.<ul><li>[knockoutBackgroundOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-knockout-background-options.html)</li><li>[manualCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-manual-crop-options.html)</li><li>[autoColorCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-color-crop-options.html)</li><li>[autoTransparentCropOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-transparent-crop-options.html)</li><li>[colorManagementOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-color-management-options.html)</li><li>[autoSetCreationOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-auto-set-creation-options.html)</li><li>[emailSetting](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/sting-constants/r-email-settings.html)</li><li>[xmpKeywords](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-xmp-keywords.html)</li><li>[unsharpMaskOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-unsharp-mask-options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li> [illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li></ul> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-pdf-options.html) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-post-script-options.html)</li><li>[illustratorOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-illustrator-options.html</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-options.html)</li><li>[photoshopLayerOptions](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-photoshop-layer-options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF/TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-exclude-master-video-from-avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Aktivieren Sie die Unterstützung](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support) von MIME-typbasierten Assets und Dynamic Media Classic-Upload-Auftragsparametern.
>* [Konfigurieren Sie die Unterstützung](config-dynamic.md) von MIME-typbasierten Upload-Auftragsparametern.

