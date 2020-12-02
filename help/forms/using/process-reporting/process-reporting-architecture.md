---
title: Funktionsweise von Process Berichte
seo-title: Funktionsweise von Process Berichte
description: Beschreibung der Dienste, aus denen der AEM Forms on JEE Process Berichte besteht, und eine Einführung in die Benutzeroberfläche von Process Berichte
seo-description: Beschreibung der Dienste, aus denen der AEM Forms on JEE Process Berichte besteht, und eine Einführung in die Benutzeroberfläche von Process Berichte
uuid: 37e31985-088a-4ef6-ba57-10a01597a873
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
discoiquuid: a6ff50df-273d-48f7-b0c6-0e69e900b97f
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---


# Funktionsweise von Process Berichte{#how-process-reporting-works}

Process Berichte ist das Berichte-Modul von AEM Forms on JEE.

Mit Process Berichte können Sie Berichte zu AEM Forms-Prozessen und -Aufgaben ausführen.

Process Berichte verwendet das eingebettete Process Berichte-Repository, um Forms-Daten zu veröffentlichen. Diese Daten werden dann zum Ausführen von Berichten verwendet.

Process Berichte umfasst die folgenden Module:

* [ProcessDataPublisher-Dienst](#processdatapublisher-service-br-p)
* [ProcessDataStorage-Dienst](#processdatastorageprovider-service-br-p)
* [OSGi-Dienst](#osgi-service-br-p)
* [Abfrage Data Servlet](#querydataservlet-service-br-p)
* [Benutzeroberfläche von Process Berichte](#process-reporting-user-interface-br-p)

## Process Berichte architecture {#process-reporting-architecture-br}

![processreportingarchitecture](assets/processreportingarchitecture.png)

## Process Berichte modules {#process-reporting-modules}

### ProcessDataPublisher-Dienst {#processdatapublisher-service-br}

Der ProcessDataPublisher-Server wird regelmäßig auf der AEM Forms-Datenbank ausgeführt und extrahiert die Daten, die seit der letzten Ausführung des Dienstes geändert wurden. Anschließend werden die Daten im Process Data Datenspeicherung-Dienst veröffentlicht.

Weitere Informationen zum Konfigurieren des Dienstes finden Sie unter [ProcessDataPublisher-Dienst konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### ProcessDataStorageProvider-Dienst {#processdatastorageprovider-service-br}

Der ProcessDataStorageProvider-Dienst empfängt Prozessdaten vom ProcessDataPublisher-Dienst und speichert die Daten im Process Berichte-Repository.

Weitere Informationen zum Konfigurieren des Dienstes finden Sie unter [ProcessDataStorageProvider-Dienst konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### OSGi-Dienst {#osgi-service-br}

Das QueryDataServlet verwendet diesen Dienst, um die Berichte-Daten aus dem Process Berichte-Repository abzurufen.

### QueryDataServlet-Dienst {#querydataservlet-service-br}

Der QueryDataServlet-Dienst akzeptiert Abfragen aus der Process Berichte-Benutzeroberfläche.

Der Dienst nutzt dann OSGi-Dienste, um die relevanten Daten des Berichte abzurufen, die Daten zu verarbeiten und die Daten an die Benutzeroberfläche zurückzugeben.

### Process Berichte-Benutzeroberfläche {#process-reporting-user-interface-br}

Die Benutzeroberfläche von Process Berichte ist eine webbrowser-basierte Benutzeroberfläche. Auf dieser Oberfläche können Sie Informationen zur Ansicht und Aufgabe verwenden, die aus der AEM Forms-Datenbank veröffentlicht werden.

Eine Einführung in die Benutzeroberfläche von Process Berichte finden Sie unter [Benutzeroberfläche von Process Berichte](/help/forms/using/process-reporting/introduction-process-reporting.md).

### QueryDataServlet-Dienst {#querydataservlet-service-br-1}

Der QueryDataServlet-Dienst akzeptiert Abfragen aus der Process Berichte-Benutzeroberfläche.

Der Dienst nutzt dann OSGi-Dienste, um die relevanten Daten des Berichte abzurufen, die Daten zu verarbeiten und die Daten an die Benutzeroberfläche zurückzugeben.

### Benutzerspezifische Berichte {#custom-reports-br}

Sie können eigene benutzerspezifische Berichte erstellen und diese Berichte auf der Registerkarte &quot;Benutzerspezifische Berichte&quot;der Benutzeroberfläche von Process Berichte anzeigen.

Die Schritte zum Erstellen eines benutzerspezifischen Berichts finden Sie unter So erstellen Sie einen benutzerspezifischen Bericht im Artikel [Benutzerspezifische Berichte in Process Berichte](/help/forms/using/process-reporting/process-reporting-custom-reports.md).
