---
title: Erste Schritte mit dem Prozess-Reporting
seo-title: Getting Started with Process Reporting
description: Die Schritte, die Sie ausführen müssen, um mit AEM Forms on JEE Process Reporting zu beginnen
seo-description: The steps you need to follow to get started with AEM Forms on JEE Process Reporting
uuid: 685cad39-da2c-411d-a0b0-201917438bcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
discoiquuid: 7c1fcde0-b983-4b24-bc19-fcee1d4f096b
docset: aem65
exl-id: 1272e854-fa64-4bfd-b073-8fbcf210e9b5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1710'
ht-degree: 100%

---

# Erste Schritte mit dem Prozess-Reporting{#getting-started-with-process-reporting}

Process Reporting gibt AEM Forms-Benutzern die Möglichkeit, Informationen über AEM Forms-Prozesse abzufragen, die derzeit in der AEM Forms-Implementierung definiert sind. Process Reporting greift jedoch nicht direkt auf Daten aus dem AEM Forms-Repository zu. Die Daten werden zunächst auf geplanter Basis im Process Reporting-Repository veröffentlicht (*vom ProcessDataPublisher &amp; ProcessDataStorage-Service* s). Die Berichte und Abfragen in Process Reporting werden dann aus den im Repository veröffentlichten Process Reporting-Daten generiert. Process Reporting wird als Bestandteil des Forms Workflow-Moduls installiert.

In diesem Artikel werden die Schritte zum Aktivieren der Veröffentlichung von AEM Forms-Daten in das Process Reporting-Repository beschrieben. Danach können Sie Process Reporting verwenden, um Berichte und Abfragen auszuführen. Der Artikel behandelt auch die verfügbaren Optionen zum Konfigurieren der Process Reporting-Services.

## Voraussetzungen für Process Reporting {#process-reporting-pre-requisites}

### Bereinigen unwichtiger Prozesse {#purge-non-essential-processes}

Wenn Sie derzeit Forms Workflow verwenden, kann die AEM Forms-Datenbank möglicherweise eine große Datenmenge enthalten

Die Process Reporting-Veröffentlichungs-Services veröffentlichen alle derzeit in der Datenbank verfügbaren AEM Forms-Daten. Dies bedeutet, dass, wenn die Datenbank ältere Daten enthält, für die Sie keine Berichte und Abfragen ausführen möchten, alle diese Daten auch im Repository veröffentlicht werden, auch wenn sie für die Berichterstellung nicht erforderlich sind. Es wird empfohlen, diese Daten zu bereinigen, bevor Sie die Services ausführen, um die Daten im Process Reporting-Repository zu veröffentlichen. Dadurch wird die Leistung sowohl des Veröffentlichungs-Services als auch des Services, der die Daten zum Reporting abfragt, verbessert.

Weitere Informationen zum Bereinigen von AEM Forms-Prozessdaten finden Sie unter [Bereinigen von Prozessdaten](https://help.adobe.com/de_DE/livecycle/11.0/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7cb2.2.html).

>[!NOTE]
>
>Tipps und Tricks für Purge Utility finden Sie im Adobe Developer Connection-Artikel zu [Bereinigen von Prozessen und Aufträgen](https://www.adobe.com/content/dam/Adobe/en/devnet/livecycle/pdfs/purging_processes_jobs.pdf).

## Konfigurieren von Process Reporting-Services {#configuring-process-reporting-services}

### Planen der Veröffentlichung von Prozessdaten {#schedule-process-data-publishing}

Die Process Reporting-Services veröffentlichen auf geplanter Basis Daten aus der AEM Forms-Datenbank in das Process Reporting-Repository.

Dieser Vorgang kann viele Ressourcen in Anspruch nehmen und die Leistung der AEM Forms-Server beeinträchtigen. Es wird empfohlen, dies außerhalb der Zeitfenster zu planen, in denen der AEM Forms-Servers ausgelastet ist.

Standardmäßig ist die Veröffentlichung von Daten so geplant, dass sie jeden Tag um 2:00 Uhr ausgeführt wird.

Um den Veröffentlichungsplan zu ändern, führen Sie folgende Schritte durch:

>[!NOTE]
>
>Wenn Sie Ihre AEM Forms-Implementierung auf einem Cluster ausführen, führen Sie die folgenden Schritte auf jedem Knoten des Clusters aus.

1. Beenden der AEM Forms-Server-Instanz.
1. &#x200B;

   * (Für Windows) Öffnen Sie die `[JBoss root]/bin/run.conf.bat`-Datei in einem Editor.
   * (Für Linux, AIX und Solaris) `[JBoss root]/bin/run.conf.sh`-Datei in einem Editor.

1. Hinzufügen des JVM-Arguments `-Dreporting.publisher.cron = <expression>.`

   Beispiel: Der folgende Cron-Ausdruck bewirkt, dass Process Reporting alle 5 Stunden AEM Forms-Daten im Process Reporting-Repository veröffentlicht:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Speichern und schließen Sie die Datei `run.conf.bat`.

1. Neustarten der AEM Forms-Server-Instanz.

1. Beenden der AEM Forms-Server-Instanz.
1. Melden Sie sich bei WebSphere Administrative Console an. Klicken Sie in der Navigationsstruktur auf **Server** > **Programm-Server** und klicken Sie anschließend im rechten Bereich auf den Servernamen.

1. Klicken Sie unter „Server Infrastructure“ auf **Java and Process Management** > **Process Definition**.

1. Klicken Sie unter „Additional Properties“ auf **Java Virtual Machine**.

   Fügen Sie in das Feld „Generic JVM Arguments“ das Argument `-Dreporting.publisher.cron = <expression>.` hinzu

   **Beispiel**: Der folgende Cron-Ausdruck bewirkt, dass Process Reporting alle 5 Stunden AEM Forms-Daten im Process Reporting-Repository veröffentlicht:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klicken Sie erst auf **Anwenden**, dann auf „OK“ und schließlich auf **Direkt in der Master-Konfiguration speichern**.
1. Neustarten der AEM Forms-Server-Instanz.
1. Beenden der AEM Forms-Server-Instanz.
1. Melden Sie sich bei Administration Console an. Die Standardadresse von WebLogic Administration Console lautet `https://[hostname]:[port]/console`.
1. Klicken Sie unter „Change Center“ auf **Lock &amp; Edit**.
1. Klicken Sie unter „Domain Structure“ auf **Environment** > **Servers** und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten **Configuration** > **Server Start**.
1. Fügen Sie im Feld „Arguments“ das JVM-Argument `-Dreporting.publisher.cron = <expression>` hinzu.

   **Beispiel**: Der folgende Cron-Ausdruck bewirkt, dass Process Reporting alle 5 Stunden AEM Forms-Daten im Process Reporting-Repository veröffentlicht:

   `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klicken Sie auf **Save** und dann auf **Activate Changes**.
1. Neustarten der AEM Forms-Server-Instanz.

![processdatapublisherservice](assets/processdatapublisherservice.png)

### ProcessDataStorage-Service {#processdatastorage-service}

Der ProcessDataStorageProvider-Service empfängt Prozessdaten vom ProcessDataPublisher-Service und speichert diese Daten im Repository für die Prozessberichterstellung.

Bei jedem Publishing-Zyklus werden die Daten in Unterordnern eines vordefinierten Stammordners gespeichert.

Sie können die Administration-Console verwenden, um den Stammspeicherort (**Standard**: `/content/reporting/pm`) und das Hierarchieformat der Unterordner (**Standard**: `/yyyy/mm/dd/hh/mi/ss`) zu konfigurieren, in denen die Prozessdaten gespeichert werden sollen.

#### So konfigurieren Sie die Repository-Speicherorte für das Prozess-Reporting {#to-configure-the-process-reporting-repository-locations}

1. Melden Sie sich mit Administrator-Berechtigungen bei der **Administration-Console** an. Die Standard-URL der Administration-Console lautet `https://'[server]:[port]'/adminui`
1. Navigieren Sie zu **Startseite** > **Services** > **Anwendungen und Services** > **Service-Management** und öffnen Sie den **ProcessDataStorageProvider**-Service.

   ![process-data-storage-service](assets/process-data-storage-service.png)

   **Stammordner**

   Der CRX-Speicherort, in dem die Prozessdaten für das Reporting gespeichert werden.

   `Default`: `/content/reporting/pm`

   **Ordnerhierarchie**

   Die Ordnerhierarchie, in der die Prozessdaten basierend auf der Erstellungszeit des Prozesses gespeichert werden.

   `Default`: `/yyyy/mm/dd/hh/mi/ss`

1. Klicken Sie auf **Speichern**.

### ReportConfiguration-Service {#reportconfiguration-service}

Der ReportConfiguration-Service wird vom Prozess-Reporting zum Konfigurieren seines Abfrage-Service verwendet.

#### So konfigurieren Sie den ReportingConfiguration-Service {#to-configure-the-reportingconfiguration-service}

1. Anmelden bei **Configuration Manager** mit CRX-Administratorberechtigungen. Die Standard-URL von Configuration Manager lautet `https://'[server]:[port]'/lc/system/console/configMgr`
1. Öffnen Sie den **ReportingConfiguration**-Service.
1. **Anzahl von Datensätzen**

   Beim Ausführen einer Abfrage im Repository kann ein Ergebnis möglicherweise eine große Anzahl von Datensätzen enthalten. Wenn die Ergebnismenge groß ist, kann die Ausführung der Abfrage Server-Ressourcen beanspruchen.

   Um große Ergebnismengen zu verarbeiten, teilt der ReportConfiguration-Service die Abfrageverarbeitung in Datensatz-Batches auf. Dadurch wird die Systemlast reduziert.

   `Default`: `1000`

   **CRX-Speicherpfad**

   Der CRX-Speicherort, in dem die Prozessdaten für die Berichterstellung gespeichert werden sollen.

   `Default`: `/content/reporting/pm`

   >[!NOTE]
   >
   >Dies ist der gleiche Speicherort, der in der ProcessDataStorage-Konfigurationsoption **Stammordner** angegeben ist..
   >
   >
   >Wenn Sie die Stammordner-Option der ProcessDataStorage-Konfiguration aktualisieren, müssen Sie den Speicherort des CRX-Speicherpfads im ReportConfiguration-Service aktualisieren.

1. Klicken Sie auf **Speichern** und schließen Sie den **CQ Configuration Manager**.

### ProcessDataPublisher-Service {#processdatapublisher-service}

Der ProcessDataPublisher-Service importiert Prozessdaten aus der AEM Forms-Datenbank und veröffentlicht die Daten zur Speicherung in den ProcessDataStorageProvider-Service.

#### Konfigurieren des ProcessDataPublisher-Services   {#to-configure-processdatapublisher-service-nbsp}

1. Melden Sie sich in der **Administrationskonsole** mit Administratorberechtigungen an.

   Die Standardeinstellung ist `https://'server':port]/adminui/`.

1. Gehen Sie zu **Startseite** > **Services** > **Programme und Services** > **Service-Verwaltung** und öffnen Sie den **ProcessDataPublisher**-Service.

![processdatapublisherservice-1](assets/processdatapublisherservice-1.png)

**Veröffentlichen von Daten**

Aktivieren Sie diese Option, um mit der Veröffentlichung von Prozessdaten zu beginnen. Standardmäßig ist die Option deaktiviert.

Aktivieren Sie die Process Reporting nur, wenn alle Konfigurationen im Zusammenhang mit Process Reporting-Komponenten ordnungsgemäß eingerichtet sind.

Alternativ können Sie diese Option verwenden, um die Veröffentlichung von Prozessdaten zu deaktivieren, wenn sie nicht mehr erforderlich ist.

`Default`: `Off`

**Batch-Intervall (Sek.)**

Bei jeder Ausführung des ProcessDataPublisher-Services teilt der Dienst zunächst die Zeit seit der letzten Ausführung des Services durch das Batch-Intervall auf. Der Service verarbeitet dann jedes Intervall von AEM Forms-Daten separat.

Dies hilft bei der Kontrolle der Datenmenge, die der Publisher bei jeder Ausführung (Batch) innerhalb eines Zyklus von Ende zu Ende verarbeitet.

Wenn der Publisher beispielsweise täglich ausgeführt wird, teilt er die Verarbeitung standardmäßig in 24 Batches mit jeweils einer Stunde auf, anstatt die gesamten Daten für einen Tag in einer einzigen Ausführung zu verarbeiten.

`Default`: `3600`

`Unit`: `Seconds`

**Sperren der Zeitüberschreitung (Sek.)**

Der Publisher-Service erhält eine Sperre, wenn er mit der Verarbeitung von Daten beginnt, sodass mehrere Instanzen des Publishers nicht gleichzeitig mit der Ausführung und Verarbeitung von Daten beginnen.

Wenn ein Publisher-Dienst, der eine Sperre erworben hat, für die vom Wert „Timeout sperren“ definierte Anzahl von Sekunden inaktiv ist, wird die Sperre aufgehoben, damit andere Publisher-Dienstinstanzen die Verarbeitung fortsetzen können.

`Default`: `3600`

`Unit`: `Seconds`

**Veröffentlichen von Daten aus**

Die AEM Forms-Umgebung enthält Daten aus der Zeit, als die Umgebung eingerichtet wurde.

Standardmäßig importiert der ProcessDataPublisher-Service alle Daten aus der AEM Forms-Datenbank.

Wenn Sie nach einem bestimmten Datum und zu einer bestimmten Uhrzeit Berichte und Abfragen zu Daten ausführen möchten, empfiehlt es sich, Datum und Uhrzeit anzugeben. Der Veröffentlichungsdienst veröffentlicht dann das Datum ab diesem Zeitpunkt.

`Default`: `01-01-1970 00:00:00`

`Format`: `dd-MM-yyyy HH:mm:ss`

## Zugriff auf die Prozess-Reporting-Benutzeroberfläche {#accessing-the-process-reporting-user-interface}

Die Benutzeroberfläche für Prozess-Reporting ist browserbasiert.

Nachdem Sie das Prozess-Reporting eingerichtet haben, können Sie mit der Arbeit mit Prozessberichten an folgendem Speicherort in Ihrer AEM Forms-Installation beginnen:

`https://<server>:<port>/lc/pr`

### Bei Prozess-Reporting anmelden {#log-in-to-process-reporting}

Wenn Sie zur Prozess-Reporting-URL navigieren (https://&lt;server>:&lt;port>/lc/pr), wird der Anmeldebildschirm angezeigt.

Geben Sie Ihre Anmeldedaten an, um sich beim Modul Prozess-Reporting anzumelden.

>[!NOTE]
>
>Zum Anmelden bei der Benutzeroberfläche Prozess-Reporting benötigen Sie die folgende AEM Forms-Berechtigung:
>
>`PERM_PROCESS_REPORTING_USER`

![Bei Prozess-Reporting anmelden](assets/capture1_new.png)

Wenn Sie sich beim Prozess-Reporting anmelden, wird die **[!UICONTROL Startseite]** angezeigt.

### Startbildschirm für Prozess-Reporting {#process-reporting-home-screen}

![process-reporting-home-screen](assets/process-reporting-home-screen.png)

**Strukturansicht für Process Reporting:** Die Strukturansicht auf der linken Seite des Startbildschirms enthält die Elemente für die Process Reporting-Module.

Die Strukturansicht besteht aus den folgenden Elementen der obersten Ebene:

**Berichte:** Dieses Element enthält die vordefinierten Berichte, die im Lieferumfang von Process Reporting enthalten sind.

Einzelheiten zu den vordefinierten Berichten finden Sie unter [Vordefinierte Berichte in Prozess-Reporting](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md).

**Ad-hoc-Abfragen:** Dieses Element enthält Optionen zum Durchführen einer filterbasierten Suche nach Prozessen und Aufgaben.

Weitere Informationen zu Ad-hoc-Abfragen finden Sie unter [Ad-hoc-Abfragen in Prozess-Reporting](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md).

**Benutzerdefiniert:** Der Knoten Benutzerdefiniert zeigt benutzerdefinierte Berichte an, die Sie erstellen.

Eine Anleitung zum Erstellen und Anzeigen benutzerdefinierter Berichte finden Sie unter [Benutzerdefinierte Berichte in Prozess-Reporting](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

**Titelleiste für Prozess-Reporting:** Die Titelleiste Prozess-Reporting enthält einige allgemeine Optionen, die Sie beim Arbeiten in der Benutzeroberfläche verwenden können.

**Prozess-Reporting-Titel:** Der Titel Prozess-Reporting wird in der linken Ecke der Titelleiste angezeigt.

Klicken Sie jederzeit auf den Titel, um zum Startbildschirm zurückzukehren.

**Letzte Aktualisierungszeit:** Die Prozessdaten werden auf geplanter Basis aus der AEM Forms-Datenbank in das Reporting-Repository veröffentlicht.

Die Zeit der letzten Aktualisierung zeigt das letzte Datum und die letzte Uhrzeit an, zu der die Datenaktualisierungen an das Reporting-Repository gesendet wurden.

Weitere Informationen zum Datenveröffentlichungsdienst und zur Planung dieses Dienstes finden Sie unter [Veröffentlichung von Prozessdaten planen](/help/forms/using/process-reporting/install-start-process-reporting.md#p-schedule-process-data-publishing-p) im Artikel Erste Schritte mit Prozessberichten.

**Prozess-Reporting-Benutzer:** Der angemeldete Benutzername wird rechts neben der Zeit der letzten Aktualisierung angezeigt.

**Dropdown-Liste der Titel der Prozess-Reporting-Leiste:** Die Dropdownliste rechts in der Prozess-Reporting-Titelleiste enthält die folgenden Optionen:

* **[!UICONTROL Synchronisieren]**: Synchronisieren Sie das eingebettete Prozess-Reporting-Repository mit der AEM Forms-Datenbank.
* **[!UICONTROL Hilfe]**: Zeigen Sie die Hilfedokumentation zu Prozess-Reporting an.
* **[!UICONTROL Abmelden]**: Abmelden von Prozess-Reporting
