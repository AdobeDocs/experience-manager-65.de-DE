---
title: Revisionsbereinigung
seo-title: Revisionsbereinigung
description: Erfahren Sie, wie Sie die Revisionsbereinigungsfunktion in AEM 6.3 verwenden.
seo-description: Erfahren Sie, wie Sie die Revisionsbereinigungsfunktion in AEM 6.3 verwenden.
uuid: 321f5038-44b0-4f1e-a1aa-2d29074eed70
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: f03ebe60-88c0-4fc0-969f-949490a8e768
feature: Konfiguration
exl-id: e53c4c81-f62e-4b6d-929a-6649c8ced23c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '5917'
ht-degree: 66%

---

# Revisionsbereinigung{#revision-cleanup}

## Einführung {#introduction}

Bei jeder Repository-Aktualisierung wird eine neue Inhaltsrevision erstellt. Dadurch wächst bei jeder Aktualisierung die Größe des Repositorys. Um ein unkontrolliertes Repository-Wachstum zu vermeiden, müssen alte Revisionen bereinigt werden, um Festplattenressourcen freizugeben. Diese Wartungsfunktionalität wird als Revisionsbereinigung bezeichnet. und ist ab AEM 6.0 als Offlineprogramm verfügbar.

Mit AEM 6.3 wurde eine Onlineversion dieser Funktionalität namens Online-Revisionsbereinigung eingeführt. Verglichen mit der Offline-Revisionsbereinigung, bei der die AEM-Instanz beendet werden muss, kann die Online-Revisionsbereinigung ausgeführt werden, wenn die AEM-Instanz online ist. Die Online-Revisionsbereinigung ist standardmäßig aktiviert und wird als Methode für die Revisionsbereinigung empfohlen.

**Hinweis**:  [Eine Einführung und die Verwendung der Online-Revisionsbereinigung finden Sie im ](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/revision-cleanup-technical-video-use.html) Video .

Die Revisionsbereinigung ist in drei Phasen unterteilt: **Schätzung**, **Komprimierung** und **Bereinigung**. Bei der Schätzung wird basierend auf der Menge an erfassten veralteten Daten entschieden, ob die nächste Phase (Komprimierung) ausgeführt wird. In der Komprimierungsphase werden Segmente und TAR-Dateien neu geschrieben; nicht verwendete Inhalte werden daraus entfernt. In der Bereinigungsphase werden die alten Segmente und alle darin enthaltenen veralteten Daten gelöscht. Im Offline-Modus kann in der Regel mehr Speicherplatz zurückgewonnen werden, da im Online-Modus der Arbeitsdatensatz von AEM berücksichtigt werden muss, für den zusätzliche Segmente beibehalten (d. h. nicht bereinigt) werden.

Weitere Informationen zur Revisionsbereinigung finden Sie unter folgenden Links:

* [Ausführen der Online-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup)
* [Häufig gestellte Fragen zur Online-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions)
* [Ausführen der Offline-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#how-to-run-offline-revision-cleanup)

Darüber hinaus können Sie auch die [offizielle Oak-Dokumentation lesen.](https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html)

### Wann sollte die Online-Revisionsbereinigung anstelle der Offline-Revisionsbereinigung verwendet werden? {#when-to-use-online-revision-cleanup-as-opposed-to-offline-revision-cleanup}

**Die Online-Revisionsbereinigung ist die empfohlene Methode zur Durchführung einer Revisionsbereinigung.** Die Offline-Revisionsbereinigung sollte nur in Ausnahmefällen erfolgen, beispielsweise bei der Migration zu einem neuen Speicherformat oder auf Anforderung der Adobe-Kundenunterstützung.

## Ausführen der Online-Revisionsbereinigung {#how-to-run-online-revision-cleanup}

Die Online-Revisionsbereinigung ist standardmäßig so konfiguriert, dass sie einmal pro Tag automatisch auf der Autoren- und Veröffentlichungsinstanz von AEM ausgeführt wird. Sie müssen nur ein Wartungsfenster für einen Zeitraum festlegen, in dem die Benutzeraktivität am wenigsten beeinträchtigt wird. Sie können die Online-Revisionsbereinigung wie folgt konfigurieren:

1. Wechseln Sie im AEM Hauptfenster zu **Tools - Vorgänge - Dashboard - Wartung** oder verweisen Sie Ihren Browser auf: `https://serveraddress:serverport/libs/granite/operations/content/maintenance.html`

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Bewegen Sie den Mauszeiger über **Tägliches Wartungsfenster** und klicken Sie auf das Symbol **Einstellungen**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Geben Sie die gewünschten Werte ein (Wiederholung, Startzeit, Endzeit) und klicken Sie auf **Speichern**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

Wenn Sie die Revisionsbereinigung manuell durchführen möchten, gehen Sie wie folgt vor:

1. Gehen Sie zu **Tools - Vorgänge - Dashboard - Wartung** oder navigieren Sie direkt zu `https://serveraddress:serverport/libs/granite/operations/content/maintenance.html`
1. Klicken Sie auf **Tägliches Wartungsfenster**.
1. Bewegen Sie den Mauszeiger über das Symbol **Revisionsbereinigung**.
1. Klicken Sie auf **Ausführen**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### Ausführen der Online-Revisionsbereinigung nach der Offline-Revisionsbereinigung {#running-online-revision-cleanup-after-offline-revision-cleanup}

Der Revisionsbereinigungsprozess gewinnt alte Revisionen generationsweise zurück. Dies bedeutet, dass bei jeder Ausführung der Revisionsbereinigung eine neue Generation erstellt und auf der Festplatte gespeichert wird. Es gibt jedoch einen Unterschied zwischen den beiden Arten der Revisionsbereinigung: Die Offline-Revisionsbereinigung behält eine Generation bei, während die Online-Revisionsbereinigung zwei Generationen aufbewahrt. Wenn Sie also die Online-Revisionsbereinigung **nach** Offline-Revisionsbereinigung ausführen, geschieht Folgendes:

1. Nach der ersten Online-Revisionsbereinigung verdoppelt sich die Größe des Repositorys. Dies geschieht, weil jetzt zwei Generationen auf der Festplatte aufbewahrt werden.
1. Während der nachfolgenden Ausführungen wächst das Repository vorübergehend, während die neue Generation erstellt wird, und stabilisiert sich dann wieder auf die Größe, die es nach der ersten Ausführung hatte, da der Online-Revisionsbereinigungsprozess die vorherige Generation zurückgewinnt.

Beachten Sie auch, dass abhängig vom Typ und der Anzahl der Commits jede Generierung eine andere Größe als die vorherige haben kann, weshalb die endgültige Größe von einem Durchlauf zum nächsten abweichen kann.

Deswegen empfiehlt es sich, eine Festplatte zu wählen, die mindestens zwei- oder dreimal so groß ist wie die ursprünglich geschätzte Repository-Größe.

## Vollständiger und Tail-Komprimierungsmodus   {#full-and-tail-compaction-modes}

**AEM 6.5** führt  **zwei neue** Modi für die  **** Komprimierungsphase des Online-Revisionsbereinigungsprozesses ein:

* Der Modus **vollständige Komprimierung** schreibt alle Segmente und TAR-Dateien im gesamten Repository neu. Die nachfolgende Bereinigungsphase kann so eine maximale Bereinigung des Repositorys durchführen. Da die vollständige Komprimierung das gesamte Repository betrifft, benötigt sie in erheblichem Umfang Systemressourcen und Zeit. Die vollständige Komprimierung entspricht der Komprimierungsphase in AEM 6.3.
* Der Modus **Tail Compaction** schreibt nur die neuesten Segmente und TAR-Dateien im Repository neu. Die aktuellsten Segmente und TAR-Dateien sind diejenigen, die seit der letzten vollständigen oder Tail-Komprimierung hinzugefügt wurden. Die nachfolgende Bereinigungsphase kann daher nur den aktuellen Teil des Repositorys bereinigen. Da die Tail-Komprimierung nur einen Teil des Repositorys betrifft, benötigt sie erheblich weniger Systemressourcen und Zeit als eine vollständige Komprimierung.

Diese Komprimierungsmodi stellen einen Kompromiss zwischen Effizienz und Ressourcenverbrauch dar: während die Tail-Komprimierung weniger effektiv ist, wirkt sie sich auch weniger auf den normalen Systembetrieb aus. Im Gegensatz dazu ist die vollständige Komprimierung effektiver, wirkt sich aber stärker auf den normalen Systembetrieb aus.

AEM 6.5 bietet bei der Komprimierung außerdem einen effizienteren Mechanismus für die Deduplizierung des Inhalts, was den Speicherbedarf des Repositorys weiter verringert.

Die beiden folgenden Diagramme enthalten die Ergebnisse aus internen Laborversuchen, die die Reduzierung der durchschnittlichen Ausführungszeiten und des durchschnittlichen Festplattenspeicherbedarfs in AEM 6.5 im Vergleich zu AEM 6.3 aufzeigen:

![onrc-duration-6_4vs63](assets/onrc-duration-6_4vs63.png) ![segmentstore-6_4vs63](assets/segmentstore-6_4vs63.png)

### Anleitung zum Konfigurieren der vollständigen und der Tail-Komprimierung {#how-to-configure-full-and-tail-compaction}

In der Standardkonfiguration wird die Tail-Komprimierung an Wochentagen und die vollständige Komprimierung an Sonntagen ausgeführt. Die Standardkonfiguration kann mithilfe des neuen Konfigurationswerts `full.gc.days` von `RevisionCleanupTask` [Wartungsaufgabe](/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup) geändert werden.

Wenn Sie den Wert `full.gc.days` konfigurieren, beachten Sie, dass die vollständige Komprimierung während der in dem Wert definierten Tage ausgeführt wird und die Tail-Komprimierung während der Tage ausgeführt wird, die im Wert nicht definiert sind. Wenn Sie beispielsweise die Ausführung einer vollständigen Komprimierung am Sonntag konfigurieren, wird die Tail-Komprimierung von Montag bis Samstag ausgeführt. Wenn Sie hingegen die Ausführung einer vollständigen Komprimierung an allen Tagen der Woche konfigurieren, wird die Tail-Komprimierung gar nicht ausgeführt.

Berücksichtigen Sie auch Folgendes:

* **Die Tail-** Verdichtung ist weniger effektiv und hat weniger Auswirkungen auf den normalen Systembetrieb. Sie sollte daher an den Werktagen ausgeführt werden.
* **Vollständige** Verdichtung ist effektiver, hat aber auch größere Auswirkungen auf den normalen Systembetrieb. Sie sollte daher außerhalb der Arbeitstage verwendet werden.
* Beide Komprimierungen sollten so konfiguriert sein, dass sie außerhalb der Spitzenzeiten ausgeführt werden.

### Fehlerbehebung {#troubleshooting}

Wenn Sie die neuen Komprimierungsmodi verwenden, beachten Sie Folgendes:

* Sie können die Ein-/Ausgabeaktivität überwachen, z. B.: E/A-Vorgänge, Wartezeiten der CPU auf E/A-Vorgänge, Größe der Commit-Warteschlange. Dies hilft Ihnen bei der Entscheidung, ob das System die E/A-Grenze erreicht hat und Upsizing erforderlich ist.
* `RevisionCleanupTaskHealthCheck` gibt den allgemeinen Gesundheitsstatus der Online-Revisionsbereinigung an. Er funktioniert wie in AEM 6.3 und unterscheidet nicht zwischen der vollständigen und der Tail-Komprimierung.
* Die Protokollmeldungen enthalten relevante Information über die Komprimierungsmodi. Wenn beispielsweise die Online-Revisionsbereinigung gestartet wird, geben die Protokollmeldungen den verwendeten Komprimierungsmodus an. Außerdem kann es in einigen Grenzfällen passieren, dass das System zur vollständigen Komprimierung wechselt, obwohl eine Tail-Komprimierung geplant ist. Diese Änderung ist in den Protokollmeldungen ersichtlich. Die folgenden Protokollbeispiele zeigen den Komprimierungsmodus und den Wechsel von der vollständigen Komprimierung zur Tail-Komprimierung:

```
TarMK GC: running tail compaction
TarMK GC: no base state available, running full compaction instead
```

### Bekannte Einschränkungen  {#known-limitations}

In einigen Fällen verzögert der Wechsel zwischen dem Tail- und dem vollständigen Komprimierungsmodus den Bereinigungsprozess. Genauer gesagt steigt die Größe des Repositorys nach einer vollständigen Komprimierung an (sie verdoppelt sich). Der zusätzliche Speicherplatz wird bei der nachfolgenden Tail-Komprimierung zurückgewonnen, bei der das Repository unter den Wert vor der vollständigen Komprimierung fällt. Auch die parallele Ausführung von Wartungsaufgaben sollte vermieden werden.

**Es empfiehlt sich, eine Festplatte zu wählen, die mindestens zwei- oder dreimal so groß ist wie die ursprünglich geschätzte Repository-Größe.**

## Häufig gestellte Fragen zur Online-Revisionsbereinigung  {#online-revision-cleanup-frequently-asked-questions}

### Aspekte der AEM 6.5-Aktualisierung {#aem-upgrade-considerations}

<table>
 <tbody>
  <tr>
   <td>Fragen </td>
   <td>Antworten</td>
  </tr>
  <tr>
   <td>Was muss ich beachten, wenn ich auf AEM 6.5 aktualisiere?</td>
   <td><p>Das Persistenzformat von TarMK ändert sich mit AEM 6.5. Für diese Änderungen ist keine proaktive Migration erforderlich. Vorhandene Repositorys durchlaufen eine parallele Migration, die für den Benutzer transparent ist. Der Migrationsprozess wird initiiert, wenn AEM 6.5 (oder zugehörige Tools) zum ersten Mal auf das Repository zugreifen.</p> <p><strong>Nachdem die Migration zum Persistenzformat AEM 6.5 initiiert wurde, kann das Repository nicht mehr in das Persistenzformat AEM 6.3 zurückgesetzt werden.</strong></p> </td>
  </tr>
 </tbody>
</table>

### Migrieren zum Oak-Segment-TAR {#migrating-to-oak-segment-tar}

<table>
 <tbody>
  <tr>
   <td><strong>Fragen</strong></td>
   <td><strong>Antworten</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Warum muss ich das Repository migrieren? </strong></td>
   <td><p>In AEM 6.3 waren Änderungen am Speicherformat erforderlich, insbesondere zur Verbesserung der Leistung und Wirksamkeit der Online-Revisionsbereinigung. Diese Änderungen sind nicht rückwärtskompatibel, daher müssen mit dem alten Oak-Segment (AEM 6.2 und früher) erstellte Repositorys migriert werden.</p> <p>Weitere Vorteile der Änderung des Speicherformats:</p>
    <ul>
     <li>Bessere Skalierbarkeit (optimierte Segmentgröße).</li>
     <li>Schnellere <a href="/help/sites-administering/data-store-garbage-collection.md" target="_blank">Bereinigung des Datenspeichers</a>.<br /> </li>
     <li>Grundlage für zukünftige Verbesserungen.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wird das vorherige TAR-Format weiterhin unterstützt? </strong></td>
   <td>AEM 6.3 unterstützt nur das neue Oak-Segment-Tar.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Ist die Migration des Inhalts immer obligatorisch? </strong></td>
   <td>Ja. Sie müssen Inhalt immer migrieren, es sei denn, Sie starten mit einer neuen Instanz.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kann ich auf 6.3 aktualisieren und die Migration später durchführen (um z. B. ein anderes Wartungsfenster zu nutzen)? </strong></td>
   <td>Nein, wie oben beschrieben, ist die Migration obligatorisch.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kann die Ausfallzeit für die Migration vermieden werden? </strong></td>
   <td>Nein. Es handelt sich um eine einmalige Aufgabe, die nicht auf einer laufenden Instanz ausgeführt werden kann.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Was passiert, wenn ich versehentlich das falsche Repository-Format verwende? </strong></td>
   <td>Wenn Sie versuchen, das Oak-Segment-Modul für ein Oak-Segment-Tar-Repository auszuführen (oder umgekehrt), schlägt der Start mit einer <em>IllegalStateException</em> mit der Meldung "Ungültiges Segmentformat"fehl. Daten werden jedoch nicht beschädigt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Müssen die Suchindizes neu indiziert werden? </strong></td>
   <td>Nein. Durch die Migration von Oak-Segment zu Oak-Segment-Tar werden Änderungen im Containerformat eingeführt. Die enthaltenen Daten sind davon nicht betroffen und werden nicht geändert.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie kann ich den während und nach der Migration erforderlichen Speicherplatz am besten berechnen? </strong></td>
   <td>Die Migration entspricht der Neuerstellung des Segmentspeichers im neuen Format. Auf Basis dieser Annahme können Sie den zusätzlich für die Migration erforderlichen Festplattenspeicher berechnen. Nach der Migration kann der alte Segmentspeicher gelöscht werden, um Speicherplatz zurückzugewinnen.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie kann ich die Dauer der Migration am besten abschätzen? </strong></td>
   <td>Die Migrationsleistung kann erheblich verbessert werden, wenn vor der Migration <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-offline-revision-cleanup">Offline-Revisionsbereinigung</a> ausgeführt wird. Allen Kunden wird empfohlen, diese als Voraussetzung für die Aktualisierung auszuführen. Im Allgemeinen sollte die Dauer der Migration der Dauer der Offline-Revisionsbereinigung ähneln, vorausgesetzt, die Offline-Revisionsbereinigung wurde vor der Migration ausgeführt.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Ausführen der Online-Revisionsbereinigung {#running-online-revision-cleanup}

<table>
 <tbody>
  <tr>
   <td><strong>Fragen</strong></td>
   <td><strong>Antworten</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie oft sollte die Online-Revisionsbereinigung durchgeführt werden? </strong></td>
   <td>Einmal pro Tag. Dies ist die Standardkonfiguration im Vorgangs-Dashboard.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie kann ich die Startzeit der Wartungsaufgabe für die Online-Revisionsbereinigung konfigurieren? </strong></td>
   <td>Siehe Abschnitt <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup">Ausführen der Online-Revisionsbereinigung</a> . </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Gibt es für die Online-Revisionsbereinigung eine maximale Frequenz, die nicht überschritten werden sollte? </strong></td>
   <td>Es wird empfohlen, die Online-Revisionsbereinigung einmal täglich auszuführen, wie dies standardmäßig konfiguriert ist.<br />  </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welche Indikatoren sind für die Frequenz entscheidend, in der die Online-Revisionsbereinigung ausgeführt werden sollte? </strong></td>
   <td>Es ist nicht notwendig, die Frequenz zu ermitteln, da die Online-Revisionsbereinigung als Wartungsaufgabe konfiguriert ist und täglich automatisch ausgeführt wird.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Warum gewinnt die Online-Revisionsbereinigung keinen Speicherplatz zurück, wenn sie das erste Mal ausgeführt wird? </strong></td>
   <td>Die Online-Revisionsbereinigung gewinnt alte Revisionen generationsweise zurück. Jedes Mal, wenn die Revisionsbereinigung ausgeführt wird, wird eine neue Generation erstellt. Nur Inhalt, der mindestens zwei Generationen alt ist, wird zurückgewonnen; daher wird beim erstmaligen Ausführen kein Speicherplatz zurückgewonnen.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Warum gewinnt die erste Online-Revisionsbereinigung keinen Speicherplatz zurück, wenn sie nach der Offline-Revisionsbereinigung ausgeführt wird? </strong></td>
   <td><p>Bei der Offline-Revisionsbereinigung wird alles zurückgewonnen, nur die letzte Generation bleibt erhalten. Bei der Online-Revisionsbereinigung bleiben die beiden letzten Generationen erhalten. Im Fall eines neuen Repositorys wird beim erstmaligen Ausführen der Online-Revisionsbereinigung im Anschluss an die Offline-Bereinigung kein Speicherplatz zurückgewonnen, da keine Generation alt genug für die Rückgewinnung ist.</p> <p>Lesen Sie hierzu auch den Abschnitt „Ausführen der Online-Revisionsbereinigung nach der Offline-Revisionsbereinigung“ in <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup">diesem Kapitel</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Haben Autoren- und Veröffentlichungsumgebungen in der Regel verschiedene Fenster für die Online-Revisionsbereinigung? </strong></td>
   <td>Dies hängt von den Arbeitszeiten und den Traffic-Mustern der Online-Präsenz für Kunden ab. Die Wartungsfenster sollten außerhalb der Hauptproduktionszeiten konfiguriert werden, um eine optimale Bereinigungswirksamkeit zu gewährleisten. Bei mehreren AEM-Veröffentlichungsinstanzen (TarMK-Farm) empfiehlt es sich, die Wartungsfenster für die Online-Revisionsbereinigung zu staffeln.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Müssen vor dem Ausführen der Online-Revisionsbereinigung irgendwelche Voraussetzungen erfüllt sein? </strong></td>
   <td><p>Die Online-Revisionsbereinigung ist nur mit AEM 6.3 und höheren Versionen verfügbar. Wenn Sie daher eine ältere Version von AEM verwenden, müssen Sie zum neuen <a href="/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar">Oak-Segment-Tar</a> migrieren.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welche Faktoren bestimmen die Dauer der Online-Revisionsbereinigung? </strong></td>
   <td>Es handelt sich um folgende Faktoren:<br /> 
    <ul>
     <li>Repository-Größe</li>
     <li>Systemlast (Anforderungen pro Minute, insbesondere Schreibvorgänge)</li>
     <li>Aktivitätsmuster (Lese- versus Schreibvorgänge)</li>
     <li>Hardwarespezifikationen (CPU-Leistung, Hauptspeicher, IOPS)</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Können Autoren weiterarbeiten, während die Online-Revisionsbereinigung läuft? </strong></td>
   <td>Ja, die Online-Revisionsbereinigung beherrscht gleichzeitige Schreibvorgänge. Die Online-Revisionsbereinigung ist jedoch schneller und effizienter, wenn keine gleichzeitigen Schreibvorgänge erfolgen. Es wird empfohlen, die Wartungsaufgabe für die Online-Revisionsbereinigung für einen relativ ruhigen Zeitraum mit geringem Traffic zu planen.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welche Mindestanforderungen gelten für Festplatten- und Heapspeicher, wenn die Online-Revisionsbereinigung ausgeführt wird? </strong></td>
   <td><p>Der Festplattenspeicher wird während der Online-Revisionsbereinigung kontinuierlich überwacht. Falls der verfügbare Speicherplatz unter einen kritischen Wert sinkt, wird der Vorgang abgebrochen. Der kritische Wert beträgt 25 % der aktuellen Festplattengröße auf dem Repository und kann nicht konfiguriert werden.</p> <p><strong>Es empfiehlt sich, eine Festplatte zu wählen, die mindestens zwei- oder dreimal so groß ist wie die ursprünglich geschätzte Repository-Größe.</strong></p> <p>Der verfügbare Heap-Speicher wird beim Bereinigungsvorgang ständig überwacht. Falls der verfügbare Heap-Speicher unter einen kritischen Wert sinkt, wird der Vorgang abgebrochen. Der kritische Wert wird über org.apache.jackrabbit.oak.segment.SegmentNodeStoreService#MEMORY_THRESHOLD konfiguriert. Der Standardwert ist 15%.</p> <p>Es gibt keine separaten Empfehlungen für die Mindestkomprimierung der Heap-Speichergröße zusätzlich zu den Empfehlungen für die AEM-Speichergröße. Als allgemeine Regel gilt: <strong>Falls eine AEM-Instanz ausreichend für die Anwendungsbereiche und erwartete Nutzlast dimensioniert ist, ist ausreichend Speicherplatz für den Bereinigungsvorgang vorhanden.</strong></p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Mit welcher Auswirkung auf die Performance muss beim Ausführen der Online-Revisionsbereinigung gerechnet werden? </strong></td>
   <td>Die Online-Revisionsbereinigung ist ein Hintergrundprozess, der parallel zu den normalen Systemvorgängen Daten aus dem Repository liest und in das Repository schreibt. Insbesondere benötigt der Vorgang u. U. für einen kurzen Zeitraum exklusiven Zugang zum Repository, sodass andere Threads nicht in das Repository schreiben können.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie lange dauert die Ausführung der Online-Revisionsbereinigung erwartungsgemäß? </strong></td>
   <td>Ausgehend von unseren letzten intern ausgeführten Performancetests sollte die Ausführung nicht mehr als 2 Stunden dauern.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Was muss getan werden, wenn die Online-Revisionsbereinigung länger dauert? </strong></td>
   <td>
    <ul>
     <li>Stellen Sie sicher, dass sie täglich ausgeführt wird.<br /> </li>
     <li>Stellen Sie sicher, dass sie während der minimalen Repository-Aktivitäten ausgeführt wird, indem Sie die Wartungsfenster im Vorgangs-Dashboard entsprechend konfigurieren.</li>
     <li>Vergrößern Sie die Systemressourcen (CPU, Arbeitsspeicher, E/A).</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Was passiert, wenn die Online-Revisionsbereinigung das konfigurierte Wartungsfenster überschreitet? </strong></td>
   <td>Stellen Sie sicher, dass andere Wartungsaufgaben die Ausführung nicht verzögern. Dies kann der Fall sein, falls mehrere Wartungsaufgaben zusätzlich zur Online-Revisionsbereinigung im selben Wartungsfenster ausgeführt werden. Beachten Sie, dass Wartungsaufgaben der Reihe nach ausgeführt werden und die Reihenfolge nicht konfiguriert werden kann.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Warum wird die Revisionsbereinigung übersprungen? </strong></td>
   <td><p>Die Revisionsbereinigung ermittelt in einer Schätzungsphase, ob eine Bereinigung notwendig ist. Bei der Schätzung wird die aktuelle Repository-Größe mit der Größe nach der letzten Komprimierung verglichen. Falls die Größe den konfigurierten Deltawert übersteigt, erfolgt eine Bereinigung. Der Delta-Formatbereich ist auf 1 GB eingestellt. Dies bedeutet im Grunde, dass die neue Revisionsbereinigungs-Iteration übersprungen wird, wenn die Repository-Größe seit dem letzten Bereinigungsvorgang nicht um 1 GB gewachsen ist. </p> <p>Unten sehen Sie die für die Schätzungsphase relevanten Protokolleinträge:</p>
    <ul>
     <li>Revisionsbereinigung wird ausgeführt: <em>Das Größendelta ist N% oder N/N (N/N Bytes), sodass die laufende Komprimierung</em> ausgeführt wird</li>
     <li>Revision GC führt <strong>not</strong> aus: <em>Das Delta der Größe ist N% oder N/N (N/N Byte), daher wird die Komprimierung für jetzt übersprungen</em></li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kann die automatische Komprimierung abgebrochen werden, falls die Auswirkung auf die Performance zu groß ist? </strong></td>
   <td>Ja. AEM 6.3 kann sicher über das Wartungsaufgaben-Fenster im Vorgangs-Dashboard oder über JMX beendet werden.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wenn die AEM-Instanz während einer geplanten Bereinigungsaufgabe beendet wird, wird der Prozess dann sicher beendet oder wird das Herunterfahren so lange blockiert, bis die Komprimierung abgeschlossen ist? </strong></td>
   <td>Die Revisionsbereinigung wird unterbrochen und das Repository wird sicher heruntergefahren.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Was passiert, wenn das System während der Online-Revisionsbereinigung abstürzt? </strong></td>
   <td>Es besteht in diesem Fall keine Gefahr für die Daten. Nicht bereinigte alte Daten werden bei der nächsten Bereinigung gelöscht.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welche Folgen hat es, wenn die Online-Revisionsbereinigung nicht ausgeführt wird? </strong></td>
   <td>Die Leistung verschlechtert sich mit der Zeit.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welche Revisionen werden erfasst? </strong></td>
   <td>Standardmäßig erfasst die Online-Revisionsbereinigung nur Revisionen, die mindestens 24 Stunden alt sind.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Was passiert, wenn zu viele gleichzeitige Schreibvorgänge an das Repository zu stark stören?</strong></td>
   <td><p>Wenn im System gleichzeitige Schreibvorgänge stattfinden, benötigt die Online-Revisionsbereinigung möglicherweise einen exklusiven Schreibzugriff, um die Änderungen am Ende eines Komprimierungszyklus zu committen. Das System wechselt in den <strong>forceCompact-Modus</strong>, wie ausführlicher in der <a href="https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html" target="_blank">Oak-Dokumentation</a> beschrieben. Bei der erzwungenen Komprimierung wird eine exklusive Schreibsperre angewendet, damit die Änderungen ohne störende gleichzeitige Schreibvorgänge gespeichert werden können. Um die Auswirkungen auf die Reaktionszeiten zu begrenzen, kann ein Zeitlimitwert festgelegt werden. Dieser Wert beträgt standardmäßig 1 Minute. Falls also die erzwungene Komprimierung nicht innerhalb 1 Minute abgeschlossen ist, wird die Komprimierung zugunsten gleichzeitiger Speichervorgänge abgebrochen.</p> <p>Die Dauer der erzwungenen Komprimierung hängt von folgenden Faktoren ab:</p>
    <ul>
     <li>Hardware: insbesondere IOPS. Die Dauer verkürzt sich mit steigenden IOPS.</li>
     <li>Segmentspeichergröße: Die Dauer steigt proportional zur Größe des Segmentspeichers.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p><strong>Wie wird die Online-Revisionsbereinigung auf einer Standby-Instanz ausgeführt? </strong></p> </td>
   <td><p>In einem Setup mit Cold-Standby muss nur die primäre Instanz für die Ausführung der Online-Revisionsbereinigung konfiguriert sein. Auf der Standby-Instanz muss die Online-Revisionsbereinigung nicht explizit geplant werden.</p> <p>Der entsprechende Vorgang auf einer Standby-Instanz ist die automatische Bereinigung - dies entspricht der Bereinigungsphase der Online-Revisionsbereinigung. Die automatische Bereinigung wird auf der Standby-Instanz im Anschluss an die Online-Revisionsbereinigung auf der primären Instanz ausgeführt.</p> <p>Auf der Standby-Instanz gibt es keine Schätzungs- und Komprimierungsphasen.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kann die Offline-Revisionsbereinigung mehr Speicherplatz freigeben als die Online-Revisionsbereinigung? </strong></td>
   <td><p>Die Offline-Revisionsbereinigung kann alte Revisionen sofort entfernen, während die Online-Revisionsbereinigung alte Versionen berücksichtigen muss, die weiterhin vom Anwendungsstapel referenziert werden. Bei der Offline-Revisionsbereinigung werden alte Daten also aggressiver bereinigt; bei der Online-Revisionsbereinigung zeigt sich der Effekt nach einigen Bereinigungszyklen.</p> <p>Lesen Sie hierzu auch den Abschnitt „Ausführen der Online-Revisionsbereinigung nach der Offline-Revisionsbereinigung“ in <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup">diesem Kapitel</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Gibt es Aspekte, die bei Dateioperationen mit Speicherzuordnung beachtet werden müssen?</td>
   <td>
    <ul>
     <li><strong>In Windows-Umgebungen</strong> wird immer der reguläre Dateizugriff erzwungen, sodass der speicherzugeordnete Zugriff nicht verwendet wird. Als allgemeine Empfehlung sollte der gesamte verfügbare RAM dem Heap zugeordnet und die segmentCache-Größe erhöht werden. Sie erhöhen den segmentCache, indem Sie die Option segmentCache.size zur Datei org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config hinzufügen (z. B. segmentCache.size=20480). Denken Sie daran, auch RAM für das Betriebssystem und andere Prozesse einzuplanen.</li>
     <li><strong>In Nicht-Windows-Umgebungen</strong> erhöhen Sie die Größe des physischen Speichers, um die Speicherzuordnung des Repositorys zu verbessern.</li>
    </ul> </td>
   <td>
    <ul>
     <li> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Überwachen der Online-Revisionsbereinigung {#monitoring-online-revision-cleanup}

<table>
 <tbody>
  <tr>
   <td><strong>Was muss während der Online-Revisionsbereinigung überwacht werden?</strong></td>
   <td>
    <ul>
     <li>Wenn die Online-Revisionsbereinigung aktiviert ist, sollte der Festplattenspeicher überwacht werden. Die Bereinigung wird nicht ausgeführt oder vorzeitig beendet, falls nicht genügend Speicherplatz vorhanden ist.</li>
     <li>Überprüfen Sie die Protokolldateien auf die Ausführungsdauer der Online-Revisionsbereinigung. Sie sollte nicht länger als 2 Stunden in Anspruch nehmen.</li>
     <li>Anzahl der Checkpoints. Falls bei der Komprimierung mehr als drei Prüfpunkte auftreten, wird empfohlen, die Prüfpunkte zu bereinigen.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie kann ich überprüfen, ob die Online-Revisionsbereinigung erfolgreich abgeschlossen wurde?</strong></td>
   <td><p>Sie können überprüfen, ob die Online-Revisionsbereinigung erfolgreich abgeschlossen wurde, indem Sie die Protokolle überprüfen.</p> <p>Beispiel: "<code>TarMK GC #{}: compaction completed in {} ({} ms), after {} cycles</code>"bedeutet, dass der Komprimierungsschritt erfolgreich abgeschlossen wurde, es sei denn, der Meldung "<code>TarMK GC #{}: compaction gave up compacting concurrent commits after {} cycles</code>"vorangestellt ist, was bedeutet, dass zu viele gleichzeitige Lasten aufgetreten sind.</p> <p>Dementsprechend gibt es eine Meldung "<code>TarMK GC #{}: cleanup completed in {} ({} ms</code>"für den erfolgreichen Abschluss des Bereinigungsschritts.</p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><strong>Wo finden wir die Statistiken der letzten Online-Revisionsbereinigungen?</strong></td>
   <td><p>Status, Fortschritt und Statistiken werden über JMX (<code>SegmentRevisionGarbageCollection</code> MBean) verfügbar gemacht. Weitere Informationen zum MBean <code>SegmentRevisionGarbageCollection</code> finden Sie im <a href="https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#monitoring-via-jmx" target="_blank">folgenden Absatz</a>.</p> <p>Der Fortschritt kann über das Attribut <code>EstimatedRevisionGCCompletion</code> der <code>SegmentRevisionGarbageCollection MBean.</code></p> <p>Sie können mit <code>ObjectName org.apache.jackrabbit.oak:name="Segment node store revision garbage collection",type="SegmentRevisionGarbageCollection”</code> eine Referenz des MBean abrufen.</p> <p>Beachten Sie, dass Statistiken nur ab dem letzten Systemstart verfügbar sind. Sie können externe Überwachungstools verwenden, um Daten über die AEM-Laufzeit hinaus aufzubewahren. Siehe <a href="/help/sites-administering/operations-dashboard.md#monitoring-with-nagios" target="_blank">die AEM Dokumentation zum Anhängen von Konsistenzprüfungen an Nagios als Beispiel für ein externes Überwachungstool</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welche Protokolleinträge sind relevant?</strong></td>
   <td>
    <ul>
     <li>Die Online-Revisionsbereinigung wurde gestartet/beendet.
      <ul>
       <li>Die Online-Revisionsbereinigung umfasst drei Phasen: Schätzung, Komprimierung und Bereinigung. In der Schätzungsphase kann das Überspringen der Komprimierung und Bereinigung erzwungen werden, falls das Repository nicht ausreichend viele alte Daten enthält. In der neuesten Version von AEM markiert die Meldung "<code>TarMK GC #{}: estimation started</code>"den Beginn der Schätzung, "<code>TarMK GC #{}: compaction started, strategy={}</code>"markiert den Beginn der Komprimierung und "T<code>arMK GC #{}: cleanup started. Current repository size is {} ({} bytes</code>"den Beginn der Bereinigung.</li>
      </ul> </li>
     <li>Durch die Revisionsbereinigung gesammelter Speicherplatz
      <ul>
       <li>Der Speicherplatz wird erst nach Abschluss der Bereinigungsphase zurückgewonnen. Der Abschluss der Bereinigungsphase wird durch die Protokollmeldung "T<code>arMK GC #{}: cleanup completed in {} ({} ms</code>"gekennzeichnet. Post cleanup size is {} ({} bytes) and space reclaimed {} ({} bytes). Compaction map weight/depth is {}/{} ({} bytes/{}).&amp;quot;.</li>
      </ul> </li>
     <li>Während der Revisionsbereinigung ist ein Problem aufgetreten
      <ul>
       <li>Es gibt viele Fehlerbedingungen. Alle sind durch WARN- oder ERROR-Protokollmeldungen gekennzeichnet, die mit "TarMK GC"beginnen.</li>
      </ul> </li>
    </ul> <p>Weitere Informationen finden Sie unten im Abschnitt <a href="/help/sites-deploying/revision-cleanup.md#troubleshooting-based-on-error-messages">Fehlerbehebung basierend auf Fehlermeldungen</a> .</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie kann ich überprüfen, wie viel Speicherplatz nach Abschluss der Online-Revisionsbereinigung zurückgewonnen wurde?</strong></td>
   <td>Am Ende des Bereinigungszyklus wird im Protokoll eine Meldung angezeigt: "<code>TarMK GC #3: cleanup completed</code>", der die Größe des Repositorys und den Umfang des zurückgewonnenen Speicherbereinigtes umfasst.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie kann die Integrität des Repositorys nach Abschluss der Online-Revisionsbereinigung überprüft werden?</strong></td>
   <td><p>Nach der Online-Revisionsbereinigung ist keine Repository-Integritätsprüfung erforderlich. </p> <p>Sie können jedoch die folgenden Aktionen ausführen, um den Repository-Status nach der Bereinigung zu überprüfen:</p>
    <ul>
     <li>Ein Repository <a href="/help/sites-deploying/consistency-check.md" target="_blank">traversal check</a></li>
     <li>Verwenden Sie das oak-run-Tool nach Abschluss des Bereinigungsprozesses, um nach Inkonsistenzen zu suchen. Weitere Informationen dazu finden Sie in der <a href="https://github.com/apache/jackrabbit-oak/blob/trunk/oak-doc/src/site/markdown/nodestore/segment/overview.md#check" target="_blank">Apache-Dokumentation.</a> Sie müssen das Tool nicht herunterfahren, AEM Sie es ausführen.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie kann ich feststellen, ob die Online-Revisionsbereinigung fehlgeschlagen ist und welche Wiederherstellungsschritte sind erforderlich?</strong></td>
   <td>Fehlerbedingungen werden durch WARN- oder ERROR-Protokollmeldungen gekennzeichnet, die mit "TarMK GC"beginnen. Weitere Informationen finden Sie unten im Abschnitt <a href="/help/sites-deploying/revision-cleanup.md#troubleshooting-based-on-error-messages">Fehlerbehebung basierend auf Fehlermeldungen</a> .</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welche Informationen werden in der Konsistenzprüfung der Revisionsbereinigung angezeigt? Wie und wann tragen sie zu den farbcodierten Statusstufen bei? </strong></td>
   <td><p>Die Konsistenzprüfung der Revisionsbereinigung ist Teil des <a href="/help/sites-administering/operations-dashboard.md#health-reports" target="_blank">Vorgangs-Dashboards</a>.<br /> </p> <p>Der Status lautet <strong>GREEN</strong> , wenn die letzte Ausführung der Online-Revisionsbereinigung erfolgreich abgeschlossen wurde.</p> <p>Es ist <strong>YELLOW</strong>, wenn die Wartungsaufgabe der Online-Revisionsbereinigung einmal abgebrochen wurde.<br /> </p> <p>Es ist <strong>RED</strong>, wenn die Wartungsaufgabe für die Online-Revisionsbereinigung dreimal hintereinander abgebrochen wurde. <strong>In diesem Fall ist eine manuelle Interaktion </strong> erforderlich, da die Online-Revisionsbereinigung wahrscheinlich erneut fehlschlägt. Weitere Informationen finden Sie unten im Abschnitt <a href="/help/sites-deploying/revision-cleanup.md#troubleshooting-online-revision-cleanup">Fehlerbehebung</a>.<br /> </p> <p>Beachten Sie, dass der Status der Konsistenzprüfung nach jedem Systemneustart zurückgesetzt wird. Für eine neu gestartete Instanz wird der Status der Konsistenzprüfung der Revisionsbereinigung grün angezeigt. Sie können externe Überwachungstools verwenden, um Daten über die AEM-Laufzeit hinaus aufzubewahren. Siehe <a href="/help/sites-administering/operations-dashboard.md#monitoring-with-nagios">die AEM Dokumentation zum Anhängen von Konsistenzprüfungen an Nagios als Beispiel für ein externes Überwachungstool</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p><strong>Wie überwacht man die automatische Bereinigung auf einer Standby-Instanz?</strong></p> </td>
   <td><p>Status, Fortschritt und Statistiken werden über JMX mithilfe des MBean <code>SegmentRevisionGarbageCollection</code> bereitgestellt. Siehe auch die folgende <a href="https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#monitoring-via-jmx" target="_blank">Oak-Dokumentation</a>. </p> <p>Sie können eine Referenz des MBean mit dem <code>ObjectName org.apache.jackrabbit.oak:name="Segment node store revision garbage collection",type="SegmentRevisionGarbageCollection”</code> abrufen.</p> <p>Beachten Sie, dass die Statistiken nur seit dem letzten Systemstart verfügbar sind. Sie können externe Überwachungstools verwenden, um Daten über die AEM-Laufzeit hinaus aufzubewahren. Siehe auch die AEM Dokumentation zum Anhängen von Konsistenzprüfungen an Nagios als Beispiel für ein externes Überwachungstool</a>.<a href="/help/sites-administering/operations-dashboard.md#monitoring-with-nagios" target="_blank"></a></p> <p>Anhand der Protokolldateien können Sie auch den Status, den Fortschritt und die Statistiken der automatischen Bereinigung überprüfen.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p><strong>Was muss während der automatischen Bereinigung auf einer Standby-Instanz überwacht werden?</strong></p> </td>
   <td>
    <ul>
     <li>Der Festplattenspeicher sollte überwacht werden, wenn die automatische Bereinigung ausgeführt wird.</li>
     <li>Die Ausführungsdauer (siehe Protokolle) sollte zwei Stunden nicht überschreiten.</li>
     <li>Segmentspeichergröße nach Ausführung der automatischen Bereinigung. Der Segmentspeicher auf der Standby-Instanz sollte ungefähr so groß wie der auf der primären Instanz sein.</li>
    </ul> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Fehlerbehebung bei der Online-Revisionsbereinigung {#troubleshooting-online-revision-cleanup}

<table>
 <tbody>
  <tr>
   <td><strong>Was kann schlimmstenfalls passieren, falls die Online-Revisionsbereinigung nicht ausgeführt wird?</strong></td>
   <td>Die AEM-Instanz hat keinen Speicherplatz mehr, was zu Produktionsausfällen führt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Ist ein hoher Benutzer-Traffic problematisch, wenn ich die Online-Revisionsbereinigung auf einer Veröffentlichungsinstanz ausführen möchte?</strong></td>
   <td>Hoher Benutzer-Traffic wirkt sich darauf aus, ob die Komprimierungsphase erfolgreich abgeschlossen wird oder nicht.<br />  </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Gemäß Konsistenzprüfung und Protokolleinträgen ist die Online-Revisionsbereinigung dreimal in Folge fehlgeschlagen. Was ist erforderlich, um die Online-Revisionsbereinigung erfolgreich abzuschließen? </strong></td>
   <td>Sie können verschiedene Maßnahmen ergreifen, um das Problem zu identifizieren und zu beheben:<br /> 
    <ul>
     <li>Analysieren Sie zunächst die Protokolleinträge.<br />  </li>
     <li>Führen Sie je nach den in den Protokollen angezeigten Informationen folgende Schritte aus:
      <ul>
       <li>Wenn in den Protokollen fünf verpasste kompakte Zyklen und eine Zeitüberschreitung beim <code>forceCompact</code>-Zyklus angezeigt werden, planen Sie das Wartungsfenster auf eine ruhige Zeit, wenn die Menge an Repository-Schreibvorgängen gering ist. Sie können die Schreibweise des Repositorys im Tool zur Überwachung der Repository-Metriken unter <em>https://serveraddress:serverport/libs/granite/operations/content/monitoring/page.html</em> überprüfen.</li>
       <li>Falls die Bereinigung am Ende des Wartungsfenster angehalten wurde, überprüfen Sie auf der Benutzeroberfläche für Wartungsaufgaben, ob das Wartungsfenster ausreichend lange konfiguriert ist.</li>
       <li>Falls der verfügbare Heap-Speicher nicht ausreicht, stellen Sie sicher, dass die Instanz genügend Speicher hat.</li>
       <li>Im Fall einer langsamen Reaktion wächst der Segmentspeicher möglicherweise zu schnell, sodass die Online-Revisionsbereinigung auch in einem längeren Wartungsfenster nicht abgeschlossen werden kann. Falls beispielsweise die Online-Revisionsbereinigung in der letzten Woche nicht erfolgreich abgeschlossen wurde, wird empfohlen, eine Offline-Wartung zu planen und eine Offline-Revisionsbereinigung auszuführen, um die Größe des Segmentspeichers zu beschränken.</li>
      </ul> </li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wie muss ich vorgehen, wenn die Warnfunktion bei der Konsistenzprüfung aktiviert ist?</strong></td>
   <td>Siehe vorherigen Punkt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Was passiert, wenn die Zeit bei der Online-Revisionsbereinigung in einem geplanten Wartungsfenster überschritten wird?</strong></td>
   <td>Die Online-Revisionsbereinigung wird abgebrochen und Reste werden entfernt. Die Online-Revisionsbereinigung wird im nächsten geplanten Wartungsfenster neu gestartet.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Was verursacht die Protokollierung von <code>SegmentNotFoundException</code>-Instanzen in <code>error.log</code> und wie kann ich sie wiederherstellen?</strong></td>
   <td><p>Ein <code>SegmentNotFoundException</code> wird vom TarMK protokolliert, wenn er versucht, auf eine Speichereinheit (ein Segment) zuzugreifen, die nicht gefunden werden kann. Es gibt drei Situationen, die diesen Fehler verursachen können:</p>
    <ol>
     <li>Eine Anwendung, die die empfohlenen Zugriffsmechanismen (wie Sling und die JCR-API) umgeht und über eine API/SPI auf niedrigerer Ebene auf das Repository zugreift und dann die Aufbewahrungsdauer für ein Segment überschreitet. Anders ausgedrückt, es wird eine Referenz auf eine Einheit für einen längeren Zeitraum als die von der Online-Revisionsbereinigung erlaubte Aufbewahrungsdauer (standardmäßig 24 Stunden) beibehalten. Dieser Fall tritt nur vorübergehend auf und führt nicht zu einer Beschädigung von Daten. Um eine Wiederherstellung zu ermöglichen, sollte das Tool oak-run verwendet werden, um die vorübergehende Natur der Ausnahme zu bestätigen (bei der Oak-Run-Prüfung sollten keine Fehler gemeldet werden). Dazu muss die Instanz offline geschaltet und danach neu gestartet werden.</li>
     <li>Ein externes Ereignis hat die Beschädigung der Daten auf der Festplatte verursacht. Hierbei kann es sich um einen Datenträgerfehler, ungenügenden Festplattenspeicher oder eine unbeabsichtigte Änderung der erforderlichen Datendateien handeln. In diesem Fall müssen Sie die Instanz in den Offline-Modus versetzen und den Fehler mithilfe der oak-run-Prüfung beheben. Weitere Informationen zum Ausführen der Oak-Run-Prüfung finden Sie in der folgenden <a href="https://github.com/apache/jackrabbit-oak/blob/trunk/oak-doc/src/site/markdown/nodestore/segment/overview.md#check" target="_blank">Apache-Dokumentation</a>.</li>
     <li>Alle anderen Vorkommnisse sollten über die <a href="https://helpx.adobe.com/de/marketing-cloud/contact-support.html" target="_blank">Adobe-Kundenunterstützung</a> adressiert werden.</li>
    </ol> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Fehlerbehebung basierend auf Fehlermeldungen {#troubleshooting-based-on-error-messages}

Die Datei error.log ist ausführlich, wenn es während der Online-Revisionsbereinigung zu Vorfällen kommt. In der folgenden Matrix werden die häufigsten Fehlermeldungen und mögliche Lösungen erläutert:

| **Schritt** | **Protokollmeldungen** | **Erklärung** | **Nächste Schritte** |
|---|---|---|---|
|  |  |  |  |
| Schätzung | TarMK GC #2: Schätzung übersprungen, weil die Komprimierung angehalten wurde | Die Schätzungsphase wird übersprungen, wenn die Komprimierung im System durch Konfiguration deaktiviert ist. | Aktivieren der Online-Revisionsbereinigung. |
|  | TarMK GC #2: Schätzung unterbrochen: ${GRUND}. Skipping compaction. | Die Schätzungsphase wurde vorzeitig beendet. Beispiele für Ereignisse, die die Schätzungsphase unterbrechen können: ungenügender Arbeitsspeicher oder Festplattenspeicher auf dem Hostsystem | Hängt vom angegebenen Grund ab. |
| Komprimierung | TarMK GC #2: Komprimierung angehalten | Solange die Komprimierungsphase durch die Konfiguration angehalten wird, werden weder die Schätzungsphase noch die Komprimierungsphase ausgeführt. | Aktivieren Sie die Online-Revisionsbereinigung. |
|  | TarMK GC #2: Komprimierung abgebrochen: ${GRUND}. | Die Komprimierungsphase wurde vorzeitig beendet. Beispiele für Ereignisse, die die Komprimierungsphase unterbrechen können: ungenügender Arbeitsspeicher oder Festplattenspeicher auf dem Hostsystem. Eine Komprimierung kann auch abgebrochen werden, wenn das System heruntergefahren wird, oder explizit über eine administrative Schnittstelle wie das Wartungsfenster im Vorgangs-Dashboard. | Hängt vom angegebenen Grund ab. |
|  | TarMK GC #2: Komprimierung fehlgeschlagen in 32.902 Min. (1974140 ms), nach 5 Zyklen | Diese Meldung bedeutet nicht, dass ein nicht behebbarer Fehler aufgetreten ist, sondern nur, dass die Komprimierung nach einer bestimmten Anzahl von Versuchen beendet wurde. Lesen Sie auch den [folgenden Absatz](https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#how-does-compaction-works-with-concurrent-writes). | Lesen Sie die folgende [Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#how-does-compaction-works-with-concurrent-writes) und die letzte Frage des Abschnitts [Ausführen der Online-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#running-online-revision-cleanup) . |
| Bereinigen | TarMK GC #2: Bereinigung unterbrochen | Die Bereinigung wurde durch Herunterfahren des Repositorys abgebrochen. Es sind keinerlei Auswirkungen auf die Konsistenz zu erwarten. Außerdem wird wahrscheinlich nicht der ganze Festplattenspeicher zurückgewonnen. Dieser wird beim nächsten Revisionsbereinigungszyklus zurückgewonnen. | Finden Sie heraus, warum das Repository heruntergefahren wurde; versuchen Sie in Zukunft, das Repository nicht während eines Wartungsfensters herunterzufahren. |

## Ausführen der Offline-Revisionsbereinigung {#how-to-run-offline-revision-cleanup}

>[!CAUTION]
>
>Je nach der mit der AEM-Installation verwendeten Oak-Version müssen unterschiedliche Versionen des Tools „oak-run“ verwendet werden. Prüfen Sie die nachfolgend aufgeführten Versionsanforderungen, bevor Sie das Tool nutzen:
>
>* Verwenden Sie für Oak-Versionen **1.0.0 bis 1.0.11** oder **1.1.0 bis 1.1.6** die Oak-run-Version** 1.0.11**
   >
   >
* Für **neuere** Oak-Versionen verwenden Sie die oak-run-Version, die dem Oak-Core der AEM-Installation entspricht.

>



Adobe bietet ein Tool namens **Oak-run** für die Durchführung der Revisionsbereinigung. Es kann unter folgender URL heruntergeladen werden:

[https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/)

Bei dem Tool handelt es sich um eine ausführbare JAR-Datei, die manuell ausgeführt werden kann, um das Repository zu komprimieren. Dieser Vorgang wird als Offline-Revisionsbereinigung bezeichnet, da das Repository zum korrekten Ausführen des Tools heruntergefahren werden muss. Planen Sie die Bereinigung für das konfigurierte Wartungsfenster.

Tipps zur Leistungssteigerung des Bereinigungsprozesses finden Sie unter [Steigern der Leistung der Offline-Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md#increasing-the-performance-of-offline-revision-cleanup).

>[!NOTE]
>
>Vor der Wartung können Sie außerdem alte Prüfpunkte löschen (Schritte 2 und 3 unten). Dies wird nur für Instanzen empfohlen, die mehr als 100 Prüfpunkte aufweisen.

1. Stellen Sie immer sicher, dass Sie über eine Sicherungskopie der AEM-Instanz verfügen.

   Fahren Sie AEM herunter.

1. (Optional) Verwenden Sie das Tool, um alte Prüfpunkte zu finden:

   ```xml
   java -jar oak-run.jar checkpoints install-folder/crx-quickstart/repository/segmentstore
   ```

1. (Optional) Löschen Sie die nicht referenzierten Prüfpunkte:

   ```xml
   java -jar oak-run.jar checkpoints install-folder/crx-quickstart/repository/segmentstore rm-unreferenced
   ```

1. Führen Sie die Komprimierung aus und warten Sie, bis diese abgeschlossen ist:

   ```xml
   java -jar -Dsun.arch.data.model=32 oak-run.jar compact install-folder/crx-quickstart/repository/segmentstore
   ```

### Steigern der Leistung der Offline-Revisionsbereinigung  {#increasing-the-performance-of-offline-revision-cleanup}

Das Oak-run-Tool beinhaltet diverse Funktionen, die die Leistung der Revisionsbereinigung steigern und das Wartungsfenster so weit wie möglich verkleinern.

Die Liste enthält einige Befehlszeilenparameter, wie im Folgenden beschrieben:

* **-mmap.** Sie können dies als &quot;true&quot;oder &quot;false&quot;festlegen. Wenn „true“ festgelegt ist, wird der Zugriff mit Speicherzuordnung verwendet. Wenn „false“ festgelegt ist, wird der Dateizugriff verwendet. Wenn kein Wert festgelegt ist, wird auf 64-Bit-Systemen der Zugriff mit Speicherzuordnung und auf 32-Bit-Systemen der Dateizugriff verwendet. Unter Windows wird immer der reguläre Dateizugriff erzwungen, weshalb diese Option ignoriert wird. **Dieser Parameter hat den Parameter -Dtar.memoryMapped ersetzt.**

* **-Dupdate.limit**. Definiert den Schwellenwert für das Löschen temporärer Transaktionen auf der Festplatte. Der Standardwert ist 10000.

* **-Dcompress-interval**. Anzahl der Komprimierungszuordnungseinträge, die bis zur Komprimierung der aktuellen Zuordnung beibehalten werden. Standard: 1000000. Sie sollten für diesen Wert eine noch höhere Zahl festlegen, um einen schnelleren Durchsatz zu erzielen, falls nicht genügend Heap-Speicher vorhanden ist. **Dieser Parameter wurde in Oak Version 1.6 entfernt und hat keine Auswirkung.** 

* **-Dcompaction-progress-log**. Die Anzahl der komprimierten Knoten, die protokolliert werden. Der Standardwert ist 150000, was bedeutet, dass die ersten 150000 komprimierten Knoten während des Vorgangs protokolliert werden. Verwenden Sie diese Option zusammen mit dem im Folgenden erläuterten Parameter.

* **-Dtar.PersistCompactionMap.** Setzen Sie diesen Parameter auf &quot;true&quot;, um Speicherplatz anstelle des Heap-Speichers für die Persistenz von Komprimierungskarten zu verwenden. Erfordert das Oak-Run-Tool **Version 1.4** und höher. Weitere Informationen finden Sie unter Frage 3 im Abschnitt [Häufig gestellte Fragen zur Offline-Revisionsbereinigung. ](/help/sites-deploying/revision-cleanup.md#offline-revision-cleanup-frequently-asked-questions) **Dieser Parameter wurde in Oak Version 1.6 entfernt und hat keine Auswirkung.** 

* **--force.** Erzwingen Sie die Komprimierung und ignorieren Sie eine nicht übereinstimmende Segmentspeicherversion.

>[!CAUTION]
>
>Mit dem Parameter `--force` wird der Segmentspeicher auf die neueste Version aktualisiert, was mit älteren Oak-Versionen inkompatibel ist. Beachten Sie außerdem, dass kein Downgrade möglich ist. Generell sollten Sie diese Parameter vorsichtig verwenden und nur, wenn Sie wirklich wissen, wie sie verwendet werden.

Ein Beispiel der verwendeten Parameter:

```xml
java -Dupdate.limit=10000 -Dcompaction-progress-log=150000 -Dlogback.configurationFile=logback.xml -Xmx8g -jar oak-run-*.jar checkpoints <repository>
```

### Zusätzliche Methoden zum Auslösen der Revisions-Bereinigung  {#additional-methods-of-triggering-revision-cleanup}

Zusätzlich zu den oben genannten Methoden können Sie die Revisionsbereinigung auch wie folgt über die JMX-Konsole auslösen:

1. Öffnen Sie die JMX-Konsole, indem Sie zu [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx) navigieren.
1. Klicken Sie auf das MBean **RevisionGarbageCollection**.
1. Klicken Sie im nächsten Fenster auf **startRevisionGC()** und dann auf **Invoke** , um den Auftrag zur Revisionsbereinigung zu starten.

### Häufig gestellte Fragen zur Offline-Revisionsbereinigung {#offline-revision-cleanup-frequently-asked-questions}

<table>
 <tbody>
  <tr>
   <td><strong>Welche Faktoren bestimmen die Dauer der Offline-Revisionsbereinigung? </strong></td>
   <td><p>Die Größe des Repositorys und die Anzahl der Revisionen, die bereinigt werden müssen, bestimmen die Dauer der Bereinigung.</p> </td>
  </tr>
  <tr>
   <td><strong>Was ist der Unterschied zwischen einer Revision und einer Seitenversion? </strong></td>
   <td>
    <ul>
     <li><strong>Oak-Revision:</strong> Oak organisiert den gesamten Inhalt in einer großen Baumstruktur, die aus Knoten und Eigenschaften besteht. Jede Momentaufnahme bzw. jede Revision dieser Inhaltsstruktur ist unveränderlich; Änderungen der Struktur werden als eine Reihe neuer Revisionen ausgedrückt. In der Regel wird durch jede Inhaltsänderung eine neue Revision ausgelöst. Siehe auch <a href="https://jackrabbit.apache.org/dev/ngp.html" target="_blank"> Follow link</a>.</li>
     <li><strong>Seitenversion: </strong> Durch die Versionierung wird ein "Schnappschuss"einer Seite zu einem bestimmten Zeitpunkt erstellt. In der Regel wird eine neue Version erstellt, wenn eine Seite aktiviert ist. Weitere Informationen finden Sie unter <a href="/help/sites-authoring/working-with-page-versions.md" target="_blank">Arbeiten mit Seitenversionen</a>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Wie kann ich die Offline-Revisionsbereinigung beschleunigen, wenn diese Aufgabe nicht innerhalb von 8 Stunden abgeschlossen wird? </strong></td>
   <td>Wenn die Revisionsaufgabe nicht innerhalb von 8 Stunden abgeschlossen wird und die <a href="/help/sites-administering/operations-dashboard.md#diagnosis-tools" target="_blank">Thread-Dumps</a> zeigen, dass der Haupt-Hotspot <code>InMemoryCompactionMap.findEntry</code> ist, verwenden Sie den folgenden Parameter mit dem Oak-Run-Tool <strong>Versionen 1.4 </strong>oder höher: <code>-Dtar.PersistCompactionMap=true</code>. Beachten Sie, dass der Parameter <code>-Dtar.PersistCompactionMap</code> in Oak Version 1.6 entfernt wurde.</td>
  </tr>
 </tbody>
</table>
