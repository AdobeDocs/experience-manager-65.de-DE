---
title: Übersicht über Transaktionsberichte für AEM Forms on JEE
description: Zählung aller gesendeten, wiedergegebenen, in ein anderes Format konvertierten Formulare und mehr
feature: Transaction Reports
exl-id: 77e95631-6b0d-406e-a1b8-78f8d9cceb63
role: Admin, User, Developer
solution: "Experience Manager, Experience Manager Forms"
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 2%

---

# Aktivieren und Anzeigen von Transaktionsberichten für AEM Forms on JEE {#transaction-reports-overview}

<!--Transaction reports in AEM Forms on JEE let you keep a count of all transactions taken place on your AEM Forms deployment. The objective is to provide information about product usage and helps business stakeholders understand their digital processing volumes. Examples of a transaction include:

* Submission of a document
* Rendition of a document
* Conversion of a document from one file format to another 

For more information on what is considered a transaction, see [Billable APIs](../../forms/using/transaction-reports-billable-apis-jee.md). Transaction log helps you to gain information about the number of documents submitted, rendered, and converted.-->

## Transaktionsberichte aktivieren {#enable-transaction-reporting}

Standardmäßig ist die Transaktionsaufzeichnung deaktiviert. Führen Sie die folgenden Schritte aus, um Transaktionsberichte zu aktivieren:

1. Navigieren Sie auf Ihrem AEM Forms on JEE zu &quot;`/adminui`&quot;, z. B. &quot;`http://10.14.18.10:8080/adminui`&quot;.
1. Melden Sie sich als **Administrator** an.
1. Wechseln Sie zu **Einstellungen** > **Core-Systemeinstellungen** > **Konfigurationen**.
1. Aktivieren Sie das Kontrollkästchen, um die Einstellungen für **Transaktionsberichte aktivieren** und **Speichern** zu aktivieren.

   ![sample-transaction-report-jee](assets/enable-transaction-jee.png)

1. Starten Sie den Server neu.
1. Abgesehen von den Änderungen auf dem Server müssen Sie auf Client-Seite die Datei `adobe-livecycle-client.jar` in Ihrem Projekt aktualisieren, wenn Sie dieselbe Datei verwenden.

<!--
* You can [enable transaction recording](../../forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) from AEM Web Console. view transaction reports on author, processing, or publish instances. View transaction reports on author or processing instances for an aggregated sum of all transactions. View transaction reports on the publish instances for a count of all transactions that take place only on that publish instance from where the report is run.
-->

<!--Do not author content (Create adaptive forms, interactive communication, themes, and other authoring activities) and process documents (Use workflows, document services, and other processing activities) on the same AEM instance. Keep the transaction recording disabled for AEM Forms servers used to author content. Keep the transaction recording enabled for AEM Forms servers used to process documents.-->

## Anzeigen des Transaktionsberichts {#view-transaction-report}

Wenn Sie Transaktionsberichte aktivieren, können Sie über das Dashboard](#transaction-report-dashboard) auf die Informationen zu den Transaktionszahlen zugreifen. Außerdem erhalten Sie einen detaillierten [Transaktionsbericht über die Protokolldatei](#transaction-report-logfile). [ Beide werden nachfolgend erläutert:

### Transaktionsbericht über das Dashboard {#transaction-report-dashboard}

Der Transaktionsbericht über das Dashboard liefert die Gesamtzahl der Transaktionen für jeden Transaktionstyp. Beispielsweise erhalten Sie Informationen zur Gesamtanzahl der wiedergegebenen, konvertierten und gesendeten Formulare, wie im Bild dargestellt. So rufen Sie den Transaktionsbericht ab:

1. Navigieren Sie in Ihrer AEM Forms on JEE zu &quot;`/adminui`&quot;, z. B. &quot;`http://10.13.15.08:8080/adminui`&quot;.
1. Melden Sie sich als **Administrator** an.
1. Klicken Sie auf Health Monitor.
1. Navigieren Sie zur Registerkarte **Transaktionsberichte** , klicken Sie auf **Gesamttransaktionen berechnen** . Jetzt sehen Sie, dass ein Kreisdiagramm die Anzahl der PDF forms darstellt - gesendet, gerendert oder konvertiert.

![sample-transaction-report-jee](assets/transaction-piechart.png)


### Transaktionsbericht über eine Protokolldatei {#transaction-report-logfile}

Der Transaktionsbericht über die Protokolldatei enthält detaillierte Informationen zu den einzelnen Transaktionen. Um auf Transaktionsprotokolle zuzugreifen, folgen Sie dem Kontextpfad relativ zum Serverstart. Transaktionen werden standardmäßig in einer separaten Protokolldatei `transaction_log.log` erfasst. Der **Dateipfad** ist relativ zum Serverstartkontext. Der Standardpfad für verschiedene Server ist unten angegeben:

```
For Jboss Turnkey:
"<AEM_Forms_Installation>/jboss/bin/transaction_log.log"

For IBM Websphere: 
"<IBM_WAS_Profile_path>/transaction_log.log"

For Oracle Weblogic:
"<Weblogic_Domain_path>/transaction_log.log"

For Jboss Cluster:
"<Jboss home>/transaction_log.log"
```

Beispiel eines Beispiel-Transaktionsdatensatzes:
`[2024-02-28 06:11:27] [INFO] TransactionRecord{service='GeneratePDFService', operation='HtmlFileToPDF', internalService='GeneratePDFService', internalOperation='HtmlFileToPDF', transactionOperationType='CONVERT', transactionCount=1, elapsedTime=1906, transactionDate=Wed Feb 28 06:11:25 UTC 2024}`

#### Transaktionsregister {#transaction-record-structure-jee}

Die Transaktionsprotokollstruktur definiert, wie jede Transaktion über ihre verschiedenen Parameter aufgezeichnet wird, z. B. Dienst, Vorgang, Transaktionstyp und andere. Jede ist im Folgenden detailliert beschrieben. Die Struktur des Transaktionsdatensatzes stellt sich wie folgt dar:

```
TransactionRecord
{
    service='...', 
    operation='...', 
    internalService='...', 
    internalOperation='...', 
    transactionOperationType='...', 
    transactionCount=..., 
    elapsedTime=..., 
    transactionDate=...
}
```

* **service**: Name des Dienstes.
* **operation**: Vorgangsname.
* **internalService**: Name des Aufrufs, wenn ein interner Aufruf erfolgt, andernfalls identisch mit dem Dienstnamen.
* **internalOperation**: Name des Aufrufs in einem internen Aufruf, ansonsten identisch mit dem Vorgangsnamen.
* **transactionOperationType**: Typ der Transaktion (Submit, Render, Convert).
* **transactionCount**: Gesamtanzahl der Transaktionen.
* **elapsedTime**: Zeit zwischen der Initiierung des Aufrufs und der erhaltenen Antwort.
* **transactionDate**: Zeitstempel, der angibt, wann der Dienst aufgerufen wurde.

**Beispiel-Transaktionsprotokoll**:

```
[2024-02-14 14:23:25] [INFO] TransactionRecord
{
    service='BarcodedFormsService', 
    operation='decode', 
    internalService='BarcodedFormsService', 
    internalOperation='decode', 
    transactionOperationType='CONVERT', 
    transactionCount=1, 
    elapsedTime=47405, 
    transactionDate=Wed Feb 14 14:22:37 UTC 2024
}
```

## Transaktionsaufzeichnungsfrequenz {#transaction-recording-frequency}

<!--Transaction persistence involves updating the total transaction count for SUBMIT, CONVERT, and RENDER operations on the server periodically: -->

Die Häufigkeit der Aufzeichnung von Transaktionen wird durch die Aktualisierungsvorgänge auf dem Server für jedes Formular bestimmt, das erfolgreich gesendet, wiedergegeben oder konvertiert wurde.

* Im **Dashboard** wird die Transaktionsanzahl regelmäßig aktualisiert. Die Standardeinstellung ist 1 Minute. Sie können die Häufigkeit aktualisieren, indem Sie die Systemeigenschaft auf &quot;`"com.adobe.idp.dsc.transaction.recordFrequency"`&quot;festlegen. Fügen Sie beispielsweise in AEM Forms für JEE unter JBoss® `-Dcom.adobe.idp.dsc.transaction.recordFrequency=5` in `JAVA_OPTS` hinzu, um die Aktualisierungshäufigkeit auf 5 Minuten festzulegen.

* In den **Transaktionsprotokollen** erfolgt die Aktualisierung für jede Transaktion sofort, wenn ein Formular erfolgreich gesendet, wiedergegeben oder konvertiert wurde.

<!-- A transaction remains in the buffer for a specified period (Flush Buffer time + Reverse replication time). By default, it takes approximately 90 seconds for the transaction count to reflect in the transaction report.

Actions like submitting a PDF Form, using Agent UI to preview an interactive communication, or using non-standard form submission methods are not accounted as transactions. AEM Forms provides an API to record such transactions. Call the API from your custom implementations to record a transaction.

## Supported Topology {#supported-topology}

Transaction reports are available only on AEM Forms on OSGi environment. It supports author-publish, author-processing-publish, and only processing topologies. For example, topologies, see [Architecture and deployment topologies for AEM Forms](../../forms/using/transaction-reports-overview.md).

The transaction count is reverse replicated from publish instances to author or processing instances. An indicative author-publish topology is displayed below:

![simple-author-publish-topology](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>AEM Forms transaction reports does not support topologies that contain only publish instances.

### Guidelines for using transaction reports {#guidelines-for-using-transaction-reports}

* Disable transaction reports on all author instances as reports on author instances includes transactions registered during authoring activities.
* Enable the **Show transactions from publish only** option on the author instance to view cumulative transactions from all publish instances. You can also view transaction reports on each publish instance for actual transactions on that particular publish instance only.
* Do not use author instances to run workflows and process documents.
* Before using transaction reporting, if you are have a toplogy with publish servers, ensure that the reverse replication is enabled for all the publish instances.
* Transaction data is reverse-replicated from a publish instance to only corresponding author or processing instance. The author or processing instance cannot further replicate data to another instance. For example, if you have author-processing-publish topology, aggregated transaction data is replicated only to the processing instance.-->

## Ähnliche Artikel {#related-articles}

* [Liste der kostenpflichtigen APIs für AEM Forms auf JEE](../../forms/using/transaction-reports-billable-apis-jee.md)
* [Eine Transaktion für benutzerdefinierte Komponenten-APIs für AEM Forms on JEE aufzeichnen](/help/forms/using/record-transaction-custom-component-jee.md)
