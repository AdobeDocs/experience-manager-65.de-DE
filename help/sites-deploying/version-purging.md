---
title: Versionsbereinigung
description: In diesem Artikel werden die verfügbaren Optionen für die Versionsbereinigung beschrieben.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
exl-id: 6f0b1951-bdda-475f-b6c0-bc18de082b7c
source-git-commit: 4e2ee7da5424ac6677eaa2392de7803e7543d13c
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 42%

---

# Versionsbereinigung{#version-purging}

In einer Standardinstallation erstellt Adobe Experience Manager (AEM) eine Version einer Seite oder eines Knotens, wenn Sie eine Seite aktivieren, nachdem der Inhalt aktualisiert wurde.

>[!NOTE]
>
>Wenn keine Inhaltsänderungen vorgenommen werden, wird die Meldung angezeigt, dass die Seite aktiviert wurde, aber keine neue Version erstellt wurde.

Mit der Registerkarte **Versionierung** des Sidekicks können Sie auf Anforderung zusätzliche Versionen erstellen. Diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie gelöscht, sodass die Repository-Größe im Laufe der Zeit zunimmt und daher verwaltet werden muss.

AEM wird mit verschiedenen Mechanismen geliefert, mit denen Sie Ihr Repository verwalten können:

* [Versionsmanager](#version-manager) Der Manager kann so konfiguriert werden, dass alte Versionen bei der Erstellung von neuen Versionen entfernt werden.

* das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) Dieses Tool wird im Rahmen der Überwachung und Wartung Ihres Repositorys verwendet.
Es ermöglicht Ihnen, gemäß den folgenden Parametern alte Versionen eines Knotens oder eine Hierarchie von Knoten zu entfernen:

   * Die maximale Anzahl der Versionen, die im Repository gespeichert werden sollen.
Wird dieser Wert überschritten, wird die älteste Version entfernt.

   * Das Höchstalter einer im Repository gespeicherten Version.
Wenn das Alter einer Version diesen Wert überschreitet, wird sie aus dem Repository gelöscht.

* [Wartungsaufgabe zur Versionsbereinigung](/help/sites-administering/operations-dashboard.md#automated-maintenance-tasks). Sie können die Wartungsaufgabe zur Versionsbereinigung planen, um alte Versionen automatisch zu löschen. Das verringert die Notwendigkeit, die Tools zur Versionsbereinigung manuell zu verwenden.

>[!CAUTION]
>
>Um die Repository-Größe zu optimieren, führen Sie die Versionsbereinigungsaufgabe häufig aus. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn nur ein begrenzter Traffic vorhanden ist.

## Version Manager {#version-manager}

Zusätzlich zur expliziten Bereinigung mithilfe des Bereinigungs-Tools kann der Versionsmanager so konfiguriert werden, dass alte Versionen bei der Erstellung neuer Versionen bereinigt werden.

Um den Versions-Manager entsprechend zu konfigurieren, [erstellen Sie eine Konfiguration](/help/sites-deploying/configuring-osgi.md) für:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Die folgenden Optionen sind verfügbar:

* `versionmanager.createVersionOnActivation` (Boolesch, Standardeinstellung: true)
Legt fest, ob bei der Aktivierung von Seiten eine Version erstellt werden soll.
Eine Version wird erstellt, es sei denn, der Replikationsagent ist so konfiguriert, dass die Erstellung von Versionen unterdrückt wird, was vom Versionsmanager berücksichtigt wird.
Eine Version wird erstellt, wenn die Aktivierung auf einem Pfad passiert, der in `versionmanager.ivPaths` enthalten ist (siehe unten).

* `versionmanager.ivPaths`(Zeichenfolge[], Standardeinstellung: `{"/"}`)
Gibt den Pfad an, über den Versionen bei einer Aktivierung implizit erstellt werden, wenn die Einstellung für `versionmanager.createVersionOnActivation` auf „true“ gesetzt ist.

* `versionmanager.purgingEnabled` (Boolesch, Standard: false) Definiert, ob die Bereinigung aktiviert werden soll, wenn neue Versionen erstellt werden.

* `versionmanager.purgePaths` (Zeichenfolge[], Standardeinstellung: {&quot;/content&quot;})
Gibt an, auf welchen Pfaden Versionen gelöscht werden sollen, wenn neue Versionen erstellt werden.

* `versionmanager.maxAgeDays` (int, Standard: 30) Bei der Versionsbereinigung werden alle Versionen entfernt, die älter als der konfigurierte Wert sind. Wenn der Wert kleiner als 1 ist, wird die Bereinigung nicht basierend auf dem Alter der Version durchgeführt.

* `versionmanager.maxNumberVersions` (int, Standard 5) Bei der Versionsbereinigung werden alle Versionen entfernt, die älter als die n. neueste Version sind. Ist der Wert kleiner als „1“, wird die Bereinigung nicht auf Basis der Anzahl der Versionen durchgeführt.

* `versionmanager.minNumberVersions` (int, Standard 0) Die Mindestanzahl von Versionen, die unabhängig vom Alter beibehalten werden. Wenn der Wert auf einen Wert kleiner 1 gesetzt ist, wird keine Mindestanzahl von Versionen beibehalten.

>[!NOTE]
>
>Es wird nicht empfohlen, viele Versionen im Repository zu behalten. Achten Sie daher bei der Konfiguration des Versionsbereinigungsvorgangs darauf, nicht zu viele Versionen aus der Bereinigung auszuschließen, da ansonsten die Repository-Größe nicht ordnungsgemäß optimiert ist. Wenn Sie aufgrund geschäftlicher Anforderungen eine große Anzahl von Versionen aufbewahren, wenden Sie sich an den Adobe-Support, um alternative Möglichkeiten zur Optimierung der Repository-Größe zu finden.

### Kombinieren von Aufbewahrungsoptionen {#combining-retention-options}

Die Optionen, mit denen definiert wird, welche Versionen aufbewahrt werden sollen (`maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), können gemäß Ihren Anforderungen kombiniert werden.

Beispielsweise bei der Definition der maximalen Anzahl von Versionen, die beibehalten werden sollen, UND der ältesten Version, die beibehalten werden soll:

* Einstellung:

   * `maxNumberVersions` = 7

   * `maxAgeDays` = 30

* Mit:

   * Zehn Versionen wurden innerhalb der letzten 60 Tage erstellt
   * Drei dieser Versionen wurden innerhalb der letzten 30 Tage erstellt

* Das bedeutet:

   * Die letzten drei Versionen werden beibehalten

Beispielsweise bei der Definition der maximalen UND minimalen Anzahl von Versionen, die beibehalten werden sollen, UND der ältesten Version, die beibehalten werden soll:

* Einstellung:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Mit:

   * Fünf Versionen wurden vor 60 Tagen erstellt

* Das bedeutet:

   * Drei Versionen werden beibehalten

## Versionsbereinigungs-Tool {#purge-versions-tool}

Das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) dient zum Bereinigen der Versionen eines Knotens oder einer Hierarchie von Knoten in Ihrem Repository. Der Hauptzweck ist die Verkleinerung des Repositorys durch Löschen alter Knotenversionen.
