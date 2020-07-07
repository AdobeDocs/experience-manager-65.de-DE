---
title: Konfigurieren Sie asynchrone Vorgänge in [!DNL Adobe Experience Manager].
description: Führen Sie asynchron einige ressourcenintensive Aufgaben durch, um die Leistung in [!DNL Experience Manager Assets]zu optimieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b59f7471ab9f3c5e6eb3365122262b592c8e6244
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 18%

---


# Asynchrone Vorgänge {#asynchronous-operations}

Um negative Auswirkungen auf die Leistung zu reduzieren, [!DNL Adobe Experience Manger Assets] werden bestimmte langfristige und ressourcenintensive Asset-Vorgänge asynchron verarbeitet. Bei der asynchronen Verarbeitung werden mehrere Aufgaben in die Warteschlange gestellt und anschließend in einer seriellen Ausführung ausgeführt, sofern Systemressourcen zur Verfügung stehen. Zu diesen Vorgängen gehören u. a.:

* Löschen vieler Assets.
* Verschieben vieler Assets oder Assets mit vielen Verweisen.
* Exportieren und Importieren von Asset-Metadaten als Massendatei
* Abrufen von Assets aus einer Remote- [!DNL Experience Manager] Bereitstellung, die eine festgelegte Schwellenwertbegrenzung überschreiten. Die Beschränkung bezieht sich auf die Anzahl der Assets.

You can view the status of asynchronous tasks from the **[!UICONTROL Async Job Status]** page.

>[!NOTE]
>
>Standardmäßig werden die [!DNL Assets] Aufgaben parallel ausgeführt. If `N` is the number of CPU cores, `N/2` tasks can execute in parallel, by default. To use custom settings for the task queue, modify the **[!UICONTROL Async Operation Default Queue]** configuration from the [!UICONTROL Web Console]. For more information, see [queue configurations](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitor the status of asynchronous operations {#monitoring-the-status-of-asynchronous-operations}

Bei jeder asynchronen [!DNL Assets] Verarbeitung eines Vorgangs erhalten Sie eine Benachrichtigung in Ihrem [!DNL Experience Manager] Posteingang [](/help/sites-authoring/inbox.md) und per E-Mail. Um den Status der asynchronen Vorgänge detailliert anzuzeigen, navigieren Sie zur Seite **[!UICONTROL Async-Auftragsstatus]**.

1. Klicken Sie in der [!DNL Experience Manager] Benutzeroberfläche auf **[!UICONTROL Vorgänge]** > **[!UICONTROL Aufträge]**.

1. Überprüfen Sie die Details für die Vorgänge auf der Seite **[!UICONTROL Async-Auftragsstatus]**.

   ![Status und Details asynchroner Vorgänge](assets/AsyncOperation-status.png)

   Informationen zum Fortschritt eines Vorgangs finden Sie in der Spalte **[!UICONTROL Status]** . Abhängig vom Fortschritt wird eine der folgenden Statusmeldungen angezeigt:

   * **[!UICONTROL Aktiv]**: Der Vorgang wird verarbeitet.
   * **[!UICONTROL Erfolg]**: Der Vorgang wurde abgeschlossen.
   * **[!UICONTROL Fehler]******: Der Vorgang konnte nicht verarbeitet werden.
   * **[!UICONTROL Geplant]**: Die Verarbeitung des Vorgangs ist für einen späteren Zeitpunkt geplant.

1. To stop an active operation, select it from the list and click **[!UICONTROL Stop]** ![stop icon](assets/do-not-localize/stop_icon.svg) from the toolbar.

1. To view extra details, for example description and logs, select the operation and click **[!UICONTROL Open]** ![open_icon](assets/do-not-localize/edit_icon.svg) from the toolbar. Die Detailseite der Aufgabe wird angezeigt.

   ![Details einer Metadaten-Import-Aufgabe](assets/job_details.png)

1. Um den Vorgang aus der Liste zu löschen, wählen Sie die Option **[!UICONTROL Löschen]** in der Symbolleiste aus. To download the details in a CSV file, click **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >Sie können eine Aufgabe nicht löschen, wenn ihr Status aktiv oder in der Warteschlange steht.

## Bereinigen abgeschlossener Aufgaben {#purge-completed-tasks}

[!DNL Experience Manager Assets] Führt täglich um 100 Uhr eine Bereinigungsstunde aus, um abgeschlossene asynchrone Aufgaben zu löschen, die älter als ein Tag sind.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

Sie können den Zeitplan für die Bereinigungszeit und die Aufgabe ändern, in der Details abgeschlossener Aufgaben vor dem Löschen beibehalten werden. Sie können auch die maximale Anzahl abgeschlossener Aufgaben konfigurieren, für die Details jederzeit beibehalten werden.

1. Klicken Sie in der [!DNL Experience Manager] Benutzeroberfläche auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Open the **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]** task.
1. Geben Sie die Schwellenzahl der Tage an, nach denen abgeschlossene Aufgaben gelöscht werden, und die maximale Anzahl der Aufgaben, für die Details im Verlauf beibehalten werden. Speichern Sie die Änderungen.

   ![Konfiguration zum Planen des Bereinigens asynchroner Aufgaben](assets/configmgr_purge_asyncjobs.png)

## Konfigurieren des Schwellenwerts für asynchrone Löschvorgänge {#configure-thresholds-for-asynchronous-delete-operations}

Wenn die Anzahl der zu löschenden Assets oder Ordner die festgelegte Schwellenzahl überschreitet, wird der Löschvorgang asynchron durchgeführt.

1. Klicken Sie in der [!DNL Experience Manager] Benutzeroberfläche auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Delete Operation Job Processing]** configuration.
1. Geben Sie im Feld **[!UICONTROL Schwellenwert für die Anzahl der Assets]** die Schwellenwerte an, um Assets, Ordner oder Verweise asynchron zu löschen. Speichern Sie die Änderungen.

   ![Festlegen des Schwellenwerts für die Aufgabe, Assets zu löschen](assets/delete_threshold.png)

## Konfigurieren des Schwellenwerts für asynchrone Verschiebungsvorgänge {#configure-thresholds-for-asynchronous-move-operations}

Wenn die Anzahl der zu verschiebenden Assets, Ordner oder Verweise die festgelegte Schwellenzahl überschreitet, wird der Verschiebungsvorgang asynchron ausgeführt.

1. Klicken Sie in der [!DNL Experience Manager] Benutzeroberfläche auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the [!UICONTROL Web Console], open the **[!UICONTROL Async Move Operation Job Processing]** configuration.
1. Geben Sie im Feld **[!UICONTROL Schwellenwert für die Anzahl der Assets/Verweise]** die Schwellenwerte an, um Assets, Ordner oder Verweise asynchron zu verschieben. Speichern Sie die Änderungen.

   ![Festlegen des Schwellenwerts für die Aufgabe zum Verschieben von Assets](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [Konfigurieren Sie E-Mail in Experience Manager](/help/sites-administering/notification.md).
>* [Stapelweises Importieren und Exportieren von Asset-Metadaten](/help/assets/metadata-import-export.md).
>* [Verwenden Sie verbundene Assets, um DAM-Assets aus Remote-Bereitstellungen](/help/assets/use-assets-across-connected-assets-instances.md)freizugeben.

