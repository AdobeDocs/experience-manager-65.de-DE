---
title: Asynchrone Vorgänge
description: Experience Manager Assets optimiert die Leistung, indem einige ressourcenintensive Aufgaben asynchron abgeschlossen werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 71%

---


# Asynchrone Vorgänge {#asynchronous-operations}

Um die Leistungsbeeinträchtigung zu verringern, verarbeitet Adobe Experience Manager Assets bestimmte langfristige und ressourcenintensive Asset-Vorgänge asynchron.

Zu diesen Vorgängen gehören u. a.:

* Löschen vieler Assets
* Verschieben vieler Assets oder Assets mit vielen Verweisen
* Exportieren/Importieren von Asset-Metadaten in großen Mengen.
* Abrufen von Assets, die über dem festgelegten Schwellenwert liegen, aus einer Remote Experience Manager-Bereitstellung.

Die asynchrone Verarbeitung umfasst den Aufbau einer Warteschlange mit mehreren Aufträgen und schließlich deren serielle Ausführung gemäß der Verfügbarkeit von Systemressourcen.

Sie können den Status asynchroner Aufträge auf der Seite **[!UICONTROL Async-Auftragsstatus]** einsehen.

>[!NOTE]
>
>Standardmäßig werden Aufträge in  Assets parallel ausgeführt. Wenn N die Anzahl der CPU-Kerne ist, können standardmäßig N/2 Aufträge parallel ausgeführt werden. Um benutzerdefinierte Einstellungen für die Auftragswarteschlange festzulegen, passen Sie die Konfiguration **[!UICONTROL Async Operation Default Queue]** über die Web-Konsole an. For more information, see [queue configurations](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitor the status of asynchronous operations {#monitoring-the-status-of-asynchronous-operations}

Jedes Mal, wenn  Assets einen Vorgang asynchron verarbeitet, erhalten Sie eine Benachrichtigung in Ihrem Posteingang sowie per E-Mail.

Um den Status der asynchronen Vorgänge detailliert anzuzeigen, navigieren Sie zur Seite **[!UICONTROL Async-Auftragsstatus]**.

1. Klicken Sie in der Experience Manager-Oberfläche auf **[!UICONTROL Vorgänge]** > **[!UICONTROL Aufträge]**.

1. Überprüfen Sie die Details für die Vorgänge auf der Seite **[!UICONTROL Async-Auftragsstatus]**.

   ![Status und Details asynchroner Vorgänge](assets/AsyncOperation-status.png)

   Den Fortschritt einzelner Vorgänge finden Sie in der Spalte **[!UICONTROL Status]**. Abhängig vom Fortschritt wird eine der folgenden Statusmeldungen angezeigt:

   * **[!UICONTROL Aktiv]**: Der Vorgang wird verarbeitet

   * **[!UICONTROL Erfolg]**: Der Vorgang wurde abgeschlossen

   * **[!UICONTROL Fehlschlag]** oder **[!UICONTROL Fehler]**: Der Vorgang konnte nicht bearbeitet werden.

   * **[!UICONTROL Geplant]**: Die Verarbeitung des Vorgangs ist für einen späteren Zeitpunkt geplant

1. To stop an active operation, select it from the list and click **[!UICONTROL Stop]** from the toolbar.

   ![Stoppsymbol](assets/stop_icon.png)

1. To view extra details, for example description and logs, select the operation and click **[!UICONTROL Open]** from the toolbar.

   ![Öffnen-Symbol](assets/open_icon.png)

   Die Detailseite für den Auftrag wird angezeigt.

   ![Auftragsdetails](assets/job_details.png)

1. Um den Vorgang aus der Liste zu löschen, wählen Sie die Option **[!UICONTROL Löschen]** in der Symbolleiste aus. To download the details in a CSV file, click **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >Sie können einen Auftrag nicht löschen, wenn er aktiv ist oder sich in der Warteschlange befindet.

## Bereinigen von abgeschlossenen Aufträgen {#purging-completed-jobs}

Experience Manager Assets führt jeden Tag um 1:00 Uhr einen Bereinigungsauftrag aus, um abgeschlossene asynchrone Aufträge zu löschen, die älter als ein Tag sind.

Sie können den Zeitplan für den Bereinigungsauftrag bearbeiten. Außerdem können Sie anpassen, wie lange die Details zu abgeschlossenen Aufträgen gespeichert werden sollen, bevor sie gelöscht werden. Darüber hinaus können Sie die maximale Anzahl abgeschlossener Aufträge konfigurieren, deren Details zu einem beliebigen Zeitpunkt gespeichert werden.

1. Klicken Sie in der Experience Manager-Oberfläche auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie den Auftrag **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]**.
1. Geben Sie den Schwellenwert für die Anzahl der Tage ein, nach denen abgeschlossene Aufträge gelöscht werden sollen. Legen Sie außerdem die maximale Anzahl der Aufträge fest, deren Details im Verlauf gespeichert werden sollen.

   ![Konfiguration zum Planen der Bereinigung asynchroner Aufträge](assets/configmgr_purge_asyncjobs.png)

1. Speichern Sie die Änderungen.

## Configure thresholds for asynchronous processing {#configuring-thresholds-for-asynchronous-processing}

Sie können den Schwellenwert für Assets oder Verweise festlegen, damit  Assets einen bestimmten Vorgang asynchron verarbeitet.

### Configure thresholds for asynchronous delete operations {#configuring-thresholds-for-asynchronous-delete-operations}

Wenn die Anzahl der Assets oder der zu löschenden Ordner den Schwellenwert überschreitet, wird der Löschvorgang asynchron ausgeführt.

1. Klicken Sie in der Experience Manager-Oberfläche auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die Konfiguration **[!UICONTROL Async Delete Operation Job Processing]**.
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets]** den Schwellenwert für die Anzahl von Assets/Ordnern für die asynchrone Verarbeitung von Löschvorgängen an.

   ![Löschen-Schwellenwert](assets/delete_threshold.png)

1. Speichern Sie die Änderungen.

### Configure thresholds for asynchronous move operations {#configuring-thresholds-for-asynchronous-move-operations}

Wenn die Anzahl der zu verschiebenden Anlagen/Ordner oder Referenzen den Schwellenwert übersteigt, wird der Verschiebevorgang asynchron ausgeführt.

1. Klicken Sie in der Experience Manager-Oberfläche auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die Konfiguration **[!UICONTROL Async Move Operation Job Processing]**.
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets/Verweise]** den Schwellenwert für Assets/Ordner oder Verweise für die asynchrone Verarbeitung von Verschiebevorgängen fest.

   ![Verschieben-Schwellenwert](assets/move_threshold.png)

1. Speichern Sie die Änderungen.
