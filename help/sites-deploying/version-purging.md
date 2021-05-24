---
title: Versionsbereinigung
seo-title: Versionsbereinigung
description: In diesem Artikel werden die verfügbaren Optionen für die Versionsbereinigung beschrieben.
seo-description: In diesem Artikel werden die verfügbaren Optionen für die Versionsbereinigung beschrieben.
uuid: a9fa25c7-e60e-4665-a726-99af9aac8f70
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: fb4d7337-7b94-430b-80d2-f1754f823c2b
docset: aem65
feature: Konfiguration
exl-id: 6f0b1951-bdda-475f-b6c0-bc18de082b7c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 69%

---

# Versionsbereinigung{#version-purging}

Bei einer Standardinstallation erstellt AEM eine neue Version einer Seite oder eines Knotens, wenn Sie eine Seite nach der Aktualisierung des Inhalts aktivieren.

>[!NOTE]
>
>Werden keine Änderungen am Inhalt vorgenommen, wird eine Meldung angezeigt, dass die Seite aktiviert wurde. Es wird jedoch keine neue Version erstellt.

Mit der Registerkarte **Versionierung** des Sidekicks können Sie auf Anforderung zusätzliche Versionen erstellen. Diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie bereinigt. Daher wächst die Größe des Repositorys im Laufe der Zeit an und muss verwaltet werden.

AEM stellt eine Reihe von Mechanismen zum Verwalten Ihres Repositorys zur Verfügung:

* [Versionsmanager](#version-manager) Der Manager kann so konfiguriert werden, dass alte Versionen bei der Erstellung von neuen Versionen entfernt werden.

* das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) Dieses Tool wird im Rahmen der Überwachung und Wartung Ihres Repositorys verwendet.
Hiermit können Sie alte Versionen eines Knotens oder eine Hierarchie von Knoten entsprechend den folgenden Parametern entfernen:

   * Die maximale Anzahl der Versionen, die im Repository gespeichert werden sollen.
Wird dieser Wert überschritten, wird die älteste Version entfernt.

   * Das Höchstalter einer im Repository gespeicherten Version.
Wenn das Alter einer Version diesen Wert überschreitet, wird sie aus dem Repository gelöscht.

* die Wartungsaufgabe [Versionsbereinigung](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Sie können die Wartungsaufgabe zur Versionsbereinigung planen, um alte Versionen automatisch zu löschen. Dadurch wird die Notwendigkeit minimiert, die Tools zur Versionsbereinigung manuell zu verwenden.

>[!CAUTION]
>
>Um die Größe des Repositorys zu optimieren, sollten Sie die Aufgabe zur Versionsbereinigung regelmäßig ausführen. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn der Netzwerkverkehr begrenzt ist.

## Versions-Manager {#version-manager}

Zusätzlich zur expliziten Bereinigung mit dem Bereinigungs-Tool kann der Versions-Manager so konfiguriert werden, dass alte Versionen bei der Erstellung von neuen Versionen entfernt werden.

Um den Versionsmanager zu konfigurieren, erstellen Sie [eine Konfiguration](/help/sites-deploying/configuring-osgi.md) für:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Die folgenden Optionen sind verfügbar:

* `versionmanager.createVersionOnActivation` (Boolesch, Standard: true) Gibt an, ob eine Version erstellt werden soll, wenn Seiten aktiviert werden.
Eine Version wird erstellt, es sei denn, der Replikationsagent ist so konfiguriert, dass er die Erstellung von Versionen unterdrückt, was vom Versions-Manager berücksichtigt wird.
Eine Version wird nur erstellt, wenn die Aktivierung auf einem Pfad erfolgt, der in `versionmanager.ivPaths` enthalten ist (siehe unten).

* `versionmanager.ivPaths`(String[], Standard:  `{"/"}`) Gibt die Pfade an, auf denen Versionen bei Aktivierung implizit erstellt werden, wenn auf &quot;true&quot;gesetzt  `versionmanager.createVersionOnActivation` ist.

* `versionmanager.purgingEnabled` (Boolesch, Standard: false) Definiert, ob die Bereinigung aktiviert werden soll, wenn neue Versionen erstellt werden.

* `versionmanager.purgePaths` (String[], Standard: {&quot;/content&quot;}) Gibt an, auf welchen Pfaden Versionen beim Erstellen neuer Versionen gelöscht werden sollen.

* `versionmanager.maxAgeDays` (int, Standard: 30) Bei der Versionsbereinigung werden alle Versionen entfernt, die älter als der konfigurierte Wert sind. Wenn der Wert kleiner als 1 ist, wird die Bereinigung nicht basierend auf dem Alter der Version durchgeführt.

* `versionmanager.maxNumberVersions` (int, Standard 5) Bei der Versionsbereinigung werden alle Versionen entfernt, die älter als die n. neueste Version sind. Wenn der Wert kleiner als 1 ist, wird die Bereinigung nicht basierend auf der Anzahl der Versionen durchgeführt.

* `versionmanager.minNumberVersions` (int, Standard 0) Die Mindestanzahl der Versionen, die unabhängig vom Alter beibehalten werden. Wenn hier ein Wert kleiner als 1 festgelegt wird, wird keine Mindestanzahl an Versionen beibehalten.

>[!NOTE]
>
>Es wird nicht empfohlen, eine große Anzahl von Versionen im Repository zu halten. Achten Sie also bei der Konfiguration des Versions-Bereinigungsvorgangs darauf, nicht zu viele Versionen von der Bereinigung auszuschließen, da sonst die Größe des Repositorys nicht richtig optimiert wird. Wenn Sie aufgrund geschäftlicher Anforderungen eine große Anzahl von Versionen aufbewahren, wenden Sie sich an den Support von Adobe, um alternative Möglichkeiten zur Optimierung der Repository-Größe zu finden.

### Kombinieren von Aufbewahrungsoptionen {#combining-retention-options}

Die Optionen, die definieren, wie welche Versionen beibehalten werden sollen ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), können je nach Ihren Anforderungen kombiniert werden.

Wenn Sie z. B. die Anzahl der Versionen, die maximal aufbewahrt werden, UND die älteste aufzubewahrende Version definieren:

* Einstellung:

   * `maxNumberVersions` = 7

   * `maxAgeDays` = 30

* mit:

   * 10 Versionen, die in den letzten 60 Tagen erstellt wurden,
   * von denen 3 Versionen innerhalb der letzten 30 Tage erstellt wurden,

* bedeutet dies, dass:

   * die letzten 3 Versionen aufbewahrt werden.

Wenn Sie z. B. die maximale UND die minimale Anzahl von Versionen, die aufbewahrt werden, UND die älteste beizubehaltende Version definieren:

* Einstellung:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* mit:

   * 5 Versionen, die in den letzten 60 Tagen erstellt wurden

* bedeutet dies, dass:

   * 3 Versionen aufbewahrt werden.

## Tool „Versionen bereinigen“{#purge-versions-tool}

Das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) dient zum Bereinigen der Versionen eines Knotens oder einer Hierarchie von Knoten in Ihrem Repository. Der Hauptzweck ist die Verkleinerung des Repositorys durch Löschen alter Knotenversionen.
