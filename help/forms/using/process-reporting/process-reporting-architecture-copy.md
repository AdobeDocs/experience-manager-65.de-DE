---
title: Funktionsweise von Prozess-Reporting
seo-title: How Process Reporting Works
description: Beschreibung der Services von AEM Forms in der Prozessberichterstellung unter JEE und Einführung in die Bedienelemente der Prozessberichterstellung
seo-description: Description of the services that make up the AEM Forms on JEE Process Reporting and an introduction to the Process Reporting UI
uuid: 4631b734-a679-495c-a708-2348bf22c1f7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
discoiquuid: a1af9920-5d2a-462f-bdee-ccec4c047c5b
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: ht
source-wordcount: '345'
ht-degree: 100%

---


# Funktionsweise von Prozess-Reporting {#how-process-reporting-works}

Die Prozessberichterstellung ist das Modul für die Berichterstellung von AEM Forms unter JEE.

Mit der Prozessberichterstellung können Sie Berichte zu AEM Forms-Prozessen und -Aufgaben ausführen.

Die Prozessberichterstellung verwendet das eingebettete Repository für die Prozessberichterstellung, um Forms-Daten zu veröffentlichen. Anschließend werden diese Daten zum Erstellen von Berichten verwendet.

Die Prozessberichterstellung besteht aus den folgenden Modulen:

* [ProcessDataPublisher-Service](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatapublisher-service-br-p)
* [ProcessDataStorage-Service](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatastorageprovider-service-br-p)
* [OSGi-Dienst](/help/forms/using/process-reporting/process-reporting-architecture.md#p-osgi-service-br-p)
* [Query Data-Servlet](/help/forms/using/process-reporting/process-reporting-architecture.md#p-querydataservlet-service-br-p)
* [Benutzeroberfläche für die Prozessberichterstellung](/help/forms/using/process-reporting/process-reporting-architecture.md#p-process-reporting-user-interface-br-p)

## Architektur der Prozessberichterstellung {#process-reporting-architecture-br}

![processreportingarchitecture](assets/processreportingarchitecture.png)

## Module der Prozessberichterstellung {#process-reporting-modules}

### ProcessDataPublisher-Service {#processdatapublisher-service-br}

Der ProcessDataPublisher-Server wird regelmäßig ausgeführt, um aus der AEM Forms-Datenbank die Daten zu extrahieren, die seit der letzten Ausführung des Services geändert wurden. Anschließend übergibt der Service diese Daten an den Process Data Storage-Service.

Weitere Informationen zum Konfigurieren des Services finden Sie unter [ProcessDataPublisher-Service konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### ProcessDataStorageProvider-Service {#processdatastorageprovider-service-br}

Der ProcessDataStorageProvider-Service empfängt Prozessdaten vom ProcessDataPublisher-Service und speichert diese Daten im Repository für die Prozessberichterstellung.

Weitere Informationen zum Konfigurieren des Services finden Sie unter [ProcessDataStorageProvider-Dienst konfigurieren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### OSGi-Dienst {#osgi-service-br}

Das QueryDataServlet verwendet diesen Service, um Berichtsdaten aus dem Repository der Prozessberichterstellung abzurufen.

### QueryDataServlet-Service {#querydataservlet-service-br}

Der QueryDataServlet-Service nimmt Abfragen aus der Benutzeroberfläche für die Prozessberichterstellung entgegen.

Der Service verwendet dann OSGi-Services, um die relevanten Berichtsdaten abzurufen, sie zu verarbeiten und anschließend an die Benutzeroberfläche zurückzugeben.

### Benutzeroberfläche für die Prozessberichterstellung {#process-reporting-user-interface-br}

Die Benutzeroberfläche für die Prozessberichterstellung ist webbrowserbasiert. Diese Schnittstelle dient dem Anzeigen von Prozess- und Aufgabendaten, die aus der AEM Forms-Datenbank veröffentlicht werden.

### QueryDataServlet-Service {#querydataservlet-service-br-1}

Der QueryDataServlet-Service nimmt Abfragen aus der Benutzeroberfläche für die Prozessberichterstellung entgegen.

Der Service verwendet dann OSGi-Services, um die relevanten Berichtsdaten abzurufen, sie zu verarbeiten und anschließend an die Benutzeroberfläche zurückzugeben.

### Benutzerdefinierte Berichte {#custom-reports-br}

Sie können Ihre eigenen benutzerdefinierten Berichte erstellen und diese auf der Registerkarte Benutzerdefinierte Berichte in der Benutzeroberfläche für die Prozessberichterstellung anzeigen.

Die Schritte zum Erstellen eines benutzerspezifischen Berichts finden Sie unter „So erstellen Sie einen benutzerspezifischen Bericht“ im Artikel [Benutzerdefinierte Berichte in Process Reporting](/help/forms/using/process-reporting/process-reporting-custom-reports.md).
