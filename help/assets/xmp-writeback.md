---
title: XMP-Writeback in Ausgabeformaten
description: Erfahren Sie, wie die XMP-Writeback-Funktion die Metadaten für ein Asset an alle oder spezifische Ausgabeformate des Elements propagiert.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 33ab9845f7800c80a6beb5db06f3fadf582122d0

---


# XMP-Writeback in Ausgabeformaten {#xmp-writeback-to-renditions}

Die XMP-Writeback-Funktion in Adobe Experience Manager (AEM) Assets repliziert Änderungen von Asset-Metadaten in den Ausgabeformaten des Assets.

Wenn Sie die Metadaten für ein Asset aus AEM Assets ändern oder das Asset hochladen, werden Änderungen zunächst innerhalb des Asset-Knotens in CRX-De gespeichert.

Die XMP-Funktion &quot;Schriftarterfassung&quot;propagiert die Änderungen der Metadaten an alle oder bestimmte Darstellungen des Assets.

Stellen Sie sich vor, Sie ändern die Eigenschaft Titel des Assets `Classic Leather` in `Nylon`.

![Metadaten](assets/metadata.png)

In diesem Fall speichert AEM Assets die Änderungen an der Eigenschaft **Titel** im Parameter `dc:title` der in der Elementhierarchie gespeicherten Asset-Metadaten.

![metadata_stored](assets/metadata_stored.png)

AEM Assets propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabeformate eines Assets.

Mit der XMP-Funktion &quot;Schriftarterfassung&quot;können Sie die Metadatenänderungen an alle oder bestimmte Darstellungen des Assets weiterleiten. Die Änderungen werden allerdings nicht unter dem Metadatenknoten in der Asset-Hierarchie gespeichert. Stattdessen werden die Änderungen mit dieser Funktion in die Binärdateien für die Ausgabeformate eingebettet.

## Aktivieren von XMP-Writeback {#enabling-xmp-writeback}

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **Adobe CQ DAM Rendition Maker** in Configuration Manager.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **Adobe CQ DAM Rendition Maker**.
1. Wählen Sie die Option **XMP propagieren** aus und speichern Sie die Änderungen.

   ![chlimage_1-135](assets/chlimage_1-346.png)

## Aktivieren von XMP-Writeback für bestimmte Ausgabeformate {#enabling-xmp-writeback-for-specific-renditions}

Damit die XMP-Writeback-Funktion die Metadatenänderungen in die Ausgabeformate kopieren kann, müssen Sie diese Ausgabeformate im Workflow-Schritt „XMP-Writeback-Vorgang“ des Workflows „DAM-Metadaten-Writeback“ angeben. Standardmäßig ist dieser Schritt mit dem ursprünglichen Format konfiguriert.

Führen Sie folgende Schritte durch, damit die XMP-Writeback-Funktion Metadaten in die Ausgabeformat-Miniaturansichten „140.100.png“ und „319.319.png“ übertragen.

1. Tippen oder klicken Sie auf das AEM-Logo und öffnen Sie **Tools** > **Workflow** > **Modelle**.
1. Öffnen Sie über die Seite „Modelle“ das Workflow-Modell **DAM-Metadaten-Writeback**.
1. Öffnen Sie auf der Eigenschaftsseite **DAM-Metadaten-Writeback** den Schritt **XMP-Writeback-Vorgang**.
1.  Tippen/Klicken Sie im Dialogfeld Schritt-Eigenschaften auf die Registerkarte **Prozess**.
1. In the **Arguments** box, add `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`, andd then tap/click **OK**.

   ![Schritteigenschaften](assets/step_properties.png)

1. Speichern Sie die Änderungen.
1. To regenerate the pyramid TIF renditions for Dynamic Media images with the new attributes, add the **Dynamic Media Process Image Assets** step to the DAM Metadata Writeback workflow.

   PTIFF-Ausgabedarstellung werden nur lokal in einer Dynamic Media Hybrid-Implementierung erstellt und gespeichert.

1. Speichern Sie den Workflow.

Die Metadatenänderungen werden in die Ausgabeformate „thumbnail.140.100.png“ und „thumbnail.319.319.png“ des Elements und nicht auf die anderen Ausgabeformate übertragen.

>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## Filtern von XMP-Metadaten {#filtering-xmp-metadata}

AEM Assets unterstützt das Filtern von Eigenschaften/Knoten nach der Whitelist und der Blacklist für XMP-Metadaten, die von den Binärdateien des Elements gelesen und in JCR gespeichert werden, wenn Assets erfasst werden.

Bei der Filterung nach der Blacklist können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn durch das Filtern nach der Blacklist eine große Anzahl von Assets mit vielen XMP-Metadaten importiert werden kann, kann es zu Stabilitätsproblemen bei AEM-Instanz/-Cluster kommen, zum Beispiel zu blockierten Beobachtungswarteschlangen.

Dieses Problem lässt sich mit dem Whitelist-Filter für XMP-Metadaten lösen, mit dem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Blacklist-Filter hinzufügen.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. AEM stores this value in a metadata field named `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **Adobe CQ DAM XmpFilter**.
1. Um die Filterfunktion nach Whitelist anzuwenden, klicken Sie auf **Whitelist auf XMP-Eigenschaften anwenden** und geben Sie die Eigenschaften an, die in das Feld **XML-Namen aus Whitelist für XMP-Filterfunktion** importiert werden sollen.

   ![chlimage_1-136](assets/chlimage_1-347.png)

1. Um nach Anwendung des Whitelist-Filters die XMP-Eigenschaften aus der Blacklist herauszufiltern, geben Sie sie im Feld **XML-Namen aus Blacklist für XMP-Filterfunktion** an.

   >[!NOTE]
   >
   >Die Option **Blacklist auf XMP-Eigenschaften anwenden** ist standardmäßig ausgewählt. Das heißt, das Filtern nach der Blacklist ist standardmäßig aktiviert. Um die Filterfunktion nach der Blacklist zu deaktivieren, deaktivieren Sie die Option **Blacklist auf XMP-Eigenschaften anwenden**.

1. Speichern Sie die Änderungen.
