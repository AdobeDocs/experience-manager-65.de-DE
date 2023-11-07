---
title: Einführung in das Prozess-Reporting
seo-title: Introduction to Process Reporting
description: Einführung und Schlüsselfunktionen von Process Reporting mit AEM Forms auf JEE
seo-description: Introduction and key capabilities of AEM Forms on JEE Process Reporting
uuid: a7f2455b-1b09-41a7-817b-e2e7a1ff9936
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4e83ed7b-3f48-4bf6-be4c-89f79949c1df
docset: aem65
exl-id: 674d28dc-7353-49de-9e12-b1998e1509c7
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 86%

---

# Einführung in das Prozess-Reporting{#introduction-to-process-reporting}

![process-reporting](assets/process-reporting.png)

Process Reporting ist ein Browser-basiertes Tool, mit dem Sie Berichte zu AEM Forms-Prozessen und -Aufgaben erstellen und anzeigen können.

Die Prozessberichterstellung bietet eine Reihe vordefinierter Berichte, mit denen Sie Informationen zu langwierigen Prozessen, Prozessdauer und Workflow-Volumen filtern und anzeigen können.

Darüber hinaus bietet Process Reporting eine Oberfläche zum Ausführen von Ad-hoc-Abfragen und zum Integrieren benutzerdefinierter Berichtsansichten in die Process Reporting-Benutzeroberfläche.

Eine Liste der unterstützten Browser finden Sie unter [Von AEM Forms unterstützte Plattformen](/help/forms/using/aem-forms-jee-supported-platforms.md).

Process Reporting basiert auf Modulen, die:

* Prozessdaten aus der AEM Forms-Datenbank lesen
* Prozessdaten in einem eingebetteten Process Reporting-Repository veröffentlichen
* Eine browserbasierte Benutzeroberfläche zum Anzeigen von Berichten bieten

## Schlüsselfunktionen {#key-capabilities}

### Always-on-Reporting {#always-on-reporting}

![site-management](assets/site-management.png)

Zeigen Sie die Liste der Prozesse mit langer Laufzeit an, erstellen Sie Diagramme zur Prozessdauer und führen Sie benutzerdefinierte Abfragen mithilfe von Filtern aus.

Process Reporting bietet außerdem die Möglichkeit, die Berichts- und Abfragedaten im CSV-Format zu exportieren.

### Ad-hoc-Berichte {#adhoc-reports}

![print-&amp;-colour](assets/print-&-colour.png)

Verwenden Sie Filter, um eine bestimmte Ansicht Ihrer Daten zu erhalten.

Sie können Prozesse oder Aufgaben nach ID, Dauer, Start- und Enddatum, Prozessinitiator usw. suchen.

Sie können mehrere Filter kombinieren, um bestimmte Berichte zu erstellen.

Anschließend können Sie die Berichtsfilter speichern, um sie zu einem späteren Zeitpunkt auszuführen.

### Prozess-/Aufgabenverlauf {#process-task-history}

![file-management](assets/file-management.png)

AEM Forms-Server führen zahlreiche Prozesse parallel aus. Diese Prozesse gehen immer wieder von einem Zustand in einen anderen über. Durch die regelmäßige Veröffentlichung von Forms-Daten in das Process Reporting-Repository werden die Übergangsinformationen zu den in AEM Forms ausgeführten Prozessen in Process Reporting beibehalten.

### Zugriffssteuerung {#access-control-br}

![untitled](assets/untitled.png)

Process Reporting bietet berechtigungsbasierten Zugriff auf die Benutzeroberfläche.

Dies bedeutet, dass nur Benutzer mit Berichterstellungsberechtigungen Zugriff auf die Process Reporting-Benutzeroberfläche haben.
