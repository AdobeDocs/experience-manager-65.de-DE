---
title: Migration von dynamischen Medien - Hybridmodus zu dynamischen Medien - S7-Modus
description: Erfahren Sie, wie Sie Ihre Instanz dynamischer Medien - Hybrid-Modus zu dynamischen Medien - S7-Modus migrieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
translation-type: tm+mt
source-git-commit: f466193a259d9e8869d7f79eafda1be20869e4af
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 2%

---


# Umstieg von Dynamic Media-Hybrid auf Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid ist eine ältere Version der Dynamic Media-Integration mit Adobe Experience Manager. Die Hybridversion wurde erstmals in AEM (Adobe Experience Manager) 6.1 eingeführt. Während die Adobe weiterhin den Hybrid-Modus unterstützt, ist er nicht der bevorzugte Modus (Dynamic Media-Scene7 ist der bevorzugte Modus). Neue Funktionen wie Smart-Zuschneiden und Panoramabilder werden ebenfalls nicht unterstützt. Dynamische Medien-Scene7 hingegen.

Weitere wichtige Unterschiede zwischen Dynamic Media-Hybrid und Dynamic Media-Scene7:

* Struktur der URLs.
* Aufnahme von Videos.
* Erstellen und Datenspeicherung von Bilddarstellungen.
* Cloud-Konfiguration und -Anmeldeinformationen (Bereitstellung).

Es stehen zwei Optionen zur Verfügung, wenn Sie von Dynamic Media-Hybrid auf Dynamic Media-Scene7 umstellen. Die erste Option besteht darin, einfach eine neue Instanz von Dynamic Media-Scene7 auf AEM bereitzustellen. Die zweite Option besteht darin, Ihre vorhandene Instanz von Dynamic Media-Hybrid auf Dynamic Media-Scene7 zu migrieren. Mit dieser Option wird das Tabellenformular unter den Schritten und Überlegungen erläutert, die Sie während des Umzugs vornehmen müssen.

>[!IMPORTANT]
>
>Adobe empfiehlt, dass Sie keine Dynamic Media-Hybrid-Implementierung auf Dynamic Media-Scene7 in Live-Produktionsinstanzen migrieren.

## Option 1 - Bereitstellung einer neuen Instanz von Dynamic Media-Scene7 auf AEM {#provision-new-dms7}

Beginnen Sie einfach mit einer neuen, bereitgestellten Instanz von Dynamic Media-Scene7 auf Adobe Experience Manager. Zusätzlich zur Erfassung und Verarbeitung von Assets über den Cloud Service für dynamische Medien wird eine Überprüfung der Adobe der Nutzung, Workflows und Komponenten dringend empfohlen. In vielen Fällen können benutzerdefinierte Komponenten und Workflows durch neue vordefinierte Funktionen ersetzt werden.

## Option 2: Migration der vorhandenen Instanz von Dynamic Media-Hybrid zu Dynamic Media-Scene7 {#process-for-migrating}

| Schritt | Aufgabe | Besonderheiten |
|---|---|---|
| 1 | Clone Dynamic Media-Hybrid Author-Instanz. | Sie sollten Ihre vorhandene Instanz des dynamischen Media-Hybrid-Autors für Ausweichzwecke so lange beibehalten, bis die verbleibenden Schritte in diesem Migrationsprozess erfolgreich abgeschlossen sind. |
| 2 | Im Beginn geklonte Autoreninstanz im Modus &quot;Dynamisches Media-Scene7&quot;. |  |
| 3 | Konfigurieren Sie in Adobe Experience Manager-Cloud Services dynamische Medien mit den Anmeldedaten für das dynamische Media-Scene7. | Adobe muss die Bereitstellung für dynamische Medien und Scene7 genehmigen. Sie verfügen über gleichzeitige Umgebung für Dynamic MediaM-Hybrid und Dynamic Media-Scene7, die für eine begrenzte Zeit unterstützt werden. |
| 4 | Erstellen Sie das Migrationsbündel, um Assets nach Bedarf zu erfassen.<br>Löschen Sie die lokalen PTIFFs, die bei der anfänglichen Erfassung in Dynamic Media-Hybrid erstellt wurden. | Wenn alle Assets derzeit in Ihrer Dynamic Media-Hybrid-Instanz verfügbar sind, enthält ein Klon davon bereits alle. Daher ist kein Paket erforderlich. |
| 5 | Führen Sie den Arbeitsablauf für die Asset-Aktualisierung aus, um Assets mit dem Cloud Service für dynamische Medien zu synchronisieren. | Adobe empfiehlt, dass der Aktualisierungsarbeitsablauf in Stapeln ausgeführt wird, um eine Kompensation zu ermöglichen. |
| 6 | Migrieren von Viewer-, Bild- und Video-Vorgaben |  |
| 7 | Gehen Sie zu jedem Web-Content-Management-referenzierten Asset und aktualisieren Sie die zugehörigen URLs. |  |
| 8 | Migrieren Sie benutzerdefinierte Workflows, um den neuen Modus &quot;Dynamische Medien - Scene7&quot;zu unterstützen (manuelle Aktualisierungen). |  |
| 9 | Überprüfen Sie Ihren Web-Content-Management-Upload und Ihre Konfiguration. |  |
| 10 | Nach der Überprüfung erhalten Sie eine Genehmigung zur Deaktivierung des Dynamic Media-Hybrid-Autors (als Fallback beibehalten). |  |
| 11 | Löschen Sie die Instanz des dynamischen Media-Hybrid-Autorenmodus nach etwa einem Monat erfolgreicher Verwendung von Dynamic Media-Scene7. |  |
