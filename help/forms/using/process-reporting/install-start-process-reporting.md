---
title: Erste Schritte mit der Prozessberichterstellung
seo-title: Erste Schritte mit der Prozessberichterstellung
description: Die Schritte, die Sie für die ersten Schritte mit der AEM Forms on JEE Process Reporting
seo-description: Die Schritte, die Sie für die ersten Schritte mit der AEM Forms on JEE Process Reporting
uuid: 685cad39-da2c-411d-a0b0-201917438bcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
discoiquuid: 7c1fcde0-b983-4b24-bc19-fcee1d4f096b
docset: aem65
translation-type: tm+mt
source-git-commit: 8f90dc4865126d52e04effc9197ef7145b1a167e

---


# Getting Started with Process Reporting{#getting-started-with-process-reporting}

Die Prozessberichterstellung gibt AEM Forms-Benutzern die Möglichkeit, Informationen zu AEM Forms-Prozessen abzurufen, die derzeit in der AEM Forms-Implementierung definiert sind. Die Prozessberichterstellung greift jedoch nicht direkt aus dem AEM Forms-Repository auf Daten zu. Die Daten werden zunächst im Process Reporting Repository planmäßig veröffentlicht (*durch die ProcessDataPublisher &amp; ProcessDataStorage-* Dienste). Die Berichte und Abfragen in der Prozessberichterstellung werden dann aus den im Repository veröffentlichten Prozessberichtsdaten generiert. Die Prozessberichterstellung wird als Teil des Forms Workflow-Moduls installiert.

In diesem Artikel werden die Schritte beschrieben, mit denen die Veröffentlichung von AEM Forms-Daten im Process Reporting Repository aktiviert wird. Danach können Sie Process Reporting verwenden, um Berichte und Abfragen auszuführen. In diesem Artikel werden auch die Optionen behandelt, die zum Konfigurieren der Process Reporting Services verfügbar sind.

## Voraussetzungen für die Prozessberichterstellung {#process-reporting-pre-requisites}

### Nichtwesentliche Prozesse bereinigen {#purge-non-essential-processes}

Wenn Sie derzeit Forms Workflow verwenden, kann die AEM Forms-Datenbank möglicherweise eine große Datenmenge enthalten

Die Process Reporting Publishing Services veröffentlichen alle AEM Forms-Daten, die derzeit in der Datenbank verfügbar sind. Dies bedeutet, dass alle Daten, die in der Datenbank ältere Daten enthalten, für die Sie keine Berichte und Abfragen ausführen möchten, auch dann im Repository veröffentlicht werden, wenn sie für die Berichterstellung nicht erforderlich sind. Es wird empfohlen, diese Daten zu bereinigen, bevor Sie die Dienste ausführen, um die Daten im Process Reporting Repository zu veröffentlichen. Dadurch wird die Leistung sowohl des Herausgeberdiensts als auch des Dienstes, der die Daten zur Berichterstellung abfragt, verbessert.

Weitere Informationen zum Bereinigen von AEM Forms-Prozessdaten finden Sie unter [Bereinigen von Prozessdaten](https://help.adobe.com/en_US/livecycle/11.0/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7cb2.2.html).

>[!NOTE]
>
>Die Tipps und Tricks des Dienstprogramms &quot;Bereinigen&quot;finden Sie im Artikel Adobe Developer Connection zum [Bereinigen von Prozessen und Aufträgen](https://www.adobe.com/content/dam/Adobe/en/devnet/livecycle/pdfs/purging_processes_jobs.pdf).

## Process Reporting Services konfigurieren {#configuring-process-reporting-services}

### Planen der Prozessdatenveröffentlichung {#schedule-process-data-publishing}

Die Process Reporting Services veröffentlichen Daten aus der AEM Forms-Datenbank planmäßig im Process Reporting Repository.

Dieser Vorgang kann ressourcenintensiv sein und die Leistung der AEM Forms-Server beeinträchtigen. Es wird empfohlen, diesen Zeitraum außerhalb der Zeitfenster des AEM Forms-Servers zu planen.

Standardmäßig ist die Veröffentlichung von Daten planmäßig für jeden Tag um 2:00 Uhr geplant.

Führen Sie die folgenden Schritte aus, um den Veröffentlichungsplan zu ändern:

>[!NOTE]
>
>Wenn Sie Ihre AEM Forms-Implementierung auf einem Cluster ausführen, führen Sie die folgenden Schritte auf jedem Knoten des Clusters aus.

1. Beenden Sie die AEM Forms-Serverinstanz.
1. 

   * (Für Windows) Öffnen Sie die `[JBoss root]/bin/run.conf.bat` Datei in einem Editor.
   * (Für Linux, AIX und Solaris) `[JBoss root]/bin/run.conf.sh` in einem Editor.

1. JVM-Argument hinzufügen `-Dreporting.publisher.cron = <expression>.`

   Beispiel: Der folgende Cron-Ausdruck bewirkt, dass Process Reporting AEM Forms-Daten alle 5 Stunden im Process Reporting-Repository veröffentlicht.

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Save and close the `run.conf.bat` file.

1. Starten Sie die AEM Forms-Serverinstanz neu.

1. Beenden Sie die AEM Forms-Serverinstanz.
1. Log in to the WebSphere Administrative Console. In the navigation tree, click **Servers** > **Application servers** and then, in the right pane, click the server name.

1. Klicken Sie unter „Server Infrastructure“ auf **Java and Process Management** > **Process Definition**.

1. Klicken Sie unter „Additional Properties“ auf **Java Virtual Machine**.

   In the Generic JVM arguments box, add the argument `-Dreporting.publisher.cron = <expression>.`

   **Beispiel**: Der folgende Cron-Ausdruck bewirkt, dass Process Reporting AEM Forms-Daten alle 5 Stunden im Process Reporting-Repository veröffentlicht.

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Click **Apply**, click OK, and then click **Save directly to the master configuration**.
1. Starten Sie die AEM Forms-Serverinstanz neu.
1. Beenden Sie die AEM Forms-Serverinstanz.
1. Melden Sie sich bei WebLogic Administration Console an. Die Standardadresse von WebLogic Administration Console ist `https://[hostname]:[port]/console`.
1. Klicken Sie unter „Change Center“ auf **Lock &amp; Edit**.
1. Klicken Sie unter „Domain Structure“ auf **Environment**> **Servers** und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten **Configuration** > **Server Start**.
1. Fügen Sie im Feld Arguments das JVM-Argument hinzu `-Dreporting.publisher.cron = <expression>`.

   **Beispiel**: Der folgende Cron-Ausdruck bewirkt, dass Process Reporting AEM Forms-Daten alle 5 Stunden im Process Reporting-Repository veröffentlicht.

   `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klicken Sie auf **Save** und dann auf **Activate Changes**.
1. Starten Sie die AEM Forms-Serverinstanz neu.

![processdatapublisherservice](assets/processdatapublisherservice.png)

### ProcessDataStorage-Dienst {#processdatastorage-service}

Der ProcessDataStorageProvider-Dienst empfängt Prozessdaten vom ProcessDataPublisher-Dienst und speichert die Daten im Process Reporting-Repository.

Bei jedem Veröffentlichungszyklus werden die Daten in Unterordnern eines vordefinierten Stammordners gespeichert.

Sie können die Administrationskonsole verwenden, um den Stammordner zu konfigurieren (**Standard**: `/content/reporting/pm`) Speicherort und Unterordner (**Standard**: `/yyyy/mm/dd/hh/mi/ss`) Hierarchieformat, in dem die Prozessdaten gespeichert werden.

#### So konfigurieren Sie die Speicherorte des Process Reporting-Repositorys {#to-configure-the-process-reporting-repository-locations}

1. Melden Sie sich mit Administratorberechtigungen bei **Administration Console** an. The default URL of Administration Console is `https://[server]:[port]/adminui`
1. Navigieren Sie zu **Startseite** > **Dienste** > **Anwendungen und Dienste** >**Dienstverwaltung** und öffnen Sie den Dienst **ProcessDataStorageProvider** .

   ![process-data-storage-service](assets/process-data-storage-service.png)

   **RootFolder**

   Der CRX-Speicherort, in dem die Prozessdaten zur Berichterstellung gespeichert werden.

   `Default`: `/content/reporting/pm`

   **Ordnerhierarchie**

   Die Ordnerhierarchie, in der die Prozessdaten basierend auf der Prozesserstellungszeit gespeichert werden.

   `Default`: `/yyyy/mm/dd/hh/mi/ss`

1. Klicken Sie auf **Speichern**.

### ReportConfiguration-Dienst {#reportconfiguration-service}

Der ReportConfiguration-Dienst wird von Process Reporting zur Konfiguration des Prozessberichtsabfragedienstes verwendet.

#### To configure the ReportingConfiguration service {#to-configure-the-reportingconfiguration-service}

1. Melden Sie sich mit den Anmeldeinformationen des CRX-Administrators bei **Configuration Manager** an. Die Standard-URL von Configuration Manager lautet `https://[server]:[port]/lc/system/console/configMgr`
1. Öffnen Sie den **ReportingConfiguration** -Dienst.
1. **Anzahl der Datensätze**

   Beim Ausführen einer Abfrage im Repository kann ein Ergebnis möglicherweise eine große Anzahl von Datensätzen enthalten. Wenn die Ergebnismenge groß ist, kann die Abfrageausführung Serverressourcen beanspruchen.

   Zur Verarbeitung großer Ergebnisse teilt der ReportConfiguration-Dienst die Abfrageverarbeitung in Datensatzstapel auf. Dadurch wird die Systemlast verringert.

   `Default`: `1000`

   **CRX-Speicherpfad**

   Der CRX-Speicherort, in dem die Prozessdaten für die Berichterstellung gespeichert werden.

   `Default`: `/content/reporting/pm`

   >[!NOTE]
   >
   >Dies ist der gleiche Speicherort, der in der Option &quot; **Stammordner**&quot;der ProcessDataStorage-Konfigurationsoption angegeben ist.
   >
   >
   >Wenn Sie die Option &quot;Stammordner&quot;in der ProcessDataStorage-Konfiguration aktualisieren, müssen Sie den Speicherort des CRX-Speicherpfads im ReportConfiguration-Dienst aktualisieren.

1. Klicken Sie auf **Speichern** und schließen Sie **CQ Configuration Manager**.

### ProcessDataPublisher-Dienst {#processdatapublisher-service}

Der ProcessDataPublisher-Dienst importiert Prozessdaten aus der AEM Forms-Datenbank und veröffentlicht die Daten zum Speichern im ProcessDataStorageProvider-Dienst.

#### So konfigurieren Sie den ProcessDataPublisher-Dienst {#to-configure-processdatapublisher-service-nbsp}

1. Melden Sie sich mit Administratorberechtigungen bei **Administration Console** an.

   The default URL is `https://[server]:port]/adminui/`.

1. Navigieren Sie zu **Startseite** > **Dienste** > **Anwendungen und Dienste** >**Dienstverwaltung** und öffnen Sie den **ProcessDataPublisher** -Dienst.

![processdatapublisherservice-1](assets/processdatapublisherservice-1.png)

**Daten veröffentlichen**

Aktivieren Sie diese Option, um die Veröffentlichung von Prozessdaten zu starten. Standardmäßig ist die Option deaktiviert.

Aktivieren Sie die Prozessberichterstellung nur, wenn alle Konfigurationen im Zusammenhang mit Process Reporting-Komponenten ordnungsgemäß eingerichtet sind.

Alternativ können Sie diese Option verwenden, um die Prozessdatenveröffentlichung zu deaktivieren, wenn sie nicht mehr erforderlich ist.

`Default`: `Off`

**Stapelintervall (s)**

Jedes Mal, wenn der ProcessDataPublisher-Dienst ausgeführt wird, teilt der Dienst die Zeit seit der letzten Ausführung des Dienstes durch das Stapelintervall auf. Der Dienst verarbeitet dann jedes Intervall der AEM Forms-Daten separat.

Dies hilft bei der Steuerung der Datengröße, die der Herausgeber während jeder Ausführung (Batch) innerhalb eines Zyklus verarbeitet.

Wenn der Herausgeber beispielsweise jeden Tag ausgeführt wird, wird die Verarbeitung standardmäßig nicht für einen Tag in einem einzigen Vorgang verarbeitet, sondern in 24 Stapel mit einer Stunde aufgeteilt.

`Default`: `3600`

`Unit`: `Seconds`

**Zeitlimit sperren (Sek.)**

Der Herausgeber-Dienst erwirbt eine Sperre, wenn er mit der Verarbeitung der Daten beginnt, sodass nicht mehrere Instanzen des Herausgebers gleichzeitig mit der Ausführung und Verarbeitung der Daten beginnen.

Wenn ein Herausgeberdienst, der eine Sperre erworben hat, für die durch den Wert &quot;Sperren-Timeout&quot;definierte Anzahl von Sekunden untätig ist, wird die Sperre freigegeben, damit andere Instanzen des Herausgeberdienstes die Verarbeitung fortsetzen können.

`Default`: `3600`

`Unit`: `Seconds`

**Daten veröffentlichen aus**

Die AEM Forms-Umgebung enthält Daten aus dem Zeitpunkt, zu dem die Umgebung eingerichtet wurde.

Standardmäßig importiert der ProcessDataPublisher-Dienst alle Daten aus der AEM Forms-Datenbank.

Wenn Sie nach einem bestimmten Datum und einer bestimmten Uhrzeit Berichte und Abfragen zu Daten ausführen möchten, sollten Sie je nach Ihren Berichterstattungsanforderungen Datum und Uhrzeit angeben. Der Veröffentlichungsdienst veröffentlicht dann das Datum ab diesem Zeitpunkt.

`Default`: `01-01-1970 00:00:00`

`Format`: `dd-MM-yyyy HH:mm:ss`

## Zugriff auf die Benutzeroberfläche der Prozessberichterstellung {#accessing-the-process-reporting-user-interface}

Die Benutzeroberfläche für Process Reporting ist browserbasiert.

Nachdem Sie die Prozessberichterstellung eingerichtet haben, können Sie mit der Prozessberichterstellung an folgendem Speicherort in Ihrer AEM Forms-Installation beginnen:

`https://<server>:<port>/lc/pr`

### Bei der Prozessberichterstellung anmelden {#log-in-to-process-reporting}

Wenn Sie zur Prozessberichterstellungs-URL (https://&lt;server>:&lt;port>/lc/pr) navigieren, wird der Anmeldebildschirm angezeigt.

Geben Sie Ihre Anmeldedaten für die Anmeldung beim Modul Prozessberichterstellung an.

>[!NOTE]
>
>Um sich bei der Benutzeroberfläche der Prozessberichterstellung anzumelden, benötigen Sie die folgende AEM Forms-Berechtigung:
>
>`PERM_PROCESS_REPORTING_USER`

![Bei Prozessberichterstellung anmelden](assets/capture1_new.png)

Wenn Sie sich bei der Prozessberichterstellung anmelden, wird der Bildschirm &quot; **[!UICONTROL Start]** &quot;angezeigt.

### Home-Bildschirm &quot;Process Reporting&quot; {#process-reporting-home-screen}

![process-reporting-home-screen](assets/process-reporting-home-screen.png)

**** Prozessberichterstellungs-Strukturansicht: Die Strukturansicht auf der linken Seite des Startbildschirms enthält die Elemente für die Process Reporting Module.

Die Strukturansicht besteht aus den folgenden Elementen der obersten Ebene:

**** Berichte: Dieses Element enthält die vordefinierten Berichte, die im Lieferumfang von Process Reporting enthalten sind.

Weitere Informationen zu vordefinierten Berichten finden Sie unter [Vordefinierte Berichte in der Prozessberichterstellung](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md).

**** Ad-hoc-Abfragen: Dieses Element enthält Optionen zum Durchführen einer filterbasierten Suche nach Prozessen und Aufgaben.

Weitere Informationen zu Ad-hoc-Abfragen finden Sie unter [Ad-hoc-Abfragen in der Prozessberichterstellung](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md).

**** Benutzerdefiniert: Der Knoten Benutzerdefiniert zeigt benutzerdefinierte Berichte an, die Sie erstellen.

Informationen zum Erstellen und Anzeigen benutzerdefinierter Berichte finden Sie unter [Benutzerspezifische Berichte in der Prozessberichterstellung](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

**** Prozessberichterstellungstitel-Leiste: Die Titelleiste der Prozessberichterstellung enthält einige allgemeine Optionen, die Sie beim Arbeiten in der Benutzeroberfläche verwenden können.

**** Titel der Prozessberichterstellung: Der Titel &quot;Prozessberichterstellung&quot;wird in der linken Ecke der Titelleiste angezeigt.

Klicken Sie jederzeit auf den Titel, um zum Startbildschirm zurückzukehren.

**** Letzte Aktualisierungszeit: Die Prozessdaten werden planmäßig aus der AEM Forms-Datenbank in das Process Reporting Repository veröffentlicht.

Die letzte Aktualisierungszeit zeigt das letzte Datum und die Uhrzeit an, zu der die Datenaktualisierungen an das Process Reporting Repository gesendet wurden.

Weitere Informationen zum Datenveröffentlichungsdienst und zum Planen dieses Dienstes finden Sie unter Prozessdatenveröffentlichung [planen](/help/forms/using/process-reporting/install-start-process-reporting.md#p-schedule-process-data-publishing-p) im Artikel Erste Schritte mit Prozessberichten.

**** Process Reporting-Benutzer: Der angemeldete Benutzername wird rechts neben der Uhrzeit der letzten Aktualisierung angezeigt.

**** Dropdown-Liste der Prozessberichtstitelleiste: Die Dropdownliste rechts in der Titelleiste der Prozessberichterstellung enthält die folgenden Optionen:

* **[!UICONTROL Synchronisieren]**: Synchronisieren Sie das eingebettete Process Reporting Repository mit der AEM Forms-Datenbank.
* **[!UICONTROL Hilfe]**: Lesen Sie die Hilfedokumentation zur Prozessberichterstellung.
* **[!UICONTROL Abmelden]**: Abmelden bei der Prozessberichterstellung

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
