---
title: Migration von Dynamic Media - Hybridmodus zu Dynamic Media - S7-Modus
description: Erfahren Sie, wie Sie Ihre Instanz von Dynamic Media - Hybrid-Modus auf Dynamic Media - S7-Modus migrieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: Business Practitioner, Administrator
exl-id: 07f0803c-4ec4-4745-8214-63370e9d0282
feature: Scene7-Modus, Hybridmodus
translation-type: tm+mt
source-git-commit: c9aec973faf4caef741961d92a6f258646aeddb7
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 2%

---

# Umstieg von Dynamic Media-Hybrid auf Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid ist eine ältere Version der Dynamic Media-Integration mit Adobe Experience Manager. Die Hybridversion wurde erstmals in AEM (Adobe Experience Manager) 6.1 eingeführt. Während die Adobe weiterhin den Hybrid-Modus unterstützt, ist er nicht der bevorzugte Modus (Dynamic Media-Scene7 ist der bevorzugte Modus). Neue Funktionen wie Smart-Zuschneiden und Panoramabilder werden ebenfalls nicht unterstützt. Dynamic Media-Scene7.

Weitere wichtige Unterschiede zwischen Dynamic Media-Hybrid und Dynamic Media-Scene7:

* Struktur der URLs.
* Aufnahme von Videos.
* Erstellen und Datenspeicherung von Bilddarstellungen.
* Cloud-Konfiguration und -Anmeldeinformationen (Bereitstellung).

Wenn Sie von Dynamic Media-Hybrid nach Dynamic Media-Scene7 wechseln, stehen Ihnen zwei Optionen zur Verfügung. Die erste Option besteht darin, einfach eine neue Instanz von Dynamic Media-Scene7 auf der AEM bereitzustellen. Die zweite Option ist die Migration Ihrer bestehenden Instanz von Dynamic Media-Hybrid nach Dynamic Media-Scene7. Mit dieser Option wird das Tabellenformular unter den Schritten und Überlegungen erläutert, die Sie während des Umzugs vornehmen müssen.

>[!IMPORTANT]
>
>Adobe empfiehlt, dass Sie keine Dynamic Media-Hybrid-Implementierung auf Live-Produktionsinstanzen nach Dynamic Media-Scene7 migrieren.

## Option 1 - Bereitstellung einer neuen Instanz von Dynamic Media-Scene7 auf AEM {#provision-new-dms7}

Erwägen Sie, einfach mit einer neuen, bereitgestellten Instanz von Dynamic Media-Scene7 auf Adobe Experience Manager neu zu beginnen. Neben der Erfassung und Verarbeitung von Assets durch Dynamic Media Cloud Service wird eine Adobe zur Prüfung der Nutzung, Workflows und Komponenten von Assets dringend empfohlen. In vielen Fällen können benutzerdefinierte Komponenten und Workflows durch neue vordefinierte Funktionen ersetzt werden.

## Option 2: Migration der vorhandenen Instanz von Dynamic Media-Hybrid auf Dynamic Media-Scene7 {#process-for-migrating}

| Schritt | Aufgabe | Besonderheiten |
|---|---|---|
| 1 | Dynamic Media-Hybrid-Autoreninstanz klonen. | Sie sollten Ihre vorhandene Instanz von Dynamic Media-Hybrid Author für Ausweichzwecke so lange beibehalten, bis die verbleibenden Schritte in diesem Migrationsprozess erfolgreich abgeschlossen sind. |
| 2 | Im Beginn geklonte Autoreninstanz im Dynamic Media-Scene7-Modus. |  |
| 3 | Konfigurieren Sie in Adobe Experience Manager-Cloud Services Dynamic Media mit Dynamic Media-Scene7-Anmeldeinformationen. | Die Adobe muss die Dynamic Media-Scene7-Bereitstellung genehmigen. Sie verfügen über gleichzeitige Umgebung für Dynamic MediaM-Hybrid und Dynamic Media-Scene7, die für eine begrenzte Zeit unterstützt werden. |
| 4 | Erstellen Sie das Migrationsbündel, um Assets nach Bedarf zu erfassen.<br>Löschen Sie die lokalen PTIFFs, die bei der anfänglichen Erfassung in Dynamic Media-Hybrid erstellt wurden. | Wenn alle Assets derzeit in Ihrer Dynamic Media-Hybrid-Instanz verfügbar sind, enthält ein Klon bereits alle Assets. Daher ist kein Paket erforderlich. |
| 5 | Führen Sie den Asset-Aktualisierungsarbeitsablauf aus, um Assets mit dem Dynamic Media-Cloud Service zu synchronisieren. | Adobe empfiehlt, dass der Aktualisierungsarbeitsablauf in Stapeln ausgeführt wird, um eine Kompensation zu ermöglichen. |
| 6 | Migrieren von Viewer-, Bild- und Video-Vorgaben |  |
| 7 | Gehen Sie zu jedem Web-Content-Management-referenzierten Asset und aktualisieren Sie die zugehörigen URLs. |  |
| 8 | Migrieren Sie benutzerdefinierte Workflows, um den neuen Dynamic Media-Scene7-Modus zu unterstützen (manuelle Aktualisierungen). |  |
| 9 | Überprüfen Sie Ihren Web-Content-Management-Upload und Ihre Konfiguration. |  |
| 10 | Nach der Überprüfung erhalten Sie eine Genehmigung zur Deaktivierung von Dynamic Media-Hybrid Author (als Fallback beibehalten). |  |
| 11 | Löschen Sie die Dynamic Media-Hybrid-Autoreninstanz nach etwa einem Monat erfolgreicher Verwendung von Dynamic Media-Scene7. |  |
