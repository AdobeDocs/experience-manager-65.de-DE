---
title: Fehlerbehebung in Adobe Experience Manager
description: Erfahren Sie mehr über die Fehlerbehebung bei AEM.
uuid: 72379531-915c-45d0-ba70-42b212665272
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6346cd93-1ca3-4510-9c31-a74c41017ddb
docset: aem65
exl-id: d2d351e7-87a5-4895-b4ec-391fb0b66798
source-git-commit: a2fd3c0c1892ac648c87ca0dec440e22144c37a2
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 33%

---

# Fehlerbehebung in Adobe Experience Manager {#troubleshooting-aem}

Im folgenden Abschnitt werden einige Probleme behandelt, auf die Sie bei der Verwendung von AEM (Adobe Experience Manager) stoßen können, sowie Empfehlungen zur Fehlerbehebung.

>[!NOTE]
>
>Wenn Sie Probleme beim Authoring in AEM beheben, finden Sie weitere Informationen unter [Fehlerbehebung für Autoren.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Bei Problemen ist es auch sinnvoll, die Liste der [Bekannte Probleme](/help/release-notes/release-notes.md) für Ihre Instanz (Release- und Service Packs).

## Fehlerbehebungsszenarien für Administratoren {#troubleshooting-scenarios-for-administrators}

Die folgende Tabelle bietet einen Überblick über Probleme, die Administratoren beheben können:

<table>
 <tbody>
  <tr>
   <td><strong>Rolle</strong></td>
   <td><strong>Problem </strong></td>
  </tr>
  <tr>
   <td>Systemadmin</td>
   <td><p>Ein Doppelklick auf die Schnellstart-JAR hat keine Auswirkungen oder öffnet die JAR-Datei mit einem anderen Programm (z. B. Archiv-Manager).</p> </td>
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

* Ein Doppelklick auf die Schnellstart-JAR-Datei hat keine Auswirkungen oder die JAR-Datei mit einem anderen Programm (z. B. Archivmanager).
* Bei Anwendungen, die auf CRX ausgeführt werden, treten Fehler wegen zu wenig Arbeitsspeicher auf.
* Der AEM Begrüßungsbildschirm wird nach einem Doppelklick auf AEM Schnellstart nicht im Browser angezeigt.

## Methoden zur Fehlerbehebung in der Analyse {#methods-for-troubleshooting-analysis}

### Erstellen von Thread-Speicherauszügen {#making-a-thread-dump}

Die Thread-Sicherheitskopie ist eine Liste aller derzeit aktiven Java™-Threads. Wenn AEM nicht richtig reagiert, kann der Thread-Speicherauszug helfen, Deadlocks oder andere Probleme zu identifizieren.

### Verwenden der Sling-Thread-Dumper {#using-sling-thread-dumper}

1. Öffnen Sie die **AEM Web-Konsole**; z. B. bei `https://localhost:4502/system/console/`.
1. Wählen Sie auf der Registerkarte **Status** die Option **Threads** aus.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### Verwenden von jstack (Befehlszeile) {#using-jstack-command-line}

1. Suchen Sie die PID (Prozess-ID) der AEM Java™-Instanz.

   Sie können beispielsweise `ps -ef` oder `jps` verwenden.

1. Ausführen:

   `jstack <pid>`

1. Zeigt die Thread-Sicherheitskopie an.

>[!NOTE]
>
>Sie können die Thread-Speicherauszüge an eine Protokolldatei anhängen, indem Sie die `>>`-Ausgabeumleitung verwenden:
>
>`jstack <pid> >> /path/to/logfile.log`

Weitere Informationen dazu finden Sie in der Dokumentation [Erstellen von Thread-Speicherauszügen von einem JVM](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17452.html?lang=en).

### Überprüfen auf nicht beendete JCR-Sitzungen {#checking-for-unclosed-jcr-sessions}

Wenn Funktionen für AEM WCM entwickelt werden, können JCR-Sitzungen geöffnet werden (vergleichbar mit dem Öffnen einer Datenbankverbindung). Wenn die geöffneten Sitzungen nie geschlossen werden, kann Ihr System folgende Symptome aufweisen:

* Das System wird langsamer.
* Sie können einen Großteil von CacheManager sehen: resizeAll -Einträge in der Protokolldatei; die folgende Zahl (size=&lt;x>) zeigt die Anzahl der Caches an, jede Sitzung öffnet mehrere Caches.
* Gelegentlich reicht der Speicherplatz des Systems nicht aus (nach einigen Stunden, Tagen oder Wochen – je nach Schweregrad).

Informationen zum Analysieren nicht geschlossener Sitzungen und zum Ermitteln, welcher Code eine Sitzung nicht schließt, finden Sie im Knowledge Base-Artikel . [Nicht geschlossene Sitzungen analysieren](https://helpx.adobe.com/de/experience-manager/kb/AnalyzeUnclosedSessions.html).

### Verwenden der Adobe Experience Manager-Web-Konsole {#using-the-adobe-experience-manager-web-console}

Der Status der OSGi-Pakete kann auch frühzeitig auf mögliche Probleme hinweisen.

1. Öffnen Sie die **AEM Web-Konsole**; z. B. bei `https://localhost:4502/system/console/`.
1. Wählen auf der Registerkarte **OSGi** die Option **Pakete** aus.
1. Überprüfen Sie Folgendes:

   * den Status der Pakete. Wenn ein Paket inaktiv oder nicht zufrieden ist, versuchen Sie, das Bundle zu stoppen und neu zu starten. Wenn das Problem weiterhin besteht, untersuchen Sie es mit anderen Methoden weiter.
   * ob Pakete mit fehlenden Abhängigkeiten vorliegen. Solche Details können durch Klicken auf den einzelnen Bundle-Namen angezeigt werden, bei dem es sich um einen Link handelt (im folgenden Beispiel gibt es keine Probleme):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
