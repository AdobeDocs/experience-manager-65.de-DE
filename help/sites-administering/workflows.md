---
title: Verwalten von Workflows
description: Erfahren Sie, wie Sie Adobe Experience Manager-Aktivitäten mithilfe von Workflows automatisieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 10eecfb8-d43d-4f01-9778-87c752dee64c
source-git-commit: 06a6d4e0ba2aeaefcfb238233dd98e8bbd6731da
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 28%

---

# Verwalten von Workflows{#administering-workflows}

Workflows ermöglichen die Automatisierung von Adobe Experience Manager (AEM)-Aktivitäten. Workflows:

* besteht aus einer Reihe von Schritten, die in einer bestimmten Reihenfolge ausgeführt werden.

   * Jeder Schritt führt eine bestimmte Aktivität aus, z. B. das Warten auf Benutzereingaben, das Aktivieren einer Seite oder das Senden einer E-Mail-Nachricht.

* Kann mit Assets im Repository, mit Benutzerkonten und mit AEM-Diensten interagieren.
* Können komplizierte Aktivitäten koordinieren, die jeden Aspekt von AEM umfassen.

Die von Ihrer Organisation eingerichteten Geschäftsprozesse können als Workflows dargestellt werden. Beispielsweise umfasst der Prozess der Veröffentlichung von Website-Inhalten in der Regel Schritte wie die Genehmigung und die Abnahme durch verschiedene Stakeholder. Diese Prozesse können als AEM Workflows implementiert und auf Inhaltsseiten und Assets angewendet werden.

* [Starten von Workflows](/help/sites-administering/workflows-starting.md)
* [Verwalten der Workflow-Instanzen](/help/sites-administering/workflows-administering.md)
* [Verwalten des Zugriffs auf Workflows](/help/sites-administering/workflows-managing.md)

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* Anwenden von und Teilnehmen an Workflows: [Arbeiten mit Workflows](/help/sites-authoring/workflows.md).
>* Das Erstellen von Workflow-Modellen und die Erweiterung der Workflow-Funktionalität: [Entwickeln und Erweitern von Workflows](/help/sites-developing/workflows.md).
>* Verbesserung der Leistung von Workflows, die umfangreiche Serverressourcen nutzen: [Gleichzeitige Workflow-Verarbeitung](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing).
>

## Workflow-Modelle und -Instanzen {#workflow-models-and-instances}

[Workflow-Modelle](/help/sites-developing/workflows.md#model) in AEM sind die Darstellung und Implementierung von Geschäftsprozessen:

* Normalerweise werden sie auf Seiten oder Assets angewendet, um ein bestimmtes Ergebnis zu erzielen.
* Diese Seiten und/oder Assets werden als Workflow-Payload bezeichnet.
* Workflow-Modelle bestehen aus einer Reihe von Schritten zur Durchführung einer bestimmten Aufgabe.
* Die Payload wird bei der weiteren Ausführung des Workflows von Schritt zu Schritt übergeben.

Wenn ein Workflow-Modell gestartet (ausgeführt) wird, wird eine Workflow-Instanz erstellt. Ein Workflow-Modell kann mehrmals gestartet werden, wobei jedes Mal eine spezifische Workflow-Instanz generiert wird. Die vom Workflow-Modell definierten Schritte werden für jede Instanz ausgeführt.

>[!CAUTION]
>
>Die durchgeführten Schritte werden durch das Workflow-Modell definiert *zum Zeitpunkt der Instanzgenerierung*. Unter [Entwickeln von Workflows](/help/sites-developing/workflows.md#model) finden Sie weitere Details.

Workflow-Instanzen schreiten durch den folgenden Lebenszyklus voran:

1. Das Workflow-Modell wird gestartet und eine Workflow-Instanz wird erstellt und ausgeführt.

   1. Die Payload der Workflow-Instanz wird identifiziert, wenn das Modell gestartet wird.
   1. Die Instanz ist im Grunde eine Kopie des Modells (wie zum Zeitpunkt der Erstellung).
   1. AEM Autoren, Administratoren oder Dienste können Workflow-Modelle starten.

1. Der erste Schritt des Workflow-Modells wird ausgeführt.
1. Der Schritt ist abgeschlossen und die Workflow-Engine verwendet das Modell, um den nächsten auszuführenden Schritt zu bestimmen.
1. Die nachfolgenden Schritte im Workflow-Modell werden ausgeführt und abgeschlossen.
1. Wenn der letzte Schritt abgeschlossen ist, wird die Workflow-Instanz abgeschlossen und somit archiviert.

Viele nützliche Workflow-Modelle werden mit AEM bereitgestellt. Darüber hinaus können die Entwickler in Ihrem Unternehmen benutzerdefinierte Workflow-Modelle erstellen, die auf die spezifischen Anforderungen Ihrer Geschäftsprozesse zugeschnitten sind.

## Workflow-Schritte {#workflow-steps}

Wenn Workflow-Schritte ausgeführt werden, sind sie mit einer Workflow-Instanz verknüpft. Der Verlauf einer Workflow-Instanz enthält Informationen zu jedem Schritt, der für die Instanz ausgeführt wurde. Diese Informationen sind hilfreich, um Probleme zu untersuchen, die während der Ausführung auftreten.

Ein Benutzer oder ein Dienst führt je nach Typ des Schritts Workflow-Schritte durch:

* Wenn ein Benutzer einen Schritt ausführt, wird ihm ein Arbeitselement zugewiesen, das in seinem Posteingang platziert wird. Der Benutzer ist dafür verantwortlich, den Schritt manuell abzuschließen, damit die Workflow-Instanz fortgesetzt wird.
* Wenn ein Dienst einen Schritt ausführt, geht die Workflow-Instanz nach Abschluss automatisch zum nächsten Schritt über.

>[!NOTE]
>
>Wenn ein Fehler auftritt, sollte die Implementierung des Dienstes/Schritts das Verhalten für ein Fehlerszenario handhaben. Die Workflow-Engine versucht den Auftrag selbst erneut, protokolliert dann einen Fehler und stoppt die Instanz.

## Workflow-Status und -Aktionen {#workflow-status-and-actions}

Ein Workflow kann einen der folgenden Status aufweisen:

* **WIRD AUSGEFÜHRT**: Die Workflow-Instanz wird ausgeführt.
* **ABGESCHLOSSEN**: Die Workflow-Instanz wurde erfolgreich beendet.

* **AUSGESETZT**: Markiert den Workflow als ausgesetzt. Beachten Sie jedoch den unten stehenden Hinweis zu einem bekannten Problem mit diesem Status.
* **ABORTED**: Die Workflow-Instanz wurde beendet.
* **STÄNDIG**: Für die Fortführung der Workflow-Instanz muss ein Hintergrundauftrag ausgeführt werden, der Auftrag kann jedoch nicht im System gefunden werden. Diese Situation kann auftreten, wenn beim Ausführen des Workflows ein Fehler auftritt.

>[!NOTE]
>
>Wenn die Ausführung eines Prozessschritts zu einem Fehler führt, wird der Schritt im Posteingang der bzw. des Admins angezeigt und der Workflow-Status lautet **WIRD AUSGEFÜHRT**.

Je nach Status können Sie Aktionen für laufende Workflow-Instanzen durchführen, wenn Sie in den normalen Fortschritt einer Workflow-Instanz eingreifen müssen:

* **Aussetzen**: Durch das Aussetzen ändert sich der Workflow-Status zu „Ausgesetzt“. Siehe den Warnhinweis unten:

>[!CAUTION]
>
>Das Markieren eines Workflow-Status mit „Aussetzen“ hat ein bekanntes Problem. In diesem Status können in einem Posteingang ausgesetzte Workflow-Elemente bearbeitet werden.

* **Fortsetzen**: Startet einen ausgesetzten Workflow an der Stelle der Ausführung neu, an der er unterbrochen wurde – und zwar mit derselben Konfiguration.
* **Beenden**: Beendet die Workflow-Ausführung und ändert den Status in **ABGEBROCHEN**. Eine abgebrochene Workflow-Instanz kann nicht neu gestartet werden.
