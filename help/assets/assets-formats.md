---
title: Von Assets unterstützte Formate
description: Liste der Dateiformate, die von AEM Assets und von Dynamic Media unterstützt werden, sowie der für jedes Format unterstützten Funktionen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 593c1e1954a1c8e0355ede9889caed05ff72f3f9

---


# Unterstützte Asset-Formate {#assets-supported-formats}

AEM Assets unterstützt eine breite Palette von Dateiformaten und jede Funktionalität bietet unterschiedliche Unterstützung für verschiedene MIME-Typen.

Um AEM Assets mit anderen standardkonformen DAM-Lösungen (Digital Asset Management) und Desktop-Software-Anwendungen zu integrieren, verwenden Sie die Extensible Metadata Platform (XMP) von Adobe.

Die Legende gibt den Grad der Unterstützung an.

| Unterstützungsebene | Beschreibung |
|:---:|---|
| ✓ | Unterstützt |
| * | Mit Funktionen von Zusatzmodulen unterstützt |
| − | Nicht zutreffend |

## Unterstützte Rasterbildformate in AEM Assets {#supported-raster-image-formats}

| Format | Speicher | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturansichten | Interaktive Bearbeitung | Metadaten-Writeback | Einblicke |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PNM | ✓ | ✓ |  |  |  |  | ✓ |
| PGM | ✓ | ✓ |  |  |  |  | ✓ |
| PBM | ✓ | ✓ |  |  |  |  | ✓ |
| PPM | ✓ | ✓ |  |  |  |  | ✓ |
| PSD ‡ | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ |  | ✓ |  |
| PICT |  |  |  |  |  |  | ✓ |
| PSB | ✓ | ✓ | ✓ | ✓ |  |  |  |

‡ Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

## Unterstützte Rasterbildformate in dynamischen Medien (#supported-raster-image-formats-dynamic-media)

| Format | Upload<br> (Input format) | Create<br> image<br> preset<br> (Output format) | Preview<br> dynamic<br> rendition | Deliver<br> dynamic<br> rendition | Download<br> dynamic<br> rendition |
|---|:---:|:---:|:---:|:---:|:---:|
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ |  |  |  |  |
| PSD **‡** | ✓ |  |  |  |  |
| [EPS](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ |  |  |  |  |

**‡** Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von Adobe Photoshop generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Berücksichtigen Sie zusätzlich zu den oben genannten Informationen Folgendes:

* Die Unterstützung für EPS-Dateien gilt nur für Rasterbilder. Zum Beispiel wird die Erstellung von Miniaturansichten für Vektorbilder im EPS-Format nicht standardmäßig unterstützt. Um die Unterstützung hinzuzufügen, [konfigurieren Sie ImageMagick](best-practices-for-imagemagick.md). Informationen zum Integrieren von Werkzeugen von Drittanbietern, um zusätzliche Funktionen zu aktivieren, finden Sie unter [Befehlszeilenbasierter Media Handler](media-handlers.md#command-line-based-media-handler).

* Metadata writeback works for PSB file format when it is added to the `NComm` handler.

* Um mithilfe von Dynamic Media dynamische Ausgaben für EPS-Dateien in der Vorschau anzuzeigen und zu generieren, informieren Sie sich unter [Dateiformate Adobe Illustrator (AI), Postscript (EPS) und PDF](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

* Metadaten-Writeback für EPS-Dateien wird ab Version 3.0 von PostScript Document Structuring Convention (PS-Adobe) unterstützt.

## Nicht unterstützte Rasterbildformate in dynamischen Medien (#unsupported-image-formats-dynamic-media)

Die folgende Tabelle beschreibt die Untertypen der Rasterbildformate, die in dynamischen Medien *nicht* unterstützt werden. In der Tabelle werden auch empfohlene Methoden beschrieben, mit denen Sie solche Dateien erkennen können.

| Format | Was wird nicht unterstützt? | Vorgeschlagene Erkennungsmethode |
|---|---|---|
| JPEG | Dateien, bei denen die ersten drei Byte falsch sind. | Um eine JPEF-Datei zu identifizieren, müssen die ersten drei Byte `ff d8 ff`vorhanden sein. Wenn es sich um etwas Anderes handelt, wird es nicht als JPEG klassifiziert.<br>・ Es gibt kein Software-Werkzeug, das bei diesem Problem helfen kann.<br>・ Ein kleines C++/java-Programm, das die ersten drei Byte einer Datei liest, sollte diese Dateitypen erkennen können.<br>・ Es ist möglicherweise besser, die Quelle solcher Dateien zu verfolgen und das Tool zu sehen, das die Datei generiert. |
| PNG | Dateien mit einer IDAT-Größe größer als 100 MB. | Sie können dieses Problem mithilfe von [libpng](http://www.libpng.org/pub/png/libpng.html) in C++ erkennen. |
| PSB |  | Verwenden Sie exiftool, wenn der Dateityp PSB ist.<br>Beispiel in einem ExifTool-Protokoll:<br>1. Dateityp: `PSB` |
| PSD | Dateien mit einem anderen Farbraum als CMYK, RGB, Graustufen oder Bitmap werden nicht unterstützt.<br>DuoTone-, Lab- und indizierte Farbräume werden nicht unterstützt. | Verwenden Sie ExifTool, wenn der Farbmodus Duplex ist.<br>Beispiel in einem ExifTool-Protokoll:<br>1. Farbmodus: `Duotone` |
|  | Dateien mit abrupten Endungen. | Adobe kann diese Bedingung nicht erkennen. Solche Dateien können auch nicht mit Adobe FotoShop geöffnet werden. Adobe empfiehlt Ihnen, das Tool, das zum Erstellen einer solchen Datei verwendet wurde, zu prüfen und eine Fehlerbehebung an der Quelle vorzunehmen. |
|  | Dateien mit einer Bittiefe größer als 16. | Verwenden Sie ExifTool, wenn die Bittiefe größer als 16 ist.<br>Beispiel in einem ExifTool-Protokoll:<br>1. Bittiefe: `32` |
|  | Datei mit Lab-Farbraum. | Verwenden Sie exiftool, wenn der Farbmodus Lab ist.<br>Beispiel in einem ExifTool-Protokoll:<br>1. Farbmodus: `Lab` |
| TIFF | Dateien mit Gleitkommadaten. Das heißt, eine TIFF-Datei mit 32-Bit-Tiefe wird nicht unterstützt. | Verwenden Sie ExifTool, wenn der MIME-Typ `image/tiff` und der SampleFormat-Wert `Float` darin enthalten ist. Beispiel in einem ExifTool-Protokoll:<br>1. MIME-Typ: `image/tiff`<br>Beispielformat: `Float #`<br>2. MIME-Typ: `image/tiff`<br>Beispielformat: `Float; Float; Float; Float` |
|  | Dateien mit Lab-Farbraum. | Verwenden Sie ExifTool, wenn der Farbmodus Lab ist.<br>Beispiel in einem ExifTool-Protokoll:<br>1. Farbmodus: `Lab` |

## Unterstützte PDF Rasterizer-Bibliothek {#supported-pdf-rasterizer-library}

Die Adobe PDF Rasterizer-Bibliothek generiert hochwertige Miniaturansichten und Vorschauen für große und ressourcenintensive Adobe Illustrator- und PDF-Dateien. Adobe empfiehlt die Verwendung der PDF Rasterizer-Bibliothek für folgende Dateien:

* Inhaltsintensive AI-/PDF-Dateien, die ressourcenintensiv zu verarbeiten sind.
* AI-/PDF-Dateien, für die standardmäßig keine Miniaturansichten generiert werden.
* AI-Dateien mit PMS-Farben (Pantone Matching System)

See [Using PDF Rasterizer](aem-pdf-rasterizer.md).

## Supported Image Transcoding library {#supported-image-transcoding-library}

Die Adobe Imaging Transcoding-Bibliothek ist eine Bildverarbeitungslösung, die Bildbearbeitungsfunktionen wie Kodierung, Transkodierung, Neuberechnung und Größenanpassung ausführt.

Die Imaging Transcoding Library unterstützt Dateien in den Formaten JPG/JPEG, PNG (8-Bit und 16-Bit), GIF, BMP, TIFF/Komprimiertes TIFF (außer 32-Bit-TIFF- und PTIFF-Dateien), ICO sowie ICN MIME-Typen.

See [Imaging Transcoding Library](imaging-transcoding-library.md).

## Supported camera raw {#supported-camera-raw}

Die Adobe Camera Raw-Bibliothek aktiviert AEM Assets für die Aufnahme von Rohbildern. See [Camera Raw support](camera-raw.md).

## Unterstützte Asset-Dokument-Formate {#supported-document-formats}

Folgende Dokument-Formate werden für Asset-Management-Funktionen unterstützt:

| Format | Speicher | Metadata<br> management | Metadata<br> extraction | Thumbnail<br> generation | Interactive<br> editing | Metadata<br> writeback | [Einblicke](touch-ui-asset-insights.md) | [Connected Assets](use-assets-across-connected-assets-instances.md) |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |  |
| DOC | ✓ | ✓ | ✓ | ✓ |  |  |  | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ |  |  |  | ✓ |
| ODT | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| RTF | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| TXT | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| XLS | ✓ | ✓ | ✓ |  |  |  |  | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ |  |  |  | ✓ |
| ODS | ✓ | ✓ | ✓ |  |  |  |  |  |
| PPT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |  | ✓ |
| ODP | ✓ | ✓ | ✓ |  |  |  |  |  |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ |  |
| PS | ✓ | ✓ |  |  |  |  |  |  |
| QXP | ✓ | ✓ |  |  |  |  |  |  |
| EPUB | ✓ | ✓ |  | ✓ | ✓ |  |  |  |

## Unterstützte Dokument-Formate in dynamischen Medien (#supported-Dokument-formats-dynamic-media)

| Format | Upload<br> (Input format) | Create<br> image<br> preset<br> (Output format) | Preview<br> dynamic<br> rendition | Deliver<br> dynamic<br> rendition | Download<br> dynamic<br> rendition |
|---|:---:|:---:|:---:|:---:|:---:|
| [AI](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ |  |  |  |  |
| [PDF](managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ |
| [INDD](managing-image-presets.md#indesign-indd-file-format) | ✓ |  |  |  |  |

Berücksichtigen Sie zusätzlich zu den oben genannten Funktionen Folgendes:

* Um mithilfe von Dynamic Media dynamische Ausgaben für PDF-Dateien zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats)

* Um mithilfe von Dynamic Media dynamische Ausgaben für AI-Dateien in der Vorschau anzuzeigen und zu generieren, informieren Sie sich unter [Adobe Illustrator (AI)-, PostScript (EPS)- und PDF-Dateiformate.](../assets/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) 

* To use Dynamic Media to generate dynamic renditions for INDD files, see [InDesign (INDD) file format](../assets/managing-image-presets.md#indesign-indd-file-format).

## Unterstützte Multimediaformate {#supported-multimedia-formats}

|  | Speicher | Metadatenverwaltung | Metadatenextraktion | Generierung von Miniaturansichten | FFMPEG-Transkodierung |
|:---|:---:|:---:|:---:|:---:|:---:|
| AAC | ✓ | ✓ |  | − | * |
| MIDI | ✓ | ✓ |  | − | * |
| 3GP | ✓ | ✓ |  | − | * |
| MP3 | ✓ | ✓ | ✓ | − | * |
| MPG | ✓ | ✓ |  | − | * |
| OGA | ✓ | ✓ |  | − | * |
| OGG | ✓ | ✓ |  | − | * |
| RA | ✓ | ✓ |  | − | * |
| WAV | ✓ | ✓ |  | − | * |
| WMA | ✓ | ✓ |  | − | * |
| DVI | ✓ | ✓ |  | * | * |
| FLV | ✓ | ✓ |  | * | * |
| M4V | ✓ | ✓ |  | * | * |
| MPEG | ✓ | ✓ |  | * | * |
| OGV | ✓ | ✓ |  | * | * |
| MOV | ✓ | ✓ |  | * | * |
| WMV | ✓ | ✓ |  | * | * |
| SWF | ✓ | ✓ |  |  |  |

## Supported input video formats in Dynamic Media for transcoding {#supported-input-video-formats-for-dynamic-media-transcoding}

| Videodateierweiterung | Container | Empfohlene Video-Codecs | Nicht unterstützte Video-Codecs |
|---|---|---|---|
| MP4 | MPEG-4 | H264/AVC (alle Profile) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (Vektoranimationsdateien) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Red Raw Video | MJPEG 2000 |  |
| RAM, RM | RealVideo | Nicht unterstützt | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | Free Lossless Audio Codec |  |
| MJ2 | Motion JPEG2000 | Motion JPEG 2000 Codec |  |

## Unterstützte Archivformate {#supported-archive-formats}

Die unterstützten Archivformate und die Anwendbarkeit gemeinsamer DAM-Workflows werden in der folgenden Tabelle behandelt.

| Formate | Speicher | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Bereitstellung dynamischer Medien |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| TGZ | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| JAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| RAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| TAR | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| ZIP | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

## Weitere unterstützte Formate {#other-supported-formats}

Die Anwendbarkeit allgemeiner DAM-Workflows für einige weitere Dateiformate wird in der folgenden Tabelle beschrieben. Die üblichen DAM-Funktionen wie Datenspeicherung, Versionierung, ACL, Workflow, Veröffentlichung und Metadatenverwaltung, mit Ausnahme von Dynamic Media Versand, werden für alle Dateien unterstützt.

| Formate | Speicher | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Bereitstellung dynamischer Medien |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| SVG | ✓ | ✓ | ✓ | ✓ | ✓ |  |
| CSS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| VTT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Javascript (wenn mit eigener Bereitstellungsdomäne konfiguriert) |  |  |  |  |  | ✓ |

## Unterstützte MIME-Typen {#supported-mime-types}

Standardmäßig erkennt AEM den Dateityp mit der Dateierweiterung. AEM kann es anhand des Inhalts der Dateien erkennen. For latter, select [!UICONTROL Detect MIME from content] option in [!UICONTROL Day CQ DAM Mime Type Service] in the AEM Web Console.

Eine Liste der unterstützten MIME-Typen ist in CRXDE Lite unter `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`.

Siehe [Konfigurieren von Unterstützung für MIME-Typ-basierte Upload-Auftragsparameter](config-dynamic.md).

See also [Enabling MIME type-based Assets/Scene7 upload job parameter support](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

| Dateierweiterung | MIME-Typ/Internetmedientyp | Standardmäßiger jobParam-Wert | Zulässiger jobParam-Wert |
|---|---|---|---|
| Bild | image/s7asset | `usmAmount=1.75&usmRadius=0.2`<br>`&usmThreshold=2&usmMonochrome=0&` | Der standardmäßige jobParam-Wert gilt für alle Assets mit Bild-MIME-Typ.<ul><li>[knockoutBackgroundOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_knockout_background_options.html)</li><li>manualCropOptions</li><li>[autoColorCropOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_auto_color_crop_options)</li><li>[autoTransparentCropOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_auto_transparent_crop_options)</li><li>[colorManagementOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_color_management_options.html)</li><li>[autoSetCreationOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_auto_set_creation_options.html)</li><li>[emailSetting](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/string_constants/index.html?f=r_email_settings)</li><li>[xmpKeywords](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_xmp_keywords)</li><li>[unsharpMaskOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_unsharp_mask_options.html)</li></ul> |
| 3G2 | video/3gpp2 |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| 3GP | video/3gpp |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_exclude_master_video_from_avs) |
| AAC | audio/x-aac |  |  |
| AFM | application/x-font-type1 |  |  |
| AI | application/postscript | `aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_post_script_options.html)</li><li> [illustratorOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_illustrator_options.html)</li></ul> |
| AIFF | audio/x-aiff |  |  |
| AVI | video/x-msvideo |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| BMP | image/bmp |  |  |
| CSS | text/css |  |  |
| DOC | application/msword |  |  |
| EPS | <ul><li>application/postscript</li><li>application/eps</li><li>application/x-eps</li><li>image/eps</li><li>image/x-eps</li></ul> |  |  |
| F4V | video/x-f4v |  | ExcludeMasterVideoFromAVS |
| FLA | application/x-shockwave-flash |  |  |
| FLV | video/x-flv |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| FPX | image/vnd.fpx |  |  |
| GIF | image/gif |  |  |
| ICC | application/vnd.iccprofile |  |  |
| ICM | application/vnd.iccprofile |  |  |
| INDD | application/x-indesign |  |  |
| JPEG | image/jpeg |  |  |
| JPG | image/jpeg |  |  |
| M2V | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| M4V | video/x-m4v |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MOV | video/quicktime |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MP3 | audio/mpeg |  |  |
| MP4 | video/mp4 |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MPEG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MPG | video/mpeg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| MTS | model/vnd.mts |  |  |
| OGV | video/ogg |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| OTF | application/x-font-otf |  |  |
| PDF | application/pdf | `pdfprocess=Rasterize&resolution=150`<br>`&colorspace=Auto&pdfbrochure=false`<br>`&keywords=false&links=false` | [pdfOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_pdf_options) |
| PFB | application/x-font-type1 |  |  |
| PFM | application/x-font-type1 |  |  |
| PICT | image/x-pict |  |  |
| PNG | image/png |  |  |
| PPT | application/vnd.ms-powerpoint |  |  |
| PS | application/postscript | `psprocess=Rasterize&psresolution=150`<br>`&pscolorspace=Auto&psalpha=false`<br>`&psextractsearchwords=false`<br>`&aiprocess=Rasterize&airesolution=150`<br>`&aicolorspace=Auto&aialpha=false` | <ul><li>[postScriptOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_post_script_options)</li><li>[illustratorOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/index.html?f=r_illustrator_options)</li></ul> |
| PSD | image/vnd.adobe.photoshop | `process=None&layerNaming=Layername`<br>`&anchor=Center&createTemplate=false`<br>`&extractText=false&extendLayers=false` | <ul><li>[photoshopOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/?f=r_photoshop_options)</li><li>[photoshopLayerOptions](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_photoshop_layer_options.html)</li></ul> |
| RTF | application/rtf |  |  |
| SVG | image/svg+xml |  |  |
| SWF | application/x-shockwave-flash |  |  |
| TAR | application/x-tar |  |  |
| TIF / TIFF | image/tiff |  |  |
| TTC | application/x-font-ttf |  |  |
| TTF | application/x-font-ttf |  |  |
| VOB | video/dvd |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| VTT | text/vtt |  |  |
| WAV | audio/x-wav |  |  |
| WEBM | video/webm |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| WMA | audio/x-ms-wma |  |  |
| WMV | video/x-ms-wmv |  | [ExcludeMasterVideoFromAVS](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/types/r_exclude_master_video_from_avs.html) |
| XLS | application/vnd.ms-excel |  |  |
| ZIP | application/zip |  |  |

>[!MORELIKETHIS]
>
>* [Aktivieren der Unterstützung von MIME-Typen-basierten Assets/Scene7-Upload-Auftragsparametern](../sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

