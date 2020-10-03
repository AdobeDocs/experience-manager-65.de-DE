---
title: Digitale Assets verwalten
description: Erfahren Sie mehr über die Asset-Management-Aufgaben wie Hochladen, Herunterladen, Bearbeiten, Suchen, Löschen, Anmerkungen und Version Ihrer digitalen Assets.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 087940d0a51c43125a309b34b82831030e7e54b4
workflow-type: tm+mt
source-wordcount: '9618'
ht-degree: 61%

---


# Manage your digital assets {#manage-digital-assets}

In [!DNL Adobe Experience Manager Assets] diesem Fall können Sie mehr tun, als nur Ihre Assets zu speichern und zu steuern. [!DNL Experience Manager] angebote zur Asset-Verwaltung auf Unternehmensebene. Sie können Assets bearbeiten und freigeben, erweiterte Suchen durchführen, mehrere Darstellungen von Dutzenden von unterstützten Dateiformaten erstellen, Versionen und digitale Rechte verwalten, die Verarbeitung von Assets automatisieren, Metadaten verwalten und steuern, mit Anmerkungen zusammenarbeiten und vieles mehr.

In diesem Artikel werden die grundlegenden Aufgaben zur Asset-Verwaltung wie Erstellen oder Hochladen beschrieben. Metadaten-Aktualisierungen; Kopieren, Verschieben und Löschen; Veröffentlichen, Rückgängigmachen der Veröffentlichung und Suchen von Assets. Informationen zur Benutzeroberfläche finden Sie unter [Erste Schritte mit der Benutzeroberfläche](/help/sites-authoring/basic-handling.md)für Assets. To manage Content Fragments, see [manage Content Fragments](/help/assets/content-fragments/content-fragments-managing.md) assets.

## Erstellen von Ordnern {#creating-folders}

Wenn Sie eine Sammlung von Assets organisieren, etwa alle `Nature`-Aufnahmen, können Sie Ordner erstellen, um diese zu gruppieren. Mit Ordnern können Sie Assets kategorisieren und organisieren. [!DNL Experience Manager Assets]Bei müssen Sie Assets nicht in Ordner organisieren, um besser zu arbeiten.

>[!NOTE]
>
>* Sharing an [!DNL Assets] folder of the type `sling:OrderedFolder` is not supported when sharing to Marketing Cloud. Wenn Sie einen Ordner freigeben möchten, wählen Sie beim Erstellen eines Ordners nicht [!UICONTROL Geordnet] aus.
>* [!DNL Experience Manager]In ist die Verwendung von `subassets` als Ordnername nicht zulässig. Es ist ein Schlüsselwort, das für Knoten reserviert ist, die Teilassets für zusammengesetzte Assets enthalten.


1. Navigieren Sie zu dem Ort in Ihrem Ordner „Digitale Assets“, an dem Sie einen neuen Ordner erstellen möchten. Klicken Sie im Menü auf **[!UICONTROL Erstellen]**. Wählen Sie **[!UICONTROL Neuer Ordner]** aus.
1. Geben Sie in das Feld **[!UICONTROL Titel]** einen Ordnernamen an. DAM verwendet standardmäßig den Titel, den Sie als Ordnernamen angegeben haben. Wenn der Ordner erstellt wurde, können Sie die Standardeinstellung außer Kraft setzen und einen anderen Ordnernamen angeben.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ihr Ordner wird im Ordner „Digitale Assets“ angezeigt.

Die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) werden nicht unterstützt:

* Der Name einer Asset-Datei darf keines der folgenden Zeichen enthalten: `* / : [ \\ ] | # % { } ? &`
* Der Name eines Asset-Ordners darf keines der folgenden Zeichen enthalten: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

Fügen Sie keine Sonderzeichen in die Erweiterungen der Asset-Dateinamen ein.

## Hochladen von Assets {#uploading-assets}

<!-- TBD the following:
Move this section into a new article. CQDOC-14874 ticket is created for this.
In this complete article, replace emphasis with UICONTROL where appropriate.
-->

You can upload various types of assets (including images, PDF files, RAW files, and so on) from your local folder or a network drive to [!DNL Experience Manager Assets].

>[!NOTE]
>
>Im Dynamic Media Scene 7-Modus können Sie nur Assets mit einer Dateigröße von maximal 2 GB hochladen.

Sie können Assets in Ordnern mit oder ohne zugewiesenem Verarbeitungsprofil hochladen.

Für Ordner mit zugewiesenem Verarbeitungsprofil wird der Profilname in der Miniaturansicht der Kartenansicht angezeigt. In der Listenansicht wird der Profilname in der Spalte **Verarbeitungsprofil** angezeigt. Siehe [Verarbeitungsprofile](/help/assets/processing-profiles.md).

Before uploading an asset, ensure that it is in a [format](/help/assets/assets-formats.md) that [!DNL Experience Manager Assets] supports.

1. Navigieren Sie in der [!DNL Assets]-Benutzeroberfläche zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Führen Sie einen der folgenden Schritte aus, um die Assets hochzuladen:

   * On the toolbar, click **[!UICONTROL Create]**. Klicken Sie dann im Menü auf **[!UICONTROL Dateien]**. Sie können die Datei im angezeigten Dialogfeld bei Bedarf umbenennen.
   * Ziehen Sie die Assets in einem Browser, der HTML5 unterstützt, direkt auf die [!DNL Assets]-Benutzeroberfläche. Das Dialogfeld zum Umbenennen der Datei wird nicht angezeigt.

   ![Option zum Hochladen von Assets erstellen](assets/create-options.png)

   Wenn Sie die Assets im Dialogfeld für die Dateiauswahl bei gedrückter Strg-/Befehlstaste markieren, können Sie mehrere Dateien auswählen. Bei Verwendung eines iPads können Sie jeweils nur eine Datei auswählen.

   Sie können das Hochladen von großen Assets (größer als 500 MB) anhalten und später von der gleichen Seite aus fortsetzen. Klicken Sie auf **[!UICONTROL Anhalten]** neben der Fortschrittsleiste, die beim Hochladen von Beginn angezeigt wird.

   ![Fortschrittsleiste für hochgeladene Assets](assets/upload-progress-bar.png)

Die Größe, ab der ein Asset als großes Asset gilt, lässt sich konfigurieren. Sie können das System beispielsweise so konfigurieren, dass Assets über 1000 MB (anstatt 500 MB) als große Assets angesehen werden. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

Die Schaltfläche „Pause“ wird nicht angezeigt, wenn eine Datei, die größer ist als 1000 MB, mit einer Datei hochgeladen wird, die kleiner ist als 1000 MB. Wenn Sie jedoch den Upload der Datei abbrechen, die kleiner ist als 1000 MB, wird die Schaltfläche **[!UICONTROL Pause]** angezeigt.

To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

Wenn Sie auf &quot; **[!UICONTROL Anhalten]**&quot;klicken, wird die Option &quot; **[!UICONTROL Abspielen]** &quot;aktiviert. Um den Upload fortzusetzen, klicken Sie auf **[!UICONTROL Abspielen]**.

![Fortsetzen des angehaltenen Asset-Uploads](assets/resume-paused-upload.png)

Um einen laufenden Upload abzubrechen, klicken Sie auf „Schließen“ (`X`) neben der Fortschrittsleiste. Wenn Sie den Upload abbrechen, löscht [!DNL Assets] den teilweise hochgeladenen Teil des Assets.

Den Upload fortsetzen zu können, ist besonders hilfreich bei geringer Bandbreite und Netzwerkfehlern, bei denen der Upload großer Assets lange dauern kann. Sie können den Uploadvorgang anhalten und später fortsetzen, wenn die Bedingungen besser sind. Beim Fortsetzen beginnt der Upload an dem Punkt, an dem Sie pausiert haben.

During the upload operation, [!DNL Experience Manager] saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, [!DNL Experience Manager] consolidates these chunks into a single block of data in the repository.

To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.

>[!CAUTION]
>
>Der Standardwert beim Auslösen des Chunk-Uploads ist 500 MB und die Größe des Chunk-Formats 50 MB. Wenn Sie die Token-Konfiguration [für die](https://helpx.adobe.com/experience-manager/kb/How-to-set-token-session-expiration-AEM.html) Apache Jackrabbit-Oak ändern, um festzulegen, dass die Konfiguration `timeout configuration` kürzer ist als die für das Hochladen eines Assets benötigte Zeit, können Sie während des Hochladevorgangs auf eine Sitzungs-Timeout-Situation stoßen. Sie müssen daher die Einstellung `chunkUploadMinFileSize` &quot;und&quot;ändern, `chunksize`damit jede Wortgruppe die Sitzung aktualisiert.
>
>Angesichts der Werte für Ablauf- und Zeitüberschreitung, Latenz, Bandbreite und erwartete gleichzeitige Uploads wird der höchste Wert gewählt, mit dem Sie Folgendes sicherstellen können:
>
>* Um sicherzustellen, dass das Hochladen von Dateien in Textbausteinen für Dateien aktiviert ist, deren Größe den Ablauf der Berechtigung zur Folge haben kann, während der Hochladevorgang läuft.
   >
   >
* Um sicherzustellen, dass die einzelnen Abschnitte vor Ablauf der Berechtigung abgeschlossen werden.


Wenn Sie ein Asset unter einem Namen hochladen, der bereits für ein Asset verwendet wird, das sich am Zielort befindet, wird eine Warnmeldung angezeigt.

Sie können festlegen, ob ein vorhandenes Asset ersetzt, eine neue Version erstellt oder beide Assets beibehalten werden sollen, indem Sie das neue hochgeladene Asset umbenennen. Wenn Sie ein vorhandenes Asset ersetzen, werden die Metadaten für das Asset sowie alle zuvor vorgenommenen Änderungen (z. B. Anmerkungen oder Zuschneiden) gelöscht. If you choose to keep both assets, the new asset is renamed with number `1` appended to its name.

![Dialogfeld &quot;Konflikt benennen&quot;, um den Konflikt mit dem Asset-Namen zu lösen](assets/resolve-naming-conflict.png)

>[!NOTE]
>
>Wenn Sie im Dialogfeld [!UICONTROL Namenskonflikt] die Option **[!UICONTROL Ersetzen]** auswählen, wird die Asset-ID für das neue Asset neu generiert. Diese ID unterscheidet sich von der ID des vorherigen Assets.
>
>Wenn Asset Insights zur Verfolgung von Impressions/Klicks mit Adobe Analytics aktiviert ist, werden die für das Asset in Analytics erfassten Daten durch die erneut generierte Asset-ID ungültig.

If the asset you upload exists in [!DNL Assets], the **[!UICONTROL Duplicates Detected]** dialog warns that you are attempting to upload a duplicate asset. The dialog appears only if the `SHA 1` checksum value of the binary of the existing asset matches the checksum value of the asset you upload. In diesem Fall spielen die Namen der Assets keine Rolle.

>[!NOTE]
>
>The [!UICONTROL Duplicates Detected] dialog appears only when the duplicate detection feature is enabled. To enable the duplicate detection feature, see [Enable Duplicate Detection](/help/assets/duplicate-detection.md).

![Dialogfeld &quot;Duplikat-Asset erkannt&quot;](assets/duplicate-asset-detected.png)

Um das doppelte-Asset in [!DNL Assets] beizubehalten, klicken Sie auf **[!UICONTROL Behalten]**. To delete the duplicate asset you uploaded, click **[!UICONTROL Delete]**.

[!DNL Experience Manager Assets] verhindert, dass Sie Assets hochladen, deren Dateinamen unzulässige Zeichen enthalten. Wenn Sie versuchen, ein Asset mit einem Dateinamen mit einem oder mehreren nicht zulässigen Zeichen hochzuladen, zeigt [!DNL Assets] eine Warnmeldung an und stoppt den Upload, bis Sie diese Zeichen entfernen oder mit einem zulässigen Namen hochladen.

Um bestimmte Dateibenennungskonventionen für Ihre Organisation einzuhalten, können Sie im Dialogfeld [!UICONTROL Assets hochladen] lange Namen für die Dateien angeben, die Sie hochladen möchten.

Allerdings werden die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) nicht unterstützt:

* Der Asset-Dateiname darf nicht enthalten: `* / : [ \\ ] | # % { } ? &`
* Der Asset-Ordnername darf nicht enthalten: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

Fügen Sie keine Sonderzeichen in die Erweiterungen der Asset-Dateinamen ein.

![Das Dialogfeld &quot;Fortschritt beim Hochladen&quot;zeigt den Status der erfolgreich hochgeladenen Dateien und Dateien an, die nicht hochgeladen werden können](assets/bulk-upload-progress.png)

In addition, the [!DNL Assets] user interface displays the most recent asset that you upload or the folder that you created first.

Wenn Sie den Upload abbrechen, bevor die Dateien hochgeladen sind, unterbricht [!DNL Assets] den Upload der aktuellen Datei und aktualisiert den Inhalt. Dateien, die bereits hochgeladen wurden, werden jedoch nicht gelöscht.

Das Dialogfeld für den Upload-Fortschritt in [!DNL Assets] zeigt die Anzahl der erfolgreich hochgeladenen Dateien und die der Dateien an, die nicht hochgeladen werden konnten.

### Serielle Uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of your [!DNL Assets] deployment. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests [!DNL Assets] can handle for concurrent asset uploads. Fehler oder ein vorzeitiger Abbruch der Upload-Vorgänge können die Folge sein. In other words, [!DNL Experience Manager Assets] may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, [!DNL Assets] ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Der serielle Upload von Assets ist standardmäßig aktiviert. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in Crx-de and set the value of the `parallelUploads` property to `true`.

### Upload assets using FTP {#uploading-assets-using-ftp}

Dynamic Media ermöglicht das stapelweise Hochladen von Assets über FTP-Server. Wenn Sie große Assets (>1 GB) hochladen oder ganze Ordner und Unterordner hochladen möchten, sollten Sie FTP verwenden. Sie können das Hochladen per FTP auch einrichten, um Uploads regelmäßig und nach Plan durchzuführen.

>[!NOTE]
>
>Im Dynamic Media Scene 7-Modus können Sie nur Assets mit einer Dateigröße von maximal 2 GB hochladen.

>[!NOTE]
>
>Um Assets über FTP im Scene7-Modus hochzuladen, installieren Sie Feature Pack 18912 auf den Autoreninstanzen [!DNL Experience Manager] . Contact [Adobe Customer Care](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) to get access to FP-18912 and complete the setup of your FTP account. Weitere Informationen finden Sie unter Feature Pack 18912 [installieren für die Migration](/help/assets/bulk-ingest-migrate.md)von Massenelementen.
>
>If you use FTP for uploading assets, the upload settings specified in [!DNL Experience Manager] are ignored. Stattdessen werden Dateiverarbeitungsregeln, wie in Dynamic Media Classic definiert, verwendet.    

**So laden Sie Assets per FTP hoch**

1. Verwenden Sie den FTP-Client Ihrer Wahl und melden Sie sich beim FTP-Server mit dem FTP-Benutzernamen und -Kennwort aus der Bereitstellungs-E-Mail an. Laden Sie die Dateien und/oder Ordner über den FTP-Client auf den FTP-Server hoch.
1. [Melden Sie sich bei Dynamic Media Classic an](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html), indem Sie die Anmeldeinformationen verwenden, die Sie in der Bereitstellungs-E-Mail erhalten haben. Klicken Sie in der Leiste „Globale Navigation“ auf **[!UICONTROL Hochladen]**.

1. Klicken Sie auf der Seite „Hochladen“ in der Nähe der linken oberen Ecke auf die Registerkarte **[!UICONTROL Über FTP]**.
1. Wählen Sie im linken Bereich der Seite einen FTP-Ordner aus, aus dem Sie Dateien hochladen. Auf der rechten Seite der Seite wählen Sie einen Zielordner aus.
1. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Auftragsoptionen]** und legen Sie auf der Grundlage der Assets, die in dem von Ihnen gewählten Ordner enthalten sind, die gewünschten Optionen fest.

   Siehe [Upload-Auftragsoptionen](#upload-job-options).

   >[!NOTE]
   >
   >When you upload assets via FTP, the upload job options you set in Dynamic Media Classic (S7) take precedent over asset processing parameters set in [!DNL Experience Manager].

1. Klicken Sie in der rechten unteren Ecke des Dialogfelds „Upload-Auftragsoptionen“ auf **[!UICONTROL Speichern]**.
1. Klicken Sie in der rechten unteren Ecke der Seite „Hochladen“ auf **[!UICONTROL Upload starten]**.

   Um den Uploadfortschritt anzuzeigen, klicken Sie in der Leiste „Globale Navigation“ auf **[!UICONTROL Aufträge]**. Auf der Seite „Aufträge“ wird der Uploadfortschritt angezeigt. You can continue working in [!DNL Experience Manager] and return to the Jobs page in Dynamic Media Classic at any time to review an in-progress job.
To cancel an upload job in progress, click **[!UICONTROL Cancel]** next to the Duration time.

#### Upload-Auftragsoptionen {#upload-job-options}

| Upload-Optionen | Unteroption | Beschreibung |
|---|---|---|
| Auftragsname |  | Der Name, der standardmäßig in diesem Feld erstellt wird, enthält den vom Benutzer eingegebenen Teil des Namens und einen Zeitstempel samt Datum. Für diesen Upload-Auftrag können Sie den Standardnamen oder einen von Ihnen selbst erstellten Namen verwenden. <br>Der Auftrag und andere Upload- und Veröffentlichungsaufträge werden auf der Seite „Aufträge“ aufgezeichnet, wo Sie den Status der Aufträge prüfen können. |
| Nach dem Hochladen veröffentlichen |  | Veröffentlicht Assets automatisch nach dem Hochladen. |
| In belieb. Ordner Assets mit ident. Namen unabh. von Erweit. überschreiben |  | Wählen Sie diese Option aus, wenn hochgeladene Dateien vorhandene Dateien mit denselben Namen ersetzen sollen. Der Name dieser Option kann möglicherweise anders lauten, je nach den Einstellungen in **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]** > **[!UICONTROL Zur Anwendung hochladen]** > **[!UICONTROL Bilder überschreiben]**. |
| Zip- oder Tar-Dateien beim Hochladen dekomprimieren |  |  |
| Auftragsoptionen |  | Click **[!UICONTROL Job Options]** to open the [!UICONTROL Upload Job Options] dialog box and choose options that affect the entire upload job. Diese Optionen sind für alle Dateitypen gleich.<br>Sie können über die Seite „Allgemeine Programmeinstellungen“ Standardoptionen für das Hochladen von Dateien auswählen. Um diese Seite zu öffnen, wählen Sie **[!UICONTROL Einstellung]** > **[!UICONTROL Anwendungseinstellungen]**. Click the **[!UICONTROL Default Upload Options]** button to open the [!UICONTROL Upload Job Options] dialog box. |
|  | Wann | Wählen Sie „Einmalig“ oder „Wiederkehrend“ aus. Zum Einrichten eines wiederkehrenden Auftrags wählen Sie eine Wiederholungsoption („Täglich“, „Wöchentlich“, „Monatlich“ oder „Benutzerdefiniert“), um anzugeben, wie oft der FTP-Upload-Auftrag wiederholt werden soll. Dann geben Sie nach Bedarf die Planungsoptionen an. |
|  | Unterordner einschließen | Laden Sie alle Unterordner im hochzuladenden Ordner hoch. The names of the folder and its subfolders you upload are entered automatically in [!DNL Experience Manager Assets]. |
|  | Optionen für das Zuschneiden | Um die Seiten eines Bildes manuell zu beschneiden, wählen Sie im Menü „Beschneiden“ die Option „Manuell“ aus. Dann geben Sie die Anzahl von Pixeln ein, die an einer oder jeder Seite des Bildes abgeschnitten werden sollen. Um wie viel das Bild beschnitten wird, hängt von der ppi-Einstellung (Pixel per Inch; Pixel pro Zoll) in der Bilddatei ab. Beispiel: Wenn das Bild 150 ppi aufweist und Sie 75 in die Textfelder für oben, rechts, unten und links eingeben, wird ein halber Zoll von jeder Seite abgeschnitten.<br> Zum automatischen Beschneiden der Leerraumpixel eines Bildes öffnen Sie das Menü „Beschneiden“, wählen Sie „Manuell“ und geben Sie zum Beschneiden der Seiten die Pixelwerte in die Felder „Oben“, „Rechts“, „Unten“ und „Links“ ein. Sie können im Menü „Beschneiden“ auch „Zuschneiden“ und anschließend folgende Optionen auswählen:<br> **Beschneiden basierend auf** <ul><li>**Farbe** : Wählen Sie die Option &quot;Farbe&quot;. Wählen Sie anschließend im Menü „Ecke“ die Bildecke mit der Farbe aus, die am besten der Leerraumfarbe entspricht, die Sie entfernen möchten.</li><li>**** Transparenz – Wählen Sie die Option „Transparenz“.<br> **Toleranz** - Ziehen Sie den Schieberegler, um eine Toleranz von 0 bis 1 festzulegen. Beim Beschneiden basierend auf Farbe geben Sie 0 an, damit Pixel nur abgeschnitten werden, wenn sie exakt der Farbe entsprechen, die Sie in der Bildecke ausgewählt haben. Werte, die näher an 1 liegen, lassen eine größere Farbdifferenz zu.<br>Für das Zuschneiden auf der Grundlage der Transparenz geben Sie den Wert 0 an, damit Pixel nur dann abgeschnitten werden, wenn sie transparent sind. Werte, die näher an 1 liegen, lassen eine größere Transparenz zu.</li></ul><br>Beachten Sie, dass diese Optionen für das Beschneiden zerstörungsfrei sind. |
|  | Farbprofiloptionen | Wählen Sie beim Erstellen optimierter Dateien eine Farbkonversion aus, die für die Bereitstellung verwendet wird:<ul><li>Beibehaltung der Standardfarbe: Behält die Farben des Quellbildes bei, wenn die Bilder Farbrauminformationen enthalten. Es findet keine Farbkonversion statt. Heutzutage ist in fast allen Bildern das entsprechende Farbprofil eingebettet. Wenn jedoch ein CMYK-Quellbild kein eingebettetes Farbprofil enthält, werden die Farben in den Farbraum sRGB (standardmäßiges Rot Grün Blau) konvertiert. sRGB ist der empfohlene Farbraum zum Anzeigen von Bildern auf Webseiten.</li><li>Ursprünglichen Farbraum beibehalten: Behält die ursprünglichen Farben bei, ohne dass an der betreffenden Stelle eine Farbkonversion stattfindet. Bei Bildern ohne eingebettetes Farbprofil wird jede Farbkonversion mit den in den Veröffentlichungseinstellungen konfigurierten Standardfarbprofilen durchgeführt. Die Farbprofile stimmen möglicherweise nicht mit der Farbe in den Dateien überein, die mit dieser Option erstellt wurden. Deshalb empfiehlt es sich, die Option „Beibehaltung der Standardfarbe“ zu verwenden.</li><li>Benutzerdefinierte Einstellung von > in:<br> Öffnet Menüs, damit Sie einen „Konvertieren von“- und einen „Konvertieren in“-Farbraum auswählen können. Diese erweiterte Option überschreibt alle Farbinformationen, die in die Quelldatei eingebettet sind. Wählen Sie diese Option aus, wenn alle Bilder, die Sie senden, falsche oder fehlende Farbprofildaten enthalten.</li></ul> |
|  | Bildbearbeitungsoptionen | Sie können die Beschneidungsmasken in Bildern beibehalten und ein Farbprofil auswählen.<br> Siehe [Festlegen von Bildbearbeitungsoptionen beim Hochladen](#setting-image-editing-options-at-upload). |
|  | PostScript-Optionen | Sie können PostScript®-Dateien rastern, Dateien beschneiden, transparente Hintergründe beibehalten sowie eine Auflösung und einen Farbraum auswählen.<br> Siehe [Festlegen von PostScript- und Illustrator-Uploadoptionen](#setting-postscript-and-illustrator-upload-options). |
|  | Photoshop-Optionen | Sie können Vorlagen aus Adobe® Photoshop®-Dateien erstellen, Ebenen beibehalten, Ebenennamen angeben, Text extrahieren und angeben, wie Bilder in Vorlagen verankert sind.<br> Beachten Sie, dass Vorlagen in [!DNL Experience Manager]nicht unterstützt werden.<br> Siehe [Festlegen von Photoshop-Uploadoptionen](#setting-photoshop-upload-options). |
|  | PDF-Optionen | Sie können die Dateien rastern, Suchbegriffe und -links extrahieren, automatisch einen E-Katalog erstellen, die Auflösung einstellen und einen Farbraum auswählen.<br> Beachten Sie, dass E-Kataloge in [!DNL Experience Manager]nicht unterstützt werden. <br> Siehe [Festlegen von PDF-Uploadoptionen](#setting-pdf-upload-options). |
|  | Illustrator-Optionen | Sie können Adobe Illustrator®-Dateien rastern, transparente Hintergründe beibehalten sowie eine Auflösung und einen Farbraum auswählen.<br> Siehe [Festlegen von PostScript- und Illustrator-Uploadoptionen](#setting-postscript-and-illustrator-upload-options). |
|  | eVideo-Optionen | Sie können eine Videodatei durch Auswahl einer Videovorgabe transkodieren.<br> Siehe [Festlegen von eVideo-Uploadoptionen](#setting-evideo-upload-options). |
|  | Stapelsatzvorgaben | Um ein Bild- oder Rotationsset aus den hochgeladenen Dateien zu erstellen, klicken Sie auf die Spalte „Aktiv“ der Vorgabe, die Sie verwenden möchten. Sie können mehrere Vorgaben auswählen. Die Vorgaben erstellen Sie auf der Seite „Anwendungseinstellungen/Stapelsatzvorgaben“ von Dynamic Media Classic.<br> Weitere Informationen zur Erstellung von Stapelsatzvorgaben finden Sie unter [Konfigurieren von Stapelsatzvorgaben zum automatischen Erstellen von Bild- und Rotationssets](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).<br> Siehe [Festlegen von Stapelsatzvorgaben beim Hochladen](#setting-batch-set-presets-at-upload). |

#### Set image editing options at upload {#setting-image-editing-options-at-upload}

When uploading image files, including AI, EPS, and PSD files, you can take the following editing actions in the [!UICONTROL Upload Job Options] dialog box:

* Beschneiden von Leerzeichen am Rand von Bildern (siehe Beschreibung in Tabelle oben).
* Ränder von Bildern manuell beschneiden (siehe Beschreibung in der oben stehenden Tabelle)
* Ein Farbprofil auswählen (siehe Optionsbeschreibung in der oben stehenden Tabelle)
* Eine Maske aus einem Beschneidungspfad erstellen
* Bilder scharfzeichnen mit Optionen für „Unscharf maskieren“
* Hintergrund aussparen

<!--
| Option | Sub-option | Description |
|---|---|---|
| Create Mask From Clipping Path | | Create a mask for the image based on its clipping path information. This option applies to images created with image-editing applications in which a clipping path was created. |
| Unsharp Masking | | Lets you fine-tune a sharpening filter effect on the final downsampled image, controlling the intensity of the effect, the radius of the effect (as measured in pixels), and a threshold of contrast that is ignored.<br> This effect uses the same options as Photoshop’s Unsharp Mask filter. Contrary to what the name suggests, Unsharp Mask is a sharpening filter. Under Unsharp Masking, set the options you want. Setting options are described in the following: |
| | Amount | Controls the amount of contrast that is applied to edge pixels.<br> Think of it as the intensity of the effect. The main difference between the amount values of Unsharp Mask in Dynamic Media and the amount values in Adobe Photoshop, is that Photoshop has an amount range of 1% to 500%. Whereas, in Dynamic Media, the value range is 0.0 to 5.0. A value of 5.0 is the rough equivalent of 500% in Photoshop; a value of 0.9 is the equivalent of 90%, and so on. |
| | Radius | Controls the radius of the effect. The value range is 0-250.<br> The effect is run on all pixels in an image and radiates out from all pixels in all directions. The radius is measured in pixels. For example, to get a similar sharpening effect for a 2000 x 2000 pixel image and 500 x 500 pixel image, you would set a radius of two pixels on the 2000 x 2000 pixel image and a radius value of one pixel on the 500 x 500 pixel image. A larger value is used for an image that has more pixels. |
| | Threshold | Threshold is a range of contrast that is ignored when the Unsharp Mask filter is applied. It is important so that no "noise" is introduced to an image when this filter is used. The value range is 0-255, which is the number of brightness steps in a grayscale image. 0=black, 128=50% gray and 255=white.<br> For example, a threshold value of 12 ignores slight variations is skin tone brightness to avoid adding noise, but still add edge contrast to areas such as where eyelashes meet skin.<br> For example, if you have a photo of someone’s face, the Unsharp Mask affects the parts of the image, such as where eyelashes and skin meet to create an obvious area of contrast, and the smooth skin itself. Even the smoothest skin exhibits subtle changes in brightness values. If you do not use a threshold value, the filter accentuates these subtle changes in skin pixels. In turn, a noisy and undesirable effect is created while contrast on the eyelashes is increased, enhancing sharpness.<br> To avoid this issue, a threshold value is introduced that tells the filter to ignore pixels that do not change contrast dramatically, like smooth skin.<br> In the zipper graphic shown earlier, notice the texture next to the zippers. Image noise is exhibited because the threshold values were too low to suppress the noise. |
| | Monochrome | Select to unsharp-mask image brightness (intensity).<br> Deselect to unsharp-mask each color component separately. |
| Knockout Background | | Automatically removes the background of an image when you upload it. This technique is useful to draw attention to a particular object and make it stand out from a busy background. Select to enable or “turn on” the Knockout Background feature and the following sub-options: |
| | Corner | Required.<br> The corner of the image that is used to define the background color to knockout.<br> You can choose from **Upper Left**, **Bottom Left**, **Upper Right**, or **Bottom Right**. |
| | Fill Method | Required.<br> Controls pixel transparency from the Corner location that you set.<br> You can choose from the following fill methods: <ul><li>**Flood Fill** - turns all pixels transparent that match the Corner that you have specified and are connected to it.</li><li>**Match Pixel** - turns all matching pixels transparent, regardless of their location on the image.</li></ul> |
| | Tolerance | Optional.<br> Controls the allowable amount of variation in pixel color matching based on the Corner location that you set.<br> Use a value of 0.0 to match pixel colors exactly or, use a value of 1.0 to allow for the greatest variation. |
-->

#### Set PostScript and Illustrator upload options {#setting-postscript-and-illustrator-upload-options}

Wenn Sie PostScript (EPS)- oder Illustrator (AI)-Bilddateien hochladen, können Sie diese auf verschiedene Arten formatieren. Sie können die Dateien rastern, den transparenten Hintergrund beibehalten sowie eine Auflösung und einen Farbraum auswählen. Options for formatting PostScript and Illustrator files are available in the [!UICONTROL Upload Job Options] dialog box under [!UICONTROL PostScript Options] and [!UICONTROL Illustrator Options].

| Option | Unteroption | Beschreibung |
|---|---|---|
| Verarbeitung |  | Wählen Sie **[!UICONTROL Rastern]**, um Vektorgrafiken in der Datei in das Bitmap-Format zu konvertieren. |
| Transparenten Hintergrund in gerendertem Bild beibehalten |  | Zur Beibehaltung der Hintergrundtransparenz der Datei. |
| Auflösung |  | Zur Einstellung der Auflösung. Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der Datei angezeigt werden. |
| Farbraum |  | Klicken Sie auf das Menü „Farbraum“ und wählen Sie unter den folgenden Farbraumoptionen: |
|  | Automatisch erkennen | Der Farbraum der Datei wird beibehalten. |
|  | Immer RGB | Zur Konvertierung in den RGB-Farbraum. |
|  | Immer CMYK | Zur Konvertierung in den CMYK-Farbraum. |
|  | Immer Graustufen | Zur Konvertierung in den Graustufenfarbraum. |

#### Festlegen von Photoshop-Upload-Optionen {#setting-photoshop-upload-options}

Photoshop Dokument-(PSD-)Dateien werden meist zum Erstellen von Bildvorlagen verwendet. When you upload a PSD file, you can create an image template automatically from the file (select the [!UICONTROL Create Template] option on the Upload screen).

Dynamic Media erstellt mehrere Bilder aus einer PSD-Datei mit Ebenen, wenn Sie die Datei zum Erstellen einer Vorlage verwenden. Für jede Ebene wird ein Bild erstellt.

Use the [!UICONTROL Crop Options] and [!UICONTROL Color Profile Options], described above, with Photoshop upload options.

>[!NOTE]
>
>Templates are not supported in [!DNL Experience Manager].

| Option | Unteroption | Beschreibung |
|---|---|---|
| Ebenen beibehalten |  | Teilt die Ebenen in der PSD-Datei ggf. in einzelne Assets auf. Die Asset-Ebenen bleiben der PSD-Datei zugeordnet. Sie können sie anzeigen, indem Sie die PSD-Datei in der Detailansicht öffnen und das Ebenenfenster auswählen. |
| Vorlage erstellen |  | Erstellt eine Vorlage aus den Ebenen der PSD-Datei. |
| Text extrahieren |  | Extrahiert den Text, damit Benutzer im Viewer den Text durchsuchen können. |
| Ebenen auf Hintergrundgröße ausdehnen |  | Erweitert die Größe aufgeteilter Bildebenen auf die Größe der Hintergrundebene. |
| Ebenenbenennung |  | Ebenen in der PSD-Datei werden als separate Bilder hochgeladen. |
|  | Ebenenname | Benennt die Bilder nach ihren Ebenennamen in der PSD-Datei. Wenn eine Ebene in der Original-PSD-Datei beispielsweise „Preisschild“ heißt, wird auch das zugehörige Bild „Preisschild“ genannt. Wenn es sich bei den Ebenennamen in der PSD-Datei jedoch um standardmäßige Photoshop-Ebenennamen handelt (Hintergrund, Ebene 1, Ebene 2 usw.), werden die Bilder nicht nach den Standardebenennamen, sondern nach den zugehörigen Ebenennummern in der PSD-Datei benannt. |
|  | Photoshop- und Ebenennummer | Benennt die Bilder nach ihren Ebenennummern in der PSD-Datei und ignoriert die ursprünglichen Ebenennamen. Bilder werden mit dem Photoshop-Dateinamen und einer angefügten Ebenennummer benannt. Zum Beispiel erhält die zweite Ebene der Datei Frühjahrsannonce.psd den Namen Frühjahrsannonce_2, auch wenn sie in Photoshop einen nicht standardmäßigen Namen hatte. |
|  | Photoshop- und Ebenenname | Benennt die Bilder nach der PSD-Datei, gefolgt vom Ebenennamen oder der -nummer. Die Ebenennummer wird verwendet, wenn es sich bei den Ebenennamen in der PSD-Datei um standardmäßige Photoshop-Ebenennamen handelt. Zum Beispiel erhält eine Ebene mit dem Namen „Preisschild“ in einer PSD-Datei mit dem Namen „Frühjahrsannonce“ den Namen „Frühjahrsannonce_Preisschild“. Eine Ebene mit dem standardmäßigen Namen „Ebene 2“ erhält den Namen „Frühjahrsannonce_2“. |
| Anker |  | Geben Sie an, wie Bilder in Vorlagen, die aus der Zusammenstellung der Ebenen aus der PSD-Datei erstellt werden, verankert werden. Der Anker ist standardmäßig zentriert. Ein zentrierter Anker eignet sich am besten zum Auffüllen desselben Raums mit Ersatzbildern, unabhängig vom Seitenverhältnis der Ersatzbilder. Bilder mit einem anderen Seitenverhältnis, die dieses Bild ersetzen, nehmen effektiv denselben Raum ein, wenn auf die Vorlage verwiesen und die Parameterersetzung durchgeführt wird. Wählen Sie eine andere Einstellung, wenn es für Ihre Anwendung erforderlich ist, dass die Ersatzbilder den zugeordneten Raum in der Vorlage ausfüllen. |

#### Optionen zum Hochladen von PDF festlegen {#setting-pdf-upload-options}

Wenn Sie eine PDF-Datei hochladen, können Sie diese auf verschiedene Arten formatieren. Sie können ihre Seiten zuschneiden, Suchbegriffe extrahieren, eine ppi (Pixel pro Zoll)-Auflösung eingeben und einen Farbraum auswählen. PDF-Dateien enthalten oft einen Beschnittrand, Schnittmarken, Registrierungsmarken und andere Druckermarken. Sie können diese Marken von den Seitenrändern aus zuschneiden, wenn Sie eine PDF-Datei hochladen.

>[!NOTE]
>
>eCatalogs are not supported in [!DNL Experience Manager].

Wählen Sie unter folgenden Optionen:

| Option | Unteroption | Beschreibung |
|---|---|---|
| Verarbeitung | Rastern | (Standard) Zum Extrahieren der Seiten aus der PDF-Datei und zum Konvertieren von Vektorgrafiken in Bitmap-Bilder. Wählen Sie diese Option, um einen E-Katalog zu erstellen. |
| Extrahieren | Suchbegriffe | Zum Extrahieren von Wörtern aus der PDF-Datei, damit die Datei in einem E-Katalog-Viewer mit einem Schlüsselwort durchsucht werden kann. |
|  | Links | Zum Extrahieren von Links aus den PDF-Dateien und zum Konvertieren der PDF-Dateien in Imagemaps, die in einem E-Katalog-Viewer verwendet werden. |
| E-Katalog aus mehrseitiger PDF automatisch erstellen |  | Zum automatischen Erstellen eines E-Katalogs aus der PDF-Datei. Der E-Katalog wird nach der von Ihnen hochgeladenen PDF-Datei benannt. (Diese Option ist nur dann verfügbar, wenn Sie die PDF-Datei beim Hochladen rastern.) |
| Auflösung |  | Zum Festlegen der Auflösung: Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der PDF-Datei angezeigt werden. Standard: 150. |
| Farbraum |  | Wählen Sie das Farbraummenü und einen Farbraum für die PDF-Datei aus. Die meisten PDF-Dateien enthalten sowohl RGB- als auch CMYK-Farbbilder. Der RGB-Farbraum eignet sich besonders gut, um Dateien online anzuzeigen. |
|  | Automatisch erkennen | Der Farbraum der PDF-Datei wird beibehalten. |
|  | Immer RGB | Zur Konvertierung in den RGB-Farbraum. |
|  | Immer CMYK | Zur Konvertierung in den CMYK-Farbraum. |
|  | Immer Graustufen | Zur Konvertierung in den Graustufenfarbraum. |

#### Festlegen von eVideo-Upload-Optionen {#setting-evideo-upload-options}

So transkodieren Sie eine Videodatei, indem Sie aus einer Vielzahl von Video-Vorgaben wählen.

| Option | Unteroption | Beschreibung |
|---|---|---|
| Adaptives Video |  | Eine einzelne Kodierungsvorgabe, die mit jedem Seitenverhältnis verwendet werden kann, um Videos für Versand zu Mobilgeräten, Tablets und Desktops zu erstellen. Hochgeladene Quellvideos, die mit dieser Vorgabe kodiert wurden, weisen eine feste Höhe auf. Die Breite wird jedoch automatisch skaliert, um das Seitenverhältnis des Videos beizubehalten. <br>Die beste Vorgehensweise ist die Verwendung der adaptiven Videokodierung. |
| Einzelne Kodierungsvorgaben | Kodierungsvorgaben sortieren | Wählen Sie &quot;Name&quot;oder &quot;Größe&quot;, um die unter &quot;Desktop&quot;, &quot;Mobil&quot;und &quot;Tablet&quot;aufgelisteten Kodierungsvorgaben nach Name oder Auflösung zu sortieren. |
|  | Desktop | Erstellen Sie eine MP4-Datei zur Bereitstellung eines Streaming- oder progressiven Videoerlebnisses auf Desktop-Computern.Wählen Sie ein oder mehrere Seitenverhältnisse mit der gewünschten Auflösung und Datenrate für die Zielgruppe aus. |
|  | Mobilgerät | Erstellen Sie eine MP4-Datei für den Versand auf iPhone- oder Android-Mobilgeräten.Wählen Sie ein oder mehrere Seitenverhältnisse mit der gewünschten Auflösung und Zielgruppe für die Datenrate aus. |
|  | Tablet | Erstellen Sie eine MP4-Datei für den Versand auf iPad- oder Android-Tablet-Geräten.Wählen Sie ein oder mehrere Seitenverhältnisse mit der gewünschten Auflösung und Datenrate für die Zielgruppe aus. |

#### Set Batch Set Presets at upload {#setting-batch-set-presets-at-upload}

Wenn Sie aus hochgeladenen Bildern automatisch einen Bildsatz oder ein Rotationsset erstellen möchten, klicken Sie auf die Spalte &quot;Aktiv&quot;für die gewünschte Vorgabe. Sie können mehrere Vorgaben auswählen. 

Weitere Informationen zur Erstellung von Stapelsatzvorgaben finden Sie unter [Konfigurieren von Stapelsatzvorgaben zum automatischen Erstellen von Bild- und Rotationssets](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets).

### Gestreamte Uploads {#streamed-uploads}

Wenn Sie viele Assets nach Adobe Experience Manager hochladen, erhöhen sich die E/A-Serveranforderungen drastisch, was die Upload-Effizienz verringert und sogar dazu führen kann, dass einige Aufgaben beim Hochladen zeitlimit überschreiten. [!DNL Experience Manager Assets] unterstützt Streaming-Uploads von Assets. Gestreamte Uploads sorgen für eine Datenträger-E/A-Reduzierung beim Hochladen, da die Speicherung von Assets in einem temporären Ordner auf dem Server vermieden wird, bevor Assets in das Repository kopiert werden. Stattdessen werden die Daten direkt an das Repository übertragen. Auf diese Weise wird die Zeit für das Hochladen von Assets und die Möglichkeit von Zeitüberschreitungen verringert. Streamed upload is enabled by default in [!DNL Assets].

>[!NOTE]
>
>Das Hochladen von Streaming ist für Adobe Experience Manager, das auf einem JEE-Server mit einer Servlet-API-Version unter 3.1 ausgeführt wird, deaktiviert.

### ZIP-Archiv mit Assets extrahieren {#extractzip}

Sie können ZIP-Archive wie jedes andere unterstützte Asset hochladen. Für ZIP-Dateien gelten dieselben Regeln für Dateinamen. [!DNL Experience Manager]Mit können Sie ein ZIP-Archiv in einen DAM-Speicherort extrahieren. Wenn die Aktivdateien nicht die Erweiterung ZIP haben, aktivieren Sie die Dateityperkennung über den Inhalt.

Wählen Sie jeweils ein ZIP-Archiv aus, klicken Sie auf **[!UICONTROL Archiv extrahieren]** und wählen Sie einen Zielordner aus. Wählen Sie eine Option für den Umgang mit eventuellen Konflikten. Wenn die Assets in der ZIP-Datei bereits im Zielordner vorhanden sind, können Sie eine der folgenden Optionen auswählen: Extrahieren überspringen, vorhandene Dateien ersetzen, beide Assets durch Umbenennen behalten oder neue Version erstellen.

After the extraction is complete, [!DNL Experience Manager] notifies you in the notification area. While [!DNL Experience Manager] extracts the ZIP, you can go back to your work without interrupting the extraction.

![Benachrichtigung über die Extraktion der ZIP-Datei](assets/Zip-extraction-notification.png)

Die Funktion hat einige Einschränkungen:

* Wenn sich ein gleichnamiger Ordner am Ziel befindet, werden die Assets aus der ZIP-Datei in diesen extrahiert.
* Wenn Sie die Extrahierung abbrechen, werden die bereits extrahierten Assets nicht gelöscht.
* Sie können nicht gleichzeitig zwei ZIP-Dateien auswählen und extrahieren. Sie können jeweils nur ein ZIP-Archiv extrahieren.
* Wenn beim Hochladen eines ZIP-Archivs im Dialogfeld „Hochladen“ ein „500 Server Error“ angezeigt wird, versuchen Sie es nach der Installation des neuesten Service Packs erneut.

## Anzeigen einer Vorschau für Assets {#previewing-assets}

Gehen Sie wie folgt vor, um eine Vorschau für ein Asset anzuzeigen.

1. From the [!DNL Assets] user interface, navigate to the location of the asset you want to preview.
1. Klicken Sie auf das gewünschte Asset, um es zu öffnen.

1. Im Vorschaumodus ist eine Zoom-Funktion für [unterstützte Bildtypen](/help/assets/assets-formats.md#supported-raster-image-formats) verfügbar (mit interaktiver Bearbeitung).

   To zoom into an asset, click `+` (or click the magnifying glass on the asset). To zoom out, click `-`. Beim Heranzoomen können Sie beliebige Bildbereiche durch Schwenken genauer untersuchen. Mit dem Pfeil „Zoom zurücksetzen“ gelangen Sie zurück zur Originalansicht. Um die Ansicht auf die Originalgröße zurückzusetzen, klicken Sie auf &quot; **[!UICONTROL Zurücksetzen]** der ![Ansicht](assets/do-not-localize/revert.png)&quot;.

**Vorschau von Assets nur mit Tastatur**

Gehen Sie wie folgt vor, um ein Asset mit der Tastatur Vorschau:

1. Navigieren Sie in der [!DNL Assets] Benutzeroberfläche mit den Pfeiltasten zum gewünschten Asset `Tab` .

1. Drücken Sie die `Enter` Taste, um das gewünschte Asset zu öffnen. Sie können Assets im Vorschau-Modus heranzoomen.

1. So vergrößern Sie das Asset:
   1. Verwenden Sie die `Tab` Taste, um den Fokus auf die Option &quot;Einzoomen&quot;zu verschieben.
   1. Verwenden Sie die `Enter` Taste, um das Bild zu vergrößern.

   Zum Auszoomen verwenden Sie die `Tab` Taste, um den Fokus auf die Zoomoption zu verschieben, und drücken Sie die Eingabetaste `Enter`.

1. Verwenden Sie `Shift` + `Tab` , um den Fokus wieder auf das Bild zu verschieben.

1. Verwenden Sie die Pfeiltasten, um sich um das gezoomte Bild zu bewegen.

>[!MORELIKETHIS]
>
>* [Vorschau dynamischer Medienelemente](/help/assets/previewing-assets.md).
>* [Anzeigen von Unter-Assets](managing-linked-subassets.md#viewing-subassets).


## Eigenschaften und Metadaten bearbeiten {#editing-properties}

1. Navigieren Sie zum Speicherort des Assets, um dessen Metadaten zu bearbeiten.

1. Select the asset, and click **[!UICONTROL Properties]** from the toolbar to view asset properties. Wählen Sie alternativ die Schnellaktion **[!UICONTROL Eigenschaften]** auf der Asset-Karte aus.

   ![Schnellaktion &quot;Eigenschaften&quot;bei der Ansicht von Asset-Karten](assets/properties_quickaction.png)

1. Bearbeiten Sie auf der Registerkarte [!UICONTROL Eigenschaften] die Metadateneigenschaften auf den verschiedenen Registerkarten. Zum Beispiel bearbeiten Sie auf der Registerkarte **[!UICONTROL Allgemein]** den Titel, die Beschreibung usw.

   >[!NOTE]
   >
   >Das Layout der Seite [!UICONTROL Eigenschaften] und die verfügbaren Metadaten sind vom zugrunde liegenden Metadatenschema abhängig. Informationen dazu, wie Sie das Layout der Seite [!UICONTROL Eigenschaften] ändern können, finden Sie unter [Metadatenschemata](/help/assets/metadata-schemas.md).

1. Um ein bestimmtes Datum/eine Zeit für die Aktivierung der Assets einzustellen, verwenden Sie die Datumsauswahl neben dem Feld **[!UICONTROL Einschaltzeit]**.

   ![Datums- und Zeitauswahl oder Verwendung von Tastaturbefehlen im Feld &quot;Uhrzeit&quot;, um Datum und Uhrzeit für die Aktivierung des Assets hinzuzufügen](assets/datepicker.png)

   *Abbildung: Verwenden Sie die Datumsauswahl, um die Aktivierung des Assets zu planen.*

1. Um das Asset nach einer bestimmten Laufzeit zu deaktivieren, wählen Sie das Datum/den Zeitpunkt mit der Datumsauswahl neben dem Feld **[!UICONTROL Ausschaltzeit]**. Das Deaktivierungsdatum sollte nach dem Aktivierungsdatum für ein Asset liegen. After the [!UICONTROL Off Time], an asset and its renditions are not available either via the [!DNL Assets] web interface or through the HTTP API.

1. Wählen Sie im Feld **[!UICONTROL Tags]** ein oder mehrere Tags aus. Um ein benutzerdefiniertes Tag hinzuzufügen, geben Sie den Namen des Tags in das Feld ein. Anschließend drücken Sie die Eingabetaste. The new tag is saved in [!DNL Experience Manager]. [!DNL YouTube] erfordert Tags zum Veröffentlichen. See [publish videos to YouTube](video.md#publishing-videos-to-youtube).

   >[!NOTE]
   >
   >To create tags, you need write permission at `/content/cq:tags/default` in the CRX repository.

1. Um eine Bewertung für das Asset anzugeben, klicken Sie auf die Registerkarte **[!UICONTROL Erweitert]** und dann auf den Stern an der richtigen Position, um die gewünschte Bewertung zuzuweisen.

   ![Registerkarte &quot;Erweitert&quot;in den Asset-Eigenschaften zum Zuweisen von Bewertungen](assets/ratings.png)

   Die Bewertungsnote, die Sie dem Asset zuweisen, wird unter **[!UICONTROL Ihre Bewertungen]** angezeigt. Die durchschnittliche Bewertungsnote, die das Asset von Benutzern erhält, wird unter **[!UICONTROL Bewertung]** angezeigt. Darüber hinaus wird die Aufschlüsselung der Bewertungen, die zur durchschnittlichen Bewertungsnote beitragen, unter **[!UICONTROL Bewertungsübersicht]** angezeigt. Sie können Assets basierend auf der durchschnittlichen Bewertungsnote durchsuchen.

1. To view usage usage statistics for the asset, click the **[!UICONTROL Insights]** tab.

   Nutzungsstatistiken umfassen folgende Metriken:

   * Anzahl der Aufrufe oder Downloads des Assets
   * Kanäle/Geräte, über die das Asset genutzt wurde
   * Kreativlösungen, in denen das Asset kürzlich verwendet wurde

   Weitere Informationen finden Sie unter [Asset Insights](/help/assets/touch-ui-asset-insights.md).

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Navigate to the [!DNL Assets] user interface. Die bearbeiteten Metadateneigenschaften, darunter Titel, Beschreibung, Bewertungen usw., werden auf der Asset-Karte in der Kartenansicht sowie in den relevanten Spalten der Listenansicht angezeigt.

## Kopieren von Assets {#copying-assets}

Beim Kopieren eines Assets oder eines Ordners wird das gesamte Asset bzw. der Ordner mitsamt seiner Inhaltsstruktur kopiert. Ein kopiertes Asset oder ein kopierter Ordner wird am Zielspeicherort dupliziert. Das Asset am Quellspeicherort bleibt unverändert.

Einige wenige, für eine bestimmte Kopie eines Assets eindeutige Attribute werden nicht übertragen. Beispiele:

* Asset-ID, Erstellungsdatum und -zeitpunkt sowie Versionen und Versionsverlauf. Einige dieser Eigenschaften sind an den Eigenschaften `jcr:uuid`, `jcr:created` und `cq:name` zu erkennen.

* Der Erstellungszeitpunkt und referenzierte Pfade sind für jedes Asset und jede seiner Wiedergaben eindeutig.

Die übrigen Eigenschaften und Metadateninformationen werden beibehalten. Eine Teilkopie wird beim Kopieren eines Assets nicht erstellt.

1. Wählen Sie in der [!DNL Assets] Benutzeroberfläche ein oder mehrere Assets aus und klicken Sie in der Symbolleiste auf &quot; **[!UICONTROL Kopieren]** &quot;. Alternativ können Sie die Option &quot; **[!UICONTROL Kopieren]** &quot;in der Symbolleiste der Assets-Oberfläche ![](assets/do-not-localize/copy_icon.png) für Schnellaktionen auf der Asset-Karte aktivieren.

   >[!NOTE]
   >
   >Wenn Sie die Schnellaktion [!UICONTROL Kopieren] verwenden, können Sie immer nur ein Asset gleichzeitig kopieren.

1. Navigieren Sie zum Speicherort, in den Sie die Assets kopieren möchten.

   >[!NOTE]
   >
   >If you copy an asset at the same location, [!DNL Experience Manager] automatically generates a variation of the name. For example, if you copy an asset titled `Square`, [!DNL Experience Manager] automatically generates the title for its copy as `Square1`.

1. Klicken Sie in der Symbolleiste auf die Option Asset **[!UICONTROL Einfügen]** ![in der Asset-Symbolleiste](assets/do-not-localize/paste.png) . Assets werden dann an diesen Speicherort kopiert.

   >[!NOTE]
   >
   >The **[!UICONTROL Paste]** option is available in the toolbar until the paste operation is completed.

## Move and rename assets {#moving-or-renaming-assets}

Wenn Sie Assets (oder Ordner) an einen anderen Speicherort verschieben, werden die Assets (oder Ordner) nicht dupliziert, anders als beim Kopieren des Assets. Die Assets (oder die Ordner) werden am Speicherort der Zielgruppe platziert und vom Quellspeicherort entfernt. Sie können das Asset auch umbenennen, wenn Sie es an die neue Position verschieben.
Wenn Sie ein veröffentlichtes Asset an einen anderen Speicherort verschieben, haben Sie die Möglichkeit, das Asset erneut zu veröffentlichen. Standardmäßig wird beim Verschieben eines veröffentlichten Assets die Veröffentlichung automatisch rückgängig gemacht. Verschiebte Assets werden erneut veröffentlicht, wenn der Autor beim Verschieben des Assets die Option &quot; [!UICONTROL Neu veröffentlichen] &quot;auswählt.

![Sie können bereits veröffentlichte Assets beim Verschieben erneut veröffentlichen](assets/republish-on-move.png)

So verschieben Sie Assets oder Ordner:

1. Navigieren Sie zum Speicherort des Assets, das Sie verschieben möchten.

1. Select the asset, and click **[!UICONTROL Move]** option from the toolbar.
   ![Option &quot;Verschieben&quot;in der Assets-Symbolleiste](assets/do-not-localize/move.png)

1. In the [!UICONTROL Move Assets] wizard, do one of the following:

   * Geben Sie nach dem Verschieben den Namen für das Asset an. Then click **[!UICONTROL Next]** to proceed.

   * Click **[!UICONTROL Cancel]** to stop the process.
   >[!NOTE]
   >
   >* Sie können denselben Namen für das Asset angeben, wenn sich am neuen Speicherort kein Asset mit diesem Namen befindet. Sie sollten jedoch einen anderen Namen verwenden, wenn Sie das Asset an einen Speichertort verschieben, an dem bereits ein Asset mit demselben Namen vorhanden ist. Wenn Sie denselben Namen verwenden, generiert das System automatisch eine Variante dieses Namens. Wenn Sie beispielsweise ein Asset mit dem Namen „Quadrat“ kopieren, generiert das System den Namen „Quadrat1“ für die Kopie.
   >* Beim Umbenennen sind keine Leerzeichen in Dateinamen zulässig.


1. Führen Sie im Dialogfeld **[!UICONTROL Ziel auswählen]** eine der folgenden Aktionen aus:

   * Navigate to the new location for the assets, and then click **[!UICONTROL Next]** to proceed.

   * Click **[!UICONTROL Back]** to return to the **[!UICONTROL Rename]** screen.

1. Wenn die verschobenen Assets verweisende Seiten, Assets oder Sammlungen umfassen, wird die Registerkarte **[!UICONTROL Verweise anpassen]** neben der Registerkarte **[!UICONTROL Ziel auswählen]** angezeigt.

   Führen Sie im Bildschirm **[!UICONTROL Verweise anpassen]** einen der folgenden Schritte aus:

   * Specify the references to be adjusted based on the new details, and then click **[!UICONTROL Move]** to proceed.

   * Aktivieren/deaktivieren Sie in der Spalte **[!UICONTROL Anpassen]** Verweise auf die Assets.
   * Click **[!UICONTROL Back]** to return to the **[!UICONTROL Select Destination]** screen.

   * Click **[!UICONTROL Cancel]** to stop the move operation.

   Wenn Sie die Verweise nicht aktualisieren, verweisen sie weiterhin auf den alten Asset-Pfad. Wenn Sie die Verweise aktualisieren, werden sie an den neuen Asset-Pfad angepasst.

### Verschieben von Assets mithilfe des Drag-Vorgangs {#move-using-drag}

Sie können Assets (oder Ordner) in einen gleichgeordneten Ordner, die [!UICONTROL Leuchtkasten] -Sammlung oder eine andere Sammlung verschieben, indem Sie sie an den Speicherort der Zielgruppe ziehen, anstatt die Option &quot; [!UICONTROL Verschieben] &quot;in der Benutzeroberfläche zu verwenden. Dieser Vorgang ist jedoch nur in der Ansicht der Liste möglich.

Wenn Sie Assets durch Ziehen verschieben, wird der Assistent zum [!UICONTROL Verschieben von Assets] nicht geöffnet. Daher erhalten Sie beim Verschieben keine Option zum Umbenennen der Assets. Darüber hinaus werden die bereits veröffentlichten Assets beim Verschieben durch Ziehen erneut veröffentlicht, ohne dass die Zustimmung des Benutzers zur erneuten Veröffentlichung eingeholt werden muss.

![Verschieben von Assets in gleichgeordnete Ordner durch Ziehen von Assets](assets/move-by-drag.gif)

## Verwalten von Ausgabeformaten {#managing-renditions}

1. Sie können Ausgabeformate für ein Asset hinzufügen oder entfernen, mit Ausnahme des Originals. Navigieren Sie zum Speicherort des Assets, für das Sie Ausgabeformate hinzufügen oder entfernen möchten.

1. Klicken Sie auf das Asset, um seine Seite zu öffnen.
1. Wählen Sie in der Benutzeroberfläche &quot;Experience Manager&quot;in der Liste die Option **[!UICONTROL Darstellungen]** aus.

   ![Linke Leiste zum Öffnen des Menüs und Auswahl der Option &quot;Darstellungen&quot;](assets/renditions_menu.png)

1. Im Bereich **[!UICONTROL Ausgabeformate]** wird die Liste der für das Asset generierten Ausgabeformate angezeigt.

   ![Bedienfeld &quot;Darstellungen&quot;auf der Seite &quot;Assets Detail&quot;](assets/renditions_panel.png)

   >[!NOTE]
   >
   >By default, [!DNL Assets] does not display the original rendition of the asset in the preview mode. If you are an administrator, you can use overlays to configure [!DNL Assets] to display original renditions in the preview mode.

1. Wählen Sie ein Wiedergabeformat aus, um es anzuzeigen oder zu löschen.

   **Eine Darstellung löschen**

   Wählen Sie eine Darstellung aus dem **[!UICONTROL Bedienfeld &quot;Ausgabeformate]** &quot;und klicken Sie dann auf die **[!UICONTROL Option &quot;Darstellung]** löschen&quot;, um eine Ausgabeoption ![](assets/do-not-localize/deleteoutline.png) aus der Symbolleiste zu löschen. Ausgabedarstellungen können nach Abschluss der Asset-Verarbeitung nicht mehr stapelweise gelöscht werden. Bei einzelnen Assets können Sie Ausgabedarstellungen manuell aus der Benutzeroberfläche entfernen. Bei mehreren Assets können Sie Experience Manager anpassen, um bestimmte Darstellungen zu löschen oder die Assets zu löschen und die gelöschten Assets erneut hochzuladen.

   **Eine neue Darstellung hochladen**

   Navigate to the asset details page for the asset, and click the **[!UICONTROL Add Rendition]** ![Add rendition option to upload new rendition](assets/do-not-localize/add.png) option in the toolbar to upload a new rendition for the asset.

   >[!NOTE]
   >
   >Wenn Sie ein Ausgabeformat im Bedienfeld **[!UICONTROL Ausgabeformate]** auswählen, wird der Kontext der Symbolleiste geändert, sodass nur die für das Ausgabeformat relevanten Aktionen angezeigt werden. Options, such as the [!UICONTROL Upload Rendition] option is not displayed. Um diese Optionen in der Symbolleiste anzuzeigen, navigieren Sie zur Detailseite für das Asset.

   Sie können die Dimensionen für das anzuzeigende Ausgabeformat auf der Detailseite des entsprechenden Bild- oder Video-Assets konfigurieren. Based on the dimensions you specify, [!DNL Assets] displays the rendition with the exact or closest dimensions.

   Überlagern Sie zum Konfigurieren der Ausgabeformatabmessungen eines Bildes auf der Asset-Detailebene den Knoten `renditionpicker` (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) und konfigurieren Sie den Wert für die width-Eigenschaft. Konfigurieren Sie die Eigenschaft **[!UICONTROL size (Long) in KB]** anstelle von „width“, um das Ausgabeformat auf der Asset-Detailseite auf Grundlage der Bildgröße anzupassen. Bei größenbasierter Anpassung gibt die Eigenschaft `preferOriginal` der Originalgröße den Vorzug, wenn das angepasste Ausgabeformat größer ist als das Original.

   Ebenso können Sie das Bild der Anmerkungsseite durch Überlagern von `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker` anpassen.

   ![Overlay RenderingPicker-Knoten in CRXDE zum Anpassen des Bilds der Anmerkungsseite](assets/renditionpicker-node-crxde.png)

   Navigieren Sie zur Konfiguration der Ausgabeformatabmessungen für ein Video-Asset zum Knoten `videopicker` im CRX-Repository am Speicherort `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, überlagern Sie den Knoten und bearbeiten Sie dann die entsprechende Eigenschaft.

   >[!NOTE]
   >
   >Videoanmerkungen werden nur bei Browsern mit HTML5-kompatiblen Videoformaten unterstützt. Darüber hinaus werden je nach Browser unterschiedliche Videoformate unterstützt.

Weitere Informationen zum Erstellen und Anzeigen von Teilassets finden Sie unter [Verwalten von Teilassets](managing-linked-subassets.md#generate-subassets).

## Löschen von Assets {#deleting-assets}

Zum Löschen von Assets muss ein Benutzer über die entsprechenden Berechtigungen verfügen `dam/asset`. Wenn Sie nur eine Änderungsberechtigung haben, haben Sie nur die Möglichkeit, die Asset-Metadaten zu bearbeiten und Notizen zum Asset hinzuzufügen. Sie können jedoch das Asset oder dessen Metadaten nicht löschen.

Um die eingehenden Verweise von anderen Seiten aufzulösen oder zu entfernen, aktualisieren Sie die entsprechenden Verweise, bevor Sie ein Asset löschen. Um zu verhindern, dass Benutzer referenzierte Assets löschen und fehlerhafte Links beibehalten, deaktivieren Sie die Option zum erzwungenen Löschen mithilfe einer Überlagerung.

So löschen Sie ein Asset oder einen Ordner mit einem Asset:

1. Navigieren Sie zum Speicherort des Assets oder des Ordners, den Sie löschen möchten.

1. Wählen Sie das Asset oder den Ordner aus und klicken Sie in der Symbolleiste auf &quot; **[!UICONTROL Löschen]** &quot; ![](assets/do-not-localize/deleteoutline.png) .

   Nachdem Sie den Löschvorgang bestätigt haben:

   * Wenn das Asset keine Referenzen aufweist, wird es gelöscht.

   * If the asset has references, an error-message informs you that **One or more assets are referenced**. You can select **[!UICONTROL Force Delete]** or **[!UICONTROL Cancel]**.
   >[!NOTE]
   >
   >* Um die eingehenden Verweise von anderen Seiten aufzulösen oder zu entfernen, aktualisieren Sie die entsprechenden Verweise, bevor Sie ein Asset löschen. Deaktivieren Sie außerdem die Schaltfläche „Löschen erzwingen“ mithilfe einer Überlagerung, um zu verhindern, dass Benutzer referenzierte Assets löschen und fehlerhafte Links hinterlassen.
   >* Es ist möglich, einen *Ordner* zu löschen, der ausgecheckte Asset-Dateien enthält. Bevor Sie einen Ordner löschen, stellen Sie sicher, dass keine digitalen Assets von Benutzern ausgecheckt werden.


>[!NOTE]
>
>Wenn Sie einen Ordner mit der oben genannten Methode aus der Benutzeroberfläche löschen, werden auch die zugehörigen Benutzergruppen gelöscht.
>
>Vorhandene redundante, nicht verwendete und automatisch generierte Benutzergruppen können jedoch mithilfe der `clean` JMX-Methode in Ihrer Autoreninstanz (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`) aus dem Repository bereinigt werden.

## Herunterladen von Assets {#downloading-assets}

Siehe [Herunterladen von Assets von Experience Manager](/help/assets/download-assets-from-aem.md).

## Veröffentlichen von Assets {#publishing-assets}

>[!NOTE]
>
>Weitere Informationen speziell zu dynamischen Medien finden Sie unter [Veröffentlichen von Assets mit dynamischen Medien](/help/assets/publishing-dynamicmedia-assets.md).

1. Navigieren Sie zum Speicherort des bzw. der Asset(s)/Ordner, den Sie veröffentlichen möchten.

1. Either select the **[!UICONTROL Publish]** quick action from the asset card, or select the asset and click the **[!UICONTROL Quick Publish]** option from the toolbar.
1. Wenn das Asset andere Assets referenziert, werden die Verweise im Assistenten aufgelistet. Es werden nur Verweise angezeigt, die entweder unveröffentlicht sind oder seit der letzten Veröffentlichung/Aufhebung der Veröffentlichung geändert wurden. Wählen Sie die Referenzen aus, die Sie veröffentlichen möchten.

   >[!NOTE]
   >
   >Leere Ordner, die Teil eines von Ihnen veröffentlichten Ordners sind, werden nicht veröffentlicht.

1. Click **[!UICONTROL Publish]** to confirm the activation for the assets.

>[!CAUTION]
>
>Wenn Sie ein Asset veröffentlichen, das momentan verarbeitet wird, wird nur der ursprüngliche Inhalt veröffentlicht. Die Wiedergabeformate fehlen. Warten Sie entweder bis, die Verarbeitung abgeschlossen ist, und veröffentlichen Sie das Asset erst dann bzw. veröffentlichen Sie es erneut, wenn die Verarbeitung abgeschlossen ist.

## Rückgängigmachen der Veröffentlichung von Assets {#unpublishing-assets}

1. Navigieren Sie zum Speicherort des Assets/Asset-Ordners, das bzw. den Sie aus der Veröffentlichungsumgebung entfernen möchten (Veröffentlichung rückgängig machen).

1. Wählen Sie das Asset/den Ordner aus, dessen Veröffentlichung rückgängig gemacht werden soll, und klicken Sie in der Symbolleiste auf die Option **[!UICONTROL &quot;Veröffentlichung]** verwalten&quot; ![](assets/do-not-localize/globe-publication.png) .

1. Wählen Sie die Aktion **[!UICONTROL Veröffentlichung rückgängig machen]** aus der Liste aus.

   ![Aktion rückgängig machen](assets/unpublish_action.png)

1. Um die Veröffentlichung des Assets später rückgängig zu machen, wählen Sie **[!UICONTROL Veröffentlichung später rückgängig machen]** und anschließend ein Datum aus, an dem die Veröffentlichung des Assets rückgängig gemacht werden soll.
1. Legen Sie ein Datum fest, an dem die Assets aus der Veröffentlichungsumgebung entfernt werden sollen.
1. Wenn das Asset andere Assets referenziert, wählen Sie die Verweise aus, deren Veröffentlichung Sie rückgängig machen möchten. Klicken Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]**.
1. Klicken Sie im Bestätigungsdialogfeld auf:

   * **[!UICONTROL Abbrechen]**, um die Aktion abzubrechen.
   * **[!UICONTROL Veröffentlichung rückgängig machen]**, um zu bestätigen, dass die Veröffentlichung der Assets zum angegebenen Datum rückgängig gemacht wird (sodass die Assets nicht mehr in der Veröffentlichungsumgebung verfügbar sind).

   >[!NOTE]
   >
   >Wenn Sie die Veröffentlichung eines komplexen Assets rückgängig machen möchten, achten Sie darauf, nur die Veröffentlichung des Assets rückgängig zu machen. Machen Sie nicht die Veröffentlichung der Referenzen rückgängig, da diese möglicherweise auch von anderen veröffentlichten Assets referenziert werden.

## Geschlossene Benutzergruppe {#closed-user-group}

A closed user group (CUG) is used to limit access to specific asset folders published from [!DNL Experience Manager]. Wenn Sie eine CUG für einen Ordner erstellen, wird der Zugriff auf diesen Ordner (einschließlich Ordner-Assets und Unterordnern) auf zugewiesene Mitglieder und Gruppen beschränkt. Um auf einen Ordner zuzugreifen, müssen Benutzer mit ihren Sicherheitsanmeldedaten angemeldet sein.

CUGs stellen eine zusätzliche Möglichkeit dar, den Zugang zu Ihren Assets zu beschränken. Sie können auch eine Anmeldeseite für den Ordner konfigurieren.

1. Select a folder from the [!DNL Assets] interface, and click the [!UICONTROL Properties] option from the toolbar to display the properties page.
1. Fügen Sie auf der Registerkarte **[!UICONTROL Berechtigungen]** unter **[!UICONTROL Geschlossene Benutzergruppe]** Mitglieder oder Gruppen hinzu.

   ![hinzufügen Benutzer in geschlossenen Benutzergruppen](assets/add_user.png)

1. Um einen Anmeldebildschirm anzuzeigen, wenn Benutzer auf den Ordner zugreifen, wählen Sie die Option **[!UICONTROL Aktivieren]** aus. Then, select the path to a login page in [!DNL Experience Manager], and save the changes.

   ![Anmeldeseite aktivieren und auswählen, die beim Ordner mit Benutzerzugriff angezeigt werden soll](assets/login_page.png)

   >[!NOTE]
   >
   >If you do not specify the path to a login page, [!DNL Experience Manager] displays the default login page in the publish instance.

1. Veröffentlichen Sie den Ordner und versuchen Sie, über die Veröffentlichungsinstanz darauf zuzugreifen. Es wird ein Anmeldebildschirm angezeigt.
1. Wenn Sie Mitglied der CUG sind, geben Sie Ihre Anmeldedaten ein. The folder is displayed after [!DNL Experience Manager] authenticates you.

## Suchen von Assets         {#assetsearch}

Die Suche nach Assets spielt bei der Nutzung eines Digital-Asset-Management-Systems eine zentrale Rolle – sowohl für eine weitere Verwendung durch Kreativprofis als auch für eine robuste Verwaltung von Assets durch Geschäftsbenutzer und Marketing-Experten oder für die Verwaltung durch DAM-Administratoren.

For simple, advanced, and custom searches to discover and use the most appropriate assets, see [search assets in Experience Manager](search-assets.md).

## Schnellaktionen {#quick-actions}

Schnellaktion-Symbole sind jeweils nur für ein Asset verfügbar. Führen Sie je nach Gerät folgende Aktionen durch, um die Symbole der Schnellaktionen anzuzeigen:

* Touch-Geräte: Tippen und halten. Mit einem Touch-Gerät, wie z. B. einem iPad, können Sie länger auf ein Asset tippen, damit die Schnellaktionen angezeigt werden.
* Nicht-Touch-Geräte: Mit Mauszeiger darüberfahren. Auf einem Desktop-Gerät wird beispielsweise eine Schnellzugriffsleiste angezeigt, wenn Sie mit dem Mauszeiger über die Miniaturansicht des Assets fahren.

### Navigieren und Auswählen von Assets {#navigating-and-selecting-assets}

You can view, navigate through, and select assets with any of the available views (Card, Column, and List) using the **[!UICONTROL Select]** option.

In der Ansicht &quot;Ansicht der Liste&quot;und &quot;Spalte&quot;wird die Option &quot; **[!UICONTROL Auswählen]** &quot;angezeigt, wenn Sie den Mauszeiger über die Asset-Miniaturansicht bewegen.

![Assets in der Ansicht Liste auswählen](assets/select_quick_in_listview.png)

![Assets in der Ansicht der Spalte auswählen](assets/select_quick_in_columnview.png)

In der Ansicht der Karte wird die Option &quot; **[!UICONTROL Auswählen]** &quot;als Schnellaktion angezeigt.

![Schnellaktion bei der Ansicht der Karte auswählen](assets/select_quick_action.png)

Beim Durchsuchen eines Ordners oder einer Sammlung in der [!DNL Assets] Benutzeroberfläche eines Browsers können Sie alle angezeigten oder geladenen Assets mit der Option &quot;Alle [!UICONTROL auswählen] &quot;in der oberen rechten Ecke auswählen. Zunächst werden nur 100 Assets in der Ansicht geladen und 200 in der Ansicht der Liste. Weitere Assets werden beim Bildlauf auf der Suchergebnisseite in Ansicht geladen. Mit der Option &quot;Alle [!UICONTROL auswählen] &quot;werden nur die geladenen Assets ausgewählt.

For more information, see [view and selecting your resources](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

## Bearbeiten von Bildern {#editing-images}

The editing tools in the [!DNL Assets] interface let you perform small editing jobs on image assets. Sie können Bilder beschneiden, drehen, spiegeln und auf andere Arten bearbeiten. Sie können auch Imagemaps zu den Assets hinzufügen.

>[!NOTE]
>
>Bei manchen Komponenten sind für den Vollbildmodus zusätzliche Optionen verfügbar.

1. Führen Sie einen der folgenden Schritte aus, um ein Element im Bearbeitungsmodus zu öffnen:

   * Select the asset and then click **[!UICONTROL Edit]** in the toolbar.
   * Click **[!UICONTROL Edit]** option that displays on an asset in the card view.
   * Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

   ![Option in der Symbolleiste bearbeiten](assets/do-not-localize/edit_icon.png)

1. Wenn Sie das Bild beschneiden möchten, klicken Sie auf **[!UICONTROL &quot;Beschneiden]** &quot;, um ein Bild ![](assets/do-not-localize/crop.png)zu beschneiden.

1. Wählen Sie die gewünschte Option aus der Liste aus. Der Zuschneidebereich wird auf dem Bild je nach gewählter Option angezeigt. Mit der Option **Freihand** können Sie das Bild ohne Einschränkungen des Seitenverhältnisses zuschneiden.

   ![Optionen für das Zuschneiden](assets/crop-options.png)

1. Wählen Sie den zuzuschneidenden Bereich und ändern Sie die Größe oder Position auf dem Bild.

1. Verwenden Sie die Optionen **[!UICONTROL &quot;]** Rückgängig ![:](assets/do-not-localize/undo.png) Rückgängig&quot;und &quot; **[!UICONTROL Wiederholen]** &quot;der Symbolleistenoptionen ![](assets/do-not-localize/redo.png) , um zum nicht beschnittenen Bild zurückzukehren oder das zugeschnittene Bild beizubehalten.
1. Click the appropriate **[!UICONTROL Rotate]** option to rotate the image clockwise or anti-clockwise.

   ![Drehen im Uhrzeigersinn und gegen den Uhrzeigersinn](assets/do-not-localize/rotate-options.png)

1. Klicken Sie auf die entsprechenden **[!UICONTROL Flip]** -Optionen, um das Bild horizontal ![um die horizontale Option](assets/do-not-localize/flip-horizontal.png) oder vertikal um die vertikale Option ![](assets/do-not-localize/flip-vertical.png)zu drehen.

1. Um die Bildbearbeitung abzuschließen, klicken Sie auf &quot; **[!UICONTROL Fertig stellen]** &quot; ![](assets/do-not-localize/check-ok-done-icon.png). Durch Klicken auf **Fertig stellen** wird auch die Wiederherstellung der Darstellungen Beginn.

>[!NOTE]
>
>Bildbearbeitung wird für die Dateiformate BMP, GIF, PNG und JPEG unterstützt.

Sie können auch Imagemaps mit dem Bild-Editor hinzufügen. Einzelheiten dazu finden Sie in [Hinzufügen von Imagemaps](/help/assets/image-maps.md).

>[!NOTE]
>
>Zum Bearbeiten einer TXT-Datei verwenden Sie **Day CQ Link Externalizer** in Configuration Manager.

## Timeline {#timeline}

In der Timeline können Sie diverse Ereignisse für ein ausgewähltes Objekt ansehen, wie z. B. aktive Workflows für ein Asset, Kommentare/Anmerkungen, Aktivitätsprotokolle und Versionen.

![Sortieren von Timeline-Einträgen für ein Asset](assets/sort_timeline.gif)

*Abbildung: Sortieren von Zeitleisteneinträgen für ein Asset*

>[!NOTE]
>
>In der [Konsole für Sammlungen](/help/assets/managing-collections-touch-ui.md#navigating-the-collections-console) bietet die Liste **[!UICONTROL Alle anzeigen]** Optionen, um nur Kommentare und Workflows anzuzeigen. Darüber hinaus wird die Timeline nur für Sammlungen auf der höchsten Ebene angezeigt, die in der Konsole aufgelistet sind. Sie wird nicht angezeigt, wenn Sie in einer der Sammlungen navigieren.

>[!NOTE]
>
>Die Timeline enthält mehrere [inhaltsfragmentspezifische Optionen](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

## Anmerkungen zu Assets {#annotating}

Anmerkungen sind Kommentare oder erläuternde Hinweise, die Bildern oder Videos hinzugefügt werden. Anmerkungen bieten Marketern die Möglichkeit, zusammenzuarbeiten und Feedback zu Assets bereitzustellen.

Videoanmerkungen werden nur bei Browsern mit HTML5-kompatiblen Videoformaten unterstützt. Video formats that [!DNL Assets] supports depend on the browser.

>[!NOTE]
>
>Bei Inhaltsfragmenten werden [Anmerkungen im Fragment-Editor erstellt](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment).

1. Navigieren Sie zum Speicherort des Assets, dem Sie Anmerkungen hinzufügen möchten.
1. Click the **[!UICONTROL Annotate]** option from one of the following:

   * [Schnellaktionen](/help/assets/managing-assets-touch-ui.md#quick-actions)
   * In der Symbolleiste, nachdem Sie das Asset ausgewählt haben        oder zur Asset-Seite navigiert sind

   ![Option &quot;Anmerkung&quot;](assets/annotate-option.png)

1. Fügen Sie im Feld **[!UICONTROL Kommentar]** am unteren Rand der Timeline einen Kommentar hinzu. Sie haben auch die Möglichkeit, einen Bereich im Bild zu markieren und im Dialogfeld **[!UICONTROL Anmerkung hinzufügen]** eine Anmerkung hinzuzufügen.

   ![Kommentarfeld im Dialogfeld &quot;Hinzufügen Anmerkung&quot;](assets/annotation-comment-box.png)

1. Um einen Benutzer über eine Anmerkung zu benachrichtigen, geben Sie die E-Mail-Adresse des Benutzers an und fügen Sie den Kommentar hinzu. Beispiel: Um Aaron MacDonald über eine Anmerkung zu benachrichtigen, geben Sie „@aa“ ein. Vorschläge für alle übereinstimmenden Benutzer werden in einer Liste angezeigt. Wählen Sie die E-Mail-Adresse von Aaron in der Liste aus, um ihn über den Kommentar zu informieren. Sie können auch weitere Benutzer innerhalb, vor oder nach der Anmerkung taggen.

   ![E-Mail-Adresse des Benutzers angeben und Kommentar hinzufügen, um den Benutzer zu benachrichtigen](assets/annotation-add-user-email.png)

   >[!NOTE]
   >
   >For a non-administrator user, the suggestions appear only if the user has read permissions at `/home` path in CRXDE.

1. Nachdem Sie die Anmerkung hinzugefügt haben, klicken Sie auf **[!UICONTROL Hinzufügen]**, um sie zu speichern. Eine Benachrichtigung über die Anmerkung wird an Aaron gesendet.

   ![Schaltfläche &quot;Hinzufügen&quot;zum Speichern einer Anmerkung](assets/annotation-add.png)

   >[!NOTE]
   >
   >Sie können mehrere Anmerkungen hinzufügen, bevor Sie diese speichern.

1. Klicken Sie auf **[!UICONTROL Schließen]**, um den Anmerkungsmodus zu verlassen.
1. To view the notification, log in to [!DNL Assets] with Aaron MacDonald&#39;s credentials and click the **[!UICONTROL Notifications]** option to view the notification.

   >[!NOTE]
   >
   >Sie können Video-Assets auch Anmerkungen hinzufügen. Während Videos mit Anmerkungen versehen werden, wird der Player angehalten, damit Sie einem Frame eine Anmerkung hinzufügen können. Details finden Sie unter [Verwalten von Video-Assets](/help/assets/managing-video-assets.md).

1. To choose a different color so you can differentiate between users, click the Profile option and click **[!UICONTROL My Preferences]**.

   ![Wählen Sie die Option &quot;Benutzereinstellungen&quot;und dann &quot;Meine Voreinstellungen&quot;, um die Benutzereinstellungen zu öffnen](assets/User-profile-preferences.png)

   Specify the desired color in the **[!UICONTROL Annotation Color]** box and then click **[!UICONTROL Accept]**.

   ![Wählen Sie in den Benutzereinstellungen die Farbe der Anmerkung aus, um die Farbe der Benutzerrolle festzulegen](assets/Annotation-color.png)

>[!NOTE]
>
>Sie können auch Anmerkungen zu einer Sammlung hinzufügen. Wenn eine Sammlung jedoch untergeordnete Sammlungen enthält, können Sie nur der übergeordneten Sammlung Anmerkungen/Kommentare hinzufügen. Die Option „Anmerken“ ist nicht für untergeordnete Sammlungen verfügbar.

### Anzeigen gespeicherter Anmerkungen {#viewing-saved-annotations}

1. Um die gespeicherten Anmerkungen zu einem Asset anzuzeigen, navigieren Sie zum Speicherort des Assets und öffnen Sie die Asset-Seite für dieses Asset.

1. Wählen Sie in der Benutzeroberfläche &quot;Experience Manager&quot;die Option &quot; **[!UICONTROL Zeitschiene]**&quot;aus.

   ![Zeitschiene im Experience Manager verfügbar](assets/view-timeline.png)

1. Wählen Sie in der Liste **[!UICONTROL Alle anzeigen]** in der Timeline **[!UICONTROL Kommentare]** aus, um die Ergebnisse anhand von Anmerkungen zu filtern.

   ![Alle Listen in der Zeitschiene anzeigen](assets/timeline-show-all-option.png)

   Klicken Sie im Bedienfeld **[!UICONTROL Timeline]** auf einen Kommentar, um die entsprechende Anmerkung auf dem Bild anzuzeigen.

   ![Zeitschienenbedienfeld zur Ansicht Anmerkung zum Bild](assets/timeline-view-annotations.png)

   Klicken Sie auf **[!UICONTROL Löschen]**, um einen bestimmten Kommentar zu löschen.

### Drucken von Anmerkungen {#printing-annotations}

Wenn ein Asset Anmerkungen aufweist oder einem Prüfungs-Workflow unterzogen wurde, können Sie das Asset einschließlich der Anmerkungen und des Prüfungsstatus für die Offline-Prüfung als PDF-Datei drucken.

Sie können auch nur die Anmerkungen oder nur den Prüfungsstatus drucken.

To print the annotations and review status, click **[!UICONTROL Print]** and follow the instructions in the wizard. The **[!UICONTROL Print]** option appears in the toolbar only when the asset has at least one annotation or review status assigned to it.

1. From the [!DNL Assets] interface, open the preview page for an asset.
1. Führen Sie einen der folgenden Schritte aus:

   * Zum Drucken aller Anmerkungen und des Prüfungsstatus überspringen Sie Schritt 3. Dann fahren Sie direkt mit Schritt 4 fort.
   * Zum Drucken bestimmter Anmerkungen und des Prüfungsstatus öffnen Sie die [Timeline](/help/assets/managing-assets-touch-ui.md#timeline) und fahren Sie mit Schritt 3 fort.

1. Zum Drucken bestimmter Anmerkungen wählen Sie die Anmerkungen aus der Timeline aus.

   ![Wählen Sie eine Anmerkung in der Zeitleiste aus, um sie zu drucken](assets/timeline-select-annotations.png)

   Um nur den Prüfungsstatus zu drucken, wählen Sie ihn aus der Timeline aus.

1. Click **[!UICONTROL Print]** from the toolbar.

   ![Druckoption in der Symbolleiste](assets/do-not-localize/print.png)

1. Wählen Sie im Dialogfeld „Drucken“ die Position, deren Anmerkungen/Prüfungsstatus in der PDF-Datei angezeigt werden sollen. Wenn Sie beispielsweise die Anmerkungen/den Status in der linken oberen Ecke der Seite drucken möchten, die das gedruckte Bild enthält, verwenden Sie die Einstellung **Oben links**. Sie ist standardmäßig aktiviert.

   ![Position der Anmerkung/des Überprüfungsstatus auswählen, der im Dialogfeld &quot;Drucken&quot;in PDF angezeigt werden soll](assets/Print-annotation-dialog.png)

   Sie können auch andere Einstellungen wählen, je nach der von Ihnen gewünschten Position der Anmerkungen oder des Status in der gedruckten PDF-Datei. Wenn sich die von Ihnen gewünschte Position der Anmerkungen/des Status auf einer Seite befindet, die nicht zum gedruckten Asset gehört, wählen Sie **[!UICONTROL Nächste Seite]**.

   >[!NOTE]
   >
   >Längere Anmerkungen werden in der PDF-Datei möglicherweise nicht richtig gerendert. Für optimales Rendering wird empfohlen, Anmerkungen auf 50 Wörter zu begrenzen.

1. Klicken Sie auf **[!UICONTROL Drucken]**. Je nach der Option, die Sie in Schritt 2 wählen, zeigt die erstellte PDF-Datei die Anmerkungen/den Status an der angegebenen Position an. Beispiel: Wenn Sie beide Anmerkungen und den Prüfungsstatus mithilfe der Einstellung **Oben links** drucken, ähnelt die erstellte Ausgabe der hier dargestellten PDF-Datei.

   ![Anmerkungs- und Überprüfungsstatus in der erstellten PDF](assets/annotation-status-pdf.png)

1. Download- ![Download-Option für PDF](assets/do-not-localize/download.png) oder ![Druckoptionen für PDF](assets/do-not-localize/print.png) im PDF mit den Optionen oben rechts.

   >[!NOTE]
   >
   >Wenn das Asset Unter-Assets enthält, können Sie alle Unter-Assets zusammen mit ihren jeweiligen seitenweisen Anmerkungen drucken.

   Um das Erscheinungsbild der gerenderten PDF-Datei zu ändern (z. B. Schriftfarbe, Größe, Stil und Hintergrundfarbe der Kommentare und Status), öffnen Sie in Configuration Manager die **[!UICONTROL Konfiguration für PDF-Anmerkungen]** und ändern Sie die gewünschten Optionen. Um beispielsweise die Anzeigefarbe des Status „Bestätigt“ zu ändern, modifizieren Sie im entsprechenden Feld den Farbcode. Informationen zum Ändern der Schriftfarbe von Anmerkungen finden Sie unter [Anmerken](/help/assets/managing-assets-touch-ui.md#annotating).

   ![Konfiguration zum Drucken der Asset-Anmerkung im PDF-Dokument](assets/annotation-print-pdf-config.png)

   Kehren Sie zu der gerenderten PDF-Datei zurück und aktualisieren Sie sie. Der aktualisierte PDF-Datei spiegelt die von Ihnen vorgenommenen Änderungen wider.

If an asset includes annotations in foreign languages (especially non-latin languages), you must first configure CQ-DAM-Handler-Gibson Font Manager Service on the [!DNL Experience Manager] server to be able to print these annotations. Beim Konfigurieren des CQ-DAM-Handler-Gibson Font Manager Service geben Sie den Pfad an, über den auf die gewünschten Sprachen zugegriffen werden kann.

1. Öffnen Sie die Konfigurationsseite „CQ-DAM-Handler-Gibson Font Manager Service“ über die URL `https://[aem_server]:[port]/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl`.
1. Um den CQ-DAM-Handler-Gibson Font Manager Service zu konfigurieren, führen Sie einen der folgenden Schritte aus:

   * Unter der Option „Verzeichnis der Systemschriftarten“ geben Sie den vollständigen Pfad für das Verzeichnis der Schriftarten auf Ihrem System an. Als Mac-Benutzer können Sie beispielsweise unter der Option „Verzeichnis der Systemschriftarten“ den Pfad als */Library/Fonts* angeben. [!DNL Experience Manager] ruft die Schriftarten aus diesem Verzeichnis ab.
   * Erstellen Sie ein Verzeichnis mit dem Namen `fonts` im Ordner `crx-quickstart`. Der CQ-DAM-Handler-Gibson Font Manager Service ruft die Schriftarten automatisch vom Speicherort `crx-quickstart/fonts` ab. Sie können diesen Standardpfad innerhalb der Option „Verzeichnis für Adobe-Serverschriftarten“ überschreiben.

   * Erstellen Sie einen neuen Ordner für Schriftarten in Ihrem System und speichern Sie in diesem Ordner die gewünschten Schriftarten. Anschließend geben Sie in der Option „Verzeichnis für Kundenschriftarten“ den vollständigen Pfad zu diesem Ordner ein.

1. Greifen Sie über die URL `https://[aem_server]:[4502]/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig` auf die Konfiguration für PDF-Anmerkungen zu.
1. Konfigurieren Sie die PDF-Datei, die Anmerkungen enthält, wie folgt mit der richtigen Schriftart:

   * Schließen Sie die Zeichenfolge `<font_family_name_of_custom_font, sans-serif>` in der Schriftartoption ein. Wenn Sie z. B. Anmerkungen in CJK (Chinesisch, Japanisch und Koreanisch) drucken möchten, schließen Sie die Zeichenfolge `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` in die Schriftartoption ein. Wenn Sie Anmerkungen in Hindi drucken möchten, laden Sie die entsprechende Schriftart herunter. Anschließend konfigurieren Sie die Schriftart als Arial Unicode MS, Noto Sans, Noto Sans CJK JP, Noto Sans Devanagari, Sans-Serif.

1. Starten Sie die [!DNL Experience Manager] Bereitstellung neu.

Here is an example of how you can configure [!DNL Experience Manager] to print annotations in CJK (Chinese, Japanese and Korean):

1. Laden Sie die Google Noto CJK-Schriftarten über die folgenden Links herunter und speichern Sie sie im Schriftartenverzeichnis, das in Font Manager Service konfiguriert ist.

   * Schriftart All In One Super CJK: [https://www.google.com/get/noto/help/cjk/](https://www.google.com/get/noto/help/cjk/)
   * Noto Sans (für europäische Sprachen): [https://www.google.com/get/noto/](https://www.google.com/get/noto/)
   * Noto-Schriftarten für eine Sprache Ihrer Wahl: [https://www.google.com/get/noto/](https://www.google.com/get/noto/)

1. Konfigurieren Sie die PDF-Datei, die Anmerkungen enthält, indem Sie den Schriftartparameter auf `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` setzen. Diese Konfiguration ist standardmäßig verfügbar und funktioniert bei allen europäischen und CJK-Sprachen.
1. Wenn sich die Sprache Ihrer Wahl von den Sprachen unterscheidet, die in Schritt 2 erwähnt werden, fügen Sie der Standardschriftart einen entsprechenden (kommagetrennten) Eintrag hinzu.

## Erstellen, Verwalten, Vorschau und Wiederherstellen von Asset-Versionen {#asset-versioning}

Bei der Versionierung wird eine Momentaufnahme von digitalen Assets zu einem bestimmten Zeitpunkt aufgezeichnet. Sie hilft Ihnen bei der späteren Wiederherstellung eines vorherigen Asset-Zustands. Wenn Sie etwa eine Änderung an einem Asset rückgängig machen wollen, stellen Sie die unbearbeitete Version des Assets wieder her. Sie [!DNL Experience Manager]können eine Version erstellen, die aktuelle Version Ansicht, Unterschiede zwischen zwei Ansichten von Bildern nebeneinander darstellen und ein Asset in der vorherigen Version wiederherstellen.

Sie können Versionen in [!DNL Experience Manager] den folgenden Szenarien erstellen:

* Laden Sie ein Asset mit demselben Dateinamen hoch, der sich am selben Speicherort befindet. Es kann sich um ein neues Asset oder um eine geänderte Version desselben Assets handeln.
* Bearbeiten Sie ein Bild in [!DNL Experience Manager] und speichern Sie die Änderungen.
* Bearbeiten Sie die Metadaten eines Assets.
* Verwenden Sie die [!DNL Experience Manager] Desktop-App, um ein vorhandenes Asset auszuchecken, zu bearbeiten und die Änderungen [hochzuladen](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#edit-assets-upload-updated-assets).

Sie können mithilfe eines Workflows die automatische Versionierung aktivieren. Wenn Sie eine Version für ein Asset erstellen, werden die Metadaten und Ausgabeformate gemeinsam mit der Version gespeichert. Ausgabeformate sind gerenderte Alternativen für dieselben Bilder, z. B. ein PNG-Ausgabeformat einer hochgeladenen JPEG-Datei.

1. Navigieren Sie zum Speicherort des Assets, für das Sie eine Version erstellen möchten, und klicken Sie darauf, um die Vorschau zu öffnen. Öffnen Sie in der oberen linken Ecke der Seite das Menü und wählen Sie **[!UICONTROL Zeitschiene]**.

   ![Wählen Sie im linken Navigationsmenü die Option &quot;Zeitschiene&quot;](assets/timeline.png)

   *Abbildung: Öffnen Sie das Menü aus dem oberen linken Bereich der Seite und wählen Sie die Option &quot;[!UICONTROL Zeitschiene]&quot;aus.*

1. So erstellen Sie eine Version des Assets

   * Click the **[!UICONTROL Actions]** at the bottom.
   * Klicken Sie auf **[!UICONTROL Als Version speichern]**, um eine Version für das Asset zu erstellen. Fügen Sie optional eine Beschriftung und einen Kommentar hinzu.
   * Klicken Sie auf **[!UICONTROL Erstellen]** , um eine Version zu erstellen.

      ![Asset-Version von der Seitenleiste erstellen](assets/create-new-version-from-timeline.png)

      *Abbildung: Erstellen Sie eine Version eines Assets über die linke[!UICONTROL Zeitleiste].*

1. So Ansicht einer Asset-Version:

   * Klicken Sie auf **[!UICONTROL Alle]** in der [!UICONTROL Zeitleiste]anzeigen.
   * Klicken Sie auf **[!UICONTROL Versionen]**. Alle für ein Asset erstellten Versionen werden in der linken Seitenleiste aufgeführt.

      ![ Option &quot;Versionen auswählen&quot;in der Zeitleiste](assets/versions_option.png)

   * Wählen Sie eine bestimmte Version des Assets aus und klicken Sie auf **[!UICONTROL Vorschau Version]**.

1. Gehen Sie wie folgt vor, um zu einer älteren Version des Assets zurückzukehren. Nach dem Zurücksetzen wird diese Version auf der [!DNL Assets] Benutzeroberfläche angezeigt und steht zur Verwendung zur Verfügung.

   * Klicken Sie auf eine Version des Assets. Fügen Sie optional eine Beschriftung und einen Kommentar hinzu.
   * Click **[!UICONTROL Revert to this Version]**.

      ![Wählen Sie eine Version aus, um sie wiederherzustellen](assets/select_version.png)

      *Abbildung: Wählen Sie eine Version aus und stellen Sie sie wieder her. Es wird die aktuelle Version, die dann den DAM-Benutzern zur Verfügung steht.*

1. Gehen Sie wie folgt vor, um zwischen zwei Versionen eines Bildes zu vergleichen:
   * Klicken Sie auf die Version, die mit der aktuellen Version verglichen werden soll.
   * Ziehen Sie den Schieberegler nach links, um diese Version über die aktuelle Version zu stellen und zu vergleichen.

   ![Verwenden Sie den Regler, um die ausgewählten Versionen eines Assets mit der aktuellen Version zu vergleichen.](assets/version-slider.gif)

   *Abbildung: Mit dem Schieberegler können Sie die ausgewählten Versionen eines Assets mühelos mit der aktuellen Version vergleichen.*

### Start a workflow on an asset {#starting-a-workflow-on-an-asset}

Informationen zum Anwenden eines Workflows auf die Verarbeitung eines Assets finden Sie unter Arbeitsablauf für [Beginn eines Assets](/help/assets/assets-workflow.md#apply-a-workflow-to-an-asset).

## Sammlungen {#collections}

Bei einer Sammlung handelt es sich um eine sortierte Gruppe von Assets. Verwenden Sie Sammlungen, um verwandte Assets zwischen Benutzern freizugeben oder ähnliche Assets zu gruppieren, um sie einfach zu finden.

* Eine Sammlung kann Assets aus verschiedenen Speicherorten enthalten, da sie nur Verweise zu diesen Assets aufweisen. Jede Sammlung hält die referenzielle Integrität von Assets aufrecht.
* Sie können Sammlungen für mehrere Benutzer mit unterschiedlichen Berechtigungsstufen wie Bearbeiten, Anzeigen usw. freigeben.

See [manage collections](/help/assets/managing-collections-touch-ui.md) for details on collection management.
