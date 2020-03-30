---
title: Bildsets
description: Erfahren Sie, wie Sie mit Bildsätzen in dynamischen Medien arbeiten können
uuid: ca2fd5b0-656e-4960-b10c-f0ec3d418760
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: ccc4eb23-934c-4e67-860b-a6faa2bcaafc
docset: aem65
translation-type: tm+mt
source-git-commit: 45de0f9d9570d64cacf7009d64072858012869a0

---


# Bildsets {#image-sets}

Über Bildsets erhalten Benutzer ein integriertes Anzeigeerlebnis, bei dem sie unterschiedliche Ansichten eines Elements durch Klicken auf eine Miniaturansicht anzeigen können. Mit Bildsets können Sie alternative Ansichten eines Elements darstellen. Dabei enthält der Viewer Zoomtools, mit denen Bilder genauer betrachtet werden können.

Bildsets werden durch ein Banner mit dem Wort `IMAGESET` gekennzeichnet. Wenn das Bildset veröffentlicht wird, wird das durch das Symbol **[!UICONTROL Welt]** angegebene Veröffentlichungsdatum zusammen mit dem Datum der letzten Änderung auf dem Banner angezeigt, was durch das Symbol **[!UICONTROL Stift]** angegeben wird.

![chlimage_1-133](assets/chlimage_1-339.png)

Innerhalb des Bildsatzes können Sie auch Muster erstellen, indem Sie einen Bildsatz erstellen und Miniaturansichten hinzufügen.

Dies ist besonders nützlich, wenn Sie einen Artikel in einer anderen Farbe, einem anderen Muster oder mit anderer Endverarbeitung darstellen möchten. Um ein Bildset mit Farbmustern zu erstellen, benötigen Sie ein Bild für alle Farben, Muster oder Endverarbeitungen, die den Benutzern dargestellt werden sollen. Außerdem benötigen Sie eine Farb-, Muster- oder Endverarbeitungsvorlage für alle Farben, Muster oder Endverarbeitungen.

Beispiel: Sie möchten Bilder von Kappen darstellen, deren Schirme unterschiedliche Farben aufweisen: rot, grün und blau. In diesem Fall benötigen Sie drei Aufnahmen der gleichen Kappe. Sie brauchen eine Aufnahme mit einem roten Schirm, eine mit einem grünen Schirm und eine mit einem blauen Schirm. Außerdem brauchen Sie ein rotes, grünes und blaues Farbmuster. Die Farbmuster dienen als Miniaturansichten, auf die Benutzer im Musterset-Viewer klicken, um die Kappe mit rotem, grünem oder blauem Schirm anzuzeigen.

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](/help/assets/managing-assets-touch-ui.md).

## Schnellstart: Bildsets {#quick-start-image-sets}

So schaffen Sie einen schnellen Einstieg:

1. [Laden Sie die Masterbilder für mehrere Ansichten hoch.](#uploading-assets-in-image-sets)

   Laden Sie zunächst die Bilder für die Bildsets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Bildset-Viewer einzoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat, um optimale Zoomdetails zu erzielen. Mit dynamischen Medien können Bilder mit einer Auflösung von jeweils bis zu 25 Megapixeln gerendert werden. Sie können beispielsweise ein Bild mit 5000 x 5000 Megapixeln oder eine beliebige andere Größenkombination mit bis zu 25 Megapixeln verwenden.

   AEM Assets unterstützt zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

1. [Erstellen Sie Bildsets.](#creating-image-sets)

   In Bildsets klicken Benutzer im Bildset-Viewer auf Miniaturansichten.

   Tippen oder klicken Sie zum Erstellen eines Bildsets in Assets auf **[!UICONTROL Erstellen > Bildsets]**. Fügen Sie anschließend Bilder hinzu und klicken Sie auf **[!UICONTROL Speichern]**.

   Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) erstellen.
   >[!IMPORTANT]
   >
   >Stapelsätze werden im Rahmen der Asset-Erfassung vom IPS (Image Production System) erstellt und stehen nur im Modus &quot;Dynamische Medien - Scene7&quot;zur Verfügung.

   See [Preparing Image Set assets for upload and Uploading your files](#uploading-assets-in-image-sets).

   Siehe [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md). 

1. Add [Image Set Viewer presets](/help/assets/managing-viewer-presets.md), as needed.

   Administratoren können Bildset-Viewer-Vorgaben erstellen oder ändern. To see your image set with a viewer preset, select the image set, and in the left-rail drop-down menu, select **[!UICONTROL Viewers]**.

   See **[!UICONTROL Tools > Assets > Viewer Presets]** to create or edit viewer presets.

1. (Optional) [Viewing Image Sets](/help/assets/image-sets.md#viewing-image-sets) that were created using batch set presets.
1. [Zeigen Sie Bildsets in einer Vorschau an.](/help/assets/previewing-assets.md)

   Wählen Sie das Bildset aus, um dessen Vorschau anzuzeigen. Klicken Sie auf die Miniaturansichtssymbole, um das Bildset im gewählten Viewer zu untersuchen. You can choose different viewers from the **[!UICONTROL Viewers]** menu, available from the left rail drop-down menu.

1. [Veröffentlichen Sie Bildsets.](/help/assets/publishing-dynamicmedia-assets.md)

   Beim Veröffentlichen eines Bildsets wird die URL- und Einbettungszeichenfolge aktiviert. In addition, you must [publish any custom viewer preset](/help/assets/managing-viewer-presets.md) that you have created. Standardmäßig vorhandene Viewer-Vorgaben wurden bereits veröffentlicht.

1. [Verknüpfen Sie URLs mit einer Webanwendung](/help/assets/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/embed-code.md).

   AEM Assets erstellt URL-Aufrufe für Bildsets und aktiviert diese, nachdem Sie die Bildsets veröffentlicht haben. Sie können diese URLs während der Asset-Vorschau kopieren. Sie können sie alternativ in Ihre Website einbetten.

   Wählen Sie das Bildset und dann im Dropdown-Menü links die Option **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen eines Bildsets mit einer Webseite](/help/assets/linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](/help/assets/embed-code.md).

To edit Image Sets, see [editing Image Sets.](#editing-image-sets) Darüber hinaus können Sie [Bildsatzeigenschaften](/help/assets/managing-assets-touch-ui.md#editing-properties)Ansicht und bearbeiten.

Wenn Sie beim Erstellen von Sets Probleme haben, lesen Sie den Abschnitt zu Bildern und Sets unter [Problembehandlung in Dynamic Media – Scene7-Modus](/help/assets/troubleshoot-dms7.md#images-and-sets).

## Hochladen von Assets in Bildsets {#uploading-assets-in-image-sets}

Laden Sie zunächst die Bilder für die Bildsets hoch. Berücksichtigen Sie den Zoom bei der Auswahl von Bildern, da Benutzer Bilder im Bildset-Viewer einzoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat. Bildsets unterstützen zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

Sie laden Bilder für Bildsets genauso wie [alle anderen Assets in Assets](/help/assets/managing-assets-touch-ui.md#uploading-assets) hoch.

### Vorbereiten von Bildset-Assets auf das Hochladen {#preparing-image-set-assets-for-upload}

Bevor Sie Bildsets erstellen, achten Sie darauf, dass die Bilder die richtige Größe und das richtige Format aufweisen.

Um ein Bildset mit mehreren Ansichten zu erstellen, benötigen Sie Bilder, die einen Artikel aus unterschiedlichen Blickwinkeln zeigen oder unterschiedliche Aspekte desselben Artikels darstellen. Ziel ist es, die wichtigen Merkmale eines Artikels so hervorzuheben, dass Benutzer einen umfassen Einblick in das Aussehen oder die Funktion des Gegenstands erhalten.

Stellen Sie sicher, dass die Bilder in Bildsets mindestens 2000 Pixel in der größten Abmessung aufweisen, da Benutzer sie einzoomen können. Assets unterstützt zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

>[!NOTE]
>
>Wenn Sie außerdem Miniaturansichten verwenden, um Produktmuster anzuzeigen, müssen Sie Folgendes ausführen:
>
>Sie benötigen Vignetten oder unterschiedliche Aufnahmen desselben Bildes, in denen dieses in verschiedenen Farben, Mustern oder Endverarbeitungen dargestellt wird. Außerdem benötigen Sie Miniaturansichtsdateien, die den verschiedenen Farben, Mustern oder Endverarbeitungen entsprechen. Um beispielsweise Miniaturansichten in einem Bildset zu präsentieren, die eine Jacke in Schwarz, Braun und Grün anzeigen, benötigen Sie:
>
>* eine schwarze, braune und grüne Aufnahme der Jacke,
>* eine schwarze, braune und grüne Miniaturansicht


## Erstellen von Bildsets {#creating-image-sets}

Sie können Bildsets über die Benutzeroberfläche oder die API erstellen. In diesem Abschnitt wird beschrieben, wie Sie Bildsets in der Benutzeroberfläche erstellen.

>[!NOTE]
>
>Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets) erstellen.
>**Wichtig:**Stapelsätze werden vom IPS (Image Production System) im Rahmen der Asset-Aufnahme erstellt und sind nur im Scene7-Modus von Dynamic Media verfügbar.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt.  Sie können die Assets manuell neu anordnen oder sortieren, nachdem sie hinzugefügt wurden. 

>[!NOTE]
>
>Bildsätze werden nicht für Assets unterstützt, deren Dateinamen ein „,“ (Komma) enthält.

**So erstellen Sie ein Bildset**

1. Tippen Sie in AEM auf das AEM-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Navigation > Assets]**. Navigieren Sie zu der Stelle, an der Sie ein Bildset erstellen möchten, und tippen Sie dann auf **[!UICONTROL Erstellen > Bildset]**, um die Seite „Bildset-Editor“ zu öffnen.

   Sie können das Set auch aus einem Ordner erstellen, der Ihre Assets enthält.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Geben Sie im Bildset-Editor im Feld **[!UICONTROL Titel]** einen Namen für das Bildset ein. Der Name wird im Banner über dem Bildset angezeigt. Geben Sie optional eine Beschreibung ein.

   ![6_5_imageset-creating-newset](assets/6_5_imageset-creatingnewset.png)

1. Nehmen Sie eine der folgenden Aktionen vor:

   * Tippen Sie oben links auf der Seite des Bildset-Editors auf **[!UICONTROL Asset hinzufügen]**.

   * Tippen Sie in der Mitte des Bildset-Editors auf **[!UICONTROL Tippen, um den Asset-Wähler zu öffnen]**.
   Tippen Sie, um die gewünschten Assets für das Bildset auszuwählen. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie die Assets ausgewählt haben, tippen Sie auf **[!UICONTROL Auswählen]**.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie einen Suchbegriff eingeben und auf **[!UICONTROL Zurück]** tippen/klicken. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Ändern Sie die Ansicht, indem Sie das Symbol „Ansicht“ tippen und dann **[!UICONTROL Spaltenansicht]**, **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Listenansicht]** wählen.

   Siehe [Arbeiten mit Selektoren](/help/assets/working-with-selectors.md). 

   ![6_5_imageset_addingassets](assets/6_5_imageset-addingassets.png)

1. Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt.  Sie können die Assets nach dem Hinzufügen manuell neu anordnen oder sortieren.

   Ziehen Sie das Symbol zum Neuanordnen eines Assets ggf. rechts neben den Dateinamen des Assets, um Bilder in der Setliste nach oben oder unten zu bewegen.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Wenn Sie eine Miniaturansicht oder einen Musterabschnitt ändern möchten, klicken Sie neben dem Bild auf das Symbol **+** **Miniaturansicht** und navigieren Sie zur gewünschten Miniaturansicht bzw. zum gewünschten Musterabschnitt. Wenn Sie alle Bilder ausgewählt haben, klicken Sie auf **[!UICONTROL Speichern]**.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie ein Bild löschen möchten, wählen Sie das Bild aus und tippen Sie auf **[!UICONTROL Asset löschen]**.

   * Wenn Sie eine Vorgabe anwenden möchten, tippen Sie oben rechts auf **[!UICONTROL Vorgabe]**. Wählen Sie anschließend eine Vorgabe aus, um sie auf alle Elemente gleichzeitig anzuwenden.
   >[!NOTE]
   >
   >Beim Erstellen des Bildsets können Sie die Miniaturansicht des Bildsets ändern oder zulassen, dass AEM die Miniaturansicht anhand der Assets im Bildset automatisch auswählt. Um eine Miniaturansicht auszuwählen, tippen Sie auf der Seite „Bildset-Editor“ oberhalb des Felds „Titel“ auf **[!UICONTROL Miniaturansicht ändern]** und wählen Sie dann ein beliebiges Bild aus (Sie können auch zu anderen Ordnern navigieren, um nach Bildern zu suchen). Wenn Sie eine Miniaturansicht ausgewählt haben und dann entscheiden, dass AEM eine aus dem Bildset generieren soll, wählen Sie **[!UICONTROL Wechseln zu]** **[!UICONTROL Automatische Miniaturansicht]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Bildset wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Anzeigen von Bildsets  {#viewing-image-sets}

Sie können Bildsätze entweder in der Benutzeroberfläche oder automatisch über [Stapelsatzvorgaben](/help/assets/config-dms7.md#creating%20batch%20set%20presets%20to%20auto-generate%20image%20sets%20and%20spin%20sets) erstellen.

>[!IMPORTANT]
>
>Batch sets are created by the IPS [Image Production System] as part of asset ingestion and are available only in Dynamic Media - Scene7 mode.)

However, sets created using batch set presets, do *not* appear in the user interface. Sie können diese Sets auf drei verschiedene Arten anzeigen. (Diese Methoden sind auch verfügbar, wenn Sie die Bildsets in der Benutzeroberfläche erstellt haben.)

* Öffnen Sie die Eigenschaften eines einzelnen Assets. Die Eigenschaften zeigen an, auf welche Sets das ausgewählte Asset verweist oder welchen Sets es angehört. Klicken Sie auf den Namen des Sets, um das gesamte Set anzuzeigen. 

   ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties2.png)

* Aus einem Mitgliederbild eines Sets. Wählen Sie im Menü **[!UICONTROL Sets** die Sets aus, zu denen das Asset gehört.

   ![6_5_imageset-setspulldownmenu](assets/6_5_imageset-setspulldownmenu.png)

* In der Suche können Sie **[!UICONTROL Filter** auswählen, dann **[!UICONTROL Dynamische Medien** erweitern und Sie **[!UICONTROL Sets]** auswählen.

   Die Suche gibt als Ergebnis Sets zurück, die in der Benutzeroberfläche manuell oder mit Stapelsatzvorgaben automatisch erstellt wurden.  Im Gegensatz zu AEM-Suchen, die mit dem Suchkriterium „Enthält“ durchgeführt werden, wird die Suchabfrage für automatisierte Sets mithilfe des Suchkriteriums „Beginnt mit“ durchgeführt. Das Festlegen des Filters auf **[!UICONTROL Sätze]** ist die einzige Möglichkeit, automatisierte Sätze zu suchen.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Sets können über die Benutzeroberfläche angezeigt werden, wie unter [Bearbeiten von Bildsets](#editing-image-sets) beschrieben. 

## Bearbeiten von Bildsets {#editing-image-sets}

Sie können mehrere Bearbeitungsaufgaben für Bildsets ausführen, z. B. die folgenden:

* Fügen Sie dem Bildset Bilder hinzu.
* Ordnen Sie Bilder im Bildset neu an.
* Löschen Sie Assets im Bildset.
* Wenden Sie Viewer-Vorgaben an. 
* Löschen Sie das Bildset.

**So bearbeiten Sie Bildsets**

1. Führen Sie einen der folgenden Schritte aus:

   * Zeigen Sie mit der Maus auf ein Bildset-Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).
   * Zeigen Sie mit der Maus auf ein Bildset-Asset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.
   * Tippen Sie auf ein Bildset-Asset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie eine der folgenden Aktionen aus, um die Bilder im Bildset zu bearbeiten:

   * Ziehen Sie ein Bild, wenn Sie ein Asset an einer neuen Position anordnen möchten (zum Verschieben von Elementen wählen Sie das Symbol zum Neuanordnen).
   * Um Elemente in auf- oder absteigender Reihenfolge zu sortieren, klicken Sie auf die Spaltenüberschrift. 
   * Um ein Asset hinzuzufügen oder ein vorhandenes Asset zu aktualisieren, klicken Sie auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu einem Asset, wählen Sie es aus und tippen Sie oben rechts auf **[!UICONTROL Auswählen.]**
      >[!NOTE]
      >
      >Wenn Sie das in AEM als Miniaturansicht verwendete Bild löschen und durch ein anderes ersetzen, wird das Original-Asset weiterhin angezeigt.
   * Klicken oder tippen Sie zum Löschen eines Assets auf **[!UICONTROL Asset löschen]**. 
   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf der Seite auf **[!UICONTROL Vorgabe]** und wählen Sie eine Viewer-Vorgabe aus.
   * Um eine Miniaturansicht hinzuzufügen oder zu ändern, wählen Sie die Miniaturansicht rechts neben dem Asset. Navigieren Sie zur neuen Miniaturansicht oder zum neuen Farbmuster-Asset, wählen Sie es aus und tippen Sie dann auf **[!UICONTROL Auswählen]**.
   * Um ein ganzes Bildset zu löschen, navigieren Sie zum Bildset, wählen Sie es aus und klicken Sie auf **[!UICONTROL Löschen]**.
   >[!NOTE]
   >
   >Sie können die Bilder in einem Bildset bearbeiten, indem Sie zu dem Set navigieren, in der linken Leiste auf **[!UICONTROL Setmitglieder]** tippen und dann auf das Stiftsymbol eines Assets, um das Bearbeitungsfenster zu öffnen.

1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie die Bearbeitung abgeschlossen haben.

## Anzeigen von Bildsets in einer Vorschau {#previewing-image-sets}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](/help/assets/previewing-assets.md).

## Veröffentlichen von Bildsets {#publishing-image-sets}

Siehe [Veröffentlichen von Assets](/help/assets/publishing-dynamicmedia-assets.md).
