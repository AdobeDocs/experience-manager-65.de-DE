---
title: Best Practices für das Übersetzen von Assets
description: Best Practices für die effiziente Verwaltung von Assets zur Synchronisation verschiedener übersetzter Versionen und zur Optimierung von Übersetzungs-Workflows.
contentOwner: AG
role: Admin
feature: Asset Management
exl-id: e632dcdb-b2b9-45bc-89e7-337b44b6fc61
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 100%

---

# Best Practices für das Übersetzen von Assets {#best-practices-for-translating-assets-efficiently}

[!DNL Adobe Experience Manager Assets] unterstützt mehrsprachige Workflows, um Binärdateien, Metadaten und Tags für digitale Assets in verschiedene Gebietsschemata zu übertragen und die übersetzten Assets zu verwalten. Details finden Sie unter [Mehrsprachige Assets](multilingual-assets.md).

Um die Assets effizient zu verwalten und sicherzustellen, dass verschiedene übersetzte Versionen synchronisiert bleiben, erstellen Sie [Sprachkopien](preparing-assets-for-translation.md) der Assets, bevor Sie die Übersetzungs-Workflows ausführen.

Bei einer Sprachkopie eines Assets oder einer Gruppe von Assets handelt es sich um Sprachgeschwister (oder eine Version der Assets in einer verwandten Sprache) mit einer ähnlichen Inhaltshierarchie.

Jede Sprachkopie ist ein unabhängiges Asset. Daher kann durch das Übertragen von Assets in mehrere Gebietsschemata die Größe des CRX-Repository deutlich zunehmen. Wenn Sie beispielsweise Assets mit einer kombinierten Größe von 10 GB in zwei Sprachen übersetzen, kann dadurch die Repository-Größe auf etwa 20 GB (10 GB für jede Sprache) ansteigen.

Asset-Binärdateien belegen im Vergleich zu Metadaten und Tags deutlich mehr Speicherplatz. Wenn die Übersetzung von Metadaten und Tags daher nur Ihrem Zweck dient, lassen Sie die Übersetzung der Binärdateien weg. Sie können die Originalkopie der Binärdateien im Repository zur Verknüpfung mit in verschiedene Gebietsschemata übertragenen Metadaten und Tags aufbewahren. Durch das Verwalten einer einzigen Kopie von Binärdateien anstelle mehrerer übersetzter Versionen werden die Auswirkungen auf die Repository-Größe minimiert.

Dateidatenspeicher und Amazon S3-Datenspeicher bieten eine Speicherinfrastruktur, die für diese Szenarien am besten geeignet ist. Diese Speicherrepositorys speichern eine Einzelkopie der Asset-Binärdateien (einschließlich Wiedergaben), die gemeinsam von Metadaten und Tags in mehreren Gebietsschemata genutzt werden kann. Daher wirkt sich das Erstellen von Asset-Sprachkopien und das Übersetzen von Metadaten und Tags nicht auf die Größe der Repositorys aus.

Sie können auch einige Konfigurationsänderungen an einigen Workflows und dem Framework für die Übersetzungsintegration vornehmen, um den Prozess weiter zu optimieren.

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

1. Aktivieren Sie den Workflow [!UICONTROL Datum der letzten Änderung festlegen].

   Mit dem Workflow [!UICONTROL DAM-Metadaten-Writeback] können Sie das Datum der letzten Änderung für ein Asset konfigurieren. Da dieser Workflow in Schritt 2 deaktiviert wird, kann [!DNL Assets] das Datum der letzten Asset-Änderung nicht länger auf dem neuesten Stand halten. Aktivieren Sie daher den Workflow *Datum der letzten Änderung festlegen*, um sicherzustellen, dass das Datum der letzten Änderung der Assets aktuell sind. Assets mit veralteten Daten der letzten Änderung können Fehler verursachen.

1. [Konfigurieren Sie das Framework für die Übersetzungsintegration](/help/sites-administering/tc-tic.md) so, dass die Übersetzung von Asset-Binärdateien gestoppt wird. Deaktivieren Sie auf der Registerkarte **[!UICONTROL Assets]** die Option [!UICONTROL Assets übersetzen], um eine Übersetzung von Asset-Binärdateien auszuschließen. 
1. Übersetzen Sie Asset-Metadaten/-Tags mithilfe von [mehrsprachigen Asset-Workflows](multilingual-assets.md).
