---
title: Verwalten Sie zusammengesetzte Assets mit Verweisen und mehrseitigen Assets in [!DNL Adobe Experience Manager].
description: Hier erfahren Sie, wie Sie Verweise auf digitale Assets von innen [!DNL Adobe InDesign], [!DNL Adobe Illustrator], and [!DNL Adobe Photoshop]aus erstellen. Verwenden Sie die Funktion "Seiten-Viewer", um einzelne Seiten von Teilassets von mehrseitigen Dateien wie PDF-, INDD-, PPT-, PPTX- und AI-Dateien Ansicht.
contentOwner: AG
translation-type: tm+mt
source-git-commit: d90a95195a97a1840e1defb49d2a09ffbd3c8650
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 17%

---


# Verwalten von zusammengesetzten und mehrseitigen Assets {#managing-compound-assets}

[!DNL Adobe Experience Manager Assets] kann identifizieren, ob eine hochgeladene Datei Verweise auf Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. If the uploaded asset contains any references to [!DNL Experience Manager] assets, a bidirectional link is created between the uploaded and referenced assets.

Besides eliminating redundancy, referencing the assets in [!DNL Adobe Creative Cloud] applications enhances collaboration and increases the efficiency and productivity of users.

[!DNL Experience Manager Assets] unterstützt bidirektionale Verweise. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus können Sie die referenzierenden Dateien auf der Seite mit den Asset-Details des referenzierten Assets Ansicht haben.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## Hinzufügen digitaler Assets als Referenz in [!DNL Adobe Illustrator] {#refai}

You can reference existing digital assets from within an [!DNL Adobe Illustrator] file.

1. Rufen Sie mithilfe der [Experience Manager-Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)die digitalen Assets im lokalen Dateisystem ab. Navigieren Sie zum Dateisystemspeicherort des Assets, auf den Sie verweisen möchten.
1. Ziehen Sie das Asset aus dem lokalen Ordner in die [!DNL Illustrator] Datei.

1. Save the [!DNL Illustrator] file to the mounted drive, or [upload](/help/assets/managing-assets-touch-ui.md#uploading-assets) to the [!DNL Experience Manager] repository.

1. Nachdem der Workflow abgeschlossen ist, navigieren Sie zur Detailseite für das Asset. The references to existing digital assets are listed under **[!UICONTROL Dependencies]** in the **[!UICONTROL References]** column.

   ![chlimage_1-84](assets/chlimage_1-258.png)

1. Es ist auch möglich, dass andere Dateien als die aktuelle Datei auf die referenzierten Assets verweisen, die unter **[!UICONTROL Abhängigkeiten]** angezeigt werden. Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **[!UICONTROL Abhängigkeiten]** auf das Asset.

   ![chlimage_1-85](assets/chlimage_1-259.png)

1. Click **[!UICONTROL View Properties]** from the toolbar. In the [!UICONTROL Properties] page, the list of files that reference the current asset appear under the **[!UICONTROL References]** column in the **[!UICONTROL Basic]** tab.

   ![Ansicht der Verweise auf Experience Manager-Assets in der Spalte &quot;Verweise&quot;in den Asset-Details](assets/asset-references.png)

   *Abbildung: Asset-Verweise in den Asset-Details.*

## Hinzufügen digitaler Assets als Referenz in [!DNL Adobe InDesign] {#add-aem-assets-as-references-in-adobe-indesign}

To reference digital assets from within an [!DNL InDesign] file, either drag assets to the [!DNL InDesign] file or export the [!DNL InDesign] file as a ZIP archive.

Referenced assets already exist in [!DNL Experience Manager Assets]. You can extract subassets by [configuring InDesign Server](indesign.md). Embedded assets in an [!DNL InDesign] file are extracted as subassets.

>[!NOTE]
>
>If the [!DNL InDesign Server] is proxied, [!DNL InDesign] files have their preview embedded within their XMP metadata. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. However, if the [!DNL InDesign Server] is not proxied, thumbnails must be explicitly extracted for [!DNL InDesign] files.

### Create references by dragging assets {#create-references-by-dragging-aem-assets}

This procedure is similar to [add digital assets as references in Adobe Illustrator](#refai).

### Erstellen von Referenzen zu Assets durch Exportieren einer ZIP-Datei {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Perform the steps in [Create workflow models](/help/sites-developing/workflows-models.md) to create a new workflow.
1. Use the Package feature of [!DNL Adobe InDesign] to export the document. [!DNL Adobe InDesign] kann ein Dokument und die verknüpften Assets als Paket exportieren. In this case, the exported folder contains a Links folder that contains sub-assets in the [!DNL InDesign] file.
1. Create a ZIP file and upload it to the [!DNL Experience Manager] repository.
1. Start the `Unarchiver` workflow.
1. Nach Abschluss des Workflows werden die Verweise im Ordner &quot;Links&quot;automatisch als Teilassets referenziert. To view a list of referred assets, navigate to the asset details page of the [!DNL InDesign] asset and close the [Rail](/help/sites-authoring/basic-handling.md#rail-selector).

## Hinzufügen digitaler Assets als Referenz in [!DNL Adobe Photoshop] {#refps}

1. Verwenden Sie die [!DNL Experience Manager] Desktop-App, um darauf zuzugreifen [!DNL Experience Manager Assets]. Laden Sie die Assets herunter und zeigen Sie sie auf dem lokalen Dateisystem an. Verwenden Sie die Funktion [!UICONTROL Linked] platzieren in [!DNL Adobe Photoshop]. Siehe [Platzieren von Assets in der Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#place-assets-in-native-documents).

   ![chlimage_1-87](assets/chlimage_1-261.png)

1. Save in [!DNL Photoshop] file to the mounted drive or or [upload](/help/assets/managing-assets-touch-ui.md#uploading-assets) to the [!DNL Experience Manager] repository.
1. After the workflow completes, the references to existing [!DNL Experience Manager] assets are listed in the asset details page.

   Rufen Sie die referenzierten Assets auf, indem Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector) auf der Asset-Detailseite schließen.

1. Die referenzierten Assets enthalten auch die Liste der Assets, von denen sie referenziert werden. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Asset-Detailseite und schließen Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Die Assets innerhalb der ebenenübergreifenden Assets können ebenfalls basierend auf ihrer Dokument-ID und ihrer Instanz-ID referenziert werden. This functionality is available with [!DNL Adobe Illustrator] and [!DNL Adobe Photoshop] versions only. For others, referencing is done on the basis of relative path of linked assets in the main compound asset as done in earlier versions of [!DNL Experience Manager].

## Erstellen von Teilassets {#generate-subassets}

Für die unterstützten Assets mit mehrseitigen Formaten — PDF-Dateien, AI-Dateien [!DNL Microsoft PowerPoint] und [!DNL Apple Keynote] -Dateien und [!DNL Adobe InDesign] -Dateien — [!DNL Experience Manager] können Teilassets generieren, die jeder einzelnen Seite des ursprünglichen Assets entsprechen. Diese Teilassets sind mit dem *übergeordneten* Asset verknüpft und erleichtern die mehrseitige Ansicht. Für alle anderen Zwecke werden die Teilassachen wie normale Aktiva in [!DNL Experience Manager]behandelt.

Die Erstellung von Unter-Assets ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Erzeugung von Teilassets zu aktivieren:

1. Log into [!DNL Experience Manager] as an administrator. Access **[!UICONTROL Tools > Workflow > Models]**.
1. Wählen Sie **[!UICONTROL DAM Update Asset]** Workflow und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf **[!UICONTROL Seitenbedienfeld]** umschalten und suchen Sie den Schritt &quot;Unterelement **[!UICONTROL erstellen&quot;]** . Hinzufügen den Schritt zum Workflow. Klicken Sie auf **[!UICONTROL Synchronisieren]**.

Führen Sie zum Generieren der Teilassets einen der folgenden Schritte aus:

* Neue Assets: Der Arbeitsablauf [!UICONTROL DAM-Aktualisierung für Assets] wird für alle neuen Assets ausgeführt, auf die hochgeladen wird [!DNL Experience Manager]. Teilassets werden automatisch für neue mehrseitige Assets generiert.
* Vorhandene mehrseitige Assets: Führen Sie den Arbeitsablauf [!UICONTROL DAM Update Assets] manuell aus, indem Sie einen der folgenden Schritte ausführen:

   * Wählen Sie ein Asset aus und klicken Sie auf [!UICONTROL Zeitschiene] , um das linke Bedienfeld zu öffnen. Alternately, use the keyboard shortcut `alt + 3`. Klicken Sie auf [!UICONTROL Beginn Workflow], wählen Sie [!UICONTROL DAM Update Asset], klicken Sie auf [!UICONTROL Beginn]und dann auf [!UICONTROL Fortfahren].
   * Wählen Sie ein Asset aus und klicken Sie in der Symbolleiste auf [!UICONTROL Erstellen > Workflow] . Wählen Sie im Popup-Dialogfeld [!UICONTROL DAM Update Asset] Workflow, klicken Sie auf [!UICONTROL Beginn]und dann auf [!UICONTROL Fortfahren].

Führen Sie insbesondere für Microsoft Word-Dokumente den Arbeitsablauf **[!UICONTROL DAM Parse Word-Dokumente]** aus. Es wird eine `cq:Page` Komponente aus dem Inhalt des Microsoft Word-Dokuments generiert. Die `cq:Page`-Komponente verweist auf die aus dem Dokument extrahierten Bilder. Diese Bilder werden auch dann extrahiert, wenn die Erstellung von Unter-Assets deaktiviert ist.

## Anzeigen von Unter-Assets {#viewing-subassets}

Die Teilassets werden nur angezeigt, wenn die Teilassets generiert wurden und für das ausgewählte mehrseitige Asset verfügbar sind. Um die generierten Teilassets Ansicht, öffnen Sie das mehrseitige Asset. Klicken Sie im oberen linken Seitenbereich auf das Symbol ![für die](assets/do-not-localize/aem_leftrail_contentonly.png) linke Leiste und klicken Sie in der Liste auf &quot; **[!UICONTROL Teilassets]** &quot;. Wenn Sie **[!UICONTROL Teilassets]** aus der Liste auswählen. Alternately, use the keyboard shortcut `alt + 5`.

![Ansichten-Teilassets für ein mehrseitiges Asset](assets/view_subassets_simulation.gif)

## Anzeigen von Seiten einer mehrseitigen Datei  {#view-pages-of-a-multi-page-file}

Sie können eine mehrseitige Datei, wie z. B. PDF, INDD, PPT, PPTX und AI, mit der Funktion &quot;Seiten-Viewer&quot;von [!DNL Experience Manager Assets]. Öffnen Sie ein mehrseitiges Asset und klicken Sie links oben auf der Seite auf &quot; **[!UICONTROL Ansichten]** &quot;. Der daraufhin geöffnete Seiten-Viewer zeigt die Seiten des Assets und die Steuerelemente zum Durchsuchen und Zoomen der einzelnen Seiten an.

![Ansicht und Anzeige von Seiten eines mehrseitigen Assets](assets/view_multipage_asset_fmr.gif)

Sie [!DNL InDesign]können z. B. Seiten mithilfe von [!DNL InDesign Server]extrahieren. If the previews of pages are saved during [!DNL InDesign] file creation, then [!DNL InDesign Server] is not required for page extraction.

Die folgenden Optionen stehen in der Symbolleiste, in der linken Leiste und in den Seiten-Viewer-Steuerelementen zur Verfügung:

* **[!UICONTROL Desktop-Aktionen]** zum Öffnen oder Einblenden eines bestimmten Unterassets mit der [!DNL Experience Manager] Desktop-App. Erfahren Sie, wie Sie Desktop-Aktionen [](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#desktopactions-v2) konfigurieren, wenn Sie die [!DNL Experience Manager] Desktop-App verwenden.

* **[!UICONTROL Mit der Option &quot;Eigenschaften]** &quot;wird die Seite &quot; [!UICONTROL Eigenschaften] &quot;des jeweiligen Unterassets geöffnet.

* **[!UICONTROL Mit der Option &quot;Anmerkung]** &quot;können Sie das spezifische Unterelement kommentieren. Die Anmerkungen, die Sie in separaten Teilassets verwenden, werden zusammen erfasst und angezeigt, wenn das übergeordnete Asset zur Ansicht geöffnet wird.

* **[!UICONTROL Die Option &quot;Seitenübersicht]** &quot;zeigt alle Teilassets gleichzeitig an.

* **[!UICONTROL Die Option &quot;Zeitschiene]** &quot;in der linken Leiste nach dem Klicken auf das Symbol ![für die](assets/do-not-localize/aem_leftrail_contentonly.png) linke Leiste zeigt den Dateistream an.

## Best practices and limitation {#best-practice-limitation-tips}

* Die Erzeugung von Teilassets kann bei jeder Experience Manager-Bereitstellung sehr ressourcenintensiv sein. Wenn Sie beim Hochladen komplexer Assets Teilassets generieren, fügen Sie den Schritt im DAM-Arbeitsablauf zum Aktualisieren von Assets hinzu. Wenn Sie bei Bedarf Teilassets erstellen, erstellen Sie einen separaten Workflow, um Teilassets zu generieren. Ein dedizierter Arbeitsablauf ermöglicht es Ihnen, die anderen Schritte im DAM Update Asset-Arbeitsablauf zu überspringen und Rechenressourcen zu speichern.

>[!MORELIKETHIS]
>
>* [Verwenden des Adobe Experience Manager-Desktop-Programms](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html)
>* [Konfigurieren von Desktop-Aktionen in Adobe Experience Manager](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#desktopactions-v2)
>* [Verknüpfte Smartobjekte in Adobe Fotoshop erstellen](https://helpx.adobe.com/photoshop/using/create-smart-objects.html#create-linked-smart-objects)
>* [Platzieren von Grafiken in Adobe InDesign](https://helpx.adobe.com/de/indesign/using/placing-graphics.html)