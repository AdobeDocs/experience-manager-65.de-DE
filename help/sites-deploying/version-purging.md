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
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
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

* die [Aufgabe Versionsbereinigung (Maintenance)](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Sie können die Wartungsaufgabe zur Versionsbereinigung planen, um alte Versionen automatisch zu löschen. Dadurch wird die manuelle Verwendung der Werkzeuge zum Bereinigen der Version minimiert.

>[!CAUTION]
>
>Um die Größe des Repositorys zu optimieren, sollten Sie die Aufgabe zur Versionsbereinigung regelmäßig ausführen. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn der Netzwerkverkehr begrenzt ist.

## Versions-Manager {#version-manager}

Zusätzlich zur expliziten Bereinigung mit dem Bereinigungs-Tool kann der Versions-Manager so konfiguriert werden, dass alte Versionen bei der Erstellung von neuen Versionen entfernt werden.

Um den Version Manager zu konfigurieren, [erstellen Sie eine Konfiguration](/help/sites-deploying/configuring-osgi.md) für:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Die folgenden Optionen sind verfügbar:

* `versionmanager.createVersionOnActivation` (Boolescher Wert, Standard: true) Gibt an, ob beim Aktivieren von Seiten eine Version erstellt werden soll.
Eine Version wird erstellt, es sei denn, der Replikationsagent ist so konfiguriert, dass er die Erstellung von Versionen unterdrückt, was vom Versions-Manager berücksichtigt wird.
Eine Version wird nur erstellt, wenn die Aktivierung auf einem Pfad erfolgt, der in `versionmanager.ivPaths` enthalten ist (siehe unten).

* `versionmanager.ivPaths`(Zeichenfolge[], Standard:  `{"/"}`) Gibt die Pfade an, auf denen Versionen implizit bei der Aktivierung erstellt werden, wenn  `versionmanager.createVersionOnActivation` sie auf &quot;true&quot;gesetzt sind.

* `versionmanager.purgingEnabled` (Boolescher Wert, Standard: false) Definiert, ob das Bereinigen aktiviert werden soll, wenn neue Versionen erstellt werden.

* `versionmanager.purgePaths` (Zeichenfolge[], Standard: {&quot;/content&quot;}) Gibt an, welche Pfade zum Bereinigen von Versionen beim Erstellen neuer Versionen verwendet werden.

* `versionmanager.maxAgeDays` (int, Standard: 30) Beim Bereinigen der Version werden alle älteren Versionen als der konfigurierte Wert entfernt. Wenn der Wert kleiner als 1 ist, wird das Bereinigen nicht basierend auf dem Alter der Version durchgeführt.

* `versionmanager.maxNumberVersions` (int, Standard 5) Beim Bereinigen der Version werden alle älteren Versionen als die n. neueste Version entfernt. Wenn der Wert kleiner als 1 ist, wird das Bereinigen nicht basierend auf der Anzahl der Versionen durchgeführt.

* `versionmanager.minNumberVersions` (int, default 0) Die Mindestanzahl Versionen, die unabhängig vom Alter beibehalten werden. Wenn hier ein Wert kleiner als 1 festgelegt wird, wird keine Mindestanzahl an Versionen beibehalten.

>[!NOTE]
>
>Es wird nicht empfohlen, eine große Anzahl von Versionen im Repository zu halten. Achten Sie also bei der Konfiguration des Versions-Bereinigungsvorgangs darauf, nicht zu viele Versionen von der Bereinigung auszuschließen, da sonst die Größe des Repositorys nicht richtig optimiert wird. Wenn Sie aufgrund von Geschäftsanforderungen eine große Anzahl von Versionen haben, wenden Sie sich bitte an den Support der Adobe, um alternative Möglichkeiten zur Optimierung der Repository-Größe zu finden.

### Kombinieren von Aufbewahrungsoptionen {#combining-retention-options}

Die Optionen, mit denen festgelegt wird, welche Versionen beibehalten werden sollen ( `maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), können je nach Ihren Anforderungen kombiniert werden.

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
