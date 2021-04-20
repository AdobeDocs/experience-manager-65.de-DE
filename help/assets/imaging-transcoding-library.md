---
title: Imaging Transcoding Library
description: Erfahren Sie, wie Sie die Adobe Imaging Transcoding Library – eine Lösung zur Bildverarbeitung, die essenzielle Bildfunktionen wie Bildkodierung, -transkodierung, -Resampling und Größenanpassung übernimmt – konfigurieren und verwenden.
contentOwner: AG
role: Administrator
feature: Renditions,Developer Tools,Asset Processing
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '998'
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
* **Hoher Durchsatz:** Die Reaktionszeit ist niedriger und der Durchsatz ist konsistent höher als ImageMagick. Daher sollten Imaging Transcoding Library die Wartezeit für Benutzer und die Hosting-Kosten verringern.
* **Bessere Skalierung bei gleichzeitiger Belastung:** Imaging Transcoding Library funktioniert unter gleichzeitigen Ladebedingungen optimal. Sie bietet hohen Durchsatz mit optimaler CPU-Leistung, Speichernutzung und niedriger Antwortzeit, was die Kosten für das Hosting verringert.

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

Sie können die folgenden Optionen für den Parameter `-resize` konfigurieren:

* `X`: Funktioniert ähnlich wie  [!DNL Experience Manager]. Beispiel: -resize 319.
* `WxH`: Das Seitenverhältnis wird beispielsweise nicht beibehalten  `-resize 319x319`.
* `Wx`: Legt die Breite fest und berechnet die Höhe mit Beibehaltung des Seitenverhältnisses. Beispiel `-resize 319x`.
* `xH`: Legt die Höhe fest und berechnet die Breite mit Beibehaltung des Seitenverhältnisses. Beispiel `-resize x319`.

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Konfigurieren der Imaging Transcoding Library {#configuring-imaging-transcoding-library}

Um die ITL-Verarbeitung zu konfigurieren, erstellen Sie eine Konfigurationsdatei und aktualisieren Sie den Workflow, um sie auszuführen.

### Konfigurationsdatei für extrahiertes Bundle {#create-conf-file} erstellen

Um die Bibliothek zu konfigurieren, erstellen Sie eine CONF-Datei, um die Bibliotheken mit den folgenden Schritten anzuzeigen. Sie benötigen Administrator- oder Root-Berechtigungen.

1. Laden Sie das [Imaging Transcoding Library-Paket von der Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) herunter und installieren Sie es mithilfe des Package Managers. Das Paket ist mit [!DNL Experience Manager] 6.5 kompatibel.

1. Um eine Bündel-ID für `com.day.cq.dam.cq-dam-switchengine` zu kennen, melden Sie sich bei der Web-Konsole an und klicken Sie auf **[!UICONTROL OSGi]** > **[!UICONTROL Pakete]**. Alternativ können Sie zum Öffnen der Bundles-Konsole auf die URL `https://[aem_server:[port]/system/console/bundles/` zugreifen. Suchen Sie das Bundle `com.day.cq.dam.cq-dam-switchengine` und dessen ID.

1. Stellen Sie sicher, dass alle erforderlichen Bibliotheken extrahiert werden, indem Sie den Ordner mit dem Befehl `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` überprüfen, wobei der Ordnername mit der Bündel-ID erstellt wird. Beispiel: Der Befehl ist `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/`, wenn die Bündel-ID `588` lautet.

1. Erstellen Sie die Datei `SWitchEngineLibs.conf`, um eine Verknüpfung zur Bibliothek herzustellen.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. hinzufügen `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` Pfad zur conf-Datei mit dem Befehl `cat SWitchEngineLibs.conf`.

1. Führen Sie den Befehl `ldconfig` aus, um die erforderlichen Links und den Cache zu erstellen.

1. Bearbeiten Sie in dem Konto, das zum Beginn von [!DNL Experience Manager] verwendet wird, die Datei `.bash_profile`. hinzufügen `LD_LIBRARY_PATH` durch Hinzufügen des Folgenden.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Um sicherzustellen, dass der Wert des Pfads auf `.` eingestellt ist, verwenden Sie den Befehl `echo $LD_LIBRARY_PATH`. Die Ausgabe sollte einfach `.` sein. Wenn der Wert nicht auf `.` festgelegt ist, starten Sie die Sitzung neu.

### [!UICONTROL DAM-Update-Asset]-Workflow {#configure-dam-asset-update-workflow} konfigurieren

Aktualisieren Sie den Workflow [!UICONTROL DAM Update Asset], um die Bibliothek zur Verarbeitung von Bildern zu verwenden.

1. Wählen Sie in der [!DNL Experience Manager]-Benutzeroberfläche **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.

1. Öffnen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** das Workflow-Modell **[!UICONTROL DAM-Update-Asset]** im Bearbeitungsmodus.

1. Öffnen Sie den Workflow-Prozessschritt **[!UICONTROL Prozessminiaturen]**. Fügen Sie auf der Registerkarte **[!UICONTROL Miniaturansichten]** die MIME-Typen hinzu, für die Sie den standardmäßigen Miniaturbildgenerierungsvorgang in der Liste **[!UICONTROL MIME-Typen überspringen]** überspringen möchten.
Wenn Sie beispielsweise mit der Imaging Transcoding Library Miniaturbilder für ein TIFF-Bild erstellen möchten, geben Sie `image/tiff` im Feld **[!UICONTROL Mime-Typen]** überspringen ein.

1. Fügen Sie auf der Registerkarte **[!UICONTROL Webfähiges Bild]** die MIME-Typen zur **[!UICONTROL Liste zum Überspringen]** hinzu, bei denen Sie den Standardprozess zum Generieren von Web-Ausgaben überspringen möchten. Wenn Sie beispielsweise im obigen Schritt den MIME-Typ `image/tiff` übersprungen haben, fügen Sie `image/tiff` zur Liste zum Überspringen hinzu.

1. Öffnen Sie den Schritt **[!UICONTROL EPS-Miniaturansichten (powered by ImageMagick)]** und navigieren Sie zur Registerkarte **[!UICONTROL Argumente]**. Fügen Sie in der Liste **[!UICONTROL Mime-Typen]** die MIME-Typen hinzu, die von der Imaging Transcoding Library verarbeitet werden sollen. Wenn Sie beispielsweise im obigen Schritt den MIME-Typ `image/tiff` übersprungen haben, fügen Sie `image/jpeg` zur Liste **[!UICONTROL Mime-Typen]** hinzu.

1. Entfernen Sie die Standardbefehle, falls vorhanden.

1. Blenden Sie das seitliche Bedienfeld ein und fügen Sie aus der Liste der Schritte **[!UICONTROL SwitchEngine Handler]** hinzu.

1. hinzufügen Befehle zum [!UICONTROL SwitchEngine-Handler] je nach Ihren individuellen Anforderungen. Passen Sie die Parameter der von Ihnen angegebenen Befehle an Ihre Anforderungen an. Wenn Sie z. B. das Farbprofil Ihres JPEG-Bildes beibehalten möchten, fügen Sie die folgenden Befehle zur Liste **[!UICONTROL Befehle]** hinzu:

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![CHlimage](assets/chlimage_1-199.png)

1. (Optional) Erstellen Sie Miniaturbilder aus einer Zwischendarstellung mit einem einzelnen Befehl. Die Zwischenausgabe dient als Quelle, um statische und Webausgaben zu generieren. Diese Methode ist schneller als die frühere Methode. Sie können mit dieser Methode jedoch keine benutzerdefinierten Parameter auf Miniaturen anwenden.

   ![CHlimage](assets/chlimage_1-200.png)

1. Um Webdarstellungen zu erstellen, konfigurieren Sie Parameter auf der Registerkarte **[!UICONTROL Web-aktiviertes Bild]**.

1. Synchronisieren Sie das aktualisierte Workflow-Modell [!UICONTROL DAM Update Asset]. Speichern Sie den Workflow.

Überprüfen Sie die Konfiguration, laden Sie ein TIFF-Bild hoch und überwachen Sie die Datei &quot;error.log&quot;. Sie werden `INFO` Meldungen mit Erwähnungen von `SwitchEngineHandlingProcess execute: executing command line` bemerken. In den Protokollen werden die generierten Darstellungen aufgeführt. Nach Abschluss des Workflows können Sie die neuen Darstellungen in [!DNL Experience Manager] Ansicht haben.

>[!MORELIKETHIS]
>
>* [Artikel zu unterstützten MIME-Typen](assets-formats.md#supported-image-transcoding-library)

