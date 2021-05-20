---
title: Vordefinierte Berichte in Prozessberichten
seo-title: Vordefinierte Berichte in Prozessberichten
description: Abfragen von AEM Forms on JEE-Prozessdaten zum Erstellen von Berichten zu langwierigen Prozessen, Prozessdauer und Workflow-Volumen
seo-description: Abfragen von AEM Forms on JEE-Prozessdaten zum Erstellen von Berichten zu langwierigen Prozessen, Prozessdauer und Workflow-Volumen
uuid: 704a8886-90ea-4793-a3fc-f998f878c928
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d93375e-ec37-4445-96ea-d315676787b4
docset: aem65
exl-id: 34e55676-6332-4616-aecc-bcc8cc1e8a29
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Vordefinierte Berichte in Prozessberichten {#pre-defined-reports-in-process-reporting}

## Vordefinierte Berichte in Prozessberichten {#pre-defined-reports-in-process-reporting-1}

AEM Forms Process Reporting wird mit den folgenden *nativen* Berichten geliefert:

* **[Lange laufende Prozesse](#long-running-processes)**: Ein Bericht über alle AEM Forms-Prozesse, deren Abschluss länger als eine bestimmte Zeit dauerte
* **[Diagramm](#process-duration-report)** für die Prozessdauer: Ein Bericht eines bestimmten AEM Forms-Prozesses nach Dauer
* **[Workflow-Volumen](#workflow-volume-report)**: Ein Bericht der ausgeführten und abgeschlossenen Instanzen des angegebenen Prozesses nach Datum

## Lange laufende Prozesse {#long-running-processes}

Der Bericht &quot;Lange laufende Prozesse&quot;zeigt die AEM Forms-Prozesse an, deren Abschluss länger als eine bestimmte Zeit in Anspruch genommen hat.

### So führen Sie einen Bericht zum langwierigen Prozess aus {#to-execute-a-long-running-process-report}

1. Um die Liste der vordefinierten Berichte in der Prozessberichterstellung anzuzeigen, klicken Sie in der Baumstruktur **Prozessberichte** auf den Knoten **Berichte** .
1. Klicken Sie auf den Berichtknoten **Lange laufende Prozesse** .

   ![long_running_node](assets/long_running_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für langlaufende Prozesse](assets/report_parameters_panel.png)

   Parameter:

   * **Dauer**  (*erforderlich*): Geben Sie eine Dauer und eine Zeiteinheit an. Zeigt alle AEM Forms-Prozesse an, die länger als die angegebene Dauer ausgeführt wurden.
   * **Started After**  (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.
   * **Started Before**  (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los** , um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht** rechts neben dem Fenster **Prozessberichte** angezeigt.

   ![long_running_processes](assets/long_running_processes.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des Bedienfelds **Bericht** , um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Ändern der Legendenfarbe**: Auswählen und Ändern der Farbe der Berichtslegende
   * **Exportieren in CSV**: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Bericht zur Prozessdauer {#process-duration-report}

Der Bericht &quot;Prozessdauer&quot;zeigt die Anzahl der Instanzen eines Forms-Prozesses nach Anzahl der Tage an, die jede Instanz ausgeführt wurde.

### So führen Sie einen Bericht zur Prozessdauer aus {#to-execute-a-process-duration-report}

1. Um die vordefinierten Berichte in Process Reporting anzuzeigen, klicken Sie in der Baumstruktur **Process Reporting** auf den Knoten **Berichte** .
1. Klicken Sie auf den Berichtknoten **Verarbeitungsdauer** .

   ![process_duration_node](assets/process_duration_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für langlaufende Prozesse](assets/process_duration_params.png)

   Parameter:

   * **Wählen Sie Process**  (*mandatory*) aus: Wählen Sie einen AEM Forms-Prozess aus.

1. Klicken Sie auf **Los** , um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht** rechts neben dem Fenster &quot;Process Reporting&quot;angezeigt.

   ![process_duration_report](assets/process_duration_report.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des Bedienfelds **Bericht** , um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Ändern der Legendenfarbe**: Auswählen und Ändern der Farbe der Berichtslegende
   * **Exportieren in CSV**: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Workflow-Volumenbericht {#workflow-volume-report}

Der Bericht Workflow-Volumen zeigt die Anzahl der derzeit ausgeführten und abgeschlossenen Instanzen eines AEM Forms-Prozesses nach Kalendertagen an.

### So führen Sie einen Workflow-Volumenbericht aus {#to-execute-a-workflow-volume-report}

1. Um die vordefinierten Berichte in Process Reporting anzuzeigen, klicken Sie in der Baumstruktur **Process Reporting** auf den Knoten **Berichte** .
1. Klicken Sie auf den Berichtknoten **Workflow-Volumen** .

   ![workflow_volumen_node](assets/workflow_volume_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Baumansicht angezeigt.

   ![Berichtsparameter für langlaufende Prozesse](assets/workflow_volume_params.png)

   Parameter:

   * **Wählen Sie Process**  (*mandatory*) aus: Wählen Sie einen AEM Forms-Prozess aus.

   * **Started After**  (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.

   * **Started Before**  (*optional*): Wählen Sie ein Datum aus. Filtert den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los** , um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht** rechts neben dem Fenster **Prozessberichte** angezeigt.

   ![workflow_volumen_report](assets/workflow_volume_report.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des Bedienfelds **Bericht** , um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten im Speicher
   * **Ändern der Legendenfarbe**: Auswählen und Ändern der Farbe der Berichtslegende
   * **Exportieren in CSV**: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen
