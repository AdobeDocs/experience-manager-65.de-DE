---
title: Imaging Transcoding Library
description: Erfahren Sie, wie Sie die Adobe Imaging Transcoding Library – eine Lösung zur Bildverarbeitung, die essenzielle Bildfunktionen wie Bildkodierung, -transkodierung, -Resampling und Größenanpassung übernimmt – konfigurieren und verwenden.
contentOwner: AG
role: Admin
feature: Renditions,Developer Tools,Asset Processing
exl-id: b67465f9-177c-49c4-b4eb-a1d6e09ac9a2
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 38%

---

# Imaging Transcoding Library {#imaging-transcoding-library}

Die Adobe Imaging Transcoding Library ist eine proprietäre Bildverarbeitungslösung, die grundlegende Bildbearbeitungsfunktionen ausführen kann, wie:

* Kodierung
* Transkodierung (unterstützte Formate konvertieren)
* Resampling von Bildern, über PS- und Intel IPP-Algorithmen
* Beibehaltung von Bittiefe und Farbprofil
* JPEG-Qualitätskomprimierung
* Ändern der Bildgröße

Die Imaging Transcoding Library bietet CMYK-Unterstützung und vollständige Alpha-Unterstützung, außer CMYK -Alpha.

Die Imaging Transcoding Library unterstützt nicht nur eine Vielzahl von Dateiformaten und Profilen, sondern bietet auch erhebliche Vorteile gegenüber anderen Lösungen von Drittanbietern in Bezug auf Leistung, Skalierbarkeit und Qualität. Im Folgenden finden Sie einige der wichtigsten Vorteile der Verwendung der Imaging Transcoding Library:

* **Skaliert mit zunehmender Dateigröße oder Auflösung**: Die Skalierung wird primär über die patentierte Fähigkeit der Imaging Transcoding Library erzielt, die Größe während der Dekodierung von Dateien anzupassen. Dadurch wird sichergestellt, dass die Speicherverwendung während der Laufzeit immer optimal und keine quadratische Funktion der steigenden Dateigröße oder der Megapixel der Auflösung ist. Die Imaging Transcoding Library kann größere Dateien sowie Dateien mit hoher Auflösung (mit mehr Megapixel) verarbeiten. Tools von Drittanbietern, z. B. ImageMagick, können keine großen Dateien bearbeiten und stürzen bei der Verarbeitung solcher Dateien ab.
* **Komprimierung in Photoshop-Qualität und Algorithmen für die Größenänderung**: Entspricht dem Branchenstandard hinsichtlich der Qualität des Downsamplings (glatt, scharf und automatisch bikubisch) und der Komprimierungsqualität. Die Imaging Transcoding Library bewertet den Qualitätsfaktor des Eingabebilds weiter und verwendet intelligente, optimale Tabellen und Qualitätseinstellungen für das Ausgabebild. Dies erzeugt Dateien in optimaler Größe, ohne Abstriche bei der visuellen Qualität.
* **Hoher Durchsatz:** Die Antwortzeit ist niedriger und der Durchsatz ist durchgängig höher als ImageMagick. Daher sollte die Imaging Transcoding Library die Wartezeit für Benutzer und die Hosting-Kosten reduzieren.
* **Skalieren Sie bei gleichzeitiger Belastung besser:** Die Imaging Transcoding Library funktioniert unter gleichzeitigen Belastungsbedingungen optimal. Sie bietet hohen Durchsatz mit optimaler CPU-Leistung, Speichernutzung und niedriger Antwortzeit, was die Kosten für das Hosting verringert.

## Unterstützte Plattformen {#supported-platforms}

Die Imaging Transcoding Library ist nur für RHEL 7- und CentOS 7-Distributionen verfügbar.

>[!NOTE]
>
>Mac OS und andere *nix-Distributionen (z. B. Debian und Ubuntu) werden nicht unterstützt.

## Nutzung {#usage}

Die Imaging Transcoding Library bietet unter anderem folgende Befehlszeilenargumente:

```shell
 -destMime PNG/JPEG: Mime type of output rendition
 -BitDepth 8/16: Preserves Bit Depth. Bitdepth ‘4’ is automatically converted to ‘8’
 -preserveBitDepth: Downscales Bit Depth (No upscaling)
 -preserveCMYK: Preserves CMYK color space
 -jpegQuality: Provides jpeg quality parameter (0-12 , corresponding to Photoshop qualities)
 -ResamplingMethod BiCubic/Lanczos/PSBicubic: Provides resampling methods. PSBicubic is a Photoshop quality resampling method.
 -resize
```

Sie können die folgenden Optionen für die `-resize` Parameter:

* `X`: Funktioniert ähnlich wie [!DNL Experience Manager]. Beispiel: -resize 319.
* `WxH`: Das Seitenverhältnis wird nicht beibehalten, z. B. `-resize 319x319`.
* `Wx`: Legt die Breite fest und berechnet die Höhe mit Beibehaltung des Seitenverhältnisses. Beispiel `-resize 319x`.
* `xH`: Legt die Höhe fest und berechnet die Breite mit Beibehaltung des Seitenverhältnisses. Beispiel `-resize x319`.

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Konfigurieren der Imaging Transcoding Library {#configuring-imaging-transcoding-library}

Erstellen Sie zum Konfigurieren der ITL-Verarbeitung eine Konfigurationsdatei und aktualisieren Sie den Workflow, um sie auszuführen.

### Konfigurationsdatei für extrahiertes Bundle erstellen {#create-conf-file}

Um die Bibliothek zu konfigurieren, erstellen Sie eine CONF-Datei, um die Bibliotheken mithilfe der folgenden Schritte anzugeben. Sie benötigen Administrator- oder Root-Berechtigungen.

1. Laden Sie die [Imaging Transcoding Library-Paket von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) und installieren Sie es mit Package Manager. Das Paket ist kompatibel mit [!DNL Experience Manager] 6.5.

1. So kennen Sie die Bundle-ID für `com.day.cq.dam.cq-dam-switchengine`, melden Sie sich bei der Web-Konsole an und klicken Sie auf **[!UICONTROL OSGi]** > **[!UICONTROL Bundles]**. Alternativ können Sie zum Öffnen der Bundles-Konsole auf `https://[aem_server:[port]/system/console/bundles/` URL. Suchen `com.day.cq.dam.cq-dam-switchengine` Bundle und dessen ID.

1. Stellen Sie sicher, dass alle erforderlichen Bibliotheken extrahiert werden, indem Sie den Ordner mit dem Befehl `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/`, wobei der Ordnername mithilfe der Bundle-ID erstellt wird. Beispielsweise lautet der Befehl `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/` if bundle id is `588`.

1. Erstellen `SWitchEngineLibs.conf` -Datei, die mit der Bibliothek verknüpft werden soll.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Hinzufügen `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` Pfad zur conf-Datei mit `cat SWitchEngineLibs.conf` Befehl.

1. Ausführen `ldconfig` -Befehl, um die erforderlichen Links und den Cache zu erstellen.

1. In dem Konto, das zum Starten verwendet wird [!DNL Experience Manager]bearbeiten `.bash_profile` -Datei. Hinzufügen `LD_LIBRARY_PATH` indem Sie Folgendes hinzufügen.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. So stellen Sie sicher, dass der Wert des Pfads auf `.`, verwenden `echo $LD_LIBRARY_PATH` Befehl. Die Ausgabe sollte nur `.`. Wenn der Wert nicht auf `.`, starten Sie die Sitzung neu.

### Konfigurieren [!UICONTROL DAM-Update-Asset] Workflow {#configure-dam-asset-update-workflow}

Aktualisieren Sie die [!UICONTROL DAM-Update-Asset] -Workflow, um die Bibliothek zur Verarbeitung von Bildern zu verwenden.

1. In [!DNL Experience Manager] Benutzeroberfläche, wählen Sie **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Aus dem **[!UICONTROL Workflow-Modelle]** Seite, öffnen Sie die **[!UICONTROL DAM-Update-Asset]** Workflow-Modell im Bearbeitungsmodus.

1. Öffnen Sie die **[!UICONTROL Prozessminiaturansichten]** Workflow-Prozessschritt. Im **[!UICONTROL Miniaturen]** Registerkarte die MIME-Typen hinzufügen, für die Sie den standardmäßigen Prozess zur Erstellung von Miniaturansichten überspringen möchten, im **[!UICONTROL MIME-Typen überspringen]** Liste.
Wenn Sie beispielsweise mit der Imaging Transcoding Library Miniaturansichten für ein TIFF-Bild erstellen möchten, geben Sie `image/tiff` im **[!UICONTROL MIME-Typen überspringen]** -Feld.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die MIME-Typen zur **[!UICONTROL Liste zum Überspringen]** hinzu, bei denen Sie den Standardprozess zum Generieren von Web-Ausgaben überspringen möchten. Wenn Sie beispielsweise den MIME-Typ übersprungen haben `image/tiff` Fügen Sie im obigen Schritt `image/tiff` in die Liste zum Überspringen.

1. Öffnen Sie die **[!UICONTROL EPS-Miniaturansichten (unterstützt von ImageMagick)]** Schritt, navigieren Sie zum **[!UICONTROL Argumente]** Registerkarte. Im **[!UICONTROL MIME-Typen]** -Liste hinzufügen, fügen Sie die MIME-Typen hinzu, die die Imaging Transcoding Library verarbeiten soll. Wenn Sie beispielsweise den MIME-Typ übersprungen haben `image/tiff` Fügen Sie im obigen Schritt `image/jpeg` der **[!UICONTROL MIME-Typen]** Liste.

1. Entfernen Sie die Standardbefehle, falls vorhanden.

1. Blenden Sie das seitliche Bedienfeld ein und fügen Sie aus der Liste der Schritte **[!UICONTROL SwitchEngine Handler]** hinzu.

1. Hinzufügen von Befehlen zu [!UICONTROL SwitchEngine Handler] basierend auf Ihren benutzerdefinierten Anforderungen. Passen Sie die Parameter der Befehle an, die Sie für Ihre Anforderungen angeben. Wenn Sie z. B. das Farbprofil Ihres JPEG-Bildes beibehalten möchten, fügen Sie die folgenden Befehle zur Liste **[!UICONTROL Befehle]** hinzu:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![chlimage](assets/chlimage_1-199.png)

1. (Optional) Generieren Sie mithilfe eines einzelnen Befehls Miniaturansichten aus einer Zwischenausgabe. Die Zwischenausgabe dient als Quelle, um statische und Webausgaben zu generieren. Diese Methode ist schneller als die frühere Methode. Sie können mit dieser Methode jedoch keine benutzerdefinierten Parameter auf Miniaturen anwenden.

   ![chlimage](assets/chlimage_1-200.png)

1. Um Webausgabeformate zu generieren, konfigurieren Sie Parameter im **[!UICONTROL Webfähiges Bild]** Registerkarte.

1. Aktualisieren synchronisieren [!UICONTROL DAM-Update-Asset] Workflow-Modell. Speichern Sie den Workflow.

Überprüfen Sie die Konfiguration, laden Sie ein TIFF-Bild hoch und überwachen Sie die Datei error.log . Sie werden `INFO` Nachrichten mit Erwähnungen von `SwitchEngineHandlingProcess execute: executing command line`. In den Protokollen werden die generierten Ausgabedarstellungen erwähnt. Sobald der Workflow abgeschlossen ist, können Sie die neuen Ausgabedarstellungen in [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Artikel zu unterstützten MIME-Typen](assets-formats.md#supported-image-transcoding-library)

