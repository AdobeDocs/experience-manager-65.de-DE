---
title: Funktionsweise von Prozess-Reporting
description: Beschreibung der Services von AEM Forms in der Prozessberichterstellung unter JEE und Einführung in die Bedienelemente der Prozessberichterstellung
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
docset: aem65
exl-id: 66dfac36-5b7e-40be-9921-efa9f2a9521c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 100%

---

# Funktionsweise von Prozess-Reporting{#how-process-reporting-works}

Die Prozessberichterstellung ist das Modul für die Berichterstellung von AEM Forms unter JEE.

Mit der Prozessberichterstellung können Sie Berichte zu AEM Forms-Prozessen und -Aufgaben ausführen.

Die Prozessberichterstellung verwendet das eingebettete Repository für die Prozessberichterstellung, um Forms-Daten zu veröffentlichen. Anschließend werden diese Daten zum Erstellen von Berichten verwendet.

Die Prozessberichterstellung besteht aus den folgenden Modulen:

* [ProcessDataPublisher-Service](#processdatapublisher-service-br-p)
* [ProcessDataStorage-Service](#processdatastorageprovider-service-br-p)
* [OSGi-Dienst](#osgi-service-br-p)
* [Query Data-Servlet](#querydataservlet-service-br-p)
* [Benutzeroberfläche für die Prozessberichterstellung](#process-reporting-user-interface-br-p)

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

Eine Einführung in die Benutzeroberfläche für die Prozessberichterstellung finden Sie unter [Benutzeroberfläche für die Prozessberichterstellung](/help/forms/using/process-reporting/introduction-process-reporting.md).

### QueryDataServlet-Service {#querydataservlet-service-br-1}

Der QueryDataServlet-Service nimmt Abfragen aus der Benutzeroberfläche für die Prozessberichterstellung entgegen.

Der Service verwendet dann OSGi-Services, um die relevanten Berichtsdaten abzurufen, sie zu verarbeiten und anschließend an die Benutzeroberfläche zurückzugeben.

### Benutzerdefinierte Berichte {#custom-reports-br}

Sie können Ihre eigenen benutzerdefinierten Berichte erstellen und diese auf der Registerkarte Benutzerdefinierte Berichte in der Benutzeroberfläche für die Prozessberichterstellung anzeigen.

Die Schritte zum Erstellen eines benutzerdefinierten Berichts finden Sie im Abschnitt zur Erstellung benutzerdefinierter Berichte im Artikel [Benutzerdefinierte Berichte in der Prozessberichterstellung](/help/forms/using/process-reporting/process-reporting-custom-reports.md).
