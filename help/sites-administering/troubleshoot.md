---
title: Beheben von Fehlern in AEM
seo-title: Troubleshooting AEM
description: Erfahren Sie mehr über das Beheben von Fehlern in AEM.
seo-description: Learn about troubleshooting issues with AEM.
uuid: 72379531-915c-45d0-ba70-42b212665272
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6346cd93-1ca3-4510-9c31-a74c41017ddb
docset: aem65
exl-id: d2d351e7-87a5-4895-b4ec-391fb0b66798
source-git-commit: d1b4cf87291f7e4a0670a21feca1ebf8dd5e0b5e
workflow-type: ht
source-wordcount: '547'
ht-degree: 100%

---

# Beheben von Fehlern in AEM {#troubleshooting-aem}

Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.

>[!NOTE]
>
>Wenn Sie Probleme mit der Bearbeitung in AEM beheben wollen, lesen Sie den Abschnitt [Fehlerbehebung für Autoren](/help/sites-authoring/troubleshooting.md).

>[!NOTE]
>
>Wenn Probleme auftreten, sollten Sie auch die Liste der [bekannten Probleme](/help/release-notes/release-notes.md) für Ihre Instanz (Version und Service Packs) prüfen.

## Fehlerbehebungsszenarien für Administratoren {#troubleshooting-scenarios-for-administrators}

Die folgende Tabelle bietet einen Überblick über Probleme, die Administratoren möglicherweise beheben müssen:

<table>
 <tbody>
  <tr>
   <td><strong>Rolle(en)</strong></td>
   <td><strong>Problem </strong></td>
  </tr>
  <tr>
   <td>Systemadmin</td>
   <td><p>Beim Doppelklicken auf die JAR-Datei für den Schnellstart passiert entweder gar nichts oder die Datei wird mit einem anderen Programm (z. B. der Archivverwaltung) geöffnet</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> </td>
   <td><p>Über CRX ausgeführte Anwendung erzeugt Fehler wegen unzureichendem Arbeitsspeicher</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> </td>
   <td><p>Der AEM-Willkommensbildschirm wird nach einem Doppelklick auf den AEM-CM-Schnellstart nicht im Browser angezeigt</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> <p>Admin-Benutzer</p> </td>
   <td><p>Erstellen von Thread-Speicherauszügen</p> </td>
  </tr>
  <tr>
   <td><p>Systemadmin</p> <p>Admin-Benutzer</p> </td>
   <td><p>Überprüfung auf nicht beendete JCR-Sitzungen</p> </td>
  </tr>
 </tbody>
</table>

## Installationsprobleme {#installation-issues}

Weitere Informationen zu den folgenden Fehlerbehebungsszenarien finden Sie in [Allgemeine Installationsprobleme](/help/sites-deploying/troubleshooting.md#common-installation-issues):

* Das Doppelklicken auf die Schnellstart-JAR-Datei hat keinen Effekt oder die Datei wird mit einem anderen Programm geöffnet (z. B. Archivmanager).
* In CRX ausgeführte Anwendungen führen zu Fehlern aufgrund unzureichendem Speicherplatz.
* Der AEM-Willkommensbildschirm wird nach einem Doppelklick auf den AEM-Schnellstart nicht im Browser angezeigt.

## Methoden für die Fehlerbehebungsanalyse {#methods-for-troubleshooting-analysis}

### Erstellen von Thread-Speicherauszügen {#making-a-thread-dump}

Ein Thread-Speicherauszug ist eine Liste aller Java-Threads, die derzeit aktiv sind. Wenn AEM nicht richtig reagiert, kann der Thread-Speicherauszug helfen, Deadlocks oder andere Probleme zu identifizieren.

### Verwenden des Sling Thread Dumper {#using-sling-thread-dumper}

1. Öffnen Sie die **AEM-Web-Konsole**; zum Beispiel unter `https://localhost:4502/system/console/`.
1. Wählen Sie auf der Registerkarte **Status** die Option **Threads** aus.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Verwenden von jstack (Befehlszeile) {#using-jstack-command-line}

1. Suchen Sie die PID (Prozess-ID) der AEM-Java-Instanz.

   Sie können beispielsweise `ps -ef` oder `jps` verwenden.

1. Ausführen:

   `jstack <pid>`

1. Daraufhin wird der Thread-Speicherauszug angezeigt.

>[!NOTE]
>
>Sie können die Thread-Speicherauszüge an eine Protokolldatei anhängen, indem Sie die `>>`-Ausgabeumleitung verwenden:
>
>`jstack <pid> >> /path/to/logfile.log`

Weitere Informationen dazu finden Sie in der Dokumentation [Erstellen von Thread-Speicherauszügen von einem JVM](https://helpx.adobe.com/de/cq/kb/TakeThreadDump.html).

### Überprüfen auf nicht beendete JCR-Sitzungen {#checking-for-unclosed-jcr-sessions}

Wenn Funktionen für AEM WCM entwickelt werden, werden möglicherweise JCR-Sitzungen geöffnet (vergleichbar mit dem Öffnen einer Datenbankverbindung). Werden die geöffneten Sitzungen nie geschlossen, können folgende Probleme in Ihrem System auftreten:

* Das System wird langsamer.
* Es befinden sich viele „CacheManager: resizeAll“-Einträge in der Protokolldatei. Die folgende Zahl (size=&lt;x>) gibt die Anzahl an Caches an; jede Sitzung öffnet mehrere Caches.
* Gelegentlich reicht der Speicherplatz des Systems nicht aus (nach einigen Stunden, Tagen oder Wochen – je nach Schweregrad).

Lesen Sie den Knowledgebase-Artikel [Analysieren von nicht beendeten Sitzungen](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html), um nicht beendete Sitzungen zu analysieren und festzustellen, welcher Code dazu führt, dass eine Sitzung nicht beendet wird.

### Verwenden der Adobe Experience Manager-Web-Konsole {#using-the-adobe-experience-manager-web-console}

Der Status der OSGi-Pakete kann auch frühzeitig auf mögliche Probleme hinweisen.

1. Öffnen Sie die **AEM-Web-Konsole**; zum Beispiel unter `https://localhost:4502/system/console/`.
1. Wählen auf der Registerkarte **OSGi** die Option **Pakete** aus.
1. Überprüfen Sie Folgendes:

   * den Status der Pakete. Falls Status wie „Inaktiv“ oder „Nicht erfüllt“ angezeigt werden, versuchen Sie, das Paket zu stoppen und neu zu starten. Wenn das Problem weiterhin besteht, müssen Sie dies mithilfe anderer Methoden weiter untersuchen.
   * ob Pakete mit fehlenden Abhängigkeiten vorliegen. Dies können Sie herausfinden, indem Sie auf den einzelnen Paket-Namen klicken, bei dem es sich um einen Link handelt (im folgenden Beispiel sind keine Probleme aufgetreten):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
