---
title: Rotationssets
description: Erfahren Sie, wie Sie mit Rotationssets in dynamischen Medien arbeiten können
uuid: 379a20a3-6a17-499a-b0f1-3a835b97aa7b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 8e9b3815-2893-4e6b-ac41-77720b42d56b
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Rotationssets{#spin-sets}

Ein Rotationsset simuliert das Drehen eines Gegenstands zur genaueren Untersuchung. Mit Rotationssets können Artikel aus jedem Winkel betrachtet werden, um die wesentlichen visuellen Details von allen Seiten sehen zu können.

Ein Rotationsset simuliert die 360-Grad-Anzeige. Dynamic Media bietet Rotationssets mit einer Achse, in denen ein Artikel gedreht werden kann. Darüber hinaus können Benutzer alle Ansichten mit nur wenigen Mausklicks frei zoomen und schwenken. So können Benutzer einen Artikel aus einem bestimmten Blickwinkel genauer untersuchen.

Spin Sets are designated by a banner with the word **[!UICONTROL SPINSET]**. In addition, if the Spin Set is published, then the publish date, indicated by the **[!UICONTROL World]** icon is on the banner along with the last modification date, indicated by the **[!UICONTROL Pencil]** icon displays.

![chlimage_1-](assets/chlimage_1-380.png)

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](/help/assets/managing-assets-touch-ui.md).

## Schnellstart: Rotationssets {#quick-start-spin-sets}

Führen Sie die folgenden Schritte aus, um den schnellen Einstieg in die Arbeit mit Rotationssets zu schaffen:

1. [Laden Sie die Bilder für mehrere Ansichten hoch.](#uploading-assets-for-spin-sets)

   Sie benötigen mindestens 8 bis 12 Aufnahmen eines Objekts für ein eindimensionales Rotationsset und 16 bis 24 Aufnahmen für ein zweidimensionales Rotationsset. Die Aufnahmen müssen in regelmäßigen Abständen gemacht werden, um den Eindruck zu erwecken, dass der Gegenstand gedreht und umgedreht wird. Wenn ein eindimensionales Rotationsset beispielsweise 12 Aufnahmen enthält, drehen Sie das Objekt für jede Aufnahme um 30 Grad (360/12).

1. [Erstellen Sie Rotationssets.](#creating-spin-sets)

   To create a Spin Set, select **[!UICONTROL Create > Spin Set]** and then name the set, choose the assets, and choose the order the images appear.

   Siehe [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md).

   >[!NOTE]
   >
   >Sie können Rotationssets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets) erstellen. **Wichtig:** Stapelsätze werden vom IPS (Image Production System) im Rahmen der Asset-Aufnahme erstellt und sind nur im Scene7-Modus von Dynamic Media verfügbar.

1. Richten Sie [Rotationsset-Viewer-Vorgaben](/help/assets/managing-viewer-presets.md) nach Bedarf ein.

   Administratoren können Rotationsset-Viewer-Vorgaben erstellen oder ändern. To see your spin set with a viewer preset, select the spin set, and in the left-rail drop-down menu, select **Viewers**.

   See **[!UICONTROL Tools > Assets > Viewer Presets]** to create or edit viewer presets.

   See [Adding and editing viewer presets.](/help/assets/managing-viewer-presets.md)

1. [Zeigen Sie Rotationssets an](#viewing-spin-sets).

   Es gibt drei verschiedene Arten, über Stapelsatzvorgaben erstellte Sätze anzuzeigen und darauf zuzugreifen. (Sets created using batch set presets, do *not* appear in the user interface.)

1. [Zeigen Sie eine Vorschau der Rotationssets an.](/help/assets/previewing-assets.md)

   Wählen Sie das Rotationsset aus, um dessen Vorschau anzuzeigen. Drehen Sie das Rotationsset. You can choose different viewers from the **[!UICONTROL Viewers]** menu, available from the left rail drop-down menu.

1. [Veröffentlichen Sie Rotationssets.](/help/assets/publishing-dynamicmedia-assets.md)

   Beim Veröffentlichen eines Rotationssets wird die URL- und Integrationszeichenfolge aktiviert. In addition, you must [publish the viewer preset](/help/assets/managing-viewer-presets.md).

1. [Verknüpfen Sie URLs mit einer Webanwendung](/help/assets/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/embed-code.md).

   AEM Assets erstellt URL-Aufrufe für Rotationssets und aktiviert diese, nachdem Sie die Rotationssets veröffentlicht haben. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ dazu können Sie sie in Ihre Website einbetten.

   Select the Spin Set, then in the left rail drop-down menu, select **[!UICONTROL Viewers]**.

   See [Linking a Spin Set to a web page](/help/assets/linking-urls-to-yourwebapplication.md) and [Embedding the Video or Image Viewer](/help/assets/embed-code.md).

If you need to, you can [edit Spin Sets](#editing-spin-sets). In addition, you can view and modify [Spin Set properties](/help/assets/managing-assets-touch-ui.md#editing-properties).

## Uploading Assets for Spin Sets {#uploading-assets-for-spin-sets}

Sie benötigen mindestens 8 bis 12 Aufnahmen eines Objekts für ein eindimensionales Rotationsset und 16 bis 24 Aufnahmen für ein zweidimensionales Rotationsset. Die Aufnahmen müssen in regelmäßigen Abständen gemacht werden, um den Eindruck zu erwecken, dass der Gegenstand gedreht und umgedreht wird. Wenn ein eindimensionales Rotationsset beispielsweise 12 Aufnahmen enthält, drehen Sie das Objekt für jede Aufnahme um 30 Grad (360/12).

Bilder für Rotationssets können Sie genauso wie [alle anderen Assets in AEM-Assets](/help/assets/managing-assets-touch-ui.md) hochladen.

### Richtlinien zum Erfassen von Bildern für ein Rotationsset {#guidelines-for-shooting-spin-set-images}

Im Folgenden finden Sie einige Best Practices für Rotationsset-Bilder. Im Allgemeinen gilt: Je mehr Bilder ein Rotationsset enthält, desto besser gelingt der Bildrotationseffekt. Wenn Sie aber zahlreiche Bilder in das Set aufnehmen, dauert es auch länger, bis die Bilder geladen werden. AEM empfiehlt die folgenden Richtlinien für die Aufnahme von Bildern für Rotationssets.

* Verwenden Sie mindestens 8 bis 12 Bilder in einem eindimensionalen Rotationsset und 16 bis 24 Bilder in einem zweidimensionalen Rotationsset. Um 360 Grad drehen zu können, sind mindestens 8 Bilder erforderlich. Eindimensionale Rotationssets werden häufiger verwendet, da die Erstellung zweidimensionaler Rotationssets sehr aufwändig ist.
* Verwenden Sie ein verlustfreies Format: TIFF und PNG werden empfohlen.
* Maskieren Sie alle Bilder so, dass der Artikel vor einem rein weißen oder kontrastreichen Hintergrund erscheint. Fügen Sie optional Schatten hinzu.
* Stellen Sie sicher, dass die Produktdetails gut beleuchtet und fokussiert sind.
* Denken Sie z. B. an Rotationsbilder für Bekleidung an einer Schaufensterpuppe oder einem Modell. Die Schaufensterpuppe ist häufig entweder komplett maskiert (eine Schaufensterpuppe aus Glas) oder es wird eine stilisierte Schaufensterpuppe im Bild gezeigt. Sie können ein modellbezogenes Rotationsset erstellen, indem Sie die Anzahl der Winkel definieren. Markieren Sie jeden Winkel mit Klebeband auf dem Boden, um dem Modell anzugeben, einen Schritt zu machen und in die Richtung der jeweiligen Aufnahme zu schauen.

## Erstellen von Rotationssets {#creating-spin-sets}

In diesem Abschnitt wird beschrieben, wie Sie Rotationssets in AEM erstellen.

>[!NOTE]
>
>Sie können Rotationssets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets) erstellen. **Wichtig:** Stapelsätze werden vom IPS (Image Production System) im Rahmen der Asset-Aufnahme erstellt und sind nur im Scene7-Modus von Dynamic Media verfügbar.
>
>Siehe „Erstellen von Stapelsatzvorgaben zum automatischen Erzeugen von Bild- und Rotationssets“ in [Konfigurieren von Dynamic Media – Scene7-Modus](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets).


>[!NOTE]
>
>Die Reihenfolge der Bilder in einem Rotationsset ist wichtig. Achten Sie darauf, sie so anzuordnen, dass die Rotation eine gleichmäßige 360-Grad-Ansicht ergibt.

**So erstellen Sie Rotationssets**

1. In Assets, navigate to where you want to create a spin set, click **[!UICONTROL Create]**, and select **[!UICONTROL Spin Set]**. Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält. Der Rotationsset-Editor wird angezeigt.

   ![6_5_spinset-createpulldownmenu](assets/6_5_spinset-createpulldownmenu.png)

1. Geben Sie im Rotationsset-Editor im Feld **[!UICONTROL Titel]** einen Namen für das Rotationsset ein. Der Name wird im Banner über dem Rotationsset angezeigt. Geben Sie optional eine Beschreibung ein.

   ![6_5_spinset-spinseteditortitle](assets/6_5_spinset-spinseteditortitle.png)

   >[!NOTE]
   >
   >Beim Erstellen des Rotationssets können Sie die Miniaturansicht des Rotationssets ändern oder zulassen, dass AEM die Miniaturansicht automatisch basierend auf den Assets im Rotationsset auswählt. To select a thumbnail, click **[!UICONTROL Change thumbnail]** and select any image (you can navigate to other folders to find images as well). If you have selected a thumbnail and then decide that you want AEM to generate one from the spin set, select **[!UICONTROL Switch to Automatic thumbnail]**.

1. Nehmen Sie eine der folgenden Aktionen vor:

   * Tippen Sie oben links auf der Seite des Rotationsset-Editors auf **[!UICONTROL Asset hinzufügen]**.

   * Tippen Sie in der Mitte des Rotationsset-Editors auf **[!UICONTROL Tippen, um den Asset-Wähler zu öffnen]**.
   Tippen Sie, um die gewünschten Assets für das Rotationsset auszuwählen. Über den ausgewählten Assets wird ein Häkchensymbol angezeigt. Wenn Sie die Assets ausgewählt haben, tippen Sie auf **[!UICONTROL Auswählen]**.

   With the Asset Selector, you can search for assets by typing in a keyword and tapping **[!UICONTROL Return**. Mit Filtern können Sie Ihre Suchergebnisse verfeinern. Sie können nach Pfad, Sammlung, Dateityp und Tags filtern. Select the filter and then tap the **[!UICONTROL Filter]** icon on the toolbar. Ändern Sie die Ansicht, indem Sie auf das Symbol „Ansicht“ tippen und zwischen **[!UICONTROL Spaltenansicht]**, **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Listenansicht]** wählen.

   Siehe [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt.  Sie können die Assets nach dem Hinzufügen manuell neu anordnen oder sortieren.

   Ziehen Sie das Symbol zum Neuanordnen eines Assets ggf. rechts neben den Dateinamen des Assets, um Bilder in der Setliste nach oben oder unten zu bewegen.

   ![Ordnen Sie Frame 11 im Rotationsset neu an, indem Sie ihn an eine neue Position ziehen.](assets/6_5_spinset-reorderassets.png)

   Ordnen Sie Frame 11 im Rotationsset neu an, indem Sie ihn an eine neue Position ziehen.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie ein Bild löschen möchten, wählen Sie das Bild aus und tippen Sie auf **[!UICONTROL Asset löschen]**.

   * Wenn Sie eine Vorgabe anwenden möchten, tippen Sie oben rechts auf **[!UICONTROL Vorgabe]**. Wählen Sie anschließend eine Vorgabe aus, um sie auf alle Elemente gleichzeitig anzuwenden.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Rotationsset wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Anzeigen von Rotationssets {#viewing-spin-sets}

Sie können Rotationssets in der Benutzeroberfläche oder automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets) erstellen. However, sets created using batch set presets, do *not* appear in the user interface. Sie haben drei verschiedene Möglichkeiten, auf mit Stapelsatzvorgaben erstellte Sets zuzugreifen. (Diese Methoden sind auch verfügbar, wenn Sie die Rotationssets in der Benutzeroberfläche erstellt haben.)

>[!NOTE]
>
>You can also view sets by way of the user interface as described in [Editing Spin Sets](#editing-spin-sets).

**So zeigen Sie Rotationssets an**

1. Beim Öffnen der Eigenschaften eines einzelnen Assets. Die Eigenschaften zeigen an, zu welchen Sets das ausgewählte Asset gehört (unter **[!UICONTROL Mitglied von Sets]**).  Klicken Sie auf den Namen des Sets, um das gesamte Set anzuzeigen. 

   ![chlimage_1-156](assets/chlimage_1-384.png)

1. Von einem zugehörigen Bild eines beliebigen Sets.  Select the **[!UICONTROL Sets]** menu to display the sets that the asset is a member of.

   ![chlimage_1-157](assets/chlimage_1-385.png)

1. Wählen Sie aus dem Menü „Suche“ die Option **[!UICONTROL Filter]**, erweitern Sie dann **[!UICONTROL Dynamische Medien]** und wählen Sie **[!UICONTROL Sets]** aus. 

   Die Suche gibt als Ergebnis Sets zurück, die in der Benutzeroberfläche manuell oder mit Stapelsatzvorgaben automatisch erstellt wurden.  For automated sets, the search query is conducted using `Starts with` search criteria which is different from AEM search which is based on using `Contains` search criteria. Setting the filter to **[!UICONTROL Sets]** is the only way to search automated sets.

   ![chlimage_1-158](assets/chlimage_1-386.png)

## Bearbeiten von Rotationssets {#editing-spin-sets}

Sie können mehrere Bearbeitungsaufgaben für Rotationssets ausführen, z. B. die folgenden:

* Fügen Sie dem Rotationsset Bilder hinzu.
* Ordnen Sie Bilder im Rotationsset neu an.
* Löschen Sie Assets im Rotationsset.
* Wenden Sie Viewer-Vorgaben an.
* Löschen Sie das Rotationsset.

**So bearbeiten Sie ein Rotationsset**

1. Führen Sie einen der folgenden Schritte aus:

   * Zeigen Sie mit der Maus auf ein Rotationsset-Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).
   * Zeigen Sie mit der Maus auf ein Rotationsset-Asset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.

   * Tippen Sie auf ein Rotationsset-Asset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie zum Bearbeiten des Rotationssets einen der folgenden Schritte aus:

   * Ziehen Sie ein Bild, wenn Sie es an einer neuen Position anordnen möchten (zum Verschieben von Elementen wählen Sie das Symbol zum Neuanordnen).
   * Um Elemente in auf- oder absteigender Reihenfolge zu sortieren, klicken Sie auf die Spaltenüberschrift. 
   * To add an asset or update an existing asset, click **[!UICONTROL Add Asset]**. Navigieren Sie zu einem Element, wählen Sie es aus und tippen Sie oben rechts auf **[!UICONTROL Auswählen.]**
Wenn Sie das in AEM als Miniaturansicht verwendete Bild löschen und durch ein anderes ersetzen, wird das Original-Asset weiterhin angezeigt.
   * To delete an asset, select it and click or tap **[!UICONTROL Delete Asset]**.
   * Um eine Vorgabe anzuwenden, tippen oder klicken Sie auf das Symbol „Vorgabe“ und wählen Sie eine Vorgabe aus.
   * Navigieren Sie zum Löschen eines ganzen Rotationssets zu diesem Rotationsset, wählen Sie es aus und wählen Sie **[!UICONTROL Löschen]**.
   >[!NOTE]
   >
   >Sie können die Bilder in einem Rotationsset bearbeiten, indem Sie zu diesem Set navigieren, in der linken Seitenleiste auf **[!UICONTROL Mitglieder des Sets]** tippen und dann auf das Bleistiftsymbol eines einzelnen Assets tippen, um das Bearbeitungsfenster zu öffnen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, wenn Sie fertig mit der Bearbeitung sind.

## Anzeigen der Vorschau von Rotationssets {#previewing-spin-sets}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](/help/assets/previewing-assets.md).

## Veröffentlichen von Rotationssets {#publishing-spin-sets}

Siehe [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).
