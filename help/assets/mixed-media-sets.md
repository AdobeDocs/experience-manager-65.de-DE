---
title: Gemischte Mediensets
description: Erfahren Sie, wie Sie mit gemischten Mediensets in dynamischen Medien arbeiten können
uuid: cecad772-ed05-46f6-ba44-107195866b0d
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ed84157a-e6b4-4dde-af2e-a1e0b6259628
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Gemischte Mediensets{#mixed-media-sets}

Mit gemischten Mediensets können Sie eine Mischung aus Bildern, Bildsets, Rotationssets und Videos in einer Präsentation bereitstellen.

Gemischte Mediensets werden durch ein Banner mit dem Wort **[!UICONTROL MixedMediaSet]** gekennzeichnet. Darüber hinaus wird bei veröffentlichten Sets für gemischte Medien das Veröffentlichungsdatum (durch das **[!UICONTROL Welt]**-Symbol gekennzeichnet) zusammen mit dem Datum der letzten Änderung (durch das **[!UICONTROL Bleistift]**-Symbol gekennzeichnet) im Banner angezeigt.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](/help/assets/managing-assets-touch-ui.md).

## Schnellstartanleitungen: Gemischte Mediensets {#quick-start-mixed-media-sets}

Führen Sie die folgenden Schritte aus, um den schnellen Einstieg in die Arbeit mit gemischten Mediensets zu schaffen:

1. [Laden Sie die Assets hoch.](#uploading-assets)

   Laden Sie zunächst die Bilder und Videos für die gemischten Mediensets hoch. Erstellen Sie bei Bedarf die [Bildsets](/help/assets/image-sets.md) und [Rotationssets](/help/assets/spin-sets.md). Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Viewer für das gemischte Medienset einzoomen können. Stellen Sie sicher, dass die Bilder mindestens 2000 Pixel in der größten Abmessung aufweisen.

1. [Erstellen Sie gemischte Mediensets.](#creating-mixed-media-sets)

   To create a Mixed Media Set, from the Assets page, tap **[!UICONTROL Create > Mixed Media Set]** and then name the set, choose the assets, and choose the order the images appear.

   Siehe [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md). 

1. Set up [Mixed Media Viewer presets](/help/assets/managing-viewer-presets.md), as needed.

   Administratoren können Viewer-Vorgaben für gemischte Mediensets erstellen oder ändern. To see your mixed media with a viewer preset, select the mixed media set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   See **[!UICONTROL Tools > Assets > Viewer Presets]** to create or edit viewer presets.

   See [Adding and editing viewer presets.](/help/assets/managing-viewer-presets.md)

1. [Zeigen Sie eine Vorschau der gemischten Mediensets an.](#previewing-mixed-media-sets)

   Wenn Sie das gemischte Medienset auswählen, können Sie eine Vorschau davon anzeigen. Klicken Sie auf die Miniaturansichtssymbole, um das gemischte Medienset im gewählten Viewer zu untersuchen. You can choose different Viewers from the **[!UICONTROL Viewers]** menu, available from the left rail drop-down menu.

1. [Veröffentlichen Sie gemischte Mediensets.](#publishing-mixed-media-sets)

   Beim Veröffentlichen eines gemischten Mediensets wird die URL- und Integrationszeichenfolge aktiviert. In addition, you must [publish the viewer preset](/help/assets/managing-viewer-presets.md#publishing-viewer-presets).

1. [Verknüpfen Sie URLs mit einer Webanwendung](/help/assets/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/embed-code.md).

   AEM Assets erstellt URL-Aufrufe für gemischte Mediensets und aktiviert diese nach deren Veröffentlichung. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ dazu können Sie sie in Ihre Website einbetten.

   Select the Mixed Media Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   See [Linking a Mixed Media Set to a web page](/help/assets/linking-urls-to-yourwebapplication.md) and [Embedding the Video or Image Viewer](/help/assets/embed-code.md).

Bei Bedarf können Sie die [gemischten Mediensets](#editing-mixed-media-sets) bearbeiten. In addition, you can view and modify [Mixed Media Set properties](/help/assets/managing-assets-touch-ui.md#editing-properties).

>[!NOTE]
>
>If you have issues creating sets, see [Troubleshooting Dynamic Media - Scene7 mode](/help/assets/troubleshoot-dms7.md).

## Uploading Assets {#uploading-assets}

Laden Sie zunächst die Bilder und Videos für die gemischten Mediensets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Viewer für das gemischte Medienset einzoomen können. Stellen Sie sicher, dass die Bilder mindestens 2000 Pixel in der größten Abmessung aufweisen.

Wenn Sie außerdem Rotationssets oder Bildsets zum Set für gemischte Medien hinzufügen möchten, müssen Sie auch diese erstellen.

## Erstellen von gemischten Mediensets {#creating-mixed-media-sets}

Sie können Ihrem gemischten Medienset Bilder, Bildsets, Rotationssets und Videos hinzufügen. Achten Sie darauf, dass die Dateien, Bildsets und Rotationssets veröffentlicht werden können, bevor Sie diese dem gemischten Medienset hinzufügen.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können die Assets manuell neu anordnen oder sortieren, nachdem sie hinzugefügt wurden. 

**So erstellen Sie ein gemischtes Medienset**

1. In Assets, navigate to where you want to create a mixed media set, and click **[!UICONTROL Create]**, and select **[!UICONTROL Mixed Media Set]**. Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält. Der Editor für gemischte Mediensets wird aufgerufen.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. Geben Sie im Editor für gemischte Mediensets im Feld **[!UICONTROL Titel]** einen Namen für das gemischte Medienset ein. Der Name wird im Banner über dem Set für gemischte Medien angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Beim Erstellen des gemischten Mediensets können Sie die Miniaturansicht des gemischten Mediensets ändern oder zulassen, dass AEM die Miniaturansicht basierend auf den Assets im gemischten Mediensatz automatisch auswählt. To select a thumbnail, click **[!UICONTROL Change thumbnail]** and select any image (you can navigate to other folders to find images as well). If you have selected a thumbnail and then decide that you want AEM to generate one from the mixed media set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Tippen Sie auf die Asset-Auswahl, um Assets auszuwählen, die Sie in Ihr gemischtes Medienset aufnehmen möchten. Wählen Sie sie aus und klicken Sie auf **[!UICONTROL Auswählen]**. 

   With the Asset Selector, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return]**. Mit Filtern können Sie Ihre Suchergebnisse verfeinern. Sie können nach Pfad, Sammlung, Dateityp und Tags filtern. Select the filter and then tap the **[!UICONTROL Filter]** icon from the toolbar. Change the view by selecting the **[!UICONTROL View]** icon and selecting **[!UICONTROL List View]**, **[!UICONTROL Column View]**, or **[!UICONTROL Card View]**.

   Siehe [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-383.png)

1. Re-order the assets by dragging them up or down the list (must select the **[!UICONTROL Reorder]** icon), as necessary.

   ![chlimage_1-141](assets/chlimage_1-352.png)

   If you want to add thumbnails, click the **+** **[!UICONTROL thumbnail]** icon next to the image and navigate to the thumbnail you want. When done selecting all the thumbnail images click **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >If you want to add assets, tap **[!UICONTROL Add Asset]**.

1. To delete an asset, select the corresponding check box and tap **[!UICONTROL Delete Asset]**.
1. To apply a preset, tap **[!UICONTROL Preset]** in the upper right corner and select a preset to apply to the assets.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Set für gemischte Medien wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Bearbeiten von Sets für gemischte Medien {#editing-mixed-media-sets}

Sie können direkt auf der Benutzeroberfläche eine Vielzahl an Bearbeitungsaufgaben für Assets in gemischten Mediensets ausführen, [genauso wie bei allen anderen Assets in Assets](/help/assets/managing-assets-touch-ui.md). Sie können außerdem die folgenden Aktionen in gemischten Mediensets ausführen:

* Fügen Sie dem gemischten Medienset Assets hinzu.
* Ordnen Sie Assets im gemischten Medienset neu an.
* Löschen Sie Assets im gemischten Medienset.
* Wenden Sie Viewer-Vorgaben an.
* Ändern Sie die Standardminiatur.

**So bearbeiten Sie ein gemischtes Medienset**

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.

   * Tippen Sie auf ein Asset in einem gemischten Medienset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie im Editor für gemischte Mediensets einen der folgenden Schritte aus:

   * Um Assets neu anzuordnen, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und ziehen Sie das Asset an eine neue Position.
   * Um Assets hinzuzufügen, tippen Sie in der Symbolleiste auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu den Assets. Bewegen Sie bei jedem Asset, das Sie hinzufügen möchten, den Mauszeiger über dem Bild des Assets (nicht über dem Namen des Assets) und tippen Sie auf das Häkchensymbol. Tippen Sie oben rechts auf **[!UICONTROL Auswählen]**.

   * Um ein Asset zu löschen, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und wählen Sie das Asset aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Asset löschen]**.

   * Um Assets anhand des Namens in aufsteigender oder absteigender Reihenfolge zu sortieren, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol). Klicken Sie rechts neben der Überschrift **[!UICONTROL Assets]** auf das Caret-Zeichen nach oben oder unten.

      >[!NOTE]
      >
      >    * To delete an entire Mixed Media Set, from any viewing mode (such as **[!UICONTROL Card View]** or **[!UICONTROL Column View]**) navigate to the Mixed Media Set. Bewegen Sie den Mauszeiger über das Asset und tippen Sie auf das Kontrollkästchensymbol, um es auszuwählen. Drücken Sie die **[!UICONTROL Rücktaste]** oder klicken Sie in der Symbolleiste auf **[!UICONTROL Mehr]** (Ellipse) und dann auf **[!UICONTROL Löschen]**.
         >
         >    
      * You can edit the assets in a Mixed Media Set by navigating to the set, clicking **Set Members]** in the left rail, and then tapping the **[!UICONTROL Pencil]** icon on an individual asset to open the editing window.


1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie die Bearbeitung abgeschlossen haben.

   >[!NOTE]
   >
   >* Um die Assets in einem gemischten Medienset zu bearbeiten, navigieren Sie zum gemischten Medienset. Tippen Sie auf das Set (ohne es auszuwählen), um es auf der Seite „AEM – Vorschau festlegen“ zu öffnen. Klicken Sie in der linken Leiste auf das Caret-Symbol nach unten, um die Dropdownliste zu öffnen, und tippen Sie auf **[!UICONTROL Mitglieder des Sets]**. Bewegen Sie auf der Seite „Mitglieder des Sets“ den Mauszeiger auf ein Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Stiftsymbol), um die Bearbeitungsseite zu öffnen.
      >
      >
   * Um ein komplettes gemischtes Medienset aus einem Anzeigemodus zu löschen (z. B. Karten- oder Spaltenansicht), navigieren Sie zum gemischten Medienset. Hover on the set, then tap **Select]** (checkmark icon). Drücken Sie die **[!UICONTROL Rücktaste]** oder tippen Sie auf **[!UICONTROL Mehr]** und dann auf **[!UICONTROL Löschen]**.


## Vorschau von gemischten Mediensets {#previewing-mixed-media-sets}

Weitere Informationen zum Aufrufen einer Vorschau von Sets für gemischte Medien finden Sie in [Asset-Vorschau](/help/assets/previewing-assets.md).

## Veröffentlichen von Sets für gemischte Medien {#publishing-mixed-media-sets}

Weitere Informationen zum Veröffentlichen von Sets für gemischte Medien finden Sie in [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Wenn das Set für gemischte Medien bei der ersten Veröffentlichung nicht vollständig an den Bereitstellungsservice übertragen wird, müssen Sie das Set für gemischte Medien möglicherweise erneut veröffentlichen.

