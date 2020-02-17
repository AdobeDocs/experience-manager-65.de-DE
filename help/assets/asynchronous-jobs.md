---
title: Asynchrone Vorgänge
description: AEM Assets optimiert die Leistung, durch das asynchrone Ausführen ressourcenintensiver Vorgänge.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Asynchrone Vorgänge {#asynchronous-operations}

Um negative Auswirkungen auf die Leistung einzuschränken, werden bestimmte lang laufende und ressourcenintensive Asset-Vorgänge in Adobe Experience Manager (AEM) Assets asynchron verarbeitet.

Zu diesen Vorgängen gehören u. a.:

* Löschen vieler Assets
* Verschieben vieler Assets oder Assets mit vielen Verweisen
* Exportieren/Importieren von Asset-Metadaten in großen Mengen.
* Abrufen von Assets, die über dem festgelegten Schwellenwert liegen, aus einer Remote-AEM-Bereitstellung.

Die asynchrone Verarbeitung umfasst den Aufbau einer Warteschlange mit mehreren Aufträgen und schließlich deren serielle Ausführung gemäß der Verfügbarkeit von Systemressourcen.

You can view the status of asynchronous jobs from the **[!UICONTROL Async Job Status]** page.

>[!NOTE]
>
>Standardmäßig werden Aufträge in AEM Assets parallel ausgeführt. Wenn N die Anzahl der CPU-Kerne ist, können standardmäßig N/2 Aufträge parallel ausgeführt werden. Um benutzerdefinierte Einstellungen für die Auftragswarteschlange festzulegen, passen Sie die Konfiguration **[!UICONTROL Async Operation Default Queue]** über die Web-Konsole an. For more information, see [queue configurations](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitor the status of asynchronous operations {#monitoring-the-status-of-asynchronous-operations}

Jedes Mal, wenn AEM Assets einen Vorgang asynchron verarbeitet, erhalten Sie eine Benachrichtigung in Ihrem Posteingang sowie per E-Mail.

To view the status of the asynchronous operations in detail, navigate to the **[!UICONTROL Async Job Status]** page.

1. Tap/click the AEM logo, and go **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.
1. In the **[!UICONTROL Async Job Status]** page, review the details of the operations.

   ![Status und Details asynchroner Vorgänge](assets/AsyncOperation-status.png)

   Den Fortschritt einzelner Vorgänge finden Sie in der Spalte **[!UICONTROL Status]**. Abhängig vom Fortschritt wird eine der folgenden Statusmeldungen angezeigt:

   * **[!UICONTROL Aktiv]**: Der Vorgang wird verarbeitet

   * **[!UICONTROL Erfolg]**: Der Vorgang wurde abgeschlossen

   * **[!UICONTROL Fehler]******: Der Vorgang konnte nicht verarbeitet werden

   * **[!UICONTROL Geplant]**: Die Verarbeitung des Vorgangs ist für einen späteren Zeitpunkt geplant

1. To stop an active operation, select it from the list and tap **[!UICONTROL Stop]** from the toolbar.

   ![stop_icon](assets/stop_icon.png)

1. To view extra details, for example description and logs, select the operation and tap **[!UICONTROL Open]** from the toolbar.

   ![open_icon](assets/open_icon.png)

   Die Detailseite für den Auftrag wird angezeigt.

   ![job_details](assets/job_details.png)

1. Um den Vorgang aus der Liste zu löschen, wählen Sie die Option **[!UICONTROL Löschen]** in der Symbolleiste aus. To download the details in a CSV file, tap **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >Sie können einen Auftrag nicht löschen, wenn er aktiv ist oder sich in der Warteschlange befindet.

## Bereinigen abgeschlossener Aufträge {#purging-completed-jobs}

AEM Assets führt jeden Tag um 1:00 Uhr einen Bereinigungsauftrag aus, um abgeschlossene asynchrone Aufträge zu löschen, die älter als einen Tag sind.

Sie können den Zeitplan für den Bereinigungsauftrag bearbeiten. Außerdem können Sie anpassen, wie lange die Details zu abgeschlossenen Aufträgen gespeichert werden sollen, bevor sie gelöscht werden. Darüber hinaus können Sie die maximale Anzahl abgeschlossener Aufträge konfigurieren, deren Details zu einem beliebigen Zeitpunkt gespeichert werden.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Open the **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]** job.
1. Geben Sie die Schwellenzahl der Tage an, nach denen abgeschlossene Aufträge gelöscht werden, und die maximale Anzahl von Aufträgen, für die Details im Verlauf beibehalten werden.

   ![Konfiguration zum Planen der Bereinigung asynchroner Aufträge](assets/configmgr_purge_asyncjobs.png)

1. Speichern Sie die Änderungen.

## Configure thresholds for asynchronous processing {#configuring-thresholds-for-asynchronous-processing}

Sie können den Schwellenwert für Assets oder Verweise festlegen, damit AEM Assets einen bestimmten Vorgang asynchron verarbeitet.

### Configure thresholds for asynchronous delete operations {#configuring-thresholds-for-asynchronous-delete-operations}

Wenn die Anzahl der Assets oder der zu löschenden Ordner den Schwellenwert überschreitet, wird der Löschvorgang asynchron verarbeitet.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the web console, open the **[!UICONTROL Async Delete Operation Job Processing]** configuration.
1. In the **[!UICONTROL Threshold number of assets]** box, specify the threshold number of assets/folders for asynchronous processing of delete operations.

   ![delete_Schwellenwert](assets/delete_threshold.png)

1. Speichern Sie die Änderungen.

### Configure thresholds for asynchronous move operations {#configuring-thresholds-for-asynchronous-move-operations}

Wenn die Anzahl der Assets oder der zu löschenden Ordner den Schwellenwert überschreitet, wird der Löschvorgang asynchron verarbeitet.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the web console, open the **[!UICONTROL Async Move Operation Job Processing]** configuration.
1. In the **[!UICONTROL Threshold number of assets/references]** box, specify the threshold number of assets/folders or references for asynchronous processing of move operations.

   ![move_Schwellenwert](assets/move_threshold.png)

1. Speichern Sie die Änderungen.
