---
title: XMP-Writeback in Ausgabeformate
description: Erfahren Sie, wie die XMP-Writeback-Funktion die Metadaten für ein Asset an alle oder spezifische Ausgabeformate des Elements propagiert.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# XMP-Writeback in Ausgabeformate {#xmp-writeback-to-renditions}

Die XMP-Writeback-Funktion in Adobe Experience Manager (AEM) Assets repliziert Änderungen von Asset-Metadaten in den Ausgabeformaten des Assets.

Wenn Sie die Metadaten für ein Asset aus AEM Assets ändern oder das Asset hochladen, werden Änderungen zunächst innerhalb des Asset-Knotens in CRX-De gespeichert.

Die XMP-Funktion &quot;Schriftarterfassung&quot;propagiert die Änderungen der Metadaten an alle oder bestimmte Darstellungen des Assets.

Consider a scenario where you modify the Title property of the asset titled `Classic Leather` to `Nylon`.

![metadata](assets/metadata.png)

In diesem Fall speichert AEM Assets die Änderungen an der Eigenschaft **Titel** im Parameter `dc:title` der in der Elementhierarchie gespeicherten Asset-Metadaten.

![metadata_saved](assets/metadata_stored.png)

AEM Assets propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabeformate eines Assets.

Mit der XMP-Funktion &quot;Schriftarterfassung&quot;können Sie die Metadatenänderungen an alle oder bestimmte Darstellungen des Assets weiterleiten. Die Änderungen werden allerdings nicht unter dem Metadatenknoten in der Asset-Hierarchie gespeichert. Stattdessen werden die Änderungen mit dieser Funktion in die Binärdateien für die Ausgabeformate eingebettet.

## Aktivieren von XMP-Writeback {#enabling-xmp-writeback}

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **Adobe CQ DAM Rendition Maker** in Configuration Manager.

1. Um Configuration Manager zu öffnen, rufen Sie auf `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **Adobe CQ DAM Rendition Maker** configuration.
1. Select the **Propagate XMP** option, and then save the changes.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Aktivieren von XMP-Writeback für bestimmte Ausgabeformate {#enabling-xmp-writeback-for-specific-renditions}

Damit die XMP-Writeback-Funktion die Metadatenänderungen in die Ausgabeformate kopieren kann, müssen Sie diese Ausgabeformate im Workflow-Schritt „XMP-Writeback-Vorgang“ des Workflows „DAM-Metadaten-Writeback“ angeben. Standardmäßig ist dieser Schritt mit der ursprünglichen Darstellung konfiguriert.

Führen Sie folgende Schritte durch, damit die XMP-Writeback-Funktion Metadaten in die Ausgabeformat-Miniaturansichten „140.100.png“ und „319.319.png“ übertragen.

1. Tap/click the AEM logo, and then navigate to **Tools** > **Workflow** > **Models**.
1. From the Models page, open the **DAM Metadata Writeback** workflow model.
1. In the **DAM Metadata Writeback** properties page, open the **XMP Writeback Process** step.
1. In the Step Properties dialog box, tap/click the **Process** tab.
1. In the **Arguments** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`, andd then tap/click **OK**.

   ![step_properties](assets/step_properties.png)

1. Speichern Sie die Änderungen.
1. To regenerate the pyramid TIF renditions for Dynamic Media images with the new attributes, add the **Dynamic Media Process Image Assets** step to the DAM Metadata Writeback workflow.

   PTIFF-Wiedergaben werden nur lokal in einer Dynamic Media Hybrid-Implementierung erstellt und gespeichert.

1. Speichern Sie den Workflow.

Die Änderungen an den Metadaten werden an die Darstellungen thumbnail.140.100.png und thumbnail.319.319.png des Assets weitergeleitet, nicht an die anderen.

>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtern von XMP-Metadaten {#filtering-xmp-metadata}

AEM Assets unterstützt sowohl die Blacklist- als auch die Whitelist-Filterung von Eigenschaften/Knoten für XMP-Metadaten, die aus Asset-Binärdateien gelesen und bei der Erfassung von Assets in JCR gespeichert werden.

Bei der Filterung nach der Blacklist können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn durch das Filtern nach der Blacklist eine große Anzahl von Assets mit vielen XMP-Metadaten importiert werden kann, kann es zu Stabilitätsproblemen bei AEM-Instanz/-Cluster kommen, zum Beispiel zu blockierten Beobachtungswarteschlangen.

Dieses Problem lässt sich mit dem Whitelist-Filter für XMP-Metadaten lösen, mit dem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Blacklist-Filter hinzufügen.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. AEM meldet diesen Wert im Metadatenfeld `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Um Configuration Manager zu öffnen, rufen Sie auf `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **Adobe CQ DAM XmpFilter** configuration.
1. To apply whitelist filtering, select **Apply Whitelist to XMP Properties**, and specify the properties to be imported in the **Whitelisted XML Names for XMP filtering** box.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. To filter out blacklisted XMP properties after applying whitelist filtering, specify them in the **Blacklisted XML Names for XMP filtering** box.

   >[!NOTE]
   >
   >Die Option **Blacklist auf XMP-Eigenschaften anwenden** ist standardmäßig ausgewählt. Das heißt, das Filtern nach der Blacklist ist standardmäßig aktiviert. To disable blacklist filtering, unselect the **Apply Blacklist to XMP Properties** option.

1. Speichern Sie die Änderungen.
