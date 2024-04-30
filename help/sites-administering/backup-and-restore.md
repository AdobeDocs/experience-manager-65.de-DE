---
title: Sichern und Wiederherstellen
description: Erfahren Sie, wie Sie AEM-Inhalte und Konfigurationen sichern und wiederherstellen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: dd26dade-b769-483e-bc11-dcfa5ed1f87e
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2314'
ht-degree: 100%

---

# Sichern und Wiederherstellen{#backup-and-restore}

Es gibt zwei Möglichkeiten zum Sichern und Wiederherstellen von Repository-Inhalten in AEM:

* Sie können ein externes Backup des Repositorys erstellen und dieses an einem sicheren Ort speichern.  Wenn das Repository abstürzt, können Sie den vorherigen Zustand des Repositorys wieder herstellen.
* Sie können interne Versionen der Repository-Inhalte erstellen.  Diese Versionen werden zusammen mit den Inhalten im Repository gespeichert, sodass Sie Knoten und hierarchische Strukturen, die Sie gelöscht oder geändert haben, schnell wiederherstellen können.

## Allgemein {#general}

Der hier beschriebene Ansatz bezieht sich auf die Sicherung und Wiederherstellung des gesamten Systems.

Falls Sie nur einen kleineren Teil der Inhalte sichern und/oder wiederherstellen müssen, der verloren gegangen ist, ist nicht unbedingt eine Wiederherstellung des Systems erforderlich:

* Sie können die Daten entweder von einem anderen System aus in Form eines Pakets abrufen
* oder das Backup auf einem temporären System wiederherstellen, dann ein Inhaltspaket erstellen und dieses auf dem System bereitstellen, auf dem dieser Inhalt fehlt.

Weitere Informationen finden Sie im nachfolgenden Abschnitt [Paket-Backup](/help/sites-administering/backup-and-restore.md#package-backup).

## Timing {#timing}

Führen Sie ein Backup nicht zeitgleich mit einer Datenspeicherbereinigung durch, da dies die Ergebnisse beider Prozesse beeinträchtigen kann.

## Offline-Backup {#offline-backup}

Sie können immer ein Offline-Backup durchführen.  Dafür müssen Sie zwar AEM stoppen, dies kann aber hinsichtlich der benötigten Zeit im Vergleich zu einem Online-Backup effizienter sein.

In den meisten Fällen erstellen Sie mithilfe eines Dateisystem-Snapshots eine schreibgeschützte Kopie der zu dem Zeitpunkt gespeicherten Inhalte.  Führen Sie folgende Schritte zum Erstellen eines Offline-Backups aus:

* Stoppen Sie das Programm.
* Erstellen Sie ein Snapshot-Backup.
* Starten Sie das Programm.

Da das Snapshot-Backup normalerweise nur ein paar Sekunden dauert, ist die gesamte Ausfallzeit nicht länger als ein paar Minuten.

## Online-Backup {#online-backup}

Bei dieser Backup-Methode erstellen Sie ein Backup vom gesamten Repository, einschließlich aller darunter bereitgestellten Anwendungen wie beispielsweise AEM.  Das Backup enthält die Inhalte, den Versionsverlauf, die Konfiguration, die Software, Hotfixes, benutzerdefinierte Anwendungen, Protokolldateien, Suchindizes usw.  Falls Sie die Clustering-Option verwenden oder der freigegebene Ordner ein Unterverzeichnis von `crx-quickstart` ist (entweder physikalisch oder per Softlink), wird das freigegebene Verzeichnis ebenfalls gesichert.

Sie können das gesamte Repository (und alle Anwendungen) zu einem späteren Zeitpunkt wiederherstellen.

Bei dieser Methode wird ein „Hot“- oder „Online“-Backup durchgeführt, d. h. das Backup wird durchgeführt, während das Repository läuft.  So kann das Repository während des Backups verwendet werden. Diese Methode kann bei standardmäßigen, TAR-basierten Repository-Instanzen verwendet werden.

Bei der Erstellung eines Backups haben Sie die folgenden Möglichkeiten:

* Backup in einem Verzeichnis mithilfe des integrierten AEM-Backup-Tools
* Backup in einem Verzeichnis mithilfe eines Dateisystem-Snapshots

In jedem Fall wird während des Backups ein Image (oder Snapshot) des Repositorys erstellt.  Anschließend sollte der Backup-Agent des Systems dafür Sorge tragen, dass dieses Image an ein dediziertes Backup-System (Bandlaufwerk) übermittelt wird.

>[!NOTE]
>
>Falls die AEM Online Backup-Funktion auf einer AEM-Instanz mit einer benutzerdefinierten Blob-Store-Konfiguration verwendet wird, ist es ratsam, einen Datenspeicherpfad außerhalb des Verzeichnisses `crx-quickstart` zu konfigurieren und den Datenspeicher separat zu sichern.

>[!CAUTION]
>
>Bei dem Online-Backup wird nur das Dateisystem gesichert.  Wenn Sie die Repository-Inhalte und/oder die Repository-Dateien in einer Datenbank speichern, muss diese Datenbank separat gesichert werden.  Falls Sie AEM mit MongoDB verwenden, lesen Sie die Dokumentation zur Verwendung der [nativen Backup-Tools von MongoDB](https://docs.mongodb.org/manual/tutorial/backup-with-mongodump/).

### AEM-Online-Backup {#aem-online-backup}

Mithilfe eines Online-Backups von Ihrem Repository können Sie Backup-Dateien erstellen, herunterladen und löschen.  Dies ist eine „Hot“- oder „Online“-Backup-Funktion, d. h. sie kann während der normalen Verwendung des Repositorys im Lese-/Schreibmodus ausgeführt werden.

>[!CAUTION]
>
>Führen Sie die AEM Online Backup-Funktion nicht zeitgleich mit der [Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md) oder der [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#how-to-run-offline-revision-cleanup) durch. Dies beeinträchtigt die Systemleistung.

Zu Beginn eines Backups können Sie den **Zielpfad** und/oder eine **Verzögerung** festlegen.

**Zielpfad** Die Backup-Dateien werden für gewöhnlich im übergeordneten Ordner des Ordners gespeichert, in dem sich die Schnellstart-JAR-Datei (.jar) befindet. Wenn sich die AEM-JAR-Datei beispielsweise im Ordner „/InstallationKits/AEM“ befindet, wird das Backup im Ordner „/InstallationKits“ generiert. Sie können auch ein Ziel an einem Speicherort Ihrer Wahl angeben.

Wenn unter **Zielpfad** ein Verzeichnis angegeben ist, wird das Image des Repositorys in diesem Verzeichnis erstellt. Falls dasselbe Verzeichnis mehrmals (oder immer) zum Speichern von Backups verwendet wird:

* werden die geänderten Dateien im Repository entsprechend unter dem Zielpfad geändert
* werden im Repository gelöschte Dateien unter dem Zielpfad gelöscht
* werden im Repository erstellte Dateien unter dem Zielpfad erstellt

>[!NOTE]
>
>Wenn Sie unter **Zielpfad** einen Dateinamen mit der Erweiterung **.zip** angeben, wird das Repository in einem temporären Verzeichnis gesichert. Die Inhalte dieses temporären Verzeichnisses werden dann komprimiert und in der ZIP-Datei gespeichert.
>
>Von dieser Vorgehensweise wird jedoch aus folgenden Gründen abgeraten:
>
>* Es ist zusätzlicher Speicherplatz während des Backup-Prozesses erforderlich (für das temporäre Verzeichnis und die ZIP-Datei)
>* Der Komprimierungsprozess wird vom Repository ausgeführt, sodass möglicherweise die Leistung beeinträchtigt wird.
>* Es kommt zu einer Verzögerung des Backup-Prozesses.
>* Bis zur Java-Version 1.6 ist Java nur in der Lage, ZIP-Dateien bis zu einer Größe von 4 GB zu erstellen.
>
>Ist es notwendig, dass Sie eine ZIP-Datei als Backup-Format erstellen, sollten Sie das Backup in einem Verzeichnis speichern und dann die ZIP-Datei mit einem Komprimierungsprogramm erstellen.

**Verzögerung** Zeigt eine Zeitverzögerung (in Millisekunden) an, damit die Repository-Leistung nicht beeinträchtigt wird. Standardmäßig wird das Repository-Backup mit voller Geschwindigkeit ausgeführt. Sie können die Geschwindigkeit der Erstellung eines Online-Backups verringern, sodass das Backup nicht dazu führt, dass andere Aufgaben langsamer ausgeführt werden.

Achten Sie bei der Festlegung einer sehr großen Verzögerung darauf, dass das Online-Backup nicht länger als 24 Stunden dauert. Andernfalls verwerfen Sie dieses Backup, da es möglicherweise nicht alle Binärdateien enthält.
 Eine Verzögerung von 1 ms führt in der Regel zu einer 10 %igen CPU-Auslastung und eine Verzögerung von 10 ms führt normalerweise zu einer CPU-Auslastung von weniger als 3 %. Die Gesamtverzögerung in Sekunden können Sie wie folgt schätzen: Repository-Größe (in MB) multipliziert mit der Verzögerung in Millisekunden geteilt durch 2 (wenn die ZIP-Option verwendet wird) bzw. geteilt durch 4 (wenn das Backup in einem Verzeichnis gespeichert wird). Das bedeutet, dass sich die Backup-Zeit durch Sichern eines 200 MB großen Repositorys in einem Verzeichnis bei einer Verzögerung von 1 Millisekunde um 50 Sekunden erhöht. 

>[!NOTE]
>
>Interne Details zu dem Prozess finden Sie in [Funktionsweise von AEM Online Backup](#how-aem-online-backup-works).

So erstellen Sie ein Backup:

1. Melden Sie sich bei AEM als Admin an.

1. Navigieren Sie zu **Tools > Vorgänge > Sicherung**.
1. Klicken Sie auf **Erstellen**. Die Backup-Konsole wird geöffnet.

   ![chlimage_1-1](assets/chlimage_1-1a.png)

1. Legen sie in der Backup-Konsole den **[Zielpfad](#aem-online-backup)** und die **[Verzögerung](#aem-online-backup)** fest.

   ![chlimage_1-2](assets/chlimage_1-2a.png)

   >[!NOTE]
   >
   >Die Backup-Konsole ist auch verfügbar unter:
   >
   >
   >` https://<*hostname*>:<*port-number*>/libs/granite/backup/content/admin.html`

1. Klicken Sie auf **Speichern**. Daraufhin wird eine Fortschrittsleiste eingeblendet, die den Fortschritt des Backups anzeigt.

   >[!NOTE]
   >
   >Sie können ein Backup jederzeit **abbrechen**.

1. Wenn das Backup abgeschlossen ist, werden die ZIP-Dateien im Backup-Fenster aufgeführt.

   ![chlimage_1-3](assets/chlimage_1-3a.png)

   >[!NOTE]
   >
   >Backup-Dateien, die nicht länger benötigt werden, können über die Konsole entfernt werden. Wählen Sie im linken Bereich die Backup-Datei aus und klicken Sie dann auf **Löschen**.

   >[!NOTE]
   >
   >Wenn Sie ein Backup in ein Verzeichnis durchgeführt haben und der Backup-Prozess abgeschlossen ist, schreibt AEM nicht in das Zielverzeichnis.

### Automatisieren von AEM Online Backup {#automating-aem-online-backup}

Sofern möglich, sollte ein Online-Backup bei geringer Systemauslastung (z. B. morgens) durchgeführt werden.

Backups können mithilfe des HTTP-Clients `wget` oder `curl` automatisiert werden. Nachfolgend sehen Sie einige Beispiele, wie ein Backup mithilfe von „curl“ automatisiert werden kann.

#### Sichern im Standard-Zielverzeichnis {#backing-up-to-the-default-target-directory}

>[!CAUTION]
>
>Im folgenden Beispiel müssen unter Umständen verschiedene Parameter im `curl`-Befehl für Ihre Instanz konfiguriert werden, wie zum Beispiel der Hostname (`localhost`), der Port (`4502`), das Admin-Kennwort (`xyz`) und der Dateiname (`backup.zip`).

```shell
curl -u admin:admin -X POST http://localhost:4502/system/console/jmx/com.adobe.granite:type=Repository/op/startBackup/java.lang.String?target=backup.zip
```

Die Backup-Datei bzw. das Backup-Verzeichnis wird auf dem Server im übergeordneten Ordner des Ordners erstellt, der den `crx-quickstart`-Ordner enthält (genauso wie beim Erstellen des Backups mithilfe eines Browsers). Wenn Sie beispielsweise AEM im Verzeichnis `/InstallationKits/crx-quickstart/` installiert haben, wird das Backup im Verzeichnis `/InstallationKits` erstellt.

Die Rückgabe beim „curl“-Befehl erfolgt sofort. Daher müssen Sie dieses Verzeichnis überwachen, um zu sehen, wann die ZIP-Datei fertig ist. Während das Backup erstellt wird, wird ein temporäres Verzeichnis (dessen Name auf dem der fertigen ZIP-Datei basiert) angezeigt, das schließlich in einer ZIP-Datei komprimiert wird. Beispiel:

* Name der resultierenden ZIP-Datei: `backup.zip`
* Name des temporären Verzeichnisses: `backup.f4d5.temp`

#### Sichern in einem anderen als dem Standard-Zielverzeichnis {#backing-up-to-a-non-default-target-directory}

Normalerweise wird die Backup-Datei bzw. das Verzeichnis auf dem Server im übergeordneten Ordner des Ordners erstellt, der den Ordner `crx-quickstart` enthält.

Soll das Backup (jedweder Art) an einem anderen Speicherort gespeichert werden, können Sie einen absoluten Pfad zum `target`-Parameter im `curl`-Befehl festlegen.

Beispielsweise um `backupJune.zip` im Verzeichnis `/Backups/2012` zu generieren:

```shell
curl -u admin:admin -X POST http://localhost:4502/system/console/jmx/com.adobe.granite:type=Repository/op/startBackup/java.lang.String?target=/Backups/2012/backupJune.zip"
```

>[!CAUTION]
>
>Wenn Sie einen anderen Anwendungs-Server (z. B. JBoss) verwenden, wird das Online-Backup möglicherweise nicht wie erwartet ausgeführt, da das Zielverzeichnis schreibgeschützt ist. Wenden Sie sich in diesem Fall an den Support.

>[!NOTE]
>
>Ein Backup kann auch [mithilfe von MBeans, die von AEM bereitgestellt werden](/help/sites-administering/jmx-console.md), ausgelöst werden.

### Backup mittels Dateisystem-Snapshot {#filesystem-snapshot-backup}

Der hier beschriebene Prozess ist besonders für große Repositorys geeignet.

>[!NOTE]
>
>Wenn Sie diesen Backup-Ansatz verwenden möchten, muss Ihr System Dateisystem-Snapshots unterstützen. Für Linux bedeutet dies beispielsweise, dass Ihre Dateisysteme auf einem logischen Volume platziert werden sollten.

1. Erstellen Sie einen Snapshot des Dateisystems, in dem AEM bereitgestellt wird.

1. Mounten Sie den Dateisystem-Snapshot.
1. Führen Sie ein Backup aus und unmounten Sie den Snapshot.

### Funktionsweise von AEM Online Backup {#how-aem-online-backup-works}

AEM Online Backup umfasst eine Reihe von internen Aktionen, die die Integrität der zu sichernden Daten und der zu erstellenden Backup-Dateien sicherstellen. Diese sind für diejenigen, die daran interessiert sind, nachfolgend aufgeführt.

Für das Online-Backup wird der folgende Algorithmus verwendet:

1. Wenn Sie eine ZIP-Datei erstellen, ist der erste Schritt die Erstellung oder Lokalisierung des Zielverzeichnisses.

   * Beim Sichern in eine ZIP-Datei wird ein temporäres Verzeichnis erstellt. Der Verzeichnisname beginnt mit `backup.` und endet mit `.temp`, z. B. `backup.f4d3.temp`.
   * Beim Sichern in ein Verzeichnis wird der im Zielpfad festgelegte Name verwendet. Es kann ein vorhandenes Verzeichnis verwendet werden. Andernfalls wird ein neues Verzeichnis erstellt.

     Es wird eine leere Datei mit dem Namen `backupInProgress.txt` im Zielverzeichnis erstellt, wenn das Backup gestartet wird. Diese Datei wird gelöscht, sobald das Backup abgeschlossen ist.

1. Die Dateien werden aus dem Quellverzeichnis in das Zielverzeichnis (oder das temporäre Verzeichnis, wenn eine Zip-Datei erstellt wird) kopiert. Der Segmentspeicher wird vor dem Datenspeicher kopiert, um eine Beschädigung des Repositorys zu vermeiden. Der Index und die Zwischenspeicherdaten werden bei der Erstellung des Backups ausgelassen. Daher werden die Daten aus dem Zwischenspeicher `crx-quickstart/repository/cache` und dem Index `crx-quickstart/repository/index` nicht in das Backup eingeschlossen. Die Fortschrittsbalkenanzeige zeigt 0 % bis 70 % an, wenn eine ZIP-Datei erstellt wird, oder 0 % bis 100 %, wenn keine ZIP-Datei erstellt wird.

1. Falls das Backup in einem vorab vorhandenen Verzeichnis erstellt wird, werden die „alten“ Dateien im Zielverzeichnis gelöscht. Alte Dateien sind Dateien, die im Quellverzeichnis nicht vorhanden sind.

Das Kopieren der Dateien in das Zielverzeichnis lässt sich in vier Phasen unterteilen:

1. In der ersten Kopierphase (Fortschrittsanzeige 0 % bis 63 %, wenn eine ZIP-Datei erstellt wird, oder 0 % bis 90 %, wenn keine ZIP-Datei erstellt wird) werden alle Dateien kopiert, während das Repository normal ausgeführt wird. Der Prozess umfasst zwei Phasen:

   * Phase A: Alles mit Ausnahme des Datenspeichers wird kopiert (mit Verzögerung).
   * Phase B: Nur der Datenspeicher wird kopiert (mit Verzögerung).

1. In der zweiten Kopierphase (Fortschrittsanzeige 63 % bis 65,8 %, wenn eine ZIP-Datei erstellt wird, oder 90 % bis 94 %, wenn keine ZIP-Datei erstellt wird) werden nur die Dateien kopiert, die seit dem Start der ersten Kopierphase im Quellverzeichnis erstellt oder geändert wurden. Abhängig von der Aktivität des Repositorys kann dies bedeuten, dass gar keine Dateien bis hin zu einer erheblichen Anzahl an Dateien enthalten sind (da die erste Dateikopierphase in der Regel am längsten dauert). Der Kopierprozess entspricht dem der ersten Phase (Phase A und Phase B mit Verzögerung).
1. In der dritten Kopierphase (Fortschrittsanzeige 65,8 % bis 68,6 %, wenn eine ZIP-Datei erstellt wird, oder 94 % bis 98 %, wenn keine ZIP-Datei erstellt wird) werden nur Dateien kopiert, die seit dem Start der zweiten Kopierphase im Quellverzeichnis erstellt oder geändert wurden. Abhängig von der Aktivität des Repositorys kann dies bedeuten, dass gar keine Dateien oder nur sehr wenige Dateien zu kopieren sind (da die zweite Dateikopierphase in der Regel sehr schnell abgeschlossen ist). Der Kopierprozess entspricht dem der zweiten Phase (Phase A und Phase B, aber ohne Verzögerung).
1. Die Dateikopierphasen 1 bis 3 werden zeitgleich ausgeführt, während das Repository ausgeführt wird. Nur die Dateien, die seit dem Start der dritten Kopierphase im Quellordner erstellt oder geändert wurden, werden kopiert. Abhängig von der Aktivität des Repositorys kann dies bedeuten, dass gar keine Dateien oder nur äußerst wenige Dateien zu kopieren sind (da die zweite Dateikopierphase in der Regel sehr schnell abgeschlossen ist). Die Fortschrittsanzeige zeigt 68,6 % bis 70 % an, wenn eine ZIP-Datei erstellt wird, oder 98 % bis 100 %, wenn keine ZIP-Datei erstellt wird. Der Kopierprozess entspricht der dritten Phase.
1. Abhängig vom Ziel:

   * Wenn eine ZIP-Datei festgelegt wurde, wird diese nun im temporären Verzeichnis erstellt. Die Fortschrittsanzeige liegt bei 70 % bis 100 %. Das temporäre Verzeichnis wird dann gelöscht.
   * Handelt es sich bei dem Ziel um ein Verzeichnis, wird die leere Datei mit dem Namen `backupInProgress.txt` gelöscht, um anzuzeigen, dass das Backup abgeschlossen ist.

## Wiederherstellen des Backups {#restoring-the-backup}

Sie können ein Backup wie folgt wiederherstellen:

* Wenn Sie ein Backup mittels eines Dateisystem-Snapshots durchgeführt haben, können Sie einfach ein Image des Systems wiederherstellen.
* Falls Sie das Backup in Form einer ZIP-Datei erstellt haben, entpacken Sie einfach die Inhalte in einen neuen Ordner und starten Sie AEM von diesem Speicherort aus.

## Paket-Backup {#package-backup}

Zum Sichern und Wiederherstellen von Inhalten können Sie eine der Package Manager-Versionen verwenden. Dabei werden Inhalte über das Inhaltspaketformat gesichert und wiederhergestellt. Der Package Manager bietet mehr Flexibilität beim Definieren und Verwalten von Paketen.

Weitere Informationen zu den Funktionen und Austauschbeziehungen von jedem dieser einzelnen Inhaltspaketformate finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

### Backup-Umfang {#scope-of-backup}

Wenn Sie Knoten entweder mit dem Package Manager oder dem Content Zipper sichern, speichert CRX die folgenden Informationen:

* die Repository-Inhalte unterhalb der Baumstruktur, die Sie ausgewählt haben.
* die Knotentyp-Definitionen, die für die zu sichernden Inhalte verwendet werden.
* die Namespace-Definitionen, die für die zu sichernden Inhalte verwendet werden.

Bei Durchführung des Backups gehen in AEM folgende Informationen verloren:

* Der Versionsverlauf
