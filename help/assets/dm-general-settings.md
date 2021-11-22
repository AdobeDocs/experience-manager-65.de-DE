---
title: Allgemeine Dynamic Media-Einstellungen konfigurieren
description: Erfahren Sie, wie Sie die allgemeinen Einstellungen in Dynamic Media verwalten. Sie können hier den Namen des Veröffentlichungs-Servers und den Namen des Ursprungs-Servers festlegen und eine Option zum Überschreiben von Bildern festlegen. Es gibt auch standardmäßige Upload-Optionen für die Unschärfemaske von Bildern und Upload-Optionen für die Verarbeitung von PostScript-, Adobe Photoshop-, PDF- und Adobe Illustrator-Dateien.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
hide: true
hidefromtoc: true
exl-id: null
source-git-commit: 343b48a4ec5e7124aaa48b7550465982d61fa5ab
workflow-type: tm+mt
source-wordcount: '2461'
ht-degree: 34%

---


# Allgemeine Dynamic Media-Einstellungen konfigurieren

Konfiguration **[!UICONTROL Allgemeine Dynamic Media-Einstellungen]** ist nur verfügbar, wenn:

* Sie führen Dynamic Media im Scene7-Modus aus. Siehe [Aktivieren von Dynamic Media im Scene7-Modus](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode).
* Sie haben eine *vorhandene* **[!UICONTROL Dynamic Media-Konfiguration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager 6.5.11 oder höher.
* Sie sind ein Experience Manager-Systemadministrator mit Administratorrechten.

Dynamic Media General Settings ist für erfahrene Website-Entwickler und -Programmierer vorgesehen. Adobe Dynamic Media empfiehlt, dass Benutzer, die diese Veröffentlichungseinstellungen ändern, mit Dynamic Media in Adobe Experience Manager und der grundlegenden Bildverarbeitungstechnologie vertraut sind.

Bei der Kontoerstellung stellt Adobe Dynamic Media automatisch die zugewiesenen Server für Ihr Unternehmen bereit. Diese Server werden verwendet, um URL-Zeichenfolgen für Ihre Website und Programme zu erstellen. Diese URL-Aufrufe gelten spezifisch für Ihr Konto.

Auf der Seite &quot;Veröffentlichungseinstellungen von Dynamic Media&quot;werden Standardeinstellungen festgelegt, die festlegen, wie Assets von Adobe Dynamic Media-Servern an Websites oder Anwendungen bereitgestellt werden. Wenn keine Einstellung festgelegt ist, stellt der Adobe Dynamic Media-Server ein Asset gemäß einer Standardeinstellung bereit, die auf der Seite &quot;Veröffentlichungseinstellungen&quot;von Dynamic Media konfiguriert wurde.

Siehe auch [Optional - Einrichtung und Konfiguration von Dynamic Media - Einstellungen für den Scene7-Modus](/help/assets/option-b-config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings) für weitere optionale Konfigurationsaufgaben.

>[!NOTE]
>
>Upgrade von Dynamic Media Classic auf Dynamic Media auf Adobe Experience Manager? Die Seite &quot;Allgemeine Einstellungen&quot;und [Veröffentlichungseinstellungen](/help/assets/dm-publish-settings.md) -Seite in Dynamic Media vorab mit den Werten ausgefüllt, die von Ihrem Dynamic Media Classic-Konto übernommen wurden. Die Ausnahmen sind alle Werte, die unter dem **[!UICONTROL Standardmäßige Upload-Optionen]** auf der Seite &quot;Allgemeine Einstellungen&quot;angezeigt. Diese Werte befinden sich bereits im Experience Manager. Alle Änderungen, die Sie unter **[!UICONTROL Standardmäßige Upload-Optionen]** auf einer der fünf Registerkarten über die Experience Manager-Benutzeroberfläche angezeigt werden, spiegeln sich in Dynamic Media wider, nicht in Dynamic Media Classic. Alle anderen Einstellungen und Werte auf der Seite &quot;Allgemeine Einstellungen&quot;und der [Veröffentlichungseinstellungen](/help/assets/dm-publish-settings.md) -Seite zwischen Dynamic Media Classic und Dynamic Media auf dem Experience Manager verwaltet.

**So konfigurieren Sie die allgemeinen Dynamic Media-Einstellungen:**

1. Wählen Sie im Experience Manager-Autorenmodus das Experience Manager-Logo aus, um auf die globale Navigationskonsole zuzugreifen.
1. Wählen Sie in der linken Leiste das Symbol Tools und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Allgemeine Dynamic Media-Einstellungen]**.
1. Legen Sie auf der Seite Server Ihre **[!UICONTROL Veröffentlichter Servername]** und **[!UICONTROL Name des ursprünglichen Servers]** und dann auf den fünf Registerkarten die standardmäßigen Upload-Optionen für die Bildbearbeitung und für PostScript-, Photoshop-, PDF- und Illustrator-Dateien konfigurieren.

   * [Server](#server-general-setting)
   * [In Programm hochladen](#upload-to-application)
   * [Bildbearbeitung](#image-editing-tab) tab
   * [PostScript](#postscript-tab) tab
   * [Photoshop](#photoshop-tab) tab
   * [PDF](#pdf-tab) tab
   * [Illustrator](#illustrator-tab) tab

   ![Dynamic Media-Seite &quot;Allgemeine Einstellungen&quot;](/help/assets/assets-dm/dm-general-settings.png)
   *Seite &quot;Allgemeine Dynamic Media-Einstellungen&quot;mit der **[!UICONTROL Bildbearbeitung]**ausgewählt ist.*<br><br>

1. Wenn Sie fertig sind, wählen Sie rechts oben auf der Seite die Option **[!UICONTROL Speichern]**.

## Server {#server-general-setting}

Bei der Kontoerstellung stellt Adobe Dynamic Media automatisch die zugewiesenen Server für Ihr Unternehmen bereit. Diese Server werden verwendet, um URL-Zeichenfolgen für Ihre Website und Programme zu erstellen. Diese URL-Aufrufe gelten spezifisch für Ihr Konto.

| Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Veröffentlichungs-Server-Name]** | Erforderlich.<br>Der Name muss `https://` im Pfad.<br>Dieser Server ist der Live-CDN (Content Deliver Network)-Server, der in allen systemgenerierten URL-Aufrufen verwendet wird, die für Ihr Konto spezifisch sind. Ändern Sie diesen Servernamen nur, wenn Sie vom technischen Support von Adobe dazu angewiesen werden. |
| **[!UICONTROL Ursprungs-Server-Name]** | Erforderlich.<br>Dieser Server wird nur für Qualitätssicherungstests verwendet. Ändern Sie diesen Servernamen nur, wenn Sie vom technischen Support von Adobe dazu aufgefordert werden. |

## In Programm hochladen {#upload-to-application}

* **[!UICONTROL Bilder überschreiben]**

   Adobe Dynamic Media lässt zwei Dateien mit demselben Namen nicht zu. Die Dynamic Media ID der Adobe jedes Elements (der Bildname abzüglich der Dateinamenerweiterung) muss eindeutig sein. Aufgrund dieser Regel **[!UICONTROL In Anwendung hochladen]** hat eine Überschreibungsmöglichkeit. Der genaue Effekt dieser Option hängt von der ausgewählten Option Bilder überschreiben ab. Diese Optionen geben an, wie Ersatzbilder hochgeladen werden: ob sie die Originalbilder ersetzen oder zu duplizierten Bildern werden. Doppelte Bilder werden mit einer `-1`. Beispiel: `chair.tif` wird umbenannt `chair-1.tif`. Diese Optionen wirken sich auf Bilder aus, die in einen anderen Ordner als das Original hochgeladen wurden, oder auf Bilder mit einer anderen Dateinamenerweiterung als das Original, z. B. JPG, TIF oder PNG.

   | Option &quot;Bilder überschreiben&quot; | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Im akt. Ordner Assets mit ident. Namen und ident. Erweiterung überschreiben]** | Nur für neue Dynamic Media-Konten Standard.<br>Diese Option ist die strengste Ersetzungsregel. Das Ersatzbild muss in den Ordner des Originalbilds hochgeladen werden und dieselbe Dateierweiterung haben wie das Originalbild. Wenn diese Voraussetzungen nicht erfüllt sind, wird ein Duplikat erstellt. |
   | **[!UICONTROL Im akt. Ordner Assets mit ident. Namen unabh. von Erweiterung überschreiben]** | Erfordert das Hochladen des Ersatzbilds in denselben Ordner wie das Originalbild, die Dateinamenerweiterung kann jedoch vom Original abweichen. Beispielsweise ersetzt &quot;chair.tif&quot;die Datei &quot;chair.jpg&quot;. |
   | **[!UICONTROL In belieb. Ordner Assets mit ident. Namen und ident. Erweit. überschreiben]** | Setzt voraus, dass das Ersatzbild dieselbe Dateierweiterung wie das Originalbild hat (beispielsweise muss chair.jpg die Datei &quot;chair.jpg&quot;ersetzen, nicht jedoch die Datei &quot;chair.tif&quot;). Sie können das Ersatzbild jedoch in einen anderen Ordner hochladen als den, in dem sich das Original befindet. Das hochgeladene Bild bleibt dann im neuen Ordner; die Datei befindet sich also nicht mehr am ursprünglichen Speicherort.. |
   | **[!UICONTROL In belieb. Ordner Assets mit ident. Namen unabh. von Erweit. überschreiben]** | Diese Option ist die am wenigsten einschränkende Ersetzungsregel. Sie können ein Ersatzbild in einen anderen Ordner hochladen als den, in dem sich das Originalbild befindet, und eine Datei mit einer anderen Dateierweiterung verwenden, um die Originaldatei zu ersetzen. Wenn sich die Originaldatei in einem anderen Ordner befindet, bleibt das Ersatzbild in dem neuen Ordner, in den es hochgeladen wurde. |

* **[!UICONTROL Zuschnitt beibehalten]**

   Steuert die Beibehaltung vorhandener manueller Zuschnittdefinitionen.

   Siehe auch `preserveCrop` in [UploadPostJob](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-upload-post-job.html) und [ReprocessAssetsJob](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-reprocess-assets-job.html), beide im Dynamic Media Viewer-Referenzhandbuch.

## Standardmäßige Upload-Optionen {#default-upload-options}

### Registerkarte &quot;Bildbearbeitung&quot; {#image-editing-tab}

Mit diesem Filter können Sie einen Scharfzeichnungsfiltereffekt für das endgültige heruntergesampelte Bild optimieren. Auf diese Weise können Sie die Intensität des Effekts, den Radius des Effekts (gemessen in Pixel) und einen Schwellenwert für den ignorierten Kontrast steuern.

Der Effekt &quot;Unschärfemaske&quot;verwendet dieselben Optionen wie der Filter &quot;Unschärfemaske&quot;von Photoshop. Im Gegensatz zu dem, was der Name besagt, ist die Unschärfemaske ein Scharfzeichnungsfilter.

| Optionen für Unschärfemaske | Beschreibung |
| --- | --- |
| **[!UICONTROL Stärke]** | Erforderlich.<br>Steuert den auf die Kantenpixel angewendeten Kontrastwert.<br>Betrachten Sie diese Unteroption als Intensität des Effekts. Der Hauptunterschied zwischen den Zahlenwerten von &quot;Unschärfemaske&quot;in Adobe Dynamic Media und den Zahlenwerten in Adobe Photoshop besteht darin, dass der Betrag in Photoshop zwischen 1 % und 500 % liegt. In Adobe Dynamic Media ist der Wertebereich dagegen `0.0` nach `5.0`. Der Wert von 5,0 in Adobe Dynamic Media entspricht ungefähr 500 % in Photoshop. Ein Wert von 0,9 entspricht 90 % usw. |
| **[!UICONTROL Radius]** | Erforderlich.<br>Steuert den Radius des Effekts.<br>Der Wertebereich ist `0` nach `250`. Der Effekt wird auf alle Pixel in einem Bild angewendet und verbreitet sich in alle Richtungen. Der Radius wird in Pixel gemessen. Um beispielsweise einen ähnlichen Scharfzeichnungseffekt für ein Bild mit 2000 x 2000 Pixel und ein Bild mit 500 x 500 Pixel zu erhalten, legen Sie einen Radius von zwei Pixel auf dem Bild mit 2000 x 2000 Pixel fest. Legen Sie dann einen Radius-Wert von einem Pixel auf dem 500 x 500 Pixelbild fest. Ein größerer Wert wird für ein Bild mit mehr Pixel verwendet. |
| **[!UICONTROL Schwelle]** | Erforderlich.<br>Beschreibt den Kontrastbereich, der beim Anwenden der Unschärfemaske ignoriert wird. Dieser Effekt ist wichtig, damit bei Verwendung dieses Filters kein Bildrauschen entsteht. Der Wertebereich ist `0` - `255`: Anzahl der Helligkeitsschritte in einem Graustufenbild. `0` = Schwarz,  = 50 % Grau und  = Weiß.`128``255`<br>Ein Schwellenwert von `12` ignoriert leichte Variationen der Hauttonhelligkeit, um Rauschen zu vermeiden, fügt aber trotzdem Kantenkontrast zu kontrastreichen Bereichen hinzu, z. B. wo Wimpern auf die Haut treffen.<br>Wenn Sie ein Foto von jemandes Gesicht haben, wirkt sich die Unschärfemaske auf die kontrastreichen Teile des Bildes aus. Zum Beispiel, wo Wimpern und Haut treffen, um einen offensichtlichen Kontrastbereich zu schaffen, und die glatte Haut selbst. Selbst die glatteste Haut weist geringfügige Änderungen der Helligkeitswerte auf. Wenn Sie keinen Schwellenwert verwenden, akzentuiert der Filter diese geringfügigen Änderungen in den Hautpixel. Dadurch entsteht ein verrauschter und unerwünschter Effekt, während der Kontrast an den Wimpern verstärkt und die Schärfe intensiviert wird.<br>Zur Vermeidung dieses Problems wird ein Schwellenwert verwendet, der den Filter anweist, die Pixel zu ignorieren, die den Kontrast nicht wesentlich ändern, beispielsweise bei glatter Haut.<br>Beachten Sie in der weiter oben gezeigten Reißverschlussgrafik die Textur neben dem Reißverschluss. Hier ist Bildrauschen erkennbar, weil die Schwellenwerte zu niedrig waren, als dass sie das Bildrauschen unterdrücken könnten. |
| **[!UICONTROL Monochrom]** | Wählen Sie diese Option aus, um die Unschärfemaske auf die Bildhelligkeit anzuwenden (Intensität).<br>Deaktivieren Sie diese Unteroption, um die Unschärfemaske auf jede Farbkomponente einzeln anzuwenden. |

Siehe auch [Scharfzeichnen von Bildern in Adobe Dynamic Media und Image Server](/help/assets/assets/sharpening_images.pdf).

### PostScript-Registerkarte {#postscript-tab}

Sie können Adobe PostScript®-Dateien rastern, transparente Hintergründe beibehalten, eine Auflösung wählen und einen Farbraum auswählen.

Sie können Adobe PostScript®-Dateien (EPS) in Adobe Dynamic Media verwenden. Adobe Dynamic Media bietet Befehle zum Konfigurieren dieser Dateien beim Hochladen.

Wenn Sie PostScript (EPS)-Bilddateien hochladen, können Sie diese auf verschiedene Arten formatieren. Sie können die Dateien rastern, den transparenten Hintergrund beibehalten sowie eine Auflösung und einen Farbraum auswählen.

| PostScript-Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Verarbeitung]** | Wählen Sie Rastern, um Vektorgrafiken in der Datei in das Bitmap-Format zu konvertieren. |
| **[!UICONTROL Transparenten Hintergrund in gerenderten Bildern beibehalten]** | Behält die Hintergrundtransparenz der Datei bei. |
| **[!UICONTROL Auflösung (Pixel/Zoll)]** | Zur Einstellung der Auflösung. Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der Datei angezeigt werden. |
| **[!UICONTROL Farbraum]** | ・ **[!UICONTROL Automatisch erkennen]** - Behält den Farbraum der Datei bei.<br>・ **[!UICONTROL Immer RGB]** - Konvertiert in den RGB-Farbraum.<br>・ **[!UICONTROL Immer CMYK]** - Konvertiert in den CMYK-Farbraum.<br>・ **[!UICONTROL Immer Graustufen]** - Konvertiert in den Graustufen-Farbraum. |

### Photoshop-Registerkarte {#photoshop-tab}

Sie können Vorlagen aus Adobe® Photoshop®-Dateien erstellen, Ebenen beibehalten, Ebenennamen angeben, Text extrahieren und angeben, wie Bilder in Vorlagen verankert sind.

| Photoshop-Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Ebenen beibehalten]** | Teilt die Ebenen in der PSD-Datei ggf. in einzelne Assets auf. Die Asset-Ebenen bleiben der PSD-Datei zugeordnet. Sie können sie anzeigen, indem Sie die PSD-Datei in der Detailansicht öffnen und das Ebenenbedienfeld auswählen. Siehe Anzeigen und Bearbeiten von Ebenen in einer PSD-Datei . |
| **[!UICONTROL Vorlage erstellen]** | Erstellt eine Vorlage aus den Ebenen der PSD-Datei. |
| **[!UICONTROL Text extrahieren]** | Extrahiert den Text, damit Benutzer im Viewer den Text durchsuchen können. |
| **[!UICONTROL Ebenen auf Hintergrundgröße ausdehnen]** | Erweitert die Größe aufgeteilter Bildebenen auf die Größe der Hintergrundebene. |
| **[!UICONTROL Ebenenbenennung]** | Erweitert die Größe aufgeteilter Bildebenen auf die Größe der Hintergrundebene.<br>・ **[!UICONTROL Ebenenname]** - Benennt die Bilder nach ihren Ebenennamen in der PSD-Datei. Wenn eine Ebene in der Original-PSD-Datei beispielsweise „Preisschild“ heißt, wird auch das zugehörige Bild „Preisschild“ genannt. Wenn es sich bei den Ebenennamen in der PSD-Datei jedoch um standardmäßige Photoshop-Ebenennamen handelt (Hintergrund, Ebene 1, Ebene 2 usw.), werden die Bilder nach ihren Ebenennummern in der PSD-Datei benannt. <br>・ **[!UICONTROL Photoshop und Ebenennummer]** - Benennt die Bilder nach ihren Ebenennummern in der PSD-Datei, wobei die ursprünglichen Ebenennamen ignoriert werden. Bilder werden mit dem Photoshop-Dateinamen und einer angefügten Ebenennummer benannt. Beispielsweise die zweite Ebene einer Datei mit dem Namen `Spring Ad.psd` heißt `Spring Ad_2` auch wenn es in Photoshop einen nicht standardmäßigen Namen hatte.<br>・ **[!UICONTROL Photoshop und Ebenenname]** - Benennt die Bilder nach der PSD-Datei, gefolgt vom Ebenennamen oder der Ebenennummer. Die Ebenennummer wird verwendet, wenn es sich bei den Ebenennamen in der PSD-Datei um standardmäßige Photoshop-Ebenennamen handelt. Beispiel: eine Ebene mit dem Namen `Price Tag` in einer PSD-Datei mit dem Namen `SpringAd` heißt `Spring Ad_Price Tag`. Eine Ebene mit dem Standardnamen Ebene 2 wird als `Spring Ad_2`. |
| **[!UICONTROL Anker]** | Geben Sie an, wie Bilder in Vorlagen, die aus der Zusammenstellung der Ebenen aus der PSD-Datei erstellt werden, verankert werden. Der Anker ist standardmäßig zentriert. Ein zentrierter Anker eignet sich am besten zum Auffüllen desselben Raums mit Ersatzbildern, unabhängig vom Seitenverhältnis der Ersatzbilder. Bilder mit einem anderen Seitenverhältnis, die dieses Bild ersetzen, nehmen effektiv denselben Raum ein, wenn auf die Vorlage verwiesen und die Parameterersetzung durchgeführt wird. Wählen Sie eine andere Einstellung, wenn es für Ihre Anwendung erforderlich ist, dass die Ersatzbilder den zugeordneten Raum in der Vorlage ausfüllen. |

### PDF-Tab {#pdf-tab}

Sie können die Dateien rastern, Suchbegriffe und Links extrahieren, die Auflösung festlegen und einen Farbraum auswählen.

| PDF-Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Verarbeitung]** | ・ **[!UICONTROL Keines]** - Die PDF wird nicht verarbeitet.<br>・ **[!UICONTROL Miniatur]** - Rippt jede Seite in der PDF-Datei und konvertiert sie in ein Miniaturbild.<br> ・ **[!UICONTROL Rastern]** - Rippt die Seiten in der PDF-Datei und konvertiert Vektorgrafiken in Bitmapbilder. Wählen Sie diese Option, um einen eCatalog zu erstellen. |
| **[!UICONTROL Extrahieren]** | ・ **[!UICONTROL Keines]** - Es werden keine Suchbegriffe oder Links aus der PDF extrahiert.<br>・ **[!UICONTROL Suchbegriffe]** - Extrahiert Suchbegriffe aus der PDF-Datei, damit die in einem E-Katalog-Viewer nach Schlüsselwörtern durchsucht werden kann.<br>・ **[!UICONTROL Links]** - Extrahiert Links aus den PDF-Dateien und konvertiert sie in Imagemaps, die in einem E-Katalog-Viewer verwendet werden.<br>・ **[!UICONTROL Suchbegriffe und Links]** - Extrahiert Suchbegriffe und Links zur Verwendung in einem E-Katalog-Viewer. |
| **[!UICONTROL Auflösung (Pixel/Zoll)]** | Zum Festlegen der Auflösung: Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der PDF-Datei angezeigt werden. Standard: 150. |
| **[!UICONTROL Farbraum]** | ・ **[!UICONTROL Automatisch erkennen]** - Behält den Farbraum der PDF-Datei bei.<br>・ **[!UICONTROL Immer RGB]** - Konvertiert in den RGB-Farbraum.<br>・ **[!UICONTROL Immer CMYK]** - Konvertiert in den CMYK-Farbraum.<br>・ **[!UICONTROL Immer Graustufen]** - Konvertiert in den Graustufen-Farbraum. |

### Illustrator-Registerkarte {#illustrator-tab}

Sie können Adobe Illustrator®-Dateien rastern, transparente Hintergründe beibehalten sowie eine Auflösung und einen Farbraum auswählen.

Sie können Adobe® Illustrator®-Dateien (AI) in Adobe Dynamic Media verwenden. Adobe Dynamic Media bietet Befehle zum Konfigurieren dieser Dateien beim Hochladen.

Beim Hochladen von Illustrator-Bilddateien (AI) können Sie diese auf verschiedene Arten formatieren. Sie können die Dateien rastern, den transparenten Hintergrund beibehalten sowie eine Auflösung und einen Farbraum auswählen. Optionen zum Formatieren von PostScript- und Illustrator-Dateien sind im Bildschirm &quot;Hochladen&quot;unter &quot;PostScript-Optionen&quot;und &quot;Illustrator-Optionen&quot;im Feld &quot;Upload-Auftragsoptionen&quot;verfügbar.


| Illustrator-Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Verarbeitung]** | Wählen Sie Rastern, um Vektorgrafiken in der Datei in das Bitmap-Format zu konvertieren. |
| **[!UICONTROL Transparenten Hintergrund in gerenderten Bildern beibehalten]** | Behält die Hintergrundtransparenz der Datei bei. |
| **[!UICONTROL Auflösung (Pixel/Zoll)]** | Zur Einstellung der Auflösung. Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der Datei angezeigt werden. |
| **[!UICONTROL Farbraum]** | ・ **[!UICONTROL Automatisch erkennen]** - Behält den Farbraum der Datei bei.<br>・ **[!UICONTROL Immer RGB]** - Konvertiert in den RGB-Farbraum.<br>・ **[!UICONTROL Immer CMYK]** - Konvertiert in den CMYK-Farbraum.<br>・ **[!UICONTROL Immer Graustufen]** - Konvertiert in den Graustufen-Farbraum. |
