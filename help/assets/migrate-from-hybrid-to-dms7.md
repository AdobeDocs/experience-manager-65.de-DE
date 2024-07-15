---
title: Migration vom Dynamic Media-Hybridmodus zum Dynamic Media-S7-Modus
description: Erfahren Sie, wie Sie Ihre Instanz vom Dynamic Media-Hybridmodus zum Dynamic Media-S7-Modus migrieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
feature: Scene7 Mode,Hybrid Mode
exl-id: 07f0803c-4ec4-4745-8214-63370e9d0282
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 100%

---

# Über den Wechsel von Dynamic Media-Hybrid zu Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid ist eine ältere Version der Dynamic Media-Integration mit Adobe Experience Manager. Die Hybridversion wurde erstmals in Adobe Experience Manager 6.1 eingeführt. Obwohl Adobe den Hybridmodus weiterhin unterstützt, ist dies nicht der bevorzugte Modus. Der bevorzugte Modus ist Dynamic Media-Scene7. Der Hybridmodus unterstützt auch keine neuen Funktionen wie smartes Zuschneiden und Panoramabilder, während Dynamic Media-Scene7 sie unterstützt.

Weitere wichtige Unterschiede zwischen Dynamic Media-Hybrid und Dynamic Media-Scene7:

* Struktur von URLs.
* Aufnahme von Videos.
* Erstellen und Speichern von Bildausgabedarstellungen.
* Cloud-Konfiguration und Anmeldedaten (Bereitstellung).

Beim Wechsel von Dynamic Media-Hybrid zu Dynamic Media-Scene7 stehen zwei Optionen zur Verfügung. Die erste Option besteht darin, einfach eine neue Instanz von Dynamic Media-Scene7 auf Experience Manager bereitzustellen. Die zweite Option besteht darin, Ihre vorhandene Instanz von Dynamic Media-Hybrid nach Dynamic Media-Scene7 zu migrieren. Bei dieser Option werden die Schritte und Überlegungen, die Sie während des Wechsels anstellen müssen, wie unten in Tabellenform dargestellt.

>[!IMPORTANT]
>
>Adobe empfiehlt, dass Sie eine Dynamic Media-Hybrid-Implementierung nicht auf Live-Produktionsinstanzen zu Dynamic Media-Scene7 migrieren.

## Option 1: Bereitstellung einer neuen Instanz von Dynamic Media-Scene7 auf Experience Manager {#provision-new-dms7}

Sie könnten einfach mit einer neuen, bereitgestellten Instanz von Dynamic Media-Scene7 auf Adobe Experience Manager neu beginnen. Zusätzlich zur Aufnahme und Verarbeitung von Assets über den Dynamic Media Cloud Service wird eine Prüfung der Asset-Nutzung, der Workflows und der Komponenten durch Adobe dringend empfohlen. Häufig können Sie benutzerdefinierte Komponenten und Workflows durch die Verwendung neuerer, vorkonfigurierter Funktionen ersetzen.

## Option 2: Migrieren der vorhandenen Instanz von Dynamic Media-Hybrid zu Dynamic Media-Scene7 {#process-for-migrating}

| Schritt | Aufgabe | Zu beachten |
|---|---|---|
| 1 | Klonen Sie die Dynamic Media-Hybrid-Autoreninstanz. | Behalten Sie Ihre vorhandene Dynamic Media-Hybrid-Autorenistanz als Fallback bei, bis die verbleibenden Schritte in diesem Migrationsprozess erfolgreich abgeschlossen sind. |
| 2 | Starten Sie die geklonte Autoreninstanz im Dynamic Media-Scene7-Modus. |  |
| 3 | Konfigurieren Sie Dynamic Media in Adobe Experience Manager Cloud Services mit Dynamic Media-Scene7-Anmeldedaten. | Adobe muss die Dynamic Media-Scene7-Bereitstellung genehmigen. So haben Sie parallele Dynamic Media-Hybrid- und Dynamic Media-Scene7-Umgebungen, die von Adobe unterstützt werden, allerdings nur für eine begrenzte Zeit. |
| 4 | Erstellen Sie ein Migrationspaket, damit Sie Assets nach Bedarf aufnehmen können.<br>Löschen Sie die lokalen PTIFF-Dateien, die bei der ersten Aufnahme in Dynamic Media-Hybrid erstellt wurden. | Wenn alle Assets derzeit in Ihrer Dynamic Media-Hybrid-Instanz verfügbar sind, enthält ein Klon dieser Instanz bereits alle Assets. Daher ist kein Paket erforderlich. |
| 5 | Führen Sie den Aktualisierungs-Workflow für Assets aus, damit Sie die Assets mit dem Dynamic Media Cloud Service synchronisieren können. | Adobe empfiehlt, den Update-Workflow in Batches durchzuführen, um eine Komprimierung zu ermöglichen. |
| 6 | Migrieren Sie Viewer-, Bild- und Videovorgaben. |  |
| 7 | Durchsuchen Sie alle Web Content Management-referenzierten Assets und aktualisieren Sie die zugehörigen URLs. |  |
| 8 | Migrieren Sie alle benutzerdefinierten Workflows, die den neuen Dynamic Media-Scene7-Modus unterstützen sollen (manuelle Updates). |  |
| 9 | Überprüfen Sie den Upload und die Konfiguration des Web Content Management. |  |
| 10 | Nach der Überprüfung können Sie eine Genehmigung zur Deaktivierung der Dynamic Media-Hybrid-Autoreninstanz einholen (als Fallback beibehalten). |  |
| 11 | Löschen Sie die Dynamic Media-Hybrid-Autoreninstanz nach etwa einem Monat erfolgreicher Verwendung von Dynamic Media-Scene7. |  |
