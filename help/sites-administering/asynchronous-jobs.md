---
title: Asynchrone Aufträge
description: Adobe Experience Manager optimiert die Leistung durch asynchrone Ausführung einiger ressourcenintensiver Aufgaben.
translation-type: tm+mt
source-git-commit: 198593fa456780816216a63790fea8cca469f8c7
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 27%

---


# Asynchrone Vorgänge {#asynchronous-operations}

Um negative Auswirkungen auf die Leistung zu reduzieren, verarbeitet Adobe Experience Manager bestimmte langjährige und ressourcenintensive Vorgänge asynchron. Bei der asynchronen Verarbeitung werden mehrere Aufträge in die Warteschlange gestellt und in einer seriellen Ausführung ausgeführt, sofern Systemressourcen zur Verfügung stehen.

Zu diesen Vorgängen gehören u. a.:

* Löschen vieler Assets
* Verschieben vieler Assets oder Assets mit vielen Verweisen
* Exportieren/Importieren von Asset-Metadaten in großen Mengen
* Abrufen von Assets, die über dem festgelegten Schwellenwert liegen, von einer Remote-Experience Manager-Bereitstellung
* Verschieben von Seiten
* Live Copies herausrollen

Sie können den Status asynchroner Aufträge über das Dashboard **[!UICONTROL Async-Auftragsstatus]** unter **Global Navigation** -> **Tools** -> **Vorgänge** -> **Aufträge** Ansicht haben.

>[!NOTE]
>
>Standardmäßig werden asynchrone Aufträge parallel ausgeführt. If *`n`* is the number of CPU cores, *`n/2`* jobs can run in parallel, by default. Um benutzerdefinierte Einstellungen für die Auftragswarteschlange zu verwenden, ändern Sie die **[!UICONTROL Standardwarteschlangenkonfiguration]** für den Async-Vorgang und die **Async-Vorgangsseitenverschiebungs- und -Rollout-Konfiguration** in der Webkonsole.
>
>For more information, see [queue configurations](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Monitor the Status of Asynchronous Operations {#monitor-the-status-of-asynchronous-operations}

Wenn AEM einen Vorgang asynchron verarbeitet, erhalten Sie eine Benachrichtigung im [Posteingang](/help/sites-authoring/inbox.md) und per E-Mail (falls aktiviert).

Um den Status der asynchronen Vorgänge detailliert anzuzeigen, navigieren Sie zur Seite **[!UICONTROL Async-Auftragsstatus]**.

1. Klicken Sie in der Benutzeroberfläche &quot;Experience Manager&quot;auf **[!UICONTROL Vorgänge]** > **[!UICONTROL Aufträge]**.

1. Überprüfen Sie die Details für die Vorgänge auf der Seite **[!UICONTROL Async-Auftragsstatus]**.

   ![Status und Details asynchroner Vorgänge](assets/async-operation-status.png)

   To determine the progress of a particular operation, see the value in the **[!UICONTROL Status]** column. Abhängig vom Fortschritt wird eine der folgenden Statusmeldungen angezeigt:

   * **[!UICONTROL Aktiv]**: Der Vorgang wird verarbeitet

   * **[!UICONTROL Erfolg]**: Der Vorgang wurde abgeschlossen

   * **[!UICONTROL Fehlschlag]** oder **[!UICONTROL Fehler]**: Der Vorgang konnte nicht bearbeitet werden.

   * **[!UICONTROL Geplant]**: Die Verarbeitung des Vorgangs ist für einen späteren Zeitpunkt geplant

1. To stop an active operation, select it from the list and click **[!UICONTROL Stop]** from the toolbar.

   ![Stoppsymbol](assets/async-stop-icon.png)

1. To view extra details, for example description and logs, select the operation and click **[!UICONTROL Open]** from the toolbar.

   ![Öffnen-Symbol](assets/async-open-icon.png)

   Die Detailseite für den Auftrag wird angezeigt.

   ![Auftragsdetails](assets/async-job-details.png)

1. Um den Vorgang aus der Liste zu löschen, wählen Sie die Option **[!UICONTROL Löschen]** in der Symbolleiste aus. To download the details in a CSV file, click **[!UICONTROL Download]**.

   >[!NOTE]
   >
   >You cannot delete a job if its status is either **Active** or **Queued**.

## Bereinigen von abgeschlossenen Aufträgen {#purging-completed-jobs}

AEM führt jeden Tag um 01:00 Uhr einen Bereinigungsauftrag aus, um abgeschlossene asynchrone Aufträge zu löschen, die älter als ein Tag sind.

Sie können den Zeitplan für den Bereinigungsauftrag bearbeiten. Außerdem können Sie anpassen, wie lange die Details zu abgeschlossenen Aufträgen gespeichert werden sollen, bevor sie gelöscht werden. Darüber hinaus können Sie die maximale Anzahl abgeschlossener Aufträge konfigurieren, deren Details zu einem beliebigen Zeitpunkt gespeichert werden.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie den **[!UICONTROL Adobe Granite Async Jobs Purge Scheduled Job]** Auftrag.
1. Geben Sie Folgendes an:
   * Die Schwellenzahl der Tage, nach denen abgeschlossene Aufträge gelöscht werden.
   * Die maximale Anzahl von Aufträgen, für die Details im Verlauf beibehalten werden.
   * Der Cron-Ausdruck, für den die Bereinigung ausgeführt werden soll.

   ![Konfiguration zum Planen der Bereinigung asynchroner Aufträge](assets/async-purge-job.png)

1. Speichern Sie die Änderungen.

## Asynchrone Verarbeitung konfigurieren {#configuring-asynchronous-processing}

Sie können die Schwellenwerte für Assets, Seiten oder Verweise konfigurieren, damit AEM einen bestimmten Vorgang asynchron verarbeitet und E-Mail-Benachrichtigungen für den Zeitpunkt der Auftragsverarbeitung umschalten.

### Vorgänge zum Löschen asynchroner Assets konfigurieren {#configuring-synchronous-delete-operations}

Wenn die Anzahl der zu löschenden Assets oder Ordner den Schwellenwert überschreitet, wird der Löschvorgang asynchron ausgeführt.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Webkonsole die **[!UICONTROL ASYN-Standardwarteschlangenkonfiguration.]**
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets]** den Schwellenwert für die Anzahl von Assets/Ordnern für die asynchrone Verarbeitung von Löschvorgängen an.

   ![Schwellenwert zum Löschen von Assets](assets/async-delete-threshold.png)

1. Aktivieren Sie die Option E-Mail-Benachrichtigung **aktivieren** , um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. z.B. Erfolg, fehlgeschlagen.
1. Speichern Sie die Änderungen.

### Vorgänge zum Konfigurieren von asynchronen Assets {#configuring-asynchronous-move-operations}

Wenn die Anzahl der zu verschiebenden Assets/Ordner oder Verweise den Schwellenwert überschreitet, wird der Verschiebungsvorgang asynchron durchgeführt.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the web console, open the **[!UICONTROL Async Move Operation Job Processing Configuration.]**
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets/Verweise]** den Schwellenwert für Assets/Ordner oder Verweise für die asynchrone Verarbeitung von Verschiebevorgängen fest.

   ![Asset-Verschiebungsschwellenwert](assets/async-move-threshold.png)

1. Aktivieren Sie die Option E-Mail-Benachrichtigung **aktivieren** , um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. z.B. Erfolg, fehlgeschlagen.
1. Speichern Sie die Änderungen.

### Vorgänge zum Konfigurieren von asynchronen Seitenverschieben {#configuring-asynchronous-page-move-operations}

Wenn die Anzahl der Verweise auf die zu verschiebende(n) Seite(n) die Schwellenzahl überschreitet, wird der Verschiebungsvorgang asynchron durchgeführt.

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the web console, open the **[!UICONTROL Async Page Move Operation Job Processing Configuration.]**
1. In the **[!UICONTROL Threshold number of references]** field, specify the threshold number of references for asynchronous processing of page move operations.

   ![Seitenverschiebungsschwellenwert](assets/async-page-move.png)

1. Aktivieren Sie die Option E-Mail-Benachrichtigung **aktivieren** , um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. z.B. Erfolg, fehlgeschlagen.
1. Speichern Sie die Änderungen.

### Asynchrone MSM-Vorgänge konfigurieren {#configuring-asynchronous-msm-operations}

1. Klicken Sie in der globalen Navigation auf **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. From the web console, open the **[!UICONTROL Async Page Move Operation Job Processing Configuration.]**
1. Aktivieren Sie die Option E-Mail-Benachrichtigung **aktivieren** , um E-Mail-Benachrichtigungen für diesen Auftragsstatus zu erhalten. z.B. Erfolg, fehlgeschlagen.

   ![MSM-Konfiguration](assets/async-msm.png)

1. Speichern Sie die Änderungen.

>[!MORELIKETHIS]
>
>* [Erstellen und Organisieren von Seiten](/help/sites-authoring/managing-pages.md)
>* [Erstellen und Synchronisieren von Live Copies](/help/sites-administering/msm-livecopy.md)
>* [Konfigurieren Sie E-Mail in Experience Manager](/help/sites-administering/notification.md).
>* [Stapelweises Importieren und Exportieren von Asset-Metadaten](/help/assets/metadata-import-export.md).
>* [Verwenden Sie verbundene Assets, um DAM-Assets aus Remote-Bereitstellungen](/help/assets/use-assets-across-connected-assets-instances.md)freizugeben.

