---
title: Imaging Transcoding Library
description: Erfahren Sie, wie Sie die Imaging Transcoding Library von Adobe konfigurieren und verwenden – eine Bildverarbeitungslösung, die zentrale Bildverarbeitungsfunktionen wie Kodierung, Transkodierung, Resampling und Größenänderung von Bildern ausführen kann.
contentOwner: AG
role: Admin
feature: Renditions,Developer Tools,Asset Processing
exl-id: b67465f9-177c-49c4-b4eb-a1d6e09ac9a2
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '975'
ht-degree: 100%

---

# Imaging Transcoding Library {#imaging-transcoding-library}

Die Adobe Imaging Transcoding Library ist eine proprietäre Bildverarbeitungslösung, die zentrale Bildbearbeitungsfunktionen durchführen kann, darunter:

* Kodierung
* Transkodierung (Konvertieren unterstützter Formate)
* Bild-Resampling mit PS- und Intel IPP-Algorithmen
* Beibehaltung der Bit-Tiefe und des Farbprofils
* JPEG-Qualitätskomprimierung
* Ändern der Bildgröße

Die Imaging Transcoding Library bietet CMYK-Unterstützung und vollständige Alpha-Unterstützung, außer CMYK-Alpha.

Neben der Unterstützung einer Vielzahl von Dateiformaten und Profilen bietet die Imaging Transcoding Library signifikante Vorteile im Vergleich zu anderen Lösungen von Drittanbietern hinsichtlich Leistung, Skalierbarkeit und Qualität. Hier nur einige Vorteile der Verwendung der Imaging Transcoding Library:

* **Skaliert mit zunehmender Dateigröße oder Auflösung**: Die Skalierung wird in erster Linie durch die patentierte Fähigkeit der Imaging Transcoding Library erreicht, die Größe während der Dekodierung von Dateien anzupassen. Dadurch wird sichergestellt, dass die Speichernutzung zur Laufzeit immer optimal ist und nicht eine quadratische Funktion der zunehmenden Dateigröße oder Megapixel-Auflösung ist. Die Imaging Transcoding Library kann größere und hochauflösende Dateien (mit höheren Megapixeln) verarbeiten. Drittanbieter-Tools wie ImageMagick können große Dateien nicht verarbeiten und stürzen bei der Verarbeitung solcher Dateien ab.
* **Komprimierungs- und Größenänderungsalgorithmen in Photoshop-Qualität**: Übereinstimmung mit dem Industriestandard in Bezug auf die Qualität des Downsamplings (glatt, scharf und automatisch bikubisch) und der Kompressionsqualität. Die Imaging Transcoding Library ermittelt außerdem den Qualitätsfaktor des Eingabebildes und setzt für das Ausgabebild intelligent Optimierungstabellen und Qualitätseinstellungen ein. Dies erzeugt Dateien in optimaler Größe, ohne Abstriche bei der visuellen Qualität.
* **Hoher Durchsatz:** Die Antwortzeit ist kürzer und der Durchsatz ist durchgängig höher als bei ImageMagick. Daher verringern sich mit der Imaging Transcoding Library die Wartezeiten für Benutzerinnen und Benutzer und die Kosten für das Hosting.
* **Bessere Skalierung bei gleichzeitiger Last:** Die Imaging Transcoding Library liefert optimale Leistung bei gleichzeitiger Last. Sie bietet hohen Durchsatz mit optimaler CPU-Leistung, Speichernutzung und niedriger Antwortzeit, was die Kosten für das Hosting verringert.

## Unterstützte Plattformen {#supported-platforms}

Die Imaging Transcoding Library ist nur für RHEL 7- und CentOS 7-Distributionen verfügbar.

>[!NOTE]
>
>MacOS und andere *nix-Distributionen (z. B. Debian und Ubuntu) werden nicht unterstützt.

## Nutzung {#usage}

Die Befehlszeilenargumente für die Imaging Transcoding Library können Folgendes enthalten:

```shell
 -destMime PNG/JPEG: Mime type of output rendition
 -BitDepth 8/16: Preserves Bit Depth. Bitdepth '4' is automatically converted to '8'
 -preserveBitDepth: Downscales Bit Depth (No upscaling)
 -preserveCMYK: Preserves CMYK color space
 -jpegQuality: Provides jpeg quality parameter (0-12 , corresponding to Photoshop qualities)
 -ResamplingMethod BiCubic/Lanczos/PSBicubic: Provides resampling methods. PSBicubic is a Photoshop quality resampling method.
 -resize
```

Für den Parameter `-resize` können folgende Optionen konfiguriert werden:

* `X`: Funktioniert ähnlich wie [!DNL Experience Manager]. Beispiel: -resize 319.
* `WxH`: Das Seitenverhältnis wird nicht beibehalten, z. B. `-resize 319x319`.
* `Wx`: Legt die Breite fest und berechnet die Höhe unter Beibehaltung des Seitenverhältnisses. Zum Beispiel: `-resize 319x`.
* `xH`: Legt die Höhe fest und berechnet die Breite unter Beibehaltung des Seitenverhältnisses. Zum Beispiel: `-resize x319`.

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Konfigurieren der Imaging Transcoding Library {#configuring-imaging-transcoding-library}

Erstellen Sie zum Konfigurieren der ITL-Verarbeitung eine Konfigurationsdatei und aktualisieren Sie den Workflow, um sie auszuführen.

### Erstellen einer Konfigurationsdatei für das extrahierte Bundle {#create-conf-file}

Um die Bibliothek zu konfigurieren, erstellen Sie eine CONF-Datei und geben Sie die Bibliotheken mithilfe der folgenden Schritte an. Sie benötigen Admin- oder Root-Berechtigungen.

1. Laden Sie das Paket mit der [Imaging Transcoding Library von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) herunter und installieren Sie es mit dem Paket-Manager. Das Paket ist kompatibel mit [!DNL Experience Manager] 6.5.

1. Die Bundle-ID für `com.day.cq.dam.cq-dam-switchengine` finden Sie, indem Sie sich bei der Web-Konsole anmelden und auf **[!UICONTROL OSGi]** > **[!UICONTROL Bundles]** klicken. Alternativ können Sie zum Öffnen der Bundles-Konsole die URL `https://[aem_server:[port]/system/console/bundles/` aufrufen. Suchen Sie das Bundle `com.day.cq.dam.cq-dam-switchengine` und seine ID.

1. Stellen Sie sicher, dass alle erforderlichen Bibliotheken extrahiert werden, indem Sie den Ordner mit dem Befehl `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` überprüfen, wobei der Ordnername die Bundle-ID enthält. Beispielsweise lautet der Befehl `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/`, wenn die Bundle-ID `588` ist.

1. Erstellen Sie eine Datei `SWitchEngineLibs.conf`, die mit der Bibliothek verknüpft wird.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Fügen Sie den Pfad `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` mit dem Befehl `cat SWitchEngineLibs.conf` der conf-Datei hinzu.

1. Führen Sie den Befehl `ldconfig` aus, um die erforderlichen Links und den Cache zu erstellen.

1. Bearbeiten Sie in dem Konto, das zum Starten von [!DNL Experience Manager] verwendet wird, die Datei `.bash_profile`. Fügen Sie `LD_LIBRARY_PATH` hinzu, indem Sie Folgendes hinzufügen.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Stellen Sie sicher, dass der Wert des Pfads auf `.` festgelegt ist, indem Sie den Befehl `echo $LD_LIBRARY_PATH` verwenden. Die Ausgabe sollte nur `.` sein. Wenn der Wert nicht auf `.` festgelegt ist, starten Sie die Sitzung neu.

### Konfigurieren Sie den Workflow [!UICONTROL DAM-Update-Asset]. {#configure-dam-asset-update-workflow}

Aktualisieren Sie den Workflow [!UICONTROL DAM-Update-Asset], um die Bibliothek zur Verarbeitung von Bildern zu verwenden.

1. Wählen Sie auf der [!DNL Experience Manager]-Benutzeroberfläche **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** aus.

1. Öffnen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM-Update-Asset]** im Bearbeitungsmodus.

1. Öffnen Sie den Workflow-Prozessschritt **[!UICONTROL Miniaturansichten verarbeiten]**. Fügen Sie auf der Registerkarte **[!UICONTROL Miniaturansichten]** die MIME-Typen, bei denen Sie den Standardprozess zum Generieren von Miniaturansichten überspringen möchten, zur Liste **[!UICONTROL MIME-Typen überspringen]** hinzu.
Wenn Sie z. B. Miniaturansichten für ein TIFF-Bild mit der Imaging Transcoding Library erstellen möchten, geben Sie in das Feld `image/tiff`MIME-Typen überspringen **[!UICONTROL den Text]** ein.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die MIME-Typen zur **[!UICONTROL Liste zum Überspringen]** hinzu, bei denen Sie den Standardprozess zum Generieren von Web-Ausgaben überspringen möchten. Wenn Sie z. B. im vorherigen Schritt den MIME-Typ `image/tiff` übersprungen haben, fügen Sie der Liste zum Überspringen `image/tiff` hinzu.

1. Öffnen Sie den Schritt **[!UICONTROL EPS-Miniaturen (unterstützt von ImageMagick)]** und navigieren Sie zur Registerkarte **[!UICONTROL Argumente]**. Fügen Sie der Liste **[!UICONTROL MIME-Typen]** die MIME-Typen hinzu, die die Imaging Transcoding Library verarbeiten soll. Wenn Sie z. B. im vorherigen Schritt den MIME-Typ `image/tiff` übersprungen haben, fügen Sie `image/jpeg` zur Liste **[!UICONTROL MIME-Typen]** hinzu.

1. Entfernen Sie die Standardbefehle, falls vorhanden.

1. Blenden Sie das seitliche Bedienfeld ein und fügen Sie aus der Liste der Schritte **[!UICONTROL SwitchEngine Handler]** hinzu.

1. Fügen Sie basierend auf Ihren benutzerdefinierten Anforderungen Befehle zu [!UICONTROL SwitchEngine Handler] hinzu. Passen Sie die Parameter der Befehle an, die Sie für Ihre Anforderungen angeben. Wenn Sie z. B. das Farbprofil Ihres JPEG-Bildes beibehalten möchten, fügen Sie die folgenden Befehle zur Liste **[!UICONTROL Befehle]** hinzu:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![chlimage](assets/chlimage_1-199.png)

1. (Optional) Generieren Sie mit einem einzelnen Befehl Miniaturansichten aus einer Zwischenausgabe. Die Zwischenausgabe dient als Quelle, um statische und Web-Ausgaben zu generieren. Diese Methode ist schneller als die frühere Methode. Mit dieser Methode können Sie jedoch keine benutzerdefinierten Parameter auf Miniaturen anwenden.

   ![chlimage](assets/chlimage_1-200.png)

1. Um Web-Ausgaben zu generieren, konfigurieren Sie Parameter auf der Registerkarte **[!UICONTROL Webfähiges Bild]**.

1. Synchronisieren Sie das aktualisierte Workflow-Modell [!UICONTROL DAM-Update-Asset]. Speichern Sie den Workflow.

Um die Konfiguration zu überprüfen, laden Sie ein TIFF-Bild hoch und überwachen Sie die Datei „error.log“. Ihnen werden `INFO`-Nachrichten auffallen, in denen `SwitchEngineHandlingProcess execute: executing command line` vorkommt. In den Protokollen werden die generierten Ausgabedarstellungen genannt. Sobald der Workflow abgeschlossen ist, können Sie die neuen Ausgabedarstellungen in [!DNL Experience Manager] anzeigen.

>[!MORELIKETHIS]
>
>* [Artikel zu unterstützten MIME-Typen](assets-formats.md#supported-image-transcoding-library)
