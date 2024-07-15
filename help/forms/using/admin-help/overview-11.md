---
title: Übersicht der Statusüberwachung
description: Dieses Dokument bietet einen Überblick über den Health Monitor und Details dazu, wie Sie darauf zugreifen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 05f8b430-141e-4921-98b1-a0d8f636e478
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---

# Übersicht der Statusüberwachung {#overview-of-health-monitor}

Health Monitor stellt wichtige Informationen zum AEM Forms-System bereit, z. B. Server-Informationen, Speichernutzung und Prozessorauslastung. Außerdem stehen Work Manager-Statistiken zur Verfügung, z. B. die Anzahl der Arbeitselemente oder Aufträge in der Warteschlange und deren Status. Sie können die folgenden Aufgaben mithilfe von Health Monitor ausführen:

* Überprüfen, ob das System ordnungsgemäß läuft
* Anzeigen von Informationen zur Diagnose von auftretenden Systemproblemen
* Ausführen von Vorgängen mit Arbeitselementen oder Aufträgen, die Probleme aufweisen
* Bereinigung von veralteten Einträgen in der Job Manager-Datenbank

Die Seite „Health Monitor“ in der Administrationskonsole verfügt über drei Registerkarten:

* Auf der Registerkarte „System“ werden Diagramme zur Ressourcenüberwachung und Informationen zum Formular-Server (oder Knoten in einer Cluster-Umgebung) angezeigt. (Weitere Informationen finden Sie unter [Anzeigen von Systeminformationen](/help/forms/using/admin-help/view-system-information.md#view-system-information).
* Auf der Registerkarte „Work Manager“ werden Daten mit Bezug auf Work Manager, z. B. die Anzahl der Arbeitselemente in der Warteschlange von Work Manager, angezeigt. Sie können die Informationen mithilfe von verschiedenen Kriterien filtern oder einzelne Arbeitselemente mithilfe der Vorgangs-Tools verwalten. (Weitere Informationen finden Sie unter [Anzeigen von Statistiken mit Bezug auf Work Manager](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).)
* Mithilfe der Registerkarte „Zeitplaner für die Auftragsbereinigung“ können Sie veraltete Einträge aus der Job Manager-Datenbank löschen. (Weitere Informationen finden Sie unter [Bereinigen von Einträgen in der Job Manager-Datenbank](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database).)

Die Health Monitor-Web-Seite wird mit Statistiken, die mithilfe einer Gemfire-API gesammelt werden, aufgefüllt. Diese API erkennt automatisch alle Knoten in einem Cluster. Sie löst auch Sicherheitsprobleme, die auftreten, wenn Statistiken von Proxy-Servern oder Lastenausgleichsmodulen gesammelt werden. Es stehen Java-Optionen zum Optimieren von Health Monitor zur Verfügung, mit deren Hilfe Sie die Auswirkungen auf die Leistung der AEM Forms-Umgebung reduzieren können. (Weitere Informationen finden Sie unter [Leistungsoptimierung von Health Monitor](/help/forms/using/admin-help/fine-tuning-health-monitor-performance.md#fine-tuning-health-monitor-performance).)

**Zugreifen auf Health Monitor**

1. Klicken Sie in der Administrationskonsole in der rechten oberen Ecke der Seite auf „Health Monitor“.
