---
title: Einführung in Process Berichte
seo-title: Einführung in Process Berichte
description: Einführung und Schlüsselfunktionen von AEM Forms on JEE Process Berichte
seo-description: Einführung und Schlüsselfunktionen von AEM Forms on JEE Process Berichte
uuid: a7f2455b-1b09-41a7-817b-e2e7a1ff9936
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4e83ed7b-3f48-4bf6-be4c-89f79949c1df
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# Einführung in Process Berichte{#introduction-to-process-reporting}

![process-Berichte](assets/process-reporting.png)

Process Berichte ist ein browserbasiertes Tool, das Sie zum Erstellen und Ansicht von Berichten zu AEM Forms-Prozessen und -Aufgaben verwenden.

Process Berichte bietet eine Reihe vordefinierter Berichte, die Ihnen das Filtern, Informationen zur Ansicht von Prozessen mit langer Laufzeit, zur Prozessdauer und zum Workflow-Volumen ermöglichen.

Darüber hinaus stellt Process Berichte eine Schnittstelle zum Ausführen von Ad-hoc-Abfragen und zum Integrieren benutzerdefinierter Report-Ansichten in die Process Berichte-Benutzeroberfläche bereit.

Die Liste der unterstützten Browser finden Sie unter [AEM Forms Unterstützte Plattformen](/help/forms/using/aem-forms-jee-supported-platforms.md).

Process Berichte basiert auf Modulen, die:

* Prozessdaten aus der AEM Forms-Datenbank lesen
* Prozessdaten in einem eingebetteten Process Berichte-Repository veröffentlichen
* Stellt eine browserbasierte Benutzeroberfläche für Berichte zur Ansicht bereit

## Schlüsselfunktionen {#key-capabilities}

### Immer aktivierter Berichte {#always-on-reporting}

![site-management](assets/site-management.png)

Ansicht der Liste von Prozessen mit langer Laufzeit, Diagrammen zur Prozessdauer und Ausführung benutzerdefinierter Abfragen mithilfe von Filtern.

Process Berichte bietet außerdem die Möglichkeit, die Bericht- und Abfrage-Daten im CSV-Format zu exportieren.

### Ad-hoc-Berichte {#adhoc-reports}

![print-&amp;-color](assets/print-&-colour.png)

Verwenden Sie Filter, um eine bestimmte Ansicht Ihrer Daten zu erhalten.

Sie können Prozesse oder Aufgaben nach ID, Dauer, Beginns- und Enddatum, Prozessinitiator usw. suchen.

Sie können mehrere Filter kombinieren, um spezifische Berichte zu erstellen.

Anschließend können Sie die Filter speichern, die zu einem späteren Zeitpunkt ausgeführt werden sollen.

### Prozess-/Aufgaben-Verlauf {#process-task-history}

![Dateiverwaltung](assets/file-management.png)

AEM Forms-Server führen zahlreiche Prozesse parallel aus. Diese Prozesse wechseln weiter von einem Status in einen anderen. Durch die regelmäßige Veröffentlichung von Forms-Daten im Process Berichte-Repository behält Process Berichte die Übergangsinformationen zu den in AEM Forms ausgeführten Prozessen bei.

### Zugriffssteuerung {#access-control-br}

![unbenannt](assets/untitled.png)

Prozessberichte bieten berechtigungsbasierten Zugriff auf die Benutzeroberfläche.

Dies bedeutet, dass nur Benutzer mit Berichte-Berechtigungen Zugriff auf die Benutzeroberfläche von Process Berichte haben.
