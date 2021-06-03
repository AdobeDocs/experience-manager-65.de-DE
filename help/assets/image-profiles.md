---
title: Dynamic Media-Bildprofile
description: Erstellen Sie Bildprofile, die Einstellungen für Unschärfemasken, smartes Zuschneiden oder smarte Farb-/Bildmuster (oder beides) enthalten, und wenden Sie dann das Profil auf einen Ordner mit Bild-Assets an.
uuid: 9049fab9-d2be-4118-8684-ce58f3c8c16a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: 4f9301db-edf8-480b-886c-b5e8fca5bf5c
feature: Bildprofile
role: Business Practitioner, Administrator
exl-id: 67240ad0-1a7c-4e58-a518-1e36d771f1a1
source-git-commit: b1e0ea01688095b29d8fb18baf6fa0bda660dad5
workflow-type: tm+mt
source-wordcount: '2752'
ht-degree: 82%

---

# Bildprofile für Dynamic Media {#image-profiles}

Wenn Sie Bilder hochladen, können Sie das Bild nach dem Hochladen automatisch zuschneiden, indem Sie ein neues Bildprofil auf den Ordner anwenden.

>[!NOTE]
>
>Smartes Zuschneiden ist nur im Scene7-Modus von Dynamic Media verfügbar.

>[!IMPORTANT]
>
>Bildprofile können nicht auf PDF-, animierte GIF- oder INDD-Dateien (Adobe InDesign) angewendet werden.

## Optionen für das Zuschneiden {#crop-options}

<!-- CQDOC-16069 for paragraph directly below -->

Die Koordinaten für das smarte Zuschneiden hängen vom Seitenverhältnis ab. Wenn bei den verschiedenen Einstellungen für das smarte Zuschneiden in einem Bildprofil das Seitenverhältnis für die hinzugefügten Abmessungen im Bildprofil dasselbe ist, wird dasselbe Seitenverhältnis an Dynamic Media gesendet. Adobe empfiehlt, denselben Zuschneidebereich zu verwenden. Dadurch wird sichergestellt, dass es keine Auswirkungen auf verschiedene Dimensionen gibt, die im Bildprofil verwendet werden.

Jeder von Ihnen erstellte smarte Zuschnitt erfordert zusätzliche Verarbeitungsschritte. Das Hinzufügen von mehr als fünf Seitenverhältnissen für das smarte Zuschneiden kann beispielsweise zu einer langsamen Aufnahmerate für Assets führen. Dies führt auch zu einer erhöhten Belastung der Systeme. Da Sie smartes Zuschneiden auf Ordnerebene anwenden können, empfiehlt Adobe, es *nur* in Ordnern anzuwenden, in denen es erforderlich ist.

Es stehen zwei Optionen für das Zuschneiden zur Auswahl. Außerdem können Sie die Erstellung von Farb- und Bildfeldern automatisieren.

<table>
 <tbody>
  <tr>
   <td><strong>Option</strong></td>
   <td><strong>Wann ist sie einzusetzen?</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Pixelzuschnitt</td>
   <td>Nur Massenzuschnitt von Bildern basierend auf Dimensionen.</td>
   <td><p>Um diese Option zu verwenden, wählen Sie aus dem Dropdownmenü „Zuschnittsoptionen“ <strong>Pixelzuschnitt</strong> aus.</p> <p>Um die Seiten eines Bildes zu beschneiden, geben Sie die Anzahl der Pixel ein, die von einer oder von allen Seiten des Bildes abgeschnitten werden sollen. Um wie viel das Bild beschnitten wird, hängt von der ppi-Einstellung (Pixel per Inch; Pixel pro Zoll) in der Bilddatei ab.</p> <p>Ein Bildprofil-Pixelzuschnitt wird wie folgt gerendert:<br /> </p>
    <ul>
     <li>Werte: oben, unten, links und rechts.</li>
     <li>Der Wert für links ist 0,0. Von dort aus wird der Pixelzuschnitt berechnet.</li>
     <li>Startpunkt des Zuschnitts: Links ist X und oben ist Y</li>
     <li>Horizontale Berechnung: Horizontale Pixelabmessungen des Originalbilds abzüglich des Werts für links und dann abzüglich des Werts für rechts.</li>
     <li>Vertikale Berechnung: Die vertikale Pixelhöhe abzüglich des Werts für oben und dann abzüglich des Werts für unten.</li>
    </ul> <p>Beispiel: Sie haben ein Bild in der Größe 4000 x 3000 Pixel. Sie verwenden folgende Werte: Oben = 250, Unten = 500, Links = 300, Rechts = 700.</p> <p>Schneiden Sie von oben links (300, 250) aus mit dem Füllraum (4000-300-700, 3000-250-500 oder 3000,2250).</p> </td>
  </tr>
  <tr>
   <td>Smartes Zuschneiden</td>
   <td>Massenzuschnitt von Bildern basierend auf ihrem visuellen Fokus.</td>
   <td><p>Smartes Zuschneiden nutzt die Möglichkeiten künstlicher Intelligenz in Adobe Sensei, um den Massenzuschnitt von Bildern schnell zu automatisieren. Smartes Zuschneiden erkennt automatisch den Fokus in jedem Bild und schneidet es entsprechend zu, um das Bildmotiv richtig zu erfassen – unabhängig von der Bildschirmgröße.</p> <p>Um smartes Zuschneiden zu verwenden, wählen Sie aus der Dropdown-Liste „Zuschnittsoptionen“ die Option <strong>Smartes Zuschneiden</strong> aus und aktivieren Sie „Responsive Bildbeschneidung“.</p> <p>Die standardmäßigen Breakpoint-Größen für „Groß“, „Mittel“ und „Klein“ decken in der Regel alle Größen ab, in denen Bilder auf Smartphones, Tablets, Computern und in Bannern verwendet werden. Sie können die Standardnamen „Groß“, „Mittel“ und „Klein“ beliebig anpassen.</p> <p>Um weitere Breakpoints hinzuzufügen, klicken Sie auf <strong>Zuschnitt hinzufügen</strong>. Wenn Sie einen Zuschnitt löschen möchten, klicken Sie auf das Papierkorb-Symbol.</p> </td>
  </tr>
  <tr>
   <td>Farb- und Bildmuster</td>
   <td>Massenweise Erstellung von Bildmustern für die einzelnen Bilder.</td>
   <td><p><strong>Hinweis:</strong> Smarte Muster werden in Dynamic Media Classic nicht unterstützt.</p> <p>Erkennen und generieren Sie automatisch hochwertige Bildmuster aus Produktbildern, die Farbe oder Material zeigen.</p> <p>Um Farb- und Bildmuster zu verwenden, wählen Sie aus der Dropdown-Liste „Zuschnittsoptionen“ <strong>Smartes Zuschneiden</strong> aus und aktivieren Sie die Funktion „Farb- und Bildmuster“. Geben Sie in den Feldern „Breite“ und „Höhe“ einen Pixelwert an.</p> <p>Zwar sind alle Bildzuschnitte über die Leiste „Ausgabedarstellungen“ verfügbar, jedoch können Farb- und Bildmuster nur über die Funktion „URL kopieren“ verwendet werden. Verwenden Sie Ihre eigene Ansichtskomponente, um den Musterabschnitt Farbfeld auf Ihrer Site zu rendern. (Hiervon ausgenommen sind Karussellbanner. Dynamic Media bietet die Anzeigekomponente für in entsprechenden Bannern verwendete Farb-/Bildmuster.)</p> <p><strong>Verwendung von Bildmustern</strong></p> <p>Die URL für Bildmuster ist einfach. Es ist:</p> <p><code>/is/image/company/&lt;asset_name&gt;:Swatch</code></p> <p>wobei <code>:Swatch</code> an die Asset-Anfrage angehängt wird.</p> <p><strong>Verwendung von Farbmustern</strong></p> <p>Um Farbmuster zu verwenden, stellen Sie wie folgt eine <code>req=userdata</code>-Anfrage:</p> <p><code>/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata</code></p> <p>Folgendes ist beispielsweise ein Farbmuster-Asset in Dynamic Media Classic:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch</code></p> <p>Die entsprechende <code>req=userdata</code>-URL für das Farbmuster-Asset lautet:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata</code></p> <p>Die <code>req=userdata</code>-Antwort sieht wie folgt aus:</p> <p><code class="code">SmartCropDef=Swatch
       SmartCropHeight=200.0
       SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200
       SmartCropType=Swatch
       SmartCropWidth=200.0
       SmartSwatchColor=0xA56DB2</code></p> <p>Sie können wie in den folgenden URL-Beispielen auch eine <code>req=userdata</code>-Antwort im XML- oder JSON-Format anfordern:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml</code></p><p><code>SmartSwatchColor</code></p><p></p></td></tr></tbody></table>

## Unschärfemaske {#unsharp-mask}

Mit **[!UICONTROL Unscharf maskieren]** können Sie einen Scharfzeichnungsfiltereffekt für das endgültige heruntergesampelte Bild optimieren. Sie können die Intensität des Effekts, den Radius des Effekts (gemessen in Pixel) und einen Schwellenwert für den Kontrast festlegen, der ignoriert werden soll. Dieser Effekt verwendet dieselben Optionen wie der Adobe Photoshop-Filter „Unscharf maskieren“.

>[!NOTE]
>
>Die Unschärfemaske wird nur auf herunterskalierte Ausgabedarstellungen im PTIFF (Pyramiden-TIFF) angewendet, die mehr als 50 % heruntergesampelt sind. Das bedeutet, dass die größten Ausgabedarstellungen im PTIFF nicht von der Unschärfemaske betroffen sind, während kleinere Ausgabedarstellungen wie Miniaturansichten geändert werden (und die Unschärfemaske anzeigen).

In **[!UICONTROL Unschärfemaske]** sind die folgenden Filteroptionen verfügbar:

| Option | Beschreibung |
| --- | --- |
| Stärke | Steuert den auf die Kantenpixel angewendeten Kontrastwert. Der Standardwert ist 1,75. Bei hochauflösenden Bildern können Sie ihn auf bis zu 5 erhöhen. Der Wert dient hierbei als ein Maß für die Filterintensität. Bereich: 0-5. |
| Radius | Bestimmt die Anzahl der Pixel um die Kantenpixel, auf die sich die Scharfzeichnung auswirkt. Bei hochauflösenden Bildern geben Sie einen Wert zwischen 1 und 2 ein. Bei einem niedrigen Wert werden lediglich die Kantenpixel scharfgezeichnet, bei einem hohen Wert werden mehr Pixel scharfgezeichnet. Der korrekte Wert hängt von der Bildgröße ab. Der Standardwert ist 0,2. Bereich: 0-250. |
| Schwelle | Bestimmt den Kontrastbereich, der bei der Anwendung des Filters „Unschärfemaske“ ignoriert werden soll. In anderen Worten: Die Option bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel eingestuft und scharfgezeichnet werden. Um Rauschen zu vermeiden, experimentieren Sie mit Werten zwischen 0 und 255. |

Das Scharfzeichnen wird unter [Scharfzeichnen von Bildern] (/help/assets/assets/sharpening_images.pdf) beschrieben.

## Erstellen von Dynamic Media-Bildprofilen {#creating-image-profiles}

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dms7.md#configuring-asset-processing).

Siehe [Profile für die Verarbeitung von Metadaten, Bildern und Videos](processing-profiles.md).

Informationen hierzu finden Sie auch im Thema über die [Best Practices für die Organisation Ihrer digitalen Assets zur Verwendung von Verarbeitungsprofilen](/help/assets/organize-assets.md).

**So erstellen Sie Dynamic Media-Bildprofile:**

1. Tippen Sie auf das Adobe Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Tippen Sie auf **[!UICONTROL Erstellen]**, damit Sie ein Bildprofil hinzufügen können.
1. Geben Sie einen Profilnamen und Werte für Unschärfemasken, Zuschneiden oder Farb-/Bildmuster (oder beides) an.

   Verwenden Sie einen Profilnamen, der dem vorgesehenen Zweck entspricht. Wenn Sie beispielsweise ein Profil erstellen möchten, das nur Farbmuster generiert - d. h. smartes Zuschneiden ist deaktiviert (deaktiviert) und Farb- und Bildmuster ist aktiviert (aktiviert) -, verwenden Sie den Profilnamen &quot;Smarte Farbmuster&quot;.

   Siehe auch Optionen für [Smartes Zuschneiden und smarte Farb-/Bildmuster](#crop-options) sowie [Unscharf maskieren](#unsharp-mask).

   ![Zuschneiden](assets/crop.png)

1. Tippen Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Profil wird in der Liste der verfügbaren Profile angezeigt.

## Bearbeiten oder Löschen von Bildprofilen für Dynamic Media {#editing-or-deleting-image-profiles}

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie das Bildprofil aus, das Sie bearbeiten oder entfernen möchten. Um sie zu bearbeiten, wählen Sie **[!UICONTROL Bildverarbeitungsprofil bearbeiten]** aus. Wählen Sie **[!UICONTROL Bildverarbeitungsprofil löschen]** aus, um es zu entfernen.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Wenn Sie das Profil bearbeitet haben, speichern Sie die Änderungen. Wenn Sie das Profil löschen, bestätigen Sie, dass Sie es entfernen möchten.

## Anwenden eines Bildprofils für Dynamic Media auf Ordner {#applying-an-image-profile-to-folders}

Wenn Sie ein Bildprofil einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Dieser Workflow bedeutet, dass Sie einem Ordner nur ein Bildprofil zuweisen können. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Bildprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen ist, werden in der Benutzeroberfläche unter Verwendung des Profilnamens angezeigt, der auf der Karte angezeigt wird.

<!-- When you add smart crop to an existing image profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

Sie können Bildprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Bildprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

### Anwenden von Bildprofilen für Dynamic Media auf bestimmte Ordner {#applying-image-profiles-to-specific-folders}

Sie können im Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** ein Bildprofil auf einen Ordner anwenden. In diesem Abschnitt wird beschrieben, wie Sie Bildprofile auf beide Arten auf Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

#### Anwenden von Bildprofilen für Dynamic Media auf Ordner über die Benutzeroberfläche „Profile“{#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie ein Bildprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Tippen Sie auf **[!UICONTROL Verarbeitungsprofil auf Ordner anwenden]** und wählen Sie mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Tippen oder klicken Sie anschließend auf **[!UICONTROL Anwenden]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Bildprofilen für Dynamic Media auf Ordner über „Eigenschaften“{#applying-image-profiles-to-folders-from-properties}

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, auf den Sie ein Bildprofil anwenden möchten.
1. Tippen Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Tippen Sie auf die Registerkarte **[!UICONTROL Bildprofile]**. Wählen Sie in der Dropdown-Liste **[!UICONTROL Profilname]** das gewünschte Profil aus und klicken Sie auf **[!UICONTROL Speichern und schließen]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Globales Anwenden eines Dynamic Media-Bildprofils {#applying-an-image-profile-globally}

Sie können ein Experience Manager nicht nur auf einen Ordner anwenden, sondern auch global anwenden, sodass auf alle Inhalte, die in -Assets in einem beliebigen Ordner hochgeladen werden, das ausgewählte Profil angewendet wird.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

**So wenden Sie ein Dynamic Media-Bildprofil global an:**

1. Führen Sie einen der folgenden Schritte aus:

   * Navigieren Sie zu `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und wenden Sie das entsprechende Profil an und klicken Sie auf **[!UICONTROL Speichern]**.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navigieren Sie in CRXDE Lite zum folgenden Knoten: `/content/dam/jcr:content`.

      Fügen Sie die Eigenschaft `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` hinzu und tippen Sie auf **[!UICONTROL Alle speichern]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern eines einzelnen Bildes {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!NOTE]
>
>Smartes Zuschneiden ist nur im Scene7-Modus von Dynamic Media verfügbar.

Sie können das Zuschnittsfenster eines Bildes manuell neu ausrichten oder die Größe ändern, um den Fokus präziser zu bestimmen.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

Siehe auch [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**So bearbeiten Sie smarte Zuschnitte oder smarte Farb-/Bildmuster eines einzelnen Bildes:**

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, auf den das Bildprofil &quot;Smartes Zuschneiden&quot;oder &quot;Smartes Farb-/Bildmuster&quot;angewendet wurde.

1. Tippen Sie auf den Ordner, damit Sie dessen Inhalt öffnen können.
1. Tippen Sie auf das Bild, dessen smarten Zuschnitt oder smartes Farb-/Bildmuster Sie anpassen möchten.
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Smartes Zuschneiden]**.

1. Führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie den Schieberegler in der oberen rechten Ecke der Seite nach links oder rechts, um die Bildanzeige zu erweitern oder zu reduzieren.
   * Ziehen Sie im Bild eine Ecke, um die Größe des sichtbaren Bereichs des Zuschnitts oder Farb-/Bildmusters anzupassen.
   * Ziehen Sie das Feld bzw. Farb-/Bildmuster im Bild an eine neue Position. Sie können nur Bildmuster bearbeiten. Farbmuster sind statisch.
   * Tippen Sie über dem Bild auf **[!UICONTROL Wiederherstellen]**, um all Ihre Änderungen rückgängig zu machen und den ursprünglichen Zuschnitt bzw. das Farb-/Bildmuster wiederherzustellen.

1. Tippen Sie in der oberen rechten Ecke der Seite auf **[!UICONTROL Speichern]** und anschließend auf **[!UICONTROL Schließen]**, um zum Asset-Ordner zurückzukehren.

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

Nachdem Sie ein Bildprofil - das smartes Zuschneiden enthält - auf einen Ordner angewendet haben, wird auf alle Bilder in diesem Ordner ein Zuschnitt angewendet. Sie können das Zuschnittsfenster in mehreren Bildern *manuell* neu ausrichten oder die Größe verändern, um den Fokus präziser zu bestimmen.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

**So bearbeiten Sie smarte Zuschnitte oder smarte Farb-/Bildmuster mehrerer Bilder:**

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** und dann zu einem Ordner, auf den das Bildprofil &quot;Smartes Zuschneiden&quot;oder &quot;Smartes Farb-/Bildmuster&quot;angewendet wurde.
1. Tippen Sie beim entsprechenden Ordner auf das Symbol **[!UICONTROL Mehr Aktionen]** (...) und anschließend auf **[!UICONTROL Smartes Zuschneiden]**.

1. Führen Sie auf der Seite **[!UICONTROL Smartes Zuschneiden bearbeiten]** eine der folgenden Aktionen durch:

   * Passen Sie die Anzeigegröße von Bildern auf der Seite an.

      Ziehen Sie den Schieberegler rechts neben der Dropdown-Liste mit Breakpoint-Namen nach links oder rechts, um den sichtbaren Bildbereich anzupassen.

      ![edit_smart_products-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtern Sie die Liste sichtbarer Bilder basierend auf Breakpoint-Namen. Im unten stehenden Beispiel werden die Bilder nach dem Breakpoint-Namen „Mittel“ gefiltert.

      Wählen Sie aus der Dropdown-Liste in der oberen rechten Ecke der Seite einen Breakpoint-Namen aus, um zu filtern, welche Bilder Ihnen angezeigt werden. (Siehe Abbildung oben.)

      ![edit_smart_products-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Passen Sie die Größe des Zuschnittsfeldes an. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen. Oder tippen oder klicken Sie auf das smarte Bildmuster unter dem Bild (Farbmuster sind statisch) und ziehen Sie die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Bildmusters anzupassen.

      ![Größenänderung des smarten Zuschnitts eines Bildes](assets/edit_smart_crops-resize.png)

   * Verschieben Sie das smarte Zuschnittsfeld. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Zuschnittsfeld im Bild an eine neue Position.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Zuschnittsfeld im Bild an eine neue Position. Oder tippen oder klicken Sie unter dem Bild auf das smarte Bildmuster (Farbmuster sind statisch) und ziehen Sie das smarte Zuschnittsfeld an eine neue Position.

      ![edit_smart_cards-move](assets/edit_smart_crops-move.png)

   * Machen Sie all Ihre Änderungen rückgängig und stellen Sie den ursprünglichen smarten Zuschnitt bzw. das smarte Farb-/Bildmuster wieder her (gilt nur für die aktuelle Bearbeitungssitzung).

      Tippen Sie über dem Bild auf **[!UICONTROL Wiederherstellen]**.

      ![edit_smart_cards-revert](assets/edit_smart_crops-revert.png)



1. Tippen Sie in der oberen rechten Ecke der Seite auf **[!UICONTROL Speichern]** und anschließend auf **[!UICONTROL Schließen]**, um zum Asset-Ordner zurückzukehren.

## Entfernen eines Bildprofils aus Ordnern {#removing-an-image-profile-from-folders}

Wenn Sie ein Bildprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

Sie können im Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** ein Bildprofil aus einem Ordner entfernen. In diesem Abschnitt werden die beiden Möglichkeiten beschrieben, wie Sie Bildprofile aus Ordnern entfernen können.

### Entfernen von Bildprofilen für Dynamic Media aus Ordnern über die Benutzeroberfläche „Profile“ {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie ein Bildprofil aus, das Sie aus einem Ordner oder mehreren Ordnern entfernen möchten.
1. Tippen Sie auf **[!UICONTROL Verarbeitungsprofil aus Ordner(n) entfernen]** und wählen Sie einen oder mehrere Ordner aus, aus denen das Profil entfernt werden soll. Tippen Sie dann auf **[!UICONTROL Entfernen]**.

   Sie können überprüfen, ob das Bildprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Bildprofilen für Dynamic Media aus Ordnern über „Eigenschaften“ {#removing-image-profiles-from-folders-via-properties}

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, aus dem Sie ein Bildprofil entfernen möchten.
1. Tippen Sie im Ordner auf das Kontrollkästchen, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Bildprofile]**.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Profilname]** die Option **[!UICONTROL Kein]** aus und klicken Sie dann auf **[!UICONTROL Speichern und schließen]**.

   Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.
