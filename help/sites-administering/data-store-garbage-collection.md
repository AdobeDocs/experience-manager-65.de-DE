---
title: Datenspeicherbereinigung
description: Erfahren Sie, wie Sie die Datenspeicherbereinigung zur Freigabe von Festplattenspeicher konfigurieren können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: 0dc4a8ce-5b0e-4bc9-a6f5-df2a67149e22
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '1891'
ht-degree: 92%

---

# Datenspeicherbereinigung {#data-store-garbage-collection}

Wenn ein herkömmliches WCM-Asset entfernt wird, kann der Verweis zum zugrunde liegenden Datenspeichereintrag aus der Knotenhierarchie entfernt werden. Der Datenspeichereintrag selbst bleibt allerdings bestehen. Dieser nicht referenzierte Datenspeichereintrag wird dadurch zu „Ausschussdaten“, die nicht aufbewahrt werden müssen. In Fällen, in denen mehrere Garbage Assets vorhanden sind, ist es von Vorteil, diese zu entfernen, um Speicherplatz zu sparen und die Backup- und Dateisystemwartungsleistung zu optimieren.

Meist neigen WCM-Anwendungen dazu, Informationen zu sammeln. Gelöscht werden die Informationen allerdings bei Weitem nicht so oft. Auch wenn neue Bilder hinzugefügt werden und sogar wenn alte Versionen ersetzt werden, behält das Versionskontrollsystem dennoch die alte Version bei und unterstützt die Möglichkeit, bei Bedarf zu dieser Version zurückzukehren. Daher wird der Großteil der Inhalte, die wir zum System hinzufügen, permanent gespeichert. Was ist also die typische Quelle für „Ausschussdaten“ im Repository, die wir bereinigen möchten?

AEM verwendet das Repository als Speicher für mehrere interne und speicherinterne Aktivitäten:

* Zusammengestellte und heruntergeladene Pakete
* Für die Veröffentlichungsreplikation erstellte temporäre Dateien
* Workflow-Payloads
* Während des DAM-Renderings temporär erstellte Assets

Wenn eines dieser temporären Objekte groß genug ist, Speicherplatz im Datenspeicher zu beanspruchen, und wenn das Objekt schließlich nicht mehr genutzt wird, bleibt der Datenspeichereintrag selbst als „Ausschuss“ vorhanden. In einer typischen WCM-Autoren-/Veröffentlichungsanwendung ist die größte Quelle von Ausschussdaten dieser Art in der Regel der Prozess der Aktivierung der Veröffentlichung. Wenn Daten für die Veröffentlichung repliziert werden, werden diese zunächst in einem effizienten Datenformat namens „Durbo“ in Sammlungen erfasst und im Repository unter `/var/replication/data` gespeichert. Die Datenbundles übersteigen oft den kritischen Größenschwellenwert für den Datenspeicher und werden daher als Datenspeichersätze gespeichert. Wenn die Replikation abgeschlossen ist, wird der Knoten in `/var/replication/data` gelöscht, doch der Datenspeichersatz bleibt als „Garbage“ bestehen.

Eine weitere Quelle von wiederherstellbaren Ausschussdaten sind Pakete. Paketdaten werden – wie alles andere auch – im Repository und bei Paketen, die größer sind als 4 KB, im Datenspeicher gespeichert. Während eines Entwicklungsprojekts oder im Laufe der Zeit können Pakete bei der Wartung eines Systems viele Male zusammengestellt und neu erstellt werden, wobei jede Version zu einem neuen Datenspeichereintrag führt, durch den der Dateneintrag der vorherigen Version verwaist.

## Wie funktioniert die automatische Datenspeicherbereinigung? {#how-does-data-store-garbage-collection-work}

Wenn das Repository mit einem externen Datenspeicher konfiguriert wurde, [wird die automatische Datenspeicherbereinigung im Rahmen des wöchentlichen Wartungsfensters automatisch ausgeführt](/help/sites-administering/data-store-garbage-collection.md#automating-data-store-garbage-collection). Die oder der Systemadmin kann bei Bedarf die [Datenspeicherbereinigung auch manuell ausführen](#running-data-store-garbage-collection). Im Allgemeinen wird empfohlen, die Datenspeicherbereinigung regelmäßig durchzuführen, doch sollten die folgenden Faktoren bei der Planung von Datenspeicherbereinigungen berücksichtigt werden:

* Datenspeicherbereinigungen nehmen Zeit in Anspruch und können die Leistung beeinträchtigen, was entsprechend eingeplant werden sollte.
* Das Entfernen der „Ausschuss“-Dateneinträge im Datenspeicher hat keinen Einfluss auf die normale Leistung. Es handelt sich also nicht um eine Leistungsoptimierung.
* Wenn die Speichernutzung und damit verbundene Faktoren wie die Sicherungszeiten kein Problem darstellen, kann die automatische Datenspeicherbereinigung getrost zeitlich verschoben werden.

Der Datenspeicherbereiniger merkt sich zunächst den aktuellen Zeitstempel, wenn der Prozess beginnt. Die Sammlung der Daten wird mithilfe eines Multi-Pass-Mark-/Sweep-Pattern-Algorithmus durchgeführt.

In der ersten Phase führt der Datenspeicher-Garbage Collector einen umfassenden Durchlauf aller Repository-Inhalte durch. Zu jedem Inhaltsobjekt mit einem Verweis zum Datenspeichereintrag sucht er die Datei im Dateisystem, führt eine Metadatenaktualisierung durch und ändert das „Zuletzt geändert“- oder MTIME-Attribut. An diesem Punkt erhalten Dateien, auf die in dieser Phase zugegriffen wurde, einen neueren Zeitstempel als den ursprünglichen Basiszeitstempel.

In der zweiten Phase durchläuft der Datenspeicherbereiniger die physische Verzeichnisstruktur des Datenspeichers auf eine sehr ähnliche Weise wie eine Suche. Er untersucht das „Zuletzt geändert“- oder MTIME-Attribut der Datei und bestimmt Folgendes:

* Wenn das MTIME neuer als der ursprüngliche Basiszeitstempel ist, wurde die Datei entweder in der ersten Phase gefunden oder es handelt sich um eine völlig neue Datei, die während des laufenden Bereinigungsprozesses zum Repository hinzugefügt wurde. In beiden Fällen wird der Dateneintrag als aktiv betrachtet und die Datei nicht gelöscht.
* Wenn das MTIME-Attribut vor dem ursprünglichen Basiszeitstempel liegt, handelt es sich bei der Datei nicht um eine aktiv referenzierte Datei und sie wird als entfernbarer „Datenausschuss“ betrachtet.

Dieser Ansatz funktioniert bei einem einzelnen Knoten mit einem privaten Datenspeicher sehr gut. Handelt es sich jedoch um einen gemeinsam genutzten Datenspeicher, bedeutet dies, dass potenziell aktive Live-Verweise auf Datenspeichereinträge von anderen Repositorys nicht geprüft werden und dass aktive referenzierte Dateien gegebenenfalls fälschlicherweise entfernt werden. Deswegen müssen Systemadmins vor der Planung jedweder Datenspeicherbereinigungen auf jeden Fall über eine gemeinsame Nutzung des Datenspeichers Bescheid wissen. Sie dürfen nur dann den einfachen integrierten Prozess zur Datenspeicherbereinigung verwenden, wenn bekannt ist, dass der Datenspeicher nicht gemeinsam genutzt wird.

>[!NOTE]
>
>Wenn Sie die automatische Bereinigung für einen eingerichteten Cluster- oder freigegebenen Speicher (mit Mongo oder Segment-Tar) durchführen, werden im Protokoll möglicherweise Warnungen angezeigt, wonach bestimmte Blob-IDs nicht gelöscht werden können. Dies geschieht, weil während einer vorherigen automatischen Bereinigung gelöschte Blob-IDs fälschlicherweise erneut von anderen Cluster- oder Freigabeknoten referenziert werden, denen die Informationen zu den ID-Löschungen fehlen. Daher wird bei der automatischen Bereinigung eine Warnung protokolliert, wenn versucht wird, eine bereits im vorherigen Durchgang gelöschte ID zu entfernen. Dieses Verhalten wirkt sich weder auf die Leistung noch auf die Funktionalität aus.

## Ausführen der Datenspeicherbereinigung {#running-data-store-garbage-collection}

Die Datenspeicherbereinigung kann je nach dem Setup des Datenspeichers, mit dem AEM ausgeführt wird, auf drei Arten erfolgen:

1. Über die [Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md) – ein Bereinigungsmechanismus, der in der Regel für die Bereinigung des Knotenspeichers verwendet wird

1. Über die [Datenspeicherbereinigung](/help/sites-administering/data-store-garbage-collection.md#running-data-store-garbage-collection-via-the-operations-dashboard) – ein Bereinigungsmechanismus speziell für externe Datenspeicher, der im Vorgangs-Dashboard verfügbar ist.
1. Über die [JMX-Konsole](/help/sites-administering/jmx-console.md).

Wenn TarMK sowohl als Knotenspeicher als auch als Datenspeicher verwendet wird, kann die Revisionsbereinigung für die Bereinigung beider Speicher eingesetzt werden. Wenn jedoch ein externer Datenspeicher wie der Dateisystemdatenspeicher konfiguriert ist, muss die Datenspeicherbereinigung explizit und separat von der Revisionsbereinigung ausgelöst werden. Die Speicherbereinigung kann über das Vorgangs-Dashboard oder die JMX-Konsole ausgelöst werden.

Die folgende Tabelle zeigt den Datenspeicherbereinigungstyp, der für alle unterstützten Datenspeicherbereitstellungen in AEM 6 verwendet werden muss:

<table>
 <tbody>
  <tr>
   <td><strong>Knotenspeicher</strong><br /> </td>
   <td><strong>Datenspeicher</strong></td>
   <td><strong>Bereinigungsmechanismus</strong><br /> </td>
  </tr>
  <tr>
   <td>TarMK</td>
   <td>TarMK</td>
   <td>Revisionsbereinigung (Binärdateien sind mit dem Segmentspeicher abgestimmt)</td>
  </tr>
  <tr>
   <td>TarMK</td>
   <td>Externes Dateisystem</td>
   <td><p>Aufgabe zur automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard</p> <p>JMX-Konsole</p> </td>
  </tr>
  <tr>
   <td>MongoDB</td>
   <td>MongoDB</td>
   <td><p>Aufgabe zur automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard</p> <p>JMX-Konsole</p> </td>
  </tr>
  <tr>
   <td>MongoDB</td>
   <td>Externes Dateisystem</td>
   <td><p>Aufgabe zur automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard</p> <p>JMX-Konsole</p> </td>
  </tr>
 </tbody>
</table>

### Ausführen der automatischen Datenspeicherbereinigung über das Vorgangs-Dashboard {#running-data-store-garbage-collection-via-the-operations-dashboard}

Das integrierte, über das [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md) verfügbare wöchentliche Wartungsfenster beinhaltet die integrierte Aufgabe, die Datenspeicherbereinigung sonntags um 1 Uhr nachts durchzuführen.

Wenn Sie die Datenspeicherbereinigung zu einem anderen Zeitpunkt ausführen müssen, kann diese auch manuell über das Vorgangs-Dashboard ausgelöst werden.

Vor der Ausführung der Datenspeicherbereinigung sollten Sie sicherstellen, dass zu dem Zeitpunkt keine Sicherungen ausgeführt werden.

1. Öffnen Sie das Vorgangs-Dashboard durch **Navigation** > **Instrumente** > **Aktivitäten** > **Wartung**.
1. Klicken Sie auf **Wöchentliches Wartungsfenster**.

   ![chlimage_1-64](assets/chlimage_1-64.png)

1. Wählen Sie die **Datenspeicherbereinigung** und klicken Sie dann auf **Ausführen** Symbol.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Die automatische Datenspeicherbereinigung wird ausgeführt und der Status wird im Dashboard angezeigt.

   ![chlimage_1-66](assets/chlimage_1-66.png)

>[!NOTE]
>
>Die Aufgabe zur Durchführung der automatischen Datenspeicherbereinigung wird nur angezeigt, wenn Sie einen externen Dateidatenspeicher konfiguriert haben. Informationen zum Einrichten eines Dateidatenspeichers finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](/help/sites-deploying/data-store-config.md#file-data-store).

### Ausführen der Datenspeicherbereinigung über die JMX-Konsole {#running-data-store-garbage-collection-via-the-jmx-console}

In diesem Abschnitt wird das manuelle Ausführen der Datenspeicherbereinigung über die JMX-Konsole beschrieben. Wenn Ihre Installation ohne einen externen Datenspeicher eingerichtet ist, betrifft dies Ihre Installation nicht. Sehen Sie sich stattdessen die Anweisungen zum Ausführen der Revisionsbereinigung unter [Warten des Repositorys](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository) an.

>[!NOTE]
>
>Wenn Sie TarMK mit einem externen Datenspeicher ausführen, müssen Sie zunächst die Versionsbereinigung ausführen, damit die Speicherbereinigung effektiv sein kann.

So führen Sie die Speicherbereinigung durch:

1. Markieren Sie in der Apache Felix OSGi Management Console die Registerkarte **Main** und wählen Sie **JMX** aus dem folgenden Menü aus.
1. Suchen Sie dann nach dem MBean **Repository Manager** und klicken Sie darauf (oder gehen Sie zu `https://<host>:<port>/system/console/jmx/org.apache.jackrabbit.oak%3Aname%3Drepository+manager%2Ctype%3DRepositoryManagement`).
1. Klicken Sie auf **startDataStoreGC(boolean markOnly)**.
1. eintragen`true`&quot; für die `markOnly` Parameter, falls erforderlich:

   | **Option** | **Beschreibung** |
   |---|---|
   | boolesches markOnly | Setzen Sie diesen Wert auf true, um beim Markierungs- und Sweep-Vorgang nur Referenzen zu markieren und nicht zu sweepen. Dieser Modus wird verwendet, wenn der zugrunde liegende BlobStore für mehrere verschiedene Repositorys freigegeben ist. Verwenden Sie in allen anderen Fällen „false“, um eine vollständige Speicherbereinigung durchzuführen. |

1. Klicken Sie auf **Invoke**. CRX führt die Speicherbereinigung durch und zeigt an, wenn diese abgeschlossen ist.

>[!NOTE]
>
>Die automatische Datenspeicherbereinigung erfasst keine Dateien, die in den letzten 24 Stunden gelöscht wurden.

>[!NOTE]
>
>Die Aufgabe zur Durchführung der automatischen Datenspeicherbereinigung startet nur, wenn Sie einen externen Dateidatenspeicher konfiguriert haben. Wenn kein externer Dateidatenspeicher konfiguriert wurde, gibt die Aufgabe, nachdem sie aufgerufen wurde, die Meldung `Cannot perform operation: no service of type BlobGCMBean found` aus. Informationen zum Einrichten eines Dateidatenspeichers finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](/help/sites-deploying/data-store-config.md#file-data-store).

## Automatisieren der Datenspeicherbereinigung {#automating-data-store-garbage-collection}

Wenn möglich, sollte die automatische Datenspeicherbereinigung ausgeführt werden, wenn das System beispielsweise morgens wenig ausgelastet ist.

Das integrierte, über das [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md) verfügbare wöchentliche Wartungsfenster beinhaltet die integrierte Aufgabe, die Datenspeicherbereinigung sonntags um 1 Uhr morgens durchzuführen. Sie sollten auch sicherstellen, dass zu dem Zeitpunkt keine Sicherungen ausgeführt werden. Der Start des Wartungsfensters kann bei Bedarf über das Dashboard angepasst werden.

>[!NOTE]
>
>Es sollte nicht beides gleichzeitig ausgeführt werden, damit alte (und nicht verwendete) Datenspeicherdateien ebenfalls gesichert werden. Auf diese Weise sind die Binärdateien nach wie vor in der Sicherung vorhanden, wenn das Zurücksetzen auf eine alte Revision erforderlich sein sollte.

Wenn Sie die automatische Datenspeicherbereinigung nicht mit dem wöchentlichen Wartungsfenster im Vorgangs-Dashboard ausführen möchten, kann sie auch mit den HTTP-Clients wget oder curl automatisiert werden. Es folgt ein Beispiel für eine Automatisierung der Sicherung mithilfe von curl:

>[!CAUTION]
>
>Im folgenden Beispiel müssen gegebenenfalls verschiedene Parameter des `curl`-Befehls für Ihre Instanz konfiguriert werden, so zum Beispiel Hostname (`localhost`), Port (`4502`), Admin-Kennwort (`xyz`) und verschiedene Parameter für die tatsächliche automatische Datenspeicherbereinigung.

Dies ist ein Beispiel für einen curl-Befehl zum Aufrufen der automatischen Datenspeicherbereinigung über die Befehlszeile:

```shell
curl -u admin:admin -X POST --data markOnly=true  https://localhost:4503/system/console/jmx/org.apache.jackrabbit.oak"%"3Aname"%"3Drepository+manager"%"2Ctype"%"3DRepositoryManagement/op/startDataStoreGC/boolean
```

Der curl-Befehl wird sofort zurückgegeben.

## Überprüfen der Datenspeicherkonsistenz {#checking-data-store-consistency}

Die Konsistenzprüfung für den Datenspeicher meldet alle Binärdateien des Datenspeichers, die fehlen, aber noch referenziert werden. Gehen Sie wie folgt vor, um eine Konsistenzprüfung zu starten:

1. Gehen Sie zur JMX-Konsole. Informationen zur Verwendung der JMX-Konsole finden Sie in [diesem Artikel](/help/sites-administering/jmx-console.md#using-the-jmx-console).
1. Suchen Sie nach dem MBean **BlobGarbageCollection** und klicken Sie darauf.
1. Klicken Sie auf den Link `checkConsistency()`.

Nach dem Abschluss der Konsistenzprüfung wird eine Meldung mit der Zahl der als fehlend gemeldeten Binärdateien angezeigt. Ist die Zahl größer als 0, prüfen Sie das `error.log`, um weitere Details zu fehlenden Binärdateien anzuzeigen.

Im Folgenden finden Sie ein Beispiel dafür, wie die fehlenden Binärdateien in den Protokollen gemeldet werden:

```xml
11:32:39.673 INFO [main] MarkSweepGarbageCollector.java:600 Consistency check found [1] missing blobs
```

```xml
11:32:39.673 WARN [main] MarkSweepGarbageCollector.java:602 Consistency check failure intheblob store : DataStore backed BlobStore [org.apache.jackrabbit.oak.plugins.blob.datastore.OakFileDataStore], check missing candidates in file /tmp/gcworkdir-1467352959243/gccand-1467352959243
```
