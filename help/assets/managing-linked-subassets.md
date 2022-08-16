---
title: Verwalten von ebenenübergreifenden Assets mit Verweisen und mehreren Seiten
description: Erfahren Sie, wie Sie Verweise auf digitale Assets in erstellen [!DNL Adobe InDesign], [!DNL Adobe Illustrator]und [!DNL Adobe Photoshop]. Verwenden Sie die Funktion "Seiten-Viewer", um einzelne Asset-Seiten mit mehrseitigen Dateien wie PDF-, INDD-, PPT-, PPTX- und AI-Dateien anzuzeigen.
contentOwner: AG
role: User, Admin
feature: Asset Management
exl-id: 1ea9d8fe-602c-452b-9a24-4125b705aedf
source-git-commit: 79d8b5896f5f8eb7a22dccea81acf0656d435f2b
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 17%

---

# Verwalten von ebenenübergreifenden und mehrseitigen Assets {#managing-compound-assets}

[!DNL Adobe Experience Manager Assets] kann erkennen, ob eine hochgeladene Datei Verweise auf Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. Wenn das hochgeladene Asset Verweise auf [!DNL Experience Manager] Assets erstellen, wird eine bidirektionale Verknüpfung zwischen den hochgeladenen und den referenzierten Assets erstellt.

Zusätzlich zur Eliminierung von Redundanz und zum Referenzieren der Assets in [!DNL Adobe Creative Cloud] Anwendungen verbessern die Zusammenarbeit und erhöhen die Effizienz und Produktivität der Benutzer.

[!DNL Experience Manager Assets] unterstützt bidirektionale Referenzierung. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus können Sie die referenzierenden Dateien auf der Asset-Detailseite des referenzierten Assets anzeigen.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## [!DNL Adobe Illustrator]: Hinzufügen digitaler Assets als Referenzen {#refai}

Sie können vorhandene digitale Assets aus einem [!DNL Adobe Illustrator] -Datei.

1. Verwenden [[!DNL Experience Manager] Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de), rufen Sie die digitalen Assets im lokalen Dateisystem ab. Navigieren Sie zum Dateisystemspeicherort des Assets, auf das Sie verweisen möchten.
1. Ziehen Sie das Asset aus dem lokalen Ordner in den [!DNL Illustrator] -Datei.

1. Speichern Sie die [!DNL Illustrator] Datei auf dem bereitgestellten Laufwerk oder [hochladen](/help/assets/manage-assets.md#uploading-assets) der [!DNL Experience Manager] Repository.

1. Nachdem der Workflow abgeschlossen ist, navigieren Sie zur Detailseite für das Asset. Die Referenzen zu vorhandenen digitalen Assets sind unter **[!UICONTROL Abhängigkeiten]** im **[!UICONTROL Verweise]** Spalte.

   ![chlimage_1-84](assets/chlimage_1-258.png)

1. Es ist auch möglich, dass andere Dateien als die aktuelle Datei auf die referenzierten Assets verweisen, die unter **[!UICONTROL Abhängigkeiten]** angezeigt werden. Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **[!UICONTROL Abhängigkeiten]** auf das Asset.

   ![chlimage_1-85](assets/chlimage_1-259.png)

1. Klicken **[!UICONTROL Eigenschaften anzeigen]** aus der Symbolleiste. Im [!UICONTROL Eigenschaften] Seite, wird die Liste der Dateien, die auf das aktuelle Asset verweisen, unter dem **[!UICONTROL Verweise]** in der Spalte **[!UICONTROL Allgemein]** Registerkarte.

   ![Anzeigen der Verweise von Experience Manager Assets in der Spalte &quot;Verweise&quot;in den Asset-Details](assets/asset-references.png)

   *Abbildung: Asset-Verweise in Asset-Details.*

## [!DNL Adobe InDesign]: Hinzufügen digitaler Assets als Referenzen {#add-aem-assets-as-references-in-adobe-indesign}

So referenzieren Sie digitale Assets aus einem [!DNL InDesign] -Datei, ziehen Sie entweder Assets in die [!DNL InDesign] Datei oder exportieren Sie die [!DNL InDesign] als ZIP-Archiv.

Referenzierte Assets sind bereits in [!DNL Experience Manager Assets]. Sie können Unter-Assets extrahieren, indem Sie [InDesign Server konfigurieren](indesign.md). Eingebettete Assets in einer [!DNL InDesign] -Datei werden als Teil-Assets extrahiert.

>[!NOTE]
>
>Wenn die Variable [!DNL InDesign Server] proximiert wird, [!DNL InDesign] -Dateien ihre Vorschau in ihre XMP Metadaten eingebettet. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. Wenn die [!DNL InDesign Server] nicht proximiert ist, müssen Miniaturansichten explizit extrahiert werden für [!DNL InDesign] Dateien.

Beim Hochladen einer INDD-Datei werden die Verweise abgerufen, indem Assets abgefragt werden, die `xmpMM:InstanceID` und `xmpMM:DocumentID` -Eigenschaft im Repository.

### Erstellen von Referenzen durch Ziehen von Assets {#create-references-by-dragging-aem-assets}

Dieses Verfahren ähnelt dem [Hinzufügen digitaler Assets als Referenzen in Adobe Illustrator](#refai).

### Erstellen von Referenzen zu Assets durch Exportieren einer ZIP-Datei {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Führen Sie die Schritte unter [Erstellen von Workflow-Modellen](/help/sites-developing/workflows-models.md) , um einen neuen Workflow zu erstellen.
1. Verwenden Sie die [Paketfunktion](https://helpx.adobe.com/indesign/how-to/indesign-package-files-for-handoff.html) von [!DNL Adobe InDesign] um das Dokument zu exportieren. [!DNL Adobe InDesign] kann ein Dokument und die verknüpften Assets als Paket exportieren. In diesem Fall enthält der exportierte Ordner eine `Links` Ordner, der Teil-Assets im [!DNL InDesign] -Datei. Die `Links` -Ordner befindet sich im selben Ordner wie die INDD-Datei.
1. Erstellen Sie eine ZIP-Datei und laden Sie sie in die [!DNL Experience Manager] Repository.
1. Starten Sie die `Unarchiver` Arbeitsablauf.
1. Nach Abschluss des Workflows werden die Referenzen im Ordner &quot;Links&quot;automatisch als Teil-Assets referenziert. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Asset-Detailseite der [!DNL InDesign] Asset und schließen Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

## [!DNL Adobe Photoshop]: Hinzufügen digitaler Assets als Referenzen {#refps}

1. Verwendung [!DNL Experience Manager] Desktop-Programm für den Zugriff [!DNL Experience Manager Assets]. Laden Sie die Assets herunter und zeigen Sie sie im lokalen Dateisystem an. Verwenden Sie die [!UICONTROL Platzieren von Links] Funktionalität in [!DNL Adobe Photoshop]. Siehe [Platzieren von Assets im Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#place-assets-in-native-documents).

1. Speichern in [!DNL Photoshop] Datei auf dem bereitgestellten Laufwerk oder [hochladen](/help/assets/manage-assets.md#uploading-assets) der [!DNL Experience Manager] Repository.
1. Nach Abschluss des Workflows werden die Verweise auf vorhandene [!DNL Experience Manager] -Assets werden auf der Asset-Detailseite aufgeführt.

   Rufen Sie die referenzierten Assets auf, indem Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector) auf der Asset-Detailseite schließen.

1. Die referenzierten Assets enthalten auch die Liste der Assets, von denen sie referenziert werden. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Asset-Detailseite und schließen Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Die Assets innerhalb der ebenenübergreifenden Assets können ebenfalls basierend auf ihrer Dokument-ID und ihrer Instanz-ID referenziert werden. Diese Funktion ist in [!DNL Adobe Illustrator] und [!DNL Adobe Photoshop] nur -Versionen. Für andere erfolgt der Verweis auf Basis des relativen Pfads verknüpfter Assets im Haupt-ebenenübergreifenden Asset, wie in früheren Versionen von [!DNL Experience Manager].

## Erstellen von Unter-Assets {#generate-subassets}

Für die unterstützten Assets mit mehrseitigen Formaten - PDF-Dateien, AI-Dateien, [!DNL Microsoft PowerPoint] und [!DNL Apple Keynote] Dateien und [!DNL Adobe InDesign] files — [!DNL Experience Manager] kann Teil-Assets generieren, die jeder einzelnen Seite des ursprünglichen Assets entsprechen. Diese Teil-Assets sind mit dem *parent* Asset und erleichtern die mehrseitige Ansicht. Für alle anderen Zwecke werden die Teilassets wie normale Vermögenswerte in [!DNL Experience Manager].

Die Erstellung von Unter-Assets ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Erstellung von Unter-Assets zu aktivieren:

1. Anmelden [!DNL Experience Manager] als Administrator. Zugriff **[!UICONTROL Instrumente]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Auswählen **[!UICONTROL DAM-Update-Asset]** Workflow und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Klicken **[!UICONTROL Seitliches Bedienfeld ein/aus]** und suchen Sie nach **[!UICONTROL Untergeordnetes Asset erstellen]** Schritt. Fügen Sie den Schritt zum Workflow hinzu. Klicken Sie auf **[!UICONTROL Synchronisieren]**.

Führen Sie einen der folgenden Schritte aus, um die Unter-Assets zu generieren:

* Neue Assets: Die [!UICONTROL DAM-Update von Assets] Der Workflow wird für jedes neue Asset ausgeführt, das in hochgeladen wird. [!DNL Experience Manager]. Teil-Assets werden automatisch für neue mehrseitige Assets generiert.
* Vorhandene mehrseitige Assets: Führen Sie die [!UICONTROL DAM-Update von Assets] einen der folgenden Schritte ausführen:

   * Wählen Sie ein Asset aus und klicken Sie auf [!UICONTROL Timeline] , um das linke Bedienfeld zu öffnen. Verwenden Sie alternativ den Tastaturbefehl `alt + 3`. Klicken [!UICONTROL Workflow starten]auswählen [!UICONTROL DAM-Update-Asset]klicken [!UICONTROL Starten]und klicken Sie auf [!UICONTROL Fortfahren].
   * Wählen Sie ein Asset aus und klicken Sie auf [!UICONTROL Erstellen] > [!UICONTROL Workflow] aus der Symbolleiste. Wählen Sie im Popup-Dialogfeld [!UICONTROL DAM-Update-Asset] Workflow, klicken Sie auf [!UICONTROL Starten]und klicken Sie auf [!UICONTROL Fortfahren].

Führen Sie speziell für Microsoft Word-Dokumente die **[!UICONTROL DAM-Analyse von Word-Dokumenten]** Arbeitsablauf. Es generiert eine `cq:Page` aus dem Inhalt des Microsoft Word-Dokuments. Die `cq:Page`-Komponente verweist auf die aus dem Dokument extrahierten Bilder. Diese Bilder werden auch dann extrahiert, wenn die Erstellung von Unter-Assets deaktiviert ist.

>[!NOTE]
>
>Im [!UICONTROL Prozess für untergeordnete Assets erstellen - Schritteigenschaften] in [!UICONTROL Prozess-Argumente]können Sie die Anzahl der Unter-Assets angeben, die [!DNL Experience Manager] generiert. Der Standardwert ist 5. Um alle Unter-Assets zu generieren, lassen Sie das Feld leer. Wenn das Feld negativ ist, werden keine Unter-Assets generiert.

## Anzeigen von Unter-Assets {#viewing-subassets}

Die Teil-Assets werden nur angezeigt, wenn die Teil-Assets generiert wurden und für das ausgewählte mehrseitige Asset verfügbar sind. Um die generierten Teil-Assets anzuzeigen, öffnen Sie das mehrseitige Asset. Klicken Sie oben links auf der Seite auf ![Option zum Öffnen der linken Leiste](assets/do-not-localize/aem_leftrail_contentonly.png) und klicken Sie auf **[!UICONTROL Unter-Assets]** aus der Liste. Wenn Sie **[!UICONTROL Unter-Assets]** aus der Liste. Verwenden Sie alternativ den Tastaturbefehl `alt + 5`.

![Anzeigen von Unter-Assets für ein mehrseitiges Asset](assets/view_subassets_simulation.gif)

## Anzeigen von Seiten einer mehrseitigen Datei  {#view-pages-of-a-multi-page-file}

Sie können eine mehrseitige Datei, z. B. PDF, INDD, PPT, PPTX und AI-Datei anzeigen, indem Sie die Funktion &quot;Seitenanzeige&quot;von [!DNL Experience Manager Assets]. Öffnen Sie ein mehrseitiges Asset und klicken Sie auf **[!UICONTROL Seiten anzeigen]** von der linken oberen Ecke der Seite aus. Der daraufhin geöffnete Seiten-Viewer zeigt die Seiten des Assets und die Steuerelemente zum Durchsuchen und Zoomen der einzelnen Seiten an.

![Anzeigen und Anzeigen von Seiten eines mehrseitigen Assets](assets/view_multipage_asset_fmr.gif)

Für [!DNL InDesign]können Sie Seiten mithilfe von extrahieren. [!DNL InDesign Server]. Wenn die Seitenvorschau gespeichert wird während [!DNL InDesign] Erstellung von Dateien und [!DNL InDesign Server] ist für die Seitenextraktion nicht erforderlich.

Die folgenden Optionen sind in der Symbolleiste, in der linken Leiste und in den Steuerelementen des Seiten-Viewers verfügbar:

* **[!UICONTROL Desktop-Aktionen]** , um ein bestimmtes Unter-Asset mit [!DNL Experience Manager] Desktop-Programm. Erfahren Sie, wie Sie [Konfigurieren von Desktop-Aktionen](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#desktopactions-v2) wenn Sie [!DNL Experience Manager] Desktop-Programm.

* **[!UICONTROL Eigenschaften]** -Option öffnet die [!UICONTROL Eigenschaften] Seite des bestimmten Unter-Assets.

* **[!UICONTROL Anmerken]** -Option können Sie das spezifische Unter-Asset kommentieren. Die Anmerkungen, die Sie für separate Unter-Assets verwenden, werden erfasst und zusammen angezeigt, wenn das übergeordnete Asset zur Anzeige geöffnet wird.

* **[!UICONTROL Seitenübersicht]** -Option zeigt alle Teil-Assets gleichzeitig an.

* **[!UICONTROL Timeline]** Option in der linken Leiste nach dem Klicken auf ![Option zum Öffnen der linken Leiste](assets/do-not-localize/aem_leftrail_contentonly.png) zeigt den Aktivitäts-Stream für die Datei an.

## Best Practices und Einschränkungen {#best-practice-limitation-tips}

* Die Erstellung von Unter-Assets kann für jede beliebige [!DNL Experience Manager] Implementierung. Wenn Sie Teil-Assets generieren, wenn komplexe Assets hochgeladen werden, fügen Sie den Schritt im Workflow DAM-Update-Asset hinzu. Wenn Sie Teil-Assets On-Demand generieren, erstellen Sie einen separaten Workflow zum Generieren von Teil-Assets. Mit einem speziellen Workflow können Sie die anderen Schritte im Workflow DAM-Update-Asset überspringen und Rechenressourcen speichern.

>[!MORELIKETHIS]
>
>* [Verwenden des Adobe Experience Manager-Desktop-Programms](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [Konfigurieren von Desktop-Aktionen in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2)
>* [Verknüpfte Smart-Objekte in Adobe Photoshop erstellen](https://helpx.adobe.com/photoshop/using/create-smart-objects.html#create-linked-smart-objects)
>* [Platzieren von Grafiken in Adobe InDesign](https://helpx.adobe.com/de/indesign/using/placing-graphics.html)

