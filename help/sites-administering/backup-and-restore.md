---
title: Sichern und Wiederherstellen
seo-title: Backup and Restore
description: Erfahren Sie, wie Sie Ihre AEM Inhalte und Konfigurationen sichern und wiederherstellen können.
seo-description: Learn how to backup and restore your AEM content.
uuid: 446a466f-f508-4430-9e50-42cd4463760e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: eb8bbb85-ca2f-4877-8ee0-bb1ee8b7d8de
exl-id: dd26dade-b769-483e-bc11-dcfa5ed1f87e
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '2283'
ht-degree: 43%

---

# Sichern und Wiederherstellen{#backup-and-restore}

Es gibt zwei Möglichkeiten zum Sichern und Wiederherstellen von Repository-Inhalten in AEM:

* Sie können eine externe Sicherung des Repositorys erstellen und an einem sicheren Speicherort speichern. Wenn das Repository kaputt geht, können Sie den vorherigen Status wiederherstellen.
* Sie können interne Versionen des Repository-Inhalts erstellen. Diese Versionen werden zusammen mit dem Inhalt im Repository gespeichert, sodass Sie Knoten und Bäume, die Sie geändert oder gelöscht haben, schnell wiederherstellen können.

## Allgemein {#general}

Der hier beschriebene Ansatz gilt für die Systemsicherung und -wiederherstellung.

Wenn Sie eine kleine Menge an Inhalt sichern und/oder wiederherstellen müssen, der verloren geht, ist nicht unbedingt eine Wiederherstellung des Systems erforderlich:

* Sie können die Daten entweder von einem anderen System über ein Package abrufen
* oder Sie die Sicherung auf einem temporären System wiederherstellen, erstellen Sie ein Inhaltspaket und stellen es auf dem System bereit, wo dieser Inhalt fehlt.

Weitere Informationen finden Sie im nachfolgenden Abschnitt [Paket-Backup](/help/sites-administering/backup-and-restore.md#package-backup).

## Timing {#timing}

Führen Sie keine Sicherung parallel zur Datenspeicherbereinigung durch, da dies die Ergebnisse beider Prozesse beeinträchtigen könnte.

## Offline-Sicherung {#offline-backup}

Sie können immer eine Offline-Sicherung durchführen. Dies erfordert eine Ausfallzeit von AEM, kann jedoch im Hinblick auf die erforderliche Zeit im Vergleich zu einem Online-Backup sehr effizient sein.

In den meisten Fällen verwenden Sie einen Dateisystem-Snapshot, um zu diesem Zeitpunkt eine schreibgeschützte Kopie des Speichers zu erstellen. Führen Sie die folgenden Schritte aus, um eine Offline-Sicherung zu erstellen:

* Stoppen Sie das Programm.
* Erstellen Sie ein Snapshot-Backup.
* Starten Sie das Programm.

Da das Snapshot-Backup in der Regel nur einige Sekunden dauert, beträgt die gesamte Ausfallzeit weniger als einige Minuten.

## Online-Backup {#online-backup}

Diese Sicherungsmethode erstellt eine Sicherungskopie des gesamten Repositorys, einschließlich aller darin bereitgestellten Anwendungen, z. B. AEM. Die Sicherung umfasst Inhalt, Versionsverlauf, Konfiguration, Software, Hotfixes, benutzerdefinierte Programme, Protokolldateien, Suchindizes usw. Falls Sie die Clustering-Option verwenden oder der freigegebene Ordner ein Unterverzeichnis von `crx-quickstart` ist (entweder physikalisch oder per Softlink), wird das freigegebene Verzeichnis ebenfalls gesichert.

Sie können das gesamte Repository (und alle Anwendungen) zu einem späteren Zeitpunkt wiederherstellen.

Diese Methode dient als &quot;Hot&quot;- oder &quot;Online&quot;-Backup, damit sie während der Ausführung des Repositorys durchgeführt werden kann. So kann das Repository während des Backups verwendet werden. Diese Methode kann bei standardmäßigen, TAR-basierten Repository-Instanzen verwendet werden.

Bei der Erstellung eines Backups haben Sie die folgenden Möglichkeiten:

* Backup in einem Verzeichnis mithilfe des integrierten AEM-Backup-Tools
* Sichern in einem Verzeichnis mithilfe eines Dateisystem-Snapshots

In jedem Fall erstellt das Backup ein Bild (oder einen Schnappschuss) des Repositorys. Anschließend sollte der Backup-Agent des Systems dafür Sorge tragen, dass dieses Image an ein dediziertes Backup-System (Bandlaufwerk) übermittelt wird.

>[!NOTE]
>
>Falls die AEM Online Backup-Funktion auf einer AEM-Instanz mit einer benutzerdefinierten Blob-Store-Konfiguration verwendet wird, ist es ratsam, einen Datenspeicherpfad außerhalb des Verzeichnisses `crx-quickstart` zu konfigurieren und den Datenspeicher separat zu sichern.

>[!CAUTION]
>
>Das Online-Backup sichert nur das Dateisystem. Wenn Sie den Repository-Inhalt und/oder die Repository-Dateien in einer Datenbank speichern, muss diese Datenbank separat gesichert werden. Wenn Sie AEM mit MongoDB verwenden, lesen Sie die Dokumentation zur Verwendung der [Native Backup-Tools von MongoDB](https://docs.mongodb.org/manual/tutorial/backup-with-mongodump/).

### AEM Online-Backup {#aem-online-backup}

Mit einer Online-Sicherung Ihres Repositorys können Sie Sicherungsdateien erstellen, herunterladen und löschen. Es handelt sich um eine &quot;Hot&quot;- oder &quot;Online&quot;-Backup-Funktion, die ausgeführt werden kann, während das Repository normal im Lese-/Schreibmodus verwendet wird.

>[!CAUTION]
>
>Führen Sie die AEM Online Backup-Funktion nicht zeitgleich mit der [Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md) oder der [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#how-to-run-offline-revision-cleanup) durch. Dies beeinträchtigt die Systemleistung.

Zu Beginn eines Backups können Sie den **Zielpfad** und/oder eine **Verzögerung** festlegen.

**Zielpfad** Die Backup-Dateien werden für gewöhnlich im übergeordneten Ordner des Ordners gespeichert, in dem sich die Schnellstart-JAR-Datei (.jar) befindet. Wenn sich die AEM-JAR-Datei beispielsweise im Ordner „/InstallationKits/AEM“ befindet, wird das Backup im Ordner „/InstallationKits“ generiert. Sie können auch ein Ziel an einem Speicherort Ihrer Wahl angeben.

Wenn die Variable **TargetPath** ein Verzeichnis ist, wird das Bild des Repositorys in diesem Verzeichnis erstellt. Wenn derselbe Ordner mehrmals (oder immer) zum Speichern der Sicherung verwendet wird,

* geänderte Dateien im Repository werden entsprechend im TargetPath geändert
* gelöschte Dateien im Repository werden im TargetPath gelöscht
* erstellte Dateien im Repository werden im TargetPath erstellt.

>[!NOTE]
>
>Wenn **TargetPath** auf den Dateinamen mit der Erweiterung eingestellt ist **.zip**, wird das Repository in einem temporären Verzeichnis gesichert und der Inhalt dieses temporären Ordners wird komprimiert und in der ZIP-Datei gespeichert.
>
>Dieser Ansatz wird deshalb nicht empfohlen, weil
>
>* Es erfordert zusätzlichen Speicherplatz während des Sicherungsprozesses (temporärer Ordner plus ZIP-Datei).
>* Der Komprimierungsprozess wird vom Repository durchgeführt und kann die Leistung beeinflussen.
>* Dadurch wird der Backup-Prozess verzögert.
>* Bis zu Java 1.6 Java kann nur ZIP-Dateien mit einer Größe von bis zu 4 Gigabyte erstellen.
>
>Ist es notwendig, dass Sie eine ZIP-Datei als Backup-Format erstellen, sollten Sie das Backup in einem Verzeichnis speichern und dann die ZIP-Datei mit einem Komprimierungsprogramm erstellen.

**Verzögerung** Zeigt eine Zeitverzögerung (in Millisekunden) an, damit die Repository-Leistung nicht beeinträchtigt wird. Standardmäßig wird das Repository-Backup mit voller Geschwindigkeit ausgeführt. Sie können die Geschwindigkeit der Erstellung eines Online-Backups verringern, sodass das Backup nicht dazu führt, dass andere Aufgaben langsamer ausgeführt werden.

Achten Sie bei der Festlegung einer sehr großen Verzögerung darauf, dass das Online-Backup nicht länger als 24 Stunden dauert. Andernfalls verwerfen Sie dieses Backup, da es möglicherweise nicht alle Binärdateien enthält.
 Eine Verzögerung von 1 ms führt in der Regel zu einer 10 %igen CPU-Auslastung und eine Verzögerung von 10 ms führt normalerweise zu einer CPU-Auslastung von weniger als 3 %. Die Gesamtverzögerung in Sekunden kann wie folgt geschätzt werden: Repository-Größe in MB, multipliziert mit der Verzögerung in Millisekunden, dividiert durch 2 (wenn die ZIP-Option verwendet wird) oder dividiert durch 4 (beim Sichern in ein Verzeichnis). Das bedeutet, dass eine Sicherung in einem Verzeichnis eines 200 MB großen Repositorys mit 1 ms Verzögerung die Sicherungsdauer um etwa 50 Sekunden erhöht.

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
   >Sie können **Abbrechen** jederzeit eine laufende Sicherung durchführen.

1. Nach Abschluss der Sicherung werden die ZIP-Dateien im Sicherungsfenster angezeigt.

   ![chlimage_1-3](assets/chlimage_1-3a.png)

   >[!NOTE]
   >
   >Backup-Dateien, die nicht mehr benötigt werden, können über die Konsole entfernt werden. Wählen Sie die Sicherungsdatei im linken Bereich aus und klicken Sie auf **Löschen**.

   >[!NOTE]
   >
   >Wenn Sie eine Sicherung in einem Verzeichnis durchgeführt haben: Nach Abschluss des Sicherungsprozesses wird AEM nicht in das Zielverzeichnis schreiben.

### Automatisieren AEM Online-Backup {#automating-aem-online-backup}

Wenn möglich, sollte das Online-Backup ausgeführt werden, wenn das System wenig ausgelastet ist, z. B. morgens.

Backups können mithilfe des HTTP-Clients `wget` oder `curl` automatisiert werden. Die folgenden Beispiele zeigen, wie Sie die Sicherung mithilfe von curl automatisieren.

#### Sichern in das standardmäßige Target-Verzeichnis {#backing-up-to-the-default-target-directory}

>[!CAUTION]
>
>Im folgenden Beispiel müssen unter Umständen verschiedene Parameter im `curl`-Befehl für Ihre Instanz konfiguriert werden, wie zum Beispiel der Hostname (`localhost`), der Port (`4502`), das Admin-Kennwort (`xyz`) und der Dateiname (`backup.zip`).

```shell
curl -u admin:admin -X POST http://localhost:4502/system/console/jmx/com.adobe.granite:type=Repository/op/startBackup/java.lang.String?target=backup.zip
```

Die Backup-Datei bzw. das Backup-Verzeichnis wird auf dem Server im übergeordneten Ordner des Ordners erstellt, der den `crx-quickstart`-Ordner enthält (genauso wie beim Erstellen des Backups mithilfe eines Browsers). Wenn Sie beispielsweise AEM im Verzeichnis `/InstallationKits/crx-quickstart/` installiert haben, wird das Backup im Verzeichnis `/InstallationKits` erstellt.

Der curl-Befehl gibt sofort zurück. Daher müssen Sie dieses Verzeichnis überwachen, um zu sehen, wann die ZIP-Datei bereit ist. Während das Backup erstellt wird, kann ein temporäres Verzeichnis (mit dem Namen, der auf dem der endgültigen ZIP-Datei basiert) angezeigt werden, am Ende wird dies komprimiert. Beispiel:

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
>Bei Verwendung eines anderen Anwendungsservers (z. B. JBoss) funktioniert die Online-Sicherung möglicherweise nicht wie erwartet, da der Zielordner nicht schreibbar ist. Wenden Sie sich in diesem Fall an den Support.

>[!NOTE]
>
>Ein Backup kann auch ausgelöst werden [Verwendung der von AEM bereitgestellten MBeans](/help/sites-administering/jmx-console.md).

### Backup von Dateisystem Snapshot {#filesystem-snapshot-backup}

Der hier beschriebene Prozess ist besonders für große Repositorys geeignet.

>[!NOTE]
>
>Wenn Sie diesen Backup-Ansatz verwenden möchten, muss Ihr System Dateisystem-Snapshots unterstützen. Für Linux bedeutet dies beispielsweise, dass Ihre Dateisysteme auf einem logischen Volume platziert werden sollten.

1. Erstellen Sie einen Snapshot des Dateisystems, in dem AEM bereitgestellt wird.

1. Bereiten Sie den Dateisystem-Snapshot.
1. Führen Sie eine Sicherung durch und heben Sie die Bereitstellung des Snapshots auf.

### Funktionsweise AEM Online-Sicherung {#how-aem-online-backup-works}

AEM Online Backup besteht aus einer Reihe interner Aktionen, die die Integrität der zu sichernden Daten und der zu erstellenden Backup-Dateien gewährleisten. Diese sind für diejenigen, die daran interessiert sind, nachfolgend aufgeführt.

Für das Online-Backup wird der folgende Algorithmus verwendet:

1. Wenn Sie eine ZIP-Datei erstellen, ist der erste Schritt die Erstellung oder Lokalisierung des Zielverzeichnisses.

   * Beim Sichern in eine ZIP-Datei wird ein temporäres Verzeichnis erstellt. Der Verzeichnisname beginnt mit `backup.` und endet mit `.temp`; Beispiel, `backup.f4d3.temp`.
   * Beim Sichern in ein Verzeichnis wird der im Zielpfad angegebene Name verwendet. Es kann ein vorhandenes Verzeichnis verwendet werden. Andernfalls wird ein neues Verzeichnis erstellt.

     Es wird eine leere Datei mit dem Namen `backupInProgress.txt` im Zielverzeichnis erstellt, wenn das Backup gestartet wird. Diese Datei wird gelöscht, wenn das Backup abgeschlossen ist.

1. Die Dateien werden beim Erstellen einer ZIP-Datei aus dem Quellverzeichnis in das Zielverzeichnis (oder in das temporäre Verzeichnis) kopiert. Der Segmentspeicher wird vor dem Datenspeicher kopiert, um eine Beschädigung des Repositorys zu vermeiden. Der Index und die Zwischenspeicherdaten werden bei der Erstellung des Backups ausgelassen. Daher werden die Daten aus dem Zwischenspeicher `crx-quickstart/repository/cache` und dem Index `crx-quickstart/repository/index` nicht in das Backup eingeschlossen. Die Fortschrittsbalkenanzeige zeigt 0 % bis 70 % an, wenn eine ZIP-Datei erstellt wird, oder 0 % bis 100 %, wenn keine ZIP-Datei erstellt wird.

1. Wenn die Sicherung in einem bereits vorhandenen Verzeichnis durchgeführt wird, werden &quot;alte&quot;Dateien im Zielverzeichnis gelöscht. Alte Dateien sind Dateien, die nicht im Quellverzeichnis vorhanden sind.

Die Dateien werden in vier Phasen in das Zielverzeichnis kopiert:

1. In der ersten Kopierphase (Fortschrittsanzeige 0 % - 63 % beim Erstellen einer ZIP-Datei oder 0 % - 90 % bei keiner ZIP-Datei) werden alle Dateien kopiert, während das Repository normal ausgeführt wird. Der Prozess umfasst zwei Phasen:

   * Phase A - Alles außer dem Datenspeicher (mit Verzögerung) wird kopiert.
   * Phase B - nur der Datenspeicher wird kopiert (mit Verzögerung).

1. In der zweiten Kopierstufe (Fortschrittsanzeige 63 % - 65,8 % beim Erstellen einer ZIP-Datei oder 90 % - 94 %, wenn keine ZIP-Datei erstellt wird) werden nur Dateien kopiert, die seit dem Start der ersten Kopierphase im Quellverzeichnis erstellt oder geändert wurden. Abhängig von der Aktivität des Repositorys kann dies bedeuten, dass gar keine Dateien bis hin zu einer signifikanten Anzahl an Dateien enthalten sind (da die erste Dateikopierphase in der Regel sehr viel Zeit in Anspruch nimmt). Der Kopierprozess entspricht dem der ersten Phase (Phase A und Phase B mit Verzögerung).
1. In der dritten Kopierphase (Fortschrittsanzeige 65,8 % bis 68,6 %, wenn eine ZIP-Datei erstellt wird, oder 94 % bis 98 %, wenn keine ZIP-Datei erstellt wird) werden nur Dateien kopiert, die seit dem Start der zweiten Kopierphase im Quellverzeichnis erstellt oder geändert wurden. Abhängig von der Aktivität des Repositorys kann dies bedeuten, dass gar keine Dateien oder nur sehr wenige Dateien zu kopieren sind (da die zweite Dateikopierphase in der Regel sehr schnell abgeschlossen ist). Der Kopierprozess entspricht dem der zweiten Phase (Phase A und Phase B, aber ohne Verzögerung).
1. Dateikopieretappen von ein bis drei werden alle gleichzeitig ausgeführt, während das Repository ausgeführt wird. Es werden nur Dateien kopiert, die seit dem Start der dritten Kopierphase im Quellverzeichnis erstellt oder geändert wurden. Abhängig von der Aktivität des Repositorys kann dies bedeuten, dass gar keine Dateien oder nur äußerst wenige Dateien zu kopieren sind (da die zweite Dateikopierphase in der Regel sehr schnell abgeschlossen ist). Die Fortschrittsanzeige zeigt 68,6 % bis 70 % an, wenn eine ZIP-Datei erstellt wird, oder 98 % bis 100 %, wenn keine ZIP-Datei erstellt wird. Der Kopiervorgang ähnelt dem dritten Schritt.
1. Je nach Zielgruppe:

   * Wenn eine ZIP-Datei angegeben wurde, wird diese jetzt aus dem temporären Verzeichnis erstellt. Fortschrittsanzeige 70 % - 100 %. Das temporäre Verzeichnis wird dann gelöscht.
   * Handelt es sich bei dem Ziel um ein Verzeichnis, wird die leere Datei mit dem Namen `backupInProgress.txt` gelöscht, um anzuzeigen, dass das Backup abgeschlossen ist.

## Wiederherstellen des Backups {#restoring-the-backup}

Sie können eine Sicherung wie folgt wiederherstellen:

* Falls Sie eine Dateisystem-Snapshot-Sicherung durchgeführt haben, können Sie einfach ein Bild des Systems wiederherstellen.
* Falls Sie das Backup als ZIP-Datei erstellt haben, entpacken Sie einfach den Inhalt in einen neuen Ordner und starten Sie AEM von diesem Speicherort aus.

## Paketsicherung {#package-backup}

Um Inhalte zu sichern und wiederherzustellen, können Sie einen der Paketmanager verwenden, der das Inhaltspaket-Format zum Sichern und Wiederherstellen von Inhalten verwendet. Der Package Manager bietet mehr Flexibilität beim Definieren und Verwalten von Paketen.

Weitere Informationen zu den Funktionen und Kompromisse der einzelnen Inhaltspaketformate finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

### Umfang der Sicherung {#scope-of-backup}

Wenn Sie Knoten entweder mit dem Package Manager oder dem Content Zipper sichern, speichert CRX die folgenden Informationen:

* Der Repository-Inhalt unterhalb der ausgewählten Baumstruktur.
* Die Knotentypdefinitionen, die für den gesicherten Inhalt verwendet werden.
* Die Namespace-Definitionen, die für den gesicherten Inhalt verwendet werden.

Bei Durchführung des Backups gehen in AEM folgende Informationen verloren:

* Der Versionsverlauf
