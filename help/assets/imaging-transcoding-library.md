---
title: Imaging Transcoding Library
description: Erfahren Sie, wie Sie die Adobe Imaging Transcoding Library – eine Lösung zur Bildverarbeitung, die essenzielle Bildfunktionen wie Bildkodierung, -transkodierung, -Resampling und Größenanpassung übernimmt – konfigurieren und verwenden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
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
* Komprimierung mit JPEG-Qualität
* Ändern der Bildgröße

Imaging Transcoding Library bietet CMYK-Unterstützung und vollständige Alpha-Unterstützung, mit Ausnahme von CMYK -Alpha.

Die Imaging Transcoding Library unterstützt nicht nur eine Vielzahl von Dateiformaten und Profilen, sondern bietet im Hinblick auf Leistung, Skalierbarkeit und Qualität auch gegenüber anderen Drittanbieterlösungen erhebliche Vorteile. Die Verwendung von Imaging Transcoding Library bietet folgende wichtige Vorteile:

* **Skaliert mit zunehmender Dateigröße oder Auflösung**: Die Skalierung wird primär über die patentierte Fähigkeit der Imaging Transcoding Library erzielt, die Größe während der Dekodierung von Dateien anzupassen. Dadurch wird sichergestellt, dass die Speicherverwendung während der Laufzeit immer optimal und keine quadratische Funktion der steigenden Dateigröße oder der Megapixel der Auflösung ist. Die Imaging Transcoding Library kann größere Dateien sowie Dateien mit hoher Auflösung (mit mehr Megapixel) verarbeiten. Tools von Drittanbietern, z. B. ImageMagick, können keine großen Dateien bearbeiten und stürzen bei der Verarbeitung solcher Dateien ab.
* **Komprimierung in Photoshop-Qualität und Algorithmen für die Größenänderung**: Entspricht dem Branchenstandard hinsichtlich der Qualität des Downsamplings (glatt, scharf und automatisch bikubisch) und der Komprimierungsqualität. Imaging Transcoding Library bewertet den Qualitätsfaktor des Eingabebilds weiter und verwendet auf intelligente Weise optimale Tabellen und Qualitätseinstellungen für das Ausgabebild. Dies erzeugt Dateien in optimaler Größe, ohne Abstriche bei der visuellen Qualität.
* **Hoher Durchsatz:** Die Antwortzeit ist niedriger und der Durchsatz ist durchgängig höher als ImageMagick. Daher sollten Imaging Transcoding Library die Wartezeit für Benutzer und die Hosting-Kosten verringern.
* **Bei gleichzeitiger Belastung besser skalieren:** Imaging Transcoding Library funktioniert unter gleichzeitigen Ladebedingungen optimal. Sie bietet hohen Durchsatz mit optimaler CPU-Leistung, Speichernutzung und niedriger Antwortzeit, was die Kosten für das Hosting verringert.

## Unterstützte Plattformen {#supported-platforms}

Imaging Transcoding Library ist nur für RHEL 7- und CentOS 7-Distributionen verfügbar.

>[!NOTE]
>
>Mac OS und andere *nix-Distributionen (z. B. Debian und Ubuntu) werden nicht unterstützt.

## Verwendung {#usage}

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

You can configure the following options for the `-resize` parameter:

* `X`: Funktioniert ähnlich wie [!DNL Experience Manager]. Beispiel: -resize 319.
* `WxH`: Das Seitenverhältnis wird beispielsweise nicht beibehalten `-resize 319x319`.
* `Wx`: Legt die Breite fest und berechnet die Höhe mit Beibehaltung des Seitenverhältnisses. Beispiel `-resize 319x`.
* `xH`: Legt die Höhe fest und berechnet die Breite mit Beibehaltung des Seitenverhältnisses. Beispiel `-resize x319`.

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Konfigurieren der Imaging Transcoding Library {#configuring-imaging-transcoding-library}

Um die ITL-Verarbeitung zu konfigurieren, erstellen Sie eine Konfigurationsdatei und aktualisieren Sie den Workflow, um sie auszuführen.

### Konfigurationsdatei für extrahiertes Bundle erstellen {#create-conf-file}

Um die Bibliothek zu konfigurieren, erstellen Sie eine CONF-Datei, um die Bibliotheken mit den folgenden Schritten anzuzeigen. Sie benötigen Administrator- oder Root-Berechtigungen.

1. Download the [Imaging Transcoding Library package from Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) and install it using the Package Manager. Das Paket ist mit [!DNL Experience Manager] 6.5 kompatibel.

1. Um eine Bündel-ID für `com.day.cq.dam.cq-dam-switchengine`zu ermitteln, melden Sie sich bei der Web-Konsole an und klicken Sie auf **[!UICONTROL OSGi]** > **[!UICONTROL Bundles]**. Alternativ können Sie zum Öffnen der Bündelkonsole auf die `https://[aem_server:[port]/system/console/bundles/` URL zugreifen. Suchen Sie nach `com.day.cq.dam.cq-dam-switchengine` Bundle und dessen ID.

1. Stellen Sie sicher, dass alle erforderlichen Bibliotheken extrahiert werden, indem Sie den Ordner mit dem Befehl überprüfen, `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/`wobei der Ordnername mit der Bündel-ID erstellt wird. Der Befehl lautet beispielsweise, `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/` wenn die Bündel-ID `588`lautet.

1. Erstellen Sie eine `SWitchEngineLibs.conf` Datei, die mit der Bibliothek verknüpft werden soll.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Hinzufügen `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` Pfad zur conf-Datei mit `cat SWitchEngineLibs.conf` Befehl.

1. Führen Sie `ldconfig` den Befehl aus, um die erforderlichen Links und den Cache zu erstellen.

1. Bearbeiten Sie die Datei in dem Konto, das zum Beginn verwendet wird [!DNL Experience Manager]`.bash_profile` . Hinzufügen `LD_LIBRARY_PATH` durch Hinzufügen folgender Elemente:

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Um sicherzustellen, dass der Wert des Pfads auf festgelegt ist, verwenden Sie `.`den `echo $LD_LIBRARY_PATH` Befehl. Die Ausgabe sollte einfach `.`sein. Wenn der Wert nicht auf `.`festgelegt ist, starten Sie die Sitzung neu.

### Arbeitsablauf für [!UICONTROL DAM-Aktualisierung von Assets] konfigurieren {#configure-dam-asset-update-workflow}

Aktualisieren Sie den Arbeitsablauf [!UICONTROL DAM Update Asset] , um die Bibliothek zur Bildverarbeitung zu verwenden.

1. Wählen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. From the **[!UICONTROL Workflow Models]** page, open the **[!UICONTROL DAM Update Asset]** workflow model in edit mode.

1. Open the **[!UICONTROL Process Thumbnails]** workflow process step. In the **[!UICONTROL Thumbnails]** tab, add the MIME types for which you want to skip the default thumbnail generation process in the **[!UICONTROL Skip Mime Types]** list.
For example, if you want to create thumbnails for a TIFF image using Imaging Transcoding Library, specify `image/tiff` in the **[!UICONTROL Skip Mime Types]** field.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die MIME-Typen zur **[!UICONTROL Liste zum Überspringen]** hinzu, bei denen Sie den Standardprozess zum Generieren von Web-Ausgaben überspringen möchten. For example, if you skipped MIME type `image/tiff` in the above step, add `image/tiff` to the skip list.

1. Open the **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** step, navigate to the **[!UICONTROL Arguments]** tab. In the **[!UICONTROL Mime Types]** list, add the MIME types you want Imaging Transcoding Library to process. For example, if you skipped the MIME type `image/tiff` in the above step, add `image/jpeg` to the **[!UICONTROL Mime Types]** list.

1. Entfernen Sie die Standardbefehle, falls vorhanden.

1. Blenden Sie das seitliche Bedienfeld ein und fügen Sie aus der Liste der Schritte **[!UICONTROL SwitchEngine Handler]** hinzu.

1. Hinzufügen Befehle für den [!UICONTROL SwitchEngine-Handler] entsprechend Ihren individuellen Anforderungen. Passen Sie die Parameter der von Ihnen angegebenen Befehle an Ihre Anforderungen an. Wenn Sie z. B. das Farbprofil Ihres JPEG-Bildes beibehalten möchten, fügen Sie die folgenden Befehle zur Liste **[!UICONTROL Befehle]** hinzu:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![CHlimage](assets/chlimage_1-199.png)

1. (Optional) Erstellen Sie Miniaturbilder aus einer Zwischendarstellung mit einem einzelnen Befehl. Die Zwischenausgabe dient als Quelle, um statische und Webausgaben zu generieren. Diese Methode ist schneller als die frühere Methode. Sie können mit dieser Methode jedoch keine benutzerdefinierten Parameter auf Miniaturen anwenden.

   ![CHlimage](assets/chlimage_1-200.png)

1. Um Webdarstellungen zu erstellen, konfigurieren Sie Parameter auf der Registerkarte &quot; **[!UICONTROL Web-aktiviertes Bild]** &quot;.

1. Sync the updated [!UICONTROL DAM Update Asset] workflow model. Speichern Sie den Workflow.

Überprüfen Sie die Konfiguration, laden Sie ein TIFF-Bild hoch und überwachen Sie die Datei &quot;error.log&quot;. Sie werden `INFO` Nachrichten mit Erwähnungen von bemerken `SwitchEngineHandlingProcess execute: executing command line`. In den Protokollen werden die generierten Darstellungen aufgeführt. Nach Abschluss des Workflows können Sie die neuen Darstellungen in [!DNL Experience Manager]bearbeiten.

>[!MORELIKETHIS]
>
>* [Artikel zu unterstützten MIME-Typen](assets-formats.md#supported-image-transcoding-library)

