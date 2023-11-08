---
title: Übersicht der Statusüberwachung
seo-title: Overview of Health Monitor
description: Dieses Dokument bietet einen Überblick über den Health Monitor und Details dazu, wie Sie darauf zugreifen können.
seo-description: This document provides the overview of the Health monitor, and details about how you can access it.
uuid: 5934fd2d-80a5-4c6d-b3ee-882c2865705b
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c303e967-944d-40b0-96ca-f91e2f42a0d0
exl-id: 05f8b430-141e-4921-98b1-a0d8f636e478
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 9%

---

# Übersicht der Statusüberwachung {#overview-of-health-monitor}

Health Monitor stellt wichtige Informationen zum AEM Forms-System bereit, z. B. Serverinformationen, Speicherbelegung und Prozessorauslastung. Außerdem stehen Work Manager-Statistiken zur Verfügung, z. B. die Anzahl der Arbeitselemente oder Aufträge in der Warteschlange und deren Status. Sie können die folgenden Aufgaben mithilfe von Health Monitor ausführen:

* Überprüfen Sie, ob das System ordnungsgemäß ausgeführt wird.
* Anzeigen von Informationen zur Diagnose von Systemproblemen bei deren Auftreten
* Ausführen von Vorgängen für Arbeitselemente oder Aufträge mit Problemen
* Bereinigen veralteter Datensätze aus der Job Manager-Datenbank

Die Seite &quot;Health Monitor&quot;in Administration Console verfügt über drei Registerkarten:

* Auf der Registerkarte System werden Diagramme zur Ressourcenüberwachung und Informationen zum Forms-Server (oder Knoten in einer Clusterumgebung) angezeigt. (Siehe [Systeminformationen anzeigen](/help/forms/using/admin-help/view-system-information.md#view-system-information).
* Auf der Registerkarte &quot;Work Manager&quot;werden Daten angezeigt, die mit Work Manager in Verbindung stehen, z. B. die Anzahl der Arbeitselemente in der Warteschlange von Work Manager. Sie können die Informationen mithilfe verschiedener Kriterien filtern oder einzelne Arbeitselemente mithilfe der Vorgangstools verwalten. (Siehe [Anzeigen von Statistiken im Zusammenhang mit Work Manager](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).
* Auf der Registerkarte &quot;Zeitplaner für die Auftragsbereinigung&quot;können Sie veraltete Datensätze aus der Job Manager-Datenbank bereinigen. (Siehe [Job Manager-Datenbank um Datensätze bereinigen](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).

Die Webseite &quot;Health Monitor&quot;enthält Statistiken, die über eine Gemfire-API erfasst wurden. Diese API erkennt automatisch alle Knoten in einem Cluster. Außerdem werden Sicherheitsprobleme behoben, die auftreten, wenn Statistiken von Proxyservern oder Lastenausgleichern erfasst werden. Es stehen Java-Optionen zum Optimieren von Health Monitor zur Verfügung, mit deren Hilfe Sie die Auswirkungen auf die Leistung der AEM Forms-Umgebung reduzieren können. (Siehe [Optimieren der Leistung von Health Monitor](/help/forms/using/admin-help/fine-tuning-health-monitor-performance.md#fine-tuning-health-monitor-performance).

**Auf die Statusüberwachung zugreifen**

1. Klicken Sie in Administration Console oben rechts auf der Seite auf Health Monitor .
