---
title: Einführung in die Prozessberichterstellung
seo-title: Einführung in die Prozessberichterstellung
description: Einführung und wichtige Funktionen von AEM Forms on JEE Process Reporting
seo-description: Einführung und wichtige Funktionen von AEM Forms on JEE Process Reporting
uuid: a7f2455b-1b09-41a7-817b-e2e7a1ff9936
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4e83ed7b-3f48-4bf6-be4c-89f79949c1df
docset: aem65
exl-id: 674d28dc-7353-49de-9e12-b1998e1509c7
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Einführung in die Prozessberichterstellung{#introduction-to-process-reporting}

![Process-Reporting](assets/process-reporting.png)

Process Reporting ist ein browserbasiertes Tool, mit dem Sie Berichte zu AEM Forms-Prozessen und -Aufgaben erstellen und anzeigen können.

Die Prozessberichterstellung bietet eine Reihe vordefinierter Berichte, mit denen Sie Informationen zu langwierigen Prozessen, Prozessdauer und Workflow-Volumen filtern und anzeigen können.

Darüber hinaus bietet Process Reporting eine Oberfläche zum Ausführen von Ad-hoc-Abfragen und zum Integrieren benutzerdefinierter Berichtsansichten in die Benutzeroberfläche für Process Reporting.

Eine Liste der unterstützten Browser finden Sie unter [Unterstützte Plattformen für AEM Forms](/help/forms/using/aem-forms-jee-supported-platforms.md).

Prozessberichte basieren auf Modulen, die:

* Prozessdaten aus der AEM Forms-Datenbank lesen
* Veröffentlichen von Prozessdaten in einem eingebetteten Process Reporting-Repository
* Bietet eine browserbasierte Benutzeroberfläche zum Anzeigen von Berichten

## Schlüsselfunktionen {#key-capabilities}

### Always-on Reporting {#always-on-reporting}

![Site-Management](assets/site-management.png)

Zeigen Sie die Liste der Prozesse mit langer Laufzeit an, erstellen Sie Diagramme zur Prozessdauer und führen Sie benutzerdefinierte Abfragen mithilfe von Filtern aus.

Die Prozessberichterstellung bietet außerdem die Möglichkeit, die Berichts- und Abfragedaten im CSV-Format zu exportieren.

### Adhoc-Berichte {#adhoc-reports}

![print-&amp;-color](assets/print-&-colour.png)

Verwenden Sie Filter, um eine bestimmte Ansicht Ihrer Daten zu erhalten.

Sie können Prozesse oder Aufgaben nach ID, Dauer, Start- und Enddatum, Prozessinitiator usw. suchen.

Sie können mehrere Filter kombinieren, um bestimmte Berichte zu erstellen.

Anschließend können Sie die Berichtsfilter speichern, um sie zu einem späteren Zeitpunkt auszuführen.

### Prozess-/Aufgabenverlauf {#process-task-history}

![Dateiverwaltung](assets/file-management.png)

AEM Forms-Server führen zahlreiche Prozesse parallel aus. Diese Prozesse verändern sich weiter von einem Status zum nächsten. Durch die regelmäßige Veröffentlichung von Forms-Daten in das Process Reporting-Repository werden die Übergangsinformationen zu den in AEM Forms ausgeführten Prozessen in Process Reporting beibehalten.

### Zugriffssteuerung {#access-control-br}

![untitled](assets/untitled.png)

Prozessberichte bieten berechtigungsbasierten Zugriff auf die Benutzeroberfläche.

Dies bedeutet, dass nur Benutzer mit Berichterstellungsberechtigungen Zugriff auf die Benutzeroberfläche &quot;Process Reporting&quot;haben.
