---
title: Fehlerbehebung bei Adobe Experience Manager
description: Erfahren Sie mehr über die Fehlerbehebung bei einigen Problemen, die möglicherweise mit Adobe Experience Manager auftreten.
uuid: 72379531-915c-45d0-ba70-42b212665272
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6346cd93-1ca3-4510-9c31-a74c41017ddb
docset: aem65
exl-id: d2d351e7-87a5-4895-b4ec-391fb0b66798
source-git-commit: 3400df1ecd545aa0fb0e3fcdcc24f629ce4c99ba
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 97%

---

# Fehlerbehebung bei Adobe Experience Manager {#troubleshooting-aem}

Der folgende Abschnitt behandelt einige Probleme, die bei der Verwendung von AEM (Adobe Experience Manager) auftreten können, sowie Vorschläge zur Fehlerbehebung.

>[!NOTE]
>
>Wenn Sie Probleme beim Erstellen von Inhalten in AEM beheben möchten, lesen Sie den Abschnitt [Fehlerbehebung für Autoren und Autorinnen](/help/sites-authoring/troubleshooting.md).

>[!NOTE]
>
>Bei Problemen ist es auch sinnvoll, die Liste der [Bekannten Probleme](/help/release-notes/release-notes.md) für Ihre Instanz (Version und Service Packs) zu prüfen.

## Fehlerbehebungsszenarien für Admins {#troubleshooting-scenarios-for-administrators}

Die folgende Tabelle bietet einen Überblick über Probleme, die Admins beheben können:

<table>
 <tbody>
  <tr>
   <td><strong>Rolle</strong></td>
   <td><strong>Problem </strong></td>
  </tr>
  <tr>
   <td>Systemadmin</td>
   <td><p>Ein Doppelklick auf die JAR-Datei für den Schnellstart zeigt keine Wirkung oder öffnet die JAR-Datei mit einem anderen Programm (z. B. dem Archiv-Manager)</p> </td>
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

Siehe [Häufige Installationsprobleme](/help/sites-deploying/troubleshooting.md#common-installation-issues) für Informationen zu den folgenden Fehlerbehebungsszenarien:

* Ein Doppelklick auf die JAR-Datei für den Schnellstart zeigt keine Wirkung oder öffnet die JAR-Datei mit einem anderen Programm (z. B. Archiv-Manager).
* Bei Applikationen, die auf CRX ausgeführt werden, treten Fehler wegen unzureichendem Speicherplatz auf.
* Der AEM-Begrüßungsbildschirm wird nach einem Doppelklick auf den AEM-Schnellstart nicht im Browser angezeigt.

## Methoden zur Fehlerbehebung in der Analyse {#methods-for-troubleshooting-analysis}

### Erstellen von Thread-Speicherauszügen {#making-a-thread-dump}

Ein Thread-Speicherauszug ist eine Liste aller Java™-Threads, die derzeit aktiv sind. Wenn AEM nicht richtig reagiert, kann der Thread-Speicherauszug helfen, Deadlocks oder andere Probleme zu identifizieren.

### Verwendung vom Sling-Thread-Speicherauszug {#using-sling-thread-dumper}

1. Öffnen Sie die **AEM-Web-Konsole**, zum Beispiel unter `https://localhost:4502/system/console/`.
1. Wählen Sie auf der Registerkarte **Status** die Option **Threads** aus.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Verwenden von jstack (Befehlszeile) {#using-jstack-command-line}

1. Suchen Sie die PID (Prozess-ID) der AEM-Java™-Instanz.

   Sie können beispielsweise `ps -ef` oder `jps` verwenden.

1. Ausführen:

   `jstack <pid>`

1. Zeigt den Thread-Speicherauszug an.

>[!NOTE]
>
>Sie können die Thread-Speicherauszüge an eine Protokolldatei anhängen, indem Sie die `>>`-Ausgabeumleitung verwenden:
>
>`jstack <pid> >> /path/to/logfile.log`

Weitere Informationen dazu finden Sie in der Dokumentation [Erstellen von Thread-Speicherauszügen von einem JVM](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17452.html?lang=de).

### Überprüfen auf nicht beendete JCR-Sitzungen {#checking-for-unclosed-jcr-sessions}

Wenn Funktionen für AEM WCM entwickelt werden, können JCR-Sitzungen geöffnet werden (vergleichbar mit dem Öffnen einer Datenbankverbindung). Wenn die geöffneten Sitzungen nie geschlossen werden, kann Ihr System folgende Symptome aufweisen:

* Das System wird langsamer.
* Es befinden sich viele „CacheManager: resizeAll“-Einträge in der Protokolldatei. Die folgende Zahl (size=&lt;x>) gibt die Anzahl an Caches an; jede Sitzung öffnet mehrere Caches.
* Gelegentlich reicht der Speicherplatz des Systems nicht aus (nach einigen Stunden, Tagen oder Wochen – je nach Schweregrad).

Informationen zum Analysieren nicht geschlossener Sitzungen und zum Ermitteln, welcher Code eine Sitzung nicht schließt, finden Sie im Knowledgebase-Artikel [Nicht geschlossene Sitzungen analysieren](https://helpx.adobe.com/de/experience-manager/kb/AnalyzeUnclosedSessions.html).

### Verwenden der Adobe Experience Manager-Web-Konsole {#using-the-adobe-experience-manager-web-console}

Der Status der OSGi-Pakete kann auch frühzeitig auf mögliche Probleme hinweisen.

1. Öffnen Sie die **AEM-Web-Konsole**, zum Beispiel unter `https://localhost:4502/system/console/`.
1. Wählen auf der Registerkarte **OSGi** die Option **Pakete** aus.
1. Überprüfen Sie Folgendes:

   * den Status der Pakete. Falls Status wie „Inaktiv“ oder „Nicht erfüllt“ angezeigt werden, versuchen Sie, das Paket zu stoppen und neu zu starten. Wenn das Problem weiterhin besteht, untersuchen Sie es mit anderen Methoden weiter.
   * ob Pakete mit fehlenden Abhängigkeiten vorliegen. Dies können Sie herausfinden, indem Sie auf den einzelnen Paketnamen klicken, bei dem es sich um einen Link handelt (im folgenden Beispiel sind keine Probleme aufgetreten):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
