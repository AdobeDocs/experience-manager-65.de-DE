---
title: Best Practices zum Übersetzen von Assets
description: Best Practices für die effiziente Verwaltung von Assets zur Synchronisation verschiedener übersetzter Versionen und zur Optimierung von Übersetzungs-Workflows.
contentOwner: AG
role: Admin
feature: Asset-Management
exl-id: e632dcdb-b2b9-45bc-89e7-337b44b6fc61
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 87%

---

# Best Practices zum Übersetzen von Assets {#best-practices-for-translating-assets-efficiently}

[!DNL Adobe Experience Manager Assets] unterstützt mehrsprachige Workflows, um Binärdateien, Metadaten und Tags für digitale Assets in verschiedene Gebietsschemas zu übertragen und die übersetzten Assets zu verwalten. Details finden Sie unter [Mehrsprachige Assets](multilingual-assets.md).

Um die Assets effizient zu verwalten und sicherzustellen, dass verschiedene übersetzte Versionen synchronisiert bleiben, erstellen Sie [Sprachkopien](preparing-assets-for-translation.md) der Assets, bevor Sie die Übersetzungsworkflows ausführen.

Die Sprachkopie eines Assets oder einer Gruppe von Assets ist ein gleichgeordnetes Sprachenelement (oder eine Version der oder des Assets in einer verwandten Sprache) mit einer ähnlichen Inhaltshierarchie.

Jede Sprachkopie ist ein unabhängiges Asset. Daher kann durch das Übertragen von Assets in mehrere Gebietsschemas die Größe des CRX-Repository deutlich zunehmen. Beispielsweise kann sich durch das Übersetzen von Assets mit einer Größe von insgesamt 10 GB in zwei Sprachen die Repositorygröße auf ca. 20 GB (10 GB für jede Sprache) erhöhen.

Asset-Binärdateien belegen im Vergleich zu Metadaten und Tags deutlich mehr Speicherplatz. Wenn das Übersetzen von Metadaten und Tags für Ihre Zwecke ausreicht, sollten Sie daher auf das Übersetzen der Binärdateien verzichten. Sie können die Originalkopie der Binärdateien im Repository zur Verknüpfung mit in verschiedene Gebietsschemas übertragenen Metadaten und Tags aufbewahren. Wenn Sie lediglich eine Einzelkopie statt mehrerer übersetzter Versionen beibehalten, wird hierdurch die Auswirkung auf die Repositorygröße minimiert.

Dateidatenspeicher und Amazon S3-Datenspeicher bieten eine Speicherinfrastruktur, die für diese Szenarien am besten geeignet ist. Diese Speicherrepositorys speichern eine Einzelkopie der Asset-Binärdateien (einschließlich Wiedergaben), die gemeinsam von Metadaten und Tags in mehreren Gebietsschemas genutzt werden kann. Daher wird die Repositorygröße nicht durch das Erstellen von Asset-Sprachkopien und Übersetzen von Metadaten und Tags beeinflusst.

Mittels gewisser Änderungen an Workflows und am Framework für die Übersetzungsintegration können Sie den Prozess weiter optimieren.

1. Führen Sie einen der folgenden Schritte aus:

   * [Richten Sie einen Dateidatenspeicher ein.](/help/sites-deploying/data-store-config.md)
   * [Richten Sie einen Amazon S3-Datenspeicher ein.](/help/sites-deploying/data-store-config.md)

<!--
1. Disable the [DAM MetaData Write-back](/help/sites-administering/workflow-offloader.md#disable-offloading) workflow.

   As the name suggests, the [!UICONTROL DAM Metadata Writeback] workflow rewrites the metadata to the binary file. Because the metadata changes after translation, writing it back to the binary file generates a different binary for a language copy.

   >[!NOTE]
   >
   >Disabling the [!UICONTROL DAM MetaData Writeback] workflow turns off XMP metadata write-back on asset binaries. Consequently, future metadata changes are no longer be saved within the assets. Evaluate the consequences before disabling this workflow.
-->

1. Aktivieren Sie den Workflow [!UICONTROL Letztes Änderungsdatum des Sets].

   Mit dem Workflow [!UICONTROL DAM-Metadaten-Writeback] wird das Datum der letzten Änderung eines Assets konfiguriert. Da Sie diesen Workflow in Schritt 2 deaktivieren, kann [!DNL Assets] das Datum der letzten Änderung von Assets nicht mehr auf dem neuesten Stand halten. Aktivieren Sie daher den Workflow *Letztes Änderungsdatum des Sets*, um sicherzustellen, dass die Datumsangaben für die letzten Asset-Änderungen aktuell sind. Assets mit veralteten Datumsangaben für letzte Änderungen können Fehler verursachen.

1. [Konfigurieren Sie das Framework für die Übersetzungsintegration](/help/sites-administering/tc-tic.md), damit Asset-Binärdateien nicht mehr übersetzt werden. Heben Sie die Auswahl der Option **[!UICONTROL Assets übersetzen]** auf der Registerkarte [!UICONTROL Assets] auf, um die Übersetzung von Asset-Binärdateien zu stoppen.
1. Übersetzen Sie Asset-Metadaten/Tags mit [mehrsprachigen Asset-Workflows](multilingual-assets.md).
