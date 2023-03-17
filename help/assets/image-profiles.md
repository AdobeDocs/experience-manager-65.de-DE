---
title: Dynamic Media-Bildprofile
description: Erstellen Sie Bildprofile, die Einstellungen für Unschärfemasken, smartes Zuschneiden oder smarte Farb-/Bildmuster (oder beides) enthalten, und wenden Sie dann das Profil auf einen Ordner mit Bild-Assets an.
uuid: 9049fab9-d2be-4118-8684-ce58f3c8c16a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: 4f9301db-edf8-480b-886c-b5e8fca5bf5c
feature: Image Profiles
role: User, Admin
exl-id: 67240ad0-1a7c-4e58-a518-1e36d771f1a1
source-git-commit: bbb64f44c80e96bafcd53277f6d753d84acf5189
workflow-type: tm+mt
source-wordcount: '3047'
ht-degree: 79%

---

# Dynamic Media-Bildprofile {#image-profiles}

Wenn Sie Bilder hochladen, können Sie das Bild nach dem Hochladen automatisch zuschneiden, indem Sie ein neues Bildprofil auf den Ordner anwenden.

>[!IMPORTANT]
>
>• Smartes Zuschneiden ist nur im Scene7-Modus von Dynamic Media verfügbar.
• Bildprofile können nicht auf PDF-, animierte GIF- oder INDD-Dateien (Adobe InDesign) angewendet werden.

## Optionen für das Zuschneiden {#crop-options}

Wenn Sie smartes Zuschneiden für Bilder implementieren, empfiehlt Adobe die folgende Best Practice und erzwingt die folgende Beschränkung:

| Begrenzungstyp | Best Practice | Erzwungene Begrenzung |
| --- | --- | --- |
| Anzahl der smarten Zuschnitte pro Bild | 5 | 100 |

Siehe auch [Dynamic Media-Beschränkungen](/help/assets/limitations.md).

<!-- CQDOC-16069 for paragraph directly below -->

Die Koordinaten für das smarte Zuschneiden hängen vom Seitenverhältnis ab. Wenn für die verschiedenen Einstellungen für smartes Zuschneiden in einem Bildprofil das Seitenverhältnis für die hinzugefügten Dimensionen im Bildprofil dasselbe ist, wird dasselbe Seitenverhältnis an Dynamic Media gesendet. Adobe empfiehlt, denselben Zuschneidebereich zu verwenden. Dadurch werden die im Bildprofil verwendeten verschiedenen Abmessungen nicht beeinträchtigt.

Jeder von Ihnen erstellte smarte Zuschnitt erfordert zusätzliche Verarbeitungsschritte. Das Hinzufügen von mehr als fünf Seitenverhältnissen für das smarte Zuschneiden kann beispielsweise zu einer langsamen Aufnahmerate für Assets führen. Es kann auch zu einer erhöhten Belastung der Systeme führen. Da Sie smartes Zuschneiden auf Ordnerebene anwenden können, empfiehlt Adobe, es *nur* in Ordnern anzuwenden, in denen es erforderlich ist.

**Richtlinien zum Definieren von smartem Zuschneiden in einem Bildprofil**
Um die Verwendung von smartem Zuschneiden unter Kontrolle zu halten und die Verarbeitungszeit und Lagerung von Kulturen zu optimieren, empfiehlt Adobe die folgenden Richtlinien und Tipps:

* Vermeiden Sie das Erstellen doppelter smarter Zuschnittprofile mit denselben Breiten- und Höhenwerten.
* Benennen Sie smarte Zuschnitte basierend auf den Zuschnittdimensionen statt auf ihrer Verwendung. Dies hilft bei der Optimierung von Duplikaten, bei denen eine einzelne Dimension auf mehreren Seiten verwendet wird.
* Erstellen Sie je Seite/je Asset-Typ Bildprofile für bestimmte Ordner und Unterordner anstelle eines gemeinsamen Smart-Zuschnittprofils, das auf alle Ordner oder Assets angewendet wird.
* Ein Bildprofil, das Sie auf Unterordner anwenden, überschreibt ein auf den Ordner angewendetes Bildprofil.
* Erstellen Sie seitenweise Bildprofile/Asset-Typ für bestimmte Ordner und Unterordner anstelle eines gemeinsamen Smart-Zuschnitt-Profils, das auf alle Ordner oder Assets angewendet wird.
* Ein Bildprofil, das Sie auf Unterordner anwenden, überschreibt ein Bildprofil, das auf den Ordner angewendet wird.
* Idealerweise sollten Sie pro Bild 10 bis 15 smarte Zuschnitte haben, um das Bildschirmverhältnis und die Verarbeitungszeit zu optimieren.

<!--
* Image assets that are going to have a smart crop applied to them must be a minimum of 50 x 50 pixels or larger. CQDOC-20087
* An Image Profile that contains duplicate smart crop dimensions is not permitted. CQDOC-20087
* Duplicate named Image Profiles that have smart crop options set are not permitted. CQDOC-20087
* Create page-wise/asset type-wise Image Profiles for specific folders and subfolders instead of a common smart crop profile that is applied to all folders or all assets.
* An Image Profile that you apply to subfolders overrides an Image Profile that is applied to the folder.
* Ideally, have 10-15 smart crops per image to optimize for screen ratios and processing time. -->
<!-- * Avoid creating duplicate smart crop profiles that have the same width and height values. 
* Name smart crops based on crop dimensions, not on end usage. Doing so helps to optimize for duplicates where a single dimension is used on multiple pages. -->

Es stehen für das Zuschneiden zwei Optionen zur Auswahl. Sie können auch die Erstellung von Farb- und Bildmustern automatisieren oder einen zugeschnittenen Inhalt über Zielauflösungen hinweg beibehalten.

>[!IMPORTANT]
• Adobe empfiehlt, alle erzeugten Zuschnitte und Farbfelder zu überprüfen, um sicherzustellen, dass sie für Ihre Marke und Ihre Werte angemessen und relevant sind.
• Das CMYK-Bildformat wird beim smarten Zuschneiden nicht unterstützt.

| Option | Wann ist sie einzusetzen? | Beschreibung |
| --- | --- | --- |
| Pixel-Zuschnitt | Nur Massenzuschnitt von Bildern basierend auf Dimensionen. | Um diese Option zu verwenden, wählen Sie aus dem Dropdown-Menü „Zuschnittsoptionen“ **[!UICONTROL Pixelzuschnitt]** aus.<br><br> Um ein Bild an den Seiten zuzuschneiden, geben Sie die Anzahl der Pixel ein, die von einer Seite oder jeder Seite des Bildes abgeschnitten werden sollen. Wieviel von dem Bild abgeschnitten wird, hängt von der ppi-Einstellung (Pixel pro Zoll) in der Bilddatei ab.<br><br>Ein Pixel-Zuschnitt im Bildprofil wird folgendermaßen dargestellt:<br>• Die Werte sind oben, unten, links und rechts.<br>• Der Wert für links ist `0,0`. Von dort aus wird der Pixelzuschnitt berechnet.<br>• Ausgangspunkt des Zuschnitts: links ist X und oben ist Y<br>• Horizontale Berechnung: horizontale Pixel-Größe des Originalbilds abzüglich links und dann abzüglich rechts.<br>• Vertikale Berechnung: Die vertikale Pixel-Höhe abzüglich des Werts für oben und dann abzüglich des Werts für unten.<br><br>Beispiel: Sie haben ein Bild in der Größe 4000 x 3000 Pixel. Sie verwenden folgende Werte: Oben = 250, Unten = 500, Links = 300, Rechts = 700.<br><br>Schneiden Sie von oben links (300, 250) aus mit dem Füllraum (4000-300-700, 3000-250-500 oder 3000,2250). |
| Smartes Zuschneiden | Massenzuschnitt von Bildern basierend auf ihrem visuellen Fokus. | Smartes Zuschneiden nutzt die Leistungsfähigkeit der künstlichen Intelligenz in Adobe Sensei, um das Zuschneiden von Bildern in großen Mengen schnell zu automatisieren. Smartes Zuschneiden erkennt und schneidet den Fokus in jedem Bild automatisch ab, um den vorgesehenen Zielpunkt unabhängig von der Bildschirmgröße zu erfassen.</p> <p>Um smartes Zuschneiden zu verwenden, wählen Sie aus der Dropdown-Liste „Zuschnittsoptionen“ die Option **[!UICONTROL Smartes Zuschneiden]** aus und aktivieren Sie „Responsive Bildbeschneidung“.</p> <p>Die standardmäßigen Breakpoint-Größen &quot;Groß&quot;, &quot;Mittel&quot;und &quot;Klein&quot;decken im Allgemeinen alle Größen ab, die die meisten Bilder auf Mobilgeräten, Tablets, Desktops und Bannern verwenden. Sie können die Standardnamen „Groß“, „Mittel“ und „Klein“ beliebig anpassen.</p> <p>Um weitere Breakpoints hinzuzufügen, wählen Sie **[!UICONTROL Zuschnitt hinzufügen]** aus. Wenn Sie einen Zuschnitt löschen möchten, klicken Sie auf das Papierkorb-Symbol. |
| Farb- und Bildmuster | Massenweise Erstellung von Bildmustern für die einzelnen Bilder. | **Hinweis:** Smarte Muster werden in Dynamic Media Classic nicht unterstützt.<br><br>Erkennen und generieren Sie automatisch hochwertige Bildmuster aus Produktbildern, die Farbe oder Textur zeigen.<br><br>Um Farb- und Bildmuster zu verwenden, wählen Sie aus der Dropdown-Liste „Zuschnittsoptionen“ **[!UICONTROL Smartes Zuschneiden]** aus und aktivieren Sie die Funktion „Farb- und Bildmuster“. Geben Sie in die Textfelder Breite und Höhe einen Wert in Pixel ein.<br><br>Zwar sind alle Bildzuschnitte über die Leiste „Ausgabedarstellungen“ verfügbar, jedoch können Farbfelder nur über die Funktion „URL kopieren“ verwendet werden. Verwenden Sie Ihre eigene Ansichtskomponente, um den Musterabschnitt „Farbfeld“ auf Ihrer Site zu rendern. (Hiervon ausgenommen sind Karussellbanner. Dynamic Media bietet die Anzeigekomponente für in entsprechenden Bannern verwendete Farb-/Bildmuster.)<br><br>**Verwenden von Bildmustern**<br> Die URL für Bildmuster ist unkompliziert. Sie setzt sich wie folgt zusammen: <br><br>`/is/image/company/&lt;asset_name&gt;:Swatch`<br>, wobei `:Swatch` an die Asset-Anfrage angehängt wird.<br><br>**Verwenden von Farbmustern**<br> Um Farbmuster zu verwenden, erstellen Sie eine Anfrage `req=userdata` mit folgendem Inhalt:<br>`/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata`<br><br>Folgendes ist beispielsweise ein Farbmuster-Asset in Dynamic Media Classic:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch`<br>Hier finden Sie die zugehörige `req=userdata`-URL zum Farbmuster-Asset:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata`<br><br>Die Antwort von `req=userdata` lautet wie folgt:<br>`SmartCropDef=Swatch SmartCropHeight=200.0`<br>`SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200`<br>`SmartCropType=Swatch`<br>`SmartCropWidth=200.0`<br>`SmartSwatchColor=0xA56DB2`<br><br>Sie können auch eine Antwort von `req=userdata` im XML- oder JSON-Format anfordern wie in den folgenden URL-Beispielen gezeigt:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,json`<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml`<br><br>**Hinweis**: Sie müssen Ihre eigene WCM-Komponente erstellen, um ein Farbmuster anzufordern, und das Attribut `SmartSwatchColor` auswerten, das durch einen 24-Bit-RGB-Hexadezimalwert dargestellt wird.<br><br>Siehe auch [`userdata` im Viewer-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/req/r-userdata.html?lang=de). |

## Unschärfemaske {#unsharp-mask}

Mit **[!UICONTROL Unscharf maskieren]** können Sie einen Scharfzeichnungsfiltereffekt für das endgültige heruntergesampelte Bild optimieren. Sie können die Intensität des Effekts, den Radius des Effekts (gemessen in Pixel) und einen Schwellenwert für den Kontrast festlegen, der ignoriert werden soll. Bei diesem Effekt werden dieselben Optionen wie bei Adobe Photoshop verwendet *Unschärfemaske* Filter.

>[!NOTE]
Die Unschärfemaske wird nur auf herunterskalierte Ausgabedarstellungen im PTIFF (Pyramiden-TIFF) angewendet, die mehr als 50 % heruntergesampelt sind. Daher werden die größten Ausgabedarstellungen im PTIFF nicht durch die Unschärfemaske beeinflusst. Demgegenüber werden kleinere Ausgabedarstellungen wie Miniaturansichten geändert (dabei wird die Unschärfemaske angezeigt).

In **[!UICONTROL Unschärfemaske]** sind die folgenden Filteroptionen verfügbar:

| Option | Beschreibung |
| --- | --- |
| Stärke | Steuert den auf Kantenpixel angewendeten Kontrastwert. Der Standardwert ist 1,75. Bei hochauflösenden Bildern können Sie ihn auf bis zu 5 erhöhen. Stellen Sie sich den Betrag als ein Maß für die Filterintensität vor. Bereich: 0-5. |
| Radius | Bestimmt die Anzahl der Pixel um die Kantenpixel, auf die sich die Scharfzeichnung auswirkt. Bei hochauflösenden Bildern geben Sie einen Wert zwischen 1 und 2 ein. Bei einem niedrigen Wert werden lediglich die Kantenpixel scharfgezeichnet, bei einem hohen Wert werden mehr Pixel scharfgezeichnet. Der korrekte Wert hängt von der Bildgröße ab. Der Standardwert ist 0,2. Bereich ist 0-250. |
| Schwelle | Bestimmt den Kontrastbereich, der bei Anwendung des Filters &quot;Unschärfemaske&quot;ignoriert werden soll. Mit anderen Worten: Diese Option bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel betrachtet und scharfgezeichnet werden. Um Rauschen zu vermeiden, experimentieren Sie mit Werten zwischen 0 und 255. |

Das Scharfzeichnen wird unter [Scharfzeichnen von Bildern](/help/assets/assets/sharpening_images.pdf) beschrieben.

## Erstellen von Dynamic Media-Bildprofilen {#creating-image-profiles}

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dms7.md#configuring-asset-processing).

Siehe [Profile für die Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md).

Informationen hierzu finden Sie auch im Thema über die [Best Practices für die Organisation Ihrer digitalen Assets zur Verwendung von Verarbeitungsprofilen](/help/assets/organize-assets.md).

**So erstellen Sie Bildprofile für Dynamic Media:**

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Auswählen **[!UICONTROL Erstellen]** , sodass Sie ein Bildprofil hinzufügen können.
1. Geben Sie einen Profilnamen und Werte für Unschärfemasken, Zuschneiden oder Farb-/Bildmuster (oder beides) an.

   Verwenden Sie einen für den Verwendungszweck spezifischen Profilnamen. Wenn Sie beispielsweise ein Profil erstellen, das nur Farb-/Bildmuster generiert – bei dem also smartes Zuschneiden deaktiviert und „Farb-/Bildmuster“ aktiviert ist –, können Sie das Profil „Smarte Farb-/Bildmuster“ nennen.

   Siehe auch Optionen für [Smartes Zuschneiden und smarte Farb-/Bildmuster](#crop-options) sowie [Unscharf maskieren](#unsharp-mask).

   ![Zuschneiden](assets/crop.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus. Das neu erstellte Profil wird in der Liste der verfügbaren Profile angezeigt.

## Bearbeiten oder Erstellen von Dynamic Media-Bildprofilen {#editing-or-deleting-image-profiles}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie das Bildprofil aus, das Sie bearbeiten oder entfernen möchten. Wählen Sie **[!UICONTROL Bildverarbeitungsprofil bearbeiten]** aus, um es zu bearbeiten. Wählen Sie **[!UICONTROL Bildverarbeitungsprofil löschen]** aus, um es zu entfernen.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Speichern Sie die Änderungen bei der Bearbeitung. Bestätigen Sie beim Löschen, dass Sie das Profil entfernen möchten.

## Anwenden eines Dynamic Media-Bildprofils auf Ordner {#applying-an-image-profile-to-folders}

Wenn Sie ein Bildprofil einem Ordner zuweisen, übernehmen automatisch alle Unterordner das Profil vom übergeordneten Ordner. Dieser Workflow bedeutet, dass Sie einem Ordner nur ein Bildprofil zuweisen können. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Bildprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen wurde, werden in der Benutzeroberfläche mit dem Namen des Profils angegeben, der in der Karte angezeigt wird.

<!-- When you add smart crop to an existing Image Profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

Sie können Bildprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Bildprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

### Anwenden von Dynamic Media-Bildprofilen auf bestimmte Ordner {#applying-image-profiles-to-specific-folders}

Sie können im Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** ein Bildprofil auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Bildprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

#### Anwenden von Dynamic Media-Bildprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie ein Bildprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Wählen Sie **[!UICONTROL Profil auf Ordner anwenden]** und mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Wählen Sie dann **[!UICONTROL Anwenden]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Dynamic Media-Bildprofilen auf Ordner über „Eigenschaften“ {#applying-image-profiles-to-folders-from-properties}

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]**. Navigieren Sie dann zum übergeordneten Ordner des Ordners, auf den Sie ein Bildprofil anwenden möchten.
1. Klicken Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und klicken Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Bildprofile]** aus. Wählen Sie in der Dropdown-Liste **[!UICONTROL Profilname]** das gewünschte Profil und dann **[!UICONTROL Speichern und schließen]** aus. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Globales Anwenden eines Dynamic Media-Bildprofils {#applying-an-image-profile-globally}

Profile können nicht nur auf einzelne Ordner, sondern auch global angewendet werden. Dann wird allen Inhalten, die Sie in Adobe Experience Manager Assets in beliebigen Ordnern hochladen, das ausgewählte Profil zugeordnet.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

**So wenden Sie ein Dynamic Media-Bildprofil global an:**

1. Führen Sie einen der folgenden Schritte aus:

   * Navigieren Sie zu `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und wenden Sie das entsprechende Profil an und wählen Sie **[!UICONTROL Speichern]** aus.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navigieren Sie in CRXDE Lite zum folgenden Knoten: `/content/dam/jcr:content`.

      Fügen Sie die Eigenschaft `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` hinzu und wählen Sie **[!UICONTROL Alle speichern]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern eines einzelnen Bildes {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!IMPORTANT]
• Smartes Zuschneiden ist nur im Scene7-Modus von Dynamic Media verfügbar.

Sie können das smarte Zuschnittsfenster eines Bildes manuell neu ausrichten oder seine Größe ändern, um den Fokus weiter zu verfeinern.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

Siehe auch [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**So bearbeiten Sie smarte Zuschnitte oder smarte Farb-/Bildmuster eines einzelnen Bildes:**

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, auf den das Bildprofil „Smartes Zuschneiden“ oder „Smartes Farb-/Bildmuster“ angewendet wurde.

1. Wählen Sie den Ordner aus, damit Sie den Inhalt öffnen können.
1. Wählen Sie das Bild aus, dessen smartes Zuschneiden oder smartes Farb-/Bildmuster Sie anpassen möchten.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Smartes Zuschneiden]** aus.

1. Führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie den Schieberegler in der rechten oberen Ecke der Seite nach links oder rechts, um die Bildanzeige zu erhöhen bzw. zu verringern.
   * Ziehen Sie auf das Bild einen Eckpunkt, um die Größe des sichtbaren Bereichs des Zuschnitts oder Farb-/Bildmusters anzupassen.
   * Ziehen Sie das Feld/Muster auf dem Bild an eine neue Position. Sie können nur Bildmuster bearbeiten. Farbmuster sind statisch.
   * Wählen Sie über dem Bild **[!UICONTROL Wiederherstellen]** aus, um all Ihre Änderungen rückgängig zu machen und den ursprünglichen Zuschnitt bzw. das Farb-/Bildmuster wiederherzustellen.

1. Wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Speichern]** und anschließend **[!UICONTROL Schließen]** aus, um zum Asset-Ordner zurückzukehren.

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

>[!IMPORTANT]
• Smartes Zuschneiden ist nur im Scene7-Modus von Dynamic Media verfügbar.

Nachdem Sie ein Bildprofil (mit der Funktion „Smartes Zuschneiden“) auf einen Ordner angewendet haben, wird der Zuschnitt auf alle Bilder in diesem Ordner angewendet. Sie können das Zuschnittsfenster in mehreren Bildern *manuell* neu ausrichten oder die Größe verändern, um den Fokus präziser zu bestimmen.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

**So bearbeiten Sie smarte Zuschnitte oder smarte Farb-/Bildmuster mehrerer Bilder:**

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu einem Ordner, auf den das Bildprofil „Smartes Zuschneiden“ oder „Smartes Farb-/Bildmuster“ angewendet wurde.
1. Wählen Sie beim entsprechenden Ordner das Symbol **[!UICONTROL Mehr Aktionen]** (...) und anschließend **[!UICONTROL Smartes Zuschneiden]** aus.

1. Führen Sie auf der Seite **[!UICONTROL Smartes Zuschneiden bearbeiten]** eine der folgenden Aktionen durch:

   * Passen Sie die Anzeigegröße von Bildern auf der Seite an.

      Ziehen Sie den Schieberegler rechts neben der Dropdown-Liste mit Breakpoint-Namen nach links oder rechts, um den sichtbaren Bildbereich anzupassen.

      ![edit_smart_products-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtern Sie die Liste der sichtbaren Bilder anhand von Breakpoint-Namen. Im folgenden Beispiel werden die Bilder nach dem Breakpoint-Namen &quot;Medium&quot;gefiltert.

      Wählen Sie aus der Dropdown-Liste in der oberen rechten Ecke der Seite einen Breakpoint-Namen aus, um zu filtern, welche Bilder Ihnen angezeigt werden. (Siehe Abbildung oben.)

      ![edit_smart_products-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Ändern Sie die Größe des smarten Zuschnittrahmens. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie auf dem Bild den Eckpunkt des Zuschnittrahmens, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen.
      * Wenn das Bild sowohl über ein smartes Zuschneiden als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie auf dem Bild den Eckpunkt des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen. Oder wählen Sie das smarte Bildmuster unter dem Bild (Farbmuster sind statisch) aus und ziehen Sie die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Bildmusters anzupassen.

      ![Größenänderung des smarten Zuschnitts eines Bildes](assets/edit_smart_crops-resize.png)

   * Verschieben Sie das smarte Zuschnittsfeld. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Zuschnittsfeld auf das Bild an eine neue Position.
      * Wenn das Bild sowohl über ein smartes Zuschneiden als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Feld für das smarte Zuschneiden auf das Bild an eine neue Position. Oder wählen Sie unter dem Bild das smarte Bildmuster (Farbmuster sind statisch) aus und ziehen Sie das smarte Zuschnittsfeld an eine neue Position.

      ![edit_smart_cards-move](assets/edit_smart_crops-move.png)

   * Machen Sie all Ihre Änderungen rückgängig und stellen Sie den ursprünglichen smarten Zuschnitt bzw. das smarte Farb-/Bildmuster wieder her (gilt nur für die aktuelle Bearbeitungssitzung).

      Wählen Sie über dem Bild **[!UICONTROL Wiederherstellen]** aus.

      ![edit_smart_cards-revert](assets/edit_smart_crops-revert.png)



1. Wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Speichern]** und anschließend **[!UICONTROL Schließen]** aus, um zum Asset-Ordner zurückzukehren.

## Entfernen eines Dynamic Media-Bildprofils aus Ordnern {#removing-an-image-profile-from-folders}

Wenn Sie ein Bildprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

Sie können im Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** ein Bildprofil aus einem Ordner entfernen. In diesem Abschnitt werden die beiden Möglichkeiten beschrieben, wie Sie Bildprofile aus Ordnern entfernen können.

### Entfernen von Dynamic Media-Bildprofilen aus Ordnern über die Benutzeroberfläche „Profile“ {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie ein Bildprofil aus, das Sie aus einem Ordner oder mehreren Ordnern entfernen möchten.
1. Wählen Sie **[!UICONTROL Verarbeitungsprofil aus Ordner(n) entfernen]** und anschließend einen oder mehrere Ordner aus, aus denen das Profil entfernt werden soll. Wählen Sie dann **[!UICONTROL Entfernen]** aus.

   Sie können überprüfen, ob das Bildprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Dynamic Media-Bildprofilen aus Ordnern über „Eigenschaften“ {#removing-image-profiles-from-folders-via-properties}

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, aus dem Sie ein Bildprofil entfernen möchten.
1. Wählen Sie beim entsprechenden Ordner das Häkchen aus, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Bildprofile]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Profilname]** die Option **[!UICONTROL Kein]** und dann **[!UICONTROL Speichern und schließen]** aus.

   Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.
