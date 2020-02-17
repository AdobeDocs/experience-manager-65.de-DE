---
title: Bildprofile für dynamische Medien
description: Erstellen Sie Bildprofile, die Einstellungen für Unschärfemasken sowie smartes Zuschneiden oder smarte Bildmuster (oder beides) enthalten, und wenden Sie das Profil auf einen Ordner mit Bild-Assets an.
uuid: 9049fab9-d2be-4118-8684-ce58f3c8c16a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: 4f9301db-edf8-480b-886c-b5e8fca5bf5c
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Bildprofile für dynamische Medien {#image-profiles}

Beim Hochladen von Bildern können Sie das Bild beim Hochladen automatisch beschneiden, indem Sie ein Bildprofil auf den Ordner anwenden.

>[!NOTE]
>
>Smartes Zuschneiden ist nur im Scene7-Modus von Dynamic Media verfügbar.

## Crop options {#crop-options}

Für das Zuschneiden von Bildern stehen Ihnen zwei Optionen und für die Automatisierung der Erstellung von Farb- und Bildmustern eine Option zur Verfügung.

<table>
 <tbody>
  <tr>
   <td><strong>Wahl</strong></td>
   <td><strong>Wann ist sie einzusetzen?</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Pixelzuschnitt</td>
   <td>Nur Massenzuschnitt von Bildern basierend auf Dimensionen.</td>
   <td><p>Um diese Option zu verwenden, wählen Sie aus dem Dropdownmenü „Zuschnittsoptionen“ <strong>Pixelzuschnitt</strong> aus.</p> <p>Um die Seiten eines Bildes zu beschneiden, geben Sie die Anzahl der Pixel ein, die von einer oder von allen Seiten des Bildes abgeschnitten werden sollen. Um wie viel das Bild beschnitten wird, hängt von der ppi-Einstellung (Pixel per Inch; Pixel pro Zoll) in der Bilddatei ab.</p> <p>Ein Bildprofil-Pixelzuschnitt wird wie folgt gerendert:<br />  </p>
    <ul>
     <li>Werte: oben, unten, links und rechts.</li>
     <li>Der Wert für links ist 0,0. Von dort aus wird der Pixelzuschnitt berechnet.</li>
     <li>Startpunkt des Zuschnitts: Links ist X und oben ist Y</li>
     <li>Horizontale Berechnung: Horizontale Pixelabmessungen des Originalbilds abzüglich des Werts für links und dann abzüglich des Werts für rechts.</li>
     <li>Vertikale Berechnung: Die vertikale Pixelhöhe abzüglich des Werts für oben und dann abzüglich des Werts für unten.</li>
    </ul> <p>Beispiel: Sie haben ein Bild in der Größe 4000 x 3000 Pixel. Sie verwenden folgende Werte: Oben = 250; Unten = 500; Links = 300; Rechts = 700.</p> <p>Schneiden Sie von oben links (300, 250) aus mit dem Füllraum (4000-300-700, 3000-250-500 oder 3000,2250).</p> </td>
  </tr>
  <tr>
   <td>Smartes Zuschneiden</td>
   <td>Massenzuschnitt von Bildern basierend auf ihrem visuellen Fokus.</td>
   <td><p>Smartes Zuschneiden nutzt die Möglichkeiten künstlicher Intelligenz in Adobe Sensei, um den Massenzuschnitt von Bildern schnell zu automatisieren. Smartes Zuschneiden erkennt automatisch den Fokus in jedem Bild und schneidet es entsprechend zu, um das Bildmotiv richtig zu erfassen – unabhängig von der Bildschirmgröße.</p> <p>Um smartes Zuschneiden zu verwenden, wählen Sie aus der Dropdownliste „Zuschnittsoptionen“ die Option <strong>Smartes Zuschneiden</strong> aus und aktivieren Sie „Responsive Bildbeschneidung“. </p> <p>Die standardmäßigen Breakpoint-Größen für „Groß“, „Mittel“ und „Klein“ decken in der Regel alle Größen ab, in denen Bilder auf Smartphones, Tablets, Computern und in Bannern verwendet werden. Sie können die Standardnamen „Groß“, „Mittel“ und „Klein“ beliebig anpassen.</p> <p>Um weitere Breakpoints hinzuzufügen, klicken Sie auf <strong>Zuschnitt hinzufügen</strong>. Wenn Sie einen Zuschnitt löschen möchten, klicken Sie auf das Papierkorb-Symbol.</p> </td>
  </tr>
  <tr>
   <td>Farb- und Bildmuster</td>
   <td>Massenweise Erstellung von Bildmustern für die einzelnen Bilder.</td>
   <td><p><strong>Hinweis:</strong> Smarte Muster werden in Dynamic Media Classic nicht unterstützt.</p> <p>Erkennen und generieren Sie automatisch hochwertige Bildmuster aus Produktbildern, die Farbe oder Material zeigen.</p> <p>Um Farb- und Bildmuster zu verwenden, wählen Sie aus der Dropdownliste „Zuschnittsoptionen“ <strong>Smartes Zuschneiden</strong> aus und aktivieren Sie die Funktion „Farb- und Bildmuster“. Geben Sie in den Feldern „Breite“ und „Höhe“ einen Pixelwert an.</p> <p>Zwar sind alle Bildzuschnitte über die Leiste „Ausgabeformate“ verfügbar, jedoch können Farb- und Bildmuster nur über die Funktion „URL kopieren“ verwendet werden. Beachten Sie, dass Sie eine eigene Anzeigekomponente verwenden müssen, um das Farbfeld auf Ihrer Site anzuzeigen. (Hiervon ausgenommen sind Karussellbanner. Dynamic Media bietet die Anzeigekomponente für in entsprechenden Bannern verwendete Farb-/Bildmuster.)</p> <p><strong>Verwendung von Bildmustern</strong></p> <p>Die URL für Bildmuster ist einfach. Sie lautet:</p> <p><code>/is/image/company/&lt;asset_name&gt;:Swatch</code></p> <p>where <code>:Swatch</code> is appended to the asset request.</p> <p><strong>Verwendung von Farbmustern</strong></p> <p>Um Farbmuster zu verwenden, stellen Sie wie folgt eine <code>req=userdata</code>-Anfrage:</p> <p><code>/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata</code></p> <p>Folgendes ist beispielsweise ein Farbmuster-Asset in Dynamic Media Classic (Scene7):</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch</code></p> <p>and here is the swatch asset's corresponding <code>req=userdata</code> URL:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata</code></p> <p>The <code>req=userdata</code> response is as follows:</p> <p><code class="code">SmartCropDef=Swatch
       SmartCropHeight=200.0
       SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200
       SmartCropType=Swatch
       SmartCropWidth=200.0
       SmartSwatchColor=0xA56DB2</code></p> <p>Sie können wie in den folgenden URL-Beispielen auch eine <code>req=userdata</code>-Antwort im XML- oder JSON-Format anfordern:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml</code></p><p><code>SmartSwatchColor</code></p><p></p></td></tr></tbody></table>

## Unschärfemaske {#unsharp-mask}

You use **[!UICONTROL Unsharp mask]** to fine-tune a sharpening filter effect on the final downsampled image. You can control intensity of effect, radius of the effect (measured in pixels), and a threshold of contrast that will be ignored. This effect uses the same options as Adobe Photoshop’s “Unsharp Mask” filter.

>[!NOTE]
>
>Die Unschärfemaske wird nur auf herunterskalierte Ausgabeformate im PTIFF (Pyramiden-TIFF) angewendet, die mehr als 50 % heruntergesampelt sind. Daher werden die größten Ausgabeformate im PTIFF nicht durch die Unschärfemaske beeinflusst. Demgegenüber werden kleinere Ausgabeformate wie Miniaturen geändert (und hierbei wird die Unschärfemaske angezeigt).

In **[!UICONTROL Unschärfemaske]** sind die folgenden Filteroptionen verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Wahl</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Stärke</td>
   <td>Steuert den auf die Kantenpixel angewendeten Kontrastwert. Der Standardwert ist 1,75. Bei hochauflösenden Bildern können Sie ihn auf bis zu 5 erhöhen. Der Wert dient hierbei als ein Maß für die Filterintensität. Bereich: 0-5.</td>
  </tr>
  <tr>
   <td>Radius</td>
   <td>Bestimmt die Anzahl der Pixel um die Kantenpixel, auf die sich die Scharfzeichnung auswirkt. Bei hochauflösenden Bildern geben Sie einen Wert zwischen 1 und 2 ein. Bei einem niedrigen Wert werden lediglich die Kantenpixel scharfgezeichnet, bei einem hohen Wert werden mehr Pixel scharfgezeichnet. Der korrekte Wert hängt von der Bildgröße ab. Der Standardwert ist 0,2.  Bereich: 0-250.</td>
  </tr>
  <tr>
   <td>Schwelle</td>
   <td><p>Bestimmt den Kontrastbereich, der bei der Anwendung des Filters „Unschärfemaske“ ignoriert werden soll. In anderen Worten: Die Option bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel eingestuft und scharfgezeichnet werden. Um Rauschen zu vermeiden, experimentieren Sie mit Werten zwischen 0 und 255.</p> </td>
  </tr>
 </tbody>
</table>

Das Scharfzeichnen wird unter [Scharfzeichnen von Bildern](/help/assets/assets/s7_sharpening_images.pdf) beschrieben.

## Erstellen von Bildprofilen für dynamische Medien {#creating-image-profiles}

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dms7.md#configuring-asset-processing).

See [Profiles for Processing Metadata, Images, and Videos](processing-profiles.md).

Informationen hierzu finden Sie auch im Thema über die [Best Practices für die Organisation Ihrer digitalen Assets zur Verwendung von Verarbeitungsprofilen](/help/assets/organize-assets.md).

**So erstellen Sie dynamische Medienbildprofile**

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Image Profiles]**.
1. Tap **[!UICONTROL Create]** to add a new image profile.
1. Geben Sie einen Profilnamen und Werte für Unschärfemasken, Zuschneiden oder Farb-/Bildmuster (oder beides) an.

   Es empfiehlt sich, einen Profilnamen auszuwählen, der den Zweck des Profils beschreibt. Wenn Sie beispielsweise ein Profil erstellen, das nur Farb-/Bildmuster generiert – wo also smartes Zuschneiden deaktiviert und „Farb- und Bildmuster“ aktiviert ist –, können Sie das Profil „Smarte Farb-/Bildmuster“ nennen.

   Siehe auch [Optionen für smartes Zuschneiden und smarte Farb-/Bildmuster](#crop-options) sowie [Unschärfemasken](#unsharp-mask).

   ![Kultur](assets/crop.png)

1. Tippen Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Profil wird in der Liste der verfügbaren Profile angezeigt.

## Bearbeiten oder Löschen von Bildprofilen für dynamische Medien {#editing-or-deleting-image-profiles}

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Image Profiles]**.
1. Wählen Sie das Bildprofil aus, das Sie bearbeiten oder entfernen möchten. Wählen Sie **[!UICONTROL Bildverarbeitungsprofil bearbeiten]** aus, um es zu bearbeiten. Wählen Sie **[!UICONTROL Bilderarbeitungsprofil löschen]** aus, um es zu entfernen.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Wenn Sie das Profil bearbeitet haben, speichern Sie die Änderungen. Wenn Sie das Profil löschen, bestätigen Sie, dass Sie es entfernen möchten.

## Anwenden eines dynamischen Medienbildprofils auf Ordner {#applying-an-image-profile-to-folders}

Wenn Sie ein Bildprofil einem Ordner zuweisen, erben automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Bildprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Bildprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen ist, werden in der Benutzeroberfläche mit Namen des Profils aufgelistet, das in der Karte angezeigt wird.

<!-- When you add smart crop to an existing image profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

Sie können Bildprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner neu verarbeiten, der bereits über ein bestehendes Bildprofil verfügt, das Sie später geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

### Anwenden von Bildprofilen für dynamische Medien auf bestimmte Ordner {#applying-image-profiles-to-specific-folders}

You can apply an image profile to a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from **[!UICONTROL Properties]**. In diesem Abschnitt werden die beiden Möglichkeiten beschrieben, mit denen Sie Bildprofile auf Ordner anwenden können.

Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

Sie können Assets in einem Ordner neu verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie später geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

#### Applying Dynamic Media image profiles to folders from Profiles user interface {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Image Profiles]**.
1. Wählen Sie ein Bildprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Tap **[!UICONTROL Apply Processing Profile to Folder(s)]** and select the folder or multiple folders you want use to receive the newly uploaded assets and tap/click **[!UICONTROL Apply]**. Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

#### Applying Dynamic Media image profiles to folders from Properties {#applying-image-profiles-to-folders-from-properties}

1. Tap the AEM logo and navigate to **[!UICONTROL Assets]** and then to the folder that you want to apply an image profile to.
1. On the folder, tap the check mark to select it and then tap **[!UICONTROL Properties]**.
1. Tippen Sie auf die Registerkarte **[!UICONTROL Bildprofile]**. From the **[!UICONTROL Profile Name]** drop-down list, select the profile, then tap **[!UICONTROL Save &amp; Close]**. Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Globales Anwenden eines dynamischen Medienbildprofils {#applying-an-image-profile-globally}

Profile können nicht nur auf einzelne Ordner, sondern auch global angewendet werden. Dann wird allen Inhalten, die Sie in AEM-Assets in beliebigen Ordnern hochladen, das ausgewählte Profil zugeordnet.

Sie können Assets in einem Ordner neu verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie später geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](processing-profiles.md#reprocessing-assets).

**So wenden Sie ein dynamisches Medienbildprofil global** an

1. Führen Sie einen der folgenden Schritte aus:

   * Navigieren Sie zum entsprechenden Profil, wenden Sie es an `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und klicken Sie auf **[!UICONTROL Speichern]**.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navigate to CRXDE Lite to the following node: `/content/dam/jcr:content`.

      Fügen Sie die Eigenschaft hinzu `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` und tippen Sie auf Alle **[!UICONTROL speichern]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern eines einzelnen Bildes {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!NOTE]
>
>Smartes Zuschneiden ist nur im Scene7-Modus von Dynamic Media verfügbar.

Sie können das Zuschnittsfenster eines Bildes manuell neu ausrichten oder die Größe ändern, um den Fokus präziser zu bestimmen.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

Siehe auch [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**So bearbeiten Sie die intelligente Beschneidung oder das intelligente Farbfeld eines einzelnen Bildes**:

1. Tap the AEM logo and navigate to **[!UICONTROL Assets]**, then to the folder that has a smart crop or smart swatch image profile applied to it.

1. Tippen Sie auf den Ordner, um dessen Inhalt zu öffnen.
1. Tippen Sie auf das Bild, dessen intelligentes Beschneiden oder intelligentes Farbfeld Sie anpassen möchten.
1. On the toolbar, tap **[!UICONTROL Smart Crop]**.

1. Führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie den Schieberegler in der oberen rechten Ecke der Seite nach links oder rechts, um die Bildanzeige zu erweitern oder zu reduzieren.
   * Ziehen Sie im Bild eine Ecke, um die Größe des sichtbaren Bereichs des Zuschnitts oder Farb-/Bildmusters anzupassen.
   * Ziehen Sie das Feld bzw. Farb-/Bildmuster im Bild an eine neue Position. Sie können nur Bildmuster bearbeiten. Farbmuster sind statisch.
   * Above the image, tap  **[!UICONTROL Revert]** to undo all your edits and restore the original crop or swatch.

1. Near the upper-right corner of the page, tap **[!UICONTROL Save]**, then tap **[!UICONTROL Close]** to return to the folder of assets.

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

Nachdem Sie ein Bildprofil - das Smart-Beschneiden enthält - auf einen Ordner angewendet haben, wird für alle Bilder in diesem Ordner eine Beschneidung angewendet. If desired, you can *manually* realign or resize the smart crop window in multiple images to further refine their focal point.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

**So bearbeiten Sie das intelligente Beschneiden- oder Smart-Farbfeld mehrerer Bilder**:

1. Tap the AEM logo and navigate to **[!UICONTROL Assets]**, then to a folder that has a smart crop or smart swatch image profile applied to it.
1. On the folder, tap the **[!UICONTROL More Actions]** (...) icon, then tap **[!UICONTROL Smart Crop]**.

1. On the **[!UICONTROL Edit Smart Crops]** page, do any of the following:

   * Passen Sie die Anzeigegröße der Bilder auf der Seite an.

      Ziehen Sie den Schieberegler rechts neben der Dropdownliste mit Breakpoint-Namen nach links oder rechts, um den sichtbaren Bildbereich anzupassen.

      ![edit_smart_products-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtern Sie die Liste sichtbarer Bilder basierend auf Breakpoint-Namen. Im unten stehenden Beispiel werden die Bilder nach dem Breakpoint-Namen „Mittel“ gefiltert.

      Wählen Sie aus der Dropdownliste in der oberen rechten Ecke der Seite einen Breakpoint-Namen aus, um zu filtern, welche Bilder Ihnen angezeigt werden. (Siehe Abbildung oben.)

      ![edit_smart_products-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Passen Sie die Größe des Zuschnittsfeldes an. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen. Oder tippen oder klicken Sie auf das smarte Bildmuster unter dem Bild (Farbmuster sind statisch) und ziehen Sie die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Bildmusters anzupassen.
      ![Größenänderung des smarten Zuschnitts eines Bildes.](assets/edit_smart_crops-resize.png)

   * Verschieben Sie das smarte Zuschnittsfeld. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Zuschnittsfeld im Bild an eine neue Position.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Zuschnittsfeld im Bild an eine neue Position. Oder tippen oder klicken Sie unter dem Bild auf das smarte Bildmuster (Farbmuster sind statisch) und ziehen Sie das smarte Zuschnittsfeld an eine neue Position.
      ![edit_smart_cards-move](assets/edit_smart_crops-move.png)

   * Machen Sie all Ihre Änderungen rückgängig und stellen Sie den ursprünglichen smarten Zuschnitt bzw. das smarte Farb-/Bildmuster wieder her (gilt nur für die aktuelle Bearbeitungssitzung).

      Tippen Sie auf **[!UICONTROL Zurück]** über dem Bild.

      ![edit_smart_cards-revert](assets/edit_smart_crops-revert.png)



1. Tippen Sie in der Nähe der oberen rechten Ecke auf **[!UICONTROL Speichern]**. then tap **[!UICONTROL Close]** to return to the folder of assets.

## Entfernen eines Bildprofils aus Ordnern {#removing-an-image-profile-from-folders}

Wenn Sie ein Bildprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, verbleibt jedoch intakt.

You can remove an image profile from a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from **[!UICONTROL Properties]**. In diesem Abschnitt werden die beiden Möglichkeiten beschrieben, wie Sie Bildprofile aus Ordnern entfernen können.

### Entfernen von Bildprofilen für dynamische Medien aus Ordnern über die Benutzeroberfläche &quot;Profile&quot; {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Tap the AEM logo and navigate to **[!UICONTROL Tools > Assets > Image Profiles]**.
1. Wählen Sie ein Bildprofil aus, das Sie aus einem Ordner oder mehreren Ordnern entfernen möchten.
1. Tap **[!UICONTROL Remove Processing Profile from Folder(s)]** and select the folder or multiple folders you want use to remove the profile from and tap **[!UICONTROL Remove]**.

   Sie können überprüfen, dass das Bildprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Bildprofilen für dynamische Medien aus Ordnern mithilfe von Eigenschaften {#removing-image-profiles-from-folders-via-properties}

1. Tap the AEM logo and navigate **[!UICONTROL Assets]** and then to the folder that you want to remove an image profile from.
1. On the folder, tap the check mark to select it, then tap **[!UICONTROL Properties]**.
1. Select the **[!UICONTROL Image Profiles]** tab.
1. Wählen Sie im Dropdownmenü **[!UICONTROL Profilname]** die Option **[!UICONTROL Keine]** und klicken Sie dann auf **[!UICONTROL Speichern und Schließen]**.

   Ordner, denen bereits ein Profil zugewiesen wurde, sind dadurch gekennzeichnet, dass der Name des Profils direkt unterhalb des Ordnernamens angezeigt wird.
