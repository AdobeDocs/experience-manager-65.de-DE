---
title: Vordefinierte Berichte in Process Berichte
seo-title: Vordefinierte Berichte in Process Berichte
description: Abfrage für AEM Forms on JEE-Prozessdaten zum Erstellen von Berichten über langlaufende Prozesse, Prozessdauer und Arbeitsablaufvolumen
seo-description: Abfrage für AEM Forms on JEE-Prozessdaten zum Erstellen von Berichten über langlaufende Prozesse, Prozessdauer und Arbeitsablaufvolumen
uuid: 704a8886-90ea-4793-a3fc-f998f878c928
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d93375e-ec37-4445-96ea-d315676787b4
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---


# Vordefinierte Berichte in Process Berichte {#pre-defined-reports-in-process-reporting}

## Vordefinierte Berichte in Process Berichte {#pre-defined-reports-in-process-reporting-1}

AEM Forms Process Berichte enthält die folgenden *Out-of-the-Box*-Berichte:

* **[Lange laufende Prozesse](#long-running-processes)**: Ein Bericht zu allen AEM Forms-Prozessen, deren Abschluss mehr als eine bestimmte Zeit dauerte
* **[Prozessdauer-Diagramm](#process-duration-report)**: Ein Bericht eines bestimmten AEM Forms-Prozesses nach Dauer
* **[Arbeitsablaufvolumen](#workflow-volume-report)**: Ein Bericht der ausgeführten und abgeschlossenen Instanzen des angegebenen Prozesses nach Datum

## Lange laufende Prozesse {#long-running-processes}

Der Bericht &quot;Dauerhaft ausgeführte Prozesse&quot;zeigt die AEM Forms-Prozesse an, die länger als eine angegebene Zeitspanne zum Abschluss gebraucht haben.

### So führen Sie einen Bericht zum Ausführen eines langwierigen Prozesses aus {#to-execute-a-long-running-process-report}

1. Klicken Sie zur Ansicht der Liste vordefinierter Berichte in Process Berichte auf der Ansicht **Process Berichte** auf den Knoten **Reports**.
1. Klicken Sie auf die Berichtsknoten **Lange ausgeführte Prozesse**.

   ![long_running_node](assets/long_running_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Ansicht angezeigt.

   ![Berichtsparameter für lange Prozesse](assets/report_parameters_panel.png)

   Parameter:

   * **Dauer**  (*obligatorisch*): Geben Sie eine Dauer und eine Zeiteinheit an. Zeigt alle AEM Forms-Prozesse an, die länger als die angegebene Dauer ausgeführt wurden.
   * **Started After**  (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die nach dem angegebenen Datum gestartet wurden.
   * **Started Before**  (*optional*): Wählen Sie ein Datum aus. Filtern Sie den Bericht, um Prozessinstanzen anzuzeigen, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los**, um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht** rechts neben dem Fenster **Berichte verarbeiten** angezeigt.

   ![long_running_processes](assets/long_running_processes.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des Bereichs **Bericht**, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten in der Datenspeicherung
   * **Legendenfarbe** ändern: Auswählen und Ändern der Farbe der Berichtslegende
   * **In CSV** exportieren: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Bericht zur Prozessdauer {#process-duration-report}

Der Bericht &quot;Prozessdauer&quot;zeigt die Anzahl der Instanzen eines Forms-Prozesses nach Anzahl der Tage an, die jede Instanz ausgeführt wurde.

### So führen Sie einen Bericht zur Prozessdauer {#to-execute-a-process-duration-report} aus

1. Klicken Sie zur Ansicht der vordefinierten Berichte in Process Berichte auf der Ansicht **Process Berichte** auf den Knoten **Reports**.
1. Klicken Sie auf die Berichtsknoten **Prozessdauer**.

   ![process_duration_node](assets/process_duration_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Ansicht angezeigt.

   ![Berichtsparameter für lange Prozesse](assets/process_duration_params.png)

   Parameter:

   * **Prozess**  auswählen (*obligatorisch*): Wählen Sie einen AEM Forms-Prozess.

1. Klicken Sie auf **Los**, um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht** rechts neben dem Fenster &quot;Process Berichte&quot;angezeigt.

   ![process_duration_report](assets/process_duration_report.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des Bereichs **Bericht**, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten in der Datenspeicherung
   * **Legendenfarbe** ändern: Auswählen und Ändern der Farbe der Berichtslegende
   * **In CSV** exportieren: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen

## Workflow-Volumenbericht {#workflow-volume-report}

Der Bericht &quot;Workflow-Volumen&quot;zeigt die Anzahl der derzeit ausgeführten und abgeschlossenen Instanzen eines AEM Forms-Prozesses nach Kalendertag an.

### So führen Sie einen Workflow-Volumenbericht aus {#to-execute-a-workflow-volume-report}

1. Klicken Sie zur Ansicht der vordefinierten Berichte in Process Berichte auf der Ansicht **Process Berichte** auf den Knoten **Reports**.
1. Klicken Sie auf den Berichtknoten **Workflow Volume**.

   ![workflow_volume_node](assets/workflow_volume_node.png)

   Wenn Sie einen Bericht auswählen, wird das Bedienfeld **Berichtsparameter** rechts neben der Ansicht angezeigt.

   ![Berichtsparameter für lange Prozesse](assets/workflow_volume_params.png)

   Parameter:

   * **Prozess**  auswählen (*obligatorisch*): Wählen Sie einen AEM Forms-Prozess.

   * **Started After**  (*optional*): Wählen Sie ein Datum aus. Der Bericht zeigt Prozessinstanzen an, die nach dem angegebenen Datum gestartet wurden.

   * **Started Before**  (*optional*): Wählen Sie ein Datum aus. Der Bericht zeigt Prozessinstanzen an, die vor dem angegebenen Datum gestartet wurden.

1. Klicken Sie auf **Los**, um den Bericht auszuführen.

   Der Bericht wird im Bereich **Bericht** rechts neben dem Fenster **Berichte verarbeiten** angezeigt.

   ![workflow_volume_report](assets/workflow_volume_report.png)

   Verwenden Sie die Optionen in der oberen rechten Ecke des Bereichs **Bericht**, um die folgenden Vorgänge für den Bericht auszuführen.

   * **Aktualisieren**: Aktualisiert den Bericht mit den neuesten Daten in der Datenspeicherung
   * **Legendenfarbe** ändern: Auswählen und Ändern der Farbe der Berichtslegende
   * **In CSV** exportieren: Daten aus dem Bericht exportieren und in eine kommagetrennte Datei herunterladen
