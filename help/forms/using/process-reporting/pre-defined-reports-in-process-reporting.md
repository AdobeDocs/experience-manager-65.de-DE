---
title: Vordefinierte Berichte in Process Reporting
seo-title: Pre-defined reports in Process Reporting
description: Abfrage von AEM Forms zu JEE-Prozessdaten zum Erstellen von Berichten zu lange laufenden Prozessen, Prozessdauer und Workflow-Volumen
seo-description: Query for AEM Forms on JEE process data to create reports on long running processes, Process duration, and Workflow volume
uuid: 704a8886-90ea-4793-a3fc-f998f878c928
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d93375e-ec37-4445-96ea-d315676787b4
docset: aem65
exl-id: 34e55676-6332-4616-aecc-bcc8cc1e8a29
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '703'
ht-degree: 100%

---

# Vordefinierte Berichte in Process Reporting {#pre-defined-reports-in-process-reporting}

## Vordefinierte Berichte in Process Reporting {#pre-defined-reports-in-process-reporting-1}

AEM Forms Process Reporting wird mit folgenden *vorkonfigurierten* Berichte ausgeliefert:

* **[Lange laufende Prozesse](#long-running-processes)**: Bericht über alle AEM Forms-Prozesse, deren Abschluss länger als eine bestimmte Zeit dauerte
* **[Diagramm zur Prozessdauer](#process-duration-report)**: Bericht zu einem bestimmten AEM Forms-Prozess nach Dauer
* **[Workflow-Volumen](#workflow-volume-report)**: Bericht der ausgeführten und abgeschlossenen Instanzen des angegebenen Prozesses nach Datum

## Lange laufende Prozesse {#long-running-processes}

Der Bericht „Lange laufende Prozesse“ zeigt die AEM Forms-Prozesse an, deren Abschluss länger als eine bestimmte Zeit in Anspruch genommen hat.

### So führen Sie einen Bericht zu einem lange laufenden Prozess aus {#to-execute-a-long-running-process-report}

1. Um die Liste der vordefinierten Berichte in Process Reporting anzuzeigen, klicken Sie auf Baumansicht in **Process Reporting** und klicken Sie dann auf den Knoten **Berichte**.
1. Klicken Sie auf den Berichtsknoten **Lange laufende Prozesse**.

   ![long_running_node](assets/long_running_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für lange laufende Prozesse](assets/report_parameters_panel.png)

   Parameter:

   * **Dauer** (*obligatorisch*): Geben Sie eine Dauer und eine Zeiteinheit an. Zeigt alle AEM Forms-Prozesse an, deren Ausführung länger als die angegebene Dauer dauerte.
   * **Gestartet nach** (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.
   * **Gestartet vor** (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los**, um den Bericht auszuführen.

   Der Bericht wird im Bedienfeld **Bericht** rechts neben dem Fenster **Process Reporting** angezeigt.

   ![long_running_processes](assets/long_running_processes.png)

   Verwenden Sie die Optionen oben rechts im Bedienfeld **Bericht**, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Der Bericht wird mit den neuesten Daten im Speicher aktualisiert.
   * **Farbe der Legende ändern**: Wählen Sie die Farbe der Berichtslegende aus bzw. ändern Sie diese.
   * **Exportieren in CSV**: Exportieren Sie die Daten aus dem Bericht und laden Sie sie in einer durch Kommas getrennten Datei (CSV) herunter.

## Bericht zur Prozessdauer  {#process-duration-report}

Der Bericht „Prozessdauer“ zeigt die Anzahl der Instanzen eines Forms-Prozesses nach Anzahl der Tage an, die jede Instanz ausgeführt wurde.

### So führen Sie einen Bericht zur Prozessdauer aus {#to-execute-a-process-duration-report}

1. Um die vordefinierten Berichte in Process Reporting anzuzeigen, klicken Sie in der Baumansicht von **Process Reporting** auf den Knoten **Berichte**.
1. Klicken Sie auf den Berichtsknoten **Dauer der Prozesse**.

   ![process_duration_node](assets/process_duration_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für lange laufende Prozesse](assets/process_duration_params.png)

   Parameter:

   * **Prozess auswählen** (*obligatorisch*): Wählen Sie einen AEM Forms-Prozess aus.

1. Klicken Sie auf **Los**, um den Bericht auszuführen.

   Der Bericht wird im Bedienfeld **Bericht** auf der rechten Seite des Fensters „Processing Report“ angezeigt.

   ![process_duration_report](assets/process_duration_report.png)

   Verwenden Sie die Optionen oben rechts im Bedienfeld **Bericht**, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Der Bericht wird mit den neuesten Daten im Speicher aktualisiert.
   * **Farbe der Legende ändern**: Wählen Sie die Farbe der Berichtslegende aus bzw. ändern Sie diese.
   * **Exportieren in CSV**: Exportieren Sie die Daten aus dem Bericht und lagen Sie sie in einer durch Komma getrennten Datei (CSV) herunter.

## Bericht zum Workflow-Volumen {#workflow-volume-report}

Der Bericht „Workflow-Volumen“ zeigt die Anzahl der derzeit ausgeführten und abgeschlossenen Instanzen eines AEM Forms-Prozesses nach Kalendertagen an.

### So führen Sie einen Bericht zum Workflow-Volumen aus {#to-execute-a-workflow-volume-report}

1. Wenn Sie die vordefinierten Berichte im Prozess-Reporting anzeigen möchten, klicken Sie in der Baumansicht **Prozess-Reporting** auf den Knoten **Berichte**.
1. Klicken Sie auf den Berichtsknoten **Workflow-Volumen**.

   ![workflow_volumen_node](assets/workflow_volume_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter-Bedienfeld für lang laufende Prozesse](assets/workflow_volume_params.png)

   Parameter:

   * **Prozess auswählen** (*obligatorisch*): Wählen Sie einen AEM Forms-Prozess aus.

   * **Gestartet nach dem** (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht nach Prozessinstanzen, die nach dem angegebenen Datum gestartet wurden.

   * **Gestartet vor dem** (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht nach Prozessinstanzen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los**, um den Bericht auszuführen.

   Der Bericht wird im Bedienfeld **Bericht** rechts neben dem Fenster **Prozess-Reporting** angezeigt.

   ![workflow_volumen_report](assets/workflow_volume_report.png)

   Verwenden Sie die Optionen oben rechts im Bedienfeld **Bericht**, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Farbe der Legende ändern**: Farbe der Berichtslegende auswählen und ändern
   * **Exportieren in CSV**: Daten aus dem Bericht exportieren und als kommagetrennte Datei herunterladen
