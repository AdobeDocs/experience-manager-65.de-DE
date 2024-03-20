---
title: Verwalten von ebenenübergreifenden Assets mit Verweisen und mehreren Seiten
description: Erfahren Sie, wie Sie Verweise auf digitale Assets in [!DNL Adobe InDesign], [!DNL Adobe Illustrator] und [!DNL Adobe Photoshop] erstellen. Verwenden Sie den Seiten-Viewer, um einzelne Asset-Seiten mit mehrseitigen Dateien wie PDF-, INDD-, PPT-, PPTX- und AI-Dateien anzuzeigen.
contentOwner: AG
role: User, Admin
feature: Asset Management
exl-id: 1ea9d8fe-602c-452b-9a24-4125b705aedf
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 97%

---

# Verwalten von ebenenübergreifenden und mehrseitigen Assets {#managing-compound-assets}

[!DNL Adobe Experience Manager Assets] kann erkennen, ob eine hochgeladene Datei Referenzen zu Assets enthält, die bereits im Repository vorhanden sind. Diese Funktion ist nur für unterstützte Dateiformate verfügbar. Wenn das hochgeladene Asset Referenzen zu [!DNL Experience Manager]-Assets enthält, wird eine bidirektionale Verknüpfung zwischen dem hochgeladenen Asset und den referenzierten Assets erstellt.

Durch die Referenzierung von AEM-Assets in [!DNL Adobe Creative Cloud]-Anwendungen wird Redundanz beseitigt und die Zusammenarbeit verbessert und die Effizienz und Produktivität der Benutzerinnen und Benutzer werden gesteigert.

[!DNL Experience Manager Assets] unterstützt die bidirektionale Referenzierung. Referenzierte Assets finden Sie auf der Asset-Detailseite der hochgeladenen Datei. Darüber hinaus finden Sie die referenzierenden Dateien auf der Asset-Detailseite des referenzierten Assets.

Referenzen werden auf der Grundlage von Pfad, Dokument-ID und Instanz-ID der referenzierten Assets aufgelöst.

## [!DNL Adobe Illustrator]: Hinzufügen digitaler Assets als Referenzen {#refai}

Sie können vorhandene digitale Assets in einer [!DNL Adobe Illustrator]-Datei referenzieren.

1. Rufen Sie unter Verwendung des [[!DNL Experience Manager] -Desktop-Programms](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de) die digitalen Assets im lokalen Dateisystem ab. Navigieren Sie zum Speicherort der Assets, die Sie referenzieren möchten.
1. Ziehen Sie das Asset aus dem lokalen Ordner in die [!DNL Illustrator]-Datei.

1. Speichern Sie die [!DNL Illustrator]-Datei im bereitgestellten Laufwerk oder [laden](/help/assets/manage-assets.md#uploading-assets) Sie sie in das [!DNL Experience Manager]-Repository hoch.

1. Nachdem der Workflow abgeschlossen ist, navigieren Sie zur Detailseite für das Asset. Die Referenzen zu vorhandenen digitalen Assets werden unter **[!UICONTROL Abhängigkeiten]** in der Spalte **[!UICONTROL Verweise]** aufgeführt.

   ![chlimage_1-84](assets/chlimage_1-258.png)

1. Es ist auch möglich, dass andere Dateien als die aktuelle Datei auf die referenzierten Assets verweisen, die unter **[!UICONTROL Abhängigkeiten]** angezeigt werden. Um eine Liste der referenzierenden Dateien für ein Asset anzuzeigen, klicken Sie unter **[!UICONTROL Abhängigkeiten]** auf das Asset.

   ![chlimage_1-85](assets/chlimage_1-259.png)

1. Klicken Sie auf der Symbolleiste auf **[!UICONTROL Eigenschaften anzeigen]**. Auf der Seite [!UICONTROL Eigenschaften] wird die Liste der Dateien, die das aktuelle Asset referenzieren, auf der Registerkarte **[!UICONTROL Allgemein]** unter der Spalte **[!UICONTROL Verweise]** angezeigt.

   ![Verweise von Experience Manager Assets in der Spalte „Verweise“ in den Asset-Details anzeigen](assets/asset-references.png)

   *Abbildung: Asset-Verweise in Asset-Details.*

## [!DNL Adobe InDesign]: Hinzufügen digitaler Assets als Referenzen {#add-aem-assets-as-references-in-adobe-indesign}

Um digitale Assets aus einer [!DNL InDesign]-Datei zu referenzieren, ziehen Sie die Assets auf die [!DNL InDesign]-Datei oder exportieren Sie die [!DNL InDesign]-Datei als ZIP-Datei.

Referenzierte Assets sind bereits in [!DNL Experience Manager Assets] enthalten. Sie können Unter-Assets extrahieren, indem Sie den [InDesign Server konfigurieren](indesign.md). Eingebettete Assets in einer [!DNL InDesign]-Datei werden als Unter-Assets extrahiert.

>[!NOTE]
>
>Wenn der [!DNL InDesign Server] einen Proxyserver hat, wird die Vorschau von [!DNL InDesign]-Dateien innerhalb der XMP-Metadaten eingebettet. In diesem Fall ist die Extraktion von Miniaturen nicht explizit erforderlich. Wenn der [!DNL InDesign Server] keinen Proxyserver hat, müssen Miniaturen für [!DNL InDesign]-Dateien explizit extrahiert werden.

Beim Hochladen einer INDD-Datei werden die Verweise abgerufen, indem Assets mit den Eigenschaften `xmpMM:InstanceID` und `xmpMM:DocumentID` im Repository abgefragt werden.

### Erstellen von Referenzen durch Ziehen von Assets {#create-references-by-dragging-aem-assets}

Dieses Verfahren weist Ähnlichkeiten mit dem [Hinzufügen digitaler Assets als Referenzen in Adobe Illustrator](#refai) auf.

### Erstellen von Referenzen zu Assets durch Exportieren einer ZIP-Datei {#create-references-to-aem-assets-by-exporting-a-zip-file}

1. Führen Sie die Schritte unter [Workflow-Modelle erstellen](/help/sites-developing/workflows-models.md) , um einen Workflow zu erstellen.
1. Exportieren Sie das Dokument mit der [Paketfunktion](https://helpx.adobe.com/indesign/how-to/save-share-projects.html) von [!DNL Adobe InDesign]. [!DNL Adobe InDesign] kann ein Dokument und die verknüpften Assets als Paket exportieren. In diesem Fall enthält der exportierte Ordner einen `Links`-Ordner, der Unter-Assets in der [!DNL InDesign]-Datei enthält. Der `Links`-Ordner befindet sich im selben Ordner wie die INDD-Datei.
1. Erstellen Sie eine ZIP-Datei und laden Sie sie in das [!DNL Experience Manager]-Repository hoch.
1. Starten Sie den `Unarchiver`-Workflow.
1. Wenn der Workflow abgeschlossen ist, werden die Verweise im Links-Ordner automatisch als Unter-Assets referenziert. Rufen Sie eine Liste der referenzierten Assets auf, indem Sie zur Asset-Detailseite des [!DNL InDesign]-Assets navigieren und die [Seitenleiste](/help/sites-authoring/basic-handling.md#rail-selector) schließen.

## [!DNL Adobe Photoshop]: Hinzufügen digitaler Assets als Referenzen {#refps}

1. Verwenden Sie das [!DNL Experience Manager]-Desktop-Programm, um auf [!DNL Experience Manager Assets] zuzugreifen. Laden Sie die Assets herunter und zeigen Sie sie im lokalen Dateisystem an. Verwenden Sie die Funktion [!UICONTROL Platzieren von Links] in [!DNL Adobe Photoshop]. Siehe [Platzieren von Assets im Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#place-assets-in-native-documents).

1. Speichern Sie die [!DNL Photoshop]-Datei auf dem bereitgestellten Laufwerk oder [laden](/help/assets/manage-assets.md#uploading-assets) Sie sie in das [!DNL Experience Manager]-Repository hoch.
1. Nach Abschluss des Workflows werden die Verweise auf vorhandene [!DNL Experience Manager]-Assets auf der Asset-Detailseite aufgeführt.

   Rufen Sie die referenzierten Assets auf, indem Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector) auf der Asset-Detailseite schließen.

1. Die referenzierten Assets enthalten auch die Liste der Assets, von denen sie referenziert werden. Um eine Liste der referenzierten Assets anzuzeigen, navigieren Sie zur Asset-Detailseite und schließen Sie die [Leiste](/help/sites-authoring/basic-handling.md#rail-selector).

>[!NOTE]
>
>Die Assets innerhalb der ebenenübergreifenden Assets können ebenfalls basierend auf ihrer Dokument-ID und ihrer Instanz-ID referenziert werden. Diese Funktion ist nur in [!DNL Adobe Illustrator] und [!DNL Adobe Photoshop] verfügbar. Bei anderen Versionen erfolgt die Referenzierung basierend auf dem relativen Pfad von verknüpften Assets im ebenenübergreifenden Haupt-Asset, wie das auch bei früheren Versionen von [!DNL Experience Manager] der Fall war.

## Erstellen von Unter-Assets {#generate-subassets}

Für unterstützte Assets mit mehrseitigen Formaten – PDF-Dateien, AI-Dateien, [!DNL Microsoft PowerPoint]- und [!DNL Apple Keynote]-Dateien sowie [!DNL Adobe InDesign]-Dateien – kann [!DNL Experience Manager] Unter-Assets für jede einzelne Seite des ursprünglichen Assets generieren. Diese Unter-Assets sind mit dem *übergeordneten* Asset verknüpft und ermöglichen die mehrseitige Anzeige. Für alle anderen Zwecke werden die Unter-Assets in [!DNL Experience Manager] wie normale Assets behandelt.

Die Erstellung von Unter-Assets ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um die Erstellung von Unter-Assets zu aktivieren:

1. Melden Sie sich in [!DNL Experience Manager] als Admin an. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Wählen Sie den Workflow **[!UICONTROL DAM-Update-Asset]** aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf **[!UICONTROL Seitliches Bedienfeld ein/aus]** und suchen Sie nach dem Schritt **[!UICONTROL Untergeordnetes Asset erstellen]**. Fügen Sie den Schritt zum Workflow hinzu. Klicken Sie auf **[!UICONTROL Synchronisieren]**.

Führen Sie einen der folgenden Schritte aus, um die Assets zu generieren:

* Neue Assets: Der Workflow [!UICONTROL DAM-Update-Asset] wird für jedes neue Asset ausgeführt, das in [!DNL Experience Manager] hochgeladen wird. Für neue mehrseitige Assets werden automatisch Unter-Assets generiert.
* Vorhandene mehrseitige Assets: Führen Sie den Workflow [!UICONTROL DAM-Update-Asset] im Anschluss an einen der folgenden Schritte aus:

   * Wählen Sie ein Asset aus und klicken Sie auf [!UICONTROL Zeitleiste], um den linken Bereich zu öffnen. Sie können auch den Tastaturbefehl `alt + 3` verwenden. Klicken Sie auf [!UICONTROL Workflow starten], wählen Sie [!UICONTROL DAM-Update-Asset] aus, klicken Sie auf [!UICONTROL Starten] und anschließend auf [!UICONTROL Fortfahren].
   * Wählen Sie ein Asset aus und klicken Sie auf der Symbolleiste auf [!UICONTROL Erstellen] > [!UICONTROL Workflow]. Wählen Sie im Popup-Dialogfeld den Workflow [!UICONTROL DAM-Update-Asset] aus, klicken Sie auf [!UICONTROL Starten] und dann auf [!UICONTROL Fortfahren].

Führen Sie speziell für Microsoft Word-Dokumente den Workflow **[!UICONTROL DAM-Analyse von Word-Dokumenten]** aus. Er generiert eine `cq:Page`-Komponente aus dem Inhalt des Microsoft Word-Dokuments. Die `cq:Page`-Komponente verweist auf die aus dem Dokument extrahierten Bilder. Diese Bilder werden auch dann extrahiert, wenn die Erstellung von Unter-Assets deaktiviert ist.

>[!NOTE]
>
>Unter [!UICONTROL Prozess für untergeordnete Assets erstellen – Schritteigenschaften] in [!UICONTROL Prozess-Argumente] können Sie die Anzahl der Unter-Assets angeben, die [!DNL Experience Manager] generiert. Der Standardwert ist 5. Um alle Unter-Assets zu generieren, lassen Sie das Feld leer. Wenn das Feld einen negativen Wert enthält, werden keine Unter-Assets generiert.

## Anzeigen von Unter-Assets {#viewing-subassets}

Die Unter-Assets werden nur angezeigt, wenn sie generiert wurden und für das ausgewählte mehrseitige Asset verfügbar sind. Um die generierten Unter-Assets anzuzeigen, öffnen Sie das mehrseitige Asset. Klicken Sie oben links auf der Seite auf ![Option zum Öffnen der linken Leiste](assets/do-not-localize/aem_leftrail_contentonly.png) und klicken Sie dann in der Liste auf **[!UICONTROL Unter-Assets]**. Wählen Sie **[!UICONTROL Unter-Assets]** aus der Liste aus. Sie können auch den Tastaturbefehl `alt + 5` verwenden.

![Anzeigen von Unter-Assets für ein mehrseitiges Asset](assets/view_subassets_simulation.gif)

## Anzeigen von Seiten einer mehrseitigen Datei  {#view-pages-of-a-multi-page-file}

Sie können eine mehrseitige Datei, z. B. eine PDF-, INDD-, PPT-, PPTX- oder AI-Datei, mithilfe des Seiten-Viewers von [!DNL Experience Manager Assets] anzeigen. Öffnen Sie ein mehrseitiges Asset und klicken Sie links oben auf der Seite auf **[!UICONTROL Seiten anzeigen]**. Der daraufhin geöffnete Seiten-Viewer zeigt die Seiten des Assets und Steuerelemente zum Durchsuchen und Zoomen der einzelnen Seiten an.

![Anzeigen der Seiten eines mehrseitigen Assets](assets/view_multipage_asset_fmr.gif)

Für [!DNL InDesign] können Sie Seiten mithilfe von [!DNL InDesign Server] extrahieren. Wenn die Vorschau von Seiten beim Erstellen einer [!DNL InDesign]-Datei gespeichert wird, ist der [!DNL InDesign Server] nicht für die Seitenextraktion erforderlich.

Die folgenden Optionen sind auf der Symbolleiste, in der linken Leiste und in den Steuerelementen des Seiten-Viewers verfügbar:

* **[!UICONTROL Desktop-Aktionen]**, um ein bestimmtes Unter-Asset mit dem [!DNL Experience Manager]-Desktop-Programm zu öffnen oder anzuzeigen. Erfahren Sie, wie Sie [Desktop-Aktionen konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#desktopactions-v2), wenn Sie das [!DNL Experience Manager]-Desktop-Programm verwenden.

* Die Option **[!UICONTROL Eigenschaften]** öffnet die Seite [!UICONTROL Eigenschaften] des Unter-Assets.

* Mit der Option **[!UICONTROL Anmerken]** können Sie das spezifische Unterelement kommentieren. Die Anmerkungen, die Sie für separate Unter-Assets verwenden, werden erfasst und zusammen angezeigt, wenn das übergeordnete Asset zur Anzeige geöffnet wird.

* Die Option **[!UICONTROL Seitenübersicht]** zeigt alle Unter-Assets gleichzeitig an.

* Nachdem auf ![Option zum Öffnen der linken Leiste](assets/do-not-localize/aem_leftrail_contentonly.png) geklickt wurde, zeigt die Option **[!UICONTROL Zeitleiste]** in der linken Leiste den Aktivitäts-Stream für die Datei an.

## Best Practices und Einschränkungen {#best-practice-limitation-tips}

* Die Erstellung von Unter-Assets kann bei jeder [!DNL Experience Manager]-Bereitstellung äußerst ressourcenintensiv sein. Wenn Sie Unter-Assets generieren, während komplexe Assets hochgeladen werden, fügen Sie den Schritt im Workflow „DAM-Update-Asset“ hinzu. Wenn Sie Unter-Assets On-Demand generieren, erstellen Sie einen separaten Workflow, um Unter-Assets zu generieren. Mit einem speziellen Workflow können Sie die anderen Schritte im Workflow „DAM-Update-Asset“ überspringen und dadurch Rechenressourcen sparen.

>[!MORELIKETHIS]
>
>* [Verwenden des Adobe Experience Manager-Desktop-Programms](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de)
>* [Konfigurieren von Desktop-Aktionen in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#desktopactions-v2)
>* [Erstellen von verknüpften Smart-Objekten in Adobe Photoshop](https://helpx.adobe.com/de/photoshop/using/create-smart-objects.html#create-linked-smart-objects)
>* [Platzieren von Grafiken in Adobe InDesign](https://helpx.adobe.com/de/indesign/using/placing-graphics.html)
