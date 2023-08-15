---
title: Versionsbereinigung
seo-title: Version Purging
description: In diesem Artikel werden die verfügbaren Optionen für die Versionsbereinigung beschrieben.
seo-description: This article describes the available options for version purging.
uuid: a9fa25c7-e60e-4665-a726-99af9aac8f70
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: fb4d7337-7b94-430b-80d2-f1754f823c2b
docset: aem65
feature: Configuring
exl-id: 6f0b1951-bdda-475f-b6c0-bc18de082b7c
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 66%

---

# Versionsbereinigung{#version-purging}

In einer Standardinstallation erstellt AEM eine neue Version einer Seite oder eines Knotens, wenn Sie eine Seite nach der Aktualisierung des Inhalts aktivieren.

>[!NOTE]
>
>Wenn keine Inhaltsänderungen vorgenommen werden, wird die Meldung angezeigt, dass die Seite aktiviert wurde, aber keine neue Version erstellt wird

Mit der Registerkarte **Versionierung** des Sidekicks können Sie auf Anforderung zusätzliche Versionen erstellen. Diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie gelöscht, sodass die Repository-Größe mit der Zeit zunimmt und daher verwaltet werden muss.

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
>Um die Größe des Repositorys zu optimieren, sollten Sie die Aufgabe zur Versionsbereinigung regelmäßig ausführen. Die Aufgabe sollte außerhalb der Geschäftszeiten geplant werden, wenn nur ein begrenzter Traffic vorhanden ist.

## Version Manager {#version-manager}

Zusätzlich zur expliziten Bereinigung mithilfe des Bereinigungs-Tools kann der Versionsmanager so konfiguriert werden, dass alte Versionen bei der Erstellung neuer Versionen bereinigt werden.

Um den Versions-Manager entsprechend zu konfigurieren, [erstellen Sie eine Konfiguration](/help/sites-deploying/configuring-osgi.md) für:

`PID com.day.cq.wcm.core.impl.VersionManagerImpl`

Die folgenden Optionen sind verfügbar:

* `versionmanager.createVersionOnActivation` (Boolesch, Standardeinstellung: true)
Legt fest, ob bei der Aktivierung von Seiten eine Version erstellt werden soll.
Eine Version wird erstellt, es sei denn, der Replikationsagent ist so konfiguriert, dass er die Erstellung von Versionen unterdrückt, was vom Versions-Manager berücksichtigt wird.
Eine Version wird erstellt, wenn die Aktivierung auf einem Pfad passiert, der in `versionmanager.ivPaths` enthalten ist (siehe unten).

* `versionmanager.ivPaths`(Zeichenfolge[], Standardeinstellung: `{"/"}`)
Gibt den Pfad an, über den Versionen bei einer Aktivierung implizit erstellt werden, wenn die Einstellung für `versionmanager.createVersionOnActivation` auf „true“ gesetzt ist.

* `versionmanager.purgingEnabled` (Boolesch, Standardeinstellung: false)
Legt fest, ob die Bereinigung bei der Erstellung von neuen Versionen aktiviert werden soll.

* `versionmanager.purgePaths` (Zeichenfolge[], Standardeinstellung: {&quot;/content&quot;})
Gibt an, auf welchen Pfaden Versionen gelöscht werden sollen, wenn neue Versionen erstellt werden.

* `versionmanager.maxAgeDays` (int, Standardeinstellung: 30)
Legt fest, dass beim Bereinigen alle Versionen entfernt werden, die älter als dieser Wert sind. Ist der Wert kleiner als „1“, wird die Bereinigung nicht auf Basis des Alters der Version durchgeführt.

* `versionmanager.maxNumberVersions` (int, Standardeinstellung: 5)
Legt fest, dass beim Bereinigen alle Versionen entfernt werden, die älter als die n-te neue Version sind. Ist der Wert kleiner als „1“, wird die Bereinigung nicht auf Basis der Anzahl der Versionen durchgeführt.

* `versionmanager.minNumberVersions` (int, Standardeinstellung: 0)
Die Mindestanzahl der Versionen, die unabhängig vom Alter beibehalten werden. Wenn der Wert auf einen Wert kleiner als 1 gesetzt ist, wird keine Mindestanzahl von Versionen beibehalten.

>[!NOTE]
>
>Es wird nicht empfohlen, eine große Anzahl von Versionen im Repository zu halten. Achten Sie also bei der Konfiguration des Versions-Bereinigungsvorgangs darauf, nicht zu viele Versionen von der Bereinigung auszuschließen, da sonst die Größe des Repositorys nicht richtig optimiert wird. Wenn Sie aus geschäftlichen Gründen eine große Anzahl von Versionen haben, wenden Sie sich an den Adobe-Support, um alternative Möglichkeiten zur Optimierung der Repository-Größe zu finden.

### Kombinieren von Aufbewahrungsoptionen {#combining-retention-options}

Die Optionen, mit denen definiert wird, welche Versionen aufbewahrt werden sollen (`maxAgeDays`, `maxNumberVersions`, `minNumberVersions`), können gemäß Ihren Anforderungen kombiniert werden.

Beispielsweise bei der Definition der maximalen Anzahl von Versionen, die beibehalten werden sollen, UND der ältesten Version, die beibehalten werden soll:

* Einstellung:

   * `maxNumberVersions` = 7

   * `maxAgeDays` = 30

* Mit:

   * 10 Versionen, die in den letzten 60 Tagen erstellt wurden
   * 3 dieser Versionen, die innerhalb der letzten 30 Tage erstellt wurden

* bedeutet Folgendes:

   * Die letzten drei Versionen werden beibehalten

Beispielsweise bei der Definition der maximalen UND minimalen Anzahl von Versionen, die beibehalten werden sollen, UND der ältesten Version, die beibehalten werden soll:

* Einstellung:

   * `maxNumberVersions` = 3
   * `maxAgeDays` = 30
   * `minNumberVersions` = 3

* Mit:

   * 5 Versionen vor 60 Tagen

* bedeutet Folgendes:

   * 3 Versionen werden beibehalten

## Versionsbereinigungs-Tool {#purge-versions-tool}

Das Tool [Versionen bereinigen](/help/sites-deploying/monitoring-and-maintaining.md#purgeversionstool) dient zum Bereinigen der Versionen eines Knotens oder einer Hierarchie von Knoten in Ihrem Repository. Der Hauptzweck ist die Verkleinerung des Repositorys durch Löschen alter Knotenversionen.
