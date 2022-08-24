---
title: Konfigurieren allgemeiner Einstellungen für Dynamic Media
description: Erfahren Sie, wie Sie die allgemeinen Einstellungen in Dynamic Media verwalten. Sie können hier den Namen des Veröffentlichungs-Servers und den Namen des Ursprungs-Servers festlegen und eine Option zum Überschreiben von Bildern festlegen. Es gibt auch standardmäßige Upload-Optionen für die Unschärfemaske von Bildern und Upload-Optionen für die Verarbeitung von PostScript-, Adobe Photoshop-, PDF- und Adobe Illustrator-Dateien.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
exl-id: 55cc7c57-87a0-4bfb-b226-36d01d36849a
source-git-commit: 9c548dbc0157607adda5ed76cab8ef970588e1e9
workflow-type: tm+mt
source-wordcount: '2498'
ht-degree: 98%

---

# Konfigurieren allgemeiner Einstellungen für Dynamic Media

Die Option **[!UICONTROL Allgemeine Dynamic Media-Einstellungen]** kann nur konfiguriert werden, wenn Folgendes zutrifft:

* Sie führen Dynamic Media im Scene7-Modus aus. Siehe [Aktivieren von Dynamic Media im Scene7-Modus](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode).
* Sie haben eine *vorhandene* **[!UICONTROL Dynamic Media-Konfiguration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager 6.5.11 oder höher. Weitere Informationen finden Sie unter [Erstellen einer Dynamic Media-Konfiguration in Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
* Sie sind ein Experience Manager-Systemadministrator mit Administratorrechten.

„Allgemeine Dynamic Media-Einstellungen“ richtet sich an erfahrene Website-Entwickler und -Programmierer. Adobe Dynamic Media empfiehlt, dass Benutzer, die diese Veröffentlichungseinstellungen ändern, mit Dynamic Media in Adobe Experience Manager und der grundlegenden Bildverarbeitungstechnologie vertraut sind.

Bei der Kontoerstellung stellt Adobe Dynamic Media automatisch die zugeordneten Server für Ihr Unternehmen bereit. Diese Server werden verwendet, um URL-Zeichenfolgen für Ihre Website und Programme zu erstellen. Diese URL-Aufrufe sind spezifisch für Ihr Konto.

Auf der Seite „Veröffentlichungseinstellungen von Dynamic Media“ werden Standardeinstellungen festgelegt, die festlegen, wie Assets von Adobe Dynamic Media-Servern für Websites oder Programme bereitgestellt werden. Wenn keine Einstellung festgelegt ist, stellt der Adobe Dynamic Media-Server ein Asset gemäß einer Standardeinstellung bereit, die auf der Seite „Veröffentlichungseinstellungen von Dynamic Media“ konfiguriert wurde.

Siehe auch [Optional - Einrichtung und Konfiguration von Dynamic Media - Einstellungen für den Scene7-Modus](/help/assets/config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings) für weitere optionale Konfigurationsaufgaben.

>[!NOTE]
>
>Sie möchten ein Upgrade von Dynamic Media Classic auf Dynamic Media auf Adobe Experience Manager durchführen? Die Seiten „Allgemeine Einstellungen“ und [Veröffentlichungseinstellungen](/help/assets/dm-publish-settings.md) in Dynamic Media werden vorab mit den Werten ausgefüllt, die von Ihrem Dynamic Media Classic-Konto übernommen werden. Die Ausnahmen sind alle Werte, die unter dem Bereich **[!UICONTROL Standardmäßige Upload-Optionen]** auf der Seite „Allgemeine Einstellungen“ angezeigt werden. Diese Werte befinden sich bereits in Experience Manager. Alle Änderungen, die Sie unter **[!UICONTROL Standardmäßige Upload-Optionen]** auf einer der fünf Registerkarten in der Experience Manager-Benutzeroberfläche vornehmen, werden in Dynamic Media, nicht jedoch in Dynamic Media Classic angezeigt. Alle anderen Einstellungen und Werte auf der Seite „Allgemeine Einstellungen“ und der Seite [Veröffentlichungseinstellungen](/help/assets/dm-publish-settings.md) werden von Dynamic Media Classic und Dynamic Media in Experience Manager verwaltet.

**So konfigurieren Sie „Allgemeine Dynamic Media-Einstellungen“:**

1. Klicken Sie im Autorenmodus in Experience Manager auf das Experience Manager-Logo, um auf die Konsole für die globale Navigation zuzugreifen.
1. Wählen Sie in der linken Leiste das Symbol „Tools“ aus und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Allgemeine Dynamic Media-Einstellungen]**.
1. Legen Sie auf der Seite „Server“ Ihre Werte für **[!UICONTROL Veröffentlichungs-Server-Name]** und **[!UICONTROL Ursprungs-Server-Name]** fest und konfigurieren Sie dann auf den fünf Registerkarten die standardmäßigen Upload-Optionen für die Bildbearbeitung sowie für PostScript-, Photoshop-, PDF- und Illustrator-Dateien.

   * [Server](#server-general-setting)
   * [Upload in das Programm](#upload-to-application)
   * Registerkarte [Bildbearbeitung](#image-editing-tab)
   * Registerkarte [PostScript](#postscript-tab)
   * Registerkarte [Photoshop](#photoshop-tab)
   * Registerkarte [PDF](#pdf-tab)
   * Registerkarte [Illustrator](#illustrator-tab)

   Seite ![Allgemeine Dynamic Media-Einstellungen](/help/assets/assets-dm/dm-general-settings.png)
   *Seite „Allgemeine Dynamic Media-Einstellungen“, auf der die Registerkarte **[!UICONTROL Bildbearbeitung]**ausgewählt ist.*<br><br>

1. Wenn Sie fertig sind, wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Speichern]** aus.

## Server {#server-general-setting}

Bei der Kontoerstellung stellt Adobe Dynamic Media automatisch die zugeordneten Server für Ihr Unternehmen bereit. Diese Server werden verwendet, um URL-Zeichenfolgen für Ihre Website und Programme zu erstellen. Diese URL-Aufrufe sind spezifisch für Ihr Konto.

| Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Veröffentlichungs-Server-Name]** | Erforderlich.<br>Der Name muss `https://` im Pfad enthalten.<br>Dies ist der Live-CDN-Server (Content Deliver Network), der in allen systemgenerierten URL-Aufrufen verwendet wird, die für Ihr Konto spezifisch sind. Ändern Sie diesen Server-Namen nur, wenn Sie vom technischen Support von Adobe dazu aufgefordert werden. |
| **[!UICONTROL Ursprungs-Server-Name]** | Erforderlich.<br>Dieser Server wird nur für Qualitätssicherungstests verwendet. Ändern Sie diesen Servernamen nur, wenn Sie vom technischen Support von Adobe dazu aufgefordert werden. |

## Upload in das Programm {#upload-to-application}

* **[!UICONTROL Bilder überschreiben]**

   Adobe Dynamic Media lässt zwei Dateien mit denselben Namen nicht zu. Die Adobe Dynamic Media-ID jedes Elements (der Bildname abzüglich der Dateinamenerweiterung) muss eindeutig sein. Aufgrund dieser Regel hat die Option **[!UICONTROL In Programm hochladen]** eine Überschreibungsmöglichkeit. Der genaue Effekt dieser Option hängt von der ausgewählten Option „Bilder überschreiben“ ab. Diese Optionen legen fest, wie die Ersatzbilder hochgeladen werden: ob sie die Originalbilder ersetzen oder als Duplikate angelegt werden. Doppelte Bilder werden mit einem `-1` umbenannt. Beispiel: `chair.tif` wird in `chair-1.tif` umbenannt. Diese Optionen gelten für Bilder, die in einen anderen Ordner als das Original hochgeladen werden, oder Bilder mit einer anderen Dateinamenerweiterung als das Original (z. B. JPG, TIF oder PNG).

   >[!NOTE]
   >
   >Um die Konsistenz mit Experience Manager zu wahren, wählen Sie für „Bilder überschreiben“ die Option **[!UICONTROL Im akt. Ordner Assets mit ident. Namen und ident. Erweiterung überschreiben]**.

   | Option „Bilder überschreiben“ | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Im akt. Ordner Assets mit ident. Namen und ident. Erweiterung überschreiben]** | *Standard* nur für neue Dynamic Media-Konten.<br>Diese Option ist die strengste Ersetzungsregel. Das Ersatzbild muss in den Ordner des Originalbilds hochgeladen werden und dieselbe Dateierweiterung haben wie das Originalbild. Wenn diese Voraussetzungen nicht erfüllt sind, wird ein Duplikat erstellt.<br>*Wählen Sie diese Option aus, um die Konsistenz mit Experience Manager sicherzustellen*. |
   | **[!UICONTROL Im akt. Ordner Assets mit ident. Namen unabh. von Erweiterung überschreiben]** | Erfordert das Hochladen des Ersatzbilds in denselben Ordner wie das Originalbild, die Dateinamenerweiterung kann jedoch vom Original abweichen. Beispielsweise ersetzt „chair.tif“ die Datei „chair.jpg“. |
   | **[!UICONTROL In belieb. Ordner Assets mit ident. Namen und ident. Erweit. überschreiben]** | Setzt voraus, dass das Ersatzbild dieselbe Dateierweiterung wie das Originalbild hat (beispielsweise muss chair.jpg die Datei „chair.jpg“ ersetzen, nicht jedoch die Datei „chair.tif“). Sie können das Ersatzbild jedoch in einen anderen Ordner hochladen als den, in dem sich das Original befindet. Das hochgeladene Bild bleibt dann im neuen Ordner; die Datei befindet sich also nicht mehr am ursprünglichen Speicherort.. |
   | **[!UICONTROL In belieb. Ordner Assets mit ident. Namen unabh. von Erweit. überschreiben]** | Diese Option ist die am wenigsten einschränkende Ersetzungsregel. Sie können ein Ersatzbild in einen anderen Ordner hochladen als den, in dem sich das Originalbild befindet, und eine Datei mit einer anderen Dateierweiterung verwenden, um die Originaldatei zu ersetzen. Wenn sich die Originaldatei in einem anderen Ordner befindet, bleibt das Ersatzbild in dem neuen Ordner, in den es hochgeladen wurde. |

* **[!UICONTROL Zuschnitt beibehalten]**

   Steuert die Beibehaltung vorhandener manueller Zuschnittdefinitionen.

   Siehe auch `preserveCrop` in [UploadPostJob](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-upload-post-job.html?lang=de) und [ReprocessAssetsJob](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-reprocess-assets-job.html?lang=de), beide im Dynamic Media Viewer-Referenzhandbuch.

## Standard-Upload-Optionen {#default-upload-options}

### Registerkarte „Bildbearbeitung“ {#image-editing-tab}

Mit diesem Filter können Sie einen Scharfzeichnungsfiltereffekt für das endgültige, heruntergesampelte Bild fein abstimmen. Auf diese Weise können Sie die Intensität des Effekts, den Radius des Effekts (gemessen in Pixel) und einen Schwellenwert für den ignorierten Kontrast steuern.

Bei dem Effekt „Unscharf maskieren“ werden dieselben Optionen wie im Filter „Unscharf maskieren“ von Photoshop verwendet. Im Gegensatz zu dem, was der Name besagt, ist „Unscharf maskieren“ ein Scharfzeichnungsfilter.

| Optionen für „Unscharf maskieren“ | Beschreibung |
| --- | --- |
| **[!UICONTROL Stärke]** | Erforderlich.<br>Steuert den auf die Kanten-Pixel angewendeten Kontrastwert.<br>Betrachten Sie diese Unteroption als Intensität des Effekts. Der Hauptunterschied zwischen den Werten von „Unscharf maskieren“ in Adobe Dynamic Media und den Werten in Adobe Photoshop ist, dass Adobe Photoshop einen Wertebereich verwendet, der von 1 % bis 500 % reicht. In Adobe Dynamic Media liegt der Wertebereich dagegen zwischen `0.0` und `5.0`. Ein Wert von 5,0 in Adobe Dynamic Media entspricht 500 % in Photoshop. Ein Wert von 0,9 entspricht 90 % usw. |
| **[!UICONTROL Radius]** | Erforderlich.<br>Steuert den Radius des Effekts.<br>Der Wertebereich ist von `0` bis `250`. Der Effekt wird auf alle Pixel in einem Bild angewendet und verbreitet sich in alle Richtungen. Der Radius wird in Pixel gemessen. Um beispielsweise einen ähnlichen Scharfzeichnungseffekt für ein Bild mit 2000 x 2000 Pixel und ein Bild mit 500 x 500 Pixel zu erhalten, legen Sie einen Radius von zwei Pixel auf dem Bild mit 2000 x 2000 Pixel fest. Legen Sie dann einen Radius-Wert von einem Pixel auf dem Bild mit 500 x 500 Pixel fest. Ein größerer Wert wird für ein Bild mit mehr Pixel verwendet. |
| **[!UICONTROL Schwelle]** | Erforderlich.<br>Beschreibt den Kontrastbereich, der beim Anwenden der Unschärfemaske ignoriert wird. Das ist wichtig, damit kein Bildrauschen entsteht, wenn dieser Filter verwendet wird. Der Wertebereich reicht von `0` bis `255`. Diese Werte stehen für die Anzahl der Helligkeitsschritte in einem Graustufenbild. `0`= Schwarz, `128`= 50 % Grau und `255`= Weiß.<br>Zum Beispiel werden bei einem Schwellenwert von `12` geringfügige Abweichungen in der Helligkeit des Hauttons ignoriert, um Bildrauschen zu vermeiden, während der Kantenkontrast in kontrastreichen Bereichen verstärkt wird, wie etwa an Stellen, wo Wimpern auf Haut treffen.<br>Wenn Sie ein Foto von jemandes Gesicht haben, wirkt sich die Unschärfemaske auf die kontrastreichen Teile des Bildes aus. Zum Beispiel, wo Wimpern und Haut sich treffen, was einen offensichtlichen Kontrastbereich schafft, und die glatte Haut selbst. Selbst die glatteste Haut weist geringfügige Änderungen der Helligkeitswerte auf. Wenn Sie keinen Schwellenwert verwenden, akzentuiert der Filter diese geringfügigen Änderungen in den Hautpixel. Dadurch entsteht ein verrauschter und unerwünschter Effekt, während der Kontrast an den Wimpern verstärkt und die Schärfe intensiviert wird.<br>Zur Vermeidung dieses Problems wird ein Schwellenwert verwendet, der den Filter anweist, die Pixel zu ignorieren, die den Kontrast nicht wesentlich ändern, beispielsweise bei glatter Haut.<br>Beachten Sie in der weiter oben gezeigten Reißverschlussgrafik die Textur neben dem Reißverschluss. Hier ist Bildrauschen erkennbar, weil die Schwellenwerte zu niedrig waren, um das Bildrauschen zu unterdrücken. |
| **[!UICONTROL Monochrom]** | Wählen Sie diese Option aus, um die Unschärfemaske auf die Bildhelligkeit (Intensität) anzuwenden.<br>Deaktivieren Sie diese Unteroption, um die Unschärfemaske auf jede Farbkomponente einzeln anzuwenden. |

Siehe auch [Scharfzeichnen von Bildern in Adobe Dynamic Media und Image Server](/help/assets/assets/sharpening_images.pdf).

### Registerkarte „PostScript“ {#postscript-tab}

Sie können Adobe PostScript®-Dateien rastern, transparente Hintergründe beibehalten sowie eine Auflösung und einen Farbraum auswählen.

Sie können Adobe PostScript®-Dateien (EPS) in Adobe Dynamic Media verwenden. Adobe Dynamic Media bietet Befehle zum Konfigurieren dieser Dateien beim Hochladen.

Wenn Sie PostScript (EPS)-Bilddateien hochladen, können Sie diese auf verschiedene Arten formatieren. Sie können die Dateien rastern, den transparenten Hintergrund beibehalten sowie eine Auflösung und einen Farbraum auswählen.

| PostScript-Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Verarbeitung]** | Wählen Sie „Rastern“, um Vektorgrafiken in der Datei in das Bitmap-Format zu konvertieren. |
| **[!UICONTROL Transparenten Hintergrund in gerenderten Bildern beibehalten]** | Zur Beibehaltung der Hintergrundtransparenz der Datei. |
| **[!UICONTROL Auflösung (Pixel/Zoll)]** | Zur Einstellung der Auflösung. Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der Datei angezeigt werden. |
| **[!UICONTROL Farbraum]** | • **[!UICONTROL Automatisch erkennen]**: Behält den Farbraum der Datei bei.<br>• **[!UICONTROL Immer RGB]**: Konvertiert in den RGB-Farbraum.<br>• **[!UICONTROL Immer CMYK]**: Konvertiert in den CMYK-Farbraum.<br>• **[!UICONTROL Immer Graustufen]**: Konvertiert in den Graustufen-Farbraum. |

### Registerkarte „Photoshop“ {#photoshop-tab}

Sie können Vorlagen aus Adobe® Photoshop®-Dateien erstellen, Ebenen beibehalten, Ebenennamen angeben, Text extrahieren und angeben, wie Bilder in Vorlagen verankert werden.

| Option „Photoshop“ | Beschreibung |
| --- | --- |
| **[!UICONTROL Ebenen beibehalten]** | Teilt die Ebenen in der PSD-Datei ggf. in einzelne Assets auf. Die Asset-Ebenen bleiben der PSD-Datei zugeordnet. Sie können sie anzeigen, indem Sie die PSD-Datei in der Detailansicht öffnen und das Ebenenfenster auswählen. Weitere Informationen finden Sie unter „Anzeigen und Bearbeiten von Ebenen in einer PSD-Datei“. |
| **[!UICONTROL Vorlage erstellen]** | Erstellt eine Vorlage aus den Ebenen der PSD-Datei. |
| **[!UICONTROL Text extrahieren]** | Extrahiert den Text, damit Benutzer den Text in einem Viewer suchen können. |
| **[!UICONTROL Ebenen auf Hintergrundgröße ausdehnen]** | Erweitert die Größe aufgeteilter Bildebenen auf die Größe der Hintergrundebene. |
| **[!UICONTROL Ebenenbenennung]** | Erweitert die Größe aufgeteilter Bildebenen auf die Größe der Hintergrundebene.<br>• **[!UICONTROL Ebenenname]**: Benennt die Bilder nach ihren Ebenennamen in der PSD-Datei. Wenn eine Ebene in der Original-PSD-Datei beispielsweise „Preisschild“ heißt, wird auch das zugehörige Bild „Preisschild“ genannt. Wenn es sich bei den Ebenennamen in der PSD-Datei jedoch um standardmäßige Photoshop-Ebenennamen handelt (Hintergrund, Ebene 1, Ebene 2 usw.), werden die Bilder nach den zugehörigen Ebenennummern in der PSD-Datei benannt. <br>• **[!UICONTROL Photoshop und Ebenennummer]**: Benennt die Bilder nach den zugehörigen Ebenennummern in der PSD-Datei, wobei die ursprünglichen Ebenennamen ignoriert werden. Bilder werden mit dem Photoshop-Dateinamen und einer angefügten Ebenennummer benannt. Zum Beispiel erhält die zweite Ebene der Datei `Spring Ad.psd` den Namen `Spring Ad_2`, selbst wenn sie in Photoshop keinen Standardnamen hatte. <br>• **[!UICONTROL Photoshop und Ebenenname]**: Benennt die Bilder nach der PSD-Datei, gefolgt vom Ebenennamen oder der Ebenennummer. Die Ebenennummer wird verwendet, wenn es sich bei den Ebenennamen in der PSD-Datei um standardmäßige Photoshop-Ebenennamen handelt. Beispielsweise erhält eine Ebene namens `Price Tag` in einer PSD-Datei namens `SpringAd` den Namen `Spring Ad_Price Tag`. Eine Ebene mit dem Standardnamen „Ebene 2“ erhält den Namen `Spring Ad_2`. |
| **[!UICONTROL Anker]** | Geben Sie an, wie Bilder in Vorlagen, die aus der Zusammenstellung der Ebenen aus der PSD-Datei erstellt werden, verankert werden. Der Anker ist standardmäßig zentriert. Ein zentrierter Anker eignet sich am besten zum Auffüllen desselben Raums mit Ersatzbildern, unabhängig vom Seitenverhältnis der Ersatzbilder. Bilder mit einem anderen Seitenverhältnis, die dieses Bild ersetzen, nehmen effektiv denselben Raum ein, wenn auf die Vorlage verwiesen und die Parameterersetzung durchgeführt wird. Wählen Sie eine andere Einstellung, wenn es für Ihre Anwendung erforderlich ist, dass die Ersatzbilder den zugeordneten Raum in der Vorlage ausfüllen. |

### Registerkarte „PDF“ {#pdf-tab}

Sie können die Dateien rastern, Suchbegriffe und Links extrahieren, die Auflösung einstellen und einen Farbraum wählen.

| Option „PDF“ | Beschreibung |
| --- | --- |
| **[!UICONTROL Verarbeitung]** | • **[!UICONTROL Keine]**: Die PDF wird nicht verarbeitet.<br>• **[!UICONTROL Miniatur]**: Teilt die PDF-Datei in einzelne Seite auf und konvertiert diese in ein Miniaturbild.<br> • **[!UICONTROL Rastern]**: Teilt die PDF-Datei in einzelne Seiten auf und konvertiert Vektorgrafiken in Bitmap-Bilder. Wählen Sie diese Option, um einen E-Katalog zu erstellen. |
| **[!UICONTROL Extrahieren]** | • **[!UICONTROL Keine]**: Es werden keine Suchbegriffe oder Links aus der PDF-Datei extrahiert.<br>• **[!UICONTROL Suchbegriffe]**: Extrahiert Suchbegriffe aus der PDF-Datei, damit die Datei in einem E-Katalog-Viewer nach einem Schlüsselwort durchsucht werden kann.<br>• **[!UICONTROL Links]**: Extrahiert Links aus den PDF-Dateien und konvertiert die PDF-Dateien in Imagemaps, die in einem E-Katalog-Viewer verwendet werden.<br>• **[!UICONTROL Suchbegriffe und Links]**: Extrahiert Suchbegriffe und Links zur Verwendung in einem E-Katalog-Viewer. |
| **[!UICONTROL Auflösung (Pixel/Zoll)]** | Zum Festlegen der Auflösung: Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der PDF-Datei angezeigt werden. Der Standardwert ist 150. |
| **[!UICONTROL Farbraum]** | • **[!UICONTROL Automatisch erkennen]**: Behält den Farbraum der PDF-Datei bei.<br>• **[!UICONTROL Immer RGB]**: Konvertiert in den RGB-Farbraum.<br>• **[!UICONTROL Immer CMYK]**: Konvertiert in den CMYK-Farbraum.<br>• **[!UICONTROL Immer Graustufen]**: Konvertiert in den Graustufen-Farbraum. |

### Registerkarte „Illustrator“ {#illustrator-tab}

Sie können Adobe Illustrator®-Dateien rastern, transparente Hintergründe beibehalten sowie eine Auflösung und einen Farbraum auswählen.

Sie können Adobe® Illustrator®-Dateien (AI) in Adobe Dynamic Media verwenden. Adobe Dynamic Media bietet Befehle zum Konfigurieren dieser Dateien beim Hochladen.

Wenn Sie Illustrator (AI)-Bilddateien hochladen, können Sie diese auf verschiedene Arten formatieren. Sie können die Dateien rastern, den transparenten Hintergrund beibehalten sowie eine Auflösung und einen Farbraum auswählen. Optionen zum Formatieren von PostScript- und Illustrator-Dateien sind im Bildschirm „Hochladen“ unter „PostScript-Optionen“ und „Illustrator-Optionen“ im Feld „Upload-Auftragsoptionen“ verfügbar.


| Illustrator-Option | Beschreibung |
| --- | --- |
| **[!UICONTROL Verarbeitung]** | Wählen Sie „Rastern“, um Vektorgrafiken in der Datei in das Bitmap-Format zu konvertieren. |
| **[!UICONTROL Transparenten Hintergrund in gerenderten Bildern beibehalten]** | Zur Beibehaltung der Hintergrundtransparenz der Datei. |
| **[!UICONTROL Auflösung (Pixel/Zoll)]** | Zur Einstellung der Auflösung. Mit dieser Einstellung wird bestimmt, wie viele Pixel pro Zoll in der Datei angezeigt werden. |
| **[!UICONTROL Farbraum]** | • **[!UICONTROL Automatisch erkennen]**: Behält den Farbraum der Datei bei.<br>• **[!UICONTROL Immer RGB]**: Konvertiert in den RGB-Farbraum.<br>• **[!UICONTROL Immer CMYK]**: Konvertiert in den CMYK-Farbraum.<br>• **[!UICONTROL Immer Graustufen]**: Konvertiert in den Graustufen-Farbraum. |
