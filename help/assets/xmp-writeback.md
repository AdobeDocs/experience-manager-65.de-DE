---
title: XMP-Writeback in Ausgabeformaten
description: Erfahren Sie, wie die XMP-Writeback-Funktion die Metadaten für ein Asset an alle oder spezifische Ausgabeformate des Elements propagiert.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 63%

---


# XMP-Writeback in Ausgabeformaten {#xmp-writeback-to-renditions}

The XMP writeback feature in [!DNL Adobe Experience Manager Assets] replicates asset metadata changes to the renditions of the asset. When you change the metadata for an asset from within [!DNL Experience Manager Assets] or while uploading the asset, changes are initially stored within the asset node in CRXDe. Die XMP-Funktion zum Speichern von Schriftstücken propagiert die Änderungen der Metadaten an alle oder bestimmte Darstellungen des Assets.

Stellen Sie sich vor, Sie ändern die Eigenschaft [!UICONTROL Titel] des Assets `Classic Leather` in `Nylon`.

![Metadaten](assets/metadata.png)

In this case, the [!DNL Experience Manager Assets] saves the changes to the **[!UICONTROL Title]** property in the `dc:title` parameter for the asset metadata stored in the asset hierarchy.

![metadata_stored](assets/metadata_stored.png)

However, [!DNL Experience Manager Assets] does not automatically propagate any metadata changes to the renditions of an asset.

Mit der XMP-Funktion &quot;Schriftarterfassung&quot;können Sie die Metadatenänderungen an alle oder bestimmte Darstellungen des Assets weiterleiten. Die Änderungen werden allerdings nicht unter dem Metadatenknoten in der Asset-Hierarchie gespeichert. Stattdessen werden die Änderungen mit dieser Funktion in die Binärdateien für die Ausgabeformate eingebettet.

## Aktivieren von XMP-Writeback {#enabling-xmp-writeback}

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]** in Configuration Manager.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Wählen Sie die Option **[!UICONTROL Propagate XMP[!UICONTROL **, und speichern Sie die Änderungen.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Aktivieren von XMP-Writeback für bestimmte Ausgabeformate {#enabling-xmp-writeback-for-specific-renditions}

To let the XMP Writeback feature propagate metadata changes to select renditions, specify these renditions to the XMP Writeback Process workflow step of [!UICONTROL DAM Metadata WriteBack] workflow. Standardmäßig ist dieser Schritt mit dem ursprünglichen Format konfiguriert.

Führen Sie folgende Schritte durch, damit die XMP-Writeback-Funktion Metadaten in die Ausgabeformat-Miniaturansichten „140.100.png“ und „319.319.png“ übertragen.

1. Navigieren Sie in der Experience Manager-Oberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Öffnen Sie über die Seite „Modelle“ das Workflow-Modell **[!UICONTROL DAM-Metadaten-Writeback]**.
1. Öffnen Sie auf der Eigenschaftsseite **[!UICONTROL DAM-Metadaten-Writeback]** den Schritt **[!UICONTROL XMP-Writeback-Vorgang]**.
1. In the [!UICONTROL Step Properties] dialog box, click the **[!UICONTROL Process]** tab.
1. In the **Arguments** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`, andd then click **OK**.

   ![Schritteigenschaften](assets/step_properties.png)

1. Speichern Sie die Änderungen.
1. To regenerate the pyramid TIFF renditions for [!DNL Dynamic Media] images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the [!UICONTROL DAM Metadata Writeback] workflow.

   PTIFF-Ausgabedarstellung werden nur lokal in einer Dynamic Media Hybrid-Implementierung erstellt und gespeichert.

1. Speichern Sie den Workflow.

Die Metadatenänderungen werden in die Ausgabeformate „thumbnail.140.100.png“ und „thumbnail.319.319.png“ des Elements und nicht auf die anderen Ausgabeformate übertragen.

>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtern von XMP-Metadaten {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] unterstützt das Filtern von Eigenschaften/Knoten nach der Whitelist und der Blacklist für XMP-Metadaten, die von den Binärdateien des Elements gelesen und in JCR gespeichert werden, wenn Assets erfasst werden.

Bei der Filterung nach der Blacklist können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn die Blacklist-Filterung das Importieren einer großen Anzahl von Assets mit zahlreichen XMP-Metadaten ermöglicht, kann die Experience Manager-Bereitstellung auf Stabilitätsprobleme stoßen, z. B. verstopfte Beobachtungswarteschlangen.

Dieses Problem lässt sich mit dem Whitelist-Filter für XMP-Metadaten lösen, mit dem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Blacklist-Filter hinzufügen.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. Experience Manager speichert diesen Wert in einem Metadatenfeld mit dem Namen `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. Um die Filterfunktion nach Whitelist anzuwenden, klicken Sie auf **[!UICONTROL Whitelist auf XMP-Eigenschaften anwenden]** und geben Sie die Eigenschaften an, die in das Feld **[!UICONTROL XML-Namen aus Whitelist für XMP-Filterfunktion]** importiert werden sollen.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. Um nach Anwendung des Whitelist-Filters die XMP-Eigenschaften aus der Blacklist herauszufiltern, geben Sie sie im Feld **[!UICONTROL XML-Namen aus Blacklist für XMP-Filterfunktion]** an.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Blacklist auf XMP-Eigenschaften anwenden]** ist standardmäßig ausgewählt. Das heißt, das Filtern nach der Blacklist ist standardmäßig aktiviert. Um die Filterfunktion nach der Blacklist zu deaktivieren, deaktivieren Sie die Option **[!UICONTROL Blacklist auf XMP-Eigenschaften anwenden]**.

1. Speichern Sie die Änderungen.
