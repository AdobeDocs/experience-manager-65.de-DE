---
title: Migration von dynamischen Medien - Hybridmodus zu dynamischen Medien - S7-Modus
description: Erfahren Sie, wie Sie Ihre Instanz dynamischer Medien - Hybrid-Modus zu dynamischen Medien - S7-Modus migrieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
translation-type: tm+mt
source-git-commit: 7aba1f3b492a07fe502f95535a94c8054a044eb5

---


# Übergang von Dynamic Media-Hybrid zu Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid ist eine ältere Version der Dynamic Media-Integration mit Adobe Experience Manager. Die Hybridversion wurde erstmals in AEM (Adobe Experience Manager) 6.1 eingeführt. Obwohl Adobe weiterhin den Hybrid-Modus unterstützt, ist er nicht der bevorzugte Modus (der bevorzugte Modus ist Dynamic Media-Scene7). Neue Funktionen wie Smart-Zuschneiden und Panoramabilder werden ebenfalls nicht unterstützt. Dynamische Medien - Scene7 hingegen schon.

Zu den weiteren wichtigen Unterschieden zwischen Dynamic Media-Hybrid und Dynamic Media-Scene7 gehören die folgenden:

* Struktur der URLs.
* Aufnahme von Videos.
* Erstellen und Datenspeicherung von Bilddarstellungen.
* Cloud-Konfiguration und -Anmeldeinformationen (Bereitstellung).

Beim Wechsel von &quot;Dynamic Media-Hybrid&quot;zu &quot;Dynamic Media-Scene7&quot;stehen zwei Optionen zur Verfügung. Die erste Option besteht darin, einfach eine neue Instanz von Dynamic Media-Scene7 in AEM bereitzustellen. Die zweite Option besteht darin, Ihre vorhandene Instanz von Dynamic Media-Hybrid auf Dynamic Media-Scene7 zu migrieren. Mit dieser Option wird das Tabellenformular unter den Schritten und Überlegungen erläutert, die Sie während des Umzugs vornehmen müssen.

>[!IMPORTANT]
>
>Adobe empfiehlt, dass Sie keine dynamische Media-Hybrid-Implementierung zu Dynamic Media-Scene7 in Live-Produktionsinstanzen migrieren.

## Option 1 - Bereitstellung einer neuen Instanz von Dynamic Media-Scene7 auf AEM {#provision-new-dms7}

Beginnen Sie einfach mit einer neuen, bereitgestellten Instanz von Dynamic Media-Scene7 in Adobe Experience Manager. Zusätzlich zur Erfassung und Verarbeitung von Assets über den Dynamischen Media Cloud-Dienst wird eine Adobe-Prüfung der Nutzung, Workflows und Komponenten von Assets dringend empfohlen. In vielen Fällen können benutzerdefinierte Komponenten und Workflows durch neue vordefinierte Funktionen ersetzt werden.

## Option 2 - Migration Ihrer vorhandenen Instanz von Dynamic Media-Hybrid zu Dynamic Media-Scene7 {#process-for-migrating}

| Schritt | Aufgabe | Besonderheiten |
|---|---|---|
| 1 | Clone Dynamic Media-Hybrid Author-Instanz. | Sie sollten Ihre vorhandene Instanz des dynamischen Media-Hybrid-Autors für Ausweichzwecke so lange beibehalten, bis die verbleibenden Schritte in diesem Migrationsprozess erfolgreich abgeschlossen sind. |
| 2 | Im Beginn geklonte Autoreninstanz im Modus &quot;Dynamische Medien-Scene7&quot;. |  |
| 3 | Konfigurieren Sie in Adobe Experience Manager Cloud-Services dynamische Medien mit dynamischen Media-Scene7-Anmeldeinformationen. | Adobe muss die Bereitstellung für dynamische Medien-Scene7 genehmigen. Sie verfügen über parallele Umgebung für dynamische MedienM-Hybrid und Dynamic Media-Scene7, die für eine begrenzte Zeit unterstützt werden. |
| 4 | Erstellen Sie das Migrationsbündel, um Assets nach Bedarf zu erfassen.<br>Löschen Sie die lokalen PTIFFs, die bei der anfänglichen Erfassung in Dynamic Media-Hybrid erstellt wurden. | Wenn alle Assets derzeit in Ihrer Dynamic Media-Hybrid-Instanz verfügbar sind, enthält ein Klon davon bereits alle. Daher ist kein Paket erforderlich. |
| 5 | Führen Sie den Arbeitsablauf für die Asset-Aktualisierung aus, um Assets mit dem Dynamischen Media Cloud-Dienst zu synchronisieren. | Adobe empfiehlt, dass der Aktualisierungsarbeitsablauf in Stapeln ausgeführt wird, um eine Kompensation zu ermöglichen. |
| 6 | Migrieren von Viewer-, Bild- und Video-Vorgaben |  |
| 7 | Gehen Sie zu jedem Web-Content-Management-referenzierten Asset und aktualisieren Sie die zugehörigen URLs. |  |
| 8 | Migrieren Sie benutzerdefinierte Workflows, um den neuen Modus für dynamische Medien-Scene7 zu unterstützen (manuelle Aktualisierungen). |  |
| 9 | Überprüfen Sie Ihren Web-Content-Management-Upload und Ihre Konfiguration. |  |
| 10 | Nach der Überprüfung erhalten Sie eine Genehmigung zur Deaktivierung des Dynamic Media-Hybrid-Autors (als Fallback beibehalten). |  |
| 11 | Löschen Sie die Instanz des dynamischen Media-Hybrid-Autorenmodus nach etwa einem Monat erfolgreicher Verwendung der dynamischen Medien-Scene7. |  |
