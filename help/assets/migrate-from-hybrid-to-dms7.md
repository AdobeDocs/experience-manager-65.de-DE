---
title: Migration von Dynamic Media - Hybridmodus zu Dynamic Media - S7-Modus
description: Erfahren Sie, wie Sie Ihre Instanz von Dynamic Media - Hybridmodus in Dynamic Media - S7-Modus migrieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
feature: Scene7-Modus,Hybridmodus
exl-id: 07f0803c-4ec4-4745-8214-63370e9d0282
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 2%

---

# Über den Wechsel von Dynamic Media-Hybrid zu Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid ist eine ältere Version der Dynamic Media-Integration mit Adobe Experience Manager. Die Hybridversion wurde erstmals in AEM (Adobe Experience Manager) 6.1 eingeführt. Obwohl die Adobe den Hybridmodus weiterhin unterstützt, ist dies nicht der bevorzugte Modus (Dynamic Media-Scene7 ist der bevorzugte Modus). Außerdem werden keine neuen Funktionen wie smartes Zuschneiden und Panoramabilder unterstützt. Dynamic Media-Scene7 dagegen.

Weitere wichtige Unterschiede zwischen Dynamic Media-Hybrid und Dynamic Media-Scene7:

* Struktur von URLs.
* Aufnahme von Videos.
* Erstellen und Speichern von Bildausgabeformaten.
* Cloud-Konfiguration und Anmeldedaten (Bereitstellung).

Beim Wechsel von Dynamic Media-Hybrid zu Dynamic Media-Scene7 stehen zwei Optionen zur Verfügung. Die erste Option besteht darin, einfach eine neue Instanz von Dynamic Media-Scene7 auf AEM bereitzustellen. Die zweite Option besteht darin, Ihre vorhandene Instanz von Dynamic Media-Hybrid nach Dynamic Media-Scene7 zu migrieren. Mit dieser Option wird das Tabellenformular unterhalb der Schritte und Überlegungen erläutert, die Sie während des Schritts durchführen müssen.

>[!IMPORTANT]
>
>Adobe empfiehlt, keine Dynamic Media-Hybrid-Implementierung auf Dynamic Media-Scene7 in Live-Produktionsinstanzen zu migrieren.

## Option 1: Bereitstellung einer neuen Instanz von Dynamic Media-Scene7 auf AEM {#provision-new-dms7}

Erwägen Sie einfach, mit einer neuen, bereitgestellten Instanz von Dynamic Media-Scene7 in Adobe Experience Manager zu beginnen. Neben der Erfassung und Verarbeitung von Assets über Dynamic Media Cloud Service wird eine Adobe-Prüfung der Asset-Nutzung, der Workflows und der Komponenten dringend empfohlen. In vielen Fällen können benutzerdefinierte Komponenten und Workflows durch neuere vordefinierte Funktionen ersetzt werden.

## Option 2: Migration der vorhandenen Instanz von Dynamic Media-Hybrid zu Dynamic Media-Scene7 {#process-for-migrating}

| Schritt | Aufgabe | Aspekte |
|---|---|---|
| 1 | Dynamic Media-Hybrid-Autoreninstanz klonen. | Sie sollten Ihre vorhandene Instanz der Dynamic Media-Hybrid-Autoreninstanz für Ausweichzwecke beibehalten, bis die verbleibenden Schritte in diesem Migrationsprozess erfolgreich abgeschlossen sind. |
| 2 | Starten Sie die geklonte Autoreninstanz im Dynamic Media-Scene7-Modus. |  |
| 3 | Konfigurieren Sie in Adobe Experience Manager Cloud Services Dynamic Media mit Dynamic Media-Scene7-Anmeldeinformationen. | Adobe muss die Dynamic Media-Scene7-Bereitstellung genehmigen. Sie verfügen über gleichzeitige Dynamic MediaM-Hybrid- und Dynamic Media-Scene7-Umgebungen, die zeitlich begrenzt unterstützt werden. |
| 4 | Erstellen Sie das Migrationspaket , um Assets nach Bedarf aufzunehmen.<br>Löschen Sie die lokalen PTIFF-Dateien, die bei der ersten Aufnahme in Dynamic Media-Hybrid erstellt wurden. | Wenn alle Assets derzeit in Ihrer Dynamic Media-Hybrid-Instanz verfügbar sind, enthält ein Klon von bereits alle Assets. Daher ist kein Bundle erforderlich. |
| 5 | Führen Sie den Workflow zur Asset-Aktualisierung aus, um Assets mit dem Dynamic Media-Cloud Service zu synchronisieren. | Adobe empfiehlt, den Aktualisierungs-Workflow in Stapeln durchzuführen, um eine Komprimierung zu ermöglichen. |
| 6 | Migrieren von Viewer-, Bild- und Videovorgaben. |  |
| 7 | Durchsuchen Sie alle Web Content Management-referenzierten Assets und aktualisieren Sie die zugehörigen URLs. |  |
| 8 | Migrieren Sie alle benutzerdefinierten Workflows, um den neuen Dynamic Media-Scene7-Modus (manuelle Aktualisierungen) zu unterstützen. |  |
| 9 | Überprüfen Sie den Upload und die Konfiguration des Web Content Management. |  |
| 10 | Nach der Überprüfung können Sie die Dynamic Media-Hybrid-Autoreninstanz deaktivieren (als Fallback beibehalten). |  |
| 11 | Löschen Sie die Dynamic Media-Hybrid-Autoreninstanz nach etwa einem Monat erfolgreicher Verwendung von Dynamic Media und Scene7. |  |
