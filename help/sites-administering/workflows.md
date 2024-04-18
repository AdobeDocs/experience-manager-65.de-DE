---
title: Verwalten von Workflows
description: Erfahren Sie, wie Sie Aktivitäten in Adobe Experience Manager mithilfe von Workflows automatisieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 10eecfb8-d43d-4f01-9778-87c752dee64c
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 100%

---

# Verwalten von Workflows{#administering-workflows}

Workflows ermöglichen die Automatisierung von Adobe Experience Manager (AEM)-Aktivitäten. Workflows:

* Bestehen aus einer Reihe von Schritten, die in einer bestimmten Reihenfolge ausgeführt werden.

   * Durch jeden Schritt wird eine bestimmte Aktivität durchgeführt – so zum Beispiel das Warten auf Benutzereingaben, das Aktivieren einer Seite oder das Senden einer E-Mail-Nachricht.

* Können mit Assets im Repository, Benutzerkonten und AEM-Diensten interagieren.
* Können komplizierte Aktivitäten koordinieren, die jeden Aspekt von AEM umfassen.

Die von Ihrer Organisation etablierten Geschäftsprozesse können als Workflows dargestellt werden. Beispielsweise umfasst der Prozess der Veröffentlichung von Website-Inhalten in der Regel Schritte wie die Genehmigung und die Abnahme durch verschiedene Stakeholder. Diese Prozesse können als AEM Workflows implementiert und auf Content-Seiten und Assets angewendet werden.

* [Starten von Workflows](/help/sites-administering/workflows-starting.md)
* [Verwalten der Workflow-Instanzen](/help/sites-administering/workflows-administering.md)
* [Verwalten des Zugriffs auf Workflows](/help/sites-administering/workflows-managing.md)

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* Anwenden von und Teilnehmen an Workflows: [Arbeiten mit Workflows](/help/sites-authoring/workflows.md).
>* Das Erstellen von Workflow-Modellen und die Erweiterung der Workflow-Funktionalität: [Entwickeln und Erweitern von Workflows](/help/sites-developing/workflows.md).
>* Verbesserung der Leistung von Workflows, die bedeutende Server-Ressourcen nutzen: [Gleichzeitige Verarbeitung von Workflows](/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing).
>

## Workflow-Modelle und -Instanzen {#workflow-models-and-instances}

[Workflow-Modelle](/help/sites-developing/workflows.md#model) in AEM sind die Darstellung und Implementierung von Geschäftsprozessen:

* In der Regel bewirken sie auf Seiten und in Assets bestimmte Ergebnisse.
* Diese Seiten und/oder Assets werden als Workflow-Payload bezeichnet.
* Workflow-Modelle bestehen aus einer Reihe von Schritten zur Durchführung einer bestimmten Aufgabe.
* Die Payload wird von Schritt zu Schritt weitergegeben, während der Workflow fortschreitet.

Wenn ein Workflow-Modell gestartet (ausgeführt) wird, wird eine Workflow-Instanz erstellt. Ein Workflow-Modell kann mehrere Male gestartet werden, wobei es jedes Mal eine eigene Workflow-Instanz generiert. Für jede Instanz werden die Schritte ausgeführt, die das Workflow-Modell festlegt.

>[!CAUTION]
>
>Die ausgeführten Schritte sind diejenigen, die vom Workflow-Modell *zum Zeitpunkt der Generierung der Instanz* festgelegt wurden. Unter [Entwickeln von Workflows](/help/sites-developing/workflows.md#model) finden Sie weitere Details.

Workflow-Instanzen schreiten durch den folgenden Lebenszyklus voran:

1. Das Workflow-Modell wird gestartet und eine Workflow-Instanz wird erstellt und ausgeführt.

   1. Die Payload der Workflow-Instanz wird identifiziert, wenn das Modell gestartet wird.
   1. Die Instanz ist effektiv eine Kopie des Modells (zum Zeitpunkt der Erstellung).
   1. AEM-Autorinnen und -Autoren, -Admins oder -Dienste können Workflow-Modelle starten.

1. Der erste Schritt des Workflow-Modells wird ausgeführt.
1. Der Schritt wird abgeschlossen und die Workflow-Engine verwendet das Modell, um den nächsten auszuführenden Schritt zu bestimmen.
1. Die nachfolgenden Schritte des Workflow-Modells werden ausgeführt und abgeschlossen.
1. Wenn der letzte Schritt abgeschlossen ist, wird auch die Workflow-Instanz abgeschlossen und damit archiviert.

Mit AEM werden viele nützliche Workflow-Modelle bereitgestellt.  Zusätzlich können die Entwickelnden in Ihrer Organisation benutzerdefinierte Workflow-Modelle erstellen, die auf die spezifischen Anforderungen Ihrer Geschäftsprozesse zugeschnitten sind.

## Workflow-Schritte {#workflow-steps}

Wenn Workflow-Schritte ausgeführt werden, werden sie mit einer Workflow-Instanz verknüpft. Der Verlauf einer Workflow-Instanz beinhaltet Informationen zu jedem für die Instanz ausgeführten Schritt. Diese Informationen sind nützlich für die Untersuchung von Problemen, die während der Ausführung auftreten.

Workflow-Schritte werden je nach Art des jeweiligen Schritts entweder von einer Person oder einem Dienst ausgeführt:

* Wenn eine Person einen Schritt ausführt, wird ihr ein Arbeitselement zugewiesen, das in ihrem Posteingang platziert wird. Die Person ist dafür zuständig, den Schritt manuell durchzuführen, sodass die Workflow-Instanz voranschreitet.
* Wenn ein Dienst einen Schritt ausführt, schreitet die Workflow-Instanz nach Fertigstellung mit dem nächsten Schritt voran.

>[!NOTE]
>
>Wenn ein Fehler auftritt, sollte die Implementierung des Dienstes/Schritts das Verhalten bei einem Fehlerszenario handhaben. Die Workflow-Engine selbst wiederholt die Ausführung des Auftrags, protokolliert dann einen Fehler und hält die Instanz an.

## Workflow-Status und -Aktionen {#workflow-status-and-actions}

Ein Workflow kann einen der folgenden Status aufweisen:

* **WIRD AUSGEFÜHRT**: Die Workflow-Instanz wird ausgeführt.
* **ABGESCHLOSSEN**: Die Workflow-Instanz wurde erfolgreich beendet.

* **AUSGESETZT**: Markiert den Workflow als ausgesetzt. Beachten Sie jedoch den unten stehenden Warnhinweis zu einem bekannten Fehler mit diesem Status.
* **ABGEBROCHEN**: Die Workflow-Instanz wurde beendet.
* **VERALTET**: Für die Fortführung der Workflow-Instanz muss ein Hintergrundauftrag ausgeführt werden, dieser Auftrag ist jedoch nicht im System zu finden. Dies kann passieren, wenn beim Ausführen des Workflows ein Fehler auftritt.

>[!NOTE]
>
>Wenn die Ausführung eines Prozessschritts zu einem Fehler führt, wird der Schritt im Posteingang der bzw. des Admins angezeigt und der Workflow-Status lautet **WIRD AUSGEFÜHRT**.

Je nach Status können Sie Aktionen zur Ausführung von Workflow-Instanzen durchführen, wenn Sie beim normalen Fortschritt einer Workflow-Instanz eingreifen müssen:

* **Aussetzen**: Durch das Aussetzen ändert sich der Workflow-Status zu „Ausgesetzt“. Siehe den Warnhinweis unten:

>[!CAUTION]
>
>Das Markieren eines Workflow-Status mit „Aussetzen“ hat ein bekanntes Problem. In diesem Status ist es möglich, Aktionen für ausgesetzte Workflow-Elemente in einem Posteingang durchzuführen.

* **Fortsetzen**: Startet einen ausgesetzten Workflow an der Stelle der Ausführung neu, an der er unterbrochen wurde – und zwar mit derselben Konfiguration.
* **Beenden**: Beendet die Workflow-Ausführung und ändert den Status in **ABGEBROCHEN**. Eine abgebrochene Workflow-Instanz kann nicht neu gestartet werden.
